---
title: CommandBuilders ile Komut Oluşturma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
ms.openlocfilehash: 76c2a6cb0661a0e39fc3a0dd599fcbb3c046f382
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149618"
---
# <a name="generating-commands-with-commandbuilders"></a>CommandBuilders ile Komut Oluşturma
`SelectCommand` Özellik, kullanıcıdan metin komutu alan bir sorgu aracı gibi çalışma zamanında dinamik olarak belirtildiğinde, uygun `InsertCommand`, `UpdateCommand`veya `DeleteCommand` tasarım zamanında belirtemeyebilirsiniz. Tek <xref:System.Data.DataTable> bir veritabanı tablosuna yaptığınız haritalar veya haritalarınız tek <xref:System.Data.Common.DbCommandBuilder> bir veritabanı tablosundan oluşturulacaksa, `DeleteCommand`nesnenin `InsertCommand`,, ve `UpdateCommand` <xref:System.Data.Common.DbDataAdapter>.  
  
 Minimum gereksinim olarak, otomatik `SelectCommand` komut oluşturmanın çalışması için özelliği ayarlamanız gerekir. `SelectCommand` Özellik tarafından alınan tablo şeması, otomatik olarak oluşturulan INSERT, UPDATE ve DELETE ifadelerinin sözdizimini belirler.  
  
 INSERT, `SelectCommand` UPDATE ve DELETE SQL komutlarını oluşturmak için gerekli meta verileri döndürmek için yürütmeniz <xref:System.Data.Common.DbCommandBuilder> gerekir. Sonuç olarak, veri kaynağına ekstra bir yolculuk gereklidir ve bu da performansı engelleyebilir. En iyi performansı elde etmek için komutlarınızı <xref:System.Data.Common.DbCommandBuilder>kullanarak değil, açıkça belirtin.  
  
 Ayrıca `SelectCommand` en az bir birincil anahtar veya benzersiz sütun döndürmesi gerekir. Hiçbiri yoksa, bir `InvalidOperation` özel durum oluşturulur ve komutlar oluşturulmaz.  
  
 Bir `DataAdapter`ile ilişkili <xref:System.Data.Common.DbCommandBuilder> olduğunda , otomatik `InsertCommand` `UpdateCommand`olarak `DeleteCommand` oluşturur , `DataAdapter` , ve özellikleri eğer null referanslar vardır. Bir `Command` özellik için zaten varsa, `Command` varolan kullanılır.  
  
 İki veya daha fazla tabloyu bir araya getirerek oluşturulan veritabanı görünümleri tek bir veritabanı tablosu olarak kabul edilmez. Bu durumda otomatik olarak <xref:System.Data.Common.DbCommandBuilder> komutoluşturmak için kullanamazsınız; komutlarınızı açıkça belirtmeniz gerekir. Veri kaynağına `DataSet` geri güncellemeleri çözmek için açıkça ayarlama komutları hakkında bilgi için, [DataAdapters ile Veri Kaynaklarını Güncelleştirme'ye](updating-data-sources-with-dataadapters.md)bakın.  
  
 Çıktı parametrelerini güncelleştirilmiş bir `DataSet`satıra geri eşlemek isteyebilirsiniz. Ortak bir görev, otomatik olarak oluşturulan kimlik alanının veya zaman damgasının değerini veri kaynağından almaktır. Çıkış <xref:System.Data.Common.DbCommandBuilder> parametrelerini varsayılan olarak güncelleştirilmiş bir satırdaki sütunlarla eşlemez. Bu durumda komutunuzu açıkça belirtmeniz gerekir. Otomatik olarak oluşturulan kimlik alanını eklenen bir satırsütununa eşleme örneği [için](retrieving-identity-or-autonumber-values.md)bkz.  
  
## <a name="rules-for-automatically-generated-commands"></a>Otomatik Oluşturulan Komutlar için Kurallar  
 Aşağıdaki tablo, otomatik olarak oluşturulan komutların nasıl oluşturulduğuna yönelik kuralları gösterir.  
  
|Komut|Kural|  
|-------------|----------|  
|`InsertCommand`|Tablodaki tüm satırlar için veri kaynağına bir <xref:System.Data.DataRow.RowState%2A> satır <xref:System.Data.DataRowState.Added>ekler. Güncelleştirilebilir (ancak kimlikler, ifadeler veya zaman damgaları gibi sütunlar değil) tüm sütunlar için değerler ekler.|  
|`UpdateCommand`|Tablodaki `RowState` tüm satırların veri kaynağındaki satırları <xref:System.Data.DataRowState.Modified>güncelleştirir. Kimlikler veya ifadeler gibi güncelleştirilemeyecek sütunlar dışında tüm sütunların değerlerini güncelleştirir. Veri kaynağındaki sütun değerlerinin satırın birincil anahtar sütun değerleriyle eşleştiği ve veri kaynağındaki kalan sütunların satırın özgün değerleriyle eşleştiği tüm satırları güncelleştirir. Daha fazla bilgi için, daha sonra bu konuda "Güncelleştirmeler ve Silmeler için İyimser Eşzamanlılık Modeli"ne bakın.|  
|`DeleteCommand`|Tablodaki `RowState` tüm satırların veri kaynağındaki satırları <xref:System.Data.DataRowState.Deleted>siler. Sütun değerlerinin satırın birincil temel sütun değerleriyle eşleştiği ve veri kaynağındaki kalan sütunların satırın özgün değerleriyle eşleştiği tüm satırları siler. Daha fazla bilgi için, daha sonra bu konuda "Güncelleştirmeler ve Silmeler için İyimser Eşzamanlılık Modeli"ne bakın.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Güncellemeler ve Silmeler için İyimser Eşzamanlılık Modeli  
 UPDATE ve DELETE ifadeleri için otomatik olarak komut oluşturma mantığı *iyimser eşzamanlılık*dayanmaktadır -diğer bir deyişle, kayıtlar düzenleme için kilitli değildir ve herhangi bir zamanda diğer kullanıcılar veya işlemler tarafından değiştirilebilir. Bir kayıt SELECT deyiminden döndürüldükten sonra değiştirilebileceğinden, ancak UPDATE veya DELETE deyimi verilmeden önce, otomatik olarak oluşturulan UPDATE veya DELETE deyimi, bir satırın yalnızca bu ifadede güncelleştirildiğini belirten bir WHERE yan tümcesi içerir. tüm özgün değerleri içerir ve veri kaynağından silinmemiştir. Bu, yeni verilerin üzerine yazılmasından kaçınmak için yapılır. Otomatik olarak oluşturulan güncelleştirme, silinmiş veya özgün değerleri içermeyen bir satırı güncelleştirmeye <xref:System.Data.DataSet>çalıştığında, komut herhangi bir kaydı <xref:System.Data.DBConcurrencyException> etkilemez ve bir atılmıştır.  
  
 ÖZGÜN DEĞERLERDEN bağımsız olarak UPDATE veya DELETE'in tamamlanmasını istiyorsanız, otomatik komut oluşturma için açıkça ayarlamanız `UpdateCommand` `DataAdapter` ve otomatik komut oluşturmanıza güvenmemeniz gerekir.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Otomatik Komut Oluşturma Mantığının Sınırlamaları  
 Aşağıdaki sınırlamalar otomatik komut oluşturma için geçerlidir.  
  
### <a name="unrelated-tables-only"></a>Yalnızca İlişkisiz Tablolar  
 Otomatik komut oluşturma mantığı, veri kaynağındaki diğer tablolarla herhangi bir ilişkiyi hesaba katmadan tek başına tablolar için INSERT, UPDATE veya DELETE deyimleri oluşturur. Sonuç olarak, veritabanında yabancı anahtar `Update` kısıtlamasına katılan bir sütun için değişiklik göndermeye çağırdığınızda bir hatayla karşılaşabilirsiniz. Bu özel durum önlemek <xref:System.Data.Common.DbCommandBuilder> için, yabancı anahtar kısıtlaması ile ilgili sütunları güncelleştirmek için kullanmayın; bunun yerine, işlemi gerçekleştirmek için kullanılan ifadeleri açıkça belirtin.  
  
### <a name="table-and-column-names"></a>Tablo ve Sütun Adları  
 Sütun adları veya tablo adları, köşeli ayraçlarla sınırlandırılsa bile boşluklar, dönemler, tırnak işaretleri veya diğer alfanümerik olmayan karakterler gibi özel karakterler içeriyorsa otomatik komut oluşturma mantığı başarısız olabilir. Sağlayıcıya bağlı olarak, QuotePrefix ve QuoteSuffix parametrelerinin ayarlanması, oluşturma mantığının boşlukları işlemesine izin verebilir, ancak özel karakterlerden kaçamaz. *Catalog.schema.table* şeklinde tam nitelikli tablo adları desteklenir.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>Otomatik olarak BIR SQL Bildirimi Oluşturmak için CommandBuilder kullanma  
 Otomatik `DataAdapter`olarak bir için SQL deyimleri `SelectCommand` oluşturmak `DataAdapter`için , `CommandBuilder` önce , sonra bir `DataAdapter` nesne oluşturmak `CommandBuilder` ve bir bağımsız değişken olarak hangi otomatik olarak SQL deyimleri oluşturacak belirtin.  
  
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
  
## <a name="modifying-the-selectcommand"></a>SelectKomutunu Değiştirme  
 INSERT, `CommandText` UPDATE `SelectCommand` veya DELETE komutlarının otomatik olarak oluşturulduktan sonra sını değiştirirseniz, bir özel durum oluşabilir. Değiştirilen, `SelectCommand.CommandText` ekleme, güncelleştirme veya silme komutları `SelectCommand.CommandText` otomatik olarak oluşturulduğunda kullanılanla tutarsız şema bilgileri içeriyorsa, `DataAdapter.Update` yönteme gelecek çağrılar, başvurulan `SelectCommand`geçerli tabloda artık bulunmayan sütunlara erişmeye çalışabilir ve bir özel durum atılır.  
  
 Otomatik olarak komutoluşturmak `CommandBuilder` için kullanılan şema bilgilerini `RefreshSchema` `CommandBuilder`yenileyebilirsiniz.  
  
 Hangi komutun otomatik olarak oluşturulduğunu bilmek istiyorsanız, `GetInsertCommand` `GetUpdateCommand` `GetDeleteCommand` `CommandBuilder` nesnenin yöntemlerini ve ilişkili komutun özelliğini `CommandText` denetleyerek otomatik olarak oluşturulan komutlara bir başvuru alabilirsiniz.  
  
 Aşağıdaki kod örneği konsola otomatik olarak oluşturulan güncelleştirme komutunu yazar.  
  
```vb
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```

```csharp
Console.WriteLine(builder.GetUpdateCommand().CommandText);
```
  
 Aşağıdaki örnek, veri `Customers` kümesindeki `custDS` tabloyu yeniden oluşturur. Bu yeni sütun bilgileriyle otomatik olarak oluşturulan komutları yenilemek için **Schema'yı Yenileme** yöntemi çağrılır.  
  
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
