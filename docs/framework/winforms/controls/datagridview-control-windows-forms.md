---
title: DataGridView Denetimi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08a0cc15cff39bb936a78db95c73568aa643d0b6
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="3c252-102">DataGridView Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="3c252-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="3c252-103">`DataGridView` Denetimi verileri tablo biçiminde görüntülemek için güçlü ve esnek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c252-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="3c252-104">Kullanabileceğiniz `DataGridView` çok küçük miktarda veri, salt okunur görünümlerde göstermek için denetlemek ya da çok büyük veri kümelerine yönelik düzenlenebilir görünümlerini göstermek için ölçeklendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c252-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="3c252-105">Genişletebilirsiniz `DataGridView` çeşitli yollarla özel davranışları kullanarak uygulamalarınızı oluşturmak için denetiminde.</span><span class="sxs-lookup"><span data-stu-id="3c252-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="3c252-106">Örneğin, program aracılığıyla kendi algoritmaları sıralama belirtebilirsiniz ve hücrelerin kendi türlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c252-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="3c252-107">Kolayca görünümünü özelleştirebilirsiniz `DataGridView` çeşitli özellikler arasında seçerek denetim.</span><span class="sxs-lookup"><span data-stu-id="3c252-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="3c252-108">Veri depoları birçok türde bir veri kaynağı olarak kullanılabilir veya `DataGridView` denetim bağlı hiçbir veri kaynağıyla çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="3c252-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="3c252-109">Bu bölümdeki konular, kavramlar ve oluşturmak için kullanabileceğiniz teknikleri açıklar `DataGridView` , uygulamalara özellikleri.</span><span class="sxs-lookup"><span data-stu-id="3c252-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c252-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="3c252-110">In This Section</span></span>  
 [<span data-ttu-id="3c252-111">DataGridView denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="3c252-111">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="3c252-112">Windows Forms mimarisi ve temel kavramlar açıklayan konulara sağlar `DataGridView` denetim.</span><span class="sxs-lookup"><span data-stu-id="3c252-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="3c252-113">Varsayılan işlevsellik Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="3c252-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c252-114">Varsayılan Görünüm ve davranış Windows Formları açıklar `DataGridView` ne zaman bir veri kaynağına bağlı denetim.</span><span class="sxs-lookup"><span data-stu-id="3c252-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="3c252-115">Windows Forms DataGridView denetiminde sütun türleri</span><span class="sxs-lookup"><span data-stu-id="3c252-115">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c252-116">Windows Forms'ta sütun türleri açıklanmaktadır `DataGridView` verileri görüntülemek ve değiştirmek veya veri eklemek kullanıcıların izin vermek için kullanılan denetimi.</span><span class="sxs-lookup"><span data-stu-id="3c252-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="3c252-117">Temel sütun, satır ve hücre özellikleri Windows Forms DataGridView denetiminde</span><span class="sxs-lookup"><span data-stu-id="3c252-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="3c252-118">Sık kullanılan hücre, satır ve sütun özelliklerini açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c252-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="3c252-119">Temel biçimlendirme ve stil oluşturma Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="3c252-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c252-120">Temel denetimin görünümünü ve görüntü hücre verilerin biçimlendirmesini değiştirme açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c252-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="3c252-121">Windows Forms DataGridView denetiminde verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="3c252-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c252-122">El ile veya bir dış veri kaynağından veri denetimiyle doldurmak nasıl açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c252-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="3c252-123">Windows Forms DataGridView denetimindeki satırları ve sütunları yeniden boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="3c252-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c252-124">Nasıl satır ve sütunların boyutu otomatik olarak hücre içeriğin sığması için ya da denetim kullanılabilir genişliğine sığacak şekilde ayarlanabilir açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c252-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="3c252-125">Windows Forms DataGridView denetiminde verileri sıralama</span><span class="sxs-lookup"><span data-stu-id="3c252-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c252-126">Denetiminde sıralama özelliklerini açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c252-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="3c252-127">Veri girişi Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="3c252-127">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c252-128">Yol kullanıcıları değiştirmek nasıl açıklayan konulara ekleme ve verileri denetiminde değiştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c252-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="3c252-129">Seçim ve Pano kullanımı Windows Forms DataGridView denetimi ile</span><span class="sxs-lookup"><span data-stu-id="3c252-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c252-130">Denetiminde hücre, satır ve sütun seçimi özelliklerini açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c252-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="3c252-131">Hücrelerini, satırları ve sütunları Windows Forms DataGridView denetiminde ile programlama</span><span class="sxs-lookup"><span data-stu-id="3c252-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="3c252-132">Hücre, satır ve sütun nesneleri ile programlamayı açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c252-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="3c252-133">Windows Forms DataGridView denetimini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="3c252-133">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c252-134">Özel boyama açıklayan konulara sağlar `DataGridView` hücre ve satırları ve oluşturma türetilmiş hücre, sütun ve satır türleri.</span><span class="sxs-lookup"><span data-stu-id="3c252-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="3c252-135">Performans ayarlama Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="3c252-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c252-136">Denetim verimli bir şekilde büyük miktarlarda veri ile çalışırken, performans sorunlarını önlemek için nasıl kullanılacağını açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="3c252-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="3c252-137">Varsayılan klavye ve fare Windows Forms DataGridView denetiminde işleme</span><span class="sxs-lookup"><span data-stu-id="3c252-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="3c252-138">Kullanıcılar ile nasıl etkileşim kurabilir açıklar `DataGridView` denetim klavye ve fare aracılığıyla.</span><span class="sxs-lookup"><span data-stu-id="3c252-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="3c252-139">Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="3c252-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="3c252-140">Açıklar nasıl `DataGridView` denetim bağlı artırır ve değiştirir <xref:System.Windows.Forms.DataGrid> denetim.</span><span class="sxs-lookup"><span data-stu-id="3c252-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="3c252-141">Ayrıca bkz. [Windows Forms DataGridView denetimi ile Tasarımcı kullanarak](http://msdn.microsoft.com/library/ms171593\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="3c252-141">Also see [Using the Designer with the Windows Forms DataGridView Control](http://msdn.microsoft.com/library/ms171593\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3c252-142">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3c252-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="3c252-143">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="3c252-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="3c252-144">Başvuru belgelerine sağlar <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="3c252-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="3c252-145"><xref:System.Windows.Forms.DataGridView> Denetim ve <xref:System.Windows.Forms.BindingSource> bileşen yakından birlikte çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="3c252-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c252-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c252-146">See Also</span></span>  
 [<span data-ttu-id="3c252-147">Windows Forms'ta kullanılacak denetimler</span><span class="sxs-lookup"><span data-stu-id="3c252-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
