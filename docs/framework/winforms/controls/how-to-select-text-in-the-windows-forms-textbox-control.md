---
title: "Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme"
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
- TextBox control [Windows Forms], selecting text programmatically
- text boxes [Windows Forms], selecting text programmatically
- text [Windows Forms], selecting in text boxes programmatically
ms.assetid: 8c591546-6a01-45c7-8e03-f78431f903b1
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 535ee9e7359782f24d48d895f094afbe47e1023b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-select-text-in-the-windows-forms-textbox-control"></a><span data-ttu-id="01ca6-102">Nasıl yapılır: Windows Forms TextBox Denetiminde Metni Seçme</span><span class="sxs-lookup"><span data-stu-id="01ca6-102">How to: Select Text in the Windows Forms TextBox Control</span></span>
<span data-ttu-id="01ca6-103">Windows Forms'ta program aracılığıyla metin seçebilirsiniz <xref:System.Windows.Forms.TextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="01ca6-103">You can select text programmatically in the Windows Forms <xref:System.Windows.Forms.TextBox> control.</span></span> <span data-ttu-id="01ca6-104">Örneğin, belirli bir dizenin metni arar işlevi oluşturursanız, görsel olarak bulunan dizesinin konumu okuyucu uyarı metne seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="01ca6-104">For example, if you create a function that searches text for a particular string, you can select the text to visually alert the reader of the found string's position.</span></span>  
  
### <a name="to-select-text-programmatically"></a><span data-ttu-id="01ca6-105">Program aracılığıyla metni seçmek için</span><span class="sxs-lookup"><span data-stu-id="01ca6-105">To select text programmatically</span></span>  
  
1.  <span data-ttu-id="01ca6-106">Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> seçmek istediğiniz metnin başına özelliğine.</span><span class="sxs-lookup"><span data-stu-id="01ca6-106">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property to the beginning of the text you want to select.</span></span>  
  
     <span data-ttu-id="01ca6-107"><xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> Özellik metin dizesi içinde ekleme noktasını belirten bir sayı, 0 ile en solundaki konumu bırakılıyor.</span><span class="sxs-lookup"><span data-stu-id="01ca6-107">The <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is a number that indicates the insertion point within the string of text, with 0 being the left-most position.</span></span> <span data-ttu-id="01ca6-108">Varsa <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> özelliği ayarlanmış değerine eşit veya daha fazla karakter metin kutusuna, ekleme noktasını son karakter sonra yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="01ca6-108">If the <xref:System.Windows.Forms.TextBoxBase.SelectionStart%2A> property is set to a value equal to or greater than the number of characters in the text box, the insertion point is placed after the last character.</span></span>  
  
2.  <span data-ttu-id="01ca6-109">Ayarlama <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> özelliğini seçmek istediğiniz metnin uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="01ca6-109">Set the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property to the length of the text you want to select.</span></span>  
  
     <span data-ttu-id="01ca6-110"><xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> Ekleme noktasını genişliğini ayarlar sayısal bir değeri bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="01ca6-110">The <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> property is a numeric value that sets the width of the insertion point.</span></span> <span data-ttu-id="01ca6-111">Ayar <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> bu seçilecek karakter sayısı 0 neden olan daha büyük bir sayı geçerli ekleme noktasından başlatılıyor.</span><span class="sxs-lookup"><span data-stu-id="01ca6-111">Setting the <xref:System.Windows.Forms.TextBoxBase.SelectionLength%2A> to a number greater than 0 causes that number of characters to be selected, starting from the current insertion point.</span></span>  
  
3.  <span data-ttu-id="01ca6-112">(İsteğe bağlı) Seçili metni üzerinden erişim <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="01ca6-112">(Optional) Access the selected text through the <xref:System.Windows.Forms.TextBoxBase.SelectedText%2A> property.</span></span>  
  
     <span data-ttu-id="01ca6-113">Bir metin içeriğini seçer aşağıdaki kodu kutusunu denetimin <xref:System.Windows.Forms.Control.Enter> olayı oluşur.</span><span class="sxs-lookup"><span data-stu-id="01ca6-113">The code below selects the contents of a text box when the control's <xref:System.Windows.Forms.Control.Enter> event occurs.</span></span> <span data-ttu-id="01ca6-114">Bu örnek metin kutusu için bir değer olup olmadığını denetler <xref:System.Windows.Forms.TextBox.Text%2A> olmayan özellik `null` ya da boş bir dize.</span><span class="sxs-lookup"><span data-stu-id="01ca6-114">This example checks if the text box has a value for the <xref:System.Windows.Forms.TextBox.Text%2A> property that is not `null` or an empty string.</span></span> <span data-ttu-id="01ca6-115">Metin kutusu odağı aldığında, metin kutusuna geçerli metin seçilir.</span><span class="sxs-lookup"><span data-stu-id="01ca6-115">When the text box receives the focus, the current text in the text box is selected.</span></span> <span data-ttu-id="01ca6-116">`TextBox1_Enter` Olay işleyicisi bağlı denetimi; daha fazla bilgi için bkz: [nasıl yapılır: olay işleyicileri oluşturma çalıştırma süresi için Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="01ca6-116">The `TextBox1_Enter` event handler must be bound to the control; for more information, see [How to: Create Event Handlers at Run Time for Windows Forms](../../../../docs/framework/winforms/how-to-create-event-handlers-at-run-time-for-windows-forms.md).</span></span>  
  
     <span data-ttu-id="01ca6-117">Bu örnekte test etmek için metin kutusunun odaklanmış kadar SEKME tuşuna basın.</span><span class="sxs-lookup"><span data-stu-id="01ca6-117">To test this example, press the Tab key until the text box has the focus.</span></span> <span data-ttu-id="01ca6-118">Metin kutusuna tıklayın, metin seçilmemiş demektir.</span><span class="sxs-lookup"><span data-stu-id="01ca6-118">If you click in the text box, the text is unselected.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01ca6-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="01ca6-119">See Also</span></span>  
 <xref:System.Windows.Forms.TextBox>  
 [<span data-ttu-id="01ca6-120">TextBox Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="01ca6-120">TextBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/textbox-control-overview-windows-forms.md)  
 [<span data-ttu-id="01ca6-121">Nasıl yapılır: Windows Forms TextBox Denetiminde Ekleme Noktasını Belirleme</span><span class="sxs-lookup"><span data-stu-id="01ca6-121">How to: Control the Insertion Point in a Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-control-the-insertion-point-in-a-windows-forms-textbox-control.md)  
 [<span data-ttu-id="01ca6-122">Nasıl yapılır: Windows Forms TextBox Denetimi ile Parola Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="01ca6-122">How to: Create a Password Text Box with the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-password-text-box-with-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="01ca6-123">Nasıl yapılır: Salt Okunur Metin Kutusu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="01ca6-123">How to: Create a Read-Only Text Box</span></span>](../../../../docs/framework/winforms/controls/how-to-create-a-read-only-text-box-windows-forms.md)  
 [<span data-ttu-id="01ca6-124">Nasıl yapılır: Dizeye Tırnak İşaretleri Koyma</span><span class="sxs-lookup"><span data-stu-id="01ca6-124">How to: Put Quotation Marks in a String</span></span>](../../../../docs/framework/winforms/controls/how-to-put-quotation-marks-in-a-string-windows-forms.md)  
 [<span data-ttu-id="01ca6-125">Nasıl yapılır: Windows Forms TextBox Denetiminde Birden Fazla Çizgiyi Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="01ca6-125">How to: View Multiple Lines in the Windows Forms TextBox Control</span></span>](../../../../docs/framework/winforms/controls/how-to-view-multiple-lines-in-the-windows-forms-textbox-control.md)  
 [<span data-ttu-id="01ca6-126">TextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="01ca6-126">TextBox Control</span></span>](../../../../docs/framework/winforms/controls/textbox-control-windows-forms.md)
