---
title: Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim
description: Hangi .NET uygulaması üzerinde .NET içinde sunucu uygulama oluştururken dikkate almanız gereken kılavuzu.
author: cartermp
ms.author: mairaw
ms.date: 06/19/2018
ms.openlocfilehash: a9eaeae515041ee1d99ede5b004ecc85e453de2d
ms.sourcegitcommit: 640cee8fc5d256cdd80e5b80240469feac10499e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/21/2018
ms.locfileid: "36298194"
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim yapma

.NET ile sunucu tarafı uygulamalar oluşturmak için iki desteklenen uygulamaları vardır: .NET Framework ve .NET Core. Her ikisi de aynı bileşenlerin çoğu paylaşabilir ve kodu arasında iki paylaşabilirsiniz. Bununla birlikte, ikisi arasındaki temel farklar vardır ve tercih ettiğiniz gerçekleştirmek istediğiniz yere bağlıdır.  Bu makale, ne zaman her kullanılacağı hakkında yönergeler sağlar.

Sunucu uygulaması için .NET Core kullanmak zaman:

* Platformlar arası gereksinimleri vardır.
* Mikro hedeflediğiniz.
* Docker kapsayıcıları kullanıyor.
* Yüksek performanslı ve ölçeklenebilir sistemlerinin gerekir.
* Uygulama başına yan yana .NET sürümleri gerekir.

Sunucu uygulaması için .NET Framework kullanan zaman:

* Uygulamanız şu anda .NET Framework (geçirmek yerine genişletmek için önerilir) kullanır.
* Uygulamanız .NET Core için üçüncü taraf .NET kitaplıklarına veya NuGet paketlerini kullanılamaz kullanır.
* Uygulamanız için .NET Core kullanılamaz .NET teknolojilerini kullanır.
* Uygulamanız .NET Core desteklemeyen bir platform kullanır.

## <a name="when-to-choose-net-core"></a>.NET Core seçmek ne zaman

Aşağıdaki bölümlerde daha ayrıntılı bir açıklaması .NET Core çekme daha önce belirtilen nedenlerini ve verin.

### <a name="cross-platform-needs"></a>Platformlar arası gerekiyor

Birden çok Platformu (Windows, Linux ve macOS) çalıştırmak için uygulama (web/hizmet) gereksinimlerinizi .NET Core kullanıyorsanız.

.NET core, geliştirme iş istasyonu olarak yukarıda sözü edilen işletim sistemlerini destekler. Visual Studio, Windows ve macOS bir tümleşik geliştirme ortamı (IDE) sağlar. MacOS, Linux ve Windows çalıştıran Visual Studio Code de kullanabilirsiniz. Visual Studio Code .NET hata ayıklama ve IntelliSense dahil çekirdek destekler. Sublime, Emacs ve VI, gibi çoğu üçüncü taraf düzenleyicileri .NET Core'u kullanmaya çalışır. Bu üçüncü taraf düzenleyicileri Düzenleyicisi IntelliSense alma kullanarak [Omnisharp](https://www.omnisharp.net/). Ayrıca herhangi bir kod düzenleyicisini kaçının ve doğrudan kullanmak [.NET Core CLI araçlarını](../core/tools/index.md), desteklenen tüm platformlar için kullanılabilir.

### <a name="microservices-architecture"></a>Mikro mimarisi

Mikro mimarisi, hizmet sınırından bir karışımını teknolojileri sağlar. Bu teknoloji karışımı aşamalı bir .NET Core embrace diğer mikro veya hizmetleri iş yeni mikro için etkinleştirir. Örneğin, mikro veya .NET Framework, Java, Ruby veya diğer tek yapılı teknolojileri ile geliştirilen Hizmetleri karıştırabilirsiniz.

Birçok altyapı platformda kullanılabilir. [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) büyük ve karmaşık mikro hizmet sistemler için tasarlanmıştır. [Azure uygulama hizmeti](https://azure.microsoft.com/services/app-service/) durum bilgisiz mikro için iyi bir seçimdir. Docker üzerinde tabanlı mikro alternatifleri sığacak mikro yaklaşımı, her türlü açıklandığı gibi [kapsayıcıları](#containers) bölümü. Tüm bu platformlar, mikro barındırmak için ideal hale ve .NET Core desteği.

Mikro mimarisi hakkında daha fazla bilgi için bkz: [.NET mikro. Mimari kapsayıcılı .NET uygulamaları için](microservices-architecture/index.md).

### <a name="containers"></a>Kapsayıcılar

Kapsayıcıları genellikle mikro mimarisi ile birlikte kullanılır. Kapsayıcılar, web uygulamaları veya herhangi bir mimari modeliyle izleyin Hizmetleri containerize için de kullanılabilir. .NET framework üzerinde Windows kapsayıcıları kullanılabilir, ancak .NET Core basit yapısını ve modülerlik kılar kapsayıcıları için daha uygun bir seçenektir. Oluşturma ve bir kapsayıcı dağıtma, kendi görüntü boyutunu .NET çerçevesi ile .NET Core ile çok daha küçük. Platformlar arası olduğu için sunucu uygulamalarını Linux Docker kapsayıcılara, örneğin dağıtabilirsiniz.

Docker kapsayıcıları barındırılması kendi Linux veya Windows altyapınızı ya da bir bulut hizmeti gibi [Azure kapsayıcı hizmeti](https://azure.microsoft.com/services/container-service/). Azure kapsayıcı hizmeti yönetmek, düzenlemek ve bulut kapsayıcı tabanlı uygulamalarda ölçeklendirin.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Yüksek performanslı ve ölçeklenebilir sistemleri gereksinimini

Sisteminizin olası en iyi performans ve ölçeklenebilirlik, .NET Core ve ASP.NET Core gerektiği zaman, en iyi seçenekler belirtilmiştir. Windows Server ve Linux yapar .NET üst gerçekleştirmek için yüksek performanslı sunucu çalışma zamanı üzerinde framework web [TechEmpower kıyaslamaları](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Performans ve ölçeklenebilirlik mikro yüzlerce çalıştırdığı mikro mimari için özellikle ilgili. ASP.NET Core ile sistemleri kadar daha az sayıda sunucuları/sanal makine (VM) ile çalıştırın. Azaltılmış sunucuları/VMs, altyapı ve barındırma maliyetlerini kaydedin.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Uygulama düzeyinde başına .NET sürümlerinin yan yana gereksinimini

Farklı sürümlerini .NET bağımlılıkları olan uygulamalar yüklemek için .NET Core öneririz. .NET core .NET çekirdeği çalışma zamanı ile aynı makinede farklı sürümlerinin yan yana yüklemesini sağlar. Bu yan yana yükleme, aynı sunucuda, her biri kendi sürümü .NET Core üzerinde birden fazla hizmet sağlar. Ayrıca, riskleri azaltır ve para uygulama yükseltmeleri ve BT işlemleri kaydeder.

## <a name="when-to-choose-net-framework"></a>.NET Framework seçmek ne zaman

.NET core yeni uygulamalar ve uygulama düzenleri için önemli avantajlar sunar. Ancak, .NET Framework birçok varolan senaryoları için doğal seçimi kadar devam eder ve bu nedenle .NET Framework tarafından .NET Core tüm sunucu uygulamaları için değiştirilir değil.

### <a name="current-net-framework-applications"></a>Geçerli .NET Framework uygulamaları

Çoğu durumda, mevcut uygulamalarınızı .NET Core geçirmek gerekmez. Bunun yerine, önerilen yaklaşım ASP.NET Core yeni bir web hizmeti yazma gibi varolan bir uygulama, genişletme gibi .NET Core kullanmaktır.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>Üçüncü taraf .NET kitaplıklarına veya NuGet paketlerini kullanılamaz .NET Core için kullanılacak bir gereksinimi

Kitaplıklar, .NET standart benimsemenin hızla. .NET standart paylaşım kod .NET Core dahil olmak üzere tüm .NET uygulamaları etkinleştirir. .NET standart 2.0 ile daha kolay şudur:

- API yüzeyi çok daha büyük hale geldi. 
- .NET Framework uyumluluk modu sunulmuştur. Bu uyumluluk modu, .NET Framework kitaplıkları başvurmak .NET standart/.NET Core projeleri sağlar. Uyumluluk modu hakkında daha fazla bilgi için bkz: [.NET standart 2.0 Duyurusu](https://blogs.msdn.microsoft.com/dotnet/2017/08/14/announcing-net-standard-2-0/).

Burada kitaplıkları veya NuGet paketlerini .NET standart/.NET Core kullanılamaz teknolojilerini kullanan durumlarda yalnızca .NET Framework kullanmanız gerekir.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>.NET Core için kullanılabilir değil .NET teknolojileri kullanmaya gerek

Bazı .NET Framework teknolojiler .NET Core kullanılamaz. Bunlardan bazıları daha sonra .NET Core sürümlerde kullanılabilir olabilir. Başkaları tarafından .NET Core hedeflenen yeni uygulama desenler için uygulanmaz ve hiçbir zaman kullanılabilir olabilir. Aşağıdaki listede, .NET Core bulunamadı en yaygın teknolojiler gösterilmektedir:

* ASP.NET Web Forms uygulamaları: ASP.NET Web Forms bulunan ve yalnızca .NET Framework. ASP.NET Core ASP.NET Web formları için kullanılamaz. ASP.NET Web Forms .NET Core getirmek için plan yok.

* ASP.NET Web Pages uygulamaları: ASP.NET Web sayfaları, ASP.NET Core dahil değildir. ASP.NET Core [Razor sayfalarının](/aspnet/core/mvc/razor-pages/) Web sayfalarıyla birçok benzerlikler vardır.

* WCF hizmetleri uygulaması. Olduğunda bile bir [WCF istemci Kitaplığı](https://github.com/dotnet/wcf) .NET Core WCF hizmetlerini kullanmak için WCF sunucu şu anda yalnızca .NET Framework kullanılabilir uygulamasıdır. Bu senaryo, .NET Core için geçerli planının bir parçası değil, ancak gelecek için kabul.

* İş akışı ile ilgili hizmetlerin: Windows Workflow Foundation (WF), (WCF + tek bir hizmette WF) iş akışı hizmetleri ve WCF Veri Hizmetleri (eski adıyla "ADO.NET Veri Hizmetleri"), yalnızca .NET Framework kullanılabilir.  WCF + WF/WF/WCF Veri Hizmetleri için .NET Core getirmek için plan yok.

* Dil desteği: Visual Basic ve F # şu anda desteklenen .NET Core, ancak tüm proje türleri için değil. Desteklenen proje şablonları listesi için bkz: [dotnet yeni şablonu seçeneklerini](../core/tools/dotnet-new.md#arguments).

Resmi yol haritası yanı sıra diğer çerçeveler .NET Core için bağlantı noktası kurulmuş vardır. Tam listesi için bkz: olarak işaretlenmiş CoreFX sorunları [bağlantı noktası çekirdek](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Bu liste, bu bileşenler için .NET Core getirmek için Microsoft'un taahhüdü temsil etmez. Yalnızca bunu isteğini topluluktan yakalama. İşaretlenen bileşenleri hakkında önemli `port-to-core`, github'da tartışmalara katılın. Ve şeyin eksik olduğunu düşünüyorsanız, yeni bir sorun dosya [CoreFX depo](https://github.com/dotnet/corefx/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>.NET Core desteklemeyen bir platform kullanmanız gerekmez

Bazı Microsoft veya üçüncü taraf platformları .NET Core desteklemez. Örneğin, .NET Framework hizmet doku durum bilgisi olan güvenilir hizmetler ve hizmet doku Reliable Actors gerektiren gibi bazı Azure Hizmetleri. Başka bir hizmetler, .NET Core üzerinde bir SDK tüketimi için henüz kullanılamıyor sağlar. Tüm Azure hizmetlerini .NET Core kullandıkça geçici bir durum budur. Bu arada, eşdeğer REST API istemcisi SDK yerine her zaman kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
 [ASP.NET ve ASP.NET Core arasında seçim yapma](/aspnet/core/choose-aspnet-framework)  
 [.NET Core Kılavuzu](../core/index.md)  
 [.NET Core için .NET Framework'bağlantı noktası oluşturma](../core/porting/index.md)  
 [Docker Üzerinde .NET Framework Kılavuzu](../framework/docker/index.md)  
 [.NET bileşenleri'ne genel bakış](components.md)  
 [.NET mikro. Kapsayıcılı .NET uygulamaları için mimarisi](microservices-architecture/index.md)
