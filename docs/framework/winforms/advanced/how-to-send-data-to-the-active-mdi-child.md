---
title: 'Nasıl yapılır: Etkin MDI alt öğesine veri gönderme'
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
ms.openlocfilehash: dab72d64cdd013125ae7c302ccf297ecdc0c98b3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589991"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a><span data-ttu-id="30834-102">Nasıl yapılır: Etkin MDI alt öğesine veri gönderme</span><span class="sxs-lookup"><span data-stu-id="30834-102">How to: Send Data to the Active MDI Child</span></span>
<span data-ttu-id="30834-103">Genellikle, bağlamında [Çok Belgeli Arabirim (MDI) uygulamaları](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), ne zaman kullanıcı Pano'dan veri bir MDI uygulaması yapıştırır gibi etkin alt pencerenin veri göndermek ihtiyacınız olacak.</span><span class="sxs-lookup"><span data-stu-id="30834-103">Often, within the context of [Multiple-Document Interface (MDI) Applications](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md), you will need to send data to the active child window, such as when the user pastes data from the Clipboard into an MDI application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="30834-104">Hangi alt pencerenin odaklanmış doğrulama ve içeriği panoya gönderme hakkında daha fazla bilgi için bkz. [etkin MDI alt belirleme](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md).</span><span class="sxs-lookup"><span data-stu-id="30834-104">For information about verifying which child window has focus and sending its contents to the Clipboard, see [Determining the Active MDI Child](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md).</span></span>  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a><span data-ttu-id="30834-105">Etkin MDI alt penceresine panodan veri göndermesini</span><span class="sxs-lookup"><span data-stu-id="30834-105">To send data to the active MDI child window from the Clipboard</span></span>  
  
1.  <span data-ttu-id="30834-106">Bir yöntem içinde etkin alt formunun etkin denetimi için metni panoya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="30834-106">Within a method, copy the text on the Clipboard to the active control of the active child form.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="30834-107">Bu örnek MDI üst formu olduğunu varsayar (`Form1`) içeren bir veya daha fazla MDI alt pencereleri olan bir <xref:System.Windows.Forms.RichTextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="30834-107">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="30834-108">Daha fazla bilgi için [MDI üst formları oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="30834-108">For more information, see [Creating MDI Parent Forms](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="30834-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30834-109">See also</span></span>
- [<span data-ttu-id="30834-110">Çok Belgeli Arabirim (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="30834-110">Multiple-Document Interface (MDI) Applications</span></span>](../../../../docs/framework/winforms/advanced/multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="30834-111">Nasıl yapılır: MDI üst formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="30834-111">How to: Create MDI Parent Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="30834-112">Nasıl yapılır: MDI alt formları oluştur</span><span class="sxs-lookup"><span data-stu-id="30834-112">How to: Create MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="30834-113">Nasıl yapılır: Etkin MDI alt öğesini belirleme</span><span class="sxs-lookup"><span data-stu-id="30834-113">How to: Determine the Active MDI Child</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-active-mdi-child.md)
- [<span data-ttu-id="30834-114">Nasıl yapılır: MDI alt formlarını düzenleme</span><span class="sxs-lookup"><span data-stu-id="30834-114">How to: Arrange MDI Child Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-arrange-mdi-child-forms.md)
