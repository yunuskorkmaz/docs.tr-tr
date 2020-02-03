---
title: DataGridView denetimini özelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744029"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="4f0ce-102">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="4f0ce-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4f0ce-103">`DataGridView` denetimi, hücrelerinin, satırlarının ve sütunlarının görünümünü ve temel davranışını (görünüm) ayarlamak için kullanabileceğiniz çeşitli özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="4f0ce-104">Ancak, <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfının yeteneklerini aşmaya yönelik özel gereksinimleriniz varsa, denetimin sahip çizimini de uygulayabilir veya özel hücreler, sütunlar ve satırlar oluşturarak yeteneklerini genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="4f0ce-105">Hücreleri ve satırları kendiniz boyamak için çeşitli `DataGridView` boyama olaylarını işleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="4f0ce-106">Mevcut işlevleri değiştirmek veya yeni işlevsellik sağlamak için, mevcut `DataGridViewCell`, `DataGridViewColumn`ve `DataGridViewRow` türlerinden türetilmiş kendi türlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="4f0ce-107">Ayrıca, bir hücre düzenleme modundayken seçtiğiniz bir denetimi görüntüleyen türetilmiş türler oluşturarak yeni düzenleme olanakları sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4f0ce-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4f0ce-108">In This Section</span></span>  
 [<span data-ttu-id="4f0ce-109">Nasıl yapılır: Windows Forms DataGridView Denetiminde Hücrelerin Görünüşünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="4f0ce-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="4f0ce-110">Hücreleri el ile boyamak için <xref:System.Windows.Forms.DataGridView.CellPainting> olayının nasıl işleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="4f0ce-111">Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="4f0ce-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="4f0ce-112">Özel, gradyan arka planı ve birden çok sütuna yayılan içerikle satırları boyamak için <xref:System.Windows.Forms.DataGridView.RowPrePaint> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint> olaylarının nasıl işleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="4f0ce-113">Nasıl yapılır: Windows Forms DataGridView Denetiminde Davranış ve Görünümünü Genişleterek Hücre ve Sütunları Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="4f0ce-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="4f0ce-114">Fare işaretçisi üzerinde bekletildiğinde hücreleri vurgulamak için `DataGridViewCell` ve `DataGridViewColumn` türetilmiş özel türlerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="4f0ce-115">Nasıl yapılır: Windows Forms DataGridView Denetimindeki Bir Düğme Sütununda Düğmeleri Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="4f0ce-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="4f0ce-116">Düğme sütununda devre dışı bırakılan düğmeleri göstermek için <xref:System.Windows.Forms.DataGridViewButtonCell> ve <xref:System.Windows.Forms.DataGridViewButtonColumn> türetilmiş özel türlerin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="4f0ce-117">Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma</span><span class="sxs-lookup"><span data-stu-id="4f0ce-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="4f0ce-118">`IDataGridViewEditingControl` arabirimini nasıl uygulayacağınızı ve bir hücre düzenleme modundayken bir <xref:System.Windows.Forms.DateTimePicker> denetimini göstermek için `DataGridViewCell` ve `DataGridViewColumn` türetilmiş özel türler oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4f0ce-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="4f0ce-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="4f0ce-120"><xref:System.Windows.Forms.DataGridView> denetimi için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="4f0ce-121"><xref:System.Windows.Forms.DataGridViewCell> sınıfı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="4f0ce-122"><xref:System.Windows.Forms.DataGridViewRow> sınıfı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="4f0ce-123"><xref:System.Windows.Forms.DataGridViewColumn> sınıfı için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="4f0ce-124"><xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4f0ce-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4f0ce-125">Related Sections</span></span>  
 [<span data-ttu-id="4f0ce-126">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="4f0ce-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4f0ce-127">Denetimin temel görünümünün ve hücre verilerinin görüntüleme biçimlendirmesinin nasıl değiştirileceğini betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f0ce-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f0ce-128">See also</span></span>

- [<span data-ttu-id="4f0ce-129">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="4f0ce-129">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="4f0ce-130">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="4f0ce-130">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
