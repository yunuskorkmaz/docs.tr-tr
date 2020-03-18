---
title: Dağıtılmış veri yönetimi için sorunlar ve çözümler
description: Mikro hizmetler dünyasında dağıtılmış veri yönetimi için zorlukların ve çözümlerin neler olduğunu öğrenin.
ms.date: 09/20/2018
ms.openlocfilehash: c30de24591d5a73fd34087f34a69e9c7ed54cd35
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834451"
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Dağıtılmış veri yönetimi için sorunlar ve çözümler

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Meydan \#Okuma 1: Her microservice sınırlarını tanımlamak için nasıl

Mikro hizmet sınırlarını tanımlamak muhtemelen herkesin karşılaştığı ilk zorluktur. Her microservice uygulamanızın bir parçası olmalı ve her microservice tüm yararları ve getirdiği zorluklar ile özerk olmalıdır. Ama bu sınırları nasıl tanımlıyorsun?

İlk olarak, uygulamanın mantıksal etki alanı modellerine ve ilgili verilere odaklanmanız gerekir. Aynı uygulama içinde ayrılmış veri adalarını ve farklı bağlamları tanımlamaya çalışın. Her bağlamın farklı bir iş dili (farklı iş terimleri) olabilir. Bağlamlar tanımlanmalı ve bağımsız olarak yönetilmelidir. Bu farklı bağlamlarda kullanılan terimler ve varlıklar benzer görünebilir, ancak belirli bir bağlamda, bir iş kavramının başka bir bağlamda farklı bir amaç için kullanıldığını ve hatta farklı bir ada sahip olabileceğini keşfedebilirsiniz. Örneğin, bir kullanıcı kimlik veya üyelik bağlamında kullanıcı, CRM bağlamında bir müşteri, sipariş bağlamında alıcı olarak ve benzeri olarak adlandırılabilir.

Her bağlam için farklı bir etki alanına sahip birden çok uygulama bağlamı arasındaki sınırları tanımlama şekliniz, her iş mikro hizmetinin sınırlarını ve ilgili etki alanı modelini ve verilerini tam olarak nasıl tanımlayabileceğinizdir. Her zaman bu mikro hizmetler arasındaki bağlantı en aza indirmek için çalışırsınız. Bu kılavuz, daha sonra [her microservice için etki alanı modeli sınırlarını tanımlayan](identify-microservice-domain-model-boundaries.md) bölümünde bu tanımlama ve etki alanı modeli tasarımı hakkında daha fazla ayrıntıya gider.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Zorluk \#2: Çeşitli mikro hizmetlerden veri alan sorgular nasıl oluşturulur?

İkinci bir zorluk, uzak istemci uygulamalarından mikro hizmetlere geveze iletişimden kaçınırken, çeşitli mikro hizmetlerden veri alan sorguların nasıl uygulanacağıdır. Bir örnek, sepet, katalog ve kullanıcı kimliği mikro hizmetlerine ait kullanıcı bilgilerini göstermesi gereken bir mobil uygulamadan gelen tek bir ekran olabilir. Başka bir örnek, birden çok mikro hizmetlerde bulunan birçok tablonun yer aldığı karmaşık bir rapor olacaktır. Doğru çözüm sorguların karmaşıklığına bağlıdır. Ancak her halükarda, sisteminizin iletişiminde verimliliği artırmak istiyorsanız, bilgileri bir araya getirmek için bir yol gerekir. En popüler çözümler şunlardır.

**API Ağ Geçidi.** Farklı veritabanlarına sahip birden çok mikro hizmetten basit veri toplama için, önerilen yaklaşım api ağ geçidi olarak adlandırılan bir toplama microservice olduğunu. Ancak, sisteminizde bir boğma noktası olabilir ve mikro hizmet özerklik ilkesini ihlal edebilir, çünkü bu desen uygulama konusunda dikkatli olmak gerekir. Bu olasılığı azaltmak için, her biri sistemin dikey bir "dilim" veya iş alanına odaklanan birden çok para cezası kesilmiş API Ağ Geçidi'ne sahip olabilirsiniz. API Ağ Geçidi deseni daha sonra [API Ağ Geçidi bölümünde](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#why-consider-api-gateways-instead-of-direct-client-to-microservice-communication) daha ayrıntılı olarak açıklanır.

**Sorgu/okuma tabloları ile CQRS.** Birden çok mikro hizmetten veri toplama için başka bir çözüm [Materyalize Görünüm deseni.](https://docs.microsoft.com/azure/architecture/patterns/materialized-view) Bu yaklaşımda, önceden (gerçek sorgular gerçekleşmeden önce normalden arındırılmış verileri hazırlamak), birden çok mikro hizmete ait verileri içeren salt okunur bir tablo oluşturursunuz. Tablo, istemci uygulamasının gereksinimlerine uygun bir biçime sahiptir.

Bir mobil uygulama için ekran gibi bir şey düşünün. Tek bir veritabanınız varsa, birden çok tablo içeren karmaşık bir birleştirme gerçekleştiren bir SQL sorgusu kullanarak bu ekrana ait verileri bir araya getirebilirsiniz. Ancak, birden çok veritabanınız varsa ve her veritabanı farklı bir mikro hizmete sahipse, bu veritabanlarını sorgulayamaz ve bir SQL birleştirme oluşturamazsınız. Karmaşık sorgunuz bir meydan okuma haline gelir. Gereksinimi CQRS yaklaşımını kullanarak giderebilirsiniz—, sadece sorgular için kullanılan farklı bir veritabanında normalden arındırılmış bir tablo oluşturursunuz. Tablo, uygulamanızın ekranının gerektirdiği alanlar ile sorgu tablosundaki sütunlar arasında bire bir ilişki yle karmaşık sorgu için gereken veriler için özel olarak tasarlanabilir. Ayrıca raporlama amaçlı hizmet verebilir.

Bu yaklaşım yalnızca özgün sorunu (mikro hizmetler arasında sorgulama ve birleştirme) çözmekle birlikte, aynı zamanda karmaşık bir birleştirmeyle karşılaştırıldığında performansı önemli ölçüde artırır, çünkü uygulamanın sorgu tablosunda ihtiyaç duyduğu verilere zaten sahipsiniz. Tabii ki, sorgu/okuma tabloları ile Komut ve Sorgu Sorumluluk Ayrımı (CQRS) kullanarak ek geliştirme çalışması anlamına gelir ve nihai tutarlılık kucaklamak gerekir. Bununla birlikte, [işbirlikçi senaryolarda](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) performans ve yüksek ölçeklenebilirlik gereksinimleri (veya bakış açısına bağlı olarak rekabetçi senaryolar) birden çok veritabanı ile CQRS uygulamanız gereken yerlerdir.

**Merkezi veritabanlarında "soğuk veri".** Gerçek zamanlı veri gerektirmeyen karmaşık raporlar ve sorgular için, yaygın bir yaklaşım "sıcak verilerinizi" (mikro hizmetlerden gelen işlem verileri) yalnızca raporlama için kullanılan büyük veritabanlarına "soğuk veri" olarak aktarmaktır. Bu merkezi veritabanı sistemi Hadoop, Azure SQL Veri Ambarı'na dayalı bir veri ambarı gibi Büyük Veri tabanlı bir sistem veya yalnızca raporlar için kullanılan tek bir SQL veritabanı (boyut sorun olmayacaksa) olabilir.

Bu merkezi veritabanının yalnızca gerçek zamanlı veri gereksinimi olmayan sorgular ve raporlar için kullanılacağını unutmayın. Orijinal güncellemeler ve işlemler, doğruluk kaynağınız olarak, mikro hizmetler verilerinizde olmalıdır. Verileri eşitleme yolunuz, olay odaklı iletişimi (sonraki bölümlerde kapsanmış) veya diğer veritabanı altyapısı alma/dışa aktarma araçlarını kullanarak olacaktır. Olay odaklı iletişim kullanıyorsanız, bu tümleştirme işlemi, CQRS sorgu tabloları için daha önce açıklandığı gibi verileri yayma şeklinizle benzer.

Ancak, uygulama tasarımınız karmaşık sorgular için birden çok mikro hizmetten sürekli olarak bilgi toplamayı içeriyorsa, kötü bir tasarımın belirtisi olabilir -bir microservice diğer mikro hizmetlerden mümkün olduğunca izole edilmelidir. (Bu, her zaman soğuk veri merkezi veritabanları kullanması gereken raporları/analizleri hariç tutar.) Bu sorun genellikle mikro hizmetleri birleştirmek için bir neden olabilir. Evrimin özerkliğini ve her bir mikro hizmetin dağıtımını güçlü bağımlılıklar, uyum ve veri toplama ile dengelemeniz gerekir.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Zorluk \#3: Birden fazla mikro hizmette tutarlılık nasıl elde edir?

Daha önce de belirtildiği gibi, her microservice ait veriler bu microservice özel ve sadece kendi microservice API kullanılarak erişilebilir. Bu nedenle, sunulan bir sorun, birden çok mikro hizmet arasında tutarlılık tutarken uçtan uca iş süreçlerinin nasıl uygulanacağıdır.

Bu sorunu analiz etmek için, [eShopOnContainers başvuru uygulamasından](https://aka.ms/eshoponcontainers)bir örneğe bakalım. Catalog microservice, ürün fiyatı da dahil olmak üzere tüm ürünler hakkında bilgi tutar. Sepet mikro hizmeti, kullanıcıların alışveriş sepetlerine ekledikleri ürün öğeleriyle ilgili zamansal verileri yönetir ve bu veriler sepete eklendikleri sırada öğelerin fiyatını içerir. Bir ürünün fiyatı katalogda güncellendiğinde, bu fiyat aynı ürünü tutan etkin sepetlerde de güncelleştirilmelidir, ayrıca sistem kullanıcıyı, sepetlerine eklediklerinden beri belirli bir öğenin fiyatının değiştiğini söyleyerek uyarmalıdır.

Bu uygulamanın varsayımsal yekpare bir sürümünde, ürün tablosundaki fiyat değiştiğinde, katalog alt sistemi sepet tablosundaki geçerli fiyatı güncelleştirmek için bir ACID işlemini kullanabilir.

Ancak, mikro hizmetlere dayalı bir uygulamada, Ürün ve Sepet tabloları kendi microservices aittir. Hiçbir microservice, Şekil 4-9'da gösterildiği gibi, doğrudan sorgularda bile başka bir mikro hizmetin sahip olduğu tabloları/depolamayı kendi işlemlerinde içermemelidir.

![Mikro hizmetler veritabanı verilerinin paylaşılamayabileceğini gösteren diyagram.](./media/distributed-data-management/indepentent-microservice-databases.png)

**Şekil 4-9**. Bir microservice başka bir microservice bir tabloya doğrudan erişemez

Sepet tablosu Sepet microservice'e ait olduğundan, Katalog microservice sepet tablosunu doğrudan güncelleştirmemelidir. Sepet mikrohizmetinde bir güncelleştirme yapmak için, Katalog microservice büyük olasılıkla tümleştirme olayları (ileti ve olay tabanlı iletişim) gibi eşzamanlı iletişimi temel alan nihai tutarlılık kullanmalıdır. Bu nasıl [eShopOnContainers](https://aka.ms/eshoponcontainers) başvuru uygulaması mikro hizmetler arasında tutarlılık bu tür gerçekleştirir.

[CAP teoremi](https://en.wikipedia.org/wiki/CAP_theorem)tarafından belirtildiği gibi, kullanılabilirlik ve ACID güçlü tutarlılık arasında seçim yapmanız gerekir. Mikro hizmet tabanlı senaryoların çoğu, güçlü tutarlılık yerine kullanılabilirlik ve yüksek ölçeklenebilirlik ister. Görev açısından kritik uygulamalar çalışır durumda ve çalışmaya devam etmeli ve geliştiriciler zayıf veya nihai tutarlılıkla çalışma tekniklerini kullanarak güçlü tutarlılık etrafında çalışabilirler. Bu, çoğu mikro hizmet tabanlı mimarinin benimsediğü yaklaşımdır.

Ayrıca, ACID tarzı veya iki aşamalı işlemler sadece mikro hizmet ilkelerine aykırı değildir; çoğu NoSQL veritabanları (Azure Cosmos DB, MongoDB, vb.) dağıtılmış veritabanları senaryolarında tipik olan iki aşamalı işleme işlemlerini desteklemez. Ancak, hizmetler ve veritabanları arasında veri tutarlılığı korumak esastır. Bu zorluk aynı zamanda, belirli verilerin gereksiz olması gerektiğinde (örneğin, ürünün adının veya açıklamasının Katalog mikrohizmetinde ve Sepet'te olması gerektiğinde) birden çok mikro hizmet arasında değişikliklerin nasıl yayılılacağından da ilgilidir. mikro hizmet.

Bu sorun için iyi bir çözüm, olay odaklı iletişim ve yayımlama ve abone sistemi aracılığıyla ifade mikro hizmetler arasında nihai tutarlılık kullanmaktır. Bu konular daha sonra bu kılavuzda [Asynchronous event-driven communication](asynchronous-message-based-communication.md#asynchronous-event-driven-communication) bölümünde ele alınmıştır.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Zorluk \#4: Mikro hizmet sınırları arasında iletişim nasıl tasarlanabilir?

Mikro hizmet sınırları içinde iletişim kurmak gerçek bir zorluktur. Bu bağlamda, iletişim hangi protokolü kullanmanız gerektiğini (HTTP ve REST, AMQP, mesajlaşma vb.) ifade etmez. Bunun yerine, hangi iletişim stilini kullanmanız gerektiğini ve özellikle mikro hizmetlerinizin nasıl birleştiğinde olması gerektiğini ele alar. Bağlantı düzeyine bağlı olarak, hata oluştuğunda, bu hatanın sisteminiz üzerindeki etkisi önemli ölçüde değişir.

Mikro hizmetler tabanlı bir uygulama gibi dağıtılmış bir sistemde, bu kadar çok yapı nın hareket ettirilmesi ve birçok sunucu veya ana bilgisayar arasında dağıtılmış hizmetlerle birlikte bileşenler sonunda başarısız olur. Kısmi arıza ve daha büyük kesintiler meydana gelecektir, bu nedenle bu tür dağıtılmış sistemdeki ortak riskleri göz önünde bulundurarak mikro hizmetlerinizi ve aralarındaki iletişimi tasarlamanız gerekir.

Popüler bir yaklaşım http (REST) tabanlı mikrohizmetleri, basitlik nedeniyle uygulamaktır. HTTP tabanlı bir yaklaşım son derece kabul edilebilir; buradaki sorun, nasıl kullandığınızla ilgilidir. HTTP isteklerini ve yanıtlarını yalnızca istemci uygulamalarından veya API Ağ Geçitlerinden gelen mikro hizmetlerle etkileşim kurmak için kullanıyorsanız, sorun değil. Ancak, mikro hizmetler arasında uzun eşzamanlı HTTP çağrıları zincirleri oluşturursanız, mikro hizmetler yekpare bir uygulamada nesneler gibi kendi sınırları boyunca iletişim kurarsanız, uygulamanız sonunda sorunlarla karşılaşır.

Örneğin, istemci uygulamanızın Sipariş mikro hizmeti gibi tek bir mikro hizmete HTTP API çağrısı yaptığını düşünün. Sırayla Sipariş mikrohizmeti, aynı istek/yanıt döngüsü içinde HTTP'yi kullanarak ek mikro hizmetler çağırırsa, bir HTTP çağrıları zinciri oluşturursunuz. Başlangıçta mantıklı gelebilir. Ancak, bu yolda giderken göz önünde bulundurulması gereken önemli noktalar vardır:

- Engelleme ve düşük performans. HTTP'nin eşzamanlı doğası nedeniyle, tüm dahili HTTP çağrıları tamamlanana kadar orijinal istek yanıt almaz. Bu çağrıların sayısının önemli ölçüde arttığını ve aynı zamanda bir microservice ara HTTP çağrılarından birinin engellendiğini düşünün. Sonuç, performansın etkilendiği ve ek HTTP istekleri arttıkça genel ölçeklenebilirliğin katlanarak etkileneceğidir.

- HTTP ile mikro hizmetleri kaplin. İş mikro hizmetleri diğer iş mikro hizmetleri ile birleştirilmiş olmamalıdır. İdeal olarak, diğer mikro hizmetlerin varlığı hakkında "bilmemelidir". Uygulamanız örnekte olduğu gibi mikro hizmetleri bağlamaya dayanıyorsa, mikrohizmet başına özerklik elde etmek neredeyse imkansız olacaktır.

- Herhangi bir mikro serviste başarısızlık. HTTP çağrıları yla bağlantılı bir mikro hizmet zinciri uygularsanız, herhangi bir mikro hizmet başarısız olduğunda (ve sonunda başarısız olurlar) tüm mikro hizmetler zinciri başarısız olur. Mikro hizmet tabanlı bir sistem, kısmi arızalar sırasında mümkün olduğunca çalışmaya devam edecek şekilde tasarlanmalıdır. Üstel geri tepme veya devre kesici mekanizmaları ile yeniden denemeler iman etsebile, HTTP çağrı zincirleri ne kadar karmaşıksa, HTTP'ye dayalı bir hata stratejisi uygulamak o kadar karmaşıktır.

Aslında, dahili mikrohizmetleriniz açıklandığı gibi HTTP istekleri zincirleri oluşturarak iletişim kuruyorsa, işlem içi iletişim mekanizmaları yerine süreçler arasında http'ye dayalı, yekpare bir uygulamanız olduğu söylenebilir.

Bu nedenle, mikro hizmet özerkliğini uygulamak ve daha iyi esneklik sağlamak için, mikro hizmetler arasında istek/yanıt iletişimi zincirlerinin kullanımını en aza indirmeniz gerekir. Asynchronous ileti ve olay tabanlı iletişim kullanarak veya orijinal HTTP istek/yanıt döngüsünden bağımsız olarak (asynchronous) HTTP yoklamasını kullanarak, yalnızca mikroservisler arası iletişim için eşzamanlı etkileşim kullanmanız önerilir.

Asynchronous iletişim kullanımı daha sonra bu kılavuzda ek ayrıntılarla açıklanmıştır bölümlerde [Asynchronous microservice entegrasyonu microservice özerkliğini](communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy) ve [Asynchronous mesaj tabanlı iletişimi](asynchronous-message-based-communication.md)zorlar.

## <a name="additional-resources"></a>Ek kaynaklar

- **CAP teoremi** \
  <https://en.wikipedia.org/wiki/CAP_theorem>

- **Nihai tutarlılık** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Veri Tutarlılığı Astarı** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Martin Fowler' ı. CQRS (Komut ve Sorgu Sorumluluğu Ayrımı)** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Materyalize Görünüm** \
  <https://docs.microsoft.com/azure/architecture/patterns/materialized-view>

- **Charles Row' u. ACID vs. BASE: Veritabanı İşlem İşleminin DEĞIŞEN pH'ı** \
  <https://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/>

- **Telafi İşlemi** \
  <https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction>

- **Udi Dahan. Hizmet Odaklı Kompozisyon** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

>[!div class="step-by-step"]
>[Önceki](logical-versus-physical-architecture.md)
>[Sonraki](identify-microservice-domain-model-boundaries.md)
