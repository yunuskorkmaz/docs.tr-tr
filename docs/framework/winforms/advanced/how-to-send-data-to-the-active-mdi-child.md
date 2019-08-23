---
title: 'Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- child forms
- MDI [Windows Forms], sending data to forms
- Clipboard [Windows Forms], pasting
- Clipboard [Windows Forms], getting data from
ms.assetid: 1047d2fe-1235-46db-aad9-563aea1d743b
ms.openlocfilehash: 0a7a2475891488d1fdd60f0db4a483c144a73f0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947840"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a><span data-ttu-id="7e091-102">Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme</span><span class="sxs-lookup"><span data-stu-id="7e091-102">How to: Send Data to the Active MDI Child</span></span>
<span data-ttu-id="7e091-103">Genellikle, [birden çok belgeli arabirim (MDI) uygulamaları](multiple-document-interface-mdi-applications.md)bağlamında, Kullanıcı panodan VERILERI bir MDI uygulamasına yapıştırılırken olduğu gibi, etkin alt pencereye veri göndermeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7e091-103">Often, within the context of [Multiple-Document Interface (MDI) Applications](multiple-document-interface-mdi-applications.md), you will need to send data to the active child window, such as when the user pastes data from the Clipboard into an MDI application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7e091-104">Hangi alt pencerenin odağa sahip olduğunu doğrulama ve içeriğini panoya gönderme hakkında daha fazla bilgi için bkz. [ETKIN MDI alt öğesini belirleme](how-to-determine-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="7e091-104">For information about verifying which child window has focus and sending its contents to the Clipboard, see [Determining the Active MDI Child](how-to-determine-the-active-mdi-child.md).</span></span>  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a><span data-ttu-id="7e091-105">Panodaki etkin MDI alt penceresine veri göndermek için</span><span class="sxs-lookup"><span data-stu-id="7e091-105">To send data to the active MDI child window from the Clipboard</span></span>  
  
1. <span data-ttu-id="7e091-106">Bir yöntem içinde Panodaki metni etkin alt formun etkin denetimine kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="7e091-106">Within a method, copy the text on the Clipboard to the active control of the active child form.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7e091-107">Bu örnek, bir`Form1` <xref:System.Windows.Forms.RichTextBox> denetim içeren bir veya daha fazla MDI alt penceresi olan bir MDI parent formu () olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="7e091-107">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="7e091-108">Daha fazla bilgi için bkz. [MDI parent Forms oluşturma](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="7e091-108">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
    ```vb  
    Public Sub mniPaste_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniPaste.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ParentForm.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Try  
             Dim theBox As RichTextBox = Ctype(activeChild.ActiveControl, RichTextBox)  
             If (Not theBox Is Nothing) Then  
                ' Create a new instance of the DataObject interface.  
                Dim data As IDataObject = Clipboard.GetDataObject()  
                ' If the data is text, then set the text of the   
                ' RichTextBox to the text in the clipboard.  
                If (data.GetDataPresent(DataFormats.Text)) Then  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString()  
                End If  
             End If  
          Catch  
             MessageBox.Show("You need to select a RichTextBox.")  
          End Try  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniPaste_Click (object sender, System.EventArgs e)  
    {  
      // Determine the active child form.  
       Form activeChild = this.ParentForm.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {  
          try   
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Create a new instance of the DataObject interface.  
                IDataObject data = Clipboard.GetDataObject();  
                // If the data is text, then set the text of the   
                // RichTextBox to the text in the clipboard.  
                if (data.GetDataPresent(DataFormats.Text))  
                {  
                   theBox.SelectedText = data.GetData(DataFormats.Text).ToString();                 
                }  
             }  
          }  
          catch   
          {  
             MessageBox.Show("You need to select a RichTextBox.");  
          }  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="7e091-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e091-109">See also</span></span>

- [<span data-ttu-id="7e091-110">Çok Belgeli Arabirim (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="7e091-110">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="7e091-111">Nasıl yapılır: MDI üst formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e091-111">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="7e091-112">Nasıl yapılır: MDI alt formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="7e091-112">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="7e091-113">Nasıl yapılır: Etkin MDI alt öğesini belirleme</span><span class="sxs-lookup"><span data-stu-id="7e091-113">How to: Determine the Active MDI Child</span></span>](how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="7e091-114">Nasıl yapılır: MDI alt formlarını düzenleme</span><span class="sxs-lookup"><span data-stu-id="7e091-114">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
