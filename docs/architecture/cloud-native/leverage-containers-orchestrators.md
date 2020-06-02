---
title: Kapsayıcılardan ve düzenleyicilerden yararlanma
description: Azure 'da Docker kapsayıcılarını ve Kubernetes düzenleyicilerinden yararlanın
ms.date: 05/13/2020
ms.openlocfilehash: b2fedac205d7a5bd8b8f8cf665ae370b9bf26654
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84282590"
---
# <a name="leveraging-containers-and-orchestrators"></a>Kapsayıcılardan ve düzenleyicilerden yararlanma

Kapsayıcılar ve düzenleyiciler, tek parçalı dağıtım yaklaşımları için ortak olan sorunları çözmeye yönelik olarak tasarlanmıştır.

## <a name="challenges-with-monolithic-deployments"></a>Tek parçalı dağıtımlar ile ilgili sorunlar

Geleneksel olarak, çoğu uygulama tek bir birim olarak dağıtılır. Bu tür uygulamalar tek bir olarak adlandırılır. Bu genel yaklaşım, birden çok modülden oluşsa bile veya derlemeler şekil 3-1 ' de gösterildiği gibi tek parçalı mimari olarak bilinir.

![Tek parçalı mimari.](./media/monolithic-design.png)

**Şekil 3-1**. Tek parçalı mimari.

Basitlik avantajlarına sahip olsalar da tek parçalı mimarilerin bir dizi zorluk yüzü vardır:

### <a name="deployment"></a>Dağıtım

Tek parçalı uygulamalar, yalnızca küçük bir değişiklik yapılmış olsa bile tüm uygulamanın tam dağıtımını gerektirir. Tam dağıtımlar pahalı ve hataya açık olabilir. Ayrıca, uygulamanın yeniden başlatılması gerekir ve bu, kullanım dışı olarak geçici olarak etkiler.

### <a name="scaling"></a>Ölçeklendirme

Tek parçalı bir uygulama, genellikle yüksek yetenek donanımlar gerektiren tek bir makine örneğinde barındırılır. Tekinin herhangi bir bölümü ölçeklendirmeyi gerektiriyorsa, uygulamanın tamamının başka bir kopyasının başka bir makineye dağıtılması gerekir. Tek tek, uygulama bileşenlerini ayrı ayrı ölçeklendiremez. Bu, hepsi veya hiçbir şey değildir. Ölçeklendirme gerektirmeyen bileşenleri ölçeklendirme, verimsiz ve maliyetli kaynak kullanımı ile sonuçlanır.

### <a name="environment"></a>Ortam

Tek parçalı uygulamalar, genellikle önceden yüklenmiş bir işletim sistemi, çalışma zamanı ve kitaplık bağımlılıkları olan bir barındırma ortamına dağıtılır. Bu ortam, uygulamanın geliştirildiğini veya test edildiğini eşleşmeyebilir. Uygulama ortamları genelinde tutarsızlıklar, tek parçalı dağıtımlar için ortak bir sorun kaynağıdır.

### <a name="coupling"></a>Bağlantısı

Tek parçalı bir uygulama, işlevsel bileşenleri arasında yüksek bir bağ deneyimlidir. Sabit sınır olmadan sistem değişiklikleri genellikle istenmeden ve pahalı yan etkilere neden olur. Yeni özellikler/düzeltmeler, uygulama için karmaşık, zaman alan ve pahalı hale gelir. Güncelleştirmeler kapsamlı test gerektirir. Ayrıca, geçiş, bileşenleri yeniden düzenleme veya alternatif uygulamalarda değiştirme olanağı da zorlaştırır. Sıkı bir sorun ayrımı ile oluşturulduğunda bile, tek parçalı kod tabanı olarak ' deki mimari liflik kümeleri, hiçbir zaman sonlandırma "özel durumlar" ile birlikte oluşur.

### <a name="platform-lock-in"></a>Platform kilidi-ın

Tek parçalı bir uygulama tek bir teknoloji yığını ile oluşturulur. Bu taahhüt, bir yeniliği sunarken, yeniliklere bir engel olabilir. Yeni özellikler ve bileşenler, daha modern teknolojiler daha iyi bir seçim olabileceği halde uygulamanın geçerli yığını kullanılarak oluşturulur. Daha uzun süreli bir risk, teknoloji yığınınızın süresi geçmiş ve kullanım dışı olma sürecinde. Tüm uygulamayı yeni, daha modern bir platforma yeniden tasarlama en iyi maliyetli ve riskli bir uygulamadır.

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>Kapsayıcıların ve düzenleyicilerinin avantajları nelerdir?

Bölüm 1 ' de kapsayıcılar tanıtıldık. Cloud Native Bilgi Işlem altyapısı 'nın (CNCF) kapsayıcının bulut Yerel [Izleme haritalarındaki](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) ilk adım olarak nasıl derecelendirmiş olduğunu vurgularız. Bu bölümde, kapsayıcıların avantajları tartışıyoruz.

Docker en popüler kapsayıcı yönetimi platformudur. Hem Linux hem de Windows üzerinde kapsayıcılarla birlikte çalışmaktadır. Kapsayıcılar, her sistemde aynı şekilde çalışan ayrı ancak tekrarlanabilir uygulama ortamları sağlar. Bu boyut, bulutta yerel hizmetler geliştirmek ve barındırmak için ideal hale getirir. Kapsayıcılar bir diğerinden yalıtılmıştır. Aynı konak donanımında iki kapsayıcı, çakışmalara neden olmadan farklı yazılım sürümlerine sahip olabilir.

Kapsayıcılar, proje yapıtları haline gelen ve kaynak denetimine işaretlenmiş basit metin tabanlı dosyalar tarafından tanımlanır. Tam sunucular ve sanal makinelerin güncelleştirilmesi için el ile çaba gerektirmesi durumunda, kapsayıcılar kolayca sürüm denetlenir. Kapsayıcılarda çalışmak üzere oluşturulan uygulamalar, derleme işlem hattının parçası olarak otomatikleştirilmiş araçlar kullanılarak geliştirilebilir, test edilebilir ve dağıtılabilir.

Kapsayıcılar sabittir. Bir kapsayıcı tanımladıktan sonra, tam olarak aynı şekilde yeniden oluşturabilir ve çalıştırabilirsiniz. Bu, bu şekilde bileşen tabanlı tasarıma yönelik olarak kullanılabilirlik sağlar. Bir uygulamanın bazı bölümleri diğerlerinden farklı şekilde geliştikçe, en sık değiştiren parçaları yalnızca dağıtırken uygulamanın tamamını yeniden dağıtmanız gerekir mi? Bir uygulamanın farklı özellikleri ve çapraz kesme sorunları ayrı birimlere ayrılabilir. Şekil 3-2, tek parçalı bir uygulamanın belirli özellikler veya işlevler için kapsayıcılardan ve mikro hizmetlerden nasıl yararlanabileceğiz gösterir. Uygulamanın kendisindeki diğer işlevsellik de Kapsayıcılı hale getirilir.

![Arka uçta mikro hizmetleri kullanmak için tek parçalı bir uygulamayı bölmek.](./media/cloud-native-design.png)

**Şekil 3-2**. Tek parçalı bir uygulamayı, mikro hizmetlere çok parçalı bir uygulama oluşturmayı kaldırma.

Her bulut Yerel hizmeti ayrı bir kapsayıcıda oluşturulup dağıtılır. Her biri gerektiğinde güncelleştirebilir. Her hizmet için uygun kaynakları olan düğümlerde tek tek hizmetler barındırılabilir. Her hizmetin çalıştığı ortam, geliştirme, test ve üretim ortamlarında paylaşılan ve kolayca sürümlü bir sabittir. Uygulamanın farklı alanlarında, tek başına derleme zamanı bağımlılıkları değil, hizmetler arasında doğrudan çağrı veya ileti olarak gerçekleştirilir. Ayrıca, uygulamanın geri kalanında değişiklik gerektirmeden belirli bir özelliği en iyi şekilde sunan teknolojiyi de seçebilirsiniz.

Kapsayıcılı hizmetler otomatik yönetim gerektirir. Bağımsız olarak dağıtılan kapsayıcıların büyük bir kümesini el ile yönetmek mümkün değildir. Örneğin, aşağıdaki görevleri göz önünde bulundurun:

- Kapsayıcı örnekleri birçok makinenin bir kümesi arasında nasıl sağlanacak?
- Dağıtıldıktan sonra kapsayıcılar birbirleriyle nasıl keşfedilir ve birbirleriyle iletişim kurar?
- Kapsayıcılar isteğe bağlı olarak nasıl ölçeklenebilen veya kullanıma hazır?
- Her kapsayıcının durumunu nasıl izleyebilirim?
- Bir kapsayıcıyı donanım ve yazılım hatalarıyla nasıl koruyabilirim?
- Canlı bir uygulama için kapsayıcıları sıfır kapalı kalma süresiyle nasıl yükseltebilirim?

Kapsayıcı yöneticileri bu ve diğer kaygıları ele alır ve otomatikleştirin.

Bulut Yerel ekonomik sistemde, Kubernetes, kapsayıcı Orchestrator ' ı d haline geldi. Bu, bulut Yerel Bilgi Işlem altyapısı (CNCF) tarafından yönetilen açık kaynaklı bir platformdur. Kubernetes, bir makine kümesi içindeki Kapsayıcılı iş yüklerinin dağıtım, ölçeklendirme ve işlevsel sorunlarını otomatikleştirir. Ancak, Kubernetes 'nin yüklenmesi ve yönetilmesi, önemli bir karmaşıkdır.

Daha iyi bir yaklaşım, Kubernetes 'in bir bulut satıcısından yönetilen hizmet olarak faydalanmasıdır. Azure bulut, [Azure Kubernetes hizmeti (AKS)](https://azure.microsoft.com/services/kubernetes-service/)ile tam olarak yönetilen bir Kubernetes platformu sunar. AKS, Kubernetes yönetiminin karmaşıklık ve operasyonel yükünü soyutlar. Kubernetes 'i bir bulut hizmeti olarak kullanırsınız; Microsoft, yönetim ve destekleme sorumluluğunu kullanır. AKS, diğer Azure hizmetleri ve geliştirme araçlarıyla da sıkı bir şekilde tümleşir.

AKS, küme temelli bir teknolojidir. Federasyon sanal makineleri veya düğümleri havuzu Azure bulutuna dağıtılır. Bunlar, yüksek oranda kullanılabilir bir ortam veya küme oluşturur. Küme, bulutta yerel uygulamanıza sorunsuz, tek bir varlık olarak görünür. Bu şekilde, AKS 'ler, yükü eşit bir şekilde dağıtan önceden tanımlanmış bir stratejiye göre Kapsayıcılı hizmetlerinizi bu düğümler arasında dağıtır.

## <a name="what-are-the-scaling-benefits"></a>Ölçeklendirme avantajları nelerdir?

Kapsayıcılarda oluşturulan hizmetler, Kubernetes gibi Orchestration araçları tarafından sunulan ölçeklendirme avantajlarından yararlanabilir. Tasarım kapsayıcıları tarafından yalnızca kendileri hakkında bilgi sahibi. Birlikte çalışması gereken birden çok kapsayıcınız varsa, bunları daha yüksek bir düzeyde düzenlemeniz gerekir. Çok sayıda kapsayıcıyı ve ağ yapılandırması gibi paylaşılan bağımlılıklarını organize etmek, düzenleme araçlarının günü kaydetmek için nereden geldiği yerdir! Kubernetes kapsayıcı grupları üzerinde bir soyutlama katmanı oluşturur ve bunları *Pod*olarak düzenler. *Düğüm*olarak adlandırılan çalışan makinelerdeki pods çalıştırılır. Bu düzenlenmiş yapı, *küme*olarak adlandırılır. Şekil 3-3, bir Kubernetes kümesinin farklı bileşenlerini gösterir.

![Kubernetes kümesi bileşenleri. ](./media/kubernetes-cluster-components.png)
 **Şekil 3-3**. Kubernetes kümesi bileşenleri.

Kapsayıcılı iş yüklerinin ölçeklendirilmesi, kapsayıcı düzenleyicilerinin temel bir özelliğidir. AKS iki boyut genelinde otomatik ölçeklendirmeyi destekler: kapsayıcı örnekleri ve işlem düğümleri. Birlikte, isteğe bağlı olarak ani artışları hızla ve verimli bir şekilde yanıtlama ve ek kaynaklar ekleme olanağı sunar. Bu bölümün ilerleyen kısımlarında, ölçeklendirilirken ölçeklendirmeyi tartıştık.

### <a name="declarative-versus-imperative"></a>Bildirime dayalı ve kesinlik

Kubernetes hem bildirime dayalı hem de kesinlik temelli yapılandırmayı destekler. Zorunlu yaklaşım, Kubernetes 'in her adımın nasıl yapılacağını söyleyen çeşitli komutları çalıştırmayı içerir. Bu görüntüyü çalıştırın. Bu Pod öğesini silin. Bu bağlantı noktasını kullanıma sunun. Bildirim temelli yaklaşımla, ne yapmak istediğinizi belirlemek için bildirim olarak adlandırılan bir yapılandırma dosyası oluşturursunuz. Kubernetes bildirimi okur ve istediğiniz bitiş durumunu gerçek bitiş durumuna dönüştürür.

Zorunlu komutların öğrenimi ve etkileşimli deneme için harika olması. Ancak, güvenilir ve tekrarlanabilir dağıtımlar sağlayan bir altyapıyı kod yaklaşımı olarak ayraç içine almak için, bildirimli olarak Kubernetes bildirim dosyalarını oluşturmak isteyeceksiniz. Bildirim dosyası bir proje yapıtı haline gelir ve Kubernetes dağıtımlarını otomatikleştirmek için CI/CD işlem hattınızda kullanılır.

Kümenizi tanımlayıcı komutları kullanarak zaten yapılandırdıysanız, kullanarak bildirim temelli bir bildirimi dışarı aktarabilirsiniz `kubectl get svc SERVICENAME -o yaml > service.yaml` . Bu komut aşağıda gösterilene benzer bir bildirim üretir:

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

Bildirim temelli yapılandırma kullanırken, `kubectl diff -f FOLDERNAME` yapılandırma dosyalarınızın bulunduğu klasöre karşı uygulamadan önce yapılacak değişikliklerin önizlemesini yapabilirsiniz. Değişiklikleri uygulamak istediğinize emin olduktan sonra çalıştırın `kubectl apply -f FOLDERNAME` . `-R`Bir klasör hiyerarşisini yinelemeli olarak işlemeye ekleyin.

Ayrıca, biri dağıtımları olan diğer Kubernetes özellikleriyle bildirim temelli yapılandırma de kullanabilirsiniz. Bildirim temelli dağıtımlar, yayınları, güncelleştirmeleri ve ölçeklendirmeyi yönetmeye yardımcı olur. Bu kişiler, Kubernetes dağıtım denetleyicisine yeni değişiklikler dağıtma, yük genişletme veya önceki bir düzeltmeye geri dönme işlemlerini yönlendirir. Bir küme kararsız durumdaysa, bildirime dayalı bir dağıtım otomatik olarak kümeyi istenen duruma geri döndürür. Örneğin, bir düğüm kilitlenmelidir, dağıtım mekanizması istediğiniz duruma ulaşmak için bir değişikliği yeniden dağıtırsınız

Bildirim temelli yapılandırma kullanmak, altyapının uygulama kodu ile birlikte denetlenebilen ve sürümü oluşturulmuş bir kod olarak temsil etmesine olanak tanır. Yapı ve dağıtım işlem hattı kullanarak sürekli dağıtım için geliştirilmiş değişiklik denetimi ve daha iyi destek sağlar.

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>Kapsayıcılar ve düzenleyiciler için hangi senaryolar idealdir?

Aşağıdaki senaryolar kapsayıcıları ve düzenlemeleri kullanmak için idealdir.

### <a name="applications-requiring-high-uptime-and-scalability"></a>Yüksek çalışma süresi ve ölçeklenebilirlik gerektiren uygulamalar

Yüksek çalışma süresi ve ölçeklenebilirlik gereksinimleri olan bireysel uygulamalar, mikro hizmetler, kapsayıcılar ve düzenleyicilerin kullanıldığı bulutta yerel mimariler için ideal adaylardır. Bunlar kapsayıcılarda geliştirilir, sürümlü ortamlar arasında test edilebilir ve sıfır kapalı kalma süresiyle üretime dağıtılır. Kubernetes kümelerinin kullanımı, bu tür uygulamaların talep üzerine ölçeklenmesini ve düğüm hatalarından otomatik olarak kurtarılmasını sağlar.

### <a name="large-numbers-of-applications"></a>Çok sayıda uygulama

Çok sayıda uygulamayı dağıtan ve bunları yöneten kuruluşlar, kapsayıcılardan ve düzenleyicilerinden faydalanır. Kapsayıcılı ortamları ve Kubernetes kümelerini ayarlamanın en ön çabası, birincil olarak sabit bir maliyettir. Bireysel uygulamaların dağıtımı, sürdürülmesi ve güncelleştirilmesi, uygulama sayısıyla değişen bir maliyettir. Az sayıda uygulamanın ötesinde, özel uygulamaları korumanın karmaşıklığı kapsayıcıları ve düzenlemeleri kullanarak bir çözüm uygulama masrafını daha da aşıyor.

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>Kapsayıcıları ve düzenlemeleri kullanmaktan ne zaman kaçınmalısınız?

Uygulamanızı on Iki öğeli uygulama ilkelerine göre derlemenize izin verirseniz kapsayıcılardan ve düzenleyicilerinin önlenmemesini göz önünde bulundurmanız gerekir. Bu durumlarda, VM tabanlı bir barındırma platformunu veya büyük olasılıkla bazı karma sistemleri göz önünde bulundurun. Bununla birlikte, belirli işlevsellik parçalarını her zaman ayrı kapsayıcılara veya hatta sunucusuz işlevlere ayırabilirsiniz.

## <a name="development-resources"></a>Geliştirme kaynakları

Bu bölümde, bir sonraki uygulamanız için kapsayıcıları ve düzenlemeleri kullanmaya başlamanıza yardımcı olabilecek geliştirme kaynaklarının kısa bir listesi gösterilmektedir. Bulut Yerel mikro hizmetleri mimari uygulamanızı nasıl tasarlayacağımızı öğrenmek istiyorsanız bu kitabın yardımcı, [.net mikro hizmetleri: Kapsayıcılı .NET uygulamaları Için mimari](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)makalesini okuyun.

### <a name="local-kubernetes-development"></a>Yerel Kubernetes geliştirme

Kubernetes dağıtımları üretim ortamlarında harika bir değer sağlar, ancak geliştirme makinenizde yerel olarak da çalıştırılabilir. Bağımsız mikro hizmetlerde bağımsız olarak çalışabilir, ancak üretime dağıtıldığında çalıştırılacak şekilde tüm sistemi yerel olarak çalıştırmanız gereken zamanlar olabilir. Yardımcı olabilecek çeşitli araçlar vardır: Minikube ve Docker Desktop. Visual Studio, Docker geliştirmesi için de araç sağlar.

### <a name="minikube"></a>Minikube

Minikube nedir? Minikube projesi, "Minikube macOS, Linux ve Windows üzerinde yerel bir Kubernetes kümesi uygular" diyor. Birincil hedefleri, "yerel Kubernetes uygulama geliştirmesi için en iyi araç olacak ve sığan Kubernetes özelliklerini desteklemeye yöneliktir." Minikube yükleme Docker 'dan ayrıdır, ancak Minikube, Docker Desktop 'ın desteklediğinden farklı hiper yöneticileri destekler. Aşağıdaki Kubernetes özellikleri şu anda Minikube tarafından desteklenmektedir:

- DNS
- NodePorts
- ConfigMaps ve gizlilikler
- Panolar
- Kapsayıcı çalışma zamanları: Docker, RKT, CRı-O ve containerd
- Kapsayıcı ağ arabirimini etkinleştirme (CNı)
- Giriş

Minikube yükledikten sonra, `minikube start` bir görüntüyü yükleyen ve yerel Kubernetes kümesini Başlatan komutunu çalıştırarak hızlı bir şekilde kullanmaya başlayabilirsiniz. Küme başlatıldıktan sonra, standart Kubernetes komutlarını kullanarak onunla etkileşime geçin `kubectl` .

### <a name="docker-desktop"></a>Docker Masaüstü

Ayrıca, Kubernetes ile doğrudan Windows 'daki Docker Desktop 'tan da çalışabilirsiniz. Windows kapsayıcıları kullanıyorsanız tek seçeneğiniz vardır ve Windows dışı kapsayıcılar için harika bir seçimdir. Şekil 3-4, Docker Desktop çalıştırılırken yerel Kubernetes desteğinin nasıl etkinleştirileceğini gösterir.

![Docker Desktop 'ta Kubernetes 'i yapılandırma](./media/docker-desktop-kubernetes.png)

**Şekil 3-4**. Docker Desktop 'ta Kubernetes 'i yapılandırma.

Docker Desktop, Kapsayıcılı uygulamaları yerel olarak yapılandırmaya ve çalıştırmaya yönelik en popüler araçtır. Docker Desktop ile çalışırken, üretime dağıtacağınız Docker kapsayıcı görüntüleri kümesine göre yerel olarak geliştirme yapabilirsiniz. Docker Desktop, Kapsayıcılı uygulamaları yerel olarak derlemek, test etmek ve teslim etmek üzere tasarlanmıştır. Hem Linux hem de Windows kapsayıcılarını destekler. Görüntülerinizi Azure Container Registry veya Docker Hub gibi bir görüntü kayıt defterine gönderdikten sonra AKS 'ler onları üretime çekebilir ve bunları dağıtabilir.

### <a name="visual-studio-docker-tooling"></a>Visual Studio Docker Araçları

Visual Studio, Web tabanlı uygulamalar için Docker geliştirmeyi destekler. Yeni bir ASP.NET Core uygulaması oluşturduğunuzda, Şekil 3-5 ' de gösterildiği gibi, Docker desteğiyle yapılandırma seçeneğiniz vardır.

![Visual Studio Docker desteğini etkinleştir](./media/visual-studio-enable-docker-support.png)

**Şekil 3-5**. Visual Studio Docker desteğini etkinleştir

Bu seçenek belirlendiğinde proje, bir `Dockerfile` Docker kapsayıcısında uygulamayı derlemek ve barındırmak için kullanılabilen bir kökünde oluşturulur. Şekil 3 -6. git 'de örnek bir Dockerfile gösterilmektedir

```docker
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY ["eShopWeb/eShopWeb.csproj", "eShopWeb/"]
RUN dotnet restore "eShopWeb/eShopWeb.csproj"
COPY . .
WORKDIR "/src/eShopWeb"
RUN dotnet build "eShopWeb.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "eShopWeb.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "eShopWeb.dll"]
```

**Şekil 3-6**. Visual Studio tarafından oluşturulan Dockerfile

Uygulamanın çalışması için varsayılan davranış, Docker 'ı kullanmak üzere yapılandırılmıştır. Şekil 3-7, Docker desteği eklenmiş şekilde oluşturulan yeni bir ASP.NET Core projesinden kullanılabilir farklı çalıştırma seçeneklerini gösterir.

![Visual Studio Docker çalıştırma seçenekleri](./media/visual-studio-docker-run-options.png)

**Şekil 3-7**. Visual Studio Docker çalıştırma seçenekleri

[Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/) , yerel geliştirmeye ek olarak, birden çok geliştiricinin Azure 'Da kendi Kubernetes yapılandırmalarına göre çalışması için kullanışlı bir yol sağlar. Şekil 3-7 ' de görebileceğiniz gibi, uygulamayı Azure Dev Spaces de çalıştırabilirsiniz.

Ayrıca, dilediğiniz zaman mevcut bir ASP.NET Core uygulamasına Docker desteği ekleyebilirsiniz. Visual Studio Çözüm Gezgini, Şekil 3-8 ' de gösterildiği gibi projeye sağ **Add**tıklayın ve  >  **Docker desteği**ekleyin.

![Visual Studio Docker desteği ekle](./media/visual-studio-add-docker-support.png)

**Şekil 3-8**. Visual Studio 'ya Docker desteği ekleme

Ayrıca şekil 3-8 ' de gösterilen kapsayıcı düzenleme desteği ekleyebilirsiniz. Varsayılan olarak Orchestrator, Kubernetes ve Held kullanır. Orchestrator 'ı seçtikten sonra `azds.yaml` Proje köküne bir dosya eklenir ve `charts` uygulamayı yapılandırmak ve Kubernetes 'e dağıtmak Için kullanılan helk grafiklerini içeren bir klasör eklenir. Şekil 3-9 yeni bir projedeki sonuç dosyalarını gösterir.

![Visual Studio Orchestrator desteği ekle](./media/visual-studio-add-orchestrator-support.png)

**Şekil 3-9**. Visual Studio 'ya düzenleme desteği ekleme

### <a name="visual-studio-code-docker-tooling"></a>Docker Tooling Visual Studio Code

Docker geliştirmeyi destekleyen Visual Studio Code için kullanılabilen birçok uzantı vardır.

Microsoft, [Visual Studio Code uzantısı Için Docker](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)sağlar. Bu uzantı, uygulamalara kapsayıcı desteği ekleme sürecini basitleştirir. Gerekli dosyaları, Docker görüntülerini oluşturur ve bir kapsayıcı içinde uygulamanızın hatalarını ayıklamanızı sağlar. Uzantı; başlatma, durdurma, İnceleme, kaldırma ve daha fazlasını içeren kapsayıcılar ve görüntüler üzerinde işlem yapmayı kolaylaştıran bir görsel gezgin sunar. Uzantı Ayrıca birden çok çalışan kapsayıcıyı tek bir birim olarak yönetmenizi sağlayan Docker Compose destekler.

>[!div class="step-by-step"]
>[Önceki](scale-applications.md) 
> [Sonraki](leverage-serverless-functions.md)
