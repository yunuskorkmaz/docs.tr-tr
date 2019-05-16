---
title: Bağımlılıklar ve .NET kitaplıkları
description: .NET kitaplıkları, NuGet bağımlılıklarını yönetmek için en iyi yöntem önerileri.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 0cd00ff36ad52bc46769ca1793b9efd02db14da1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644259"
---
# <a name="dependencies"></a>Bağımlılıklar

Bir .NET Kitaplığı'na bağımlılıkları ekleme birincil yolu, NuGet paketlerini başvuruyor. NuGet paket başvuruları hızlı bir şekilde yeniden kullanmak ve önceden yazılı işlevselliğinden olanak sağlar, ancak uyuşmazlıkları .NET geliştiricileri için ortak bir kaynağı oldukları. Bağımlılıkları doğru şekilde yönetme, diğer .NET kitaplıkları değişiklikleri .NET Kitaplığı ' nıza kesilmesini önlemek önemlidir ve tersi!

## <a name="diamond-dependencies"></a>Baklava bağımlılıkları

Bir paket birden çok sürümünü, bağımlılık ağacında bir .NET projesi için yaygın bir durumdur. Örneğin, bir uygulama her biri aynı paketin farklı sürümlerine bağlı iki NuGet paketlerini bağlıdır. Uygulamanın bağımlılık grafiğinde bir baklava bağımlılık artık var.

![Bağımlılık elmas](./media/dependencies/diamond-dependency.png "bağımlılık elmas")

Oluşturma zamanında NuGet bağımlılıklarının bağımlılıklar dahil olmak üzere bir proje, bağlı olduğu tüm paketleri analiz eder. Bir paket birden çok sürümünü algılandığında kurallar birini seçmek için değerlendirilir. Aynı uygulamada bir derleme sürümlerini yan yana çalışan .NET sorunlu olduğundan paketleri birleştirme gereklidir.

Çoğu elmas bağımlılıkları kolayca çözümlenir; Ancak, bazı durumlarda sorunlar oluşturabilirsiniz:

1. **Çakışan NuGet paket başvuruları** paket geri yükleme sırasında çözümlenen bir sürüm engelle.
2. **Sürümleri arasında önemli değişiklikler** hatalar ve özel durumlar çalışma zamanında neden olur.
3. **Paket derleme tanımlayıcı ada**, derleme sürümü değişti ve uygulamanız .NET Framework üzerinde çalışıyor. Derleme bağlama yeniden yönlendirmeleri gereklidir.

Paketleri ne olacağını bilmeniz mümkün değildir kendi birlikte kullanılır. Kitaplığınızı bozucu bir baklava bağımlılık olasılığını azaltmak için en iyi yolu, bağımlı paketlerin sayısını en aza sağlamaktır.

**✔️ YAPMAK** .NET kitaplığınızda gereksiz bağımlılıkları gözden geçirin.

## <a name="nuget-dependency-version-ranges"></a>NuGet bağımlılık sürüm aralıklarını

Paket başvurusu geçerli paketleri veren aralığını belirtir. Genellikle, proje dosyasındaki paket başvurusu sürümü en düşük sürüm olan ve en büyük değer yoktur.

```xml
<!-- Accepts any version 1.0 and above. -->
<PackageReference Include="ExamplePackage" Version="1.0" />
```

NuGet bağımlılıkları çözümlenirken kullanan kurallar [karmaşık](/nuget/consume-packages/dependency-resolution), ancak NuGet, geçerli en düşük sürümü her zaman görünür. NuGet, en yüksek kullanarak geçerli en düşük sürüm tercih ettiği en az bir uyumluluk sorunlarını en düşük olacağı için kullanılabilir.

NuGet'ın en düşük uygun sürüm kural nedeniyle, bir üst sürümü veya tam aralığı en son sürümü girmeyi önlemek açısından paket başvuruları yerleştirmek gerekli değildir. Sizin için en düşük, en uyumlu sürümü bulmak NuGet zaten çalışır.

```xml
<!-- Accepts 1.0 up to 1.x, but not 2.0 and higher. -->
<PackageReference Include="ExamplePackage" Version="[1.0,2.0)" />

<!-- Accepts exactly 1.0. -->
<PackageReference Include="ExamplePackage" Version="[1.0]" />
```

Üst sürüm sınırları NuGet bir çakışma varsa başarısız olmasına neden olur. Örneğin, bir kitaplık başka bir kitaplığı 2.0 gerekirken veya üzeri tam olarak 1.0 kabul eder. Yeni değişiklikler 2.0 sürümünde tanıtılmıştır, ancak katı veya üst sınırı sürüm bağımlılık hata garanti eder.

![Bağımlılık çakışma elmas](./media/dependencies/diamond-dependency-conflict.png "bağımlılık çakışma elmas")

**❌ SAĞLAMADIĞI** sahip NuGet paket başvuruları ile en düşük sürümü yok.

**❌ KAÇININ** tam bir sürümünü gerektirdiğinden NuGet paket başvuruları.

**❌ KAÇININ** NuGet paket başvuruları sürüm üst sınırına sahip.

## <a name="nuget-shared-source-packages"></a>Paylaşılan NuGet kaynak paketleri

Dış NuGet Paket bağımlılıklarını azaltmak için bir paylaşılan kaynak paketlerinin başvurmak için yoludur. Paylaşılan kaynak pakette [kaynak kodu dosyaları](/nuget/reference/nuspec#including-content-files) başvurulduğunda bir projeye eklenir. Projenizi geri kalanı ile derlenmiş kaynak kodu dosyaları yalnızca koyduğunuzdan olmadığından herhangi bir dış bağımlılık ve çakışma olasılığı yoktur.

Kaynak paketleri için çok küçük işlev parçalarını dahil olmak üzere paylaşılan. Örneğin, bir paylaşılan kaynak paketi HTTP çağrıları yapmak için yardımcı yöntemler.

![Paylaşılan kaynak paketi](./media/dependencies/shared-source-package.png "paylaşılan kaynak paketi")

```xml
<PackageReference Include="Microsoft.Extensions.Buffers.Testing.Sources" PrivateAssets="All" Version="1.0" />
```

![Paylaşılan kaynak proje](./media/dependencies/shared-source-project.png "paylaşılan kaynak proje")

Paylaşılan kaynak paketleri bazı kısıtlamalara sahiptir. Tarafından yalnızca başvurulabilir `PackageReference`, böylece eski `packages.config` projeleri hariç tutulur. Ayrıca paylaşılan kaynak paketleri yalnızca aynı dil türündeki projeleri tarafından kullanılabilir. Bu sınırlamalar nedeniyle paylaşılan kaynak paketleri en iyi şekilde işlevi bir açık kaynak projesi içinde paylaşmak için kullanılır.

**✔️ DÜŞÜNÜN** paylaşılan kaynak paketleri için işlev küçük, iç parçalarını başvuruyor.

**✔️ DÜŞÜNÜN** işlev küçük, iç parçalarını sağlıyorsa paketinizin bir paylaşılan kaynak paketi yapma.

**✔️ YAPMAK** paylaşılan kaynak paketlerle başvuru `PrivateAssets="All"`.

> Bu ayar, NuGet paket yalnızca geliştirme anında kullanılacak olan ve genel bir bağımlılık olarak kullanıma sunulan olmamalıdır söyler.

**❌ SAĞLAMADIĞI** kaynak paketi türlerinde ortak API'nizi paylaştığı.

> Türleri başvuru bütünleştirilmiş kod içine derlenmiş ve bütünleştirilmiş kod sınırları arasında alınıp verilen kaynak paylaşılan. Örneğin, bir paylaşılan kaynak `IRepository` türü tek bir projede, aynı paylaşılan kaynak ayrı bir türden `IRepository` başka bir projede. Paylaşılan kaynak paketlerinde türler olmalıdır bir `internal` görünürlük.

**❌ SAĞLAMADIĞI** paylaşılan kaynak paketleri NuGet.org için yayımlayın.

> Paket kaynak kodunu içeren ve yalnızca aynı dil türündeki projeleri tarafından kullanılabilir kaynak paylaşılan. Örneğin, bir C# paylaşılan kaynak paketi tarafından kullanılamaz bir F# uygulama.
>
> Paylaşılan kaynak paketleri yayımlama bir [yerel akış veya MyGet](./publish-nuget-package.md) bunları dahili olarak projenize içinde kullanmak için.

>[!div class="step-by-step"]
>[Önceki](nuget.md)
>[İleri](sourcelink.md)
