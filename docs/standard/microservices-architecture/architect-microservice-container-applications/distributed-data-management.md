---
title: Dağıtılmış veri yönetimi için sorunlar ve çözümler
description: Talepler ve mikro hizmetler dünyasında Dağıtılmış veri yönetimi çözümleri ne olduğunu öğrenin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: 3e683044ea6a31116f1e7da6d690fc32ad87bd76
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909694"
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Dağıtılmış veri yönetimi için sorunlar ve çözümler

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Sınama \#1: Her mikro hizmet sınırlarını tanımlama

Mikro hizmet sınırlarını tanımlama herkes karşılaştığında ilk testten olabilir. Her mikro hizmet, uygulamanızın bir parçası olması gerekir ve her bir mikro hizmetin tüm avantajları ve onu ilettiği zorlukları ile otonom olmalıdır. Ancak, bu sınırları nasıl saptadınız mı?

İlk olarak, uygulamanın mantıksal etki alanı modelleri ve ilgili verileri gerekir. Veri ve aynı uygulama içinde farklı bağlamlardaki ayrılmış Adaları belirlemeye çalışın. Her bağlamı, farklı iş dili (farklı iş terimlerini) olabilir. Bağlamları tanımlanabilir ve bağımsız olarak yönetilebilir. Hüküm ve bu farklı bağlamlardaki kullanılabilir varlıklar benzer görünebilir, ancak başka bir bağlamda farklı bir amaç için bir iş kavramını belirli bir bağlamda kullanılan keşfedin ve hatta farklı bir ad olabilir. Örneğin, bir kullanıcının kullanıcı kimliği veya üyelik bağlamı olarak olarak CRM bağlamda, bir müşteri bir sipariş bağlamında bir alıcı olarak adlandırılabilir ve VS.

Her bağlamı tam olarak her iş mikro hizmet ve onun ilişkili için sınırları nasıl tanımlamak için farklı bir etki alanı ile birden çok uygulama içerikleri arasındaki sınırları tanımlamak şekilde etki alanı modeli ve veri. Her zaman bu mikro hizmetler arasında eşleştirmeye en aza indirmek çalışır. Bu kılavuzda bu bölümdeki tanımlama ve etki alanı modeli tasarımı hakkında daha fazla ayrıntıya gider [her mikro hizmet için etki alanı modeli sınırlarını tanımlama](identify-microservice-domain-model-boundaries.md) daha sonra.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Sınama \#2: Birden fazla mikro hizmetler veri alan sorguları oluşturma

İkinci sık iletişim için mikro Hizmetleri kaçınarak uzak istemci uygulamalardan birden fazla mikro hizmetler, veri alan sorguları uygulanması zordur. Sepet, katalog ve kullanıcı kimlik mikro hizmetin ait kullanıcı bilgilerini göstermek için gereken bir mobil uygulama tek bir ekrandan bir örnek olabilir. Başka bir örnek, birden fazla mikro Hizmetleri bulunan birçok tabloları içeren karmaşık bir rapor olabilir. Doğru çözüm, sorgu karmaşıklığına bağlıdır. Ancak her durumda, iletişimin sistemin verimliliğini artırmak istiyorsanız toplam bilgileri için bir yol gerekir. En popüler çözümler aşağıda verilmiştir.

**API ağ geçidi.** Farklı veritabanlarına ait birden fazla mikro hizmetin gelen Basit veri toplama için önerilen yaklaşım bir API ağ geçidi başvurulan bir toplama mikro hizmetidir. Ancak, sisteminizdeki bir sıkıştırma noktası olabilir ve mikro hizmet bağımsız çalışma sınırı ilkesini ihlal edebilir çünkü bu düzen uygulama hakkında dikkatli olmanız gerekir. Bu olasılığını azaltmak için her bir dikey "dilim" ya da sistemin iş alanı odaklanarak birden çok fined şirketlerinde API ağ geçitleri olabilir. API ağ geçidi desenini daha ayrıntılı olarak açıklanan [API ağ geçidi bölüm](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#why-consider-api-gateways-instead-of-direct-client-to-microservice-communication) daha sonra.

**CQRS sorgu/okuma tablolarla.** Birden fazla mikro hizmetin veri toplama için başka bir çözüm [gerçekleştirilmiş görünüm düzeni](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). Bu yaklaşımda, önceden oluşturduğunuz (hazırlama normalleştirilmişlikten çıkarılmış veriler gerçek sorguları meydana gelmeden), birden fazla mikro hizmetin ait verilerle bir salt okunur tablo. Tablo, istemci uygulamanın ihtiyaçlarına uygun bir biçimde.

Mobil uygulama ekran gibi göz önünde bulundurun. Tek bir veritabanı varsa, verileri birden çok tablo karmaşık birleşim gerçekleştiren bir SQL sorgusu kullanarak bu ekran için birlikte çekeceği. Ancak, birden çok veritabanına sahip ve her veritabanı farklı bir mikro hizmet tarafından sahip olunan, bu veritabanlarını sorgulama ve SQL birleştirme oluşturma olamaz. Bir challenge, karmaşık bir sorgu olur. CQRS yaklaşımı kullanarak bir gereksinimi ele almanız — normalleştirilmişlikten çıkarılmış bir tablo sorguları için kullanılan farklı bir veritabanı oluşturun. Tablo, özellikle uygulamanızın ekran ve sorgu tablodaki sütunlar için gerekli alanlar arasında bire bir ilişki ile karmaşık bir sorgu için ihtiyacınız olan verileri için tasarlanmış olması. Ayrıca raporlama amacıyla hizmet.

Bu yaklaşım yalnızca özgün (sorgu ve birleştirme mikro hizmetler arasında nasıl) sorunu çözer, ancak zaten sahip olduğunuz sorgu tabloda uygulamanız için gereken veriler için Ayrıca önemli ölçüde karmaşık bir birleşim ile karşılaştırıldığında performansı iyileştirir. Elbette, komut ve sorgu sorumluluğu ayrımı (CQRS) içeren sorgu/okuma tablolar'ı kullanarak ek geliştirme iş anlamına gelir ve nihai tutarlılık yaklaşımını benimseyin gerekecektir. Öte yandan, performans ve yüksek ölçeklenebilirlik gereksinimlerine [işbirliği senaryoları](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) (veya bağlı açısından rekabetçi senaryoları) olan birden çok veritabanıyla CQRS burada uygulamalıdır.

**"Soğuk verileri" merkezi veritabanları.** Karmaşık raporlar ve gerçek zamanlı veri gerektirmeyebilecek sorgular için "veri"Sık erişimli dışarı aktarmak için yaygın bir yaklaşım olan (mikro hizmetler işlemsel verileri) olarak "soğuk veri" yalnızca raporlama için kullanılan büyük veritabanları. Merkezi bir veritabanı sistemi Hadoop, bir Azure SQL veri ambarı veya (boyutta bir sorun olmayacaktır değilse), raporlar için kullanılan bile tek bir SQL veritabanı gibi bir veri ambarı gibi büyük veri tabanlı bir sistem emin olabilir.

Bu merkezi bir veritabanında yalnızca sorgular ve gerçek zamanlı veri gerekmeyen raporlar için kullanılacak aklınızda bulundurun. Özgün güncelleştirmeleri ve işlemleri, kaynağınız getirilir, mikro hizmetler verilerinizi olmanız gerekir. Olay temelli iletişim (sonraki bölümde ele) kullanarak ya da diğer veritabanı altyapısı içeri/dışarı aktarma araçları kullanarak verileri eşitlemek şekilde olacaktır. Olay temelli iletişim kullanırsanız, bu tümleştirme işlemi benzer şekilde CQRS sorgu tablolar için daha önce açıklandığı gibi veri yaymak olacaktır.

Ancak, uygulama tasarımınızı sürekli karmaşık sorgular için birden fazla mikro hizmetin bilgileri toplayarak içeriyorsa, bir hatalı tasarım - bir mikro hizmet belirtisi olarak yalıtılmış olarak diğer mikro hizmetler mümkün olabilir. (Her zaman soğuk veri merkezi veritabanlarını kullanması gereken raporları/analizleri dışlar.) Bu sorun genellikle mikro hizmetler birleştirmek için bir neden olabilir. Gelişimi, özerkliği ve güçlü bağımlılıkları uyumda ve veri toplama ile her bir mikro Hizmet dağıtımının dengelemeniz gerekir.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Sınama \#3: Birden çok mikro hizmetler arasında tutarlılığı elde etme

Daha önce belirtildiği gibi her bir mikro hizmet tarafından sahip olunan veri, mikro hizmet için özeldir ve yalnızca kendi mikro hizmet API'si kullanılarak erişilebilir. Bu nedenle, sunulan birden fazla mikro hizmetler arasında tutarlılık sağlarken uçtan uca iş süreçlerini uygulanması zordur.

Bu sorunu çözümlemek için bir örnekten göz atalım [hizmetine başvuru uygulaması](https://aka.ms/eshoponcontainers). Katalog mikro hizmet ürün fiyatı da dahil olmak üzere tüm ürünlerle ilgili bilgileri tutar. Sepet mikro hizmet sepete eklendikleri zaman öğeleri fiyatını içeren zamana bağlı veri kullanıcılar için Alışveriş sepetleri, eklemekte olduğunuz ürün öğeleri hakkında yönetir. Bir ürünün fiyatını katalogda güncelleştirildiğinde, bu fiyat, aynı ürün tutan etkin sepetleri güncelleştirilmelidir yanı sıra sistem büyük olasılıkla bunu sepetine eklendi beri belirli bir öğenin fiyat değiştiğini belirten kullanıcı bildirmelisiniz.

Fiyat Ürünler tablosuna değiştiğinde bir kuramsal tek parça sürümünde bu uygulama Kataloğu alt yalnızca bir ACID işlemi sepet tablodaki geçerli fiyatı güncelleştirmek için kullanabilirsiniz.

Ancak, bir mikro hizmet tabanlı uygulama ürün ve sepet tabloları ilgili kendi mikro hizmetin sahibi olur. Şekil 4-9'da gösterildiği gibi hiçbir mikro hizmet tablolar/doğrudan sorgu içinde bile kendi işlemleri içinde başka bir mikro hizmet tarafından sahip olunan depolama hiç olmadığı kadar içermelidir.

![Bir mikro hizmet, bir tablodaki başka bir mikro hizmet doğrudan erişemez, nihai tutarlılık, verileri eşitlemek için kullanılmalıdır.](./media/image9.png)

**Şekil 4-9**. Bir mikro hizmet, bir tablodaki başka bir mikro hizmet doğrudan erişemez

Sepet tablo sepet mikro hizmet tarafından sahiplenildiğinden Kataloğu mikro hizmet sepet tablo doğrudan güncelleştirme olmamalıdır. Katalog mikro hizmet sepet mikro hizmet için bir güncelleştirme yapmak için büyük olasılıkla zaman uyumsuz iletişim tümleştirme olayları (ileti ve olay tabanlı iletişim) gibi temel nihai tutarlılık kullanmanız gerekir. Bu, nasıl [hizmetine](https://aka.ms/eshoponcontainers) başvuru uygulaması, mikro hizmetler arasında tutarlılık bu tür gerçekleştirir.

Tarafından belirtildiği gibi [CAP Teoremi](https://en.wikipedia.org/wiki/CAP_theorem), ACID güçlü tutarlılık ve kullanılabilirlik arasında seçim yapmanız gerekir. Mikro hizmet tabanlı çoğu senaryoda, kullanılabilirlik ve güçlü tutarlılık aksine yüksek ölçeklenebilirlik talep. Görev açısından kritik uygulamalar kalması gereken ve çalışan ve geliştiricilerin güçlü tutarlılık zayıf veya nihai tutarlılık ile çalışmaya yönelik teknikleri kullanarak çalışabilir. Çoğu mikro hizmet tabanlı mimari tarafından uygulanan yaklaşıma budur.

Ayrıca, ACID stili veya iki aşamalı tamamlama işlemleri yalnızca mikro hizmetler ilkelerine karşı değildir; Çoğu NoSQL veritabanları (örneğin, Azure Cosmos DB, MongoDB, vb.) iki aşamalı tamamlama işlem, dağıtılmış veritabanları senaryolarında desteklemez. Ancak, veri koruma hizmetleri ve veritabanları arasında tutarlılığı gereklidir. Bu zorluğu da yedekli olacak şekilde bazı verilere ihtiyaç duyduğunda, birden fazla mikro hizmetler arasında değişiklikleri yaymak nasıl soruyu ilgili — Örneğin, ne zaman ürün adına veya açıklamasına Kataloğu mikro hizmet ve sepet olması gerekir mikro hizmet.

Bu sorun için iyi bir çözümdür, olay tabanlı iletişim ve bir Yayımla ve abone ol sistemi geliştirilmiştir mikro hizmetler arasındaki son tutarlılık kullanmaktır. Bu konulara bölümünde ele alınmıştır [zaman uyumsuz olay temelli iletişim](asynchronous-message-based-communication.md#asynchronous-event-driven-communication) bu kılavuzun sonraki.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Sınama \#4: Mikro hizmet sınırları arasında iletişimi tasarlamak nasıl

Mikro hizmet arasında iletişim kuran sınırları gerçek zor olur. Bu bağlamda iletişimi için başvurmadığından, protokol (HTTP ve REST, AMQP, Mesajlaşma vb.) kullanmanız gerekir. Bunun yerine, kullanmanız gereken hangi iletişim stili ve özellikle bu nasıl bağlı mikro hizmetlerin olmalıdır yöneliktir. Hata oluştuğunda bağlantısından düzeyine bağlı olarak, bu hata, sistem üzerindeki etkisini önemli ölçüde farklılık gösterir.

Bir mikro hizmet tabanlı uygulama, çok sayıda yapıtları gezinmek ve birçok sunucuları veya konaklar arasında dağıtılmış hizmetlerle gibi dağıtılmış bir sistemde bileşenleri sonunda başarısız olur. Böylece bunlar Dağıtılmış Sistem bu tür genel risk dikkate üzerinde mikro hizmetlerin ve iletişim tasarım gerek kısmi hata ve daha da büyük kesintiler oluşacaktır.

HTTP REST tabanlı mikro hizmetler, kendi kolaylık olması nedeniyle uygulamak yaygın bir yaklaşımdır. HTTP tabanlı yaklaşım edilebilir, sorun burada kullandığınız nasıl ilişkilidir. Yalnızca istemci uygulamaları veya API ağ geçitleri, mikro hizmetler ile etkileşim kurmak için HTTP isteklerini ve yanıtlarını kullanırsanız, uygundur. Ancak mikro hizmetler arasında zaman uyumlu HTTP çağrıları için uzun zincirleri oluşturursanız, mikro hizmetler tek parça bir uygulamayı nesneleri değilmiş gibi kendi sınırları arasında iletişim kurma, uygulamanızın sonunda sorunlarla karşılaşırsanız çalışır.

Örneğin, istemci uygulamanız sıralama mikro hizmet gibi tek bir mikro hizmet için bir HTTP API çağrısı yapar düşünün. Sıralama mikro hizmet sırayla ek çağırırsa döngüsü içinde aynı istek/yanıt HTTP kullanarak mikro hizmetler, HTTP çağrıları zinciri oluşturmakta olduğunuz. Başlangıçta makul görünebilir. Ancak, bu yolunda giderken dikkat edilmesi gereken önemli noktalar vardır:

- Engelleme ve düşük performans. HTTP zaman uyumlu yapısı nedeniyle, tüm iç HTTP çağrıları tamamlanana kadar özgün istek yanıt elde edemez. Bu çağrı sayısı önemli ölçüde artırır ve aynı zamanda bir mikro hizmet için bir ara HTTP çağrıları engellenir hayal edin. Performansı etkilenir ve genel ölçeklenebilirlik katlanarak ek HTTP istekleri artış etkilenecek sonucudur.

- HTTP ile eşleştirmeye mikro hizmetler. İş mikro hizmetler ile diğer iş mikro hizmetler sıkı bağlı olmaması gerekir. İdeal olarak, "diğer mikro hizmetler hakkında varlığını alışık oldukları olmaması gerekir". Uygulamanız mikro hizmetler örnekte olduğu gibi eşlenmesiyle dayanıyorsa, mikro hizmet başına otonomi elde neredeyse imkansız olur.

- Herhangi bir mikro hizmet hatası. Herhangi bir mikro hizmet başarısız olursa (ve sonunda başarısız olur olduğunda) ve tüm zincir mikro HTTP çağrıları ile bağlantılı bir mikro hizmet zinciri uygulanması durumunda başarısız olur. Mikro hizmet tabanlı bir sistem yanı sıra mümkün kısmi hataları sırasında çalışmaya devam etmek için tasarlanmış olmalıdır. Yeniden deneme üstel geri alma ya da devre kesicinin mekanizmaları kullanan istemci mantığı uygulamasına olsa bile, daha fazla karmaşık HTTP çağrısı zincirleri olan HTTP tabanlı bir hata stratejilerini uygulamasına olanak olduğunu daha karmaşık.

İç, mikro hizmetler, HTTP isteklerini zincirleri açıklandığı oluşturarak kurarken aslında, işlem içi iletişim mekanizmaları yerine işlemleri arasındaki HTTP tabanlı ancak tek parça bir uygulamayı sahip tartışılabilir.

Bu nedenle, mikro hizmet otonomi zorlamak ve daha iyi bir dayanıklılık olması için istek/yanıt iletişim zincirleri kullanımını mikro hizmetler arasında en aza indirmeniz gerekir. Yalnızca zaman uyumsuz etkileşim inter-mikro hizmet iletişim için zaman uyumsuz ileti ve olay-tabanlı iletişim veya özgün HTTP isteği bağımsız olarak (zaman uyumsuz) HTTP yoklama kullanarak kullanmanızı tavsiye edilir / yanıt döngüsü.

Zaman uyumsuz iletişim kullanımı ile ek ayrıntılar sonraki bölümlerde bu kılavuzda açıklanan [zaman uyumsuz bir mikro hizmet tümleştirmesi zorlar mikro hizmet'ın bağımsız çalışma sınırı](communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy) ve [zaman uyumsuz ileti tabanlı iletişim](asynchronous-message-based-communication.md).

## <a name="additional-resources"></a>Ek kaynaklar

- **CAP Teoremi** \
  <https://en.wikipedia.org/wiki/CAP_theorem>

- **Son tutarlılık** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Veri tutarlılığı temel bilgileri** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Martin Fowler. CQRS (komut ve sorgu sorumluluğu ayrımı)** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Gerçekleştirilmiş Görünüm** \
  <https://docs.microsoft.com/azure/architecture/patterns/materialized-view>

- **Charles satır. ACID vs. TEMEL: Veritabanı işlem işleme Shifting pH** \
  <https://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/>

- **Telafi işlemi** \
  <https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction>

- **UDI Dahan. Hizmet yönelimli oluşturma** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

>[!div class="step-by-step"]
>[Önceki](logical-versus-physical-architecture.md)
>[İleri](identify-microservice-domain-model-boundaries.md)
