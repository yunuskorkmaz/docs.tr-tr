---
title: Azure Service Fabric kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Azure Service Fabric kullanma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: d65968e3d37f53cceee55120110ad4bb3c13d304
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-azure-service-fabric"></a>Azure Service Fabric kullanma

Microsoft'un geçiş stilde genellikle tek yapılı, kutusunu ürünler, hizmetler teslim etmek için teslim öğesinden gelen Azure Service Fabric çıkan. Derleme ve Azure SQL Database, Azure Cosmos DB, Azure Service Bus veya Cortana'nın arka uç gibi ölçekte büyük Hizmetleri işletim deneyimi Service Fabric şeklinde. Bu daha da fazla Hizmetleri benimsenen gibi platform zamanla gelişen. Önemlisi, Service Fabric yalnızca azure'da aynı zamanda tek başına Windows Server dağıtımlarında çalıştırmak gerekiyordu.

Service Fabric amacı takımlar mikro yaklaşımı kullanarak iş sorunlarını çözebilir böylece oluşturma ve bir hizmeti çalıştıran ve altyapı kaynaklarını verimli bir şekilde faydalanma sabit sorunları çözmeye yöneliktir.

Service Fabric mikro yaklaşım kullanan uygulamalar oluşturmanıza yardımcı olmak için iki geniş alanları sağlar:

-   Dağıtmak için sistem hizmetleri sağlayan bir platform ölçeklendirme, yükseltme, algılamak, başarısız hizmetlerini yeniden başlatın, hizmet konumu bulmak, durumunu yönetme ve durumunu izleyin. Bu sistem hizmetleri yürürlükte daha önce açıklanan mikro özelliklerinin çoğunu sağlar.

-   Programlama API'leri veya frameworks mikro uygulamalar oluşturmanıza yardımcı olmak için: [güvenilir aktörler ve güvenilir hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-choose-framework). Elbette, mikro hizmet oluşturmak için herhangi bir kod seçebilirsiniz ancak bu API'leri iş daha kolay hale ve bunlar daha ayrıntılı bir düzeyde platformuyla tümleştirebilirsiniz. Sistem durumu ve tanılama bilgileri veya alabilirsiniz bu şekilde güvenilir durum yönetimi yararlanabilir.

Service Fabric hizmetinizin nasıl oluşturulacağına göre bağımsızdır ve herhangi bir teknoloji kullanabilirsiniz. Ancak, daha kolay mikro oluşturmak için yerleşik programlama API'ler sağlar.

Şekil 4-26'da gösterildiği gibi oluşturun ve mikro Service Fabric basit işlemler veya Docker kapsayıcılar olarak çalıştırın. Kapsayıcı tabanlı mikro işlem tabanlı mikro aynı Service Fabric kümesi içinde ile karışık mümkündür.

![](./media/image30.png)

**Şekil 4-26**. Mikro işlemler veya Azure Service Fabric kapsayıcılarında olarak dağıtma

Linux ve Windows konaklarda tabanlı Service Fabric kümeleri Docker Linux kapsayıcıları ve Windows kapsayıcıları, sırasıyla çalıştırabilirsiniz.

Azure Service Fabric kapsayıcıları desteği hakkında güncel bilgiler için bkz: [Service Fabric ve kapsayıcıları](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

Service Fabric olan bir platform iyi bir örneği burada bir farklı mantıksal mimarisine (iş mikro veya sınırlanmış bağlamları) de tanıtılan fiziksel uygulama tanımlayabilirsiniz [fiziksel ve mantıksal mimarisi Mimari](#logical-architecture-versus-physical-architecture) bölümü. Örneğin, uygulamanız [durum bilgisi olan güvenilir hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction) içinde [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-overview), bölümde sunulan [durum bilgisi olan mikro karşı Stateless](#stateless-versus-stateful-microservices) Daha sonra birden çok fiziksel hizmetleriyle iş mikro hizmet kavramını olabilir.

Şekil 4-27 ve bir doku durum bilgisi olan güvenilir hizmeti uygularken mantıksal/iş mikro açısından, düşünmeye olarak gösterilen, genellikle iki katmanı Hizmetleri uygulamak gerekir. İlk (her bölüm bir durum bilgisi olan bir hizmettir) birden çok bölüm işleyen arka uç durum bilgisi olan güvenilir hizmetidir. , Ön uç hizmeti veya ağ geçidi hizmeti, Yönlendirme ve veri toplama birden çok bölüm veya durum bilgisi olan hizmet örnekleri sorumlu saniyedir. Bu ağ geçidi hizmeti de yeniden deneme döngüleri ile arka uç hizmetine erişim istemci-tarafı iletişim işler.
Özel hizmet veya giden kutusu Service Fabric da kullanabilirsiniz alternatevely uygularsanız bir ağ geçidi hizmeti bilinir [Ters Proxy Hizmeti](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy).

![](./media/image31.png)

**Şekil 4-27**. İş mikro birkaç durum bilgisi olan hizmet örneği ve ön uç özel ağ geçidi ile

Herhangi bir durumda, hizmet doku durum bilgisi olan güvenilir hizmetler kullandığınızda, ayrıca, genellikle birden çok fiziksel hizmetlerinden oluşur bir mantıksal veya iş mikro hizmet (ilişkisindeki bağlamı) vardır. Her bunları, ağ geçidi hizmeti ve bölüm hizmet olarak ASP.NET Web API Hizmetleri, Şekil 4-26'da gösterildiği gibi uygulanabilir.

Service Fabric grup ve grupları Hizmetleri dağıtma bir [Service Fabric uygulaması](https://docs.microsoft.com/azure/service-fabric/service-fabric-application-model), birim paketleme ve dağıtım orchestrator veya kümesine ait değil. Bu hizmetler sınırlarına dağıtabilirsiniz şekilde bu nedenle, Service Fabric uygulaması bu otonom iş ve mantıksal mikro hizmet sınır veya sınırlanmış bağlam de eşleştirilebilir.

## <a name="service-fabric-and-containers"></a>Service Fabric ve kapsayıcıları

Service Fabric kapsayıcılara göre kapsayıcı görüntüler Service Fabric kümesi içinde Hizmetleri'nde de dağıtabilirsiniz. Şekil 4-28 gösterildiği gibi çoğu zaman yalnızca olacaktır hizmeti başına bir kapsayıcı.

![](./media/image32.png)

**Şekil 4-28**. İş mikro Service Fabric olarak birkaç hizmetleriyle (kapsayıcı)

Ancak, sözde "sepet" (birlikte mantıksal bir hizmetin parçası olarak dağıtılması gereken iki kapsayıcı) de Service Fabric olası kapsayıcılardır. Önemli şey iş mikro hizmet birkaç bağlı öğeleri mantıksal sınırlarından olmasıdır. Çoğu durumda, bir tek veri modeli tek bir hizmetle olabilir, ancak bazı diğer durumlarda fiziksel birkaç hizmetleri de sahip olabilir.

Mid-2017 itibariyle, Service Fabric BT güvenilir durum bilgisi olan hizmetler kapsayıcılarında dağıtamazsınız — yalnızca durum bilgisi olmayan hizmetler ve aktör Hizmetleri kapsayıcılarında dağıtabilirsiniz. Ancak Şekil 4-29 gösterildiği gibi işlemleri Hizmetleri'nde ve aynı Service Fabric uygulaması kapsayıcılarında Hizmetleri'nde karıştırabilirsiniz unutmayın.

![](./media/image33.png)

**Şekil 4-29**. Bir Service Fabric uygulaması kapsayıcıları ve durum bilgisi olan hizmetler ile eşlenmiş iş mikro hizmet

Azure Service Fabric kapsayıcı desteği hakkında daha fazla bilgi için bkz: [Service Fabric ve kapsayıcıları](https://docs.microsoft.com/azure/service-fabric/service-fabric-containers-overview).

## <a name="stateless-versus-stateful-microservices"></a>Durum bilgisiz durum bilgisi olan mikro karşılaştırması

Daha önce belirtildiği gibi her mikro hizmet (mantıksal sınırlanmış içerik), etki alanı modeli (verileri ve mantığı) sahip olmanız gerekir. Durum bilgisiz mikro söz konusu olduğunda, veritabanlarını SQL Server gibi ilişkisel seçenekleri ya da MongoDB ya da Azure Cosmos DB gibi NoSQL seçenekleri kullanan dış olacaktır.

Ancak Hizmetleri kendileri de verileri mikro hizmet içinde bulunduğu anlamına gelir Service Fabric durum bilgisi olan olabilir. Bu veriler, yalnızca aynı sunucuda ancak mikro hizmet işleminde bellek içinde mevcut olabilecek ve sabit sürücülerde kalıcı ve diğer düğümlere çoğaltılan. Şekil 4-30 farklı yaklaşımlara gösterir.

![](./media/image34.png)

**Şekil 4-30**. Durum bilgisiz durum bilgisi olan mikro karşılaştırması

Durum bilgisi olmayan bir yaklaşım mükemmel geçerli değil ve bir yaklaşım için geleneksel ve bilinen desenleri benzer olduğundan durum bilgisi olan mikro uygulamak daha kolay olur. Ancak durum bilgisiz mikro zorunlu tuttukları işlem ve veri kaynakları arasındaki gecikme süresi. Bunlar ayrıca ek önbellek ve Kuyruklar ile performansını artırmak çalışırken daha hareketli parça içerir. Sonuç, çok fazla katmanlarına sahip karmaşık mimarileri ile düşebilir emin olur.

Buna karşılık, [durum bilgisi olan mikro](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) Gelişmiş senaryolarda, etki alanı mantığı ve verileri arasında bir gecikme olduğundan excel. Bir hizmet olarak veritabanlarını geri oyun sona erdikten yoğun veri işleme ve tüm diğer düşük gecikmeli senaryolar daha hızlı erişim için yerel durumunu etkinleştir durum bilgisi olan hizmetlerinden yararlanabilirsiniz.

Durum bilgisiz ve durum bilgisi olan Tamamlayıcı hizmetleridir. Örneği için bir durum bilgisi olan hizmet birden çok bölüme bölebilir sağ şemada Şekil 4-30 de görebilirsiniz. Bu bölümler erişmek için bölüm anahtara göre her bir bölümü adres bildiği bir ağ geçidi hizmeti olarak davranan bir durum bilgisiz hizmet gerekebilir.

Durum bilgisi olan hizmetler sakıncaları vardır. Bunlar, bir ölçek genişletme olanak tanıyan karmaşıklık düzeyi zorunlu tuttukları. Genellikle dış veritabanı sistemleri tarafından uygulanan işlevleri veri çoğaltma gibi görevler için durum bilgisi olan mikro ve veri bölümlendirme arasında ele alınması gerekir. Ancak, bu bir orchestrator oluşturulacağı yeri alanlardan biridir [Azure Service Fabric](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-platform-architecture) ile kendi [durum bilgisi olan güvenilir hizmetler](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-services-introduction#when-to-use-reliable-services-apis) en yardımcı olabilir — geliştirme ve durum bilgisi olan yaşam döngüsü basitleştirme tarafından mikro kullanarak [güvenilir Hizmetleri API](https://docs.microsoft.com/azure/service-fabric/service-fabric-work-with-reliable-collections) ve [Reliable Actors](https://docs.microsoft.com/azure/service-fabric/service-fabric-reliable-actors-introduction).

Aktör deseni destekleyen ve hataya dayanıklılık ve iş mantığı ve verileri arasında gecikme geliştirmek durum bilgisi olan hizmetler izin diğer mikro hizmet çerçeveler Microsoft, [Orleans](https://github.com/dotnet/orleans)Microsoft Research ve [ Akka.NET](https://getakka.net/). Her iki çerçeveleri şu anda Docker için destek geliştirme.

Docker kapsayıcıları durum bilgisiz kendilerini olduğuna dikkat edin. Durum bilgisi olan hizmet uygulamak istiyorsanız, daha önce not ettiğiniz ek önerilerde bulunan ve üst düzey çerçeveleri biri gerekir. 

>[!div class="step-by-step"]
[Önceki] (scalable-available-multi-container-microservice-applications.md) [sonraki] (.. /docker-Application-Development-Process/index.MD)
