---
title: Sıkça Sorulan Sorular
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
ms.openlocfilehash: 07801ee7bfbb32540880cdc8599e5b69797b09f9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67743546"
---
# <a name="frequently-asked-questions"></a>Sıkça Sorulan Sorular
Aşağıdaki bölümlerde, uyguladığınızda karşılaşabileceğiniz bazı yaygın sorunlar yanıt [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 Ek sorunlar açıklanmıştır [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="cannot-connect"></a>Bağlantı kurulamıyor  
 S. Veritabanım için bağlanamıyorum.  
  
 A. Bağlantı dizenizi doğru olduğundan ve SQL Server örneğinizin çalıştığından emin olun. Ayrıca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] adlandırılmış kanal protokolünün etkinleştirilmesi gerekir. Daha fazla bilgi için [izlenecek yollarla öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
## <a name="changes-to-database-lost"></a>Kayıp veritabanında yapılan değişiklikler  
 S. Ben veritabanındaki veriler için bir değişiklik yapıldığında, ancak ben Uygulamam reran, değişiklik artık oluştu.  
  
 A. Çağırmanızı emin <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sonuçları veritabanına kaydetmek için.  
  
## <a name="database-connection-open-how-long"></a>Veritabanı bağlantısı: Ne kadar süreyle açılsın mı?  
 S. Veritabanı bağlantım ne kadar süre açık kalır?  
  
 A. Sorgu sonuçları tükettiğiniz kadar bağlantı genellikle açık kalır. Biraz bekliyorsanız tüm olan ve sonuçları işlemek üzere karşılık sonuçları önbelleğe alma, Uygula <xref:System.Linq.Enumerable.ToList%2A> sorgulanamıyor. Her bir nesnenin yalnızca bir kez işlendiği nerede yaygın senaryolarda, akış modelinde hem de üstün `DataReader` ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Bağlantı kullanımı hakkında tam Ayrıntılar aşağıdakilere bağlıdır:  
  
- Bağlantı durumu, <xref:System.Data.Linq.DataContext> ile bir bağlantı nesnesi oluşturulur.  
  
- Bağlantı dizesi ayarlarını (örneğin, etkinleştirme birden çok etkin sonuç kümesi (MARS). Daha fazla bilgi için [birden çok etkin sonuç kümesi (MARS)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md).  
  
## <a name="updating-without-querying"></a>Sorgulama olmadan güncelleştiriliyor  
 S. Tablo verilerini ilk veritabanını sorgulama olmadan güncelleştirebilir miyim?  
  
 A. Ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] set tabanlı güncelleştirme komutları yok. ilk sorgulama olmadan güncelleştirmek için aşağıdaki tekniklerden birini kullanabilirsiniz:  
  
- Kullanım <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> SQL kod gönderilecek.  
  
- Nesnesinin yeni bir örneğini oluşturun ve güncelleştirme etkileyen tüm geçerli değerleri (alanlar) başlatır. Ardından nesneye ekleyin <xref:System.Data.Linq.DataContext> kullanarak <xref:System.Data.Linq.Table%601.Attach%2A> ve değiştirmek istediğiniz alanı değiştirin.  
  
## <a name="unexpected-query-results"></a>Beklenmeyen sorgu sonuçları  
 S. Sorgum beklenmeyen sonuçlar döndürüyor. Nasıl nasıl bir durumla karşılaşıyorsunuz inceleyebilirsiniz?  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] ürettiği SQL kodunu incelemek için çeşitli araçlar sağlar. En önemli biri <xref:System.Data.Linq.DataContext.Log%2A>. Daha fazla bilgi için [hata ayıklama desteği](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="unexpected-stored-procedure-results"></a>Beklenmeyen bir saklı yordam sonuçları  
 S. Dönüş değeri tarafından hesaplanan bir saklı yordam sahibim `MAX()`. Saklı yordam O/R Tasarımcısı yüzeyine sürüklediğinizde, dönüş değeri doğru değil.  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] veritabanı tarafından oluşturulan değerleri depolanmış yordamlar yoluyla döndürmek için iki yol sunar:  
  
- Çıkış sonucu adlandırarak.  
  
- Çıkış parametresi açıkça belirterek.  
  
 Yanlış çıktının bir örneği verilmiştir. Çünkü [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sonuçları eşlenemez her zaman 0 değerini döndürür:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select max(i) from t where name like 'hello'`  
  
 `end`  
  
 Doğru çıktının bir örneği bir output parametresi kullanarak verilmiştir:  
  
 `create procedure proc2`  
  
 `@result int OUTPUT`  
  
 `as`  
  
 `select @result = MAX(i) from t where name like 'hello'`  
  
 `go`  
  
 Doğru çıktının bir örneği sonucu adlandırarak verilmiştir:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select nax(i) AS MaxResult from t where name like 'hello'`  
  
 `end`  
  
 Daha fazla bilgi için [özelleştirme işlemleri tarafından kullanarak saklı yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md).  
  
## <a name="serialization-errors"></a>Serileştirme hataları  
 S. Seri hale getirmek çalıştığınızda şu hatayı alıyorum: "... 'System.Data.Linq.ChangeTracker+StandardChangeTracker' türü seri hale getirilebilir olarak işaretlenmemiş."  
  
 A. Kod oluşturma işleminde [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekler <xref:System.Runtime.Serialization.DataContractSerializer> seri hale getirme. Desteklemediği <xref:System.Xml.Serialization.XmlSerializer> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Daha fazla bilgi için [serileştirme](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md).  
  
## <a name="multiple-dbml-files"></a>Birden çok DBML dosyaları  
 S. Bazı tablolar ortak paylaşan birden çok DBML dosyaları sahibim, bir derleyici hatası alıyorum.  
  
 A. Ayarlama **bağlam Namespace** ve **varlık Namespace** Nesne İlişkisel Tasarımcısı özelliklerinden her DBML dosyasının farklı bir değer. Bu yaklaşım, ad/ad alanı çakışma ortadan kaldırır.  
  
## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>Veritabanı tarafından oluşturulan değerleri ekleme veya güncelleştirme ayarı açık kaçınma  
 S. Bir veritabanı tablosu ile sahibim bir `DateCreated` SQL varsayılan sütun `Getdate()`. Kullanarak yeni bir kayıt eklemek çalıştığımda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], değer kümesine `NULL`. Veritabanı varsayılan olarak ayarlanması için beklenir.  
  
 A. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu durum kimlik (otomatik artış) ve rowguıdcol (veritabanı tarafından oluşturulan GUID) ve zaman damgası sütunları için otomatik olarak işler. Diğer durumlarda, el ile ayarlamanız <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> = `true` ve <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> özellikleri.  
  
## <a name="multiple-dataloadoptions"></a>Birden çok DataLoadOptions  
 S. Ek yükü seçenekleri ilk yazmadan belirtebilir miyim?  
  
 A. Evet. Birincisi, aşağıdaki örnekte olduğu gibi yazılmaz:  
  
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
  
## <a name="errors-using-sql-compact-35"></a>SQL kullanarak hataları Compact 3.5  
 S. Ben dışında bir SQL Server Compact 3.5 veritabanı tabloları sürüklediğinizde bir hata alıyorum.  
  
 A. Nesne İlişkisel Tasarımcısı SQL Server Compact 3.5, ancak desteklememektedir [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çalışma zamanı yapar. Bu durumda, kendi varlık sınıfları oluşturma ve uygun öznitelikleri eklemeniz gerekir.  
  
## <a name="errors-in-inheritance-relationships"></a>Devralma ilişkilerinde hataları  
 S. Araç kutusu devralma şekli Nesne İlişkisel Tasarımcısı'nda iki varlık bağlanmak için kullandım, ancak hata alıyorum.  
  
 A. İlişki oluşturmak yeterli değildir. Ayrıştırıcı sütununu temel sınıf ayrıştırıcı değeri gibi bilgiler sağlamanız gerekir ve türetilen sınıf ayrıştırıcı değeri.  
  
## <a name="provider-model"></a>Sağlayıcı modeli  
 S. Bir ortak sağlayıcı modeli kullanılabilir mi?  
  
 A. Hiçbir genel sağlayıcı modeli kullanılabilir. Şu anda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] yalnızca SQL Server ve SQL Server Compact 3.5 destekler.  
  
## <a name="sql-injection-attacks"></a>SQL ekleme saldırıları  
 S. Nasıl olduğunu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL ekleme saldırılarına karşı korunuyor?  
  
 A. SQL ekleme, kullanıcı girişini birleştirerek biçimlendirilmiş geleneksel SQL sorguları için önemli bir risk olmuştur. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Bu tür ekleme kullanarak önler <xref:System.Data.SqlClient.SqlParameter> sorgularda. Kullanıcı girişi parametre değerlerini etkinleştirilir. Bu yaklaşım, kötü amaçlı komutlar müşteri girişten kullanılmasını engeller.  
  
## <a name="changing-read-only-flag-in-dbml-files"></a>DBML dosyaları salt okunur bayrağı değiştirme  
 S. Bir nesne modeli DBML dosyasından oluşturduğunuzda nasıl bazı özelliklerinden ayarlayıcılar ortadan?  
  
 A. Bu gelişmiş bir senaryo için aşağıdaki adımları uygulayın:  
  
1. Değiştirerek .dbml dosyasına da özelliği değiştirilecek <xref:System.Data.Linq.ITable.IsReadOnly%2A> bayrak `True`.  
  
2. Kısmi bir sınıf ekleyin. Bir oluşturucu parametrelerle salt okunur üyeler için oluşturun.  
  
3. Varsayılan gözden geçirme <xref:System.Data.Linq.Mapping.UpdateCheck> değeri (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>), uygulamanız için doğru değeri olup olmadığını belirlemek için.  
  
    > [!CAUTION]
    >  Visual Studio'da Nesne İlişkisel Tasarımcısı'nı kullanıyorsanız, değişikliklerinizi yazılabilir.  
  
## <a name="aptca"></a>APTCA  
 S. System.Data.Linq kısmen güvenilen kod tarafından kullanılmak üzere işaretlenmiş mi?  
  
 A. Evet, System.Data.Linq.dll ile işaretlenmiş bu .NET Framework derlemeleri arasında derlemesidir <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği. Bu işaretleme olmadan, yalnızca tam olarak güvenilen kod tarafından kullanım için .NET Framework derlemeleri amacını taşımaktadır.  
  
 Asıl senaryoda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kısmen izin vererek çağıranlar etkinleştirmek için güvenilen için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Web uygulamalarından erişilecek derleme burada *güven* Orta bir yapılandırmadır.  
  
## <a name="mapping-data-from-multiple-tables"></a>Birden çok tablodan veri eşleme  
 S. My varlığındaki veriler birden çok tablodan gelir. Bunu nasıl eşleştiği?  
  
 A. Bir veritabanında bir görünüm oluşturma ve harita görünümü için varlık. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] tablolar için yaptığı gibi görünümler için aynı SQL oluşturur.  
  
> [!NOTE]
>  Bu senaryoda görünümleri kullanımını sınırlamaları vardır. Üzerinde gerçekleştirilen işlemler, bu yaklaşım en güvenli bir şekilde çalışır <xref:System.Data.Linq.Table%601> temel alınan görünümü tarafından desteklenir. Yalnızca hangi işlemlerin hedeflenen bildirin. Örneğin, çoğu uygulama salt okunurdur ve başka bir büyük sayı gerçekleştirmek `Create` / `Update` / `Delete` kullanarak işlemlerini yalnızca saklı yordamlar görünümleri karşı.  
  
## <a name="connection-pooling"></a>Bağlantı Havuzu  
 S. Yardımcı bir yapısı var. <xref:System.Data.Linq.DataContext> havuzu?  
  
 A. Örneklerini yeniden denemeyin <xref:System.Data.Linq.DataContext>. Her <xref:System.Data.Linq.DataContext> tek bir belirli düzenleme/sorgu oturum için (kimlik önbellek dahil) durumu korur. Veritabanının mevcut durumuna göre yeni örnekler elde etmek için yeni bir kullanın <xref:System.Data.Linq.DataContext>.  
  
 Temel alınan ADO.NET bağlantı havuzu kullanmaya devam edebilirsiniz. Daha fazla bilgi için [SQL Server Connection Pooling (ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="second-datacontext-is-not-updated"></a>İkinci DataContext güncelleştirilmemiş  
 S. Bir örneği kullandım <xref:System.Data.Linq.DataContext> değerleri veritabanında depolamak için. Ancak, ikinci bir <xref:System.Data.Linq.DataContext> aynı veritabanında güncelleştirilmiş değerleri yansıtmaz. İkinci <xref:System.Data.Linq.DataContext> örneği gibi görünüyor önbelleğe alınan değer döndürmek için.  
  
 A. Bu davranış tasarım gereğidir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aynı örnek/gördüğünüz ağdaki ilk örnek dönüş değerleri devam eder. Güncelleştirmeler yapmak için iyimser eşzamanlılığı kullanın. Özgün veriler, aslında hala değiştirilmemiş olduğunu onaylamak için karşı geçerli veritabanı durumunu denetlemek için kullanılır. Değiştiyse, bir çakışma oluşur ve uygulamanızı çözmeniz gerekir. Geçerli veritabanı durumuna özgün durumuna Sıfırla ve güncelleştirmeyi yeniden denemek için uygulamanızın bir seçenektir. Daha fazla bilgi için [nasıl yapılır: Değişiklik çakışmalarını yönetme](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 Ayrıca <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> hangi sırayla kapalı önbelleğe alma ve değişiklik izleme false. Ardından, en son değerleri, sorgu her zaman alabilir.  
  
## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Salt okunur modda SubmitChanges çağrılamıyor  
 S. Çağrılacak çalıştığımda <xref:System.Data.Linq.DataContext.SubmitChanges%2A> salt okunur modda bir hata alıyorum.  
  
 A. Salt okunur modda değişiklikleri izleme özelliğini bağlam devre dışı bırakır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [Sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)
- [LINQ to SQL’de Güvenlik](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)
