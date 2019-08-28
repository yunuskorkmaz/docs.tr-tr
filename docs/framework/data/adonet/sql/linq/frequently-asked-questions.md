---
title: Sıkça Sorulan Sorular
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 714ec7bda4f6c79b789d6c3029b68a04cef1342b
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041236"
---
# <a name="frequently-asked-questions"></a>Sıkça Sorulan Sorular

Aşağıdaki bölümlerde, uyguladığınızda [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]karşılaşabileceğiniz bazı yaygın sorunlar yanıtlanır.

[Sorun gidermede](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)ek sorunlar ele alınır.

## <a name="cannot-connect"></a>Bağlanamıyor

S. Veritabanıma bağlanamıyorum.

A. Bağlantı dizeniz doğru olduğundan ve SQL Server örneğinizin çalıştığından emin olun. Ayrıca adlandırılmış kanallar [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] protokolünün etkinleştirilmesini gerektirir. Daha fazla bilgi için bkz. [Izlenecek yollara göre öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).

## <a name="changes-to-database-lost"></a>Veritabanında yapılan değişiklikler kayboldu

S. Veritabanında verilerde bir değişiklik yaptık, ancak uygulamamı yeniden kaydederken değişiklik artık orada yoktu.

A. Sonuçları veritabanına kaydetmek için çağırdığınızdan <xref:System.Data.Linq.DataContext.SubmitChanges%2A> emin olun.

## <a name="database-connection-open-how-long"></a>Veritabanı bağlantısı: Ne kadar süreyle açık?

S. Veritabanı bağlantısı ne kadar süreyle açık kalır?

A. Sorgu sonuçlarını tüketene kadar bağlantı genellikle açık kalır. Tüm sonuçları işlemek için zaman almayı beklediğinizi ve sonuçların önbelleğe alınmasını istemiyorsanız, sorguya uygulayın <xref:System.Linq.Enumerable.ToList%2A> . Her nesnenin yalnızca bir kez işlendiği yaygın senaryolarda, akış modeli hem `DataReader` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]hem de ' de üst düzeydir.

Bağlantı kullanımının tam ayrıntıları aşağıdakilere bağlıdır:

- Bir bağlantı nesnesi ile <xref:System.Data.Linq.DataContext> oluşturulursa bağlantı durumu.

- Bağlantı dizesi ayarları (örneğin, birden çok etkin sonuç kümesi (MARS) etkinleştiriliyor. Daha fazla bilgi için bkz. [birden çok etkin sonuç kümesi (mars)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md).

## <a name="updating-without-querying"></a>Sorgulanmadan güncelleştirme

S. Veritabanını sorgulamadan tablo verilerini güncelleştirebilir miyim?

A. , [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Küme tabanlı güncelleştirme komutlarına sahip olmasa da, ilk sorgulanmadan güncelleştirmek için aşağıdaki tekniklerden birini kullanabilirsiniz:

- SQL <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> kodu göndermek için kullanın.

- Nesnenin yeni bir örneğini oluşturun ve güncelleştirmeyi etkileyen tüm geçerli değerleri (alanlar) başlatın. Sonra öğesini kullanarak <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.Table%601.Attach%2A> nesnesini öğesine ekleyin ve değiştirmek istediğiniz alanı değiştirin.

## <a name="unexpected-query-results"></a>Beklenmeyen sorgu sonuçları

S. Sorgum beklenmeyen sonuçlar döndürüyor. Ne olduğunu nasıl giderebilirim?

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]oluşturduğu SQL kodunu incelemek için çeşitli araçlar sağlar. En önemlileri <xref:System.Data.Linq.DataContext.Log%2A>bunlardan biridir. Daha fazla bilgi için bkz. [hata ayıklama desteği](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).

## <a name="unexpected-stored-procedure-results"></a>Beklenmeyen saklı yordam sonuçları

S. Dönüş değeri tarafından `MAX()`hesaplanan bir saklı yordamım var. Saklı yordamı O/R Designer yüzeyine sürükledikten sonra, dönüş değeri doğru değil.

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], saklı yordamlar yoluyla veritabanı tarafından oluşturulan değerleri döndürmek için iki yol sunar:

- Çıkış sonucunu adlandırarak.

- Açıkça bir çıkış parametresi belirterek.

Aşağıda yanlış çıktının bir örneği verilmiştir. Sonuçları [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] eşlemediğinden, her zaman 0 değerini döndürür:

```sql
create procedure proc2

as

begin

select max(i) from t where name like 'hello'

end
```

Aşağıda, çıkış parametresi kullanarak doğru çıkışın bir örneği verilmiştir:

```sql
create procedure proc2

@result int OUTPUT

as

select @result = MAX(i) from t where name like 'hello'

go
```

Aşağıda, çıkış sonucunu adlandırarak doğru çıkışın bir örneği verilmiştir:

```sql
create procedure proc2

as

begin

select nax(i) AS MaxResult from t where name like 'hello'

end
```

Daha fazla bilgi için bkz. [saklı yordamları kullanarak Işlemleri özelleştirme](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md).

## <a name="serialization-errors"></a>Serileştirme hataları

S. Seri hale getirme yapmayı denediğimde aşağıdaki hatayı alıyorum: "' System. Data. LINQ. ChangeTracker + StandardChangeTracker ' yazın... seri hale getirilebilir olarak işaretlenmemiş. "

A. İçindeki [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kod üretimi serileştirme <xref:System.Runtime.Serialization.DataContractSerializer> destekler. <xref:System.Xml.Serialization.XmlSerializer> Veya<xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>desteklemez. Daha fazla bilgi için bkz. [serileştirme](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md).

## <a name="multiple-dbml-files"></a>Birden çok DBML dosyası

S. Ortak olarak bazı tabloları paylaşan birden çok DBML dosyası olduğunda bir derleyici hatası alıyorum.

A. **Bağlam ad alanını** ve **varlık ad alanı** özelliklerini nesne ilişkisel Tasarımcısı her dbml dosyası için ayrı bir değere ayarlayın. Bu yaklaşım ad/ad alanı çarpışmasını ortadan kaldırır.

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>INSERT veya Update üzerinde veritabanı tarafından oluşturulan değerlerin açık ayarından kaçınma

S. `DateCreated` SQL`Getdate()`için varsayılan olarak bir sütun içeren bir veritabanı tablom var. Kullanarak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]yeni bir kayıt eklemeye çalıştığımda, değer olarak `NULL`ayarlanır. Veritabanının varsayılan olarak ayarlanmış olmasını bekler.

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kimlik (otomatik artış) ve ROWGUIDCOL (veritabanı tarafından üretilen GUID) ve zaman damgası sütunları için bu durumu otomatik olarak işler. Diğer durumlarda, ve <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> özellikleriniel= ile ayarlamanız `true` = gerekir. <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate>

## <a name="multiple-dataloadoptions"></a>Çoklu dataloadoçen

S. İlk üzerine yazmadan ek yükleme seçenekleri belirtebilir miyim?

A. Evet. Aşağıdaki örnekte olduğu gibi ilki üzerine yazılmaz:

```vb
Dim dlo As New DataLoadOptions()
dlo.LoadWith(Of Order)(Function(o As Order) o.Customer)
dlo.LoadWith(Of Order)(Function(o As Order) o.OrderDetails)
```

```csharp
DataLoadOptions dlo = new DataLoadOptions();
dlo.LoadWith<Order>(o => o.Customer);
dlo.LoadWith<Order>(o => o.OrderDetails);
```

## <a name="errors-using-sql-compact-35"></a>SQL Compact 3,5 kullanarak hatalar

S. SQL Server Compact 3,5 veritabanından tablo sürüklediğiniz zaman bir hata alıyorum.

A. Nesne İlişkisel Tasarımcısı, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çalışma zamanı olsa da, SQL Server Compact 3,5 'yi desteklemez. Bu durumda, kendi varlık sınıflarınızı oluşturmanız ve uygun öznitelikleri eklemeniz gerekir.

## <a name="errors-in-inheritance-relationships"></a>Devralma Ilişkilerinde hatalar

S. İki varlığa bağlanmak için Nesne İlişkisel Tasarımcısı araç kutusu devralma şeklini kullandım, ancak hata alıyorum.

A. İlişki oluşturma yeterli değildir. Ayrıştırıcı sütunu, taban sınıf ayrıştırıcı değeri ve türetilmiş sınıf ayrıştırıcı değeri gibi bilgileri sağlamanız gerekir.

## <a name="provider-model"></a>Sağlayıcı modeli

S. Ortak bir sağlayıcı modeli kullanılabilir mi?

A. Kullanılabilir ortak sağlayıcı modeli yok. Şu anda yalnızca SQL Server [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ve SQL Server Compact 3,5 destekler.

## <a name="sql-injection-attacks"></a>SQL ekleme saldırıları

S. SQL ekleme saldırılarından nasıl korunur?[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]

A. SQL ekleme, Kullanıcı girişini birleştirerek oluşturulan geleneksel SQL sorguları için önemli bir risk oldu. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]sorgularda kullanarak <xref:System.Data.SqlClient.SqlParameter> bu tür ekleme işlemini önler. Kullanıcı girişi parametre değerlerine açıktır. Bu yaklaşım, kötü amaçlı komutların müşteri girişinden kullanılmasını önler.

## <a name="changing-read-only-flag-in-dbml-files"></a>DBML dosyalarındaki salt okunurdur bayrağını değiştirme

S. DBML dosyasından bir nesne modeli oluştururken bazı özelliklerden ayarlayıcıları ortadan kaldırmak Nasıl yaparım??

A. Bu gelişmiş senaryo için aşağıdaki adımları uygulayın:

1. . Dbml dosyasında, <xref:System.Data.Linq.ITable.IsReadOnly%2A> bayrağını olarak `True`değiştirerek özelliği değiştirin.

2. Kısmi bir sınıf ekleyin. Salt okunurdur üyeleri için parametrelere sahip bir Oluşturucu oluşturun.

3. Uygulamanızın doğru değeri <xref:System.Data.Linq.Mapping.UpdateCheck> olup olmadığını<xref:System.Data.Linq.Mapping.UpdateCheck.Never>anlamak için varsayılan değeri () gözden geçirin.

    > [!CAUTION]
    > Visual Studio 'da Nesne İlişkisel Tasarımcısı kullanıyorsanız değişikliklerinizin üzerine yazılabilir.

## <a name="aptca"></a>APTCA

S. System. Data. Linq kısmen güvenilen kod tarafından kullanılmak üzere işaretlendi mi?

A. Evet, System. Data. LINQ. dll derlemesi, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliğiyle işaretlenmiş .NET Framework derlemeleri arasındadır. Bu işaret olmadan, .NET Framework derlemeler yalnızca tam olarak güvenilen kod tarafından kullanılmaya yöneliktir.

Kısmen güvenilen çağıranlara [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] izin vermek için içindeki asıl senaryo, *güven* yapılandırmasının [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Orta olduğu Web uygulamalarından erişilmesine imkan tanımalıdır.

## <a name="mapping-data-from-multiple-tables"></a>Birden çok tablodan veri eşleme

S. Varlığındaki veriler birden çok tablodan geliyor. Nasıl yaparım? eşleme yapılsın mı?

A. Veritabanında bir görünüm oluşturabilir ve varlığı görünüme eşleyebilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]görünümler için aynı SQL 'i tablolar için yaptığı gibi oluşturur.

> [!NOTE]
> Bu senaryodaki görünümlerin kullanımı sınırlamaları vardır. Bu yaklaşım, üzerinde <xref:System.Data.Linq.Table%601> gerçekleştirilen işlemler temel alınan görünüm tarafından desteklense de en güvenli şekilde gerçekleşir. Yalnızca hangi işlemlerin hedeflendiklerini bilirsiniz. Örneğin, çoğu uygulama salt okunurdur ve diğer bir boyutlandırılabilir sayı yalnızca görünümlerde uygulanan saklı yordamları `Create` kullanarak işlemleri gerçekleştirir `Delete` /. `Update` /

## <a name="connection-pooling"></a>Bağlantı Havuzu

S. <xref:System.Data.Linq.DataContext> Havuzda yardımcı olabilecek bir yapı var mı?

A. Örneklerini yeniden kullanmayı denemeyin <xref:System.Data.Linq.DataContext>. Her <xref:System.Data.Linq.DataContext> biri belirli bir düzenleme/sorgu oturumu için durumu (kimlik önbelleği dahil) korur. Veritabanının geçerli durumuna göre yeni örnekler almak için yeni <xref:System.Data.Linq.DataContext>bir kullanın.

Temel ADO.NET bağlantı havuzunu kullanmaya devam edebilirsiniz. Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).

## <a name="second-datacontext-is-not-updated"></a>İkinci DataContext güncelleştirilmedi

S. Değerlerini veritabanında depolamak <xref:System.Data.Linq.DataContext> için bir örneğini kullandım. Ancak, aynı veritabanında <xref:System.Data.Linq.DataContext> ikinci bir saniye güncelleştirilmiş değerleri yansıtmamaktadır. İkinci <xref:System.Data.Linq.DataContext> örnek, önbelleğe alınmış değerleri döndürüyor gibi görünüyor.

A. Bu davranış tasarıma göre yapılır. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]İlk örnekte gördüğünüz örneklerin/değerlerin aynısını döndürmeye devam eder. Güncelleştirmeler yaptığınızda iyimser eşzamanlılık kullanırsınız. Özgün veriler, gerçekten de değişmeden olduğunu doğrulamak üzere geçerli veritabanı durumunu denetlemek için kullanılır. Değiştirildiyse, bir çakışma oluşur ve uygulamanız bunu çözmelidir. Uygulamanızın bir seçeneği, özgün durumu geçerli veritabanı durumuna sıfırlamadır ve güncelleştirmeyi yeniden dener. Daha fazla bilgi için [nasıl yapılır: Değişiklik çakışmalarını](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md)yönetin.

Ayrıca, önbelleğe alma <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> ve değişiklik izlemeyi kapatan yanlış olarak ayarlayabilirsiniz. Daha sonra, her sorgumanızda en son değerleri alabilirsiniz.

## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Salt okuma modunda SubmitChanges çağrılamaz

S. Salt okuma modunda çağrı <xref:System.Data.Linq.DataContext.SubmitChanges%2A> yapmayı denediğimde bir hata alıyorum.

A. Salt okuma modu, içeriğin değişiklikleri izleme özelliğini devre dışı bırakır.

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [Sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)
- [LINQ to SQL’de Güvenlik](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)
