---
title: bitset 类
ms.date: 03/27/2019
f1_keywords:
- bitset/std::bitset
- bitset/std::bitset::element_type
- bitset/std::bitset::all
- bitset/std::bitset::any
- bitset/std::bitset::count
- bitset/std::bitset::flip
- bitset/std::bitset::none
- bitset/std::bitset::reset
- bitset/std::bitset::set
- bitset/std::bitset::size
- bitset/std::bitset::test
- bitset/std::bitset::to_string
- bitset/std::bitset::to_ullong
- bitset/std::bitset::to_ulong
- bitset/std::bitset::reference
helpviewer_keywords:
- std::bitset [C++]
- std::bitset [C++], element_type
- std::bitset [C++], all
- std::bitset [C++], any
- std::bitset [C++], count
- std::bitset [C++], flip
- std::bitset [C++], none
- std::bitset [C++], reset
- std::bitset [C++], set
- std::bitset [C++], size
- std::bitset [C++], test
- std::bitset [C++], to_string
- std::bitset [C++], to_ullong
- std::bitset [C++], to_ulong
- std::bitset [C++], reference
ms.assetid: 28b86964-87b4-429c-8124-b6c251b6c50b
ms.openlocfilehash: 2337a5e8355006ef2c05874b9e3e46b469c41beb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243347"
---
# <a name="bitset-class"></a>bitset 类

介绍一种类型的对象，该对象存储由固定数量的位构成的序列，这些位提供一种紧凑方式来保留一组项或条件的标志。 bitset 类支持对 bitset 类型的对象执行操作，此类对象包含位集合并提供对每一个位的定时访问。

## <a name="syntax"></a>语法

```cpp
template <size_t N>
class bitset
```

### <a name="parameters"></a>参数

*N*\
类型的非零整数 bitset 对象中指定的位数`size_t`必须在编译时已知的。

## <a name="remarks"></a>备注

与类似的 [vector\<bool> 类](../standard-library/vector-bool-class.md)不同，bitset 类没有迭代器，并且不是 C++ 标准库容器。 它与 vector\<bool> 的不同之处还在于它有某个特定大小，该大小在编译时根据声明 **bitset\<N\>** 时由模板参数 *N* 指定的大小确定并固定。

如果某个位的值为 1，则该位已设置；如果其值为 0，则该位已重置。 翻转或反转某个位就是将其值从 1 更改到 0 或从 0 到 1。 bitset 中的 *N* 个位由从 0 到 *N* - 1 的整数值索引，其中 0 索引第一个位的位置，*N* - 1 索引最后一个位的位置。

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[bitset](#bitset)|构造 `bitset\<N>` 类的对象并将位初始化为零、某个指定值或从字符串中的字符获取的值。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[element_type](#element_type)|数据类型的同义词的类型**bool** ，可以用于引用中的元素位`bitset`。|

### <a name="functions"></a>函数

|||
|-|-|
|[all](#all)|在此测试的所有位`bitset`以确定它们是否都设置为**true**。|
|[any](#any)|成员函数测试序列中是否有任何位设置为 1。|
|[计数](#count)|成员函数返回位序列中设置的位数。|
|[flip](#flip)|反转 `bitset` 中的所有位的值或反转位于指定位置的单个位。|
|[none](#none)|测试 `bitset` 对象中是否不存在任何已设置为 1 的位。|
|[reset](#reset)|将 `bitset` 中的所有位重置为 0 或将位于指定位置的位重置为 0。|
|[set](#set)|将 `bitset` 中的所有位设置为 1 或将位于指定位置的位设置为 1。|
|size[](#size)|返回 `bitset` 对象中的位数。|
|[test](#test)|测试 `bitset` 中指定位置处的位是否设置为 1。|
|[to_string](#to_string)|将 `bitset` 对象转换为字符串表示形式。|
|[to_ullong](#to_ullong)|返回中的位值的总和`bitset`作为**无符号长长**。|
|[to_ulong](#to_ulong)|将转换`bitset`对象传递给**无符号长**会产生包含如果用于初始化的位序列`bitset`。|

### <a name="classes"></a>类

|||
|-|-|
|[reference](#reference)|一个代理类，它提供对 `bitset`（用于将单个位作为 `bitset` 类的 `operator[]` 的帮助程序类进行访问和操作）中包含的位的引用。|

### <a name="operators"></a>运算符

|||
|-|-|
|[operator!=](#op_neq)|测试目标 `bitset` 是否与指定的 `bitset` 不相等。|
|[operator&=](#op_and_eq)|使用逻辑 `AND` 操作执行位组的按位组合。|
|[operator<<](#op_lshift)|将 `bitset` 中的位移动到左侧指定数目的位置并将结果返回到新的 `bitset`。|
|[operator<<=](#op_lshift_eq)|将 `bitset` 中的位移动到左侧指定数目的位置并将结果返回到目标 `bitset`。|
|[operator==](#op_eq_eq)|测试目标 `bitset` 是否与指定的 `bitset` 相等。|
|[operator>>](#op_rshift)|将 `bitset` 中的位移动到右侧指定数目的位置并将结果返回到新 `bitset`。|
|[operator>>=](#op_rshift_eq)|将 `bitset` 中的位移动到右侧指定数目的位置并将结果返回到目标 `bitset`。|
|[operator&#91;&#93;](#op_at)|如果 `bitset` 可修改，则返回对 `bitset` 中指定位置处的位的引用；否则返回该位置处的位值。|
|[operator^=](#op_xor_eq)|使用独占 `OR` 操作执行位组的按位组合。|
|[operator&#124;=](#op_or_eq)|使用非独占 `OR` 操作执行位组的按位组合。|
|[operator~](#op_not)|反转目标 `bitset` 中的所有位并返回结果。|

### <a name="structures"></a>结构

|||
|-|-|
|[hash](#hash)||

### <a name="all"></a> 所有

测试此位组中的所有位以确定它们是否都设置为 true。

```cpp
bool all() const;
```

#### <a name="return-value"></a>返回值

如果此集中的所有位都为 true，则返回 true。 如果一个或多个位为 false，则返回 **false**。

### <a name="any"></a> 任何

测试序列中是否有任何位设置为 1。

```cpp
bool any() const;
```

#### <a name="return-value"></a>返回值

如果位组中有任何位设置为 1，则为 **true**；如果所有位均为 0，则为 **false**。

#### <a name="example"></a>示例

```cpp
// bitset_any.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "The original bitset b1( 6 ) is: ( "<< b1 << " )"
        << endl;

   b = b1.any ( );

   if ( b )
      cout << "At least one of the bits in bitset is set to 1."
           << endl;
   else
      cout << "None of the bits in bitset are set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );

   cout << "The reset bitset is: ( "<< b1 << " )"
        << endl;

   rb = rb1.any ( );

   if ( rb )
      cout << "At least one of the bits in the reset bitset "
           << "are set to 1." << endl;
   else
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
}
```

```Output
The original bitset b1( 6 ) is: ( 00110 )
At least one of the bits in bitset is set to 1.
The reset bitset is: ( 00000 )
None of the bits in bitset b1 are set to 1.
```

### <a name="bitset"></a> 位组

构造 `bitset\<N>` 类的对象并将位初始化为零、某个指定值或从字符串中的字符获取的值。

```cpp
bitset();

bitset(
    unsigned long long val);

explicit bitset(
    const char* _CStr);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos = 0);

template <class CharType,
    class Traits,
    class Allocator>
explicit bitset(
    const basic_string<CharType, Traits, Allocator>& str,
    typename basic_string<CharType, Traits, Allocator>::size_type _Pos,
    typename basic_string<CharType, Traits, Allocator>::size_type count,
    CharType _Zero = CharType ('0'),
    CharType _One = CharType ('1'));
```

#### <a name="parameters"></a>参数

*val*\
使用其二进制表示法初始化正在构造的位组中的位的无符号整数。

*str*\
由 0 和 1 组成的用于初始化位组位值的字符串。

*_CStr*\
由 0 和 1 组成的用于初始化位组位值的 C 类型字符串。

*_Pos*\
字符串中的字符位置，从左到右计数，且从 0 开始，用于初始化位组中的第一位。

*计数*\
字符串中的字符数，用于提供位组中位的初始值。

*_Zero*\
用于表示 0 的字符。 默认值为“0”。

*（_o)* \
用于表示 1 的字符。 默认值为“1”。

#### <a name="remarks"></a>备注

可使用三个构造函数构造 `bitset\<N>` 类的对象：

- 第一个构造函数不接受参数，构造 `bitset\<N>` 类的对象并将所有 N 位初始化为默认值 0。

- 第二个构造函数将构造类的对象`bitset\<N>`并将位初始化使用单个**无符号长长**参数。

- 第三个构造函数构造 `bitset\<N>` 类的对象，并将 N 位初始化为与由 0 和 1 组成的 c 类型字符字符串中提供的字符相对应的值。 不通过将字符串转换为字符串类型 `bitset<5> b5("01011");` 来调用构造函数

还提供了两个构造函数模板：

- 第一个构造函数模板构造 `bitset\<N>` 类的对象并初始化由 0 和 1 组成的字符串中提供的字符中的位。 如果字符串的任何字符为非 0 或非 1，则该构造函数引发 [invalid argument](../standard-library/invalid-argument-class.md) 类的对象。 如果指定的位置 ( *_Pos*) 构造函数将引发类的对象是字符串的长度超出[out_of_range](../standard-library/out-of-range-class.md)。 该构造函数只设置位置 `_Pos + j` 处的字符串中的字符为 1 的位组中 *j* 位置处的位。 默认情况下 *_Pos*为 0。

- 第二个构造函数模板类似于第一个，但包含一个附加参数 (*计数*)，用于指定要初始化位数。 它还具有两个可选参数 *_Zero*并 *（_o)* ，这表示中的哪些字符*str*转译为表示 0 位或 1 的位，分别是。

#### <a name="example"></a>示例

```cpp
// bitset_bitset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   // Using the default constructor
   using namespace std;
   bitset<2> b0;
   cout << "The set of bits in bitset<2> b0 is: ( "
        << b0 << " )." << endl;

   // Using the second member function
   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1( 6 ) is: ( "
        << b1 << " )." << endl;

   // The template parameter N can be an expresssion
   bitset< 2 * sizeof ( int ) > b2;
   cout << "The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( "
        << b2 << " )." << endl;

   // The base two representation will be truncated
   // if its length exceeds the size of the bitset
   bitset<3> b3 ( 6 );
   cout << "The set of bits in bitset<3> b3( 6 ) is ( "
        << b3 << " )." << endl;

   // Using a c-style string to initialize the bitset
    bitset<7> b3andahalf ( "1001001" );
    cout << "The set of bits in bitset<7> b3andahalf ( \"1001001\" )"
         << " is ( " << b3andahalf << " )." << endl;

   // Using the fifth member function with the first parameter
   string bitval4 ( "10011" );
   bitset<5> b4 ( bitval4 );
   cout << "The set of bits in bitset<5> b4( bitval4 ) is ( "
        << b4 << " )." << endl;

   // Only part of the string may be used for initialization

   // Starting at position 3 for a length of 6 (100110)
   string bitval5 ("11110011011");
   bitset<6> b5 ( bitval5, 3, 6 );
   cout << "The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( "
        << b5 << " )." << endl;

   // The bits not initialized with part of the string
   // will default to zero
   bitset<11> b6 ( bitval5, 3, 5 );
   cout << "The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( "
        << b6 << " )." << endl;

   // Starting at position 2 and continue to the end of the string
   bitset<9> b7 ( bitval5, 2 );
   cout << "The set of bits in bitset<9> b7( bitval, 2 ) is ( "
        << b7 << " )." << endl;
}
```

```Output
The set of bits in bitset<2> b0 is: ( 00 ).
The set of bits in bitset<5> b1( 6 ) is: ( 00110 ).
The set of bits in bitset<2 * sizeof ( int ) > b2 is: ( 00000000 ).
The set of bits in bitset<3> b3( 6 ) is ( 110 ).
The set of bits in bitset<5> b4( bitval4 ) is ( 10011 ).
The set of bits in bitset<11> b5( bitval, 3, 6 ) is ( 100110 ).
The set of bits in bitset<11> b6( bitval5, 3, 5 ) is ( 00000010011 ).
The set of bits in bitset<9> b7( bitval, 2 ) is ( 110011011 ).
```

### <a name="count"></a> 计数

返回位序列中设置的位数。

```cpp
size_t count() const;
```

#### <a name="return-value"></a>返回值

位序列中设置的位数。

#### <a name="example"></a>示例

```cpp
// bitset_count.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
    using namespace std;

    bitset<5> b1(4);

    cout << "The collection of bits in the original bitset is: ( "
         << b1 << " )" << endl;

    size_t i;
    i = b1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << i << "." << endl;

    bitset<5> fb1;
    fb1 = b1.flip();

    cout << "The collection of flipped bits in the modified bitset "
         << "is: ( " << b1 << " )" << endl;

    size_t ii;
    ii = fb1.count();
    cout << "The number of bits in the bitset set to 1 is: "
         << ii << "." << endl;
}
```

```Output
The collection of bits in the original bitset is: ( 00100 )
The number of bits in the bitset set to 1 is: 1.
The collection of flipped bits in the modified bitset is: ( 11011 )
The number of bits in the bitset set to 1 is: 4.
```

### <a name="element_type"></a> element_type

数据类型的同义词的类型**bool** ，可以用于引用位组中的元素位。

```cpp
typedef bool element_type;
```

#### <a name="example"></a>示例

```cpp
// bitset_elem_type.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<3> b1 ( 2 );
   cout << "Original bitset b1(6) is: ( "<< b1 << " )"
        << endl;

   //Compare two ways to reference bits in a bitset
   bool b;
   bitset<5>::element_type e;

   b = b1.test ( 2 );
   if ( b )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
   b1[2] = 1;
   cout << "Bitset b1 modified by b1[2] = 1 is: ( "<< b1 << " )"
        << endl;

   e = b1.test ( 2 );
   if ( e )
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 1." << endl;
   else
      cout << "The bit at position 2 of bitset b1"
           << "has a value of 0." << endl;
}
```

```Output
Original bitset b1(6) is: ( 010 )
The bit at position 2 of bitset b1has a value of 0.
Bitset b1 modified by b1[2] = 1 is: ( 110 )
The bit at position 2 of bitset b1has a value of 1.
```

### <a name="flip"></a> 翻转

反转位组中的所有位的值或反转位于指定位置的单个位。

```cpp
bitset\<N>& flip();
bitset\<N>& flip(size_t _Pos);
```

#### <a name="parameters"></a>参数

*_Pos*\
要将其值反转的位的位置。

#### <a name="return-value"></a>返回值

对其调用了成员函数且经过修改的位组副本。

#### <a name="remarks"></a>备注

第二个成员函数将引发[out_of_range](../standard-library/out-of-range-class.md)异常指定为参数的位置是否大于大小*N*的**bitset\<** *N* **>** 其位已经过反转。

#### <a name="example"></a>示例

```cpp
// bitset_flip.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 6 );

   cout << "The collection of bits in the original bitset is: ( "
        << b1 << " )" << endl;

   bitset<5> fb1;
   fb1 = b1.flip ( );

   cout << "After flipping all the bits, the bitset becomes: ( "
        << fb1 << " )" << endl;

   bitset<5> f3b1;
   f3b1 = b1.flip ( 3 );

   cout << "After flipping the fourth bit, the bitset becomes: ( "
        << f3b1 << " )" << endl << endl;

   bitset<5> b2;
   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b2.flip(i);
      cout << b2 << "  The bit flipped is in position "
           << i << ".\n";
   }
}
```

```Output
The collection of bits in the original bitset is: ( 00110 )
After flipping all the bits, the bitset becomes: ( 11001 )
After flipping the fourth bit, the bitset becomes: ( 10001 )

00001  The bit flipped is in position 0.
00011  The bit flipped is in position 1.
00111  The bit flipped is in position 2.
01111  The bit flipped is in position 3.
11111  The bit flipped is in position 4.
```

### <a name="hash"></a> 哈希

```cpp
template <class T> struct hash;
template <size_t N> struct hash<bitset<N>>;
```

### <a name="none"></a> 无

测试位组对象中是否不存在任何已设置为 1 的位。

```cpp
bool none() const;
```

#### <a name="return-value"></a>返回值

如果位组中不存在任何已设置为 1 的位则为 **true**；如果至少有一位已设置为 1 则为 **false**。

#### <a name="example"></a>示例

```cpp
// bitset_none.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   bool b, rb;

   cout << "Original bitset b1(6) is: ( " << b1 << " )"
        << endl;

   b = b1.none ( );

   if ( b )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;

   bitset<5> rb1;
   rb1 = b1.reset ( );
   rb = rb1.none ( );
   if ( rb )
      cout << "None of the bits in bitset b1 are set to 1."
           << endl;
   else
      cout << "At least one of the bits in bitset b1 is set to 1."
           << endl;
}
```

```Output
Original bitset b1(6) is: ( 00110 )
At least one of the bits in bitset b1 is set to 1.
None of the bits in bitset b1 are set to 1.
```

### <a name="op_neq"></a> 运算符 ！ =

测试目标位组是否与指定的位组不相等。

```cpp
bool operator!=(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>参数

*右侧*\
要与目标位组比较是否不相等的位组。

#### <a name="return-value"></a>返回值

如果两个位组不同则为 **true**；如果相同则为 **false**。

#### <a name="remarks"></a>备注

位组必须大小相同才能由成员运算符函数测试是否不相等。

#### <a name="example"></a>示例

```cpp
// bitset_op_NE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 != b2 )
      cout << "Bitset b1 is different from bitset b2." << endl;
   else
      cout << "Bitset b1 is the same as bitset b2." << endl;

   if ( b1 != b3 )
      cout << "Bitset b1 is different from bitset b3." << endl;
   else
      cout << "Bitset b1 is the same as bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 != b4 )
   //   cout << "Bitset b1 is different from bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="op_and_eq"></a> 运算符&amp;=

使用逻辑 `AND` 操作执行位组的按位组合。

```cpp
bitset\<N>& operator&=(const bitset\<N>& right);
```

#### <a name="parameters"></a>参数

*右侧*\
要与目标位组按位组合的位组。

#### <a name="return-value"></a>返回值

修改的目标位组的按位而得出的`AND`位组指定为参数的操作。

#### <a name="remarks"></a>备注

组合的两个位`AND`运算符返回**true**如果每位均为 true; 否则，他们的组合返回**false**。

位组必须大小相同才能与按位合并`AND`运算符由成员运算符函数。

#### <a name="example"></a>示例

```cpp
// bitset_op_bitwise.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 &= b2;
   cout << "After bitwise AND combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset is unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 &= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise AND combination,
the target bitset b1 becomes:   ( 00011 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_lshift"></a> 运算符\<\<

将位组中的位向左侧移动指定数目的位置并将结果返回到新的位组。

```cpp
bitset\<N> operator<<(size_t _Pos) const;
```

#### <a name="parameters"></a>参数

*_Pos*\
位组中的位要向左侧移动的位置数目。

#### <a name="return-value"></a>返回值

将位向左侧移动所需数目的位置后的修改位组。

#### <a name="remarks"></a>备注

成员运算符函数返回 **bitset**( **\*this**) **<<= pos,** ，其中 [<<=](#op_lshift_eq) 将位组中的位向左侧移动指定数目的位置并将结果返回到目标位组。

#### <a name="example"></a>示例

```cpp
// bitset_op_LS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << " the bitset b2 is: ( "<< b2 << " )."
        << endl;

   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << " the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

### <a name="op_lshift_eq"></a> 运算符&lt;&lt;=

将位组中的位向左侧移动指定数目的位置并将结果返回到目标位组。

```cpp
bitset\<N>& operator<<=(size_t _Pos);
```

#### <a name="parameters"></a>参数

*_Pos*\
位组中的位要向左侧移动的位置数目。

#### <a name="return-value"></a>返回值

经过修改的目标位组，以便已将位向左侧移动所需数目的位置。

#### <a name="remarks"></a>备注

如果不存在要移动到此位置的元素，则函数将位清除为 0 值。

#### <a name="example"></a>示例

```cpp
// bitset_op_LSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;
   b1 <<= 2;
   cout << "After shifting the bits 2 positions to the left,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the target bitset b1 becomes: ( 11100 ).
```

### <a name="op_eq_eq"></a> 运算符 = =

测试目标位组是否与指定的位组相等。

```cpp
bool operator==(const bitset\<N>& right) const;
```

#### <a name="parameters"></a>参数

*右侧*\
要与目标位组比较是否相等的位组。

#### <a name="return-value"></a>返回值

如果两个位组相同则为 **true**；如果不同则为 **false**。

#### <a name="remarks"></a>备注

位组必须大小相同才能由成员运算符函数测试是否相等。

#### <a name="example"></a>示例

```cpp
// bitset_op_EQ.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 7 );
   bitset<5> b3 ( 2 );
   bitset<4> b4 ( 7 );

   if ( b1 == b2 )
      cout << "Bitset b1 is the same as bitset b2." << endl;
   else
      cout << "Bitset b1 is different from bitset b2." << endl;

   if ( b1 == b3 )
      cout << "Bitset b1 is the same as bitset b3." << endl;
   else
      cout << "Bitset b1 is different from bitset b3." << endl;

   // This would cause an error because bitsets must have the
   // same size to be tested
   // if ( b1 == b4 )
   //   cout << "Bitset b1 is the same as bitset b4." << endl;
   // else
   //   cout << "Bitset b1 is different from bitset b4." << endl;
}
```

```Output
Bitset b1 is the same as bitset b2.
Bitset b1 is different from bitset b3.
```

### <a name="op_rshift"></a> 运算符&gt;&gt;

将位组中的位向右侧移动指定数目的位置并将结果返回到新的位组。

```cpp
bitset\<N> operator>>(size_t _Pos) const;
```

#### <a name="parameters"></a>参数

*_Pos*\
位组中的位要向右侧移动的位置数目。

#### <a name="return-value"></a>返回值

新的位组，其中已相对于目标位组将位向右侧移动所需数目的位置。

#### <a name="example"></a>示例

```cpp
// bitset_op_RS.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   cout << "The bitset b1 is: ( "<< b1 << " )." << endl;

   bitset<5> b2;
   b2 = b1 << 2;

   cout << "After shifting the bits 2 positions to the left,\n"
        << "the bitset b2 is: ( "<< b2 << " )."
        << endl;
   bitset<5> b3 = b2 >> 1;

   cout << "After shifting the bits 1 position to the right,\n"
        << "the bitset b3 is: ( " << b3 << " )."
        << endl;
}
```

```Output
The bitset b1 is: ( 00111 ).
After shifting the bits 2 positions to the left,
the bitset b2 is: ( 11100 ).
After shifting the bits 1 position to the right,
the bitset b3 is: ( 01110 ).
```

### <a name="op_rshift_eq"></a> 运算符&gt;&gt;=

将位组中的位向右侧移动指定数目的位置并将结果返回到目标位组。

```cpp
bitset\<N>& operator>>=(size_t _Pos);
```

#### <a name="parameters"></a>参数

*_Pos*\
位组中的位要向右侧移动的位置数目。

#### <a name="return-value"></a>返回值

经过修改的目标位组，以便已将位向右侧移动所需数目的位置。

#### <a name="remarks"></a>备注

如果不存在要移动到此位置的元素，则函数将位清除为 0 值。

#### <a name="example"></a>示例

```cpp
// bitset_op_RSE.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 28 );
   cout << "The target bitset b1 is: ( "<< b1 << " )." << endl;

   b1 >>= 2;
   cout << "After shifting the bits 2 positions to the right,\n"
        << "the target bitset b1 becomes: ( "<< b1 << " )."
        << endl;
}
```

```Output
The target bitset b1 is: ( 11100 ).
After shifting the bits 2 positions to the right,
the target bitset b1 becomes: ( 00111 ).
```

### <a name="op_at"></a> operator]

如果位组可修改，则返回对位组中指定位置处的位的引用；否则返回该位置处的位值。

```cpp
bool operator[](size_t _Pos) const;
reference operator[](size_t _Pos);
```

#### <a name="parameters"></a>参数

*_Pos*\
位在位组内所处的位置。

#### <a name="remarks"></a>备注

在构建过程中将 [\_ITERATOR\_DEBUG\_LEVEL](../standard-library/iterator-debug-level.md) 定义为 1 或 2时，如果尝试访问位组边界以外的元素，则可执行文件中将发生运行时错误。 有关详细信息，请参阅[经过检查的迭代器](../standard-library/checked-iterators.md)。

#### <a name="example"></a>示例

```cpp
// bitset_op_REF.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bool b;
   bitset<5> b1 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;

   int i;
   for ( i = 0 ; i <= 4 ; i++ )
   {
      b = b1[ i ];
      cout << "  The bit in position "
           << i << " is " << b << ".\n";
   }
}
```

### <a name="op_xor_eq"></a> 运算符 ^ =

使用独占 `OR` 操作执行位组的按位组合。

```cpp
bitset\<N>& operator^=(const bitset\<N>& right);
```

#### <a name="parameters"></a>参数

*右侧*\
要与目标位组按位组合的位组。

#### <a name="return-value"></a>返回值

将位组指定为参数，由按位异 `OR` 操作生成的经过修改的目标位组。

#### <a name="remarks"></a>备注

如果至少一位，但不是所有位为 **true**，则由异 **OR** 运算符组合的两个位返回 **true**；否则，它们的组合返回 **false**。

位组必须大小相同才能由成员运算符函数使用异 `OR` 运算符按位组合。

#### <a name="example"></a>示例

```cpp
// bitset_op_bitwiseOR.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;
   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 ^= b2;
   cout << "After bitwise exclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise exclusive OR combination,
the target bitset b1 becomes:   ( 01100 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_or_eq"></a> 运算符&#124;=

使用非独占 `OR` 操作执行位组的按位组合。

```cpp
bitset\<N>& operator|=(const bitset\<N>& right);
```

#### <a name="parameters"></a>参数

*右侧*\
要与目标位组按位组合的位组。

#### <a name="return-value"></a>返回值

将位组指定为参数，由按位非独占 `OR` 操作生成的经过修改的目标位组。

#### <a name="remarks"></a>备注

如果至少一位为 **true**，则由非独占 `OR` 运算符组合的两个位返回 **true**；如果两个位均为 **false**，则它们的组合返回 **false**。

位组必须大小相同才能由成员运算符函数使用非独占 `OR` 运算符按位组合。

#### <a name="example"></a>示例

```cpp
// bitset_op_BIO.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2 ( 11 );
   bitset<4> b3 ( 7 );

   cout << "The target bitset b1 is:    ( "<< b1 << " )." << endl;
   cout << "The parameter bitset b2 is: ( "<< b2 << " )." << endl;
   cout << endl;

   b1 |= b2;
   cout << "After bitwise inclusive OR combination,\n"
        << "the target bitset b1 becomes:   ( "<< b1 << " )."
        << endl;

   // Note that the parameter-specified bitset in unchanged
   cout << "The parameter bitset b2 remains: ( "<< b2 << " )."
        << endl;

   // The following would cause an error because the bisets
   // must be of the same size to be combined
   // b1 |= b3;
}
```

```Output
The target bitset b1 is:    ( 00111 ).
The parameter bitset b2 is: ( 01011 ).

After bitwise inclusive OR combination,
the target bitset b1 becomes:   ( 01111 ).
The parameter bitset b2 remains: ( 01011 ).
```

### <a name="op_not"></a> 运算符 ~

反转目标位组中的所有位并返回结果。

```cpp
bitset\<N> operator~() const;
```

#### <a name="return-value"></a>返回值

已针对目标位组反转其所有位的位组。

#### <a name="example"></a>示例

```cpp
// bitset_op_invert.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <bitset>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );
   bitset<5> b2;
   b2 = ~b1;

   cout << "Bitset b1 is: ( "<< b1 << " )." << endl;
   cout << "Bitset b2 = ~b1 is: ( "<< b2 << " )." << endl;

   // These bits could also be flipped using the flip member function
   bitset<5> b3;
   b3 = b1.flip( );
   cout << "Bitset b3 = b1.flip( ) is: ( "<< b2 << " )." << endl;
}
```

```Output
Bitset b1 is: ( 00111 ).
Bitset b2 = ~b1 is: ( 11000 ).
Bitset b3 = b1.flip( ) is: ( 11000 ).
```

### <a name="reference"></a> 引用

一个代理类，它提供对位组（用于将单个位作为位组类的 `operator[]` 的帮助程序类进行访问和操作）中包含的位的引用。

```cpp
class reference {
   friend class bitset\<N>;
public:
   reference& operator=(bool val);
   reference& operator=(const reference& _Bitref);
   bool operator~() const;
   operator bool() const;
   reference& flip();
};
```

#### <a name="parameters"></a>参数

*val*\
类型的对象的值**bool**要分配给有点位组中。

*_Bitref*\
窗体 *x [ i ]* 对位组 *x* 中 *i* 位置上的位的引用。

#### <a name="return-value"></a>返回值

由类引用的第一个、第二个和第五个成员函数的自变量位置指定的对位组中的位的引用，并且由 **true** 或 **false** 来反映类引用的第三个和第四个成员函数的位组中经过修改的位的值。

#### <a name="remarks"></a>备注

`reference` 类仅作为位组 `operator[]` 的帮助程序类存在。 成员类描述可以访问位组中的单个位的对象。 让*b*是类型的对象**bool**， *x*并*y*类型的对象**bitset\<** *N* **>** ，并且*我*并*j*中对此类对象的有效位置。 表示法 *x [i]* 引用位组 *x* 中的 *i* 位置上的位。 `reference` 类的成员函数按顺序提供以下操作：

|操作|定义|
|---------------|----------------|
|*x*[*i*] = *b*|存储**bool**值*b*位位置*我*位组中*x*。|
|*x*[*i*] = *y*[*j*]|将位 *y*[ *j*] 的值存储在位组 *x* 中的位位置 *i* 上。|
|*b* = ~ *x*[*i*]|将位的翻转的值存储*x*[*我*] 中**bool** *b*。|
|*b* = *x*[*i*]|将存储的位值*x*[*我*] 中**bool** *b*。|
|*x*[*i*]. `flip`( )|将位 *x*[ *i*] 的翻转值存储在 *x* 中的位位置 *i* 后面。|

#### <a name="example"></a>示例

```cpp
// bitset_reference.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 2 );
   bitset<5> b2 ( 6 );
   cout << "The initialized bitset<5> b1( 2 ) is: ( "<< b1 << " )."
        << endl;
   cout << "The initialized bitset<5> b2( 6 ) is: ( "<< b2 << " )."
        << endl;

   // Example of x [i] = b storing bool b at bit position i
   // in bitset x
   b1[ 0 ] = true;
   cout << "The bitset<5> b1 with the bit at position 0 set to 1"
        << "is: ( "<< b1 << " )" << endl;

   // Example of x [i] = y [j] storing the bool value of the
   // bit at position j in bitset y at bit position i in bitset x
   b2 [4] = b1 [0];      // b1 [0] = true
   cout << "The bitset<5> b2 with the bit at position 4 set to the "
        << "value\nof the bit at position 0 of the bit in "
        << "bitset<5> b1 is: ( "<<  b2  << " )" << endl;

   // Example of b = ~x [i] flipping the value of the bit at
   // position i of bitset x and storing the value in an
   // object b of type bool
   bool b = ~b2 [4];      // b2 [4] = false
   if ( b )
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = ~b2 [4] "
           << "of type bool is false." << endl;

   // Example of b = x [i] storing the value of the bit at
   // position i of bitset x in the object b of type bool
   b = b2 [4];
   if ( b )
      cout << "The value of the object b = b2 [4] "
           << "of type bool is true." << endl;
   else
      cout << "The value of the object b = b2 [4] "
           << "of type bool is false." << endl;

   // Example of x [i] . flip ( ) toggling the value of the bit at
   // position i of bitset x
   cout << "Before flipping the value of the bit at position 4 in "
        << "bitset b2,\nit is ( "<<  b2  << " )." << endl;
   b2 [4].flip( );
   cout << "After flipping the value of the bit at position 4 in "
        << "bitset b2,\nit becomes ( "<<  b2  << " )." << endl;
   bool c;
   c = b2 [4].flip( );
   cout << "After a second flip, the value of the position 4 "
        << "bit in b2 is now: " << c << ".";
}
```

```Output
The initialized bitset<5> b1( 2 ) is: ( 00010 ).
The initialized bitset<5> b2( 6 ) is: ( 00110 ).
The bitset<5> b1 with the bit at position 0 set to 1 is: ( 00011 )
The bitset<5> b2 with the bit at position 4 set to the value
of the bit at position 0 of the bit in bitset<5> b1 is: ( 10110 )
The value of the object b = ~b2 [4] of type bool is false.
The value of the object b = b2 [4] of type bool is true.
Before flipping the value of the bit at position 4 in bitset b2,
it is ( 10110 ).
After flipping the value of the bit at position 4 in bitset b2,
it becomes ( 00110 ).
After a second flip, the value of the position 4 bit in b2 is now: 1.
```

### <a name="reset"></a> 重置

将位组中的所有位重置为 0 或将位于指定位置的位重置为 0。

```cpp
bitset\<N>& reset();
bitset\<N>& reset(size_t _Pos);
```

#### <a name="parameters"></a>参数

*_Pos*\
要重置为 0 的位组中的位的位置。

#### <a name="return-value"></a>返回值

对其调用成员函数的位组副本。

#### <a name="remarks"></a>备注

如果指定的位置大于位组的大小，则第二个成员函数引发 [out_of_range](../standard-library/out-of-range-class.md) 异常。

#### <a name="example"></a>示例

```cpp
// bitset_reset.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 13 );
   cout << "The set of bits in bitset<5> b1(13) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1r3;
   b1r3 = b1.reset( 2 );
   cout << "The collecion of bits obtained from resetting the\n"
        << "third bit of bitset b1 is: ( "<< b1r3 << " )"
        << endl;

   bitset<5> b1r;
   b1r = b1.reset( );
   cout << "The collecion of bits obtained from resetting all\n"
        << "the elements of the bitset b1 is: ( "<< b1r << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(13) is: ( 01101 )
The collecion of bits obtained from resetting the
third bit of bitset b1 is: ( 01001 )
The collecion of bits obtained from resetting all
the elements of the bitset b1 is: ( 00000 )
```

### <a name="set"></a> 设置

将位组中的所有位设置为 1 或将位于指定位置的位设置为 1。

```cpp
bitset\<N>& set();

bitset\<N>& set(
    size_t _Pos,
    bool val = true);
```

#### <a name="parameters"></a>参数

*_Pos*\
要设置为分配值的位组中的位的位置。

*val*\
要向指定位置的位分配的值。

#### <a name="return-value"></a>返回值

对其调用成员函数的位组副本。

#### <a name="remarks"></a>备注

如果指定的位置大于位组的大小，则第二个成员函数引发 [out_of_range](../standard-library/out-of-range-class.md) 异常。

#### <a name="example"></a>示例

```cpp
// bitset_set.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 6 );
   cout << "The set of bits in bitset<5> b1(6) is: ( "<< b1 << " )"
        << endl;

   bitset<5> b1s0;
   b1s0 = b1.set( 0 );
   cout << "The collecion of bits obtained from setting the\n"
        << "zeroth bit of bitset b1 is: ( "<< b1s0 << " )"
        << endl;

   bitset<5> bs1;
   bs1 = b1.set( );
   cout << "The collecion of bits obtained from setting all the\n"
        << "elements of the bitset b1 is: ( "<< bs1 << " )"
        << endl;
}
```

```Output
The set of bits in bitset<5> b1(6) is: ( 00110 )
The collecion of bits obtained from setting the
zeroth bit of bitset b1 is: ( 00111 )
The collecion of bits obtained from setting all the
elements of the bitset b1 is: ( 11111 )
```

### <a name="size"></a> 大小

返回 bitset 对象中的位数。

```cpp
size_t size() const;
```

#### <a name="return-value"></a>返回值

bitset\<N> 中 *N* 的位数。

#### <a name="example"></a>示例

```cpp
// bitset_size.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main()
{
    using namespace std;

    bitset<5> b1(6);
    size_t i;

    cout << "The set of bits in bitset<5> b1( 6 ) is: ( "<< b1 << " )"
         << endl;

    i = b1.size();

    cout << "The number of bits in bitset b1 is: " << i << "."
         << endl;
}
```

```Output
The set of bits in bitset<5> b1( 6 ) is: ( 00110 )
The number of bits in bitset b1 is: 5.
```

### <a name="test"></a> 测试

测试位组中指定位置处的位是否设置为 1。

```cpp
bool test(size_t _Pos) const;
```

#### <a name="parameters"></a>参数

*_Pos*\
要测试其值的位组中位的位置。

#### <a name="return-value"></a>返回值

如果将参数位置指定的位设置为 1 则为 **true**；否则为 **false**。

#### <a name="remarks"></a>备注

成员函数引发 [out_of_range](../standard-library/out-of-range-class.md)

### <a name="to_string"></a> to_string

将位组对象转换为字符串表示形式。

```
template <class charT = char, class traits = char_traits<charT>, class Allocator = allocator<charT> >
   basic_string<charT, traits, Allocator> to_string(charT zero = charT('0'), charT one = charT('1')) const;
```

#### <a name="return-value"></a>返回值

类的字符串对象`basic_string`，其中每个设置位的位组中具有相应的字符为 1，0 的字符的位是取消设置。

#### <a name="example"></a>示例

```cpp
// bitset_to_string.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>
#include <string>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   string s1;
   s1 =  b1.template to_string<char, 
   char_traits<char>, allocator<char> >( );
   cout << "The string returned from the bitset b1"
        << "\n  by the member function to_string( ) is: "
        << s1 << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The string returned from the bitset b1
  by the member function to_string( ) is: 00111.
```

### <a name="to_ullong"></a> to_ullong

返回**无符号长长**值，该值包含相同的位将设置为位组对象的内容。

```
unsigned long long to_ullong() const;
```

#### <a name="return-value"></a>返回值

返回位序列中作为中的位值的总和**无符号长长**。 这**无符号长长**值将重建同一组位，如果它用于初始化位组。

#### <a name="exceptions"></a>Exceptions

将引发[overflow_error](overflow-error-class.md)位序列中的任一位具有一些值，如果对象不能表示为类型的值**unsigned long long**。

#### <a name="remarks"></a>备注

返回位序列中作为中的位值的总和**无符号长长**。

### <a name="to_ulong"></a> to_ulong

将位组对象转换为整数，它将生成的包含如果用于初始化位组位的序列。

```
unsigned long to_ulong( ) const;
```

#### <a name="return-value"></a>返回值

一个整数时，生成将位在位组中用于初始化位组。

#### <a name="remarks"></a>备注

应用成员函数将返回的位组中包含的位序列中找到具有相同的 1 和 0 位序列的整数。

成员函数将引发[overflow_error](overflow-error-class.md)位序列中的任一位具有一些值，如果对象不能表示为类型的值**无符号长**。

#### <a name="example"></a>示例

```cpp
// bitset_to_ulong.cpp
// compile with: /EHsc
#include <bitset>
#include <iostream>

int main( )
{
   using namespace std;

   bitset<5> b1 ( 7 );

   cout << "The ordered set of bits in the bitset<5> b1( 7 )"
        << "\n  that was generated by the number 7 is: ( "
        << b1 << " )" << endl;

   unsigned long int i;
   i = b1.to_ulong( );
   cout << "The integer returned from the bitset b1,"
        << "\n  by the member function to_long( ), that"
        << "\n  generated the bits as a base two number is: "
        << i << "." << endl;
}
```

```Output
The ordered set of bits in the bitset<5> b1( 7 )
  that was generated by the number 7 is: ( 00111 )
The integer returned from the bitset b1,
  by the member function to_long( ), that
  generated the bits as a base two number is: 7.
```
