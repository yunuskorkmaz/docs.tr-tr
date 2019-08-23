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
ms.openlocfilehash: f50f32ad65dd621dee3847d72b5a186afcc4a86d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969155"
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="336cd-102">DataGrid Denetimi (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="336cd-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="336cd-103">Denetim yerini alır ve `DataGrid` `DataGrid` denetime işlevsellik ekler; ancak, isterseniz denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="336cd-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="336cd-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="336cd-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="336cd-105">Windows Forms `DataGrid` denetim, ADO.NET veri kümelerine bir kullanıcı arabirimi sağlar, tablo verilerini görüntüler ve veri kaynağında güncelleştirmeleri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="336cd-105">The Windows Forms `DataGrid` control provides a user interface to ADO.NET datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="336cd-106">`DataGrid` Denetim geçerli bir veri kaynağına ayarlandığında, denetim otomatik olarak doldurulur ve verilerin şekline göre sütunlar ve satırlar oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="336cd-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="336cd-107">Denetim `DataGrid` , bir tablo kümesi arasındaki tek bir tabloyu ya da hiyerarşik ilişkileri göstermek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="336cd-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="336cd-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="336cd-108">In This Section</span></span>  
 [<span data-ttu-id="336cd-109">DataGrid Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="336cd-109">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="336cd-110">`DataGrid` Denetimin temel özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="336cd-111">Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme</span><span class="sxs-lookup"><span data-stu-id="336cd-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="336cd-112">Tasarımcı kullanılarak `DataGrid` denetime nasıl tablo ve sütun ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="336cd-113">Nasıl yapılır: Windows Forms DataGrid denetimine tablolar ve sütunlar ekleme</span><span class="sxs-lookup"><span data-stu-id="336cd-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="336cd-114">`DataGrid` Denetime program aracılığıyla nasıl tablo ve sütun ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="336cd-115">Nasıl yapılır: Tasarımcı kullanarak Windows Forms DataGrid denetimini bir veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="336cd-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="336cd-116">ADO.NET veri kümesinin `DataGrid` Tasarımcıyı kullanarak denetime nasıl bağlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-116">Describes how to bind an ADO.NET dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="336cd-117">Nasıl yapılır: Windows Forms DataGrid denetimini bir veri kaynağına bağlama</span><span class="sxs-lookup"><span data-stu-id="336cd-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="336cd-118">Bir ADO.NET veri kümesinin `DataGrid` denetime nasıl bağlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-118">Describes how to bind an ADO.NET dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="336cd-119">Nasıl yapılır: Windows Forms DataGrid denetimindeki çalışma zamanında görünen verileri değiştirme</span><span class="sxs-lookup"><span data-stu-id="336cd-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="336cd-120">`DataGrid` Denetimdeki verilerin programlı olarak nasıl değiştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="336cd-121">Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGrid denetimiyle ana ayrıntılar listesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="336cd-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="336cd-122">Bir üst/alt ilişkisiyle birbirine bağlı iki tablonun, Tasarımcıyı kullanarak iki ayrı `DataGrid` denetime nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="336cd-123">Nasıl yapılır: Windows Forms DataGrid denetimiyle ana ayrıntılar listesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="336cd-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="336cd-124">İki ayrı `DataGrid` denetimin üst/alt ilişkisiyle birbirine bağlı iki tablonun nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="336cd-125">Nasıl yapılır: Windows Forms DataGrid denetimindeki sütunları silme veya gizleme</span><span class="sxs-lookup"><span data-stu-id="336cd-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="336cd-126">`DataGrid` Denetimdeki sütunların nasıl kaldırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="336cd-127">Nasıl yapılır: Tasarımcıyı kullanarak Windows Forms DataGrid denetimini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="336cd-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="336cd-128">Tasarımcı kullanarak `DataGrid` denetimin ilişkili özelliklerinin nasıl değiştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="336cd-129">Nasıl yapılır: Windows Forms DataGrid denetimini biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="336cd-129">How to: Format the Windows Forms DataGrid Control</span></span>](how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="336cd-130">`DataGrid` Denetimin görünümle ilgili özelliklerinin nasıl değiştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="336cd-131">Windows Forms DataGrid Denetimi için Klavye Kısayolları</span><span class="sxs-lookup"><span data-stu-id="336cd-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="336cd-132">`DataGrid` Denetimde gezinmek için kısayolları listeler.</span><span class="sxs-lookup"><span data-stu-id="336cd-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="336cd-133">Nasıl yapılır: Windows Forms DataGrid denetimindeki tıklamalarına yanıt verme</span><span class="sxs-lookup"><span data-stu-id="336cd-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="336cd-134">Kullanıcının `DataGrid` denetimde tıklamış olduğu hücreyi nasıl belirleyebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="336cd-135">Nasıl yapılır: Windows Forms DataGrid denetimiyle girişi doğrulama</span><span class="sxs-lookup"><span data-stu-id="336cd-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="336cd-136">`DataGrid` Denetime bağlanacak veri kümesindeki girişin nasıl doğrulanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="336cd-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="336cd-137">Başvuru</span><span class="sxs-lookup"><span data-stu-id="336cd-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="336cd-138"><xref:System.Windows.Forms.DataGrid> Sınıfına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="336cd-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="336cd-139"><xref:System.Windows.Forms.DataGrid> Denetimi verilere bağlamak için bu özelliği kullanma hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="336cd-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="336cd-140">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="336cd-140">Related Sections</span></span>  
 [<span data-ttu-id="336cd-141">Windows Forms Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="336cd-141">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="336cd-142">Windows Forms veri bağlama hakkındaki konuların bağlantılarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="336cd-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="336cd-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="336cd-143">See also</span></span>

- [<span data-ttu-id="336cd-144">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="336cd-144">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="336cd-145">Windows Forms DataGridView ve DataGrid Denetimleri Arasındaki Farklar</span><span class="sxs-lookup"><span data-stu-id="336cd-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
