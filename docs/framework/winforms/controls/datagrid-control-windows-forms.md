---
title: DataGrid Denetimi (Windows Forms)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c60927451ad4350ef507f2e2a661bcfaab4ea788
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="5d359-102">DataGrid Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="5d359-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="5d359-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler `DataGrid` kontrol; ancak, `DataGrid` denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="5d359-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="5d359-104">Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="5d359-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="5d359-105">Windows Forms `DataGrid` denetimi için kullanıcı arabirimi sağlar [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] tablo verilerini görüntüleme ve etkinleştirme veri kümeleri, veri kaynağına güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="5d359-105">The Windows Forms `DataGrid` control provides a user interface to [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="5d359-106">Zaman `DataGrid` denetimi geçerli bir veri kaynağı için ayarlandığında, sütunları ve satırları veri şekli hakkında temel oluşturma, denetimi otomatik olarak doldurulur.</span><span class="sxs-lookup"><span data-stu-id="5d359-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="5d359-107">`DataGrid` Denetimi, tek bir tablo veya tablo kümesini arasındaki hiyerarşik ilişkiyi görüntülemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5d359-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5d359-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="5d359-108">In This Section</span></span>  
 [<span data-ttu-id="5d359-109">DataGrid denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="5d359-109">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="5d359-110">Temel özelliklerini açıklar `DataGrid` denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5d359-111">Nasıl yapılır: tabloları ekleyebilir ve sütunları Windows Forms DataGrid denetiminde Tasarımcısı'nı kullanarak</span><span class="sxs-lookup"><span data-stu-id="5d359-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="5d359-112">Tablolar ve sütunlar ekleme işlemi açıklanmaktadır `DataGrid` Tasarımcısı'nı kullanarak denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="5d359-113">Nasıl yapılır: tabloları ekleyebilir ve sütunları Windows Forms DataGrid denetimi</span><span class="sxs-lookup"><span data-stu-id="5d359-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5d359-114">Tablolar ve sütunlar ekleme işlemi açıklanmaktadır `DataGrid` programlı olarak denetleme.</span><span class="sxs-lookup"><span data-stu-id="5d359-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="5d359-115">Nasıl yapılır: Windows Forms DataGrid denetimini Tasarımcısı'nı kullanarak bir veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="5d359-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="5d359-116">' E nasıl bağlanacağını açıklar bir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset `DataGrid` Tasarımcısı'nı kullanarak denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-116">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="5d359-117">Nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="5d359-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="5d359-118">' E nasıl bağlanacağını açıklar bir [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset `DataGrid` denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-118">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5d359-119">Nasıl yapılır: Windows Forms DataGrid denetiminde çalışma zamanında değiştirme görüntülenen verileri</span><span class="sxs-lookup"><span data-stu-id="5d359-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="5d359-120">Program aracılığıyla da verilerin nasıl değiştirilebileceğini açıklar `DataGrid` denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5d359-121">Nasıl yapılır: Windows Forms DataGrid Tasarımcısı'nı kullanarak denetimi ile ana Ayrıntılar listeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="5d359-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="5d359-122">İki ayrı bir üst/alt ilişkisi birlikte bağlı iki tablo görüntülenecek açıklar `DataGrid` Tasarımcısı'nı kullanarak denetler.</span><span class="sxs-lookup"><span data-stu-id="5d359-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="5d359-123">Nasıl yapılır: Windows Forms DataGrid denetimi ile ana Ayrıntılar listeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="5d359-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="5d359-124">İki ayrı bir üst/alt ilişkisi birlikte bağlı iki tablo görüntülenecek açıklar `DataGrid` kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="5d359-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="5d359-125">Nasıl yapılır: sütunları silme veya gizleme Windows Forms DataGrid denetimi</span><span class="sxs-lookup"><span data-stu-id="5d359-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5d359-126">Sütun kaldırmayı açıklar `DataGrid` denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5d359-127">Nasıl yapılır: Tasarımcı kullanarak Windows Formları DataGrid denetimini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="5d359-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="5d359-128">Görünüm ilgili özelliklerini değiştirmek açıklar `DataGrid` Tasarımcısı'nı kullanarak denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="5d359-129">Nasıl yapılır: Windows Forms DataGrid denetimini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="5d359-129">How to: Format the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5d359-130">Görünüm ilgili özelliklerini değiştirmek açıklar `DataGrid` denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5d359-131">Windows Forms DataGrid denetimi için klavye kısayolları</span><span class="sxs-lookup"><span data-stu-id="5d359-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5d359-132">Listeler gezinme için kısayolları `DataGrid` denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5d359-133">Nasıl yapılır: Windows Forms DataGrid denetiminde tıklamalarına yanıt</span><span class="sxs-lookup"><span data-stu-id="5d359-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5d359-134">Bir kullanıcının hangi hücrenin içinde tıklamıştır belirlemek açıklar `DataGrid` denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="5d359-135">Nasıl yapılır: Windows Forms DataGrid denetimiyle girişi doğrulama</span><span class="sxs-lookup"><span data-stu-id="5d359-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="5d359-136">Bağlı veri kümesi girişinde doğrulamak açıklar `DataGrid` denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5d359-137">Başvuru</span><span class="sxs-lookup"><span data-stu-id="5d359-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="5d359-138">Genel bir bakış sağlar <xref:System.Windows.Forms.DataGrid> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="5d359-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="5d359-139">Bağlamak için bu özelliği kullanma hakkında ayrıntılı bilgi sağlar <xref:System.Windows.Forms.DataGrid> verilere denetim.</span><span class="sxs-lookup"><span data-stu-id="5d359-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5d359-140">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="5d359-140">Related Sections</span></span>  
 [<span data-ttu-id="5d359-141">Windows Forms veri bağlama</span><span class="sxs-lookup"><span data-stu-id="5d359-141">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="5d359-142">Windows Forms veri bağlama konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="5d359-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d359-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5d359-143">See Also</span></span>  
 [<span data-ttu-id="5d359-144">DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="5d359-144">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="5d359-145">Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="5d359-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
