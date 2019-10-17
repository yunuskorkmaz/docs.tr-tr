---
ms.openlocfilehash: 7d40324e6b0bc4afab9dd39b236f0909f360cc9b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394276"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Önbelleğe alma: CompactOnMemoryPressure özelliği kaldırıldı

ASP.NET Core 3,0 sürümü, [kullanılmayan MemoryCacheOptions API 'lerini](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18)kaldırdı.

#### <a name="change-description"></a>Açıklamayı Değiştir

Bu değişiklik, [ASPNET/önbelleğe alma #](https://github.com/aspnet/Caching/issues/221), için bir izleme. Tartışma için bkz. [ASPNET/Extensions # 1062](https://github.com/aspnet/Extensions/issues/1062).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`MemoryCacheOptions.CompactOnMemoryPressure` özelliği kullanılabilir.

#### <a name="new-behavior"></a>Yeni davranış

@No__t-0 özelliği kaldırılmıştır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Önbelleği otomatik olarak sıkıştırmak sorunlara neden oldu. Beklenmeyen davranışları önlemek için, önbelleğin yalnızca gerektiğinde sıkıştırılması gerekir.

#### <a name="recommended-action"></a>Önerilen eylem

Önbelleği sıkıştırmak için, `MemoryCache` ' a Alta ve gerektiğinde `Compact` ' i çağırın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
