---
title: 'Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Sürükleyip Bırakma İşlemlerini Etkinleştirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17bf3b8e50c4e51cb14225e402903428a309d67a
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-enable-drag-and-drop-operations-with-the-windows-forms-richtextbox-control"></a><span data-ttu-id="d8091-102">Nasıl yapılır: Windows Forms RichTextBox Denetimi ile Sürükleyip Bırakma İşlemlerini Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="d8091-102">How to: Enable Drag-and-Drop Operations with the Windows Forms RichTextBox Control</span></span>
<span data-ttu-id="d8091-103">Windows Forms ile sürükle ve bırak işlemleri <xref:System.Windows.Forms.RichTextBox> denetim işleyerek yapılır <xref:System.Windows.Forms.RichTextBox.DragEnter> ve <xref:System.Windows.Forms.RichTextBox.DragDrop> olaylar.</span><span class="sxs-lookup"><span data-stu-id="d8091-103">Drag-and-drop operations with the Windows Forms <xref:System.Windows.Forms.RichTextBox> control are done by handling the <xref:System.Windows.Forms.RichTextBox.DragEnter> and <xref:System.Windows.Forms.RichTextBox.DragDrop> events.</span></span> <span data-ttu-id="d8091-104">Bu nedenle, sürükle ve bırak işlemleri ile son derece basit <xref:System.Windows.Forms.RichTextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="d8091-104">Thus, drag-and-drop operations are extremely simple with the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
### <a name="to-enable-drag-operations-in-a-richtextbox-control"></a><span data-ttu-id="d8091-105">RichTextBox denetiminde sürükleme işlemleri etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="d8091-105">To enable drag operations in a RichTextBox control</span></span>  
  
1.  <span data-ttu-id="d8091-106">Ayarlama <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> özelliği <xref:System.Windows.Forms.RichTextBox> denetimini `true`.</span><span class="sxs-lookup"><span data-stu-id="d8091-106">Set the <xref:System.Windows.Forms.RichTextBox.AllowDrop%2A> property of the <xref:System.Windows.Forms.RichTextBox> control to `true`.</span></span>  
  
2.  <span data-ttu-id="d8091-107">Olay işleyicisi kod yazma <xref:System.Windows.Forms.RichTextBox.DragEnter> olay.</span><span class="sxs-lookup"><span data-stu-id="d8091-107">Write code in the event handler of the <xref:System.Windows.Forms.RichTextBox.DragEnter> event.</span></span> <span data-ttu-id="d8091-108">Kullanım bir `if` deyimi sürüklenen verileri (Bu durumda, metin) kabul edilebilir bir türde olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="d8091-108">Use an `if` statement to ensure that the data being dragged is of an acceptable type (in this case, text).</span></span> <span data-ttu-id="d8091-109"><xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> Özelliği herhangi bir değere ayarlanabilir <xref:System.Windows.Forms.DragDropEffects> numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="d8091-109">The <xref:System.Windows.Forms.DragEventArgs.Effect%2A?displayProperty=nameWithType> property can be set to any value of the <xref:System.Windows.Forms.DragDropEffects> enumeration.</span></span>  
  
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
  
     <span data-ttu-id="d8091-110">(Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d8091-110">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
3.  <span data-ttu-id="d8091-111">İşlemek için kod yazma <xref:System.Windows.Forms.RichTextBox.DragDrop> olay.</span><span class="sxs-lookup"><span data-stu-id="d8091-111">Write code to handle the <xref:System.Windows.Forms.RichTextBox.DragDrop> event.</span></span> <span data-ttu-id="d8091-112">Kullanım <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> sürüklenen veri alma yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d8091-112">Use the <xref:System.Windows.Forms.DataObject.GetData%2A?displayProperty=nameWithType> method to retrieve the data being dragged.</span></span>  
  
     <span data-ttu-id="d8091-113">Aşağıdaki kod örneğinde ayarlar <xref:System.Windows.Forms.RichTextBox.Text%2A> özelliği <xref:System.Windows.Forms.RichTextBox> sürüklenen veri eşit denetim.</span><span class="sxs-lookup"><span data-stu-id="d8091-113">In the example below, the code sets the <xref:System.Windows.Forms.RichTextBox.Text%2A> property of the <xref:System.Windows.Forms.RichTextBox> control equal to the data being dragged.</span></span> <span data-ttu-id="d8091-114">Zaten varsa metinde <xref:System.Windows.Forms.RichTextBox> denetim, sürüklenen metin ekleme noktasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="d8091-114">If there is already text in the <xref:System.Windows.Forms.RichTextBox> control, the dragged text is inserted at the insertion point.</span></span>  
  
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
  
     <span data-ttu-id="d8091-115">(Visual C# ve [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) formun oluşturucuda olay işleyicisi kaydetmek için aşağıdaki kodu yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="d8091-115">(Visual C# and [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) Place the following code in the form's constructor to register the event handler.</span></span>  
  
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
  
### <a name="to-test-the-drag-and-drop-functionality-in-your-application"></a><span data-ttu-id="d8091-116">Uygulamanızda sürükle ve bırak işlevselliğini sınamak için</span><span class="sxs-lookup"><span data-stu-id="d8091-116">To test the drag-and-drop functionality in your application</span></span>  
  
1.  <span data-ttu-id="d8091-117">Kaydedin ve uygulamanızı oluşturun.</span><span class="sxs-lookup"><span data-stu-id="d8091-117">Save and build your application.</span></span> <span data-ttu-id="d8091-118">Çalışırken, WordPad çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d8091-118">While it is running, run WordPad.</span></span>  
  
     <span data-ttu-id="d8091-119">WordPad sürükle ve bırak işlemleri sağlayan Windows tarafından yüklenen bir metin Düzenleyicisi ' dir.</span><span class="sxs-lookup"><span data-stu-id="d8091-119">WordPad is a text editor installed by Windows that allows drag-and-drop operations.</span></span> <span data-ttu-id="d8091-120">Erişilebilir durumda tıklayarak **Başlat** düğmesi, seçme **çalıştırmak**yazarak `WordPad` metin kutusunda **çalıştırmak** iletişim kutusunu ve ardından  **Tamam**.</span><span class="sxs-lookup"><span data-stu-id="d8091-120">It is accessible by clicking the **Start** button, selecting **Run**, typing `WordPad` in the text box of the **Run** dialog box, and then clicking **OK**.</span></span>  
  
2.  <span data-ttu-id="d8091-121">WordPad açıldıktan sonra bir metin dizesinin içinde yazın.</span><span class="sxs-lookup"><span data-stu-id="d8091-121">Once WordPad is open, type a string of text in it.</span></span> <span data-ttu-id="d8091-122">Fare kullanarak, metni seçin ve ardından seçili metnin üzerine sürükleyin <xref:System.Windows.Forms.RichTextBox> Windows uygulamanız denetiminde.</span><span class="sxs-lookup"><span data-stu-id="d8091-122">Using the mouse, select the text, and then drag the selected text over to the <xref:System.Windows.Forms.RichTextBox> control in your Windows application.</span></span>  
  
     <span data-ttu-id="d8091-123">Fareyi üzerine geldiğinizde dikkat <xref:System.Windows.Forms.RichTextBox> denetimi (ve sonuç olarak, Yükselt <xref:System.Windows.Forms.RichTextBox.DragEnter> olay), fare işaretçisini değişir ve seçili metne düşürebilir <xref:System.Windows.Forms.RichTextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="d8091-123">Notice that when you point the mouse at the <xref:System.Windows.Forms.RichTextBox> control (and, consequently, raise the <xref:System.Windows.Forms.RichTextBox.DragEnter> event), the mouse pointer changes and you can drop the selected text into the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
     <span data-ttu-id="d8091-124">Seçili metni fare düğmesini bıraktığınızda, bırakılan (diğer bir deyişle, <xref:System.Windows.Forms.RichTextBox.DragDrop> olayı) ve içinde eklenen <xref:System.Windows.Forms.RichTextBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="d8091-124">When you release the mouse button, the selected text is dropped (that is, the <xref:System.Windows.Forms.RichTextBox.DragDrop> event is raised) and is inserted within the <xref:System.Windows.Forms.RichTextBox> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8091-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8091-125">See Also</span></span>  
 <xref:System.Windows.Forms.RichTextBox>  
 [<span data-ttu-id="d8091-126">Nasıl yapılır: Uygulamalar Arasında Sürükle ve Bırak İşlemleri Gerçekleştirme</span><span class="sxs-lookup"><span data-stu-id="d8091-126">How to: Perform Drag-and-Drop Operations Between Applications</span></span>](../../../../docs/framework/winforms/advanced/how-to-perform-drag-and-drop-operations-between-applications.md)  
 [<span data-ttu-id="d8091-127">RichTextBox Denetimi</span><span class="sxs-lookup"><span data-stu-id="d8091-127">RichTextBox Control</span></span>](../../../../docs/framework/winforms/controls/richtextbox-control-windows-forms.md)  
 [<span data-ttu-id="d8091-128">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="d8091-128">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
