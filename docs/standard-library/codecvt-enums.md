---
title: '&lt;codecvt&gt; 枚举'
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_mode
ms.assetid: 46a8b073-01bc-46d3-b3d3-a8540f9422c1
helpviewer_keywords:
- std::codecvt_mode
ms.openlocfilehash: bbef1fe28c3321f06c0cc586062cd017168f8e73
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68459796"
---
# <a name="ltcodecvtgt-enums"></a>&lt;codecvt&gt; 枚举

## <a name="codecvt_mode"></a>  codecvt_mode 枚举

指定 [locale](../standard-library/locale-class.md) facet 的配置信息。

```cpp
enum codecvt_mode {
    consume_header = 4,
    generate_header = 2,
    little_endian = 1
};
```

### <a name="remarks"></a>备注

枚举定义为 [\<codecvt>](../standard-library/codecvt.md) 中声明的区域设置 facet 提供配置信息的三个常量。 非重复值为：

- `consume_header`，在读取多字节序列时使用初始标头序列，并确定要读取的后续多字节序列的字节顺序

- `generate_header`，在写入多字节序列时生成初始标头序列，以播发要编写的后续多字节序列的字节顺序

- `little_endian`，在 little-endian 顺序中，而不是在默认 big endian 顺序中生成多字节序列

这些常量可以任意组合并用“OR”连在一起。

## <a name="see-also"></a>请参阅

[\<codecvt>](../standard-library/codecvt.md)
