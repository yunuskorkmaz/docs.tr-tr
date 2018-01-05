---
title: "Nasıl yapılır: Bir Windows Forms DataGridView Denetiminde Ayrı Hücrelere ToolTips Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tooltips [Windows Forms], adding to data grids
- DataGridView control [Windows Forms], adding tooltips
- data grids [Windows Forms], adding tooltips
ms.assetid: 2a81f9de-d58b-4ea8-bc0b-8d93c2f4cf78
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a533f4cbf5000489e774ba8661c3ab03cea4948a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="d8c5d-102">Nasıl yapılır: Bir Windows Forms DataGridView Denetiminde Ayrı Hücrelere ToolTips Ekleme</span><span class="sxs-lookup"><span data-stu-id="d8c5d-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d8c5d-103">Varsayılan olarak, araç ipuçları değerlerini görüntülemek için kullanılan <xref:System.Windows.Forms.DataGridView> tüm içerikleri göstermek için çok küçük olan hücre.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="d8c5d-104">Ancak, tek tek hücreler için araç ipucu metni değerlerini ayarlamak için bu davranış kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="d8c5d-105">Bu, kullanıcıların bir hücre hakkında ek bilgi görüntülemek için veya alternatif bir açıklama hücre içeriğinin kullanıcılara sağlamak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="d8c5d-106">Örneğin, durum simgelerini görüntüleyen bir satır varsa, araç ipuçları kullanma metin açıklamaları sağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="d8c5d-107">Ayarlayarak da hücre düzeyi ipuçlarını görüntülemeyi devre dışı bırakabilirsiniz <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="d8c5d-108">Bir araç ipucu bir hücreye eklemek için</span><span class="sxs-lookup"><span data-stu-id="d8c5d-108">To add a ToolTip to a cell</span></span>  
  
-   <span data-ttu-id="d8c5d-109">Ayarlama <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d8c5d-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d8c5d-110">Compiling the Code</span></span>  
  
-   <span data-ttu-id="d8c5d-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d8c5d-111">This example requires:</span></span>  
  
-   <span data-ttu-id="d8c5d-112">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `Rating` dört yıldız aracılığıyla bir dize değerini görüntülemek için ("*") simgeler.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("*") symbols.</span></span> <span data-ttu-id="d8c5d-113"><xref:System.Windows.Forms.DataGridView.CellFormatting> Denetiminin olayı olmalıdır ilişkili örnekte gösterilen olay işleyicisi yöntemi ile.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
-   <span data-ttu-id="d8c5d-114">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d8c5d-115">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d8c5d-115">Robust Programming</span></span>  
 <span data-ttu-id="d8c5d-116">Bağladığınızda <xref:System.Windows.Forms.DataGridView> denetlemek için dış veri kaynağına veya sanal modu uygulama tarafından kendi veri kaynağı sağlamak, performans sorunlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="d8c5d-117">Büyük miktarlarda veri çalışırken performans cezası önlemek için tanıtıcı <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> ayarı yerine olay <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> birden çok hücreyi özelliği.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="d8c5d-118">Ne zaman, tanıtıcı bu olay bir hücrenin değerini alma <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> özelliği olayını başlatır ve değerini döndürür <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> özelliği olarak belirtilen olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8c5d-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8c5d-119">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="d8c5d-120">Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="d8c5d-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)
