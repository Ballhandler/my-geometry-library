# my-geometry-library

Библиотека для работы с геометрическими фигурами на TypeScript.

## Возможности
Создание геометрических фигур: круг, прямоугольник, треугольник  
Вычисление площади и периметра  
Система событий при создании и обновлении фигур  
Фабрика для асинхронного создания фигур  

## Установка.
```typeScript
npm install github:Ballhandler/my-geometry-library
```

## Использование
### Создание фигур через фабрику

```typeScript
import { ShapeFactory, Circle, Rectangle, Triangle } from 'my-geometry-library';

// Создание круга
const circle = await ShapeFactory.createCircle(5);

// Создание прямоугольника
const rectangle = await ShapeFactory.createRectangle(10, 5);

// Создание треугольника
const triangle = await ShapeFactory.createTriangle(3, 4, 5);
```
### Работа с фигурами
```typeScript
// Получение параметров
const params = circle.getParameters(); // { radius: 5 }

// Вычисления
const area = rectangle.getArea();       // 50
const perimeter = rectangle.getPerimeter(); // 30

// Изменения размеров
rectangle.width = 10;
rectangle.height = 5;
circle.radius = 10;
triangle.sideA = 3;
triangle.sideB = 4;
triangle.sideC = 5;
```
### Подписка на события
```typeScript
const circle = await ShapeFactory.createCircle(10);

circle.addEventListener('created', (event: Event) => {
    const customEvent = event as CustomEvent;
    console.log('Создана фигура:', customEvent.detail.shapeid);
});

circle.addEventListener('updated', (event: Event) => {
    const customEvent = event as CustomEvent;
    console.log('Обновлены данные:', customEvent.detail.data);
});

circle.addEventListener('error', (event: Event) => {
    const customEvent = event as CustomEvent;
    console.log('Ошибка:', customEvent.detail.error);
});
```
## API

|     Метод      | Описание                    |
|--------------- |-----------------------------|
| getType()      | Возвращает тип фигуры       |
| getArea()      | Вычисляет площадь           |
| getPerimeter() | Вычисляет периметр          |
| getParameters()| Возвращает параметры фигуры |
| isValid()      | Проверяет валидность фигуры |