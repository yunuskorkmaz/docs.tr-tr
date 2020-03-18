---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75902009"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Önbelleğe alma: CompactOnMemoryPressure özelliği kaldırıldı

ASP.NET Core 3.0 sürümü [eski MemoryCacheOptions API'leri](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18)kaldırıldı.

#### <a name="change-description"></a>Açıklamayı değiştir

Bu değişiklik [aspnet/Caching#221'in](https://github.com/aspnet/Caching/issues/221)devamıdır. Tartışmak için [dotnet/extensions#1062'ye](https://github.com/dotnet/extensions/issues/1062)bakın.

#### <a name="version-introduced"></a>Sürüm tanıtıldı

3,0

#### <a name="old-behavior"></a>Eski davranış

`MemoryCacheOptions.CompactOnMemoryPressure`mülkiyet mevcuttu.

#### <a name="new-behavior"></a>Yeni davranış

Mülk `MemoryCacheOptions.CompactOnMemoryPressure` kaldırıldı.

#### <a name="reason-for-change"></a>Değişiklik nedeni

Önbelleğin otomatik olarak sıkıştırılarak sorunlara neden oldu. Beklenmeyen davranışları önlemek için önbellek yalnızca gerektiğinde sıkıştırılmalıdır.

#### <a name="recommended-action"></a>Önerilen eylem

Önbelleği sıkıştırmak için, `MemoryCache` downcast ve gerektiğinde arayın. `Compact`

#### <a name="category"></a>Kategori

ASP.NET Çekirdeği

#### <a name="affected-apis"></a>Etkilenen API’ler

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
