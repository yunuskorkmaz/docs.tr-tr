---
title: "SQL Server veri türleri ve ADO.NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81b43550-23e8-43bb-b460-7eb8ac825c33
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: b8ecdffc8e2dc9795a3bc9623c5e0127e068cc4f
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-data-types-and-adonet"></a><span data-ttu-id="b7002-102">SQL Server veri türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b7002-102">SQL Server Data Types and ADO.NET</span></span>
<span data-ttu-id="b7002-103">SQL Server ve .NET Framework olası veri kaybına yol açabilir farklı tür sistemlerde temel alır.</span><span class="sxs-lookup"><span data-stu-id="b7002-103">SQL Server and the .NET Framework are based on different type systems, which can result in potential data loss.</span></span> <span data-ttu-id="b7002-104">Veri bütünlüğü, SQL Server için .NET Framework veri sağlayıcısı korumak için (<xref:System.Data.SqlClient>) SQL Server verilerle çalışmak için yazılan erişimci yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b7002-104">To preserve data integrity, the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>) provides typed accessor methods for working with SQL Server data.</span></span> <span data-ttu-id="b7002-105">Numaralandırmalara kullanabilirsiniz <xref:System.Data.SqlDbType> belirtmek için sınıflar <xref:System.Data.SqlClient.SqlParameter> veri türleri.</span><span class="sxs-lookup"><span data-stu-id="b7002-105">You can use the enumerations in the <xref:System.Data.SqlDbType> classes to specify <xref:System.Data.SqlClient.SqlParameter> data types.</span></span>  
  
 <span data-ttu-id="b7002-106">Daha fazla bilgi ve verileri tanımlayan SQL Server ve .NET Framework veri türleri arasındaki eşlemeleri yazın bir tablo için bkz: [SQL Server veri türü eşlemeleri](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).</span><span class="sxs-lookup"><span data-stu-id="b7002-106">For more information and a table that that describes the data type mappings between SQL Server and .NET Framework data types, see [SQL Server Data Type Mappings](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md).</span></span>  
  
 <span data-ttu-id="b7002-107">SQL Server 2008 yapılandırılmış, yarı yapılandırılmış ve yapılandırılmamış veri tarih ve saat ile çalışmak için iş gereksinimlerini karşılamak için tasarlanmış yeni veri türleri tanıtır.</span><span class="sxs-lookup"><span data-stu-id="b7002-107">SQL Server 2008 introduces new data types that are designed to meet business needs to work with date and time, structured, semi-structured, and unstructured data.</span></span> <span data-ttu-id="b7002-108">Bu SQL Server 2008 Books Online içinde belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="b7002-108">These are documented in SQL Server 2008 Books Online.</span></span>  
  
 <span data-ttu-id="b7002-109">Uygulamanızda kullanılabilir SQL Server veri türleri, kullanmakta olduğunuz SQL Server sürümüne bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="b7002-109">The SQL Server data types that are available for use in your application depends on the version of SQL Server that you are using.</span></span> <span data-ttu-id="b7002-110">Daha fazla bilgi için SQL Server Books Online'nın ilgili sürümü aşağıdaki tabloda bakın.</span><span class="sxs-lookup"><span data-stu-id="b7002-110">For more information, see the relevant version of SQL Server Books Online in the following table.</span></span>  
  
 <span data-ttu-id="b7002-111">**SQL Server Books Online**</span><span class="sxs-lookup"><span data-stu-id="b7002-111">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="b7002-112">Veri türleri (veritabanı altyapısı)</span><span class="sxs-lookup"><span data-stu-id="b7002-112">Data Types (Database Engine)</span></span>](http://go.microsoft.com/fwlink/?LinkID=107468)  
  
## <a name="in-this-section"></a><span data-ttu-id="b7002-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b7002-113">In This Section</span></span>  
 [<span data-ttu-id="b7002-114">SqlTypes ve DataSet</span><span class="sxs-lookup"><span data-stu-id="b7002-114">SqlTypes and the DataSet</span></span>](../../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md)  
 <span data-ttu-id="b7002-115">Türü desteğini açıklar `SqlTypes` içinde `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="b7002-115">Describes type support for `SqlTypes` in the `DataSet`.</span></span>  
  
 [<span data-ttu-id="b7002-116">Null Değerleri İşleme</span><span class="sxs-lookup"><span data-stu-id="b7002-116">Handling Null Values</span></span>](../../../../../docs/framework/data/adonet/sql/handling-null-values.md)  
 <span data-ttu-id="b7002-117">Null değerler ve üç değerli mantığı ile nasıl çalışılacağı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7002-117">Demonstrates how to work with null values and three-valued logic.</span></span>  
  
 [<span data-ttu-id="b7002-118">GUID ve uniqueidentifier Değerlerini Karşılaştırma</span><span class="sxs-lookup"><span data-stu-id="b7002-118">Comparing GUID and uniqueidentifier Values</span></span>](../../../../../docs/framework/data/adonet/sql/comparing-guid-and-uniqueidentifier-values.md)  
 <span data-ttu-id="b7002-119">SQL Server ve .NET Framework GUID ve uniqueidentifier değerlerle çalışma gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7002-119">Demonstrates how to work with GUID and uniqueidentifier values in SQL Server and the .NET Framework.</span></span>  
  
 [<span data-ttu-id="b7002-120">Tarih ve Saat Verileri</span><span class="sxs-lookup"><span data-stu-id="b7002-120">Date and Time Data</span></span>](../../../../../docs/framework/data/adonet/sql/date-and-time-data.md)  
 <span data-ttu-id="b7002-121">SQL Server 2008'de sunulan yeni tarih ve saat veri türleri kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b7002-121">Describes how to use the new date and time data types introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="b7002-122">Büyük UDT’ler</span><span class="sxs-lookup"><span data-stu-id="b7002-122">Large UDTs</span></span>](../../../../../docs/framework/data/adonet/sql/large-udts.md)  
 <span data-ttu-id="b7002-123">SQL Server 2008'de sunulan atama büyük değerinden veri almayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b7002-123">Demonstrates how to retrieve data from large value UDTs introduced in SQL Server 2008.</span></span>  
  
 [<span data-ttu-id="b7002-124">SQL Server'da XML Verileri</span><span class="sxs-lookup"><span data-stu-id="b7002-124">XML Data in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/xml-data-in-sql-server.md)  
 <span data-ttu-id="b7002-125">SQL Server'dan alınan XML veri ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="b7002-125">Describes how to work with XML data retrieved from SQL Server.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b7002-126">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b7002-126">Reference</span></span>  
 <xref:System.Data.DataSet>  
 <span data-ttu-id="b7002-127">Açıklar `DataSet` sınıfı ve tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="b7002-127">Describes the `DataSet` class and all of its members.</span></span>  
  
 <xref:System.Data.SqlTypes>  
 <span data-ttu-id="b7002-128">Açıklar `SqlTypes` ad alanı ve tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="b7002-128">Describes the `SqlTypes` namespace and all of its members.</span></span>  
  
 <xref:System.Data.SqlDbType>  
 <span data-ttu-id="b7002-129">Açıklar `SqlDbType` numaralandırma ve tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="b7002-129">Describes the `SqlDbType` enumeration and all of its members.</span></span>  
  
 <xref:System.Data.DbType>  
 <span data-ttu-id="b7002-130">Açıklar `DbType` numaralandırma ve tüm üyeleri.</span><span class="sxs-lookup"><span data-stu-id="b7002-130">Describes the `DbType` enumeration and all of its members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7002-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b7002-131">See Also</span></span>  
 [<span data-ttu-id="b7002-132">SQL Server Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="b7002-132">SQL Server Data Type Mappings</span></span>](../../../../../docs/framework/data/adonet/sql-server-data-type-mappings.md)  
 [<span data-ttu-id="b7002-133">Parametreleri ve Parametre Veri Türlerini Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="b7002-133">Configuring Parameters and Parameter Data Types</span></span>](../../../../../docs/framework/data/adonet/configuring-parameters-and-parameter-data-types.md)  
 [<span data-ttu-id="b7002-134">Tablo Değerli Parametreler</span><span class="sxs-lookup"><span data-stu-id="b7002-134">Table-Valued Parameters</span></span>](../../../../../docs/framework/data/adonet/sql/table-valued-parameters.md)  
 [<span data-ttu-id="b7002-135">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="b7002-135">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 [<span data-ttu-id="b7002-136">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b7002-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
