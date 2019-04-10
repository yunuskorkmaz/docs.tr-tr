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
ms.openlocfilehash: 881996563acef36a1981ca6236c155b8fc56ef0a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307329"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a><span data-ttu-id="e8293-102">Nasıl yapılır: Windows Forms CheckBox Denetimleriyle Seçenekleri Ayarlama</span><span class="sxs-lookup"><span data-stu-id="e8293-102">How to: Set Options with Windows Forms CheckBox Controls</span></span>
<span data-ttu-id="e8293-103">Bir Windows Forms <xref:System.Windows.Forms.CheckBox> denetim Evet/Hayır seçenekleri veya True/False kullanıcılara vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e8293-103">A Windows Forms <xref:System.Windows.Forms.CheckBox> control is used to give users True/False or Yes/No options.</span></span> <span data-ttu-id="e8293-104">Seçildiğinde denetim bir onay işareti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e8293-104">The control displays a check mark when it is selected.</span></span>  
  
### <a name="to-set-options-with-checkbox-controls"></a><span data-ttu-id="e8293-105">CheckBox denetimleriyle seçenekleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="e8293-105">To set options with CheckBox controls</span></span>  
  
1. <span data-ttu-id="e8293-106">Değerini incelemek <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği durumunu belirlemek ve bir seçeneği belirlemek için bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="e8293-106">Examine the value of the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine its state, and use that value to set an option.</span></span>  
  
     <span data-ttu-id="e8293-107">Aşağıda, ne zaman kod örneğinde <xref:System.Windows.Forms.CheckBox> denetimin <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayı oluşturulur, formun <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği `false` onay kutusu işaretli değilse.</span><span class="sxs-lookup"><span data-stu-id="e8293-107">In the code sample below, when the <xref:System.Windows.Forms.CheckBox> control's <xref:System.Windows.Forms.CheckBox.CheckedChanged> event is raised, the form's <xref:System.Windows.Forms.Control.AllowDrop%2A> property is set to `false` if the check box is checked.</span></span> <span data-ttu-id="e8293-108">Bu, kullanıcı etkileşimi kısıtlamak istediğiniz durumlarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e8293-108">This is useful for situations where you want to restrict user interaction.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e8293-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8293-109">See also</span></span>

- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="e8293-110">CheckBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e8293-110">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="e8293-111">Nasıl yapılır: Windows Forms CheckBox Tıklamalarına Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="e8293-111">How to: Respond to Windows Forms CheckBox Clicks</span></span>](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [<span data-ttu-id="e8293-112">CheckBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="e8293-112">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
