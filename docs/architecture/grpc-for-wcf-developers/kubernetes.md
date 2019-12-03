---
title: WCF geliştiricileri için Kubernetes-gRPC
description: Bir Kubernetes kümesinde ASP.NET Core gRPC hizmetlerini çalıştırma.
ms.date: 09/02/2019
ms.openlocfilehash: 22271343f8f0d0454469b2f35e717f5b7e939294
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711283"
---
# <a name="kubernetes"></a>Kubernetes

Kapsayıcıları Docker konaklarında el ile çalıştırmak mümkün olsa da, güvenilir üretim sistemleri için bir kümedeki çeşitli sunucularda çalışan birden çok örneği yönetmek üzere kapsayıcı düzenleme altyapısını kullanmak daha iyidir. Kubernetes, Docker Sısınma ve Apache Mesos dahil çeşitli kapsayıcı düzenleme altyapıları mevcuttur. Ancak bu altyapılardan, Kubernetes, en yaygın olarak kullanıldığından, bu bölümün odağı olacaktır.

Kubernetes aşağıdaki işlevleri içerir:

- **Zamanlama** , bir küme içindeki birden çok düğümdeki kapsayıcıları çalıştırır, kullanılabilir kaynağın dengeli kullanımını sağlar, kesintiler varsa kapsayıcıları çalışır durumda tutun ve görüntülerin yeni sürümlerine veya yeni yapılandırmalara yapılan güncelleştirmeleri idare edin.
- **Sistem durumu denetimleri** devam eden hizmeti sağlamak için kapsayıcıları izler.
- **DNS & hizmeti bulma** , bir küme içindeki hizmetler arasında yönlendirmeyi işler.
- Giriş, seçili Hizmetleri **dışarıdan gösterir ve** genellikle bu hizmetlerin örneklerinde yük dengelemesi sağlar.
- **Kaynak yönetimi** , kapsayıcılara depolama gibi dış kaynakları ekler.

Bu bölümde, bir ASP.NET Core gRPC hizmetinin ve hizmeti bir Kubernetes kümesine tüketen bir Web sitesinin nasıl dağıtılacağı ayrıntılandıralınacaktır. Kullanılan örnek uygulama, GitHub 'daki [DotNet-Architecture/GRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) deposunda bulunur.

## <a name="kubernetes-terminology"></a>Kubernetes terminolojisi

Kubernetes *istenen durum yapılandırmasını*KULLANıR: API, *pods*, *dağıtımlar*ve *Hizmetler*gibi nesneleri belirtmek için kullanılır ve *Denetim düzlemi* , bir *kümedeki*tüm *düğümlerde* istenen durumu uygulama konusunda dikkatli olur. Kubernetes kümesinde, programlama yoluyla veya `kubectl` komut satırı aracını kullanarak iletişim kurabileceğiniz *KUBERNETES API*'sini çalıştıran bir *ana* düğüm bulunur. `kubectl`, komut satırı bağımsız değişkenleri aracılığıyla nesne oluşturabilir ve yönetebilir, ancak Kubernetes nesneleri için bildirim verilerini içeren YAML dosyalarıyla en iyi şekilde çalışabilir.

### <a name="kubernetes-yaml-files"></a>Kubernetes YAML dosyaları

Her Kubernetes YAML dosyası en az üç en üst düzey özelliğe sahip olacaktır:

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

`apiVersion` özelliği, dosyanın hangi sürümü (ve hangi API) hedeflenmiştir belirtmek için kullanılır. `kind` özelliği, YAML 'nin gösterdiği nesne türünü belirtir. `metadata` özelliği `name`, `namespace`ve `labels`gibi nesne özelliklerini içerir.

Çoğu Kubernetes YAML dosyalarında, nesneyi oluşturmak için gereken kaynakları ve yapılandırmayı açıklayan bir `spec` bölümü de olur.

### <a name="pods"></a>Pod

Pods, Kubernetes içindeki temel yürütme birimleridir. Birden çok kapsayıcıyı çalıştırabilir, ancak aynı zamanda tek kapsayıcıları çalıştırmak için de kullanılır. Pod, kapsayıcılar için gereken tüm depolama kaynaklarını ve ağ IP adresini de içerir.

### <a name="services"></a>Hizmetler

Hizmetler, pods 'leri (veya pods kümelerini) tanımlayan meta nesnelerdir ve küme DNS hizmetini kullanarak bir hizmet adını Pod IP adresleri kümesine eşleme gibi küme içinde erişmek için bir yol sağlar.

### <a name="deployments"></a>Dağıtımlar

Dağıtımlar, pods için *istenen durum* nesneleridir. El ile bir pod oluşturursanız, bu, sonlandırıldığında yeniden başlatılmaz. Dağıtımlar, kümeye olan ve bu yığınların kaç kopyasının mevcut zamanda çalışıyor olduğunu bildirmek için kullanılır.

### <a name="other-objects"></a>Diğer nesneler

Pods, hizmetler ve dağıtımlar en temel nesne türlerinden yalnızca üçüne sahiptir. Kubernetes kümeleri tarafından yönetilen düzinelerce daha fazla nesne türü vardır. Daha fazla bilgi için bkz. [Kubernetes kavramları](https://kubernetes.io/docs/concepts/) belgeleri.

### <a name="namespaces"></a>{1&gt;Ad alanları&lt;1}

Kubernetes kümeleri yüzlerce veya binlerce düğüme ölçeklendirilmesi ve benzer sayıda hizmeti çalıştırmak için tasarlanmıştır. Nesne adlarıyla çakışıyor önlemek için ad alanları, nesneleri daha büyük uygulamaların bir parçası olarak gruplamak için kullanılır. Kubernetes 'in kendi hizmetleri bir `default` ad alanında çalışır. Varsayılan nesneler veya kümedeki diğer kiracılar ile ilgili potansiyel çakışıyor kaçınmak için tüm Kullanıcı nesnelerinin kendi ad alanlarında oluşturulması gerekir.

## <a name="get-started-with-kubernetes"></a>Kubernetes 'i kullanmaya başlama

Windows için Docker Desktop veya Mac için Docker Desktop çalıştırıyorsanız, Kubernetes zaten kullanılabilir. Bunu, **Ayarlar** penceresinin **Kubernetes** bölümünde etkinleştirmeniz yeterlidir:

![Docker Desktop 'ta Kubernetes 'i etkinleştirme](media/kubernetes/enable-kubernetes-docker-desktop.png)

Linux 'ta yerel bir Kubernetes kümesi çalıştırmak için, [minikube](https://github.com/kubernetes/minikube)veya [MicroK8s](https://microk8s.io/) ' yi [düşünün.](https://snapcraft.io/)

Kümenizin çalıştığını ve erişilebilir olduğunu doğrulamak için `kubectl version` komutunu çalıştırın:

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

Bu örnekte, hem `kubectl` CLı hem de Kubernetes sunucusu 1.14.6 sürümünü çalıştırıyor. Her bir `kubectl` sürümünün sunucunun önceki ve sonraki sürümünü desteklemesi gerekir, bu nedenle `kubectl` 1,14 sunucu sürümleri 1,13 ve 1,15 ile çalışmalıdır.

## <a name="run-services-on-kubernetes"></a>Kubernetes üzerinde hizmetleri çalıştırma

Örnek uygulamanın, üç YAML dosyası içeren bir `kube` dizini vardır. `namespace.yml` dosyası özel bir ad alanı bildirir: `stocks`. `stockdata.yml` dosyası, gRPC uygulaması için dağıtımı ve hizmeti bildirir ve `stockweb.yml` dosyası, gRPC hizmetini kullanan bir ASP.NET Core 3,0 MVC web uygulaması için dağıtımı ve hizmeti bildirir.

`kubectl`bir `YAML` dosyası kullanmak için `apply -f` komutunu çalıştırın:

```console
kubectl apply -f object.yml
```

`apply` komutu, YAML dosyasının geçerliliğini denetler ve API 'den alınan tüm hataları görüntüler, ancak bu işlem biraz zaman alabilir çünkü dosyada belirtilen tüm nesneler oluşturuluncaya kadar beklemez. Kümedeki nesne oluşturmayı denetlemek için ilgili nesne türleriyle birlikte `kubectl get` komutunu kullanın.

### <a name="the-namespace-declaration"></a>Ad alanı bildirimi

Ad alanı bildirimi basittir ve yalnızca bir `name`atanmasını gerektirir:

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

`namespace.yml` dosyasını uygulamak ve ad alanının başarıyla oluşturulduğunu onaylamak için `kubectl` kullanın:

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a>StockData uygulaması

`stockdata.yml` dosyası iki nesne bildirir: bir dağıtım ve bir hizmet.

#### <a name="the-stockdata-deployment"></a>StockData dağıtımı

YAML dosyasının Dağıtım bölümü, gereken kopyaların sayısı ve dağıtım tarafından oluşturulup yönetilecek Pod nesnelerinin bir `template` dahil olmak üzere dağıtımın kendisi için `spec` sağlar. Dağıtım nesnelerinin, ana Kubernetes API 'SI yerine `apiVersion`belirtilen `apps` API 'SI tarafından yönetildiğini unutmayın.

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
  replicas: 1
  template:
    metadata:
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

`spec.selector` özelliği, çalışan pods 'yi dağıtıma eşleştirmek için kullanılır. Pod 'un `metadata.labels` özelliği `matchLabels` özelliğiyle eşleşmelidir veya API çağrısı başarısız olur.

`template.spec` bölümü kapsayıcıyı çalıştırılacak şekilde bildirir. Docker Desktop tarafından sağlandıkları gibi yerel bir Kubernetes kümesiyle çalışırken, bir sürüm etiketi olduğu sürece yerel olarak oluşturulan görüntüleri belirtebilirsiniz.

> [!IMPORTANT]
> Varsayılan olarak, Kubernetes her zaman yeni bir görüntü çekmeyi ve çekmeye çalışır. Görüntüyü bilinen depolarından hiçbirinde bulamazsa Pod oluşturma işlemi başarısız olur. Yerel görüntülerle çalışmak için `imagePullPolicy` `Never`olarak ayarlayın.

`ports` özelliği, pod üzerinde hangi kapsayıcı bağlantı noktalarının yayımlanacağını belirtir. `stockservice` görüntüsü, hizmeti standart HTTP bağlantı noktasında çalıştırır, bu nedenle bağlantı noktası 80 yayımlandı.

`resources` bölümü, Pod içinde çalışan kapsayıcıya kaynak sınırları uygular. Tek bir pod 'ın bir düğümdeki tüm kullanılabilir CPU veya bellek tüketmesini engellemesi nedeniyle bu iyi bir uygulamadır.

> [!NOTE]
> ASP.NET Core 3,0, en iyi duruma getirilmiştir ve kaynak sınırlı kapsayıcılarda çalışacak şekilde ayarlanmıştır. `dotnet/core/aspnet` Docker görüntüsü bir ortam değişkenini ayarlayarak, `dotnet` çalışma zamanına bir kapsayıcıda olduğunu söyler.

#### <a name="the-stockdata-service"></a>StockData hizmeti

YAML dosyasının hizmet bölümü, küme içindeki yığınlara erişim sağlayan hizmeti bildirir.

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

Hizmet `spec`, bir etiketi `run: stockdata`olan pods 'yi aramak için, bu örnekte, çalışan `Pods`eşleştirmek için `selector` özelliğini kullanır. Eşleşen FID 'ler üzerinde belirtilen `port`, adlandırılmış hizmet tarafından yayımlanır. `stocks` ad alanında çalışan diğer pods 'Ler, bu hizmette HTTP 'ye, adres olarak `http://stockdata` kullanarak erişebilir. Diğer ad alanlarında çalışan pods `http://stockdata.stocks` ana bilgisayar adını kullanabilir. [Ağ ilkelerini](https://kubernetes.io/docs/concepts/services-networking/network-policies/)kullanarak, çapraz ad alanı hizmet erişimini denetleyebilirsiniz.

#### <a name="deploy-the-stockdata-application"></a>StockData uygulamasını dağıtma

`stockdata.yml` dosyasını uygulamak ve dağıtım ve hizmetin oluşturulduğunu onaylamak için `kubectl` kullanın:

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a>StockWeb uygulaması

`stockweb.yml` dosyası, MVC uygulaması için dağıtımı ve hizmeti bildirir.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a>Ortam değişkenleri

Dağıtım nesnesinin `env` bölümü, `stockweb:1.0.0` görüntülerini çalıştıran kapsayıcıda ayarlanacak ortam değişkenlerini belirtir.

**`StockData__Address`** ortam değişkeni, EnvironmentVariables yapılandırma sağlayıcısı için teşekkürler `StockData:Address` yapılandırma ayarıyla eşlenir. Bu ayar, adlar arasında ayrı bölümlere iki alt çizgi kullanır. Adres, aynı Kubernetes ad alanında çalışan `stockdata` hizmetinin hizmet adını kullanır.

**`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** ortam değişkeni <xref:System.Net.Http.HttpClient>IÇIN şifrelenmemiş HTTP/2 bağlantılarına izin veren bir <xref:System.AppContext> anahtarı ayarlar. Bu ortam değişkeni, burada gösterildiği gibi, kodda anahtarı ayarlamayla aynı şeyi yapar:

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Anahtar için bir ortam değişkeni kullanıyorsanız, bağlamı uygulamanın çalıştığı bağlama göre kolayca değiştirebilirsiniz.

#### <a name="service-types"></a>Hizmet türleri

`type: NodePort` özelliği, Web uygulamasını küme dışından erişilebilir hale getirmek için kullanılır. Bu özellik türü, Kubernetes 'in hizmette bağlantı noktası 80 ' i kümenin dış ağ yuvaları üzerinde rastgele bir bağlantı noktasına yayımlamasına neden olur. Atanan bağlantı noktasını `kubectl get service` komutunu kullanarak bulabilirsiniz.

`stockdata` hizmetine küme dışından erişilememelidir, bu nedenle `ClusterIP`varsayılan türünü kullanır.

Üretim sistemleri, ortak uygulamaları dış tüketicilere sunmak için büyük olasılıkla Tümleşik yük dengeleyici kullanır. Bu şekilde sunulan hizmetler `LoadBalancer` türünü kullanmalıdır.

Hizmet türleri hakkında daha fazla bilgi için bkz. [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) belgeleri.

#### <a name="deploy-the-stockweb-application"></a>StockWeb uygulamasını dağıtma

`stockweb.yml` dosyasını uygulamak ve dağıtım ve hizmetin oluşturulduğunu onaylamak için `kubectl` kullanın:

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

`get service` komutunun çıktısı, HTTP bağlantı noktasının dış ağdaki 32564 numaralı bağlantı noktasına yayımlandığını gösterir. Docker Desktop için bu, localhost olur. `http://localhost:32564`göz atarak uygulamaya erişebilirsiniz.

### <a name="test-the-application"></a>Uygulamayı test etme

StockWeb uygulaması, basit bir istek-yanıt hizmetinden alınan NASDAQ hisse senetleri listesini görüntüler. Bu gösterim için her satırda Ayrıca döndürülen hizmet örneğinin benzersiz KIMLIĞI gösterilir.

![StockWeb ekran görüntüsü](media/kubernetes/stockweb-screenshot.png)

`stockdata` hizmetinin çoğaltmalarının sayısı artdıysa, **sunucu** değerinin satırdan satıra değiştirilmesini bekleyebilir, ancak aslında tüm 100 kayıtları aynı örnekten döndürülür. Sayfayı birkaç saniyede bir kez yenilerseniz, sunucu KIMLIĞI aynı kalır. Bunun nedeni nedir? Burada çalmak için iki etken vardır.

İlk olarak, Kubernetes hizmeti bulma sistemi varsayılan olarak hepsini bir kez deneme yük dengelemeyi kullanır. DNS sunucusu ilk kez sorgulandığında, hizmet için ilk eşleşen IP adresini döndürür. Bir sonraki sefer, listenin bir sonraki IP adresini döndürür ve sonuna kadar bu şekilde devam eder. Bu noktada başlangıç noktasına geri döngü yapılır.

İkincisi, StockWeb uygulamasının gRPC istemcisi için kullanılan `HttpClient`, [HttpClientFactory ASP.NET Core](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)tarafından oluşturulup yönetilir ve bu istemcinin tek bir örneği, sayfaya yapılan her çağrı için kullanılır. İstemci yalnızca bir DNS araması yapar, bu nedenle tüm istekler aynı IP adresine yönlendirilir. `HttpClientHandler` performans nedeniyle önbelleğe alındığından, önbelleğe alınan DNS girişinin süresi dolana veya işleyici örneği bazı nedenlerle atılana kadar, hızlı bir şekilde art arda birden çok istek aynı IP *adresini kullanacaktır.*

Sonuç, varsayılan olarak bir gRPC hizmetine yapılan isteklerin kümedeki hizmetin tüm örneklerine dengelenemez. Farklı tüketiciler farklı örnekler kullanacaktır, ancak isteklerin iyi bir şekilde dağıtılmasını veya kaynakların dengeli kullanımını garanti etmez.

Sonraki bölümde, [hizmet kafesleri](service-mesh.md)bu sorunu ele alacak.

>[!div class="step-by-step"]
>[Önceki](docker.md)
>[İleri](service-mesh.md)
