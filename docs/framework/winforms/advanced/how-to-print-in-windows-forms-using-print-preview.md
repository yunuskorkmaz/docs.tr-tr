---
title: "Nasıl yapılır: Windows Forms'da Baskı Önizlemeyi Kullanarak Yazdırma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: 07137d03dd9a20d8eab564757618e48e25b45353
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931763"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="eaf8d-102">Nasıl yapılır: Windows Forms'da Baskı Önizlemeyi Kullanarak Yazdırma</span><span class="sxs-lookup"><span data-stu-id="eaf8d-102">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="eaf8d-103">Yazdırma hizmetlerinin yanı sıra baskı önizleme sunmak için Windows Forms programlamada çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-103">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="eaf8d-104">Uygulamanıza baskı önizleme hizmetleri eklemenin kolay bir yolu, bir dosyayı yazdırmak için <xref:System.Windows.Forms.PrintPreviewDialog> <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleme mantığı ile birlikte bir denetim kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-104">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="eaf8d-105">Bir metin belgesini PrintPreview Iletişim kutusu denetimiyle önizlemek için</span><span class="sxs-lookup"><span data-stu-id="eaf8d-105">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1. <span data-ttu-id="eaf8d-106">Formunuza bir <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>ve iki dize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-106">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <span data-ttu-id="eaf8d-107">Yazdırmak istediğiniz belgeye özelliği ayarlayın ve belgenin içeriğini açın ve daha önce eklediğiniz dizeye okuyun. <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A></span><span class="sxs-lookup"><span data-stu-id="eaf8d-107">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="eaf8d-108">Belgeyi yazdırırken yaptığınız gibi, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisinde, sayfa başına satırları hesaplamak ve belgenin içeriğini işlemek için, <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfının <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliğini ve dosya içeriğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-108">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="eaf8d-109">Her sayfa çizildikten sonra, son sayfa olup olmadığını denetleyin ve <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliğini <xref:System.Drawing.Printing.PrintPageEventArgs> uygun şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-109">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="eaf8d-110">Olay, olana kadar <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A>tetiklenir. `false` <xref:System.Drawing.Printing.PrintDocument.PrintPage></span><span class="sxs-lookup"><span data-stu-id="eaf8d-110">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="eaf8d-111">Belgenin işlenmesi bittiğinde, işlenecek dizeyi sıfırlayın.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-111">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="eaf8d-112">Ayrıca, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayın olay işleme yöntemiyle ilişkili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-112">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="eaf8d-113">Uygulamanızda yazdırma uyguladıysanız adım 2 ve 3 ' ü zaten tamamlamış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-113">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="eaf8d-114">Aşağıdaki kod örneğinde, olay işleyicisi, formda kullanılan yazı tipinde "testPage. txt" dosyasını yazdırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-114">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="eaf8d-115"><xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> Denetimin<xref:System.Drawing.Printing.PrintDocument> özelliğini formdaki bileşeneayarlayın<xref:System.Windows.Forms.PrintPreviewDialog> .</span><span class="sxs-lookup"><span data-stu-id="eaf8d-115">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <span data-ttu-id="eaf8d-116"><xref:System.Windows.Forms.PrintPreviewDialog> Denetimindeki <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-116">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="eaf8d-117">Genellikle bir düğmenin <xref:System.Windows.Forms.Control.Click> olay <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> işleme yönteminden çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-117">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="eaf8d-118">Çağırma <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> olayı<xref:System.Drawing.Printing.PrintDocument.PrintPage> başlatır ve çıktıyı <xref:System.Windows.Forms.PrintPreviewDialog> denetime işler.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-118">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="eaf8d-119">Kullanıcı iletişim kutusundaki yazdır simgesine tıkladığında, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay yeniden oluşturulur ve Önizleme iletişim kutusu yerine çıktıyı yazıcıya gönderir.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-119">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="eaf8d-120">Bu nedenle, 3. adımdaki işleme sürecinin sonunda dize sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-120">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="eaf8d-121">Aşağıdaki kod örneğinde, form üzerindeki <xref:System.Windows.Forms.Control.Click> bir düğme için olay işleme yöntemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-121">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="eaf8d-122">Bu olay işleme yöntemi, belgeyi okumak ve Baskı Önizleme iletişim kutusunu göstermek için yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-122">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="eaf8d-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="eaf8d-123">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eaf8d-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="eaf8d-124">Compiling the Code</span></span>  
 <span data-ttu-id="eaf8d-125">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="eaf8d-125">This example requires:</span></span>  
  
- <span data-ttu-id="eaf8d-126">System, System. Windows. Forms, System. Drawing derlemelerine başvuru.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-126">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eaf8d-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eaf8d-127">See also</span></span>

- [<span data-ttu-id="eaf8d-128">Nasıl yapılır: Windows Forms bir çok sayfalı metin dosyası yazdırma</span><span class="sxs-lookup"><span data-stu-id="eaf8d-128">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="eaf8d-129">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="eaf8d-129">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
- [<span data-ttu-id="eaf8d-130">Windows Forms'ta Daha Güvenli Yazdırma</span><span class="sxs-lookup"><span data-stu-id="eaf8d-130">More Secure Printing in Windows Forms</span></span>](../more-secure-printing-in-windows-forms.md)
