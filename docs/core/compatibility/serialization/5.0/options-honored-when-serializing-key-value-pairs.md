---
title: 'Son değişiklik: PropertyNamingPolicy, Propertynamecaseduyarsız ve encoder seçenekleri anahtar-değer çiftleri için kabul edilir'
description: Bir anahtar-değer çifti örneğinin anahtar ve değer özellik adlarını serileştirilirken ve seri durumdan çıkarılırken, PropertyNamingPolicy, Propertynamecaseduyarsız ve kodlayıcı seçeneklerinin kabul edildiği .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 10/18/2020
ms.openlocfilehash: 5d75cb7feea32cc4b942e5261c5b609e00a5082c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761633"
---
# <a name="propertynamingpolicy-propertynamecaseinsensitive-and-encoder-options-are-honored-when-serializing-and-deserializing-key-value-pairs"></a><span data-ttu-id="f8ec2-103">Anahtar-değer çiftlerini serileştirmek ve seri durumdan çıkarılırken PropertyNamingPolicy, Propertynamecaseduyarsız ve kodlayıcı seçenekleri kabul edilir</span><span class="sxs-lookup"><span data-stu-id="f8ec2-103">PropertyNamingPolicy, PropertyNameCaseInsensitive, and Encoder options are honored when serializing and deserializing key-value pairs</span></span>

<span data-ttu-id="f8ec2-104"><xref:System.Text.Json.JsonSerializer> Şimdi, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> <xref:System.Text.Json.JsonSerializerOptions.Encoder> <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> bir örneğin ve özellik adlarını serileştirilirken, ve seçeneklerini görürsünüz <xref:System.Collections.Generic.KeyValuePair%602> .</span><span class="sxs-lookup"><span data-stu-id="f8ec2-104"><xref:System.Text.Json.JsonSerializer> now honors the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options when serializing the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names of a <xref:System.Collections.Generic.KeyValuePair%602> instance.</span></span> <span data-ttu-id="f8ec2-105">Ayrıca, <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> örneklerin serisini kaldırırken ve seçeneklerini de kabul eder <xref:System.Collections.Generic.KeyValuePair%602> .</span><span class="sxs-lookup"><span data-stu-id="f8ec2-105">Additionally, <xref:System.Text.Json.JsonSerializer> honors the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options when deserializing <xref:System.Collections.Generic.KeyValuePair%602> instances.</span></span>

## <a name="change-description"></a><span data-ttu-id="f8ec2-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f8ec2-106">Change description</span></span>

### <a name="serialization"></a><span data-ttu-id="f8ec2-107">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="f8ec2-107">Serialization</span></span>

<span data-ttu-id="f8ec2-108">.NET Core 3. x sürümlerinde ve [ NuGet paketindekiSystem.Text.Js](https://www.nuget.org/packages/System.Text.Json)4.6.0-4.7.2 sürümlerinde, <xref:System.Collections.Generic.KeyValuePair%602> örneklerin özellikleri herhangi bir ve seçenekten bağımsız olarak her zaman "Key" ve "Value" olarak serileştirilir <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f8ec2-108">In .NET Core 3.x versions and in the 4.6.0-4.7.2 versions of the [System.Text.Json NuGet package](https://www.nuget.org/packages/System.Text.Json), the properties of <xref:System.Collections.Generic.KeyValuePair%602> instances are always serialized as "Key" and "Value" exactly, regardless of any <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> and <xref:System.Text.Json.JsonSerializerOptions.Encoder?displayProperty=nameWithType> options.</span></span> <span data-ttu-id="f8ec2-109">Aşağıdaki kod örneği, <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> belirtilen özellik adlandırma ilkesi tarafından önerilse de, Serileştirmeden sonra, ve özelliklerinin nasıl Camel bir şekilde olduğunu gösterir. *not*</span><span class="sxs-lookup"><span data-stu-id="f8ec2-109">The following code example shows how the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> properties are *not* camel-cased after serialization, even though the specified property-naming policy dictates so.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// Expected: {"key":1,"value":1}
// Actual: {"Key":1,"Value":1}
```

<span data-ttu-id="f8ec2-110">.NET 5,0 ' den başlayarak, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> ve <xref:System.Text.Json.JsonSerializerOptions.Encoder> seçenekleri, örnekleri serileştirilirken kabul edilir <xref:System.Collections.Generic.KeyValuePair%602> .</span><span class="sxs-lookup"><span data-stu-id="f8ec2-110">Starting in .NET 5.0, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options are honored when serializing <xref:System.Collections.Generic.KeyValuePair%602> instances.</span></span> <span data-ttu-id="f8ec2-111">Aşağıdaki kod örneği, <xref:System.Collections.Generic.KeyValuePair%602.Key> ve <xref:System.Collections.Generic.KeyValuePair%602.Value> özelliklerinin, belirtilen özellik adlandırma ilkesine uygun olarak serileştirme sonrasında nasıl Camel olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8ec2-111">The following code example shows how the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> properties are camel-cased after serialization, in accordance with the specified property-naming policy.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
KeyValuePair<int, int> kvp = KeyValuePair.Create(1, 1);
Console.WriteLine(JsonSerializer.Serialize(kvp, options));
// {"key":1,"value":1}
```

### <a name="deserialization"></a><span data-ttu-id="f8ec2-112">Seri</span><span class="sxs-lookup"><span data-stu-id="f8ec2-112">Deserialization</span></span>

<span data-ttu-id="f8ec2-113">.NET Core 3. x sürümlerinde ve [ NuGet paketindekiSystem.Text.Js](https://www.nuget.org/packages/System.Text.Json)4.7. x SÜRÜMLERINDE, <xref:System.Text.Json.JsonException> JSON Özellik adları tam olarak `Key` ve `Value` Örneğin büyük harfle başlamadıklarında oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f8ec2-113">In .NET Core 3.x versions and in the 4.7.x versions of the [System.Text.Json NuGet package](https://www.nuget.org/packages/System.Text.Json), a <xref:System.Text.Json.JsonException> is thrown when the JSON property names are not precisely `Key` and `Value`, for example, if they don't start with an uppercase letter.</span></span> <span data-ttu-id="f8ec2-114">Özel durum, belirtilen bir özellik adlandırma ilkesi açıkça izin veriyorsa bile oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f8ec2-114">The exception is thrown even if a specified property-naming policy expressly permits it.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";
// Throws JsonException.
JsonSerializer.Deserialize<KeyValuePair<int, int>>(json, options);
```

<span data-ttu-id="f8ec2-115">.NET 5,0 ' den başlayarak, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> ve <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> seçenekleri kullanılarak seri durumdan çıkarılırken kabul edilir <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="f8ec2-115">Starting in .NET 5.0, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> and <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> options are honored when deserializing using <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="f8ec2-116">Örneğin, aşağıdaki kod parçacığı, <xref:System.Collections.Generic.KeyValuePair%602.Key> <xref:System.Collections.Generic.KeyValuePair%602.Value> belirtilen özellik adlandırma ilkesi izin verdiğinden, küçük harf ve özellik adlarının başarıyla serisini kaldırma işlemi gösterir.</span><span class="sxs-lookup"><span data-stu-id="f8ec2-116">For example, the following code snippet shows successful deserialization of lowercased <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names because the specified property-naming policy permits it.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""key"":1,""value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

<span data-ttu-id="f8ec2-117">Önceki sürümlerle seri hale getirilen yüklere uyum sağlamak için, "Key" ve "Value", serisi kaldırılırken eşleşmesi için özel olarak tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="f8ec2-117">To accommodate payloads that were serialized with previous versions, "Key" and "Value" are special-cased to match when deserializing.</span></span> <span data-ttu-id="f8ec2-118"><xref:System.Collections.Generic.KeyValuePair%602.Key>Ve <xref:System.Collections.Generic.KeyValuePair%602.Value> özellik adları, aşağıdaki kod örneğinde yer almayan bir seçeneğe göre Camel değildir <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> .</span><span class="sxs-lookup"><span data-stu-id="f8ec2-118">Even though the <xref:System.Collections.Generic.KeyValuePair%602.Key> and <xref:System.Collections.Generic.KeyValuePair%602.Value> property names aren't camel-cased according to the in <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> option in the following code example, they deserialize successfully.</span></span>

```csharp
var options = new JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase };
string json = @"{""Key"":1,""Value"":1}";

KeyValuePair<int, int> kvp = JsonSerializer.Deserialize<KeyValuePair<int, int>>(json);
Console.WriteLine(kvp.Key); // 1
Console.WriteLine(kvp.Value); // 1
```

## <a name="version-introduced"></a><span data-ttu-id="f8ec2-119">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f8ec2-119">Version introduced</span></span>

<span data-ttu-id="f8ec2-120">5.0</span><span class="sxs-lookup"><span data-stu-id="f8ec2-120">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="f8ec2-121">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="f8ec2-121">Reason for change</span></span>

<span data-ttu-id="f8ec2-122">Önemli müşteri geri bildirimi, kullanılması <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> gerektiğini belirtti.</span><span class="sxs-lookup"><span data-stu-id="f8ec2-122">Substantial customer feedback indicated that the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> should be honored.</span></span> <span data-ttu-id="f8ec2-123"><xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> <xref:System.Text.Json.JsonSerializerOptions.Encoder> <xref:System.Collections.Generic.KeyValuePair%602> Tüm DIĞER düz eski CLR nesneleri (POCO) ile aynı şekilde işlenebilmesi için, ve seçenekleri de kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="f8ec2-123">For completeness, the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> and <xref:System.Text.Json.JsonSerializerOptions.Encoder> options are also honored, so that <xref:System.Collections.Generic.KeyValuePair%602> instances are treated the same as any other plain old CLR object (POCO).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="f8ec2-124">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f8ec2-124">Recommended action</span></span>

<span data-ttu-id="f8ec2-125">Bu değişiklik sizin için kesintiye uğradıysanız, istenen semantiğini uygulayan [özel bir dönüştürücü](../../../../standard/serialization/system-text-json-converters-how-to.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8ec2-125">If this change is disruptive to you, you can use a [custom converter](../../../../standard/serialization/system-text-json-converters-how-to.md) that implements the desired semantics.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="f8ec2-126">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f8ec2-126">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.SerializeAsync%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Serialize`
- `Overload:System.Text.Json.JsonSerializer.SerializeAsync`
- `Overload:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes`
- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

Serialization

-->
