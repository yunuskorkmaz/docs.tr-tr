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
# <a name="how-to-send-data-to-the-active-mdi-child"></a>Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme
Genellikle, [birden çok belgeli arabirim (MDI) uygulamaları](multiple-document-interface-mdi-applications.md)bağlamında, Kullanıcı panodan VERILERI bir MDI uygulamasına yapıştırılırken olduğu gibi, etkin alt pencereye veri göndermeniz gerekir.  
  
> [!NOTE]
> Hangi alt pencerenin odağa sahip olduğunu doğrulama ve içeriğini panoya gönderme hakkında daha fazla bilgi için bkz. [ETKIN MDI alt öğesini belirleme](how-to-determine-the-active-mdi-child.md).  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>Panodaki etkin MDI alt penceresine veri göndermek için  
  
1. Bir yöntem içinde Panodaki metni etkin alt formun etkin denetimine kopyalayın.  
  
    > [!NOTE]
    > Bu örnek, bir`Form1` <xref:System.Windows.Forms.RichTextBox> denetim içeren bir veya daha fazla MDI alt penceresi olan bir MDI parent formu () olduğunu varsayar. Daha fazla bilgi için bkz. [MDI parent Forms oluşturma](how-to-create-mdi-parent-forms.md).  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çok Belgeli Arabirim (MDI) Uygulamaları](multiple-document-interface-mdi-applications.md)
- [Nasıl yapılır: MDI üst formları oluşturma](how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: MDI alt formları oluşturma](how-to-create-mdi-child-forms.md)
- [Nasıl yapılır: Etkin MDI alt öğesini belirleme](how-to-determine-the-active-mdi-child.md)
- [Nasıl yapılır: MDI alt formlarını düzenleme](how-to-arrange-mdi-child-forms.md)
