---
title: Sıkça Sorulan Sorular
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 3cc879e97438138554f1d39cf588e01bfbba28a6
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634709"
---
# <a name="frequently-asked-questions"></a>Sıkça Sorulan Sorular

Aşağıdaki bölümlerde, LINQ uyguladığınızda karşılaşabileceğiniz bazı yaygın sorunlar yanıtlanacaktır.

[Sorun gidermede](troubleshooting.md)ek sorunlar ele alınır.

## <a name="cannot-connect"></a>Bağlanamıyor

S. Veritabanıma bağlanamıyorum.

BİR. Bağlantı dizeniz doğru olduğundan ve SQL Server örneğinizin çalıştığından emin olun. Ayrıca, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] adlandırılmış kanallar protokolünün etkinleştirilmesini gerektirir. Daha fazla bilgi için bkz. [Izlenecek yollara göre öğrenme](learning-by-walkthroughs.md).

## <a name="changes-to-database-lost"></a>Veritabanında yapılan değişiklikler kayboldu

S. Veritabanında verilerde bir değişiklik yaptık, ancak uygulamamı yeniden kaydederken değişiklik artık orada yoktu.

BİR. Sonuçları veritabanına kaydetmek için <xref:System.Data.Linq.DataContext.SubmitChanges%2A> çağırdığınızdan emin olun.

## <a name="database-connection-open-how-long"></a>Veritabanı bağlantısı: ne kadar süreyle açık?

S. Veritabanı bağlantısı ne kadar süreyle açık kalır?

BİR. Sorgu sonuçlarını tüketene kadar bağlantı genellikle açık kalır. Tüm sonuçları işlemek için zaman almayı beklemeniz ve sonuçların önbelleğe alınmasına izin vermek istiyorsanız sorguya <xref:System.Linq.Enumerable.ToList%2A> uygulayın. Her nesnenin yalnızca bir kez işlendiği yaygın senaryolarda, akış modeli hem `DataReader` hem de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]üst düzeydir.

Bağlantı kullanımının tam ayrıntıları aşağıdakilere bağlıdır:

- <xref:System.Data.Linq.DataContext> bağlantı nesnesi ile oluşturulursa bağlantı durumu.

- Bağlantı dizesi ayarları (örneğin, birden çok etkin sonuç kümesi (MARS) etkinleştiriliyor. Daha fazla bilgi için bkz. [birden çok etkin sonuç kümesi (mars)](../multiple-active-result-sets-mars.md).

## <a name="updating-without-querying"></a>Sorgulanmadan güncelleştirme

S. Veritabanını sorgulamadan tablo verilerini güncelleştirebilir miyim?

BİR. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ayarlanan tabanlı güncelleştirme komutlarına sahip olmasa da, öncelikle güncelleştirme yapmak için aşağıdaki tekniklerden birini kullanabilirsiniz:

- SQL kodu göndermek için <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> kullanın.

- Nesnenin yeni bir örneğini oluşturun ve güncelleştirmeyi etkileyen tüm geçerli değerleri (alanlar) başlatın. Sonra, <xref:System.Data.Linq.Table%601.Attach%2A> kullanarak nesneyi <xref:System.Data.Linq.DataContext> ekleyin ve değiştirmek istediğiniz alanı değiştirin.

## <a name="unexpected-query-results"></a>Beklenmeyen sorgu sonuçları

S. Sorgum beklenmeyen sonuçlar döndürüyor. Ne olduğunu nasıl giderebilirim?

BİR. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], oluşturduğu SQL kodunu incelemek için çeşitli araçlar sağlar. En önemlileri bunlardan biri <xref:System.Data.Linq.DataContext.Log%2A>. Daha fazla bilgi için bkz. [hata ayıklama desteği](debugging-support.md).

## <a name="unexpected-stored-procedure-results"></a>Beklenmeyen saklı yordam sonuçları

S. Dönüş değeri `MAX()`tarafından hesaplanan bir saklı yordamım var. Saklı yordamı O/R Designer yüzeyine sürükledikten sonra, dönüş değeri doğru değil.

BİR. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], saklı yordamlar yoluyla veritabanı tarafından oluşturulan değerleri döndürmek için iki yol sunar:

- Çıkış sonucunu adlandırarak.

- Açıkça bir çıkış parametresi belirterek.

Aşağıda yanlış çıktının bir örneği verilmiştir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sonuçları eşlemediğinden, her zaman 0 değerini döndürür:

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

Daha fazla bilgi için bkz. [saklı yordamları kullanarak Işlemleri özelleştirme](customizing-operations-by-using-stored-procedures.md).

## <a name="serialization-errors"></a>Serileştirme hataları

S. Seri hale getirme yapmayı denediğimde şu hatayı alıyorum: "System. Data. LINQ. ChangeTracker + StandardChangeTracker ' yazın... seri hale getirilebilir olarak işaretlenmemiş. "

BİR. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kod üretimi <xref:System.Runtime.Serialization.DataContractSerializer> Serileştirmeyi destekler. <xref:System.Xml.Serialization.XmlSerializer> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>desteklemez. Daha fazla bilgi için bkz. [serileştirme](serialization.md).

## <a name="multiple-dbml-files"></a>Birden çok DBML dosyası

S. Ortak olarak bazı tabloları paylaşan birden çok DBML dosyası olduğunda bir derleyici hatası alıyorum.

BİR. **Bağlam ad alanını** ve **varlık ad alanı** özelliklerini nesne ilişkisel Tasarımcısı her dbml dosyası için ayrı bir değere ayarlayın. Bu yaklaşım ad/ad alanı çarpışmasını ortadan kaldırır.

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>INSERT veya Update üzerinde veritabanı tarafından oluşturulan değerlerin açık ayarından kaçınma

S. SQL `Getdate()`varsayılan olarak `DateCreated` sütunu olan bir veritabanı tablom var. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kullanarak yeni bir kayıt eklemeye çalıştığımda, değer `NULL`olarak ayarlanır. Veritabanının varsayılan olarak ayarlanmış olmasını bekler.

BİR. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kimlik (otomatik artış) ve ROWGUIDCOL (veritabanı tarafından üretilen GUID) ve zaman damgası sütunları için bu durumu otomatik olarak işler. Diğer durumlarda, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>=`true` ve <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A>=<xref:System.Data.Linq.Mapping.AutoSync.Always>/<xref:System.Data.Linq.Mapping.AutoSync.OnInsert>/özelliklerini el ile ayarlamanız gerekir.

## <a name="multiple-dataloadoptions"></a>Çoklu dataloadoçen

S. İlk üzerine yazmadan ek yükleme seçenekleri belirtebilir miyim?

BİR. Evet. Aşağıdaki örnekte olduğu gibi ilki üzerine yazılmaz:

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

BİR. Nesne İlişkisel Tasarımcısı, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çalışma zamanı olsa da SQL Server Compact 3,5 ' i desteklemez. Bu durumda, kendi varlık sınıflarınızı oluşturmanız ve uygun öznitelikleri eklemeniz gerekir.

## <a name="errors-in-inheritance-relationships"></a>Devralma Ilişkilerinde hatalar

S. İki varlığa bağlanmak için Nesne İlişkisel Tasarımcısı araç kutusu devralma şeklini kullandım, ancak hata alıyorum.

BİR. İlişki oluşturma yeterli değildir. Ayrıştırıcı sütunu, taban sınıf ayrıştırıcı değeri ve türetilmiş sınıf ayrıştırıcı değeri gibi bilgileri sağlamanız gerekir.

## <a name="provider-model"></a>Sağlayıcı modeli

S. Ortak bir sağlayıcı modeli kullanılabilir mi?

BİR. Kullanılabilir ortak sağlayıcı modeli yok. Şu anda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL Server ve yalnızca 3,5 SQL Server Compact destekler.

## <a name="sql-injection-attacks"></a>SQL ekleme saldırıları

S. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL ekleme saldırılarından nasıl korunur?

BİR. SQL ekleme, Kullanıcı girişini birleştirerek oluşturulan geleneksel SQL sorguları için önemli bir risk oldu. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], sorgularda <xref:System.Data.SqlClient.SqlParameter> kullanarak bu tür ekleme işlemini önler. Kullanıcı girişi parametre değerlerine açıktır. Bu yaklaşım, kötü amaçlı komutların müşteri girişinden kullanılmasını önler.

## <a name="changing-read-only-flag-in-dbml-files"></a>DBML dosyalarındaki salt okunurdur bayrağını değiştirme

S. DBML dosyasından bir nesne modeli oluştururken bazı özelliklerden ayarlayıcıları ortadan kaldırmak Nasıl yaparım??

BİR. Bu gelişmiş senaryo için aşağıdaki adımları uygulayın:

1. . Dbml dosyasında, <xref:System.Data.Linq.ITable.IsReadOnly%2A> bayrağını `True`değiştirerek özelliği değiştirin.

2. Kısmi bir sınıf ekleyin. Salt okunurdur üyeleri için parametrelere sahip bir Oluşturucu oluşturun.

3. Uygulamanızın doğru değeri olup olmadığını öğrenmek için varsayılan <xref:System.Data.Linq.Mapping.UpdateCheck> değerini (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>) gözden geçirin.

    > [!CAUTION]
    > Visual Studio 'da Nesne İlişkisel Tasarımcısı kullanıyorsanız değişikliklerinizin üzerine yazılabilir.

## <a name="aptca"></a>APTCA

S. System. Data. Linq kısmen güvenilen kod tarafından kullanılmak üzere işaretlendi mi?

BİR. Evet, System. Data. LINQ. dll derlemesi, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliğiyle işaretlenmiş .NET Framework derlemeleri arasındadır. Bu işaret olmadan, .NET Framework derlemeler yalnızca tam olarak güvenilen kod tarafından kullanılmaya yöneliktir.

Kısmi güvenilir arayanlara izin vermek için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ' deki asıl senaryo, *güven* yapılandırmasının Orta olduğu Web uygulamalarından [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] derlemeye erişilmesine imkan tanımalıdır.

## <a name="mapping-data-from-multiple-tables"></a>Birden çok tablodan veri eşleme

S. Varlığındaki veriler birden çok tablodan geliyor. Nasıl yaparım? eşleme yapılsın mı?

BİR. Veritabanında bir görünüm oluşturabilir ve varlığı görünüme eşleyebilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], görünümler için aynı SQL 'i tablolar için yaptığı gibi oluşturur.

> [!NOTE]
> Bu senaryodaki görünümlerin kullanımı sınırlamaları vardır. Bu yaklaşım, <xref:System.Data.Linq.Table%601> üzerinde gerçekleştirilen işlemler temel alınan görünüm tarafından desteklense de en güvenli şekilde gerçekleşir. Yalnızca hangi işlemlerin hedeflendiklerini bilirsiniz. Örneğin, çoğu uygulama salt okunurdur ve başka bir boyutlandırılabilir sayı, yalnızca görünümlerde yapılan saklı yordamları kullanarak /`Delete` işlemleri `Update``Create`/.

## <a name="connection-pooling"></a>Bağlantı Havuzu

S. <xref:System.Data.Linq.DataContext> havuzda yardımcı olabilecek bir yapı var mı?

BİR. <xref:System.Data.Linq.DataContext>örneklerini yeniden kullanmayı denemeyin. Her <xref:System.Data.Linq.DataContext>, belirli bir düzenleme/sorgu oturumu için durumu (kimlik önbelleği dahil) korur. Veritabanının geçerli durumuna göre yeni örnekler almak için yeni bir <xref:System.Data.Linq.DataContext>kullanın.

Temel ADO.NET bağlantı havuzunu kullanmaya devam edebilirsiniz. Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../../sql-server-connection-pooling.md).

## <a name="second-datacontext-is-not-updated"></a>İkinci DataContext güncelleştirilmedi

S. Değerleri veritabanında depolamak için bir <xref:System.Data.Linq.DataContext> örneği kullandım. Ancak, aynı veritabanındaki ikinci bir <xref:System.Data.Linq.DataContext> güncelleştirilmiş değerleri yansıtmamaktadır. İkinci <xref:System.Data.Linq.DataContext> örnek, önbelleğe alınmış değerler döndürüyor gibi görünüyor.

BİR. Bu davranış tasarım gereğidir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], ilk örnekte gördüğünüz örnekleri/değerleri döndürmeye devam eder. Güncelleştirmeler yaptığınızda iyimser eşzamanlılık kullanırsınız. Özgün veriler, gerçekten de değişmeden olduğunu doğrulamak üzere geçerli veritabanı durumunu denetlemek için kullanılır. Değiştirildiyse, bir çakışma oluşur ve uygulamanız bunu çözmelidir. Uygulamanızın bir seçeneği, özgün durumu geçerli veritabanı durumuna sıfırlamadır ve güncelleştirmeyi yeniden dener. Daha fazla bilgi için bkz. [nasıl yapılır: değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md).

Ayrıca, önbelleğe alma ve değişiklik izlemeyi kapatan <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> false olarak ayarlayabilirsiniz. Daha sonra, her sorgumanızda en son değerleri alabilirsiniz.

## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Salt okuma modunda SubmitChanges çağrılamaz

S. <xref:System.Data.Linq.DataContext.SubmitChanges%2A> salt okunurdur modda çağırmaya çalıştığımda bir hata alıyorum.

BİR. Salt okuma modu, içeriğin değişiklikleri izleme özelliğini devre dışı bırakır.

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](reference.md)
- [Sorun giderme](troubleshooting.md)
- [LINQ to SQL’de Güvenlik](security-in-linq-to-sql.md)
