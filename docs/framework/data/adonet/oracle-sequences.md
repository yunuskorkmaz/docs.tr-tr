---
title: Oracle Dizileri
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: 5e979a0a6750a654a69522d1fb10cdfa7242b893
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189168"
---
# <a name="oracle-sequences"></a>Oracle Dizileri

Oracle için .NET Framework Veri Sağlayıcısı, kullanarak ekleme gerçekleştirildikten sonra, sunucu tarafından oluşturulan anahtar Oracle dizi değerlerinin alınması için destek sağlar <xref:System.Data.OracleClient.OracleDataAdapter> .  
  
 SQL Server ve Oracle, birincil anahtar olarak belirlenebilir sütunları otomatik olarak arttırın oluşturulmasını destekler. Bu değerler, bir tabloya satırlar eklendikçe sunucu tarafından oluşturulur. SQL Server, bir sütunun Identity özelliğini ayarlarsınız; Oracle 'da bir sıra oluşturursunuz. Oracle 'daki SQL Server ve diziler içindeki otomatik artırma sütunları arasındaki fark şudur:  
  
- SQL Server, bir sütunu otomatik artış sütunu olarak işaretlersiniz ve yeni bir satır eklediğinizde SQL Server otomatik olarak sütun için yeni değerler oluşturur.  
  
- Oracle 'da, tablonuzdaki bir sütun için yeni değerler oluşturmak üzere bir dizi oluşturur, ancak sıra ile tablo veya sütun arasında doğrudan bir bağlantı yoktur. Oracle dizisi, tablo veya saklı yordam gibi bir nesnedir.  
  
 Oracle veritabanında bir dizi oluşturduğunuzda, başlangıç değerini ve değerleri arasındaki artışı tanımlayabilirsiniz. Yeni satırları göndermeden önce yeni değerler için de sırayı sorgulayabilirsiniz. Bu, kodunuzun veritabanına eklemeden önce yeni satırlar için anahtar değerlerini tanıyabileceği anlamına gelir.  
  
 SQL Server ve ADO.NET kullanarak otomatik artış sütunları oluşturma hakkında daha fazla bilgi için bkz. [kimlik veya OtomatikSayı değerlerini alma](retrieving-identity-or-autonumber-values.md) ve [AutoIncrement sütunları oluşturma](./dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki C# örneği, Oracle veritabanından nasıl yeni dizi değerleri alacağınızı gösterir. Örnek, yeni satırları göndermek için kullanılan INSERT INTO sorgusunda bulunan diziye başvurur ve sonra Oracle10g içinde tanıtılan döndürme yan tümcesi kullanılarak oluşturulan dizi değerini döndürür. Örnek, ADO kullanarak bir dizi bekleyen yeni satır ekler <xref:System.Data.DataTable> . "Yer tutucu" birincil anahtar değerleri oluşturmak için NET 'in otomatik artış işlevselliği. Yeni satır için ADO.NET artış değeri yalnızca bir "PlaceHolder" olduğunu unutmayın. Bu, veritabanının ADO.NET tarafından oluşturulanlarından farklı değerler üretebileceği anlamına gelir.  
  
 Bekleyen eklemeleri veritabanına göndermeden önce, örnek satırların içeriğini görüntüler. Ardından, kod yeni bir nesne oluşturur <xref:System.Data.OracleClient.OracleDataAdapter> ve <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> ve <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> özelliklerini ayarlar. Örnek ayrıca çıkış parametrelerini kullanarak sunucu tarafından oluşturulan değerleri döndürme mantığını sağlar. Daha sonra örnek, bekleyen satırları göndermek için güncelleştirmeyi yürütür ve içeriğini görüntüler <xref:System.Data.DataTable> .  
  
```csharp  
public void OracleSequence(String connectionString)  
{  
   String insertString =
      "INSERT INTO SequenceTest_Table (ID, OtherColumn)" +  
      "VALUES (SequenceTest_Sequence.NEXTVAL, :OtherColumn)" +  
      "RETURNING ID INTO :ID";  
  
   using (OracleConnection conn = new OracleConnection(connectionString))  
   {  
      //Open a connection.  
      conn.Open();  
      OracleCommand cmd = conn.CreateCommand();  
  
      // Prepare the database.  
      cmd.CommandText = "DROP SEQUENCE SequenceTest_Sequence";  
      try { cmd.ExecuteNonQuery(); } catch { }  
  
      cmd.CommandText = "DROP TABLE SequenceTest_Table";  
      try { cmd.ExecuteNonQuery(); } catch { }  
  
      cmd.CommandText = "CREATE TABLE SequenceTest_Table " +  
                     "(ID int PRIMARY KEY, OtherColumn varchar(255))";  
      cmd.ExecuteNonQuery();  
  
      cmd.CommandText = "CREATE SEQUENCE SequenceTest_Sequence " +  
                        "START WITH 100 INCREMENT BY 5";  
      cmd.ExecuteNonQuery();  
  
      DataTable testTable = new DataTable();  
      DataColumn column = testTable.Columns.Add("ID", typeof(int));  
      column.AutoIncrement = true;  
      column.AutoIncrementSeed = -1;  
      column.AutoIncrementStep = -1;  
      testTable.PrimaryKey = new DataColumn[] { column };  
      testTable.Columns.Add("OtherColumn", typeof(string));  
      for (int rowCounter = 1; rowCounter <= 15; rowCounter++)  
      {  
         testTable.Rows.Add(null, "Row #" + rowCounter.ToString());  
      }  
  
      Console.WriteLine("Before Update => ");  
      foreach (DataRow row in testTable.Rows)  
      {  
         Console.WriteLine("   {0} - {1}", row["ID"], row["OtherColumn"]);  
      }  
      Console.WriteLine();  
  
      cmd.CommandText =
        "SELECT ID, OtherColumn FROM SequenceTest_Table";  
      OracleDataAdapter da = new OracleDataAdapter(cmd);  
      da.InsertCommand = new OracleCommand(insertString, conn);  
      da.InsertCommand.Parameters.Add(":ID", OracleType.Int32, 0, "ID");  
      da.InsertCommand.Parameters[0].Direction = ParameterDirection.Output;  
      da.InsertCommand.Parameters.Add(":OtherColumn", OracleType.VarChar, 255, "OtherColumn");  
      da.InsertCommand.UpdatedRowSource = UpdateRowSource.OutputParameters;  
      da.UpdateBatchSize = 10;  
  
      da.Update(testTable);  
  
      Console.WriteLine("After Update => ");  
      foreach (DataRow row in testTable.Rows)  
      {  
         Console.WriteLine("   {0} - {1}", row["ID"], row["OtherColumn"]);  
      }  
      // Close the connection.  
      conn.Close();  
   }  
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Oracle ve ADO.NET](oracle-and-adonet.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
