---
title: "Alma ve ADO.NET veri değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 35de20b1cb35fdcd87a653f1ac202c01d345c317
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-and-modifying-data-in-adonet"></a><span data-ttu-id="94b74-102">Alma ve ADO.NET veri değiştirme</span><span class="sxs-lookup"><span data-stu-id="94b74-102">Retrieving and Modifying Data in ADO.NET</span></span>
<span data-ttu-id="94b74-103">Birincil işlev herhangi bir veritabanı uygulamasını bir veri kaynağına bağlanma ve içerdiği veriler alınıyor.</span><span class="sxs-lookup"><span data-stu-id="94b74-103">A primary function of any database application is connecting to a data source and retrieving the data that it contains.</span></span> <span data-ttu-id="94b74-104">Kullanarak veri almak için de komutları yürütün olanak tanıyan bir uygulama ile bir veri kaynağı arasında bir köprü olarak ADO .NET Framework veri sağlayıcıları hizmet bir **DataReader** veya **DataAdapter** .</span><span class="sxs-lookup"><span data-stu-id="94b74-104">The .NET Framework data providers of ADO.NET serve as a bridge between an application and a data source, allowing you to execute commands as well as to retrieve data by using a **DataReader** or a **DataAdapter**.</span></span> <span data-ttu-id="94b74-105">Bir anahtar herhangi bir veritabanı uygulamasını veritabanında depolanan veri güncelleştirme becerisini işlevdir.</span><span class="sxs-lookup"><span data-stu-id="94b74-105">A key function of any database application is the ability to update the data that is stored in the database.</span></span> <span data-ttu-id="94b74-106">ADO.NET, verileri güncelleştirme kullanılmasına **DataAdapter** ve <xref:System.Data.DataSet>, ve **komutu** nesneleri; ve bu da gerektirebilir işlemleri kullanma.</span><span class="sxs-lookup"><span data-stu-id="94b74-106">In ADO.NET, updating data involves using the **DataAdapter** and <xref:System.Data.DataSet>, and **Command** objects; and it may also involve using transactions.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94b74-107">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="94b74-107">In This Section</span></span>  
 [<span data-ttu-id="94b74-108">Bir veri kaynağına bağlanma</span><span class="sxs-lookup"><span data-stu-id="94b74-108">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 <span data-ttu-id="94b74-109">Bir veri kaynağı bağlantı kurmak ve bağlantı olayları ile çalışmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="94b74-109">Describes how to establish a connection to a data source and how to work with connection events.</span></span>  
  
 [<span data-ttu-id="94b74-110">Bağlantı dizeleri</span><span class="sxs-lookup"><span data-stu-id="94b74-110">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 <span data-ttu-id="94b74-111">Bağlantı dizeleri kullanılarak, bağlantı dizesi anahtar sözcükler, güvenlik bilgileri de dahil olmak üzere ve depolamak ve bunlara alma çeşitli yönlerini açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="94b74-111">Contains topics describing various aspects of using connection strings, including connection string keywords, security info, and storing and retrieving them.</span></span>  
  
 [<span data-ttu-id="94b74-112">Bağlantı havuzu</span><span class="sxs-lookup"><span data-stu-id="94b74-112">Connection Pooling</span></span>](../../../../docs/framework/data/adonet/connection-pooling.md)  
 <span data-ttu-id="94b74-113">.NET Framework veri sağlayıcıları için bağlantı havuzunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="94b74-113">Describes connection pooling for the .NET Framework data providers.</span></span>  
  
 [<span data-ttu-id="94b74-114">Komutları ve parametreleri</span><span class="sxs-lookup"><span data-stu-id="94b74-114">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 <span data-ttu-id="94b74-115">Komutları ve komut oluşturucular oluşturma, parametreleri yapılandırmak ve almak ve veri değiştirmek için komutları yürütmek nasıl açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="94b74-115">Contains topics describing how to create commands and command builders, configure parameters, and how to execute commands to retrieve and modify data.</span></span>  
  
 [<span data-ttu-id="94b74-116">DataAdapters ve DataReader</span><span class="sxs-lookup"><span data-stu-id="94b74-116">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 <span data-ttu-id="94b74-117">Açıklayan DataReader, DataAdapters, parametreleri, olaylarını işleme ve toplu işlemleri konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="94b74-117">Contains topics describing DataReaders, DataAdapters, parameters, handling DataAdapter events and performing batch operations.</span></span>  
  
 [<span data-ttu-id="94b74-118">İşlemler ve eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="94b74-118">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 <span data-ttu-id="94b74-119">Yerel işlemler, dağıtılmış işlemler gerçekleştirmek ve iyimser eşzamanlılık ile çalışmak nasıl açıklayan konuları içerir.</span><span class="sxs-lookup"><span data-stu-id="94b74-119">Contains topics describing how to perform local transactions, distributed transactions, and work with optimistic concurrency.</span></span>  
  
 [<span data-ttu-id="94b74-120">Kimliği veya sayı değerlerini alma</span><span class="sxs-lookup"><span data-stu-id="94b74-120">Retrieving Identity or Autonumber Values</span></span>](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 <span data-ttu-id="94b74-121">İçin oluşturulan değerler eşleme örneğidir bir **kimlik** sütununda bir [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] tablo veya bir **sayı** eklenen bir satırın bir tablodaki bir sütun için bir Microsoft Access tablosundaki.</span><span class="sxs-lookup"><span data-stu-id="94b74-121">Provides an example of mapping the values generated for an **identity** column in a [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] table or for an **Autonumber** field in a Microsoft Access table, to a column of an inserted row in a table.</span></span> <span data-ttu-id="94b74-122">Birleştirme kimlik değerleri açıklanır bir `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="94b74-122">Discusses merging identity values in a `DataTable`.</span></span>  
  
 [<span data-ttu-id="94b74-123">İkili veriler alınıyor</span><span class="sxs-lookup"><span data-stu-id="94b74-123">Retrieving Binary Data</span></span>](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 <span data-ttu-id="94b74-124">İkili veriler veya kullanarak büyük veri yapıları almak açıklar `CommandBehavior`.`SequentialAccess`</span><span class="sxs-lookup"><span data-stu-id="94b74-124">Describes how to retrieve binary data or large data structures using `CommandBehavior`.`SequentialAccess`</span></span> <span data-ttu-id="94b74-125">varsayılan davranışını değiştirmek için bir `DataReader`.</span><span class="sxs-lookup"><span data-stu-id="94b74-125">to modify the default behavior of a `DataReader`.</span></span>  
  
 [<span data-ttu-id="94b74-126">Saklı yordamlar verilerle değiştirme</span><span class="sxs-lookup"><span data-stu-id="94b74-126">Modifying Data with Stored Procedures</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 <span data-ttu-id="94b74-127">Saklı yordam giriş parametreleri ve yeni bir kimlik değeri döndüren bir veritabanında, satır ekleme parametreleri çıktı nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94b74-127">Describes how to use stored procedure input parameters and output parameters to insert a row in a database, returning a new identity value.</span></span>  
  
 [<span data-ttu-id="94b74-128">Veritabanı şema bilgileri alınıyor</span><span class="sxs-lookup"><span data-stu-id="94b74-128">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 <span data-ttu-id="94b74-129">Kullanılabilir veritabanları ya da kataloglar, tablolar ve görünümler bir veritabanı tablolar ve veri kaynağındaki diğer şema bilgileri için mevcut kısıtlamaları alma yolları açıklanır.</span><span class="sxs-lookup"><span data-stu-id="94b74-129">Describes how to obtain available databases or catalogs, tables and views in a database, constraints that exist for tables, and other schema information from a data source.</span></span>  
  
 [<span data-ttu-id="94b74-130">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="94b74-130">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 <span data-ttu-id="94b74-131">Sağlayıcı fabrikası modeli açıklar ve temel sınıflarda kullanımı gösterilmiştir `System.Data.Common` ad alanı.</span><span class="sxs-lookup"><span data-stu-id="94b74-131">Describes the provider factory model and demonstrates how to use the base classes in the `System.Data.Common` namespace.</span></span>  
  
 [<span data-ttu-id="94b74-132">ADO.NET veri izleme</span><span class="sxs-lookup"><span data-stu-id="94b74-132">Data Tracing in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-tracing.md)  
 <span data-ttu-id="94b74-133">ADO.NET yerleşik veri izleme işlevselliği nasıl sağladığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="94b74-133">Describes how ADO.NET provides built-in data tracing functionality.</span></span>  
  
 [<span data-ttu-id="94b74-134">Performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="94b74-134">Performance Counters</span></span>](../../../../docs/framework/data/adonet/performance-counters.md)  
 <span data-ttu-id="94b74-135">Performans sayaçları için kullanılabilir açıklar `SqlClient` ve `OracleClient`.</span><span class="sxs-lookup"><span data-stu-id="94b74-135">Describes performance counters available for `SqlClient` and `OracleClient`.</span></span>  
  
 [<span data-ttu-id="94b74-136">Zaman uyumsuz programlama</span><span class="sxs-lookup"><span data-stu-id="94b74-136">Asynchronous Programming</span></span>](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 <span data-ttu-id="94b74-137">Açıklar [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] zaman uyumsuz programlama desteği.</span><span class="sxs-lookup"><span data-stu-id="94b74-137">Describes [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] support for asynchronous programming.</span></span>  
  
 [<span data-ttu-id="94b74-138">SqlClient akış desteği</span><span class="sxs-lookup"><span data-stu-id="94b74-138">SqlClient Streaming Support</span></span>](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 <span data-ttu-id="94b74-139">Veri akış uygulamaları nasıl yazılacağından [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] gerek kalmadan tam olarak bellekte yüklenir.</span><span class="sxs-lookup"><span data-stu-id="94b74-139">Discusses how to write applications that stream data from [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] without having it fully loaded in memory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94b74-140">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="94b74-140">See Also</span></span>  
 [<span data-ttu-id="94b74-141">ADO.NET veri türü eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="94b74-141">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="94b74-142">Veri kümeleri, DataTable ve DataView</span><span class="sxs-lookup"><span data-stu-id="94b74-142">DataSets, DataTables, and DataViews</span></span>](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="94b74-143">ADO.NET uygulamalarının güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="94b74-143">Securing ADO.NET Applications</span></span>](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="94b74-144">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="94b74-144">SQL Server and ADO.NET</span></span>](../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="94b74-145">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="94b74-145">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
