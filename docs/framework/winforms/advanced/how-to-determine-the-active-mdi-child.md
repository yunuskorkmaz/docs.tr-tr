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
ms.openlocfilehash: 57491faa10c182630d41565ba236d65e393929b3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182539"
---
# <a name="how-to-determine-the-active-mdi-child"></a>Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme
Zaman zaman, şu anda etkin olan alt forma odaklanan denetim üzerinde çalışan bir komut sağlamak isteyeceksiniz. Örneğin, seçili metni alt formun metin kutusundan Pano'ya kopyalamak istediğinizi varsayalım. Standart Edit menüsündeki Kopyala menüsündeki <xref:System.Windows.Forms.Control.Click> etkinliğini kullanarak seçili metni Pano'ya kopyalayan bir yordam oluşturursunuz.  
  
 Bir MDI uygulaması aynı alt formun birçok örneğine sahip olabileceğinden, yordamın hangi formu kullanacağını bilmesi gerekir. Doğru formu belirtmek için, <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> odak noktası olan veya en son etkin olan alt formu döndüren özelliği kullanın.  
  
 Form üzerinde birden fazla denetiminiz olduğunda, hangi denetimin etkin olduğunu da belirtmeniz gerekir. <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> Özellik gibi, <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> özellik de etkin alt forma odaklanarak denetimi döndürür. Aşağıdaki yordam, alt form menüsünden, MDI formundaki menüden veya araç çubuğu düğmesinden çağrılabilen bir kopyalama yordamını göstermektedir.  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a>Etkin MDI alt çocuğunu belirlemek için (metnini Panoya kopyalamak için)  
  
1. Bir yöntem içinde, etkin alt formun etkin denetiminin metnini Pano'ya kopyalayın.  
  
    > [!NOTE]
    > Bu örnek, denetim içeren bir veya`Form1`daha fazla MDI alt penceresi <xref:System.Windows.Forms.RichTextBox> olan bir MDI üst formu () olduğunu varsayar. Daha fazla bilgi için Bkz. [MDI Üst Formları Oluşturma.](how-to-create-mdi-parent-forms.md)  
  
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

- [Çoklu Belge Arabirimi (MDI) Uygulamaları](multiple-document-interface-mdi-applications.md)
- [Nasıl yapılır: MDI Üst Formları Oluşturma](how-to-create-mdi-parent-forms.md)
- [Nasıl yapılır: MDI Alt Formları Oluşturma](how-to-create-mdi-child-forms.md)
- [Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme](how-to-send-data-to-the-active-mdi-child.md)
- [Nasıl yapılır: MDI Alt Formlarını Düzenleme](how-to-arrange-mdi-child-forms.md)
