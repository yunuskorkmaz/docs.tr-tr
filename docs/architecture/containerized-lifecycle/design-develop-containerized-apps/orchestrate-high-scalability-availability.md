---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Gerçek üretim uygulamaları, tüm konteynerlerin sağlık, iş yükü ve yaşam döngülerini işleyen orkestratörlerle dağıtılmalı ve yönetilmelidir.
ms.date: 02/15/2019
ms.openlocfilehash: e548e6b3816dec1e56c273c53c9fd052443eb09b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76919535"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme

Uygulamanız mikro hizmetlere dayanıyorsa veya birden fazla kapsayıcıya bölünmüşse, üretime hazır uygulamalar için orkestratörlerin kullanılması esastır. Daha önce de tanıtılan, mikrohizmet tabanlı bir yaklaşımda, her microservice bir geliştirme ve dağıtım bakış açısından özerk olacak şekilde kendi modeli ve veri sahibi. Ancak birden çok hizmetten (SOA gibi) oluşan daha geleneksel bir uygulamanız olsa bile, dağıtılmış bir sistem olarak dağıtılması gereken tek bir iş uygulamasından oluşan birden çok kapsayıcınız veya hizmetiniz de olacaktır. Bu tür sistemler ölçeklendirmek ve yönetmek için karmaşıktır; bu nedenle, üretime hazır ve ölçeklenebilir çok konteyner uygulaması na sahip olmak istiyorsanız kesinlikle bir orkestratöre ihtiyacınız vardır.

Şekil 4-6, birden çok mikro hizmet (kapsayıcı) oluşan bir uygulama kümesine dağıtım göstermektedir.

![Bir kümede oluşan Docker uygulamalarını gösteren diyagram.](./media/orchestrate-high-scalability-availability/composed-docker-applications-cluster.png)

**Şekil 4-6**. Bir kapsayıcı kümesi

Mantıklı bir yaklaşım gibi görünüyor. Ama nasıl yük dengeleme, yönlendirme işleme ve bu bestelenmiş uygulamaları düzenlemek?

Docker CLI, tek bir ana bilgisayarda bir kapsayıcıyı yönetme gereksinimlerini karşılar, ancak daha karmaşık dağıtılmış uygulamalar için birden çok ana bilgisayarda dağıtılan birden çok kapsayıcıyı yönetme konusunda yetersiz kalır. Çoğu durumda, kapsayıcıları otomatik olarak başlatacak, kapsayıcıları görüntü başına birden çok örneği olan ölçeklendirecek, askıya alacak veya gerektiğinde kapatacak ve ideal olarak ağ ve veri gibi kaynaklara nasıl erişeceklerini denetleyecek bir yönetim platformuna ihtiyacınız var Depolama.

Tek tek kapsayıcıların veya basit oluşturulan uygulamaların yönetiminin ötesine geçmek ve mikro hizmetlerle daha büyük kurumsal uygulamalara yönelmek için, düzenleme ve kümeleme platformlarına yönelmeniz gerekir.

Mimari ve geliştirme açısından bakıldığında, büyük, kurumsal, mikro hizmetler tabanlı, uygulamalar oluşturuyorsanız, gelişmiş senaryoları destekleyen aşağıdaki platformları ve ürünleri anlamak önemlidir:

- **Kümeler ve orkestrasyoncular.** Uygulamaları, büyük mikro hizmetler tabanlı bir uygulama gibi birçok Docker ana bilgisayar arasında ölçeklendirmeniz gerektiğinde, temel platformun karmaşıklığını soyutlayarak tüm bu ana bilgisayarları tek bir küme olarak yönetebilmeniz çok önemlidir. Konteyner kümeleri ve orkestratörleri bunu sağlıyor. Orkestratörlere örnek olarak Azure Service Fabric ve Kubernetes verilebilir. Kubernetes Azure'da Azure Kubernetes Hizmeti aracılığıyla kullanılabilir.

- **Schedulers.** *Zamanlama,* bir yöneticinin kapsayıcıları kümede başlatabilmesi anlamına gelir, bu nedenle zamanlayıcılar da bunu yapmak için bir kullanıcı arabirimi sağlar. Küme zamanlayıcısının çeşitli sorumlulukları vardır: kümenin kaynaklarını verimli kullanmak, kullanıcı tarafından sağlanan kısıtlamaları ayarlamak, düğümler veya ana bilgisayarlar arasında denge kapları verimli bir şekilde yüklemek ve yüksek sağlarken hatalara karşı sağlam olmak Kullanılabilir -lik.

Küme ve zamanlayıcı kavramları yakından ilişkilidir, bu nedenle farklı satıcılar tarafından sağlanan ürünler genellikle her iki yetenek kümesini de sağlar. Aşağıdaki bölüm kümeler ve zamanlayıcılar için sahip olduğunuz en önemli platform ve yazılım seçeneklerini gösterir. Bu orkestratörler Azure gibi genel bulutlarda yaygın olarak sunulur.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Konteyner kümeleme, düzenleme ve zamanlama için yazılım platformları

| Platform | Yorumlar |
|:---:|:---|
| **Kubernetes** <br/> ![Kubernetes logosunun bir resmi.](./media/orchestrate-high-scalability-availability/kubernetes-container-orchestration-system-logo.png) | [*Kubernetes,*](https://kubernetes.io/) küme altyapısı ve konteyner planlamasından düzenleme özelliklerine kadar değişen işlevsellik sağlayan açık kaynaklı bir üründür. Uygulama kapsayıcılarının dağıtımını, ölçeklemesini ve işlemlerini ana bilgisayar kümeleri arasında otomatikleştirmenizi sağlar. <br/> <br/> *Kubernetes,* uygulama kapsayıcılarını kolay yönetim ve keşif için mantıksal birimlere gruplandıran konteyner merkezli bir altyapı sağlar. <br/> <br/> *Kubernetes* Linux'ta olgun, Windows'ta daha az olgun. |
| **Azure Kubernetes Hizmeti (AKS)** <br/> ![Azure Kubernetes Hizmet logosunun bir görüntüsü.](./media/orchestrate-high-scalability-availability/azure-kubernetes-service-logo.png) | [Azure Kubernetes Service (AKS),](https://azure.microsoft.com/services/kubernetes-service/) Azure'da Kubernetes kümesinin yönetimini, dağıtımını ve işlemlerini kolaylaştıran yönetilen bir Kubernetes konteyner düzenleme hizmetidir. |
| **Azure Service Fabric** <br/> ![Azure Hizmet Kumaşı logosunun bir görüntüsü.](./media/orchestrate-high-scalability-availability/azure-service-fabric-logo.png) | [Service Fabric,](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) uygulama oluşturmak için bir Microsoft mikro hizmetler platformudur. Bu hizmetlerin bir [orkestratör](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) ve makine kümeleri oluşturur. Service Fabric hizmetleri kapsayıcı veya düz işlemler olarak dağıtabilir. Hatta aynı uygulama ve küme içinde kapsayıcılarda hizmetleri ile süreçlerde hizmetleri karıştırabilirsiniz. <br/> <br/> *Service Fabric* kümeleri Azure'da, şirket içinde veya herhangi bir bulutta dağıtılabilir. Ancak, Azure'da dağıtım yönetilen bir yaklaşımla basitleştirilir. <br/> <br/> *Hizmet Kumaş* [stateful hizmetleri](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) ve [Güvenilir Aktörler](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/)gibi ek ve isteğe bağlı prescriptive Hizmet Kumaş [programlama modelleri](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) sağlar. <br/> <br/> *Service Fabric* Windows'da olgundur (Windows'da gelişen yıllar), Linux'ta daha az olgundur. <br/> <br/> 2017 yılından bu yana Service Fabric'te hem Linux hem de Windows kapsayıcıları desteklenir. |
| **Azure Servis Kumaş Örgü** <br/> ![Azure Service Fabric Mesh logosunun bir görüntüsü.](./media/orchestrate-high-scalability-availability/azure-service-fabric-mesh-logo.png) | [*Azure Service Fabric Mesh,*](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) Service Fabric ile aynı güvenilirlik, görev açısından kritik performans ve ölçeği sunar, ancak aynı zamanda tam olarak yönetilen ve sunucusuz bir platform sunar. Bir küme, VM, depolama veya ağ yapılandırmasını yönetmeniz gerekmez. Sadece başvurunuzun gelişimine odaklanın. <br/> <br/> *Service Fabric Mesh* hem Windows hem de Linux kapsayıcılarını destekler ve istediğiniz programlama dili ve çerçevesi ile geliştirmenize olanak sağlar.

## <a name="using-container-based-orchestrators-in-azure"></a>Azure'da konteyner tabanlı orkestratörleri kullanma

Birçok bulut satıcısı Docker konteyner desteğinin yanı sıra Azure, Amazon EC2 Konteyner Hizmeti ve Google Konteyner Motoru dahil docker kümeleri ve orkestrasyon desteği sunar. Azure, Azure Kubernetes Hizmeti (AKS), Azure Hizmet Kumaşı ve Azure Servis Kumaş Kafesi aracılığıyla Docker kümesi ve orkestratör desteği sağlar.

## <a name="using-azure-kubernetes-service"></a>Azure Kubernetes Hizmetini Kullanma

Bir Kubernetes kümesi birkaç Docker ana bilgisayarını bir araya getirerek bunları tek bir sanal Docker ana bilgisayar olarak ortaya çıkarır, böylece kümeye birden fazla kapsayıcı dağıtabilir ve istediğiniz sayıda kapsayıcı örneğiyle ölçeklendirebilirsiniz. Küme ölçeklenebilirlik, sağlık ve benzeri gibi tüm karmaşık yönetim sıhhi tesisat ele alacaktır.

AKS, Azure'da kapsayıcı uygulamaları çalıştırmak için önceden yapılandırılmış bir sanal makine kümesinin oluşturulmasını, yapılandırmasını ve yönetimini basitleştirmenin bir yolunu sağlar. Popüler açık kaynak zamanlama ve düzenleme araçlarının optimize edilmiş yapılandırmasını kullanan AKS, Microsoft Azure'da kapsayıcı tabanlı uygulamaları dağıtmak ve yönetmek için mevcut becerilerinizi kullanmanıza veya büyük ve büyüyen bir topluluk uzmanlığından yararlanmanıza olanak tanır .

Azure Kubernetes Hizmeti, azure için özel olarak popüler Docker kümeleme açık kaynak araçları nın ve teknolojilerinin yapılandırmasını optimize eder. Hem kapsayıcılarınız hem de uygulama yapılandırmanız için taşınabilirlik sunan açık bir çözüm elabilirsiniz. Boyutu, ana bilgisayar sayısını ve orkestratör araçlarını seçersiniz ve AKS diğer her şeyi işler.

![Bir Kubernetes küme yapısını gösteren diyagram.](./media/orchestrate-high-scalability-availability/kubernetes-cluster-simplified-structure.png)

**Şekil 4-7**. Kubernetes kümesinin basitleştirilmiş yapısı ve topolojisi

Şekil 4-7, bir ana düğümün (VM) kümenin koordinasyonunun çoğunu kontrol ettiği bir Kubernetes kümesinin yapısını gösterir ve uygulama açısından tek bir havuz olarak yönetilen düğümlerin geri kalanına kapsayıcılar dağıtabilirsiniz. Bu, binlerce hatta on binlerce kapsayıcıya ölçeklendirmenize olanak tanır.

## <a name="development-environment-for-kubernetes"></a>Kubernetes için geliştirme ortamı

[Docker'ın Temmuz 2018'de duyurduğu](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/)geliştirme ortamında, Kubernetes sadece [Docker Desktop'ı](https://www.docker.com/community-edition)yükleyerek tek bir geliştirme makinesinde (Windows 10 veya macOS) da çalıştırılabilir. Daha sonra şekil 4-8'de gösterildiği gibi daha fazla tümleştirme testleri için buluta (AKS) dağıtabilirsiniz.

![Bir dev makinede Kubernetes gösteren diyagram sonra AKS dağıtılan.](./media/orchestrate-high-scalability-availability/kubernetes-development-environment.png)

**Şekil 4-8**. Dev makine ve bulut kubernetes çalışan

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Azure Kubernetes Hizmeti (AKS) ile başlayın

AKS kullanmaya başlamak için, Azure portalından veya CLI'yi kullanarak bir AKS kümesi dağıtırsınız. Bir Kubernetes kümesini Azure'a dağıtma hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)

AKS'nin bir parçası olarak varsayılan olarak yüklenen yazılımların herhangi biri için herhangi bir ücret yoktur. Tüm varsayılan seçenekler açık kaynak yazılımla uygulanır. AKS, Azure'da birden fazla sanal makine için kullanılabilir. Yalnızca seçtiğiniz işlem örneklerinin yanı sıra depolama ve ağ gibi tüketilen diğer temel altyapı kaynakları için ücretlendirilirsiniz. AKS kendisi için artımlı ücret yoktur.

Orijinal `kubectl` `.yaml` dosyalara dayalı olarak Kubernetes'e dağıtım hakkında daha fazla uygulama bilgisi için [AKS'de (Azure Kubernetes Hizmeti) eShopOnContainers'ı ayarlama yazısına](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service))bakın.

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Miğfer grafikleri ile Kubernetes kümelerine dağıtın

Bir uygulamayı Bir Kubernetes kümesine dağıtırken, `kubectl.exe` önceki bölümde belirtildiği gibi, özgün CLI aracını yerel biçime (dosyalara)`.yaml` dayalı dağıtım dosyalarını kullanarak kullanabilirsiniz. Ancak, karmaşık mikrohizmet tabanlı uygulamalar dağıtılırken olduğu gibi daha karmaşık Kubernetes uygulamaları [için, Helm](https://helm.sh/)kullanılması önerilir.

Miğfer Grafikleri, en karmaşık Kubernetes uygulamasını bile tanımlamanıza, sürüm kurmanıza, yüklemenize, paylaşmanıza, yükseltmenize veya geri almanıza yardımcı olur.

Daha da ileri giderek, [Azure'daki Azure Dev Alanları](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) gibi ek Kubernetes ortamları da Miğfer grafiklerini temel aldığı için Mik kullanımı önerilir.

Helm, Microsoft, Google, Bitnami ve Helm katılımcısı topluluğu ile işbirliği içinde [Cloud Native Computing Foundation (CNCF)](https://www.cncf.io/) tarafından sürdürülür.

Miğfer grafikleri ve Kubernetes hakkında daha fazla uygulama bilgisi için, [AKS'ye eShopOnContainers dağıtmak için Miğfer Şemaları Kullanarak](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts)sonrası bakın.

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Kubernetes uygulama yaşam döngüsünü sayıltın sayılsa için Azure Dev Spaces'i kullanın

[Azure Dev Spaces,](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) takımlar için hızlı, yinelemeli Kubernetes geliştirme deneyimi sağlar. Minimum geliştirme makinesi kurulumu ile, doğrudan Azure Kubernetes Service (AKS) içinde yinelemeli olarak kapsayıcıları çalıştırabilir ve kapsayıcıların hatasını ayıklayabilirsiniz. Visual Studio, Visual Studio Code veya komut satırı gibi tanıdık araçları kullanarak Windows, Mac veya Linux'ta geliştirebilirsiniz.

Belirtildiği gibi, Azure Dev Spaces kapsayıcı tabanlı uygulamaları dağıtırken Miğfer grafiklerini kullanır.

Azure Dev Spaces, Visual Studio 2017 veya Visual Studio Code'u kullanarak Azure'daki global Kubernetes kümesinde kodu hızla yineleyip hata ayıklamanızı sağladığı ndan, geliştirme ekiplerinin Kubernetes'te daha üretken olmasına yardımcı olur. Azure'daki Kubernetes kümesi paylaşılan yönetilen bir Kubernetes kümesidir, böylece ekibiniz birlikte çalışabilir. Kodunuzu yalıtılmış olarak geliştirebilir, ardından genel kümeye dağıtabilir ve bağımlılıkları çoğaltmadan veya alay etmeden diğer bileşenlerle uç-uç sınama yapabilirsiniz.

Şekil 4-9'da gösterildiği gibi, Azure Dev Spaces'teki en ayırt edici özellik kümedeki genel dağıtımın geri kalanına entegre çalıştırabilen 'boşluklar' oluşturma yeteneğidir:

![Azure Dev Spaces'te birden çok boşluk kullanımını gösteren diyagram.](./media/orchestrate-high-scalability-availability/use-multiple-spaces-azure-dev.png)

**Şekil 4-9**. Azure Geliştirme Alanlarında birden çok boşluk kullanma

Azure Dev Spaces, yeni sürümlerin test edilmesini kolaylaştırmak için üretim mikro hizmetlerini geliştirme kapsayıcısı örneğiyle saydam bir şekilde karıştırıp eşleyebilir. Temel olarak, Azure'da paylaşılan bir geliştirme alanı ayarlayabilirsiniz. Her geliştirici uygulamanın yalnızca kendi bölümüne odaklanabilir ve senaryolarının bağlı olduğu tüm diğer hizmetleri ve bulut kaynaklarını içeren bir geliştirme alanında yinelemeli olarak "önceden işlenmiş" kod geliştirebilir. Bağımlılıklar her zaman günceldir ve geliştiriciler üretimi yansıtan bir şekilde çalışır.

Azure Dev Spaces, ekip üyelerinizi kırma korkusu olmadan ve izole olarak çalışmanızı sağlayan bir alan konsepti sağlar. Bu özellik URL öneklerine dayanır; Bir kapsayıcının isteği için URL'de bir geliştirme alanı öneki kullanırsanız, Azure Geliştirme Spaces varsa, söz sözlere dağıtılan kapsayıcının özel bir sürümünü çalıştırAr. Aksi takdirde, genel/konsolide sürümü çalıştıracaktır.

Somut bir örnekte pratik bir görünüm elde etmek için [Azure Dev Spaces'teki eShopOnContainers wiki sayfasını](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) görebilirsiniz.

Daha fazla bilgi için Azure [Dev Spaces ile Takım Geliştirme](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore)makalesine bakın.

## <a name="additional-resources"></a>Ek kaynaklar

- **Azure Kubernetes Hizmeti (AKS) ile başlarken** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure Dev Alanları** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes' e ait.** Resmi site. \
  <https://kubernetes.io/>

## <a name="using-azure-service-fabric"></a>Azure Service Fabric Kullanma

Azure Hizmet Kumaşı, Microsoft'un tipik olarak tarzda yekpare olan "kutu" ürünleri sunmaktan hizmet sunmaya geçişinden kaynaklanmaktadır. Azure SQL Veritabanı, Azure Cosmos DB, Azure Hizmet Veri Servisi Veri Servisi veya Cortana'nın Arka Uç biçimli Hizmet Kumaşı gibi ölçekte büyük hizmetler oluşturma ve çalıştırma deneyimi. Platform zaman içinde daha fazla hizmet kabul olarak gelişti. Daha da önemlisi, Service Fabric yalnızca Azure'da değil, bağımsız Windows Server dağıtımlarında da çalışmak zorundaydı.

Service Fabric'in amacı, ekiplerin mikro hizmet yaklaşımı yla iş sorunlarını çözebilmeleri için, hizmet oluşturma nın ve altyapı kaynaklarını verimli bir şekilde kullanmanın zor sorunlarını çözmektir.

Service Fabric, mikro hizmetler yaklaşımını kullanan uygulamalar oluşturmanıza yardımcı olmak için iki geniş alan sağlar:

- Başarısız hizmetleri dağıtmak, ölçeklendirmek, yükseltmek, algılamak ve yeniden başlatmak, hizmet konumunu keşfetmek, durumu yönetmek ve sistem durumunu izlemek için sistem hizmetleri sağlayan bir platform. Yürürlükteki bu sistem hizmetleri, daha önce açıklanan mikro hizmetlerin birçok özelliğini mümkün kılar.

- Programlama API'leri veya çerçeveleri, mikro hizmetler olarak uygulamalar oluşturmanıza yardımcı olur: [güvenilir aktörler ve güvenilir hizmetler.](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) Microservice oluşturmak için herhangi bir kod seçebilirsiniz, ancak bu API'ler iş daha basit hale getirmek ve daha derin bir düzeyde platform ile entegre. Bu şekilde sağlık ve tanılama bilgilerini alabilir veya güvenilir devlet yönetiminden yararlanabilirsiniz.

Service Fabric, hizmetinizi nasıl oluşturduğunuza ilişkin olarak agnostiktir ve her teknolojiyi kullanabilirsiniz. Ancak, mikro hizmetler oluşturmayı kolaylaştıran yerleşik programlama API'leri sağlar.

Şekil 4-10'da gösterildiği gibi, Servis Kumaşı'nda basit işlemler veya Docker kapları olarak mikro hizmetler oluşturabilir ve çalıştırabilirsiniz. Konteyner tabanlı mikro hizmetleri aynı Service Fabric kümesi içinde proses tabanlı mikro hizmetlerle karıştırmak da mümkündür.

![Azure Hizmet Kumaşı kümelerinin karşılaştırımını gösteren diyagram.](./media/orchestrate-high-scalability-availability/azure-service-fabric-cluster-types.png)

**Şekil 4-10**. Azure Hizmet Kumaşı'nda mikro hizmetleri işlem veya kapsayıcı olarak dağıtma

İlk resimde, her düğüm her microservice için bir işlem çalışır süreçler olarak mikro hizmetler bakın. İkinci resimde, mikro hizmetleri, her düğümün Docker'ı mikro hizmet başına bir konteyner olmak üzere birkaç kapsayıcıyla çalıştırdığı kapsayıcılar olarak görürsünüz. Linux ve Windows ana bilgisayarlarına dayalı Service Fabric kümeleri sırasıyla Docker Linux kapsayıcılarını ve Windows Kapsayıcılarını çalıştırabilir.

Azure Hizmet Kumaşı'ndaki kapsayıcı desteği hakkında güncel bilgiler için [Service Fabric ve kapsayıcılara](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)bakın.

Service Fabric, fiziksel uygulamadan farklı bir mantıksal mimari (iş mikrohizmetleri veya Sınırlı Bağlamlar) tanımlayabileceğiniz bir platforma iyi bir örnektir. Örneğin, bir sonraki bölümde tanıtılan [Azure Hizmet Kumaşı'nda](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) [DevletE Uygun Güvenilir Hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) uygularsanız,["Durumsuz ve devlete açık mikro hizmetler](#stateless-versus-stateful-microservices)" birden çok fiziksel hizmetiçeren bir iş mikrohizmet konseptine sahipsiniz.

Şekil 4-10'da gösterildiği gibi ve mantıksal/iş mikrohizmet perspektifinden düşünerek, Service Fabric Stateful Reliable Service uygularken genellikle iki hizmet katmanı uygulamanız gerekir. Bunlardan ilki, birden çok bölümü işleyen arka uç durumlu güvenilir hizmettir (her bölüm devletli bir hizmettir). İkincisi, birden çok bölüm veya devlet hizmeti örnekleri arasında yönlendirme ve veri toplama dan sorumlu ön uç hizmeti veya Ağ Geçidi hizmetidir. Bu Ağ Geçidi hizmeti, arka uç hizmetine erişen yeniden deneme döngüleri ile istemci tarafı iletişimi de işler. Özel hizmetinizi uygularsanız ağ geçidi hizmeti olarak adlandırılır veya alternatif olarak kullanıma sunabileceğiniz Servis [Kumaşı ters proxy'yi](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)de kullanabilirsiniz.

![Kapsayıcılarda birkaç durumlu hizmeti gösteren diyagram.](./media/orchestrate-high-scalability-availability/service-fabric-stateful-business-microservice.png)

**Şekil 4-11**. Birkaç devlet hizmeti örnekleri ve özel bir ağ geçidi ön uç ile İş microservice

Her durumda, Service Fabric Stateful Reliable Services'ı kullandığınızda, birden çok fiziksel hizmetiçeren mantıksal veya iş microservice (Sınırlı Bağlam) da vardır. Her biri, Ağ Geçidi hizmeti ve Bölümleme hizmeti, Şekil 4-11'de gösterildiği gibi ASP.NET Web API hizmeti olarak uygulanabilir. Service Fabric konteynerler birkaç devlet güvenilir hizmetleri desteklemek için reçete vardır.

Service Fabric'te, hizmet gruplarını, orkestratör veya küme için paketleme ve dağıtım birimi olan [Service Fabric Application](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model)olarak gruplandırabilir ve dağıtabilirsiniz. Bu nedenle, Hizmet Kumaş Uygulaması bu özerk iş ve mantıksal microservice sınırı veya Sınırlı Bağlam eşlenebilir, böylece bu hizmetleri özerk olarak dağıtabilirsiniz.

### <a name="service-fabric-and-containers"></a>Servis Kumaş ve konteynerler

Service Fabric'teki konteynerlerle ilgili olarak, Hizmetleri Servis Kumaşı kümesiiçindeki konteyner görüntülerine de dağıtabilirsiniz. Şekil 4-12'nin gösterdiği gibi, çoğu zaman servis başına yalnızca bir kapsayıcı olacaktır.

![Bir veritabanına beslenen hizmet başına bir kapsayıcıyı gösteren diyagram.](./media/orchestrate-high-scalability-availability/azure-service-fabric-business-microservice.png)

**Şekil 4-12**. Service Fabric'te çeşitli hizmetler (konteynerler) ile iş mikrohizmeti

Hizmet Kumaşuygulaması, harici bir veritabanına erişen birkaç kapsayıcıyı çalıştırabilir ve tüm küme Bir Business Microservice'in mantıksal sınırı olacaktır. Ancak, "kenar araba" olarak adlandırılan kapsayıcılar (mantıksal bir hizmetin bir parçası olarak birlikte dağıtılması gereken iki kapsayıcı) Service Fabric'te de mümkündür. Önemli olan, bir iş microservice birkaç tutarlı elemanları etrafında mantıksal sınır olmasıdır. Çoğu durumda, tek bir veri modeli ile tek bir hizmet olabilir, ancak diğer bazı durumlarda da birkaç fiziksel hizmetler olabilir.

Şekil 4-13'te gösterildiği gibi, aynı Service Fabric uygulamasında, süreçlerdeki hizmetleri ve kapsayıcıdaki hizmetleri karıştırabileceğinizi unutmayın.

![Aynı uygulamadaki işlemlerdeki ve kapsayıcılarda hizmetleri gösteren diyagram.](./media/orchestrate-high-scalability-availability/business-microservice-mapped-to-service-fabric-application.png)

**Şekil 4-13**. Konteynerler ve devlet hizmetleri ile Hizmet Kumaş uygulamasına eşlenen iş microservice

Azure Hizmet Kumaşı'nda konteyner desteği hakkında daha fazla bilgi için [Service Fabric ve kapsayıcılara](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview)bakın.

## <a name="stateless-versus-stateful-microservices"></a>Stateless karşı stateful microservices

Daha önce de belirtildiği gibi, her microservice (mantıksal Sınırlı Bağlam) etki alanı modeli (veri ve mantık) sahibi olmalıdır. Durum dışı mikro hizmetler söz konusu olduğunda, veritabanları sql server veya Azure Cosmos DB veya MongoDB gibi NoSQL seçenekleri gibi ilişkisel seçenekleri kullanan harici olacaktır.

Ancak hizmetlerin kendisi de Service Fabric'te devlete ait olabilir, bu da verilerin mikro hizmet içinde bulunduğu anlamına gelir. Bu veriler yalnızca aynı sunucuda değil, mikrohizmet işlemi içinde, bellekte ve sabit disklerde kalıcı olarak bulunabilir ve diğer düğümlere çoğaltılabilir. Şekil 4-14 farklı yaklaşımları göstermektedir.

![Durumsuz ve durumlu bir hizmetin karşılaştırılmasını gösteren diyagram.](./media/orchestrate-high-scalability-availability/stateless-vs-stateful-microservices.png)

**Şekil 4-14**. Stateless karşı stateful microservices

Devletsiz hizmetlerde, durum (kalıcılık, veritabanı) mikro hizmet dışında tutulur. Devlet hizmetlerinde, devlet mikro hizmet içinde tutulur. Vatansız bir yaklaşım son derece geçerlidir ve uygulanması, geleneksel ve iyi bilinen kalıplara benzediğinden, devlete uygun mikro hizmetlerden daha kolaydır. Ancak devletsiz mikro hizmetler, süreç ve veri kaynakları arasında gecikme cezası uygular. Ayrıca, ek önbellek ve kuyruklarla performansı artırmaya çalışırken daha fazla hareketli parça içerirler. Sonuç olarak, çok fazla katmanı olan karmaşık mimarilere sahip olabilirsiniz.

Buna karşılık, etki alanı mantığı ve veri arasında gecikme yok, çünkü [durumlu mikro hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) gelişmiş senaryolarda excel olabilir. Ağır veri işleme, oyun geri uçları, hizmet olarak veritabanları ve diğer düşük gecikme li senaryoların tümü, yerel durumu daha hızlı erişim sağlayan devlet hizmetlerinden yararlanır.

Devletsiz ve devlethizmetleri birbirini tamamlar. Örneğin, Şekil 4-14'te doğru diyagramda görebileceğiniz gibi, durumlu bir hizmet birden çok bölüme ayrılabilir. Bu bölümlere erişmek için, bölüm anahtarlarını temel alan her bölümü nasıl ele alabileceğinizi bilen bir ağ geçidi hizmeti gibi davranan bir hizmete ihtiyacınız olabilir.

Devlet hizmetlerinin dezavantajları vardır. Ölçeklendirilecek yüksek bir karmaşıklık düzeyi empoze ederler. Genellikle dış veritabanı sistemleri tarafından uygulanacak işlevsellik, durum sallanabilir mikro hizmetler arasında veri çoğaltma ve veri bölümleme gibi görevler için ele alınmalıdır. Ancak bu, [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) gibi bir orkestratörün [güvenilir güvenilir hizmetlerine](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) sahip olduğu alanlardan biridir ve Güvenilir Hizmetler [API'sini](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) ve [Güvenilir Aktörleri](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction)kullanarak devlete uygun mikro hizmetlerin geliştirilmesini ve yaşam döngüsünü basitleştirerek en çok yardımcı olabilir.

Stateful hizmetleri sağlayan diğer microservice çerçeveleri, Aktör desen destek ve iş mantığı ve veri arasında hata toleransı ve gecikme geliştirmek Microsoft [Orleans](https://github.com/dotnet/orleans), Microsoft Research, ve [Akka.NET](https://getakka.net/). Her iki çerçeve de şu anda Docker'a verdikleri desteği artırıyor.

Docker konteynerlerinin kendilerinin de vatansız olduğunu unutmayın. Devlet hizmeti uygulamak istiyorsanız, daha önce belirtilen ek açıklayıcı ve üst düzey çerçevelerden birine ihtiyacınız vardır.

## <a name="using-azure-service-fabric-mesh"></a>Azure Servis Kumaş Örgü kullanma

Azure Service Fabric Mesh, geliştiricilerin herhangi bir altyapıyı yönetmeden kritik görev uygulamaları oluşturmasına ve dağıtmasına olanak tanıyan tam olarak yönetilen bir hizmettir. Service Fabric Mesh’i kullanarak, talep üzerine ölçeklendirilen güvenli ve dağıtılmış mikro hizmet uygulamaları oluşturup çalıştırabilirsiniz.

Şekil 4-15'te gösterildiği gibi, Hizmet Kumaş ı Örgü'de barındırılan uygulamalar, altyapının güç yetirilmesi konusunda endişelenmeden çalışır ve ölçeklendirilebilir.

![Yerel bir depodan Hizmet Kumaş Kafesi'ne dağıtım gösteren diyagram.](media/orchestrate-high-scalability-availability/deploy-microservice-containers-apps-service-fabric-mesh.png)

**Şekil 4-15**. Servis Kumaş Örgü bir microservice / konteyner uygulaması dağıtma

Kapakların altında, Servis Kumaş Örgü binlerce makine kümelerinden oluşmaktadır. Tüm küme işlemleri geliştiriciden gizli olarak gerçekleştirilir. Kapsayıcılarınızı yüklemeniz ve ihtiyacınız olan kaynakları, kullanılabilirlik gereksinimlerini ve kaynak sınırlarını belirtmeniz yeterlidir. Service Fabric Mesh, uygulama dağıtımınızın ihtiyaç duyduğu altyapıyı otomatik olarak dağıtır ve altyapı hatalarını da yöneterek uygulamalarınızın yüksek oranda kullanılabilir durumda olmasını sağlar. Altyapı konusunda değil yalnızca uygulamanızın durumuna ve yanıt süresine dikkat etmeniz gerekir.

Daha fazla bilgi için [Service Fabric Mesh belgelerine](https://docs.microsoft.com/azure/service-fabric-mesh/)bakın.

## <a name="choosing-orchestrators-in-azure"></a>Azure'da orkestratör seçimi

Aşağıdaki tablo, iş yüklerine ve işletim sistemi odağına bağlı olarak hangi orkestratörün kullanılacağı konusunda rehberlik sağlar.

![Kubernetes ve Servis Kumaşı'nı karşılaştıran bir tablonun görüntüsü.](media/orchestrate-high-scalability-availability/orchestrator-selection-azure-guidance.png)

**Şekil 4-16**. Azure kılavuzunda orkestra seçimi

>[!div class="step-by-step"]
>[Önceki](soa-applications.md)
>[Sonraki](deploy-azure-kubernetes-service.md)
