---
title: Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçin
description: Hangi .NET uygulamasının üzerinde. NET'te bir sunucu uygulaması derlerken, dikkate almanız gereken bir kılavuz.
author: cartermp
ms.author: mairaw
ms.date: 06/19/2018
ms.openlocfilehash: 01e7222ccd4a764f75481e58d4ac305daadfe1a8
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50034292"
---
# <a name="choosing-between-net-core-and-net-framework-for-server-apps"></a>Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim

.NET ile sunucu tarafı uygulamalar oluşturmak için iki desteklenen uygulamaları vardır: .NET Framework ve .NET Core. Her ikisi de aynı bileşenleri çoğunu paylaşmak ve ikisi arasında kod paylaşabilirsiniz. Bununla birlikte, ikisi arasındaki temel farklar vardır ve kendi seçtiğiniz gerçekleştirmek istediğiniz üzerinde bağlıdır.  Bu makalede, ne zaman her kullanılacağı hakkında yönergeler sağlar.

.NET Core için sunucu uygulamanızı kullanın. zaman:

* Platformlar arası ihtiyaçları vardır.
* Mikro hizmetler hedeflediğiniz.
* Docker kapsayıcılarını kullanıyor.
* Yüksek performanslı ve ölçeklenebilir sistemleri ihtiyacınız vardır.
* Uygulama başına yan yana .NET sürümleri gerekir.

.NET Framework için sunucu uygulamanızı kullanan olduğunda:

* Uygulamanızı .NET Framework (geçirmek yerine genişletmek için önerilir) şu anda kullanır.
* Uygulamanızı .NET Core için üçüncü taraf .NET kitaplıkları veya kullanılabilir değil NuGet paketlerini kullanır.
* Uygulamanızı .NET Core için kullanılamayan .NET teknolojilerini kullanır.
* Uygulamanızı .NET Core desteği olmayan bir platform kullanır.

## <a name="when-to-choose-net-core"></a>Ne zaman .NET Core seçin

Aşağıdaki bölümlerde, .NET Core çekme için yukarıda belirtilen nedenlerden daha ayrıntılı bir açıklama sağlar.

### <a name="cross-platform-needs"></a>Platformlar arası gerekiyor

Uygulama (web/hizmet) gereksinimlerinizi birden çok platformda (Windows, Linux ve macOS) çalıştırmak için .NET Core kullanıyorsanız.

.NET core geliştirme iş istasyonunuzu daha önce sözü edilen işletim sistemlerini destekler. Visual Studio, Windows ve macOS için bir tümleşik geliştirme ortamı (IDE) sağlar. Ayrıca, macOS, Linux ve Windows üzerinde çalışan Visual Studio Code kullanabilirsiniz. Visual Studio Code hata ayıklama ve IntelliSense dahil olmak üzere .NET Core, destekler. Çoğu üçüncü taraf düzenleyiciler, Sublime Emacs ve gibi VI, .NET Core ile çalışır. Bu üçüncü taraf düzenleyicileri Düzenleyicisi IntelliSense Al kullanarak [Omnisharp](https://www.omnisharp.net/). Ayrıca herhangi bir kod düzenleyici önlemek ve doğrudan [.NET Core CLI Araçları](../core/tools/index.md), desteklenen tüm platformlar için kullanılabilir.

### <a name="microservices-architecture"></a>Mikro hizmet mimarisi

Bir mikro hizmet mimarisi, bir hizmet sınırında teknolojilerinin bir karışımını sağlar. Bu teknoloji karışımı diğer mikro hizmetler veya hizmetler ile çalışan yeni mikro hizmetler için .NET Core, aşamalı bir embrace sağlar. Örneğin, mikro hizmetler veya .NET Framework, Java, Ruby veya tek parçalı diğer teknolojiler ile geliştirilen Hizmetleri karıştırabilirsiniz.

Birçok altyapı platformda kullanılabilir. [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) büyük ve karmaşık bir mikro hizmet sistemler için tasarlanmıştır. [Azure App Service](https://azure.microsoft.com/services/app-service/) durum bilgisi olmayan mikro hizmetler için iyi bir seçimdir. Mikro hizmetler alternatifleri üzerinde Docker tabanlı mikro hizmetler yaklaşımı, herhangi bir türden açıklandığı gibi uygun [kapsayıcıları](#containers) bölümü. Bu tüm platformlarda, .NET Core desteği ve mikro hizmetlerin barındırmak için ideal hale getirilmeleri.

Mikro hizmet mimarisi hakkında daha fazla bilgi için bkz: [.NET mikro Hizmetleri. Kapsayıcılı .NET uygulamaları mimarisi](microservices-architecture/index.md).

### <a name="containers"></a>Kapsayıcılar

Kapsayıcılar, mikro hizmet mimarisi ile birlikte sık kullanılır. Kapsayıcılar, web uygulamaları veya herhangi bir mimari deseni izleyen Hizmetleri kapsayıcılı hale getirme için de kullanılabilir. .NET framework Windows kapsayıcılarında kullanılabilir, ancak basit bir .NET Core doğasını ve modülerlik kılar kapsayıcılar için daha iyi bir seçenek. Oluşturma ve kapsayıcı dağıtma, kendi görüntüsünün boyutu .NET Framework ile .NET Core küçüktür. Platformlar arası olduğundan, sunucu uygulamaları için Linux Docker kapsayıcılar, örneğin dağıtabilirsiniz.

Docker kapsayıcıları barındırılabilir Linux veya Windows kendi altyapınızı ya da bir bulut hizmeti gibi [Azure Container Service](https://azure.microsoft.com/services/container-service/). Azure Container Service, yönetme, düzenlemeyi ve kapsayıcı tabanlı uygulamaları bulutta ölçeklendirin.

### <a name="a-need-for-high-performance-and-scalable-systems"></a>Yüksek performanslı ve ölçeklenebilir sistemleri için bir gereksinimi

Sisteminizi iyi olası performans ve ölçeklenebilirlik, .NET Core ve ASP.NET Core gerektiğinde olan en iyi seçenekleri. Windows Server ve Linux kolaylaştırır .NET üst gerçekleştirmek için yüksek performanslı sunucu çalışma zamanı üzerinde framework web [TechEmpower Kıyaslama](https://www.techempower.com/benchmarks/#hw=ph&test=plaintext).

Performans ve ölçeklenebilirlik mikro hizmetler yüzlerce çalıştığı mikro hizmet mimarileri için yakından ilgili olan. ASP.NET Core ile sistemleri çok daha az sayıda sunucuları/sanal makineler (VM) ile çalıştırın. Azaltılmış sunucuları/VMs, altyapı ve barındırma maliyetlerinden tasarruf.

### <a name="a-need-for-side-by-side-of-net-versions-per-application-level"></a>Uygulama düzeyinde başına .NET sürümlerinin yan yana gereksinimini

Farklı sürümleri .NET ilgili bağımlılıkları olan uygulamaları yüklemek için .NET Core öneririz. .NET core, .NET Core çalışma zamanı ile aynı makinede farklı sürümlerinin yan yana yüklemesini sağlar. Bu yan yana yükleme birden fazla hizmeti aynı sunucuda, her biri kendi sürümünde .NET Core sağlar. Ayrıca, riskleri azaltır ve para uygulama yükseltmeleri ve BT işlemleri kaydeder.

## <a name="when-to-choose-net-framework"></a>Ne zaman .NET Framework seçin

.NET core için yeni uygulamalar ve uygulama desenleri önemli avantajlar sunar. Ancak, .NET Framework mevcut birçok senaryo için doğal seçenek olmaya devam eder ve bu nedenle .NET Framework ile .NET Core tüm sunucu uygulamaları için değiştirilir değil.

### <a name="current-net-framework-applications"></a>Geçerli .NET Framework uygulamaları

Çoğu durumda, mevcut uygulamalarınızı .NET Core geçişi gerekmez. Bunun yerine, önerilen yaklaşım yeni bir web hizmeti ASP.NET Core yazma gibi mevcut bir uygulamayı yeniden genişletirken .NET Core kullanmaktır.

### <a name="a-need-to-use-third-party-net-libraries-or-nuget-packages-not-available-for-net-core"></a>.NET Core için üçüncü taraf .NET kitaplıkları veya kullanılabilir değil NuGet paketlerini kullanmak için bir gereksinim

Hızlı bir şekilde kitaplıkları .NET Standard benimsemektedir. .NET standard paylaşım kod arasında tüm .NET uygulamalarının .NET Core dahil olmak üzere sağlar. .NET Standard 2.0 ile bunu daha da kolaydır:

- Bir API yüzeyi, çok daha büyük hale geldi. 
- .NET Framework uyumluluk modu kullanıma sunuldu. Bu uyumluluk modu, .NET Framework kitaplıkları başvurmak .NET standart/.NET Core projeleri sağlar. Uyumluluk modu hakkında daha fazla bilgi için bkz: [.NET Standard 2.0 ile tanışın](https://blogs.msdn.microsoft.com/dotnet/2017/08/14/announcing-net-standard-2-0/).

Burada kitaplıkları veya NuGet paketlerini de .NET standart/.NET Core kullanılamayan teknolojilerini kullanan durumlarda yalnızca .NET Framework kullanmanız gerekir.

### <a name="a-need-to-use-net-technologies-not-available-for-net-core"></a>.NET Core için kullanılabilir değil .NET teknolojileri kullanmaya gerek

' De .NET Core bazı .NET Framework teknolojilerini kullanılamaz. Bunların bazılarını daha sonra .NET Core sürümlerinde kullanılabilir olabilir. Diğer .NET Core tarafından hedeflenen yeni uygulama desenleri için geçerli değildir ve hiçbir zaman kullanılabilir. Aşağıdaki liste, en yaygın teknolojileri de .NET Core bulunamadı gösterir:

* ASP.NET Web formları uygulamalarını: ASP.NET Web Forms yüklenebilir yalnızca .NET Framework. ASP.NET Core, ASP.NET Web formları için kullanılamaz. .NET Core ile ASP.NET Web Forms getirmek için herhangi bir plan yoktur.

* ASP.NET Web Pages uygulamaları: ASP.NET Web sayfaları, ASP.NET Core dahil edilmemiş. 

* WCF hizmetleri uygulaması. Olduğunda bile bir [WCF istemci Kitaplığı](https://github.com/dotnet/wcf) .NET Core WCF hizmetlerinden kullanmak için WCF sunucusu uygulaması şu anda yalnızca .NET Framework içinde kullanılabilir. Bu senaryo, .NET Core için geçerli planın bir parçası değildir ancak geleceğe yönelik değerlendiriliyor.

* İş akışı ile ilgili hizmetler: Windows Workflow Foundation (WF) iş akışı Hizmetleri (WCF + WF tek bir hizmette) ve WCF Veri Hizmetleri (eski adıyla "ADO.NET Data Services" da bilinir), yalnızca .NET Framework içinde kullanılabilir.  WF/WCF + WF/WCF Data Services için .NET Core getirmek için herhangi bir plan yoktur.

* Dil desteği: Visual Basic ve F # şu anda desteklenen .NET Core, ancak tüm proje türleri için değil. Desteklenen proje şablonları listesi için bkz. [dotnet yeni şablon seçeneklerini](../core/tools/dotnet-new.md#arguments).

Resmi yol haritası yanı sıra .NET Core için unity'nin için diğer çerçeveler vardır. Olarak işaretlenmiş Corefx'te sorunlar tam listesi için bkz. [bağlantı noktası çekirdek](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aport-to-core). Bu liste, bu bileşenler, .NET Core getirmek için Microsoft'un taahhüdü temsil etmez. Bunlar yalnızca bunu yapma arzusu topluluğundan yakalayacağınızı. Olarak işaretlenmiş bileşenleri hakkında dikkatli olun `port-to-core`, GitHub üzerindeki tartışmaların katılın. Bir şeyler eksik olduğunu düşünüyorsanız, yeni bir konu dosya [Corefx'te depo](https://github.com/dotnet/corefx/issues/new).

### <a name="a-need-to-use-a-platform-that-doesnt-support-net-core"></a>.NET Core desteği olmayan bir platform kullanın gerekmez

.NET Core, bazı Microsoft veya üçüncü taraf platformları desteklemez. Örneğin, Service Fabric durum bilgisi olan Reliable Services ve Service Fabric Reliable Actors, .NET Framework gerektiren gibi bazı Azure Hizmetleri. Bazı diğer hizmetler üzerinde .NET Core SDK tüketimi için henüz kullanılamıyor sağlar. Tüm Azure hizmetlerinin .NET Core kullanırken geçici bir durumda budur. Bu arada, eşdeğer REST API İstemci SDK'sı yerine her zaman kullanabilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

* [ASP.NET ve ASP.NET Core arasında seçim yapma](/aspnet/core/choose-aspnet-framework)
* [.NET Framework'ü hedefleyen ASP.NET Core](/aspnet/core#aspnet-core-targeting-net-framework)
* [Hedef çerçeveler](frameworks.md)
* [.NET Core Kılavuzu](../core/index.md)  
* [.NET Core ile .NET Framework'ten taşıma](../core/porting/index.md)  
* [Docker Üzerinde .NET Framework Kılavuzu](../framework/docker/index.md)  
* [.NET bileşenleri'ne genel bakış](components.md)  
* [.NET mikro Hizmetleri. Kapsayıcılı .NET uygulamaları mimarisi](microservices-architecture/index.md)
