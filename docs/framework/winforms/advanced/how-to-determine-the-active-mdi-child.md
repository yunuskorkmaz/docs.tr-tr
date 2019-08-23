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
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="c0c9f-102">Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme</span><span class="sxs-lookup"><span data-stu-id="c0c9f-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="c0c9f-103">Bazen, geçerli etkin alt form üzerinde odağa sahip olan denetimde çalışan bir komut sağlamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="c0c9f-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="c0c9f-104">Örneğin, alt formun metin kutusundan seçili metni pano 'ya kopyalamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="c0c9f-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="c0c9f-105">Standart düzenleme menüsündeki Kopyala menü öğesinin <xref:System.Windows.Forms.Control.Click> olayını kullanarak seçili metni panoya kopyalayan bir yordam oluşturacaksınız.</span><span class="sxs-lookup"><span data-stu-id="c0c9f-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="c0c9f-106">Bir MDI uygulamasının aynı alt formun birçok örneği olabileceğinden, yordamın hangi formun kullanılacağını bilmeleri gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0c9f-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="c0c9f-107">Doğru formu belirtmek için, odağa sahip olan <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> veya en son etkin olan alt formu döndüren özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c0c9f-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="c0c9f-108">Form üzerinde çeşitli denetimleriniz olduğunda, hangi denetimin etkin olduğunu da belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c0c9f-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="c0c9f-109"><xref:System.Windows.Forms.Form.ActiveMdiChild%2A> Özelliği gibi<xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> , özelliği de etkin alt form üzerinde odak olan denetimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="c0c9f-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="c0c9f-110">Aşağıdaki yordam alt form menüsünden çağrılabilen bir kopyalama yordamını, MDI formundaki menüyü veya bir araç çubuğu düğmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0c9f-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="c0c9f-111">Etkin MDI alt öğesini belirleme (metnini panoya kopyalamak için)</span><span class="sxs-lookup"><span data-stu-id="c0c9f-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1. <span data-ttu-id="c0c9f-112">Bir yöntem içinde, etkin alt formun etkin denetiminin metnini panoya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="c0c9f-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c0c9f-113">Bu örnek, bir`Form1` <xref:System.Windows.Forms.RichTextBox> denetim içeren bir veya daha fazla MDI alt penceresi olan bir MDI parent formu () olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="c0c9f-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="c0c9f-114">Daha fazla bilgi için bkz. [MDI parent Forms oluşturma](how-to-create-mdi-parent-forms.md).</span><span class="sxs-lookup"><span data-stu-id="c0c9f-114">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c0c9f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0c9f-115">See also</span></span>

- [<span data-ttu-id="c0c9f-116">Çok Belgeli Arabirim (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="c0c9f-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="c0c9f-117">Nasıl yapılır: MDI üst formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0c9f-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="c0c9f-118">Nasıl yapılır: MDI alt formları oluşturma</span><span class="sxs-lookup"><span data-stu-id="c0c9f-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="c0c9f-119">Nasıl yapılır: Etkin MDI alt öğesine veri gönderme</span><span class="sxs-lookup"><span data-stu-id="c0c9f-119">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="c0c9f-120">Nasıl yapılır: MDI alt formlarını düzenleme</span><span class="sxs-lookup"><span data-stu-id="c0c9f-120">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
