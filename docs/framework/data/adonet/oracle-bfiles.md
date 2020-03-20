---
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: 40060a7ea8576e08140d972072d086606d640366
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149446"
---
# <a name="oracle-bfiles"></a>Oracle BFILE
Oracle için .NET Framework Data <xref:System.Data.OracleClient.OracleBFile> Provider, Oracle <xref:System.Data.OracleClient.OracleType.BFile> veri türüyle çalışmak için kullanılan sınıfı içerir.  
  
 Oracle **BFILE** veri türü, maksimum 4 gigabayt boyutuna sahip ikili verilere başvuru içeren bir Oracle **LOB** veri türüdür. Oracle **BFILE,** verilerinin sunucu yerine işletim sistemindeki fiziksel bir dosyada depolanması açısından diğer Oracle **LOB** veri türlerinden farklıdır. **BFILE** veri türünün verilere salt okunur erişim sağladığını unutmayın.  
  
 **Bir BFILE** veri türünün lob veri **LOB** türünden ayıran diğer özellikleri şunlardır:  
  
- Yapılandırılmamış veriler içerir.  
  
- Sunucu tarafı öbeklemi destekler.  
  
- Referans kopya semantik kullanır. Örneğin, bir **BFILE**üzerinde bir kopyalama işlemi gerçekleştirirseniz, yalnızca **BFILE** bulucu (dosyaya başvurudur) kopyalanır. Dosyadaki veriler kopyalanmaz.  
  
 **BFILE** veri türü boyutu büyük olan LOB'lara başvurmak için kullanılmalıdır ve bu nedenle veritabanında depolamak için pratik değildir. **LOB** veri türüyle karşılaştırıldığında bir **BFILE** veri türü kullanırken daha fazla istemci, sunucu ve iletişim yükü söz konusudur. Yalnızca az miktarda veri almanız **gerekiyorsa, Bir BFILE'ye** erişmek daha verimlidir. Nesnenin tamamını edinmeniz gerekiyorsa veritabanında yerleşik LOB'lara erişmek daha verimlidir.  
  
 NULL Olmayan **Her OracleBFile** nesnesi, temel fiziksel dosyanın konumunu tanımlayan iki varlıkla ilişkilidir:  
  
1. Dosya sistemindeki bir dizin için bir veritabanı diğer adı olan bir Oracle DIRECTORY nesnesi ve  
  
2. DIzin nesnesi ile ilişkili dizinde bulunan altta yatan fiziksel dosyanın dosya adı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki C# örneği, Oracle tablosunda nasıl bir **BFILE** oluşturabileceğinizi ve ardından **oracleBFile** nesnesi biçiminde nasıl alabileceğinizi gösterir. Örnek, nesnenin <xref:System.Data.OracleClient.OracleDataReader> ve **OracleBFile** **Ara** ve **Oku** yöntemlerinin kullanılmasını gösterir. Bu örneği kullanmak için öncelikle Oracle sunucusunda "c:\\\bfiles" adlı bir dizin ve "MyFile.jpg" adlı dosya oluşturmanız gerektiğini unutmayın.  
  
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
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle ve ADO.NET](oracle-and-adonet.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
