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
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="e189c-102">DataReader kullanarak veri alma</span><span class="sxs-lookup"><span data-stu-id="e189c-102">Retrieve data using a DataReader</span></span>
<span data-ttu-id="e189c-103">**DataReader**kullanarak veri almak için Komut **nesnesinin** bir örneğini oluşturun ve ardından veri kaynağından satırları almak için **Command.ExecuteReader'ı** arayarak bir **DataReader** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="e189c-103">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="e189c-104">**DataReader,** yordam mantığının bir veri kaynağından elde edilen sonuçları sırayla verimli bir şekilde işlemesini sağlayan, engellenmemiş bir veri akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="e189c-104">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="e189c-105">Veriler bellekte önbelleğe alınmadığından, büyük miktarda veri alırken **DataReader** iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="e189c-105">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="e189c-106">Aşağıdaki örnek, geçerli bir DataReader'ı temsil eden `command` ve geçerli bir Komut nesnesini temsil eden `reader` bir **DataReader'ı**kullanarak gösteriş gösterir.</span><span class="sxs-lookup"><span data-stu-id="e189c-106">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="e189c-107">Sorgu sonuçlarından bir satır elde etmek için **DataReader.Read** yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e189c-107">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="e189c-108">Döndürülen satırın her sütununa, sütunun adını veya ordinal numarasını **DataReader'a**geçirerek erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e189c-108">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="e189c-109">Ancak, en iyi performans **için, DataReader** kendi yerel veri türlerinde sütun değerlerine erişmenizi sağlayan bir dizi yöntem sağlar **(GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, vb).</span><span class="sxs-lookup"><span data-stu-id="e189c-109">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="e189c-110">Veri sağlayıcısına özgü **DataReaders**için dakti-yazılı erişimci <xref:System.Data.SqlClient.SqlDataReader>yöntemlerin listesi için bkz. <xref:System.Data.OleDb.OleDbDataReader></span><span class="sxs-lookup"><span data-stu-id="e189c-110">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="e189c-111">Temel veri türünü bildiğinizde yazılan erişimci yöntemlerikullanmak, sütun değerini alırken gereken tür dönüştürme miktarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="e189c-111">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="e189c-112">Aşağıdaki örnek, bir **DataReader nesnesi** üzerinden yineler ve her satırdan iki sütun döndürür.</span><span class="sxs-lookup"><span data-stu-id="e189c-112">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="e189c-113">DataReader'ı Kapatma</span><span class="sxs-lookup"><span data-stu-id="e189c-113">Closing the DataReader</span></span>  
 <span data-ttu-id="e189c-114">**DataReader** nesnesini kullanmayı bitirdiğinizde her zaman **Kapat** yöntemini arayın.</span><span class="sxs-lookup"><span data-stu-id="e189c-114">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="e189c-115">**Komutunuz** çıktı parametreleri veya iade değerleri içeriyorsa, **DataReader** kapatılana kadar bu değerler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e189c-115">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="e189c-116">Bir **DataReader** açık ken, **Bağlantı** yalnızca bu **DataReader**tarafından kullanılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e189c-116">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="e189c-117">Özgün **DataReader** kapatılana **kadar,** başka bir **DataReader**oluşturma da dahil olmak üzere Bağlantı için herhangi bir komut yürütemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="e189c-117">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e189c-118">Sınıfınızın **Finalize** yönteminde **Bağlantıyı** **Kapat** veya **Elden Çıkar'ı,** **DataReader'ı**veya yönetilen başka bir nesneyi aramayın.</span><span class="sxs-lookup"><span data-stu-id="e189c-118">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="e189c-119">Sonlandırıcıda, yalnızca sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın.</span><span class="sxs-lookup"><span data-stu-id="e189c-119">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="e189c-120">Sınıfınız yönetilmeyen kaynaklara sahip değilse, sınıf tanımınıza bir **Sonlandırma** yöntemi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="e189c-120">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="e189c-121">Daha fazla bilgi için [Çöp Toplama'ya](../../../standard/garbage-collection/index.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="e189c-121">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="e189c-122">NextResult kullanarak birden çok sonuç kümesi alma</span><span class="sxs-lookup"><span data-stu-id="e189c-122">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="e189c-123">**DataReader** birden çok sonuç kümesi döndürürse, sonuç kümeleri aracılığıyla sırayla yinelemek için **NextResult** yöntemini arayın.</span><span class="sxs-lookup"><span data-stu-id="e189c-123">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="e189c-124">Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlDataReader> yöntemi kullanarak iki SELECT deyiminin sonuçlarını işleme gösterir. <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A></span><span class="sxs-lookup"><span data-stu-id="e189c-124">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="e189c-125">DataReader'dan şema bilgisi alma</span><span class="sxs-lookup"><span data-stu-id="e189c-125">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="e189c-126">**DataReader** açıkken, **GetSchemaTable** yöntemini kullanarak geçerli sonuç kümesi hakkında şema bilgilerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e189c-126">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="e189c-127">**GetSchemaTable,** <xref:System.Data.DataTable> geçerli sonuç kümesiiçin şema bilgilerini içeren satırlar ve sütunlarla dolu bir nesneyi döndürür.</span><span class="sxs-lookup"><span data-stu-id="e189c-127">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="e189c-128">**DataTable,** sonuç kümesinin her sütunu için bir satır içerir.</span><span class="sxs-lookup"><span data-stu-id="e189c-128">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="e189c-129">Şema tablosunun her sütunu, sonuç kümesinin satırlarında döndürülen sütunların bir özelliğiyle eşlenir, **sütun adı** özelliğin adıdır ve sütunun değeri özelliğin değeridir.</span><span class="sxs-lookup"><span data-stu-id="e189c-129">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="e189c-130">Aşağıdaki örnek, **DataReader**için şema bilgilerini yazar.</span><span class="sxs-lookup"><span data-stu-id="e189c-130">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="e189c-131">OLE DB bölümleri ile çalışma</span><span class="sxs-lookup"><span data-stu-id="e189c-131">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="e189c-132">Hiyerarşik sıra kümeleri veya bölümler (OLE DB türü **DBTYPE_HCHAPTER**, ADO <xref:System.Data.OleDb.OleDbDataReader>türü **adChapter**), .</span><span class="sxs-lookup"><span data-stu-id="e189c-132">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="e189c-133">Bir bölümü içeren bir sorgu **DataReader**olarak döndürüldüğünde, bölüm bu **DataReader'da** sütun olarak döndürülür ve **DataReader nesnesi** olarak açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e189c-133">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="e189c-134">ADO.NET **DataSet,** tablolar arasındaki üst-alt ilişkileri kullanarak hiyerarşik satır kümelerini temsil etmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e189c-134">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="e189c-135">Daha fazla bilgi için [Bkz. Veri Kümeleri, Veri Tabloları ve Veri Görünümleri.](./dataset-datatable-dataview/index.md)</span><span class="sxs-lookup"><span data-stu-id="e189c-135">For more information, see [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="e189c-136">Aşağıdaki kod örneği, müşteri listesindeki her müşteri için bir sipariş bölümü sütunu oluşturmak için MSDataShape Sağlayıcısı'nı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e189c-136">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="e189c-137">Oracle REF CURSOR ile sonuçları döndürme</span><span class="sxs-lookup"><span data-stu-id="e189c-137">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="e189c-138">Oracle için .NET Framework Data Provider, bir sorgu sonucunu döndürmek için Oracle REF CURSOR kullanımını destekler.</span><span class="sxs-lookup"><span data-stu-id="e189c-138">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="e189c-139">Bir Oracle REF CURSOR <xref:System.Data.OracleClient.OracleDataReader>olarak döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e189c-139">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="e189c-140">Yöntemi kullanarak <xref:System.Data.OracleClient.OracleDataReader> Oracle REF CURSOR'u temsil eden bir nesne alabilirsiniz. <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A></span><span class="sxs-lookup"><span data-stu-id="e189c-140">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="e189c-141">Ayrıca, <xref:System.Data.OracleClient.OracleCommand> bir veya daha fazla Oracle REF CURSOR'u <xref:System.Data.OracleClient.OracleDataAdapter> **selectcommand** olarak döndüren bir <xref:System.Data.DataSet>tane de belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e189c-141">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="e189c-142">Oracle veri kaynağından döndürülen bir REF CURSOR'a erişmek için, sorgunuz için bir sorun <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleCommand.Parameters> oluşturun ve <xref:System.Data.OracleClient.OracleCommand>REF CURSOR'unuzun koleksiyonuna başvuran bir çıktı parametresi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e189c-142">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="e189c-143">Parametrenin adı, sorgunuzdaki REF CURSOR parametresinin adıile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="e189c-143">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="e189c-144">Parametrenin türünü <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>' e ayarlama</span><span class="sxs-lookup"><span data-stu-id="e189c-144">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e189c-145"><xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> İade yönteminref <xref:System.Data.OracleClient.OracleCommand> CURSOR için bir. <xref:System.Data.OracleClient.OracleDataReader></span><span class="sxs-lookup"><span data-stu-id="e189c-145">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="e189c-146">Birden <xref:System.Data.OracleClient.OracleCommand> çok REF CURSORs döndürürseniz, birden çok çıkış parametresi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e189c-146">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="e189c-147">Yöntemi arayarak farklı REF CURSOR'lara <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e189c-147">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e189c-148">İlk REF <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> CURSOR'a başvuran bir <xref:System.Data.OracleClient.OracleDataReader> başvuruyu döndürme çağrısı.</span><span class="sxs-lookup"><span data-stu-id="e189c-148">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="e189c-149">Daha sonra sonraki <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> REF CURSOR erişmek için yöntemi arayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e189c-149">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="e189c-150">Koleksiyonunuzdaki <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> parametreler REF CURSOR çıkış parametrelerine <xref:System.Data.OracleClient.OracleDataReader> göre ada göre eşleşse de, bunlara <xref:System.Data.OracleClient.OracleCommand.Parameters> koleksiyona eklendikleri sırada erişir.</span><span class="sxs-lookup"><span data-stu-id="e189c-150">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="e189c-151">Örneğin, aşağıdaki Oracle paket ve paket gövdesini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e189c-151">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="e189c-152">Aşağıdaki kod, <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> koleksiyona iki tür parametre ekleyerek önceki Oracle paketinden REF CURSOR'ları döndüren bir kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e189c-152">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="e189c-153">Aşağıdaki kod önceki komutun <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> <xref:System.Data.OracleClient.OracleDataReader>sonuçlarını .</span><span class="sxs-lookup"><span data-stu-id="e189c-153">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="e189c-154">REF CURSOR parametreleri sırayla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="e189c-154">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="e189c-155">Aşağıdaki örnek, Oracle paketinin sonuçlarıyla bir önceki <xref:System.Data.DataSet> komutu kullanır.</span><span class="sxs-lookup"><span data-stu-id="e189c-155">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
> <span data-ttu-id="e189c-156">**Bir Taşma Özel Durum'dan**kaçınmak için, değeri bir 'de depolamadan önce Oracle NUMBER türünden <xref:System.Data.DataRow>geçerli bir .NET Framework türüne herhangi bir dönüştürme yi işlemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="e189c-156">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="e189c-157">**Bir Taşma Özel Durum** oluştu olup olmadığını belirlemek için <xref:System.Data.Common.DataAdapter.FillError> olay kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e189c-157">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="e189c-158"><xref:System.Data.Common.DataAdapter.FillError> Olay hakkında daha fazla bilgi için [DataAdapter Olaylarını Işleme](handling-dataadapter-events.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="e189c-158">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e189c-159">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e189c-159">See also</span></span>

- [<span data-ttu-id="e189c-160">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="e189c-160">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="e189c-161">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="e189c-161">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="e189c-162">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="e189c-162">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="e189c-163">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e189c-163">ADO.NET Overview</span></span>](ado-net-overview.md)
