---
title: Bağımlılıklar ve .NET kitaplıkları
description: .NET kitaplıklarında NuGet bağımlılıklarını yönetmeye yönelik en iyi yöntem önerileri.
ms.date: 10/02/2018
ms.openlocfilehash: b5742bf4724c4aff4beb4ca40a543bd096528a00
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706510"
---
# <a name="dependencies"></a>Bağımlılıklar

.NET kitaplığına bağımlılık eklemenin birincil yolu NuGet paketlerine başvuruyorlardır. NuGet paket başvuruları, zaten yazılmış işlevselliği hızlı bir şekilde yeniden kullanmanıza ve bu işlevselliği kullanmanıza olanak tanır, ancak .NET geliştiricileri için yaygın bir savunma kaynağıdır. Bağımlılıkları doğru şekilde yönetmek, diğer .NET kitaplıklarında bulunan değişikliklerin .NET kitaplığınızı bozmasını engellemek için önemlidir, tersi de geçerlidir!

## <a name="diamond-dependencies"></a>Elmas bağımlılıkları

.NET projesinin, bağımlılık ağacında bir paketin birden fazla sürümüne sahip olması yaygın bir durumdur. Örneğin, bir uygulama, her biri aynı paketin farklı sürümlerine bağlı olan iki NuGet paketine bağımlıdır. Bir elmas bağımlılığı artık uygulamanın bağımlılık grafiğinde bulunur.

![Elmas bağımlılığı](./media/dependencies/diamond-dependency.png "Elmas bağımlılığı")

Derleme zamanında, NuGet, bağımlılıkların bağımlılıkları da dahil olmak üzere bir projenin bağımlı olduğu tüm paketleri analiz eder. Bir paketin birden çok sürümü algılandığında, kurallar bir tane seçmek üzere değerlendirilir. Aynı uygulamadaki bir derlemenin yan yana sürümlerini çalıştırmak .NET 'te sorunlu olduğundan paketlerin kaldırılması gerekir.

Çoğu elmas bağımlılığı kolayca çözülür; Ancak, belirli koşullarda sorunlar oluşturabilirler:

1. **Çakışan NuGet paket başvuruları** , paketin geri yükleme sırasında bir sürümün çözümlenmesini engelliyor.
2. **Sürümler arasındaki son değişiklikler,** çalışma zamanında hatalara ve özel durumlara neden oluyor.
3. **Paket derlemesi tanımlayıcı adlı**, derleme sürümü değişti ve uygulama .NET Framework çalışıyor. Derleme bağlama yeniden yönlendirmeleri gereklidir.

Hangi paketlerin sizin de birlikte kullanılacağını Bileme olanaksızdır. Bir elmas bağımlılığını düşürmenin olasılığını azaltmanın iyi bir yolu, bağlı olduğunuz paket sayısını en aza indirmektir.

**✔️** , .net kitaplığınızı gereksiz bağımlılıklar için gözden geçirin.

## <a name="nuget-dependency-version-ranges"></a>NuGet bağımlılığı sürüm aralıkları

Paket başvurusu, izin verdiği geçerli paketlerin aralığını belirtir. Genellikle proje dosyasındaki paket başvuru sürümü en düşük sürümdür ve en fazla bir değer yoktur.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

Bir yandan,, bağımlılıkları çözümlerken NuGet tarafından kullanılan kurallar [karmaşıktır](/nuget/consume-packages/dependency-resolution), ancak NuGet her zaman en düşük uygun sürümü arar. En düşük uyumluluk sorunlarına sahip olacağı için NuGet, en yüksek kullanılabilir sürümü kullanarak en düşük uygun sürümü tercih eder.

NuGet 'in en düşük geçerli sürüm kuralı nedeniyle, en son sürümü almayı önlemek için paket başvurularına bir üst sürüm veya tam Aralık yerleştirmeniz gerekli değildir. NuGet, sizin için en düşük, en uyumlu sürümü bulmayı zaten deniyor.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Çakışma varsa, üst sürüm sınırları NuGet 'in başarısız olmasına neden olur. Örneğin, bir kitaplık, farklı bir kitaplık 2,0 veya üzeri gerektirdiğinden tam olarak 1,0 kabul eder. Sürüm 2,0 ' de önemli değişiklikler sunulurken, katı veya üst sınır sürümü bağımlılığı bir hata garanti eder.

![Elmas bağımlılığı çakışması](./media/dependencies/diamond-dependency-conflict.png "Elmas bağımlılığı çakışması")

**❌** en düşük sürüm olmadan NuGet paket başvuruları yoktur.

**❌ önlemek** Tam bir sürümü talep eden NuGet paket başvuruları.

**❌ önlemek** Sürüm üst sınırı olan NuGet paket başvuruları.

## <a name="nuget-shared-source-packages"></a>NuGet paylaşılan kaynak paketleri

Dış NuGet paket bağımlılıklarını azaltmanın bir yolu, paylaşılan kaynak paketlerine başvurmaktır. Paylaşılan bir kaynak paketi, başvuruluyorsa bir projede yer alan [kaynak kodu dosyaları](/nuget/reference/nuspec#including-content-files) içerir. Yalnızca projenizin geri kalanı ile derlenen kaynak kodu dosyalarını dahil ettiğinden, dış bağımlılık ve çakışma şansı yoktur.

Paylaşılan kaynak paketleri, küçük işlevsellik parçaları için harika. Örneğin, HTTP çağrıları yapmak için bir yardımcı yöntem paylaşılan kaynak paketidir.

![Paylaşılan kaynak paketi](./media/dependencies/shared-source-package.png "Paylaşılan kaynak paketi")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Paylaşılan kaynak proje](./media/dependencies/shared-source-project.png "Paylaşılan kaynak proje")

Paylaşılan kaynak paketlerinde bazı sınırlamalar vardır. Yalnızca `PackageReference`tarafından başvurulabilirler, bu nedenle eski `packages.config` projelerin hariç tutulur. Ayrıca, paylaşılan kaynak paketleri yalnızca aynı dil türüne sahip projeler tarafından kullanılabilir. Bu sınırlamalar nedeniyle, paylaşılan kaynak paketleri, bir açık kaynak proje içindeki işlevselliği paylaşmak için en iyi şekilde kullanılır.

✔️ küçük, iç işlevsellik parçaları için paylaşılan kaynak paketlerine başvurmayı **göz önünde bulundurun** .

**✔️** , küçük, iç işlevsellik parçaları sağlıyorsa paketinizi paylaşılan bir kaynak paketi yapmayı düşünün.

**✔️** paylaşılan kaynak paketlerine `PrivateAssets="All"`başvurun.

> Bu ayar NuGet 'e paketin yalnızca geliştirme zamanında kullanılacağını ve genel bağımlılık olarak sunulmayacağını söyler.

**❌** ortak API 'niz içinde paylaşılan kaynak paketi türleri yok.

> Paylaşılan kaynak türleri, başvurulan derlemeye derlenir ve derleme sınırları arasında değiştirilemez. Örneğin, bir projedeki bir paylaşılan kaynak `IRepository` türü, başka bir projede aynı paylaşılan kaynak `IRepository` ayrı bir tür. Paylaşılan kaynak paketlerindeki türlerin `internal` görünürlüğü olmalıdır.

❌ paylaşılan kaynak paketlerini NuGet.org 'e **yayımlamaz** .

> Paylaşılan kaynak paketleri kaynak kodu içerir ve yalnızca aynı dil türüne sahip projeler tarafından kullanılabilir. Örneğin, paylaşılan bir C# kaynak paketi bir F# uygulama tarafından kullanılamaz.
>
> Paylaşılan kaynak paketlerini yerel bir akışa yayımlayın veya bunları projenizde dahili olarak tüketmek üzere [MyGet](./publish-nuget-package.md) yapın.

>[!div class="step-by-step"]
>[Önceki](nuget.md)
>[İleri](sourcelink.md)
