---
title: codecvt 类
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt
- xlocale/std::codecvt::extern_type
- xlocale/std::codecvt::intern_type
- xlocale/std::codecvt::state_type
- xlocale/std::codecvt::always_noconv
- xlocale/std::codecvt::do_always_noconv
- xlocale/std::codecvt::do_encoding
- xlocale/std::codecvt::do_in
- xlocale/std::codecvt::do_length
- xlocale/std::codecvt::do_max_length
- xlocale/std::codecvt::do_out
- xlocale/std::codecvt::do_unshift
- xlocale/std::codecvt::encoding
- xlocale/std::codecvt::in
- xlocale/std::codecvt::length
- xlocale/std::codecvt::max_length
- xlocale/std::codecvt::out
- xlocale/std::codecvt::unshift
helpviewer_keywords:
- std::codecvt [C++]
- std::codecvt [C++], extern_type
- std::codecvt [C++], intern_type
- std::codecvt [C++], state_type
- std::codecvt [C++], always_noconv
- std::codecvt [C++], do_always_noconv
- std::codecvt [C++], do_encoding
- std::codecvt [C++], do_in
- std::codecvt [C++], do_length
- std::codecvt [C++], do_max_length
- std::codecvt [C++], do_out
- std::codecvt [C++], do_unshift
- std::codecvt [C++], encoding
- std::codecvt [C++], in
- std::codecvt [C++], length
- std::codecvt [C++], max_length
- std::codecvt [C++], out
- std::codecvt [C++], unshift
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
ms.openlocfilehash: 631c3b88be5e2a03798ff6d8e3fb200ad257a8d7
ms.sourcegitcommit: 4b0928a1a497648d0d327579c8262f25ed20d02e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2019
ms.locfileid: "72890189"
---
# <a name="codecvt-class"></a>codecvt 类

描述可用作区域设置 facet 的对象的类模板。 此模板类能够控制用于对程序中和程序外的字符进行编码的值序列之间的转换。

## <a name="syntax"></a>语法

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>参数

*CharType* \
在程序中用于对字符进行编码的类型。

*字节*\
用于对程序外的字符进行编码的类型。

*StateType* \
一种类型，此类型可用于表示字符表示形式的内部和外部类型之间转换的中间状态。

## <a name="remarks"></a>备注

类模板描述可用作[区域设置 facet](../standard-library/locale-class.md#facet_class)的对象，用于控制*CharType*类型的值序列和类型为*Byte*的值序列之间的转换。 类*StateType*的特征是转换， *StateType*类的对象在转换过程中存储任何必需的状态信息。

内部编码使用每个字符的固定字节数的表示形式，通常为**char**或类型**wchar_t**。

对于任何区域设置 facet，静态对象 `id` 的初始存储值为零。 首次尝试访问其存储值后，将在 `id` 中存储唯一正值。

[do_in](#do_in) 和 [do_out](#do_out) 的模板版本始终返回 `codecvt_base::noconv`。

C++ 标准库定义了若干显式专用化：

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

在**wchar_t**和**char**序列之间转换。

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

在编码为 UTF-16 的 `char16_t` 序列和编码为 UTF-8 的**char**序列之间进行转换。

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

在编码为32（UCS-4）的 `char32_t` 序列和编码为 UTF-8 的**char**序列之间进行转换。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[codecvt](#codecvt)|用作区域设置 facet 以处理转换的 `codecvt` 类的对象的构造函数。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[extern_type](#extern_type)|用于外部表示形式的字符类型。|
|[intern_type](#intern_type)|用于内部表示形式的字符类型。|
|[state_type](#state_type)|一种字符类型，此类型用于表示内部和外部表示形式进行转换期间的中间状态。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[always_noconv](#always_noconv)|测试是否不需要完成转换。|
|[do_always_noconv](#do_always_noconv)|为测试是否不需要完成转换而调用的虚拟函数。|
|[do_encoding](#do_encoding)|一种虚拟函数，该函数测试 `Byte` 流的编码是否依赖于状态、使用的 `Byte` 值与生成的 `CharType` 值之间的比率是否是常量，如果是，则确定该比率的值。|
|[do_in](#do_in)|一种虚拟函数，通过调用此函数可将内部 `Byte` 值的序列转换为外部 `CharType` 值的序列。|
|[do_length](#do_length)|一种虚拟函数，该函数确定给定外部 `Byte` 值序列中的多少 `Byte` 值不超过给定的内部 `CharType` 值数，并返回 `Byte` 值的数目。|
|[do_max_length](#do_max_length)|返回生成一个内部 `CharType` 所需的最大外部字节数的虚拟函数。|
|[do_out](#do_out)|一种虚拟函数，通过调用此函数可将内部 `CharType` 值的序列转换为外部字节的序列。|
|[do_unshift](#do_unshift)|一种虚拟函数，通过调用此函数可提供依赖于状态的转换中所需的 `Byte` 值以完成 `Byte` 值序列中的最后一个字符。|
|[encoding](#encoding)|测试 `Byte` 流的编码是否依赖于状态、使用的 `Byte` 值与生成的 `CharType` 值之间的比率是否是常量，如果是，则确定此比率的值。|
|[in](#in)|将 `Byte` 值序列的外部表示形式转换为 `CharType` 值序列的内部表示形式。|
|[length](#length)|确定给定外部 `Byte` 值序列中的多少 `Byte` 值不超过给定数量的内部 `CharType` 值，并返回 `Byte` 值的数目。|
|[max_length](#max_length)|返回生成一个内部 `CharType`所需的外部 `Byte` 值的最大数目。|
|[out](#out)|将内部 `CharType` 值的序列转换为外部 `Byte` 值的序列。|
|[unshift](#unshift)|提供依赖于状态的转换中需要的外部 `Byte` 值以完成 `Byte` 值序列中的最后一个字符。|

## <a name="requirements"></a>要求

**标头：** \<locale>

**命名空间:** std

## <a name="always_noconv"></a>  codecvt::always_noconv

测试是否无需进行转换。

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>返回值

一个布尔值，如果无需进行转换，则为**true** ;如果至少有一个需要完成，则**为 false** 。

### <a name="remarks"></a>备注

此成员函数返回 [do_always_noconv](#do_always_noconv)。

### <a name="example"></a>示例

```cpp
// codecvt_always_noconv.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result1 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;

   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result2 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;
}
```

```Output
No conversion is needed.
At least one conversion is required.
```

## <a name="codecvt"></a>  codecvt::codecvt

用作区域设置 facet 以处理转换的 codecvt 类的对象的构造函数。

```cpp
explicit codecvt(size_t refs = 0);
```

### <a name="parameters"></a>参数

*refs* \
用于指定对象的内存管理类型的整数值。

### <a name="remarks"></a>备注

*Refs*参数的可能值及其重要性为：

- 0：对象的生存期由包含该对象的区域设置管理。

- 1：必须手动管理对象的生存期。

- 2：未定义这些值。

构造函数通过[locale：： facet](../standard-library/locale-class.md#facet_class)`(refs)`初始化其 `locale::facet` 基对象。

## <a name="do_always_noconv"></a>  codecvt::do_always_noconv

一种虚拟函数，通过调用此函数可测试是否无需进行转换。

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>返回值

仅当对[do_in](#do_in)或[do_out](#do_out)的每个调用都返回 `noconv`时，受保护的虚拟成员函数才返回**true** 。

模板版本始终返回 **true**。

### <a name="example"></a>示例

请参阅 [always_noconv](#always_noconv) 的示例，它调用 `do_always_noconv`。

## <a name="do_encoding"></a>  codecvt::do_encoding

一种虚拟函数，用于测试 `Byte` 流的编码是否依赖于状态、使用的 `Byte` 值与生成的 `CharType` 值之间的比率是否是常量，如果是，则确定该比率的值。

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>返回值

受保护的虚拟成员函数返回：

- -1，如果类型序列 `extern_type` 的编码是依赖于状态的，则为-1。

- 如果编码涉及不同长度的序列，则为 0。

- 如果编码仅涉及 *N* 长度的序列，则为 *N*

### <a name="example"></a>示例

请参阅 [encoding](#encoding) 的示例，它调用 `do_encoding`。

## <a name="do_in"></a>  codecvt::do_in

一种虚拟函数，通过调用此函数可将外部 `Byte` 值的序列转换为内部 `CharType` 值的序列。

```cpp
virtual result do_in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>参数

*状态*\
每次调用成员函数时保留的转换状态。

*first1* \
指向待转换序列开头的指针。

*last1* \
指向待转换序列末尾的指针。

*next1* \
指向超出已转换序列末尾到第一个未转换字符的指针。

*first2* \
指向已转换序列开头的指针。

*last2* \
指向已转换序列末尾的指针。

*next2* \
指向上次转换后 `CharType` 之后的 `CharType` 的指针，指向目标序列中第一个未修改的字符。

### <a name="return-value"></a>返回值

返回指示操作成功、部分成功或失败的值。 该函数返回：

- 如果源序列的格式不正确，则 `codecvt_base::error`。

- 如果函数不执行任何转换，则为 `codecvt_base::noconv`。

- 如果转换成功，则 `codecvt_base::ok`。

- 如果源没有足够的，或者如果目标不够大，则 `codecvt_base::partial`，以便成功进行转换。

### <a name="remarks"></a>备注

*状态*必须表示新源序列开头的初始转换状态。 此函数根据需要来更改其存储的值以反映成功转换的当前状态。 否则未指定其存储的值。

### <a name="example"></a>示例

请参阅 [in](#in) 的示例，它调用 `do_in`。

## <a name="do_length"></a>  codecvt::do_length

一种虚拟函数，该函数确定给定外部 `Byte` 值序列中的多少 `Byte` 值不超过给定的内部 `CharType` 值数，并返回 `Byte` 值的数目。

```cpp
virtual int do_length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>参数

*状态*\
每次调用成员函数时保留的转换状态。

*first1* \
指向外部序列开头的指针。

*last1* \
指向外部序列末尾的指针。

*len2*\
成员函数可返回的最大 `Byte` 值数。

### <a name="return-value"></a>返回值

一个整数，表示位于 [`first1`，`last1`）的外部源序列定义的最大转换数的计数，而不是大于*len2*。

### <a name="remarks"></a>备注

受保护的虚拟成员函数有效地调用*状态*`do_in( state, first1, last1, next1, buf, buf + len2, next2)`、`next1` 和 `next2`的某些缓冲区 `buf`和指针。

然后，它将返回 `next2`  -  `buf`。 因此，它会计算在 [`first1`，`last1`）处由源序列定义的最大转换数，不能大于*len2*。

模板版本始终返回*last1* - *first1*和*len2*中较小的一个。

### <a name="example"></a>示例

请参阅[length](#length)的示例，它调用 `do_length`。

## <a name="do_max_length"></a>  codecvt::do_max_length

返回生成一个内部 `CharType`所需的最大外部 `Byte` 值数的虚拟函数。

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>返回值

生成一个 `CharType`所需的最大 `Byte` 值数。

### <a name="remarks"></a>备注

受保护的虚拟成员函数将返回可由[do_length](#do_length)`( first1, last1, 1)` 为*first1*和*last1*的任意有效值返回的最大允许值。

### <a name="example"></a>示例

请参阅 [max_length](#max_length) 的示例，它调用 `do_max_length`。

## <a name="do_out"></a>  codecvt::do_out

一种虚拟函数，通过调用此函数可将内部 `CharType` 值的序列转换为外部 `Byte` 值的序列。

```cpp
virtual result do_out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>参数

*状态*\
每次调用成员函数时保留的转换状态。

*first1* \
指向待转换序列开头的指针。

*last1* \
指向待转换序列末尾的指针。

*next1* \
指向第一个转换 `CharType` 后的第一个未转换 `CharType` 的指针的指针。

*first2* \
指向已转换序列开头的指针。

*last2* \
指向已转换序列末尾的指针。

*next2* \
指向第一个转换 `Byte` 后的第一个未转换 `Byte` 的指针的指针。

### <a name="return-value"></a>返回值

该函数返回：

- 如果源序列的格式不正确，则 `codecvt_base::error`。

- 如果函数不执行任何转换，则为 `codecvt_base::noconv`。

- 如果转换成功，则 `codecvt_base::ok`。

- `codecvt_base::partial` 源是否不足，或者目标大小是否不足以使转换成功。

### <a name="remarks"></a>备注

*状态*必须表示新源序列开头的初始转换状态。 此函数根据需要来更改其存储的值以反映成功转换的当前状态。 否则未指定其存储的值。

### <a name="example"></a>示例

请参阅 [out](#out) 的示例，它调用 `do_out`。

## <a name="do_unshift"></a>  codecvt::do_unshift

一种虚拟函数，通过调用此函数可提供依赖于状态的转换中所需的 `Byte` 值以完成 `Byte` 值序列中的最后一个字符。

```cpp
virtual result do_unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>参数

*状态*\
每次调用成员函数时保留的转换状态。

*first2* \
指向目标范围内第一个位置的指针。

*last2* \
指向目标范围内最后一个位置的指针。

*next2* \
指向目标序列中第一个未更改元素的指针。

### <a name="return-value"></a>返回值

该函数返回：

- `codecvt_base::error`*状态*是否表示无效状态

- 如果该函数不执行任何转换，则为 `codecvt_base::noconv`

- 如果转换成功，则 `codecvt_base::ok`

- 如果目标不够大以致无法成功转换，则 `codecvt_base::partial`

### <a name="remarks"></a>备注

受保护的虚拟成员函数尝试将源元素 `CharType`（0）转换为它在 [`first2`，`last2`）内存储的目标序列，但终止元素除外 `Byte`（0）。 它始终在*next2*中存储指向目标序列中第一个未更改元素的指针。

_ *State* 必须代表新源序列开头的初始转换状态。 此函数根据需要来更改其存储的值以反映成功转换的当前状态。 通常情况下，转换源元素 `CharType` （0）会使当前状态成为初始转换状态。

### <a name="example"></a>示例

请参阅 [unshift](#unshift) 的示例，它调用 `do_unshift`。

## <a name="encoding"></a>  codecvt::encoding

测试 `Byte` 流的编码是否依赖于状态、使用的 `Byte` 值与生成的 `CharType` 值之间的比率是否是常量，如果是，则确定此比率的值。

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>返回值

如果返回值为正，则该值为生成 `CharType` 字符所需 `Byte` 字符数。

受保护的虚拟成员函数返回：

- -1，如果类型序列 `extern_type` 的编码是依赖于状态的，则为-1。

- 如果编码涉及不同长度的序列，则为 0。

- 如果编码仅涉及 *N* 长度的序列，则为 *N*。

### <a name="remarks"></a>备注

此成员函数返回 [do_encoding](#do_encoding)。

### <a name="example"></a>示例

```cpp
// codecvt_encoding.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
}
```

```Output
1
1
1
```

## <a name="extern_type"></a>  codecvt::extern_type

用于外部表示形式的字符类型。

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>备注

类型是模板参数 `Byte` 的同义词。

## <a name="in"></a>  codecvt::in

将 `Byte` 值序列的外部表示形式转换为 `CharType` 值序列的内部表示形式。

```cpp
result in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>参数

*状态*\
每次调用成员函数时保留的转换状态。

*first1* \
指向待转换序列开头的指针。

*last1* \
指向待转换序列末尾的指针。

*next1* \
指向超出已转换序列末尾到第一个未转换字符的指针。

*first2* \
指向已转换序列开头的指针。

*last2* \
指向已转换序列末尾的指针。

*next2* \
指向上次转换后 `Chartype` 到目标序列中第一个未更改字符后面的 `CharType` 的指针。

### <a name="return-value"></a>返回值

返回指示操作成功、部分成功或失败的值。 该函数返回：

- 如果源序列的格式不正确，则 `codecvt_base::error`。

- 如果函数不执行任何转换，则为 `codecvt_base::noconv`。

- 如果转换成功，则 `codecvt_base::ok`。

- `codecvt_base::partial` 源是否不足，或者目标大小是否不足以使转换成功。

### <a name="remarks"></a>备注

*状态*必须表示新源序列开头的初始转换状态。 此函数根据需要来更改其存储的值以反映成功转换的当前状态。 部分转换后，必须将*状态*设置为，以允许在新字符到达时恢复转换。

此成员函数返回[do_in](#do_in)`( state, first1,  last1,  next1, first2, last2,  next2)`。

### <a name="example"></a>示例

```cpp
// codecvt_in.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));
   const char* pszNext;
   wchar_t* pwszNext;
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).in( state,
          pszExt, &pszExt[strlen(pszExt)], pszNext,
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;
   exit(-1);
}
```

```Output
It worked! The converted string is:
[This is the string to be converted!]
```

## <a name="intern_type"></a>  codecvt::intern_type

用于内部表示形式的字符类型。

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>备注

类型是模板参数 `CharType` 的同义词。

## <a name="length"></a>  codecvt::length

确定给定外部 `Byte` 值序列中的多少 `Byte` 值不超过给定数量的内部 `CharType` 值，并返回 `Byte` 值的数目。

```cpp
int length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>参数

*状态*\
每次调用成员函数时保留的转换状态。

*first1* \
指向外部序列开头的指针。

*last1* \
指向外部序列末尾的指针。

*len2*\
可由成员函数返回的最大字节数。

### <a name="return-value"></a>返回值

一个整数，表示位于 [`first1`，`last1`）的外部源序列定义的最大转换数的计数，而不是大于*len2*。

### <a name="remarks"></a>备注

此成员函数返回[do_length](#do_length)`( state, first1, last1, len2)`。

### <a name="example"></a>示例

```cpp
// codecvt_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string whose length is to be measured!";
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).length( state,
          pszExt, &pszExt[strlen(pszExt)], LEN );
   cout << "The length of the string is: ";
   wcout << res;
   cout << "." << endl;
   exit(-1);
}
```

```Output
The length of the string is: 50.
```

## <a name="max_length"></a>  codecvt::max_length

返回生成一个内部 `CharType`所需的外部 `Byte` 值的最大数目。

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>返回值

生成一个 `CharType`所需的最大 `Byte` 值数。

### <a name="remarks"></a>备注

此成员函数返回 [do_max_length](#do_max_length)。

### <a name="example"></a>示例

```cpp
// codecvt_max_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc( "C");//English_Britain" );//German_Germany
   int res = use_facet<codecvt<char, char, mbstate_t> >
     ( loc ).max_length( );
   wcout << res << endl;
}
```

```Output
1
```

## <a name="out"></a>  codecvt::out

将内部 `CharType` 值的序列转换为外部 `Byte` 值的序列。

```cpp
result out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>参数

*状态*\
每次调用成员函数时保留的转换状态。

*first1* \
指向待转换序列开头的指针。

*last1* \
指向待转换序列末尾的指针。

*next1* \
指向最后一个 `CharType` 转换后的第一个未转换 `CharType` 的指针的引用。

*first2* \
指向已转换序列开头的指针。

*last2* \
指向已转换序列末尾的指针。

*next2* \
指向上次转换后的第一个未转换的 `Byte` `Byte` 指针的指针。

### <a name="return-value"></a>返回值

此成员函数返回[do_out](#do_out)`( state, first1, last1, next1, first2, last2, next2)`。

### <a name="remarks"></a>备注

有关详细信息，请参阅 [codecvt::do_out](#do_out)。

### <a name="example"></a>示例

```cpp
// codecvt_out.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
#include <wchar.h>
using namespace std;
#define LEN 90
int main( )
{
   char pszExt[LEN+1];
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );
   char* pszNext;
   const wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).out( state,
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );
   pszExt[wcslen( pwszInt )] = 0;
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )
   << "The converted string is:\n ["
   << &pszExt[0]
   << "]" << endl;
}
```

```Output
It worked: The converted string is:
[This is the wchar_t string to be converted.]
```

## <a name="state_type"></a>  codecvt::state_type

一种字符类型，此类型用于表示内部和外部表示形式进行转换期间的中间状态。

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>备注

类型是模板参数 `StateType` 的同义词。

## <a name="unshift"></a>  codecvt::unshift

提供在依赖于状态的转换中完成 `Byte` 值序列中最后一个字符所需的 `Byte` 值。

```cpp
result unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>参数

*状态*\
每次调用成员函数时保留的转换状态。

*first2* \
指向目标范围内第一个位置的指针。

*last2* \
指向目标范围内最后一个位置的指针。

*next2* \
指向目标序列中第一个未更改元素的指针。

### <a name="return-value"></a>返回值

该函数返回：

- `codecvt_base::error` 状态是否表示无效状态。

- 如果函数不执行任何转换，则为 `codecvt_base::noconv`。

- 如果转换成功，则 `codecvt_base::ok`。

- `codecvt_base::partial` 如果目标不够大，则无法成功转换。

### <a name="remarks"></a>备注

受保护的虚拟成员函数尝试将源元素 `CharType`（0）转换为它在 [`first2`，`last2`）内存储的目标序列，但终止元素除外 `Byte`（0）。 它始终在*next2*中存储指向目标序列中第一个未更改元素的指针。

*状态*必须表示新源序列开头的初始转换状态。 此函数根据需要来更改其存储的值以反映成功转换的当前状态。 通常情况下，转换源元素 `CharType` （0）会使当前状态成为初始转换状态。

此成员函数返回[do_unshift](#do_unshift)`( state, first2, last2, next2 )`。

## <a name="see-also"></a>请参阅

[\<locale>](../standard-library/locale.md)\
[代码页](../c-runtime-library/code-pages.md)\
[区域设置名称、语言和国家/地区字符串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
