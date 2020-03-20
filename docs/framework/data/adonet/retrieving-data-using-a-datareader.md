---
title: DataReader Kullanarak Veri Alma
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 88cd85ce343aaab08b944f81c9659918014da0a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149030"
---
# <a name="retrieve-data-using-a-datareader"></a>DataReader kullanarak veri alma
**DataReader**kullanarak veri almak için Komut **nesnesinin** bir örneğini oluşturun ve ardından veri kaynağından satırları almak için **Command.ExecuteReader'ı** arayarak bir **DataReader** oluşturun. **DataReader,** yordam mantığının bir veri kaynağından elde edilen sonuçları sırayla verimli bir şekilde işlemesini sağlayan, engellenmemiş bir veri akışı sağlar. Veriler bellekte önbelleğe alınmadığından, büyük miktarda veri alırken **DataReader** iyi bir seçimdir.

Aşağıdaki örnek, geçerli bir DataReader'ı temsil eden `command` ve geçerli bir Komut nesnesini temsil eden `reader` bir **DataReader'ı**kullanarak gösteriş gösterir.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Sorgu sonuçlarından bir satır elde etmek için **DataReader.Read** yöntemini kullanın. Döndürülen satırın her sütununa, sütunun adını veya ordinal numarasını **DataReader'a**geçirerek erişebilirsiniz. Ancak, en iyi performans **için, DataReader** kendi yerel veri türlerinde sütun değerlerine erişmenizi sağlayan bir dizi yöntem sağlar **(GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, vb). Veri sağlayıcısına özgü **DataReaders**için dakti-yazılı erişimci <xref:System.Data.SqlClient.SqlDataReader>yöntemlerin listesi için bkz. <xref:System.Data.OleDb.OleDbDataReader> Temel veri türünü bildiğinizde yazılan erişimci yöntemlerikullanmak, sütun değerini alırken gereken tür dönüştürme miktarını azaltır.  
  
 Aşağıdaki örnek, bir **DataReader nesnesi** üzerinden yineler ve her satırdan iki sütun döndürür.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>DataReader'ı Kapatma  
 **DataReader** nesnesini kullanmayı bitirdiğinizde her zaman **Kapat** yöntemini arayın.  
  
 **Komutunuz** çıktı parametreleri veya iade değerleri içeriyorsa, **DataReader** kapatılana kadar bu değerler kullanılamaz.  
  
 Bir **DataReader** açık ken, **Bağlantı** yalnızca bu **DataReader**tarafından kullanılmaktadır. Özgün **DataReader** kapatılana **kadar,** başka bir **DataReader**oluşturma da dahil olmak üzere Bağlantı için herhangi bir komut yürütemezsiniz.  
  
> [!NOTE]
> Sınıfınızın **Finalize** yönteminde **Bağlantıyı** **Kapat** veya **Elden Çıkar'ı,** **DataReader'ı**veya yönetilen başka bir nesneyi aramayın. Sonlandırıcıda, yalnızca sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın. Sınıfınız yönetilmeyen kaynaklara sahip değilse, sınıf tanımınıza bir **Sonlandırma** yöntemi eklemeyin. Daha fazla bilgi için [Çöp Toplama'ya](../../../standard/garbage-collection/index.md)bakın.  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>NextResult kullanarak birden çok sonuç kümesi alma  
 **DataReader** birden çok sonuç kümesi döndürürse, sonuç kümeleri aracılığıyla sırayla yinelemek için **NextResult** yöntemini arayın. Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlDataReader> yöntemi kullanarak iki SELECT deyiminin sonuçlarını işleme gösterir. <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>DataReader'dan şema bilgisi alma  
 **DataReader** açıkken, **GetSchemaTable** yöntemini kullanarak geçerli sonuç kümesi hakkında şema bilgilerini alabilirsiniz. **GetSchemaTable,** <xref:System.Data.DataTable> geçerli sonuç kümesiiçin şema bilgilerini içeren satırlar ve sütunlarla dolu bir nesneyi döndürür. **DataTable,** sonuç kümesinin her sütunu için bir satır içerir. Şema tablosunun her sütunu, sonuç kümesinin satırlarında döndürülen sütunların bir özelliğiyle eşlenir, **sütun adı** özelliğin adıdır ve sütunun değeri özelliğin değeridir. Aşağıdaki örnek, **DataReader**için şema bilgilerini yazar.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>OLE DB bölümleri ile çalışma  
 Hiyerarşik sıra kümeleri veya bölümler (OLE DB türü **DBTYPE_HCHAPTER**, ADO <xref:System.Data.OleDb.OleDbDataReader>türü **adChapter**), . Bir bölümü içeren bir sorgu **DataReader**olarak döndürüldüğünde, bölüm bu **DataReader'da** sütun olarak döndürülür ve **DataReader nesnesi** olarak açıklanır.  
  
 ADO.NET **DataSet,** tablolar arasındaki üst-alt ilişkileri kullanarak hiyerarşik satır kümelerini temsil etmek için de kullanılabilir. Daha fazla bilgi için [Bkz. Veri Kümeleri, Veri Tabloları ve Veri Görünümleri.](./dataset-datatable-dataview/index.md)  
  
 Aşağıdaki kod örneği, müşteri listesindeki her müşteri için bir sipariş bölümü sütunu oluşturmak için MSDataShape Sağlayıcısı'nı kullanır.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" &
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")

    Using custCMD As OleDbCommand = New OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " &
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " &
        "RELATE CustomerID TO CustomerID)", connection)

        connection.Open()

        Using custReader As OleDbDataReader = custCMD.ExecuteReader()

            Do While custReader.Read()
                Console.WriteLine("Orders for " & custReader.GetString(1))
                ' custReader.GetString(1) = CompanyName  

                Using orderReader As OleDbDataReader = custReader.GetValue(2)
                    ' custReader.GetValue(2) = Orders chapter as DataReader  

                    Do While orderReader.Read()
                        Console.WriteLine(vbTab & orderReader.GetInt32(1))
                        ' orderReader.GetInt32(1) = OrderID  
                    Loop
                    orderReader.Close()
                End Using
            Loop
            ' Make sure to always close readers and connections.  
            custReader.Close()
        End Using
    End Using
End Using
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection(
    "Provider=MSDataShape;Data Provider=SQLOLEDB;" +
    "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"))
{
    using (OleDbCommand custCMD = new OleDbCommand(
        "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +
        "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +
        "RELATE CustomerID TO CustomerID)", connection))
    {
        connection.Open();

        using (OleDbDataReader custReader = custCMD.ExecuteReader())
        {

            while (custReader.Read())
            {
                Console.WriteLine("Orders for " + custReader.GetString(1));
                // custReader.GetString(1) = CompanyName  

                using (OleDbDataReader orderReader = (OleDbDataReader)custReader.GetValue(2))
                {
                    // custReader.GetValue(2) = Orders chapter as DataReader  

                    while (orderReader.Read())
                        Console.WriteLine("\t" + orderReader.GetInt32(1));
                    // orderReader.GetInt32(1) = OrderID  
                    orderReader.Close();
                }
            }
            // Make sure to always close readers and connections.  
            custReader.Close();
        }
    }
}
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Oracle REF CURSOR ile sonuçları döndürme  
 Oracle için .NET Framework Data Provider, bir sorgu sonucunu döndürmek için Oracle REF CURSOR kullanımını destekler. Bir Oracle REF CURSOR <xref:System.Data.OracleClient.OracleDataReader>olarak döndürülür.  
  
 Yöntemi kullanarak <xref:System.Data.OracleClient.OracleDataReader> Oracle REF CURSOR'u temsil eden bir nesne alabilirsiniz. <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> Ayrıca, <xref:System.Data.OracleClient.OracleCommand> bir veya daha fazla Oracle REF CURSOR'u <xref:System.Data.OracleClient.OracleDataAdapter> **selectcommand** olarak döndüren bir <xref:System.Data.DataSet>tane de belirtebilirsiniz.  
  
 Oracle veri kaynağından döndürülen bir REF CURSOR'a erişmek için, sorgunuz için bir sorun <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleCommand.Parameters> oluşturun ve <xref:System.Data.OracleClient.OracleCommand>REF CURSOR'unuzun koleksiyonuna başvuran bir çıktı parametresi ekleyin. Parametrenin adı, sorgunuzdaki REF CURSOR parametresinin adıile eşleşmelidir. Parametrenin türünü <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>' e ayarlama <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> İade yönteminref <xref:System.Data.OracleClient.OracleCommand> CURSOR için bir. <xref:System.Data.OracleClient.OracleDataReader>  
  
 Birden <xref:System.Data.OracleClient.OracleCommand> çok REF CURSORs döndürürseniz, birden çok çıkış parametresi ekleyin. Yöntemi arayarak farklı REF CURSOR'lara <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> erişebilirsiniz. İlk REF <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> CURSOR'a başvuran bir <xref:System.Data.OracleClient.OracleDataReader> başvuruyu döndürme çağrısı. Daha sonra sonraki <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> REF CURSOR erişmek için yöntemi arayabilirsiniz. Koleksiyonunuzdaki <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> parametreler REF CURSOR çıkış parametrelerine <xref:System.Data.OracleClient.OracleDataReader> göre ada göre eşleşse de, bunlara <xref:System.Data.OracleClient.OracleCommand.Parameters> koleksiyona eklendikleri sırada erişir.  
  
 Örneğin, aşağıdaki Oracle paket ve paket gövdesini göz önünde bulundurun.  
  
```sql
CREATE OR REPLACE PACKAGE CURSPKG AS
  TYPE T_CURSOR IS REF CURSOR;
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,
    DEPTCURSOR OUT T_CURSOR);
END CURSPKG;  
  
CREATE OR REPLACE PACKAGE BODY CURSPKG AS
  PROCEDURE OPEN_TWO_CURSORS (EMPCURSOR OUT T_CURSOR,
    DEPTCURSOR OUT T_CURSOR)
  IS
  BEGIN
    OPEN EMPCURSOR FOR SELECT * FROM DEMO.EMPLOYEE;
    OPEN DEPTCURSOR FOR SELECT * FROM DEMO.DEPARTMENT;
  END OPEN_TWO_CURSORS;
END CURSPKG;
```  
  
 Aşağıdaki kod, <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> koleksiyona iki tür parametre ekleyerek önceki Oracle paketinden REF CURSOR'ları döndüren bir kod oluşturur.  
  
```vb  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
```  
  
```csharp  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
```  
  
 Aşağıdaki kod önceki komutun <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> <xref:System.Data.OracleClient.OracleDataReader>sonuçlarını . REF CURSOR parametreleri sırayla döndürülür.  
  
```vb  
oraConn.Open()  
  
Dim cursCmd As OracleCommand = New OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn)  
cursCmd.CommandType = CommandType.StoredProcedure  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output  
  
Dim reader As OracleDataReader = cursCmd.ExecuteReader()  
  
Console.WriteLine(vbCrLf & "Emp ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2))  
Loop  
  
reader.NextResult()  
  
Console.WriteLine(vbCrLf & "Dept ID" & vbTab & "Name")  
  
Do While reader.Read()  
  Console.WriteLine("{0}" & vbTab & "{1}", reader.GetOracleNumber(0), reader.GetString(1))  
Loop  
' Make sure to always close readers and connections.  
reader.Close()  
oraConn.Close()  
```  
  
```csharp  
oraConn.Open();  
  
OracleCommand cursCmd = new OracleCommand("CURSPKG.OPEN_TWO_CURSORS", oraConn);  
cursCmd.CommandType = CommandType.StoredProcedure;  
cursCmd.Parameters.Add("EMPCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
cursCmd.Parameters.Add("DEPTCURSOR", OracleType.Cursor).Direction = ParameterDirection.Output;  
  
OracleDataReader reader = cursCmd.ExecuteReader();  
  
Console.WriteLine("\nEmp ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}, {2}", reader.GetOracleNumber(0), reader.GetString(1), reader.GetString(2));  
  
reader.NextResult();  
  
Console.WriteLine("\nDept ID\tName");  
  
while (reader.Read())  
  Console.WriteLine("{0}\t{1}", reader.GetOracleNumber(0), reader.GetString(1));  
// Make sure to always close readers and connections.  
reader.Close();  
oraConn.Close();  
```  
  
 Aşağıdaki örnek, Oracle paketinin sonuçlarıyla bir önceki <xref:System.Data.DataSet> komutu kullanır.  
  
```vb  
Dim ds As DataSet = New DataSet()  
  
Dim adapter As OracleDataAdapter = New OracleDataAdapter(cursCmd)  
adapter.TableMappings.Add("Table", "Employees")  
adapter.TableMappings.Add("Table1", "Departments")  
  
adapter.Fill(ds)  
```  
  
```csharp  
DataSet ds = new DataSet();  
  
OracleDataAdapter adapter = new OracleDataAdapter(cursCmd);  
adapter.TableMappings.Add("Table", "Employees");  
adapter.TableMappings.Add("Table1", "Departments");  
  
adapter.Fill(ds);  
```

> [!NOTE]
> **Bir Taşma Özel Durum'dan**kaçınmak için, değeri bir 'de depolamadan önce Oracle NUMBER türünden <xref:System.Data.DataRow>geçerli bir .NET Framework türüne herhangi bir dönüştürme yi işlemenizi öneririz. **Bir Taşma Özel Durum** oluştu olup olmadığını belirlemek için <xref:System.Data.Common.DataAdapter.FillError> olay kullanabilirsiniz. <xref:System.Data.Common.DataAdapter.FillError> Olay hakkında daha fazla bilgi için [DataAdapter Olaylarını Işleme](handling-dataadapter-events.md)konusuna bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [Veritabanı Şema Bilgilerini Alma](retrieving-database-schema-information.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
