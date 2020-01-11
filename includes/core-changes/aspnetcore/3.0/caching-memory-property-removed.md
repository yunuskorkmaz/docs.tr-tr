---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75902009"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Önbelleğe alma: CompactOnMemoryPressure özelliği kaldırıldı

ASP.NET Core 3,0 sürümü, [kullanılmayan MemoryCacheOptions API 'lerini](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18)kaldırdı.

#### <a name="change-description"></a>Açıklamayı Değiştir

Bu değişiklik, [ASPNET/önbelleğe alma #](https://github.com/aspnet/Caching/issues/221), için bir izleme. Tartışma için bkz. [DotNet/Extensions # 1062](https://github.com/dotnet/extensions/issues/1062).

#### <a name="version-introduced"></a>Sunulan sürüm

3.0

#### <a name="old-behavior"></a>Eski davranış

`MemoryCacheOptions.CompactOnMemoryPressure` özellik var.

#### <a name="new-behavior"></a>Yeni davranış

`MemoryCacheOptions.CompactOnMemoryPressure` özelliği kaldırılmıştır.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Önbelleği otomatik olarak sıkıştırmak sorunlara neden oldu. Beklenmeyen davranışları önlemek için, önbelleğin yalnızca gerektiğinde sıkıştırılması gerekir.

#### <a name="recommended-action"></a>Önerilen eylem

Önbelleği sıkıştırmak için, `MemoryCache` Alta ve gerektiğinde `Compact` çağırın.

#### <a name="category"></a>Kategori

ASP.NET Core

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
