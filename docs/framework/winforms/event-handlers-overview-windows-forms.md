---
title: Olay İşleyicilerine Genel Bakış
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
ms.openlocfilehash: 10ba458197973ede35849a86fec35003f139b8d2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743462"
---
# <a name="event-handlers-overview-windows-forms"></a>Olay İşleyicilerine Genel Bakış (Windows Forms)
Olay işleyicisi, bir olaya bağlanan bir yöntemdir. Olay ortaya çıktığında, olay işleyicisi içindeki kod yürütülür. Her olay işleyicisi, olayı doğru bir şekilde işleyebilmeniz için iki parametre sağlar. Aşağıdaki örnekte, bir <xref:System.Windows.Forms.Button> denetiminin <xref:System.Windows.Forms.Control.Click> olayı için bir olay işleyicisi gösterilmektedir.  
  
```vb  
Private Sub button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles button1.Click  
  
End Sub  
```  
  
```csharp  
private void button1_Click(object sender, System.EventArgs e)   
{  
  
}  
```  
  
```cpp  
private:  
  void button1_Click(System::Object ^ sender,  
    System::EventArgs ^ e)  
  {  
  
  }  
```  
  
 `sender`ilk parametresi, olayı oluşturan nesneye bir başvuru sağlar. Yukarıdaki örnekte `e`ikinci parametresi, işlenmekte olan olaya özgü bir nesne geçirir. Nesnenin özelliklerine (ve bazen yöntemlerine) başvurarak, fare olayları veya sürükle ve bırak olaylarında aktarılan veriler için fare konumu gibi bilgileri elde edebilirsiniz.  
  
 Genellikle her olay, ikinci parametre için farklı bir olay nesnesi türüne sahip bir olay işleyicisi oluşturur. <xref:System.Windows.Forms.Control.MouseDown> ve <xref:System.Windows.Forms.Control.MouseUp> olayları gibi bazı olay işleyicileri, ikinci parametreleri için aynı nesne türüne sahiptir. Bu olay türleri için, her iki olayı da işlemek üzere aynı olay işleyicisini kullanabilirsiniz.  
  
 Aynı olay işleyicisini farklı denetimler için aynı olayı işlemek için de kullanabilirsiniz. Örneğin, bir formda <xref:System.Windows.Forms.RadioButton> denetimleri grubunuz varsa, <xref:System.Windows.Forms.Control.Click> olayı için tek bir olay işleyicisi oluşturabilir ve her bir denetimin <xref:System.Windows.Forms.Control.Click> olayının tek olay işleyicisine bağlı olmasını sağlayabilirsiniz. Daha fazla bilgi için bkz. [nasıl yapılır: birden çok olayı Windows Forms Içindeki tek bir olay Işleyicisine bağlama](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
- [Olaylara Genel Bakış](events-overview-windows-forms.md)
