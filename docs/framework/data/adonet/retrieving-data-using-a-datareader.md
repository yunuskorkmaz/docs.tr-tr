---
title: DataReader Kullanarak Veri Alma
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: f3add49d48a569664d4cbb6b5c26d5f3379b6f18
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794404"
---
# <a name="retrieve-data-using-a-datareader"></a>DataReader kullanarak veri alma
**DataReader**kullanarak verileri almak Için, **komut** nesnesinin bir örneğini oluşturun ve sonra bir veri kaynağından satırları almak için **Command. ExecuteReader** çağırarak bir **DataReader** oluşturun. **DataReader** , yordamsal mantığın bir veri kaynağından oluşan sonuçları sırayla verimli bir şekilde işlemesini sağlayan, arabelleğe alınmamış bir veri akışı sağlar. Veriler bellekte önbelleğe alınmadığı için büyük miktarlarda veri alırken **DataReader** iyi bir seçimdir.

Aşağıdaki örnekte, `reader` geçerli bir DataReader temsil eden ve `command` geçerli bir komut nesnesini temsil eden bir **DataReader**kullanımı gösterilmektedir.  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

Sorgu sonuçlarından bir satır almak için **DataReader. Read** metodunu kullanın. Döndürülen satırın her sütununa, sütunun ad veya sıra numarasını **DataReader**' a geçirerek erişebilirsiniz. Bununla birlikte, en iyi performans için, **DataReader** kendi yerel veri türlerindeki (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**vb.) sütun değerlerine erişmenize izin veren bir dizi yöntem sunar. Veri sağlayıcısına özgü **DataReaders**türü belirlenmiş erişimci yöntemlerinin bir listesi için bkz <xref:System.Data.OleDb.OleDbDataReader> . ve. <xref:System.Data.SqlClient.SqlDataReader> Temel alınan veri türünü bildiğiniz durumlarda türü belirlenmiş erişimci yöntemlerinin kullanılması, sütun değerini alırken gereken tür dönüştürme miktarını azaltır.  
  
 Aşağıdaki örnek, bir **DataReader** nesnesi üzerinden yinelenir ve her satırdan iki sütun döndürür.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a>DataReader kapatılıyor  
 **DataReader** nesnesini kullanmayı bitirdiğinizde her zaman **Close** yöntemini çağırın.  
  
 **Komutunuz** çıkış parametrelerini veya dönüş değerlerini Içeriyorsa, **DataReader** kapatılana kadar bu değerler kullanılamaz.  
  
 Bir **DataReader** açık olsa da **bağlantı** , bu **DataReader**tarafından özel olarak kullanılıyor. Özgün **DataReader** kapatılana kadar, başka bir **DataReader**oluşturma da dahil olmak üzere **bağlantı**için herhangi bir komut yürütemezsiniz.  
  
> [!NOTE]
> Bir **bağlantıyı**, bir **DataReader**'ı veya sınıfınızın **Finalize** yönteminde herhangi bir yönetilen nesneyi **kapatma** veya **atma** işlemini çağırmayın. Sonlandırıcıda yalnızca, sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın. Sınıfınız hiçbir yönetilmeyen kaynağa sahip değilse, sınıf tanımınıza bir **Finalize** yöntemi eklemeyin. Daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>NextResult kullanarak birden çok sonuç kümesi alma  
 **DataReader** birden çok sonuç kümesi döndürürse, sonuç kümelerini sırayla yinelemek Için **NextResult** yöntemini çağırın. Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yöntemi kullanılarak <xref:System.Data.SqlClient.SqlDataReader> iki SELECT deyimi sonuçlarının işlenme işlemini gösterir.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>DataReader 'tan şema bilgileri alma  
 Bir **DataReader** açıkken, **GetSchemaTable** yöntemini kullanarak geçerli sonuç kümesiyle ilgili şema bilgilerini alabilirsiniz. **GetSchemaTable** , geçerli <xref:System.Data.DataTable> sonuç kümesi için şema bilgilerini içeren satırlar ve sütunlar ile doldurulmuş bir nesne döndürür. **DataTable** , sonuç kümesinin her bir sütunu için bir satır içerir. Şema tablosunun her sütunu, sonuç kümesinin satırlarında döndürülen sütunların bir özelliğine eşlenir; burada **sütunadı** , özelliğin adıdır ve sütununun değeri özelliğin değeridir. Aşağıdaki örnek, **DataReader**için şema bilgilerini yazar.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>OLE DB bölümler ile çalışma  
 Hiyerarşik satır kümeleri veya bölümler (OLE DB türü **dbtype_hchapter**, ADO türü **adbölüm**) kullanılarak <xref:System.Data.OleDb.OleDbDataReader>alınabilir. Bölüm içeren bir sorgu **DataReader**olarak döndürüldüğünde, bölüm bu **DataReader** 'da bir sütun olarak döndürülür ve bir **DataReader** nesnesi olarak sunulur.  
  
 ADO.NET **veri kümesi** , tablolar arasında üst-alt ilişkilerini kullanarak hiyerarşik satır kümelerini temsil etmek için de kullanılabilir. Daha fazla bilgi için bkz. [veri kümeleri, DataTable ve DataView](./dataset-datatable-dataview/index.md).  
  
 Aşağıdaki kod örneği, bir müşteri listesindeki her müşteri için siparişlerin bir bölüm sütununu oluşturmak üzere MSDataShape sağlayıcısını kullanır.  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Oracle REF IMLEÇLER ile sonuçları döndürme  
 Oracle için .NET Framework Veri Sağlayıcısı, Oracle REF IMLEÇLER 'in bir sorgu sonucu döndürecek şekilde kullanılmasını destekler. Oracle REF CURSOR bir <xref:System.Data.OracleClient.OracleDataReader>olarak döndürülür.  
  
 Yöntemini kullanarak bir Oracle <xref:System.Data.OracleClient.OracleDataReader> başvuru imlecini temsil eden bir nesnesi alabilirsiniz. <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> Ayrıca, bir veya daha <xref:System.Data.OracleClient.OracleCommand> fazla Oracle başvuru imleçlerini bir <xref:System.Data.DataSet>tane doldurdukları için <xref:System.Data.OracleClient.OracleDataAdapter> SelectCommand olarak döndüren bir de belirtebilirsiniz.  
  
 Oracle veri kaynağından döndürülen bir başvuru imlecine erişmek için, sorgunuz için bir <xref:System.Data.OracleClient.OracleCommand> oluşturun ve başvuru imlecine <xref:System.Data.OracleClient.OracleCommand.Parameters> <xref:System.Data.OracleClient.OracleCommand>başvuran bir çıkış parametresi ekleyin. Parametrenin adı Sorgunuzdaki REF CURSOR parametresinin adıyla eşleşmelidir. Parametresinin türünü olarak <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>ayarlayın. ' In yöntemi başvuru imleci <xref:System.Data.OracleClient.OracleDataReader> için döndürür.<xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType>  
  
 Birden çok başvuru imleci döndürürse,birdençokçıkışparametresiekleyin.<xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> Yöntemini çağırarak farklı başvuru imleçlerinin erişimine erişebilirsiniz. Çağrısı <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> , ilk başvuru imlecine <xref:System.Data.OracleClient.OracleDataReader> başvuran döndürür. Ardından, <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> sonraki başvuru imleçlerini erişmek için yöntemini çağırabilirsiniz. Koleksiyonunuzdaki <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> parametreler, başvuru imleci çıkış parametreleriyle ada göre eşleşir <xref:System.Data.OracleClient.OracleDataReader> , ancak onlara <xref:System.Data.OracleClient.OracleCommand.Parameters> koleksiyona eklendikleri sırayla erişir.  
  
 Örneğin, aşağıdaki Oracle paketini ve paket gövdesini göz önünde bulundurun.  
  
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
  
 Aşağıdaki kod, <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> koleksiyona iki tür <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> parametre ekleyerek önceki Oracle paketinden başvuru imleçleri döndüren bir oluşturur.  
  
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
  
 Aşağıdaki kod, <xref:System.Data.OracleClient.OracleDataReader.Read> ve <xref:System.Data.OracleClient.OracleDataReader.NextResult> yöntemlerini <xref:System.Data.OracleClient.OracleDataReader>kullanarak önceki komutun sonucunu döndürür. REF CURSOR parametreleri sırayla döndürülür.  
  
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
  
 Aşağıdaki örnek, Oracle paketinin sonuçlarıyla <xref:System.Data.DataSet> birlikte doldurmak için Previous komutunu kullanır.  
  
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
> Bir **OverflowException**'ı önlemek için, değeri bir <xref:System.Data.DataRow>içinde depolamadan önce Oracle Number türünden geçerli bir .NET Framework türüne dönüştürme işleminin de işlemesini öneririz. Bir OverflowException 'ın oluşup <xref:System.Data.Common.DataAdapter.FillError> oluşmadığını öğrenmek için olayını kullanabilirsiniz. <xref:System.Data.Common.DataAdapter.FillError> Olay hakkında daha fazla bilgi için bkz. [DataAdapter olaylarını işleme](handling-dataadapter-events.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [Komutlar ve Parametreler](commands-and-parameters.md)
- [Veritabanı Şema Bilgilerini Alma](retrieving-database-schema-information.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
