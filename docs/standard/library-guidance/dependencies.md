---
title: Bağımlılıklar ve .NET kitaplıkları
description: .NET kitaplıklarında NuGet bağımlılıklarını yönetmek için en iyi uygulama önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: 6a260b54c45a0cd231059ab3bc6f2707ef7fb20e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "76731484"
---
# <a name="dependencies"></a>Bağımlılıklar

.NET kitaplığına bağımlılık eklemenin birincil yolu NuGet paketlerine başvurmaktır. NuGet paket başvuruları, önceden yazılmış işlevselliği hızla yeniden kullanmanıza ve bunlardan yararlanmanıza olanak tanır, ancak bunlar .NET geliştiricileri için ortak bir sürtünme kaynağıdır. Bağımlılıkları doğru yönetmek, diğer .NET kitaplıklarında yapılan değişikliklerin .NET kitaplığınızı kırmasını önlemek için önemlidir ve bunun tersi de önemlidir!

## <a name="diamond-dependencies"></a>Elmas bağımlılıkları

Bir .NET projesinin bağımlılık ağacında bir paketin birden çok sürümü olması yaygın bir durumdur. Örneğin, bir uygulama, her biri aynı paketin farklı sürümlerine dayanan iki NuGet paketine bağlıdır. Uygulamanın bağımlılık grafiğinde elmas bağımlılığı artık mevcut.

![Elmas bağımlılığı](./media/dependencies/diamond-dependency.png "Elmas bağımlılığı")

Yapı zamanında NuGet, bağımlılıkların bağımlılıkları da dahil olmak üzere projenin bağlı olduğu tüm paketleri analiz eder. Bir paketin birden çok sürümü algılandığında, bir paket seçmek için kurallar değerlendirilir. Bir derlemenin yan yana sürümlerini aynı uygulamada çalıştırmak .NET'te sorunlu olduğundan, paketleri birleştirme gereklidir.

Çoğu elmas bağımlılığı kolayca çözülür; ancak, belirli durumlarda sorunlar yaratabilirler:

1. **Çakışan NuGet paket başvuruları,** paket geri yüklemesi sırasında bir sürümün çözülmesini engeller.
2. **Sürümler arasındaki son dakika değişiklikleri** çalışma zamanında hatalara ve özel durumlara neden olur.
3. **Paket derlemesi güçlü adlandırılmış,** montaj sürümü değiştirildi ve uygulama .NET Framework üzerinde çalışıyor. Derleme bağlama yönlendirmeleri gereklidir.

Sizinkinin yanında hangi paketlerin kullanılacağını bilmek mümkün değildir. Kitaplığınızı kıran elmas bağımlılığı olasılığını azaltmanın iyi bir yolu, bağlı olduğunuz paket sayısını en aza indirmektir.

✔️ .NET kitaplığınızı gereksiz bağımlılıklar için gözden geçirin.

## <a name="nuget-dependency-version-ranges"></a>NuGet bağımlılık sürüm aralıkları

Paket başvurusu, izin verdiği geçerli paketlerin aralığını belirtir. Genellikle, proje dosyasındaki paket başvuru sürümü minimum sürümüdür ve en fazla sürüm yoktur.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

NuGet'in bağımlılıkları çözerken kullandığı kurallar [karmaşıktır,](/nuget/consume-packages/dependency-resolution)ancak NuGet her zaman en düşük geçerli sürümü arar. NuGet, en düşük uyumluluk sorunları olacağından, kullanılabilir en yüksek sürümü kullanmaya göre en düşük geçerli sürümü tercih eder.

NuGet'in en düşük geçerli sürüm kuralı nedeniyle, en son sürümü almaktan kaçınmak için paket başvurularına bir üst sürüm veya tam aralık yerleştirmeye gerek yoktur. NuGet zaten sizin için en düşük, en uyumlu sürümü bulmaya çalışır.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Üst sürüm sınırları, bir çakışma olduğunda NuGet'in başarısız olmasına neden olur. Örneğin, bir kitaplık tam olarak 1,0'ı kabul ederken, başka bir kitaplık 2,0 veya üzeri gerektirir. Sürüm 2.0'da kırılma değişiklikleri getirilmiş olsa da, katı veya üst sınır sürüm bağımlılığı bir hatayı garanti eder.

![Elmas bağımlılık çatışması](./media/dependencies/diamond-dependency-conflict.png "Elmas bağımlılık çatışması")

❌En az sürümü olmayan NuGet paket referansları YOKTUR.

❌Kaçının NuGet paket başvuruları tam bir sürümünü talep.

❌Kaçının NuGet paketi referansları bir sürüm üst sınırı ile.

## <a name="nuget-shared-source-packages"></a>NuGet paylaşılan kaynak paketleri

Dış NuGet paket bağımlılıklarını azaltmanın bir yolu paylaşılan kaynak paketlerine başvurmaktır. Paylaşılan kaynak paketi, başvurulduğunda projeye dahil edilen [kaynak kodu dosyalarını](/nuget/reference/nuspec#including-content-files) içerir. Projenizin geri kalanıyla derlenen kaynak kod dosyalarını dahil ettiğiniz için dışbağımlılık ve çakışma olasılığı yoktur.

Paylaşılan kaynak paketleri, küçük işlevsellik parçalarını da içeren harikadır. Örneğin, HTTP aramaları yapmak için yardımcı yöntemlerin paylaşılan bir kaynak paketi.

![Paylaşılan kaynak paketi](./media/dependencies/shared-source-package.png "Paylaşılan kaynak paketi")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Paylaşılan kaynak projesi](./media/dependencies/shared-source-project.png "Paylaşılan kaynak projesi")

Paylaşılan kaynak paketlerinin bazı sınırlamaları vardır. Bunlar `PackageReference`yalnızca, eski `packages.config` projeler hariç tutulabilir. Ayrıca paylaşılan kaynak paketleri yalnızca aynı dil türüne sahip projeler tarafından kullanılabilir. Bu sınırlamalar nedeniyle paylaşılan kaynak paketleri en iyi açık kaynak proje içinde işlevselliği paylaşmak için kullanılır.

✔️ Küçük, dahili işlevsellik parçaları için paylaşılan kaynak paketlerine başvurmayı düşünün.

✔️ Küçük, dahili işlevsellik parçaları sağlıyorsa paketinizi paylaşılan bir kaynak paketi haline getirmeyi düşünün.

✔️ DO referans ile `PrivateAssets="All"`paylaşılan kaynak paketleri .

> Bu ayar, NuGet paketinin yalnızca geliştirme sırasında kullanılacağını ve genel bağımlılık olarak açıklanmaması gerektiğini söyler.

❌Ortak API'nizde paylaşılan kaynak paketi türleri YOKTUR.

> Paylaşılan kaynak türleri başvuru derleme derlemesine derlenir ve derleme sınırları arasında değiştirilemez. Örneğin, bir projedeki `IRepository` paylaşılan kaynak türü, başka bir projedeki `IRepository` aynı paylaşılan kaynaktan ayrı bir türdür. Paylaşılan kaynak paketlerindeki türlerin `internal` görünürlüğü olmalıdır.

❌Paylaşılan kaynak paketlerini NuGet.org yayınlamaYIN.

> Paylaşılan kaynak paketleri kaynak kodu içerir ve yalnızca aynı dil türüne sahip projeler tarafından kullanılabilir. Örneğin, C# paylaşılan kaynak paketi bir F# uygulaması tarafından kullanılamaz.
>
> Paylaşılan kaynak paketlerini yerel bir [özet akışında yayımlayın veya MyGet](./publish-nuget-package.md) bunları projeniz dahilinde dahili olarak tüketin.

>[!div class="step-by-step"]
>[Önceki](nuget.md)
>[Sonraki](sourcelink.md)
