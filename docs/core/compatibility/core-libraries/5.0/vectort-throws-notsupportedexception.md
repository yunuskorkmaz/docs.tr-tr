---
title: 'Son değişiklik: vektör, <T> NotSupportedException oluşturur'
description: Vector öğesinin <T> desteklenmeyen tür parametreleri için her zaman bir özel durum oluşturulduğu çekirdek .net kitaplıklarında .net 5,0 son değişikliği hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: 63db7c6b720735b180ed11098227b31a14008f74
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761517"
---
# <a name="vectort-always-throws-notsupportedexception-for-unsupported-types"></a>Vektör, \<T> Desteklenmeyen türler için her zaman NotSupportedException oluşturur

<xref:System.Numerics.Vector%601?displayProperty=nameWithType> Artık, <xref:System.NotSupportedException> desteklenmeyen tür parametreleri için her zaman bir oluşturur.

## <a name="change-description"></a>Açıklamayı Değiştir

Daha önce, üyeleri <xref:System.Numerics.Vector%601> <xref:System.NotSupportedException> Desteklenmeyen bir tür olduğunda her zaman bir oluşturmaz `T` . [unsupported type](#unsupported-types) Donanım hızlandırmasının desteklediği kod yolları nedeniyle özel durum her zaman oluşturulmaz. Örneğin, `Vector<bool> + Vector<bool>` ARM32 gibi `default` donanım hızlandırmayan platformlarda bir özel durum oluşturmak yerine döndürüldü. Desteklenmeyen türler için, <xref:System.Numerics.Vector%601> Üyeler farklı platformlarda ve donanım yapılandırmalarında tutarsız davranışlar sergilen.

.NET 5,0 ' den başlayarak, <xref:System.Numerics.Vector%601> Üyeler <xref:System.NotSupportedException> `T` desteklenen bir tür olmadığında her zaman tüm donanım yapılandırmalarında bir oluşturur.

### <a name="unsupported-types"></a>Desteklenmeyen türler

Tür parametresi için desteklenen türler <xref:System.Numerics.Vector%601> şunlardır:

- `byte`
- `sbyte`
- `short`
- `ushort`
- `int`
- `uint`
- `long`
- `ulong`
- `float`
- `double`

Desteklenen türler değişmemiştir, ancak gelecekte değişebilir.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Tür parametresi için desteklenmeyen bir tür kullanmayın <xref:System.Numerics.Vector%601> .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Numerics.Vector%601?displayProperty=fullName> ve tüm üyelerini

<!--

#### Category

Core .NET libraries

### Affected APIs

- ``T:System.Numerics.Vector`1``

-->
