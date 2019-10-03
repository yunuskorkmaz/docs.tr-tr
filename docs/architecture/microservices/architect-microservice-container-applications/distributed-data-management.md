---
title: Dağıtılmış veri yönetimi ile ilgili sorunlar ve çözümler
description: Mikro hizmetler dünyasında dağıtılmış veri yönetimiyle ilgili zorluk ve çözümlerin ne olduğunu öğrenin.
ms.date: 09/20/2018
ms.openlocfilehash: c30de24591d5a73fd34087f34a69e9c7ed54cd35
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834451"
---
# <a name="challenges-and-solutions-for-distributed-data-management"></a>Dağıtılmış veri yönetimi ile ilgili sorunlar ve çözümler

## <a name="challenge-1-how-to-define-the-boundaries-of-each-microservice"></a>Sınama \#1: her mikro hizmetin sınırlarını tanımlama

Mikro hizmet sınırlarının tanımlanması büyük olasılıkla herkesin karşılaştığı ilk güçlük dır. Her mikro hizmet uygulamanızın bir parçası olmalıdır ve bu her mikro hizmet, ilettiği tüm avantajlarla ve güçlüklerle birlikte otonom olmalıdır. Ancak bu sınırları nasıl tanımlayabilirim?

İlk olarak, uygulamanın mantıksal etki alanı modellerine ve ilgili verilere odaklanmanız gerekir. Aynı uygulamadaki ayrılmış Adaları ve farklı bağlamlarını ayırt etmek için deneyin. Her bağlamın farklı bir iş dili (farklı iş koşulları) olabilir. Bağlamlar bağımsız olarak tanımlanmalıdır ve yönetilmelidir. Bu farklı bağlamlarda kullanılan hüküm ve varlıklar benzer olabilir, ancak belirli bir bağlamda, bir iş kavramının başka bir bağlamda farklı bir amaçla kullanıldığını ve hatta farklı bir ada sahip olabileceğini de fark edebilirsiniz. Örneğin, bir kullanıcı kimlik veya üyelik bağlamında bir kullanıcı olarak, CRM bağlamındaki bir müşteri olarak, bir sıralama Bağlamında alıcı olarak veya benzeri bir kullanıcı olarak adlandırılabilir.

Her bağlam için farklı bir etki alanı ile birden çok uygulama bağlamı arasındaki sınırları nasıl tanımlayabilmeniz, her bir iş mikro hizmeti ve ilgili etki alanı modeli ve verileri için sınırları nasıl tanımlayabilmeniz gerekir. Bu mikro hizmetler arasındaki kuponu en aza indirmenize her zaman çalışılır. Bu kılavuz, bu kimlik ve etki alanı modeli tasarımı hakkında daha ayrıntılı bilgi, [her mikro hizmet için etki alanı modeli sınırlarını tanımlama](identify-microservice-domain-model-boundaries.md) bölümünde daha fazla ayrıntıya gider.

## <a name="challenge-2-how-to-create-queries-that-retrieve-data-from-several-microservices"></a>Sınama \#2: çeşitli mikro hizmetlerden veri alan sorgular oluşturma

İkinci bir sınama, birkaç mikro hizmetten veri alan sorguların nasıl uygulanacağı, uzak istemci uygulamalarından gelen mikro hizmetlerle geveze iletişiminden kaçınmaya yönelik bir sınamadır. Bir örnek, bir mobil uygulamadan, sepet, Katalog ve Kullanıcı kimliği mikro hizmetleri tarafından sahip olunan Kullanıcı bilgilerini göstermesi gereken tek bir ekran olabilir. Birden fazla mikro hizmette bulunan çok sayıda tabloyu içeren bir karmaşık rapor olabilir. Doğru çözüm, sorguların karmaşıklığına bağlıdır. Ancak, sistem iletişiminizdeki verimliliği artırmak isterseniz bilgileri toplamanın bir yolu olması gerekir. En popüler çözümler şunlardır.

**API ağ geçidi.** Farklı veritabanlarına sahip birden fazla mikro hizmetten basit veri toplama için önerilen yaklaşım, API ağ geçidi olarak adlandırılan bir toplama mikro hizmetidir. Ancak, bu düzenin uygulanması konusunda dikkatli olmanız gerekir, çünkü sisteminizde bir sıkıştırma noktası olabilir ve mikro hizmet bağımsız çalışma sınırı ilkesini ihlal edebilir. Bu olasılığa karşı azaltmak için, her birinin dikey bir "dilim" veya sistemin iş alanına odaklanarak birden çok fined API ağ geçidine sahip olabilirsiniz. API ağ geçidi, daha sonra [API ağ geçidi bölümünde](direct-client-to-microservice-communication-versus-the-api-gateway-pattern.md#why-consider-api-gateways-instead-of-direct-client-to-microservice-communication) daha ayrıntılı olarak açıklanmıştır.

**Sorgu/okuma tabloları olan CQRS.** Birden çok mikro hizmetten veri toplamak için başka bir çözüm, [gerçekleştirilmiş görünüm](https://docs.microsoft.com/azure/architecture/patterns/materialized-view)modelidir. Bu yaklaşımda, birden fazla mikro hizmet tarafından sahip olunan verilerin bulunduğu salt okunurdur bir tablo olan, önceden (gerçek sorgular gerçekleşmeden önce diğer verileri hazırlama) oluşturursunuz. Tablonun, istemci uygulamanın ihtiyaçlarına uygun bir biçimi vardır.

Mobil uygulama için ekran gibi bir şey düşünün. Tek bir veritabanınız varsa, birden çok tablo içeren karmaşık bir birleştirmeyi gerçekleştiren SQL sorgusunu kullanarak bu ekran için verileri birlikte çekebilirsiniz. Ancak, birden çok veritabanınız varsa ve her bir veritabanı farklı bir mikro hizmete aitse, bu veritabanlarını sorgulayabilir ve bir SQL birleşimi oluşturamazsınız. Karmaşık sorgunuz bir zorluk haline gelir. CQRS yaklaşımını kullanarak gereksinime bir şekilde erişebilirsiniz. yalnızca sorgular için kullanılan farklı bir veritabanında, yoğun bir tablo oluşturursunuz. Tablo, uygulamanızın ekranı ve sorgu tablosundaki sütunlar arasındaki alanlar arasında bire bir ilişki ile karmaşık sorgu için gereken veriler için özel olarak tasarlanabilir. Raporlama amaçları için de hizmet verebilir.

Bu yaklaşım yalnızca özgün sorunu çözmez (mikro hizmetlere sorgulama ve ayrılma), ancak uygulamanın sorgu tablosunda ihtiyaç duyacağı verilere zaten sahip olduğunuz için karmaşık bir JOIN ile karşılaştırıldığında performansı önemli ölçüde artırır. Tabii ki, sorgu/okuma tabloları ile Komut ve Sorgu Sorumluluklarının Ayrılığı (CQRS) kullanmak ek geliştirme işi anlamına gelir ve nihai tutarlılığı fazla ayraç içine almanız gerekir. Nonetheless, [işbirliği senaryolarında](http://udidahan.com/2011/10/02/why-you-should-be-using-cqrs-almost-everywhere/) performans ve yüksek ölçeklenebilirlik gereksinimleri (veya görünümün noktasına bağlı olarak rekabet senaryolarında), birden çok veritabanı ile CQRS uygulamanız gereken yerdir.

**Merkezi veritabanlarındaki "soğuk veriler".** Gerçek zamanlı veriler gerektirmeyen karmaşık raporlar ve sorgular için, "sık erişimli verileri" (mikro hizmetlerdeki işlem verileri), yalnızca raporlama için kullanılan büyük veritabanlarına "soğuk veriler" olarak dışarı aktarmalıdır. Bu merkezi veritabanı sistemi Hadoop gibi büyük bir veri tabanlı sistem olabilir, Azure SQL veri ambarı 'nı temel alan bir veri ambarı veya hatta yalnızca raporlar için kullanılan tek bir SQL veritabanı (boyut bir sorun değilse).

Bu merkezi veritabanının yalnızca gerçek zamanlı veriler gerektirmeyen sorgular ve raporlar için kullanıldığını göz önünde bulundurun. Asıl kaynak olarak özgün güncelleştirmeler ve işlemler, mikro hizmet verilerinizde olması gerekir. Verileri eşitlemenize olanak, olay odaklı iletişim (sonraki bölümlerde ele alınmıştır) veya diğer veritabanı altyapısı içeri/dışarı aktarma araçları kullanılarak yapılır. Olay odaklı iletişim kullanıyorsanız, bu tümleştirme süreci, verileri daha önce CQRS sorgu tablolarında açıklandığı gibi yaymanız ile benzerdir.

Ancak, uygulama tasarımınız karmaşık sorgular için birden fazla mikro hizmetten sürekli bilgi toplamak içeriyorsa, kötü bir tasarımın belirtisi olabilir. mikro hizmet, diğer mikro hizmetlerden mümkün olduğunca yalıtılmış olmalıdır. (Bu, her zaman soğuk veri merkezi veritabanlarını kullanması gereken raporları/Analizi dışlar.) Bu sorunun olması, mikro hizmetleri birleştirmenin bir nedeni olabilir. Güçlü bağımlılıklar, cohezme ve veri toplama ile her bir mikro hizmetin dağıtımı ve dağıtım bağımsız çalışma sınırı dengelenmesi gerekir.

## <a name="challenge-3-how-to-achieve-consistency-across-multiple-microservices"></a>Sınama \#3: birden fazla mikro hizmet arasında tutarlılık elde etme

Daha önce belirtildiği gibi, her mikro hizmetin sahip olduğu veriler bu mikro hizmet için özeldir ve yalnızca mikro hizmet API 'SI kullanılarak erişilebilir. Bu nedenle, sunulan bir zorluk, birden fazla mikro hizmette tutarlılık sağlarken uçtan uca iş süreçlerini uygulama.

Bu sorunu çözmek için [Eshoponcontainers başvuru uygulamasından](https://aka.ms/eshoponcontainers)bir örneğe bakalım. Katalog mikro hizmeti, ürün fiyatı dahil olmak üzere tüm ürünlerle ilgili bilgileri tutar. Sepet mikro hizmeti, kullanıcıların kendi alışveriş sepetlerine eklediği ürün öğeleriyle ilgili zamana bağlı verileri yönetir ve bu da öğelerin sepete eklendikleri sırada dahil edilen fiyatını içerir. Bir ürünün fiyatı katalogda güncelleştirildiği zaman, bu fiyat aynı ürüne sahip olan etkin sepetlerinde de güncelleştirilmeleri gerekir ve ayrıca sistem büyük olasılıkla kullanıcıyı, belirli bir öğenin fiyatının sepetlerine ekledikleri tarihten sonra değiştiğini söyleyen şekilde uyarmalıdır.

Bu uygulamanın kuramsal tek parçalı bir sürümünde, Ürünler tablosundaki fiyat değiştiğinde, katalog alt sistemi yalnızca bir ACID işlemi kullanarak sepet tablosundaki geçerli fiyatı güncelleştirebilir.

Ancak, mikro hizmet tabanlı bir uygulamada, ürün ve sepet tabloları ilgili mikro hizmetlere aittir. Bir mikro hizmet, Şekil 4-9 ' de gösterildiği gibi, başka bir mikro hizmetin kendisine ait olan ve doğrudan sorgularda bile kendi işlemlerinde sahip olan tabloları/depolamayı içermemelidir.

![Mikro Hizmetler veritabanı verilerinin paylaşılacağını gösteren diyagram.](./media/distributed-data-management/indepentent-microservice-databases.png)

**Şekil 4-9**. Mikro hizmet, başka bir mikro hizmette bulunan bir tabloya doğrudan erişemez

Sepet tablosu sepet mikro hizmetine ait olduğundan, Katalog mikro hizmeti sepet tablosunu doğrudan güncelleştirmemelidir. Sepet mikro hizmetinde bir güncelleştirme yapmak için, Katalog mikro hizmeti, tümleştirme olayları (ileti ve olay tabanlı iletişim) gibi zaman uyumsuz iletişime göre muhtemelen nihai tutarlılık kullanmalıdır. Bu, [Eshoponcontainers](https://aka.ms/eshoponcontainers) başvuru uygulamasının mikro hizmetlerde bu tür tutarlılığı gerçekleştirmektir.

[Cap](https://en.wikipedia.org/wiki/CAP_theorem)'ler tarafından belirtildiği gibi, kullanılabilirlik ve ACID güçlü tutarlılığı arasında seçim yapmanız gerekir. Çoğu mikro hizmet tabanlı senaryo, güçlü tutarlılığa karşı, talep kullanılabilirliği ve yüksek ölçeklenebilirlik sağlar. Görev açısından kritik uygulamalar çalışır durumda kalmalıdır ve geliştiriciler, zayıf veya nihai tutarlılık ile çalışma tekniklerini kullanarak güçlü tutarlılığı geçici olarak çözebilirler. Bu, mikro hizmet tabanlı mimarilerin çoğu tarafından gerçekleştirilen yaklaşımdır.

Üstelik, ACID stili veya iki aşamalı tamamlama işlemleri yalnızca mikro hizmet ilkelerine karşı değildir; birçok NoSQL veritabanı (Azure Cosmos DB, MongoDB vb. gibi), dağıtılmış veritabanları senaryolarında tipik olarak iki aşamalı tamamlama işlemlerini desteklemez. Ancak, hizmetler ve veritabanları arasında veri tutarlılığı sağlamak gereklidir. Bu zorluk, bazı verilerin gereksiz olması gerektiğinde birden fazla mikro hizmette değişiklik yayma sorusıyla de ilgilidir. Örneğin, kataloğun mikro hizmetinde ve sepetindeki ürün adının veya açıklamasının olması gerektiğinde Mikro hizmet.

Bu sorun için iyi bir çözüm, olay odaklı iletişim ve bir Yayımla ve abone ol sistemi ile ifade edilen mikro hizmetler arasındaki nihai tutarlılığı kullanmaktır. Bu konular, bu kılavuzda daha sonra [zaman uyumsuz olay odaklı iletişim](asynchronous-message-based-communication.md#asynchronous-event-driven-communication) bölümünde ele alınmıştır.

## <a name="challenge-4-how-to-design-communication-across-microservice-boundaries"></a>Sınama \#4: mikro hizmet sınırları genelinde iletişim tasarlama

Mikro hizmet sınırları genelinde iletişim kurmak gerçek bir zorluk dır. Bu bağlamda iletişim, kullanmanız gereken Protokolü (HTTP ve REST, AMQP, mesajlaşma vb.) ifade etmez. Bunun yerine, hangi iletişim stilini kullanacağınızı ve özellikle mikro hizmetlerinizin ne şekilde bağlanmış olduğunu ele alınmaktadır. Bir başarısızlık düzeyine bağlı olarak, hata oluştuğunda sisteminizde bu hatanın etkisi önemli ölçüde farklılık gösterecektir.

Mikro hizmet tabanlı bir uygulama gibi dağıtılmış bir sistemde, çok sayıda sunucu veya ana bilgisayar üzerinde dağıtılmış hizmetleri kapsayan çok sayıda yapıtı ile, bileşen sonunda başarısız olur. Kısmi hata ve hatta daha büyük kesintiler meydana gelir. bu nedenle, mikro hizmetlerinizi ve bu tür dağıtılmış sistem üzerindeki yaygın riskleri göz önünde bulundurarak iletişim kurmak gerekir.

Popüler bir yaklaşım, basitliği nedeniyle HTTP (REST) tabanlı mikro hizmetleri uygulamaktır. HTTP tabanlı bir yaklaşım kusursuz kabul edilebilir; Buradaki sorun, nasıl kullanılacağı ile ilgilidir. İstemci uygulamalarından veya API ağ geçitlerinden gelen mikro hizmetleriniz ile etkileşim kurmak için yalnızca HTTP isteklerini ve yanıtlarını kullanırsanız, bu iyi bir deyişle. Ancak mikro hizmetler genelinde zaman uyumlu HTTP çağrılarının uzun zincirlerini oluşturursanız, mikro hizmetler tek parçalı bir uygulamadaki nesneler olsaydı, uygulamanız en sonunda sorunlar halinde çalışacaktır.

Örneğin, istemci uygulamanızın sıralama mikro hizmeti gibi tek bir mikro hizmete HTTP API çağrısı yaptığı hakkında düşünün. Eğer mikro hizmet sıralaması aynı istek/yanıt döngüsünün içinde HTTP kullanarak ek mikro hizmetleri çağırırsa, bir HTTP çağrıları zinciri oluşturursunuz. Başlangıçta makul bir şekilde ses verebilir. Bununla birlikte, bu yolu kapatmakta dikkate alınması gereken önemli noktaları vardır:

- Engelleme ve düşük performans. HTTP 'nin zaman uyumlu doğası nedeniyle, tüm iç HTTP çağrıları tamamlanana kadar özgün istek yanıt almaz. Bu çağrıların sayısının önemli ölçüde artıp artmadığını ve aynı zamanda bir mikro hizmete yönelik ara HTTP çağrılarından biri engellendiğinde düşünün. Sonuç performansı etkilendi ve ek HTTP istekleri artdıkça genel ölçeklenebilirlik de üstel olarak etkilenir.

- HTTP ile mikro hizmetleri bir şekilde derleyin. İş mikro hizmetleri diğer iş mikro hizmetleriyle birlikte kullanılmamalıdır. İdeal olarak, diğer mikro hizmetlerin varlığı hakkında "bilgi" almamaları gerekir. Uygulamanız, örnekte olduğu gibi kupmıservice ' i kullanıyorsa, mikro hizmet başına bağımsız çalışma sınırı elde etmek neredeyse imkansızdır.

- Herhangi bir mikro hizmette hata. HTTP çağrıları ile bağlanmış bir mikro hizmetler zinciri uyguladıysanız, mikro hizmetlerden herhangi biri başarısız olduğunda (ve sonuç verdiğinde) mikro hizmet zincirinin tamamı başarısız olur. Mikro hizmet tabanlı bir sistem, kısmi hatalarda çalışmaya ve mümkün olduğunca çalışmaya devam etmek için tasarlanmalıdır. Üstel geri alma veya devre kesici mekanizmalarıyla yeniden denemeler kullanan istemci mantığını uygulasanız bile, HTTP çağrısı zincirlerinin daha karmaşık olması, http 'ye dayalı bir hata stratejisi gerçekleştirmenin daha karmaşıktır.

Aslında, iç mikro hizmetleriniz açıklandığı gibi HTTP isteklerinin zincirlerini oluşturarak iletişim kurıyorsam, tek parçalı bir uygulamaya sahip olabilirsiniz ancak bir tane, işlem içi iletişim mekanizmaları yerine işlemler arasında HTTP 'yi temel alır.

Bu nedenle, mikro hizmet bağımsız çalışma sınırı zorlamak ve daha iyi dayanıklılık sağlamak için, mikro hizmetler genelinde istek/yanıt iletişimi zincirlerinin kullanımını en aza indirmelisiniz. Zaman uyumsuz ileti ve olay tabanlı iletişim kullanarak ya da (zaman uyumsuz) HTTP yoklamasını, özgün HTTP isteğinden bağımsız olarak kullanarak, mikro hizmet iletişimi için yalnızca zaman uyumsuz etkileşim kullanmanız önerilir/ Yanıt çevrimi.

Zaman uyumsuz iletişimin kullanımı, [zaman uyumsuz mikro hizmet tümleştirmesi, mikro hizmetin bağımsız çalışma sınırı](communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy) ve [zaman uyumsuz ileti tabanlı iletişimi](asynchronous-message-based-communication.md)zorladığı bölümlerde bu kılavuzda daha sonra ek ayrıntılarla açıklanır.

## <a name="additional-resources"></a>Ek kaynaklar

- Üst **sınır** \
  <https://en.wikipedia.org/wiki/CAP_theorem>

- **Nihai tutarlılık** \
  <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Veri tutarlılığı** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Marwler. CQRS (Komut ve Sorgu Sorumluluklarının Ayrılığı)**  \
  <https://martinfowler.com/bliki/CQRS.html>

- **Gerçekleştirilmiş görünüm** \
  <https://docs.microsoft.com/azure/architecture/patterns/materialized-view>

- **Charles satırı. ACID ile temel: veritabanı Işlem Işleme** \ ' ın kaydırma pH
  <https://www.dataversity.net/acid-vs-base-the-shifting-ph-of-database-transaction-processing/>

- **Telafi işlemi** \
  <https://docs.microsoft.com/azure/architecture/patterns/compensating-transaction>

- **UDI Dahan. Hizmet odaklı bileşim** \
  <http://udidahan.com/2014/07/30/service-oriented-composition-with-video/>

>[!div class="step-by-step"]
>[Önceki](logical-versus-physical-architecture.md)
>[İleri](identify-microservice-domain-model-boundaries.md)
