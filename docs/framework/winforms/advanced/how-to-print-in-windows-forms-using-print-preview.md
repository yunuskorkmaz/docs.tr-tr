---
title: "Nasıl yapılır: Windows Forms'ta Baskı Önizlemeyi Kullanarak Yazdırma"
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
helpviewer_keywords:
- printing [Windows Forms], using print preview
- printing [Windows Forms], with print preview
- print preview
ms.assetid: 4a16f7e2-ae10-4485-b0ae-3d558334d0fe
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9da52f338c7cbe62f265279440422e380be3cbfd
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-print-in-windows-forms-using-print-preview"></a><span data-ttu-id="dedf6-102">Nasıl yapılır: Windows Forms'ta Baskı Önizlemeyi Kullanarak Yazdırma</span><span class="sxs-lookup"><span data-stu-id="dedf6-102">How to: Print in Windows Forms Using Print Preview</span></span>
<span data-ttu-id="dedf6-103">Windows Forms'ta baskı önizlemeyi yazdırma hizmetlerine ek olarak sunmak için programlama çok yaygın bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="dedf6-103">It is very common in Windows Forms programming to offer print preview in addition to printing services.</span></span> <span data-ttu-id="dedf6-104">Baskı Önizleme Hizmetleri uygulamanıza eklemek için kolay bir yol kullanmaktır bir <xref:System.Windows.Forms.PrintPreviewDialog> denetimi ile birlikte <xref:System.Drawing.Printing.PrintDocument.PrintPage> bir dosya yazdırma için olay işleme mantığı.</span><span class="sxs-lookup"><span data-stu-id="dedf6-104">An easy way to add print preview services to your application is to use a <xref:System.Windows.Forms.PrintPreviewDialog> control in combination with the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event-handling logic for printing a file.</span></span>  
  
### <a name="to-preview-a-text-document-with-a-printpreviewdialog-control"></a><span data-ttu-id="dedf6-105">PrintPreviewDialog denetimi ile bir metin belgesini önizlemek için</span><span class="sxs-lookup"><span data-stu-id="dedf6-105">To preview a text document with a PrintPreviewDialog control</span></span>  
  
1.  <span data-ttu-id="dedf6-106">Ekleme bir <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>ve formunuza iki dizeleri.</span><span class="sxs-lookup"><span data-stu-id="dedf6-106">Add a <xref:System.Windows.Forms.PrintPreviewDialog>, <xref:System.Drawing.Printing.PrintDocument>, and two strings to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#1)]  
  
2.  <span data-ttu-id="dedf6-107">Ayarlama <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> belge özelliğine istediğiniz yazdırma ve açın ve daha önce eklediğiniz dizeye belge içeriklerini okuma.</span><span class="sxs-lookup"><span data-stu-id="dedf6-107">Set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the document's contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="dedf6-108">İçinde belge yazdırma gibi <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisi, kullanım <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfı ve sayfa başına satır hesaplamak ve belgenin içeriğini işlemek için dosya içerikleri.</span><span class="sxs-lookup"><span data-stu-id="dedf6-108">As you would for printing the document, in the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the file contents to calculate lines per page and render the document's contents.</span></span> <span data-ttu-id="dedf6-109">Her bir sayfa çizilir sonra son sayfa olup olmadığını denetleyin ve ayarlayın <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="dedf6-109">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="dedf6-110"><xref:System.Drawing.Printing.PrintDocument.PrintPage> Olayı kadar <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> olan `false`.</span><span class="sxs-lookup"><span data-stu-id="dedf6-110">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="dedf6-111">Belge işlemeyi tamamladığında, işlenmek üzere dize sıfırlayın.</span><span class="sxs-lookup"><span data-stu-id="dedf6-111">When the document has finished rendering, reset the string to be rendered.</span></span> <span data-ttu-id="dedf6-112">Ayrıca, emin olun <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay, kendi olay işleme yöntemi ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="dedf6-112">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dedf6-113">Uygulamanızda yazdırma uyguladıysanız, zaten olarak adım 2 ve 3 tamamlanmamış olabilir.</span><span class="sxs-lookup"><span data-stu-id="dedf6-113">You may have already completed steps 2 and 3 if you have implemented printing in your application.</span></span>  
  
     <span data-ttu-id="dedf6-114">Aşağıdaki kod örneğinde, olay işleyicisi form üzerinde kullanılan aynı yazı tipi "testPage.txt" dosyasında yazdırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dedf6-114">In the following code example, the event handler is used to print the "testPage.txt" file in the same font used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#3)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#3)]  
  
4.  <span data-ttu-id="dedf6-115">Ayarlama <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> özelliği <xref:System.Windows.Forms.PrintPreviewDialog> denetimini <xref:System.Drawing.Printing.PrintDocument> formdaki bileşen.</span><span class="sxs-lookup"><span data-stu-id="dedf6-115">Set the <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A> property of the <xref:System.Windows.Forms.PrintPreviewDialog> control to the <xref:System.Drawing.Printing.PrintDocument> component on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#5)]  
  
5.  <span data-ttu-id="dedf6-116">Çağrı <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> yöntemi <xref:System.Windows.Forms.PrintPreviewDialog> denetim.</span><span class="sxs-lookup"><span data-stu-id="dedf6-116">Call the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method on the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="dedf6-117">Genellikle çağırırdı <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> gelen <xref:System.Windows.Forms.Control.Click> düğmesinin olay işleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dedf6-117">You would typically call <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> from the <xref:System.Windows.Forms.Control.Click> event-handling method of a button.</span></span> <span data-ttu-id="dedf6-118">Çağırma <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> başlatır <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay ve çıktıyı işler <xref:System.Windows.Forms.PrintPreviewDialog> denetim.</span><span class="sxs-lookup"><span data-stu-id="dedf6-118">Calling <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> raises the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event and renders the output to the <xref:System.Windows.Forms.PrintPreviewDialog> control.</span></span> <span data-ttu-id="dedf6-119">Kullanıcı iletişim kutusundaki yazdırma simgesine tıkladığında <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı yeniden Önizleme iletişim kutusu yerine yazıcıya çıktı gönderen.</span><span class="sxs-lookup"><span data-stu-id="dedf6-119">When the user clicks the print icon on the dialog, the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised again, sending the output to the printer instead of the preview dialog.</span></span> <span data-ttu-id="dedf6-120">Adım 3'te oluşturma işleminin sonunda dizesini sıfırlamak nedeni budur.</span><span class="sxs-lookup"><span data-stu-id="dedf6-120">This is why the string is reset at the end of the rendering process in step 3.</span></span>  
  
     <span data-ttu-id="dedf6-121">Aşağıdaki örnekte gösterildiği kod <xref:System.Windows.Forms.Control.Click> formda bir düğmesi için olay işleme yöntemi.</span><span class="sxs-lookup"><span data-stu-id="dedf6-121">The following code example shows the <xref:System.Windows.Forms.Control.Click> event-handling method for a button on the form.</span></span> <span data-ttu-id="dedf6-122">Bu olay işleme yöntemi belgeyi okumak ve Baskı Önizleme iletişim kutusu göstermek için yöntemleri çağırır.</span><span class="sxs-lookup"><span data-stu-id="dedf6-122">This event-handling method calls the methods to read the document and show the print preview dialog.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#4)]
     [!code-vb[System.Drawing.Printing.PrintPreviewExample#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#4)]  
  
## <a name="example"></a><span data-ttu-id="dedf6-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="dedf6-123">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintPreviewExample#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintPreviewExample/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dedf6-124">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="dedf6-124">Compiling the Code</span></span>  
 <span data-ttu-id="dedf6-125">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="dedf6-125">This example requires:</span></span>  
  
-   <span data-ttu-id="dedf6-126">Sistem, System.Windows.Forms, System.Drawing derlemeleri başvurular.</span><span class="sxs-lookup"><span data-stu-id="dedf6-126">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
-   <span data-ttu-id="dedf6-127">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="dedf6-127">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="dedf6-128">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dedf6-128">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="dedf6-129">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="dedf6-129">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dedf6-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dedf6-130">See Also</span></span>  
 [<span data-ttu-id="dedf6-131">Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma</span><span class="sxs-lookup"><span data-stu-id="dedf6-131">How to: Print a Multi-Page Text File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 [<span data-ttu-id="dedf6-132">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="dedf6-132">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [<span data-ttu-id="dedf6-133">Windows Forms'ta Daha Güvenli Yazdırma</span><span class="sxs-lookup"><span data-stu-id="dedf6-133">More Secure Printing in Windows Forms</span></span>](../../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)
