---
title: .NET kitaplıkları için platformlar arası hedefleme
description: Platformlar arası .NET kitaplıkları oluşturmaya yönelik en iyi yöntem önerileri.
ms.date: 08/12/2019
ms.openlocfilehash: 61adff3759984554bb83531b4f9d8a49e29c929c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731452"
---
# <a name="cross-platform-targeting"></a>Platformlar arası hedefleme

Modern .NET birden çok işletim sistemini ve cihazı destekler. .NET açık kaynaklı kitaplıkların, Azure 'da barındırılan bir ASP.NET Web sitesi mi yoksa Unity 'de bir .NET oyunu mi sundukları gibi çok sayıda geliştirici desteklemesi gerekir.

## <a name="net-standard"></a>.NET Standard

.NET Standard, bir .NET kitaplığına platformlar arası destek eklemenin en iyi yoludur. [.NET Standard](../net-standard.md) , tüm .NET uygulamalarında bulunan .NET API 'lerinin bir belirtimidir. .NET Standard hedefleme, belirli bir .NET Standard sürümünde olan API 'Leri kullanmak için kısıtlanmış kitaplıklar oluşturmanızı sağlar. Bu, .NET Standard bu sürümü uygulayan tüm platformlar tarafından kullanılabilir olduğunu gösterir.

![.NET Standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

.NET Standard ve projenizi başarıyla derleyerek, kitaplığın tüm platformlarda başarıyla çalışacağını garanti etmez:

1. Platforma özgü API 'Ler diğer platformlarda başarısız olur. Örneğin, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> Windows üzerinde başarılı olur ve başka herhangi bir IŞLETIM sisteminde kullanıldığında <xref:System.PlatformNotSupportedException> oluşturur.
2. API 'Ler farklı davranabilirler. Örneğin, bir uygulama iOS veya UWP üzerinde güncel derleme kullandığında, yansıma API 'Leri farklı performans özelliklerine sahiptir.

> [!TIP]
> .NET ekibi, olası sorunları bulmanıza yardımcı olmak için [bir Roslyn Çözümleyicisi sunmaktadır](../analyzers/api-analyzer.md) .

`netstandard2.0` hedef dahil ✔️.

> Genel amaçlı kitaplıkların çoğu .NET Standard 2,0 dışında API 'Lere ihtiyaç mamalıdır. .NET Standard 2,0 tüm modern platformlar tarafından desteklenir ve tek bir hedefle birden çok platformu desteklemek için önerilen yoldur.

❌ `netstandard1.x` hedefini kullanmaktan kaçının.

> .NET Standard 1. x, büyük bir paket bağımlılığı grafiği oluşturan ve geliştiricilerin derlerken çok sayıda paket indirmelerine neden olan ayrıntılı bir NuGet paketleri kümesi olarak dağıtılır. .NET Framework 4.6.1, UWP ve Xamarin gibi modern .NET platformları, tüm destek .NET Standard 2,0. Yalnızca daha eski bir platformu hedeflemek istiyorsanız .NET Standard 1. x hedefini hedefleyin.

bir `netstandard1.x` hedefi gerekiyorsa ✔️ `netstandard2.0` hedefi vardır.

> .NET Standard 2,0 destekleyen tüm platformlar `netstandard2.0` hedefini kullanır ve daha eski platformlar çalışmaya devam eder ve `netstandard1.x` hedefini kullanmaya geri dönecektir.

❌, kitaplık platforma özgü bir uygulama modelini kullanıyorsa .NET Standard hedefini içermez.

> Örneğin, UWP Denetim araç seti kitaplığı, yalnızca UWP üzerinde kullanılabilen bir uygulama modeline bağlıdır. Uygulama modeline özgü API 'Ler .NET Standard kullanılabilir olmayacaktır.

## <a name="multi-targeting"></a>Çoklu hedefleme

Bazen kitaplıklarınızdan çerçeveye özel API 'Lere erişmeniz gerekir. Çerçeveye özgü API 'Leri çağırmak için en iyi yol, projenizi yalnızca bir yerine birçok [.net hedef](../frameworks.md) çerçevesi için oluşturan Çoklu hedefleme kullanmaktır.

Tüketicilerinizin tek tek çerçeveler için derleme yapmasına gerek kalmadan, bir .NET Standard çıkışına ve bir veya daha fazla çerçeveye özgü çıktıya sahip olmaya çalışmamalısınız. Çoklu hedefleme ile, tüm derlemeler tek bir NuGet paketi içinde paketlenmiştir. Daha sonra tüketiciler aynı pakete başvurabilir ve NuGet uygun uygulamayı seçer. .NET Standard kitaplığınız, NuGet paketinizin çerçeveye özgü bir uygulama sunduğu durumlar dışında her yerde kullanılan geri dönüş Kitaplığı işlevi görür. Çoklu hedefleme, kodunuzda koşullu derleme kullanmanıza ve çerçeveye özgü API 'Leri çağırayapılandırmanıza olanak tanır.

![Birden çok bütünleştirilmiş kod içeren NuGet paketi](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "Birden çok bütünleştirilmiş kod içeren NuGet paketi")

✔️ .NET Standard ek olarak .NET uygulamalarını hedeflemeyi düşünün.

> .NET uygulamalarını hedefleme, .NET Standard dışında olan platforma özel API 'Leri aramanızı sağlar.
>
> Bunu yaparken .NET Standard desteğini kaldırmayın. Bunun yerine, uygulama ve teklif yeteneği API 'Lerini oluşturun. Bu şekilde, kitaplığınız her yerde kullanılabilir ve özelliklerin çalışma zamanı ışığını destekler.

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

kaynak kodunuz tüm hedefler için aynıysa, .NET Standard ❌ çoklu hedeflemeyi kullanmaktan kaçının.

> .NET Standard derlemesi NuGet tarafından otomatik olarak kullanılacaktır. Bağımsız .NET uygulamalarının hedeflenmesi, `*.nupkg` boyutunu avantajsız olarak artırır.

✔️ bir `netstandard2.0` hedefi sunarken `net461` için bir hedef eklemeyi düşünün.

> .NET Framework .NET Standard 2,0 ' in kullanılması .NET Framework 4.7.2 giderilen bazı sorunları içerir. Hala .NET Framework 4.6.1-4.7.1 ' de bulunan geliştiriciler için .NET Framework 4.6.1 için oluşturulmuş bir ikili sunarak deneyimi geliştirebilirsiniz.

✔️, bir NuGet paketi kullanarak kitaplığınızı dağıtır.

> NuGet, geliştirici için en iyi hedefi seçer ve uygun uygulamayı seçmek zorunda kalmalarını sağlar.

✔️, Çoklu hedefleme bir proje dosyasının `TargetFrameworks` özelliğini kullanır.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

✔️, UWP ve Xamarin için Çoklu hedefleme proje dosyanızı büyük ölçüde basitleştirirken [MSBuild. SDK. Extras](https://github.com/onovotny/MSBuildSdkExtras) kullanmayı düşünün.

## <a name="older-targets"></a>Daha eski hedefler

.NET, artık yaygın olarak kullanılmayan platformların yanı sıra, .NET Framework, destek ve uzun süreli olan sürümlerinin hedeflenmesini destekler. Kitaplığınızın mümkün olduğunca çok sayıda hedef üzerinde çalışmasını sağlamak için bir değer olsa da, eksik API 'Leri geçici olarak çözmek için önemli ölçüde ek yük eklenebilir. Belirli çerçevelerin daha fazla hedeflenmesini ve bunların erişim ve sınırlamalarını göz önünde bulundurduğumuz düşünülmektedir.

❌, taşınabilir sınıf kitaplığı (PCL) hedefi içermez. Örneğin, `portable-net45+win8+wpa81+wp8`.

> .NET Standard, platformlar arası .NET kitaplıklarını desteklemeye yönelik modern bir yoldur ve PCLs 'yi değiştirir.

❌ artık desteklenmeyen .NET platformları için hedefler dahil DEĞILDIR. Örneğin, `SL4``WP`.

>[!div class="step-by-step"]
>[Önceki](get-started.md)
>[İleri](strong-naming.md)
