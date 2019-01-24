---
title: Windows Forms DataGridView Denetimini Özelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 901b221f74fa76221ed3f19e9eb4c5f17c6534fa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559560"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="83fac-102">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="83fac-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="83fac-103">`DataGridView` Denetim görünümünü ve temel davranışını (Görünüm) kendi hücreler, satırlar ve sütunlarla ayarlamak için kullanabileceğiniz çeşitli özellikler sağlar.</span><span class="sxs-lookup"><span data-stu-id="83fac-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="83fac-104">Sunulan özelliklerin ötesine geçebilen özel gereksinimleri varsa <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı, ancak ayrıca sahip çizim denetimi için uygulayan veya özel bir hücre, sütunları ve satırları oluşturarak yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="83fac-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="83fac-105">Hücre ve satırları kendiniz boyamak için çeşitli işleyebilir `DataGridView` boyama olayları.</span><span class="sxs-lookup"><span data-stu-id="83fac-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="83fac-106">Mevcut işlevselliğini değiştirmenize veya yeni işlevsellik sağlamak için mevcut türetilen kendi türlerinizi oluşturabilirsiniz `DataGridViewCell`, `DataGridViewColumn`, ve `DataGridViewRow` türleri.</span><span class="sxs-lookup"><span data-stu-id="83fac-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="83fac-107">Bir hücre düzenleme modunda olduğunda, seçtiğiniz bir denetimi görüntüleme türetilmiş türleri oluşturarak yeni düzenleme özellikleri de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="83fac-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83fac-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="83fac-108">In This Section</span></span>  
 [<span data-ttu-id="83fac-109">Nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="83fac-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="83fac-110">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.CellPainting> boyamak için olay hücreleri el ile.</span><span class="sxs-lookup"><span data-stu-id="83fac-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="83fac-111">Nasıl yapılır: Windows Forms DataGridView denetiminde satırların görünüşünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="83fac-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="83fac-112">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.RowPrePaint> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint> satırlarla gradyan, özel bir arka plan boyama ve içerik için olayları yayılan birden çok sütun.</span><span class="sxs-lookup"><span data-stu-id="83fac-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="83fac-113">Nasıl yapılır: Davranış ve görünümünü genişleterek hücre ve sütunları Windows Forms DataGridView denetiminde özelleştirme</span><span class="sxs-lookup"><span data-stu-id="83fac-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="83fac-114">Öğesinden türetilen özel türler oluşturmayı açıklar `DataGridViewCell` ve `DataGridViewColumn` için fare işaretçisi üzerinde getirildiğinde hücreleri vurgulayın.</span><span class="sxs-lookup"><span data-stu-id="83fac-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="83fac-115">Nasıl yapılır: Windows Forms DataGridView denetimindeki bir düğme sütununda düğmeleri devre dışı bırak</span><span class="sxs-lookup"><span data-stu-id="83fac-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="83fac-116">Öğesinden türetilen özel türler oluşturmayı açıklar <xref:System.Windows.Forms.DataGridViewButtonCell> ve <xref:System.Windows.Forms.DataGridViewButtonColumn> bir düğme sütununda düğmeleri devre dışı görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="83fac-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="83fac-117">Nasıl yapılır: Windows Forms DataGridView hücrelerinde konak denetimleri</span><span class="sxs-lookup"><span data-stu-id="83fac-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="83fac-118">Nasıl uygulanacağını açıklar `IDataGridViewEditingControl` arabirim ve türetilen özel türler oluşturma `DataGridViewCell` ve `DataGridViewColumn` görüntülemek için bir <xref:System.Windows.Forms.DateTimePicker> bir hücre düzenleme modunda olduğunda denetim.</span><span class="sxs-lookup"><span data-stu-id="83fac-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="83fac-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="83fac-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="83fac-120">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="83fac-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="83fac-121">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewCell> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="83fac-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="83fac-122">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewRow> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="83fac-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="83fac-123">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridViewColumn> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="83fac-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="83fac-124">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="83fac-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="83fac-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="83fac-125">Related Sections</span></span>  
 [<span data-ttu-id="83fac-126">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="83fac-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="83fac-127">Denetiminin temel görünümünü ve görüntü hücre verilerin biçimlendirmesini değiştirme açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="83fac-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83fac-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="83fac-128">See also</span></span>
- [<span data-ttu-id="83fac-129">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="83fac-129">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
- [<span data-ttu-id="83fac-130">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="83fac-130">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
