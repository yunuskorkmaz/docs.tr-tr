---
title: Dayanıklı iletişim
description: Azure için Cloud Native .NET uygulamaları tasarlama | Esnek Iletişim
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 33e4c03c1f3d8c01f72c588326fbb0bdfa512cdd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613752"
---
# <a name="resilient-communications"></a>Dayanıklı iletişimler

Bu kitapta, mikro hizmet tabanlı bir mimari yaklaşım geliştirdik. Böyle bir mimari önemli avantajlar sağladığından birçok zorluk gösterir:

- *İşlem dışı ağ iletişimi.* Her mikro hizmet, ağ tıkanıklığı, gecikme süresi ve geçici hataları tanıtan bir ağ protokolü üzerinden iletişim kurar.

- *Hizmet bulma.* Mikro hizmetler, kendi IP adresleri ve bağlantı noktalarıyla bir makine kümesi üzerinde çalışırken birbirleriyle nasıl keşif ve iletişim kurar?

- *Resiliency.* Kısa süreli arızaların nasıl yönetileceği ve sistemin kararlı tutulması nasıl yapılır?

- *Yük Dengeleme.* Gelen trafik, bir mikro hizmetin birden fazla örneğine nasıl dağıtılır?

- *Güven.* Aktarım düzeyi şifreleme ve sertifika yönetimi gibi güvenlik sorunları nasıl zorlanır?

- *Dağıtılmış Izleme.* -Birden çok tüketen mikro hizmette tek bir istek için izlenebilirliği ve izlemeyi nasıl ilişkilendirirsiniz ve yakalarsınız?

Bu sorunları farklı kitaplıklar ve çerçevelerle ele alabilirsiniz, ancak uygulama pahalı, karmaşık ve zaman alıcı olabilir. Ayrıca iş mantığına bağlı altyapı endişeleri de vardır.

## <a name="service-mesh"></a>Hizmet ağı

Daha iyi bir yaklaşım, *hizmet ağı*olan gelişen bir teknolojidir. [Hizmet ağı](https://www.nginx.com/blog/what-is-a-service-mesh/) , hizmet iletişimini ve yukarıda bahsedilen diğer zorlukları işlemek için yerleşik yeteneklere sahip yapılandırılabilir bir altyapı katmanıdır. Bu sorun, bir hizmet proxy 'sine taşıyarak bu kaygıları ayırır. Ara sunucu, iş kodu yalıtımı sağlamak için ayrı bir işleme ( [sepet](https://docs.microsoft.com/azure/architecture/patterns/sidecar)olarak adlandırılır) dağıtılır. Ancak, sepet hizmeti ile birlikte oluşturulur ve yaşam döngüsünü paylaşır. Şekil 6-7, bu senaryoyu gösterir.

![Yan otomobil ile hizmet ağı](./media/service-mesh-with-side-car.png)

**Şekil 6-7**. Yan otomobil ile hizmet ağı

Önceki şekilde, proxy 'nin mikro hizmetler ve küme arasındaki iletişimi nasıl kestiğine ve yönettiğini aklınızda olduğunu aklınızda.

Hizmet kafesi iki farklı bileşene mantıksal olarak ayrılır: bir [veri düzlemi](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) ve [Denetim düzlemi](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc). Şekil 6-8, bu bileşenleri ve bunların sorumluluklarını gösterir.

![Hizmet ağı denetimi ve veri düzlemi](./media/istio-control-and-data-plane.png)

**Şekil 6-8.** Hizmet ağı denetimi ve veri düzlemi

Bir hizmet ağı yapılandırıldıktan sonra oldukça işlevseldir. Hizmet bulma uç noktasından karşılık gelen bir örnek havuzunu alabilir. Daha sonra ağ, belirli bir örneğe bir istek gönderebilir ve sonucun gecikme süresini ve yanıt türünü kaydedebilir. Bir kafes, son istekler için gözlemlenen gecikme süresi de dahil olmak üzere birçok etkene dayanarak hızlı bir yanıt döndürmesinin en olası örneğini seçebilir.

Bir örnek yanıt vermezse veya başarısız olursa, ağ başka bir örnekteki isteği yeniden dener. Hata döndürürse, bir Ağ Yük Dengeleme havuzundan örneği çıkarır ve sonra da bunu yeniden dener. Bir istek zaman aşımına uğrarsa, bir ağ başarısız olabilir ve isteği yeniden deneyebilir. Bir kafes, bir merkezi ölçüm sistemine ölçümleri ve dağıtılmış izlemeyi yakalar ve yayar.

## <a name="istio-and-envoy"></a>İstio ve Envoy

Şu anda birkaç hizmet ağı seçeneği mevcut olsa da, bu yazma sırasında en popüler olan [istio](https://istio.io/docs/concepts/what-is-istio/) . İstio, IBM, Google ve Lyft ile Birleşik bir Venn. Bu, yeni veya mevcut bir dağıtılmış uygulamayla tümleştirilebilen açık kaynaklı bir tekliftir. Teknoloji, mikro hizmetleri güvenli hale getirmek, bağlamak ve izlemek için tutarlı ve kapsamlı bir çözüm sağlar. Özellikleri şunları içerir:

- Güçlü kimlik tabanlı kimlik doğrulaması ve yetkilendirmeyle bir kümede hizmetten hizmete iletişimi güvenli hale getirme.
- HTTP, [GRPC](https://grpc.io/), WEBSOCKET ve TCP trafiği için otomatik yük dengeleme.
- Zengin yönlendirme kuralları, yeniden denemeler, yük devretme ve hata ekleme ile trafik davranışının ayrıntılı denetimi.
- Erişim denetimlerini, hız sınırlarını ve kotaları destekleyen takılabilir bir ilke katmanı ve yapılandırma API 'SI.
- Küme giriş ve çıkış dahil olmak üzere bir küme içindeki tüm trafiğe yönelik otomatik ölçümler, Günlükler ve izlemeler.

Bir Istio uygulamasına yönelik anahtar bileşen, [Envoy proxy 'sine](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)sahip bir proxy hizmetidir. Her bir hizmetle birlikte çalışır ve aşağıdaki özellikler için platformdan bağımsız bir temel sağlar:

- Dinamik hizmet bulma.
- Yük dengeleme.
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

### <a name="references"></a>Başvurular

- [Polly](http://www.thepollyproject.org/)

- [Yeniden deneme biçimi](https://docs.microsoft.com/azure/architecture/patterns/retry)

- [Devre kesici stili](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

- [Azure 'da esnekliği teknik incelemesi](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [Ağ gecikmesi](https://www.techopedia.com/definition/8553/network-latency)

- [Yedeklilik](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy)

- [coğrafi çoğaltma](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication)

- [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)

- [Otomatik ölçeklendirme kılavuzu](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)

- [İstio dili](https://istio.io/docs/concepts/what-is-istio/)

- [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
>[Önceki](infrastructure-resiliency-azure.md) 
> [Sonraki](monitoring-health.md)
