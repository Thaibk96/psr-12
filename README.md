# PSR-12: Extended Coding Style

## 1. Overview
PSR-2 được ra đời vào năm 2012, nhưng kể từ đó tới nay PHP đã bổ sung thêm nhiều cú pháp mới, vì vậy mà PSR-12 ra đời như một cách để mở rộng cho PSR-2 về các cú pháp mới của PHP. Cụ thể PSR-12 là quy ước mở rộng, kế thừa và thay thế cho PSR-2.
## 2. General

### 2.1 Basic Coding Standard
Trước tiên, code phải thuân theo các nguyên tắc ở [PSR-1](./psr-1/README.md).

### 2.2 Files
Tất cả các file PHP phải kết thúc bằng một dòng trống.

Trong một file chỉ có code PHP thì không được sử dụng thẻ đóng `?>`

### 2.3 Lines
Không có hard limit cho độ dài của dòng code, tức là mỗi dòng code có thể dài bao nhiêu tùy thích.

Tuy không có giới hạn về hard limit, nhưng soft limit của mỗi dòng code là 120 ký tự. Đối với các chương trình tự động check coding convention, nếu số lượng ký tự vượt qua soft limit thì chỉ được thông báo warning (cảnh báo) chứ không được thông báo error (lỗi).

Mỗi dòng code nên nhỏ hơn 80 ký tự, nếu dài quá thì nên chia nhỏ ra thành nhiều dòng và mỗi dòng cũng nên nhỏ hơn 80 ký tự.

Mỗi dòng code không được thừa khoảng trắng ở cuối dòng.

Không được phép có nhiều hơn một câu lệnh trên mỗi dòng.

### 2.4 Indenting
Sử dụng 4 dấu cách (space) để thụt lề, không được phép sử dụng dấu tab. Nên thay đổi indent của tab bằng 4 đối với PHP.

### 2.5 Keywords and Types
Các keyword và type trong PHP phải được viết thường.

Keyword dạng rút gọn phải được sử dụng, tức là `bool` thay vì `boolean`, `int` thay vì `integer`, ...

## 3. Declare Statements, Namespace, and Import Statements

## 4. Classes, Properties, and Methods
Thuật ngữ `class` đề cập đến tất cả các `class`, `interface` và `trait`.

Khi khởi tạo một class mới, dấu () phải luôn hiện diện ngay cả khi không có đối số nào được truyền cho hàm tạo.
```php
new Foo();
```

### 4.1 Extends and Implements
Từ khóa `extends` và `implements` phải được khai báo trên cùng một dòng với tên class.

Dấu ngoặc nhọn mở phải được viết trên một dòng riêng, dấu ngoặc nhọn đóng phải được viết ở dòng tiếp theo khi kết thúc class.
```php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```

Danh sách những `interface` được `implements` có thể được viết trên nhiều dòng, với mỗi dòng sẽ được thụt lề một lần. Interface được implements đầu tiền sẽ phải được viết ở dòng tiếp theo, sau đó là mỗi interface trên một dòng.
```php
namespace Vendor\Package;
 
use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;
 
class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
```

### 4.2 Using traits
Từ khóa `use` để sử dụng trait phải được khai báo ở dòng tiếp theo của dấu ngoặc ngọn mở.

Khi mà thân `class` không khai báo gì ngoài từ khóa `use` để sử dụng `trait`, thì dấu ngoặc nhọn đóng phải nằm ở dòng tiếp theo của lệnh `use`.

Mỗi `trait` phải một từ khóa `use` và trên một dòng riêng. 

Nếu `class` có khai báo thêm, thì phải có một dòng trống ở phía sau các câu lệnh `use`.

```php
namespace Vendor\Package;
 
use Vendor\Package\FirstTrait;
use Vendor\Package\SecondTrait;
use Vendor\Package\ThirdTrait;
 
class ClassName
{
    use FirstTrait;
    use SecondTrait;
    use ThirdTrait;
    
    private $property;
}
```

### 4.3 Properties and Constants
Tất cả các thuộc tính đều phải khai báo đầy đủ tính visibility (public, protected, private)

Không được sử dụng từ khóa `var` để khai báo property

Mỗi dòng chỉ có thể khai báo một property

Thêm thuộc tính không nên sử dụng tiền tố `_` để thể hiện tính protected hay private. Hay cũng có thể nói việc thêm property bắt đầu bằng tiền tố `_` không có ý nghĩa gì cả.

Chỉ có một dấu cách giữa kiểu khai báo và tên property.

Một ví dụ đầy đủ các nguyên tắc trên:
```php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
    public static int $bar = 0;
}
```

### 4.4 Methods and Functions
Giống như property, tính visibility phải được khai báo cho mọi method.

Tên method không nên sử dụng tiền tố `_` để thể hiện tính protected hay private. Hay cũng có thể nói việc tên method bắt đầu bằng tiền tố `_` không có ý nghĩa gì cả.

Không được phép có khoảng trắng ở phía sau tên method hoặc function.

Dấu ngoặc nhọn mở ra thân function hoặc method phải được nằm trên một dòng riêng. Điều này cũng tương tự với dấu ngoặc nhọn đóng.

Không được khoảng trắng ở phía sau dấu mở ngoặc đơn, và khoảng trắng ở phía trước dấu đóng ngoặc đơn.

Đối với method:
```php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```

Đối với function:
```php
function fooBarBaz($arg1, &$arg2, $arg3 = [])
{
    // function body
}
```

### 4.5 Method and Function Arguments
Trong danh sách các tham số, không được có khoảng trắng ở trươc dấu phẩy, và phía sau dấu phẩy luôn phải có một khoảng trắng.

Các tham số mà có giá trị mặc định phải nằm ở các vị trí sau cùng trong danh sách các tham số.
```php
namespace Vendor\Package;
 
class ClassName
{
    public function foo(int $arg1, &$arg2, $arg3 = [])
    {
        // method body
    }
}
```
Danh sách các tham số có thể được viết trên nhiều dòng, mỗi dòng sẽ phải thụt lề thêm một cấp. Tham số đầu tiên phải nằm ở dòng tiếp theo, và sau đó là mỗi tham số được viết trên một dòng.

Khi tham số được viết trên nhiều dòng, dấu ngoặc đơn đóng và dấu ngoặc nhọn mở phải được đặt trên cùng một dòng, ngăn cách nhau bằng một khoảng trắng.
```php
namespace Vendor\Package;
 
class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        $arg2,
        array $arg3 = []
    ) {
        // method body
    }
}
```
Khi bạn khai báo kiểu dữ liệu trả về, thì phải có một khoảng trắng nằm giữa dấu hai chấm `:` và kiểu dữ liệu. Dấu hai chấm và kiểu dữ liệu phải nằm cùng dòng với dấu ngoặc đơn đóng.
```php
declare(strict_types=1);
 
namespace Vendor\Package;
 
class ReturnTypeVariations
{
    public function functionName(int $arg1, $arg2): string
    {
        return 'foo';
    }
 
    public function anotherFunction(
        string $foo,
        string $bar,
        int $baz
    ): string {
        return 'foo';
    }
}
```
Nếu khai bảo trả về kiểu nullable, thì không được có khoảng trắng giữa dấu hỏi chấm và kiểu dữ liệu.

Nếu sử dụng toán tử `&` trước các tham số, thì không được có khoảng trắng ở phía sau nó.
```php
declare(strict_types=1);
 
namespace Vendor\Package;
 
class ReturnTypeVariations
{
    public function functionName(?string $arg1, ?int &$arg2): ?string
    {
        return 'foo';
    }
}
```
Không được có khoảng trắng giữa dấu ba chấm ... và tên tham số:
```php
public function process(string $algorithm, ...$parts)
{
    // processing
}
```
Nếu sử dụng cả hai toán tử & và ..., thì không có khoảng trắng ở giữa chúng.
```php
public function process(string $algorithm, &...$parts)
{
    // processing
}
```
### 4.6 `abstract`, `final` và `static`
Khi sử dụng, `abstract` và `final` phải được đặt trước phần khai báo `visibility`.

Khi sử dụng, `static` phải được đặt sau phần khai báo `visibility`.
```php
namespace Vendor\Package;
 
abstract class ClassName
{
    protected static $foo;
 
    abstract protected function zim();
 
    final public static function bar()
    {
        // method body
    }
}
```
### 4.7 Method and Function Calls
Khi thực hiện lời gọi function hoặc method, không được có khoảng trắng giữa tên function/method và dấu mở ngoặc đơn, không có khoảng trắng phía sau dấu mở ngoặc đơn, và không có khoảng trắng ở phía trước dấu mở ngoặc đơn.

Với danh sách các tham số, không được phép có khoảng trắng ở phía trước dấu phẩy, và phải có một khoảng trắng ở phía sau mỗi dấu phẩy.
```php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

Danh sách các tham số có thể được viết trên nhiều dòng, với mỗi dòng sẽ phải được thù lề thêm 1 cấp. Tham số đầu tiên sẽ phải nằm ở dòng tiếp theo và sau đó là mỗi tham số trên một dòng.
```php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```
Với những lời gọi function/method có sử dụng tham số là array hoặc anonymous function, thì những tham số dạng array/anonymous function có thể được viết trên nhiều dòng, nhưng những tham số còn lại vẫn có thể viết trên một dòng.
```php
somefunction($foo, $bar, [
  // ...
], $baz);
 
$app->get('/hello/{name}', function ($name) use ($app) {
    return 'Hello ' . $app->escape($name);
});
```

## 5. Control Structures
Tổng quan về các quy tắc dành cho `control structures` (if, swtich , loop, try catch):

- Phải có một khoảng trắng phía sau từ khóa của mỗi `control structures`.
- Không được có khoảng trắng ở phía sau dấu ngoặc đơn mở.
- Không được có khoảng trắng ở phía trước dấu ngoặc đơn đóng.
- Phải có một khoảng trắng ở giữa dấu ngoặc đơn đóng và dấu ngoặc nhọn mở.
- Phần thân của `control structures` phải được thụt lề thêm một cấp.
- Phần thân của `control structures` phải nằm ở dòng tiếp theo so với dấu mở ngoặc nhọn.
- Dấu ngoặc nhọn đóng phải nằm ở dòng tiếp theo so với phần thân của `control structures`.
- Phần thân của mỗi cấu trúc điều kiện đi kèm với một cặp dấu ngoặc nhọn. Đây là tiêu chuẩn để đảm bảo tính dễ nhìn cũng như giảm thiểu lỗi khi bổ sung thêm code vào `control structures`.

Phần thân của mỗi `control structures` đi kèm với một cặp dấu ngoặc nhọn. Đây là tiêu chuẩn để đảm bảo tính dễ nhìn cũng như giảm thiểu lỗi khi bổ sung thêm code vào 'control structures'.

### 5.1 `if`, `elseif`, `else`
Cấu trúc câu lệnh `if` sẽ được trình bày như trong ví dụ sau. Bạn hãy chú ý đến các dấu ngoặc đơn, khoảng trắng và dấu ngoặc nhọn; các từ khóa như else và elseif phải được đặt dùng dòng với dấu ngoặc nhọn đóng của phần thân cấu trúc điều khiển phía trước.
```php
if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
```
Nên sử dụng `elseif` hơn là `else if`.

Biểu thức ở giữa cặp dấu ngoặc đơn có thể được viết trên nhiều dòng, với mỗi dòng sẽ được thù lề thêm một cấp. Điều kiện đầu tiên sẽ phải được viết trên dòng tiếp theo. Dấu ngoặc đơn đóng và dấu ngoặc nhọn mở phải được viết trên cùng một dòng và ngăn cách bằng một khoảng trắng.

Các toán tử `boolean` trong điều kiện phải được viết ở đầu hoặc cuối của mỗi dòng, nhưng không được phép sử dụng cả hai (lúc thì ở đầu, lúc thì ở cuối).
```php 
if (
    $expr1
    && $expr2
) {
    // if body
} elseif (
    $expr3
    && $expr4
) {
    // elseif body
}
```
Hạn chế sử dụng else.
```php 
if ($expr1) {
    // body
} 

if ($expr2) {
    // body
} 
    // body;
```

### 5.2 `switch`, `case`
Cấu trúc `switch` sẽ được trình bày như trong ví dụ sau. Bạn hãy để ý tới vị trí của các dấu ngoặc đơn, khoảng trắng và dấu ngoặc nhọn. Từ khóa `case` phải được thụt lề thêm một cấp so với từ khóa `switch`, và từ khóa `break` (hoặc từ khóa kết thúc như return) phải được thụt lề thêm một cấp so với `case`.

Phải có comment kiểu như // no break khi bạn cố ý không sử dụng `break` (hoặc các từ khóa kết thúc khác) mà phần thân của `case` vẫn có code.
```php 
<?php
 
switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```

Biểu thức ở giữa cặp dấu ngoặc đơn có thể được viết trên nhiều dòng, với mỗi dòng sẽ được thù lề thêm một cấp. Điều kiện đầu tiên sẽ phải được viết trên dòng tiếp theo. Dấu ngoặc đơn đóng và dấu ngoặc nhọn mở phải được viết trên cùng một dòng và ngăn cách bằng một khoảng trắng.

Các toán tử `boolean` trong điều kiện phải được viết ở đầu hoặc cuối của mỗi dòng, nhưng không được phép sử dụng cả hai (lúc thì ở đầu, lúc thì ở cuối).

### 5.3 `while`, `do while`
Cấu trúc `while` sẽ được trình bay như trong ví dụ sau. Bạn hãy chú tới ví trí của các dấu ngoặc đơn, khoảng trắng và dấu ngoặc nhọn nhé.
```php 
while ($expr) {
    // structure body
}
```

Biểu thức ở giữa cặp dấu ngoặc đơn có thể được viết trên nhiều dòng, với mỗi dòng sẽ được thụt lề thêm một cấp. Điều kiện đầu tiên sẽ phải được viết trên dòng tiếp theo. Dấu ngoặc đơn đóng và dấu ngoặc nhọn mở phải được viết trên cùng một dòng và ngăn cách bằng một khoảng trắng.

Các toán tử `boolean` trong điều kiện phải được viết ở đầu hoặc cuối của mỗi dòng, nhưng không được phép sử dụng cả hai (lúc thì ở đầu, lúc thì ở cuối).
```php 
while (
    $expr1
    && $expr2
) {
    // structure body
}
```

`do while` cũng tương tự:
```php 
do {
    // structure body;
} while ($expr);

do {
    // structure body;
} while (
    $expr1
    && $expr2
);
```

### 5.4 `for`
Cấu trúc `for` sẽ được trình bày như trong ví dụ sau, bạn hãy để ý tới vị trí của các dấu ngoặc đơn, khoảng trắng và dấu ngoặc nhọn nhé.
```php 
for ($i = 0; $i < 10; $i++) {
    // for body
}
```

Biểu thức trong dấu ngoặc đơn có thể được viết trên nhiều dòng, với mỗi dòng sẽ được thụt lề thêm một cấp. Biểu thức đầu tiên phải được viết ở dòng tiếp theo. Dấu ngoặc đơn đóng và dấu ngoặc nhọn mở phải được viết trên cùng một dòng và ngăn cách bằng một khoảng trắng.
```php 
for (
    $i = 0;
    $i < 10;
    $i++
) {
    // for body
}
```

### 5.5 `foreach`
Cấu trúc `foreach` sẽ được trình bày như sau, hãy để ý tới vị trí của các dấu ngoặc đơn, khoảng trắng và dấu ngoặc nhọn.
```php 
foreach ($iterable as $key => $value) {
    // foreach body
}
```

### 5.6 `try`, `catch`, `finally`
Cấu trúc `try`, `catch`, `finally` sẽ được trình bày như sau, hãy để ý tới vị trí của các dấu ngoặc đơn, khoảng trắng và dấu ngoặc nhọn.
```php 
try {
    // try body
} catch (FirstThrowableType $e) {
    // catch body
} catch (OtherThrowableType | AnotherThrowableType $e) {
    // catch body
} finally {
    // finally body
}
```

## 6. Operators
Các quy tắc kiểu cho các toán tử được nhóm theo độ hiếm (số toán hạng mà chúng lấy).

Khi có khoảng trắng được sử dụng xung quanh các toán tử, thì bạn cũng có thể sử dụng nhiều khoảng trắng để tăng tính dễ đọc cho code.

Các toán tử không được mô tả dưới đây đều không có quy ước xác định.

### 6.1. Unary operators
Toán tử increment/decrement không được có khoảng trắng giữa toán tử và toán hạng.
```php
$i++;
++$j;
```

Toán tử ép kiểu không có khoảng trắng giữa cặp dấu ngoặc đơn.
```php
$intValue = (int) $input;
```

### Binary operators
Tất cả các toán tử [arithmetic](https://www.php.net/manual/en/language.operators.arithmetic.php), [comparison](https://www.php.net/manual/en/language.operators.comparison.php), [assignment](https://www.php.net/manual/en/language.operators.assignment.php), [bitwise](https://www.php.net/manual/en/language.operators.bitwise.php), [logical](https://www.php.net/manual/en/language.operators.logical.php), [string](https://www.php.net/manual/en/language.operators.string.php), và [type](https://www.php.net/manual/en/language.operators.type.php) phía trước và phía sau phải có một khoảng trắng.
```php
if ($a === $b) {
    $foo = $bar ?? $a ?? $b;
} elseif ($a > $b) {
    $foo = $a + $b * $c;
}
```

### Ternary operators
Toán tử điều kiện phải có ít nhất một khoảng trắng xung quanh cả hai ký tự `?` và `:`
```php
$variable = $foo ? 'foo' : 'bar';
```

Khi toán hạng ở giữa được bỏ qua, thì phải tuân theo quy tắc giống như một toán tử so sánh:
```php
$variable = $foo ?: 'bar'; 
```

## 7.Closures
Closures phải được khai báo kèm theo một khoảng trắng ở phía sau từ khóa `function`, phía trước và phía sau từ khóa `use`.

Dấu ngoặc nhọn mở phải được viết trên cùng dòng, dấu ngoặc nhọn đóng thì được viết ở dòng tiếp theo so với phần thân của closure.

Không có khoảng trắng ở phía sau dấu ngoặc đơn mở, và không có khoảng trắng ở phía trước dấu ngoặc đơn đóng.

Danh sách tham số và danh sách biến không được có khoảng trắng ở trước các dấu phẩy, và phải có một khoảng trắng ở phía sau mỗi dấu phẩy.

Tham số có giá trị mặc định phải nằm ở phía sau trong danh sách các tham số.

Nếu khai báo kiểu dữ liệu trả về, thì phải tuân theo quy tắc giống như quy tắc với functions và methods; Nếu sử dụng từ khóa `use`, dấu hai chấm phải viết liền phía sau (không có khoảng trắng) dấu ngoặc đơn đóng.

Khai báo một closure chuẩn sẽ giống như ví dụ sau, hãy chú ý tới viej trí của các dấu ngoặc đơn, dấu phẩy, khoảng trắng và các dấu ngoặc nhọn:
```php
<?php
 
$closureWithArgs = function ($arg1, $arg2) {
    // body
};
 
$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};
 
$closureWithArgsVarsAndReturn = function ($arg1, $arg2) use ($var1, $var2): bool {
    // body
};
```

Danh sách tham số có thể được viết trên nhiều dòng, với mỗi dòng sẽ thụt lề vào một cấp. Tham số đầu tiên sẽ phải viết ở dòng tiếp theo, sau đó là mỗi tham số lần lượt trên một dòng.

Khi kết thúc danh sách (dù là danh sách tham số hay danh sách biến) mà viết trên nhiều dòng khác nhau, thì dấu ngoặc đơn đóng và dấu ngoặc nhọn mở phải được viết trên cùng dòng, ngăn cách nhau bằng một khoảng trắng.

Cách khai báo sẽ tương tự như ví dụ sau:
```php
<?php

$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // body
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // body
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // body
};
```

Lưu ý: các quy tắc trên cũng được áp dụng khi closure được sử dụng như là một tham số trong các lời gọi function/method
```php
<?php
 
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);
```

## 8.Anonymous Classes
Class ẩn danh phải tuân theo các quy tắc và hướng dấn như phần closures ở trên.
```php
<?php

$instance = new class {};
```

Dấu ngoặc nhọn mở có thể được viết cùng dòng với từ khóa `class` và danh sách các interfaces được `implements`. Nhưng khi danh sách các interfaces được viết trên nhiều dòng khác nhau, thì dấu ngoặc nhọn phải được viết ở dòng tiếp theo so với interface cuối cùng.
```php
<?php
 
// Brace on the same line
$instance = new class extends \Foo implements \HandleableInterface {
    // Class content
};
 
// Brace on the next line
$instance = new class extends \Foo implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // Class content
};
```

Tham khảo: https://www.php-fig.org/psr/psr-12/


