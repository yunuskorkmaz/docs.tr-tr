---
title: Oracle BFILEs
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: f48bd85559d55d9a1190310bcf13cd4a68625011
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="oracle-bfiles"></a>Oracle BFILEs
Oracle için .NET Framework veri sağlayıcısı içerir <xref:System.Data.OracleClient.OracleBFile> Oracle ile çalışmak için kullanılan sınıf <xref:System.Data.OracleClient.OracleType.BFile> veri türü.  
  
 Oracle **BDOSYA** veri türü olan bir Oracle **LOB** en fazla 4 gigabayt ikili veriler için bir başvuru içeren veri türü. Bir Oracle **BDOSYA** diğer Oracle'dan farklı **LOB** verilerini işletim sisteminde yerine fiziksel bir dosya sunucusunda depolanan, veri türleri. Unutmayın **BDOSYA** veri türü veri salt okunur erişim sağlar.  
  
 Diğer özelliklerini bir **BDOSYA** buradan ayırt veri türü bir **LOB** veri türü olan şekilde:  
  
-   Yapılandırılmamış verileri içerir.  
  
-   Sunucu tarafı Öbekleme destekler.  
  
-   Kopyalama Semantiğini kullanır başvuru. Örneğin, bir kopyalama işlemi gerçekleştirirseniz bir **BDOSYA**, yalnızca **BDOSYA** (Bu bir dosyaya başvuru) Bulucu kopyalanır. Veri dosyasında kopyalanmaz.  
  
 **BDOSYA** veri türü boyutu büyük LOB'lar başvurmak için kullanılması gerekir ve bu nedenle, veritabanında depolamak pratik. Daha fazla istemci ve sunucu iletişimi yükünü kullanırken katılan bir **BDOSYA** veri türü ile karşılaştırıldığında **LOB** veri türü. Erişim daha verimli bir **BDOSYA** yalnızca çok küçük miktarda veri edinmeniz gerekiyorsa. Nesnenin tamamı edinmeniz gerekiyorsa veritabanı yerleşik LOB'lar erişmek için daha verimli olur.  
  
 NULL olmayan her **OracleBFile** nesne temel alınan fiziksel dosya konumunu tanımlayan iki varlık ile ilişkili değil:  
  
1.  Dosya sisteminde bir dizin için bir veritabanı diğer adı olan bir Oracle dizin nesnesi ve  
  
2.  Dizin nesneyle ilişkili dizininde bulunan temel alınan fiziksel dosya, dosya adı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki C# örnek nasıl oluşturabileceğinizi gösteren bir **BDOSYA** bir Oracle tablo ve biçiminde almak bir **OracleBFile** nesnesi. Örnek kullanılmasını gösterir <xref:System.Data.OracleClient.OracleDataReader> nesne ve **OracleBFile** **Seek** ve **okuma** yöntemleri. Bu örneği kullanmak için öncelikle adlı bir dizin oluşturmanız gerekir Not "c:\\\bfiles" ve "MyFile.jpg" adlı Oracle Sunucusu üzerinde dosya.  
  
```csharp  
using System;  
using System.IO;  
using System.Data;  
using System.Data.OracleClient;  
  
public class Sample  
{  
   public static void Main(string[] args)  
   {  
      OracleConnection connection = new OracleConnection(  
        "Data Source=Oracle8i;Integrated Security=yes");  
      connection.Open();  
  
      OracleCommand command = connection.CreateCommand();  
      command.CommandText =   
        "CREATE or REPLACE DIRECTORY MyDir as 'c:\\bfiles'";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "DROP TABLE MyBFileTable";  
      try {  
        command.ExecuteNonQuery();  
      }  
      catch {  
      }  
      command.CommandText =   
        "CREATE TABLE MyBFileTable(col1 number, col2 BFILE)";  
      command.ExecuteNonQuery();  
      command.CommandText =   
        "INSERT INTO MyBFileTable values ('2', BFILENAME('MyDir', " +  
        "'MyFile.jpg'))";  
      command.ExecuteNonQuery();  
      command.CommandText = "SELECT * FROM MyBFileTable";  
  
        byte[] buffer = new byte[100];  
  
      OracleDataReader reader = command.ExecuteReader();  
      using (reader) {  
          if (reader.Read()) {  
                OracleBFile bFile = reader.GetOracleBFile(1);  
                using (bFile) {  
                  bFile.Seek(0, SeekOrigin.Begin);  
                  bFile.Read(buffer, 0, 100);  
              }  
          }  
      }  
  
      connection.Close();  
   }  
  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oracle ve ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
