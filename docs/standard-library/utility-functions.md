---
title: '&lt;utility&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- utility/std::exchange
- utility/std::forward
- utility/std::make_pair
- utility/std::move
- utility/std::swap
ms.assetid: b1df38cd-3a59-4098-9c81-83342eb719a4
helpviewer_keywords:
- std::exchange [C++]
- std::forward [C++]
- std::make_pair [C++]
- std::move [C++]
- std::swap [C++]
ms.openlocfilehash: 723b077500b9b741445efcd8574fb26cd53e5fc7
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246299"
---
# <a name="ltutilitygt-functions"></a>&lt;utility&gt; 函数

## <a name="asconst"></a> as_const

```cpp
template <class T> constexpr add_const_t<T>& as_const(T& t) noexcept;
template <class T> void as_const(const T&&) = delete;
```

### <a name="return-value"></a>返回值

返回*T*。

## <a name="declval"></a> declval

```cpp
template <class T> add_rvalue_reference_t<T> declval() noexcept;  // as unevaluated operand
```

## <a name="exchange"></a> exchange

**(C++14)** 向对象赋予新值并返回其旧值。

```cpp
template <class T, class Other = T>
    T exchange(T& val, Other&& new_val)
```

### <a name="parameters"></a>参数

*val*\
将接收 new_val 的值的对象。

*new_val*\
其值将被复制或移到 val 中的对象。

### <a name="remarks"></a>备注

对于复杂类型，`exchange` 可避免在移动构造函数可用时复制旧值、避免在新值是临时对象或进行移动时复制新值，并且可使用任何可用的转换赋值运算符接受任何类型作为新值。 Exchange 函数是不同于[std::swap](../standard-library/algorithm-functions.md#swap) ，左边的参数不是移动或复制到右侧的参数。

### <a name="example"></a>示例

下面的示例说明如何使用 `exchange`。 在实际情况下，`exchange` 对难以复制的大型对象非常有用：

```cpp
#include <utility>
#include <iostream>

using namespace std;

struct C
{
   int i;
   //...
};

int main()
{
   // Use brace initialization
   C c1{ 1 };
   C c2{ 2 };
   C result = exchange(c1, c2);
   cout << "The old value of c1 is: " << result.i << endl;
   cout << "The new value of c1 after exchange is: " << c1.i << endl;

   return 0;
}
```

```Output
The old value of c1 is: 1
The new value of c1 after exchange is: 2
```

## <a name="forward"></a> 转发

如果自变量是右值或右值引用，则有条件地将其自变量强制转换为右值引用。 这会将自变量的右值状态还原到转发函数，以支持完美转发。

```cpp
template <class Type>    // accepts lvalues
    constexpr Type&& forward(typename remove_reference<Type>::type& Arg) noexcept

template <class Type>    // accepts everything else
    constexpr Type&& forward(typename remove_reference<Type>::type&& Arg) noexcept
```

### <a name="parameters"></a>参数

*类型*\
传入的值的类型*Arg*，这可能是不同的类型*Arg*。 通常由转发函数的模板自变量决定。

*arg*\
要强制转换的自变量。

### <a name="return-value"></a>返回值

返回的右值引用*Arg*如果中传递的值*Arg*最初为右值或对 rvalue 的引用; 否则，返回*Arg*而无需修改其类型。

### <a name="remarks"></a>备注

你必须指定显式模板参数来调用 `forward`。

`forward` 不转发其自变量。 而是在其参数最初为右值或右值引用时，通过有条件地将参数强制转换为右值引用，`forward` 使得编译器能够在得知转发的参数的原始类型后执行重载决策。 转发函数的参数的类型可能不同于其原始类型-例如，当右值用作函数的参数和绑定到参数名称;拥有名称可使其成为左值，与作为右值实际存在的任何值-`forward`还原自变量的右值状态。

还原右值状态参数的原始值，以执行重载决策被称为*完美转发*。 通过完美转发，模板函数可接受任一引用类型的自变量，并在必要时还原其右值状态以执行正确的重载决策。 通过使用完美转发，你可以保留右值的移动语义，而且无需提供仅根据其自变量的引用类型而变化的函数的重载。

## <a name="from_chars"></a> from_chars

```cpp
from_chars_result from_chars(const char* first, const char* last, see below& value, int base = 10);

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general); 

from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

## <a name="get"></a> 获取

按索引位置或类型从 `pair` 对象获取元素。

```cpp
// get reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr tuple_element_t<Index, pair<T1, T2>>&
    get(pair<T1, T2>& Pr) noexcept;

// get reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr T1& get(pair<T1, T2>& Pr) noexcept;

// get reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr T2& get(pair<T1, T2>& Pr) noexcept;

// get const reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr const tuple_element_t<Index, pair<T1, T2>>&
    get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr const T1& get(const pair<T1, T2>& Pr) noexcept;

// get const reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr const T2& get(const pair<T1, T2>& Pr) noexcept;

// get rvalue reference to element at Index in pair Pr
template <size_t Index, class T1, class T2>
    constexpr tuple_element_t<Index, pair<T1, T2>>&&
    get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T1 in pair Pr
template <class T1, class T2>
    constexpr T1&& get(pair<T1, T2>&& Pr) noexcept;

// get rvalue reference to element T2 in pair Pr
template <class T2, class T1>
    constexpr T2&& get(pair<T1, T2>&& Pr) noexcept;
```

### <a name="parameters"></a>参数

*索引*\
所选的元素的从 0 开始的索引。

*T1*\
第一个 pair 元素的类型。

*T2*\
第二个 pair 元素的类型。

*拉取请求*\
要从中进行选择的对。

### <a name="remarks"></a>备注

每个模板函数都返回对其 `pair` 参数的元素的引用。

对于索引重载，如果的值*索引*是的 0，则函数返回`pr.first`如果的值*索引*是的 1，则函数返回`pr.second`。 类型 `RI` 是返回的元素的类型。

不具有索引参数的重载，要返回的元素的类型参数推导。 调用`get<T>(Tuple)`如果将生成编译器错误*pr*包含多于或少于一个元素类型为 t。

### <a name="example"></a>示例

```cpp
#include <utility>
#include <iostream>
using namespace std;
int main()
{

    typedef pair<int, double> MyPair;

    MyPair c0(9, 3.14);

    // get elements by index
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0) << endl;

    // get elements by type (C++14)
    MyPair c1(1, 0.27);
    cout << " " << get<int>(c1);
    cout << " " << get<double>(c1) << endl;
}
```

```Output
9 3.14
1 0.27
```

## <a name="index_sequence"></a> index_sequence

```cpp
template<size_t... I>
    using index_sequence = integer_sequence<size_t, I...>;
```

## <a name="index_sequence_for"></a> index_sequence_for

```cpp
template<class... T>
    using index_sequence_for = make_index_sequence<sizeof...(T)>;
```

## <a name="make_index_sequence"></a> make_index_sequence

```cpp
template<size_t N>
    using make_index_sequence = make_integer_sequence<size_t, N>;
```

## <a name="make_integer_sequence"></a> make_integer_sequence

```cpp
template<class T, T N>
    using make_integer_sequence = integer_sequence<T, see below >;
```

## <a name="make_pair"></a> make_pair

一种可用来构造 `pair` 类型对象的模板函数，其中，组件类型将根据作为参数传递的数据类型自动进行选择。

```cpp
template <class T, class U>
    pair<T, U> make_pair(T& Val1, U& Val2);

template <class T, class U>
    pair<T, U> make_pair(T& Val1, U&& Val2);

template <class T, class U>
    pair<T, U> make_pair(T&& Val1, U& Val2);

template <class T, class U>
    pair<T, U> make_pair(T&& Val1, U&& Val2);
```

### <a name="parameters"></a>参数

*Val1*\
用于初始化第一个 `pair` 元素的值。

*Val2*\
用于初始化第二个 `pair` 元素的值。

### <a name="return-value"></a>返回值

构造的配对对象： `pair` < `T`，`U`> (`Val1`， `Val2`)。

### <a name="remarks"></a>备注

`make_pair` 可以将 [reference_wrapper 类](../standard-library/reference-wrapper-class.md)类型的对象转换为引用类型，将衰减数组和函数转换为指针。

在返回的 `pair` 对象中，`T` 通过以下方式确定：

- 如果输入类型 `T` 为 `reference_wrapper<X>`，则返回的类型 `T` 为 `X&`。

- 否则，返回的类型 `T` 为 `decay<T>::type`。 如果[decay 类](../standard-library/decay-class.md)不受支持，则返回的类型`T`等同于输入类型`T`。

返回的类型 `U` 以类似的方式通过输入类型 `U` 来确定。

其中一个优点`make_pair`是要存储的对象的类型由编译器自动确定，且无需显式指定。 不使用显式模板参数，例如`make_pair<int, int>(1, 2)`当你使用`make_pair`因为它是详细信息，并添加复杂的右值引用问题，可能会导致编译失败。 就此示例来说，正确的语法应该是 `make_pair(1, 2)`

利用 `make_pair` 帮助程序函数，还可以实现向需要一个配对作为输入参数的函数传递两个值。

### <a name="example"></a>示例

有关如何使用 helper 函数 `make_pair` 声明和初始化对的示例，请参阅 [pair 结构](../standard-library/pair-structure.md)。

## <a name="move"></a> 移动

无条件将其自变量强制转换为右值引用，从而表示其可以移动（如果其类型支持移动）。

```cpp
template <class Type>
    constexpr typename remove_reference<Type>::type&& move(Type&& Arg) noexcept;
```

### <a name="parameters"></a>参数

*类型*\
从自变量的类型推导的类型传入*Arg*一起引用折叠规则。

*arg*\
要强制转换的自变量。 尽管的类型*Arg*看起来指定为右值引用，`move`也接受左值自变量，因为可以将左值引用绑定到右值引用。

### <a name="return-value"></a>返回值

作为右值引用 `Arg`，无论其类型是否是引用类型。

### <a name="remarks"></a>备注

模板参数*类型*不应显式指定，而是从传入的值的类型推导*Arg*。 类型*类型*根据引用折叠规则进行进一步调整。

`move` 不移动其参数。 相反，通过无条件地将其自变量强制转换，这可能是左值 — 为右值引用，它使得编译器随后能够移动，而不是复制中传递的值*Arg*如果其类型为支持移动。 如果其类型不支持移动，则将进行复制。

如果中传递的值*Arg*是左值 — 即，它具有一个名称或可以采用其地址 — 发生移动时将失效。 不引用中传递的值*Arg*按其名称或地址后它已经被移动。

## <a name="moveif"></a> move_if_noexcept

```cpp
template <class T> constexpr conditional_t< !is_nothrow_move_constructible_v<T> && is_copy_constructible_v<T>, const T&, T&&> move_if_noexcept(T& x) noexcept;
```

## <a name="swap"></a> 交换

交换两个类型的元素或[pair 结构](../standard-library/pair-structure.md)对象。

```cpp
template <class T>
    void swap(T& left, T& right) noexcept(see below );
template <class T, size_t N>
    void swap(T (&left)[N], T (&right)[N]) noexcept(is_nothrow_swappable_v<T>);
template <class T, class U>
    void swap(pair<T, U>& left, pair<T, U>& right);
```

### <a name="parameters"></a>参数

*左侧*\
类型或类型对象`pair`。

*右侧*\
类型或类型对象`pair`。

### <a name="remarks"></a>备注

其中一个优点`swap`是要存储的对象的类型由编译器自动确定，且无需显式指定。 不使用显式模板参数，例如`swap<int, int>(1, 2)`当你使用`swap`因为它是详细信息，并添加复杂的右值引用问题，可能会导致编译失败。

## <a name="to_chars"></a> to_chars

```cpp
to_chars_result to_chars(char* first, char* last, see below value, int base = 10);
to_chars_result to_chars(char* first, char* last, float value); 
to_chars_result to_chars(char* first, char* last, double value); 
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt); 
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt); 
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision); 
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision); 
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="remarks"></a>备注

通过填充范围值转换为字符字符串`[first, last)`，其中`[first, last)`必须是有效的范围。
