---
title: Sunucu uygulamaları için .NET 5 ve .NET Framework arasında seçim yapın
description: Bir sunucu uygulaması oluştururken hangi .NET uygulamasının kullanılması gerektiğine karar vermenize yardımcı olacak bir kılavuz.
author: cartermp
ms.date: 10/06/2020
ms.openlocfilehash: 989a0f83968473523c3d77bed155d6841b240edc
ms.sourcegitcommit: 39b1d5f2978be15409c189a66ab30781d9082cd8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2020
ms.locfileid: "92050500"
---
# <a name="net-5-vs-net-framework-for-server-apps"></a>.NET 5 vs. Server uygulamaları için .NET Framework

Sunucu tarafı uygulamalar oluşturmaya yönelik iki desteklenen .NET uygulaması vardır: .NET Framework ve .NET 5 (.NET Core dahil). Her ikisi de aynı bileşenlerden birçoğunu paylaşır ve iki arasında kod paylaşabilirsiniz. Bununla birlikte, ikisi arasında temel farklılıklar vardır ve seçiminiz, gerçekleştirmek istediğiniz seçeneğe bağlıdır. Bu makale, her birinin ne zaman kullanılacağı hakkında rehberlik sağlar.

Sunucu uygulamanız için .NET 5 ' i şu durumlarda kullanın:

- Platformlar arası gereksinimleriniz var.
- Mikro hizmetleri hedefliyoruz.
- Docker Kapsayıcıları kullanıyorsunuz.
- Yüksek performanslı ve ölçeklenebilir sistemleriniz olmalıdır.
- Uygulama başına yan yana .NET sürümlerine ihtiyacınız vardır.

Sunucu uygulamanız için .NET Framework şu durumlarda kullanın:

- Uygulamanız Şu anda .NET Framework kullanıyor (öneri, geçiş yerine genişletilir).
- Uygulamanız üçüncü taraf .NET kitaplıklarını veya .NET 5 için kullanılamayan NuGet paketlerini kullanır.
- Uygulamanız .NET 5 için kullanılamayan .NET teknolojilerini kullanır.
- Uygulamanız .NET 5 ' i desteklemeyen bir platform kullanıyor.

## <a name="when-to-choose-net-5"></a>Ne zaman .NET 5 seçin

Aşağıdaki bölümlerde, .NET 5 ' i çekmeye yönelik daha önceden belirtilen nedenler hakkında daha ayrıntılı bir açıklama verilmektedir.

### <a name="cross-platform-needs"></a>Platformlar arası gereksinimler

Uygulamanızın (Web/hizmet) birden çok platformda (Windows, Linux ve macOS) çalışması gerekiyorsa, .NET 5 kullanın.

.NET 5, daha önce bahsedilen işletim sistemlerini geliştirme iş istasyonunuz olarak destekler. Visual Studio, Windows ve macOS için tümleşik bir geliştirme ortamı (IDE) sağlar. MacOS, Linux ve Windows üzerinde çalışan Visual Studio Code de kullanabilirsiniz. Visual Studio Code, IntelliSense ve hata ayıklama dahil .NET 5 ' ü destekler. Alt Lime, Emacs ve VI gibi üçüncü taraf düzenleyicilerin çoğu .NET 5 ile çalışır. Bu üçüncü taraf düzenleyiciler, [Omnisharp](https://www.omnisharp.net/)kullanarak düzenleyici IntelliSense 'i alır. Ayrıca, herhangi bir kod düzenleyiciden kaçınabilir ve tüm desteklenen platformlar için kullanılabilen [.NET Core CLI](../core/tools/index.md)doğrudan kullanabilirsiniz.

### <a name="microservices-architecture"></a>Mikro hizmetler mimarisi

Mikro hizmetler mimarisi, bir hizmet sınırı genelinde teknolojilerin karışımına izin verir. Bu teknoloji karışımı, diğer mikro hizmetler veya hizmetlerle çalışan yeni mikro hizmetler için .NET 5 ' in aşamalı bir şekilde kullanılmasını mümkün. Örneğin, .NET Framework, Java, Ruby veya diğer tek parçalı teknolojilerle geliştirilen mikro hizmetleri veya hizmetleri karıştırabilirsiniz.

Kullanılabilir çok sayıda altyapı platformu vardır. [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) , büyük ve karmaşık mikro hizmet sistemleri için tasarlanmıştır. [Azure App Service](https://azure.microsoft.com/services/app-service/) , durum bilgisi olmayan mikro hizmetler için iyi bir seçimdir. Docker tabanlı mikro hizmet alternatifleri, [kapsayıcılar](#containers) bölümünde açıklandığı gibi her türlü mikro hizmet yaklaşımını ister. Tüm bu platformlar .NET 5 ' i destekler ve mikro hizmetlerinizin barındırılmasına yönelik ideal hale getirir.

Mikro hizmet mimarisi hakkında daha fazla bilgi için bkz [. .net mikro hizmetleri. Kapsayıcılı .NET uygulamaları için mimari](../architecture/microservices/index.md).

### <a name="containers"></a>Kapsayıcılar

Kapsayıcılar genellikle mikro hizmetler mimarisiyle birlikte kullanılır. Kapsayıcılar Ayrıca, herhangi bir mimari kalıbı izleyen Web uygulamalarını veya hizmetlerini kapsayıleştirmek için de kullanılabilir. .NET Framework, Windows kapsayıcılarında kullanılabilir, ancak .NET 5 ' in modülerliği ve hafif doğası kapsayıcılar için daha iyi bir seçenek sunar. Bir kapsayıcı oluştururken ve dağıttığınızda görüntünün boyutu, .NET 5 ' ten .NET Framework göre çok daha küçüktür. Platformlar arası olduğundan, örneğin, Linux Docker kapsayıcılarına sunucu uygulamaları dağıtabilirsiniz.

Docker Kapsayıcıları kendi Linux veya Windows altyapınızda veya [Azure Kubernetes hizmeti](https://azure.microsoft.com/services/kubernetes-service/)gibi bir bulut hizmetinde barındırılabilir. Azure Kubernetes hizmeti, bulutta kapsayıcı tabanlı uygulamaları yönetebilir, düzenleyebilir ve ölçeklendirebilir.

### <a name="high-performance-and-scalable-systems"></a>Yüksek performanslı ve ölçeklenebilir sistemler

Sisteminizin olası en iyi performans ve ölçeklenebilirlik ihtiyacı olduğunda, .NET 5 ve ASP.NET Core en iyi seçeneklerdir. Windows Server ve Linux için yüksek performanslı sunucu çalışma zamanı, .NET Framework 'ün [Techempower kıyaslamaları](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)üzerinde en iyi şekilde gerçekleştirdiği bir Web çerçevesi

Performans ve ölçeklenebilirlik özellikle, yüzlerce mikro hizmetin çalıştığı mikro hizmet mimarileri ile ilgilidir. ASP.NET Core, sistemler çok daha az sayıda sunucu/sanal makine (VM) ile çalışır. Azaltılmış sunucular/VM 'Ler altyapı ve barındırma için maliyetleri kaydeder.

### <a name="side-by-side-net-versions-per-application-level"></a>Uygulama düzeyi başına yan yana .NET sürümleri

.NET 'in farklı sürümlerindeki bağımlılıklara sahip uygulamaları yüklemek için .NET 5 ' i öneririz. .NET 5, .NET 5 çalışma zamanının farklı sürümlerinin aynı makinede yan yana yüklenmesini destekler. Bu yan yana yükleme, her biri kendi .NET 5 sürümü (veya .NET Core 2,1 veya 3,1) üzerinde aynı sunucuda birden çok hizmete izin verir. Ayrıca riskleri düşürür ve uygulama yükseltmeleri ve BT işlemlerinde tasarruf sağlar.

.NET Framework ile yan yana yükleme mümkün değildir. Bu bir Windows bileşenidir ve aynı anda bir makinede yalnızca bir sürüm bulunabilir. .NET Framework her sürümü önceki sürümün yerini alır. .NET Framework sonraki bir sürümünü hedefleyen yeni bir uygulama yüklerseniz, önceki sürüm değiştirildiğinden makinede çalışan mevcut uygulamaları kesebilirsiniz.

## <a name="when-to-choose-net-framework"></a>Ne zaman .NET Framework seçin

.NET 5, yeni uygulamalar ve uygulama desenleri için önemli avantajlar sunar. Ancak, .NET Framework birçok mevcut senaryo için doğal seçim olmaya devam eder ve bu nedenle .NET Framework tüm sunucu uygulamaları için .NET 5 ile değiştirilmez.

### <a name="current-net-framework-applications"></a>Geçerli .NET Framework uygulamaları

Çoğu durumda, mevcut uygulamalarınızı .NET 5 ' e geçirmeniz gerekmez. Bunun yerine, ASP.NET Core ' de yeni bir Web hizmeti yazma gibi, mevcut bir uygulamayı genişletmekle birlikte .NET 5 ' in kullanılması önerilir.

### <a name="third-party-libraries-or-nuget-packages-not-available-for-net-5"></a>Üçüncü taraf kitaplıkları veya NuGet paketleri .NET 5 için kullanılamaz

.NET Standard .NET 5 de dahil olmak üzere tüm .NET uygulamalarında kod paylaşmaya izin verebilir. .NET Standard 2,0 ile bir uyumluluk modu .NET Standard ve .NET 5 projelerinin .NET Framework kitaplıklarına başvurmasına olanak tanır. Daha fazla bilgi için bkz. [.NET Framework kitaplıkları Için destek](whats-new/whats-new-in-dotnet-standard.md#support-for-net-framework-libraries).

.NET Framework yalnızca kitaplıkların veya NuGet paketlerinin .NET Standard veya .NET 5 ' te kullanılamayan teknolojileri kullanması durumunda kullanmanız gerekir.

### <a name="net-technologies-not-available-for-net-5"></a>.NET teknolojileri .NET 5 için kullanılamaz

Bazı .NET Framework teknolojileri .NET 5 sürümünde kullanılamaz. Aşağıdaki listede, .NET 5 ' te bulunmayan en yaygın teknolojiler gösterilmektedir:

- ASP.NET Web Forms uygulamalar: ASP.NET Web Forms yalnızca .NET Framework kullanılabilir. ASP.NET Core, ASP.NET Web Forms için kullanılamaz.

- ASP.NET Web Pages uygulamaları: ASP.NET Web Pages ASP.NET Core.

- WCF Hizmetleri uygulama. .NET 5 ' ten WCF hizmetlerini kullanmak için bir [WCF istemci kitaplığı](https://github.com/dotnet/wcf) olsa da, WCF sunucu uygulamasının şu anda yalnızca .NET Framework kullanılabilir.

- İş akışı ile ilgili hizmetler: Windows Workflow Foundation (WF), Workflow Services (tek bir hizmette WCF + WF) ve WCF Veri Hizmetleri (eskiden "ADO.NET Data Services" olarak bilinirdi) yalnızca .NET Framework kullanılabilir.

- Dil desteği: Visual Basic ve F # Şu anda .NET 5 ' te destekleniyor, ancak tüm proje türleri için desteklenmiyor. Desteklenen proje şablonlarının listesi için bkz. [DotNet New Için şablon seçenekleri](../core/tools/dotnet-new.md#arguments).

### <a name="platform-doesnt-support-net-5"></a>Platform .NET 5 ' i desteklemiyor

Bazı Microsoft veya üçüncü taraf platformları .NET 5 ' i desteklemez. Bazı Azure Hizmetleri, .NET 5 ' te tüketim için henüz kullanılamayan bir SDK sağlar. Bu gibi durumlarda, istemci SDK 'Sı yerine eşdeğer REST API kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET ve ASP.NET Core arasında seçim yapın](/aspnet/core/choose-aspnet-framework)
- [.NET Framework'ü hedefleyen ASP.NET Core](/aspnet/core/introduction-to-aspnet-core?view=aspnetcore-2.2&preserve-view=true#aspnet-core-targeting-net-framework)
- [Hedef çerçeveler](frameworks.md)
- [.NET tanıtımı](../core/introduction.md)
- [.NET Framework 'den .NET 5 ' e taşıma](../core/porting/index.md)
- [.NET ve Docker’a Giriş](../core/docker/introduction.md)
- [.NET bileşenlerine genel bakış](components.md)
- [.NET mikro hizmetleri. Kapsayıcılı .NET uygulamaları için mimari](../architecture/microservices/index.md)
