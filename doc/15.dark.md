# Dark-режим в Berry CSS

Berry CSS позволяет работать в dark-режиме (темном режиме браузера).

## Что такое dark-режим?

Некоторым пользователям нравится смотреть сайты в темном режиме. Это когда используется темный фон со светлыми буквами. 

Пример переключения на AlpineJS.

```html
<div x-data="{ darkMode: false }" :class="{ 'dark': darkMode }">
    <button class="button" @click="darkMode = !darkMode">Переключить режим</button>
  
    <div class="pad20 mar20-t rounded bg-primary100 dark:bg-primary700">
        <div class="t-primary700 dark:t-primary200">Этот блок меняет стили в зависимости от dark-режима.</div>
    </div>
</div>
```

```html
<div class="bg-primary100 dark:bg-primary700">
    <div class="t-primary700 dark:t-primary200">Этот блок меняет стили в зависимости от dark-режима.</div>
</div>
```

Для того, чтобы включить dark-режим, нужно указать у родительского элемента класс `.dark`. Если dark-режим нужен для всего сайта, то его следует указывать у тэга `html`: `<html class="dark">`


## Переключение dark-режима пользователем

Скорее всего dark-режим будет включаться пользователем сайта вручную. Для этого на сайте можно разместить js-код, который будет прописывать и снимать класс `.dark` у тега `html`. 

Для того, чтобы автоматически принимать этот класс для всех страниц сайта, следует в секции `head` считать данные из LocalStorage:

```js
&lt;script&gt;
    const SITE_HOST = window.location.hostname; 
    const KEY_THEME_DARK = `theme.${SITE_HOST.replace(/\//g, '_')}`;

    if (localStorage.getItem(KEY_THEME_DARK) === null) {
        theme = window.matchMedia("(prefers-color-scheme: dark)").matches ? "dark" : "light";
        localStorage.setItem(KEY_THEME_DARK, theme);
    }

    if (localStorage.getItem(KEY_THEME_DARK) === "dark") {
        document.documentElement.classList.add("dark");
    }

    function toggleThemeDark() {
        const isDark = document.documentElement.classList.toggle("dark");
        localStorage.setItem(KEY_THEME_DARK, isDark ? "dark" : "light"); 
        return isDark;
    }
&lt;/script&gt;
```

В этих примерах dark-состояние сохраняется в LocalStorage с ключом привязанному к адресу сайта. При первом посещении будет также проверяться темный режем браузера, если он включен, то код сразу пропишет `.dark` для всего сайта.

Если использовать [AlpineJS](https://alpinejs.dev/), то переключение можно реализовать следующим кодом:

```html
<span 
    x-data="{isDark: localStorage.getItem(KEY_THEME_DARK) === 'dark'}" 
    @click="isDark = toggleThemeDark();" 
    :class="isDark ? 'bi-moon' : 'bi-sun-fill'" 
    class="b-inline cursor-pointer" title="Dark/Light"></span>
```

В этом примере формируются иконки Bootstrap Icons, которые переключают класс `.dark` у тега `html` с помощью функции `toggleThemeDark()`.




## Использование функции `light-dark()`

CSS-функция `light-dark()` позволяет переключать два значения в зависимости от светлой или темной темы пользователя. Для этого используется css-свойство `color-scheme` (light/dark). В Berry CSS по умолчанию используется светлый режим:

```css
:root {
    color-scheme: light; 
}
```

А для класса `.dark` он меняется на темный:

```css
.dark {
    color-scheme: dark;
}
```

Таким образом можно использовать `light-dark()` для любых произвольных стилей:

```html
<div style="background-color: light-dark(var(--red200), var(--green800))">Text</div>
```

В этом примере цвет блока в светлом режиме будет red200, а в темном изменится на green800. 



## Использование dark-режима по умолчанию

Для этого достаточно принудительно прописать класс `.dark` у тега `html`.

Точно также можно прописать класс `.dark` у любого другого блока, внутри которого нужно использовать темный режим.


## Семантика dark-режима

С помощью классов с префиксом `dark:` можно явно указывать желаемые цвета в dark-режиме. 

```html
<p class="t-primary500 bg-gray100 dark:t-primary200 dark:bg-gray700">Текст</p>
<!-- 
    цвет текста: primary500
    цвет фона: gray100
    
    цвет текста в dark-режиме: primary200
    цвет фона в dark-режиме: gray700
 -->
```

Dark-режим поддерживается для всех классов всех цветов, а также `hover-`, `bor-`, `gr-` и других. Таким образом можно использовать dark-классы для любого блока.


## Переопределение css-переменных для dark-режима

Поскольку Berry CSS управляется через css-переменные, то нужно переопределить некоторые из них для dark-режима. 

```css
&lt;style&gt;
:root, .dark {
    --primary-hue: 355deg;
    --primary-sat: 40%;
    
    /* dark mode */
    --primary-hue-dark: 325deg;
    --primary-sat-dark: 20%;
}

.dark {
    --body-bg: var(--primary800);
}
&lt;/style&gt;
```

Обратите внимание, что здесь меняются `--primary-hue` и `--primary-sat` (основной цвет primary), поэтому для темного режима нужно также явно задать `--primary-hue-dark` и `--primary-sat-dark`. Если этого не сделать, то будут использованы значения по умолчанию (216deg и 25%).

> Для темного режима обычно используют тот же оттенок, что и основной цвет, но уменьшают насыщенность (saturation). Именно поэтому для dark-режима используются отдельные css-переменные, которые следует задавать явно.

Такой архитектурный подход позволяет применять dark-режим не только ко всему сайту, но и к отдельному блоку:

```html
<div class="dark">
    <div class="bg-primary100 t-primary600 dark:bg-primary600 dark:t-primary300">Lorem ipsum dolor</div>
</div>
```

В данном примере dark-режим будет применён только к этому блоку (будут работать dark-классы), сам сайт останется светлым.


## Стилизация элементов для dark-режима


Для стилизации элементов сайта вы можете использовать такой вариант:

```css
.dark {
    --body-bg: var(--primary950);
    --body-color: var(--primary200);
    
    --link-color: var(--primary500);
    --link-hover-color: var(--primary600);
    
    --form-input-background: var(--primary900);
    --form-input-color: var(--primary200);
    --form-input-border: 1px solid var(--primary750);

    --form-input-focus-border-color: var(--primary600);
    --form-input-focus-shadow: 0 0 0 0.1rem var(--primary700);
    --form-input-focus-background: var(--primary750);
    --form-input-focus-color: var(--primary150);
    --placeholder-color: var(--primary500);
    
    --button-bg-color: var(--primary700);
    --button-text-color: var(--primary100);
    
    --button-disabled-bg-color: var(--gray600);
    --button-disabled-text-color: var(--gray200);
    
    --pre-bg-color: var(--primary800);
    --pre-text-color: var(--primary200);
    
    --pre-border-top: var(--primary700) solid 1px;
    --pre-border-right: var(--primary700) double 3px;
    --pre-border-bottom: var(--primary700) solid 1px;
    --pre-border-left: var(--primary700) double 3px;
    
    --code-background-color: var(--primary550);
    --code-text-color: var(--primary100);
    
    --mark-background-color: var(--primary500);
    --mark-text-color: var(--primary100);
    
    --var-background-color: hsl(var(--accent-hue) var(--accent-sat) 40%);
    --var-text-color: hsl(var(--accent-hue) var(--accent-sat) 90%);
    
    --kbd-background-color:  var(--primary650);
    --kbd-text-color:  var(--primary100);
    --kbd-border: 1px var(--primary600) solid;
    
    --samp-background-color: var(--primary700);
    --samp-text-color: var(--primary200);
    
    --table-th-background   : var(--primary700);
    --table-tr-border-bottom: var(--primary600) 1px solid;
    --table-th-border-top   : var(--primary600) 1px solid;
    --table-th-border-bottom: var(--primary600) 1px solid;
    --table-th-border-right : var(--primary600) 1px solid;
    --table-tr-hover-bg: var(--primary750);
    
    --table-td-border-right: var(--primary600) 1px solid;
    
    --table-striped-odd-bg : var(--primary650);
    --table-striped-even-bg: var(--primary600);
    
    --hr-border: 1px solid var(--primary300);
    
    --bordered: var(--primary600) 1px solid;
    
    --thumbnail-border: var(--primary700) 1px solid;
}
```

Таким образом, как только пользователь включит dark-режим, то браузер автоматически применит эти переменные для отображения всего сайта.


## Theme-зация

Если используется theme-зация сайта (то есть множество разных тем оформления), то можно использовать следующий код:

```css
/*  THEME RED — может быть отдельным css-файлом */
:root {
    /* основной цвет для light */
    --primary-hue: 355deg;
    --primary-sat: 40%;
    
    /* основной цвет для dark */
    --primary-hue-dark: 355deg;
    --primary-sat-dark: 30%; /* понижаем насыщенность */
}

/* общие стили для всех themеs */
:root {
    /* цвет фона по умолчанию */
    --body-bg: var(--gray100);
    
    /* автоматическая подстройка цветов через микширование */
    /* цвет текста */
    --body-color: color-mix(in hsl, var(--primary500) 60%, contrast-color(var(--body-bg)));
    
    /* цвет ссылок */
    --link-color: color-mix(in hsl, var(--primary500) 100%, contrast-color(var(--body-bg)));
    --link-hover-color: color-mix(in hsl, var(--primary500) 80%, contrast-color(var(--body-bg)));
}

/* персонализация цветов для dark-режима */
.dark {
    /* фон BODY */
    --body-bg: var(--primary800);
    
    /* остальные цвета */
    --button-bg-color: var(--primary700);
    --button-text-color: var(--primary100);
    
    /* ... и т.д.*/
}
```

Такой подход используется в [Albireo CMS](https://maxsite.org/albireo) для всех themes-файлов.
