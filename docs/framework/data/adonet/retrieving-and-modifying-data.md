---
title: Verileri alma ve değiştirme
description: .NET Framework, ADO.NET 'deki veri sağlayıcıları, verileri okumak ve güncelleştirmek için bir uygulamayla veri kaynağı arasında bir köprü olarak görev yapar.
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: f916324dc829526a5e6b0078021b09786755f666
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286617"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="c76fd-103">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="c76fd-103">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="c76fd-104">Herhangi bir veritabanı uygulamasının birincil işlevi bir veri kaynağına bağlanıyor ve içerdiği verileri alıyor.</span><span class="sxs-lookup"><span data-stu-id="c76fd-104">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="c76fd-105">ADO.NET veri sağlayıcıları bir uygulama ile veri kaynağı arasında bir köprü olarak görev yapar ve ayrıca, bir **DataReader** veya **DataAdapter**kullanarak veri alma ve komutları yürütmenize olanak tanır. .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c76fd-105">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="c76fd-106">Herhangi bir veritabanı uygulamasının anahtar işlevi, veritabanında depolanan verileri güncelleştirebilme olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="c76fd-106">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="c76fd-107">ADO.NET ' de, verilerin güncelleştirilmesi **DataAdapter** ve <xref:System.Data.DataSet> **Command** nesnelerinin yanı sıra işlemleri kullanmayı da gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="c76fd-107">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c76fd-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c76fd-108">In This Section</span></span>  
 [<span data-ttu-id="c76fd-109">Bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="c76fd-109">Connecting to a Data Source</span></span>](connecting-to-a-data-source.md)  
 <span data-ttu-id="c76fd-110">Bir veri kaynağına nasıl bağlantı kurulacağını ve bağlantı olaylarıyla nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="c76fd-110">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="c76fd-111">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="c76fd-111">Connection Strings</span></span>](connection-strings.md)  
 <span data-ttu-id="c76fd-112">Bağlantı dizesi anahtar sözcükleri, güvenlik bilgileri ve bunları depolama ve alma gibi bağlantı dizelerini kullanmanın çeşitli yönlerini açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="c76fd-112">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="c76fd-113">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="c76fd-113">Connection Pooling</span></span>](connection-pooling.md)  
 <span data-ttu-id="c76fd-114">.NET Framework veri sağlayıcıları için bağlantı havuzunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="c76fd-114">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="c76fd-115">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="c76fd-115">Commands and Parameters</span></span>](commands-and-parameters.md)  
 <span data-ttu-id="c76fd-116">Komutların ve komut oluşturucuların nasıl oluşturulacağını, parametrelerin nasıl yapılandırılacağını ve verilerin alınması ve değiştirilmesi için komutların nasıl yürütüleceğini açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="c76fd-116">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="c76fd-117">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="c76fd-117">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)  
 <span data-ttu-id="c76fd-118">DataReaders, DataAdapter, Parameters, DataAdapter olaylarını işleme ve Batch işlemleri gerçekleştirme konularını açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="c76fd-118">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="c76fd-119">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="c76fd-119">Transactions and Concurrency</span></span>](transactions-and-concurrency.md)  
 <span data-ttu-id="c76fd-120">Yerel işlemlerin nasıl gerçekleştirileceğini, dağıtılmış işlemlerin ve iyimser eşzamanlılık ile nasıl çalıştığını açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="c76fd-120">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="c76fd-121">Kimliği veya Otomatik Sayı Değerlerini Alma</span><span class="sxs-lookup"><span data-stu-id="c76fd-121">Retrieving Identity or Autonumber Values</span></span>](retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="c76fd-122">Bir SQL Server tablosundaki bir **kimlik** sütunu için veya bir Microsoft Access tablosundaki bir **OtomatikSayı** alanı için oluşturulan değerleri bir tabloda bulunan satır sütunuyla eşlemek için bir örnek sağlar.</span><span class="sxs-lookup"><span data-stu-id="c76fd-122">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="c76fd-123">İçindeki kimlik değerlerini birleştirmeyi açıklar `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="c76fd-123">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="c76fd-124">İkili Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="c76fd-124">Retrieving Binary Data</span></span>](retrieving-binary-data.md)  
 <span data-ttu-id="c76fd-125">Kullanılarak ikili verilerin veya büyük veri yapılarının nasıl alınacağını açıklar `CommandBehavior` .`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="c76fd-125">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="c76fd-126">Varsayılan davranışını değiştirmek için `DataReader` .</span><span class="sxs-lookup"><span data-stu-id="c76fd-126">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="c76fd-127">Saklı Yordamlarla Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="c76fd-127">Modifying Data with Stored Procedures</span></span>](modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="c76fd-128">Yeni bir kimlik değeri döndüren bir veritabanına satır eklemek için saklı yordam giriş parametrelerinin ve çıkış parametrelerinin nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c76fd-128">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="c76fd-129">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="c76fd-129">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)  
 <span data-ttu-id="c76fd-130">Kullanılabilir veritabanlarının veya katalogların, tabloların ve görünümlerin bir veritabanında, tablolar için var olan kısıtlamaların ve bir veri kaynağından alınan diğer şema bilgilerinin nasıl alınacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c76fd-130">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="c76fd-131">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="c76fd-131">DbProviderFactories</span></span>](dbproviderfactories.md)  
 <span data-ttu-id="c76fd-132">Sağlayıcı fabrikası modelini açıklar ve ad alanındaki temel sınıfların nasıl kullanılacağını gösterir `System.Data.Common` .</span><span class="sxs-lookup"><span data-stu-id="c76fd-132">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="c76fd-133">ADO.NET’te Veri İzleme</span><span class="sxs-lookup"><span data-stu-id="c76fd-133">Data Tracing in ADO.NET</span></span>](data-tracing.md)  
 <span data-ttu-id="c76fd-134">ADO.NET 'in yerleşik veri izleme işlevselliği nasıl sağladığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c76fd-134">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="c76fd-135">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="c76fd-135">Performance Counters</span></span>](performance-counters.md)  
 <span data-ttu-id="c76fd-136">Ve için kullanılabilir performans sayaçlarını `SqlClient` açıklar `OracleClient` .</span><span class="sxs-lookup"><span data-stu-id="c76fd-136">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="c76fd-137">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="c76fd-137">Asynchronous Programming</span></span>](asynchronous-programming.md)  
 <span data-ttu-id="c76fd-138">Zaman uyumsuz programlama için ADO.NET desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="c76fd-138">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="c76fd-139">SqlClient Akış Desteği</span><span class="sxs-lookup"><span data-stu-id="c76fd-139">SqlClient Streaming Support</span></span>](sqlclient-streaming-support.md)  
 <span data-ttu-id="c76fd-140">Verilerin belleğe tam olarak yüklenmesini gerektirmeden SQL Server veri akışı yapan uygulamaların nasıl yazılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="c76fd-140">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c76fd-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c76fd-141">See also</span></span>

- [<span data-ttu-id="c76fd-142">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="c76fd-142">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="c76fd-143">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="c76fd-143">DataSets, DataTables, and DataViews</span></span>](./dataset-datatable-dataview/index.md)
- [<span data-ttu-id="c76fd-144">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="c76fd-144">Securing ADO.NET Applications</span></span>](securing-ado-net-applications.md)
- [<span data-ttu-id="c76fd-145">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="c76fd-145">SQL Server and ADO.NET</span></span>](./sql/index.md)
- [<span data-ttu-id="c76fd-146">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c76fd-146">ADO.NET Overview</span></span>](ado-net-overview.md)
