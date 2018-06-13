---
title: "Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma"
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
ms.openlocfilehash: 6d6701e5e4b9a0b0fbb677b49f3791075976745a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523009"
---
# <a name="how-to-print-a-multi-page-text-file-in-windows-forms"></a><span data-ttu-id="fe0c5-102">Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma</span><span class="sxs-lookup"><span data-stu-id="fe0c5-102">How to: Print a Multi-Page Text File in Windows Forms</span></span>
<span data-ttu-id="fe0c5-103">Metin yazdırmak çalışan Windows tabanlı uygulamalar için çok yaygındır.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-103">It is very common for Windows-based applications to print text.</span></span> <span data-ttu-id="fe0c5-104"><xref:System.Drawing.Graphics> Sınıfı bir ekran veya yazıcı gibi bir cihaza çizim nesneleri (grafik veya metin) için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-104">The <xref:System.Drawing.Graphics> class provides methods for drawing objects (graphics or text) to a device, such as a screen or printer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe0c5-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Yöntemlerinin <xref:System.Windows.Forms.TextRenderer> yazdırmak için desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of <xref:System.Windows.Forms.TextRenderer> are not supported for printing.</span></span> <span data-ttu-id="fe0c5-106">Her zaman kullanmalısınız <xref:System.Drawing.Graphics.DrawString%2A> yöntemlerinin <xref:System.Drawing.Graphics>metin yazdırma amacıyla çizmek için aşağıdaki kod örneğinde gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-106">You should always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of <xref:System.Drawing.Graphics>, as shown in the following code example, to draw text for printing purposes.</span></span>  
  
### <a name="to-print-text"></a><span data-ttu-id="fe0c5-107">Metin yazdırma</span><span class="sxs-lookup"><span data-stu-id="fe0c5-107">To print text</span></span>  
  
1.  <span data-ttu-id="fe0c5-108">Ekleme bir <xref:System.Drawing.Printing.PrintDocument> bileşeni ve formunuza bir dize.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-108">Add a <xref:System.Drawing.Printing.PrintDocument> component and a string to your form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#8)]
     [!code-vb[System.Drawing.Printing.PrintExamples#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#8)]  
  
2.  <span data-ttu-id="fe0c5-109">Bir belge yazdırma ayarlamak <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> belge özelliğine istediğiniz yazdırma ve açın ve daha önce eklediğiniz dizeye belge içeriklerini okuma.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-109">If printing a document, set the <xref:System.Drawing.Printing.PrintDocument.DocumentName%2A> property to the document you wish to print, and open and read the documents contents to the string you added previously.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#1)]
     [!code-vb[System.Drawing.Printing.PrintExamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#1)]  
  
3.  <span data-ttu-id="fe0c5-110">İçinde <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay işleyicisi, kullanım <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> sınıfı ve hesaplamak için belge içeriklerini satır uzunluğu ve sayfa başına satır.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-110">In the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event handler, use the <xref:System.Drawing.Printing.PrintPageEventArgs.Graphics%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> class and the document contents to calculate line length and lines per page.</span></span> <span data-ttu-id="fe0c5-111">Her bir sayfa çizilir sonra son sayfa olup olmadığını denetleyin ve ayarlayın <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> özelliği <xref:System.Drawing.Printing.PrintPageEventArgs> uygun şekilde.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-111">After each page is drawn, check to see if it is the last page, and set the <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> property of the <xref:System.Drawing.Printing.PrintPageEventArgs> accordingly.</span></span> <span data-ttu-id="fe0c5-112"><xref:System.Drawing.Printing.PrintDocument.PrintPage> Olayı kadar <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> olan `false`.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-112">The <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is raised until <xref:System.Drawing.Printing.PrintPageEventArgs.HasMorePages%2A> is `false`.</span></span> <span data-ttu-id="fe0c5-113">Ayrıca, emin olun <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay, kendi olay işleme yöntemi ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-113">Also, make sure the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event is associated with its event-handling method.</span></span>  
  
     <span data-ttu-id="fe0c5-114">Aşağıdaki kod örneğinde, olay işleyicisi form üzerinde kullanılan aynı yazı tipi "testPage.txt" dosyasının içeriği yazdırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-114">In the following code example, the event handler is used to print the contents of the "testPage.txt" file in the same font as is used on the form.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#2)]
     [!code-vb[System.Drawing.Printing.PrintExamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="fe0c5-115">Çağrı <xref:System.Drawing.Printing.PrintDocument.Print%2A> yükseltmek için yöntemi <xref:System.Drawing.Printing.PrintDocument.PrintPage> olay.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-115">Call the <xref:System.Drawing.Printing.PrintDocument.Print%2A> method to raise the <xref:System.Drawing.Printing.PrintDocument.PrintPage> event.</span></span>  
  
     [!code-csharp[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#5)]
     [!code-vb[System.Drawing.Printing.PrintExamples#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="fe0c5-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="fe0c5-116">Example</span></span>  
 [!code-csharp[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/CS/Form1.cs#0)]
 [!code-vb[System.Drawing.Printing.PrintExamples#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Printing.PrintExamples/VB/Form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fe0c5-117">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="fe0c5-117">Compiling the Code</span></span>  
 <span data-ttu-id="fe0c5-118">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="fe0c5-118">This example requires:</span></span>  
  
-   <span data-ttu-id="fe0c5-119">Yazdırmak için metni içeren testPage.txt adlı bir metin dosyası C: sürücüsünün kök dizininde bulunan\\.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-119">A text file named testPage.txt containing the text to print, located in the root of drive C:\\.</span></span> <span data-ttu-id="fe0c5-120">Farklı bir dosya yazdırmak için kodu girin.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-120">Edit the code to print a different file.</span></span>  
  
-   <span data-ttu-id="fe0c5-121">Sistem, System.Windows.Forms, System.Drawing derlemeleri başvurular.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-121">References to the System, System.Windows.Forms, System.Drawing assemblies.</span></span>  
  
-   <span data-ttu-id="fe0c5-122">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="fe0c5-122">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="fe0c5-123">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-123">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="fe0c5-124">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="fe0c5-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe0c5-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fe0c5-125">See Also</span></span>  
 <xref:System.Drawing.Graphics>  
 <xref:System.Drawing.Brush>  
 [<span data-ttu-id="fe0c5-126">Windows Forms Yazdırma Desteği</span><span class="sxs-lookup"><span data-stu-id="fe0c5-126">Windows Forms Print Support</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
