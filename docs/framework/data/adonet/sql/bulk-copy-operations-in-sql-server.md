---
title: SQL Server’da Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: e538e48400d955a0013a12dbf2d10f1f96c3ddfe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649554"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="af98f-102">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="af98f-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="af98f-103">Microsoft SQL Server adlandırılmış bir popüler komut satırı yardımcı programını içeren **bcp** için hızlı bir şekilde toplu tabloları veya görünümleri SQL Server veritabanları ile büyük dosyaları kopyalanıyor.</span><span class="sxs-lookup"><span data-stu-id="af98f-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="af98f-104"><xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı benzer işlevler sağlayan çözümler yönetilen kod yazmanıza olanak verir.</span><span class="sxs-lookup"><span data-stu-id="af98f-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="af98f-105">Verileri bir SQL Server tablosunu (örneğin, INSERT deyimleri) yüklemek için farklı yöntemleri vardır ancak <xref:System.Data.SqlClient.SqlBulkCopy> bir önemli performans avantajı onları sunar.</span><span class="sxs-lookup"><span data-stu-id="af98f-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="af98f-106"><xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı, yalnızca SQL Server tablolarına veri yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="af98f-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="af98f-107">Ancak, veri kaynağı SQL Server için sınırlı değildir. için verilerin yüklenmesi sürece herhangi bir veri kaynağı kullanılabilir bir <xref:System.Data.DataTable> örneği veya ile okunan bir <xref:System.Data.IDataReader> örneği.</span><span class="sxs-lookup"><span data-stu-id="af98f-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="af98f-108">Kullanarak <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı gerçekleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="af98f-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="af98f-109">Tekil toplu kopyalama işlemi</span><span class="sxs-lookup"><span data-stu-id="af98f-109">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="af98f-110">Çoklu toplu kopyalama işlemleri</span><span class="sxs-lookup"><span data-stu-id="af98f-110">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="af98f-111">Bir işlem içinde bir toplu kopyalama işlemi</span><span class="sxs-lookup"><span data-stu-id="af98f-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af98f-112">.NET Framework sürüm 1.1 veya önceki bir sürümünü kullanırken (desteklemeyen <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı), SQL Server Transact-SQL yürütmek **BULK INSERT** using deyimi <xref:System.Data.SqlClient.SqlCommand> nesne.</span><span class="sxs-lookup"><span data-stu-id="af98f-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af98f-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="af98f-113">In This Section</span></span>  
 [<span data-ttu-id="af98f-114">Toplu Kopyalama Örnek Kurulumu</span><span class="sxs-lookup"><span data-stu-id="af98f-114">Bulk Copy Example Setup</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-example-setup.md)  
 <span data-ttu-id="af98f-115">Toplu kopyalama örneklerde kullanılan tablolar açıklar ve AdventureWorks veritabanı içinde tablolar oluşturmak için SQL komut dosyaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="af98f-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="af98f-116">Tekil Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="af98f-116">Single Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/single-bulk-copy-operations.md)  
 <span data-ttu-id="af98f-117">SQL Server'ı kullanarak bir örneğine bir tekil toplu kopyalama veri bunu nasıl yapacağınız açıklanmaktadır <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı ve Transact-SQL deyimlerini kullanarak toplu kopyalama işlemi gerçekleştirme ve <xref:System.Data.SqlClient.SqlCommand> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="af98f-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="af98f-118">Çoklu Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="af98f-118">Multiple Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-bulk-copy-operations.md)  
 <span data-ttu-id="af98f-119">Çoklu toplu kopyalama işlemleri veri örneği SQL Server'ı kullanarak bunu nasıl yapacağınız açıklanmaktadır <xref:System.Data.SqlClient.SqlBulkCopy> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="af98f-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="af98f-120">İşlem ve Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="af98f-120">Transaction and Bulk Copy Operations</span></span>](../../../../../docs/framework/data/adonet/sql/transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="af98f-121">Toplu kopyalama işlemi nasıl işleyin veya geri alma işlemi dahil olmak üzere, bir işlem içinde açıklar.</span><span class="sxs-lookup"><span data-stu-id="af98f-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af98f-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af98f-122">See also</span></span>

- [<span data-ttu-id="af98f-123">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="af98f-123">SQL Server and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/index.md)
- [<span data-ttu-id="af98f-124">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="af98f-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
