---
title: .NET Core ve Açık Kaynak
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: bed5bb6aad5f3e651f7c4c0651a2365f17eb8a0b
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635287"
---
# <a name="net-core-and-open-source"></a>.NET Core ve açık kaynak

Bu makalede, .NET Core'un ne olduğuna kısa bir genel bakış sağlanmıştır ve daha fazla bilgiyi nasıl bulabileceğinizi gösterir. .NET Core için belgelerin tam listesini bulmak için [.NET Core kılavuzunu ziyaret edin.](../../core/index.yml)

## <a name="what-is-net-core"></a>.NET Core nedir?  

.NET Core, .NET Standardının genel amacı, modüler, çapraz platform ve açık kaynak uygulamasıdır. .NET Framework (ancak .NET Core daha küçük bir kümedir) ile aynı API'lerin çoğunu içerir ve çalışma zamanı, çerçeve, derleyici ve çeşitli işletim sistemlerini ve yonga hedeflerini destekleyen araçlar bileşenlerini içerir. .NET Core uygulaması öncelikle ASP.NET Core iş yüklerinden değil, aynı zamanda daha modern bir uygulamaya sahip olmak için ihtiyaç ve istekten kaynaklandı. Aygıt, bulut ve gömülü/IoT senaryolarında kullanılabilir.  
  
.NET Core ile başlamak için 10 dakika içinde .NET öğretici [Hello World'u ziyaret edin.](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)  
  
.NET Core'un temel özellikleri şunlardır:
  
- **Çapraz platform:** .NET Core, ihtiyacınız olan uygulama özelliklerini uygulamak ve platform hedefiniz ne olursa olsun bu kodu yeniden kullanmak için temel işlevsellik sağlar. Şu anda üç ana işletim sistemi (OS): Windows, Linux ve macOS destekler. Desteklenen işletim sistemlerinde değiştirilmemiş uygulamalar ve kitaplıklar yazabilirsiniz. Desteklenen işletim sistemlerinin listesini görmek için [.NET Core yol haritasını](https://github.com/dotnet/core/blob/master/roadmap.md)ziyaret edin.
  
- **Açık kaynak:** .NET Core [.NET Foundation'ın](https://www.dotnetfoundation.org/) yönetimi altındaki birçok projeden biridir ve [GitHub'da](https://github.com/)mevcuttur.  .NET Core'un açık kaynak kodl› bir proje olması, daha şeffaf bir gelişim sürecini teşvik eder ve aktif ve ilgili bir topluluğu teşvik eder.  
  
- **Esnek dağıtım:** Uygulamanızı dağıtmanın iki ana yolu vardır: çerçeveye bağımlı dağıtım veya bağımsız dağıtım. Çerçeveye bağımlı dağıtımda, yalnızca uygulamanız ve üçüncü taraf bağımlılıkları yüklenir ve uygulamanız .NET Core'un sistem çapındaki bir sürümüne bağlıdır. Bağımsız dağıtım ile, uygulamanızı oluşturmak için kullanılan .NET Core sürümü de uygulamanız ve üçüncü taraf bağımlılıkları ile birlikte dağıtılır ve diğer sürümlerle yan yana çalıştırılabilir. Daha fazla bilgi için [bkz.](../../core/deploying/index.md)

- **Modüler:** .NET Core modülerdir çünkü NuGet aracılığıyla daha küçük montaj paketlerinde piyasaya sürülür. .NET Core, temel işlevlerin çoğunu içeren büyük bir derleme yerine daha küçük, özellik merkezli paketler olarak kullanılabilir hale getirilir. Bu modülerlik bizim için daha çevik bir geliştirme modeli sağlar ve uygulamanızı yalnızca ihtiyacınız olan NuGet paketlerini içerecek şekilde optimize etmenizi sağlar. Daha küçük bir uygulama yüzey alanının avantajları arasında daha sıkı güvenlik, daha az hizmet, daha iyi performans ve kullanım için ödeme modelinde maliyetlerin düşmesi yer alıyor.  
  
## <a name="the-net-core-platform"></a>.NET Core platformu
  
.NET Core platformu yönetilen derleyiciler, çalışma zamanı, taban sınıf kitaplıkları ve ASP.NET Core gibi çok sayıda uygulama modeli dahil olmak üzere çeşitli bileşenlerden oluşur. Farklı bileşenler hakkında daha fazla bilgi edinebilir ve aşağıdaki [GitHub](https://github.com/) depolarını ziyaret ederek etkileşime girebilirsiniz:  
  
- [.NET Core ana sayfa](https://github.com/dotnet/core)  
  
- [Çalışma zamanı - .NET Core platformu ve çalışma zamanı](https://github.com/dotnet/runtime)  
  
- [CLI - .NET Core komut satırı araçları](https://github.com/dotnet/cli)  
  
- [Roslyn - .NET Derleyici Platformu](https://github.com/dotnet/roslyn)  
  
- [ASP.NET Core](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET öğretici - Alo World 10 dakika içinde](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [.NET Core kılavuzu](../../core/index.yml)
- [ASP.NET Çekirdek dokümanları](/aspnet/core/)
