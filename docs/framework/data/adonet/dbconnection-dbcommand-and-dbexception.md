---
title: DbConnection, DbCommand ve DbException
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
ms.openlocfilehash: 31bd23d854afd10d0c292042ac3963978de5fd4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725252"
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection, DbCommand ve DbException
Oluşturduktan sonra bir <xref:System.Data.Common.DbProviderFactory> ve <xref:System.Data.Common.DbConnection>, sonra verileri veri kaynağından almak için komutlar ve veri okuyucu ile çalışabilirsiniz.  
  
## <a name="retrieving-data-example"></a>Örnek veri alma  
 Bu örnek alan bir `DbConnection` bağımsız değişken olarak nesnesi. A <xref:System.Data.Common.DbCommand> ayarlayarak kategoriler tablosundan verileri seçmek için oluşturulan <xref:System.Data.Common.DbCommand.CommandText%2A> SQL SELECT deyimi. Kod kategorileri tablosu veri kaynağında bulunduğunu varsayar. Bağlantı açıldığında ve verileri kullanarak alınır bir <xref:System.Data.Common.DbDataReader>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Bir komut örneği çalıştırma  
 Bu örnek alan bir `DbConnection` bağımsız değişken olarak nesnesi. Varsa `DbConnection` bağlantısı açıldığında, geçerli olduğundan ve <xref:System.Data.Common.DbCommand> oluşturulan ve yürütüldü. <xref:System.Data.Common.DbCommand.CommandText%2A> Kategorileri tabloya bir INSERT Northwind veritabanında gerçekleştiren SQL INSERT deyimi ayarlayın. Kod, Northwind veritabanına veri kaynağında var olduğundan ve INSERT deyiminde kullanılan SQL söz dizimi belirtilen sağlayıcı için geçerli olduğunu varsayar. Veri kaynağından oluşan hatalar olarak işlenmesini <xref:System.Data.Common.DbException> kod bloğu ve diğer tüm özel durumlar işlenir <xref:System.Exception> blok.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>DbException ile veri hataları işleme  
 <xref:System.Data.Common.DbException> Adına bir veri kaynağı oluşturulan tüm özel durumlar için temel sınıfı. Bir özel durum sınıfı başvurmak zorunda kalmadan farklı sağlayıcıları tarafından oluşturulan özel durumları işlemek için özel durum işleme kodunu bunu kullanabilirsiniz. Aşağıdaki kod parçası nasıl kullanılacağını gösteren <xref:System.Data.Common.DbException> kullanarak veri kaynağına tarafından döndürülen hata bilgileri görüntülemek için <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, ve <xref:System.Exception.Message%2A> özellikleri. Çıkış, hata, sağlayıcı adı, bir hata kodu ve şu hata ile ilişkili ileti belirten bir kaynak türünü görüntüler.  
  
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
- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [DbProviderFactory Alma](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [DbDataAdapter ile Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
