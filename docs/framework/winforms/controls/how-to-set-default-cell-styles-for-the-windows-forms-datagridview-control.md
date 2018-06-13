---
title: 'Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stillerini Ayarlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: ed7ff720d8ef4aa2caa858ea61c4d38866cf50a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538687"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="d0432-102">Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="d0432-102">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d0432-103">İle <xref:System.Windows.Forms.DataGridView> denetimi, belirli sütunları ve satırları ve tüm denetim için varsayılan hücre stillerini belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d0432-103">With the <xref:System.Windows.Forms.DataGridView> control, you can specify default cell styles for the entire control and for specific columns and rows.</span></span> <span data-ttu-id="d0432-104">Bu varsayılan aşağı sütun düzeyi sonra satır düzeyinde sonra hücre düzeyi denetim düzeyden filtreleyin.</span><span class="sxs-lookup"><span data-stu-id="d0432-104">These defaults filter down from the control level to the column level, then to the row level, then to the cell level.</span></span> <span data-ttu-id="d0432-105">Belirli bir varsa <xref:System.Windows.Forms.DataGridViewCellStyle> özelliği hücre düzeyinde ayarlanmamışsa, varsayılan özellik ayarı satır düzeyinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0432-105">If a particular <xref:System.Windows.Forms.DataGridViewCellStyle> property is not set at the cell level, the default property setting at the row level is used.</span></span> <span data-ttu-id="d0432-106">Özelliği de satır düzeyinde ayarlanmazsa, varsayılan sütun ayarı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0432-106">If the property is also not set at the row level, the default column setting is used.</span></span> <span data-ttu-id="d0432-107">Son olarak, özellik de sütun düzeyinde varsayılan ayarlı değil, <xref:System.Windows.Forms.DataGridView> ayarı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d0432-107">Finally, if the property is also not set at the column level, the default <xref:System.Windows.Forms.DataGridView> setting is used.</span></span> <span data-ttu-id="d0432-108">Bu ayar, birçok düzeyde özellik ayarları çoğaltmak olmamasına özen gösterin.</span><span class="sxs-lookup"><span data-stu-id="d0432-108">With this setting, you can avoid having to duplicate the property settings at multiple levels.</span></span> <span data-ttu-id="d0432-109">Her düzey, yalnızca yukarıdaki düzeyleri farklı stilleri belirtin.</span><span class="sxs-lookup"><span data-stu-id="d0432-109">At each level, simply specify the styles that differ from the levels above it.</span></span> <span data-ttu-id="d0432-110">Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimindeki hücre stilleri](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d0432-110">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="d0432-111">Visual Studio'da bu görev için kapsamlı destek yoktur.</span><span class="sxs-lookup"><span data-stu-id="d0432-111">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="d0432-112">Ayrıca bkz. [nasıl yapılır: varsayılan hücre stillerini ayarlama ve veri biçimleri Windows Forms DataGridView denetimi kullanan bir tasarımcı](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="d0432-112">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a><span data-ttu-id="d0432-113">Varsayılan hücre stilleri programlı olarak ayarlamak için</span><span class="sxs-lookup"><span data-stu-id="d0432-113">To set the default cell styles programmatically</span></span>  
  
1.  <span data-ttu-id="d0432-114">Özellik kümesinin <xref:System.Windows.Forms.DataGridViewCellStyle> üzerinden alınan <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d0432-114">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> retrieved through the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  <span data-ttu-id="d0432-115">Oluşturma ve başlatma yeni <xref:System.Windows.Forms.DataGridViewCellStyle> nesneleri birden çok satır ve sütun tarafından kullanım için.</span><span class="sxs-lookup"><span data-stu-id="d0432-115">Create and initialize new <xref:System.Windows.Forms.DataGridViewCellStyle> objects for use by multiple rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  <span data-ttu-id="d0432-116">Ayarlama `DefaultCellStyle` belirli satırları ve sütunları özelliği.</span><span class="sxs-lookup"><span data-stu-id="d0432-116">Set the `DefaultCellStyle` property of specific rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a><span data-ttu-id="d0432-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="d0432-117">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d0432-118">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="d0432-118">Compiling the Code</span></span>  
 <span data-ttu-id="d0432-119">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d0432-119">This example requires:</span></span>  
  
-   <span data-ttu-id="d0432-120">A <xref:System.Windows.Forms.DataGridView> adlı Denetim `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="d0432-120">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="d0432-121">Başvurular <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, ve <xref:System.Windows.Forms?displayProperty=nameWithType> derlemeler.</span><span class="sxs-lookup"><span data-stu-id="d0432-121">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="d0432-122">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="d0432-122">Robust Programming</span></span>  
 <span data-ttu-id="d0432-123">Çok büyük veri kümeleri ile çalışırken en büyük ölçeklenebilirlik elde etmek için paylaşmalıdır <xref:System.Windows.Forms.DataGridViewCellStyle> birden çok satırları, sütunları veya ayrı ayrı ayrı ayrı öğeler stil özelliklerini ayarlamak yerine aynı stilleri kullanın hücreleri nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d0432-123">To achieve maximum scalability when you work with very large data sets, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than set the style properties for individual elements separately.</span></span> <span data-ttu-id="d0432-124">Ayrıca, paylaşılan satırlar oluşturmak ve bunları kullanarak erişim <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d0432-124">Additionally, you should create shared rows and access them by using the <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="d0432-125">Daha fazla bilgi için bkz: [Windows Forms DataGridView denetimini ölçeklendirme için en iyi yöntemler](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d0432-125">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0432-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d0432-126">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="d0432-127">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="d0432-127">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="d0432-128">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="d0432-128">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="d0432-129">Windows Forms DataGridView Denetimini Ölçeklendirme için En İyi Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d0432-129">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="d0432-130">Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="d0432-130">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
