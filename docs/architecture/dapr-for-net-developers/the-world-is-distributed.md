---
title: Dünya dağıtıldı
description: Tek parçalı ve SOA yaklaşımları ile Dağıtılmış uygulamaların avantajları ve güçlükleri.
author: robvet
ms.date: 02/17/2021
ms.openlocfilehash: df182e81bcf95a84fc283dbb945d20f2218b0d0b
ms.sourcegitcommit: d623f686701b94bef905ec5e93d8b55d031c5d6f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/17/2021
ms.locfileid: "103623947"
---
# <a name="the-world-is-distributed"></a>Dünya dağıtıldı

Yalnızca ' cool KID ': *modern, dağıtılmış sistemler ve tek parçalı uygulamalar vardır!*

Ancak, bu yalnızca "seyrek erişimli" değildir. İlerleyen BT liderleri, Kurumsal Mimarlar ve kurnaz geliştiricileri, modern dağıtılmış uygulamaları araştırıp değerlendirdiklerinde bu düşünceleri yankılandırmaktadır. Birçok, içinde satın alınmış. Bunlar, dağıtılmış mikro hizmet uygulamalarının ilkelerine, desenlerine ve uygulamalarına göre, mevcut kurumsal uygulamaları yeni ve yeniden modelliyoruz.

Ancak, bu gelişden çok sayıda soru yükseltilir...

- Dağıtılmış uygulama tam olarak nedir?
- Neden popülerliği edindikleri?
- Maliyetler nelerdir?
- Yani, ne kadar avantajları vardır?

Başlamak için geri sarın ve son 15 yıla göz atalım. Bu süre boyunca, genellikle uygulamaları tek bir tek parçalı birim olarak geliştirdik. Şekil 1-1, mimariyi gösterir.

![Tek parçalı mimari.](./media/the-world-is-distributed/monolithic-design.png)

**Şekil 1-1**. Tek parçalı mimari.

Tek sunuculu bir işlemde sıralama, kimlik ve pazarlama modüllerinin nasıl yürütüleceğini aklınızda edin. Uygulama verileri paylaşılan bir veritabanında depolanır. İş işlevselliği, HTML ve yeniden oluşturulan arayüzler aracılığıyla sunulur.

Birçok şekilde tek parçalı uygulamalar vardır `straightforward` . Bunlar basittir:

- Oluşturma
- Test
- Dağıtma
- Sorun giderme
- Dikey olarak Ölçeklendir (ölçeği büyütme)

Ancak, tek parçalı mimarilerin önemli güçlükleri olabilir.

Zaman içinde, denetimin kaybedilme işlemini yaptığınız bir noktaya ulaşabilirsiniz...

- Mimariden, tek bir kişinin anlamaması için overwhelmingly karmaşık hale geldi.
- Her biri istenmeden ve pahalı yan etkileri getirmekle birlikte değişiklikler yapmanız gerekir.
- Yeni özellikler/düzeltmeler, uygulama zaman alan ve pahalı hale gelir.
- En küçük değişiklik bile tüm uygulama pahalı ve riskli bir tam dağıtımı gerektirir.
- Kararsız bir bileşen sistemin tamamını kilitedebilir.
- Yeni teknolojiler ve çerçeveler eklemek bir seçenek değildir.
- Çevik teslim yöntemlerinin uygulanması zordur.
- Kod tabanı, ' de hiçbir zaman sonlandırma "özel durumlar" ile bir arada bulunan mimari Eroi 'ler olarak ayarlanır.
- Danışmanların sonunda yer aldığı ve yeniden yazmanız söylüyoruz.

BT uygulayıcıları bu durumu çağırır `the Fear Cycle` . Teknoloji işletmenizde herhangi bir süre boyunca karşılaştıysanız, bu sorunla karşılaştık. BT bütçenize neşeli ve BT bütçenizi tüketmektedir. Yeni ve yenilikçi çözümler oluşturmak yerine, bütçelerinizdeki çoğu eski uygulamaları korumak için kullanılır.

Korku yerine işletmeler gerekir `speed and agility` . Bunlar, piyasa koşullarına hızlı yanıt verebilecekleri mimari bir stil arar. Canlı bir uygulamanın küçük bölümlerini güncelleştirmek ve tek tek ölçeklendirmek anında gerekir.

[Hizmet odaklı mimari](https://en.wikipedia.org/wiki/Service-oriented_architecture)veya, hız ve çeviklik elde etmeye yönelik erken bir girişim, veya `SOA` . Bu modelde, hizmet tüketicileri ve hizmet sağlayıcıları, genellikle [kurumsal Service Bus](https://en.wikipedia.org/wiki/Enterprise_service_bus)veya olarak adlandırılan ara yazılım mesajlaşma bileşenleri aracılığıyla işbirliği yapılır `ESB` . Şekil 1-2, mimariyi gösterir.

![SOA.](./media/the-world-is-distributed/soa-basic.png)

**Şekil 1-2**. SOA mimarisi.

SOA ile, ESB ile kaydedilen merkezi hizmet sağlayıcıları. İş mantığı, sağlayıcı ve tüketicileri bütünleştirmek için ESB 'de yerleşik olarak oluşturulur. Hizmet tüketicileri daha sonra ESB 'yi kullanarak bu sağlayıcıları bulabilir ve bunlarla iletişim kurabilir.

SOA 'nin bu yaklaşıma sahip olmasına rağmen, bu yaklaşımı uygulamak genellikle karmaşıklığı artırabilir ve performans sorunlarına neden olur. Bakım maliyetleri yüksek ve ESB ara yazılım pahalı hale geldi. Hizmetler büyük olacak. Bunlar genellikle paylaşılan bağımlılıklar ve veri depolarıdır. Sonunda, SOAs genellikle değişikliğe dayanıklı merkezi hizmetlerden oluşan bir ' dağıtılmış monoparçalı olarak ' yapısına neden olur.

Günümüzde, birçok kuruluşun sistem oluşturmaya yönelik dağıtılmış bir mikro hizmet mimari yaklaşımını benimseerek hız ve çevikliği vardır. Şekil 1-3, dağıtılmış teknikler ve uygulamalar kullanılarak oluşturulan aynı sistemi gösterir.

![Dağıtılmış mimari.](./media/the-world-is-distributed/distributed-design.png)

**Şekil 1-3**. Dağıtılmış mimari.

Aynı uygulamanın dağıtılmış bir hizmet kümesi genelinde nasıl açıklanmadığını göz önünde edin. Her biri kendi içinde bulunur ve kendi kodunu, verilerini ve bağımlılıklarını kapsüller. Her biri bir yazılım kapsayıcısında dağıtılır ve bir kapsayıcı Orchestrator tarafından yönetilir. Birden çok hizmet tarafından paylaşılan tek bir veritabanı yerine, her hizmet özel bir veritabanına sahip olur. Diğer hizmetler doğrudan bu veritabanına erişemez ve yalnızca sahibi olan hizmetin genel API 'SI aracılığıyla kullanıma sunulan verileri alabilir. Bazı hizmetlerin bir NoSQL veri deposu olmak üzere tam bir ilişkisel veritabanı gerektirdiğini not edin. Sepet hizmeti, durumunu dağıtılmış bir anahtar/değer önbelleğinde depolar. Gelen trafiğin bir API ağ geçidi hizmeti üzerinden nasıl yönlendirdiğine göz önünde. Hizmetlere yapılan çağrıların yönlendirmesinden ve çapraz kesme sorunlarını zormaktan sorumludur. En önemlisi, uygulama modern bulut platformlarında bulunan ölçeklenebilirlik, kullanılabilirlik ve dayanıklılık özelliklerinden tam olarak yararlanır.

Ancak, dağıtılmış hizmetler çevikliği ve hız sağlayacaksa, farklı bir zorluk kümesi sunabilirler. Aşağıdakileri göz önünde bulundurun...

- Dağıtılmış hizmetler birbirini nasıl bulabilir ve zaman uyumlu olarak iletişim kurabilir mi?
- Zaman uyumsuz mesajlaşma uygulayabilir miyim?
- Bir işlem genelinde bağlamsal bilgileri nasıl koruyabilirler?
- Hatalara nasıl dayanıklı hale gelebilirler?
- Dalgalanmaları karşılamak için nasıl ölçeklenebilirler?
- Nasıl izlendikleri ve gözlemlenmiştir?

Bu güçlüklerin her biri için, birden çok ürün genellikle kullanılabilir. Ancak, uygulamanızı ürün farklarından koruma altına alarak kodu sürdürülebilir ve taşınabilir hale tutarak bir zorluk sorunu.

Bu kitap, Davpr 'yi tanıtır. Davpr, dağıtılmış bir uygulama çalışma zamanı. Dağıtılmış uygulamalarla birlikte gelen birçok güçlük doğrudan ele alır. Daha ileriye bakıyor, Davpr dağıtılmış uygulama geliştirmeye yönelik bir etkiye sahip olma potansiyelini içeriyor.

## <a name="summary"></a>Özet

Bu bölümde, Dağıtılmış uygulamaların benimsenmesini tartıştık. Dağıtılmış hizmetlerden oluşan tek parçalı bir sistem yaklaşımını geliştirdik. Dağıtılmış bir yaklaşımı değerlendirirken yaygın olarak karşılaşılan güçlüklerden çoğunu sunuyoruz.

Şimdi geri dönüp, daha sonra da yeni bir Davpr dünyasını sunmamıza izin verin.

>[!div class="step-by-step"]
>[Önceki](foreword.md) 
> [Sonraki](dapr-at-20000-feet.md)
