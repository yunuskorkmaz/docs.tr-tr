---
title: DataViews
ms.date: 03/30/2017
ms.assetid: 0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b
ms.openlocfilehash: 8a06accb11631f2dce6b0d39587d7274223c0e68
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786351"
---
# <a name="dataviews"></a><span data-ttu-id="798fb-102">DataViews</span><span class="sxs-lookup"><span data-stu-id="798fb-102">DataViews</span></span>
<span data-ttu-id="798fb-103">, Genellikle veri bağlama uygulamalarında kullanılan bir özellik olan, <xref:System.Data.DataView> içinde depolanan verilerin farklı görünümlerini <xref:System.Data.DataTable>oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="798fb-103">A <xref:System.Data.DataView> enables you to create different views of the data stored in a <xref:System.Data.DataTable>, a capability that is often used in data-binding applications.</span></span> <span data-ttu-id="798fb-104">Bir **DataView**kullanarak verileri farklı sıralama siparişleriyle bir tabloda kullanıma sunabilirsiniz ve verileri satır durumuna göre veya bir filtre ifadesine göre filtreleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="798fb-104">Using a **DataView**, you can expose the data in a table with different sort orders, and you can filter the data by row state or based on a filter expression.</span></span>  
  
 <span data-ttu-id="798fb-105">Bir **DataView** , temel alınan **DataTable**'daki verilerin dinamik bir görünümünü sağlar: içerik, sıralama ve üyelik, gerçekleşen değişiklikleri yansıtır.</span><span class="sxs-lookup"><span data-stu-id="798fb-105">A **DataView** provides a dynamic view of data in the underlying **DataTable**: the content, ordering, and membership reflect changes as they occur.</span></span> <span data-ttu-id="798fb-106">Bu davranış, belirli bir filtre ve/veyasıralama düzenini temel alan bir <xref:System.Data.DataRow> tablodan dizi döndüren DataTable 'ın **Select** yönteminden farklıdır: Bu içerik, temel tablodaki değişiklikleri yansıtır, ancak üyeliği ve sıralama statik kalır.</span><span class="sxs-lookup"><span data-stu-id="798fb-106">This behavior differs from the **Select** method of the **DataTable**, which returns a <xref:System.Data.DataRow> array from a table based on a particular filter and/or sort order: this content reflects changes to the underlying table, but its membership and ordering remain static.</span></span> <span data-ttu-id="798fb-107">**DataView** 'ın dinamik özellikleri, veri bağlama uygulamaları için ideal hale getirir.</span><span class="sxs-lookup"><span data-stu-id="798fb-107">The dynamic capabilities of the **DataView** make it ideal for data-binding applications.</span></span>  
  
 <span data-ttu-id="798fb-108">Bir **DataView** size, farklı sıralama ve filtreleme ölçütleri uygulayabileceğiniz bir veritabanı görünümü gibi tek bir veri kümesinin dinamik görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="798fb-108">A **DataView** provides you with a dynamic view of a single set of data, much like a database view, to which you can apply different sorting and filtering criteria.</span></span> <span data-ttu-id="798fb-109">Ancak, bir veritabanı görünümünün aksine, bir **DataView** tablo olarak kabul edilemez ve birleştirilmiş tabloların bir görünümünü sağlayamaz.</span><span class="sxs-lookup"><span data-stu-id="798fb-109">Unlike a database view, however, a **DataView** cannot be treated as a table and cannot provide a view of joined tables.</span></span> <span data-ttu-id="798fb-110">Kaynak tabloda mevcut olmayan sütunları da dışlayamazsınız ve kaynak tabloda bulunmayan hesaplama sütunları gibi sütunları ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="798fb-110">You also cannot exclude columns that exist in the source table, nor can you append columns, such as computational columns, that do not exist in the source table.</span></span>  
  
 <span data-ttu-id="798fb-111">Bir **veri kümesindeki**tüm <xref:System.Data.DataView.DataViewManager%2A> tablolar için görünüm ayarlarını yönetmek üzere bir kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="798fb-111">You can use a <xref:System.Data.DataView.DataViewManager%2A> to manage view settings for all the tables in a **DataSet**.</span></span> <span data-ttu-id="798fb-112">**DataViewManager** , her tablo için varsayılan görünüm ayarlarını yönetmenin kolay bir yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="798fb-112">The **DataViewManager** provides you with a convenient way to manage default view settings for each table.</span></span> <span data-ttu-id="798fb-113">Bir denetimi bir **veri kümesinin**birden fazla tablosuna bağlarken **DataViewManager** 'a bağlama ideal seçenektir.</span><span class="sxs-lookup"><span data-stu-id="798fb-113">When binding a control to more than one table of a **DataSet**, binding to a **DataViewManager** is the ideal choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="798fb-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="798fb-114">In This Section</span></span>  
 [<span data-ttu-id="798fb-115">DataView Oluşturma</span><span class="sxs-lookup"><span data-stu-id="798fb-115">Creating a DataView</span></span>](creating-a-dataview.md)  
 <span data-ttu-id="798fb-116">**DataTable**Için bir **DataView** oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="798fb-116">Describes how to create a **DataView** for a **DataTable**.</span></span>  
  
 [<span data-ttu-id="798fb-117">Verileri Sıralama ve Filtreleme</span><span class="sxs-lookup"><span data-stu-id="798fb-117">Sorting and Filtering Data</span></span>](sorting-and-filtering-data.md)  
 <span data-ttu-id="798fb-118">Bir **DataView** özelliklerinin belirli filtre ölçütlerine uyan veri satırlarının alt kümelerini döndürme veya belirli bir sıralama düzeninde verileri döndürme için nasıl ayarlanacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="798fb-118">Describes how to set the properties of a **DataView** to return subsets of data rows meeting specific filter criteria, or to return data in a particular sort order.</span></span>  
  
 [<span data-ttu-id="798fb-119">DataRows ve DataRowViews</span><span class="sxs-lookup"><span data-stu-id="798fb-119">DataRows and DataRowViews</span></span>](datarows-and-datarowviews.md)  
 <span data-ttu-id="798fb-120">**DataView**tarafından sunulan verilere nasıl erişebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="798fb-120">Describes how to access the data exposed by the **DataView**.</span></span>  
  
 [<span data-ttu-id="798fb-121">Satırları Bulma</span><span class="sxs-lookup"><span data-stu-id="798fb-121">Finding Rows</span></span>](finding-rows.md)  
 <span data-ttu-id="798fb-122">**DataView**içinde belirli bir satırın nasıl bulunacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="798fb-122">Describes how to find a particular row in a **DataView**.</span></span>  
  
 [<span data-ttu-id="798fb-123">ChildViews ve İlişkileri</span><span class="sxs-lookup"><span data-stu-id="798fb-123">ChildViews and Relations</span></span>](childviews-and-relations.md)  
 <span data-ttu-id="798fb-124">Bir **DataView**kullanarak üst-alt ilişkiden veri görünümlerinin nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="798fb-124">Describes how to create views of data from a parent-child relationship using a **DataView**.</span></span>  
  
 [<span data-ttu-id="798fb-125">DataView Değiştirme</span><span class="sxs-lookup"><span data-stu-id="798fb-125">Modifying DataViews</span></span>](modifying-dataviews.md)  
 <span data-ttu-id="798fb-126">Güncelleştirmeleri etkinleştirme veya devre dışı bırakma dahil olmak üzere **DataView**aracılığıyla temel alınan **DataTable** 'daki verilerin nasıl değiştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="798fb-126">Describes how to modify the data in the underlying **DataTable** via the **DataView**, including enabling or disabling updates.</span></span>  
  
 [<span data-ttu-id="798fb-127">DataView Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="798fb-127">Handling DataView Events</span></span>](handling-dataview-events.md)  
 <span data-ttu-id="798fb-128">Bir **DataView** içeriği veya sırası güncelleştirilirken bildirim almak Için **ListChanged** olayının nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="798fb-128">Describes how to use the **ListChanged** event to receive notification when the contents or order of a **DataView** is being updated.</span></span>  
  
 [<span data-ttu-id="798fb-129">DataView Yönetme</span><span class="sxs-lookup"><span data-stu-id="798fb-129">Managing DataViews</span></span>](managing-dataviews.md)  
 <span data-ttu-id="798fb-130">Bir **veri kümesindeki**her tablo için **DataView** ayarlarını yönetmek üzere **DataViewManager** 'ın nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="798fb-130">Describes how to use a **DataViewManager** to manage **DataView** settings for each table in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="798fb-131">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="798fb-131">Related Sections</span></span>  
 <span data-ttu-id="798fb-132">[ASP.NET Web Uygulamaları](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="798fb-132">[ASP.NET Web Applications](https://docs.microsoft.com/previous-versions/655cec97(v=vs.100))</span></span>  
 <span data-ttu-id="798fb-133">ASP.NET uygulamaları, Web Forms ve Web hizmetleri oluşturmak için genel bakış ve ayrıntılı, adım adım yordamlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="798fb-133">Provides overviews and detailed, step-by-step procedures for creating ASP.NET applications, Web Forms, and Web Services.</span></span>  
  
 <span data-ttu-id="798fb-134">[Windows uygulamaları](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="798fb-134">[Windows Applications](https://docs.microsoft.com/previous-versions/ms184421(v=vs.100))</span></span>  
 <span data-ttu-id="798fb-135">Windows Forms ve konsol uygulamalarıyla çalışma hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="798fb-135">Provides detailed information about working with Windows Forms and console applications.</span></span>  
  
 [<span data-ttu-id="798fb-136">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="798fb-136">DataSets, DataTables, and DataViews</span></span>](index.md)  
 <span data-ttu-id="798fb-137">**Veri kümesi** nesnesini ve uygulama verilerini yönetmek için nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="798fb-137">Describes the **DataSet** object and how you can use it to manage application data.</span></span>  
  
 [<span data-ttu-id="798fb-138">DataTables</span><span class="sxs-lookup"><span data-stu-id="798fb-138">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="798fb-139">**DataTable** nesnesini ve uygulama verilerini kendi başına veya bir **veri kümesinin**parçası olarak yönetmek için nasıl kullanabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="798fb-139">Describes the **DataTable** object and how you can use it to manage application data by itself or as part of a **DataSet**.</span></span>  
  
 [<span data-ttu-id="798fb-140">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="798fb-140">ADO.NET</span></span>](../index.md)  
 <span data-ttu-id="798fb-141">ADO.NET mimarisini ve bileşenlerini ve var olan veri kaynaklarına erişmek ve uygulama verilerini yönetmek için ADO.NET 'in nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="798fb-141">Describes the ADO.NET architecture and components, and how to use ADO.NET to access existing data sources and manage application data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="798fb-142">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="798fb-142">See also</span></span>

- [<span data-ttu-id="798fb-143">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="798fb-143">ADO.NET Overview</span></span>](../ado-net-overview.md)
