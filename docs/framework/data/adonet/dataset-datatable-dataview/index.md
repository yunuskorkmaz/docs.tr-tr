---
title: DataSets, DataTables ve DataViews
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 4b5e81f415685d6ee3529c7e4f9d389e8017427e
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203641"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="083c6-102">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="083c6-102">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="083c6-103">ADO.net <xref:System.Data.DataSet> , içerdiği verilerin kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="083c6-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="083c6-104">Bir <xref:System.Data.DataSet> , verileri içeren tablolar ve tablolar arasındaki ilişkiler dahil olmak üzere tüm veri kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="083c6-104">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="083c6-105">Bağımsız olarak veya birleşimine uygulanabilecek bir <xref:System.Data.DataSet>ile çalışmanın birkaç yolu vardır.</span><span class="sxs-lookup"><span data-stu-id="083c6-105">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="083c6-106">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="083c6-106">You can:</span></span>  
  
- <span data-ttu-id="083c6-107">Programlı olarak <xref:System.Data.DataRelation>bir <xref:System.Data.DataTable> <xref:System.Data.Constraint> , veiçindevetablolarıverilerledoldurma.<xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="083c6-107">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="083c6-108">' İ kullanarak var olan bir `DataAdapter`ilişkisel veri kaynağından veri tabloları iledoldurun.<xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="083c6-108">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="083c6-109">XML kullanarak <xref:System.Data.DataSet> içerikleri yükleyin ve kalıcı hale getirin.</span><span class="sxs-lookup"><span data-stu-id="083c6-109">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="083c6-110">Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="083c6-110">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="083c6-111">Türü kesin belirlenmiş <xref:System.Data.DataSet> bir XML Web hizmeti kullanılarak da taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="083c6-111">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="083c6-112">Tasarımı, XML Web <xref:System.Data.DataSet> Hizmetleri kullanarak verileri aktarmak için ideal hale getirir.</span><span class="sxs-lookup"><span data-stu-id="083c6-112">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="083c6-113">XML Web hizmetlerine genel bakış için bkz. [XML Web Hizmetleri 'Ne genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="083c6-113">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="083c6-114">XML Web hizmetinden alınan bir <xref:System.Data.DataSet> örnek için bkz. [XML Web hizmetinden veri kümesi](consuming-a-dataset-from-an-xml-web-service.md)kullanma.</span><span class="sxs-lookup"><span data-stu-id="083c6-114">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="083c6-115">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="083c6-115">In This Section</span></span>  
 [<span data-ttu-id="083c6-116">DataSet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="083c6-116">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="083c6-117">Bir <xref:System.Data.DataSet>örneğini oluşturmak için söz dizimini açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-117">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="083c6-118">DataSet’e DataTable Ekleme</span><span class="sxs-lookup"><span data-stu-id="083c6-118">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="083c6-119">' A <xref:System.Data.DataSet>tablo ve sütun oluşturmayı ve eklemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-119">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="083c6-120">DataRelations Ekleme</span><span class="sxs-lookup"><span data-stu-id="083c6-120">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="083c6-121">İçindeki tablolar arasında ilişki oluşturmayı açıklar <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="083c6-121">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="083c6-122">DataRelations İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="083c6-122">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="083c6-123">Bir <xref:System.Data.DataSet> üst-alt ilişkisinin alt veya üst satırlarını döndürmek için içindeki tablolar arasındaki ilişkilerin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-123">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="083c6-124">DataSet İçeriklerini Birleştirme</span><span class="sxs-lookup"><span data-stu-id="083c6-124">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="083c6-125">Bir <xref:System.Data.DataSet>, veya dizisinin içeriğinin başka bir <xref:System.Data.DataSet>, <xref:System.Data.DataTable>veya <xref:System.Data.DataRow> dizisinin içeriğini nasıl birleştirebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-125">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="083c6-126">DataSet İçeriklerini Kopyalama</span><span class="sxs-lookup"><span data-stu-id="083c6-126">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="083c6-127">Bir <xref:System.Data.DataSet> öğesinin, belirtilen verilerin yanı sıra şema içerebilen bir kopyasının nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-127">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="083c6-128">DataSet Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="083c6-128">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="083c6-129">' A <xref:System.Data.DataSet> ait olayları ve bunların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-129">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="083c6-130">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="083c6-130">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="083c6-131">Türü <xref:System.Data.DataSet> nelerin olduğunu ve nasıl oluşturulacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-131">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="083c6-132">DataTables</span><span class="sxs-lookup"><span data-stu-id="083c6-132">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="083c6-133">Oluşturma <xref:System.Data.DataTable>, şema tanımlama ve verileri işleme işlemlerinin nasıl yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-133">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="083c6-134">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="083c6-134">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="083c6-135">Oluşturmayı ve kullanmayı <xref:System.Data.DataTableReader>açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-135">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="083c6-136">DataViews</span><span class="sxs-lookup"><span data-stu-id="083c6-136">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="083c6-137">Oluşturma ve `DataViews` bunlarla çalışmayı ve <xref:System.Data.DataView> olayları nasıl kullanacağınızı açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-137">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="083c6-138">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="083c6-138">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="083c6-139">Bir veri kaynağı <xref:System.Data.DataSet> olarak XML ile nasıl etkileşime gireceğini açıklar ve bir <xref:System.Data.DataSet> XML verisi olarak içeriğini yükleme ve kalıcı hale getirme de dahildir.</span><span class="sxs-lookup"><span data-stu-id="083c6-139">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="083c6-140">XML Web Hizmetinden DataSet Kullanma</span><span class="sxs-lookup"><span data-stu-id="083c6-140">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="083c6-141">Verileri aktarmak için kullanan bir <xref:System.Data.DataSet> XML Web hizmeti oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-141">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="083c6-142">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="083c6-142">Related Sections</span></span>  
 [<span data-ttu-id="083c6-143">ADO.NET’teki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="083c6-143">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="083c6-144">ADO.NET ' de yeni olan özellikleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="083c6-144">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="083c6-145">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="083c6-145">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="083c6-146">ADO.NET 'in tasarımına ve bileşenlerine bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="083c6-146">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="083c6-147">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="083c6-147">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="083c6-148">Veri kaynağından veri içeren bir veri **kümesinin** nasıl yükleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-148">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="083c6-149">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="083c6-149">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="083c6-150">Veri **kümesindeki** verilerde yapılan değişikliklerin veri kaynağına geri nasıl çözümleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-150">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="083c6-151">DataSet’e Var Olan Kısıtlamaları Ekleme</span><span class="sxs-lookup"><span data-stu-id="083c6-151">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="083c6-152">Bir veri **kümesinin** birincil anahtar bilgileri ile bir veri kaynağından nasıl doldurulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="083c6-152">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="083c6-153">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="083c6-153">See also</span></span>

- [<span data-ttu-id="083c6-154">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="083c6-154">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="083c6-155">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="083c6-155">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
