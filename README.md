AdminLTE Asset Bundle
=====================

*Backend UI for Yii2 Framework, based on [AdminLTE](https://github.com/almasaeed2010/AdminLTE)*

改它的初衷：
----
后台的皮肤，本来是蛮好用的。但对国内用户就操蛋了，里面使用了google的字体，后台访问受限。


希望增加的功能：
----
皮肤是好看了。但需要内置组件的皮肤，还没有具体到每一个组件的皮肤更新。
因为希望增加组件相关的引用，自动弄上样式，而不是在Yii引用时，写一堆关于class的名字


!["Yii2 AdminLTE Presentation"](https://cloud.githubusercontent.com/assets/874234/7603896/753228ee-f943-11e4-9d42-2a31b41eb42d.jpg)

This package contains an [Asset Bundle for Yii 2.0 Framework](http://www.yiiframework.com/doc-2.0/guide-structure-assets.html)
which registers the CSS files for the AdminLTE user-interface.

The CSS files are installed via Yii's recommended usage of the `fxp/composer-asset-plugin` v1.1.1 or later.


Installation
------------

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

To install AdminLTE v2 run:

```
php composer.phar require tsaoko/yii2-adminlte-asset "2.*"
```


Quick Start
-----------

Once the extension is installed, you can have a **preview** by reconfiguring the path mappings of the view component:

For Yii 2 [Application Template](https://github.com/yiisoft/yii2-app-advanced) or [Basic Application Template](https://github.com/yiisoft/yii2-app-basic)

```php
'components' => [
    'view' => [
         'theme' => [
             'pathMap' => [
                '@app/views' => '@vendor/tsaoko/yii2-adminlte-asset/example-views/yiisoft/yii2-app'
             ],
         ],
    ],
],
```

This asset bundle provides sample files for layout and view (see folder `examples/`), they are **not meant to be customized directly in the `vendor/` folder**.

Therefore it is recommended to **copy the views into your application** and adjust them to your needs.


Customization
-------------

- Copy files from `vendor/dmstr/yii2-adminlte-asset/example-views/yiisoft/yii2-app` (or other theme) to `@app/views`.
- Remove the custom `view` configuration from your application by deleting the path mappings, if you have made them before.
- Edit your views adhering to html markup `vendor/almasaeed2010/adminlte/pages`

### Skins

By default the extension uses blue skin for AdminLTE. You can change it in config file.

```php
'components' => [
    'assetManager' => [
        'bundles' => [
            'tsaoko\web\AdminLteAsset' => [
                'skin' => 'skin-black',
            ],
        ],
    ],
],
```

And then just replace class of body `skin-blue`. You can use `AdminLteHelper::skinClass()` if you don't want to alter every view file when you change skin color.
```html
<body class="<?= \tsaoko\helpers\AdminLteHelper::skinClass() ?>">
```

**Note:** Use `AdminLteHelper::skinClass()` only if you override the skin through configuration. Otherwise you will not get the correct css class of body.

Here is the list of available skins:

```
"skin-blue",
"skin-black",
"skin-red",
"skin-yellow",
"skin-purple",
"skin-green",
"skin-blue-light",
"skin-black-light",
"skin-red-light",
"skin-yellow-light",
"skin-purple-light",
"skin-green-light"
```

If you want to use native DOM of headers AdminLTE

```html
<h1>
    About <small>static page</small>
</h1>
```

then you can follow the code:

```php
/* @var $this yii\web\View */

$this->params['breadcrumbs'][] = 'About';

$this->beginBlock('content-header'); ?>
About <small>static page</small>
<?php $this->endBlock(); ?>

<div class="site-about">
    <p> This is the About page. You may modify the following file to customize its content: </p>
    <code><?= __FILE__ ?></code>
</div>
```

### Left sidebar menu - Widget Menu

If you need to separate sections of the menu then just add the `li.header` item to `items`
```php
    'items' => [
        ['label' => 'Gii', 'icon' => 'fa fa-file-code-o', 'url' => ['/gii']],
        ['label' => 'Debug', 'icon' => 'fa fa-dashboard', 'url' => ['/debug']],
        ['label' => 'MAIN NAVIGATION', 'options' => ['class' => 'header']], // here
        // ... a group items
        ['label' => '', 'options' => ['class' => 'header']],
        // ... a group items
        ['label' => '', 'options' => ['class' => 'header']],
        // ... a group items
```





Further Information
-------------------

For AdminLTE documentation, please read https://almsaeedstudio.com/themes/AdminLTE/documentation/index.html
