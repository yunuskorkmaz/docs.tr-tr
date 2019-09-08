---
title: SQL Server ve ADO.NET
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: b54725fa8dbff7db82ed197f4961e773a06895e4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782335"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="1c070-102">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1c070-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="1c070-103">Bu bölümde, SQL Server (<xref:System.Data.SqlClient>) için .NET Framework veri sağlayıcısı özgü özellikler ve davranışlar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1c070-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="1c070-104"><xref:System.Data.SqlClient>veritabanına özgü protokolleri kapsülleyen SQL Server sürümlerine erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c070-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="1c070-105">Veri sağlayıcısının işlevselliği, OLE DB, ODBC ve Oracle için .NET Framework veri sağlayıcılarından benzer olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1c070-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="1c070-106"><xref:System.Data.SqlClient>SQL Server doğrudan iletişim kurmak için tablo veri akışı (TDS) ayrıştırıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="1c070-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1c070-107">SQL Server için .NET Framework veri sağlayıcısı kullanmak için, bir uygulamanın <xref:System.Data.SqlClient> ad alanına başvurması gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c070-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1c070-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="1c070-108">In This Section</span></span>  
 [<span data-ttu-id="1c070-109">SQL Server Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1c070-109">SQL Server Security</span></span>](sql-server-security.md)  
 <span data-ttu-id="1c070-110">SQL Server güvenlik özelliklerine ve SQL Server hedeflenen güvenli ADO.NET uygulamaları oluşturmaya yönelik uygulama senaryolarına genel bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="1c070-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="1c070-111">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1c070-111">SQL Server Data Types and ADO.NET</span></span>](sql-server-data-types.md)  
 <span data-ttu-id="1c070-112">SQL Server veri türleriyle nasıl çalışacağınızı ve .NET Framework veri türleriyle nasıl etkileşime gireceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c070-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="1c070-113">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="1c070-113">SQL Server Binary and Large-Value Data</span></span>](sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="1c070-114">SQL Server büyük değerli verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c070-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="1c070-115">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="1c070-115">SQL Server Data Operations in ADO.NET</span></span>](sql-server-data-operations.md)  
 <span data-ttu-id="1c070-116">SQL Server içindeki verilerle nasıl çalışabileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c070-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="1c070-117">Toplu kopyalama işlemleri, MARS, zaman uyumsuz işlemler ve tablo değerli parametreler hakkında bölümler içerir.</span><span class="sxs-lookup"><span data-stu-id="1c070-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="1c070-118">SQL Server Özellikleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1c070-118">SQL Server Features and ADO.NET</span></span>](sql-server-features-and-adonet.md)  
 <span data-ttu-id="1c070-119">ADO.NET uygulama geliştiricileri için yararlı olan SQL Server özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c070-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="1c070-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="1c070-120">LINQ to SQL</span></span>](./linq/index.md)  
 <span data-ttu-id="1c070-121">LINQ to SQL uygulamalar oluşturmak için gereken temel yapı taşlarını, süreçlerini ve teknikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="1c070-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="1c070-122">SQL Server veritabanı altyapısının tüm belgeleri için, kullandığınız SQL Server sürümü için SQL Server Books Online 'a bakın.</span><span class="sxs-lookup"><span data-stu-id="1c070-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="1c070-123">Books Online SQL Server</span><span class="sxs-lookup"><span data-stu-id="1c070-123">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="1c070-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c070-124">See also</span></span>

- [<span data-ttu-id="1c070-125">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="1c070-125">Securing ADO.NET Applications</span></span>](../securing-ado-net-applications.md)
- [<span data-ttu-id="1c070-126">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="1c070-126">Data Type Mappings in ADO.NET</span></span>](../data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="1c070-127">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="1c070-127">DataSets, DataTables, and DataViews</span></span>](../dataset-datatable-dataview/index.md)
- [<span data-ttu-id="1c070-128">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="1c070-128">Retrieving and Modifying Data in ADO.NET</span></span>](../retrieving-and-modifying-data.md)
- [<span data-ttu-id="1c070-129">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="1c070-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
