---
title: pointers_to_members 杂注
ms.date: 08/29/2019
f1_keywords:
- pointers_to_members_CPP
- vc-pragma.pointers_to_members
helpviewer_keywords:
- class members, pointers to
- pragmas, pointers_to_members
- members, pointers to
- pointers_to_members pragma
ms.assetid: 8325428c-c90a-4aed-9e82-cb1dda23f4ca
ms.openlocfilehash: fb5b277252b6c1422a87c5f2a2e2b7230ec49632
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70219062"
---
# <a name="pointers_to_members-pragma"></a>pointers_to_members 杂注

**C++相关**

指定指向类成员的指针是否可以在其关联类定义之前声明。 用于控制指针大小, 以及解释指针所需的代码。

## <a name="syntax"></a>语法

> **#pragma pointers_to_members (** *指针声明*[ **,** *最常见表示形式*])

## <a name="remarks"></a>备注

你可以将**pointers_to_members**杂注作为使用[/vmb 或/vmg](../build/reference/vmb-vmg-representation-method.md)编译器选项或[继承关键字](../cpp/inheritance-keywords.md)的替代方法放置在源文件中。

*指针声明*参数用于指定是否已在关联的函数定义之前或之后声明指向成员的指针。 *指针声明*参数是以下两个符号之一:

| 参数 | 注释 |
|--------------|--------------|
| **full_generality** | 生成安全的（有时并非最佳）代码。 如果在关联的类定义之前声明指向成员的任何指针, 则使用**full_generality** 。 此参数始终使用由*最常见的表示形式*参数指定的指针表示形式。 等效于 /vmg。 |
| **best_case** | 使用指向成员的所有指针的最佳大小写表示形式生成安全的最佳代码。 要求在声明指向类成员的指针之前定义此类。 默认值为**best_case**。 |

*最常见的表示形式*参数指定最小的指针表示形式, 编译器可以安全地使用该表示形式引用指向翻译单元中某个类的成员的任何指针。 参数可以是以下值之一:

| 参数 | 注释 |
|--------------|--------------|
| **single_inheritance** | 最常规的表示形式为单一继承（指向成员函数的指针）。 如果类定义（已为其声明指向成员的指针）的继承模型为多重继承或虚拟继承，则会导致出现错误。 |
| **multiple_inheritance** | 最常规的表示形式为多重继承（指向成员函数的指针）。 如果类定义（已为其声明指向成员的指针）的继承模型为虚拟继承，则会导致出现错误。 |
| **virtual_inheritance** | 最常规的表示形式为虚拟继承（指向成员函数的指针）。 绝不会导致出现错误。 使用时, **virtual_inheritance**是默认`#pragma pointers_to_members(full_generality)`参数。 |

> [!CAUTION]
> 建议仅将**pointers_to_members**杂注放置在要影响的源代码文件中, 并且在任何`#include`指令之后。 此做法可以减小杂注影响其他文件以及为同一变量、函数或类名意外指定多个定义的风险。

## <a name="example"></a>示例

```cpp
//   Specify single-inheritance only
#pragma pointers_to_members( full_generality, single_inheritance )
```

**结束C++特定**

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
