---
title: Saklı Yordamlarla Verileri Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: ebf5c61010a6f658d846ed435ea3a7d18d0d3832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934446"
---
# <a name="modifying-data-with-stored-procedures"></a>Saklı Yordamlarla Verileri Değiştirme
Saklı yordamlar verileri giriş parametresi olarak kabul edebilir ve verileri çıkış parametreleri, sonuç kümeleri veya dönüş değerleri olarak döndürebilir. Aşağıdaki örnek, ADO.NET 'in giriş parametrelerini, çıkış parametrelerini ve dönüş değerlerini nasıl göndereceğini ve alacağını gösterir. Örnek, birincil anahtar sütununun SQL Server veritabanında bir kimlik sütunu olduğu tabloya yeni bir kayıt ekler.  
  
> [!NOTE]
> Kullanarak veri düzenlemek veya silmek için SQL Server saklı yordamlar kullanıyorsanız <xref:System.Data.SqlClient.SqlDataAdapter>, saklı yordam tanımında set nocount kullanmayın. Bu, etkilenen satırların sayısının sıfır olmasına neden olur ve bu da `DataAdapter` eşzamanlılık çakışması olarak yorumladığı anlamına gelir. Bu olayda, bir <xref:System.Data.DBConcurrencyException> oluşturulur.  
  
## <a name="example"></a>Örnek  
 Örnek, **Northwind** **Categories** tablosuna yeni bir kategori eklemek için aşağıdaki saklı yordamı kullanır. Saklı yordam, **CategoryName** sütunundaki değeri bir giriş parametresi olarak alır ve Identity alanının yeni değerini almak için SCOPE_IDENTITY () işlevini kullanır, **CategoryID**ve bir output parametresinde döndürür. Return ifadesinde, eklenecek satırların sayısını@ROWCOUNT döndürmek için @ işlevi kullanılır.  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 Aşağıdaki kod örneği, `InsertCategory` <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> için <xref:System.Data.SqlClient.SqlDataAdapter>kaynak olarak yukarıda gösterilen saklı yordamı kullanır. Çıkış parametresi, `Update` öğesinin <xref:System.Data.DataSet> yöntemiçağrıldığındakayıtveritabanınaeklendiktensonraöğesineyansıtılır<xref:System.Data.SqlClient.SqlDataAdapter>. `@Identity` Kod ayrıca dönüş değerini alır.  
  
> [!NOTE]
> Kullanırken <xref:System.Data.OleDb.OleDbDataAdapter>, diğer parametrelerden önce bir <xref:System.Data.ParameterDirection> **returnValue** ile parametreleri belirtmeniz gerekir.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Komut Yürütme](../../../../docs/framework/data/adonet/executing-a-command.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
