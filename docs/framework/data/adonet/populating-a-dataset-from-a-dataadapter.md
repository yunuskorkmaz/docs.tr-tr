---
title: DataAdapter’dan bir DataSet Doldurma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: d2d7719c7f6c2cacd6d68ecae226673248bbd680
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149238"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a><span data-ttu-id="f8bab-102">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="f8bab-102">Populating a DataSet from a DataAdapter</span></span>
<span data-ttu-id="f8bab-103">ADO.NET, <xref:System.Data.DataSet> veri kaynağından bağımsız tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir temsilidir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-103">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model independent of the data source.</span></span> <span data-ttu-id="f8bab-104">Tablolar, `DataSet` kısıtlamalar ve tablolar arasındaki ilişkileri içeren tam bir veri kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8bab-104">The `DataSet` represents a complete set of data that includes tables, constraints, and relationships among the tables.</span></span> <span data-ttu-id="f8bab-105">Veri `DataSet` kaynağından bağımsız olduğundan, `DataSet` uygulamanın yerel verilerini ve birden çok veri kaynağından gelen verileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-105">Because the `DataSet` is independent of the data source, a `DataSet` can include data local to the application, and data from multiple data sources.</span></span> <span data-ttu-id="f8bab-106">Mevcut veri kaynakları `DataAdapter`ile etkileşim .</span><span class="sxs-lookup"><span data-stu-id="f8bab-106">Interaction with existing data sources is controlled through the `DataAdapter`.</span></span>  
  
 <span data-ttu-id="f8bab-107">Özelliği, `SelectCommand` veri `DataAdapter` kaynağından veri alan bir `Command` nesnedir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-107">The `SelectCommand` property of the `DataAdapter` is a `Command` object that retrieves data from the data source.</span></span> <span data-ttu-id="f8bab-108">, `InsertCommand` `UpdateCommand`, `DeleteCommand` ve özellikleri `DataAdapter` `Command` veri kaynağındaki verilerde yapılan değişikliklere göre veri güncelleştirmeleri yönetmek `DataSet`nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-108">The `InsertCommand`, `UpdateCommand`, and `DeleteCommand` properties of the `DataAdapter` are `Command` objects that manage updates to the data in the data source according to modifications made to the data in the `DataSet`.</span></span> <span data-ttu-id="f8bab-109">Bu özellikler, [DataAdapters ile Veri Kaynaklarının Güncelleştirilmesi](updating-data-sources-with-dataadapters.md)nde daha ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="f8bab-109">These properties are covered in more detail in [Updating Data Sources with DataAdapters](updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="f8bab-110">`DataAdapter` Yöntem `Fill` a sonuçları `DataSet` `SelectCommand` ile doldurmak için `DataAdapter`kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8bab-110">The `Fill` method of the `DataAdapter` is used to populate a `DataSet` with the results of the `SelectCommand` of the `DataAdapter`.</span></span> <span data-ttu-id="f8bab-111">`Fill`onun bağımsız değişkenleri olarak alır `DataSet` a `DataTable` doldurulur ve bir `DataTable` nesne, ya da satırlar `SelectCommand`döndürülen ile doldurulacak adı .</span><span class="sxs-lookup"><span data-stu-id="f8bab-111">`Fill` takes as its arguments a `DataSet` to be populated, and a `DataTable` object, or the name of the `DataTable` to be filled with the rows returned from the `SelectCommand`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8bab-112">Bir `DataAdapter` tablonun tümünün alınmasını kullanmak zaman alır, özellikle de tabloda çok sayıda satır varsa.</span><span class="sxs-lookup"><span data-stu-id="f8bab-112">Using the `DataAdapter` to retrieve all of a table takes time, especially if there are many rows in the table.</span></span> <span data-ttu-id="f8bab-113">Bunun nedeni, veritabanına erişme, verileri bulma ve işleme ve ardından verileri istemciye aktarmanın zaman alan olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="f8bab-113">This is because accessing the database, locating and processing the data, and then transferring the data to the client is time-consuming.</span></span> <span data-ttu-id="f8bab-114">Tüm tabloyu istemciye çekmek de sunucudaki tüm satırları kilitler.</span><span class="sxs-lookup"><span data-stu-id="f8bab-114">Pulling all of the table to the client also locks all of the rows on the server.</span></span> <span data-ttu-id="f8bab-115">Performansı artırmak için, istemciye döndürülen satır sayısını büyük ölçüde azaltmak için `WHERE` yan tümceyi kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8bab-115">To improve performance, you can use the `WHERE` clause to greatly reduce the number of rows returned to the client.</span></span> <span data-ttu-id="f8bab-116">Ayrıca, `SELECT` bildirimde yalnızca gerekli sütunları açıkça listeleyerek istemciye döndürülen veri miktarını da azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8bab-116">You can also reduce the amount of data returned to the client by only explicitly listing required columns in the `SELECT` statement.</span></span> <span data-ttu-id="f8bab-117">Başka bir iyi geçici çözüm toplu olarak satırları almaktır (bir seferde birkaç yüz satır gibi) ve yalnızca istemci geçerli toplu iş ile tamamlandığında sonraki toplu almak.</span><span class="sxs-lookup"><span data-stu-id="f8bab-117">Another good workaround is to retrieve the rows in batches (such as several hundred rows at a time) and only retrieve the next batch when the client is finished with the current batch.</span></span>  
  
 <span data-ttu-id="f8bab-118">Yöntem, `Fill` sütun `DataReader` adlarını ve tablolar `DataSet`oluşturmak için kullanılan türleri döndürmek için nesneyi zımni olarak kullanır ve tablolardaki satırları `DataSet`doldurmak için verileri.</span><span class="sxs-lookup"><span data-stu-id="f8bab-118">The `Fill` method uses the `DataReader` object implicitly to return the column names and types that are used to create the tables in the `DataSet`, and the data to populate the rows of the tables in the `DataSet`.</span></span> <span data-ttu-id="f8bab-119">Tablolar ve sütunlar yalnızca zaten yoksa oluşturulur; aksi `Fill` takdirde `DataSet` varolan şema kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8bab-119">Tables and columns are only created if they do not already exist; otherwise `Fill` uses the existing `DataSet` schema.</span></span> <span data-ttu-id="f8bab-120">Sütun [türleri, ADO.NET'daki Veri Türü Eşlemeleri'ndeki](data-type-mappings-in-ado-net.md)tablolara göre .NET Framework türleri olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f8bab-120">Column types are created as .NET Framework types according to the tables in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span> <span data-ttu-id="f8bab-121">Birincil anahtarlar, veri kaynağında `DataAdapter`ve **.**`MissingSchemaAction`</span><span class="sxs-lookup"><span data-stu-id="f8bab-121">Primary keys are not created unless they exist in the data source and `DataAdapter`**.**`MissingSchemaAction`</span></span> <span data-ttu-id="f8bab-122">olarak `MissingSchemaAction` **ayarlanır.** `AddWithKey`.</span><span class="sxs-lookup"><span data-stu-id="f8bab-122">is set to `MissingSchemaAction`**.**`AddWithKey`.</span></span> <span data-ttu-id="f8bab-123">Bir `Fill` tablo için birincil anahtarın var olduğunu bulursa, `DataSet` birincil anahtar sütun değerlerinin veri kaynağından döndürülen satırlarla eşleştiği satırlar için veri kaynağındaki verilerle birlikte verilerin üzerine yazılır.</span><span class="sxs-lookup"><span data-stu-id="f8bab-123">If `Fill` finds that a primary key exists for a table, it will overwrite data in the `DataSet` with data from the data source for rows where the primary key column values match those of the row returned from the data source.</span></span> <span data-ttu-id="f8bab-124">Birincil anahtar bulunamazsa, veriler `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f8bab-124">If no primary key is found, the data is appended to the tables in the `DataSet`.</span></span> <span data-ttu-id="f8bab-125">`Fill`doldurduğunuzda var olabilecek tüm eşlemeleri kullanır `DataSet` (bkz. [DataAdapter DataTable ve DataColumn Eşlemeleri).](dataadapter-datatable-and-datacolumn-mappings.md)</span><span class="sxs-lookup"><span data-stu-id="f8bab-125">`Fill` uses any mappings that may exist when you populate the `DataSet` (see [DataAdapter DataTable and DataColumn Mappings](dataadapter-datatable-and-datacolumn-mappings.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f8bab-126">Bir `SelectCommand` OUTER JOIN sonuçlarını döndürürse, `DataAdapter` `PrimaryKey` elde edilen `DataTable`değer için bir değer belirlemez.</span><span class="sxs-lookup"><span data-stu-id="f8bab-126">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` does not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="f8bab-127">Yinelenen satırların `PrimaryKey` doğru şekilde çözüldüğünden emin olmak için kendinizi tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-127">You must define the `PrimaryKey` yourself to make sure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="f8bab-128">Daha fazla bilgi için [Bkz. Birincil Anahtarları Tanımlama.](./dataset-datatable-dataview/defining-primary-keys.md)</span><span class="sxs-lookup"><span data-stu-id="f8bab-128">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="f8bab-129">Aşağıdaki kod örneği, Microsoft SQL <xref:System.Data.SqlClient.SqlDataAdapter> Server <xref:System.Data.SqlClient.SqlConnection> `Northwind` veritabanında a kullanan bir örnek <xref:System.Data.DataTable> oluşturur `DataSet` ve bir müşteri listesiyle bir'de doldurulur.</span><span class="sxs-lookup"><span data-stu-id="f8bab-129">The following code example creates an instance of a <xref:System.Data.SqlClient.SqlDataAdapter> that uses a <xref:System.Data.SqlClient.SqlConnection> to the Microsoft SQL Server `Northwind` database and populates a <xref:System.Data.DataTable> in a `DataSet` with the list of customers.</span></span> <span data-ttu-id="f8bab-130">SQL deyimi <xref:System.Data.SqlClient.SqlConnection> ve <xref:System.Data.SqlClient.SqlDataAdapter> kurucuya geçirilen bağımsız <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter>değişkenler.</span><span class="sxs-lookup"><span data-stu-id="f8bab-130">The SQL statement and <xref:System.Data.SqlClient.SqlConnection> arguments passed to the <xref:System.Data.SqlClient.SqlDataAdapter> constructor are used to create the <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> property of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8bab-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8bab-131">Example</span></span>  
  
```vb  
' Assumes that connection is a valid SqlConnection object.  
Dim queryString As String = _  
  "SELECT CustomerID, CompanyName FROM dbo.Customers"  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  queryString, connection)  
  
Dim customers As DataSet = New DataSet  
adapter.Fill(customers, "Customers")  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
```  
  
> [!NOTE]
> <span data-ttu-id="f8bab-132">Bu örnekte gösterilen kod açıkça açılmıyor `Connection`ve .</span><span class="sxs-lookup"><span data-stu-id="f8bab-132">The code shown in this example does not explicitly open and close the `Connection`.</span></span> <span data-ttu-id="f8bab-133">Yöntem, `Fill` bağlantının `Connection` `DataAdapter` zaten açık olmadığını bulursa, kullandığı yöntemi dolaylı olarak açar.</span><span class="sxs-lookup"><span data-stu-id="f8bab-133">The `Fill` method implicitly opens the `Connection` that the `DataAdapter` is using if it finds that the connection is not already open.</span></span> <span data-ttu-id="f8bab-134">Bağlantıyı `Fill` açtıysanız, tamamlandığında da bağlantıyı `Fill` kapatır.</span><span class="sxs-lookup"><span data-stu-id="f8bab-134">If `Fill` opened the connection, it also closes the connection when `Fill` is finished.</span></span> <span data-ttu-id="f8bab-135">Bu, bir veya bir `Fill` `Update`.</span><span class="sxs-lookup"><span data-stu-id="f8bab-135">This can simplify your code when you deal with a single operation such as a `Fill` or an `Update`.</span></span> <span data-ttu-id="f8bab-136">Ancak, açık bağlantı gerektiren birden çok işlem gerçekleştiriyorsanız, veri kaynağına karşı `Open` işlemleri gerçekleştiren `Connection`ve daha sonra yöntemin isini `Close` çağırarak `Connection`uygulamanızın performansını artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8bab-136">However, if you are performing multiple operations that require an open connection, you can improve the performance of your application by explicitly calling the `Open` method of the `Connection`, performing the operations against the data source, and then calling the `Close` method of the `Connection`.</span></span> <span data-ttu-id="f8bab-137">Diğer istemci uygulamaları tarafından kullanılmak üzere kaynakları serbest tutmak için veri kaynağına bağlantıları mümkün olduğunca kısa bir süre açık tutmaya çalışmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f8bab-137">You should try to keep connections to the data source open as briefly as possible to free resources for use by other client applications.</span></span>  
  
## <a name="multiple-result-sets"></a><span data-ttu-id="f8bab-138">Birden Fazla Sonuç Kümesi</span><span class="sxs-lookup"><span data-stu-id="f8bab-138">Multiple Result Sets</span></span>  
 <span data-ttu-id="f8bab-139">Birden `DataAdapter` çok sonuç kümesiyle karşılaşırsa, `DataSet`'de birden çok tablo oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8bab-139">If the `DataAdapter` encounters multiple result sets, it creates multiple tables in the `DataSet`.</span></span> <span data-ttu-id="f8bab-140">Tablolara Tablo0 için "Tablo" ile başlayarak Tablo*N'nin*artımlı varsayılan adı verilir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-140">The tables are given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span> <span data-ttu-id="f8bab-141">Bir tablo adı `Fill` yönteme bağımsız değişken olarak aktarılırsa, tablolara TableName0 için "TableName" ile başlayarak Tablo Adı*N'nin*artımlı varsayılan adı verilir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-141">If a table name is passed as an argument to the `Fill` method, the tables are given an incremental default name of TableName*N*, starting with "TableName" for TableName0.</span></span>  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a><span data-ttu-id="f8bab-142">Birden Çok DataAdapters'dan Bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="f8bab-142">Populating a DataSet from Multiple DataAdapters</span></span>  
 <span data-ttu-id="f8bab-143">Herhangi bir `DataAdapter` sayıda nesne bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f8bab-143">Any number of `DataAdapter` objects can be used with a `DataSet`.</span></span> <span data-ttu-id="f8bab-144">Her `DataAdapter` biri bir veya daha `DataTable` fazla nesneyi doldurmak ve güncelleştirmeleri ilgili veri kaynağına geri çözmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-144">Each `DataAdapter` can be used to fill one or more `DataTable` objects and resolve updates back to the relevant data source.</span></span> <span data-ttu-id="f8bab-145">`DataRelation`ve `Constraint` nesneler `DataSet` yerel olarak eklenebilir, bu da farklı veri kaynaklarından gelen verileri ilişkilendirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8bab-145">`DataRelation` and `Constraint` objects can be added to the `DataSet` locally, which enables you to relate data from dissimilar data sources.</span></span> <span data-ttu-id="f8bab-146">Örneğin, bir `DataSet` Microsoft SQL Server veritabanından, OLE DB aracılığıyla açığa çıkarılan bir IBM DB2 veritabanından ve XML akışı yapan bir veri kaynağından veri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-146">For example, a `DataSet` can contain data from a Microsoft SQL Server database, an IBM DB2 database exposed through OLE DB, and a data source that streams XML.</span></span> <span data-ttu-id="f8bab-147">Bir veya `DataAdapter` daha fazla nesne her veri kaynağına iletişimi işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-147">One or more `DataAdapter` objects can handle communication to each data source.</span></span>  
  
### <a name="example"></a><span data-ttu-id="f8bab-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="f8bab-148">Example</span></span>  
 <span data-ttu-id="f8bab-149">Aşağıdaki kod örneği, Microsoft SQL Server'daki `Northwind` veritabanındaki müşterilerin listesini ve Microsoft `Northwind` Access 2000'de depolanan veritabanından gelen siparişlerin listesini doldurur.</span><span class="sxs-lookup"><span data-stu-id="f8bab-149">The following code example populates a list of customers from the `Northwind` database on Microsoft SQL Server, and a list of orders from the `Northwind` database stored in Microsoft Access 2000.</span></span> <span data-ttu-id="f8bab-150">Doldurulan tablolar bir `DataRelation`,, ve müşteri listesi ile ilgili daha sonra bu müşteri için siparişler ile görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-150">The filled tables are related with a `DataRelation`, and the list of customers is then displayed with the orders for that customer.</span></span> <span data-ttu-id="f8bab-151">Nesneler hakkında `DataRelation` daha fazla bilgi için [Navigating DataRelations](./dataset-datatable-dataview/navigating-datarelations.md) [bkz.](./dataset-datatable-dataview/adding-datarelations.md)</span><span class="sxs-lookup"><span data-stu-id="f8bab-151">For more information about `DataRelation` objects, see [Adding DataRelations](./dataset-datatable-dataview/adding-datarelations.md) and [Navigating DataRelations](./dataset-datatable-dataview/navigating-datarelations.md).</span></span>  
  
```vb  
' Assumes that customerConnection is a valid SqlConnection object.  
' Assumes that orderConnection is a valid OleDbConnection object.  
Dim custAdapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", customerConnection)  
  
Dim ordAdapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SELECT * FROM Orders", orderConnection)  
  
Dim customerOrders As DataSet = New DataSet()  
custAdapter.Fill(customerOrders, "Customers")  
ordAdapter.Fill(customerOrders, "Orders")  
  
Dim relation As DataRelation = _  
  customerOrders.Relations.Add("CustOrders", _  
  customerOrders.Tables("Customers").Columns("CustomerID"), _
  customerOrders.Tables("Orders").Columns("CustomerID"))  
  
Dim pRow, cRow As DataRow  
For Each pRow In customerOrders.Tables("Customers").Rows  
  Console.WriteLine(pRow("CustomerID").ToString())  
  
  For Each cRow In pRow.GetChildRows(relation)  
    Console.WriteLine(vbTab & cRow("OrderID").ToString())  
  Next  
Next  
```  
  
```csharp  
// Assumes that customerConnection is a valid SqlConnection object.  
// Assumes that orderConnection is a valid OleDbConnection object.  
SqlDataAdapter custAdapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", customerConnection);  
OleDbDataAdapter ordAdapter = new OleDbDataAdapter(  
  "SELECT * FROM Orders", orderConnection);  
  
DataSet customerOrders = new DataSet();  
  
custAdapter.Fill(customerOrders, "Customers");  
ordAdapter.Fill(customerOrders, "Orders");  
  
DataRelation relation = customerOrders.Relations.Add("CustOrders",  
  customerOrders.Tables["Customers"].Columns["CustomerID"],  
  customerOrders.Tables["Orders"].Columns["CustomerID"]);  
  
foreach (DataRow pRow in customerOrders.Tables["Customers"].Rows)  
{  
  Console.WriteLine(pRow["CustomerID"]);  
   foreach (DataRow cRow in pRow.GetChildRows(relation))  
    Console.WriteLine("\t" + cRow["OrderID"]);  
}  
```  
  
## <a name="sql-server-decimal-type"></a><span data-ttu-id="f8bab-152">SQL Server Ondalık Yazı</span><span class="sxs-lookup"><span data-stu-id="f8bab-152">SQL Server Decimal Type</span></span>  
 <span data-ttu-id="f8bab-153">Varsayılan olarak, `DataSet` .NET Framework veri türlerini kullanarak verileri depolar.</span><span class="sxs-lookup"><span data-stu-id="f8bab-153">By default, the `DataSet` stores data by using .NET Framework data types.</span></span> <span data-ttu-id="f8bab-154">Çoğu uygulama için bunlar veri kaynağı bilgilerinin uygun bir temsilini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8bab-154">For most applications, these provide a convenient representation of data source information.</span></span> <span data-ttu-id="f8bab-155">Ancak, veri kaynağındaki veri türü SQL Server ondalık veya sayısal veri türü olduğunda bu gösterim bir soruna neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-155">However, this representation may cause a problem when the data type in the data source is a SQL Server decimal or numeric data type.</span></span> <span data-ttu-id="f8bab-156">.NET Framework `decimal` veri türü en fazla 28 önemli basamak sağlarken, SQL Server `decimal` veri türü 38 önemli basamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8bab-156">The .NET Framework `decimal` data type allows a maximum of 28 significant digits, whereas the SQL Server `decimal` data type allows 38 significant digits.</span></span> <span data-ttu-id="f8bab-157">Bir `SqlDataAdapter` işlem sırasında `Fill` sql server `decimal` alanının kesinliği 28 karakterden büyük olduğunu belirlerse, `DataTable`geçerli satır .</span><span class="sxs-lookup"><span data-stu-id="f8bab-157">If the `SqlDataAdapter` determines during a `Fill` operation that the precision of a SQL Server `decimal` field is larger than 28 characters, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="f8bab-158">Bunun `FillError` yerine olay oluşur, bu da bir kesinlik kaybı oluşup oluşmayacağını belirlemenize ve uygun şekilde yanıt vermenize olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="f8bab-158">Instead the `FillError` event occurs, which enables you to determine whether a loss of precision will occur, and respond appropriately.</span></span> <span data-ttu-id="f8bab-159">`FillError` Olay hakkında daha fazla bilgi için [DataAdapter Olaylarını Işleme](handling-dataadapter-events.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="f8bab-159">For more information about the `FillError` event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span> <span data-ttu-id="f8bab-160">SQL Server `decimal` değerini almak için bir <xref:System.Data.SqlClient.SqlDataReader> nesne kullanabilir <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> ve yöntemi çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8bab-160">To get the SQL Server `decimal` value, you can also use a <xref:System.Data.SqlClient.SqlDataReader> object and call the <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> method.</span></span>  
  
 <span data-ttu-id="f8bab-161">ADO.NET 2.0 için <xref:System.Data.SqlTypes> geliştirilmiş destek `DataSet`tanıttı.</span><span class="sxs-lookup"><span data-stu-id="f8bab-161">ADO.NET 2.0 introduced enhanced support for <xref:System.Data.SqlTypes> in the `DataSet`.</span></span> <span data-ttu-id="f8bab-162">Daha fazla bilgi için [SqlTypes ve DataSet'e](./sql/sqltypes-and-the-dataset.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="f8bab-162">For more information, see [SqlTypes and the DataSet](./sql/sqltypes-and-the-dataset.md).</span></span>  
  
## <a name="ole-db-chapters"></a><span data-ttu-id="f8bab-163">OLE DB Bölümleri</span><span class="sxs-lookup"><span data-stu-id="f8bab-163">OLE DB Chapters</span></span>  
 <span data-ttu-id="f8bab-164">Hiyerarşik satır kümeleri veya bölümler (OLE DB türü `DBTYPE_HCHAPTER`, ADO türü) `adChapter`bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f8bab-164">Hierarchical rowsets, or chapters (OLE DB type `DBTYPE_HCHAPTER`, ADO type `adChapter`) can be used to fill the contents of a `DataSet`.</span></span> <span data-ttu-id="f8bab-165">İşlem <xref:System.Data.OleDb.OleDbDataAdapter> sırasında `Fill` bölümlere alınan bir sütunla `DataTable` karşılaştığında, bölümlere alınan sütun için bir sütun oluşturulur ve bu tablo bölümdeki sütun ve satırlarla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="f8bab-165">When the <xref:System.Data.OleDb.OleDbDataAdapter> encounters a chaptered column during a `Fill` operation, a `DataTable` is created for the chaptered column, and that table is filled with the columns and rows from the chapter.</span></span> <span data-ttu-id="f8bab-166">Bölümlenmiş sütun için oluşturulan tablo, hem ana tablo adı hem de "*ParentTableNameChapteredColumnName*" şeklindeki bölümlenmiş sütun adı kullanılarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f8bab-166">The table created for the chaptered column is named by using both the parent table name and the chaptered column name in the form "*ParentTableNameChapteredColumnName*".</span></span> <span data-ttu-id="f8bab-167">Bölümlenmiş sütunun `DataSet` adıyla eşleşen tablo zaten varsa, geçerli tablo bölüm verileriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="f8bab-167">If a table already exists in the `DataSet` that matches the name of the chaptered column, the current table is filled with the chapter data.</span></span> <span data-ttu-id="f8bab-168">Varolan bir tabloda bölümde bulunan sütunla eşleşen bir sütun yoksa, yeni bir sütun eklenir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-168">If there is no column in an existing table that matches a column found in the chapter, a new column is added.</span></span>  
  
 <span data-ttu-id="f8bab-169">Bölümlerdeki `DataSet` tablolar bölümlere aktarılmış sütunlarda verilerle doldurulmadan önce, üst ve alt tabloya bir tamsayı sütunu ekleyerek, üst sütunu otomatik artışa ayarlayarak ve her iki `DataRelation` tablodan eklenen sütunlar kullanılarak hiyerarşik satır kümesinin üst ve alt tabloları arasında bir ilişki oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f8bab-169">Before the tables in the `DataSet` are filled with the data in the chaptered columns, a relation is created between the parent and child tables of the hierarchical rowset by adding an integer column to both the parent and child table, setting the parent column to auto-increment, and creating a `DataRelation` using the added columns from both tables.</span></span> <span data-ttu-id="f8bab-170">Eklenen ilişki , "*ParentTableNameChapterColumnName*" şeklindeki ana tablo ve bölüm sütun adları kullanılarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f8bab-170">The added relation is named by using the parent table and chapter column names in the form "*ParentTableNameChapterColumnName*".</span></span>  
  
 <span data-ttu-id="f8bab-171">İlgili sütunun yalnızca `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="f8bab-171">Note that the related column only exists in the `DataSet`.</span></span> <span data-ttu-id="f8bab-172">Veri kaynağından sonraki dolgular, varolan satırlarla birleştirilen değişiklikler yerine tablolara yeni satırlar eklenmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-172">Subsequent fills from the data source can cause new rows to be added to the tables instead of changes being merged into existing rows.</span></span>  
  
 <span data-ttu-id="f8bab-173">Ayrıca, bir `DataAdapter.Fill` `DataTable`alır aşırı yük kullanırsanız, sadece bu tablo nun doldurulacağını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f8bab-173">Note also that, if you use the `DataAdapter.Fill` overload that takes a `DataTable`, only that table will be filled.</span></span> <span data-ttu-id="f8bab-174">Otomatik artışlı bir insa sütunu yine de tabloya eklenir, ancak alt tablo oluşturulmaz veya doldurulmaz ve ilişki oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="f8bab-174">An auto-incrementing integer column will still be added to the table, but no child table will be created or filled, and no relation will be created.</span></span>  
  
 <span data-ttu-id="f8bab-175">Aşağıdaki örnek, müşteri listesindeki her müşteri için bir sipariş bölümü sütunu oluşturmak için MSDataShape Sağlayıcı'yı kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8bab-175">The following example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span> <span data-ttu-id="f8bab-176">A `DataSet` daha sonra verilerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="f8bab-176">A `DataSet` is then filled with the data.</span></span>  
  
```vb  
Using connection As OleDbConnection = New OleDbConnection( _  
  "Provider=MSDataShape;Data Provider=SQLOLEDB;" & _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=northwind")  
  
Dim adapter As OleDbDataAdapter = New OleDbDataAdapter( _  
  "SHAPE {SELECT CustomerID, CompanyName FROM Customers} " & _  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " & _  
  "RELATE CustomerID TO CustomerID)", connection)  
  
Dim customers As DataSet = New DataSet()  
  
adapter.Fill(customers, "Customers")  
End Using  
```  
  
```csharp  
using (OleDbConnection connection = new OleDbConnection("Provider=MSDataShape;Data Provider=SQLOLEDB;" +  
  "Data Source=(local);Integrated Security=SSPI;Initial Catalog=northwind"))  
{  
OleDbDataAdapter adapter = new OleDbDataAdapter("SHAPE {SELECT CustomerID, CompanyName FROM Customers} " +  
  "APPEND ({SELECT CustomerID, OrderID FROM Orders} AS Orders " +  
  "RELATE CustomerID TO CustomerID)", connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");  
}  
```  
  
 <span data-ttu-id="f8bab-177">`Fill` İşlem tamamlandığında, iki `DataSet` tablo içerir: `Customers` `CustomersOrders`ve `CustomersOrders` , burada bölümlü sütun temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f8bab-177">When the `Fill` operation is complete, the `DataSet` contains two tables: `Customers` and `CustomersOrders`, where `CustomersOrders` represents the chaptered column.</span></span> <span data-ttu-id="f8bab-178">Tabloya `Orders` `Customers` adlandırılmış ek bir sütun eklenir ve `CustomersOrders` tabloya `CustomersOrders` adlandırılmış ek bir sütun eklenir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-178">An additional column named `Orders` is added to the `Customers` table, and an additional column named `CustomersOrders` is added to the `CustomersOrders` table.</span></span> <span data-ttu-id="f8bab-179">Tablodaki `Orders` `Customers` sütun otomatik artış ayarı.</span><span class="sxs-lookup"><span data-stu-id="f8bab-179">The `Orders` column in the `Customers` table is set to auto-increment.</span></span> <span data-ttu-id="f8bab-180">A `DataRelation` `CustomersOrders`, , üst tablo `Customers` olarak tablolara eklenen sütunlar kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f8bab-180">A `DataRelation`, `CustomersOrders`, is created by using the columns that were added to the tables with `Customers` as the parent table.</span></span> <span data-ttu-id="f8bab-181">Aşağıdaki tablolar bazı örnek sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8bab-181">The following tables show some sample results.</span></span>  
  
### <a name="tablename-customers"></a><span data-ttu-id="f8bab-182">Masa Adı: Müşteriler</span><span class="sxs-lookup"><span data-stu-id="f8bab-182">TableName: Customers</span></span>  
  
|<span data-ttu-id="f8bab-183">CustomerID</span><span class="sxs-lookup"><span data-stu-id="f8bab-183">CustomerID</span></span>|<span data-ttu-id="f8bab-184">CompanyName</span><span class="sxs-lookup"><span data-stu-id="f8bab-184">CompanyName</span></span>|<span data-ttu-id="f8bab-185">Siparişler</span><span class="sxs-lookup"><span data-stu-id="f8bab-185">Orders</span></span>|  
|----------------|-----------------|------------|  
|<span data-ttu-id="f8bab-186">Alfkı</span><span class="sxs-lookup"><span data-stu-id="f8bab-186">ALFKI</span></span>|<span data-ttu-id="f8bab-187">Alfreds Futterkiste</span><span class="sxs-lookup"><span data-stu-id="f8bab-187">Alfreds Futterkiste</span></span>|<span data-ttu-id="f8bab-188">0</span><span class="sxs-lookup"><span data-stu-id="f8bab-188">0</span></span>|  
|<span data-ttu-id="f8bab-189">ANATR</span><span class="sxs-lookup"><span data-stu-id="f8bab-189">ANATR</span></span>|<span data-ttu-id="f8bab-190">Ana Trujillo Emparedados y helados</span><span class="sxs-lookup"><span data-stu-id="f8bab-190">Ana Trujillo Emparedados y helados</span></span>|<span data-ttu-id="f8bab-191">1</span><span class="sxs-lookup"><span data-stu-id="f8bab-191">1</span></span>|  
  
### <a name="tablename-customersorders"></a><span data-ttu-id="f8bab-192">Tablo Adı: Müşteri Siparişleri</span><span class="sxs-lookup"><span data-stu-id="f8bab-192">TableName: CustomersOrders</span></span>  
  
|<span data-ttu-id="f8bab-193">CustomerID</span><span class="sxs-lookup"><span data-stu-id="f8bab-193">CustomerID</span></span>|<span data-ttu-id="f8bab-194">OrderID</span><span class="sxs-lookup"><span data-stu-id="f8bab-194">OrderID</span></span>|<span data-ttu-id="f8bab-195">Müşteri Siparişleri</span><span class="sxs-lookup"><span data-stu-id="f8bab-195">CustomersOrders</span></span>|  
|----------------|-------------|---------------------|  
|<span data-ttu-id="f8bab-196">Alfkı</span><span class="sxs-lookup"><span data-stu-id="f8bab-196">ALFKI</span></span>|<span data-ttu-id="f8bab-197">10643</span><span class="sxs-lookup"><span data-stu-id="f8bab-197">10643</span></span>|<span data-ttu-id="f8bab-198">0</span><span class="sxs-lookup"><span data-stu-id="f8bab-198">0</span></span>|  
|<span data-ttu-id="f8bab-199">Alfkı</span><span class="sxs-lookup"><span data-stu-id="f8bab-199">ALFKI</span></span>|<span data-ttu-id="f8bab-200">10692</span><span class="sxs-lookup"><span data-stu-id="f8bab-200">10692</span></span>|<span data-ttu-id="f8bab-201">0</span><span class="sxs-lookup"><span data-stu-id="f8bab-201">0</span></span>|  
|<span data-ttu-id="f8bab-202">ANATR</span><span class="sxs-lookup"><span data-stu-id="f8bab-202">ANATR</span></span>|<span data-ttu-id="f8bab-203">10308</span><span class="sxs-lookup"><span data-stu-id="f8bab-203">10308</span></span>|<span data-ttu-id="f8bab-204">1</span><span class="sxs-lookup"><span data-stu-id="f8bab-204">1</span></span>|  
|<span data-ttu-id="f8bab-205">ANATR</span><span class="sxs-lookup"><span data-stu-id="f8bab-205">ANATR</span></span>|<span data-ttu-id="f8bab-206">10625</span><span class="sxs-lookup"><span data-stu-id="f8bab-206">10625</span></span>|<span data-ttu-id="f8bab-207">1</span><span class="sxs-lookup"><span data-stu-id="f8bab-207">1</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f8bab-208">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8bab-208">See also</span></span>

- [<span data-ttu-id="f8bab-209">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="f8bab-209">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="f8bab-210">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="f8bab-210">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="f8bab-211">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="f8bab-211">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="f8bab-212">Birden Çok Etkin Sonuç Kümesi (MARS)</span><span class="sxs-lookup"><span data-stu-id="f8bab-212">Multiple Active Result Sets (MARS)</span></span>](./sql/multiple-active-result-sets-mars.md)
- [<span data-ttu-id="f8bab-213">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f8bab-213">ADO.NET Overview</span></span>](ado-net-overview.md)
