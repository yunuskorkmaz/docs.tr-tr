---
title: Hizmet kafesleri-WCF geliştiricileri için gRPC
description: Bir Kubernetes kümesinde gRPC hizmetlerine istekleri yönlendirmek ve dengelemek için bir hizmet ağı kullanma.
ms.date: 12/15/2020
ms.openlocfilehash: a1c72a4facf1c133af912bbee242328653a051b6
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938136"
---
# <a name="service-meshes"></a>Hizmet ağları

Hizmet ağı, bir ağ içindeki yönlendirme hizmeti isteklerinin denetimini alan bir altyapı bileşenidir. Hizmet kafesleri, bir Kubernetes kümesi içindeki her türlü ağ düzeyi kaygılarını işleyebilir, örneğin:

- Hizmet bulma
- Yük dengeleme
- Hataya dayanıklılık
- Şifreleme
- İzleme

Kubernetes hizmet kafesleri, kafeste bulunan her Pod 'a *sepet proxy 'si* olarak adlandırılan ek bir kapsayıcı ekleyerek çalışır. Ara sunucu tüm gelen ve giden ağ isteklerini işlemeyi devralır. Daha sonra, ağ yapılandırma ve yönetimini uygulama kapsayıcılarından ayrı bir şekilde tutabilirsiniz. Çoğu durumda, bu ayrım uygulama kodunda herhangi bir değişiklik yapılmasını gerektirmez.

[Önceki bölümün örneğinde](kubernetes.md#test-the-application), Web uygulamasından alınan GRPC Isteklerinin hepsi GRPC hizmetinin tek bir örneğine yönlendirilir. Bunun nedeni, hizmetin ana bilgisayar adının bir IP adresine çözümlenmesi ve bu IP adresinin Örneğin kullanım ömrü boyunca önbelleğe alınması nedeniyle oluşur `HttpClientHandler` . DNS aramalarını el ile işleyerek veya birden çok istemci oluşturarak bu davranışı geçici olarak çözmek mümkün olabilir. Ancak bu geçici çözüm, uygulama kodunu herhangi bir iş veya müşteri değeri eklemeden karmaşıklaştırır.

Bir hizmet ağı kullandığınızda, uygulama kapsayıcısından gelen istekler sepet proxy 'sine gönderilir. Dışarıdan yükleme proxy 'si, daha sonra diğer hizmetin tüm örnekleri arasında onları akıllıca dağıtabilir. Kafes de şunları yapabilir:

- Bir hizmetin tek tek örneklerinden oluşan hatalara sorunsuz bir şekilde yanıt verin.
- Başarısız çağrılar veya zaman aşımları için yeniden deneme semantiğini işleyin.
- Başarısız istekleri istemci uygulamasına döndürülmeksizin alternatif bir örneğe yeniden yönlendir.

Aşağıdaki ekran görüntüsünde, Linkerd hizmet ağıyla çalışan StockWeb uygulaması gösterilmektedir. Uygulama kodunda değişiklik yapılmaz ve Docker görüntüsü kullanılmıyor. Gerekli tek değişiklik, ve hizmetleri için YAML dosyalarındaki dağıtıma ek açıklamanın ekleniydi `stockdata` `stockweb` .

![Hizmet ağı ile StockWeb](media/service-mesh/stockweb-servicemesh-screenshot.png)

StockWeb uygulamasından gelen isteklerin, uygulama kodundaki tek bir örnekten kaynaklanan StockData hizmetinin her iki çoğaltmasına de yönlendirildiğini **sunucu** sütunundan görebilirsiniz `HttpClient` . Aslında, kodu gözden geçirdikten sonra, StockData hizmeti için tüm 100 isteklerinin aynı örneği kullanarak aynı anda yapıldığını görürsünüz `HttpClient` . Hizmet ağı ile bu istekler arasında dengelenebilir, ancak birçok hizmet örneği kullanılabilir.

Hizmet kafesleri yalnızca bir küme içindeki trafiğe uygulanır. Dış istemciler için, bkz. bir sonraki bölüm, [Yük Dengeleme](load-balancing.md).

## <a name="service-mesh-options"></a>Hizmet ağ seçenekleri

Üç genel amaçlı hizmet kafesi uygulaması şu anda Kubernetes [:](https://istio.io) [ICD, Linkerd](https://linkerd.io)ve [tüketil Connect](https://consul.io/mesh.html)ile kullanılabilir. Tüm üç istek yönlendirme/proxy sağlama, trafik şifreleme, esnekliği, konaktan konağa kimlik doğrulaması ve trafik denetimi sağlar.

Hizmet kafesi seçme, birden fazla etkene bağlıdır:

- Kuruluşun maliyetler, uyumluluk, ücretli destek planları vb. için özel gereksinimleri.
- Kümenin doğası, boyutu, dağıtılan hizmet sayısı ve küme ağı içindeki trafik hacmi.
- Ağı dağıtma ve yönetme kolaylığı ve hizmetlerle kullanma.

## <a name="example-add-linkerd-to-a-deployment"></a>Örnek: bir dağıtıma Linkerd ekleme

Bu örnekte, [önceki bölümde](kubernetes.md) *StockKube* uygulamasıyla linkerd hizmet ağı 'nı nasıl kullanacağınızı öğreneceksiniz.
Bu örneği izlemek için, [Linkerd CLI 'yı yüklemeniz](https://linkerd.io/2/getting-started/#step-1-install-the-cli)gerekir. GitHub sürümlerini listeleyen bölümden Windows ikili dosyalarını indirebilirsiniz. Uç sürümlerden birini değil en son *kararlı* yayını kullandığınızdan emin olun.

Linkerd CLı yüklü olduğunda, Kubernetes kümenize Linkerd bileşenlerini yüklemek için [Başlarken yönergelerini izleyin](https://linkerd.io/2/getting-started/index.html) . Yönergeler basittir ve yükleme, yerel bir Kubernetes örneği üzerinde yalnızca birkaç dakika sürer.

### <a name="add-linkerd-to-kubernetes-deployments"></a>Kubernetes dağıtımlarını Linkerd 'e ekleme

Linkerd CLı, `inject` Kubernetes dosyalarına gerekli bölümleri ve özellikleri eklemek için bir komut sağlar. Komutu çalıştırabilir ve çıktıyı yeni bir dosyaya yazabilirsiniz.

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

Yapılan değişiklikleri görmek için yeni dosyaları inceleyebilirsiniz. Dağıtım nesneleri için, Linkerd 'nin oluşturulduğu sırada Pod 'a bir sepet ara sunucu kapsayıcısı eklemesine söylemek için bir meta veri ek açıklaması eklenir.

Komutun çıkışını doğrudan kanala yöneltmeyi de mümkün hale gelir `linkerd inject` `kubectl` . Aşağıdaki komutlar PowerShell veya herhangi bir Linux kabuğunda çalışır.

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a>Linkerd panosundaki Hizmetleri inceleyin

CLI kullanarak Linkerd panosunu açın `linkerd` .

```console
linkerd dashboard
```

Pano, ağa bağlı tüm hizmetler hakkında ayrıntılı bilgi sağlar.

![StockKube uygulamalarını gösteren linkerd panosu](media/service-mesh/linkerd-screenshot.png)

Aşağıdaki örnekte gösterildiği gibi StockData gRPC hizmetinin çoğaltmaların sayısını arttırırsanız ve tarayıcıdaki StockWeb sayfasını yenilediğinizde, **sunucu** sütununda bir kimlik karışımı görmeniz gerekir. Bu karışım, tüm kullanılabilir örneklerin istek görüyor olduğunu gösterir.

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
>[Önceki](kubernetes.md) 
> [Sonraki](load-balancing.md)
