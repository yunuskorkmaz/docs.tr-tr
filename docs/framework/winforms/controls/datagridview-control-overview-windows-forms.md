---
title: DataGridView Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- DataGridView
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
ms.openlocfilehash: 74de5b449525be9ff93fcbef0ddabd041470177c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742487"
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="6ad74-102">DataGridView Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="6ad74-102">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="6ad74-103"><xref:System.Windows.Forms.DataGridView> denetimi yerini alır ve <xref:System.Windows.Forms.DataGrid> denetimine işlevsellik ekler; Ancak, ' yi seçerseniz, <xref:System.Windows.Forms.DataGrid> denetimi hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="6ad74-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="6ad74-104">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6ad74-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="6ad74-105"><xref:System.Windows.Forms.DataGridView> denetimiyle, birçok farklı türdeki veri kaynağından tablo verilerini görüntüleyebilir ve düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6ad74-105">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="6ad74-106"><xref:System.Windows.Forms.DataGridView> denetimine veri bağlama basittir ve sezgisel hale gelir ve çoğu durumda, <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliğini ayarlamak kadar basittir.</span><span class="sxs-lookup"><span data-stu-id="6ad74-106">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="6ad74-107">Birden çok liste veya tablo içeren bir veri kaynağına bağladığınızda <xref:System.Windows.Forms.DataGridView.DataMember%2A> özelliğini, bağlanacak listeyi veya tabloyu belirten bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="6ad74-107">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="6ad74-108"><xref:System.Windows.Forms.DataGridView> denetimi standart Windows Forms veri bağlama modelini destekler, bu nedenle aşağıdaki listede açıklanan sınıfların örneklerine bağlanır:</span><span class="sxs-lookup"><span data-stu-id="6ad74-108">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
- <span data-ttu-id="6ad74-109">Tek boyutlu diziler dahil <xref:System.Collections.IList> arabirimini uygulayan herhangi bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="6ad74-109">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
- <span data-ttu-id="6ad74-110"><xref:System.Data.DataTable> ve <xref:System.Data.DataSet> sınıfları gibi <xref:System.ComponentModel.IListSource> arabirimini uygulayan herhangi bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="6ad74-110">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
- <span data-ttu-id="6ad74-111"><xref:System.ComponentModel.BindingList%601> sınıfı gibi <xref:System.ComponentModel.IBindingList> arabirimini uygulayan herhangi bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="6ad74-111">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
- <span data-ttu-id="6ad74-112"><xref:System.Windows.Forms.BindingSource> sınıfı gibi <xref:System.ComponentModel.IBindingListView> arabirimini uygulayan herhangi bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="6ad74-112">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="6ad74-113"><xref:System.Windows.Forms.DataGridView> denetimi, bu arabirimlerin döndürdüğü nesnelerin ortak özelliklerine veya döndürülen nesneler üzerinde uygulanmışsa bir <xref:System.ComponentModel.ICustomTypeDescriptor> arabirimi tarafından döndürülen özellikler koleksiyonuna veri bağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="6ad74-113">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="6ad74-114">Genellikle, bir <xref:System.Windows.Forms.BindingSource> bileşene bağlanır ve <xref:System.Windows.Forms.BindingSource> bileşenini başka bir veri kaynağına bağlayabilir veya iş nesneleriyle dolduracaksınız.</span><span class="sxs-lookup"><span data-stu-id="6ad74-114">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="6ad74-115"><xref:System.Windows.Forms.BindingSource> bileşeni tercih edilen veri kaynağıdır çünkü çok çeşitli veri kaynaklarına bağlanabilir ve birçok veri bağlama sorununu otomatik olarak çözümleyebilir.</span><span class="sxs-lookup"><span data-stu-id="6ad74-115">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="6ad74-116">Daha fazla bilgi için bkz. [BindingSource bileşeni](bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="6ad74-116">For more information, see [BindingSource Component](bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="6ad74-117"><xref:System.Windows.Forms.DataGridView> denetimi, temel alınan veri deposu olmadan *ilişkisiz* modda da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="6ad74-117">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="6ad74-118">İlişkisiz <xref:System.Windows.Forms.DataGridView> denetimi kullanan bir kod örneği için bkz. [Izlenecek yol: ilişkisiz Windows Forms DataGridView denetimi oluşturma](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="6ad74-118">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="6ad74-119"><xref:System.Windows.Forms.DataGridView> denetimi yüksek oranda yapılandırılabilir ve Genişletilebilir olur ve görünümünü ve davranışını özelleştirmek için birçok özellik, yöntem ve olay sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ad74-119">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="6ad74-120">Windows Forms uygulamanızın tablo verilerini görüntülemesini istediğinizde, başkalarından önce <xref:System.Windows.Forms.DataGridView> denetimini kullanmayı düşünün (örneğin, <xref:System.Windows.Forms.DataGrid>).</span><span class="sxs-lookup"><span data-stu-id="6ad74-120">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="6ad74-121">Salt okunurdur, salt okunurdur veya bir kullanıcının milyonlarca kayıt içeren bir tabloyu düzenlemesini sağladıysanız, <xref:System.Windows.Forms.DataGridView> denetimi size kolayca programlanabilir, bellek açısından verimli bir çözüm sunar.</span><span class="sxs-lookup"><span data-stu-id="6ad74-121">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6ad74-122">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="6ad74-122">In This Section</span></span>  
 [<span data-ttu-id="6ad74-123">DataGridView Denetimi Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="6ad74-123">DataGridView Control Technology Summary</span></span>](datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="6ad74-124"><xref:System.Windows.Forms.DataGridView> denetim kavramlarını ve ilgili sınıfların kullanımını özetler.</span><span class="sxs-lookup"><span data-stu-id="6ad74-124">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="6ad74-125">DataGridView Denetimi Mimarisi</span><span class="sxs-lookup"><span data-stu-id="6ad74-125">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="6ad74-126">Tür hiyerarşisini ve devralma yapısını açıklayan <xref:System.Windows.Forms.DataGridView> denetiminin mimarisini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ad74-126">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="6ad74-127">DataGridView Denetimi Senaryoları</span><span class="sxs-lookup"><span data-stu-id="6ad74-127">DataGridView Control Scenarios</span></span>](datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="6ad74-128"><xref:System.Windows.Forms.DataGridView> denetimlerinin kullanıldığı en yaygın senaryoları açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ad74-128">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="6ad74-129">DataGridView Denetimi Kod Dizini</span><span class="sxs-lookup"><span data-stu-id="6ad74-129">DataGridView Control Code Directory</span></span>](datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="6ad74-130">Çeşitli <xref:System.Windows.Forms.DataGridView> görevleri için belgelerde kod örneklerine bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ad74-130">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="6ad74-131">Bu örnekler, görev türüne göre kategorilere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="6ad74-131">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="6ad74-132">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="6ad74-132">Related Sections</span></span>  
 [<span data-ttu-id="6ad74-133">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="6ad74-133">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ad74-134">Bilgileri göstermek ve kullanıcıların bilgileri değiştirmesine veya eklemesine izin vermek için kullanılan Windows Forms <xref:System.Windows.Forms.DataGridView> denetimindeki sütun türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="6ad74-134">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="6ad74-135">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="6ad74-135">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ad74-136">Denetimin verileri el ile veya dış veri kaynağından nasıl doldurulacağını betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ad74-136">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="6ad74-137">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="6ad74-137">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ad74-138">Özel boyama <xref:System.Windows.Forms.DataGridView> hücreleri ve satırları tanımlayan ve türetilmiş hücre, sütun ve satır türlerini oluşturan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ad74-138">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="6ad74-139">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="6ad74-139">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="6ad74-140">Büyük miktarlarda verilerle çalışırken performans sorunlarından kaçınmak için denetimin etkili bir şekilde nasıl kullanılacağını betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6ad74-140">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad74-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ad74-141">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="6ad74-142">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="6ad74-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="6ad74-143">Windows Forms DataGridView Denetimindeki Varsayılan İşlevler</span><span class="sxs-lookup"><span data-stu-id="6ad74-143">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="6ad74-144">Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı</span><span class="sxs-lookup"><span data-stu-id="6ad74-144">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
