---
title: 'Son değişiklik: karakter serisini kaldırma, tek karakterlik dize gerektirir'
description: System.Text.Json 'un, bir Char hedefi serisi kaldırılırken JSON 'da tek char dizesi gerektirdiğini .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 12/15/2020
ms.openlocfilehash: 39a2d25b00bf8855cfbf46a4d78b8545052703e5
ms.sourcegitcommit: 635a0ff775d2447a81ef7233a599b8f88b162e5d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/17/2020
ms.locfileid: "97633877"
---
# <a name="systemtextjson-requires-single-char-string-to-deserialize-a-char"></a>System.Text.Json, bir karakter serisini kaldırmak için tek char dizesi gerektirir

Bir using öğesini başarıyla serisini kaldırmak için <xref:System.Char> <xref:System.Text.Json> JSON dizesinin tek bir karakter içermesi gerekir.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, JSON 'daki çok dizeli bir `char` `char` özellik veya alana başarıyla seri hale getirilmesi gerekir. `char`Aşağıdaki örnekte olduğu gibi, yalnızca ilk dize kullanılır:

```csharp
// .NET Core 3.0 and 3.1: Returns the first char 'a'.
// .NET 5.0 and later: Throws JsonException because payload has more than one char.
char deserializedChar = JsonSerializer.Deserialize<char>("\"abc\"");
```

.NET 5,0 ve üzeri sürümlerde, tek dize dışında bir şey, `char` <xref:System.Text.Json.JsonException> seri durumdan çıkarma hedefi bir olduğunda oluşturulmasına neden olur `char` . Aşağıdaki örnek dize tüm .NET sürümlerinde başarıyla seri durumdan çıkarılacak:

```csharp
// Correct usage.
char deserializedChar = JsonSerializer.Deserialize<char>("\"a\"");
```

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="reason-for-change"></a>Değişiklik nedeni

Seri durumdan çıkarma için ayrıştırma yalnızca, hedef türü için belirtilen yük geçerliyse başarılı olur. Bir `char` tür için, yalnızca geçerli yük tek bir `char` dizedir.

## <a name="recommended-action"></a>Önerilen eylem

JSON serisini bir `char` hedefte kaldırdığınızda, dizenin tek dışında bulunduğundan emin olun `char` .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`

### Category

Serialization

-->
