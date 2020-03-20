---
title: RichTextBox Denetiminde Öznitelikleri BiçimlendirmeNin Ne Zaman Değişeceğini Belirleyin
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
ms.openlocfilehash: a190c3479b58464763e0eefdd32d14e88a1f05e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142270"
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetiminde Biçimlendirme Öznitelikleri Değiştiğinde Belirleme
Windows Forms <xref:System.Windows.Forms.RichTextBox> denetiminin yaygın kullanımı, metni yazı tipi seçenekleri veya paragraf stilleri gibi özniteliklerle biçimlendirmektir. Uygulamanızın, birçok sözcük işleme uygulamasında olduğu gibi, bir araç çubuğunu görüntülemek amacıyla metin biçimlendirmesindeki değişiklikleri izlemesi gerekebilir.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Biçimlendirme özniteliklerindeki değişikliklere yanıt vermek için  
  
1. Özniteliğin <xref:System.Windows.Forms.RichTextBox.SelectionChanged> değerine bağlı olarak uygun bir eylem gerçekleştirmek için olay işleyicisi kodu yazın. Aşağıdaki örnek, <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliğin değerine bağlı olarak bir araç çubuğu düğmesinin görünümünü değiştirir. Araç çubuğu düğmesi yalnızca ekleme noktası denetimde taşındığında güncelleştirilir.  
  
     Aşağıdaki örnekte, denetimli <xref:System.Windows.Forms.RichTextBox> bir form <xref:System.Windows.Forms.ToolBar> ve araç çubuğu düğmesi içeren bir denetim varsayar. Araç çubukları ve araç çubuğu düğmeleri hakkında daha fazla bilgi için [bkz.](how-to-add-buttons-to-a-toolbar-control.md)  
  
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
