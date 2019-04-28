---
title: .NET Core ve Açık Kaynak
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5eeef28f9a1d81ffa6328bfa5f2a8ed5295b47aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61644154"
---
# <a name="net-core-and-open-source"></a>.NET Core ve Açık Kaynak
Bu konu nedir .NET Core ve daha fazla bilgi nasıl bulabileceğinizi gösterilmektedir, kısa bir genel bakış sağlar. .NET Core için konular tam listesi için bkz [.NET Core Kılavuzu](../../core/index.md).
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a>.NET Core nedir?  
 .NET core olan bir genel amaçlı, .NET Standard modüler, platformlar arası ve açık kaynak uygulamasıdır. .NET Framework ile aynı API'ler birçoğunu içerir (ancak .NET Core, daha küçük bir kümesi) ve çeşitli işletim sistemlerini destekleyen ve yonga hedef çalışma zamanı, framework, derleyici ve araçları bileşenleri içerir. .NET Core uygulaması, öncelikli olarak ASP.NET Core iş yükleri aynı zamanda gerektiğinden temelli ve daha modern bir uygulama istediğiniz. Cihaz, Bulut ve katıştırılmış IOT senaryoları kullanılabilir.  
  
 .NET Core ile çalışmaya başlamak için lütfen [.NET Core giriş sayfası](https://www.microsoft.com/net/core).  
  
 .NET Core temel özellikleri şunlardır:  
  
- **Platformlar arası:** .NET Core gerekir ve bu kod, platform hedefi bağımsız olarak yeniden uygulama özellikleri uygulamak için temel işlevleri sağlar. Şu anda üç ana işletim sistemlerini (OS) da destekler: Windows, Linux ve Macos'ta. Uygulamalar ve desteklenen işletim sistemleri arasında değiştirilmeden çalıştırılmasını kitaplıklar yazabilirsiniz. Desteklenen işletim sistemlerinin listesini görmek için ziyaret [.NET Core yol haritası](https://github.com/dotnet/core/blob/master/roadmap.md).
  
- **Açık kaynak:** .NET Core Hizmetleri altında çok sayıda proje biridir [.NET Foundation](https://www.dotnetfoundation.org/) ve kullanılabilir [GitHub](https://github.com/).  .NET Core açık kaynaklı proje olarak sahip daha saydam bir geliştirme süreci yükseltir ve etkin ve bağlı bir topluluk yükseltir.  
  
- **Esnek dağıtım:** uygulamanızı dağıtmak için iki ana yolu vardır: framework bağımlı dağıtım veya kendi içinde dağıtım. Framework bağımlı dağıtım, yalnızca, uygulama ve üçüncü taraf bağımlılıklarının yüklendiğinden ve uygulamanızı bir bulunması için .NET Core sistem genelinde sürümüne bağlıdır.  Kendi içinde dağıtım, uygulamanızı oluşturmak için kullanılan .NET Core sürümünün Ayrıca uygulama ve üçüncü taraf bağımlılıkları birlikte dağıtılır ve yan yana çalıştırabilirsiniz diğer sürümleriyle birlikte.    Daha fazla bilgi için [.NET Core uygulaması dağıtımını](../../core/deploying/index.md).

- **Modüler:** .NET Core olduğundan modüler küçük derleme paketlerinde NuGet yayımlanır. Temel işlevlerini çoğunu içeren bir büyük derleme yerine, .NET Core daha küçük bir özellik merkezli paketleri olarak kullanılabilir hale getirilir. Bu bizim için daha Çevik bir geliştirme modeli sağlar ve, uygulamanızı yalnızca gereksinim duyduğunuz NuGet paketlerini içerecek şekilde iyileştirmenize imkan sağlar. Hizmet, Gelişmiş performans ve ödeme what-,-Öde modelinde maliyetleri azaltan azaltılmış daha sıkı güvenlik, daha küçük bir uygulama yüzey alanını avantajları şunlardır.  
  
## <a name="the-net-core-platform"></a>.NET Core platformu  
 .NET Core platformu yönetilen derleyiciler, çalışma zamanı, taban sınıfı kitaplıkları ve ASP.NET Core gibi çok sayıda uygulama modelleri içeren çeşitli bileşenlerinin yapılır. Farklı bileşenleri hakkında daha fazla bilgi ve, aşağıdaki ziyaret ederek bağlı [GitHub](https://github.com/) depolar:  
  
- [.NET Core](https://github.com/dotnet/core)  
  
- [Corefx'te - .NET Core temel kitaplıkları](https://github.com/dotnet/corefx)  
  
- [CoreCLR - .NET Core çalışma zamanı](https://github.com/dotnet/coreclr)  
  
- [CLI - .NET Core komut satırı araçları](https://github.com/dotnet/cli)  
  
- [Roslyn - .NET derleyici platformu](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/aspnet/home)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET core giriş sayfası](https://www.microsoft.com/net/core)
- [.NET Core Kılavuzu](../../core/index.md)
- [ASP.NET Core belgeleri](/aspnet/core/)
