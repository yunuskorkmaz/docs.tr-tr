---
title: "DataGridView Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6d9cc6568813af866acaf20696b870bedc3099be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="9b5f3-102">DataGridView Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="9b5f3-102">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="9b5f3-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.DataGrid> kontrol; ancak, <xref:System.Windows.Forms.DataGrid> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="9b5f3-104">Daha fazla bilgi için bkz: [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="9b5f3-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="9b5f3-105">İle <xref:System.Windows.Forms.DataGridView> denetimi görüntülemek ve birçok farklı türde veri kaynaklarını tablo verileri düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-105">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="9b5f3-106">Veri bağlama <xref:System.Windows.Forms.DataGridView> denetimidir basit ve sezgisel ve çoğu durumda ayarı olarak kadar basit hale <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-106">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="9b5f3-107">Birden çok listeleri veya tablo içeren bir veri kaynağına bağlama ayarlanmadığında <xref:System.Windows.Forms.DataGridView.DataMember%2A> liste veya bağlamak için tabloyu belirten bir dize özelliği.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-107">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="9b5f3-108"><xref:System.Windows.Forms.DataGridView> Denetimi, aşağıdaki listede açıklanan sınıfların örnekleri bağlamak için standart Windows Forms veri bağlama modelini destekler:</span><span class="sxs-lookup"><span data-stu-id="9b5f3-108">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
-   <span data-ttu-id="9b5f3-109">Uygulayan herhangi bir sınıf <xref:System.Collections.IList> tek boyutlu diziler dahil olmak üzere arabirimi.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-109">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="9b5f3-110">Uygulayan herhangi bir sınıf <xref:System.ComponentModel.IListSource> gibi arabirim <xref:System.Data.DataTable> ve <xref:System.Data.DataSet> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-110">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
-   <span data-ttu-id="9b5f3-111">Uygulayan herhangi bir sınıf <xref:System.ComponentModel.IBindingList> gibi arabirim <xref:System.ComponentModel.BindingList%601> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-111">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
-   <span data-ttu-id="9b5f3-112">Uygulayan herhangi bir sınıf <xref:System.ComponentModel.IBindingListView> gibi arabirim <xref:System.Windows.Forms.BindingSource> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-112">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="9b5f3-113"><xref:System.Windows.Forms.DataGridView> Denetimi veri bağlamasını bu arabirimleri tarafından döndürülen nesne genel özelliklerine veya tarafından döndürülen özellikleri koleksiyonuna destekler bir <xref:System.ComponentModel.ICustomTypeDescriptor> , döndürülen nesnelerin uygulanırsa, arabirim.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-113">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="9b5f3-114">Genellikle, bağlayacaksınız bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bağ <xref:System.Windows.Forms.BindingSource> başka bir bileşen veri kaynağı veya iş nesneleri ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-114">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="9b5f3-115"><xref:System.Windows.Forms.BindingSource> Bileşeni olduğundan tercih edilen veri kaynağı çok çeşitli veri kaynaklarına bağlayabilirsiniz ve birçok veri bağlama sorunları otomatik olarak çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-115">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="9b5f3-116">Daha fazla bilgi için bkz: [BindingSource bileşeni](../../../../docs/framework/winforms/controls/bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="9b5f3-116">For more information, see [BindingSource Component](../../../../docs/framework/winforms/controls/bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="9b5f3-117"><xref:System.Windows.Forms.DataGridView> Denetimi de kullanılabilir *ilişkisiz* moduyla alttaki hiç veri deposu.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-117">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="9b5f3-118">İlişkisiz bir kullanan bir kod örneği için <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [izlenecek yol: bağlantısız bir Windows Forms DataGridView denetimi oluşturma](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="9b5f3-118">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="9b5f3-119"><xref:System.Windows.Forms.DataGridView> Denetimidir yüksek oranda yapılandırılabilir ve genişletilebilir ve birçok özellikleri, yöntemleri ve görünümünü ve davranışını özelleştirmek için olayları sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-119">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="9b5f3-120">Tablo verileri görüntülemek için Windows Forms uygulaması istediğinizde kullanmayı <xref:System.Windows.Forms.DataGridView> diğerlerinden önce denetim (örneğin, <xref:System.Windows.Forms.DataGrid>).</span><span class="sxs-lookup"><span data-stu-id="9b5f3-120">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="9b5f3-121">Salt okunur değerlerini oluşan küçük bir kılavuz görüntülüyorsanız veya kayıtları, milyonlarca içeren bir tablo düzenlemek bir kullanıcı etkinleştiriyorsanız <xref:System.Windows.Forms.DataGridView> denetimi, bir yedeğe programlanabilir, bellek verimli çözümüyle sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-121">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9b5f3-122">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9b5f3-122">In This Section</span></span>  
 [<span data-ttu-id="9b5f3-123">DataGridView Denetimi Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="9b5f3-123">DataGridView Control Technology Summary</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="9b5f3-124">Özetler <xref:System.Windows.Forms.DataGridView> kavramları ve ilgili sınıfların kullanımını denetleme.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-124">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="9b5f3-125">DataGridView Denetimi Mimarisi</span><span class="sxs-lookup"><span data-stu-id="9b5f3-125">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="9b5f3-126">Mimarisini açıklar <xref:System.Windows.Forms.DataGridView> türü hiyerarşi ve devralma yapısını açıklayan denetim.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-126">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="9b5f3-127">DataGridView Denetimi Senaryoları</span><span class="sxs-lookup"><span data-stu-id="9b5f3-127">DataGridView Control Scenarios</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="9b5f3-128">En yaygın senaryoları açıklar <xref:System.Windows.Forms.DataGridView> denetimleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-128">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="9b5f3-129">DataGridView Denetimi Kod Dizini</span><span class="sxs-lookup"><span data-stu-id="9b5f3-129">DataGridView Control Code Directory</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="9b5f3-130">Kod örneklerinde çeşitli belgelerine ait bağlantılar sağlanmıştır <xref:System.Windows.Forms.DataGridView> görevler.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-130">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="9b5f3-131">Bu örnekler görev türü tarafından ayrılır.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-131">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9b5f3-132">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9b5f3-132">Related Sections</span></span>  
 [<span data-ttu-id="9b5f3-133">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="9b5f3-133">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9b5f3-134">Windows Forms'ta sütun türleri açıklanmaktadır <xref:System.Windows.Forms.DataGridView> denetim bilgilerini görüntülemek ve değiştirmek veya bilgi eklemek kullanıcılara izin vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-134">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="9b5f3-135">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="9b5f3-135">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9b5f3-136">El ile veya bir dış veri kaynağından veri denetimiyle doldurmak nasıl açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-136">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="9b5f3-137">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="9b5f3-137">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9b5f3-138">Özel boyama açıklayan konulara sağlar <xref:System.Windows.Forms.DataGridView> hücre ve satırları ve oluşturma türetilmiş hücre, sütun ve satır türleri.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-138">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="9b5f3-139">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="9b5f3-139">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9b5f3-140">Denetim verimli bir şekilde büyük miktarlarda veri ile çalışırken, performans sorunlarını önlemek için nasıl kullanılacağını açıklayan konulara sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-140">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b5f3-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9b5f3-141">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="9b5f3-142">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="9b5f3-142">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="9b5f3-143">Windows Forms DataGridView Denetimindeki Varsayılan İşlevler</span><span class="sxs-lookup"><span data-stu-id="9b5f3-143">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="9b5f3-144">Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı</span><span class="sxs-lookup"><span data-stu-id="9b5f3-144">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
