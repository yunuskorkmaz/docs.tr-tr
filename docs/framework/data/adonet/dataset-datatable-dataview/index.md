---
title: DataSets, DataTables ve DataViews
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: d712f82b0d776b671a8d8219276c32761d245047
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521289"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="52afd-102">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="52afd-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="52afd-103">ADO.NET <xref:System.Data.DataSet> içerdiği veri kaynağını bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan veri bellekte gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="52afd-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="52afd-104">A <xref:System.Data.DataSet> sipariş ve tablolar arasındaki ilişkileri yanı sıra, verileri sınırlamak içeren tablolar da dahil olmak üzere veri eksiksiz bir kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="52afd-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="52afd-105">İle çalışmaya ilişkin birkaç şekilde bir <xref:System.Data.DataSet>, hangi uygulanabilir bağımsız olarak veya birlikte.</span><span class="sxs-lookup"><span data-stu-id="52afd-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="52afd-106">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="52afd-106">You can:</span></span>  
  
-   <span data-ttu-id="52afd-107">Program aracılığıyla oluşturma bir <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, ve <xref:System.Data.Constraint> içinde bir <xref:System.Data.DataSet> ve tabloları verilerle doldurun.</span><span class="sxs-lookup"><span data-stu-id="52afd-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
-   <span data-ttu-id="52afd-108">Doldurma <xref:System.Data.DataSet> var olan bir ilişkisel veri kaynağı kullanarak veri tabloları içeren bir `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="52afd-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
-   <span data-ttu-id="52afd-109">Yük ve kalıcı <xref:System.Data.DataSet> kullanarak XML içeriği.</span><span class="sxs-lookup"><span data-stu-id="52afd-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="52afd-110">Daha fazla bilgi için [kullanarak bir veri kümesi XML'de](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="52afd-110">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="52afd-111">Türü kesin belirlenmiş <xref:System.Data.DataSet> kullanarak bir XML Web Hizmeti ayrıca taşınabilen.</span><span class="sxs-lookup"><span data-stu-id="52afd-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="52afd-112">Tasarımını <xref:System.Data.DataSet> XML Web Hizmetleri ile veri taşıma için ideal hale getirir.</span><span class="sxs-lookup"><span data-stu-id="52afd-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="52afd-113">XML Web Hizmetleri genel bakış için bkz. [XML Web Hizmetleri genel bakış](https://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span><span class="sxs-lookup"><span data-stu-id="52afd-113">For an overview of XML Web services, see [XML Web Services Overview](https://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span></span> <span data-ttu-id="52afd-114">Kullanan bir örnek için bir <xref:System.Data.DataSet> bir XML Web hizmetinden bkz [bir XML Web hizmetinden DataSet kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="52afd-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="52afd-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="52afd-115">In This Section</span></span>  
 [<span data-ttu-id="52afd-116">DataSet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="52afd-116">Creating a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 <span data-ttu-id="52afd-117">Örneği oluşturmak için söz dizimini açıklar bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="52afd-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="52afd-118">DataSet’e DataTable Ekleme</span><span class="sxs-lookup"><span data-stu-id="52afd-118">Adding a DataTable to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="52afd-119">Oluşturma ve tablolar ve sütunlar ekleme açıklar bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="52afd-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="52afd-120">DataRelations Ekleme</span><span class="sxs-lookup"><span data-stu-id="52afd-120">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 <span data-ttu-id="52afd-121">Tablolar arasındaki ilişkileri oluşturmayı açıklar bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="52afd-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="52afd-122">DataRelations İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="52afd-122">Navigating DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 <span data-ttu-id="52afd-123">Tablolar arasındaki ilişkileri açıklar bir <xref:System.Data.DataSet> bir üst-alt ilişkinin alt veya üst satırları döndürür.</span><span class="sxs-lookup"><span data-stu-id="52afd-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="52afd-124">DataSet İçeriklerini Birleştirme</span><span class="sxs-lookup"><span data-stu-id="52afd-124">Merging DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 <span data-ttu-id="52afd-125">İçeriği bir birleştirme işlemini açıklamaktadır <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow> başka bir diziye <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="52afd-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="52afd-126">DataSet İçeriklerini Kopyalama</span><span class="sxs-lookup"><span data-stu-id="52afd-126">Copying DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 <span data-ttu-id="52afd-127">Bir kopyasını oluşturmayı açıklar bir <xref:System.Data.DataSet> belirtilen verilerin yanı sıra şema içerebilir.</span><span class="sxs-lookup"><span data-stu-id="52afd-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="52afd-128">DataSet Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="52afd-128">Handling DataSet Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 <span data-ttu-id="52afd-129">Olayları açıklayan bir <xref:System.Data.DataSet> ve bunların nasıl kullanıldığı.</span><span class="sxs-lookup"><span data-stu-id="52afd-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="52afd-130">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="52afd-130">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 <span data-ttu-id="52afd-131">Hangi yazılmış anlatılmaktadır <xref:System.Data.DataSet> olduğu ve nasıl oluşturup kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52afd-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="52afd-132">DataTables</span><span class="sxs-lookup"><span data-stu-id="52afd-132">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="52afd-133">Nasıl oluşturulacağını açıklar bir <xref:System.Data.DataTable>şema tanımlayabilir ve verilerini işleme.</span><span class="sxs-lookup"><span data-stu-id="52afd-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="52afd-134">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="52afd-134">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 <span data-ttu-id="52afd-135">Nasıl oluşturup kullanacağınızı açıklayan bir <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="52afd-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="52afd-136">DataViews</span><span class="sxs-lookup"><span data-stu-id="52afd-136">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="52afd-137">Oluşturma ve bunlarla çalışmak açıklar `DataViews` ve çalışmak <xref:System.Data.DataView> olayları.</span><span class="sxs-lookup"><span data-stu-id="52afd-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="52afd-138">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="52afd-138">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="52afd-139">Açıklayan nasıl <xref:System.Data.DataSet> yükleniyor ve içeriğini kalıcı dahil olmak üzere bir veri kaynağı olarak XML ile etkileşime giren bir <xref:System.Data.DataSet> XML verileri olarak.</span><span class="sxs-lookup"><span data-stu-id="52afd-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="52afd-140">XML Web Hizmetinden DataSet Kullanma</span><span class="sxs-lookup"><span data-stu-id="52afd-140">Consuming a DataSet from an XML Web Service</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="52afd-141">Kullanan bir XML Web hizmeti oluşturmayı açıklar bir <xref:System.Data.DataSet> aktarım veri.</span><span class="sxs-lookup"><span data-stu-id="52afd-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="52afd-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="52afd-142">Related Sections</span></span>  
 [<span data-ttu-id="52afd-143">ADO.NET’teki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="52afd-143">What's New in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/whats-new.md)  
 <span data-ttu-id="52afd-144">ADO.NET yeni özellikleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="52afd-144">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="52afd-145">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="52afd-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 <span data-ttu-id="52afd-146">Tasarım ve ADO.NET bileşenlerini tanıtır.</span><span class="sxs-lookup"><span data-stu-id="52afd-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="52afd-147">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="52afd-147">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="52afd-148">Nasıl yükleneceğini açıklayan bir **veri kümesi** bir veri kaynağı ile.</span><span class="sxs-lookup"><span data-stu-id="52afd-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="52afd-149">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="52afd-149">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="52afd-150">Veriler üzerinde değişiklikler çözümlemeyi açıklar bir **veri kümesi** veri kaynağına geri dönün.</span><span class="sxs-lookup"><span data-stu-id="52afd-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="52afd-151">DataSet’e Var Olan Kısıtlamaları Ekleme</span><span class="sxs-lookup"><span data-stu-id="52afd-151">Adding Existing Constraints to a DataSet</span></span>](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="52afd-152">Nasıl doldurulacağını açıklar bir **veri kümesi** birincil anahtar bilgilerini bir veri kaynağından.</span><span class="sxs-lookup"><span data-stu-id="52afd-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52afd-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="52afd-153">See also</span></span>
- [<span data-ttu-id="52afd-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="52afd-154">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)
- [<span data-ttu-id="52afd-155">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="52afd-155">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
