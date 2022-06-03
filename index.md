---
layout: default
---

<h2 id="toc">فهرست محتوا</h2>

<div markdown="1">
### [CSS](#css)
<!-- no toc -->
- [ترکیب](#css-syntax)
- [ترتیب ویژگی ها](#section-5)
- [ویژگی های منطقی](#section-6)
- [رنگ ها](#section-7)
- [از import@ استفاده نکنید](#import--)
- [انتخاب گر های media@](#media)
- [تعریف های یک خطی](#section-8)
- [حالت های خلاصه](#section-9)
- [کدنویسی تو در تو](#section-10)
- [عملگرها در پیش پردازنده ها](#section-11)
- [نظرات درون کد](#section-12)
- [نام کلاس ها](#section-13)
- [انتخاب گر ها](#section-14)
- [انتخاب گر های فرزندان](#section-15)
- [سازماندهی](#section-16)
</div>

<div markdown="1">
### [HTML](#html)
<!-- no toc -->
- [ترکیب](#html-syntax)
- [نوع سند HTML5](#html5)
- [ویژگی Language](#language)
- [سازگاری با IE](#ie---)
- [رمزنگاری کارکتر ها](#section)
- [وارد کردن CSS و JavaScript](#css--javascript)
- [صحیح و شفاف](#section-1)
- [ترتیب ویژگی ها](#section-2)
- [مقادیر Boolean](#boolean)
- [کاهش تگ ها](#section-3)
- [تنظیمات ویرایشگر](#section-4)
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
### سازگاری با IE

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

```css
.element {
  color: rgb(255 255 255 / 0.65);
  background-color: rgb(0 0 0 / 0.95);
}
```

<div markdown="1">
### رنگ ها

به علت پشتیبانی از [رنگ های سطح 4](https://www.w3.org/TR/css-color-4/) در [تمام مرورگرهای اصلی](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/rgb#space-separated_values) از این به بعد ویژگی های `rgba` و `hsla` به عنوان میانبر برای `rga` و `hsl` به حساب می آیند ، بنابراین شما می توانید مقدار شفافیت ( Alpha ) را تنظیم کنید. همچنین در نسخه های جدید از قالب تنظیم مقادیر با فاصله نیز پشتیبانی می شود. جهت تطابق پذیری در آینده سعی کنید از این روش استفاده کنید.

جدای از مقدار رنگ و قالب تعریف آن ، سعی کنید که همیشه رنگ شما قوانین [حداقل کنتراست WCAG](https://webaim.org/articles/contrast/) را رعایت کرده باشد. نسبت `4.5:1` برای `16px` یا کمتر و نسبت `3:1` برای مقادیر بزرگتر.

**بیشتر بخوانید :**

- [Smashing Magazine - A Guide To Modern CSS Colors](https://www.smashingmagazine.com/2021/11/guide-modern-css-colors/)
- [`rgb()` - MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/rgb)

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
### از `import@` استفاده نکنید

در مقایسه با `<link>` قطعا ‌`import@` بسیار کند تر عمل می کند. این مورد باعث می شود درخواست های اضافی ثبت شود و خطایابی را بسیار سخت تر می کند. می توانید از راه های جایگزین استفاده کنید :

- استفاده از چند `<link>` جداگانه
- کل فایل های CSS را با استفاده از کتابخانه های پیش پردازنده مانند [Sass](https://sass-lang.com/) یا [Less](https://lesscss.org/) کامپایل کرده و به یک فایل تبدیل کنید
- در صورت استفاده از فریموورک هایی مانند Rails یا Jekyll می توانید تمام فایل های CSS خود را با یکدیگر الحاق کنید

جهت اطلاعات بیشتر, [این مقاله از Steve Souders](https://www.stevesouders.com/blog/2009/04/09/dont-use-import/) را مطالعه کنید.

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
### انتخاب گر های `media@`

در صورت استفاده از این انتخاب گر ها ، آن ها در نزدیک ترین مکان به بلاک های مربوطه قرار دهید. هیچوقت آن ها را به صورت جداگانه در جای دیگر ( مثلا آخر کد ها - مانند خیلی از قالب های آماده که خریداری می کنید ) قرار ندهید. جهت سهولت در برنامه نویسی و خطایابی های آینده ، آن ها را کنار بلاک مربوطه استفاده کنید.

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
### تعریف های یک خطی

در صورتی که بلاک شما فقط **یک ویژگی** دارد , آن ویژگی و براکت ها را تنها در یک خط قرار دهید تا ویرایش آن سریعتر شده و خوانا تر شود هر قانونی که دارای چند ویژگی باشد باید به صورت خطهای جدا تعریف شود..

نکته کلیدی این مورد ، خطایابی است. برای مثال اگر یک CSS Validator به شما بگوید که در خط 183 مشکلی وجود دارد ، اگر شما تعریف یک خطی داشته باشید کاملا متوجه مشکل خواهید شد. و در صورتی که چند ویژگی داشته باشید ، خط های جداگانه به راحتی شما کمک خواهند کرد.

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
### حالت های خلاصه

برای ویژگی ها یا مقادیر سعی کنید همیشه حالت کامل را در نظر بگیرید یا از قرار دادن مقادیر اضافه پرهیز کنید. ویژگی هایی که اشتباهات رایج در آن ها پیش می آید مانند :

- `padding`
- `margin`
- `font`
- `background`
- `border`
- `border-radius`

معمولا نیاز نداریم تا تمام مقادیر را به صورت خلاصه تعریف کنیم. مثلا برای سربرگ ها فقط Margin های بالا و پایین تعریف می شوند. پس بنابراین اگر نیاز بود این دو مقدار را بازنویسی کنید. تعریف یک مقدار `0` به معنی بازنویسی مقدار پیشفرض مرورگر یا ویژگی قبلی خواهد بود.

استفاده بیش از حد از ویژگی‌های ( خلاصه ) کوتاه‌نویسی منجر به کدهای نامرتب‌ تر و عوارض جانبی ناخواسته می‌شود.

Mozilla Developer Network یک [مقاله مفید](https://developer.mozilla.org/en-US/docs/Web/CSS/Shorthand_properties) برای افرادی که با این شرایط آشنا نیستند منتشر کرده است..

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
### کدنویسی تو در تو

تا حد امکان از تودرتوی غیرضروری در پیش پردازشگرها (Sass / Less) خودداری کنید - آن را ساده نگه دارید و از تودرتو معکوس خودداری کنید. این روش را فقط در صورتی استفاده کنید که باید سبک‌ها را به یک Parent اختصاص دهید یا اینکه چندین عنصر وجود دارد که باید تودرتو شوند.

**بیشتر بخوانید :**

- <a href="https://markdotto.com/2015/07/20/css-nesting/">Nesting in Sass and Less</a>

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
### عملگرها در پیش پردازنده ها

جهت خوانایی بهتر ، تمام عملگرهای ریاضی را به همراه عملوند ها در یک پرانتز جداگانه با فاصله های خالی قرار دهید.

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
### نظرات درون کد

کدهای شما ممکن است توسط افراد دیگری نیز خوانده یا خطایابی شوند ( برای مثال در پروژه های متن باز یا پروژه های گروهی ). سعی کنید همیشه نظرات مفید و کارآمدی در مورد کدهایی که نوشته اید قرار دهید.

از خلاصه نویسی های بی مورد پرهیز کرده و در صورت نیاز حتی جملات طولانی و کامل برای کد خود قرار دهید. از عبارت `//` برای نظرگذاری عبارات CSS در پیش پردازنده ها استفاده کنید. زمانی که نسخه Production تهیه میکنید تمام نظرات را حذف کنید.

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
### نام کلاس ها

- برای نام کلاس ها فقط از حروف کوچک و خط تیره استفاده کنید. خط تیره به صورت رایج موارد مرتبط با هم را نشان می هد ، برای مثال نام های : `btn`. و `btn-danger`.
- از عبارات مرتبط و معنا دار استفاده کنید. برای مثال نام `btn`. برای _button_ مناسب است ولی نام `s`. هیچ معنا و مفهوم خاصی ندارد.
- تا جای ممکن نام کلاس ها را کوتاه در نظر بگیرید. از اسامی بلند و بیهوده استفاده نکنید.
- از اسامی معنادار ، ساختاری و هدفمند استفاده کنید.
- از پیشوندهای مناسب بر اساس نزدیک ترین Parent استفاده کنید.
- Prefix classes based on the closest parent or base class.
- از کلاس های `.js-*` برای نشان دادن رفتارها استفاده کنید ( در مقابل سبک ), ولی سعی کنید این کلاس ها خارج از CSS شما باشند.

استفاده از بسیاری از این قوانین در هنگام ایجاد ویژگی های سفارشی و نام متغیرهای پیش پردازنده ها نیز مفید است.

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
### انتخاب گر ها

- از کلاس ها استفاده کنید و ترجیحا سراغ تگ های عمومی المان ها نروید. با این کار ظاهر خوانا تری دارید که به کد HTML شما وابسته نیست.
- از انتخاب گر های متعدد استفاده نکنید. برای مثال `[class^="..."]`. ثابت شده که چنین مواردی عملکرد مرورگر را با اخلال مواجه کرده و سرعت را کم می کند.
- انتخابگرها را کوتاه نگه دارید و سعی کنید تعداد عناصر را در هر انتخابگر به سه محدود کنید.
- کلاس ها را فقط وقتی نیاز بود به نزدیک ترین Parent محدود کنید. در غیر اینصورت از کلاس های پیشوند دار استفاده کنید.

**بیشتر بخوانید :**

- [Scope CSS classes with prefixes](https://markdotto.com/2012/02/16/scope-css-classes-with-prefixes/)
- [Stop the cascade](https://markdotto.com/2012/03/02/stop-the-cascade/)

</div>

```css
.custom-table > tbody > tr > td,
.custom-table > tbody > tr > th {
  /* ... */
}
```

<div markdown="1">
### انتخاب گر های فرزندان

در صورت نیاز می توانید از [ترکیب کننده فرزندان (`>`)](https://developer.mozilla.org/en-US/docs/Web/CSS/Child_combinator) استفاده کنید تا حالت آبشاری انتخابگر را برای ظاهر بعضی المان ها مانند جداول که معمولا به صورت Recursive هستند به راحتی محدود کنید. از این روش برای محدود کردن اعمال ظاهر روی فرزندان استفاده کنید تا از بازنویسی های بی مورد جلوگیری شود.

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

<div markdown="1">
### سازماندهی

- کدهای مربوط به یک بخش خاص از وب سایت خود را به صورت دسته بندی شده قرار دهید.
- از یک روند نظرگذاری مرتب پیروی کنید.
- بین دسته بندی های خود از فضاهای خالی مناسب استفاده کنید تا در صورت سنگین یا طولانی بودن کد های CSS متن خوانا تری داشته باشید.
- در صورتی که فایل های CSS مختلفی دارید ، آن ها را بر اساس بخش های سایت جدا کنید نه بر اساس صفحات. مثلا دسته بندی بر اساس صفحه اصلی ، صفحه ارتباط با ما و ... اشتباه است و دسته بندی بر اساس سربرگ ، پانوشت ، عکس ها و ... صحیح است.

</div>
