---
title: 'Son değişiklik: tür parametresi null olduğunda serileştirme özel durum oluşturur'
description: Bir tür parametresine sahip JsonSerialize serileştirme yöntemlerinin artık bu parametre için null geçirildiğinde bir özel durum oluşturması için .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: af2885394418072ad7efec5855490b5b80152fe6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761634"
---
# <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a>JsonSerializer. Serialize, tür parametresi null olduğunda ArgumentNullException oluşturur

<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> , ve <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> Bu parametre için artık bir parametre içeren bir parametresi olan aşırı yüklemeler, <xref:System.Type> <xref:System.ArgumentNullException> `null` Bu parametre için her zaman geçirilir.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,1 ' de, <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> parametresine <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> sahip olan, ve aşırı yüklemeler <xref:System.Type> <xref:System.ArgumentNullException> `null` parametre için geçirildiğinde `Type inputType` oluşturulur, ancak `Object value` parametresi de değildir `null` . .NET 5,0 ' den başlayarak, bu yöntemler *her zaman* <xref:System.ArgumentNullException> parametresi için bir ne zaman `null` geçirildiğinde oluşturulur <xref:System.Type> .

.NET Core 3,1 davranışı:

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

.NET 5,0 ve üzeri davranış:

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="reason-for-change"></a>Değişiklik nedeni

`null`Parametresi için geçirme `Type inputType` kabul edilemez ve her zaman bir oluşturması gerekir <xref:System.ArgumentNullException> .

## <a name="recommended-action"></a>Önerilen eylem

`null`Bu yöntemlerin parametresini geçirdiğinizden emin olun `Type inputType` .

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=fullName>

<!--

### Affected APIs

- `M:System.Text.Json.JsonSerializer.Serialize(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.Serialize(System.Text.Json.Utf8JsonWriter,System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`
- `M:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)`
- `M:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)`

### Category

Serialization

-->
