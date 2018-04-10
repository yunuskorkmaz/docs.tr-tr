---
title: Azure Bulut ve Windows kapsayıcıları varolan .NET uygulamaları modernize
description: Kaldırın ve mevcut uygulamalar Azure Bulutu ve bu e-kitap ile kapsayıcıları için shift hakkında bilgi edinme.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.prod: .net
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ba48579735379bfc857993cd1546f5f7125101f4
ms.sourcegitcommit: d3cfda0943364aaf6ccd574f55f584576c8a4fee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/08/2018
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-v10"></a>Azure Bulut ve Windows kapsayıcıları (v1.0) ile varolan .NET uygulamaları modernize

![kapak resmi](./media/cover.png)

TARAFINDAN YAYIMLANAN  
Microsoft Press ve Microsoft DevDiv  
Bölümler, Microsoft Corporation'ın  
One Microsoft Way  
Redmond, Washington 98052-6399  

Telif Hakkı © Microsoft Corporation'ın 2017  

Tüm hakları saklıdır. Bu kitap içeriğini hiçbir bölümü herhangi bir biçimde veya herhangi bir yöntem publisher'ın yazılı izni olmadan çoğaltılamaz.

Bu kitap, ücretsiz bir elektronik defteri (e-kitap) http://dot.net/architecture gibi Microsoft'taki birden çok kanallar aracılığıyla kullanılabilen biçiminde kullanılabilir.

Bu kitap, e-posta ile ilgili sorularınız varsa [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

Bu kitap sağlanan "olarak-olan" ve yazar görünümler ve görüşlerini ifade eder. Görünümler, görüşlerini ve URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu Defteri'nde ifade bilgileri bildirilmeksizin değiştirilebilir.

Burada açıklanan bazı örnekler yalnızca çizim için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya çıkarılmamalıdır.

Microsoft ve http://www.microsoft.com "Ticari" Web sayfasında listelenen ticari Microsoft şirketler grubunun ticari markalarıdır. Diğer tüm işaretleri, ilgili sahiplerinin özelliği var.

Yazar:
> **Cesar de la Torre**, Sr. PM, .NET ürün ekibi, Microsoft Corp.

Katılımcıların ve gözden geçirenler:
> **Tan Hunter**, .NET ekibi, Microsoft iş ortağı Director PM  
> **Paul Yuknewicz**, asıl PM Yöneticisi, Microsoft Visual Studio Araçları ekibi  
> **Lisa Guthrie**, Sr. Visual Studio Araçları ekibi, Microsoft PM  
> **Ankit Asthana**, asıl PM Yöneticisi, .NET ekibi, Microsoft  
> **Unai Zorrilla**, geliştirici sağlama, düz kavramları  
> **Javier Valero**, baş Müdürü Grupo çözümleri adresindeki işletim  

## <a name="introduction"></a>Giriş

Web uygulamalarınızı modernize ve buluta taşımak karar verdiğinizde, mutlaka tam olarak uygulamalarınızı yeniden düzenlenmesine gerekmez. Bir uygulama mikro gibi gelişmiş bir yaklaşım kullanarak mimarisinin yeniden düzenlenmesinden her zaman Maliyet ve zaman kısıtlamaları nedeniyle bir seçenek değildir. Uygulama türüne bağlı olarak, bir uygulama mimarisinin yeniden düzenlenmesinden ayrıca gerekli olmayabilir. Düşük maliyet kuruluşunuzun bulut geçiş stratejisi iyileştirmek için kendi iş gereksinimlerinizi ve uygulamalarınızı gereksinimlerini göz önünde bulundurmanız önemlidir. Belirlemek gerekir:

- Hangi uygulamaların bir dönüşüm gerekiyor veya mimarisinin yeniden düzenlenmesinden.

- Hangi uygulamaların yalnızca kısmen modernized gerekir.

- Hangi uygulamaların, "kaldırın ve shift" bulut için doğrudan.

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz, öncelikle "kaldırın ve shift" senaryoları ve var olan Microsoft .NET Framework web ya da hizmet odaklı uygulamalar ilk modernization odaklanır. Yükseltme shift ise uygulamanın kodunu ve temel mimarisi değiştirmeden daha yeni ya da daha yeni bir ortam için bir iş yükü taşıma işlemi.

Bu kılavuzda, var olan .NET Framework sunucu uygulamalarınızın belirli alanlarında mimarisinin yeniden düzenlenmesinden veya tüm uygulamaların değiştirilemeyen modernizing doğrudan buluta taşıma konusunda açıklanmaktadır.

Bu kılavuz, ayrıca uygulamalarınızı buluta taşıma ve belirli bir dizi yeni teknolojileri ve Windows kapsayıcıları ve azure'da orchestrators gibi yaklaşım kullanarak uygulamaları kısmen modernizing avantajlarını vurgular.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Var olan .NET uygulamaları için bulut yolu

Kuruluşlar, genellikle çeviklik ve hız için kendi uygulamalarında alabilirsiniz buluta Taşı'yı seçin. Genellikle şirket içi sunucular ayarlamak için geçen hafta karşılaştırılan dakika içinde bulutta binlerce sunucuya (VM'ler) ayarlayabilirsiniz.

Geçiş için tek ve tümünü kapsayan tek bir strateji hiç bulut uygulamaları. Sizin için doğru geçiş stratejisi, kuruluşunuzun ihtiyaçlarına ve öncelikleri ve geçirdiğiniz uygulamaları tür bağlıdır. Tüm uygulamalar için bir hizmet olarak platform taşıma yatırım garanti ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) modeli veya geliştirme bir [bulut yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) uygulama modeli. Çoğu durumda, iş gereksinimlerinize göre buluta varlıklarınızı taşıma yatırım aşamalı veya artımlı bir yaklaşım alabilir.

En uzun vadeli çeviklik ve kuruluş için değerli modern uygulamalar için de yatırım yararlanabilir *bulut iyileştirilmiş* ve *bulut yerel* uygulama mimarilerindeki. Ancak, eski varlıklar veya var uygulamalar buluta önemli faydaları hayata geçirmek için geçiş sırasında en az zaman ve para (mimarisinin yeniden düzenlenmesinden veya kod değişiklik yok) harcamanız anahtarıdır.

Şekil 1-1 artımlı aşamalarında .NET uygulamalarınız buluta taşıdığınızda yapabileceğiniz olası yolları gösterilmektedir.

 ![Var olan .NET uygulamaları ve Hizmetleri için modernization yolları](./media/image1-1.png)

> **Şekil 1-1**. Var olan .NET uygulamaları ve Hizmetleri için modernization yolları

Her geçiş yaklaşımı farklı avantajları ve bunu kullanma nedenleri vardır. Buluta uygulamaları geçirme ya da birden çok yaklaşımlar ile belirli bileşenlerini seçin, tek bir yaklaşım seçebilirsiniz. Tek tek uygulamalar için tek bir yaklaşım veya olgunluk durumu sınırlı değildir. Örneğin, ortak bir karma yaklaşım belirli şirket içi bileşenlerini ve diğer bileşenleri bulutta gerekir.

Yalnızca ilk iki geçiş düzeylerinde kaldırın ve uygulamalarınızı kaydır:

**Düzey 1: Bulut altyapı hazır**: Bu geçiş yaklaşımda, yalnızca yeniden barındırma veya geçerli şirket içi bir hizmet olarak altyapı uygulamaları taşırsanız ([Iaas](https://azure.microsoft.com/overview/what-is-iaas/)) platformu. Uygulamalarınızı önce olarak neredeyse aynı birleşim sahip, ancak artık bulutta VM'ler için dağıtmadan.

**Düzey 2: Bulut DevOps hazır**: Bu düzeyde bir ilk yükseltme ve shift sonra ve hala mimarisinin yeniden düzenlenmesinden veya kodunu değiştirerek olmadan, uygulamanızı bulutta çalışmasını daha da fazla avantajlara. Enterprise geliştirme işlemleri (DevOps) işlemlerinizi daraltmayı göre daha hızlı dağıtmayı uygulamalarınızı çeviklik geliştirin. Bunun için Docker altyapısını temel Windows kapsayıcıları gibi bir teknoloji kullanarak. Kapsayıcıları birden çok aşamada dağıttığınızda, uygulama bağımlılıkları neden uyuşmazlık kaldırın. Kapsayıcılar ayrıca veri, izleme ve sürekli tümleştirme/sürekli dağıtımı (CI/CD) işlem hatları ile ilgili ek bulut yönetimli Hizmetleri'ni kullanın.

Olgunluk üçüncü düzeyde bulutta nihai amacıyla olmakla birlikte, birçok uygulama ve bu kılavuzun değil ana odak için isteğe bağlıdır:

**Düzey 3: Bulut iyileştirilmiş**: Bu geçiş yaklaşım, genellikle iş gereksinimlerini ve kritik uygulamalarınızı modernizing hedefleri tarafından yönetilir. Bu düzeyde PaaS bilgi işlem platformlarına uygulamalarınızı taşımak için PaaS Hizmetleri kullanın. Uygulamanız [bulut yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) uygulamaları ve mikro mimarisi ile uzun vadeli çeviklik uygulamaları geliştirin ve yeni sınırları ölçeklendirmek için. Bu tür modernization genellikle özel bulut için mimariden gerektirir. Yeni kod, genellikle özellikle bulut yerel uygulama ve mikro hizmet tabanlı modelleri taşıdığınızda yazılmalıdır. Bu yaklaşım, tek yapılı ve şirket içi uygulama ortamınızda elde etmek zordur faydaları elde size yardımcı olabilir.

Tablo 1-1 ana avantajları ve her geçiş veya modernization yaklaşım seçme nedenleri açıklanmaktadır.

| **Bulut altyapısı kullanıma hazır** <br /> *Yükseltme ve kaydırma* | **Bulut DevOps kullanıma hazır** <br /> *Yükseltme ve kaydırma* | **Bulut için iyileştirilmiş** *Modernize/düzenleme/yeniden yazma* |
|---|---|---|
| **Uygulamanın işlem hedef** |
| Azure vm'lerinin dağıtılan uygulamalar | VM'ler, Azure Service Fabric ya da Azure kapsayıcı hizmeti (diğer bir deyişle, Kubernetes) dağıttığınız kapsayıcılı tek yapılı veya N katmanlı uygulamalar | Kapsayıcılı mikro veya PaaS Azure App Service, Azure Service Fabric, Azure kapsayıcı hizmeti (diğer bir deyişle, Kubernetes) göre normal uygulamalar |
| **Veri hedefi** |
| SQL veya herhangi bir VM üzerinde ilişkisel veritabanı | Azure SQL veritabanı yönetilen örneği | Azure SQL Database, Azure Cosmos DB veya diğer NoSQL |
| **Avantajlar**|
| <li>Hiçbir mimarisinin yeniden düzenlenmesinden yeni bir kod <li> Hızlı geçiş için en az çaba <li> Azure'da desteklenen en küçük ortak paydası <li> Temel kullanılabilirliği garanti altına alır. <li> Buluta taşıdıktan sonra bunu daha da modernize kolaydır | <li>Hiçbir mimarisinin yeniden düzenlenmesinden yeni bir kod <li> Kapsayıcıları artımlı çaba VM'ler sunar. <li> Gelişmiş Dağıtım ve DevOps kapsayıcıları nedeniyle yayın becerisi <li> Yoğunluğu ve daha düşük bir dağıtım maliyeti <li> Uygulamalar ve bağımlılıklarını taşınabilirliği <li> Azure kapsayıcı hizmeti (veya Kubernetes) ile ve Azure Service Fabric, yüksek kullanılabilirlik ve orchestration sağlar <li> Service Fabric düğümleri/VM düzeltme eki uygulama <li> Ana bilgisayar hedefleri esnekliğini: Azure sanal makineler veya sanal makine ölçek ayarlar, Azure kapsayıcı hizmeti (veya Kubernetes), Service Fabric ve gelecekteki kapsayıcı tabanlı seçimi | <li>Bulut, düzenleme, gereken yeni kod Mimarı <li> Mikro bulut yerel yaklaşımlar <li> Yeni web uygulamaları, tek yapılı, N katmanlı, bulut dayanıklı ve bulut için iyileştirilmiş <li> Tam olarak yönetilen hizmetler <li> Otomatik düzeltme eki uygulama <li> Ölçek için en iyi duruma getirilmiş <li> Alt sistemi tarafından otonom Çeviklik için en iyi duruma getirilmiş <li> Dağıtım ve DevOps yerleşik <li> Yuvalar ve dağıtım stratejileri gibi gelişmiş DevOps <li> PaaS ve orchestrator hedefleri: Azure App Service, Azure kapsayıcı hizmeti (veya Kubernetes), Azure Service Fabric ve gelecekteki kapsayıcı tabanlı PaaS |
| **Zorlukları** |
| <li> Harcama işletim ya da veri merkezleri kapatma shift dışında küçük bulut değeri <li> Çok az yönetilir: Hayır işletim sistemi veya ara yazılım düzeltme eki uygulama; Terraform, Spinnaker veya Puppet gibi kaybolabileceğini altyapı çözümleri | <li> Containerizing öğrenme eğrisi içinde ek bir adım gerektir değişmez değil | <li> Yeniden düzenleme veya (artan zaman ve bütçe) yeniden yazma işlemi önemli kodu gerektirebilir |
> **Tablo 1-1.** Avantajları ve mevcut .NET uygulamaları ve Hizmetleri için modernization yollarını zorlukları

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Temel teknolojileri ve olgunluk seviyesi tarafından mimariler

.NET framework uygulamaları başlangıçta geç 2001'de sunulan sürüm 1.0, .NET Framework ile başlatıldı. Ardından, şirketler taşınmış daha yeni sürümleri (2.0, 3.5 ve .NET gibi 4.x). Bu uygulamaların çoğu Windows Server ve Internet Information Server (IIS) çalıştıran ve SQL Server, Oracle, MySQL veya diğer RDBMS gibi bir ilişkisel veritabanı kullanılır.

Varolan .NET uygulamaların çoğu günümüzde .NET Framework'e dayalı 4.x ya da .NET Framework 3.5 ve ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, Windows Communication Foundation (WCF), ASP.NET SignalR ve ASP.NET Web sayfaları gibi kullanım web çerçeveleri . Bunlar, .NET Framework teknolojileri Windows bağımlı kurdu. Bu bağımlılık eski uygulamalar yalnızca geçiriyorsanız ve uygulama altyapınızı küçük değişiklikler yapmak istediğiniz dikkate almak önemlidir.

Şekil 1-2 birincil teknolojilerini ve üç bulut olgunluk düzeylerin her birinde kullanılan mimarisi stilleri gösterir:

![Var olan .NET modernizing her olgunluk seviyesi için birincil teknolojileri web uygulamaları](./media/image1-2.png)

> **Şekil 1-2.** Var olan .NET modernizing her olgunluk seviyesi için birincil teknolojileri web uygulamaları

Şekil 1-2 en yaygın senaryolardan vurgular, ancak birçok karma ve karma Çeşitlemeler mimariye geldiğinde mümkün. Örneğin, yalnızca tek yapılı mimarilerinde varolan web uygulamaları için aynı zamanda hizmet yönlendirmesi, N katmanlı ve diğer mimarisi stili Çeşitlemeler olgunluk modelleri uygulayın.

Her olgunluk seviyesi modernization işleminde aşağıdaki temel teknolojileri ve yaklaşımlar ile ilişkilidir:

- **Bulut altyapısı için hazır** (rehost veya kaldırın ve shift temel): ilk adım olarak, birçok kuruluş yalnızca hızlı bir şekilde bulut geçiş stratejisi yürütmek istediğiniz. Bu durumda, uygulamaları yalnızca rehosted. Çoğu yeniden barındırılmasını kullanarak otomatikleştirilebilir [Azure geçirmek](https://aka.ms/azuremigrate), bulut araçları gibi Kılavuzu, Öngörüler ve Azure'a geçirme yardımcı olmak için gereken mekanizmaları sağlayan bir hizmet dayalı [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)ve [Azure veritabanı geçiş hizmeti](https://azure.microsoft.com/campaigns/database-migration/). Böylece buluta eski uygulamaları taşıdığınızda altyapı ayrıntıları varlıklarınız hakkında bilgi edinebilirsiniz el ile yeniden barındırılmasını yukarı de ayarlayabilirsiniz. Örneğin, uygulamalarınızı VM'ler için Azure'da çok az ile taşıyabilir yalnızca küçük yapılandırma değişiklikleri ile büyük olasılıkla değiştirme. Bu durumda özellikle Azure'da sanal ağlar oluşturursanız, bir şirket içi ortama benzer ağdır.

- **Bulut DevOps hazır** (Geliştirilmiş yükseltme ve üst karakter): uygulama çekirdek mimarisini değiştirmeden bazı önemli avantajlar buluta kazanmak için birkaç önemli dağıtımi iyileştirmeleri sağlama konusunda bu modelidir. Burada temel adım eklemektir [Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) var olan .NET Framework uygulamalarınız için destek. Bu önemli bir adım (kapsayıcıyla taşıma) genel yükseltme ve shift çaba çok açık olacak şekilde kodu temas gerektirmez. Gibi araçları kullanabilirsiniz [Image2Docker](https://github.com/docker/communitytools-image2docker-win) veya kendi araçları ile Visual Studio [Docker](https://www.docker.com/). Visual Studio, ASP.NET uygulamalarının ve Windows kapsayıcıları görüntüleri akıllı Varsayılanları otomatik olarak seçer. Bu araçlar, hızlı bir iç döngü hem Azure'a kapsayıcıları almak için hızlı bir yolunu sunar. Birden çok ortamlara dağıttığınızda, çeviklik geliştirildi. Ardından, üretime taşıyarak, Windows Kapsayıcılarınızı orchestrators gibi dağıtabileceğiniz [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) veya [Azure kapsayıcı hizmeti](https://azure.microsoft.com/services/container-service/) (Kubernetes, DC/OS ve Swarm). Bu ilk modernization sırasında da varlıklar gibi araçlarla izleme buluttan ekleyebilirsiniz [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); İle uygulama yaşam döngülerine CI/CD işlem hatlarını [Visual Studio Team Services](https://www.visualstudio.com/team-services/); ve mevcut olan çok daha fazla veri kaynağı hizmetler. Başlangıçta geleneksel kullanılarak geliştirilmiş bir tek yapılı web uygulaması örneği için değiştirebileceğiniz [ASP.NET Web Forms](https://www.asp.net/web-forms) veya [ASP.NET MVC](https://www.asp.net/mvc), ancak artık, onu Windows kapsayıcıları kullanarak dağıtın. Windows kapsayıcıları kullandığınızda, ayrıca, verilerinizi bir veritabanında geçiş yapmanız gerekir [yönetilen Azure SQL veritabanı örneği](https://docs.microsoft.com/azure/sql-database/), uygulamanızın çekirdek mimarisini değiştirmeden tüm.

- **Bulut için iyileştirilmiş**: belirtildiği gibi bulut uygulamaları modernize zaman nihai amacıyla sisteminizi gibi PaaS platformlarda temel [Azure App Service](https://azure.microsoft.com/services/app-service/). PaaS platformları odaklanmak modern web uygulamaları ve uygulamalarınızı dayalı yeni hizmetleriyle genişletmek [sunucusuz bilgi işlem](https://azure.microsoft.com/overview/serverless-computing/) ve platformlar gibi [Azure işlevleri](https://azure.microsoft.com/services/functions/). İkinci ve daha gelişmiş bu olgunluk modelde mikro mimarileri hakkında senaryodur ve [bulut yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) , genellikle orchestrators gibi kullanan uygulamalar [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) veya [Azure kapsayıcı hizmeti](https://azure.microsoft.com/services/container-service/) (Kubernetes, DC/OS ve Swarm). Bu orchestrators özellikle mikro ve birden çok kapsayıcı uygulamaları için yapılır. Bu yaklaşım (örneğin, mikro ve PaaS), genellikle yeni kod-belirli PaaS platformlar için uyarlanmış kodu veya mikro gibi belirli mimarileri ile hizalar kod yazmaya gerektirir.

Şekil 1-3 her olgunluk seviyesi için kullanabileceğiniz iç teknolojileri gösterir:

![Her modernization olgunluk seviyesi için iç teknolojileri](./media/image1-3.png)

> **Şekil 1-3.** Her modernization olgunluk seviyesi için iç teknolojileri

## <a name="lift-and-shift-scenarios"></a>Yükseltme ve shift senaryoları

Yükseltme ve shift geçişler için yükseltme ve shift pek çok farklı Çeşitleme uygulama senaryolarında kullanabilirsiniz aklınızda bulundurun. Yalnızca uygulamanızı yeniden barındırma Şekil 1-VMs bulutta yalnızca uygulamanız için ve veritabanı sunucunuz için kullandığınız 4'te, gösterilene benzer bir senaryo olabilir.

![Bulutta saf bir Iaas senaryosu örneği](./media/image1-4.png)

> **Şekil 1-4**. Bulutta saf bir Iaas senaryosu örneği

İlerleyen, yalnızca o olgunluk düzeyden öğeleri kullanan bir saf bulut DevOps hazır bir uygulama olabilir. Veya bir ara durum uygulamasından bazı öğeler ile bulut altyapısı hazır ve diğer öğeleri bulut DevOps kullanıma hazır'dan olabilir ("seçin ve Seç" bir ya da karma modeli), Şekil 1-5'te ister.

!["Seçin ve Seç" içeren örnek senaryo, Iaas, DevOps ve verilerin kapsayıcıyla taşınmasını varlıklar veritabanı](./media/image1-5.png)

> **Şekil 1-5.** "Seçin ve Seç" içeren örnek senaryo, Iaas, DevOps ve verilerin kapsayıcıyla taşınmasını varlıklar veritabanı

Ardından, geçirmek, birçok var olan .NET Framework uygulamaları için ideal senaryo olarak çok az şey yapmanızı önemli avantajlarından yararlanabilmek için bir bulut DevOps hazır uygulamaya geçişi yapılamadı. Bu yaklaşım Ayrıca, bulut iyileştirme için olası bir sonraki adım olarak ayarlar. Şekil 1-6 bir örneği gösterir.

![Windows kapsayıcıları ve yönetilen hizmetler ile örnek buluta DevOps hazır uygulamalar senaryo](./media/image1-6.png)

> **Şekil 1-6.** Windows kapsayıcıları ve yönetilen hizmetler ile örnek buluta DevOps hazır uygulamalar senaryo

Bile devam edilirse, belirli senaryoları için birkaç mikro ekleyerek varolan buluta DevOps hazır uygulamanız genişletebilirsiniz. Bu, kısmen bulut yerel düzeyine taşıyabilir bulut iyileştirilmiş modelinde olmayan mevcut kılavuzunun odak.


## <a name="what-this-guide-does-not-cover"></a>Ne bu kılavuzda ele alınmamaktadır

Bu kılavuz, Şekil 1-7'de gösterildiği gibi belirli bir alt kümesini örnek senaryolar kapsar. Bu kılavuz yalnızca yükseltme ve shift senaryoları ve sonuç olarak, bulut DevOps hazır model üzerinde odaklanmıştır. Bulut DevOps hazır modelinde, bir .NET Framework uygulamasını Windows kapsayıcıları yanı sıra, izleme gibi ek bileşeni kullanılarak modernized ve CI/CD ardışık düzenleri. Her bileşen, bulut uygulamalarını daha hızlı dağıtma ve çeviklik esastır.

![Yükseltme ve kaydırma ve ilk modernization bulut DevOps kullanılmaya hazır uygulamalar](./media/image1-7.png)

> **Şekil 1-7.** Yükseltme ve kaydırma ve ilk modernization bulut DevOps kullanılmaya hazır uygulamalar

Bu kılavuzun odağı özeldir. Yükseltme ve varolan .NET uygulamalarınızın shift mimarisinin yeniden düzenlenmesinden olmadan ve kod değişikliğine elde etmek için uygulayabileceğiniz yol gösterir. Sonuç olarak, uygulamanızın bulut DevOps kullanıma hazır olmak nasıl gösterilir.

Bu kılavuz, bir mikro mimarisi gelişmesi nasıl gibi bulut yerel uygulamaları ile nasıl çalışılacağını göstermez. Uygulamalarınızı yeniden düzenlenmesine veya üzerinde mikro dayalı yeni uygulamalar oluşturmak için e-kitap bakın [.NET mikro: mimarisi kapsayıcılı .NET uygulamaları için](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Ek kaynaklar

- **Microsoft Platformu ve araçları ile Docker uygulama yaşam döngüsü kapsayıcılı** (indirilebilir e-kitap): [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

- **.NET mikro: Kapsayıcılı .NET uygulamaları mimarisi** (indirilebilir e-kitap): [ *https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

- **ASP.NET Core ve Azure ile modern web uygulamaları mimariden** (indirilebilir e-kitap): [ *https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>Bu kılavuz kullanan

Bu kılavuz, geliştiriciler ve .NET Framework sevkiyat ve uygulamaları serbest Gelişmiş çeviklik dayalı mevcut ASP.NET uygulamaları modernize istediğiniz çözüm mimarları için yazılmıştır.

Bir kurumsal Mimarı veya geliştirme sağlama/Windows kapsayıcıları kullanarak ve kullanırken buluta dağıtarak alabilirsiniz avantajları genel bir bakış yalnızca isteyen yönetmenin gibi bir teknik karar veren varsa, aynı zamanda bu kılavuzda yararlı olabilir Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Bu kılavuz kullanma

Bu kılavuzda "neden" adresleri-var olan uygulamalarınız ve almak için bulut uygulamalarınızı taşıdığınızda Windows kapsayıcıları kullanma belirli faydası modernize oluşturmak istemenizin nedeni. Kılavuzun ilk birkaç bölümlerde içerik mimarları ve genel bir bakış isteyen, ancak kullanan uygulama ve teknik, adım adım ayrıntıları odaklanmak gerekmez teknik karar alıcılar için tasarlanmıştır.

Bu kılavuzun önceki bölümde belirli dağıtım senaryoları odaklanan birden çok izlenecek yollar sunar. Bu kılavuz, senaryoları özetlemek ve bunların avantajları vurgulayın için daha kısa sürümleri izlenecek yollar sunar. Tam izlenecek yollar detaya gitme kurulumu ve uygulama ayrıntılarını ve bir dizi yayımlanan [wiki gönderileri](https://github.com/dotnet-architecture/eShopModernizing/wiki) aynı ortak alanda [GitHub deposuna](https://github.com/dotnet-architecture/eShopModernizing) ilgili örnek uygulamaları (sonraki ele bulunduğu yerde bölümü). Önceki bölümde ve adım adım wiki izlenecek yollar github'da geliştiriciler ve uygulama ayrıntılarını odaklanmak istiyorsanız mimarları için daha fazla ilgi olacaktır.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Örnek uygulamaları için eski uygulamaları modernizing: eShopModernizing

[EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) bağlantıların github'da eski tek yapılı web uygulamaları benzetimi iki örnek uygulama sunar. Bir web uygulaması, ASP.NET MVC kullanılarak geliştirilen; İkinci web uygulaması, ASP.NET Web Forms kullanılarak geliştirilir. Her iki web uygulamaları üzerinde geleneksel .NET Framework temel alır. Bu örnek uygulamaları modernized için var olan eski .NET Framework uygulamaları olması gerektiği gibi .NET Core veya ASP.NET Core kullanmayın.

Her iki örnek uygulamaları modernized koduyla ikinci bir sürüme sahip ve hangi oldukça basittir. Uygulama sürümleri arasındaki en önemli fark, ikinci sürümleri dağıtım seçeneği Windows kapsayıcılar kullanma ' dir. Ayrıca var. ikinci sürümleri, Azure depolama görüntüleri yönetmek için BLOB güvenlik ve Azure Application Insights izleme ve denetim uygulamaları yönetmek için Azure Active Directory gibi birkaç eklemeler

## <a name="send-your-feedback"></a>Geri bildirim gönder

Bu kılavuz, geliştirme ve varolan .NET web uygulamaları modernizing seçeneklerinizi anlamanıza yardımcı olması için yazılmıştır. Kılavuzu ve ilgili örnek uygulamalar artmaktadır. Geri bildiriminiz Hoş Geldiniz! Bu kılavuzda nasıl daha yararlı olabileceği hakkında yorumlar varsa, lütfen göndermenize [ dotnet-architecture-ebooks-feedback@service.microsoft.com ](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
[Next](lift-and-shift-existing-apps-azure-iaas.md)
