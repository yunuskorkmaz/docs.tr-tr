---
title: Toplu kopyalama örnek Kurulumu
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: cb4e92529c8e68bd7e47e5943f7e79dcc97603e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362445"
---
# <a name="bulk-copy-example-setup"></a><span data-ttu-id="76390-102">Toplu kopyalama örnek Kurulumu</span><span class="sxs-lookup"><span data-stu-id="76390-102">Bulk Copy Example Setup</span></span>
<span data-ttu-id="76390-103"><xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı, yalnızca SQL Server tablolarına veri yazmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="76390-103">The <xref:System.Data.SqlClient.SqlBulkCopy> class can be used to write data only to SQL Server tables.</span></span> <span data-ttu-id="76390-104">Bu konuda gösterilen kod örnekleri SQL Server örnek veritabanını kullanın **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="76390-104">The code samples shown in this topic use the SQL Server sample database, **AdventureWorks**.</span></span> <span data-ttu-id="76390-105">Varolan tablolardan değiştirmekten kaçınmak için kod örnekleri önce oluşturmanız gerekir tablolara veri yazma.</span><span class="sxs-lookup"><span data-stu-id="76390-105">To avoid altering the existing tables code samples write data to tables that you must create first.</span></span>  
  
 <span data-ttu-id="76390-106">**BulkCopyDemoMatchingColumns** ve **BulkCopyDemoDifferentColumns** tabloları hem de temel **AdventureWorks** **Production.Products**  tablo.</span><span class="sxs-lookup"><span data-stu-id="76390-106">The **BulkCopyDemoMatchingColumns** and **BulkCopyDemoDifferentColumns** tables are both based on the **AdventureWorks** **Production.Products** table.</span></span> <span data-ttu-id="76390-107">Bu tablolar kullanan kod örnekleri, gelen verileri eklenir **Production.Products** Bu örnek tablolar birine tablo.</span><span class="sxs-lookup"><span data-stu-id="76390-107">In code samples that use these tables, data is added from the **Production.Products** table to one of these sample tables.</span></span> <span data-ttu-id="76390-108">**BulkCopyDemoDifferentColumns** tablo örnek veri kaynağını sütunlarından; hedef tabloyla eşleştirmek verilmektedir zaman kullanılır **BulkCopyDemoMatchingColumns** çoğu diğer örnekler için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76390-108">The **BulkCopyDemoDifferentColumns** table is used when the sample illustrates how to map columns from the source data to the destination table; **BulkCopyDemoMatchingColumns** is used for most other samples.</span></span>  
  
 <span data-ttu-id="76390-109">Birkaç kod örnekleri kullanmayı göstermektedir <xref:System.Data.SqlClient.SqlBulkCopy> yazmak için birden çok tablo için sınıf.</span><span class="sxs-lookup"><span data-stu-id="76390-109">A few of the code samples demonstrate how to use one <xref:System.Data.SqlClient.SqlBulkCopy> class to write to multiple tables.</span></span> <span data-ttu-id="76390-110">Bu örnekler için **BulkCopyDemoOrderHeader** ve **BulkCopyDemoOrderDetail** tabloları, hedef tablo olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="76390-110">For these samples, the **BulkCopyDemoOrderHeader** and **BulkCopyDemoOrderDetail** tables are used as the destination tables.</span></span> <span data-ttu-id="76390-111">Bu tablolar temel alan **Sales.SalesOrderHeader** ve **Sales.SalesOrderDetail** tablolar **AdventureWorks**.</span><span class="sxs-lookup"><span data-stu-id="76390-111">These tables are based on the **Sales.SalesOrderHeader** and **Sales.SalesOrderDetail** tables in **AdventureWorks**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="76390-112">**SqlBulkCopy** kod örnekleri kullanarak söz dizimi göstermek için sağlanan **SqlBulkCopy** yalnızca.</span><span class="sxs-lookup"><span data-stu-id="76390-112">The **SqlBulkCopy** code samples are provided to demonstrate the syntax for using **SqlBulkCopy** only.</span></span> <span data-ttu-id="76390-113">Kaynak ve hedef tablolar aynı SQL Server örneğinde bulunuyorsa, daha kolay ve hızlı bir Transact-SQL kullanmak için bunu `INSERT … SELECT` verileri kopyalamak için deyimi.</span><span class="sxs-lookup"><span data-stu-id="76390-113">If the source and destination tables are located in the same SQL Server instance, it is easier and faster to use a Transact-SQL `INSERT … SELECT` statement to copy the data.</span></span>  
  
## <a name="table-setup"></a><span data-ttu-id="76390-114">Tablo kurulumu</span><span class="sxs-lookup"><span data-stu-id="76390-114">Table Setup</span></span>  
 <span data-ttu-id="76390-115">Tabloları düzgün çalışması kod örnekleri için gerekli oluşturmak için aşağıdaki Transact-SQL deyimlerini bir SQL Server veritabanında çalıştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="76390-115">To create the tables necessary for the code samples to run correctly, you must run the following Transact-SQL statements in a SQL Server database.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76390-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="76390-116">See Also</span></span>  
 [<span data-ttu-id="76390-117">SQL Server’da Toplu Kopyalama İşlemleri</span><span class="sxs-lookup"><span data-stu-id="76390-117">Bulk Copy Operations in SQL Server</span></span>](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [<span data-ttu-id="76390-118">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="76390-118">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
