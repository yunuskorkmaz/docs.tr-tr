---
title: 'Son değişiklik: karakter serisini kaldırma, tek karakterlik dize gerektirir'
description: System.Text.Json 'un, bir Char hedefine seri durumdan çıkarılırken JSON 'da tek char dizesi gerektirdiğini .NET 5 ' teki son değişiklik hakkında bilgi edinin.
ms.date: 12/15/2020
ms.openlocfilehash: e901f8ee7e7521af948a3bcde5cf969640436f7f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256341"
---
# <a name="systemtextjson-requires-single-char-string-to-deserialize-a-char"></a>System.Text.Json, bir karakter serisini kaldırmak için tek char dizesi gerektirir

Bir using öğesini başarıyla serisini kaldırmak için <xref:System.Char> <xref:System.Text.Json> JSON dizesinin tek bir karakter içermesi gerekir.

## <a name="change-description"></a>Açıklamayı Değiştir

Önceki .NET sürümlerinde, JSON 'daki çok dizeli bir `char` `char` özellik veya alana başarıyla seri hale getirilmesi gerekir. `char`Aşağıdaki örnekte olduğu gibi, yalnızca ilk dize kullanılır:

```csharp
// .NET Core 3.0 and 3.1: Returns the first char 'a'.
// .NET 5 and later: Throws JsonException because payload has more than one char.
char deserializedChar = JsonSerializer.Deserialize<char>("\"abc\"");
```

.NET 5 ve üzeri sürümlerde, tek dize dışında bir şey, `char` <xref:System.Text.Json.JsonException> seri durumdan çıkarma hedefi bir olduğunda oluşturulmasına neden olur `char` . Aşağıdaki örnek dize tüm .NET sürümlerinde başarıyla seri durumdan çıkarılacak:

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
