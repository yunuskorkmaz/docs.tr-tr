---
title: Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 0f589f37d79c9ec8d55153aac4c846726a379055
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948031"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama
Erişilebilirlik yardımları özel programları ve engelli kişilerin yardımcı aygıtları bilgisayarlar daha etkili bir şekilde kullanır. Ekran okuyucuları, klavye ve fare kullanmak yerine sözlü komutları sağlayan kişiler için gizli ve ses giriş yardımcı olan kişilere yönelik olarak verilebilir. Bu erişilebilirlik yardımları Windows Forms denetimleri tarafından kullanıma sunulan erişilebilirlik özellikleri ile etkileşim kurun. Bu özellikler şunlardır:  
  
- **AccessibilityObject**  
  
- **AccessibleDefaultActionDescription**  
  
- **AccessibleDescription**  
  
- **AccessibleName**  
  
- **AccessibleRole**  
  
## <a name="accessibilityobject-property"></a>AccessibilityObject özelliği  
 Bu salt okunur özelliği içeren bir <xref:System.Windows.Forms.AccessibleObject> örneği. **AccessibleObject** uygulayan <xref:Accessibility.IAccessible> denetimin açıklaması, ekran konumunu, gezinme yeteneklerini ve değeri hakkında bilgi sağlayan bir arabirimi. Tasarımcı, denetimi forma eklendiğinde bu değeri ayarlar.  
  
## <a name="accessibledefaultactiondescription-property"></a>AccessibleDefaultActionDescription özelliği  
 Bu dize, denetimin eylemi açıklar. Özellikler penceresinde görünmez ve yalnızca kodda ayarlanabilir. Aşağıdaki örnekte, bu özellik bir düğme denetimi için ayarlar:  
  
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
 Bu dize bir denetimi açıklamaktadır. Bu Özellikler penceresinde veya kod aşağıdaki gibi ayarlanabilir:  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>AccessibleName özelliği  
 Erişilebilirlik yardımları bildirilen bir denetimin adıdır. Bu Özellikler penceresinde veya kod aşağıdaki gibi ayarlanabilir:  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a>AccessibleRole özelliği  
 Bu özellik içeren bir <xref:System.Windows.Forms.AccessibleRole> numaralandırma denetim kullanıcı arabirimi rolünü açıklar. Yeni bir denetim ayarlanmış değere sahip `Default`. Bu, varsayılan olarak, açardı bir **düğmesi** denetim görür bir **düğmesi**. Bir denetimi başka bir rol varsa bu özelliği sıfırlamak isteyebilirsiniz. Örneğin, kullanmakta olduğunuz bir **PictureBox** olarak denetim bir **grafik**, ve rol olarak bildirmek için erişilebilirlik yardımları isteyebileceğiniz bir **grafik**, olarak değil bir **PictureBox** . Bu özellik, geliştirdiğiniz özel denetimler için belirtmek isteyebilirsiniz. Bu özellik Özellikler penceresinde veya kod aşağıdaki gibi ayarlanabilir:  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
