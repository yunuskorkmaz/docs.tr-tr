---
title: JSON-.NET seri hale getirme
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 8ccd7afe4abb928e7723aa740507774012fc85d1
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71083106"
---
# <a name="how-to-serialize-json-in-net"></a><span data-ttu-id="cfffd-102">.NET ' te JSON seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="cfffd-102">How to serialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="cfffd-103">JSON serileştirme belgeleri oluşturma aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="cfffd-104">Bu makale tüm senaryoları kapsamamaktadır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="cfffd-105">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [System. Text. JSON sorunlarını](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) , özellikle de [JSON-işlevselliği-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)etiketini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="cfffd-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="cfffd-106">Bu makalede, <xref:System.Text.Json> JavaScript nesne gösterimi (JSON) ve öğesinden seri hale getirmek ve seri durumdan çıkarmak için ad alanı kullanımı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="cfffd-107">Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="cfffd-108">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="cfffd-108">Namespaces</span></span>

<span data-ttu-id="cfffd-109"><xref:System.Text.Json> Ad alanı tüm giriş noktalarını ve ana türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="cfffd-110">Ad <xref:System.Text.Json.Serialization> alanı, serileştirme ve seri durumdan çıkarma ile ilgili gelişmiş senaryolar ve özelleştirme için öznitelikler ve API 'leri içerir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="cfffd-111">Bu nedenle, bu makalede gösterilen kod örnekleri aşağıdaki `using` yönergelerden birini veya her ikisini de gerektirir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-111">Therefore, the code examples shown in this article require one or both of the following `using` directives:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="cfffd-112">Ad alanındaki öznitelikler Şu anda sürümünde `System.Text.Json`desteklenmemektedir. <xref:System.Runtime.Serialization></span><span class="sxs-lookup"><span data-stu-id="cfffd-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="cfffd-113">.NET nesnelerini JSON 'a yazma (serileştirme)</span><span class="sxs-lookup"><span data-stu-id="cfffd-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="cfffd-114">JSON 'yi bir dizeye yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="cfffd-114">To write JSON to a string, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cfffd-115">Aşağıdaki örnek genel tür parametresiyle bir aşırı yükleme kullanır:</span><span class="sxs-lookup"><span data-stu-id="cfffd-115">The following example uses an overload with a generic type parameter:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="cfffd-116">Genel tür parametresini atlayabilir ve bunun yerine genel tür çıkarımı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cfffd-116">You can omit the generic type parameter and use generic type inference instead:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="cfffd-117">Aşağıda, koleksiyonları ve iç içe sınıfları içeren bir örnek türü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-117">Here's an example type to be serialized, which contains collections and nested classes:</span></span>

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

<span data-ttu-id="cfffd-118">JSON çıktısı varsayılan olarak Mini olarak belirlenir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-118">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="cfffd-119">Aşağıdaki örnek, biçimlendirilen aynı JSON 'ı gösterir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):</span><span class="sxs-lookup"><span data-stu-id="cfffd-119">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

<span data-ttu-id="cfffd-120">' Nin <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemeleri, ' a <xref:System.IO.Stream>serileştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfffd-120">Overloads of <xref:System.Text.Json.JsonSerializer.Serialize%2A> let you serialize to a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="cfffd-121">`Stream` Aşırı yüklemelerin zaman uyumsuz sürümleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="cfffd-121">Async versions of the `Stream` overloads are available.</span></span>

### <a name="serialize-to-utf-8"></a><span data-ttu-id="cfffd-122">UTF-8 ' e serileştirme</span><span class="sxs-lookup"><span data-stu-id="cfffd-122">Serialize to UTF-8</span></span>

<span data-ttu-id="cfffd-123">UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-123">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="cfffd-124">Alternatif olarak, ' ı <xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.Utf8JsonWriter> alan bir aşırı yükleme vardır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-124">As an alternative, a <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is available.</span></span>

<span data-ttu-id="cfffd-125">UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-125">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="cfffd-126">Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="cfffd-126">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="cfffd-127">Serileştirme davranışı</span><span class="sxs-lookup"><span data-stu-id="cfffd-127">Serialization behavior</span></span>

* <span data-ttu-id="cfffd-128">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-128">By default, all public properties are serialized.</span></span> <span data-ttu-id="cfffd-129">[Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties).</span><span class="sxs-lookup"><span data-stu-id="cfffd-129">You can [specify properties to exclude](#exclude-properties).</span></span>
* <span data-ttu-id="cfffd-130">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERIN, ASCII aralığındaki HTML duyarlı karakterlerin yanı sıra [JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterlerle çıkar.</span><span class="sxs-lookup"><span data-stu-id="cfffd-130">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="cfffd-131">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-131">By default, JSON is minified.</span></span> <span data-ttu-id="cfffd-132">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfffd-132">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="cfffd-133">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-133">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="cfffd-134">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names).</span><span class="sxs-lookup"><span data-stu-id="cfffd-134">You can [customize JSON name casing](#customize-json-names).</span></span>
* <span data-ttu-id="cfffd-135">Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="cfffd-135">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="cfffd-136">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposunda [Döngüsel başvurularda sorun](https://github.com/dotnet/corefx/issues/38579) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cfffd-136">For more information, see the [issue on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="cfffd-137">Şu anda, alanlar hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="cfffd-137">Currently, fields are excluded.</span></span>

<span data-ttu-id="cfffd-138">Desteklenen türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="cfffd-138">Supported types include:</span></span>

* <span data-ttu-id="cfffd-139">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="cfffd-139">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="cfffd-140">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="cfffd-140">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="cfffd-141">Tek boyutlu ve pürüzlü Diziler (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="cfffd-141">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="cfffd-142">`Dictionary<string,TValue>`burada, `TValue`veya birpoco.`object` `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="cfffd-142">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="cfffd-143">Aşağıdaki ad alanlarından Koleksiyonlar.</span><span class="sxs-lookup"><span data-stu-id="cfffd-143">Collections from the following namespaces.</span></span> <span data-ttu-id="cfffd-144">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [koleksiyon desteği sorunu](https://github.com/dotnet/corefx/issues/36643) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cfffd-144">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="cfffd-145">JSON 'ı .NET Objects 'e okuma (serisini kaldırma)</span><span class="sxs-lookup"><span data-stu-id="cfffd-145">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="cfffd-146">Bir dizeden seri durumdan çıkarmak için aşağıdaki örnekte <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> gösterildiği gibi yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-146">To deserialize from a string, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method, as shown in the following example:</span></span>

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="cfffd-147">Bir örnek için [serileştirme](#how-to-write-net-objects-to-json-serialize) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cfffd-147">For an example, see the [serialize](#how-to-write-net-objects-to-json-serialize) section.</span></span> <span data-ttu-id="cfffd-148">JSON ve .NET nesnesi aynıdır, ancak yön ters çevrilir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-148">The JSON and .NET object are the same, but the direction is reversed.</span></span>

<span data-ttu-id="cfffd-149">' Nin <xref:System.Text.Json.JsonSerializer.Deserialize*> aşırı yüklemeleri, ' `Stream`dan seri durumdan çıkarabilmeniz için</span><span class="sxs-lookup"><span data-stu-id="cfffd-149">Overloads of <xref:System.Text.Json.JsonSerializer.Deserialize*> let you deserialize from a `Stream`.</span></span>  <span data-ttu-id="cfffd-150">`Stream` Aşırı yüklemelerin zaman uyumsuz sürümleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="cfffd-150">Async versions of the `Stream` overloads are available.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="cfffd-151">UTF-8 ' den serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="cfffd-151">Deserialize from UTF-8</span></span>

<span data-ttu-id="cfffd-152">UTF-8 ' den seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> , aşağıdaki örneklerde gösterildiği `Utf8JsonReader` gibi bir `ReadOnlySpan<byte>`veya içeren bir aşırı yükleme çağırın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-152">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples:</span></span>

```csharp
byte[] utf8Json;
//...
var readOnlySpan = new ReadOnlySpan<byte>(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
byte[] utf8Json;
//...
var utf8Reader = new Utf8JsonReader(utf8Json);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a><span data-ttu-id="cfffd-153">Seri durumdan çıkarma davranışı</span><span class="sxs-lookup"><span data-stu-id="cfffd-153">Deserialization behavior</span></span>

* <span data-ttu-id="cfffd-154">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-154">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="cfffd-155">[Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="cfffd-155">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="cfffd-156">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="cfffd-156">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="cfffd-157">Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cfffd-157">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="cfffd-158">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cfffd-158">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="cfffd-159">Daha fazla bilgi için bkz. [sabit nesne desteğiyle Ilgili GitHub sorunu](https://github.com/dotnet/corefx/issues/38569) ve GitHub 'daki DotNet/corefx deposundaki [salt okunurdur özellik desteği](https://github.com/dotnet/corefx/issues/38163) .</span><span class="sxs-lookup"><span data-stu-id="cfffd-159">For more information, see the GitHub [issue on immutable object support](https://github.com/dotnet/corefx/issues/38569) and the [issue on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="cfffd-160">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-160">By default, enums are supported as numbers.</span></span>
* <span data-ttu-id="cfffd-161">Alanlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="cfffd-161">Fields aren't supported.</span></span>
* <span data-ttu-id="cfffd-162">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cfffd-162">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="cfffd-163">Gerekirse [açıklamalara ve sondaki virgüllerin belirtilmesine izin](#allow-comments-and-trailing-commas) verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfffd-163">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas) if needed.</span></span>
* <span data-ttu-id="cfffd-164">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-164">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="cfffd-165">Biçimlendirilen JSON 'a serileştirme</span><span class="sxs-lookup"><span data-stu-id="cfffd-165">Serialize to formatted JSON</span></span>

<span data-ttu-id="cfffd-166">JSON çıkışını gerçekten yazdırmak için şu şekilde <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true`ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-166">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cfffd-167">Seri hale getirilecek bir örnek türü ve JSON çıktısı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-167">Here's an example type to be serialized and JSON output:</span></span>

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

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="cfffd-168">Yorumlara ve sondaki virgülleri izin ver</span><span class="sxs-lookup"><span data-stu-id="cfffd-168">Allow comments and trailing commas</span></span>

<span data-ttu-id="cfffd-169">JSON 'da varsayılan açıklamalara ve sondaki virgüllerin kullanımına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="cfffd-169">By default comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="cfffd-170">JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini olarak `JsonCommentHandling.Skip`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cfffd-170">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span> <span data-ttu-id="cfffd-171">Ve sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini olarak `true`ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="cfffd-171">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="cfffd-172">Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-172">The following example shows how to allow both:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="cfffd-173">Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-173">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a><span data-ttu-id="cfffd-174">JSON adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cfffd-174">Customize JSON names</span></span>

<span data-ttu-id="cfffd-175">Varsayılan olarak, özellik adları ve sözlük anahtarları, büyük/küçük harf gibi JSON çıktısında değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="cfffd-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="cfffd-176">Bu bölümde nasıl yapılacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="cfffd-176">This section explains how to:</span></span>

* <span data-ttu-id="cfffd-177">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cfffd-177">Customize individual property names</span></span>
* <span data-ttu-id="cfffd-178">Tüm özellik adlarını ortası durumuna Dönüştür</span><span class="sxs-lookup"><span data-stu-id="cfffd-178">Convert all property names to camel case</span></span>
* <span data-ttu-id="cfffd-179">Özel özellik adlandırma ilkesi uygulama</span><span class="sxs-lookup"><span data-stu-id="cfffd-179">Implement a custom property naming policy</span></span>
* <span data-ttu-id="cfffd-180">Sözlük anahtarlarını ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="cfffd-180">Convert dictionary keys to camel case</span></span>

<span data-ttu-id="cfffd-181">Şu anda, Numaralandırmaların otomatik olarak ortası örneğine dönüştürülmesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cfffd-181">Currently, there's no support for automatically converting enums to camel case.</span></span> <span data-ttu-id="cfffd-182">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposunda [kamel durum desteğinin numaralandırmasında sorun](https://github.com/dotnet/corefx/issues/37725) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cfffd-182">For more information, see the [issue on enum camel case support](https://github.com/dotnet/corefx/issues/37725) in the dotnet/corefx repository on GitHub.</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="cfffd-183">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="cfffd-183">Customize individual property names</span></span>

<span data-ttu-id="cfffd-184">Ayrı özelliklerin adını ayarlamak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfffd-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="cfffd-185">Serileştirme ve sonuç JSON için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-185">Here's an example type to serialize and resulting JSON:</span></span>

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

<span data-ttu-id="cfffd-186">Bu öznitelik tarafından ayarlanan özellik adı:</span><span class="sxs-lookup"><span data-stu-id="cfffd-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="cfffd-187">Serileştirme ve seri durumundan çıkarma için her iki yönde de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="cfffd-188">Özellik adlandırma ilkelerine göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="cfffd-189">Tüm JSON Özellik adları için ortası Case kullanın</span><span class="sxs-lookup"><span data-stu-id="cfffd-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="cfffd-190">Tüm JSON Özellik adları için ortası durumunu kullanmak için, aşağıdaki <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> örnekte `JsonNamingPolicy.CamelCase`gösterildiği gibi olarak ayarlanır:</span><span class="sxs-lookup"><span data-stu-id="cfffd-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cfffd-191">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-191">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="cfffd-192">Ortası durum özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="cfffd-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="cfffd-193">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="cfffd-194">Öznitelikleri tarafından `[JsonPropertyName]` geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-194">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="cfffd-195">Özel bir JSON Özellik adlandırma ilkesi kullanma</span><span class="sxs-lookup"><span data-stu-id="cfffd-195">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="cfffd-196">Özel bir JSON Özellik adlandırma ilkesi kullanmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonNamingPolicy> <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> yönteminden türeten bir sınıf oluşturun ve yöntemi geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-196">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="cfffd-197">Daha sonra özelliği <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> , adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-197">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cfffd-198">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-198">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="cfffd-199">JSON özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="cfffd-199">The JSON property naming policy:</span></span>

* <span data-ttu-id="cfffd-200">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-200">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="cfffd-201">Öznitelikleri tarafından `[JsonPropertyName]` geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-201">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="cfffd-202">Camel durum sözlüğü anahtarları</span><span class="sxs-lookup"><span data-stu-id="cfffd-202">Camel case dictionary keys</span></span>

<span data-ttu-id="cfffd-203">Seri hale getirilecek bir nesnenin özelliği tür `Dictionary<string,TValue>`ise `string` , anahtarlar ortası duruma dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-203">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="cfffd-204">Bunu yapmak için, aşağıdaki <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> örnekte `JsonNamingPolicy.CamelCase`gösterildiği gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-204">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cfffd-205">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-205">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="cfffd-206">Özellik</span><span class="sxs-lookup"><span data-stu-id="cfffd-206">Property</span></span> |<span data-ttu-id="cfffd-207">Değer</span><span class="sxs-lookup"><span data-stu-id="cfffd-207">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="cfffd-208">Tarih</span><span class="sxs-lookup"><span data-stu-id="cfffd-208">Date</span></span>    | <span data-ttu-id="cfffd-209">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="cfffd-209">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="cfffd-210">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="cfffd-210">TemperatureC</span></span>| <span data-ttu-id="cfffd-211">25</span><span class="sxs-lookup"><span data-stu-id="cfffd-211">25</span></span> |
| <span data-ttu-id="cfffd-212">Özet</span><span class="sxs-lookup"><span data-stu-id="cfffd-212">Summary</span></span>| <span data-ttu-id="cfffd-213">kolay</span><span class="sxs-lookup"><span data-stu-id="cfffd-213">Hot</span></span>|
| <span data-ttu-id="cfffd-214">TemperatureRanges</span><span class="sxs-lookup"><span data-stu-id="cfffd-214">TemperatureRanges</span></span> | <span data-ttu-id="cfffd-215">Durgun, 20</span><span class="sxs-lookup"><span data-stu-id="cfffd-215">Cold, 20</span></span><br><span data-ttu-id="cfffd-216">Sık erişimli, 40</span><span class="sxs-lookup"><span data-stu-id="cfffd-216">Hot, 40</span></span>|

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

<span data-ttu-id="cfffd-217">Ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-217">The camel case naming policy applies to serialization only.</span></span>

## <a name="exclude-properties"></a><span data-ttu-id="cfffd-218">Dışlama özellikleri</span><span class="sxs-lookup"><span data-stu-id="cfffd-218">Exclude properties</span></span>

<span data-ttu-id="cfffd-219">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="cfffd-220">Bir kısmının JSON çıktısında görünmesini istemiyorsanız, birkaç seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="cfffd-221">Bu bölümde nasıl hariç tutulacak açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="cfffd-221">This section explains how to exclude:</span></span>

* <span data-ttu-id="cfffd-222">Bireysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="cfffd-222">Individual properties</span></span>
* <span data-ttu-id="cfffd-223">Tüm salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="cfffd-223">All read-only properties</span></span>
* <span data-ttu-id="cfffd-224">Tüm null değerli özellikler</span><span class="sxs-lookup"><span data-stu-id="cfffd-224">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="cfffd-225">Bireysel özellikleri Dışla</span><span class="sxs-lookup"><span data-stu-id="cfffd-225">Exclude individual properties</span></span>

<span data-ttu-id="cfffd-226">Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="cfffd-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="cfffd-227">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-227">Here's an example type to serialize and JSON output:</span></span>

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

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="cfffd-228">Tüm salt okuma özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="cfffd-228">Exclude all read-only properties</span></span>

<span data-ttu-id="cfffd-229">Tüm salt okunurdur özelliklerini hariç tutmak için, aşağıdaki örnekte <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> gösterildiği `true`gibi öğesini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-229">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cfffd-230">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-230">Here's an example type to serialize and JSON output:</span></span>

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

<span data-ttu-id="cfffd-231">Bu seçenek yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-231">This option applies only to serialization.</span></span> <span data-ttu-id="cfffd-232">Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-232">During deserialization, read-only properties are ignored by default.</span></span> <span data-ttu-id="cfffd-233">Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="cfffd-233">A property is read-only if it contains a public getter but not a public setter.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="cfffd-234">Tüm null değer özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="cfffd-234">Exclude all null value properties</span></span>

<span data-ttu-id="cfffd-235">Tüm null değer özelliklerini dışlamak için, aşağıdaki örnekte <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> gösterildiği gibi `true`özelliğini olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="cfffd-236">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="cfffd-237">Özellik</span><span class="sxs-lookup"><span data-stu-id="cfffd-237">Property</span></span> |<span data-ttu-id="cfffd-238">Değer</span><span class="sxs-lookup"><span data-stu-id="cfffd-238">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="cfffd-239">Tarih</span><span class="sxs-lookup"><span data-stu-id="cfffd-239">Date</span></span>    | <span data-ttu-id="cfffd-240">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="cfffd-240">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="cfffd-241">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="cfffd-241">TemperatureC</span></span>| <span data-ttu-id="cfffd-242">25</span><span class="sxs-lookup"><span data-stu-id="cfffd-242">25</span></span> |
| <span data-ttu-id="cfffd-243">Özet</span><span class="sxs-lookup"><span data-stu-id="cfffd-243">Summary</span></span>| <span data-ttu-id="cfffd-244">null</span><span class="sxs-lookup"><span data-stu-id="cfffd-244">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="cfffd-245">Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-245">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="cfffd-246">Seri durumdan çıkarma sırasında, JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-246">During deserialization, null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="cfffd-247">Nullable değer türleri için null değerler özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="cfffd-247">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="cfffd-248">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [null yapılamayan değer türlerinde sorun](https://github.com/dotnet/corefx/issues/40922) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="cfffd-248">For more information, see the [issue on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="cfffd-249">Büyük/küçük harfe duyarsız Özellik eşleştirme</span><span class="sxs-lookup"><span data-stu-id="cfffd-249">Case-insensitive property matching</span></span>

<span data-ttu-id="cfffd-250">Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar.</span><span class="sxs-lookup"><span data-stu-id="cfffd-250">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="cfffd-251">Bu davranışı değiştirmek için, <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> öğesini olarak `true`ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-251">To change that behavior, set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="cfffd-252">Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-252">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="cfffd-253">Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-253">It can be deserialized into the following type that has Pascal case property names.</span></span>

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

## <a name="include-properties-of-derived-classes"></a><span data-ttu-id="cfffd-254">Türetilmiş sınıfların özelliklerini Ekle</span><span class="sxs-lookup"><span data-stu-id="cfffd-254">Include properties of derived classes</span></span>

<span data-ttu-id="cfffd-255">Derleme zamanında seri hale getirilecek tür için belirttiğiniz zaman polimorfik serileştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="cfffd-255">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="cfffd-256">Örneğin, bir `WeatherForecast` sınıfınız ve türetilmiş bir sınıfınız `WeatherForecastWithWind`olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="cfffd-256">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

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

<span data-ttu-id="cfffd-257">Ve, derleme `Serialize` `WeatherForecast`süresi sırasında yönteminin geçirildiği veya çıkartılan tür olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="cfffd-257">And suppose the type passed to, or inferred by, the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="cfffd-258">Bu senaryoda, `WindSpeed` `weatherForecast` nesne gerçekten bir `WeatherForecastWithWind` nesne olsa bile Özellik serileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="cfffd-258">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="cfffd-259">Yalnızca temel sınıf özellikleri serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-259">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="cfffd-260">Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="cfffd-260">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="cfffd-261">Türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-261">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="cfffd-262">Çalışma zamanında türü belirtmenize <xref:System.Text.Json.JsonSerializer.Serialize%2A> izin veren aşırı yüklemesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-262">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="cfffd-263">Seri hale getirilecek `object`nesneyi bildirin.</span><span class="sxs-lookup"><span data-stu-id="cfffd-263">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="cfffd-264">Yukarıdaki örnek senaryoda, her iki yaklaşım `WindSpeed` özelliğin JSON çıktısına dahil olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="cfffd-264">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a><span data-ttu-id="cfffd-265">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="cfffd-265">Handle overflow JSON</span></span>

<span data-ttu-id="cfffd-266">Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cfffd-266">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="cfffd-267">Örneğin, hedef türünün bu olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="cfffd-267">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="cfffd-268">Ve seri durumdan çıkarılacak JSON şu şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="cfffd-268">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="cfffd-269">Gösterilen `DatesAvailable` türde gösterilen JSON serisini kaldırırsanız, ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor.</span><span class="sxs-lookup"><span data-stu-id="cfffd-269">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="cfffd-270">Bu özellikler gibi ek verileri yakalamak için, [jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini veya `Dictionary<string,object>` `Dictionary<string,JsonElement>`türünde bir özelliğe uygulayın:</span><span class="sxs-lookup"><span data-stu-id="cfffd-270">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

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

<span data-ttu-id="cfffd-271">Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veri `ExtensionData` özelliğin anahtar-değer çiftleri haline gelir:</span><span class="sxs-lookup"><span data-stu-id="cfffd-271">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="cfffd-272">Özellik</span><span class="sxs-lookup"><span data-stu-id="cfffd-272">Property</span></span> |<span data-ttu-id="cfffd-273">Değer</span><span class="sxs-lookup"><span data-stu-id="cfffd-273">Value</span></span>  |<span data-ttu-id="cfffd-274">Notlar</span><span class="sxs-lookup"><span data-stu-id="cfffd-274">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="cfffd-275">Tarih</span><span class="sxs-lookup"><span data-stu-id="cfffd-275">Date</span></span>    | <span data-ttu-id="cfffd-276">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="cfffd-276">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="cfffd-277">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="cfffd-277">TemperatureC</span></span>| <span data-ttu-id="cfffd-278">0</span><span class="sxs-lookup"><span data-stu-id="cfffd-278">0</span></span> | <span data-ttu-id="cfffd-279">Büyük/küçük harfe duyarlı`temperatureC` uyuşmazlık (JSON 'da), bu nedenle özellik ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="cfffd-279">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="cfffd-280">Özet</span><span class="sxs-lookup"><span data-stu-id="cfffd-280">Summary</span></span> | <span data-ttu-id="cfffd-281">kolay</span><span class="sxs-lookup"><span data-stu-id="cfffd-281">Hot</span></span> ||
| <span data-ttu-id="cfffd-282">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="cfffd-282">ExtensionData</span></span> | <span data-ttu-id="cfffd-283">temperatureC: 25</span><span class="sxs-lookup"><span data-stu-id="cfffd-283">temperatureC: 25</span></span> |<span data-ttu-id="cfffd-284">Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.</span><span class="sxs-lookup"><span data-stu-id="cfffd-284">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="cfffd-285">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="cfffd-285">DatesAvailable:</span></span><br>  <span data-ttu-id="cfffd-286">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="cfffd-286">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="cfffd-287">8/2/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="cfffd-287">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="cfffd-288">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-288">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="cfffd-289">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="cfffd-289">SummaryWords:</span></span><br><span data-ttu-id="cfffd-290">İyi</span><span class="sxs-lookup"><span data-stu-id="cfffd-290">Cool</span></span><br><span data-ttu-id="cfffd-291">Rüzgarlı</span><span class="sxs-lookup"><span data-stu-id="cfffd-291">Windy</span></span><br><span data-ttu-id="cfffd-292">İnsankimliği</span><span class="sxs-lookup"><span data-stu-id="cfffd-292">Humid</span></span> |<span data-ttu-id="cfffd-293">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-293">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="cfffd-294">Hedef nesne serileştirildiğinde, uzantı veri anahtarı değer çiftleri, gelen JSON 'da olduğu gibi JSON özellikleri olur:</span><span class="sxs-lookup"><span data-stu-id="cfffd-294">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="cfffd-295">`ExtensionData` Özellik adının JSON içinde görünmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="cfffd-295">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="cfffd-296">Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfffd-296">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="use-utf8jsonwriter-directly"></a><span data-ttu-id="cfffd-297">Doğrudan Utf8JsonWriter kullanma</span><span class="sxs-lookup"><span data-stu-id="cfffd-297">Use Utf8JsonWriter directly</span></span>

<span data-ttu-id="cfffd-298">Aşağıdaki örnek <xref:System.Text.Json.Utf8JsonWriter> sınıfının doğrudan nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-298">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class directly.</span></span>

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

## <a name="use-utf8jsonreader-directly"></a><span data-ttu-id="cfffd-299">Doğrudan Utf8JsonReader kullanma</span><span class="sxs-lookup"><span data-stu-id="cfffd-299">Use Utf8JsonReader directly</span></span>

<span data-ttu-id="cfffd-300">Aşağıdaki örnek <xref:System.Text.Json.Utf8JsonReader> sınıfının doğrudan nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="cfffd-300">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class directly.</span></span> <span data-ttu-id="cfffd-301">Kod, `jsonUtf8` değişkenin UTF-8 olarak kodlanmış geçerli JSON içeren bir bayt dizisi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="cfffd-301">The code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

```csharp
var options = new JsonReaderOptions
{
    AllowTrailingCommas = true,
    CommentHandling = JsonCommentHandling.Skip
};
Utf8JsonReader reader = new Utf8JsonReader(jsonUtf8, options);

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

## <a name="additional-resources"></a><span data-ttu-id="cfffd-302">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="cfffd-302">Additional resources</span></span>

* [<span data-ttu-id="cfffd-303">System. Text. JSON genel bakış</span><span class="sxs-lookup"><span data-stu-id="cfffd-303">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="cfffd-304">System. Text. JSON API başvurusu</span><span class="sxs-lookup"><span data-stu-id="cfffd-304">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="cfffd-305">System. Text. JSON içinde DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="cfffd-305">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
