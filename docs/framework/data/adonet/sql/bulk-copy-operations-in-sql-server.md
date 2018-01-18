---
title: "SQL Server toplu kopyalama işlemleri"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6efca83c6d3157e7fc4ff0e49ad32cab7cee9251
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="b3f7b-102">SQL Server toplu kopyalama işlemleri</span><span class="sxs-lookup"><span data-stu-id="b3f7b-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="b3f7b-103">Microsoft SQL Server adlandırılmış popüler bir komut satırı yardımcı programını içeren **bcp** için hızlı bir şekilde toplu tabloları ve görünümleri SQL Server veritabanlarını içine büyük dosyaların kopyalanması.</span><span class="sxs-lookup"><span data-stu-id="b3f7b-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="b3f7b-104"><xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı benzer işlevler sağlayan yönetilen kod çözümleri yazmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="b3f7b-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="b3f7b-105">Verileri bir SQL Server tabloya (örneğin, INSERT deyimleri) yüklemek için başka yolları vardır, ancak <xref:System.Data.SqlClient.SqlBulkCopy> bunları üzerinde önemli performans avantaj sunar.</span><span class="sxs-lookup"><span data-stu-id="b3f7b-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="b3f7b-106"><xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı, yalnızca SQL Server tablolarına veri yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b3f7b-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="b3f7b-107">Ancak, veri kaynağı SQL Server'a sınırlı değildir; verileri için yüklenebilir sürece herhangi bir veri kaynağı kullanılabilir bir <xref:System.Data.DataTable> örneği veya okumasını bir <xref:System.Data.IDataReader> örneği.</span><span class="sxs-lookup"><span data-stu-id="b3f7b-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="b3f7b-108">Kullanarak <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı, gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b3f7b-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
-   <span data-ttu-id="b3f7b-109">Bir tek toplu kopyalama işlemi</span><span class="sxs-lookup"><span data-stu-id="b3f7b-109">A single bulk copy operation</span></span>  
  
-   <span data-ttu-id="b3f7b-110">Birden çok toplu kopyalama işlemleri</span><span class="sxs-lookup"><span data-stu-id="b3f7b-110">Multiple bulk copy operations</span></span>  
  
-   <span data-ttu-id="b3f7b-111">Bir işlem içinde toplu kopyalama işlemi</span><span class="sxs-lookup"><span data-stu-id="b3f7b-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3f7b-112">.NET Framework sürüm 1.1 veya önceki bir sürümünü kullanırken (desteklemeyen <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı), SQL Server Transact-SQL yürütebilir **BULK INSERT** deyimiyle <xref:System.Data.SqlClient.SqlCommand> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b3f7b-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b3f7b-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="b3f7b-113">In This Section</span></span>  
 [<span data-ttu-id="b3f7b-114">Toplu Kopyalama Örnek Kurulumu</span><span class="sxs-lookup"><span data-stu-id="b3f7b-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="b3f7b-115">Toplu kopyalama örneklerde kullanılan tablolar açıklar ve tabloları AdventureWorks veritabanını oluşturmak için SQL komut dosyaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3f7b-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="b3f7b-116">Tekil Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="b3f7b-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="b3f7b-117">SQL Server'ı kullanarak, bir örneğine tek toplu kopyalama veri yapmak açıklar <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı ve Transact-SQL deyimlerini kullanarak toplu kopyalama işlemi gerçekleştirme ve <xref:System.Data.SqlClient.SqlCommand> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b3f7b-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="b3f7b-118">Çoklu Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="b3f7b-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="b3f7b-119">Birden çok toplu kopyalama işlemleri veri SQL Server'ı kullanarak bir örneğini içine nasıl açıklar <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b3f7b-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="b3f7b-120">İşlem ve Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="b3f7b-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="b3f7b-121">Toplu kopyalama işlemi nasıl yürütme veya geri alma işlemi de dahil olmak üzere bir işlem içinde açıklar.</span><span class="sxs-lookup"><span data-stu-id="b3f7b-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3f7b-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3f7b-122">See Also</span></span>  
 [<span data-ttu-id="b3f7b-123">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="b3f7b-123">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)  
 [<span data-ttu-id="b3f7b-124">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="b3f7b-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
