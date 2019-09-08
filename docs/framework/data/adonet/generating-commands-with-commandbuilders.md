---
title: CommandBuilders ile Komut Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: 7cc8ff5391fca7c3315dda433785a182f476bca7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783883"
---
# <a name="generating-commands-with-commandbuilders"></a>CommandBuilders ile Komut Oluşturma
Özelliği, kullanıcıdan metin komutu alan bir sorgu aracı aracılığıyla olduğu gibi çalışma zamanında dinamik olarak belirtildiğinde, uygun `InsertCommand`, `UpdateCommand`veya `DeleteCommand` tasarım zamanını belirtmeyebilirsiniz. `SelectCommand` Tek bir <xref:System.Data.DataTable> veritabanı tablosundan haritalarınız veya oluşturulursa,,, ve `UpdateCommand` <xref:System.Data.Common.DbDataAdapter>' ı otomatik olarak oluşturmak `DeleteCommand` `InsertCommand`için <xref:System.Data.Common.DbCommandBuilder> nesnesinden faydalanabilir.  
  
 En düşük gereksinim olarak, otomatik komut oluşturma `SelectCommand` özelliğinin çalışması için özelliği ayarlamanız gerekir. `SelectCommand` Özelliği tarafından alınan tablo şeması, otomatik olarak oluşturulan INSERT, Update ve DELETE deyimlerinin söz dizimini belirler.  
  
 INSERT, Update ve `SelectCommand` DELETE SQL komutlarını oluşturmak için gereken meta verileri döndürmek üzere öğesini yürütmelidir.<xref:System.Data.Common.DbCommandBuilder> Sonuç olarak, veri kaynağına fazladan bir seyahat gerekir ve bu da performansı azaltabilir. En iyi performansı elde etmek için, komutlarınızı kullanmak <xref:System.Data.Common.DbCommandBuilder>yerine açıkça belirtin.  
  
 `SelectCommand` Ayrıca en az bir birincil anahtar veya benzersiz sütun döndürmelidir. Hiçbiri yoksa, bir `InvalidOperation` özel durum oluşturulur ve komutlar oluşturulmaz.  
  
 İle `DataAdapter` `InsertCommand` ilişkilendirildiğinde,`UpdateCommand`,,, ve özelliklerini,`DataAdapter` null başvurularsa <xref:System.Data.Common.DbCommandBuilder> otomatik `DeleteCommand` olarak oluşturur. Bir `Command` özellik için zaten varsa, var olan `Command` kullanılır.  
  
 İki veya daha fazla tabloyu birlikte birleştirerek oluşturulan veritabanı görünümleri tek bir veritabanı tablosu olarak kabul edilmez. Bu örnekte, <xref:System.Data.Common.DbCommandBuilder> komutları otomatik olarak oluşturmak için kullanamazsınız; komutlarınızı açık bir şekilde belirtmeniz gerekir. Güncelleştirmeleri `DataSet` veri kaynağına geri çözümlemeye yönelik komutları açıkça ayarlama hakkında daha fazla bilgi için, bkz. [veri kaynaklarını DataAdapter ile güncelleştirme](updating-data-sources-with-dataadapters.md).  
  
 Çıkış parametrelerini, öğesinin `DataSet`güncelleştirilmiş satırına geri eşlemek isteyebilirsiniz. Bir ortak görev, otomatik olarak oluşturulan bir kimlik alanının veya veri kaynağından zaman damgasının değerini alıyor. , <xref:System.Data.Common.DbCommandBuilder> Çıkış parametrelerini varsayılan olarak güncelleştirilmiş bir satırdaki sütunlara eşlemecektir. Bu örnekte, komutunuz açıkça belirtmeniz gerekir. Otomatik olarak oluşturulan bir kimlik alanını, ekli bir satırın sütununa geri eşleme örneği için bkz. [kimlik veya OtomatikSayı değerlerini alma](retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Otomatik olarak oluşturulan komutlar için kurallar  
 Aşağıdaki tabloda otomatik olarak oluşturulan komutların nasıl oluşturulduğu kurallar gösterilmektedir.  
  
|Komut|Kural|  
|-------------|----------|  
|`InsertCommand`|Tablodaki tüm satırlar için veri kaynağına bir <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Added>satır ekler. Güncelleştirilebilir olan tüm sütunlar için değerler ekler (Ancak kimlikler, ifadeler veya zaman damgaları gibi sütunlar).|  
|`UpdateCommand`|`RowState` Tablodaki<xref:System.Data.DataRowState.Modified>tüm satırlar için veri kaynağındaki satırları güncelleştirir. Kimlikler veya ifadeler gibi, güncelleştirilemez olan sütunlar hariç tüm sütunların değerlerini güncelleştirir. Veri kaynağındaki sütun değerlerinin satırın birincil anahtar sütun değerleriyle eşleştiği ve veri kaynağındaki kalan sütunların satırın orijinal değerleriyle eşleştiği tüm satırları güncelleştirir. Daha fazla bilgi için, bu konunun devamındaki "Güncelleştirmeler ve silmeler için Iyimser eşzamanlılık modeli" başlığına bakın.|  
|`DeleteCommand`|' A `RowState` <xref:System.Data.DataRowState.Deleted>sahip tablodaki tüm satırlar için veri kaynağındaki satırları siler. Sütun değerlerinin satırın birincil anahtar sütun değerleriyle eşleştiği ve veri kaynağındaki kalan sütunların satırın orijinal değerleriyle eşleştiği tüm satırları siler. Daha fazla bilgi için, bu konunun devamındaki "Güncelleştirmeler ve silmeler için Iyimser eşzamanlılık modeli" başlığına bakın.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Güncelleştirmeler ve silmeler için iyimser eşzamanlılık modeli  
 UPDATE ve DELETE deyimlerine yönelik komutları otomatik olarak oluşturma mantığı, *iyimser eşzamanlılık*tabanlıdır; Yani, kayıtlar düzenlenmek üzere kilitlenmez ve herhangi bir zamanda diğer Kullanıcı veya süreçler tarafından değiştirilebilir. Bir kayıt, SELECT ifadesinden döndürülmeden sonra değiştirilmiş olabileceğinden, UPDATE veya DELETE deyimi verildikten sonra, otomatik olarak oluşturulan UPDATE veya DELETE deyimi bir WHERE yan tümcesi içerir, bu da bir satırın yalnızca tüm özgün değerleri içerir ve veri kaynağından silinmez. Bu, yeni verilerin üzerine yazılmasını önlemek için yapılır. Otomatik olarak oluşturulan bir güncelleştirme silinmiş olan veya içinde <xref:System.Data.DataSet>bulunan özgün değerleri içermeyen bir satırı güncelleştirmeyi denediğinde, komut herhangi bir kaydı etkilemez ve bir <xref:System.Data.DBConcurrencyException> oluşturulur.  
  
 Güncelleştirme veya silme işleminin özgün değerlerden bağımsız olarak tamamlanmasını istiyorsanız, otomatik komut oluşturmaya dayanmayan `UpdateCommand` `DataAdapter` ve için öğesini açıkça ayarlamanız gerekir.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Otomatik komut oluşturma mantığının sınırlamaları  
 Otomatik komut oluşturma için aşağıdaki sınırlamalar geçerlidir.  
  
### <a name="unrelated-tables-only"></a>Yalnızca ilişkisiz tablolar  
 Otomatik komut oluşturma mantığı, veri kaynağındaki diğer tablolarla hiçbir ilişki hesaba katmadan tek başına tablolar için INSERT, UPDATE veya DELETE deyimlerini oluşturur. Sonuç olarak, veritabanındaki bir yabancı anahtar kısıtlamasına katılan bir sütun `Update` için değişiklik göndermek üzere çağrılırken bir hatayla karşılaşabilirsiniz. Bu özel durumdan kaçınmak için, yabancı anahtar kısıtlamasında <xref:System.Data.Common.DbCommandBuilder> yer alan sütunları güncelleştirmek için kullanmayın; bunun yerine, işlemi gerçekleştirmek için kullanılan deyimleri açıkça belirtin.  
  
### <a name="table-and-column-names"></a>Tablo ve sütun adları  
 Sütun adları veya tablo adlarında boşluk, nokta, tırnak işaretleri gibi özel karakterler veya köşeli ayraç ile sınırlandırılmış olsa bile, alfasayısal olmayan karakterler içeriyorsa otomatik komut oluşturma mantığı başarısız olabilir. Sağlayıcıya bağlı olarak, QuotePrefix ve QuoteSuffix parametrelerinin ayarlanması nesil mantığın boşluk işlemesini sağlayabilir, ancak özel karakterler içeremez. *Catalog. Schema. Table* biçimindeki tam nitelikli tablo adları desteklenir.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>CommandBuilder kullanarak bir SQL Ifadesini otomatik olarak oluşturma  
 Otomatik `DataAdapter`olarak bir için SQL deyimleri oluşturmak üzere, öğesinin `DataAdapter` `SelectCommand` `DataAdapter`özelliğini ayarlayın, sonra bir `CommandBuilder` `CommandBuilder` nesnesi oluşturun ve için otomatik olarak kullanılacak bir bağımsız değişken olarak belirtin. SQL deyimlerini oluştur.  
  
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
  
## <a name="modifying-the-selectcommand"></a>SelectCommand 'i değiştirme  
 INSERT, Update veya `CommandText` DELETE komutları `SelectCommand` otomatik olarak oluşturulduktan sonra ' ın öğesini değiştirirseniz, bir özel durum ortaya çıkabilir. Değiştirilen `SelectCommand.CommandText` , INSERT, Update veya delete komutları otomatik olarak oluşturulduğunda `SelectCommand.CommandText` kullanılan ile tutarsız şema bilgileri içeriyorsa `DataAdapter.Update` , yönteme gelecekteki çağrılar Artık tarafından `SelectCommand`başvurulan geçerli tabloda yok ve bir özel durum oluşturulacak.  
  
 ' In `CommandBuilder` `RefreshSchema`metodunuçağırarak komutları otomatik olarak oluşturmak için tarafından kullanılan şema bilgilerini yenileyebilirsiniz. `CommandBuilder`  
  
 Hangi komutun otomatik olarak oluşturulduğunu `GetInsertCommand`biliyorsanız, `CommandBuilder` nesnesinin, `GetUpdateCommand`, ve `GetDeleteCommand` yöntemlerini kullanarak otomatik olarak oluşturulan komutlara bir başvuru elde edebilir ve `CommandText`ilişkili komutun özelliği.  
  
 Aşağıdaki kod örneği, otomatik olarak oluşturulan Update komutuna konsola yazar.  
  
```vb
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```

```csharp
Console.WriteLine(builder.GetUpdateCommand().CommandText);
```
  
 Aşağıdaki örnek, `custDS` veri kümesindeki `Customers` tabloyu yeniden oluşturur. Bu yeni sütun bilgileriyle otomatik olarak oluşturulan komutları yenilemek için **RefreshSchema** yöntemi çağırılır.  
  
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

- [Komutlar ve Parametreler](commands-and-parameters.md)
- [Komut Yürütme](executing-a-command.md)
- [DbConnection, DbCommand ve DbException](dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET’e Genel Bakış](ado-net-overview.md)
