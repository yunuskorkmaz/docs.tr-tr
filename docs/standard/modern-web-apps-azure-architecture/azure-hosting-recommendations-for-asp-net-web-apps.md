---
title: Azure barındırma önerileri için ASP.NET Core web uygulamaları
description: ASP.NET Core ve Azure ile modern Web uygulamaları tasarlama | Azure barındırma önerileri ASP.NET web uygulamaları için
author: ardalis
ms.author: wiwagn
ms.date: 06/06/2019
ms.openlocfilehash: 7cfb9ada4f963aa392a41cfb9f1b2df22f542d41
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758682"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>Azure barındırma önerileri için ASP.NET Core web uygulamaları

> "Satır iş liderleri her yerde uygulamaları bulut (SaaS olarak da bilinir) almak için BT departmanları atlayarak ve magazine aboneliği yaptıkları gibi bunlar için ödeme yapma. Ve hizmet artık gerekli olmadığında, abonelik sol üst köşedeki kullanılmayan hiçbir donanım ile iptal edebilirsiniz. "  
> _\- Daryl Plummer, Gartner analisti_

İnovasyonunuz ne olursa olsun, uygulamanızın ihtiyaçlarına ve mimari, Microsoft Azure bunu destekleyebilir. Barındırma gereksinimlerinize statik bir Web sitesi veya hizmetleri onlarca oluşan karmaşık bir uygulama olarak basit olabilir. ASP.NET Core tek parça web uygulamaları ve destekleyici hizmetler için önerilen çeşitli iyi bilinen yapılandırmaları vardır. Bu makalede bulunan önerileri barındırılması, uygulamalar, tek tek işlemleri veya veri olup tam kaynak türüne göre gruplandırılır.

## <a name="web-applications"></a>Web uygulamaları

Web uygulamaları ile barındırılabilir:

- App Service Web Apps

- Kapsayıcılar (çeşitli seçenekleri)

- Sanal makineler (VM)

Bu App Service Web Apps için önerilen basit kapsayıcı tabanlı uygulamaları dahil olmak üzere çoğu senaryo için yaklaşımdır. Mikro hizmet mimarileri için kapsayıcı tabanlı bir yaklaşımda göz önünde bulundurun. Uygulamanızı çalıştıran makineler hakkında daha fazla denetime ihtiyacınız varsa, Azure sanal makineler göz önünde bulundurun.

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps, web uygulamalarını barındırmak için en iyi duruma getirilmiş tam olarak yönetilen bir platform sunar. Bu Azure altyapınızla ilgilenirken, sizin işlerinize odaklanmanızı odaklanmanıza olanak tanır, çalıştırmak ve uygulamayı ölçeklendirmek gereken sunan bir hizmet (PaaS) olarak platformudur. App Service Web Apps'in temel özelliklerinden bazıları:

- DevOps iyileştirmesi (sürekli tümleştirme ve teslim, birden çok ortama, A / B testi, komut dosyası oluşturma desteği).

- Küresel ölçekli ve yüksek kullanılabilirlik.

- SaaS platformları ve şirket içi verilerinizi bağlantılar.

- Güvenlik ve uyumluluk.

- Visual Studio tümleştirmesi.

Azure App Service, çoğu web uygulaması için en iyi seçenektir. Dağıtım ve yönetim süreçleri platform ile tümleştirilmiştir, siteler hızla yüksek trafik yüklerinin altından kalkacak şekilde ölçeklendirilebilir ve yerleşik Yük Dengeleme ve trafik Yöneticisi yüksek kullanılabilirlik sağlar. Bir çevrimiçi geçiş aracı ile kolayca Azure App Service için var olan siteler, Web uygulamaları Galerisi'nden açık kaynaklı uygulama kullanma veya çerçevesi ve tercih ettiğiniz araçları kullanarak yeni bir site oluşturmak taşıyabilirsiniz. WebJobs özelliği, App Service web uygulamanıza işleme arka plan işinin eklemenizi kolaylaştırır. Mevcut bir varsa ASP.NET uygulaması yerel bir veritabanı kullanılarak şirket içinde barındırılan, bir Azure SQL veritabanı (veya tercih etmeleri durumunda, şirket içi veritabanı sunucusuna güvenli erişim) ile bir App Service Web uygulaması için uygulamayı geçirmek için bir yol yoktur.

![Önerdiğimiz geçiş stratejisi için şirket Azure App Service'e .NET uygulamaları](./media/image1-6.png)

Çoğu durumda, bir App Service Web uygulaması için yerel olarak barındırılan bir ASP.NET uygulamasından taşıma bir işlemdir. Çok az kayıpla veya hiç değişiklik uygulama gerekli olmalıdır ve Azure App Service Web Apps sunduğu çok sayıda özellikten yararlanmak hızlıca başlatabilirsiniz.

Bulut için optimize edilmemiş uygulamalarının yanı sıra Azure App Service Web Apps gibi pek çok basit tek parça (dağıtılmış olmayan) uygulama, çok sayıda ASP.NET Core uygulamaları için mükemmel bir çözümdür. Bu yaklaşımda, temel ve anlamak ve yönetmek basit mimari:

![Temel Azure Mimarisi](./media/image1-5.png)

Tek bir kaynak grubundaki kaynaklar az sayıda böyle bir uygulamayı yönetmek genellikle yeterli olur. Genellikle tek bir birim olarak dağıtılan uygulamalar yerine birçok ayrı işlemlerde, yapılan bu uygulamaları bu için iyi adaylar olan [temel mimari yaklaşım](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app). Bu yaklaşım basit mimari rağmen yine de barındırılan uygulamanın (düğüm başına daha fazla kaynakları) hem de ölçek ve out izin verir. (isteğe bağlı herhangi bir artış karşılamak için daha fazla barındırılan düğümler). Otomatik ölçeklendirme sayesinde uygulama otomatik olarak isteğe bağlı ve ortalama yük düğümlere göre uygulama barındırma düğüm sayısını ayarlamak için yapılandırılabilir.

### <a name="app-service-web-apps-for-containers"></a>App Service Web Apps için kapsayıcılar

Web apps, doğrudan barındırma desteği yanı sıra [kapsayıcılar için App Service Web Apps](https://azure.microsoft.com/services/app-service/containers/) Windows ve Linux'ta kapsayıcılı uygulamaları çalıştırmak için kullanılabilir. Bu hizmeti kullandığınızda, kolayca dağıtın ve işinizle ölçeklendirilebilen kapsayıcılı uygulamaları çalıştırın. Uygulamalar App Service Web Apps'in yukarıda listelenen tüm özelliklere sahiptir. Ayrıca, kapsayıcı desteği için Web Apps, Docker Hub, Azure Container Registry ve GitHub ile CI/CD kolaylaştırılmıştır. Azure DevOps için bir kayıt defteri değişiklikleri yayımlamak derleme ve dağıtım işlem hatları tanımlamak için kullanabilirsiniz. Bu değişiklikleri daha sonra bir hazırlama ortamında test ve kesintisiz yükseltmeleri izin vererek, dağıtım yuvalarını kullanarak üretim için otomatik olarak dağıtılır. Önceki sürümler için geri alma yalnızca kolayca yapılabilir.

Burada kapsayıcılar için Web Apps en mantıklı birkaç senaryo vardır. Windows veya Linux kapsayıcıları olup olmadığını, kapsayıcılı hale getirme, mevcut uygulamaları varsa, bunlar bu araç takımı kullanarak kolayca barındırabilirsiniz. Yalnızca kapsayıcınızı yayımlayın ve ardından bu görüntüyü en son sürümünü tercih ettiğiniz kayıt defterinizden çekme kapsayıcılar için Web Apps yapılandırın. Bulut için iyileştirilmiş bir Modeli'ne modelleri barındırma Klasik uygulamasından geçirmeye "lift- and -shift" bir yaklaşım budur.

![Kapsayıcılar için Azure Web Apps için .NET uygulamasını kapsayıcılı şirket içi geçirme](./media/image1-8.png)

Bu yaklaşım da iyi Geliştirme ekibiniz için bir kapsayıcı tabanlı geliştirme süreci taşımak durumunda çalışır. "Kapsayıcılar ile uygulama geliştirme iç döngü" kapsayıcılar ile uygulama oluşturmayı içerir. Kod de kapsayıcı yapılandırması için yapılan değişiklikler kaynak denetimine gönderilir ve otomatik bir yapı yeni kapsayıcı görüntülerini bir kayıt defteri gibi Docker Hub veya Azure Container Registry yayımlamak için sorumludur. Bu görüntüler ardından temel olarak, üretim dağıtımları yanı sıra, ek geliştirme için aşağıdaki diyagramda gösterildiği gibi kullanılır:

![Uçtan uca Docker DevOps yaşam döngüsü iş akışı](./media/image1-7.png)

Kapsayıcılar ile geliştirme, özellikle kapsayıcıları üretimde kullanıldığında, birçok avantaj sunar. Aynı kapsayıcı yapılandırması içinde derleme ve üretim sistemlerine test etmek için yerel geliştirme makinesinden çalıştığı her ortamda uygulamayı barındırmak için kullanılır. Bu makine yapılandırması veya yazılım sürümleri farklılıkları kaynaklanan hataları olasılığını önemli ölçüde azaltır. Geliştiriciler, kapsayıcı tüm işletim sistemlerinde çalıştırılabileceğinden hangi Araçlar bunlar işletim sistemi dahil olmak üzere en verimli birlikte de kullanabilirsiniz. Bazı durumlarda, yoğun kaynak kullanımı tek bir geliştirme makinesinde çalışmasını sağlayacak çok sayıda kapsayıcı içeren dağıtılmış uygulamalar olabilir. Bu senaryoda, Kubernetes ve sonraki bölümde yer alan Azure geliştirme alanları kullanarak yükseltmek mantıklıdır.

Daha büyük uygulama bölümleri kendi küçük, bağımsız ayrılır gibi *mikro Hizmetler*, ek tasarım desenleri, uygulama davranışını geliştirmek için kullanılabilir. Tek tek Hizmetleri ile doğrudan çalışmak yerine bir *API ağ geçidi* erişimi basitleştirin ve arka ucuna istemciden ayırın. Arka uçları farklı ön uçlar için ayrı bir hizmet olan tüketicilerini uyumlu bir şekilde geliştirmek hizmetler sağlar. Ortak Hizmetleri ayrı bir erişilebilir *sepet* ortak istemci bağlantısı kitaplıkları kullanarak içerebilir kapsayıcı *Büyükelçi* deseni.

![Mikro hizmetler mimarisi belirtildiği birkaç sık karşılaşılan tasarım desenleri ile örnek.](./media/image1-10.png)

[Mikro hizmet tabanlı sistemlerde oluştururken dikkate alınması gereken Tasarım desenleri hakkında daha fazla bilgi edinin.](https://docs.microsoft.com/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Service (AKS), barındırılan Kubernetes ortamınızı hızla ve kolayca kapsayıcı düzenleme uzmanlığı gerektirmeden kapsayıcıya alınmış uygulamaları dağıtmayı ve yönetmeyi yönetir. Sağlama, yükseltme ve uygulamalarınızı çevrimdışı duruma getirmeden kaynakları isteğe bağlı olarak ölçeklendirme Süren işlemlerin ve bakımın yükünü de kaldırır.

AKS, karmaşıklığı ve azure'a SORUMLULUĞUN çoğunu devrederek bir Kubernetes kümesi yönetmenin işlemsel ek yükü azaltır. Barındırılan bir Kubernetes hizmeti, sistem durumu izleme ve sizin için bakım gibi kritik görevleri Azure tanıtıcıları. Ayrıca, yalnızca aracı düğümleri için yönetici değil, kümeleri içinde ödeme. Yönetilen bir Kubernetes hizmeti olarak Aks Aşağıdakileri sağlar:

- Otomatik Kubernetes sürüm yükseltmeleri ve düzeltme eki uygulama.
- Kolay küme ölçeklendirme.
- Kendi kendini onaran barındırılan denetim düzlemi (Yöneticiler).
- Maliyet tasarrufu - yalnızca çalışan aracı havuz düğümleri için ödeme yaparsınız.

AKS kümenizde düğümleri yönetimi işlemleri Azure ile artık birçok el ile Küme yükseltme gibi görevleri gerekir. Azure Bu kritik bakım görevlerini sizin için gerçekleştirdiğinden, AKS doğrudan erişim sağlamaz (gibi SSH ile) kümeye.

AKS yararlanarak ekiplere Azure geliştirme alanları da yararlanabilirsiniz. Azure geliştirme alanları, tüm mikro hizmetler mimarisi veya AKS'de çalışan uygulama ile doğrudan çalışmak takımlar sağlayarak geliştirme ve mikro hizmet uygulamalarını hızlı bir yinelemesini odaklanmak için takımlar yardımcı olur. Azure geliştirme alanları, ayrıca rest AKS kümesi ya da diğer geliştiriciler etkilemeden yalıtım, mikro hizmetler mimarisinde bölümlerini birbirinden bağımsız olarak güncelleştirmek için bir yol sağlar.

![Azure geliştirme alanları iş akışı örneği](./media/image1-9.gif)

Azure geliştirme alanları:

- Yerel makine Kurulum zaman ve kaynak gereksinimlerini en aza indirin
- Takımlar daha hızla yineleme yapmasına izin ver
- Takım tarafından istenen tümleştirme ortamlarında sayısını azaltın
- Geliştirme ve test ederken, dağıtılmış bir sistemde belirli hizmetleri sahte gereken Kaldır

[Azure geliştirme alanları hakkında daha fazla bilgi edinin](https://docs.microsoft.com/azure/dev-spaces/about)

### <a name="azure-virtual-machines"></a>Azure sanal makineleri

App Service'te çalıştırılacak önemli değişiklikler gerektirecek bir var olan bir uygulamanız varsa, buluta geçirme basitleştirmek için sanal makineleri seçebilirsiniz. Ancak, doğru şekilde yapılandırma, güvenlik altına alma ve Vm'leri koruma çok daha fazla zaman ve Azure App Service ile karşılaştırıldığında IT uzmanlığı gerektirir. Azure sanal makineleri düşünüyorsanız, düzeltme eki uygulama, güncelleştirme ve VM ortamınızı yönetmek için gereken sürekli bir bakım çabası dikkate emin olun. Azure sanal makineleri olan altyapı (Iaas), hizmet olarak App Service PaaS olsa da. Kapsayıcılar için Web App'e bir Windows kapsayıcı olarak uygulamanızın dağıtılacağı senaryonuz için uygun bir seçenek olup da dikkate almanız gerekir.

## <a name="logical-processes"></a>Mantıksal işlemleri

Uygulama geri kalanından birbirinden ayrı mantıksal işlemlerin "sunucusuz" bir şekilde Azure işlevleri için bağımsız olarak dağıtılabilir. Azure işlevleri yalnızca çalıştırmak için uygulama veya altyapı hakkında endişelenmeden belirli bir sorun için ihtiyacınız olan kod yazmanıza olanak sağlar. Programlama dilleri, C de dahil olmak üzere çeşitli arasından seçim yapabilirsiniz\#, F\#, Node.js, Python ve PHP, eldeki en verimli dil görev için çekme etmenize imkan sağlar. Çoğu bulut tabanlı çözümler gibi kullanımınız yalnızca zaman miktarı ödeme yapar ve Azure işlevleri'nin ölçeği gerektikçe güvenebilir.

## <a name="data"></a>Veri

Uygulamanızı uygun veri sağlayıcısı için söz konusu verileri kullanabilmesi için azure, çok çeşitli veri depolama seçenekleri sunar.

İşlem, ilişkisel veri, Azure SQL veritabanı en iyi seçenektir. Yüksek performanslı okuma çoğunlukla veriler için bir Azure SQL veritabanı tarafından desteklenen bir Redis önbelleği iyi bir çözümdür.

Yapılandırılmamış JSON verilerini çeşitli şekillerde, Blobları veya tabloları, Azure depolama, SQL veritabanı sütunlarından documentdb'ye depolanabilir. Bu, DocumentDB işlevi sorgulanırken en iyi sunar ve çok sayıda sorgulama desteklemelidir, JSON tabanlı belgeleri için önerilen seçenektir.

Uygulama davranışını düzenlemek için kullanılan geçici komutu veya olay tabanlı verileri, Azure Service Bus veya Azure depolama kuyruklarını kullanabilirsiniz. Azure depolama veri yolu, daha fazla esneklik sunar ve önemsiz içinde ve uygulamalar arasında ileti için önerilen hizmetidir.

## <a name="architecture-recommendations"></a>Mimari önerileri

Uygulamanızın gereksinimlerini mimarisinin belirleyen unsurlar olmalıdır. Birçok farklı Azure hizmetlerini kullanılabilir. Doğru olanı seçme önemli bir karardır. Microsoft, yaygın senaryolar için en iyi duruma getirilmiş tipik mimariler belirlemenize yardımcı olması için başvuru mimarileri Galerisi sunar. Bir başvuru mimarisi, haritalar, uygulamanızın gereksinimleri için yakından veya daha az sunar, başlangıç noktası bulabilirsiniz.

Şekil 11-2, bir örnek başvuru mimarisini gösterir. Bu diyagramda, pazarlama için en iyi duruma getirilmiş Sitecore içerik yönetim sistemi Web sitesi için önerilen mimari bir yaklaşım açıklanmaktadır.

![](./media/image11-2.png)

**Şekil 11-1.** Sitecore pazarlama Web sitesi başvuru mimarisi.

**Başvuruları – Azure barındırma önerileri**

- Azure çözüm Architectures\
  <https://azure.microsoft.com/solutions/architecture/>

- Azure temel Web uygulaması Architecture\
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- Microservices\ için Tasarım desenleri
  <https://docs.microsoft.com/azure/architecture/microservices/design/patterns>

- Azure Geliştirici Guide\
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Web Apps overview\
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Containers\ için Web App
  <https://azure.microsoft.com/services/app-service/containers/>

- Azure Kubernetes Service'i (AKS) giriş \
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Önceki](development-process-for-azure.md)
