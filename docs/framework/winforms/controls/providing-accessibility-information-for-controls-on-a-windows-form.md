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
ms.openlocfilehash: 672104db94826cfbe113a7ae0ea29546b0c3b9da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181996"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a>Bir Windows Formundaki Denetimler için Erişilebilirlik Bilgileri Sağlama
Erişilebilirlik yardımcıları, engelli kişilerin bilgisayarları daha etkili kullanmasına yardımcı olan özel programlar ve aygıtlardır. Örnekler arasında, fare veya klavye kullanmak yerine sözlü komutlar sağlayan kişiler için kör olan kişiler için ekran okuyucular ve ses girişi yardımcı programları yer alır. Bu erişilebilirlik yardımcıları, Windows Forms denetimleri tarafından açığa çıkarılan erişilebilirlik özellikleriyle etkileşime girerek etkileşime girebilirsiniz. Bu özellikler şunlardır:  
  
- **Accessibilityobject**  
  
- **ErişilebilirDefaultActionDescription**  
  
- **Accessibledescription**  
  
- **Accessiblename**  
  
- **Accessiblerole**  
  
## <a name="accessibilityobject-property"></a>ErişilebilirlikNesne Özelliği  
 Salt okunur özelliği bir <xref:System.Windows.Forms.AccessibleObject> örnek içerir. **Erişilebilir Nesne,** denetimin <xref:Accessibility.IAccessible> açıklaması, ekran konumu, gezinme yetenekleri ve değeri hakkında bilgi sağlayan arabirimi uygular. Denetim forma eklendiğinde tasarımcı bu değeri ayarlar.  
  
## <a name="accessibledefaultactiondescription-property"></a>ErişilebilirDefaultActionDescription Özelliği  
 Bu dize, denetimin eylemini açıklar. Özellikler penceresinde görünmez ve yalnızca kod olarak ayarlanabilir. Aşağıdaki örnek, bir düğme denetimi için bu özelliği ayarlar:  
  
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
  
## <a name="accessibledescription-property"></a>Erişilebilir Açıklama Özelliği  
 Bu dize denetimi açıklar. Özellikler penceresinde veya kod olarak aşağıdaki gibi ayarlanabilir:  
  
```vb  
Button1.AccessibleDescription = "A button with text 'Exit'."  
```

```csharp  
Button1.AccessibleDescription = "A button with text 'Exit'";  
```

```cpp  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a>ErişilebilirAd Özelliği  
 Bu, erişilebilirlik yardımcılarına bildirilen bir denetimin adıdır. Özellikler penceresinde veya kod olarak aşağıdaki gibi ayarlanabilir:  
  
```vb  
Button1.AccessibleName = "Order"  
```

```csharp  
Button1.AccessibleName = "Order";  
```

```cpp  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a>ErişilebilirRol Özelliği  
 Numaralandırma <xref:System.Windows.Forms.AccessibleRole> içeren bu özellik, denetimin kullanıcı arabirimi rolünü açıklar. Yeni bir denetim değeri `Default`' ne göre ayarlanır. Bu, varsayılan olarak, bir **Düğme** denetiminin **Düğme**gibi hareket ettiği anlamına gelir. Denetimin başka bir rolü varsa bu özelliği sıfırlamak isteyebilirsiniz. Örneğin, **Bir Grafik**olarak **PictureBox** denetimi kullanıyor olabilirsiniz ve erişilebilirlik yardımcılarını, **Rolü PictureBox**olarak değil, **Grafik**olarak bildirmek için isteyebilirsiniz. Ayrıca, geliştirdiğiniz özel denetimler için bu özelliği belirtmek isteyebilirsiniz. Bu özellik Özellikler penceresinde veya kod olarak aşağıdaki gibi ayarlanabilir:  
  
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
