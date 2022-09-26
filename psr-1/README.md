# PSR-1: Basic Coding Standard

## 1. Files

### 1.1. PHP Tags
File PHP chỉ được phép sử dụng `<?php` và `<?=`. KHÔNG ĐƯỢC sử dụng các biến thể thẻ khác.

### 1.2. Character Encoding
File PHP chỉ được phép sử dụng encode `UTF-8 without BOM`.

### 1.3. Side Effects
File PHP NÊN dùng để khai báo các thành phần của PHP (class, function, const) và các hiệu ứng phụ (include, thiết lập init PHP), nhưng KHÔNG NÊN dùng cả hai trong một file. Để hiểu rõ hơn nguyên tắc này, bạn hãy xem ví dụ sau

Không nên code thế này:
```php
<?php

ini_set('error_reporting', E_ALL);
 
include "file.php";
 
echo "<html>\n";

function foo()
{
    // function body
}
```

Đoạn code trên bao gồm cả việc khai báo các hiệu ứng phụ (init_set, include) và cả việc khai báo thành phần của PHP (function foo). Chúng ta KHÔNG NÊN code như vậy. Thay vào đó, hãy tách chúng ra làm 2 file.

`functions.php`
```php
<?php

function foo()
{
    // function body
}
```

`index.php`
```php
<?php

ini_set('error_reporting', E_ALL);
 
include "file.php";
include "functions.php";

echo "<html>\n";
```

## 2. Namespace and Class Names
Namespaces và class PHẢI tuân theo PSR "autoloading": [[PSR-0](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md), [PSR-4](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md)].

Mỗi class được khai báo trên một file PHP riêng và có namespace tối thiểu một cấp, cấp đầu tiên là tên vendor (tên đơn vị phát hành)

Tên class PHẢI được khai báo trong StudlyCaps.

Tên class PHẢI được viết dạng `ClassName` thay vì `classname`, `Classname`, `class_name` hay `Class_Name`

Từ PHP 5.3, PHẢI sử dụng namespace khi khai báo class.

KHÔNG ĐƯỢC code thế này:
```php
<?php
 
class Classname
{
    //
}
```

Mà PHẢI code thế này:
```php
<?php
 
namespace Vendor;
 
class ClassName
{
    //
}
```

Từ phiên bản PHP 5.2.x trở về trước, có thể code thế này, nhưng giờ nó không còn được sử dụng nữa.
```php
<?php
 
class Vendor_ClassName
{
    ///
}
```

## 3. Class Constants, Properties, and Methods
Hằng khai báo trong class phải được viết hoa và ngăn cách bằng dấu gạch dưới.
```php
<?php
namespace Vendor\Model;
 
class Foo
{
    const VERSION = '1.0';
    const DATE_APPROVED = '2012-06-01';
}
```

Thuộc tính khai báo trong class có thể viết ở dạng `$ten_thuoc_tinh`, `$TenThuocTinh` hoặc `$tenThuocTinh`. Nhưng nếu bạn chọn một kiểu rồi thì phải thống nhất về cách code trong một phạm vi nào đó, như phạm vi trong class, trong package hoặc trong vendor. Nên sử dụng `$tenThuocTinh`.

Tên `function` phải được đặt ở dang methodName()
```php
<?php
 
namespace Vendor\Model;
  
class Foo
{
    public function methodName()
    {
        //
    }
}
```

## 4. PSR-12
Code PHP theo chuẩn [PSR-12](../README.md)

Tham khảo: https://www.php-fig.org/psr/psr-1/
