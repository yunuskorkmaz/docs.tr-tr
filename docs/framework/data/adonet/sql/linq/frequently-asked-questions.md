---
title: "Sıkça Sorulan Sorular"
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
ms.assetid: 252ed666-0679-4eea-b71b-2f14117ef443
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: edb48bd9cb0ff00c733af2d6ff4e616655a62b26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="frequently-asked-questions"></a>Sıkça Sorulan Sorular
Aşağıdaki bölümlerde, uyguladığınızda karşılaşabileceğiniz bazı yaygın sorunlar yanıt [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)].  
  
 Ek sorunlar ele içinde [sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md).  
  
## <a name="cannot-connect"></a>Bağlantı kurulamıyor  
 Q. Veritabanı için bağlantı kuramıyor.  
  
 BİR. Bağlantı dizesinin doğru olduğundan emin olun ve, [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] örneği çalışır. Ayrıca [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] adlandırılmış kanal protokolünün etkinleştirilmesi gerekir. Daha fazla bilgi için bkz: [tarafından izlenecek yollar öğrenme](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md).  
  
## <a name="changes-to-database-lost"></a>Kayıp veritabanındaki değişiklikleri  
 Q. I veritabanındaki veriler için bir değişiklik yapıldığında, ancak Uygulamam reran zaman değişikliği artık vardı.  
  
 BİR. Sizi aramasını emin olun <xref:System.Data.Linq.DataContext.SubmitChanges%2A> sonuçları veritabanına kaydetmek için.  
  
## <a name="database-connection-open-how-long"></a>Veritabanı bağlantısı: Ne kadar süreyle açılsın mı?  
 Q. Veritabanı bağlantım ne kadar süreyle açık kalacak?  
  
 BİR. Sorgu sonuçları tüketen kadar bağlantı genellikle açık kalır. Sürmesine bekliyorsanız, tüm sonuçları ve misiniz işlemek üzere değil sonuçları önbelleğe alma, Uygula <xref:System.Linq.Enumerable.ToList%2A> sorgulanamıyor. Her bir nesne yalnızca bir kez işlendiği burada ortak senaryolarda akış model hem de üstündedir `DataReader` ve [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
 Bağlantı kullanımı hakkında tam Ayrıntılar aşağıdakilere bağlıdır:  
  
-   Bağlantı durumu, <xref:System.Data.Linq.DataContext> bir bağlantı nesnesi ile oluşturulur.  
  
-   Bağlantı dizesi ayarları (örneğin, etkinleştirme birden fazla etkin sonuç kümesi (MARS). Daha fazla bilgi için bkz: [birden fazla etkin sonuç kümeleri (MARS)](../../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md).  
  
## <a name="updating-without-querying"></a>Sorgulama olmadan güncelleştiriliyor  
 Q. Tablo verisi ilk veritabanını sorgulama olmadan güncelleştirebilir miyim?  
  
 BİR. Ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kümesi tabanlı güncelleştirme komutları yok ilk sorgulama olmadan güncelleştirmek için aşağıdaki yöntemlerden birini kullanabilirsiniz:  
  
-   Kullanım <xref:System.Data.Linq.DataContext.ExecuteCommand%2A> SQL kodu göndermek için.  
  
-   Nesne yeni bir örneğini oluşturun ve güncelleştirme etkileyen tüm geçerli değerleri (alanları) başlatın. Nesneye iliştirmek <xref:System.Data.Linq.DataContext> kullanarak <xref:System.Data.Linq.Table%601.Attach%2A> ve değiştirmek istediğiniz alanı değiştirin.  
  
## <a name="unexpected-query-results"></a>Beklenmeyen sorgu sonuçları  
 Q. Sorguyu beklenmeyen sonuçlar veriyor. Nasıl ne oluştuğunu inceleyebilirsiniz?  
  
 BİR. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Bunu oluşturan SQL kodunu incelemek için çeşitli araçlar sağlar. En önemlisi, biri <xref:System.Data.Linq.DataContext.Log%2A>. Daha fazla bilgi için bkz: [hata ayıklama desteği](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md).  
  
## <a name="unexpected-stored-procedure-results"></a>Beklenmeyen saklı yordam sonuçları  
 Q. Dönüş değeri olarak hesaplanan bir saklı yordam sahip `MAX()`. Saklı yordam sürüklediğinizde ı [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] yüzey, dönüş değeri doğru değil.  
  
 BİR. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]saklı yordamlar aracılığıyla veritabanında oluşturulan değer döndürmek için iki yöntem sunar:  
  
-   Elde edilen sonucu adlandırılmasıyla.  
  
-   Çıktı parametresi açıkça belirterek.  
  
 Hatalı çıktı örneği verilmiştir. Çünkü [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] sonuçları eşlenemiyor her zaman 0 döndürür:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select max(i) from t where name like 'hello'`  
  
 `end`  
  
 Doğru bir çıkış çıktı parametresi kullanılarak verilmiştir:  
  
 `create procedure proc2`  
  
 `@result int OUTPUT`  
  
 `as`  
  
 `select @result = MAX(i) from t where name like 'hello'`  
  
 `go`  
  
 Doğru bir çıkış elde edilen sonucu adlandırılmasıyla verilmiştir:  
  
 `create procedure proc2`  
  
 `as`  
  
 `begin`  
  
 `select nax(i) AS MaxResult from t where name like 'hello'`  
  
 `end`  
  
 Daha fazla bilgi için bkz: [özelleştirme işlemleri tarafından kullanarak saklı yordamlar](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md).  
  
## <a name="serialization-errors"></a>Seri hale getirme hataları  
 Q. Seri hale getirmek çalıştığınızda aşağıdaki hatayı alıyorsunuz: "'System.Data.Linq.ChangeTracker+StandardChangeTracker' yazın... seri hale getirilebilir olarak işaretlenmemiş."  
  
 BİR. Kod oluşturma [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekleyen <xref:System.Runtime.Serialization.DataContractSerializer> seri hale getirme. Desteklemediği <xref:System.Xml.Serialization.XmlSerializer> veya <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Daha fazla bilgi için bkz: [seri hale getirme](../../../../../../docs/framework/data/adonet/sql/linq/serialization.md).  
  
## <a name="multiple-dbml-files"></a>Birden çok DBML dosyaları  
 Q. Bazı tablo ortak paylaşan birden çok DBML dosyaları varsa, bir derleyici hatası alın.  
  
 BİR. Ayarlama **bağlamı Namespace** ve **varlık Namespace** özelliklerinden [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] her DBML dosyası için farklı bir değere. Bu yaklaşım, ad/ad alanı çakışma ortadan kaldırır.  
  
## <a name="avoiding-explicit-setting-of-database-generated-values-on-insert-or-update"></a>INSERT veya Update üzerinde veritabanında oluşturulan değerlerin açık ayarı önleme  
 Q. Bir veritabanı tablosu ile sahip bir `DateCreated` SQL varsayılan olarak bir sütun `Getdate()`. Çalıştığımda kullanarak yeni bir kayıt eklemek [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)], değer kümesine `NULL`. Veritabanı varsayılan olarak ayarlanması için beklenir.  
  
 BİR. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Bu durumda otomatik olarak kimliği (otomatik artım) ve rowguıdcol (veritabanında oluşturulan GUID) ve zaman damgası sütunları işler. Diğer durumlarda, el ile ayarlamanız gerekir <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> = `true` ve <xref:System.Data.Linq.Mapping.ColumnAttribute.AutoSync%2A> = <xref:System.Data.Linq.Mapping.AutoSync.Always> / <xref:System.Data.Linq.Mapping.AutoSync.OnInsert> / <xref:System.Data.Linq.Mapping.AutoSync.OnUpdate> özellikleri.  
  
## <a name="multiple-dataloadoptions"></a>Birden çok DataLoadOptions  
 Q. Ek yükleme seçenekleri ilk yazmadan belirtebilir miyim?  
  
 BİR. Evet. İlk, aşağıdaki örnekte olduğu gibi geçersiz kılınmaz:  
  
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
 Q. Tabloları dışı sürüklediğinizde, bir hata alıyorsunuz bir [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] veritabanı.  
  
 BİR. [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Desteklemediği [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)], ancak [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] çalışma zamanı yapar. Bu durumda, kendi varlık sınıfları oluşturmak ve uygun özniteliklerini eklemeniz gerekir.  
  
## <a name="errors-in-inheritance-relationships"></a>Devralma ilişkisi hataları  
 Q. Araç kutusu devralma şeklinde kullanılan [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] bağlanmak için iki varlık, ancak hatayla karşılaşıyorsunuz.  
  
 BİR. İlişkiyi oluşturmak yeterli değildir. Ayrıştırıcı sütunun temel sınıf Ayrıştırıcıyı değeri gibi bilgileri sağlamanız gerekir ve türetilmiş sınıf Ayrıştırıcıyı değeri.  
  
## <a name="provider-model"></a>Sağlayıcı modeli  
 Q. Bir ortak sağlayıcı modeli var mı?  
  
 BİR. Kullanılabilir hiçbir ortak sağlayıcısı modelidir. Şu anda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] destekleyen [!INCLUDE[ssNoVersion](../../../../../../includes/ssnoversion-md.md)] ve [!INCLUDE[ssEW](../../../../../../includes/ssew-md.md)] yalnızca.  
  
## <a name="sql-injection-attacks"></a>SQL ekleme saldırıları  
 Q. Nasıl olduğunu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] SQL ekleme saldırılarından korumalı?  
  
 BİR. SQL ekleme, kullanıcı girişi birleştirerek biçimlendirilmiş geleneksel SQL sorguları için önemli bir riski olmuştur. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]kullanarak bu tür eklemesini önler <xref:System.Data.SqlClient.SqlParameter> sorgularda. Kullanıcı girişi parametre değerlerini çevrilir. Bu yaklaşım, müşteri girişten kullanılan kötü amaçlı komutlar engeller.  
  
## <a name="changing-read-only-flag-in-dbml-files"></a>DBML dosyaları salt okunur bayrağı değiştirme  
 Q. Nesne modeli DBML dosyasından oluşturduğunuzda nasıl bazı özelliklerinden ayarlayıcılar ortadan?  
  
 BİR. Bu gelişmiş senaryo için aşağıdaki adımları gerçekleştirin:  
  
1.  Değiştirerek özelliği .dbml dosyasında değişiklik <xref:System.Data.Linq.ITable.IsReadOnly%2A> bayrağını `True`.  
  
2.  Kısmi bir sınıf ekleyin. Bir oluşturucu parametrelerle salt okunur üyelerini oluşturun.  
  
3.  Varsayılan gözden <xref:System.Data.Linq.Mapping.UpdateCheck> değeri (<xref:System.Data.Linq.Mapping.UpdateCheck.Never>), uygulamanız için geçerli bir değer olup olmadığını belirlemek için.  
  
    > [!CAUTION]
    >  Kullanıyorsanız [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] içinde [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)], değişikliklerinizi üzerine yazılmış olabilir.  
  
## <a name="aptca"></a>APTCA  
 Q. System.Data.Linq kısmen güvenilen kod tarafından kullanılmak üzere işaretlenmiş mi?  
  
 BİR. Evet, System.Data.Linq.dll derleme de arasında bir değer [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] derlemeler ile işaretlenen <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği. Bu işaretleme, derlemelerde olmadan [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] yalnızca tam olarak güvenilen kod tarafından kullanılmak üzere tasarlanmıştır.  
  
 Asıl senaryoda [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] kısmen izin vererek arayanlar etkinleştirmek için güvenilir için [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Web uygulamalarından erişilebilmesi için derleme nerede *güven* Orta bir yapılandırmadır.  
  
## <a name="mapping-data-from-multiple-tables"></a>Birden çok tablodan veri eşleme  
 Q. My varlık verilerde birden çok tablodan gelir. Bunu nasıl eşleme?  
  
 BİR. Bir veritabanında bir görünüm oluşturun ve varlık görünümüne eşleyin. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]tablolar için yaptığı gibi aynı SQL görünümleri için oluşturur.  
  
> [!NOTE]
>  Bu senaryoda görünümlerin kullanımı sınırlamaları vardır. Üzerinde gerçekleştirilen işlemler zaman bu yaklaşımı en güvenli bir şekilde çalışır <xref:System.Data.Linq.Table%601> temel alınan görünüm tarafından desteklenir. Yalnızca hangi işlemleri tasarlanmıştır bildirin. Örneğin, çoğu uygulamayı salt okunurdur ve başka bir oldukça büyük numarası gerçekleştirmek `Create` / `Update` / `Delete` kullanarak işlemlerini yalnızca saklı yordamlar görünümleri karşı.  
  
## <a name="connection-pooling"></a>Bağlantı havuzu  
 Q. Var olan yardımcı olabilecek bir yapıdır <xref:System.Data.Linq.DataContext> havuzu?  
  
 BİR. Örneklerini yeniden yüklemeye çalışmayın <xref:System.Data.Linq.DataContext>. Her <xref:System.Data.Linq.DataContext> bir belirli bir düzenleme/sorgu oturumu için (bir kimlik önbellek dahil) durumunu korur. Veritabanı geçerli durumunu temel alan yeni örnekleri almak için yeni bir kullanın <xref:System.Data.Linq.DataContext>.  
  
 Arka plandaki kullanmaya devam edebilirsiniz [!INCLUDE[vstecado](../../../../../../includes/vstecado-md.md)] bağlantı havuzu. Daha fazla bilgi için bkz: [SQL Server bağlantı havuzu (ADO.NET)](../../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).  
  
## <a name="second-datacontext-is-not-updated"></a>İkinci DataContext güncelleştirilmez  
 Q. Tek bir örneğini kullanılan <xref:System.Data.Linq.DataContext> değerleri veritabanında depolamak için. Ancak, ikinci bir <xref:System.Data.Linq.DataContext> aynı veritabanında güncelleştirilen değerler yansıtmaz. İkinci <xref:System.Data.Linq.DataContext> örneği önbelleğe alınan değer döndürmek görünüyor.  
  
 BİR. Bu davranış tasarım gereğidir. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]aynı örnekleri/gördüğünüz ilk örnekte dönüş değerleri devam eder. Güncelleştirme yapmak için iyimser eşzamanlılık kullanın. Özgün veriler, aslında hala değiştirilmemiş olduğunu onaylanacak karşı geçerli veritabanı durumunu denetlemek için kullanılır. Değiştiyse, bir çakışma oluşur ve uygulamanızı çözümlenebilmesi gerekir. Geçerli veritabanı durumunu özgün durumuna sıfırlamak için ve güncelleştirmeyi yeniden denemek için uygulamanızın bir seçenektir. Daha fazla bilgi için bkz: [nasıl yapılır: yönetmek değişiklik çakışmaları](../../../../../../docs/framework/data/adonet/sql/linq/how-to-manage-change-conflicts.md).  
  
 Ayrıca ayarlayabilirsiniz <xref:System.Data.Linq.DataContext.ObjectTrackingEnabled%2A> hangi sırayla kapalı önbelleğe alma ve değişiklik izleme false. Ardından, sorgu her zaman en son değerleri alabilirsiniz.  
  
## <a name="cannot-call-submitchanges-in-read-only-mode"></a>Salt okunur modda SubmitChanges çağrılamıyor  
 Q. Çalıştığımda çağırmak <xref:System.Data.Linq.DataContext.SubmitChanges%2A> hata alıyorum salt okunur modda.  
  
 BİR. Salt okunur modda değişiklikleri izleme özelliğini bağlamının devre dışı bırakır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başvuru](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [Sorun giderme](../../../../../../docs/framework/data/adonet/sql/linq/troubleshooting.md)  
 [LINQ-SQL güvenlik](../../../../../../docs/framework/data/adonet/sql/linq/security-in-linq-to-sql.md)
