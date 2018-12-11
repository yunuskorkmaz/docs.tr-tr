---
title: Azure Service Fabric kullanma
description: Yalnızca Bu kapsayıcıları düzenlemek için kullanmanın yanı sıra kullanabileceğiniz hangi Azure Service Fabric uygulama modellerini anlayın.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/20/2018
ms.openlocfilehash: b29be05f5ab353ddfae0d23211efaf57979d0604
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53126971"
---
# <a name="using-azure-service-fabric"></a>Azure Service Fabric kullanma

Azure Service Fabric, Microsoft'un geçiş stili genellikle tek parçalı, kutusu ürünleri, hizmetleri sunmak için teslim öğesinden gelen çıkan. Service Fabric yapı ve büyük hizmetlerini uygun ölçekte, Azure SQL veritabanı, Azure Cosmos DB, Azure Service Bus veya Cortana'nın arka ucu gibi işletim deneyimini şeklinde. Bunu daha da fazla Hizmetleri benimsenen gibi platform zaman içinde gelişerek. Önemlisi, yalnızca Azure aynı zamanda tek başına Windows Server dağıtımlarındaki çalıştırmak Service Fabric vardı.

Takımlar bir mikro hizmet yaklaşımı kullanarak iş sorunlarını çözebilir. böylece, oluşturma ve bir hizmetin çalıştırılması ve altyapı kaynaklarını verimli bir şekilde yararlanarak sabit sorunları çözmek için Service Fabric amacı olan.

Service Fabric, mikro hizmetler yaklaşımı kullanan uygulamalar oluşturmanıza yardımcı olmak üzere iki geniş alanları sağlar:

- Dağıtmak için sistem hizmetleri sağlayan bir platform ölçeklendirme, yükseltme, algılamanıza ve başarısız hizmetlerini yeniden başlatın, hizmet konumu bulmak, durumunu yönetme ve durumunu izleyin. Bu sistem hizmetlerini etkin mikro Hizmetleri daha önce açıklanan özelliklerini etkinleştirir.

- Mikro hizmet uygulamaları oluşturmanıza yardımcı olmak için programlama API'leri veya çerçeveleri: [reliable actors ve güvenilir hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Mikro hizmet oluşturmak için herhangi bir kod seçebilirsiniz ancak bu API'leri işi daha basit hale ve bunlar daha ayrıntılı bir platform ile tümleştirin. Güvenilir durum yönetimi, sistem durumu ve tanılama bilgileri veya alabilirsiniz bu şekilde yararlanabilirsiniz.

Service Fabric hizmetinizin nasıl oluşturulacağına göre belirsiz olduğundan ve tüm teknolojileri kullanabilirsiniz. Bununla birlikte, mikro hizmetler oluşturmayı kolay hale getiren yerleşik programlama API'leri sağlar.

Şekil 4-27'de gösterildiği gibi oluşturun ve Service Fabric'te mikro Hizmetleri; basit işlemler ya da Docker kapsayıcıları olarak çalışır. Kapsayıcı tabanlı mikro hizmetler ile işlem tabanlı mikro hizmetler aynı Service Fabric kümesi içinde karma olarak mümkündür.

![Karşılaştırması, Azure service Fabric kümeleri: Mikro hizmetler olarak her düğüme bir işlem için her bir mikro hizmetin çalıştığı işlemleri; Mikro hizmetler olarak her düğüme birkaç kapsayıcılar ile Docker çalıştığı kapsayıcılar mikro hizmet başına bir kapsayıcı.](./media/image30.png)

**Şekil 4-27**. Mikro hizmetler, işlemler veya Azure Service Fabric'teki kapsayıcıları olarak dağıtma

Linux ve Windows ana bilgisayarlarını temel alan Service Fabric kümelerinde Docker Linux kapsayıcıları ve Windows kapsayıcıları sırasıyla çalıştırabilirsiniz.

Azure Service fabric'te kapsayıcı desteği hakkında güncel bilgiler için bkz: [Service Fabric ve kapsayıcılar](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric, bir platformun iyi bir örnek burada bir farklı mantıksal mimarisine (iş mikro hizmetler veya sınırlanmış Bağlamlar) sunulan fiziksel uygulaması tanımlayabilirsiniz [fiziksel ve mantıksal mimarisi Mimari](logical-versus-physical-architecture.md) bölümü. Örneğin, uygulamanız [durum bilgisi olan Reliable Services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction), bölümünde tanıtılır [durum bilgisi olan mikro hizmetler ve durum bilgisi olmayan](#stateless-versus-stateful-microservices) ile iş mikro hizmet kavramını daha sonra olabilir birden çok fiziksel Hizmetleri.

Şekil 4-28 ve mantıksal/iş mikro hizmet açısından, bir Service Fabric durum bilgisi olan güvenilir hizmet uygularken düşünmeye olarak gösterilen, genellikle iki katmanda Hizmetleri uygulamak ihtiyacınız olacak. İlk (her bölüm bir durum bilgisi olan bir hizmettir) birden çok bölüm işleme arka uç durum bilgisi olan güvenilir hizmetidir. Ön uç hizmeti veya birden çok bölüm ya da durum bilgisi olan hizmet örnekleri arasında yönlendirme ve veri toplama sorumlu ağ geçidi hizmeti saniyedir. Bu ağ geçidi hizmeti, yeniden deneme döngüleri ile arka uç hizmetine erişim ayrıca istemci-tarafı iletişimi gerçekleştirir. Bir ağ geçidi hizmeti, özel bir hizmet ekleme ya da alternatif olarak kullanıma hazır Service Fabric ayrıca kullanabileceğiniz çağırdı [ters proxy](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image31.png)

**Şekil 4-28**. İş bir mikro hizmet birkaç durum bilgisi olan hizmet örnekleri ve özel ağ geçidi ön uç

Herhangi bir durumda, Service Fabric durum bilgisi olan Reliable Services kullandığınızda, ayrıca, genellikle birden çok fiziksel hizmetlerinden oluşur bir mantıksal veya iş mikro hizmet (içerik sınırlanmış) vardır. Bunları, ağ geçidi hizmet ve bölüm hizmeti her ASP.NET Web API Hizmetleri olarak Şekil 4-28'de gösterildiği gibi uygulanabilir.

Service Fabric'te, Grup ve hizmet olarak grupları dağıtma bir [Service Fabric uygulaması](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), paketleme ve dağıtım için orchestrator ya da küme biriminin olduğu. Bu hizmetler otonom olarak dağıtabilirsiniz, böylece bu nedenle, Service Fabric uygulaması bu otonom iş ve mantıksal bir mikro hizmet sınırı veya içerik sınırlanmış, de eşleştirilebilir.

## <a name="service-fabric-and-containers"></a>Service Fabric ve kapsayıcılar

Service Fabric'teki kapsayıcıları onaylamaz, Service Fabric kümesi dahilindeki kapsayıcı görüntülerinizi Hizmetleri'nde dağıtabilirsiniz. Şekil 4-29 gösterildiği gibi çoğu zaman yalnızca olmayacaktır hizmet başına bir kapsayıcı.

![Service Fabric uygulaması extern veritabanına erişen birden fazla kapsayıcılar çalıştırabilir ve tüm küme iş mikro hizmetlerin ayırt mantıksal sınır olacaktır](./media/image32.png)

**Şekil 4-29**. Çeşitli Hizmetleri (kapsayıcılar) Service Fabric ile mikro iş

Bununla birlikte, sözde "sepet" (mantıksal bir hizmetin parçası olarak birlikte dağıtılmış olması gereken iki kapsayıcı) de Service Fabric'te olası kapsayıcılardır. Önemli olan iş mikro hizmet birkaç cohesive öğeleri mantıksal sınırlarından olmasıdır. Çoğu durumda, bir tek veri modeli ile tek bir hizmet olabilir, ancak diğer bazı durumlarda, bazı fiziksel hizmetleri de olabilir.

Şekil 4-30 gösterildiği gibi hizmetleri ve kapsayıcıları Service Fabric uygulamasının Hizmetleri'nde karıştırabilirsiniz unutmayın.

![Hizmetleri ve kapsayıcıları hem aynı düğümde çalışan bir Service Fabric uygulaması.](./media/image33.png)

**Şekil 4-30**. Kapsayıcılar ve durum bilgisi olan hizmetler ile bir Service Fabric uygulaması için eşleştirilmiş iş mikro hizmet

Azure Service fabric'te kapsayıcı desteği hakkında daha fazla bilgi için bkz: [Service Fabric ve kapsayıcılar](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Durum bilgisiz ve durum bilgisi olan mikro hizmetler

Her mikro hizmet (mantıksal içerik sınırlanmış), daha önce bahsedildiği gibi etki alanı modeli (veri ve mantıksal) sahip olmanız gerekir. Durum bilgisi olmayan mikro hizmetler söz konusu olduğunda, veritabanları, SQL Server gibi ilişkisel seçenekleri veya Azure Cosmos DB veya MongoDB gibi NoSQL seçenekleri kullanan dış olacaktır.

Ancak hizmetler ayrıca veri mikro hizmet içinde bulunduğu anlamına gelir Service Fabric durum bilgisi olan olabilir. Bu veriler aynı sunucuda değil, ancak mikro hizmet işlemi, bellek içinde mevcut olmayabilir ve sabit sürücülerde kalıcı ve diğer düğümlere çoğaltılır. Şekil 4-30 farklı yaklaşımlar gösterir.

![Durum bilgisi olmayan hizmetler (Kalıcılık, veritabanı) durumunu mikro hizmet dışında tutulur. Durum bilgisi olan hizmetler durumları, mikro hizmet içinde tutulur.](./media/image34.png)

**Şekil 4-31**. Durum bilgisiz ve durum bilgisi olan mikro hizmetler

Durum bilgisi olmayan bir yaklaşım mükemmel geçerli olduğundan ve durum bilgisi olan mikro hizmetler geleneksel ve iyi bilinen desenleri için benzer bir yaklaşım olduğundan uygulamak daha kolaydır. Ancak, durum bilgisi olmayan mikro hizmetler, işlem ve veri kaynakları arasındaki gecikme süresini büyük oranda yansıtmaktadır. Bunlar ayrıca ek önbellek ve Kuyruklar ile performansı artırmak çalışırken daha fazla hareketli parça içerir. Sonuç, çok fazla katman karmaşık mimarilerin kalabilirsiniz emin olur.

Buna karşılık, [durum bilgisi olan mikro Hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) olmadığı için etki alanı mantığı ve verileri arasında herhangi bir gecikme Gelişmiş senaryolar excel. Yoğun veri işleme, geri oyun, bir hizmet olarak veritabanı sona erer ve tüm diğer düşük gecikmeli senaryolar daha hızlı erişim için yerel durumunu etkinleştirmek durum bilgisi olan hizmetler yararlanın.

Durum bilgisiz ve durum bilgisi olan hizmetler tamamlayıcıdır. Örneğin, durum bilgisi olan bir hizmet birden çok bölümdeki bölebilir doğru diyagramda, Şekil 4-31'de görebilirsiniz. Bu bölümler erişmek için bildiği her bölüm bölüm anahtara göre ele almak bir ağ geçidi hizmeti olarak davranan bir durum bilgisi olmayan hizmet gerekebilir.

Durum bilgisi olan hizmetler dezavantajları vardır. Bunlar, bir ölçek genişletme izin veren bir karmaşıklık düzeyi büyük oranda yansıtmaktadır. Genellikle dış veritabanı sistemleri tarafından uygulanan işlevleri veri çoğaltma gibi görevler için durum bilgisi olan mikro hizmetler ve bölümleme verilerde ele alınması gerekir. Burada bir orchestrator gibi alanlarından budur ancak [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) ile kendi [durum bilgisi olan reliable services](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) en çok yardımcı olabilir; geliştirme ve durum bilgisi olan yaşam döngüsü basitleştirerek mikro hizmetler kullanarak [Reliable Services API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) ve [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Gerçekleştiren deseni destekleyen ve hataya dayanıklılık ve iş mantığı ve verileri arasındaki gecikme süresini artırmak durum bilgisi olan hizmetler sağlayan diğer mikro hizmet çerçeveleri olan Microsoft [Orleans](https://github.com/dotnet/orleans), Microsoft Research ve [ Akka.NET](https://getakka.net/). Her iki çerçeveler kendi Docker desteği şu anda geliştirdiğinizi.

Docker kapsayıcıları durum bilgisiz kendilerini olduğunu unutmayın. Durum bilgisi olan hizmet uygulamak istiyorsanız, daha önce not ettiğiniz ek önerilerde bulunan ve daha üst düzey altyapılarından birini gerekir.

## <a name="using-azure-service-fabric-mesh"></a>Azure Service Fabric kafes kullanma 

Azure Service Fabric Mesh geliştiricilerin derleme ve iş açısından kritik uygulamalar herhangi bir altyapı yönetimine gerek kalmadan dağıtma sağlayan tam olarak yönetilen bir hizmettir. Service Fabric Mesh oluşturmak ve isteğe bağlı olarak ölçeklendirilebilen güvenli, dağıtılmış mikro hizmet uygulamaları çalıştırmak için kullanın. 

4-32, şekilde gösterildiği gibi Service Fabric Mesh üzerinde barındırılan uygulamaları çalıştırıp ölçeklendirmenize gerek kalmadan, destekleyen altyapı konusunda endişelenmenize gerek.

![Docker masaüstünde çalışan çok kapsayıcılı bir uygulama için Service Fabric Mesh Azure altyapı hakkında endişelenmeden dağıtılabilir.](media/image39.png)

**Şekil 4-32**. Service Fabric Mesh bir mikro hizmet/kapsayıcı uygulaması dağıtma

Güvenli Service Fabric Mesh makineler binlerce kümelerini oluşur. Tüm küme işlemlerini geliştiriciden gizlidir. Kapsayıcılarınızı karşıya yükleme ve ihtiyacınız olan kaynakları, kullanılabilirlik gereksinimlerini ve kaynak sınırları belirtin yeterlidir. Service Fabric Mesh uygulama dağıtımınız tarafından istenen altyapı otomatik olarak ayırır ve ayrıca uygulamalarınızın yüksek oranda kullanılabilir olduğundan emin olma altyapı hataları işleme. Altyapıya değil, uygulamanızın yanıt hızını ve sistem durumu hakkında önemli yeterlidir.

Daha fazla bilgi için bkz: [Service Fabric Mesh belgeleri](https://docs.microsoft.com/azure/service-fabric-mesh/).

## <a name="choosing-orchestrators-in-azure"></a>Azure'da düzenleyicileri seçme

Aşağıdaki tabloda, iş yükleri ve işletim sistemi odak bağlı olarak kullanmak için hangi orchestrator hakkında yönergeler sağlanır.

![Azure Kubernetes hizmeti, Windows, Linux daha olgun ve genellikle kapsayıcılara göre microsevices dağıtmak için kullanılır. Azure Service Fabric (hem küme hem de kafes) Windows, Linux, kapsayıcılar, mikro hizmetler düz işlemleri ve durum bilgisi olan hizmetler göre temel mikro hizmetlere yönelik yaygın olarak kullanılan daha olgun kullanılıyor.](media/image40.png)

**Şekil 4-33**. Orchestrator seçimde Azure Kılavuzu

>[!div class="step-by-step"]
>[Önceki](scalable-available-multi-container-microservice-applications.md)
>[İleri](../docker-application-development-process/index.md)