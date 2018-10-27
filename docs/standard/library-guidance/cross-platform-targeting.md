---
title: Platformlar arası hedefleme
description: Platformlar arası .NET kitaplıkları oluşturmak için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 72fa891d5b1054af485a98d89b4efb11d6b0018b
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50049080"
---
# <a name="cross-platform-targeting"></a>Platformlar arası hedefleme

Birden çok işletim sistemleri ve cihazların modern .NET destekler. Azure veya bir .NET oyununuzu Unity barındırılan ASP.NET Web sitesi oluşturuyor mümkün olduğu kadar çok geliştiricileri desteklemek .NET açık kaynak kitaplıkları için önemlidir.

## <a name="net-standard"></a>.NET standard

.NET standard platformlar arası destek .NET Kitaplığı'na eklemek için en iyi yoludur. [.NET standard](../net-standard.md) bir belirtimi .NET API'leri, tüm .NET uygulamalarında kullanılabilir. .NET Standard hedefleyen Standard'ın .NET, .NET Standard sürümünü kullanan tüm platformlar tarafından kullanılabilir olması anlamına gelir, belirli bir sürümü olan API'leri kullanmak için kısıtlanır kitaplıkları oluşturmak olanak tanır.

![.NET standard](./media/cross-platform-targeting/platforms-netstandard.png ".NET Standard")

.NET Standard desteği ve başarıyla projenizde, derlemek, kitaplık başarıyla tüm platformlarda çalışacak garanti etmez:

1. Platforma özgü API, diğer platformlarda başarısız olur. Örneğin, <xref:Microsoft.Win32.Registry?displayProperty=nameWithType> Windows üzerinde başarısız ve throw <xref:System.PlatformNotSupportedException> diğer tüm işletim sistemlerinde kullanıldığında.
2. API'ler farklı şekilde davranabilir. Örneğin, bir uygulama, iOS veya UWP, zamanında tamamlanan derleme kullandığında yansıma API'leri farklı performans özelliklerine sahiptir.

> [!TIP]
> .NET ekibi [Roslyn çözümleyicinizi sunar](../analyzers/api-analyzer.md) olası sorunları keşfetmenize yardımcı olmak için.

**✔️ YAPMAK** dahil olmak üzere ile Başlat bir `netstandard2.0` hedef.

> En genel amaçlı kitaplıkları API'ler .NET Standard 2.0 dışında gerçekleştirmeniz gerekmez. .NET standard 2.0 tüm modern platformlar tarafından desteklenir ve bir hedef ile birden çok platform desteklemek için önerilen yoldur.

**❌ KAÇININ** dahil olmak üzere bir `netstandard1.x` hedef.

> .NET standard 1.x NuGet paketlerini büyük paket bağımlılık grafiği oluşturur ve geliştiricilerin çok sayıda paketleri oluştururken indirme sonuçları ayrıntılı kümesi olarak dağıtılır. .NET Framework 4.6.1, UWP ve Xamarin, gibi Modern .NET platformları, tüm .NET Standard 2.0 desteği. Yalnızca .NET Standard hedeflemesi gereken özellikle daha eski bir platformunu hedeflemeniz gerekirse 1.x.

**✔️ YAPMAK** dahil bir `netstandard2.0` gerektiriyorsa hedef bir `netstandard1.x` hedef.

> .NET Standard 2.0 destekleyen tüm platformlar kullanacağı `netstandard2.0` hedef ve avantaj daha eski platformlar hala çalışır ve kullanmaya geri döner ancak daha küçük bir paket grafik kalmamasını `netstandard1.x` hedef.

**❌ SAĞLAMADIĞI** kitaplığı bir platforma özgü uygulama modelini kullanır. .NET standart bir hedef ekleyin.

> Örneğin, bir UWP Denetim Araç Seti kitaplığı yalnızca UWP üzerinde kullanılabilir bir uygulama modeli bağlıdır. Uygulama modeli özel API'ler .NET Standard sürümünde kullanılabilir olmayacak.

## <a name="multi-targeting"></a>Çoklu sürüm desteği

Bazen, kitaplıklarından çerçeveye özgü API erişmeniz gerekir. Çoklu fazla projeniz derlenir, sürüm, çerçeveye özgü API'leri çağırmak için en iyi yolu kullanarak [.NET hedef Framework](../frameworks.md) yerine yalnızca bir tane.

Tüketicileriniz, tek tek çerçeveleri için yapı zorunda korumak için .NET standart çıktı artı bir veya daha fazla çerçeveye özgü çıkışları çaba göstermelisiniz. Çoklu sürüm desteği ile tüm derlemeler içinde tek bir NuGet paketi olarak paketlenir. Tüketiciler aynı paket ardından başvurabilir ve NuGet uygun uygulama seçer. Geri dönüş kitaplığı NuGet paketinizi çerçeveye özgü uygulama yeri sunar durumları hariç her yerde kullanılan, .NET Standard kitaplığı işlevi görür. Multi-targeting'e koşullu derleme kodunuzda kullanın ve çerçeveye özgü API'leri çağırmak sağlar.

![NuGet paketi ile birden çok derleme](./media/cross-platform-targeting/nuget-package-multiple-assemblies.png "birden çok derleme ile NuGet paketi")

**✔️ DÜŞÜNÜN** .NET uygulamalarının yanı sıra .NET Standard desteği.

> .NET uygulamaları hedefleyen .NET Standard dışında olan platforma özel API'leri çağırmak sağlar.
>
> Bunu yaptığınızda, .NET Standard desteği bırak değil. Bunun yerine, uygulamadan throw ve API'leri becerisi sağlar. Bu şekilde kitaplığınızı her yerde kullanılabilir ve çalışma zamanı açık yukarı özelliklerini destekler.

**❌ KAÇININ** çoklu hedefleme-.NET Standard ile tüm hedefler için aynı kaynak kodunuzu ise kullanarak.

> .NET Standard derleme NuGet tarafından otomatik olarak kullanılır. Tek tek .NET uygulamalarını hedefleme artırır `*.nupkg` hiçbir avantajı olmadan boyutu.

**✔️ DÜŞÜNÜN** ekleme için hedef `net461` teklifi ne zaman bir `netstandard2.0` hedef. 

> .NET Standard 2.0, .NET Framework kullanarak .NET Framework 4.7.2 ele alınan bazı sorunlar vardır. .NET Framework 4.6.1 - .NET Framework 4.6.1 için yerleşik bir ikili sunarak bunları 4.7.1 hala açıktır geliştiriciler için kullanım deneyimi sunmasını sağlayabilirsiniz.

**✔️ YAPMAK** bir NuGet paketi kullanarak kitaplığınızda dağıtın.

> NuGet, geliştirici için en iyi hedef seçin ve bunları uygun uygulama almak zorunda korunamadı.

**✔️ YAPMAK** kullanan bir proje dosyasının `TargetFrameworks` özelliği çoklu sürüm desteği olduğunda.

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <!-- This project will output netstandard2.0 and net461 assemblies -->
    <TargetFrameworks>netstandard2.0;net461</TargetFrameworks>
  </PropertyGroup>
</Project>
```

**✔️ DÜŞÜNÜN** kullanarak [MSBuild.Sdk.Extras](https://github.com/onovotny/MSBuildSdkExtras) çoklu sürüm desteği olduğunda UWP ve Xamarin gibi proje dosyanız büyük ölçüde basitleştirir.

## <a name="older-targets"></a>Eski hedefleri

.NET, Internet Explorer'ın artık yaygın olarak kullanılan platformları yanı sıra destek dışında uzun hedefleme .NET Framework sürümlerini destekler. Varken değer olabildiğince fazla sayıda hedefe API'leri eksik etrafında çalışmak zorunda ekleyebilirsiniz kitaplığı iş üzerinde ek yükünü önemli yaparak içinde. Çerçeve hedefleme değer bunların erişim ve sınırlamaları dikkate alarak kalmadığında belirli inanıyoruz.

**❌ SAĞLAMADIĞI** taşınabilir sınıf kitaplığı (PCL) hedef içerir. Örneğin: `portable-net45+win8+wpa81+wp8`

> .NET standard platformlar arası .NET kitaplıkları destekleyen modern yoludur ve PCLs değiştirir.

**❌ SAĞLAMADIĞI** artık desteklenmeyen bir .NET platformları için hedefler içerir. Örneğin, `SL4`, `WP`.

>[!div class="step-by-step"]
[Önceki](./get-started.md)
[İleri](./strong-naming.md)
