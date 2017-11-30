---
title: "Windows Forms DataGridView Denetimini Özelleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7d1246a8052af19057f7aa9d6729e34203177f8e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="216a9-102">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="216a9-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="216a9-103">`DataGridView` Denetim görünüm ve temel davranışını (Görünüm) hücrelerini, satırları ve sütunları ayarlamak için kullanabileceğiniz çeşitli özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="216a9-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="216a9-104">Yeteneklerini gidin özel gereksinimleri olup olmadığını <xref:System.Windows.Forms.DataGridViewCellStyle> sınıfı, ancak denetim için çizim sahibi uygulamak ya da özel hücreler, sütunları ve satırları oluşturarak yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="216a9-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="216a9-105">Hücre ve satırları kendiniz boyamak için çeşitli işleyebilir `DataGridView` boyama olaylar.</span><span class="sxs-lookup"><span data-stu-id="216a9-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="216a9-106">Varolan işlevlerini değiştirin veya yeni işlevsellik sağlamak için mevcut türetilmiş kendi türlerinizi oluşturabilirsiniz `DataGridViewCell`, `DataGridViewColumn`, ve `DataGridViewRow` türleri.</span><span class="sxs-lookup"><span data-stu-id="216a9-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="216a9-107">Bir hücre düzenleme modunda olduğunda seçtiğiniz bir denetimi görüntüleme türetilmiş türler oluşturarak yeni düzenleme yetenekleri de sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="216a9-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="216a9-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="216a9-108">In This Section</span></span>  
 [<span data-ttu-id="216a9-109">Nasıl yapılır: Windows Forms DataGridView denetiminde hücrelerin görünüşünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="216a9-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="216a9-110">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.CellPainting> boyamak için olay hücreleri el ile.</span><span class="sxs-lookup"><span data-stu-id="216a9-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="216a9-111">Nasıl yapılır: Windows Forms DataGridView denetiminde satırların görünüşünü özelleştirme</span><span class="sxs-lookup"><span data-stu-id="216a9-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="216a9-112">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.RowPrePaint> ve <xref:System.Windows.Forms.DataGridView.RowPostPaint> satırları gradyan, özel bir arka plan boyama ve içerik için olayları yayılan birden çok sütun.</span><span class="sxs-lookup"><span data-stu-id="216a9-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="216a9-113">Nasıl yapılır: hücreleri özelleştirebilir ve Windows Forms DataGridView denetiminde sütunları davranış ve görünümünü genişleterek</span><span class="sxs-lookup"><span data-stu-id="216a9-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="216a9-114">Türetilen özel türlerinin nasıl oluşturulacağı açıklanır `DataGridViewCell` ve `DataGridViewColumn` fare işaretçisi üzerlerinde getirildiğinde hücreleri vurgulamak için.</span><span class="sxs-lookup"><span data-stu-id="216a9-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="216a9-115">Nasıl yapılır: Windows bir düğme sütununda düğmeleri devre dışı bırakma Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="216a9-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="216a9-116">Türetilen özel türlerinin nasıl oluşturulacağı açıklanır <xref:System.Windows.Forms.DataGridViewButtonCell> ve <xref:System.Windows.Forms.DataGridViewButtonColumn> bir düğme sütununda düğmeleri devre dışı görüntülemek için.</span><span class="sxs-lookup"><span data-stu-id="216a9-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="216a9-117">Nasıl yapılır: Windows Forms DataGridView hücrelerinde denetimleri barındırma</span><span class="sxs-lookup"><span data-stu-id="216a9-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="216a9-118">Nasıl uygulandığı açıklanır `IDataGridViewEditingControl` arabirim ve türetilen özel türler oluşturma `DataGridViewCell` ve `DataGridViewColumn` görüntülemek için bir <xref:System.Windows.Forms.DateTimePicker> bir hücre düzenleme modunda olduğunda denetim.</span><span class="sxs-lookup"><span data-stu-id="216a9-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="216a9-119">Başvuru</span><span class="sxs-lookup"><span data-stu-id="216a9-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="216a9-120">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="216a9-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="216a9-121">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewCell> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="216a9-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="216a9-122">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewRow> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="216a9-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="216a9-123">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridViewColumn> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="216a9-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="216a9-124">Başvuru belgelerine sağlar <xref:System.Windows.Forms.IDataGridViewEditingControl> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="216a9-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="216a9-125">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="216a9-125">Related Sections</span></span>  
 [<span data-ttu-id="216a9-126">Temel biçimlendirme ve stil oluşturma Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="216a9-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="216a9-127">Temel denetimin görünümünü ve görüntü hücre verilerin biçimlendirmesini değiştirme açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="216a9-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="216a9-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="216a9-128">See Also</span></span>  
 [<span data-ttu-id="216a9-129">DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="216a9-129">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="216a9-130">Windows Forms DataGridView denetiminde sütun türleri</span><span class="sxs-lookup"><span data-stu-id="216a9-130">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
