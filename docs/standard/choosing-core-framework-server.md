---
title: Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma
description: Bir sunucu uygulaması oluştururken hangi .NET uygulamasının kullanılması gerektiğine karar vermenize yardımcı olacak bir kılavuz.
author: cartermp
ms.date: 04/28/2020
ms.openlocfilehash: a3c15e8f2198b1bcc4e623a7dc7f5cddca9c83f6
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89415026"
---
# <a name="net-core-vs-net-framework-for-server-apps"></a>.NET Core ile sunucu uygulamaları için .NET Framework

Sunucu tarafı uygulamalar oluşturmaya yönelik iki desteklenen .NET uygulaması vardır: .NET Framework ve .NET Core. Her ikisi de aynı bileşenlerden birçoğunu paylaşır ve iki arasında kod paylaşabilirsiniz. Bununla birlikte, ikisi arasında temel farklılıklar vardır ve seçiminiz, gerçekleştirmek istediğiniz seçeneğe bağlıdır. Bu makale, her birinin ne zaman kullanılacağı hakkında rehberlik sağlar.

Şu durumlarda sunucu uygulamanız için .NET Core kullanın:

- Platformlar arası gereksinimleriniz var.
- Mikro hizmetleri hedefliyoruz.
- Docker Kapsayıcıları kullanıyorsunuz.
- Yüksek performanslı ve ölçeklenebilir sistemleriniz olmalıdır.
- Uygulama başına yan yana .NET sürümlerine ihtiyacınız vardır.

Sunucu uygulamanız için .NET Framework şu durumlarda kullanın:

- Uygulamanız Şu anda .NET Framework kullanıyor (öneri, geçiş yerine genişletilir).
- Uygulamanız üçüncü taraf .NET kitaplıklarını veya .NET Core için mevcut olmayan NuGet paketlerini kullanır.
- Uygulamanız .NET Core için kullanılamayan .NET teknolojilerini kullanır.
- Uygulamanız .NET Core desteklemeyen bir platform kullanıyor. Windows, macOS ve Linux .NET Core 'u destekler.

## <a name="when-to-choose-net-core"></a>Ne zaman .NET Core seçme

Aşağıdaki bölümlerde, .NET Core çekmeye yönelik daha önce belirtilen nedenlerden daha ayrıntılı bir açıklama verilmektedir.

### <a name="cross-platform-needs"></a>Platformlar arası gereksinimler

Uygulamanızın (Web/hizmet) birden çok platformda (Windows, Linux ve macOS) çalışması gerekiyorsa .NET Core kullanın.

.NET Core, geliştirme iş istasyonunuz olarak yukarıda bahsedilen işletim sistemlerini destekler. Visual Studio, Windows ve macOS için tümleşik bir geliştirme ortamı (IDE) sağlar. MacOS, Linux ve Windows üzerinde çalışan Visual Studio Code de kullanabilirsiniz. Visual Studio Code, IntelliSense ve hata ayıklama dahil .NET Core 'u destekler. Alt Lime, Emacs ve VI gibi üçüncü taraf düzenleyicilerin çoğu .NET Core ile çalışır. Bu üçüncü taraf düzenleyiciler, [Omnisharp](https://www.omnisharp.net/)kullanarak düzenleyici IntelliSense 'i alır. Ayrıca, herhangi bir kod düzenleyiciden kaçınabilir ve tüm desteklenen platformlar için kullanılabilen [.NET Core CLI](../core/tools/index.md)doğrudan kullanabilirsiniz.

### <a name="microservices-architecture"></a>Mikro hizmetler mimarisi

Mikro hizmetler mimarisi, bir hizmet sınırı genelinde teknolojilerin karışımına izin verir. Bu teknoloji karışımı, diğer mikro hizmetler veya hizmetlerle çalışan yeni mikro hizmetler için .NET Core 'un aşamalı bir şekilde kullanılmasına izin vermez. Örneğin, .NET Framework, Java, Ruby veya diğer tek parçalı teknolojilerle geliştirilen mikro hizmetleri veya hizmetleri karıştırabilirsiniz.

Kullanılabilir çok sayıda altyapı platformu vardır. [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) , büyük ve karmaşık mikro hizmet sistemleri için tasarlanmıştır. [Azure App Service](https://azure.microsoft.com/services/app-service/) , durum bilgisi olmayan mikro hizmetler için iyi bir seçimdir. Docker tabanlı mikro hizmet alternatifleri, [kapsayıcılar](#containers) bölümünde açıklandığı gibi her türlü mikro hizmet yaklaşımını ister. Tüm bu platformlar .NET çekirdeğini destekler ve mikro hizmetlerinizin barındırılmasına yönelik ideal hale getirir.

Mikro hizmet mimarisi hakkında daha fazla bilgi için bkz [. .net mikro hizmetleri. Kapsayıcılı .NET uygulamaları için mimari](../architecture/microservices/index.md).

### <a name="containers"></a>Kapsayıcılar

Kapsayıcılar genellikle mikro hizmetler mimarisiyle birlikte kullanılır. Kapsayıcılar Ayrıca, herhangi bir mimari kalıbı izleyen Web uygulamalarını veya hizmetlerini kapsayıleştirmek için de kullanılabilir. .NET Framework, Windows kapsayıcılarında kullanılabilir, ancak .NET Core 'un modülerliği ve hafif doğası, kapsayıcılar için daha iyi bir seçenek sunar. Bir kapsayıcı oluştururken ve dağıttığınızda görüntünün boyutu .NET Core ile .NET Framework kıyasla çok daha küçüktür. Platformlar arası olduğundan, örneğin, Linux Docker kapsayıcılarına sunucu uygulamaları dağıtabilirsiniz.

Docker Kapsayıcıları kendi Linux veya Windows altyapınızda veya [Azure Kubernetes hizmeti](https://azure.microsoft.com/services/kubernetes-service/)gibi bir bulut hizmetinde barındırılabilir. Azure Kubernetes hizmeti, bulutta kapsayıcı tabanlı uygulamaları yönetebilir, düzenleyebilir ve ölçeklendirebilir.

### <a name="high-performance-and-scalable-systems"></a>Yüksek performanslı ve ölçeklenebilir sistemler

Sisteminizin olası en iyi performans ve ölçeklenebilirlik ihtiyacı olduğunda, .NET Core ve ASP.NET Core en iyi seçenekleriniz vardır. Windows Server ve Linux için yüksek performanslı sunucu çalışma zamanı, .NET Framework 'ün [Techempower kıyaslamaları](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)üzerinde en iyi şekilde gerçekleştirdiği bir Web çerçevesi

Performans ve ölçeklenebilirlik özellikle, yüzlerce mikro hizmetin çalıştığı mikro hizmet mimarileri ile ilgilidir. ASP.NET Core, sistemler çok daha az sayıda sunucu/sanal makine (VM) ile çalışır. Azaltılmış sunucular/VM 'Ler altyapı ve barındırma için maliyetleri kaydeder.

### <a name="side-by-side-net-versions-per-application-level"></a>Uygulama düzeyi başına yan yana .NET sürümleri

.NET Core 'un farklı sürümlerindeki bağımlılıklara sahip uygulamaları yüklemek için .NET Core önerilir. .NET Core, .NET Core çalışma zamanının farklı sürümlerinin aynı makinede yan yana yüklenmesini destekler. Bu yan yana yükleme, her biri kendi .NET Core sürümünde aynı sunucuda birden çok hizmete izin verir. Ayrıca riskleri düşürür ve uygulama yükseltmeleri ve BT işlemlerinde tasarruf sağlar.

.NET Framework ile yan yana yükleme mümkün değildir. Bu bir Windows bileşenidir ve aynı anda bir makinede yalnızca bir sürüm bulunabilir. .NET Framework her sürümü önceki sürümün yerini alır. .NET Framework sonraki bir sürümünü hedefleyen yeni bir uygulama yüklerseniz, önceki sürüm değiştirildiğinden makinede çalışan mevcut uygulamaları kesebilirsiniz.

## <a name="when-to-choose-net-framework"></a>Ne zaman .NET Framework seçin

.NET Core, yeni uygulamalar ve uygulama desenleri için önemli avantajlar sunar. Ancak, .NET Framework birçok mevcut senaryo için doğal seçim olmaya devam eder ve bu nedenle .NET Framework tüm sunucu uygulamaları için .NET Core ile değiştirilmez.

### <a name="current-net-framework-applications"></a>Geçerli .NET Framework uygulamaları

Çoğu durumda, mevcut uygulamalarınızı .NET Core 'a geçirmeniz gerekmez. Bunun yerine, ASP.NET Core ' de yeni bir Web hizmeti yazma gibi, mevcut bir uygulamayı genişletmekle birlikte .NET Core 'u kullanmak önerilen bir yaklaşımdır.

### <a name="aspnet-core-on-net-framework"></a>.NET Framework ASP.NET Core

.NET Framework ASP.NET Core için destek hakkında daha fazla bilgi için bkz. [.NET Core destek ilkesi](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).

### <a name="third-party-libraries-or-nuget-packages-not-available-for-net-core"></a>.NET Core için üçüncü taraf kitaplıkları veya NuGet paketleri kullanılamıyor

Kitaplıklar .NET Standard hızlı bir şekilde kullanılır. .NET Standard .NET Core dahil olmak üzere tüm .NET uygulamalarında kod paylaşmaya izin vermez. .NET Standard 2,0 ile bu da daha kolay olur:

- API yüzeyi çok daha büyük hale geldi.
- .NET Framework uyumluluk modunu sunmuştur.

  Bu uyumluluk modu, .NET Standard ve .NET Core projelerinin .NET Framework kitaplıklarına başvurmasına olanak tanır. Uyumluluk modu hakkında daha fazla bilgi edinmek için bkz. [duyurusu .NET Standard 2,0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Yalnızca kitaplıkların veya NuGet paketlerinin .NET Standard veya .NET Core 'da kullanılamayan teknolojileri kullandığı durumlarda .NET Framework kullanmanız gerekir.

### <a name="net-technologies-not-available-for-net-core"></a>.NET Core için .NET teknolojileri kullanılamıyor

Bazı .NET Framework teknolojileri .NET Core 'da kullanılamaz. Bunlardan bazıları daha sonraki .NET Core sürümlerinde kullanılabilir olabilir. Diğerleri, .NET Core tarafından hedeflenen yeni uygulama düzenlerine uygulanmaz ve hiçbir şekilde kullanılamaz. Aşağıdaki listede, .NET Core 'da bulunmayan en yaygın teknolojiler gösterilmektedir:

- ASP.NET Web Forms uygulamalar: ASP.NET Web Forms yalnızca .NET Framework kullanılabilir. ASP.NET Core, ASP.NET Web Forms için kullanılamaz. .NET Core 'a ASP.NET Web Forms getirmek için bir plan yoktur.

- ASP.NET Web Pages uygulamaları: ASP.NET Web Pages ASP.NET Core.

- WCF Hizmetleri uygulama. .NET Core 'dan WCF hizmetlerini kullanmak için bir [WCF istemci kitaplığı](https://github.com/dotnet/wcf) olsa bıle, WCF sunucu uygulamasının şu anda yalnızca .NET Framework kullanılabilir. Bu senaryo, .NET Core için geçerli planın bir parçası değildir, ancak gelecekte göz önünde bulundurulmaktadır.

- İş akışı ile ilgili hizmetler: Windows Workflow Foundation (WF), Workflow Services (tek bir hizmette WCF + WF) ve WCF Veri Hizmetleri (eskiden "ADO.NET Data Services" olarak bilinirdi) yalnızca .NET Framework kullanılabilir. Bu teknolojileri .NET Core 'a getirmeye yönelik bir plan yoktur.

- Dil desteği: Visual Basic ve F # Şu anda .NET Core 'da desteklenir, ancak tüm proje türleri için desteklenmez. Desteklenen proje şablonlarının listesi için bkz. [DotNet New Için şablon seçenekleri](../core/tools/dotnet-new.md#arguments).

### <a name="platform-doesnt-support-net-core"></a>Platform .NET Core 'ı desteklemiyor

Bazı Microsoft veya üçüncü taraf platformları .NET Core ' u desteklemez. Bazı Azure Hizmetleri, .NET Core kullanımı için henüz kullanılabilir olmayan bir SDK sağlar. Bu, tüm Azure hizmetlerinin .NET Core 'u kullanması halinde geçici bir durumda. Bu sırada, istemci SDK 'Sı yerine eşdeğer REST API kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET ve ASP.NET Core arasında seçim yapın](/aspnet/core/choose-aspnet-framework)
- [.NET Framework'ü hedefleyen ASP.NET Core](/aspnet/core/introduction-to-aspnet-core#aspnet-core-targeting-net-framework)
- [Hedef çerçeveler](frameworks.md)
- [.NET Core tanıtımı](../core/introduction.md)
- [.NET Framework 'den .NET Core 'a taşıma](../core/porting/index.md)
- [.NET ve Docker’a Giriş](../core/docker/introduction.md)
- [.NET bileşenlerine genel bakış](components.md)
- [.NET mikro hizmetleri. Kapsayıcılı .NET uygulamaları için mimari](../architecture/microservices/index.md)
