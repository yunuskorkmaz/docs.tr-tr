---
title: DataGridView Denetimi
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
ms.openlocfilehash: fc40c0f08c0c11fa9acc94ce12caab8766658f1e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746954"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="358a7-102">DataGridView Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="358a7-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="358a7-103">`DataGridView` denetim, verileri tablolu biçimde görüntülemenin güçlü ve esnek bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="358a7-104">Daha az miktarda verinin salt okunurdur görünümlerini göstermek için `DataGridView` denetimini kullanabilir veya çok büyük veri kümelerinin düzenlenebilir görünümlerini göstermek üzere ölçeklendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358a7-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="358a7-105">`DataGridView` denetimini, uygulamalarınızda özel davranışlar oluşturmak için kullanabileceğiniz çeşitli yollarla genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358a7-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="358a7-106">Örneğin, kendi sıralama algoritmalarınızı programlı bir şekilde belirtebilir ve kendi hücre türlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358a7-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="358a7-107">`DataGridView` denetiminin görünümünü kolayca özelleştirerek birçok özellik arasından seçim yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="358a7-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="358a7-108">Birçok veri deposu türü bir veri kaynağı olarak kullanılabilir veya `DataGridView` denetimi kendisine hiçbir veri kaynağı olmadan çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="358a7-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="358a7-109">Bu bölümdeki konularda, uygulamalarınızda `DataGridView` özellikler oluşturmak için kullanabileceğiniz kavramlar ve teknikler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="358a7-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="358a7-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="358a7-110">In This Section</span></span>  
 [<span data-ttu-id="358a7-111">DataGridView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="358a7-111">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="358a7-112">Windows Forms `DataGridView` denetiminin mimarisini ve temel kavramlarını tanımlayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="358a7-113">Windows Forms DataGridView Denetimindeki Varsayılan İşlevler</span><span class="sxs-lookup"><span data-stu-id="358a7-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="358a7-114">Bir veri kaynağına bağlandığında Windows Forms `DataGridView` denetiminin varsayılan görünümünü ve davranışını açıklar.</span><span class="sxs-lookup"><span data-stu-id="358a7-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="358a7-115">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="358a7-115">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="358a7-116">Verileri göstermek ve kullanıcıların verileri değiştirmesine veya eklemesine izin vermek için kullanılan Windows Forms `DataGridView` denetimindeki sütun türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="358a7-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="358a7-117">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="358a7-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="358a7-118">Yaygın olarak kullanılan hücre, satır ve sütun özelliklerini tanımlayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="358a7-119">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="358a7-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="358a7-120">Denetimin temel görünümünün ve hücre verilerinin görüntüleme biçimlendirmesinin nasıl değiştirileceğini betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="358a7-121">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="358a7-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="358a7-122">Denetimin verileri el ile veya dış veri kaynağından nasıl doldurulacağını betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="358a7-123">Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="358a7-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="358a7-124">Satır ve sütun boyutunun, hücre içeriğinin sığması veya denetimin kullanılabilir genişliğine sığması için otomatik olarak nasıl ayarlanacağını betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="358a7-125">Windows Forms DataGridView Denetimindeki Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="358a7-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="358a7-126">Denetimdeki sıralama özelliklerini tanımlayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="358a7-127">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="358a7-127">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="358a7-128">Kullanıcıların denetimdeki verileri ekleme ve değiştirme biçimini nasıl değiştireceğiniz hakkında konular sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="358a7-129">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="358a7-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="358a7-130">Denetimdeki hücre, satır ve sütun seçimi özelliklerini tanımlayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="358a7-131">Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="358a7-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="358a7-132">Hücre, satır ve sütun nesneleriyle nasıl program kullanacağınızı betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="358a7-133">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="358a7-133">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="358a7-134">Özel boyama `DataGridView` hücreleri ve satırları tanımlayan ve türetilmiş hücre, sütun ve satır türlerini oluşturan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="358a7-135">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="358a7-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="358a7-136">Büyük miktarlarda verilerle çalışırken performans sorunlarından kaçınmak için denetimin etkili bir şekilde nasıl kullanılacağını betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="358a7-137">Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı</span><span class="sxs-lookup"><span data-stu-id="358a7-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="358a7-138">Kullanıcıların klavye ve fare aracılığıyla `DataGridView` denetimiyle nasıl etkileşime girebileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="358a7-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="358a7-139">Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="358a7-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="358a7-140">`DataGridView` denetiminin üzerinde nasıl gelişmediğini açıklar ve <xref:System.Windows.Forms.DataGrid> denetimini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="358a7-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="358a7-141">Ayrıca bkz. [tasarımcı Windows Forms DataGridView denetimiyle kullanımı](using-the-designer-with-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="358a7-141">Also see [Using the Designer with the Windows Forms DataGridView Control](using-the-designer-with-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="358a7-142">Başvuru</span><span class="sxs-lookup"><span data-stu-id="358a7-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="358a7-143"><xref:System.Windows.Forms.DataGridView> denetimi için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="358a7-144"><xref:System.Windows.Forms.BindingSource> bileşeni için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="358a7-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="358a7-145"><xref:System.Windows.Forms.DataGridView> denetimi ve <xref:System.Windows.Forms.BindingSource> bileşeni, birbirine yakın şekilde çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="358a7-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358a7-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="358a7-146">See also</span></span>

- [<span data-ttu-id="358a7-147">Windows Forms'da Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="358a7-147">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
