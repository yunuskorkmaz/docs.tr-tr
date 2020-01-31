---
title: Bir düğmeyi Iptal düğmesi olarak belirleyin
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 123b3e275065efadd24815320ea7d855808e60b9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743253"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Nasıl yapılır: Bir Windows Forms Düğmesini İptal Düğmesi Olarak Belirtme
Herhangi bir Windows formunda, bir <xref:System.Windows.Forms.Button> denetimini iptal düğmesi olacak şekilde belirleyebilirsiniz. Kullanıcı, form üzerindeki diğer denetimin odağa sahip olduğu bağımsız olarak ESC tuşuna bastığında bir iptal düğmesi görüntülenir. Bu tür bir düğme, genellikle kullanıcının herhangi bir eylemde bulunmadan bir işlemden hızlı bir şekilde çıkmasına olanak tanımak üzere programlanır.  
  
### <a name="to-designate-the-cancel-button"></a>İptal düğmesini belirlemek için  
  
1. Formun <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğini uygun <xref:System.Windows.Forms.Button> denetimine ayarlayın.  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Düğme Kontrolüne Genel Bakış](button-control-overview-windows-forms.md)
- [Windows Forms Düğme Kontrolü Seçme Yolları](ways-to-select-a-windows-forms-button-control.md)
- [Nasıl yapılır: Windows Forms Düğme Tıklamalarına Yanıt Verme](how-to-respond-to-windows-forms-button-clicks.md)
- [Nasıl yapılır: Bir Windows Forms Düğmesini Kabul Et Düğmesi Olarak Belirtme](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Düğme Kontrolü](button-control-windows-forms.md)
