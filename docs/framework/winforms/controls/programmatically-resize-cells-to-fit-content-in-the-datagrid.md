---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetiminde İçeriği Sığdıracak Şekilde Hücreleri Programlı Olarak Yeniden Boyutlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells to fit content
- cells [Windows Forms], resizing to fit contents
- DataGridView control [Windows Forms], resizing cells
- grids [Windows Forms], resizing cells to fit content
ms.assetid: 63d770dc-b3f5-462b-901a-3125b2753792
ms.openlocfilehash: 3686656cc113245514bdb3237bdb24c4c665409f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538148"
---
# <a name="how-to-programmatically-resize-cells-to-fit-content-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="17bd5-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde İçeriği Sığdıracak Şekilde Hücreleri Programlı Olarak Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="17bd5-102">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="17bd5-103">Kullanabileceğiniz <xref:System.Windows.Forms.DataGridView> kontrol böylece kesmeden tüm değerleri görüntüler satırlar, sütunlar ve üstbilgileri yeniden boyutlandırmak için yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="17bd5-103">You can use the <xref:System.Windows.Forms.DataGridView> control methods to resize rows, columns, and headers so that they display their entire values without truncation.</span></span> <span data-ttu-id="17bd5-104">Bu yöntemler yeniden boyutlandırmak için kullanabileceğiniz <xref:System.Windows.Forms.DataGridView> seçtiğiniz öğeleri bazen.</span><span class="sxs-lookup"><span data-stu-id="17bd5-104">You can use these methods to resize <xref:System.Windows.Forms.DataGridView> elements at times of your choosing.</span></span> <span data-ttu-id="17bd5-105">Alternatif olarak, içerik her değiştiğinde bu öğeler otomatik olarak yeniden boyutlandırmak için denetimi yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17bd5-105">Alternately, you can configure the control to resize these elements automatically whenever content changes.</span></span> <span data-ttu-id="17bd5-106">Ancak, büyük veri kümeleri veya verilerinizi sıklıkla değiştiği ile çalışırken Bu Verimsiz, olabilir.</span><span class="sxs-lookup"><span data-stu-id="17bd5-106">This can be inefficient, however, when you are working with large data sets or when your data changes frequently.</span></span> <span data-ttu-id="17bd5-107">Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki boyutlandırma seçenekleri](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="17bd5-107">For more information, see [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="17bd5-108">Genellikle, program aracılığıyla ayarlar <xref:System.Windows.Forms.DataGridView> yalnızca yeni verileri veri kaynağından veya kullanıcı bir değer düzenlendiğinde yüklediğinizde, içeriğin sığması için öğeleri.</span><span class="sxs-lookup"><span data-stu-id="17bd5-108">Typically, you will programmatically adjust <xref:System.Windows.Forms.DataGridView> elements to fit their content only when you load new data from a data source or when the user has edited a value.</span></span> <span data-ttu-id="17bd5-109">Bu performansı iyileştirmek kullanışlıdır ancak satırları ve sütunları fareyle el ile yeniden boyutlandırın sağlamak istediğinizde de kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="17bd5-109">This is useful to optimize performance, but it is also useful when you want to enable your users to manually resize rows and columns with the mouse.</span></span>  
  
 <span data-ttu-id="17bd5-110">Aşağıdaki kod örneğinde programlı olarak yeniden boyutlandırma için kullanılabilir seçenekler gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="17bd5-110">The following code example demonstrates the options available to you for programmatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17bd5-111">Örnek</span><span class="sxs-lookup"><span data-stu-id="17bd5-111">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CPP/programmaticsizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/CS/programmaticsizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.ProgrammaticResizing#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.ProgrammaticResizing/VB/programmaticsizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="17bd5-112">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="17bd5-112">Compiling the Code</span></span>  
 <span data-ttu-id="17bd5-113">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="17bd5-113">This example requires:</span></span>  
  
-   <span data-ttu-id="17bd5-114">Sistem, System.Drawing ve System.Windows.Forms derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="17bd5-114">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="17bd5-115">Visual Basic veya Visual C# için bu örnek komut satırından oluşturma hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [komut satırı derleme ile csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="17bd5-115">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="17bd5-116">Bu örnek Visual Studio'da yeni bir projeye kod yapıştırılarak de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17bd5-116">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="17bd5-117">Ayrıca bkz. [nasıl yapılır: derleme ve çalıştırma bir tam Windows Forms kod örneği kullanarak Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="17bd5-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17bd5-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17bd5-118">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>  
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>  
 <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>  
 <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>  
 [<span data-ttu-id="17bd5-119">Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="17bd5-119">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="17bd5-120">Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="17bd5-120">Sizing Options in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="17bd5-121">Nasıl yapılır: Windows Forms DataGridView Denetiminde İçerik Değiştiğinde Hücreleri Otomatik Olarak Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="17bd5-121">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/automatically-resize-cells-when-content-changes-in-the-datagrid.md)
