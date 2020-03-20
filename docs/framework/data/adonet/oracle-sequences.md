---
title: Oracle Dizileri
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: d6e6bb51b8bd317c7161500b89993be689659fad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149420"
---
# <a name="oracle-sequences"></a>Oracle Dizileri
Oracle için .NET Framework Data Provider, eklerin sataşlarını kullanarak yaptıktan sonra sunucu tarafından <xref:System.Data.OracleClient.OracleDataAdapter>oluşturulan anahtar Oracle Sequence değerlerini almak için destek sağlar.  
  
 SQL Server ve Oracle, birincil anahtar olarak atanabilecek otomatik olarak artan sütunların oluşturulmasını destekler. Satırlar tabloya eklendikçe, bu değerler sunucu tarafından oluşturulur. SQL Server'da bir sütunun Kimlik özelliğini ayarlarsınız; Oracle'da bir Dizi oluşturursunuz. SQL Server'daki otomatik artış sütunları ile Oracle'daki diziler arasındaki fark şudur:  
  
- SQL Server'da, bir sütunu otomatik artış sütunu olarak işaretlersiniz ve SQL Server yeni bir satır eklediğinizde sütun için otomatik olarak yeni değerler oluşturur.  
  
- Oracle'da, tablonuzdaki bir sütun için yeni değerler oluşturmak için bir sıra oluşturursunuz, ancak sıra ile tablo veya sütun arasında doğrudan bir bağlantı yoktur. Oracle dizisi, tablo veya depolanan yordam gibi bir nesnedir.  
  
 Oracle veritabanında bir dizi oluşturduğunuzda, ilk değerini ve değerleri arasındaki artış tanımlayabilirsiniz. Ayrıca, yeni satırlar göndermeden önce sırayı yeni değerler için sorgulayabilirsiniz. Bu, kodunuzu veritabanına eklemeden önce yeni satırlar için anahtar değerleri tanıyabilir anlamına gelir.  
  
 SQL Server ve ADO.NET kullanarak otomatik artış sütunları oluşturma hakkında daha fazla bilgi [için](retrieving-identity-or-autonumber-values.md) [Creating AutoIncrement Columns](./dataset-datatable-dataview/creating-autoincrement-columns.md)bkz.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki C# örneği, Oracle veritabanından yeni sıra değerlerini nasıl alabileceğinizi gösterir. Örnek, yeni satırları göndermek için kullanılan INSERT INTO sorgusundaki sıraya başvurur ve oracle10g'da tanıtılan RETURNING yan tümcesi kullanılarak oluşturulan sıra değerini döndürür. Örnek, ADO kullanarak bekleyen <xref:System.Data.DataTable> yeni satırlar bir dizi ekler. NET'in birincil anahtar değerlerini "yer tutucu" oluşturmak için otomatik artış işlevselliği. Yeni satır için oluşturulan ADO.NET artış değerinin sadece bir "yer tutucu" olduğunu unutmayın. Bu, veritabanının ADO.NET oluşturduklarından farklı değerler oluşturabileceği anlamına gelir.  
  
 Bekleyen ekler veritabanına göndermeden önce, örnek satırların içeriğini görüntüler. Daha sonra, kod yeni <xref:System.Data.OracleClient.OracleDataAdapter> bir nesne <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> oluşturur <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> ve onun ve özelliklerini ayarlar. Örnek, çıkış parametrelerini kullanarak sunucu tarafından oluşturulan değerleri döndürmek için de mantık sağlar. Daha sonra, örnek bekleyen satırları göndermek için güncelleştirmeyi yürütür <xref:System.Data.DataTable>ve içeriğini görüntüler.  
  
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
