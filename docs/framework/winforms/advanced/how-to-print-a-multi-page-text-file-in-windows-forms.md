---
title: 'Nasıl yapılır: çok sayfalı metin dosyası yazdırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- printing [Windows Forms], printing multiple pages
- text [Windows Forms], printing Windows Forms
- Windows Forms, printing text
- printing [Windows Forms], text
ms.assetid: 362427f8-03d4-4826-b49f-60ab066ad322
ms.openlocfilehash: 51e30706bb7693988d611701d013792c82dccd0b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740652"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="b2bf7-102">Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma</span><span class="sxs-lookup"><span data-stu-id="b2bf7-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="b2bf7-103">Windows tabanlı uygulamaların metin yazdırması çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="b2bf7-104"><xref:System.Drawing.Graphics> sınıfı, ekran veya yazıcı gibi bir cihaza nesneleri (grafik veya metin) çizmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2bf7-105"><xref:System.Windows.Forms.TextRenderer> <xref:System.Windows.Forms.TextRenderer.DrawText%2A> yöntemleri yazdırma için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="b2bf7-106">Yazdırma amaçlarıyla metin çizmek için, aşağıdaki kod örneğinde gösterildiği gibi <xref:System.Drawing.Graphics><xref:System.Drawing.Graphics.DrawString%2A> yöntemlerini her zaman kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="b2bf7-107">Metin yazdırmak için</span><span class="sxs-lookup"><span data-stu-id="b2bf7-107">To print text</span></span>  
  
1. <span data-ttu-id="b2bf7-108">Formunuza bir <xref:System.Drawing.Printing.PrintDocument> bileşeni ve dize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. <span data-ttu-id="b2bf7-109">Belge yazdırıyorsanız, <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> özelliğini yazdırmak istediğiniz belge olarak ayarlayın ve belgeler içeriğini açın ve daha önce eklediğiniz dizeye belge içeriğini okuyun.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <span data-ttu-id="b2bf7-110"><xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisinde, satır uzunluğunu ve sayfa başına satırları hesaplamak için <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfının <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliğini ve belge içeriğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="b2bf7-111">Her sayfa çizildikten sonra, son sayfa olup olmadığını denetleyin ve <xref:System.Drawing.Printing.PrintPageEventArgs> <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliğini uygun şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="b2bf7-112"><xref:System.Drawing.Printing.PrintDocument.PrintPage> olayı, <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> `false`kadar tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="b2bf7-113">Ayrıca, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayının olay işleme yöntemiyle ilişkili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="b2bf7-114">Aşağıdaki kod örneğinde, olay işleyicisi "testPage. txt" dosyasının içeriğini formda kullanılan yazı tipiyle yazdırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="b2bf7-115"><xref:System.Drawing.Printing.PrintDocument.PrintPage> olayını yükseltmek için <xref:System.Drawing.Printing.PrintDocument.Print%2A> yöntemi çağırın.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="b2bf7-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="b2bf7-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b2bf7-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b2bf7-117">Compiling the Code</span></span>  
 <span data-ttu-id="b2bf7-118">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b2bf7-118">This example requires:</span></span>  
  
- <span data-ttu-id="b2bf7-119">C:\\sürücüsünün kökünde bulunan, yazdırılacak metni içeren testPage. txt adlı bir metin dosyası.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="b2bf7-120">Farklı bir dosyayı yazdırmak için kodu düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-120">Edit the code to print a different file.</span></span>  
  
- <span data-ttu-id="b2bf7-121">System, System. Windows. Forms, System. Drawing derlemelerine başvuru.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
- <span data-ttu-id="b2bf7-122">Bu örneği Visual Basic veya görsel C#için komut satırından oluşturma hakkında daha fazla bilgi için, bkz. [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [CSC. exe ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b2bf7-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b2bf7-123">Ayrıca, kodu yeni bir projeye yapıştırarak bu örneği Visual Studio 'da da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2bf7-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2bf7-124">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="b2bf7-125">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="b2bf7-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
