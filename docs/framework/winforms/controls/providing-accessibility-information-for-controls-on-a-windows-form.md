---
title: Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 791944bd9e8f5520a571e6fb415d69022aa0bead
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991709"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama
Erişilebilirlik yardımları, Engelli kişilerin bilgisayarları daha verimli bir şekilde kullanmasına yardımcı olan özel programlar ve cihazlardır. Bu örneklerde, fare veya klavyeyi kullanmak yerine, kısayol tuşları sağlayan kişiler için görme ve ses girişi yardımcı programları için ekran okuyucular bulunur. Bu erişilebilirlik yardımları, Windows Forms denetimleri tarafından sunulan erişilebilirlik özellikleriyle etkileşime geçebilir. Bu özellikler şunlardır:  
  
- **AccessibilityObject**  
  
- **Erişilebilir Defaultactiondescription**  
  
- **Erişilebilir açıklama**  
  
- **Erişilebilir ad**  
  
- **Erişilebilir OLE**  
  
## <a name="accessibilityobject-property"></a>AccessibilityObject özelliği  
 Bu salt okunurdur özelliği bir <xref:System.Windows.Forms.AccessibleObject> örnek içerir. **Erişilebilir nesne** , denetimin açıklaması, <xref:Accessibility.IAccessible> ekran konumu, gezinme becerileri ve değer hakkında bilgi sağlayan arabirimini uygular. Tasarımcı, bu değeri denetim forma eklendiğinde ayarlar.  
  
## <a name="accessibledefaultactiondescription-property"></a>Erişilebilir Defaultactiondescription özelliği  
 Bu dize, denetimin eylemini açıklar. Özellikler penceresi görünmez ve yalnızca kodda ayarlanabilir. Aşağıdaki örnek, bir düğme denetimi için bu özelliği ayarlar:  
  
```vb  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
``` 

```csharp  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
```

```cpp  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a>Erişilebilir Açıklama özelliği  
 Bu dize, denetimi açıklar. Özellikler penceresi veya kodda aşağıdaki gibi ayarlanabilir.  
  
```vb  
Button1.AccessibleDescription = "A button with text 'Exit'."  
```

```csharp  
Button1.AccessibleDescription = "A button with text 'Exit'";  
```

```cpp  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>Erişilebilirblename özelliği  
 Bu, erişilebilirlik yardımlarına bildirilen bir denetimin adıdır. Özellikler penceresi veya kodda aşağıdaki gibi ayarlanabilir.  
  
```vb  
Button1.AccessibleName = "Order"  
```

```csharp  
Button1.AccessibleName = "Order";  
```

```cpp  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a>Erişilebilir OLE özelliği  
 Bir <xref:System.Windows.Forms.AccessibleRole> sabit listesi içeren bu özellik, denetimin kullanıcı arabirimi rolünü açıklar. Yeni bir denetimin değeri olarak `Default`ayarlanır. Bu, varsayılan olarak bir **düğme** denetiminin **düğme**işlevi gördüğü anlamına gelir. Bir denetimin başka bir rolü varsa, bu özelliği sıfırlamak isteyebilirsiniz. Örneğin, bir **PictureBox** denetimini **grafik**olarak kullanıyor olabilirsiniz ve erişilebilirlik yardımlarının rolü **PictureBox**olarak değil bir **grafik**olarak rapor etmek isteyebilirsiniz. Bu özelliği, geliştirmiş olduğunuz özel denetimler için de belirtmek isteyebilirsiniz. Bu özellik Özellikler penceresi veya kodda aşağıdaki gibi ayarlanabilir:  
  
```vb 
PictureBox1.AccessibleRole = AccessibleRole.Chart  
```

```csharp  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
```

```cpp  
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
