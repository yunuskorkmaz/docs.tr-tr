---
title: DataReader Kullanarak Veri Alma
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 8063f239123ec1a2f2650adf9d76f7ceaaa50673
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61664267"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="687d0-102">DataReader kullanarak veri alma</span><span class="sxs-lookup"><span data-stu-id="687d0-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="687d0-103">Kullanarak verileri almak için bir **DataReader**, bir örneğini oluşturmak **komut** nesne ve oluşturup bir **DataReader** çağırarak **Command.ExecuteReader**  satırları bir veri kaynağından almak için.</span><span class="sxs-lookup"><span data-stu-id="687d0-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="687d0-104">**DataReader** arabellekten çıkarılan bir yordam mantığı verimli bir şekilde bir veri kaynağından sonuçları sıralı olarak işlediğinden sağlayan veri akışını sağlar.</span><span class="sxs-lookup"><span data-stu-id="687d0-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="687d0-105">**DataReader** verileri bellek içinde önbelleğe alınmamış çünkü büyük miktarlarda veri alınırken iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="687d0-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="687d0-106">Kullanarak aşağıdaki örnekte gösterildiği bir **DataReader**burada `reader` geçerli DataReader temsil eder ve `command` geçerli olan komut nesnesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="687d0-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="687d0-107">Kullanım **DataReader.Read** satır öğesinden gelen soru sonuçları elde etmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="687d0-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="687d0-108">Döndürülen satırın her sütun adı veya sıra numarası sütununun geçirerek erişebileceğiniz **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="687d0-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="687d0-109">Ancak, en iyi performans için **DataReader** bir dizi kendi yerel veri türlerinde sütun değerleri erişmenize olanak tanıyan yöntemler sağlar (**GetDateTime**, **GetDouble**, **GetGuid**, **Getınt32**, vb.).</span><span class="sxs-lookup"><span data-stu-id="687d0-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="687d0-110">Sağlayıcıya özgü veriler için belirlenmiş erişimci metotlarını bir listesi için **DataReaders**, bkz: <xref:System.Data.OleDb.OleDbDataReader> ve <xref:System.Data.SqlClient.SqlDataReader>.</span><span class="sxs-lookup"><span data-stu-id="687d0-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="687d0-111">Temel alınan verileri bildiğiniz durumlarda yazılan erişimci yöntemlerini kullanarak türü sütun değeri alınırken gerekli tür dönüştürme miktarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="687d0-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="687d0-112">Aşağıdaki örnek gezinir bir **DataReader** nesnesi ve her satırdan iki sütun döndürür.</span><span class="sxs-lookup"><span data-stu-id="687d0-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="687d0-113">DataReader kapatma</span><span class="sxs-lookup"><span data-stu-id="687d0-113">Closing the DataReader</span></span>  
 <span data-ttu-id="687d0-114">Her zaman çağrı **Kapat** kullanarak tamamladığınızda yöntemi **DataReader** nesne.</span><span class="sxs-lookup"><span data-stu-id="687d0-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="687d0-115">Varsa, **komut** çıktısını içeren parametreleri veya dönüş değerleri, bu değerleri kullanılamaz kadar **DataReader** kapatılır.</span><span class="sxs-lookup"><span data-stu-id="687d0-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="687d0-116">Ancak bir **DataReader** açıkken **bağlantı** , tarafından özel olarak **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="687d0-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="687d0-117">Herhangi bir komut yürütülemiyor **bağlantı**, başka bir oluşturma gibi **DataReader**, özgün kadar **DataReader** kapatılır.</span><span class="sxs-lookup"><span data-stu-id="687d0-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="687d0-118">Çağırmayın **Kapat** veya **Dispose** üzerinde bir **bağlantı**, **DataReader**, ya da diğer yönetilen nesnelere **Finalize**  sınıfınızın yöntemi.</span><span class="sxs-lookup"><span data-stu-id="687d0-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="687d0-119">İçindeki bir sonlandırıcı yalnızca sınıfınıza doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın.</span><span class="sxs-lookup"><span data-stu-id="687d0-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="687d0-120">Sınıfınızın herhangi bir yönetilmeyen kaynağa sahip değilse içermeyen bir **Finalize** sınıf tanımına yöntemi.</span><span class="sxs-lookup"><span data-stu-id="687d0-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="687d0-121">Daha fazla bilgi için [çöp toplama](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="687d0-121">For more information, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="687d0-122">Birden çok sonuç alınırken NextResult kullanarak ayarlar</span><span class="sxs-lookup"><span data-stu-id="687d0-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="687d0-123">Varsa **DataReader** çağrısı birden çok sonuç kümesi döndürür **NextResult** sonucu yineleme yapmak için gereken yöntemini ayarlar sıralı olarak.</span><span class="sxs-lookup"><span data-stu-id="687d0-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="687d0-124">Aşağıdaki örnekte gösterildiği <xref:System.Data.SqlClient.SqlDataReader> kullanarak iki SELECT deyimleri sonuçlarını işleme <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="687d0-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="687d0-125">DataReader gelen şema bilgilerini alma</span><span class="sxs-lookup"><span data-stu-id="687d0-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="687d0-126">Ancak bir **DataReader** olan şema bilgileri kullanılarak ayarlanan geçerli sonucu ile ilgili alabilirsiniz açık **GetSchemaTable** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="687d0-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="687d0-127">**GetSchemaTable** döndürür bir <xref:System.Data.DataTable> nesne satır ve geçerli sonuç kümesi için şema bilgileri içeren sütunlar ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="687d0-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="687d0-128">**DataTable** sonuç kümesinin her bir sütun için bir satır içerir.</span><span class="sxs-lookup"><span data-stu-id="687d0-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="687d0-129">Şema tablonun her sütunu eşleyen bir özelliğine döndürülen sütunlar sonuç satırlarını ayarlama, burada **ColumnName** özelliği adıdır ve özelliğinin değeri sütun değeridir.</span><span class="sxs-lookup"><span data-stu-id="687d0-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="687d0-130">Aşağıdaki örnek, şema bilgileri için Yazar **DataReader**.</span><span class="sxs-lookup"><span data-stu-id="687d0-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="687d0-131">OLE DB bölümlerle çalışma</span><span class="sxs-lookup"><span data-stu-id="687d0-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="687d0-132">Hiyerarşik satır kümeleri ya da bölümlerini (OLE DB türü **DBTYPE_HCHAPTER**, ADO türü **adChapter**), kullanılarak alınabilir <xref:System.Data.OleDb.OleDbDataReader>.</span><span class="sxs-lookup"><span data-stu-id="687d0-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="687d0-133">Olarak bölüm içeren bir sorgu döndürüldüğünde bir **DataReader**, bu bölümde, bir sütun olarak döndürülen **DataReader** ve olarak kullanıma sunulduğunu bir **DataReader** nesne.</span><span class="sxs-lookup"><span data-stu-id="687d0-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="687d0-134">ADO.NET **veri kümesi** hiyerarşik satır kümeleri tablolar arasındaki üst-alt ilişkileri kullanarak temsil etmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="687d0-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="687d0-135">Daha fazla bilgi için [DataSets, DataTables ve DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="687d0-135">For more information, see [DataSets, DataTables, and DataViews](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="687d0-136">Aşağıdaki kod örneği MSDataShape sağlayıcı bir bölüm sütunu her müşteriye ait siparişlerin müşterilerin listesini oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="687d0-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="687d0-137">Oracle REF CURSOR sonuçlar döndürüyor</span><span class="sxs-lookup"><span data-stu-id="687d0-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="687d0-138">Oracle için .NET Framework veri sağlayıcısı, bir sorgu sonuç döndürmek için Oracle REF CURSOR kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="687d0-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="687d0-139">Bir Oracle REF CURSOR olarak döndürülen bir <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="687d0-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="687d0-140">Alabileceğiniz bir <xref:System.Data.OracleClient.OracleDataReader> kullanarak bir Oracle REF CURSOR temsil eden bir nesne <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="687d0-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="687d0-141">Ayrıca belirtebileceğiniz bir <xref:System.Data.OracleClient.OracleCommand> olarak bir veya daha fazla Oracle REF CURSOR döndüren **SelectCommand** için bir <xref:System.Data.OracleClient.OracleDataAdapter> doldurmak için kullanılan bir <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="687d0-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="687d0-142">Bir Oracle veri kaynağından döndürülen bir REF CURSOR erişmek için oluşturun bir <xref:System.Data.OracleClient.OracleCommand> sorgunuz için ve REF CURSOR için başvuran çıkış parametresi ekleyin <xref:System.Data.OracleClient.OracleCommand.Parameters> koleksiyonunu, <xref:System.Data.OracleClient.OracleCommand>.</span><span class="sxs-lookup"><span data-stu-id="687d0-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="687d0-143">Parametrenin adını sorgunuzda REF CURSOR parametrenin adı eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="687d0-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="687d0-144">Parametre türünü ayarlamak <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="687d0-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="687d0-145"><xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> Yöntemi, <xref:System.Data.OracleClient.OracleCommand> döndürür bir <xref:System.Data.OracleClient.OracleDataReader> REF CURSOR için.</span><span class="sxs-lookup"><span data-stu-id="687d0-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="687d0-146">Varsa, <xref:System.Data.OracleClient.OracleCommand> birden çok REF CURSOR döndürür birden çok çıktı parametreleri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="687d0-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="687d0-147">Farklı REF CURSOR çağırarak erişebileceğiniz <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="687d0-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="687d0-148">Çağrı <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> döndürür bir <xref:System.Data.OracleClient.OracleDataReader> ilk REF CURSOR başvuruyor.</span><span class="sxs-lookup"><span data-stu-id="687d0-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="687d0-149">Ardından çağırabilirsiniz <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> sonraki REF CURSOR erişmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="687d0-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="687d0-150">Ancak parametrelerinde, <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> koleksiyon eşleşme REF CURSOR parametreleri adıyla çıkış <xref:System.Data.OracleClient.OracleDataReader> bunları içinde eklendikleri için sırada erişir <xref:System.Data.OracleClient.OracleCommand.Parameters> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="687d0-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="687d0-151">Örneğin, aşağıdaki Oracle paket ve paket gövdesi göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="687d0-151">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="687d0-152">Aşağıdaki kod oluşturur bir <xref:System.Data.OracleClient.OracleCommand> döndüren REF CURSOR önceki Oracle paketi türünde iki parametre ekleyerek <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> için <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="687d0-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="687d0-153">Aşağıdaki kod, önceki komutla sonuçlarını döndürür <xref:System.Data.OracleClient.OracleDataReader.Read> ve <xref:System.Data.OracleClient.OracleDataReader.NextResult> yöntemlerinin <xref:System.Data.OracleClient.OracleDataReader>.</span><span class="sxs-lookup"><span data-stu-id="687d0-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="687d0-154">REF CURSOR parametreleri sırayla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="687d0-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="687d0-155">Aşağıdaki örnek önceki komutun doldurmak için kullanır. bir <xref:System.Data.DataSet> Oracle paket sonuçlarla.</span><span class="sxs-lookup"><span data-stu-id="687d0-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
>  <span data-ttu-id="687d0-156">Önlemek için bir **OverflowException**, değer depolanmadan önce her türünden dönüştürme Oracle numarası geçerli bir .NET Framework türü de ele öneririz bir <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="687d0-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="687d0-157">Kullanabileceğiniz <xref:System.Data.Common.DataAdapter.FillError> belirlemek için olay bir **OverflowException** oluştu.</span><span class="sxs-lookup"><span data-stu-id="687d0-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="687d0-158">Daha fazla bilgi için <xref:System.Data.Common.DataAdapter.FillError> olay bkz [DataAdapter olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="687d0-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="687d0-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="687d0-159">See also</span></span>

- [<span data-ttu-id="687d0-160">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="687d0-160">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [<span data-ttu-id="687d0-161">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="687d0-161">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [<span data-ttu-id="687d0-162">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="687d0-162">Retrieving Database Schema Information</span></span>](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)
- [<span data-ttu-id="687d0-163">ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="687d0-163">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
