---
title: Davpr Observability yapı taşı
description: Observability yapı bloğunun açıklaması, özellikleri, avantajları ve nasıl uygulanacağı
author: edwinvw
ms.date: 02/07/2021
ms.reviewer: robvet
ms.openlocfilehash: 6add36b2030c3061ee522604b2e07f05875b98a9
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604716"
---
# <a name="the-dapr-observability-building-block"></a>Davpr Observability yapı taşı

Modern dağıtılmış sistemler karmaşıktır. Küçük, gevşek olarak bağlanmış ve bağımsız dağıtılabilir hizmetlerle başlayabilirsiniz. Bu hizmetler çapraz işlem ve sunucu sınırları. Daha sonra farklı türlerde altyapı yedekleme hizmetleri (veritabanları, ileti aracıları, Anahtar kasaları) kullanır. Son olarak, bu farklı parçalar bir uygulama oluşturmak için birlikte oluşturur.

Çok sayıda ayrı, hareketli parçalar sayesinde ne olduğunu nasıl anladığınızda? Ne yazık ki, geçmişteki eski izleme yaklaşımları yeterince fazla değil. Bunun yerine, sistemin uçtan uca **observable** olması gerekir. Modern [Observability](../cloud-native/observability-patterns.md) uygulamaları, her zaman uygulamanın sistem durumu hakkında görünürlük ve öngörüler sağlar. Bu kişiler, çıktıyı gözlemleyerek iç durumu çıkarımı sağlar. Observability, dağıtılmış uygulamaları izlemek ve sorunlarını gidermek için zorunludur.

Observability kazanmak için kullanılan sistem bilgileri **telemetri** olarak adlandırılır. Bu, dört geniş kategoriye ayrılabilir:

1. **Dağıtılmış izleme** , Dağıtılmış işlemlerde yer alan hizmetler ve hizmetler arasındaki trafiğe ilişkin öngörüler sağlar.
1. **Ölçümler** , bir hizmetin performansına ve kaynak tüketimine ilişkin öngörüler sağlar.
1. **Günlüğe kaydetme** , kodun nasıl yürütüldüğü ve hataların oluşma hakkında öngörüler sağlar.
1. **Sistem durumu** uç noktaları, bir hizmetin kullanılabilirliğine ilişkin öngörüler sağlar.

Telemetri derinliği, bir uygulama platformunun Observability özellikleri tarafından belirlenir. Azure bulutunu göz önünde bulundurun. Telemetri kategorilerinin tümünü içeren zengin bir telemetri deneyimi sağlar. Herhangi bir yapılandırma olmadan, Azure IaaS ve PaaS hizmetlerinin çoğu Azure [Application Insights](/azure/azure-monitor/app/app-insights-overview) hizmetine telemetri yayar ve yayımlamaktır. Application Insights, yüksek görsel panolarla sistem günlüğü, izleme ve sorun alanı sunar. Hatta, iletişim özelliklerini temel alan hizmetler arasındaki bağımlılıkları gösteren bir diyagramı işleyebilir.

Ancak, bir uygulama Azure PaaS ve IaaS kaynaklarını kullanamıyoruz ne olursa? Application Insights zengin telemetri deneyiminden yararlanmak yine de mümkün mü? Yanıt Evet 'tir. Azure olmayan bir uygulama, Azure Application Insights telemetri yaymak için kitaplıkları içeri aktarabilir, yapılandırma ve araç kodu ekleyebilir. Ancak, bu yaklaşım uygulamayı Application Insights sıkı bir şekilde **bağar** . Uygulamayı farklı bir izleme platformuna taşımak, pahalı yeniden düzenleme gerektirebilir. Sıkı bir şekilde Observability mek ve kodun dışından kullanım sağlamak için harika olmaz misiniz?

Davpr ile yapabilirsiniz. Daha sonra, bir Davpr 'nin dağıtılmış uygulamalarınıza nasıl Observability ekleyebilmesine bakalım.

## <a name="what-it-solves"></a>Ne çözdüğü

Davpr Observability Building bloğu uygulamadan uples Observability ayrışar. Bu, davpr sıdecars ve davpr denetim düzlemi oluşturan Davpr sistem hizmetleri tarafından oluşturulan trafiği otomatik olarak yakalar. Blok, trafiği birden çok hizmete yayılan tek bir işlemden ilişkilendirir. Ayrıca performans ölçümlerini, kaynak kullanımını ve sistemin sistem durumunu gösterir. Telemetri, açık standart biçimlerde yayımlanır ve bu sayede, bilgilerin izleme arka ucuna eklenmesi sağlanır. Burada bilgiler görselleştirilir, sorgulanabilir ve analiz edilebilir.

Davpr, sıhhi tesisat 'yi uztığından, uygulama Observability nasıl uygulandığının farkında değildir. Kitaplıklara başvurulmasına veya özel izleme kodu uygulamanıza gerek yoktur. Davpr, geliştiricinin Observability tesisat değil iş mantığı oluşturmaya odaklanarak çalışmasına izin verir. Observability, mepr düzeyinde yapılandırılır ve farklı takımlar tarafından oluşturulduğunda bile hizmetler genelinde tutarlıdır ve farklı teknoloji yığınları ile oluşturulur.

## <a name="how-it-works"></a>Nasıl çalışır?

Davpr 'nin [Dışarıdan yükleme mimarisi](dapr-at-20000-feet.md#sidecar-architecture) , yerleşik Observability özellikleri sunar. Hizmetler iletişim kurarken, Davpr 'ler trafiği durdurur ve izleme, ölçümler ve günlüğe kaydetme bilgilerini ayıklar. Telemetri açık bir standartlar biçiminde yayımlanır. Varsayılan olarak, Davpr [Opentelemetri](https://opentelemetry.io/) ve [zipy](https://zipkin.io/)'yi destekler.

Davpr, farklı arka uç izleme araçlarına telemetri yayımlayabilen [toplayıcılar](https://docs.dapr.io/operations/monitoring/tracing/open-telemetry-collector/) sağlar. Bu araçlar analiz ve sorgulama için bir Dadpr telemetrisi sunar. Şekil 9-1, Davpr Observability mimarisini gösterir:

![Davpr Observability mimarisi](media/observability/observability-architecture.png)

**Şekil 9-1**. Davpr Observability mimarisi.

1. A hizmeti, B hizmetinde bir işlem çağırır. Çağrı, a hizmeti için a 'nın B hizmeti için bir kacar sepet 'ten yönlendirilir.
1. Hizmet B işlemi tamamlarsa, bir yanıt hizmet A 'ya bir yanıt gönderilir. Her istek ve yanıt için tüm kullanılabilir telemetri toplar ve yayımlar.
1. Yapılandırılan toplayıcı telemetri alır ve izleme arka ucuna gönderir.  

Geliştirici olarak, Observability eklemenin, pub/Sub veya State Management gibi diğer Davpr oluşturma bloklarını yapılandırmadan farklı olduğunu aklınızda bulundurun. Bir yapı bloğuna başvurmak yerine bir toplayıcı ve izleme arka ucu eklersiniz. Şekil 9-1, farklı izleme arka uçları ile tümleştirilen birden çok toplayıcı yapılandırmak için mümkün olduğunu gösterir.

Bu bölümün başlangıcında dört telemetri kategorisi tanımlanmıştı. Aşağıdaki bölümler her kategori için ayrıntı sağlayacaktır. Bunlar, popüler izleme arka uçları ile tümleştirilen toplayıcıların nasıl yapılandırılacağı hakkında yönergeler içerir.

### <a name="distributed-tracing"></a>Dağıtılmış izleme

Dağıtılmış izleme, dağıtılmış bir uygulamadaki hizmetler arasında akan trafiğe ilişkin öngörüler sağlar. Değiştirilen istek ve yanıt iletilerinin günlüğü, sorun giderme sorunları için değerli bir bilgi kaynağıdır. Sabit bölüm, aynı işlemden kaynaklanan *iletileri eş* olarak gösterir.

Davpr, ilgili iletileri ilişkilendirmek için [W3C Trace bağlamını](https://www.w3.org/TR/trace-context) kullanır. Aynı bağlam bilgilerini, benzersiz bir işlem oluşturan istek ve yanıtlara çıkartır. Şekil 9-2, bağıntı 'nın nasıl çalıştığını gösterir:

![W3C Trace bağlam örneği](media/observability/w3c-trace-context.png)

**Şekil 9-2**. W3C Trace bağlam örneği.

1. Hizmet A, B hizmetinde bir işlem çağırır. Service A çağrısı başlattığı için, Davpr benzersiz bir izleme bağlamı oluşturur ve bu dosyayı istek içine çıkarır.
1. B hizmeti, isteği alır ve hizmeti C üzerinde bir işlem çağırır. Davpr gelen isteğin bir izleme bağlamı içerdiğini algılar ve bunu, ekleme to Service to the The The The The The The The The Service a The The The The  
1. Service C, isteği alır ve işler. Davpr, gelen isteğin bir izleme bağlamı içerdiğini algılar ve bunu yeniden B hizmetine geri giden yanıtı ekleme göre yayar.
1. B hizmeti yanıtı alır ve işler. Daha sonra yeni bir yanıt oluşturur ve izleme bağlamını bir A hizmetine geri giden yanıt ekleme olarak yayar.

Birlikte gelen bir istek ve yanıt kümesine *izleme* denir. Şekil 9-3 bir izlemeyi gösterir:

![İzlemeler ve yayılmalar](media/observability/traces-spans.png)

**Şekil 9-3**. İzlemeler ve yayılmalar.

Şekilde, izlemenin birçok hizmet arasında gerçekleşen benzersiz bir uygulama işlemini nasıl temsil ettiğini unutmayın. İzleme, *yayılmalar* koleksiyonudur. Her yayılma, izleme içinde yapılan tek bir işlem veya iş birimini temsil eder. Yayılmalar, benzersiz işlemi uygulayan hizmetler arasında gönderilen isteklerdir ve yanıtlardır.

Sonraki bölümlerde, izleme telemetrisini bir izleme arka ucuna yayımlayarak nasıl inceleyeceğiniz açıklanmaktadır.

#### <a name="use-a-zipkin-monitoring-back-end"></a>Bir sıkıştırma arka ucu kullanın

[Zipkabağı](https://zipkin.io/) , açık kaynaklı bir dağıtılmış izleme sistemidir. Telemetri verilerini alabilir ve görselleştirin. Davpr, Ferkaya için varsayılan destek sunar. Aşağıdaki örnek, Davpr telemetrisini görselleştirmek üzere Zipkabağı 'nın nasıl yapılandırılacağını gösterir.

##### <a name="enable-and-configure-tracing"></a>İzlemeyi etkinleştirme ve yapılandırma

Başlamak için, bir Davpr yapılandırma dosyası kullanan Davpr çalışma zamanı için izlemenin etkinleştirilmesi gerekir. Aşağıda adlı bir yapılandırma dosyası örneği verilmiştir `tracing-config.yaml` :  

```yaml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: tracing-config
  namespace: default
spec:
  tracing:
    samplingRate: "1"
    zipkin:
      endpointAddress: "http://zipkin.default.svc.cluster.local:9411/api/v2/spans"
```

`samplingRate`Öznitelik, izlemeleri yayımlamak için kullanılan aralığı belirtir. Değer `0` (izleme devre dışı) ve `1` (her izleme yayımlanır) arasında olmalıdır. Örneğin, bir değeri ile, `0.5` yayımlanan trafiği önemli ölçüde azaltan diğer tüm izleme yayımlanır. `endpointAddress`Bir Kubernetes kümesinde çalışan bir Zipkaya sunucusunda bir uç noktaya işaret eder. Zipkaya için varsayılan bağlantı noktası `9411` . Yapılandırma Kubernetes CLı kullanılarak Kubernetes kümesine uygulanmalıdır:

```console
kubectl apply -f tracing-config.yaml
```

##### <a name="install-the-zipkin-server"></a>Zipkaya sunucusu 'nı yükler

Şirket içinde iç barındırılan modda Davpr yüklenirken, bir sıkıştırma sunucusu otomatik olarak yüklenir ve izleme, `$HOME/.dapr/config.yaml` veya Windows üzerinde bulunan varsayılan yapılandırma dosyasında etkinleştirilir `%USERPROFILE%\.dapr\config.yaml` .

Aynı halde bir Kubernetes kümesine düğüm yüklerken, varsayılan olarak Zipbağı eklenmez. Adlı aşağıdaki Kubernetes bildirim dosyası `zipkin.yaml` , kümeye standart bir Zipkaya sunucusu dağıtır:

```yaml
kind: Deployment
apiVersion: apps/v1
metadata:
  name: zipkin
  namespace: eshop
  labels:
    service: zipkin
spec:
  replicas: 1
  selector:
    matchLabels:
      service: zipkin
  template:
    metadata:
      labels:
        service: zipkin
    spec:
      containers:
        - name: zipkin
          image: openzipkin/zipkin-slim
          imagePullPolicy: IfNotPresent
          ports:
            - name: http
              containerPort: 9411
              protocol: TCP

---

kind: Service
apiVersion: v1
metadata:
  name: zipkin
  namespace: eshop
  labels:
    service: zipkin
spec:
  type: NodePort
  ports:
    - port: 9411
      targetPort: 9411
      nodePort: 32411
      protocol: TCP
      name: zipkin
  selector:
    service: zipkin

```

Dağıtım standart `openzipkin/zipkin-slim` kapsayıcı görüntüsünü kullanır. Sıkıştırma hizmeti, bağlantı noktasındaki Telemetriyi görüntülemek için kullanabileceğiniz, Web ön ucu 'nı kullanıma sunar `32411` . Kubernetes CLı ' yı kullanarak Kubernetes kümesine Zipbir bildirim dosyasını uygulayın ve Zipkabağı sunucusunu dağıtın:

```console
kubectl apply -f zipkin.yaml
```

##### <a name="configure-the-services-to-use-the-tracing-configuration"></a>İzleme yapılandırmasını kullanmak için Hizmetleri yapılandırma

Artık her şey telemetri yayımlamaya başlamak için doğru şekilde ayarlanmıştır. Uygulamanın bir parçası olarak dağıtılan her bir Davpr sepet, başlatıldığında telemetri yayma konusunda talimat verilmelidir. Bunu yapmak için, her bir `dapr.io/config` hizmetin dağıtımına, yapılandırmaya başvuran bir ek açıklama ekleyin `tracing-config` . Aşağıda, ek açıklamayı içeren bir eShop sıralaması API hizmetinin bildirim dosyasına bir örnek verilmiştir:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ordering-api
  namespace: eshop
  labels:
    app: eshop
spec:
  replicas: 1
  selector:
    matchLabels:
      app: eshop
  template:
    metadata:
      labels:
        app: simulation
      annotations:
        dapr.io/enabled: "true"
        dapr.io/app-id: "ordering-api"
        dapr.io/config: "tracing-config"
    spec:
      containers:
      - name: simulation
        image: eshop/ordering.api:linux-latest
```

##### <a name="inspect-the-telemetry-in-zipkin"></a>Kabağı 'nda Telemetriyi inceleyin

Uygulama başlatıldıktan sonra, Davpr sideckileri, Telemetriyi bir sunucuya yayIr. Bu Telemetriyi incelemek için bir Web tarayıcısının üzerine gelin <http://localhost:32411> . Bir Web ön ucu görürsünüz:

![Ferkabağı başlangıç sayfası](media/observability/zipkin.png)

*Izleme bul* sekmesinde, izlemeleri sorgulayabilirsiniz. *Sorgu Çalıştır* düğmesine herhangi bir kısıtlama belirtmeden basmak, alınan tüm *izlemeleri* gösterir:

![İzlemelerin listesi](media/observability/zipkin-traces-overview.png)

Belirli bir izlemenin yanındaki *göster* düğmesine tıkladığınızda, bu izlemenin ayrıntıları gösterilir:

![İzlemenin ayrıntıları](media/observability/zipkin-trace-details.png)

Ayrıntılar sayfasındaki her öğe, seçili izlemenin parçası olan bir isteği temsil eden bir yaydır.

##### <a name="inspect-the-dependencies-between-services"></a>Hizmetler arasındaki bağımlılıkları inceleyin

NPR 'ler arasındaki trafiği işlerken, Ferkabağı hizmetler arasındaki bağımlılıkları tespit etmek için izleme bilgilerini kullanabilir. Bunu işlem içinde görmek için, Ferkabağı Web sayfasındaki *Bağımlılıklar* sekmesine gidin ve Büyüteç Camı ile düğmeyi seçin. Kabağı, hizmetlere ve bunların bağımlılıklarına genel bir bakış gösterecektir:

![Ferkata bir bağımlılık grafiği](media/observability/zipkin-dependencies.png)

Hizmetler arasındaki satırlardaki animasyonlu noktalar istekleri temsil eder ve kaynaktan hedefe taşınır. Kırmızı noktalar başarısız bir isteği gösterir.

#### <a name="use-a-jaeger-or-new-relic-monitoring-back-end"></a>Bir Jaeger veya yeni bir relik izleme arka ucu kullanın

Aynı zamanda, diğer izleme arka uç yazılımları de Zipkabağı biçimini kullanarak Telemetriyi destekler. [Jaeger](https://www.jaegertracing.io/) , Uber teknolojileri tarafından oluşturulan açık kaynaklı bir izleme sistemidir. Dağıtılmış hizmetler arasındaki işlemleri izlemek ve karmaşık mikro hizmet ortamlarının sorunlarını gidermek için kullanılır. [New relik](https://newrelic.com/) , bir *tam yığın* Observability platformudur. Bir dağıtılmış uygulamadaki ilgili verileri, sisteminizin tamamına yönelik bir resim ile bağlantılandırır. Denemek için, `endpointAddress` DAPR yapılandırma dosyasında bir Caeger ya da yeni relik sunucusu için bir işaret noktası belirtin. Aşağıda, DAPR 'yi bir Caeger sunucusuna telemetri gönderecek şekilde yapılandıran bir yapılandırma dosyası örneği verilmiştir. Caeger URL 'SI, Ferkabağı URL 'siyle aynıdır. Tek fark sunucunun çalıştığı bağlantı noktasıdır:

 ```yaml
 apiVersion: dapr.io/v1alpha1
 kind: Configuration
 metadata:
   name: tracing-config
   namespace: default
 spec:
   tracing:
     samplingRate: "1"
     zipkin:
       endpointAddress: "http://localhost:9415/api/v2/spans"
 ```

Yeni yeniden denemek için yeni relik API 'sinin uç noktasını belirtin. Yeni relik için yapılandırma dosyasına bir örnek aşağıda verilmiştir:

 ```yaml
apiVersion: dapr.io/v1alpha1
 kind: Configuration
 metadata:
   name: tracing-config
   namespace: default
 spec:
   tracing:
     samplingRate: "1"
     zipkin:
       endpointAddress: "https://trace-api.newrelic.com/trace/v1?Api-Key=<NR-API-KEY>&Data-Format=zipkin&Data-Format-Version=2"
 ```

Kullanım hakkında daha fazla bilgi için, Jaeger ve yeni relik Web sitelerine göz atın.

### <a name="metrics"></a>Ölçümler

Ölçümler, performans ve kaynak tüketimine ilişkin öngörüler sağlar. Aynı şekilde, Davpr, sistem ve çalışma zamanı ölçümlerinin geniş bir koleksiyonunu yayar. Davpr, ölçüm standardı olarak [Prometheus](https://prometheus.io/) kullanır. Davpr sıdecars ve sistem hizmetleri, bağlantı noktasında ölçüm uç noktasını kullanıma sunar `9090` . Bir *Prometheus atık* , bu uç noktayı, ölçümleri toplamak için önceden tanımlanmış bir aralıkta çağırır. Atık oluşturma, ölçüm değerlerini bir izleme arka ucuna gönderir. Şekil 9-4, scraping işlemini gösterir:

![Scraping Prometheus ölçümleri](media/observability/prometheus-scraper.png)

**Şekil 9-4**. Scraping Prometheus ölçümleri.

Yukarıdaki şekilde, her sepet ve sistem hizmeti, 9090 bağlantı noktasını dinleyen bir ölçüm uç noktası sunar. Prometheus ölçümleri, her bir uç noktadan ölçümleri yakalar ve bilgileri izleme arka ucuna yayımlamış.  

#### <a name="service-discovery"></a>Hizmet bulma

Ölçümlerin, ölçümlerin nerede toplanacağını öğrendiğinde merak edebilirsiniz. Prometheus, hedef dağıtım ortamlarında yerleşik olarak bulunan keşif mekanizmalarıyla tümleştirilebilir. Örneğin, Kubernetes 'te çalışırken Prometheus, ortamda çalışan tüm kullanılabilir Kubernetes kaynaklarını bulmak için Kubernetes API 'siyle tümleştirilebilir.

#### <a name="metrics-list"></a>Ölçüm listesi

Davpr, Davpr sistem hizmetleri ve çalışma zamanı için büyük bir ölçüm kümesi oluşturur. Bazı örnekler:

| Metric                                         | Kaynak | Açıklama                                                  |
| ---------------------------------------------- | :----: | ------------------------------------------------------------ |
| dapr_operator_service_created_total            | Sistem | DAPR Işleç hizmeti tarafından oluşturulan toplam DAPR Hizmetleri sayısıdır. |
| dapr_injector_sidecar_injection/requests_total | Sistem | Davpr Sidecar-Injector hizmeti tarafından alınan sepet ekleme isteklerinin toplam sayısı. |
| dapr_placement_runtimes_total                  | Sistem | Davpr yerleştirme hizmetine bildirilen toplam ana bilgisayar sayısı. |
| dapr_sentry_cert_sign_request_received_total   | Sistem | Davpr Sentry hizmeti tarafından alınan sertifika imzalama isteği (CRSs) sayısı. |
| dapr_runtime_component_loaded      | Çalışma Zamanı | Başarıyla yüklenen Davpr bileşenleri sayısı.           |
| dapr_grpc_io_server_completed_rpcs | Çalışma Zamanı | Yönteme ve duruma göre gRPC çağrılarının sayısı.                    |
| dapr_http_server_request_count     | Çalışma Zamanı | HTTP sunucusunda başlatılan HTTP isteklerinin sayısı.           |
| dapr_http/Client/sent_bytes        | Çalışma Zamanı | Bir HTTP istemcisi tarafından istek gövdesinde (üstbilgiler dahil değil) gönderilen toplam bayt sayısı. |

Kullanılabilir ölçümler hakkında daha fazla bilgi için bkz. [Davpr ölçümleri belgeleri](https://docs.dapr.io/operations/monitoring/metrics/).

#### <a name="configure-dapr-metrics"></a>Davpr ölçümlerini yapılandırma

Çalışma zamanında, `--enable-metrics=false` bağımsız değişkenini Davpr komutuna ekleyerek ölçüm toplama uç noktasını devre dışı bırakabilirsiniz. Ayrıca, uç nokta için varsayılan bağlantı noktasını `--metrics-port 9090` bağımsız değişkenle de değiştirebilirsiniz.

Ayrıca, çalışma zamanı ölçümleri toplamasını statik olarak etkinleştirmek veya devre dışı bırakmak için bir Davpr yapılandırma dosyası da kullanabilirsiniz:

```yaml
apiVersion: dapr.io/v1alpha1
kind: Configuration
metadata:
  name: dapr-config
  namespace: eshop
spec:
  tracing:
    samplingRate: "1"
  metric:
    enabled: false
```

#### <a name="visualize-dapr-metrics"></a>Davpr ölçümlerini görselleştirin

Prometheus atık oluşturma ve ölçümleri izleme arka ucuna yayımlama konusunda, ham verileri nasıl anladınız? Ölçümleri çözümlemek için popüler bir görselleştirme aracı [Grafana](https://grafana.com/grafana/). Grafana ile, kullanılabilir ölçülerden panolar oluşturabilirsiniz. Aşağıda, Davpr sistem hizmetleri ölçümlerini görüntüleyen bir panoya örnek verilmiştir:

![Grafana, Davpr sistem hizmetleri ölçümlerini görüntüleyen Pano](media/observability/grafana-sample.png)

Davpr belgeleri, [Prometheus ve Grafana yükleme öğreticisini](https://docs.dapr.io/operations/monitoring/metrics/grafana/)içerir.

### <a name="logging"></a>Günlüğe Kaydetme

Günlüğe kaydetme, çalışma zamanında bir hizmette neler olduğunu gösteren öngörüler sağlar. Bir uygulamayı çalıştırırken, Davpr sıdecars ve Davpr sistem hizmetlerinden günlük girdilerini otomatik olarak yayar. Ancak, uygulama kodunuzda belgelenmiş günlüğe kaydetme girdileri otomatik olarak dahil **edilmez** . Uygulama kodundan günlük yayma yapmak için, [.net Için Opentelemetri SDK](https://opentelemetry.io/docs/net/)gibi belırlı bir SDK 'yı içeri aktarabilirsiniz. Günlüğe kaydetme uygulama kodu, bu bölümün ilerleyen kısımlarında, *Davpr .NET SDK kullanılarak* bölümünde ele alınmıştır.  

#### <a name="log-entry-structure"></a>Günlük girdisi yapısı

Davpr yapılandırılmış günlüğe kaydetme yayar. Her günlük girdisi aşağıdaki biçimdedir:

| Alan    | Açıklama                                          | Örnek                             |
| -------- | ---------------------------------------------------- | ----------------------------------- |
| time     | ISO8601 biçimli zaman damgası                          | `2021-01-10T14:19:31.000Z`          |
| düzey    | Girişin düzeyi ( `debug` \| `info` \| `warn` \| `error` )   | `info`                              |
| tür     | Günlük Türü                                             | `log`                               |
| msg      | Günlük Iletisi                                          | `metrics server started on :62408/` |
| scope    | Günlüğe kaydetme kapsamı                                        | `dapr.runtime`                      |
| örnek | Bapr 'nin çalıştığı ana bilgisayar adı                             | TSTSRV01                            |
| app_id   | Davpr uygulama KIMLIĞI                                          | sıralama-API                        |
| ver      | Davpr çalışma zamanı sürümü                                 | `1.0.0`-RC. 2                        |

Sorun giderme senaryosunda günlüğe kaydetme girişlerinde arama yaparken, `time` ve `level` alanları özellikle yararlıdır. Zaman alanı, belirli zaman aralıklarını belirleyebilmeniz için günlük girdilerini sıralar. Sorun giderirken, *hata ayıklama düzeyindeki* günlük girişleri kodun davranışı hakkında daha fazla bilgi sağlar.

#### <a name="plain-text-versus-json-format"></a>Düz metin ve JSON biçimi

Varsayılan olarak, Davpr yapılandırılmış günlük ' i düz metin biçiminde yayar. Her günlük girdisi, anahtar/değer çiftlerini içeren bir dize olarak biçimlendirilir. Düz metinde günlüğe kaydetme örneği aşağıda verilmiştir:

```text
== DAPR == time="2021-01-12T16:11:39.4669323+01:00" level=info msg="starting Dapr Runtime -- version 1.0.0-rc.2 -- commit 196483d" app_id=ordering-api instance=TSTSRV03 scope=dapr.runtime type=log ver=1.0.0-rc.2
== DAPR == time="2021-01-12T16:11:39.467933+01:00" level=info msg="log level set to: info" app_id=ordering-api instance=TSTSRV03 scope=dapr.runtime type=log ver=1.0.0-rc.2
== DAPR == time="2021-01-12T16:11:39.467933+01:00" level=info msg="metrics server started on :62408/" app_id=ordering-api instance=TSTSRV03 scope=dapr.metrics type=log ver=1.0.0-rc.2
```

Basit olsa da, bu biçimin ayrıştırılması zordur. Günlük girişlerini bir izleme aracıyla görüntülüyorsanız, JSON biçimli günlüğe kaydetmeyi etkinleştirmek isteyeceksiniz. JSON girdileriyle, bir izleme aracı tek tek alanları dizinedebilir ve sorgulayabilir. JSON biçiminde aynı günlük girdileri aşağıda verilmiştir:

```json
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "starting Dapr Runtime -- version 1.0.0-rc.2 -- commit 196483d", "scope": "dapr.runtime", "time": "2021-01-12T16:11:39.4669323+01:00", "type": "log", "ver": "1.0.0-rc.2"}
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "log level set to: info", "scope": "dapr.runtime", "type": "log", "time": "2021-01-12T16:11:39.467933+01:00", "ver": "1.0.0-rc.2"}
{"app_id": "ordering-api", "instance": "TSTSRV03", "level": "info", "msg": "metrics server started on :62408/", "scope": "dapr.metrics", "type": "log", "time": "2021-01-12T16:11:39.467933+01:00", "ver": "1.0.0-rc.2"}
```

JSON biçimlendirmesini etkinleştirmek için, her bir Davpr sidecar 'yi yapılandırmanız gerekir. Kendi kendine barındırılan modda, `--log-as-json` komut satırında bayrağını belirtebilirsiniz:

```console
dapr run --app-id ordering-api --log-level info --log-as-json dotnet run
```

Kubernetes 'de, `dapr.io/log-as-json` uygulamanın her dağıtımına bir ek açıklama ekleyebilirsiniz:

```yaml
annotations:
   dapr.io/enabled: "true"
   dapr.io/app-id: "ordering-api"
   dapr.io/app-port: "80"
   dapr.io/config: "dapr-config"
   dapr.io/log-as-json: "true"
```

Helk kullanarak bir Kubernetes kümesinde Davpr 'yi yüklediğinizde, tüm Davpr sistem hizmetleri için JSON biçimli günlüğe kaydetmeyi etkinleştirebilirsiniz:

```console
helm repo add dapr https://dapr.github.io/helm-charts/
helm repo update
kubectl create namespace dapr-system
helm install dapr dapr/dapr --namespace dapr-system --set global.logAsJson=true
```

#### <a name="collect-logs"></a>Günlük toplama

Davpr tarafından yayılan Günlükler analiz için bir izleme arka ucuna dağıtılabilir. Günlük Toplayıcısı, bir sistemden günlükleri toplayan ve bunları bir izleme arka ucuna gönderen bir bileşendir. Popüler bir günlük toplayıcısı [akıcı Entd](https://www.fluentd.org/). Bkz. [nasıl yapılır: vapr belgelerindeki Kubernetes 'te, akıcı Entd, elastik arama ve kibana ayarlama](https://docs.dapr.io/operations/monitoring/logging/fluentd/) . Bu makale, izleme arka ucu olarak Akıştoplayıcı ve [elk yığınını](https://www.elastic.co/elastic-stack) (elastik arama ve kibana) ayarlamaya yönelik yönergeler içerir.

### <a name="health-status"></a>Sistem durumu

Bir hizmetin sistem durumu, kullanılabilirliği hakkında öngörüler sağlar. Her bir Davpr dışarıdan yükleme, sepet durumunu anlamak için barındırma ortamı tarafından kullanılabilen bir sistem durumu API 'SI sunar. API 'de bir işlem vardır:

```console
GET http://localhost:3500/v1.0/healthz
```

İşlem iki HTTP durum kodu döndürür:

- 204: sepet sağlıklı olduğunda
- 500: sepet sağlıklı olmadığında

Şirket içinde barındırılan modda çalışırken sistem durumu API 'SI otomatik olarak çağrılmaz. API 'yi, uygulama kodundan veya bir sistem durumu izleme aracından çalıştırabilirsiniz.

Kubernetes 'te çalışırken, DAPR sidecar-Injector, Kubernetes 'i otomatik olarak *yapılandırır.* 

Kubernetes, bir kapsayıcının çalışır duruma getirme olup olmadığını anlamak için emize yönelik yoklamalar kullanır. Bir limek araştırması bir hata kodu döndürürse, Kubernetes kapsayıcının ölü olduğunu varsayar ve otomatik olarak yeniden başlatır. Bu özellik, uygulamanızın genel kullanılabilirliğini artırır.

Kubernetes, bir kapsayıcının trafiği kabul etmeye hazır olup olmadığını anlamak için hazırlık araştırmaları kullanır. Tüm kapsayıcıları kullanılabilir olduğunda Pod, Ready olarak kabul edilir. Hazır olma durumu, bir Kubernetes hizmetinin bir yük dengeleme senaryosunda bir pod 'e trafik iletip yönlendirmeyeceğini belirler. Artık, yok, yük dengeleyiciden otomatik olarak kaldırılır.

Lileleme ve hazırlık araştırmaları birkaç yapılandırılabilir parametreye sahiptir. Her ikisi de Pod 'ın bildirim dosyasının kapsayıcı belirtimi bölümünde yapılandırılır. Varsayılan olarak, Davpr her sepet kapsayıcısı için aşağıdaki yapılandırmayı kullanır:

```yaml
livenessProbe:
      httpGet:
        path: v1.0/healthz
        port: 3500
      initialDelaySeconds: 5
      periodSeconds: 10
      timeoutSeconds : 5
      failureThreshold : 3
readinessProbe:
      httpGet:
        path: v1.0/healthz
        port: 3500
      initialDelaySeconds: 5
      periodSeconds: 10
      timeoutSeconds : 5
      failureThreshold: 3
```

 Yoklamalar için aşağıdaki parametreler mevcuttur:

- , `path` Davpr SAĞLıK API uç noktasını belirtir.
- , `port` Davpr sağlık API 'si bağlantı noktasını belirtir.
- , `initialDelaySeconds` Kubernetes 'ın kapsayıcıyı ilk kez yoklamaya başlamadan önce bekleyeceği saniye sayısını belirtir.
- , `periodSeconds` Kubernetes 'lerin her bir yoklama arasında bekleyeceği saniye sayısını belirtir.
- , `timeoutSeconds` Kubernetes 'in zaman aşımından önce API 'den Yanıt beklemesi gereken saniye sayısını belirtir. Zaman aşımı hata olarak yorumlanır.
- `failureThreshold`Kapsayıcının etkin değil veya hazır değil olduğunu düşünmeden önce, Kubernetes 'nin kabul edeceği başarısız durum kodu sayısını belirtir.

### <a name="dapr-dashboard"></a>Davpr panosu

Davpr, Davpr uygulamaları, bileşenleri ve yapılandırmalarında durum bilgilerini sunan bir pano sunar. Panoyu 8080 numaralı bağlantı noktasında yerel makinede bir Web uygulaması olarak başlatmak için Davpr CLı kullanın:

```console
dapr dashboard
```

Kubernetes 'te çalışan Davpr uygulaması için aşağıdaki komutu kullanın:

```console
dapr dashboard -k
```

Pano, uygulamanızdaki bir Davpr dışarıdan arabası bulunduğu tüm hizmetlere genel bir bakış ile açılır. Aşağıdaki ekran görüntüsünde, Kubernetes 'te çalışan Eshopondadpr uygulamasının Davpr panosu gösterilmektedir:

![Davpr panosuna genel bakış sayfası](media/observability/dapr-dashboard-overview.png)

Bir Davpr uygulamasının sorunlarını giderirken, Davpr panosu önemli değildir. Bu, Davpr sıdecars ve sistem hizmetleri hakkında bilgi sağlar. Günlük girişleri dahil olmak üzere her bir hizmetin yapılandırmasında ayrıntıya gidebilirsiniz.

Pano Ayrıca uygulamanızın yapılandırılmış bileşenlerini (ve yapılandırmalarını) gösterir:

![Davpr Pano bileşenleri sayfası](media/observability/dapr-dashboard-components.png)

Pano aracılığıyla kullanılabilecek büyük miktarda bilgi vardır. Bunu, bir Davpr uygulaması çalıştırarak ve panoya göz atarak keşfedebilirsiniz. Başlamak için eşlik eden Eshopondadpr uygulamasını kullanabilirsiniz.

Davpr Pano komutları hakkında daha fazla bilgi için, davpr belgelerinden [davpr Pano CLI komut başvurusunu](https://docs.dapr.io/reference/cli/dapr-dashboard/) inceleyin.

## <a name="use-the-dapr-net-sdk"></a>Davpr .NET SDK 'sını kullanma

Davpr .NET SDK 'Sı herhangi bir belirli Observability özelliği içermiyor. Tüm Observability özellikleri, Davpr düzeyinde sunulur.

.NET uygulama kodunuzda telemetri yaymak istiyorsanız [.net Için Opentelemetri SDK 'sını](https://opentelemetry.io/docs/net/)göz önünde bulundurmanız gerekir. Açık telemetri projesi platformlar arası, açık kaynak ve satıcı belirsiz. Telemetri verilerini oluşturma, yayma, toplama, işleme ve dışarı aktarmaya yönelik uçtan uca bir uygulama sağlar. Otomatik ve el ile izleme desteği sunan dil başına tek bir izleme kitaplığı vardır. Telemetri, açık telemetri standardı kullanılarak yayımlanır. Projenin bulut sağlayıcılarından, satıcılarından ve son kullanıcılardan geniş sektör desteği ve benimseme olanağı vardır.

## <a name="reference-application-eshopondapr"></a>Başvuru uygulaması: Eshopondadpr

Eşlik eden Eshopondadpr başvuru uygulamasındaki Observability, birkaç bölümden oluşur. Tüm nesnelerin telemetrisi yakalanır. Ayrıca, önceki eShopOnContainers örneğinden devralınan diğer Observability özellikleri de mevcuttur.

### <a name="custom-health-dashboard"></a>Özel durum panosu

Eshopondadpr 'deki **Webstatus** projesi, eShop hizmetlerinin sistem durumuna ilişkin Öngörüler sağlayan özel bir sistem durumu panosıdır. Bu Pano, Davpr sistem durumu API 'sini kullanmaz, ancak ASP.NET Core yerleşik [durum denetimleri mekanizmasını](/aspnet/core/host-and-deploy/health-checks) kullanır. Pano yalnızca hizmetlerin sistem durumunu değil, hizmetlerin bağımlılıklarının durumunu da sağlamaz. Örneğin, bir veritabanı kullanan bir hizmet, aşağıdaki ekran görüntüsünde gösterildiği gibi bu veritabanının sistem durumunu da sağlar:

![Eshopondadpr özel durum panosu](media/observability/eshop-health-dashboard.png)

### <a name="seq-log-aggregator"></a>Seq Günlük Toplayıcısı

[Sıra](https://datalust.co/seq) , günlükleri toplamak Için Eshopondadpr 'de kullanılan popüler bir günlük toplayıcısı sunucusudur. Uygulama hizmetlerinden günlüğe kaydetme, ancak Davpr sistem hizmetlerinden veya sıfları olmayan sıra. Seq uygulama günlüğünü oluşturur ve günlükleri analiz etmek ve sorgulamak için bir Web ön ucu sunar. İzleme panoları oluşturmaya yönelik işlevler de sunar.

Eshopondadpr uygulama hizmetleri, [SeriLog](https://serilog.net/) günlük kitaplığını kullanarak yapılandırılmış günlüğü yayar. Serilog, **Havuz** adlı bir yapı için günlük olaylarını yayımlar. Havuz, Serilog 'in günlüğe kaydetme olaylarını yazdığı bir hedef platformdur. Seq için bir de dahil olmak üzere [birçok Serilog havuzları mevcuttur](https://github.com/serilog/serilog/wiki/Provided-Sinks). Sıra, Eshopondadpr içinde kullanılan Serilog Havuzu.

### <a name="application-insights"></a>Application Insights

Eshopondadpr Hizmetleri ayrıca .NET Core için Microsoft Application Insights SDK 'sını kullanarak doğrudan Azure Application Insights telemetri gönderir. Daha fazla bilgi için bkz. Microsoft docs 'taki [ASP.NET Core uygulamalar Için Azure Application Insights](/azure/azure-monitor/app/asp-net-core) .

## <a name="summary"></a>Özet

Üretim ortamında Dağıtılmış bir sistem çalıştırılırken iyi Observability çok önemlidir.

Davpr, dağıtılmış izleme, günlüğe kaydetme, ölçümler ve sistem durumu gibi farklı türlerde telemetri sağlar.

Davpr yalnızca, Davpr sistem hizmetleri ve sıfları için telemetri üretir. Uygulama kodunuzun telemetrisi otomatik olarak dahil değildir. Ancak, uygulama kodunuzda telemetri göstermek için .NET için Opentelemetri SDK gibi belirli bir SDK 'Yı kullanabilirsiniz.

Davpr telemetrisi, Açık standartlara dayalı bir biçimde üretilerek, büyük bir kullanılabilir izleme araçları kümesiyle gerçekleştirilebilir. Bazı örnekler şunlardır: Zipar, Azure Application Insights, ELK yığını, New relik ve Grafana. Belirli izleme arka uçları ile Davpr uygulamalarınızı izlemeye yönelik öğreticiler için bkz. davpr belgelerindeki [davpr ile uygulamanızı izleme](https://docs.dapr.io/operations/monitoring/) .

Bu telemetri için bir telemetri atık ve izleme arka ucuna yayınlıyor olmanız gerekir.

Davpr yapılandırılmış günlüğe kaydetmeyi yayan yapılandırılabilir. Yapılandırılmış günlüğe kaydetme, arka uç izleme araçlarıyla dizin oluşturulduğundan daha kırmızıdır. Dizini oluşturulmuş günlük kaydı, kullanıcıların günlüğe kaydetme sırasında arama yaparken zengin sorguları yürütmelerine olanak sağlar.

Davpr, Davpr Hizmetleri ve yapılandırması hakkında bilgi sunan bir pano sunar.

## <a name="references"></a>Başvurular

- [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview/)
- [Telemetriyi açın](https://opentelemetry.io/)
- [Ferkabağı](https://zipkin.io/)
- [W3C Trace bağlamı](https://www.w3.org/TR/trace-context/)
- [Jaeger](https://www.jaegertracing.io/)
- [New Relic](https://newrelic.com/)
- [Prometheus](https://prometheus.io/)
- [Grafana](https://grafana.com/grafana/)
- [.NET için telemetri SDK 'sını açın](https://opentelemetry.io/docs/net/)
- [Fluentd](https://www.fluentd.org/)
- [ELK yığını](https://www.elastic.co/elastic-stack)
- [Sıra](https://datalust.co/seq)
- [Serilog](https://serilog.net/)

> [!div class="step-by-step"]
> [Önceki](bindings.md) 
>  [Sonraki](secrets.md)
