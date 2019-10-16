---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Gerçek üretim uygulamalarının, tüm kapsayıcıların sistem durumunu, iş yükünü ve yaşam döngülerini ele alan düzenleyiciler ile dağıtılması ve yönetilmesi gerekir.
ms.date: 02/15/2019
ms.openlocfilehash: dcc1c8686210e34df33aef024429898a098fa33d
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395405"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme

Uygulamanızın mikro hizmetlere dayalı olması veya birden çok kapsayıcıya bölünmesi durumunda üretime hazırmış uygulamalar için düzenleyiciler kullanmak gereklidir. Daha önce belirtildiği gibi, mikro hizmet tabanlı bir yaklaşımda, her mikro hizmet modelin ve verilerinin sahibi olur, böylece bir geliştirme ve dağıtım noktasından otonom hale gelir. Ancak, birden çok hizmetten (SOA gibi) oluşan daha geleneksel bir uygulamanız olsa da, dağıtılmış bir sistem olarak dağıtılması gereken tek bir iş uygulamasının bulunduğu birden fazla kapsayıcıyla veya hizmete sahip olursunuz. Bu tür sistemler, ölçeği genişletmek ve yönetmek için karmaşıktır; Bu nedenle, üretime hazırlı ve ölçeklenebilir çok kapsayıcılı bir uygulamaya sahip olmak istiyorsanız kesinlikle bir Orchestrator gerekir.

Şekil 4-6, birden fazla mikro hizmetten (kapsayıcılardan) oluşan bir uygulama kümesine dağıtımı gösterir.

![Bir kümede oluşturulan Docker uygulamalarını gösteren diyagram.](./media/orchestrate-high-scalability-availability/composed-docker-applications-cluster.png)

**Şekil 4-6**. Kapsayıcılar kümesi

Mantıksal bir yaklaşım gibi görünüyor. Ancak yük dengelemeyi nasıl işleirsiniz, Yönlendirme ve bu oluşturulan uygulamalar nasıl düzenlenir?

Docker komut satırı arabirimi (CLı), bir konak üzerinde tek bir kapsayıcıyı yönetme ihtiyaçlarını karşılar, ancak daha karmaşık dağıtılmış uygulamalar için birden çok konağa dağıtılan birden çok kapsayıcıyı yönetmek için geldiğinde kısa sürer. Çoğu durumda, kapsayıcıları otomatik olarak başlatacak, her görüntü için birden fazla örneğe sahip kapsayıcıları ölçeklendirecek, onları askıya alacak veya gerektiğinde kapatmak için bir yönetim platformuna ihtiyacınız vardır ve ayrıca, ağ ve veri gibi kaynaklara nasıl eriştikleri de kontrol edersiniz Depo.

Tek tek kapsayıcıların veya basit oluşturulan uygulamaların yönetimini ötesinde ve mikro hizmetlerle daha büyük kurumsal uygulamalarda gezinmek için, düzenleme ve kümeleme platformları ' nı açmanız gerekir.

Bir mimaride ve geliştirme noktasından büyük, kurumsal, mikro hizmet tabanlı uygulamalar oluşturuyorsanız, gelişmiş senaryoları destekleyen aşağıdaki platformları ve ürünleri anlamanız önemlidir:

- **Kümeler ve düzenleyiciler.** Büyük mikro hizmet tabanlı bir uygulamayla gibi birçok Docker konağında uygulama ölçeklendirmeniz gerektiğinde, temel alınan platformun karmaşıklığını soyutlayarak bu konakların tümünü tek bir küme olarak yönetebilmek önemlidir. Kapsayıcı kümelerinin ve düzenleyicilerinin sağladığı bu. Düzenleyicilerinin örnekleri Azure Service Fabric ve Kubernetes ' dir. Kubernetes, Azure 'da Azure Kubernetes hizmeti üzerinden kullanılabilir.

- **Zamanlayıcılar.** *Zamanlama* , yöneticinin bir kümedeki kapsayıcıları başlatma yeteneğinin olması anlamına gelir. bu nedenle, zamanlayıcılar Ayrıca bunu yapmak için bir kullanıcı arabirimi sağlar. Bir küme Zamanlayıcısı çeşitli sorumluluklara sahiptir: kümenin kaynaklarını verimli bir şekilde kullanmak, Kullanıcı tarafından sağlanan kısıtlamaları ayarlamak için, düğümler veya konaklar genelinde kapsayıcıları etkin bir şekilde dengelemek ve yüksek bir sağlama sırasında hatalara karşı dayanıklı olması için sonrası.

Bir kümenin ve Scheduler 'ın kavramlarıyla ilgili olarak, farklı satıcılar tarafından sunulan ürünlerin çoğu özellik kümesini sağlaması çok benzer. Aşağıdaki bölümde, kümeler ve zamanlayıcılar için sahip olduğunuz en önemli platform ve yazılım seçimleri gösterilmektedir. Bu düzenleyiciler, Azure gibi genel bulutlarda yaygın olarak sunulur.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Kapsayıcı Kümelemesi, düzenleme ve zamanlama için yazılım platformları

| Platform | Açıklamalar |
|:---:|:---|
| **Kubernetes** <br/> ![ Kubernetes logosunun bir görüntüsü. ](./media/orchestrate-high-scalability-availability/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes*](https://kubernetes.io/) , özellikleri düzenlemek için küme altyapısı ve kapsayıcı zamanlamalarından değişen işlevselliği sağlayan açık kaynaklı bir üründür. Ana bilgisayar kümelerinde uygulama kapsayıcılarının dağıtım, ölçeklendirme ve işlemlerini otomatikleştirmenizi sağlar. <br/> <br/> *Kubernetes* , kolay yönetim ve bulma için uygulama kapsayıcılarını mantıksal birimlere gruplandıran kapsayıcı merkezli bir altyapı sağlar. <br/> <br/> *Kubernetes* , Linux 'Ta, Windows 'da daha az olgun bir yerde. |
| **Azure Kubernetes hizmeti (AKS)** <br/> ![a Azure Kubernetes hizmet logosunun bir görüntüsü. ](./media/orchestrate-high-scalability-availability/azure-kubernetes-service-logo.png) | [Azure Kubernetes hizmeti (AKS)](https://azure.microsoft.com/services/kubernetes-service/) , Azure 'Da Kubernetes kümesinin yönetimini, dağıtımını ve işlemlerini basitleştiren, yönetilen bir Kubernetes kapsayıcı düzenleme hizmetidir. |
| **Azure Service Fabric** <br/> ![a Azure Service Fabric logosunun bir görüntüsü. ](./media/orchestrate-high-scalability-availability/azure-service-fabric-logo.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) , uygulama oluşturmaya yönelik bir Microsoft mikro hizmetler platformudur. Bu, hizmetlerin bir [Orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) ve makine kümeleri oluşturur. Service Fabric, Hizmetleri kapsayıcı olarak veya düz süreçler olarak dağıtabilir. Aynı uygulama ve küme içindeki kapsayıcılardaki hizmetler ile süreçlerdeki hizmetleri de karıştırabilirler. <br/> <br/> *Service Fabric* kümeler Azure 'da, şirket içinde veya herhangi bir bulutta dağıtılabilir. Ancak, Azure 'da dağıtım, yönetilen bir yaklaşım ile basitleştirilmiştir. <br/> <br/> *Service Fabric* , [durum bilgisi olan hizmetler](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) ve [Reliable Actors](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/)gibi ek ve isteğe bağlı, seçkin [Service Fabric programlama modelleri](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) sağlar. <br/> <br/> *Service Fabric* , Windows 'Da (Windows 'da gelişen yıllar) ve Linux 'ta daha az olgun olması. <br/> <br/> Hem Linux hem de Windows kapsayıcıları 2017 tarihinden itibaren Service Fabric desteklenir. |
| **Azure Service Fabric ağı** <br/> ![a Azure Service Fabric kafes logosunun bir görüntüsü. ](./media/orchestrate-high-scalability-availability/azure-service-fabric-mesh-logo.png) | [*Azure Service Fabric ağı*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) aynı güvenilirliği, görev açısından kritik performansı ve ölçeği Service Fabric olarak sunar, ancak aynı zamanda tamamen yönetilen ve sunucusuz bir platform sunar. Bir kümeyi, VM 'Leri, depolamayı veya ağ yapılandırmasını yönetmeniz gerekmez. Yalnızca uygulamanızın geliştirilmesine odaklanırsınız. <br/> <br/> *Service Fabric ağ* , hem Windows hem de Linux kapsayıcıları destekler, böylece dilediğiniz programlama diliyle ve çerçevesiyle geliştirebilirsiniz.

## <a name="using-container-based-orchestrators-in-azure"></a>Azure 'da kapsayıcı tabanlı düzenleyiciler kullanma

Çeşitli bulut satıcıları, Azure, Amazon EC2 Container Service ve Google Container Engine gibi Docker kapsayıcıları ve Docker kümeleri ve düzenleme desteği sunar. Azure, Azure Kubernetes hizmeti (AKS), Azure Service Fabric ve Azure Service Fabric ağı aracılığıyla Docker kümesi ve Orchestrator desteği sağlar.

## <a name="using-azure-kubernetes-service"></a>Azure Kubernetes hizmetini kullanma

Bir Kubernetes kümesi, birkaç Docker barındırır ve bunları tek bir sanal Docker ana bilgisayarı olarak kullanıma sunar, böylece kümeye birden çok kapsayıcı dağıtabilir ve herhangi bir sayıda kapsayıcı örneğiyle ölçek genişletme yapabilirsiniz. Küme, ölçeklenebilirlik, sağlık ve benzeri tüm karmaşık yönetim sıhhi kileri idare eder.

AKS, Azure 'da Kapsayıcılı uygulamaları çalıştırmak üzere önceden yapılandırılmış bir sanal makine kümesinin oluşturulmasını, yapılandırılmasını ve yönetimini basitleştirmek için bir yol sağlar. Popüler açık kaynak zamanlama ve düzenleme araçlarının iyileştirilmiş bir yapılandırmasını kullanarak, AKS, Microsoft Azure kapsayıcıda kapsayıcı tabanlı uygulamalar dağıtmak ve yönetmek için mevcut becerilerinizi kullanmanıza veya büyük ve büyüyen bir topluluk uzmanlığına göre çizmenizi sağlar .

Azure Kubernetes hizmeti, popüler Docker Kümelemesi açık kaynaklı araçların ve teknolojilerin yapılandırmasını özellikle Azure için iyileştirir. Kapsayıcılar ve uygulama yapılandırmanız için taşınabilirlik sağlayan bir açık çözüm alırsınız. Boyut, ana bilgisayar sayısı ve Orchestrator Araçları ' nı seçin ve AKS diğer her şeyi işler.

![Bir Kubernetes küme yapısını gösteren diyagram.](./media/orchestrate-high-scalability-availability/kubernetes-cluster-simplified-structure.png)

**Şekil 4-7**. Kubernetes kümesinin Basitleştirilmiş yapısı ve topolojisi

Şekil 4-7, ana düğümün (VM) küme koordinasyonunu denetlediği bir Kubernetes kümesinin yapısını gösterir ve kapsayıcıları bir uygulama noktasından tek bir havuz olarak yönetilen düğümlerin geri kalanına dağıtabilirsiniz. Bu, binlerce kapsayıcının binlerce veya onlarca ölçeğini ölçeklendirmenize olanak tanır.

## <a name="development-environment-for-kubernetes"></a>Kubernetes için geliştirme ortamı

[Docker 'ın 2018 Temmuz 'da duyurduğu](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/)geliştirme ortamında, Kubernetes yalnızca [Docker Desktop](https://www.docker.com/community-edition)'ı yükleyerek tek bir geliştirme makinesinde (Windows 10 veya MacOS) da çalıştırılabilir. Şekil 4-8 ' de gösterildiği gibi daha sonra daha fazla tümleştirme testi için buluta dağıtabilirsiniz (AKS).

![Bir geliştirici makinesinde Kubernetes 'i gösteren ve daha sonra AKS 'e dağıtılan diyagram.](./media/orchestrate-high-scalability-availability/kubernetes-development-environment.png)

**Şekil 4-8**. Geliştirme makinesi ve bulutu 'nda Kubernetes çalıştırma

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Azure Kubernetes hizmeti (AKS) ile çalışmaya başlama

AKS 'yi kullanmaya başlamak için Azure portal veya CLı kullanarak bir AKS kümesi dağıtırsınız. Azure 'a bir Kubernetes kümesi dağıtma hakkında daha fazla bilgi için bkz. [Azure Kubernetes Service (AKS) kümesi dağıtma](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Varsayılan olarak AKS 'nin bir parçası olarak yüklenen yazılımların herhangi bir ücreti yoktur. Tüm varsayılan seçenekler açık kaynaklı yazılımlarla uygulanır. AKS, Azure 'da birden çok sanal makine için kullanılabilir. Yalnızca seçtiğiniz işlem örnekleri için ücretlendirilirsiniz, Ayrıca, depolama ve ağ gibi diğer temel altyapı kaynakları kullanılır. AKS 'in kendisi için artımlı ücret alınmaz.

@No__t-0 ve özgün `.yaml` dosyalarını temel alan Kubernetes 'e dağıtım hakkında daha fazla uygulama bilgisi için, [AKS 'de (Azure Kubernetes hizmeti) eShopOnContainers 'ı ayarlama](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service))bölümüne bakın.

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Kubernetes kümelerine helk grafiklerle dağıtım

Bir Kubernetes kümesine bir uygulama dağıttığınızda, önceki bölümde zaten bahsedildiği gibi, özgün `kubectl.exe` CLı aracını yerel biçime (`.yaml` dosya) göre kullanarak dağıtım dosyalarını kullanabilirsiniz. Ancak, karmaşık mikro hizmet tabanlı uygulamalar dağıtımında olduğu gibi daha karmaşık Kubernetes uygulamaları için [Held](https://helm.sh/)kullanılması önerilir.

HELI grafikleri, en karmaşık Kubernetes uygulamasını bile tanımlamanıza, sürümüne, yüklemenize, paylaşmanıza, yükseltmenize veya geri almanıza yardımcı olur.

Ayrıca, [Azure dev SPACES](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) gibi Azure 'Daki ek Kubernetes ortamları da HELI grafiklerini temel alan da, helk kullanımı da önerilir.

HELI, Microsoft, Google, BitNami ve helmkatkıda bulunan topluluğuyla işbirliği içinde [bulut Yerel Bilgi Işlem altyapısı (CNCF)](https://www.cncf.io/) tarafından korunur.

Helk grafikleri ve Kubernetes hakkında daha fazla uygulama bilgisi için, [AKS 'ye eShopOnContainers dağıtmak üzere helk grafiklerini kullanma](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts)konusuna bakın.

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Kubernetes uygulama yaşam döngüsü için Azure Dev Spaces kullanın

[Azure dev Spaces](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) takımlar için hızlı, yinelemeli bir Kubernetes geliştirme deneyimi sağlar. En düşük geliştirme makinesi kurulumu ile doğrudan Azure Kubernetes Service (AKS) ' de çalışan ve hata ayıklama kapsayıcılarını seçebilirsiniz. Visual Studio, Visual Studio Code veya komut satırı gibi tanıdık araçları kullanarak Windows, Mac veya Linux 'ta geliştirme yapabilirsiniz.

Belirtildiği gibi, kapsayıcı tabanlı uygulamalar dağıtıldığında Azure Dev Spaces Held grafiklerini kullanır.

Azure Dev Spaces, yalnızca Visual Studio 2017 veya Visual Studio Code kullanarak doğrudan Azure 'daki genel bir Kubernetes kümesinde kodu hızlı bir şekilde yinelemenize ve hata ayıklamanıza olanak sağladığından geliştirme ekiplerinin Kubernetes üzerinde daha üretken olmasına yardımcı olur. Azure 'daki Kubernetes kümesi paylaşılan bir yönetilen Kubernetes kümesidir ve bu sayede ekibiniz birlikte çalışarak işbirliği yapabilir. Kodunuzu yalıtımlı olarak geliştirebilir, daha sonra genel kümeye dağıtabilir ve bağımlılıkları çoğaltmadan veya mocize etmeden diğer bileşenlerle uçtan uca test gerçekleştirebilirsiniz.

Şekil 4-9 ' de gösterildiği gibi, Azure Dev Spaces en farklılaştırıcı özelliği, kümedeki genel dağıtımın geri kalanı ile tümleştirilen ' Spaces ' oluşturma yeteneğidir:

![Azure Dev Spaces birden çok boşluk kullanımını gösteren diyagram.](./media/orchestrate-high-scalability-availability/use-multiple-spaces-azure-dev.png)

**Şekil 4-9**. Azure Dev Spaces birden çok boşluk kullanma

Azure Dev Spaces, yeni sürümlerin test edilmesini kolaylaştırmak için üretim mikro hizmetlerini geliştirme kapsayıcı örneğiyle saydam bir şekilde karıştırarak ve eşleştirebilir. Temel olarak, Azure 'da paylaşılan bir geliştirme alanı ayarlayabilirsiniz. Her geliştirici uygulamanın yalnızca bir kısmına odaklanabilir ve senaryolarının bağımlı olduğu diğer tüm hizmetleri ve bulut kaynaklarını zaten içeren bir geliştirme alanında "önceden kaydedilmiş" kodu geliştirebilir. Bağımlılıklar her zaman güncel değildir ve geliştiriciler üretimi yansıtan bir şekilde çalışır.

Azure Dev Spaces, yalıtım halinde ve takım üyelerinizi bozmadan bir şekilde çalışmanıza olanak sağlayan bir alan kavramı sağlar. Bu özellik, URL öneklerini temel alır; bir kapsayıcının isteği için URL 'de bir dev Space öneki kullanırsanız Azure Dev Spaces, kapsayıcının Bu alan için dağıttığındaki özel bir sürümünü (varsa) çalıştırır. Aksi takdirde, genel/birleştirilmiş sürümü çalıştırır.

Somut bir örnek üzerinde pratik bir görünüm almak için [Azure dev Spaces Eshoponcontainers wiki sayfasını](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) görebilirsiniz.

Daha fazla bilgi için [Azure dev Spaces Ile takım geliştirme](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore)makalesine bakın.

## <a name="additional-resources"></a>Ek kaynaklar

- **Azure Kubernetes Service (AKS)**  \ ' i kullanmaya başlama
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Spaces** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes.** Resmi site. \
  <https://kubernetes.io/>

## <a name="using-azure-service-fabric"></a>Azure Service Fabric Kullanma

Azure Service Fabric, Microsoft 'un, genellikle stil halinde tek parçalı bir biçimde olan ve Hizmetleri teslim eden "Box" ürünlerini sunmaya yönelik geçiş işleminden bağımsız. Azure SQL veritabanı, Azure Cosmos DB, Azure Service Bus veya Cortana 'nın arka ucu, şekillendirilmiş Service Fabric gibi ölçekte büyük hizmetleri derleme ve çalıştırma deneyimi. Platform zaman içinde gelişmiş ve daha fazla hizmet benimsemiştir. Önemlisi, Service Fabric yalnızca Azure 'da değil, tek başına Windows Server dağıtımlarında de çalıştırdık.

Service Fabric amacı, bir hizmet oluşturma ve çalıştırma ve altyapı kaynaklarını verimli bir şekilde kullanma ile ilgili sorunları çözmektir. böylece takımlar, mikro hizmetler yaklaşımını kullanarak iş sorunlarını çözebilir.

Service Fabric, mikro hizmetler yaklaşımını kullanan uygulamalar oluşturmanıza yardımcı olacak iki geniş alan sağlar:

- Başarısız hizmetleri dağıtmak, ölçeklendirmek, yükseltmek, algılamak ve yeniden başlatmak, hizmet konumunu bulmak, durumu yönetmek ve sistem durumunu izlemek için sistem hizmetleri sağlayan bir platform. Bu sistem hizmetleri, daha önce açıklanan mikro hizmetlerin birçok özelliğini etkinleştirir.

- Mikro hizmet olarak uygulamalar oluşturmanıza yardımcı olmak için API 'Ler veya çerçeveler programlama: [güvenilir aktörler ve güvenilir hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Mikro hizmetinizi derlemek için herhangi bir kod seçebilirsiniz, ancak bu API 'Ler işi daha basit hale getirir ve platformlarla daha derin bir düzeyde tümleşir. Bu şekilde, sistem durumu ve tanılama bilgilerini alabilir veya güvenilir durum yönetiminden faydalanabilirsiniz.

Service Fabric, hizmetinizi nasıl derlemenize göre belirsiz ve herhangi bir teknolojiyi kullanabilirsiniz. Ancak, mikro hizmetler oluşturmayı kolaylaştıran yerleşik programlama API 'Leri sağlar.

Şekil 4-10 ' da gösterildiği gibi, mikro hizmetleri basit süreçler olarak veya Docker Kapsayıcıları olarak Service Fabric oluşturabilir ve çalıştırabilirsiniz. Ayrıca, aynı Service Fabric kümesi içinde işlem tabanlı mikro hizmetler ile kapsayıcı tabanlı mikro hizmetleri karıştırmak da mümkündür.

![Azure Service Fabric kümelerinin karşılaştırmasını gösteren diyagram.](./media/orchestrate-high-scalability-availability/azure-service-fabric-cluster-types.png)

**Şekil 4-10**. Azure Service Fabric mikro Hizmetleri işlem olarak veya kapsayıcılar olarak dağıtma

İlk görüntüde, her düğümün her mikro hizmet için tek bir işlem çalıştırdığı, mikro Hizmetleri işlem olarak görürsünüz. İkinci görüntüde, mikro Hizmetleri kapsayıcı olarak görürsünüz; burada her düğüm, mikro hizmet başına bir kapsayıcı olmak üzere birkaç kapsayıcı ile Docker 'ı çalıştırır. Linux ve Windows konaklarına dayalı Service Fabric kümeleri, sırasıyla Docker Linux kapsayıcılarını ve Windows kapsayıcılarını çalıştırabilir.

Azure Service Fabric 'de kapsayıcılar desteğiyle ilgili güncel bilgiler için, bkz. [Service Fabric ve kapsayıcılar](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric, fiziksel uygulamadan farklı bir mantıksal mimari (iş mikro hizmetleri veya sınırlı bağlamlar) tanımlayabileceğiniz bir platforma yönelik iyi bir örnektir. Örneğin, "durum[bilgisiz ve durum bilgisi olan mikro hizmetler](#stateless-versus-stateful-microservices)" adlı bir sonraki bölümde kullanıma sunulan [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview)'da [durum bilgisi olan Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) uygularsanız, birden çok ile bir iş mikro hizmet kavramı vardır. fiziksel hizmetler.

Şekil 4-10 ' de gösterildiği gibi, bir mantıksal/iş mikro hizmet perspektifinden düşünürken, bir durum bilgisi olan güvenilir Service Fabric bir hizmet uygularken, genellikle iki adet hizmet katmanı uygulamanız gerekecektir. Birincisi, birden çok bölümü işleyen (her bölüm durum bilgisi olan bir hizmettir), durum bilgisi olan güvenilir bir hizmettir. İkincisi, birden çok bölüme veya durum bilgisi olmayan hizmet örneklerine yönlendirme ve veri toplama işlemi sırasında ön uç hizmet veya ağ geçidi hizmetidir. Bu ağ geçidi hizmeti, arka uç hizmetine erişirken yeniden deneme döngülerine sahip istemci tarafı iletişimini de işler. Özel hizmetinizi uygularsanız, bir ağ geçidi hizmeti olarak adlandırılır veya alternatif olarak Service Fabric [ters proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)'yi de kullanabilirsiniz.

![Kapsayıcılarda durum bilgisi olan birkaç hizmeti gösteren diyagram.](./media/orchestrate-high-scalability-availability/service-fabric-stateful-business-microservice.png)

**Şekil 4-11**. Çeşitli durum bilgisi olan hizmet örneklerine ve özel ağ geçidi ön ucuna sahip iş mikro hizmeti

Herhangi bir durumda Service Fabric durum bilgisi olan Reliable Services kullandığınızda, birden fazla fiziksel hizmetten oluşan bir mantıksal veya iş mikro hizmeti (sınırlı bağlam) de vardır. Her biri, Şekil 4-11 ' de gösterildiği gibi, ağ geçidi hizmeti ve bölüm hizmeti ASP.NET Web API hizmetleri olarak uygulanabilir. Service Fabric kapsayıcılarda durum bilgisi olan birkaç güvenilir hizmeti desteklemeye yönelik bir hizmet içerir.

Service Fabric, hizmet gruplarını, Orchestrator veya Cluster için paketleme ve dağıtım birimi olan [Service Fabric bir uygulama](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)olarak gruplandırabilir ve dağıtabilirsiniz. Bu nedenle, Service Fabric uygulaması bu özerk iş ve mantıksal mikro hizmet sınırına ya da sınırlanmış bağlamla eşleştirilebilir, bu nedenle bu hizmetleri olarak çalışabilen dağıtabilirsiniz.

### <a name="service-fabric-and-containers"></a>Service Fabric ve kapsayıcılar

Service Fabric kapsayıcılarla ilgili olarak, Hizmetleri bir Service Fabric kümesi içindeki kapsayıcı görüntülerinde da dağıtabilirsiniz. Şekil 4-12 gösterdiği gibi, çoğu zaman hizmet başına yalnızca bir kapsayıcı olacaktır.

![Bir veritabanında hizmet beslemenin tek bir kapsayıcısını gösteren diyagram.](./media/orchestrate-high-scalability-availability/azure-service-fabric-business-microservice.png)

**Şekil 4-12**. Service Fabric 'de çeşitli hizmetler (kapsayıcılar) ile iş mikro hizmeti

Bir Service Fabric uygulama bir dış veritabanına erişen birkaç kapsayıcıyı çalıştırabilir ve tüm küme bir Iş mikro hizmetinin mantıksal sınırı olur. Ancak, "sidecar" kapsayıcıları (bir mantıksal hizmetin parçası olarak birlikte dağıtılması gereken iki kapsayıcı) de Service Fabric de mümkündür. Önemli olan şey, bir iş mikro hizmetinin çeşitli birlikte bulunan öğelerin etrafında mantıksal sınır olmasıdır. Çoğu durumda, tek bir veri modeli olan tek bir hizmet olabilir, ancak bazı durumlarda birçok fiziksel hizmete de sahip olabilirsiniz.

, Şekil 4-13 ' de gösterildiği gibi, süreçlerdeki Hizmetleri ve kapsayıcılardaki hizmetleri aynı Service Fabric uygulamasına karıştırabileceğinizi unutmayın.

![Süreçlerdeki Hizmetleri ve aynı uygulamadaki kapsayıcıları gösteren diyagram.](./media/orchestrate-high-scalability-availability/business-microservice-mapped-to-service-fabric-application.png)

**Şekil 4-13**. Kapsayıcılar ve durum bilgisi olan hizmetlerle Service Fabric uygulamayla eşlenmiş iş mikro hizmeti

Azure Service Fabric 'da kapsayıcı desteği hakkında daha fazla bilgi için bkz. [Service Fabric ve kapsayıcılar](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Durum bilgisiz ve durum bilgisi olan mikro hizmetler

Daha önce belirtildiği gibi, her mikro hizmet (mantıksal sınırlı bağlam) kendi etki alanı modeline (veri ve Logic) sahip olmalıdır. Durum bilgisi olmayan mikro hizmetler söz konusu olduğunda veritabanları dış olur, SQL Server gibi ilişkisel seçenekler veya Azure Cosmos DB ya da MongoDB gibi NoSQL seçenekleri kullanılır.

Ancak hizmetlerin kendisi de Service Fabric durum bilgisi alabilir, bu da verilerin mikro hizmette bulunduğu anlamına gelir. Bu veriler yalnızca aynı sunucuda değil, mikro hizmet sürecinde, bellekte ve sabit sürücülerde kalıcı olarak bulunabilir ve diğer düğümlere çoğaltılır. Şekil 4-14 farklı yaklaşımları gösterir.

![Durum bilgisiz ve durum bilgisi olmayan bir hizmetin karşılaştırmasını gösteren diyagram.](./media/orchestrate-high-scalability-availability/stateless-vs-stateful-microservices.png)

**Şekil 4-14**. Durum bilgisiz ve durum bilgisi olan mikro hizmetler

Durum bilgisi olmayan hizmetlerde durum (Kalıcılık, veritabanı) mikro hizmette tutulur. Durum bilgisi olan hizmetlerde durum, mikro hizmet içinde tutulur. Durum bilgisiz olmayan bir yaklaşım kusursuz olur ve yaklaşım geleneksel ve iyi bilinen desenlere benzer olduğundan, durum bilgisi olan mikro hizmetlerden daha kolay bir şekilde uygulanır. Ancak durum bilgisi olmayan mikro hizmetler işlem ve veri kaynakları arasında gecikme süresi getirmiyor. Ayrıca, ek önbellek ve kuyrukların performansını artırmaya çalışırken daha fazla hareketli parça de içerirler. Sonuç olarak, çok fazla katmana sahip karmaşık mimarilerde bitebilmeniz gerekir.

Buna karşılık, etki alanı mantığı ve verileri arasında gecikme olmadığı için [durum bilgisi olan mikro hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) , Gelişmiş senaryolarda Excel 'de bulunabilir. Yoğun veri işleme, oyun arka uçları, hizmet olarak veritabanları ve diğer düşük gecikmeli senaryolar, daha hızlı erişim için yerel durumu etkinleştiren durum bilgisi olan hizmetlerden yararlanır.

Durum bilgisiz ve durum bilgisi olan hizmetler tamamlayıcı. Örneğin, Şekil 4-14 ' de doğru diyagramda görebileceğiniz gibi, durum bilgisi olan bir hizmet birden çok bölüme ayrılabilir. Bu bölümlere erişmek için, Bölüm anahtarlarına göre her bir bölümün nasıl ele alınacağını bilen bir ağ geçidi hizmeti olarak davranan, durum bilgisi olmayan bir hizmetin olması gerekebilir.

Durum bilgisi olan hizmetlerin dezavantajları vardır. Ölçeklendirilmesi için yüksek karmaşıklık düzeyi getirirler. Genellikle dış veritabanı sistemleri tarafından uygulanan işlevsellik, durum bilgisi olmayan mikro hizmetler ve veri bölümlendirme genelinde veri çoğaltma gibi görevler için değinilmelidir. Bununla birlikte, [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) gibi, [durum bilgisi olan güvenilir Hizmetleri](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) olan bir Orchestrator 'ın, [Reliable Services API kullanarak durum bilgisi olmayan mikro hizmetlerin geliştirilmesini ve yaşam döngüsünü basitleştirerek en iyi şekilde yardım ettiği alanlardan biridir. ](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections)ve [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Aktör modelini destekleyen ve iş mantığı ile veriler arasındaki hata toleransını ve gecikme süresini artıran diğer mikro hizmet çerçeveleri [, Microsoft Research](https://github.com/dotnet/orleans)ve [Akka.net](https://getakka.net/). Her iki çerçeve de Docker desteğini geliştirmekte.

Docker Kapsayıcıları 'nın durumsuz olduğunu unutmayın. Durum bilgisi olmayan bir hizmet uygulamak istiyorsanız, daha önce belirtilen ek ve daha yüksek düzeyli çerçevelerden birine ihtiyacınız vardır.

## <a name="using-azure-service-fabric-mesh"></a>Azure Service Fabric ağı kullanma

Azure Service Fabric ağı, geliştiricilerin herhangi bir altyapıyı yönetmeksizin görev açısından kritik uygulamalar oluşturup dağıtmalarını sağlayan, tam olarak yönetilen bir hizmettir. İsteğe bağlı olarak ölçeklenen güvenli, dağıtılmış mikro hizmet uygulamaları derlemek ve çalıştırmak için Service Fabric ağı kullanın.

Şekil 4-15 ' de gösterildiği gibi, Service Fabric kafeste barındırılan uygulamalar, altyapıyı kapatmadan altyapı hakkında endişelenmeden çalışır ve ölçeklendirebilir.

![Yerel depodan Service Fabric kafese dağıtımı gösteren diyagram.](media/orchestrate-high-scalability-availability/deploy-microservice-containers-apps-service-fabric-mesh.png)

**Şekil 4-15**. Service Fabric ağı 'na mikro hizmet/kapsayıcı uygulaması dağıtma

Kapsar Service Fabric ağ, binlerce makine kümelerinden oluşur. Tüm küme işlemleri geliştiriciden gizlenir. Yalnızca Kapsayıcınız yüklemeniz ve ihtiyacınız olan kaynakları, kullanılabilirlik gereksinimlerini ve kaynak sınırlarını belirtmeniz yeterlidir. Service Fabric ağ, uygulama dağıtımınız tarafından istenen altyapıyı otomatik olarak ayırır ve ayrıca, uygulamanızın yüksek oranda kullanılabilir olmasını sağlamak için altyapı başarısızlıklarını da işler. Altyapıya değil, yalnızca uygulamanızın sistem durumu ve yanıt verme bilgilerini dikkate almanız gerekir.

Daha fazla bilgi için [Service Fabric kafes belgelerine](https://docs.microsoft.com/azure/service-fabric-mesh/)bakın.

## <a name="choosing-orchestrators-in-azure"></a>Azure 'da düzenleyiciler seçme

Aşağıdaki tabloda, iş yükleri ve işletim sistemi odağına bağlı olarak hangi Orchestrator 'ın kullanılacağı hakkında rehberlik verilmektedir.

![Kubernetes ve Service Fabric karşılaştıran bir tablonun görüntüsü.](media/orchestrate-high-scalability-availability/orchestrator-selection-azure-guidance.png)

**Şekil 4-16**. Azure kılavuzunda Orchestrator seçimi

>[!div class="step-by-step"]
>[Önceki](soa-applications.md)
>[İleri](deploy-azure-kubernetes-service.md)
