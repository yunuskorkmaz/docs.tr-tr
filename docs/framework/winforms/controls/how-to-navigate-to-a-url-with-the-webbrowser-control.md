---
title: "Nasıl yapılır: WebBrowser denetimi ile URL'ye gitme"
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
ms.openlocfilehash: 8d592aea972a95a582cc35ecb14227edec5860ce
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707241"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Nasıl yapılır: WebBrowser denetimi ile URL'ye gitme
Aşağıdaki kod örneğinde nasıl gidileceğini gösteren <xref:System.Windows.Forms.WebBrowser> belirli bir URL'ye denetimi.  
  
 Yeni belge tam yüklü olduğunda belirlemek için tanıtıcı <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> olay. Bu olay bir gösterimi için bkz. [nasıl yapılır: WebBrowser denetimi ile yazdırma](how-to-print-with-a-webbrowser-control.md).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [WebBrowser Denetimi](webbrowser-control-windows-forms.md)
- [Nasıl yapılır: WebBrowser denetimi ile yazdırma](how-to-print-with-a-webbrowser-control.md)
