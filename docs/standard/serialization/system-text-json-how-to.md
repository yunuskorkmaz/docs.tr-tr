---
title: C#-.NET kullanarak JSON serileştirmek ve serisini kaldırma
description: Bu makalede, System.Text.Json .net 'TEKI JSON 'a seri hale getirmek ve seri durumdan çıkarmak için ad alanını nasıl kullanabileceğiniz gösterilmektedir. Örnek kod içerir.
ms.date: 05/13/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 7ad2721f12c5d14b61b35ecf7696ff0d6a6f27da
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289518"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="265c7-104">.NET içinde JSON ve seri hale getirme (sıralama ve kaldırma)</span><span class="sxs-lookup"><span data-stu-id="265c7-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="265c7-105">Bu makalede, <xref:System.Text.Json> JavaScript nesne gösterimi (JSON) ve öğesinden seri hale getirmek ve seri durumdan çıkarmak için ad alanı kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="265c7-105">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="265c7-106">İçinden mevcut kodu aktarıyorsanız `Newtonsoft.Json` , bkz. [nasıl geçiş `System.Text.Json` yapılacağı ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="265c7-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="265c7-107">Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="265c7-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="265c7-108">Serileştirme örnek kodunun çoğu, <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` JSON (girintileme ve insanlar okunabilirlik için boşluk) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="265c7-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="265c7-109">Üretim kullanımı için genellikle bu ayar için varsayılan değerini kabul etmiş olursunuz `false` .</span><span class="sxs-lookup"><span data-stu-id="265c7-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="265c7-110">Kod örnekleri, aşağıdaki sınıfa ve türevlerini ifade eder:</span><span class="sxs-lookup"><span data-stu-id="265c7-110">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="265c7-111">Ad alanları</span><span class="sxs-lookup"><span data-stu-id="265c7-111">Namespaces</span></span>

<span data-ttu-id="265c7-112"><xref:System.Text.Json>Ad alanı tüm giriş noktalarını ve ana türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="265c7-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="265c7-113"><xref:System.Text.Json.Serialization>Ad alanı, serileştirme ve seri durumdan çıkarma ile ilgili gelişmiş senaryolar ve özelleştirme için öznitelikler ve API 'leri içerir.</span><span class="sxs-lookup"><span data-stu-id="265c7-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="265c7-114">Bu makalede gösterilen kod örnekleri, `using` Bu ad alanlarından biri veya her ikisi için yönergeler gerektirir:</span><span class="sxs-lookup"><span data-stu-id="265c7-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="265c7-115"><xref:System.Runtime.Serialization>Ad alanındaki öznitelikler Şu anda sürümünde desteklenmemektedir `System.Text.Json` .</span><span class="sxs-lookup"><span data-stu-id="265c7-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="265c7-116">.NET nesnelerini JSON 'a yazma (serileştirme)</span><span class="sxs-lookup"><span data-stu-id="265c7-116">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="265c7-117">JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="265c7-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="265c7-118">Aşağıdaki örnek bir dize olarak JSON oluşturur:</span><span class="sxs-lookup"><span data-stu-id="265c7-118">The following example creates JSON as a string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="265c7-119">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="265c7-119">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="265c7-120">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="265c7-120">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="265c7-121">Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="265c7-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="265c7-122">Öğesinin aşırı yüklemesi `Serialize()` genel bir tür parametresi alır:</span><span class="sxs-lookup"><span data-stu-id="265c7-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="265c7-123">Serileştirme örneği</span><span class="sxs-lookup"><span data-stu-id="265c7-123">Serialization example</span></span>

<span data-ttu-id="265c7-124">Aşağıda, koleksiyonları ve iç içe yerleştirilmiş bir sınıfı içeren örnek bir sınıf verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-124">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="265c7-125">Önceki türün bir örneğinin serileştirilmesi için JSON çıktısı aşağıdaki örnekteki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="265c7-125">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="265c7-126">JSON çıktısı varsayılan olarak Mini olarak belirlenir:</span><span class="sxs-lookup"><span data-stu-id="265c7-126">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="265c7-127">Aşağıdaki örnek, biçimlendirilen aynı JSON 'ı gösterir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):</span><span class="sxs-lookup"><span data-stu-id="265c7-127">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="265c7-128">UTF-8 ' e serileştirme</span><span class="sxs-lookup"><span data-stu-id="265c7-128">Serialize to UTF-8</span></span>

<span data-ttu-id="265c7-129">UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="265c7-129">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="265c7-130">' İ <xref:System.Text.Json.JsonSerializer.Serialize%2A> alan bir aşırı yükleme <xref:System.Text.Json.Utf8JsonWriter> de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="265c7-130">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="265c7-131">UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="265c7-131">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="265c7-132">Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="265c7-132">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="265c7-133">Serileştirme davranışı</span><span class="sxs-lookup"><span data-stu-id="265c7-133">Serialization behavior</span></span>

* <span data-ttu-id="265c7-134">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="265c7-134">By default, all public properties are serialized.</span></span> <span data-ttu-id="265c7-135">[Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="265c7-135">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="265c7-136">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="265c7-136">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="265c7-137">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="265c7-137">By default, JSON is minified.</span></span> <span data-ttu-id="265c7-138">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="265c7-138">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="265c7-139">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="265c7-139">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="265c7-140">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="265c7-140">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="265c7-141">Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="265c7-141">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="265c7-142">Şu anda, alanlar hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="265c7-142">Currently, fields are excluded.</span></span>

<span data-ttu-id="265c7-143">Desteklenen türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="265c7-143">Supported types include:</span></span>

* <span data-ttu-id="265c7-144">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="265c7-144">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="265c7-145">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="265c7-145">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="265c7-146">Tek boyutlu ve pürüzlü Diziler ( `ArrayName[][]` ).</span><span class="sxs-lookup"><span data-stu-id="265c7-146">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="265c7-147">`Dictionary<string,TValue>`Burada `TValue` , `object` `JsonElement` veya bir poco.</span><span class="sxs-lookup"><span data-stu-id="265c7-147">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="265c7-148">Aşağıdaki ad alanlarından Koleksiyonlar.</span><span class="sxs-lookup"><span data-stu-id="265c7-148">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="265c7-149">Ek türleri işlemek veya yerleşik dönüştürücüler tarafından desteklenmeyen işlevler sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="265c7-149">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="265c7-150">JSON 'ı .NET Objects 'e okuma (serisini kaldırma)</span><span class="sxs-lookup"><span data-stu-id="265c7-150">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="265c7-151">Bir dizeden veya dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="265c7-151">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="265c7-152">Aşağıdaki örnek, bir dizeden JSON okur ve `WeatherForecast` daha önce [serileştirme örneği](#serialization-example)için gösterilen sınıfının bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="265c7-152">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="265c7-153">Zaman uyumlu kod kullanarak bir dosyadan seri durumdan çıkarmak için, aşağıdaki örnekte gösterildiği gibi dosyayı bir dizeye okuyun:</span><span class="sxs-lookup"><span data-stu-id="265c7-153">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="265c7-154">Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için yöntemini çağırın <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> :</span><span class="sxs-lookup"><span data-stu-id="265c7-154">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="265c7-155">UTF-8 ' den serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="265c7-155">Deserialize from UTF-8</span></span>

<span data-ttu-id="265c7-156">UTF-8 ' den seri durumdan çıkarmak için, <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> `Utf8JsonReader` `ReadOnlySpan<byte>` Aşağıdaki örneklerde gösterildiği gibi bir veya içeren bir aşırı yükleme çağırın.</span><span class="sxs-lookup"><span data-stu-id="265c7-156">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="265c7-157">Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="265c7-157">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="265c7-158">Seri durumdan çıkarma davranışı</span><span class="sxs-lookup"><span data-stu-id="265c7-158">Deserialization behavior</span></span>

* <span data-ttu-id="265c7-159">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="265c7-159">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="265c7-160">[Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="265c7-160">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="265c7-161">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="265c7-161">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="265c7-162">Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="265c7-162">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="265c7-163">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="265c7-163">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="265c7-164">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="265c7-164">By default, enums are supported as numbers.</span></span> <span data-ttu-id="265c7-165">[Enum adlarını dizeler olarak seri hale](#enums-as-strings)getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="265c7-165">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="265c7-166">Alanlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="265c7-166">Fields aren't supported.</span></span>
* <span data-ttu-id="265c7-167">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="265c7-167">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="265c7-168">[Yorumlara ve sondaki virgüllerin bulunmasına izin](#allow-comments-and-trailing-commas)verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="265c7-168">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="265c7-169">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="265c7-169">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="265c7-170">Yerleşik dönüştürücüler tarafından desteklenmeyen işlevselliği sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="265c7-170">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="265c7-171">Biçimlendirilen JSON 'a serileştirme</span><span class="sxs-lookup"><span data-stu-id="265c7-171">Serialize to formatted JSON</span></span>

<span data-ttu-id="265c7-172">JSON çıkışını gerçekten yazdırmak için şu <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> şekilde ayarlayın `true` :</span><span class="sxs-lookup"><span data-stu-id="265c7-172">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="265c7-173">Aşağıda, seri hale getirilebilir ve düzgün şekilde yazdırılan JSON çıkışının örnek bir türü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-173">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="265c7-174">JSON adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="265c7-174">Customize JSON names and values</span></span>

<span data-ttu-id="265c7-175">Varsayılan olarak, özellik adları ve sözlük anahtarları, büyük/küçük harf gibi JSON çıktısında değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="265c7-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="265c7-176">Sabit listesi değerleri sayı olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="265c7-176">Enum values are represented as numbers.</span></span> <span data-ttu-id="265c7-177">Bu bölümde nasıl yapılacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="265c7-177">This section explains how to:</span></span>

* [<span data-ttu-id="265c7-178">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="265c7-178">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="265c7-179">Tüm özellik adlarını ortası durumuna Dönüştür</span><span class="sxs-lookup"><span data-stu-id="265c7-179">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="265c7-180">Özel özellik adlandırma ilkesi uygulama</span><span class="sxs-lookup"><span data-stu-id="265c7-180">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="265c7-181">Sözlük anahtarlarını ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="265c7-181">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="265c7-182">Numaralandırmaları dizelere ve ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="265c7-182">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="265c7-183">JSON özellik adlarını ve değerlerini özel olarak işleme gerektiren diğer senaryolar için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="265c7-183">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="265c7-184">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="265c7-184">Customize individual property names</span></span>

<span data-ttu-id="265c7-185">Ayrı özelliklerin adını ayarlamak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="265c7-185">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="265c7-186">Serileştirme ve sonuç JSON için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-186">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="265c7-187">Bu öznitelik tarafından ayarlanan özellik adı:</span><span class="sxs-lookup"><span data-stu-id="265c7-187">The property name set by this attribute:</span></span>

* <span data-ttu-id="265c7-188">Serileştirme ve seri durumundan çıkarma için her iki yönde de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="265c7-188">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="265c7-189">Özellik adlandırma ilkelerine göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="265c7-189">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="265c7-190">Tüm JSON Özellik adları için ortası Case kullanın</span><span class="sxs-lookup"><span data-stu-id="265c7-190">Use camel case for all JSON property names</span></span>

<span data-ttu-id="265c7-191">Tüm JSON Özellik adları için ortası durumunu kullanmak için, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase` Aşağıdaki örnekte gösterildiği gibi olarak ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="265c7-191">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="265c7-192">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-192">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="265c7-193">Ortası durum özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="265c7-193">The camel case property naming policy:</span></span>

* <span data-ttu-id="265c7-194">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="265c7-194">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="265c7-195">Öznitelikleri tarafından geçersiz kılınır `[JsonPropertyName]` .</span><span class="sxs-lookup"><span data-stu-id="265c7-195">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="265c7-196">Bu nedenle, örnekteki JSON Özellik adının `Wind` ortası durum olmaması neden olur.</span><span class="sxs-lookup"><span data-stu-id="265c7-196">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="265c7-197">Özel bir JSON Özellik adlandırma ilkesi kullanma</span><span class="sxs-lookup"><span data-stu-id="265c7-197">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="265c7-198">Özel bir JSON Özellik adlandırma ilkesi kullanmak için, <xref:System.Text.Json.JsonNamingPolicy> <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> Aşağıdaki örnekte gösterildiği gibi yönteminden türeten bir sınıf oluşturun ve yöntemi geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="265c7-198">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="265c7-199">Daha sonra <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> özelliği, adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="265c7-199">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="265c7-200">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-200">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="265c7-201">JSON özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="265c7-201">The JSON property naming policy:</span></span>

* <span data-ttu-id="265c7-202">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="265c7-202">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="265c7-203">Öznitelikleri tarafından geçersiz kılınır `[JsonPropertyName]` .</span><span class="sxs-lookup"><span data-stu-id="265c7-203">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="265c7-204">Bu, örnekteki JSON Özellik adının `Wind` büyük harfle değil.</span><span class="sxs-lookup"><span data-stu-id="265c7-204">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="265c7-205">Camel durum sözlüğü anahtarları</span><span class="sxs-lookup"><span data-stu-id="265c7-205">Camel case dictionary keys</span></span>

<span data-ttu-id="265c7-206">Seri hale getirilecek bir nesnenin özelliği tür ise `Dictionary<string,TValue>` , `string` anahtarlar ortası duruma dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="265c7-206">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="265c7-207">Bunu yapmak için, <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase` Aşağıdaki örnekte gösterildiği gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="265c7-207">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="265c7-208">Anahtar-değer çiftlerine sahip adlı bir sözlük ile bir nesneyi serileştirmek `TemperatureRanges` `"ColdMinTemp", 20` ve `"HotMinTemp", 40` Aşağıdaki örnekte olduğu gibi JSON çıktısına neden olur:</span><span class="sxs-lookup"><span data-stu-id="265c7-208">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="265c7-209">Sözlük anahtarları için ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="265c7-209">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="265c7-210">Bir sözlüğün serisini kaldırırsanız, için belirtseniz bile anahtarlar JSON dosyasıyla eşleşir `JsonNamingPolicy.CamelCase` `DictionaryKeyPolicy` .</span><span class="sxs-lookup"><span data-stu-id="265c7-210">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="265c7-211">Dizeler dize olarak numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="265c7-211">Enums as strings</span></span>

<span data-ttu-id="265c7-212">Varsayılan olarak, numaralandırmalar sayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="265c7-212">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="265c7-213">Sabit listesi adlarını dizeler olarak seri hale getirmek için öğesini kullanın <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .</span><span class="sxs-lookup"><span data-stu-id="265c7-213">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="265c7-214">Örneğin, bir sabit listesi olan aşağıdaki sınıfı seri hale getirmeniz gerektiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="265c7-214">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="265c7-215">Özet ise `Hot` , varsayılan olarak SERILEŞTIRILMIŞ JSON sayısal değer 3 ' ü içerir:</span><span class="sxs-lookup"><span data-stu-id="265c7-215">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="265c7-216">Aşağıdaki örnek kod, sayısal değerler yerine enum adlarını seri hale getirir ve adları ortası örneğine dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="265c7-216">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="265c7-217">Elde edilen JSON aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="265c7-217">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="265c7-218">Aşağıdaki örnekte gösterildiği gibi, sabit listesi dize adları da seri durumdan çıkarılmış olabilir:</span><span class="sxs-lookup"><span data-stu-id="265c7-218">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="265c7-219">Özellikleri serileştirme dışında tut</span><span class="sxs-lookup"><span data-stu-id="265c7-219">Exclude properties from serialization</span></span>

<span data-ttu-id="265c7-220">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="265c7-220">By default, all public properties are serialized.</span></span> <span data-ttu-id="265c7-221">Bir kısmının JSON çıktısında görünmesini istemiyorsanız, birkaç seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="265c7-221">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="265c7-222">Bu bölümde nasıl hariç tutulacak açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="265c7-222">This section explains how to exclude:</span></span>

* [<span data-ttu-id="265c7-223">Bireysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="265c7-223">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="265c7-224">Tüm salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="265c7-224">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="265c7-225">Tüm null değerli özellikler</span><span class="sxs-lookup"><span data-stu-id="265c7-225">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="265c7-226">Bireysel özellikleri Dışla</span><span class="sxs-lookup"><span data-stu-id="265c7-226">Exclude individual properties</span></span>

<span data-ttu-id="265c7-227">Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="265c7-227">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="265c7-228">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-228">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="265c7-229">Tüm salt okuma özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="265c7-229">Exclude all read-only properties</span></span>

<span data-ttu-id="265c7-230">Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="265c7-230">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="265c7-231">Tüm salt okunurdur özelliklerini hariç tutmak için, <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> `true` Aşağıdaki örnekte gösterildiği gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="265c7-231">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="265c7-232">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-232">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="265c7-233">Bu seçenek yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="265c7-233">This option applies only to serialization.</span></span> <span data-ttu-id="265c7-234">Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="265c7-234">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="265c7-235">Tüm null değer özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="265c7-235">Exclude all null value properties</span></span>

<span data-ttu-id="265c7-236">Tüm null değer özelliklerini dışlamak için, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> `true` Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="265c7-236">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="265c7-237">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-237">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="265c7-238">Özellik</span><span class="sxs-lookup"><span data-stu-id="265c7-238">Property</span></span> |<span data-ttu-id="265c7-239">Değer</span><span class="sxs-lookup"><span data-stu-id="265c7-239">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="265c7-240">Tarih</span><span class="sxs-lookup"><span data-stu-id="265c7-240">Date</span></span>    | <span data-ttu-id="265c7-241">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="265c7-241">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="265c7-242">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="265c7-242">TemperatureCelsius</span></span>| <span data-ttu-id="265c7-243">25</span><span class="sxs-lookup"><span data-stu-id="265c7-243">25</span></span> |
| <span data-ttu-id="265c7-244">Özet</span><span class="sxs-lookup"><span data-stu-id="265c7-244">Summary</span></span>| <span data-ttu-id="265c7-245">null</span><span class="sxs-lookup"><span data-stu-id="265c7-245">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="265c7-246">Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="265c7-246">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="265c7-247">Seri durumdan çıkarma üzerindeki etkisi hakkında daha fazla bilgi için bkz. [serisi kaldırılırken null değeri yoksay](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="265c7-247">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="265c7-248">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="265c7-248">Customize character encoding</span></span>

<span data-ttu-id="265c7-249">Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="265c7-249">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="265c7-250">Diğer bir deyişle, bu, `\uxxxx` karakterin Unicode kodunun bulunduğu konum ile değiştirilir `xxxx` .</span><span class="sxs-lookup"><span data-stu-id="265c7-250">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="265c7-251">Örneğin, `Summary` özelliği Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="265c7-251">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="265c7-252">Dil karakter kümelerini serileştirme</span><span class="sxs-lookup"><span data-stu-id="265c7-252">Serialize language character sets</span></span>

<span data-ttu-id="265c7-253">Bir veya daha fazla dilin karakter kümesini kaçış olmadan seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi bir örneği oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> :</span><span class="sxs-lookup"><span data-stu-id="265c7-253">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="265c7-254">Bu kod, Kiril veya Yunan karakterlerinden kaçış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="265c7-254">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="265c7-255">`Summary`Özellik Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="265c7-255">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="265c7-256">Tüm dil kümelerini kaçış olmadan seri hale getirmek için kullanın <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="265c7-256">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="265c7-257">Belirli karakterleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="265c7-257">Serialize specific characters</span></span>

<span data-ttu-id="265c7-258">Diğer bir seçenek de, kaçırılmadan, izin vermek istediğiniz tek tek karakterleri belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="265c7-258">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="265c7-259">Aşağıdaki örnek, жарко 'in yalnızca ilk iki karakterini seri hale getirir:</span><span class="sxs-lookup"><span data-stu-id="265c7-259">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="265c7-260">Yukarıdaki kod tarafından üretilen JSON örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-260">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="265c7-261">Tüm karakterleri seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="265c7-261">Serialize all characters</span></span>

<span data-ttu-id="265c7-262"><xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, kullanarak kaçı en aza indirin:</span><span class="sxs-lookup"><span data-stu-id="265c7-262">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="265c7-263">Varsayılan kodlayıcıyla karşılaştırıldığında kodlayıcı, `UnsafeRelaxedJsonEscaping` karakterlerin kaçışsız geçmesine izin verme konusunda daha fazla izne sahiptir:</span><span class="sxs-lookup"><span data-stu-id="265c7-263">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="265c7-264">,, Ve gibi HTML 'ye duyarlı karakterleri atmaz `<` `>` `&` `'` .</span><span class="sxs-lookup"><span data-stu-id="265c7-264">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="265c7-265">Bu, XSS veya bilgi açıklama saldırılarına karşı ek derinlemesine savunma korumaları sunmaz, örneğin, *karakter*kümesinde istemci ve sunucu disagreeing neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="265c7-265">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="265c7-266">Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="265c7-266">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="265c7-267">Örneğin, sunucu yanıt üst bilgisini gönderiyorsa onu kullanabilirsiniz `Content-Type: application/json; charset=utf-8` .</span><span class="sxs-lookup"><span data-stu-id="265c7-267">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="265c7-268">Ham `UnsafeRelaxedJsonEscaping` çıkışın BIR HTML sayfasına veya bir öğeye yayılmasın `<script>` .</span><span class="sxs-lookup"><span data-stu-id="265c7-268">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="265c7-269">Türetilmiş sınıfların serileştirme özellikleri</span><span class="sxs-lookup"><span data-stu-id="265c7-269">Serialize properties of derived classes</span></span>

<span data-ttu-id="265c7-270">Çok biçimli bir tür hiyerarşisinin serileştirilmesi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="265c7-270">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="265c7-271">Örneğin, bir özellik bir arabirim ya da soyut sınıf olarak tanımlanmışsa, çalışma zamanı türü ek özelliklere sahip olsa bile yalnızca arabirim veya soyut sınıf üzerinde tanımlanan özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="265c7-271">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="265c7-272">Bu davranışın istisnaları, bu bölümde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="265c7-272">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="265c7-273">Örneğin, bir `WeatherForecast` sınıfınız ve türetilmiş bir sınıfınız olduğunu varsayalım `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="265c7-273">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="265c7-274">Ve derleme zamanında yöntemin tür bağımsız değişkeninin `Serialize` Şu olduğunu varsayalım `WeatherForecast` :</span><span class="sxs-lookup"><span data-stu-id="265c7-274">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="265c7-275">Bu senaryoda, `WindSpeed` `weatherForecast` nesne gerçekten bir nesne olsa bile Özellik serileştirilmez `WeatherForecastDerived` .</span><span class="sxs-lookup"><span data-stu-id="265c7-275">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="265c7-276">Yalnızca temel sınıf özellikleri serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="265c7-276">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="265c7-277">Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="265c7-277">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="265c7-278">Yukarıdaki örnekteki türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="265c7-278">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="265c7-279"><xref:System.Text.Json.JsonSerializer.Serialize%2A>Çalışma zamanında türü belirtmenize olanak sağlayan aşırı yüklemesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="265c7-279">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at run time:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="265c7-280">Seri hale getirilecek nesneyi bildirin `object` .</span><span class="sxs-lookup"><span data-stu-id="265c7-280">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="265c7-281">Yukarıdaki örnek senaryoda, her iki yaklaşım `WindSpeed` ÖZELLIĞIN JSON çıktısına dahil olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="265c7-281">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="265c7-282">Bu yaklaşımlar yalnızca kök nesnenin seri hale getirilmesi için, bu kök nesnenin özellikleri için değil, polimorfik serileştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="265c7-282">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="265c7-283">Bunları tür olarak tanımlarsanız alt düzey nesneler için polimorfik serileştirme alabilirsiniz `object` .</span><span class="sxs-lookup"><span data-stu-id="265c7-283">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="265c7-284">Örneğin, `WeatherForecast` sınıfınızın, tür olarak tanımlanabilen adında bir özelliği olduğunu varsayalım `PreviousForecast` `WeatherForecast` `object` :</span><span class="sxs-lookup"><span data-stu-id="265c7-284">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="265c7-285">`PreviousForecast`Özelliği bir örneği içeriyorsa `WeatherForecastDerived` :</span><span class="sxs-lookup"><span data-stu-id="265c7-285">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="265c7-286">Serileştirmede JSON çıktısı `WeatherForecastWithPrevious` **içermez** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="265c7-286">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="265c7-287">Serileştirmede JSON çıktısı `WeatherForecastWithPreviousAsObject` **dahildir** `WindSpeed` .</span><span class="sxs-lookup"><span data-stu-id="265c7-287">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="265c7-288">Seri hale getirmek için `WeatherForecastWithPreviousAsObject` , `Serialize<object>` ya da `GetType` kök nesnesi türetilmiş bir tür olabilecek bir nesne olmadığından çağırmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="265c7-288">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="265c7-289">Aşağıdaki kod örneği, `Serialize<object>` veya çağırmaz `GetType` :</span><span class="sxs-lookup"><span data-stu-id="265c7-289">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="265c7-290">Yukarıdaki kod doğru şekilde serileştirir `WeatherForecastWithPreviousAsObject` :</span><span class="sxs-lookup"><span data-stu-id="265c7-290">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="265c7-291">Özellikleri, arabirimler ile birlikte tanımlamaya yönelik aynı yaklaşım `object` .</span><span class="sxs-lookup"><span data-stu-id="265c7-291">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="265c7-292">Aşağıdaki arabirime ve uygulamaya sahip olduğunuzu ve uygulama örnekleri içeren özelliklerle bir sınıfı seri hale getirmek istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="265c7-292">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

<span data-ttu-id="265c7-293">Bir örneğini serileştirçalıştığınızda `Forecasts` , yalnızca `Tuesday` `WindSpeed` özelliğini gösterir, çünkü `Tuesday` Şu şekilde tanımlanır `object` :</span><span class="sxs-lookup"><span data-stu-id="265c7-293">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="265c7-294">Aşağıdaki örnek, önceki koddan elde edilen JSON 'u göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="265c7-294">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="265c7-295">Polimorfik **serileştirme**hakkında daha fazla bilgi için ve **serisini kaldırma**hakkında bilgi için, bkz. ' [den Newtonsoft.Json System.Text.Json ' ye geçiş ](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="265c7-295">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="265c7-296">Yorumlara ve sondaki virgülleri izin ver</span><span class="sxs-lookup"><span data-stu-id="265c7-296">Allow comments and trailing commas</span></span>

<span data-ttu-id="265c7-297">Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="265c7-297">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="265c7-298">JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini olarak ayarlayın `JsonCommentHandling.Skip` .</span><span class="sxs-lookup"><span data-stu-id="265c7-298">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="265c7-299">Ve sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini olarak ayarlayın `true` .</span><span class="sxs-lookup"><span data-stu-id="265c7-299">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="265c7-300">Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="265c7-300">The following example shows how to allow both:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="265c7-301">Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-301">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="265c7-302">Büyük/küçük harfe duyarsız Özellik eşleştirme</span><span class="sxs-lookup"><span data-stu-id="265c7-302">Case-insensitive property matching</span></span>

<span data-ttu-id="265c7-303">Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar.</span><span class="sxs-lookup"><span data-stu-id="265c7-303">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="265c7-304">Bu davranışı değiştirmek için şu <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> şekilde ayarlayın `true` :</span><span class="sxs-lookup"><span data-stu-id="265c7-304">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="265c7-305">Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="265c7-305">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="265c7-306">Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="265c7-306">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="265c7-307">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="265c7-307">Handle overflow JSON</span></span>

<span data-ttu-id="265c7-308">Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="265c7-308">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="265c7-309">Örneğin, hedef türünün bu olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="265c7-309">For example, suppose your target type is this:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="265c7-310">Ve seri durumdan çıkarılacak JSON şu şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="265c7-310">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="265c7-311">Gösterilen türde gösterilen JSON serisini kaldırırsanız, `DatesAvailable` ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor.</span><span class="sxs-lookup"><span data-stu-id="265c7-311">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="265c7-312">Bu özellikler gibi ek verileri yakalamak için, [Jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini veya türünde bir özelliğe uygulayın `Dictionary<string,object>` `Dictionary<string,JsonElement>` :</span><span class="sxs-lookup"><span data-stu-id="265c7-312">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="265c7-313">Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veri özelliğin anahtar-değer çiftleri haline gelir `ExtensionData` :</span><span class="sxs-lookup"><span data-stu-id="265c7-313">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="265c7-314">Özellik</span><span class="sxs-lookup"><span data-stu-id="265c7-314">Property</span></span> |<span data-ttu-id="265c7-315">Değer</span><span class="sxs-lookup"><span data-stu-id="265c7-315">Value</span></span>  |<span data-ttu-id="265c7-316">Notlar</span><span class="sxs-lookup"><span data-stu-id="265c7-316">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="265c7-317">Tarih</span><span class="sxs-lookup"><span data-stu-id="265c7-317">Date</span></span>    | <span data-ttu-id="265c7-318">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="265c7-318">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="265c7-319">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="265c7-319">TemperatureCelsius</span></span>| <span data-ttu-id="265c7-320">0</span><span class="sxs-lookup"><span data-stu-id="265c7-320">0</span></span> | <span data-ttu-id="265c7-321">Büyük/küçük harfe duyarlı uyuşmazlık ( `temperatureCelsius` JSON 'da), bu nedenle özellik ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="265c7-321">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="265c7-322">Özet</span><span class="sxs-lookup"><span data-stu-id="265c7-322">Summary</span></span> | <span data-ttu-id="265c7-323">Sık Erişimli</span><span class="sxs-lookup"><span data-stu-id="265c7-323">Hot</span></span> ||
| <span data-ttu-id="265c7-324">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="265c7-324">ExtensionData</span></span> | <span data-ttu-id="265c7-325">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="265c7-325">temperatureCelsius: 25</span></span> |<span data-ttu-id="265c7-326">Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.</span><span class="sxs-lookup"><span data-stu-id="265c7-326">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="265c7-327">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="265c7-327">DatesAvailable:</span></span><br>  <span data-ttu-id="265c7-328">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="265c7-328">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="265c7-329">8/2/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="265c7-329">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="265c7-330">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="265c7-330">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="265c7-331">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="265c7-331">SummaryWords:</span></span><br><span data-ttu-id="265c7-332">Seyrek Erişimli</span><span class="sxs-lookup"><span data-stu-id="265c7-332">Cool</span></span><br><span data-ttu-id="265c7-333">Rüzgarlı</span><span class="sxs-lookup"><span data-stu-id="265c7-333">Windy</span></span><br><span data-ttu-id="265c7-334">İnsankimliği</span><span class="sxs-lookup"><span data-stu-id="265c7-334">Humid</span></span> |<span data-ttu-id="265c7-335">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="265c7-335">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="265c7-336">Hedef nesne serileştirildiğinde, uzantı veri anahtarı değer çiftleri, gelen JSON 'da olduğu gibi JSON özellikleri olur:</span><span class="sxs-lookup"><span data-stu-id="265c7-336">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="265c7-337">`ExtensionData`Özellik ADıNıN JSON içinde görünmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="265c7-337">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="265c7-338">Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="265c7-338">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="265c7-339">Seri durumdan çıkarılırken null değeri yoksay</span><span class="sxs-lookup"><span data-stu-id="265c7-339">Ignore null when deserializing</span></span>

<span data-ttu-id="265c7-340">Varsayılan olarak, JSON 'daki bir özellik null ise, hedef nesnedeki karşılık gelen özellik null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="265c7-340">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="265c7-341">Bazı senaryolarda, target özelliği varsayılan bir değere sahip olabilir ve varsayılan değeri geçersiz kılmak için null değer istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="265c7-341">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="265c7-342">Örneğin, aşağıdaki kodun hedef nesneniz temsil ettiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="265c7-342">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="265c7-343">Ve aşağıdaki JSON öğesinin seri durumdan çıkarıldığını varsayalım:</span><span class="sxs-lookup"><span data-stu-id="265c7-343">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="265c7-344">Seri durumdan çıktıktan sonra, `Summary` nesnesinin özelliği `WeatherForecastWithDefault` null olur.</span><span class="sxs-lookup"><span data-stu-id="265c7-344">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="265c7-345">Bu davranışı değiştirmek için, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> `true` Aşağıdaki örnekte gösterildiği gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="265c7-345">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="265c7-346">Bu seçenekle `Summary` nesnenin özelliği, `WeatherForecastWithDefault` serisini kaldırma işleminden sonra varsayılan "Özet yok" değeridir.</span><span class="sxs-lookup"><span data-stu-id="265c7-346">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="265c7-347">JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="265c7-347">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="265c7-348">Nullable değer türleri için null değerler özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="265c7-348">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="265c7-349">Utf8JsonReader, Utf8JsonWriter ve JsonDocument</span><span class="sxs-lookup"><span data-stu-id="265c7-349">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="265c7-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>, bir veya ' dan okunan UTF-8 kodlu JSON metin için yüksek performanslı, düşük bir ayırma, Salt ilet okuyucu olur `ReadOnlySpan<byte>` `ReadOnlySequence<byte>` .</span><span class="sxs-lookup"><span data-stu-id="265c7-350"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="265c7-351">, `Utf8JsonReader` Özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="265c7-351">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="265c7-352"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>Yöntemi `Utf8JsonReader` , kapakların altında kullanır.</span><span class="sxs-lookup"><span data-stu-id="265c7-352">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="265c7-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>, ve gibi ortak .NET türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur `String` `Int32` `DateTime` .</span><span class="sxs-lookup"><span data-stu-id="265c7-353"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="265c7-354">Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="265c7-354">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="265c7-355"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>Yöntemi `Utf8JsonWriter` , kapakların altında kullanır.</span><span class="sxs-lookup"><span data-stu-id="265c7-355">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="265c7-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>kullanarak salt okunurdur Belge Nesne Modeli (DOM) oluşturma yeteneği sağlar `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="265c7-356"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="265c7-357">DOM, bir JSON yükünde verilere rastgele erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="265c7-357">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="265c7-358">Yükü oluşturan JSON öğelerine tür aracılığıyla erişilebilir <xref:System.Text.Json.JsonElement> .</span><span class="sxs-lookup"><span data-stu-id="265c7-358">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="265c7-359">`JsonElement`Türü, JSON metnini ortak .net türlerine dönüştürmek Için API 'lerle birlikte dizi ve nesne numaralandırıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="265c7-359">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="265c7-360">`JsonDocument`bir <xref:System.Text.Json.JsonDocument.RootElement> özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="265c7-360">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="265c7-361">Aşağıdaki bölümlerde, bu araçların JSON okuma ve yazma için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="265c7-361">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="265c7-362">Veri erişimi için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="265c7-362">Use JsonDocument for access to data</span></span>

<span data-ttu-id="265c7-363">Aşağıdaki örnek, <xref:System.Text.Json.JsonDocument> BIR JSON dizesindeki verilere rastgele erişim için sınıfının nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="265c7-363">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="265c7-364">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="265c7-364">The preceding code:</span></span>

* <span data-ttu-id="265c7-365">Analiz edilecek JSON 'in adlı bir dizede olduğunu varsayar `jsonString` .</span><span class="sxs-lookup"><span data-stu-id="265c7-365">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="265c7-366">Özelliği olan bir dizideki nesneler için Ortalama bir sınıf hesaplar `Students` `Grade` .</span><span class="sxs-lookup"><span data-stu-id="265c7-366">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="265c7-367">Bir sınıfa sahip olmayan öğrenciler için varsayılan bir 70 sınıfı atar.</span><span class="sxs-lookup"><span data-stu-id="265c7-367">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="265c7-368">Her yinelemeyle bir değişkeni arttırarak öğrencileri sayar `count` .</span><span class="sxs-lookup"><span data-stu-id="265c7-368">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="265c7-369"><xref:System.Text.Json.JsonElement.GetArrayLength%2A>Aşağıdaki örnekte gösterildiği gibi bir alternatif çağrdır:</span><span class="sxs-lookup"><span data-stu-id="265c7-369">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="265c7-370">Bu kodun işlediği JSON örneğine bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-370">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="265c7-371">JSON yazmak için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="265c7-371">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="265c7-372">Aşağıdaki örnek, öğesinden nasıl JSON yazılacağını göstermektedir <xref:System.Text.Json.JsonDocument> :</span><span class="sxs-lookup"><span data-stu-id="265c7-372">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="265c7-373">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="265c7-373">The preceding code:</span></span>

* <span data-ttu-id="265c7-374">Bir JSON dosyasını okur, verileri bir `JsonDocument` dosyasına yükler ve bir dosyaya biçimli (düzgün yazdırılmış) JSON yazar.</span><span class="sxs-lookup"><span data-stu-id="265c7-374">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="265c7-375"><xref:System.Text.Json.JsonDocumentOptions>JSON girişi içindeki açıklamalara izin verildiğini ancak yok sayılacağını belirtmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="265c7-375">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="265c7-376">İşiniz bittiğinde, <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> Yazıcı üzerindeki çağrılar.</span><span class="sxs-lookup"><span data-stu-id="265c7-376">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="265c7-377">Diğer bir seçenek de yazıcı boşaltıatıldığı zaman yazıcının temizlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="265c7-377">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="265c7-378">Örnek kod tarafından işlenecek JSON girişi örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="265c7-378">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

<span data-ttu-id="265c7-379">Sonuç, aşağıdaki düzgün yazdırılmış JSON çıktıdır:</span><span class="sxs-lookup"><span data-stu-id="265c7-379">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="265c7-380">Utf8JsonWriter kullanma</span><span class="sxs-lookup"><span data-stu-id="265c7-380">Use Utf8JsonWriter</span></span>

<span data-ttu-id="265c7-381">Aşağıdaki örnek sınıfının nasıl kullanılacağını gösterir <xref:System.Text.Json.Utf8JsonWriter> :</span><span class="sxs-lookup"><span data-stu-id="265c7-381">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="265c7-382">Utf8JsonReader kullanma</span><span class="sxs-lookup"><span data-stu-id="265c7-382">Use Utf8JsonReader</span></span>

<span data-ttu-id="265c7-383">Aşağıdaki örnek sınıfının nasıl kullanılacağını gösterir <xref:System.Text.Json.Utf8JsonReader> :</span><span class="sxs-lookup"><span data-stu-id="265c7-383">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="265c7-384">Yukarıdaki kod, `jsonUtf8` DEĞIŞKENIN UTF-8 olarak kodlanmış GEÇERLI JSON içeren bir bayt dizisi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="265c7-384">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="265c7-385">Utf8JsonReader kullanarak verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="265c7-385">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="265c7-386">Aşağıdaki örnek, bir dosyanın zaman uyumlu olarak nasıl okunacağını ve bir değerin nasıl aranacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="265c7-386">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="265c7-387">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="265c7-387">The preceding code:</span></span>

* <span data-ttu-id="265c7-388">JSON 'un bir nesne dizisi içerdiğini ve her nesne dize türünde bir "ad" özelliği içerebildiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="265c7-388">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="265c7-389">"University" ile biten nesneleri ve "ad" özellik değerlerini sayar.</span><span class="sxs-lookup"><span data-stu-id="265c7-389">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="265c7-390">Dosyanın UTF-16 olarak kodlandığını varsayar ve bunu UTF-8 ' e dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="265c7-390">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="265c7-391">Aşağıdaki kod kullanılarak UTF-8 olarak kodlanmış bir dosya doğrudan bir ile okunabilir `ReadOnlySpan<byte>` :</span><span class="sxs-lookup"><span data-stu-id="265c7-391">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="265c7-392">Dosya bir UTF-8 bayt sırası işareti (BOM) içeriyorsa, okuyucu metin gerektirdiğinden, baytları öğesine geçirmeden önce kaldırın `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="265c7-392">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="265c7-393">Aksi takdirde, BOM geçersiz JSON olarak değerlendirilir ve okuyucu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="265c7-393">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="265c7-394">Yukarıdaki kodun okuya, bir JSON örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="265c7-394">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="265c7-395">Sonuçtaki Özet ileti "2 ' den 4 ' ün" University "ile biten adlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="265c7-395">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a><span data-ttu-id="265c7-396">Utf8JsonReader kullanarak akıştan okuma</span><span class="sxs-lookup"><span data-stu-id="265c7-396">Read from a stream using Utf8JsonReader</span></span>

<span data-ttu-id="265c7-397">Büyük bir dosyayı (örneğin, boyutu bir gigabayt veya daha fazla) okurken, dosyanın tamamını aynı anda belleğe yükleme zorunluluğunu ortadan kaldırmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="265c7-397">When reading a large file (a gigabyte or more in size, for example), you might want to avoid having to load the entire file into memory at once.</span></span> <span data-ttu-id="265c7-398">Bu senaryo için bir kullanabilirsiniz <xref:System.IO.FileStream> .</span><span class="sxs-lookup"><span data-stu-id="265c7-398">For this scenario, you can use a <xref:System.IO.FileStream>.</span></span>

<span data-ttu-id="265c7-399">`Utf8JsonReader`Bir akıştan okumak için kullanırken, aşağıdaki kurallar geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="265c7-399">When using the `Utf8JsonReader` to read from a stream, the following rules apply:</span></span>

* <span data-ttu-id="265c7-400">Kısmi JSON yükünün bulunduğu arabellek en az, onun içindeki en büyük JSON belirteci kadar büyük olmalıdır, böylece okuyucu ilerlemeye devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="265c7-400">The buffer containing the partial JSON payload must be at least as big as the largest JSON token within it so that the reader can make forward progress.</span></span>
* <span data-ttu-id="265c7-401">Arabellek en az JSON içindeki boşluk olan en büyük dizi kadar büyük olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="265c7-401">The buffer must be at least as big as the largest sequence of white space within the JSON.</span></span>
* <span data-ttu-id="265c7-402">Okuyucu, JSON yükünde bir sonrakini tamamen okuuncaya kadar okuduğu verileri takip etmez <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> .</span><span class="sxs-lookup"><span data-stu-id="265c7-402">The reader doesn't keep track of the data it has read until it completely reads the next <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> in the JSON payload.</span></span> <span data-ttu-id="265c7-403">Bu nedenle, arabellekte kalan baytlar varsa, bunları okuyucuya yeniden geçirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="265c7-403">So when there are bytes left over in the buffer, you have to pass them to the reader again.</span></span> <span data-ttu-id="265c7-404"><xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A>Kaç baytın kaldığını anlamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="265c7-404">You can use <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A> to determine how many bytes are left over.</span></span>

<span data-ttu-id="265c7-405">Aşağıdaki kod bir akıştan nasıl okunacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="265c7-405">The following code illustrates how to read from a stream.</span></span> <span data-ttu-id="265c7-406">Örnek bir gösterir <xref:System.IO.MemoryStream> .</span><span class="sxs-lookup"><span data-stu-id="265c7-406">The example shows a <xref:System.IO.MemoryStream>.</span></span> <span data-ttu-id="265c7-407">Benzer kod, <xref:System.IO.FileStream> `FileStream` Başlangıç AŞAMASıNDA bir UTF-8 bom içerdiğinde, ile birlikte çalışır.</span><span class="sxs-lookup"><span data-stu-id="265c7-407">Similar code will work with a <xref:System.IO.FileStream>, except when the `FileStream` contains a UTF-8 BOM at the start.</span></span> <span data-ttu-id="265c7-408">Bu durumda, kalan baytları öğesine geçirmeden önce bu üç baytı arabellekten çıkarmanız gerekir `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="265c7-408">In that case, you need to strip those three bytes from the buffer before passing the remaining bytes to the `Utf8JsonReader`.</span></span> <span data-ttu-id="265c7-409">Aksi halde, BOM JSON 'ın geçerli bir parçası olarak kabul edilmediğinden okuyucu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="265c7-409">Otherwise the reader would throw an exception, since the BOM is not considered a valid part of the JSON.</span></span>

<span data-ttu-id="265c7-410">Örnek kod, bir 4KB arabelleğiyle başlar ve boyutun, bir bütün JSON belirtecine sığamayacak kadar büyük olmadığını bulduğu her seferinde arabellek boyutunu iki katına çıkarır. Bu, okuyucunun JSON yükünde ilerlemesinin ilerlemesini sağlamak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="265c7-410">The sample code starts with a 4KB buffer and doubles the buffer size each time it finds that the size is not big enough to fit a complete JSON token, which is required for the reader to make forward progress on the JSON payload.</span></span> <span data-ttu-id="265c7-411">Kod parçacığında belirtilen JSON örneği, yalnızca çok küçük bir başlangıç arabelleği boyutu ayarlarsanız (örneğin, 10 bayt) bir arabellek boyutunu tetikler.</span><span class="sxs-lookup"><span data-stu-id="265c7-411">The JSON sample provided in the snippet triggers a buffer size increase only if you set a very small initial buffer size, for example, 10 bytes.</span></span> <span data-ttu-id="265c7-412">Başlangıçtaki arabellek boyutunu 10 olarak ayarlarsanız, `Console.WriteLine` deyimler arabellek boyutunun arttığı nedeni ve etkisini gösterir.</span><span class="sxs-lookup"><span data-stu-id="265c7-412">If you set the initial buffer size to 10, the `Console.WriteLine` statements illustrate the cause and effect of buffer size increases.</span></span> <span data-ttu-id="265c7-413">4 KB ilk arabellek boyutunda, tüm örnek JSON her biri tarafından gösterilir `Console.WriteLine` ve arabellek boyutunun hiçbir zaman artırılması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="265c7-413">At the 4KB initial buffer size, the entire sample JSON is shown by each `Console.WriteLine`, and the buffer size never has to be increased.</span></span>

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

<span data-ttu-id="265c7-414">Yukarıdaki örnek, arabelleğin ne kadar büyüeceği hakkında sınır yoktur.</span><span class="sxs-lookup"><span data-stu-id="265c7-414">The preceding example sets no limit to how big the buffer can grow.</span></span> <span data-ttu-id="265c7-415">Belirteç boyutu çok büyükse, kod bir <xref:System.OutOfMemoryException> özel durumla başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="265c7-415">If the token size is too large, the code could fail with an <xref:System.OutOfMemoryException> exception.</span></span> <span data-ttu-id="265c7-416">Bu, JSON 1 GB veya daha fazla boyuttaki bir belirteç içeriyorsa, 1 GB boyutunun, arabelleğe sığamayacak kadar büyük bir boyuta neden olduğundan bu durum oluşabilir `int32` .</span><span class="sxs-lookup"><span data-stu-id="265c7-416">This can happen if the JSON contains a token that is around 1 GB or more in size, because doubling the 1 GB size results in a size that is too large to fit into an `int32` buffer.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="265c7-417">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="265c7-417">Additional resources</span></span>

* <span data-ttu-id="265c7-418">[System.Text.Jsonbakýþ](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="265c7-418">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="265c7-419">Özel dönüştürücü yazma</span><span class="sxs-lookup"><span data-stu-id="265c7-419">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="265c7-420">[Öğesinden geçişNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="265c7-420">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="265c7-421">[İçinde DateTime ve DateTimeOffset desteğiSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="265c7-421">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="265c7-422">[System.Text.JsonAPI başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="265c7-422">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
