---
title: Toplu Kopyalama Örnek Kurulumu
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 80350d112da03c00e422432ce271ca5ea3ac58ab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148848"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="64186-102">Toplu Kopyalama Örnek Kurulumu</span><span class="sxs-lookup"><span data-stu-id="64186-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="64186-103">Sınıf <xref:System.Data.SqlClient.SqlBulkCopy> yalnızca SQL Server tablolarına veri yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="64186-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="64186-104">Bu konuda gösterilen kod örnekleri SQL Server örnek veritabanı, **AdventureWorks**kullanın.</span><span class="sxs-lookup"><span data-stu-id="64186-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="64186-105">Varolan tablolar kod örnekleri değiştirmemek için önce oluşturmanız gereken tablolara veri yazın.</span><span class="sxs-lookup"><span data-stu-id="64186-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="64186-106">**BulkCopyDemoMatchingColumns** ve **BulkCopyDemoDifferentColumns** tablolar **adventureworks** **Production.Products** tablosuna dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64186-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="64186-107">Bu tabloları kullanan kod örneklerinde, **Production.Products** tablosundan bu örnek tablolardan birine veriler eklenir.</span><span class="sxs-lookup"><span data-stu-id="64186-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="64186-108">**BulkCopyDemoDifferentColumns** tablosu, örnekte kaynak verilerden hedef tabloya sütunların nasıl eşlenecek gösterildiğinde kullanılır; **BulkCopyDemoMatchingColumns** diğer örneklerin çoğu için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="64186-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="64186-109">Kod örneklerinden birkaçı, birden <xref:System.Data.SqlClient.SqlBulkCopy> çok tabloya yazmak için bir sınıfın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="64186-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="64186-110">Bu örnekler için, **BulkCopyDemoOrderHeader** ve **BulkCopyDemoOrderDetail** tabloları hedef tabloları olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="64186-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="64186-111">Bu tablolar **AdventureWorks** **Sales.SalesOrderHeader** ve **Sales.SalesOrderDetail** tabloları dayanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="64186-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64186-112">**SqlBulkCopy** kod örnekleri yalnızca **SqlBulkCopy** kullanmak için sözdizimini göstermek için sağlanır.</span><span class="sxs-lookup"><span data-stu-id="64186-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="64186-113">Kaynak ve hedef tablolar aynı SQL Server örneğinde bulunuyorsa, verileri kopyalamak için `INSERT … SELECT` Transact-SQL deyimi kullanmak daha kolay ve daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="64186-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="64186-114">Tablo Kurulumu</span><span class="sxs-lookup"><span data-stu-id="64186-114">Table Setup</span></span>  
 <span data-ttu-id="64186-115">Kod örneklerinin düzgün çalışması için gerekli tabloları oluşturmak için, aşağıdaki İşlem-SQL deyimlerini bir SQL Server veritabanında çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="64186-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```sql
USE AdventureWorks  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoMatchingColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoMatchingColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoMatchingColumns]([ProductID] [int] IDENTITY(1,1) NOT NULL,  
    [Name] [nvarchar](50) NOT NULL,  
    [ProductNumber] [nvarchar](25) NOT NULL,  
 CONSTRAINT [PK_ProductID] PRIMARY KEY CLUSTERED  
(  
    [ProductID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoDifferentColumns]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoDifferentColumns]  
  
CREATE TABLE [dbo].[BulkCopyDemoDifferentColumns]([ProdID] [int] IDENTITY(1,1) NOT NULL,  
    [ProdNum] [nvarchar](25) NOT NULL,  
    [ProdName] [nvarchar](50) NOT NULL,  
 CONSTRAINT [PK_ProdID] PRIMARY KEY CLUSTERED  
(  
    [ProdID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderHeader]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderHeader]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderHeader]([SalesOrderID] [int] IDENTITY(1,1) NOT NULL,  
    [OrderDate] [datetime] NOT NULL,  
    [AccountNumber] [nvarchar](15) NULL,  
 CONSTRAINT [PK_SalesOrderID] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
  
IF EXISTS (SELECT * FROM dbo.sysobjects
 WHERE id = object_id(N'[dbo].[BulkCopyDemoOrderDetail]')  
 AND OBJECTPROPERTY(id, N'IsUserTable') = 1)  
    DROP TABLE [dbo].[BulkCopyDemoOrderDetail]  
  
CREATE TABLE [dbo].[BulkCopyDemoOrderDetail]([SalesOrderID] [int] NOT NULL,  
    [SalesOrderDetailID] [int] NOT NULL,  
    [OrderQty] [smallint] NOT NULL,  
    [ProductID] [int] NOT NULL,  
    [UnitPrice] [money] NOT NULL,  
 CONSTRAINT [PK_LineNumber] PRIMARY KEY CLUSTERED  
(  
    [SalesOrderID] ASC,  
    [SalesOrderDetailID] ASC  
) ON [PRIMARY]) ON [PRIMARY]  
```  
  
## <a name="see-also"></a><span data-ttu-id="64186-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="64186-116">See also</span></span>

- [<span data-ttu-id="64186-117">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="64186-117">Bulk Copy Operations in SQL Server</span></span>](bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="64186-118">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="64186-118">ADO.NET Overview</span></span>](../ado-net-overview.md)
