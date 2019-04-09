---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetiminde Biçimlendirme Öznitelikleri Değiştiğinde Belirleme'
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
ms.openlocfilehash: e35ebb7c90be00a814d465af3546de2bcd11c5de
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183956"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetiminde Biçimlendirme Öznitelikleri Değiştiğinde Belirleme
Windows Forms yaygın bir kullanımı <xref:System.Windows.Forms.RichTextBox> denetim metin yazı tipi seçenekleri veya stilleri gibi özniteliklerle biçimlendirme. Birçok kelime işleme uygulaması olduğu gibi bir araç çubuğunu görüntüleme amacıyla biçimlendirme metin değişiklikleri izlemek, uygulamanız gerekebilir.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Biçimlendirme öznitelikleri değişikliklere yanıt vermek için  
  
1.  Kod yazmaya <xref:System.Windows.Forms.RichTextBox.SelectionChanged> özniteliğin değerine bağlı olarak uygun bir eylem gerçekleştirmek için olay işleyicisi. Aşağıdaki örnek bir araç çubuğu düğmesinin değerine bağlı olarak değişir <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliği. Araç çubuğu düğmesini yalnızca denetiminde ekleme noktasını taşındığında güncelleştirilecektir.  
  
     Aşağıdaki örnekte bir form varsayar bir <xref:System.Windows.Forms.RichTextBox> denetimi ve bir <xref:System.Windows.Forms.ToolBar> içeren bir araç çubuğu düğmesi denetimi. Araç çubukları ve araç çubuğu düğmeleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: Bir ToolBar denetimine düğme ekleme](how-to-add-buttons-to-a-toolbar-control.md).  
  
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
- [Windows Forms'ta Kullanılacak Denetimler](controls-to-use-on-windows-forms.md)
