---
title: <text>
type: references
order: 2.12
version: 2.1
---

# &lt;text&gt;

The weex builtin component 'text' is used to render text with specified style rule. <text> tag can contain text value only. You can use variable interpolation in the text content with the mark `{% raw %}{{}}{% endraw %}`.

## Child Components

This component supports no child components.

## Attributes

* value(string): text value of this component. This is equal to the content of 'text'. 

### example

```
var textComponent = this.$el("textid");
this.text = textComponent.attr.value;
```

## Styles

* lines: specify the text lines. Default value is `0` for unlimited.
* text styles: check out [text styles](../text-style.html)

  * support 'color' style.
  * support 'font-size' style. iOS: default vlaue `32`. Android: platform specify. HTML5: default value `32`.
  * support 'font-style' style.
  * support 'font-weight' style.
  * support 'text-align' style.
  * support 'text-decoration' style.
  * support 'text-overflow' style.
  * support 'line-height'(available from v0.6.1) style. line-height in iOS is different from h5 and Android, text value will be placed at bottom of line box.
  * not support 'flex-direction, 'justify-content', 'align-items' which is active for child nodes, and text has no child nodes.

### common styles
check out [common styles for components](../common-style.html)

* support flexbox related styles.
* support box model related styles.
* support 'position' related styles.
* support 'opacity', 'background-color' etc.

## Events

### common events
check out [common events](../common-event.html)

* support 'click' event.
* support 'appear' / 'disappear' event. 

## Example

```html
<template>
  <div class="wrapper">
    <div class="panel">
      <text class="text" lines="3">Weex 是一套简单易用的跨平台开发方案，能以 Web 的开发体验构建高性能、可扩展的原生应用。Vue 是一个轻量并且功能强大的渐进式前端框架。</text>
    </div>
    <div class="panel">
      <text class="text" lines="3">Weex is an cross-platform development solution that builds high-performance, scalable native applications with a Web development experience. Vue is a lightweight and powerful progressive front-end framework. </text>
    </div>
  </div>
</template>


<style scoped>
  .wrapper {
    flex-direction: column;
    justify-content: center;
  }
  .panel {
    width: 600px;
    margin-left: 75px;
    border-width: 2px;
    border-style: solid;
    border-color: #BBB;
    padding-top: 15px;
    padding-bottom: 15px;
    padding-left: 15px;
    padding-right: 15px;
    margin-bottom: 30px;
  }
  .text {
    lines: 3;
    color: #666666;
    font-size: 32px;
  }
</style>
```

[try it](http://dotwe.org/vue/154e20171d350a081fba7878c53cf7d2)

## iconfont

`support:v0.12.0`

support `ttf` and `woff` font format to custom your text, call [addRule](../modules/dom.html#addRule) in dom module to build your own `font-family`


```html
<template>
    <div style='flex-direction:row;margin-top:50px'>
        <text style='font-family:iconfont4;font-size:50;color:green'>&#xe614;&#xe612;&#xe613;</text>
        <text style='font-family:iconfont4;font-size:50;'>&#xe614;&#xe612;&#xe613;&#xe61d;&#xe714;</text>
        <text style='font-family:iconfont4;font-size:60;color:blue'>&#xe711;</text>
        <text style='font-family:iconfont4;font-size:60;color:green'>&#xe71c;&#xe60b;</text>
    </div>
</template>
<script>
    module.exports = {
        created: function() {

        var domModule = weex.requireModule('dom');
        //目前支持ttf、woff文件，不支持svg、eot类型,moreItem at http://www.iconfont.cn/

        domModule.addRule('fontFace', {
            'fontFamily': "iconfont2",
            'src': "url('http://at.alicdn.com/t/font_1469606063_76593.ttf')"
        });
    }
}
</script>
```

[try it](http://dotwe.org/vue/d96b6f89aadd1d628111c16a30e80482)