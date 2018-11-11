---
title: Mikro hizmetler ve yüksek ölçeklenebilirlik ve kullanılabilirlik için birden çok kapsayıcılı uygulamaları yönetme
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Mikro hizmetler ve yüksek ölçeklenebilirlik ve kullanılabilirlik için birden çok kapsayıcılı uygulamaları yönetme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 25175e2a4409d53be412ae72be5af1c07c3ec68d
ms.sourcegitcommit: 296183dbe35077b5c5e5e74d5fbe7f399bc507ee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2018
ms.locfileid: "50982782"
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Mikro hizmetler ve yüksek ölçeklenebilirlik ve kullanılabilirlik için birden çok kapsayıcılı uygulamaları yönetme

Uygulamanız üzerinde mikro hizmet tabanlı ya da birden çok kapsayıcıda yalnızca bölme düzenleyicileri kullanarak üretime hazır uygulamalar için gereklidir. Böylece bir geliştirme ve dağıtım açısından otonom mikro hizmet tabanlı bir yaklaşım, daha önce tanıtılan her mikro hizmet kendi modeli ve veri sahibi. Ancak oluşan daha geleneksel bir uygulama (SOA gibi) birden çok Hizmetleri olsa da birden çok kapsayıcı veya hizmet dağıtılmış bir sistemde dağıtılması gereken bir tek iş uygulaması oluşturan gerekir. Ölçeği genişletme ve yönetmek için bu tür sistemler karmaşıktır; Bu nedenle, üretime hazır ve ölçeklenebilir çok kapsayıcılı bir uygulama istiyorsanız kesinlikle bir orchestrator gerekir.

Şekil 4-23 (kapsayıcılar) birden çok mikro hizmetlerden bir uygulama kümesi dağıtmayı gösterir.

![](./media/image23.PNG)

**Şekil 4-23**. Kapsayıcıları kümesi

Mantıksal bir yaklaşım gibi görünüyor. Ancak uygulamaları oluşan işleme Yük Dengeleme, Yönlendirme ve bunlar işlemlerini nasılsın?

Tek bir Docker ana bilgisayarları düz Docker altyapısındaki bir konak üzerinde tek bir görüntü örneklerini yönetme gereksinimlerini karşılayan, ancak daha karmaşık dağıtılmış uygulamaların birden çok konak üzerinde dağıtılan birden çok kapsayıcı yönetmek için söz konusu olduğunda kısa döner. Çoğu durumda, otomatik olarak kapsayıcılar, görüntü başına birden çok örneği ölçeklendirme kapsayıcılarla başlayın, bunları askıya alma veya gerektiğinde Kapat ve ideal olarak ayrıca nasıl veri ve ağ gibi kaynaklara erişim denetimini bir yönetim platformunun gerekir depolama alanı.

Kapsayıcılara veya çok basit oluşturulmuş uygulamalar ve mikro Hizmetleri daha büyük kuruluş uygulamaları doğru taşıma yönetimini ötesine gitmek için düzenleme ve platformları kümeleme için etkinleştirmeniz gerekir.

Mikro hizmet tabanlı uygulamaları, oluşan büyük bir kurumsal oluşturuyorsanız bir mimari ve geliştirme açısından bakıldığında, aşağıdaki platformları ve Gelişmiş senaryolar destekleyen ürünleri anlamak önemlidir:

**Kümeler ve düzenleyicileri**. Büyük bir mikro hizmet tabanlı uygulama, bu konak tarafından temel platform karmaşıklığını özetleyen tek bir küme halinde yönetmek için kritik olduğu gibi birçok Docker konakları arasında uygulamalarının ölçeğini gerektiğinde. Neler kapsayıcı kümeleri ve düzenleyicileri sağlar olmasıdır. Azure Service Fabric, Kubernetes, Docker Swarm ve Mesosphere DC/OS düzenleyicileri örnekleridir. Son üç açık kaynak düzenleyicileri, azure'da Azure Container Service aracılığıyla kullanılabilir.

**Zamanlayıcılar**. *Zamanlama* özelliğine de bir kullanıcı Arabirimi sağlar, böylece bir kümedeki kapsayıcıları başlatmak bir yöneticinin anlamına gelir. Bir küme Zamanlayıcı çeşitli sorumlulukları vardır: küme kaynaklarını verimli bir şekilde kullanmak için verimli bir şekilde düğümleri veya konaklar arasında Yük Dengeleme kapsayıcıları için kullanıcı tarafından sağlanan kısıtlamaları ayarlamak ve yüksek sağlarken hatalarına karşı güçlü Kullanılabilirlik.

Genellikle farklı satıcılar tarafından sağlanan ürün iki yetenekleri sağlamak için bir küme ve bir zamanlayıcı yakından ilişkilidir. Aşağıdaki listede, yazılım seçenek kümeleri ve zamanlayıcılar olması ve en önemli platform gösterir. Bu düzenleyiciler, Azure gibi genel bulutlarda genel kullanıma sunulur.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Yazılım platformlarının kümeleme kapsayıcı, düzenleme ve zamanlama için

Kubernetes

![Kubernetes logosu](./media/image24.png)

> Kubernetes kümesi altyapısı ve zamanlama işlemlerini özellikleri için kapsayıcı aralıkları işlevselliği sağlayan açık kaynaklı üründür. Bu ana bilgisayar kümeleri arasında dağıtım, ölçeklendirme ve uygulama kapsayıcıların işlemlerini otomatikleştirmenizi sağlar.
>
> Kubernetes uygulama kapsayıcıları kolay yönetim ve bulma için mantıksal birimler halinde gruplandırır kapsayıcı merkezli bir altyapı sağlar.
>
> Kubernetes, Linux, Windows daha az olgun olgun.

Docker Swarm

![Docker Swarm logosu](./media/image25.png)

> Docker Swarm, Docker kapsayıcıları zamanlayabilir ve küme olanak tanır. Swarm kullanarak Docker ana bilgisayarları havuzu tek, sanal bir Docker konağı kapatabilirsiniz. İstemciler, Swarm için birden çok konak ölçeklendirmek için uygulamaları kolaylaştırır anlamı Konaklara yaptıkları aynı şekilde Swarm için API isteklerinin yapabilirsiniz.
>
> Docker Swarm, docker, şirket için kullanılan bir üründür.
>
> Docker v1.12 veya yerel ve yerleşik Swarm modu daha sonra çalıştırabilir.

Mesosphere DC/OS

![Mesosphere DC/OS logosu](./media/image26.png)

> Mesosphere Kurumsal DC/OS (üzerinde Apache Mesos tabanlı), kapsayıcılar ve dağıtılan uygulamaları çalıştırmak bir üretime hazır platformudur.
>
> DC/OS kümesinde kullanılabilir kaynakları koleksiyonu özetleyen ve bu kaynaklar üzerinde oluşturulan bileşenler için kullanılabilir hale getirme çalışır. Marathon, genellikle DC/OS ile tümleşik bir zamanlayıcı olarak kullanılır.
>
> DC/OS, Linux, Windows daha az olgun olgun.

Azure Service Fabric

![Azure Service Fabric logosu](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) uygulamaları oluşturmaya yönelik bir Microsoft mikro hizmet platformudur. Bu bir [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) , hizmetleri ve makine kümeleri oluşturur. Service Fabric Hizmetleri düz işlemleri veya kapsayıcıları olarak dağıtabilirsiniz. Hatta işlemlerde karışımı Hizmetleri aynı uygulama ve küme kapsayıcılara hizmetleriyle alabilir.
>
> Service Fabric, ek ve isteğe bağlı sağlar öngörücü [Service Fabric programlama modellerini ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) gibi [durum bilgisi olan hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) ve [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).
>
> Service Fabric (yıl içinde Windows gelişen) Windows, daha az olgun Linux'ta olgun kullanılıyor. 
> Hem Linux hem de Windows kapsayıcıları Service Fabric'te 2017 itibarıyla desteklenir.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Microsoft Azure'daki kapsayıcı tabanlı düzenleyicileri kullanarak

Docker kapsayıcıları desteği yanı sıra Docker kümeler ve düzenleme desteği, Microsoft Azure, Amazon EC2 Container Service ve Google Container altyapısı dahil olmak üzere birden fazla bulut satıcılarına sunar. Microsoft Azure Docker sonraki bölümde açıklandığı gibi küme ve orchestrator desteği Azure Container Service (ACS) aracılığıyla sağlar.

Başka bir seçenek ise Microsoft Azure Service ayrıca Linux ve Windows kapsayıcıları göre Docker'ı destekleyen Fabric (bir mikro hizmet platformu) kullanmaktır. Service Fabric, Azure veya başka bir bulut üzerinde çalışır ve de çalışır [şirket içi](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Azure Container Service'i kullanma

Bir Docker kümesi birden fazla Docker ana bilgisayarları havuzları ve birden çok kapsayıcı kümesine dağıtmak için bunları bir tek sanal Docker konağı olarak kullanıma sunar. Küme ölçeklenebilirliği, sistem durumu ve benzeri gibi tüm karmaşık yönetim ayarlamaları, işler. Şekil 4-24 bir Docker kümesi oluşturulan uygulamalar için Azure Container Service (ACS) nasıl eşlendiğini temsil eder.

ACS oluşturma, yapılandırma ve kapsayıcılı uygulamaları çalıştırmak için önceden yapılandırılmış sanal makine kümesi yönetimini basitleştirmek için bir yol sağlar. Popüler açık kaynak planlama ve düzenleme araçlarının iyileştirilmiş yapılandırmalarını kullanarak ACS mevcut becerilerinizi kullanabilir veya Microsoft azure'daki kapsayıcı tabanlı uygulamaları dağıtmak ve yönetmek için topluluk uzmanlığından geniş ve büyüyen bir gövdesi üzerinde çizim yapmanızı sağlar .

Azure kapsayıcı hizmeti popüler Docker kümeleme açık kaynaklı araçların ve teknolojilerin yapılandırmasını özellikle Azure'a yönelik en iyi duruma getirir. Hem kapsayıcılarınız hem de uygulama yapılandırmanız için taşınabilirlik sunan bir açık çözümü sahip olursunuz. Boyutu, konak sayısını ve düzenleyici araçlarını seçin ve kapsayıcı hizmeti, diğer her şey yapar.

![](./media/image28.png)

**Şekil 4-24**. Azure Container Service'te küme seçenekleri

ACS, uygulama kapsayıcılarınızın tamamen taşınabilir olmasını sağlamak için Docker görüntülerini yararlanır. Bu, bu uygulamaları binlerce veya on binlerce kapsayıcının ölçeklendirilebilir emin olmak için tercih ettiğiniz gibi DC/OS (Apache Mesos tarafından desteklenen), (ilk olarak Google tarafından oluşturulan) Kubernetes ve Docker Swarm, açık kaynaklı düzenleme platformları destekler.

Azure kapsayıcı hizmeti, Azure'un kuruluş düzeyindeki özelliklerinden faydalanırken düzenleme katmanına dahil olmak üzere uygulama taşınabilirliğini, yararlanmak sağlar.

![](./media/image29.png)

**Şekil 4-25**. Acs'de düzenleyicileri

Şekil 4-25 gösterildiği gibi Azure Container Service DC/OS, Kubernetes veya Docker Swarm dağıtmak için Azure tarafından sağlanan yalnızca altyapısıdır ancak ACS herhangi bir ek orchestrator uygulamaz. Bu nedenle, ACS bir orchestrator bu nedenle, kapsayıcılar için mevcut açık kaynak düzenleyicileri yararlanan bir altyapı yoktur.

Kullanım açısından bakıldığında, Azure Container Service, popüler açık kaynak araçları ve teknolojileri kullanan bir kapsayıcı barındırma ortamı sağlamak için hedeftir. Şu an için kullandığınız düzenleyici için standart API uç noktalarını gösterir. Bu uç noktaları kullanarak, bu Uç noktalara konuşabilirsiniz tüm yazılımlardan faydalanabilirsiniz. Örneğin, Docker Swarm uç noktasıyla Docker komut satırı arabirimi (CLI) kullanmayı seçebilirsiniz. DC/OS için DC/OS CLI'yı kullanmayı seçebilirsiniz.

### <a name="getting-started-with-azure-container-service"></a>Azure Container Service ile çalışmaya başlama 

Azure Container Service'i kullanmaya başlamak için bir Azure Container Service kümesi Azure portalında bir Azure Resource Manager şablonu kullanarak dağıtmanız veya [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Kullanılabilir şablonlar [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), ve [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Hızlı Başlangıç şablonları, ek veya Gelişmiş Azure yapılandırmalarını dahil edecek şekilde değiştirilebilir. Bir Azure Container Service kümesi dağıtma hakkında daha fazla bilgi için bkz. [bir Azure Container Service kümesi dağıtma](https://docs.microsoft.com/azure/container-service/container-service-deployment) Azure Web sitesinde.

Herhangi bir ACS bir parçası olarak varsayılan olarak yüklü olan yazılım için herhangi bir ücret yoktur. Tüm varsayılan seçenekleri ile açık kaynaklı yazılım uygulanır.

ACS şu anda standart A, D, DS, G ve GS serisi azure'da Linux sanal makineleri için kullanılabilir. Yalnızca seçtiğiniz işlem örnekleri yanı sıra, depolama ve ağ gibi kullanılan temel altyapı kaynakları için ücretlendirilirsiniz. ACS hizmetinin kendisi için artımlı ücretlendirme yoktur.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Docker kapsayıcı barındırma çözümlerine Azure Container Service ile giriş**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Docker Swarm'a genel bakış**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **Swarm modu genel bakış**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **Mesosphere DC/OS genel bakış**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes.** Resmi sitesi. \
    [*https://kubernetes.io/*](https://kubernetes.io/)


>[!div class="step-by-step"]
[Önceki](resilient-high-availability-microservices.md)
[İleri](using-azure-service-fabric.md)
