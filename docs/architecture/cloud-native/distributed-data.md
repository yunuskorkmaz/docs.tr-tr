---
title: Dağıtılmış veriler
description: Tek parçalı ve bulutta yerel uygulamalardaki veri depolama alanını kontrast.
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: b7c8c43b16f2f70f9009c4fe4a8d19c52fa7ea2a
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91163940"
---
# <a name="distributed-data"></a>Dağıtılmış veriler

Bu kitapta gördüğünüze göre, bulutta yerel bir yaklaşım, uygulamaları tasarlama, dağıtma ve yönetme şeklini değiştirir. Ayrıca verileri yönetme ve depolama şeklini de değiştirir.

Şekil 5-1, farkları karşıtlıkları.

![Bulutta yerel uygulamalarda veri depolama](./media/distributed-data.png)

**Şekil 5-1**. Bulutta yerel uygulamalarda veri yönetimi

Deneyimli geliştiriciler, Şekil 5-1 ' nin sol tarafında bulunan mimariyi kolayca tanıyacaktır. Bu *tek parçalı uygulamada*, iş hizmeti bileşenleri, tek bir ilişkisel veritabanından veri paylaşarak paylaşılan bir hizmet katmanında birlikte bir araya sahiptir.

Birçok şekilde, tek bir veritabanı veri yönetimini basit tutar. Verileri birden çok tablo genelinde sorgulama basittir. Veri güncelleştirmesiyle birlikte yapılan değişiklikler veya hepsi geri alma. [ACID işlemleri](/windows/desktop/cossdk/acid-properties) güçlü ve anında tutarlılığı garanti eder.

Bulutta yerel olarak tasarlamak için farklı bir yaklaşım sunuyoruz. Şekil 5-1 ' nin sağ tarafında, iş işlevselliğinin küçük, bağımsız mikro hizmetlere nasıl ayırt edici olduğunu göz önünde ayırın. Her mikro hizmet belirli bir iş özelliğini ve kendi verilerini kapsar. Tek parçalı veritabanı, her biri bir mikro hizmetle hizalanan çok daha küçük veritabanları ile dağıtılmış bir veri modeline sahiptir. Duman temizlediğinde, *mikro hizmet başına bir veritabanı*sunan tasarımla karşılaştık.

## <a name="database-per-microservice-why"></a>Veritabanı başına mikro hizmet, neden?

Mikro hizmet başına bu veritabanı, özellikle hızlı bir şekilde gelişen ve büyük ölçekli ölçeklendirmeyi destekleyen sistemler için birçok avantaj sağlar. Bu modelle...

- Etki alanı verileri, hizmet içinde kapsüllenir
- Veri şeması, diğer hizmetleri doğrudan etkilemeden geliştirebilirsiniz
- Her veri deposu bağımsız olarak ölçeklendirilebilecek
- Bir hizmette veri deposu hatası diğer hizmetleri doğrudan etkilemez

Verilerin ayrılması, her mikro hizmetin iş yükü, depolama ihtiyacı ve okuma/yazma desenleri için en iyi duruma getirilmiş veri depolama türünü uygulamasına olanak sağlar. Seçimler ilişkisel, belge, anahtar-değer, hatta grafik tabanlı veri depoları içerir.

Şekil 5-2, bulut Yerel sisteminde çok yönlü kalıcılığı ilkesini gösterir.

![Çok yönlü veri kalıcılığı](./media/polyglot-data-persistence.png)

**Şekil 5-2**. Çok yönlü veri kalıcılığı

Önceki şekilde, her mikro hizmetin farklı bir veri deposu türünü nasıl desteklediğine göz önünde.

- Ürün kataloğu mikro hizmeti, temel alınan verilerinin zengin ilişkisel yapısına uyum sağlamak için bir ilişkisel veritabanı kullanır.
- Alışveriş Sepeti mikro hizmeti, basit, anahtar-değer veri deposunu destekleyen bir dağıtılmış önbellek kullanır.
- Sıralama mikro hizmeti, yazma işlemleri için hem NoSql belge veritabanını hem de Yüksek hacimlerdeki okuma işlemlerine uyum sağlamak için yüksek hacimli bir anahtar/değer deposu kullanır.
  
İlişkisel veritabanları, karmaşık verilerle mikro hizmetler için uygun olmaya devam ederken, NoSQL veritabanları önemli popülerliği kazanmıştır. Büyük ölçekli ve yüksek kullanılabilirlik sağlarlar. Şeicilerin, veri sınıflarının bir mimarisinden ve ORMs de daha pahalı ve zaman alıcı bir mimariden uzaklaşmasını sağlar. Bu bölümün ilerleyen kısımlarında NoSQL veritabanları ele alınmaktadır.

 Verileri ayrı mikro hizmetlere kapsüllemek, çevikliği, performansı ve ölçeklenebilirliği artırabilir, ayrıca birçok zorluk da sunar. Sonraki bölümde, bu güçlükleri ve bunların üstesinden gelmelerine yardımcı olacak desenler ve uygulamalarla birlikte tartıştık.  

## <a name="cross-service-queries"></a>Çapraz hizmet sorguları

Mikro hizmetler bağımsızdır ve Inventory, Shipping veya sıralaması gibi belirli işlevsel yeteneklere odaklanırken, genellikle diğer mikro hizmetlerle tümleştirme gerektirir. Genellikle tümleştirme, verileri bir tane *sorgulayan* bir mikro hizmet içerir. Şekil 5-3, senaryoyu gösterir.

![Mikro hizmetler genelinde sorgulama](./media/cross-service-query.png)

**Şekil 5-3**. Mikro hizmetler genelinde sorgulama

Yukarıdaki şekilde, bir kullanıcının alışveriş sepetine bir öğe ekleyen bir alışveriş sepeti mikro hizmeti görüyoruz. Bu mikro hizmet için veri deposu sepet ve satır öğesi verileri içerdiğinde, ürün veya fiyatlandırma verilerinin bakımını yapmaz. Bunun yerine, bu veri öğeleri kataloğa ve fiyatlandırma mikro hizmetlerine aittir. Bu bir sorunu gösterir. Alışveriş Sepeti mikro hizmeti, veritabanında ürün veya fiyatlandırma verileri yoksa kullanıcının alışveriş sepetine bir ürün ekleyebilir mi?

Bölüm 4 ' te açıklanan bir seçenek, alışveriş sepetinden kataloğa ve fiyatlandırma mikro hizmetlerine yönelik [doğrudan BIR http çağrıdır](service-to-service-communication.md#queries) . Ancak, Bölüm 4 ' te, zaman uyumlu HTTP her *iki* mikro hizmeti birlikte çağırıyor, bağımsız çalışma sınırı ve bunların mimari avantajlarını azalttık.

Ayrıca, her hizmet için ayrı gelen ve giden kuyruklarla bir istek-yanıt modelini uygulayabiliriz. Ancak bu model karmaşıktır ve istek ve yanıt iletilerinin ilişkilendirilmesi için yeniden tesisat gerektirir.
Arka uç mikro hizmet çağrılarını ayırdığından, çağıran hizmetin hala zaman uyumlu olarak çağrının tamamlanmasını beklemesi gerekir. Ağ tıkanıklığı, geçici hatalar veya aşırı yüklenmiş mikro hizmet, uzun süre çalışan ve hatta başarısız işlemlere neden olabilir.

Bunun yerine, çapraz hizmet bağımlılıklarını kaldırmak için yaygın olarak kabul edilen bir model, Şekil 5-4 ' de gösterilen [gerçekleştirilmiş görünüm](/azure/architecture/patterns/materialized-view)düzeninizdir.

![Gerçekleştirilmiş görünüm deseninin](./media/materialized-view-pattern.png)

**Şekil 5-4**. Gerçekleştirilmiş Görünüm Düzeni

Bu düzende, alışveriş sepeti hizmetine bir yerel veri tablosu ( *okuma modeli*olarak bilinir) yerleştirebilirsiniz. Bu tablo, ürün ve fiyatlandırma mikro hizmetlerinden gereken verilerin yoğun bir kopyasını içerir. Verileri doğrudan alışveriş sepeti mikro hizmetine kopyalamak, pahalı çapraz hizmet çağrıları gereksinimini ortadan kaldırır. Hizmetin yerel verileri ile hizmetin yanıt süresini ve güvenilirliğini artırırsınız. Ayrıca, kendi verilerinin kopyasına sahip olmak, alışveriş sepeti hizmetini daha dayanıklı hale getirir. Katalog hizmeti kullanılamaz hale gelirse, doğrudan alışveriş sepeti hizmetini etkilemez. Alışveriş sepeti, kendi mağazasındaki verilerle çalışmaya devam edebilir.

Bu yaklaşım ile catch, artık sisteminizde Yinelenen veriler olmasını sağlamak. Ancak, bulutta yerel sistemlerdeki verileri *genel* olarak çoğaltmak, yerleşik bir uygulamadır ve bir kenar yumuşatma veya kötü uygulama olarak kabul edilmez. Bir *ve yalnızca bir hizmetin* bir veri kümesine sahip olabileceğini ve bu hizmetin üzerinde yetki sahibi olabileceğini göz önünde bulundurun. Kayıt sistemi güncelleştirilirken okuma modellerini eşitlemeniz gerekir. Eşitleme genellikle Şekil 5,4 ' de gösterildiği gibi, bir [Yayımlama/abonelik düzeniyle](service-to-service-communication.md#events)zaman uyumsuz mesajlaşma yoluyla uygulanır.

## <a name="distributed-transactions"></a>Dağıtılmış işlemler

Mikro hizmetler genelinde verileri sorgularken çok sayıda mikro hizmette bir işlem uygulamak daha da karmaşıktır. Farklı mikro hizmetlerde bağımsız veri kaynakları arasında veri tutarlılığı sağlamanın devralınmış bir şekilde belirtilmedi. Bulutta yerel uygulamalarda dağıtılmış işlemlerin bulunmaması, dağıtılmış işlemleri programlı bir şekilde yönetmeniz anlamına gelir. *Anında tutarlılık* dünyasının *nihai tutarlılığa*kadar ilerinizden olursunuz.

Şekil 5-5 sorunu gösterir.

![Saga düzeninde işlem](./media/saga-transaction-operation.png)

**Şekil 5-5**. Mikro hizmetler genelinde işlem uygulama

Yukarıdaki şekilde, beş bağımsız mikro hizmet sipariş oluşturan dağıtılmış bir işleme katılır. Her mikro hizmet kendi veri mağazasını tutar ve kendi deposu için yerel bir işlem uygular. Siparişi oluşturmak için, *her* bir mikro hizmetin yerel işleminin başarılı olması veya *tümünün* iptal edilmesi ve işlemi geri toplaması gerekir. Mikro hizmetlerin her birinde yerleşik işlem desteği kullanılabilir olsa da, verilerin tutarlı tutulması için beş hizmetin tamamına yayılabilen dağıtılmış bir işlem desteklenmez.

Bunun yerine, bu dağıtılmış işlemi *programlı olarak*oluşturmanız gerekir.

Dağıtılmış işlem desteği eklemek için popüler bir düzende Saga deseninin olması önerilir. Yerel işlemler programlı bir şekilde gruplanarak ve her birini sırayla çağırarak uygulanır. Herhangi bir yerel işlem başarısız olursa, Saga işlemi iptal eder ve bir [dengeleyici](/azure/architecture/patterns/compensating-transaction)işlem kümesi çağırır. Telafi işlemleri, önceki yerel işlemler tarafından yapılan değişiklikleri geri alır ve veri tutarlılığını geri yükler. Şekil 5-6, Saga düzeniyle başarısız olan bir işlemi gösterir.

![Saga düzenine geri alma](./media/saga-rollback-operation.png)

**Şekil 5-6**. Bir işlem geri alınıyor

Önceki şekilde Inventory mikro hizmetinde *Envanter güncelleştirme* işlemi başarısız oldu. Saga, envanter sayılarını ayarlamak için bir dengeleyici işlem kümesi (kırmızı renkte) çağırır, ödemeyi ve siparişi iptal eder ve her bir mikro hizmet için verileri tutarlı bir duruma geri döndürür.

Saga desenleri genellikle bir dizi ilgili olay olarak veya bir ilgili komut kümesi olarak düzenlenir. Bölüm 4 ' te, genişletilmiş bir Saga uygulamasının temeli olacak hizmet toplayıcısı modelini tartıştık. Ayrıca, Azure Service Bus ve Azure Event Grid konuları ve bu da, choretik bir Saga uygulamasının bir temeli olacak konular ile de tartışıldık.

## <a name="high-volume-data"></a>Yüksek hacimli veriler

Büyük ölçekli bulutta yerel uygulamalar genellikle yüksek hacimli veri gereksinimlerini destekler. Bu senaryolarda geleneksel veri depolama teknikleri performans sorunlarına neden olabilir. Büyük ölçekte dağıtım yapan karmaşık sistemler için Komut ve Sorgu Sorumluluklarının Ayrılığı (CQRS) ve olay kaynağını belirleme uygulama performansını iyileştirebilir.  

### <a name="cqrs"></a>CQRS

[CQRS](/azure/architecture/patterns/cqrs), performansı, ölçeklenebilirliği ve güvenliği en üst düzeye çıkarmaya yardımcı olabilecek mimari bir modeldir. Model, verileri yazan işlemlerden verileri okuyan işlemleri ayırır.

Normal senaryolarda, hem okuma hem *de* yazma işlemleri için aynı varlık modeli ve veri deposu nesnesi kullanılır.

Ancak, yüksek hacimli bir veri senaryosu, okuma ve yazma işlemleri için ayrı modellerden ve veri tablolarından faydalanabilir. Performansı artırmak için okuma işlemi, pahalı yinelenen tablo birleştirmeleri ve tablo kilitlerinin önüne geçmek amacıyla verilerin yüksek oranda büyük bir gösterimine karşı sorgulayabilir. *Komut*olarak bilinen *yazma* işlemi, tutarlılığı güvence altına alan verilerin tamamen normalleştirilmiş bir gösterimine karşı güncelleştirilir. Daha sonra her iki gösterimi de eşitlenmiş halde tutmak için bir mekanizma uygulamanız gerekir. Genellikle, yazma tablosu değiştirildiğinde, değişikliği okuma tablosuna çoğaltan bir olay yayınlar.

Şekil 5-7, CQRS deseninin bir uygulamasını gösterir.

![Komut ve Sorgu Sorumluluklarının Ayrılığı](./media/cqrs-implementation.png)

**Şekil 5-7**. CQRS uygulama

Önceki şekilde, ayrı komut ve sorgu modelleri uygulanır. Her veri yazma işlemi, yazma deposuna kaydedilir ve sonra okuma deposuna yayılır. Veri yayma işleminin [nihai tutarlılık](https://www.cloudcomputingpatterns.org/eventual_consistency/)ilkesi üzerinde nasıl çalıştığı hakkında daha fazla dikkat edin. Okuma modeli, sonunda yazma modeliyle eşitlenir, ancak işlemde bazı gecikme olabilir. Sonraki bölümde nihai tutarlılığı tartıştık.

Bu ayrım, okuma ve yazma işlemlerini bağımsız olarak ölçeklendirmeye olanak sağlar. Okuma işlemleri sorgularda en iyi duruma getirilmiş şemayı kullanır, yazma işlemleri güncelleştirmeler için iyileştirilmiş bir şema kullanır. Okuma sorguları, yoğun verilere karşı, karmaşık iş mantığı ise yazma modeline uygulanabilirler. Ayrıca, yazma işlemlerinde, okumaların açığa çıkarmadan daha sıkı güvenlik sağlayabilirsiniz.

CQRS 'nin uygulanması, bulutta yerel hizmetler için uygulama performansını iyileştirebilir. Ancak, daha karmaşık bir tasarıma neden olur. Bu ilkeyi, buluttan faydalanabilecek bulut Yerel uygulamanızın bölümlerine dikkatle ve stratejik bir şekilde uygulayın. CQRS hakkında daha fazla bilgi için bkz. Microsoft Book [.net mikro hizmetleri: Kapsayıcılı .NET uygulamaları Için mimari](../microservices/microservice-ddd-cqrs-patterns/apply-simplified-microservice-cqrs-ddd-patterns.md).

### <a name="event-sourcing"></a>Olay kaynağını belirleme

Yüksek hacimli veri senaryolarını iyileştirmeye yönelik başka bir yaklaşım da [olay](/azure/architecture/patterns/event-sourcing)kaynağını içerir.

Bir sistem genellikle bir veri varlığının geçerli durumunu depolar. Kullanıcı telefon numarasını değiştirirse (örneğin, müşteri kaydı yeni sayıyla güncelleştirilir). Her zaman bir veri varlığının geçerli durumunu biliyoruz, ancak her güncelleştirme önceki durumun üzerine yazar.

Çoğu durumda bu model sorunsuz bir şekilde çalışmaktadır. Ancak, yüksek hacimli sistemlerde, işlemsel kilitleme ve sık sık güncelleştirme işlemlerinden gelen ek yük veritabanı performansını, yanıt hızını ve sınır ölçeklenebilirliğini etkileyebilir.

Olay kaynağını belirleme, verileri yakalamaya yönelik farklı bir yaklaşım alır. Verileri etkileyen her işlem, bir olay deposunda kalıcı hale getirilir. Bir veri kaydının durumunu güncelleştirmek yerine, her bir değişikliği geçmiş olayların sıralı listesine (muhasebecinin defterine benzer şekilde) ekler. Olay deposu, verilerin kayıt sistemi haline gelir. Bir mikro hizmetin sınırlanmış bağlamı içinde çeşitli gerçekleştirilmiş görünümler yaymak için kullanılır. Şekil 5,8, deseninin gösterildiği.

![Olay Kaynağını Belirleme](./media/event-sourcing.png)

**Şekil 5-8**. Olay Kaynağını Belirleme

Önceki şekilde, bir kullanıcının alışveriş sepeti için her girdinin (mavi), temel alınan bir olay deposuna nasıl eklendiği konusunda bir değer olduğunu aklınızda saklayın. Bitişik gerçekleştirilmiş görünümde, sistem, her bir alışveriş sepeti ile ilişkili tüm olayları yeniden kaydederek geçerli durumu projeler halinde gösterir. Bu görünüm veya okuma modeli, daha sonra Kullanıcı arabirimine geri sunulur. Olaylar ayrıca, dış sistemlerle ve uygulamalarla tümleştirilebilir veya bir varlığın geçerli durumunu tespit etmek üzere sorgulanamaz. Bu yaklaşımda geçmişi korursunuz. Bir varlığın yalnızca geçerli durumunu değil, Ayrıca bu duruma nasıl erişeceğimizi bilirsiniz.

Olayların kaynağını belirleme, olay kaynağını belirleme yazma modelini basitleştirir. Güncelleştirme veya silme yok. Her veri girişini değişmez bir olay olarak eklemek, çakışma, kilitleme ve ilişkisel veritabanlarıyla ilişkili eşzamanlılık çakışmalarını en aza indirir. Gerçekleştirilmiş görünüm düzeniyle okuma modellerinin oluşturulması, görünümü yazma modelinden ayırarak, uygulama kullanıcı arabirimi ihtiyaçlarını iyileştirmek için en iyi veri deposunu seçmenizi sağlar.

Bu model için doğrudan olay kaynağını destekleyen bir veri deposu düşünün. Azure Cosmos DB, MongoDB, Cassandra, Couşdb ve kvendb iyi adaylardır.

Tüm desenlerdeki ve teknolojilerde olduğu gibi, gerekli olduğunda stratejik bir şekilde uygulayın. Olay kaynağını artırmak daha yüksek performans ve ölçeklenebilirlik sağlayabiliyor olsa da karmaşıklık ve öğrenme eğrisinin masrafına gelir.

>[!div class="step-by-step"]
>[Önceki](service-mesh-communication-infrastructure.md) 
> [Sonraki](relational-vs-nosql-data.md)
