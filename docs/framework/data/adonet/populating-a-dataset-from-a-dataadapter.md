---
title: DataAdapter’dan bir DataSet Doldurma
description: Veri kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan ADO.NET içindeki DataAdapter nesnesinden bir veri kümesini doldurmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: ac84af884238b166266d4206802878c1e21169fd
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91177416"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a><span data-ttu-id="ef538-103">DataAdapter’dan bir DataSet Doldurma</span><span class="sxs-lookup"><span data-stu-id="ef538-103">Populating a DataSet from a DataAdapter</span></span>

<span data-ttu-id="ef538-104">ADO.NET, <xref:System.Data.DataSet> veri kaynağından bağımsız tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="ef538-104">The ADO.NET <xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model independent of the data source.</span></span> <span data-ttu-id="ef538-105">, Tablolar `DataSet` arasındaki tabloları, kısıtlamaları ve ilişkileri içeren tüm veri kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ef538-105">The `DataSet` represents a complete set of data that includes tables, constraints, and relationships among the tables.</span></span> <span data-ttu-id="ef538-106">, `DataSet` Veri kaynağından bağımsız olduğundan, bir `DataSet` uygulamaya yerel veri ve birden çok veri kaynağından veri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ef538-106">Because the `DataSet` is independent of the data source, a `DataSet` can include data local to the application, and data from multiple data sources.</span></span> <span data-ttu-id="ef538-107">Mevcut veri kaynaklarıyla etkileşim aracılığıyla denetlenir `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="ef538-107">Interaction with existing data sources is controlled through the `DataAdapter`.</span></span>  
  
 <span data-ttu-id="ef538-108">`SelectCommand`Öğesinin özelliği, `DataAdapter` `Command` veri kaynağından veri alan bir nesnedir.</span><span class="sxs-lookup"><span data-stu-id="ef538-108">The `SelectCommand` property of the `DataAdapter` is a `Command` object that retrieves data from the data source.</span></span> <span data-ttu-id="ef538-109">, `InsertCommand` `UpdateCommand` Ve özellikleri, `DeleteCommand` `DataAdapter` `Command` içindeki verilerde yapılan değişikliklere göre veri kaynağındaki verilerle ilgili güncelleştirmeleri yöneten nesnelerdir `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="ef538-109">The `InsertCommand`, `UpdateCommand`, and `DeleteCommand` properties of the `DataAdapter` are `Command` objects that manage updates to the data in the data source according to modifications made to the data in the `DataSet`.</span></span> <span data-ttu-id="ef538-110">Bu özellikler, [veri kaynaklarını DataAdapter Ile güncelleştirme konusunda](updating-data-sources-with-dataadapters.md)daha ayrıntılı olarak ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="ef538-110">These properties are covered in more detail in [Updating Data Sources with DataAdapters](updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="ef538-111">Yöntemi, öğesinin `Fill` `DataAdapter` sonuçlarıyla birlikte doldurmak için kullanılır `DataSet` `SelectCommand` `DataAdapter` .</span><span class="sxs-lookup"><span data-stu-id="ef538-111">The `Fill` method of the `DataAdapter` is used to populate a `DataSet` with the results of the `SelectCommand` of the `DataAdapter`.</span></span> <span data-ttu-id="ef538-112">`Fill``DataSet`, ' nin doldurulduğu bağımsız değişkenlerini, bir `DataTable` nesnesini veya ' `DataTable` den döndürülen satırlarla doldurulacak olan adını alır `SelectCommand` .</span><span class="sxs-lookup"><span data-stu-id="ef538-112">`Fill` takes as its arguments a `DataSet` to be populated, and a `DataTable` object, or the name of the `DataTable` to be filled with the rows returned from the `SelectCommand`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef538-113">`DataAdapter`Bir tablonun tümünü almak için kullanılması, özellikle tabloda çok sayıda satır olması durumunda zaman alır.</span><span class="sxs-lookup"><span data-stu-id="ef538-113">Using the `DataAdapter` to retrieve all of a table takes time, especially if there are many rows in the table.</span></span> <span data-ttu-id="ef538-114">Bunun nedeni, veritabanına erişmek, verileri bulmak ve işlemek ve sonra verilerin istemciye aktarılması zaman alır.</span><span class="sxs-lookup"><span data-stu-id="ef538-114">This is because accessing the database, locating and processing the data, and then transferring the data to the client is time-consuming.</span></span> <span data-ttu-id="ef538-115">Tüm tablosunun istemciye çekmeleri, sunucudaki tüm satırları da kilitler.</span><span class="sxs-lookup"><span data-stu-id="ef538-115">Pulling all of the table to the client also locks all of the rows on the server.</span></span> <span data-ttu-id="ef538-116">Performansı artırmak için, `WHERE` yan tümcesini kullanarak istemciye döndürülen satır sayısını büyük ölçüde azaltabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef538-116">To improve performance, you can use the `WHERE` clause to greatly reduce the number of rows returned to the client.</span></span> <span data-ttu-id="ef538-117">Ayrıca, yalnızca deyimindeki gerekli sütunları açıkça listeleyerek istemciye döndürülen veri miktarını azaltabilirsiniz `SELECT` .</span><span class="sxs-lookup"><span data-stu-id="ef538-117">You can also reduce the amount of data returned to the client by only explicitly listing required columns in the `SELECT` statement.</span></span> <span data-ttu-id="ef538-118">Başka bir iyi geçici çözüm de satırları toplu olarak (örneğin, bir kerede birkaç yüz satır) almak ve yalnızca, geçerli toplu işlemle istemci tamamlandığında sonraki toplu işi almak içindir.</span><span class="sxs-lookup"><span data-stu-id="ef538-118">Another good workaround is to retrieve the rows in batches (such as several hundred rows at a time) and only retrieve the next batch when the client is finished with the current batch.</span></span>  
  
 <span data-ttu-id="ef538-119">Yöntemi, içindeki `Fill` `DataReader` tabloları oluşturmak için kullanılan sütun adlarını ve türlerini `DataSet` ve içindeki tabloların satırlarının doldurulmasıyla ilgili verileri döndürmek için nesneyi örtük olarak kullanır `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="ef538-119">The `Fill` method uses the `DataReader` object implicitly to return the column names and types that are used to create the tables in the `DataSet`, and the data to populate the rows of the tables in the `DataSet`.</span></span> <span data-ttu-id="ef538-120">Tablolar ve sütunlar yalnızca henüz yoksa oluşturulur; Aksi halde `Fill` mevcut `DataSet` Şemayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef538-120">Tables and columns are only created if they do not already exist; otherwise `Fill` uses the existing `DataSet` schema.</span></span> <span data-ttu-id="ef538-121">Sütun türleri, [ADO.net Içindeki veri türü eşlemelerinde](data-type-mappings-in-ado-net.md)bulunan tablolara göre .NET Framework türleri olarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ef538-121">Column types are created as .NET Framework types according to the tables in [Data Type Mappings in ADO.NET](data-type-mappings-in-ado-net.md).</span></span> <span data-ttu-id="ef538-122">Birincil anahtarlar veri kaynağında yoksa oluşturulmaz `DataAdapter` **.**`MissingSchemaAction`</span><span class="sxs-lookup"><span data-stu-id="ef538-122">Primary keys are not created unless they exist in the data source and `DataAdapter`**.**`MissingSchemaAction`</span></span> <span data-ttu-id="ef538-123">, olarak ayarlanır `MissingSchemaAction` **.** `AddWithKey` ..</span><span class="sxs-lookup"><span data-stu-id="ef538-123">is set to `MissingSchemaAction`**.**`AddWithKey`.</span></span> <span data-ttu-id="ef538-124">`Fill`Bir tablonun birincil anahtarının mevcut olduğunu belirlerse, `DataSet` birincil anahtar sütun değerlerinin veri kaynağından döndürülen satırla eşleştiği satırlar için veri kaynağındaki verilerle veri üzerine yazar.</span><span class="sxs-lookup"><span data-stu-id="ef538-124">If `Fill` finds that a primary key exists for a table, it will overwrite data in the `DataSet` with data from the data source for rows where the primary key column values match those of the row returned from the data source.</span></span> <span data-ttu-id="ef538-125">Birincil anahtar bulunamazsa, veriler içindeki tablolara eklenir `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="ef538-125">If no primary key is found, the data is appended to the tables in the `DataSet`.</span></span> <span data-ttu-id="ef538-126">`Fill` ' i doldurduğunuzda mevcut olabilecek eşlemeleri kullanır `DataSet` (bkz. [DataAdapter DataTable ve DataColumn Mappings](dataadapter-datatable-and-datacolumn-mappings.md)).</span><span class="sxs-lookup"><span data-stu-id="ef538-126">`Fill` uses any mappings that may exist when you populate the `DataSet` (see [DataAdapter DataTable and DataColumn Mappings](dataadapter-datatable-and-datacolumn-mappings.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef538-127">, `SelectCommand` BIR Dış birleştirmenin sonuçlarını döndürürse, `DataAdapter` `PrimaryKey` sonuç için bir değer yapmaz `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="ef538-127">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` does not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="ef538-128">`PrimaryKey`Yinelenen satırların doğru bir şekilde çözümlendiğini doğrulamak için kendinizi tanımlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef538-128">You must define the `PrimaryKey` yourself to make sure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="ef538-129">Daha fazla bilgi için bkz. [birincil anahtarları tanımlama](./dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="ef538-129">For more information, see [Defining Primary Keys](./dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="ef538-130">Aşağıdaki kod örneği, bir ' ın, <xref:System.Data.SqlClient.SqlDataAdapter> Microsoft SQL Server veritabanına kullanan bir örneğini oluşturur ve bir içinde bir <xref:System.Data.SqlClient.SqlConnection> `Northwind` <xref:System.Data.DataTable> `DataSet` ile birlikte, müşteriler listesiyle doldurur.</span><span class="sxs-lookup"><span data-stu-id="ef538-130">The following code example creates an instance of a <xref:System.Data.SqlClient.SqlDataAdapter> that uses a <xref:System.Data.SqlClient.SqlConnection> to the Microsoft SQL Server `Northwind` database and populates a <xref:System.Data.DataTable> in a `DataSet` with the list of customers.</span></span> <span data-ttu-id="ef538-131">Oluşturucuya geçirilen SQL deyimleri ve <xref:System.Data.SqlClient.SqlConnection> bağımsız değişkenler <xref:System.Data.SqlClient.SqlDataAdapter> <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> , öğesinin özelliğini oluşturmak için kullanılır <xref:System.Data.SqlClient.SqlDataAdapter> .</span><span class="sxs-lookup"><span data-stu-id="ef538-131">The SQL statement and <xref:System.Data.SqlClient.SqlConnection> arguments passed to the <xref:System.Data.SqlClient.SqlDataAdapter> constructor are used to create the <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> property of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef538-132">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef538-132">Example</span></span>  
  
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
> <span data-ttu-id="ef538-133">Bu örnekte gösterilen kod açık bir şekilde açılmaz ve kapatmaz `Connection` .</span><span class="sxs-lookup"><span data-stu-id="ef538-133">The code shown in this example does not explicitly open and close the `Connection`.</span></span> <span data-ttu-id="ef538-134">`Fill`Yöntemi, `Connection` `DataAdapter` bağlantının zaten açık olmadığını bulursa kullandığı öğesini örtülü olarak açar.</span><span class="sxs-lookup"><span data-stu-id="ef538-134">The `Fill` method implicitly opens the `Connection` that the `DataAdapter` is using if it finds that the connection is not already open.</span></span> <span data-ttu-id="ef538-135">`Fill`Bağlantı açıldıysa, tamamlandığında da bağlantıyı kapatır `Fill` .</span><span class="sxs-lookup"><span data-stu-id="ef538-135">If `Fill` opened the connection, it also closes the connection when `Fill` is finished.</span></span> <span data-ttu-id="ef538-136">Bu, veya gibi tek bir işlemle uğraşdığınızda kodunuzun basitleşmesini sağlayabilir `Fill` `Update` .</span><span class="sxs-lookup"><span data-stu-id="ef538-136">This can simplify your code when you deal with a single operation such as a `Fill` or an `Update`.</span></span> <span data-ttu-id="ef538-137">Ancak, açık bağlantı gerektiren birden çok işlem gerçekleştiriyorsanız uygulamanızın performansını, `Open` `Connection` veri kaynağına karşı işlemleri gerçekleştirerek ve sonra metodunu çağırarak, kendi metodunu açıkça çağırarak geliştirebilirsiniz `Close` `Connection` .</span><span class="sxs-lookup"><span data-stu-id="ef538-137">However, if you are performing multiple operations that require an open connection, you can improve the performance of your application by explicitly calling the `Open` method of the `Connection`, performing the operations against the data source, and then calling the `Close` method of the `Connection`.</span></span> <span data-ttu-id="ef538-138">Kaynakları diğer istemci uygulamalar tarafından kullanılmak üzere serbest bırakmak için veri kaynağına yönelik bağlantıları daha kısa sürede açık tutmaya çalışın.</span><span class="sxs-lookup"><span data-stu-id="ef538-138">You should try to keep connections to the data source open as briefly as possible to free resources for use by other client applications.</span></span>  
  
## <a name="multiple-result-sets"></a><span data-ttu-id="ef538-139">Birden Fazla Sonuç Kümesi</span><span class="sxs-lookup"><span data-stu-id="ef538-139">Multiple Result Sets</span></span>  

 <span data-ttu-id="ef538-140">`DataAdapter`Birden çok sonuç kümesiyle karşılaşırsa, içinde birden çok tablo oluşturur `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="ef538-140">If the `DataAdapter` encounters multiple result sets, it creates multiple tables in the `DataSet`.</span></span> <span data-ttu-id="ef538-141">Tablolara, TABLE0 için "Table" ile başlayarak, tablo*N*' nin artımlı varsayılan adı verilir.</span><span class="sxs-lookup"><span data-stu-id="ef538-141">The tables are given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span> <span data-ttu-id="ef538-142">Bir tablo adı yöntemine bir bağımsız değişken olarak geçirilirse `Fill` , tablolara TableName0 için "TableName" ile başlayarak TableName*N*artımlı varsayılan adı verilir.</span><span class="sxs-lookup"><span data-stu-id="ef538-142">If a table name is passed as an argument to the `Fill` method, the tables are given an incremental default name of TableName*N*, starting with "TableName" for TableName0.</span></span>  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a><span data-ttu-id="ef538-143">Birden çok DataAdapter nesnesinden veri kümesini doldurma</span><span class="sxs-lookup"><span data-stu-id="ef538-143">Populating a DataSet from Multiple DataAdapters</span></span>  

 <span data-ttu-id="ef538-144">Herhangi bir sayıda `DataAdapter` nesne, ile kullanılabilir `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="ef538-144">Any number of `DataAdapter` objects can be used with a `DataSet`.</span></span> <span data-ttu-id="ef538-145">Her biri `DataAdapter` , bir veya daha fazla nesneyi doldurup `DataTable` güncelleştirmeleri ilgili veri kaynağına geri çözümlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef538-145">Each `DataAdapter` can be used to fill one or more `DataTable` objects and resolve updates back to the relevant data source.</span></span> <span data-ttu-id="ef538-146">`DataRelation` ve `Constraint` nesneler yerel olarak eklenebilir `DataSet` , bu da benzer veri kaynaklarından verileri ilişkilendirmenize olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef538-146">`DataRelation` and `Constraint` objects can be added to the `DataSet` locally, which enables you to relate data from dissimilar data sources.</span></span> <span data-ttu-id="ef538-147">Örneğin, bir `DataSet` Microsoft SQL Server veritabanından veri, OLE DB üzerinden sunulan BIR IBM DB2 veritabanı ve XML akışı yapan bir veri kaynağı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ef538-147">For example, a `DataSet` can contain data from a Microsoft SQL Server database, an IBM DB2 database exposed through OLE DB, and a data source that streams XML.</span></span> <span data-ttu-id="ef538-148">Bir veya daha fazla `DataAdapter` nesne, her bir veri kaynağıyla iletişimi işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ef538-148">One or more `DataAdapter` objects can handle communication to each data source.</span></span>  
  
### <a name="example"></a><span data-ttu-id="ef538-149">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef538-149">Example</span></span>  

 <span data-ttu-id="ef538-150">Aşağıdaki kod örneği, Microsoft SQL Server veritabanından bir müşteri listesini `Northwind` ve `Northwind` Microsoft Access 2000 ' de depolanan veritabanından alınan siparişlerin listesini doldurur.</span><span class="sxs-lookup"><span data-stu-id="ef538-150">The following code example populates a list of customers from the `Northwind` database on Microsoft SQL Server, and a list of orders from the `Northwind` database stored in Microsoft Access 2000.</span></span> <span data-ttu-id="ef538-151">Doldurulmuş tablolar bir ile ilgilidir `DataRelation` ve müşteriler listesi bu müşterinin siparişleriyle birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="ef538-151">The filled tables are related with a `DataRelation`, and the list of customers is then displayed with the orders for that customer.</span></span> <span data-ttu-id="ef538-152">Nesneler hakkında daha fazla bilgi için `DataRelation` bkz. [DataRelation 'ı ekleme](./dataset-datatable-dataview/adding-datarelations.md) ve DataRelation 'ı [gezinme](./dataset-datatable-dataview/navigating-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="ef538-152">For more information about `DataRelation` objects, see [Adding DataRelations](./dataset-datatable-dataview/adding-datarelations.md) and [Navigating DataRelations](./dataset-datatable-dataview/navigating-datarelations.md).</span></span>  
  
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
  
## <a name="sql-server-decimal-type"></a><span data-ttu-id="ef538-153">SQL Server ondalık türü</span><span class="sxs-lookup"><span data-stu-id="ef538-153">SQL Server Decimal Type</span></span>  

 <span data-ttu-id="ef538-154">Varsayılan olarak, `DataSet` .NET Framework veri türlerini kullanarak verileri depolar.</span><span class="sxs-lookup"><span data-stu-id="ef538-154">By default, the `DataSet` stores data by using .NET Framework data types.</span></span> <span data-ttu-id="ef538-155">Çoğu uygulama için, veri kaynağı bilgilerinin kullanışlı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef538-155">For most applications, these provide a convenient representation of data source information.</span></span> <span data-ttu-id="ef538-156">Ancak, veri kaynağındaki veri türü SQL Server Decimal veya numeric veri türü olduğunda bu gösterim soruna neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef538-156">However, this representation may cause a problem when the data type in the data source is a SQL Server decimal or numeric data type.</span></span> <span data-ttu-id="ef538-157">.NET Framework `decimal` veri türü en fazla 28 önemli basamağa izin veriyor, ancak SQL Server `decimal` veri türü 38 önemli basamağa izin veriyor.</span><span class="sxs-lookup"><span data-stu-id="ef538-157">The .NET Framework `decimal` data type allows a maximum of 28 significant digits, whereas the SQL Server `decimal` data type allows 38 significant digits.</span></span> <span data-ttu-id="ef538-158">`SqlDataAdapter`Bir işlem sırasında, `Fill` bir SQL Server alanının duyarlığının `decimal` 28 karakterden daha büyük olduğunu belirlerse, geçerli satır öğesine eklenmez `DataTable` .</span><span class="sxs-lookup"><span data-stu-id="ef538-158">If the `SqlDataAdapter` determines during a `Fill` operation that the precision of a SQL Server `decimal` field is larger than 28 characters, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="ef538-159">Bunun yerine, `FillError` bir duyarlık kaybı olup olmadığını ve uygun şekilde yanıt verip vermeyeceğinizi belirlemenizi sağlayan olay oluşur.</span><span class="sxs-lookup"><span data-stu-id="ef538-159">Instead the `FillError` event occurs, which enables you to determine whether a loss of precision will occur, and respond appropriately.</span></span> <span data-ttu-id="ef538-160">Olay hakkında daha fazla bilgi için `FillError` bkz. [DataAdapter olaylarını işleme](handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="ef538-160">For more information about the `FillError` event, see [Handling DataAdapter Events](handling-dataadapter-events.md).</span></span> <span data-ttu-id="ef538-161">SQL Server değerini almak için `decimal` , bir nesnesi de kullanabilir <xref:System.Data.SqlClient.SqlDataReader> ve <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> yöntemini çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef538-161">To get the SQL Server `decimal` value, you can also use a <xref:System.Data.SqlClient.SqlDataReader> object and call the <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> method.</span></span>  
  
 <span data-ttu-id="ef538-162">ADO.NET 2,0, içinde için geliştirilmiş destek getirmiştir <xref:System.Data.SqlTypes> `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="ef538-162">ADO.NET 2.0 introduced enhanced support for <xref:System.Data.SqlTypes> in the `DataSet`.</span></span> <span data-ttu-id="ef538-163">Daha fazla bilgi için bkz. [SqlTypes ve DataSet](./sql/sqltypes-and-the-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="ef538-163">For more information, see [SqlTypes and the DataSet](./sql/sqltypes-and-the-dataset.md).</span></span>  
  
## <a name="ole-db-chapters"></a><span data-ttu-id="ef538-164">OLE DB bölümler</span><span class="sxs-lookup"><span data-stu-id="ef538-164">OLE DB Chapters</span></span>  

 <span data-ttu-id="ef538-165">Hiyerarşik satır kümeleri veya bölümler (OLE DB türü `DBTYPE_HCHAPTER` , ADO türü `adChapter` ), içeriğini dolduracak şekilde kullanılabilir `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="ef538-165">Hierarchical rowsets, or chapters (OLE DB type `DBTYPE_HCHAPTER`, ADO type `adChapter`) can be used to fill the contents of a `DataSet`.</span></span> <span data-ttu-id="ef538-166"><xref:System.Data.OleDb.OleDbDataAdapter>Bir işlem sırasında bir bölümlenebilir sütun ile karşılaştığında, `Fill` `DataTable` bölümlenebilir sütun için bir oluşturulur ve bu tablo, bölümün sütunları ve satırlarıyla doldurulur.</span><span class="sxs-lookup"><span data-stu-id="ef538-166">When the <xref:System.Data.OleDb.OleDbDataAdapter> encounters a chaptered column during a `Fill` operation, a `DataTable` is created for the chaptered column, and that table is filled with the columns and rows from the chapter.</span></span> <span data-ttu-id="ef538-167">Bölümlendirilen sütun için oluşturulan tablo, hem üst tablo adı hem de "*Parenttablenamebölüteredcolumnname*" biçiminde bölümlendirilen sütun adı kullanılarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ef538-167">The table created for the chaptered column is named by using both the parent table name and the chaptered column name in the form "*ParentTableNameChapteredColumnName*".</span></span> <span data-ttu-id="ef538-168">İçinde, `DataSet` bölümlenebilir sütunun adıyla eşleşen bir tablo zaten varsa, geçerli tablo bölüm verileriyle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="ef538-168">If a table already exists in the `DataSet` that matches the name of the chaptered column, the current table is filled with the chapter data.</span></span> <span data-ttu-id="ef538-169">Varolan bir tabloda, bölümde bulunan bir sütunla eşleşen bir sütun yoksa, yeni bir sütun eklenir.</span><span class="sxs-lookup"><span data-stu-id="ef538-169">If there is no column in an existing table that matches a column found in the chapter, a new column is added.</span></span>  
  
 <span data-ttu-id="ef538-170">İçindeki tablolar, `DataSet` bölümlenebilir sütunlardaki verilerle doldurulmadan önce hem üst hem de alt tabloya bir tamsayı sütunu ekleyerek hiyerarşik satır kümesinin üst ve alt tabloları arasında bir ilişki oluşturulur, üst sütunu otomatik artış olarak ayarlar ve `DataRelation` her iki tablodan de eklenen sütunları kullanarak oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ef538-170">Before the tables in the `DataSet` are filled with the data in the chaptered columns, a relation is created between the parent and child tables of the hierarchical rowset by adding an integer column to both the parent and child table, setting the parent column to auto-increment, and creating a `DataRelation` using the added columns from both tables.</span></span> <span data-ttu-id="ef538-171">Eklenen ilişki, "*Parenttablenamecolumntercolumnname*" biçiminde üst tablo ve bölüm sütun adları kullanılarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ef538-171">The added relation is named by using the parent table and chapter column names in the form "*ParentTableNameChapterColumnName*".</span></span>  
  
 <span data-ttu-id="ef538-172">İlgili sütunun içinde yalnızca bulunduğunu unutmayın `DataSet` .</span><span class="sxs-lookup"><span data-stu-id="ef538-172">Note that the related column only exists in the `DataSet`.</span></span> <span data-ttu-id="ef538-173">Veri kaynağından sonraki dolgular, varolan satırlarla birleştirilecek değişiklikler yerine tablolara yeni satırların eklenmesine neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef538-173">Subsequent fills from the data source can cause new rows to be added to the tables instead of changes being merged into existing rows.</span></span>  
  
 <span data-ttu-id="ef538-174">Ayrıca, öğesini `DataAdapter.Fill` alan aşırı yüklemeyi kullanırsanız `DataTable` , yalnızca bu tablo doldurulacak şekilde aklınızda kalır.</span><span class="sxs-lookup"><span data-stu-id="ef538-174">Note also that, if you use the `DataAdapter.Fill` overload that takes a `DataTable`, only that table will be filled.</span></span> <span data-ttu-id="ef538-175">Tabloya otomatik artan tamsayı sütunu yine de eklenecek, ancak hiçbir alt tablo oluşturulmayacak ya da doldurulmayacak ve hiçbir ilişki oluşturulmayacak.</span><span class="sxs-lookup"><span data-stu-id="ef538-175">An auto-incrementing integer column will still be added to the table, but no child table will be created or filled, and no relation will be created.</span></span>  
  
 <span data-ttu-id="ef538-176">Aşağıdaki örnek, bir müşteriler listesindeki her müşteri için siparişlerin bir bölüm sütununu oluşturmak üzere MSDataShape sağlayıcısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef538-176">The following example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span> <span data-ttu-id="ef538-177">`DataSet`Daha sonra veriler ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="ef538-177">A `DataSet` is then filled with the data.</span></span>  
  
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
  
 <span data-ttu-id="ef538-178">`Fill`İşlem tamamlandığında, `DataSet` iki tablo içerir: `Customers` ve `CustomersOrders` , burada `CustomersOrders` bölümleyen sütunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ef538-178">When the `Fill` operation is complete, the `DataSet` contains two tables: `Customers` and `CustomersOrders`, where `CustomersOrders` represents the chaptered column.</span></span> <span data-ttu-id="ef538-179">Tabloya adlı ek bir sütun `Orders` eklenir `Customers` ve tabloya adlı ek bir sütun `CustomersOrders` eklenir `CustomersOrders` .</span><span class="sxs-lookup"><span data-stu-id="ef538-179">An additional column named `Orders` is added to the `Customers` table, and an additional column named `CustomersOrders` is added to the `CustomersOrders` table.</span></span> <span data-ttu-id="ef538-180">`Orders` `Customers` Tablodaki sütun otomatik artış olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ef538-180">The `Orders` column in the `Customers` table is set to auto-increment.</span></span> <span data-ttu-id="ef538-181">`DataRelation`,, `CustomersOrders` `Customers` Üst tablo olarak bulunan tablolara eklenen sütunlar kullanılarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ef538-181">A `DataRelation`, `CustomersOrders`, is created by using the columns that were added to the tables with `Customers` as the parent table.</span></span> <span data-ttu-id="ef538-182">Aşağıdaki tablolarda bazı örnek sonuçlar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ef538-182">The following tables show some sample results.</span></span>  
  
### <a name="tablename-customers"></a><span data-ttu-id="ef538-183">TabloAdı: müşteriler</span><span class="sxs-lookup"><span data-stu-id="ef538-183">TableName: Customers</span></span>  
  
|<span data-ttu-id="ef538-184">CustomerID</span><span class="sxs-lookup"><span data-stu-id="ef538-184">CustomerID</span></span>|<span data-ttu-id="ef538-185">CompanyName</span><span class="sxs-lookup"><span data-stu-id="ef538-185">CompanyName</span></span>|<span data-ttu-id="ef538-186">Siparişler</span><span class="sxs-lookup"><span data-stu-id="ef538-186">Orders</span></span>|  
|----------------|-----------------|------------|  
|<span data-ttu-id="ef538-187">ALFKI</span><span class="sxs-lookup"><span data-stu-id="ef538-187">ALFKI</span></span>|<span data-ttu-id="ef538-188">Alfreds Futterkte</span><span class="sxs-lookup"><span data-stu-id="ef538-188">Alfreds Futterkiste</span></span>|<span data-ttu-id="ef538-189">0</span><span class="sxs-lookup"><span data-stu-id="ef538-189">0</span></span>|  
|<span data-ttu-id="ef538-190">ANATR</span><span class="sxs-lookup"><span data-stu-id="ef538-190">ANATR</span></span>|<span data-ttu-id="ef538-191">Ana Trujillo Emparedaddos y Helados</span><span class="sxs-lookup"><span data-stu-id="ef538-191">Ana Trujillo Emparedados y helados</span></span>|<span data-ttu-id="ef538-192">1</span><span class="sxs-lookup"><span data-stu-id="ef538-192">1</span></span>|  
  
### <a name="tablename-customersorders"></a><span data-ttu-id="ef538-193">TableName: CustomersOrders</span><span class="sxs-lookup"><span data-stu-id="ef538-193">TableName: CustomersOrders</span></span>  
  
|<span data-ttu-id="ef538-194">CustomerID</span><span class="sxs-lookup"><span data-stu-id="ef538-194">CustomerID</span></span>|<span data-ttu-id="ef538-195">OrderID</span><span class="sxs-lookup"><span data-stu-id="ef538-195">OrderID</span></span>|<span data-ttu-id="ef538-196">Müşteri Sorleyicileri</span><span class="sxs-lookup"><span data-stu-id="ef538-196">CustomersOrders</span></span>|  
|----------------|-------------|---------------------|  
|<span data-ttu-id="ef538-197">ALFKI</span><span class="sxs-lookup"><span data-stu-id="ef538-197">ALFKI</span></span>|<span data-ttu-id="ef538-198">10643</span><span class="sxs-lookup"><span data-stu-id="ef538-198">10643</span></span>|<span data-ttu-id="ef538-199">0</span><span class="sxs-lookup"><span data-stu-id="ef538-199">0</span></span>|  
|<span data-ttu-id="ef538-200">ALFKI</span><span class="sxs-lookup"><span data-stu-id="ef538-200">ALFKI</span></span>|<span data-ttu-id="ef538-201">10692</span><span class="sxs-lookup"><span data-stu-id="ef538-201">10692</span></span>|<span data-ttu-id="ef538-202">0</span><span class="sxs-lookup"><span data-stu-id="ef538-202">0</span></span>|  
|<span data-ttu-id="ef538-203">ANATR</span><span class="sxs-lookup"><span data-stu-id="ef538-203">ANATR</span></span>|<span data-ttu-id="ef538-204">10308</span><span class="sxs-lookup"><span data-stu-id="ef538-204">10308</span></span>|<span data-ttu-id="ef538-205">1</span><span class="sxs-lookup"><span data-stu-id="ef538-205">1</span></span>|  
|<span data-ttu-id="ef538-206">ANATR</span><span class="sxs-lookup"><span data-stu-id="ef538-206">ANATR</span></span>|<span data-ttu-id="ef538-207">10625</span><span class="sxs-lookup"><span data-stu-id="ef538-207">10625</span></span>|<span data-ttu-id="ef538-208">1</span><span class="sxs-lookup"><span data-stu-id="ef538-208">1</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ef538-209">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef538-209">See also</span></span>

- [<span data-ttu-id="ef538-210">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="ef538-210">DataAdapters and DataReaders</span></span>](dataadapters-and-datareaders.md)
- [<span data-ttu-id="ef538-211">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="ef538-211">Data Type Mappings in ADO.NET</span></span>](data-type-mappings-in-ado-net.md)
- [<span data-ttu-id="ef538-212">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="ef538-212">Modifying Data with a DbDataAdapter</span></span>](modifying-data-with-a-dbdataadapter.md)
- [<span data-ttu-id="ef538-213">Birden Çok Etkin Sonuç Kümesi (MARS)</span><span class="sxs-lookup"><span data-stu-id="ef538-213">Multiple Active Result Sets (MARS)</span></span>](./sql/multiple-active-result-sets-mars.md)
- [<span data-ttu-id="ef538-214">ADO.NET’e Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ef538-214">ADO.NET Overview</span></span>](ado-net-overview.md)
