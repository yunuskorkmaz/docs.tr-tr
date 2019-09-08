---
title: DbConnection, DbCommand ve DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 09526f111adeecb817ce4c4e587ca3713e0d8cde
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785194"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection, DbCommand ve DbException
<xref:System.Data.Common.DbProviderFactory> Bir<xref:System.Data.Common.DbConnection>ve oluşturduktan sonra, veri kaynağından veri almak için komutlar ve veri okuyucularıyla çalışabilirsiniz.  
  
## <a name="retrieving-data-example"></a>Veri alma örneği  
 Bu örnek, bir `DbConnection` nesneyi bağımsız değişken olarak alır. Bir <xref:System.Data.Common.DbCommand> SQL SELECT ifadesine <xref:System.Data.Common.DbCommand.CommandText%2A> ayarlayarak Kategoriler tablosundan verileri seçmek için oluşturulur. Kod, kategori tablosunun veri kaynağında bulunduğunu varsayar. Bağlantı açılır ve veriler bir <xref:System.Data.Common.DbDataReader>kullanılarak alınır.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Komut örneği yürütme  
 Bu örnek, bir `DbConnection` nesneyi bağımsız değişken olarak alır. Geçerliyse bağlantı açılır <xref:System.Data.Common.DbCommand> ve oluşturulur ve yürütülür. `DbConnection` , <xref:System.Data.Common.DbCommand.CommandText%2A> Northwind veritabanındaki Categories tablosuna bir INSERT uygulayan SQL INSERT ifadesine ayarlanır. Kod, Northwind veritabanının veri kaynağında bulunduğunu ve INSERT ifadesinde kullanılan SQL sözdiziminin belirtilen sağlayıcı için geçerli olduğunu varsayar. Veri kaynağında oluşan hatalar <xref:System.Data.Common.DbException> kod bloğu tarafından işlenir ve diğer tüm özel durumlar <xref:System.Exception> bloğunda işlenir.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>DbException ile veri hatalarını işleme  
 <xref:System.Data.Common.DbException> Sınıfı, bir veri kaynağı adına oluşturulan tüm özel durumlar için temel sınıftır. Özel durum sınıfına başvuruda bulunmak zorunda kalmadan farklı sağlayıcılar tarafından oluşturulan özel durumları işlemek için özel durum işleme kodunuzda kullanabilirsiniz. Aşağıdaki kod <xref:System.Data.Common.DbException> parçası, <xref:System.Exception.Source%2A> <xref:System.Exception.GetType%2A> ,<xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, ve<xref:System.Exception.Message%2A> özelliklerini kullanarak veri kaynağı tarafından döndürülen hata bilgilerini göstermek için kullanımını gösterir. Çıktıda hata türü, sağlayıcı adını belirten kaynak, bir hata kodu ve hatayla ilişkili ileti görüntülenir.  
  
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
