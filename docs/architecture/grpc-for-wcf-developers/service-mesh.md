---
title: Hizmet kafesleri-WCF geliştiricileri için gRPC
description: Bir Kubernetes kümesinde gRPC hizmetlerine istekleri yönlendirmek ve dengelemek için bir hizmet ağı kullanma.
ms.date: 09/02/2019
ms.openlocfilehash: cc4855b1ed27e29076e4f13f5c5d3dffa63a6554
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711271"
---
# <a name="service-meshes"></a><span data-ttu-id="ed7be-103">Hizmet kafesleri</span><span class="sxs-lookup"><span data-stu-id="ed7be-103">Service meshes</span></span>

<span data-ttu-id="ed7be-104">Hizmet ağı, bir ağ içindeki yönlendirme hizmeti isteklerinin denetimini alan bir altyapı bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="ed7be-104">A service mesh is an infrastructure component that takes control of routing service requests within a network.</span></span> <span data-ttu-id="ed7be-105">Hizmet kafesleri, bir Kubernetes kümesi içindeki her türlü ağ düzeyi kaygılarını işleyebilir, örneğin:</span><span class="sxs-lookup"><span data-stu-id="ed7be-105">Service meshes can handle all kinds of network-level concerns within a Kubernetes cluster, including:</span></span>

- <span data-ttu-id="ed7be-106">Hizmet bulma</span><span class="sxs-lookup"><span data-stu-id="ed7be-106">Service discovery</span></span>
- <span data-ttu-id="ed7be-107">Yük dengeleme</span><span class="sxs-lookup"><span data-stu-id="ed7be-107">Load balancing</span></span>
- <span data-ttu-id="ed7be-108">Hataya dayanıklılık</span><span class="sxs-lookup"><span data-stu-id="ed7be-108">Fault tolerance</span></span>
- <span data-ttu-id="ed7be-109">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="ed7be-109">Encryption</span></span>
- <span data-ttu-id="ed7be-110">İzleme</span><span class="sxs-lookup"><span data-stu-id="ed7be-110">Monitoring</span></span>

<span data-ttu-id="ed7be-111">Kubernetes hizmet kafesleri, kafeste bulunan her Pod 'a *sepet proxy 'si*olarak adlandırılan ek bir kapsayıcı ekleyerek çalışır.</span><span class="sxs-lookup"><span data-stu-id="ed7be-111">Kubernetes service meshes work by adding an extra container, called a *sidecar proxy*, to each pod included in the mesh.</span></span> <span data-ttu-id="ed7be-112">Ara sunucu tüm gelen ve giden ağ isteklerini işlemeyi, ağ yapılandırma ve yönetiminin önemli bir şekilde uygulama kapsayıcılarından ayrı tutulmasını sağlar ve birçok durumda uygulama kodunda herhangi bir değişiklik yapılmasına gerek kalmadan yapılır.</span><span class="sxs-lookup"><span data-stu-id="ed7be-112">The proxy takes over handling all inbound and outbound network requests, allowing configuration and management of networking matters to be kept separate from the application containers and, in many cases, without requiring any changes to the application code.</span></span>

<span data-ttu-id="ed7be-113">Web uygulamasındaki gRPC isteklerinin hepsi gRPC hizmetinin tek bir örneğine yönlendirildiği [önceki bölümün örneğini](kubernetes.md#test-the-application)alın.</span><span class="sxs-lookup"><span data-stu-id="ed7be-113">Take the [previous chapter's example](kubernetes.md#test-the-application), where the gRPC requests from the web application were all routed to a single instance of the gRPC service.</span></span> <span data-ttu-id="ed7be-114">Bu durum hizmetin ana bilgisayar adının bir IP adresine çözümlenmesi ve IP adresinin `HttpClientHandler` örneğinin kullanım ömrü boyunca önbelleğe alınması nedeniyle oluşur.</span><span class="sxs-lookup"><span data-stu-id="ed7be-114">This happens because the service's hostname is resolved to an IP address, and that IP address is cached for the lifetime of the `HttpClientHandler` instance.</span></span> <span data-ttu-id="ed7be-115">DNS aramalarını el ile veya birden çok istemci oluşturarak bu sorunu geçici olarak çözmek mümkün olabilir, ancak bu, herhangi bir iş veya müşteri değeri eklemeden uygulama kodunu önemli ölçüde karmaşıklaştırır.</span><span class="sxs-lookup"><span data-stu-id="ed7be-115">It might be possible to work around this by handling DNS lookups manually or creating multiple clients, but this would complicate the application code considerably without adding any business or customer value.</span></span>

<span data-ttu-id="ed7be-116">Bir hizmet ağı kullanarak, uygulama kapsayıcısından gelen istekler sepet proxy 'sine gönderilir ve bu da bunları diğer hizmetin tüm örneklerine akıllıca dağıtabilen.</span><span class="sxs-lookup"><span data-stu-id="ed7be-116">Using a service mesh, the requests from the application container are sent to the sidecar proxy, which can distribute them intelligently across all instances of the other service.</span></span> <span data-ttu-id="ed7be-117">Kafes de şunları yapabilir:</span><span class="sxs-lookup"><span data-stu-id="ed7be-117">The mesh can also:</span></span>

- <span data-ttu-id="ed7be-118">Bir hizmetin tek tek örneklerinden oluşan hatalara sorunsuz bir şekilde yanıt verin.</span><span class="sxs-lookup"><span data-stu-id="ed7be-118">Respond seamlessly to failures of individual instances of a service.</span></span>
- <span data-ttu-id="ed7be-119">Başarısız çağrılar veya zaman aşımları için yeniden deneme semantiğini işle</span><span class="sxs-lookup"><span data-stu-id="ed7be-119">Handle retry semantics for failed calls or timeouts</span></span>
- <span data-ttu-id="ed7be-120">Başarısız istekleri, istemci uygulamasına hiç döndürülmeksizin alternatif bir örneğe yeniden yönlendir.</span><span class="sxs-lookup"><span data-stu-id="ed7be-120">Reroute failed requests to an alternate instance without returning to the client application at all.</span></span>

<span data-ttu-id="ed7be-121">Aşağıdaki ekran görüntüsünde, Linkerd hizmet ağıyla çalışan StockWeb uygulaması, uygulama kodunda hiçbir değişiklik yapılmıyor veya hatta kullanılan Docker görüntüsü gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ed7be-121">The following screenshot shows the StockWeb application running with the Linkerd service mesh, with no changes to the application code, or even the Docker image being used.</span></span> <span data-ttu-id="ed7be-122">Gerekli tek değişiklik, `stockdata` ve `stockweb` Hizmetleri için YAML dosyalarındaki dağıtıma ek açıklamanın ekleniydi.</span><span class="sxs-lookup"><span data-stu-id="ed7be-122">The only change required was the addition of an annotation to the Deployment in the YAML files for the `stockdata` and `stockweb` services.</span></span>

![Hizmet ağı ile StockWeb](media/service-mesh/stockweb-servicemesh-screenshot.png)

<span data-ttu-id="ed7be-124">StockWeb uygulamasından gelen isteklerin, uygulama kodundaki tek bir `HttpClient` örneğinden kaynaklanan StockData hizmetinin her iki çoğaltmasına de yönlendirildiğini sunucu sütunundan görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed7be-124">You can see from the Server column that the requests from the StockWeb application have been routed to both replicas of the StockData service, despite originating from a single `HttpClient` instance in the application code.</span></span> <span data-ttu-id="ed7be-125">Aslında, kodu gözden geçirdikten sonra, StockData hizmetine yönelik tüm 100 isteklerinin aynı anda hizmet ağı ile aynı `HttpClient` örneğini kullanarak yapıldığını görürsünüz, ancak bu istekler arasında dengelenebilir, ancak birçok hizmet örneği mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="ed7be-125">In fact, if you review the code, you'll see that all 100 requests to the StockData service are made simultaneously using the same `HttpClient` instance, yet with the service mesh, those requests will be balanced across however many service instances are available.</span></span>

<span data-ttu-id="ed7be-126">Hizmet kafesleri yalnızca bir küme içindeki trafiğe uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ed7be-126">Service meshes only apply to traffic within a cluster.</span></span> <span data-ttu-id="ed7be-127">Dış istemciler için, bkz. bir [sonraki bölüm, Yük Dengeleme](load-balancing.md).</span><span class="sxs-lookup"><span data-stu-id="ed7be-127">For external clients, see [the next chapter, Load Balancing](load-balancing.md).</span></span>

## <a name="service-mesh-options"></a><span data-ttu-id="ed7be-128">Hizmet ağ seçenekleri</span><span class="sxs-lookup"><span data-stu-id="ed7be-128">Service mesh options</span></span>

<span data-ttu-id="ed7be-129">Şu anda Kubernetes: ICD, Linkerd ve Tüketil Connect ile kullanılabilecek üç genel amaçlı hizmet kafesi uygulaması vardır.</span><span class="sxs-lookup"><span data-stu-id="ed7be-129">There are three general-purpose service mesh implementations currently available for use with Kubernetes: Istio, Linkerd, and Consul Connect.</span></span> <span data-ttu-id="ed7be-130">Tüm üç istek yönlendirme/proxy sağlama, trafik şifreleme, esnekliği, konaktan konağa kimlik doğrulaması ve trafik denetimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed7be-130">All three provide request routing/proxying, traffic encryption, resilience, host-to-host authentication, and traffic control.</span></span>

<span data-ttu-id="ed7be-131">Hizmet kafesi seçme, birden fazla etkene bağlıdır:</span><span class="sxs-lookup"><span data-stu-id="ed7be-131">Choosing a service mesh depends multiple factors:</span></span>

- <span data-ttu-id="ed7be-132">Kuruluşun maliyetler, uyumluluk, ücretli destek planları vb. için özel gereksinimleri.</span><span class="sxs-lookup"><span data-stu-id="ed7be-132">The organization's specific requirements around costs, compliance, paid support plans, and so on.</span></span>
- <span data-ttu-id="ed7be-133">Kümenin doğası, boyutu, dağıtılan hizmet sayısı ve küme ağı içindeki trafik hacmi.</span><span class="sxs-lookup"><span data-stu-id="ed7be-133">The nature of the cluster, its size, the number of services deployed, and the volume of traffic within the cluster network.</span></span>
- <span data-ttu-id="ed7be-134">Ağı dağıtma ve yönetme kolaylığı ve hizmetlerle kullanma.</span><span class="sxs-lookup"><span data-stu-id="ed7be-134">Ease of deploying and managing the mesh and using it with services.</span></span>

<span data-ttu-id="ed7be-135">Her hizmet ağı hakkında daha fazla bilgiyi ilgili web sitelerinden bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed7be-135">More information on each service mesh is available from their respective websites.</span></span>

- [<span data-ttu-id="ed7be-136">**Istio** -istio.io</span><span class="sxs-lookup"><span data-stu-id="ed7be-136">**Istio** - istio.io</span></span>](https://istio.io)
- [<span data-ttu-id="ed7be-137">**Linkerd** -linkerd.io</span><span class="sxs-lookup"><span data-stu-id="ed7be-137">**Linkerd** - linkerd.io</span></span>](https://linkerd.io)
- [<span data-ttu-id="ed7be-138">**Tüketil** -Consul.io/mesh.html</span><span class="sxs-lookup"><span data-stu-id="ed7be-138">**Consul** - consul.io/mesh.html</span></span>](https://consul.io/mesh.html)

## <a name="example-add-linkerd-to-a-deployment"></a><span data-ttu-id="ed7be-139">Örnek: bir dağıtıma Linkerd ekleme</span><span class="sxs-lookup"><span data-stu-id="ed7be-139">Example: add Linkerd to a deployment</span></span>

<span data-ttu-id="ed7be-140">Bu örnekte, [önceki bölümde](kubernetes.md) *StockKube* uygulamasıyla linkerd hizmet ağı 'nı nasıl kullanacağınızı öğreneceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ed7be-140">In this example, you'll learn how to use the Linkerd service mesh with the *StockKube* application from [the previous section](kubernetes.md).</span></span>
<span data-ttu-id="ed7be-141">Bu örneği izlemek için, [Linkerd CLI 'yı yüklemeniz](https://linkerd.io/2/getting-started/#step-1-install-the-cli)gerekir.</span><span class="sxs-lookup"><span data-stu-id="ed7be-141">To follow this example, you'll need to [install the Linkerd CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli).</span></span> <span data-ttu-id="ed7be-142">Windows ikili dosyaları GitHub yayınları bölümünden indirilebilir; uç sürümlerden birini değil en son **kararlı** yayını kullandığınızdan emin olun.</span><span class="sxs-lookup"><span data-stu-id="ed7be-142">Windows binaries can be downloaded from the GitHub releases section; make sure to use the most recent **stable** release and not one of the edge releases.</span></span>

<span data-ttu-id="ed7be-143">Linkerd CLı yüklü olduğunda, Kubernetes kümenize Linkerd bileşenlerini yüklemek için [Linkerd Web sitesinde*kullanmaya* başlama yönergeleri ' ni izleyin.</span><span class="sxs-lookup"><span data-stu-id="ed7be-143">With the Linkerd CLI installed, follow the [*Getting Started* instructions on the Linkerd web site] to install the Linkerd components on your Kubernetes cluster.</span></span> <span data-ttu-id="ed7be-144">Yönergeler doğrudan ileriye doğru ve yükleme, yerel bir Kubernetes örneği üzerinde yalnızca birkaç dakika sürer.</span><span class="sxs-lookup"><span data-stu-id="ed7be-144">The instructions are straight-forward and installation should only take a couple of minutes on a local Kubernetes instance.</span></span>

### <a name="add-linkerd-to-kubernetes-deployments"></a><span data-ttu-id="ed7be-145">Kubernetes dağıtımlarını Linkerd 'e ekleme</span><span class="sxs-lookup"><span data-stu-id="ed7be-145">Add Linkerd to Kubernetes deployments</span></span>

<span data-ttu-id="ed7be-146">Linkerd CLı, Kubernetes dosyalarına gerekli bölümleri ve özellikleri eklemek için bir `inject` komutu sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed7be-146">The Linkerd CLI provides an `inject` command to add the necessary sections and properties to Kubernetes files.</span></span> <span data-ttu-id="ed7be-147">Komutu çalıştırabilir ve çıktıyı yeni bir dosyaya yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed7be-147">You can run the command and write the output to a new file.</span></span>

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

<span data-ttu-id="ed7be-148">Yapılan değişiklikleri görmek için yeni dosyaları inceleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ed7be-148">You can inspect the new files to see what changes have been made.</span></span> <span data-ttu-id="ed7be-149">Dağıtım nesneleri için, Linkerd 'nin oluşturulduğu sırada Pod 'a bir sepet ara sunucu kapsayıcısı eklemesine söylemek için bir meta veri ek açıklaması eklenir.</span><span class="sxs-lookup"><span data-stu-id="ed7be-149">For Deployment objects, a metadata annotation is added to tell Linkerd to inject a sidecar proxy container into the Pod when it's created.</span></span>

<span data-ttu-id="ed7be-150">Ayrıca, `linkerd inject` komutunun çıkışını doğrudan `kubectl` için boru yapmak mümkündür.</span><span class="sxs-lookup"><span data-stu-id="ed7be-150">It's also possible to pipe the output of the `linkerd inject` command to `kubectl` directly.</span></span> <span data-ttu-id="ed7be-151">Aşağıdaki komutlar PowerShell veya herhangi bir Linux kabuğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="ed7be-151">The following commands will work in PowerShell or any Linux shell.</span></span>

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a><span data-ttu-id="ed7be-152">Linkerd panosundaki Hizmetleri inceleyin</span><span class="sxs-lookup"><span data-stu-id="ed7be-152">Inspect services in the Linkerd dashboard</span></span>

<span data-ttu-id="ed7be-153">`linkerd` CLı kullanarak Linkerd panosunu başlatın.</span><span class="sxs-lookup"><span data-stu-id="ed7be-153">Launch the Linkerd dashboard using the `linkerd` CLI.</span></span>

```console
linkerd dashboard
```

<span data-ttu-id="ed7be-154">Pano, ağa bağlı tüm hizmetler hakkında ayrıntılı bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ed7be-154">The dashboard provides detailed information about all services that are connected to the mesh.</span></span>

![StockKube uygulamalarını gösteren linkerd panosu](media/service-mesh/linkerd-screenshot.png)

<span data-ttu-id="ed7be-156">Aşağıdaki örnekte gösterildiği gibi StockData gRPC hizmetinin çoğaltmaların sayısını artırabilir ve tarayıcıdaki StockWeb sayfasını yenilediğinizde, sunucu sütununda isteklerin tüm kullanılabilir örneklerle sunulduğunu belirten bir kimlik karışımı görmeniz gerekir. .</span><span class="sxs-lookup"><span data-stu-id="ed7be-156">If you increase the number of replicas of the StockData gRPC service as shown in the following example, and refresh the StockWeb page in the browser, you should see a mix of IDs in the Server column, indicating that requests are being served by all the available instances.</span></span>

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
><span data-ttu-id="ed7be-157">[Önceki](kubernetes.md)
>[İleri](load-balancing.md)</span><span class="sxs-lookup"><span data-stu-id="ed7be-157">[Previous](kubernetes.md)
[Next](load-balancing.md)</span></span>
