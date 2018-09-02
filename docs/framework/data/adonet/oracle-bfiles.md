---
title: Oracle Bfıle
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 683b4a9be826e1d0d4ee354fada10168d833e3d7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398796"
---
# <a name="oracle-bfiles"></a>Oracle Bfıle
Oracle için .NET Framework veri sağlayıcısı içerir <xref:System.Data.OracleClient.OracleBFile> Oracle ile çalışmak için kullanılan sınıfı <xref:System.Data.OracleClient.OracleType.BFile> veri türü.  
  
 Oracle **BDOSYA** veri türü olan Oracle **LOB** boyut sınırı 4 gigabayt ikili verilerle bir başvuru içeren veri türü. Oracle **BDOSYA** diğer Oracle'dan farklı **LOB** veri türlerini içeren, veriler işletim sistemi yerine fiziksel bir dosya sunucusunda depolanır. Unutmayın **BDOSYA** veri türü veri salt okunur erişim sağlar.  
  
 Diğer özelliklerini bir **BDOSYA** ondan ayırt veri türü bir **LOB** olan BT'nin veri türü:  
  
-   Yapılandırılmamış verileri içerir.  
  
-   Sunucu tarafı parçalama destekler.  
  
-   Kopyalama semantiği kullanan başvuru. Örneğin, bir kopyalama işlemi gerçekleştirirseniz bir **BDOSYA**, yalnızca **BDOSYA** (aynı dosyaya bir başvuru) Bulucu kopyalanır. Dosyadaki dosya kopyalanmaz.  
  
 **BDOSYA** veri türü, boyutu büyük LOB'lar başvurmak için kullanılması gerekir ve bu nedenle, veritabanında depolamak pratik değildir. Daha fazla istemci ve sunucu iletişimi ek yük dahil kullanırken bir **BDOSYA** veri türü ile karşılaştırıldığında **LOB** veri türü. Erişmek için daha verimli bir **BDOSYA** yalnızca az miktarda veriniz almak gerekiyorsa. Tüm nesnesi elde etmeniz gerekiyorsa veritabanı yerleşik LOB'lar erişmek için daha verimlidir.  
  
 NULL olmayan her **OracleBFile** nesne, temel alınan fiziksel dosya konumunu tanımlayan iki varlık ile ilişkilendirilmiş:  
  
1.  Dosya sistemindeki bir dizin için bir veritabanı diğer adı olan bir Oracle dizin nesnesi ve  
  
2.  Dizin nesneyle ilişkili dizinde bulunan temel alınan fiziksel dosyanın dosya adı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki C# örneği nasıl oluşturabileceğinizi gösteren bir **BDOSYA** bir Oracle tablo ve ardından bunu biçiminde alma bir **OracleBFile** nesne. Örnek kullanarak gösterir <xref:System.Data.OracleClient.OracleDataReader> nesne ve **OracleBFile** **arama** ve **okuma** yöntemleri. Bu örneği kullanmak için öncelikle adlı bir dizin oluşturmanız gerekir Not "c:\\\bfiles" ve "MyFile.jpg" Oracle sunucusunda adlı bir dosya.  
  
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
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
