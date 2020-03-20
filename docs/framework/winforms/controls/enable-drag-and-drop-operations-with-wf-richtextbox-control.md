---
title: RichTextBox Denetimi ile Sürükle ve Bırak Işlemlerini Etkinleştir
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- examples [Windows Forms], text boxes
- drag and drop [Windows Forms], richTextBox control
- text boxes [Windows Forms], drag-and-drop operations
- RichTextBox control [Windows Forms], drag-and-drop operations
ms.assetid: ca167d1c-2014-4cf0-96a0-20598470be3b
ms.openlocfilehash: 27e5c18598552c465ef17f5e58069bc10e401c09
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182345"
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="f965b-102">Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Sürükleyip Bırakma İşlemlerini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f965b-102">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="f965b-103">Windows Forms <xref:System.Windows.Forms.RichTextBox> denetimi ile sürükle ve bırak işlemleri <xref:System.Windows.Forms.RichTextBox.DragEnter> <xref:System.Windows.Forms.RichTextBox.DragDrop> ve olayları işleyerek yapılır.</span><span class="sxs-lookup"><span data-stu-id="f965b-103">Drag-and-drop operations with the Windows Forms <xref:System.Windows.Forms.RichTextBox> control are done by handling the <xref:System.Windows.Forms.RichTextBox.DragEnter> and <xref:System.Windows.Forms.RichTextBox.DragDrop> events.</span></span> <span data-ttu-id="f965b-104">Bu nedenle, sürükle ve bırak işlemleri <xref:System.Windows.Forms.RichTextBox> denetim ile son derece basittir.</span><span class="sxs-lookup"><span data-stu-id="f965b-104">Thus, drag-and-drop operations are extremely simple with the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a><span data-ttu-id="f965b-105">RichTextBox denetiminde sürükleme işlemlerini etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="f965b-105">To enable drag operations in a RichTextBox control</span></span>  
  
1. <span data-ttu-id="f965b-106">Denetimin <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> özelliğini <xref:System.Windows.Forms.RichTextBox> `true`' ye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="f965b-106">Set the <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> property of the <xref:System.Windows.Forms.RichTextBox> control to `true`.</span></span>  
  
2. <span data-ttu-id="f965b-107"><xref:System.Windows.Forms.RichTextBox.DragEnter> Olayın olay işleyicisi kodu yazın.</span><span class="sxs-lookup"><span data-stu-id="f965b-107">Write code in the event handler of the <xref:System.Windows.Forms.RichTextBox.DragEnter> event.</span></span> <span data-ttu-id="f965b-108">Sürüklenen `if` verilerin kabul edilebilir bir türde olduğundan emin olmak için bir deyim kullanın (bu durumda, metin).</span><span class="sxs-lookup"><span data-stu-id="f965b-108">Use an `if` statement to ensure that the data being dragged is of an acceptable type (in this case, text).</span></span> <span data-ttu-id="f965b-109">Özellik <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> numaralandırmanın <xref:System.Windows.Forms.DragDropEffects> herhangi bir değerine ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f965b-109">The <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> property can be set to any value of the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragEnter(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragEnter  
       If (e.Data.GetDataPresent(DataFormats.Text)) Then  
          e.Effect = DragDropEffects.Copy  
       Else  
          e.Effect = DragDropEffects.None  
       End If  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragEnter(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       if (e.Data.GetDataPresent(DataFormats.Text))
          e.Effect = DragDropEffects.Copy;  
       else  
          e.Effect = DragDropEffects.None;  
    }  
    ```  
  
    ```cpp  
    private:  
       void richTextBox1_DragEnter(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          if (e->Data->GetDataPresent(DataFormats::Text))  
             e->Effect = DragDropEffects::Copy;  
          else  
             e->Effect = DragDropEffects::None;  
       }  
    ```  
  
     <span data-ttu-id="f965b-110">(Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="f965b-110">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragEnter += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragEnter);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragEnter += gcnew  
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragEnter);  
    ```  
  
3. <span data-ttu-id="f965b-111"><xref:System.Windows.Forms.RichTextBox.DragDrop> Olayı işlemek için kod yazın.</span><span class="sxs-lookup"><span data-stu-id="f965b-111">Write code to handle the <xref:System.Windows.Forms.RichTextBox.DragDrop> event.</span></span> <span data-ttu-id="f965b-112">Sürüklenen <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> verileri almak için yöntemi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f965b-112">Use the <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> method to retrieve the data being dragged.</span></span>  
  
     <span data-ttu-id="f965b-113">Aşağıdaki örnekte, kod, <xref:System.Windows.Forms.RichTextBox.Text%2A> denetimin <xref:System.Windows.Forms.RichTextBox> özelliğini sürüklenen verilere eşit olarak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f965b-113">In the example below, the code sets the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control equal to the data being dragged.</span></span> <span data-ttu-id="f965b-114"><xref:System.Windows.Forms.RichTextBox> Denetimde zaten metin varsa, sürüklenen metin ekleme noktasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="f965b-114">If there is already text in the <xref:System.Windows.Forms.RichTextBox> control, the dragged text is inserted at the insertion point.</span></span>  
  
    ```vb  
    Private Sub RichTextBox1_DragDrop(ByVal sender As Object, _
       ByVal e As System.Windows.Forms.DragEventArgs) _
       Handles RichTextBox1.DragDrop  
       Dim i As Int16
       Dim s As String  
  
       ' Get start position to drop the text.  
       i = RichTextBox1.SelectionStart  
       s = RichTextBox1.Text.Substring(i)  
       RichTextBox1.Text = RichTextBox1.Text.Substring(0, i)  
  
       ' Drop the text on to the RichTextBox.  
       RichTextBox1.Text = RichTextBox1.Text + _  
          e.Data.GetData(DataFormats.Text).ToString()  
       RichTextBox1.Text = RichTextBox1.Text + s  
    End Sub  
    ```  
  
    ```csharp  
    private void richTextBox1_DragDrop(object sender,
    System.Windows.Forms.DragEventArgs e)  
    {  
       int i;  
       String s;  
  
       // Get start position to drop the text.  
       i = richTextBox1.SelectionStart;  
       s = richTextBox1.Text.Substring(i);  
       richTextBox1.Text = richTextBox1.Text.Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       richTextBox1.Text = richTextBox1.Text +
          e.Data.GetData(DataFormats.Text).ToString();  
       richTextBox1.Text = richTextBox1.Text + s;  
    }  
    ```  
  
    ```cpp  
    private:  
       System::Void richTextBox1_DragDrop(System::Object ^  sender,  
          System::Windows::Forms::DragEventArgs ^  e)  
       {  
          int i;  
          String ^s;  
  
       // Get start position to drop the text.  
       i = richTextBox1->SelectionStart;  
       s = richTextBox1->Text->Substring(i);  
       richTextBox1->Text = richTextBox1->Text->Substring(0,i);  
  
       // Drop the text on to the RichTextBox.  
       String ^str = String::Concat(richTextBox1->Text, e->Data  
       ->GetData(DataFormats->Text)->ToString());
       richTextBox1->Text = String::Concat(str, s);  
       }  
    ```  
  
     <span data-ttu-id="f965b-115">(Görsel C# ve Görsel C++) Olay işleyicisini kaydetmek için aşağıdaki kodu formun oluşturucusuna yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="f965b-115">(Visual C# and Visual C++) Place the following code in the form's constructor to register the event handler.</span></span>  
  
    ```csharp  
    this.richTextBox1.DragDrop += new  
        System.Windows.Forms.DragEventHandler  
        (this.richTextBox1_DragDrop);  
    ```  
  
    ```cpp  
    this->richTextBox1->DragDrop += gcnew
       System::Windows::Forms::DragEventHandler  
       (this, &Form1::richTextBox1_DragDrop);  
    ```  
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a><span data-ttu-id="f965b-116">Uygulamanızdaki sürükle ve bırak işlevini test etmek için</span><span class="sxs-lookup"><span data-stu-id="f965b-116">To test the drag-and-drop functionality in your application</span></span>  
  
1. <span data-ttu-id="f965b-117">Uygulamanızı kaydedin ve oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f965b-117">Save and build your application.</span></span> <span data-ttu-id="f965b-118">Çalışırken WordPad'i çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f965b-118">While it is running, run WordPad.</span></span>  
  
     <span data-ttu-id="f965b-119">WordPad, Windows tarafından yüklenen ve sürükle ve bırak işlemlerine izin veren bir metin düzenleyicisidir.</span><span class="sxs-lookup"><span data-stu-id="f965b-119">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="f965b-120">**Başlat** düğmesine tıklayarak, **Çalıştır'ı**seçerek `WordPad` , **Çalıştır** iletişim kutusunun metin kutusuna yazarak ve sonra **Tamam'ı**tıklatarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="f965b-120">It is accessible by clicking the **Start** button, selecting **Run**, typing `WordPad` in the text box of the **Run** dialog box, and then clicking **OK**.</span></span>  
  
2. <span data-ttu-id="f965b-121">WordPad açıldıktan sonra, içinde bir metin dizisi yazın.</span><span class="sxs-lookup"><span data-stu-id="f965b-121">Once WordPad is open, type a string of text in it.</span></span> <span data-ttu-id="f965b-122">Fareyi kullanarak metni seçin ve ardından seçili metni <xref:System.Windows.Forms.RichTextBox> Windows uygulamanızdaki denetime sürükleyin.</span><span class="sxs-lookup"><span data-stu-id="f965b-122">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.RichTextBox> control in your Windows application.</span></span>  
  
     <span data-ttu-id="f965b-123">Fareyi <xref:System.Windows.Forms.RichTextBox> denetime doğrulttuğa (ve dolayısıyla olayı <xref:System.Windows.Forms.RichTextBox.DragEnter> yükselttiğinde), fare işaretçisinin değiştiğine ve <xref:System.Windows.Forms.RichTextBox> seçili metni denetime bırakabileceğinize dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="f965b-123">Notice that when you point the mouse at the <xref:System.Windows.Forms.RichTextBox> control (and, consequently, raise the <xref:System.Windows.Forms.RichTextBox.DragEnter> event), the mouse pointer changes and you can drop the selected text into the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
     <span data-ttu-id="f965b-124">Fare düğmesini serbest bıraktığınızda, seçili metin bırakılır <xref:System.Windows.Forms.RichTextBox.DragDrop> (diğer bir deyişle, olay yükseltilir) ve denetim in <xref:System.Windows.Forms.RichTextBox> içine eklenir.</span><span class="sxs-lookup"><span data-stu-id="f965b-124">When you release the mouse button, the selected text is dropped (that is, the <xref:System.Windows.Forms.RichTextBox.DragDrop> event is raised) and is inserted within the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f965b-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f965b-125">See also</span></span>

- <xref:System.Windows.Forms.RichTextBox>
- [<span data-ttu-id="f965b-126">Nasıl yapılır: Uygulamalar Arasında Sürükle ve Bırak İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="f965b-126">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../advanced/how-to-perform-drag-and-drop-operations-between-applications.md)
- [<span data-ttu-id="f965b-127">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="f965b-127">RichTextBox Control</span></span>](richtextbox-control-windows-forms.md)
- [<span data-ttu-id="f965b-128">Windows Forms'ta Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="f965b-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
