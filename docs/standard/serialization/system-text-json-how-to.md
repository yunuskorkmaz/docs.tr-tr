---
title: C#-.NET kullanarak JSON serileştirmek ve serisini kaldırma
description: System.Text.Json.Net 'TEKI JSON 'a seri hale getirmek ve seri durumdan çıkarmak için ad alanını nasıl kullanacağınızı öğrenin. Örnek kod içerir.
ms.date: 11/05/2020
no-loc:
- 'System.Text.Json'
- 'Newtonsoft.Json'
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: aba45a99562b67df17e1ff33ecc3c8bbad63ec30
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440822"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="97864-104">.NET içinde JSON ve seri hale getirme (sıralama ve kaldırma)</span><span class="sxs-lookup"><span data-stu-id="97864-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="97864-105">Bu makalede, <xref:System.Text.Json?displayProperty=fullName> JavaScript nesne gösterimi (JSON) ' den seri hale getirmek ve seri durumdan çıkarmak için ad alanının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="97864-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="97864-106">İçinden mevcut kodu aktarıyorsanız `Newtonsoft.Json` , bkz. [nasıl geçiş `System.Text.Json` yapılacağı ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="97864-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="97864-107">Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="97864-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="97864-108">Serileştirme örnek kodunun çoğu, <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` JSON (girintileme ve insanlar okunabilirlik için boşluk) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="97864-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="97864-109">Üretim kullanımı için genellikle bu ayar için varsayılan değerini kabul etmiş olursunuz `false` .</span><span class="sxs-lookup"><span data-stu-id="97864-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="97864-110">Kod örnekleri, aşağıdaki sınıfa ve türevlerini ifade eder:</span><span class="sxs-lookup"><span data-stu-id="97864-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="97864-111">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="97864-111">Namespaces</span></span>

<span data-ttu-id="97864-112"><xref:System.Text.Json>Ad alanı tüm giriş noktalarını ve ana türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="97864-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="97864-113"><xref:System.Text.Json.Serialization>Ad alanı, serileştirme ve seri durumdan çıkarma ile ilgili gelişmiş senaryolar ve özelleştirme için öznitelikler ve API 'leri içerir.</span><span class="sxs-lookup"><span data-stu-id="97864-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="97864-114">Bu makalede gösterilen kod örnekleri, `using` Bu ad alanlarından biri veya her ikisi için yönergeler gerektirir:</span><span class="sxs-lookup"><span data-stu-id="97864-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="97864-115"><xref:System.Runtime.Serialization>Ad alanındaki öznitelikler ' de desteklenmez `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="97864-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="97864-116">.NET nesnelerini JSON 'a yazma (serileştirme)</span><span class="sxs-lookup"><span data-stu-id="97864-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="97864-117">JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="97864-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="97864-118">Aşağıdaki örnek bir dize olarak JSON oluşturur:</span><span class="sxs-lookup"><span data-stu-id="97864-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="97864-119">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="97864-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="97864-120">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="97864-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="97864-121">Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97864-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="97864-122">Öğesinin aşırı yüklemesi `Serialize()` genel bir tür parametresi alır:</span><span class="sxs-lookup"><span data-stu-id="97864-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="97864-123">Serileştirme örneği</span><span class="sxs-lookup"><span data-stu-id="97864-123">Serialization example</span></span>

<span data-ttu-id="97864-124">Aşağıda, koleksiyon türü özellikleri ve Kullanıcı tanımlı bir tür içeren örnek bir sınıf verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-124">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

> [!TIP]
> <span data-ttu-id="97864-125">"POCO", [düz eskı clr nesnesini](https://en.wikipedia.org/wiki/Plain_old_CLR_object)temsil eder.</span><span class="sxs-lookup"><span data-stu-id="97864-125">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="97864-126">POCO, örneğin devralma veya öznitelikler aracılığıyla herhangi bir çerçeveye özgü türe bağımlı olmayan bir .NET türüdür.</span><span class="sxs-lookup"><span data-stu-id="97864-126">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="97864-127">Önceki türün bir örneğinin serileştirilmesi için JSON çıktısı aşağıdaki örnekteki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="97864-127">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="97864-128">JSON çıktısı varsayılan olarak Mini olarak belirlenir:</span><span class="sxs-lookup"><span data-stu-id="97864-128">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="97864-129">Aşağıdaki örnek aynı JSON 'ı gösterir, ancak biçimlendirilir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):</span><span class="sxs-lookup"><span data-stu-id="97864-129">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

### <a name="serialize-to-utf-8"></a><span data-ttu-id="97864-130">UTF-8 ' e serileştirme</span><span class="sxs-lookup"><span data-stu-id="97864-130">Serialize to UTF-8</span></span>

<span data-ttu-id="97864-131">UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="97864-131">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="97864-132">' İ <xref:System.Text.Json.JsonSerializer.Serialize%2A> alan bir aşırı yükleme <xref:System.Text.Json.Utf8JsonWriter> de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="97864-132">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="97864-133">UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="97864-133">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="97864-134">Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="97864-134">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="97864-135">Serileştirme davranışı</span><span class="sxs-lookup"><span data-stu-id="97864-135">Serialization behavior</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="97864-136">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="97864-136">By default, all public properties are serialized.</span></span> <span data-ttu-id="97864-137">[Yoksayılacak özellikleri belirtebilirsiniz](#ignore-properties).</span><span class="sxs-lookup"><span data-stu-id="97864-137">You can [specify properties to ignore](#ignore-properties).</span></span>
* <span data-ttu-id="97864-138">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="97864-138">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="97864-139">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="97864-139">By default, JSON is minified.</span></span> <span data-ttu-id="97864-140">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97864-140">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="97864-141">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="97864-141">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="97864-142">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="97864-142">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="97864-143">Varsayılan olarak, döngüsel başvurular algılanır ve özel durumlar oluşur.</span><span class="sxs-lookup"><span data-stu-id="97864-143">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="97864-144">[Başvuruları koruyabilir ve döngüsel başvuruları işleyebilirsiniz](#preserve-references-and-handle-circular-references).</span><span class="sxs-lookup"><span data-stu-id="97864-144">You can [preserve references and handle circular references](#preserve-references-and-handle-circular-references).</span></span>
* <span data-ttu-id="97864-145">Varsayılan olarak, [alanlar](../../csharp/programming-guide/classes-and-structs/fields.md) yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="97864-145">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="97864-146">[Alanları dahil](#include-fields)edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97864-146">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="97864-147">System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır.</span><span class="sxs-lookup"><span data-stu-id="97864-147">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="97864-148">Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="97864-148">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="97864-149">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="97864-149">By default, all public properties are serialized.</span></span> <span data-ttu-id="97864-150">[Yoksayılacak özellikleri belirtebilirsiniz](#ignore-properties).</span><span class="sxs-lookup"><span data-stu-id="97864-150">You can [specify properties to ignore](#ignore-properties).</span></span>
* <span data-ttu-id="97864-151">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="97864-151">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="97864-152">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="97864-152">By default, JSON is minified.</span></span> <span data-ttu-id="97864-153">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97864-153">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="97864-154">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="97864-154">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="97864-155">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="97864-155">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="97864-156">Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="97864-156">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="97864-157">[Alanlar](../../csharp/programming-guide/classes-and-structs/fields.md) yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="97864-157">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="97864-158">Desteklenen türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="97864-158">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="97864-159">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="97864-159">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="97864-160">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span><span class="sxs-lookup"><span data-stu-id="97864-160">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="97864-161">Tek boyutlu ve pürüzlü Diziler ( `T[][]` ).</span><span class="sxs-lookup"><span data-stu-id="97864-161">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="97864-162">Aşağıdaki ad alanlarından gelen koleksiyonlar ve sözlükler.</span><span class="sxs-lookup"><span data-stu-id="97864-162">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="97864-163">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="97864-163">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="97864-164">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span><span class="sxs-lookup"><span data-stu-id="97864-164">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="97864-165">Tek boyutlu ve pürüzlü Diziler ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="97864-165">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="97864-166">`Dictionary<string,TValue>` Burada `TValue` , `object` `JsonElement` veya bir poco.</span><span class="sxs-lookup"><span data-stu-id="97864-166">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="97864-167">Aşağıdaki ad alanlarından Koleksiyonlar.</span><span class="sxs-lookup"><span data-stu-id="97864-167">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="97864-168">Ek türleri işlemek veya yerleşik dönüştürücüler tarafından desteklenmeyen işlevler sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="97864-168">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="97864-169">JSON 'ı .NET Objects 'e okuma (serisini kaldırma)</span><span class="sxs-lookup"><span data-stu-id="97864-169">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="97864-170">Bir dizeden veya dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="97864-170">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="97864-171">Aşağıdaki örnek, bir dizeden JSON okur ve `WeatherForecastWithPOCOs` daha önce [serileştirme örneği](#serialization-example)için gösterilen sınıfının bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="97864-171">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="97864-172">Zaman uyumlu kod kullanarak bir dosyadan seri durumdan çıkarmak için, aşağıdaki örnekte gösterildiği gibi dosyayı bir dizeye okuyun:</span><span class="sxs-lookup"><span data-stu-id="97864-172">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="97864-173">Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için yöntemini çağırın <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> :</span><span class="sxs-lookup"><span data-stu-id="97864-173">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="97864-174">UTF-8 ' den serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="97864-174">Deserialize from UTF-8</span></span>

<span data-ttu-id="97864-175">UTF-8 ' den seri durumdan çıkarmak için, <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> `Utf8JsonReader` `ReadOnlySpan<byte>` Aşağıdaki örneklerde gösterildiği gibi bir veya içeren bir aşırı yükleme çağırın.</span><span class="sxs-lookup"><span data-stu-id="97864-175">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="97864-176">Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="97864-176">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="97864-177">Seri durumdan çıkarma davranışı</span><span class="sxs-lookup"><span data-stu-id="97864-177">Deserialization behavior</span></span>

<span data-ttu-id="97864-178">JSON serisi kaldırılırken aşağıdaki davranışlar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="97864-178">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="97864-179">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="97864-179">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="97864-180">[Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="97864-180">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="97864-181">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="97864-181">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="97864-182">Ortak olmayan oluşturucular seri hale getirici tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="97864-182">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="97864-183">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenir.</span><span class="sxs-lookup"><span data-stu-id="97864-183">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="97864-184">Bkz. [değişmez türler ve kayıtlar](#immutable-types-and-records).</span><span class="sxs-lookup"><span data-stu-id="97864-184">See [Immutable types and Records](#immutable-types-and-records).</span></span>
* <span data-ttu-id="97864-185">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="97864-185">By default, enums are supported as numbers.</span></span> <span data-ttu-id="97864-186">[Enum adlarını dizeler olarak seri hale](#enums-as-strings)getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97864-186">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="97864-187">Varsayılan olarak, alanlar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="97864-187">By default, fields are ignored.</span></span> <span data-ttu-id="97864-188">[Alanları dahil](#include-fields)edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97864-188">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="97864-189">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97864-189">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="97864-190">[Yorumlara ve sondaki virgüllerin bulunmasına izin](#allow-comments-and-trailing-commas)verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97864-190">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="97864-191">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="97864-191">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="97864-192">System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır.</span><span class="sxs-lookup"><span data-stu-id="97864-192">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="97864-193">Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="97864-193">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="97864-194">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="97864-194">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="97864-195">[Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="97864-195">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span> <span data-ttu-id="97864-196">ASP.NET Core uygulamalar [Varsayılan olarak büyük/küçük harf duyarlı belirtir](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="97864-196">ASP.NET Core apps [specify case-insensitivity by default](#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="97864-197">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="97864-197">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="97864-198">Seri durumdan çıkarma için genel, iç veya özel olabilen parametresiz bir Oluşturucu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97864-198">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="97864-199">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="97864-199">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="97864-200">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="97864-200">By default, enums are supported as numbers.</span></span> <span data-ttu-id="97864-201">[Enum adlarını dizeler olarak seri hale](#enums-as-strings)getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97864-201">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="97864-202">Alanlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="97864-202">Fields aren't supported.</span></span>
* <span data-ttu-id="97864-203">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97864-203">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="97864-204">[Yorumlara ve sondaki virgüllerin bulunmasına izin](#allow-comments-and-trailing-commas)verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97864-204">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="97864-205">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="97864-205">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="97864-206">System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır.</span><span class="sxs-lookup"><span data-stu-id="97864-206">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="97864-207">Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="97864-207">For more information, see [Web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="97864-208">Yerleşik dönüştürücüler tarafından desteklenmeyen işlevselliği sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="97864-208">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="97864-209">Biçimlendirilen JSON 'a serileştirme</span><span class="sxs-lookup"><span data-stu-id="97864-209">Serialize to formatted JSON</span></span>

<span data-ttu-id="97864-210">JSON çıkışını gerçekten yazdırmak için şu <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> şekilde ayarlayın `true` :</span><span class="sxs-lookup"><span data-stu-id="97864-210">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="97864-211">Aşağıda, seri hale getirilebilir ve düzgün şekilde yazdırılan JSON çıkışının örnek bir türü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-211">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="include-fields"></a><span data-ttu-id="97864-212">Dahil etme alanları</span><span class="sxs-lookup"><span data-stu-id="97864-212">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="97864-213"><xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, seri hale getirilirken veya seri durumdan çıkarılırken alanları dahil etmek için genel ayarını veya [[jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="97864-213">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="15,17,19,31":::

<span data-ttu-id="97864-214">Salt okuma alanlarını yok saymak için <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> genel ayarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="97864-214">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="97864-215">Alanlar System.Text.Json .NET Core 3,1 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="97864-215">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="97864-216">[Özel dönüştürücüler](system-text-json-converters-how-to.md) , bu işlevselliği sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="97864-216">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="customize-json-names-and-values"></a><span data-ttu-id="97864-217">JSON adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="97864-217">Customize JSON names and values</span></span>

<span data-ttu-id="97864-218">Varsayılan olarak, özellik adları ve sözlük anahtarları, büyük/küçük harf gibi JSON çıktısında değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="97864-218">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="97864-219">Sabit listesi değerleri sayı olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="97864-219">Enum values are represented as numbers.</span></span> <span data-ttu-id="97864-220">Bu bölümde nasıl yapılacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="97864-220">This section explains how to:</span></span>

* [<span data-ttu-id="97864-221">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="97864-221">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="97864-222">Tüm özellik adlarını ortası durumuna Dönüştür</span><span class="sxs-lookup"><span data-stu-id="97864-222">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="97864-223">Özel özellik adlandırma ilkesi uygulama</span><span class="sxs-lookup"><span data-stu-id="97864-223">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="97864-224">Sözlük anahtarlarını ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="97864-224">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="97864-225">Numaralandırmaları dizelere ve ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="97864-225">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="97864-226">JSON özellik adlarını ve değerlerini özel olarak işleme gerektiren diğer senaryolar için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="97864-226">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="97864-227">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="97864-227">Customize individual property names</span></span>

<span data-ttu-id="97864-228">Ayrı özelliklerin adını ayarlamak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="97864-228">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="97864-229">Serileştirme ve sonuç JSON için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-229">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="97864-230">Bu öznitelik tarafından ayarlanan özellik adı:</span><span class="sxs-lookup"><span data-stu-id="97864-230">The property name set by this attribute:</span></span>

* <span data-ttu-id="97864-231">Serileştirme ve seri durumundan çıkarma için her iki yönde de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="97864-231">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="97864-232">Özellik adlandırma ilkelerine göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="97864-232">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="97864-233">Tüm JSON Özellik adları için ortası Case kullanın</span><span class="sxs-lookup"><span data-stu-id="97864-233">Use camel case for all JSON property names</span></span>

<span data-ttu-id="97864-234">Tüm JSON Özellik adları için ortası durumunu kullanmak için, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase` Aşağıdaki örnekte gösterildiği gibi olarak ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="97864-234">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="97864-235">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-235">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="97864-236">Ortası durum özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="97864-236">The camel case property naming policy:</span></span>

* <span data-ttu-id="97864-237">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="97864-237">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="97864-238">Öznitelikleri tarafından geçersiz kılınır `[JsonPropertyName]` .</span><span class="sxs-lookup"><span data-stu-id="97864-238">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="97864-239">Bu nedenle, örnekteki JSON Özellik adının `Wind` ortası durum olmaması neden olur.</span><span class="sxs-lookup"><span data-stu-id="97864-239">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="97864-240">Özel bir JSON Özellik adlandırma ilkesi kullanma</span><span class="sxs-lookup"><span data-stu-id="97864-240">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="97864-241">Özel bir JSON Özellik adlandırma ilkesi kullanmak için, <xref:System.Text.Json.JsonNamingPolicy> <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> Aşağıdaki örnekte gösterildiği gibi yönteminden türeten bir sınıf oluşturun ve yöntemi geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="97864-241">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="97864-242">Daha sonra <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> özelliği, adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="97864-242">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="97864-243">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-243">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="97864-244">JSON özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="97864-244">The JSON property naming policy:</span></span>

* <span data-ttu-id="97864-245">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="97864-245">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="97864-246">Öznitelikleri tarafından geçersiz kılınır `[JsonPropertyName]` .</span><span class="sxs-lookup"><span data-stu-id="97864-246">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="97864-247">Bu, örnekteki JSON Özellik adının `Wind` büyük harfle değil.</span><span class="sxs-lookup"><span data-stu-id="97864-247">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="97864-248">Camel durum sözlüğü anahtarları</span><span class="sxs-lookup"><span data-stu-id="97864-248">Camel case dictionary keys</span></span>

<span data-ttu-id="97864-249">Seri hale getirilecek bir nesnenin özelliği tür ise `Dictionary<string,TValue>` , `string` anahtarlar ortası duruma dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="97864-249">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="97864-250">Bunu yapmak için, <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase` Aşağıdaki örnekte gösterildiği gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="97864-250">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="97864-251">Anahtar-değer çiftlerine sahip adlı bir sözlük ile bir nesneyi serileştirmek `TemperatureRanges` `"ColdMinTemp", 20` ve `"HotMinTemp", 40` Aşağıdaki örnekte olduğu gibi JSON çıktısına neden olur:</span><span class="sxs-lookup"><span data-stu-id="97864-251">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="97864-252">Sözlük anahtarları için ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="97864-252">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="97864-253">Bir sözlüğün serisini kaldırırsanız, için belirtseniz bile anahtarlar JSON dosyasıyla eşleşir `JsonNamingPolicy.CamelCase` `DictionaryKeyPolicy` .</span><span class="sxs-lookup"><span data-stu-id="97864-253">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="97864-254">Dizeler dize olarak numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="97864-254">Enums as strings</span></span>

<span data-ttu-id="97864-255">Varsayılan olarak, numaralandırmalar sayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="97864-255">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="97864-256">Sabit listesi adlarını dizeler olarak seri hale getirmek için öğesini kullanın <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .</span><span class="sxs-lookup"><span data-stu-id="97864-256">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="97864-257">Örneğin, bir sabit listesi olan aşağıdaki sınıfı seri hale getirmeniz gerektiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="97864-257">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="97864-258">Özet ise `Hot` , varsayılan olarak SERILEŞTIRILMIŞ JSON sayısal değer 3 ' ü içerir:</span><span class="sxs-lookup"><span data-stu-id="97864-258">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="97864-259">Aşağıdaki örnek kod, sayısal değerler yerine enum adlarını seri hale getirir ve adları ortası örneğine dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="97864-259">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="97864-260">Elde edilen JSON aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="97864-260">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="97864-261">Aşağıdaki örnekte gösterildiği gibi, sabit listesi dize adları da seri durumdan çıkarılmış olabilir:</span><span class="sxs-lookup"><span data-stu-id="97864-261">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="ignore-properties"></a><span data-ttu-id="97864-262">Özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="97864-262">Ignore properties</span></span>

<span data-ttu-id="97864-263">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="97864-263">By default, all public properties are serialized.</span></span> <span data-ttu-id="97864-264">Bir kısmının JSON çıktısında görünmesini istemiyorsanız, birkaç seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="97864-264">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="97864-265">Bu bölümde nasıl yoksayılacağını açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="97864-265">This section explains how to ignore:</span></span>

::: zone pivot="dotnet-5-0"

* [<span data-ttu-id="97864-266">Bireysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="97864-266">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="97864-267">Tüm salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="97864-267">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="97864-268">Tüm null değerli özellikler</span><span class="sxs-lookup"><span data-stu-id="97864-268">All null-value properties</span></span>](#ignore-all-null-value-properties)
* [<span data-ttu-id="97864-269">Tüm varsayılan değer özellikleri</span><span class="sxs-lookup"><span data-stu-id="97864-269">All default-value properties</span></span>](#ignore-all-default-value-properties)
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [<span data-ttu-id="97864-270">Bireysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="97864-270">Individual properties</span></span>](#ignore-individual-properties)
* [<span data-ttu-id="97864-271">Tüm salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="97864-271">All read-only properties</span></span>](#ignore-all-read-only-properties)
* [<span data-ttu-id="97864-272">Tüm null değerli özellikler</span><span class="sxs-lookup"><span data-stu-id="97864-272">All null-value properties</span></span>](#ignore-all-null-value-properties)
::: zone-end

### <a name="ignore-individual-properties"></a><span data-ttu-id="97864-273">Tek tek özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="97864-273">Ignore individual properties</span></span>

<span data-ttu-id="97864-274">Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="97864-274">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="97864-275">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-275">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

::: zone pivot="dotnet-5-0"
<span data-ttu-id="97864-276">[[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğinin özelliğini ayarlayarak koşullu dışlama belirtebilirsiniz `Condition` .</span><span class="sxs-lookup"><span data-stu-id="97864-276">You can specify conditional exclusion by setting the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property.</span></span> <span data-ttu-id="97864-277"><xref:System.Text.Json.Serialization.JsonIgnoreCondition>Sabit listesi aşağıdaki seçenekleri sağlar:</span><span class="sxs-lookup"><span data-stu-id="97864-277">The <xref:System.Text.Json.Serialization.JsonIgnoreCondition> enum provides the following options:</span></span>

* <span data-ttu-id="97864-278">`Always` -Özellik her zaman yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="97864-278">`Always` - The property is always ignored.</span></span> <span data-ttu-id="97864-279">Hayır `Condition` belirtilmişse, bu seçenek kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="97864-279">If no `Condition` is specified, this option is assumed.</span></span>
* <span data-ttu-id="97864-280">`Never` -Özelliği `DefaultIgnoreCondition` ,, `IgnoreReadOnlyProperties` ve genel ayarlarından bağımsız olarak her zaman serileştirilmiş ve seri durumdan çıkarılmış olur `IgnoreReadOnlyFields` .</span><span class="sxs-lookup"><span data-stu-id="97864-280">`Never` - The property is always serialized and deserialized, regardless of the `DefaultIgnoreCondition`, `IgnoreReadOnlyProperties`, and `IgnoreReadOnlyFields` global settings.</span></span>
* <span data-ttu-id="97864-281">`WhenWritingDefault` -Bir başvuru türü veya değer türü ise, bu özellik serileştirme üzerinde yok sayılır `null` `default` .</span><span class="sxs-lookup"><span data-stu-id="97864-281">`WhenWritingDefault` - The property is ignored on serialization if it's a reference type `null` or a value type `default`.</span></span>
* <span data-ttu-id="97864-282">`WhenWritingNull` -Bir başvuru türü ise, bu özellik serileştirme üzerinde yok sayılır `null` .</span><span class="sxs-lookup"><span data-stu-id="97864-282">`WhenWritingNull` - The property is ignored on serialization if it's a reference type `null`.</span></span>

<span data-ttu-id="97864-283">Aşağıdaki örnek, [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğinin özelliğinin kullanımını gösterir `Condition` :</span><span class="sxs-lookup"><span data-stu-id="97864-283">The following example illustrates use of the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute's `Condition` property:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/JsonIgnoreAttributeExample.cs" highlight="10,13,16":::
::: zone-end

### <a name="ignore-all-read-only-properties"></a><span data-ttu-id="97864-284">Tüm salt okunurdur özellikleri yoksay</span><span class="sxs-lookup"><span data-stu-id="97864-284">Ignore all read-only properties</span></span>

<span data-ttu-id="97864-285">Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="97864-285">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="97864-286">Serileştirilirken tüm salt okunurdur özellikleri yok saymak için <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> `true` Aşağıdaki örnekte gösterildiği gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="97864-286">To ignore all read-only properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="97864-287">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-287">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="97864-288">Bu seçenek yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="97864-288">This option applies only to serialization.</span></span> <span data-ttu-id="97864-289">Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="97864-289">During deserialization, read-only properties are ignored by default.</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="97864-290">Bu seçenek yalnızca özellikler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="97864-290">This option applies only to properties.</span></span> <span data-ttu-id="97864-291">[Alanları serileştirilirken](#include-fields)salt okunurdur alanları yok saymak için <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> genel ayarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="97864-291">To ignore read-only fields when [serializing fields](#include-fields), use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

### <a name="ignore-all-null-value-properties"></a><span data-ttu-id="97864-292">Tüm null değer özelliklerini yoksay</span><span class="sxs-lookup"><span data-stu-id="97864-292">Ignore all null-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="97864-293">Tüm null değer özelliklerini yok saymak için, <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull> Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="97864-293">To ignore all null-value properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingNull>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreNullOnSerialize.cs" highlight="28":::

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="97864-294">Serileştirilirken tüm null değer özelliklerini yok saymak için, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> `true` Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="97864-294">To ignore all null-value properties when serializing, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="97864-295">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-295">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="97864-296">Özellik</span><span class="sxs-lookup"><span data-stu-id="97864-296">Property</span></span> |<span data-ttu-id="97864-297">Değer</span><span class="sxs-lookup"><span data-stu-id="97864-297">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="97864-298">Tarih</span><span class="sxs-lookup"><span data-stu-id="97864-298">Date</span></span>    | <span data-ttu-id="97864-299">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="97864-299">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="97864-300">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="97864-300">TemperatureCelsius</span></span>| <span data-ttu-id="97864-301">25</span><span class="sxs-lookup"><span data-stu-id="97864-301">25</span></span> |
| <span data-ttu-id="97864-302">Özet</span><span class="sxs-lookup"><span data-stu-id="97864-302">Summary</span></span>| <span data-ttu-id="97864-303">null</span><span class="sxs-lookup"><span data-stu-id="97864-303">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

::: zone-end

### <a name="ignore-all-default-value-properties"></a><span data-ttu-id="97864-304">Tüm varsayılan değer özelliklerini yoksay</span><span class="sxs-lookup"><span data-stu-id="97864-304">Ignore all default-value properties</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="97864-305">Değer türü özelliklerindeki varsayılan değerlerin serileştirmesini engellemek için, <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault> Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="97864-305">To prevent serialization of default values in value type properties, set the <xref:System.Text.Json.JsonSerializerOptions.DefaultIgnoreCondition> property to <xref:System.Text.Json.Serialization.JsonIgnoreCondition.WhenWritingDefault>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/IgnoreValueDefaultOnSerialize.cs" highlight="28":::
::: zone-end

<span data-ttu-id="97864-306">`WhenWritingDefault`Ayar aynı zamanda null değer başvuru türü özelliklerinin serileştirmesini de önler.</span><span class="sxs-lookup"><span data-stu-id="97864-306">The `WhenWritingDefault` setting also prevents serialization of null-value reference type properties.</span></span>

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="97864-307">.NET Core 3,1 ' deki değer türü varsayılanlarına sahip özelliklerin serileştirmesini önleyen yerleşik bir yol yoktur System.Text.Json .</span><span class="sxs-lookup"><span data-stu-id="97864-307">There is no built-in way to prevent serialization of properties with value type defaults in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="customize-character-encoding"></a><span data-ttu-id="97864-308">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="97864-308">Customize character encoding</span></span>

<span data-ttu-id="97864-309">Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="97864-309">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="97864-310">Diğer bir deyişle, bu, `\uxxxx` karakterin Unicode kodunun bulunduğu konum ile değiştirilir `xxxx` .</span><span class="sxs-lookup"><span data-stu-id="97864-310">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="97864-311">Örneğin, `Summary` özelliği Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="97864-311">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="97864-312">Dil karakter kümelerini serileştirme</span><span class="sxs-lookup"><span data-stu-id="97864-312">Serialize language character sets</span></span>

<span data-ttu-id="97864-313">Bir veya daha fazla dilin karakter kümesini kaçış olmadan seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi bir örneği oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> :</span><span class="sxs-lookup"><span data-stu-id="97864-313">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="97864-314">Bu kod, Kiril veya Yunan karakterlerinden kaçış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="97864-314">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="97864-315">`Summary`Özellik Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="97864-315">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="97864-316">Tüm dil kümelerini kaçış olmadan seri hale getirmek için kullanın <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="97864-316">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="97864-317">Belirli karakterleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="97864-317">Serialize specific characters</span></span>

<span data-ttu-id="97864-318">Diğer bir seçenek de, kaçırılmadan, izin vermek istediğiniz tek tek karakterleri belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="97864-318">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="97864-319">Aşağıdaki örnek, жарко 'in yalnızca ilk iki karakterini seri hale getirir:</span><span class="sxs-lookup"><span data-stu-id="97864-319">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="97864-320">Yukarıdaki kod tarafından üretilen JSON örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-320">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="97864-321">Tüm karakterleri seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="97864-321">Serialize all characters</span></span>

<span data-ttu-id="97864-322"><xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, kullanarak kaçı en aza indirin:</span><span class="sxs-lookup"><span data-stu-id="97864-322">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="97864-323">Varsayılan kodlayıcıyla karşılaştırıldığında kodlayıcı, `UnsafeRelaxedJsonEscaping` karakterlerin kaçışsız geçmesine izin verme konusunda daha fazla izne sahiptir:</span><span class="sxs-lookup"><span data-stu-id="97864-323">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="97864-324">,, Ve gibi HTML 'ye duyarlı karakterleri atmaz `<` `>` `&` `'` .</span><span class="sxs-lookup"><span data-stu-id="97864-324">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="97864-325">Bu, XSS veya bilgi açıklama saldırılarına karşı ek derinlemesine savunma korumaları sunmaz, örneğin, *karakter* kümesinde istemci ve sunucu disagreeing neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="97864-325">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="97864-326">Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="97864-326">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="97864-327">Örneğin, sunucu yanıt üst bilgisini gönderiyorsa onu kullanabilirsiniz `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="97864-327">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="97864-328">Ham `UnsafeRelaxedJsonEscaping` çıkışın BIR HTML sayfasına veya bir öğeye yayılmasın `<script>` .</span><span class="sxs-lookup"><span data-stu-id="97864-328">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="97864-329">Türetilmiş sınıfların serileştirme özellikleri</span><span class="sxs-lookup"><span data-stu-id="97864-329">Serialize properties of derived classes</span></span>

<span data-ttu-id="97864-330">Çok biçimli bir tür hiyerarşisinin serileştirilmesi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="97864-330">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="97864-331">Örneğin, bir özellik bir arabirim ya da soyut sınıf olarak tanımlanmışsa, çalışma zamanı türü ek özelliklere sahip olsa bile yalnızca arabirim veya soyut sınıf üzerinde tanımlanan özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="97864-331">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="97864-332">Bu davranışın istisnaları, bu bölümde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="97864-332">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="97864-333">Örneğin, bir `WeatherForecast` sınıfınız ve türetilmiş bir sınıfınız olduğunu varsayalım `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="97864-333">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="97864-334">Ve derleme zamanında yöntemin tür bağımsız değişkeninin `Serialize` Şu olduğunu varsayalım `WeatherForecast` :</span><span class="sxs-lookup"><span data-stu-id="97864-334">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="97864-335">Bu senaryoda, `WindSpeed` `weatherForecast` nesne gerçekten bir nesne olsa bile Özellik serileştirilmez `WeatherForecastDerived` .</span><span class="sxs-lookup"><span data-stu-id="97864-335">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="97864-336">Yalnızca temel sınıf özellikleri serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="97864-336">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="97864-337">Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="97864-337">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="97864-338">Yukarıdaki örnekteki türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="97864-338">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="97864-339"><xref:System.Text.Json.JsonSerializer.Serialize%2A>Çalışma zamanında türü belirtmenize olanak sağlayan aşırı yüklemesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="97864-339">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="97864-340">Seri hale getirilecek nesneyi bildirin `object` .</span><span class="sxs-lookup"><span data-stu-id="97864-340">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="97864-341">Yukarıdaki örnek senaryoda, her iki yaklaşım `WindSpeed` ÖZELLIĞIN JSON çıktısına dahil olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="97864-341">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="97864-342">Bu yaklaşımlar yalnızca kök nesnenin seri hale getirilmesi için, bu kök nesnenin özellikleri için değil, polimorfik serileştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="97864-342">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="97864-343">Bunları tür olarak tanımlarsanız alt düzey nesneler için polimorfik serileştirme alabilirsiniz `object` .</span><span class="sxs-lookup"><span data-stu-id="97864-343">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="97864-344">Örneğin, `WeatherForecast` sınıfınızın, tür olarak tanımlanabilen adında bir özelliği olduğunu varsayalım `PreviousForecast` `WeatherForecast` `object` :</span><span class="sxs-lookup"><span data-stu-id="97864-344">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="97864-345">`PreviousForecast`Özelliği bir örneği içeriyorsa `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="97864-345">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="97864-346">Serileştirmede JSON çıktısı `WeatherForecastWithPrevious` **içermez** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="97864-346">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="97864-347">Serileştirmede JSON çıktısı `WeatherForecastWithPreviousAsObject` **dahildir** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="97864-347">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="97864-348">Seri hale getirmek için `WeatherForecastWithPreviousAsObject` , `Serialize<object>` ya da `GetType` kök nesnesi türetilmiş bir tür olabilecek bir nesne olmadığından çağırmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="97864-348">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="97864-349">Aşağıdaki kod örneği, `Serialize<object>` veya çağırmaz `GetType` :</span><span class="sxs-lookup"><span data-stu-id="97864-349">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="97864-350">Yukarıdaki kod doğru şekilde serileştirir `WeatherForecastWithPreviousAsObject` :</span><span class="sxs-lookup"><span data-stu-id="97864-350">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "PreviousForecast": {
    "WindSpeed": 35,
    "Date": "2019-08-01T00:00:00-07:00",
    "TemperatureCelsius": 25,
    "Summary": "Hot"
  }
}
```

<span data-ttu-id="97864-351">Özellikleri, arabirimler ile birlikte tanımlamaya yönelik aynı yaklaşım `object` .</span><span class="sxs-lookup"><span data-stu-id="97864-351">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="97864-352">Aşağıdaki arabirime ve uygulamaya sahip olduğunuzu ve uygulama örnekleri içeren özelliklerle bir sınıfı seri hale getirmek istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="97864-352">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="97864-353">Bir örneğini serileştirçalıştığınızda `Forecasts` , yalnızca `Tuesday` `WindSpeed` özelliğini gösterir, çünkü `Tuesday` Şu şekilde tanımlanır `object` :</span><span class="sxs-lookup"><span data-stu-id="97864-353">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="97864-354">Aşağıdaki örnek, önceki koddan elde edilen JSON 'u göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="97864-354">The following example shows the JSON that results from the preceding code:</span></span>

```json
{
  "Monday": {
    "Date": "2020-01-06T00:00:00-08:00",
    "TemperatureCelsius": 10,
    "Summary": "Cool"
  },
  "Tuesday": {
    "Date": "2020-01-07T00:00:00-08:00",
    "TemperatureCelsius": 11,
    "Summary": "Rainy",
    "WindSpeed": 10
  }
}
```

<span data-ttu-id="97864-355">Polimorfik **serileştirme** hakkında daha fazla bilgi için ve **serisini kaldırma** hakkında bilgi için, bkz. ' [den Newtonsoft.Json System.Text.Json ' ye geçiş](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="97864-355">For more information about polymorphic **serialization** , and for information about **deserialization** , see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="97864-356">Yorumlara ve sondaki virgülleri izin ver</span><span class="sxs-lookup"><span data-stu-id="97864-356">Allow comments and trailing commas</span></span>

<span data-ttu-id="97864-357">Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="97864-357">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="97864-358">JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini olarak ayarlayın `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="97864-358">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="97864-359">Ve sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="97864-359">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="97864-360">Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="97864-360">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="97864-361">Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-361">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="97864-362">Büyük/küçük harfe duyarsız Özellik eşleştirme</span><span class="sxs-lookup"><span data-stu-id="97864-362">Case-insensitive property matching</span></span>

<span data-ttu-id="97864-363">Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar.</span><span class="sxs-lookup"><span data-stu-id="97864-363">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="97864-364">Bu davranışı değiştirmek için şu <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> şekilde ayarlayın `true` :</span><span class="sxs-lookup"><span data-stu-id="97864-364">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="97864-365">Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="97864-365">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="97864-366">Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="97864-366">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="97864-367">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="97864-367">Handle overflow JSON</span></span>

<span data-ttu-id="97864-368">Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97864-368">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="97864-369">Örneğin, hedef türünün bu olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="97864-369">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="97864-370">Ve seri durumdan çıkarılacak JSON şu şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="97864-370">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="97864-371">Gösterilen türde gösterilen JSON serisini kaldırırsanız, `DatesAvailable` ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor.</span><span class="sxs-lookup"><span data-stu-id="97864-371">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="97864-372">Bu özellikler gibi ek verileri yakalamak için, [[Jsonextensiondata]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini türü bir özelliğe uygulayın `Dictionary<string,object>` `Dictionary<string,JsonElement>` :</span><span class="sxs-lookup"><span data-stu-id="97864-372">To capture extra data such as these properties, apply the [[JsonExtensionData]](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="97864-373">Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veri özelliğin anahtar-değer çiftleri haline gelir `ExtensionData` :</span><span class="sxs-lookup"><span data-stu-id="97864-373">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="97864-374">Özellik</span><span class="sxs-lookup"><span data-stu-id="97864-374">Property</span></span> |<span data-ttu-id="97864-375">Değer</span><span class="sxs-lookup"><span data-stu-id="97864-375">Value</span></span>  |<span data-ttu-id="97864-376">Notlar</span><span class="sxs-lookup"><span data-stu-id="97864-376">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="97864-377">Tarih</span><span class="sxs-lookup"><span data-stu-id="97864-377">Date</span></span>    | <span data-ttu-id="97864-378">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="97864-378">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="97864-379">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="97864-379">TemperatureCelsius</span></span>| <span data-ttu-id="97864-380">0</span><span class="sxs-lookup"><span data-stu-id="97864-380">0</span></span> | <span data-ttu-id="97864-381">Büyük/küçük harfe duyarlı uyuşmazlık ( `temperatureCelsius` JSON 'da), bu nedenle özellik ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="97864-381">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="97864-382">Özet</span><span class="sxs-lookup"><span data-stu-id="97864-382">Summary</span></span> | <span data-ttu-id="97864-383">Sık Erişimli</span><span class="sxs-lookup"><span data-stu-id="97864-383">Hot</span></span> ||
| <span data-ttu-id="97864-384">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="97864-384">ExtensionData</span></span> | <span data-ttu-id="97864-385">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="97864-385">temperatureCelsius: 25</span></span> |<span data-ttu-id="97864-386">Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.</span><span class="sxs-lookup"><span data-stu-id="97864-386">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="97864-387">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="97864-387">DatesAvailable:</span></span><br>  <span data-ttu-id="97864-388">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="97864-388">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="97864-389">8/2/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="97864-389">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="97864-390">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="97864-390">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="97864-391">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="97864-391">SummaryWords:</span></span><br><span data-ttu-id="97864-392">Seyrek Erişim</span><span class="sxs-lookup"><span data-stu-id="97864-392">Cool</span></span><br><span data-ttu-id="97864-393">Rüzgarlı</span><span class="sxs-lookup"><span data-stu-id="97864-393">Windy</span></span><br><span data-ttu-id="97864-394">İnsankimliği</span><span class="sxs-lookup"><span data-stu-id="97864-394">Humid</span></span> |<span data-ttu-id="97864-395">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="97864-395">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="97864-396">Hedef nesne serileştirildiğinde, uzantı veri anahtarı değer çiftleri, gelen JSON 'da olduğu gibi JSON özellikleri olur:</span><span class="sxs-lookup"><span data-stu-id="97864-396">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 0,
  "Summary": "Hot",
  "temperatureCelsius": 25,
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="97864-397">`ExtensionData`Özellik ADıNıN JSON içinde görünmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="97864-397">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="97864-398">Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="97864-398">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="preserve-references-and-handle-circular-references"></a><span data-ttu-id="97864-399">Başvuruları koru ve döngüsel başvuruları işle</span><span class="sxs-lookup"><span data-stu-id="97864-399">Preserve references and handle circular references</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="97864-400">Başvuruları korumak ve döngüsel başvuruları işlemek için olarak ayarlayın <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A> .</span><span class="sxs-lookup"><span data-stu-id="97864-400">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="97864-401">Bu ayar aşağıdaki davranışa neden olur:</span><span class="sxs-lookup"><span data-stu-id="97864-401">This setting causes the following behavior:</span></span>

* <span data-ttu-id="97864-402">Seri hale getirme:</span><span class="sxs-lookup"><span data-stu-id="97864-402">On serialize:</span></span>

  <span data-ttu-id="97864-403">Karmaşık türler yazarken serileştirici Ayrıca meta veri özellikleri ( `$id` , `$values` ve `$ref` ) yazar.</span><span class="sxs-lookup"><span data-stu-id="97864-403">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="97864-404">Seri durumdan çıkarma tarihi:</span><span class="sxs-lookup"><span data-stu-id="97864-404">On deserialize:</span></span>

  <span data-ttu-id="97864-405">Meta veriler beklenir (zorunlu olmasa da) ve seri hale getirici bunu anlamaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="97864-405">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="97864-406">Aşağıdaki kod, ayarın kullanımını gösterir `Preserve` .</span><span class="sxs-lookup"><span data-stu-id="97864-406">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="97864-407">Bu özellik değer türlerini veya sabit türleri korumak için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="97864-407">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="97864-408">Seri durumdan çıkarma sırasında, tüm yük okunduktan sonra sabit bir tür örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="97864-408">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="97864-409">Bu nedenle, JSON yükünün içinde bir başvuru görünürse aynı örneğin serisini kaldırma imkansızdır.</span><span class="sxs-lookup"><span data-stu-id="97864-409">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="97864-410">Değer türleri, değişmez türler ve diziler için hiçbir başvuru meta verisi serileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="97864-410">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="97864-411">Seri durumdan çıkarma sırasında, veya bulunursa bir özel durum oluşturulur `$ref` `$id` .</span><span class="sxs-lookup"><span data-stu-id="97864-411">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="97864-412">Ancak, `$id` `$values` kullanılarak seri hale getirilen yüklerin serisini kaldırma olanağı sağlamak için değer türleri (koleksiyonlar durumunda ve ' de) yoksayar Newtonsoft.Json .</span><span class="sxs-lookup"><span data-stu-id="97864-412">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="97864-413">Newtonsoft.Json Bu tür türler için meta verileri serileştirmez.</span><span class="sxs-lookup"><span data-stu-id="97864-413">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="97864-414">Nesnelerin eşit olup olmadığını anlamak için, System.Text.Json <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType> <xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType> değer eşitlik yerine başvuru eşitlik () kullanır ( <xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> iki nesne örneği karşılaştırılırken).</span><span class="sxs-lookup"><span data-stu-id="97864-414">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="97864-415">Başvuruların serileştirilme ve seri durumdan çıkarıldığı hakkında daha fazla bilgi için bkz <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType> ..</span><span class="sxs-lookup"><span data-stu-id="97864-415">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="97864-416"><xref:System.Text.Json.Serialization.ReferenceResolver>Sınıfı serileştirme ve seri durumundan çıkarma için başvuruları koruma davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97864-416">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="97864-417">Özel davranışı belirtmek için türetilmiş bir sınıf oluşturun.</span><span class="sxs-lookup"><span data-stu-id="97864-417">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="97864-418">Bir örnek için bkz. [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span><span class="sxs-lookup"><span data-stu-id="97864-418">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="97864-419">System.Text.Json .NET Core 3,1 yalnızca değere göre serileştirme destekler ve döngüsel başvurular için bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97864-419">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="allow-or-write-numbers-in-quotes"></a><span data-ttu-id="97864-420">Tırnak işaretleri halinde izin ver veya yaz</span><span class="sxs-lookup"><span data-stu-id="97864-420">Allow or write numbers in quotes</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="97864-421">Bazı serileştiriciler sayıları JSON dizeleri (tırnak işaretleriyle çevrelenmiş) olarak kodlayabilir.</span><span class="sxs-lookup"><span data-stu-id="97864-421">Some serializers encode numbers as JSON strings (surrounded by quotes).</span></span> <span data-ttu-id="97864-422">Örneğin: `{"DegreesCelsius":"23"}` yerine `{"DegreesCelsius":23}` .</span><span class="sxs-lookup"><span data-stu-id="97864-422">For example: `{"DegreesCelsius":"23"}` instead of `{"DegreesCelsius":23}`.</span></span> <span data-ttu-id="97864-423">Tırnak işaretleri içindeki sayıları seri hale getirmek veya giriş nesnesi grafiğinin tamamına tırnak içinde kabul etmek için <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="97864-423">To serialize numbers in quotes or accept numbers in quotes across the entire input object graph, set <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A?displayProperty=nameWithType> as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/QuotedNumbers.cs" highlight="27-28":::

<span data-ttu-id="97864-424">System.Text.JsonASP.NET Core aracılığıyla dolaylı olarak kullandığınızda, ASP.NET Core [Web varsayılan seçeneklerini](xref:System.Text.Json.JsonSerializerDefaults.Web)belirttiğinden, serisi kaldırılırken tırnak işaretli sayılara izin verilir.</span><span class="sxs-lookup"><span data-stu-id="97864-424">When you use System.Text.Json indirectly through ASP.NET Core, quoted numbers are allowed when deserializing because ASP.NET Core specifies [web default options](xref:System.Text.Json.JsonSerializerDefaults.Web).</span></span>

<span data-ttu-id="97864-425">Belirli özellikler, alanlar veya türler için tırnak işaretli sayılara izin vermek veya yazmak için [[Jsonnumberhandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="97864-425">To allow or write quoted numbers for specific properties, fields, or types, use the [[JsonNumberHandling]](xref:System.Text.Json.Serialization.JsonNumberHandlingAttribute) attribute.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="97864-426">System.Text.Json .NET Core 3,1, tırnak işaretleriyle çevrelenen sayıları serileştirmek veya seri durumdan çıkarmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="97864-426">System.Text.Json in .NET Core 3.1 doesn't support serializing or deserializing numbers surrounded by quotation marks.</span></span> <span data-ttu-id="97864-427">Daha fazla bilgi için bkz. [tekliflere Izin verme veya yazma numaraları](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span><span class="sxs-lookup"><span data-stu-id="97864-427">For more information, see [Allow or write numbers in quotes](system-text-json-migrate-from-newtonsoft-how-to.md#allow-or-write-numbers-in-quotes).</span></span>
::: zone-end

## <a name="immutable-types-and-records"></a><span data-ttu-id="97864-428">Sabit türler ve kayıtlar</span><span class="sxs-lookup"><span data-stu-id="97864-428">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="97864-429">System.Text.Json , sabit bir sınıfın veya yapının serisini kaldırma olanağı sağlayan parametreli bir Oluşturucu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="97864-429">System.Text.Json can use a parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="97864-430">Bir sınıf için, tek Oluşturucu parametreli bir ise, bu Oluşturucu kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="97864-430">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="97864-431">Bir yapı veya birden çok Oluşturucu içeren bir sınıf için, [[Jsonconstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) özniteliğini uygulayarak kullanılacak olanı belirtin.</span><span class="sxs-lookup"><span data-stu-id="97864-431">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) attribute.</span></span> <span data-ttu-id="97864-432">Özniteliği kullanılmazsa, varsa Ortak parametresiz bir Oluşturucu her zaman kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97864-432">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="97864-433">Özniteliği yalnızca ortak oluşturucularla birlikte kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97864-433">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="97864-434">Aşağıdaki örnek `[JsonConstructor]` özniteliğini kullanır:</span><span class="sxs-lookup"><span data-stu-id="97864-434">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="97864-435">C# 9 ' da kayıtlar aşağıdaki örnekte gösterildiği gibi desteklenir:</span><span class="sxs-lookup"><span data-stu-id="97864-435">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="97864-436">Tüm özellik ayarlayıcıları ortak olmadığından, sabit olan türler için, [genel olmayan özellik erişimcileri](#non-public-property-accessors)hakkında aşağıdaki bölüme bakın.</span><span class="sxs-lookup"><span data-stu-id="97864-436">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="97864-437">`JsonConstructorAttribute` ve C# 9 kayıt desteği .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="97864-437">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="97864-438">Ortak olmayan özellik erişimcileri</span><span class="sxs-lookup"><span data-stu-id="97864-438">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="97864-439">Ortak olmayan bir özellik erişimcisinin kullanımını etkinleştirmek için, aşağıdaki örnekte gösterildiği gibi [[Jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="97864-439">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="97864-440">Ortak olmayan özellik erişimcileri .NET Core 3,1 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="97864-440">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="97864-441">Daha fazla bilgi için, bkz. [ Newtonsoft.Json makaleden geçiş](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span><span class="sxs-lookup"><span data-stu-id="97864-441">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="97864-442">JsonSerializerOptions 'ı Kopyala</span><span class="sxs-lookup"><span data-stu-id="97864-442">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="97864-443">[JsonSerializerOptions Oluşturucusu] (XREF:) var System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerOptions)), aşağıdaki örnekte gösterildiği gibi, var olan örnekle aynı seçeneklere sahip yeni bir örnek oluşturmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="97864-443">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="97864-444">`JsonSerializerOptions`Mevcut bir örneği alan bir Oluşturucu .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="97864-444">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="97864-445">JsonSerializerOptions için Web Varsayılanları</span><span class="sxs-lookup"><span data-stu-id="97864-445">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="97864-446">Web uygulamaları için farklı varsayılan değerlere sahip olan seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="97864-446">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="97864-447">[JsonSerializerOptions Oluşturucusu] (XREF:) var System.Text.Json . JsonSerializerOptions .% 23ctor ( System.Text.Json . JsonSerializerDefaults)? View = net-5,0&Preserve-View = true), aşağıdaki örnekte gösterildiği gibi, ASP.NET Core Web Apps için kullandığı varsayılan seçeneklerle yeni bir örnek oluşturmanıza olanak sağlar:</span><span class="sxs-lookup"><span data-stu-id="97864-447">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="97864-448">Web uygulamaları için farklı varsayılan değerlere sahip olan seçenekler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="97864-448">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="97864-449">`JsonSerializerOptions`Varsayılan kümesini belirten bir Oluşturucu .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="97864-449">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="97864-450">HttpClient ve HttpContent genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="97864-450">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="97864-451">JSON yüklerini ağdan serileştirmek ve serisini kaldırma yaygın işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="97864-451">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="97864-452">[HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) ve [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) üzerindeki genişletme yöntemleri, bu işlemleri tek bir kod satırında yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="97864-452">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="97864-453">Bu uzantı yöntemleri, [JsonSerializerOptions için Web varsayılanlarını](#web-defaults-for-jsonserializeroptions)kullanır.</span><span class="sxs-lookup"><span data-stu-id="97864-453">These extension methods use [web defaults for JsonSerializerOptions](#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="97864-454">Aşağıdaki örnek, ve kullanımını göstermektedir <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="97864-454">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="23,30":::

<span data-ttu-id="97864-455">Ayrıca, HttpContent için uzantı yöntemleri de vardır System.Text.Json . [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)</span><span class="sxs-lookup"><span data-stu-id="97864-455">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="97864-456">Ve ' de uzantı yöntemleri `HttpClient` `HttpContent` System.Text.Json .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="97864-456">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="97864-457">Utf8JsonReader, Utf8JsonWriter ve JsonDocument</span><span class="sxs-lookup"><span data-stu-id="97864-457">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="97864-458"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> , bir veya ' dan okunan UTF-8 kodlu JSON metin için yüksek performanslı, düşük bir ayırma, Salt ilet okuyucu olur `ReadOnlySpan<byte>` `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="97864-458"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="97864-459">, `Utf8JsonReader` Özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="97864-459">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="97864-460"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>Yöntemi `Utf8JsonReader` , kapakların altında kullanır.</span><span class="sxs-lookup"><span data-stu-id="97864-460">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="97864-461"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> , ve gibi ortak .NET türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur `String` `Int32` `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="97864-461"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="97864-462">Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="97864-462">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="97864-463"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>Yöntemi `Utf8JsonWriter` , kapakların altında kullanır.</span><span class="sxs-lookup"><span data-stu-id="97864-463">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="97864-464"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> kullanarak salt okunurdur Belge Nesne Modeli (DOM) oluşturma yeteneği sağlar `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="97864-464"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="97864-465">DOM, bir JSON yükünde verilere rastgele erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="97864-465">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="97864-466">Yükü oluşturan JSON öğelerine tür aracılığıyla erişilebilir <xref:System.Text.Json.JsonElement> .</span><span class="sxs-lookup"><span data-stu-id="97864-466">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="97864-467">`JsonElement`Türü, JSON metnini ortak .net türlerine dönüştürmek Için API 'lerle birlikte dizi ve nesne numaralandırıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="97864-467">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="97864-468">`JsonDocument` bir <xref:System.Text.Json.JsonDocument.RootElement> özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="97864-468">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="97864-469">Aşağıdaki bölümlerde, bu araçların JSON okuma ve yazma için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="97864-469">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="97864-470">Veri erişimi için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="97864-470">Use JsonDocument for access to data</span></span>

<span data-ttu-id="97864-471">Aşağıdaki örnek, <xref:System.Text.Json.JsonDocument> BIR JSON dizesindeki verilere rastgele erişim için sınıfının nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="97864-471">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="97864-472">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="97864-472">The preceding code:</span></span>

* <span data-ttu-id="97864-473">Analiz edilecek JSON 'in adlı bir dizede olduğunu varsayar `jsonString` .</span><span class="sxs-lookup"><span data-stu-id="97864-473">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="97864-474">Özelliği olan bir dizideki nesneler için Ortalama bir sınıf hesaplar `Students` `Grade` .</span><span class="sxs-lookup"><span data-stu-id="97864-474">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="97864-475">Bir sınıfa sahip olmayan öğrenciler için varsayılan bir 70 sınıfı atar.</span><span class="sxs-lookup"><span data-stu-id="97864-475">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="97864-476">Her yinelemeyle bir değişkeni arttırarak öğrencileri sayar `count` .</span><span class="sxs-lookup"><span data-stu-id="97864-476">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="97864-477"><xref:System.Text.Json.JsonElement.GetArrayLength%2A>Aşağıdaki örnekte gösterildiği gibi bir alternatif çağrdır:</span><span class="sxs-lookup"><span data-stu-id="97864-477">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="97864-478">Bu kodun işlediği JSON örneğine bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-478">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="97864-479">JSON yazmak için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="97864-479">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="97864-480">Aşağıdaki örnek, öğesinden nasıl JSON yazılacağını göstermektedir <xref:System.Text.Json.JsonDocument> :</span><span class="sxs-lookup"><span data-stu-id="97864-480">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="97864-481">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="97864-481">The preceding code:</span></span>

* <span data-ttu-id="97864-482">Bir JSON dosyasını okur, verileri bir `JsonDocument` dosyasına yükler ve bir dosyaya biçimli (düzgün yazdırılmış) JSON yazar.</span><span class="sxs-lookup"><span data-stu-id="97864-482">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="97864-483"><xref:System.Text.Json.JsonDocumentOptions>JSON girişi içindeki açıklamalara izin verildiğini ancak yok sayılacağını belirtmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="97864-483">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="97864-484">İşiniz bittiğinde, <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> Yazıcı üzerindeki çağrılar.</span><span class="sxs-lookup"><span data-stu-id="97864-484">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="97864-485">Diğer bir seçenek de yazıcı boşaltıatıldığı zaman yazıcının temizlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="97864-485">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="97864-486">Örnek kod tarafından işlenecek JSON girişi örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="97864-486">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="97864-487">Sonuç, aşağıdaki düzgün yazdırılmış JSON çıktıdır:</span><span class="sxs-lookup"><span data-stu-id="97864-487">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="97864-488">Utf8JsonWriter kullanma</span><span class="sxs-lookup"><span data-stu-id="97864-488">Use Utf8JsonWriter</span></span>

<span data-ttu-id="97864-489">Aşağıdaki örnek sınıfının nasıl kullanılacağını gösterir <xref:System.Text.Json.Utf8JsonWriter> :</span><span class="sxs-lookup"><span data-stu-id="97864-489">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="97864-490">Utf8JsonReader kullanma</span><span class="sxs-lookup"><span data-stu-id="97864-490">Use Utf8JsonReader</span></span>

<span data-ttu-id="97864-491">Aşağıdaki örnek sınıfının nasıl kullanılacağını gösterir <xref:System.Text.Json.Utf8JsonReader> :</span><span class="sxs-lookup"><span data-stu-id="97864-491">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="97864-492">Yukarıdaki kod, `jsonUtf8` DEĞIŞKENIN UTF-8 olarak kodlanmış GEÇERLI JSON içeren bir bayt dizisi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="97864-492">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="97864-493">Utf8JsonReader kullanarak verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="97864-493">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="97864-494">Aşağıdaki örnek, bir dosyanın zaman uyumlu olarak nasıl okunacağını ve bir değerin nasıl aranacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="97864-494">The following example shows how to read a file synchronously and search for a value.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="97864-495">( [Bu örneğin zaman uyumsuz bir sürümü](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs) kullanılabilir.)</span><span class="sxs-lookup"><span data-stu-id="97864-495">(An [async version of this example](https://github.com/dotnet/samples/blob/18e31a5f1abd4f347bf96bfdc3e40e2cfb36e319/core/json/Program.cs) is available.)</span></span>

<span data-ttu-id="97864-496">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="97864-496">The preceding code:</span></span>

* <span data-ttu-id="97864-497">JSON 'un bir nesne dizisi içerdiğini ve her nesne dize türünde bir "ad" özelliği içerebildiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="97864-497">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="97864-498">"University" ile biten nesneleri ve "ad" özellik değerlerini sayar.</span><span class="sxs-lookup"><span data-stu-id="97864-498">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="97864-499">Dosyanın UTF-16 olarak kodlandığını varsayar ve bunu UTF-8 ' e dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="97864-499">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="97864-500">Aşağıdaki kod kullanılarak UTF-8 olarak kodlanmış bir dosya doğrudan bir ile okunabilir `ReadOnlySpan<byte>` :</span><span class="sxs-lookup"><span data-stu-id="97864-500">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="97864-501">Dosya bir UTF-8 bayt sırası işareti (BOM) içeriyorsa, okuyucu metin gerektirdiğinden, baytları öğesine geçirmeden önce kaldırın `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="97864-501">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="97864-502">Aksi takdirde, BOM geçersiz JSON olarak değerlendirilir ve okuyucu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97864-502">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="97864-503">Yukarıdaki kodun okuya, bir JSON örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="97864-503">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="97864-504">Sonuçtaki Özet ileti "2 ' den 4 ' ün" University "ile biten adlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="97864-504">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="97864-505">Utf8JsonReader kullanarak akıştan okuma</span><span class="sxs-lookup"><span data-stu-id="97864-505">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="97864-506">Büyük bir dosyayı (örneğin, boyutu bir gigabayt veya daha fazla) okurken, dosyanın tamamını aynı anda belleğe yükleme zorunluluğunu ortadan kaldırmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97864-506">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="97864-507">Bu senaryo için bir kullanabilirsiniz <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="97864-507">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="97864-508">`Utf8JsonReader`Bir akıştan okumak için kullanırken, aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="97864-508">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="97864-509">Kısmi JSON yükünün bulunduğu arabellek en az, onun içindeki en büyük JSON belirteci kadar büyük olmalıdır, böylece okuyucu ilerlemeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="97864-509">The buffer containing the partial JSON payload must be at least as large as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="97864-510">Arabellek en az JSON içindeki boşluk olan en büyük dizi kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="97864-510">The buffer must be at least as large as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="97864-511">Okuyucu, JSON yükünde bir sonrakini tamamen okuuncaya kadar okuduğu verileri takip etmez <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> .</span><span class="sxs-lookup"><span data-stu-id="97864-511">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="97864-512">Bu nedenle, arabellekte kalan baytlar varsa, bunları okuyucuya yeniden geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="97864-512">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="97864-513"><xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A>Kaç baytın kaldığını anlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97864-513">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="97864-514">Aşağıdaki kod bir akıştan nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="97864-514">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="97864-515">Örnek bir gösterir <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="97864-515">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="97864-516">Benzer kod, <xref:System.IO.FileStream> `FileStream` Başlangıç AŞAMASıNDA bir UTF-8 bom içerdiğinde, ile birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="97864-516">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="97864-517">Bu durumda, kalan baytları öğesine geçirmeden önce bu üç baytı arabellekten çıkarmanız gerekir `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="97864-517">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="97864-518">Aksi halde, BOM JSON 'ın geçerli bir parçası olarak kabul edilmediğinden okuyucu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97864-518">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="97864-519">Örnek kod, bir 4KB arabelleği ile başlar ve boyutun, bir bütün JSON belirtecine sığamayacak kadar büyük olmadığını bulduğu her bulduğunda, bu, okuyucunun JSON yükünde ilerlemesinin ilerlemesini sağlamak için gerekli olan her seferinde arabellek boyutunu iki katına çıkarır.</span><span class="sxs-lookup"><span data-stu-id="97864-519">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not large enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="97864-520">Kod parçacığında belirtilen JSON örneği, yalnızca çok küçük bir başlangıç arabelleği boyutu ayarlarsanız (örneğin, 10 bayt) bir arabellek boyutunu tetikler.</span><span class="sxs-lookup"><span data-stu-id="97864-520">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="97864-521">Başlangıçtaki arabellek boyutunu 10 olarak ayarlarsanız, `Console.WriteLine` deyimler arabellek boyutunun arttığı nedeni ve etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="97864-521">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="97864-522">4 KB ilk arabellek boyutunda, tüm örnek JSON her biri tarafından gösterilir `Console.WriteLine` ve arabellek boyutunun hiçbir zaman artırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="97864-522">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="97864-523">Yukarıdaki örnek, arabelleğin ne kadar büyüeceği hakkında sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="97864-523">The preceding example sets no limit to how large the buffer can grow.</span></span> <span data-ttu-id="97864-524">Belirteç boyutu çok büyükse, kod bir <xref:System.OutOfMemoryException> özel durumla başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="97864-524">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="97864-525">Bu, JSON 1 GB veya daha fazla boyuttaki bir belirteç içeriyorsa, 1 GB boyutunun, arabelleğe sığamayacak kadar büyük bir boyuta neden olduğundan bu durum oluşabilir `int32` .</span><span class="sxs-lookup"><span data-stu-id="97864-525">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="97864-526">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="97864-526">Additional resources</span></span>

* [<span data-ttu-id="97864-527">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="97864-527">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="97864-528">Özel dönüştürücü yazma</span><span class="sxs-lookup"><span data-stu-id="97864-528">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="97864-529">Öğesinden geçiş Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="97864-529">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="97864-530">İçinde DateTime ve DateTimeOffset desteği System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="97864-530">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="97864-531">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="97864-531">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
