---
title: "Nasıl yapılır: Windows Forms RichTextBox Denetiminde Biçimlendirme Öznitelikleri Değiştiğinde Belirleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0dc272e26124acf5c6bd5cf3030941c26c021c49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a>Nasıl yapılır: Windows Forms RichTextBox Denetiminde Biçimlendirme Öznitelikleri Değiştiğinde Belirleme
Windows Forms yaygın kullanımı <xref:System.Windows.Forms.RichTextBox> denetim metin yazı tipi seçenekleri veya paragraf stilleri gibi özniteliklerle biçimlendirme. Uygulamanız çok sayıda sözcük uygulamaları olduğu gibi bir araç çubuğunu görüntüleme amacıyla biçimlendirme metin değişiklikleri izlemek gerekebilir.  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a>Biçimlendirme özniteliklerini değişiklikler yanıtlamak için  
  
1.  Kod yazma <xref:System.Windows.Forms.RichTextBox.SelectionChanged> özniteliğin değerine bağlı olarak uygun bir eylem gerçekleştirmek için olay işleyicisi. Aşağıdaki örnek bir araç çubuğu düğmesi değerine bağlı olarak görünümünü değiştirir <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliği. Araç çubuğu düğmesi, yalnızca denetiminde ekleme noktasını taşındığında güncelleştirilecektir.  
  
     Aşağıdaki örnek bir formla varsayar bir <xref:System.Windows.Forms.RichTextBox> denetim ve <xref:System.Windows.Forms.ToolBar> araç çubuğu düğmesi içeren denetimi. Araç çubukları ve araç çubuğu düğmeleri hakkında daha fazla bilgi için bkz: [nasıl yapılır: bir araç çubuğu denetimi düğmelerine ekleme](../../../../docs/framework/winforms/controls/how-to-add-buttons-to-a-toolbar-control.md).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.RichTextBox.SelectionChanged>  
 <xref:System.Windows.Forms.RichTextBox>  
 [RichTextBox denetimi](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [Windows Forms'ta kullanılacak denetimler](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
