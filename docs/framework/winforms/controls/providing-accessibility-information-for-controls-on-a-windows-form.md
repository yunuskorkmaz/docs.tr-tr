---
title: "Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d7afc8cc67dc3a428e4995230345938075fbcc0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama
Erişilebilirlik yardımları özelleştirilmiş programlardır ve engelli kişilere yardımcı aygıtları bilgisayarlar daha etkili bir şekilde kullanın. Örnek ekran okuyucular blind ve ses giriş yardımcı programları klavye ve fare kullanmak yerine sözlü komutları sağlayan kişiler için birden çok kişi için verilebilir. Windows Forms denetimleri tarafından kullanıma sunulan erişilebilirlik özelliklerini bu erişilebilirlik yardımları etkileşim. Bu özellikleri şunlardır:  
  
-   **AccessibilityObject**  
  
-   **AccessibleDefaultActionDescription**  
  
-   **AccessibleDescription**  
  
-   **AccessibleName**  
  
-   **AccessibleRole**  
  
## <a name="accessibilityobject-property"></a>AccessibilityObject özelliği  
 Bu salt okunur özelliği içeren bir <xref:System.Windows.Forms.AccessibleObject> örneği. **AccessibleObject** uygulayan <xref:Accessibility.IAccessible> denetimin açıklaması, ekran konumu, gezinme yeteneklerini ve değer hakkında bilgi sağlayan arabirim. Forma denetim eklendiğinde Tasarımcı bu değeri ayarlar.  
  
## <a name="accessibledefaultactiondescription-property"></a>AccessibleDefaultActionDescription özelliği  
 Bu dize denetiminin eylemi açıklar. Özellikler penceresinde görüntülenmez ve kodda yalnızca ayarlanabilir. Aşağıdaki örnek, bu özellik bir düğme denetimi için ayarlar:  
  
```  
' Visual Basic  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
  
// C#  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
  
// C++  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a>AccessibleDescription özelliği  
 Bu dize denetimi açıklar. Bu özellikler penceresini veya kod aşağıdaki gibi ayarlanabilir:  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>AccessibleName özelliği  
 Erişilebilirlik yardımları bildirilen bir denetimin adıdır. Bu özellikler penceresini veya kod aşağıdaki gibi ayarlanabilir:  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a>AccessibleRole özelliği  
 Bu özellik içeren bir <xref:System.Windows.Forms.AccessibleRole> numaralandırma, denetimi kullanıcı arabirimi rolünü açıklar. Yeni bir denetim ayarlamak değere sahip `Default`. Bu, varsayılan olarak, anlamına gelir bir **düğmesini** denetimi olarak görev yapan bir **düğmesini**. Başka bir rol bir denetim varsa, bu özellik sıfırlamak isteyebilirsiniz. Örneğin, kullanıyor olabileceğiniz bir **PictureBox** olarak kontrol bir **grafik**, ve rol olarak bildirmek için erişilebilirlik yardımları isteyebilirsiniz bir **grafik**, olarak değil bir **PictureBox** . Bu özellik, geliştirdiğiniz özel denetimler için belirtmek isteyebilirsiniz. Bu özelliği Özellikler penceresini veya kod aşağıdaki gibi ayarlanabilir:  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.AccessibleObject>  
 <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.AccessibleRole>
