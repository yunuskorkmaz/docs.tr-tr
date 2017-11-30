---
title: "Saklı yordamlar verilerle değiştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 7d8e9a46-1af6-4a02-bf61-969d77ae07e0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1f8f0c37e5ac84d878f1d443d2bcc1e8ded099a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="modifying-data-with-stored-procedures"></a>Saklı yordamlar verilerle değiştirme
Saklı yordamlar veri giriş parametreleri olarak kabul edebilir ve veri çıkış parametreleri, sonuç kümesi ya da dönüş değeri geri dönebilirsiniz. Aşağıdaki örnekte nasıl ADO.NET alıp gönderen giriş gösterilmektedir parametreleri, çıktı parametrelerini ve dönüş değerleri. Örneğin, birincil anahtar sütunu bir kimlik sütunu bir SQL Server veritabanında olduğu bir tabloya yeni bir kayıt ekler.  
  
> [!NOTE]
>  Düzenlemek veya kullanarak verileri silmek için SQL Server saklı yordamları kullanıyorsanız, bir <xref:System.Data.SqlClient.SqlDataAdapter>, saklı yordam tanımı'nda SET NOCOUNT ON kullanmadığınızdan emin olun. Bu sıfır olarak döndürülen etkilenen satırların sayısı neden olur, `DataAdapter` bir eşzamanlılık çakışması yorumlar. Bu olay bir <xref:System.Data.DBConcurrencyException> oluşturulur.  
  
## <a name="example"></a>Örnek  
 Yeni bir kategori eklemek için aşağıdaki saklı yordamı örnek kullanır **Northwind** **kategorileri** tablo. Saklı yordam değerini alır **CategoryName** sütunu bir giriş parametresi ve kullandığı SCOPE_IDENTITY() olarak işlev kimlik alanına yeni değerini almak için **adlı kullanıcı, Categoryıd'si**ve döndürün bir çıkış parametresi. RETURN deyimi kullanan @@ROWCOUNT işlevi eklenen satır sayısını döndürür.  
  
```  
CREATE PROCEDURE dbo.InsertCategory  
  @CategoryName nvarchar(15),  
  @Identity int OUT  
AS  
INSERT INTO Categories (CategoryName) VALUES(@CategoryName)  
SET @Identity = SCOPE_IDENTITY()  
RETURN @@ROWCOUNT  
```  
  
 Aşağıdaki kod örneğinde `InsertCategory` saklı yordamı için kaynak olarak yukarıda gösterilen <xref:System.Data.SqlClient.SqlDataAdapter.InsertCommand%2A> , <xref:System.Data.SqlClient.SqlDataAdapter>. `@Identity` Çıktı parametresi olarak yansıtılabilir <xref:System.Data.DataSet> kaydı veritabanına eklendikten sonra `Update` yöntemi <xref:System.Data.SqlClient.SqlDataAdapter> olarak adlandırılır. Kod ayrıca dönüş değerini alır.  
  
> [!NOTE]
>  Kullanırken <xref:System.Data.OleDb.OleDbDataAdapter>, parametrelerle belirtmelisiniz bir <xref:System.Data.ParameterDirection> , **ReturnValue** parametrelerden önce.  
  
 [!code-csharp[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.SprocIdentityReturn#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.SprocIdentityReturn/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Alma ve ADO.NET veri değiştirme](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [DataAdapters ve DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Bir komutu yürütme](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
