---
title: 'Son değişiklik: Vector2. Lerp ve Vector4. Lerp için davranış değişikliği'
description: Vector2. Lerp ve Vector4. Lerp uygulamasının bir kayan noktalı yuvarlama hatası için doğru hesapta değiştiği, çekirdek .NET kitaplıklarında .NET 5 ile ilgili son değişiklik hakkında bilgi edinin.
ms.date: 11/01/2020
ms.openlocfilehash: a7014c30f2b102dc9a19e9a58f97b7c0ed8cd648
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257004"
---
# <a name="behavior-change-for-vector2lerp-and-vector4lerp"></a>Vector2.Lerp ve Vector4.Lerp için davranış değişikliği

<xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> Bir kayan nokta yuvarlama hatası için uygulamasının uygulanması ve doğru hesaba değiştirilmesi.

## <a name="change-description"></a>Açıklamayı Değiştir

Daha önce <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=nameWithType> ve <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=nameWithType> olarak uygulandı `value1 + (value2 - value1) * amount` . Ancak, bir kayan nokta yuvarlama hatası nedeniyle, bu algoritma olduğunda her zaman döndürmez `value2` `amount` `1.0f` .

.NET 5 ve sonraki sürümlerde, uygulama ile aynı algoritmayı kullanır <xref:System.Numerics.Vector3.Lerp(System.Numerics.Vector3,System.Numerics.Vector3,System.Single)?displayProperty=nameWithType> `(value1 * (1.0f - amount)) + (value2 * amount)` . Bu algoritma, yuvarlama hatası için doğru şekilde hesaplar. Şimdi, ne zaman, `amount` `1.0f` sonuç kesin olarak olur `value2` . Güncelleştirilmiş algoritma Ayrıca algoritmaların kullanılabilir olduğunda, kullanımı uygun şekilde iyileştirilme olanağı sağlar <xref:System.MathF.FusedMultiplyAdd%2A?displayProperty=nameWithType> .

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

Herhangi bir işlem gerekli değildir. Ancak, eski davranışı sürdürmek istiyorsanız, `Lerp` önceki algoritmasını kullanan kendi işlevinizi uygulayabilirsiniz `value1 + (value2 - value1) * amount` .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)?displayProperty=fullName>
- <xref:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Numerics.Vector2.Lerp(System.Numerics.Vector2,System.Numerics.Vector2,System.Single)`
- `M:System.Numerics.Vector4.Lerp(System.Numerics.Vector4,System.Numerics.Vector4,System.Single)`

-->
