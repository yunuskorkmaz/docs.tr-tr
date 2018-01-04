---
title: ".NET Core ve Açık Kaynak"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cc41a51a9c85b84f2f5365eb1650ebec37888652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="net-core-and-open-source"></a>.NET Core ve Açık Kaynak
Bu konuda ne .NET Core olduğu ve nasıl daha fazla bilgi bulabilirsiniz gösterir kısa bir genel bakış sağlar. .NET Core konuları tam listesi için ziyaret edin [.NET Core Kılavuzu](../../core/index.md).
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a>.NET Core nedir?  
 .NET core genel amaçlı, modüler, platformlar arası ve açık kaynak uygulaması .NET standart olur. .NET Framework ile aynı API'ler çoğunu içerir (ancak .NET Core kümesidir daha küçük) ve çeşitli işletim sistemlerini destekleyen ve yonga hedefleri çalışma zamanı, framework, derleyici ve araçları bileşenleri içerir. .NET Core uygulama öncelikli olarak ASP.NET Core iş yükleri de gerektiğinden gereksiniminden ve daha modern uygulama işlemleriniz. Cihaz, Bulut ve katıştırılmış IOT senaryolarını kullanılabilir.  
  
 .NET Core'u kullanmaya başlamak için lütfen ziyaret [.NET Core giriş sayfası](https://www.microsoft.com/net/core).  
  
 .NET Core temel özellikleri aşağıda verilmiştir:  
  
-   **Platformlar arası:** .NET Core gerekir ve bu kod, platform hedefi bağımsız olarak yeniden uygulama özelliklerini uygulamak için anahtar işlevselliği sağlar. Şu anda üç ana işletim sistemlerini (OS) desteklemektedir: Windows, Linux ve macOS. Uygulamalar ve desteklenen işletim sistemleri arasında değiştirilmemiş çalıştırmak kitaplıkları yazabilirsiniz. Desteklenen işletim sistemlerinin listesini görmek için ziyaret [.NET Core yol haritası](https://github.com/dotnet/core/blob/master/roadmap.md).
  
-   **Açık kaynak:** .NET Core Hizmetleri altında çok sayıda proje biridir [.NET Foundation](http://www.dotnetfoundation.org/) ve kullanılabilir [GitHub](https://github.com/).  .NET Core açık kaynaklı proje olarak daha saydam bir geliştirme sürecinin yükseltir ve etkin ve bağlı bir topluluk yükseltir.  
  
-   **Esnek dağıtım:** uygulamanızı dağıtmak için başlıca iki yolu vardır: framework bağımlı dağıtımı veya kendi içinde bulunan dağıtımı. Framework bağımlı dağıtım, yalnızca, uygulama ve üçüncü taraf bağımlılıkları yüklenir ve uygulamanızı .NET bulunması için çekirdek sistem genelinde sürümüne bağlıdır.  Kendi içinde bulunan dağıtım ile uygulamanızı oluşturmak için kullanılan .NET Core sürümü de uygulama ve üçüncü taraf bağımlılıkları ile birlikte dağıtılır ve yan yana çalıştırabilirsiniz diğer sürümleri ile.    Daha fazla bilgi için bkz: [.NET Core uygulama dağıtımı](../../core/deploying/index.md).

-   **Modüler:** .NET Core olduğundan modüler küçük derleme paketlerinde NuGet yayımlanır. Çekirdek işlevselliğini çoğunu içeren bir büyük derleme yerine, .NET Core küçük özelliği merkezli paketleri olarak kullanılabilir hale getirilir. Bu daha Çevik Geliştirme modeli bize sağlar ve yalnızca gereksinim duyduğunuz NuGet paketleri dahil etmek için uygulamanızı en iyi duruma olanak tanır. Hizmet, performans geliştirildi ve ödeme için-what-size-kullanım modeli maliyetlerini azaltılabilir azaltılmış daha sıkı güvenlik, daha küçük bir uygulama yüzey alanını yararları içerir.  
  
## <a name="the-net-core-platform"></a>.NET Core platformu  
 .NET Core platform yönetilen derleyicileri, çalışma zamanı, temel sınıf kitaplıkları ve ASP.NET Core gibi çok sayıda uygulama modelleri içeren çeşitli bileşenlerinin yapılır. Farklı bileşenleri hakkında daha fazla bilgi ve, aşağıdaki ziyaret ederek bağlı [GitHub](https://github.com/) depoları:  
  
-   [.NET Core](https://github.com/dotnet/core)  
  
-   [CoreFX - .NET Core temel kitaplıkları](https://github.com/dotnet/corefx)  
  
-   [CoreCLR - .NET çekirdeği çalışma zamanı](https://github.com/dotnet/coreclr)  
  
-   [CLI - .NET Core komut satırı araçları](https://github.com/dotnet/cli)  
  
-   [Roslyn - .NET derleyici platformu](https://github.com/dotnet/roslyn)  
  
-   [ASP.NET Core](https://github.com/aspnet/home)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET core giriş sayfası](https://www.microsoft.com/net/core)  
 [.NET Core Kılavuzu](../../core/index.md)  
 [ASP.NET Core belgeleri](/aspnet/core/)
