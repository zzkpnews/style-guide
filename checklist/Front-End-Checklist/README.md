<h2 align="center"><a href="http://lab.johnsenzhou.com/Front-End-Checklist/">中原科技网 前端开发指导清单</a></h2>

<p align="center">
  <em><strong>前端开发清单</strong>是一份在站点/HTML页面发布到生产环境之前需要测试的所有元素的详尽列表。</em>
</p>

> 本文档Fork自github项目[Front-End-Checklist](https://github.com/thedaviddias/Front-End-Checklist),并根据中原科技网的业务要求做了一些调整。

## 目录

1. **[Head](#head)**
2. **[HTML](#html)**
3. **[Webfonts](#webfonts)**
4. **[CSS](#css)**
5. **[Images](#images)**
6. **[JavaScript](#javascript)**
7. **[Security](#security)**
8. **[Performance](#performance)**
9. **[Accessibility](#accessibility)**
10. **[SEO](#seo)**

## 一些声明

**前端开发清单**中的所列出的点是大部分前端项目所必需的关注的, 但某些元素可以省略或者并不是这么重要 (在管理Web应用程序的情况下，你可能并不需要RSS订阅源)。我们选择使用一下3级区分:

* ![Low][low_img] **推荐**，但在某些特定情况下可以省略。
* ![Medium][medium_img] **强烈推荐**，但是可能在某些特殊情况下能被省略。某些元素，如果省略将会对性能或SEO方面产生不良影响。
* ![High][high_img] **不能被任何理由忽略**。忽略可能会导致你的页面部分功能障碍或者产生可访问性以及SEO等问题。测试优先级需要首先考虑这些元素。

某些资源拥有特定的标识符，帮助你去理解清单上不同类型的内容或帮助。

* 📖: 文档或文章
* 🛠: 在线工具/测试工具
* 📹: 媒体或视频内容

---

## Head

> **注意:** 你能在[HEAD列表](https://github.com/joshbuchea/HEAD)中找到HTML文档`<head>`标签内所有可配置的属性。

### Meta 标签

* [ ] **Doctype（文档类型）:** ![High][high_img] 以下Doctype标签声明文档为HTML5类型，需要写在HTML文件的顶部。

```html
<!-- 声明文档为 HTML5 类型 -->
<!doctype html>
```

> * 📖 [设置文档字符编码格式 - HTML5 W3C](https://www.w3.org/TR/html5/syntax.html#determining-the-character-encoding)

* 下列两个 meta 标签需要首先声明在head中：Charset 和 Viewport。*

* [ ] **Charset（字符）:** ![High][high_img] 正确声明`Charset` meta (UTF-8)。

```html
<!-- 设置文档的字符编码 -->
<meta charset="utf-8">
```

* [ ] **Viewport（视口）:** ![High][high_img] 正确声明`viewport` meta。

```html
<!-- 响应式网页设计viewpoint声明 -->
<meta name="viewport" content="width=device-width, initial-scale=1">
```

* [ ] **Title（标题）:** ![High][high_img] 所有页面都必须使用`title`标签(SEO:Google会计算标题中使用的字符的像素宽度，范围在472和482像素之间，所以平均字符数限制大约在55个字符左右)。

```html
<!-- 文档标题 -->
<title>网站标题不超过55个字符</title>
```

> * 📖 [Title 标签 - HTML - MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/title)
> * 🛠 [SERP 代码段生成器](https://www.sistrix.com/serp-snippet-generator/)

* [ ] **Description（描述）:** ![High][high_img] 提供`description`标签， 它是唯一的，且内容不能超过150个字符。

```html
<!-- Meta Description -->
<meta name="description" content="Description of the page less than 150 characters">
```

> * 📖[Meta Description 属性 - HTML - MDN](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/The_head_metadata_in_HTML#Adding_an_author_and_description)

* [ ] **Favicons（图标）:** ![Medium][medium_img] 每个`favicon`都被创建并正确显示，如果你只有一个`favicon.ico`，把它放在你网站的根目录下。 通常来说你不需要做任何操作他就能正常显示。 然而, 使用一下示例中的方法是比较好的做法。不过现在我们推荐使用**PNG**格式，相比`.ico`格式有较好的优势(推荐尺寸: 32x32px)。

```html
<!-- 标准favicon -->
<link rel="icon" type="image/x-icon" href="https://example.com/favicon.ico">
<!-- 推荐favicon格式 -->
<link rel="icon" type="image/png" href="https://example.com/favicon.png">
```

> * 🛠 [Favicon 生成器](https://www.favicon-generator.org/)
> * 🛠 [RealFaviconGenerator](https://realfavicongenerator.net/)
> * 📖 [Favicon Cheat Sheet](https://github.com/audreyr/favicon-cheat-sheet)
> * 📖 [Favicons, Touch Icons, Tile Icons, etc. Which Do You Need? - CSS 技巧](https://css-tricks.com/favicon-quiz/)
> * 📖 [PNG favicons - caniuse](https://caniuse.com/#feat=link-icon-png)

* [ ] **Apple Web App Meta:** ![Low][low_img] 苹果设备目前使用的 Meta 标签

```html
<!-- (创建至少200x200像素尺寸的Apple图标文件以支持你可能需要的用到的所有尺寸) -->
<link rel="apple-touch-icon" href="/custom-icon.png">

<!-- 设置Web应用程序是否以全屏模式运行。 -->
<meta name="apple-mobile-web-app-capable" content="yes">

<!-- 设置状态栏样式（有关其可用值，请参见下面的“苹果设备支持的Meta标记列表”） -->
<!-- 除非您具有先前的Meta标签，否则本Meta标签无效 -->
<meta name="apple-mobile-web-app-status-bar-style" content="black">
```

> * 📖 [在苹果设备中配置Web应用程序](https://developer.apple.com/library/content/documentation/AppleApplications/Reference/SafariWebContent/ConfiguringWebApplications/ConfiguringWebApplications.html)
> * 📖 [苹果设备支持的Meta标记列表](https://developer.apple.com/library/content/documentation/AppleApplications/Reference/SafariHTMLRef/Articles/MetaTags.html)

- [ ] **Windows Tiles:**![Low][low_img] Windows 操作系统磁贴

```html
<!-- Microsoft Tiles -->
<meta name="msapplication-config" content="browserconfig.xml" />
```

browserconfig.xml文件的最小所需xml标记如下所示:

```xml
<?xml version="1.0" encoding="utf-8"?>
<browserconfig>
   <msapplication>
     <tile>
        <square70x70logo src="small.png"/>
        <square150x150logo src="medium.png"/>
        <wide310x150logo src="wide.png"/>
        <square310x310logo src="large.png"/>
     </tile>
   </msapplication>
</browserconfig>
```

> 📖 [浏览器配置模式参考](https://msdn.microsoft.com/en-us/library/dn320426(v=vs.85).aspx)

* [ ] **Canonical:** ![Medium][medium_img] 使用`rel="canonical"`以避免重复的内容。

```html
<!-- 帮助防止重复内容出现 -->
<link rel="canonical" href="http://example.com/2017/09/a-new-article-to-red.html">
```

> - 📖 [使用规范的URLs - Search Console Help - Google Support](https://support.google.com/webmasters/answer/139066?hl=en)
> - 📖 [rel = canonical的5个常见错误 - Google Webmaster Blog](https://webmasters.googleblog.com/2013/04/5-common-mistakes-with-relcanonical.html)

### HTML 标签

* [ ] **Language tag（语言标签）:** ![High][high_img] 指定你网站的语言标签并与当前页面语言相关联。

```html
<html lang="zh_cn">
```

* [ ] **Direction tag（方向标签）:** ![Medium][medium_img] `direction`属性规定元素内容的文本方向。(可以在另一个HTML标签上使用)

```html
<html dir="rtl">
```

> * 📖 [dir 属性 - HTML - MDN](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/dir)

* [ ] **Alternate language（备用语言）:** ![Low][low_img] 指定网站的语言标签并与当前页面的语言相关联。

```html
<link rel="alternate" href="https://es.example.com/" hreflang="es">
```

* [ ] **x-default:** ![Low][low_img] 表明此类网页未定位到特定的语言或区域设置。

```html
<link rel="alternate" href="https://example.com/" hreflang="x-default" />
```

> * 📖 [x-default - Google](https://webmasters.googleblog.com/2013/04/x-default-hreflang-for-international-pages.html)

* [ ] **Conditional comments（条件注释）:** ![Low][low_img] 如有需要，可针对IE添加条件注释。

> 📖 [关于条件注释(Internet Explorer) - MSDN - Microsoft](https://msdn.microsoft.com/en-us/library/ms537512(v=vs.85).aspx)

* [ ] **RSS feed（RSS 订阅）:** ![Low][low_img] 如果你的项目是一个博客或者有大量的文章，可以添加一个RSS链接。

* [ ] **CSS Critical（最小 CSS 合集）:** ![Medium][medium_img] `CSS critical`收集并呈现当前页面可见部分的核心CSS。在主要的CSS调用渲染之前以单行(最小化)在`<style></style>`中嵌入。

> * 🛠 [由Addy Osmani于GitHub撰写的Critical](https://github.com/addyosmani/critical)

* [ ] **CSS order（加载顺序）:** ![High][high_img] 所有CSS文件都需要在JavaScript文件加载之前加载完成(除了有时JS文件异步加载到页面之外的情况)。

### Social meta 标签

强烈推荐***Facebook OG*** and ***Twitter Cards***。如果你针对某些特定的存在并希望确保显示，也可以考虑其他社交媒体的meta。

* [ ] **Facebook Open Graph:** ![Low][low_img] 所有Facebook Open Graph（OG）都经过测试并且没有任何错误。图片至少需要600 x 315像素，建议使用1200 x 630像素。

> **注意:** 使用 `og:image:width` 和 `og:image:height` 将会爬取制定尺寸的图像，以便图像能够快速呈现，无需进行异步下载和处理。

```html
<meta property="og:type" content="website">
<meta property="og:url" content="https://example.com/page.html">
<meta property="og:title" content="Content Title">
<meta property="og:image" content="https://example.com/image.jpg">
<meta property="og:description" content="Description Here">
<meta property="og:site_name" content="Site Name">
<meta property="og:locale" content="en_US">
<!-- Next tags are optional but recommended -->
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
```

> * 📖 [A Guide to Sharing for Webmasters](https://developers.facebook.com/docs/sharing/webmasters/)
> * 🛠 使用[Facebook OG testing](https://developers.facebook.com/tools/debug/)测试你的页面。
> * 📖 [Best Practices - Sharing](https://developers.facebook.com/docs/sharing/best-practices/)

* [ ] **Twitter 卡片:** ![Low][low_img]

```html
<meta name="twitter:card" content="summary">
<meta name="twitter:site" content="@site_account">
<meta name="twitter:creator" content="@individual_account">
<meta name="twitter:url" content="https://example.com/page.html">
<meta name="twitter:title" content="Content Title">
<meta name="twitter:description" content="Content description less than 200 characters">
<meta name="twitter:image" content="https://example.com/image.jpg">
```

> * 📖 [推特卡片使用入门 — Twitter Developers](https://developer.twitter.com/en/docs/tweets/optimize-with-cards/guides/getting-started)
> * 🛠 使用[Twitter card validator](https://cards-dev.twitter.com/validator)测试你的页面。

**[⬆ 返回顶部](#目录)**

---

## HTML

### 最佳实践

* [ ] **HTML5 Semantic Elements（HTML5语义化元素）:** ![High][high_img] 正确地使用HTML5语义化标签(header, section, footer, main...).

> 📖 [HTML 参考](http://htmlreference.io/)

* [ ] **Error pages（错误页面）:** ![High][high_img] 404页面和5xx错误页面的存在。记得在5xx错误页面中集成CSS样式文件(在当前服务器上无外部调用)。

* [ ] **Noopener:** ![Medium][medium_img] 如果你使用外部链接`target="_blank"`, 你的链接必须有个`rel="noopener"`属性，防止制表符的隐藏。如果你需要兼容旧版本的火狐浏览器，请使用`rel="noopener noreferrer"`。

> 📖 [关于 rel=noopener](https://mathiasbynens.github.io/rel-noopener/)

* [ ] **Clean up comments（清除注释）:** ![Low][low_img] 在将页面发布到生产环境之前，应该删除不必要的代码。

### HTML 测试

* [ ] **W3C compliant（兼容）:** ![High][high_img] 所有页面需要使用W3C验证器进行测试，以检测HTML代码中的可能存在的问题。

> * 🛠 [W3C validator](https://validator.w3.org/)

* [ ] **HTML Lint:** ![High][high_img] 使用工具来帮助我们分析HTML代码中可能存在的问题。

> * 🛠 [肮脏的标记列表](https://www.10bestdesign.com/dirtymarkup/)
> * 🛠 [webhint](https://webhint.io/)

* [ ] **Desktop Browsers:** ![High][high_img] 所有页面都在桌面浏览器上通过测试(Safari, Firefox, Chrome, Internet Explorer, EDGE...)。

* [ ] **Mobile Browsers:**  ![High][high_img] 所有页面都在移动端浏览器上通过测试(Native browser, Chrome, Safari...).

* [ ] **Link checker（链接检查器）:** ![High][high_img] 页面中链接没有失效，请确认你没有404错误。

> * 🛠 [W3C Link Checker](https://validator.w3.org/checklink)

* [ ] **Adblockers test（广告拦截器测试）:** ![Medium][medium_img] 你的的网站会在启用广告拦截器的情况下正确显示页面内容(你可以提供一条消息，引导人们停用其广告拦截器)。

> [Pixel Perfect - Chrome 扩展](https://chrome.google.com/webstore/detail/perfectpixel-by-welldonec/dkaagdgjmgdmbnecmcefdhjekcoceebi?hl=en)

**[⬆ 返回顶部](#目录)**

---

## Webfonts

> **注意:** 使用webfonts可能会导致文档样式闪烁以及文本不可见，所以在使用时需要考虑使用后备字体，或者使用webfont加载器来控制字体加载行为。
> 
> * 📖 [Google Technical considerations about webfonts](https://developers.google.com/fonts/docs/technical_considerations)

* [ ] **Webfont format（字体格式）:** ![High][high_img] 现代浏览器都支持WOFF、WOFF2、TTF格式

> * 📖 [WOFF - Web开放字体格式 - Caniuse](https://caniuse.com/#feat=woff).
> * 📖 [WOFF 2.0 - Web开放字体格式 - Caniuse](https://caniuse.com/#feat=woff2).
> * 📖 [TTF/OTF - TrueType和OpenType字体支持](https://caniuse.com/#feat=ttf)
> * 📖 [Using @font-face - CSS-Tricks](https://css-tricks.com/snippets/css/using-font-face/)

* [ ] **Webfont size（字体大小）:** ![High][high_img] Webfont大小不超过 2 MB (包括所有版本在内)。

* [ ] **Webfont loader（字体加载器）:** ![Low][low_img] 使用Webfont加载器控制加载行为。

> * 🛠 [Typekit Web字体加载器](https://github.com/typekit/webfontloader)

**[⬆ 返回顶部](#目录)**

## CSS

> **注意:** 大部分前端开发人员都会看看[CSS指南](https://cssguidelin.es/)和[Sass指南](https://sass-guidelin.es/)。如果你对CSS属性有疑问，可以访问[CSS参考文档](http://cssreference.io/)。

* [ ] **响应式网站设计:** ![High][high_img] 网站使用响应式设计。
* [ ] **CSS打印属性:** ![Medium][medium_img] 提供打印样式表，并确保使用正确。
* [ ] **预处理器:** ![Medium][medium_img] 你的网站使用css预处理器(推荐[Sass](http://sass-lang.com/)).
* [ ] **唯一ID:** ![High][high_img] 如果使用了ID，确保ID的唯一性。
* [ ] **Reset CSS:** ![High][high_img] 使用CSS reset(如reset.css, normalize.css, reboot) *(如果你使用的是CSS框架，例如Bootstrap或Foundation，则reset.css已被包含在其中)*

> * 📖 [Reset.css](https://meyerweb.com/eric/tools/css/reset/)
> * 📖 [Normalize.css](https://necolas.github.io/normalize.css/)
> * 📖 [Reboot](https://getbootstrap.com/docs/4.0/content/reboot/)

* [ ] **JS 前缀:** ![Low][low_img] 所有以**js-**开头的class(或者JavaScript文件中使用的id)不写入css文件。

```html
<div id="js-slider" class="my-slider">
<!-- Or -->
<div id="id-used-by-cms" class="js-slider my-slider">
```

* [ ] **CSS embed or line:** ![High][high_img] 避免使用CSS嵌入或内联，仅用于必要的情况(例如: background-image for slider, CSS critical).
* [ ] **浏览器内核前缀:** ![High][high_img] 对部分属性加上浏览器内核前缀，生成你浏览器兼容的属性。

> * 🛠 [Autoprefixer CSS online](https://autoprefixer.github.io/)

### 性能

- [ ] **Concatenation（合并）:** ![High][high_img] 将CSS文件合并到一个文件中。 *(不适用HTTP/2)*
- [ ] **Minification（压缩）:** ![High][high_img] 压缩所有CSS文件。
- [ ] **Non-blocking（非阻塞）:** ![Medium][medium_img] CSS文件需要非阻塞加载，以防在DOM加载时花费大量时间。

> * 📖 [loadCSS by filament group](https://github.com/filamentgroup/loadCSS)
> * 📖 [使用loadCSS预加载CSS的示例](https://gist.github.com/thedaviddias/c24763b82b9991e53928e66a0bafc9bf)

- [ ] **未使用的CSS:** ![Low][low_img] 删除未使用的CSS。

> * 🛠 [UnCSS Online](https://uncss-online.com/)
> * 🛠 [PurifyCSS](https://github.com/purifycss/purifycss)
> * 🛠 [PurgeCSS](https://github.com/FullHuman/purgecss)
> * 🛠 [Chrome DevTools Coverage](https://developers.google.com/web/updates/2017/04/devtools-release-notes#coverage)

### CSS 测试

* [ ] **格式检查:** ![High][high_img] 所有的CSS或SCSS文件没有任何格式错误。

> * 🛠 [stylelint, a CSS linter](https://stylelint.io/)
> * 📖 [Sass指南](https://sass-guidelin.es/)

* [ ] **响应式网页设计:** ![High][high_img] 所有页面都需要经过以下几种情况的测试: 320px, 768px, 1024px (根据自己的项目情况，可以设置更多)。

* [ ] **CSS验证器:** ![Medium][medium_img] CSS都需经过测试，同时所有错误都被修复。

> 🛠 [CSS验证器](https://jigsaw.w3.org/css-validator/)

* [ ] **桌面浏览器:** ![High][high_img] 所有页面都在桌面浏览器进行了测试(Safari, Firefox, Chrome, Internet Explorer, EDGE...)。
* [ ] **移动端浏览器:**  ![High][high_img] 所有页面都在移动端浏览器进行了测试(Native browser, Chrome, Safari...)。
* [ ] **操作系统:**  ![High][high_img] 所有页面都在当前操作系统上进行了测试(Windows, Android, iOS, Mac...)。
* [ ] **Design fidelity 设计图保真度）:** ![High][high_img] 页面需要像素级实现。根据设计稿的质量，你可能不会100％与设计稿相同，但你的网页需要尽可能的靠近设计稿的要求。

> [Pixel Perfect - Chrome Extension](https://chrome.google.com/webstore/detail/perfectpixel-by-welldonec/dkaagdgjmgdmbnecmcefdhjekcoceebi?hl=en)

* [ ] **Reading direction（浏览文本方向）:** ![High][high_img] 如果需要的话，所有页面都需要对LTR和RTL语言进行测试。

> * 📖 [构建RTL-Aware Web Apps & Websites: Part 1 | Mozilla Hacks](https://hacks.mozilla.org/2015/09/building-rtl-aware-web-apps-and-websites-part-1/)
> * 📖 [构建RTL-Aware Web Apps & Websites: Part 2 | Mozilla Hacks](https://hacks.mozilla.org/2015/10/building-rtl-aware-web-apps-websites-part-2/)

**[⬆ 返回顶部](#目录)**

---

## Images

> **注意:** 想要完整的了解图像优化，可以在Addy Osmani查看免费电子书**[图像优化基础](https://images.guide/)**。

### 最佳实践

* [ ] **优化:** ![High][high_img] 所有图像都经过优化并且可在浏览器中正常显示。WebP格式可用于关键页面（如首页）。

> * 🛠 [Imagemin](https://github.com/imagemin/imagemin)
> * 🛠 使用[ImageOptim](https://imageoptim.com/)免费优化您的图像。
> * 🛠 使用[KeyCDN Image Processing](https://www.keycdn.com/support/image-processing) for image optimization in real time.
> * 🛠 使用[Kraken.io](https://kraken.io/web-interface) png和jpg优化的绝佳替代品。 免费计划每个文件最大1mb。
> * 🛠 [TinyPNG](https://tinypng.com/) 无损优化png，apng（动画png）和jpg图像。 提供免费和付费版本。
> * 🛠 [ZorroSVG](http://quasimondo.com/ZorroSVG/) 使用svg遮罩的类似jpg的压缩形式的透明图像。
> * 🛠 [SVGO](https://github.com/svg/svgo) 基于Nodejs的工具，用于优化SVG矢量图形文件。
> * 🛠 [SVGOMG](https://jakearchibald.github.io/svgomg/) 基于SVGO的基于Web的GUI版本，可在线优化您的svg。

* [ ] **Picture/Srcset:** ![Medium][medium_img] 使用Picture/Srcset为用户当前的视口提供最合适的图像。

> * 📖 [如何使用srcset构建响应式图像](https://www.sitepoint.com/how-to-build-responsive-images-with-srcset/)。

* [ ] **视网膜屏:** ![Low][low_img] 提供x2 或 3x的图像来支持视网膜屏显示。
* [ ] **雪碧图:** ![Medium][medium_img] 小图片放到一个雪碧图中。
* [ ] **宽高:** ![High][high_img] 请在<img>上设置宽度和高度属性，如果最终的渲染图像大小已知（可以忽略CSS大小）。
* [ ] **图片描述文本:** ![High][high_img] 所有 `<img>` 必须有`alt`属性来直观的描述图片（在无障碍网页中尤其重要）。

> 📖 [Alt-文本: 终极指南](https://axesslab.com/alt-texts/)

* [ ] **懒加载:** ![Medium][medium_img] 图片使用懒加载 (记得适中提供 noscript 标签).

**[⬆ 返回顶部](#目录)**

---

## JavaScript

### 最佳实践

* [ ] **JavaScript 内联:** ![High][high_img] 确保没有任何js代码内联(与HTML代码混合)。
* [ ] **合并:** ![High][high_img] 合并js文件。
* [ ] **压缩:** ![High][high_img] 压缩所有js文件(可以添加 `.min` 后缀)。

> [压缩资源 (HTML, CSS, and JavaScript)](https://developers.google.com/speed/docs/insights/MinifyResources)

* [ ] **JavaScript安全性:** ![High][high_img]

> [用JavaScript开发安全应用程序指南](https://www.owasp.org/index.php/DOM_based_XSS_Prevention_Cheat_Sheet#Guidelines_for_Developing_Secure_Applications_Utilizing_JavaScript)

* [ ] **`noscript` 标签:** ![Medium][medium_img] 在 HTML 的 body 标签里使用 `<noscript>` 标签以在客户端不支持JavaScript时提供其他展示, [一个使用示例](https://webdesign.tutsplus.com/tutorials/quick-tip-dont-forget-the-noscript-element--cms-25498).

```html
<noscript>
  您需要启用JavaScript才能运行此应用。
</noscript>
```

* [ ] **Non-blocking（非阻塞）:** ![Medium][medium_img] JavaScript文件使用async或延迟使用defer属性异步加载。

> * 📖 [删除阻止渲染的JavaScript代码](https://developers.google.com/speed/docs/insights/BlockingJS)

* [ ] **优化和更新JS依赖库:** ![Medium][medium_img] 项目中使用的所有JavaScript库需要更新至最新版本（对于简单的功能，建议使用Vanilla Javascript）。

> * 📖 [你或许并不需要jQuery](http://youmightnotneedjquery.com/)
> * 📖 [使用原生JavaScript来构建功能强大的Web应用程序](https://plainjs.com/)

* [ ] **Modernizr（现代化）:** ![Low][low_img] 如果您需要指定某些特定功能，则可以使用自定义Modernizr在`<html>`标签中添加class。

> * 🛠 [自定义你的 Modernizr](https://modernizr.com/download?setclasses)

### JavaScript 测试

* [ ] **ESLint:** ![High][high_img] 用ESLint检测并没有错误(基于你的配置规则)。

> * 📖 [ESLint - 适用于JavaScript和JSX的可插入linting实用程序](https://eslint.org/)

**[⬆ 返回顶部](#目录)**

---

## Security

### 扫描并检查你的网站

> * [securityheaders.io](https://securityheaders.io/)
> * [Mozilla 的 Observatory 项目](https://observatory.mozilla.org/)

### 最佳实践

* [ ] **HTTPS:** ![Medium][medium_img] 每个页面和所有外部内容(插件、图像...)都使用HTTPS。

> * 🛠 [Let's Encrypt - 免费 SSL/TLS 证书](https://letsencrypt.org/)
> * 🛠 [免费 SSL 服务测试](https://www.ssllabs.com/ssltest/index.html)
> * 📖 [Can I Use 上严格的传输安全列表](http://caniuse.com/#feat=stricttransportsecurity)

* [ ] **HTTP严格传输安全性(HSTS):** ![Medium][medium_img] HTTP头设置 'Strict-Transport-Security'.

> * 🛠 [检查HSTS预加载状态和资格](https://hstspreload.org/)
> * 📖 [HTTP严格传输安全速查表 - OWASP](https://www.owasp.org/index.php/HTTP_Strict_Transport_Security_Cheat_Sheet)
> * 📖 [传输层保护速查表 - OWASP](https://www.owasp.org/index.php/Transport_Layer_Protection_Cheat_Sheet)

* [ ] **跨站点请求伪造攻击(CSRF):** ![High][high_img] 确保向服务器端发出的请求是合法的，并来自您的网站/应用程序，以防止发生CSRF攻击。

> 📖 [跨站点请求伪造（CSRF）防范清单 - OWASP](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)_Prevention_Cheat_Sheet)

* [ ] **跨站脚本攻击(XSS):** ![High][high_img] 确保页面或网站没有XSS攻击的可能性。

> * 📖 [XSS (跨站脚本攻击) 防范清单 - OWASP](https://www.owasp.org/index.php/XSS_(Cross_Site_Scripting)_Prevention_Cheat_Sheet)
> * 📖 [基于DOM的XSS防范清单 - OWASP](https://www.owasp.org/index.php/DOM_based_XSS_Prevention_Cheat_Sheet)

* [ ] **Content Type Options（内容类型选项）** ![Medium][medium_img] 防止Google Chrome和Internet Explorer尝试将响应的内容类型从服务器声明的内容类型中嗅探出来。

> * 📖 [X-Content-Type-Options - Scott Helme](https://scotthelme.co.uk/hardening-your-http-response-headers/#x-content-type-options)

* [ ] **X-Frame-Options (XFO)（外部框架连接设定）** ![Medium][medium_img] 保护网站的访问者免受劫持攻击。

> * 📖 [X-Frame-Options - Scott Helme](https://scotthelme.co.uk/hardening-your-http-response-headers/#x-frame-options)
> * 📖 [RFC7034 - HTTP Header Field X-Frame-Options](https://tools.ietf.org/html/rfc7034)

* [ ] **Content Security Policy（内容安全策略）** ![Medium][medium_img] 定义内容如何加载到您的网站上的方式以及允许加载的位置。也可以用来防止劫持攻击。
 
> * 📖 [内容安全策略 - 介绍 - Scott Helme](https://scotthelme.co.uk/content-security-policy-an-introduction/)
> * 📖 [CSP 速查表 - Scott Helme](https://scotthelme.co.uk/csp-cheat-sheet/)
> * 📖 [CSP 速查表 - OWASP](https://www.owasp.org/index.php/Content_Security_Policy_Cheat_Sheet)
> * 📖 [内容安全政策参考](https://content-security-policy.com/)

**[⬆ 返回顶部](#目录)**

---

## Performance

### 最佳实践

- [ ] **需要达到的目标:** ![Medium][medium_img] 你的网页需要达到如下目标：
  - 在第一秒内展示出一个有意义的绘画
  - 在“平均”配置下互动时间不到5秒（在速度为400ms的RTT和400kbps传输速度的慢速3G网络上，售价200美元的Android）在2秒内可以重复访问
  - 压缩后的关键文件大小低于170Kb

> * 🛠 [网站页面分析器](https://tools.pingdom.com)
> * 🛠 [WebPageTest](https://www.webpagetest.org/)
> * 📖 [Size Limit: 使网页更轻](https://evilmartians.com/chronicles/size-limit-make-the-web-lighter)

- [ ] **文件压缩:** ![Medium][medium_img] 压缩你的HTML文件。

* [ ] **懒加载:** ![Medium][medium_img] 图片、js脚本和CSS需要懒加载，以提高当前页面的响应时间（请参见各自部分的详细信息）。

* [ ] **Cookie大小:** ![Medium][medium_img] 如果使用Cookie，确保每个Cookie不超过4096个字节，并且域名下不超过20个Cookie。

> * 📖 [Cookie规范: RFC 6265](https://tools.ietf.org/html/rfc6265)
> * 📖 [Cookies](https://developer.mozilla.org/en-US/docs/Web/HTTP/Cookies)
> * 🛠 [浏览器Cookie限制](http://browsercookielimits.squawky.net/)

* [ ] **第三方组件:** ![Medium][medium_img] 在可能的情况下，用静态组件替代依赖于外部JS的第三方iframe或组件（如共享按钮），从而限制对外部API的调用，并将用户活动保持为私有。

> * 🛠 [简单的共享按钮生成器](https://simplesharingbuttons.com/)

### 为将到来的请求做准备

> 📖 [以下几种技术的详细说明](https://css-tricks.com/prefetching-preloading-prebrowsing/)

* [ ] **DNS解析:** ![Low][low_img] 使用`dns-prefetch`让第三方DNS服务商主动去执行域名解析的功能。

```html
<link rel="dns-prefetch" href="https://example.com">
```

* [ ] **预连接:** ![Low][low_img] 使用`preconnect`在空闲期间提前做好DNS查询, TCP三次握手和TLS协商。

```html
<link rel="preconnect" href="https://example.com">
```

* [ ] **预获取:** ![Low][low_img] 使用`prefetch`在空闲期间提前请求即将需要的资源(例如：图像的懒加载)。

```html
<link rel="prefetch" href="image.png">
```

* [ ] **预加载:** ![Low][low_img] 使用`preload`提前加载当前页面所需要的资源(例如：js脚本放在`<body>`的最后)。

```html
<link rel="preload" href="app.js">
```

> 📖 [预加载和预获取之间的差异](https://medium.com/reloading/preload-prefetch-and-priorities-in-chrome-776165961bbf)

### 性能测试

* [ ] **Google PageSpeed:** ![High][high_img] 所有的网页都经过测试（不仅仅是首页），而且得分至少为90/100。

> * 🛠 [Google PageSpeed](https://developers.google.com/speed/pagespeed/insights/)
> * 🛠 [用Google测试移动端速度](https://testmysite.withgoogle.com)
> * 🛠 [WebPagetest - 网站性能和优化测试](https://www.webpagetest.org/)
> * 🛠 [GTmetrix - 网站速度和性能优化](https://gtmetrix.com/)
> * 🛠 [Speedrank - 改善您网站的性能](https://speedrank.app/)

**[⬆ 返回顶部](#目录)**

---

## Accessibility

> **注意:** 查看注意事项视频列表[A11ycasts with Rob Dodson](https://www.youtube.com/playlist?list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g) 📹

### 最佳实践

- [ ] **渐进式增强:** ![Medium][medium_img] 主要功能如主导航和搜索等功能应该在没有启用JavaScript的情况下能够正常运行。

> 📖 [在Chrome开发者具中启用/禁用JavaScript](https://www.youtube.com/watch?v=kBmvq2cE0D8)

- [ ] **颜色对比度:** ![Medium][medium_img] 颜色对比度至少通过WCAG AA标准验证(移动端需要通过AAA)。

> * 🛠 [Contrast ratio](https://leaverou.github.io/contrast-ratio/)

#### 标题

* [ ] **H1:** ![High][high_img] 所有页面都有H1，它不是网站的标题。
* [ ] **Headings:** ![High][high_img] 标题应以正确的顺序合理使用(H1至H6)。

> * 📹 [Why headings and landmarks are so important -- A11ycasts #18](https://www.youtube.com/watch?v=vAAzdi1xuUY&index=9&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g)

### 语义化

- [ ] **使用特定的HTML5输入类型:** ![Medium][medium_img] 这对于显示不同类型的自定义键盘和小部件的移动设备尤其重要。

> * 📖 [Mobile Input Types](http://mobileinputtypes.com/)

### 表单

* [ ] **Label:** ![High][high_img] `label`与每个输入表单元素相关联，如果`label`无法显示，请使用`aria-label`代替。

> 📖 [使用aria-label属性 - MDN](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-label_attribute)

### Accessibility 测试

* [ ] **Accessibility标准测试:** ![High][high_img] 使用WAVE工具测试你的页面是否符合accessibility标准。

> * 🛠 [Wave testing](http://wave.webaim.org/)

* [ ] **Keyboard navigation（键盘导航）:** ![High][high_img] 在你的键盘上以可能出现的操作顺序去测试，确保所有交互式元素都可访问和可用。
* [ ] **Screen-reader（屏幕阅读器）:** ![Medium][medium_img] 所有页面都在屏幕阅读器(VoiceOver, ChromeVox, NVDA or Lynx)中进行了测试。
* [ ] **Focus style（专注风格）:** ![High][high_img] 如果焦点被禁用，它将被CSS中的可见状态所替代。

> * 📹 [Managing Focus - A11ycasts #22](https://www.youtube.com/watch?v=srLRSQg6Jgg&index=5&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g)

**[⬆ 返回顶部](#目录)**

---

## SEO

* [ ] **Google Analytics:** ![High][high_img] Google Analytics 正确安装和配置。

> * 🛠 [Google Analytics](https://analytics.google.com/analytics/web/)
> * 🛠 [GA Checker (and others)](http://www.gachecker.com/)

* [ ] **Baidu Analytics:** ![High][high_img] Baidu Analytics 正确安装和配置（国内网站）。

* [ ] **Headings logic:** ![Medium][medium_img] 标题文字有助于表达当前页面的主要内容。

> * 🛠 [Tota11y, tab Headings](http://khan.github.io/tota11y/#Try-it)

* [ ] **sitemap.xml:** ![High][high_img] 创建`sitemap.xml`文件并提交到Google Search Console(以前的Google管理员工具)。

> * 🛠 [Sitemap generator](https://websiteseochecker.com/html-sitemap-generator/)

* [ ] **robots.txt:** ![High][high_img] `robots.txt`正确配置，不要阻止网页被爬取。

> * 📖 [The robots.txt file](https://varvy.com/robottxt.html)
> * 🛠 使用[Google Robots Testing Tool](https://www.google.com/webmasters/tools/robots-testing-tool)测试你的`robots.txt`。 

* [ ] **Structured Data（结构化数据）:** ![High][high_img] 使用Structured Data的页面通过测试并且没有错误。Structured Data会帮助爬虫理解当前页面的内容。

> * 📖 [Structured Data 简介 | 搜索 | Google Developers](https://developers.google.com/search/docs/guides/intro-structured-data)
> * 📖 [RDFa - Linked Data in HTML](https://rdfa.info/)
> * 📖 [JSON-LD](https://json-ld.org/)
> * 📖 [Microdata](https://www.w3.org/TR/microdata/)
> * 🛠 使用[Structured Data Testing Tool](https://developers.google.com/structured-data/testing-tool/)测试你的页面。
> * 🛠 适用于结构化数据的完整结构列表[Schema.org Full Heirarchy](http://schema.org/docs/full.html)

* [ ] **Sitemap HTML（HTML网站地图）:** ![Medium][medium_img] 提供HTML网站地图，可通过网站页脚中的链接进行访问。

> * 📖 [Sitemap 指南 | Google 支持](https://support.google.com/webmasters/answer/183668?hl=en)
> * 🛠 [Sitemap 生成器](https://websiteseochecker.com/html-sitemap-generator/)

* [ ] **Pagination link tags:** ![Medium][medium_img] Provide `rel="prev"` and `rel="next"` to indicate paginated content.

> * 🛠 [分页（rel =“ prev / next”）测试工具](https://technicalseo.com/seo-tools/rel-prev-next/)
> * 📖 [分页准则 - Google Support](https://support.google.com/webmasters/answer/1663744?hl=en)

```html
<!-- Example: Pagination link tags for page 2 of a paginated list -->
<link rel="prev" href="https://example.com/?page=1">
<link rel="next" href="https://example.com/?page=3">
```

**[⬆ 返回顶部](#目录)**

## 前端开发清单徽章

如果想标示出你的项目遵循了这份“前端开发清单”的各项规定，欢迎将如下徽章放在你的项目的README文件上！

➔ [![Front‑End_Checklist followed](https://img.shields.io/badge/Front‑End_Checklist-followed-brightgreen.svg)](https://github.com/thedaviddias/Front-End-Checklist/)

```md
[![Front‑End_Checklist followed](https://img.shields.io/badge/Front‑End_Checklist-followed-brightgreen.svg)](https://github.com/thedaviddias/Front-End-Checklist/)
```

**[⬆ 返回顶部](#目录)**

---

## 开源协议

[![CC0](https://i.creativecommons.org/p/zero/1.0/88x31.png)](https://creativecommons.org/publicdomain/zero/1.0/)

**[⬆ 回到顶部](#目录)**

[low_img]: data/images/priority/low.svg
[medium_img]: data/images/priority/medium.svg
[high_img]: data/images/priority/high.svg
