---
title: 'Son değişiklik: ASP.NET Core uygulamalar tırnaklı sayıların serisini kaldırmada izin veriyor'
description: ASP.NET Core uygulamaların bir özel durum oluşturmak yerine JSON dizeleri olarak temsil edilen sayıları başarıyla seri durumdan çıkaracağı .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 10/21/2020
ms.openlocfilehash: fc8a4c6638be391c22c7cfb2fc7c216c88377f29
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761421"
---
# <a name="aspnet-core-apps-allow-deserializing-quoted-numbers"></a><span data-ttu-id="3a09a-103">ASP.NET Core uygulamalar, tırnak işaretli sayıların serisini kaldırmada izin veriyor</span><span class="sxs-lookup"><span data-stu-id="3a09a-103">ASP.NET Core apps allow deserializing quoted numbers</span></span>

<span data-ttu-id="3a09a-104">.NET 5,0 ' den başlayarak ASP.NET Core uygulamalar, tarafından belirtilen varsayılan seri kaldırma seçeneklerini kullanır <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3a09a-104">Starting in .NET 5.0, ASP.NET Core apps use the default deserialization options as specified by <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3a09a-105"><xref:System.Text.Json.JsonSerializerDefaults.Web>Seçenek kümesi, ayarı içerir <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3a09a-105">The <xref:System.Text.Json.JsonSerializerDefaults.Web> set of options includes setting <xref:System.Text.Json.JsonSerializerOptions.NumberHandling> to <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3a09a-106">Bu değişiklik, ASP.NET Core uygulamaların özel durum oluşturmak yerine JSON dizeleri olarak temsil edilen sayıları başarıyla seri durumdan çıkaracağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="3a09a-106">This change means that ASP.NET Core apps will successfully deserialize numbers that are represented as JSON strings instead of throwing an exception.</span></span>

## <a name="change-description"></a><span data-ttu-id="3a09a-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="3a09a-107">Change description</span></span>

<span data-ttu-id="3a09a-108">.NET Core 3,0-3,1 ' de, <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonException> JSON yükünde tırnak içine alınmış bir sayıyla karşılaştığında seri kaldırma sırasında bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3a09a-108">In .NET Core 3.0 - 3.1, <xref:System.Text.Json.JsonSerializer> throws a <xref:System.Text.Json.JsonException> during deserialization if it encounters a quoted number in a JSON payload.</span></span> <span data-ttu-id="3a09a-109">Tırnak işaretleri nesne grafiklerde sayı özellikleriyle eşleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3a09a-109">The quoted numbers are used to map with number properties in object graphs.</span></span> <span data-ttu-id="3a09a-110">.NET Core 3,0-3,1 ' de rakamlar yalnızca <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> belirteçlerden okunurdur.</span><span class="sxs-lookup"><span data-stu-id="3a09a-110">In .NET Core 3.0 - 3.1, numbers are only read from <xref:System.Text.Json.JsonTokenType.Number?displayProperty=nameWithType> tokens.</span></span>

<span data-ttu-id="3a09a-111">.NET 5,0 ' den başlayarak, JSON yüklere ilişkin tırnak işaretli sayılar, ASP.NET Core uygulamalar için varsayılan olarak geçerli kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="3a09a-111">Starting in .NET 5.0, quoted numbers in JSON payloads are considered valid, by default, for ASP.NET Core apps.</span></span> <span data-ttu-id="3a09a-112">Tırnak işaretli sayıların serisini kaldırma sırasında hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="3a09a-112">No exception is thrown during deserialization of quoted numbers.</span></span>

> [!TIP]
>
> - <span data-ttu-id="3a09a-113">Varsayılan, tek başına veya için davranış değişikliği yoktur <xref:System.Text.Json.JsonSerializer> <xref:System.Text.Json.JsonSerializerOptions> .</span><span class="sxs-lookup"><span data-stu-id="3a09a-113">There is no behavior change for the default, standalone <xref:System.Text.Json.JsonSerializer> or <xref:System.Text.Json.JsonSerializerOptions>.</span></span>
> - <span data-ttu-id="3a09a-114">Bu, teknik olarak önemli bir değişiklik değildir, çünkü bir senaryoyu daha kısıtlayıcı hale getirir (yani, bir özel durum oluşturmak yerine bir JSON dizesinden zorlama bir sayı içinde başarılı olur).</span><span class="sxs-lookup"><span data-stu-id="3a09a-114">This is technically not a breaking change, since it makes a scenario more permissive instead of more restrictive (that is, it succeeds in coercing a number from a JSON string instead of throwing an exception).</span></span> <span data-ttu-id="3a09a-115">Ancak, bu pek çok ASP.NET Core uygulamayı etkileyen önemli bir davranış değişikliği olduğundan, burada belgelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="3a09a-115">However, since this is a significant behavioral change that affects many ASP.NET Core apps, it is documented here.</span></span>
> - <span data-ttu-id="3a09a-116"><xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType>Ve <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> genişletme yöntemleri, <xref:System.Text.Json.JsonSerializerDefaults.Web> serileştirme seçenekleri kümesini de kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a09a-116">The <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpContentJsonExtensions.ReadFromJsonAsync%2A?displayProperty=nameWithType> extension methods also use the <xref:System.Text.Json.JsonSerializerDefaults.Web> set of serialization options.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="3a09a-117">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3a09a-117">Version introduced</span></span>

<span data-ttu-id="3a09a-118">5.0</span><span class="sxs-lookup"><span data-stu-id="3a09a-118">5.0</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="3a09a-119">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3a09a-119">Reason for change</span></span>

<span data-ttu-id="3a09a-120">Birden çok Kullanıcı, içinde daha fazla izin veren numara işleme için bir seçenek istedi <xref:System.Text.Json.JsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="3a09a-120">Multiple users have requested an option for more permissive number handling in <xref:System.Text.Json.JsonSerializer>.</span></span> <span data-ttu-id="3a09a-121">Bu geri bildirim, çok sayıda JSON üreticileri (örneğin, web genelindeki hizmetler) tırnak işaretleri halinde yaydığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3a09a-121">This feedback indicates that many JSON producers (for example, services across the web) emit quoted numbers.</span></span> <span data-ttu-id="3a09a-122">Alıntılanmış sayıların okunmasına (serisi kaldırılan) izin vererek, .NET uygulamaları varsayılan olarak bu yükleri Web bağlamlarına başarıyla ayrıştırabilirler.</span><span class="sxs-lookup"><span data-stu-id="3a09a-122">By allowing quoted numbers to be read (deserialized), .NET apps can successfully parse these payloads, by default, in web contexts.</span></span> <span data-ttu-id="3a09a-123">Yapılandırma, <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> farklı uygulama katmanlarında aynı seçenekleri (örneğin, istemci, sunucu ve paylaşılan) belirleyebilmeniz için aracılığıyla sunulur.</span><span class="sxs-lookup"><span data-stu-id="3a09a-123">The configuration is exposed via <xref:System.Text.Json.JsonSerializerDefaults.Web?displayProperty=nameWithType> so that you can specify the same options across different application layers, for example, client, server, and shared.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="3a09a-124">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3a09a-124">Recommended action</span></span>

<span data-ttu-id="3a09a-125">Bu değişiklik kesintiye uğradıysanız, örneğin, doğrulama için katı sayı işleme bağımlıysa, önceki davranışı yeniden etkinleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3a09a-125">If this change is disruptive, for example, if you depend on the strict number handling for validation, you can re-enable the previous behavior.</span></span> <span data-ttu-id="3a09a-126"><xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType>Seçeneğini olarak ayarlayın <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3a09a-126">Set the <xref:System.Text.Json.JsonSerializerOptions.NumberHandling?displayProperty=nameWithType> option to <xref:System.Text.Json.Serialization.JsonNumberHandling.Strict?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3a09a-127">ASP.NET Core MVC ve Web API uygulamaları için, aşağıdaki kodu kullanarak seçeneğini ' de yapılandırabilirsiniz `Startup` :</span><span class="sxs-lookup"><span data-stu-id="3a09a-127">For ASP.NET Core MVC and web API apps, you can configure the option in `Startup` by using the following code:</span></span>

```csharp
services.AddControllers()
   .AddJsonOptions(options.NumberHandling = JsonNumberHandling.Strict);
```

## <a name="affected-apis"></a><span data-ttu-id="3a09a-128">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3a09a-128">Affected APIs</span></span>

- <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=fullName>
- <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A?displayProperty=fullName>

<!--

### Affected APIs

- `Overload:System.Text.Json.JsonSerializer.Deserialize`
- `Overload:System.Text.Json.JsonSerializer.DeserializeAsync`

### Category

- ASP.NET Core
- Serialization

-->
