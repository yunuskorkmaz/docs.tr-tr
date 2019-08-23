---
title: DataAdapter’dan bir DataSet Doldurma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3fa0ac7d-e266-4954-bfac-3fbe2f913153
ms.openlocfilehash: 5e86eb4c37d20be53d271aba9f4913f2eeccd923
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928340"
---
# <a name="populating-a-dataset-from-a-dataadapter"></a>DataAdapter’dan bir DataSet Doldurma
ADO.net <xref:System.Data.DataSet> , veri kaynağından bağımsız tutarlı bir ilişkisel programlama modeli sağlayan verilerin bellekte yerleşik bir gösterimidir. , `DataSet` Tablolar arasındaki tabloları, kısıtlamaları ve ilişkileri içeren tüm veri kümesini temsil eder. , Veri kaynağından bağımsız olduğundan, bir `DataSet` uygulamaya yerel veri ve birden çok veri kaynağından veri içerebilir. `DataSet` Mevcut veri kaynaklarıyla etkileşim aracılığıyla `DataAdapter`denetlenir.  
  
 Öğesinin özelliği, veri kaynağından veri `Command` alan bir nesnedir. `SelectCommand` `DataAdapter` `InsertCommand` ,Ve`DeleteCommand` özellikleri `Command` ,içindeki`DataSet`verilerde yapılan değişikliklere göre veri kaynağındaki verilerle ilgili güncelleştirmeleri yöneten nesnelerdir.`DataAdapter` `UpdateCommand` Bu özellikler, [veri kaynaklarını DataAdapter Ile güncelleştirme konusunda](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)daha ayrıntılı olarak ele alınmıştır.  
  
 `Fill` Yöntemi `DataSet` ,öğesinin`DataAdapter`sonuçlarıyla birlikte`SelectCommand` doldurmak için kullanılır. `DataAdapter` `Fill`, `DataSet` `DataTable` `DataTable` ' nin doldurulduğu bağımsız değişkenlerini, bir nesnesini veya ' den döndürülen satırlarla doldurulacak olan adını alır. `SelectCommand`  
  
> [!NOTE]
> Bir tablonun tümünü almak içinkullanılması,özellikletablodaçoksayıdasatırolmasıdurumundazamanalır.`DataAdapter` Bunun nedeni, veritabanına erişmek, verileri bulmak ve işlemek ve sonra verilerin istemciye aktarılması zaman alır. Tüm tablosunun istemciye çekmeleri, sunucudaki tüm satırları da kilitler. Performansı artırmak için, `WHERE` yan tümcesini kullanarak istemciye döndürülen satır sayısını büyük ölçüde azaltabilirsiniz. Ayrıca, yalnızca `SELECT` deyimindeki gerekli sütunları açıkça listeleyerek istemciye döndürülen veri miktarını azaltabilirsiniz. Başka bir iyi geçici çözüm de satırları toplu olarak (örneğin, bir kerede birkaç yüz satır) almak ve yalnızca, geçerli toplu işlemle istemci tamamlandığında sonraki toplu işi almak içindir.  
  
 Yöntemi, içindeki tabloları `DataReader` `DataSet`oluşturmak için kullanılan sütun adlarını ve türlerini ve içindeki tabloların satırlarının `DataSet`doldurulmasıyla ilgili verileri döndürmek için nesneyi örtük olarak kullanır. `Fill` Tablolar ve sütunlar yalnızca henüz yoksa oluşturulur; Aksi `Fill` halde mevcut `DataSet` şemayı kullanır. Sütun türleri, [ADO.net Içindeki veri türü eşlemelerinde](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)bulunan tablolara göre .NET Framework türleri olarak oluşturulur. Birincil anahtarlar veri kaynağında `DataAdapter`yoksa oluşturulmaz **.** `MissingSchemaAction` , olarak `MissingSchemaAction`ayarlanır **.** `AddWithKey`. Bir tablonun birincil anahtarının mevcut olduğunu `DataSet` belirlerse,birincilanahtarsütundeğerlerininverikaynağındandöndürülensatırlaeşleştiğisatırlariçinverikaynağındakiverilerleveriüzerineyazar.`Fill` Birincil anahtar bulunamazsa, veriler içindeki `DataSet`tablolara eklenir. `Fill`' i doldurduğunuzda mevcut `DataSet` olabilecek eşlemeleri kullanır (bkz. [DataAdapter DataTable ve DataColumn Mappings](../../../../docs/framework/data/adonet/dataadapter-datatable-and-datacolumn-mappings.md)).  
  
> [!NOTE]
> , `SelectCommand` Bir dış birleştirmenin `DataAdapter` sonuçlarını döndürürse, sonuç `DataTable`için bir `PrimaryKey` değer yapmaz. Yinelenen satırların doğru bir `PrimaryKey` şekilde çözümlendiğini doğrulamak için kendinizi tanımlamanız gerekir. Daha fazla bilgi için bkz. [birincil anahtarları tanımlama](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md).  
  
 Aşağıdaki kod örneği, <xref:System.Data.SqlClient.SqlDataAdapter> bir <xref:System.Data.DataTable> ' ın, Microsoft SQL Server `Northwind` veritabanına <xref:System.Data.SqlClient.SqlConnection> kullanan bir örneğini oluşturur ve bir içinde `DataSet` bir ile birlikte, müşteriler listesiyle doldurur. Oluşturucuya geçirilen <xref:System.Data.SqlClient.SqlConnection> <xref:System.Data.SqlClient.SqlDataAdapter.SelectCommand%2A> <xref:System.Data.SqlClient.SqlDataAdapter>SQL deyimleri ve bağımsız değişkenler, öğesinin özelliğini oluşturmak için kullanılır. <xref:System.Data.SqlClient.SqlDataAdapter>  
  
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
> Bu örnekte gösterilen kod açık bir şekilde açılmaz ve kapatmaz `Connection`. Yöntemi, bağlantının zaten açık `Connection` olmadığını bulursa kullandığı öğesini örtülü olarak açar `DataAdapter`. `Fill` Bağlantı açıldıysa, tamamlandığında da `Fill` bağlantıyı kapatır. `Fill` Bu, `Fill` `Update`veya gibi tek bir işlemle uğraşdığınızda kodunuzun basitleşmesini sağlayabilir. Ancak, açık bir bağlantı gerektiren birden çok işlem gerçekleştiriyorsanız, ' `Open` `Connection`ın metodunu açıkça çağırarak ve veri kaynağına karşı işlemleri gerçekleştirerek uygulamanızın performansını geliştirebilirsiniz ve sonra `Close` yöntemini`Connection`çağırarak. Kaynakları diğer istemci uygulamalar tarafından kullanılmak üzere serbest bırakmak için veri kaynağına yönelik bağlantıları daha kısa sürede açık tutmaya çalışın.  
  
## <a name="multiple-result-sets"></a>Birden çok sonuç kümesi  
 Birden çok sonuç kümesiyle `DataSet` karşılaşırsa,içindebirdençoktablooluşturur.`DataAdapter` Tablolara, TABLE0 için "Table" ile başlayarak, tablo*N*' nin artımlı varsayılan adı verilir. Bir tablo adı `Fill` yöntemine bir bağımsız değişken olarak geçirilirse, tablolara TableName0 için "TableName" ile başlayarak TableName*N*artımlı varsayılan adı verilir.  
  
## <a name="populating-a-dataset-from-multiple-dataadapters"></a>Birden çok DataAdapter nesnesinden veri kümesini doldurma  
 Herhangi bir `DataAdapter` `DataSet`sayıda nesne, ile kullanılabilir. Her `DataAdapter` biri, bir veya daha fazla `DataTable` nesneyi doldurup güncelleştirmeleri ilgili veri kaynağına geri çözümlemek için kullanılabilir. `DataRelation`ve `Constraint` nesneler `DataSet` yerel olarak eklenebilir, bu da benzer veri kaynaklarından verileri ilişkilendirmenize olanak sağlar. Örneğin, bir `DataSet` Microsoft SQL Server veritabanından veri, OLE DB üzerinden sunulan bir IBM DB2 veritabanı ve XML akışı yapan bir veri kaynağı içerebilir. Bir veya daha `DataAdapter` fazla nesne, her bir veri kaynağıyla iletişimi işleyebilir.  
  
### <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, Microsoft SQL Server `Northwind` veritabanından bir müşteri listesini ve Microsoft Access 2000 ' de depolanan `Northwind` veritabanından alınan siparişlerin listesini doldurur. Doldurulmuş tablolar bir `DataRelation`ile ilgilidir ve müşteriler listesi bu müşterinin siparişleriyle birlikte görüntülenir. Nesneler hakkında `DataRelation` daha fazla bilgi için bkz. [DataRelation 'ı ekleme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/adding-datarelations.md) ve DataRelation 'ı [gezinme](../../../../docs/framework/data/adonet/dataset-datatable-dataview/navigating-datarelations.md).  
  
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
 Varsayılan olarak, .NET Framework `DataSet` veri türlerini kullanarak verileri depolar. Çoğu uygulama için, veri kaynağı bilgilerinin kullanışlı bir gösterimini sağlar. Ancak, veri kaynağındaki veri türü SQL Server Decimal veya numeric veri türü olduğunda bu gösterim soruna neden olabilir. .NET Framework `decimal` veri türü en fazla 28 önemli basamağa izin veriyor, ancak SQL Server `decimal` veri türü 38 önemli basamağa izin veriyor. Bir `SqlDataAdapter` `decimal` `DataTable`işlem sırasında, bir SQL Server alanının duyarlığının 28 karakterden daha büyük olduğunu belirlerse, geçerli satır öğesine eklenmez. `Fill` Bunun yerine, bir duyarlık kaybı olup olmadığını ve uygun şekilde yanıt verip vermeyeceğinizi belirlemenizi sağlayan olayoluşur.`FillError` `FillError` Olay hakkında daha fazla bilgi için bkz. [DataAdapter olaylarını işleme](../../../../docs/framework/data/adonet/handling-dataadapter-events.md). SQL Server `decimal` değerini almak için, bir <xref:System.Data.SqlClient.SqlDataReader> nesnesi de kullanabilir ve <xref:System.Data.SqlClient.SqlDataReader.GetSqlDecimal%2A> yöntemini çağırabilirsiniz.  
  
 ADO.NET 2,0, <xref:System.Data.SqlTypes> `DataSet`içinde için geliştirilmiş destek getirmiştir. Daha fazla bilgi için bkz. [SqlTypes ve DataSet](../../../../docs/framework/data/adonet/sql/sqltypes-and-the-dataset.md).  
  
## <a name="ole-db-chapters"></a>OLE DB bölümler  
 Hiyerarşik satır kümeleri veya bölümler (OLE DB türü `DBTYPE_HCHAPTER`, ADO türü `adChapter`), içeriğini `DataSet`dolduracak şekilde kullanılabilir. <xref:System.Data.OleDb.OleDbDataAdapter> Bir `DataTable` işlem sırasında bir bölümlenebilir sütun ile karşılaştığında, bölümlenebilir sütun için bir oluşturulur ve bu tablo, bölümün sütunları ve satırlarıyla doldurulur. `Fill` Bölümlendirilen sütun için oluşturulan tablo, hem üst tablo adı hem de "*Parenttablenamebölüteredcolumnname*" biçiminde bölümlendirilen sütun adı kullanılarak adlandırılır. İçinde, `DataSet` bölümlenebilir sütunun adıyla eşleşen bir tablo zaten varsa, geçerli tablo bölüm verileriyle doldurulur. Varolan bir tabloda, bölümde bulunan bir sütunla eşleşen bir sütun yoksa, yeni bir sütun eklenir.  
  
 İçindeki `DataSet` tablolar, bölümlenebilir sütunlardaki verilerle doldurulmadan önce hem üst hem de alt tabloya bir tamsayı sütunu ekleyerek hiyerarşik satır kümesinin üst ve alt tabloları arasında bir ilişki oluşturulur ve üst sütunu Her iki tablodan de eklenen sütunları `DataRelation` kullanarak otomatik artırma ve oluşturma. Eklenen ilişki, "*Parenttablenamecolumntercolumnname*" biçiminde üst tablo ve bölüm sütun adları kullanılarak adlandırılır.  
  
 İlgili sütunun içinde `DataSet`yalnızca bulunduğunu unutmayın. Veri kaynağından sonraki dolgular, varolan satırlarla birleştirilecek değişiklikler yerine tablolara yeni satırların eklenmesine neden olabilir.  
  
 Ayrıca, öğesini `DataAdapter.Fill` `DataTable`alan aşırı yüklemeyi kullanırsanız, yalnızca bu tablo doldurulacak şekilde aklınızda kalır. Tabloya otomatik artan tamsayı sütunu yine de eklenecek, ancak hiçbir alt tablo oluşturulmayacak ya da doldurulmayacak ve hiçbir ilişki oluşturulmayacak.  
  
 Aşağıdaki örnek, bir müşteriler listesindeki her müşteri için siparişlerin bir bölüm sütununu oluşturmak üzere MSDataShape sağlayıcısını kullanır. `DataSet` Daha sonra veriler ile doldurulur.  
  
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
  
 `CustomersOrders` `Customers` `CustomersOrders` İşlem tamamlandığında, iki tablo içerir:ve,buradabölümleyensütunutemsileder.`DataSet` `Fill` Tabloya adlı `Orders` ek bir sütun eklenir `CustomersOrders` `CustomersOrders` ve tabloya adlı ek bir sütun eklenir. `Customers` `Customers` Tablodaki sütun otomatik artış olarak ayarlanır. `Orders` ,, Üst tablo olarak bulunan `Customers` tablolara eklenen sütunlar kullanılarak oluşturulur. `CustomersOrders` `DataRelation` Aşağıdaki tablolarda bazı örnek sonuçlar gösterilmektedir.  
  
### <a name="tablename-customers"></a>TableName Müşterinizin  
  
|Ister|CompanyName|Siparişlerine|  
|----------------|-----------------|------------|  
|ALFKI|Alfreds Futterkte|0|  
|ANATR|Ana Trujillo Emparedaddos y Helados|1\.|  
  
### <a name="tablename-customersorders"></a>TableName Müşteri Sorleyicileri  
  
|Ister|Sipariş|Müşteri Sorleyicileri|  
|----------------|-------------|---------------------|  
|ALFKI|10643|0|  
|ALFKI|10692|0|  
|ANATR|10308|1\.|  
|ANATR|10625|1\.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [DataAdapters ve DataReaders](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [ADO.NET’te Veri Türü Eşlemeleri](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)
- [DbDataAdapter ile Verileri Değiştirme](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)
- [Birden Çok Etkin Sonuç Kümesi (MARS)](../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)
- [ADO.NET yönetilen sağlayıcılar ve veri kümesi Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
