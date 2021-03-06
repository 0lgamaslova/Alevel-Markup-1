# Лекция 7

===

# :triangular_flag_on_post: 1.`Позиционирование`

Свойство **_position_** позволяет точно задать новое местоположение блока относительно того места, где он находился бы в нормальном потоке документа. По умолчанию все элементы располагаются последовательно один за другим в том порядке, в котором они определены в структуре HTML-документа.

Для изменения типа позиционирования применяется свойство [position](https://webref.ru/css/position). Само по себе это свойство используется крайне редко и как правило идёт в комбинации со свойствами [left](https://webref.ru/css/left), [right](https://webref.ru/css/right), [top](https://webref.ru/css/top), [bottom](https://webref.ru/css/bottom), которые определяют, соответственно, положение элемента слева, справа, сверху и снизу.


*   **left** — задаёт координаты левого края элемента от левого края родителя или левого края исходного положения элемента.
*   **right** — задаёт координаты правого края элемента от правого края родителя или правого края исходного положения элемента.
*   **top** — задаёт координаты верхнего края элемента от верхнего края родителя или верхнего края исходного положения элемента.
*   **bottom** — задаёт координаты нижнего края элемента от нижнего края родителя или нижнего края исходного положения элемента.


Заметьте, что напрямую нельзя задать положение правого края элемента от левого края родителя и наоборот. Также нельзя задать положение верхнего края элемента от нижнего края родителя и наоборот.

:point_right: **`У position есть пять значений.`**

*   **static** — нормальное или статичное позиционирование, при этом элементы отображаются на веб-странице в том порядке, в каком они идут в исходном коде HTML сверху вниз. static — это значение по умолчанию для position.
*   **relative** — относительное позиционирование. Изменяет положение элемента от его исходного расположения.
*   **absolute** — абсолютное позиционирование. Элемент при этом не существует в потоке документа и его положение задаётся относительно краёв браузера.
*   **fixed** — фиксированное позиционирование. По своему действию похоже на абсолютное позиционирование, но в отличие от него привязывается к указанной свойствами left, top, right и bottom точке на экране и не меняет своего положения при прокрутке веб-страницы.
*   **sticky** — липкое позиционирование. Обычно применяется для фиксации заголовка на одном месте, пока содержимое, к которому относится заголовок, прокручивается на странице.

Свойство position не наследуется, так что для дочерних элементов его требуется указывать явно.



@@@ (json)
[
    ["position:", "comment"],
    ["static", "**Значение по умолчанию**, означает отсутствие позиционирования. Элементы отображаются последовательно один за другим в том порядке, в котором они определены в HTML-документе. Используется для очистки любого другого значения позиционирования."],
    [":small_blue_diamond: relative", "Относительно позиционированный элемент **сдвигается со своего обычного места в разных направлениях относительно границ родительского контейнера, а пространство, которое он занимал, не исчезает**. При этом такой элемент может перекрывать другое содержимое на странице."],
    [":small_blue_diamond:absolute", "Абсолютно позиционированный элемент **полностью удаляется из потока документа и позиционируется относительно границ его блока-контейнера** (другого элемента или окна браузера). Блок-контейнер для абсолютно позиционированного элемента — ближайший элемент-предок, значение свойства position которого равно relative."],
    [":small_blue_diamond: fixed:", "**Фиксирует элемент в указанном месте страницы**. Блоком-контейнером фиксированного элемента является окно просмотра, то есть элемент всегда фиксируется относительно окна браузера и не меняет своего положения во время прокрутки страницы. Сам элемент при этом полностью удаляется из основного потока документа."]
]
@@@

:small_blue_diamond: будут работать `top`, `right`, `bottom`, `left` и `z-index`

===

## `position: static` 

**_Статическое позиционирование_** производится по умолчанию, в том случае, если свойство `position` не указано.

Его можно также явно указать через CSS-свойство.

Например:


```
HTML:
    <div>
        Без позиционирования ("position: static").
    
        <h2>Заголовок</h2>
    
        <div>А тут - всякий разный текст... <br/>
             ... В две строки!</div>
    </div>

CSS:
    .holder {
        background: #fee;
        width: 500px;
    }
    h2 {
        position: relative;
        left: -10%;
        background: #aef;
        margin: 0;
  }
```


![](https://github.com/olgamaslovaolga/Alevel-Markup/raw/master/images/img-poss.png)"width:450px;"

Такая запись встречается редко и используется для переопределения других значений `position`.

Элемент с `position: static` ещё называют **_не позиционированным_**.


**Для нормального позиционирования характерны следующие особенности:**

*   элементы на веб-странице выводятся в том порядке, как они описаны в коде HTML;
*   свойства left, right, top и bottom не дают никакого эффекта;
*   свойство z-index не работает.

===

### `position: relative`

**_Относительное позиционирование_** сдвигает элемент относительно его обычного положения.

Синтаксис:

```
    position: relative
```

Для того, чтобы применить относительное позиционирование, необходимо указать элементу CSS-свойство `position: relative` и координаты `left/right/top/bottom`.

Этот стиль сдвинет элемент на 10 пикселей относительно обычной позиции по вертикали и горизонтали:


```
HTML:
    <div class="holder">
        Заголовок сдвинут на 10px вниз.

        <h2>Заголовок</h2>

        <div>А тут - всякий разный текст... <br/>
         ... В две строки!</div>
    </div>
    
CSS:
    .holder {
        background: #fee; width: 500px
    }
    h2 {
        position: relative;
        top: 10px;
        background: #aef;
        margin: 0;
    }
```

![](https://github.com/olgamaslovaolga/Alevel-Markup/raw/master/images/img-posr.png)"width:450px;"

===

## `position: absolute`

Синтаксис:

```
    position: absolute;
```

**Абсолютное позиционирование делает две вещи:**

1. **Элемент исчезает с того места, где он должен быть и позиционируется заново.** Остальные элементы, располагаются так, как будто этого элемента никогда не было.
2. **Координаты `top/bottom/left/right` для нового местоположения отсчитываются от ближайшего позиционированного родителя**, т.е. родителя с позиционированием, отличным от <code>static</code>. Если такого родителя нет – то относительно документа.


Кроме того:

*   **Ширина элемента с `position: absolute` устанавливается по содержимому.** Детали алгоритма вычисления ширины [описаны в стандарте](http://www.w3.org/TR/CSS2/visudet.html#abs-non-replaced-width).
*   **Элемент получает `display:block`**, который перекрывает почти все возможные `display` (см. [Relationships between „display“, „position“, and „float“](http://www.w3.org/TR/CSS2/visuren.html#dis-pos-flo)).


Например, отпозиционируем заголовок в правом-верхнем углу документа:

```
HTML:
    <div class="holder">
        Заголовок в правом-верхнем углу документа.
        
        <h2>Заголовок</h2>

        <div>А тут - всякий разный текст... <br/>
         ... В две строки!</div>
    </div>
    
CSS:
    .holder {
        background: #fee;
        width: 500px
    }
    h2 {
        position: absolute;
        right: 0;
        top: 0;
        background: #aef;
        margin: 0;
    }

```

![](https://github.com/olgamaslovaolga/Alevel-Markup/raw/master/images/img-posa.png)"width:600px;"



:fire: **`position: absolute` в позиционированном родителе:**

Если у элемента есть позиционированный предок, то `position: absolute` работает относительно него, а не относительно документа.

То есть, достаточно поставить родительскому `div` позицию `relative`, даже без координат – и заголовок будет в его правом-верхнем углу, вот так:


```
HTML:
    <div class="parent">
        Заголовок в правом-верхнем углу DIV'а.
        <h2 style="">Заголовок</h2>
        <div>А тут - всякий разный текст... <br/>
             ... В две строки!</div>
    </div>
    
CSS:
    h2 {
        position: absolute;
        right: 0;
        top: 0;
        background: #aef;
        margin: 0;
    }

    .parent {
        background: #fee;
        width: 500px; 
        position: relative;
    }
```

![](https://github.com/olgamaslovaolga/Alevel-Markup/raw/master/images/img-posar.png)"width:600px;"


:heavy_exclamation_mark: Нужно пользоваться таким позиционированием с осторожностью, т.к оно может перекрыть текст. Этим оно отличается от `float`.

:heavy_exclamation_mark: Важное отличие от `relative`: **так как элемент удаляется со своего обычного места, то элементы под ним сдвигаются, занимая освободившееся пространство**. Это видно в примере выше: строки идут одна за другой.

Так как при `position:absolute` размер блока устанавливается по содержимому, то широкий `Заголовок` «съёжился» до прямоугольника в углу.

Иногда бывает нужно поменять элементу `position` на `absolute`, но так, чтобы элементы вокруг не сдвигались. Как правило это делают, меняя соседей – добавляют `margin/padding` или вставляют в документ пустой элемент с такими же размерами.


:point_down:

Одновременное указание `left`/`right`, `top`/`bottom`:

В абсолютно позиционированном элементе можно одновременно задавать противоположные границы.

Браузер растянет такой элемент до границ.


```

HTML:
    <div style="background:#aef;text-align:center">10px от границ</div>
    
CSS:
    div {
        position: absolute;
        left: 10px; right: 10px; top: 10px; bottom: 10px;
    }
    
```
![](https://github.com/olgamaslovaolga/Alevel-Markup/raw/master/images/img-posw.png)"width:450px;"

===

##  `position: fixed`

Это подвид абсолютного позиционирования.

Синтаксис:

```
    position: fixed;
```

Позиционирует объект точно так же, как `absolute`, но **относительно `window`**.

Разница в нескольких словах:

**Когда страницу прокручивают, фиксированный элемент остаётся на своём месте и не прокручивается вместе со страницей.**

В следующем примере, при прокрутке документа, ссылка `#top` всегда остаётся на своём месте.


```
CSS: 
  #top {
    position: fixed;
    right: 10px;
    top: 10px;
    background: #fee;
  }


HTML:
    <divclas="holder">
        <a href="#" id="top">Наверх (остаётся при прокрутке)</a>
        
        Фиксированное позиционирование.
        
        <p>Текст страницы.. Прокрути меня...</p>
        <p>Много строк..</p><p>Много строк..</p>
        <p>Много строк..</p><p>Много строк..</p>
        <p>Много строк..</p><p>Много строк..</p>
        <p>Много строк..</p><p>Много строк..</p>
    </html>
```

===

# :triangular_flag_on_post: 2. `Координаты`

Для сдвига можно использовать координаты:

*   `top` – сдвиг от «обычной» верхней границы
*   `bottom` – сдвиг от нижней границы
*   `left` – сдвиг слева
*   `right` – сдвиг справа


Не будут работать одновременно указанные `top` и `bottom`, `left` и `right`. Нужно использовать только одну границу из каждой пары.

**Возможны отрицательные координаты** и координаты, использующие другие единицы измерения. Например, `left: 10%` сдвинет элемент на 10% его ширины вправо, а `left: -10%` – влево. При этом часть элемента может оказаться за границей окна:


```
CSS:
  h2 {
    position: relative;
    left: -10%;
  }

HTML:
    <div style="background: #fee; width: 500px">
        <h2 style="background: #aef; margin: 0;">Заголовок сдвинут на 10% влево.</h2>
    </div>
```


**Свойства `left`/`top` не будут работать для `position:static` **. Если их все же поставить, браузер их проигнорирует. Эти свойства предназначены для работы только с позиционированными элементами.

Благодаря комбинации свойств position, `left`, `top`, `right` и `bottom` можно отображать элемент в точке с заданными координатами, фиксировать его в указанном месте, определять положение одного элемента относительно другого, управлять размерами и др.

Для свойства **_top_** положительные значения перемещают верхний край позиционируемого элемента ниже, а отрицательные — выше верхнего края его блока-контейнера. Для свойства **left** положительные значения сдвигают край позиционируемого элемента вправо, а отрицательные значения — влево. То есть, положительные значения смещают элемент внутрь блока-контейнера, а отрицательные — за его пределы.

Атрибуты **_bottom_** и **_right_** дают противоположный эффект

Если атрибут **_right_** имеет положительное значение, то элемент сдвигается влево относительно его правого края, если же атрибут **_right_** имеет отрицательное значение, то элемент сдвигается вправо

При положительном значении атрибута bottom элемент сдвигается вверх, а при отрицательном смещается вниз

При относительном позиционировании элемента его смещение относительно исходного положения приводит к образованию "пустоты" в основном потоке ( место, которое занимал элемент, не заполняется следующими за ним элементами )


# :triangular_flag_on_post: 3. `z-index` или кто кого перекроет

Для изменения положения элементов по оси Z применяется свойство `z-index`, которое непосредственно связано со свойством position. 
z-index работает только для элементов, у которых position задано как relative, absolute или fixed.

Если в одном месте страницы оказываются несколько «абсолютных» блоков, то они перекрывают друг друга. По умолчанию выше оказывается тот блок, который расположен дальше в коде страницы.

C помощью CSS-свойства z-index можно управлять тем, как перекрываются блоки. Значением этого свойства может быть целое число. Чем больше z-index, тем выше располагается блок.


![](https://github.com/olgamaslovaolga/Alevel-Markup/raw/master/images/img-poszi.png)"width:450px;"

```
.blue, .pink, .orange {
    position: absolute;
}

.blue {
    z-index: 2;
}

.orange {
    z-index: 3;
}

.green {
    z-index: 100; // has no effect since the green box is non-positioned
}
```

![](https://github.com/olgamaslovaolga/Alevel-Markup/raw/master/images/img-poszi2.png)"width:450px;"

Смотри тут [https://codepen.io/OlgaMaslova/pen/vYYPMWz](https://codepen.io/OlgaMaslova/pen/vYYPMWz)

===


# :triangular_flag_on_post: 4. Свойство `transition`

**_transition_** позволяет анимировать исходное значение CSS-свойства на новое значение с течением времени, управляя скоростью смены значений свойств.

Смена свойств происходит при наступлении определенного события, которое описывается соответствующим псевдоклассом. Чаще всего используется псевдокласс :hover. Переходы применяются ко всем элементам, а также к псевдоэлементам :before и :after.

 

@@@ (json)
[
    ["**position:**", "**comment**"],
    ["**transition-property**", "Содержит название CSS-свойств, к которым будет применен эффект перехода. Значение свойства может содержать как одно свойство, так и список свойств через запятую. Если поставить all - применит эффект перехода ко всем свойствам элемента."],
    ["**transition-duration**", "Задает промежуток времени, в течение которого должен осуществляться переход. Если разные свойства имеют разные значения для перехода, они указываются через запятую. Если продолжительность перехода не указана, то анимация при смене значений свойств происходить не будет. Значение является обязательным"],
    ["**transition-timing-function**", "Свойство задает временную функцию, которая описывает скорость перехода объекта от одного значения к другому. Если вы определяете более одного перехода для элемент, например, цвет фона элемента и его положение, вы можете использовать разные функции для каждого свойства. Возможные значения: ease , linear , ease-in , ease-out , ease-in-out , cubic-bezier."],
    ["**transition-delay**", "Необязательное свойство, позволяет сделать так, чтобы изменение свойства происходило не моментально, а с некоторой задержкой."]
]
@@@

.

Все свойства, отвечающие за изменение внешнего вида элемента, можно объединить в одно свойство `transition`: 


> **div { transition: transition-property transition-duration transition-timing-function transition-delay; }**


Например:

```
    .link { 
        color: white; 
        transition: color 0.4s ease;
    } 
 
    .link:hover { 
        color: black; 
    }
```

О transition читаем : [http://shpargalkablog.ru/2011/07/transformaciya-css.html](http://shpargalkablog.ru/2011/07/transformaciya-css.html)  или [https://html5book.ru/css3-transition/](https://html5book.ru/css3-transition/) 


# :triangular_flag_on_post: 5. Свойство `transform`

**_transform_** - изменяют размер, форму и положение элемента на веб-странице. Трансформации преобразовывают элемент, не затрагивая остальные элементы веб-страницы, т.е. другие элементы не сдвигаются относительно него. По умолчанию трансформация происходит относительно центра элемента.

Существуют два вида трансформаций – 2D и 3D.

@@@ (json)
[
    ["**position:**", "**comment**"],
    ["**translate(x,y)**", "Сдвигает элемент на новое место, перемещая относительно обычного положения вправо и вниз, используя координаты X и Y, не затрагивая при этом соседние элементы. Если нужно сдвинуть элемент влево или вверх, то нужно использовать отрицательные значения."],
    ["**scale(x,y)**", "Масштабирует элементы, делая их больше или меньше. Значения от 0 до 1 уменьшают элемент. Первое значение масштабирует элемент по ширине, второе — по высоте. Отрицательные значения отображают элемент зеркально."],
    ["**rotate(угол)**", "Поворачивает элементы на заданное количество градусов, отрицательные значения от -1deg до -360deg поворачивают элемент против часовой стрелки, положительные — по часовой стрелке. Значение rotate(720deg) поворачивает элемент на два полных оборота."],
    ["**skew(x-угол, y-угол)**", "Используется для деформирования (искажения) сторон элемента относительно координатных осей. Если указано одно значение, второе будет определено браузером автоматически."]
]
@@@

```
.box { 
    -webkit-transform: rotate(360deg); 
    -ms-transform: rotate(360deg);  
    transform: rotate(360deg);
}
```
Можно объединить несколько трансформаций одного элемента, перечислив их **через пробел** в порядке проявления.

```
.box {transform: scale(1.5) rotate(-10deg);} 

```

 Допустимые значения ([Пример смотрим тут ](https://codepen.io/nazarelen/pen/EaNbLX)):

`matrix() `— любое число

`translate()`, `translateX()`, `translateY()` — единицы длины (положительные и отрицательные), %

`scale()`, `scaleX()`, `scaleY()` — любое число

`rotate()` — угол (deg, grad, rad или turn)

`skew()`, `skewX()`, `skewY()` — угол (deg, grad, rad).

# :house: HomeWork

**1.Первый уровень (“3 блока”)**

Повторите по данному по образцу:

![](https://github.com/olgamaslovaolga/Alevel-Markup/raw/master/images/img-hw7.1.png)"width: 200px;"


**2.Второй уровень(“задать позицию”)**

 Установить позицию элемента <h1> относительно окна браузера. 50px сверху и 50px справа.
 Установить позицию элемента <h2> влево 20px, вниз 30px относительно его нормального положения.
 Установить позицию элемента <h3> 50px слева, 100px сверху, относительно HTML страницы.
 
```
    <p>Это параграф.</p>
    <h1 style="background: #ccc">Title 1</h1>
    <p>Это параграф.</p>
    <h2 style="background: #4CAF50">Title 2</h2>
    <p>Это еще параграф.</p>
    <h3 style="background: #f2dedd">Title 3</h3>
    <p>Это параграф.</p>
   
```

**3.Третий уровень(“хочу как тут”)**

Упражняемся с transform и transition. Создаем блок согласно макета: 

![](https://github.com/olgamaslovaolga/Alevel-Markup/raw/master/images/hw-7.png)"width: 500px;"

Картинку берем [тут](https://drive.google.com/open?id=1kBibHePnomfvgprRwDMogohF-Z7ezSiN) . 

Цвет фона  #0d5825. Ширина 1-й карты 150px. Размер шрифта 25px. 

Текст - это цитата (определяем семантический тег правильно!)


*** Усложняем задание (по желанию ! ): Добавить ховер эффект к предыдущему заданию как показано [на видео](https://s.nimbusweb.me/share/2729558/3gct0x4fzgor8phdf4o1) 
