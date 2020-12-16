---
ms.openlocfilehash: 53840ddd59ae3463bae2930fd0151ab2cd2d65cb
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97593337"
---
### <a name="design-time-builds-only-return-top-level-package-references"></a>Tasarım zamanı derlemeleri yalnızca üst düzey paket başvurularını döndürüyor

.NET Core SDK 3.1.400 ' den başlayarak, hedef tarafından yalnızca üst düzey paket başvuruları döndürülür `RunResolvePackageDependencies` .

#### <a name="version-introduced"></a>Sunulan sürüm

.NET Core SDK 3.1.400

#### <a name="change-description"></a>Açıklamayı Değiştir

.NET Core SDK önceki sürümlerinde, `RunResolvePackageDependencies` hedef, NuGet varlıkları dosyasından bilgi içeren aşağıdaki MSBuild öğelerini oluşturdu:

- `PackageDefinitions`
- `PackageDependencies`
- `TargetDefinitions`
- `FileDefinitions`
- `FileDependencies`

Bu veriler, Çözüm Gezgini içindeki bağımlılıklar düğümünü doldurmak için Visual Studio tarafından kullanılır. Ancak, bu büyük miktarda veri olabilir ve bağımlılıklar düğümü genişletilmediği takdirde veriler gerekli değildir.

.NET Core SDK sürüm 3.1.400 başlayarak, bu öğelerin çoğu varsayılan olarak oluşturulmaz. Yalnızca türündeki öğeler `Package` döndürülür. Visual Studio 'Nun bağımlılıklar düğümünü doldurması gerekiyorsa, bilgileri doğrudan varlıklar dosyasından okur.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, Visual Studio 'nun içindeki çözüm yükleme performansını geliştirmek için sunulmuştur. Daha önce, çoğu kullanıcının hiçbir şekilde görüntüleyememesi gereken birçok başvuruyu yükleyen tüm paket başvuruları yüklenecektir.

#### <a name="recommended-action"></a>Önerilen eylem

Oluşturulmakta olan bu öğelere bağlı MSBuild `EmitLegacyAssetsFileItems` mantığınıza sahipseniz, özelliği `true` proje dosyanızda olarak ayarlayın. Bu ayar, tüm öğelerin oluşturulduğu önceki davranışa izin vermez.

#### <a name="category"></a>Kategori

MSBuild

#### <a name="affected-apis"></a>Etkilenen API’ler

Yok
