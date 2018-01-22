---
title: DataSets, DataTables ve DataViews
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 5fe09601be7173fd1a9228dc090732ded7afdd90
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="2ee3f-102">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="2ee3f-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="2ee3f-103">ADO.NET <xref:System.Data.DataSet> içerdiği veri kaynağını bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlar veri bellekte gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="2ee3f-104">A <xref:System.Data.DataSet> sipariş ve tablolar arasındaki ilişkileri yanı sıra, verileri sınırlamak içeren tablolar dahil olmak üzere verileri eksiksiz bir kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="2ee3f-105">İle çalışmaya ilişkin birkaç yolu vardır bir <xref:System.Data.DataSet>, hangi uygulanabilir bağımsız olarak veya birlikte.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="2ee3f-106">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2ee3f-106">You can:</span></span>  
  
-   <span data-ttu-id="2ee3f-107">Program aracılığıyla oluşturma bir <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, ve <xref:System.Data.Constraint> içinde bir <xref:System.Data.DataSet> ve veri tablolarıyla doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
-   <span data-ttu-id="2ee3f-108">Doldurmak <xref:System.Data.DataSet> var olan bir ilişkisel veri kaynağı kullanılarak verileri tablolar ile bir `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
-   <span data-ttu-id="2ee3f-109">Yük ve kalıcı <xref:System.Data.DataSet> XML kullanarak içeriği.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="2ee3f-110">Daha fazla bilgi için bkz: [XML kullanarak bir veri kümesinde](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="2ee3f-110">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="2ee3f-111">Kesin türü belirtilmiş <xref:System.Data.DataSet> bir XML Web hizmetini kullanarak da taşınabilen.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="2ee3f-112">Tasarımını <xref:System.Data.DataSet> XML Web Hizmetleri kullanarak veri taşıma için ideal hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="2ee3f-113">XML Web Hizmetleri genel bakış için bkz: [XML Web Hizmetleri genel bakış](http://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span><span class="sxs-lookup"><span data-stu-id="2ee3f-113">For an overview of XML Web services, see [XML Web Services Overview](http://msdn.microsoft.com/library/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span></span> <span data-ttu-id="2ee3f-114">Kullanma örneği için bir <xref:System.Data.DataSet> bir XML Web hizmetinden bkz [bir XML Web hizmetinden veri kümesi kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="2ee3f-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ee3f-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="2ee3f-115">In This Section</span></span>  
 [<span data-ttu-id="2ee3f-116">DataSet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="2ee3f-116">Creating a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 <span data-ttu-id="2ee3f-117">Örneği oluşturmak için söz dizimi açıklanmıştır bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="2ee3f-118">DataSet’e DataTable Ekleme</span><span class="sxs-lookup"><span data-stu-id="2ee3f-118">Adding a DataTable to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="2ee3f-119">Oluşturma ve tablolar ve sütunlar ekleme açıklar bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="2ee3f-120">DataRelations Ekleme</span><span class="sxs-lookup"><span data-stu-id="2ee3f-120">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 <span data-ttu-id="2ee3f-121">Tablolar arasındaki ilişkileri oluşturmayı açıklar bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="2ee3f-122">DataRelations İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="2ee3f-122">Navigating DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 <span data-ttu-id="2ee3f-123">Tablolar arasındaki ilişkileri kullanmayı açıklar bir <xref:System.Data.DataSet> üst-alt ilişkinin bir alt veya üst satır döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="2ee3f-124">DataSet İçeriklerini Birleştirme</span><span class="sxs-lookup"><span data-stu-id="2ee3f-124">Merging DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 <span data-ttu-id="2ee3f-125">İçeriği bir birleştirme açıklar <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow> başka diziye <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="2ee3f-126">DataSet İçeriklerini Kopyalama</span><span class="sxs-lookup"><span data-stu-id="2ee3f-126">Copying DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 <span data-ttu-id="2ee3f-127">Bir kopyasını oluşturmayı açıklar bir <xref:System.Data.DataSet> belirtilen veri yanı sıra şema içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="2ee3f-128">DataSet Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="2ee3f-128">Handling DataSet Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 <span data-ttu-id="2ee3f-129">Olayları açıklayan bir <xref:System.Data.DataSet> ve bunları nasıl kullanacağınızı.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="2ee3f-130">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="2ee3f-130">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 <span data-ttu-id="2ee3f-131">Hangi yazılmış anlatılmaktadır <xref:System.Data.DataSet> olduğu ve nasıl oluşturulacağı ve bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="2ee3f-132">DataTables</span><span class="sxs-lookup"><span data-stu-id="2ee3f-132">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="2ee3f-133">Nasıl oluşturulacağını açıklar bir <xref:System.Data.DataTable>Şeması Tanımlama ve verileri işlemek.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="2ee3f-134">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="2ee3f-134">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 <span data-ttu-id="2ee3f-135">Oluşturma ve kullanma açıklar bir <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="2ee3f-136">DataViews</span><span class="sxs-lookup"><span data-stu-id="2ee3f-136">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="2ee3f-137">Oluşturma ve bunlarla çalışmak açıklar `DataViews` ve bunlarla çalışmak <xref:System.Data.DataView> olaylar.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="2ee3f-138">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="2ee3f-138">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="2ee3f-139">Açıklar nasıl <xref:System.Data.DataSet> yükleme ve içeriği kalıcı yapma dahil olmak üzere bir veri kaynağı olarak XML ile etkileşime giren bir <xref:System.Data.DataSet> XML verileri olarak.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="2ee3f-140">XML Web Hizmetinden DataSet Kullanma</span><span class="sxs-lookup"><span data-stu-id="2ee3f-140">Consuming a DataSet from an XML Web Service</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="2ee3f-141">Kullanan XML Web hizmeti oluşturmayı açıklar bir <xref:System.Data.DataSet> Aktarım verileri.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2ee3f-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="2ee3f-142">Related Sections</span></span>  
 [<span data-ttu-id="2ee3f-143">ADO.NET’teki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="2ee3f-143">What's New in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/whats-new.md)  
 <span data-ttu-id="2ee3f-144">ADO.NET yeni özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-144">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="2ee3f-145">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2ee3f-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 <span data-ttu-id="2ee3f-146">Tasarım ve ADO.NET bileşenlerinin bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="2ee3f-147">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="2ee3f-147">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="2ee3f-148">Nasıl yükleneceğini açıklayan bir **DataSet** bir veri kaynağı ile.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="2ee3f-149">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="2ee3f-149">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="2ee3f-150">Verilerde değişiklik çözümlemeyi açıklar bir **DataSet** veri kaynağına geri.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="2ee3f-151">DataSet’e Var Olan Kısıtlamaları Ekleme</span><span class="sxs-lookup"><span data-stu-id="2ee3f-151">Adding Existing Constraints to a DataSet</span></span>](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="2ee3f-152">Doldurmak nasıl açıklar bir **DataSet** bir veri kaynağından birincil anahtar bilgileri.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ee3f-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2ee3f-153">See Also</span></span>  
 [<span data-ttu-id="2ee3f-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2ee3f-154">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="2ee3f-155">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="2ee3f-155">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
