---
title: WCF geliştiricileri için Kubernetes-gRPC
description: Bir Kubernetes kümesinde ASP.NET Core gRPC hizmetlerini çalıştırma.
ms.date: 12/15/2020
ms.openlocfilehash: 0b457d6fa982b5f5b983194d4aedbff0eb782f36
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938070"
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

Kubernetes *istenen durum yapılandırmasını* KULLANıR: API, *pods*, *dağıtımlar* ve *Hizmetler* gibi nesneleri belirtmek için kullanılır ve *Denetim düzlemi* , bir *kümedeki* tüm *düğümlerde* istenen durumu uygulama konusunda dikkatli olur. Kubernetes kümesinde, programlama yoluyla veya komut satırı aracını kullanarak iletişim kurabileceğiniz *KUBERNETES API*'sini çalıştıran bir *ana* düğüm bulunur `kubectl` . `kubectl` komut satırı bağımsız değişkenleri aracılığıyla nesne oluşturabilir ve yönetebilir, ancak Kubernetes nesneleri için bildirim verilerini içeren YAML dosyalarıyla en iyi şekilde çalışabilir.

### <a name="kubernetes-yaml-files"></a>Kubernetes YAML dosyaları

Her Kubernetes YAML dosyası en az üç en üst düzey özelliğe sahip olacaktır:

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

`apiVersion`Özelliği, dosyanın hangi sürümü (ve HANGI API) hedeflenmiştir belirtmek için kullanılır. `kind`Özelliği, YAML 'nin gösterdiği nesne türünü belirtir. `metadata`Özelliği,, ve gibi nesne özelliklerini içerir `name` `namespace` `labels` .

Çoğu Kubernetes YAML dosyalarında, `spec` nesneyi oluşturmak için gereken kaynakları ve yapılandırmayı açıklayan bir bölüm de olur.

### <a name="pods"></a>Pod

Pods, Kubernetes içindeki temel yürütme birimleridir. Birden çok kapsayıcıyı çalıştırabilir, ancak aynı zamanda tek kapsayıcıları çalıştırmak için de kullanılır. Pod, kapsayıcılar için gereken tüm depolama kaynaklarını ve ağ IP adresini de içerir.

### <a name="services"></a>Hizmetler

Hizmetler, pods 'leri (veya pods kümelerini) tanımlayan meta nesnelerdir ve küme DNS hizmetini kullanarak bir hizmet adını Pod IP adresleri kümesine eşleme gibi küme içinde erişmek için bir yol sağlar.

### <a name="deployments"></a>Dağıtımlar

Dağıtımlar, pods için *istenen durum* nesneleridir. El ile bir pod oluşturursanız, bu, sonlandırıldığında yeniden başlatılmaz. Dağıtımlar, kümeye olan ve bu yığınların kaç kopyasının mevcut zamanda çalışıyor olduğunu bildirmek için kullanılır.

### <a name="other-objects"></a>Diğer nesneler

Pods, hizmetler ve dağıtımlar en temel nesne türlerinden yalnızca üçüne sahiptir. Kubernetes kümeleri tarafından yönetilen düzinelerce daha fazla nesne türü vardır. Daha fazla bilgi için bkz. [Kubernetes kavramları](https://kubernetes.io/docs/concepts/) belgeleri.

### <a name="namespaces"></a>Ad alanları

Kubernetes kümeleri yüzlerce veya binlerce düğüme ölçeklendirilmesi ve benzer sayıda hizmeti çalıştırmak için tasarlanmıştır. Nesne adlarıyla çakışıyor önlemek için ad alanları, nesneleri daha büyük uygulamaların bir parçası olarak gruplamak için kullanılır. Kubernetes 'in kendi hizmetleri bir `default` ad alanında çalışır. Varsayılan nesneler veya kümedeki diğer kiracılar ile ilgili potansiyel çakışıyor kaçınmak için tüm Kullanıcı nesnelerinin kendi ad alanlarında oluşturulması gerekir.

## <a name="get-started-with-kubernetes"></a>Kubernetes’i kullanmaya başlama

Windows için Docker Desktop veya Mac için Docker Desktop çalıştırıyorsanız, Kubernetes zaten kullanılabilir. Bunu, **Ayarlar** penceresinin **Kubernetes** bölümünde etkinleştirmeniz yeterlidir:

![Docker Desktop 'ta Kubernetes 'i etkinleştirme](media/kubernetes/enable-kubernetes-docker-desktop-v2.png)

Linux 'ta yerel bir Kubernetes kümesi çalıştırmak için, [minikube](https://github.com/kubernetes/minikube)veya [MicroK8s](https://microk8s.io/) ' yi [düşünün.](https://snapcraft.io/)

Kümenizin çalıştığını ve erişilebilir olduğunu doğrulamak için şu `kubectl version` komutu çalıştırın:

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:50:19Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:41:49Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"linux/amd64"}
```

Bu örnekte, hem `kubectl` CLI hem de Kubernetes sunucusu 1.14.6 sürümünü çalıştırıyor. Her sürümünün, `kubectl` sunucunun önceki ve sonraki sürümünü desteklemesi gerekir, bu nedenle `kubectl` 1,14, sunucu sürümleri 1,13 ve 1,15 ile birlikte çalışmalıdır.

## <a name="run-services-on-kubernetes"></a>Kubernetes üzerinde hizmetleri çalıştırma

Örnek uygulamanın, `kube` üç YAML dosyası içeren bir dizini vardır. `namespace.yml`Dosya özel bir ad alanı bildirir: `stocks` . `stockdata.yml`Dosya, GRPC uygulaması Için dağıtımı ve hizmeti bildirir ve `stockweb.yml` Dosya, GRPC hizmetini tüketen ASP.NET Core 5,0 MVC web uygulaması için dağıtım ve hizmeti bildirir.

İle bir dosya kullanmak için şu `YAML` `kubectl` komutu çalıştırın `apply -f` :

```console
kubectl apply -f object.yml
```

`apply`Komut, YAML dosyasının geçerliliğini denetler ve API 'den alınan hataları görüntüler, ancak bu adım biraz zaman alabilir çünkü dosyada belirtilen tüm nesneler oluşturuluncaya kadar beklemez. `kubectl get`Kümeden nesne oluşturmayı denetlemek için ilgili nesne türleriyle komutunu kullanın.

### <a name="the-namespace-declaration"></a>Ad alanı bildirimi

Ad alanı bildirimi basittir ve yalnızca şunu atanmasını gerektirir `name` :

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

`kubectl` `namespace.yml` Dosyayı uygulamak ve ad alanının başarıyla oluşturulduğunu onaylamak için kullanın:

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a>StockData uygulaması

`stockdata.yml`Dosya iki nesne bildirir: bir dağıtım ve bir hizmet.

#### <a name="the-stockdata-deployment"></a>StockData dağıtımı

YAML dosyasının Dağıtım bölümü, `spec` gereken çoğaltma sayısı ve `template` Dağıtım tarafından oluşturulup yönetilecek Pod nesneleri için bir dağıtımı sağlar. Dağıtım nesnelerinin, `apps` `apiVersion` ana Kubernetes API 'si yerine ' de belirtildiği gibi API tarafından yönetildiğini unutmayın.

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

`spec.selector`Özelliği, çalışan pods 'Yi dağıtıma eşleştirmek için kullanılır. Pod 'un `metadata.labels` özelliği özelliği ile eşleşmelidir, `matchLabels` ya da API çağrısı başarısız olur.

`template.spec`Bölüm, kapsayıcıyı çalıştırılacak şekilde bildirir. Docker Desktop tarafından sağlandıkları gibi yerel bir Kubernetes kümesiyle çalışırken, bir sürüm etiketi olduğu sürece yerel olarak oluşturulan görüntüleri belirtebilirsiniz.

> [!IMPORTANT]
> Varsayılan olarak, Kubernetes her zaman yeni bir görüntü çekmeyi ve çekmeye çalışır. Görüntüyü bilinen depolarından hiçbirinde bulamazsa Pod oluşturma işlemi başarısız olur. Yerel görüntülerle çalışmak için öğesini `imagePullPolicy` olarak ayarlayın `Never` .

`ports`Özelliği, pod üzerinde hangi kapsayıcı bağlantı noktalarının yayımlanacağını belirtir. `stockservice`Görüntü, hizmeti standart http bağlantı noktasında çalıştırır, bu nedenle bağlantı noktası 80 yayımlandı.

`resources`Bölüm, Pod içinde çalışan kapsayıcıya kaynak sınırları uygular. Tek bir pod 'ın bir düğümdeki tüm kullanılabilir CPU veya bellek tüketmesini engellemesi nedeniyle bu iyi bir uygulamadır.

> [!NOTE]
> ASP.NET Core 5,0, en iyi duruma getirilmiştir ve kaynak sınırlı kapsayıcılarda çalışacak şekilde ayarlanmıştır. `dotnet/core/aspnet`Docker görüntüsü bir ortam değişkenini ayarlayarak `dotnet` çalışma zamanına bir kapsayıcıda olduğunu söyler.

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

Hizmet, `spec` `selector` `Pods` bir etiketi olan bir pods 'yi aramak için, bu durumda, çalışmayı eşleştirmek için özelliğini kullanır `run: stockdata` . `port`Eşleşen FID 'ler üzerinde belirtilen, adlandırılmış hizmet tarafından yayımlanır. Ad alanında çalışan diğer yığınların `stocks` adresi olarak kullanarak bu HIZMETTE http 'ye erişimi olabilir `http://stockdata` . Diğer ad alanlarında çalışan pods `http://stockdata.stocks` ana bilgisayar adını kullanabilir. [Ağ ilkelerini](https://kubernetes.io/docs/concepts/services-networking/network-policies/)kullanarak, çapraz ad alanı hizmet erişimini denetleyebilirsiniz.

#### <a name="deploy-the-stockdata-application"></a>StockData uygulamasını dağıtma

`kubectl` `stockdata.yml` Dosyayı uygulamak ve dağıtım ve hizmetin oluşturulduğunu onaylamak için kullanın:

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

`stockweb.yml`Dosya, MVC uygulaması Için dağıtımı ve hizmeti bildirir.

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

`env`Dağıtım nesnesinin bölümü, görüntüleri çalıştıran kapsayıcıda ayarlanacak ortam değişkenlerini belirtir `stockweb:1.0.0` .

**`StockData__Address`** Ortam değişkeni, `StockData:Address` EnvironmentVariables yapılandırma sağlayıcısı için teşekkürler yapılandırma ayarıyla eşlenir. Bu ayar, adlar arasında ayrı bölümlere iki alt çizgi kullanır. Adres, `stockdata` aynı Kubernetes ad alanında çalışan hizmetin hizmet adını kullanır.

**`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** Ortam değişkeni, <xref:System.AppContext> IÇIN şifrelenmemiş HTTP/2 bağlantılarına izin veren bir anahtar ayarlar <xref:System.Net.Http.HttpClient> . Bu ortam değişkeni, burada gösterildiği gibi, kodda anahtarı ayarlamayla aynı şeyi yapar:

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

Anahtar için bir ortam değişkeni kullanıyorsanız, bağlamı uygulamanın çalıştığı bağlama göre kolayca değiştirebilirsiniz.

#### <a name="service-types"></a>Hizmet türleri

`type: NodePort`Özelliği, Web uygulamasını küme dışından erişilebilir hale getirmek için kullanılır. Bu özellik türü, Kubernetes 'in hizmette bağlantı noktası 80 ' i kümenin dış ağ yuvaları üzerinde rastgele bir bağlantı noktasına yayımlamasına neden olur. Atanan bağlantı noktasını komutunu kullanarak bulabilirsiniz `kubectl get service` .

`stockdata`Hizmet, küme dışından erişilememelidir, bu nedenle varsayılan türünü kullanır `ClusterIP` .

Üretim sistemleri, ortak uygulamaları dış tüketicilere sunmak için büyük olasılıkla Tümleşik yük dengeleyici kullanır. Bu şekilde sunulan hizmetler `LoadBalancer` türü kullanmalıdır.

Hizmet türleri hakkında daha fazla bilgi için bkz. [Kubernetes Publishing Services](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) belgeleri.

#### <a name="deploy-the-stockweb-application"></a>StockWeb uygulamasını dağıtma

`kubectl` `stockweb.yml` Dosyayı uygulamak ve dağıtım ve hizmetin oluşturulduğunu onaylamak için kullanın:

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

Komutun çıktısı, `get service` http bağlantı noktasının dış ağdaki bağlantı noktasında yayımlandığını gösterir `32564` . Docker Desktop için bu IP adresi localhost olacaktır. Uygulamasına göz atarak uygulamaya erişebilirsiniz `http://localhost:32564` .

### <a name="test-the-application"></a>Uygulamayı test edin

StockWeb uygulaması, basit bir istek-yanıt hizmetinden alınan NASDAQ hisse senetleri listesini görüntüler. Bu gösterim için her satırda Ayrıca döndürülen hizmet örneğinin benzersiz KIMLIĞI gösterilir.

![StockWeb ekran görüntüsü](media/kubernetes/stockweb-screenshot.png)

Hizmetin çoğaltma sayısı `stockdata` artdıysa, **sunucu** değerinin satırdan satıra değiştirilmesini bekleyebilir, ancak aslında tüm 100 kayıtları her zaman aynı örnekten döndürülür. Sayfayı birkaç saniyede bir kez yenilerseniz, sunucu KIMLIĞI aynı kalır. Bunun nedeni nedir? Burada çalmak için iki etken vardır.

İlk olarak, Kubernetes hizmeti bulma sistemi varsayılan olarak hepsini bir kez deneme yük dengelemeyi kullanır. DNS sunucusu ilk kez sorgulandığında, hizmet için ilk eşleşen IP adresini döndürür. Bir sonraki sefer, listenin bir sonraki IP adresini döndürür ve sonuna kadar bu şekilde devam eder. Bu noktada başlangıç noktasına geri döngü yapılır.

İkincisi, `HttpClient` StockWeb uygulamasının gRPC istemcisi için kullanılan, [HttpClientFactory ASP.NET Core](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)tarafından oluşturulup yönetilir ve bu istemcinin tek bir örneği, sayfaya yapılan her çağrı için kullanılır. İstemci yalnızca bir DNS araması yapar, bu nedenle tüm istekler aynı IP adresine yönlendirilir. Ve, `HttpClientHandler` performans nedenleriyle önbelleğe alındığından, önbelleğe ALıNAN DNS girişinin süresi dolana veya işleyici örneği bazı nedenlerle atılana kadar, *her* bir hızla art arda birden çok istek aynı IP adresini kullanacaktır.

Sonuç, varsayılan olarak bir gRPC hizmetine yapılan isteklerin kümedeki hizmetin tüm örneklerine dengelenemez. Farklı tüketiciler farklı örnekler kullanacaktır, ancak isteklerin iyi bir şekilde dağıtılmasını veya kaynakların dengeli kullanımını garanti etmez.

Sonraki bölümde, [hizmet kafesleri](service-mesh.md)bu sorunu ele alacak.

>[!div class="step-by-step"]
>[Önceki](docker.md) 
> [Sonraki](service-mesh.md)
