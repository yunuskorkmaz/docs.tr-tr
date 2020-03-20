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
# <a name="bulk-copy-example-setup"></a>Toplu Kopyalama Örnek Kurulumu
Sınıf <xref:System.Data.SqlClient.SqlBulkCopy> yalnızca SQL Server tablolarına veri yazmak için kullanılabilir. Bu konuda gösterilen kod örnekleri SQL Server örnek veritabanı, **AdventureWorks**kullanın. Varolan tablolar kod örnekleri değiştirmemek için önce oluşturmanız gereken tablolara veri yazın.  
  
 **BulkCopyDemoMatchingColumns** ve **BulkCopyDemoDifferentColumns** tablolar **adventureworks** **Production.Products** tablosuna dayanmaktadır. Bu tabloları kullanan kod örneklerinde, **Production.Products** tablosundan bu örnek tablolardan birine veriler eklenir. **BulkCopyDemoDifferentColumns** tablosu, örnekte kaynak verilerden hedef tabloya sütunların nasıl eşlenecek gösterildiğinde kullanılır; **BulkCopyDemoMatchingColumns** diğer örneklerin çoğu için kullanılır.  
  
 Kod örneklerinden birkaçı, birden <xref:System.Data.SqlClient.SqlBulkCopy> çok tabloya yazmak için bir sınıfın nasıl kullanılacağını gösterir. Bu örnekler için, **BulkCopyDemoOrderHeader** ve **BulkCopyDemoOrderDetail** tabloları hedef tabloları olarak kullanılır. Bu tablolar **AdventureWorks** **Sales.SalesOrderHeader** ve **Sales.SalesOrderDetail** tabloları dayanmaktadır.  
  
> [!NOTE]
> **SqlBulkCopy** kod örnekleri yalnızca **SqlBulkCopy** kullanmak için sözdizimini göstermek için sağlanır. Kaynak ve hedef tablolar aynı SQL Server örneğinde bulunuyorsa, verileri kopyalamak için `INSERT … SELECT` Transact-SQL deyimi kullanmak daha kolay ve daha hızlıdır.  
  
## <a name="table-setup"></a>Tablo Kurulumu  
 Kod örneklerinin düzgün çalışması için gerekli tabloları oluşturmak için, aşağıdaki İşlem-SQL deyimlerini bir SQL Server veritabanında çalıştırmanız gerekir.  
  
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
