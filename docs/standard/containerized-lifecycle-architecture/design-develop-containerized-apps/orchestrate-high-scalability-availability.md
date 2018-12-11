---
title: Mikro Hizmetleri ve yüksek ölçeklenebilirlik ve kullanılabilirlik için çok kapsayıcılı uygulamaları yönetme
description: Microsoft Platformu ve araçları ile kapsayıcı Docker uygulaması yaşam
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/19/2017
ms.openlocfilehash: fa64562808bba9c9dea5a5eedc367af7decf83b7
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126906"
---
# <a name="orchestrating-microservices-and-multicontainer-applications-for-high-scalability-and-availability"></a>Mikro Hizmetleri ve yüksek ölçeklenebilirlik ve kullanılabilirlik için çok kapsayıcılı uygulamaları yönetme

Uygulamanız üzerinde mikro hizmet tabanlı ya da birden çok kapsayıcıda yalnızca bölme düzenleyicileri kullanarak üretime hazır uygulamalar için gereklidir. Böylece bir geliştirme ve dağıtım açısından otonom mikro hizmet tabanlı bir yaklaşım, daha önce tanıtılan her mikro hizmet kendi modeli ve veri sahibi. Ancak oluşan daha geleneksel bir uygulama (SOA gibi) birden çok Hizmetleri olsa da birden çok kapsayıcı veya hizmet dağıtılmış bir sistemde dağıtılması gereken bir tek iş uygulaması oluşturan gerekir. Ölçeği genişletme ve yönetmek için bu tür sistemler karmaşıktır; Bu nedenle, üretime hazır ve ölçeklenebilir çok kapsayıcılı bir uygulama istiyorsanız kesinlikle bir orchestrator gerekir.

Şekil 4-6, bir uygulama (kapsayıcılar) birden çok mikro hizmetlerden oluşan bir küme içine dağıtım gösterilmektedir.

![](./media/image6.png)

Şekil 4-6: Kapsayıcıları kümesi

Mantıksal bir yaklaşım gibi görünüyor. Ancak Yük Dengeleme, Yönlendirme ve oluşan bu uygulamaları işlemlerini nasıl işlediğinin?

Docker komut satırı arabirimi (CLI) bir konak üzerindeki bir kapsayıcı yönetme gereksinimlerini karşılayan, ancak daha karmaşık dağıtılmış uygulamaların birden çok konak üzerinde dağıtılan birden çok kapsayıcı yönetmek için söz konusu olduğunda kısa döner. Çoğu durumda, otomatik olarak kapsayıcıları Başlat, bunları, askıya alma veya gerektiğinde Kapat ve ideal olarak ayrıca ağ ve veri depolama alanı gibi kaynakları nasıl erişim denetimi yönetim platformu gerekir.

Kapsayıcılara veya çok basit oluşturulmuş uygulamalar ve mikro Hizmetleri daha büyük kuruluş uygulamaları doğru taşıma yönetimini ötesine gitmek için düzenleme ve platformları kümeleme için etkinleştirmeniz gerekir.

Yapı büyük, Kurumsal, mikro hizmet tabanlı olması durumunda bir mimari ve geliştirme açısından bakıldığında, uygulamalar, aşağıdaki platformları ve Gelişmiş senaryolar destekleyen ürünleri anlamak önemlidir:

-   **Kümeler ve düzenleyicileri** ölçeklendirmek gerektiğinde-uygulamalarının çoğu Docker ana bilgisayarları arasında olduğu gibi büyük mikro hizmet tabanlı uygulamaları ile tüm bu konak tarafından tek bir küme olarak yönetmek için önemlidir temel platform karmaşıklığını özetleyen. Neler kapsayıcı kümeleri ve düzenleyicileri sağlar olmasıdır. Docker Swarm, Mesosphere DC/OS, Kubernetes (ilk üç Azure Container Service kullanılabilir) ve Azure Service Fabric düzenleyicileri örnekleridir.

-   **Zamanlayıcılar** *zamanlama* özelliğine de bir kullanıcı arabirimi sağlar, böylece bir kümedeki kapsayıcıları başlatmak bir yöneticinin anlamına gelir. Bir küme Zamanlayıcı çeşitli sorumlulukları vardır: küme kaynaklarını verimli bir şekilde kullanmak için verimli bir şekilde düğümleri veya konaklar arasında Yük Dengeleme kapsayıcıları için kullanıcı tarafından sağlanan kısıtlamaları ayarlamak ve yüksek sağlarken hatalarına karşı güçlü Kullanılabilirlik.

Genellikle farklı satıcılar tarafından sağlanan ürün iki yetenekleri sağlamak için bir küme ve bir zamanlayıcı yakından ilişkilidir. Tablo 4-1 en önemli platformu ve kümeler ve planlayıcılar için sahip olduğunuz yazılım seçenekleri listeler. Bu kümeler, genellikle Azure gibi genel bulutlarda sunulur.

Tablo 4-1: Yazılım platformlarının kümeleme kapsayıcı, düzenleme ve zamanlama için

| Platform | Açıklama |
|---|---|
| Docker Swarm<br/> ![Docker Swarm logosu](./media/image7.png) | Docker Swarm, Docker kapsayıcıları zamanlayabilir ve küme olanağı sağlar. Swarm kullanarak Docker ana bilgisayarları havuzu tek, sanal bir Docker konağı kapatabilirsiniz. İstemcilerin API isteklerinin Swarm için Swarm ölçeklendirmek için uygulamaları için birden çok konak kolaylaştırır, yani Konaklara aynı şekilde yapabilirsiniz. <br /><br /> Docker Swarm, docker, şirket için kullanılan bir üründür. <br /><br /> Docker v1.12 veya yerel ve yerleşik Swarm modu daha sonra çalıştırabilir. |
| Mesosphere DC/OS<br/>![Mesosphere DC/OS logosu](./media/image8.png) |  Mesosphere Kurumsal DC/OS (üzerinde Apache Mesos tabanlı), kapsayıcılar ve dağıtılan uygulamaları çalıştırmak bir üretime hazır platformudur. <br /><br /> DC/OS kümesinde kullanılabilir kaynakları koleksiyonu özetleyen ve bu kaynaklar üzerinde oluşturulan bileşenler için kullanılabilir hale getirme çalışır. Marathon, genellikle DC/OS ile tümleşik bir zamanlayıcı olarak kullanılır. |
| Google Kubernetes<br />![Google Kubernetes logosu](./media/image9.png) | Kubernetes kümesi altyapısı ve zamanlama işlemlerini özellikleri için kapsayıcı aralıkları işlevselliği sağlayan açık kaynaklı üründür. Bununla, konak kümeleri arasında dağıtım, ölçeklendirme ve uygulama kapsayıcıların işlemlerini otomatikleştirebilirsiniz. <br /><br /> Kubernetes uygulama kapsayıcıları kolay yönetim ve bulma için mantıksal birimler halinde gruplandırır kapsayıcı merkezli bir altyapı sağlar. |
| Azure Service Fabric<br />![Azure Service Fabric logosu](./media/image10.png) | [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview) uygulamaları oluşturmaya yönelik bir Microsoft mikro hizmet platformudur. Bu bir [orchestrator](https://docs.microsoft.com/azure/service-fabric/service-fabric-cluster-resource-manager-introduction) , hizmetleri ve makine kümeleri oluşturur. Varsayılan olarak, Service Fabric dağıtır ve hizmet işlemleri olarak etkinleştirir, ancak Service Fabric, Docker kapsayıcı görüntüleri Hizmetleri'nde dağıtabilirsiniz. Daha da önemlisi hizmetleriyle aynı uygulamada kapsayıcılardaki Hizmetleri karıştırabilirsiniz. <br /><br /> Mayıs 2017'den itibaren Docker kapsayıcıları olarak dağıtma hizmetlerini destekleyen bir Service Fabric Önizleme durumda özelliğidir. <br /><br /> Service Fabric Hizmetleri kullanarak birçok yönden geliştirebilirsiniz [Service Fabric programlama modellerini](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework) dağıtma [Konuk yürütülebilir dosyaları](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-existing-app) kapsayıcıları yanı sıra. Service Fabric gibi öngörücü uygulama modellerini destekler [durum bilgisi olan hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) ve [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

## <a name="using-container-based-orchestrators-in-azure"></a>Azure'da kapsayıcı tabanlı düzenleyicileri kullanma

Docker kapsayıcıları desteği yanı sıra Docker kümeler ve düzenleme desteği, Azure, Amazon EC2 Container Service ve Google Container altyapısı dahil olmak üzere birden fazla bulut satıcılarına sunar. Azure Docker sonraki bölümde açıklandığı gibi Azure Container Service kümesi ve orchestrator desteğini sağlar.

Başka bir seçenek de Linux ve Windows kapsayıcıları göre Docker'ı destekleyen Azure Service Fabric kullanmaktır. Service Fabric, Azure veya diğer bir bulutta çalışan yanı [şirket içi](https://docs.microsoft.com/azure/service-fabric/service-fabric-deploy-anywhere).

## <a name="using-azure-container-service"></a>Azure Container Service'i kullanma

Bir Docker kümesi birden fazla Docker ana bilgisayarları havuzları ve birden çok kapsayıcı kümesine dağıtmak için bunları bir tek sanal Docker konağı olarak kullanıma sunar. Küme ölçeklenebilirliği ve sistem durumu gibi karmaşık yönetim tesisat işler. Şekil 4-7, oluşturulan uygulamalar için bir Docker kümesi Container Service'e nasıl eşlendiğini temsil eder.

Kapsayıcı hizmeti oluşturma, yapılandırma ve kapsayıcılı uygulamaları çalıştırmak için önceden yapılandırılmış bir VM kümesi yönetimini basitleştirmek için bir yol sağlar. Popüler açık kaynak planlama ve düzenleme araçlarının iyileştirilmiş yapılandırmalarını kullanarak, kapsayıcı hizmeti, mevcut becerilerinizi kullanabilir veya dağıtmak ve kapsayıcı tabanlı yönetmek için topluluk uzmanlığından geniş ve büyüyen gövdesi üzerinde çizim olanağı sağlar Azure uygulamalarında.

Kapsayıcı hizmeti popüler Docker kümeleme açık kaynaklı araçların ve teknolojilerin yapılandırmasını özellikle Azure'a yönelik en iyi duruma getirir. Hem kapsayıcılarınız hem de uygulama yapılandırmanız için taşınabilirlik sunan bir açık çözümü sahip olursunuz. Boyutu, konak sayısını ve düzenleyici araçlarını seçin ve kapsayıcı hizmeti, diğer her şey yapar.

Kapsayıcı hizmeti, uygulama kapsayıcılarınızın tamamen taşınabilir olmasını sağlamak için Docker görüntüleri kullanır. Bu, seçiminiz bu uygulamaları binlerce veya on binlerce kapsayıcının göre ölçeklendirilebileceğinden emin olmak için DC/OS, Kubernetes ve Docker Swarm gibi açık kaynaklı düzenleme platformlarını destekler.

Azure Container Service ile Azure'un kuruluş düzeyindeki özelliklerinden faydalanırken düzenleme katmanına dahil olmak üzere uygulama taşınabilirliğini, yararlanabilirsiniz.

![](./media/image11.png)

Şekil 4-7: Azure Container Service'te küme seçenekleri

Şekil 4-8'de gösterildiği gibi Container Service DC/OS, Kubernetes ve Docker Swarm dağıtmak için Azure tarafından sağlanan altyapı yalnızca olduğu, ancak herhangi bir ek orchestrator uygulamaz. Bu nedenle, değil bir orchestrator, bu nedenle kapsayıcı hizmetidir; kapsayıcılar için açık kaynak düzenleyicileri mevcut yararlanan bir altyapısı var.

![](./media/image12.png)

Şekil 4-8: Container Service'te düzenleyicileri

Kullanım açısından bakıldığında, kapsayıcı hizmeti popüler açık kaynak araçları ve teknolojileri kullanan bir kapsayıcı barındırma ortamı sağlamak için hedefidir. Şu an için kullandığınız düzenleyici için standart API uç noktalarını gösterir. Bu uç noktaları kullanarak, bu uç noktalar ile iletişim kurabilen herhangi bir yazılım kullanabilirsiniz. Örneğin, Docker Swarm uç noktasıyla Docker CLI'yı kullanmayı seçebilirsiniz. DC/OS için DC/OS CLI'yı kullanmayı seçebilirsiniz.

### <a name="getting-started-with-container-service"></a>Container Service ile çalışmaya başlama

Container Service'i kullanmaya başlamak için bir kapsayıcı hizmeti kümesi Azure portalında bir Azure Resource Manager şablonu kullanarak dağıtmanız veya [CLI](https://docs.microsoft.com/cli/azure/install-azure-cli). Kullanılabilir şablonlar [Docker Swarm](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-swarm), [Kubernetes](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-kubernetes), ve [DC/OS](https://github.com/Azure/azure-quickstart-templates/tree/master/101-acs-dcos). Hızlı Başlangıç şablonları, ek veya Gelişmiş Azure yapılandırmalarını dahil edecek şekilde değiştirebilirsiniz.

**Daha fazla bilgi** Azure Web sitesinde bir Container Service kümesi dağıtma hakkında daha fazla bilgi edinmek için okumaya devam [bir Azure Container Service kümesi dağıtma](https://docs.microsoft.com/azure/container-service/dcos-swarm/container-service-deployment).

Herhangi bir ACS bir parçası olarak varsayılan olarak yüklü olan yazılım için herhangi bir ücret yoktur. Tüm varsayılan seçenekleri ile açık kaynaklı yazılım uygulanır.

Kapsayıcı hizmeti şu anda standart A, D, DS, G ve GS serisi azure'da Linux VM'ler için kullanılabilir. Yalnızca depolama ve ağ gibi kullanılan temel altyapı kaynakları yanı sıra seçtiğiniz işlem örnekleri için ücretlendirilirsiniz. Artımlı ücretlendirme yoktur kapsayıcı hizmetinin kendisi.

### <a name="additional-resources"></a>Ek kaynaklar

Burada bulabilirsiniz ek bilgi konumları şunlardır:

-   Docker kapsayıcı barındırma çözümlerine Container Service ile giriş:  
    https://docs.microsoft.com/azure/container-service/kubernetes/container-service-intro-kubernetes>

-   Docker Swarm'a genel bakış:  
    <https://docs.docker.com/swarm/overview/>

-   Swarm modu genel bakış:  
    <https://docs.docker.com/engine/swarm/>

-   Mesosphere DC/OS genel bakış:    
    <https://docs.mesosphere.com/1.7/overview/>

-   Kubernetes (resmi site):  
    <https://kubernetes.io/>

## <a name="using-service-fabric"></a>Service Fabric kullanarak

Service Fabric, Microsoft'un geçiş stili genellikle tek parçalı, "kutu" ürünleri, hizmetleri sunmak için teslim öğesinden gelen çıkan. Service Fabric oluşturma ve büyük hizmetlerini uygun ölçekte, Azure SQL veritabanı, Azure Document DB, Azure Service Bus veya Cortana'nın arka uç, gibi işletim deneyimini şeklinde. Bunu daha da fazla Hizmetleri benimsenen gibi platform zaman içinde gelişerek. Önemlisi, yalnızca Azure aynı zamanda tek başına Windows Server dağıtımlarındaki çalıştırmak Service Fabric vardı.

Service Fabric amacı oluşturma ve bir hizmetin çalıştırılması ve takımlar bir mikro hizmet yaklaşımı kullanarak iş sorunlarını çözebilir. böylece altyapı kaynaklarını verimli bir şekilde yararlanarak zor sorunları çözmek sağlamaktır.

Service Fabric, mikro hizmetler yaklaşımı kullanan uygulamalar oluşturmanıza yardımcı olmak üzere iki geniş alanları sağlar:

-   Dağıtmak için sistem hizmetleri sağlayan bir platform ölçeklendirme, yükseltme, algılamanıza ve başarısız hizmetlerini yeniden başlatın, hizmet konumu bulmak, durumunu yönetme ve durumunu izleyin. Bu sistem hizmetleri etkin birçok mikro Hizmetleri daha önce açıklanan özelliklerini sağlar.

-   Programlama API'leri veya çerçeveleri, mikro hizmetler olarak uygulamalar oluşturmanıza yardımcı olacak: [reliable actors ve güvenilir hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Elbette, mikro hizmet oluşturmak için herhangi bir kod seçebilirsiniz ancak bu API'leri işi daha basit hale ve bunlar daha ayrıntılı bir platform ile tümleştirin. Güvenilir durum yönetimi, sistem durumu ve tanılama bilgileri veya alabilirsiniz bu şekilde yararlanabilirsiniz.

Service Fabric hizmetinizin nasıl oluşturulacağına göre belirsiz olduğundan ve tüm teknolojileri kullanabilirsiniz. Bununla birlikte, mikro hizmetler oluşturmayı kolay hale getiren yerleşik programlama API'leri sağlar.

Şekil 4-9 nasıl oluşturabileceğinizi ve basit işlemler ya da Docker kapsayıcıları olarak Service Fabric mikro hizmetler çalıştırmak gösterir. Kapsayıcı tabanlı mikro hizmetler ile işlem tabanlı mikro hizmetler aynı Service Fabric kümesi içinde karma olarak mümkündür.

![](./media/image13.png)

Şekil 4-9: Mikro hizmetler, işlemler veya Azure Service Fabric'teki kapsayıcıları olarak dağıtma

Linux ve Windows ana bilgisayarlarını temel alan Service Fabric kümelerinde Docker Linux kapsayıcıları ve Windows kapsayıcıları çalıştırabilirsiniz.

**Daha fazla bilgi** Service fabric'te kapsayıcı desteği hakkında güncel bilgi Azure Web sitesinde okuma [Service Fabric ve kapsayıcılar](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric, bir farklı mantıksal mimarisine (iş mikro hizmetler veya sınırlanmış Bağlamlar) fiziksel uygulaması tanımlayabilirsiniz Platform iyi bir örnektir. Örneğin, uygulamanız [durum bilgisi olan Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) içinde [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), sonraki bölümde tanıtılır "[durum bilgisi olmayan durum bilgisi olan mikro Hizmetlerkarşı](#stateless-versus-stateful-microservices), "birden çok fiziksel Hizmetleri ile iş mikro hizmet kavramını sahip.

Şekil 4-10 yanı sıra, bir Service Fabric durum bilgisi olan güvenilir hizmet uygularken mantıksal/iş mikro hizmet açısından, düşünme olarak gösterilen, genellikle iki katmanda Hizmetleri uygulamak ihtiyacınız olacak. İlk birden çok bölüm işleme arka uç durum bilgisi olan güvenilir hizmetidir. Ön uç hizmeti veya birden çok bölüm ya da durum bilgisi olan hizmet örnekleri arasında yönlendirme ve veri toplama sorumlu ağ geçidi hizmeti saniyedir. Bu ağ geçidi hizmeti de yeniden deneme döngüleri Service Fabric ile birlikte kullanılan arka uç hizmetine erişim ile istemci tarafı iletişimi gerçekleştirir [ters proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image14.png)

Şekil 4-10: Service fabric'te birkaç durum bilgisi olan ve olmayan Hizmetleri ile iş mikro hizmet

Herhangi bir durumda, Service Fabric durum bilgisi olan Reliable Services kullandığınızda, ayrıca, genellikle birden çok fiziksel hizmetlerinden oluşur bir mantıksal veya iş mikro hizmet (içerik sınırlanmış) vardır. Bunları, ağ geçidi hizmet ve bölüm hizmeti her ASP.NET Web API Hizmetleri olarak Şekil 4-10'da gösterildiği gibi uygulanabilir.

Service Fabric'te, Grup ve hizmet olarak grupları dağıtma bir [Service Fabric uygulaması](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), paketleme ve dağıtım için orchestrator ya da küme biriminin olduğu. Bu nedenle, Service Fabric uygulaması bu otonom iş ve mantıksal bir mikro hizmet sınırı veya içerik sınırlanmış, de eşleştirilebilir.

### <a name="service-fabric-and-containers"></a>Service Fabric ve kapsayıcılar

Service Fabric'teki kapsayıcıları onaylamaz, Service Fabric kümesi dahilindeki kapsayıcı görüntülerinizi Hizmetleri'nde dağıtabilirsiniz. Şekil 4-11 çoğu hizmet başına yalnızca bir kapsayıcı olacağı süreyi gösterir.

![](./media/image15.png)

Şekil 4-11: Çeşitli Hizmetleri (kapsayıcılar) Service Fabric ile mikro iş

Bununla birlikte, sözde "sepet" (mantıksal bir hizmetin parçası olarak birlikte dağıtılmış olması gereken iki kapsayıcı) de Service Fabric'te olası kapsayıcılardır. Önemli olan iş mikro hizmet birkaç cohesive öğeleri mantıksal sınırlarından olmasıdır. Çoğu durumda, bir tek veri modeli ile tek bir hizmet olabilir, ancak diğer bazı durumlarda, fiziksel birçok hizmet de olabilir.

Şu (Nisan 2017) andan itibaren Service Fabric'te kapsayıcılarına SF güvenilir durum bilgisi olan hizmetler dağıtamazsınız; yalnızca konuk kapsayıcılar, durum bilgisi olmayan hizmetler veya aktör hizmetlerle kapsayıcılardaki dağıtabilirsiniz. Ancak, Şekil 4-12'de gösterildiği gibi hizmetleri ve kapsayıcıları Service Fabric uygulamasının Hizmetleri'nde kullanabileceğinizi unutmayın.

![](./media/image16.png)

Şekil 4-12: Kapsayıcılar ve durum bilgisi olan hizmetler ile bir Service Fabric uygulaması için eşleştirilmiş iş mikro hizmet

Destek, Docker kapsayıcıları Linux veya Windows kapsayıcıları kullanmanıza bağlı olarak farklıdır. Service Fabric'teki kapsayıcıları için destek, gelecek sürümlerde genişletme. Service fabric'te kapsayıcı desteği Azure Web sitesinde ilgili güncel haberler için okuma [Service Fabric ve kapsayıcılar](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Durum bilgisiz ve durum bilgisi olan mikro hizmetler

Her mikro hizmet (mantıksal içerik sınırlanmış), daha önce bahsedildiği gibi etki alanı modeli (veri ve mantıksal) sahip olmanız gerekir. Durum bilgisi olmayan mikro hizmetler söz konusu olduğunda, veritabanları, SQL Server gibi ilişkisel seçenekleri veya MongoDB veya Azure DocumentDB gibi NoSQL seçenekleri kullanan dış olacaktır.

Ancak hizmetler ayrıca veri mikro hizmet içinde bulunduğu anlamına gelir durum bilgisi olabilir. Bu veri sürücülerinde kalıcı aynı sunucuda değil, ancak mikro hizmet işlemi, bellek içinde mevcut olabilecek ve diğer düğümlere çoğaltılır. Şekil 4-13 farklı yaklaşımlar gösterir.

![](./media/image17.png)

Şekil 4-13: Durum bilgisiz ve durum bilgisi olan mikro hizmetler

Durum bilgisi olmayan bir yaklaşım mükemmel geçerli olduğundan ve durum bilgisi olan mikro hizmetler geleneksel ve iyi bilinen desenleri için benzer bir yaklaşımdır çünkü uygulamak daha kolaydır. Ancak, durum bilgisi olmayan mikro hizmetler, işlem ve veri kaynakları arasındaki gecikme süresini büyük oranda yansıtmaktadır. Bunlar ayrıca performansı ek önbellek ve Kuyruklar ile çalışılırken daha fazla hareketli parça içerir. Sonuç, çok fazla katman karmaşık mimarilerin kalabilirsiniz emin olur.

Buna karşılık, [durum bilgisi olan mikro Hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) Gelişmiş senaryolarda etki alanı mantığı ve verileri arasında herhangi bir gecikme olduğundan excel. Yoğun veri işleme, oyun arka uçları, veritabanları ve diğer düşük gecikmeli senaryolar tüm yerel durumu için daha hızlı erişim sağlayan durum bilgisi olan hizmetler yararlanın hizmeti olarak.

Durum bilgisiz ve durum bilgisi olan hizmetler tamamlayıcıdır. Örneğin, durum bilgisi olan hizmet birden çok bölümdeki bölme. Bu bölümler erişmek için bildiği her bölüm bölüm anahtara göre ele almak bir ağ geçidi hizmeti olarak davranan bir durum bilgisi olmayan hizmet gerekebilir.

Durum bilgisi olan hizmetler dezavantajları vardır. Bunlar, ölçeği genişletme imkan tanıyan karmaşıklık düzeyini büyük oranda yansıtmaktadır. Genellikle dış veritabanı sistemleri tarafından uygulanan işlevleri veri çoğaltma gibi görevler için durum bilgisi olan mikro hizmetler ve bölümleme verilerde ele alınması gerekir. Burada bir orchestrator gibi alanlarından budur ancak [Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) ile kendi [durum bilgisi olan reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) en çok yardımcı olabilir; geliştirme ve durum bilgisi olan yaşam döngüsü basitleştirerek mikro hizmetler kullanarak [Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) ve [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Gerçekleştiren deseni destekleyen ve hataya dayanıklılık ve iş mantığı ve verileri arasındaki gecikme süresini artırmak durum bilgisi olan hizmetler sağlayan diğer mikro hizmet çerçeveleri olan Microsoft [Orleans](https://github.com/dotnet/orleans), Microsoft Research ve [ Akka.NET](https://getakka.net/). Her iki çerçeveler kendi Docker desteği şu anda geliştirdiğinizi.

Docker kapsayıcıları durum bilgisiz kendilerini olduğunu unutmayın. Durum bilgisi olan hizmet uygulamak istiyorsanız, daha önce not ettiğiniz ek önerilerde bulunan ve daha üst düzey altyapılarından birini gerekir. Ancak, bu makalenin yazıldığı tarih itibarıyla, Service fabric'te durum bilgisi olan hizmetler düz mikro hizmetler olarak yalnızca bir kapsayıcı olarak desteklenmez. Reliable services desteği kapsayıcıları Service Fabric gelecek sürümlerinde kullanıma sunulacak.

>[!div class="step-by-step"]
>[Önceki](soa-applications.md)
>[İleri](docker-apps-development-environment.md)