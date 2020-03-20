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
# <a name="how-to-determine-the-active-mdi-child"></a><span data-ttu-id="1eda3-102">Nasıl yapılır: Etkin MDI Alt Öğesini Belirleme</span><span class="sxs-lookup"><span data-stu-id="1eda3-102">How to: Determine the Active MDI Child</span></span>
<span data-ttu-id="1eda3-103">Zaman zaman, şu anda etkin olan alt forma odaklanan denetim üzerinde çalışan bir komut sağlamak isteyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1eda3-103">On occasion, you will want to provide a command that operates on the control that has focus on the currently active child form.</span></span> <span data-ttu-id="1eda3-104">Örneğin, seçili metni alt formun metin kutusundan Pano'ya kopyalamak istediğinizi varsayalım.</span><span class="sxs-lookup"><span data-stu-id="1eda3-104">For example, suppose you want to copy selected text from the child form's text box to the Clipboard.</span></span> <span data-ttu-id="1eda3-105">Standart Edit menüsündeki Kopyala menüsündeki <xref:System.Windows.Forms.Control.Click> etkinliğini kullanarak seçili metni Pano'ya kopyalayan bir yordam oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="1eda3-105">You would create a procedure that copies selected text to the Clipboard using the <xref:System.Windows.Forms.Control.Click> event of the Copy menu item on the standard Edit menu.</span></span>  
  
 <span data-ttu-id="1eda3-106">Bir MDI uygulaması aynı alt formun birçok örneğine sahip olabileceğinden, yordamın hangi formu kullanacağını bilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="1eda3-106">Because an MDI application can have many instances of the same child form, the procedure needs to know which form to use.</span></span> <span data-ttu-id="1eda3-107">Doğru formu belirtmek için, <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> odak noktası olan veya en son etkin olan alt formu döndüren özelliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="1eda3-107">To specify the correct form, use the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, which returns the child form that has the focus or that was most recently active.</span></span>  
  
 <span data-ttu-id="1eda3-108">Form üzerinde birden fazla denetiminiz olduğunda, hangi denetimin etkin olduğunu da belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="1eda3-108">When you have several controls on a form, you also need to specify which control is active.</span></span> <span data-ttu-id="1eda3-109"><xref:System.Windows.Forms.Form.ActiveMdiChild%2A> Özellik gibi, <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> özellik de etkin alt forma odaklanarak denetimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1eda3-109">Like the <xref:System.Windows.Forms.Form.ActiveMdiChild%2A> property, the <xref:System.Windows.Forms.ContainerControl.ActiveControl%2A> property returns the control with the focus on the active child form.</span></span> <span data-ttu-id="1eda3-110">Aşağıdaki yordam, alt form menüsünden, MDI formundaki menüden veya araç çubuğu düğmesinden çağrılabilen bir kopyalama yordamını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="1eda3-110">The procedure below illustrates a copy procedure that can be called from a child form menu, a menu on the MDI form, or a toolbar button.</span></span>  
  
### <a name="to-determine-the-active-mdi-child-to-copy-its-text-to-the-clipboard"></a><span data-ttu-id="1eda3-111">Etkin MDI alt çocuğunu belirlemek için (metnini Panoya kopyalamak için)</span><span class="sxs-lookup"><span data-stu-id="1eda3-111">To determine the active MDI child (to copy its text to the Clipboard)</span></span>  
  
1. <span data-ttu-id="1eda3-112">Bir yöntem içinde, etkin alt formun etkin denetiminin metnini Pano'ya kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="1eda3-112">Within a method, copy the text of the active control of the active child form to the Clipboard.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="1eda3-113">Bu örnek, denetim içeren bir veya`Form1`daha fazla MDI alt penceresi <xref:System.Windows.Forms.RichTextBox> olan bir MDI üst formu () olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="1eda3-113">This example assumes there is an MDI parent form (`Form1`) that has one or more MDI child windows containing a <xref:System.Windows.Forms.RichTextBox> control.</span></span> <span data-ttu-id="1eda3-114">Daha fazla bilgi için Bkz. [MDI Üst Formları Oluşturma.](how-to-create-mdi-parent-forms.md)</span><span class="sxs-lookup"><span data-stu-id="1eda3-114">For more information, see [Creating MDI Parent Forms](how-to-create-mdi-parent-forms.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1eda3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1eda3-115">See also</span></span>

- [<span data-ttu-id="1eda3-116">Çoklu Belge Arabirimi (MDI) Uygulamaları</span><span class="sxs-lookup"><span data-stu-id="1eda3-116">Multiple-Document Interface (MDI) Applications</span></span>](multiple-document-interface-mdi-applications.md)
- [<span data-ttu-id="1eda3-117">Nasıl yapılır: MDI Üst Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1eda3-117">How to: Create MDI Parent Forms</span></span>](how-to-create-mdi-parent-forms.md)
- [<span data-ttu-id="1eda3-118">Nasıl yapılır: MDI Alt Formları Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1eda3-118">How to: Create MDI Child Forms</span></span>](how-to-create-mdi-child-forms.md)
- [<span data-ttu-id="1eda3-119">Nasıl yapılır: Etkin MDI Alt Öğesine Veri Gönderme</span><span class="sxs-lookup"><span data-stu-id="1eda3-119">How to: Send Data to the Active MDI Child</span></span>](how-to-send-data-to-the-active-mdi-child.md)
- [<span data-ttu-id="1eda3-120">Nasıl yapılır: MDI Alt Formlarını Düzenleme</span><span class="sxs-lookup"><span data-stu-id="1eda3-120">How to: Arrange MDI Child Forms</span></span>](how-to-arrange-mdi-child-forms.md)
