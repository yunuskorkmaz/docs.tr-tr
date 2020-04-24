---
title: C#-.NET kullanarak JSON serileştirmek ve serisini kaldırma
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 6324fe28b23e4df74bcf3fd1dbb7e0c14d5e3d1b
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135808"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="51f0c-102">.NET içinde JSON ve seri hale getirme (sıralama ve kaldırma)</span><span class="sxs-lookup"><span data-stu-id="51f0c-102">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="51f0c-103">Bu makalede, <xref:System.Text.Json> JAVASCRIPT nesne GÖSTERIMI (JSON) ve öğesinden seri hale getirmek ve seri durumdan çıkarmak için ad alanı kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-103">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="51f0c-104">İçinden `Newtonsoft.Json`mevcut kodu aktarıyorsanız, bkz. [nasıl geçiş `System.Text.Json`yapılacağı ](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="51f0c-104">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="51f0c-105">Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-105">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="51f0c-106">Serileştirme örnek kodunun çoğu, JSON ( <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> girintileme `true` ve insanlar okunabilirlik için boşluk) olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-106">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="51f0c-107">Üretim kullanımı için genellikle bu ayar `false` için varsayılan değerini kabul etmiş olursunuz.</span><span class="sxs-lookup"><span data-stu-id="51f0c-107">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="51f0c-108">Kod örnekleri, aşağıdaki sınıfa ve türevlerini ifade eder:</span><span class="sxs-lookup"><span data-stu-id="51f0c-108">The code examples refer to the following class and variants of it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a><span data-ttu-id="51f0c-109">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="51f0c-109">Namespaces</span></span>

<span data-ttu-id="51f0c-110"><xref:System.Text.Json> Ad alanı tüm giriş noktalarını ve ana türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-110">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="51f0c-111">Ad <xref:System.Text.Json.Serialization> alanı, serileştirme ve seri durumdan çıkarma ile ilgili gelişmiş senaryolar ve özelleştirme için öznitelikler ve API 'leri içerir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-111">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="51f0c-112">Bu makalede gösterilen kod örnekleri, bu ad `using` alanlarından biri veya her ikisi için yönergeler gerektirir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-112">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="51f0c-113"><xref:System.Runtime.Serialization> Ad alanındaki öznitelikler Şu anda sürümünde `System.Text.Json`desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-113">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="51f0c-114">.NET nesnelerini JSON 'a yazma (serileştirme)</span><span class="sxs-lookup"><span data-stu-id="51f0c-114">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="51f0c-115">JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-115">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="51f0c-116">Aşağıdaki örnek bir dize olarak JSON oluşturur:</span><span class="sxs-lookup"><span data-stu-id="51f0c-116">The following example creates JSON as a string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

<span data-ttu-id="51f0c-117">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="51f0c-117">The following example uses synchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

<span data-ttu-id="51f0c-118">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="51f0c-118">The following example uses asynchronous code to create a JSON file:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

<span data-ttu-id="51f0c-119">Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-119">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="51f0c-120">Öğesinin `Serialize()` aşırı yüklemesi genel bir tür parametresi alır:</span><span class="sxs-lookup"><span data-stu-id="51f0c-120">An overload of `Serialize()` takes a generic type parameter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a><span data-ttu-id="51f0c-121">Serileştirme örneği</span><span class="sxs-lookup"><span data-stu-id="51f0c-121">Serialization example</span></span>

<span data-ttu-id="51f0c-122">Aşağıda, koleksiyonları ve iç içe yerleştirilmiş bir sınıfı içeren örnek bir sınıf verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-122">Here's an example class that contains collections and a nested class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

<span data-ttu-id="51f0c-123">Önceki türün bir örneğinin serileştirilmesi için JSON çıktısı aşağıdaki örnekteki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="51f0c-123">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="51f0c-124">JSON çıktısı varsayılan olarak Mini olarak belirlenir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-124">The JSON output is minified by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="51f0c-125">Aşağıdaki örnek, biçimlendirilen aynı JSON 'ı gösterir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):</span><span class="sxs-lookup"><span data-stu-id="51f0c-125">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="51f0c-126">UTF-8 ' e serileştirme</span><span class="sxs-lookup"><span data-stu-id="51f0c-126">Serialize to UTF-8</span></span>

<span data-ttu-id="51f0c-127">UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-127">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<span data-ttu-id="51f0c-128">' <xref:System.Text.Json.JsonSerializer.Serialize%2A> İ alan <xref:System.Text.Json.Utf8JsonWriter> bir aşırı yükleme de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="51f0c-128">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="51f0c-129">UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-129">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="51f0c-130">Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="51f0c-130">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="51f0c-131">Serileştirme davranışı</span><span class="sxs-lookup"><span data-stu-id="51f0c-131">Serialization behavior</span></span>

* <span data-ttu-id="51f0c-132">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-132">By default, all public properties are serialized.</span></span> <span data-ttu-id="51f0c-133">[Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="51f0c-133">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="51f0c-134">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-134">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="51f0c-135">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-135">By default, JSON is minified.</span></span> <span data-ttu-id="51f0c-136">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51f0c-136">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="51f0c-137">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-137">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="51f0c-138">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="51f0c-138">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="51f0c-139">Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="51f0c-139">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="51f0c-140">Şu anda, alanlar hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="51f0c-140">Currently, fields are excluded.</span></span>

<span data-ttu-id="51f0c-141">Desteklenen türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="51f0c-141">Supported types include:</span></span>

* <span data-ttu-id="51f0c-142">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="51f0c-142">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="51f0c-143">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="51f0c-143">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="51f0c-144">Tek boyutlu ve pürüzlü Diziler (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="51f0c-144">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="51f0c-145">`Dictionary<string,TValue>``object`burada, veya bir poco `TValue` `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="51f0c-145">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="51f0c-146">Aşağıdaki ad alanlarından Koleksiyonlar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-146">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="51f0c-147">Ek türleri işlemek veya yerleşik dönüştürücüler tarafından desteklenmeyen işlevler sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="51f0c-147">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="51f0c-148">JSON 'ı .NET Objects 'e okuma (serisini kaldırma)</span><span class="sxs-lookup"><span data-stu-id="51f0c-148">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="51f0c-149">Bir dizeden veya dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-149">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="51f0c-150">Aşağıdaki örnek, bir dizeden JSON okur ve daha önce [serileştirme örneği](#serialization-example)için gösterilen `WeatherForecast` sınıfının bir örneğini oluşturur:</span><span class="sxs-lookup"><span data-stu-id="51f0c-150">The following example reads JSON from a string and creates an instance of the `WeatherForecast` class shown earlier for the [serialization example](#serialization-example):</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

<span data-ttu-id="51f0c-151">Zaman uyumlu kod kullanarak bir dosyadan seri durumdan çıkarmak için, aşağıdaki örnekte gösterildiği gibi dosyayı bir dizeye okuyun:</span><span class="sxs-lookup"><span data-stu-id="51f0c-151">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

<span data-ttu-id="51f0c-152">Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-152">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="51f0c-153">UTF-8 ' den serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="51f0c-153">Deserialize from UTF-8</span></span>

<span data-ttu-id="51f0c-154">UTF-8 ' den seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> , aşağıdaki örneklerde gösterildiği `Utf8JsonReader` gibi bir `ReadOnlySpan<byte>`veya içeren bir aşırı yükleme çağırın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-154">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="51f0c-155">Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-155">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a><span data-ttu-id="51f0c-156">Seri durumdan çıkarma davranışı</span><span class="sxs-lookup"><span data-stu-id="51f0c-156">Deserialization behavior</span></span>

* <span data-ttu-id="51f0c-157">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-157">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="51f0c-158">[Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="51f0c-158">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="51f0c-159">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="51f0c-159">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="51f0c-160">Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="51f0c-160">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="51f0c-161">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="51f0c-161">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="51f0c-162">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-162">By default, enums are supported as numbers.</span></span> <span data-ttu-id="51f0c-163">[Enum adlarını dizeler olarak seri hale](#enums-as-strings)getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51f0c-163">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="51f0c-164">Alanlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="51f0c-164">Fields aren't supported.</span></span>
* <span data-ttu-id="51f0c-165">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51f0c-165">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="51f0c-166">[Yorumlara ve sondaki virgüllerin bulunmasına izin](#allow-comments-and-trailing-commas)verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51f0c-166">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="51f0c-167">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-167">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="51f0c-168">Yerleşik dönüştürücüler tarafından desteklenmeyen işlevselliği sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="51f0c-168">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="51f0c-169">Biçimlendirilen JSON 'a serileştirme</span><span class="sxs-lookup"><span data-stu-id="51f0c-169">Serialize to formatted JSON</span></span>

<span data-ttu-id="51f0c-170">JSON çıkışını gerçekten yazdırmak için şu şekilde <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true`ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-170">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

<span data-ttu-id="51f0c-171">Aşağıda, seri hale getirilebilir ve düzgün şekilde yazdırılan JSON çıkışının örnek bir türü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-171">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a><span data-ttu-id="51f0c-172">JSON adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="51f0c-172">Customize JSON names and values</span></span>

<span data-ttu-id="51f0c-173">Varsayılan olarak, özellik adları ve sözlük anahtarları, büyük/küçük harf gibi JSON çıktısında değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="51f0c-173">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="51f0c-174">Sabit listesi değerleri sayı olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-174">Enum values are represented as numbers.</span></span> <span data-ttu-id="51f0c-175">Bu bölümde nasıl yapılacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="51f0c-175">This section explains how to:</span></span>

* [<span data-ttu-id="51f0c-176">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="51f0c-176">Customize individual property names</span></span>](#customize-individual-property-names)
* [<span data-ttu-id="51f0c-177">Tüm özellik adlarını ortası durumuna Dönüştür</span><span class="sxs-lookup"><span data-stu-id="51f0c-177">Convert all property names to camel case</span></span>](#use-camel-case-for-all-json-property-names)
* [<span data-ttu-id="51f0c-178">Özel özellik adlandırma ilkesi uygulama</span><span class="sxs-lookup"><span data-stu-id="51f0c-178">Implement a custom property naming policy</span></span>](#use-a-custom-json-property-naming-policy)
* [<span data-ttu-id="51f0c-179">Sözlük anahtarlarını ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="51f0c-179">Convert dictionary keys to camel case</span></span>](#camel-case-dictionary-keys)
* [<span data-ttu-id="51f0c-180">Numaralandırmaları dizelere ve ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="51f0c-180">Convert enums to strings and camel case</span></span>](#enums-as-strings)

<span data-ttu-id="51f0c-181">JSON özellik adlarını ve değerlerini özel olarak işleme gerektiren diğer senaryolar için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="51f0c-181">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="51f0c-182">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="51f0c-182">Customize individual property names</span></span>

<span data-ttu-id="51f0c-183">Ayrı özelliklerin adını ayarlamak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-183">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="51f0c-184">Serileştirme ve sonuç JSON için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-184">Here's an example type to serialize and resulting JSON:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="51f0c-185">Bu öznitelik tarafından ayarlanan özellik adı:</span><span class="sxs-lookup"><span data-stu-id="51f0c-185">The property name set by this attribute:</span></span>

* <span data-ttu-id="51f0c-186">Serileştirme ve seri durumundan çıkarma için her iki yönde de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-186">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="51f0c-187">Özellik adlandırma ilkelerine göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-187">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="51f0c-188">Tüm JSON Özellik adları için ortası Case kullanın</span><span class="sxs-lookup"><span data-stu-id="51f0c-188">Use camel case for all JSON property names</span></span>

<span data-ttu-id="51f0c-189">Tüm JSON Özellik adları için ortası durumunu kullanmak için, aşağıdaki <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> örnekte `JsonNamingPolicy.CamelCase`gösterildiği gibi olarak ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="51f0c-189">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

<span data-ttu-id="51f0c-190">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-190">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="51f0c-191">Ortası durum özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="51f0c-191">The camel case property naming policy:</span></span>

* <span data-ttu-id="51f0c-192">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-192">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="51f0c-193">Öznitelikleri tarafından `[JsonPropertyName]` geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-193">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="51f0c-194">Bu nedenle, örnekteki JSON Özellik adının `Wind` ortası durum olmaması neden olur.</span><span class="sxs-lookup"><span data-stu-id="51f0c-194">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="51f0c-195">Özel bir JSON Özellik adlandırma ilkesi kullanma</span><span class="sxs-lookup"><span data-stu-id="51f0c-195">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="51f0c-196">Özel bir JSON Özellik adlandırma ilkesi kullanmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonNamingPolicy> <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> yönteminden türeten bir sınıf oluşturun ve yöntemi geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-196">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

<span data-ttu-id="51f0c-197">Daha sonra özelliği <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> , adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-197">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

<span data-ttu-id="51f0c-198">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-198">Here's an example class to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="51f0c-199">JSON özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="51f0c-199">The JSON property naming policy:</span></span>

* <span data-ttu-id="51f0c-200">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-200">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="51f0c-201">Öznitelikleri tarafından `[JsonPropertyName]` geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-201">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="51f0c-202">Bu, örnekteki JSON Özellik adının `Wind` büyük harfle değil.</span><span class="sxs-lookup"><span data-stu-id="51f0c-202">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="51f0c-203">Camel durum sözlüğü anahtarları</span><span class="sxs-lookup"><span data-stu-id="51f0c-203">Camel case dictionary keys</span></span>

<span data-ttu-id="51f0c-204">Seri hale getirilecek bir nesnenin özelliği tür `Dictionary<string,TValue>`ise, `string` anahtarlar ortası duruma dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-204">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="51f0c-205">Bunu yapmak için, aşağıdaki <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> örnekte `JsonNamingPolicy.CamelCase`gösterildiği gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-205">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

<span data-ttu-id="51f0c-206">Anahtar-değer çiftlerine `TemperatureRanges` `"ColdMinTemp", 20` sahip adlı bir sözlük ile bir nesneyi serileştirmek ve `"HotMinTemp", 40` aşağıdaki örnekte olduğu gibi JSON çıktısına neden olur:</span><span class="sxs-lookup"><span data-stu-id="51f0c-206">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

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

<span data-ttu-id="51f0c-207">Sözlük anahtarları için ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-207">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="51f0c-208">Bir sözlüğün serisini kaldırırsanız, için belirtseniz `JsonNamingPolicy.CamelCase` bıle anahtarlar JSON dosyasıyla eşleşir. `DictionaryKeyPolicy`</span><span class="sxs-lookup"><span data-stu-id="51f0c-208">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="51f0c-209">Dizeler dize olarak numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="51f0c-209">Enums as strings</span></span>

<span data-ttu-id="51f0c-210">Varsayılan olarak, numaralandırmalar sayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-210">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="51f0c-211">Sabit listesi adlarını dizeler olarak seri hale getirmek için <xref:System.Text.Json.Serialization.JsonStringEnumConverter>öğesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-211">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="51f0c-212">Örneğin, bir sabit listesi olan aşağıdaki sınıfı seri hale getirmeniz gerektiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="51f0c-212">For example, suppose you need to serialize the following class that has an enum:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

<span data-ttu-id="51f0c-213">Özet ise `Hot`, varsayılan olarak serileştirilmiş JSON sayısal değer 3 ' ü içerir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-213">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

<span data-ttu-id="51f0c-214">Aşağıdaki örnek kod, sayısal değerler yerine enum adlarını seri hale getirir ve adları ortası örneğine dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="51f0c-214">The following sample code serializes the enum names instead of the numeric values, and converts the names to camel case:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

<span data-ttu-id="51f0c-215">Elde edilen JSON aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="51f0c-215">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="51f0c-216">Aşağıdaki örnekte gösterildiği gibi, sabit listesi dize adları da seri durumdan çıkarılmış olabilir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-216">Enum string names can be deserialized as well, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="51f0c-217">Özellikleri serileştirme dışında tut</span><span class="sxs-lookup"><span data-stu-id="51f0c-217">Exclude properties from serialization</span></span>

<span data-ttu-id="51f0c-218">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-218">By default, all public properties are serialized.</span></span> <span data-ttu-id="51f0c-219">Bir kısmının JSON çıktısında görünmesini istemiyorsanız, birkaç seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-219">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="51f0c-220">Bu bölümde nasıl hariç tutulacak açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="51f0c-220">This section explains how to exclude:</span></span>

* [<span data-ttu-id="51f0c-221">Bireysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="51f0c-221">Individual properties</span></span>](#exclude-individual-properties)
* [<span data-ttu-id="51f0c-222">Tüm salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="51f0c-222">All read-only properties</span></span>](#exclude-all-read-only-properties)
* [<span data-ttu-id="51f0c-223">Tüm null değerli özellikler</span><span class="sxs-lookup"><span data-stu-id="51f0c-223">All null-value properties</span></span>](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a><span data-ttu-id="51f0c-224">Bireysel özellikleri Dışla</span><span class="sxs-lookup"><span data-stu-id="51f0c-224">Exclude individual properties</span></span>

<span data-ttu-id="51f0c-225">Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-225">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="51f0c-226">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-226">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="51f0c-227">Tüm salt okuma özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="51f0c-227">Exclude all read-only properties</span></span>

<span data-ttu-id="51f0c-228">Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="51f0c-228">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="51f0c-229">Tüm salt okunurdur özelliklerini hariç tutmak için, aşağıdaki örnekte <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> gösterildiği `true`gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-229">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="51f0c-230">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-230">Here's an example type to serialize and JSON output:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="51f0c-231">Bu seçenek yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-231">This option applies only to serialization.</span></span> <span data-ttu-id="51f0c-232">Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-232">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="51f0c-233">Tüm null değer özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="51f0c-233">Exclude all null value properties</span></span>

<span data-ttu-id="51f0c-234">Tüm null değer özelliklerini dışlamak için, aşağıdaki örnekte <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> gösterildiği gibi `true`özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-234">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

<span data-ttu-id="51f0c-235">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-235">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="51f0c-236">Özellik</span><span class="sxs-lookup"><span data-stu-id="51f0c-236">Property</span></span> |<span data-ttu-id="51f0c-237">Değer</span><span class="sxs-lookup"><span data-stu-id="51f0c-237">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="51f0c-238">Tarih</span><span class="sxs-lookup"><span data-stu-id="51f0c-238">Date</span></span>    | <span data-ttu-id="51f0c-239">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="51f0c-239">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="51f0c-240">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="51f0c-240">TemperatureCelsius</span></span>| <span data-ttu-id="51f0c-241">25</span><span class="sxs-lookup"><span data-stu-id="51f0c-241">25</span></span> |
| <span data-ttu-id="51f0c-242">Özet</span><span class="sxs-lookup"><span data-stu-id="51f0c-242">Summary</span></span>| <span data-ttu-id="51f0c-243">null</span><span class="sxs-lookup"><span data-stu-id="51f0c-243">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

<span data-ttu-id="51f0c-244">Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-244">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="51f0c-245">Seri durumdan çıkarma üzerindeki etkisi hakkında daha fazla bilgi için bkz. [serisi kaldırılırken null değeri yoksay](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="51f0c-245">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="51f0c-246">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="51f0c-246">Customize character encoding</span></span>

<span data-ttu-id="51f0c-247">Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-247">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="51f0c-248">Diğer bir deyişle, bu, karakterin `\uxxxx` Unicode `xxxx` kodunun bulunduğu konum ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-248">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="51f0c-249">Örneğin, `Summary` özelliği Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-249">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="51f0c-250">Dil karakter kümelerini serileştirme</span><span class="sxs-lookup"><span data-stu-id="51f0c-250">Serialize language character sets</span></span>

<span data-ttu-id="51f0c-251">Bir veya daha fazla dilin karakter kümesini kaçış olmadan seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi bir örneği <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin:</span><span class="sxs-lookup"><span data-stu-id="51f0c-251">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

<span data-ttu-id="51f0c-252">Bu kod, Kiril veya Yunan karakterlerinden kaçış yapmaz.</span><span class="sxs-lookup"><span data-stu-id="51f0c-252">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="51f0c-253">`Summary` Özellik Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-253">If the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="51f0c-254">Tüm dil kümelerini kaçış olmadan seri hale getirmek için <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>kullanın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-254">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="51f0c-255">Belirli karakterleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="51f0c-255">Serialize specific characters</span></span>

<span data-ttu-id="51f0c-256">Diğer bir seçenek de, kaçırılmadan, izin vermek istediğiniz tek tek karakterleri belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-256">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="51f0c-257">Aşağıdaki örnek, жарко 'in yalnızca ilk iki karakterini seri hale getirir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-257">The following example serializes only the first two characters of жарко:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

<span data-ttu-id="51f0c-258">Yukarıdaki kod tarafından üretilen JSON örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-258">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="51f0c-259">Tüm karakterleri seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="51f0c-259">Serialize all characters</span></span>

<span data-ttu-id="51f0c-260">Aşağıdaki örnekte gösterildiği gibi, kullanarak <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>kaçı en aza indirin:</span><span class="sxs-lookup"><span data-stu-id="51f0c-260">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> <span data-ttu-id="51f0c-261">Varsayılan kodlayıcıyla karşılaştırıldığında `UnsafeRelaxedJsonEscaping` kodlayıcı, karakterlerin kaçışsız geçmesine izin verme konusunda daha fazla izne sahiptir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-261">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="51f0c-262">, `<`, Ve `>` `&` `'`gibi HTML 'ye duyarlı karakterleri atmaz.</span><span class="sxs-lookup"><span data-stu-id="51f0c-262">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="51f0c-263">Bu, XSS veya bilgi açıklama saldırılarına karşı ek derinlemesine savunma korumaları sunmaz, örneğin, *karakter*kümesinde istemci ve sunucu disagreeing neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-263">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="51f0c-264">Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-264">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="51f0c-265">Örneğin, sunucu yanıt üst bilgisini `Content-Type: application/json; charset=utf-8`gönderiyorsa onu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51f0c-265">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="51f0c-266">Ham `UnsafeRelaxedJsonEscaping` ÇıKıŞıN bir HTML sayfasına veya bir `<script>` öğeye yayılmasın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-266">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="51f0c-267">Türetilmiş sınıfların serileştirme özellikleri</span><span class="sxs-lookup"><span data-stu-id="51f0c-267">Serialize properties of derived classes</span></span>

<span data-ttu-id="51f0c-268">Çok biçimli bir tür hiyerarşisinin serileştirilmesi desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="51f0c-268">Serialization of a polymorphic type hierarchy is not supported.</span></span> <span data-ttu-id="51f0c-269">Örneğin, bir özellik bir arabirim ya da soyut sınıf olarak tanımlanmışsa, çalışma zamanı türü ek özelliklere sahip olsa bile yalnızca arabirim veya soyut sınıf üzerinde tanımlanan özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-269">For example, if a property is defined as an interface or an abstract class, only the properties defined on the interface or abstract class are serialized, even if the runtime type has additional properties.</span></span> <span data-ttu-id="51f0c-270">Bu davranışın istisnaları, bu bölümde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-270">The exceptions to this behavior are explained in this section.</span></span>

<span data-ttu-id="51f0c-271">Örneğin, bir `WeatherForecast` sınıfınız ve türetilmiş bir sınıfınız `WeatherForecastDerived`olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="51f0c-271">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastDerived`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

<span data-ttu-id="51f0c-272">Ve derleme zamanında `Serialize` yöntemin tür bağımsız değişkeninin şu olduğunu `WeatherForecast`varsayalım:</span><span class="sxs-lookup"><span data-stu-id="51f0c-272">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

<span data-ttu-id="51f0c-273">Bu senaryoda, `WindSpeed` `weatherForecast` nesne gerçekten bir `WeatherForecastDerived` nesne olsa bile Özellik serileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="51f0c-273">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastDerived` object.</span></span> <span data-ttu-id="51f0c-274">Yalnızca temel sınıf özellikleri serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-274">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="51f0c-275">Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-275">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="51f0c-276">Yukarıdaki örnekteki türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-276">To serialize the properties of the derived type in the preceding example, use one of the following approaches:</span></span>

* <span data-ttu-id="51f0c-277">Çalışma zamanında türü belirtmenize <xref:System.Text.Json.JsonSerializer.Serialize%2A> izin veren aşırı yüklemesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-277">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* <span data-ttu-id="51f0c-278">Seri hale getirilecek nesneyi bildirin `object`.</span><span class="sxs-lookup"><span data-stu-id="51f0c-278">Declare the object to be serialized as `object`.</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

<span data-ttu-id="51f0c-279">Yukarıdaki örnek senaryoda, her iki yaklaşım `WindSpeed` özelliğin JSON çıktısına dahil olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="51f0c-279">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> <span data-ttu-id="51f0c-280">Bu yaklaşımlar yalnızca kök nesnenin seri hale getirilmesi için, bu kök nesnenin özellikleri için değil, polimorfik serileştirme sağlar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-280">These approaches provide polymorphic serialization only for the root object to be serialized, not for properties of that root object.</span></span>

<span data-ttu-id="51f0c-281">Bunları tür `object`olarak tanımlarsanız alt düzey nesneler için polimorfik serileştirme alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51f0c-281">You can get polymorphic serialization for lower-level objects if you define them as type `object`.</span></span> <span data-ttu-id="51f0c-282">Örneğin, `WeatherForecast` sınıfınızın, tür `PreviousForecast` `WeatherForecast` olarak tanımlanabilen adında bir özelliği olduğunu varsayalım: `object`</span><span class="sxs-lookup"><span data-stu-id="51f0c-282">For example, suppose your `WeatherForecast` class has a property named `PreviousForecast` that can be defined as type `WeatherForecast` or `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

<span data-ttu-id="51f0c-283">`PreviousForecast` Özelliği bir örneği içeriyorsa `WeatherForecastDerived`:</span><span class="sxs-lookup"><span data-stu-id="51f0c-283">If the `PreviousForecast` property contains an instance of `WeatherForecastDerived`:</span></span>

* <span data-ttu-id="51f0c-284">Serileştirmede `WeatherForecastWithPrevious` JSON çıktısı **içermez** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="51f0c-284">The JSON output from serializing `WeatherForecastWithPrevious` **doesn't include** `WindSpeed`.</span></span>
* <span data-ttu-id="51f0c-285">Serileştirmede `WeatherForecastWithPreviousAsObject` JSON çıktısı **dahildir** `WindSpeed`.</span><span class="sxs-lookup"><span data-stu-id="51f0c-285">The JSON output from serializing `WeatherForecastWithPreviousAsObject` **includes** `WindSpeed`.</span></span>

<span data-ttu-id="51f0c-286">Seri hale `WeatherForecastWithPreviousAsObject`getirmek için, ya `Serialize<object>` `GetType` da kök nesnesi türetilmiş bir tür olabilecek bir nesne olmadığından çağırmak gerekmez.</span><span class="sxs-lookup"><span data-stu-id="51f0c-286">To serialize `WeatherForecastWithPreviousAsObject`, it isn't necessary to call `Serialize<object>` or `GetType` because the root object isn't the one that may be of a derived type.</span></span> <span data-ttu-id="51f0c-287">Aşağıdaki kod örneği, veya `Serialize<object>` `GetType`çağırmaz:</span><span class="sxs-lookup"><span data-stu-id="51f0c-287">The following code example doesn't call `Serialize<object>` or `GetType`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

<span data-ttu-id="51f0c-288">Yukarıdaki kod doğru şekilde serileştirir `WeatherForecastWithPreviousAsObject`:</span><span class="sxs-lookup"><span data-stu-id="51f0c-288">The preceding code correctly serializes `WeatherForecastWithPreviousAsObject`:</span></span>

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

<span data-ttu-id="51f0c-289">Özellikleri `object` , arabirimler ile birlikte tanımlamaya yönelik aynı yaklaşım.</span><span class="sxs-lookup"><span data-stu-id="51f0c-289">The same approach of defining properties as `object` works with interfaces.</span></span> <span data-ttu-id="51f0c-290">Aşağıdaki arabirime ve uygulamaya sahip olduğunuzu ve uygulama örnekleri içeren özelliklerle bir sınıfı seri hale getirmek istediğinizi varsayalım:</span><span class="sxs-lookup"><span data-stu-id="51f0c-290">Suppose you have the following interface and implementation, and you want to serialize a class with properties that contain implementation instances:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

<span data-ttu-id="51f0c-291">Bir `Forecasts`örneğini serileştirçalıştığınızda, yalnızca `Tuesday` `WindSpeed` özelliğini gösterir, çünkü `Tuesday` şu şekilde `object`tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="51f0c-291">When you serialize an instance of `Forecasts`, only `Tuesday` shows the `WindSpeed` property, because `Tuesday` is defined as `object`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

<span data-ttu-id="51f0c-292">Aşağıdaki örnek, önceki koddan elde edilen JSON 'u göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-292">The following example shows the JSON that results from the preceding code:</span></span>

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

<span data-ttu-id="51f0c-293">Polimorfik **serileştirme**hakkında daha fazla bilgi edinmek ve **serisini kaldırma**hakkında bilgi Için, bkz. [Newtonsoft. JSON 'Dan System. Text. JSON 'a geçiş](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span><span class="sxs-lookup"><span data-stu-id="51f0c-293">For more information about polymorphic **serialization**, and for information about **deserialization**, see [How to migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="51f0c-294">Yorumlara ve sondaki virgülleri izin ver</span><span class="sxs-lookup"><span data-stu-id="51f0c-294">Allow comments and trailing commas</span></span>

<span data-ttu-id="51f0c-295">Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="51f0c-295">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="51f0c-296">JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini olarak `JsonCommentHandling.Skip`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-296">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span>
<span data-ttu-id="51f0c-297">Ve sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-297">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="51f0c-298">Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-298">The following example shows how to allow both:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

<span data-ttu-id="51f0c-299">Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-299">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="51f0c-300">Büyük/küçük harfe duyarsız Özellik eşleştirme</span><span class="sxs-lookup"><span data-stu-id="51f0c-300">Case-insensitive property matching</span></span>

<span data-ttu-id="51f0c-301">Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-301">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="51f0c-302">Bu davranışı değiştirmek için şu şekilde <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> `true`ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-302">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

<span data-ttu-id="51f0c-303">Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-303">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="51f0c-304">Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-304">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a><span data-ttu-id="51f0c-305">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="51f0c-305">Handle overflow JSON</span></span>

<span data-ttu-id="51f0c-306">Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="51f0c-306">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="51f0c-307">Örneğin, hedef türünün bu olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="51f0c-307">For example, suppose your target type is this:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="51f0c-308">Ve seri durumdan çıkarılacak JSON şu şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="51f0c-308">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="51f0c-309">Gösterilen türde gösterilen JSON serisini kaldırırsanız, `DatesAvailable` ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor.</span><span class="sxs-lookup"><span data-stu-id="51f0c-309">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="51f0c-310">Bu özellikler gibi ek verileri yakalamak için, [Jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini veya `Dictionary<string,object>` `Dictionary<string,JsonElement>`türünde bir özelliğe uygulayın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-310">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

<span data-ttu-id="51f0c-311">Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veri `ExtensionData` özelliğin anahtar-değer çiftleri haline gelir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-311">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="51f0c-312">Özellik</span><span class="sxs-lookup"><span data-stu-id="51f0c-312">Property</span></span> |<span data-ttu-id="51f0c-313">Değer</span><span class="sxs-lookup"><span data-stu-id="51f0c-313">Value</span></span>  |<span data-ttu-id="51f0c-314">Notlar</span><span class="sxs-lookup"><span data-stu-id="51f0c-314">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="51f0c-315">Tarih</span><span class="sxs-lookup"><span data-stu-id="51f0c-315">Date</span></span>    | <span data-ttu-id="51f0c-316">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="51f0c-316">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="51f0c-317">TemperatureCelsius</span><span class="sxs-lookup"><span data-stu-id="51f0c-317">TemperatureCelsius</span></span>| <span data-ttu-id="51f0c-318">0</span><span class="sxs-lookup"><span data-stu-id="51f0c-318">0</span></span> | <span data-ttu-id="51f0c-319">Büyük/küçük harfe duyarlı`temperatureCelsius` UYUŞMAZLıK (JSON 'da), bu nedenle özellik ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="51f0c-319">Case-sensitive mismatch (`temperatureCelsius` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="51f0c-320">Özet</span><span class="sxs-lookup"><span data-stu-id="51f0c-320">Summary</span></span> | <span data-ttu-id="51f0c-321">Sık Erişimli</span><span class="sxs-lookup"><span data-stu-id="51f0c-321">Hot</span></span> ||
| <span data-ttu-id="51f0c-322">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="51f0c-322">ExtensionData</span></span> | <span data-ttu-id="51f0c-323">temperatureCelsius: 25</span><span class="sxs-lookup"><span data-stu-id="51f0c-323">temperatureCelsius: 25</span></span> |<span data-ttu-id="51f0c-324">Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.</span><span class="sxs-lookup"><span data-stu-id="51f0c-324">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="51f0c-325">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="51f0c-325">DatesAvailable:</span></span><br>  <span data-ttu-id="51f0c-326">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="51f0c-326">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="51f0c-327">8/2/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="51f0c-327">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="51f0c-328">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-328">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="51f0c-329">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="51f0c-329">SummaryWords:</span></span><br><span data-ttu-id="51f0c-330">Seyrek Erişimli</span><span class="sxs-lookup"><span data-stu-id="51f0c-330">Cool</span></span><br><span data-ttu-id="51f0c-331">Rüzgarlı</span><span class="sxs-lookup"><span data-stu-id="51f0c-331">Windy</span></span><br><span data-ttu-id="51f0c-332">İnsankimliği</span><span class="sxs-lookup"><span data-stu-id="51f0c-332">Humid</span></span> |<span data-ttu-id="51f0c-333">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-333">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="51f0c-334">Hedef nesne serileştirildiğinde, uzantı veri anahtarı değer çiftleri, gelen JSON 'da olduğu gibi JSON özellikleri olur:</span><span class="sxs-lookup"><span data-stu-id="51f0c-334">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="51f0c-335">`ExtensionData` ÖZELLIK adının JSON içinde görünmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="51f0c-335">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="51f0c-336">Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-336">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="51f0c-337">Seri durumdan çıkarılırken null değeri yoksay</span><span class="sxs-lookup"><span data-stu-id="51f0c-337">Ignore null when deserializing</span></span>

<span data-ttu-id="51f0c-338">Varsayılan olarak, JSON 'daki bir özellik null ise, hedef nesnedeki karşılık gelen özellik null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-338">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="51f0c-339">Bazı senaryolarda, target özelliği varsayılan bir değere sahip olabilir ve varsayılan değeri geçersiz kılmak için null değer istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="51f0c-339">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="51f0c-340">Örneğin, aşağıdaki kodun hedef nesneniz temsil ettiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="51f0c-340">For example, suppose the following code represents your target object:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

<span data-ttu-id="51f0c-341">Ve aşağıdaki JSON öğesinin seri durumdan çıkarıldığını varsayalım:</span><span class="sxs-lookup"><span data-stu-id="51f0c-341">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

<span data-ttu-id="51f0c-342">Seri durumdan çıktıktan sonra `Summary` , `WeatherForecastWithDefault` nesnesinin özelliği null olur.</span><span class="sxs-lookup"><span data-stu-id="51f0c-342">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="51f0c-343">Bu davranışı değiştirmek için, aşağıdaki <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> örnekte `true`gösterildiği gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="51f0c-343">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

<span data-ttu-id="51f0c-344">Bu seçenekle `Summary` `WeatherForecastWithDefault` nesnenin özelliği, serisini kaldırma işleminden sonra varsayılan "Özet yok" değeridir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-344">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="51f0c-345">JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-345">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="51f0c-346">Nullable değer türleri için null değerler özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="51f0c-346">Null values for non-nullable value types cause exceptions.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="51f0c-347">Utf8JsonReader, Utf8JsonWriter ve JsonDocument</span><span class="sxs-lookup"><span data-stu-id="51f0c-347">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="51f0c-348"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>, bir veya `ReadOnlySpan<byte>` `ReadOnlySequence<byte>`' dan okunan UTF-8 kodlu JSON metin için yüksek performanslı, düşük bir ayırma, Salt ilet okuyucu olur.</span><span class="sxs-lookup"><span data-stu-id="51f0c-348"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>` or `ReadOnlySequence<byte>`.</span></span> <span data-ttu-id="51f0c-349">, `Utf8JsonReader` Özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="51f0c-349">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="51f0c-350"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> Yöntemi, kapakların altında kullanır `Utf8JsonReader` .</span><span class="sxs-lookup"><span data-stu-id="51f0c-350">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="51f0c-351"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>, `String` `Int32`ve `DateTime`gibi ortak .net türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="51f0c-351"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="51f0c-352">Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="51f0c-352">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="51f0c-353"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> Yöntemi, kapakların altında kullanır `Utf8JsonWriter` .</span><span class="sxs-lookup"><span data-stu-id="51f0c-353">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="51f0c-354"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>kullanarak `Utf8JsonReader`salt okunurdur belge nesne MODELI (DOM) oluşturma yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-354"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="51f0c-355">DOM, bir JSON yükünde verilere rastgele erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-355">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="51f0c-356">Yükü oluşturan JSON öğelerine <xref:System.Text.Json.JsonElement> tür aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-356">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="51f0c-357">Türü `JsonElement` , JSON metnini ortak .net türlerine dönüştürmek için API 'lerle birlikte dizi ve nesne numaralandırıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-357">The `JsonElement` type provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="51f0c-358">`JsonDocument`bir <xref:System.Text.Json.JsonDocument.RootElement> özellik sunar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-358">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="51f0c-359">Aşağıdaki bölümlerde, bu araçların JSON okuma ve yazma için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-359">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="51f0c-360">Veri erişimi için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="51f0c-360">Use JsonDocument for access to data</span></span>

<span data-ttu-id="51f0c-361">Aşağıdaki örnek, bir JSON dizesindeki verilere rastgele <xref:System.Text.Json.JsonDocument> erişim için sınıfının nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-361">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data in a JSON string:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

<span data-ttu-id="51f0c-362">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="51f0c-362">The preceding code:</span></span>

* <span data-ttu-id="51f0c-363">Analiz edilecek JSON 'in adlı `jsonString`bir dizede olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-363">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="51f0c-364">`Grade` Özelliği olan bir `Students` dizideki nesneler için Ortalama bir sınıf hesaplar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-364">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span>
* <span data-ttu-id="51f0c-365">Bir sınıfa sahip olmayan öğrenciler için varsayılan bir 70 sınıfı atar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-365">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="51f0c-366">Her yinelemeyle bir `count` değişkeni arttırarak öğrencileri sayar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-366">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="51f0c-367">Aşağıdaki örnekte gösterildiği gibi bir <xref:System.Text.Json.JsonElement.GetArrayLength%2A>alternatif çağrdır:</span><span class="sxs-lookup"><span data-stu-id="51f0c-367">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>, as shown in the following example:</span></span>

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

<span data-ttu-id="51f0c-368">Bu kodun işlediği JSON örneğine bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-368">Here's an example of the JSON that this code processes:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="51f0c-369">JSON yazmak için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="51f0c-369">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="51f0c-370">Aşağıdaki örnek, öğesinden nasıl JSON yazılacağını göstermektedir <xref:System.Text.Json.JsonDocument>:</span><span class="sxs-lookup"><span data-stu-id="51f0c-370">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

<span data-ttu-id="51f0c-371">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="51f0c-371">The preceding code:</span></span>

* <span data-ttu-id="51f0c-372">Bir JSON dosyasını okur, verileri bir `JsonDocument`dosyasına yükler ve bir dosyaya biçimli (düzgün YAZDıRıLMıŞ) JSON yazar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-372">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="51f0c-373">JSON <xref:System.Text.Json.JsonDocumentOptions> girişi içindeki açıklamalara izin verildiğini ancak yok sayılacağını belirtmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-373">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="51f0c-374">İşiniz bittiğinde, yazıcı <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> üzerindeki çağrılar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-374">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="51f0c-375">Diğer bir seçenek de yazıcı boşaltıatıldığı zaman yazıcının temizlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-375">An alternative is to let the writer autoflush when it's disposed.</span></span>

<span data-ttu-id="51f0c-376">Örnek kod tarafından işlenecek JSON girişi örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-376">Here's an example of JSON input to be processed by the example code:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

<span data-ttu-id="51f0c-377">Sonuç, aşağıdaki düzgün yazdırılmış JSON çıktıdır:</span><span class="sxs-lookup"><span data-stu-id="51f0c-377">The result is the following pretty-printed JSON output:</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="51f0c-378">Utf8JsonWriter kullanma</span><span class="sxs-lookup"><span data-stu-id="51f0c-378">Use Utf8JsonWriter</span></span>

<span data-ttu-id="51f0c-379">Aşağıdaki örnek <xref:System.Text.Json.Utf8JsonWriter> sınıfının nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-379">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a><span data-ttu-id="51f0c-380">Utf8JsonReader kullanma</span><span class="sxs-lookup"><span data-stu-id="51f0c-380">Use Utf8JsonReader</span></span>

<span data-ttu-id="51f0c-381">Aşağıdaki örnek <xref:System.Text.Json.Utf8JsonReader> sınıfının nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-381">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

<span data-ttu-id="51f0c-382">Yukarıdaki kod, `jsonUtf8` değişkenin UTF-8 olarak KODLANMıŞ geçerli JSON içeren bir bayt dizisi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-382">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="51f0c-383">Utf8JsonReader kullanarak verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="51f0c-383">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="51f0c-384">Aşağıdaki örnek, bir dosyanın zaman uyumlu olarak nasıl okunacağını ve bir değerin nasıl aranacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-384">The following example shows how to read a file synchronously and search for a value:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

<span data-ttu-id="51f0c-385">Yukarıdaki kod:</span><span class="sxs-lookup"><span data-stu-id="51f0c-385">The preceding code:</span></span>

* <span data-ttu-id="51f0c-386">JSON 'un bir nesne dizisi içerdiğini ve her nesne dize türünde bir "ad" özelliği içerebildiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="51f0c-386">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="51f0c-387">"University" ile biten nesneleri ve "ad" özellik değerlerini sayar.</span><span class="sxs-lookup"><span data-stu-id="51f0c-387">Counts objects and "name" property values that end with "University".</span></span>
* <span data-ttu-id="51f0c-388">Dosyanın UTF-16 olarak kodlandığını varsayar ve bunu UTF-8 ' e dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="51f0c-388">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="51f0c-389">Aşağıdaki kod kullanılarak UTF-8 olarak kodlanmış bir dosya doğrudan bir `ReadOnlySpan<byte>`ile okunabilir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-389">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  <span data-ttu-id="51f0c-390">Dosya bir UTF-8 bayt sırası işareti (BOM) içeriyorsa, okuyucu metin gerektirdiğinden, baytları öğesine `Utf8JsonReader`geçirmeden önce kaldırın.</span><span class="sxs-lookup"><span data-stu-id="51f0c-390">If the file contains a UTF-8 byte order mark (BOM), remove it before passing the bytes to the `Utf8JsonReader`, since the reader expects text.</span></span> <span data-ttu-id="51f0c-391">Aksi takdirde, BOM geçersiz JSON olarak değerlendirilir ve okuyucu bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="51f0c-391">Otherwise, the BOM is considered invalid JSON, and the reader throws an exception.</span></span>

<span data-ttu-id="51f0c-392">Yukarıdaki kodun okuya, bir JSON örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="51f0c-392">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="51f0c-393">Sonuçtaki Özet ileti "2 ' den 4 ' ün" University "ile biten adlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="51f0c-393">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a><span data-ttu-id="51f0c-394">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="51f0c-394">Additional resources</span></span>

* <span data-ttu-id="51f0c-395">[System.Text.Jsonbakýþ](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="51f0c-395">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* [<span data-ttu-id="51f0c-396">Özel dönüştürücü yazma</span><span class="sxs-lookup"><span data-stu-id="51f0c-396">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* <span data-ttu-id="51f0c-397">[Öğesinden geçişNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="51f0c-397">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="51f0c-398">[İçinde DateTime ve DateTimeOffset desteğiSystem.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="51f0c-398">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="51f0c-399">[System.Text.JsonAPI başvurusu](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="51f0c-399">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
