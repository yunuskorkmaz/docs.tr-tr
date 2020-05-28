---
title: "Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme"
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
ms.openlocfilehash: f6cb26ff247bba75cc351d453314bade2d38d9f5
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144844"
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
