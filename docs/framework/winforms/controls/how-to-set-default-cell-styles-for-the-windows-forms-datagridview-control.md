---
title: DataGridView denetimi için varsayılan hücre stillerini ayarlama
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 6b2d7de671e48ae8f55987c262e15717138b3fb4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744875"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="7ec98-102">Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="7ec98-102">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7ec98-103"><xref:System.Windows.Forms.DataGridView> denetimiyle, tüm denetim için ve belirli sütun ve satırlar için varsayılan hücre stillerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ec98-103">With the <xref:System.Windows.Forms.DataGridView> control, you can specify default cell styles for the entire control and for specific columns and rows.</span></span> <span data-ttu-id="7ec98-104">Bu varsayılanlar, denetim düzeyinden sütun düzeyine, ardından satır düzeyine, sonra da hücre düzeyine göre filtreleyerek ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7ec98-104">These defaults filter down from the control level to the column level, then to the row level, then to the cell level.</span></span> <span data-ttu-id="7ec98-105">Belirli bir <xref:System.Windows.Forms.DataGridViewCellStyle> özelliği hücre düzeyinde ayarlanmamışsa, satır düzeyindeki varsayılan özellik ayarı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ec98-105">If a particular <xref:System.Windows.Forms.DataGridViewCellStyle> property is not set at the cell level, the default property setting at the row level is used.</span></span> <span data-ttu-id="7ec98-106">Özellik satır düzeyinde de ayarlanmamışsa, varsayılan sütun ayarı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ec98-106">If the property is also not set at the row level, the default column setting is used.</span></span> <span data-ttu-id="7ec98-107">Son olarak, özellik sütun düzeyinde de ayarlanmamışsa, varsayılan <xref:System.Windows.Forms.DataGridView> ayarı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7ec98-107">Finally, if the property is also not set at the column level, the default <xref:System.Windows.Forms.DataGridView> setting is used.</span></span> <span data-ttu-id="7ec98-108">Bu ayarla, özellik ayarlarını birden çok düzeyde çoğaltmak zorunda kalmaktan kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7ec98-108">With this setting, you can avoid having to duplicate the property settings at multiple levels.</span></span> <span data-ttu-id="7ec98-109">Her düzeyde, yukarıdaki düzeyden farklı olan stilleri belirtmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="7ec98-109">At each level, simply specify the styles that differ from the levels above it.</span></span> <span data-ttu-id="7ec98-110">Daha fazla bilgi için [Windows Forms DataGridView Denetimindeki Hücre stilleri](cell-styles-in-the-windows-forms-datagridview-control.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7ec98-110">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="7ec98-111">Visual Studio 'da bu görev için kapsamlı destek vardır.</span><span class="sxs-lookup"><span data-stu-id="7ec98-111">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="7ec98-112">Ayrıca bkz. [nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGridView denetimi Için varsayılan hücre stillerini ve veri biçimlerini ayarlama](default-cell-styles-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="7ec98-112">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](default-cell-styles-datagridview.md).</span></span>  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a><span data-ttu-id="7ec98-113">Varsayılan hücre stillerini programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="7ec98-113">To set the default cell styles programmatically</span></span>  
  
1. <span data-ttu-id="7ec98-114"><xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliği aracılığıyla alınan <xref:System.Windows.Forms.DataGridViewCellStyle> özelliklerini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ec98-114">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> retrieved through the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2. <span data-ttu-id="7ec98-115">Birden çok satır ve sütun tarafından kullanılmak üzere yeni <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri oluşturun ve başlatın.</span><span class="sxs-lookup"><span data-stu-id="7ec98-115">Create and initialize new <xref:System.Windows.Forms.DataGridViewCellStyle> objects for use by multiple rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3. <span data-ttu-id="7ec98-116">Belirli satırların ve sütunların `DefaultCellStyle` özelliğini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7ec98-116">Set the `DefaultCellStyle` property of specific rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a><span data-ttu-id="7ec98-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ec98-117">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7ec98-118">Kod Derleme</span><span class="sxs-lookup"><span data-stu-id="7ec98-118">Compiling the Code</span></span>  
 <span data-ttu-id="7ec98-119">Bu örnek şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="7ec98-119">This example requires:</span></span>  
  
- <span data-ttu-id="7ec98-120">`dataGridView1`adlı <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="7ec98-120">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="7ec98-121"><xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemelerine başvurular.</span><span class="sxs-lookup"><span data-stu-id="7ec98-121">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="7ec98-122">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="7ec98-122">Robust Programming</span></span>  
 <span data-ttu-id="7ec98-123">Çok büyük veri kümeleriyle çalışırken en yüksek ölçeklenebilirlik elde etmek için, tek tek öğeler için stil özelliklerini ayrı ayrı ayarlamak yerine, <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri birden çok satırda, sütunda veya aynı stilleri kullanan hücrelerden paylaşmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ec98-123">To achieve maximum scalability when you work with very large data sets, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than set the style properties for individual elements separately.</span></span> <span data-ttu-id="7ec98-124">Ayrıca, <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> özelliğini kullanarak paylaşılan satırlar oluşturmanız ve bunlara erişmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7ec98-124">Additionally, you should create shared rows and access them by using the <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="7ec98-125">Daha fazla bilgi için bkz. [Windows Forms DataGridView denetimini ölçeklendirme Için En Iyi uygulamalar](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="7ec98-125">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec98-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ec98-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7ec98-127">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="7ec98-127">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7ec98-128">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="7ec98-128">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7ec98-129">Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ec98-129">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="7ec98-130">Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="7ec98-130">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
