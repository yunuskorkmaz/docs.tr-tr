---
title: "DataAdapter kümesinden doldurma"
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
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c0991398a28e491d381d10dea8a14ed463c67c89
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2018
---
# <a name="populating-a-dataset-from-a-dataadapter"></a><span data-ttu-id="a8b94-102">DataAdapter kümesinden doldurma</span><span class="sxs-lookup"><span data-stu-id="a8b94-102">Populating a DataSet from a DataAdapter</span></span>
<span data-ttu-id="a8b94-103">[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataSet> Bir tutarlı ilişkisel programlama modeli bağımsız veri kaynağının sağlayan veri bellekte gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="a8b94-103">The [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]<xref:System.Data.DataSet> is a memory-resident representation of data that provides a consistent relational programming model independent of the data source.</span></span> <span data-ttu-id="a8b94-104">`DataSet` Tabloları, kısıtlamalar ve tablolar arasında ilişkiler içeren verileri eksiksiz bir kümesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a8b94-104">The `DataSet` represents a complete set of data that includes tables, constraints, and relationships among the tables.</span></span> <span data-ttu-id="a8b94-105">Çünkü `DataSet` veri kaynağı, bağımsız bir `DataSet` verileri uygulamaya yerel ve birden çok veri kaynaklarından verileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a8b94-105">Because the `DataSet` is independent of the data source, a `DataSet` can include data local to the application, and data from multiple data sources.</span></span> <span data-ttu-id="a8b94-106">Mevcut veri kaynakları ile etkileşim aracılığıyla denetlenir `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-106">Interaction with existing data sources is controlled through the `DataAdapter`.</span></span>  
  
 <span data-ttu-id="a8b94-107">`SelectCommand` Özelliği `DataAdapter` olan bir `Command` veri kaynağından veri alır nesnesi.</span><span class="sxs-lookup"><span data-stu-id="a8b94-107">The `SelectCommand` property of the `DataAdapter` is a `Command` object that retrieves data from the data source.</span></span> <span data-ttu-id="a8b94-108">`InsertCommand`, `UpdateCommand`, Ve `DeleteCommand` özelliklerini `DataAdapter` olan `Command` verilerde yapılan değişikliklere göre veri kaynağındaki verileri yapılan güncelleştirmeleri yönetebilirsiniz nesneleri `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-108">The `InsertCommand`, `UpdateCommand`, and `DeleteCommand` properties of the `DataAdapter` are `Command` objects that manage updates to the data in the data source according to modifications made to the data in the `DataSet`.</span></span> <span data-ttu-id="a8b94-109">Bu özellikleri daha ayrıntılı olarak ele alınmaktadır [veri kaynaklarıyla güncelleştirme DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span><span class="sxs-lookup"><span data-stu-id="a8b94-109">These properties are covered in more detail in [Updating Data Sources with DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).</span></span>  
  
 <span data-ttu-id="a8b94-110">`Fill` Yöntemi `DataAdapter` doldurmak için kullanılan bir `DataSet` sonuçlarını içeren `SelectCommand` , `DataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-110">The `Fill` method of the `DataAdapter` is used to populate a `DataSet` with the results of the `SelectCommand` of the `DataAdapter`.</span></span> <span data-ttu-id="a8b94-111">`Fill`kendi bağımsız değişkenleri olarak alır bir `DataSet` doldurulması için ve bir `DataTable` nesne veya adını `DataTable` döndürülen satır ile doldurulacak `SelectCommand`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-111">`Fill` takes as its arguments a `DataSet` to be populated, and a `DataTable` object, or the name of the `DataTable` to be filled with the rows returned from the `SelectCommand`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8b94-112">Kullanarak `DataAdapter` özellikle tablodaki satır sayısını varsa tüm bir tabloyu alır süreyi almak için.</span><span class="sxs-lookup"><span data-stu-id="a8b94-112">Using the `DataAdapter` to retrieve all of a table takes time, especially if there are many rows in the table.</span></span> <span data-ttu-id="a8b94-113">Bulma ve verileri işlerken veritabanına erişirken çünkü ve sonra istemci için verileri aktarma zaman alır.</span><span class="sxs-lookup"><span data-stu-id="a8b94-113">This is because accessing the database, locating and processing the data, and then transferring the data to the client is time-consuming.</span></span> <span data-ttu-id="a8b94-114">Tüm tablonun istemciye çekme sunucusunda tüm satırların kilitler.</span><span class="sxs-lookup"><span data-stu-id="a8b94-114">Pulling all of the table to the client also locks all of the rows on the server.</span></span> <span data-ttu-id="a8b94-115">Performansı artırmak için kullanabileceğiniz `WHERE` istemciye döndürülen satır sayısını önemli ölçüde azaltan yan tümcesi.</span><span class="sxs-lookup"><span data-stu-id="a8b94-115">To improve performance, you can use the `WHERE` clause to greatly reduce the number of rows returned to the client.</span></span> <span data-ttu-id="a8b94-116">Yalnızca açıkça gerekli sütunlarda listeleyerek istemciye döndürülen veri miktarını da azaltabilir `SELECT` deyimi.</span><span class="sxs-lookup"><span data-stu-id="a8b94-116">You can also reduce the amount of data returned to the client by only explicitly listing required columns in the `SELECT` statement.</span></span> <span data-ttu-id="a8b94-117">Gruplar halinde (örneğin, bir seferde birkaç yüz satırlar) satırları alma ve istemci ile geçerli toplu işlem tamamlandığında sonraki yalnızca almak için başka bir iyi geçici bir çözüm değildir.</span><span class="sxs-lookup"><span data-stu-id="a8b94-117">Another good workaround is to retrieve the rows in batches (such as several hundred rows at a time) and only retrieve the next batch when the client is finished with the current batch.</span></span>  
  
 <span data-ttu-id="a8b94-118">`Fill` Yöntemi kullanan `DataReader` sütun adlarının ve tablo oluşturmak için kullanılan türler örtük olarak döndürülecek nesne `DataSet`ve tablo satırları doldurmak için veri `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-118">The `Fill` method uses the `DataReader` object implicitly to return the column names and types that are used to create the tables in the `DataSet`, and the data to populate the rows of the tables in the `DataSet`.</span></span> <span data-ttu-id="a8b94-119">Zaten mevcut değilse tablolar ve sütunlar yalnızca oluşturulur; Aksi takdirde `Fill` varolan kullanan `DataSet` şema.</span><span class="sxs-lookup"><span data-stu-id="a8b94-119">Tables and columns are only created if they do not already exist; otherwise `Fill` uses the existing `DataSet` schema.</span></span> <span data-ttu-id="a8b94-120">Sütun türleri olarak oluşturulan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tablolarda göre türleri [ADO.NET veri türü eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span><span class="sxs-lookup"><span data-stu-id="a8b94-120">Column types are created as [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] types according to the tables in [Data Type Mappings in ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md).</span></span> <span data-ttu-id="a8b94-121">Birincil anahtarları veri kaynağında mevcut sürece oluşturulmaz ve `DataAdapter` **.**`MissingSchemaAction`</span><span class="sxs-lookup"><span data-stu-id="a8b94-121">Primary keys are not created unless they exist in the data source and `DataAdapter`**.**`MissingSchemaAction`</span></span> <span data-ttu-id="a8b94-122">ayarlanmış `MissingSchemaAction` **.** `AddWithKey`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-122">is set to `MissingSchemaAction`**.**`AddWithKey`.</span></span> <span data-ttu-id="a8b94-123">Varsa `Fill` bulur bir tablo için birincil anahtar varsa, veri üzerine yazar `DataSet` veri kaynağından döndürülen birincil anahtar sütun değerleri eşleştiği bu satırın satırlar için veri kaynağı ile.</span><span class="sxs-lookup"><span data-stu-id="a8b94-123">If `Fill` finds that a primary key exists for a table, it will overwrite data in the `DataSet` with data from the data source for rows where the primary key column values match those of the row returned from the data source.</span></span> <span data-ttu-id="a8b94-124">Birincil anahtar bulunursa, veri tablolarında eklenir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-124">If no primary key is found, the data is appended to the tables in the `DataSet`.</span></span> <span data-ttu-id="a8b94-125">`Fill`doldurma sırasında oluşabilecek tüm eşlemeleri kullanan `DataSet` (bkz [DataAdapter DataTable ve DataColumn eşlemeleri](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).</span><span class="sxs-lookup"><span data-stu-id="a8b94-125">`Fill` uses any mappings that may exist when you populate the `DataSet` (see [DataAdapter DataTable and DataColumn Mappings](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a8b94-126">Varsa `SelectCommand` bir dış birleşim, sonuçlarını döndürür `DataAdapter` ayarlı değil bir `PrimaryKey` elde edilen değer `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-126">If the `SelectCommand` returns the results of an OUTER JOIN, the `DataAdapter` does not set a `PrimaryKey` value for the resulting `DataTable`.</span></span> <span data-ttu-id="a8b94-127">Tanımlamanız gerekir `PrimaryKey` kendinize yinelenen satırları düzgün olarak çözülen emin olun.</span><span class="sxs-lookup"><span data-stu-id="a8b94-127">You must define the `PrimaryKey` yourself to make sure that duplicate rows are resolved correctly.</span></span> <span data-ttu-id="a8b94-128">Daha fazla bilgi için bkz: [tanımlama birincil anahtarlar](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span><span class="sxs-lookup"><span data-stu-id="a8b94-128">For more information, see [Defining Primary Keys](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).</span></span>  
  
 <span data-ttu-id="a8b94-129">Aşağıdaki kod örneğinde bir örneğini oluşturur bir <xref:System.Data.SqlClient.SqlDataAdapter> kullanan bir <xref:System.Data.SqlClient.SqlConnection> Microsoft SQL Server `Northwind` veritabanı ve dolduran bir <xref:System.Data.DataTable> içinde bir `DataSet` müşterilerin listesi ile.</span><span class="sxs-lookup"><span data-stu-id="a8b94-129">The following code example creates an instance of a <xref:System.Data.SqlClient.SqlDataAdapter> that uses a <xref:System.Data.SqlClient.SqlConnection> to the Microsoft SQL Server `Northwind` database and populates a <xref:System.Data.DataTable> in a `DataSet` with the list of customers.</span></span> <span data-ttu-id="a8b94-130">SQL deyimi ve <xref:System.Data.SqlClient.SqlConnection> bağımsız değişkenleri geçirilen <xref:System.Data.SqlClient.SqlDataAdapter> oluşturmak için kullanılan Oluşturucu <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> özelliği <xref:System.Data.SqlClient.SqlDataAdapter>.</span><span class="sxs-lookup"><span data-stu-id="a8b94-130">The SQL statement and <xref:System.Data.SqlClient.SqlConnection> arguments passed to the <xref:System.Data.SqlClient.SqlDataAdapter> constructor are used to create the <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> property of the <xref:System.Data.SqlClient.SqlDataAdapter>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8b94-131">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8b94-131">Example</span></span>  
  
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
>  <span data-ttu-id="a8b94-132">Bu örnekte gösterilen kodu açıkça açılmaz ve Kapat `Connection`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-132">The code shown in this example does not explicitly open and close the `Connection`.</span></span> <span data-ttu-id="a8b94-133">`Fill` Yöntemi örtük olarak açılır `Connection` , `DataAdapter` bağlantı zaten açık olduğunu bulursa kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="a8b94-133">The `Fill` method implicitly opens the `Connection` that the `DataAdapter` is using if it finds that the connection is not already open.</span></span> <span data-ttu-id="a8b94-134">Varsa `Fill` bağlantısı açıldığı de bağlantıyı kapatır zaman `Fill` tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="a8b94-134">If `Fill` opened the connection, it also closes the connection when `Fill` is finished.</span></span> <span data-ttu-id="a8b94-135">Tek bir işlemle gibi dağıttığınızda bu kodunuzu kolaylaştırabilir bir `Fill` veya bir `Update`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-135">This can simplify your code when you deal with a single operation such as a `Fill` or an `Update`.</span></span> <span data-ttu-id="a8b94-136">Açık bir bağlantı gerektiren birden çok işlem gerçekleştiriyorsanız, ancak performansı, uygulamanızın açıkça çağırarak artırabilirsiniz `Open` yöntemi `Connection`, veri kaynağına karşı işlemlerini gerçekleştirme ve ardından çağırma `Close` yöntemi `Connection`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-136">However, if you are performing multiple operations that require an open connection, you can improve the performance of your application by explicitly calling the `Open` method of the `Connection`, performing the operations against the data source, and then calling the `Close` method of the `Connection`.</span></span> <span data-ttu-id="a8b94-137">Veri kaynağı bağlantıları mümkün olduğunca kısa bir süre kullanmak için kaynakları serbest bırakmak için diğer istemci uygulamaları tarafından açık tutmak denemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="a8b94-137">You should try to keep connections to the data source open as briefly as possible to free resources for use by other client applications.</span></span>  
  
## <a name="multiple-result-sets"></a><span data-ttu-id="a8b94-138">Birden çok sonuç kümesi</span><span class="sxs-lookup"><span data-stu-id="a8b94-138">Multiple Result Sets</span></span>  
 <span data-ttu-id="a8b94-139">Varsa `DataAdapter` karşılaştığı birden çok sonuç kümeleri, birden fazla tabloya oluşturur `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-139">If the `DataAdapter` encounters multiple result sets, it creates multiple tables in the `DataSet`.</span></span> <span data-ttu-id="a8b94-140">Tabloları tablosunun bir artımlı varsayılan adı verilen*N*Table0 için "Tablo" ile başlayan.</span><span class="sxs-lookup"><span data-stu-id="a8b94-140">The tables are given an incremental default name of Table*N*, starting with "Table" for Table0.</span></span> <span data-ttu-id="a8b94-141">Bağımsız değişken olarak bir tablo adı geçip geçmediğini `Fill` yöntemi, tablolar TableName artımlı varsayılan adını verilmiştir*N*TableName0 için "TableName" ile başlayan.</span><span class="sxs-lookup"><span data-stu-id="a8b94-141">If a table name is passed as an argument to the `Fill` method, the tables are given an incremental default name of TableName*N*, starting with "TableName" for TableName0.</span></span>  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a><span data-ttu-id="a8b94-142">Birden çok DataAdapters kümesinden doldurma</span><span class="sxs-lookup"><span data-stu-id="a8b94-142">Populating a DataSet from Multiple DataAdapters</span></span>  
 <span data-ttu-id="a8b94-143">Herhangi bir sayıda `DataAdapter` nesneleri ile kullanılabilir bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-143">Any number of `DataAdapter` objects can be used with a `DataSet`.</span></span> <span data-ttu-id="a8b94-144">Her `DataAdapter` bir veya daha fazla doldurmak için kullanılan `DataTable` nesneleri ve çözümleme güncelleştirmeleri ilgili veri kaynağına yedekleyin.</span><span class="sxs-lookup"><span data-stu-id="a8b94-144">Each `DataAdapter` can be used to fill one or more `DataTable` objects and resolve updates back to the relevant data source.</span></span> <span data-ttu-id="a8b94-145">`DataRelation`ve `Constraint` nesneleri eklenebilir `DataSet` yerel olarak, farklı veri kaynaklarından veri ilişkili olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8b94-145">`DataRelation` and `Constraint` objects can be added to the `DataSet` locally, which enables you to relate data from dissimilar data sources.</span></span> <span data-ttu-id="a8b94-146">Örneğin, bir `DataSet` bir Microsoft SQL Server veritabanı, OLE DB ve XML akışları bir veri kaynağı kullanıma sunulan IBM DB2 veritabanına verileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a8b94-146">For example, a `DataSet` can contain data from a Microsoft SQL Server database, an IBM DB2 database exposed through OLE DB, and a data source that streams XML.</span></span> <span data-ttu-id="a8b94-147">Bir veya daha fazla `DataAdapter` nesneleri, her veri kaynağı iletişimi işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a8b94-147">One or more `DataAdapter` objects can handle communication to each data source.</span></span>  
  
### <a name="example"></a><span data-ttu-id="a8b94-148">Örnek</span><span class="sxs-lookup"><span data-stu-id="a8b94-148">Example</span></span>  
 <span data-ttu-id="a8b94-149">Aşağıdaki kod örneğinde müşterilerden listesini doldurur `Northwind` Microsoft SQL Server veritabanı ve siparişleri listesini `Northwind` Microsoft Access 2000'de depolanan veritabanı.</span><span class="sxs-lookup"><span data-stu-id="a8b94-149">The following code example populates a list of customers from the `Northwind` database on Microsoft SQL Server, and a list of orders from the `Northwind` database stored in Microsoft Access 2000.</span></span> <span data-ttu-id="a8b94-150">Doldurulmuş tablolar ile ilişkili bir `DataRelation`, müşterilerin listesini sonra o müşteri için siparişleri ile birlikte görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a8b94-150">The filled tables are related with a `DataRelation`, and the list of customers is then displayed with the orders for that customer.</span></span> <span data-ttu-id="a8b94-151">Hakkında daha fazla bilgi için `DataRelation` nesneleri bkz [ekleme DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) ve [gezinme DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md).</span><span class="sxs-lookup"><span data-stu-id="a8b94-151">For more information about `DataRelation` objects, see [Adding DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) and [Navigating DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md).</span></span>  
  
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
  
## <a name="sql-server-decimal-type"></a><span data-ttu-id="a8b94-152">SQL Server Decimal türü</span><span class="sxs-lookup"><span data-stu-id="a8b94-152">SQL Server Decimal Type</span></span>  
 <span data-ttu-id="a8b94-153">Varsayılan olarak, `DataSet` kullanarak verileri depolayan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri türleri.</span><span class="sxs-lookup"><span data-stu-id="a8b94-153">By default, the `DataSet` stores data by using [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data types.</span></span> <span data-ttu-id="a8b94-154">Çoğu uygulama için bu veri kaynağı bilgileri kullanışlı bir gösterimini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8b94-154">For most applications, these provide a convenient representation of data source information.</span></span> <span data-ttu-id="a8b94-155">Ancak, veri kaynağındaki veri türü bir SQL Server ondalık veya sayısal veri türü olduğunda bu gösterim bir soruna neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8b94-155">However, this representation may cause a problem when the data type in the data source is a SQL Server decimal or numeric data type.</span></span> <span data-ttu-id="a8b94-156">[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` Veri türü verir en fazla 28 önemli basamak, ancak SQL Server `decimal` veri türü 38 basamak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8b94-156">The [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` data type allows a maximum of 28 significant digits, whereas the SQL Server `decimal` data type allows 38 significant digits.</span></span> <span data-ttu-id="a8b94-157">Varsa `SqlDataAdapter` sırasında belirler bir `Fill` işlemi, bir SQL Server'ın duyarlık `decimal` alandır 28 karakterden uzun, geçerli satır eklenmez `DataTable`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-157">If the `SqlDataAdapter` determines during a `Fill` operation that the precision of a SQL Server `decimal` field is larger than 28 characters, the current row is not added to the `DataTable`.</span></span> <span data-ttu-id="a8b94-158">Bunun yerine `FillError` olayı oluşur, duyarlık kaybı oluşur ve uygun şekilde yanıt olup olmadığını belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a8b94-158">Instead the `FillError` event occurs, which enables you to determine whether a loss of precision will occur, and respond appropriately.</span></span> <span data-ttu-id="a8b94-159">Hakkında daha fazla bilgi için `FillError` olayı bkz [olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span><span class="sxs-lookup"><span data-stu-id="a8b94-159">For more information about the `FillError` event, see [Handling DataAdapter Events](../../../../docs/framework/data/adonet/handling-dataadapter-events.md).</span></span> <span data-ttu-id="a8b94-160">SQL sunucusu `decimal` değeri, ayrıca kullanabileceğiniz bir <xref:System.Data.SqlClient.SqlDataReader> nesne ve arama <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a8b94-160">To get the SQL Server `decimal` value, you can also use a <xref:System.Data.SqlClient.SqlDataReader> object and call the <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> method.</span></span>  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]<span data-ttu-id="a8b94-161">sunulan 2.0 için gelişmiş destek <xref:System.Data.SqlTypes> içinde `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-161"> 2.0 introduced enhanced support for <xref:System.Data.SqlTypes> in the `DataSet`.</span></span> <span data-ttu-id="a8b94-162">Daha fazla bilgi için bkz: [SqlTypes ve veri kümesini](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).</span><span class="sxs-lookup"><span data-stu-id="a8b94-162">For more information, see [SqlTypes and the DataSet](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).</span></span>  
  
## <a name="ole-db-chapters"></a><span data-ttu-id="a8b94-163">OLE DB bölümler</span><span class="sxs-lookup"><span data-stu-id="a8b94-163">OLE DB Chapters</span></span>  
 <span data-ttu-id="a8b94-164">Hiyerarşik satır kümeleri veya bölümlerle (OLE DB türü `DBTYPE_HCHAPTER`, ADO türü `adChapter`) içeriğini doldurmak için kullanılan bir `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-164">Hierarchical rowsets, or chapters (OLE DB type `DBTYPE_HCHAPTER`, ADO type `adChapter`) can be used to fill the contents of a `DataSet`.</span></span> <span data-ttu-id="a8b94-165">Zaman <xref:System.Data.OleDb.OleDbDataAdapter> bölümlere sütun sırasında karşılaştığı bir `Fill` işlemi, bir `DataTable` bölümlere sütunu için oluşturulur ve bu tablo, bölüm satırları ve sütunları ile doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a8b94-165">When the <xref:System.Data.OleDb.OleDbDataAdapter> encounters a chaptered column during a `Fill` operation, a `DataTable` is created for the chaptered column, and that table is filled with the columns and rows from the chapter.</span></span> <span data-ttu-id="a8b94-166">Üst tablo adı ve bölümlere sütun adı biçiminde kullanarak bölümlere sütun adlı için oluşturulan tablo "*ParentTableNameChapteredColumnName*".</span><span class="sxs-lookup"><span data-stu-id="a8b94-166">The table created for the chaptered column is named by using both the parent table name and the chaptered column name in the form "*ParentTableNameChapteredColumnName*".</span></span> <span data-ttu-id="a8b94-167">Bir tablo zaten varsa `DataSet` bölümlere sütunun adı ile eşleşen, geçerli tabloda bölüm verilerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a8b94-167">If a table already exists in the `DataSet` that matches the name of the chaptered column, the current table is filled with the chapter data.</span></span> <span data-ttu-id="a8b94-168">Bölümde bulunan bir sütun eşleşen varolan bir tabloda sütun yok ise, yeni bir sütun eklenir.</span><span class="sxs-lookup"><span data-stu-id="a8b94-168">If there is no column in an existing table that matches a column found in the chapter, a new column is added.</span></span>  
  
 <span data-ttu-id="a8b94-169">Tablolarda önce `DataSet` doldurulur bölümlere sütunlardaki verilerle bir ilişkisi üst ve alt arasında tabloları hiyerarşik satır kümesinin üst ve alt tabloya bir tamsayı sütunu ekleyerek üst sütun ayarını oluşturulur otomatik artış ve oluşturma bir `DataRelation` eklenen sütunları her iki tablodan kullanarak.</span><span class="sxs-lookup"><span data-stu-id="a8b94-169">Before the tables in the `DataSet` are filled with the data in the chaptered columns, a relation is created between the parent and child tables of the hierarchical rowset by adding an integer column to both the parent and child table, setting the parent column to auto-increment, and creating a `DataRelation` using the added columns from both tables.</span></span> <span data-ttu-id="a8b94-170">Form üst tablo ve bölüm sütun adlarını kullanarak eklenen ilişkisi adlı "*ParentTableNameChapterColumnName*".</span><span class="sxs-lookup"><span data-stu-id="a8b94-170">The added relation is named by using the parent table and chapter column names in the form "*ParentTableNameChapterColumnName*".</span></span>  
  
 <span data-ttu-id="a8b94-171">Bulunmaktadır yalnızca ilgili sütunu Not `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="a8b94-171">Note that the related column only exists in the `DataSet`.</span></span> <span data-ttu-id="a8b94-172">Veri kaynağından sonraki dolgular varolan satırlara birleştirilen değişiklikleri yerine tablolara eklenecek yeni satırlar neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="a8b94-172">Subsequent fills from the data source can cause new rows to be added to the tables instead of changes being merged into existing rows.</span></span>  
  
 <span data-ttu-id="a8b94-173">Kullanırsanız, ayrıca `DataAdapter.Fill` alan aşırı bir `DataTable`, yalnızca o tabloyu doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a8b94-173">Note also that, if you use the `DataAdapter.Fill` overload that takes a `DataTable`, only that table will be filled.</span></span> <span data-ttu-id="a8b94-174">Bir otomatik artan tamsayı sütunu yine tabloya eklenecek olan ancak hiçbir alt tablo oluşturulan veya doldurulmuş ve hiçbir ilişkisi oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a8b94-174">An auto-incrementing integer column will still be added to the table, but no child table will be created or filled, and no relation will be created.</span></span>  
  
 <span data-ttu-id="a8b94-175">Aşağıdaki örnek MSDataShape sağlayıcı siparişleri her müşteri için bir bölüm sütununa müşterilerin listesini oluşturmak için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a8b94-175">The following example uses the MSDataShape Provider to generate a chapter column of orders for each customer in a list of customers.</span></span> <span data-ttu-id="a8b94-176">A `DataSet` sonra verilerle doldurulur.</span><span class="sxs-lookup"><span data-stu-id="a8b94-176">A `DataSet` is then filled with the data.</span></span>  
  
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
  
 <span data-ttu-id="a8b94-177">Zaman `Fill` işlemi tamamlandığında, `DataSet` iki tablo içerir: `Customers` ve `CustomersOrders`, burada `CustomersOrders` bölümlere sütunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a8b94-177">When the `Fill` operation is complete, the `DataSet` contains two tables: `Customers` and `CustomersOrders`, where `CustomersOrders` represents the chaptered column.</span></span> <span data-ttu-id="a8b94-178">Adlı ek bir sütun `Orders` eklenen `Customers` tablo ve adlı ek bir sütun `CustomersOrders` eklenen `CustomersOrders` tablo.</span><span class="sxs-lookup"><span data-stu-id="a8b94-178">An additional column named `Orders` is added to the `Customers` table, and an additional column named `CustomersOrders` is added to the `CustomersOrders` table.</span></span> <span data-ttu-id="a8b94-179">`Orders` Sütununda `Customers` tablo otomatik artım ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a8b94-179">The `Orders` column in the `Customers` table is set to auto-increment.</span></span> <span data-ttu-id="a8b94-180">A `DataRelation`, `CustomersOrders`, tablolarla eklenme sütunları kullanılarak oluşturulan `Customers` üst tablo olarak.</span><span class="sxs-lookup"><span data-stu-id="a8b94-180">A `DataRelation`, `CustomersOrders`, is created by using the columns that were added to the tables with `Customers` as the parent table.</span></span> <span data-ttu-id="a8b94-181">Aşağıdaki tabloda bazı örnek sonuçları gösterir.</span><span class="sxs-lookup"><span data-stu-id="a8b94-181">The following tables show some sample results.</span></span>  
  
### <a name="tablename-customers"></a><span data-ttu-id="a8b94-182">TableName: müşteriler</span><span class="sxs-lookup"><span data-stu-id="a8b94-182">TableName: Customers</span></span>  
  
|<span data-ttu-id="a8b94-183">CustomerID</span><span class="sxs-lookup"><span data-stu-id="a8b94-183">CustomerID</span></span>|<span data-ttu-id="a8b94-184">CompanyName</span><span class="sxs-lookup"><span data-stu-id="a8b94-184">CompanyName</span></span>|<span data-ttu-id="a8b94-185">Siparişleri</span><span class="sxs-lookup"><span data-stu-id="a8b94-185">Orders</span></span>|  
|----------------|-----------------|------------|  
|<span data-ttu-id="a8b94-186">ALFKI</span><span class="sxs-lookup"><span data-stu-id="a8b94-186">ALFKI</span></span>|<span data-ttu-id="a8b94-187">Alfreds Futterkiste</span><span class="sxs-lookup"><span data-stu-id="a8b94-187">Alfreds Futterkiste</span></span>|<span data-ttu-id="a8b94-188">0</span><span class="sxs-lookup"><span data-stu-id="a8b94-188">0</span></span>|  
|<span data-ttu-id="a8b94-189">ANATR</span><span class="sxs-lookup"><span data-stu-id="a8b94-189">ANATR</span></span>|<span data-ttu-id="a8b94-190">Ana Trujillo Emparedados y helados</span><span class="sxs-lookup"><span data-stu-id="a8b94-190">Ana Trujillo Emparedados y helados</span></span>|<span data-ttu-id="a8b94-191">1.</span><span class="sxs-lookup"><span data-stu-id="a8b94-191">1</span></span>|  
  
### <a name="tablename-customersorders"></a><span data-ttu-id="a8b94-192">TableName: CustomersOrders</span><span class="sxs-lookup"><span data-stu-id="a8b94-192">TableName: CustomersOrders</span></span>  
  
|<span data-ttu-id="a8b94-193">CustomerID</span><span class="sxs-lookup"><span data-stu-id="a8b94-193">CustomerID</span></span>|<span data-ttu-id="a8b94-194">OrderID</span><span class="sxs-lookup"><span data-stu-id="a8b94-194">OrderID</span></span>|<span data-ttu-id="a8b94-195">CustomersOrders</span><span class="sxs-lookup"><span data-stu-id="a8b94-195">CustomersOrders</span></span>|  
|----------------|-------------|---------------------|  
|<span data-ttu-id="a8b94-196">ALFKI</span><span class="sxs-lookup"><span data-stu-id="a8b94-196">ALFKI</span></span>|<span data-ttu-id="a8b94-197">10643</span><span class="sxs-lookup"><span data-stu-id="a8b94-197">10643</span></span>|<span data-ttu-id="a8b94-198">0</span><span class="sxs-lookup"><span data-stu-id="a8b94-198">0</span></span>|  
|<span data-ttu-id="a8b94-199">ALFKI</span><span class="sxs-lookup"><span data-stu-id="a8b94-199">ALFKI</span></span>|<span data-ttu-id="a8b94-200">10692</span><span class="sxs-lookup"><span data-stu-id="a8b94-200">10692</span></span>|<span data-ttu-id="a8b94-201">0</span><span class="sxs-lookup"><span data-stu-id="a8b94-201">0</span></span>|  
|<span data-ttu-id="a8b94-202">ANATR</span><span class="sxs-lookup"><span data-stu-id="a8b94-202">ANATR</span></span>|<span data-ttu-id="a8b94-203">10308</span><span class="sxs-lookup"><span data-stu-id="a8b94-203">10308</span></span>|<span data-ttu-id="a8b94-204">1.</span><span class="sxs-lookup"><span data-stu-id="a8b94-204">1</span></span>|  
|<span data-ttu-id="a8b94-205">ANATR</span><span class="sxs-lookup"><span data-stu-id="a8b94-205">ANATR</span></span>|<span data-ttu-id="a8b94-206">10625</span><span class="sxs-lookup"><span data-stu-id="a8b94-206">10625</span></span>|<span data-ttu-id="a8b94-207">1.</span><span class="sxs-lookup"><span data-stu-id="a8b94-207">1</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a8b94-208">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a8b94-208">See Also</span></span>  
 [<span data-ttu-id="a8b94-209">DataAdapters ve DataReaders</span><span class="sxs-lookup"><span data-stu-id="a8b94-209">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="a8b94-210">ADO.NET’te Veri Türü Eşlemeleri</span><span class="sxs-lookup"><span data-stu-id="a8b94-210">Data Type Mappings in ADO.NET</span></span>](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [<span data-ttu-id="a8b94-211">DbDataAdapter ile Verileri Değiştirme</span><span class="sxs-lookup"><span data-stu-id="a8b94-211">Modifying Data with a DbDataAdapter</span></span>](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [<span data-ttu-id="a8b94-212">Birden Çok Etkin Sonuç Kümesi (MARS)</span><span class="sxs-lookup"><span data-stu-id="a8b94-212">Multiple Active Result Sets (MARS)</span></span>](../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [<span data-ttu-id="a8b94-213">ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi</span><span class="sxs-lookup"><span data-stu-id="a8b94-213">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
