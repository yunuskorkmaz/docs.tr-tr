---
title: 'Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama'
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
ms.openlocfilehash: dc9e7b1aea74874c66bf9eb96a5b919ed9b4b73b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534092"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a>Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama
Windows Forms <xref:System.Windows.Forms.CheckBox> denetim Evet/Hayır seçenekleri veya kullanıcılara True/False vermek için kullanılır. Seçili olduğunda denetimi bir onay işareti görüntülenir.  
  
### <a name="to-set-options-with-checkbox-controls"></a>CheckBox denetimleriyle seçenekleri ayarlamak için  
  
1.  Değerini inceleyin <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliğini durumunu belirlemek ve bir seçenek ayarlamak için bu değeri kullanın.  
  
     Aşağıda, ne zaman kod örneğinde <xref:System.Windows.Forms.CheckBox> denetimin <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayı, formun <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği ayarlanmış `false` onay kutusu işaretli değilse. Bu, kullanıcı etkileşimi kısıtlamak istediğiniz durumlarda kullanışlıdır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.CheckBox>  
 [CheckBox Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/checkbox-control-overview-windows-forms.md)  
 [Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-checkbox-clicks.md)  
 [CheckBox Denetimi](../../../../docs/framework/winforms/controls/checkbox-control-windows-forms.md)
