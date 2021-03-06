---
title: fputc、fputwc
ms.date: 11/04/2016
api_name:
- fputc
- fputwc
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fputc
- fputwc
- _fputtc
helpviewer_keywords:
- streams, writing characters to
- fputtc function
- _fputtc function
- fputwc function
- fputc function
ms.assetid: 5a0a593d-43f4-4fa2-a401-ec4e23de4d2f
ms.openlocfilehash: 3d289e54bca53be52d0b308d759f4200eca8599c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70956966"
---
# <a name="fputc-fputwc"></a>fputc、fputwc

将字符写入流。

## <a name="syntax"></a>语法

```C
int fputc(
   int c,
   FILE *stream
);
wint_t fputwc(
   wchar_t c,
   FILE *stream
);
```

### <a name="parameters"></a>参数

*c*<br/>
要写入的字符。

*stream*<br/>
指向**文件**结构的指针。

## <a name="return-value"></a>返回值

其中每个函数都会返回写入的字符。 对于**fputc**，返回值**EOF**表示错误。 对于**fputwc**， **WEOF**的返回值指示错误。 如果*stream*为**NULL**，则这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则它们将返回**EOF** ，并将**Errno**设置为**EINVAL**。

有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

其中每个函数将单个字符*c*写入到文件位置指示符指示的位置（如果已定义），并根据需要提升指示器。 对于**fputc**和**fputwc**，该文件与*stream*关联。 如果文件不支持定位请求，或在追加模式中打开，则该字符将被追加到流的末尾。

如果在 ANSI 模式下打开流，则这两个函数行为相同。 **fputc**当前不支持输出到 UNICODE 流中。

后缀为 **_nolock** 的版本是相同的，只不过它们可能会受到其他线程的影响。 有关详细信息，请参阅 [_fputc_nolock、_fputwc_nolock](fputc-nolock-fputwc-nolock.md)。

下面是例程特定的备注。

|例程所返回的值|备注|
|-------------|-------------|
|**fputc**|等效于**putc**，但仅作为函数实现，而不是作为函数和宏实现。|
|**fputwc**|**Fputc**的宽字符版本。 根据*流*是在文本模式还是二进制模式中打开，将*c*写入多字节字符或宽字符。|

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_fputtc**|**fputc**|**fputc**|**fputwc**|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**fputc**|\<stdio.h>|
|**fputwc**|\<stdio.h> 或 \<wchar.h>|

通用 Windows 平台 (UWP) 应用中不支持控制台。 与控制台（**stdin**、 **stdout**和**stderr**）关联的标准流句柄必须重定向，然后 C 运行时函数才能在 UWP 应用中使用它们。 有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_fputc.c
// This program uses fputc
// to send a character array to stdout.

#include <stdio.h>

int main( void )
{
   char strptr1[] = "This is a test of fputc!!\n";
   char *p;

   // Print line to stream using fputc.
   p = strptr1;
   while( (*p != '\0') && fputc( *(p++), stdout ) != EOF ) ;

}
```

```Output
This is a test of fputc!!
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[fgetc、fgetwc](fgetc-fgetwc.md)<br/>
[putc、putwc](putc-putwc.md)<br/>
