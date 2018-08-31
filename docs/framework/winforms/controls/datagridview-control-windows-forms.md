---
title: DataGridView Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- data grids [Windows Forms
- data [Windows Forms], displaying in tabular format
- grid controls [Windows Forms]
- datasets [Windows Forms], user interface
- Windows Forms, displaying data
- data presentation
- tabular data [Windows Forms], displaying on Windows Forms
- datasets [Windows Forms], displaying in DataGridView control
- DataGridView control [Windows Forms]
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
ms.openlocfilehash: 2ef387437befe3df67e261b719140456a3fde9dd
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2018
ms.locfileid: "43332513"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="92b55-102">DataGridView Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="92b55-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="92b55-103">`DataGridView` Denetimi verileri tablo biçiminde görüntülemek için güçlü ve esnek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b55-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="92b55-104">Kullanabileceğiniz `DataGridView` az miktarda veriniz salt okunur görünümlerini göstermek için denetim ya da çok büyük veri kümelerini düzenlenebilir görünümlerini göstermek için ölçeklendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="92b55-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="92b55-105">Genişletebileceğiniz `DataGridView` uygulamalarınızda özel davranışlar oluşturun için yol çeşitli denetim.</span><span class="sxs-lookup"><span data-stu-id="92b55-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="92b55-106">Örneğin, program aracılığıyla kendi algoritmaların sıralanması belirtebilirsiniz ve hücrelerin kendi türlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="92b55-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="92b55-107">Kolayca görünümünü özelleştirebilirsiniz `DataGridView` arasında çeşitli özellikleri seçerek denetimi.</span><span class="sxs-lookup"><span data-stu-id="92b55-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="92b55-108">Birçok veri depolarının türde bir veri kaynağı olarak kullanılabilir veya `DataGridView` denetim, kendisiyle ilişkili hiçbir veri kaynağıyla çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="92b55-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="92b55-109">Bu bölümdeki konular, kavramlar ve oluşturmak için kullanabileceğiniz teknikleri açıklar `DataGridView` uygulamalarınızla özellikleri.</span><span class="sxs-lookup"><span data-stu-id="92b55-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="92b55-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="92b55-110">In This Section</span></span>  
 [<span data-ttu-id="92b55-111">DataGridView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="92b55-111">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="92b55-112">Windows Forms mimarisine ve temel kavramları açıklayan konuları sağlar `DataGridView` denetimi.</span><span class="sxs-lookup"><span data-stu-id="92b55-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="92b55-113">Windows Forms DataGridView Denetimindeki Varsayılan İşlevler</span><span class="sxs-lookup"><span data-stu-id="92b55-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92b55-114">Varsayılan görünümünü ve davranışını Windows Forms açıklar `DataGridView` ne zaman, bir veri kaynağına bağlı olduğu denetim.</span><span class="sxs-lookup"><span data-stu-id="92b55-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="92b55-115">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="92b55-115">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92b55-116">Windows Forms'ta sütun türleri açıklayan `DataGridView` verileri görüntülemek ve değiştirmek veya veri eklemek kullanıcılara izin vermek için kullanılan denetimi.</span><span class="sxs-lookup"><span data-stu-id="92b55-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="92b55-117">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="92b55-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="92b55-118">Sık kullanılan hücre, satır ve sütun özelliklerini açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b55-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="92b55-119">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="92b55-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92b55-120">Denetiminin temel görünümünü ve görüntü hücre verilerin biçimlendirmesini değiştirme açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b55-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="92b55-121">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="92b55-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92b55-122">El ile veya bir dış veri kaynağından denetimi veriyle doldurmak nasıl açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b55-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="92b55-123">Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="92b55-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92b55-124">Nasıl satırları ve sütunları boyutu otomatik olarak hücre içeriğini sığdırmak için veya denetim kullanılabilir genişliğine sığacak şekilde ayarlanabilir açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b55-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="92b55-125">Windows Forms DataGridView Denetimindeki Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="92b55-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92b55-126">Denetiminde sıralama özellikleri açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b55-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="92b55-127">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="92b55-127">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92b55-128">Kullanıcıların değiştirme açıklayan konulara ekleyin ve denetimi veri değiştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b55-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="92b55-129">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="92b55-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92b55-130">Denetiminde hücre, satır ve sütun seçimi özellikleri açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b55-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="92b55-131">Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="92b55-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="92b55-132">Hücre, satır ve sütun nesneleri ile program açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b55-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="92b55-133">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="92b55-133">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92b55-134">Özel boyama açıklayan konuları sağlar `DataGridView` hücre ve satırları ve oluşturma türetilmiş hücre, sütun ve satır türleri.</span><span class="sxs-lookup"><span data-stu-id="92b55-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="92b55-135">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="92b55-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92b55-136">Denetim verimli bir şekilde büyük miktarlarda veri ile çalışırken, performans sorunlarını önlemek için nasıl kullanılacağını açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="92b55-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="92b55-137">Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı</span><span class="sxs-lookup"><span data-stu-id="92b55-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="92b55-138">Kullanıcılar ile nasıl etkileşim kurabileceğine açıklar `DataGridView` denetim klavye ve fare.</span><span class="sxs-lookup"><span data-stu-id="92b55-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="92b55-139">Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="92b55-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="92b55-140">Açıklayan nasıl `DataGridView` denetim üzerinde artırır ve değiştirir <xref:System.Windows.Forms.DataGrid> denetimi.</span><span class="sxs-lookup"><span data-stu-id="92b55-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="92b55-141">Ayrıca bkz: [Tasarımcı kullanarak Windows Forms DataGridView denetimi ile](using-the-designer-with-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="92b55-141">Also see [Using the Designer with the Windows Forms DataGridView Control](using-the-designer-with-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="92b55-142">Başvuru</span><span class="sxs-lookup"><span data-stu-id="92b55-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="92b55-143">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="92b55-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="92b55-144">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="92b55-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="92b55-145"><xref:System.Windows.Forms.DataGridView> Denetimi ve <xref:System.Windows.Forms.BindingSource> bileşen yakından birlikte çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="92b55-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92b55-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92b55-146">See Also</span></span>  
 [<span data-ttu-id="92b55-147">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="92b55-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
