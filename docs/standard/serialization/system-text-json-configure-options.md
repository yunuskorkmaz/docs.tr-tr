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
ms.openlocfilehash: 5f32e1369e58dd9550f28abc822f187dee46c022
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009839"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a><span data-ttu-id="a25af-103">İle JsonSerializerOptions örneklerinin örneğini oluşturma System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="a25af-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="a25af-104">Bu makalede, kullanırken performans sorunlarının nasıl önleneceği açıklanmaktadır <xref:System.Text.Json.JsonSerializerOptions> .</span><span class="sxs-lookup"><span data-stu-id="a25af-104">This article explains how to avoid performance problems when you use <xref:System.Text.Json.JsonSerializerOptions>.</span></span> <span data-ttu-id="a25af-105">Ayrıca, kullanılabilir parametreli oluşturucuların nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a25af-105">It also shows how to use the parameterized constructors that are available.</span></span>

## <a name="reuse-jsonserializeroptions-instances"></a><span data-ttu-id="a25af-106">JsonSerializerOptions örneklerini yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="a25af-106">Reuse JsonSerializerOptions instances</span></span>

<span data-ttu-id="a25af-107">`JsonSerializerOptions`Aynı seçeneklerle tekrar tekrar kullanırsanız, `JsonSerializerOptions` her kullandığınızda yeni bir örnek oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="a25af-107">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="a25af-108">Her çağrı için aynı örneği yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="a25af-108">Reuse the same instance for every call.</span></span> <span data-ttu-id="a25af-109">Bu kılavuz, özel dönüştürücüler için yazdığınız koda ve veya ' i çağırdığınızda geçerlidir <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a25af-109">This guidance applies to code you write for custom converters and when you call <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="a25af-110">Aşağıdaki kod, yeni seçenek örneklerinin kullanımı için performans cezaını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a25af-110">The following code demonstrates the performance penalty for using new options instances.</span></span>

:::code language="csharp" source="snippets/system-text-json-configure-options/csharp/ReuseOptionsInstances.cs":::

<span data-ttu-id="a25af-111">Yukarıdaki kod, aynı seçenek örneğini kullanarak küçük bir nesne 100.000 kez seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="a25af-111">The preceding code serializes a small object 100,000 times using the same options instance.</span></span> <span data-ttu-id="a25af-112">Daha sonra aynı nesneyi aynı sayıda seri hale getirir ve her seferinde yeni bir seçenek örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a25af-112">Then it serializes the same object the same number of times and creates a new options instance each time.</span></span> <span data-ttu-id="a25af-113">Tipik bir çalıştırma süresi farkı, 40.140 milisaniyeye kıyasla 190 ' dir.</span><span class="sxs-lookup"><span data-stu-id="a25af-113">A typical run time difference is 190 compared to 40,140 milliseconds.</span></span> <span data-ttu-id="a25af-114">Yineleme sayısını arttırmanız halinde fark daha büyük olur.</span><span class="sxs-lookup"><span data-stu-id="a25af-114">The difference is even greater if you increase the number of iterations.</span></span>

<span data-ttu-id="a25af-115">Seri hale getirici, yeni bir seçenek örneği geçirildiğinde nesne grafiğindeki her bir türün ilk serileştirilmesi sırasında bir ısınma aşamasına geçer.</span><span class="sxs-lookup"><span data-stu-id="a25af-115">The serializer undergoes a warm-up phase during the first serialization of each type in the object graph when a new options instance is passed to it.</span></span> <span data-ttu-id="a25af-116">Bu ısınma, serileştirme için gereken meta verilerin bir önbelleğinin oluşturulmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="a25af-116">This warm-up includes creating a cache of metadata that is needed for serialization.</span></span> <span data-ttu-id="a25af-117">Meta veriler, özellik Getters, ayarlayıcıları, Oluşturucu bağımsız değişkenleri, belirtilen öznitelikler ve benzeri temsilciler içerir.</span><span class="sxs-lookup"><span data-stu-id="a25af-117">The metadata includes delegates to property getters, setters, constructor arguments, specified attributes, and so forth.</span></span> <span data-ttu-id="a25af-118">Bu meta veri önbelleği seçenekler örneğinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="a25af-118">This metadata cache is stored in the options instance.</span></span> <span data-ttu-id="a25af-119">Aynı ısınma işlemi ve önbellek seri durumundan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="a25af-119">The same warm-up process and cache applies to deserialization.</span></span>

<span data-ttu-id="a25af-120">Bir örnekteki meta veri önbelleğinin boyutu, `JsonSerializerOptions` seri hale getirilecek türlerin sayısına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a25af-120">The size of the metadata cache in a `JsonSerializerOptions` instance depends on the number of types to be serialized.</span></span> <span data-ttu-id="a25af-121">Seri hale getirici için çok sayıda tür geçirirseniz — Örneğin, dinamik olarak üretilen türler —, önbellek boyutu büyümeye devam eder ve bir soruna neden olabilir `OutOfMemoryException` .</span><span class="sxs-lookup"><span data-stu-id="a25af-121">If you pass numerous types—for example, dynamically generated types—to the serializer, the cache size will continue to grow and can end up causing an `OutOfMemoryException`.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="a25af-122">JsonSerializerOptions 'ı Kopyala</span><span class="sxs-lookup"><span data-stu-id="a25af-122">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="a25af-123">[JsonSerializerOptions Oluşturucusu] (XREF:) var System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)), aşağıdaki örnekte gösterildiği gibi, var olan örnekle aynı seçeneklere sahip yeni bir örnek oluşturmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="a25af-123">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="a25af-124">`JsonSerializerOptions`Mevcut bir örneği alan bir Oluşturucu .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a25af-124">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="a25af-125">JsonSerializerOptions için Web Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="a25af-125">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="a25af-126">Web uygulamaları için farklı varsayılan değerlere sahip olan seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a25af-126">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="a25af-127">[JsonSerializerOptions Oluşturucusu] (XREF:) var System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults)? View = net-5,0&Preserve-View = true), aşağıdaki örnekte gösterildiği gibi, ASP.NET Core Web Apps için kullandığı varsayılan seçeneklerle yeni bir örnek oluşturmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="a25af-127">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="a25af-128">Web uygulamaları için farklı varsayılan değerlere sahip olan seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a25af-128">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="a25af-129">`JsonSerializerOptions`Varsayılan kümesini belirten bir Oluşturucu .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a25af-129">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="a25af-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a25af-130">See also</span></span>

* [<span data-ttu-id="a25af-131">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="a25af-131">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="a25af-132">JSON’u seri hale getirme ve seri halden çıkarma</span><span class="sxs-lookup"><span data-stu-id="a25af-132">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="a25af-133">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="a25af-133">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="a25af-134">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a25af-134">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="a25af-135">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="a25af-135">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="a25af-136">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="a25af-136">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="a25af-137">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="a25af-137">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="a25af-138">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="a25af-138">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="a25af-139">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="a25af-139">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="a25af-140">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="a25af-140">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="a25af-141">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="a25af-141">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="a25af-142">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="a25af-142">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="a25af-143">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="a25af-143">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="a25af-144">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="a25af-144">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="a25af-145">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="a25af-145">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="a25af-146">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="a25af-146">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="a25af-147">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="a25af-147">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
