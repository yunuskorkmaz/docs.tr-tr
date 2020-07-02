---
title: Baskı önizlemeyi kullanarak yazdırma
description: Windows Forms PrintPreview Iletişim kutusunu kullanarak uygulamanıza baskı önizleme hizmetleri eklemeyi öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
ms.openlocfilehash: abcf77db40f648df1a0cd49922bb49e5c9407811
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621619"
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="7ca73-103">Nasıl yapılır: Windows Forms'ta Baskı Önizlemeyi Kullanarak Yazdırma</span><span class="sxs-lookup"><span data-stu-id="7ca73-103">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="7ca73-104">Yazdırma hizmetlerinin yanı sıra baskı önizleme sunmak için Windows Forms programlamada çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="7ca73-104">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="7ca73-105">Uygulamanıza baskı önizleme hizmetleri eklemenin kolay bir yolu, <xref:System.Windows.Forms.PrintPreviewDialog> <xref:System.Drawing.Printing.PrintDocument.PrintPage> bir dosyayı yazdırmak için olay işleme mantığı ile birlikte bir denetim kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="7ca73-105">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="7ca73-106">Bir metin belgesini PrintPreview Iletişim kutusu denetimiyle önizlemek için</span><span class="sxs-lookup"><span data-stu-id="7ca73-106">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1. <span data-ttu-id="7ca73-107">Formunuza bir <xref:System.Windows.Forms.PrintPreviewDialog> , <xref:System.Drawing.Printing.PrintDocument> ve iki dize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7ca73-107">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2. <span data-ttu-id="7ca73-108"><xref:System.Drawing.Printing.PrintDocument.DocumentName%2A>Yazdırmak istediğiniz belgeye özelliği ayarlayın ve belgenin içeriğini açın ve daha önce eklediğiniz dizeye okuyun.</span><span class="sxs-lookup"><span data-stu-id="7ca73-108">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="7ca73-109">Belgeyi yazdırırken yaptığınız gibi, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisinde, <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> <xref:System.Drawing.Printing.PrintPageEventArgs> sayfa başına satırları hesaplamak ve belgenin içeriğini işlemek için, sınıfının özelliğini ve dosya içeriğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="7ca73-109">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="7ca73-110">Her sayfa çizildikten sonra, son sayfa olup olmadığını denetleyin ve <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliğini <xref:System.Drawing.Printing.PrintPageEventArgs> uygun şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ca73-110">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="7ca73-111"><xref:System.Drawing.Printing.PrintDocument.PrintPage>Olay, olana kadar tetiklenir <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> `false` .</span><span class="sxs-lookup"><span data-stu-id="7ca73-111">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="7ca73-112">Belgenin işlenmesi bittiğinde, işlenecek dizeyi sıfırlayın.</span><span class="sxs-lookup"><span data-stu-id="7ca73-112">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="7ca73-113">Ayrıca, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayın olay işleme yöntemiyle ilişkili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="7ca73-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="7ca73-114">Uygulamanızda yazdırma uyguladıysanız adım 2 ve 3 ' ü zaten tamamlamış olabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ca73-114">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="7ca73-115">Aşağıdaki kod örneğinde, olay işleyicisi, formda kullanılan yazı tipinde "testPage.txt" dosyasını yazdırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ca73-115">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4. <span data-ttu-id="7ca73-116"><xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> <xref:System.Windows.Forms.PrintPreviewDialog> Denetimin özelliğini <xref:System.Drawing.Printing.PrintDocument> formdaki bileşene ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ca73-116">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5. <span data-ttu-id="7ca73-117"><xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>Denetimindeki yöntemi çağırın <xref:System.Windows.Forms.PrintPreviewDialog> .</span><span class="sxs-lookup"><span data-stu-id="7ca73-117">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="7ca73-118">Genellikle <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> <xref:System.Windows.Forms.Control.Click> bir düğmenin olay işleme yönteminden çağrı yapılır.</span><span class="sxs-lookup"><span data-stu-id="7ca73-118">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="7ca73-119">Çağırma <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> olayı başlatır <xref:System.Drawing.Printing.PrintDocument.PrintPage> ve çıktıyı <xref:System.Windows.Forms.PrintPreviewDialog> denetime işler.</span><span class="sxs-lookup"><span data-stu-id="7ca73-119">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="7ca73-120">Kullanıcı iletişim kutusundaki yazdır simgesine tıkladığında, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay yeniden oluşturulur ve Önizleme iletişim kutusu yerine çıktıyı yazıcıya gönderir.</span><span class="sxs-lookup"><span data-stu-id="7ca73-120">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="7ca73-121">Bu nedenle, 3. adımdaki işleme sürecinin sonunda dize sıfırlanır.</span><span class="sxs-lookup"><span data-stu-id="7ca73-121">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="7ca73-122">Aşağıdaki kod örneğinde, <xref:System.Windows.Forms.Control.Click> form üzerindeki bir düğme için olay işleme yöntemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="7ca73-122">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="7ca73-123">Bu olay işleme yöntemi, belgeyi okumak ve Baskı Önizleme iletişim kutusunu göstermek için yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="7ca73-123">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="7ca73-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ca73-124">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7ca73-125">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="7ca73-125">Compiling the Code</span></span>  
 <span data-ttu-id="7ca73-126">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7ca73-126">This example requires:</span></span>  
  
- <span data-ttu-id="7ca73-127">System, System. Windows. Forms, System. Drawing derlemelerine başvuru.</span><span class="sxs-lookup"><span data-stu-id="7ca73-127">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ca73-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ca73-128">See also</span></span>

- [<span data-ttu-id="7ca73-129">Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma</span><span class="sxs-lookup"><span data-stu-id="7ca73-129">How to: Print a Multi-Page Text File in Windows Forms</span></span>](how-to-print-a-multi-page-text-file-in-windows-forms.md)
- [<span data-ttu-id="7ca73-130">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="7ca73-130">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
- [<span data-ttu-id="7ca73-131">Windows Forms'ta Daha Güvenli Yazdırma</span><span class="sxs-lookup"><span data-stu-id="7ca73-131">More Secure Printing in Windows Forms</span></span>](../more-secure-printing-in-windows-forms.md)
