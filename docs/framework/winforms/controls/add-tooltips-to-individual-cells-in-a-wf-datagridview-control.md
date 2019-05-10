---
title: 'Nasıl yapılır: Bir Windows Forms DataGridView Denetiminde Ayrı Hücrelere ToolTips Ekleme'
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
ms.openlocfilehash: d0e9b3ad742633b135a2fe1c00af3fa72af7b44a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64663450"
---
# <a name="how-to-add-tooltips-to-individual-cells-in-a-windows-forms-datagridview-control"></a><span data-ttu-id="57955-102">Nasıl yapılır: Bir Windows Forms DataGridView Denetiminde Ayrı Hücrelere ToolTips Ekleme</span><span class="sxs-lookup"><span data-stu-id="57955-102">How to: Add ToolTips to Individual Cells in a Windows Forms DataGridView Control</span></span>
<span data-ttu-id="57955-103">Varsayılan olarak, araç ipuçları değerlerini görüntülemek için kullanılan <xref:System.Windows.Forms.DataGridView> tüm içerikleri göstermek için çok küçük hücreleri.</span><span class="sxs-lookup"><span data-stu-id="57955-103">By default, ToolTips are used to display the values of <xref:System.Windows.Forms.DataGridView> cells that are too small to show their entire contents.</span></span> <span data-ttu-id="57955-104">Ancak, tek tek hücrelere araç ipucu metin değerlerini ayarlamak için bu davranış, kılabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57955-104">You can override this behavior, however, to set ToolTip-text values for individual cells.</span></span> <span data-ttu-id="57955-105">Bu, kullanıcıların bir hücre hakkında ek bilgi görüntülemek veya kullanıcılara hücre içeriğini başka bir açıklamasını sağlamak için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="57955-105">This is useful to display to users additional information about a cell or to provide to users an alternate description of the cell contents.</span></span> <span data-ttu-id="57955-106">Örneğin, durum simgelerini görüntüleyen bir satır varsa, araç ipuçlarını kullanarak metin açıklamaları sağlamak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57955-106">For example, if you have a row that displays status icons, you may want to provide text explanations using ToolTips.</span></span>  
  
 <span data-ttu-id="57955-107">Ayarlayarak da hücre düzeyinde araç ipuçlarının görüntülenmesini devre dışı bırakabilirsiniz <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="57955-107">You can also disable the display of cell-level ToolTips by setting the <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType> property to `false`.</span></span>  
  
### <a name="to-add-a-tooltip-to-a-cell"></a><span data-ttu-id="57955-108">Bir araç ipucu bir hücreye eklemek için</span><span class="sxs-lookup"><span data-stu-id="57955-108">To add a ToolTip to a cell</span></span>  
  
- <span data-ttu-id="57955-109">Ayarlama <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="57955-109">Set the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/cpp/datagridviewcell.tooltiptext.cpp#1)]
     [!code-csharp[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/CS/datagridviewcell.tooltiptext.cs#1)]
     [!code-vb[System.Windows.Forms.DataGridViewCell.ToolTipText#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewCell.ToolTipText/VB/datagridviewcell.tooltiptext.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="57955-110">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="57955-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="57955-111">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="57955-111">This example requires:</span></span>  
  
- <span data-ttu-id="57955-112">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1` adlı bir sütun içeren `Rating` dört yıldız arasında bir dize değerleri görüntülemek için ("\*") simgeler.</span><span class="sxs-lookup"><span data-stu-id="57955-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `Rating` for displaying string values of one through four asterisk ("\*") symbols.</span></span> <span data-ttu-id="57955-113"><xref:System.Windows.Forms.DataGridView.CellFormatting> Olay denetimin olmalıdır ilişkili örnekte gösterilen olay işleyicisi yöntemi ile.</span><span class="sxs-lookup"><span data-stu-id="57955-113">The <xref:System.Windows.Forms.DataGridView.CellFormatting> event of the control must be associated with the event handler method shown in the example.</span></span>  
  
- <span data-ttu-id="57955-114">Başvurular <xref:System?displayProperty=nameWithType> ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="57955-114">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="57955-115">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="57955-115">Robust Programming</span></span>  
 <span data-ttu-id="57955-116">Bağladığınızda <xref:System.Windows.Forms.DataGridView> denetlemek için bir dış veri kaynağına veya sanal modu uygulama tarafından kendi veri kaynağı sağlamak için performans sorunlarıyla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="57955-116">When you bind the <xref:System.Windows.Forms.DataGridView> control to an external data source or provide your own data source by implementing virtual mode, you might encounter performance issues.</span></span> <span data-ttu-id="57955-117">Büyük miktarlarda veri ile çalışırken, bir performans cezasını önlemek için tanıtıcı <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> ayar yerine olay <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> birden çok hücre özelliği.</span><span class="sxs-lookup"><span data-stu-id="57955-117">To avoid a performance penalty when working with large amounts of data, handle the <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded> event rather than setting the <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property of multiple cells.</span></span> <span data-ttu-id="57955-118">Ne zaman ele bu olay bir hücrenin değerini alma <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> özelliği olayını başlatır ve değerini döndürür <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> özelliği olarak belirtilen olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="57955-118">When you handle this event, getting the value of a cell <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A> property raises the event and returns the value of the <xref:System.Windows.Forms.DataGridViewCellToolTipTextNeededEventArgs.ToolTipText%2A?displayProperty=nameWithType> property as specified in the event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57955-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="57955-119">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ShowCellToolTips%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell>
- <xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="57955-120">Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="57955-120">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)
