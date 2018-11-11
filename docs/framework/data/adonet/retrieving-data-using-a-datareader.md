---
title: DataReader kullanarak veri alma
ms.date: 10/259/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: d3c59b667c05be083e44de8cc3e7e44d50fefc71
ms.sourcegitcommit: b5cd9d5d3b75a5537fc9ad8a3f085f0bb1845ee0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2018
ms.locfileid: "43516797"
---
# <a name="retrieve-data-using-a-datareader"></a>DataReader kullanarak veri alma
Kullanarak verileri almak için bir **DataReader**, bir örneğini oluşturmak **komut** nesne ve oluşturup bir **DataReader** çağırarak **Command.ExecuteReader**  satırları bir veri kaynağından almak için. **DataReader** arabellekten çıkarılan bir yordam mantığı verimli bir şekilde bir veri kaynağından sonuçları sıralı olarak işlediğinden sağlayan veri akışını sağlar. **DataReader** verileri bellek içinde önbelleğe alınmamış çünkü büyük miktarlarda veri alınırken iyi bir seçimdir.

Kullanarak aşağıdaki örnekte gösterildiği bir **DataReader**burada `reader` geçerli DataReader temsil eder ve `command` geçerli olan komut nesnesini temsil eder.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Kullanım **DataReader.Read** satır öğesinden gelen soru sonuçları elde etmek için yöntemi. Döndürülen satırın her sütun adı veya sıra numarası sütununun geçirerek erişebileceğiniz **DataReader**. Ancak, en iyi performans için **DataReader** bir dizi kendi yerel veri türlerinde sütun değerleri erişmenize olanak tanıyan yöntemler sağlar (**GetDateTime**, **GetDouble**, **GetGuid**, **Getınt32**, vb.). Sağlayıcıya özgü veriler için belirlenmiş erişimci metotlarını bir listesi için **DataReaders**, bkz: <xref:System.Data.OleDb.OleDbDataReader> ve <xref:System.Data.SqlClient.SqlDataReader>. Temel alınan verileri bildiğiniz durumlarda yazılan erişimci yöntemlerini kullanarak türü sütun değeri alınırken gerekli tür dönüştürme miktarını azaltır.  
  
 Aşağıdaki örnek gezinir bir **DataReader** nesnesi ve her satırdan iki sütun döndürür.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>DataReader kapatma  
 Her zaman çağrı **Kapat** kullanarak tamamladığınızda yöntemi **DataReader** nesne.  
  
 Varsa, **komut** çıktısını içeren parametreleri veya dönüş değerleri, bu değerleri kullanılamaz kadar **DataReader** kapatılır.  
  
 Ancak bir **DataReader** açıkken **bağlantı** , tarafından özel olarak **DataReader**. Herhangi bir komut yürütülemiyor **bağlantı**, başka bir oluşturma gibi **DataReader**, özgün kadar **DataReader** kapatılır.  
  
> [!NOTE]
>  Çağırmayın **Kapat** veya **Dispose** üzerinde bir **bağlantı**, **DataReader**, ya da diğer yönetilen nesnelere **Finalize**  sınıfınızın yöntemi. İçindeki bir sonlandırıcı yalnızca sınıfınıza doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın. Sınıfınızın herhangi bir yönetilmeyen kaynağa sahip değilse içermeyen bir **Finalize** sınıf tanımına yöntemi. Daha fazla bilgi için [çöp toplama](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>Birden çok sonuç alınırken NextResult kullanarak ayarlar  
 Varsa **DataReader** çağrısı birden çok sonuç kümesi döndürür **NextResult** sonucu yineleme yapmak için gereken yöntemini ayarlar sıralı olarak. Aşağıdaki örnekte gösterildiği <xref:System.Data.SqlClient.SqlDataReader> kullanarak iki SELECT deyimleri sonuçlarını işleme <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yöntemi.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>DataReader gelen şema bilgilerini alma  
 Ancak bir **DataReader** olan şema bilgileri kullanılarak ayarlanan geçerli sonucu ile ilgili alabilirsiniz açık **GetSchemaTable** yöntemi. **GetSchemaTable** döndürür bir <xref:System.Data.DataTable> nesne satır ve geçerli sonuç kümesi için şema bilgileri içeren sütunlar ile doldurulur. **DataTable** sonuç kümesinin her bir sütun için bir satır içerir. Şema tablonun her sütunu eşleyen bir özelliğine döndürülen sütunlar sonuç satırlarını ayarlama, burada **ColumnName** özelliği adıdır ve özelliğinin değeri sütun değeridir. Aşağıdaki örnek, şema bilgileri için Yazar **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>OLE DB bölümlerle çalışma  
 Hiyerarşik satır kümeleri ya da bölümlerini (OLE DB türü **DBTYPE_HCHAPTER**, ADO türü **adChapter**), kullanılarak alınabilir <xref:System.Data.OleDb.OleDbDataReader>. Olarak bölüm içeren bir sorgu döndürüldüğünde bir **DataReader**, bu bölümde, bir sütun olarak döndürülen **DataReader** ve olarak kullanıma sunulduğunu bir **DataReader** nesne.  
  
 ADO.NET **veri kümesi** hiyerarşik satır kümeleri tablolar arasındaki üst-alt ilişkileri kullanarak temsil etmek için de kullanılabilir. Daha fazla bilgi için [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Aşağıdaki kod örneği MSDataShape sağlayıcı bir bölüm sütunu her müşteriye ait siparişlerin müşterilerin listesini oluşturmak için kullanır.  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Oracle REF CURSOR sonuçlar döndürüyor  
 Oracle için .NET Framework veri sağlayıcısı, bir sorgu sonuç döndürmek için Oracle REF CURSOR kullanımını destekler. Bir Oracle REF CURSOR olarak döndürülen bir <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Alabileceğiniz bir <xref:System.Data.OracleClient.OracleDataReader> kullanarak bir Oracle REF CURSOR temsil eden bir nesne <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> yöntemi. Ayrıca belirtebileceğiniz bir <xref:System.Data.OracleClient.OracleCommand> olarak bir veya daha fazla Oracle REF CURSOR döndüren **SelectCommand** için bir <xref:System.Data.OracleClient.OracleDataAdapter> doldurmak için kullanılan bir <xref:System.Data.DataSet>.  
  
 Bir Oracle veri kaynağından döndürülen bir REF CURSOR erişmek için oluşturun bir <xref:System.Data.OracleClient.OracleCommand> sorgunuz için ve REF CURSOR için başvuran çıkış parametresi ekleyin <xref:System.Data.OracleClient.OracleCommand.Parameters> koleksiyonunu, <xref:System.Data.OracleClient.OracleCommand>. Parametrenin adını sorgunuzda REF CURSOR parametrenin adı eşleşmelidir. Parametre türünü ayarlamak <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>. <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> Yöntemi, <xref:System.Data.OracleClient.OracleCommand> döndürür bir <xref:System.Data.OracleClient.OracleDataReader> REF CURSOR için.  
  
 Varsa, <xref:System.Data.OracleClient.OracleCommand> birden çok REF CURSOR döndürür birden çok çıktı parametreleri ekleyin. Farklı REF CURSOR çağırarak erişebileceğiniz <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> yöntemi. Çağrı <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> döndürür bir <xref:System.Data.OracleClient.OracleDataReader> ilk REF CURSOR başvuruyor. Ardından çağırabilirsiniz <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> sonraki REF CURSOR erişmek için yöntemi. Ancak parametrelerinde, <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> koleksiyon eşleşme REF CURSOR parametreleri adıyla çıkış <xref:System.Data.OracleClient.OracleDataReader> bunları içinde eklendikleri için sırada erişir <xref:System.Data.OracleClient.OracleCommand.Parameters> koleksiyonu.  
  
 Örneğin, aşağıdaki Oracle paket ve paket gövdesi göz önünde bulundurun.  
  
```  
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
  
 Aşağıdaki kod oluşturur bir <xref:System.Data.OracleClient.OracleCommand> döndüren REF CURSOR önceki Oracle paketi türünde iki parametre ekleyerek <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> için <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> koleksiyonu.  
  
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
  
 Aşağıdaki kod, önceki komutla sonuçlarını döndürür <xref:System.Data.OracleClient.OracleDataReader.Read> ve <xref:System.Data.OracleClient.OracleDataReader.NextResult> yöntemlerinin <xref:System.Data.OracleClient.OracleDataReader>. REF CURSOR parametreleri sırayla döndürülür.  
  
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
  
 Aşağıdaki örnek önceki komutun doldurmak için kullanır. bir <xref:System.Data.DataSet> Oracle paket sonuçlarla.  
  
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
>  Önlemek için bir **OverflowException**, değer depolanmadan önce her türünden dönüştürme Oracle numarası geçerli bir .NET Framework türü de ele öneririz bir <xref:System.Data.DataRow>. Kullanabileceğiniz <xref:System.Data.Common.DataAdapter.FillError> belirlemek için olay bir **OverflowException** oluştu. Daha fazla bilgi için <xref:System.Data.Common.DataAdapter.FillError> olay bkz [DataAdapter olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [DataReader ile çalışma](https://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Veritabanı Şema Bilgilerini Alma](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
