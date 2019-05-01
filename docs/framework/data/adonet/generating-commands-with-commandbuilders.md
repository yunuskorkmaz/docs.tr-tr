---
title: CommandBuilders ile Komut Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: 42463249a6636e625729f90fc31fa7589ef7ef74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61878793"
---
# <a name="generating-commands-with-commandbuilders"></a>CommandBuilders ile Komut Oluşturma
Zaman `SelectCommand` gibi bir metinsel komutu kullanıcıdan alan bir sorgu aracı, uygun belirlemek mümkün olmayabilir özelliği çalışma zamanında dinamik olarak belirtilen `InsertCommand`, `UpdateCommand`, veya `DeleteCommand` tasarım zamanında. Varsa, <xref:System.Data.DataTable> eşler veya oluşturulan bir tek veritabanı tablosundan avantajlarından yararlanabilirsiniz <xref:System.Data.Common.DbCommandBuilder> otomatik olarak oluşturmak için nesne `DeleteCommand`, `InsertCommand`, ve `UpdateCommand` , <xref:System.Data.Common.DbDataAdapter>.  
  
 Bir en düşük gereksinim ayarlamalısınız `SelectCommand` sırayla çalışması otomatik komut oluşturma özelliği. Tablo şeması alınamıyor tarafından `SelectCommand` özelliği otomatik olarak oluşturulan bir INSERT, UPDATE ve DELETE deyimleri söz dizimi belirler.  
  
 <xref:System.Data.Common.DbCommandBuilder> Yürütmeli `SelectCommand` INSERT, UPDATE ve DELETE SQL komutlarını oluşturmak gerekli meta verileri döndürmek için. Sonuç olarak, ek bir seyahat veri kaynağı için gereklidir ve bu performansı düşürür. En iyi performans elde etmek için Komutlarınızın açıkça belirtmek yerine <xref:System.Data.Common.DbCommandBuilder>.  
  
 `SelectCommand` Ayrıca en az bir birincil anahtar veya benzersiz sütun döndürmelidir. Hiçbiri yoksa bir `InvalidOperation` özel durum oluşturulur ve komutlar oluşturulmaz.  
  
 İle ilişkili olduğunda bir `DataAdapter`, <xref:System.Data.Common.DbCommandBuilder> otomatik olarak oluşturduğu `InsertCommand`, `UpdateCommand`, ve `DeleteCommand` özelliklerini `DataAdapter` null başvuru olmaları durumunda. Varsa bir `Command` var olan bir özellik için zaten `Command` kullanılır.  
  
 İki veya daha fazla tablo bir araya getirme tarafından oluşturulmuş veritabanı görünümleri tek veritabanı tablosu olarak kabul edilmez. Bu örnekte kullanamazsınız <xref:System.Data.Common.DbCommandBuilder> otomatik olarak oluşturmak için kullanılan komutlar; komutlarınızı açıkça belirtmeniz gerekir. Açıkça güncelleştirmeleri çözümlemek için komutları ayarlama hakkında bilgi için bir `DataSet` veri kaynağına geri bkz [güncelleştirme veri kaynaklarını DataAdapters ile](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Çıkış parametreleri güncelleştirilmiş satırına harita isteyebileceğiniz bir `DataSet`. Yaygın görevlerden biri bir otomatik olarak oluşturulan kimlik alanının değeri alınırken olması veya zaman damgası veri kaynağından. <xref:System.Data.Common.DbCommandBuilder> Çıkış parametreleri bir güncelleştirilen satırı sütunlar için varsayılan olarak eşleştirmez. Bu örnekte, komut açıkça belirtmeniz gerekir. Otomatik olarak oluşturulan kimlik alanına eklenen bir satırın geri bir sütununa eşleme örneği için bkz: [alınırken kimlik veya otomatik sayı değerlerini](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Kurallar için komutları otomatik olarak oluşturulur.  
 Aşağıdaki tabloda komutları üretilen nasıl otomatik olarak oluşturulan için kuralları gösterir.  
  
|Komut|Kural|  
|-------------|----------|  
|`InsertCommand`|Veri kaynağı ile bir tablodaki tüm satırlar için bir satır ekler bir <xref:System.Data.DataRow.RowState%2A> , <xref:System.Data.DataRowState.Added>. Tüm güncelleştirilebilir olan sütunlar (ancak değil sütunları kimlikleri, ifadeler veya zaman damgaları gibi) için değerler ekler.|  
|`UpdateCommand`|Güncelleştirmeleri satırları bir tablodaki tüm satırlar için veri kaynağındaki bir `RowState` , <xref:System.Data.DataRowState.Modified>. Kimlikleri veya ifadeleri gibi güncelleştirilebilir olmayan sütunları hariç tüm sütunların değerlerini güncelleştirir. Tüm satırları, veri kaynağındaki sütun değerlerini satırın birincil anahtar sütunu değerlerinin eşleştiğinde ve kalan sütunların veri kaynağındaki satırı öğesinin özgün değerleri eşleştiğinde güncelleştirir. Daha fazla bilgi için bu konunun "İyimser eşzamanlılık Model için güncelleştirmeleri ve siler," konusuna bakın.|  
|`DeleteCommand`|Veri kaynağı ile bir tablodaki tüm satırlar için satırları siler bir `RowState` , <xref:System.Data.DataRowState.Deleted>. Sütun değerleri satırın birincil anahtar sütunu değerlerinin eşleştiğinde ve kalan sütunların veri kaynağındaki satırı öğesinin özgün değerleri eşleştiğinde tüm satırları siler. Daha fazla bilgi için bu konunun "İyimser eşzamanlılık Model için güncelleştirmeleri ve siler," konusuna bakın.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Güncelleştirme ve silme için iyimser eşzamanlılık modeli  
 Komutları için UPDATE ve DELETE deyimleri otomatik olarak oluşturmak için mantıksal dayanır *iyimser eşzamanlılık*--diğer bir deyişle, kayıtları düzenleme için kilitli değil ve diğer kullanıcılara veya işlemlere göre herhangi bir zamanda değiştirilebilir. Bir kayıt SELECT deyimi döndürüldü, ancak UPDATE veya DELETE deyimindeki verilmeden önce otomatik olarak oluşturulan bir UPDATE veya DELETE deyiminin WHERE yan tümcesi içeren sonra değiştirilmiş çünkü bir satır varsa yalnızca güncelleştirilmiş olduğunu belirten, Tüm orijinal değerleri içeren ve veri kaynağından silinmez. Bu, yeni verilerin üzerine yazılmasını önlemek için yapılır. Otomatik olarak oluşturulan bir güncelleştirme girişimde bulunan orijinal değerleri içermiyor ya da silinmiş olan bir satırı güncelleştirmek bulunduğu <xref:System.Data.DataSet>, herhangi bir kayıt komutu etkilemez ve <xref:System.Data.DBConcurrencyException> oluşturulur.  
  
 UPDATE veya DELETE özgün değerlerine bakılmaksızın tamamlanması istiyorsanız açıkça ayarlamalısınız `UpdateCommand` için `DataAdapter` ve otomatik komut nesil bağımlı kalmayacak.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Otomatik komut oluşturma mantığı sınırlamaları  
 Otomatik komut oluşturma için aşağıdaki sınırlamalar geçerlidir.  
  
### <a name="unrelated-tables-only"></a>Yalnızca olmayan tablolar  
 INSERT, mantıksal oluşturur otomatik komut oluşturma güncelleştirin veya tek başına tablolar için diğer tablolara veri kaynağındaki tüm ilişkileri dikkate almadan silmeyi. Sonuç olarak, çağırırken bir hatayla karşılaşabilirsiniz `Update` bir veritabanındaki yabancı anahtar kısıtlaması yer aldığı bir sütun için değişiklikleri göndermek için. Bu özel durumdan kaçınmak için kullanmayın <xref:System.Data.Common.DbCommandBuilder> sütunlar bir yabancı anahtar kısıtlaması içinde; güncelleştirmek için bunun yerine, açıkça işlemi gerçekleştirmek için kullanılan ifadelerini belirtin.  
  
### <a name="table-and-column-names"></a>Tablo ve sütun adları  
 Sütun adları ya da tablo adları, boşluk, nokta, tırnak işaretleri veya diğer alfasayısal olmayan karakterleri gibi özel karakterler içeriyorsa otomatik komut oluşturma mantığı köşeli parantez ayrılmış olsa bile başarısız olabilir. Sağlayıcısına bağlı olarak QuotePrefix ve QuoteSuffix parametreleri ayarlanıyor nesil mantıksal işlem boşluklara izin verebilir, ancak özel karakterleri kaçış olamaz. Tablo adları biçiminde tam *catalog.schema.table* desteklenir.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>Bir SQL deyimi otomatik olarak oluşturulacak CommandBuilder kullanma  
 SQL deyimleri için otomatik olarak oluşturmak için bir `DataAdapter`, ilk olarak `SelectCommand` özelliği `DataAdapter`, oluşturup bir `CommandBuilder` nesne ve bağımsız değişken olarak belirtin `DataAdapter` hangi `CommandBuilder` otomatik olarak SQL deyimleri oluştur.  
  
```vb  
' Assumes that connection is a valid SqlConnection object   
' inside of a Using block.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers", connection)  
Dim builder As SqlCommandBuilder = New SqlCommandBuilder(adapter)  
builder.QuotePrefix = "["  
builder.QuoteSuffix = "]"  
```  
  
```csharp  
// Assumes that connection is a valid SqlConnection object  
// inside of a using block.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers", connection);  
SqlCommandBuilder builder = new SqlCommandBuilder(adapter);  
builder.QuotePrefix = "[";  
builder.QuoteSuffix = "]";  
```  
  
## <a name="modifying-the-selectcommand"></a>SelectCommand değiştirme  
 Değiştirirseniz `CommandText` , `SelectCommand` INSERT, UPDATE veya DELETE komutları otomatik olarak oluşturduktan sonra bir özel durum ortaya çıkabilir. Varsa değiştirilmiş `SelectCommand.CommandText` ile tutarsız şema bilgileri içeriyor `SelectCommand.CommandText` kullanılan zaman ekleme, güncelleştirme veya komutları silmek olan otomatik olarak oluşturulan, gelecekteki çağrılar `DataAdapter.Update` yöntemi sütunları erişmeyi deneyebilir, tarafından başvurulan geçerli tabloda artık mevcut `SelectCommand`, ve bir özel durum oluşturulur.  
  
 Tarafından kullanılan şema bilgileri yenileyebilirsiniz `CommandBuilder` çağırarak komutları otomatik olarak oluşturulacak `RefreshSchema` yöntemi `CommandBuilder`.  
  
 Hangi komut otomatik olarak oluşturulmuş bilmek istiyorsanız, kullanarak otomatik olarak oluşturulan komutları başvuru edinebilirsiniz `GetInsertCommand`, `GetUpdateCommand`, ve `GetDeleteCommand` yöntemlerinin `CommandBuilder` nesne ve denetimi`CommandText`özelliği ilişkili komutu.  
  
 Aşağıdaki kod örneği, otomatik olarak oluşturulmuş güncelleştirme komut konsola yazar.  
  
```vb
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```

```csharp
Console.WriteLine(builder.GetUpdateCommand().CommandText);
```
  
 Aşağıdaki örnek yeniden oluşturur `Customers` tablosundaki `custDS` veri kümesi. **RefreshSchema** yöntemi otomatik olarak oluşturulan bu yeni bir sütun bilgileri komutlarla yenilemek için çağrılır.  
  
```vb  
' Assumes an open SqlConnection and SqlDataAdapter inside of a Using block.  
adapter.SelectCommand.CommandText = _  
  "SELECT CustomerID, ContactName FROM dbo.Customers"  
builder.RefreshSchema()  
  
custDS.Tables.Remove(custDS.Tables("Customers"))  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
// Assumes an open SqlConnection and SqlDataAdapter inside of a using block.  
adapter.SelectCommand.CommandText =   
  "SELECT CustomerID, ContactName FROM dbo.Customers";  
builder.RefreshSchema();  
  
custDS.Tables.Remove(custDS.Tables["Customers"]);  
adapter.Fill(custDS, "Customers");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)
- [Komut Yürütme](../../../../docs/framework/data/adonet/executing-a-command.md)
- [DbConnection, DbCommand ve DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET yönetilen sağlayıcıları ve DataSet Geliştirici Merkezi](https://go.microsoft.com/fwlink/?LinkId=217917)
