---
title: "Toplu kopyalama örnek Kurulumu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dafbb4012eabda5eb437ec077d571fc28c3e806b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="bulk-copy-example-setup"></a>Toplu kopyalama örnek Kurulumu
<xref:System.Data.SqlClient.SqlBulkCopy> Sınıfı, yalnızca SQL Server tablolarına veri yazmak için kullanılabilir. Bu konuda gösterilen kod örnekleri SQL Server örnek veritabanını kullanın **AdventureWorks**. Varolan tablolardan değiştirmekten kaçınmak için kod örnekleri önce oluşturmanız gerekir tablolara veri yazma.  
  
 **BulkCopyDemoMatchingColumns** ve **BulkCopyDemoDifferentColumns** tabloları hem de temel **AdventureWorks** **Production.Products**  tablo. Bu tablolar kullanan kod örnekleri, gelen verileri eklenir **Production.Products** Bu örnek tablolar birine tablo. **BulkCopyDemoDifferentColumns** tablo örnek veri kaynağını sütunlarından; hedef tabloyla eşleştirmek verilmektedir zaman kullanılır **BulkCopyDemoMatchingColumns** çoğu diğer örnekler için kullanılır.  
  
 Birkaç kod örnekleri kullanmayı göstermektedir <xref:System.Data.SqlClient.SqlBulkCopy> yazmak için birden çok tablo için sınıf. Bu örnekler için **BulkCopyDemoOrderHeader** ve **BulkCopyDemoOrderDetail** tabloları, hedef tablo olarak kullanılır. Bu tablolar temel alan **Sales.SalesOrderHeader** ve **Sales.SalesOrderDetail** tablolar **AdventureWorks**.  
  
> [!NOTE]
>  **SqlBulkCopy** kod örnekleri kullanarak söz dizimi göstermek için sağlanan **SqlBulkCopy** yalnızca. Kaynak ve hedef tablolar aynı SQL Server örneğinde bulunuyorsa, daha kolay ve hızlı bir Transact-SQL kullanmak için bunu `INSERT … SELECT` verileri kopyalamak için deyimi.  
  
## <a name="table-setup"></a>Tablo kurulumu  
 Tabloları düzgün çalışması kod örnekleri için gerekli oluşturmak için aşağıdaki Transact-SQL deyimlerini bir SQL Server veritabanında çalıştırmanız gerekir.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [SQL Server’da Toplu Kopyalama İşlemleri](../../../../../docs/framework/data/adonet/sql/bulk-copy-operations-in-sql-server.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
