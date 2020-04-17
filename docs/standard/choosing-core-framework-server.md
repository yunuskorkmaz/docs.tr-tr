---
title: Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma
description: .NET'te sunucu uygulaması yaparken göz önünde bulundurmanız gereken bir kılavuz.
author: cartermp
ms.date: 06/19/2018
ms.openlocfilehash: 885a7fb3419eafa5d88ef621cf6ad04a8d48bb59
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607499"
---
# <a name="choose-between-net-core-and-net-framework-for-server-apps"></a>Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma

.NET: .NET Framework ve .NET Core ile sunucu tarafı uygulamaları oluşturmak için desteklenen iki uygulama vardır. Her ikisi de aynı bileşenlerin çoğunu paylaşır ve kodu ikisi arasında paylaşabilirsiniz. Ancak, ikisi arasında temel farklılıklar vardır ve seçiminiz başarmak istediğiniz şeye bağlıdır.  Bu makalede, her birinin ne zaman kullanılacağı konusunda kılavuz luk lar verilmektedir.

Sunucu uygulamanız için .NET Core'u şu anda kullanın:

- Platform ötesi ihtiyaçların var.
- Mikro hizmetleri hedef lıyorsun.
- Docker konteynerlerini kullanıyorsunuz.
- Yüksek performanslı ve ölçeklenebilir sistemlere ihtiyacınız var.
- Uygulama başına yan yana .NET sürümlerine ihtiyacınız vardır.

Sunucu uygulamanız için .NET Framework'u şu anda kullanın:

- Uygulamanız şu anda .NET Framework kullanır (öneri, geçiş yerine genişletmektir).
- Uygulamanız üçüncü taraf .NET kitaplıklarını veya .NET Core için kullanılamayan NuGet paketlerini kullanır.
- Uygulamanız .NET Core için kullanılamayan .NET teknolojilerini kullanır.
- Uygulamanız .NET Core'u desteklemeyen bir platform kullanır. Windows, macOS ve Linux desteği .NET Core.

## <a name="when-to-choose-net-core"></a>.NET Core ne zaman seçilir?

Aşağıdaki bölümlerde .NET Core'u seçmek için daha önce belirtilen nedenler hakkında daha ayrıntılı bir açıklama yer alabilmektedir.

### <a name="cross-platform-needs"></a>Çapraz platform ihtiyaçları

Uygulamanızın (web/hizmetin) birden çok platformda (Windows, Linux ve macOS) çalışması gerekiyorsa, .NET Core'u kullanın.

.NET Core, geliştirme iş istasyonunuz olarak daha önce bahsedilen işletim sistemlerini destekler. Visual Studio, Windows ve macOS için Entegre Geliştirme Ortamı (IDE) sağlar. MacOS, Linux ve Windows'da çalışan Visual Studio Code'u da kullanabilirsiniz. Visual Studio Code, IntelliSense ve hata ayıklama dahil olmak üzere .NET Core'u destekler. Sublime, Emacs ve VI gibi üçüncü taraf editörlerin çoğu .NET Core ile çalışır. Bu üçüncü taraf editörler [Omnisharp](https://www.omnisharp.net/)kullanarak editör IntelliSense olsun. Ayrıca herhangi bir kod düzenleyicisi önlemek ve doğrudan [.NET Core CLI](../core/tools/index.md)kullanabilirsiniz , tüm desteklenen platformlar için kullanılabilir.

### <a name="microservices-architecture"></a>Mikro hizmetler mimarisi

Microservices mimarisi, hizmet sınırı boyunca teknolojilerin bir karışımını sağlar. Bu teknoloji karışımı, diğer mikro hizmetler veya hizmetlerle çalışan yeni mikro hizmetler için .NET Core'un kademeli olarak benimsenmesini sağlar. Örneğin, .NET Framework, Java, Ruby veya diğer yekpare teknolojilerle geliştirilen mikro hizmetleri veya hizmetleri karıştırabilirsiniz.

Birçok altyapı platformu mevcuttur. [Azure Servis Kumaşı,](https://azure.microsoft.com/services/service-fabric/) büyük ve karmaşık mikro hizmet sistemleri için tasarlanmıştır. [Azure Uygulama Hizmeti,](https://azure.microsoft.com/services/app-service/) durum suz mikro hizmetler için iyi bir seçimdir. Docker'a dayalı microservices [alternatifleri, Konteynerler](#containers) bölümünde açıklandığı gibi her türlü mikrohizmet yaklaşımına uygundur. Tüm bu platformlar .NET Core'u destekler ve mikro hizmetlerinizi barındırmak için idealdir.

Microservices mimarisi hakkında daha fazla bilgi için .NET Microservices bölümüne [bakın. Kapsayıcı .NET Uygulamaları için Mimari](../architecture/microservices/index.md).

### <a name="containers"></a>Kapsayıcılar

Kapsayıcılar genellikle bir microservices mimarisi ile birlikte kullanılır. Kapsayıcılar, herhangi bir mimari deseni izleyen web uygulamalarını veya hizmetlerini konteynerize etmek için de kullanılabilir. .NET Framework Windows kapsayıcılarında kullanılabilir, ancak .NET Core'un modülerliği ve hafif yapısı, kapsayıcılar için daha iyi bir seçim olmasını sağlar. Bir kapsayıcı oluştururken ve dağıtırken, görüntünün boyutu .NET Core ile .NET Framework'e göre çok daha küçüktür. Bu çapraz platform olduğundan, sunucu uygulamalarını Linux Docker kapsayıcılarına dağıtabilirsiniz, örneğin.

Docker kapsayıcıları kendi Linux veya Windows altyapınızda veya Azure [Kubernetes Hizmeti](https://azure.microsoft.com/services/kubernetes-service/)gibi bir bulut hizmetinde barındırılabilir. Azure Kubernetes Service, bulutta kapsayıcı tabanlı uygulamaları yönetebilir, düzenleyebilir ve ölçeklendirebilir.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Yüksek performanslı ve ölçeklenebilir sistemlere duyulan ihtiyaç

Sisteminizmümkün olan en iyi performans avede ihtiyaç duyduğunda ,NET Core ve ASP.NET Core en iyi seçeneklerinizdir. Windows Server ve Linux için yüksek performanslı sunucu çalışma süresi .NET [TechEmpower kriterleri](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)üzerinde en iyi performans gösteren web çerçevesi yapar.

Performans ve ölçeklenebilirlik, yüzlerce mikro hizmetin çalışıyor olabileceği mikro hizmetler mimarileri için özellikle önemlidir. ASP.NET Core ile sistemler çok daha az sayıda sunucu/Sanal Makine (VM) ile çalışır. İndirimli sunucular/VM'ler altyapı ve barındırma maliyetlerinden tasarruf sağlar.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Uygulama düzeyi başına .NET sürümlerinin yan yana ihtiyaç

.NET'in farklı sürümlerine bağımlı uygulamalar yüklemek için .NET Core'u öneririz. .NET Core, .NET Core çalışma zamanının farklı sürümlerinin aynı makinede yan yana kurulumunu sunar. Bu yan yana yükleme, her biri .NET Core'un kendi sürümünde olmak üzere aynı sunucuda birden çok hizmete izin verir. Ayrıca riskleri düşürür ve uygulama yükseltmeleri ve BT işlemlerinde tasarruf sağlar.

## <a name="when-to-choose-net-framework"></a>.NET Framework ne zaman seçilir?

.NET Core, yeni uygulamalar ve uygulama modelleri için önemli avantajlar sunar. Ancak, .NET Framework varolan birçok senaryo için doğal bir seçim olmaya devam eder ve bu nedenle .NET Framework tüm sunucu uygulamaları için .NET Core ile değiştirilmez.

### <a name="current-net-framework-applications"></a>Güncel .NET Çerçeve uygulamaları

Çoğu durumda, varolan uygulamalarınızı .NET Core'a geçirmeniz gerekmez. Bunun yerine, ASP.NET Core'da yeni bir web hizmeti yazmak gibi varolan bir uygulamayı genişletirken .NET Core'u kullanmanız önerilir.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>.NET Core için kullanılamayan üçüncü taraf .NET kitaplıklarını veya NuGet paketlerini kullanma gereksinimi

Kitaplıklar hızla .NET Standard'ı benimsiyor. .NET Standard, .NET Core dahil olmak üzere tüm .NET uygulamaları arasında kod paylaşımını sağlar. .NET Standard 2.0 ile bu daha da kolaydır:

- API yüzeyi çok daha büyük oldu.
- Bir .NET Framework uyumluluk modu tanıtıldı. Bu uyumluluk modu .NET Standard/.NET Core projelerinin .NET Framework kitaplıklarına başvurmasını sağlar. Uyumluluk modu hakkında daha fazla bilgi edinmek için şu bünyede [.NET Standart 2.0'ı duyurmak](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Bu nedenle, yalnızca kitaplıkların veya NuGet paketlerinin .NET Standard/.NET Core'da bulunmayan teknolojileri kullandığı durumlarda .NET Framework'ü kullanmanız gerekir.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>.NET Core için mevcut olmayan .NET teknolojilerini kullanma gereksinimi

Bazı .NET Framework teknolojileri .NET Core'da kullanılamaz. Bazıları daha sonra .NET Core sürümlerinde kullanılabilir. Diğerleri .NET Core tarafından hedeflenen yeni uygulama modelleri için geçerli değildir ve asla kullanılamayabilir. Aşağıdaki liste .NET Core'da bulunmayan en yaygın teknolojileri gösterir:

- ASP.NET Web Formları uygulamaları: ASP.NET Web Formları yalnızca .NET Framework'de mevcuttur. ASP.NET Core, web formlarını ASP.NET için kullanılamaz. web formlarını .NET Core'a ASP.NET getirme planları yoktur.

- ASP.NET Web Sayfaları uygulamaları: ASP.NET Web Sayfaları ASP.NET Çekirdek'e dahil değildir.

- WCF hizmetleri uygulaması. .NET Core'dan WCF hizmetlerini tüketecek bir [WCF-Client kitaplığı](https://github.com/dotnet/wcf) olsa bile, WCF sunucu uygulaması şu anda yalnızca .NET Framework'de kullanılabilir. Bu senaryo .NET Core için geçerli planın bir parçası değildir, ancak gelecek için düşünülmektedir.

- İş akışıyla ilgili hizmetler: Windows İş Akışı Vakfı (WF), İş Akışı Hizmetleri (Tek bir hizmette WCF + WF) ve WCF Veri Hizmetleri (eski adıyla "ADO.NET Veri Hizmetleri") yalnızca .NET Framework'de kullanılabilir.  WF/WCF+WF/WCF Veri Hizmetlerini .NET Core'a getirme planları yoktur.

- Dil desteği: Visual Basic ve F# şu anda .NET Core'da desteklenir, ancak tüm proje türleri için desteklenmez. Desteklenen proje şablonlarının listesi [için, dotnet yeni şablon seçeneklerine](../core/tools/dotnet-new.md#arguments)bakın.

Resmi yol haritasına ek olarak, .NET Core'a taşıması gereken başka çerçeveler de vardır. Tam liste için, bağlantı noktası olarak işaretlenmiş CoreFX [sorunlarına](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core)bakın. Bu liste, Microsoft'un bu bileşenleri .NET Core'a getirme taahhüdünü temsil etmez. Sadece toplumdan bunu yapma arzusunu yakalıyorlar. Olarak işaretlenmiş bileşenlerden herhangi birini `port-to-core`önemsiyorsanız, GitHub'daki tartışmalara katılın. Ve bir şey eksik olduğunu düşünüyorsanız, [.NET deposunda](https://github.com/dotnet/runtime/issues/new)yeni bir sorun dosya.

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>.NET Core'u desteklemeyen bir platform kullanma gereksinimi

Bazı Microsoft veya üçüncü taraf platformlar .NET Core'u desteklemez. Bazı Azure hizmetleri ,.NET Core'da henüz kullanıma sunulmamış bir SDK sağlar. Tüm Azure hizmetlerinin .NET Core'u kullandığı için bu bir geçiş durumudur. Bu arada, her zaman istemci SDK yerine eşdeğer REST API kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET ve ASP.NET Core arasında seçim yapın](/aspnet/core/choose-aspnet-framework)
- [.NET Framework'ü hedefleyen ASP.NET Core](/aspnet/core/introduction-to-aspnet-core#aspnet-core-targeting-net-framework)
- [Hedef çerçeveler](frameworks.md)
- [.NET Çekirdek Rehberi](../core/index.yml)
- [.NET Framework'den .NET Core'a taşıma](../core/porting/index.md)
- [.NET ve Docker’a Giriş](../core/docker/introduction.md)
- [.NET Bileşenlerine Genel Bakış](components.md)
- [.NET MikroHizmetler. Konteynerleştirilmiş .NET Uygulamaları için Mimari](../architecture/microservices/index.md)
