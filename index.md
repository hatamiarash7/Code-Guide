---
layout: default
---

<h2 id="toc">فهرست محتوا</h2>

<div markdown="1">
### [HTML](#html)
<!-- no toc -->
- [HTML syntax](#html-syntax)
- [HTML5 doctype](#html5-doctype)
- [Language attribute](#language-attribute)
- [IE compatibility mode](#ie-compatibility-mode)
- [Character encoding](#character-encoding)
- [CSS and JavaScript includes](#css-and-javascript-includes)
- [Practicality over purity](#practicality-over-purity)
- [Attribute order](#attribute-order)
- [Boolean attributes](#boolean-attributes)
- [Reduce markup](#reduce-markup)
- [Editor preferences](#editor-preferences)
</div>

<div markdown="1">
### [CSS](#css)
<!-- no toc -->
- [CSS syntax](#css-syntax)
- [Declaration order](#declaration-order)
- [Colors](#colors)
- [Logical properties](#logical-properties)
- [Avoid @import`s](#avoid-imports)
- [Media query placement](#media-query-placement)
- [Single declarations](#single-declarations)
- [Shorthand notation](#shorthand-notation)
- [Nesting in preprocessors](#nesting-in-preprocessors)
- [Operators in preprocessors](#operators-in-preprocessors)
- [Comments](#comments)
- [Class names](#class-names)
- [Selectors](#selectors)
- [Child and descendant selectors](#child-and-descendant-selectors)
- [Organization](#organization)
</div>

## قانون طلایی

> Every line of code should appear to be written by a single person, no matter the number of contributors.

همیشه از این قوانین یا موارد شخصی خودتان استفاده کنید. هر خطای کوچک یا
بزرگی بود آن را گزارش دهید. در صورت داشتن هرگونه نظر ، پیشنهاد ، انتقاد یا
مشارکت یک [Issue ثبت کنید](https://github.com/hatamiarash7/Code-Guide/issues/new).

## HTML

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Page title</title>
  </head>
  <body>
    <img src="images/company-logo.png" alt="Company" />
    <h1 class="hello-world">Hello, world!</h1>
  </body>
</html>
```

<div markdown="1">
### ترکیب
{: #html-syntax }

- از حروف بزرگ برای تگ ها استفاده نکنید ( همچنین برای doctype )
- برای جلو بردن کدها از tab معادل 2 فاصله خالی استفاده کنید
- کدهای زیرمجموعه فقط باید یک بار جلو بروند ( معادل 2 فاصله خالی )</
- برای مقادیر تگ های همیشه از ( " ) استفاده کنید نه ( ' )
- برای المان های مستقل مانند ( `<img>` ) از اسلش استفاده
  نکنید - در [HTML5](https://html.spec.whatwg.org/multipage/syntax.html#syntax-start-tag) این مورد اختیاری می باشد
- تگ های اختیاری پایانی را حذف نکنید ( مانند `</li>` یا `</body>`)

</div>

```html
<!DOCTYPE html>
<html>
  <head>
    <!-- ... -->
  </head>
  <body>
    <!-- ... -->
  </body>
</html>
```

<div markdown="1">
### نوع سند HTML5

اجرای حالت [استاندارد](https://developer.mozilla.org/en-US/docs/Web/HTML/Quirks_Mode_and_Standards_Mode) و رندر گیری بهتر در هر مرورگی با قراردادن این تگ در ابتدای هر فایل HTML
انجام خواهد شد.

</div>

```html
<html lang="en">
  <!-- ... -->
</html>
```

<div markdown="1">
### ویژگی Language

نقل قول از توضیحات HTML5 :

> Authors are encouraged to specify a lang attribute on the root html element, giving the document's language. This aids speech synthesis tools to determine what pronunciations to use, translation tools to determine what rules to use, and so forth.

در مورد ویژگی `lang` [بیشتر بخوانید](https://html.spec.whatwg.org/multipage/semantics.html#the-html-element). جهت مشاهده [لیست کدهای زبان](https://www.iana.org/assignments/language-subtag-registry/language-subtag-registry) به <abbr title="Internet Assigned Numbers Authority">IANA</abbr> مراجعه کنید.

</div>

```html
<!-- IE10 and below only -->
<meta http-equiv="x-ua-compatible" content="ie=edge" />
```

<div markdown="1">
### IE حالت سازگاری با

این روزها دیگر نیاز نیست جهت سازگاری با Internet Explorer از تگ `<meta>` مربوط به آن استفاده کرد ، مگر آن که بخواهید از IE نسخه 10 و قبل تر از آن پشتیبانی کنید. این تگ در IE11 حذف شد و دیگر در Microsoft Edge استفاده نمی شود.

جهت اطلاعات بیشتر, [این مقاله را](https://stackoverflow.com/questions/6771258/what-does-meta-http-equiv-x-ua-compatible-content-ie-edge-do) بخوانید.

</div>

```html
<head>
  <meta charset="utf-8" />
</head>
<body>
  <p>Use an em dash like so—no HTML entity required.</p>
</body>
```

<div markdown="1">
### رمزنگاری کارکتر ها ( رمزگذاری یونیکد )

با اعلام نوع کدگذاری می توانید به راحتی از ارائه صحیح محتوا به کاربران اطمینان پیدا کنید. همچنین این مورد به شما کمک می کند تا از کارکتر های رایج علائم به جای کد HTML آن ها استفاده کنید. برای مثال `—` به جای `&emdash;`. البته بعضی کارکتر ها که برای XML رزرو شده اند همچنان باید به حالت قبل استفاده شوند مانند `ampersand`, `non-breaking spaces`, `less/greater than` and `quotes—you`.

رمزنگاری پیشنهادی UTF-8 می باشد.

</div>

```html
<!-- External CSS -->
<link rel="stylesheet" href="code-guide.css" />

<!-- In-document CSS -->
<style>
  /* ... */
</style>

<!-- JavaScript -->
<script src="code-guide.js"></script>
```

<div markdown="1">
### وارد کردن CSS و JavaScript

طبق قواعد HTML5 ، نیازی به تعریف ویژگی `type` برای فایل های
جاوا اسکریپت یا CSS نیست. مانند `text/css` و
`text/javascript` که این موارد به صورت پیشفرض اعمال شده و صحیح
هستند.

### لینک قواعد HTML5

- [استفاده از link](https://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-link-element)
- [استفاده از style](https://www.w3.org/TR/2011/WD-html5-20110525/semantics.html#the-style-element)
- [استفاده از script](https://www.w3.org/TR/2011/WD-html5-20110525/scripting-1.html#the-script-element)

</div>

```html
<!-- Good -->
<button>...</button>

<!-- Not good -->
<div class="btn" onClick="...">...</div>
```

<div markdown="1">
### صحیح و شفاف

همیشه برای حفظ استاندارد های HTML تلاش کنید. تا جای ممکن کدهایی با کمترین علامت گذاری و مشکل بنویسید

</div>

```html
<a class="..." id="..." data-toggle="modal" href="#"> Example link </a>

<input class="form-control" type="text" />

<img src="..." alt="..." />
```

<div markdown="1">
### ترتیب ویژگی ها

ویژگی ها HTML جهت خوانا تر بودن کد باید به ترتیب قرار بگیرند.

- `class`
- `id`, `name`
- `data-*`
- `src`, `for`, `type`, `href`, `value`
- `title`, `alt`
- `role`, `aria-*`
- `tabindex`
- `style`

ویژگی هایی که برای شناسایی المان ها بیشتر رایج هستند باید در ابتدا بیایند ، مانند `class`, `id`, `name`, و `data`. باقی ویژگی های شناسایی در مرحله دوم و سپس ویژگی های دسترسی و ظاهری تعریف می شوند.

</div>

```html
<input type="text" disabled />

<input type="checkbox" value="1" checked />

<select>
  <option value="1" selected>1</option>
</select>
```

<div markdown="1">
### مقادیر Boolean

ویژگی های صحیح و غلط نیازی به تعریف مقدار ندارند. در XHTML شما باید مقداری برای آن ها داشته باشید ولی در HTML5 چنین چیزی نیاز نیست.

جهت مطالعه بیشتر به [این صفحه](https://html.spec.whatwg.org/multipage/common-microsyntaxes.html#boolean-attributes) از WhatWG مراجعه کنید.

> The presence of a boolean attribute on an element represents the true value, and the absence of the attribute represents the false value.

اگر شما <em>باید</em> مقداری را تعریف کنید ولی **به آن نیاز ندارید**, از این راهنمایی استفاده کنید :

> If the attribute is present, its value must either be the empty string or [...] the attribute's canonical name, with no leading or trailing whitespace.

خلاصه اینکه, **نیاز به تعریف مقدار نیست**.

</div>

```html
<!-- Not so great -->
<span class="avatar">
  <img src="..." />
</span>

<!-- Better -->
<img class="avatar" src="..." />
```

<div markdown="1">
### کاهش تگ ها

تا جای ممکن تگ های اضافی در کد خود استفاده نکنید تا در پایان ، کد HTML کوتاه ، منظم و خوانا تری داشته باشید. برای مثال کد روبرو را نگاه کنید :

</div>

<div></div>

<div markdown="1">
### تنظیمات ویرایشگر

تنظیمات ویرایشگر خود را به این صورت قرار دهید تا کدهای تمیز و خوانا تری داشته باشید :

- مقدار هر tab را برابر با 2 کارکتر خالی قرار دهید
- کارکترهای خالی آخر هر خط را حذف کنید
- کدگذاری را روی UTF-8 قرار دهید
- آخر هر فایل یک خط خالی بگذارید

سعی کنید این تنظیمات را در یک فایل editorconfig. اعمال کنید تا در هر ویرایشگری قابل استفاده باشد و نیاز به تنظیم مجدد نباشد ( برای مثال اگر کدهای شما توسط فرد دیگری با ویرایشگر متفاوت باز شود ، آن فرد نیاز به تنظیم ویرایشگر خود ندارد و این فایل همین کار را انجام خواهد داد )

مطالعه بیشتر :

- [EditorConfig](https://editorconfig.org/)
- [توضیحات Bootstrap](https://getbootstrap.com/docs/4.0/getting-started/introduction/#editor-config)
- [نمونه](https://github.com/twbs/bootstrap/blob/main/.editorconfig)

</div>

## CSS

```scss
// Bad CSS
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin: 0px 0px 15px;
  background-color: rgba(0, 0, 0, 0.5);
  box-shadow: 0px 1px 2px #ccc, inset 0 1px 0 #ffffff;
}

// Good CSS
.selector,
.selector-secondary,
.selector[type="text"] {
  padding: 15px;
  margin-bottom: 15px;
  background-color: rgb(0 0 0 / 0.5);
  box-shadow: 0 1px 2px #ccc, inset 0 1px 0 #fff;
}
```

<div markdown="1">
### ترکیب
{: #css-syntax }

- برای جلو بردن کدها از tab معادل 2 فاصله خالی استفاده کنید
- وقتی که استایل ها را به صورت دسته ای اعمال میکنید ، اسامی انتخابگر ها را در یک خط بنویسید
- جهت خوانا بودن بیشتر قبل از براکت شروع کننده ی بلک ، یک فاصله خالی بگذارید
- براکت پایان دهنده ی بلاک را در یک خط جدید قرار دهید
- بعد از هر علامت `:` برای ویژگی ها ، یک فاصله خالی بگذارید
- جهت خطایابی بهتر ، هر تعریف را در یک خط جداگانه قرار دهید
- در پایان هر خط تعریف ، یک `;` علامت بگذارید ، آخرین خط اختیاری است ولی جهت خطایابی بهتر آن را بگذارید
- ویژگی هایی که مقادیر آن ها چندگانه هستند و با علامت `,` از هم جدا می شوند ، پس از علامت یک فاصله خالی بگذارید. مانند ( `box-shadow` )
- درون مقادیر آرایه ای مانند `rgb()`, `rgba()`, `hsl()`, `hsla()`, یا `rect()` از علامت , استفاده نکنید. در این صورت مقادیری که مربوط به رنگ هستند ، با دیگر مقادیر متمایز خواهند شد.
- در اول مقادیر عددی از 0 استفاده نکنید ( برای مثال `5.` به جای `0.5` و `5px.-` به جای `0.5px-`)
- برای مقادیر رنگی HEX از حروف انگلیسی کوچک استفاده کنید ، مانند `fff` به هنگام مشاهده کد ، حروف کوچک راحت تر از یکدیگر تشخیص داده می شوند.
- در صورت ممکن برای مقادیر رنگی HEX از عبارت خلاصه تر استفاده کنید. برای مثال `fff` به جای `ffffff`
- به هنگام استفاده از ویژگی های یک تگ HTML در انتخاب گر ها ، مقدار آن را در `"` بگذارید. مانند `input[type="text"]`. در بعضی موارد آن ها اختیاری هستند.
- برای مقادیر 0 از واحد ها استفاده نکنید و صرفا همان 0 خالی را بگذارید مانند `margin: 0` به جای `margin: 0px`

در این مورد سوالات بیشتری دارید ? به [این مقاله](https://en.wikipedia.org/wiki/Cascading_Style_Sheets#Syntax) در ویکیپدیا مراجعه کنید.

</div>

```scss
.declaration-order {
  // Positioning
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  z-index: 100;

  // Box model
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100px;
  height: 100px;

  // Typography
  font: normal 14px "Helvetica Neue", sans-serif;
  line-height: 1.5;
  color: #333;
  text-align: center;
  text-decoration: underline;

  // Visual
  background-color: #f5f5f5;
  border: 1px solid #e5e5e5;
  border-radius: 3px;

  // Misc
  opacity: 1;
}
```

<div markdown="1">
### ترتیب ویژگی ها

در یک بلاک ، ویژگی هایی که در یک دسته بندی مرتبط وجود دارند باید به ترتیب قرار بگیرند :

- محل قرارگیری - Positioning
- ابعاد و حالت - Box model
- ویژگی های متنی - Typographic
- ویژگی ها ظاهری - Visual
- متفرقه - Misc

ویژگی های مربوط به محل قرارگیری در ابتدا قرار می گیرند زیرا با توجه به ماهیتشان می توانند یک المان را از کادر خارج کرده یا مقادیر ابعاد و حالت را از بین ببرند. پس از آن ویژگی های مربوط به ابعاد و حالت المان می آید تا مکان نهایی المان و نوع قرارگیری آن را مشخص کند.

برای مثال در حالی که ویژگی `border` بخشی از Box Model می باشد ، برخی سیستم ها به صورت کلی ویژگی [`box-sizing`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing) را ریست کرده و با `border-box` جایگزین می کنند. در این صورت ویژگی `border-width` دیگر اثری در ابعاد شی ما نخواهد داشت. این مورد همراه با تعریف کردن دو ویژگی `border` و `border-radius` باعث خواهند شد این موارد زیرمجموعه بخش Visual یا بصری قرار بگیرند.

ترکیب‌ها و توابع پیش‌پردازنده باید در هر جایی که مناسب‌تر است ظاهر شوند. برای مثال ویژگی `border-top-radius` به جای `border-radius` قرار خواهد گرفت یا ویژگی `responsive-font-size` به جای `font-size` قرار خواهد گرفت.

جهت مشاهده لیست کامل ویژگی ها و ترتیب آن ها به [این مقاله](https://github.com/stormwarning/stylelint-config-recess-order) مراجعه کنید.

</div>

```scss
// Without logical properties
.element {
  margin-right: auto;
  margin-left: auto;
  border-top: 1px solid #eee;
  border-bottom: 1px solid #eee;
}

// With logical properties
.element {
  margin-inline: auto;
  border-block: 1px solid #eee;
}
```

<div markdown="1">
### ویژگی های منطقی

ویژگی های منطقی ( Logical ) جایگزین هایی برای ویژگی های جهت و ابعاد هستند مانند `block` و `inline`. به صورت پیشفرض block به جهت های عمودی ( بالا و پایین ) اشاره می کند در حالی که inline به جهت های افقی ( راست و چپ ) اشاره می کند. شما می توانید این ویژگی ها را در تمام قالب های CSS خود با مرورگر های جدید استفاده کنید.

**چرا باید از این ویژگی ها استفاده کنیم ؟**. در جواب این سوال باید بگویم که تمام زبان ها به صورت افقی نوشته نمی شوند. بنابراین [حالت های نوشتاری](https://developer.mozilla.org/en-US/docs/Web/CSS/writing-mode) باید منعطف باشد. با استفاده از چنین ویژگی هایی به راحتی می توانید از زبان هایی که به صورت افقی و عمودی نوشته می شوند پشتیبانی کنید مانند کره ای ، ژاپنی و چینی. به علاوه اینکه نوشتن آنها کوتاه تر و ساده تر خواهد شد.

**مطالعه بیشتر :**

- [CSS Logical Properties and Values – MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Logical_Properties)
- [CSS Logical Properties and Values — CSS Tricks](https://css-tricks.com/css-logical-properties-and-values/)
- [CSS Writing Modes – MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Writing_Modes)

</div>

<div markdown="1">
### Colors

With the support of [CSS Color Levels 4](https://www.w3.org/TR/css-color-4/) [in all major browsers](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/rgb#space-separated_values), `rgba()` and `hsla()` are now aliases for `rgb()` and `hsl()`, meaning you can modify alpha values in `rgb()` and `hsl()`. Along with this comes support for new space-separated syntax for color values. For compability with future CSS color functions, use this new syntax.

Regardless of your color values and syntax, always ensure your color choices meet [WCAG minimum contrast ratios](https://webaim.org/articles/contrast/) (4.5:1 for 16px and smaller, 3:1 for larger).

**Additional reading:**

- [Smashing Magazine - A Guide To Modern CSS Colors](https://www.smashingmagazine.com/2021/11/guide-modern-css-colors/)
- [`rgb()` - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/rgb)
</div>

```css
.element {
  color: rgb(255 255 255 / 0.65);
  background-color: rgb(0 0 0 / 0.95);
}
```

<div markdown="1">
### Avoid `@import`s

Compared to `<link>`s, `@import` is slower, adds extra page requests, and can cause other unforeseen problems. Avoid them and instead opt for an alternate approach:

- Use multiple `<link>`elements
- Compile your CSS with a preprocessor like [Sass](https://sass-lang.com/) or [Less](https://lesscss.org/) into a single file
- Concatenate your CSS files with features provided in Rails, Jekyll, and other environments

For more information, [read this article by Steve Souders](https://www.stevesouders.com/blog/2009/04/09/dont-use-import/).

</div>

```html
<!-- Use link elements -->
<link rel="stylesheet" href="core.css" />

<!-- Avoid @imports -->
<style>
  @import url("more.css");
</style>
```

<div markdown="1">
### Media query placement

Place media queries as close to their relevant rule sets whenever possible. Don't bundle them all in a separate stylesheet or at the end of the document. Doing so only makes it easier for folks to miss them in the future. Here's a typical setup.

</div>

```css
.element {
  ...;
}
.element-avatar {
  ...;
}
.element-selected {
  ...;
}

@media (min-width: 480px) {
  .element {
    ...;
  }
  .element-avatar {
    ...;
  }
  .element-selected {
    ...;
  }
}
```

<div markdown="1">
### Single declarations

In instances where a rule set includes **only one declaration**, consider removing line breaks for readability and faster editing. Any rule set with multiple declarations should be split to separate lines.

The key factor here is error detection—e.g., a CSS validator stating you have a syntax error on Line 183. With a single declaration, there's no missing it. With multiple declarations, separate lines is a must for your sanity.

</div>

```scss
// Single declarations on one line
.span1 {
  width: 60px;
}
.span2 {
  width: 140px;
}
.span3 {
  width: 220px;
}

// Multiple declarations, one per line
.sprite {
  display: inline-block;
  width: 16px;
  height: 15px;
  background-image: url("../img/sprite.png");
}
.icon {
  background-position: 0 0;
}
.icon-home {
  background-position: 0 -20px;
}
.icon-account {
  background-position: 0 -40px;
}
```

<div markdown="1">
### Shorthand notation

Limit shorthand declaration usage to instances where you must explicitly set all available values. Frequently overused shorthand properties include:

- `padding`
- `margin`
- `font`
- `background`
- `border`
- `border-radius`

Usually we don't need to set all the values a shorthand property represents. For example, HTML headings only set top and bottom margin, so when necessary, only override those two values. A `0` value implies an override of either a browser default or previously specified value.

Excessive use of shorthand properties leads to sloppier code with unnecessary overrides and unintended side effects.

The Mozilla Developer Network has a great article on [shorthand properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties) for those unfamiliar with notation and behavior.

</div>

```scss
// Bad example
.element {
  margin: 0 0 10px;
  background: red;
  background: url("image.jpg");
  border-radius: 3px 3px 0 0;
}

// Good example
.element {
  margin-bottom: 10px;
  background-color: red;
  background-image: url("image.jpg");
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
}
```

<div markdown="1">
### Nesting in preprocessors

Avoid unnecessary nesting in preprocessors whenever possible—keep it simple and avoid reverse nesting. Consider nesting only if you must scope styles to a parent and if there are multiple elements to be nested.

**Additional reading:**

- <a href="https://markdotto.com/2015/07/20/css-nesting/">Nesting in Sass and Less</a>
</div>

```scss
// Without nesting
.table > thead > tr > th { … }
.table > thead > tr > td { … }

// With nesting
.table > thead > tr {
  > th { … }
  > td { … }
}
```

<div markdown="1">
### Operators in preprocessors

For improved readability, wrap all math operations in parentheses with a single space between values, variables, and operators.

</div>

```scss
// Bad example
.element {
  margin: 10px 0 @variable*2 10px;
}

// Good example
.element {
  margin: 10px 0 (@variable * 2) 10px;
}
```

<div markdown="1">
### Comments

Code is written and maintained by people. Ensure your code is descriptive, well commented, and approachable by others. Great code comments convey context or purpose. Do not simply reiterate a component or class name. Use the `//` syntax when writing CSS with preprocessors. When shipping CSS to production, remove all comments.

Be sure to write in complete sentences for larger comments and succinct phrases for general notes.

</div>

```scss
// Bad example
// Modal header
.modal-header {
  ...
}

// Good example
// Wrapping element for .modal-title and .modal-close
.modal-header {
  ...
}
```

<div markdown="1">
### Class names

- Keep classes lowercase and use dashes (not underscores or camelCase). Dashes serve as natural breaks in related class (e.g., `.btn` and `.btn-danger`).
- Avoid excessive and arbitrary shorthand notation. `.btn` is useful for _button_, but `.s` doesn't mean anything.
- Keep classes as short and succinct as possible.
- Use meaningful names; use structural or purposeful names over presentational.
- Prefix classes based on the closest parent or base class.
- Use `.js-*` classes to denote behavior (as opposed to style), but keep these classes out of your CSS.

It's also useful to apply many of these same rules when creating custom properties and preprocessor variable names.

</div>

```scss
// Bad example
.t { ... }
.red { ... }
.header { ... }

// Good example
.tweet { ... }
.important { ... }
.tweet-header { ... }
```

<div markdown="1">
### Selectors

- Use classes over generic element tags for more explicit and reliable styling that isn't dependent on your markup.
- Avoid using several attribute selectors (e.g., `[class^="..."]`) on commonly occuring components. Browser performance is known to be impacted by these.
- Keep selectors short and strive to limit the number of elements in each selector to three.
- Scope classes to the closest parent `only` when necessary (e.g., when not using prefixed classes).

**Additional reading:**

- [Scope CSS classes with prefixes](https://markdotto.com/2012/02/16/scope-css-classes-with-prefixes/)
- [Stop the cascade](https://markdotto.com/2012/03/02/stop-the-cascade/)
</div>

```scss
// Bad example
span { ... }
.page-container #stream .stream-item .tweet .tweet-header .username { ... }
.avatar { ... }

// Good example
.avatar { ... }
.tweet-header .username { ... }
.tweet .avatar { ... }
```

<div markdown="1">
### Child and descendant selectors

When necessary, it may be helpful to use [the child combinator (`>`)](https://developer.mozilla.org/en-US/docs/Web/CSS/Child_combinator) to limit the cascade of some styles in elements like `<table>`s that are often recursively nested. Use it to limit styles to the immediate children elements of a parent element to avoid unnecessary overrides later on.

</div>

```css
.custom-table > tbody > tr > td,
.custom-table > tbody > tr > th {
  /* ... */
}
```

<div markdown="1">
### Organization

- Organize sections of code by component.
- Develop a consistent commenting hierarchy.
- Use consistent white space to your advantage when separating sections of code for scanning larger documents.
- When using multiple CSS files, break them down by component instead of page. Pages can be rearranged and components moved.
</div>

```scss
//
// Component section heading
//

.element { ... }


//
// Component section heading
//
// Sometimes you need to include optional context for the entire component. Do that up here if it's important enough.
//

.element { ... }

// Contextual sub-component or modifer
.element-heading { ... }
```
