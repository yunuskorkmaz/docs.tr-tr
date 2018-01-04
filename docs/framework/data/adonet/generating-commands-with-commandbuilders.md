---
title: "Komutları CommandBuilders ile oluşturma"
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
ms.assetid: 6e3fb8b5-373b-4f9e-ab03-a22693df8e91
caps.latest.revision: "6"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 0227da6029f1c565f44c46a08d786149d6da5086
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="generating-commands-with-commandbuilders"></a>Komutları CommandBuilders ile oluşturma
Zaman `SelectCommand` gibi bir metinsel komutu kullanıcıdan götüren bir sorgu aracıyla, uygun belirlemek mümkün olmayabilir özelliği çalışma zamanında dinamik olarak belirtilen `InsertCommand`, `UpdateCommand`, veya `DeleteCommand` tasarım zamanında. Varsa, <xref:System.Data.DataTable> eşlendiği veya oluşturulan tek veritabanı tablosundan özelliklerden yararlanabilirsiniz <xref:System.Data.Common.DbCommandBuilder> otomatik olarak oluşturmak için nesne `DeleteCommand`, `InsertCommand`, ve `UpdateCommand` , <xref:System.Data.Common.DbDataAdapter>.  
  
 En az bir gereklilik olarak ayarlamalısınız `SelectCommand` çalışmak otomatik komut oluşturma için sırayla özelliği. Tablo şemasını alınan tarafından `SelectCommand` özelliği otomatik olarak oluşturulan INSERT, UPDATE ve DELETE deyimlerinin sözdizimi belirler.  
  
 <xref:System.Data.Common.DbCommandBuilder> Yürütülmelidir `SelectCommand` meta verileri INSERT, UPDATE ve DELETE SQL komutlarını oluşturmak gerekli dönebilmek için. Sonuç olarak, veri kaynağı için fazladan bir seyahat gereklidir ve bu performansı düşürür. En iyi performans elde etmek için komutlarınızı açıkça belirtmek yerine <xref:System.Data.Common.DbCommandBuilder>.  
  
 `SelectCommand` En az bir birincil anahtar veya benzersiz bir sütun da döndürmesi gerekir. Hiçbiri yoksa bir `InvalidOperation` özel durum oluşturulur ve komutları oluşturulmaz.  
  
 İle ilişkili olduğunda bir `DataAdapter`, <xref:System.Data.Common.DbCommandBuilder> otomatik olarak oluşturur `InsertCommand`, `UpdateCommand`, ve `DeleteCommand` özelliklerini `DataAdapter` null başvurular olmaları durumunda. Varsa bir `Command` var olan bir özellik için zaten `Command` kullanılır.  
  
 İki veya daha fazla tablo bir araya getirme tarafından oluşturulan veritabanı görünümleri tek veritabanı tablosu olarak kabul edilmez. Bu örnekte, kullanamazsınız <xref:System.Data.Common.DbCommandBuilder> otomatik olarak oluşturmak için kullanılan komutlar; komutlarınızı açıkça belirtmeniz gerekir. Açıkça güncelleştirmeleri çözümlemek için komutları ayarlama hakkında bilgi için bir `DataSet` geri veri kaynağı için [veri kaynaklarıyla güncelleştirme DataAdapters](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md).  
  
 Çıkış parametreleri güncelleştirilmiş satırına eşlemek isteyebilirsiniz bir `DataSet`. Bir ortak görev bir otomatik olarak oluşturulan kimlik alanı değerini alma olması veya zaman damgası veri kaynağından. <xref:System.Data.Common.DbCommandBuilder> Çıkış parametreleri güncelleştirilmiş bir satır sütunlara varsayılan olarak eşleştirmez. Bu örnekte, komutunuzu açıkça belirtmeniz gerekir. Otomatik olarak oluşturulan kimlik alanına eklenen satırın geri bir sütununa eşleme örneği için bkz: [alma kimliği veya sayı değerlerini](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md).  
  
## <a name="rules-for-automatically-generated-commands"></a>Kuralları otomatik olarak oluşturulan komutları  
 Aşağıdaki tabloda komutları üretilen nasıl otomatik olarak oluşturulan için kuralları gösterir.  
  
|Komut|Kural|  
|-------------|----------|  
|`InsertCommand`|Veri kaynağı ile tablodaki tüm satırlar için bir satır ekler bir <xref:System.Data.DataRow.RowState%2A> , <xref:System.Data.DataRowState.Added>. Tüm güncelleştirilebilir sütunlar (ancak olmayan sütunları kimlikleri, ifadeler veya zaman damgası gibi) için değerleri ekler.|  
|`UpdateCommand`|Güncelleştirmeleri satır ile tablodaki tüm satırlar için veri kaynağında bir `RowState` , <xref:System.Data.DataRowState.Modified>. Kimlikler veya ifadeler gibi güncelleştirilebilir olmayan sütunları hariç tüm sütunları güncelleştirir. Tüm satırları sütun değerleri veri kaynağında satırın birincil anahtar sütun değerleri eşleştiğinde ve veri kaynağında kalan sütunlar satırın özgün değerlerine eşleştiğinde güncelleştirir. Daha fazla bilgi için "İyimser eşzamanlılık modeli için güncelleştirmeler ve siler," bölümüne bakın.|  
|`DeleteCommand`|Tüm satırların tablo ile veri kaynağında satırları siler bir `RowState` , <xref:System.Data.DataRowState.Deleted>. Tüm satırları sütun değerlerini satırın birincil anahtar sütun değerleri eşleştiğinde ve veri kaynağında kalan sütunlar satırın özgün değerlerine eşleştiğinde siler. Daha fazla bilgi için "İyimser eşzamanlılık modeli için güncelleştirmeler ve siler," bölümüne bakın.|  
  
## <a name="optimistic-concurrency-model-for-updates-and-deletes"></a>Güncelleştirmeleri ve silme için iyimser eşzamanlılık modeli  
 Komutları güncelleştirme ve silme deyimleri için otomatik olarak oluşturmak için mantığı dayanır *iyimser eşzamanlılık*--diğer bir deyişle, kayıtlarını düzenleme için kilitlenmiş değil ve diğer kullanıcılara veya işlemlere tarafından herhangi bir zamanda değiştirilebilir. Bir kayıt SELECT deyiminden döndürüldü, ancak UPDATE veya DELETE deyiminde verilmeden önce otomatik olarak oluşturulan UPDATE veya DELETE deyiminde WHERE yan tümcesi içeren sonra değiştirilmiş çünkü bir satır varsa yalnızca güncelleştirilir belirtme, Tüm orijinal değerleri içeren ve veri kaynağından silinmez. Bu, yeni verilerin üzerine yazılmasını önlemek için yapılır. Burada otomatik olarak oluşturulan bir güncelleştirmeyi dener, silinmiş veya bulunan özgün değerler içermeyen bir satırı güncelleştirme <xref:System.Data.DataSet>, komut herhangi bir kayıt etkilemez ve <xref:System.Data.DBConcurrencyException> atılır.  
  
 Özgün değerlere bakılmaksızın tamamlamak için güncelleştirme veya silme istiyorsanız, açıkça ayarlamalısınız `UpdateCommand` için `DataAdapter` ve üzerinde otomatik komut oluşturma değil.  
  
## <a name="limitations-of-automatic-command-generation-logic"></a>Otomatik komut oluşturma mantığı sınırlamaları  
 Aşağıdaki sınırlamalar otomatik komut oluşturma için geçerlidir.  
  
### <a name="unrelated-tables-only"></a>Yalnızca olmayan tablolar  
 Mantık ekleme, oluşturur otomatik komut oluşturma GÜNCELLEŞTİRMEK veya diğer tablolarla veri kaynağında herhangi bir ilişki dikkate alarak olmadan tek başına tablolar için deyimleri SİLİN. Sonuç olarak, çağrılırken bir hata karşılaşabilirsiniz `Update` bir yabancı anahtar kısıtlaması veritabanında yer aldığı bir sütun için değişiklikleri göndermek için. Bu özel durumun önlemek için kullanmayın <xref:System.Data.Common.DbCommandBuilder> sütunları yabancı anahtar kısıtlamasını; söz konusu güncelleştirmek için bunun yerine, açıkça işlemi gerçekleştirmek için kullanılan ifadelerini belirtin.  
  
### <a name="table-and-column-names"></a>Tablo ve sütun adları  
 Sütun adları veya tablo adları, boşluk, nokta, tırnak işaretleri veya diğer alfasayısal olmayan karakterler gibi özel karakterler içeriyorsa, otomatik komut oluşturma mantığı köşeli parantez ayrılmış olsa bile başarısız olabilir. Sağlayıcı bağlı olarak QuotePrefix ve QuoteSuffix parametrelerini ayarlama işlemi alanları oluşturma mantığı izin verebilir, ancak özel karakterlerinden Çık olamaz. Tablo adları biçiminde tam *catalog.schema.table* desteklenir.  
  
## <a name="using-the-commandbuilder-to-automatically-generate-an-sql-statement"></a>Otomatik olarak bir SQL deyimi oluşturmak için CommandBuilder kullanma  
 SQL deyimleri için otomatik olarak oluşturmak için bir `DataAdapter`, ilk `SelectCommand` özelliği `DataAdapter`, ardından oluşturun bir `CommandBuilder` nesne ve bağımsız değişken olarak belirtin `DataAdapter` kendisi için `CommandBuilder` otomatik olarak SQL deyimleri oluşturur.  
  
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
 Değiştirirseniz `CommandText` , `SelectCommand` INSERT, UPDATE veya DELETE komutları otomatik olarak oluşturulduktan sonra bir özel durum ortaya çıkabilir. Varsa değiştirilmiş `SelectCommand.CommandText` tutmuyor şema bilgileri içeriyor `SelectCommand.CommandText` kullanılan zaman ekleme, güncelleştirme veya komutları silmek olan otomatik olarak oluşturulan, gelecekteki çağrıları `DataAdapter.Update` yöntemi sütunları erişmek çalışabilir, tarafından başvurulan geçerli tablosundaki artık mevcut `SelectCommand`, ve bir özel durum.  
  
 Tarafından kullanılan şema bilgileri Yenile `CommandBuilder` çağırarak komutları otomatik olarak oluşturmak için `RefreshSchema` yöntemi `CommandBuilder`.  
  
 Hangi komutu otomatik olarak oluşturulan bilmek istiyorsanız, kullanarak otomatik olarak oluşturulan komutları başvuru edinebilirsiniz `GetInsertCommand`, `GetUpdateCommand`, ve `GetDeleteCommand` yöntemlerinin `CommandBuilder` nesne ve denetimi`CommandText`özelliği ilişkili komutu.  
  
 Aşağıdaki kod örneğinde, otomatik olarak oluşturulan güncelleştirme komutu konsola yazar.  
  
```  
Console.WriteLine(builder.GetUpdateCommand().CommandText)  
```  
  
 Aşağıdaki örnekte yeniden `Customers` tablosundaki `custDS` veri kümesi. **RefreshSchema** yöntemi, bu yeni sütun bilgileri otomatik olarak oluşturulan komutlarıyla yenilemek için çağrılır.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Komutlar ve Parametreler](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Komut Yürütme](../../../../docs/framework/data/adonet/executing-a-command.md)  
 [DbConnection, DbCommand ve DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET yönetilen sağlayıcıları ve veri kümesi Geliştirici Merkezi](http://go.microsoft.com/fwlink/?LinkId=217917)
