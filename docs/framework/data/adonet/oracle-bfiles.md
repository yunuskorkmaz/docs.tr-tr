---
description: 'Daha fazla bilgi edinin: Oracle BFILEs'
title: Oracle BFILE
ms.date: 03/30/2017
ms.assetid: 341bbf84-4734-4d44-8723-ccedee954e21
ms.openlocfilehash: e1fda4ad4acb225dc9a70c92b2c4f2b1d61ab1d7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672497"
---
# <a name="oracle-bfiles"></a>Oracle BFILE

Oracle için .NET Framework Veri Sağlayıcısı, <xref:System.Data.OracleClient.OracleBFile> Oracle veri türüyle çalışmak için kullanılan sınıfını içerir <xref:System.Data.OracleClient.OracleType.BFile> .  
  
 Oracle **bDosya** veri türü, en fazla 4 gigabayt boyutlu ikili verilere başvuru Içeren bir Oracle **lob** veri türüdür. Oracle **bDosya** , verileri sunucu yerine işletim sistemindeki fiziksel bir dosyada depolanan diğer Oracle **lob** veri türlerinden farklıdır. **BDosya** veri türünün verilere salt okunurdur erişimi sağladığını unutmayın.  
  
 **Bir bu veri türünün** bir **lob** veri türünden ayırt edilmesini sağlayan diğer özellikleri şunlardır:  
  
- Yapılandırılmamış verileri içerir.  
  
- Sunucu tarafı parçalama destekler.  
  
- Başvuru kopyalama semantiğini kullanır. Örneğin, bir **bDosya** üzerinde kopyalama işlemi gerçekleştirirseniz, yalnızca **bDosya** Konumlandırıcı (dosyanın bir başvurusu) kopyalanır. Dosyadaki veriler kopyalanmaz.  
  
 **BDosya** veri türü,, boyutu büyük olan LOBs 'ye başvurmak için kullanılmalıdır ve bu nedenle veritabanında depolanması pratik değildir. **Lob** veri türü ile karşılaştırıldığında bir **bDosya** veri türü kullanılırken daha fazla istemci, sunucu ve iletişim yükü söz konusu olur. Yalnızca az miktarda veri edinmeniz gerekiyorsa, bir **bDosya** 'ya erişmek daha etkilidir. Nesnenin tamamını edinmeniz gerekiyorsa, veritabanına yerleşik lob 'Ları erişmek daha etkilidir.  
  
 NULL olmayan her bir **Oraclebdosya** nesnesi, temel alınan fiziksel dosyanın konumunu tanımlayan iki varlıkla ilişkilendirilir:  
  
1. Dosya sistemindeki bir dizin için veritabanı diğer adı olan Oracle DIZIN nesnesi ve  
  
2. DIZIN nesnesiyle ilişkili dizinde bulunan, temel alınan fiziksel dosyanın dosya adı.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki C# örneği, bir Oracle tablosunda bir **bDosya** oluşturup bunu bir **oraclebdosya** nesnesi biçiminde nasıl alabileceğinizi gösterir. Örnek, <xref:System.Data.OracleClient.OracleDataReader> nesnesinin ve **oraclebdosya** **Seek** ve **Read** yöntemlerinin kullanımını gösterir. Bu örneği kullanmak için, önce Oracle sunucusunda "c: \\ \bfiles" adlı bir dizin ve "MyFile.jpg" adlı dosya oluşturmanız gerektiğini unutmayın.  
  
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
