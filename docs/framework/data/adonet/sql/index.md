---
title: SQL Server ve ADO.NET
description: Veritabanına özgü protokolleri kapsülleyen SQL Server için .NET Framework Veri Sağlayıcısı özellikleri ve davranışları hakkında bilgi edinin.
titleSuffix: ''
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: a517bccd9b60d00f6c6c636c9164d63fb5966de3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197397"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="7d53c-103">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7d53c-103">SQL Server and ADO.NET</span></span>

<span data-ttu-id="7d53c-104">Bu bölümde, SQL Server () için .NET Framework Veri Sağlayıcısı özgü özellikler ve davranışlar açıklanmaktadır <xref:System.Data.SqlClient> .</span><span class="sxs-lookup"><span data-stu-id="7d53c-104">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="7d53c-105"><xref:System.Data.SqlClient> veritabanına özgü protokolleri kapsülleyen SQL Server sürümlerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d53c-105"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="7d53c-106">Veri sağlayıcısının işlevselliği, OLE DB, ODBC ve Oracle için .NET Framework veri sağlayıcılarından benzer olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7d53c-106">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="7d53c-107"><xref:System.Data.SqlClient> SQL Server doğrudan iletişim kurmak için tablo veri akışı (TDS) ayrıştırıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="7d53c-107"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7d53c-108">SQL Server için .NET Framework Veri Sağlayıcısı kullanmak için, bir uygulamanın ad alanına başvurması gerekir <xref:System.Data.SqlClient> .</span><span class="sxs-lookup"><span data-stu-id="7d53c-108">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7d53c-109">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="7d53c-109">In This Section</span></span>  

 [<span data-ttu-id="7d53c-110">SQL Server Güvenliği</span><span class="sxs-lookup"><span data-stu-id="7d53c-110">SQL Server Security</span></span>](sql-server-security.md)  
 <span data-ttu-id="7d53c-111">SQL Server güvenlik özelliklerine ve SQL Server hedeflenen güvenli ADO.NET uygulamaları oluşturmaya yönelik uygulama senaryolarına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="7d53c-111">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="7d53c-112">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7d53c-112">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)  
 <span data-ttu-id="7d53c-113">SQL Server veri türleriyle nasıl çalışacağınızı ve .NET Framework veri türleriyle nasıl etkileşime gireceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d53c-113">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="7d53c-114">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="7d53c-114">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="7d53c-115">SQL Server büyük değerli verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d53c-115">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="7d53c-116">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="7d53c-116">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)  
 <span data-ttu-id="7d53c-117">SQL Server içindeki verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d53c-117">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="7d53c-118">Toplu kopyalama işlemleri, MARS, zaman uyumsuz işlemler ve tablo değerli parametreler hakkında bölümler içerir.</span><span class="sxs-lookup"><span data-stu-id="7d53c-118">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="7d53c-119">SQL Server Özellikleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7d53c-119">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)  
 <span data-ttu-id="7d53c-120">ADO.NET uygulama geliştiricileri için yararlı olan SQL Server özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d53c-120">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="7d53c-121">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7d53c-121">LINQ to SQL</span></span>](./linq/index.md)  
 <span data-ttu-id="7d53c-122">LINQ to SQL uygulamalar oluşturmak için gereken temel yapı taşlarını, süreçlerini ve teknikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="7d53c-122">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="7d53c-123">SQL Server veritabanı altyapısının tüm belgeleri için, kullandığınız SQL Server sürümü için SQL Server Books Online 'a bakın.</span><span class="sxs-lookup"><span data-stu-id="7d53c-123">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="7d53c-124">Books Online SQL Server</span><span class="sxs-lookup"><span data-stu-id="7d53c-124">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="7d53c-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d53c-125">See also</span></span>

- [<span data-ttu-id="7d53c-126">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="7d53c-126">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="7d53c-127">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="7d53c-127">Data Type Mappings in ADO.NET</span></span>](../data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="7d53c-128">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="7d53c-128">DataSets, DataTables, and DataViews</span></span>](../dataset-datatable-dataview/index.md)
- [<span data-ttu-id="7d53c-129">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="7d53c-129">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="7d53c-130">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="7d53c-130">ADO.NET Overview</span></span>](../ado-net-overview.md)
