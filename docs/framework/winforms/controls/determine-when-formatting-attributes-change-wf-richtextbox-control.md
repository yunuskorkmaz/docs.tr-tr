---
title: RichTextBox denetiminde biçimlendirme öznitelikleri değiştiğinde belirleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- RichTextBox control [Windows Forms], determining font changes
- text boxes [Windows Forms], determining font changes
- SelChange event
ms.assetid: bdfed015-f77a-41e5-b38f-f8629b2fa166
ms.openlocfilehash: f9b2a1028f79059ec7d4d6bf3683100455bb5dea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746041"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetiminde Biçimlendirme Öznitelikleri Değiştiğinde Belirleme
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetiminin yaygın kullanımı, yazı tipi seçenekleri veya paragraf stilleri gibi özniteliklerle biçimlendirme metinleridir. Uygulamanızın birçok sözcük işleme uygulamasında olduğu gibi, bir araç çubuğunu görüntülemek amacıyla metin biçimlendirmesinde değişiklik yapması gerekebilir.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Biçimlendirme özniteliklerinde değişikliklere yanıt vermek için  
  
1. Özniteliğin değerine bağlı olarak uygun bir eylem gerçekleştirmek için <xref:System.Windows.Forms.RichTextBox.SelectionChanged> olay işleyicisine kod yazın. Aşağıdaki örnek, <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliğinin değerine bağlı olarak bir araç çubuğu düğmesinin görünümünü değiştirir. Araç çubuğu düğmesi yalnızca ekleme noktası denetimde taşındığında güncelleştirilir.  
  
     Aşağıdaki örnekte, bir <xref:System.Windows.Forms.RichTextBox> denetimi olan bir form ve bir araç çubuğu düğmesi içeren bir <xref:System.Windows.Forms.ToolBar> denetimi varsayılır. Araç çubukları ve araç çubuğu düğmeleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: araç çubuğu denetimine düğme ekleme](how-to-add-buttons-to-a-toolbar-control.md).  
  
    ```vb  
    ' The following code assumes the existence of a toolbar control  
    ' with at least one toolbar button.  
    Private Sub RichTextBox1_SelectionChanged(ByVal sender As Object, ByVal e As System.EventArgs) Handles RichTextBox1.SelectionChanged  
       If RichTextBox1.SelectionBullet = True Then  
          ' Bullet button on toolbar should appear pressed  
          ToolBarButton1.Pushed = True  
       Else  
           ' Bullet button on toolbar should appear unpressed  
           ToolBarButton1.Pushed = False  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private void richTextBox1_SelectionChanged(object sender,  
    System.EventArgs e)  
    {  
       if (richTextBox1.SelectionBullet == true)   
       {  
          // Bullet button on toolbar should appear pressed  
          toolBarButton1.Pushed = true;  
       }  
       else   
       {  
          // Bullet button on toolbar should appear unpressed  
          toolBarButton1.Pushed = false;  
       }  
    }  
    ```  
  
    ```cpp  
    // The following code assumes the existence of a toolbar control  
    // with at least one toolbar button.  
    private:  
       System::Void richTextBox1_SelectionChanged(  
          System::Object ^  sender, System::EventArgs ^  e)  
       {  
          if (richTextBox1->SelectionBullet == true)  
          {  
             // Bullet button on toolbar should appear pressed  
             toolBarButton1->Pushed = true;  
          }  
          else  
          {  
             // Bullet button on toolbar should appear unpressed  
             toolBarButton1->Pushed = false;  
          }  
       }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [RichTextBox Denetimi](richtextbox-control-windows-forms.md)
- [Windows Forms'da Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
