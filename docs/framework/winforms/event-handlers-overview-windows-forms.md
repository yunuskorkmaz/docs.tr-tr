---
title: "Olay İşleyicilerine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms, event handling
- event handling [Windows Forms], Windows Forms
- event handlers [Windows Forms], about event handlers
ms.assetid: 228112e1-1711-42ee-8ffa-ff3555bffe66
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7353f3ab4513d8331b1d38cb01ad16c7d3cde165
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="event-handlers-overview-windows-forms"></a>Olay İşleyicilerine Genel Bakış (Windows Forms)
Olay işleyicisi olaya bağlı bir yöntemdir. Olay işleyicisi içindeki kod olay oluşturulduğunda yürütülür. Her olay işleyicisi olayını düzgün bir şekilde işlemek izin veren iki parametre sağlar. Aşağıdaki örnekte bir olay işleyicisi için bir <xref:System.Windows.Forms.Button> denetimin <xref:System.Windows.Forms.Control.Click> olay.  
  
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
  
 İlk parametre`sender`, olayı nesnesine başvuru sağlar. İkinci parametre `e`, yukarıdaki örnekte, bir nesne belirli o anda işlenen olayı geçirir. Nesnenin özelliklerini (ve bazı durumlarda, yöntemlerinden) başvurarak fare olayları ya da sürükle ve bırak olayları aktarılan veri için fareyi konumu gibi bilgi edinebilirsiniz.  
  
 Genellikle her olay ikinci parametre için farklı olay nesne türüne sahip bir olay işleyicisi oluşturur. İçin olanlar gibi bazı olay işleyicileri <xref:System.Windows.Forms.Control.MouseDown> ve <xref:System.Windows.Forms.Control.MouseUp> olayları, kendi ikinci parametre için aynı nesne türü vardır. Bu olaylar türleri için her iki olayları işlemek için aynı olay işleyicisi kullanabilirsiniz.  
  
 Aynı olay işleyicisi, farklı denetimleri için aynı olayını işlemek için de kullanabilirsiniz. Örneğin, bir grup varsa <xref:System.Windows.Forms.RadioButton> formdaki denetimler, bir tek olay işleyicisi oluşturabilir <xref:System.Windows.Forms.Control.Click> olay ve her bir denetimin <xref:System.Windows.Forms.Control.Click> olay tek olay işleyicisine bağımlı. Daha fazla bilgi için bkz: [nasıl yapılır: Windows Forms'ta tek olay işleyicisine birden çok olay bağlanmak](../../../docs/framework/winforms/how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Windows Forms'ta olay işleyicileri oluşturma](../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md)  
 [Olaylara genel bakış](../../../docs/framework/winforms/events-overview-windows-forms.md)
