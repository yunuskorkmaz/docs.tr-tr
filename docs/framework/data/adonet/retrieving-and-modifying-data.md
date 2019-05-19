---
title: ADO.NET’te Veri Alma ve Değiştirme
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: a5ac8fbd2a53d2670471c1ef5e59508f582ed944
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881430"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="ca8ef-102">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ca8ef-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="ca8ef-103">Herhangi bir veritabanı uygulama birincil işlevi bir veri kaynağına bağlanmak ve içerdiği veriler alınıyor.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="ca8ef-104">ADO.NET, .NET Framework veri sağlayıcıları kullanarak veri almak için de komutları yürütmek olanak tanıyan bir uygulama ve bir veri kaynağı arasında bir köprü olarak hizmet verecek bir **DataReader** veya **DataAdapter** .</span><span class="sxs-lookup"><span data-stu-id="ca8ef-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="ca8ef-105">Herhangi bir veritabanı uygulama anahtar işlevi veritabanında depolanan verileri güncelleştirmek için olanağıdır.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="ca8ef-106">ADO.NET ile veri güncelleştirme kullanılmasına **DataAdapter** ve <xref:System.Data.DataSet>, ve **komut** nesneler; ve bu da gerektirebilir işlemleri kullanma.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca8ef-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="ca8ef-107">In This Section</span></span>  
 [<span data-ttu-id="ca8ef-108">Veri Kaynağına Bağlanma</span><span class="sxs-lookup"><span data-stu-id="ca8ef-108">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 <span data-ttu-id="ca8ef-109">Nasıl bir veri kaynağına bağlantı kurmak ve bağlantı olayları ile çalışma konusunda açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="ca8ef-110">Bağlantı Dizeleri</span><span class="sxs-lookup"><span data-stu-id="ca8ef-110">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 <span data-ttu-id="ca8ef-111">Bağlantı dizeleri kullanarak, bağlantı dizesi anahtar sözcükler, güvenlik bilgileri de dahil olmak üzere ve depolamak ve bunları almak çeşitli yönlerini açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="ca8ef-112">Bağlantı Havuzu</span><span class="sxs-lookup"><span data-stu-id="ca8ef-112">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 <span data-ttu-id="ca8ef-113">.NET Framework veri sağlayıcıları için bağlantı havuzu açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="ca8ef-114">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca8ef-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="ca8ef-115">Komutlar ve komut oluşturucular oluşturma parametreleri yapılandırmak nasıl ve almak ve verileri değiştirmek için komutları yürütmek nasıl eklendiğini açıklayan konulara içerir.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="ca8ef-116">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="ca8ef-116">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 <span data-ttu-id="ca8ef-117">DataReader, DataAdapters parametrelerini açıklayan, DataAdapter olaylarını işleme ve toplu işlemleri gerçekleştirme konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="ca8ef-118">İşlemler ve Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="ca8ef-118">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="ca8ef-119">Yerel işlemler, dağıtılmış işlemler gerçekleştirmek ve iyimser eşzamanlılık ile çalışmak nasıl eklendiğini açıklayan konulara içerir.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="ca8ef-120">Kimliği veya Otomatik Sayı Değerlerini Alma</span><span class="sxs-lookup"><span data-stu-id="ca8ef-120">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="ca8ef-121">Eşleme için oluşturulan değerleri bir örnek sağlar bir **kimlik** için bir SQL Server tablo veya sütun bir **sayı** tablodaki eklenen bir satır içeren bir sütun için bir Microsoft Access tablosundaki.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-121">Provides an example of mapping the values generated for an **identity** column in a SQL Server table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="ca8ef-122">Birleştirme kimlik değerleri açıklar bir `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="ca8ef-123">İkili Verileri Alma</span><span class="sxs-lookup"><span data-stu-id="ca8ef-123">Retrieving Binary Data</span></span>](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 <span data-ttu-id="ca8ef-124">İkili verileri veya büyük veri yapılarını kullanarak alınacak açıklar `CommandBehavior`.`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="ca8ef-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="ca8ef-125">varsayılan davranışını değiştirmek için bir `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="ca8ef-126">Saklı Yordamlarla Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ca8ef-126">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="ca8ef-127">Saklı yordam giriş parametreleri ve çıkış parametreleri bir veritabanında yeni bir kimlik değeri döndüren bir satır eklemek için nasıl kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="ca8ef-128">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="ca8ef-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 <span data-ttu-id="ca8ef-129">Kullanılabilir veritabanlarını veya kataloglar, tabloları ve görünümleri bir veritabanındaki tabloları ve diğer şema bilgileri bir veri kaynağından mevcut kısıtlamalar alma yolları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="ca8ef-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="ca8ef-130">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="ca8ef-131">Sağlayıcı fabrikası modelini açıklar ve taban sınıflardaki kullanmayı gösteren `System.Data.Common` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="ca8ef-132">ADO.NET’te Veri İzleme</span><span class="sxs-lookup"><span data-stu-id="ca8ef-132">Data Tracing in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-tracing.md)  
 <span data-ttu-id="ca8ef-133">ADO.NET veri yerleşik izleme işlevselliği nasıl sağladığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="ca8ef-134">Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="ca8ef-134">Performance Counters</span></span>](../../../../docs/framework/data/adonet/performance-counters.md)  
 <span data-ttu-id="ca8ef-135">İçin kullanılabilen performans sayaçlarının açıklar `SqlClient` ve `OracleClient`.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="ca8ef-136">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="ca8ef-136">Asynchronous Programming</span></span>](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 <span data-ttu-id="ca8ef-137">Zaman uyumsuz programlama için ADO.NET desteğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-137">Describes ADO.NET support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="ca8ef-138">SqlClient Akış Desteği</span><span class="sxs-lookup"><span data-stu-id="ca8ef-138">SqlClient Streaming Support</span></span>](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 <span data-ttu-id="ca8ef-139">SQL Server'dan veri akışı, tam olarak belleğe zorunda kalmadan uygulamaları yazmak nasıl ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-139">Discusses how to write applications that stream data from SQL Server without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca8ef-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca8ef-140">See also</span></span>

- [<span data-ttu-id="ca8ef-141">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="ca8ef-141">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="ca8ef-142">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="ca8ef-142">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [<span data-ttu-id="ca8ef-143">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="ca8ef-143">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)
- [<span data-ttu-id="ca8ef-144">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ca8ef-144">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="ca8ef-145">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="ca8ef-145">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
