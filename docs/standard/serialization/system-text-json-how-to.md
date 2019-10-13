---
title: .NET kullanarak C# JSON serileştirmek ve serisini kaldırma
author: tdykstra
ms.author: tdykstra
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 22c2fd5fc5eaf7a5dc9b71a7335b0b844fa92b51
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291609"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="29ba0-102">.NET 'te JSON serileştirme ve serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="29ba0-102">How to serialize and deserialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="29ba0-103">JSON serileştirme belgeleri oluşturma aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="29ba0-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="29ba0-104">Bu makale tüm senaryoları kapsamamaktadır.</span><span class="sxs-lookup"><span data-stu-id="29ba0-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="29ba0-105">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [System. Text. JSON sorunlarını](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) , özellikle de [JSON-işlevselliği-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)etiketini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="29ba0-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="29ba0-106">Bu makalede, JavaScript Nesne Gösterimi (JSON) içinde ve dışında seri hale getirmek ve seri durumdan çıkarmak için <xref:System.Text.Json> ad alanının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="29ba0-107">Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="29ba0-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="29ba0-108">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="29ba0-108">Namespaces</span></span>

<span data-ttu-id="29ba0-109">@No__t-0 ad alanı tüm giriş noktalarını ve ana türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="29ba0-110">@No__t-0 ad alanı, serileştirme ve seri durumdan çıkarma için özel gelişmiş senaryolar ve özelleştirmeler için öznitelikler ve API 'Leri içerir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="29ba0-111">Bu nedenle, bu makalede gösterilen kod örnekleri, aşağıdaki `using` yönergelerinden birini veya her ikisini de gerektirir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-111">Therefore, the code examples shown in this article require one or both of the following `using` directives:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="29ba0-112">@No__t-0 ad alanındaki öznitelikler Şu anda `System.Text.Json` ' de desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="29ba0-113">.NET nesnelerini JSON 'a yazma (serileştirme)</span><span class="sxs-lookup"><span data-stu-id="29ba0-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="29ba0-114">JSON 'yi bir dizeye yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="29ba0-114">To write JSON to a string, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="29ba0-115">Aşağıdaki örnek genel tür parametresiyle bir aşırı yükleme kullanır:</span><span class="sxs-lookup"><span data-stu-id="29ba0-115">The following example uses an overload with a generic type parameter:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="29ba0-116">Genel tür parametresini atlayabilir ve bunun yerine genel tür çıkarımı kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="29ba0-116">You can omit the generic type parameter and use generic type inference instead:</span></span>

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="29ba0-117">Aşağıda, koleksiyonları ve iç içe sınıfları içeren bir örnek türü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-117">Here's an example type to be serialized, which contains collections and nested classes:</span></span>

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

<span data-ttu-id="29ba0-118">JSON çıktısı varsayılan olarak Mini olarak belirlenir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-118">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="29ba0-119">Aşağıdaki örnek, biçimlendirilen aynı JSON 'ı gösterir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):</span><span class="sxs-lookup"><span data-stu-id="29ba0-119">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

<span data-ttu-id="29ba0-120">@No__t aşırı yüklemeleri-0 <xref:System.IO.Stream> ' e serileştirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="29ba0-120">Overloads of <xref:System.Text.Json.JsonSerializer.Serialize%2A> let you serialize to a <xref:System.IO.Stream>.</span></span> <span data-ttu-id="29ba0-121">@No__t-0 aşırı yüklemelerinin zaman uyumsuz sürümleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="29ba0-121">Async versions of the `Stream` overloads are available.</span></span>

### <a name="serialize-to-utf-8"></a><span data-ttu-id="29ba0-122">UTF-8 ' e serileştirme</span><span class="sxs-lookup"><span data-stu-id="29ba0-122">Serialize to UTF-8</span></span>

<span data-ttu-id="29ba0-123">UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-123">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="29ba0-124">Alternatif olarak, bir <xref:System.Text.Json.Utf8JsonWriter> alan <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemesi kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-124">As an alternative, a <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is available.</span></span>

<span data-ttu-id="29ba0-125">UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="29ba0-125">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="29ba0-126">Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="29ba0-126">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="29ba0-127">Serileştirme davranışı</span><span class="sxs-lookup"><span data-stu-id="29ba0-127">Serialization behavior</span></span>

* <span data-ttu-id="29ba0-128">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-128">By default, all public properties are serialized.</span></span> <span data-ttu-id="29ba0-129">[Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties).</span><span class="sxs-lookup"><span data-stu-id="29ba0-129">You can [specify properties to exclude](#exclude-properties).</span></span>
* <span data-ttu-id="29ba0-130">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERIN, ASCII aralığındaki HTML duyarlı karakterlerin yanı sıra [JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterlerle çıkar.</span><span class="sxs-lookup"><span data-stu-id="29ba0-130">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="29ba0-131">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-131">By default, JSON is minified.</span></span> <span data-ttu-id="29ba0-132">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29ba0-132">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="29ba0-133">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-133">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="29ba0-134">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names).</span><span class="sxs-lookup"><span data-stu-id="29ba0-134">You can [customize JSON name casing](#customize-json-names).</span></span>
* <span data-ttu-id="29ba0-135">Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="29ba0-135">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="29ba0-136">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposunda [Döngüsel başvurularda sorun](https://github.com/dotnet/corefx/issues/38579) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="29ba0-136">For more information, see the [issue on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="29ba0-137">Şu anda, alanlar hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="29ba0-137">Currently, fields are excluded.</span></span>

<span data-ttu-id="29ba0-138">Desteklenen türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="29ba0-138">Supported types include:</span></span>

* <span data-ttu-id="29ba0-139">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="29ba0-139">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="29ba0-140">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="29ba0-140">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="29ba0-141">Tek boyutlu ve pürüzlü Diziler (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="29ba0-141">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="29ba0-142">`TValue`;  `object`, `JsonElement` veya bir POCO.</span><span class="sxs-lookup"><span data-stu-id="29ba0-142">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="29ba0-143">Aşağıdaki ad alanlarından Koleksiyonlar.</span><span class="sxs-lookup"><span data-stu-id="29ba0-143">Collections from the following namespaces.</span></span> <span data-ttu-id="29ba0-144">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [koleksiyon desteği sorunu](https://github.com/dotnet/corefx/issues/36643) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="29ba0-144">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="29ba0-145">JSON 'ı .NET Objects 'e okuma (serisini kaldırma)</span><span class="sxs-lookup"><span data-stu-id="29ba0-145">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="29ba0-146">Bir dizeden serisini kaldırmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-146">To deserialize from a string, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method, as shown in the following example:</span></span>

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="29ba0-147">Bir örnek için [serileştirme](#how-to-write-net-objects-to-json-serialize) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="29ba0-147">For an example, see the [serialize](#how-to-write-net-objects-to-json-serialize) section.</span></span> <span data-ttu-id="29ba0-148">JSON ve .NET nesnesi aynıdır, ancak yön ters çevrilir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-148">The JSON and .NET object are the same, but the direction is reversed.</span></span>

<span data-ttu-id="29ba0-149">@No__t aşırı yüklemeleri-0 `Stream` ' den seri durumdan çıkarmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-149">Overloads of <xref:System.Text.Json.JsonSerializer.Deserialize*> let you deserialize from a `Stream`.</span></span>  <span data-ttu-id="29ba0-150">@No__t-0 aşırı yüklemelerinin zaman uyumsuz sürümleri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="29ba0-150">Async versions of the `Stream` overloads are available.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="29ba0-151">UTF-8 ' den serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="29ba0-151">Deserialize from UTF-8</span></span>

<span data-ttu-id="29ba0-152">UTF-8 ' den seri durumdan çıkarmak için, aşağıdaki örneklerde gösterildiği gibi, `Utf8JsonReader` veya `ReadOnlySpan<byte>` alan <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> aşırı yüklemesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-152">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples:</span></span>

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

## <a name="deserialization-behavior"></a><span data-ttu-id="29ba0-153">Seri durumdan çıkarma davranışı</span><span class="sxs-lookup"><span data-stu-id="29ba0-153">Deserialization behavior</span></span>

* <span data-ttu-id="29ba0-154">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="29ba0-154">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="29ba0-155">[Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="29ba0-155">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="29ba0-156">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="29ba0-156">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="29ba0-157">Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="29ba0-157">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="29ba0-158">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="29ba0-158">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="29ba0-159">Daha fazla bilgi için bkz. [sabit nesne desteğiyle Ilgili GitHub sorunu](https://github.com/dotnet/corefx/issues/38569) ve GitHub 'daki DotNet/corefx deposundaki [salt okunurdur özellik desteği](https://github.com/dotnet/corefx/issues/38163) .</span><span class="sxs-lookup"><span data-stu-id="29ba0-159">For more information, see the GitHub [issue on immutable object support](https://github.com/dotnet/corefx/issues/38569) and the [issue on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="29ba0-160">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-160">By default, enums are supported as numbers.</span></span>
* <span data-ttu-id="29ba0-161">Alanlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="29ba0-161">Fields aren't supported.</span></span>
* <span data-ttu-id="29ba0-162">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="29ba0-162">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="29ba0-163">Gerekirse [açıklamalara ve sondaki virgüllerin belirtilmesine izin](#allow-comments-and-trailing-commas) verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29ba0-163">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas) if needed.</span></span>
* <span data-ttu-id="29ba0-164">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-164">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="29ba0-165">Biçimlendirilen JSON 'a serileştirme</span><span class="sxs-lookup"><span data-stu-id="29ba0-165">Serialize to formatted JSON</span></span>

<span data-ttu-id="29ba0-166">JSON çıkışını oldukça yazdırmak için <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> ' ı `true` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-166">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="29ba0-167">Seri hale getirilecek bir örnek türü ve JSON çıktısı aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-167">Here's an example type to be serialized and JSON output:</span></span>

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

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="29ba0-168">Yorumlara ve sondaki virgülleri izin ver</span><span class="sxs-lookup"><span data-stu-id="29ba0-168">Allow comments and trailing commas</span></span>

<span data-ttu-id="29ba0-169">JSON 'da varsayılan açıklamalara ve sondaki virgüllerin kullanımına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="29ba0-169">By default comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="29ba0-170">JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini `JsonCommentHandling.Skip` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29ba0-170">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span> <span data-ttu-id="29ba0-171">Sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="29ba0-171">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="29ba0-172">Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-172">The following example shows how to allow both:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

<span data-ttu-id="29ba0-173">Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-173">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a><span data-ttu-id="29ba0-174">JSON adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="29ba0-174">Customize JSON names</span></span>

<span data-ttu-id="29ba0-175">Varsayılan olarak, özellik adları ve sözlük anahtarları, büyük/küçük harf gibi JSON çıktısında değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="29ba0-175">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="29ba0-176">Bu bölümde nasıl yapılacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="29ba0-176">This section explains how to:</span></span>

* <span data-ttu-id="29ba0-177">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="29ba0-177">Customize individual property names</span></span>
* <span data-ttu-id="29ba0-178">Tüm özellik adlarını ortası durumuna Dönüştür</span><span class="sxs-lookup"><span data-stu-id="29ba0-178">Convert all property names to camel case</span></span>
* <span data-ttu-id="29ba0-179">Özel özellik adlandırma ilkesi uygulama</span><span class="sxs-lookup"><span data-stu-id="29ba0-179">Implement a custom property naming policy</span></span>
* <span data-ttu-id="29ba0-180">Sözlük anahtarlarını ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="29ba0-180">Convert dictionary keys to camel case</span></span>

<span data-ttu-id="29ba0-181">Şu anda, Numaralandırmaların otomatik olarak ortası örneğine dönüştürülmesi desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="29ba0-181">Currently, there's no support for automatically converting enums to camel case.</span></span> <span data-ttu-id="29ba0-182">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposunda [kamel durum desteğinin numaralandırmasında sorun](https://github.com/dotnet/corefx/issues/37725) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="29ba0-182">For more information, see the [issue on enum camel case support](https://github.com/dotnet/corefx/issues/37725) in the dotnet/corefx repository on GitHub.</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="29ba0-183">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="29ba0-183">Customize individual property names</span></span>

<span data-ttu-id="29ba0-184">Ayrı özelliklerin adını ayarlamak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="29ba0-184">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="29ba0-185">Serileştirme ve sonuç JSON için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-185">Here's an example type to serialize and resulting JSON:</span></span>

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

<span data-ttu-id="29ba0-186">Bu öznitelik tarafından ayarlanan özellik adı:</span><span class="sxs-lookup"><span data-stu-id="29ba0-186">The property name set by this attribute:</span></span>

* <span data-ttu-id="29ba0-187">Serileştirme ve seri durumundan çıkarma için her iki yönde de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-187">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="29ba0-188">Özellik adlandırma ilkelerine göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-188">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="29ba0-189">Tüm JSON Özellik adları için ortası Case kullanın</span><span class="sxs-lookup"><span data-stu-id="29ba0-189">Use camel case for all JSON property names</span></span>

<span data-ttu-id="29ba0-190">Tüm JSON Özellik adları için ortası durumunu kullanmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> ' ı `JsonNamingPolicy.CamelCase` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-190">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="29ba0-191">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-191">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="29ba0-192">Ortası durum özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="29ba0-192">The camel case property naming policy:</span></span>

* <span data-ttu-id="29ba0-193">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-193">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="29ba0-194">@No__t-0 öznitelikleri tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="29ba0-194">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="29ba0-195">Özel bir JSON Özellik adlandırma ilkesi kullanma</span><span class="sxs-lookup"><span data-stu-id="29ba0-195">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="29ba0-196">Özel bir JSON Özellik adlandırma ilkesi kullanmak için, <xref:System.Text.Json.JsonNamingPolicy> ' dan türeten bir sınıf oluşturun ve aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> yöntemini geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-196">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="29ba0-197">Sonra <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> özelliğini, adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-197">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="29ba0-198">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-198">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="29ba0-199">JSON özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="29ba0-199">The JSON property naming policy:</span></span>

* <span data-ttu-id="29ba0-200">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-200">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="29ba0-201">@No__t-0 öznitelikleri tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="29ba0-201">Is overridden by `[JsonPropertyName]` attributes.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="29ba0-202">Camel durum sözlüğü anahtarları</span><span class="sxs-lookup"><span data-stu-id="29ba0-202">Camel case dictionary keys</span></span>

<span data-ttu-id="29ba0-203">Seri hale getirilecek bir nesnenin bir özelliği `Dictionary<string,TValue>` türünde ise, `string` anahtarlar ortası duruma dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-203">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="29ba0-204">Bunu yapmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> ' ı `JsonNamingPolicy.CamelCase` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-204">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="29ba0-205">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-205">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="29ba0-206">Özellik</span><span class="sxs-lookup"><span data-stu-id="29ba0-206">Property</span></span> |<span data-ttu-id="29ba0-207">Değer</span><span class="sxs-lookup"><span data-stu-id="29ba0-207">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="29ba0-208">Tarih</span><span class="sxs-lookup"><span data-stu-id="29ba0-208">Date</span></span>    | <span data-ttu-id="29ba0-209">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="29ba0-209">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="29ba0-210">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="29ba0-210">TemperatureC</span></span>| <span data-ttu-id="29ba0-211">25</span><span class="sxs-lookup"><span data-stu-id="29ba0-211">25</span></span> |
| <span data-ttu-id="29ba0-212">Özet</span><span class="sxs-lookup"><span data-stu-id="29ba0-212">Summary</span></span>| <span data-ttu-id="29ba0-213">Sık Erişimli</span><span class="sxs-lookup"><span data-stu-id="29ba0-213">Hot</span></span>|
| <span data-ttu-id="29ba0-214">TemperatureRanges</span><span class="sxs-lookup"><span data-stu-id="29ba0-214">TemperatureRanges</span></span> | <span data-ttu-id="29ba0-215">Durgun, 20</span><span class="sxs-lookup"><span data-stu-id="29ba0-215">Cold, 20</span></span><br><span data-ttu-id="29ba0-216">Sık erişimli, 40</span><span class="sxs-lookup"><span data-stu-id="29ba0-216">Hot, 40</span></span>|

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

<span data-ttu-id="29ba0-217">Ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-217">The camel case naming policy applies to serialization only.</span></span>

## <a name="exclude-properties"></a><span data-ttu-id="29ba0-218">Dışlama özellikleri</span><span class="sxs-lookup"><span data-stu-id="29ba0-218">Exclude properties</span></span>

<span data-ttu-id="29ba0-219">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-219">By default, all public properties are serialized.</span></span> <span data-ttu-id="29ba0-220">Bir kısmının JSON çıktısında görünmesini istemiyorsanız, birkaç seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="29ba0-220">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="29ba0-221">Bu bölümde nasıl hariç tutulacak açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="29ba0-221">This section explains how to exclude:</span></span>

* <span data-ttu-id="29ba0-222">Bireysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="29ba0-222">Individual properties</span></span>
* <span data-ttu-id="29ba0-223">Tüm salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="29ba0-223">All read-only properties</span></span>
* <span data-ttu-id="29ba0-224">Tüm null değerli özellikler</span><span class="sxs-lookup"><span data-stu-id="29ba0-224">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="29ba0-225">Bireysel özellikleri Dışla</span><span class="sxs-lookup"><span data-stu-id="29ba0-225">Exclude individual properties</span></span>

<span data-ttu-id="29ba0-226">Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="29ba0-226">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="29ba0-227">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-227">Here's an example type to serialize and JSON output:</span></span>

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

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="29ba0-228">Tüm salt okuma özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="29ba0-228">Exclude all read-only properties</span></span>

<span data-ttu-id="29ba0-229">Tüm salt okuma özelliklerini hariç tutmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> ' ı `true` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-229">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="29ba0-230">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-230">Here's an example type to serialize and JSON output:</span></span>

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

<span data-ttu-id="29ba0-231">Bu seçenek yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-231">This option applies only to serialization.</span></span> <span data-ttu-id="29ba0-232">Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="29ba0-232">During deserialization, read-only properties are ignored by default.</span></span> <span data-ttu-id="29ba0-233">Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="29ba0-233">A property is read-only if it contains a public getter but not a public setter.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="29ba0-234">Tüm null değer özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="29ba0-234">Exclude all null value properties</span></span>

<span data-ttu-id="29ba0-235">Tüm null değer özelliklerini dışlamak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> özelliğini `true` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-235">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="29ba0-236">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-236">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="29ba0-237">Özellik</span><span class="sxs-lookup"><span data-stu-id="29ba0-237">Property</span></span> |<span data-ttu-id="29ba0-238">Değer</span><span class="sxs-lookup"><span data-stu-id="29ba0-238">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="29ba0-239">Tarih</span><span class="sxs-lookup"><span data-stu-id="29ba0-239">Date</span></span>    | <span data-ttu-id="29ba0-240">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="29ba0-240">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="29ba0-241">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="29ba0-241">TemperatureC</span></span>| <span data-ttu-id="29ba0-242">25</span><span class="sxs-lookup"><span data-stu-id="29ba0-242">25</span></span> |
| <span data-ttu-id="29ba0-243">Özet</span><span class="sxs-lookup"><span data-stu-id="29ba0-243">Summary</span></span>| <span data-ttu-id="29ba0-244">değer</span><span class="sxs-lookup"><span data-stu-id="29ba0-244">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="29ba0-245">Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-245">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="29ba0-246">Seri durumdan çıkarma sırasında, JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="29ba0-246">During deserialization, null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="29ba0-247">Nullable değer türleri için null değerler özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="29ba0-247">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="29ba0-248">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [null yapılamayan değer türlerinde sorun](https://github.com/dotnet/corefx/issues/40922) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="29ba0-248">For more information, see the [issue on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="29ba0-249">Büyük/küçük harfe duyarsız Özellik eşleştirme</span><span class="sxs-lookup"><span data-stu-id="29ba0-249">Case-insensitive property matching</span></span>

<span data-ttu-id="29ba0-250">Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar.</span><span class="sxs-lookup"><span data-stu-id="29ba0-250">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="29ba0-251">Bu davranışı değiştirmek için <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> ' ı `true` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-251">To change that behavior, set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="29ba0-252">Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-252">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="29ba0-253">Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-253">It can be deserialized into the following type that has Pascal case property names.</span></span>

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

## <a name="include-properties-of-derived-classes"></a><span data-ttu-id="29ba0-254">Türetilmiş sınıfların özelliklerini Ekle</span><span class="sxs-lookup"><span data-stu-id="29ba0-254">Include properties of derived classes</span></span>

<span data-ttu-id="29ba0-255">Derleme zamanında seri hale getirilecek tür için belirttiğiniz zaman polimorfik serileştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="29ba0-255">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="29ba0-256">Örneğin, `WeatherForecast` sınıfına ve türetilmiş bir sınıfa sahip olduğunuzu varsayalım-1 @no__t:</span><span class="sxs-lookup"><span data-stu-id="29ba0-256">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

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

<span data-ttu-id="29ba0-257">Ve, derleme zamanında `Serialize` yönteminin `WeatherForecast` olduğunu veya bu tür tarafından algılanır olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="29ba0-257">And suppose the type passed to, or inferred by, the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="29ba0-258">Bu senaryoda, `weatherForecast` nesnesi gerçekten `WeatherForecastWithWind` nesnesi olsa bile `WindSpeed` özelliği serileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="29ba0-258">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="29ba0-259">Yalnızca temel sınıf özellikleri serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-259">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="29ba0-260">Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="29ba0-260">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="29ba0-261">Türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-261">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="29ba0-262">Çalışma zamanında türü belirtmenizi sağlayan <xref:System.Text.Json.JsonSerializer.Serialize%2A> ' nın aşırı yüklemesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-262">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="29ba0-263">@No__t-0 olarak seri hale getirilecek nesneyi bildirin.</span><span class="sxs-lookup"><span data-stu-id="29ba0-263">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="29ba0-264">Yukarıdaki örnek senaryoda, her iki yaklaşım da `WindSpeed` özelliğinin JSON çıktısına dahil olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="29ba0-264">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

## <a name="handle-overflow-json"></a><span data-ttu-id="29ba0-265">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="29ba0-265">Handle overflow JSON</span></span>

<span data-ttu-id="29ba0-266">Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="29ba0-266">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="29ba0-267">Örneğin, hedef türünün bu olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="29ba0-267">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="29ba0-268">Ve seri durumdan çıkarılacak JSON şu şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="29ba0-268">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="29ba0-269">Gösterilen türde gösterilen JSON serisini kaldırırsanız `DatesAvailable` ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor.</span><span class="sxs-lookup"><span data-stu-id="29ba0-269">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="29ba0-270">Bu özellikler gibi ek verileri yakalamak için, [Jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini `Dictionary<string,object>` veya `Dictionary<string,JsonElement>` türünde bir özelliğe uygulayın:</span><span class="sxs-lookup"><span data-stu-id="29ba0-270">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

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

<span data-ttu-id="29ba0-271">Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veriler `ExtensionData` özelliğinin anahtar-değer çiftleri haline gelir:</span><span class="sxs-lookup"><span data-stu-id="29ba0-271">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="29ba0-272">Özellik</span><span class="sxs-lookup"><span data-stu-id="29ba0-272">Property</span></span> |<span data-ttu-id="29ba0-273">Değer</span><span class="sxs-lookup"><span data-stu-id="29ba0-273">Value</span></span>  |<span data-ttu-id="29ba0-274">Notlar</span><span class="sxs-lookup"><span data-stu-id="29ba0-274">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="29ba0-275">Tarih</span><span class="sxs-lookup"><span data-stu-id="29ba0-275">Date</span></span>    | <span data-ttu-id="29ba0-276">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="29ba0-276">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="29ba0-277">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="29ba0-277">TemperatureC</span></span>| <span data-ttu-id="29ba0-278">0</span><span class="sxs-lookup"><span data-stu-id="29ba0-278">0</span></span> | <span data-ttu-id="29ba0-279">Büyük/küçük harfe duyarlı uyuşmazlık (JSON içinde `temperatureC`), bu nedenle özellik ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="29ba0-279">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="29ba0-280">Özet</span><span class="sxs-lookup"><span data-stu-id="29ba0-280">Summary</span></span> | <span data-ttu-id="29ba0-281">Sık Erişimli</span><span class="sxs-lookup"><span data-stu-id="29ba0-281">Hot</span></span> ||
| <span data-ttu-id="29ba0-282">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="29ba0-282">ExtensionData</span></span> | <span data-ttu-id="29ba0-283">temperatureC: 25</span><span class="sxs-lookup"><span data-stu-id="29ba0-283">temperatureC: 25</span></span> |<span data-ttu-id="29ba0-284">Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.</span><span class="sxs-lookup"><span data-stu-id="29ba0-284">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="29ba0-285">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="29ba0-285">DatesAvailable:</span></span><br>  <span data-ttu-id="29ba0-286">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="29ba0-286">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="29ba0-287">8/2/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="29ba0-287">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="29ba0-288">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-288">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="29ba0-289">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="29ba0-289">SummaryWords:</span></span><br><span data-ttu-id="29ba0-290">Seyrek Erişimli</span><span class="sxs-lookup"><span data-stu-id="29ba0-290">Cool</span></span><br><span data-ttu-id="29ba0-291">Rüzgarlı</span><span class="sxs-lookup"><span data-stu-id="29ba0-291">Windy</span></span><br><span data-ttu-id="29ba0-292">İnsankimliği</span><span class="sxs-lookup"><span data-stu-id="29ba0-292">Humid</span></span> |<span data-ttu-id="29ba0-293">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-293">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="29ba0-294">Hedef nesne serileştirildiğinde, uzantı veri anahtarı değer çiftleri, gelen JSON 'da olduğu gibi JSON özellikleri olur:</span><span class="sxs-lookup"><span data-stu-id="29ba0-294">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="29ba0-295">@No__t-0 özellik adının JSON içinde görünmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="29ba0-295">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="29ba0-296">Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="29ba0-296">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="use-utf8jsonwriter-directly"></a><span data-ttu-id="29ba0-297">Doğrudan Utf8JsonWriter kullanma</span><span class="sxs-lookup"><span data-stu-id="29ba0-297">Use Utf8JsonWriter directly</span></span>

<span data-ttu-id="29ba0-298">Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonWriter> sınıfının doğrudan nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-298">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class directly.</span></span>

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

## <a name="use-utf8jsonreader-directly"></a><span data-ttu-id="29ba0-299">Doğrudan Utf8JsonReader kullanma</span><span class="sxs-lookup"><span data-stu-id="29ba0-299">Use Utf8JsonReader directly</span></span>

<span data-ttu-id="29ba0-300">Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonReader> sınıfının doğrudan nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="29ba0-300">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class directly.</span></span> <span data-ttu-id="29ba0-301">Kod, `jsonUtf8` değişkeninin UTF-8 olarak kodlanmış geçerli JSON içeren bir bayt dizisi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="29ba0-301">The code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="29ba0-302">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="29ba0-302">Additional resources</span></span>

* [<span data-ttu-id="29ba0-303">System. Text. JSON genel bakış</span><span class="sxs-lookup"><span data-stu-id="29ba0-303">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="29ba0-304">System. Text. JSON API başvurusu</span><span class="sxs-lookup"><span data-stu-id="29ba0-304">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="29ba0-305">System. Text. JSON içinde DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="29ba0-305">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
