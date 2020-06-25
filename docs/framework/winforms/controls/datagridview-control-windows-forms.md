---
title: DataGridView Denetimi
description: Daha `DataGridView` az miktarda verinin salt okunurdur görünümlerini göstermek için denetimi kullanmayı veya çok büyük veri kümelerinin düzenlenebilir görünümlerini göstermek üzere ölçeklendirmeyi öğrenin.
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
ms.openlocfilehash: f9a45e8be7975697ca5c0d019c6bc4119f562aea
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325896"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="6ba09-103">DataGridView Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6ba09-103">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="6ba09-104">`DataGridView`Denetim, verileri tablolu biçimde görüntülemenin güçlü ve esnek bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-104">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="6ba09-105">Daha `DataGridView` az miktarda verinin salt okunurdur görünümlerini göstermek için denetimini kullanabilir veya çok büyük veri kümelerinin düzenlenebilir görünümlerini göstermek üzere ölçeklendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba09-105">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="6ba09-106">`DataGridView`Uygulamanızda özel davranışlar oluşturmak için, denetimi çeşitli yollarla genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba09-106">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="6ba09-107">Örneğin, kendi sıralama algoritmalarınızı programlı bir şekilde belirtebilir ve kendi hücre türlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba09-107">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="6ba09-108">`DataGridView`Birçok özellik arasından seçim yaparak denetimin görünümünü kolayca özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ba09-108">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="6ba09-109">Birçok veri deposu türü bir veri kaynağı olarak kullanılabilir veya `DataGridView` Denetim, hiçbir veri kaynağı ile bağlantılı olmadan çalışabilir.</span><span class="sxs-lookup"><span data-stu-id="6ba09-109">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="6ba09-110">Bu bölümdeki konularda, uygulamalarınızda özellik oluşturmak için kullanabileceğiniz kavramlar ve teknikler açıklanır `DataGridView` .</span><span class="sxs-lookup"><span data-stu-id="6ba09-110">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ba09-111">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6ba09-111">In This Section</span></span>  
 [<span data-ttu-id="6ba09-112">DataGridView Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6ba09-112">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="6ba09-113">Windows Forms denetiminin mimarisini ve temel kavramlarını tanımlayan konuları sağlar `DataGridView` .</span><span class="sxs-lookup"><span data-stu-id="6ba09-113">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="6ba09-114">Windows Forms DataGridView Denetimindeki Varsayılan İşlevler</span><span class="sxs-lookup"><span data-stu-id="6ba09-114">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ba09-115">Bir veri kaynağına bağlandığında Windows Forms denetiminin varsayılan görünümünü ve davranışını açıklar `DataGridView` .</span><span class="sxs-lookup"><span data-stu-id="6ba09-115">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="6ba09-116">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="6ba09-116">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ba09-117">`DataGridView`Verileri göstermek ve kullanıcıların verileri değiştirmesine veya eklemesine izin vermek için kullanılan Windows Forms denetimindeki sütun türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-117">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="6ba09-118">Windows Forms DataGridView Denetimindeki Temel Sütun, Satır ve Hücre Özellikleri</span><span class="sxs-lookup"><span data-stu-id="6ba09-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="6ba09-119">Yaygın olarak kullanılan hücre, satır ve sütun özelliklerini tanımlayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-119">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="6ba09-120">Windows Forms DataGridView Denetimindeki Temel Biçim ve Stiller</span><span class="sxs-lookup"><span data-stu-id="6ba09-120">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ba09-121">Denetimin temel görünümünün ve hücre verilerinin görüntüleme biçimlendirmesinin nasıl değiştirileceğini betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-121">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="6ba09-122">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="6ba09-122">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ba09-123">Denetimin verileri el ile veya dış veri kaynağından nasıl doldurulacağını betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-123">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="6ba09-124">Windows Forms DataGridView Denetiminde Hücre ve Satırları Yeniden Boyutlandırma</span><span class="sxs-lookup"><span data-stu-id="6ba09-124">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ba09-125">Satır ve sütun boyutunun, hücre içeriğinin sığması veya denetimin kullanılabilir genişliğine sığması için otomatik olarak nasıl ayarlanacağını betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-125">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="6ba09-126">Windows Forms DataGridView Denetimindeki Verileri Sıralama</span><span class="sxs-lookup"><span data-stu-id="6ba09-126">Sorting Data in the Windows Forms DataGridView Control</span></span>](sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ba09-127">Denetimdeki sıralama özelliklerini tanımlayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-127">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="6ba09-128">Windows Forms DataGridView Denetimindeki Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="6ba09-128">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ba09-129">Kullanıcıların denetimdeki verileri ekleme ve değiştirme biçimini nasıl değiştireceğiniz hakkında konular sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-129">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="6ba09-130">Windows Forms DataGridView Denetimi ile Seçim ve Pano Kullanımı</span><span class="sxs-lookup"><span data-stu-id="6ba09-130">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ba09-131">Denetimdeki hücre, satır ve sütun seçimi özelliklerini tanımlayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-131">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="6ba09-132">Windows Forms DataGridView Denetiminde Hücreler, Satırlar ve Sütunlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="6ba09-132">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="6ba09-133">Hücre, satır ve sütun nesneleriyle nasıl program kullanacağınızı betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-133">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="6ba09-134">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6ba09-134">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ba09-135">Özel boyama `DataGridView` hücrelerini ve satırları betimleyen ve türetilmiş hücre, sütun ve satır türleri oluşturan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-135">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="6ba09-136">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="6ba09-136">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ba09-137">Büyük miktarlarda verilerle çalışırken performans sorunlarından kaçınmak için denetimin etkili bir şekilde nasıl kullanılacağını betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ba09-137">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="6ba09-138">Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı</span><span class="sxs-lookup"><span data-stu-id="6ba09-138">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ba09-139">Kullanıcıların `DataGridView` klavye ve fare aracılığıyla denetimle nasıl etkileşime girebileceği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6ba09-139">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="6ba09-140">Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="6ba09-140">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="6ba09-141">`DataGridView`Denetimin üzerinde nasıl gelişmediğini ve denetimin yerini aldığını açıklar <xref:System.Windows.Forms.DataGrid> .</span><span class="sxs-lookup"><span data-stu-id="6ba09-141">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="6ba09-142">Ayrıca bkz. [tasarımcı Windows Forms DataGridView denetimiyle kullanımı](using-the-designer-with-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6ba09-142">Also see [Using the Designer with the Windows Forms DataGridView Control](using-the-designer-with-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="6ba09-143">Başvuru</span><span class="sxs-lookup"><span data-stu-id="6ba09-143">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="6ba09-144">Denetim için başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> .</span><span class="sxs-lookup"><span data-stu-id="6ba09-144">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="6ba09-145">Bileşen için başvuru belgeleri sağlar <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="6ba09-145">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="6ba09-146"><xref:System.Windows.Forms.DataGridView>Denetim ve bileşen, <xref:System.Windows.Forms.BindingSource> birbirine yakın şekilde çalışacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="6ba09-146">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ba09-147">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ba09-147">See also</span></span>

- [<span data-ttu-id="6ba09-148">Windows Forms'ta Kullanılacak Denetimler</span><span class="sxs-lookup"><span data-stu-id="6ba09-148">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
