---
title: JSON-.NET seri hale getirme
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 5c499e7a0abcbf141b6fc68f6eb9ec8983c0a7cf
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054358"
---
# <a name="how-to-serialize-json-in-net"></a><span data-ttu-id="e0591-102">.NET ' te JSON seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="e0591-102">How to serialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e0591-103">JSON serileştirme belgeleri oluşturma aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="e0591-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="e0591-104">Bu makale tüm senaryoları kapsamamaktadır.</span><span class="sxs-lookup"><span data-stu-id="e0591-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="e0591-105">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [System. Text. JSON sorunlarını](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) , özellikle de [JSON-işlevselliği-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)etiketini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="e0591-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="e0591-106">Bu makalede, <xref:System.Text.Json> JavaScript nesne gösterimi (JSON) ve öğesinden seri hale getirmek ve seri durumdan çıkarmak için ad alanı kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e0591-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="e0591-107">Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="e0591-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="e0591-108">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="e0591-108">Namespaces</span></span>

<span data-ttu-id="e0591-109"><xref:System.Text.Json> Ad alanı tüm giriş noktalarını ve ana türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="e0591-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="e0591-110">Ad <xref:System.Text.Json.Serialization> alanı, serileştirme ve seri durumdan çıkarma ile ilgili gelişmiş senaryolar ve özelleştirme için öznitelikler ve API 'leri içerir.</span><span class="sxs-lookup"><span data-stu-id="e0591-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="e0591-111">Bu nedenle, bu makalede gösterilen kod örnekleri aşağıdaki `using` yönergelerden birini veya her ikisini de gerektirir:</span><span class="sxs-lookup"><span data-stu-id="e0591-111">Therefore the code examples shown in this article require one or both of the following `using` directives:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="e0591-112">Ad alanındaki öznitelikler Şu anda sürümünde `System.Text.Json`desteklenmemektedir. <xref:System.Runtime.Serialization></span><span class="sxs-lookup"><span data-stu-id="e0591-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="e0591-113">.NET nesnelerini JSON 'a yazma (serileştirme)</span><span class="sxs-lookup"><span data-stu-id="e0591-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="e0591-114">JSON 'yi bir dizeye yazmak için, genel tür parametresi veya genel tür çıkarımı kullanarak [Jsonserializer. Serialize](xref:System.Text.Json.JsonSerializer.Serialize*)çağırın:</span><span class="sxs-lookup"><span data-stu-id="e0591-114">To write JSON to a string, call [JsonSerializer.Serialize](xref:System.Text.Json.JsonSerializer.Serialize*), using a generic type parameter or generic type inference:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast = ... ;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="e0591-115">Aşağıda, koleksiyonları ve iç içe sınıfları içeren bir örnek türü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0591-115">Here's an example type to be serialized, which contains collections and nested classes:</span></span>

```csharp
public class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public IList<DateTimeOffset> DatesAvailable { get; set;}
    public Dictionary<string, HighLowTemperatures> TemperatureRanges { get; set; }
    public string [] SummaryWords { get; set; }
}

public class HighLowTemperatures
{
    public Temperature High { get; set; }
    public Temperature Low { get; set; }
}

public class Temperature
{
    public int DegreesCelsius { get; set; }
}
```

<span data-ttu-id="e0591-116">JSON çıktısı varsayılan olarak Mini olarak belirlenir:</span><span class="sxs-lookup"><span data-stu-id="e0591-116">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="e0591-117">Aşağıdaki örnek, biçimlendirilen aynı JSON 'ı gösterir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):</span><span class="sxs-lookup"><span data-stu-id="e0591-117">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": {
        "DegreesCelsius": 20
      },
      "Low": {
        "DegreesCelsius": -10
      }
    },
    "Hot": {
      "High": {
        "DegreesCelsius": 60
      },
      "Low": {
        "DegreesCelsius": 20
      }
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

<span data-ttu-id="e0591-118">' Nin <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemeleri, ' a <xref:System.IO.Stream>serileştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0591-118">Overloads of <xref:System.Text.Json.JsonSerializer.Serialize%2A> let you serialize to a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="e0591-119">`Stream` Aşırı yüklemelerin zaman uyumsuz sürümleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e0591-119">Async versions of the `Stream` overloads are available.</span></span>

### <a name="serialize-to-utf-8"></a><span data-ttu-id="e0591-120">UTF-8 ' e serileştirme</span><span class="sxs-lookup"><span data-stu-id="e0591-120">Serialize to UTF-8</span></span>

<span data-ttu-id="e0591-121">[Jsonserializer. SerializeToUtf8Bytes](xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes*)çağrısı:</span><span class="sxs-lookup"><span data-stu-id="e0591-121">Call [JsonSerializer.SerializeToUtf8Bytes](xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes*):</span></span>

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="e0591-122">Alternatif olarak, ' ı <xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.Utf8JsonWriter> alan bir aşırı yükleme vardır.</span><span class="sxs-lookup"><span data-stu-id="e0591-122">As an alternative, a <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is available.</span></span>

<span data-ttu-id="e0591-123">UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0591-123">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="e0591-124">Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="e0591-124">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="default-serialization-behavior"></a><span data-ttu-id="e0591-125">Varsayılan serileştirme davranışı</span><span class="sxs-lookup"><span data-stu-id="e0591-125">Default serialization behavior</span></span>

* <span data-ttu-id="e0591-126">Tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="e0591-126">All public properties are serialized.</span></span> <span data-ttu-id="e0591-127">[Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties).</span><span class="sxs-lookup"><span data-stu-id="e0591-127">You can [specify properties to exclude](#exclude-properties).</span></span>
* <span data-ttu-id="e0591-128">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERIN, ASCII aralığındaki HTML duyarlı karakterlerin yanı sıra [JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterlerle çıkar.</span><span class="sxs-lookup"><span data-stu-id="e0591-128">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes  non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="e0591-129">JSON, Mini kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="e0591-129">JSON is minified.</span></span> <span data-ttu-id="e0591-130">İsteğe bağlı olarak [JSON 'ı yazdırabilirsiniz](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="e0591-130">You can optionally [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="e0591-131">JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="e0591-131">Casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="e0591-132">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names).</span><span class="sxs-lookup"><span data-stu-id="e0591-132">You can [customize JSON name casing](#customize-json-names).</span></span>
* <span data-ttu-id="e0591-133">[Döngüsel başvurular](https://github.com/dotnet/corefx/issues/38579) algılandı ve özel durumlar oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="e0591-133">[Circular references](https://github.com/dotnet/corefx/issues/38579) are detected and exceptions thrown.</span></span>
* <span data-ttu-id="e0591-134">Alanlar hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="e0591-134">Fields are excluded.</span></span>

<span data-ttu-id="e0591-135">Desteklenen türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e0591-135">Supported types include:</span></span>

* <span data-ttu-id="e0591-136">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="e0591-136">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and boolean.</span></span>
* <span data-ttu-id="e0591-137">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="e0591-137">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="e0591-138">Tek boyutlu ve pürüzlü Diziler (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="e0591-138">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="e0591-139">`Dictionary<string,TValue>`burada, `TValue`veya birpoco.`object` `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="e0591-139">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="e0591-140">Aşağıdaki ad alanlarından [koleksiyon türleri](https://github.com/dotnet/corefx/issues/36643) :</span><span class="sxs-lookup"><span data-stu-id="e0591-140">[Collection types](https://github.com/dotnet/corefx/issues/36643) from the following namespaces:</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="e0591-141">JSON 'ı .NET Objects 'e okuma (serisini kaldırma)</span><span class="sxs-lookup"><span data-stu-id="e0591-141">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="e0591-142">Bir dizeden seri durumdan çıkarmak için, [Jsonserializer. serisini](xref:System.Text.Json.JsonSerializer.Deserialize*)çağırın:</span><span class="sxs-lookup"><span data-stu-id="e0591-142">To deserialize from a string, call [JsonSerializer.Deserialize](xref:System.Text.Json.JsonSerializer.Deserialize*):</span></span>

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="e0591-143">Bir örnek için [serileştirme](#how-to-write-net-objects-to-json-serialize) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e0591-143">For an example, see the [serialize](#how-to-write-net-objects-to-json-serialize) section.</span></span> <span data-ttu-id="e0591-144">JSON ve .NET nesnesi aynıdır, ancak yön ters çevrilir.</span><span class="sxs-lookup"><span data-stu-id="e0591-144">The JSON and .NET object are the same, but the direction is reversed.</span></span>

<span data-ttu-id="e0591-145">' Nin <xref:System.Text.Json.JsonSerializer.Deserialize*> aşırı yüklemeleri, ' `Stream`dan seri durumdan çıkarabilmeniz için</span><span class="sxs-lookup"><span data-stu-id="e0591-145">Overloads of <xref:System.Text.Json.JsonSerializer.Deserialize*> let you deserialize from a `Stream`.</span></span>  <span data-ttu-id="e0591-146">`Stream` Aşırı yüklemelerin zaman uyumsuz sürümleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="e0591-146">Async versions of the `Stream` overloads are available.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="e0591-147">UTF-8 ' den serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="e0591-147">Deserialize from UTF-8</span></span>

<span data-ttu-id="e0591-148">Bir [jsonserializer çağırın.](xref:System.Text.Json.JsonSerializer.Deserialize*) bir `Utf8JsonReader` veya `ReadOnlySpan<byte>`alan aşırı yükleme serisini kaldırma:</span><span class="sxs-lookup"><span data-stu-id="e0591-148">Call a [JsonSerializer.Deserialize](xref:System.Text.Json.JsonSerializer.Deserialize*) overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`:</span></span>

```csharp
byte[] utf8Json = ... ;

var readOnlySpan = new ReadOnlySpan<byte>(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
byte[] utf8Json = ... ;

var utf8Reader = new Utf8JsonReader(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="default-deserialization-behavior"></a><span data-ttu-id="e0591-149">Varsayılan seri kaldırma davranışı</span><span class="sxs-lookup"><span data-stu-id="e0591-149">Default deserialization behavior</span></span>

* <span data-ttu-id="e0591-150">Özellik adı eşleştirmesi büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="e0591-150">Property name matching is case-sensitive.</span></span> <span data-ttu-id="e0591-151">İsteğe bağlı olarak [büyük/küçük harf](#case-insensitive-property-matching)duyarlı belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0591-151">You can optionally specify [case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="e0591-152">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="e0591-152">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="e0591-153">Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e0591-153">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="e0591-154">[Sabit nesneler](https://github.com/dotnet/corefx/issues/38569) veya [salt okunurdur özellikleri](https://github.com/dotnet/corefx/issues/38163) seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e0591-154">Deserialization to [immutable objects](https://github.com/dotnet/corefx/issues/38569) or [read-only properties](https://github.com/dotnet/corefx/issues/38163) isn't supported.</span></span>
* <span data-ttu-id="e0591-155">Numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e0591-155">Enums are supported as numbers.</span></span>
* <span data-ttu-id="e0591-156">Alanlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e0591-156">Fields aren't supported.</span></span>
* <span data-ttu-id="e0591-157">JSON 'da açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e0591-157">Comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="e0591-158">[Yorumlara ve sondaki virgüllerin bulunmasına izin](#allow-comments-and-trailing-commas)verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0591-158">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="e0591-159">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="e0591-159">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="e0591-160">Biçimlendirilen JSON 'a serileştirme</span><span class="sxs-lookup"><span data-stu-id="e0591-160">Serialize to formatted JSON</span></span>

<span data-ttu-id="e0591-161">Doğru <xref:System.Text.Json.JsonSerializerOptions.WriteIndented> olarak ayarla:</span><span class="sxs-lookup"><span data-stu-id="e0591-161">Set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="e0591-162">Seri hale getirilecek bir örnek türü ve JSON çıktısı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0591-162">Here's an example type to be serialized and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="e0591-163">Yorumlara ve sondaki virgülleri izin ver</span><span class="sxs-lookup"><span data-stu-id="e0591-163">Allow comments and trailing commas</span></span>

<span data-ttu-id="e0591-164">Olarak ayarlayın <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling> ve true olarak <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas>ayarlayın: `JsonCommentHandling.Skip`</span><span class="sxs-lookup"><span data-stu-id="e0591-164">Set <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling> to `JsonCommentHandling.Skip`, and set <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="e0591-165">Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0591-165">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a><span data-ttu-id="e0591-166">JSON adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e0591-166">Customize JSON names</span></span>

<span data-ttu-id="e0591-167">Bu bölümde nasıl yapılacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="e0591-167">This section explains how to:</span></span>

* <span data-ttu-id="e0591-168">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e0591-168">Customize individual property names</span></span>
* <span data-ttu-id="e0591-169">Tüm özellik adlarını ortası durumuna Dönüştür</span><span class="sxs-lookup"><span data-stu-id="e0591-169">Convert all property names to camel case</span></span>
* <span data-ttu-id="e0591-170">Özel özellik adlandırma ilkesi uygulama</span><span class="sxs-lookup"><span data-stu-id="e0591-170">Implement a custom property naming policy</span></span>
* <span data-ttu-id="e0591-171">Sözlük anahtarlarını ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="e0591-171">Convert dictionary keys to camel case</span></span>

<span data-ttu-id="e0591-172">[Numaralandırmaların otomatik olarak ortası örneğine dönüştürülmesi](https://github.com/dotnet/corefx/issues/37725)desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e0591-172">There's no support for automatically [converting enums to camel case](https://github.com/dotnet/corefx/issues/37725).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="e0591-173">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="e0591-173">Customize individual property names</span></span>

<span data-ttu-id="e0591-174">Ayrı özelliklerin adını ayarlamak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0591-174">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="e0591-175">Serileştirme ve sonuç JSON için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0591-175">Here's an example type to serialize and resulting JSON:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="e0591-176">Bu öznitelik tarafından ayarlanan özellik adı:</span><span class="sxs-lookup"><span data-stu-id="e0591-176">The property name set by this attribute:</span></span>

* <span data-ttu-id="e0591-177">Serileştirme ve seri durumundan çıkarma için her iki yönde de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e0591-177">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="e0591-178">Özellik adlandırma ilkelerine göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="e0591-178">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="e0591-179">Tüm JSON Özellik adları için ortası Case kullanın</span><span class="sxs-lookup"><span data-stu-id="e0591-179">Use camel case for all JSON property names</span></span>

<span data-ttu-id="e0591-180">Ayarla <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> :`JsonNamingPolicy.CamelCase`</span><span class="sxs-lookup"><span data-stu-id="e0591-180">Set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> to `JsonNamingPolicy.CamelCase`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="e0591-181">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0591-181">Here's an example class to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="e0591-182">Ortası durum özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="e0591-182">The camel case property naming policy:</span></span>

* <span data-ttu-id="e0591-183">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e0591-183">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="e0591-184">Öznitelikleri tarafından `[JsonPropertyName]` geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="e0591-184">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="e0591-185">Özel bir JSON Özellik adlandırma ilkesi kullanma</span><span class="sxs-lookup"><span data-stu-id="e0591-185">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="e0591-186"><xref:System.Text.Json.JsonNamingPolicy.ConvertName*>Türet <xref:System.Text.Json.JsonNamingPolicy> ve geçersiz kıl:</span><span class="sxs-lookup"><span data-stu-id="e0591-186">Derive from <xref:System.Text.Json.JsonNamingPolicy> and override <xref:System.Text.Json.JsonNamingPolicy.ConvertName*>:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="e0591-187">Adlandırma <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> ilkesi sınıfınızın bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e0591-187">Set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="e0591-188">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0591-188">Here's an example class to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATUREC": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="e0591-189">JSON özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="e0591-189">The JSON property naming policy:</span></span>

* <span data-ttu-id="e0591-190">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e0591-190">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="e0591-191">Öznitelikleri tarafından `[JsonPropertyName]` geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="e0591-191">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="e0591-192">Camel durum sözlüğü anahtarları</span><span class="sxs-lookup"><span data-stu-id="e0591-192">Camel case dictionary keys</span></span>

<span data-ttu-id="e0591-193">Seri hale getirilecek bir nesnenin özelliği tür `Dictionary<string,Tvalue>`ise `string` , anahtarlar ortası duruma dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="e0591-193">If a property of an object to be serialized is of type `Dictionary<string,Tvalue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="e0591-194">Bunu yapmak için şu şekilde <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase`ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e0591-194">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="e0591-195">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0591-195">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="e0591-196">Özellik</span><span class="sxs-lookup"><span data-stu-id="e0591-196">Property</span></span> |<span data-ttu-id="e0591-197">Değer</span><span class="sxs-lookup"><span data-stu-id="e0591-197">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="e0591-198">Tarih</span><span class="sxs-lookup"><span data-stu-id="e0591-198">Date</span></span>    | <span data-ttu-id="e0591-199">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="e0591-199">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="e0591-200">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="e0591-200">TemperatureC</span></span>| <span data-ttu-id="e0591-201">25</span><span class="sxs-lookup"><span data-stu-id="e0591-201">25</span></span> |
| <span data-ttu-id="e0591-202">Özet</span><span class="sxs-lookup"><span data-stu-id="e0591-202">Summary</span></span>| <span data-ttu-id="e0591-203">kolay</span><span class="sxs-lookup"><span data-stu-id="e0591-203">Hot</span></span>|
| <span data-ttu-id="e0591-204">TemperatureRanges</span><span class="sxs-lookup"><span data-stu-id="e0591-204">TemperatureRanges</span></span> | <span data-ttu-id="e0591-205">Durgun, 20</span><span class="sxs-lookup"><span data-stu-id="e0591-205">Cold, 20</span></span><br><span data-ttu-id="e0591-206">Sık erişimli, 40</span><span class="sxs-lookup"><span data-stu-id="e0591-206">Hot, 40</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "cold": 20,
    "hot": 40
  }
}
```

<span data-ttu-id="e0591-207">Ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e0591-207">The camel case naming policy applies to serialization only.</span></span>

## <a name="exclude-properties"></a><span data-ttu-id="e0591-208">Dışlama özellikleri</span><span class="sxs-lookup"><span data-stu-id="e0591-208">Exclude properties</span></span>

<span data-ttu-id="e0591-209">Bu bölümde nasıl hariç tutulacak açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="e0591-209">This section explains how to exclude:</span></span>

* <span data-ttu-id="e0591-210">Bireysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="e0591-210">Individual properties</span></span>
* <span data-ttu-id="e0591-211">Tüm salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="e0591-211">All read-only properties</span></span>
* <span data-ttu-id="e0591-212">Tüm null değerli özellikler</span><span class="sxs-lookup"><span data-stu-id="e0591-212">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="e0591-213">Bireysel özellikleri Dışla</span><span class="sxs-lookup"><span data-stu-id="e0591-213">Exclude individual properties</span></span>

<span data-ttu-id="e0591-214">[[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e0591-214">Use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="e0591-215">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0591-215">Here's an example type to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonIgnore]
    public int WindSpeed { get; set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="e0591-216">Tüm salt okuma özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="e0591-216">Exclude all read-only properties</span></span>

<span data-ttu-id="e0591-217">Doğru <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties> olarak ayarla:</span><span class="sxs-lookup"><span data-stu-id="e0591-217">Set <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="e0591-218">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0591-218">Here's an example type to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public int WindSpeed { get; private set; }
}
```

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="e0591-219">Bu seçenek yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e0591-219">This option applies only to serialization.</span></span> <span data-ttu-id="e0591-220">Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="e0591-220">During deserialization, read-only properties are ignored by default.</span></span> <span data-ttu-id="e0591-221">Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="e0591-221">A property is read-only if it contains a public getter but not a public setter.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="e0591-222">Tüm null değer özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="e0591-222">Exclude all null value properties</span></span>

<span data-ttu-id="e0591-223">Doğru <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> olarak ayarla:</span><span class="sxs-lookup"><span data-stu-id="e0591-223">Set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="e0591-224">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e0591-224">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="e0591-225">Özellik</span><span class="sxs-lookup"><span data-stu-id="e0591-225">Property</span></span> |<span data-ttu-id="e0591-226">Değer</span><span class="sxs-lookup"><span data-stu-id="e0591-226">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="e0591-227">Tarih</span><span class="sxs-lookup"><span data-stu-id="e0591-227">Date</span></span>    | <span data-ttu-id="e0591-228">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="e0591-228">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="e0591-229">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="e0591-229">TemperatureC</span></span>| <span data-ttu-id="e0591-230">25</span><span class="sxs-lookup"><span data-stu-id="e0591-230">25</span></span> |
| <span data-ttu-id="e0591-231">Özet</span><span class="sxs-lookup"><span data-stu-id="e0591-231">Summary</span></span>| <span data-ttu-id="e0591-232">null</span><span class="sxs-lookup"><span data-stu-id="e0591-232">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="e0591-233">Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="e0591-233">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="e0591-234">Seri durumdan çıkarma sırasında, JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="e0591-234">During deserialization, null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="e0591-235">[Nullable değer türleri Için null değerler özel durumlara neden olur](https://github.com/dotnet/corefx/issues/40922).</span><span class="sxs-lookup"><span data-stu-id="e0591-235">[Null values for non-nullable value types cause exceptions](https://github.com/dotnet/corefx/issues/40922).</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="e0591-236">Büyük/küçük harfe duyarsız Özellik eşleştirme</span><span class="sxs-lookup"><span data-stu-id="e0591-236">Case-insensitive property matching</span></span>

<span data-ttu-id="e0591-237">Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar.</span><span class="sxs-lookup"><span data-stu-id="e0591-237">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="e0591-238">Bu davranışı değiştirmek için, true <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="e0591-238">To change that behavior, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> to true:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="e0591-239">Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e0591-239">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="e0591-240">Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="e0591-240">It can be deserialized into the following type that has Pascal case property names.</span></span>

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
  "summary": "Hot",
}
```

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="include-properties-of-derived-classes"></a><span data-ttu-id="e0591-241">Türetilmiş sınıfların özelliklerini Ekle</span><span class="sxs-lookup"><span data-stu-id="e0591-241">Include properties of derived classes</span></span>

<span data-ttu-id="e0591-242">Derleme zamanında seri hale getirilecek tür için belirttiğiniz zaman polimorfik serileştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e0591-242">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="e0591-243">Örneğin, bir `WeatherForecast` sınıfınız ve türetilmiş bir sınıfınız `WeatherForecastWithWind`olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="e0591-243">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
class WeatherForecastWithWind : WeatherForecast
{
    public int WindSpeed { get; set; }
}
```

<span data-ttu-id="e0591-244">Ve, derleme `Serialize` `WeatherForecast`süresi sırasında yönteminin geçirildiği veya çıkartılan tür olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="e0591-244">And suppose the type passed to, or inferred by, the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="e0591-245">Bu senaryoda, `WindSpeed` `weatherForecast` nesne gerçekten bir `WeatherForecastWithWind` nesne olsa bile Özellik serileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="e0591-245">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="e0591-246">Yalnızca temel sınıf özellikleri serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="e0591-246">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="e0591-247">Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="e0591-247">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="e0591-248">Türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="e0591-248">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="e0591-249">Çalışma zamanında türü belirtmenize `Serialize` izin veren aşırı yüklemesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="e0591-249">Call an overload of `Serialize` that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="e0591-250">Seri hale getirilecek `object`nesneyi bildirin.</span><span class="sxs-lookup"><span data-stu-id="e0591-250">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="e0591-251">Yukarıdaki örnek senaryoda, her iki yaklaşım `WindSpeed` özelliğin JSON çıktısına dahil olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="e0591-251">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a><span data-ttu-id="e0591-252">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="e0591-252">Handle overflow JSON</span></span>

<span data-ttu-id="e0591-253">Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0591-253">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="e0591-254">Örneğin, hedef türünün bu olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="e0591-254">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="e0591-255">Ve seri durumdan çıkarılacak JSON şu şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="e0591-255">And the JSON to be deserialized is this:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "temperatureC": 25,
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

<span data-ttu-id="e0591-256">Gösterilen `DatesAvailable` türde gösterilen JSON serisini kaldırırsanız, ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor.</span><span class="sxs-lookup"><span data-stu-id="e0591-256">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="e0591-257">Bu özellikler gibi ek verileri yakalamak için, [jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini veya `Dictionary<string,object>` `Dictionary<string,JsonElement>`türünde bir özelliğe uygulayın:</span><span class="sxs-lookup"><span data-stu-id="e0591-257">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    [JsonExtensionData]
    public Dictionary<string, object> ExtensionData { get; set; }
}
```

<span data-ttu-id="e0591-258">Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veri `ExtensionData` özelliğin anahtar-değer çiftleri haline gelir:</span><span class="sxs-lookup"><span data-stu-id="e0591-258">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="e0591-259">Özellik</span><span class="sxs-lookup"><span data-stu-id="e0591-259">Property</span></span> |<span data-ttu-id="e0591-260">Değer</span><span class="sxs-lookup"><span data-stu-id="e0591-260">Value</span></span>  |<span data-ttu-id="e0591-261">Notlar</span><span class="sxs-lookup"><span data-stu-id="e0591-261">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="e0591-262">Tarih</span><span class="sxs-lookup"><span data-stu-id="e0591-262">Date</span></span>    | <span data-ttu-id="e0591-263">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="e0591-263">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="e0591-264">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="e0591-264">TemperatureC</span></span>| <span data-ttu-id="e0591-265">0</span><span class="sxs-lookup"><span data-stu-id="e0591-265">0</span></span> | <span data-ttu-id="e0591-266">Büyük/küçük harfe duyarlı`temperatureC` uyuşmazlık (JSON 'da), bu nedenle özellik ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="e0591-266">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="e0591-267">Özet</span><span class="sxs-lookup"><span data-stu-id="e0591-267">Summary</span></span> | <span data-ttu-id="e0591-268">kolay</span><span class="sxs-lookup"><span data-stu-id="e0591-268">Hot</span></span> ||
| <span data-ttu-id="e0591-269">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="e0591-269">ExtensionData</span></span> | <span data-ttu-id="e0591-270">temperatureC: 25</span><span class="sxs-lookup"><span data-stu-id="e0591-270">temperatureC: 25</span></span> |<span data-ttu-id="e0591-271">Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.</span><span class="sxs-lookup"><span data-stu-id="e0591-271">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="e0591-272">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="e0591-272">DatesAvailable:</span></span><br>  <span data-ttu-id="e0591-273">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="e0591-273">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="e0591-274">8/2/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="e0591-274">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="e0591-275">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="e0591-275">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="e0591-276">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="e0591-276">SummaryWords:</span></span><br><span data-ttu-id="e0591-277">İyi</span><span class="sxs-lookup"><span data-stu-id="e0591-277">Cool</span></span><br><span data-ttu-id="e0591-278">Rüzgarlı</span><span class="sxs-lookup"><span data-stu-id="e0591-278">Windy</span></span><br><span data-ttu-id="e0591-279">İnsankimliği</span><span class="sxs-lookup"><span data-stu-id="e0591-279">Humid</span></span> |<span data-ttu-id="e0591-280">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="e0591-280">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="e0591-281">Hedef nesne serileştirildiğinde, uzantı veri anahtarı değer çiftleri, gelen JSON 'da olduğu gibi JSON özellikleri olur:</span><span class="sxs-lookup"><span data-stu-id="e0591-281">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 0,
  "Summary": "Hot",
  "temperatureC": 25,
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

<span data-ttu-id="e0591-282">`ExtensionData` Özellik adının JSON içinde görünmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="e0591-282">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="e0591-283">Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e0591-283">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="use-utf8jsonwriter-directly"></a><span data-ttu-id="e0591-284">Doğrudan Utf8JsonWriter kullanma</span><span class="sxs-lookup"><span data-stu-id="e0591-284">Use Utf8JsonWriter directly</span></span>

<span data-ttu-id="e0591-285">Aşağıdaki örnek <xref:System.Text.Json.Utf8JsonWriter> sınıfının doğrudan nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0591-285">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class directly.</span></span>

```csharp
var options = new JsonWriterOptions
{
    Indented = true
};

using (var stream = new MemoryStream())
{
    using (var writer = new Utf8JsonWriter(stream, options))
    {
        writer.WriteStartObject();
        writer.WriteString("date", DateTimeOffset.UtcNow);
        writer.WriteNumber("temp", 42);
        writer.WriteEndObject();
    }

    string json = Encoding.UTF8.GetString(stream.ToArray());
    Console.WriteLine(json);
}
```

## <a name="use-utf8jsonreader-directly"></a><span data-ttu-id="e0591-286">Doğrudan Utf8JsonReader kullanma</span><span class="sxs-lookup"><span data-stu-id="e0591-286">Use Utf8JsonReader directly</span></span>

<span data-ttu-id="e0591-287">Aşağıdaki örnek <xref:System.Text.Json.Utf8JsonReader> sınıfının doğrudan nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0591-287">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class directly.</span></span> <span data-ttu-id="e0591-288">Kod, `jsonUtf8` değişkenin UTF-8 olarak kodlanmış geçerli JSON içeren bir bayt dizisi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="e0591-288">The code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

```csharp
Utf8JsonReader reader = new Utf8JsonReader(jsonUtf8, isFinalBlock: true, state: default);

while (reader.Read())
{
    Console.Write(reader.TokenType);

    switch (reader.TokenType)
    {
        case JsonTokenType.PropertyName:
        case JsonTokenType.String:
            {
                string text = reader.GetString();
                Console.Write(" ");
                Console.Write(text);
                break;
            }

        case JsonTokenType.Number:
            {
                int value = reader.GetInt32();
                Console.Write(" ");
                Console.Write(value);
                break;
            }

            // Other token types elided for brevity
    }

    Console.WriteLine();
}
```

## <a name="additional-resources"></a><span data-ttu-id="e0591-289">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="e0591-289">Additional resources</span></span>

* [<span data-ttu-id="e0591-290">System. Text. JSON genel bakış</span><span class="sxs-lookup"><span data-stu-id="e0591-290">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="e0591-291">System. Text. JSON API başvurusu</span><span class="sxs-lookup"><span data-stu-id="e0591-291">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="e0591-292">System. Text. JSON içinde DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="e0591-292">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
