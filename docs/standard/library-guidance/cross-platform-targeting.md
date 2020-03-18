---
title: .NET kitaplıkları için çapraz platform hedeflemesi
description: Platform arası .NET kitaplıkları oluşturmak için en iyi uygulama önerileri.
ms.date: 08/12/2019
ms.openlocfilehash: 61adff3759984554bb83531b4f9d8a49e29c929c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731452"
---
# <a name="cross-platform-targeting"></a>Platformlar arası hedefleme

Modern .NET birden çok işletim sistemi ve cihazı destekler. .NET açık kaynak kitaplıklarının, ister Azure'da barındırılan bir ASP.NET web sitesi ister Unity'de bir .NET oyunu oluşturmaları olsun, mümkün olduğunca çok geliştiriciyi desteklemesi önemlidir.

## <a name="net-standard"></a>.NET Standard

.NET Standard, bir .NET kitaplığına çapraz platform desteği eklemenin en iyi yoludur. [.NET Standardı,](../net-standard.md) tüm .NET uygulamalarında bulunan .NET API'lerinin bir belirtimidir. Hedefleme .NET Standard, .NET Standard'ın belirli bir sürümünde bulunan API'leri kullanmak üzere kısıtlanmış kitaplıklar oluşturmanıza olanak tanır, bu da .NET Standard'ın bu sürümünü uygulayan tüm platformlar tarafından kullanılabilir olduğu anlamına gelir.

![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

.NET Standard'ı hedeflemek ve projenizi başarıyla derlemek, kitaplığın tüm platformlarda başarılı bir şekilde çalışacağına garanti etmez:

1. Platforma özel API'ler diğer platformlarda başarısız olur. Örneğin, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> Windows'ta başarılı <xref:System.PlatformNotSupportedException> olacak ve başka bir işletim sistemi üzerinde kullanıldığında atmak.
2. API'ler farklı davranabilir. Örneğin, bir uygulama iOS veya UWP'de zamanından önce derleme kullandığında yansıma API'leri farklı performans özelliklerine sahiptir.

> [!TIP]
> .NET ekibi, olası sorunları keşfetmenize yardımcı olacak [bir Roslyn çözümleyicisi sunar.](../analyzers/api-analyzer.md)

✔️ DO bir `netstandard2.0` hedef dahil ile başlar.

> Genel amaçlı kitaplıkların çoğu .NET Standart 2.0 dışında API'ler gerekmez. .NET Standart 2.0 tüm modern platformlar tarafından desteklenir ve tek bir hedefle birden fazla platformu desteklemek için önerilen yoldur.

❌Bir `netstandard1.x` hedef dahil kaçının.

> .NET Standart 1.x, büyük bir paket bağımlılık grafiği oluşturan ve geliştiricilerin oluştururken çok sayıda paket indirmesi ile sonuçlanan nuget paketlerinin tanecikli kümesi olarak dağıtılır. .NET Framework 4.6.1, UWP ve Xamarin gibi modern .NET platformları, tüm destek .NET Standart 2.0. Sadece daha eski bir platformu hedeflemeniz gerekiyorsa .NET Standart 1.x'i hedeflemeniz gerekir.

✔️ bir `netstandard2.0` `netstandard1.x` hedef gerekiyorsa bir hedef içerir.

> .NET Standard 2.0'ı destekleyen `netstandard2.0` tüm platformlar hedefi kullanır ve daha küçük bir paket grafiğine `netstandard1.x` sahip olmanın avantajını kullanırken, eski platformlar çalışmaya devam edecek ve hedefi kullanmaya geri dönecektir.

❌Kitaplık platforma özgü bir uygulama modeline dayanıyorsa bir .NET Standart hedefi eklemeyin.

> Örneğin, UWP denetim araç kiti kitaplığı yalnızca UWP'de kullanılabilen bir uygulama modeline bağlıdır. Uygulama modeline özgü API'ler .NET Standard'da kullanılamaz.

## <a name="multi-targeting"></a>Çok hedefleme

Bazen kitaplıklarınızdan çerçeveye özgü API'lere erişmeniz gerekir. Çerçeveye özgü API'leri aramanın en iyi yolu, projenizi tek bir hedef için değil, birçok [.NET hedef çerçevesi](../frameworks.md) için oluşturan çok hedeflemeli kullanmaktır.

Tüketicilerinizi bireysel çerçeveler için oluşturmak zorunda kalmaktan korumak için ,NET Standart çıktısına ve bir veya daha fazla çerçeveye özgü çıktıya sahip olmak için çaba göstermelisiniz. Çoklu hedefleme ile tüm montajlar tek bir NuGet paketinin içinde paketlenir. Tüketiciler daha sonra aynı pakete başvuruyapabilir ve NuGet uygun uygulamayı seçecektir. .NET Standart kitaplığınız, NuGet paketinizin çerçeveye özgü bir uygulama sunduğu durumlar dışında her yerde kullanılan geri dönüş kitaplığı olarak hizmet vermektedir. Çoklu hedefleme, kodunuzda koşullu derlemeyi kullanmanıza ve çerçeveye özgü API'leri aramanıza olanak tanır.

![Birden fazla derlemeli NuGet paketi](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Birden fazla derlemeli NuGet paketi")

✔️ .NET Standardına ek olarak .NET uygulamalarını hedeflemeyi göz önünde bulundurun.

> .NET uygulamalarını hedeflemek, .NET Standardı'nın dışında olan platforma özgü API'leri aramanızı sağlar.
>
> Bunu yaparken .NET Standard desteğini düşürmeyin. Bunun yerine, uygulamadan atın ve yetenek API'leri sunun. Bu şekilde, kitaplığınız her yerde kullanılabilir ve özelliklerin çalışma zamanı ışıklarını destekler.

```csharp
public static class GpsLocation
{
    // This project uses multi-targeting to expose device-specific APIs to .NET Standard.
    public static async Task<(double latitude, double longitude)> GetCoordinatesAsync()
    {
#if NET461
        return CallDotNetFramworkApi();
#elif WINDOWS_UWP
        return CallUwpApi();
#else
        throw new PlatformNotSupportedException();
#endif
    }

    // Allows callers to check without having to catch PlatformNotSupportedException
    // or replicating the OS check.
    public static bool IsSupported
    {
        get
        {
#if NET461 || WINDOWS_UWP
            return true;
#else
            return false;
#endif
        }
    }
}
```

❌Kaynak kodunuz tüm hedefler için aynıysa, çoklu hedeflemenin yanı sıra .NET Standard'ı hedeflemekten kaçının.

> .NET Standart derlemesi NuGet tarafından otomatik olarak kullanılacaktır. Bireysel .NET uygulamalarını `*.nupkg` hedeflemek, boyutu hiçbir fayda sağlamadan artırır.

✔️ Bir `netstandard2.0` hedef `net461` sunarken bir hedef eklemeyi düşünün.

> .NET Framework'den .NET Standard 2.0'ın kullanılmasında .NET Framework 4.7.2'de ele alınan bazı sorunlar vardır. .NET Framework 4.6.1 - 4.7.1'de hala olan geliştiricilerin deneyimini ,NET Framework 4.6.1 için oluşturulmuş bir ikili teklif ederek geliştirebilirsiniz.

✔️ DO kitaplığınızı bir NuGet paketi kullanarak dağıtın.

> NuGet geliştirici için en iyi hedefi seçecek ve onları uygun uygulamayı seçmek zorunda kalkan.

✔️ ÇOKLU hedefleme yaparken `TargetFrameworks` proje dosyasının özelliğini kullanın.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

✔️, proje dosyanızı büyük ölçüde basitleştiren UWP ve Xamarin için çoklu hedefleme yaparken [MSBuild.Sdk.Extras'ı](https://github.com/onovotny/MSBuildSdkExtras) kullanmayı düşünün.

## <a name="older-targets"></a>Eski hedefler

.NET, .NET Framework'ün uzun süredir desteksiz olan hedefleme sürümlerini ve artık yaygın olarak kullanılmayan platformları destekler. Kitaplığınızın mümkün olduğunca çok hedef üzerinde çalışmasını sağlamanın bir değeri olsa da, eksik API'ler üzerinde çalışmak zorunda kalmak önemli ek yükü ekleyebilir. Erişim leri ve sınırlamaları göz önünde bulundurularak, bazı çerçevelerin artık hedef almaya değer olmadığına inanıyoruz.

❌Taşınabilir Sınıf Kitaplığı (PCL) hedefini EKLEMEYİn. Örneğin, `portable-net45+win8+wpa81+wp8`.

> .NET Standard, çapraz platform .NET kitaplıklarını desteklemenin ve PCL'lerin yerini alan modern bir yoldur.

❌Artık desteklenmeyen .NET platformları için hedefler EKLEMEYIN. Örneğin, `SL4`. `WP`

>[!div class="step-by-step"]
>[Önceki](get-started.md)
>[Sonraki](strong-naming.md)
