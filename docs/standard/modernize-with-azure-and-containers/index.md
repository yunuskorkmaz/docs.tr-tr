---
title: Var olan .NET uygulamaları ile Azure Bulutu ve Windows kapsayıcıları modernize (2 edition)
description: Shift kaldırın ve bu e-kitap ile kapsayıcıları ve Azure cloud mevcut uygulamaları modernize öğrenin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 4/28/2018
ms.openlocfilehash: 3fcfdca68e05494785148cbbe149cdc2f812c577
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/10/2018
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Azure Bulut ve Windows kapsayıcıları varolan .NET uygulamaları modernize (2 edition)

![kapak resmi](./media/cover.png)

TARAFINDAN YAYIMLANAN  
Microsoft Press ve Microsoft DevDiv  
Bölümler, Microsoft Corporation'ın  
One Microsoft Way  
Redmond, Washington 98052-6399  

Telif Hakkı © Microsoft Corporation 2018  

Tüm hakları saklıdır. Bu kitap içeriğini hiçbir bölümü herhangi bir biçimde veya herhangi bir yöntem publisher'ın yazılı izni olmadan çoğaltılamaz.

Bu kitap gibi ücretsiz bir elektronik defteri (e-kitap) Microsoft'taki birden çok kanallar aracılığıyla kullanılabilen form kullanılabilir http://dot.net/architecture.

Bu kitap, e-posta ile ilgili sorularınız varsa [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

Bu kitap sağlanan "olarak-olan" ve yazar görünümler ve görüşlerini ifade eder. Görünümler, görüşlerini ve URL ve diğer Internet Web sitesi başvuruları dahil olmak üzere bu Defteri'nde ifade bilgileri bildirilmeksizin değiştirilebilir.

Burada açıklanan bazı örnekler yalnızca çizim için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya çıkarılmamalıdır.

Microsoft ve adresinde listelenmiş ticari http://www.microsoft.com "Ticari" Web sayfasında Microsoft şirketler grubunun ticari markalarıdır. Diğer tüm işaretleri, ilgili sahiplerinin özelliği var.

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

Web uygulamaları veya hizmetleri modernize ve buluta taşımak karar verdiğinizde, uygulamalarınızı tam olarak rearchitect mutlaka gerekmez. Mikro gibi gelişmiş bir yaklaşım kullanarak bir uygulama bütçeden her zaman Maliyet ve zaman kısıtlamaları nedeniyle bir seçenek değildir. Uygulama türüne bağlı olarak, bir uygulama bütçeden ayrıca gerekli olmayabilir. Düşük maliyet kuruluşunuzun bulut geçiş stratejisi iyileştirmek için kendi iş gereksinimlerinizi ve uygulamalarınızı gereksinimlerini göz önünde bulundurmanız önemlidir. Belirlemek gerekir:

- Hangi uygulamaların bir dönüşüm gerekiyor veya bütçeden.

- Hangi uygulamaların yalnızca kısmen modernized gerekir.

- Hangi uygulamaların, "kaldırın ve shift" bulut için doğrudan.

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz uygulamanın kodunu değiştirmeden önemli ölçüde daha yeni ya da daha yeni bir ortam için bir iş yükü taşıma işlemi anlamına öncelikle var olan Microsoft .NET Framework web ya da hizmet odaklı uygulamalar, ilk modernization üzerinde odaklanmıştır. ve temel mimarisi. 

Bu kılavuz, ayrıca uygulamalarınızı buluta taşıma ve belirli bir dizi yeni teknolojileri ve Windows kapsayıcıları ve ilgili işlem platformları Windows kapsayıcıları destekleyen Azure gibi yaklaşım kullanarak uygulamaları kısmen modernizing avantajlarını vurgular.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Var olan .NET uygulamaları için bulut yolu

Kuruluşlar, genellikle çeviklik ve hız için kendi uygulamalarında alabilirsiniz buluta Taşı'yı seçin. Genellikle şirket içi sunucular ayarlamak için geçen hafta karşılaştırılan dakika içinde bulutta binlerce sunucuya (VM'ler) ayarlayabilirsiniz.

Geçiş için tek ve tümünü kapsayan tek bir strateji hiç bulut uygulamaları. Sizin için doğru geçiş stratejisi, kuruluşunuzun ihtiyaçlarına ve öncelikleri ve geçirdiğiniz uygulamaları tür bağlıdır. Tüm uygulamalar için bir hizmet olarak platform taşıma yatırım garanti ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) modeli veya geliştirme bir [bulut yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) uygulama modeli. Çoğu durumda, iş gereksinimlerinize göre buluta varlıklarınızı taşıma yatırım aşamalı veya artımlı bir yaklaşım alabilir.

En uzun vadeli çeviklik ve kuruluş için değerli modern uygulamalar için de yatırım yararlanabilir *bulut yerel* uygulama mimarilerindeki. Ancak, eski varlıklar veya var uygulamalar buluta önemli faydaları hayata geçirmek için geçiş sırasında en az zaman ve para (bütçeden veya kod değişiklik yok) harcamanız anahtarıdır.

Şekil 1-1 artımlı aşamalarında .NET uygulamalarınız buluta taşıdığınızda yapabileceğiniz olası yolları gösterilmektedir.

 ![Var olan .NET uygulamaları ve Hizmetleri için modernization yolları](./media/image1-1.png)

> **Şekil 1-1**. Var olan .NET uygulamaları ve Hizmetleri için modernization yolları

Her geçiş yaklaşımı farklı avantajları ve bunu kullanma nedenleri vardır. Buluta uygulamaları geçirme ya da birden çok yaklaşımlar ile belirli bileşenlerini seçin, tek bir yaklaşım seçebilirsiniz. Tek tek uygulamalar için tek bir yaklaşım veya olgunluk durumu sınırlı değildir. Örneğin, ortak bir karma yaklaşım belirli şirket içi bileşenlerini ve diğer bileşenleri bulutta gerekir.

Her uygulama olgunluk seviyesi için kısa bir açıklama ve tanımı aşağıda verilmiştir:

**Düzey 1: Bulut altyapı hazır** uygulamalar: Bu geçiş yaklaşımda, yalnızca geçirmek ya da geçerli şirket içi uygulamalarınıza bir hizmet olarak Altyapı yeniden barındırma ([Iaas](https://azure.microsoft.com/overview/what-is-iaas/)) platformu. Uygulamalarınızı önce olarak neredeyse aynı birleşim sahip, ancak artık bulutta VM'ler için dağıtmadan.
Bu basit tür bir geçiş genellikle sektörünün "Yükselt & Shift." olarak bilinen

**Düzey 2: Bulut iyileştirilmiş** uygulamalar: Bu düzeyde ve bütçeden veya önemli kod değiştirilmesi olmadan hala kapsayıcıları gibi ve ek modern teknolojileri ile bulutta uygulamanızı çalışmasını başka avantajları kazanmadan Bulut yönetilen hizmetler. Enterprise geliştirme işlemleri (DevOps) işlemlerinizi daraltmayı göre daha hızlı dağıtmayı uygulamalarınızı çeviklik geliştirin. Bunun için Docker altyapısını temel Windows kapsayıcıları gibi teknolojileri kullanarak. Kapsayıcıları birden çok aşamada dağıttığınızda, uygulama bağımlılıkları neden uyuşmazlık kaldırın. Bu olgunluk modelde Iaas kapsayıcılarında dağıtabilir veya ek kullanırken PaaS bulut yönetimli services veritabanları için ilgili bir hizmet, izleme ve sürekli tümleştirme/sürekli dağıtım (CI/CD) ardışık düzen önbelleğe.

Olgunluk üçüncü düzeyde bulutta nihai amacıyla olmakla birlikte, birçok uygulama ve bu kılavuzun değil ana odak için isteğe bağlıdır:

**Düzey 3: Bulut-yerel** uygulamalar: Bu geçiş yaklaşım, genellikle iş gereksinimlerini ve kritik uygulamalarınızı modernizing hedefleri tarafından yönetilir. Bu düzeyde PaaS bilgi işlem platformlarına uygulamalarınızı taşımak için PaaS Hizmetleri kullanın. Uygulamanız [bulut yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) uygulamaları ve mikro mimarisi ile uzun vadeli çeviklik uygulamaları geliştirin ve yeni sınırları ölçeklendirmek için. Bu tür modernization genellikle özel bulut için mimariden gerektirir. Yeni kod, genellikle özellikle bulut yerel uygulama ve mikro hizmet tabanlı modelleri taşıdığınızda yazılmalıdır. Bu yaklaşım, tek yapılı ve şirket içi uygulama ortamınızda elde etmek zordur faydaları elde size yardımcı olabilir.

Tablo 1-1 ana avantajları ve her geçiş veya modernization yaklaşım seçme nedenleri açıklanmaktadır.

| **Bulut altyapısı kullanıma hazır** <br /> *Yükseltme ve kaydırma* | **Bulut için iyileştirilmiş** <br /> *Modernize* | **Bulut-yerel** <br /> *Modernize, rearchitect ve yeniden yazma* |
|---|---|---|
| **Uygulamanın işlem hedef** |
| Azure vm'lerinin dağıtılan uygulamalar | Tek yapılı veya Azure App Service, Azure kapsayıcı örneği (ACI), sanal makineleri kapsayıcıları, Azure Service Fabric veya AKS (Azure Kubernetes hizmeti) ile dağıtılan N katmanlı uygulamalar | Kapsayıcılı mikro Azure Kubernetes hizmet (AKS), Service Fabric ve/veya Azure işlevlerini dayalı sunucusuz mikro. |
| **Veri hedefi** |
| SQL veya herhangi bir VM üzerinde ilişkisel veritabanı | Yönetilen Azure SQL veritabanı örneği veya bulutta yönetilen başka bir veritabanı. | Mikro hizmet, Azure SQL Database, Azure Cosmos DB ya da yönetilen başka bir bulut veritabanında göre başına fined çizgisi veritabanları |
| **Avantajlar**|
| <li>Hiçbir bütçeden yeni bir kod <li> Hızlı geçiş için en az çaba <li> Azure'da desteklenen en küçük ortak paydası <li> Temel kullanılabilirliği garanti altına alır. <li> Buluta taşıdıktan sonra bunu daha da modernize kolaydır | <li> Hiçbir bütçeden <li> En az kod/yapılandırma değişiklikleri <li> Gelişmiş Dağıtım ve DevOps kapsayıcıları nedeniyle yayın becerisi <li> Yoğunluğu ve daha düşük bir dağıtım maliyeti <li> Uygulamalar ve bağımlılıklarını taşınabilirliği <li> Ana bilgisayar hedefleri esnekliğini: PaaS yaklaşımlar ve Iaas | <li> Mimari için bulut, buluttan en iyi avantajlarından yararlanabilmek ancak yeni kodu gereklidir <li> Mikro bulut yerel yaklaşımlar <li> Modern iş açısından önemli uygulamaları, bulut dayanıklı ölçeklenebilir <li> Tam olarak yönetilen hizmetler <li> Ölçek için en iyi duruma getirilmiş <li> Alt sistemi tarafından otonom Çeviklik için en iyi duruma getirilmiş <li> Dağıtım ve DevOps yerleşik |
| **Zorlukları** |
| <li> Harcama işletim ya da veri merkezleri kapatma shift dışında küçük bulut değeri <li> Az yönetilir: hiçbir işletim sistemi veya ara yazılım düzeltme eki uygulama; Terraform, Spinnaker veya Puppet gibi altyapı çözümleri kullanabilirsiniz | <li> Geliştiriciler ve BT işlemleri için öğrenme eğrisini içinde ek bir adım olan containerizing <li> DevOps ve CI/CD ardışık düzen 'şart' Bu yaklaşım için genellikle olur. Aksi halde kuruluşun kültür şu anda mevcut, ek bir sınaması olması olabilir| <li> Bulut yerel uygulamalar ve mikro hizmet mimarisi için rearchitecture gerektirir ve genellikle yeniden düzenleme veya modernizing zaman yeniden yazma işlemi önemli kodu (artan zaman ve bütçe) gerektirir <li> DevOps ve CI/CD ardışık düzen 'şart' Bu yaklaşım için genellikle olur. Aksi halde kuruluşun kültür şu anda mevcut, ek bir sınaması olması olabilir|
> **Tablo 1-1.** Avantajları ve mevcut .NET uygulamaları ve Hizmetleri için modernization yollarını zorlukları

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Temel teknolojileri ve olgunluk seviyesi tarafından mimariler

.NET framework uygulamaları başlangıçta geç 2001'de sunulan sürüm 1.0, .NET Framework ile başlatıldı. Ardından, şirketler taşınmış daha yeni sürümleri (2.0, 3.5 ve .NET gibi 4.x). Bu uygulamaların çoğu Windows Server ve Internet Information Server (IIS) çalıştıran ve SQL Server, Oracle, MySQL veya diğer RDBMS gibi bir ilişkisel veritabanı kullanılır.

Varolan .NET uygulamaların çoğu günümüzde .NET Framework'e dayalı 4.x ya da .NET Framework 3.5 ve ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, Windows Communication Foundation (WCF), ASP.NET SignalR ve ASP.NET Web sayfaları gibi kullanım web çerçeveleri . Bunlar, .NET Framework teknolojileri Windows bağımlı kurdu. Bu bağımlılık eski uygulamalar yalnızca geçiriyorsanız ve uygulama altyapınızı küçük değişiklikler yapmak istediğiniz dikkate almak önemlidir.

Şekil 1-2 birincil teknolojilerini ve üç bulut olgunluk düzeylerin her birinde kullanılan mimarisi stilleri gösterir:

![Var olan .NET modernizing her olgunluk seviyesi için birincil teknolojileri web uygulamaları](./media/image1-2.png)

> **Şekil 1-2.** Var olan .NET modernizing her olgunluk seviyesi için birincil teknolojileri web uygulamaları

Şekil 1-2 en yaygın senaryolardan vurgular, ancak birçok karma ve karma Çeşitlemeler mimariye geldiğinde mümkün. Örneğin, yalnızca tek yapılı mimarilerinde varolan web uygulamaları için aynı zamanda hizmet yönlendirmesi, N katmanlı ve diğer mimarisi stili Çeşitlemeler olgunluk modelleri uygulayın. Daha yüksek odak veya bir ya da başka bir mimari türü ve ilgili teknolojileri yüzdesi uygulamalarınızı genel olgunluk seviyesi belirler.

Her olgunluk seviyesi modernization işleminde aşağıdaki temel teknolojileri ve yaklaşımlar ile ilişkilidir:

- **Bulut altyapısı için hazır** (rehost veya Yükselt & shift temel): ilk adım olarak, birçok kuruluş yalnızca hızlı bir şekilde bulut geçiş stratejisi yürütmek istediğiniz. Bu durumda, uygulamaları rehosted. Çoğu yeniden barındırılmasını kullanarak otomatikleştirilebilir [Azure geçirmek](https://aka.ms/azuremigrate), bulut araçları gibi Kılavuzu, Öngörüler ve Azure'a geçirme yardımcı olmak için gereken mekanizmaları sağlayan bir hizmet dayalı [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/)ve [Azure veritabanı geçiş hizmeti](https://azure.microsoft.com/campaigns/database-migration/). Böylece buluta eski uygulamaları taşıdığınızda altyapı ayrıntıları varlıklarınız hakkında bilgi edinebilirsiniz el ile yeniden barındırılmasını yukarı de ayarlayabilirsiniz. Örneğin, uygulamalarınızı VM'ler için Azure'da az ile taşıyabilir yalnızca küçük yapılandırma değişiklikleri ile büyük olasılıkla değiştirme. Bu durumda özellikle Azure'da sanal ağlar oluşturursanız, bir şirket içi ortama benzer ağdır.

- **Bulut için iyileştirilmiş** (yönetilen Hizmetleri ve Windows kapsayıcılar): uygulama çekirdek mimarisini değiştirmeden bazı önemli avantajlar buluta kazanmak için birkaç önemli dağıtımi iyileştirmeleri sağlama konusunda bu modelidir. Burada temel adım eklemektir [Windows kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) var olan .NET Framework uygulamalarınız için destek. Bu önemli bir adım (kapsayıcıyla taşıma) genel yükseltme ve shift çaba açık olacak şekilde kodu temas gerektirmez. Gibi araçları kullanabilirsiniz [Image2Docker](https://github.com/docker/communitytools-image2docker-win) veya kendi araçları ile Visual Studio [Docker](https://www.docker.com/). Visual Studio, ASP.NET uygulamalarının ve Windows kapsayıcıları görüntüleri akıllı Varsayılanları otomatik olarak seçer. Bu araçlar, hızlı bir iç döngü hem Azure'a kapsayıcıları almak için hızlı bir yolunu sunar. Birden çok ortamlara dağıttığınızda, çeviklik geliştirildi. Ardından, üretime taşıyarak, Windows Kapsayıcılarınızı dağıtabilirsiniz [kapsayıcıları için Azure Web uygulaması](https://azure.microsoft.com/en-us/services/app-service/containers/), [Azure kapsayıcı örnekleri (ACI) ve Windows Server 2016 ve bir Iaas yaklaşım tercih ederseniz kapsayıcılar olan Azure VM'ler. Orchestrators gibi içine biraz daha karmaşık çok kapsayıcı uygulamaları için [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) veya [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/en-us/services/container-service/). Bu ilk modernization sırasında da varlıklar gibi araçlarla izleme buluttan ekleyebilirsiniz [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview); İle uygulama yaşam döngülerine CI/CD işlem hatlarını [Visual Studio Team Services](https://www.visualstudio.com/team-services/); ve mevcut olan çok daha fazla veri kaynağı hizmetler. Başlangıçta geleneksel kullanılarak geliştirilmiş bir tek yapılı web uygulaması örneği için değiştirebileceğiniz [ASP.NET Web Forms](https://www.asp.net/web-forms) veya [ASP.NET MVC](https://www.asp.net/mvc), ancak artık, onu Windows kapsayıcıları kullanarak dağıtın. Windows kapsayıcıları kullandığınızda, ayrıca, verilerinizi bir veritabanında geçiş yapmanız gerekir [yönetilen Azure SQL veritabanı örneği](https://docs.microsoft.com/azure/sql-database/), uygulamanızın çekirdek mimarisini değiştirmeden tüm.

- **Bulut yerel**: sunulduğu şekilde mimariden hakkında düşünmelidir [bulut yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) , büyük ve karmaşık uygulamaları ile çalışan birden çok bağımsız geliştirme ekiplerinin hedeflerken uygulamaları Geliştirilmiş ve sınırlarına dağıtılan farklı mikro. Ayrıca, granularized ve bağımsız ölçeklenebilirlik nedeniyle mikro hizmet başına. Bu mimari yaklaşımlar çok önemli zorlukları ve karmaşıklık yüz ancak büyük oranda bulut PaaS kullanılarak basitleştirilebilir ve orchestrators ister [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/en-us/services/container-service/) (Kubernetes yönetilen), [Azure hizmeti Doku, ve [Azure işlevleri](https://azure.microsoft.com/services/functions/) sunucusuz bir yaklaşım için. Bu yaklaşım (örneğin, mikro ve sunucusuz) genellikle bulut için Mimari ve yeni kod yazma gerektirir — belirli PaaS platformlar için uyarlanmış kodu veya mikro gibi belirli mimarileri ile hizalar kodu.

Şekil 1-3 her olgunluk seviyesi için kullanabileceğiniz iç teknolojileri gösterir:

![Her modernization olgunluk seviyesi için iç teknolojileri](./media/image1-3.png)

> **Şekil 1-3.** Her modernization olgunluk seviyesi için iç teknolojileri

## <a name="lift-and-shift-scenario"></a>Yükseltme ve shift senaryosu

Yükseltme ve shift geçişler için yükseltme ve shift pek çok farklı Çeşitleme uygulama senaryolarında kullanabilirsiniz aklınızda bulundurun. Yalnızca uygulamanızı yeniden barındırma Şekil 1-VMs bulutta yalnızca uygulamanız için ve veritabanı sunucunuz için kullandığınız 4'te, gösterilene benzer bir senaryo olabilir.

![Bulutta saf bir Iaas senaryosu örneği](./media/image1-4.png)

> **Şekil 1-4**. Bulutta saf bir Iaas senaryosu örneği

## <a name="modernization-scenarios"></a>Modernization senaryoları

Modernization senaryoları için öğeleri yalnızca o olgunluk düzeyden kullanan saf bulut için iyileştirilmiş bir uygulama olabilir. Veya bir ara durum uygulamasından bazı öğeler ile bulut altyapısı hazır ve diğer öğeleri Bulutla optimize edilmiş olabilir ("seçin ve Seç" bir ya da karma modeli), Şekil 1-5'te ister.

!["Seçin ve Seç" içeren örnek senaryo, Iaas, DevOps ve verilerin kapsayıcıyla taşınmasını varlıklar veritabanı](./media/image1-5.png)

> **Şekil 1-5.** "Seçin ve Seç" içeren örnek senaryo, Iaas, DevOps ve verilerin kapsayıcıyla taşınmasını varlıklar veritabanı

Ardından, geçirmek, birçok var olan .NET Framework uygulamaları için ideal senaryo olarak çok az şey yapmanızı önemli avantajlarından yararlanabilmek için bir bulut için optimize edilmiş uygulamaya geçişi yapılamadı. Bu yaklaşım Ayrıca, bulut-yerel için bir olası gelecekteki evrimi ayarlar. Şekil 1-6 bir örneği gösterir.

![Windows kapsayıcıları ve yönetilen hizmetler ile örnek bulut iyileştirilmiş uygulamaları senaryo](./media/image1-6.png)

> **Şekil 1-6.** Windows kapsayıcıları ve yönetilen hizmetler ile örnek bulut iyileştirilmiş uygulamaları senaryo

Bile devam edilirse, belirli senaryoları için birkaç mikro ekleyerek varolan bulut iyileştirilmiş uygulamanız genişletebilirsiniz. Bu, kısmen mevcut kılavuzunun ana odak değil bulut yerel model düzeyine taşımanız.


## <a name="what-this-guide-does-not-cover"></a>Ne bu kılavuzda ele alınmamaktadır

Bu kılavuz, Şekil 1-7'de gösterildiği gibi belirli bir alt kümesini örnek senaryolar kapsar. Bu kılavuz yalnızca yükseltme ve shift senaryoları ve sonuç olarak, Bulutla optimize edilmiş model üzerinde odaklanmıştır. Bulut için iyileştirilmiş modelinde, bir .NET Framework uygulamasını Windows kapsayıcıları yanı sıra, izleme gibi ek bileşeni kullanılarak modernized ve CI/CD ardışık düzenleri. Her bileşen, bulut uygulamalarını daha hızlı dağıtma ve çeviklik esastır.

![Bulut yerel bu kılavuzda ele alınmamaktadır](./media/image1-7.png)

> **Şekil 1-7.** Bulut yerel bu kılavuzda ele alınmamaktadır

Bu kılavuzun odağı özeldir. Yükseltme ve varolan .NET uygulamalarınızın shift bütçeden olmadan ve kod değişikliğine elde etmek için uygulayabileceğiniz yol gösterir. Sonuç olarak, bu, uygulamanızın nasıl yapılacağını gösterir Bulutla optimize edilmiş.

Bu kılavuz bir mikro mimarisi gelişmesi nasıl gibi bulut yerel uygulamalarının nasıl oluşturulacağını göstermez. Uygulamalarınızı rearchitect veya üzerinde mikro dayalı yeni uygulamalar oluşturmak için e-kitap bakın [.NET mikro: mimarisi kapsayıcılı .NET uygulamaları için](https://aka.ms/microservicesebook).

### <a name="additional-resources"></a>Ek kaynaklar

- **Microsoft Platformu ve araçları ile Docker uygulama yaşam döngüsü kapsayıcılı** (indirilebilir e-kitap): [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

- **.NET mikro: Kapsayıcılı .NET uygulamaları mimarisi** (indirilebilir e-kitap): [*https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

- **ASP.NET Core ve Azure ile modern web uygulamaları mimariden** (indirilebilir e-kitap): [*https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>Bu kılavuz kullanan

Bu kılavuz, geliştiriciler ve mevcut ASP.NET web uygulamaları veya sevkiyat ve uygulamaları serbest Gelişmiş Çeviklik için .NET Framework tabanlı WCF hizmetleri modernize istediğiniz çözüm mimarları için yazılmıştır.

Bir kurumsal Mimarı veya geliştirme sağlama/Windows kapsayıcıları kullanarak ve kullanırken buluta dağıtarak alabilirsiniz avantajları genel bir bakış yalnızca isteyen yönetmenin gibi bir teknik karar veren varsa, aynı zamanda bu kılavuzda yararlı olabilir Microsoft Azure.

## <a name="how-to-use-this-guide"></a>Bu kılavuz kullanma

Bu kılavuzda "neden" adresleri-var olan uygulamalarınız ve almak için bulut uygulamalarınızı taşıdığınızda Windows kapsayıcıları kullanma belirli faydası modernize oluşturmak istemenizin nedeni. Kılavuzun ilk birkaç bölümlerde içerik mimarları ve genel bir bakış isteyen, ancak kullanan uygulama ve teknik, adım adım ayrıntıları odaklanmak gerekmez teknik karar alıcılar için tasarlanmıştır.

Bu kılavuzun önceki bölümde belirli dağıtım senaryoları odaklanan birden çok izlenecek yollar sunar. Bu kılavuz, senaryoları özetlemek ve bunların avantajları vurgulayın için daha kısa sürümleri izlenecek yollar sunar. Tam izlenecek yollar detaya gitme kurulumu ve uygulama ayrıntılarını ve bir dizi yayımlanan [wiki gönderileri](https://github.com/dotnet-architecture/eShopModernizing/wiki) aynı ortak alanda [GitHub deposuna](https://github.com/dotnet-architecture/eShopModernizing) ilgili örnek uygulamaları (sonraki ele bulunduğu yerde bölümü). Önceki bölümde ve adım adım wiki izlenecek yollar github'da geliştiriciler ve uygulama ayrıntılarını odaklanmak istiyorsanız mimarları için daha fazla ilgi olacaktır.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Örnek uygulamaları için eski uygulamaları modernizing: eShopModernizing

[EShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) bağlantıların github'da eski tek yapılı web uygulamaları benzetimi iki örnek uygulama sunar. Bir web uygulaması, ASP.NET MVC kullanılarak geliştirilen; İkinci web uygulamasını ASP.NET Web Forms kullanılarak geliştirilen ve bir WCF Hizmeti arka uç tüketen WinForms istemci masaüstü bir uygulama ile N katmanlı uygulama üçüncü uygulamadır. Bu uygulamalar üzerinde geleneksel .NET Framework temel alır. Bu örnek uygulamaları modernized için var olan eski .NET Framework uygulamaları olması gerektiği gibi .NET Core veya ASP.NET Core kullanmayın.

Bu örnek uygulamaları modernized koduyla ikinci bir sürüme sahip ve hangi oldukça basittir. Uygulama sürümleri arasındaki en önemli fark, ikinci sürümleri dağıtım seçeneği Windows kapsayıcılar kullanma ' dir. Ayrıca var. ikinci sürümleri, Azure depolama görüntüleri yönetmek için BLOB güvenlik ve Azure Application Insights izleme ve denetim uygulamaları yönetmek için Azure Active Directory gibi birkaç eklemeler

## <a name="send-your-feedback"></a>Geri bildirim gönder

Bu kılavuz, geliştirme ve varolan .NET web uygulamaları modernizing seçeneklerinizi anlamanıza yardımcı olması için yazılmıştır. Kılavuzu ve ilgili örnek uygulamalar artmaktadır. Geri bildiriminiz Hoş Geldiniz! Bu kılavuzda nasıl daha yararlı olabileceği hakkında yorumlar varsa, lütfen göndermenize [ dotnet-architecture-ebooks-feedback@service.microsoft.com ](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

>[!div class="step-by-step"]
[Next](lift-and-shift-existing-apps-azure-iaas.md)
