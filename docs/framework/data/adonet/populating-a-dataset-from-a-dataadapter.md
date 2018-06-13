---
title: DataAdapter kümesinden doldurma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: ced280be0fa14077be893c59596ed65b424172c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33356946"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>DataAdapter kümesinden doldurma
[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataSet> Bir tutarlı ilişkisel programlama modeli bağımsız veri kaynağının sağlayan veri bellekte gösterimidir. `DataSet` Tabloları, kısıtlamalar ve tablolar arasında ilişkiler içeren verileri eksiksiz bir kümesini temsil eder. Çünkü `DataSet` veri kaynağı, bağımsız bir `DataSet` verileri uygulamaya yerel ve birden çok veri kaynaklarından verileri içerebilir. Mevcut veri kaynakları ile etkileşim aracılığıyla denetlenir `DataAdapter`.  
  
 `SelectCommand` Özelliği `DataAdapter` olan bir `Command` veri kaynağından veri alır nesnesi. `InsertCommand`, `UpdateCommand`, Ve `DeleteCommand` özelliklerini `DataAdapter` olan `Command` verilerde yapılan değişikliklere göre veri kaynağındaki verileri yapılan güncelleştirmeleri yönetebilirsiniz nesneleri `DataSet`. Bu özellikleri daha ayrıntılı olarak ele alınmaktadır [veri kaynaklarıyla güncelleştirme DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 `Fill` Yöntemi `DataAdapter` doldurmak için kullanılan bir `DataSet` sonuçlarını içeren `SelectCommand` , `DataAdapter`. `Fill` kendi bağımsız değişkenleri olarak alır bir `DataSet` doldurulması için ve bir `DataTable` nesne veya adını `DataTable` döndürülen satır ile doldurulacak `SelectCommand`.  
  
> [!NOTE]
>  Kullanarak `DataAdapter` özellikle tablodaki satır sayısını varsa tüm bir tabloyu alır süreyi almak için. Bulma ve verileri işlerken veritabanına erişirken çünkü ve sonra istemci için verileri aktarma zaman alır. Tüm tablonun istemciye çekme sunucusunda tüm satırların kilitler. Performansı artırmak için kullanabileceğiniz `WHERE` istemciye döndürülen satır sayısını önemli ölçüde azaltan yan tümcesi. Yalnızca açıkça gerekli sütunlarda listeleyerek istemciye döndürülen veri miktarını da azaltabilir `SELECT` deyimi. Gruplar halinde (örneğin, bir seferde birkaç yüz satırlar) satırları alma ve istemci ile geçerli toplu işlem tamamlandığında sonraki yalnızca almak için başka bir iyi geçici bir çözüm değildir.  
  
 `Fill` Yöntemi kullanan `DataReader` sütun adlarının ve tablo oluşturmak için kullanılan türler örtük olarak döndürülecek nesne `DataSet`ve tablo satırları doldurmak için veri `DataSet`. Zaten mevcut değilse tablolar ve sütunlar yalnızca oluşturulur; Aksi takdirde `Fill` varolan kullanan `DataSet` şema. Sütun türleri olarak oluşturulan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] tablolarda göre türleri [ADO.NET veri türü eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md). Birincil anahtarları veri kaynağında mevcut sürece oluşturulmaz ve `DataAdapter` **.**`MissingSchemaAction` ayarlanmış `MissingSchemaAction` **.** `AddWithKey`. Varsa `Fill` bulur bir tablo için birincil anahtar varsa, veri üzerine yazar `DataSet` veri kaynağından döndürülen birincil anahtar sütun değerleri eşleştiği bu satırın satırlar için veri kaynağı ile. Birincil anahtar bulunursa, veri tablolarında eklenir `DataSet`. `Fill` doldurma sırasında oluşabilecek tüm eşlemeleri kullanan `DataSet` (bkz [DataAdapter DataTable ve DataColumn eşlemeleri](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
>  Varsa `SelectCommand` bir dış birleşim, sonuçlarını döndürür `DataAdapter` ayarlı değil bir `PrimaryKey` elde edilen değer `DataTable`. Tanımlamanız gerekir `PrimaryKey` kendinize yinelenen satırları düzgün olarak çözülen emin olun. Daha fazla bilgi için bkz: [tanımlama birincil anahtarlar](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Aşağıdaki kod örneğinde bir örneğini oluşturur bir <xref:System.Data.SqlClient.SqlDataAdapter> kullanan bir <xref:System.Data.SqlClient.SqlConnection> Microsoft SQL Server `Northwind` veritabanı ve dolduran bir <xref:System.Data.DataTable> içinde bir `DataSet` müşterilerin listesi ile. SQL deyimi ve <xref:System.Data.SqlClient.SqlConnection> bağımsız değişkenleri geçirilen <xref:System.Data.SqlClient.SqlDataAdapter> oluşturmak için kullanılan Oluşturucu <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> özelliği <xref:System.Data.SqlClient.SqlDataAdapter>.  
  
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
>  Bu örnekte gösterilen kodu açıkça açılmaz ve Kapat `Connection`. `Fill` Yöntemi örtük olarak açılır `Connection` , `DataAdapter` bağlantı zaten açık olduğunu bulursa kullanıyor. Varsa `Fill` bağlantısı açıldığı de bağlantıyı kapatır zaman `Fill` tamamlandı. Tek bir işlemle gibi dağıttığınızda bu kodunuzu kolaylaştırabilir bir `Fill` veya bir `Update`. Açık bir bağlantı gerektiren birden çok işlem gerçekleştiriyorsanız, ancak performansı, uygulamanızın açıkça çağırarak artırabilirsiniz `Open` yöntemi `Connection`, veri kaynağına karşı işlemlerini gerçekleştirme ve ardından çağırma `Close` yöntemi `Connection`. Veri kaynağı bağlantıları mümkün olduğunca kısa bir süre kullanmak için kaynakları serbest bırakmak için diğer istemci uygulamaları tarafından açık tutmak denemelisiniz.  
  
## <a name="multiple-result-sets"></a>Birden çok sonuç kümesi  
 Varsa `DataAdapter` karşılaştığı birden çok sonuç kümeleri, birden fazla tabloya oluşturur `DataSet`. Tabloları tablosunun bir artımlı varsayılan adı verilen*N*Table0 için "Tablo" ile başlayan. Bağımsız değişken olarak bir tablo adı geçip geçmediğini `Fill` yöntemi, tablolar TableName artımlı varsayılan adını verilmiştir*N*TableName0 için "TableName" ile başlayan.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Birden çok DataAdapters kümesinden doldurma  
 Herhangi bir sayıda `DataAdapter` nesneleri ile kullanılabilir bir `DataSet`. Her `DataAdapter` bir veya daha fazla doldurmak için kullanılan `DataTable` nesneleri ve çözümleme güncelleştirmeleri ilgili veri kaynağına yedekleyin. `DataRelation` ve `Constraint` nesneleri eklenebilir `DataSet` yerel olarak, farklı veri kaynaklarından veri ilişkili olanak sağlar. Örneğin, bir `DataSet` bir Microsoft SQL Server veritabanı, OLE DB ve XML akışları bir veri kaynağı kullanıma sunulan IBM DB2 veritabanına verileri içerebilir. Bir veya daha fazla `DataAdapter` nesneleri, her veri kaynağı iletişimi işleyebilir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde müşterilerden listesini doldurur `Northwind` Microsoft SQL Server veritabanı ve siparişleri listesini `Northwind` Microsoft Access 2000'de depolanan veritabanı. Doldurulmuş tablolar ile ilişkili bir `DataRelation`, müşterilerin listesini sonra o müşteri için siparişleri ile birlikte görüntülenir. Hakkında daha fazla bilgi için `DataRelation` nesneleri bkz [ekleme DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) ve [gezinme DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md).  
  
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
  
## <a name="sql-server-decimal-type"></a>SQL Server Decimal türü  
 Varsayılan olarak, `DataSet` kullanarak verileri depolayan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri türleri. Çoğu uygulama için bu veri kaynağı bilgileri kullanışlı bir gösterimini sağlar. Ancak, veri kaynağındaki veri türü bir SQL Server ondalık veya sayısal veri türü olduğunda bu gösterim bir soruna neden olabilir. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` Veri türü verir en fazla 28 önemli basamak, ancak SQL Server `decimal` veri türü 38 basamak sağlar. Varsa `SqlDataAdapter` sırasında belirler bir `Fill` işlemi, bir SQL Server'ın duyarlık `decimal` alandır 28 karakterden uzun, geçerli satır eklenmez `DataTable`. Bunun yerine `FillError` olayı oluşur, duyarlık kaybı oluşur ve uygun şekilde yanıt olup olmadığını belirlemenizi sağlar. Hakkında daha fazla bilgi için `FillError` olayı bkz [olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md). SQL sunucusu `decimal` değeri, ayrıca kullanabileceğiniz bir <xref:System.Data.SqlClient.SqlDataReader> nesne ve arama <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> yöntemi.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] sunulan 2.0 için gelişmiş destek <xref:System.Data.SqlTypes> içinde `DataSet`. Daha fazla bilgi için bkz: [SqlTypes ve veri kümesini](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>OLE DB bölümler  
 Hiyerarşik satır kümeleri veya bölümlerle (OLE DB türü `DBTYPE_HCHAPTER`, ADO türü `adChapter`) içeriğini doldurmak için kullanılan bir `DataSet`. Zaman <xref:System.Data.OleDb.OleDbDataAdapter> bölümlere sütun sırasında karşılaştığı bir `Fill` işlemi, bir `DataTable` bölümlere sütunu için oluşturulur ve bu tablo, bölüm satırları ve sütunları ile doldurulur. Üst tablo adı ve bölümlere sütun adı biçiminde kullanarak bölümlere sütun adlı için oluşturulan tablo "*ParentTableNameChapteredColumnName*". Bir tablo zaten varsa `DataSet` bölümlere sütunun adı ile eşleşen, geçerli tabloda bölüm verilerle doldurulur. Bölümde bulunan bir sütun eşleşen varolan bir tabloda sütun yok ise, yeni bir sütun eklenir.  
  
 Tablolarda önce `DataSet` doldurulur bölümlere sütunlardaki verilerle bir ilişkisi üst ve alt arasında tabloları hiyerarşik satır kümesinin üst ve alt tabloya bir tamsayı sütunu ekleyerek üst sütun ayarını oluşturulur otomatik artış ve oluşturma bir `DataRelation` eklenen sütunları her iki tablodan kullanarak. Form üst tablo ve bölüm sütun adlarını kullanarak eklenen ilişkisi adlı "*ParentTableNameChapterColumnName*".  
  
 Bulunmaktadır yalnızca ilgili sütunu Not `DataSet`. Veri kaynağından sonraki dolgular varolan satırlara birleştirilen değişiklikleri yerine tablolara eklenecek yeni satırlar neden olabilir.  
  
 Kullanırsanız, ayrıca `DataAdapter.Fill` alan aşırı bir `DataTable`, yalnızca o tabloyu doldurulur. Bir otomatik artan tamsayı sütunu yine tabloya eklenecek olan ancak hiçbir alt tablo oluşturulan veya doldurulmuş ve hiçbir ilişkisi oluşturulur.  
  
 Aşağıdaki örnek MSDataShape sağlayıcı siparişleri her müşteri için bir bölüm sütununa müşterilerin listesini oluşturmak için kullanır. A `DataSet` sonra verilerle doldurulur.  
  
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
  
 Zaman `Fill` işlemi tamamlandığında, `DataSet` iki tablo içerir: `Customers` ve `CustomersOrders`, burada `CustomersOrders` bölümlere sütunu temsil eder. Adlı ek bir sütun `Orders` eklenen `Customers` tablo ve adlı ek bir sütun `CustomersOrders` eklenen `CustomersOrders` tablo. `Orders` Sütununda `Customers` tablo otomatik artım ayarlanır. A `DataRelation`, `CustomersOrders`, tablolarla eklenme sütunları kullanılarak oluşturulan `Customers` üst tablo olarak. Aşağıdaki tabloda bazı örnek sonuçları gösterir.  
  
### <a name="tablename-customers"></a>TableName: müşteriler  
  
|CustomerID|CompanyName|Siparişleri|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Ana Trujillo Emparedados y helados|1.|  
  
### <a name="tablename-customersorders"></a>TableName: CustomersOrders  
  
|CustomerID|OrderID|CustomersOrders|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1.|  
|ANATR|10625|1.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [ADO.NET’te Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [DbDataAdapter ile Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [Birden Çok Etkin Sonuç Kümesi (MARS)](../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
