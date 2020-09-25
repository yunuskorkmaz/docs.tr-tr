---
title: CommandBuilders ile Komut Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: d88f5772e038766d49baf8c758c547e6d5667904
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91200725"
---
# <a name="generating-commands-with-commandbuilders"></a>CommandBuilders ile Komut Oluşturma

Özelliği, `SelectCommand` kullanıcıdan metin komutu alan bir sorgu aracı aracılığıyla olduğu gibi çalışma zamanında dinamik olarak belirtildiğinde, uygun `InsertCommand` , `UpdateCommand` veya `DeleteCommand` Tasarım zamanını belirtmeyebilirsiniz. <xref:System.Data.DataTable>Tek bir veritabanı tablosundan haritalarınız veya oluşturulursa,,, ve ' ı <xref:System.Data.Common.DbCommandBuilder> otomatik olarak oluşturmak için nesnesinden faydalanabilir `DeleteCommand` `InsertCommand` `UpdateCommand` <xref:System.Data.Common.DbDataAdapter> .  
  
 En düşük gereksinim olarak, `SelectCommand` otomatik komut oluşturma özelliğinin çalışması için özelliği ayarlamanız gerekir. Özelliği tarafından alınan tablo şeması, `SelectCommand` otomatik olarak oluşturulan INSERT, Update ve DELETE deyimlerinin söz dizimini belirler.  
  
 <xref:System.Data.Common.DbCommandBuilder> `SelectCommand` Insert, Update ve DELETE SQL komutlarını oluşturmak için gereken meta verileri döndürmek üzere öğesini yürütmelidir. Sonuç olarak, veri kaynağına fazladan bir seyahat gerekir ve bu da performansı azaltabilir. En iyi performansı elde etmek için, komutlarınızı kullanmak yerine açıkça belirtin <xref:System.Data.Common.DbCommandBuilder> .  
  
 `SelectCommand`Ayrıca en az bir birincil anahtar veya benzersiz sütun döndürmelidir. Hiçbiri yoksa, bir `InvalidOperation` özel durum oluşturulur ve komutlar oluşturulmaz.  
  
 İle ilişkilendirildiğinde,,,, `DataAdapter` <xref:System.Data.Common.DbCommandBuilder> `InsertCommand` `UpdateCommand` ve özelliklerini, `DeleteCommand` `DataAdapter` null başvurularsa otomatik olarak oluşturur. Bir `Command` özellik için zaten varsa, var olan `Command` kullanılır.  
  
 İki veya daha fazla tabloyu birlikte birleştirerek oluşturulan veritabanı görünümleri tek bir veritabanı tablosu olarak kabul edilmez. Bu örnekte, <xref:System.Data.Common.DbCommandBuilder> komutları otomatik olarak oluşturmak için kullanamazsınız; komutlarınızı açık bir şekilde belirtmeniz gerekir. Güncelleştirmeleri veri kaynağına geri çözümlemeye yönelik komutları açıkça ayarlama hakkında daha fazla bilgi için `DataSet` , bkz. [veri kaynaklarını DataAdapter ile güncelleştirme](updating-data-sources-with-dataadapters.md).  
  
 Çıkış parametrelerini, öğesinin güncelleştirilmiş satırına geri eşlemek isteyebilirsiniz `DataSet` . Bir ortak görev, otomatik olarak oluşturulan bir kimlik alanının veya veri kaynağından zaman damgasının değerini alıyor. , <xref:System.Data.Common.DbCommandBuilder> Çıkış parametrelerini varsayılan olarak güncelleştirilmiş bir satırdaki sütunlara eşlemecektir. Bu örnekte, komutunuz açıkça belirtmeniz gerekir. Otomatik olarak oluşturulan bir kimlik alanını, ekli bir satırın sütununa geri eşleme örneği için bkz. [kimlik veya OtomatikSayı değerlerini alma](retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Otomatik olarak oluşturulan komutlar için kurallar  

 Aşağıdaki tabloda otomatik olarak oluşturulan komutların nasıl oluşturulduğu kurallar gösterilmektedir.  
  
|Komut|Kural|  
|-------------|----------|  
|`InsertCommand`|Tablodaki tüm satırlar için veri kaynağına bir satır ekler <xref:System.Data.DataRow.RowState%2A> <xref:System.Data.DataRowState.Added> . Güncelleştirilebilir olan tüm sütunlar için değerler ekler (Ancak kimlikler, ifadeler veya zaman damgaları gibi sütunlar).|  
|`UpdateCommand`|Tablodaki tüm satırlar için veri kaynağındaki satırları güncelleştirir `RowState` <xref:System.Data.DataRowState.Modified> . Kimlikler veya ifadeler gibi, güncelleştirilemez olan sütunlar hariç tüm sütunların değerlerini güncelleştirir. Veri kaynağındaki sütun değerlerinin satırın birincil anahtar sütun değerleriyle eşleştiği ve veri kaynağındaki kalan sütunların satırın orijinal değerleriyle eşleştiği tüm satırları güncelleştirir. Daha fazla bilgi için, bu konunun devamındaki "Güncelleştirmeler ve silmeler için Iyimser eşzamanlılık modeli" başlığına bakın.|  
|`DeleteCommand`|' A sahip tablodaki tüm satırlar için veri kaynağındaki satırları siler `RowState` <xref:System.Data.DataRowState.Deleted> . Sütun değerlerinin satırın birincil anahtar sütun değerleriyle eşleştiği ve veri kaynağındaki kalan sütunların satırın orijinal değerleriyle eşleştiği tüm satırları siler. Daha fazla bilgi için, bu konunun devamındaki "Güncelleştirmeler ve silmeler için Iyimser eşzamanlılık modeli" başlığına bakın.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Güncelleştirmeler ve silmeler için iyimser eşzamanlılık modeli  

 UPDATE ve DELETE deyimlerine yönelik komutları otomatik olarak oluşturma mantığı, *iyimser eşzamanlılık*tabanlıdır; Yani, kayıtlar düzenlenmek üzere kilitlenmez ve herhangi bir zamanda diğer Kullanıcı veya süreçler tarafından değiştirilebilir. Bir kayıt, SELECT ifadesinden döndürülmeden sonra değiştirilmiş olabileceğinden, UPDATE veya DELETE deyimi alınmadan önce, otomatik olarak oluşturulan UPDATE veya DELETE deyimi bir WHERE yan tümcesi içerir, bir satırın yalnızca tüm orijinal değerleri içermesi ve veri kaynağından silinmemiş olması halinde güncelleştirildiğini belirten bir WHERE yan tümcesi vardır. Bu, yeni verilerin üzerine yazılmasını önlemek için yapılır. Otomatik olarak oluşturulan bir güncelleştirme silinmiş olan veya içinde bulunan özgün değerleri içermeyen bir satırı güncelleştirmeyi denediğinde <xref:System.Data.DataSet> , komut herhangi bir kaydı etkilemez ve bir oluşturulur <xref:System.Data.DBConcurrencyException> .  
  
 GÜNCELLEŞTIRME veya SILME işleminin özgün değerlerden bağımsız olarak tamamlanmasını istiyorsanız, `UpdateCommand` `DataAdapter` otomatik komut oluşturmaya dayanmayan ve için öğesini açıkça ayarlamanız gerekir.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Otomatik komut oluşturma mantığının sınırlamaları  

 Otomatik komut oluşturma için aşağıdaki sınırlamalar geçerlidir.  
  
### <a name="unrelated-tables-only"></a>Yalnızca ilişkisiz tablolar  

 Otomatik komut oluşturma mantığı, veri kaynağındaki diğer tablolarla hiçbir ilişki hesaba katmadan tek başına tablolar için INSERT, UPDATE veya DELETE deyimlerini oluşturur. Sonuç olarak, `Update` veritabanındaki bir yabancı anahtar kısıtlamasına katılan bir sütun için değişiklik göndermek üzere çağrılırken bir hatayla karşılaşabilirsiniz. Bu özel durumdan kaçınmak için, <xref:System.Data.Common.DbCommandBuilder> yabancı anahtar kısıtlamasında yer alan sütunları güncelleştirmek için kullanmayın; bunun yerine, işlemi gerçekleştirmek için kullanılan deyimleri açıkça belirtin.  
  
### <a name="table-and-column-names"></a>Tablo ve sütun adları  

 Sütun adları veya tablo adlarında boşluk, nokta, tırnak işaretleri gibi özel karakterler veya köşeli ayraç ile sınırlandırılmış olsa bile, alfasayısal olmayan karakterler içeriyorsa otomatik komut oluşturma mantığı başarısız olabilir. Sağlayıcıya bağlı olarak, QuotePrefix ve QuoteSuffix parametrelerinin ayarlanması nesil mantığın boşluk işlemesini sağlayabilir, ancak özel karakterler içeremez. *Catalog. Schema. Table* biçimindeki tam nitelikli tablo adları desteklenir.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>CommandBuilder kullanarak bir SQL Ifadesini otomatik olarak oluşturma  

 Otomatik olarak bir için SQL deyimleri oluşturmak üzere, `DataAdapter` `SelectCommand` öğesinin özelliğini ayarlayın, `DataAdapter` sonra bir `CommandBuilder` nesnesi oluşturun ve `DataAdapter` için `CommandBuilder` otomatik olarak SQL deyimleri üretecek bir bağımsız değişken olarak belirtin.  
  
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

 `CommandText` `SelectCommand` Insert, Update veya delete komutları otomatik olarak oluşturulduktan sonra ' ın öğesini değiştirirseniz, bir özel durum ortaya çıkabilir. Değişiklik `SelectCommand.CommandText` `SelectCommand.CommandText` , INSERT, Update veya delete komutları otomatik olarak oluşturulduğunda kullanılan ile tutarsız şema bilgileri içeriyorsa, yönteme gelecekteki çağrılar, `DataAdapter.Update` tarafından başvurulan geçerli tabloda artık bulunmayan sütunlara erişmeye çalışabilir `SelectCommand` ve bir özel durum oluşturulur.  
  
 ' `CommandBuilder` In metodunu çağırarak komutları otomatik olarak oluşturmak için tarafından kullanılan şema bilgilerini yenileyebilirsiniz `RefreshSchema` `CommandBuilder` .  
  
 Hangi komutun otomatik olarak oluşturulduğunu biliyorsanız, `GetInsertCommand` `GetUpdateCommand` nesnesinin, ve yöntemlerinin yanı sıra `GetDeleteCommand` `CommandBuilder` `CommandText` ilişkili komutun özelliğini denetleyerek otomatik olarak oluşturulan komutlara bir başvuru elde edebilirsiniz.  
  
 Aşağıdaki kod örneği, otomatik olarak oluşturulan Update komutuna konsola yazar.  
  
```vb
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```

```csharp
Console.WriteLine(builder.GetUpdateCommand().CommandText);
```
  
 Aşağıdaki örnek, `Customers` veri kümesindeki tabloyu yeniden oluşturur `custDS` . Bu yeni sütun bilgileriyle otomatik olarak oluşturulan komutları yenilemek için **RefreshSchema** yöntemi çağırılır.  
  
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
