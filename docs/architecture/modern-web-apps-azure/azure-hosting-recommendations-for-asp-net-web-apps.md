---
title: ASP.NET Core Web uygulamaları için Azure barındırma önerileri
description: ASP.NET Core ve Azure ile modern web uygulamalarını mimarın ASP.NET Web Apps için Azure barındırma önerileri
author: ardalis
ms.author: wiwagn
ms.date: 06/06/2019
ms.openlocfilehash: ed8771a4d79b45d8fad0e5309c886c2e00402ec7
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71331996"
---
# <a name="azure-hosting-recommendations-for-aspnet-core-web-apps"></a>ASP.NET Core Web uygulamaları için Azure barındırma önerileri

> "Her yerde iş kolu liderlerinin her ikisi de, buluttan uygulamaları (SaaS olarak da bilinir) almak ve bunları dergi abonelikleri gibi ödemeleri için BT departmanlarını atlar. Hizmete artık gerek duyulmuyorsa, köşede kullanılmayan bir ekipman olmadan aboneliği iptal edebilirler. "  
> _\- Daristl Pköpmer, Gartner analist_

Uygulamanızın ihtiyaçları ve mimarisi ne olursa olsun Microsoft Azure destekleyebilir. Barındırma gereksinimleriniz, statik bir Web sitesi veya onlarca hizmetlerden oluşan gelişmiş bir uygulama kadar basit olabilir. ASP.NET Core tek parçalı Web uygulamaları ve destekleyici hizmetler için önerilen birkaç tanınmış yapılandırma vardır. Bu makaledeki öneriler, tam uygulamalar, bireysel süreçler veya veriler arasında barındırılacak kaynak türüne göre gruplandırılır.

## <a name="web-applications"></a>Web uygulamaları

Web uygulamaları, ile barındırılabilir:

- App Service Web Apps

- Kapsayıcılar (çeşitli seçenekler)

- Sanal makineler (VM 'Ler)

Bu App Service Web Apps, basit kapsayıcı tabanlı uygulamalar da dahil olmak üzere çoğu senaryo için önerilen yaklaşımdır. Mikro hizmet mimarileri için kapsayıcı tabanlı bir yaklaşım düşünün. Uygulamanızı çalıştıran makineler üzerinde daha fazla denetime ihtiyacınız varsa, Azure sanal makinelerini göz önünde bulundurun.

### <a name="app-service-web-apps"></a>App Service Web Apps

App Service Web Apps, Web uygulamalarını barındırmak için iyileştirilmiş, tam olarak yönetilen bir platform sunar. Bu bir hizmet olarak platform (PaaS) teklifi, Azure 'un uygulamayı çalıştırmak ve ölçeklendirmek için gereken altyapıyı ele alırken iş mantığınıza odaklanmanızı sağlar. App Service Web Apps 'nin bazı önemli özellikleri:

- DevOps iyileştirmesi (sürekli tümleştirme ve teslim, birden çok ortam, A/B testi, betik oluşturma desteği).

- Küresel ölçek ve yüksek kullanılabilirlik.

- SaaS platformlarına ve şirket içi verilerinize bağlantılar.

- Güvenlik ve uyumluluk.

- Visual Studio tümleştirmesi.

Azure App Service çoğu Web uygulaması için en iyi seçenektir. Dağıtım ve yönetim, platformla tümleşiktir, siteler yüksek trafik yüklerini işlemek için hızlıca ölçeklendirebilir ve yerleşik yük dengeleme ve Traffic Manager yüksek kullanılabilirlik sağlar. Mevcut siteleri çevrimiçi geçiş aracı ile kolayca Azure App Service taşıyabilir, Web uygulaması galerisinden açık kaynaklı bir uygulama kullanabilir veya seçtiğiniz Framework ve araçları kullanarak yeni bir site oluşturabilirsiniz. WebJobs özelliği, App Service Web uygulamanıza arka plan iş işlemesi eklemeyi kolaylaştırır. Şirket içinde yerel bir veritabanı kullanılarak barındırılan mevcut bir ASP.NET uygulamanız varsa, uygulamayı Azure SQL veritabanı ile bir App Service Web uygulamasına geçirmeye yönelik açık bir yol vardır (veya tercih edilirse şirket içi veritabanı sunucunuza güvenli erişim sağlayabilirsiniz).

![Şirket içi .NET uygulamaları Azure App Service için önerilen geçiş stratejisi](./media/image1-6.png)

Çoğu durumda, yerel olarak barındırılan bir ASP.NET uygulamasından App Service bir Web uygulamasına geçiş yapmak basit bir işlemdir. Uygulamanın kendisi için çok az değişiklik yapmanız gerekmez ve Azure App Service Web Apps sunduğu birçok özellikten faydalanması hızlı bir başlangıç yapabilir.

Bulut için iyileştirilmiş uygulamalara ek olarak, Azure App Service Web Apps birçok ASP.NET Core uygulama gibi birçok basit tek parçalı (dağıtılmamış) uygulamalara yönelik harika bir çözümdür. Bu yaklaşımda, mimari temel ve kolay anlaşılması ve yönetimi basittir:

![Temel Azure mimarisi](./media/image1-5.png)

Tek bir kaynak grubundaki az sayıda kaynak, genellikle bu tür bir uygulamayı yönetmek için yeterlidir. Genellikle tek bir birim olarak dağıtılan ve birçok ayrı işlemlerden oluşan uygulamalar yerine, bu [temel mimari yaklaşım](https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app)için iyi adaylardır. Bu yaklaşım, mimari açıdan basit olsa da, barındırılan uygulamanın her türlü artışı karşılamak için her ikisini de (düğüm başına daha fazla kaynak) ve dışarı (daha fazla barındırılan düğüm) ölçeklendirmesine izin verir. Otomatik ölçeklendirme ile uygulama, düğümler arasında talep ve ortalama yük temelinde uygulamayı barındıran düğüm sayısını otomatik olarak ayarlanacak şekilde yapılandırılabilir.

### <a name="app-service-web-apps-for-containers"></a>Kapsayıcılar için App Service Web Apps

Web uygulamalarının doğrudan barındırılmasına yönelik desteğe ek olarak, [kapsayıcılar için App Service Web Apps](https://azure.microsoft.com/services/app-service/containers/) Windows ve Linux 'ta Kapsayıcılı uygulamalar çalıştırmak için kullanılabilir. Bu hizmeti kullanarak, işinizle ölçeklenebilen Kapsayıcılı uygulamaları kolayca dağıtabilir ve çalıştırabilirsiniz. Uygulamalar yukarıda listelenen App Service Web Apps tüm özelliklere sahiptir. Ayrıca, kapsayıcılar için Web Apps Docker Hub, Azure Container Registry ve GitHub ile kolaylaştırılmış CI/CD 'yi destekler. Değişiklikleri bir kayıt defterine yayınlayan derleme ve dağıtım işlem hatlarını tanımlamak için Azure DevOps ' i kullanabilirsiniz. Bu değişiklikler daha sonra bir hazırlama ortamında test edilebilir ve dağıtım yuvaları kullanılarak otomatik olarak üretime dağıtılır ve bu da sıfır kesinti yaşlara izin verir. Önceki sürümlere geri dönme işlemi, kolayca yapılabilir.

Kapsayıcıların Web Apps en mantıklı hale getirilbileceği birkaç senaryo vardır. Windows veya Linux kapsayıcılarında Kapsayıcılı kullanabileceğiniz mevcut uygulamalarınız varsa, bu araç takımını kullanarak bunları kolayca barındırabilirsiniz. Yalnızca kapsayıcınızı yayımlayın ve sonra kapsayıcıların Web Apps, bu görüntünün en son sürümünü tercih ettiğiniz kayıt defterinden çekmek üzere yapılandırın. Bu, klasik uygulama barındırma modellerinden buluta iyileştirilmiş bir modele geçiş yapmak için bir "kaldırma ve kaydırma" yaklaşımıdır.

![Kapsayıcılı şirket içi .NET uygulamasını kapsayıcılar için Azure Web Apps geçirme](./media/image1-8.png)

Bu yaklaşım, geliştirme ekibiniz kapsayıcı tabanlı bir geliştirme sürecine taşıyabildiği durumlarda da iyi bir şekilde çalışacaktır. Kapsayıcılarla uygulama geliştirmenin "iç döngüsü", kapsayıcı ile uygulama oluşturmayı içerir. Kodda yapılan değişiklikler ve kapsayıcı yapılandırması da kaynak denetimine gönderilir ve yeni kapsayıcı görüntülerini Docker Hub veya Azure Container Registry gibi bir kayıt defterine yayımlarken otomatik derleme sorumludur. Bu görüntüler daha sonra ek geliştirme için temel olarak ve aşağıdaki diyagramda gösterildiği gibi üretime yönelik dağıtımlar için de kullanılır:

![Uçtan uca Docker DevOps yaşam döngüsü Iş akışı](./media/image1-7.png)

Kapsayıcılarla geliştirme, özellikle kapsayıcılar üretimde kullanıldığında birçok avantaj sunar. Aynı kapsayıcı yapılandırması, uygulamasının çalıştığı her ortamda barındırmak için, yerel geliştirme makinesinden sistemleri üretime derlemek ve test etmek için kullanılır. Bu durum, makine yapılandırması veya yazılım sürümlerindeki farklardan kaynaklanan arızaların oluşma olasılığını önemli ölçüde azaltır. Geliştiriciler, kapsayıcılar herhangi bir IŞLETIM sistemi üzerinde çalıştırılabildiği için, işletim sistemi dahil olmak üzere en çok hangi araçları da kullanabilir. Bazı durumlarda, çok sayıda kapsayıcı içeren dağıtılmış uygulamalar, tek bir geliştirme makinesinde çalışmak için çok kaynak yoğunluklu olabilir. Bu senaryoda, sonraki bölümde bahsedilen Kubernetes ve Azure Dev Spaces kullanarak yükseltme yapmak mantıklı olabilir.

Daha büyük uygulamaların bir bölümü kendi daha küçük, bağımsız *mikro hizmetlere*bölündüğü için ek tasarım desenleri, uygulama davranışını geliştirmek için kullanılabilir. Bir *API ağ geçidi* , bireysel hizmetlerle doğrudan çalışmak yerine erişimi basitleştirecek ve istemciyi arka uçtan ayırarak alabilir. Farklı ön uçlar için ayrı hizmet arka uçları olması ayrıca hizmetlerin tüketicilerle birlikte gelişmelerini sağlar. Ortak hizmetlere, *amelçi* deseninin kullanıldığı ortak istemci bağlantı kitaplıklarını içerebilen ayrı bir *sepet* kapsayıcısı aracılığıyla erişilebilir.

![Birkaç ortak tasarım deseni belirtilmiş mikro hizmetler örnek mimarisi.](./media/image1-10.png)

[Mikro hizmet tabanlı sistemler oluştururken göz önünde bulundurmanız gereken tasarım desenleri hakkında daha fazla bilgi edinin.](https://docs.microsoft.com/azure/architecture/microservices/design/patterns)

### <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Azure Kubernetes hizmeti (AKS), barındırılan Kubernetes ortamınızı yönetir ve kapsayıcı düzenleme uzmanlığı olmadan Kapsayıcılı uygulamaları dağıtmayı ve yönetmeyi kolaylaştırır. Ayrıca, uygulamalarınızı çevrimdışı duruma getirmeden, kaynakları etkinleştirerek, yükselterek ve ölçeklendirerek devam eden işlemlerin ve bakımın yükünü ortadan kaldırır.

AKS, bu sorumluluğun büyük bir kısmını Azure 'a devrederek bir Kubernetes kümesini yönetmenin karmaşıklık ve operasyonel yükünü azaltır. Barındırılan bir Kubernetes hizmeti olarak Azure, sistem durumu izleme ve bakım gibi kritik görevleri sizin için işler. Ayrıca, ana bilgisayarlar için değil, yalnızca kümelerinizdeki aracı düğümleri için ödeme yaparsınız. Yönetilen bir Kubernetes hizmeti olarak AKS şunları sağlar:

- Otomatik Kubernetes sürüm yükseltmeleri ve düzeltme eki uygulama.
- Kolay küme ölçekleme.
- Kendi kendini onaran barındırılan denetim düzlemi (Yöneticiler).
- Maliyet tasarrufu-yalnızca aracı havuzu düğümleri çalıştırmak için ödeme yapın.

Azure, AKS kümenizdeki düğümlerin yönetimini gerçekleştirirken, küme yükseltmeleri gibi pek çok görevi el ile gerçekleştirmenize gerek kalmaz. Azure bu kritik bakım görevlerini sizin için işletiğinden, AKS kümeye doğrudan erişim (SSH ile) sağlamaz.

AKS kullanan takımlar, Azure Dev Spaces de yararlanabilir. Azure Dev Spaces, takımların mikro hizmet uygulamalarının geliştirilmesine ve hızlı yinelemesine odaklanarak ekiplerin, AKS 'de çalışan tüm mikro hizmetler mimarisi veya uygulamaları ile doğrudan çalışmasına yardımcı olur. Azure Dev Spaces, mikro hizmetler mimarinizin bölümlerini, AKS kümesinin veya diğer geliştiricilerin geri kalanını etkilemeden yalıtımsız olarak güncelleştirmek için bir yol da sağlar.

![Azure Dev Spaces iş akışı örneği](./media/image1-9.gif)

Azure Dev Spaces:

- Yerel makine kurulum süresini ve kaynak gereksinimlerini en aza indir
- Ekiplerin daha hızlı yineleme yapmasına izin ver
- Ekibin gerektirdiği tümleştirme ortamlarının sayısını azaltın
- Geliştirme/test ederken Dağıtılmış sistemde belirli hizmetleri sahte bir şekilde çıkarma gereksinimini ortadan kaldırma

[Azure Dev Spaces hakkında daha fazla bilgi edinin](https://docs.microsoft.com/azure/dev-spaces/about)

### <a name="azure-virtual-machines"></a>Azure sanal makineleri

App Service ' de çalışmak için önemli değişiklikler gerektiren mevcut bir uygulamanız varsa, buluta geçişi kolaylaştırmak için sanal makineleri seçebilirsiniz. Ancak, VM 'Leri doğru şekilde yapılandırmak, güvenli hale getirmek ve sürdürmek, Azure App Service kıyasla daha fazla zaman ve BT uzmanlığı gerektirir. Azure sanal makinelerini düşünüyorsanız, VM ortamınızı düzeltme eki uygulamak, güncelleştirmek ve yönetmek için gereken devam eden bakım çabasıyla karşılaştığınızdan emin olun. Azure sanal makineleri hizmet olarak altyapı (IaaS) olduğundan App Service PaaS olur. Ayrıca, Kapsayıcılar için Web App için uygulamanızın Windows kapsayıcısı olarak dağıtılmasının, senaryonuz için uygun bir seçenek olabileceğini de göz önünde bulundurmanız gerekir.

## <a name="logical-processes"></a>Mantıksal süreçler

Uygulamanın geri kalanından ayrışlabilecek tek tek mantıksal işlemler, Azure Işlevlerine "sunucusuz" bir şekilde dağıtılabilir. Azure Işlevleri, belirli bir sorun için ihtiyaç duyduğunuz kodu, uygulamayı veya altyapıyı çalıştırmak için herhangi bir endişelenmeden yazmanızı sağlar. C @ no__t-0, F @ no__t-1, Node. js, Python ve PHP dahil olmak üzere çeşitli programlama dilleri arasından seçim yapabilirsiniz. Bu, eldeki görev için en üretken dili seçmenizi sağlar. Bulut tabanlı çoğu çözüm gibi, yalnızca kullandığınız süre için ödeme yaparsınız ve gerektiğinde ölçeği ölçeklendirmek için Azure Işlevlerine güvenebilirsiniz.

## <a name="data"></a>Data

Azure çok çeşitli veri depolama seçenekleri sunarak uygulamanızın söz konusu veriler için uygun veri sağlayıcısını kullanabilmesi için.

İşlem, ilişkisel veriler için Azure SQL veritabanları en iyi seçenektir. Yüksek performanslı okuma verileri için, Azure SQL veritabanı tarafından desteklenen bir Redsıs önbelleği iyi bir çözümdür.

Yapılandırılmamış JSON verileri, SQL veritabanı sütunlarından blob 'lara veya Azure Storage 'daki tablolara DocumentDB 'ye kadar çeşitli yollarla depolanabilir. Bu şekilde, DocumentDB en iyi sorgulama işlevlerini sunar ve sorgulamayı desteklemesi gereken çok sayıda JSON tabanlı belge için önerilen seçenektir.

Uygulama davranışını düzenlemek için kullanılan geçici komut veya olay tabanlı veriler Azure Service Bus veya Azure depolama kuyruklarını kullanabilir. Azure Storage veri yolu daha fazla esneklik sunar ve uygulamalar içinde ve arasında önemsiz olmayan mesajlaşma için önerilen hizmettir.

## <a name="architecture-recommendations"></a>Mimari önerileri

Uygulamanızın gereksinimleri mimarisini dikte etmelidir. Kullanılabilir birçok farklı Azure hizmeti vardır. Doğru birinin seçilmesi önemli bir karardır. Microsoft, yaygın senaryolar için optimize edilmiş tipik mimarilerin tanımlanmasına yardımcı olmak için bir başvuru mimarileri Galerisi sunar. Uygulamanızın gereksinimlerine yakın bir şekilde eşleşen bir başvuru mimarisi bulabilir veya en azından bir başlangıç noktası sunar.

Şekil 11-1, örnek bir başvuru mimarisini gösterir. Bu diyagramda, pazarlama için en iyi duruma getirilmiş Sitecore içerik yönetimi sistem web sitesi için önerilen bir mimari yaklaşımı açıklanmaktadır.

![Şekil 11-1](./media/image11-2.png)

**Şekil 11-1.** Sitecore pazarlama web sitesi başvuru mimarisi.

**Başvurular – Azure barındırma önerileri**

- Azure çözüm mimarileri \
  <https://azure.microsoft.com/solutions/architecture/>

- Azure temel Web uygulaması mimarisi \
  <https://docs.microsoft.com/azure/architecture/reference-architectures/app-service-web-app/basic-web-app>

- Mikro hizmetler için tasarım desenleri \
  <https://docs.microsoft.com/azure/architecture/microservices/design/patterns>

- Azure Geliştirici Kılavuzu \
  <https://azure.microsoft.com/campaigns/developer-guide/>

- Web Apps genel bakış \
  <https://docs.microsoft.com/azure/app-service/app-service-web-overview>

- Kapsayıcılar için Web App \
  <https://azure.microsoft.com/services/app-service/containers/>

- Azure Kubernetes hizmetine (AKS) giriş
  <https://docs.microsoft.com/azure/aks/intro-kubernetes>

>[!div class="step-by-step"]
>[Önceki](development-process-for-azure.md)
