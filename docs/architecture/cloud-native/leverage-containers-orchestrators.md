---
title: Kapsayıcılardan ve düzenleyicilerden yararlanma
description: Azure 'da Docker kapsayıcılarını ve Kubernetes düzenleyicilerinden yararlanın
ms.date: 06/30/2019
ms.openlocfilehash: 7b136ed2760ea471f42ff82d20298ff8714c6dee
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73087229"
---
# <a name="leveraging-containers-and-orchestrators"></a>Kapsayıcılardan ve düzenleyicilerden yararlanma

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kapsayıcılar ve düzenleyiciler, tek parçalı dağıtım yaklaşımları için ortak olan sorunları çözmeye yönelik olarak tasarlanmıştır.

## <a name="challenges-with-monolithic-deployments"></a>Tek parçalı dağıtımlar ile ilgili sorunlar

Geleneksel olarak, çoğu uygulama tek bir birim olarak dağıtılır. Bu tür uygulamalar tek bir olarak adlandırılır. Bu genel yaklaşım, birden çok modülden oluşsa bile veya derlemeler şekil 3-1 ' de gösterildiği gibi tek parçalı mimari olarak bilinir.

![Tek parçalı mimari.](./media/monolithic-architecture.png)

**Şekil 3-1**. Tek parçalı mimari.

Basitlik avantajlarına sahip olsalar da tek parçalı mimarilerin bir dizi zorluk yüzü vardır:

### <a name="deployments"></a>Dağıtımlar

Tek parçalı uygulamalara dağıtım, genellikle yalnızca bir küçük modül değiştirilse bile tüm uygulamanın yeniden başlatılmasını gerektirir. Uygulamayı barındıran makinelerin sayısına bağlı olarak, bu, dağıtımlar sırasında kapalı kalma süresine yol açabilir.

### <a name="hosting"></a>Barındırma

Tek parçalı uygulamalar tamamen tek bir makine örneğinde barındırılır. Bu, dağıtılmış bir uygulamadaki herhangi bir modülün gerek duyduğu daha yüksek yetenek donanımlar gerektirebilir. Ayrıca, uygulamanın herhangi bir bölümü bir performans sorunu haline gelirse, genişletmek için tüm uygulamanın ek makine düğümlerine dağıtılması gerekir.

### <a name="environment"></a>Ortam

Tek parçalı uygulamalar, genellikle mevcut bir barındırma ortamına (işletim sistemi, yüklü çerçeveler vb.) dağıtılır. Bu ortam, uygulamanın geliştirildiği veya test ettiği ortamla eşleşmeyebilir. Uygulamanın ortamındaki tutarsızlıklar, tek parçalı dağıtımlar için ortak bir sorun kaynağıdır.

### <a name="coupling"></a>Bağlantısı

Tek parçalı uygulamalar, uygulamanın farklı parçaları arasında ve uygulama ile ortamı arasında çok büyük bir çışa sahiptir. Bu, belirli bir hizmeti daha sonra veya daha sonra bir diğer uygulamada ölçeklenebilirlik veya takas etmek için bir veya daha fazla sorun yaşamamayı zorlaştırır. Bu, aynı zamanda sistemde yapılan değişiklikler için büyük olasılıkla büyük uygulamalarda çok daha büyük etkileri olmasına yol açar.

### <a name="technology-choice"></a>Teknoloji seçimi

Tek parçalı uygulamalar, birim olarak oluşturulup dağıtılır. Bu, basitlik ve uygunluk olanakları sunar, ancak yenilik için bir engel olabilir. Sistemdeki yeni bir özellik veya modül daha modern bir platforma veya çerçeveye daha iyi uygun olsa da, uygulamanın tutarlılığının yanı sıra geliştirme ve dağıtım kolaylığı için uygulamanın geçerli yaklaşımı kullanılarak oluşturulmuştur.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Kapsayıcıların ve düzenleyicilerinin avantajları nelerdir?

Docker, en popüler kapsayıcı yönetimi ve görüntüleme platformudur ve Linux ve Windows üzerinde kapsayıcılarla hızlı bir şekilde çalışmanıza olanak sağlar. Kapsayıcılar, her sistemde aynı şekilde çalışan ayrı ancak tekrarlanabilir uygulama ortamları sağlar. Bu, bulut Yerel uygulamalarında uygulamalar ve uygulama bileşenleri geliştirmek ve barındırmak için idealdir. Kapsayıcılar birbirinden yalıtılmıştır, bu nedenle aynı konak donanımında iki kapsayıcı, çakışmaya neden olan bağımlılıklar olmadan farklı yazılım sürümlerine ve hatta işletim sistemine sahip olabilir.

Diğer özellikler, kapsayıcılar kaynak denetimine denetlenebilecekleri basit dosyalar tarafından tanımlanır. Tam sunuculardan farklı olarak, güncelleştirmeleri uygulamak veya ek hizmetleri yüklemek için sık olarak çalışan sanal makineler olsa bile kapsayıcı altyapısı kolayca sürüm denetimli olabilir. Bu nedenle, kapsayıcılarda çalışmak üzere oluşturulan uygulamalar, derleme işlem hattının bir parçası olarak otomatikleştirilmiş araçlar kullanılarak geliştirilebilir, test edilebilir ve dağıtılabilir.

Kapsayıcılar sabittir. Bir kapsayıcının tanımına sahip olduktan sonra, bu kapsayıcıyı yeniden oluşturabilirsiniz ve tam olarak aynı şekilde çalışır. Bu, bu şekilde bileşen tabanlı tasarıma yönelik olarak kullanılabilirlik sağlar. Bir uygulamanın bazı bölümleri başkaları kadar sık değişmemekle karşılaşmıyorsanız, en sık değiştiren parçaları yalnızca dağıtırken uygulamanın tamamını yeniden dağıtmanız gerekir mi? Bir uygulamanın farklı özellikleri ve çapraz kesme sorunları ayrı birimlere ayrılabilir. Şekil 3-2, tek parçalı bir uygulamanın belirli özellikler veya işlevler için kapsayıcılardan ve mikro hizmetlerden nasıl yararlanabileceğiz gösterir. Uygulamanın kendisindeki diğer işlevsellik de Kapsayıcılı hale getirilir.

arka uçta mikro hizmetleri kullanmak için tek parçalı bir uygulamayı bölmek ![. **şekil 3-2**](./media/breaking-up-monolith-with-backend-microservices.png)
. Arka uçta mikro hizmetleri kullanmak için tek parçalı bir uygulamayı bölmek.

Ayrı kapsayıcılar kullanılarak oluşturulan bulutta yerel uygulamalar, bir uygulamanın gerektirdiği kadar çok veya büyük bir şekilde dağıtılması özelliğinden yararlanır. Her hizmet için uygun kaynakları olan düğümlerde tek tek hizmetler barındırılabilir. Her hizmetin çalıştığı ortam sabittir, geliştirme, test ve üretim arasında paylaşılabilir ve kolayca sürümlenebilir. Uygulamanın farklı alanlarında, tek başına derleme zamanı bağımlılıkları değil, hizmetler arasında doğrudan çağrı veya ileti olarak gerçekleştirilir. Uygulamanın geri kalanında değişiklik gerektirmeden bu özellik veya beceri için en mantıklı bir teknoloji sunan teknolojiyi seçebilir.

## <a name="what-are-the-scaling-benefits"></a>Ölçeklendirme avantajları nelerdir?

Kapsayıcılarda oluşturulan hizmetler, Kubernetes gibi Orchestration araçları tarafından sunulan ölçeklendirme avantajlarından yararlanabilir. Tasarım kapsayıcıları tarafından yalnızca kendileri hakkında bilgi sahibi. Birlikte çalışması gereken birden çok kapsayıcıyla çalışmaya başladıktan sonra, bunları daha yüksek bir düzeyde düzenlemek biraz zaman alabilir. Çok sayıda kapsayıcıyı ve ağ yapılandırması gibi paylaşılan bağımlılıklarını organize etmek, düzenleme araçlarının günü kaydetmek için nereden geldiği yerdir! Kubernetes, Kapsayıcılı uygulamaların dağıtımını, ölçeklendirilmesini ve yönetimini otomatikleştirmek için tasarlanan bir kapsayıcı düzenleme platformudur. Kapsayıcı gruplarının üstünde bir soyutlama katmanı oluşturur ve bunları *Pod*olarak düzenler. *Düğüm*olarak adlandırılan çalışan makinelerdeki pods çalıştırılır. Tüm düzenlenmiş Grup, *küme*olarak adlandırılır. Şekil 3-3, bir Kubernetes kümesinin farklı bileşenlerini gösterir.

Kubernetes küme bileşenlerini ![. **şekil 3-3**](./media/kubernetes-cluster-components.png)
. Kubernetes kümesi bileşenleri.

Kubernetes, talepleri karşılamak için kümeleri ölçeklendirmeye yönelik yerleşik destek içerir. Kapsayıcılı mikro hizmetlerle birleştirilmiş bu, bulutta yerel uygulamalar sağlar ve gerektiğinde ek kaynaklarla isteğe bağlı ani artışlar hızla ve verimli bir şekilde yanıtlayabilir.

### <a name="declarative-versus-imperative"></a>Bildirime dayalı ve kesinlik

Kubernetes hem bildirime dayalı hem de kesinlik temelli nesne yapılandırmasını destekler. Zorunlu yaklaşım, Kubernetes 'in her adımın nasıl yapılacağını söyleyen çeşitli komutları çalıştırmayı içerir. Bu görüntüyü *çalıştırın* . Bu Pod öğesini *silin* . Bu bağlantı noktasını *kullanıma sunun* . Bildirim temelli yaklaşımla, *ne yapmak* yerine *istediğinizi* açıklayan bir yapılandırma dosyası kullanırsınız ve Kubernetes istenen bitiş durumuna ulaşmak için ne yapılacağını tanımlar. Kümenizi zaten zorunlu komutları kullanarak yapılandırdıysanız, `kubectl get svc SERVICENAME -o yaml > service.yaml`kullanarak bildirime dayalı bir bildirimi dışarı aktarabilirsiniz. Bu, şunun gibi bir bildirim dosyası oluşturur:

```yaml
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: "2019-09-13T13:58:47Z"
  labels:
    component: apiserver
    provider: kubernetes
  name: kubernetes
  namespace: default
  resourceVersion: "153"
  selfLink: /api/v1/namespaces/default/services/kubernetes
  uid: 9b1fac62-d62e-11e9-8968-00155d38010d
spec:
  clusterIP: 10.96.0.1
  ports:
  - name: https
    port: 443
    protocol: TCP
    targetPort: 6443
  sessionAffinity: None
  type: ClusterIP
status:
  loadBalancer: {}
```

Bildirim temelli yapılandırma kullanırken, yapılandırma dosyalarınızın bulunduğu klasöre karşı `kubectl diff -f FOLDERNAME` kullanarak uygulamadan önce yapılacak değişiklikleri önizleyebilirsiniz. Değişiklikleri uygulamak istediğinize emin olduktan sonra `kubectl apply -f FOLDERNAME`çalıştırın. Bir klasör hiyerarşisini yinelemeli olarak işlemek için `-R` ekleyin.

Hizmetlere ek olarak, *dağıtımlar*gibi diğer Kubernetes özellikleri için bildirim temelli yapılandırma kullanabilirsiniz. Bildirim temelli dağıtımlar, dağıtım denetleyicileri tarafından küme kaynaklarını güncelleştirmek için kullanılır. Dağıtımlar yeni değişiklikleri almak, daha fazla yük desteklemek üzere ölçeği genişletmek veya önceki bir düzeltmeye geri dönmek için kullanılır. Bir küme kararsız durumdaysa, bildirim temelli dağıtımlar otomatik olarak kümeyi istenen bir duruma getirmek için bir mekanizma sağlar.

Bildirim temelli yapılandırma kullanmak, altyapının uygulama kodu ile birlikte denetlenebilen ve sürümü oluşturulmuş bir kod olarak temsil etmesine olanak tanır. Bu, geliştirilmiş değişiklik denetimi ve kaynak denetim değişikliklerine bağlı bir yapı ve dağıtım işlem hattı kullanarak sürekli dağıtım için daha iyi destek sağlar.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Kapsayıcılar ve düzenleyiciler için hangi senaryolar idealdir?

Aşağıdaki senaryolar kapsayıcıları ve düzenlemeleri kullanmak için idealdir.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Yüksek çalışma süresi ve ölçeklenebilirlik gerektiren uygulamalar

Yüksek çalışma süresi ve ölçeklenebilirlik gereksinimleri olan bireysel uygulamalar, mikro hizmetler, kapsayıcılar ve düzenleyicilerin kullanıldığı bulutta yerel mimariler için ideal adaylardır. Bu uygulamalar, sürümlü ortamlar kullanılarak kapsayıcılarda geliştirilebilir, üretime geçmeden önce kapsamlı bir şekilde test edilebilir ve sıfır kapalı kalma süresiyle üretime dağıtılabilir. Kubernetes kümelerinin kullanımı, bu tür uygulamaların talep üzerine ölçeklenmesini ve düğüm hatalarından otomatik olarak kurtarılmasını sağlar.

### <a name="large-numbers-of-applications"></a>Çok sayıda uygulama

Ve daha sonra kapsayıcılardan ve düzenleyicilerinden çok sayıda uygulama avantajı olması gereken kuruluşlar. Kapsayıcılı ortamları ve Kubernetes kümelerini ayarlamanın en ön çabası, birincil olarak sabit bir maliyettir. Bireysel uygulamaların dağıtımı, bakımını yapma ve güncelleştirme, sürdürülmesi gereken uygulama sayısına göre farklılık gösteren bir maliyettir. Belirli bir oldukça az sayıda uygulamanın ötesinde, özel uygulamaların korunmasının karmaşıklığı kapsayıcıları ve düzenlemeleri kullanarak bir çözüm uygulama masrafını aşmaktadır.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Kapsayıcıları ve düzenlemeleri kullanmaktan ne zaman kaçınmalısınız?

Uygulamanızı, on Iki öğeli uygulama prensipini takip etmek veya derlemenize izin vermenizdir, büyük olasılıkla kapsayıcılardan ve düzenleyicilerinden Kaçınmaktan daha iyi bir şekilde başlayacaksınız. Bu gibi durumlarda, belirli işlevsellik parçalarını ayrı kapsayıcılara veya hatta sunucusuz işlevlere taşıyabilmeniz için bir VM tabanlı barındırma platformu veya belki de büyük olasılıkla bir karma sistemle ilerlemek en iyi hale gelebilir.

## <a name="development-resources"></a>Geliştirme kaynakları

Bu bölümde, bir sonraki uygulamanız için kapsayıcıları ve düzenlemeleri kullanmaya başlamanıza yardımcı olabilecek geliştirme kaynaklarının kısa bir listesi gösterilmektedir. Bulut Yerel mikro hizmetleri mimari uygulamanızı nasıl tasarlayacağımızı öğrenmek istiyorsanız bu kitabın yardımcı, [.net mikro hizmetleri: Kapsayıcılı .NET uygulamaları Için mimari](https://aka.ms/microservicesebook)makalesini okuyun.

### <a name="local-kubernetes-development"></a>Yerel Kubernetes geliştirme

Kubernetes dağıtımları üretim ortamlarında harika bir değer sağlar, ancak bunları yerel olarak da çalıştırabilirsiniz. Çoğu zaman ayrı uygulamalarda veya mikro hizmetlerde bağımsız olarak çalışabilmeniz için oldukça iyi olabiliyor olsa da, bazen üretime dağıtıldığında çalıştırılacak şekilde tüm sistemi yerel olarak çalıştırabilmenizde yarar vardır. Bunu yapmanın birkaç yolu vardır, ikisi de Minikube ve Docker Desktop. Visual Studio, Docker geliştirmesi için de araç sağlar.

### <a name="minikube"></a>Minikube

Minikube nedir? Minikube projesi, "Minikube macOS, Linux ve Windows üzerinde yerel bir Kubernetes kümesi uygular" diyor. Birincil hedefleri, "yerel Kubernetes uygulama geliştirmesi için en iyi araç olacak ve sığan Kubernetes özelliklerini desteklemeye yöneliktir." Minikube yükleme Docker 'dan ayrıdır, ancak Minikube, Docker Desktop 'ın desteklediğinden farklı hiper yöneticileri destekler. Aşağıdaki Kubernetes özellikleri şu anda Minikube tarafından desteklenmektedir:

- DNS
- NodePorts
- ConfigMaps ve gizlilikler
- Panolar
- Kapsayıcı çalışma zamanları: Docker, RKT, CRı-O ve containerd
- Kapsayıcı ağ arabirimini etkinleştirme (CNı)
- Giriş

Minikube yükledikten sonra, bir görüntüyü indiren ve yerel Kubernetes kümesini Başlatan `minikube start` komutunu çalıştırarak hızlı bir şekilde kullanmaya başlayabilirsiniz. Küme başlatıldıktan sonra, standart Kubernetes `kubectl` komutlarını kullanarak onunla etkileşime geçin.

### <a name="docker-desktop"></a>Docker Masaüstü

Ayrıca, Kubernetes ile doğrudan Windows 'daki Docker Desktop 'tan da çalışabilirsiniz. Windows kapsayıcıları kullanıyorsanız bu tek seçenektir ve Windows olmayan kapsayıcılar için harika bir seçimdir. Docker Desktop 'tan çalışan Kubernetes 'i yapılandırmak için standart Docker Desktop yapılandırma uygulaması kullanılır.

![Docker Desktop 'ta Kubernetes 'i yapılandırma](./media/docker-desktop-kubernetes.png)

**Şekil 3-4**. Docker Desktop 'ta Kubernetes 'i yapılandırma.

Docker Desktop, Kapsayıcılı uygulamaları yerel olarak yapılandırmak ve çalıştırmak için en popüler araç olan bir araçtır. Docker Desktop ile çalışırken, üretime dağıtacağınız Docker kapsayıcı görüntüleri kümesine göre yerel olarak geliştirme yapabilirsiniz. Docker Desktop, Kapsayıcılı uygulamaları yerel olarak derlemek, test etmek ve teslim etmek üzere tasarlanmıştır. Görüntüler Azure Container Registry veya Docker Hub gibi bir görüntü kayıt defterine gönderildikten sonra Azure Kubernetes hizmeti (AKS) gibi hizmetler üretimde uygulamayı yönetir.

### <a name="visual-studio-docker-tooling"></a>Visual Studio Docker Araçları

Visual Studio, Web uygulamaları için Docker geliştirmeyi destekler. Yeni bir ASP.NET Core uygulaması oluşturduğunuzda, Şekil 3-5 ' de gösterildiği gibi, proje oluşturma işleminin bir parçası olarak onu Docker desteğiyle yapılandırma seçeneği sunulur.

![Visual Studio Docker desteğini etkinleştir](./media/visual-studio-enable-docker-support.png)

**Şekil 3-5**. Visual Studio Docker desteğini etkinleştir

Bu seçenek belirlendiğinde, proje kökünde bir `Dockerfile` oluşturulur ve bu, uygulamayı bir Docker kapsayıcısında derlemek ve barındırmak için kullanılabilir. Şekil 3-6 ' de örnek Dockerfile gösterilmektedir.

```docker
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-stretch AS build
WORKDIR /src
COPY ["WebApplication3/WebApplication3.csproj", "WebApplication3/"]
RUN dotnet restore "WebApplication3/WebApplication3.csproj"
COPY . .
WORKDIR "/src/WebApplication3"
RUN dotnet build "WebApplication3.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication3.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication3.dll"]
```

**Şekil 3-6**. Visual Studio tarafından oluşturulan Dockerfile

Uygulamanın çalışması için varsayılan davranış, Docker 'ı kullanmak üzere yapılandırılmıştır. Şekil 3-7, Docker desteği eklenmiş şekilde oluşturulan yeni bir ASP.NET Core projesinden kullanılabilir farklı çalıştırma seçeneklerini gösterir.

![Visual Studio Docker çalıştırma seçenekleri](./media/visual-studio-docker-run-options.png)

**Şekil 3-7**. Visual Studio Docker çalıştırma seçenekleri

[Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) , yerel geliştirmeye ek olarak, birden çok geliştiricinin Azure 'Da kendi Kubernetes yapılandırmalarına göre çalışması için kullanışlı bir yol sağlar. Şekil 3-7 ' de görebileceğiniz gibi, uygulamayı Azure Dev Spaces de çalıştırabilirsiniz.

ASP.NET Core uygulamanıza Docker desteği eklememeniz durumunda, daha sonra her zaman ekleyebilirsiniz. Visual Studio Çözüm Gezgini, Şekil 3-8 ' de gösterildiği gibi projeye sağ tıklayın ve > **Docker desteği** **Ekle** ' yi seçin.

![Visual Studio Docker desteği ekle](./media/visual-studio-add-docker-support.png)

**Şekil 3-8**. Visual Studio Docker desteği ekle

Docker desteğinin yanı sıra, Şekil 3-8 ' de de gösterilen kapsayıcı düzenleme desteğini de ekleyebilirsiniz. Varsayılan olarak Orchestrator, Kubernetes ve Held kullanır. Orchestrator 'ı seçtikten sonra proje köküne bir `azds.yaml` dosyası eklenir ve uygulamayı yapılandırmak ve Kubernetes 'e dağıtmak için kullanılan helk grafiklerini içeren bir `charts` klasörü eklenir. Şekil 3-9 yeni bir projedeki sonuç dosyalarını gösterir.

![Visual Studio Orchestrator desteği ekle](./media/visual-studio-add-orchestrator-support.png)

**Şekil 3-9**. Visual Studio Orchestrator desteği ekle

## <a name="references"></a>Referanslar

- [Kubernetes nedir?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Minikube ile Kubernetes yükleme](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube vs Docker Masaüstü](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Docker için Visual Studio Araçları](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[Önceki](scale-applications.md)
>[İleri](leverage-serverless-functions.md)
