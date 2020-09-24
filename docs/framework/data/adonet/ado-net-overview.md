---
title: Genel Bakış
description: Daha ayrıntılı açıklamalar ve örnekler için .NET Framework 'de ADO.NET ' e genel bakışı okuyun ve kaynaklar hakkında bilgi edinin.
ms.date: 03/30/2017
ms.assetid: ee3bc1d8-11db-4be4-89eb-c708cf04117d
ms.openlocfilehash: 459e4a548a4d1358b196dc41ec495921833728d4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153501"
---
# <a name="adonet-overview"></a><span data-ttu-id="4e76f-103">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4e76f-103">ADO.NET Overview</span></span>

<span data-ttu-id="4e76f-104">ADO.NET, SQL Server ve XML gibi veri kaynaklarına ve OLE DB ve ODBC aracılığıyla sunulan veri kaynaklarına tutarlı erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-104">ADO.NET provides consistent access to data sources such as SQL Server and XML, and to data sources exposed through OLE DB and ODBC.</span></span> <span data-ttu-id="4e76f-105">Veri paylaşımı tüketici uygulamaları, bu veri kaynaklarına bağlanmak ve içerdikleri verileri almak, işlemek ve güncelleştirmek için ADO.NET kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="4e76f-105">Data-sharing consumer applications can use ADO.NET to connect to these data sources and retrieve, handle, and update the data that they contain.</span></span>  
  
 <span data-ttu-id="4e76f-106">ADO.NET veri işlemesini, ayrı ayrı veya art arda kullanılabilecek ayrı bileşenlere ayırır.</span><span class="sxs-lookup"><span data-stu-id="4e76f-106">ADO.NET separates data access from data manipulation into discrete components that can be used separately or in tandem.</span></span> <span data-ttu-id="4e76f-107">ADO.NET, bir veritabanına bağlanmak, komutları yürütmek ve sonuçları almak için .NET Framework veri sağlayıcıları içerir.</span><span class="sxs-lookup"><span data-stu-id="4e76f-107">ADO.NET includes .NET Framework data providers for connecting to a database, executing commands, and retrieving results.</span></span> <span data-ttu-id="4e76f-108">Bu sonuçlar doğrudan işlenirler, bir ADO.NET nesnesine yerleştirilmiş, <xref:System.Data.DataSet> birden fazla kaynaktaki verilerle birleştirilmiş veya katmanlar arasında geçilen bir nesnesine yerleştirildi.</span><span class="sxs-lookup"><span data-stu-id="4e76f-108">Those results are either processed directly, placed in an ADO.NET <xref:System.Data.DataSet> object in order to be exposed to the user in an ad hoc manner, combined with data from multiple sources, or passed between tiers.</span></span> <span data-ttu-id="4e76f-109">Bu `DataSet` nesne ayrıca bir .NET Framework veri sağlayıcısından bağımsız olarak, uygulamadaki yerel verileri yönetmek için veya XML 'den kaynaklıdır.</span><span class="sxs-lookup"><span data-stu-id="4e76f-109">The `DataSet` object can also be used independently of a .NET Framework data provider to manage data local to the application or sourced from XML.</span></span>  
  
 <span data-ttu-id="4e76f-110">ADO.NET sınıfları System.Data.dll bulunur ve System.Xml.dll bulunan XML sınıflarıyla tümleşiktir.</span><span class="sxs-lookup"><span data-stu-id="4e76f-110">The ADO.NET classes are found in System.Data.dll, and are integrated with the XML classes found in System.Xml.dll.</span></span> <span data-ttu-id="4e76f-111">Veritabanına bağlanan, verileri alan ve ardından bir konsol penceresinde görüntüleyen örnek kod için, bkz. [ADO.net Code Examples](ado-net-code-examples.md).</span><span class="sxs-lookup"><span data-stu-id="4e76f-111">For sample code that connects to a database, retrieves data from it, and then displays that data in a console window, see [ADO.NET Code Examples](ado-net-code-examples.md).</span></span>  
  
 <span data-ttu-id="4e76f-112">ADO.NET, yerel bileşen nesne modeli (COM) geliştiricilerine ActiveX Data Objects (ADO) tarafından sağlanan işlevselliğe benzer şekilde yönetilen kod yazan geliştiricilere işlevsellik sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-112">ADO.NET provides functionality to developers who write managed code similar to the functionality provided to native component object model (COM) developers by ActiveX Data Objects (ADO).</span></span> <span data-ttu-id="4e76f-113">.NET uygulamalarınızda verilere erişmek için ADO değil ADO.NET kullanmanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="4e76f-113">We recommend that you use ADO.NET, not ADO, for accessing data in your .NET applications.</span></span>  
  
 <span data-ttu-id="4e76f-114">ADO.NET, .NET Framework içinde en doğrudan veri erişimi yöntemini sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-114">ADO.NET provides the most direct method of data access within the .NET Framework.</span></span> <span data-ttu-id="4e76f-115">Uygulamaların temel depolama modeli yerine kavramsal bir modelde çalışmasına izin veren üst düzey bir soyutlama için, bkz. [ADO.NET Entity Framework](./ef/index.md).</span><span class="sxs-lookup"><span data-stu-id="4e76f-115">For a higher-level abstraction that allows applications to work against a conceptual model instead of the underlying storage model, see the [ADO.NET Entity Framework](./ef/index.md).</span></span>  
  
 <span data-ttu-id="4e76f-116">**Gizlilik bildirimi**: System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll ve System.Data.DataSetExtensions.dll derlemeleri bir kullanıcının özel verileri ile özel olmayan veriler arasında ayrım yapmazlar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-116">**Privacy Statement**: The System.Data.dll, System.Data.Design.dll, System.Data.OracleClient.dll, System.Data.SqlXml.dll, System.Data.Linq.dll, System.Data.SqlServerCe.dll, and System.Data.DataSetExtensions.dll assemblies do not distinguish between a user's private data and non-private data.</span></span>  <span data-ttu-id="4e76f-117">Bu derlemeler kullanıcının özel verilerini toplamaz, depolamaz veya taşımıyor.</span><span class="sxs-lookup"><span data-stu-id="4e76f-117">These assemblies do not collect, store, or transport any user's private data.</span></span> <span data-ttu-id="4e76f-118">Ancak, üçüncü taraf uygulamalar bu derlemeleri kullanarak bir kullanıcının özel verilerini toplayabilir, saklayabilir veya taşıbilirler.</span><span class="sxs-lookup"><span data-stu-id="4e76f-118">However, third-party applications might collect, store, or transport a user's private data using these assemblies.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e76f-119">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4e76f-119">In This Section</span></span>  

 [<span data-ttu-id="4e76f-120">ADO.NET Mimarisi</span><span class="sxs-lookup"><span data-stu-id="4e76f-120">ADO.NET Architecture</span></span>](ado-net-architecture.md)  
 <span data-ttu-id="4e76f-121">ADO.NET mimarisi ve bileşenlerine genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-121">Provides an overview of the architecture and components of ADO.NET.</span></span>  
  
 [<span data-ttu-id="4e76f-122">ADO.NET Teknoloji Seçenekleri ve Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="4e76f-122">ADO.NET Technology Options and Guidelines</span></span>](ado-net-technology-options-and-guidelines.md)  
 <span data-ttu-id="4e76f-123">Varlık veri platformuna dahil olan ürünleri ve teknolojileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-123">Describes the products and technologies included with the Entity Data Platform.</span></span>  
  
 [<span data-ttu-id="4e76f-124">LINQ ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4e76f-124">LINQ and ADO.NET</span></span>](linq-and-ado-net.md)  
 <span data-ttu-id="4e76f-125">Dil ile tümleşik sorgunun (LINQ) ADO.NET 'de nasıl uygulandığını ve ilgili konuların bağlantılarını sağladığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-125">Describes how Language-Integrated Query (LINQ) is implemented in ADO.NET and provides links to relevant topics.</span></span>  
  
 [<span data-ttu-id="4e76f-126">.NET Framework Veri Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="4e76f-126">.NET Framework Data Providers</span></span>](data-providers.md)  
 <span data-ttu-id="4e76f-127">.NET Framework veri sağlayıcısının tasarımına ve ADO.NET ile birlikte bulunan .NET Framework veri sağlayıcılarına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-127">Provides an overview of the design of the .NET Framework data provider and of the .NET Framework data providers that are included with ADO.NET.</span></span>  
  
 [<span data-ttu-id="4e76f-128">ADO.NET Veri Kümeleri</span><span class="sxs-lookup"><span data-stu-id="4e76f-128">ADO.NET DataSets</span></span>](ado-net-datasets.md)  
 <span data-ttu-id="4e76f-129">Tasarıma ve bileşenlere genel bir bakış sağlar `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="4e76f-129">Provides an overview of the `DataSet` design and components.</span></span>  
  
 [<span data-ttu-id="4e76f-130">ADO.NET’te Yan Yana Yürütme</span><span class="sxs-lookup"><span data-stu-id="4e76f-130">Side-by-Side Execution in ADO.NET</span></span>](side-by-side-execution.md)  
 <span data-ttu-id="4e76f-131">ADO.NET sürümlerindeki farklılıkları ve yan yana yürütme ve uygulama uyumluluğuna ilişkin etkilerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-131">Discusses differences in ADO.NET versions and their effect on side-by-side execution and application compatibility.</span></span>  
  
 [<span data-ttu-id="4e76f-132">ADO.NET Kod Örnekleri</span><span class="sxs-lookup"><span data-stu-id="4e76f-132">ADO.NET Code Examples</span></span>](ado-net-code-examples.md)  
 <span data-ttu-id="4e76f-133">ADO.NET veri sağlayıcılarını kullanarak veri alan kod örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-133">Provides code samples that retrieve data using the ADO.NET data providers.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4e76f-134">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="4e76f-134">Related Sections</span></span>  

 [<span data-ttu-id="4e76f-135">ADO.NET’teki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="4e76f-135">What's New in ADO.NET</span></span>](whats-new.md)  
 <span data-ttu-id="4e76f-136">ADO.NET ' de yeni olan özellikleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="4e76f-136">Introduces features that are new in ADO.NET.</span></span>  
  
 [<span data-ttu-id="4e76f-137">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="4e76f-137">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)  
 <span data-ttu-id="4e76f-138">ADO.NET kullanılırken güvenli kodlama uygulamalarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-138">Describes secure coding practices when using ADO.NET.</span></span>  
  
 [<span data-ttu-id="4e76f-139">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="4e76f-139">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)  
 <span data-ttu-id="4e76f-140">.NET Framework veri türleri ve .NET Framework veri sağlayıcıları arasındaki veri türü eşlemelerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-140">Describes data type mappings between .NET Framework data types and the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="4e76f-141">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="4e76f-141">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)  
 <span data-ttu-id="4e76f-142">Bir veri kaynağına bağlanmayı, verileri almayı ve verileri değiştirmeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="4e76f-142">Describes how to connect to a data source, retrieve data, and modify data.</span></span> <span data-ttu-id="4e76f-143">Bu `DataReaders` ve içerir `DataAdapters` .</span><span class="sxs-lookup"><span data-stu-id="4e76f-143">This includes `DataReaders` and `DataAdapters`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e76f-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e76f-144">See also</span></span>

- [<span data-ttu-id="4e76f-145">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4e76f-145">ADO.NET</span></span>](index.md)
- [<span data-ttu-id="4e76f-146">Visual Studio'da verilere erişime</span><span class="sxs-lookup"><span data-stu-id="4e76f-146">Accessing data in Visual Studio</span></span>](/visualstudio/data-tools/accessing-data-in-visual-studio)
