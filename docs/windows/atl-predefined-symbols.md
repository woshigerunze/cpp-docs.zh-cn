---
title: ATL 预定义的符号
ms.date: 02/14/2019
helpviewer_keywords:
- symbols [C++], ATL predefined
- ATL symbols
ms.assetid: 60d8f4e6-6ed9-47f3-9051-e4bf34384456
ms.openlocfilehash: 6e876fe27bd57194513f637fda90845ca68c59ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62390966"
---
# <a name="atl-predefined-symbols"></a>ATL 预定义的符号

在 ATL 标头文件中，定义了这些符号，但它们支持标准的 Windows 应用程序功能和操作。 这些符号主要用于对话框。

当您正在使用对话框和控件中[对话框编辑器](../windows/dialog-editor.md)，这些符号将出现在[属性窗口](/visualstudio/ide/reference/properties-window)与公共控件相关联。 例如，如果您的对话框具有**取消**按钮，命令将与相关联的符号 IDCANCEL 中**属性**窗口。

|||
|-|-|
|IDABORT|（控件）对话框中，中止按钮|
|IDC_STATIC|（控件）静态控件|
|IDCANCEL|（控件）对话框中，取消按钮|
|IDIGNORE|（控件）对话框中，忽略按钮|
|IDNO|（控件）对话框中，没有按钮|
|IDOK|（控件）对话框中，确定按钮|
|IDR_ACCELERATOR1|（资源）快捷键对应表|
|IDRETRY|（控件）对话框中，重试按钮|
|IDS_PROJNAME|（字符串）当前应用程序名称|
|IDYES|（控件）对话框中，是按钮|

## <a name="requirements"></a>要求

ATL

## <a name="see-also"></a>请参阅

[预定义的符号 ID](../windows/predefined-symbol-ids.md)<br/>
[MFC 预定义的符号](../windows/mfc-predefined-symbols.md)<br/>
[Win32 预定义符号](../windows/win32-predefined-symbols.md)<br/>