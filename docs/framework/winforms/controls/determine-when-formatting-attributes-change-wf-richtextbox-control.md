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
# <a name="how-to-determine-when-formatting-attributes-change-in-the-windows-forms-richtextbox-control"></a><span data-ttu-id="a92a9-102">Nasıl yapılır: Windows Forms RichTextBox Denetiminde Biçimlendirme Öznitelikleri Değiştiğinde Belirleme</span><span class="sxs-lookup"><span data-stu-id="a92a9-102">How to: Determine When Formatting Attributes Change in the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="a92a9-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetiminin yaygın kullanımı, yazı tipi seçenekleri veya paragraf stilleri gibi özniteliklerle biçimlendirme metinleridir.</span><span class="sxs-lookup"><span data-stu-id="a92a9-103">A common use of the Windows Forms <xref:System.Windows.Forms.RichTextBox> control is formatting text with attributes such as font options or paragraph styles.</span></span> <span data-ttu-id="a92a9-104">Uygulamanızın birçok sözcük işleme uygulamasında olduğu gibi, bir araç çubuğunu görüntülemek amacıyla metin biçimlendirmesinde değişiklik yapması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="a92a9-104">Your application may need to keep track of any changes in text formatting for the purpose of displaying a toolbar, as in many word-processing applications.</span></span>  
  
### <a name="to-respond-to-changes-in-formatting-attributes"></a><span data-ttu-id="a92a9-105">Biçimlendirme özniteliklerinde değişikliklere yanıt vermek için</span><span class="sxs-lookup"><span data-stu-id="a92a9-105">To respond to changes in formatting attributes</span></span>  
  
1. <span data-ttu-id="a92a9-106">Özniteliğin değerine bağlı olarak uygun bir eylem gerçekleştirmek için <xref:System.Windows.Forms.RichTextBox.SelectionChanged> olay işleyicisine kod yazın.</span><span class="sxs-lookup"><span data-stu-id="a92a9-106">Write code in the <xref:System.Windows.Forms.RichTextBox.SelectionChanged> event handler to perform an appropriate action depending on the value of the attribute.</span></span> <span data-ttu-id="a92a9-107">Aşağıdaki örnek, <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> özelliğinin değerine bağlı olarak bir araç çubuğu düğmesinin görünümünü değiştirir.</span><span class="sxs-lookup"><span data-stu-id="a92a9-107">The following example changes the appearance of a toolbar button depending on the value of the <xref:System.Windows.Forms.RichTextBox.SelectionBullet%2A> property.</span></span> <span data-ttu-id="a92a9-108">Araç çubuğu düğmesi yalnızca ekleme noktası denetimde taşındığında güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a92a9-108">The toolbar button will only be updated when the insertion point is moved in the control.</span></span>  
  
     <span data-ttu-id="a92a9-109">Aşağıdaki örnekte, bir <xref:System.Windows.Forms.RichTextBox> denetimi olan bir form ve bir araç çubuğu düğmesi içeren bir <xref:System.Windows.Forms.ToolBar> denetimi varsayılır.</span><span class="sxs-lookup"><span data-stu-id="a92a9-109">The example below assumes a form with a <xref:System.Windows.Forms.RichTextBox> control and a <xref:System.Windows.Forms.ToolBar> control that contains a toolbar button.</span></span> <span data-ttu-id="a92a9-110">Araç çubukları ve araç çubuğu düğmeleri hakkında daha fazla bilgi için bkz. [nasıl yapılır: araç çubuğu denetimine düğme ekleme](how-to-add-buttons-to-a-toolbar-control.md).</span><span class="sxs-lookup"><span data-stu-id="a92a9-110">For more information about toolbars and toolbar buttons, see [How to: Add Buttons to a ToolBar Control](how-to-add-buttons-to-a-toolbar-control.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a92a9-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a92a9-111">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox.SelectionChanged>
- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="a92a9-112">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="a92a9-112">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="a92a9-113">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="a92a9-113">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
