---
title: SQL Server’da Toplu Kopyalama İşlemleri
description: Büyük dosyaları SQL Server veritabanlarındaki tablolara veya görünümlere toplu olarak kopyalamanın yönetilen kod çözümlerini yazmak için SqlBulkCopy sınıfını kullanmayı öğrenin.
ms.date: 03/30/2017
ms.assetid: 83a7a0d2-8018-4354-97b9-0b1d99f8342b
ms.openlocfilehash: 4f877836aa45efe162cce3c42cb5733f86deab2c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286526"
---
# <a name="bulk-copy-operations-in-sql-server"></a><span data-ttu-id="69096-103">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="69096-103">Bulk Copy Operations in SQL Server</span></span>
<span data-ttu-id="69096-104">Microsoft SQL Server, büyük dosyaları SQL Server veritabanlarındaki tablolara veya görünümlere hızlıca toplu olarak kopyalamak için **bcp** adlı popüler bir komut satırı yardımcı programı içerir.</span><span class="sxs-lookup"><span data-stu-id="69096-104">Microsoft SQL Server includes a popular command-line utility named **bcp** for quickly bulk copying large files into tables or views in SQL Server databases.</span></span> <span data-ttu-id="69096-105"><xref:System.Data.SqlClient.SqlBulkCopy>Sınıfı, benzer işlevler sağlayan yönetilen kod çözümlerini yazmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="69096-105">The <xref:System.Data.SqlClient.SqlBulkCopy> class allows you to write managed code solutions that provide similar functionality.</span></span> <span data-ttu-id="69096-106">SQL Server tabloya veri yüklemek için başka yollar vardır (örneğin INSERT deyimleri), ancak <xref:System.Data.SqlClient.SqlBulkCopy> bunlar üzerinde önemli bir performans avantajı sunar.</span><span class="sxs-lookup"><span data-stu-id="69096-106">There are other ways to load data into a SQL Server table (INSERT statements, for example) but <xref:System.Data.SqlClient.SqlBulkCopy> offers a significant performance advantage over them.</span></span>  
  
 <span data-ttu-id="69096-107"><xref:System.Data.SqlClient.SqlBulkCopy>Sınıfı yalnızca SQL Server tablolarına veri yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="69096-107">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="69096-108">Ancak veri kaynağı SQL Server sınırlı değildir; veriler bir örneğe yüklene, <xref:System.Data.DataTable> ya da bir örnekle okunan sürece, herhangi bir veri kaynağı kullanılabilir <xref:System.Data.IDataReader> .</span><span class="sxs-lookup"><span data-stu-id="69096-108">But the data source is not limited to SQL Server; any data source can be used, as long as the data can be loaded to a <xref:System.Data.DataTable> instance or read with a <xref:System.Data.IDataReader> instance.</span></span>  
  
 <span data-ttu-id="69096-109">Sınıfını kullanarak şunları yapabilirsiniz <xref:System.Data.SqlClient.SqlBulkCopy> :</span><span class="sxs-lookup"><span data-stu-id="69096-109">Using the <xref:System.Data.SqlClient.SqlBulkCopy> class, you can perform:</span></span>  
  
- <span data-ttu-id="69096-110">Tek bir toplu kopyalama işlemi</span><span class="sxs-lookup"><span data-stu-id="69096-110">A single bulk copy operation</span></span>  
  
- <span data-ttu-id="69096-111">Birden çok toplu kopyalama işlemi</span><span class="sxs-lookup"><span data-stu-id="69096-111">Multiple bulk copy operations</span></span>  
  
- <span data-ttu-id="69096-112">Bir işlem içindeki toplu kopyalama işlemi</span><span class="sxs-lookup"><span data-stu-id="69096-112">A bulk copy operation within a transaction</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69096-113">.NET Framework sürüm 1,1 veya önceki bir sürümü kullandığınızda ( <xref:System.Data.SqlClient.SqlBulkCopy> sınıfını desteklemeyen), nesneyi kullanarak SQL Server Transact-SQL **bulk INSERT** ifadesini çalıştırabilirsiniz <xref:System.Data.SqlClient.SqlCommand> .</span><span class="sxs-lookup"><span data-stu-id="69096-113">When using .NET Framework version 1.1 or earlier (which does not support the <xref:System.Data.SqlClient.SqlBulkCopy> class), you can execute the SQL Server Transact-SQL **BULK INSERT** statement using the <xref:System.Data.SqlClient.SqlCommand> object.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="69096-114">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="69096-114">In This Section</span></span>  
 [<span data-ttu-id="69096-115">Toplu Kopyalama Örnek Kurulumu</span><span class="sxs-lookup"><span data-stu-id="69096-115">Bulk Copy Example Setup</span></span>](bulk-copy-example-setup.md)  
 <span data-ttu-id="69096-116">Toplu kopyalama örneklerinde kullanılan tabloları açıklar ve AdventureWorks veritabanında tabloları oluşturmak için SQL betikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="69096-116">Describes the tables used in the bulk copy examples and provides SQL scripts for creating the tables in the AdventureWorks database.</span></span>  
  
 [<span data-ttu-id="69096-117">Tekil Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="69096-117">Single Bulk Copy Operations</span></span>](single-bulk-copy-operations.md)  
 <span data-ttu-id="69096-118">Sınıfını kullanarak bir SQL Server örneğine verilerin tek bir toplu kopyasının nasıl yapılacağını <xref:System.Data.SqlClient.SqlBulkCopy> ve Transact-SQL deyimlerini ve sınıfını kullanarak toplu kopyalama işleminin nasıl gerçekleştirileceğini açıklar <xref:System.Data.SqlClient.SqlCommand> .</span><span class="sxs-lookup"><span data-stu-id="69096-118">Describes how to do a single bulk copy of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class, and how to perform the bulk copy operation using Transact-SQL statements and the <xref:System.Data.SqlClient.SqlCommand> class.</span></span>  
  
 [<span data-ttu-id="69096-119">Çoklu Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="69096-119">Multiple Bulk Copy Operations</span></span>](multiple-bulk-copy-operations.md)  
 <span data-ttu-id="69096-120">Sınıfını kullanarak bir SQL Server örneğine veri çoklu toplu kopyalama işlemlerinin nasıl yapılacağını açıklar <xref:System.Data.SqlClient.SqlBulkCopy> .</span><span class="sxs-lookup"><span data-stu-id="69096-120">Describes how to do multiple bulk copy operations of data into an instance of SQL Server using the <xref:System.Data.SqlClient.SqlBulkCopy> class.</span></span>  
  
 [<span data-ttu-id="69096-121">İşlem ve Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="69096-121">Transaction and Bulk Copy Operations</span></span>](transaction-and-bulk-copy-operations.md)  
 <span data-ttu-id="69096-122">İşlemin nasıl gerçekleştirileceği veya geri alınması dahil olmak üzere bir işlem içinde toplu kopyalama işleminin nasıl gerçekleştirileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="69096-122">Describes how to perform a bulk copy operation within a transaction, including how to commit or rollback the transaction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69096-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69096-123">See also</span></span>

- [<span data-ttu-id="69096-124">SQL Server ve ADO.NET</span><span class="sxs-lookup"><span data-stu-id="69096-124">SQL Server and ADO.NET</span></span>](index.md)
- [<span data-ttu-id="69096-125">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="69096-125">ADO.NET Overview</span></span>](../ado-net-overview.md)
