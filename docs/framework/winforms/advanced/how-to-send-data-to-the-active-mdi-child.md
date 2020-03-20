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
ms.openlocfilehash: 563be8494cb84dc74b45985d3ba74e4b6a07eb8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182490"
---
# <a name="how-to-send-data-to-the-active-mdi-child"></a>Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme
Genellikle, [Çoklu Belge Arabirimi (MDI) Uygulamaları](multiple-document-interface-mdi-applications.md)bağlamında, kullanıcı panodaki verileri Bir MDI uygulamasına yapıştırdığında olduğu gibi, etkin alt pencereye veri göndermeniz gerekir.  
  
> [!NOTE]
> Hangi alt pencerenin odak noktası olduğunu doğrulamak ve içeriğini Panoya gönderme hakkında bilgi [için](how-to-determine-the-active-mdi-child.md)bkz.  
  
### <a name="to-send-data-to-the-active-mdi-child-window-from-the-clipboard"></a>Panodan etkin MDI alt penceresine veri göndermek için  
  
1. Bir yöntem içinde, Pano'daki metni etkin alt formun etkin denetimine kopyalayın.  
  
    > [!NOTE]
    > Bu örnek, denetim içeren bir veya`Form1`daha fazla MDI alt penceresi <xref:System.Windows.Forms.RichTextBox> olan bir MDI üst formu () olduğunu varsayar. Daha fazla bilgi için Bkz. [MDI Üst Formları Oluşturma.](how-to-create-mdi-parent-forms.md)  
  
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

- [Çoklu Belge Arabirimi (MDI) Uygulamaları](multiple-document-interface-mdi-applications.md)
- [Nasıl yapılır: MDI Üst Formları Oluşturma](how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: MDI Alt Formları Oluşturma](how-to-create-mdi-child-forms.md)
- [Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme](how-to-determine-the-active-mdi-child.md)
- [Nasıl yapılır: MDI Alt Formlarını Düzenleme](how-to-arrange-mdi-child-forms.md)
