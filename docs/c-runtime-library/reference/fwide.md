---
title: fwide
ms.date: 11/04/2016
api_name:
- fwide
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fwide
helpviewer_keywords:
- fwide function
ms.assetid: a4641f5b-d74f-4946-95d5-53a64610d28d
ms.openlocfilehash: 2e986ba5ab28072f4933e555eea32a5893c8df56
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956225"
---
# <a name="fwide"></a>fwide

未实现。

## <a name="syntax"></a>语法

```C
int fwide(
   FILE *stream,
   int mode;
);
```

### <a name="parameters"></a>参数

*stream*<br/>
指向**文件**结构的指针（已忽略）。

*模式*<br/>
流的新宽度：宽字符为正，字节为负，保持不变的为零。 （将忽略此值。）

## <a name="return-value"></a>返回值

此函数当前仅返回*mode*。

## <a name="remarks"></a>备注

此函数的当前版本不符合标准。

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fwide**|\<wchar.h>|

有关详细信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。