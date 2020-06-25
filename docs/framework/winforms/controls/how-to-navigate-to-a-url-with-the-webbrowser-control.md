---
title: "Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme"
description: Özel bir URL 'ye gitmek için Windows Forms WebBrowser. gezinmek denetimini nasıl kullanacağınızı öğrenin. Ayrıca, yeni belgenin ne zaman yüklendiğini nasıl saptayacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: e6ad360cc73a84ca040869832bb59d354cb78bd5
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325566"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme
Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.WebBrowser> denetimin belirli BIR URL 'ye nasıl gezindiğini gösterilmektedir.

 Yeni belgenin tam olarak yüklenip yüklenmediğini anlamak için <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olayı işleyin. Bu olayın bir gösterimi için bkz. [nasıl yapılır: bir WebBrowser denetimi Ile yazdırma](how-to-print-with-a-webbrowser-control.md).

## <a name="example"></a>Örnek

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a>Kod Derleniyor
 Bu örnek şunları gerektirir:

- <xref:System.Windows.Forms.WebBrowser>Adlı bir denetim `webBrowser1` .

- `System`Ve `System.Windows.Forms` derlemelerine başvurular.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser Denetimi](webbrowser-control-windows-forms.md)
- [Nasıl yapılır: Bir WebBrowser Denetimi ile Yazdırma](how-to-print-with-a-webbrowser-control.md)
