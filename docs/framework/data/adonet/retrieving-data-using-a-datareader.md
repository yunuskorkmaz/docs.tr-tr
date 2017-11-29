---
title: DataReader kullanarak veri alma
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0b66ca2fbcc760598b771b4c02a46acc3c9c1d4e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-data-using-a-datareader"></a>DataReader kullanarak veri alma
Kullanarak verileri alınırken bir **DataReader** örneği oluşturmayı içerir **komutu** nesnesi ve ardından oluşturarak bir **DataReader** çağırarak  **Command.ExecuteReader** satır veri kaynağından veri almak için. Aşağıdaki örnek kullanarak gösterilmektedir bir **DataReader** nerede `reader` geçerli DataReader temsil eder ve `command` geçerli bir komut nesnesi temsil eder.  
  
```  
reader = command.ExecuteReader();  
```  
  
 Kullandığınız **okuma** yöntemi **DataReader** nesnesi bir satır sorgunun sonuçları elde edilir. Ad veya sıralı başvuru için sütunun geçirerek döndürülen satır her bir sütununda erişebilirsiniz **DataReader**. Ancak, en iyi performans için **DataReader** bir dizi kendi yerel veri türlerinde sütun değerlerini erişmenize olanak sağlayan yöntemler sağlar (**GetDateTime**, **GetDouble**, **GetGuid**, **Getınt32**, vb.). Sağlayıcıya özgü veriler için yazılan erişimci yöntemleri listesi **DataReader**, bkz: <xref:System.Data.OleDb.OleDbDataReader> ve <xref:System.Data.SqlClient.SqlDataReader>. Temel alınan veri türü bilinen varsayarak yazılı erişimci yöntemlerini kullanarak sütun değeri alınırken gerekli tür dönüştürme miktarını azaltır.  
  
> [!NOTE]
>  .NET Framework'ün Windows Server 2003 sürümü için ek bir özelliği içerir **DataReader**, **HasRows**, varsa belirlemenize olanak sağlayan **DataReader**buradan okuma önce herhangi bir sonuç döndürdü.  
  
 Aşağıdaki kod örneğinde dolaşır bir **DataReader** nesnesi ve her satırdan iki sütun döndürür.  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 **DataReader** arabellekten çıkarılan bir verimli bir veri kaynağından sonuçları sıralı olarak işlemek yordamsal mantığını sağlayan veri akışı sağlar. **DataReader** verileri bellekte önbelleğe alınmamış çünkü büyük miktarlarda veri alınırken olduğunda iyi bir seçimdir.  
  
## <a name="closing-the-datareader"></a>DataReader kapatma  
 Her zaman çağırmalıdır **Kapat** kullanmayı bitirdikten sonra yöntemi **DataReader** nesnesi.  
  
 Varsa, **komutu** çıkış içeren parametreleri veya dönüş değerlerini, bunların kullanılamayacak kadar **DataReader** kapalı.  
  
 Not Bu süre bir **DataReader** açık **bağlantı** tarafından özel olarak, kullanımda olan **DataReader**. Herhangi bir komut yürütülemiyor **bağlantı**, başka bir oluşturma dahil **DataReader**, özgün kadar **DataReader** kapalı.  
  
> [!NOTE]
>  Çağırmayın **Kapat** veya **Dispose** üzerinde bir **bağlantı**, **DataReader**, veya diğer yönetilen nesne içinde **Finalize**  sınıfınızın yöntemi. Bir Sonlandırıcı, yalnızca sınıfınız doğrudan sahibi yönetilmeyen kaynakları serbest bırakmak. Sınıfınıza yönetilmeyen kaynakları sahip olmadığından, içermeyen bir **Finalize** Sınıf tanımınız yöntemi. Daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a>NextResult kullanarak birden çok sonuç kümesi alınıyor  
 Birden çok sonuç kümesi döndürdüyse **DataReader** sağlar **NextResult** sonuç yinelemek için yöntemi sırayla ayarlar. Aşağıdaki örnekte gösterildiği <xref:System.Data.SqlClient.SqlDataReader> kullanarak iki SELECT deyimleri sonuçlarını işleme <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yöntemi.  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a>DataReader alma şema bilgileri  
 Sırada bir **DataReader** olan kullanılarak geçerli sonuç kümesinde şema bilgilerini alabilir açık **GetSchemaTable** yöntemi. **GetSchemaTable** döndüren bir <xref:System.Data.DataTable> nesne, geçerli sonuç kümesi için şema bilgileri içeren satır ve sütun ile doldurulur. **DataTable** sonuç kümesinin her bir sütun için bir satır içerir. Her sütunun şema tablo satırının eşlendiğini döndürülen sütunun özelliği için sonuç kümesi, burada **ColumnName** özelliğinin değeri sütunun değeri ve özelliğin adı. Aşağıdaki kod örneği için şema bilgileri Yazar **DataReader**.  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a>OLE DB bölümleri ile çalışma  
 Hiyerarşik satır kümeleri veya bölümlerle (OLE DB türü **DBTYPE_HCHAPTER**, ADO türü **adChapter**) kullanılarak alınabilir <xref:System.Data.OleDb.OleDbDataReader>. Olarak bir bölüm içeren bir sorgu döndürüldüğünde bir **DataReader**, bu bölümde, bir sütun olarak döndürülür **DataReader** ve olarak sunulan bir **DataReader** nesnesi.  
  
 ADO.NET **DataSet** üst-alt tablolar arasında ilişkiler kullanarak hiyerarşik satır kümeleri temsil etmek için de kullanılabilir. Daha fazla bilgi için bkz: [veri kümeleri, DataTable ve DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).  
  
 Aşağıdaki kod örneğinde MSDataShape sağlayıcı siparişleri her müşteri için bir bölüm sütununa müşterilerin listesini oluşturmak için kullanır.  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind")  
  
Dim custCMD As OleDbCommand = New OleDbCommand( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
connection.Open()  
  
Dim custReader As OleDbDataReader = custCMD.ExecuteReader()  
Dim orderReader As OleDbDataReader  
  
Do While custReader.Read()  
  Console.WriteLine("Orders for " & custReader.GetString(1))   
  ' custReader.GetString(1) = CompanyName  
  
  orderReader = custReader.GetValue(2)  
  ' custReader.GetValue(2) = Orders chapter as DataReader  
  
  Do While orderReader.Read()  
    Console.WriteLine(vbTab & orderReader.GetInt32(1))  
    ' orderReader.GetInt32(1) = OrderID  
  Loop  
  orderReader.Close()  
Loop  
' Make sure to always close readers and connections.  
custReader.Close()  
End Using  
```  
  
```csharp  
Using (OleDbConnection connection = new OleDbConnection(  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=localhost;Integrated Security=SSPI;Initial Catalog=northwind"));  
{  
OleDbCommand custCMD = new OleDbCommand(  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS CustomerOrders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
connection.Open();  
  
OleDbDataReader custReader = custCMD.ExecuteReader();  
OleDbDataReader orderReader;  
  
while (custReader.Read())  
{  
  Console.WriteLine("Orders for " + custReader.GetString(1));   
  // custReader.GetString(1) = CompanyName  
  
  orderReader = (OleDbDataReader)custReader.GetValue(2);        
  // custReader.GetValue(2) = Orders chapter as DataReader  
  
  while (orderReader.Read())  
    Console.WriteLine("\t" + orderReader.GetInt32(1));          
    // orderReader.GetInt32(1) = OrderID  
  orderReader.Close();  
}  
// Make sure to always close readers and connections.  
custReader.Close();  
}  
```  
  
## <a name="returning-results-with-oracle-ref-cursors"></a>Oracle REF imleçler sonuçlarıyla döndürme  
 Oracle için .NET Framework veri sağlayıcısı sorgu sonucu döndürmek için Oracle REF imleçler kullanımını destekler. Bir Oracle REF İMLEÇ olarak döndürülür bir <xref:System.Data.OracleClient.OracleDataReader>.  
  
 Alabilirsiniz bir **OracleDataReader** kullanarak bir Oracle REF İMLEÇ temsil eden nesnesi <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> yöntemi için ve ayrıca belirtebilirsiniz bir <xref:System.Data.OracleClient.OracleCommand> olarak bir veya daha fazla Oracle REF imleçler döndürür  **SelectCommand** için bir <xref:System.Data.OracleClient.OracleDataAdapter> doldurmak için kullanılan bir <xref:System.Data.DataSet>.  
  
 Bir Oracle veri kaynağından döndürülen REF İMLEÇ erişmek için oluşturma bir **OracleCommand** sorgunuz için ve REF İMLECİ başvuruda bulunan bir output parametresi ekleyin **parametreleri** , koleksiyonu **OracleCommand**. Parametrenin adı Sorgunuzdaki REF İMLEÇ parametresinin adı eşleşmelidir. Parametre türünü ayarlayın **OracleType.Cursor**. **ExecuteReader** yöntemi, **OracleCommand** döndürülecek bir **OracleDataReader** REF İMLECİ için.  
  
 Varsa, **OracleCommand** birden çok REF İMLEÇLER, döndürür birden çok çıktı parametreleri ekleyin. Çağırarak farklı REF imleçler erişebilirsiniz **OracleCommand.ExecuteReader** yöntemi. Çağrı **ExecuteReader** döndüren bir **OracleDataReader** ilk REF İMLECİ başvuruyor. Ardından çağırabilirsiniz **OracleDataReader.NextResult** sonraki REF imleçler erişim yöntemi. Ancak parametrelerinde, **OracleCommand.Parameters** koleksiyonu eşleşme REF İMLECİ çıkış parametresi adıyla **OracleDataReader** bunları eklendiklerisıraylaerişir **Parametreleri** koleksiyonu.  
  
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
  
 Aşağıdaki kod oluşturur bir **OracleCommand** döndüren REF imleçler önceki Oracle paketinden türünde iki parametre ekleyerek **OracleType.Cursor** için **parametreleri** koleksiyonu.  
  
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
  
 Aşağıdaki kod önceki komutunu kullanarak sonuçlarını döndürür **okuma** ve **NextResult** yöntemlerinin **OracleDataReader**. REF İMLEÇ parametreleri sıraya göre döndürülür.  
  
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
  
 Aşağıdaki örnek önceki komutunu doldurmak için kullanan bir **DataSet** Oracle paket sonuçlarını içeren.  
  
> [!NOTE]
>  Önlemek için bir **OverflowException**, ayrıca değer'de depolama önce herhangi bir dönüştürmeye Oracle numarası türünden geçerli bir .NET Framework türüne işlemek öneririz bir **DataRow**. Kullanabileceğiniz **FillError** belirlemek için olay bir **OverflowException** oluştu. Daha fazla bilgi için **FillError** olayı bkz [olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataReader ile çalışma](http://msdn.microsoft.com/en-us/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [DataAdapters ve DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [Komutları ve parametreleri](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Veritabanı şema bilgileri alınıyor](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
