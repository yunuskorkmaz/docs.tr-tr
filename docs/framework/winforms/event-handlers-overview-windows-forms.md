---
title: Olay İşleyicilerine Genel Bakış (Windows Forms)
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
ms.openlocfilehash: cab35250f4fedf0a08dc7198430a668c7428c207
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54567760"
---
# <a name="event-handlers-overview-windows-forms"></a>Olay İşleyicilerine Genel Bakış (Windows Forms)
Bir olay işleyicisi olaya bağlı olan bir yöntemdir. Bir olay oluştuğunda, olay işleyicisi içindeki kod yürütülür. Her bir olay işleyicisi doğru olayı işlemek izin veren iki parametre sağlar. Aşağıdaki örnek, bir olay işleyicisi için gösterir. bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay.  
  
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
  
 İlk parametre`sender`, olayı oluşturan nesneye bir başvuru sağlar. İkinci parametre `e`, yukarıdaki örnekte, bir nesne belirli o anda işlenen olay geçirir. Nesnenin özelliklerini (ve bazı durumlarda, metotlarını) başvurarak fare olayları ya da sürükle ve bırak olayları aktarılan veri için fare konumu gibi bilgiler elde edebilirsiniz.  
  
 Genellikle her olay ikinci parametre için farklı olay nesne türüne sahip bir olay işleyicisi oluşturur. Yönelik olanlar gibi bazı olay işleyicileri <xref:System.Windows.Forms.Control.MouseDown> ve <xref:System.Windows.Forms.Control.MouseUp> olaylar, aynı nesne türünü, ikinci parametresinin sahiptir. Bu tür olaylar için her iki olayları işlemek için aynı olay işleyicisi kullanabilirsiniz.  
  
 Aynı olay işleyicisi, farklı denetimler için aynı olayı işlemek için de kullanabilirsiniz. Örneğin, bir grup varsa <xref:System.Windows.Forms.RadioButton> bir form üzerinde denetimleri için tek olay işleyicisine oluşturabilir <xref:System.Windows.Forms.Control.Click> olay ve her bir denetimin <xref:System.Windows.Forms.Control.Click> olayını tek olay işleyicisine bağlı. Daha fazla bilgi için [nasıl yapılır: Windows Forms'ta tek olay işleyicisine birden fazla olay bağlama](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms'ta Olay İşleyicileri Oluşturma](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)
- [Olaylara Genel Bakış](../../../docs/framework/winforms/events-overview-windows-forms.md)
