---
title: Saklı Yordamlarla Verileri Değiştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
ms.openlocfilehash: 7dfd4f07ba0a0473975d87c7cd166635473344a6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149337"
---
# <a name="modifying-data-with-stored-procedures"></a>Saklı Yordamlarla Verileri Değiştirme
Saklı yordamlar, veri giriş parametresi olarak kabul edebilir ve veri çıkış parametreleri, sonuç kümesi ya da dönüş değeri döndürebilir. Aşağıdaki örnekte nasıl ADO.NET gönderir ve girdi aldığı gösterilmektedir parametreleri, çıktı parametreleri ve dönüş değerleri. Örneğin, birincil anahtar sütunu bir kimlik sütunu bir SQL Server veritabanında olduğu bir tabloya yeni bir kayıt ekler.  
  
> [!NOTE]
>  Düzenleme veya silme verileri kullanarak SQL Server saklı yordamları kullanıyorsanız bir <xref:System.Data.SqlClient.SqlDataAdapter>, saklı yordam tanımında SET NOCOUNT ON kullanmadığınızdan emin olun. Bu, etkilenen satır sayısı sıfır olarak döndürülen neden olur, `DataAdapter` bir eşzamanlılık çakışması yorumlar. Bu olay bir <xref:System.Data.DBConcurrencyException> oluşturulur.  
  
## <a name="example"></a>Örnek  
 Örnek, yeni bir kategori eklemek için aşağıdaki depolanan yordamı kullanır. **Northwind** **kategorileri** tablo. Saklı yordam değeri alır **CategoryName** sütunu bir giriş parametresi ve kullanımları SCOPE_IDENTITY() olarak işlev kimlik alanının yeni değerini almak için **CategoryID**ve döndürün. bir çıkış parametresi. RETURN deyimi kullanır @@ROWCOUNT eklenen satır sayısını döndürmek için işlevi.  
  
```sql
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 Aşağıdaki kod örneğinde `InsertCategory` saklı yordam için kaynak olarak, yukarıda gösterilen <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> , <xref:System.Data.SqlClient.SqlDataAdapter>. `@Identity` Çıkış parametresi yansıtılır <xref:System.Data.DataSet> kaydı veritabanına eklendikten sonra `Update` yöntemi <xref:System.Data.SqlClient.SqlDataAdapter> çağrılır. Kod Ayrıca, dönüş değeri alır.  
  
> [!NOTE]
>  Kullanırken <xref:System.Data.OleDb.OleDbDataAdapter>, parametrelerle belirtmelisiniz bir <xref:System.Data.ParameterDirection> , **ReturnValue** parametrelerden önce.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [ADO.NET’te Veri Alma ve Değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [Komut Yürütme](../../../../docs/framework/data/adonet/executing-a-command.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
