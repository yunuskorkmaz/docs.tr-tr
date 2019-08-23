---
title: 'Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- MDI [Windows Forms], child windows
- child forms
- MDI [Windows Forms], activating forms
- MDI [Windows Forms], locating focus
ms.assetid: 33880ec3-0207-4c2b-a616-ff140443cc0f
ms.openlocfilehash: 91100b37e4cae9041479b209e40034efe376df5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946213"
---
# <a name="how-to-determine-the-active-mdi-child"></a>Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme
Bazen, geçerli etkin alt form üzerinde odağa sahip olan denetimde çalışan bir komut sağlamak isteyeceksiniz. Örneğin, alt formun metin kutusundan seçili metni pano 'ya kopyalamak istediğinizi varsayalım. Standart düzenleme menüsündeki Kopyala menü öğesinin <xref:System.Windows.Forms.Control.Click> olayını kullanarak seçili metni panoya kopyalayan bir yordam oluşturacaksınız.  
  
 Bir MDI uygulamasının aynı alt formun birçok örneği olabileceğinden, yordamın hangi formun kullanılacağını bilmeleri gerekir. Doğru formu belirtmek için, odağa sahip olan <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> veya en son etkin olan alt formu döndüren özelliğini kullanın.  
  
 Form üzerinde çeşitli denetimleriniz olduğunda, hangi denetimin etkin olduğunu da belirtmeniz gerekir. <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> Özelliği gibi<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> , özelliği de etkin alt form üzerinde odak olan denetimi döndürür. Aşağıdaki yordam alt form menüsünden çağrılabilen bir kopyalama yordamını, MDI formundaki menüyü veya bir araç çubuğu düğmesini gösterir.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Etkin MDI alt öğesini belirleme (metnini panoya kopyalamak için)  
  
1. Bir yöntem içinde, etkin alt formun etkin denetiminin metnini panoya kopyalayın.  
  
    > [!NOTE]
    > Bu örnek, bir`Form1` <xref:System.Windows.Forms.RichTextBox> denetim içeren bir veya daha fazla MDI alt penceresi olan bir MDI parent formu () olduğunu varsayar. Daha fazla bilgi için bkz. [MDI parent Forms oluşturma](how-to-create-mdi-parent-forms.md).  
  
    ```vb  
    Public Sub mniCopy_Click(ByVal sender As Object, _  
       ByVal e As System.EventArgs) Handles mniCopy.Click  
  
       ' Determine the active child form.  
       Dim activeChild As Form = Me.ActiveMDIChild  
  
       ' If there is an active child form, find the active control, which  
       ' in this example should be a RichTextBox.  
       If (Not activeChild Is Nothing) Then  
          Dim theBox As RichTextBox = _  
            TryCast(activeChild.ActiveControl, RichTextBox)  
  
          If (Not theBox Is Nothing) Then  
             'Put selected text on Clipboard.  
             Clipboard.SetDataObject(theBox.SelectedText)  
          Else  
             MessageBox.Show("You need to select a RichTextBox.")  
          End If  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    protected void mniCopy_Click (object sender, System.EventArgs e)  
    {  
       // Determine the active child form.  
       Form activeChild = this.ActiveMdiChild;  
  
       // If there is an active child form, find the active control, which  
       // in this example should be a RichTextBox.  
       if (activeChild != null)  
       {    
          try  
          {  
             RichTextBox theBox = (RichTextBox)activeChild.ActiveControl;  
             if (theBox != null)  
             {  
                // Put the selected text on the Clipboard.  
                Clipboard.SetDataObject(theBox.SelectedText);  
  
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
- [Nasıl yapılır: Etkin MDI alt öğesine veri gönderme](how-to-send-data-to-the-active-mdi-child.md)
- [Nasıl yapılır: MDI alt formlarını düzenleme](how-to-arrange-mdi-child-forms.md)
