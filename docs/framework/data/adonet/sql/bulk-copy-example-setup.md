---
title: Toplu Kopyalama Örnek Kurulumu
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 2a7c0ddef42ff56306a42288c6960987ce7f714a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918086"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="de758-102">Toplu Kopyalama Örnek Kurulumu</span><span class="sxs-lookup"><span data-stu-id="de758-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="de758-103"><xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı yalnızca SQL Server tablolarına veri yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="de758-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="de758-104">Bu konuda gösterilen kod örnekleri, **AdventureWorks**SQL Server örnek veritabanını kullanır.</span><span class="sxs-lookup"><span data-stu-id="de758-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="de758-105">Mevcut tabloların değiştirilmesini önlemek için, önce oluşturmanız gereken tablolara veri yazar.</span><span class="sxs-lookup"><span data-stu-id="de758-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="de758-106">**BulkCopyDemoMatchingColumns** ve **Bulkcopydemofarklıentcolumns** tabloları, hem **AdventureWorks** **Production. Products** tablosuna dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="de758-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="de758-107">Bu tabloları kullanan kod örneklerinde, veriler **üretim. Products** tablosundan bu örnek tablolardan birine eklenir.</span><span class="sxs-lookup"><span data-stu-id="de758-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="de758-108">Örnek, kaynak verilerden hedef tabloya sütunların nasıl eşlendiğini gösteren **Bulkcopydemofarklıya sütunları** tablosu kullanılır; Diğer çoğu örnek için **BulkCopyDemoMatchingColumns** kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de758-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="de758-109">Kod örneklerinin birkaçı, bir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfın birden çok tabloya yazmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="de758-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="de758-110">Bu örnekler için, **BulkCopyDemoOrderHeader** ve **BulkCopyDemoOrderDetail** tabloları hedef tabloları olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="de758-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="de758-111">Bu tablolar, **AdventureWorks**içindeki **Sales. SalesOrderHeader** ve **Sales. SalesOrderDetail** tablolarını temel alır.</span><span class="sxs-lookup"><span data-stu-id="de758-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de758-112">**SqlBulkCopy** kod örnekleri yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="de758-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="de758-113">Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL `INSERT … SELECT` ifadesinin kullanılması daha kolay ve hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="de758-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="de758-114">Tablo kurulumu</span><span class="sxs-lookup"><span data-stu-id="de758-114">Table Setup</span></span>  
 <span data-ttu-id="de758-115">Kod örneklerinin düzgün çalışması için gereken tabloları oluşturmak için aşağıdaki Transact-SQL deyimlerini bir SQL Server veritabanında çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="de758-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="de758-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="de758-116">See also</span></span>

- [<span data-ttu-id="de758-117">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="de758-117">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)
- [<span data-ttu-id="de758-118">ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="de758-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
