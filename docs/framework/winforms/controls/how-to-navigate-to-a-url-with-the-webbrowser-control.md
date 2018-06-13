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
ms.openlocfilehash: f34577d45ddfbd2445fd4558c5694facf3f1aa29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531891"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Nasıl yapılır: WebBrowser Denetimi ile URL'ye Gitme
Aşağıdaki kod örneğinde gitmek gösterilmiştir <xref:System.Windows.Forms.WebBrowser> denetlemek için belirli bir URL.  
  
 Yeni belge tam yüklü olduğunda belirlemek için tanıtıcı <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olay. Bu olay tanıtımı için bkz: [nasıl yapılır: bir WebBrowser denetimi ile yazdırma](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).  
  
## <a name="example"></a>Örnek  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   A <xref:System.Windows.Forms.WebBrowser> adlı Denetim `webBrowser1`.  
  
-   Başvurular `System` ve `System.Windows.Forms` derlemeler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>  
 [WebBrowser Denetimi](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
 [Nasıl yapılır: Bir WebBrowser Denetimi ile Yazdırma](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
