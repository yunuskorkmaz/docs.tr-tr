---
title: DataGridView Denetimindeki kenarlık ve kılavuz çizgisi stillerini değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
ms.openlocfilehash: 918102a87ee29a3d3b78d6e6eedce57237135a51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744703"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9c8e4-102">Nasıl yapılır: Windows Forms DataGridView Denetiminde Kenarlık ve Kılavuz Çizgi Stillerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="9c8e4-102">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9c8e4-103"><xref:System.Windows.Forms.DataGridView> denetimiyle, Kullanıcı deneyimini geliştirmek için denetimin kenarlığının ve kılavuz çizgilerinin görünümünü özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-103">With the <xref:System.Windows.Forms.DataGridView> control, you can customize the appearance of the control's border and gridlines to improve the user experience.</span></span> <span data-ttu-id="9c8e4-104">Denetim içindeki hücrelerin kenarlık stillerine ek olarak kılavuz çizgisi rengini ve denetim kenarlığı stilini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-104">You can modify the gridline color and the control border style in addition to the border styles for the cells within the control.</span></span> <span data-ttu-id="9c8e4-105">Ayrıca, normal hücreler, satır üst bilgisi hücreleri ve sütun üst bilgisi hücreleri için farklı hücre kenarlık stilleri uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-105">You can also apply different cell border styles for ordinary cells, row header cells, and column header cells.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c8e4-106">Kılavuz çizgisi rengi yalnızca <xref:System.Windows.Forms.DataGridViewCellBorderStyle> numaralandırmanın <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>ve <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> değerleriyle ve <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> numaralandırmasının <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> değerine sahip olacak şekilde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-106">The gridline color is used only with the <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, and <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> values of the <xref:System.Windows.Forms.DataGridViewCellBorderStyle> enumeration and the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> value of the <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> enumeration.</span></span> <span data-ttu-id="9c8e4-107">Bu Numaralandırmaların diğer değerleri, işletim sistemi tarafından belirtilen renkleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-107">The other values of these enumerations use colors specified by the operating system.</span></span> <span data-ttu-id="9c8e4-108">Ayrıca, Windows XP ve Windows Server 2003 ailesinde <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> yöntemi aracılığıyla görsel stiller etkinleştirildiğinde <xref:System.Windows.Forms.DataGridView.GridColor%2A> Özellik değeri kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-108">Additionally, when visual styles are enabled on Windows XP and the Windows Server 2003 family through the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method, the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property value is not used.</span></span>  
  
### <a name="to-change-the-gridline-color-programmatically"></a><span data-ttu-id="9c8e4-109">Kılavuz çizgisi rengini programlı olarak değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="9c8e4-109">To change the gridline color programmatically</span></span>  
  
- <span data-ttu-id="9c8e4-110"><xref:System.Windows.Forms.DataGridView.GridColor%2A> özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-110">Set the <xref:System.Windows.Forms.DataGridView.GridColor%2A> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a><span data-ttu-id="9c8e4-111">Tüm DataGridView denetiminin kenarlık stilini programlı olarak değiştirme</span><span class="sxs-lookup"><span data-stu-id="9c8e4-111">To change the border style of the entire DataGridView control programmatically</span></span>  
  
- <span data-ttu-id="9c8e4-112"><xref:System.Windows.Forms.DataGridView.BorderStyle%2A> özelliğini <xref:System.Windows.Forms.BorderStyle> sabit listesi değerlerinden birine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-112">Set the <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> property to one of the <xref:System.Windows.Forms.BorderStyle> enumeration values.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a><span data-ttu-id="9c8e4-113">DataGridView hücrelerinin kenarlık stillerini programlı olarak değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="9c8e4-113">To change the border styles for DataGridView cells programmatically</span></span>  
  
- <span data-ttu-id="9c8e4-114"><xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>ve <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-114">Set the <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, and <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> properties.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a><span data-ttu-id="9c8e4-115">Örnek</span><span class="sxs-lookup"><span data-stu-id="9c8e4-115">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9c8e4-116">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="9c8e4-116">Compiling the Code</span></span>  
 <span data-ttu-id="9c8e4-117">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="9c8e4-117">This example requires:</span></span>  
  
- <span data-ttu-id="9c8e4-118">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-118">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="9c8e4-119"><xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>ve <xref:System.Drawing?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-119">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c8e4-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c8e4-120">See also</span></span>

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [<span data-ttu-id="9c8e4-121">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="9c8e4-121">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
