---
title: "Nasıl yapılır: Windows Forms'da Çok Sayfalı Metin Dosyası Yazdırma"
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
ms.openlocfilehash: bd858279a4d8a3509a91bcd1c62fb1f61d6d2bb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931784"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="5dc7e-102">Nasıl yapılır: Windows Forms'da Çok Sayfalı Metin Dosyası Yazdırma</span><span class="sxs-lookup"><span data-stu-id="5dc7e-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="5dc7e-103">Windows tabanlı uygulamaların metin yazdırması çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="5dc7e-104"><xref:System.Drawing.Graphics> Sınıfı, ekran veya yazıcı gibi bir cihaza nesneleri (grafik veya metin) çizmek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5dc7e-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Yöntemleri<xref:System.Windows.Forms.TextRenderer> yazdırma için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="5dc7e-106">Yazdırma amaçlarıyla metin çizmek için <xref:System.Drawing.Graphics.DrawString%2A> , aşağıdaki <xref:System.Drawing.Graphics>kod örneğinde gösterildiği gibi her zaman yöntemini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="5dc7e-107">Metin yazdırmak için</span><span class="sxs-lookup"><span data-stu-id="5dc7e-107">To print text</span></span>  
  
1. <span data-ttu-id="5dc7e-108">Formunuza bir <xref:System.Drawing.Printing.PrintDocument> bileşen ve dize ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2. <span data-ttu-id="5dc7e-109">Bir belge yazdırıyorsanız, <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> özelliği yazdırmak istediğiniz belgeye ayarlayın ve belge içeriğini açın ve daha önce eklediğiniz dizeye belge içeriğini okuyun.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3. <span data-ttu-id="5dc7e-110">Olay işleyicisinde, satır uzunluğunu ve sayfa <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> başına satırları hesaplamak <xref:System.Drawing.Printing.PrintPageEventArgs> için sınıfının özelliğini ve belge içeriğini kullanın. <xref:System.Drawing.Printing.PrintDocument.PrintPage></span><span class="sxs-lookup"><span data-stu-id="5dc7e-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="5dc7e-111">Her sayfa çizildikten sonra, son sayfa olup olmadığını denetleyin ve <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliğini <xref:System.Drawing.Printing.PrintPageEventArgs> uygun şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="5dc7e-112">Olay, olana kadar <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A>tetiklenir. `false` <xref:System.Drawing.Printing.PrintDocument.PrintPage></span><span class="sxs-lookup"><span data-stu-id="5dc7e-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="5dc7e-113">Ayrıca, <xref:System.Drawing.Printing.PrintDocument.PrintPage> olayın olay işleme yöntemiyle ilişkili olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="5dc7e-114">Aşağıdaki kod örneğinde, olay işleyicisi "testPage. txt" dosyasının içeriğini formda kullanılan yazı tipiyle yazdırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4. <span data-ttu-id="5dc7e-115">Olayı yükseltmek için <xref:System.Drawing.Printing.PrintDocument.Print%2A>yönteminiçağırın <xref:System.Drawing.Printing.PrintDocument.PrintPage> .</span><span class="sxs-lookup"><span data-stu-id="5dc7e-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="5dc7e-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="5dc7e-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5dc7e-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5dc7e-117">Compiling the Code</span></span>  
 <span data-ttu-id="5dc7e-118">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5dc7e-118">This example requires:</span></span>  
  
- <span data-ttu-id="5dc7e-119">C:\\sürücüsünün kökünde bulunan, yazdırılacak metni içeren TestPage. txt adlı bir metin dosyası.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="5dc7e-120">Farklı bir dosyayı yazdırmak için kodu düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-120">Edit the code to print a different file.</span></span>  
  
- <span data-ttu-id="5dc7e-121">System, System. Windows. Forms, System. Drawing derlemelerine başvuru.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
- <span data-ttu-id="5dc7e-122">Bu örneği Visual Basic veya görsel C#için komut satırından oluşturma hakkında daha fazla bilgi için, bkz. [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [CSC. exe ile komut satırı oluşturma](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5dc7e-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5dc7e-123">Ayrıca, kodu yeni bir projeye yapıştırarak bu örneği Visual Studio 'da da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dc7e-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dc7e-124">See also</span></span>

- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="5dc7e-125">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="5dc7e-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
