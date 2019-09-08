---
title: SQL Server’da Toplu Kopyalama İşlemleri
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: ae97bcdd6776d573cf9e523133c2c00a42c273bb
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782531"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="d9b9d-102">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="d9b9d-102">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="d9b9d-103">Microsoft SQL Server, büyük dosyaları SQL Server veritabanlarındaki tablolara veya görünümlere hızlıca toplu olarak kopyalamak için **bcp** adlı popüler bir komut satırı yardımcı programı içerir.</span><span class="sxs-lookup"><span data-stu-id="d9b9d-103">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="d9b9d-104">Sınıfı <xref:System.Data.SqlClient.SqlBulkCopy> , benzer işlevler sağlayan yönetilen kod çözümlerini yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9b9d-104">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="d9b9d-105">SQL Server tabloya veri yüklemek için başka yollar vardır (örneğin INSERT deyimleri), ancak <xref:System.Data.SqlClient.SqlBulkCopy> bunlar üzerinde önemli bir performans avantajı sunar.</span><span class="sxs-lookup"><span data-stu-id="d9b9d-105">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="d9b9d-106"><xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı yalnızca SQL Server tablolarına veri yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d9b9d-106">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="d9b9d-107">Ancak veri kaynağı SQL Server sınırlı değildir; veriler bir <xref:System.Data.DataTable> örneğe yüklene, ya da bir <xref:System.Data.IDataReader> örnekle okunan sürece, herhangi bir veri kaynağı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d9b9d-107">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="d9b9d-108"><xref:System.Data.SqlClient.SqlBulkCopy> Sınıfını kullanarak şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d9b9d-108">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="d9b9d-109">Tek bir toplu kopyalama işlemi</span><span class="sxs-lookup"><span data-stu-id="d9b9d-109">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="d9b9d-110">Birden çok toplu kopyalama işlemi</span><span class="sxs-lookup"><span data-stu-id="d9b9d-110">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="d9b9d-111">Bir işlem içindeki toplu kopyalama işlemi</span><span class="sxs-lookup"><span data-stu-id="d9b9d-111">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9b9d-112">.NET Framework sürüm 1,1 veya önceki bir sürümü kullandığınızda ( <xref:System.Data.SqlClient.SqlBulkCopy> sınıfını desteklemeyen), <xref:System.Data.SqlClient.SqlCommand> nesneyi kullanarak SQL Server Transact-SQL **bulk INSERT** ifadesini çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9b9d-112">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d9b9d-113">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d9b9d-113">In This Section</span></span>  
 [<span data-ttu-id="d9b9d-114">Toplu Kopyalama Örnek Kurulumu</span><span class="sxs-lookup"><span data-stu-id="d9b9d-114">Bulk Copy Example Setup</span></span>](bulk-copy-example-setup.md)  
 <span data-ttu-id="d9b9d-115">Toplu kopyalama örneklerinde kullanılan tabloları açıklar ve AdventureWorks veritabanında tabloları oluşturmak için SQL betikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d9b9d-115">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="d9b9d-116">Tekil Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="d9b9d-116">Single Bulk Copy Operations</span></span>](single-bulk-copy-operations.md)  
 <span data-ttu-id="d9b9d-117"><xref:System.Data.SqlClient.SqlBulkCopy> Sınıfını kullanarak bir SQL Server örneğine verilerin tek bir toplu kopyasının nasıl yapılacağını ve Transact-SQL deyimlerini <xref:System.Data.SqlClient.SqlCommand> ve sınıfını kullanarak toplu kopyalama işleminin nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d9b9d-117">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="d9b9d-118">Çoklu Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="d9b9d-118">Multiple Bulk Copy Operations</span></span>](multiple-bulk-copy-operations.md)  
 <span data-ttu-id="d9b9d-119"><xref:System.Data.SqlClient.SqlBulkCopy> Sınıfını kullanarak bir SQL Server örneğine veri çoklu toplu kopyalama işlemlerinin nasıl yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="d9b9d-119">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="d9b9d-120">İşlem ve Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="d9b9d-120">Transaction and Bulk Copy Operations</span></span>](transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="d9b9d-121">İşlemin nasıl gerçekleştirileceği veya geri alınması dahil olmak üzere bir işlem içinde toplu kopyalama işleminin nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="d9b9d-121">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9b9d-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9b9d-122">See also</span></span>

- [<span data-ttu-id="d9b9d-123">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d9b9d-123">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="d9b9d-124">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d9b9d-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
