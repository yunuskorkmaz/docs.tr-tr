---
title: Dayanıklı iletişim
description: Azure için Cloud Native .NET uygulamaları tasarlama | Esnek Iletişim
ms.date: 06/30/2019
ms.openlocfilehash: d7fd4552059f527ad5166dcb6be04248bfad8e4a
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214496"
---
# <a name="resilient-communications"></a>Dayanıklı iletişimler

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Bu kitapta, geleneksel tek parçalı Uygulama tasarımının ötesine geçme ve dağıtılmış, kendinden bağımsız bir hizmet kümesinin bağımsız olarak çalıştığı ve her biriyle iletişim kuran mikro hizmet tabanlı bir mimariyi benimseme evangelized. diğer bir deyişle, HTTP ve HTTPS gibi standart iletişim protokollerini kullanma. Böyle bir mimari birçok önemli avantaj satın alırken birçok zorluk da sunar. Örneğin, aşağıdaki kaygıları göz önünde bulundurun:

- *İşlem dışı ağ iletişimi.* Her hizmet, ağ tıkanıklığı, gecikme süresi ve geçici hataları tanıtan bir ağ protokolü üzerinden iletişim kurar.
- *Hizmet bulma.* Her hizmet kendi IP adresine ve bağlantı noktasına sahip bir makine kümesi üzerinde çalışırken, hizmetler birbirleriyle nasıl keşfedip birbirleriyle iletişim kurar?
- *Resiliency.* Kısa süreli arızaların nasıl yönetileceği ve sistemin kararlı tutulması nasıl yapılır?
- *Yük Dengeleme.* Gelen trafik bir hizmetin birden fazla örneğine nasıl dağıtılır?
- *Güven.* Aktarım düzeyi şifreleme ve sertifika yönetimi gibi güvenlik sorunları nasıl zorlanır?
- \* Dağıtılmış Izleme. -Birden çok tüketim hizmeti genelinde tek bir istek için izlenebilirliği ve izlemeyi nasıl ilişkilendirirsiniz ve yakalarsınız?

Bu sorunlar çeşitli kitaplıklar ve çerçevelerle ele alınabilir, ancak kod tabanınızın içinde uygulanması pahalı, karmaşık ve zaman alıcı olabilir. Üstelik, altyapı sorunlarının iş mantığıyla birlikte bulunduğu bir çözüm ile bitimuz.

## <a name="service-mesh"></a>Hizmet ağı

*Hizmet ağı*ile yeni ve hızlı bir şekilde gelişen teknolojiyi göz önünde bulundurmanız daha iyi bir yaklaşımdır. [Hizmet ağı](https://www.nginx.com/blog/what-is-a-service-mesh/) , hizmet iletişimini ve yukarıda bahsedilen birçok zorluğu ele almak için yerleşik yeteneklere sahip yapılandırılabilir bir altyapı katmanıdır. Bu sorunları iş kodunuzla ayırır ve bunları hizmetlerinizin her birine eşlik eden bir hizmet proxy 'sine taşIar. Genellikle [sepet deseninin](https://docs.microsoft.com/azure/architecture/patterns/sidecar)adı verilen hizmet ağı ara sunucusu, iş kodınızdan yalıtım ve kapsülleme sağlamak üzere ayrı bir işleme dağıtılır. Ancak, proxy ile birlikte oluşturulan hizmete yakından bağlanır ve yaşam döngüsünü paylaştırılır. Şekil 6-9, bu senaryoyu gösterir.

![Yan otomobil ile hizmet ağı](./media/service-mesh-with-side-car.png)

**Şekil 6-9**. Yan otomobil ile hizmet ağı

Önceki şekilde, proxy 'nin mikro hizmetler ve küme arasındaki iletişimi nasıl kestiğine ve yönettiğini aklınızda olduğunu aklınızda.

Hizmet kafesi, mantıksal olarak iki farklı bileşene ayrılır: [Veri düzlemi](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) ve [Denetim düzlemi](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc). Şekil 6-10, bu bileşenleri ve bunların sorumluluklarını gösterir.

![Hizmet ağı denetimi ve veri düzlemi](./media/istio-control-and-data-plane.png)

**Şekil 6-10.** Hizmet ağı denetimi ve veri düzlemi

Bir hizmet ağı yapılandırıldıktan sonra oldukça işlevseldir. Hizmet bulma uç noktasından karşılık gelen bir örnek havuzunu alabilir. Daha sonra belirli bir örneğe bir istek gönderebilir ve sonucun gecikme süresini ve yanıt türünü kaydedebilir. Bir kafes, son istekler için gözlemlenen gecikme süresi de dahil olmak üzere birçok etkene dayanarak hızlı bir yanıt döndürmesinin en olası örneğini seçebilir.

Bir örnek yanıt vermeyi başaramazsa veya başarısız olursa, ağ başka bir örnekteki isteği yeniden deneyebilir. Bir havuz sürekli olarak hata döndürürse, bir ağ, daha sonra yeniden denenmek üzere Yük Dengeleme havuzundan çıkarabilir. Bir istek zaman aşımına uğrarsa, bir ağ başarısız olabilir ve isteği yeniden deneyebilir. Bir kafes, daha sonra merkezi bir ölçüm sistemine yayınlanmayan ölçümler ve dağıtılmış izleme biçimindeki davranışı yakalar.

## <a name="istio-and-envoy"></a>İstio ve Envoy

Şu anda birkaç hizmet ağı seçeneği mevcut olsa da, bu yazma sırasında en popüler olan [Istio](https://istio.io/docs/concepts/what-is-istio/) . IBM, Google ve Lyft kaynaklı bir Birleşik hizmet, yeni veya mevcut bir dağıtılmış uygulamayla tümleştirilebilen açık kaynaklı bir tekliftir. Mikro hizmetleri güvenli hale getirmek, bağlamak ve izlemek için tutarlı ve kapsamlı bir çözüm sağlar. Özellikleri şunları içerir:

- Güçlü kimlik tabanlı kimlik doğrulaması ve yetkilendirmeyle bir kümede hizmetten hizmete iletişimi güvenli hale getirme.
- HTTP, [GRPC](https://grpc.io/), WEBSOCKET ve TCP trafiği için otomatik yük dengeleme.
- Zengin yönlendirme kuralları, yeniden denemeler, yük devretme ve hata ekleme ile trafik davranışının ayrıntılı denetimi.
- Erişim denetimlerini, hız sınırlarını ve kotaları destekleyen takılabilir bir ilke katmanı ve yapılandırma API 'SI.
- Küme giriş ve çıkış dahil olmak üzere bir küme içindeki tüm trafiğe yönelik otomatik ölçümler, Günlükler ve izlemeler.

Bir Istio uygulamasına yönelik anahtar bileşen, [Envoy proxy 'sine](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)sahip bir proxy hizmetidir. Lyft 'den kaynaklanan ve daha sonra [Cloud Native Computing Foundation](https://www.cncf.io/) 'a katkıda bulunulan (Bölüm 1 ' de ele alınmıştır), Envoy proxy her bir hizmetle birlikte çalışır ve aşağıdaki özellikler için platformdan bağımsız bir temel sağlar:

- Dinamik hizmet bulma.
- Yük Dengeleme.
- TLS sonlandırma.
- HTTP ve gRPC proxy 'leri.
- Devre kesici dayanıklılığı.
- Durum denetimleri.
- [Kanarya](https://martinfowler.com/bliki/CanaryRelease.html) dağıtımlarıyla güncelleştirmeler kullanıma alınıyor.

Daha önce anlatıldığı gibi, Envoy kümedeki her mikro hizmet için bir sepet olarak dağıtılır.

## <a name="integration-with-azure-kubernetes-services"></a>Azure Kubernetes hizmetleriyle tümleştirme

Azure bulut, Azure Kubernetes Hizmetleri içinde bu şekilde çalışan ve doğrudan destek sağlar. Aşağıdaki bağlantılar başlamanıza yardımcı olabilir:

- [AKS 'e Istio 'da yükleme](https://docs.microsoft.com/azure/aks/istio-install)
- [AKS ve Istio kullanma](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

>[!div class="step-by-step"]
>[Önceki](infrastructure-resiliency-azure.md)
>[İleri](monitoring-health.md)
