---
title: DataGrid Denetimi (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
ms.openlocfilehash: 5a69605901eef7366c7a9ff9930e5f4ec6cece23
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65878769"
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="582bd-102">DataGrid Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="582bd-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="582bd-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler `DataGrid` denetler; ancak, `DataGrid` denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="582bd-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="582bd-104">Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="582bd-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="582bd-105">Windows Forms `DataGrid` denetim tablosal verileri görüntüleme ve etkinleştirme güncelleştirmeleri veri kaynağına ADO.NET veri kümeleri, bir kullanıcı arabirimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="582bd-105">The Windows Forms `DataGrid` control provides a user interface to ADO.NET datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="582bd-106">Zaman `DataGrid` denetimi, geçerli bir veri kaynağı için ayarlandığında, sütunları ve satırları şeklindeki veri temel oluşturma, denetim otomatik olarak doldurulur.</span><span class="sxs-lookup"><span data-stu-id="582bd-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="582bd-107">`DataGrid` Denetimi, tek bir tablo veya tablo kümesini arasındaki hiyerarşik ilişkileri görüntülemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="582bd-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="582bd-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="582bd-108">In This Section</span></span>  
 [<span data-ttu-id="582bd-109">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="582bd-109">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="582bd-110">Temel özellikleri açıklanmıştır `DataGrid` denetimi.</span><span class="sxs-lookup"><span data-stu-id="582bd-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="582bd-111">Nasıl yapılır: Windows Forms DataGrid Tasarımcısı'nı kullanarak denetimine tablolar ve sütunlar ekleme</span><span class="sxs-lookup"><span data-stu-id="582bd-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="582bd-112">Tablolar ve sütunlar ekleme işlemi açıklanmaktadır `DataGrid` Tasarımcısı'nı kullanarak denetim.</span><span class="sxs-lookup"><span data-stu-id="582bd-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="582bd-113">Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme</span><span class="sxs-lookup"><span data-stu-id="582bd-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="582bd-114">Tablolar ve sütunlar ekleme işlemi açıklanmaktadır `DataGrid` programlı olarak denetleme.</span><span class="sxs-lookup"><span data-stu-id="582bd-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="582bd-115">Nasıl yapılır: Windows Forms DataGrid denetimi Tasarımcısı'nı kullanarak bir veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="582bd-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="582bd-116">Bir ADO.NET veri kümesi için bağlama işlemini açıklamaktadır `DataGrid` Tasarımcısı'nı kullanarak denetim.</span><span class="sxs-lookup"><span data-stu-id="582bd-116">Describes how to bind an ADO.NET dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="582bd-117">Nasıl yapılır: Windows Forms DataGrid denetimini veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="582bd-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="582bd-118">Bir ADO.NET veri kümesi için bağlama işlemini açıklamaktadır `DataGrid` denetimi.</span><span class="sxs-lookup"><span data-stu-id="582bd-118">Describes how to bind an ADO.NET dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="582bd-119">Nasıl yapılır: Windows Forms DataGrid denetiminde çalışma zamanında görüntülenen verileri değiştirme</span><span class="sxs-lookup"><span data-stu-id="582bd-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="582bd-120">Program verilerin nasıl değiştirilebileceğini açıklar `DataGrid` denetimi.</span><span class="sxs-lookup"><span data-stu-id="582bd-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="582bd-121">Nasıl yapılır: Windows Forms Tasarımcısı'nı kullanarak DataGrid denetimi ile ana-Ayrıntılar listeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="582bd-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="582bd-122">İki tablo, iki ayrı bir üst/alt ilişkisi birlikte bağlı görüntülenecek açıklar `DataGrid` Tasarımcısı'nı kullanarak denetler.</span><span class="sxs-lookup"><span data-stu-id="582bd-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="582bd-123">Nasıl yapılır: Windows Forms DataGrid denetimi ile ana-Ayrıntılar listeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="582bd-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="582bd-124">İki tablo, iki ayrı bir üst/alt ilişkisi birlikte bağlı görüntülenecek açıklar `DataGrid` kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="582bd-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="582bd-125">Nasıl yapılır: Silme veya Windows Forms DataGrid denetiminde sütunları gizleme</span><span class="sxs-lookup"><span data-stu-id="582bd-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="582bd-126">Sütunları kaldırmayı açıklar `DataGrid` denetimi.</span><span class="sxs-lookup"><span data-stu-id="582bd-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="582bd-127">Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGrid denetimini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="582bd-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="582bd-128">Görünüm ilgili özelliklerini değiştirmek açıklar `DataGrid` Tasarımcısı'nı kullanarak denetim.</span><span class="sxs-lookup"><span data-stu-id="582bd-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="582bd-129">Nasıl yapılır: Windows Forms DataGrid denetimini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="582bd-129">How to: Format the Windows Forms DataGrid Control</span></span>](how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="582bd-130">Görünüm ilgili özelliklerini değiştirmek açıklar `DataGrid` denetimi.</span><span class="sxs-lookup"><span data-stu-id="582bd-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="582bd-131">Windows Forms DataGrid Denetimi için Klavye Kısayolları</span><span class="sxs-lookup"><span data-stu-id="582bd-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="582bd-132">Metinde gezinme kısayolları listeler `DataGrid` denetimi.</span><span class="sxs-lookup"><span data-stu-id="582bd-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="582bd-133">Nasıl yapılır: Windows Forms DataGrid denetiminde Tıklamalara yanıt verme</span><span class="sxs-lookup"><span data-stu-id="582bd-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="582bd-134">Bir kullanıcının hangi hücresi içinde tıklamıştır olmadığının nasıl belireneceğini açıklar `DataGrid` denetimi.</span><span class="sxs-lookup"><span data-stu-id="582bd-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="582bd-135">Nasıl yapılır: Windows Forms DataGrid denetimiyle girişi doğrulama</span><span class="sxs-lookup"><span data-stu-id="582bd-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="582bd-136">Bağlı veri girişi doğrulama açıklar `DataGrid` denetimi.</span><span class="sxs-lookup"><span data-stu-id="582bd-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="582bd-137">Başvuru</span><span class="sxs-lookup"><span data-stu-id="582bd-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="582bd-138">Genel bir bakış sağlar <xref:System.Windows.Forms.DataGrid> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="582bd-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="582bd-139">Bağlamak için bu özelliği kullanmayla ilgili ayrıntıları sağlayan <xref:System.Windows.Forms.DataGrid> veri denetimi.</span><span class="sxs-lookup"><span data-stu-id="582bd-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="582bd-140">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="582bd-140">Related Sections</span></span>  
 [<span data-ttu-id="582bd-141">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="582bd-141">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="582bd-142">Windows Forms veri bağlama konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="582bd-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="582bd-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="582bd-143">See also</span></span>

- [<span data-ttu-id="582bd-144">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="582bd-144">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="582bd-145">Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="582bd-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
