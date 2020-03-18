---
title: Mikro hizmet başına veritabanı
description: Monolitik ve bulut ait uygulamalarda kontrast veri depolama.
author: robvet
ms.date: 01/22/2020
ms.openlocfilehash: c0c5611fa866d70f155e4bdad2eee1181b13c065
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141451"
---
# <a name="database-per-microservice"></a>Mikro hizmet başına veritabanı

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu kitapta gördüğümüz gibi, bulut açi yaklaşımı uygulamaları tasarlama, dağıtma ve yönetme şeklinizi değiştirir. Ayrıca, verileri yönetme ve depolama şeklinizi de değiştirir.

Şekil 5-1 farklılıkları karşılar.

![Bulut ayarı uygulamalarda veri depolama](./media/distributed-data.png)

**Şekil 5-1**. Bulut ait uygulamalarda veri yönetimi

Deneyimli geliştiriciler şekil 5-1'in sol tarafındaki mimariyi kolayca tanıyacaktır. Bu *yekpare uygulamada,* iş hizmeti bileşenleri paylaşılan bir hizmet katmanında bir araya getirin ve tek bir ilişkisel veritabanından veri paylaşır.

Birçok yönden, tek bir veritabanı veri yönetimini basit tutar. Verileri birden çok tabloda sorgulamak kolaydır. Verilerde yapılan değişiklikler birlikte güncellenir veya hepsi geri alır. [ACID işlemleri](https://docs.microsoft.com/windows/desktop/cossdk/acid-properties) güçlü ve anında tutarlılığı garanti altına adamaktadır.

Bulut-yerli için tasarım, farklı bir yaklaşım benimsiyoruz. Şekil 5-1'in sağ tarafında, iş işlevlerinin küçük, bağımsız mikro hizmetlere nasıl ayrıştırdığını unutmayın. Her microservice belirli bir iş yeteneği ve kendi verilerini kapsüller. Yekpare veritabanı, her biri bir microservice ile hizalayan çok daha küçük veritabanları ile dağıtılmış bir veri modeli ne ayrılır. Duman temizlendiğinde, *mikrohizmet başına*bir veritabanı ortaya çıkaran bir tasarım ile ortaya çıkar.

## <a name="why"></a>Neden?

Mikro hizmet başına bu veritabanı, özellikle hızla gelişmesi ve büyük ölçekli desteklenmesi gereken sistemler için birçok avantaj sağlar. Bu model ile...

- Etki alanı verileri hizmet içinde kapsüllenir
- Veri şeması diğer hizmetleri doğrudan etkilemeden gelişebilir
- Her veri deposu bağımsız olarak ölçeklendirilebilir
- Bir hizmetteki veri deposu hatası diğer hizmetleri doğrudan etkilemez

Verileri ayırma, her bir mikro hizmetin iş yükü, depolama gereksinimleri ve okuma/yazma desenleri için en iyi şekilde optimize edilmiş veri deposu türünü uygulamasına da olanak tanır. Seçenekler ilişkisel, belge, anahtar değeri ve hatta grafik tabanlı veri depolarını içerir.

Şekil 5-2, bulut-yerel bir sistemde çok dillikalıcılık ilkesini sunar.

![Polyglot veri kalıcılığı](./media/polyglot-data-persistence.png)

**Şekil 5-2**. Polyglot veri kalıcılığı

Önceki şekilde, her bir mikro hizmetin farklı türde bir veri deposunu nasıl desteklediğini not edin.

- Ürün kataloğu microservice, temel verilerinin zengin ilişkisel yapısını karşılamak için ilişkisel bir veritabanı tüketir.
- Alışveriş sepeti microservice, basit, anahtar değerli veri deposunu destekleyen dağıtılmış bir önbellek tüketir.
- Sipariş microservice, yüksek hacimli okuma işlemlerini karşılamak için hem yazma işlemleri için bir NoSql belge veritabanı hem de son derece denormalleştirilmiş anahtar/değer deposu tüketir.
  
İlişkisel veritabanları karmaşık verilere sahip mikro hizmetler için geçerli liğini korurken, NoSQL veritabanları önemli ölçüde popülerlik kazanmıştır. Onlar büyük ölçekli ve yüksek kullanılabilirlik sağlar. Onların şemasız doğası geliştiricilerin bozuk para ve zaman alıcı yapmak dakti-sa'lık veri sınıfları ve ORM'ler mimarisinden uzaklaşmalarını sağlar. Bu bölümde noSQL veritabanlarını daha sonra ele alıyoruz.

 Verileri ayrı mikro hizmetlere kapsülleme çevikliği, performansı ve ölçeklenebilirliği artırabilirken, aynı zamanda birçok zorluk da sunar. Bir sonraki bölümde, bu zorlukların üstesinden gelinmeye yardımcı olacak kalıplar ve uygulamalarla birlikte tartışAcağız.  

## <a name="cross-service-queries"></a>Servisler arası sorgular

Mikro hizmetler bağımsız olsa da ve envanter, sevkiyat veya sipariş gibi belirli işlevsel yeteneklere odaklanırken, sık sık diğer mikro hizmetlerle tümleştirme gerektirir. Genellikle tümleştirme, bir microservice'in diğerini veri *sorgulamasını* içerir. Şekil 5-3 senaryoyu gösterir.

![Mikro hizmetler arasında sorgulama](./media/cross-service-query.png)

**Şekil 5-3**. Mikro hizmetler arasında sorgulama

Önceki şekilde, kullanıcının alışveriş sepetine bir öğe ekleyen bir alışveriş sepeti microservice görüyoruz. Bu mikro hizmetin veri deposu sepet ve satır öğesi verileri içerse de, ürün veya fiyatlandırma verilerini korumaz. Bunun yerine, bu veri öğeleri katalog ve fiyatlandırma mikroservices aittir. Bu bir sorun teşkil sunuyor. Alışveriş sepeti microservice, veritabanında ürün veya fiyatlandırma verileri yoksa, kullanıcının alışveriş sepetine nasıl ürün ekleyebilir?

Bölüm 4'te tartışılan seçeneklerden biri, alışveriş sepetinden katalog ve fiyatlandırma mikro hizmetlerine [doğrudan http çağrısıdır.](service-to-service-communication.md#queries) Ancak, bölüm 4, biz senkron HTTP *birlikte çift* mikrohizmetleri çağırır, onların özerklik azaltarak ve mimari yararları azalan söyledi.

Ayrıca, her hizmet için ayrı gelen ve giden kuyrukları içeren bir istek yanıtde deseni uygulayabiliriz. Ancak, bu desen karmaşıktır ve istek ve yanıt iletilerini ilişkilendirmek için tesisat gerektirir.
Arka uç mikrohizmet çağrılarını ayırmak la birlikte, arama hizmeti yine de çağrının tamamlanmasını eşzamanlı olarak beklemelidir. Ağ tıkanıklığı, geçici hatalar veya aşırı yüklü bir mikro hizmet, uzun süreli ve hatta başarısız işlemlere neden olabilir.

Bunun yerine, çapraz hizmet bağımlılıklarını kaldırmak için yaygın olarak kabul gören bir desen, Şekil 5-4'te gösterilen [Materyalize Görünüm Deseni'dir.](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)

![Maddeleştirilmiş görünüm deseni](./media/materialized-view-pattern.png)

**Şekil 5-4**. Gerçekleştirilmiş Görünüm Düzeni

Bu desenle, alışveriş sepeti hizmetine yerel bir veri tablosu *(okuma modeli*olarak bilinir) yersiniz. Bu tablo, ürün ve fiyatlandırma mikroservices gerekli verilerin normalleştirilmiş bir kopyasını içerir. Verilerin doğrudan alışveriş sepetine kopyalanması, pahalı servisler arası çağrılara duyulan ihtiyacı ortadan kaldırır. Hizmete yerel verilerle, hizmetin yanıt süresini ve güvenilirliğini artırırsınız. Ayrıca, verilerin kendi kopyasına sahip olmak alışveriş sepeti hizmetini daha esnek hale getirir. Katalog hizmeti kullanılamıyorsa, alışveriş sepeti hizmetini doğrudan etkilemez. Alışveriş sepeti kendi mağazasından gelen verilerle çalışmaya devam edebilir.

Bu yaklaşımın yakaladığı fark, artık sisteminizde yinelenen verilerin olmasıdır. Ancak, bulut-yerel sistemlerde verileri *stratejik olarak* çoğaltmak yerleşik bir uygulamadır ve bir anti-desen veya kötü uygulama olarak kabul edilmez. Bir ve *tek bir hizmetin* bir veri kümesine sahip olabileceğini ve bu konuda yetkisahibi olabileceğini unutmayın. Kayıt sistemi güncelleştirildiğinde okunan modelleri eşitlemeniz gerekir. Senkronizasyon genellikle Şekil 5.4'te gösterildiği gibi, [yayımla/abone](service-to-service-communication.md#events)oltasıyla eşzamanlı mesajlaşma yoluyla uygulanır.

## <a name="distributed-transactions"></a>Dağıtılmış işlemler

Mikro hizmetler arasında veri sorgulamak zor olsa da, çeşitli mikro hizmetler arasında bir işlem uygulamak daha da karmaşıktır. Farklı mikro hizmetlerde bağımsız veri kaynakları arasında veri tutarlılığını korumanın doğasında var olan zorluk hafife alınamaz. Bulut ait uygulamalarda dağıtılmış hareketlerin olmaması, dağıtılmış hareketleri programlı bir şekilde yönetmeniz gerektiği anlamına gelir. *Hemen tutarlılık* lı bir dünyadan nihai *tutarlılığa geçersiniz.*

Şekil 5-5 sorunu gösterir.

![Destan deseninde işlem](./media/saga-transaction-operation.png)

**Şekil 5-5**. Mikro hizmetler arasında bir işlem uygulama

Önceki şekilde, beş bağımsız mikro hizmet bir sipariş oluşturan dağıtılmış bir işlem katılır. Her microservice kendi veri deposu tutar ve deposu için yerel bir işlem uygular. Siparişi oluşturmak için, *her bir* mikro hizmet için yerel işlemin başarılı olması veya *tüm* işlemin iptal edilip geri alması gerekir. Yerleşik işlem desteği her mikro hizmetin içinde kullanılabilir olsa da, verileri tutarlı tutmak için beş hizmete de yayılan dağıtılmış bir işlem için destek yoktur.

Bunun yerine, bu dağıtılmış hareketi *programlı bir şekilde*oluşturmanız gerekir.

Dağıtılmış işlem desteği eklemek için popüler bir desen Saga desenidir. Yerel işlemleri programlı ve sıralı olarak gruplandırarak uygulanır. Yerel işlemlerden herhangi biri başarısız olursa, Destan işlemi iptal eder ve telafi [edici hareketler](https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction)kümesi çağırır. Telafi edici hareketler, önceki yerel hareketler tarafından yapılan değişiklikleri geri alar ve veri tutarlılığını geri yükler. Şekil 5-6, Saga deseniyle başarısız bir işlemi gösterir.

![Destan deseninde geri dön](./media/saga-rollback-operation.png)

**Şekil 5-6**. Bir hareketi geri alma

Önceki şekilde, *Stok güncelleştirme* işlemi Stok mikrohizmetinde başarısız oldu. Destan, stok sayımlarını ayarlamak, ödemeyi ve siparişi iptal etmek ve her mikro hizmetiçin verileri tutarlı bir duruma döndürmek için bir dizi telafi hareketi (kırmızı) çağırır.

Destan desenleri genellikle ilgili olaylar dizisi olarak koreografisi yapılır veya ilgili komutlar kümesi olarak düzenlenmiştir. Bölüm 4'te, planlı bir destan uygulamasının temelini oluşturabilecek hizmet toplayıcı modelini tartıştık. Ayrıca, koreografisi yapılan bir destan uygulamasının temelini oluşturabilecek Azure Hizmet Veri Tos ve Azure Event Grid konularıyla birlikte etkinliği de tartıştık.

## <a name="high-volume-data"></a>Yüksek hacimli veriler

Büyük bulut tabanlı uygulamalar genellikle yüksek hacimli veri gereksinimlerini destekler. Bu senaryolarda, geleneksel veri depolama teknikleri darboğazlara neden olabilir. Büyük ölçekte dağıtılan karmaşık sistemler için, hem Komut hem de Sorgu Sorumluluğu Ayrımı (CQRS) ve Olay Kaynağı uygulama performansını artırabilir.  

### <a name="cqrs"></a>CQRS

[CQRS](https://docs.microsoft.com/azure/architecture/patterns/cqrs), performans, ölçeklenebilirlik ve güvenliği en üst düzeye çıkarmaya yardımcı olabilecek mimari bir desendir. Desen, verileri okuyan işlemleri veri yazan işlemlerden ayırır.

Normal senaryolar için, aynı varlık modeli ve veri deposu nesnesi hem okuma *hem de* yazma işlemleri için kullanılır.

Ancak, yüksek hacimli bir veri senaryosu okuma ve yazma için ayrı modeller ve veri tablolarından yararlanabilir. Performansı artırmak için, okuma işlemi pahalı yinelenen tablo birleştirmeleri ve tablo kilitleri önlemek için verilerin son derece denormalleştirilmiş gösterimi karşı sorgu olabilir. *Komut*olarak bilinen *yazma* işlemi, tutarlılığı garanti edecek verilerin tamamen normalleştirilmiş bir temsiline karşı güncellenir. Daha sonra her iki gösterimi eşit tutmak için bir mekanizma uygulamanız gerekir. Genellikle, yazma tablosu değiştirildiğinde, okuma tablosunda yapılan değişikliği çoğaltan bir olay yayımlar.

Şekil 5-7 CQRS deseninin bir uygulamasını gösterir.

![Komut ve Sorgu Sorumluluğu Ayrımı](./media/cqrs-implementation.png)

**Şekil 5-7**. CQRS uygulaması

Önceki şekilde, ayrı komut ve sorgu modelleri uygulanır. Her veri yazma işlemi yazma deposuna kaydedilir ve daha sonra okuma deposuna yayılır. Veri yayma işleminin [nihai tutarlılık](http://www.cloudcomputingpatterns.org/eventual_consistency/)ilkesine göre nasıl işlediğine dikkat edin. Okuma modeli sonunda yazma modeli yle eşitlenir, ancak işlemde bazı gecikmeler olabilir. Bir sonraki bölümde nihai tutarlılığı tartışıyoruz.

Bu ayrım okuma ve yazmanın bağımsız olarak ölçeklemesini sağlar. Okuma işlemleri sorgular için en iyi duruma getirilmiş bir şema kullanırken, yazmalar güncelleştirmeler için en iyi duruma getirilmiş bir şema kullanır. Okuma sorguları normalize edilmiş verilere ters gider, karmaşık iş mantığı yazma modeline uygulanabilir. Yanı sıra, yazma işlemlerine, teşhir okumalardan daha sıkı güvenlik dayatabilirsiniz.

CQRS uygulanması, bulut ait hizmetler için uygulama performansını artırabilir. Ancak, daha karmaşık bir tasarım alabın. Bu ilkeyi bulut yerel uygulamanızın bundan yararlanacak bölümlerine dikkatli ve stratejik bir şekilde uygulayın. CQRS hakkında daha fazla bilgi için Microsoft kitabı [.NET Microservices: Architecture for Containerized .NET Applications](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns)bölümüne bakın.

### <a name="event-sourcing"></a>Olay kaynak

Yüksek hacimli veri senaryolarını optimize etmek için başka bir yaklaşım [Olay Kaynak](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing)içerir.

Sistem genellikle bir veri varlığının geçerli durumunu depolar. Örneğin, bir kullanıcı telefon numarasını değiştirirse, müşteri kaydı yeni numarayla güncelleştirilir. Bir veri varlığının geçerli durumunu her zaman biliriz, ancak her güncelleştirme önceki durumu yazar.

Çoğu durumda, bu model iyi çalışır. Ancak, yüksek hacimli sistemlerde, işlem kilitleme ve sık güncelleştirme işlemlerinden kaynaklanan ek yük veritabanı performansını, yanıt verme yeteneğini ve ölçeklenebilirliği sınırlayabilir.

Olay Kaynak veri yakalama için farklı bir yaklaşım alır. Verileri etkileyen her işlem bir olay deposunda kalıcıdır. Bir veri kaydının durumunu güncelleştirmek yerine, her değişikliği bir muhasebecinin genel muhasebesine benzer şekilde geçmiş olayların sıralı listesine ekleriz. Olay Deposu, veriler için kayıt sistemi haline gelir. Bir mikro hizmetin sınırlı bağlamında çeşitli materyalize görünümleri yaymak için kullanılır. Şekil 5.8 deseni gösterir.

![Olay Kaynağını Belirleme](./media/event-sourcing.png)

**Şekil 5-8**. Olay Kaynağını Belirleme

Önceki şekilde, bir kullanıcının alışveriş sepetine ait her girişin (mavi renkte) temel bir etkinlik deposuna nasıl eklenilen bir şekilde eklenilenlere dikkat edin. Bitişik maddeleştirilmiş görünümde, sistem her alışveriş sepetiyle ilişkili tüm olayları yeniden oynatarak geçerli durumu projeleri. Bu görünüm veya okuma modeli, daha sonra geri UI maruz kalır. Olaylar, dış sistemler ve uygulamalarla da tümleştirilebilir veya bir varlığın geçerli durumunu belirlemek için sorgulanabilir. Bu yaklaşımla, tarihi korursunuz. Sadece bir varlığın durumunu değil, aynı zamanda bu duruma nasıl ulaştığınızı da biliyorsunuz.

Mekanik olarak konuşursak, olay kaynak yazma modelini basitleştirir. Güncelleştirme veya silme yok. Her veri girişini değişmez bir olay olarak ekleyen, ilişkisel veritabanlarıyla ilişkili çekişme, kilitleme ve eşzamanlılık çakışmalarını en aza indirir. Materyalize görünüm deseni ile okuma modelleri oluşturma, görünümü yazma modelinden ayırmanızı ve uygulama kullanıcı larınızın gereksinimlerini en iyi duruma getirmek için en iyi veri deposunu seçmenize olanak tanır.

Bu desen için, olay kaynağını doğrudan destekleyen bir veri deposu düşünün. Azure Cosmos DB, MongoDB, Cassandra, CouchDB ve RavenDB iyi adaylardır.

Tüm kalıpve teknolojilerde olduğu gibi, stratejik ve gerektiğinde uygulayın. Olay kaynak artan performans ve ölçeklenebilirlik sağlayabilir iken, karmaşıklık ve bir öğrenme eğrisi pahasına gelir.

>[!div class="step-by-step"]
>[Önceki](service-mesh-communication-infrastructure.md)
>[Sonraki](relational-vs-nosql-data.md)
