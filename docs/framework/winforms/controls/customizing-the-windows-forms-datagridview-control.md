---
title: Windows Forms DataGridView Denetimini Özelleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 92bbace4d0869aca67025f1e4ac8c451fe073219
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529850"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="8d33d-102">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8d33d-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8d33d-103">`DataGridView` Denetim görünüm ve temel davranışını (Görünüm) hücrelerini, satırları ve sütunları ayarlamak için kullanabileceğiniz çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="8d33d-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="8d33d-104">Yeteneklerini gidin özel gereksinimleri olup olmadığını <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı, ancak denetim için çizim sahibi uygulamak ya da özel hücreler, sütunları ve satırları oluşturarak yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="8d33d-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="8d33d-105">Hücre ve satırları kendiniz boyamak için çeşitli işleyebilir `DataGridView` boyama olaylar.</span><span class="sxs-lookup"><span data-stu-id="8d33d-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="8d33d-106">Varolan işlevlerini değiştirin veya yeni işlevsellik sağlamak için mevcut türetilmiş kendi türlerinizi oluşturabilirsiniz `DataGridViewCell`, `DataGridViewColumn`, ve `DataGridViewRow` türleri.</span><span class="sxs-lookup"><span data-stu-id="8d33d-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="8d33d-107">Bir hücre düzenleme modunda olduğunda seçtiğiniz bir denetimi görüntüleme türetilmiş türler oluşturarak yeni düzenleme yetenekleri de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d33d-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8d33d-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8d33d-108">In This Section</span></span>  
 [<span data-ttu-id="8d33d-109">Nasıl yapılır: Windows Forms DataGridView Denetiminde Hücrelerin Görünüşünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8d33d-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="8d33d-110">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.CellPainting> boyamak için olay hücreleri el ile.</span><span class="sxs-lookup"><span data-stu-id="8d33d-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="8d33d-111">Nasıl yapılır: Windows Forms DataGridView Denetiminde Satırların Görünüşünü Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8d33d-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="8d33d-112">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.RowPrePaint> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint> satırları gradyan, özel bir arka plan boyama ve içerik için olayları yayılan birden çok sütun.</span><span class="sxs-lookup"><span data-stu-id="8d33d-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="8d33d-113">Nasıl yapılır: Windows Forms DataGridView Denetiminde Davranış ve Görünümünü Genişleterek Hücre ve Sütunları Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="8d33d-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="8d33d-114">Türetilen özel türlerinin nasıl oluşturulacağı açıklanır `DataGridViewCell` ve `DataGridViewColumn` fare işaretçisi üzerlerinde getirildiğinde hücreleri vurgulamak için.</span><span class="sxs-lookup"><span data-stu-id="8d33d-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="8d33d-115">Nasıl yapılır: Windows Forms DataGridView Denetimindeki Bir Düğme Sütununda Düğmeleri Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="8d33d-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="8d33d-116">Türetilen özel türlerinin nasıl oluşturulacağı açıklanır <xref:System.Windows.Forms.DataGridViewButtonCell> ve <xref:System.Windows.Forms.DataGridViewButtonColumn> bir düğme sütununda düğmeleri devre dışı görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="8d33d-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="8d33d-117">Nasıl yapılır: Windows Forms DataGridView Hücrelerinde Denetimleri Barındırma</span><span class="sxs-lookup"><span data-stu-id="8d33d-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="8d33d-118">Nasıl uygulandığı açıklanır `IDataGridViewEditingControl` arabirim ve türetilen özel türler oluşturma `DataGridViewCell` ve `DataGridViewColumn` görüntülemek için bir <xref:System.Windows.Forms.DateTimePicker> bir hücre düzenleme modunda olduğunda denetim.</span><span class="sxs-lookup"><span data-stu-id="8d33d-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8d33d-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="8d33d-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="8d33d-120">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="8d33d-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="8d33d-121">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewCell> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8d33d-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="8d33d-122">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewRow> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8d33d-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="8d33d-123">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewColumn> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8d33d-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="8d33d-124">Başvuru belgelerine sağlar <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8d33d-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8d33d-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="8d33d-125">Related Sections</span></span>  
 [<span data-ttu-id="8d33d-126">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="8d33d-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8d33d-127">Temel denetimin görünümünü ve görüntü hücre verilerin biçimlendirmesini değiştirme açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d33d-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d33d-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8d33d-128">See Also</span></span>  
 [<span data-ttu-id="8d33d-129">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="8d33d-129">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="8d33d-130">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="8d33d-130">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
