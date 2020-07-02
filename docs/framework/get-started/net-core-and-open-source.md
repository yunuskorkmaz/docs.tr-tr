---
title: .NET Core ve Açık Kaynak
description: Genel amaçlı, modüler, platformlar arası ve .NET Standard açık kaynaklı bir uygulama olan .NET Core hakkında genel bakış konusunu okuyun.
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: 08d30d047c25b3b6d681d72b46b81a0cb21f8e0a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622763"
---
# <a name="net-core-and-open-source"></a>.NET Core ve açık kaynak

Bu makalede .NET Core 'un ne olduğuna ilişkin kısa bir genel bakış sağlanır ve nasıl daha fazla bilgi bulabileceğiniz gösterilmektedir. .NET Core belgelerinin tüm listesini bulmak için [.NET Core Kılavuzu](../../core/index.yml)' nu ziyaret edin.

## <a name="what-is-net-core"></a>.NET Core nedir?  

.NET Core, .NET Standard genel amaçlı, modüler, platformlar arası ve açık kaynaklı bir uygulamadır. .NET Framework ile aynı API 'lerin birçoğunu içerir (ancak .NET Core daha küçük bir küme) ve çeşitli işletim sistemlerini ve yonga hedeflerini destekleyen çalışma zamanı, çerçeve, derleyici ve araç bileşenlerini içerir. .NET Core uygulamasının öncelikli olarak ASP.NET Core iş yükleri tarafından ve ayrıca ihtiyacın yanı sıra daha modern bir uygulamaya sahip olması gerekir. Cihaz, bulut ve katıştırılmış/IoT senaryolarında kullanılabilir.  
  
.NET Core 'u kullanmaya başlamak için [10 dakikalık](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).net öğreticisini ziyaret edin Merhaba dünya.  
  
.NET Core 'un ana özellikleri şunlardır:
  
- **Platformlar arası:** .NET Core, ihtiyacınız olan uygulama özelliklerini uygulamak ve platform hedefinizden bağımsız olarak bu kodu yeniden kullanmak için temel işlevsellik sağlar. Şu anda üç ana işletim sistemi (OS) desteklemektedir: Windows, Linux ve macOS. Desteklenen işletim sistemleri arasında değiştirilmemiş olarak çalışan uygulamalar ve kitaplıklar yazabilirsiniz. Desteklenen işletim sistemlerinin listesini görmek için [.NET Core yol haritası](https://github.com/dotnet/core/blob/master/roadmap.md)' nı ziyaret edin.
  
- **Açık Kaynak:** .NET Core, [.net Foundation](https://www.dotnetfoundation.org/) 'ın Stewardship altındaki birçok projeden biridir ve [GitHub](https://github.com/)' da kullanılabilir. Açık kaynaklı bir proje olarak .NET Core, daha saydam bir geliştirme sürecini ve etkin ve bağlı bir topluluğu yükseltir.  
  
- **Esnek dağıtım:** uygulamanızı dağıtmanın iki ana yolu vardır: çerçeveye bağımlı dağıtım veya kendi kendine kapsanan dağıtım. Çerçeveye bağımlı dağıtım ile, yalnızca uygulamanız ve üçüncü taraf bağımlılıkları yüklenir ve uygulamanız, .NET Core 'un sistem genelindeki bir sürümüne bağlıdır. Kendi kendine içerilen dağıtım ile uygulamanızı oluşturmak için kullanılan .NET Core sürümü, uygulamanız ve üçüncü taraf bağımlılıklarınızla birlikte da dağıtılır ve diğer sürümlerle yan yana çalışabilir. Daha fazla bilgi için bkz. [.NET Core uygulama dağıtımı](../../core/deploying/index.md).

- **Modüler:** .NET Core, daha küçük derleme paketlerinde NuGet aracılığıyla yayınlandığı için modüler hale gelir. Çekirdek işlevlerin çoğunu içeren bir büyük derleme yerine, .NET Core daha küçük, Özellik merkezli paketler olarak sunulmaktadır. Bu modülik, bizim için daha çevik bir geliştirme modeli sağlar ve uygulamanızı yalnızca ihtiyacınız olan NuGet paketlerini içerecek şekilde iyileştirmenize olanak tanır. Daha küçük bir uygulama yüzeyi alanının avantajları, daha sıkı güvenlik, azaltılmış bakım, iyileştirilmiş performans ve bir Kullandıkça öde modelinde daha düşük maliyetlere sahiptir.  
  
## <a name="the-net-core-platform"></a>.NET Core platformu
  
.NET Core platformu, yönetilen derleyiciler, çalışma zamanı, temel sınıf kitaplıkları ve ASP.NET Core gibi çok sayıda uygulama modeli dahil olmak üzere çeşitli bileşenlerden oluşur. Aşağıdaki [GitHub](https://github.com/) depolarını ziyaret ederek, farklı bileşenler hakkında daha fazla bilgi alabilirsiniz:  
  
- [.NET Core giriş sayfası](https://github.com/dotnet/core)  
  
- [Çalışma zamanı-.NET Core platformu ve çalışma zamanı](https://github.com/dotnet/runtime)  
  
- [CLı-.NET Core komut satırı araçları](https://github.com/dotnet/cli)  
  
- [Roslyn-.NET Compiler Platform](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET öğreticisi-10 dakika içinde Merhaba Dünya](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [.NET Core kılavuzu](../../core/index.yml)
- [ASP.NET Core docs](/aspnet/core/)
