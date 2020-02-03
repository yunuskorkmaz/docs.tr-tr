---
title: TextBox denetiminde metin Seç
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
ms.openlocfilehash: 8a32e40f14ddae6f8ddcaa6d62337329df6fde26
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745309"
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="f2c65-102">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="f2c65-102">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="f2c65-103">Windows Forms <xref:System.Windows.Forms.TextBox> denetiminde metin programlama yoluyla seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2c65-103">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="f2c65-104">Örneğin, belirli bir dize için metin arayan bir işlev oluşturursanız, bulunan dizenin konumunun okuyucuyu görsel olarak uyarmak için metni seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2c65-104">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="f2c65-105">Metni programlı olarak seçmek için</span><span class="sxs-lookup"><span data-stu-id="f2c65-105">To select text programmatically</span></span>  
  
1. <span data-ttu-id="f2c65-106"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliğini seçmek istediğiniz metnin başlangıcına ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f2c65-106">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="f2c65-107"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliği, ekleme noktasını metin dizesi içinde gösteren ve 0 ' ın en sol konumu olacak şekilde belirten bir sayıdır.</span><span class="sxs-lookup"><span data-stu-id="f2c65-107">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="f2c65-108"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliği, metin kutusundaki karakter sayısına eşit veya daha büyük bir değere ayarlandıysa, ekleme noktası son karakterden sonra yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="f2c65-108">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2. <span data-ttu-id="f2c65-109"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliğini seçmek istediğiniz metnin uzunluğuna ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f2c65-109">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="f2c65-110"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliği, ekleme noktasının genişliğini ayarlayan sayısal bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="f2c65-110">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="f2c65-111"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> 0 ' dan büyük bir sayıya ayarlamak, geçerli ekleme noktasından başlayarak bu sayıda karakteri seçilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="f2c65-111">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3. <span data-ttu-id="f2c65-112">Seçim Seçilen metne <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> özelliği aracılığıyla erişin.</span><span class="sxs-lookup"><span data-stu-id="f2c65-112">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="f2c65-113">Aşağıdaki kod, denetimin <xref:System.Windows.Forms.Control.Enter> olayı gerçekleştiğinde bir metin kutusunun içeriğini seçer.</span><span class="sxs-lookup"><span data-stu-id="f2c65-113">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="f2c65-114">Bu örnek, metin kutusunun `null` veya boş bir dize olmayan <xref:System.Windows.Forms.TextBox.Text%2A> özelliği için bir değere sahip olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="f2c65-114">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="f2c65-115">Metin kutusu odağı aldığında, metin kutusundaki geçerli metin seçilidir.</span><span class="sxs-lookup"><span data-stu-id="f2c65-115">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="f2c65-116">`TextBox1_Enter` olay işleyicisi denetime bağlanmalıdır; daha fazla bilgi için bkz. [nasıl yapılır: çalışma zamanında olay Işleyicileri oluşturma Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="f2c65-116">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="f2c65-117">Bu örneği test etmek için, metin kutusu odaklanana kadar SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="f2c65-117">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="f2c65-118">Metin kutusuna tıkladığınızda metin seçili değildir.</span><span class="sxs-lookup"><span data-stu-id="f2c65-118">If you click in the text box, the text is unselected.</span></span>  
  
    ```vb  
    Private Sub TextBox1_Enter(ByVal sender As Object, ByVal e As System.EventArgs) Handles TextBox1.Enter  
       If (Not String.IsNullOrEmpty(TextBox1.Text)) Then  
          TextBox1.SelectionStart = 0  
          TextBox1.SelectionLength = TextBox1.Text.Length  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void textBox1_Enter(object sender, System.EventArgs e){  
       if (!String.IsNullOrEmpty(textBox1.Text))  
       {  
          textBox1.SelectionStart = 0;  
          textBox1.SelectionLength = textBox1.Text.Length;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void textBox1_Enter(System::Object ^ sender,  
          System::EventArgs ^ e) {  
       if (!System::String::IsNullOrEmpty(textBox1->Text))  
       {  
          textBox1->SelectionStart = 0;  
          textBox1->SelectionLength = textBox1->Text->Length;  
       }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="f2c65-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2c65-119">See also</span></span>

- <xref:System.Windows.Forms.TextBox>
- [<span data-ttu-id="f2c65-120">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f2c65-120">TextBox Control Overview</span></span>](textbox-control-overview-windows-forms.md)
- [<span data-ttu-id="f2c65-121">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="f2c65-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)
- [<span data-ttu-id="f2c65-122">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2c65-122">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="f2c65-123">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f2c65-123">How to: Create a Read-Only Text Box</span></span>](how-to-create-a-read-only-text-box-windows-forms.md)
- [<span data-ttu-id="f2c65-124">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="f2c65-124">How to: Put Quotation Marks in a String</span></span>](how-to-put-quotation-marks-in-a-string-windows-forms.md)
- [<span data-ttu-id="f2c65-125">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f2c65-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)
- [<span data-ttu-id="f2c65-126">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="f2c65-126">TextBox Control</span></span>](textbox-control-windows-forms.md)
