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
ms.openlocfilehash: b6c1255fa17d91daaa73001fea04f26e73dba0ae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015822"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme
Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.WebBrowser> denetimin belirli bir URL 'ye nasıl gezindiğini gösterilmektedir.

 Yeni belgenin tam olarak yüklenip yüklenmediğini anlamak için <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olayı işleyin. Bu olayın bir gösterimi için bkz [. nasıl yapılır: WebBrowser denetimiyle](how-to-print-with-a-webbrowser-control.md)yazdır.

## <a name="example"></a>Örnek

```vb
Me.webBrowser1.Navigate("http://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("http://www.microsoft.com");
```

## <a name="compiling-the-code"></a>Kod Derleniyor
 Bu örnek şunları gerektirir:

- <xref:System.Windows.Forms.WebBrowser> Adlı`webBrowser1`bir denetim.

- `System` Ve`System.Windows.Forms` derlemelerine başvurular.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser Denetimi](webbrowser-control-windows-forms.md)
- [Nasıl yapılır: WebBrowser denetimi ile yazdırma](how-to-print-with-a-webbrowser-control.md)
