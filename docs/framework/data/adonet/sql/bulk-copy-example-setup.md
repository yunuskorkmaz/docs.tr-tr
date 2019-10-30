---
title: Toplu Kopyalama Örnek Kurulumu
ms.date: 03/30/2017
ms.assetid: d4dde6ac-b8b6-4593-965a-635c8fb2dadb
ms.openlocfilehash: 28fa5cde1dcbaf9f38450116a56fc11d904edc1c
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040261"
---
# <a name="bulk-copy-example-setup"></a>Toplu Kopyalama Örnek Kurulumu
<xref:System.Data.SqlClient.SqlBulkCopy> sınıfı yalnızca SQL Server tablolarına veri yazmak için kullanılabilir. Bu konuda gösterilen kod örnekleri, **AdventureWorks**SQL Server örnek veritabanını kullanır. Mevcut tabloların değiştirilmesini önlemek için, önce oluşturmanız gereken tablolara veri yazar.  
  
 **BulkCopyDemoMatchingColumns** ve **Bulkcopydemofarklıentcolumns** tabloları, hem **AdventureWorks** **Production. Products** tablosuna dayalıdır. Bu tabloları kullanan kod örneklerinde, veriler **üretim. Products** tablosundan bu örnek tablolardan birine eklenir. Örnek, kaynak verilerden hedef tabloya sütunların nasıl eşlendiğini gösteren **Bulkcopydemofarklıya sütunları** tablosu kullanılır; Diğer çoğu örnek için **BulkCopyDemoMatchingColumns** kullanılır.  
  
 Kod örneklerinin birkaçı, birden çok tabloya yazmak için bir <xref:System.Data.SqlClient.SqlBulkCopy> sınıfını nasıl kullanacağınızı gösterir. Bu örnekler için, **BulkCopyDemoOrderHeader** ve **BulkCopyDemoOrderDetail** tabloları hedef tabloları olarak kullanılır. Bu tablolar, **AdventureWorks**içindeki **Sales. SalesOrderHeader** ve **Sales. SalesOrderDetail** tablolarını temel alır.  
  
> [!NOTE]
> **SqlBulkCopy** kod örnekleri yalnızca **SqlBulkCopy** kullanma sözdizimini göstermek için verilmiştir. Kaynak ve hedef tablolar aynı SQL Server örneğinde yer alıyorsa, verileri kopyalamak için Transact-SQL `INSERT … SELECT` deyimlerinin kullanılması daha kolay ve hızlıdır.  
  
## <a name="table-setup"></a>Tablo kurulumu  
 Kod örneklerinin düzgün çalışması için gereken tabloları oluşturmak için aşağıdaki Transact-SQL deyimlerini bir SQL Server veritabanında çalıştırmanız gerekir.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [SQL Server’da Toplu Kopyalama İşlemleri](bulk-copy-operations-in-sql-server.md)
- [ADO.NET’e Genel Bakış](../ado-net-overview.md)
