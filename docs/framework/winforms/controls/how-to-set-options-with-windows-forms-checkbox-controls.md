---
title: 'Nasıl yapılır: Windows Forms CheckBox denetimleriyle seçenekleri ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- checked
helpviewer_keywords:
- CheckBox control [Windows Forms], checked state
- check boxes [Windows Forms], using to set options
- CheckBox control [Windows Forms], using to set options
ms.assetid: 2ac70498-7e3e-4e07-8901-ccabaeb5fd3e
ms.openlocfilehash: a8159e9e9a2484b95399aba67b1a10b1252a4357
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525566"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Nasıl yapılır: Windows Forms CheckBox denetimleriyle seçenekleri ayarlama
Bir Windows Forms <xref:System.Windows.Forms.CheckBox> denetim Evet/Hayır seçenekleri veya True/False kullanıcılara vermek için kullanılır. Seçildiğinde denetim bir onay işareti görüntüler.  
  
### <a name="to-set-options-with-checkbox-controls"></a>CheckBox denetimleriyle seçenekleri ayarlama  
  
1.  Değerini incelemek <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği durumunu belirlemek ve bir seçeneği belirlemek için bu değeri kullanın.  
  
     Aşağıda, ne zaman kod örneğinde <xref:System.Windows.Forms.CheckBox> denetimin <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayı oluşturulur, formun <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği `false` onay kutusu işaretli değilse. Bu, kullanıcı etkileşimi kısıtlamak istediğiniz durumlarda kullanışlıdır.  
  
    ```vb  
    Private Sub CheckBox1_CheckedChanged(ByVal sender As System.Object, _  
       ByVal e As System.EventArgs) Handles CheckBox1.CheckedChanged  
       ' Determine the CheckState of the check box.  
       If CheckBox1.CheckState = CheckState.Checked Then  
          ' If checked, do not allow items to be dragged onto the form.  
          Me.AllowDrop = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void checkBox1_CheckedChanged(object sender, System.EventArgs e)  
    {  
       // Determine the CheckState of the check box.  
       if (checkBox1.CheckState == CheckState.Checked)   
       {  
          // If checked, do not allow items to be dragged onto the form.  
          this.AllowDrop = false;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void checkBox1_CheckedChanged(System::Object ^ sender,  
          System::EventArgs ^ e)  
       {  
          // Determine the CheckState of the check box.  
          if (checkBox1->CheckState == CheckState::Checked)   
          {  
             // If checked, do not allow items to be dragged onto the form.  
             this->AllowDrop = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.CheckBox>
- [CheckBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)
- [Nasıl yapılır: Windows Forms CheckBox tıklamalarına yanıt verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)
- [CheckBox Denetimi](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
