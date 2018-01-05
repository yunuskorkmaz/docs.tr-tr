---
title: "Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme"
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
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c8de64ac28fe57e3c448c671859053fad4aae3b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="0d45a-102">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="0d45a-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="0d45a-103">Windows Forms zaman <xref:System.Windows.Forms.TextBox> denetim odağı ilk alır, varolan herhangi bir metni sola metin kutusu içinde varsayılan ekleme.</span><span class="sxs-lookup"><span data-stu-id="0d45a-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="0d45a-104">Kullanıcı klavye veya fare ekleme noktasını taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d45a-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="0d45a-105">Metin kutusu kaybeder ve odak yeniden kazanabilmesi ekleme noktasını yerlerde kullanıcı son onu yerleştirilen olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0d45a-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="0d45a-106">Bazı durumlarda, bu davranış kullanıcıya disconcerting olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d45a-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="0d45a-107">Word uygulaması işleme, kullanıcı sonra varolan herhangi bir metni görünmesi yeni karakterler bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d45a-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="0d45a-108">Bir veri girişi uygulamasında kullanıcı varolan bir girişi değiştirmek için yeni karakterler bekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0d45a-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="0d45a-109"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Ve <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özellikleri amacınıza uygun olarak davranışını değiştirmek etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="0d45a-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="0d45a-110">TextBox denetiminde ekleme noktasını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="0d45a-110">To control the insertion point in a TextBox control</span></span>  
  
1.  <span data-ttu-id="0d45a-111">Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> uygun bir değere özelliği.</span><span class="sxs-lookup"><span data-stu-id="0d45a-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="0d45a-112">Ekleme noktasını ilk karakterin hemen soluna sıfır yerleştirir.</span><span class="sxs-lookup"><span data-stu-id="0d45a-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2.  <span data-ttu-id="0d45a-113">(İsteğe bağlı) Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliğini seçmek istediğiniz metnin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="0d45a-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="0d45a-114">Aşağıdaki kod ekleme noktasını her zaman 0 olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d45a-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="0d45a-115">`TextBox1_Enter` Olay işleyicisi bağlı denetimi; daha fazla bilgi için bkz: [Windows Forms'ta olay işleyicileri oluşturma](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0d45a-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../../../../docs/framework/winforms/creating-event-handlers-in-windows-forms.md).</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       TextBox1.SelectionStart = 0  
       TextBox1.SelectionLength = 0  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(Object sender, System.EventArgs e) {  
       textBox1.SelectionStart = 0;  
       textBox1.SelectionLength = 0;  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^  sender,  
          System::EventArgs ^  e)  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = 0;  
       }  
    ```  
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="0d45a-116">Ekleme noktasını varsayılan olarak görünür hale getirme</span><span class="sxs-lookup"><span data-stu-id="0d45a-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="0d45a-117"><xref:System.Windows.Forms.TextBox> Ekleme noktasını, varsayılan olarak yeni bir form yalnızca IF görülebilir <xref:System.Windows.Forms.TextBox> denetimidir sekme sırasındaki ilk.</span><span class="sxs-lookup"><span data-stu-id="0d45a-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="0d45a-118">Ekleme noktasını yalnızca size Aksi takdirde görünür <xref:System.Windows.Forms.TextBox> klavye veya fare odaktaki.</span><span class="sxs-lookup"><span data-stu-id="0d45a-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="0d45a-119">Metin kutusu noktasını yeni bir form üzerinde varsayılan olarak görünür yapmak için</span><span class="sxs-lookup"><span data-stu-id="0d45a-119">To make the text box insertion point visible by default on a new form</span></span>  
  
-   <span data-ttu-id="0d45a-120">Ayarlama <xref:System.Windows.Forms.TextBox> denetimin <xref:System.Windows.Forms.Control.TabIndex%2A> özelliğine `0`.</span><span class="sxs-lookup"><span data-stu-id="0d45a-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d45a-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d45a-121">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="0d45a-122">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="0d45a-122">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="0d45a-123">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d45a-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="0d45a-124">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d45a-124">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="0d45a-125">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="0d45a-125">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="0d45a-126">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="0d45a-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-select-text-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="0d45a-127">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0d45a-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="0d45a-128">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="0d45a-128">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
