# 字段显示

### 分隔线
如果要在字段之间添加一条分隔线：

```php
$show->divider();
```

### 换行
如果要在字段之间使用换行：

```php
$show->newline();
```

### 修改显示内容
用下面的方法修改显示内容

```php
$show->title()->as(function ($title) {
    return "<{$title}>";
});

$show->contents()->as(function ($content) {
    return "<pre>{$content}</pre>";
});
```

### 帮助方法
帮助方法与数据表格字段帮助方法使用一致，可参考[帮助方法](model-grid-column.md#help)。


### 内置显示扩展方法
下面是通过as方法内置实现的几个常用的显示样式：

#### view
`view`方法可以引入一个视图文件。
```php
// 模板中接收以下三个变量：
// name 字段名称
// value 字段值
// model 当前行数据
$show->content->view('admin.fields.content');
```

#### explode
`explode`方法可以把字符串分割为数组。
```php
$show->tag->explode()->label();

// 可以指定分隔符，默认","
$show->tag->explode('|')->label();
```

#### prepend
```php
// 当字段值是一个字符串
$show->email->prepend('mailto:');

// 当字段值是一个数组
$show->arr->prepend('first item');
```

#### append
```php
// 当字段值是一个字符串
$show->email->append('@gmail.com');

// 当字段值是一个数组
$show->arr->append('last item');
```

#### image
字段avatar的内容是图片的路径或者url，可以将它显示为图片：

```php
$show->avatar()->image();
```
image()方法的参数参考Field::image()

#### file
字段document的内容是文件的路径或者url，可以将它显示为文件：

```php
$show->avatar()->file();
```
file()方法的参数参考Field::file()

#### link
字段homepage的内容是url链接，可以将它显示为HTML链接：

```php
$show->homepage()->link();
```
link()方法的参数参考Field::link()

#### label
将字段tag的内容显示为label：

```php
$show->tag()->label();
```
label()方法的参数参考Field::label()

#### badge
将字段rate的内容显示为badge：

```php
$show->rate()->badge();
```
badge()方法的参数参考Field::badge()

#### using
如果字段gender的取值为f、m，分别需要用女、男来显示

```php
$show->gender()->using(['f' => '女', 'm' => '男']);
```

#### 图片轮播
如果字段值为图片数组，可以用下面的调用显示为图片轮播组件

```php
$show->field('images')->carousel();

// 设置显示尺寸和图片服务器
$show->field('images')->carousel($width = 300, int $height = 200, $server);
```

#### 显示文件尺寸
如果字段数据是表示文件大小的字节数，可以通过调用filezise方法来显示更有可读性的文字

```php
$show->field('file_size')->filesize();
```
这样数值199812019将会显示为190.56 MB
