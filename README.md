# Rezak


Это консольная программа, которая обрезает пустые рамки изображения.
Присоединиться к улучшению функционала может любой желающий, открыв актуальные задачи по [ссылке](https://github.com/Alexandrsv/Rezak/projects/1). Добавляйте новые, задавайте вопросы.

###### Но зачем?

- Предположим, что есть задача наскринить отзывов, для дальнейшего размещения скринов в вебе. Если лениво скринить руками, то на странице в вебе список таких скринов будет смотреться криво. Для облегчения жизни можно обрезать картинки по контенту.
- Предположим у нас есть пдф книга, с большими отступами от текста которую ну очень хочется почитать на планшете с маленьким экраном. Можно разобрать книгу на картинки, обрезать и потом собрать. Читать будет удобнее.


## Запуск

Для одиночного файла ```python main.py demo.png```

Массово обрезать файлы в папке ```find ./img -type f | xargs -n1 python main.py```


###### Было

![Было](https://sun9-43.userapi.com/impg/K3vsG6za8c7TPLdhAykxTvF5kYStDKGZuiIFkw/O8J5XGVeAus.jpg?size=504x296&quality=96&sign=ff4a56a2423d0fbce13ca03ba1577354&type=album)

###### Стало

![Стало](https://sun9-55.userapi.com/impg/6GiLcT-v5zruZdmBaR8t8bBvb-VxxrpBvh3EqQ/V4XY4dThsPo.jpg?size=296x283&quality=96&sign=7dc6f207365b88c565264ebbb7e968f2&type=album)


## Алгоритм работы

Приложение "Резак" использует библиотеку Pillow, для работы с изображениями

- При помощи Pillow картинка загружается в виде матрицы, в которой содержатся цвета.
- Берем координаты пикселя 1.1 и получаем его цвет. Предполагается, что по этим координатам можно получить цвет рамки
- Резак последовательно, попиксельно проверяет оси X и Y, двигаясь сверху, снизу, слева, справа, по направлению от края изображения, пока не найдет пиксель, цвет которого отличается.
- В результате прохода получаем 4 самые крайние координаты пикселей, относительно 4х сторон и обрезаем изображение
- Profit
