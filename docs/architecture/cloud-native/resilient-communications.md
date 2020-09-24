---
title: Dayanıklı iletişim
description: Azure için Cloud Native .NET uygulamaları tasarlama | Esnek Iletişim
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 18b26223634efc5c05f680d0cbb7c8cbc2490a59
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166046"
---
# <a name="resilient-communications"></a><span data-ttu-id="2c9c3-103">Dayanıklı iletişimler</span><span class="sxs-lookup"><span data-stu-id="2c9c3-103">Resilient communications</span></span>

<span data-ttu-id="2c9c3-104">Bu kitapta, mikro hizmet tabanlı bir mimari yaklaşım geliştirdik.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-104">Throughout this book, we've embraced a microservice-based architectural approach.</span></span> <span data-ttu-id="2c9c3-105">Böyle bir mimari önemli avantajlar sağladığından birçok zorluk gösterir:</span><span class="sxs-lookup"><span data-stu-id="2c9c3-105">While such an architecture provides important benefits, it presents many challenges:</span></span>

- <span data-ttu-id="2c9c3-106">*İşlem dışı ağ iletişimi.*</span><span class="sxs-lookup"><span data-stu-id="2c9c3-106">*Out-of-process network communication.*</span></span> <span data-ttu-id="2c9c3-107">Her mikro hizmet, ağ tıkanıklığı, gecikme süresi ve geçici hataları tanıtan bir ağ protokolü üzerinden iletişim kurar.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-107">Each microservice communicates over a network protocol that introduces network congestion, latency, and transient faults.</span></span>

- <span data-ttu-id="2c9c3-108">*Hizmet bulma.*</span><span class="sxs-lookup"><span data-stu-id="2c9c3-108">*Service discovery.*</span></span> <span data-ttu-id="2c9c3-109">Mikro hizmetler, kendi IP adresleri ve bağlantı noktalarıyla bir makine kümesi üzerinde çalışırken birbirleriyle nasıl keşif ve iletişim kurar?</span><span class="sxs-lookup"><span data-stu-id="2c9c3-109">How do microservices discover and communicate with each other when running across a cluster of machines with their own IP addresses and ports?</span></span>

- <span data-ttu-id="2c9c3-110">*Resiliency.*</span><span class="sxs-lookup"><span data-stu-id="2c9c3-110">*Resiliency.*</span></span> <span data-ttu-id="2c9c3-111">Kısa süreli arızaların nasıl yönetileceği ve sistemin kararlı tutulması nasıl yapılır?</span><span class="sxs-lookup"><span data-stu-id="2c9c3-111">How do you manage short-lived failures and keep the system stable?</span></span>

- <span data-ttu-id="2c9c3-112">*Yük Dengeleme.*</span><span class="sxs-lookup"><span data-stu-id="2c9c3-112">*Load balancing.*</span></span> <span data-ttu-id="2c9c3-113">Gelen trafik, bir mikro hizmetin birden fazla örneğine nasıl dağıtılır?</span><span class="sxs-lookup"><span data-stu-id="2c9c3-113">How does inbound traffic get distributed across multiple instances of a microservice?</span></span>

- <span data-ttu-id="2c9c3-114">*Güven.*</span><span class="sxs-lookup"><span data-stu-id="2c9c3-114">*Security.*</span></span> <span data-ttu-id="2c9c3-115">Aktarım düzeyi şifreleme ve sertifika yönetimi gibi güvenlik sorunları nasıl zorlanır?</span><span class="sxs-lookup"><span data-stu-id="2c9c3-115">How are security concerns such as transport-level encryption and certificate management enforced?</span></span>

- <span data-ttu-id="2c9c3-116">*Dağıtılmış Izleme.*</span><span class="sxs-lookup"><span data-stu-id="2c9c3-116">*Distributed Monitoring.*</span></span> <span data-ttu-id="2c9c3-117">-Birden çok tüketen mikro hizmette tek bir istek için izlenebilirliği ve izlemeyi nasıl ilişkilendirirsiniz ve yakalarsınız?</span><span class="sxs-lookup"><span data-stu-id="2c9c3-117">- How do you correlate and capture traceability and monitoring for a single request across multiple consuming microservices?</span></span>

<span data-ttu-id="2c9c3-118">Bu sorunları farklı kitaplıklar ve çerçevelerle ele alabilirsiniz, ancak uygulama pahalı, karmaşık ve zaman alıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-118">You can address these concerns with different libraries and frameworks, but the implementation can be expensive, complex, and time-consuming.</span></span> <span data-ttu-id="2c9c3-119">Ayrıca iş mantığına bağlı altyapı endişeleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-119">You also end up with infrastructure concerns coupled to business logic.</span></span>

## <a name="service-mesh"></a><span data-ttu-id="2c9c3-120">Hizmet ağı</span><span class="sxs-lookup"><span data-stu-id="2c9c3-120">Service mesh</span></span>

<span data-ttu-id="2c9c3-121">Daha iyi bir yaklaşım, *hizmet ağı*olan gelişen bir teknolojidir.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-121">A better approach is an evolving technology entitled *Service Mesh*.</span></span> <span data-ttu-id="2c9c3-122">[Hizmet ağı](https://www.nginx.com/blog/what-is-a-service-mesh/) , hizmet iletişimini ve yukarıda bahsedilen diğer zorlukları işlemek için yerleşik yeteneklere sahip yapılandırılabilir bir altyapı katmanıdır.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-122">A [service mesh](https://www.nginx.com/blog/what-is-a-service-mesh/) is a configurable infrastructure layer with built-in capabilities to handle service communication and the other challenges mentioned above.</span></span> <span data-ttu-id="2c9c3-123">Bu sorun, bir hizmet proxy 'sine taşıyarak bu kaygıları ayırır.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-123">It decouples these concerns by moving them into a service proxy.</span></span> <span data-ttu-id="2c9c3-124">Ara sunucu, iş kodu yalıtımı sağlamak için ayrı bir işleme ( [sepet](/azure/architecture/patterns/sidecar)olarak adlandırılır) dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-124">The proxy is deployed into a separate process (called a [sidecar](/azure/architecture/patterns/sidecar)) to provide isolation from business code.</span></span> <span data-ttu-id="2c9c3-125">Ancak, sepet hizmeti ile birlikte oluşturulur ve yaşam döngüsünü paylaşır.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-125">However, the sidecar is linked to the service - it's created with it and shares its lifecycle.</span></span> <span data-ttu-id="2c9c3-126">Şekil 6-7, bu senaryoyu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-126">Figure 6-7 shows this scenario.</span></span>

![Yan otomobil ile hizmet ağı](./media/service-mesh-with-side-car.png)

<span data-ttu-id="2c9c3-128">**Şekil 6-7**.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-128">**Figure 6-7**.</span></span> <span data-ttu-id="2c9c3-129">Yan otomobil ile hizmet ağı</span><span class="sxs-lookup"><span data-stu-id="2c9c3-129">Service mesh with a side car</span></span>

<span data-ttu-id="2c9c3-130">Önceki şekilde, proxy 'nin mikro hizmetler ve küme arasındaki iletişimi nasıl kestiğine ve yönettiğini aklınızda olduğunu aklınızda.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-130">In the previous figure, note how the proxy intercepts and manages communication among the microservices and the cluster.</span></span>

<span data-ttu-id="2c9c3-131">Hizmet kafesi iki farklı bileşene mantıksal olarak ayrılır: bir [veri düzlemi](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) ve [Denetim düzlemi](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span><span class="sxs-lookup"><span data-stu-id="2c9c3-131">A service mesh is logically split into two disparate components: A [data plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) and [control plane](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc).</span></span> <span data-ttu-id="2c9c3-132">Şekil 6-8, bu bileşenleri ve bunların sorumluluklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-132">Figure 6-8 shows these components and their responsibilities.</span></span>

![Hizmet ağı denetimi ve veri düzlemi](./media/istio-control-and-data-plane.png)

<span data-ttu-id="2c9c3-134">**Şekil 6-8.**</span><span class="sxs-lookup"><span data-stu-id="2c9c3-134">**Figure 6-8.**</span></span> <span data-ttu-id="2c9c3-135">Hizmet ağı denetimi ve veri düzlemi</span><span class="sxs-lookup"><span data-stu-id="2c9c3-135">Service mesh control and data plane</span></span>

<span data-ttu-id="2c9c3-136">Bir hizmet ağı yapılandırıldıktan sonra oldukça işlevseldir.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-136">Once configured, a service mesh is highly functional.</span></span> <span data-ttu-id="2c9c3-137">Hizmet bulma uç noktasından karşılık gelen bir örnek havuzunu alabilir.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-137">It can retrieve a corresponding pool of instances from a service discovery endpoint.</span></span> <span data-ttu-id="2c9c3-138">Daha sonra ağ, belirli bir örneğe bir istek gönderebilir ve sonucun gecikme süresini ve yanıt türünü kaydedebilir.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-138">The mesh can then send a request to a specific instance, recording the latency and response type of the result.</span></span> <span data-ttu-id="2c9c3-139">Bir kafes, son istekler için gözlemlenen gecikme süresi de dahil olmak üzere birçok etkene dayanarak hızlı bir yanıt döndürmesinin en olası örneğini seçebilir.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-139">A mesh can choose the instance most likely to return a fast response based on many factors, including its observed latency for recent requests.</span></span>

<span data-ttu-id="2c9c3-140">Bir örnek yanıt vermezse veya başarısız olursa, ağ başka bir örnekteki isteği yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-140">If an instance is unresponsive or fails, the mesh will retry the request on another instance.</span></span> <span data-ttu-id="2c9c3-141">Hata döndürürse, bir Ağ Yük Dengeleme havuzundan örneği çıkarır ve sonra da bunu yeniden dener.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-141">If it returns errors, a mesh will evict the instance from the load-balancing pool and restate it after it heals.</span></span> <span data-ttu-id="2c9c3-142">Bir istek zaman aşımına uğrarsa, bir ağ başarısız olabilir ve isteği yeniden deneyebilir.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-142">If a request times out, a mesh can fail and then retry the request.</span></span> <span data-ttu-id="2c9c3-143">Bir kafes, bir merkezi ölçüm sistemine ölçümleri ve dağıtılmış izlemeyi yakalar ve yayar.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-143">A mesh captures and emits metrics and distributed tracing to a centralized metrics system.</span></span>

## <a name="istio-and-envoy"></a><span data-ttu-id="2c9c3-144">İstio ve Envoy</span><span class="sxs-lookup"><span data-stu-id="2c9c3-144">Istio and Envoy</span></span>

<span data-ttu-id="2c9c3-145">Şu anda birkaç hizmet ağı seçeneği mevcut olsa da, bu yazma sırasında en popüler olan [istio](https://istio.io/docs/concepts/what-is-istio/) .</span><span class="sxs-lookup"><span data-stu-id="2c9c3-145">While a few service mesh options currently exist, [Istio](https://istio.io/docs/concepts/what-is-istio/) is the most popular at the time of this writing.</span></span> <span data-ttu-id="2c9c3-146">İstio, IBM, Google ve Lyft ile Birleşik bir Venn.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-146">Istio is a joint venture from IBM, Google, and Lyft.</span></span> <span data-ttu-id="2c9c3-147">Bu, yeni veya mevcut bir dağıtılmış uygulamayla tümleştirilebilen açık kaynaklı bir tekliftir.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-147">It's an open-source offering that can be integrated into a new or existing distributed application.</span></span> <span data-ttu-id="2c9c3-148">Teknoloji, mikro hizmetleri güvenli hale getirmek, bağlamak ve izlemek için tutarlı ve kapsamlı bir çözüm sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-148">The technology provides a consistent and complete solution to secure, connect, and monitor microservices.</span></span> <span data-ttu-id="2c9c3-149">Özellikleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="2c9c3-149">Its features include:</span></span>

- <span data-ttu-id="2c9c3-150">Güçlü kimlik tabanlı kimlik doğrulaması ve yetkilendirmeyle bir kümede hizmetten hizmete iletişimi güvenli hale getirme.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-150">Secure service-to-service communication in a cluster with strong identity-based authentication and authorization.</span></span>
- <span data-ttu-id="2c9c3-151">HTTP, [GRPC](https://grpc.io/), WEBSOCKET ve TCP trafiği için otomatik yük dengeleme.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-151">Automatic load balancing for HTTP, [gRPC](https://grpc.io/), WebSocket, and TCP traffic.</span></span>
- <span data-ttu-id="2c9c3-152">Zengin yönlendirme kuralları, yeniden denemeler, yük devretme ve hata ekleme ile trafik davranışının ayrıntılı denetimi.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-152">Fine-grained control of traffic behavior with rich routing rules, retries, failovers, and fault injection.</span></span>
- <span data-ttu-id="2c9c3-153">Erişim denetimlerini, hız sınırlarını ve kotaları destekleyen takılabilir bir ilke katmanı ve yapılandırma API 'SI.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-153">A pluggable policy layer and configuration API supporting access controls, rate limits, and quotas.</span></span>
- <span data-ttu-id="2c9c3-154">Küme giriş ve çıkış dahil olmak üzere bir küme içindeki tüm trafiğe yönelik otomatik ölçümler, Günlükler ve izlemeler.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-154">Automatic metrics, logs, and traces for all traffic within a cluster, including cluster ingress and egress.</span></span>

<span data-ttu-id="2c9c3-155">Bir Istio uygulamasına yönelik anahtar bileşen, [Envoy proxy 'sine](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)sahip bir proxy hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-155">A key component for an Istio implementation is a proxy service entitled the [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy).</span></span> <span data-ttu-id="2c9c3-156">Her bir hizmetle birlikte çalışır ve aşağıdaki özellikler için platformdan bağımsız bir temel sağlar:</span><span class="sxs-lookup"><span data-stu-id="2c9c3-156">It runs alongside each service and provides a platform-agnostic foundation for the following features:</span></span>

- <span data-ttu-id="2c9c3-157">Dinamik hizmet bulma.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-157">Dynamic service discovery.</span></span>
- <span data-ttu-id="2c9c3-158">Yük dengeleme.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-158">Load balancing.</span></span>
- <span data-ttu-id="2c9c3-159">TLS sonlandırma.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-159">TLS termination.</span></span>
- <span data-ttu-id="2c9c3-160">HTTP ve gRPC proxy 'leri.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-160">HTTP and gRPC proxies.</span></span>
- <span data-ttu-id="2c9c3-161">Devre kesici dayanıklılığı.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-161">Circuit breaker resiliency.</span></span>
- <span data-ttu-id="2c9c3-162">Durum denetimleri.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-162">Health checks.</span></span>
- <span data-ttu-id="2c9c3-163">[Kanarya](https://martinfowler.com/bliki/CanaryRelease.html) dağıtımlarıyla güncelleştirmeler kullanıma alınıyor.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-163">Rolling updates with [canary](https://martinfowler.com/bliki/CanaryRelease.html) deployments.</span></span>

<span data-ttu-id="2c9c3-164">Daha önce anlatıldığı gibi, Envoy kümedeki her mikro hizmet için bir sepet olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-164">As previously discussed, Envoy is deployed as a sidecar to each microservice in the cluster.</span></span>

## <a name="integration-with-azure-kubernetes-services"></a><span data-ttu-id="2c9c3-165">Azure Kubernetes hizmetleriyle tümleştirme</span><span class="sxs-lookup"><span data-stu-id="2c9c3-165">Integration with Azure Kubernetes Services</span></span>

<span data-ttu-id="2c9c3-166">Azure bulut, Azure Kubernetes Hizmetleri içinde bu şekilde çalışan ve doğrudan destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c9c3-166">The Azure cloud embraces Istio and provides direct support for it within Azure Kubernetes Services.</span></span> <span data-ttu-id="2c9c3-167">Aşağıdaki bağlantılar başlamanıza yardımcı olabilir:</span><span class="sxs-lookup"><span data-stu-id="2c9c3-167">The following links can help you get started:</span></span>

- [<span data-ttu-id="2c9c3-168">AKS 'e Istio 'da yükleme</span><span class="sxs-lookup"><span data-stu-id="2c9c3-168">Installing Istio in AKS</span></span>](/azure/aks/istio-install)
- [<span data-ttu-id="2c9c3-169">AKS ve Istio kullanma</span><span class="sxs-lookup"><span data-stu-id="2c9c3-169">Using AKS and Istio</span></span>](/azure/aks/istio-scenario-routing)

### <a name="references"></a><span data-ttu-id="2c9c3-170">Başvurular</span><span class="sxs-lookup"><span data-stu-id="2c9c3-170">References</span></span>

- [<span data-ttu-id="2c9c3-171">Polly</span><span class="sxs-lookup"><span data-stu-id="2c9c3-171">Polly</span></span>](http://www.thepollyproject.org/)

- [<span data-ttu-id="2c9c3-172">Yeniden deneme biçimi</span><span class="sxs-lookup"><span data-stu-id="2c9c3-172">Retry pattern</span></span>](/azure/architecture/patterns/retry)

- [<span data-ttu-id="2c9c3-173">Devre Kesici düzeni</span><span class="sxs-lookup"><span data-stu-id="2c9c3-173">Circuit Breaker pattern</span></span>](/azure/architecture/patterns/circuit-breaker)

- [<span data-ttu-id="2c9c3-174">Azure 'da esnekliği teknik incelemesi</span><span class="sxs-lookup"><span data-stu-id="2c9c3-174">Resilience in Azure whitepaper</span></span>](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [<span data-ttu-id="2c9c3-175">Ağ gecikmesi</span><span class="sxs-lookup"><span data-stu-id="2c9c3-175">network latency</span></span>](https://www.techopedia.com/definition/8553/network-latency)

- [<span data-ttu-id="2c9c3-176">Yedeklilik</span><span class="sxs-lookup"><span data-stu-id="2c9c3-176">Redundancy</span></span>](/azure/architecture/guide/design-principles/redundancy)

- [<span data-ttu-id="2c9c3-177">coğrafi çoğaltma</span><span class="sxs-lookup"><span data-stu-id="2c9c3-177">geo-replication</span></span>](/azure/sql-database/sql-database-active-geo-replication)

- [<span data-ttu-id="2c9c3-178">Azure Traffic Manager</span><span class="sxs-lookup"><span data-stu-id="2c9c3-178">Azure Traffic Manager</span></span>](/azure/traffic-manager/traffic-manager-overview)

- [<span data-ttu-id="2c9c3-179">Otomatik ölçeklendirme kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2c9c3-179">Autoscaling guidance</span></span>](/azure/architecture/best-practices/auto-scaling)

- [<span data-ttu-id="2c9c3-180">İstio dili</span><span class="sxs-lookup"><span data-stu-id="2c9c3-180">Istio</span></span>](https://istio.io/docs/concepts/what-is-istio/)

- [<span data-ttu-id="2c9c3-181">Envoy proxy</span><span class="sxs-lookup"><span data-stu-id="2c9c3-181">Envoy proxy</span></span>](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
><span data-ttu-id="2c9c3-182">[Önceki](infrastructure-resiliency-azure.md) 
> [Sonraki](monitoring-health.md)</span><span class="sxs-lookup"><span data-stu-id="2c9c3-182">[Previous](infrastructure-resiliency-azure.md)
[Next](monitoring-health.md)</span></span>
