---
title: Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: 5e967c1bbe54095cc11e48b014600158da7fe6a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189905"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e8088-102">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="e8088-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e8088-103">`DataGridView` Denetim temel hücrelerin görünüşünü ve görüntü biçimlendirme hücre değerlerini tanımlamak kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e8088-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="e8088-104">Görünüm tanımlayabilirsiniz ve biçimlendirme stilleri tek tek hücrelere, özel sütunlar ve satırlar hücreleri veya denetimindeki tüm hücreleri özelliklerini ayarlayarak `DataGridViewCellStyle` çeşitli erişilen nesneler `DataGridView` denetim özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e8088-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="e8088-105">Ayrıca, bu stilleri hücre değerini gibi faktörlere göre işleyerek dinamik olarak değiştirebilirsiniz `CellFormatting` olay.</span><span class="sxs-lookup"><span data-stu-id="e8088-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e8088-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e8088-106">In This Section</span></span>  
 [<span data-ttu-id="e8088-107">Nasıl yapılır: Kenarlık ve kılavuz çizgi stillerini Windows Forms DataGridView denetiminde değiştirme</span><span class="sxs-lookup"><span data-stu-id="e8088-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="e8088-108">Nasıl ayarlanacağı açıklanır `DataGridView` denetimi sınır ve sınır satırları hücreler arasındaki görünümü tanımlayan özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e8088-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="e8088-109">Windows Forms DataGridView Denetimindeki Hücre Stilleri</span><span class="sxs-lookup"><span data-stu-id="e8088-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e8088-110">Açıklar `DataGridViewCellStyle` sınıfı ve bu türün özelliklerini denetiminde hücrelerin nasıl görüntüleneceğini tanımlamak için nasıl etkileşim kuracağını.</span><span class="sxs-lookup"><span data-stu-id="e8088-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="e8088-111">Nasıl yapılır: Windows Forms DataGridView denetimi için varsayılan hücre stillerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="e8088-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e8088-112">Nasıl kullanılacağını açıklar `DataGridViewCellStyle` belirli satırlar ve sütunlar ve tüm denetiminde hücreler varsayılan görünümünü tanımlamak için özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e8088-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="e8088-113">Nasıl yapılır: Verileri biçimlendirme Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="e8088-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e8088-114">Kullanarak hücre görüntüleme değerlerinin nasıl biçimlendirileceğini açıklar `DataGridViewCellStyle` özellikleri.</span><span class="sxs-lookup"><span data-stu-id="e8088-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="e8088-115">Nasıl yapılır: Windows Forms DataGridView denetiminde yazı tipi ve renk stillerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="e8088-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e8088-116">Nasıl kullanılacağını açıklar `DefaultCellStyle` temel ayarlamak için özellik denetiminde tüm hücreler için özellikleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e8088-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="e8088-117">Nasıl yapılır: Windows Forms DataGridView denetimi için alternatif satır stillerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="e8088-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e8088-118">Büyük defter benzeri etkisi farklı görüntülenen değişen satırların kullanarak denetimi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="e8088-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="e8088-119">Nasıl yapılır: Windows Forms DataGridView denetimindeki satırları özelleştirmek için satır şablonunu kullanma</span><span class="sxs-lookup"><span data-stu-id="e8088-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="e8088-120">Nasıl kullanılacağını açıklar `RowTemplate` denetiminde tüm satırlar için kullanılacak satır özellikleri ayarlamak için özellik.</span><span class="sxs-lookup"><span data-stu-id="e8088-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e8088-121">Başvuru</span><span class="sxs-lookup"><span data-stu-id="e8088-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="e8088-122">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="e8088-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="e8088-123">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e8088-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="e8088-124">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.CellFormatting> olay.</span><span class="sxs-lookup"><span data-stu-id="e8088-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="e8088-125">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e8088-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e8088-126">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e8088-126">Related Sections</span></span>  
 [<span data-ttu-id="e8088-127">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e8088-127">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e8088-128">Özel boyama açıklayan konuları sağlar <xref:System.Windows.Forms.DataGridView> hücre ve satırları ve oluşturma türetilmiş hücre, sütun ve satır türleri.</span><span class="sxs-lookup"><span data-stu-id="e8088-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="e8088-129">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="e8088-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="e8088-130">Yaygın olarak açıklayan konulara kullanılan hücre, satır ve sütun özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="e8088-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8088-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8088-131">See also</span></span>

- [<span data-ttu-id="e8088-132">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="e8088-132">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
