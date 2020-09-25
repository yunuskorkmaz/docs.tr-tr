---
title: DbConnection, DbCommand ve DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 3075999c15fccc3a41c191297a146c362b3638e8
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183331"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection, DbCommand ve DbException

Bir ve oluşturduktan sonra <xref:System.Data.Common.DbProviderFactory> <xref:System.Data.Common.DbConnection> , veri kaynağından veri almak için komutlar ve veri okuyucularıyla çalışabilirsiniz.  
  
## <a name="retrieving-data-example"></a>Veri alma örneği  

 Bu örnek, bir `DbConnection` nesneyi bağımsız değişken olarak alır. Bir <xref:System.Data.Common.DbCommand> SQL SELECT ifadesine ayarlayarak Kategoriler tablosundan verileri seçmek için oluşturulur <xref:System.Data.Common.DbCommand.CommandText%2A> . Kod, kategori tablosunun veri kaynağında bulunduğunu varsayar. Bağlantı açılır ve veriler bir kullanılarak alınır <xref:System.Data.Common.DbDataReader> .  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Komut örneği yürütme  

 Bu örnek, bir `DbConnection` nesneyi bağımsız değişken olarak alır. `DbConnection`Geçerliyse bağlantı açılır ve <xref:System.Data.Common.DbCommand> oluşturulur ve yürütülür. , <xref:System.Data.Common.DbCommand.CommandText%2A> Northwind veritabanındaki Categories tablosuna bir INSERT uygulayan SQL INSERT ifadesine ayarlanır. Kod, Northwind veritabanının veri kaynağında bulunduğunu ve INSERT ifadesinde kullanılan SQL sözdiziminin belirtilen sağlayıcı için geçerli olduğunu varsayar. Veri kaynağında oluşan hatalar <xref:System.Data.Common.DbException> kod bloğu tarafından işlenir ve diğer tüm özel durumlar <xref:System.Exception> bloğunda işlenir.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>DbException ile veri hatalarını işleme  

 <xref:System.Data.Common.DbException>Sınıfı, bir veri kaynağı adına oluşturulan tüm özel durumlar için temel sınıftır. Özel durum sınıfına başvuruda bulunmak zorunda kalmadan farklı sağlayıcılar tarafından oluşturulan özel durumları işlemek için özel durum işleme kodunuzda kullanabilirsiniz. Aşağıdaki kod parçası,,, <xref:System.Data.Common.DbException> <xref:System.Exception.GetType%2A> <xref:System.Exception.Source%2A> <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A> ve özelliklerini kullanarak veri kaynağı tarafından döndürülen hata bilgilerini göstermek için kullanımını gösterir <xref:System.Exception.Message%2A> . Çıktıda hata türü, sağlayıcı adını belirten kaynak, bir hata kodu ve hatayla ilişkili ileti görüntülenir.  
  
```vb  
Try  
    ' Do work here.  
Catch ex As DbException  
    ' Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType())  
    Console.WriteLine("Source: {0}", ex.Source)  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode)  
    Console.WriteLine("Message: {0}", ex.Message)  
Finally  
    ' Perform cleanup here.  
End Try  
```  
  
```csharp  
try  
{  
    // Do work here.  
}  
catch (DbException ex)  
{  
    // Display information about the exception.  
    Console.WriteLine("GetType: {0}", ex.GetType());  
    Console.WriteLine("Source: {0}", ex.Source);  
    Console.WriteLine("ErrorCode: {0}", ex.ErrorCode);  
    Console.WriteLine("Message: {0}", ex.Message);  
}  
finally  
{  
    // Perform cleanup here.  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DbProviderFactories](dbproviderfactories.md)
- [DbProviderFactory Alma](obtaining-a-dbproviderfactory.md)
- [DbDataAdapter ile Verileri Değiştirme](modifying-data-with-a-dbdataadapter.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
