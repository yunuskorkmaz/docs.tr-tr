---
title: Hizmet kafesleri-WCF geliştiricileri için gRPC
description: Bir Kubernetes kümesinde gRPC hizmetlerine istekleri yönlendirmek ve dengelemek için bir hizmet ağı kullanma.
ms.date: 09/02/2019
ms.openlocfilehash: a29d6893e585c7eb60c847cef0149afeeaebcdab
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503392"
---
# <a name="service-meshes"></a><span data-ttu-id="e7139-103">Hizmet kafesleri</span><span class="sxs-lookup"><span data-stu-id="e7139-103">Service meshes</span></span>

<span data-ttu-id="e7139-104">Hizmet ağı, bir ağ içindeki yönlendirme hizmeti isteklerinin denetimini alan bir altyapı bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="e7139-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="e7139-105">Hizmet kafesleri, bir Kubernetes kümesi içindeki her türlü ağ düzeyi kaygılarını işleyebilir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="e7139-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="e7139-106">Hizmet bulma</span><span class="sxs-lookup"><span data-stu-id="e7139-106">Service discovery</span></span>
- <span data-ttu-id="e7139-107">Yük dengeleme</span><span class="sxs-lookup"><span data-stu-id="e7139-107">Load balancing</span></span>
- <span data-ttu-id="e7139-108">Hataya dayanıklılık</span><span class="sxs-lookup"><span data-stu-id="e7139-108">Fault tolerance</span></span>
- <span data-ttu-id="e7139-109">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="e7139-109">Encryption</span></span>
- <span data-ttu-id="e7139-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="e7139-110">Monitoring</span></span>

<span data-ttu-id="e7139-111">Kubernetes hizmet kafesleri, kafeste bulunan her Pod 'a *sepet proxy 'si*olarak adlandırılan ek bir kapsayıcı ekleyerek çalışır.</span><span class="sxs-lookup"><span data-stu-id="e7139-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="e7139-112">Ara sunucu tüm gelen ve giden ağ isteklerini işlemeyi devralır.</span><span class="sxs-lookup"><span data-stu-id="e7139-112">The proxy takes over handling all inbound and outbound network requests.</span></span> <span data-ttu-id="e7139-113">Daha sonra, ağ yapılandırma ve yönetimini uygulama kapsayıcılarından ayrı olarak tutabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7139-113">You can then keep configuration and management of networking matters separate from the application containers.</span></span> <span data-ttu-id="e7139-114">Çoğu durumda, bu ayrım uygulama kodunda herhangi bir değişiklik yapılmasını gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="e7139-114">In many cases, this separation doesn't require any changes to the application code.</span></span>

<span data-ttu-id="e7139-115">[Önceki bölümün örneğinde](kubernetes.md#test-the-application), Web uygulamasından alınan GRPC Isteklerinin hepsi GRPC hizmetinin tek bir örneğine yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="e7139-115">In the [previous chapter's example](kubernetes.md#test-the-application), the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="e7139-116">Bu durum hizmetin ana bilgisayar adının bir IP adresine çözümlenmesi ve IP adresinin `HttpClientHandler` örneğinin kullanım ömrü boyunca önbelleğe alınması nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="e7139-116">This happens because the service's host name is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="e7139-117">DNS aramalarını el ile işleyerek veya birden çok istemci oluşturarak bu sorunu geçici olarak çözmek mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7139-117">It might be possible to work around this by handling DNS lookups manually or creating multiple clients.</span></span> <span data-ttu-id="e7139-118">Ancak bu geçici çözüm, uygulama kodunu herhangi bir iş veya müşteri değeri eklemeden karmaşıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="e7139-118">But this workaround would complicate the application code without adding any business or customer value.</span></span>

<span data-ttu-id="e7139-119">Bir hizmet ağı kullandığınızda, uygulama kapsayıcısından gelen istekler sepet proxy 'sine gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e7139-119">When you use a service mesh, the requests from the application container are sent to the sidecar proxy.</span></span> <span data-ttu-id="e7139-120">Dışarıdan yükleme proxy 'si, daha sonra diğer hizmetin tüm örnekleri arasında onları akıllıca dağıtabilir.</span><span class="sxs-lookup"><span data-stu-id="e7139-120">The sidecar proxy can then distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="e7139-121">Kafes de şunları yapabilir:</span><span class="sxs-lookup"><span data-stu-id="e7139-121">The mesh can also:</span></span>

- <span data-ttu-id="e7139-122">Bir hizmetin tek tek örneklerinden oluşan hatalara sorunsuz bir şekilde yanıt verin.</span><span class="sxs-lookup"><span data-stu-id="e7139-122">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="e7139-123">Başarısız çağrılar veya zaman aşımları için yeniden deneme semantiğini işleyin.</span><span class="sxs-lookup"><span data-stu-id="e7139-123">Handle retry semantics for failed calls or timeouts.</span></span>
- <span data-ttu-id="e7139-124">Başarısız istekleri istemci uygulamasına döndürülmeksizin alternatif bir örneğe yeniden yönlendir.</span><span class="sxs-lookup"><span data-stu-id="e7139-124">Reroute failed requests to an alternate instance without returning to the client application.</span></span>

<span data-ttu-id="e7139-125">Aşağıdaki ekran görüntüsünde, Linkerd hizmet ağıyla çalışan StockWeb uygulaması gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e7139-125">The following screenshot shows the StockWeb application running with the Linkerd service mesh.</span></span> <span data-ttu-id="e7139-126">Uygulama kodunda değişiklik yapılmaz ve Docker görüntüsü kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e7139-126">There are no changes to the application code, and the Docker image isn't being used.</span></span> <span data-ttu-id="e7139-127">Gerekli tek değişiklik, `stockdata` ve `stockweb` Hizmetleri için YAML dosyalarındaki dağıtıma ek açıklamanın ekleniydi.</span><span class="sxs-lookup"><span data-stu-id="e7139-127">The only change required was the addition of an annotation to the deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![Hizmet ağı ile StockWeb](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="e7139-129">StockWeb uygulamasından gelen isteklerin, uygulama kodundaki tek bir `HttpClient` örneğinden kaynaklanan StockData hizmetinin her iki çoğaltmasına de yönlendirildiğini **sunucu** sütunundan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7139-129">You can see from the **Server** column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="e7139-130">Aslında, kodu gözden geçirdikten sonra, StockData Service 'e yönelik tüm 100 isteklerinin aynı `HttpClient` örneğini kullanarak aynı anda yapıldığını görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="e7139-130">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously by using the same `HttpClient` instance.</span></span> <span data-ttu-id="e7139-131">Hizmet ağı ile bu istekler arasında dengelenebilir, ancak birçok hizmet örneği kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7139-131">With the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="e7139-132">Hizmet kafesleri yalnızca bir küme içindeki trafiğe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e7139-132">Service meshes apply only to traffic within a cluster.</span></span> <span data-ttu-id="e7139-133">Dış istemciler için, bkz. bir sonraki bölüm, [Yük Dengeleme](load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="e7139-133">For external clients, see the next chapter, [Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="e7139-134">Hizmet ağ seçenekleri</span><span class="sxs-lookup"><span data-stu-id="e7139-134">Service mesh options</span></span>

<span data-ttu-id="e7139-135">Üç genel amaçlı hizmet kafesi uygulaması şu anda Kubernetes [:](https://istio.io) [ICD, Linkerd](https://linkerd.io)ve [tüketil Connect](https://consul.io/mesh.html)ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e7139-135">Three general-purpose service mesh implementations are currently available for use with Kubernetes: [Istio](https://istio.io), [Linkerd](https://linkerd.io), and [Consul Connect](https://consul.io/mesh.html).</span></span> <span data-ttu-id="e7139-136">Tüm üç istek yönlendirme/proxy sağlama, trafik şifreleme, esnekliği, konaktan konağa kimlik doğrulaması ve trafik denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7139-136">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="e7139-137">Hizmet kafesi seçme, birden fazla etkene bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="e7139-137">Choosing a service mesh depends on multiple factors:</span></span>

- <span data-ttu-id="e7139-138">Kuruluşun maliyetler, uyumluluk, ücretli destek planları vb. için özel gereksinimleri.</span><span class="sxs-lookup"><span data-stu-id="e7139-138">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="e7139-139">Kümenin doğası, boyutu, dağıtılan hizmet sayısı ve küme ağı içindeki trafik hacmi.</span><span class="sxs-lookup"><span data-stu-id="e7139-139">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="e7139-140">Ağı dağıtma ve yönetme kolaylığı ve hizmetlerle kullanma.</span><span class="sxs-lookup"><span data-stu-id="e7139-140">Ease of deploying and managing the mesh and using it with services.</span></span>

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="e7139-141">Örnek: bir dağıtıma Linkerd ekleme</span><span class="sxs-lookup"><span data-stu-id="e7139-141">Example: Add Linkerd to a deployment</span></span>

<span data-ttu-id="e7139-142">Bu örnekte, [önceki bölümde](kubernetes.md) *StockKube* uygulamasıyla linkerd hizmet ağı 'nı nasıl kullanacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="e7139-142">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="e7139-143">Bu örneği izlemek için, [Linkerd CLI 'yı yüklemeniz](https://linkerd.io/2/getting-started/#step-1-install-the-cli)gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7139-143">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="e7139-144">GitHub sürümlerini listeleyen bölümden Windows ikili dosyalarını indirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7139-144">You can download Windows binaries from the section that lists GitHub releases.</span></span> <span data-ttu-id="e7139-145">Uç sürümlerden birini değil en son *kararlı* yayını kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="e7139-145">Be sure to use the most recent *stable* release and not one of the edge releases.</span></span>

<span data-ttu-id="e7139-146">Linkerd CLı yüklü olduğunda, Kubernetes kümenize Linkerd bileşenlerini yüklemek için [Başlarken yönergelerini izleyin](https://linkerd.io/2/getting-started/index.html) .</span><span class="sxs-lookup"><span data-stu-id="e7139-146">With the Linkerd CLI installed, follow the [Getting Started](https://linkerd.io/2/getting-started/index.html) instructions to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="e7139-147">Yönergeler basittir ve yükleme, yerel bir Kubernetes örneği üzerinde yalnızca birkaç dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="e7139-147">The instructions are straightforward, and installation should take only a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="e7139-148">Kubernetes dağıtımlarını Linkerd 'e ekleme</span><span class="sxs-lookup"><span data-stu-id="e7139-148">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="e7139-149">Linkerd CLı, Kubernetes dosyalarına gerekli bölümleri ve özellikleri eklemek için bir `inject` komutu sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7139-149">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="e7139-150">Komutu çalıştırabilir ve çıktıyı yeni bir dosyaya yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7139-150">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="e7139-151">Yapılan değişiklikleri görmek için yeni dosyaları inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e7139-151">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="e7139-152">Dağıtım nesneleri için, Linkerd 'nin oluşturulduğu sırada Pod 'a bir sepet ara sunucu kapsayıcısı eklemesine söylemek için bir meta veri ek açıklaması eklenir.</span><span class="sxs-lookup"><span data-stu-id="e7139-152">For deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the pod when it's created.</span></span>

<span data-ttu-id="e7139-153">Ayrıca, `linkerd inject` komutunun çıkışını doğrudan `kubectl` için boru yapmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="e7139-153">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="e7139-154">Aşağıdaki komutlar PowerShell veya herhangi bir Linux kabuğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="e7139-154">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="e7139-155">Linkerd panosundaki Hizmetleri inceleyin</span><span class="sxs-lookup"><span data-stu-id="e7139-155">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="e7139-156">`linkerd` CLı kullanarak Linkerd panosunu açın.</span><span class="sxs-lookup"><span data-stu-id="e7139-156">Open the Linkerd dashboard by using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="e7139-157">Pano, ağa bağlı tüm hizmetler hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e7139-157">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![StockKube uygulamalarını gösteren linkerd panosu](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="e7139-159">Aşağıdaki örnekte gösterildiği gibi StockData gRPC hizmetinin çoğaltmaların sayısını arttırırsanız ve tarayıcıdaki StockWeb sayfasını yenilediğinizde, **sunucu** sütununda bir kimlik karışımı görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e7139-159">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the **Server** column.</span></span> <span data-ttu-id="e7139-160">Bu karışım, tüm kullanılabilir örneklerin istek görüyor olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="e7139-160">This mix indicates that all the available instances are serving requests.</span></span>

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 2 # Increase the target number of instances
  template:
    metadata:
      annotations:
        linkerd.io/inject: enabled
      creationTimestamp: null
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

>[!div class="step-by-step"]
><span data-ttu-id="e7139-161">[Önceki](kubernetes.md)
>[İleri](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="e7139-161">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
