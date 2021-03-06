---
title: DUMPBIN 选项
ms.date: 10/24/2019
f1_keywords:
- dumpbin
helpviewer_keywords:
- DUMPBIN program, options
ms.assetid: 563b696e-7599-4480-94b9-014776289ec8
ms.openlocfilehash: 81c66f1971294531a2904a0b681819476bcc1eb2
ms.sourcegitcommit: 6ed1bc5b26dc60a780c1fc5f2f19d57ba1dc47d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/30/2019
ms.locfileid: "73144553"
---
# <a name="dumpbin-options"></a>DUMPBIN 选项

选项包括一个*选项说明符*，该说明符为短划线（`-`）或正斜杠（`/`），后跟选项的名称。 不能缩写选项名称。 某些选项采用冒号（`:`）之后指定的参数。 选项规范内不允许有空格或制表符。 在命令行上使用一个或多个空格或制表符分隔选项规范。 选项名及其关键字或文件名参数不区分大小写。 大多数选项都适用于所有二进制文件，但一些选项仅适用于某些类型的文件。 默认情况下，DUMPBIN 会将信息发送到标准输出。 使用[/out](out-dumpbin.md)选项将输出发送到文件。

## <a name="options-list"></a>选项列表

DUMPBIN 具有以下选项：

- [/ALL](all.md)

- [/ARCHIVEMEMBERS](archivemembers.md)

- [/CLRHEADER](clrheader.md)

- [/DEPENDENTS](dependents.md)

- [/DIRECTIVES](directives.md)

- [/DISASM\[： {BYTES\|NOBYTES}\]](disasm.md)

- [/ERRORREPORT： {NONE |PROMPT |QUEUE |收发](errorreport-dumpbin-exe.md)

- [/EXPORTS](dash-exports.md)

- [/FPO](fpo.md)

- [/HEADERS](headers.md)

- [/IMPORTS\[： filename\]](imports-dumpbin.md)

- [/LINENUMBERS](linenumbers.md)

- [/LINKERMEMBER\[： {1 | 2}\]](linkermember.md)

- [/LOADCONFIG](loadconfig.md)

- [/NOPDB](nopdb.md)

- [/OUT： filename](out-dumpbin.md)

- [/PDATA](pdata.md)

- [/PDBPATH\[： VERBOSE\]](pdbpath.md)

- [/RANGEE： vaMin\[，vaMax\]](range.md)

- [/RAWDATA\[： {NONE\|1\|2\|4\|8}\[，#\]\]](rawdata.md)

- [/RELOCATIONS](relocations.md)

- [/SECTION：名称](section-dumpbin.md)

- [/SUMMARY](summary.md)

- [/SYMBOLS](symbols.md)

- [/TLS](tls.md)

若要列出命令行上的 DUMPBIN 支持的选项，请使用 **/？** 选.

## <a name="see-also"></a>请参阅

[其他 MSVC 生成工具](c-cpp-build-tools.md)\
[DUMPBIN 命令行](dumpbin-command-line.md)\
[DUMPBIN 引用](dumpbin-reference.md)
