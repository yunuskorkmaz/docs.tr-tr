---
description: 'Hakkında daha fazla bilgi edinin: sık sorulan sorular'
title: Sık Sorulan Sorular
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 476e9adc3dc88bce786b8b8423e05e800c821320
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99739085"
---
# <a name="frequently-asked-questions"></a>Sık Sorulan Sorular

Aşağıdaki bölümlerde, LINQ uyguladığınızda karşılaşabileceğiniz bazı yaygın sorunlar yanıtlanacaktır.

[Sorun gidermede](troubleshooting.md)ek sorunlar ele alınır.

## <a name="cannot-connect"></a>Bağlanamıyor

S. Veritabanıma bağlanamıyorum.

A. Bağlantı dizeniz doğru olduğundan ve SQL Server örneğinizin çalıştığından emin olun. Ayrıca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] adlandırılmış kanallar protokolünün etkinleştirilmesini gerektirir. Daha fazla bilgi için bkz. [Izlenecek yollara göre öğrenme](learning-by-walkthroughs.md).

## <a name="changes-to-database-lost"></a>Veritabanında yapılan değişiklikler kayboldu

S. Veritabanında verilerde bir değişiklik yaptık, ancak uygulamamı yeniden kaydederken değişiklik artık orada yoktu.

A. <xref:System.Data.Linq.DataContext.SubmitChanges%2A>Sonuçları veritabanına kaydetmek için çağırdığınızdan emin olun.

## <a name="database-connection-open-how-long"></a>Veritabanı bağlantısı: ne kadar süreyle açık?

S. Veritabanı bağlantısı ne kadar süreyle açık kalır?

A. Sorgu sonuçlarını tüketene kadar bağlantı genellikle açık kalır. Tüm sonuçları işlemek için zaman almayı beklediğinizi ve sonuçların önbelleğe alınmasını istemiyorsanız, <xref:System.Linq.Enumerable.ToList%2A> sorguya uygulayın. Her nesnenin yalnızca bir kez işlendiği yaygın senaryolarda, akış modeli hem hem de ' de üst düzeydir `DataReader` [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] .

Bağlantı kullanımının tam ayrıntıları aşağıdakilere bağlıdır:

- <xref:System.Data.Linq.DataContext>Bir bağlantı nesnesi ile oluşturulursa bağlantı durumu.

- Bağlantı dizesi ayarları (örneğin, birden çok etkin sonuç kümesi (MARS) etkinleştiriliyor. Daha fazla bilgi için bkz. [birden çok etkin sonuç kümesi (mars)](../multiple-active-result-sets-mars.md).

## <a name="updating-without-querying"></a>Sorgulanmadan güncelleştirme

S. Veritabanını sorgulamadan tablo verilerini güncelleştirebilir miyim?

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], Küme tabanlı güncelleştirme komutlarına sahip olmasa da, ilk sorgulanmadan güncelleştirmek için aşağıdaki tekniklerden birini kullanabilirsiniz:

- <xref:System.Data.Linq.DataContext.ExecuteCommand%2A>SQL kodu göndermek için kullanın.

- Nesnenin yeni bir örneğini oluşturun ve güncelleştirmeyi etkileyen tüm geçerli değerleri (alanlar) başlatın. Sonra öğesini kullanarak nesnesini öğesine ekleyin <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.Table%601.Attach%2A> ve değiştirmek istediğiniz alanı değiştirin.

## <a name="unexpected-query-results"></a>Beklenmeyen sorgu sonuçları

S. Sorgum beklenmeyen sonuçlar döndürüyor. Ne olduğunu nasıl giderebilirim?

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] oluşturduğu SQL kodunu incelemek için çeşitli araçlar sağlar. En önemlileri bunlardan biridir <xref:System.Data.Linq.DataContext.Log%2A> . Daha fazla bilgi için bkz. [hata ayıklama desteği](debugging-support.md).

## <a name="unexpected-stored-procedure-results"></a>Beklenmeyen saklı yordam sonuçları

S. Dönüş değeri tarafından hesaplanan bir saklı yordamım var `MAX()` . Saklı yordamı O/R Designer yüzeyine sürükledikten sonra, dönüş değeri doğru değil.

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , saklı yordamlar yoluyla veritabanı tarafından oluşturulan değerleri döndürmek için iki yol sunar:

- Çıkış sonucunu adlandırarak.

- Açıkça bir çıkış parametresi belirterek.

Aşağıda yanlış çıktının bir örneği verilmiştir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Sonuçları eşlemediğinden, her zaman 0 değerini döndürür:

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

A. İçindeki kod üretimi [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Runtime.Serialization.DataContractSerializer> serileştirme destekler. <xref:System.Xml.Serialization.XmlSerializer>Veya desteklemez <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> . Daha fazla bilgi için bkz. [serileştirme](serialization.md).

## <a name="multiple-dbml-files"></a>Birden çok DBML dosyası

S. Ortak olarak bazı tabloları paylaşan birden çok DBML dosyası olduğunda bir derleyici hatası alıyorum.

A. **Bağlam ad alanını** ve **varlık ad alanı** özelliklerini nesne ilişkisel Tasarımcısı her dbml dosyası için ayrı bir değere ayarlayın. Bu yaklaşım ad/ad alanı çarpışmasını ortadan kaldırır.

## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>INSERT veya Update üzerinde Database-Generated değerlerinin açık ayarından kaçınma

S. SQL için varsayılan olarak bir sütun içeren bir veritabanı tablom var `DateCreated` `Getdate()` . Kullanarak yeni bir kayıt eklemeye çalıştığımda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] , değer olarak ayarlanır `NULL` . Veritabanının varsayılan olarak ayarlanmış olmasını bekler.

A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kimlik (otomatik artış) ve ROWGUIDCOL (veritabanı tarafından üretilen GUID) ve zaman damgası sütunları için bu durumu otomatik olarak işler. Diğer durumlarda, <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> = `true` ve <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> özelliklerini el ile ayarlamanız gerekir.

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

A. Nesne İlişkisel Tasarımcısı, çalışma zamanı olsa da, SQL Server Compact 3,5 'yi desteklemez [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] . Bu durumda, kendi varlık sınıflarınızı oluşturmanız ve uygun öznitelikleri eklemeniz gerekir.

## <a name="errors-in-inheritance-relationships"></a>Devralma Ilişkilerinde hatalar

S. İki varlığa bağlanmak için Nesne İlişkisel Tasarımcısı araç kutusu devralma şeklini kullandım, ancak hata alıyorum.

A. İlişki oluşturma yeterli değildir. Ayrıştırıcı sütunu, taban sınıf ayrıştırıcı değeri ve türetilmiş sınıf ayrıştırıcı değeri gibi bilgileri sağlamanız gerekir.

## <a name="provider-model"></a>Sağlayıcı modeli

S. Ortak bir sağlayıcı modeli kullanılabilir mi?

A. Kullanılabilir ortak sağlayıcı modeli yok. Şu anda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yalnızca SQL Server ve SQL Server Compact 3,5 destekler.

## <a name="sql-injection-attacks"></a>SQL-Injection saldırıları

S. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]SQL ekleme saldırılarından nasıl korunur?

A. SQL ekleme, Kullanıcı girişini birleştirerek oluşturulan geleneksel SQL sorguları için önemli bir risk oldu. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sorgularda kullanarak bu tür ekleme işlemini önler <xref:System.Data.SqlClient.SqlParameter> . Kullanıcı girişi parametre değerlerine açıktır. Bu yaklaşım, kötü amaçlı komutların müşteri girişinden kullanılmasını önler.

## <a name="changing-read-only-flag-in-dbml-files"></a>DBML dosyalarındaki salt okunurdur bayrağını değiştirme

S. DBML dosyasından bir nesne modeli oluştururken bazı özelliklerden ayarlayıcıları ortadan kaldırmak Nasıl yaparım??

A. Bu gelişmiş senaryo için aşağıdaki adımları uygulayın:

1. . Dbml dosyasında, bayrağını olarak değiştirerek özelliği değiştirin <xref:System.Data.Linq.ITable.IsReadOnly%2A> `True` .

2. Kısmi bir sınıf ekleyin. Salt okunurdur üyeleri için parametrelere sahip bir Oluşturucu oluşturun.

3. <xref:System.Data.Linq.Mapping.UpdateCheck> <xref:System.Data.Linq.Mapping.UpdateCheck.Never> Uygulamanızın doğru değeri olup olmadığını anlamak için varsayılan değeri () gözden geçirin.

    > [!CAUTION]
    > Visual Studio 'da Nesne İlişkisel Tasarımcısı kullanıyorsanız değişikliklerinizin üzerine yazılabilir.

## <a name="aptca"></a>APTCA

S. System. Data. Linq kısmen güvenilen kod tarafından kullanılmak üzere işaretlendi mi?

A. Evet, System.Data.Linq.dll derlemesi özniteliğiyle işaretlenen bu .NET Framework derlemelerinden arasındadır <xref:System.Security.AllowPartiallyTrustedCallersAttribute> . Bu işaret olmadan, .NET Framework derlemeler yalnızca tam olarak güvenilen kod tarafından kullanılmaya yöneliktir.

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Kısmen güvenilen çağıranlara izin vermek için içindeki asıl senaryo, [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] *güven* yapılandırmasının Orta olduğu Web uygulamalarından erişilmesine imkan tanımalıdır.

## <a name="mapping-data-from-multiple-tables"></a>Birden çok tablodan veri eşleme

S. Varlığındaki veriler birden çok tablodan geliyor. Nasıl yaparım? eşleme yapılsın mı?

A. Veritabanında bir görünüm oluşturabilir ve varlığı görünüme eşleyebilirsiniz. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] görünümler için aynı SQL 'i tablolar için yaptığı gibi oluşturur.

> [!NOTE]
> Bu senaryodaki görünümlerin kullanımı sınırlamaları vardır. Bu yaklaşım, üzerinde gerçekleştirilen işlemler <xref:System.Data.Linq.Table%601> temel alınan görünüm tarafından desteklense de en güvenli şekilde gerçekleşir. Yalnızca hangi işlemlerin hedeflendiklerini bilirsiniz. Örneğin, çoğu uygulama salt okunurdur ve diğer bir boyutlandırılabilir sayı `Create` / `Update` / `Delete` yalnızca görünümlerde uygulanan saklı yordamları kullanarak işlemleri gerçekleştirir.

## <a name="connection-pooling"></a>Bağlantı Havuzu

S. Havuzda yardımcı olabilecek bir yapı var <xref:System.Data.Linq.DataContext> mı?

A. Örneklerini yeniden kullanmayı denemeyin <xref:System.Data.Linq.DataContext> . Her biri <xref:System.Data.Linq.DataContext> belirli bir düzenleme/sorgu oturumu için durumu (kimlik önbelleği dahil) korur. Veritabanının geçerli durumuna göre yeni örnekler almak için yeni bir kullanın <xref:System.Data.Linq.DataContext> .

Temel ADO.NET bağlantı havuzunu kullanmaya devam edebilirsiniz. Daha fazla bilgi için bkz. [SQL Server bağlantı havuzu (ADO.net)](../../sql-server-connection-pooling.md).

## <a name="second-datacontext-is-not-updated"></a>İkinci DataContext güncelleştirilmedi

S. <xref:System.Data.Linq.DataContext>Değerlerini veritabanında depolamak için bir örneğini kullandım. Ancak, aynı veritabanında ikinci bir saniye <xref:System.Data.Linq.DataContext> güncelleştirilmiş değerleri yansıtmamaktadır. İkinci <xref:System.Data.Linq.DataContext> örnek, önbelleğe alınmış değerleri döndürüyor gibi görünüyor.

A. Bu davranış tasarım gereğidir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] İlk örnekte gördüğünüz örneklerin/değerlerin aynısını döndürmeye devam eder. Güncelleştirmeler yaptığınızda iyimser eşzamanlılık kullanırsınız. Özgün veriler, gerçekten de değişmeden olduğunu doğrulamak üzere geçerli veritabanı durumunu denetlemek için kullanılır. Değiştirildiyse, bir çakışma oluşur ve uygulamanız bunu çözmelidir. Uygulamanızın bir seçeneği, özgün durumu geçerli veritabanı durumuna sıfırlamadır ve güncelleştirmeyi yeniden dener. Daha fazla bilgi için bkz. [nasıl yapılır: değişiklik çakışmalarını yönetme](how-to-manage-change-conflicts.md).

Ayrıca <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> , önbelleğe alma ve değişiklik izlemeyi kapatan yanlış olarak ayarlayabilirsiniz. Daha sonra, her sorgumanızda en son değerleri alabilirsiniz.

## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Salt okuma modunda SubmitChanges çağrılamaz

S. <xref:System.Data.Linq.DataContext.SubmitChanges%2A>Salt okuma modunda çağrı yapmayı denediğimde bir hata alıyorum.

A. Salt okuma modu, içeriğin değişiklikleri izleme özelliğini devre dışı bırakır.

## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](reference.md)
- [Sorun giderme](troubleshooting.md)
- [LINQ to SQL’de Güvenlik](security-in-linq-to-sql.md)
