---
title: SQL Server ve ADO.NET
ms.date: 03/30/2017
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
ms.openlocfilehash: 32fc946f46ddac63d87b7e5a3d8f7120799f7223
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43423084"
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="51346-102">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="51346-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="51346-103">Bu bölümde, özellikler ve SQL Server için .NET Framework veri sağlayıcısı özgü davranışları açıklanmaktadır (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="51346-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="51346-104"><xref:System.Data.SqlClient> Veritabanı özgü protokoller yalıtan SQL Server sürümleri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="51346-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="51346-105">Veri sağlayıcısı işlevselliği, OLE DB, ODBC ve Oracle için .NET Framework veri sağlayıcıları benzer olacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="51346-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="51346-106"><xref:System.Data.SqlClient> doğrudan SQL Server ile iletişim kurmak için bir tablo veri akışı (TDS) ayrıştırıcı içerir.</span><span class="sxs-lookup"><span data-stu-id="51346-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51346-107">SQL Server için .NET Framework veri sağlayıcısı kullanmak için bir uygulama başvurmalıdır <xref:System.Data.SqlClient> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="51346-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="51346-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="51346-108">In This Section</span></span>  
 [<span data-ttu-id="51346-109">SQL Server Güvenliği</span><span class="sxs-lookup"><span data-stu-id="51346-109">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="51346-110">SQL Server'ı hedefleyen güvenli ADO.NET uygulamalar oluşturmak için SQL Server güvenlik özellikleri ve uygulama senaryolarına bir bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="51346-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="51346-111">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="51346-111">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 <span data-ttu-id="51346-112">SQL Server veri türleri ile çalışmayı öğrenin ve .NET Framework veri türleri ile nasıl etkileşim kurduklarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="51346-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="51346-113">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="51346-113">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="51346-114">SQL Server'daki verileri büyük bir değer ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="51346-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="51346-115">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="51346-115">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 <span data-ttu-id="51346-116">SQL Server'daki verileri ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="51346-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="51346-117">Toplu kopyalama işlemleri, MARS, zaman uyumsuz işlemler ve tablo değerli parametreler hakkında daha fazla bölüm içerir.</span><span class="sxs-lookup"><span data-stu-id="51346-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="51346-118">SQL Server Özellikleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="51346-118">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 <span data-ttu-id="51346-119">ADO.NET uygulama geliştiricileri için yararlı olan SQL Server özelliklerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="51346-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="51346-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="51346-120">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="51346-121">Temel yapı taşlarını, süreçleri ve LINQ SQL uygulamaları oluşturmak için gereken teknikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="51346-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="51346-122">SQL Server veritabanı altyapısı tam belgelerine, kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online'a bakın.</span><span class="sxs-lookup"><span data-stu-id="51346-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="51346-123">SQL Server Çevrimiçi Kitapları</span><span class="sxs-lookup"><span data-stu-id="51346-123">SQL Server Books Online</span></span>](/sql/sql-server/sql-server-technical-documentation)  
  
## <a name="see-also"></a><span data-ttu-id="51346-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="51346-124">See Also</span></span>  
 [<span data-ttu-id="51346-125">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="51346-125">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="51346-126">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="51346-126">Data Type Mappings in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="51346-127">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="51346-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="51346-128">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="51346-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="51346-129">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="51346-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
