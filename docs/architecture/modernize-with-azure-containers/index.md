---
title: Azure Bulutu ve Windows Kapsayıcıları ile Mevcut .NET Uygulamalarını Modernize Edin (2. baskı)
description: Bu e-kitapla mevcut uygulamaları Azure bulutuna ve kapsayıcılara kaldırmayı, kaydırmayı ve modernize etmeyi öğrenin.
ms.date: 04/28/2018
ms.openlocfilehash: 9439de84dd46ac3153d951378764d10184c33a52
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628454"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>Azure bulutu ve Windows Kapsayıcıları ile mevcut .NET uygulamalarını modernize edin (2. baskı)

![Modern .NET uygulamaları kılavuzunun kapak resmi.](./media/index/web-application-guide-cover-image.png)

YAYIMLAYAN  
Microsoft Press ve Microsoft DevDiv  
Microsoft Corporation'ın bölümleri  
One Microsoft Way  
Redmond, Washington 98052-6399  

Telif hakkı © 2020 Microsoft Corporation tarafından  

Tüm hakları saklıdır. Bu kitabın içeriğinin hiçbir bölümü, yayımcının yazılı izni olmadan herhangi bir şekilde çoğaltılamaz.

Bu kitap gibi Microsoft'ta birden fazla kanal aracılığıyla kullanılabilir bir elektronik kitap (e-kitap) şeklinde ücretsiz olarak <https://dot.net/architecture>kullanılabilir.

Bu kitapla ilgili sorularınız varsa, e-posta adresine [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book).

Bu kitap "olduğu gibi" sağlanır ve yazarın görüş ve görüşlerini ifade eder. URL ve diğer Internet web sitesi referansları da dahil olmak üzere bu kitapta ifade edilen görüşler, görüşler ve bilgiler önceden haber verilmeden değişebilir.

Burada tarif edilen bazı örnekler yalnızca açıklama için sağlanmıştır ve kurgusaldır. Gerçek bir ilişki veya bağlantı amaçlanmamıştır veya böyle bir bağlantı olduğu sonucuna varılmamalıdır.

Microsoft ve "Ticari <https://www.microsoft.com> Markalar" web sayfasında listelenen ticari markalar, Microsoft şirketler grubunun ticari markalarıdır. Diğer tüm markalar ilgili sahiplerinin mülkiyetindedir.

Yazar:
> **Cesar de la Torre**, Sr. PM, .NET Ürün Ekibi, Microsoft Corp.

Katılımcılar ve gözden geçirenler:
> **Scott Hunter**, İş Ortağı Direktörü PM, .NET ekibi, Microsoft  
> **Paul Yuknewicz**, Baş PM Yöneticisi, Visual Studio Tools ekibi, Microsoft  
> **Lisa Guthrie**, Sr. PM, Visual Studio Tools ekibi, Microsoft  
> **Ankit Asthana**, Baş PM Yöneticisi, .NET ekibi, Microsoft  
> **Unai Zorrilla**, Geliştirici Kurşun, Düz Kavramlar  
> **Javier Valero**, Grupo Solutio'da Operasyon Müdürü  

## <a name="introduction"></a>Giriş

When you decide to modernize your web applications or services and move them to the cloud, you don't necessarily have to fully rearchitect your apps. Mikro hizmetler gibi gelişmiş bir yaklaşım kullanarak bir uygulamayı yeniden yapılandırış, maliyet ve zaman kısıtlamaları nedeniyle her zaman bir seçenek değildir. Uygulama türüne bağlı olarak, bir uygulamayı yeniden yapılandırmak da gerekli olmayabilir. Kuruluşunuzun bulut geçiş stratejisinin maliyet etkinliğini optimize etmek için, işletmenizin gereksinimlerini ve uygulamalarınızın gereksinimlerini göz önünde bulundurmanız önemlidir. Şunları belirlemeniz gerekir:

- Hangi uygulamalar bir dönüşüm veya yeniden architecting gerektirir.

- Hangi uygulamaların yalnızca kısmen modernize edilmesi gerekir.

- Hangi uygulamaları doğrudan buluta "kaldırıp kaydırabilirsiniz".

## <a name="about-this-guide"></a>Bu kılavuz hakkında

Bu kılavuz, öncelikle mevcut Microsoft .NET Framework web veya hizmet odaklı uygulamaların ilk modernizasyonuna odaklanır, bu da bir iş yükünü uygulamanın kodunu önemli ölçüde değiştirmeden daha yeni veya daha modern bir ortama taşıma eylemi anlamına gelir ve temel mimari.

Bu kılavuz, Windows Kapsayıcıları ve Azure'da Windows Kapsayıcılarını destekleyen ilgili bilgi işlem platformları gibi belirli bir dizi yeni teknoloji ve yaklaşım kullanarak uygulamalarınızı buluta taşımanın ve uygulamaları kısmen modernize etmenin avantajlarını da vurgular.

## <a name="path-to-the-cloud-for-existing-net-applications"></a>Varolan .NET uygulamaları için buluta giden yol

Kuruluşlar genellikle uygulamaları için alabilecekleri çeviklik ve hız için buluta taşınmayı seçerler. Bulutta, şirket içi sunucular kurmak için gereken haftalarla karşılaştırıldığında, binlerce sunucu (VM) dakika içinde ayarlayabilirsiniz.

Uygulamaları buluta geçirmek için tek bir, tek boyutlu tüm strateji yoktur. Sizin için doğru geçiş stratejisi, kuruluşunuzun gereksinimlerine ve önceliklerine ve geçiş yaptığınız uygulamaların türüne bağlıdır. Tüm uygulamalar, bir hizmet[(PaaS)](https://azure.microsoft.com/overview/what-is-paas/)modeli olarak bir platforma geçme veya [bulut tabanlı](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) bir uygulama modeli geliştirme yatırımı garanti etmez. Çoğu durumda, işletme gereksinimlerinize bağlı olarak varlıklarınızı buluta taşımak için aşamalı veya artımlı bir yaklaşım benimseebilirsiniz.

Kuruluş için en iyi uzun vadeli çeviklik ve değere sahip modern uygulamalar için *bulut yerel* uygulama mimarilerine yatırım yapmaktan yararlanabilirsiniz. Ancak, var olan veya eski varlıklar olan uygulamalar için anahtar, önemli faydalar elde etmek için buluta taşınırken en az zaman ve para harcamaktır (yeniden architecting veya kod değişikliği yok).

Şekil 1-1, varolan .NET uygulamalarını artımlı aşamalarda buluta taşıdığınızda alabileceğiniz olası yolları gösterir.

 ![Mevcut .NET uygulamaları ve hizmetleri için modernizasyon yolları](./media/image1-1.png)

**Şekil 1-1**. Mevcut .NET uygulamaları ve hizmetleri için modernizasyon yolları

Her geçiş yaklaşımının farklı yararları ve kullanma nedenleri vardır. Uygulamaları buluta geçirdiğinizde tek bir yaklaşım seçebilir veya birden çok yaklaşımdan belirli bileşenleri seçebilirsiniz. Bireysel uygulamalar tek bir yaklaşım veya olgunluk durumu ile sınırlı değildir. Örneğin, ortak bir karma yaklaşım, buluttaki bazı şirket içi bileşenlere ve diğer bileşenlere sahip olur.

Her uygulama olgunluk düzeyi için tanım ve kısa açıklama şunlardır:

**Düzey 1: Bulut Altyapısına Hazır** uygulamalar: Bu geçiş yaklaşımında, mevcut şirket içi uygulamalarınızı hizmet[(IaaS)](https://azure.microsoft.com/overview/what-is-iaas/)platformu olarak bir altyapıya geçirmeniz veya yeniden barındırmanız yeterlidir. Uygulamalarınız daha önce olduğu gibi hemen hemen aynı kompozisyona sahiptir, ancak şimdi bunları buluttaki VM'lere dağıtabilirsiniz.
Bu basit geçiş türü genellikle endüstride "Lift & Shift" olarak bilinir.

**Düzey 2: Bulut Optimize Edilmiş** uygulamalar: Bu düzeyde ve yine de önemli kodları yeniden tasarlayıp değiştirmeden, kapsayıcılar ve bulut tarafından yönetilen ek hizmetler gibi modern teknolojilerle uygulamanızı bulutta çalıştırmadan ek avantajlar elde edebilirsiniz. Kurumsal geliştirme işlemleri (DevOps) süreçlerinizi iyileştirerek uygulamalarınızın daha hızlı gönderilme çevikliğini artırırsınız. Bunu Docker Engine'i temel alan Windows Kapsayıcıları gibi teknolojileri kullanarak elde elabilirsiniz. Kapsayıcılar, birden çok aşamada dağıtıyaptığınızda uygulama bağımlılıklarının neden olduğu sürtünmeyi kaldırır. Bu vade modelinde, veritabanları, hizmet olarak önbellek, izleme ve sürekli tümleştirme/sürekli dağıtım (CI/CD) boru hatlarıyla ilgili bulut tarafından yönetilen ek hizmetleri kullanırken IaaS veya PaaS'a kapsayıcılar dağıtabilirsiniz.

Üçüncü olgunluk düzeyi buluttaki nihai hedeftir, ancak bu kılavuzun ana odak noktası değil, birçok uygulama için isteğe bağlıdır:

**Düzey 3: Bulut-Yerel** uygulamalar: Bu geçiş yaklaşımı genellikle iş gereksinimine bağlıdır ve görev açısından kritik uygulamalarınızı modernize etme hedeflenir. Bu düzeyde, uygulamalarınızı PaaS bilgi işlem platformlarına taşımak için PaaS hizmetlerini kullanırsınız. Uygulamaları uzun vadeli çeviklikle geliştirmek ve yeni sınırlara ölçeklendirmek için [bulut yerel](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) uygulamaları ve mikro hizmetler mimarisini uygularsınız. Bu tür modernizasyon genellikle bulut için özel olarak mimaring gerektirir. Özellikle bulut tabanlı uygulamaya ve mikro hizmet tabanlı modellere geçdiğinizde, genellikle yeni kod yazılmalıdır. Bu yaklaşım, yekpare ve şirket içi uygulama ortamınızda elde etmesi zor avantajlar elde etmenize yardımcı olabilir.

Tablo 1-1, her bir göç veya modernleşme yaklaşımının ana yararlarını ve nedenlerini açıklamaktadır.

| **Bulut Altyapısına Hazır** <br /> *Lift and shift* | **Bulut Optimize Edile** <br /> *Modernleştir* | **Bulut-Yerli** <br /> *Modernleştirin, yeniden tasarla ve yeniden yazma* |
|---|---|---|
| **Uygulamanın bilgi işlem hedefi** |
| Azure'da VM'lere dağıtılan uygulamalar | Azure Uygulama Hizmeti, Azure Kapsayıcı Örneği (ACI), kapsayıcılı VM'ler veya AKS 'ye (Azure Kubernetes Hizmeti) dağıtılan monolitik veya N Katmanlı uygulamalar | Azure Kubernetes Hizmeti (AKS) ve/veya sunucusuz mikro hizmetlerde Azure İşlevlerini temel alan kapsayıcı mikro hizmetler. |
| **Veri hedefi** |
| VM'deki SQL veya herhangi bir ilişkisel veritabanı | Azure SQL Veritabanı Yönetilen Örnek veya buluttaki başka bir yönetilen veritabanı. | Azure SQL Veritabanı, Azure Cosmos DB veya buluttaki başka bir yönetilen veritabanını temel alan mikro hizmet başına para cezası veri tabanları |
| **Avantaj -ları**|
| <li>Yeniden mimarlık yok, yeni kod yok <li> Hızlı geçiş için en az çaba <li> Azure'da desteklenen en az yaygın payda <li> Temel kullanılabilirlik garantileri <li> Buluta geçtikten sonra, daha da modernizasyonu | <li> Yeniden mimarlık yok <li> En az kod/config değişiklikleri <li> Konteynerler nedeniyle serbest bırakmak için geliştirilmiş dağıtım ve DevOps çeviklik <li> Daha fazla yoğunluk ve daha düşük dağıtım maliyetleri <li> Uygulamaların ve bağımlılıkların taşınabilirliği <li> Ev sahibi hedeflerin esnekliği: PaaS yaklaşımları veya IaaS | <li> Bulutun mimarı, buluttan en iyi avantajları elde elabilirsiniz, ancak yeni kod gereklidir <li> Microservices bulut ait yaklaşımlar <li> Modern görev açısından kritik uygulamalar, buluta dayanıklı hiper ölçeklenebilir <li> Tam yönetilen hizmetler <li> Ölçek için optimize edilmiş <li> Alt sisteme göre otonom çeviklik için optimize edilerek <li> Dağıtım ve DevOps üzerine yerleşik |
| **Zorluklar** |
| <li> İşletme giderindeki kayma veya veri merkezlerini kapatma dışında daha küçük bulut değeri <li> Az yönetilir: Hiçbir işletim sistemi veya middleware yama; Terraform, Spinnaker veya Puppet gibi altyapı çözümlerini kullanabilir | <li> Konteynerleme, geliştiriciler ve BT İşlemleri için öğrenme eğrisinde ek bir adımdır <li> DevOps ve CI / CD boru hatları genellikle bu yaklaşım için 'bir zorunluluktur'. Kuruluşun kültüründe şu anda mevcut değilse, ek bir sorun olabilir| <li> Bulut yerel uygulamaları ve mikro hizmet mimarileri için yeniden mimari gerektirir ve genellikle modernizasyon (artan zaman ve bütçe) önemli kod yeniden düzenleme veya yeniden yazma gerektirir|
> **Tablo 1-1.** Mevcut .NET uygulamaları ve hizmetleri için modernizasyon yollarının avantajları ve zorlukları

### <a name="key-technologies-and-architectures-by-maturity-level"></a>Vade düzeyine göre temel teknolojiler ve mimariler

.NET Framework uygulamaları başlangıçta 2001 sonlarında yayımlanan .NET Framework sürüm 1.0 ile başlamıştır. Daha sonra şirketler yeni sürümlere (2.0, 3.5 ve .NET 4.x gibi) yöneldi. Bu uygulamaların çoğu Windows Server ve Internet Information Server (IIS) üzerinde çalıştırDı ve SQL Server, Oracle, MySQL veya diğer RDBMS gibi ilişkisel bir veritabanı kullandı.

Mevcut .NET uygulamalarının çoğu günümüzde .NET Framework 4.x,hatta .NET Framework 3.5'e dayanıyor olabilir ve ASP.NET MVC, ASP.NET Web Forms, ASP.NET Web API, Windows Communication Foundation (WCF), ASP.NET SignalR ve ASP.NET Web Sayfaları gibi web çerçevelerini kullanabilir . Kurulan bu .NET Framework teknolojileri Windows'a bağlıdır. Bu bağımlılık, yalnızca eski uygulamaları geçirip uygulama altyapınızda en az değişiklik yapmak istiyorsanız göz önünde bulundurmanız önemlidir.

Şekil 1-2, üç bulut olgunluk düzeyinin her birinde kullanılan birincil teknolojileri ve mimari stilleri gösterir:

![Mevcut .NET web uygulamalarını modernize etmek için her bir olgunluk düzeyi için birincil teknolojiler](./media/image1-2.png)

**Şekil 1-2.** Mevcut .NET web uygulamalarını modernize etmek için her bir olgunluk düzeyi için birincil teknolojiler

Şekil 1-2 en yaygın senaryoları vurgular, ancak mimari söz konusu olduğunda birçok karma ve karışık varyasyon mümkündür. Örneğin, olgunluk modelleri yalnızca varolan web uygulamalarındaki yekpare mimariler için değil, aynı zamanda hizmet yönlendirmesi, N-Tier ve diğer mimari stil varyasyonları için de geçerlidir. Bir veya başka bir mimari türü ve ilgili teknolojilerüzerinde daha yüksek odak veya yüzde, uygulamalarınızın genel olgunluk düzeyini belirler.

Modernizasyon sürecindeki her olgunluk düzeyi aşağıdaki temel teknolojiler ve yaklaşımlarla ilişkilidir:

- **Bulut Altyapısına Hazır (yeniden** barındırma veya temel kaldırma & kayması): İlk adım olarak, birçok kuruluş yalnızca bulut geçiş stratejisini hızlı bir şekilde yürütmek ister. Bu durumda, uygulamalar yeniden barındırılır. Çoğu yeniden barındırma, [Azure Site Kurtarma](https://azure.microsoft.com/services/site-recovery/) ve [Azure Veritabanı Geçiş Hizmeti](https://azure.microsoft.com/campaigns/database-migration/)gibi bulut araçlarına bağlı olarak Azure'a geçişte size yardımcı olmak için gereken kılavuz, öngörüve mekanizmaları sağlayan bir hizmet olan [Azure Geçir'i](https://aka.ms/azuremigrate)kullanarak otomatikleştirilebilir. Eski uygulamaları buluta taşıdığınızda varlıklarınız hakkındaki altyapı ayrıntılarını öğrenebilmeniz için yeniden barındırmayı el ile de ayarlayabilirsiniz. Örneğin, uygulamalarınızı azure'da küçük yapılandırma değişiklikleriyle çok az değişiklikle VM'lere taşıyabilirsiniz. Bu durumda ağ, özellikle Azure'da sanal ağlar oluşturuyorsanız, şirket içi ortama benzer.

- **Bulut Tarafından Optimize Edilmiş** (Yönetilen Hizmetler ve Windows Kapsayıcıları): Bu model, uygulamanın temel mimarisini değiştirmeden buluttan bazı önemli avantajlar elde etmek için birkaç önemli dağıtım optimizasyonu yapmakla ilgilidir. Buradaki temel adım, varolan .NET Framework uygulamalarınıza [Windows Kapsayıcıları](https://docs.microsoft.com/virtualization/windowscontainers/about/) desteği eklemektir. Bu önemli adım (konteynerleştirme) koda dokunmayı gerektirmez, bu nedenle genel kaldırma ve kaydırma çabası hafiftir. Docker [için](https://www.docker.com/)araçları ile [Image2Docker](https://github.com/docker/communitytools-image2docker-win) veya Visual Studio gibi araçları kullanabilirsiniz. Visual Studio, ASP.NET uygulamaları ve Windows Kapsayıcıları görüntüleri için otomatik olarak akıllı varsayılanları seçer. Bu araçlar hem hızlı bir iç döngü hem de kapsayıcıları Azure'a getirmek için hızlı bir yol sunar. Birden çok ortama dağıtıladiğinizde çevikliğiniz artar.
Daha sonra üretime geçmek için Windows Kapsayıcılarınızı [Kapsayıcılar için Azure Web Uygulamasına,](https://azure.microsoft.com/services/app-service/containers/) [Azure Kapsayıcı Örneklerine (ACI)](https://azure.microsoft.com/services/container-instances/)ve Windows Server 2016'lı Azure VM'lerine ve iaaS yaklaşımını tercih ederseniz kapsayıcılara dağıtabilirsiniz. Daha karmaşık çoklu kapsayıcı uygulamaları için [Azure Kubernetes Hizmeti (AKS/ACS)](https://azure.microsoft.com/services/container-service/)gibi orkestratörleri kullanmayı düşünün.

Bu ilk modernizasyon sırasında, [Azure Uygulama Öngörüleri](https://docs.microsoft.com/azure/application-insights/app-insights-overview)gibi araçlarla izleme gibi buluttan varlıklar da ekleyebilirsiniz; [Azure DevOps Hizmetleri](https://azure.microsoft.com/services/devops/)ile uygulama yaşam döngüleriniz için CI/CD boru hatları; ve Azure'da kullanılabilen daha birçok veri kaynağı hizmeti. Örneğin, başlangıçta geleneksel [ASP.NET Web Formları](https://www.asp.net/web-forms) veya ASP.NET [MVC](https://www.asp.net/mvc)kullanılarak geliştirilen yekpare bir web uygulamasını değiştirebilirsiniz, ancak şimdi Windows Kapsayıcıları'nı kullanarak dağıtabilirsiniz. Windows Kapsayıcıları kullandığınızda, uygulamanızın temel mimarisini değiştirmeden verilerinizi [Azure SQL Veritabanı Yönetilen Örneği'ndeki](https://docs.microsoft.com/azure/sql-database/)bir veritabanına da geçirmelisiniz.

- **Bulut-Yerel**: Tanıtılan gibi, geliştirilebilen ve dağıtılabilen farklı mikro hizmetler üzerinde çalışan birden fazla bağımsız geliştirme ekibiyle büyük ve karmaşık uygulamaları hedeflediğinizde [bulut açi](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications) uygulamalarını tasarlamalısınız. Ayrıca, mikrohizmet başına granüler ve bağımsız ölçeklenebilirlik nedeniyle. Bu mimari yaklaşımlar çok önemli zorluklarla ve karmaşıklıklarla karşı karşıyadır, ancak bulut PaaS ve [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (yönetilen Kubernetes) ve [Azure Fonksiyonları](https://azure.microsoft.com/services/functions/) gibi orkestratörleri sunucusuz bir yaklaşım için kullanarak büyük ölçüde basitleştirilmiş olabilir. Tüm bu yaklaşımlar (mikro hizmetler ve Serverless gibi) genellikle bulutiçin mimar ve belirli PaaS platformlarına uyarlanmış yeni kod yazmak veya mikro hizmetler gibi belirli mimarileri hizalayan kod gerektirir.

Şekil 1-3, her vade düzeyi için kullanabileceğiniz dahili teknolojileri gösterir:

![Her modernizasyon olgunluk düzeyi için iç teknolojiler](./media/image1-3.png)

**Şekil 1-3.** Her modernizasyon olgunluk düzeyi için iç teknolojiler

## <a name="lift-and-shift-scenario"></a>Kaldırma ve kaydırma senaryosu

Kaldırma ve kaydırma geçişleri için, uygulama senaryolarınızda birçok farklı kaldırma ve kaydırma varyasyonunu kullanabileceğinizi unutmayın. Yalnızca uygulamanızı yeniden barındırArsanız, bulutta yalnızca uygulamanız ve veritabanı sunucunuz için VM'leri kullandığınız Şekil 1-4'te gösterilen senaryo gibi bir senaryonuz olabilir.

![Bulutta saf bir IaaS senaryosu örneği](./media/image1-4.png)

**Şekil 1-4**. Bulutta saf bir IaaS senaryosu örneği

## <a name="modernization-scenarios"></a>Modernizasyon senaryoları

Modernizasyon senaryoları için, yalnızca bu olgunluk düzeyinden öğeleri kullanan saf bir Bulut Optimize edilmiş uygulamanız olabilir. Veya, Şekil 1-5'te olduğu gibi Bulut Altyapısına Hazır bazı öğeleri ve Bulut Optimize Edilmiş diğer öğelerle ("seç ve seç" veya karma model) bir ara durum uygulamanız olabilir.

![Örnek "seç ve seç" senaryosu, IaaS, DevOps ve kapsayıcılaştırma varlıkları veritabanı ile](./media/image1-5.png)

**Şekil 1-5.** Örnek "seç ve seç" senaryosu, IaaS, DevOps ve kapsayıcılaştırma varlıkları veritabanı ile

Ardından, varolan birçok .NET Framework uygulamasının geçiş için ideal bir senaryo olarak, az çalışmadan önemli avantajlar elde etmek için Bulut Tarafından Optimize Edilmiş bir uygulamaya geçiş olabilirsiniz. Bu yaklaşım aynı zamanda sizi bulut-yerel için olası bir gelecekteki evrim olarak ayarlar. Şekil 1-6 bir örnek gösterir.

![Windows Kapsayıcıları ve yönetilen hizmetlerle Bulut Tarafından Optimize Edilmiş uygulamalar senaryosuna örnek](./media/image1-6.png)

**Şekil 1-6.** Windows Kapsayıcıları ve yönetilen hizmetlerle Bulut Tarafından Optimize Edilmiş uygulamalar senaryosuna örnek

Daha da ileri giderek, belirli senaryolar için birkaç mikro hizmet ekleyerek mevcut Bulut Için Optimize edilmiş uygulamanızı genişletebilirsiniz. Bu, sizi kısmen mevcut kılavuzun ana odak noktası olmayan Bulut-Yerel modeli düzeyine taşır.

## <a name="what-this-guide-does-not-cover"></a>Bu kılavuzun kapsamadığı

Bu kılavuz, Şekil 1-7'de gösterildiği gibi örnek senaryoların belirli bir alt kümesini kapsar. Bu kılavuz yalnızca kaldırma ve kaydırma senaryolarına ve nihayetinde Bulut Için Optimize Edilmiş modele odaklanır. Bulut Tarafından Optimize Edilen modelde, Bir .NET Framework uygulaması Windows Kapsayıcıları kullanılarak ve izleme ve CI/CD ardışık hatları gibi ek bileşenler kullanılarak modernize edilir. Her bileşen, uygulamaları buluta daha hızlı ve çevik bir şekilde dağıtmak için çok önemlidir.

![Bulut-Yerel bu kılavuzda yer alan değil](./media/image1-7.png)

**Şekil 1-7.** Bulut-Yerel bu kılavuzda yer alan değil

Bu kılavuzun odak noktası özeldir. Mevcut .NET uygulamalarınızın yeniden architectaolmadan ve kod değişikliği olmadan kaldırılması ve kaydırılması için izleyebileceğiniz yolu gösterir. Sonuç olarak, uygulamanızın Bulut Tarafından Optimize Edilebildiğini gösterir.

Bu kılavuz, mikro hizmetler mimarisine nasıl evrececeğiniz gibi Bulut-Yerel uygulamaları nasıl oluşturabileceğinizi göstermez. Uygulamalarınızı yeniden architect olarak yeniden oluşturmak veya mikro hizmetlere dayalı yepyeni uygulamalar oluşturmak için e-kitap [.NET Microservices: Containerized .NET uygulamaları için mimariye](https://aka.ms/microservicesebook)bakın.

### <a name="additional-resources"></a>Ek kaynaklar

- **Microsoft platformu ve araçları ile Containerized Docker uygulama yaşam döngüsü** (indirilebilir e-kitap) \
  <https://aka.ms/dockerlifecycleebook>

- **.NET Microservices: Konteynerleştirilmiş .NET uygulamaları için mimari** (indirilebilir e-kitap) \
  <https://aka.ms/microservicesebook>

- ASP.NET Core ve Azure (indirilebilir e-kitap) **ile modern web uygulamalarının mimarlığı** \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>Bu kılavuzu kimler kullanmalı?

Bu kılavuz, gönderim ve serbest uygulamalarda daha iyi çeviklik için .NET Framework'e dayalı mevcut ASP.NET web uygulamalarını veya WCF hizmetlerini modernize etmek isteyen geliştiriciler ve çözüm mimarları için yazılmıştır.

Bu kılavuzu, windows kapsayıcılarını kullanarak ve Microsoft Azure'u kullanırken buluta dağıtarak elde edebileceğiniz avantajlara genel bir bakış isteyen kurumsal bir mimar veya geliştirme müşteri adayı/yöneticisi gibi teknik bir karar vericiyseniz de yararlı bulabilirsiniz.

## <a name="how-to-use-this-guide"></a>Bu kılavuz nasıl kullanılır?

Bu kılavuz, mevcut uygulamalarınızı modernize etmek isteyebileceğin "neden"-neden ve uygulamalarınızı buluta taşırken Windows Kapsayıcıları'nı kullanmaktan elde ettiğiniz belirli faydaları ele alır. Kılavuzun ilk birkaç bölümündeki içerik, genel bir bakış isteyen, ancak uygulama ve teknik, adım adım ayrıntılara odaklanması gerekmeyen mimarlar ve teknik karar vericiler için tasarlanmıştır.

Bu kılavuzun son bölümü, belirli dağıtım senaryolarına odaklanan birden çok gözden geçirme işlemi sunar. Bu kılavuz, senaryoları özetlemek ve bunların avantajlarını vurgulamak için gözden geçirmelerin daha kısa sürümlerini sunar. Tam walkthroughs kurulum ve uygulama ayrıntıları ayrıntılı ve ilgili örnek uygulamalar (sonraki bölümde ele) ikamet aynı ortak [GitHub repo](https://github.com/dotnet-architecture/eShopModernizing) [wiki mesaj](https://github.com/dotnet-architecture/eShopModernizing/wiki) kümesi olarak yayınlanır. Son bölüm ve GitHub üzerinde adım adım wiki walkthroughs uygulama ayrıntıları odaklanmak isteyen geliştiriciler ve mimarlar için daha fazla ilgi olacaktır.

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>Eski uygulamaları modernize etmek için örnek uygulamalar: eShopModernizing

GitHub'daki [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) repo, eski yekpare web uygulamalarını simüle eden iki örnek uygulama sunar. Bir web uygulaması ASP.NET MVC kullanılarak geliştirilmiştir; Ikinci web uygulaması ASP.NET Web Forms kullanılarak geliştirilmiştir ve üçüncü uygulama bir WCF hizmeti arka uç tüketen bir WinForms istemci masaüstü uygulaması ile bir N-Tier uygulamasıdır. Tüm bu uygulamalar geleneksel .NET Framework'e dayanmaktadır. Bu örnek uygulamalar .NET Core veya ASP.NET Core'u, modernize edilecek mevcut/eski .NET Framework uygulamaları olması gerektiği için kullanmaz.

Bu örnek uygulamaların, modernize edilmiş koda sahip ve oldukça basit olan ikinci bir sürümü vardır. Uygulama sürümleri arasındaki en önemli fark, ikinci sürümlerin dağıtım seçimi olarak Windows Kapsayıcıları kullanmasıdır. Ayrıca, görüntüleri yönetmek için Azure Depolama Blobs, güvenliği yönetmek için Azure Active Directory ve uygulamaları izlemek ve denetlemek için Azure Uygulama İstatistikleri gibi ikinci sürümlere birkaç ekleme de vardır.

## <a name="send-your-feedback"></a>Geri bildiriminizi gönderin

Bu kılavuz, varolan .NET web uygulamalarını geliştirme ve modernize etme seçeneklerinizi anlamanıza yardımcı olmak için yazılmıştır. Kılavuz ve ilgili örnek uygulamalar gelişmektedir. Geri bildiriminiz bizim için çok önemlidir! Bu kılavuzun nasıl daha yararlı olabileceği hakkında yorumlarınız [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)varsa, lütfen lütfen .

>[!div class="step-by-step"]
>[Sonraki](lift-and-shift-existing-apps-azure-iaas.md) <!-- Next Chapter -->
