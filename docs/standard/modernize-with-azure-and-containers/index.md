---
title: Mevcut .NET uygulamaları ile Azure Bulut ve Windows kapsayıcıları modernleştirin (2 sürümü)
description: Kaldırma ve kaydırma ve bu e-kitap kapsayıcılarla ve Azure bulut için mevcut uygulamaları modernize öğrenin.
ms.date: 04/28/2018
ms.openlocfilehash: 79e06c64867a7e1bb6c5d7da718886a713cb3c4c
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834007"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Azure Bulutu ve Windows kapsayıcıları ile mevcut .NET uygulamalarını modernleştirme (2 sürümü)

![Görüntü Modernleştirin .NET uygulamaları Kılavuzu'nun kapsar.](./media/index/web-application-guide-cover-image.png)

TARAFINDAN YAYIMLANAN  
Microsoft Press ve Microsoft Devdiv'e  
Bölümler, Microsoft Corporation'ın  
One Microsoft Way  
Redmond, Washington 98052-6399  

Telif Hakkı © 2018 Microsoft Corporation  

Tüm hakları saklıdır. Bu kitap içeriğini işlevinin hiçbir bölümü herhangi bir biçimdeki veya yayımcı yazılı izni olmadan herhangi bir yöntemle yeniden oluşturulabilir.

Bu kitap gibi bir elektronik kitap (e-kitap) Microsoft'ta birden çok kanal aracılığıyla biçiminde ücretsiz kullanılabilir <https://dot.net/architecture>.

Bu kitap, e-posta ile ilgili sorularınız varsa [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

Bu kitap sağlanan "olarak-olduğunu" ve yazarın görünümleri ve düşünceleri son derece ifade eder. Görünümler, fikrini ve URL ve diğer Internet Web sitesi referansları da dahil olmak üzere bu kitap, ifade bilgiler değiştirilebilir.

Burada açıklanan bazı örnekler yalnızca çizim için sağlanmıştır ve bu kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya çıkarılmamalıdır.

Microsoft ve adresinde listelenmiş ticari <https://www.microsoft.com> "Ticari" Web sayfasında Microsoft şirketler grubunun ticari markalarıdır. Diğer tüm işaretleri sahiplerinin özelliği var.

Yazar:
> **Cesar de la Torre**, üst düzey PM, .NET ürün ekibi, Microsoft Corp.

Katılımcılar ve gözden geçirenler:
> **Scott Hunter**, .NET ekibi, Microsoft iş ortağı Direktörü PM  
> **Paul Yuknewicz**, baş PM Yöneticisi, Microsoft Visual Studio Araçları ekibi  
> **Lisa Guthrie**, üst düzey PM, Visual Studio Araçları takım, Microsoft  
> **Ankit Asthana**, baş PM Yöneticisi, Microsoft .NET ekibi  
> **Unai Zorrilla**, geliştirici sağlama, düz kavramları  
> **Javier Valero**, Enformasyon Müdürü Grupo çözümleri işletim  

## <a name="introduction"></a>Giriş

Web uygulamalarınız veya hizmetleriniz modernleştirin ve bunları buluta taşımanıza karar verdiğinizde, uygulamalarınızı tam olarak yeniden oluşturma olması gerekmez. Mikro hizmetler gibi gelişmiş bir yaklaşım kullanarak bir uygulama bütçeden her zaman Maliyet ve zaman kısıtlamaları nedeniyle bir seçenek değildir. Uygulama türüne bağlı olarak, bir uygulama bütçeden de gerekli olmayabilir. Kuruluşunuzun bulut geçişi stratejisi maliyet açısından uygunluğunu iyileştirmek için işletmenizin ihtiyaçlarını ve uygulamalarınızın gereksinimlerini göz önünde bulundurmanız önemlidir. Belirlemeniz gerekir:

- Hangi uygulamaların bir dönüştürme gerekli veya yeniden oluşturma.

- Hangi uygulamaların yalnızca kısmen modernleştirdiğini gerekir.

- Hangi uygulamaların, "lift- and -shift" doğrudan buluta.

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz bir iş yükünü önemli ölçüde uygulamanın kodunu değiştirmeden daha yeni veya daha modern bir ortama taşıma eylemi anlamı öncelikle var olan Microsoft .NET Framework web veya hizmet odaklı uygulamalar, ilk modernizasyonu üzerinde odaklanır. ve temel mimarisi. 

Bu kılavuz, ayrıca uygulamalarınızı buluta taşıma ve kısmen belirli bir dizi yeni teknolojileri ve Windows kapsayıcıları ve ilgili işlem-azure'da Windows kapsayıcılarını destekleyen platformlar gibi bir yaklaşım kullanarak uygulamaları modernleştirme avantajlarını vurgular.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Yolu için var olan .NET uygulamalarını buluta

Kuruluşlar genellikle çevikliğini ve müşterilerin uygulamaları için aldıkları hızı için buluta taşımak için seçin. Genellikle şirket içi sunucularını ayarlamak için geçen haftaya göre dakikalar içinde bulutta binlerce sunucuya (VM) ayarlayabilirsiniz.

Geçiş için bir tek, BT'ye stratejisi hiç uygulamaları bulutta. Sizin için doğru geçiş stratejisi, kuruluşunuzun gereksinimlerine ve öncelikleri ve geçirmekte olduğunuz uygulama türüne bağlıdır. Tüm uygulamalar bir hizmet olarak platform taşıma yatırım garanti ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) modeli veya geliştirme bir [bulutta yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) uygulama modeli. Çoğu durumda, iş gereksinimlerinize göre buluta taşıma varlıklarınızı yatırım yapmaya artımlı ya da aşamalı bir yaklaşım alabilir.

En iyi uzun dönemli çevikliğini ve kuruluş için bir değer ile modern uygulamalar için yatırım gelen yararlanabilecek *bulutta yerel* uygulama mimarileri. Ancak, eski varlıklar veya var uygulamalar önemli avantajlardan faydalanmak için buluta taşıma sırasında en az zaman ve para (hiçbir bütçeden veya kod değişiklikleri) harcamaya anahtardır.

Şekil 1-1, artımlı aşamalı olarak var olan .NET uygulamalarını buluta taşıdığınızda, uygulayabileceğiniz olası yolları gösterir.

 ![Mevcut .NET uygulamaları ve Hizmetleri için modernizasyonu yolları](./media/image1-1.png)

> **Şekil 1-1**. Mevcut .NET uygulamaları ve Hizmetleri için modernizasyonu yolları

Her geçiş yaklaşımı farklı avantajları ve bunu kullanma nedenleri vardır. Uygulamaları buluta taşımayı ya da belirli bileşenlerin birden çok yaklaşımın seçin, tek bir yaklaşım tercih edebilirsiniz. Tek tek uygulamalar için tek bir yaklaşım veya Kapasite Olgunlaştırma durumda değilsiniz. Örneğin, ortak karma bir yaklaşım belirli şirket içi bileşenlerin yanı sıra diğer bileşenleri bulutta gerekir.

Her uygulama olgunluk seviyesi için kısa bir açıklama ve tanımı aşağıda verilmiştir:

**Düzey 1: Bulut altyapısını kullanıma hazır** uygulamalar: Bu geçiş yaklaşımı, yalnızca geçirme veya bir hizmet olarak altyapı için geçerli şirket içi uygulamalarınızı yeniden barındırma ([Iaas](https://azure.microsoft.com/overview/what-is-iaas/)) platform. Uygulamalarınızı önce olarak neredeyse aynı bileşim sahip, ancak artık, bulutta VM dağıtın.
Basit bu geçiş türü genellikle sektördeki "Kaldırma ve kaydırma." olarak bilinir

**2. düzey: Bulut için optimize edilmiş** uygulamalar: Bu düzeyde ve işleve bölmenize veya önemli kod değiştirmeyi olmadan yine de kapsayıcılar ve ek bulutta yönetilen hizmetler gibi modern teknolojiler ile bulutta uygulamanızın çalışmasını ek avantajlar elde edebilirsiniz. Uygulamalarınızı Kurumsal geliştirme işlemleri (DevOps) işlemlerinizi düzelterek daha hızlı gönderin çevikliğini artırmak. Bu Windows kapsayıcıları, Docker altyapısını temel alan gibi teknolojileri kullanarak elde edin. Birden çok aşamalı olarak dağıttığınızda, uygulama bağımlılıkları nedeniyle uyuşmazlıkları kapsayıcıları kaldırın. Bu Kapasite Olgunlaştırma model içinde ek kullanırken PaaS Hizmetleri bulutta yönetilen veritabanları, ilgili bir hizmeti izleme ve sürekli tümleştirme/sürekli dağıtım (CI/CD) işlem hatları önbelleğe veya Iaas kapsayıcılarında dağıtabilirsiniz.

Üçüncü düzeyini vade, nihai amacıyla bulutta olmakla birlikte birçok uygulama ve değil odaklandığı bu kılavuzun için isteğe bağlıdır:

**3. düzey: Bulutta yerel** uygulamalar: Bu geçiş yaklaşımı, genellikle iş gereksinimlerini ve görev açısından kritik uygulamalarınızı modernleştirme hedefler tarafından yönetilir. Bu düzeyde PaaS hizmetlerini PaaS bilgi işlem platformları için uygulamalarınızı taşımak için kullanın. Uygulamanız [bulutta yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) uygulamalar ve mikro hizmetler mimarisi ile uzun süreli çevikliği uygulamalar geliştiren ve yeni sınırları ölçeklendirmek için. Bu tür bir modernizasyonu, genellikle özel bulut için tasarlama gerektirir. Özellikle, bulutta çalışan uygulama ve mikro hizmet tabanlı modeller için taşıdığınızda yeni kod genellikle yazılmalıdır. Bu yaklaşım, tek parça ve şirket içi uygulama ortamınızda elde etmek zor avantajlara yardımcı olabilir.

Tablo 1-1, başlıca avantajları ve her geçiş veya modernizasyonu yaklaşımını seçme nedenleri açıklanmaktadır.

| **Bulut altyapısı için hazır** <br /> *Lift- and -shift* | **Bulut için iyileştirilmiş** <br /> *Modernize* | **Bulutta yerel** <br /> *Yeniden oluşturma modernleştirin ve yeniden yazma* |
|---|---|---|
| **Uygulamanın işlem hedefi** |
| Azure'da sanal makineler için dağıtılan uygulamalar | Azure App Service, Azure Container örneği (ACI), sanal makineleri, kapsayıcıları veya AKS (Azure Kubernetes hizmeti) ile dağıtılan tek parça veya N katmanlı uygulamalar | Kapsayıcılı mikro hizmet tabanlı Azure işlevleri, sunucusuz mikro hizmetler ve/veya Azure Kubernetes Service (AKS). |
| **Verileri hedefi** |
| SQL veya bir VM üzerinde herhangi bir ilişkisel veritabanı | Azure SQL veritabanı yönetilen örneğine veya başka bir yönetilen veritabanı bulutta. | Azure SQL veritabanı, Azure Cosmos DB veya başka bir yönetilen veritabanı bulut tabanlı bir mikro hizmet, başına fined dilimi veritabanı |
| **Avantajlar**|
| <li>Hiçbir bütçeden, yeni kodu <li> Hızlı geçiş için en az çaba <li> Azure'da desteklenen en küçük ortak paydası <li> Temel kullanılabilirliği garanti eder <li> Buluta taşıdıktan sonra bunu daha da fazla modernleştirin kolaydır | <li> Hiçbir bütçeden <li> Çok az kod/yapılandırma değişiklikleri <li> Geliştirilmiş dağıtım ve DevOps çevikliği kapsayıcıları nedeniyle serbest bırakmak için <li> Yoğunluğu ve dağıtım maliyetlerini düşürün <li> Uygulamalar ve bağımlılıklar için taşınabilirlik <li> Ana hedef esneklik: Yaklaşım PaaS veya Iaas | <li> Mimarı bulut için buluttan en iyi avantajlarından yararlanın, ancak yeni kodu gereklidir <li> Mikro hizmetler bulutta yerel yaklaşımları <li> Modern iş açısından kritik uygulamalar, dayanıklı bulut ölçeklenebilir <li> Tam olarak yönetilen hizmetler <li> Ölçek için en iyi duruma getirilmiş <li> Alt sistemi tarafından otonom Çeviklik için en iyi duruma getirilmiş <li> Dağıtım ve DevOps üzerinde oluşturulmuş |
| **Zorlukları** |
| <li> Shift gider işletim ya da veri merkezleri kapatma dışında daha küçük bulut değer <li> Az yönetilir: Hiçbir işletim sistemi veya bir ara yazılım düzeltme eki uygulama; Terraform, Spinnaker veya Puppet gibi altyapı çözümlerini kullanıyor olabilir | <li> Kapsayıcılı hale getirmek geliştiricilerin ve BT işlemleri için öğrenme eğrisini içinde ek bir adım olduğunu <li> DevOps ve CI/CD işlem hatları 'şart' Bu yaklaşım genellikle olur. Aksi takdirde şu anda kuruluşun kültüründeki varsa, ek bir zorluğu olması olabilir| <li> Bulutta yerel uygulamalar ve mikro hizmet mimarileri için rearchitecture gerektirir ve genellikle yeniden düzenleme ya da modernleştirme olduğunda yeniden yazma önemli kod (daha fazla zaman ve bütçe) gerektirir <li> DevOps ve CI/CD işlem hatları 'şart' Bu yaklaşım genellikle olur. Aksi takdirde şu anda kuruluşun kültüründeki varsa, ek bir zorluğu olması olabilir|
> **Tablo 1-1.** Avantajları ve zorluklarının modernizasyonu yol mevcut .NET uygulamaları ve Hizmetleri

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Temel teknolojileri ve olgunluk seviyesi ile mimarileri

.NET framework uygulamaları, başlangıçta geç 2001'de yayımlanan sürüm 1.0, .NET Framework ile başlatıldı. Ardından, şirketlerin taşınır daha yeni sürümleri (örneğin, 2.0, 3.5 ve .NET 4.x). Söz konusu uygulamaların çoğu Windows Server ve Internet Information Server (IIS) üzerinde çalışan ve SQL Server, Oracle, MySQL veya diğer bir RDBMS gibi bir ilişkisel veritabanı kullanılır.

Çoğu mevcut .NET uygulamaları günümüzde .NET Framework tabanlı 4.x, ya da .NET Framework 3.5 ve ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, Windows Communication Foundation (WCF), ASP.NET SignalR ve ASP.NET Web sayfaları gibi web çerçeveleri kullanın . Bu, Windows üzerinde .NET Framework teknolojilerini bağımlı kurdu. Bu bağımlılık, eski uygulamaları yalnızca geçirdiğiniz ve uygulama altyapınızın küçük değişiklikler yapmak istediğiniz göz önünde bulundurmanız önemlidir.

Şekil 1-2 birincil teknolojileri ve mimari stilleri düzeylerinin her biri üç bulut olgunluk sırasında kullanılan gösterir:

![Web uygulamaları mevcut .NET modernleştirilmesi için her olgunluk seviyesi için birincil teknolojileri](./media/image1-2.png)

> **Şekil 1-2.** Web uygulamaları mevcut .NET modernleştirilmesi için her olgunluk seviyesi için birincil teknolojileri

Şekil 1-2, en sık karşılaşılan senaryolardan vurgular, ancak birçok karma ve karma çeşitlemeleri mimariye geldiğinde mümkün olur. Örneğin, yalnızca mevcut web apps'te tek parçalı mimariyi için aynı zamanda hizmet yönlendirmesi, N katmanı ve diğer mimari stili Çeşitlemeler Kapasite Olgunlaştırma Model uygulayın. Daha yüksek odak veya bir ya da başka bir mimari türü ve ilgili teknolojiler yüzdesi, uygulamalarınızın genel olgunluk düzeyini belirler.

Her olgunluk seviyesi modernizasyonu sürecinde aşağıdaki anahtar teknolojileri ve yaklaşım ile ilişkilendirilir:

- **Bulut altyapısını kullanıma hazır** (rehost veya kaldırmak ve kaydırmak temel): İlk adım, birçok kuruluş yalnızca hızlı bir şekilde buluta geçiş stratejisi yürütmek istiyorsunuz. Bu durumda, uygulamaları yeniden barındırılan. Çoğu yeniden barındırma kullanılarak otomatikleştirilebilir [Azure geçişi](https://aka.ms/azuremigrate), Kılavuzu, Öngörüler ve Azure'a geçiş ile yardımcı olmak için gereken mekanizmalar sağlayan bir hizmet gibi bulut araçları temel [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)ve [Azure veritabanı geçiş hizmeti](https://azure.microsoft.com/campaigns/database-migration/). Böylece, eski uygulamaları buluta taşıdığınızda altyapı ayrıntılarını varlıklarınız hakkında bilgi edinebilirsiniz el ile yeniden barındırma yukarı de ayarlayabilirsiniz. Örneğin, vm'lere uygulamalarınızı Azure'da biraz ile taşıyabilirsiniz yalnızca küçük bir yapılandırma değişiklikleri ile büyük olasılıkla değiştirme. Bu durumda özellikle Azure'da sanal ağlar oluşturma, bir şirket içi ortama benzer ağdır.

- **Bulut için iyileştirilmiş** (yönetilen Hizmetleri ile Windows kapsayıcıları): Bu model, uygulama temel mimarisini değiştirmeden buluttan önemli bazı avantajlar elde etmek için birkaç önemli dağıtımi iyileştirmeleri yapma konusunda ' dir. Burada temel adım eklemektir [Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) var olan .NET Framework uygulamalarınız için desteği. Bu önemli adım (kapsayıcı) açık genel lift- and -shift çaba, bu nedenle kodu bitişik olmasını gerektirmez. Araçları gibi kullanabileceğiniz [Image2Docker](https://github.com/docker/communitytools-image2docker-win) ya da Visual Studio için kendi araçlarıyla [Docker](https://www.docker.com/). Visual Studio, ASP.NET uygulamaları ve Windows kapsayıcı görüntüleri için akıllı varsayılanlar otomatik olarak seçer. Bu araçlar, hızlı bir iç döngü hem Azure'a kapsayıcıları almak için hızlı bir yolunu sunar. Birden çok ortama dağıtırken çevikliğinizi geliştirildi. Ardından, üretim aşamasına geçmeniz için Windows kapsayıcıları için dağıtabileceğiniz [kapsayıcılar için Azure Web App](https://azure.microsoft.com/services/app-service/containers/), [Azure Container Instances'a (ACI)](https://azure.microsoft.com/services/container-instances/)ve Windows Server 2016 ve isterseniz kapsayıcılar ile Azure Vm'leri bir Iaas yaklaşımını. Daha karmaşık çok kapsayıcılı uygulamalar gibi düzenleyicileri kullanarak göz önünde bulundurun [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/). 

Bu ilk modernizasyonu sırasında da varlıklar gibi araçlarla izleme buluttan ekleyebilirsiniz [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); CI/CD işlem hatları ile uygulama yaşam döngülerine için [Azure DevOps Hizmetleri](https://azure.microsoft.com/services/devops/); ve Azure'da kullanılabilen pek çok daha fazla veri kaynağı hizmeti. Başlangıçta geleneksel kullanılarak geliştirilmiş bir tek parçalı bir web uygulaması örneği için değiştirebileceğiniz [ASP.NET Web Forms](https://www.asp.net/web-forms) veya [ASP.NET MVC](https://www.asp.net/mvc), ancak artık Windows kapsayıcıları kullanarak dağıtmadan. Windows kapsayıcıları kullandığınızda, ayrıca verilerinizi bir veritabanına geçirmeden [Azure SQL veritabanı yönetilen örneği](https://docs.microsoft.com/azure/sql-database/), uygulamanızın temel mimarisini değiştirmeden tüm.

- **Bulutta yerel**: Sunulduğu şekilde tasarlama hakkında almalısınız [bulutta yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) olabilir farklı mikro hizmetleri üzerinde çalışan birden çok bağımsız geliştirme ekipleri ile büyük ve karmaşık uygulamaları emit hedeflerken uygulamalar geliştirilen ve otonom olarak dağıtılabilir. Ayrıca, granularized ve bağımsız ölçeklenebilirlik nedeniyle mikro hizmet başına. Bu mimari yaklaşım çok önemli güçlükler ve karmaşıklık ancak büyük ölçüde bulut PaaS kullanılarak basitleştirilebilir ve düzenleyicileri gibi [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (yönetilen Kubernetes) ve [Azure işlevleri](https://azure.microsoft.com/services/functions/) sunucusuz bir yaklaşım için. Bu yaklaşımların (örneğin, mikro hizmetler ve sunucusuz) genellikle, yeni kod yazmak ve bulut için Mimari gerektirir — belirli bir PaaS platformlar için uyarlanmış bir kod ya da, mikro hizmetler gibi belirli mimarilerin hedeflenmesini ile eşleşen kod.

Şekil 1-3 iç teknolojileri her olgunluk seviyesi için kullanabileceğiniz gösterilmektedir:

![Her modernizasyonu olgunluk seviyesi için iç teknolojileri](./media/image1-3.png)

> **Şekil 1-3.** Her modernizasyonu olgunluk seviyesi için iç teknolojileri

## <a name="lift-and-shift-scenario"></a>Lift- and -shift senaryosu

Lift and shift ile geçiş işleminde, uygulama senaryolarınız lift and shift ile birçok farklı çeşitleri kullanabileceğiniz aklınızda bulundurun. Yalnızca uygulamanızı yeniden barındırma, Şekil 1-Vm'leri buluta yalnızca uygulamanızın ve veritabanı sunucunuz için kullandığınız 4, gösterilene benzer bir senaryo gerekebilir.

![Bulutta saf bir Iaas senaryosu örneği](./media/image1-4.png)

> **Şekil 1-4**. Bulutta saf bir Iaas senaryosu örneği

## <a name="modernization-scenarios"></a>Modernizasyonu senaryoları

Modernizasyonu senaryoları için öğeleri yalnızca o olgunluk düzeyden kullanan saf bulut için iyileştirilmiş bir uygulama olabilir. Veya Bulut altyapısını kullanıma hazır ve bulut için iyileştirilmiş diğer öğelerden bazı öğeleri ile bir ara durum uygulamanın olabilir (bir "çekme ve Seç" ya da karma modeli), Şekil 1-5'te ister.

!["Çekme ve Seç" içeren örnek senaryo, Iaas, DevOps ve kapsayıcı varlıkları üzerinde daha fazla veritabanı](./media/image1-5.png)

> **Şekil 1-5.** "Çekme ve Seç" içeren örnek senaryo, Iaas, DevOps ve kapsayıcı varlıkları üzerinde daha fazla veritabanı

Ardından, geçirmek, çok sayıda mevcut .NET Framework uygulamaları için ideal senaryo olarak az şey yapmanızı önemli avantajlarından yararlanabilmek için bir bulut için iyileştirilmiş uygulamaya geçirebilirsiniz. Bu yaklaşım Ayrıca, buluta özgü için olası bir gelecekteki gelişimine ayarlar. Şekil 1-6 bir örnek gösterilmektedir.

![Windows kapsayıcıları ve yönetilen Hizmetleri ile örnek uygulamaları bulut için iyileştirilmiş senaryo](./media/image1-6.png)

> **Şekil 1-6.** Windows kapsayıcıları ve yönetilen Hizmetleri ile örnek uygulamaları bulut için iyileştirilmiş senaryo

Daha da ileri giderek, belirli senaryolar için birkaç mikro hizmetler ekleyerek mevcut bulut için iyileştirilmiş uygulamanızı genişletebilirsiniz. Bu kısmen odaklandığı mevcut kılavuzunun değil bulutta yerel modelinin düzeyine taşıyabilir.

## <a name="what-this-guide-does-not-cover"></a>Ne bu kılavuzda ele alınmamaktadır

Bu kılavuz, Şekil 1-7'de gösterildiği gibi belirli bir alt kümesini örnek senaryoları kapsar. Bu kılavuz yalnızca lift- and -shift senaryoları ve sonuç olarak, Bulutla optimize edilmiş model üzerinde odaklanır. Bulut için iyileştirilmiş modelinde izleme gibi ek bileşenler yanı sıra Windows kapsayıcıları kullanarak bir .NET Framework uygulamasına modernleştirdiğini ve CI/CD işlem hatları. Her dağıtım, bulut uygulamalarını daha hızlı ve Çevik bir biçimde temel bileşenidir.

![Buluta özgü bu kılavuzda ele alınmamaktadır](./media/image1-7.png)

> **Şekil 1-7.** Buluta özgü bu kılavuzda ele alınmamaktadır

Bu kılavuzun odağı özeldir. Lift and shift mevcut .NET uygulamalarınızın ile bir işleve bölmenize olmadan ve kod değişikliğine gerek olmadan elde etmek için uygulayabileceğiniz yol gösterir. Sonuç olarak, bu, uygulamanızın nasıl yapılacağını gösterir Bulutla optimize edilmiş.

Bu kılavuzda bir mikro hizmet mimarisi için geliştirilebilen nasıl gibi bulutta yerel uygulamalar oluşturmak nasıl göstermez. E-kitabı, uygulamalarınızı yeniden oluşturma veya üzerinde mikro hizmet tabanlı yeni uygulamalar oluşturmak için bkz. [.NET mikro Hizmetleri: Kapsayıcılı .NET uygulamaları mimarisi](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Ek kaynaklar

- **Docker uygulaması yaşam döngüsü Microsoft Platformu ve araçları ile kapsayıcılı hale** (indirilebilir e-kitap) \
  <https://aka.ms/dockerlifecycleebook>

- **.NET Mikro Hizmetleri: Kapsayıcılı .NET uygulamaları mimarisi** (indirilebilir e-kitap) \
  <https://aka.ms/microservicesebook>

- **ASP.NET Core ve Azure ile modern web uygulamaları oluşturmaya** (indirilebilir e-kitap) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Bu kılavuzda kullanan

Bu kılavuzda, geliştiricilere ve varolan ASP.NET web uygulamaları veya .NET Framework'ü sevkiyat ve uygulamaları serbest Gelişmiş Çeviklik için temel WCF hizmetlerini modernleştirin isteyen çözüm mimarları için yazılmıştır.

Bir kurumsal Mimarı veya Geliştirme lideri/Windows kapsayıcıları kullanarak ve buluta kullanırken dağıtarak alabilirsiniz avantajları genel bir bakış yalnızca isteyen yönetmenin gibi teknik karar yer alan bir oluşturucu yoksa, ayrıca bu kılavuzda yararlı olabilir Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Bu kılavuz nasıl kullanılır?

Bu kılavuzda ele "neden"-neden alın, uygulamalarınızı buluta taşıdığınızda Windows kapsayıcıları kullanarak belirli avantajlar yanı sıra mevcut uygulamalarınızı modernize etme isteyebilirsiniz. Kılavuzun ilk birkaç bölüm içeriğinde, mimarlar ve genel bir bakış isteyen, ancak kullanan uygulama ve teknik, adım adım ayrıntıları gerekmez teknik karar verenler için tasarlanmıştır.

Bu kılavuzun önceki bölümde belirli dağıtım senaryosunda, odaklanan birden çok izlenecek yollar sunar. Bu kılavuz, senaryoları özetlemek ve faydaları vurgulamak için daha kısa sürümlerini izlenecek yollar sunar. Tam Kılavuzlar kurulumu ve uygulama ayrıntılarına detaya ve bir dizi yayımlanan [wiki gönderileri](https://github.com/dotnet-architecture/eShopModernizing/wiki) aynı genel [GitHub deposunu](https://github.com/dotnet-architecture/eShopModernizing) (sonraki açıklanan ilgili örnek uygulamaları bulunduğu yerde Bölüm). Son bölüm ve GitHub üzerinde adım adım wiki ile ilgili izlenecek yollar, geliştiricilere ve mimarlara uygulama ayrıntılara odaklanmak isteyen daha fazla ilgi olacaktır.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Örnek uygulamalar için eski uygulamaları modernleştirme: eShopModernizing

[EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) depo github'daki eski tek yapılı web uygulamaları benzetimi iki örnek uygulamalar sunar. Bir web uygulamasını ASP.NET MVC kullanılarak geliştirilen; İkinci web uygulamasına ASP.NET Web Forms kullanarak geliştirilen ve bir WCF Hizmeti arka ucuna tüketen WinForms istemci masaüstü uygulaması ile N katmanlı uygulama üçüncü uygulamasıdır. Bu uygulamalar, geleneksel .NET Framework temel alır. Bu örnek uygulamaları, modernleştirdiğini için var olan eski .NET Framework uygulamaları için beklenen gibi .NET Core veya ASP.NET Core kullanmayın.

Bu örnek uygulamaları Modernleştirilmiş kodla ikinci bir sürüm varsa ve hangi oldukça basittir. Uygulama sürümleri arasındaki en önemli fark, ikinci sürümleri Windows kapsayıcıları dağıtımlardaki seçim kullanmasıdır. Ayrıca var. ikinci sürümleri, Azure depolama görüntülerini yönetmek için Blobları izleme ve uygulamaları denetim için güvenlik ve Azure Application ınsights'ı yönetmek için Azure Active Directory gibi bazı eklemeler

## <a name="send-your-feedback"></a>Geri bildirim gönderin

Bu kılavuz, geliştirme ve mevcut .NET web uygulamaları modernleştirme seçenekleriniz anlamanıza yardımcı olması için yazılmıştır. İlgili örnek uygulamalar ve kılavuz dönüştürüyoruz. Geri bildiriminiz bizim için çok önemlidir! Bu kılavuz nasıl daha yararlı olabileceği hakkında açıklamalar varsa, Lütfen bunları gönderin [ dotnet-architecture-ebooks-feedback@service.microsoft.com ](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
>[Next](lift-and-shift-existing-apps-azure-iaas.md)
