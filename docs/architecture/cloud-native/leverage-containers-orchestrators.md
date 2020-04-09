---
title: Kapsayıcılardan ve düzenleyicilerden yararlanma
description: Azure'da Docker Konteynerleri ve Kubernetes Orkestratörlerinden Yararlanma
ms.date: 06/30/2019
ms.openlocfilehash: 44b2fff8c9c88717d83e41a421b9817e2cc68135
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989044"
---
# <a name="leveraging-containers-and-orchestrators"></a>Kapsayıcılardan ve düzenleyicilerden yararlanma

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Konteynerler ve orkestratörler, yekpare dağıtım yaklaşımlarında yaygın olan sorunları çözmek için tasarlanmıştır.

## <a name="challenges-with-monolithic-deployments"></a>Yekpare dağıtımlarla ilgili zorluklar

Geleneksel olarak, çoğu uygulama tek bir birim olarak dağıtılmıştır. Bu tür uygulamalar monolit olarak adlandırılır. Uygulamaları birden fazla modül veya derlemeden oluşsalar bile tek birim olarak dağıtmanın bu genel yaklaşımı, Şekil 3-1'de gösterildiği gibi yekpare mimari olarak bilinir.

![Yekpare mimari.](./media/monolithic-architecture.png)

**Şekil 3-1**. Yekpare mimari.

Basitlik avantajına sahip olmalarına rağmen, yekpare mimariler bir takım zorluklarla karşı karşıyadır:

### <a name="deployments"></a>Dağıtımlar

Yekpare uygulamalara dağıtım genellikle, yalnızca küçük bir modül değiştirilse bile, tüm uygulamanın yeniden başlatılmasını gerektirir. Uygulamayı barındıran makine sayısına bağlı olarak, bu dağıtımlar sırasında kapalı kalma süresine neden olabilir.

### <a name="hosting"></a>Barındırma

Monolitik uygulamalar tamamen tek bir makine örneğinde barındırılır. Bu, dağıtılmış bir uygulamadaki herhangi bir modülün ihtiyaç duyduğundan daha yüksek özellikli donanım gerektirebilir. Ayrıca, uygulamanın herhangi bir bölümü darboğaza dönüşürse, ölçeklendirmek için uygulamanın tamamının ek makine düğümlerine dağıtılması gerekir.

### <a name="environment"></a>Ortam

Monolitik uygulamalar genellikle varolan bir barındırma ortamına (işletim sistemi, yüklü çerçeveler, vb.) dağıtılır. Bu ortam, uygulamanın geliştirildiği veya test edildiği ortamla eşleşmeyebilir. Uygulamanın ortamındaki tutarsızlıklar, yekpare dağıtımlar için sık karşılaşılan bir sorun kaynağıdır.

### <a name="coupling"></a>Kaplin

Monolitik uygulamaların, uygulamanın farklı bölümleri ile uygulama ile çevresi arasında büyük bir bağlantı yada ması olasıdır. Bu, belirli bir hizmeti veya endişeyi daha sonra, ölçeklenebilirliğini artırmak veya alternatif bir uygulamada takas etmek için hesaba katmayı zorlaştırabilir. Bu bağlantı aynı zamanda sistem değişiklikleri için çok daha büyük potansiyel etkilere yol açar, daha büyük uygulamalarda kapsamlı test gerektiren.

### <a name="technology-choice"></a>Teknoloji seçimi

Monolitik uygulamalar bir birim olarak oluşturulur ve dağıtılır. Bu basitlik ve tekdüzelik sunuyor ama yenilik için bir engel olabilir. Sistemdeki yeni bir özellik veya modül daha modern bir platform veya çerçeveye daha uygun olsa da, tutarlılık ve dağıtım kolaylığı açısından uygulamanın mevcut yaklaşımı kullanılarak oluşturulabilir.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Konteynerlerin ve orkestratörlerin faydaları nelerdir?

Docker en popüler konteyner yönetimi ve görüntüleme platformudur ve Linux ve Windows'daki konteynerlerle hızlı bir şekilde çalışmanızı sağlar. Kapsayıcılar, herhangi bir sistemde aynı şekilde çalışan ayrı ancak tekrarlanabilir uygulama ortamları sağlar. Bu, bulut ayarı uygulamalarda uygulamaları ve uygulama bileşenlerini geliştirmek ve barındırmak için onları mükemmel hale getirir. Kapsayıcılar birbirinden izole edilir, bu nedenle aynı ana bilgisayar donanımındaki iki kapsayıcı, çakışmalara neden olan bağımlılıklar olmadan yazılımın ve hatta işletim sisteminin farklı sürümlerine sahip olabilir.

Dahası, kapsayıcılar kaynak denetimine denetlenebilir basit dosyalar tarafından tanımlanır. Tam sunucuların aksine, güncellemeleri uygulamak veya ek hizmetler yüklemek için sık sık manuel çalışma gerektiren sanal makineler bile, konteyner altyapısı kolayca sürüm kontrollü olabilir. Böylece, kapsayıcılarda çalışacak şekilde oluşturulmuş uygulamalar geliştirilebilir, sınanabilir ve otomatik araçlar kullanılarak bir yapı boru hattının parçası olarak dağıtılabilir.

Konteynerler değişmez. Bir kapsayıcıtanımına sahip olduğunuzda, bu kapsayıcıyı yeniden oluşturabilirsiniz ve bu kapsayıcı tam olarak aynı şekilde çalışır. Bu değişmezlik, bileşen tabanlı tasarıma kendini verir. Bir uygulamanın bazı bölümleri diğerleri kadar sık değişmiyorsa, en sık değişen bölümleri dağıtabilecekken neden uygulamanın tamamını yeniden dağıtın? Bir uygulamanın farklı özellikleri ve çapraz kesme endişeleri ayrı birimlere ayrılabilir. Şekil 3-2, yekpare bir uygulamanın belirli özellikleri veya işlevleri atayarak kapsayıcılardan ve mikro hizmetlerden nasıl yararlanabileceğini gösterir. Uygulamanın kendisinde kalan işlevsellik de kapsayıcı olmuştur.

![Arka uçta mikro hizmetleri kullanmak için yekpare bir uygulamayı kırmak. ](./media/breaking-up-monolith-with-backend-microservices.png)
 **Şekil 3-2**. Arka uçta mikro hizmetleri kullanmak için yekpare bir uygulamayı kırmak.

Ayrı kapsayıcılar kullanılarak oluşturulmuş bulut tabanlı uygulamalar, bir uygulamayı gerektiği kadar veya az dağıtabilme özelliğinden yararlanır. Tek tek hizmetler, her hizmete uygun kaynaklara sahip düğümler üzerinde barındırılabilir. Her hizmetin çalıştığı ortam değişmezdir, dev, test ve üretim arasında paylaşılabilir ve kolayca sürülebilir. Uygulamanın farklı alanları arasında bağlantı açıkça aramalar veya iletiler arasında hizmetler arasında değil, monolit içinde zaman bağımlılıkları derlemek olarak oluşur. Ve genel uygulamanın herhangi bir bölümü, uygulamanın geri kalanında değişiklik gerektirmeden bu özellik veya özellik için en mantıklı teknolojiyi seçebilir.

## <a name="what-are-the-scaling-benefits"></a>Ölçeklemenin faydaları nelerdir?

Konteynerler üzerine inşa edilen hizmetler, Kubernetes gibi düzenleme araçlarının sağladığı ölçekleme avantajlarından yararlanabilir. Tasarım kapları sadece kendilerini biliyorum. Birlikte çalışması gereken birden çok kapsayıcıya sahip olmaya başladığınızda, bunları daha yüksek bir düzeyde düzenlemeye değebilir. Çok sayıda kapsayıcıyı ve ağ yapılandırması gibi paylaşılan bağımlılıklarını organize etmek, orkestrasyon araçlarının günü kurtarmak için geldiği yerdir! Kubernetes, konteyner uygulamalarının dağıtımını, ölçeklemesini ve yönetimini otomatikleştirmek için tasarlanmış bir konteyner düzenleme platformudur. Kapsayıcı gruplarının üzerine bir soyutlama katmanı oluşturur ve bunları *bölmeler*halinde düzenler. Bölmeler *düğüm*olarak adlandırılan işçi makinelerinde çalışır. Tüm organize grup *küme*olarak adlandırılır. Şekil 3-3 bir Kubernetes kümesinin farklı bileşenlerini gösterir.

![Kubernetes küme bileşenleri. ](./media/kubernetes-cluster-components.png)
 **Şekil 3-3**. Kubernetes küme bileşenleri.

Kubernetes, talebi karşılamak için kümeleri ölçekleme için yerleşik destek lemiştir. Kapsayıcı mikro hizmetlerle birlikte, bulut yerel uygulamalara ihtiyaç duyulduğunda ve nerede ihtiyaç duyulduğunda ek kaynaklarla talepteki ani artışlara hızlı ve verimli bir şekilde yanıt verebilme olanağı sağlar.

### <a name="declarative-versus-imperative"></a>Bildirimsel karşı zorunluluk

Kubernetes hem bildirimsel hem de zorunlu nesne yapılandırmadestekler. Zorunlu yaklaşım, Kubernetes'e her adımda ne yapması gerektiğini söyleyen çeşitli komutlar çalıştırmayı içerir. Bu görüntüyü *çalıştırın.* Bu bölmeyi *silin.* Bu bağlantı noktasını *ortaya çıkar.* Bildirimsel yaklaşımla, *ne yapmanız* yerine *ne istediğinizi* açıklayan bir yapılandırma dosyası kullanırsınız ve Kubernetes istenen bitiş durumuna ulaşmak için ne yapmanız gerektiğini bulur. Kümenizi zorunlu komutları kullanarak zaten yapılandırıldıysanız, 'yi kullanarak bir `kubectl get svc SERVICENAME -o yaml > service.yaml`bildirim bildirimi dışa aktarabilirsiniz. Bu, bunun gibi bir manifesto dosyası üretecektir:

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

Bildirimsel yapılandırmayı kullanırken, yapılandırma dosyalarınızın bulunduğu klasöre karşı `kubectl diff -f FOLDERNAME` kullanarak bunları işlemeden önce yapılacak değişiklikleri önizleyebilirsiniz. Değişiklikleri uygulamak istediğinizden emin olduktan sonra `kubectl apply -f FOLDERNAME`çalıştırın. Bir `-R` klasör hiyerarşisi özyinelemeli olarak işlemek için ekleyin.

Hizmetlere ek olarak, *dağıtımlar*gibi diğer Kubernetes özellikleri için bildirimsel yapılandırma kullanabilirsiniz. Bildirimsel dağıtımlar, küme kaynaklarını güncelleştirmek için dağıtım denetleyicileri tarafından kullanılır. Dağıtımlar yeni değişiklikleri kullanıma çıkarmak, daha fazla yükü desteklemek için ölçeklendirmek veya önceki bir düzeltmeye geri dönmek için kullanılır. Bir küme kararsızsa, bildirimsel dağıtımlar kümeyi otomatik olarak istenilen duruma geri getirmek için bir mekanizma sağlar.

Bildirimsel yapılandırmanın kullanılması, altyapının uygulama koduyla birlikte iade edilebilen ve sürümlendirilebilen kod olarak temsil edilmesine olanak tanır. Bu, kaynak denetimi değişikliklerine bağlı bir yapı ve dağıtım ardışık hattını kullanarak sürekli dağıtım için gelişmiş değişim denetimi ve daha iyi destek sağlar.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Konteynerler ve orkestrasyonlar için hangi senaryolar idealdir?

Aşağıdaki senaryolar kapsayıcılar ve orkestratörler kullanmak için idealdir.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Yüksek çalışma süresi ve ölçeklenebilirlik gerektiren uygulamalar

Yüksek çalışma süresi ve ölçeklenebilirlik gereksinimleri olan bireysel uygulamalar, mikro hizmetler, kapsayıcılar ve orkestratörler kullanarak bulut yerel mimariler için ideal adaylardır. Bu uygulamalar, sürümlü ortamlar kullanılarak kaplarda geliştirilebilir, üretime geçmeden önce kapsamlı bir şekilde test edilebilir ve sıfır kesintiyle üretime dağıtılabilir. Kubernetes kümelerinin kullanımı, bu tür uygulamaların isteğe bağlı olarak ölçeklendirilebilmesini ve düğüm hatalarından otomatik olarak kurtarabilmesini sağlar.

### <a name="large-numbers-of-applications"></a>Çok sayıda uygulama

Çok sayıda uygulamayı dağıtan ve daha sonra muhafaza etmesi gereken kuruluşlar kapsayıcılardan ve orkestratörlerden yararlanır. Kapsayıcı ortamlar ve Kubernetes kümeleri kurma ön çaba öncelikle sabit bir maliyettir. Tek tek uygulamaları dağıtma, sürdürme ve güncelleştirmenin, bakımı gereken uygulama sayısına göre değişen bir maliyeti vardır. Belirli bir oldukça az sayıda uygulamanın ötesinde, özel uygulamaları elle korumanın karmaşıklığı, kapsayıcılar ve orkestratörler kullanarak bir çözümü uygulama maliyetini aşıyor.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Konteynerleri ve orkestratörleri kullanmaktan ne zaman kaçınmalısınız?

On iki faktörlü uygulama ilkelerine uygun olarak uygulamanızı oluşturmak istemiyor sanız veya yapamıyorsanız, konteynerlerden ve orkestratörlerden kaçınmanız daha iyi olacaktır. Bu gibi durumlarda, vm tabanlı bir barındırma platformu veya muhtemelen bazı işlevsellik parçalarını ayrı kapsayıcılara ve hatta sunucusuz işlevlere dönüştürebileceğiniz bir karma sistemle ilerlemek en iyisi olabilir.

## <a name="development-resources"></a>Geliştirme kaynakları

Bu bölümde, bir sonraki uygulamanız için kapsayıcılar ve orkestratörler kullanmaya başlamanıza yardımcı olabilecek geliştirme kaynaklarının kısa bir listesi gösterilmektedir. Bulut-yerel mikrohizmetler mimari uygulamanızı nasıl tasarladığınıza ilişkin rehberlik arıyorsanız, bu kitabın arkadaşı [.NET Microservices: Architecture for Containerized .NET Applications](https://aka.ms/microservicesebook)'ı okuyun.

### <a name="local-kubernetes-development"></a>Yerel Kubernetes Geliştirme

Kubernetes dağıtımları üretim ortamlarında büyük değer sağlar, ancak bunları yerel olarak da çalıştırabilirsiniz. Çoğu zaman bağımsız olarak tek tek uygulamalar veya mikro hizmetler üzerinde çalışabilmek iyi olsa da, bazen üretime dağıtıldığında çalışacağı gibi tüm sistemi yerel olarak çalıştırabilmek iyidir. Bunu başarmanın birkaç yolu vardır, bunlardan ikisi Minikube ve Docker Desktop'dır. Visual Studio ayrıca Docker gelişimi için takım sağlar.

### <a name="minikube"></a>Minikube

Minikube nedir? Minikube projesi "Minikube macOS, Linux ve Windows'da yerel bir Kubernetes kümesini uyguluyor" diyor. Birincil hedefleri "yerel Kubernetes uygulama geliştirme için en iyi araç olmak ve uygun tüm Kubernetes özelliklerini desteklemektir." Minikube'yi yüklemek Docker'dan ayrıdır, ancak Minikube Docker Desktop'ın desteklediğinden farklı hipervizörleri destekler. Aşağıdaki Kubernetes özellikleri şu anda Minikube tarafından desteklenir:

- DNS
- Düğüm Bağlantı Noktaları
- ConfigMaps ve sırları
- Panolar
- Konteyner çalışma süreleri: Docker, rkt, CRI-O ve konteyner
- Kapsayıcı Ağ Arabirimini Etkinleştirme (CNI)
- Giriş

Minikube'yi yükledikten sonra, görüntüyü indiren `minikube start` komutu çalıştırarak hızlı bir şekilde kullanmaya başlayabilir ve yerel Kubernetes kümesini başlatabilirsiniz. Küme başlatıldıktan sonra, standart Kubernetes `kubectl` komutlarını kullanarak onunla etkileşime girebilirsiniz.

### <a name="docker-desktop"></a>Docker Masaüstü

Ayrıca Windows'da Doğrudan Docker Desktop'dan Kubernetes ile de çalışabilirsiniz. Windows Kapsayıcıları kullanıyorsanız tek seçeneğiniz budur ve Windows olmayan kapsayıcılar için de mükemmel bir seçimdir. Standart Docker Desktop yapılandırma uygulaması, Docker Desktop'tan çalışan Kubernetes'i yapılandırmak için kullanılır.

![Docker Masaüstünde Kubernetes'i Yapılandırma](./media/docker-desktop-kubernetes.png)

**Şekil 3-4**. Docker Desktop'da Kubernetes'i yapılandırma.

Docker Desktop zaten yerel olarak kapsayıcı uygulamaları yapılandırmak ve çalıştırmak için en popüler araçtır. Docker Desktop ile çalışırken, üretime dağıtacağınız Docker kapsayıcı görüntülerinin aynısını yerel olarak geliştirebilirsiniz. Docker Desktop, konteyner uygulamaları yerel olarak "oluşturmak, test etmek ve sevk etmek" için tasarlanmıştır. Görüntüler Azure Konteyner Kayıt Defteri veya Docker Hub gibi bir resim kayıt defterine gönderildikten sonra, Azure Kubernetes Service (AKS) gibi hizmetler üretimde uygulamayı yönetir.

### <a name="visual-studio-docker-tooling"></a>Görsel Stüdyo Docker Takım

Visual Studio web uygulamaları için Docker geliştirme destekler. Yeni bir ASP.NET Core uygulaması oluşturduğunuzda, şekil 3-5'te gösterildiği gibi, proje oluşturma sürecinin bir parçası olarak docker desteği ile yapılandırma seçeneği verilir.

![Visual Studio Docker Desteği etkinleştirin](./media/visual-studio-enable-docker-support.png)

**Şekil 3-5**. Visual Studio Docker Desteği etkinleştirin

Bu seçenek seçildiğinde, proje, uygulamayı `Dockerfile` docker kapsayıcısında oluşturmak ve barındırmak için kullanılabilecek kökünde bir ile oluşturulur. Örnek Dockerfile Şekil 3-6'da gösterilmiştir.

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

**Şekil 3-6**. Visual Studio Dockerfile oluşturulan

Uygulama çalıştığında varsayılan davranış Docker'ı da kullanacak şekilde yapılandırılır. Şekil 3-7, Docker desteği ile oluşturulan yeni bir ASP.NET Core projesinden elde edilen farklı çalışma seçeneklerini gösterir.

![Visual Studio Docker Çalışma Seçenekleri](./media/visual-studio-docker-run-options.png)

**Şekil 3-7**. Visual Studio Docker Çalışma Seçenekleri

[Azure Geliştirme Alanları,](https://docs.microsoft.com/azure/dev-spaces/) yerel geliştirmeye ek olarak, birden çok geliştiricinin Azure'da kendi Kubernetes yapılandırmalarıyla çalışması için kullanışlı bir yol sağlar. Şekil 3-7'de de görebileceğiniz gibi, uygulamayı Azure Geliştirme Spaces'te de çalıştırabilirsiniz.

ASP.NET Core uygulamanıza Docker desteğini oluştururken eklemezseniz, her zaman daha sonra ekleyebilirsiniz. Visual Studio Solution Explorer'dan projeye sağ tıklayın ve Şekil 3-8'de gösterildiği gibi**Docker Desteği** **Ekle'yi** > seçin.

![Visual Studio Docker Desteği Ekle](./media/visual-studio-add-docker-support.png)

**Şekil 3-8**. Visual Studio Docker Desteği Ekle

Docker desteğine ek olarak, Şekil 3-8'de de gösterilen Konteyner Orkestrasyon Desteği'ni de ekleyebilirsiniz. Varsayılan olarak, orkestratör Kubernetes ve Helm kullanır. Orkestratörü seçtikten sonra, proje `azds.yaml` köküne bir dosya eklenir `charts` ve uygulamayı yapılandırmak ve Kubernetes'e dağıtmak için kullanılan Miğfer grafiklerini içeren bir klasör eklenir. Şekil 3-9 yeni bir projede ortaya çıkan dosyaları gösterir.

![Visual Studio Ekle Orkestratör Desteği](./media/visual-studio-add-orchestrator-support.png)

**Şekil 3-9**. Visual Studio Ekle Orkestratör Desteği

## <a name="references"></a>Başvurular

- [Kubernetes nedir?](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [Minikube ile Kubernetes kurulumu](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube vs Docker Masaüstü](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Docker için Görsel Stüdyo Araçları](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[Önceki](scale-applications.md)
>[Sonraki](leverage-serverless-functions.md)
