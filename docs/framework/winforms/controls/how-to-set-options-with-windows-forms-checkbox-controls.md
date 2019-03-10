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
ms.openlocfilehash: 3eb68d76d936f13e78d13629455c6ac7fb537b40
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714794"
---
# <a name="how-to-set-options-with-windows-forms-checkbox-controls"></a><span data-ttu-id="4ed26-102">Nasıl yapılır: Windows Forms CheckBox denetimleriyle seçenekleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="4ed26-102">How to: Set Options with Windows Forms CheckBox Controls</span></span>
<span data-ttu-id="4ed26-103">Bir Windows Forms <xref:System.Windows.Forms.CheckBox> denetim Evet/Hayır seçenekleri veya True/False kullanıcılara vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4ed26-103">A Windows Forms <xref:System.Windows.Forms.CheckBox> control is used to give users True/False or Yes/No options.</span></span> <span data-ttu-id="4ed26-104">Seçildiğinde denetim bir onay işareti görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4ed26-104">The control displays a check mark when it is selected.</span></span>  
  
### <a name="to-set-options-with-checkbox-controls"></a><span data-ttu-id="4ed26-105">CheckBox denetimleriyle seçenekleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="4ed26-105">To set options with CheckBox controls</span></span>  
  
1.  <span data-ttu-id="4ed26-106">Değerini incelemek <xref:System.Windows.Forms.CheckBox.Checked%2A> özelliği durumunu belirlemek ve bir seçeneği belirlemek için bu değeri kullanın.</span><span class="sxs-lookup"><span data-stu-id="4ed26-106">Examine the value of the <xref:System.Windows.Forms.CheckBox.Checked%2A> property to determine its state, and use that value to set an option.</span></span>  
  
     <span data-ttu-id="4ed26-107">Aşağıda, ne zaman kod örneğinde <xref:System.Windows.Forms.CheckBox> denetimin <xref:System.Windows.Forms.CheckBox.CheckedChanged> olayı oluşturulur, formun <xref:System.Windows.Forms.Control.AllowDrop%2A> özelliği `false` onay kutusu işaretli değilse.</span><span class="sxs-lookup"><span data-stu-id="4ed26-107">In the code sample below, when the <xref:System.Windows.Forms.CheckBox> control's <xref:System.Windows.Forms.CheckBox.CheckedChanged> event is raised, the form's <xref:System.Windows.Forms.Control.AllowDrop%2A> property is set to `false` if the check box is checked.</span></span> <span data-ttu-id="4ed26-108">Bu, kullanıcı etkileşimi kısıtlamak istediğiniz durumlarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="4ed26-108">This is useful for situations where you want to restrict user interaction.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4ed26-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ed26-109">See also</span></span>
- <xref:System.Windows.Forms.CheckBox>
- [<span data-ttu-id="4ed26-110">CheckBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4ed26-110">CheckBox Control Overview</span></span>](checkbox-control-overview-windows-forms.md)
- [<span data-ttu-id="4ed26-111">Nasıl yapılır: Windows Forms CheckBox tıklamalarına yanıt verme</span><span class="sxs-lookup"><span data-stu-id="4ed26-111">How to: Respond to Windows Forms CheckBox Clicks</span></span>](how-to-respond-to-windows-forms-checkbox-clicks.md)
- [<span data-ttu-id="4ed26-112">CheckBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="4ed26-112">CheckBox Control</span></span>](checkbox-control-windows-forms.md)
