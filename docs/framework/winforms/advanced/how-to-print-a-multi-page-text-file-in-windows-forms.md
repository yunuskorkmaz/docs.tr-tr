---
title: "Nasıl yapılır: Windows Forms'ta çok sayfalı metin dosyası yazdırma"
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
ms.openlocfilehash: f2f91fbaab7fb999a2243e13be9af0bbff0e41ac
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714144"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="ae645-102">Nasıl yapılır: Windows Forms'ta çok sayfalı metin dosyası yazdırma</span><span class="sxs-lookup"><span data-stu-id="ae645-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="ae645-103">Metin yazdırma Windows tabanlı uygulamalar için çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="ae645-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="ae645-104"><xref:System.Drawing.Graphics> Sınıfı bir aygıta bir ekran veya yazıcı gibi çizim nesneleri (grafik veya metin) için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="ae645-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae645-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Yöntemlerinin <xref:System.Windows.Forms.TextRenderer> yazdırma için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="ae645-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="ae645-106">Her zaman kullanmalısınız <xref:System.Drawing.Graphics.DrawString%2A> yöntemlerinin <xref:System.Drawing.Graphics>metin yazdırma amacıyla çizmek için aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="ae645-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="ae645-107">Metin yazdırma</span><span class="sxs-lookup"><span data-stu-id="ae645-107">To print text</span></span>  
  
1.  <span data-ttu-id="ae645-108">Ekleme bir <xref:System.Drawing.Printing.PrintDocument> bileşeni ve formunuza bir dize.</span><span class="sxs-lookup"><span data-stu-id="ae645-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2.  <span data-ttu-id="ae645-109">Belge yazdırma verilirse <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> belge özelliğini istediğiniz yazdırma, açın ve daha önce eklediğiniz dizeye belge içeriklerini okuma.</span><span class="sxs-lookup"><span data-stu-id="ae645-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3.  <span data-ttu-id="ae645-110">İçinde <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisi, kullanım <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfı ve belge içeriğini hesaplamak için satır uzunluğu ve sayfa başına satır.</span><span class="sxs-lookup"><span data-stu-id="ae645-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="ae645-111">Her sayfanın çekildikten sonra son sayfa olup olmadığını denetleyin ve ayarlama <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="ae645-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="ae645-112"><xref:System.Drawing.Printing.PrintDocument.PrintPage> Kadar olayı yükseltildiğinde <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> olduğu `false`.</span><span class="sxs-lookup"><span data-stu-id="ae645-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="ae645-113">Ayrıca, emin <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay, olay işleme yöntemi ile ilişkili.</span><span class="sxs-lookup"><span data-stu-id="ae645-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="ae645-114">Aşağıdaki kod örneğinde, olay işleyicisi, form üzerinde kullanılan aynı yazı tipi "testPage.txt" dosyasının içeriği yazdırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ae645-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="ae645-115">Çağrı <xref:System.Drawing.Printing.PrintDocument.Print%2A> yükseltmek için yöntemi <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay.</span><span class="sxs-lookup"><span data-stu-id="ae645-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="ae645-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="ae645-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae645-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="ae645-117">Compiling the Code</span></span>  
 <span data-ttu-id="ae645-118">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ae645-118">This example requires:</span></span>  
  
-   <span data-ttu-id="ae645-119">Yazdırmak için metni içeren testPage.txt adlı bir metin dosyası C: sürücüsünün kök dizininde bulunan\\.</span><span class="sxs-lookup"><span data-stu-id="ae645-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="ae645-120">Farklı bir dosya yazdırma için kodu düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="ae645-120">Edit the code to print a different file.</span></span>  
  
-   <span data-ttu-id="ae645-121">Sistem, System.Windows.Forms, System.Drawing derlemelere başvurular.</span><span class="sxs-lookup"><span data-stu-id="ae645-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
-   <span data-ttu-id="ae645-122">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ae645-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ae645-123">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ae645-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae645-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ae645-124">See also</span></span>
- <xref:System.Drawing.Graphics>
- <xref:System.Drawing.Brush>
- [<span data-ttu-id="ae645-125">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="ae645-125">Windows Forms Print Support</span></span>](windows-forms-print-support.md)
