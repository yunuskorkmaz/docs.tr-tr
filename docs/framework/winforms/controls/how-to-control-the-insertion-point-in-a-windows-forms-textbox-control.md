---
title: TextBox denetimindeki ekleme noktasını denetleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], insertion point
- insertion points [Windows Forms], TextBox controls
- text boxes [Windows Forms], controlling insertion point
ms.assetid: 5bee7d34-5121-429e-ab1f-d8ff67bc74c1
ms.openlocfilehash: fd4803820921f0c922a4ce885f809abee8fd4c6c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742211"
---
# <a name="how-to-control-the-insertion-point-in-a-windows-forms-textbox-control"></a><span data-ttu-id="e2f84-102">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="e2f84-102">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>
<span data-ttu-id="e2f84-103">Bir Windows Forms <xref:System.Windows.Forms.TextBox> denetimi ilk olarak odağı aldığında, metin kutusundaki varsayılan ekleme varolan metnin solunda yer alır.</span><span class="sxs-lookup"><span data-stu-id="e2f84-103">When a Windows Forms <xref:System.Windows.Forms.TextBox> control first receives the focus, the default insertion within the text box is to the left of any existing text.</span></span> <span data-ttu-id="e2f84-104">Kullanıcı ekleme noktasını klavye veya fare ile taşıyabilir.</span><span class="sxs-lookup"><span data-stu-id="e2f84-104">The user can move the insertion point with the keyboard or the mouse.</span></span> <span data-ttu-id="e2f84-105">Metin kutusu kaybediyor ve sonra odağı kaybederse, ekleme noktası kullanıcının en son yerleştirmiş olduğu her yerde olur.</span><span class="sxs-lookup"><span data-stu-id="e2f84-105">If the text box loses and then regains the focus, the insertion point will be wherever the user last placed it.</span></span>  
  
 <span data-ttu-id="e2f84-106">Bazı durumlarda, bu davranış kullanıcıya disconcerting olabilir.</span><span class="sxs-lookup"><span data-stu-id="e2f84-106">In some cases, this behavior can be disconcerting to the user.</span></span> <span data-ttu-id="e2f84-107">Bir sözcük işleme uygulamasında, Kullanıcı yeni karakterlerin mevcut metinden sonra görünmesini bekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e2f84-107">In a word processing application, the user might expect new characters to appear after any existing text.</span></span> <span data-ttu-id="e2f84-108">Bir veri girişi uygulamasında, Kullanıcı var olan herhangi bir girdinin yerine yeni karakterlerin değiştirilmesini bekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="e2f84-108">In a data entry application, the user might expect new characters to replace any existing entry.</span></span> <span data-ttu-id="e2f84-109"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> ve <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özellikleri, davranışını amacınıza uyacak şekilde değiştirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e2f84-109">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> and <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> properties enable you to modify the behavior to suit your purpose.</span></span>  
  
### <a name="to-control-the-insertion-point-in-a-textbox-control"></a><span data-ttu-id="e2f84-110">TextBox denetiminde ekleme noktasını denetlemek için</span><span class="sxs-lookup"><span data-stu-id="e2f84-110">To control the insertion point in a TextBox control</span></span>  
  
1. <span data-ttu-id="e2f84-111"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliğini uygun bir değer olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e2f84-111">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to an appropriate value.</span></span> <span data-ttu-id="e2f84-112">Sıfır, ekleme noktasını ilk karakterin soluna hemen koyar.</span><span class="sxs-lookup"><span data-stu-id="e2f84-112">Zero places the insertion point immediately to the left of the first character.</span></span>  
  
2. <span data-ttu-id="e2f84-113">Seçim <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliğini seçmek istediğiniz metnin uzunluğuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e2f84-113">(Optional) Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="e2f84-114">Aşağıdaki kod her zaman ekleme noktasını 0 olarak döndürür.</span><span class="sxs-lookup"><span data-stu-id="e2f84-114">The code below always returns the insertion point to 0.</span></span> <span data-ttu-id="e2f84-115">`TextBox1_Enter` olay işleyicisi denetime bağlanmalıdır; daha fazla bilgi için bkz. [Windows Forms olay Işleyicileri oluşturma](../creating-event-handlers-in-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="e2f84-115">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [Creating Event Handlers in Windows Forms](../creating-event-handlers-in-windows-forms.md).</span></span>  
  
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
  
## <a name="making-the-insertion-point-visible-by-default"></a><span data-ttu-id="e2f84-116">Ekleme noktasının varsayılan olarak görünmesini sağlama</span><span class="sxs-lookup"><span data-stu-id="e2f84-116">Making the Insertion Point Visible by Default</span></span>  
 <span data-ttu-id="e2f84-117"><xref:System.Windows.Forms.TextBox> ekleme noktası, varsayılan olarak yeni bir formda görünür ve yalnızca <xref:System.Windows.Forms.TextBox> denetimi sekme sıraucundadır.</span><span class="sxs-lookup"><span data-stu-id="e2f84-117">The <xref:System.Windows.Forms.TextBox> insertion point is visible by default in a new form only if the <xref:System.Windows.Forms.TextBox> control is first in the tab order.</span></span> <span data-ttu-id="e2f84-118">Aksi halde, ekleme noktası yalnızca <xref:System.Windows.Forms.TextBox> klavye veya fare ile odağı verirseniz görünür.</span><span class="sxs-lookup"><span data-stu-id="e2f84-118">Otherwise, the insertion point appears only if you give the <xref:System.Windows.Forms.TextBox> the focus with either the keyboard or the mouse.</span></span>  
  
#### <a name="to-make-the-text-box-insertion-point-visible-by-default-on-a-new-form"></a><span data-ttu-id="e2f84-119">Metin kutusu ekleme noktasını yeni bir formda varsayılan olarak görünür hale getirmek için</span><span class="sxs-lookup"><span data-stu-id="e2f84-119">To make the text box insertion point visible by default on a new form</span></span>  
  
- <span data-ttu-id="e2f84-120"><xref:System.Windows.Forms.TextBox> denetiminin <xref:System.Windows.Forms.Control.TabIndex%2A> özelliğini `0`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e2f84-120">Set the <xref:System.Windows.Forms.TextBox> control's <xref:System.Windows.Forms.Control.TabIndex%2A> property to `0`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f84-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2f84-121">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="e2f84-122">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e2f84-122">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="e2f84-123">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e2f84-123">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="e2f84-124">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e2f84-124">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="e2f84-125">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="e2f84-125">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="e2f84-126">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="e2f84-126">How to: Select Text in the Windows Forms TextBox Control</span></span>](how-to-select-text-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="e2f84-127">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e2f84-127">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="e2f84-128">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="e2f84-128">TextBox Control</span></span>](textbox-control-windows-forms.md)
