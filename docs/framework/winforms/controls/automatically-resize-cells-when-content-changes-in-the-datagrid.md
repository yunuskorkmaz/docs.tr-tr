---
title: 'Nasıl yapılır: Windows Forms DataGridView denetiminde içerik değiştiğinde hücreleri otomatik olarak yeniden boyutlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data grids [Windows Forms], resizing cells automatically
- cells [Windows Forms], resizing automatically
- DataGridView control [Windows Forms], resizing cells
ms.assetid: 1d68934d-a04c-4b12-9e66-c856c6828131
ms.openlocfilehash: c745af77b5608a7b80f96e4d4421745ea28405ad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54592308"
---
# <a name="how-to-automatically-resize-cells-when-content-changes-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f1b29-102">Nasıl yapılır: Windows Forms DataGridView denetiminde içerik değiştiğinde hücreleri otomatik olarak yeniden boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="f1b29-102">How to: Automatically Resize Cells When Content Changes in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f1b29-103">Yapılandırabileceğiniz <xref:System.Windows.Forms.DataGridView> satırları, sütunları yeniden boyutlandırmak için Denetim ve üst bilgileri otomatik olarak her içerik değişiklikleri, hücre her zaman değerlerine kırpma olmadan görüntülemek için büyük olacak şekilde.</span><span class="sxs-lookup"><span data-stu-id="f1b29-103">You can configure the <xref:System.Windows.Forms.DataGridView> control to resize its rows, columns, and headers automatically whenever content changes, so that cells are always large enough to display their values without clipping.</span></span>  
  
 <span data-ttu-id="f1b29-104">Hangi hücrelerin yeni boyutlar belirlemek için kullanılan kısıtlamak için birçok seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="f1b29-104">You have many options to restrict which cells are used to determine the new sizes.</span></span> <span data-ttu-id="f1b29-105">Örneğin, yalnızca şu anda görüntülenen satırların değerlere göre sütunların genişliğini otomatik olarak yeniden boyutlandırmak için denetimi yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1b29-105">For example, you can configure the control to automatically resize the width of its columns based only on the values in rows that are currently displayed.</span></span> <span data-ttu-id="f1b29-106">Bu durumda, boyutlandırma yöntemleri gibi kullanmak isteyebilirsiniz ancak bu, Etkisizliği çok sayıda satırı, ile çalışırken önleyebilirsiniz <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> bazen ettiğiniz boyutlarını ayarlamak için.</span><span class="sxs-lookup"><span data-stu-id="f1b29-106">With this, you can avoid inefficiency when working with large numbers of rows, although in this case, you might want to use sizing methods such as <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A> to adjust sizes at times of your choosing.</span></span>  
  
 <span data-ttu-id="f1b29-107">Otomatik yeniden boyutlandırma hakkında daha fazla bilgi için bkz. [Windows Forms DataGridView denetimindeki boyutlandırma seçenekleri](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="f1b29-107">For more information about automatic resizing, see [Sizing Options in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="f1b29-108">Aşağıdaki kod örneği, otomatik olarak yeniden boyutlandırmak için kullanılabilir seçenekleri gösterir.</span><span class="sxs-lookup"><span data-stu-id="f1b29-108">The following code example demonstrates the options available for automatic resizing.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1b29-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="f1b29-109">Example</span></span>  
 [!code-cpp[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CPP/autosizing.cpp#0)]
 [!code-csharp[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/CS/autosizing.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.AutoSizing#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.AutoSizing/VB/autosizing.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f1b29-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="f1b29-110">Compiling the Code</span></span>  
 <span data-ttu-id="f1b29-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f1b29-111">This example requires:</span></span>  
  
-   <span data-ttu-id="f1b29-112">Sistem, System.Drawing ve System.Windows.Forms derlemelere başvuruları.</span><span class="sxs-lookup"><span data-stu-id="f1b29-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="f1b29-113">Visual Basic veya Visual C# için bu örnek komut satırından derleme hakkında daha fazla bilgi için bkz: [komut satırından derleme](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) veya [oluşturma ile komut satırı csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="f1b29-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="f1b29-114">Visual Studio bu örnekte yeni bir projeye kod yapıştırarak da oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f1b29-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="f1b29-115">Ayrıca bkz: [nasıl yapılır: Derleme ve Visual Studio kullanarak tam bir Windows Formları kod örneği çalıştırma](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="f1b29-115">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f1b29-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1b29-116">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [<span data-ttu-id="f1b29-117">Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="f1b29-117">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f1b29-118">Windows Forms DataGridView Denetimindeki Boyutlandırma Seçenekleri</span><span class="sxs-lookup"><span data-stu-id="f1b29-118">Sizing Options in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sizing-options-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f1b29-119">Nasıl yapılır: Windows Forms DataGridView denetiminde içeriği sığdıracak şekilde hücreleri programlı olarak yeniden boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="f1b29-119">How to: Programmatically Resize Cells to Fit Content in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programmatically-resize-cells-to-fit-content-in-the-datagrid.md)
