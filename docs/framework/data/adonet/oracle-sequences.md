---
title: Oracle Dizileri
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: 8fe7513093d06f3928540f2de8cba902ce62b56e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878460"
---
# <a name="oracle-sequences"></a>Oracle Dizileri
Oracle için .NET Framework veri sağlayıcısı kullanarak ekler gerçekleştirdikten sonra anahtar Oracle sırası sunucu tarafından oluşturulan değerleri almak için destek sağlar. <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
 SQL Server ve Oracle, birincil anahtar olarak belirlenebilir sütunları otomatik olarak artırma oluşturmayı destekler. Tabloya satır eklendikçe bu değerler sunucu tarafından oluşturulur. SQL Server'da, bir sütunun kimlik özelliği ayarlayın; Oracle bir dizi oluşturun. Otomatik artış sütunları SQL Server ve Oracle dizileri arasındaki fark olmasıdır:  
  
- SQL Server'daki sütun otomatik artış sütunu olarak işaretlemek ve yeni bir satır ekleyin, SQL Server otomatik olarak yeni sütun değerlerini oluşturur.  
  
- Oracle, tablonuzda bir sütun için yeni değerler oluşturmak için bir sıra oluşturmak, ancak sıra ve tablo veya sütun arasında doğrudan bağlantı yoktur. Oracle dizisi, bir tablo veya saklı yordam gibi bir nesnedir.  
  
 Bir Oracle veritabanında bir dizi oluşturduğunuzda, bunun başlangıçtaki değerini ve Artım değerleri arasında tanımlayabilirsiniz. Ayrıca, yeni satırları göndermeden önce yeni değerler dizisi sorgulayabilirsiniz. Veritabanına eklemeden önce anahtar değerlerinin yeni satırlar için kodunuzu tanıyabilmesi anlamına gelir.  
  
 SQL Server ve ADO.NET kullanarak otomatik artış sütunları oluşturma hakkında daha fazla bilgi için bkz. [alınırken kimlik veya otomatik sayı değerlerini](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md) ve [AutoIncrement sütunları oluşturma](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki C# örneği, nasıl Oracle veritabanından yeni dizisi değerleri alabilir gösterir. Örneğin, yeni satırlar göndermek için kullanılan INSERT INTO sorgusunu sırayla başvuruyor ve Oracle10g içinde tanıtılan DÖNDÜRME yan tümcesi kullanılarak oluşturulan dizisi değeri döndürür. Örnek, bir dizi yeni satırlarda bekleyen ekler. bir <xref:System.Data.DataTable> ADO kullanarak. NET otomatik artış işlevi "yer tutucusunu" birincil anahtar değerlerini oluşturur. ADO.NET için yeni satır oluşturulan değeri Artır "yer tutucusu" olduğuna dikkat edin. Bu, veritabanının ADO.NET oluşturur olanlardan farklı değerler üretebilir anlamına gelir.  
  
 Bekleyen eklemeleri veritabanına göndermeden önce örnek satırlar içeriğini görüntüler. Ardından, yeni bir kod oluşturur <xref:System.Data.OracleClient.OracleDataAdapter> nesne ve ayarlar, <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> ve <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> özellikleri. Örnek Çıktı parametreleri kullanarak sunucu tarafından oluşturulan değerleri döndürülme mantığının de sağlar. Örnek daha sonra bekleyen satırları göndermek için güncelleştirme yürütür ve içeriğini görüntüler <xref:System.Data.DataTable>.  
  
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

- [Oracle ve ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
