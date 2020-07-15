---
title: DataSets, DataTables ve DataViews
description: Tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimi olan ADO.NET veri kümesiyle çalışmanın birkaç yolunu öğrenin.
ms.date: 03/30/2017
ms.assetid: 6d4c4b69-8919-4224-8a65-6cca1c61b48f
ms.openlocfilehash: 53e12f701b9be1938d62f46bbeb6e63d95c03386
ms.sourcegitcommit: e7748001b1cee80ced691d8a76ca814c0b02dd9b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86374513"
---
# <a name="datasets-datatables-and-dataviews"></a><span data-ttu-id="86e40-103">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="86e40-103">DataSets, DataTables, and DataViews</span></span>

<span data-ttu-id="86e40-104">ADO.NET, <xref:System.Data.DataSet> içerdiği verilerin kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="86e40-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model regardless of the source of the data it contains.</span></span> <span data-ttu-id="86e40-105">Bir, <xref:System.Data.DataSet> verileri içeren tablolar ve tablolar arasındaki ilişkiler dahil olmak üzere tüm veri kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="86e40-105">A <xref:System.Data.DataSet> represents a complete set of data including the tables that contain, order, and constrain the data, as well as the relationships between the tables.</span></span>  
  
<span data-ttu-id="86e40-106">Bağımsız olarak veya birleşimine uygulanabilecek bir ile çalışmanın birkaç yolu vardır <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="86e40-106">There are several ways of working with a <xref:System.Data.DataSet>, which can be applied independently or in combination.</span></span> <span data-ttu-id="86e40-107">Şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="86e40-107">You can:</span></span>  
  
- <span data-ttu-id="86e40-108">Programlı olarak <xref:System.Data.DataTable> bir, <xref:System.Data.DataRelation> ve <xref:System.Data.Constraint> içinde ve <xref:System.Data.DataSet> tabloları verilerle doldurma.</span><span class="sxs-lookup"><span data-stu-id="86e40-108">Programmatically create a <xref:System.Data.DataTable>, <xref:System.Data.DataRelation>, and <xref:System.Data.Constraint> within a <xref:System.Data.DataSet> and populate the tables with data.</span></span>  
  
- <span data-ttu-id="86e40-109">' İ <xref:System.Data.DataSet> kullanarak var olan bir ilişkisel veri kaynağından veri tabloları ile doldurun `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="86e40-109">Populate the <xref:System.Data.DataSet> with tables of data from an existing relational data source using a `DataAdapter`.</span></span>  
  
- <span data-ttu-id="86e40-110">XML kullanarak içerikleri yükleyin ve kalıcı hale getirin <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="86e40-110">Load and persist the <xref:System.Data.DataSet> contents using XML.</span></span> <span data-ttu-id="86e40-111">Daha fazla bilgi için bkz. [veri KÜMESINDE XML kullanma](using-xml-in-a-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="86e40-111">For more information, see [Using XML in a DataSet](using-xml-in-a-dataset.md).</span></span>  
  
<span data-ttu-id="86e40-112">Türü kesin belirlenmiş bir <xref:System.Data.DataSet> XML Web hizmeti kullanılarak da taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86e40-112">A strongly typed <xref:System.Data.DataSet> can also be transported using an XML Web service.</span></span> <span data-ttu-id="86e40-113">Tasarımı, <xref:System.Data.DataSet> XML Web Hizmetleri kullanarak verileri aktarmak için ideal hale getirir.</span><span class="sxs-lookup"><span data-stu-id="86e40-113">The design of the <xref:System.Data.DataSet> makes it ideal for transporting data using XML Web services.</span></span> <span data-ttu-id="86e40-114">XML Web hizmetlerine genel bakış için bkz. [XML Web Hizmetleri 'Ne genel bakış](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="86e40-114">For an overview of XML Web services, see [XML Web Services Overview](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w9fdtx28(v=vs.100)).</span></span> <span data-ttu-id="86e40-115"><xref:System.Data.DataSet>XML Web hizmetinden alınan bir örnek için bkz. [XML Web hizmetinden veri kümesi](consuming-a-dataset-from-an-xml-web-service.md)kullanma.</span><span class="sxs-lookup"><span data-stu-id="86e40-115">For an example of consuming a <xref:System.Data.DataSet> from an XML Web service, see [Consuming a DataSet from an XML Web Service](consuming-a-dataset-from-an-xml-web-service.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="86e40-116">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="86e40-116">In this section</span></span>

 [<span data-ttu-id="86e40-117">Güvenlik kılavuzu</span><span class="sxs-lookup"><span data-stu-id="86e40-117">Security guidance</span></span>](security-guidance.md)  
 <span data-ttu-id="86e40-118">Ve için Güvenlik Kılavuzu <xref:System.Data.DataSet> sağlar <xref:System.Data.DataTable> .</span><span class="sxs-lookup"><span data-stu-id="86e40-118">Provides security guidance for <xref:System.Data.DataSet> and <xref:System.Data.DataTable>.</span></span>

 [<span data-ttu-id="86e40-119">DataSet Oluşturma</span><span class="sxs-lookup"><span data-stu-id="86e40-119">Creating a DataSet</span></span>](creating-a-dataset.md)  
 <span data-ttu-id="86e40-120">Bir örneğini oluşturmak için söz dizimini açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="86e40-120">Describes the syntax for creating an instance of a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="86e40-121">DataSet’e DataTable Ekleme</span><span class="sxs-lookup"><span data-stu-id="86e40-121">Adding a DataTable to a DataSet</span></span>](adding-a-datatable-to-a-dataset.md)  
 <span data-ttu-id="86e40-122">' A tablo ve sütun oluşturmayı ve eklemeyi açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="86e40-122">Describes how to create and add tables and columns to a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="86e40-123">DataRelations Ekleme</span><span class="sxs-lookup"><span data-stu-id="86e40-123">Adding DataRelations</span></span>](adding-datarelations.md)  
 <span data-ttu-id="86e40-124">İçindeki tablolar arasında ilişki oluşturmayı açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="86e40-124">Describes how to create relations between tables in a <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="86e40-125">DataRelations İçinde Gezinme</span><span class="sxs-lookup"><span data-stu-id="86e40-125">Navigating DataRelations</span></span>](navigating-datarelations.md)  
 <span data-ttu-id="86e40-126">Bir <xref:System.Data.DataSet> üst-alt ilişkisinin alt veya üst satırlarını döndürmek için içindeki tablolar arasındaki ilişkilerin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86e40-126">Describes how to use the relations between tables in a <xref:System.Data.DataSet> to return the child or parent rows of a parent-child relationship.</span></span>  
  
 [<span data-ttu-id="86e40-127">DataSet İçeriklerini Birleştirme</span><span class="sxs-lookup"><span data-stu-id="86e40-127">Merging DataSet Contents</span></span>](merging-dataset-contents.md)  
 <span data-ttu-id="86e40-128">Bir <xref:System.Data.DataSet> , <xref:System.Data.DataTable> veya dizisinin içeriğinin başka bir, veya dizisinin içeriğini <xref:System.Data.DataRow> nasıl birleştirebileceğinizi açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="86e40-128">Describes how to merge the contents of one <xref:System.Data.DataSet>, <xref:System.Data.DataTable>, or <xref:System.Data.DataRow> array into another <xref:System.Data.DataSet>.</span></span>  
  
 [<span data-ttu-id="86e40-129">DataSet İçeriklerini Kopyalama</span><span class="sxs-lookup"><span data-stu-id="86e40-129">Copying DataSet Contents</span></span>](copying-dataset-contents.md)  
 <span data-ttu-id="86e40-130">Bir öğesinin, <xref:System.Data.DataSet> belirtilen verilerin yanı sıra şema içerebilen bir kopyasının nasıl oluşturulduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="86e40-130">Describes how to create a copy of a <xref:System.Data.DataSet> that can contain schema as well as specified data.</span></span>  
  
 [<span data-ttu-id="86e40-131">DataSet Olaylarını İşleme</span><span class="sxs-lookup"><span data-stu-id="86e40-131">Handling DataSet Events</span></span>](handling-dataset-events.md)  
 <span data-ttu-id="86e40-132">' A ait olayları <xref:System.Data.DataSet> ve bunların nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86e40-132">Describes the events of a <xref:System.Data.DataSet> and how to use them.</span></span>  
  
 [<span data-ttu-id="86e40-133">Türü Belirtilmiş DataSets</span><span class="sxs-lookup"><span data-stu-id="86e40-133">Typed DataSets</span></span>](typed-datasets.md)  
 <span data-ttu-id="86e40-134">Türü nelerin <xref:System.Data.DataSet> olduğunu ve nasıl oluşturulacağını ve kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86e40-134">Discusses what a typed <xref:System.Data.DataSet> is and how to create and use it.</span></span>  
  
 [<span data-ttu-id="86e40-135">DataTables</span><span class="sxs-lookup"><span data-stu-id="86e40-135">DataTables</span></span>](datatables.md)  
 <span data-ttu-id="86e40-136">Oluşturma <xref:System.Data.DataTable> , şema tanımlama ve verileri işleme işlemlerinin nasıl yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86e40-136">Describes how to create a <xref:System.Data.DataTable>, define the schema, and manipulate data.</span></span>  
  
 [<span data-ttu-id="86e40-137">DataTableReaders</span><span class="sxs-lookup"><span data-stu-id="86e40-137">DataTableReaders</span></span>](datatablereaders.md)  
 <span data-ttu-id="86e40-138">Oluşturmayı ve kullanmayı açıklar <xref:System.Data.DataTableReader> .</span><span class="sxs-lookup"><span data-stu-id="86e40-138">Describes how to create and use a <xref:System.Data.DataTableReader>.</span></span>  
  
 [<span data-ttu-id="86e40-139">DataViews</span><span class="sxs-lookup"><span data-stu-id="86e40-139">DataViews</span></span>](dataviews.md)  
 <span data-ttu-id="86e40-140">Oluşturma ve bunlarla çalışmayı ve olayları nasıl kullanacağınızı açıklar `DataViews` <xref:System.Data.DataView> .</span><span class="sxs-lookup"><span data-stu-id="86e40-140">Describes how to create and work with `DataViews` and work with <xref:System.Data.DataView> events.</span></span>  
  
 [<span data-ttu-id="86e40-141">DataSet içinde XML kullanma</span><span class="sxs-lookup"><span data-stu-id="86e40-141">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="86e40-142"><xref:System.Data.DataSet>Bir veri kaynağı olarak XML ile nasıl etkileşime gireceğini açıklar ve BIR XML verisi olarak içeriğini yükleme ve kalıcı hale getirme de dahildir <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="86e40-142">Describes how the <xref:System.Data.DataSet> interacts with XML as a data source, including loading and persisting the contents of a <xref:System.Data.DataSet> as XML data.</span></span>  
  
 [<span data-ttu-id="86e40-143">XML Web Hizmetinden DataSet Kullanma</span><span class="sxs-lookup"><span data-stu-id="86e40-143">Consuming a DataSet from an XML Web Service</span></span>](consuming-a-dataset-from-an-xml-web-service.md)  
 <span data-ttu-id="86e40-144">Verileri aktarmak için kullanan bir XML Web hizmeti oluşturmayı açıklar <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="86e40-144">Describes how to create an XML Web service that uses a <xref:System.Data.DataSet> to transport data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="86e40-145">İlgili bölümler</span><span class="sxs-lookup"><span data-stu-id="86e40-145">Related sections</span></span>

 [<span data-ttu-id="86e40-146">ADO.NET’teki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="86e40-146">What's New in ADO.NET</span></span>](../whats-new.md)  
 <span data-ttu-id="86e40-147">ADO.NET ' de yeni olan özellikleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="86e40-147">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="86e40-148">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="86e40-148">ADO.NET Overview</span></span>](../ado-net-overview.md)  
 <span data-ttu-id="86e40-149">ADO.NET 'in tasarımına ve bileşenlerine bir giriş sağlar.</span><span class="sxs-lookup"><span data-stu-id="86e40-149">Provides an introduction to the design and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="86e40-150">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="86e40-150">Populating a DataSet from a DataAdapter</span></span>](../populating-a-dataset-from-a-dataadapter.md)  
 <span data-ttu-id="86e40-151">Veri kaynağından veri içeren bir veri **kümesinin** nasıl yükleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="86e40-151">Describes how to load a **DataSet** with data from a data source.</span></span>  
  
 [<span data-ttu-id="86e40-152">Veri Kaynaklarını DataAdapters ile Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="86e40-152">Updating Data Sources with DataAdapters</span></span>](../updating-data-sources-with-dataadapters.md)  
 <span data-ttu-id="86e40-153">Veri **kümesindeki** verilerde yapılan değişikliklerin veri kaynağına geri nasıl çözümleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="86e40-153">Describes how to resolve changes to the data in a **DataSet** back to the data source.</span></span>  
  
 [<span data-ttu-id="86e40-154">DataSet’e Var Olan Kısıtlamaları Ekleme</span><span class="sxs-lookup"><span data-stu-id="86e40-154">Adding Existing Constraints to a DataSet</span></span>](../adding-existing-constraints-to-a-dataset.md)  
 <span data-ttu-id="86e40-155">Bir veri **kümesinin** birincil anahtar bilgileri ile bir veri kaynağından nasıl doldurulacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="86e40-155">Describes how to populate a **DataSet** with primary key information from a data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86e40-156">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86e40-156">See also</span></span>

- [<span data-ttu-id="86e40-157">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="86e40-157">ADO.NET</span></span>](../index.md)
- [<span data-ttu-id="86e40-158">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="86e40-158">ADO.NET Overview</span></span>](../ado-net-overview.md)
