---
title: 20.000 fit üzerinde davpr
description: Nepr 'nin ne olduğu, ne yaptığı ve nasıl çalıştığı hakkında üst düzey bir genel bakış.
author: robvet
ms.date: 02/17/2021
ms.openlocfilehash: 6e5d73f8c49ecb3eec518986e2af60c68195c0ab
ms.sourcegitcommit: 5ce37699c2a51ed173171813be68ef7577b1aba5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/23/2021
ms.locfileid: "104881087"
---
# <a name="dapr-at-20000-feet"></a>20.000 fit üzerinde davpr

Bölüm 1 ' de, dağıtılmış mikro hizmet uygulamalarının birlikte ele alındığı açıklanır. Ancak, mimari ve operasyonel karmaşıklığı önemli ölçüde artıracağız. Bu şekilde, soru, "Pastanıza nasıl sahip olabilirsiniz" ve "çok fazla yemek mu?" şeklinde olur. Diğer bir deyişle, dağıtılmış mimarinin çeviklerinden nasıl yararlanabilir ve karmaşıklığını en aza indirirsiniz?

PAPR veya *Dağıtılmış uygulama çalışma zamanı*, modern dağıtılmış uygulamalar oluşturmanın yeni bir yoludur.

Prototip olarak başlatılan, yüksek oranda başarılı bir açık kaynaklı projede geliştirilmiştir. Destekleyicisi, Microsoft, Bapr 'yi tasarlamak ve derlemek için müşterilerle ve açık kaynaklı toplulukla yakından işbirliği yaptı. Davpr projesi, dağıtılmış uygulamalar geliştirmeye yönelik bazı en zorlu zorluk sorunlarını çözmek için tüm arka planlardan geliştiricilere bir araya getirir.

Bu kitap, bir .NET geliştiricisinin görüş açısından, Davpr 'ye bakar. Bu bölümde, Davpr ve nasıl çalıştığı hakkında kavramsal bir anlama oluşturacaksınız. Daha sonra, uygulamalarınızda Dadpr 'yi nasıl kullanabileceğiniz konusunda pratik, uygulamalı yönergeler sunuyoruz.

20.000 fit ' te bir Jet 'e uçan düşünün. Pencereyi gözden geçirin ve aşağıdaki dikey pencereyi geniş bir perspektiften görürsünüz. Aynı şekilde, Davpr için de aynı şekilde yapalim. 20.000 fit 'te Davpr üzerinden kendinizi görselleştirin. Ne görüyorsunuz?

## <a name="dapr-and-the-problem-it-solves"></a>Davpr ve çözdüğü sorun

DAPR, modern dağıtılmış uygulamalarda büyük bir sınama ele alınmaktadır: **karmaşıklık**.

Bir takılabilir bileşenler mimarisi sayesinde, Davpr Dağıtılmış uygulamaların arkasındaki sıhhi tesisat 'yi büyük ölçüde basitleştirir. Bu, uygulamanızı, Davpr çalışma zamanından altyapı özelliklerine bağlayan **dinamik bir birleştirici** sağlar.

Hizmetlerinizin birini durum bilgisi olarak oluşturmak için bir gereksinim düşünün mı? Tasarımınız ne olacaktır? Redis Cache gibi bir durum deposunu hedefleyen özel kod yazabilirsiniz. Ancak, Davpr durum yönetimi yeteneklerini kullanıma hazır olarak sunar. Hizmetiniz, bir Davpr **bileşen yapılandırması** YAML dosyası aracılığıyla bir durum depolama **bileşenine** dinamik olarak bağlanan bir davpr durum yönetimi **yapı taşı** çağırır. Davpr, Reddir dahil olmak üzere önceden oluşturulmuş çeşitli durum depolama bileşenleriyle birlikte gelir. Bu modelde, hizmetiniz durum yönetimini Davpr çalışma zamanına devreder. Hizmetinizin SDK, kitaplık veya temel bileşene doğrudan başvurusu yok. Durum depolarını, Redsıs 'den MySQL veya Cassandra 'dan kod değişikliği olmadan da değiştirebilirsiniz.

Şekil 2-1, 20.000 metreden Davpr 'yi gösterir.

![20.000 fit ](./media/dapr-at-20000-feet/dapr-high-level.png)
 **Şekil 2-1**' de davpr. 20.000 fit üzerinde davpr.

Şeklin en üst satırında, Davpr 'nin popüler geliştirme platformları için dile özgü SDK 'lar sağladığını aklınızda bulabilirsiniz. Davpr v 1,0, Go, Node.js, Python, .NET, Java ve JavaScript 'i destekler. Bu kitap, ASP.NET Core tümleştirme için doğrudan destek sağlayan Davpr .NET SDK 'sına odaklanır.

Dile özgü SDK 'lar geliştirici deneyimini geliştirirken, Davpr platform belirsiz. Aynı şekilde, Davpr 'nin programlama modeli standart HTTP/gRPC iletişim protokolleri aracılığıyla özellikleri kullanıma sunar. Herhangi bir programlama platformu, yerel HTTP ve gRPC API 'Leri aracılığıyla Davpr 'yi çağırabilir.  

Şeklin merkezinde mavi kutular, Davpr oluşturma bloklarını temsil eder. , Uygulamanızın tüketebileceği bir dağıtılmış uygulama özelliği sunar.

Alt satır, PAPR 'nin taşınabilirlik ve üzerinde çalışacağı farklı ortamları vurgular.

## <a name="dapr-architecture"></a>Davpr mimarisi

Bu noktada, Jet, daha sonra, Davpr 'nin nasıl çalıştığına ilişkin daha yakından bir bakış sunarak ters bir şekilde azalan bir şekilde geri dönebilir.

### <a name="building-blocks"></a>Yapı taşları

Yeni perspektifinden, Davpr **oluşturma bloklarının** daha ayrıntılı bir görünümünü görürsünüz.

Yapı taşı, dağıtılmış bir altyapı özelliğini kapsüller. İşlevselliğe HTTP veya gRPC API 'Leri aracılığıyla erişebilirsiniz. Şekil 2-2, Davpr v 1,0 için kullanılabilir blokları gösterir.

![Davpr yapı taşları](./media/dapr-at-20000-feet/building-blocks.png)

**Şekil 2-2**. Davpr yapı taşları.

Aşağıdaki tabloda her bir blok tarafından sunulan altyapı hizmetleri açıklanmaktadır.

| Yapı taşı | Açıklama |
|----------------|-------------|
| [Durum yönetimi](state-management.md) | Uzun süreli durum bilgisi olan hizmetler için bağlamsal bilgileri destekler. |
| [Hizmet çağrısı](service-invocation.md) | Platform belirsiz protokollerini ve iyi bilinen uç noktaları kullanarak doğrudan, hizmetten hizmete çağrıları çağırın. |
| [Yayımla ve abone ol](publish-subscribe.md) | Hizmetler arasında güvenli, ölçeklenebilir bir yayın/alt ileti uygulama. |
| [Bağlamalar](bindings.md) | Çift yönlü iletişim ile dış kaynaklar tarafından oluşturulan olaylardan kodu tetikleyin. |
| [Gözlemlenebilirlik](observability.md) | Ağ üzerinden yapılan hizmetlerde ileti çağrılarını izleyin ve ölçün. |
| [Gizli Diziler](secrets.md) | Dış gizli depolara güvenli şekilde erişin. |
| Aktörler | Yeniden kullanılabilir aktör nesnelerinde Logic ve verileri kapsülleyebilirsiniz. |

Yapı taşları, hizmetinizdeki dağıtılmış uygulama yeteneklerinin uygulanmasını soyutlar. Şekil 2-3 bu etkileşimi gösterir.

![Davpr derleme blokları tümleştirmesi](./media/dapr-at-20000-feet/building-blocks-integration.png)

**Şekil 2-3**. Davpr yapı blok tümleştirmesi.

Yapı taşları her kaynak için somut uygulama sağlayan Davpr bileşenlerini çağırır. Hizmetinizin kodu yalnızca yapı bloğundan haberdar değildir. Dış SDK 'larda veya kitaplıklarda hiçbir bağımlılık yoktur-Davpr sizin için bir tesisat uygular. Her yapı taşı bağımsızdır. Uygulamanızdaki birini, bazılarını veya tümünü kullanabilirsiniz. Değer olarak-Add, Davpr bina blokları, kapsamlı Observability dahil sektörde en iyi deneyimler.

Yaklaşan bölümlerde her bir Davpr yapı taşı için ayrıntılı açıklama ve kod örnekleri sağlıyoruz. Bu noktada, Jet daha da daha da fazla. Yeni perspektifinden, artık Davpr bileşenleri katmanına daha yakından bakacağız.

### <a name="components"></a>Bileşenler

Yapı taşları, dağıtılmış uygulama yeteneklerini çağırmak için bir API kullanıma sunurken, Davpr bileşenleri olması için somut bir uygulama sağlar.

Davpr **durum depolama** bileşenini göz önünde bulundurun. CRUD işlemlerinde durumu yönetmek için Tekdüzen bir yol sağlar. Hizmet kodunuzda herhangi bir değişiklik yapmadan aşağıdaki Davpr durum bileşenlerinden herhangi biri arasında geçiş yapabilirsiniz:

- AWS DynamoDB
- Hava çıkış
- Azure Blob Depolama
- Azure CosmosDB
- Azure Table Storage
- Cassandra
- Bulut Firestore (veri deposu modu)
- CloudState
- Couchbase
- Etcd
- HashiCorp Tüketil
- Tehlikeli elcast
- Memcached
- MongoDB
- PostgreSQL
- Redis
- RethinkDB
- SQL Server
- Zookeeper

Her bileşen ortak bir durum yönetimi arabirimi aracılığıyla gerekli uygulamayı sağlar:

```go
 type Store interface {
   Init(metadata Metadata) error
   Delete(req *DeleteRequest) error
   BulkDelete(req []DeleteRequest) error
   Get(req *GetRequest) (*GetResponse, error)
   Set(req *SetRequest) error
   BulkSet(req []SetRequest) error
}
```

> [!TIP]
> DAPR çalışma zamanının yanı sıra, tüm DAPR bileşenleri Golang 'de yazılmış veya Go dili. Git, açık kaynak topluluk genelinde popüler bir dildir ve platformlar arası bir Davpr taahhüdüne yönelik atmalar.

Belki de durum depolude Azure Redis Cache başlatabilirsiniz. Aşağıdaki yapılandırmayla belirtirsiniz:

 ```yaml
 apiVersion: dapr.io/v1alpha1
 kind: Component
 metadata:
   name: statestore
   namespace: default
 spec:
   type: state.redis
   version: v1
   metadata:
   - name: redisHost
     value: <HOST>
   - name: redisPassword
     value: <PASSWORD>
   - name: enableTLS
     value: <bool> # Optional. Allowed: true, false.
   - name: failover
     value: <bool> # Optional. Allowed: true, false.
 ```

**Spec** bölümünde, davpr 'yi durum yönetimi için Redis Cache kullanacak şekilde yapılandırırsınız. Bölüm bileşene özgü meta verileri de içerir. Bu durumda, ek Redu ayarlarını yapılandırmak için kullanabilirsiniz.

Daha sonraki bir zamanda uygulama üretime geçmeye hazırlanmaya devam edilir. Üretim ortamı için durum yönetiyi Azure Tablo depolama olarak değiştirmek isteyebilirsiniz. Azure Tablo depolama, ekonomik ve yüksek oranda dayanıklı olan durum yönetimi özellikleri sağlar.

Bu yazma sırasında, aşağıdaki bileşen türleri, Davpr tarafından sağlanır:

| Bileşen | Açıklama |
|-----------|-------------|
| [Hizmet bulma](https://github.com/dapr/components-contrib/tree/master/nameresolution) | Hizmet çağırma yapı bloğu tarafından hizmetten hizmete bulma sağlamak üzere barındırma ortamıyla tümleştirilecek şekilde kullanılır. |
| [Durum](https://github.com/dapr/components-contrib/tree/master/state) | , Çok çeşitli durum depolama uygulamalarıyla etkileşimde bulunmak için tekdüzen arabirimi sağlar. |
| [Pub/Sub](https://github.com/dapr/components-contrib/tree/master/pubsub) | Çok çeşitli ileti veri yolu uygulamalarıyla etkileşimde bulunmak için tekdüzen arabirimi sağlar. |
| [Bağlamalar](https://github.com/dapr/components-contrib/tree/master/bindings) | Dış sistemlerden uygulama olaylarını tetiklemek ve isteğe bağlı veri yükleri ile dış sistemleri çağırmak için tekdüzen arabirimi sağlar. |
| [Ara yazılım](https://github.com/dapr/components-contrib/tree/master/middleware) | Özel ara yazılım, istek işleme ardışık düzenine takılır ve bir istek ya da yanıt üzerinde ek eylemler çağırabilir. |
| [Gizli depolar](https://github.com/dapr/components-contrib/tree/master/secretstores) | Bulut, kenar, ticari ve açık kaynaklı hizmetler de dahil olmak üzere dış gizli depolarla etkileşim kurmak için tekdüzen arabirimi sağlar. |

Bu işlem, Jet 'in Davpr üzerinden tamamlanmasını tamamladıktan sonra bir kez daha görürsünüz ve nasıl birbirine bağlandığını görebilirsiniz.

### <a name="sidecar-architecture"></a>Sidecar mimarisi

Davpr, bir [sepet mimarisi](/azure/architecture/patterns/sidecar)aracılığıyla yapı taşlarını ve bileşenlerini sunar. Bir sepet, DAPR 'nin ayrı bir bellek işleminde veya hizmetinizdeki ayrı kapsayıcıda çalışmasına olanak sağlar. Sidecler, hizmetin bir parçası olmadıkları ve ona bağlı olduğu için yalıtım ve kapsülleme sağlar. Bu ayrım, her birinin kendi çalışma zamanı ortamına sahip olmasını ve farklı programlama platformları üzerinde oluşturulmuş olmasını sağlar. Şekil 2-4, bir sepet deseninin gösterildiği bir araç.

![Sidecar mimarisi](./media/dapr-at-20000-feet/sidecar-generic.png)

**Şekil 2-4**. Sidecar mimarisi.

Düzen, motosikletlere eklenen sepetlere benzediğinden sepet olarak adlandırılmıştır. Önceki şekilde, dağıtılmış uygulama özellikleri sağlamak için, vapr sepet 'nin hizmetinize nasıl eklendiği hakkında daha fazla.

### <a name="hosting-environments"></a>Barındırma ortamları

Davpr platformlar arası desteğe sahiptir ve birçok farklı ortamda çalışabilir. Bu ortamlar, Kubernetes, bir sanal makine grubu veya Azure IoT Edge gibi uç ortamları içerir.

Yerel geliştirme için, başlamak için en kolay yöntem [Şirket içinde barındırılan moddadır](https://docs.dapr.io/concepts/overview/#self-hosted). Şirket içinde barındırılan modda, mikro hizmetler ve Davpr 'ler, Kubernetes gibi bir kapsayıcı Düzenleyicisi olmadan ayrı yerel işlemlerde çalışır. Daha fazla bilgi için bkz. [Davpr CLI 'yı indirme ve yükleme](https://docs.dapr.io/getting-started/install-dapr/).

Şekil 2-5, HTTP veya gRPC aracılığıyla iletişim kuran iki ayrı bellek öğesinde barındırılan bir uygulamayı ve Davpr 'yi gösterir.

![Şirket içinde barındırılan sepet mimarisi](./media/dapr-at-20000-feet/self-hosted-dapr-sidecar.png)

**Şekil 2-5**. Şirket içinde barındırılan Davpr sidecar.

Varsayılan olarak, Davpr varsayılan durum yönetimi ve Observability sağlamak üzere Redsıs ve Zipkaları için Docker Kapsayıcıları yüklüyor. Docker 'ı yerel makinenize yüklemek istemiyorsanız, [herhangi bir Docker kapsayıcısı olmadan şirket içinde barındırılan modda da Dadpr 'yi çalıştırabilirsiniz](https://docs.dapr.io/operations/hosting/self-hosted/self-hosted-no-docker/). Ancak, el ile durum yönetimi ve Pub/Sub için varsayılan bileşenleri yüklemelisiniz.

Davpr, Kubernetes gibi [Kapsayıcılı ortamlarda](https://docs.dapr.io/concepts/overview/#kubernetes-hosted)da çalışır. Şekil 2-6, aynı Kubernetes Pod 'daki uygulama kapsayıcısının yanı sıra ayrı bir yan otomobil kapsayıcısında çalışan Davpr 'yi gösterir.

![Kubernetes-barındırılan sepet mimarisi](./media/dapr-at-20000-feet/kubernetes-hosted-dapr-sidecar.png)

**Şekil 2-6**. Kubernetes-barındırılan Davpr sidecar.

## <a name="dapr-performance-considerations"></a>Davpr performans konuları

Gördüğünüz gibi, Davpr, uygulamanızı dağıtılmış uygulama olanaklarından ayırmak için bir sepet mimarisi sunar. Bir Davpr işleminin çağrılması, en az bir işlem dışı ağ çağrısı gerektirir. Şekil 2-7, bir Davpr trafik deseninin bir örneğini gösterir.

![Davpr trafik desenleri](./media/dapr-at-20000-feet/dapr-traffic-patterns.png)

**Şekil 2-7**. Davpr trafik desenleri.

Önceki şekle bakarak, biri her çağrının gecikme süresini ve ek yükünü sormayabilir.  

Davpr ekibi çok fazla performansa yatırım yapmış. Yüksek miktarda mühendislik çabası, Davpr 'yi verimli hale getirmiştir. Her zaman, yüksek performans ve küçük ikili yükleri sunan gRPC ile Davpr sikileri arasındaki çağrılar yapılır. Çoğu durumda, ek yükün alt milisaniyelik olması gerekir.

Geliştiriciler, performansı artırmak için, gRPC ile Davpr derleme bloklarını çağırabilir.

gRPC, yaş-eski [uzak yordam çağrısı (RPC) protokolünü gelişten](https://en.wikipedia.org/wiki/Remote_procedure_call) modern ve yüksek performanslı bir çerçevedir. gRPC, HTTP Rekele hizmeti üzerinde önemli performans geliştirmeleri sağlayan Aktarım Protokolü için HTTP/2 kullanır:

- Aynı bağlantı üzerinden birden çok paralel istek göndermek için çoğullama desteği-HTTP 1,1, işleme bir kerede tek bir istek/yanıt iletisi ile sınırlar.
- Hem istemci isteklerini hem de sunucu yanıtlarını aynı anda göndermek için çift yönlü tam çift yönlü iletişim.
- Zaman uyumsuz akış büyük veri kümelerine yönelik istekleri ve yanıtları etkinleştiren yerleşik akış.

Daha fazla bilgi edinmek için, [Azure 'a yönelik Cloud-Native .NET uygulamaları](../cloud-native/index.md) mimarlarından [GRPC 'ye genel bakış](../cloud-native/grpc.md#what-is-grpc) konusunu inceleyin.  

## <a name="dapr-and-service-meshes"></a>Davpr ve hizmet kafesleri

Hizmet kafesi, dağıtılmış uygulamalar için hızlı bir şekilde gelişen bir teknolojidir.

Hizmet ağı, Service-Service iletişimini, dayanıklılığı, yük dengelemesini ve telemetri yakalamayı işlemeye yönelik yerleşik yeteneklere sahip yapılandırılabilir bir altyapı katmanıdır. Bu sorunlar için sorumluluğu, hizmetlerden ve hizmet kafes katmanında gider. Davpr gibi bir hizmet ağı da bir sepet mimarisini de izler.

Şekil 2-8, hizmet kafesi teknolojisini uygulayan bir uygulama gösterir.

![Hizmet ağı](./media/dapr-at-20000-feet/service-mesh-with-side-car.png)

**Şekil 2-8**. Yan otomobil olan hizmet ağı.

Önceki şekilde, iletilerin her bir hizmet ile birlikte çalışan bir sepet proxy tarafından nasıl ele alınacağını gösterir. Her proxy, hizmete özel trafik kurallarıyla yapılandırılabilir. İletileri anlamıştır ve bunları hizmetlerinize ve dış dünyaya yönlendirebilir.

Bu nedenle, "bir hizmet ağı KAPR mi?" sorusu haline gelir.

Her ikisi de bir sepet mimarisi kullanırken, her teknolojinin farklı bir amacı vardır. Davpr, dağıtılmış uygulama özellikleri sağlar. Hizmet ağı, özel bir ağ altyapısı katmanı sağlar.

Her biri farklı bir düzeyde çalışır, her ikisi de aynı uygulamada birlikte çalışabilir. Örneğin, bir hizmet ağı, hizmetler arasında ağ iletişimi sağlayabilir. Davpr, durum yönetimi veya aktör hizmetleri gibi uygulama hizmetleri sağlayabilir.

Şekil 2-9, hem Davpr hem de hizmet kafes teknolojisini uygulayan bir uygulama gösterir.

![PAPR ve hizmet ağı birlikte](./media/dapr-at-20000-feet/dapr-and-service-mesh.png)

**Şekil 2-9**. PAPR ve hizmet ağı birlikte.

[Davpr çevrimiçi belgeleri](https://docs.dapr.io/concepts/faq/#networking-and-service-meshes) , davpr ve hizmet ağı tümleştirmesini kapsar.

## <a name="summary"></a>Özet

Bu bölüm, dağıtılmış bir uygulama çalışma zamanı olan PAPR 'ye tanıtılmıştır.

Davpr, Microsoft tarafından müşterilerin ve açık kaynaklı topluluktaki yakın işbirliğiyle sponsorlu açık kaynaklı bir projem.

DAPR, en çekirdekli, dağıtılmış mikro hizmet uygulamalarının tüm karmaşıklığını azaltmaya yardımcı olur. Bu, blok API 'Leri oluşturmaya yönelik bir kavram üzerine kurulmuştur. Davpr oluşturma blokları, durum yönetimi, hizmetten hizmete çağrı ve yayın/alt mesajlaşma gibi yaygın olarak dağıtılmış uygulama yeteneklerini kullanıma sunar. Davpr bileşenleri, yapı taşlarının altına düştir ve her bir özellik için somut uygulama sağlar. Uygulamalar, yapılandırma dosyaları aracılığıyla çeşitli bileşenlere bağlanır.

Sonraki bölümlerde, uygulamalarınızda Davpr kullanma konusunda pratik, uygulamalı yönergeler sunuyoruz.

### <a name="references"></a>Başvurular

- [Davpr belgeleri](https://dapr.io/)
- [Öğrenme Davpr](https://www.amazon.com/Learning-Dapr-Building-Distributed-Applications/dp/1492072427/ref=sr_1_1?dchild=1&keywords=dapr&qid=1604794794&sr=8-1)
- [.NET mikro hizmetleri: Kapsayıcılı .NET uygulamaları için mimari](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)
- [Azure için Cloud-Native .NET uygulamaları tasarlama](https://dotnet.microsoft.com/download/e-book/cloud-native-azure/pdf)

> [!div class="step-by-step"]
> [Önceki](the-world-is-distributed.md) 
>  [Sonraki](getting-started.md)
