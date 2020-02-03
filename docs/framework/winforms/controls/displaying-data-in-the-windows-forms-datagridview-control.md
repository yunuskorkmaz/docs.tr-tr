---
title: DataGridView denetiminde verileri görüntüleme
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: d02362895d75df3735d19554bd44bb8ac443c6c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745873"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="76764-102">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="76764-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="76764-103">`DataGridView` denetimi, çeşitli dış veri kaynaklarından verileri göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76764-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="76764-104">Alternatif olarak, denetime satırlar ve sütunlar ekleyebilir ve bunu verilerle el ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76764-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="76764-105">Denetimi bir veri kaynağına bağladığınızda, veri kaynağının şemasına göre sütunları otomatik olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76764-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="76764-106">Bu sütunlar tıpkı istediğiniz gibi görünmezse, bunları gizleyebilir, kaldırabilir veya yeniden düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76764-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="76764-107">Ayrıca, veri kaynağından gelmeyen ek verileri göstermek için ilişkisiz sütunlar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="76764-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="76764-108">Ayrıca, standart biçimleri (örn. para birimi biçimi) kullanarak verilerinizi görüntüleyebilir veya görüntüleme biçimlendirmesini verilerinizi sunacak şekilde özelleştirebilirsiniz (örneğin, negatif sayıların arka plan rengini değiştirme veya dize değerlerini değiştirme gibi) ilgili görüntülerle).</span><span class="sxs-lookup"><span data-stu-id="76764-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="76764-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="76764-109">In This Section</span></span>  
 [<span data-ttu-id="76764-110">Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları</span><span class="sxs-lookup"><span data-stu-id="76764-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="76764-111">Denetimi verilerle doldurma seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="76764-112">Windows Forms DataGridView Denetiminde Veri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="76764-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="76764-113">Hücre görüntüleme değerlerini biçimlendirmeye yönelik seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="76764-114">İzlenecek yol: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="76764-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="76764-115">Denetimin verilerle el ile nasıl doldurulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="76764-116">Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="76764-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="76764-117">Bir veritabanından çekilen bilgiler içeren bir `BindingSource` bağlayarak denetimin verilerle nasıl doldurulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="76764-118">Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetiminde Sütunları Otomatik Olarak Oluşturma</span><span class="sxs-lookup"><span data-stu-id="76764-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="76764-119">Bağlı bir veri kaynağına göre otomatik olarak sütunların nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="76764-120">Nasıl yapılır: Otomatik Oluşturulan Sütunları Windows Forms DataGridView Denetiminden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="76764-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="76764-121">Bir bağlantılı veri kaynağından otomatik olarak oluşturulan sütunları gizleme veya silme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="76764-122">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="76764-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="76764-123">Bir bağlantılı veri kaynağından otomatik olarak oluşturulan sütunların nasıl yeniden düzenlenmesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="76764-124">Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetimine Bağlantısız Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="76764-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="76764-125">Bağlı bir veri kaynağından, ek, ilişkisiz sütunlar görüntüleyerek verilerin nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="76764-126">Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama</span><span class="sxs-lookup"><span data-stu-id="76764-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="76764-127">Her nesnenin kendi satırında görüntülenmesi için denetimin rastgele nesneler koleksiyonuna nasıl bağlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="76764-128">Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="76764-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="76764-129">Denetimin belirli bir satırına bağlanacak bir nesnenin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="76764-130">İzlenecek yol: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="76764-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="76764-131">Bir `DataGridView` denetiminde gösterilen değerlerin başka bir denetimde seçili olan satıra bağlı olması için, iki ilişkili veritabanı tablolarından verilerin nasıl görüntüleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="76764-132">Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="76764-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="76764-133">Değerlerine göre hücrelerin görünümünü değiştirmek için <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> olayının nasıl işleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="76764-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="76764-134">Başvuru</span><span class="sxs-lookup"><span data-stu-id="76764-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="76764-135"><xref:System.Windows.Forms.DataGridView> denetimi için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="76764-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="76764-136"><xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="76764-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="76764-137"><xref:System.Windows.Forms.BindingSource> bileşeni için başvuru belgeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="76764-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="76764-138">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="76764-138">Related Sections</span></span>  
 [<span data-ttu-id="76764-139">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="76764-139">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="76764-140">Kullanıcıların denetimdeki verileri ekleme ve değiştirme biçimini nasıl değiştireceğiniz hakkında konular sağlar.</span><span class="sxs-lookup"><span data-stu-id="76764-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76764-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76764-141">See also</span></span>

- [<span data-ttu-id="76764-142">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="76764-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="76764-143">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="76764-143">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
