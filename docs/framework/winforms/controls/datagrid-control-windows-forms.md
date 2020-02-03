---
title: DataGrid Denetimi
ms.date: 03/30/2017
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
ms.openlocfilehash: efcc8770232f657c13135cefb4027f814d4d7d19
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742521"
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="e5bcf-102">DataGrid Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e5bcf-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="e5bcf-103"><xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve `DataGrid` denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, `DataGrid` denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="e5bcf-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e5bcf-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="e5bcf-105">Windows Forms `DataGrid` denetimi bir kullanıcı arabirimini ADO.NET veri kümelerine, tablo verilerinin görüntülenmesini ve veri kaynağında yapılan güncelleştirmeleri etkinleştirmeyi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-105">The Windows Forms `DataGrid` control provides a user interface to ADO.NET datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="e5bcf-106">`DataGrid` denetimi geçerli bir veri kaynağına ayarlandığında, denetim otomatik olarak doldurulur, veri şekline göre sütunlar ve satırlar oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="e5bcf-107">`DataGrid` denetimi bir tablo kümesi arasındaki tek bir tabloyu ya da hiyerarşik ilişkileri göstermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5bcf-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e5bcf-108">In This Section</span></span>  
 [<span data-ttu-id="e5bcf-109">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e5bcf-109">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="e5bcf-110">`DataGrid` denetiminin temel özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="e5bcf-111">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimine Tablolar ve Sütunlar Ekleme</span><span class="sxs-lookup"><span data-stu-id="e5bcf-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="e5bcf-112">Tasarımcıyı kullanarak `DataGrid` denetimine nasıl tablo ve sütun ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="e5bcf-113">Nasıl yapılır: Windows Forms DataGrid Denetimine Tablo ve Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="e5bcf-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="e5bcf-114">`DataGrid` denetimine program aracılığıyla nasıl tablo ve sütun ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="e5bcf-115">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="e5bcf-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="e5bcf-116">Tasarımcı kullanarak bir ADO.NET veri kümesinin `DataGrid` denetimine nasıl bağlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-116">Describes how to bind an ADO.NET dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="e5bcf-117">Nasıl yapılır: Windows Forms DataGrid Denetimini Veri Kaynağına Bağlama</span><span class="sxs-lookup"><span data-stu-id="e5bcf-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="e5bcf-118">Bir ADO.NET veri kümesinin `DataGrid` denetimine nasıl bağlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-118">Describes how to bind an ADO.NET dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="e5bcf-119">Nasıl yapılır: Windows Forms DataGrid Denetiminde Çalışma Zamanında Görüntülenen Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="e5bcf-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="e5bcf-120">`DataGrid` denetimindeki verilerin programlı olarak nasıl değiştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="e5bcf-121">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimi ile Ana-Ayrıntılar Listeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5bcf-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="e5bcf-122">Tasarımcıyı kullanarak iki ayrı `DataGrid` denetimine bir üst/alt ilişkisiyle birbirine bağlanan iki tablonun nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="e5bcf-123">Nasıl yapılır: Windows Forms DataGrid denetimiyle ana Ayrıntılar listeleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="e5bcf-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="e5bcf-124">İki ayrı `DataGrid` denetiminde, üst/alt ilişkisiyle birbirine bağlı iki tablonun nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="e5bcf-125">Nasıl yapılır: Windows Forms DataGrid Denetiminde Sütunları Silme veya Gizleme</span><span class="sxs-lookup"><span data-stu-id="e5bcf-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="e5bcf-126">`DataGrid` denetimindeki sütunların nasıl kaldırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="e5bcf-127">Nasıl yapılır: Tasarımcı Kullanarak Windows Forms DataGrid Denetimini Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e5bcf-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="e5bcf-128">Tasarımcı kullanarak `DataGrid` denetiminin görünümle ilgili özelliklerinin nasıl değiştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="e5bcf-129">Nasıl yapılır: Windows Forms DataGrid Denetimini Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="e5bcf-129">How to: Format the Windows Forms DataGrid Control</span></span>](how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="e5bcf-130">`DataGrid` denetiminin görünümle ilgili özelliklerinin nasıl değiştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="e5bcf-131">Windows Forms DataGrid Denetimi için Klavye Kısayolları</span><span class="sxs-lookup"><span data-stu-id="e5bcf-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="e5bcf-132">`DataGrid` denetiminde gezinmek için kısayolları listeler.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="e5bcf-133">Nasıl yapılır: Windows Forms DataGrid Denetiminde Tıklamalara Yanıt Verme</span><span class="sxs-lookup"><span data-stu-id="e5bcf-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="e5bcf-134">Kullanıcının `DataGrid` denetiminde tıklamış olduğu hücreyi nasıl belirleyebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="e5bcf-135">Nasıl yapılır: Windows Forms DataGrid Denetimiyle Girişi Doğrulama</span><span class="sxs-lookup"><span data-stu-id="e5bcf-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="e5bcf-136">`DataGrid` denetimine bağlantılı veri kümesindeki girişin nasıl doğrulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e5bcf-137">Başvuru</span><span class="sxs-lookup"><span data-stu-id="e5bcf-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="e5bcf-138"><xref:System.Windows.Forms.DataGrid> sınıfına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="e5bcf-139"><xref:System.Windows.Forms.DataGrid> denetimini verilere bağlamak için bu özelliği kullanma hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e5bcf-140">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e5bcf-140">Related Sections</span></span>  
 [<span data-ttu-id="e5bcf-141">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="e5bcf-141">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="e5bcf-142">Windows Forms veri bağlama hakkındaki konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5bcf-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5bcf-143">See also</span></span>

- [<span data-ttu-id="e5bcf-144">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="e5bcf-144">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="e5bcf-145">Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="e5bcf-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
