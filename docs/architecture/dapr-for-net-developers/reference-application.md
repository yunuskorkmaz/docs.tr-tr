---
title: Eshopondadpr başvuru uygulamasına giriş
description: Eshopondadpr başvuru uygulamasına ve geçmişine genel bakış.
author: amolenk
ms.date: 02/07/2021
ms.openlocfilehash: 86b3c329e957446bd13fed850abc4edf0cf56f0f
ms.sourcegitcommit: 456b3cd82a87b453fa737b4661295070d1b6d684
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100639276"
---
# <a name="dapr-reference-application"></a>Davpr başvuru uygulaması

Kitabın başında, Davpr 'nin temel avantajları hakkında bilgi edindiniz. DAPR 'nin, mimari ve operasyonel karmaşıklığı azaltırken takımınızın dağıtılmış uygulamalar oluşturmasına nasıl yardımcı olduğunu gördünüz. Bu şekilde, bazı küçük Davpr uygulamaları oluşturma fırsatınız vardı. Şimdi, Davpr oluşturma bloklarını ve bileşenlerini gösteren bir uçtan uca mikro hizmet uygulamasını keşfetmeye son bir süredir.

Ancak ilk olarak küçük bir geçmiş.

## <a name="eshop-on-containers"></a>kapsayıcılarda eShop

Birkaç yıl önce, Microsoft, [kapsayıcı olmayan .NET uygulamalarına yönelik .net mikro hizmetleri 'ne yönelik](https://dotnet.microsoft.com/download/e-book/microservices-architecture/pdf)popüler bir kılavuz kitabı piyasaya sürülen, önde gelen topluluk uzmanlarıyla ortaklık altında. Şekil 3-1, kitabı gösterir:

![Kapsayıcılı mikro hizmet .NET uygulamaları tasarlama.](./media/reference-application/architecting-microservices-book.png)

**Şekil 3-1**. .NET mikro hizmetleri: Kapsayıcılı .NET uygulamaları için mimari.

Dağıtılmış uygulamalar oluşturmaya yönelik ilkeler, desenler ve en iyi uygulamalar hakkında daha derin kitap. Mimari kavramların gösterildiği tam özellikli bir mikro hizmet başvuru uygulaması içerir. Eklenen, [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers), uygulama, giyme ve kahve Mug 'leri dahil olmak üzere çeşitli .net öğelerini satan bir eticaret storefront gösterir.  Yerleşik .NET Core, uygulama platformlar arası ve Linux ya da Windows kapsayıcılarında çalıştırılabilir. Şekil 3-2 orijinal eShop mimarisini gösterir.

![eShopOnContainers başvuru uygulama mimarisi.](./media/reference-application/eshop-on-containers.png)

**Şekil 3-2**. Özgün `ShopOnContainers` başvuru uygulaması.

Görebileceğiniz gibi eShopOnContainers birçok hareketli parça içerir:

1. Üç farklı ön uç istemcisi.
1. Arka uçtan ön uca soyutlamak için bir uygulama ağ geçidi.
1. Çeşitli arka uç çekirdek mikro hizmetleri.
1. Zaman uyumsuz yayın/alt mesajlaşma sağlayan bir olay veri yolu bileşeni.

EShopOnContainers başvuru uygulaması .NET Community genelinde yaygın olarak kabul edilmiştir ve birçok büyük ticari mikro hizmet uygulamasını modellemek için kullanılır.

## <a name="eshop-on-dapr"></a>Davpr üzerinde eShop

Bu kitaba eşlik eden eShop uygulamasının alternatif bir sürümü. [Eshopondadpr](https://github.com/dotnet-architecture/eShopOnDapr)olarak adlandırılır. Güncelleştirilmiş sürüm, Davpr yapı taşlarını ve bileşenlerini tümleştirerek önceki eShopOnContainers uygulamasını gelişir. Şekil 3-3, yeni kolaylaştırılmış çözüm mimarisini göstermektedir:  

![Eshopondadpr başvuru uygulaması mimarisi.](./media/reference-application/eshop-on-dapr.png)

**Şekil 3-3**. Eshopondadpr başvuru uygulaması mimarisi.

Eshopondadpr başvuru uygulamasının odağı, Davpr üzerinde olduğundan, özgün uygulama güncelleştirilmiştir. Mimari aşağıdakilerden oluşur:

1. Popüler angular SPA çerçevesinde yazılan [tek sayfalı uygulama](https://docs.microsoft.com/archive/msdn-magazine/2013/november/asp-net-single-page-applications-build-modern-responsive-web-apps-with-asp-net) ön ucu. Bir API Gateway mikro hizmetine Kullanıcı istekleri gönderir.

1. API ağ geçidi, arka uç çekirdekli mikro hizmetleri ön uç istemcisinden soyutlar. Bu, yüksek performanslı bir hizmet proxy 'si olan [Envoy](https://www.envoyproxy.io/)kullanılarak uygulanır. Envoy, gelen istekleri çeşitli arka uç mikro hizmetlerine yönlendirir. Çoğu istek basit CRUD operasyonlardır (örneğin, katalogdan markalar listesini alır) ve arka uç mikro hizmetine doğrudan çağrısıyla işlenir.

1. Diğer istekler mantıksal olarak daha karmaşıktır ve birden fazla mikro hizmetin birlikte çalışmasını gerektirir. Bu durumlarda eShopOnDapr, işlemi gerçekleştirmek için gereken mikro hizmetlerde bir iş akışını düzenleyen bir [toplayıcı mikro hizmeti](../cloud-native/service-to-service-communication.md#service-aggregator-pattern) uygular.

1. Çekirdek arka uç mikro Hizmetleri kümesi, bir eCommerce Mağazası için gereken işlevselliği içerir. Her biri kendi içinde ve diğerlerinden bağımsızdır. Her mikro hizmet, yaygın olarak kabul edilen etki alanı oluşturma desenlerine göre belirli bir *iş kapasitesini* yalıtır:

   - Sepet hizmeti müşterinin alışveriş sepeti deneyimini yönetir.
   - Katalog hizmeti, satışa sunulan ürün öğelerini yönetir.
   - Kimlik hizmeti kimlik doğrulaması ve kimliği yönetir.
   - Sipariş Hizmeti, sipariş yerleştirme ve yönetmenin tüm yönlerini işler.
   - Ödeme hizmeti müşterinin ödemesini transacts.

   Her hizmetin kendi kalıcı depolama alanı vardır. Mikro hizmet [en iyi uygulamalarına](../cloud-native/distributed-data.md#database-per-microservice-why)uymak, tüm hizmetlerin etkileşimde bulunduğu paylaşılan bir veri deposu değildir.

   Her mikro hizmetin tasarımı, bireysel gereksinimlerine göre belirlenir. Basit hizmetler, temel alınan veri depolarına erişmek için temel CRUD işlemlerini kullanır. Sıralama gibi gelişmiş hizmetler, iş karmaşıklığını yönetmek için Domain-Driven tasarım yaklaşımı kullanır. Gerekirse, hizmetler .NET Core, Java, Go, NodeJS ve daha fazlası gibi farklı teknoloji yığınlarında oluşturulabilir.

1. Son olarak, olay veri yolu, Davpr yayımlama/abone olma bileşenlerini sarmalanmış. Mikro hizmetler arasında zaman uyumsuz yayımlama/abone olma mesajlaşmasını mümkün kılar. Geliştiriciler herhangi bir Davpr tarafından desteklenen bir ileti Aracısı ekleyebilir.

### <a name="application-of-dapr-building-blocks"></a>Davpr yapı taşları uygulaması

Eshopondadpr codebase, eShopOnContainers kod temelinin daha kolay. Davpr oluşturma blokları, büyük miktarda hata durumunda bir sıhhi tesisat kodu değiştirir.

Şekil 3-4, eShop başvuru uygulamasındaki Davpr tümleştirmesini gösterir.

![Eshopondadpr başvuru uygulaması mimarisi](./media/reference-application/eshop-on-dapr-buildingblocks.png)

**Şekil 3-4**. Eshopondadpr 'de davpr tümleştirmesi.

Önceki şekilde, hangi hizmetlerin hangi Davpr oluşturma bloklarını kullanacağınızı görebilirsiniz.

1. Orijinal eShopOnContainers uygulaması, sipariş hizmetindeki DDD kavramlarını ve desenlerini gösterir. Güncelleştirilmiş Eshopondadpr 'de, sipariş hizmeti *aktör yapı taşını* alternatif bir uygulama olarak kullanır. Aktörlerin çift yönlü erişim modeli, iptal etme desteğiyle durum bilgisi olan bir sıralama işlemini uygulamayı kolaylaştırır.
1. Sipariş verme hizmeti, [bağlama yapı](bindings.md)taşı kullanarak sipariş onayı e-postaları gönderir.
1. Arka uç Hizmetleri, [yayımla & abone ol yapı bloğunu](publish-subscribe.md)kullanarak zaman uyumsuz olarak iletişim kurar.
1. Gizli dizi yönetimi gizli dizi [Yapı bloğu](secrets.md)tarafından yapılır.
1. API Gateway ve Web alışveriş toplayıcısı Hizmetleri, arka uç hizmetlerindeki yöntemleri çağırmak için [hizmet çağırma yapı taşını](service-invocation.md) kullanır.
1. Sepet hizmeti, müşterinin alışveriş sepetinin durumunu depolamak için [durum yönetimi oluşturma bloğunu](state-management.md) kullanır.

### <a name="benefits-of-applying-dapr-to-eshop"></a>Davpr 'yi eShop 'a uygulamanın avantajları

Genel olarak, Davpr yapı taşları kullanımı uygulamaya Observability ve esneklik ekler:

1. Observability: Davpr oluşturma bloklarını kullanarak, herhangi bir kod yazmak zorunda kalmadan, hizmetler ve Davpr bileşenleri arasında her iki çağrı için zengin dağıtılmış izleme elde edersiniz. EShopOnContainers 'da, öngörüleri sağlamak için büyük miktarda özel günlüğe kaydetme kullanılır.
1. Esneklik: artık bir bileşen yapılandırma dosyasını değiştirerek altyapıyı *takas* edebilirsiniz. Kod değişikliği gerekli değildir.

Aşağıda, belirli yapı taşları tarafından sunulan avantajlardan daha fazla örnek verilmiştir:

- **Hizmet çağrısı**
  - Mepr 'nin [MTLS](https://blog.cloudflare.com/introducing-tls-client-auth/)desteği sayesinde, hizmetler artık şifreli kanallar üzerinden iletişim kurar.
  - Geçici hatalar oluştuğunda, hizmet çağrıları otomatik olarak yeniden denenir.
  - Otomatik hizmet bulma, hizmetlerin birbirini bulması için gereken yapılandırma miktarını azaltır.

- **Yayımla/abone ol**
  - eShopOnContainer hem Azure Service Bus hem de Kbbitmq 'yi desteklemek için büyük miktarda özel kod içeriyordu. Geliştiriciler, yerel geliştirme ve test için üretim ve Kbbitmq için Azure Service Bus kullanır. `IEventBus`Bu ileti aracıları arasında değiştirmeyi etkinleştirmek üzere bir soyutlama katmanı oluşturuldu. Bu katman yaklaşık *700 satırdan oluşan hata* durumunda hataya neden olan koddan oluşur. Davpr ile güncelleştirilmiş uygulama yalnızca *35 satır kodu* gerektirir. Özgün kod satırlarının **%5** ' i! Daha da önemlisi, uygulama basit ve anlaşılması kolay bir işlemdir.
  - Eshopondadpr, PAPR 'nin, pub/Sub kullanmak için zengin ASP.NET Core tümleştirmesini kullanır. `Topic`İletilere abone olmak için ASP.NET Core denetleyicisi yöntemlerine öznitelikler eklersiniz. Bu nedenle, her ileti Aracısı için ayrı bir ileti işleyicisi döngüsü yazmanız gerekmez.
  - HTTP çağrıları olarak hizmete yönlendirilen iletiler, bilgi eklemek için ASP.NET Core ara yazılım kullanımını, yeni kavramlar veya SDK 'lara yönelik SDK 'lara girmeden etkinleştirir.

- **Bağlamalar**
  - EShopOnContainers çözümü, müşteriye yönelik sipariş onayını e-posta ile göndermek için bir *Yapılacaklar* öğesi içeriyordu. Bu düşünce, sonunda SendGrid gibi bir üçüncü taraf e-posta API 'SI uygulamamıştı. Davpr ile, e-posta bildiriminin uygulanması, kaynak bağlamayı yapılandırma kadar kolaydır. Dış API 'Ler veya SDK 'Ların öğrenbir olması gerekmez.

> [!NOTE]
> Aktör yapı taşı, bu kitabın ilk sürümünde ele alınmıyor. Aktör yapı bloğunda kapsamlı bir bölüm ve Eshopondadpr ile tümleştirmesi 1,1 güncelleştirmesine dahil edilir.

## <a name="summary"></a>Özet

Bu bölümde Eshopondadpr başvuru uygulamasına tanıtılmıştır. Bu, yaygın olarak popüler eShopOnContainers mikro hizmet başvuru uygulamasının bir evmidir. Eshopondadpr, bir mikro hizmet uygulaması oluşturmak için gereken karmaşıklıkları önemli ölçüde basitleştirecek şekilde büyük miktarda özel işlevi Davpr oluşturma blokları ve bileşenleri ile değiştirir.

### <a name="references"></a>Başvurular

- [Eshopondadpr](https://github.com/dotnet-architecture/eShopOnDapr)

- [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers)

- [Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri](https://dotnet.microsoft.com/download/e-book/microservices-architecture/pdf)

- [Azure için Cloud-Native .NET uygulamaları tasarlama](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf)

> [!div class="step-by-step"]
> [Önceki](getting-started.md) 
>  [Sonraki](state-management.md)
