---
title: DataGridView Denetimindeki ayrı hücrelere araç Ipucu ekleme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
ms.openlocfilehash: ac86db5fa27a95adb20888cd59b5e236941d9177
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732186"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="ebbc0-102">Nasıl yapılır: Bir Windows Forms DataGridView Denetiminde Ayrı Hücrelere ToolTips Ekleme</span><span class="sxs-lookup"><span data-stu-id="ebbc0-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="ebbc0-103">Varsayılan olarak, araç Ipuçları, tüm içeriğini göstermek için çok küçük olan <xref:System.Windows.Forms.DataGridView> hücrelerinin değerlerini görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="ebbc0-104">Bununla birlikte, tek tek hücreler için araç Ipucu metin değerlerini ayarlamak için bu davranışı geçersiz kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="ebbc0-105">Bu, kullanıcılara bir hücreyle ilgili ek bilgiler göstermek veya kullanıcılara hücre içeriğinin alternatif bir açıklamasını sağlamak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="ebbc0-106">Örneğin, durum simgelerini görüntüleyen bir satırınız varsa, araç Ipuçlarını kullanarak metin açıklamaları sağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="ebbc0-107">Ayrıca, <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> özelliğini `false`olarak ayarlayarak hücre düzeyi araç Ipuçlarının görüntülenmesini devre dışı bırakabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="ebbc0-108">Bir hücreye araç Ipucu eklemek için</span><span class="sxs-lookup"><span data-stu-id="ebbc0-108">To add a ToolTip to a cell</span></span>  
  
- <span data-ttu-id="ebbc0-109"><xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ebbc0-110">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="ebbc0-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="ebbc0-111">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="ebbc0-111">This example requires:</span></span>  
  
- <span data-ttu-id="ebbc0-112">`dataGridView1` adlı bir <xref:System.Windows.Forms.DataGridView> denetim, bir-dört yıldız işareti ("\*") sembollerinin dize değerlerini görüntülemek için `Rating` adlı bir sütun içerir.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("\*") symbols.</span></span> <span data-ttu-id="ebbc0-113">Denetimin <xref:System.Windows.Forms.DataGridView.CellFormatting> olayının, örnekte gösterilen olay işleyicisi yöntemiyle ilişkilendirilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
- <span data-ttu-id="ebbc0-114"><xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ebbc0-115">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="ebbc0-115">Robust Programming</span></span>  
 <span data-ttu-id="ebbc0-116"><xref:System.Windows.Forms.DataGridView> denetimini bir dış veri kaynağına bağladığınızda veya sanal modu uygulayarak kendi veri kaynağınızı sağladığınızda, performans sorunlarıyla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="ebbc0-117">Büyük miktarlardaki verilerle çalışırken bir performans cezasından kaçınmak için, birden çok hücrenin <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> özelliğini ayarlamak yerine <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> olayı işleyin.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="ebbc0-118">Bu olayı işlerken, bir hücrenin değerini alma <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> özelliği olayı oluşturur ve olay işleyicisinde belirtilen <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> özelliğinin değerini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebbc0-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebbc0-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="ebbc0-120">Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="ebbc0-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
