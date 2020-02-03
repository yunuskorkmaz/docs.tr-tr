---
title: DataGridView Denetimindeki temel biçimlendirme ve stil oluşturma
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d295718b7bd4f3bc4c5f63b6e6cb911f733525fe
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732002"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="86b36-102">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="86b36-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="86b36-103">`DataGridView` denetimi, hücrelerin temel görünümünü ve hücre değerlerinin görüntüleme biçimlendirmesini tanımlamanızı kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="86b36-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="86b36-104">Tek tek hücreler için görünüm ve biçimlendirme stilleri, belirli sütun ve satırlardaki hücreler için ya da denetimdeki tüm hücreler için, çeşitli `DataGridView` denetim özellikleriyle erişilen `DataGridViewCellStyle` nesnelerinin özelliklerini ayarlayarak belirleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86b36-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="86b36-105">Ayrıca, bu stilleri, `CellFormatting` olayını işleyerek hücre değeri gibi etkenlere göre dinamik olarak değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86b36-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86b36-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="86b36-106">In This Section</span></span>  
 [<span data-ttu-id="86b36-107">Nasıl yapılır: Windows Forms DataGridView Denetiminde Kenarlık ve Kılavuz Çizgi Stillerini Değiştirme</span><span class="sxs-lookup"><span data-stu-id="86b36-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="86b36-108">Denetim kenarlığının görünüşünü ve hücreler arasındaki sınır çizgilerini tanımlayan `DataGridView` özelliklerinin nasıl ayarlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86b36-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="86b36-109">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="86b36-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="86b36-110">`DataGridViewCellStyle` sınıfını ve bu türün özelliklerinin, denetimin denetimde nasıl görüntüleneceğini tanımlamak için nasıl etkileşim kuracağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86b36-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="86b36-111">Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Varsayılan Hücre Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="86b36-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="86b36-112">Belirli satırlarda ve sütunlarda ve tüm denetimdeki hücrelerin varsayılan görünümünü tanımlamak için `DataGridViewCellStyle` özelliklerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86b36-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="86b36-113">Nasıl yapılır: Windows Forms DataGridView Denetiminde Verileri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="86b36-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="86b36-114">`DataGridViewCellStyle` özellikleri kullanılarak hücre görüntüleme değerlerini biçimlendirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="86b36-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="86b36-115">Nasıl yapılır: Windows Forms DataGridView Denetiminde Yazı Tipi ve Renk Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="86b36-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="86b36-116">Denetimdeki tüm hücreler için temel görüntü özelliklerini ayarlamak üzere `DefaultCellStyle` özelliğinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86b36-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="86b36-117">Nasıl yapılır: Windows Forms DataGridView Denetimi İçin Alternatif Satır Stillerini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="86b36-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="86b36-118">Farklı şekilde görüntülenen alternatif satırları kullanarak denetimde bir muhasebe benzeri efektin nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86b36-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="86b36-119">Nasıl Yapılır: Windows Forms DataGridView Denetimindeki Satırları Özelleştirmek için Satır Şablonunu Kullanma</span><span class="sxs-lookup"><span data-stu-id="86b36-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="86b36-120">Denetimdeki tüm satırlarda kullanılacak satır özelliklerini ayarlamak için `RowTemplate` özelliğinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86b36-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="86b36-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="86b36-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="86b36-122"><xref:System.Windows.Forms.DataGridView> denetimi için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="86b36-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="86b36-123"><xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="86b36-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="86b36-124"><xref:System.Windows.Forms.DataGridView.CellFormatting> olayı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="86b36-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="86b36-125"><xref:System.Windows.Forms.DataGridView.RowTemplate%2A> özelliği için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="86b36-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="86b36-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="86b36-126">Related Sections</span></span>  
 [<span data-ttu-id="86b36-127">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="86b36-127">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="86b36-128">Özel boyama <xref:System.Windows.Forms.DataGridView> hücreleri ve satırları tanımlayan ve türetilmiş hücre, sütun ve satır türlerini oluşturan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="86b36-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="86b36-129">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="86b36-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="86b36-130">Yaygın olarak kullanılan hücre, satır ve sütun özelliklerini tanımlayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="86b36-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86b36-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86b36-131">See also</span></span>

- [<span data-ttu-id="86b36-132">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="86b36-132">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
