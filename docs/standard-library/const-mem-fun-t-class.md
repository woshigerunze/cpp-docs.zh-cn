---
title: const_mem_fun_t 类
ms.date: 02/21/2019
f1_keywords:
- functional/std::const_mem_fun_t
helpviewer_keywords:
- const_mem_fun_t class
ms.assetid: f169d381-019b-4a0e-a9a3-54da6d948270
ms.openlocfilehash: 5263612a26b2bcb606ad712a2a8e0a521ce9437a
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688211"
---
# <a name="const_mem_fun_t-class"></a>const_mem_fun_t 类

一种适配器类，在使用引用自变量进行初始化的情况下，该类允许将不带任何自变量的 const 成员函数作为一元函数对象调用。 在 c + + 11 中已弃用，在 c + + 17 中删除。

## <a name="syntax"></a>语法

```cpp
template <class Result, class Type>
class const_mem_fun_t : public unary_function <Type *, Result>
{
    explicit const_mem_fun_t(Result (Type::* Pm)() const);
    Result operator()(const Type* Pleft) const;
};
```

### <a name="parameters"></a>参数

*Pm* \
一个指针，指向要转换为函数对象的 `Type` 类成员函数。

*Pleft* \
在其上调用*Pm*成员函数的对象。

## <a name="return-value"></a>返回值

一个自适应一元函数。

## <a name="remarks"></a>备注

类模板存储*Pm*的副本，该副本必须是指向私有成员对象中 `Type` 类的成员函数的指针。 它将其成员函数定义 `operator()` 为返回（`Pleft` -> \* `Pm`）（） **const**。

## <a name="example"></a>示例

通常不直接使用 `const_mem_fun_t` 的构造函数；helper 函数 `mem_fun` 用于调整成员函数。 有关如何使用成员函数适配器的示例，请参阅 [mem_fun](../standard-library/functional-functions.md#mem_fun)。
