---
title: DataReader Kullanarak Veri Alma
description: Bu örnek kodla ADO.NET içinde bir DataReader kullanarak veri almayı öğrenin. DataReader, arabelleğe alınmamış bir veri akışı sağlar.
ms.date: 10/29/2018
dev_langs:
- csharp
- vb
ms.assetid: 97afc121-fb8b-465b-bab3-6d844420badb
ms.openlocfilehash: 6e5161cc325bf0379bb9241b99c473c539ad1081
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286604"
---
# <a name="retrieve-data-using-a-datareader"></a><span data-ttu-id="74668-104">DataReader kullanarak veri alma</span><span class="sxs-lookup"><span data-stu-id="74668-104">Retrieve data using a DataReader</span></span>
<span data-ttu-id="74668-105">**DataReader**kullanarak verileri almak Için, **komut** nesnesinin bir örneğini oluşturun ve sonra bir veri kaynağından satırları almak için **Command. ExecuteReader** çağırarak bir **DataReader** oluşturun.</span><span class="sxs-lookup"><span data-stu-id="74668-105">To retrieve data using a **DataReader**, create an instance of the **Command** object, and then create a **DataReader** by calling **Command.ExecuteReader** to retrieve rows from a data source.</span></span> <span data-ttu-id="74668-106">**DataReader** , yordamsal mantığın bir veri kaynağından oluşan sonuçları sırayla verimli bir şekilde işlemesini sağlayan, arabelleğe alınmamış bir veri akışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="74668-106">The **DataReader** provides an unbuffered stream of data that allows procedural logic to efficiently process results from a data source sequentially.</span></span> <span data-ttu-id="74668-107">Veriler bellekte önbelleğe alınmadığı için büyük miktarlarda veri alırken **DataReader** iyi bir seçimdir.</span><span class="sxs-lookup"><span data-stu-id="74668-107">The **DataReader** is a good choice when you're retrieving large amounts of data because the data is not cached in memory.</span></span>

<span data-ttu-id="74668-108">Aşağıdaki örnekte, geçerli bir **DataReader** `reader` DataReader temsil eden ve `command` geçerli bir komut nesnesini temsil eden bir DataReader kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="74668-108">The following example illustrates using a **DataReader**, where `reader` represents a valid DataReader and `command` represents a valid Command object.</span></span>  

```csharp
reader = command.ExecuteReader();  
```

```vb
reader = command.ExecuteReader()
```  

<span data-ttu-id="74668-109">Sorgu sonuçlarından bir satır almak için **DataReader. Read** metodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="74668-109">Use the **DataReader.Read** method to obtain a row from the query results.</span></span> <span data-ttu-id="74668-110">Döndürülen satırın her sütununa, sütunun ad veya sıra numarasını **DataReader**' a geçirerek erişebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74668-110">You can access each column of the returned row by passing the name or ordinal number of the column to the **DataReader**.</span></span> <span data-ttu-id="74668-111">Bununla birlikte, en iyi performans için, **DataReader** kendi yerel veri türlerindeki (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**vb.) sütun değerlerine erişmenize izin veren bir dizi yöntem sunar.</span><span class="sxs-lookup"><span data-stu-id="74668-111">However, for best performance, the **DataReader** provides a series of methods that allow you to access column values in their native data types (**GetDateTime**, **GetDouble**, **GetGuid**, **GetInt32**, and so on).</span></span> <span data-ttu-id="74668-112">Veri sağlayıcısına özgü **DataReaders**türü belirlenmiş erişimci yöntemlerinin bir listesi için bkz <xref:System.Data.OleDb.OleDbDataReader> <xref:System.Data.SqlClient.SqlDataReader> . ve.</span><span class="sxs-lookup"><span data-stu-id="74668-112">For a list of typed accessor methods for data provider-specific **DataReaders**, see <xref:System.Data.OleDb.OleDbDataReader> and <xref:System.Data.SqlClient.SqlDataReader>.</span></span> <span data-ttu-id="74668-113">Temel alınan veri türünü bildiğiniz durumlarda türü belirlenmiş erişimci yöntemlerinin kullanılması, sütun değerini alırken gereken tür dönüştürme miktarını azaltır.</span><span class="sxs-lookup"><span data-stu-id="74668-113">Using the typed accessor methods when you know the underlying data type reduces the amount of type conversion required when retrieving the column value.</span></span>  
  
 <span data-ttu-id="74668-114">Aşağıdaki örnek, bir **DataReader** nesnesi üzerinden yinelenir ve her satırdan iki sütun döndürür.</span><span class="sxs-lookup"><span data-stu-id="74668-114">The following example iterates through a **DataReader** object and returns two columns from each row.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.HasRows#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.HasRows/VB/source.vb#1)]  
  
## <a name="closing-the-datareader"></a><span data-ttu-id="74668-115">DataReader kapatılıyor</span><span class="sxs-lookup"><span data-stu-id="74668-115">Closing the DataReader</span></span>  
 <span data-ttu-id="74668-116">**DataReader** nesnesini kullanmayı bitirdiğinizde her zaman **Close** yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="74668-116">Always call the **Close** method when you have finished using the **DataReader** object.</span></span>  
  
 <span data-ttu-id="74668-117">**Komutunuz** çıkış parametrelerini veya dönüş değerlerini Içeriyorsa, **DataReader** kapatılana kadar bu değerler kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="74668-117">If your **Command** contains output parameters or return values, those values are not available until the **DataReader** is closed.</span></span>  
  
 <span data-ttu-id="74668-118">Bir **DataReader** açık olsa da **bağlantı** , bu **DataReader**tarafından özel olarak kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="74668-118">While a **DataReader** is open, the **Connection** is in use exclusively by that **DataReader**.</span></span> <span data-ttu-id="74668-119">Özgün **DataReader** kapatılana kadar, başka bir **DataReader**oluşturma da dahil olmak üzere **bağlantı**için herhangi bir komut yürütemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="74668-119">You cannot execute any commands for the **Connection**, including creating another **DataReader**, until the original **DataReader** is closed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74668-120">Bir **bağlantıyı**, bir **DataReader**'ı veya sınıfınızın **Finalize** yönteminde herhangi bir yönetilen nesneyi **kapatma** veya **atma** işlemini çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="74668-120">Do not call **Close** or **Dispose** on a **Connection**, a **DataReader**, or any other managed object in the **Finalize** method of your class.</span></span> <span data-ttu-id="74668-121">Sonlandırıcıda yalnızca, sınıfınızın doğrudan sahip olduğu yönetilmeyen kaynakları serbest bırakın.</span><span class="sxs-lookup"><span data-stu-id="74668-121">In a finalizer, only release unmanaged resources that your class owns directly.</span></span> <span data-ttu-id="74668-122">Sınıfınız hiçbir yönetilmeyen kaynağa sahip değilse, sınıf tanımınıza bir **Finalize** yöntemi eklemeyin.</span><span class="sxs-lookup"><span data-stu-id="74668-122">If your class does not own any unmanaged resources, do not include a **Finalize** method in your class definition.</span></span> <span data-ttu-id="74668-123">Daha fazla bilgi için bkz. [çöp toplama](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="74668-123">For more information, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="retrieving-multiple-result-sets-using-nextresult"></a><span data-ttu-id="74668-124">NextResult kullanarak birden çok sonuç kümesi alma</span><span class="sxs-lookup"><span data-stu-id="74668-124">Retrieving multiple result sets using NextResult</span></span>  
 <span data-ttu-id="74668-125">**DataReader** birden çok sonuç kümesi döndürürse, sonuç kümelerini sırayla yinelemek Için **NextResult** yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="74668-125">If the **DataReader** returns multiple result sets, call the **NextResult** method to iterate through the result sets sequentially.</span></span> <span data-ttu-id="74668-126">Aşağıdaki örnek, <xref:System.Data.SqlClient.SqlDataReader> yöntemi kullanılarak ıkı SELECT deyimi sonuçlarının işlenme işlemini gösterir <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> .</span><span class="sxs-lookup"><span data-stu-id="74668-126">The following example shows the <xref:System.Data.SqlClient.SqlDataReader> processing the results of two SELECT statements using the <xref:System.Data.SqlClient.SqlCommand.ExecuteReader%2A> method.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.NextResult#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.NextResult/VB/source.vb#1)]  
  
## <a name="getting-schema-information-from-the-datareader"></a><span data-ttu-id="74668-127">DataReader 'tan şema bilgileri alma</span><span class="sxs-lookup"><span data-stu-id="74668-127">Getting schema information from the DataReader</span></span>  
 <span data-ttu-id="74668-128">Bir **DataReader** açıkken, **GetSchemaTable** yöntemini kullanarak geçerli sonuç kümesiyle ilgili şema bilgilerini alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74668-128">While a **DataReader** is open, you can retrieve schema information about the current result set using the **GetSchemaTable** method.</span></span> <span data-ttu-id="74668-129">**GetSchemaTable** <xref:System.Data.DataTable> , geçerli sonuç kümesi için şema bilgilerini içeren satırlar ve sütunlar ile doldurulmuş bir nesne döndürür.</span><span class="sxs-lookup"><span data-stu-id="74668-129">**GetSchemaTable** returns a <xref:System.Data.DataTable> object populated with rows and columns that contain the schema information for the current result set.</span></span> <span data-ttu-id="74668-130">**DataTable** , sonuç kümesinin her bir sütunu için bir satır içerir.</span><span class="sxs-lookup"><span data-stu-id="74668-130">The **DataTable** contains one row for each column of the result set.</span></span> <span data-ttu-id="74668-131">Şema tablosunun her sütunu, sonuç kümesinin satırlarında döndürülen sütunların bir özelliğine eşlenir; burada **sütunadı** , özelliğin adıdır ve sütununun değeri özelliğin değeridir.</span><span class="sxs-lookup"><span data-stu-id="74668-131">Each column of the schema table maps to a property of the columns returned in the rows of the result set, where the **ColumnName** is the name of the property and the value of the column is the value of the property.</span></span> <span data-ttu-id="74668-132">Aşağıdaki örnek, **DataReader**için şema bilgilerini yazar.</span><span class="sxs-lookup"><span data-stu-id="74668-132">The following example writes out the schema information for **DataReader**.</span></span>  
  
 [!code-csharp[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.GetSchemaTable#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.GetSchemaTable/VB/source.vb#1)]  
  
## <a name="working-with-ole-db-chapters"></a><span data-ttu-id="74668-133">OLE DB bölümler ile çalışma</span><span class="sxs-lookup"><span data-stu-id="74668-133">Working with OLE DB chapters</span></span>  
 <span data-ttu-id="74668-134">Hiyerarşik satır kümeleri veya bölümler (OLE DB türü **dbtype_hchapter**, ADO türü **adbölüm**) kullanılarak alınabilir <xref:System.Data.OleDb.OleDbDataReader> .</span><span class="sxs-lookup"><span data-stu-id="74668-134">Hierarchical rowsets, or chapters (OLE DB type **DBTYPE_HCHAPTER**, ADO type **adChapter**), can be retrieved using the <xref:System.Data.OleDb.OleDbDataReader>.</span></span> <span data-ttu-id="74668-135">Bölüm içeren bir sorgu **DataReader**olarak döndürüldüğünde, bölüm bu **DataReader** 'da bir sütun olarak döndürülür ve bir **DataReader** nesnesi olarak sunulur.</span><span class="sxs-lookup"><span data-stu-id="74668-135">When a query that includes a chapter is returned as a **DataReader**, the chapter is returned as a column in that **DataReader** and is exposed as a **DataReader** object.</span></span>  
  
 <span data-ttu-id="74668-136">ADO.NET **veri kümesi** , tablolar arasında üst-alt ilişkilerini kullanarak hiyerarşik satır kümelerini temsil etmek için de kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74668-136">The ADO.NET **DataSet** can also be used to represent hierarchical rowsets by using parent-child relationships between tables.</span></span> <span data-ttu-id="74668-137">Daha fazla bilgi için bkz. [veri kümeleri, DataTable ve DataView](./dataset-datatable-dataview/index.md).</span><span class="sxs-lookup"><span data-stu-id="74668-137">For more information, see [DataSets, DataTables, and DataViews](./dataset-datatable-dataview/index.md).</span></span>  
  
 <span data-ttu-id="74668-138">Aşağıdaki kod örneği, bir müşteri listesindeki her müşteri için siparişlerin bir bölüm sütununu oluşturmak üzere MSDataShape sağlayıcısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="74668-138">The following code example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span>  
  
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
  
## <a name="returning-results-with-oracle-ref-cursors"></a><span data-ttu-id="74668-139">Oracle REF IMLEÇLER ile sonuçları döndürme</span><span class="sxs-lookup"><span data-stu-id="74668-139">Returning results with Oracle REF CURSORs</span></span>  
 <span data-ttu-id="74668-140">Oracle için .NET Framework Veri Sağlayıcısı, Oracle REF IMLEÇLER 'in bir sorgu sonucu döndürecek şekilde kullanılmasını destekler.</span><span class="sxs-lookup"><span data-stu-id="74668-140">The .NET Framework Data Provider for Oracle supports the use of Oracle REF CURSORs to return a query result.</span></span> <span data-ttu-id="74668-141">Oracle REF CURSOR bir olarak döndürülür <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="74668-141">An Oracle REF CURSOR is returned as an <xref:System.Data.OracleClient.OracleDataReader>.</span></span>  
  
 <span data-ttu-id="74668-142"><xref:System.Data.OracleClient.OracleDataReader>Yöntemini kullanarak bir Oracle başvuru imlecini temsil eden bir nesnesi alabilirsiniz <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> .</span><span class="sxs-lookup"><span data-stu-id="74668-142">You can retrieve an <xref:System.Data.OracleClient.OracleDataReader> object that represents an Oracle REF CURSOR by using the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader%2A> method.</span></span> <span data-ttu-id="74668-143">Ayrıca, <xref:System.Data.OracleClient.OracleCommand> bir veya daha fazla Oracle başvuru imleçlerini bir tane doldurdukları Için **SelectCommand** olarak döndüren bir de belirtebilirsiniz <xref:System.Data.OracleClient.OracleDataAdapter> <xref:System.Data.DataSet> .</span><span class="sxs-lookup"><span data-stu-id="74668-143">You can also specify an <xref:System.Data.OracleClient.OracleCommand> that returns one or more Oracle REF CURSORs as the **SelectCommand** for an <xref:System.Data.OracleClient.OracleDataAdapter> used to fill a <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="74668-144">Oracle veri kaynağından döndürülen bir başvuru IMLECINE erişmek için, <xref:System.Data.OracleClient.OracleCommand> sorgunuz için bir oluşturun ve başvuru imlecine başvuran bir çıkış parametresi ekleyin <xref:System.Data.OracleClient.OracleCommand.Parameters> <xref:System.Data.OracleClient.OracleCommand> .</span><span class="sxs-lookup"><span data-stu-id="74668-144">To access a REF CURSOR returned from an Oracle data source, create an <xref:System.Data.OracleClient.OracleCommand> for your query and add an output parameter that references the REF CURSOR to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection of your <xref:System.Data.OracleClient.OracleCommand>.</span></span> <span data-ttu-id="74668-145">Parametrenin adı Sorgunuzdaki REF CURSOR parametresinin adıyla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="74668-145">The name of the parameter must match the name of the REF CURSOR parameter in your query.</span></span> <span data-ttu-id="74668-146">Parametresinin türünü olarak ayarlayın <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="74668-146">Set the type of the parameter to <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType>.</span></span> <span data-ttu-id="74668-147">' <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> In YÖNTEMI <xref:System.Data.OracleClient.OracleCommand> <xref:System.Data.OracleClient.OracleDataReader> başvuru imleci için döndürür.</span><span class="sxs-lookup"><span data-stu-id="74668-147">The <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method of your <xref:System.Data.OracleClient.OracleCommand> returns an <xref:System.Data.OracleClient.OracleDataReader> for the REF CURSOR.</span></span>  
  
 <span data-ttu-id="74668-148"><xref:System.Data.OracleClient.OracleCommand>Birden çok başvuru imleci döndürürse, birden çok çıkış parametresi ekleyin.</span><span class="sxs-lookup"><span data-stu-id="74668-148">If your <xref:System.Data.OracleClient.OracleCommand> returns multiple REF CURSORS, add multiple output parameters.</span></span> <span data-ttu-id="74668-149">Yöntemini çağırarak farklı başvuru Imleçlerinin erişimine erişebilirsiniz <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="74668-149">You can access the different REF CURSORs by calling the <xref:System.Data.OracleClient.OracleCommand.ExecuteReader?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="74668-150">Çağrısı, <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> <xref:System.Data.OracleClient.OracleDataReader> Ilk başvuru imlecine başvuran döndürür.</span><span class="sxs-lookup"><span data-stu-id="74668-150">The call to <xref:System.Data.OracleClient.OracleCommand.ExecuteReader> returns an <xref:System.Data.OracleClient.OracleDataReader> referencing the first REF CURSOR.</span></span> <span data-ttu-id="74668-151">Ardından, <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> sonrakı başvuru imleçlerini erişmek için yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74668-151">You can then call the <xref:System.Data.OracleClient.OracleDataReader.NextResult?displayProperty=nameWithType> method to access subsequent REF CURSORs.</span></span> <span data-ttu-id="74668-152"><xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType>Koleksiyonunuzdaki parametreler, başvuru imleci çıkış parametreleriyle ada göre eşleşir, ancak <xref:System.Data.OracleClient.OracleDataReader> onlara koleksiyona eklendikleri sırayla erişir <xref:System.Data.OracleClient.OracleCommand.Parameters> .</span><span class="sxs-lookup"><span data-stu-id="74668-152">Although the parameters in your <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection match the REF CURSOR output parameters by name, the <xref:System.Data.OracleClient.OracleDataReader> accesses them in the order in which they were added to the <xref:System.Data.OracleClient.OracleCommand.Parameters> collection.</span></span>  
  
 <span data-ttu-id="74668-153">Örneğin, aşağıdaki Oracle paketini ve paket gövdesini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="74668-153">For example, consider the following Oracle package and package body.</span></span>  
  
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
  
 <span data-ttu-id="74668-154">Aşağıdaki kod, <xref:System.Data.OracleClient.OracleCommand> koleksiyona iki tür parametre ekleyerek önceki Oracle PAKETINDEN başvuru imleçleri döndüren bir oluşturur <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="74668-154">The following code creates an <xref:System.Data.OracleClient.OracleCommand> that returns the REF CURSORs from the previous Oracle package by adding two parameters of type <xref:System.Data.OracleClient.OracleType.Cursor?displayProperty=nameWithType> to the <xref:System.Data.OracleClient.OracleCommand.Parameters?displayProperty=nameWithType> collection.</span></span>  
  
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
  
 <span data-ttu-id="74668-155">Aşağıdaki kod, ve yöntemlerini kullanarak önceki komutun sonucunu döndürür <xref:System.Data.OracleClient.OracleDataReader.Read> <xref:System.Data.OracleClient.OracleDataReader.NextResult> <xref:System.Data.OracleClient.OracleDataReader> .</span><span class="sxs-lookup"><span data-stu-id="74668-155">The following code returns the results of the previous command using the <xref:System.Data.OracleClient.OracleDataReader.Read> and <xref:System.Data.OracleClient.OracleDataReader.NextResult> methods of the <xref:System.Data.OracleClient.OracleDataReader>.</span></span> <span data-ttu-id="74668-156">REF CURSOR parametreleri sırayla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="74668-156">The REF CURSOR parameters are returned in order.</span></span>  
  
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
  
 <span data-ttu-id="74668-157">Aşağıdaki örnek, <xref:System.Data.DataSet> Oracle paketinin sonuçlarıyla birlikte doldurmak için Previous komutunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="74668-157">The following example uses the previous command to populate a <xref:System.Data.DataSet> with the results of the Oracle package.</span></span>  
  
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
> <span data-ttu-id="74668-158">Bir **OverflowException**'ı önlemek için, değeri bir içinde depolamadan önce Oracle Number türünden geçerli bir .NET Framework türüne dönüştürme işleminin de işlemesini öneririz <xref:System.Data.DataRow> .</span><span class="sxs-lookup"><span data-stu-id="74668-158">To avoid an **OverflowException**, we recommend that you also handle any conversion from the Oracle NUMBER type to a valid .NET Framework type before storing the value in a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="74668-159"><xref:System.Data.Common.DataAdapter.FillError>Bir **OverflowException** 'ın oluşup oluşmadığını öğrenmek için olayını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="74668-159">You can use the <xref:System.Data.Common.DataAdapter.FillError> event to determine if an **OverflowException** has occurred.</span></span> <span data-ttu-id="74668-160">Olay hakkında daha fazla bilgi için <xref:System.Data.Common.DataAdapter.FillError> bkz. [DataAdapter olaylarını işleme](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="74668-160">For more information on the <xref:System.Data.Common.DataAdapter.FillError> event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74668-161">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74668-161">See also</span></span>

- [<span data-ttu-id="74668-162">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="74668-162">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="74668-163">Komutlar ve Parametreler</span><span class="sxs-lookup"><span data-stu-id="74668-163">Commands and Parameters</span></span>](commands-and-parameters.md)
- [<span data-ttu-id="74668-164">Veritabanı Şema Bilgilerini Alma</span><span class="sxs-lookup"><span data-stu-id="74668-164">Retrieving Database Schema Information</span></span>](retrieving-database-schema-information.md)
- [<span data-ttu-id="74668-165">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="74668-165">ADO.NET Overview</span></span>](ado-net-overview.md)
