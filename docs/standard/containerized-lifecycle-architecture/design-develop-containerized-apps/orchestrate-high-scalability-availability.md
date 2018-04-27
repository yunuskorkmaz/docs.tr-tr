---
title: Mikro ve yüksek ölçeklenebilirlik ve kullanılabilirlik multicontainer uygulamaları yönetme
description: Microsoft Platformu ve araçları ile kapsayıcılı Docker uygulama yaşam döngüsü
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 59c03755bebce98e018f56fc7213b00a0d3eae38
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2018
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>Mikro ve yüksek ölçeklenebilirlik ve kullanılabilirlik multicontainer uygulamaları yönetme

Uygulamanızın üzerinde mikro tabanlı veya yalnızca arasında birden çok kapsayıcı bölünmüş durumunda orchestrators kullanarak üretime hazır uygulamalar için gereklidir. Böylece bir geliştirme ve dağıtım noktası görünüm otonom mikro hizmet tabanlı bir yaklaşım, daha önce sunulduğu şekilde her mikro hizmet modeli ve veri sahip olur. Ancak oluşur daha geleneksel (SOA gibi) birden çok hizmet uygulamasının olsa da birden çok kapsayıcı veya dağıtılmış bir sistem olarak dağıtılması için gereken bir tek iş uygulaması oluşturan Hizmetleri sahip olursunuz. Bu tür sistemlere genişletme ve yönetmek için karmaşık; Bu nedenle üretime hazır ve ölçeklenebilir bir multicontainer uygulama sahip olmak istiyorsanız kesinlikle bir orchestrator gerekir.

Şekil 4-6 kümesinde birden çok mikro (kapsayıcı) oluşan bir uygulamanın dağıtım gösterilmektedir.

![](./media/image6.png)

Şekil 4-6: bir kümenin kapsayıcıları

Mantıksal bir yaklaşım gibi görünüyor. Ancak, Yük Dengeleme, Yönlendirme ve oluşan bu uygulamaları yönetme nasıl işleme?

Docker komut satırı arabirimi (CLI) bir ana bilgisayardaki bir kapsayıcı yönetme gereksinimleri karşılayan, ancak daha karmaşık dağıtılmış uygulamalar için birden çok ana bilgisayara dağıtılan birden çok kapsayıcı Yönetimi söz konusu olduğunda kısa döner. Çoğu durumda, otomatik olarak kapsayıcıları başlatmak, bunları, askıya almak veya gerektiğinde kapatmak ve ideal Ayrıca ağ ve veri depolama alanı gibi kaynaklar nasıl erişim denetimini bir yönetim platformunun gerekir.

Tek tek kapsayıcıları veya çok basit oluşan uygulamaları ve mikro büyük kuruluş uygulamalarıyla doğru taşıma yönetimini ötesine gitmek için düzenleme ve platformlar kümeleme için etkinleştirmeniz gerekir.

Yapı büyük, Kurumsal, mikro tabanlı olması durumunda bir mimari ve geliştirme açısından bakıldığında, uygulamalar, aşağıdaki platformları ve Gelişmiş senaryoları desteklemek ürünleri anlamak önemlidir:

-   **Kümeleri ve orchestrators** ölçeklendirmek gerektiğinde-uygulamaları birçok Docker ana bilgisayarları arasında gibi büyük mikro tabanlı bir uygulama ile tüm ana bilgisayarlar tarafından tek bir küme olarak yönetmek için önemlidir temel alınan platform karmaşıklığını özetleyen. Neler kapsayıcı kümeleri ve orchestrators sağlar olmasıdır. Docker Swarm, Mesosphere DC/OS, Kubernetes (ilk üç Azure kapsayıcı hizmeti kullanılabilir) ve Azure Service Fabric orchestrators örnekleridir.

-   **Zamanlayıcılar** *zamanlama* özelliğine de bir kullanıcı arabirimi sağlar, böylece bir küme kapsayıcılarında başlatmak bir yöneticinin anlamına gelir. Bir küme Zamanlayıcı birkaç sorumlulukları vardır: küme kaynaklarını verimli bir şekilde kullanmak için verimli bir şekilde düğümleri veya konaklar arasında Yük Dengeleme kapsayıcıları için kullanıcı tarafından sağlanan kısıtlamaları ayarlamak ve yüksek sağlarken karşı hataları sağlam için Kullanılabilirlik.

Genellikle farklı satıcıları tarafından sağlanan ürünleri hem yetenekleri sağlamak için bir küme ve bir zamanlayıcı kavramlarını yakından ilişkilidir. Tablo 4-1, en önemli platform ve kümeler ve zamanlayıcılar sahip yazılım seçimi listeler. Bu kümeleri, genellikle Azure gibi genel bulut olarak sunulur.

Tablo 4-1: yazılım platformlarının kapsayıcı kümeleme, düzenleme ve zamanlama

| Platform | Açıklama |
|---|---|
| Docker Swarm<br/> ![http://rancher.com/wp-content/themes/rancher-2016/assets/images/swarm.png?v=2016-07-10-am](./media/image7.png) | Docker Swarm kümesi ve Docker kapsayıcıları zamanlama olanağı sağlar. Swarm kullanarak, bir tek, sanal Docker ana bilgisayara bir havuzu Docker ana bilgisayarları kapatabilirsiniz. İstemcileri API istekleri Swarm için Swarm ölçeklendirmek üzere uygulamalar için birden çok ana bilgisayar için kolaylaştırır, anlamı konaklarına aynı şekilde yapabilirsiniz. <br /><br /> Docker Swarm, Docker, şirket gelen bir üründür. <br /><br /> Docker v1.12 veya daha sonra yerel ve yerleşik Swarm modu çalıştırabilirsiniz. |
| Mesosphere DC/OS<br/>![https://mesosphere.com/wp-content/uploads/2016/04/logo-horizontal-styled.png](./media/image8.png) |  Kurumsal DC/OS mesosphere (üzerinde Apache Mesos bağlı olarak) kapsayıcıları ve dağıtılmış uygulamaları çalıştırmak için bir üretime hazır platformudur. <br /><br /> DC/OS kümesinde kullanılabilir kaynaklar koleksiyonu özetleyen ve bu kaynakları üstünde derlendikten bileşenleri için kullanılabilir hale getirme çalışır. Marathon genellikle DC/OS ile tümleşik bir zamanlayıcı olarak kullanılır. |
| Google Kubernetes<br />![https://pbs.twimg.com/media/Bt\_pEfqCAAAiVyz.png](./media/image9.png) | Kubernetes küme altyapısı ve yönetme olanağı zamanlama kapsayıcı aralıkları işlevselliği sağlayan bir açık kaynaklı üründür. Bununla, ana bilgisayar kümelerinde dağıtım, ölçeklendirme ve uygulama kapsayıcıları işlemlerini otomatikleştirebilirsiniz. <br /><br /> Kubernetes kolay yönetim ve bulma için mantıksal birimler halinde uygulama kapsayıcıları grupları kapsayıcı merkezli bir altyapı sağlar. |
| Azure Service Fabric<br />![https://azure.microsoft.com/svghandler/service-fabric?width=600&height=315](./media/image10.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) uygulamaları oluşturmak için bir Microsoft mikro platformudur. Bu bir [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) , hizmetleri ve makine kümeleri oluşturur. Varsayılan olarak, Service Fabric dağıtır ve Hizmetleri işlemler olarak etkinleştirir, ancak Service Fabric Hizmetleri Docker kapsayıcısı görüntülerinde dağıtabilirsiniz. Daha da önemlisi, aynı uygulama kapsayıcılardaki hizmetleriyle işlemleri Hizmetleri'nde karıştırabilirsiniz. <br /><br /> Mayıs 2017 itibariyle Önizleme durumda Docker kapsayıcı olarak dağıtma hizmetlerini destekleyen bir Service Fabric özelliğidir. <br /><br /> Service Fabric Hizmetleri kullanarak birçok yolla geliştirebilirsiniz [Service Fabric modellerini programlama](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) dağıtma [Konuk yürütülebilir dosyalar](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app) kapsayıcıları yanı sıra. Service Fabric destekleyen Düzenleyici uygulama modelleri gibi [durum bilgisi olan hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) ve [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

## <a name="using-container-based-orchestrators-in-azure"></a>Azure kapsayıcı tabanlı orchestrators kullanma

Docker kapsayıcıları destek artı Docker kümeleri ve düzenleme desteği, Azure, Amazon EC2 kapsayıcı hizmeti ve Google kapsayıcı altyapısı dahil olmak üzere çeşitli bulut satıcılar sunar. Azure Docker sonraki bölümde açıklandığı gibi Azure kapsayıcı hizmeti kümesi ve orchestrator desteğini sağlar.

Ayrıca Linux ve Windows kapsayıcıları göre Docker destekleyen Azure Service Fabric kullanan başka bir seçenektir. Service Fabric çalıştıran Azure veya başka bir buluta yanı [şirket içi](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Azure kapsayıcı hizmeti kullanma

Docker küme birden çok Docker ana havuzları ve kümeye birden çok kapsayıcı dağıtabilmek için bunları tek bir sanal Docker ana bilgisayar, kullanıma sunar. Küme, ölçeklenebilirlik ve sistem durumu gibi tüm karmaşık yönetim tesisat işleyecek. Şekil 4-7 Docker küme oluşan uygulamalar için kapsayıcı hizmeti nasıl eşlendiğini temsil eder.

Kapsayıcı hizmeti oluşturma, yapılandırma ve kapsayıcılı uygulamaları çalıştırmak için önceden yapılandırılmış sanal makineleri bir küme yönetimi basitleştirmek için bir yol sağlar. Popüler açık kaynak planlama ve düzenleme Araçları'nın en iyi duruma getirilmiş bir Yapılandırması'nı kullanarak kapsayıcı hizmeti, varolan yeteneklerinizi kullanın veya topluluk uzmanlık dağıtmak ve kapsayıcı tabanlı yönetmek için büyük ve artan gövde üzerinde çizmek için olanak sağlar Azure uygulamalarında.

Kapsayıcı hizmeti popüler Docker kümeleme açık kaynak Araçlar ve teknolojiler yapılandırmasını özellikle Azure için en iyi duruma getirir. Taşınabilirlik kapsayıcılarınızı ve uygulama yapılandırmanızı sağlayan açık olan çözüm alın. Boyut, ana bilgisayar sayısı ve orchestrator araçları seçin ve kapsayıcı hizmeti şey işler.

Kapsayıcı hizmeti Docker görüntüleri uygulama kapsayıcıları tümüyle taşınabilir olduğundan emin olmak için kullanır. Bu uygulamalar binlerce veya hatta binlerce kapsayıcıları ölçeklendirebilirsiniz emin olmak için tercih ettiğiniz DC/OS, Kubernetes ve Docker Swarm gibi açık kaynaklı orchestration platformlarda destekler.

Azure kapsayıcı hizmeti ile Azure Kurumsal düzeyde özelliklerini hala düzenleme katmanları dahil olmak üzere uygulama taşınabilirliği korurken yararlanabilirsiniz.

![](./media/image11.png)

Şekil 4-7: Azure kapsayıcı hizmeti seçenek kümeleme

Şekil 4-8'de gösterildiği gibi kapsayıcı hizmeti DC/OS, Kubernetes veya Docker Swarm dağıtmak için Azure tarafından sağlanan yalnızca altyapısıdır, ancak herhangi bir ek orchestrator uygulamıyor. Bu nedenle, olmayan bir orchestrator, bu nedenle kapsayıcı hizmetidir; Yalnızca mevcut açık kaynak orchestrators kapsayıcıları için yararlanan bir alt yapısıdır.

![](./media/image12.png)

Şekil 4-8: Orchestrators kapsayıcı hizmetinde

Kullanım açısından bakıldığında, kapsayıcı hizmeti popüler açık kaynak Araçlar ve teknolojiler kullanarak bir kapsayıcı barındırma ortamı sağlamak için hedefidir. Bu amaçla, standart API uç noktaları için seçilen orchestrator gösterir. Bu uç noktalar kullanarak, bu uç noktalar ile iletişim kurabilen herhangi bir yazılım kullanabilirsiniz. Örneğin, Docker Swarm uç nokta söz konusu olduğunda, Docker CLI kullanmayı seçebilirsiniz. DC/OS için DC/OS CLI kullanmayı seçebilirsiniz.

### <a name="getting-started-with-container-service"></a>Kapsayıcı hizmetini kullanmaya başlama

Kapsayıcı hizmeti kullanmaya başlamak için bir kapsayıcı hizmeti kümesi Azure portalından bir Azure Resource Manager şablonu kullanarak dağıttığınız veya [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Kullanılabilir şablonların dahil [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), ve [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Ek veya Gelişmiş Azure yapılandırması eklemek için hızlı başlangıç şablonlarını değiştirebilirsiniz.

**Daha fazla bilgi** Azure Web sitesinde bir kapsayıcı hizmeti kümesini dağıtma hakkında daha fazla bilgi için okuma [Azure kapsayıcı hizmeti kümesini dağıtma](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment).

Varsayılan olarak ACS bir parçası olarak yüklenen yazılım hiçbirini hiçbir ücretlerinin vardır. Tüm varsayılan seçenekleri açık kaynaklı yazılım ile uygulanır.

Kapsayıcı hizmeti şu anda standart A, D, DS, G ve GS serisi Linux VM'ler için Azure'da için kullanılabilir. Yalnızca, depolama ve ağ gibi diğer temel altyapı kaynakları kısıtlanarak yanı sıra seçtiğiniz işlem örnekleri için sizden ücret kesilir. Vardır kapsayıcı hizmeti için artımlı harcamanız kendisi.

### <a name="additional-resources"></a>Ek kaynaklar

Burada bulabilirsiniz ek bilgi konumları şunlardır:

-   Kapsayıcı hizmeti çözümleriyle barındırma Docker kapsayıcısı giriş:  
    https://docs.microsoft.com/azure/container-service/kubernetes/container-service-intro-kubernetes>

-   Docker Swarm genel bakış:  
    <https://docs.docker.com/swarm/overview/>

-   Swarm moduna genel bakış:  
    <https://docs.docker.com/engine/swarm/>

-   Mesosphere DC/OS genel bakış:    
    <https://docs.mesosphere.com/1.7/overview/>

-   Kubernetes (resmi site):  
    <https://kubernetes.io/>

## <a name="using-service-fabric"></a>Service Fabric kullanma

Microsoft'un geçiş stilde genellikle tek yapılı, "kutu" ürünler, hizmetler teslim etmek için teslim öğesinden gelen Service Fabric çıkan. Derleme ve Azure SQL Database, Azure belge DB, Azure Service Bus veya Cortana'nın arka uç gibi ölçekte büyük Hizmetleri işletim deneyimi Service Fabric şeklinde. Bu daha da fazla Hizmetleri benimsenen gibi platform zamanla gelişen. Önemlisi, Service Fabric yalnızca azure'da aynı zamanda tek başına Windows Server dağıtımlarında çalıştırmak gerekiyordu.

Service Fabric amacı oluşturma ve bir hizmeti çalıştıran ve böylece takımlar mikro yaklaşımı kullanarak iş sorunlarını çözebilir altyapı kaynaklarını verimli bir şekilde kullanılarak zor sorunları çözmeye yöneliktir.

Service Fabric mikro yaklaşım kullanan uygulamalar oluşturmanıza yardımcı olmak için iki geniş alanları sağlar:

-   Dağıtmak için sistem hizmetleri sağlayan bir platform ölçeklendirme, yükseltme, algılamak, başarısız hizmetlerini yeniden başlatın, hizmet konumu bulmak, durumunu yönetme ve durumunu izleyin. Bu sistem hizmetleri yürürlükte daha önce açıklanan mikro özelliklerinin çoğunu sağlar.

-   Programlama API'leri veya frameworks mikro uygulamalar oluşturmanıza yardımcı olmak için: [güvenilir aktörler ve güvenilir hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Elbette, mikro hizmet oluşturmak için herhangi bir kod seçebilirsiniz ancak bu API'leri iş daha kolay hale ve bunlar daha ayrıntılı bir düzeyde platformuyla tümleştirebilirsiniz. Sistem durumu ve tanılama bilgileri veya alabilirsiniz bu şekilde güvenilir durum yönetimi yararlanabilir.

Service Fabric hizmetinizin nasıl oluşturulacağına göre bağımsızdır ve herhangi bir teknoloji kullanabilirsiniz. Ancak, daha kolay mikro oluşturmak için yerleşik programlama API'ler sağlar.

Şekil 4-9 oluşturmak ve basit işlemler veya Docker kapsayıcılar olarak Service Fabric mikro çalıştırmak nasıl gösterir. Kapsayıcı tabanlı mikro işlem tabanlı mikro aynı Service Fabric kümesi içinde ile karışık mümkündür.

![](./media/image13.png)

Şekil 4-9: mikro işlemler veya Azure Service Fabric kapsayıcılarında olarak dağıtma

Linux ve Windows konaklarda tabanlı Service Fabric kümeleri Docker Linux kapsayıcıları ve Windows kapsayıcıları çalıştırabilirsiniz.

**Daha fazla bilgi** Service Fabric kapsayıcıları desteği hakkında güncel bilgi Azure Web sitesinde okuma [Service Fabric ve kapsayıcıları](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric ile bir başka mantıksal mimarisine (iş mikro veya sınırlanmış bağlamları) fiziksel uygulama tanımlayabilirsiniz platformun iyi bir örnektir. Örneğin, uygulamanız [durum bilgisi olan güvenilir hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) içinde [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), sonraki bölümde sunulan "[Stateless durum bilgisi olan mikrokarşı](#stateless-versus-stateful-microservices), "birden çok fiziksel hizmetleriyle iş mikro hizmet kavramını sahip.

Şekil 4-10 ve bir doku durum bilgisi olan güvenilir hizmeti uygularken mantıksal/iş mikro açısından, düşünmeye olarak gösterilen, genellikle iki katmanı Hizmetleri uygulamak gerekir. İlk birden çok bölüm işleyen arka uç durum bilgisi olan güvenilir hizmetidir. , Ön uç hizmeti veya ağ geçidi hizmeti, Yönlendirme ve veri toplama birden çok bölüm veya durum bilgisi olan hizmet örnekleri sorumlu saniyedir. Bu ağ geçidi hizmeti, istemci-tarafı iletişim Service Fabric ile birlikte kullanılan arka uç hizmetine erişim yeniden deneme döngüsü ile aynı zamanda işleyen [ters proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image14.png)

Şekil 4-10: iş mikro Service Fabric birkaç durum bilgisi olan ve durum bilgisiz Hizmetleri ile

Herhangi bir durumda, hizmet doku durum bilgisi olan güvenilir hizmetler kullandığınızda, ayrıca, genellikle birden çok fiziksel hizmetlerinden oluşur bir mantıksal veya iş mikro hizmet (ilişkisindeki bağlamı) vardır. Her bunları, ağ geçidi hizmeti ve bölüm hizmet olarak ASP.NET Web API Hizmetleri, Şekil 4-10'da gösterildiği gibi uygulanabilir.

Service Fabric grup ve grupları Hizmetleri dağıtma bir [Service Fabric uygulaması](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), birim paketleme ve dağıtım orchestrator veya kümesine ait değil. Bu nedenle, Service Fabric uygulaması bu otonom iş ve mantıksal mikro hizmet sınır veya sınırlanmış bağlamı da eşleştirilebilir.

### <a name="service-fabric-and-containers"></a>Service Fabric ve kapsayıcıları

Service Fabric kapsayıcılara göre kapsayıcı görüntüler Service Fabric kümesi içinde Hizmetleri'nde de dağıtabilirsiniz. Şekil 4-11, çoğu hizmeti başına yalnızca bir kapsayıcı olacaktır zaman gösterilmektedir.

![](./media/image15.png)

Şekil 4-11: iş mikro Service Fabric olarak birkaç hizmetleriyle (kapsayıcı)

Ancak, sözde "sepet" (birlikte mantıksal bir hizmetin parçası olarak dağıtılması gereken iki kapsayıcı) de Service Fabric olası kapsayıcılardır. Önemli şey iş mikro hizmet birkaç bağlı öğeleri mantıksal sınırlarından olmasıdır. Çoğu durumda, bir tek veri modeli tek bir hizmetle olabilir, ancak bazı diğer durumlarda fiziksel birkaç hizmetleri de sahip olabilir.

Bu (Nisan 2017) yazma itibariyle, Service Fabric BT güvenilir durum bilgisi olan hizmetler kapsayıcılarında dağıtamazsınız — yalnızca konuk kapsayıcıları, durum bilgisi olmayan hizmetler veya aktör Hizmetleri kapsayıcılarında dağıtabilirsiniz. Ancak Şekil 4-12'de gösterildiği gibi işlemleri Hizmetleri'nde ve aynı Service Fabric uygulaması kapsayıcılarında Hizmetleri'nde karıştırabilirsiniz unutmayın.

![](./media/image16.png)

Şekil 4-12: bir Service Fabric uygulaması kapsayıcıları ve durum bilgisi olan hizmetler ile eşlenmiş iş mikro hizmet

Destek, Docker kapsayıcıları Linux veya Windows kapsayıcıları kullanmanıza bağlı olarak farklıdır. Service Fabric kapsayıcılarında desteği, gelecek sürümlerde genişletme. Azure Web sitesinde Service Fabric, kapsayıcı desteği hakkında güncel haberleri okuyun [Service Fabric ve kapsayıcıları](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Durum bilgisiz durum bilgisi olan mikro karşılaştırması

Daha önce belirtildiği gibi her mikro hizmet (mantıksal sınırlanmış içerik), etki alanı modeli (verileri ve mantığı) sahip olmanız gerekir. Durum bilgisiz mikro söz konusu olduğunda, veritabanlarını SQL Server gibi ilişkisel seçenekleri ya da MongoDB veya Azure DocumentDB gibi NoSQL seçenekleri kullanan dış olacaktır.

Ancak Hizmetleri kendilerini ayrıca veri mikro hizmet içinde bulunan başka bir deyişle, durum bilgisi olabilir. Bu veri sürücülerinde kalıcı aynı sunucu üzerinde değil, ancak bellekte mikro hizmet işlemi içinde mevcut olabilecek ve diğer düğümlere yinelenmiş. Şekil 4-13 farklı yaklaşımlara gösterir.

![](./media/image17.png)

Şekil 4-13: durum bilgisiz durum bilgisi olan mikro karşılaştırması

Durum bilgisi olmayan bir yaklaşım mükemmel geçerli değil ve bir yaklaşım için geleneksel ve bilinen desenleri benzer olduğundan durum bilgisi olan mikro uygulamak daha kolay olur. Ancak durum bilgisiz mikro zorunlu tuttukları işlem ve veri kaynakları arasındaki gecikme süresi. Bunlar ayrıca ek önbellek ve Kuyruklar ile performansını artırmak çalışırken daha hareketli parça içerir. Sonuç, çok fazla katmanlarına sahip karmaşık mimarileri ile düşebilir emin olur.

Buna karşılık, [durum bilgisi olan mikro](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) etki alanı mantığı ve verileri arasında bir gecikme olduğundan Gelişmiş senaryolar excel. Yoğun veri işleme, oyun arka uçları, hizmet ve tüm yerel durumu için daha hızlı erişim sağlayan durum bilgisi olan hizmetler yararlı diğer düşük gecikmeli senaryolar olarak veritabanları.

Durum bilgisiz ve durum bilgisi olan Tamamlayıcı hizmetleridir. Örneğin, durum bilgisi olan hizmet birden çok bölüme bölme. Bu bölümler erişmek için bölüm anahtara göre her bir bölümü adres bildiği bir ağ geçidi hizmeti olarak davranan bir durum bilgisiz hizmet gerekebilir.

Durum bilgisi olan hizmetler sakıncaları vardır. Bunlar, genişletilecek veren karmaşıklık düzeyini zorunlu tuttukları. Genellikle dış veritabanı sistemleri tarafından uygulanan işlevleri veri çoğaltma gibi görevler için durum bilgisi olan mikro ve veri bölümlendirme arasında ele alınması gerekir. Ancak, bu bir orchestrator oluşturulacağı yeri alanlardan biridir [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) ile kendi [durum bilgisi olan güvenilir hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) en yardımcı olabilir — geliştirme ve durum bilgisi olan yaşam döngüsü basitleştirme tarafından mikro kullanarak [güvenilir Hizmetleri API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) ve [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Aktör deseni destekleyen ve hataya dayanıklılık ve iş mantığı ve verileri arasında gecikme geliştirmek durum bilgisi olan hizmetler izin diğer mikro hizmet çerçeveler Microsoft, [Orleans](https://github.com/dotnet/orleans)Microsoft Research ve [ Akka.NET](https://getakka.net/). Her iki çerçeveleri şu anda Docker için destek geliştirme.

Docker kapsayıcıları durum bilgisiz kendilerini olduğuna dikkat edin. Durum bilgisi olan hizmet uygulamak istiyorsanız, daha önce not ettiğiniz ek önerilerde bulunan ve üst düzey çerçeveleri biri gerekir. Ancak, bu makalenin yazıldığı sırada durum bilgisi olan Service Fabric Hizmetleri'nde düz mikro olarak yalnızca kapsayıcı olarak desteklenmez. Güvenilir hizmetler destek kapsayıcılarında Service Fabric gelecek sürümlerinde kullanılabilir.


>[!div class="step-by-step"]
[Önceki] (soa-applications.md) [sonraki] (docker-apps-development-environment.md)
