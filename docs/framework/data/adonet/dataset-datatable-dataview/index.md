---
title: DataSets, DataTables ve DataViews
description: Tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimi olan ADO.NET veri kümesiyle çalışmanın birkaç yolunu öğrenin.
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: f6562452261cbc1f7ee36fb264b858646a42e4f5
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286901"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="cf728-103">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="cf728-103">DataSets, DataTables, and DataViews</span></span>
<span data-ttu-id="cf728-104">ADO.NET, <xref:System.Data.DataSet> içerdiği verilerin kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="cf728-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="cf728-105">Bir, <xref:System.Data.DataSet> verileri içeren tablolar ve tablolar arasındaki ilişkiler dahil olmak üzere tüm veri kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="cf728-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
 <span data-ttu-id="cf728-106">Bağımsız olarak veya birleşimine uygulanabilecek bir ile çalışmanın birkaç yolu vardır <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="cf728-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="cf728-107">Seçenekleriniz şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cf728-107">You can:</span></span>  
  
- <span data-ttu-id="cf728-108">Programlı olarak <xref:System.Data.DataTable> bir, <xref:System.Data.DataRelation> ve <xref:System.Data.Constraint> içinde ve <xref:System.Data.DataSet> tabloları verilerle doldurma.</span><span class="sxs-lookup"><span data-stu-id="cf728-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="cf728-109">' İ <xref:System.Data.DataSet> kullanarak var olan bir ilişkisel veri kaynağından veri tabloları ile doldurun `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="cf728-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="cf728-110">XML kullanarak içerikleri yükleyin ve kalıcı hale getirin <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="cf728-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="cf728-111">Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="cf728-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
 <span data-ttu-id="cf728-112">Türü kesin belirlenmiş bir <xref:System.Data.DataSet> XML Web hizmeti kullanılarak da taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cf728-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="cf728-113">Tasarımı, <xref:System.Data.DataSet> XML Web Hizmetleri kullanarak verileri aktarmak için ideal hale getirir.</span><span class="sxs-lookup"><span data-stu-id="cf728-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="cf728-114">XML Web hizmetlerine genel bakış için bkz. [XML Web Hizmetleri 'Ne genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="cf728-114">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="cf728-115"><xref:System.Data.DataSet>XML Web hizmetinden alınan bir örnek için bkz. [XML Web hizmetinden veri kümesi](consuming-a-dataset-from-an-xml-web-service.md)kullanma.</span><span class="sxs-lookup"><span data-stu-id="cf728-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf728-116">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cf728-116">In This Section</span></span>  
 [<span data-ttu-id="cf728-117">DataSet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cf728-117">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="cf728-118">Bir örneğini oluşturmak için söz dizimini açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="cf728-118">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="cf728-119">DataSet’e DataTable Ekleme</span><span class="sxs-lookup"><span data-stu-id="cf728-119">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="cf728-120">' A tablo ve sütun oluşturmayı ve eklemeyi açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="cf728-120">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="cf728-121">DataRelations Ekleme</span><span class="sxs-lookup"><span data-stu-id="cf728-121">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="cf728-122">İçindeki tablolar arasında ilişki oluşturmayı açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="cf728-122">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="cf728-123">DataRelations İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="cf728-123">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="cf728-124">Bir <xref:System.Data.DataSet> üst-alt ilişkisinin alt veya üst satırlarını döndürmek için içindeki tablolar arasındaki ilişkilerin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf728-124">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="cf728-125">DataSet İçeriklerini Birleştirme</span><span class="sxs-lookup"><span data-stu-id="cf728-125">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="cf728-126">Bir <xref:System.Data.DataSet> , <xref:System.Data.DataTable> veya dizisinin içeriğinin başka bir, veya dizisinin içeriğini <xref:System.Data.DataRow> nasıl birleştirebileceğinizi açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="cf728-126">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="cf728-127">DataSet İçeriklerini Kopyalama</span><span class="sxs-lookup"><span data-stu-id="cf728-127">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="cf728-128">Bir öğesinin, <xref:System.Data.DataSet> belirtilen verilerin yanı sıra şema içerebilen bir kopyasının nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf728-128">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="cf728-129">DataSet Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="cf728-129">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="cf728-130">' A ait olayları <xref:System.Data.DataSet> ve bunların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf728-130">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="cf728-131">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="cf728-131">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="cf728-132">Türü nelerin <xref:System.Data.DataSet> olduğunu ve nasıl oluşturulacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf728-132">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="cf728-133">DataTables</span><span class="sxs-lookup"><span data-stu-id="cf728-133">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="cf728-134">Oluşturma <xref:System.Data.DataTable> , şema tanımlama ve verileri işleme işlemlerinin nasıl yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf728-134">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="cf728-135">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="cf728-135">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="cf728-136">Oluşturmayı ve kullanmayı açıklar <xref:System.Data.DataTableReader> .</span><span class="sxs-lookup"><span data-stu-id="cf728-136">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="cf728-137">DataViews</span><span class="sxs-lookup"><span data-stu-id="cf728-137">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="cf728-138">Oluşturma ve bunlarla çalışmayı ve olayları nasıl kullanacağınızı açıklar `DataViews` <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="cf728-138">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="cf728-139">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="cf728-139">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="cf728-140"><xref:System.Data.DataSet>Bir veri kaynağı olarak XML ile nasıl etkileşime gireceğini açıklar ve BIR XML verisi olarak içeriğini yükleme ve kalıcı hale getirme de dahildir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="cf728-140">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="cf728-141">XML Web Hizmetinden DataSet Kullanma</span><span class="sxs-lookup"><span data-stu-id="cf728-141">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="cf728-142">Verileri aktarmak için kullanan bir XML Web hizmeti oluşturmayı açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="cf728-142">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cf728-143">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="cf728-143">Related Sections</span></span>  
 [<span data-ttu-id="cf728-144">ADO.NET’teki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="cf728-144">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="cf728-145">ADO.NET ' de yeni olan özellikleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="cf728-145">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="cf728-146">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cf728-146">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="cf728-147">ADO.NET 'in tasarımına ve bileşenlerine bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="cf728-147">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="cf728-148">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="cf728-148">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="cf728-149">Veri kaynağından veri içeren bir veri **kümesinin** nasıl yükleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf728-149">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="cf728-150">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="cf728-150">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="cf728-151">Veri **kümesindeki** verilerde yapılan değişikliklerin veri kaynağına geri nasıl çözümleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf728-151">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="cf728-152">DataSet’e Var Olan Kısıtlamaları Ekleme</span><span class="sxs-lookup"><span data-stu-id="cf728-152">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="cf728-153">Bir veri **kümesinin** birincil anahtar bilgileri ile bir veri kaynağından nasıl doldurulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="cf728-153">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf728-154">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf728-154">See also</span></span>

- [<span data-ttu-id="cf728-155">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="cf728-155">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="cf728-156">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="cf728-156">ADO.NET Overview</span></span>](../ado-net-overview.md)
