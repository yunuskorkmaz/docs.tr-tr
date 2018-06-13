---
title: DataReader kullanarak veri alma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 0c78db5ce7a6a988e40718daca1d828096a734d2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33353266"
---
# <a name="retrieving-data-using-a-datareader"></a><span data-ttu-id="8e598-102">DataReader kullanarak veri alma</span><span class="sxs-lookup"><span data-stu-id="8e598-102">Retrieving Data Using a DataReader</span></span>
<span data-ttu-id="8e598-103">Kullanarak verileri alınırken bir **DataReader** örneği oluşturmayı içerir **komutu** nesnesi ve ardından oluşturarak bir **DataReader** çağırarak  **Command.ExecuteReader** satır veri kaynağından veri almak için.</span><span class="sxs-lookup"><span data-stu-id="8e598-103">Retrieving data using a **DataReader** involves creating an instance of the **Command** object and then creating a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="8e598-104">Aşağıdaki örnek kullanarak gösterilmektedir bir **DataReader** nerede `reader` geçerli DataReader temsil eder ve `command` geçerli bir komut nesnesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8e598-104">The following example illustrates using a **DataReader** where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  
  
```  
reader = command.ExecuteReader();  
```  
  
 <span data-ttu-id="8e598-105">Kullandığınız **okuma** yöntemi **DataReader** nesnesi bir satır sorgunun sonuçları elde edilir.</span><span class="sxs-lookup"><span data-stu-id="8e598-105">You use the **Read** method of the **DataReader** object to obtain a row from the results of the query.</span></span> <span data-ttu-id="8e598-106">Ad veya sıralı başvuru için sütunun geçirerek döndürülen satır her bir sütununda erişebilirsiniz **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="8e598-106">You can access each column of the returned row by passing the name or ordinal reference of the column to the **DataReader**.</span></span> <span data-ttu-id="8e598-107">Ancak, en iyi performans için **DataReader** bir dizi kendi yerel veri türlerinde sütun değerlerini erişmenize olanak sağlayan yöntemler sağlar (**GetDateTime**, **GetDouble**, **GetGuid**, **Getınt32**, vb.).</span><span class="sxs-lookup"><span data-stu-id="8e598-107">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="8e598-108">Sağlayıcıya özgü veriler için yazılan erişimci yöntemleri listesi **DataReader**, bkz: <xref:System.Data.OleDb.OleDbDataReader> ve <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8e598-108">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="8e598-109">Temel alınan veri türü bilinen varsayarak yazılı erişimci yöntemlerini kullanarak sütun değeri alınırken gerekli tür dönüştürme miktarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="8e598-109">Using the typed accessor methods, assuming the underlying data type is known, reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e598-110">.NET Framework'ün Windows Server 2003 sürümü için ek bir özelliği içerir **DataReader**, **HasRows**, varsa belirlemenize olanak sağlayan **DataReader**buradan okuma önce herhangi bir sonuç döndürdü.</span><span class="sxs-lookup"><span data-stu-id="8e598-110">The Windows Server 2003 release of the .NET Framework includes an additional property for the **DataReader**, **HasRows**, which enables you to determine if the **DataReader** has returned any results before reading from it.</span></span>  
  
 <span data-ttu-id="8e598-111">Aşağıdaki kod örneğinde dolaşır bir **DataReader** nesnesi ve her satırdan iki sütun döndürür.</span><span class="sxs-lookup"><span data-stu-id="8e598-111">The following code example iterates through a **DataReader** object, and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
 <span data-ttu-id="8e598-112">**DataReader** arabellekten çıkarılan bir verimli bir veri kaynağından sonuçları sıralı olarak işlemek yordamsal mantığını sağlayan veri akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="8e598-112">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="8e598-113">**DataReader** verileri bellekte önbelleğe alınmamış çünkü büyük miktarlarda veri alınırken olduğunda iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="8e598-113">The **DataReader** is a good choice when retrieving large amounts of data because the data is not cached in memory.</span></span>  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="8e598-114">DataReader kapatma</span><span class="sxs-lookup"><span data-stu-id="8e598-114">Closing the DataReader</span></span>  
 <span data-ttu-id="8e598-115">Her zaman çağırmalıdır **Kapat** kullanmayı bitirdikten sonra yöntemi **DataReader** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8e598-115">You should always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="8e598-116">Varsa, **komutu** çıkış içeren parametreleri veya dönüş değerlerini, bunların kullanılamayacak kadar **DataReader** kapalı.</span><span class="sxs-lookup"><span data-stu-id="8e598-116">If your **Command** contains output parameters or return values, they will not be available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="8e598-117">Not Bu süre bir **DataReader** açık **bağlantı** tarafından özel olarak, kullanımda olan **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="8e598-117">Note that while a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="8e598-118">Herhangi bir komut yürütülemiyor **bağlantı**, başka bir oluşturma dahil **DataReader**, özgün kadar **DataReader** kapalı.</span><span class="sxs-lookup"><span data-stu-id="8e598-118">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e598-119">Çağırmayın **Kapat** veya **Dispose** üzerinde bir **bağlantı**, **DataReader**, veya diğer yönetilen nesne içinde **Finalize**  sınıfınızın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e598-119">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="8e598-120">Bir Sonlandırıcı, yalnızca sınıfınız doğrudan sahibi yönetilmeyen kaynakları serbest bırakmak.</span><span class="sxs-lookup"><span data-stu-id="8e598-120">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="8e598-121">Sınıfınıza yönetilmeyen kaynakları sahip olmadığından, içermeyen bir **Finalize** Sınıf tanımınız yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e598-121">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="8e598-122">Daha fazla bilgi için bkz: [çöp toplama](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e598-122">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="8e598-123">NextResult kullanarak birden çok sonuç kümesi alınıyor</span><span class="sxs-lookup"><span data-stu-id="8e598-123">Retrieving Multiple Result Sets using NextResult</span></span>  
 <span data-ttu-id="8e598-124">Birden çok sonuç kümesi döndürdüyse **DataReader** sağlar **NextResult** sonuç yinelemek için yöntemi sırayla ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8e598-124">If multiple result sets are returned, the **DataReader** provides the **NextResult** method to iterate through the result sets in order.</span></span> <span data-ttu-id="8e598-125">Aşağıdaki örnekte gösterildiği <xref:System.Data.SqlClient.SqlDataReader> kullanarak iki SELECT deyimleri sonuçlarını işleme <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e598-125">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="8e598-126">DataReader alma şema bilgileri</span><span class="sxs-lookup"><span data-stu-id="8e598-126">Getting Schema Information from the DataReader</span></span>  
 <span data-ttu-id="8e598-127">Sırada bir **DataReader** olan kullanılarak geçerli sonuç kümesinde şema bilgilerini alabilir açık **GetSchemaTable** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e598-127">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="8e598-128">**GetSchemaTable** döndüren bir <xref:System.Data.DataTable> nesne, geçerli sonuç kümesi için şema bilgileri içeren satır ve sütun ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="8e598-128">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="8e598-129">**DataTable** sonuç kümesinin her bir sütun için bir satır içerir.</span><span class="sxs-lookup"><span data-stu-id="8e598-129">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="8e598-130">Her sütunun şema tablo satırının eşlendiğini döndürülen sütunun özelliği için sonuç kümesi, burada **ColumnName** özelliğinin değeri sütunun değeri ve özelliğin adı.</span><span class="sxs-lookup"><span data-stu-id="8e598-130">Each column of the schema table row maps to a property of the column returned in the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="8e598-131">Aşağıdaki kod örneği için şema bilgileri Yazar **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="8e598-131">The following code example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="8e598-132">OLE DB bölümleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="8e598-132">Working with OLE DB Chapters</span></span>  
 <span data-ttu-id="8e598-133">Hiyerarşik satır kümeleri veya bölümlerle (OLE DB türü **DBTYPE_HCHAPTER**, ADO türü **adChapter**) kullanılarak alınabilir <xref:System.Data.OleDb.OleDbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8e598-133">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**) can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="8e598-134">Olarak bir bölüm içeren bir sorgu döndürüldüğünde bir **DataReader**, bu bölümde, bir sütun olarak döndürülür **DataReader** ve olarak sunulan bir **DataReader** nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8e598-134">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="8e598-135">ADO.NET **DataSet** üst-alt tablolar arasında ilişkiler kullanarak hiyerarşik satır kümeleri temsil etmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8e598-135">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets using parent-child relationships between tables.</span></span> <span data-ttu-id="8e598-136">Daha fazla bilgi için bkz: [veri kümeleri, DataTable ve DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e598-136">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="8e598-137">Aşağıdaki kod örneğinde MSDataShape sağlayıcı siparişleri her müşteri için bir bölüm sütununa müşterilerin listesini oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="8e598-137">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="8e598-138">Oracle REF imleçler sonuçlarıyla döndürme</span><span class="sxs-lookup"><span data-stu-id="8e598-138">Returning Results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="8e598-139">Oracle için .NET Framework veri sağlayıcısı sorgu sonucu döndürmek için Oracle REF imleçler kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="8e598-139">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="8e598-140">Bir Oracle REF İMLEÇ olarak döndürülür bir <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="8e598-140">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="8e598-141">Alabilirsiniz bir **OracleDataReader** kullanarak bir Oracle REF İMLEÇ temsil eden nesnesi <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> yöntemi için ve ayrıca belirtebilirsiniz bir <xref:System.Data.OracleClient.OracleCommand> olarak bir veya daha fazla Oracle REF imleçler döndürür  **SelectCommand** için bir <xref:System.Data.OracleClient.OracleDataAdapter> doldurmak için kullanılan bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="8e598-141">You can retrieve an **OracleDataReader** object, that represents an Oracle REF CURSOR using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method, and you can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="8e598-142">Bir Oracle veri kaynağından döndürülen REF İMLEÇ erişmek için oluşturma bir **OracleCommand** sorgunuz için ve REF İMLECİ başvuruda bulunan bir output parametresi ekleyin **parametreleri** , koleksiyonu **OracleCommand**.</span><span class="sxs-lookup"><span data-stu-id="8e598-142">To access a REF CURSOR returned from an Oracle data source, create an **OracleCommand** for your query and add an output parameter that references the REF CURSOR to the **Parameters** collection of your **OracleCommand**.</span></span> <span data-ttu-id="8e598-143">Parametrenin adı Sorgunuzdaki REF İMLEÇ parametresinin adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="8e598-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="8e598-144">Parametre türünü ayarlayın **OracleType.Cursor**.</span><span class="sxs-lookup"><span data-stu-id="8e598-144">Set the type of the parameter to **OracleType.Cursor**.</span></span> <span data-ttu-id="8e598-145">**ExecuteReader** yöntemi, **OracleCommand** döndürülecek bir **OracleDataReader** REF İMLECİ için.</span><span class="sxs-lookup"><span data-stu-id="8e598-145">The **ExecuteReader** method of your **OracleCommand** will return an **OracleDataReader** for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="8e598-146">Varsa, **OracleCommand** birden çok REF İMLEÇLER, döndürür birden çok çıktı parametreleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8e598-146">If your **OracleCommand** returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="8e598-147">Çağırarak farklı REF imleçler erişebilirsiniz **OracleCommand.ExecuteReader** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e598-147">You can access the different REF CURSORs by calling the **OracleCommand.ExecuteReader** method.</span></span> <span data-ttu-id="8e598-148">Çağrı **ExecuteReader** döndüren bir **OracleDataReader** ilk REF İMLECİ başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="8e598-148">The call to **ExecuteReader** returns an **OracleDataReader** referencing the first REF CURSOR.</span></span> <span data-ttu-id="8e598-149">Ardından çağırabilirsiniz **OracleDataReader.NextResult** sonraki REF imleçler erişim yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8e598-149">You can then call the **OracleDataReader.NextResult** method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="8e598-150">Ancak parametrelerinde, **OracleCommand.Parameters** koleksiyonu eşleşme REF İMLECİ çıkış parametresi adıyla **OracleDataReader** bunları eklendiklerisıraylaerişir **Parametreleri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8e598-150">Although the parameters in your **OracleCommand.Parameters** collection match the REF CURSOR output parameters by name, the **OracleDataReader** accesses them in the order that they were added to the **Parameters** collection.</span></span>  
  
 <span data-ttu-id="8e598-151">Örneğin, aşağıdaki Oracle paket ve paket gövdesi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="8e598-151">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="8e598-152">Aşağıdaki kod oluşturur bir **OracleCommand** döndüren REF imleçler önceki Oracle paketinden türünde iki parametre ekleyerek **OracleType.Cursor** için **parametreleri** koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="8e598-152">The following code creates an **OracleCommand** that returns the REF CURSORs from the previous Oracle package by adding two parameters of type **OracleType.Cursor** to the **Parameters** collection.</span></span>  
  
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
  
 <span data-ttu-id="8e598-153">Aşağıdaki kod önceki komutunu kullanarak sonuçlarını döndürür **okuma** ve **NextResult** yöntemlerinin **OracleDataReader**.</span><span class="sxs-lookup"><span data-stu-id="8e598-153">The following code returns the results of the previous command using the **Read** and **NextResult** methods of the **OracleDataReader**.</span></span> <span data-ttu-id="8e598-154">REF İMLEÇ parametreleri sıraya göre döndürülür.</span><span class="sxs-lookup"><span data-stu-id="8e598-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="8e598-155">Aşağıdaki örnek önceki komutunu doldurmak için kullanan bir **DataSet** Oracle paket sonuçlarını içeren.</span><span class="sxs-lookup"><span data-stu-id="8e598-155">The following example uses the previous command to populate a **DataSet** with the results of the Oracle package.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8e598-156">Önlemek için bir **OverflowException**, ayrıca değer'de depolama önce herhangi bir dönüştürmeye Oracle numarası türünden geçerli bir .NET Framework türüne işlemek öneririz bir **DataRow**.</span><span class="sxs-lookup"><span data-stu-id="8e598-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a **DataRow**.</span></span> <span data-ttu-id="8e598-157">Kullanabileceğiniz **FillError** belirlemek için olay bir **OverflowException** oluştu.</span><span class="sxs-lookup"><span data-stu-id="8e598-157">You can use the **FillError** event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="8e598-158">Daha fazla bilgi için **FillError** olayı bkz [olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="8e598-158">For more information on the **FillError** event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8e598-159">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8e598-159">See Also</span></span>  
 [<span data-ttu-id="8e598-160">DataReader ile çalışma</span><span class="sxs-lookup"><span data-stu-id="8e598-160">Working with DataReaders</span></span>](http://msdn.microsoft.com/library/126a966a-d08d-4d22-a19f-f432908b2b54)  
 [<span data-ttu-id="8e598-161">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="8e598-161">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="8e598-162">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="8e598-162">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="8e598-163">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="8e598-163">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 [<span data-ttu-id="8e598-164">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="8e598-164">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
