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
# <a name="populating-a-dataset-from-a-dataadapter"></a>DataAdapter’dan bir DataSet Doldurma
ADO.NET, <xref:System.Data.DataSet> veri kaynağından bağımsız tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir temsilidir. Tablolar, `DataSet` kısıtlamalar ve tablolar arasındaki ilişkileri içeren tam bir veri kümesini temsil eder. Veri `DataSet` kaynağından bağımsız olduğundan, `DataSet` uygulamanın yerel verilerini ve birden çok veri kaynağından gelen verileri içerebilir. Mevcut veri kaynakları `DataAdapter`ile etkileşim .  
  
 Özelliği, `SelectCommand` veri `DataAdapter` kaynağından veri alan bir `Command` nesnedir. , `InsertCommand` `UpdateCommand`, `DeleteCommand` ve özellikleri `DataAdapter` `Command` veri kaynağındaki verilerde yapılan değişikliklere göre veri güncelleştirmeleri yönetmek `DataSet`nesnelerdir. Bu özellikler, [DataAdapters ile Veri Kaynaklarının Güncelleştirilmesi](updating-data-sources-with-dataadapters.md)nde daha ayrıntılı olarak ele alınmıştır.  
  
 `DataAdapter` Yöntem `Fill` a sonuçları `DataSet` `SelectCommand` ile doldurmak için `DataAdapter`kullanılır. `Fill`onun bağımsız değişkenleri olarak alır `DataSet` a `DataTable` doldurulur ve bir `DataTable` nesne, ya da satırlar `SelectCommand`döndürülen ile doldurulacak adı .  
  
> [!NOTE]
> Bir `DataAdapter` tablonun tümünün alınmasını kullanmak zaman alır, özellikle de tabloda çok sayıda satır varsa. Bunun nedeni, veritabanına erişme, verileri bulma ve işleme ve ardından verileri istemciye aktarmanın zaman alan olmasıdır. Tüm tabloyu istemciye çekmek de sunucudaki tüm satırları kilitler. Performansı artırmak için, istemciye döndürülen satır sayısını büyük ölçüde azaltmak için `WHERE` yan tümceyi kullanabilirsiniz. Ayrıca, `SELECT` bildirimde yalnızca gerekli sütunları açıkça listeleyerek istemciye döndürülen veri miktarını da azaltabilirsiniz. Başka bir iyi geçici çözüm toplu olarak satırları almaktır (bir seferde birkaç yüz satır gibi) ve yalnızca istemci geçerli toplu iş ile tamamlandığında sonraki toplu almak.  
  
 Yöntem, `Fill` sütun `DataReader` adlarını ve tablolar `DataSet`oluşturmak için kullanılan türleri döndürmek için nesneyi zımni olarak kullanır ve tablolardaki satırları `DataSet`doldurmak için verileri. Tablolar ve sütunlar yalnızca zaten yoksa oluşturulur; aksi `Fill` takdirde `DataSet` varolan şema kullanır. Sütun [türleri, ADO.NET'daki Veri Türü Eşlemeleri'ndeki](data-type-mappings-in-ado-net.md)tablolara göre .NET Framework türleri olarak oluşturulur. Birincil anahtarlar, veri kaynağında `DataAdapter`ve **.**`MissingSchemaAction` olarak `MissingSchemaAction` **ayarlanır.** `AddWithKey`. Bir `Fill` tablo için birincil anahtarın var olduğunu bulursa, `DataSet` birincil anahtar sütun değerlerinin veri kaynağından döndürülen satırlarla eşleştiği satırlar için veri kaynağındaki verilerle birlikte verilerin üzerine yazılır. Birincil anahtar bulunamazsa, veriler `DataSet`. `Fill`doldurduğunuzda var olabilecek tüm eşlemeleri kullanır `DataSet` (bkz. [DataAdapter DataTable ve DataColumn Eşlemeleri).](dataadapter-datatable-and-datacolumn-mappings.md)  
  
> [!NOTE]
> Bir `SelectCommand` OUTER JOIN sonuçlarını döndürürse, `DataAdapter` `PrimaryKey` elde edilen `DataTable`değer için bir değer belirlemez. Yinelenen satırların `PrimaryKey` doğru şekilde çözüldüğünden emin olmak için kendinizi tanımlamanız gerekir. Daha fazla bilgi için [Bkz. Birincil Anahtarları Tanımlama.](./dataset-datatable-dataview/defining-primary-keys.md)  
  
 Aşağıdaki kod örneği, Microsoft SQL <xref:System.Data.SqlClient.SqlDataAdapter> Server <xref:System.Data.SqlClient.SqlConnection> `Northwind` veritabanında a kullanan bir örnek <xref:System.Data.DataTable> oluşturur `DataSet` ve bir müşteri listesiyle bir'de doldurulur. SQL deyimi <xref:System.Data.SqlClient.SqlConnection> ve <xref:System.Data.SqlClient.SqlDataAdapter> kurucuya geçirilen bağımsız <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter>değişkenler.  
  
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
> Bu örnekte gösterilen kod açıkça açılmıyor `Connection`ve . Yöntem, `Fill` bağlantının `Connection` `DataAdapter` zaten açık olmadığını bulursa, kullandığı yöntemi dolaylı olarak açar. Bağlantıyı `Fill` açtıysanız, tamamlandığında da bağlantıyı `Fill` kapatır. Bu, bir veya bir `Fill` `Update`. Ancak, açık bağlantı gerektiren birden çok işlem gerçekleştiriyorsanız, veri kaynağına karşı `Open` işlemleri gerçekleştiren `Connection`ve daha sonra yöntemin isini `Close` çağırarak `Connection`uygulamanızın performansını artırabilirsiniz. Diğer istemci uygulamaları tarafından kullanılmak üzere kaynakları serbest tutmak için veri kaynağına bağlantıları mümkün olduğunca kısa bir süre açık tutmaya çalışmalısınız.  
  
## <a name="multiple-result-sets"></a>Birden Fazla Sonuç Kümesi  
 Birden `DataAdapter` çok sonuç kümesiyle karşılaşırsa, `DataSet`'de birden çok tablo oluşturur. Tablolara Tablo0 için "Tablo" ile başlayarak Tablo*N'nin*artımlı varsayılan adı verilir. Bir tablo adı `Fill` yönteme bağımsız değişken olarak aktarılırsa, tablolara TableName0 için "TableName" ile başlayarak Tablo Adı*N'nin*artımlı varsayılan adı verilir.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Birden Çok DataAdapters'dan Bir DataSet Doldurma  
 Herhangi bir `DataAdapter` sayıda nesne bir `DataSet`. Her `DataAdapter` biri bir veya daha `DataTable` fazla nesneyi doldurmak ve güncelleştirmeleri ilgili veri kaynağına geri çözmek için kullanılabilir. `DataRelation`ve `Constraint` nesneler `DataSet` yerel olarak eklenebilir, bu da farklı veri kaynaklarından gelen verileri ilişkilendirmenizi sağlar. Örneğin, bir `DataSet` Microsoft SQL Server veritabanından, OLE DB aracılığıyla açığa çıkarılan bir IBM DB2 veritabanından ve XML akışı yapan bir veri kaynağından veri içerebilir. Bir veya `DataAdapter` daha fazla nesne her veri kaynağına iletişimi işleyebilir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, Microsoft SQL Server'daki `Northwind` veritabanındaki müşterilerin listesini ve Microsoft `Northwind` Access 2000'de depolanan veritabanından gelen siparişlerin listesini doldurur. Doldurulan tablolar bir `DataRelation`,, ve müşteri listesi ile ilgili daha sonra bu müşteri için siparişler ile görüntülenir. Nesneler hakkında `DataRelation` daha fazla bilgi için [Navigating DataRelations](./dataset-datatable-dataview/navigating-datarelations.md) [bkz.](./dataset-datatable-dataview/adding-datarelations.md)  
  
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
  
## <a name="sql-server-decimal-type"></a>SQL Server Ondalık Yazı  
 Varsayılan olarak, `DataSet` .NET Framework veri türlerini kullanarak verileri depolar. Çoğu uygulama için bunlar veri kaynağı bilgilerinin uygun bir temsilini sağlar. Ancak, veri kaynağındaki veri türü SQL Server ondalık veya sayısal veri türü olduğunda bu gösterim bir soruna neden olabilir. .NET Framework `decimal` veri türü en fazla 28 önemli basamak sağlarken, SQL Server `decimal` veri türü 38 önemli basamak sağlar. Bir `SqlDataAdapter` işlem sırasında `Fill` sql server `decimal` alanının kesinliği 28 karakterden büyük olduğunu belirlerse, `DataTable`geçerli satır . Bunun `FillError` yerine olay oluşur, bu da bir kesinlik kaybı oluşup oluşmayacağını belirlemenize ve uygun şekilde yanıt vermenize olanak tanır. `FillError` Olay hakkında daha fazla bilgi için [DataAdapter Olaylarını Işleme](handling-dataadapter-events.md)konusuna bakın. SQL Server `decimal` değerini almak için bir <xref:System.Data.SqlClient.SqlDataReader> nesne kullanabilir <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> ve yöntemi çağırabilirsiniz.  
  
 ADO.NET 2.0 için <xref:System.Data.SqlTypes> geliştirilmiş destek `DataSet`tanıttı. Daha fazla bilgi için [SqlTypes ve DataSet'e](./sql/sqltypes-and-the-dataset.md)bakın.  
  
## <a name="ole-db-chapters"></a>OLE DB Bölümleri  
 Hiyerarşik satır kümeleri veya bölümler (OLE DB türü `DBTYPE_HCHAPTER`, ADO türü) `adChapter`bir `DataSet`. İşlem <xref:System.Data.OleDb.OleDbDataAdapter> sırasında `Fill` bölümlere alınan bir sütunla `DataTable` karşılaştığında, bölümlere alınan sütun için bir sütun oluşturulur ve bu tablo bölümdeki sütun ve satırlarla doldurulur. Bölümlenmiş sütun için oluşturulan tablo, hem ana tablo adı hem de "*ParentTableNameChapteredColumnName*" şeklindeki bölümlenmiş sütun adı kullanılarak adlandırılır. Bölümlenmiş sütunun `DataSet` adıyla eşleşen tablo zaten varsa, geçerli tablo bölüm verileriyle doldurulur. Varolan bir tabloda bölümde bulunan sütunla eşleşen bir sütun yoksa, yeni bir sütun eklenir.  
  
 Bölümlerdeki `DataSet` tablolar bölümlere aktarılmış sütunlarda verilerle doldurulmadan önce, üst ve alt tabloya bir tamsayı sütunu ekleyerek, üst sütunu otomatik artışa ayarlayarak ve her iki `DataRelation` tablodan eklenen sütunlar kullanılarak hiyerarşik satır kümesinin üst ve alt tabloları arasında bir ilişki oluşturulur. Eklenen ilişki , "*ParentTableNameChapterColumnName*" şeklindeki ana tablo ve bölüm sütun adları kullanılarak adlandırılır.  
  
 İlgili sütunun yalnızca `DataSet`. Veri kaynağından sonraki dolgular, varolan satırlarla birleştirilen değişiklikler yerine tablolara yeni satırlar eklenmesine neden olabilir.  
  
 Ayrıca, bir `DataAdapter.Fill` `DataTable`alır aşırı yük kullanırsanız, sadece bu tablo nun doldurulacağını unutmayın. Otomatik artışlı bir insa sütunu yine de tabloya eklenir, ancak alt tablo oluşturulmaz veya doldurulmaz ve ilişki oluşturulmaz.  
  
 Aşağıdaki örnek, müşteri listesindeki her müşteri için bir sipariş bölümü sütunu oluşturmak için MSDataShape Sağlayıcı'yı kullanır. A `DataSet` daha sonra verilerle doldurulur.  
  
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
  
 `Fill` İşlem tamamlandığında, iki `DataSet` tablo içerir: `Customers` `CustomersOrders`ve `CustomersOrders` , burada bölümlü sütun temsil eder. Tabloya `Orders` `Customers` adlandırılmış ek bir sütun eklenir ve `CustomersOrders` tabloya `CustomersOrders` adlandırılmış ek bir sütun eklenir. Tablodaki `Orders` `Customers` sütun otomatik artış ayarı. A `DataRelation` `CustomersOrders`, , üst tablo `Customers` olarak tablolara eklenen sütunlar kullanılarak oluşturulur. Aşağıdaki tablolar bazı örnek sonuçları gösterir.  
  
### <a name="tablename-customers"></a>Masa Adı: Müşteriler  
  
|CustomerID|CompanyName|Siparişler|  
|----------------|-----------------|------------|  
|Alfkı|Alfreds Futterkiste|0|  
|ANATR|Ana Trujillo Emparedados y helados|1|  
  
### <a name="tablename-customersorders"></a>Tablo Adı: Müşteri Siparişleri  
  
|CustomerID|OrderID|Müşteri Siparişleri|  
|----------------|-------------|---------------------|  
|Alfkı|10643|0|  
|Alfkı|10692|0|  
|ANATR|10308|1|  
|ANATR|10625|1|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](dataadapters-and-datareaders.md)
- [ADO.NET’te Veri Türü Eşlemeleri](data-type-mappings-in-ado-net.md)
- [DbDataAdapter ile Verileri Değiştirme](modifying-data-with-a-dbdataadapter.md)
- [Birden Çok Etkin Sonuç Kümesi (MARS)](./sql/multiple-active-result-sets-mars.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
