---
title: /Tc、/Tp、/TC、/TP（指定源文件类型）
ms.date: 01/11/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
ms.openlocfilehash: c93da6d2498d46e4b7bf3ad37dde852bb6bc82a1
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927630"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc、/Tp、/TC、/TP（指定源文件类型）

**/Tc**选项将其 filename 参数指定为 c 源文件，即使该文件没有 .c 扩展名也是如此。 **/Tp**选项指定其 filename 参数是C++源文件，即使该文件没有 .cpp 或扩展名，也是如此。 选项和文件名之间的空格是可选的。 每个选项指定一个文件;若要指定其他文件，请重复选项。

**/Tc**和 **/tp**是 **/tc**和 **/tp**的全局变量。 它们指定编译器将命令行中名为的所有文件视为 C 源文件（ **/tc**）或C++源文件（ **/tp**），而不考虑命令行上与选项相关的位置。 可以通过 **/tc**或 **/tp**在单个文件上覆盖这些全局选项。

## <a name="syntax"></a>语法

> **/Tc** _filename_
>  **/Tp** _filename_
>  **/TC**
>  **/TP**

## <a name="arguments"></a>自变量

*filename*<br/>
C 或C++源文件。

## <a name="remarks"></a>备注

默认情况下， **CL**假定扩展名为 c 的文件是 c 源文件，文件扩展名为 .cpp，或扩展名C++为 .cxx。

当指定了**tc**或**tc**选项时，将忽略[/Zc： Wchar_t （wchar_t 是本机类型）](zc-wchar-t-wchar-t-is-native-type.md)选项的任何规范。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 开发环境中设置此编译器选项

1. 打开项目的“属性页” 对话框。 有关详细信息，请参阅[在 Visual Studio 中设置 C++ 编译器和生成属性](../working-with-project-properties.md)。

1. 选择 "**配置属性** > " " > **C/C++** **高级**" 属性页。

1. 修改**编译为**属性。 选择 **"确定" 或 "** **应用**" 以应用所做的更改。

### <a name="to-set-this-compiler-option-programmatically"></a>以编程方式设置此编译器选项

- 请参阅 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>。

## <a name="examples"></a>示例

此 CL 命令行指定 prg、prg 和均为 C 源文件。 CL 不会识别 prg。

> CL MAIN。C/TcTEST.PRG/TcCOLLATE.PRG 打印。PRG

此 CL 命令行指定将 TEST2、.cxx、TEST3 和 TEST4 编译为C++文件，并将 TEST5 编译为 c 文件中。

> CL TEST1。C TEST2.CXX TEST3。是 TEST4。O/Tc TEST5。Z/TP

## <a name="see-also"></a>请参阅

[MSVC 编译器选项](compiler-options.md)<br/>
[MSVC 编译器命令行语法](compiler-command-line-syntax.md)
