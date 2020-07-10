---
title: DataGridView Denetimine Genel Bakış
description: Birçok farklı türdeki veri kaynağından tablo verilerini göstermek ve düzenlemek için Windows Forms DataGridView denetimini kullanmayı öğrenin.
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
ms.openlocfilehash: 3e68f536853081453f6ba746d342bc016bc8ca17
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174620"
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="38f32-103">DataGridView Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="38f32-103">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="38f32-104"><xref:System.Windows.Forms.DataGridView>Denetim yerini alır ve denetime işlevsellik ekler <xref:System.Windows.Forms.DataGrid> ; ancak, isterseniz <xref:System.Windows.Forms.DataGrid> Denetim hem geri uyumluluk hem de gelecekteki kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="38f32-104">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="38f32-105">Daha fazla bilgi için bkz. [Windows Forms DataGridView ve DataGrid denetimleri arasındaki farklar](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="38f32-105">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="38f32-106"><xref:System.Windows.Forms.DataGridView>Denetimiyle birçok farklı türde veri kaynağından tablo verilerini görüntüleyebilir ve düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="38f32-106">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="38f32-107">Verileri <xref:System.Windows.Forms.DataGridView> denetime bağlama basittir ve sezgisel olur ve çoğu durumda özelliğin ayarlanması kadar basittir <xref:System.Windows.Forms.DataGridView.DataSource%2A> .</span><span class="sxs-lookup"><span data-stu-id="38f32-107">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="38f32-108">Birden çok liste veya tablo içeren bir veri kaynağına bağladığınızda, <xref:System.Windows.Forms.DataGridView.DataMember%2A> özelliği bağlamak için listeyi veya tabloyu belirten bir dizeye ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="38f32-108">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="38f32-109"><xref:System.Windows.Forms.DataGridView>Denetim standart Windows Forms veri bağlama modelini destekler, bu nedenle aşağıdaki listede açıklanan sınıf örneklerine bağlanır:</span><span class="sxs-lookup"><span data-stu-id="38f32-109">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
- <span data-ttu-id="38f32-110"><xref:System.Collections.IList>Tek boyutlu diziler dahil olmak üzere arabirimi uygulayan herhangi bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="38f32-110">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
- <span data-ttu-id="38f32-111">Ve sınıfları gibi arabirimi uygulayan herhangi bir sınıf <xref:System.ComponentModel.IListSource> <xref:System.Data.DataTable> <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="38f32-111">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
- <span data-ttu-id="38f32-112">Sınıfı gibi arabirimi uygulayan herhangi bir sınıf <xref:System.ComponentModel.IBindingList> <xref:System.ComponentModel.BindingList%601> .</span><span class="sxs-lookup"><span data-stu-id="38f32-112">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
- <span data-ttu-id="38f32-113">Sınıfı gibi arabirimi uygulayan herhangi bir sınıf <xref:System.ComponentModel.IBindingListView> <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="38f32-113">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="38f32-114"><xref:System.Windows.Forms.DataGridView>Denetim, bu arabirimlerin döndürdüğü nesnelerin ortak özelliklerine veya <xref:System.ComponentModel.ICustomTypeDescriptor> döndürülen nesneler üzerinde uygulanmışsa bir arabirim tarafından döndürülen özellikler koleksiyonuna veri bağlamayı destekler.</span><span class="sxs-lookup"><span data-stu-id="38f32-114">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="38f32-115">Genellikle, bir <xref:System.Windows.Forms.BindingSource> bileşene bağlanır ve <xref:System.Windows.Forms.BindingSource> bileşeni başka bir veri kaynağına bağlayabilir veya iş nesneleriyle dolduracaksınız.</span><span class="sxs-lookup"><span data-stu-id="38f32-115">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="38f32-116">Çok <xref:System.Windows.Forms.BindingSource> çeşitli veri kaynaklarına bağlanabileceğinden ve birçok veri bağlama sorununu otomatik olarak çözümleyebildiğinden, bileşen tercih edilen veri kaynağıdır.</span><span class="sxs-lookup"><span data-stu-id="38f32-116">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="38f32-117">Daha fazla bilgi için bkz. [BindingSource bileşeni](bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="38f32-117">For more information, see [BindingSource Component](bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="38f32-118"><xref:System.Windows.Forms.DataGridView>Denetim, temel alınan veri deposu olmadan *ilişkisiz* modda da kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="38f32-118">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="38f32-119">İlişkisiz denetim kullanan bir kod örneği için <xref:System.Windows.Forms.DataGridView> bkz. [izlenecek yol: Ilişkisiz Windows Forms DataGridView denetimi oluşturma](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="38f32-119">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="38f32-120"><xref:System.Windows.Forms.DataGridView>Denetim, yüksek oranda yapılandırılabilir ve genişletilebilir ve görünümünü ve davranışını özelleştirmek için birçok özellik, yöntem ve olay sağlar.</span><span class="sxs-lookup"><span data-stu-id="38f32-120">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="38f32-121">Windows Forms uygulamanızın tablo verilerini görüntülemesini istediğinizde, <xref:System.Windows.Forms.DataGridView> denetimi diğerlerinden önce kullanmayı düşünün (örneğin, <xref:System.Windows.Forms.DataGrid> ).</span><span class="sxs-lookup"><span data-stu-id="38f32-121">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="38f32-122">Salt okunurdur, salt okunurdur veya bir kullanıcının milyonlarca kayıt içeren bir tabloyu düzenlemesini <xref:System.Windows.Forms.DataGridView> sağladıysanız, denetim size kolayca programlanabilir, bellek açısından verimli bir çözüm sunar.</span><span class="sxs-lookup"><span data-stu-id="38f32-122">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38f32-123">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="38f32-123">In This Section</span></span>  
 [<span data-ttu-id="38f32-124">DataGridView Denetimi Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="38f32-124">DataGridView Control Technology Summary</span></span>](datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="38f32-125"><xref:System.Windows.Forms.DataGridView>Denetim kavramlarını ve ilgili sınıfların kullanımını özetler.</span><span class="sxs-lookup"><span data-stu-id="38f32-125">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="38f32-126">DataGridView Denetim Mimarisi</span><span class="sxs-lookup"><span data-stu-id="38f32-126">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="38f32-127"><xref:System.Windows.Forms.DataGridView>Tür hiyerarşisini ve devralma yapısını açıklayan denetim mimarisini açıklar.</span><span class="sxs-lookup"><span data-stu-id="38f32-127">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="38f32-128">DataGridView Denetimi Senaryoları</span><span class="sxs-lookup"><span data-stu-id="38f32-128">DataGridView Control Scenarios</span></span>](datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="38f32-129">Denetimlerin kullanıldığı en yaygın senaryoları açıklar <xref:System.Windows.Forms.DataGridView> .</span><span class="sxs-lookup"><span data-stu-id="38f32-129">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="38f32-130">DataGridView Denetimi Kod Dizini</span><span class="sxs-lookup"><span data-stu-id="38f32-130">DataGridView Control Code Directory</span></span>](datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="38f32-131">Çeşitli görevler için belgelerde kod örneklerine bağlantılar sağlar <xref:System.Windows.Forms.DataGridView> .</span><span class="sxs-lookup"><span data-stu-id="38f32-131">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="38f32-132">Bu örnekler, görev türüne göre kategorilere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="38f32-132">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="38f32-133">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="38f32-133">Related Sections</span></span>  
 [<span data-ttu-id="38f32-134">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="38f32-134">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="38f32-135"><xref:System.Windows.Forms.DataGridView>Bilgileri göstermek ve kullanıcıların bilgileri değiştirmesine veya eklemesine izin vermek için kullanılan Windows Forms denetimindeki sütun türlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="38f32-135">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="38f32-136">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="38f32-136">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="38f32-137">Denetimin verileri el ile veya dış veri kaynağından nasıl doldurulacağını betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="38f32-137">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="38f32-138">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="38f32-138">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="38f32-139">Özel boyama <xref:System.Windows.Forms.DataGridView> hücrelerini ve satırları betimleyen ve türetilmiş hücre, sütun ve satır türleri oluşturan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="38f32-139">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="38f32-140">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="38f32-140">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="38f32-141">Büyük miktarlarda verilerle çalışırken performans sorunlarından kaçınmak için denetimin etkili bir şekilde nasıl kullanılacağını betimleyen konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="38f32-141">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f32-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="38f32-142">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="38f32-143">DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="38f32-143">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="38f32-144">Windows Forms DataGridView Denetimindeki Varsayılan İşlevler</span><span class="sxs-lookup"><span data-stu-id="38f32-144">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="38f32-145">Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı</span><span class="sxs-lookup"><span data-stu-id="38f32-145">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
