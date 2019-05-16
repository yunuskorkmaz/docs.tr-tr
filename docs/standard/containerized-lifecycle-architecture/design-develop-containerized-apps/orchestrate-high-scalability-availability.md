---
title: Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme
description: Gerçek üretimde uygulamaların dağıtılması ve sistem durumu, iş yükü ve tüm kapsayıcıların yaşam döngüsü işleyen düzenleyicilerle yönetilen gerekir.
ms.date: 02/15/2019
ms.openlocfilehash: 6cb41e632db7c7c6b9412bf54d2efeb44deee80f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644721"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Yüksek ölçeklenebilirlik ve kullanılabilirlik için mikro hizmetleri ve çok kapsayıcılı uygulamaları yönetme

Uygulamanız üzerinde mikro hizmet tabanlı ya da birden çok kapsayıcıya bölme düzenleyicileri kullanarak üretime hazır uygulamalar için gereklidir. Böylece bir geliştirme ve dağıtım açısından otonom mikro hizmet tabanlı bir yaklaşım, daha önce tanıtılan her mikro hizmet kendi modeli ve veri sahibi. Ancak oluşan daha geleneksel bir uygulama (SOA gibi) birden çok Hizmetleri olsa da birden çok kapsayıcı veya hizmet dağıtılmış bir sistemde dağıtılması gereken bir tek iş uygulaması oluşturan olursunuz. Ölçeği genişletme ve yönetmek için bu tür sistemler karmaşıktır; Bu nedenle, üretime hazır ve ölçeklenebilir çok kapsayıcılı bir uygulama istiyorsanız kesinlikle bir orchestrator gerekir.

Şekil 4-6, bir uygulama (kapsayıcılar) birden çok mikro hizmetlerden oluşan bir küme içine dağıtım gösterilmektedir.

![Bir kümede oluşturulmuş Docker uygulamaları: Her bir hizmet örneği için bir kapsayıcı kullanırsınız. Docker kapsayıcıları "dağıtım" birimleridir ve çok sayıda kapsayıcı Docker.A ana bilgisayar örneği işleyen bir kapsayıcıdır](./media/image6.png)

**Şekil 4-6**. Kapsayıcıları kümesi

Mantıksal bir yaklaşım gibi görünüyor. Ancak Yük Dengeleme, Yönlendirme ve oluşan bu uygulamaları işlemlerini nasıl işlediğinin?

Docker komut satırı arabirimi (CLI) bir konak üzerindeki bir kapsayıcı yönetme gereksinimlerini karşılayan, ancak daha karmaşık dağıtılmış uygulamaların birden çok konak üzerinde dağıtılan birden çok kapsayıcı yönetmek için söz konusu olduğunda kısa döner. Çoğu durumda, otomatik olarak kapsayıcıları Başlat, kapsayıcı görüntüsü başına birden çok örneği ile ölçeği genişletme, bunları askıya alma veya gerekli ve ideal olarak ayrıca nasıl veri ve ağ gibi kaynaklara erişim denetimini kapatma bir yönetim platformunun gerekir depolama alanı.

Kapsayıcılara veya basit oluşturulmuş uygulamalar ve mikro Hizmetleri daha büyük kuruluş uygulamaları doğru taşıma yönetimini ötesine gitmek için düzenleme ve platformları kümeleme için etkinleştirmeniz gerekir.

Yapı büyük, Kurumsal, mikro hizmet tabanlı kullanıyorsanız bir mimari ve geliştirme açısından bakıldığında, uygulamalar, aşağıdaki platformları ve Gelişmiş senaryolar destekleyen ürünleri anlamak önemlidir:

- **Kümeler ve düzenleyiciler.** Uygulamalarının çoğu Docker konakları arasında Ölçeklendirmesi gerektiğinde, olduğu gibi büyük mikro hizmet tabanlı uygulamaları ile tüm bu konak tarafından temel platform karmaşıklığını özetleyen tek bir küme halinde yönetmek için önemlidir. Neler kapsayıcı kümeleri ve düzenleyicileri sağlar olmasıdır. Azure Service Fabric ve Kubernetes düzenleyicileri örnekleridir. Kubernetes, azure'da Azure Kubernetes hizmeti aracılığıyla kullanılabilir.

- **Zamanlayıcılar.** *Zamanlama* özelliğine de zamanlayıcılar Bunu yapmak için bir kullanıcı arabirimi sağlamak için bir kümedeki kapsayıcıları başlatmak bir yöneticinin anlamına gelir. Bir küme Zamanlayıcı çeşitli sorumlulukları vardır: küme kaynaklarını verimli bir şekilde kullanmak için verimli bir şekilde düğümleri veya konaklar arasında Yük Dengeleme kapsayıcıları için kullanıcı tarafından sağlanan kısıtlamaları ayarlamak ve yüksek sağlarken hatalarına karşı güçlü Kullanılabilirlik.

Genellikle farklı satıcılar tarafından sağlanan ürün iki yetenekleri sağlamak için bir küme ve bir zamanlayıcı yakından ilişkilidir. Aşağıdaki bölümde, kümeler ve planlayıcılar için sahip olduğunuz yazılım seçenekleri ve en önemli platform gösterilmektedir. Bu düzenleyiciler, Azure gibi genel bulutlarda yaygın olarak sunulur.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Yazılım platformlarının kümeleme kapsayıcı, düzenleme ve zamanlama için

| Platform | Açıklamalar |
|:---:|:---|
| **Kubernetes** <br/> ![Kubernetes logosu](./media/kubernetes-logo.png) | [*Kubernetes* ](https://kubernetes.io/) küme altyapısı ve kapsayıcı özelliklerini düzenlemek için zamanlama aralıkları işlevselliği sağlayan bir açık kaynaklı üründür. Bu ana bilgisayar kümeleri arasında dağıtım, ölçeklendirme ve uygulama kapsayıcıların işlemlerini otomatikleştirmenizi sağlar. <br/> <br/> *Kubernetes* uygulama kapsayıcıları kolay yönetim ve bulma için mantıksal birimler halinde gruplandırır kapsayıcı merkezli bir altyapı sağlar. <br/> <br/> *Kubernetes* Linux'ta, Windows daha az olgun olgun olduğu. |
| **Azure Kubernetes Service'i (AKS)** <br/> ![Azure Kubernetes hizmeti logosu](./media/aks-logo.png) | [Azure Kubernetes Service (AKS)](https://azure.microsoft.com/services/kubernetes-service/) olduğu yönetilen bir Kubernetes kapsayıcı düzenleme hizmeti azure'da Kubernetes küme yönetimi, dağıtımı ve işlemleri basitleştirir. |
| **Azure Service Fabric** <br/> ![Azure Service Fabric logosu](./media/service-fabric-logo.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) uygulamaları oluşturmaya yönelik bir Microsoft mikro hizmet platformudur. Bu bir [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) , hizmetleri ve makine kümeleri oluşturur. Service Fabric Hizmetleri düz işlemleri veya kapsayıcıları olarak dağıtabilirsiniz. Hatta işlemlerde karışımı Hizmetleri aynı uygulama ve küme kapsayıcılara hizmetleriyle alabilir. <br/> <br/> *Service Fabric* kümeleri, azure'da, şirket içi veya buluttaki dağıtılabilir. Ancak, dağıtım azure'da yönetilen bir yaklaşım ile basitleştirilmiştir. <br/> <br/> *Service Fabric* ek ve isteğe bağlı sağlar öngörücü [Service Fabric programlama modellerini](https://azure.microsoft.com/documentation/articles/service-fabric-choose-framework/) gibi [durum bilgisi olan hizmetler](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-services-introduction/) ve [Reliable Actors](https://azure.microsoft.com/documentation/articles/service-fabric-reliable-actors-introduction/) . <br/> <br/> *Service Fabric* (yıl içinde Windows gelişen) Windows, daha az olgun Linux'ta olgun bileşenidir. <br/> <br/> Hem Linux hem de Windows kapsayıcıları Service Fabric'te 2017 itibarıyla desteklenir. |
| **Azure Service Fabric Mesh** <br/> ![Azure Service Fabric kafes logosu](./media/azure-service-fabric-mesh-logo.png) | [*Azure Service Fabric Mesh* ](https://docs.microsoft.com/azure/service-fabric-mesh/service-fabric-mesh-overview) aynı güvenilirlik, görev açısından kritik performans ve ölçek Service fabric sunar, ancak ayrıca tümüyle yönetilen ve sunucusuz bir platform sunar. Bir küme sanal makineleri, depolama veya ağ yapılandırmasını yönetmenize gerek yoktur. Yalnızca uygulamanızın geliştirmeye odaklanın. <br/> <br/> *Service Fabric Mesh* tüm programlama dili ve framework tercih ettiğiniz geliştirme olanak tanıyan, hem Windows hem de Linux kapsayıcıları destekler.

## <a name="using-container-based-orchestrators-in-azure"></a>Azure'da kapsayıcı tabanlı düzenleyicileri kullanma

Docker kapsayıcıları desteği yanı sıra Docker kümeler ve düzenleme desteği, Azure, Amazon EC2 Container Service ve Google Container altyapısı dahil olmak üzere birden fazla bulut satıcılarına sunar. Azure Docker, Azure Kubernetes Service (AKS), Azure Service Fabric ve Azure Service Fabric Mesh küme ve orchestrator destek sağlar.

## <a name="using-azure-kubernetes-service"></a>Azure Kubernetes hizmetini kullanarak

Bir Kubernetes kümesi birkaç Docker ana bilgisayarları havuzları ve herhangi bir sayıda container Instances ile ölçek genişletme ve küme içinde birden çok kapsayıcı dağıtma için bunları bir tek sanal Docker konağı olarak kullanıma sunar. Küme ölçeklenebilirliği, sistem durumu ve benzeri gibi tüm karmaşık yönetim ayarlamaları, işler.

AKS, oluşturma, yapılandırma ve kapsayıcılı uygulamaları çalıştırmak için önceden yapılandırılmış sanal makinelerin azure'da bir küme yönetimi basitleştirmek için bir yol sağlar. Popüler açık kaynak planlama ve düzenleme araçlarının iyileştirilmiş yapılandırmalarını kullanarak AKS mevcut becerilerinizi kullanabilir veya Microsoft azure'daki kapsayıcı tabanlı uygulamaları dağıtmak ve yönetmek için topluluk uzmanlığından geniş ve büyüyen bir gövdesi üzerinde çizim yapmanızı sağlar .

Azure Kubernetes hizmeti popüler Docker kümeleme açık kaynaklı araçların ve teknolojilerin yapılandırmasını özellikle Azure'a yönelik en iyi duruma getirir. Hem kapsayıcılarınız hem de uygulama yapılandırmanız için taşınabilirlik sunan bir açık çözümü sahip olursunuz. Boyutu, konak sayısını ve düzenleyici araçlarını seçmeniz ve diğer her şey AKS işler.

![Kubernetes kümesi yapısı: DNS, Zamanlayıcı, proxy vb. işleyen bir ana düğümü ve kapsayıcıları barındıran birden çok çalışan düğümü yoktur.](media/image36.png)

**Şekil 4-7**. Kubernetes küme Basitleştirilmiş yapısı ve topolojisi

Şekil 4-7 burada küme eşgüdümüyle çoğunu bir ana düğüm (VM) denetler ve bir uygulama açısından tek bir havuz olarak yönetilen düğümlerin geri kalanı kapsayıcınızı da dağıtabilirsiniz bir Kubernetes kümesi yapısı gösterilmektedir. Bu, binlerce veya on binlerce kapsayıcının ölçeğini olanak sağlar.

## <a name="development-environment-for-kubernetes"></a>Kubernetes için geliştirme ortamı

Geliştirme ortamında, [Temmuz 2018'de duyurulan Docker](https://blog.docker.com/2018/07/kubernetes-is-now-available-in-docker-desktop-stable-channel/), Kubernetes de çalıştırabilir (Windows 10 veya macOS) bir tek bir geliştirme makinesinde yalnızca yükleyerek [Docker Masaüstü](https://www.docker.com/community-edition). Daha sonra işlenmek üzere buluta (AKS) daha ayrıntılı tümleştirme testleri, Şekil 4-8 ' gösterildiği gibi dağıtabilirsiniz.

![Docker üzerinde Temmuz ' 2018 ile Docker masaüstü geliştirme makine desteği Kubernetes kümeleri için duyurdu.](media/kubernetes-development-environment.png)

**Şekil 4-8**. Kubernetes geliştirme makinesi ve bulutta çalışan

## <a name="get-started-with-azure-kubernetes-service-aks"></a>Azure Kubernetes Service (AKS) ile çalışmaya başlama

AKS'ı kullanmaya başlamak için Azure portalından veya CLI kullanarak bir AKS kümesi dağıtın. Bir Azure Container Service kümesi dağıtma hakkında daha fazla bilgi için bkz. [Azure Kubernetes Service (AKS) kümesini dağıtma](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

Herhangi birini varsayılan olarak, AKS bir parçası olarak yüklenen yazılım için herhangi bir ücret yoktur. Tüm varsayılan seçenekleri ile açık kaynaklı yazılım uygulanır. AKS, azure'da birden çok sanal makine için kullanılabilir. Yalnızca seçtiğiniz işlem örnekleri yanı sıra, depolama ve ağ gibi kullanılan temel altyapı kaynakları için ücret ödersiniz. AKS kendisi için artımlı ücretlendirme yoktur.

Kubernetes dağıtımı hakkında bilgi için daha fazla uygulama temel `kubectl` ve orijinal `.yaml` dosyaları, üzerinde gönderisine bakın [hizmetine (Azure Kubernetes hizmeti) AKS'de ayarlama](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.-Setting-the-solution-up-in-AKS-(Azure-Kubernetes-Service)).

## <a name="deploy-with-helm-charts-into-kubernetes-clusters"></a>Helm grafikleri ile Kubernetes küme halinde dağıtın

Bir Kubernetes kümesine uygulama dağıtma, özgün kullanabileceğiniz `kubectl.exe` tabanlı dağıtım dosyalarını kullanarak CLI aracı yerel Biçimlendir (`.yaml` dosyaları), önceki bölümde belirtildiği gibi zaten. Ancak, daha karmaşık Kubernetes uygulamaları için gibi karmaşık mikro hizmet tabanlı uygulamaları dağıtırken kullanılacak önerilir [Helm](https://helm.sh/).

Helm grafikleri sürümü, yükleme, paylaşım, yükseltme veya geri alma bile en karmaşık Kubernetes uygulamasını tanımlamanıza yardımcı olur.

Daha fazla devam, Helm kullanımı da önerilir çünkü Azure, ek Kubernetes ortamlarda gibi [Azure geliştirme alanları](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) de Helm grafikleri üzerinde temel alır.

Helm tarafından korunduğu [bulut yerel bilgisayar Foundation (CNCF)](https://www.cncf.io/) Microsoft, Google, Bitnami ve Helm katkıda bulunan topluluğunun işbirliğiyle.

Daha fazla uygulama hakkında bilgi için Helm grafikleri ve Kubernetes gönderiye bakın [hizmetine AKS'ye dağıtma için Helm grafikleri kullanarak](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.1-Deploying-to-AKS-using-Helm-Charts).

## <a name="use-azure-dev-spaces-for-you-kubernetes-application-lifecycle"></a>Azure geliştirme alanları, Kubernetes uygulama yaşam döngüsü kullanın.

[Azure geliştirme alanları](https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces) takımlar için hızlı, yinelemeli bir Kubernetes geliştirme deneyimi sağlar. En az bir geliştirme makinesi kuruluma yinelemeli olarak çalıştırın ve doğrudan Azure Kubernetes Service (AKS) kapsayıcıları hata ayıklama. Windows, Mac veya Visual Studio, Visual Studio Code veya komut satırı gibi tanıdık araçlar kullanarak Linux üzerinde geliştirme yapabilirsiniz.

Belirtildiği gibi Azure geliştirme alanları Helm grafikleri kapsayıcı tabanlı uygulamaları dağıtırken kullanır.

Azure geliştirme alanları geliştirme ekipleri, hızla yineleyin ve yalnızca Visual Studio 2017 veya Visual Studio Code kullanarak azure'da genel bir Kubernetes kümesi doğrudan kodda hata ayıklama izin verdiğinden, Kubernetes üzerinde daha üretken olmanıza yardımcı olur. Azure'da Kubernetes kümesi paylaşılan olduğunu, takımınızın işbirliği içinde birlikte çalışabilmesi için Kubernetes kümesi yönetilen. Yalıtım, kodunuzda geliştirin sonra genel kümeye dağıtın ve uçtan uca çoğaltmak veya bağımlılıkları sahte işlem olmadan diğer bileşenlerle testi gerçekleştirin.

4-9, şekilde gösterildiği gibi Azure geliştirme alanları en ayırt edici özelliği 'geri kalanı kümedeki genel dağıtımı için tümleşik çalıştırabilirsiniz alanları' oluşturma özelliktir.

![Azure geliştirme alanları, saydam karıştırın ve yeni sürümlerini test etmeye kolaylaştırmak için geliştirme kapsayıcı örneği, üretim mikro hizmetler eşleştirin.](media/image38.png)

**Şekil 4-9**. Azure geliştirme alanlarında birden çok alanları kullanma

Temel olarak, bir Azure paylaşılan geliştirme alanında ayarlayabilirsiniz. Her geliştirici yalnızca uygulama kendi parçası üzerinde odaklanın yinelemeli olarak tüm diğer hizmetler içeren bir geliştirme alanında "önceden kaydedilmiş" kod geliştirin ve bulut kendi senaryoları bağımlı kaynakları. Bağımlılıkları her zaman güncel olduğundan ve geliştiricilerin üretim yansıtan bir şekilde çalışıyoruz.

Azure geliştirme alanları, yalıtım ve ekip üyeleriniz bozucu ödemeden olmadan çalışmanıza olanak sağlayan bir alan kavramı sağlar. Bu özellik, URL ön ekleri üzerinde temel alır. bir kapsayıcının istek için URL'de bir geliştirme alanı ön ekini kullanıyorsanız, varsa, Azure geliştirme alanları için bu alanı, dağıtılan kapsayıcı özel bir sürümünü çalıştırır. Aksi takdirde, genel/birleşik sürümü çalışacaktır.

Gördüğünüz [hizmetine wiki sayfasında Azure geliştirme alanları](https://github.com/dotnet-architecture/eShopOnContainers/wiki/10.2-Using-Azure-Dev-Spaces-and-AKS) somut örneği pratik bir görünüm elde edin.

Daha fazla bilgi için makaleye bakın [Azure geliştirme alanları ile takım geliştirme](https://docs.microsoft.com/azure/dev-spaces/team-development-netcore).

## <a name="additional-resources"></a>Ek kaynaklar

- **Azure Kubernetes Service (AKS) ile çalışmaya başlama** \
  <https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal>

- **Azure geliştirme alanları** \
  <https://docs.microsoft.com/azure/dev-spaces/azure-dev-spaces>

- **Kubernetes.** Resmi sitesi. \
  <https://kubernetes.io/>

## <a name="using-azure-service-fabric"></a>Azure Service Fabric Kullanma

Azure Service Fabric, Microsoft'un geçiş stili genellikle tek parçalı, "kutu" ürünleri, hizmetleri sunmak için teslim öğesinden gelen çıkan. Service Fabric oluşturma ve büyük hizmetlerini uygun ölçekte, Azure SQL veritabanı, Azure Cosmos DB, Azure Service Bus veya Cortana'nın arka uç, gibi işletim deneyimini şeklinde. Bunu daha da fazla Hizmetleri benimsenen gibi platform zaman içinde gelişerek. Önemlisi, yalnızca Azure aynı zamanda tek başına Windows Server dağıtımlarındaki çalıştırmak Service Fabric vardı.

Takımlar bir mikro hizmet yaklaşımı kullanarak iş sorunlarını çözebilir. böylece, oluşturma ve bir hizmetin çalıştırılması ve altyapı kaynaklarını verimli bir şekilde yararlanarak sabit sorunları çözmek için Service Fabric amacı olan.

Service Fabric, mikro hizmetler yaklaşımı kullanan uygulamalar oluşturmanıza yardımcı olmak üzere iki geniş alanları sağlar:

- Dağıtmak için sistem hizmetleri sağlayan bir platform ölçeklendirme, yükseltme, algılamanıza ve başarısız hizmetlerini yeniden başlatın, hizmet konumu bulmak, durumunu yönetme ve durumunu izleyin. Bu sistem hizmetlerini etkin mikro Hizmetleri daha önce açıklanan özelliklerini etkinleştirir.

- Programlama API'leri veya çerçeveleri, mikro hizmetler olarak uygulamalar oluşturmanıza yardımcı olacak: [reliable actors ve güvenilir hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Mikro hizmet oluşturmak için herhangi bir kod seçebilirsiniz ancak bu API'leri işi daha basit hale ve bunlar daha ayrıntılı bir platform ile tümleştirin. Güvenilir durum yönetimi, sistem durumu ve tanılama bilgileri veya alabilirsiniz bu şekilde yararlanabilirsiniz.

Service Fabric hizmetinizin nasıl oluşturulacağına göre belirsiz olduğundan ve tüm teknolojileri kullanabilirsiniz. Bununla birlikte, mikro hizmetler oluşturmayı kolay hale getiren yerleşik programlama API'leri sağlar.

Şekil 4-10'da gösterildiği gibi oluşturun ve Service Fabric'te mikro Hizmetleri; basit işlemler ya da Docker kapsayıcıları olarak çalışır. Kapsayıcı tabanlı mikro hizmetler ile işlem tabanlı mikro hizmetler aynı Service Fabric kümesi içinde karma olarak mümkündür.

![Karşılaştırması, Azure service Fabric kümeleri: Mikro hizmetler olarak her düğüme bir işlem için her bir mikro hizmetin çalıştığı işlemleri; Mikro hizmetler olarak her düğüme birkaç kapsayıcılar ile Docker çalıştığı kapsayıcılar mikro hizmet başına bir kapsayıcı.](./media/azure-service-fabric-cluster-types.png)

**Şekil 4-10**. Mikro hizmetler, işlemler veya Azure Service Fabric'teki kapsayıcıları olarak dağıtma

Linux ve Windows ana bilgisayarlarını temel alan Service Fabric kümelerinde Docker Linux kapsayıcıları ve Windows kapsayıcıları sırasıyla çalıştırabilirsiniz.

Azure Service fabric'te kapsayıcı desteği hakkında güncel bilgiler için bkz: [Service Fabric ve kapsayıcılar](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric iyi bir platformun burada bir farklı mantıksal mimarisine (iş mikro hizmetler veya sınırlanmış Bağlamlar) fiziksel uygulaması tanımlayabilirsiniz. bir örnektir. Örneğin, uygulamanız [durum bilgisi olan Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) içinde [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), sonraki bölümde tanıtılır "[durum bilgisi olmayan durum bilgisi olan mikro Hizmetlerkarşı](#stateless-versus-stateful-microservices), "birden çok fiziksel Hizmetleri ile iş mikro hizmet kavramını sahip.

Şekil 4-10 yanı sıra, bir Service Fabric durum bilgisi olan güvenilir hizmet uygularken mantıksal/iş mikro hizmet açısından, düşünme olarak gösterilen, genellikle iki katmanda Hizmetleri uygulamak ihtiyacınız olacak. İlk (her bölüm bir durum bilgisi olan bir hizmettir) birden çok bölüm işleme arka uç durum bilgisi olan güvenilir hizmetidir. Ön uç hizmeti veya birden çok bölüm ya da durum bilgisi olan hizmet örnekleri arasında yönlendirme ve veri toplama sorumlu ağ geçidi hizmeti saniyedir. Bu ağ geçidi hizmeti, yeniden deneme döngüleri ile arka uç hizmetine erişim ayrıca istemci-tarafı iletişimi gerçekleştirir. Bir ağ geçidi hizmeti, özel bir hizmet ekleme ya da alternatif olarak kullanıma hazır Service Fabric ayrıca kullanabileceğiniz çağırdı [ters proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![Service Fabric, kapsayıcılarda birkaç durum bilgisi olan reliable services desteklemek için reçete sahiptir.](./media/service-fabric-stateful-business-microservice.png)

**Şekil 4-11**. İş bir mikro hizmet birkaç durum bilgisi olan hizmet örnekleri ve özel ağ geçidi ön uç

Herhangi bir durumda, Service Fabric durum bilgisi olan Reliable Services kullandığınızda, ayrıca, birden çok fiziksel hizmetlerinden oluşur bir mantıksal veya iş mikro hizmet (içerik sınırlanmış) vardır. Bunları, ağ geçidi hizmet ve bölüm hizmeti her ASP.NET Web API Hizmetleri olarak Şekil 4-11'de gösterildiği gibi uygulanabilir.

Service Fabric'te, Grup ve hizmet olarak grupları dağıtma bir [Service Fabric uygulaması](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), paketleme ve dağıtım için orchestrator ya da küme biriminin olduğu. Bu hizmetler otonom olarak dağıtabilirsiniz, böylece bu nedenle, Service Fabric uygulaması bu otonom iş ve mantıksal bir mikro hizmet sınırı veya içerik sınırlanmış, de eşleştirilebilir.

### <a name="service-fabric-and-containers"></a>Service Fabric ve kapsayıcılar

Service Fabric'teki kapsayıcıları onaylamaz, Service Fabric kümesi dahilindeki kapsayıcı görüntülerinizi Hizmetleri'nde dağıtabilirsiniz. Şekil 4-12 gösterildiği gibi çoğu zaman yalnızca olmayacaktır hizmet başına bir kapsayıcı.

![Harici bir veritabanına erişme birkaç kapsayıcıları Service Fabric uygulaması çalıştırabilir ve tüm küme iş mikro hizmetlerin ayırt mantıksal sınır olacaktır](./media/azure-service-fabric-business-microservice.png)

**Şekil 4-12**. Çeşitli Hizmetleri (kapsayıcılar) Service Fabric ile mikro iş

Bununla birlikte, sözde "sepet" (mantıksal bir hizmetin parçası olarak birlikte dağıtılmış olması gereken iki kapsayıcı) de Service Fabric'te olası kapsayıcılardır. Önemli olan iş mikro hizmet birkaç cohesive öğeleri mantıksal sınırlarından olmasıdır. Çoğu durumda, bir tek veri modeli ile tek bir hizmet olabilir, ancak diğer bazı durumlarda, bazı fiziksel hizmetleri de olabilir.

Şekil 4-13'te gösterildiği gibi işlemlerde, hizmetler ve kapsayıcılar, aynı Service Fabric uygulama Hizmetleri'nde karıştırabilirsiniz unutmayın.

![Hizmetleri ve kapsayıcıları hem aynı düğümde çalışan bir service fabric uygulaması.](./media/business-microservice-mapped-to-service-fabric-application.png)

**Şekil 4-13**. Kapsayıcılar ve durum bilgisi olan hizmetler ile bir Service Fabric uygulaması için eşleştirilmiş iş mikro hizmet

Azure Service fabric'te kapsayıcı desteği hakkında daha fazla bilgi için bkz: [Service Fabric ve kapsayıcılar](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Durum bilgisiz ve durum bilgisi olan mikro hizmetler

Her mikro hizmet (mantıksal içerik sınırlanmış), daha önce bahsedildiği gibi etki alanı modeli (veri ve mantıksal) sahip olmanız gerekir. Durum bilgisi olmayan mikro hizmetler söz konusu olduğunda, veritabanları, SQL Server gibi ilişkisel seçenekleri veya Azure Cosmos DB veya MongoDB gibi NoSQL seçenekleri kullanan dış olacaktır.

Ancak hizmetler ayrıca veri mikro hizmet içinde bulunduğu anlamına gelir Service Fabric durum bilgisi olan olabilir. Bu veriler aynı sunucuda değil, ancak mikro hizmet işlemi, bellek içinde mevcut olmayabilir ve sabit sürücülerde kalıcı ve diğer düğümlere çoğaltılır. Şekil 4-30 farklı yaklaşımlar gösterir.

![Durum bilgisi olmayan hizmetler (Kalıcılık, veritabanı) durumunu mikro hizmet dışında tutulur. İçinde durum bilgisi olan hizmetler durumu mikro hizmet içinde tutulur.](./media/stateless-vs-stateful-microservices.png)

**Şekil 4-14**. Durum bilgisiz ve durum bilgisi olan mikro hizmetler

Durum bilgisi olmayan bir yaklaşım mükemmel geçerli olduğundan ve durum bilgisi olan mikro hizmetler geleneksel ve iyi bilinen desenleri için benzer bir yaklaşım olduğundan uygulamak daha kolaydır. Ancak, durum bilgisi olmayan mikro hizmetler, işlem ve veri kaynakları arasındaki gecikme süresini büyük oranda yansıtmaktadır. Bunlar ayrıca ek önbellek ve Kuyruklar ile performansı artırmak çalışırken daha fazla hareketli parça içerir. Sonuç, çok fazla katman karmaşık mimarilerin kalabilirsiniz emin olur.

Buna karşılık, [durum bilgisi olan mikro Hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) olmadığı için etki alanı mantığı ve verileri arasında herhangi bir gecikme Gelişmiş senaryolar excel. Yoğun veri işleme, geri oyun, bir hizmet olarak veritabanı sona erer ve tüm diğer düşük gecikmeli senaryolar daha hızlı erişim için yerel durumunu etkinleştirmek durum bilgisi olan hizmetler yararlanın.

Durum bilgisiz ve durum bilgisi olan hizmetler tamamlayıcıdır. Örneğin, doğru diyagramdaki Şekil 4-31 görebileceğiniz gibi bir durum bilgisi olan hizmet birden çok bölümdeki bölünebilir. Bu bölümler erişmek için bildiği her bölüm bölüm anahtara göre ele almak bir ağ geçidi hizmeti olarak davranan bir durum bilgisi olmayan hizmet gerekebilir.

Durum bilgisi olan hizmetler dezavantajları vardır. Bunlar, ölçeği için bir yüksek karmaşıklık düzeyini büyük oranda yansıtmaktadır. Genellikle dış veritabanı sistemleri tarafından uygulanan işlevleri veri çoğaltma gibi görevler için durum bilgisi olan mikro hizmetler ve bölümleme verilerde ele alınması gerekir. Burada bir orchestrator gibi alanlarından budur ancak [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) ile kendi [durum bilgisi olan reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) en çok yardımcı olabilir; geliştirme ve durum bilgisi olan yaşam döngüsü basitleştirerek mikro hizmetler kullanarak [Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) ve [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Gerçekleştiren deseni destekleyen ve hataya dayanıklılık ve iş mantığı ve verileri arasındaki gecikme süresini artırmak durum bilgisi olan hizmetler sağlayan diğer mikro hizmet çerçeveleri olan Microsoft [Orleans](https://github.com/dotnet/orleans), Microsoft Research ve [ Akka.NET](https://getakka.net/). Her iki çerçeveler kendi Docker desteği şu anda geliştirdiğinizi.

Docker kapsayıcıları durum bilgisiz kendilerini olduğunu unutmayın. Durum bilgisi olan hizmet uygulamak istiyorsanız, daha önce not ettiğiniz ek önerilerde bulunan ve daha üst düzey altyapılarından birini gerekir.

## <a name="using-azure-service-fabric-mesh"></a>Azure Service Fabric kafes kullanma

Azure Service Fabric Mesh, derlemek ve tüm altyapı yönetimine gerek kalmadan, iş açısından kritik uygulamalar dağıtmak geliştiricilerinin sağlayan tam olarak yönetilen bir hizmettir. Service Fabric Mesh oluşturmak ve isteğe bağlı olarak ölçeklendirilebilen güvenli, dağıtılmış mikro hizmet uygulamaları çalıştırmak için kullanın.

4-15, şekilde gösterildiği gibi Service Fabric Mesh üzerinde barındırılan uygulamaları çalıştırıp ölçeklendirmenize gerek kalmadan, destekleyen altyapı konusunda endişelenmenize gerek.

![Docker masaüstünde çalışan bir çoklu kapsayıcı uygulaması Azure Service Fabric Mesh için altyapı hakkında endişelenmeden dağıtılabilir.](media/image39.png)

**Şekil 4-15**. Service Fabric Mesh bir mikro hizmet/kapsayıcı uygulaması dağıtma

Güvenli Service Fabric Mesh makineler binlerce kümelerini oluşur. Tüm küme işlemlerini geliştiriciden gizlidir. Kapsayıcılarınızı karşıya yükleme ve ihtiyacınız olan kaynakları, kullanılabilirlik gereksinimlerini ve kaynak sınırları belirtin yeterlidir. Service Fabric Mesh uygulama dağıtımınız tarafından istenen altyapı otomatik olarak ayırır ve ayrıca uygulamalarınızın yüksek oranda kullanılabilir olduğundan emin olma altyapı hataları işleme. Altyapıya değil, uygulamanızın yanıt hızını ve sistem durumu hakkında önemli yeterlidir.

Daha fazla bilgi için bkz: [Service Fabric Mesh belgeleri](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Azure'da düzenleyicileri seçme

Aşağıdaki tabloda, iş yükleri ve işletim sistemi odak bağlı olarak kullanmak için hangi orchestrator hakkında yönergeler sağlanır.

![Azure Kubernetes hizmeti, Windows, Linux daha olgun ve genellikle kapsayıcılara göre mikro hizmetler dağıtmak için kullanılır. Azure Service Fabric (hem küme hem de kafes) Windows, Linux, kapsayıcılar, mikro hizmetler düz işlemleri ve durum bilgisi olan hizmetler göre temel mikro hizmetlere yönelik yaygın olarak kullanılan daha olgun kullanılıyor.](media/image40.png)

**Şekil 4-16**. Orchestrator seçimde Azure Kılavuzu

>[!div class="step-by-step"]
>[Önceki](soa-applications.md)
>[İleri](deploy-azure-kubernetes-service.md)
