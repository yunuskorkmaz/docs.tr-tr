---
title: Windows Forms DataGridView Denetiminde Verileri Görüntüleme
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: c153d422470ff20491567aed70557e461dc2b4e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168642"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c1912-102">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="c1912-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c1912-103">`DataGridView` Denetimi, çeşitli dış veri kaynaklarından verileri görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c1912-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="c1912-104">Alternatif olarak, denetimine satır ve sütun ekleme ve el ile veri ile doldurulacak.</span><span class="sxs-lookup"><span data-stu-id="c1912-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="c1912-105">Denetim bir veri kaynağına bağlandığınızda, veri kaynağının şemasını temel alınarak otomatik olarak bir sütun oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1912-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="c1912-106">Yalnızca istediğiniz gibi bu sütun gösterilmezse, gizleme, kaldırmak veya yeniden düzenleme.</span><span class="sxs-lookup"><span data-stu-id="c1912-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="c1912-107">Bağlanmamış sütunlar veri kaynağından gelmez ek verileri görüntülemek için de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c1912-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="c1912-108">Ayrıca, standart biçim (örneğin, para birimi biçimi) kullanarak verilerinizi görüntüleyebilir veya (negatif sayılar arka plan rengini değiştirmek veya dize değerleri değiştirme gibi için gerekir, ancak verilerinizi sunmak için biçimlendirme görünen özelleştirebilirsiniz. karşılık gelen görüntülerle).</span><span class="sxs-lookup"><span data-stu-id="c1912-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c1912-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c1912-109">In This Section</span></span>  
 [<span data-ttu-id="c1912-110">Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları</span><span class="sxs-lookup"><span data-stu-id="c1912-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c1912-111">Denetim verileri ile doldurmak için seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="c1912-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="c1912-112">Windows Forms DataGridView Denetiminde Veri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="c1912-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c1912-113">Hücre görüntüleme değerleri biçimlendirme seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c1912-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="c1912-114">İzlenecek yol: Bağlantısız bir Windows Forms DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="c1912-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c1912-115">El ile denetim veri ile doldurmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="c1912-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="c1912-116">Nasıl yapılır: Windows Forms DataGridView denetimine veri bağlama</span><span class="sxs-lookup"><span data-stu-id="c1912-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c1912-117">Bağlama tarafından denetim veri ile doldurmak açıklanmaktadır bir `BindingSource` çekilen bir veritabanından bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="c1912-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="c1912-118">Nasıl yapılır: Bir veri bağlantılı Windows Forms DataGridView denetiminde sütunları otomatik olarak oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1912-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="c1912-119">Bağlı veri kaynağını temel alan sütunları otomatik olarak oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="c1912-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="c1912-120">Nasıl yapılır: Otomatik oluşturulan sütunları Windows Forms DataGridView denetiminden kaldırma</span><span class="sxs-lookup"><span data-stu-id="c1912-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="c1912-121">Bağlı veri kaynağından otomatik olarak oluşturulan sütunları silme veya gizlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="c1912-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="c1912-122">Nasıl yapılır: Windows Forms DataGridView denetiminde sütunların sırasını değiştirme</span><span class="sxs-lookup"><span data-stu-id="c1912-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c1912-123">Bağlı veri kaynağından otomatik olarak oluşturulan sütunları yeniden açıklar.</span><span class="sxs-lookup"><span data-stu-id="c1912-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="c1912-124">Nasıl yapılır: Bir veri bağlantılı Windows Forms DataGridView denetimine bağlantısız sütun ekleme</span><span class="sxs-lookup"><span data-stu-id="c1912-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="c1912-125">Ek, bağlanmamış sütunlar görüntüleyerek bir bağımlı veri kaynağı ek açıklar.</span><span class="sxs-lookup"><span data-stu-id="c1912-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="c1912-126">Nasıl yapılır: Windows Forms DataGridView denetimlerine nesne bağlama</span><span class="sxs-lookup"><span data-stu-id="c1912-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="c1912-127">Böylece her bir nesnenin kendi satırında görüntülenen denetimini rastgele nesneleri koleksiyonu için bağlama işlemini açıklamaktadır.</span><span class="sxs-lookup"><span data-stu-id="c1912-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="c1912-128">Nasıl yapılır: Windows Forms DataGridView satırlarına bağlı nesnelere erişme</span><span class="sxs-lookup"><span data-stu-id="c1912-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="c1912-129">Denetimin belirli bir satıra bağlı bir nesne almak nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="c1912-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="c1912-130">İzlenecek yol: İki Windows Forms DataGridView denetimi kullanarak ana/ayrıntı formu oluşturma</span><span class="sxs-lookup"><span data-stu-id="c1912-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="c1912-131">İki ilişkili veritabanı tablolarındaki verileri görüntüleyen açıklar böylece birinde gösterilen değerleri `DataGridView` denetimi başka bir denetimi şu anda seçilen satırın bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c1912-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="c1912-132">Nasıl yapılır: Windows Forms DataGridView denetiminde veri biçimlendirmeyi özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c1912-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c1912-133">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> değerlerine bağlı olarak hücrelerin görünüşünü değiştirmek için olay.</span><span class="sxs-lookup"><span data-stu-id="c1912-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="c1912-134">Başvuru</span><span class="sxs-lookup"><span data-stu-id="c1912-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="c1912-135">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> denetimi.</span><span class="sxs-lookup"><span data-stu-id="c1912-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="c1912-136">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="c1912-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="c1912-137">İçin başvuru belgeleri sağlar <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="c1912-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c1912-138">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="c1912-138">Related Sections</span></span>  
 [<span data-ttu-id="c1912-139">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="c1912-139">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="c1912-140">Kullanıcıların değiştirme açıklayan konulara ekleyin ve denetimi veri değiştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1912-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1912-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1912-141">See also</span></span>

- [<span data-ttu-id="c1912-142">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="c1912-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="c1912-143">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="c1912-143">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
