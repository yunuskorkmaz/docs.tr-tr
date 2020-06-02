---
title: DataAdapter’dan bir DataSet Doldurma
description: Veri kaynağından bağımsız olarak tutarlı bir ilişkisel programlama modeli sağlayan ADO.NET içindeki DataAdapter nesnesinden bir veri kümesini doldurmayı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: 3d4da840e1d51ec6f309915787caa8891db3eb59
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286669"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>DataAdapter’dan bir DataSet Doldurma
ADO.NET, <xref:System.Data.DataSet> veri kaynağından bağımsız tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimidir. , Tablolar `DataSet` arasındaki tabloları, kısıtlamaları ve ilişkileri içeren tüm veri kümesini temsil eder. , `DataSet` Veri kaynağından bağımsız olduğundan, bir `DataSet` uygulamaya yerel veri ve birden çok veri kaynağından veri içerebilir. Mevcut veri kaynaklarıyla etkileşim aracılığıyla denetlenir `DataAdapter` .  
  
 `SelectCommand`Öğesinin özelliği, `DataAdapter` `Command` veri kaynağından veri alan bir nesnedir. , `InsertCommand` `UpdateCommand` Ve özellikleri, `DeleteCommand` `DataAdapter` `Command` içindeki verilerde yapılan değişikliklere göre veri kaynağındaki verilerle ilgili güncelleştirmeleri yöneten nesnelerdir `DataSet` . Bu özellikler, [veri kaynaklarını DataAdapter Ile güncelleştirme konusunda](updating-data-sources-with-dataadapters.md)daha ayrıntılı olarak ele alınmıştır.  
  
 Yöntemi, öğesinin `Fill` `DataAdapter` sonuçlarıyla birlikte doldurmak için kullanılır `DataSet` `SelectCommand` `DataAdapter` . `Fill``DataSet`, ' nin doldurulduğu bağımsız değişkenlerini, bir `DataTable` nesnesini veya ' `DataTable` den döndürülen satırlarla doldurulacak olan adını alır `SelectCommand` .  
  
> [!NOTE]
> `DataAdapter`Bir tablonun tümünü almak için kullanılması, özellikle tabloda çok sayıda satır olması durumunda zaman alır. Bunun nedeni, veritabanına erişmek, verileri bulmak ve işlemek ve sonra verilerin istemciye aktarılması zaman alır. Tüm tablosunun istemciye çekmeleri, sunucudaki tüm satırları da kilitler. Performansı artırmak için, `WHERE` yan tümcesini kullanarak istemciye döndürülen satır sayısını büyük ölçüde azaltabilirsiniz. Ayrıca, yalnızca deyimindeki gerekli sütunları açıkça listeleyerek istemciye döndürülen veri miktarını azaltabilirsiniz `SELECT` . Başka bir iyi geçici çözüm de satırları toplu olarak (örneğin, bir kerede birkaç yüz satır) almak ve yalnızca, geçerli toplu işlemle istemci tamamlandığında sonraki toplu işi almak içindir.  
  
 Yöntemi, içindeki `Fill` `DataReader` tabloları oluşturmak için kullanılan sütun adlarını ve türlerini `DataSet` ve içindeki tabloların satırlarının doldurulmasıyla ilgili verileri döndürmek için nesneyi örtük olarak kullanır `DataSet` . Tablolar ve sütunlar yalnızca henüz yoksa oluşturulur; Aksi halde `Fill` mevcut `DataSet` Şemayı kullanır. Sütun türleri, [ADO.net Içindeki veri türü eşlemelerinde](data-type-mappings-in-ado-net.md)bulunan tablolara göre .NET Framework türleri olarak oluşturulur. Birincil anahtarlar veri kaynağında yoksa oluşturulmaz `DataAdapter` **.**`MissingSchemaAction` , olarak ayarlanır `MissingSchemaAction` **.** `AddWithKey` .. `Fill`Bir tablonun birincil anahtarının mevcut olduğunu belirlerse, `DataSet` birincil anahtar sütun değerlerinin veri kaynağından döndürülen satırla eşleştiği satırlar için veri kaynağındaki verilerle veri üzerine yazar. Birincil anahtar bulunamazsa, veriler içindeki tablolara eklenir `DataSet` . `Fill`' i doldurduğunuzda mevcut olabilecek eşlemeleri kullanır `DataSet` (bkz. [DataAdapter DataTable ve DataColumn Mappings](dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
> , `SelectCommand` BIR Dış birleştirmenin sonuçlarını döndürürse, `DataAdapter` `PrimaryKey` sonuç için bir değer yapmaz `DataTable` . `PrimaryKey`Yinelenen satırların doğru bir şekilde çözümlendiğini doğrulamak için kendinizi tanımlamanız gerekir. Daha fazla bilgi için bkz. [birincil anahtarları tanımlama](./dataset-datatable-dataview/defining-primary-keys.md).  
  
 Aşağıdaki kod örneği, bir ' ın, <xref:System.Data.SqlClient.SqlDataAdapter> Microsoft SQL Server veritabanına kullanan bir örneğini oluşturur ve bir içinde bir <xref:System.Data.SqlClient.SqlConnection> `Northwind` <xref:System.Data.DataTable> `DataSet` ile birlikte, müşteriler listesiyle doldurur. Oluşturucuya geçirilen SQL deyimleri ve <xref:System.Data.SqlClient.SqlConnection> bağımsız değişkenler <xref:System.Data.SqlClient.SqlDataAdapter> <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> , öğesinin özelliğini oluşturmak için kullanılır <xref:System.Data.SqlClient.SqlDataAdapter> .  
  
## <a name="example"></a>Örnek  
  
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
> Bu örnekte gösterilen kod açık bir şekilde açılmaz ve kapatmaz `Connection` . `Fill`Yöntemi, `Connection` `DataAdapter` bağlantının zaten açık olmadığını bulursa kullandığı öğesini örtülü olarak açar. `Fill`Bağlantı açıldıysa, tamamlandığında da bağlantıyı kapatır `Fill` . Bu, veya gibi tek bir işlemle uğraşdığınızda kodunuzun basitleşmesini sağlayabilir `Fill` `Update` . Ancak, açık bağlantı gerektiren birden çok işlem gerçekleştiriyorsanız uygulamanızın performansını, `Open` `Connection` veri kaynağına karşı işlemleri gerçekleştirerek ve sonra metodunu çağırarak, kendi metodunu açıkça çağırarak geliştirebilirsiniz `Close` `Connection` . Kaynakları diğer istemci uygulamalar tarafından kullanılmak üzere serbest bırakmak için veri kaynağına yönelik bağlantıları daha kısa sürede açık tutmaya çalışın.  
  
## <a name="multiple-result-sets"></a>Birden Fazla Sonuç Kümesi  
 `DataAdapter`Birden çok sonuç kümesiyle karşılaşırsa, içinde birden çok tablo oluşturur `DataSet` . Tablolara, TABLE0 için "Table" ile başlayarak, tablo*N*' nin artımlı varsayılan adı verilir. Bir tablo adı yöntemine bir bağımsız değişken olarak geçirilirse `Fill` , tablolara TableName0 için "TableName" ile başlayarak TableName*N*artımlı varsayılan adı verilir.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Birden çok DataAdapter nesnesinden veri kümesini doldurma  
 Herhangi bir sayıda `DataAdapter` nesne, ile kullanılabilir `DataSet` . Her biri `DataAdapter` , bir veya daha fazla nesneyi doldurup `DataTable` güncelleştirmeleri ilgili veri kaynağına geri çözümlemek için kullanılabilir. `DataRelation`ve `Constraint` nesneler yerel olarak eklenebilir `DataSet` , bu da benzer veri kaynaklarından verileri ilişkilendirmenize olanak sağlar. Örneğin, bir `DataSet` Microsoft SQL Server veritabanından veri, OLE DB üzerinden sunulan BIR IBM DB2 veritabanı ve XML akışı yapan bir veri kaynağı içerebilir. Bir veya daha fazla `DataAdapter` nesne, her bir veri kaynağıyla iletişimi işleyebilir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, Microsoft SQL Server veritabanından bir müşteri listesini `Northwind` ve `Northwind` Microsoft Access 2000 ' de depolanan veritabanından alınan siparişlerin listesini doldurur. Doldurulmuş tablolar bir ile ilgilidir `DataRelation` ve müşteriler listesi bu müşterinin siparişleriyle birlikte görüntülenir. Nesneler hakkında daha fazla bilgi için `DataRelation` bkz. [DataRelation 'ı ekleme](./dataset-datatable-dataview/adding-datarelations.md) ve DataRelation 'ı [gezinme](./dataset-datatable-dataview/navigating-datarelations.md).  
  
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
  
## <a name="sql-server-decimal-type"></a>SQL Server ondalık türü  
 Varsayılan olarak, `DataSet` .NET Framework veri türlerini kullanarak verileri depolar. Çoğu uygulama için, veri kaynağı bilgilerinin kullanışlı bir gösterimini sağlar. Ancak, veri kaynağındaki veri türü SQL Server Decimal veya numeric veri türü olduğunda bu gösterim soruna neden olabilir. .NET Framework `decimal` veri türü en fazla 28 önemli basamağa izin veriyor, ancak SQL Server `decimal` veri türü 38 önemli basamağa izin veriyor. `SqlDataAdapter`Bir işlem sırasında, `Fill` bir SQL Server alanının duyarlığının `decimal` 28 karakterden daha büyük olduğunu belirlerse, geçerli satır öğesine eklenmez `DataTable` . Bunun yerine, `FillError` bir duyarlık kaybı olup olmadığını ve uygun şekilde yanıt verip vermeyeceğinizi belirlemenizi sağlayan olay oluşur. Olay hakkında daha fazla bilgi için `FillError` bkz. [DataAdapter olaylarını işleme](handling-dataadapter-events.md). SQL Server değerini almak için `decimal` , bir nesnesi de kullanabilir <xref:System.Data.SqlClient.SqlDataReader> ve <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> yöntemini çağırabilirsiniz.  
  
 ADO.NET 2,0, içinde için geliştirilmiş destek getirmiştir <xref:System.Data.SqlTypes> `DataSet` . Daha fazla bilgi için bkz. [SqlTypes ve DataSet](./sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>OLE DB bölümler  
 Hiyerarşik satır kümeleri veya bölümler (OLE DB türü `DBTYPE_HCHAPTER` , ADO türü `adChapter` ), içeriğini dolduracak şekilde kullanılabilir `DataSet` . <xref:System.Data.OleDb.OleDbDataAdapter>Bir işlem sırasında bir bölümlenebilir sütun ile karşılaştığında, `Fill` `DataTable` bölümlenebilir sütun için bir oluşturulur ve bu tablo, bölümün sütunları ve satırlarıyla doldurulur. Bölümlendirilen sütun için oluşturulan tablo, hem üst tablo adı hem de "*Parenttablenamebölüteredcolumnname*" biçiminde bölümlendirilen sütun adı kullanılarak adlandırılır. İçinde, `DataSet` bölümlenebilir sütunun adıyla eşleşen bir tablo zaten varsa, geçerli tablo bölüm verileriyle doldurulur. Varolan bir tabloda, bölümde bulunan bir sütunla eşleşen bir sütun yoksa, yeni bir sütun eklenir.  
  
 İçindeki tablolar, `DataSet` bölümlenebilir sütunlardaki verilerle doldurulmadan önce hem üst hem de alt tabloya bir tamsayı sütunu ekleyerek hiyerarşik satır kümesinin üst ve alt tabloları arasında bir ilişki oluşturulur, üst sütunu otomatik artış olarak ayarlar ve `DataRelation` her iki tablodan de eklenen sütunları kullanarak oluşturma. Eklenen ilişki, "*Parenttablenamecolumntercolumnname*" biçiminde üst tablo ve bölüm sütun adları kullanılarak adlandırılır.  
  
 İlgili sütunun içinde yalnızca bulunduğunu unutmayın `DataSet` . Veri kaynağından sonraki dolgular, varolan satırlarla birleştirilecek değişiklikler yerine tablolara yeni satırların eklenmesine neden olabilir.  
  
 Ayrıca, öğesini `DataAdapter.Fill` alan aşırı yüklemeyi kullanırsanız `DataTable` , yalnızca bu tablo doldurulacak şekilde aklınızda kalır. Tabloya otomatik artan tamsayı sütunu yine de eklenecek, ancak hiçbir alt tablo oluşturulmayacak ya da doldurulmayacak ve hiçbir ilişki oluşturulmayacak.  
  
 Aşağıdaki örnek, bir müşteriler listesindeki her müşteri için siparişlerin bir bölüm sütununu oluşturmak üzere MSDataShape sağlayıcısını kullanır. `DataSet`Daha sonra veriler ile doldurulur.  
  
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
  
 `Fill`İşlem tamamlandığında, `DataSet` iki tablo içerir: `Customers` ve `CustomersOrders` , burada `CustomersOrders` bölümleyen sütunu temsil eder. Tabloya adlı ek bir sütun `Orders` eklenir `Customers` ve tabloya adlı ek bir sütun `CustomersOrders` eklenir `CustomersOrders` . `Orders` `Customers` Tablodaki sütun otomatik artış olarak ayarlanır. `DataRelation`,, `CustomersOrders` `Customers` Üst tablo olarak bulunan tablolara eklenen sütunlar kullanılarak oluşturulur. Aşağıdaki tablolarda bazı örnek sonuçlar gösterilmektedir.  
  
### <a name="tablename-customers"></a>TabloAdı: müşteriler  
  
|CustomerID|CompanyName|Siparişler|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkte|0|  
|ANATR|Ana Trujillo Emparedaddos y Helados|1|  
  
### <a name="tablename-customersorders"></a>TableName: CustomersOrders  
  
|CustomerID|OrderID|Müşteri Sorleyicileri|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [ADO.NET’te Veri Türü Eşlemeleri](data-type-mappings-in-ado-net.md)
- [DbDataAdapter ile Verileri Değiştirme](modifying-data-with-a-dbdataadapter.md)
- [Birden Çok Etkin Sonuç Kümesi (MARS)](./sql/multiple-active-result-sets-mars.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
