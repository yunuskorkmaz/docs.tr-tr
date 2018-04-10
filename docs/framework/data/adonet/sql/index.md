---
title: SQL Server ve ADO.NET
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c18b1fb1-2af1-4de7-80a4-95e56fd976cb
caps.latest.revision: 7
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: de9480855038afea9f8c7f26e73818846961d633
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="sql-server-and-adonet"></a><span data-ttu-id="4fca7-102">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4fca7-102">SQL Server and ADO.NET</span></span>
<span data-ttu-id="4fca7-103">Bu bölümde özellikleri ve SQL Server için .NET Framework veri sağlayıcısı için belirli davranışları açıklanmaktadır (<xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="4fca7-103">This section describes features and behaviors that are specific to the .NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient>).</span></span>  
  
 <span data-ttu-id="4fca7-104"><xref:System.Data.SqlClient>Veritabanı özgü protokoller yalıtır SQL Server sürümleri erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fca7-104"><xref:System.Data.SqlClient> provides access to versions of SQL Server, which encapsulates database-specific protocols.</span></span> <span data-ttu-id="4fca7-105">Veri sağlayıcısı işlevselliğini OLE DB, ODBC ve Oracle için .NET Framework veri sağlayıcısı benzer şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="4fca7-105">The functionality of the data provider is designed to be similar to that of the .NET Framework data providers for OLE DB, ODBC, and Oracle.</span></span> <span data-ttu-id="4fca7-106"><xref:System.Data.SqlClient>doğrudan SQL Server ile iletişim kurmak için bir tablo veri akışı (TDS) ayrıştırıcısı içerir.</span><span class="sxs-lookup"><span data-stu-id="4fca7-106"><xref:System.Data.SqlClient> includes a tabular data stream (TDS) parser to communicate directly with SQL Server.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4fca7-107">SQL Server için .NET Framework veri sağlayıcısı kullanmak için bir uygulama başvurmalıdır <xref:System.Data.SqlClient> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="4fca7-107">To use the .NET Framework Data Provider for SQL Server, an application must reference the <xref:System.Data.SqlClient> namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4fca7-108">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="4fca7-108">In This Section</span></span>  
 [<span data-ttu-id="4fca7-109">SQL Server Güvenliği</span><span class="sxs-lookup"><span data-stu-id="4fca7-109">SQL Server Security</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-security.md)  
 <span data-ttu-id="4fca7-110">SQL Server'ı hedefleyen güvenli ADO.NET uygulamaları oluşturmak için SQL Server güvenlik özellikleri ve uygulama senaryoları genel bakış sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fca7-110">Provides an overview of SQL Server security features, and application scenarios for creating secure ADO.NET applications that target SQL Server.</span></span>  
  
 [<span data-ttu-id="4fca7-111">SQL Server Veri Türleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4fca7-111">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 <span data-ttu-id="4fca7-112">SQL Server veri türleri ile çalışma konusunda ve .NET Framework veri türleri ile nasıl etkileşim kurduklarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4fca7-112">Describes how to work with SQL Server data types and how they interact with .NET Framework data types.</span></span>  
  
 [<span data-ttu-id="4fca7-113">SQL Server İkili ve Büyük Değerli Veriler</span><span class="sxs-lookup"><span data-stu-id="4fca7-113">SQL Server Binary and Large-Value Data</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-binary-and-large-value-data.md)  
 <span data-ttu-id="4fca7-114">SQL Server'da büyük değer veri ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4fca7-114">Describes how to work with large value data in SQL Server.</span></span>  
  
 [<span data-ttu-id="4fca7-115">ADO.NET’te SQL Server Veri İşlemleri</span><span class="sxs-lookup"><span data-stu-id="4fca7-115">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 <span data-ttu-id="4fca7-116">SQL Server veri ile nasıl çalışılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="4fca7-116">Describes how to work with data in SQL Server.</span></span> <span data-ttu-id="4fca7-117">Toplu kopyalama işlemleri, MARS, zaman uyumsuz işlemleri ve tablo değerli parametreleri hakkında bölümleri içerir.</span><span class="sxs-lookup"><span data-stu-id="4fca7-117">Contains sections about bulk copy operations, MARS, asynchronous operations, and table-valued parameters.</span></span>  
  
 [<span data-ttu-id="4fca7-118">SQL Server Özellikleri ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4fca7-118">SQL Server Features and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-features-and-adonet.md)  
 <span data-ttu-id="4fca7-119">ADO.NET uygulama geliştiricileri için faydalı olan SQL Server özellikleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4fca7-119">Describes SQL Server features that are useful for ADO.NET application developers.</span></span>  
  
 [<span data-ttu-id="4fca7-120">LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4fca7-120">LINQ to SQL</span></span>](../../../../../docs/framework/data/adonet/sql/linq/index.md)  
 <span data-ttu-id="4fca7-121">Temel yapı taşlarının, işlemleri ve LINQ SQL uygulamaları oluşturmak için gereken teknikleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="4fca7-121">Describes the basic building blocks, processes, and techniques required for creating LINQ to SQL applications.</span></span>  
  
 <span data-ttu-id="4fca7-122">Kullanmakta olduğunuz SQL Server sürümü için SQL Server Books Online SQL Server veritabanı altyapısı tam belgelerine bakın.</span><span class="sxs-lookup"><span data-stu-id="4fca7-122">For complete documentation of the SQL Server Database Engine, see SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 [<span data-ttu-id="4fca7-123">SQL Server Books Online</span><span class="sxs-lookup"><span data-stu-id="4fca7-123">SQL Server Books Online</span></span>](http://msdn.microsoft.com/library/ms130214.aspx)  
  
## <a name="see-also"></a><span data-ttu-id="4fca7-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4fca7-124">See Also</span></span>  
 [<span data-ttu-id="4fca7-125">ADO.NET Uygulamalarının Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="4fca7-125">Securing ADO.NET Applications</span></span>](../../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [<span data-ttu-id="4fca7-126">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="4fca7-126">Data Type Mappings in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="4fca7-127">DataSets, DataTables ve DataViews</span><span class="sxs-lookup"><span data-stu-id="4fca7-127">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="4fca7-128">ADO.NET’te Veri Alma ve Değiştirme</span><span class="sxs-lookup"><span data-stu-id="4fca7-128">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="4fca7-129">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="4fca7-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
