---
title: ASP.NET Core web uygulamaları için Azure barındırma önerileri
description: ASP.NET Core ve Azure ile Mimar Modern Web Uygulamaları | ASP.NET web uygulamaları için Azure barındırma önerileri
author: ardalis
ms.author: wiwagn
ms.date: 06/06/2019
ms.openlocfilehash: 5587b8b20da8a6801d77b722e9c3326f6e695574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416722"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>ASP.NET Core web uygulamaları için Azure barındırma önerileri

> "Her yerdeki iş dünyası liderleri, buluttan (SaaS olarak da bilinir) uygulama almak için BT departmanlarını atlıyor ve dergi aboneliği gibi onlar için ödeme yapıyor. Ve hizmete artık gerek kalmadığında, köşede kullanılmayan hiçbir ekipman olmadan aboneliği iptal edebilirler."  
> _\-Daryl Plummer, Gartner analisti_

Uygulamanızın gereksinimleri ve mimarisi ne olursa olsun, Microsoft Azure bu uygulamayı destekleyebilir. Barındırma ihtiyaçlarınız statik bir web sitesi veya düzinelerce hizmetten oluşan sofistike bir uygulama kadar basit olabilir. Core monolitik web uygulamaları ve destekleyici hizmetler ASP.NET için, tavsiye edilen birkaç iyi bilinen yapılandırmaları vardır. Bu makaledeki öneriler, tam uygulamalar, bireysel işlemler veya veriler olsun, barındırılacak kaynağın türüne göre gruplandırılır.

## <a name="web-applications"></a>Web uygulamaları

Web uygulamaları şu şekilde barındırılabilir:

- Uygulama Hizmeti Web Uygulamaları

- Kapsayıcılar (birkaç seçenek)

- Sanal Makineler (VM)

Bunlardan, App Service Web Apps basit kapsayıcı tabanlı uygulamalar da dahil olmak üzere çoğu senaryo için önerilen yaklaşımdır. Mikro hizmet mimarileri için kapsayıcı tabanlı bir yaklaşım düşünün. Uygulamanızı çalıştıran makineler üzerinde daha fazla denetime ihtiyacınız varsa, Azure Sanal Makineleri'ni düşünün.

### <a name="app-service-web-apps"></a>Uygulama Hizmeti Web Uygulamaları

App Service Web Apps, web uygulamalarını barındırmak için optimize edilmiş tam olarak yönetilen bir platform sunar. Azure uygulamayı çalıştırmak ve ölçeklendirmek için gereken altyapıyla ilgilenirken, iş mantığınıza odaklanmanızı sağlayan bir hizmet (PaaS) sunan bir platformdur. App Service Web Apps'ın bazı temel özellikleri:

- DevOps optimizasyonu (sürekli tümleştirme ve teslimat, birden çok ortam, A/B testi, komut dosyası desteği).

- Küresel ölçek ve yüksek kullanılabilirlik.

- SaaS platformlarına bağlantılar ve şirket içi verileriniz.

- Güvenlik ve uyumluluk.

- Visual Studio entegrasyonu.

Azure App Service, çoğu Web uygulaması için en iyi seçenektir. Dağıtım ve yönetim süreçleri platform ile tümleştirilmiştir, siteler hızla yüksek trafik yüklerinin altından kalkacak şekilde ölçeklendirilebilir ve yerleşik yük dengeleme ve trafik yöneticisi yüksek kullanılabilirlik sağlar. Mevcut siteleri çevrimiçi geçiş aracı ile kolayca Azure App Service’a taşıyabilir, Web Uygulaması Galerisi'nden açık kaynaklı bir uygulamayı kullanabilir veya istediğiniz çerçeve ve araçları kullanarak yeni bir site oluşturabilirsiniz. WebJobs özelliği, App Service Web uygulamanıza arka plan iş işlemleri eklemeyi kolaylaştırır. Yerel bir veritabanı nı kullanarak şirket içinde barındırılan varolan bir ASP.NET uygulamanız varsa, uygulamayı Azure SQL Veritabanı na sahip bir App Service Web App Uygulamasına geçirmenin (veya tercih edilirse şirket içi veritabanı sunucunuza güvenli erişim) açık bir yol vardır.

![Şirket içi .NET uygulamaları için Azure Uygulama Hizmeti için önerilen geçiş stratejisi](./media/image1-6.png)

Çoğu durumda, yerel olarak barındırılan bir ASP.NET uygulamasından App Service Web App'e geçmek basit bir işlemdir. Uygulamanın kendisinde çok az veya hiç değişiklik yapılması gerekmemelidir ve Azure App Service Web Apps'ın sunduğu birçok özellikten hızla yararlanmaya başlayabilir.

Azure App Service Web Apps, bulut için optimize edilmeyen uygulamalara ek olarak, birçok ASP.NET Core uygulaması gibi birçok basit tek litik (dağıtılmamış) uygulama için mükemmel bir çözümdür. Bu yaklaşımda, mimari nin anlaşılması ve yönetilmesi temel ve basittir:

![Temel Azure mimarisi](./media/image1-5.png)

Tek bir kaynak grubundaki az sayıda kaynak genellikle böyle bir uygulamayı yönetmek için yeterlidir. Genellikle birçok ayrı işlemden oluşan uygulamalar yerine tek bir birim olarak dağıtılan uygulamalar, bu [temel mimari yaklaşım](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app)için iyi adaylardır. Mimari olarak basit olsa da, bu yaklaşım yine de barındırılan uygulamanın talepteki herhangi bir artışı karşılamak için hem (düğüm başına daha fazla kaynak) hem de dışarı (daha fazla barındırılan düğüm) ölçeklendirmesine olanak tanır. Otomatik ölçekle uygulama, isteğe ve düğümler üzerindeki ortalama yüke göre uygulamayı barındıran düğüm sayısını otomatik olarak ayarlanacak şekilde yapılandırılabilir.

### <a name="app-service-web-apps-for-containers"></a>Kapsayıcılar için Uygulama Hizmeti Web Uygulamaları

Web uygulamalarını doğrudan barındırma desteğine ek olarak, [Kapsayıcılar için App Service Web Apps,](https://azure.microsoft.com/services/app-service/containers/) Windows ve Linux'ta kapsayıcı uygulamaları çalıştırmak için de kullanılabilir. Bu hizmeti kullanarak, işletmenizle ölçeklendirilebilen kapsayıcı uygulamaları kolayca dağıtabilir ve çalıştırabilirsiniz. Uygulamalar, yukarıda listelenen App Service Web Apps'ın tüm özelliklerine sahiptir. Ayrıca, Kapsayıcılar için Web Apps, Docker Hub, Azure Konteyner Kayıt Defteri ve GitHub ile aerodinamik CI/CD'yi destekler. Kayıt defterinde değişiklik yayımlayan yapı ve dağıtım ardışık hatlarını tanımlamak için Azure DevOps'leri kullanabilirsiniz. Bu değişiklikler daha sonra bir evreleme ortamında sınanabilir ve dağıtım yuvalarını kullanarak otomatik olarak üretime dağıtılabilir ve sıfır kapalı kalma süresi yükseltmelerine izin verir. Önceki sürümlere geri alma gibi kolayca yapılabilir.

Kapsayıcılar için Web Uygulamaları'nın en mantıklı olduğu birkaç senaryo vardır. İster Windows ister Linux kapsayıcılarında olsun, konteynerleştirebileceğiniz varolan uygulamalarınız varsa, bunları bu araç kümesini kullanarak kolayca barındırabilirsiniz. Kapsayıcınızı yayımlayın ve ardından seçtiğiniz kayıt defterinizden bu resmin en son sürümünü çekmek için Kapsayıcılar için Web Uygulamalarını yapılandırın. Bu, klasik uygulama barındırma modellerinden bulut için optimize edilmiş bir modele geçiş için bir "kal ve değiştir" yaklaşımıdır.

![Kapsayıcılı konteynırı şirket içi .NET uygulamasını Kapsayıcılar için Azure Web Apps'a geçirin](./media/image1-8.png)

Geliştirme ekibiniz kapsayıcı tabanlı bir geliştirme sürecine geçebiliyorsa, bu yaklaşım da iyi çalışır. Kapsayıcılarla uygulama geliştirmenin "iç döngüsü", uygulamanın kapsayıcılarla oluşturulmasını içerir. Kodda ve kapsayıcı yapılandırmasına yapılan değişiklikler kaynak denetimine itilir ve otomatik bir yapı yeni kapsayıcı görüntülerini Docker Hub veya Azure Kapsayıcı Kayıt Defteri gibi bir kayıt defterine yayımlamasorumlusundan sorumludur. Bu görüntüler daha sonra ek geliştirmenin yanı sıra aşağıdaki diyagramda gösterildiği gibi üretime dağıtımlar için de temel olarak kullanılır:

![Sonuna Kadar Docker DevOps Yaşam Döngüsü İş Akışı](./media/image1-7.png)

Konteynerlerle geliştirmek, özellikle konteynerler üretimde kullanıldığında birçok avantaj sağlar. Aynı kapsayıcı yapılandırması, yerel geliştirme makinesinden üretim sistemlerine ve test sistemlerine kadar uygulamayı çalıştığı her ortamda barındırmak için kullanılır. Bu, makine yapılandırması veya yazılım sürümlerindeki farklılıklardan kaynaklanan hata olasılığını büyük ölçüde azaltır. Kapsayıcılar herhangi bir işletim sisteminde çalıştırılabildiği için geliştiriciler, işletim sistemi de dahil olmak üzere en üretken araçları da kullanabilirler. Bazı durumlarda, birçok kapsayıcıiçeren dağıtılmış uygulamalar tek bir geliştirme makinesinde çalıştırılmak için çok kaynak yoğun olabilir. Bu senaryoda, bir sonraki bölümde kapsanan Kubernetes ve Azure Dev Spaces'i kullanmaya yükseltme yapmak mantıklı olabilir.

Daha büyük uygulamaların bazı bölümleri kendi küçük, bağımsız *mikro hizmetlerine*bölündükçe, uygulama davranışını iyileştirmek için ek tasarım desenleri kullanılabilir. Bir *API ağ geçidi,* tek tek hizmetlerle doğrudan çalışmak yerine erişimi basitleştirebilir ve istemciyi arka ucundan ayırabilir. Farklı ön uçlar için ayrı servis arka uçları olması da hizmetleri tüketicileri ile uyum içinde gelişmeye olanak sağlar. Ortak hizmetlere, *büyükelçi* deseni kullanılarak ortak istemci bağlantı kitaplıklarını içerebilecek ayrı bir *kenar araç* kapsayıcısı aracılığıyla erişilebilir.

![Microservices örnek mimarisi ile birkaç ortak tasarım desenleri kaydetti.](./media/image1-10.png)

[Mikro hizmet tabanlı sistemler inşa ederken göz önünde bulundurmak için tasarım desenleri hakkında daha fazla bilgi edinin.](https://docs.microsoft.com/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes Hizmeti (AKS), barındırılan Kubernetes ortamınızı yöneterek kapsayıcılı uygulamaları, kapsayıcı yönetimi uzmanlığı gerekmeden hızla ve kolayca dağıtma olanağı sunar. Ayrıca, kaynakları isteğe bağlı olarak sağlama, yükseltme ve ölçeklendirme işlemlerini uygulamalarınızı çevrimdışı duruma geçirmeden yaparak sürekliliği olan işlemlerin ve bakımların yükünü ortadan kaldırır.

AKS, sorumluluğun çoğunu Azure’a devrederek bir Kubernetes kümesi yönetmenin karmaşıklığı ve işlemsel yükünü azaltır. Barındırılan bir Kubernetes hizmeti olarak, Azure sistem durumu izleme ve bakım gibi kritik görevleri sizin için gerçekleştirir. Ayrıca, yalnızca kümelerinizdeki aracı düğümleri için ödeme yapmazsınız, ustalar için değil. Yönetilen bir Kubernetes hizmeti olarak AKS aşağıdakileri sağlar:

- Otomatik Kubernetes sürüm yükseltmeleri ve yama.
- Kolay küme ölçekleme.
- Kendi kendine iyileşme barındırılan kontrol uçağı (ustalar).
- Maliyet tasarrufu - yalnızca acente havuzu düğümlerini çalıştırmak için ödeme.

AKS kümenizde düğümleri Azure yönetirken, küme yükseltme gibi görevleri el ile gerçekleştirmeniz gerekmez. Azure bu kritik bakım görevlerini sizin için işlediği için, AKS kümeye doğrudan erişim (SSH gibi) sağlamaz.

AKS'den yararlanan ekipler, Azure Dev Spaces'den de yararlanabilir. Azure Dev Spaces, ekiplerin aks'te çalışan tüm mikro hizmet mimarisi veya uygulamalarıyla doğrudan çalışmalarına izin vererek ekiplerin mikro hizmet uygulamalarının geliştirilmesine ve hızlı bir şekilde yinelenmesine odaklanmalarına yardımcı olur. Azure Dev Spaces, aks kümesinin geri kalanını veya diğer geliştiricileri etkilemeden mikrohizmetler mimarinizin bölümlerini bağımsız olarak bağımsız olarak güncelleştirmenin bir yolunu da sağlar.

![Azure Dev Spaces iş akışı örneği](./media/image1-9.gif)

Azure Dev Alanları:

- Yerel makine kurulum süresini ve kaynak gereksinimlerini en aza indirin
- Ekiplerin daha hızlı yinelemesine izin ver
- Ekip tarafından gerekli olan tümleştirme ortamlarının sayısını azaltın
- Geliştirme/test ederken dağıtılmış sistemde belirli hizmetlerle alay etme gereksinimini ortadan kaldırma

[Azure Dev Alanları hakkında daha fazla bilgi edinin](https://docs.microsoft.com/azure/dev-spaces/about)

### <a name="azure-virtual-machines"></a>Azure Sanal Makineler

Uygulama Hizmeti'nde çalıştırılabilmesi için önemli değişiklikler gerektiren varolan bir uygulamanız varsa, buluta geçişi kolaylaştırmak için Sanal Makineler'i seçebilirsiniz. Ancak, VM'leri doğru şekilde yapılandırmak, güvence altına almak ve korumak, Azure Uygulama Hizmeti'ne kıyasla çok daha fazla zaman ve BT uzmanlığı gerektirir. Azure Sanal Makineleri düşünüyorsanız, VM ortamınızı yamamak, güncellemek ve yönetmek için gereken devam eden bakım çabasını dikkate aldığınızdan emin olun. Azure Sanal Makineler bir hizmet olarak altyapıdır (IaaS), App Service ise PaaS'tır. Uygulamanızı Kapsayıcılar için Web Uygulamasına Windows Kapsayıcısı olarak dağıtmanın senaryonuz için uygun bir seçenek olup olmadığını da düşünmelisiniz.

## <a name="logical-processes"></a>Mantıksal süreçler

Uygulamanın geri kalanından ayrıtutulabilen tek tek mantıksal işlemler, "sunucusuz" bir şekilde Azure İşlevleri'ne bağımsız olarak dağıtılabilir. Azure İşlevler, belirli bir sorun için gereksinim duyduğunuz kodu, çalıştırmak için uygulama veya altyapı konusunda endişelenmeden yazmanızı sağlar. C,\#F,\#Node.js, Python ve PHP gibi çeşitli programlama dillerinden birini seçerek elinizdeki görev için en üretken dili seçebilirsiniz. Bulut tabanlı çözümlerin çoğunda olduğu gibi, yalnızca kullandığınız süre için ödeme yapabilirsiniz ve Azure Fonksiyonları'nın gerektiğinde ölçeklendirilenlerine güvenebilirsiniz.

## <a name="data"></a>Veriler

Azure, uygulamanızın söz konusu veriler için uygun veri sağlayıcısını kullanabilmesi için çok çeşitli veri depolama seçenekleri sunar.

İşlemsel, ilişkisel veriler için Azure SQL Veritabanları en iyi seçenektir. Yüksek performanslı çoğunlukla okuma verileri için, Azure SQL Veritabanı tarafından desteklenen redis önbelleği iyi bir çözümdür.

Yapılandırılmamış JSON verileri, SQL Veritabanı sütunlarından Azure Depolama'daki Blob'lara veya Tablolar'a ve Azure Cosmos DB'ye kadar çeşitli şekillerde depolanabilir. Bunlardan Azure Cosmos DB en iyi sorgulama işlevini sunar ve sorgulamayı desteklemesi gereken çok sayıda JSON tabanlı belge için önerilen seçenektir.

Uygulama davranışını düzenlemek için kullanılan geçici komut veya olay tabanlı veriler Azure Hizmet Veri Veri Si'ni veya Azure Depolama Kuyruklarını kullanabilir. Azure Depolama Veri Servisi daha fazla esneklik sunar ve uygulamalar içinde ve arasında önemsiz olmayan mesajlaşma lar için önerilen hizmettir.

## <a name="architecture-recommendations"></a>Mimari öneriler

Uygulamanızın gereksinimleri mimarisini dikte etmelidir. Birçok farklı Azure hizmeti mevcuttur. Doğru olanı seçmek önemli bir karardır. Microsoft, yaygın senaryolar için en iyi duruma getirilmiş tipik mimarileri belirlemeye yardımcı olmak için bir başvuru mimarisi galerisi sunar. Uygulamanızın gereksinimlerini yakından eşleyen veya en azından bir başlangıç noktası sunan bir başvuru mimarisi bulabilirsiniz.

Şekil 11-1 örnek bir referans mimarisi gösterir. Bu diyagram, pazarlama için optimize edilmiş bir Sitecore içerik yönetim sistemi web sitesi için önerilen mimari yaklaşımı açıklar.

![Şekil 11-1](./media/image11-2.png)

**Şekil 11-1.** Sitecore pazarlama web sitesi referans mimarisi.

**Referanslar – Azure barındırma önerileri**

- Azure Çözüm Mimarileri\
  <https://azure.microsoft.com/solutions/architecture/>

- Azure Temel Web Uygulama Mimarisi\
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- Mikrohizmetler için Tasarım Desenleri\
  <https://docs.microsoft.com/azure/architecture/microservices/design/patterns>

- Azure Geliştirici Kılavuzu\
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Web Apps genel bakış\
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Kapsayıcılar için Web Uygulaması\
  <https://azure.microsoft.com/services/app-service/containers/>

- Azure Kubernetes Hizmetine Giriş (AKS)\
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Önceki](development-process-for-azure.md)
