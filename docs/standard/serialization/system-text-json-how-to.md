---
title: .NET kullanarak C# JSON serileştirmek ve serisini kaldırma
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 047d5b5c6fa339089d2054eb6bfe8b3066c1d00c
ms.sourcegitcommit: dfad244ba549702b649bfef3bb057e33f24a8fb2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2020
ms.locfileid: "75904653"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="5188f-102">.NET içinde JSON ve seri hale getirme (sıralama ve kaldırma)</span><span class="sxs-lookup"><span data-stu-id="5188f-102">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="5188f-103">Bu makalede, JavaScript Nesne Gösterimi (JSON) içinde ve içinde seri hale getirmek ve seri durumdan çıkarmak için <xref:System.Text.Json> ad alanının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5188f-103">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="5188f-104">Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="5188f-104">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="5188f-105">Seri hale getirme örnek kodunun çoğu, JSON 'ı (örneğin girintileme ve insanlar okunabilirlik için boşluk) `true` <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> belirler.</span><span class="sxs-lookup"><span data-stu-id="5188f-105">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="5188f-106">Üretim kullanımı için genellikle bu ayar için `false` varsayılan değerini kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="5188f-106">For production use, you would typically accept the default value of `false` for this setting.</span></span>

## <a name="namespaces"></a><span data-ttu-id="5188f-107">{1&gt;Ad alanları&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5188f-107">Namespaces</span></span>

<span data-ttu-id="5188f-108"><xref:System.Text.Json> ad alanı tüm giriş noktalarını ve ana türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="5188f-108">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="5188f-109"><xref:System.Text.Json.Serialization> ad alanı, serileştirme ve seri durumdan çıkarma için özel gelişmiş senaryolar ve özelleştirmeler için öznitelikler ve API 'Leri içerir.</span><span class="sxs-lookup"><span data-stu-id="5188f-109">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="5188f-110">Bu makalede gösterilen kod örnekleri, bu ad alanlarından biri veya her ikisi için `using` yönergeler gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5188f-110">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="5188f-111"><xref:System.Runtime.Serialization> ad alanındaki öznitelikler Şu anda `System.Text.Json`desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5188f-111">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="5188f-112">.NET nesnelerini JSON 'a yazma (serileştirme)</span><span class="sxs-lookup"><span data-stu-id="5188f-112">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="5188f-113">JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="5188f-113">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="5188f-114">Aşağıdaki örnek bir dize olarak JSON oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5188f-114">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="5188f-115">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="5188f-115">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="5188f-116">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="5188f-116">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="5188f-117">Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5188f-117">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="5188f-118">`Serialize()` aşırı yüklemesi genel bir tür parametresi alır:</span><span class="sxs-lookup"><span data-stu-id="5188f-118">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="5188f-119">Serileştirme örneği</span><span class="sxs-lookup"><span data-stu-id="5188f-119">Serialization example</span></span>

<span data-ttu-id="5188f-120">Aşağıda, koleksiyonları ve iç içe yerleştirilmiş bir sınıfı içeren örnek bir sınıf verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-120">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="5188f-121">Önceki türün bir örneğinin serileştirilmesi için JSON çıktısı aşağıdaki örnekteki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="5188f-121">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="5188f-122">JSON çıktısı varsayılan olarak Mini olarak belirlenir:</span><span class="sxs-lookup"><span data-stu-id="5188f-122">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="5188f-123">Aşağıdaki örnek, biçimlendirilen aynı JSON 'ı gösterir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):</span><span class="sxs-lookup"><span data-stu-id="5188f-123">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="5188f-124">UTF-8 ' e serileştirme</span><span class="sxs-lookup"><span data-stu-id="5188f-124">Serialize to UTF-8</span></span>

<span data-ttu-id="5188f-125">UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemi çağırın:</span><span class="sxs-lookup"><span data-stu-id="5188f-125">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="5188f-126"><xref:System.Text.Json.Utf8JsonWriter> alan <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemesi de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="5188f-126">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="5188f-127">UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="5188f-127">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="5188f-128">Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="5188f-128">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="5188f-129">Serileştirme davranışı</span><span class="sxs-lookup"><span data-stu-id="5188f-129">Serialization behavior</span></span>

* <span data-ttu-id="5188f-130">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-130">By default, all public properties are serialized.</span></span> <span data-ttu-id="5188f-131">[Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="5188f-131">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="5188f-132">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="5188f-132">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="5188f-133">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="5188f-133">By default, JSON is minified.</span></span> <span data-ttu-id="5188f-134">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5188f-134">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="5188f-135">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="5188f-135">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="5188f-136">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="5188f-136">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="5188f-137">Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="5188f-137">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="5188f-138">Şu anda, alanlar hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="5188f-138">Currently, fields are excluded.</span></span>

<span data-ttu-id="5188f-139">Desteklenen türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="5188f-139">Supported types include:</span></span>

* <span data-ttu-id="5188f-140">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="5188f-140">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="5188f-141">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="5188f-141">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="5188f-142">Tek boyutlu ve pürüzlü Diziler (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="5188f-142">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="5188f-143">`Dictionary<string,TValue>` `TValue` `object`, `JsonElement`veya bir POCO.</span><span class="sxs-lookup"><span data-stu-id="5188f-143">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="5188f-144">Aşağıdaki ad alanlarından Koleksiyonlar.</span><span class="sxs-lookup"><span data-stu-id="5188f-144">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="5188f-145">Ek türleri işlemek veya yerleşik dönüştürücüler tarafından desteklenmeyen işlevler sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="5188f-145">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="5188f-146">JSON 'ı .NET Objects 'e okuma (serisini kaldırma)</span><span class="sxs-lookup"><span data-stu-id="5188f-146">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="5188f-147">Bir dizeden veya dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="5188f-147">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="5188f-148">Aşağıdaki örnek, bir dizeden JSON okur ve daha önce [serileştirme örneği](#serialization-example)için gösterilen `WeatherForecast` sınıfının bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5188f-148">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="5188f-149">Zaman uyumlu kod kullanarak bir dosyadan seri durumdan çıkarmak için, aşağıdaki örnekte gösterildiği gibi dosyayı bir dizeye okuyun:</span><span class="sxs-lookup"><span data-stu-id="5188f-149">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="5188f-150">Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> yöntemi çağırın:</span><span class="sxs-lookup"><span data-stu-id="5188f-150">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="5188f-151">UTF-8 ' den serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="5188f-151">Deserialize from UTF-8</span></span>

<span data-ttu-id="5188f-152">UTF-8 ' den seri durumdan çıkarmak için, aşağıdaki örneklerde gösterildiği gibi `Utf8JsonReader` veya `ReadOnlySpan<byte>`alan <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> aşırı yüklemeyi çağırın.</span><span class="sxs-lookup"><span data-stu-id="5188f-152">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="5188f-153">Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="5188f-153">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="5188f-154">Seri durumdan çıkarma davranışı</span><span class="sxs-lookup"><span data-stu-id="5188f-154">Deserialization behavior</span></span>

* <span data-ttu-id="5188f-155">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="5188f-155">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="5188f-156">[Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="5188f-156">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="5188f-157">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="5188f-157">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="5188f-158">Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5188f-158">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="5188f-159">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="5188f-159">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="5188f-160">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="5188f-160">By default, enums are supported as numbers.</span></span> <span data-ttu-id="5188f-161">[Enum adlarını dizeler olarak seri hale](#enums-as-strings)getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5188f-161">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="5188f-162">Alanlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5188f-162">Fields aren't supported.</span></span>
* <span data-ttu-id="5188f-163">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5188f-163">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="5188f-164">[Yorumlara ve sondaki virgüllerin bulunmasına izin](#allow-comments-and-trailing-commas)verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5188f-164">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="5188f-165">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5188f-165">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="5188f-166">Yerleşik dönüştürücüler tarafından desteklenmeyen işlevselliği sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="5188f-166">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="5188f-167">Biçimlendirilen JSON 'a serileştirme</span><span class="sxs-lookup"><span data-stu-id="5188f-167">Serialize to formatted JSON</span></span>

<span data-ttu-id="5188f-168">JSON çıkışını gerçekten yazdırmak için <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true`olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5188f-168">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="5188f-169">Aşağıda, seri hale getirilebilir ve düzgün şekilde yazdırılan JSON çıkışının örnek bir türü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-169">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="5188f-170">JSON adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5188f-170">Customize JSON names and values</span></span>

<span data-ttu-id="5188f-171">Varsayılan olarak, özellik adları ve sözlük anahtarları, büyük/küçük harf gibi JSON çıktısında değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="5188f-171">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="5188f-172">Sabit listesi değerleri sayı olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-172">Enum values are represented as numbers.</span></span> <span data-ttu-id="5188f-173">Bu bölümde nasıl yapılacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="5188f-173">This section explains how to:</span></span>

* [<span data-ttu-id="5188f-174">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5188f-174">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="5188f-175">Tüm özellik adlarını ortası durumuna Dönüştür</span><span class="sxs-lookup"><span data-stu-id="5188f-175">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="5188f-176">Özel özellik adlandırma ilkesi uygulama</span><span class="sxs-lookup"><span data-stu-id="5188f-176">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="5188f-177">Sözlük anahtarlarını ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="5188f-177">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="5188f-178">Numaralandırmaları dizelere ve ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="5188f-178">Convert enums to strings and camel case</span></span>](#enums-as-strings) 

<span data-ttu-id="5188f-179">JSON özellik adlarını ve değerlerini özel olarak işleme gerektiren diğer senaryolar için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="5188f-179">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="5188f-180">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5188f-180">Customize individual property names</span></span>

<span data-ttu-id="5188f-181">Ayrı özelliklerin adını ayarlamak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5188f-181">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="5188f-182">Serileştirme ve sonuç JSON için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-182">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="5188f-183">Bu öznitelik tarafından ayarlanan özellik adı:</span><span class="sxs-lookup"><span data-stu-id="5188f-183">The property name set by this attribute:</span></span>

* <span data-ttu-id="5188f-184">Serileştirme ve seri durumundan çıkarma için her iki yönde de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5188f-184">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="5188f-185">Özellik adlandırma ilkelerine göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="5188f-185">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="5188f-186">Tüm JSON Özellik adları için ortası Case kullanın</span><span class="sxs-lookup"><span data-stu-id="5188f-186">Use camel case for all JSON property names</span></span>

<span data-ttu-id="5188f-187">Tüm JSON Özellik adları için ortası durumunu kullanmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase`olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5188f-187">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="5188f-188">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-188">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="5188f-189">Ortası durum özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="5188f-189">The camel case property naming policy:</span></span>

* <span data-ttu-id="5188f-190">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5188f-190">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="5188f-191">`[JsonPropertyName]` öznitelikleri tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="5188f-191">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="5188f-192">Bu, örnekte `Wind` JSON özelliği adının ortası durum olmadığı durumdur.</span><span class="sxs-lookup"><span data-stu-id="5188f-192">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="5188f-193">Özel bir JSON Özellik adlandırma ilkesi kullanma</span><span class="sxs-lookup"><span data-stu-id="5188f-193">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="5188f-194">Özel bir JSON Özellik adlandırma ilkesi kullanmak için, <xref:System.Text.Json.JsonNamingPolicy> türeten bir sınıf oluşturun ve aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> yöntemini geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="5188f-194">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="5188f-195">Sonra <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> özelliğini, adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5188f-195">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="5188f-196">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-196">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="5188f-197">JSON özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="5188f-197">The JSON property naming policy:</span></span>

* <span data-ttu-id="5188f-198">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5188f-198">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="5188f-199">`[JsonPropertyName]` öznitelikleri tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="5188f-199">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="5188f-200">Bu, örnekte `Wind` JSON özelliği adının büyük harfle değil.</span><span class="sxs-lookup"><span data-stu-id="5188f-200">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="5188f-201">Camel durum sözlüğü anahtarları</span><span class="sxs-lookup"><span data-stu-id="5188f-201">Camel case dictionary keys</span></span>

<span data-ttu-id="5188f-202">Seri hale getirilecek bir nesnenin özelliği `Dictionary<string,TValue>`türünde ise, `string` anahtarlar ortası duruma dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-202">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="5188f-203">Bunu yapmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase`olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5188f-203">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="5188f-204">Anahtar-değer çiftleri `"ColdMinTemp", 20` olan `TemperatureRanges` adlı bir sözlükten bir nesneyi serileştirmek ve `"HotMinTemp", 40` aşağıdaki örnekte olduğu gibi JSON çıktısına neden olur:</span><span class="sxs-lookup"><span data-stu-id="5188f-204">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="5188f-205">Sözlük anahtarları için ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5188f-205">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="5188f-206">Bir sözlüğün serisini kaldırırsanız, `DictionaryKeyPolicy`için `JsonNamingPolicy.CamelCase` belirtseniz bile anahtarlar JSON dosyasıyla eşleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="5188f-206">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="5188f-207">Dizeler dize olarak numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="5188f-207">Enums as strings</span></span>

<span data-ttu-id="5188f-208">Varsayılan olarak, numaralandırmalar sayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-208">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="5188f-209">Enum adlarını dizeler olarak seri hale getirmek için <xref:System.Text.Json.Serialization.JsonStringEnumConverter>kullanın.</span><span class="sxs-lookup"><span data-stu-id="5188f-209">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="5188f-210">Örneğin, bir sabit listesi olan aşağıdaki sınıfı seri hale getirmeniz gerektiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="5188f-210">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="5188f-211">Özet `Hot`, varsayılan olarak seri hale getirilmiş JSON sayısal değeri 3 ' tir:</span><span class="sxs-lookup"><span data-stu-id="5188f-211">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="5188f-212">Aşağıdaki örnek kod, sayısal değerler yerine enum adlarını seri hale getirir ve adları ortası örneğine dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="5188f-212">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="5188f-213">Elde edilen JSON aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="5188f-213">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="5188f-214">Aşağıdaki örnekte gösterildiği gibi, sabit listesi dize adları da seri durumdan çıkarılmış olabilir:</span><span class="sxs-lookup"><span data-stu-id="5188f-214">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="5188f-215">Özellikleri serileştirme dışında tut</span><span class="sxs-lookup"><span data-stu-id="5188f-215">Exclude properties from serialization</span></span>

<span data-ttu-id="5188f-216">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-216">By default, all public properties are serialized.</span></span> <span data-ttu-id="5188f-217">Bir kısmının JSON çıktısında görünmesini istemiyorsanız, birkaç seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="5188f-217">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="5188f-218">Bu bölümde nasıl hariç tutulacak açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="5188f-218">This section explains how to exclude:</span></span>

* [<span data-ttu-id="5188f-219">Bireysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="5188f-219">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="5188f-220">Tüm salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="5188f-220">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="5188f-221">Tüm null değerli özellikler</span><span class="sxs-lookup"><span data-stu-id="5188f-221">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="5188f-222">Bireysel özellikleri Dışla</span><span class="sxs-lookup"><span data-stu-id="5188f-222">Exclude individual properties</span></span>

<span data-ttu-id="5188f-223">Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="5188f-223">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="5188f-224">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-224">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="5188f-225">Tüm salt okuma özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="5188f-225">Exclude all read-only properties</span></span>

<span data-ttu-id="5188f-226">Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="5188f-226">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="5188f-227">Tüm salt okuma özelliklerini hariç tutmak için, aşağıdaki örnekte gösterildiği gibi, <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> `true`olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5188f-227">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="5188f-228">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-228">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="5188f-229">Bu seçenek yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5188f-229">This option applies only to serialization.</span></span> <span data-ttu-id="5188f-230">Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="5188f-230">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="5188f-231">Tüm null değer özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="5188f-231">Exclude all null value properties</span></span>

<span data-ttu-id="5188f-232">Tüm null değer özelliklerini dışlamak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> özelliğini `true`olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5188f-232">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="5188f-233">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-233">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="5188f-234">Özellik</span><span class="sxs-lookup"><span data-stu-id="5188f-234">Property</span></span> |<span data-ttu-id="5188f-235">Değer</span><span class="sxs-lookup"><span data-stu-id="5188f-235">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="5188f-236">Tarih</span><span class="sxs-lookup"><span data-stu-id="5188f-236">Date</span></span>    | <span data-ttu-id="5188f-237">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="5188f-237">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="5188f-238">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="5188f-238">TemperatureCelsius</span></span>| <span data-ttu-id="5188f-239">25</span><span class="sxs-lookup"><span data-stu-id="5188f-239">25</span></span> |
| <span data-ttu-id="5188f-240">Özet</span><span class="sxs-lookup"><span data-stu-id="5188f-240">Summary</span></span>| <span data-ttu-id="5188f-241">{1&gt;null&lt;1}</span><span class="sxs-lookup"><span data-stu-id="5188f-241">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="5188f-242">Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="5188f-242">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="5188f-243">Seri durumdan çıkarma üzerindeki etkisi hakkında daha fazla bilgi için bkz. [serisi kaldırılırken null değeri yoksay](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="5188f-243">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="5188f-244">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="5188f-244">Customize character encoding</span></span>

<span data-ttu-id="5188f-245">Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="5188f-245">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="5188f-246">Diğer bir deyişle, `xxxx` karakterin Unicode kodu olduğu `\uxxxx` bunların yerini alır.</span><span class="sxs-lookup"><span data-stu-id="5188f-246">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="5188f-247">Örneğin, `Summary` özelliği Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesnesi şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="5188f-247">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="5188f-248">Dil karakter kümelerini serileştirme</span><span class="sxs-lookup"><span data-stu-id="5188f-248">Serialize language character sets</span></span>

<span data-ttu-id="5188f-249">Bir veya daha fazla dilin karakter kümesini kaçış olmadan seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi, bir <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>örneği oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin:</span><span class="sxs-lookup"><span data-stu-id="5188f-249">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="5188f-250">Bu kod, Kiril veya Yunan karakterlerinden kaçış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="5188f-250">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="5188f-251">`Summary` özelliği Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesnesi şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="5188f-251">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="5188f-252">Tüm dil kümelerini kaçış olmadan seri hale getirmek için <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>kullanın.</span><span class="sxs-lookup"><span data-stu-id="5188f-252">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="5188f-253">Belirli karakterleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="5188f-253">Serialize specific characters</span></span>

<span data-ttu-id="5188f-254">Diğer bir seçenek de, kaçırılmadan, izin vermek istediğiniz tek tek karakterleri belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="5188f-254">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="5188f-255">Aşağıdaki örnek, жарко 'in yalnızca ilk iki karakterini seri hale getirir:</span><span class="sxs-lookup"><span data-stu-id="5188f-255">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="5188f-256">Yukarıdaki kod tarafından üretilen JSON örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-256">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="5188f-257">Tüm karakterleri seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="5188f-257">Serialize all characters</span></span>

<span data-ttu-id="5188f-258">Kaçı en aza indirmek için aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="5188f-258">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="5188f-259">Varsayılan kodlayıcıyla karşılaştırıldığında `UnsafeRelaxedJsonEscaping` kodlayıcı, karakterlerin kaçışsız geçmesine izin verme konusunda daha fazla izne sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5188f-259">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="5188f-260">`<`, `>`, `&`ve `'`gibi HTML 'ye duyarlı karakterlerin kaçış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="5188f-260">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="5188f-261">Bu, XSS veya bilgi açıklama saldırılarına karşı ek derinlemesine savunma korumaları sunmaz, örneğin, *karakter*kümesinde istemci ve sunucu disagreeing neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-261">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="5188f-262">Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="5188f-262">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="5188f-263">Örneğin, sunucu yanıt üst bilgisini `Content-Type: application/json; charset=utf-8`gönderiyorsa onu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5188f-263">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="5188f-264">Ham `UnsafeRelaxedJsonEscaping` çıkışının bir HTML sayfasına veya bir `<script>` öğesine yayılmasın.</span><span class="sxs-lookup"><span data-stu-id="5188f-264">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="5188f-265">Türetilmiş sınıfların serileştirme özellikleri</span><span class="sxs-lookup"><span data-stu-id="5188f-265">Serialize properties of derived classes</span></span>

<span data-ttu-id="5188f-266">Çok biçimli bir tür hiyerarşisinin serileştirilmesi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="5188f-266">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="5188f-267">Örneğin, bir özellik bir arabirim ya da soyut sınıf olarak tanımlanmışsa, çalışma zamanı türü ek özelliklere sahip olsa bile yalnızca arabirim veya soyut sınıf üzerinde tanımlanan özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-267">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="5188f-268">Bu davranışın istisnaları, bu bölümde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5188f-268">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="5188f-269">Örneğin, bir `WeatherForecast` sınıfa ve `WeatherForecastDerived`türetilmiş bir sınıfa sahip olduğunuzu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="5188f-269">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="5188f-270">Ve derleme zamanında `Serialize` yönteminin tür bağımsız değişkeninin `WeatherForecast`olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="5188f-270">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="5188f-271">Bu senaryoda, `weatherForecast` nesnesi gerçekten bir `WeatherForecastDerived` nesnesi olsa bile `WindSpeed` özelliği serileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="5188f-271">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="5188f-272">Yalnızca temel sınıf özellikleri serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="5188f-272">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="5188f-273">Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5188f-273">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="5188f-274">Yukarıdaki örnekteki türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="5188f-274">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="5188f-275">Çalışma zamanında türü belirtmenize izin veren <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="5188f-275">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="5188f-276">`object`olarak seri hale getirilecek nesneyi bildirin.</span><span class="sxs-lookup"><span data-stu-id="5188f-276">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="5188f-277">Yukarıdaki örnek senaryoda, her iki yaklaşım da `WindSpeed` özelliğin JSON çıktısına dahil olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="5188f-277">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="5188f-278">Bu yaklaşımlar yalnızca kök nesnenin seri hale getirilmesi için, bu kök nesnenin özellikleri için değil, polimorfik serileştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="5188f-278">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span> 

<span data-ttu-id="5188f-279">`object`tür olarak tanımlarsanız alt düzey nesneler için polimorfik serileştirme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5188f-279">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="5188f-280">Örneğin, `WeatherForecast` sınıfınızın, tür `WeatherForecast` veya `object`olarak tanımlanabilen `PreviousForecast` adında bir özelliği olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="5188f-280">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="5188f-281">`PreviousForecast` özelliği bir `WeatherForecastDerived`örneği içeriyorsa:</span><span class="sxs-lookup"><span data-stu-id="5188f-281">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="5188f-282">Seri hale getirme `WeatherForecastWithPrevious` JSON çıktısı `WindSpeed`**içermez** .</span><span class="sxs-lookup"><span data-stu-id="5188f-282">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="5188f-283">Seri hale getirme `WeatherForecastWithPreviousAsObject` JSON çıktısı `WindSpeed`**içerir** .</span><span class="sxs-lookup"><span data-stu-id="5188f-283">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="5188f-284">`WeatherForecastWithPreviousAsObject`seri hale getirmek için `Serialize<object>` veya `GetType` çağırmak gerekmez, çünkü kök nesne türetilmiş bir türde olabilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-284">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="5188f-285">Aşağıdaki kod örneği `Serialize<object>` veya `GetType`çağırmaz:</span><span class="sxs-lookup"><span data-stu-id="5188f-285">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="5188f-286">Yukarıdaki kod `WeatherForecastWithPreviousAsObject`doğru şekilde serileştirir:</span><span class="sxs-lookup"><span data-stu-id="5188f-286">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="5188f-287">Özellikleri `object` olarak tanımlamaya yönelik aynı yaklaşım, arabirimleriyle birlikte çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5188f-287">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="5188f-288">Aşağıdaki arabirime ve uygulamaya sahip olduğunuzu ve uygulama örnekleri içeren özelliklerle bir sınıfı seri hale getirmek istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="5188f-288">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

<span data-ttu-id="5188f-289">Bir `Forecasts`örneğini serileştirçalıştığınızda, `Tuesday` `object`olarak tanımlandığından yalnızca `Tuesday` `WindSpeed` özelliğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="5188f-289">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="5188f-290">Aşağıdaki örnek, önceki koddan elde edilen JSON 'u göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5188f-290">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="5188f-291">Polimorfik **serileştirme**hakkında daha fazla bilgi edinmek ve **serisini kaldırma**hakkında bilgi Için, bkz. [Newtonsoft. JSON 'Dan System. Text. JSON 'a geçiş](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="5188f-291">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="5188f-292">Yorumlara ve sondaki virgülleri izin ver</span><span class="sxs-lookup"><span data-stu-id="5188f-292">Allow comments and trailing commas</span></span>

<span data-ttu-id="5188f-293">Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="5188f-293">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="5188f-294">JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini `JsonCommentHandling.Skip`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5188f-294">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="5188f-295">Sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="5188f-295">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="5188f-296">Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="5188f-296">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="5188f-297">Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-297">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="5188f-298">Büyük/küçük harfe duyarsız Özellik eşleştirme</span><span class="sxs-lookup"><span data-stu-id="5188f-298">Case-insensitive property matching</span></span>

<span data-ttu-id="5188f-299">Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar.</span><span class="sxs-lookup"><span data-stu-id="5188f-299">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="5188f-300">Bu davranışı değiştirmek için <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> `true`olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5188f-300">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="5188f-301">Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5188f-301">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="5188f-302">Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-302">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="5188f-303">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="5188f-303">Handle overflow JSON</span></span>

<span data-ttu-id="5188f-304">Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5188f-304">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="5188f-305">Örneğin, hedef türünün bu olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="5188f-305">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="5188f-306">Ve seri durumdan çıkarılacak JSON şu şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="5188f-306">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="5188f-307">Gösterilen türde gösterilen JSON serisini kaldırırsanız, `DatesAvailable` ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor.</span><span class="sxs-lookup"><span data-stu-id="5188f-307">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="5188f-308">Bu özellikler gibi ek verileri yakalamak için, `Dictionary<string,object>` veya `Dictionary<string,JsonElement>`türünde bir özelliğe [Jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini uygulayın:</span><span class="sxs-lookup"><span data-stu-id="5188f-308">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="5188f-309">Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veriler `ExtensionData` özelliğinin anahtar-değer çiftleri haline gelir:</span><span class="sxs-lookup"><span data-stu-id="5188f-309">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="5188f-310">Özellik</span><span class="sxs-lookup"><span data-stu-id="5188f-310">Property</span></span> |<span data-ttu-id="5188f-311">Değer</span><span class="sxs-lookup"><span data-stu-id="5188f-311">Value</span></span>  |<span data-ttu-id="5188f-312">Notlar</span><span class="sxs-lookup"><span data-stu-id="5188f-312">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="5188f-313">Tarih</span><span class="sxs-lookup"><span data-stu-id="5188f-313">Date</span></span>    | <span data-ttu-id="5188f-314">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="5188f-314">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="5188f-315">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="5188f-315">TemperatureCelsius</span></span>| <span data-ttu-id="5188f-316">0</span><span class="sxs-lookup"><span data-stu-id="5188f-316">0</span></span> | <span data-ttu-id="5188f-317">Büyük/küçük harfe duyarlı uyuşmazlık (JSON içinde`temperatureCelsius`), bu nedenle özellik ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="5188f-317">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="5188f-318">Özet</span><span class="sxs-lookup"><span data-stu-id="5188f-318">Summary</span></span> | <span data-ttu-id="5188f-319">Sık Erişimli</span><span class="sxs-lookup"><span data-stu-id="5188f-319">Hot</span></span> ||
| <span data-ttu-id="5188f-320">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="5188f-320">ExtensionData</span></span> | <span data-ttu-id="5188f-321">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="5188f-321">temperatureCelsius: 25</span></span> |<span data-ttu-id="5188f-322">Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.</span><span class="sxs-lookup"><span data-stu-id="5188f-322">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="5188f-323">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="5188f-323">DatesAvailable:</span></span><br>  <span data-ttu-id="5188f-324">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="5188f-324">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="5188f-325">8/2/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="5188f-325">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="5188f-326">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="5188f-326">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="5188f-327">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="5188f-327">SummaryWords:</span></span><br><span data-ttu-id="5188f-328">Seyrek Erişimli</span><span class="sxs-lookup"><span data-stu-id="5188f-328">Cool</span></span><br><span data-ttu-id="5188f-329">Rüzgarlı</span><span class="sxs-lookup"><span data-stu-id="5188f-329">Windy</span></span><br><span data-ttu-id="5188f-330">İnsankimliği</span><span class="sxs-lookup"><span data-stu-id="5188f-330">Humid</span></span> |<span data-ttu-id="5188f-331">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="5188f-331">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="5188f-332">Hedef nesne serileştirildiğinde, uzantı veri anahtarı değer çiftleri, gelen JSON 'da olduğu gibi JSON özellikleri olur:</span><span class="sxs-lookup"><span data-stu-id="5188f-332">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="5188f-333">`ExtensionData` özelliği adının JSON içinde görünmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="5188f-333">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="5188f-334">Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5188f-334">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="5188f-335">Seri durumdan çıkarılırken null değeri yoksay</span><span class="sxs-lookup"><span data-stu-id="5188f-335">Ignore null when deserializing</span></span>

<span data-ttu-id="5188f-336">Varsayılan olarak, JSON 'daki bir özellik null ise, hedef nesnedeki karşılık gelen özellik null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="5188f-336">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="5188f-337">Bazı senaryolarda, target özelliği varsayılan bir değere sahip olabilir ve varsayılan değeri geçersiz kılmak için null değer istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="5188f-337">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="5188f-338">Örneğin, aşağıdaki kodun hedef nesneniz temsil ettiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="5188f-338">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="5188f-339">Ve aşağıdaki JSON öğesinin seri durumdan çıkarıldığını varsayalım:</span><span class="sxs-lookup"><span data-stu-id="5188f-339">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="5188f-340">Seri durumdan çıktıktan sonra, `WeatherForecastWithDefault` nesnesinin `Summary` özelliği null.</span><span class="sxs-lookup"><span data-stu-id="5188f-340">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="5188f-341">Bu davranışı değiştirmek için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> `true`olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="5188f-341">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="5188f-342">Bu seçenekle, `WeatherForecastWithDefault` nesnesinin `Summary` özelliği, serisini kaldırma işleminden sonra varsayılan "Özet yok" değeridir.</span><span class="sxs-lookup"><span data-stu-id="5188f-342">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="5188f-343">JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="5188f-343">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="5188f-344">Nullable değer türleri için null değerler özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="5188f-344">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="5188f-345">Utf8JsonReader, Utf8JsonWriter ve JsonDocument</span><span class="sxs-lookup"><span data-stu-id="5188f-345">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="5188f-346"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> UTF-8 kodlu JSON metnine yönelik yüksek performanslı, düşük bir ayırma, Salt ilet okuyucu, bir `ReadOnlySpan<byte>` veya `ReadOnlySequence<byte>`okur.</span><span class="sxs-lookup"><span data-stu-id="5188f-346"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="5188f-347">`Utf8JsonReader`, özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="5188f-347">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="5188f-348"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemi, kapsamakta olan `Utf8JsonReader` kullanır.</span><span class="sxs-lookup"><span data-stu-id="5188f-348">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="5188f-349"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>, `String`, `Int32`ve `DateTime`gibi ortak .NET türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="5188f-349"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="5188f-350">Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="5188f-350">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="5188f-351"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemi, kapsamakta olan `Utf8JsonWriter` kullanır.</span><span class="sxs-lookup"><span data-stu-id="5188f-351">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="5188f-352"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>, `Utf8JsonReader`kullanarak salt okunurdur Belge Nesne Modeli (DOM) oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="5188f-352"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="5188f-353">DOM, bir JSON yükünde verilere rastgele erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5188f-353">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="5188f-354">Yükü oluşturan JSON öğelerine <xref:System.Text.Json.JsonElement> türü aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="5188f-354">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="5188f-355">`JsonElement` türü, JSON metnini ortak .NET türlerine dönüştürmek için API 'lerle birlikte dizi ve nesne numaralandırıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="5188f-355">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="5188f-356">`JsonDocument`, bir <xref:System.Text.Json.JsonDocument.RootElement> özelliğini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="5188f-356">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="5188f-357">Aşağıdaki bölümlerde, bu araçların JSON okuma ve yazma için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5188f-357">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="5188f-358">Veri erişimi için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="5188f-358">Use JsonDocument for access to data</span></span>

<span data-ttu-id="5188f-359">Aşağıdaki örnek, bir JSON dizesindeki verilere rastgele erişim için <xref:System.Text.Json.JsonDocument> sınıfının nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5188f-359">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="5188f-360">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="5188f-360">The preceding code:</span></span>

* <span data-ttu-id="5188f-361">Çözümlenecek JSON 'ın `jsonString`adlı bir dizede olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="5188f-361">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="5188f-362">Bir `Grade` özelliğine sahip `Students` dizisindeki nesneler için Ortalama bir sınıf hesaplar.</span><span class="sxs-lookup"><span data-stu-id="5188f-362">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="5188f-363">Bir sınıfa sahip olmayan öğrenciler için varsayılan bir 70 sınıfı atar.</span><span class="sxs-lookup"><span data-stu-id="5188f-363">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="5188f-364">Her yinelemeyle bir `count` değişkenini arttırarak öğrencileri sayar.</span><span class="sxs-lookup"><span data-stu-id="5188f-364">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="5188f-365">Aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonElement.GetArrayLength%2A>bir alternatif çağrdır:</span><span class="sxs-lookup"><span data-stu-id="5188f-365">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="5188f-366">Bu kodun işlediği JSON örneğine bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-366">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="5188f-367">JSON yazmak için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="5188f-367">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="5188f-368">Aşağıdaki örnek, bir <xref:System.Text.Json.JsonDocument>JSON yazmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="5188f-368">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="5188f-369">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="5188f-369">The preceding code:</span></span>

* <span data-ttu-id="5188f-370">Bir JSON dosyası okur, verileri bir `JsonDocument`yükler ve bir dosyaya biçimlendirilen (düzgün yazdırılmış) JSON yazar.</span><span class="sxs-lookup"><span data-stu-id="5188f-370">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="5188f-371">JSON girişi içindeki açıklamalara izin verildiğini ancak yok sayılacağını belirtmek için <xref:System.Text.Json.JsonDocumentOptions> kullanır.</span><span class="sxs-lookup"><span data-stu-id="5188f-371">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="5188f-372">İşiniz bittiğinde, yazıcı <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> çağırır.</span><span class="sxs-lookup"><span data-stu-id="5188f-372">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="5188f-373">Diğer bir seçenek de yazıcı boşaltıatıldığı zaman yazıcının temizlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="5188f-373">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="5188f-374">Örnek kod tarafından işlenecek JSON girişi örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5188f-374">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="5188f-375">Sonuç, aşağıdaki düzgün yazdırılmış JSON çıktıdır:</span><span class="sxs-lookup"><span data-stu-id="5188f-375">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="5188f-376">Utf8JsonWriter kullanma</span><span class="sxs-lookup"><span data-stu-id="5188f-376">Use Utf8JsonWriter</span></span>

<span data-ttu-id="5188f-377">Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonWriter> sınıfının nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5188f-377">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="5188f-378">Utf8JsonReader kullanma</span><span class="sxs-lookup"><span data-stu-id="5188f-378">Use Utf8JsonReader</span></span>

<span data-ttu-id="5188f-379">Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonReader> sınıfının nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5188f-379">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="5188f-380">Yukarıdaki kod, `jsonUtf8` değişkeninin UTF-8 olarak kodlanmış geçerli JSON içeren bir bayt dizisi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="5188f-380">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="5188f-381">Utf8JsonReader kullanarak verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="5188f-381">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="5188f-382">Aşağıdaki örnek, bir dosyanın zaman uyumlu olarak nasıl okunacağını ve bir değerin nasıl aranacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="5188f-382">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="5188f-383">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="5188f-383">The preceding code:</span></span>

* <span data-ttu-id="5188f-384">JSON 'un bir nesne dizisi içerdiğini ve her nesne dize türünde bir "ad" özelliği içerebildiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="5188f-384">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="5188f-385">"University" ile biten nesneleri ve "ad" özellik değerlerini sayar.</span><span class="sxs-lookup"><span data-stu-id="5188f-385">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="5188f-386">Dosyanın UTF-16 olarak kodlandığını varsayar ve bunu UTF-8 ' e dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5188f-386">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="5188f-387">UTF-8 olarak kodlanmış bir dosya aşağıdaki kodu kullanarak doğrudan bir `ReadOnlySpan<byte>`okunabilir:</span><span class="sxs-lookup"><span data-stu-id="5188f-387">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

  <span data-ttu-id="5188f-388">Dosya bir UTF-8 bayt sırası işareti (BOM) içeriyorsa, bu, okuyucunun metin beklediği için baytları `Utf8JsonReader`geçirmeden önce kaldırın.</span><span class="sxs-lookup"><span data-stu-id="5188f-388">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="5188f-389">Aksi takdirde, BOM geçersiz JSON olarak değerlendirilir ve okuyucu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5188f-389">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="5188f-390">Yukarıdaki kodun okuya, bir JSON örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5188f-390">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="5188f-391">Sonuçtaki Özet ileti "2 ' den 4 ' ün" University "ile biten adlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="5188f-391">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="5188f-392">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="5188f-392">Additional resources</span></span>

* [<span data-ttu-id="5188f-393">System. Text. JSON genel bakış</span><span class="sxs-lookup"><span data-stu-id="5188f-393">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="5188f-394">Özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="5188f-394">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="5188f-395">Newtonsoft. JSON 'dan geçiş yapma</span><span class="sxs-lookup"><span data-stu-id="5188f-395">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="5188f-396">System. Text. JSON içinde DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="5188f-396">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* [<span data-ttu-id="5188f-397">System. Text. JSON API başvurusu</span><span class="sxs-lookup"><span data-stu-id="5188f-397">System.Text.Json API reference</span></span>](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
