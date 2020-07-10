---
title: DataGridView denetiminde verileri görüntüleme
description: Çeşitli dış veri kaynaklarından verileri göstermek için Windows Forms DataGridView denetimini nasıl kullanacağınızı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: a0f3e6627290521b8c10477c31459f1486e79162
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174581"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9ab17-103">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="9ab17-103">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9ab17-104">`DataGridView`Denetim, çeşitli dış veri kaynaklarından verileri göstermek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ab17-104">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="9ab17-105">Alternatif olarak, denetime satırlar ve sütunlar ekleyebilir ve bunu verilerle el ile doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ab17-105">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="9ab17-106">Denetimi bir veri kaynağına bağladığınızda, veri kaynağının şemasına göre sütunları otomatik olarak oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ab17-106">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="9ab17-107">Bu sütunlar tıpkı istediğiniz gibi görünmezse, bunları gizleyebilir, kaldırabilir veya yeniden düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ab17-107">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="9ab17-108">Ayrıca, veri kaynağından gelmeyen ek verileri göstermek için ilişkisiz sütunlar ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ab17-108">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="9ab17-109">Ayrıca, verilerinizi standart biçimler (örn. para birimi biçimi) kullanarak görüntüleyebilir veya verilerinizi sunmak için (örneğin, negatif sayıların arka plan rengini değiştirme veya dize değerlerini karşılık gelen görüntülerle değiştirme gibi) görüntüleme biçimlendirmesini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ab17-109">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9ab17-110">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9ab17-110">In This Section</span></span>  
 [<span data-ttu-id="9ab17-111">Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları</span><span class="sxs-lookup"><span data-stu-id="9ab17-111">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9ab17-112">Denetimi verilerle doldurma seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab17-112">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="9ab17-113">Windows Forms DataGridView Denetiminde Veri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="9ab17-113">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9ab17-114">Hücre görüntüleme değerlerini biçimlendirmeye yönelik seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab17-114">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="9ab17-115">İzlenecek yol: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ab17-115">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9ab17-116">Denetimin verilerle el ile nasıl doldurulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab17-116">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="9ab17-117">Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="9ab17-117">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9ab17-118">Bir veritabanından çekilen bilgiler içeren bir öğesine bağlayarak denetimin verilerle nasıl doldurulacağını açıklar `BindingSource` .</span><span class="sxs-lookup"><span data-stu-id="9ab17-118">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="9ab17-119">Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetiminde Sütunları Otomatik Olarak Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ab17-119">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="9ab17-120">Bağlı bir veri kaynağına göre otomatik olarak sütunların nasıl oluşturulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab17-120">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="9ab17-121">Nasıl yapılır: Otomatik Oluşturulan Sütunları Windows Forms DataGridView Denetiminden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="9ab17-121">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="9ab17-122">Bir bağlantılı veri kaynağından otomatik olarak oluşturulan sütunları gizleme veya silme işlemini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab17-122">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="9ab17-123">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="9ab17-123">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9ab17-124">Bir bağlantılı veri kaynağından otomatik olarak oluşturulan sütunların nasıl yeniden düzenlenmesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab17-124">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="9ab17-125">Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetimine Bağlantısız Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="9ab17-125">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="9ab17-126">Bağlı bir veri kaynağından, ek, ilişkisiz sütunlar görüntüleyerek verilerin nasıl ekleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab17-126">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="9ab17-127">Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama</span><span class="sxs-lookup"><span data-stu-id="9ab17-127">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="9ab17-128">Her nesnenin kendi satırında görüntülenmesi için denetimin rastgele nesneler koleksiyonuna nasıl bağlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab17-128">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="9ab17-129">Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="9ab17-129">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="9ab17-130">Denetimin belirli bir satırına bağlanacak bir nesnenin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab17-130">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="9ab17-131">İzlenecek yol: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="9ab17-131">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="9ab17-132">İki ilişkili veritabanı tablolarındaki verilerin nasıl görüntüleneceğini açıklar. böylece, bir denetimde gösterilen değerlerin `DataGridView` başka bir denetimde seçili olan satıra bağlı olması sağlanır.</span><span class="sxs-lookup"><span data-stu-id="9ab17-132">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="9ab17-133">Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="9ab17-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9ab17-134"><xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>Değerlerine göre hücrelerin görünümünü değiştirmek için olayın nasıl işleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="9ab17-134">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9ab17-135">Başvuru</span><span class="sxs-lookup"><span data-stu-id="9ab17-135">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="9ab17-136">Denetim için başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView> .</span><span class="sxs-lookup"><span data-stu-id="9ab17-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="9ab17-137">Özelliği için başvuru belgeleri sağlar <xref:System.Windows.Forms.DataGridView.DataSource%2A> .</span><span class="sxs-lookup"><span data-stu-id="9ab17-137">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="9ab17-138">Bileşen için başvuru belgeleri sağlar <xref:System.Windows.Forms.BindingSource> .</span><span class="sxs-lookup"><span data-stu-id="9ab17-138">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9ab17-139">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="9ab17-139">Related Sections</span></span>  
 [<span data-ttu-id="9ab17-140">Windows Forms DataGridView Denetimindeki Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="9ab17-140">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9ab17-141">Kullanıcıların denetimdeki verileri ekleme ve değiştirme biçimini nasıl değiştireceğiniz hakkında konular sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ab17-141">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ab17-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ab17-142">See also</span></span>

- [<span data-ttu-id="9ab17-143">DataGridView denetimi</span><span class="sxs-lookup"><span data-stu-id="9ab17-143">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="9ab17-144">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="9ab17-144">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
