---
title: Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim yapın
description: .NET ' te bir sunucu uygulaması oluştururken göz önünde bulundurmanız gereken .NET uygulaması hakkında bir kılavuz.
author: cartermp
ms.author: mairaw
ms.date: 06/19/2018
ms.openlocfilehash: b2b9e15cfdfd63d070ae94c29a9f2d1a5b5c87b2
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75738675"
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma

.NET Core: .NET Framework ve .NET Core ile sunucu tarafı uygulamalar oluşturmaya yönelik iki desteklenen uygulama vardır. Her ikisi de aynı bileşenlerden birçoğunu paylaşır ve iki arasında kod paylaşabilirsiniz. Bununla birlikte, ikisi arasında temel farklılıklar vardır ve seçiminiz, gerçekleştirmek istediğiniz seçeneğe bağlıdır.  Bu makale, her birinin ne zaman kullanılacağı hakkında rehberlik sağlar.

Şu durumlarda sunucu uygulamanız için .NET Core kullanın:

- Platformlar arası gereksinimleriniz var.
- Mikro hizmetleri hedefliyorsanız.
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

.NET Core, geliştirme iş istasyonunuz olarak yukarıda bahsedilen işletim sistemlerini destekler. Visual Studio, Windows ve macOS için tümleşik bir geliştirme ortamı (IDE) sağlar. MacOS, Linux ve Windows üzerinde çalışan Visual Studio Code de kullanabilirsiniz. Visual Studio Code, IntelliSense ve hata ayıklama dahil .NET Core 'u destekler. Alt Lime, Emacs ve VI gibi üçüncü taraf düzenleyicilerin çoğu .NET Core ile çalışır. Bu üçüncü taraf düzenleyiciler, [Omnisharp](https://www.omnisharp.net/)kullanarak düzenleyici IntelliSense 'i alır. Ayrıca, herhangi bir kod düzenleyiciden kaçınabilir ve desteklenen tüm platformlar için kullanılabilen [.NET Core CLI araçları](../core/tools/index.md)' nı doğrudan kullanabilirsiniz.

### <a name="microservices-architecture"></a>Mikro hizmetler mimarisi

Mikro hizmetler mimarisi, bir hizmet sınırı genelinde teknolojilerin karışımına izin verir. Bu teknoloji karışımı, diğer mikro hizmetler veya hizmetlerle çalışan yeni mikro hizmetler için .NET Core 'un aşamalı bir şekilde kullanılmasına izin vermez. Örneğin, .NET Framework, Java, Ruby veya diğer tek parçalı teknolojilerle geliştirilen mikro hizmetleri veya hizmetleri karıştırabilirsiniz.

Kullanılabilir çok sayıda altyapı platformu vardır. [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) , büyük ve karmaşık mikro hizmet sistemleri için tasarlanmıştır. [Azure App Service](https://azure.microsoft.com/services/app-service/) , durum bilgisi olmayan mikro hizmetler için iyi bir seçimdir. Docker tabanlı mikro hizmet alternatifleri, [kapsayıcılar](#containers) bölümünde açıklandığı gibi her türlü mikro hizmet yaklaşımını ister. Tüm bu platformlar .NET çekirdeğini destekler ve mikro hizmetlerinizin barındırılmasına yönelik ideal hale getirir.

Mikro hizmet mimarisi hakkında daha fazla bilgi için bkz [. .net mikro hizmetleri. Kapsayıcılı .NET uygulamaları için mimari](../architecture/microservices/index.md).

### <a name="containers"></a>Kapsayıcılar

Kapsayıcılar genellikle mikro hizmetler mimarisiyle birlikte kullanılır. Kapsayıcılar Ayrıca, herhangi bir mimari kalıbı izleyen Web uygulamalarını veya hizmetlerini kapsayıleştirmek için de kullanılabilir. .NET Framework, Windows kapsayıcılarında kullanılabilir, ancak .NET Core 'un modülerliği ve hafif doğası, kapsayıcılar için daha iyi bir seçenek sunar. Bir kapsayıcı oluştururken ve dağıttığınızda görüntünün boyutu .NET Core ile .NET Framework kıyasla çok daha küçüktür. Platformlar arası olduğundan, örneğin, Linux Docker kapsayıcılarına sunucu uygulamaları dağıtabilirsiniz.

Docker Kapsayıcıları kendi Linux veya Windows altyapınızda veya [Azure Kubernetes hizmeti](https://azure.microsoft.com/services/kubernetes-service/)gibi bir bulut hizmetinde barındırılabilir. Azure Kubernetes hizmeti, bulutta kapsayıcı tabanlı uygulamaları yönetebilir, düzenleyebilir ve ölçeklendirebilir.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Yüksek performanslı ve ölçeklenebilir sistemler için bir gereksinim

Sisteminizin olası en iyi performans ve ölçeklenebilirlik ihtiyacı olduğunda, .NET Core ve ASP.NET Core en iyi seçenekleriniz vardır. Windows Server ve Linux için yüksek performanslı sunucu çalışma zamanı, .NET Framework 'ün [Techempower kıyaslamaları](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext)üzerinde en iyi şekilde gerçekleştirdiği bir Web çerçevesi

Performans ve ölçeklenebilirlik özellikle, yüzlerce mikro hizmetin çalıştığı mikro hizmet mimarileri ile ilgilidir. ASP.NET Core, sistemler çok daha az sayıda sunucu/sanal makine (VM) ile çalışır. Azaltılmış sunucular/VM 'Ler altyapı ve barındırma için maliyetleri kaydeder.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Uygulama düzeyi başına .NET sürümlerinin yan yana ihtiyacı

.NET Core 'un farklı sürümlerindeki bağımlılıklara sahip uygulamaları yüklemek için .NET Core önerilir. .NET Core, .NET Core çalışma zamanının farklı sürümlerinin aynı makinede yan yana yüklenmesini sağlar. Bu yan yana yükleme, her biri kendi .NET Core sürümünde aynı sunucuda birden çok hizmete izin verir. Ayrıca riskleri düşürür ve uygulama yükseltmeleri ve BT işlemlerinde tasarruf sağlar.

## <a name="when-to-choose-net-framework"></a>Ne zaman .NET Framework seçin

.NET Core, yeni uygulamalar ve uygulama desenleri için önemli avantajlar sunar. Ancak .NET Framework, birçok mevcut senaryo için doğal seçim olmaya devam eder ve .NET Framework tüm sunucu uygulamaları için .NET Core ile değiştirilmez.

### <a name="current-net-framework-applications"></a>Geçerli .NET Framework uygulamaları

Çoğu durumda, mevcut uygulamalarınızı .NET Core 'a geçirmeniz gerekmez. Bunun yerine, ASP.NET Core ' de yeni bir Web hizmeti yazma gibi, mevcut bir uygulamayı genişletmekle birlikte .NET Core 'u kullanmak önerilen bir yaklaşımdır.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>.NET Core için mevcut olmayan üçüncü taraf .NET kitaplıklarını veya NuGet paketlerini kullanma gereksinimi

Kitaplıklar .NET Standard hızlı bir şekilde kullanılır. .NET Standard .NET Core dahil tüm .NET uygulamalarında kod paylaşmaya izin verebilir. .NET Standard 2,0 ile bu da daha kolay olur:

- API yüzeyi çok daha büyük hale geldi. 
- .NET Framework uyumluluk modu sunuldu. Bu uyumluluk modu .NET Standard/. NET Core projelerinin .NET Framework kitaplıklarına başvurmasına olanak tanır. Uyumluluk modu hakkında daha fazla bilgi edinmek için bkz. [duyurusu .NET Standard 2,0](https://devblogs.microsoft.com/dotnet/announcing-net-standard-2-0/).

Bu nedenle, yalnızca kitaplıkların veya NuGet paketlerinin .NET Standard/. NET Core 'da kullanılamayan teknolojileri kullanması durumunda, .NET Framework kullanmanız gerekir.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>.NET Core için kullanılamaz .NET teknolojilerini kullanma gereksinimi

Bazı .NET Framework teknolojileri .NET Core 'da kullanılamaz. Bunlardan bazıları daha sonraki .NET Core sürümlerinde kullanılabilir olabilir. Diğerleri, .NET Core tarafından hedeflenen yeni uygulama düzenlerine uygulanmaz ve hiçbir şekilde kullanılamaz. Aşağıdaki listede, .NET Core 'da bulunmayan en yaygın teknolojiler gösterilmektedir:

- ASP.NET Web Forms uygulamalar: ASP.NET Web Forms yalnızca .NET Framework mevcuttur. ASP.NET Core, ASP.NET Web Forms için kullanılamaz. .NET Core 'a ASP.NET Web Forms getirmek için bir plan yoktur.

- ASP.NET Web Pages uygulamaları: ASP.NET Web Pages ASP.NET Core. 

- WCF Hizmetleri uygulama. .NET Core 'dan WCF hizmetlerini kullanmak için bir [WCF-istemci kitaplığı](https://github.com/dotnet/wcf) olsa bıle, WCF sunucu uygulamasının şu anda yalnızca .NET Framework kullanılabilir. Bu senaryo, .NET Core için geçerli planın bir parçası değildir, ancak geleceğe göre değerlendirilir.

- İş akışı ile ilgili hizmetler: Windows Workflow Foundation (WF), Iş akışı hizmetleri (tek bir hizmette WCF + WF) ve WCF Veri Hizmetleri (eskiden "ADO.NET Data Services" olarak bilinirdi) yalnızca .NET Framework mevcuttur.  WF/WCF + WF/WCF Veri Hizmetleri .NET Core 'a getirmeye yönelik bir plan yoktur.

- Dil desteği: Visual Basic ve F# Şu anda .NET Core 'da desteklenir, ancak tüm proje türleri için desteklenmez. Desteklenen proje şablonlarının listesi için bkz. [DotNet New Için şablon seçenekleri](../core/tools/dotnet-new.md#arguments).

Resmi yol haritasını ek olarak, .NET Core 'a yönelik başka çerçeveler de vardır. Tam liste için bkz. [ana bağlantı noktası](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core)olarak Işaretlenmiş CoreFX sorunları. Bu liste, Microsoft 'un bu bileşenleri .NET Core 'a getirmeye yönelik bir taahhütünü temsil etmez. Bu, bunu yapmak için topluluktaki isteği yakalarlar. `port-to-core`olarak işaretlenen bileşenlerden herhangi birini düşünüyorsanız, GitHub 'daki tartışmalara katılın. Bir şeyin eksik olduğunu düşünüyorsanız, [.net deposunda](https://github.com/dotnet/runtime/issues/new)yeni bir sorun verin.

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>.NET Core desteklemeyen bir platform kullanmanız gerekir

Bazı Microsoft veya üçüncü taraf platformları .NET Core ' u desteklemez. Bazı Azure Hizmetleri, .NET Core kullanımı için henüz kullanılabilir olmayan bir SDK sağlar. Bu, tüm Azure hizmetlerinin .NET Core 'u kullanması halinde geçici bir durumda. Bu sırada, istemci SDK 'Sı yerine her zaman eşdeğer REST API kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET ve ASP.NET Core arasında seçim yapın](/aspnet/core/choose-aspnet-framework)
- [ASP.NET Core hedefleme .NET Framework](/aspnet/core#aspnet-core-targeting-net-framework)
- [Hedef çerçeveler](frameworks.md)
- [.NET Core Kılavuzu](../core/index.md)
- [.NET Framework 'den .NET Core 'a taşıma](../core/porting/index.md)
- [.NET ve Docker’a Giriş](../core/docker/introduction.md)
- [.NET bileşenlerine genel bakış](components.md)
- [.NET mikro hizmetleri. Kapsayıcılı .NET uygulamaları için mimari](../architecture/microservices/index.md)
