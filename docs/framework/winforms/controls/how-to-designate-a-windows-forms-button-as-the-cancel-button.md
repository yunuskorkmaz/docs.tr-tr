---
title: 'Nasıl yapılır: Bir Windows Forms düğmesini iptal düğmesi olarak belirtme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: 74d025677682735fc7f1c68116b2364887f0519c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701475"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>Nasıl yapılır: Bir Windows Forms düğmesini iptal düğmesi olarak belirtme
Herhangi bir Windows formunda, belirlediğiniz bir <xref:System.Windows.Forms.Button> iptal düğmesi olarak denetimi. Her kullanıcının hangi bağımsız olarak form üzerindeki diğer denetim odağa sahip ESC tuşuna bastığında iptal düğmesine tıklandığında. Böyle bir düğme, kullanıcının herhangi bir işlem taahhüt vermek zorunda kalmadan bir işlemi hızlı bir şekilde çıkmak etkinleştirmek için genellikle programlanır.  
  
### <a name="to-designate-the-cancel-button"></a>İptal düğmesi atamak için  
  
1.  Formun <xref:System.Windows.Forms.Form.CancelButton%2A> özelliğini uygun <xref:System.Windows.Forms.Button> denetimi.  
  
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
- [Düğme Kontrolüne Genel Bakış](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)
- [Windows Forms Düğme Kontrolü Seçme Yolları](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)
- [Nasıl yapılır: Windows Forms düğme tıklamalarına yanıt verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)
- [Nasıl yapılır: Bir Windows Forms düğmesini kabul et düğmesi olarak belirtme](../../../../docs/framework/winforms/controls/how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Düğme Kontrolü](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
