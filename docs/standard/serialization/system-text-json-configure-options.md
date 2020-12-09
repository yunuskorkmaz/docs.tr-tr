---
title: İle JsonSerializerOptions örneği System.Text.Json
description: Performans sorunlarından kaçının ve JsonSerializerOptions örnekleri için kullanılabilir oluşturucuların nasıl kullanılacağını öğrenin.
ms.date: 12/02/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 257c99e117dea9a9b3ab2352c9a442d71a2cdabd
ms.sourcegitcommit: 0014aa4d5cb2da56a70e03fc68f663d64df5247a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96918560"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a><span data-ttu-id="16114-103">İle JsonSerializerOptions örneklerinin örneğini oluşturma System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="16114-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="16114-104">Bu makalede, kullanırken performans sorunlarının nasıl önleneceği açıklanmaktadır <xref:System.Text.Json.JsonSerializerOptions> .</span><span class="sxs-lookup"><span data-stu-id="16114-104">This article explains how to avoid performance problems when you use <xref:System.Text.Json.JsonSerializerOptions>.</span></span> <span data-ttu-id="16114-105">Ayrıca, kullanılabilir parametreli oluşturucuların nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16114-105">It also shows how to use the parameterized constructors that are available.</span></span>

## <a name="reuse-jsonserializeroptions-instances"></a><span data-ttu-id="16114-106">JsonSerializerOptions örneklerini yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="16114-106">Reuse JsonSerializerOptions instances</span></span>

<span data-ttu-id="16114-107">`JsonSerializerOptions`Aynı seçeneklerle tekrar tekrar kullanırsanız, `JsonSerializerOptions` her kullandığınızda yeni bir örnek oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="16114-107">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="16114-108">Her çağrı için aynı örneği yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="16114-108">Reuse the same instance for every call.</span></span> <span data-ttu-id="16114-109">Bu kılavuz, özel dönüştürücüler için yazdığınız koda ve veya ' i çağırdığınızda geçerlidir <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="16114-109">This guidance applies to code you write for custom converters and when you call <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="16114-110">Aşağıdaki kod, yeni seçenek örneklerinin kullanımı için performans cezaını gösterir.</span><span class="sxs-lookup"><span data-stu-id="16114-110">The following code demonstrates the performance penalty for using new options instances.</span></span>

:::code language="csharp" source="snippets/system-text-json-configure-options/csharp/ReuseOptionsInstances.cs":::

<span data-ttu-id="16114-111">Yukarıdaki kod, aynı seçenek örneğini kullanarak küçük bir nesne 100.000 kez seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="16114-111">The preceding code serializes a small object 100,000 times using the same options instance.</span></span> <span data-ttu-id="16114-112">Daha sonra aynı nesneyi aynı sayıda seri hale getirir ve her seferinde yeni bir seçenek örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="16114-112">Then it serializes the same object the same number of times and creates a new options instance each time.</span></span> <span data-ttu-id="16114-113">Tipik bir çalıştırma süresi farkı, 40.140 milisaniyeye kıyasla 190 ' dir.</span><span class="sxs-lookup"><span data-stu-id="16114-113">A typical run time difference is 190 compared to 40,140 milliseconds.</span></span> <span data-ttu-id="16114-114">Yineleme sayısını arttırmanız halinde fark daha büyük olur.</span><span class="sxs-lookup"><span data-stu-id="16114-114">The difference is even greater if you increase the number of iterations.</span></span>

<span data-ttu-id="16114-115">Seri hale getirici, yeni bir seçenek örneği geçirildiğinde nesne grafiğindeki her bir türün ilk serileştirilmesi sırasında bir ısınma aşamasına geçer.</span><span class="sxs-lookup"><span data-stu-id="16114-115">The serializer undergoes a warm-up phase during the first serialization of each type in the object graph when a new options instance is passed to it.</span></span> <span data-ttu-id="16114-116">Bu ısınma, serileştirme için gereken meta verilerin bir önbelleğinin oluşturulmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="16114-116">This warm-up includes creating a cache of metadata that is needed for serialization.</span></span> <span data-ttu-id="16114-117">Meta veriler, özellik Getters, ayarlayıcıları, Oluşturucu bağımsız değişkenleri, belirtilen öznitelikler ve benzeri temsilciler içerir.</span><span class="sxs-lookup"><span data-stu-id="16114-117">The metadata includes delegates to property getters, setters, constructor arguments, specified attributes, and so forth.</span></span> <span data-ttu-id="16114-118">Bu meta veri önbelleği seçenekler örneğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="16114-118">This metadata cache is stored in the options instance.</span></span> <span data-ttu-id="16114-119">Aynı ısınma işlemi ve önbellek seri durumundan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="16114-119">The same warm-up process and cache applies to deserialization.</span></span>

<span data-ttu-id="16114-120">Bir örnekteki meta veri önbelleğinin boyutu, `JsonSerializerOptions` seri hale getirilecek türlerin sayısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="16114-120">The size of the metadata cache in a `JsonSerializerOptions` instance depends on the number of types to be serialized.</span></span> <span data-ttu-id="16114-121">Seri hale getirici için çok sayıda tür geçirirseniz — Örneğin, dinamik olarak üretilen türler —, önbellek boyutu büyümeye devam eder ve bir soruna neden olabilir `OutOfMemoryException` .</span><span class="sxs-lookup"><span data-stu-id="16114-121">If you pass numerous types—for example, dynamically generated types—to the serializer, the cache size will continue to grow and can end up causing an `OutOfMemoryException`.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="16114-122">JsonSerializerOptions 'ı Kopyala</span><span class="sxs-lookup"><span data-stu-id="16114-122">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="16114-123">[JsonSerializerOptions Oluşturucusu] (XREF:) var System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)), aşağıdaki örnekte gösterildiği gibi, var olan örnekle aynı seçeneklere sahip yeni bir örnek oluşturmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="16114-123">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="16114-124">`JsonSerializerOptions`Mevcut bir örneği alan bir Oluşturucu .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="16114-124">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="16114-125">JsonSerializerOptions için Web Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="16114-125">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="16114-126">Web uygulamaları için farklı varsayılan değerlere sahip olan seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="16114-126">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="16114-127">[JsonSerializerOptions Oluşturucusu] (XREF:) var System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults)? View = net-5,0&Preserve-View = true), aşağıdaki örnekte gösterildiği gibi, ASP.NET Core Web Apps için kullandığı varsayılan seçeneklerle yeni bir örnek oluşturmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="16114-127">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="16114-128">Web uygulamaları için farklı varsayılan değerlere sahip olan seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="16114-128">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="16114-129">`JsonSerializerOptions`Varsayılan kümesini belirten bir Oluşturucu .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="16114-129">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="16114-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="16114-130">See also</span></span>

* [<span data-ttu-id="16114-131">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="16114-131">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="16114-132">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="16114-132">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="16114-133">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="16114-133">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="16114-134">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="16114-134">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="16114-135">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="16114-135">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="16114-136">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="16114-136">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="16114-137">Döngüsel başvuruları koru</span><span class="sxs-lookup"><span data-stu-id="16114-137">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="16114-138">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="16114-138">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="16114-139">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="16114-139">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="16114-140">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="16114-140">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
