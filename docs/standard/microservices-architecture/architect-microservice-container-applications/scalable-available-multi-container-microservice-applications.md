---
title: Mikro ve yüksek ölçeklenebilirlik ve kullanılabilirlik için birden çok kapsayıcı uygulamaları yönetme
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Mikro ve yüksek ölçeklenebilirlik ve kullanılabilirlik için birden çok kapsayıcı uygulamaları yönetme
keywords: Docker, mikro, ASP.NET, kapsayıcı
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c484372c0b5626fc20c8991a432e62353baa7a4c
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="orchestrating-microservices-and-multi-container-applications-for-high-scalability-and-availability"></a>Mikro ve yüksek ölçeklenebilirlik ve kullanılabilirlik için birden çok kapsayıcı uygulamaları yönetme

Uygulamanızın üzerinde mikro tabanlı veya yalnızca arasında birden çok kapsayıcı bölünmüş durumunda orchestrators kullanarak üretime hazır uygulamalar için gereklidir. Böylece bir geliştirme ve dağıtım noktası görünüm otonom mikro hizmet tabanlı bir yaklaşım, daha önce sunulduğu şekilde her mikro hizmet modeli ve veri sahip olur. Ancak oluşur daha geleneksel (SOA gibi) birden çok hizmet uygulamasının olsa da birden çok kapsayıcı veya dağıtılmış bir sistem olarak dağıtılması için gereken bir tek iş uygulaması oluşturan Hizmetleri sahip olursunuz. Bu tür sistemlere genişletme ve yönetmek için karmaşık; Bu nedenle üretime hazır ve ölçeklenebilir çok kapsayıcısı uygulamasına sahip olmak istiyorsanız kesinlikle bir orchestrator gerekir.

Şekil 4-23 kümesinde birden çok mikro (kapsayıcı) oluşan bir uygulamanın dağıtım gösterilmektedir.

![](./media/image23.PNG)

**Şekil 4-23**. Kapsayıcıların bir küme

Mantıksal bir yaklaşım gibi görünüyor. Ancak nasıl, işleme Yük Dengeleme, Yönlendirme ve bunları yönetme uygulamaları oluşur?

Tek Docker ana bilgisayarları düz Docker Makinesi'nde tek bir görüntü örnekleri bir konak üzerinde yönetme gereksinimlerini karşılayan, ancak daha karmaşık dağıtılmış uygulamalar için birden çok ana bilgisayara dağıtılan birden çok kapsayıcı Yönetimi söz konusu olduğunda kısa döner. Çoğu durumda, otomatik olarak kapsayıcıları, görüntü başına birden çok örneği ile genişleme kapsayıcıları başlatmak, bunları askıya alma veya gerektiğinde kapatmak ve ideal ayrıca nasıl veri ve ağ gibi kaynaklara erişim denetimini bir yönetim platformunun gerekir depolama alanı.

Tek tek kapsayıcıları veya çok basit oluşan uygulamaları ve mikro büyük kuruluş uygulamalarıyla doğru taşıma yönetimini ötesine gitmek için düzenleme ve platformlar kümeleme için etkinleştirmeniz gerekir.

Mikro tabanlı uygulamaların oluşan büyük kuruluş oluşturuluyorsa bir mimari ve geliştirme açısından bakıldığında, aşağıdaki platformları ve Gelişmiş senaryoları desteklemek ürünleri anlamak önemlidir:

**Kümeleri ve orchestrators**. Mikro hizmet tabanlı büyük bir uygulama, tüm ana bilgisayarlar tek bir küme temel platform karmaşıklığını özetleyen tarafından yönetebilmek için çok önemli olduğu gibi birçok Docker ana bilgisayarlar arasında uygulamalarının ölçeklendirmek gerektiğinde. Neler kapsayıcı kümeleri ve orchestrators sağlar olmasıdır. Azure Service Fabric, Kubernetes, Docker Swarm ve Mesosphere DC/OS orchestrators örnektir. Son üç açık kaynak orchestrators Azure Azure kapsayıcı hizmeti üzerinden kullanılabilir.

**Zamanlayıcılar**. *Zamanlama* özelliğine de bir kullanıcı Arabirimi sağladıkları için bir küme kapsayıcılarında başlatmak bir yöneticinin anlamına gelir. Bir küme Zamanlayıcı birkaç sorumlulukları vardır: küme kaynaklarını verimli bir şekilde kullanmak için verimli bir şekilde düğümleri veya konaklar arasında Yük Dengeleme kapsayıcıları için kullanıcı tarafından sağlanan kısıtlamaları ayarlamak ve yüksek sağlarken karşı hataları sağlam için Kullanılabilirlik.

Genellikle farklı satıcıları tarafından sağlanan ürünleri hem yetenekleri sağlamak için bir küme ve bir zamanlayıcı kavramlarını yakından ilişkilidir. Aşağıdaki liste, yazılım seçimler kümeleri ve zamanlayıcılar için sahip ve en önemli platform gösterir. Bu orchestrators, genellikle Azure gibi genel bulut olarak sunulur.

## <a name="software-platforms-for-container-clustering-orchestration-and-scheduling"></a>Kapsayıcı kümeleme, düzenleme ve zamanlama için yazılım platformları

Kubernetes

![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image24.png)

> Kubernetes küme altyapısı ve yönetme olanağı zamanlama kapsayıcı aralıkları işlevselliği sağlayan bir açık kaynaklı üründür. Ana bilgisayar kümelerinde dağıtım, ölçeklendirme ve uygulama kapsayıcıları işlemlerini otomatikleştirmenizi sağlar.
>
> Kubernetes kolay yönetim ve bulma için mantıksal birimler halinde uygulama kapsayıcıları grupları kapsayıcı merkezli bir altyapı sağlar.
>
> Kubernetes Linux, Windows daha az olgun olgun ' dir.

Docker Swarm

![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image25.png)

> Docker Swarm, küme ve Docker kapsayıcıları zamanlama sağlar. Swarm kullanarak, bir tek, sanal Docker ana bilgisayara bir havuzu Docker ana bilgisayarları kapatabilirsiniz. İstemcileri Swarm için birden çok ana ölçeklendirme uygulamaları kolaylaştırır anlamı konaklarına yaparlar aynı şekilde Swarm API isteğinde bulunabilir.
>
> Docker Swarm, Docker, şirket gelen bir üründür.
>
> Docker v1.12 veya daha sonra yerel ve yerleşik Swarm modu çalıştırabilirsiniz.

Mesosphere DC/OS

![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image26.png)

> Kurumsal DC/OS mesosphere (üzerinde Apache Mesos bağlı olarak) kapsayıcıları ve dağıtılmış uygulamaları çalıştırmak için bir üretime hazır platformudur.
>
> DC/OS kümesinde kullanılabilir kaynaklar koleksiyonu özetleyen ve bu kaynakları üstünde derlendikten bileşenleri için kullanılabilir hale getirme çalışır. Marathon genellikle DC/OS ile tümleşik bir zamanlayıcı olarak kullanılır.
>
> DC/OS Linux, Windows daha az olgun olgun ' dir.

Azure Service Fabric

![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image27.png)

> [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) uygulamaları oluşturmak için bir Microsoft mikro platformudur. Bu bir [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) , hizmetleri ve makine kümeleri oluşturur. Service Fabric Hizmetleri kapsayıcıları veya düz işlemler olarak dağıtabilirsiniz. Hatta işlemlerde karışımı Hizmetleri aynı uygulama ve küme kapsayıcılara Hizmetleri ile dağıtabilirsiniz.
>
> Service Fabric sağlar Ek ve isteğe bağlı düzenleyici [Service Fabric modellerini programlama ](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) gibi [durum bilgisi olan hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) ve [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).
>
> Service Fabric Windows'taki (Windows'ta yıl gelişen), daha az olgun Linux olgun. 
> Linux ve Windows kapsayıcıları Service Fabric 2017 itibaren desteklenir.

## <a name="using-container-based-orchestrators-in-microsoft-azure"></a>Microsoft Azure'da kapsayıcı tabanlı orchestrators kullanma

Birden fazla bulut satıcı Docker kapsayıcıları artı Docker kümeleri ve Microsoft Azure, Amazon EC2 kapsayıcı hizmeti ve Google kapsayıcı altyapısı dahil düzenleme desteği, sunar. Microsoft Azure bir sonraki bölümde açıklandığı gibi küme ve orchestrator Destek aracılığıyla Azure kapsayıcı Hizmeti'ni (ACS), Docker sağlar.

Microsoft Azure hizmet de Linux ve Windows kapsayıcıları göre Docker desteklediği Fabric (bir mikro platformu) kullanan başka bir seçenektir. Service Fabric Azure veya başka bir bulut üzerinde çalışır ve aynı zamanda çalıştırır [şirket içi](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Azure kapsayıcı hizmeti kullanma

Docker küme birden çok Docker ana havuzları ve kümeye birden çok kapsayıcı dağıtabilmek için bunları tek bir sanal Docker ana bilgisayar, kullanıma sunar. Kümenin tüm karmaşık yönetim tesisat, ölçeklenebilirlik, sistem durumu ve diğerleri gibi işler. Şekil 4-24 Docker küme oluşan uygulamaları için Azure kapsayıcı Hizmeti'ni (ACS) nasıl eşlendiğini temsil eder.

ACS oluşturma, yapılandırma ve bir küme kapsayıcılı uygulamaları çalıştırmak için önceden yapılandırılmış sanal makinelerin yönetimini basitleştirmek için bir yol sağlar. Popüler açık kaynak planlama ve düzenleme Araçları'nın en iyi duruma getirilmiş bir Yapılandırması'nı kullanarak ACS varolan yeteneklerinizi kullanın veya Microsoft Azure üzerinde kapsayıcı tabanlı uygulamaları dağıtmak ve yönetmek için topluluk uzmanlık büyük ve artan bir gövde üzerinde çizmek sağlar .

Azure kapsayıcı hizmeti popüler Docker kümeleme açık kaynak Araçlar ve teknolojiler yapılandırmasını özellikle Azure için en iyi duruma getirir. Taşınabilirlik kapsayıcılarınızı ve uygulama yapılandırmanızı sağlayan açık olan çözüm alın. Boyut, ana bilgisayar sayısı ve orchestrator araçları seçin ve kapsayıcı hizmeti şey işler.

![](./media/image28.png)

**Şekil 4-24**. Azure kapsayıcı hizmeti küme seçenekleri

ACS, uygulama kapsayıcıları tümüyle taşınabilir olduğundan emin olmak için Docker görüntüleri yararlanır. Bu uygulamalar binlerce veya hatta binlerce kapsayıcıları için Genişletilebilir emin olmak için tercih ettiğiniz DC/OS (Apache Mesos tarafından desteklenen), (ilk olarak Google tarafından oluşturulan) Kubernetes ve Docker Swarm, gibi açık kaynaklı orchestration platformlarda destekler.

Azure kapsayıcı hizmeti hala düzenleme katmanları dahil olmak üzere uygulama taşınabilirliği korurken Azure Kurumsal düzeyde özelliklerden yararlanmak sağlar.

![](./media/image29.png)

**Şekil 4-25**. ACS orchestrators

Şekil 4-25 gösterildiği gibi Azure kapsayıcı hizmeti DC/OS, Kubernetes veya Docker Swarm dağıtmak için Azure tarafından sağlanan yalnızca altyapısıdır ancak ACS herhangi bir ek orchestrator uygulamıyor. Bu nedenle, ACS bir orchestrator, bu nedenle kapsayıcıları için mevcut açık kaynak orchestrators yararlanan bir altyapı değil.

Kullanım açısından bakıldığında, Azure kapsayıcı hizmeti popüler açık kaynak Araçlar ve teknolojiler kullanarak bir kapsayıcı barındırma ortamı sağlamak için hedefidir. Bu amaçla, standart API uç noktaları için seçilen orchestrator gösterir. Bu uç noktalar kullanarak, bu uç noktalar ile iletişim kurabilirsiniz herhangi bir yazılım yararlanabilirsiniz. Örneğin, Docker Swarm uç nokta söz konusu olduğunda, Docker komut satırı arabirimi (CLI) kullanmayı seçebilirsiniz. DC/OS için DC/OS CLI kullanmayı seçebilirsiniz.

### <a name="getting-started-with-azure-container-service"></a>Azure kapsayıcı hizmeti ile çalışmaya başlama 

Azure kapsayıcı hizmeti kullanmaya başlamak için bir Azure kapsayıcı hizmeti kümesi Azure portalından bir Azure Resource Manager şablonu kullanarak dağıttığınız veya [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Kullanılabilir şablonların dahil [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), ve [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Hızlı Başlangıç şablonlarını ek veya Gelişmiş Azure yapılandırması eklemek için değiştirilebilir. Azure kapsayıcı hizmeti kümesini dağıtma hakkında daha fazla bilgi için bkz: [Azure kapsayıcı hizmeti kümesini dağıtma](https://docs.microsoft.com/azure/container-service/container-service-deployment) Azure Web sitesinde.

Varsayılan olarak ACS bir parçası olarak yüklenen yazılım hiçbirini hiçbir ücretlerinin vardır. Tüm varsayılan seçenekleri açık kaynaklı yazılım ile uygulanır.

ACS standart A, D, DS, G ve GS serisi Linux sanal makineleri azure'da şu anda kullanılabilir. Yalnızca seçtiğiniz işlem örnek olarak, depolama ve ağ gibi kullanılan diğer temel altyapı kaynaklar için ücretlendirilirsiniz. ACS kendisi için artımlı harcamanız yok.

## <a name="additional-resources"></a>Ek kaynaklar

-   **Azure kapsayıcı hizmeti çözümleriyle barındırma Docker kapsayıcısı giriş**
    [*https://docs.microsoft.com/azure/container-service/container-service-intro*](https://docs.microsoft.com/azure/container-service/container-service-intro)

-   **Docker Swarm genel bakış**
    [*https://docs.docker.com/swarm/overview/*](https://docs.docker.com/swarm/overview/)

-   **Swarm moduna genel bakış**
    [*https://docs.docker.com/engine/swarm/*](https://docs.docker.com/engine/swarm/)

-   **Mesosphere DC/OS genel bakış**
    [*https://docs.mesosphere.com/1.7/overview/*](https://docs.mesosphere.com/1.7/overview/)

-   **Kubernetes.** Resmi site. \
    [*https://kubernetes.io/*](https://kubernetes.io/)


>[!div class="step-by-step"]
[Önceki] (esnek-yüksek-kullanılabilirlik-microservices.md) [sonraki] (kullanarak-azure-service-fabric.md)
