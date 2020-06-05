---
ms.openlocfilehash: 2094da7ec94028c112d6683620ac1146a1544dab
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446984"
---
### <a name="localization-pubternal-apis-removed"></a>Yerelleştirme: "Pubternal" API 'Leri kaldırıldı

ASP.NET Core ortak API yüzeyini daha iyi korumak için bazı :::no-loc text="\"pubternal\""::: Yerelleştirme API 'leri kaldırılmıştır. Bir :::no-loc text="\"pubternal\""::: API 'nin `public` erişim değiştiricisi vardır ve bir [iç](/dotnet/csharp/language-reference/keywords/internal) amacı gösteren bir ad alanında tanımlanır.

Tartışma için bkz. [DotNet/aspnetcore # 22291](https://github.com/dotnet/aspnetcore/issues/22291).

#### <a name="version-introduced"></a>Sunulan sürüm

5,0 Preview 6

#### <a name="old-behavior"></a>Eski davranış

Aşağıdaki API 'Ler `public` :

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri:
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="new-behavior"></a>Yeni davranış

Aşağıdaki listede değişiklikler özetlenmektedir:

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper``Microsoft.Extensions.Localization.AssemblyWrapper`Şimdi geldi `internal` .
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider``Microsoft.Extensions.Localization.Internal.IResourceStringProvider`Şimdi geldi `internal` .
- `Microsoft.Extensions.Localization.ResourceManagerStringLocalizer`aşağıdaki parametre türlerinden birini kabul eden Oluşturucu aşırı yüklemeleri artık şunlardır `internal` :
  - `AssemblyWrapper`
  - `IResourceStringProvider`

#### <a name="reason-for-change"></a>Değişiklik nedeni

[ASPNET/Duyurular # 377](https://github.com/aspnet/Announcements/issues/377#issue-473651882)'de daha kapsamlı bir şekilde açıklanmıştı, :::no-loc text="\"pubternal\""::: türler `public` API yüzeyinden kaldırılmıştır. Bu değişiklikler, bu tasarım kararına daha fazla sınıf uyarlar. Söz konusu sınıflar, takımın iç testi için uzantı noktaları olarak tasarlanmıştır.

#### <a name="recommended-action"></a>Önerilen eylem

Büyük olasılıkla, bazı uygulamalar kasıtlı veya yanlışlıkla türlerine bağlı olabilir :::no-loc text="\"pubternal\""::: . Türlerin dışında nasıl geçiş yapılacağını öğrenmek için [Yeni davranış](#new-behavior) bölümlerine bakın.

Ortak API 'nin bu değişiklikten önce izin verilen ancak şimdi olmayan bir senaryo belirlediyseniz, [DotNet/aspnetcore](https://github.com/dotnet/aspnetcore/issues)' da bir sorun oluştu.

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

- `Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- <xref:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `T:Microsoft.Extensions.Localization.Internal.AssemblyWrapper`
- `T:Microsoft.Extensions.Localization.Internal.IResourceStringProvider`
- `Overload:Microsoft.Extensions.Localization.ResourceManagerStringLocalizer.#ctor`

-->
