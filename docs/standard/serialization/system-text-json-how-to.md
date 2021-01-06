---
title: C#-.NET kullanarak JSON serileştirmek ve serisini kaldırma
description: System.Text.Json.Net 'TEKI JSON 'a seri hale getirmek ve seri durumdan çıkarmak için ad alanını nasıl kullanacağınızı öğrenin. Örnek kod içerir.
ms.date: 01/04/2021
ms.custom: contperf-fy21q2
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: bd257cf8d79ea2afa209fe71ad7eff969a62d6b2
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938721"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="2021d-104">.NET içinde JSON ve seri hale getirme (sıralama ve kaldırma)</span><span class="sxs-lookup"><span data-stu-id="2021d-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="2021d-105">Bu makalede, <xref:System.Text.Json?displayProperty=fullName> JavaScript nesne gösterimi (JSON) ' den seri hale getirmek ve seri durumdan çıkarmak için ad alanının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2021d-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="2021d-106">İçinden mevcut kodu aktarıyorsanız `Newtonsoft.Json` , bkz. [nasıl geçiş `System.Text.Json` yapılacağı ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="2021d-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="2021d-107">Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="2021d-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="2021d-108">Serileştirme örnek kodunun çoğu, <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` JSON (girintileme ve insanlar okunabilirlik için boşluk) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2021d-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="2021d-109">Üretim kullanımı için genellikle bu ayar için varsayılan değerini kabul etmiş olursunuz `false` .</span><span class="sxs-lookup"><span data-stu-id="2021d-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="2021d-110">Kod örnekleri, aşağıdaki sınıfa ve türevlerini ifade eder:</span><span class="sxs-lookup"><span data-stu-id="2021d-110">The code examples refer to the following class and variants of it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

> [!NOTE]
> <span data-ttu-id="2021d-111">System.Text.Json Visual Basic tarafından desteklenmeyen [başvuru yapıları](../../csharp/language-reference/builtin-types/struct.md#ref-struct)kullanır.</span><span class="sxs-lookup"><span data-stu-id="2021d-111">System.Text.Json uses [ref structs](../../csharp/language-reference/builtin-types/struct.md#ref-struct), which are not supported by Visual Basic.</span></span> <span data-ttu-id="2021d-112">System.Text.JsonAPI 'leri Visual Basic kullanmaya çalışırsanız, BC40000 derleme hataları alırsınız.</span><span class="sxs-lookup"><span data-stu-id="2021d-112">If you try to use System.Text.Json APIs with Visual Basic, you get BC40000 compile errors.</span></span> <span data-ttu-id="2021d-113">Hata iletisi, sorunun eski bir API olduğunu gösterir, ancak gerçek sorun `ref struct` derleyicide desteklenmeyen destek olmamasıdır.</span><span class="sxs-lookup"><span data-stu-id="2021d-113">The error message indicates that the problem is an obsolete API, but the actual issue is lack of `ref struct` support in the compiler.</span></span>

## <a name="namespaces"></a><span data-ttu-id="2021d-114">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="2021d-114">Namespaces</span></span>

<span data-ttu-id="2021d-115"><xref:System.Text.Json>Ad alanı tüm giriş noktalarını ve ana türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="2021d-115">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="2021d-116"><xref:System.Text.Json.Serialization>Ad alanı, serileştirme ve seri durumdan çıkarma ile ilgili gelişmiş senaryolar ve özelleştirme için öznitelikler ve API 'leri içerir.</span><span class="sxs-lookup"><span data-stu-id="2021d-116">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="2021d-117">Bu makalede gösterilen kod örnekleri, `using` Bu ad alanlarından biri veya her ikisi için yönergeler gerektirir:</span><span class="sxs-lookup"><span data-stu-id="2021d-117">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

> [!IMPORTANT]
> <span data-ttu-id="2021d-118"><xref:System.Runtime.Serialization>Ad alanındaki öznitelikler ' de desteklenmez `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="2021d-118">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-as-json-serialize"></a><span data-ttu-id="2021d-119">.NET nesnelerini JSON (serileştirme) olarak yazma</span><span class="sxs-lookup"><span data-stu-id="2021d-119">How to write .NET objects as JSON (serialize)</span></span>

<span data-ttu-id="2021d-120">JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="2021d-120">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="2021d-121">Aşağıdaki örnek bir dize olarak JSON oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2021d-121">The following example creates JSON as a string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::

<span data-ttu-id="2021d-122">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="2021d-122">The following example uses synchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::

<span data-ttu-id="2021d-123">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="2021d-123">The following example uses asynchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::

<span data-ttu-id="2021d-124">Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2021d-124">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="2021d-125">Öğesinin aşırı yüklemesi `Serialize()` genel bir tür parametresi alır:</span><span class="sxs-lookup"><span data-stu-id="2021d-125">An overload of `Serialize()` takes a generic type parameter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a><span data-ttu-id="2021d-126">Serileştirme örneği</span><span class="sxs-lookup"><span data-stu-id="2021d-126">Serialization example</span></span>

<span data-ttu-id="2021d-127">Aşağıda, koleksiyon türü özellikleri ve Kullanıcı tanımlı bir tür içeren örnek bir sınıf verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2021d-127">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::

> [!TIP]
> <span data-ttu-id="2021d-128">"POCO", [düz eskı clr nesnesini](https://en.wikipedia.org/wiki/Plain_old_CLR_object)temsil eder.</span><span class="sxs-lookup"><span data-stu-id="2021d-128">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="2021d-129">POCO, örneğin devralma veya öznitelikler aracılığıyla herhangi bir çerçeveye özgü türe bağımlı olmayan bir .NET türüdür.</span><span class="sxs-lookup"><span data-stu-id="2021d-129">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="2021d-130">Önceki türün bir örneğinin serileştirilmesi için JSON çıktısı aşağıdaki örnekteki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="2021d-130">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="2021d-131">JSON çıktısı küçültülmüş (boşluk, girintileme ve yeni satır karakterleri kaldırılır) varsayılan olarak:</span><span class="sxs-lookup"><span data-stu-id="2021d-131">The JSON output is minified (whitespace, indentation, and new-line characters are removed) by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="2021d-132">Aşağıdaki örnek aynı JSON 'ı gösterir, ancak biçimlendirilir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):</span><span class="sxs-lookup"><span data-stu-id="2021d-132">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

## <a name="serialize-to-utf-8"></a><span data-ttu-id="2021d-133">UTF-8 ' e serileştirme</span><span class="sxs-lookup"><span data-stu-id="2021d-133">Serialize to UTF-8</span></span>

<span data-ttu-id="2021d-134">UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="2021d-134">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::

<span data-ttu-id="2021d-135">' İ <xref:System.Text.Json.JsonSerializer.Serialize%2A> alan bir aşırı yükleme <xref:System.Text.Json.Utf8JsonWriter> de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="2021d-135">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="2021d-136">UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="2021d-136">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="2021d-137">Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="2021d-137">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="2021d-138">Serileştirme davranışı</span><span class="sxs-lookup"><span data-stu-id="2021d-138">Serialization behavior</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="2021d-139">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="2021d-139">By default, all public properties are serialized.</span></span> <span data-ttu-id="2021d-140">[Yoksayılacak özellikleri belirtebilirsiniz](system-text-json-ignore-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2021d-140">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="2021d-141">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="2021d-141">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="2021d-142">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2021d-142">By default, JSON is minified.</span></span> <span data-ttu-id="2021d-143">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2021d-143">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="2021d-144">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="2021d-144">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="2021d-145">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](system-text-json-customize-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2021d-145">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="2021d-146">Varsayılan olarak, döngüsel başvurular algılanır ve özel durumlar oluşur.</span><span class="sxs-lookup"><span data-stu-id="2021d-146">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="2021d-147">[Başvuruları koruyabilir ve döngüsel başvuruları işleyebilirsiniz](system-text-json-preserve-references.md).</span><span class="sxs-lookup"><span data-stu-id="2021d-147">You can [preserve references and handle circular references](system-text-json-preserve-references.md).</span></span>
* <span data-ttu-id="2021d-148">Varsayılan olarak, [alanlar](../../csharp/programming-guide/classes-and-structs/fields.md) yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="2021d-148">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="2021d-149">[Alanları dahil](#include-fields)edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2021d-149">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="2021d-150">System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2021d-150">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="2021d-151">Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="2021d-151">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="2021d-152">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="2021d-152">By default, all public properties are serialized.</span></span> <span data-ttu-id="2021d-153">[Yoksayılacak özellikleri belirtebilirsiniz](system-text-json-ignore-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2021d-153">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="2021d-154">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="2021d-154">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="2021d-155">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2021d-155">By default, JSON is minified.</span></span> <span data-ttu-id="2021d-156">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2021d-156">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="2021d-157">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="2021d-157">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="2021d-158">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](system-text-json-customize-properties.md).</span><span class="sxs-lookup"><span data-stu-id="2021d-158">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="2021d-159">Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="2021d-159">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="2021d-160">[Alanlar](../../csharp/programming-guide/classes-and-structs/fields.md) yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="2021d-160">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="2021d-161">Desteklenen türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2021d-161">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="2021d-162">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="2021d-162">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="2021d-163">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span><span class="sxs-lookup"><span data-stu-id="2021d-163">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="2021d-164">Tek boyutlu ve pürüzlü Diziler ( `T[][]` ).</span><span class="sxs-lookup"><span data-stu-id="2021d-164">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="2021d-165">Aşağıdaki ad alanlarından gelen koleksiyonlar ve sözlükler.</span><span class="sxs-lookup"><span data-stu-id="2021d-165">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="2021d-166">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="2021d-166">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="2021d-167">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span><span class="sxs-lookup"><span data-stu-id="2021d-167">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="2021d-168">Tek boyutlu ve pürüzlü Diziler ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="2021d-168">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="2021d-169">`Dictionary<string,TValue>` Burada `TValue` , `object` `JsonElement` veya bir poco.</span><span class="sxs-lookup"><span data-stu-id="2021d-169">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="2021d-170">Aşağıdaki ad alanlarından Koleksiyonlar.</span><span class="sxs-lookup"><span data-stu-id="2021d-170">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="2021d-171">Ek türleri işlemek veya yerleşik dönüştürücüler tarafından desteklenmeyen işlevler sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="2021d-171">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-as-net-objects-deserialize"></a><span data-ttu-id="2021d-172">.NET nesneleri olarak JSON okuma (serisini kaldırma)</span><span class="sxs-lookup"><span data-stu-id="2021d-172">How to read JSON as .NET objects (deserialize)</span></span>

<span data-ttu-id="2021d-173">Bir dizeden veya dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="2021d-173">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="2021d-174">Aşağıdaki örnek, bir dizeden JSON okur ve `WeatherForecastWithPOCOs` daha önce [serileştirme örneği](#serialization-example)için gösterilen sınıfının bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="2021d-174">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::

<span data-ttu-id="2021d-175">Zaman uyumlu kod kullanarak bir dosyadan seri durumdan çıkarmak için, aşağıdaki örnekte gösterildiği gibi dosyayı bir dizeye okuyun:</span><span class="sxs-lookup"><span data-stu-id="2021d-175">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::

<span data-ttu-id="2021d-176">Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için yöntemini çağırın <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> :</span><span class="sxs-lookup"><span data-stu-id="2021d-176">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::

> [!TIP]
> <span data-ttu-id="2021d-177">Seri durumdan çıkarmak istediğiniz JSON varsa ve bunun serisini kaldırmak için sınıfınız yoksa, Visual Studio 2019, ihtiyacınız olan sınıfı otomatik olarak oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="2021d-177">If you have JSON that you want to deserialize, and you don't have the class to deserialize it into, Visual Studio 2019 can automatically generate the class you need:</span></span>
>
> 1. <span data-ttu-id="2021d-178">Seri durumdan çıkarmak için gereken JSON 'ı kopyalayın.</span><span class="sxs-lookup"><span data-stu-id="2021d-178">Copy the JSON that you need to deserialize.</span></span>
> 1. <span data-ttu-id="2021d-179">Bir sınıf dosyası oluşturun ve şablon kodunu silin.</span><span class="sxs-lookup"><span data-stu-id="2021d-179">Create a class file and delete the template code.</span></span>
> 1. <span data-ttu-id="2021d-180">**Düzenleme**  >  **Yapıştır Özel**  >  **JSON 'ı sınıflar olarak Yapıştır**' ı seçin.</span><span class="sxs-lookup"><span data-stu-id="2021d-180">Choose **Edit** > **Paste Special** > **Paste JSON as Classes**.</span></span>
>
> <span data-ttu-id="2021d-181">Sonuç, seri durumdan çıkarma hedefi için kullanabileceğiniz bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="2021d-181">The result is a class that you can use for your deserialization target.</span></span>

## <a name="deserialize-from-utf-8"></a><span data-ttu-id="2021d-182">UTF-8 ' den serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="2021d-182">Deserialize from UTF-8</span></span>

<span data-ttu-id="2021d-183">UTF-8 ' den seri durumdan çıkarmak için, <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> `ReadOnlySpan<byte>` `Utf8JsonReader` Aşağıdaki örneklerde gösterildiği gibi bir veya içeren bir aşırı yükleme çağırın.</span><span class="sxs-lookup"><span data-stu-id="2021d-183">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `ReadOnlySpan<byte>` or a `Utf8JsonReader`, as shown in the following examples.</span></span> <span data-ttu-id="2021d-184">Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="2021d-184">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::

## <a name="deserialization-behavior"></a><span data-ttu-id="2021d-185">Seri durumdan çıkarma davranışı</span><span class="sxs-lookup"><span data-stu-id="2021d-185">Deserialization behavior</span></span>

<span data-ttu-id="2021d-186">JSON serisi kaldırılırken aşağıdaki davranışlar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="2021d-186">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="2021d-187">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="2021d-187">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="2021d-188">[Büyük/küçük harf duyarlı belirtebilirsiniz](system-text-json-character-casing.md).</span><span class="sxs-lookup"><span data-stu-id="2021d-188">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span>
* <span data-ttu-id="2021d-189">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="2021d-189">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="2021d-190">Ortak olmayan oluşturucular seri hale getirici tarafından yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="2021d-190">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="2021d-191">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2021d-191">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="2021d-192">Bkz. [değişmez türler ve kayıtlar](system-text-json-immutability.md).</span><span class="sxs-lookup"><span data-stu-id="2021d-192">See [Immutable types and Records](system-text-json-immutability.md).</span></span>
* <span data-ttu-id="2021d-193">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2021d-193">By default, enums are supported as numbers.</span></span> <span data-ttu-id="2021d-194">[Enum adlarını dizeler olarak seri hale](system-text-json-customize-properties.md#enums-as-strings)getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2021d-194">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="2021d-195">Varsayılan olarak, alanlar yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="2021d-195">By default, fields are ignored.</span></span> <span data-ttu-id="2021d-196">[Alanları dahil](#include-fields)edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2021d-196">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="2021d-197">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2021d-197">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="2021d-198">[Yorumlara ve sondaki virgüllerin bulunmasına izin](system-text-json-invalid-json.md)verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2021d-198">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="2021d-199">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2021d-199">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="2021d-200">System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2021d-200">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="2021d-201">Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="2021d-201">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="2021d-202">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="2021d-202">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="2021d-203">[Büyük/küçük harf duyarlı belirtebilirsiniz](system-text-json-character-casing.md).</span><span class="sxs-lookup"><span data-stu-id="2021d-203">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span> <span data-ttu-id="2021d-204">ASP.NET Core uygulamalar [Varsayılan olarak büyük/küçük harf duyarlı belirtir](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="2021d-204">ASP.NET Core apps [specify case-insensitivity by default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="2021d-205">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="2021d-205">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="2021d-206">Seri durumdan çıkarma için genel, iç veya özel olabilen parametresiz bir Oluşturucu kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2021d-206">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="2021d-207">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="2021d-207">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="2021d-208">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="2021d-208">By default, enums are supported as numbers.</span></span> <span data-ttu-id="2021d-209">[Enum adlarını dizeler olarak seri hale](system-text-json-customize-properties.md#enums-as-strings)getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2021d-209">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="2021d-210">Alanlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="2021d-210">Fields aren't supported.</span></span>
* <span data-ttu-id="2021d-211">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2021d-211">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="2021d-212">[Yorumlara ve sondaki virgüllerin bulunmasına izin](system-text-json-invalid-json.md)verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2021d-212">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="2021d-213">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="2021d-213">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="2021d-214">System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır.</span><span class="sxs-lookup"><span data-stu-id="2021d-214">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="2021d-215">Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="2021d-215">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="2021d-216">Yerleşik dönüştürücüler tarafından desteklenmeyen işlevselliği sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="2021d-216">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="2021d-217">Biçimlendirilen JSON 'a serileştirme</span><span class="sxs-lookup"><span data-stu-id="2021d-217">Serialize to formatted JSON</span></span>

<span data-ttu-id="2021d-218">JSON çıkışını gerçekten yazdırmak için şu <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> şekilde ayarlayın `true` :</span><span class="sxs-lookup"><span data-stu-id="2021d-218">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::

<span data-ttu-id="2021d-219">Aşağıda, seri hale getirilebilir ve düzgün şekilde yazdırılan JSON çıkışının örnek bir türü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="2021d-219">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="2021d-220">`JsonSerializerOptions`Aynı seçeneklerle tekrar tekrar kullanırsanız, `JsonSerializerOptions` her kullandığınızda yeni bir örnek oluşturmayın.</span><span class="sxs-lookup"><span data-stu-id="2021d-220">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="2021d-221">Her çağrı için aynı örneği yeniden kullanın.</span><span class="sxs-lookup"><span data-stu-id="2021d-221">Reuse the same instance for every call.</span></span> <span data-ttu-id="2021d-222">Daha fazla bilgi için bkz. [JsonSerializerOptions örneklerini yeniden kullanma](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span><span class="sxs-lookup"><span data-stu-id="2021d-222">For more information, see [Reuse JsonSerializerOptions instances](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).</span></span>

## <a name="include-fields"></a><span data-ttu-id="2021d-223">Dahil etme alanları</span><span class="sxs-lookup"><span data-stu-id="2021d-223">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="2021d-224"><xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, seri hale getirilirken veya seri durumdan çıkarılırken alanları dahil etmek için genel ayarını veya [[jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliğini kullanın:</span><span class="sxs-lookup"><span data-stu-id="2021d-224">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::

<span data-ttu-id="2021d-225">Salt okuma alanlarını yok saymak için <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> genel ayarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="2021d-225">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="2021d-226">Alanlar System.Text.Json .NET Core 3,1 ' de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="2021d-226">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="2021d-227">[Özel dönüştürücüler](system-text-json-converters-how-to.md) , bu işlevselliği sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="2021d-227">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="2021d-228">HttpClient ve HttpContent genişletme yöntemleri</span><span class="sxs-lookup"><span data-stu-id="2021d-228">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="2021d-229">JSON yüklerini ağdan serileştirmek ve serisini kaldırma yaygın işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="2021d-229">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="2021d-230">[HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) ve [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) üzerindeki genişletme yöntemleri, bu işlemleri tek bir kod satırında yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="2021d-230">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="2021d-231">Bu uzantı yöntemleri, [JsonSerializerOptions için Web varsayılanlarını](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)kullanır.</span><span class="sxs-lookup"><span data-stu-id="2021d-231">These extension methods use [web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="2021d-232">Aşağıdaki örnek, ve kullanımını göstermektedir <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="2021d-232">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::

<span data-ttu-id="2021d-233">Ayrıca, HttpContent için uzantı yöntemleri de vardır System.Text.Json . [](xref:System.Net.Http.Json.HttpContentJsonExtensions)</span><span class="sxs-lookup"><span data-stu-id="2021d-233">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="2021d-234">Ve ' de uzantı yöntemleri `HttpClient` `HttpContent` System.Text.Json .NET Core 3,1 ' de kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2021d-234">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="2021d-235">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2021d-235">See also</span></span>

* [<span data-ttu-id="2021d-236">System.Text.Json bakýþ</span><span class="sxs-lookup"><span data-stu-id="2021d-236">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="2021d-237">JsonSerializerOptions örneklerinin örneğini oluşturma</span><span class="sxs-lookup"><span data-stu-id="2021d-237">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="2021d-238">Büyük/küçük harf duyarlı eşlemeyi etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="2021d-238">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="2021d-239">Özellik adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2021d-239">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="2021d-240">Özellikleri yoksayma</span><span class="sxs-lookup"><span data-stu-id="2021d-240">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="2021d-241">Geçersiz JSON’a izin verme</span><span class="sxs-lookup"><span data-stu-id="2021d-241">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="2021d-242">Sap taşması JSON’ı</span><span class="sxs-lookup"><span data-stu-id="2021d-242">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="2021d-243">Başvuruları koruma</span><span class="sxs-lookup"><span data-stu-id="2021d-243">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="2021d-244">Sabit türler ve genel olmayan erişimciler</span><span class="sxs-lookup"><span data-stu-id="2021d-244">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="2021d-245">Polimorfik serileştirme</span><span class="sxs-lookup"><span data-stu-id="2021d-245">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="2021d-246">' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json</span><span class="sxs-lookup"><span data-stu-id="2021d-246">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="2021d-247">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="2021d-247">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="2021d-248">Özel serileştiriciler ve seri hale getiriciler yazma</span><span class="sxs-lookup"><span data-stu-id="2021d-248">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="2021d-249">JSON serileştirme için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="2021d-249">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="2021d-250">DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="2021d-250">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="2021d-251">[System.Text.Json API başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="2021d-251">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="2021d-252">[System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="2021d-252">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
