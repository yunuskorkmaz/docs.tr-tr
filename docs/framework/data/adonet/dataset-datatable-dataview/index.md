---
title: "Veri kümeleri, DataTable ve DataView"
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
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 642a81b926262fb8ea95234d90e4c1a0c49ea96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="59222-102">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="59222-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="59222-103">ADO.NET <xref:System.Data.DataSet> içerdiği veri kaynağını bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlar veri bellekte gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="59222-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="59222-104">A <xref:System.Data.DataSet> sipariş ve tablolar arasındaki ilişkileri yanı sıra, verileri sınırlamak içeren tablolar dahil olmak üzere verileri eksiksiz bir kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="59222-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="59222-105">İle çalışmaya ilişkin birkaç yolu vardır bir <xref:System.Data.DataSet>, hangi uygulanabilir bağımsız olarak veya birlikte.</span><span class="sxs-lookup"><span data-stu-id="59222-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="59222-106">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="59222-106">You can:</span></span>  
  
-   <span data-ttu-id="59222-107">Program aracılığıyla oluşturma bir <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, ve <xref:System.Data.Constraint> içinde bir <xref:System.Data.DataSet> ve veri tablolarıyla doldurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="59222-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
-   <span data-ttu-id="59222-108">Doldurmak <xref:System.Data.DataSet> var olan bir ilişkisel veri kaynağı kullanılarak verileri tablolar ile bir `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="59222-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
-   <span data-ttu-id="59222-109">Yük ve kalıcı <xref:System.Data.DataSet> XML kullanarak içeriği.</span><span class="sxs-lookup"><span data-stu-id="59222-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="59222-110">Daha fazla bilgi için bkz: [XML kullanarak bir veri kümesinde](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="59222-110">For more information, see [Using XML in a DataSet](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="59222-111">Kesin türü belirtilmiş <xref:System.Data.DataSet> bir XML Web hizmetini kullanarak da taşınabilen.</span><span class="sxs-lookup"><span data-stu-id="59222-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="59222-112">Tasarımını <xref:System.Data.DataSet> XML Web Hizmetleri kullanarak veri taşıma için ideal hale getirir.</span><span class="sxs-lookup"><span data-stu-id="59222-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="59222-113">XML Web Hizmetleri genel bakış için bkz: [XML Web Hizmetleri genel bakış](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span><span class="sxs-lookup"><span data-stu-id="59222-113">For an overview of XML Web services, see [XML Web Services Overview](http://msdn.microsoft.com/en-us/9db0c7b8-bca6-462b-9be5-f5f9a7f05a4d).</span></span> <span data-ttu-id="59222-114">Kullanma örneği için bir <xref:System.Data.DataSet> bir XML Web hizmetinden bkz [bir XML Web hizmetinden veri kümesi kullanma](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="59222-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="59222-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="59222-115">In This Section</span></span>  
 [<span data-ttu-id="59222-116">Bir veri kümesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="59222-116">Creating a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-a-dataset.md)  
 <span data-ttu-id="59222-117">Örneği oluşturmak için söz dizimi açıklanmıştır bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="59222-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="59222-118">DataTable bir veri kümesine ekleme</span><span class="sxs-lookup"><span data-stu-id="59222-118">Adding a DataTable to a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="59222-119">Oluşturma ve tablolar ve sütunlar ekleme açıklar bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="59222-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="59222-120">DataRelation ekleme</span><span class="sxs-lookup"><span data-stu-id="59222-120">Adding DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md)  
 <span data-ttu-id="59222-121">Tablolar arasındaki ilişkileri oluşturmayı açıklar bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="59222-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="59222-122">DataRelation gezinme</span><span class="sxs-lookup"><span data-stu-id="59222-122">Navigating DataRelations</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md)  
 <span data-ttu-id="59222-123">Tablolar arasındaki ilişkileri kullanmayı açıklar bir <xref:System.Data.DataSet> üst-alt ilişkinin bir alt veya üst satır döndürülecek.</span><span class="sxs-lookup"><span data-stu-id="59222-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="59222-124">Veri kümesi içeriği birleştirme</span><span class="sxs-lookup"><span data-stu-id="59222-124">Merging DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/merging-dataset-contents.md)  
 <span data-ttu-id="59222-125">İçeriği bir birleştirme açıklar <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, veya <xref:System.Data.DataRow> başka diziye <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="59222-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="59222-126">Veri kümesi içeriği kopyalama</span><span class="sxs-lookup"><span data-stu-id="59222-126">Copying DataSet Contents</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/copying-dataset-contents.md)  
 <span data-ttu-id="59222-127">Bir kopyasını oluşturmayı açıklar bir <xref:System.Data.DataSet> belirtilen veri yanı sıra şema içerebilir.</span><span class="sxs-lookup"><span data-stu-id="59222-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="59222-128">Veri kümesi olayları işleme</span><span class="sxs-lookup"><span data-stu-id="59222-128">Handling DataSet Events</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-dataset-events.md)  
 <span data-ttu-id="59222-129">Olayları açıklayan bir <xref:System.Data.DataSet> ve bunları nasıl kullanacağınızı.</span><span class="sxs-lookup"><span data-stu-id="59222-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="59222-130">Yazılan veri kümeleri</span><span class="sxs-lookup"><span data-stu-id="59222-130">Typed DataSets</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)  
 <span data-ttu-id="59222-131">Hangi yazılmış anlatılmaktadır <xref:System.Data.DataSet> olduğu ve nasıl oluşturulacağı ve bunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="59222-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="59222-132">DataTables</span><span class="sxs-lookup"><span data-stu-id="59222-132">DataTables</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)  
 <span data-ttu-id="59222-133">Nasıl oluşturulacağını açıklar bir <xref:System.Data.DataTable>Şeması Tanımlama ve verileri işlemek.</span><span class="sxs-lookup"><span data-stu-id="59222-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="59222-134">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="59222-134">DataTableReaders</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatablereaders.md)  
 <span data-ttu-id="59222-135">Oluşturma ve kullanma açıklar bir <xref:System.Data.DataTableReader>.</span><span class="sxs-lookup"><span data-stu-id="59222-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="59222-136">DataView</span><span class="sxs-lookup"><span data-stu-id="59222-136">DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)  
 <span data-ttu-id="59222-137">Oluşturma ve bunlarla çalışmak açıklar `DataViews` ve bunlarla çalışmak <xref:System.Data.DataView> olaylar.</span><span class="sxs-lookup"><span data-stu-id="59222-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="59222-138">Bir veri kümesini XML kullanma</span><span class="sxs-lookup"><span data-stu-id="59222-138">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="59222-139">Açıklar nasıl <xref:System.Data.DataSet> yükleme ve içeriği kalıcı yapma dahil olmak üzere bir veri kaynağı olarak XML ile etkileşime giren bir <xref:System.Data.DataSet> XML verileri olarak.</span><span class="sxs-lookup"><span data-stu-id="59222-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="59222-140">XML Web hizmetinden veri kümesi kullanma</span><span class="sxs-lookup"><span data-stu-id="59222-140">Consuming a DataSet from an XML Web Service</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="59222-141">Kullanan XML Web hizmeti oluşturmayı açıklar bir <xref:System.Data.DataSet> Aktarım verileri.</span><span class="sxs-lookup"><span data-stu-id="59222-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="59222-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="59222-142">Related Sections</span></span>  
 [<span data-ttu-id="59222-143">ADO.NET yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="59222-143">What's New in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/whats-new.md)  
 <span data-ttu-id="59222-144">ADO.NET yeni özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="59222-144">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="59222-145">ADO.NET genel bakış</span><span class="sxs-lookup"><span data-stu-id="59222-145">ADO.NET Overview</span></span>](../../../../../docs/framework/data/adonet/ado-net-overview.md)  
 <span data-ttu-id="59222-146">Tasarım ve ADO.NET bileşenlerinin bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="59222-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="59222-147">DataAdapter kümesinden doldurma</span><span class="sxs-lookup"><span data-stu-id="59222-147">Populating a DataSet from a DataAdapter</span></span>](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="59222-148">Nasıl yükleneceğini açıklayan bir **DataSet** bir veri kaynağı ile.</span><span class="sxs-lookup"><span data-stu-id="59222-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="59222-149">Veri kaynakları ile DataAdapters güncelleştiriliyor</span><span class="sxs-lookup"><span data-stu-id="59222-149">Updating Data Sources with DataAdapters</span></span>](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="59222-150">Verilerde değişiklik çözümlemeyi açıklar bir **DataSet** veri kaynağına geri.</span><span class="sxs-lookup"><span data-stu-id="59222-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="59222-151">Varolan kısıtlamaları bir veri kümesine ekleme</span><span class="sxs-lookup"><span data-stu-id="59222-151">Adding Existing Constraints to a DataSet</span></span>](../../../../../docs/framework/data/adonet/adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="59222-152">Doldurmak nasıl açıklar bir **DataSet** bir veri kaynağından birincil anahtar bilgileri.</span><span class="sxs-lookup"><span data-stu-id="59222-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59222-153">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="59222-153">See Also</span></span>  
 [<span data-ttu-id="59222-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="59222-154">ADO.NET</span></span>](../../../../../docs/framework/data/adonet/index.md)  
 [<span data-ttu-id="59222-155">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="59222-155">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
