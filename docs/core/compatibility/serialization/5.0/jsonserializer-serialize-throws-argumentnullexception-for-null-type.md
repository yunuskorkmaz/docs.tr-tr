---
title: 'Son değişiklik: tür parametresi null olduğunda serileştirme özel durum oluşturur'
description: .NET 5 ' teki son değişiklik hakkında bilgi edinin. bir tür parametresine sahip JsonSerialize serileştirme yöntemleri artık bu parametre için null geçirildiğinde bir özel durum oluşturur.
ms.date: 10/18/2020
ms.openlocfilehash: 81b3b754c11599eea435c750f1386fcaa2f0b54d
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2021
ms.locfileid: "102256302"
---
# <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a>JsonSerializer. Serialize, tür parametresi null olduğunda ArgumentNullException oluşturur

<xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> , ve <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> Bu parametre için artık bir parametre içeren bir parametresi olan aşırı yüklemeler, <xref:System.Type> <xref:System.ArgumentNullException> `null` Bu parametre için her zaman geçirilir.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 3,1 ' de, <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> parametresine <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> sahip olan, ve aşırı yüklemeler <xref:System.Type> <xref:System.ArgumentNullException> `null` parametre için geçirildiğinde `Type inputType` oluşturulur, ancak `Object value` parametresi de değildir `null` . .NET 5 ' den başlayarak, bu yöntemler *her zaman* <xref:System.ArgumentNullException> parametresi için bir ne zaman `null` geçirildiğinde oluşturulur <xref:System.Type> .

.NET Core 3,1 davranışı:

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

.NET 5 ve üzeri davranış:

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
