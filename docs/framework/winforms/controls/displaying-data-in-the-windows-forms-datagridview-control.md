---
title: "Windows Forms DataGridView Denetiminde Verileri Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 193562b5dd00950ec483da94e2ea6ea059e88805
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="cf6e0-102">Windows Forms DataGridView Denetiminde Verileri Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="cf6e0-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="cf6e0-103">`DataGridView` Denetimi, çeşitli dış veri kaynakları verileri görüntülemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="cf6e0-104">Alternatif olarak, satırları ve sütunları denetimine ekleme ve el ile veri ile doldurulacak.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="cf6e0-105">Denetim bir veri kaynağına bağlama otomatik olarak veri kaynağının şemasını temel alan sütunlar oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="cf6e0-106">Bu sütun yalnızca istediğiniz gibi görünmüyorsa gizleme, kaldırmak veya yeniden düzenleme.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="cf6e0-107">Veri kaynağından gelmez ek verileri görüntülemek için bağlanmamış sütunlar de ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="cf6e0-108">Ayrıca, (örneğin, para birimi biçimi) standart biçimlerini kullanarak verilerinizi görüntüleyebilir veya (negatif sayılar için arka plan rengi değiştirme veya dize değerlerini değiştirme gibi için gereken ancak verilerinizi sunmak için biçimlendirme görüntü özelleştirebilirsiniz karşılık gelen görüntülerle).</span><span class="sxs-lookup"><span data-stu-id="cf6e0-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf6e0-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cf6e0-109">In This Section</span></span>  
 [<span data-ttu-id="cf6e0-110">Windows Forms DataGridView Denetiminde Veri Görüntüleme Modları</span><span class="sxs-lookup"><span data-stu-id="cf6e0-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cf6e0-111">Denetim verilerle doldurmak için seçenekleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="cf6e0-112">Windows Forms DataGridView Denetiminde Veri Biçimlendirme</span><span class="sxs-lookup"><span data-stu-id="cf6e0-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cf6e0-113">Hücre görüntüleme değerleri biçimlendirme seçeneklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="cf6e0-114">İzlenecek yol: Bağlantısız Bir Windows Forms DataGridView Denetimi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf6e0-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cf6e0-115">El ile denetim verilerle doldurmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="cf6e0-116">Nasıl yapılır: Windows Forms DataGridView Denetimine Veri Bağlama</span><span class="sxs-lookup"><span data-stu-id="cf6e0-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cf6e0-117">Bağlama tarafından denetimi verileri ile doldurmak açıklanmaktadır bir `BindingSource` bir veritabanından çekilen bilgiler içerir.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="cf6e0-118">Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetiminde Sütunları Otomatik Olarak Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf6e0-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="cf6e0-119">Bir bağlı veri kaynağına göre sütunları otomatik olarak oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="cf6e0-120">Nasıl yapılır: Otomatik Oluşturulan Sütunları Windows Forms DataGridView Denetiminden Kaldırma</span><span class="sxs-lookup"><span data-stu-id="cf6e0-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="cf6e0-121">Bir bağlı veri kaynağı'ndan otomatik olarak oluşturulan sütunları silme veya gizlemek açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="cf6e0-122">Nasıl yapılır: Windows Forms DataGridView Denetiminde Sütunların Sırasını Değiştirme</span><span class="sxs-lookup"><span data-stu-id="cf6e0-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cf6e0-123">Bir bağlı veri kaynağı'ndan otomatik olarak oluşturulan sütunları yeniden açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="cf6e0-124">Nasıl yapılır: Veri Bağlantılı Windows Forms DataGridView Denetimine Bağlantısız Sütun Ekleme</span><span class="sxs-lookup"><span data-stu-id="cf6e0-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="cf6e0-125">Bağlı veri kaynağı ek, bağlanmamış sütunlar görüntüleyerek desteklemek üzere açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="cf6e0-126">Nasıl yapılır: Windows Forms DataGridView Denetimlerine Nesne Bağlama</span><span class="sxs-lookup"><span data-stu-id="cf6e0-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="cf6e0-127">Böylece her nesne kendi satırında görüntülenen denetimi rasgele nesneler koleksiyonuna bağlamak açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="cf6e0-128">Nasıl yapılır: Windows Forms DataGridView Satırlarına Bağlı Nesnelere Erişme</span><span class="sxs-lookup"><span data-stu-id="cf6e0-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](../../../../docs/framework/winforms/controls/how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="cf6e0-129">Belirli bir denetim satır için bağımlı bir nesne almak açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="cf6e0-130">İzlenecek yol: İki Windows Forms DataGridView Denetimi Kullanarak Ana/Ayrıntı Formu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf6e0-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](../../../../docs/framework/winforms/controls/creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="cf6e0-131">İki ilgili veritabanı tablodan verilerinin nasıl görüntüleneceğini açıklar böylece birinde gösterilen değerleri `DataGridView` başka bir denetim şu anda seçilen satırın denetim bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="cf6e0-132">Nasıl yapılır: Windows Forms DataGridView Denetiminde Veri Biçimlendirmeyi Özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cf6e0-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cf6e0-133">Nasıl yapılacağını açıklar <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> değerlerine bağlı olarak hücrelerin görünüşünü değiştirmek için olay.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cf6e0-134">Başvuru</span><span class="sxs-lookup"><span data-stu-id="cf6e0-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="cf6e0-135">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView> denetim.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="cf6e0-136">Başvuru belgelerine sağlar <xref:System.Windows.Forms.DataGridView.DataSource%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="cf6e0-137">Başvuru belgelerine sağlar <xref:System.Windows.Forms.BindingSource> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cf6e0-138">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="cf6e0-138">Related Sections</span></span>  
 [<span data-ttu-id="cf6e0-139">Windows Forms DataGridView Denetiminde Veri Girişi</span><span class="sxs-lookup"><span data-stu-id="cf6e0-139">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="cf6e0-140">Yol kullanıcıları değiştirmek nasıl açıklayan konulara ekleme ve verileri denetiminde değiştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf6e0-141">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf6e0-141">See Also</span></span>  
 [<span data-ttu-id="cf6e0-142">DataGridView Denetimi</span><span class="sxs-lookup"><span data-stu-id="cf6e0-142">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="cf6e0-143">Windows Forms DataGridView Denetiminde Sütun Türleri</span><span class="sxs-lookup"><span data-stu-id="cf6e0-143">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
