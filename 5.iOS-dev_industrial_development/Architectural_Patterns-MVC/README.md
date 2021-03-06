# Архитектурные паттерны: MVC

## Задача 1

1. Создайте собственный класс `CustomButton`, название на ваше усмотрение, где: 
- будет собственный инициализатор, в который передаются, к примеру, параметры `title`, `titleColor` и другие по желанию 
- замыкание, в котором вызывающий объект, контроллер или родительское UIView, определят действие по нажатию кнопки
- `@objc private func buttonTapped()` будет спрятана внутрь реализации `CustomButton`, и на уровне родительского `UIView` фигурировать не будет 

2. Замените во всех контроллерах общие `UIButton` на вашу `CustomButton` 

## Задача 2 

Обновление данных: обрабатываем в UI touch event, передаем данные в слой модели, там видоизменяем и отдаем обратно в виде нотификации.

а) сохранить в модели любое слово, назовем его условный "пароль" 

б) создать кастомные `UITextField` + `UIButton` в `FeedViewController`

в) кнопка отправляет введенный текст (с проверкой на пустое значение) в модель - метод модели `check(word:)` 

г) модель проверяет слово и отправляет ответ верно / неверно 

* если верно, показывается `UILabel` с зеленым текстом 
* если неверно, показывается `UILabel` с красным текстом 

Подсказки: 
- контроллер использует метод модели, зависимость от модели внедряется через инициализатор. Если UI был сверстан через __Storyboard__, рекомендуем переверстать UI через код с использованием, к примеру, Cocoapods + SnapKit и написать свои инициализаторы
- с точки зрения архитектуры из двух подходов для общения модели и контроллера выберите одно: модель возвращает значение или через замыкание, или через нотификацию

* если используются замыкания, помним про `weak self` или `unowned self` 
* если нотификации - вызов метода `.post` удобно делать из `property observer`, то есть из `didSet` того свойства, значение которого мы хотим передать в нотификации 
