---
title: DbConnection, DbCommand ve DbException
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
ms.assetid: 58aab611-7e6f-4749-b983-28ab7ae87dbe
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f6fb5783ad8d0863ffcce0665795081c6f2041d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="dbconnection-dbcommand-and-dbexception"></a>DbConnection, DbCommand ve DbException
Oluşturduktan sonra bir <xref:System.Data.Common.DbProviderFactory> ve <xref:System.Data.Common.DbConnection>, sonra veri kaynağından veri almak için komutlar ve veri okuyucu ile çalışabilirsiniz.  
  
## <a name="retrieving-data-example"></a>Veri örneği alınıyor  
 Bu örnekte geçen bir `DbConnection` bağımsız değişken olarak nesne. A <xref:System.Data.Common.DbCommand> ayarlayarak kategoriler tablosundan verileri seçmek için oluşturulan <xref:System.Data.Common.DbCommand.CommandText%2A> SQL SELECT deyimi. Kod, kategoriler tablosu veri kaynağında var olduğunu varsayar. Bağlantı açıldığında ve veriler kullanılarak alınır bir <xref:System.Data.Common.DbDataReader>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommandData#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommandData/VB/source.vb#1)]  
  
## <a name="executing-a-command-example"></a>Bir komut örneği çalıştırma  
 Bu örnekte geçen bir `DbConnection` bağımsız değişken olarak nesne. Varsa `DbConnection` bağlantı açıldığında geçerli olduğundan ve bir <xref:System.Data.Common.DbCommand> oluşturulan ve yürütülemiyor. <xref:System.Data.Common.DbCommand.CommandText%2A> Northwind veritabanına kategorileri tabloya INSERT gerçekleştiren bir SQL INSERT deyimi için ayarlayın. Kod, Northwind veritabanı veri kaynağında var olduğunu ve INSERT deyiminde kullanılan SQL söz dizimi belirtilen sağlayıcı için geçerli olduğunu varsayar. Veri kaynağında oluşan hatalar tarafından işlenmesini <xref:System.Data.Common.DbException> kod bloğu ve diğer tüm özel durumları işlenir <xref:System.Exception> bloğu.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbCommand#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbCommand/VB/source.vb#1)]  
  
## <a name="handling-data-errors-with-dbexception"></a>DbException ile veri hataları işleme  
 <xref:System.Data.Common.DbException> Sınıfı, bir veri kaynağı adına oluşturulan tüm özel durumlar için temel sınıf. Bir özel durum sınıfı başvurmak zorunda kalmadan farklı sağlayıcıları tarafından oluşturulan özel durumları işlemek için özel durum işleme kodunu bunu kullanabilirsiniz. Aşağıdaki kod parçası nasıl kullanılacağı ortaya <xref:System.Data.Common.DbException> veri kaynağını kullanarak döndürülen hata bilgileri görüntülemek için <xref:System.Exception.GetType%2A>, <xref:System.Exception.Source%2A>, <xref:System.Runtime.InteropServices.ExternalException.ErrorCode%2A>, ve <xref:System.Exception.Message%2A> özellikleri. Çıkış hata, sağlayıcı adı, hata kodu ve hata ile ilişkili ileti gösteren kaynak türünü görüntüler.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [Bir DbProviderFactory alma](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [Bir DbDataAdapter verilerle değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
