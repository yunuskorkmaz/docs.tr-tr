---
title: DataGridView Denetimine Genel Bakış (Windows Forms)
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
ms.openlocfilehash: 095c89fd305b1eeb73e2919760abe48e848c6aa0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59112885"
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="e5631-102">DataGridView Denetimine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="e5631-102">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="e5631-103"><xref:System.Windows.Forms.DataGridView> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.DataGrid> denetler; ancak, <xref:System.Windows.Forms.DataGrid> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="e5631-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="e5631-104">Daha fazla bilgi için [farklar arasında Windows Forms DataGridView ve DataGrid denetimleri](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e5631-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="e5631-105">İle <xref:System.Windows.Forms.DataGridView> denetimi, görüntüleyebilir ve tablosal verilerden birçok farklı türde veri kaynaklarını düzenleyin.</span><span class="sxs-lookup"><span data-stu-id="e5631-105">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="e5631-106">Veri bağlama <xref:System.Windows.Forms.DataGridView> denetimidir basit ve sezgisel ve çoğu durumda ayarı olarak basit <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e5631-106">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="e5631-107">Birden çok listeler veya tablolar içeren bir veri kaynağına bağlandığınızda ayarlamak <xref:System.Windows.Forms.DataGridView.DataMember%2A> liste veya bağlamak için tabloyu belirten bir dize özelliği.</span><span class="sxs-lookup"><span data-stu-id="e5631-107">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="e5631-108"><xref:System.Windows.Forms.DataGridView> Denetimi için aşağıda açıklanan sınıfların örneklerini bağlamak için standart Windows Forms veri bağlama modelini destekler:</span><span class="sxs-lookup"><span data-stu-id="e5631-108">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
-   <span data-ttu-id="e5631-109">Uygulayan sınıfa <xref:System.Collections.IList> arabirimi, tek boyutlu diziler de dahil olmak üzere.</span><span class="sxs-lookup"><span data-stu-id="e5631-109">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="e5631-110">Uygulayan sınıfa <xref:System.ComponentModel.IListSource> gibi arabirim <xref:System.Data.DataTable> ve <xref:System.Data.DataSet> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="e5631-110">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
-   <span data-ttu-id="e5631-111">Uygulayan sınıfa <xref:System.ComponentModel.IBindingList> gibi arabirim <xref:System.ComponentModel.BindingList%601> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e5631-111">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
-   <span data-ttu-id="e5631-112">Uygulayan sınıfa <xref:System.ComponentModel.IBindingListView> gibi arabirim <xref:System.Windows.Forms.BindingSource> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="e5631-112">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="e5631-113"><xref:System.Windows.Forms.DataGridView> Denetimi bu arabirimleri tarafından döndürülen nesnelerin genel özelliklerini veya özellikler koleksiyonu tarafından döndürülen veri bağlamayı destekler bir <xref:System.ComponentModel.ICustomTypeDescriptor> döndürülen nesnelerin uygulanırsa, arabirim.</span><span class="sxs-lookup"><span data-stu-id="e5631-113">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="e5631-114">Genellikle, bağlayacaksınız bir <xref:System.Windows.Forms.BindingSource> bileşeni ve bağlama <xref:System.Windows.Forms.BindingSource> bileşen başka bir veri kaynağı veya iş nesneleri ile doldurur.</span><span class="sxs-lookup"><span data-stu-id="e5631-114">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="e5631-115"><xref:System.Windows.Forms.BindingSource> Bileşeni olduğundan tercih edilen veri kaynağı çok çeşitli veri kaynakları bağlayabilirsiniz ve çok sayıda veri bağlama sorunlarını otomatik olarak çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e5631-115">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="e5631-116">Daha fazla bilgi için [BindingSource bileşeni](bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="e5631-116">For more information, see [BindingSource Component](bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="e5631-117"><xref:System.Windows.Forms.DataGridView> Denetimi ayrıca kullanılabilir *ilişkisiz* moduyla temel alınan veri depo yok.</span><span class="sxs-lookup"><span data-stu-id="e5631-117">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="e5631-118">İlişkisiz bir kullanan bir kod örnek <xref:System.Windows.Forms.DataGridView> denetlemek için bkz: [izlenecek yol: Oluşturma bağlantısız bir Windows Forms DataGridView denetiminde](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e5631-118">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="e5631-119"><xref:System.Windows.Forms.DataGridView> Denetimidir son derece yapılandırılabilir ve genişletilebilir ve birçok özellikleri, yöntemleri ve onun görünümünü ve davranışını özelleştirmek için olayları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5631-119">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="e5631-120">Tablosal verileri görüntülemek için Windows Forms uygulaması istediğinizde kullanmayı <xref:System.Windows.Forms.DataGridView> diğerlerinden önce denetim (örneğin, <xref:System.Windows.Forms.DataGrid>).</span><span class="sxs-lookup"><span data-stu-id="e5631-120">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="e5631-121">Salt okunur değerleri küçük bir kılavuz görüntülüyorsanız ya da milyonlarca kayıt içeren bir tablo düzenlemek bir kullanıcı etkinleştiriyorsanız <xref:System.Windows.Forms.DataGridView> denetimi, bir kolayca programlanabilir, belleği verimli kullanan Çözümle sağlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="e5631-121">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5631-122">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="e5631-122">In This Section</span></span>  
 [<span data-ttu-id="e5631-123">DataGridView Denetimi Teknoloji Özeti</span><span class="sxs-lookup"><span data-stu-id="e5631-123">DataGridView Control Technology Summary</span></span>](datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="e5631-124">Özetler <xref:System.Windows.Forms.DataGridView> kavramları ve ilişkili sınıflarının kullanımını denetler.</span><span class="sxs-lookup"><span data-stu-id="e5631-124">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="e5631-125">DataGridView Denetimi Mimarisi</span><span class="sxs-lookup"><span data-stu-id="e5631-125">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="e5631-126">Mimarisini açıklar <xref:System.Windows.Forms.DataGridView> türü ve devralma hiyerarşisi yapısını açıklayan denetimi.</span><span class="sxs-lookup"><span data-stu-id="e5631-126">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="e5631-127">DataGridView Denetimi Senaryoları</span><span class="sxs-lookup"><span data-stu-id="e5631-127">DataGridView Control Scenarios</span></span>](datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="e5631-128">En yaygın senaryoları açıklar <xref:System.Windows.Forms.DataGridView> denetimleri kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5631-128">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="e5631-129">DataGridView Denetimi Kod Dizini</span><span class="sxs-lookup"><span data-stu-id="e5631-129">DataGridView Control Code Directory</span></span>](datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="e5631-130">Kod örnekleri çeşitli belgelerine bağlantılar sağlar <xref:System.Windows.Forms.DataGridView> görevleri.</span><span class="sxs-lookup"><span data-stu-id="e5631-130">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="e5631-131">Bu örnekler, görev türüne göre kategorize edilir.</span><span class="sxs-lookup"><span data-stu-id="e5631-131">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e5631-132">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="e5631-132">Related Sections</span></span>  
 [<span data-ttu-id="e5631-133">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="e5631-133">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e5631-134">Windows Forms'ta sütun türleri ele alınmaktadır <xref:System.Windows.Forms.DataGridView> denetim bilgilerini görüntülemek ve değiştirmek veya bilgi eklemek kullanıcılara izin vermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e5631-134">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="e5631-135">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e5631-135">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e5631-136">El ile veya bir dış veri kaynağından denetimi veriyle doldurmak nasıl açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5631-136">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="e5631-137">Windows Forms DataGridView Denetimini Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e5631-137">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e5631-138">Özel boyama açıklayan konuları sağlar <xref:System.Windows.Forms.DataGridView> hücre ve satırları ve oluşturma türetilmiş hücre, sütun ve satır türleri.</span><span class="sxs-lookup"><span data-stu-id="e5631-138">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="e5631-139">Windows Forms DataGridView Denetiminde Performans Ayarlaması</span><span class="sxs-lookup"><span data-stu-id="e5631-139">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e5631-140">Denetim verimli bir şekilde büyük miktarlarda veri ile çalışırken, performans sorunlarını önlemek için nasıl kullanılacağını açıklayan konuları sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5631-140">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5631-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e5631-141">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="e5631-142">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="e5631-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="e5631-143">Windows Forms DataGridView Denetimindeki Varsayılan İşlevler</span><span class="sxs-lookup"><span data-stu-id="e5631-143">Default Functionality in the Windows Forms DataGridView Control</span></span>](default-functionality-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e5631-144">Windows Forms DataGridView Denetiminde Varsayılan Klavye ve Fare Kullanımı</span><span class="sxs-lookup"><span data-stu-id="e5631-144">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
