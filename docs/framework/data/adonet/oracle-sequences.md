---
title: Oracle sıraları
ms.date: 03/30/2017
ms.assetid: 27cd371d-8252-414d-b5b2-5d31fa44b585
ms.openlocfilehash: 9f89234168351191c63d81fd4f3b68b01bfac2da
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="oracle-sequences"></a>Oracle sıraları
Oracle için .NET Framework veri sağlayıcısı kullanarak eklemeleri gerçekleştirildikten sonra anahtar Oracle sırası sunucu tarafından üretilen değerleri almak için destek sağlar <xref:System.Data.OracleClient.OracleDataAdapter>.  
  
 SQL Server ve Oracle birincil anahtarlar olarak belirlenebilir sütunları otomatik olarak artırma oluşturulmasını destekler. Tabloya satır eklendikçe bu değerleri sunucu tarafından üretilir. SQL Server'da bir sütunun kimliğini özelliğini ayarlayın; Oracle bir sırası oluşturun. Otomatik artış sütunları SQL Server ve Oracle sıralarında arasındaki farkı olan:  
  
-   SQL Server'daki bir sütun bir otomatik artım sütun olarak işaretlemek ve yeni satır eklediğinizde SQL Server sütunu için yeni değerleri otomatik olarak oluşturur.  
  
-   Oracle, bir sütun için yeni değerleri tablonuzda oluşturmak için bir sıra oluşturun ancak dizisi ve tablo veya sütun arasında doğrudan bağlantı yoktur. Bir Oracle sırası bir tablo ya da bir saklı yordam gibi bir nesnedir.  
  
 Bir Oracle veritabanına bir dizisi oluşturduğunuzda, ilk değerini ve Artım değerleri arasında tanımlayabilirsiniz. Yeni satırlar göndermeden önce yeni değerleri dizisi de sorgulayabilirsiniz. Veritabanına eklemeden önce kodunuzu yeni satırlar için anahtar değerleri tanıyabilmesi anlamına gelir.  
  
 SQL Server ve ADO.NET kullanarak otomatik artış sütunları oluşturma hakkında daha fazla bilgi için bkz: [alma kimliği veya sayı değerlerini](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md) ve [oluşturma AutoIncrement sütunları](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki C# örnek nasıl Oracle veritabanından yeni sırası değerleri alabilir gösterir. Örnek yeni satırlar göndermek için kullanılan INSERT INTO sorgusunu sırayla başvuruyor ve ardından Oracle10g içinde sunulan DÖNDÜRME yan tümcesi kullanılarak oluşturulan sıra değerini döndürür. Yeni satır bekleyen bir dizi örnek, bir <xref:System.Data.DataTable> ADO kullanarak. "Yer tutucu" birincil anahtar değerlerini oluşturmak için NET'in otomatik artım işlevselliği. Yeni satır için oluşturulan ADO.NET artış değeri "yer tutucusu" olduğuna dikkat edin. Veritabanı ADO.NET oluşturur olanlardan farklı değerler oluşturabilir anlamına gelir.  
  
 Veritabanında bekleyen eklemeleri göndermeden önce örnek satırları içeriğini görüntüler. Sonra yeni bir kod oluşturur <xref:System.Data.OracleClient.OracleDataAdapter> nesne ve kümeleri kendi <xref:System.Data.OracleClient.OracleDataAdapter.InsertCommand%2A> ve <xref:System.Data.OracleClient.OracleDataAdapter.UpdateBatchSize%2A> özellikleri. Örnek Çıktı parametreleri kullanarak sunucu tarafından üretilen değerler döndürmesine mantığı da sağlar. Ardından, örnek bekleyen satırları göndermek için güncelleştirme yürütür ve içeriğini görüntüler <xref:System.Data.DataTable>.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Oracle ve ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
