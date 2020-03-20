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
ms.openlocfilehash: ffec8a9f8e080dec78152e62e00e2dceefbdaab0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141698"
---
# <a name="event-handlers-overview-windows-forms"></a>Olay İşleyicilerine Genel Bakış (Windows Forms)
Olay işleyicisi, bir olaya bağlı bir yöntemdir. Olay yükseltildiğinde, olay işleyicisi içindeki kod yürütülür. Her olay işleyicisi, olayı düzgün şekilde işlemenize olanak tanıyan iki parametre sağlar. Aşağıdaki örnekte, bir <xref:System.Windows.Forms.Button> denetim olayı için <xref:System.Windows.Forms.Control.Click> bir olay işleyicisi gösterilmektedir.  
  
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
  
 İlk parametre,`sender`olayı yükselten nesneye bir başvuru sağlar. İkinci parametre, `e`yukarıdaki örnekte, işlenen olaya özgü bir nesne geçer. Nesnenin özelliklerine (ve bazen yöntemlerine) başvurarak, fare olayları veya sürükle ve bırak olaylarında aktarılan veriler için farenin konumu gibi bilgileri elde edebilirsiniz.  
  
 Genellikle her olay, ikinci parametre için farklı bir olay nesnesi türüne sahip bir olay işleyicisi üretir. Bazı olay işleyicileri, bu <xref:System.Windows.Forms.Control.MouseDown> ve <xref:System.Windows.Forms.Control.MouseUp> olaylar için olanlar gibi, ikinci parametre için aynı nesne türü ne var. Bu tür olaylar için, her iki olayı işlemek için aynı olay işleyicisini kullanabilirsiniz.  
  
 Aynı olay işleyicisini farklı denetimler için aynı olayı işlemek için de kullanabilirsiniz. Örneğin, formda bir denetim <xref:System.Windows.Forms.RadioButton> grubunuz varsa, olay için tek bir olay <xref:System.Windows.Forms.Control.Click> işleyicisi oluşturabilir <xref:System.Windows.Forms.Control.Click> ve her denetimin olayının tek olay işleyicisine bağlanmasını sağlayabilirsiniz. Daha fazla bilgi için [bkz: Windows Formlarında Birden Çok Olayı Tek Bir Olay İşleyicisine Bağlayın.](how-to-connect-multiple-events-to-a-single-event-handler-in-windows-forms.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Windows Forms'ta Olay İşleyicileri Oluşturma](creating-event-handlers-in-windows-forms.md)
- [Olaylara Genel Bakış](events-overview-windows-forms.md)
