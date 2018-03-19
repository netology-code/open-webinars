# Верстаем выезжающее меню

> Информация для преподавателя:
материалы к лекции находятся в репозитории https://github.com/netology-code/slide-in-menu

## Глоссарий понятий
Т.к. на сегодняшнем занятии присутствуют слушатели с абсолютно разным начальным уровнем подготовки, мы уделим некоторое время повторению некоторых базовых понятий, с которыми мы сегодня столкнемся.

### HTML
#### Что такое html?
Чтобы браузер смог отобразить что-либо, ему нужен универсальный способ описания документов.
HTML — HyperText Markup Language — «язык гипертекстовой разметки».
Cтандартизированный язык разметки документов во Всемирной паутине.
HTML создавался как язык для обмена научной и технической документацией, пригодный для использования людьми, не являющимися специалистами в области вёрстки. HTML был задуман и создан как средство структурирования и форматирования документов без их привязки к средствам воспроизведения.
Стандарт поддерживается Консорциумом Всемирной паутины W3C. В стандарт как раз входит допустимый набор элементов - тегов, их роль, и прочие особенности их использования. Текущая версия стандарта HTML 5.1
Вёрстка веб-страниц — создание структуры html-кода, и описание стилей, размещающие элементы веб-страницы (изображения, текст и т. д.) в окне браузера, согласно разработанному макету, таким образом, чтобы элементы дизайна выглядели аналогично макету.
#### Тег
Теги в HTML заключены в угловые скобки < > Нам привычнее их называть символами меньше и больше. Так как нам нужно обозначать начало и конец элемента, например абзаца, то существует понятие открывающего и закрывающего тега. Тег p — позволяет выделить абзац текста (Paragraph по английски).
```
<p>Абзац</p>
<p>Абзац</p>
<p>Абзац</p>
```
На сегодняшнем занятии мы познакомимся с несколькими тегами. Теги могут быть вовлечены в различные отношения:
например, если теги вложены в один и тот же тег и идут друг за другом, то такие теги называются соседями.
При этом соседи которые следую раньше — предшественники. А позже — последователи. Ближайший предшественник — предыдущий тег. Ближайший последователь — следующий.

### css
Как мы уже выяснили, html изначально предназначался для описания структуры контента страниц, а не для форматирования этого контента.
Но как же быть с внешним видом? 
В настоящее время за оформление страницы отвечает css.
CSS – Cascading Style Sheets – каскадные таблицы стилей – это язык, содержащий набор информации, отвечающий за то, как именно будет отображаться страница сайта визуально: используя css, мы можем запрограммировать внешний вид страницы: оформление и расположение блоков и элементов. СSS поддерживается абсолютно всеми браузерами, и благодаря свой простоте, де-факто HTML+CSS стали стандартом для построения веб-интерфейсов.
#### css-правило - элемент css
CSS правило:
```
p {
  color: red;
}
```
В терминах css это – правило. Оно всегда состоит из: селектор (p) – указание к каким тегам применяются указанные в правиле стили пары «свойство» – «значение», разделенных двоеточием и обязательно заканчивающихся точкой с запятой. Объявление правила заключается в фигурные скобки, которые показывают, где начинается и где заканчивается объявление правила.
Что может быть селектором?

+ тег
+ атрибут тега(класс)
+ несколько тегов, несколько классов или же их сочетание и не только.

Какие свойства можно записать внутри правила? Все, что относится к внешнему виду, положению и представлению на экране(ширина, высота, позиция, способ расположения по отношению к соседним тегам, цвет, фон и многое другое).

#### Что такое атрибут тега?
Чтобы сообщить браузеру дополнительную информацию о содержимом тегов или задать специальные свойства используются атрибуты. Атрибуты задаются в открывающем теги
Значение атрибута задается в двойных кавычках “ " после символа =.
Атрибутов может быть несколько, тогда они перечисляются через пробел.
Есть универсальные атрибуты, которые можно указать в любом теге. Например: id — позволяет задать тегу универсальный идентификатор, чтобы в дальнейшем ссылаться на него class — позволяет задать один или несколько через пробел определенных пользователем классов для дальнейшего управления внешним видом элемента через стили. 
У некоторых тегов могут быть особенные атрибуты, например у input(поле ввода) есть атрибут type, с помощью которого поле ввода может превращаться в чекбокс.

Чтобы обратиться к тегу по имени класса, нам нужно в css записать имя этого класса с точкой в начале:

```
.main-header {
    color: red;
    font-size: 50px;
}
```
...
```
<h2 class="main-header">Заголовок 1</h2>
```
Важно, чтобы при этом имя класса, указанное в html коде, в точностью совпадало с именем, указанном в css - иначе правило для указанного тега попросту не сработает.


## Введение
В современном вебе очень распространен паттерн бугер-меню. Этот прием пришел в десктопный веб из мобильной разработки. Поскольку экран телефона или планшета гораздо меньше, чем монитор компьютера, дизайнеры и разработчики искали способы спрятать не приоритетную информацию. Поэтому меню в один момент превратилось в три полоски в углу экрана и стало показываться только по клику на «бургер».
Сегодня мы научимся делать именно такое модное, выезжающее по клику меню.
При этом наше решение будет кроссбраузерным, что не маловажно. Меню будет работать во всех браузерах вплоть до IE 9.

## Разметка
Начнем создавать HTML-разметку, которая послужит каркасом для страницы с меню.
Нам потребуется выделить области для самого меню и для контента страницы.
Создадим общий родительский контейнер с классом `.wrapper`. Он будет оборачивать всю нашу страницу и пригодится нам в дальнейшем.
Внутри него мы расположим меню при помощи HTML5 тег `nav`.
Спецификация тега `nav` позволяет вкладывать внутрь ссылки без необходимости группировать их при помощи списков.
Раньше меню делали при помощи спосков. Например, вот так:
```HTML
<ul>
  <li><a href="">Пункт меню 1</a></li>
  <li><a href="">Пункт меню 2</a></li>
  <li><a href="">Пункт меню 3</a></li>
</ul>
```
Довольно много разметки. Плюс приходилось «сбрасывать» стили по умолчанию для списков. Слишком неэффективно.
Теперь, с повялением тега `nav` мы можем сделать это более изящно. Взглянем на эту разметку:
```HTML
<nav>
  <a href="">Пункт меню 1</a>  
  <a href="">Пункт меню 2</a>
  <a href="">Пункт меню 3</a>  
</nav>
```
Кода стало заметно меньше и нет проблем со стилями по умолчанию.

Теперь добавим в разметку блок, в котором будет размещаться разметка страницы. Весь контент сайта по правилам HTML5 принято размещать внутри тега `main`. Это дает поисковым роботам понять, что является контентом на вашем сайте.
Мы сделаем именно так и добавим в тег `main` немного текста-заглушки, чтобы визуально видеть контент.

[Финальная разметка](http://codepen.io/solarrust/pen/qRLMWJ?editors=1100)

Пока наша страница выглядит не очень. Но это все потому, что мы еще не написали ни грамма стилей.
[Шуточная картинка о HTML без CSS](https://s-media-cache-ak0.pinimg.com/564x/45/7f/36/457f36b0f9e778013f4921ce6bc91f6d.jpg)
Весь механизм и вся красота базируется на чистом CSS. К нему мы и перейдем.

## Стили
### Основные стили
Для начала зададим основные стили странице. Без них совсем никуда.
```css
* {
  box-sizing: border-box;
}

html, body {
  height: 100%;
  font-family: sans-serif;
}

body {
  margin: 0;
}
```
В этих стилях мы «говорим», что все элементы на странице будут расчитывать свои размеры исходя из алгоритма `border-box`.
Дальше мы задаем всей странице высоту в 100% экрана. Таким образом страница займет все видимое пространство по высоте.
В последнем правиле мы сбрасываем стандартный отступ в 8px для элемента `body`.

### Стили для блоков
Теперь перейдем к отдельным блокам нашей страницы. Расположим меню слева от контента. На то место, где он будет появляться после нажатия на «бургер». Также отделим меню от остальной страницы визуально, при помощи фона.
```css
nav {
  background: #FFCC99;
  padding: 20px;
  width: 320px;
}
```
Теперь расположим ссылки друг под другом.
```css
nav a {
  display: block;
  color: black;
  text-decoration: none;
  padding: 10px 0;
}
```
Единственное, что на этом уроке мы сделаем с контентом это зададим ему отступы, чтобы он не прилипал к меню. На реальном проекте в этом месте будет располагаться контент вашего сайта и для него нужны будут отделные стили. Но это уже другая история.
```css
main {
  padding: 20px;
}
```

Чтобы меню было приклеено к левому краю страницы, укажем блоку `nav` `position: fixed`. Теперь положение меню вычисляется относительно экрана браузера. Укажем также координаты верхнего левого края `top: 0` и `left: 0`, не забудем указать `height: 100%` для того, чтобы меню занимало всю доступную высоту экрана по вертикали.
```css
nav {
  height: 100%;
  position: fixed;
  left: 0;
  top: 0;
}
```

Теперь поработаем над «контентом»: после манипуляций с нашим меню мы видим, что часть контента у нас невидима, т.к. попала под наше меню. Исправляем эту ситуацию так: зададим блоку `main` отступ слева, равный ширине нашего меню:
```css
main {
  margin-left: 320px;
}
```
[Промежуточный вариант](https://codepen.io/solarrust/pen/BpGvvm?editors=1100)

### Волшебная кнопка
Теперь займемся кнопкой, котора будет управлять нашим меню. По клику на нее наше меню будет выезжать и уезжать обратно.
Добавим в нашу HTML-разметку новые элементы. Это обязательная составляющая магии.
Добавим чек-бокс:
```HTML
<input type="checkbox" id="navigation">
```
Для этого нам понадобится тег `input` с атрибутом `type` и его значением `checkbox`. Присвоим чек-боксу идентификатор `navigation`.
Теперь ниже добавим `label` и свяжем его с нашим чек-боксом при помощи атрибута `for` и имени идентификатора.
```HTML
<label for="navigation"></label>
```
Чтобы обойтись без JavaScript, мы воспользуемся атрибутом `checked`, который устанавливается, когда чек-бокс нажат и пропадает при повторном нажатии. Воспользуемся этой особенностью и сотворим немного магии:
1. Спрячем меню за пределы экрана
```css
nav {
  margin: 0 0 0 -320px;
}
```
2. Разместим наш чек-бокс так, чтобы его было видно даже при открытом меню:
```css
input {
  position: fixed;
  top: 5px;
  left: 330px;
}
```
3. А теперь волшебное правило. При нажатом чек-боксе свойство `margin` у меню меняется на 0 и мы можем его видеть:
```css
input:checked ~ nav{
  margin: 0;
}
```
В последнем правиле мы использовали псевдокласс `:checked`. Он отвечает за состояние, когда чек-бокс нажат. Псевдокласс помогает выбрать нам некий элемент по его состоянию. Еще одним, наверняка известным вам псевдоклассом является `:hover` – состояние элемента при наведении курсора. Его мы тоже позже используем.
Помимо этого в нашем селекторе есть загадочный знак `~`. Он является частью составного селектора и выбирает элемент из второй части селектора, который находится рядом с элементом из первой части селектора.
Таким образом наш селектор можно расшифровать так: «Выбираем элемент `nav`, который находится неподалеку от нажатого чек-бокса.»

[Пример работы чек-бокса](https://codepen.io/solarrust/pen/ggQqjj?editors=1100)

С меню мы разобрались, а вот контент никак не реагирует на скрытие/появление меню. Давайте добавим эту «реакцию».
Однако, можно заметить, что метод с `margin` для контента не подойдет – мы же не хотим, чтобы ширина контента менялась? Чтобы сдвигать контент, и при этом сохранять его ширину неизменной (именно «задвигать», а не сужать) – мы воспользуемся css трансформацией:
```css
input:checked ~ main {
  transform: translate3d(320px, 0, 0);
}
```
Немного поменяем стили нашей кнопки и заставим ее двигаться вместе с меню:
```css
input {
  position: fixed;
  top: 5px;
  left: 10px;
  z-index: 10;
}

input:checked{
  left: 330px;
}
```

Это дает желаемый эффект, но появляется горизонтальная прокрутка! Что же делать? Здесь нас выручит наш блок `.wrapper`, чтобы предотвратить появление горизонтальной прокрутки на странице, зададим этому блоку свойство `overflow: hidden`, это позволит нам «скрывать» все лишнее:
```css
.wrapper {
  overflow: hidden;
}
```
Наша кнопка до сих пор выглядит как чек-бокс, но не как кнопка. Давайте сделаем ее более похожей на «бургер». Cделаем сам чек-бокс невидимым, передав всю власть элементу `label`. Добавим фоном иконку для нашего меню:
```css
input {
  display: none;
}

label {
  position: fixed;
  top: 5px;
  left: 10px;
  z-index: 10;
  width: 32px;
  height: 32px;
  background: url(https://goo.gl/MU28uI) no-repeat center / cover;
  padding: 5px 0;
}

input:checked ~ label{
  left: 330px;
}
```
Так-то лучше! Теперь при нажатии на `label` наше меню реагирует и появляется или исчезает.

[Пример когда все работает](https://codepen.io/solarrust/pen/mRQodz?editors=1100)

### Наводим лоск
Теперь у нас все работает. Но современные технологии способны на большее. Давайте сделаем красиво и добавим плавности нашим трансформациям.
Для этого нам потребуется свойство `transition`. Мы укажем его всем элементам, которые двигаются:
```css
nav {
  transition: margin-left 400ms ease-in;
}

main {
  transition: transform 400ms ease-in;
}

label {
  transition: left 400ms ease-in;
}
```

И еще немного красоты: добавим реакцию пунктам меню на наведение курсора мыши. Сделаем это при помощи уже упомянутого псевдокласса `:hover`:
```css
nav a:hover {
  color: red;
  transition: color 200ms;
}
```
[Окончательная верстка](https://codepen.io/solarrust/pen/jyQJey?editors=1100)

Наша работа окончена! Теперь вы сможете сверстать такое же меню на любом сайте. Меняйте стили, время анимации, добавляйте свою магию и не бойтесь экспериментировать.


### Вендерные префиксы
Дополнительно мы можем добавить кроссбраузерности.
Под кроссбраузерностью следует понимать одинаковую работу и внешний вид во всех нужных нам браузерах.
Для этого нам нужно будет познакомиться с понятем **вендерный префикс**. С помощью таких префиксов браузеры, которые еще не в полной мере поддерживают то или иное свойство могут делать то, что нам нужно.
Проверить, какие свойства поддерживаются, а какие нет можно на сайте [Can I use](caniuse.com).
К тому же в большинстве текстовых редакторов можно установить специальный плагин Автопрефиксер, который за вас будет проверять такие свойства и расставлять префиксы там, где это требуется. Но пока мы сделаем это руками.
Вендорный префикс `-webkit-` нужен для того, чтобы наша верстка отлично работала в браузерах на основе Хромиума (Хром, Опера, Яндекс.Браузер). Все остальные браузеры отлично понимают все написанные нами стили.

Добавим этот вендорный префикс к свойствам `transition` и `transform`.
На этом наша работа окончена.