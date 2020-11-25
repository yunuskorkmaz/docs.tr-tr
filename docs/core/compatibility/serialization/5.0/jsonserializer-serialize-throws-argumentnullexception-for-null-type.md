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
# <a name="jsonserializerserialize-throws-argumentnullexception-when-type-parameter-is-null"></a><span data-ttu-id="f4854-103">JsonSerializer. Serialize, tür parametresi null olduğunda ArgumentNullException oluşturur</span><span class="sxs-lookup"><span data-stu-id="f4854-103">JsonSerializer.Serialize throws ArgumentNullException when type parameter is null</span></span>

<span data-ttu-id="f4854-104"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType> , ve <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> Bu parametre için artık bir parametre içeren bir parametresi olan aşırı yüklemeler, <xref:System.Type> <xref:System.ArgumentNullException> `null` Bu parametre için her zaman geçirilir.</span><span class="sxs-lookup"><span data-stu-id="f4854-104"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> overloads that have a parameter of type <xref:System.Type> now throw an <xref:System.ArgumentNullException> whenever `null` is passed for that parameter.</span></span>

## <a name="change-description"></a><span data-ttu-id="f4854-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f4854-105">Change description</span></span>

<span data-ttu-id="f4854-106">.NET Core 3,1 ' de, <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> parametresine <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> sahip olan, ve aşırı yüklemeler <xref:System.Type> <xref:System.ArgumentNullException> `null` parametre için geçirildiğinde `Type inputType` oluşturulur, ancak `Object value` parametresi de değildir `null` .</span><span class="sxs-lookup"><span data-stu-id="f4854-106">In .NET Core 3.1, the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>, <xref:System.Text.Json.JsonSerializer.SerializeAsync(System.IO.Stream,System.Object,System.Type,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>, and <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes(System.Object,System.Type,System.Text.Json.JsonSerializerOptions)?displayProperty=nameWithType> overloads that have a <xref:System.Type> parameter throw an <xref:System.ArgumentNullException> when `null` is passed for the `Type inputType` parameter, but not if the `Object value` parameter is also `null`.</span></span> <span data-ttu-id="f4854-107">.NET 5,0 ' den başlayarak, bu yöntemler *her zaman* <xref:System.ArgumentNullException> parametresi için bir ne zaman `null` geçirildiğinde oluşturulur <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="f4854-107">Starting in .NET 5.0, these methods *always* throw an <xref:System.ArgumentNullException> when `null` is passed for the <xref:System.Type> parameter.</span></span>

<span data-ttu-id="f4854-108">.NET Core 3,1 davranışı:</span><span class="sxs-lookup"><span data-stu-id="f4854-108">Behavior in .NET Core 3.1:</span></span>

```csharp
// Returns a string with value "null".
JsonSerializer.Serialize(null, null);

// Returns a byte array with value "null".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

<span data-ttu-id="f4854-109">.NET 5,0 ve üzeri davranış:</span><span class="sxs-lookup"><span data-stu-id="f4854-109">Behavior in .NET 5.0 and later:</span></span>

```csharp
// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.Serialize(null, null);

// Throws ArgumentNullException: "Value cannot be null. (Parameter 'inputType')".
JsonSerializer.SerializeToUtf8Bytes(null, null);
```

## <a name="version-introduced"></a><span data-ttu-id="f4854-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f4854-110">Version introduced</span></span>

<span data-ttu-id="f4854-111">5.0</span><span class="sxs-lookup"><span data-stu-id="f4854-111">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f4854-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="f4854-112">Reason for change</span></span>

<span data-ttu-id="f4854-113">`null`Parametresi için geçirme `Type inputType` kabul edilemez ve her zaman bir oluşturması gerekir <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="f4854-113">Passing in `null` for the `Type inputType` parameter is unacceptable and should always throw an <xref:System.ArgumentNullException>.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f4854-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f4854-114">Recommended action</span></span>

<span data-ttu-id="f4854-115">`null`Bu yöntemlerin parametresini geçirdiğinizden emin olun `Type inputType` .</span><span class="sxs-lookup"><span data-stu-id="f4854-115">Make sure that you are not passing `null` for the `Type inputType` parameter of these methods.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f4854-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f4854-116">Affected APIs</span></span>

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
