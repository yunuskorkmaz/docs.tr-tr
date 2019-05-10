---
title: DataAdapter’dan bir DataSet Doldurma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: 0d9f349bf4e7e2a2a698dc988e5c366291169200
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211441"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>DataAdapter’dan bir DataSet Doldurma
[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataSet> Sağlayan bir tutarlı ilişkisel programlama modeli bağımsız veri kaynağının veri bellekte gösterimidir. `DataSet` Tablolar, kısıtlamalar ve tablolar arasındaki ilişkileri içeren verileri eksiksiz bir kümesini temsil eder. Çünkü `DataSet` veri kaynağını, bağımsız bir `DataSet` uygulamaya yerel veri ve birden çok veri kaynaklarından alınan verileri içerebilir. Mevcut veri kaynaklarıyla etkileşim aracılığıyla denetlenir `DataAdapter`.  
  
 `SelectCommand` Özelliği `DataAdapter` olduğu bir `Command` nesnesini, veri kaynağından veri alır. `InsertCommand`, `UpdateCommand`, Ve `DeleteCommand` özelliklerini `DataAdapter` olan `Command` verilerde yapılan değişiklikleri göre veri kaynağındaki verileri güncellemelerini yönetmelerini nesneleri `DataSet`. Bu özellikleri daha ayrıntılı olarak ele alınmaktadır [güncelleştirme veri kaynaklarını DataAdapters ile](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 `Fill` Yöntemi `DataAdapter` doldurmak için kullanılan bir `DataSet` sonuçlarını içeren `SelectCommand` , `DataAdapter`. `Fill` bağımsız değişkenler olarak alır bir `DataSet` doldurulması için ve bir `DataTable` nesne veya adını `DataTable` döndürülen satırlar ile doldurulacak `SelectCommand`.  
  
> [!NOTE]
>  Kullanarak `DataAdapter` özellikle tabloda birçok satır varsa her bir tablo tarafından gerçekleştirilen işlemlerin zaman alınamıyor. Bunun nedeni, bulma ve veri işleme veritabanına erişirken, ve ardından istemciye veri aktarma işlemdir. Tüm tablonun istemciye çekme sunucusunda tüm satırların kilitler. Performansı artırmak için kullanabileceğiniz `WHERE` satır sayısı büyük ölçüde azaltmak için yan tümcesi istemciye döndürülen. Ayrıca gerekli sütunlarda yalnızca açıkça listeleyerek istemciye döndürülen veri miktarını azaltabilirsiniz `SELECT` deyimi. Gruplar halinde (örneğin, aynı anda birkaç yüz satır) satırları alma ve istemci ile geçerli toplu işlem sona erdiğinde yalnızca sonraki almak başka bir iyi çözüm olabilir.  
  
 `Fill` Yöntemi kullanan `DataReader` içinde tablolar oluşturmak için kullanılan türleri ve sütun adları örtük olarak döndürülecek nesne `DataSet`ve tablo satırları doldurmak için veri `DataSet`. Tablolar ve sütunlar zaten mevcut değilse yalnızca oluşturulur; Aksi takdirde `Fill` varolan kullanan `DataSet` şema. Sütun türleri olarak oluşturulan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] türlerine göre tablolarında [ADO.NET'te veri türü eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md). Birincil anahtarları, veri kaynağında oldukları sürece oluşturulmaz ve `DataAdapter` **.**`MissingSchemaAction` ayarlanır `MissingSchemaAction` **.** `AddWithKey`. Varsa `Fill` bulur bir tablo için birincil anahtar varsa, verileri üzerine yazar `DataSet` birincil anahtar sütun değerleri eşleştiği bu satırın satırlar için veri kaynağı veri kaynağından döndürdü. Birincil anahtar bulunursa, veri tablolarında eklenir `DataSet`. `Fill` kullanır, doldurmanız oluşabilecek tüm eşlemeleri `DataSet` (bkz [DataAdapter DataTable ve DataColumn eşlemeleri](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
>  Varsa `SelectCommand` bir dış birleştirme, sonuçlarını döndürür `DataAdapter` ayarlı değil bir `PrimaryKey` elde edilen değer `DataTable`. Tanımlamanız gerekir `PrimaryKey` kendinize yinelenen satırları düzgün şekilde çözümlendiğinden emin emin olun. Daha fazla bilgi için [birincil anahtarlar tanımlama](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Aşağıdaki kod örneği bir örneğini oluşturur bir <xref:System.Data.SqlClient.SqlDataAdapter> kullanan bir <xref:System.Data.SqlClient.SqlConnection> Microsoft SQL Server `Northwind` doldurur ve veritabanı bir <xref:System.Data.DataTable> içinde bir `DataSet` müşteriler listesi. SQL deyimi ve <xref:System.Data.SqlClient.SqlConnection> geçirilen bağımsız değişkenler <xref:System.Data.SqlClient.SqlDataAdapter> oluşturmak için kullanılan Oluşturucu <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> özelliği <xref:System.Data.SqlClient.SqlDataAdapter>.  
  
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
>  Bu örnekte gösterilen kodu açıkça açılmaz ve Kapat `Connection`. `Fill` Yöntemi örtülü olarak açılır `Connection` , `DataAdapter` bağlantı zaten açık değilse, bulursa kullanıyor. Varsa `Fill` bağlantısı açılır de bağlantıyı kapatır, `Fill` tamamlandı. Tek bir işlemle gibi dağıttığınızda bu kodunuzu basitleştirebilirsiniz bir `Fill` veya `Update`. Açık bir bağlantı gerektiren birden çok işlem gerçekleştiriyorsanız, ancak performansı, uygulamanızın açıkça çağrılarak artırabilirsiniz `Open` yöntemi `Connection`, veri kaynağına karşı işlemleri gerçekleştirmeye ve ardından arama `Close` yöntemi `Connection`. Veri kaynağı bağlantıları mümkün olduğunca kısa bir süreliğine ücretsiz kaynakları kullanmak için diğer istemci uygulamalar tarafından açık tutun çalışmanız gerekir.  
  
## <a name="multiple-result-sets"></a>Birden çok sonuç kümesi  
 Varsa `DataAdapter` karşılaştığı birden çok sonuç kümesi, birden çok tablodan oluşturur `DataSet`. Tabloları tablosunun bir artımlı varsayılan adı verilen*N*Table0 için "Tablo" ile başlayan. Bağımsız değişkeni olarak bir tablo adı geçip geçmediğini `Fill` yöntemi, tabloları TableName bir artımlı varsayılan adı verilir*N*TableName0 için "TableName" ile başlayan.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Birden çok DataAdapters kümesinden doldurma  
 Herhangi bir sayıda `DataAdapter` nesneleri ile kullanılabilir bir `DataSet`. Her `DataAdapter` bir veya daha fazla doldurmak için kullanılan `DataTable` nesneleri ve çözümle güncelleştirmeleri ilgili veri kaynağına geri. `DataRelation` ve `Constraint` nesneler eklenebilir `DataSet` yerel olarak sağlayan farklı veri kaynaklarından alınan verileri ilişkilendirmek. Örneğin, bir `DataSet` , OLE DB ve XML akışı veri kaynağı kullanıma sunulan bir IBM DB2 veritabanı Microsoft SQL Server veritabanından veri içerebilir. Bir veya daha fazla `DataAdapter` nesneleri, her veri kaynağı iletişimi işleyebilir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, müşterilerin listesini doldurur `Northwind` Microsoft SQL Server veritabanı ve Sipariş listesini `Northwind` Microsoft Access 2000'de depolanan veritabanı. Doldurulmuş tabloları ile ilişkili bir `DataRelation`, müşterilerin listesini daha sonra bu müşterinin siparişlerine ile birlikte görüntülenir. Hakkında daha fazla bilgi için `DataRelation` nesneleri bkz [DataRelations ekleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) ve [gezinme DataRelations](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md).  
  
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
 Varsayılan olarak, `DataSet` kullanarak verilerini depolayan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] veri türleri. Çoğu uygulama için bu veri kaynağı bilgilerini kullanışlı bir gösterimini sağlar. Ancak, veri kaynağındaki veri türü bir SQL Server ondalık veya sayısal veri türü olduğunda bu gösterim bir soruna neden olabilir. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] `decimal` Veri türü 28 önemli basamaklarının maksimum sağlar ancak SQL Server `decimal` veri türü 38 basamak sağlar. Varsa `SqlDataAdapter` sırasında belirler bir `Fill` işlemi, bir SQL Server'ın duyarlık `decimal` alan 28 karakterden daha büyük, geçerli satır eklenmez `DataTable`. Bunun yerine `FillError` bir olay oluşursa, kesinlik kaybı oluşur ve uygun şekilde yanıt olup olmadığını belirlemenize olanak sağlar. Hakkında daha fazla bilgi için `FillError` olay bkz [DataAdapter olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md). SQL Server'ı almak için `decimal` değeri, ayrıca kullanabileceğiniz bir <xref:System.Data.SqlClient.SqlDataReader> nesne ve çağrı <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> yöntemi.  
  
 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] tanıtılan 2.0 için gelişmiş destek <xref:System.Data.SqlTypes> içinde `DataSet`. Daha fazla bilgi için [SqlTypes ve DataSet](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>OLE DB bölüm  
 Hiyerarşik satır kümeleri ya da bölümlerini (OLE DB türü `DBTYPE_HCHAPTER`, ADO türü `adChapter`) içeriğini doldurmak için kullanılan bir `DataSet`. Zaman <xref:System.Data.OleDb.OleDbDataAdapter> sırasında bölümlere sütun karşılaştığında bir `Fill` işlemi, bir `DataTable` bölümlere sütunun oluşturulur ve bu tablo, bölüm satırları ve sütunları ile doldurulur. Hem üst tablo adını hem de bölümlere sütun adı biçiminde kullanılarak bölümlere sütun adlı için oluşturulan tabloyu "*ParentTableNameChapteredColumnName*". Bir tablo zaten varsa `DataSet` bölümlere sütunun adı ile eşleşen, geçerli tablonun bölüm verilerle doldurulur. Varolan tablodaki bir sütun bölümde bulunan eşleşen hiçbir sütun yoksa, yeni bir sütun eklenir.  
  
 Tablolardaki önce `DataSet` doldurulur bölümlere sütunlardaki verileri ile bir ilişki üst ve alt hiyerarşik kümesi tabloları üst ve alt tablo için bir tamsayı sütunu ekleyerek üst sütun ayarını oluşturulur otomatik artış ve oluşturma bir `DataRelation` eklenen her iki tablonun sütunlarından kullanarak. Eklenen ilişki biçiminde üst tablo ve bölüm sütun adlarını kullanarak adlı "*ParentTableNameChapterColumnName*".  
  
 Bulunmaktadır yalnızca ilgili sütunda Not `DataSet`. Veri kaynağından alınan sonraki dolgular, var olan satırları birleştirilen değişiklikler yerine tablolara eklenecek yeni satırlar neden olabilir.  
  
 Kullanırsanız, ayrıca unutmayın `DataAdapter.Fill` alan aşırı yüklemesini bir `DataTable`, yalnızca bu tabloyu doldurulur. Otomatik artan bir tamsayı sütunu tabloya hala eklenir ancak hiçbir alt tablo oluşturulacak veya doldurulmuş ve hiçbir ilişkisi oluşturulur.  
  
 Aşağıdaki örnek, bir bölüm sütunu her müşteriye ait siparişlerin müşterilerin listesini oluşturmak için MSDataShape sağlayıcısı kullanır. A `DataSet` ardından verilerle doldurulur.  
  
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
  
 Zaman `Fill` işlemi tamamlandıktan sonra `DataSet` iki tablo içerir: `Customers` ve `CustomersOrders`burada `CustomersOrders` bölümlere sütunu temsil eder. Adlı ek bir sütun `Orders` eklenir `Customers` tablo ve adlı ek bir sütun `CustomersOrders` eklenir `CustomersOrders` tablo. `Orders` Sütununda `Customers` tablo otomatik artacak şekilde ayarlayın. A `DataRelation`, `CustomersOrders`, tablolarla eklenen sütunları kullanılarak oluşturulan `Customers` üst tablo olarak. Aşağıdaki tabloda bazı örnek sonuçları gösterir.  
  
### <a name="tablename-customers"></a>TableName: Müşteriler  
  
|CustomerID|CompanyName|Siparişler|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkiste|0|  
|ANATR|Ana Trujillo Emparedados y helados|1.|  
  
### <a name="tablename-customersorders"></a>TableName: CustomersOrders  
  
|CustomerID|Sipariş Kimliği|CustomersOrders|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1.|  
|ANATR|10625|1.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [ADO.NET’te Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [DbDataAdapter ile Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [Birden Çok Etkin Sonuç Kümesi (MARS)](../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
