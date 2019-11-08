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
ms.openlocfilehash: f0245feb710f33d5fcea2a7125b8753ba6064018
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740437"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a><span data-ttu-id="0edc9-102">.NET 'te JSON serileştirme ve serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="0edc9-102">How to serialize and deserialize JSON in .NET</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0edc9-103">JSON serileştirme belgeleri oluşturma aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-103">The JSON serialization documentation is under construction.</span></span> <span data-ttu-id="0edc9-104">Bu makale tüm senaryoları kapsamamaktadır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-104">This article doesn't cover all scenarios.</span></span> <span data-ttu-id="0edc9-105">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [System. Text. JSON sorunlarını](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) , özellikle de [JSON-işlevselliği-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)etiketini inceleyin.</span><span class="sxs-lookup"><span data-stu-id="0edc9-105">For more information, examine [System.Text.Json issues](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) in the dotnet/corefx repository on GitHub, especially those labeled [json-functionality-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc).</span></span>

<span data-ttu-id="0edc9-106">Bu makalede, JavaScript Nesne Gösterimi (JSON) içinde ve dışında seri hale getirmek ve seri durumdan çıkarmak için <xref:System.Text.Json> ad alanının nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-106">This article shows how to use the <xref:System.Text.Json> namespace to serialize and deserialize to and from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="0edc9-107">Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

## <a name="namespaces"></a><span data-ttu-id="0edc9-108">Ad Alanları</span><span class="sxs-lookup"><span data-stu-id="0edc9-108">Namespaces</span></span>

<span data-ttu-id="0edc9-109"><xref:System.Text.Json> ad alanı tüm giriş noktalarını ve ana türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-109">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="0edc9-110"><xref:System.Text.Json.Serialization> ad alanı, serileştirme ve seri durumdan çıkarma için özel gelişmiş senaryolar ve özelleştirmeler için öznitelikler ve API 'Leri içerir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-110">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="0edc9-111">Bu makalede gösterilen kod örnekleri, bu ad alanlarından biri veya her ikisi için `using` yönergeler gerektirir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-111">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<span data-ttu-id="0edc9-112"><xref:System.Runtime.Serialization> ad alanındaki öznitelikler Şu anda `System.Text.Json`desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="0edc9-112">Attributes from the <xref:System.Runtime.Serialization> namespace aren't currently supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-to-json-serialize"></a><span data-ttu-id="0edc9-113">.NET nesnelerini JSON 'a yazma (serileştirme)</span><span class="sxs-lookup"><span data-stu-id="0edc9-113">How to write .NET objects to JSON (serialize)</span></span>

<span data-ttu-id="0edc9-114">JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-114">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="0edc9-115">Aşağıdaki örnek bir dize olarak JSON oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0edc9-115">The following example creates JSON as a string:</span></span>

```csharp
string json = JsonSerializer.Serialize(weatherForecast);
```

<span data-ttu-id="0edc9-116">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="0edc9-116">The following example uses synchronous code to create a JSON file:</span></span>

```csharp
File.WriteAllText(outputFileName, JsonSerializer.Serialize(weatherForecast));
```

<span data-ttu-id="0edc9-117">Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:</span><span class="sxs-lookup"><span data-stu-id="0edc9-117">The following example uses asynchronous code to create a JSON file:</span></span>

```csharp
using (FileStream fs = File.Create(outputFileName))
{
    await JsonSerializer.SerializeAsync(fs, weatherForecast);
}
```

<span data-ttu-id="0edc9-118">Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-118">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="0edc9-119">`Serialize()` aşırı yüklemesi genel bir tür parametresi alır:</span><span class="sxs-lookup"><span data-stu-id="0edc9-119">An overload of `Serialize()` takes a generic type parameter:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

### <a name="serialization-example"></a><span data-ttu-id="0edc9-120">Serileştirme örneği</span><span class="sxs-lookup"><span data-stu-id="0edc9-120">Serialization example</span></span>

<span data-ttu-id="0edc9-121">Koleksiyonları ve iç içe sınıfları içeren örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-121">Here's an example type that contains collections and nested classes:</span></span>

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

<span data-ttu-id="0edc9-122">Önceki türün bir örneğinin serileştirilmesi için JSON çıktısı aşağıdaki örnekteki gibi görünür.</span><span class="sxs-lookup"><span data-stu-id="0edc9-122">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="0edc9-123">JSON çıktısı varsayılan olarak Mini olarak belirlenir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-123">The JSON output is minified by default:</span></span> 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="0edc9-124">Aşağıdaki örnek, biçimlendirilen aynı JSON 'ı gösterir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):</span><span class="sxs-lookup"><span data-stu-id="0edc9-124">The following example shows the same JSON, formatted (that is, pretty-printed with whitespace and indentation):</span></span>

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

### <a name="serialize-to-utf-8"></a><span data-ttu-id="0edc9-125">UTF-8 ' e serileştirme</span><span class="sxs-lookup"><span data-stu-id="0edc9-125">Serialize to UTF-8</span></span>

<span data-ttu-id="0edc9-126">UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemi çağırın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-126">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

```csharp
byte[] jsonUtf8Bytes = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="0edc9-127"><xref:System.Text.Json.Utf8JsonWriter> alan <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemesi de mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="0edc9-127">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="0edc9-128">UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-128">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="0edc9-129">Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="0edc9-129">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="0edc9-130">Serileştirme davranışı</span><span class="sxs-lookup"><span data-stu-id="0edc9-130">Serialization behavior</span></span>

* <span data-ttu-id="0edc9-131">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-131">By default, all public properties are serialized.</span></span> <span data-ttu-id="0edc9-132">[Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties-from-serialization).</span><span class="sxs-lookup"><span data-stu-id="0edc9-132">You can [specify properties to exclude](#exclude-properties-from-serialization).</span></span>
* <span data-ttu-id="0edc9-133">[Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERIN, ASCII aralığındaki HTML duyarlı karakterlerin yanı sıra [JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterlerle çıkar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-133">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="0edc9-134">Varsayılan olarak JSON, Mini olarak belirlenir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-134">By default, JSON is minified.</span></span> <span data-ttu-id="0edc9-135">JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0edc9-135">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="0edc9-136">Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-136">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="0edc9-137">[JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names-and-values).</span><span class="sxs-lookup"><span data-stu-id="0edc9-137">You can [customize JSON name casing](#customize-json-names-and-values).</span></span>
* <span data-ttu-id="0edc9-138">Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.</span><span class="sxs-lookup"><span data-stu-id="0edc9-138">Circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="0edc9-139">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposunda [Döngüsel başvurularda sorun](https://github.com/dotnet/corefx/issues/38579) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-139">For more information, see the [issue on circular references](https://github.com/dotnet/corefx/issues/38579) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="0edc9-140">Şu anda, alanlar hariç tutulur.</span><span class="sxs-lookup"><span data-stu-id="0edc9-140">Currently, fields are excluded.</span></span>

<span data-ttu-id="0edc9-141">Desteklenen türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0edc9-141">Supported types include:</span></span>

* <span data-ttu-id="0edc9-142">Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.</span><span class="sxs-lookup"><span data-stu-id="0edc9-142">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="0edc9-143">Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span><span class="sxs-lookup"><span data-stu-id="0edc9-143">User-defined [Plain Old CLR Objects (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).</span></span>
* <span data-ttu-id="0edc9-144">Tek boyutlu ve pürüzlü Diziler (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="0edc9-144">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="0edc9-145">`TValue`;  `object`, `JsonElement` veya bir POCO.</span><span class="sxs-lookup"><span data-stu-id="0edc9-145">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="0edc9-146">Aşağıdaki ad alanlarından Koleksiyonlar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-146">Collections from the following namespaces.</span></span> <span data-ttu-id="0edc9-147">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [koleksiyon desteği sorunu](https://github.com/dotnet/corefx/issues/36643) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-147">For more information, see the [issue on collection support](https://github.com/dotnet/corefx/issues/36643) in the dotnet/corefx repository on GitHub.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

<span data-ttu-id="0edc9-148">Ek türleri işlemek için [özel dönüştürücüler uygulayabilir](system-text-json-converters-how-to.md) veya yerleşik dönüştürücüler tarafından desteklenmeyen işlevler sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0edc9-148">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-into-net-objects-deserialize"></a><span data-ttu-id="0edc9-149">JSON 'ı .NET Objects 'e okuma (serisini kaldırma)</span><span class="sxs-lookup"><span data-stu-id="0edc9-149">How to read JSON into .NET objects (deserialize)</span></span>

<span data-ttu-id="0edc9-150">Bir dizeden veya dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-150">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="0edc9-151">Aşağıdaki örnek bir dizeden JSON okur:</span><span class="sxs-lookup"><span data-stu-id="0edc9-151">The following example reads JSON from a string:</span></span>

```csharp
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

<span data-ttu-id="0edc9-152">Zaman uyumlu kod kullanarak bir dosyadan seri durumdan çıkarmak için, aşağıdaki örnekte gösterildiği gibi dosyayı bir dizeye okuyun:</span><span class="sxs-lookup"><span data-stu-id="0edc9-152">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

```csharp
string jsonString = File.ReadAllText(inputFileName);
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

<span data-ttu-id="0edc9-153">Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> yöntemi çağırın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-153">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

```csharp
using (FileStream fs = File.OpenRead(inputFileName))
{
    weatherForecast = await JsonSerializer.DeserializeAsync<WeatherForecast>(fs);
}
```

<span data-ttu-id="0edc9-154">Örnek bir tür ve karşılık gelen JSON için [serileştirme örnek](#serialization-example) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-154">For an example type and corresponding JSON, see the [Serialization example](#serialization-example) section.</span></span>

### <a name="deserialize-from-utf-8"></a><span data-ttu-id="0edc9-155">UTF-8 ' den serisini kaldırma</span><span class="sxs-lookup"><span data-stu-id="0edc9-155">Deserialize from UTF-8</span></span>

<span data-ttu-id="0edc9-156">UTF-8 ' den seri durumdan çıkarmak için, aşağıdaki örneklerde gösterildiği gibi `Utf8JsonReader` veya `ReadOnlySpan<byte>`alan <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> aşırı yüklemeyi çağırın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-156">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `Utf8JsonReader` or a `ReadOnlySpan<byte>`, as shown in the following examples.</span></span> <span data-ttu-id="0edc9-157">Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-157">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

```csharp
var readOnlySpan = new ReadOnlySpan<byte>(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
var utf8Reader = new Utf8JsonReader(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a><span data-ttu-id="0edc9-158">Seri durumdan çıkarma davranışı</span><span class="sxs-lookup"><span data-stu-id="0edc9-158">Deserialization behavior</span></span>

* <span data-ttu-id="0edc9-159">Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-159">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="0edc9-160">[Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).</span><span class="sxs-lookup"><span data-stu-id="0edc9-160">You can [specify case-insensitivity](#case-insensitive-property-matching).</span></span>
* <span data-ttu-id="0edc9-161">JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.</span><span class="sxs-lookup"><span data-stu-id="0edc9-161">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="0edc9-162">Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0edc9-162">Deserialization to reference types without a parameterless constructor isn't supported.</span></span>
* <span data-ttu-id="0edc9-163">Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0edc9-163">Deserialization to immutable objects or read-only properties isn't supported.</span></span> <span data-ttu-id="0edc9-164">Daha fazla bilgi için bkz. [sabit nesne desteğiyle Ilgili GitHub sorunu](https://github.com/dotnet/corefx/issues/38569) ve GitHub 'daki DotNet/corefx deposundaki [salt okunurdur özellik desteği](https://github.com/dotnet/corefx/issues/38163) .</span><span class="sxs-lookup"><span data-stu-id="0edc9-164">For more information, see the GitHub [issue on immutable object support](https://github.com/dotnet/corefx/issues/38569) and the [issue on read-only property support](https://github.com/dotnet/corefx/issues/38163) in the dotnet/corefx repository on GitHub.</span></span>
* <span data-ttu-id="0edc9-165">Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-165">By default, enums are supported as numbers.</span></span> <span data-ttu-id="0edc9-166">[Enum adlarını dizeler olarak seri hale](#enums-as-strings)getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0edc9-166">You can [serialize enum names as strings](#enums-as-strings).</span></span>
* <span data-ttu-id="0edc9-167">Alanlar desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="0edc9-167">Fields aren't supported.</span></span>
* <span data-ttu-id="0edc9-168">Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0edc9-168">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="0edc9-169">[Yorumlara ve sondaki virgüllerin bulunmasına izin](#allow-comments-and-trailing-commas)verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0edc9-169">You can [allow comments and trailing commas](#allow-comments-and-trailing-commas).</span></span>
* <span data-ttu-id="0edc9-170">[Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-170">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="0edc9-171">Yerleşik dönüştürücüler tarafından desteklenmeyen işlevselliği sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .</span><span class="sxs-lookup"><span data-stu-id="0edc9-171">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="0edc9-172">Biçimlendirilen JSON 'a serileştirme</span><span class="sxs-lookup"><span data-stu-id="0edc9-172">Serialize to formatted JSON</span></span>

<span data-ttu-id="0edc9-173">JSON çıkışını oldukça yazdırmak için <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> ' ı `true` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-173">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="0edc9-174">Aşağıda, seri hale getirilebilir ve düzgün şekilde yazdırılan JSON çıkışının örnek bir türü verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-174">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

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

## <a name="customize-json-names-and-values"></a><span data-ttu-id="0edc9-175">JSON adlarını ve değerlerini özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0edc9-175">Customize JSON names and values</span></span>

<span data-ttu-id="0edc9-176">Varsayılan olarak, özellik adları ve sözlük anahtarları, büyük/küçük harf gibi JSON çıktısında değiştirilmez.</span><span class="sxs-lookup"><span data-stu-id="0edc9-176">By default, property names and dictionary keys are unchanged in the JSON output, including case.</span></span> <span data-ttu-id="0edc9-177">Sabit listesi değerleri sayı olarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-177">Enum values are represented as numbers.</span></span> <span data-ttu-id="0edc9-178">Bu bölümde nasıl yapılacağı açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="0edc9-178">This section explains how to:</span></span>

* <span data-ttu-id="0edc9-179">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0edc9-179">Customize individual property names</span></span>
* <span data-ttu-id="0edc9-180">Tüm özellik adlarını ortası durumuna Dönüştür</span><span class="sxs-lookup"><span data-stu-id="0edc9-180">Convert all property names to camel case</span></span>
* <span data-ttu-id="0edc9-181">Özel özellik adlandırma ilkesi uygulama</span><span class="sxs-lookup"><span data-stu-id="0edc9-181">Implement a custom property naming policy</span></span>
* <span data-ttu-id="0edc9-182">Sözlük anahtarlarını ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="0edc9-182">Convert dictionary keys to camel case</span></span>
* <span data-ttu-id="0edc9-183">Numaralandırmaları dizelere ve ortası örneğine Dönüştür</span><span class="sxs-lookup"><span data-stu-id="0edc9-183">Convert enums to strings and camel case</span></span> 

<span data-ttu-id="0edc9-184">JSON özellik adlarını ve değerlerini özel olarak işleme gerektiren diğer senaryolar için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="0edc9-184">For other scenarios that require special handling of JSON property names and values, you can [implement custom converters](system-text-json-converters-how-to.md).</span></span>

### <a name="customize-individual-property-names"></a><span data-ttu-id="0edc9-185">Bireysel özellik adlarını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0edc9-185">Customize individual property names</span></span>

<span data-ttu-id="0edc9-186">Ayrı özelliklerin adını ayarlamak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-186">To set the name of individual properties, use the [[JsonPropertyName]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) attribute.</span></span>

<span data-ttu-id="0edc9-187">Serileştirme ve sonuç JSON için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-187">Here's an example type to serialize and resulting JSON:</span></span>

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

<span data-ttu-id="0edc9-188">Bu öznitelik tarafından ayarlanan özellik adı:</span><span class="sxs-lookup"><span data-stu-id="0edc9-188">The property name set by this attribute:</span></span>

* <span data-ttu-id="0edc9-189">Serileştirme ve seri durumundan çıkarma için her iki yönde de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-189">Applies in both directions, for serialization and deserialization.</span></span>
* <span data-ttu-id="0edc9-190">Özellik adlandırma ilkelerine göre önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-190">Takes precedence over property naming policies.</span></span>

### <a name="use-camel-case-for-all-json-property-names"></a><span data-ttu-id="0edc9-191">Tüm JSON Özellik adları için ortası Case kullanın</span><span class="sxs-lookup"><span data-stu-id="0edc9-191">Use camel case for all JSON property names</span></span>

<span data-ttu-id="0edc9-192">Tüm JSON Özellik adları için ortası durumunu kullanmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> ' ı `JsonNamingPolicy.CamelCase` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-192">To use camel case for all JSON property names, set <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="0edc9-193">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-193">Here's an example class to serialize and JSON output:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureCelsius { get; set; }
    public string Summary { get; set; }
    [JsonPropertyName("Wind")]
    public int WindSpeed { get; set; }
}
```

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
  "Wind": 35
}
```

<span data-ttu-id="0edc9-194">Ortası durum özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="0edc9-194">The camel case property naming policy:</span></span>

* <span data-ttu-id="0edc9-195">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-195">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="0edc9-196">`[JsonPropertyName]` öznitelikleri tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-196">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="0edc9-197">Bu, örnekte `Wind` JSON özelliği adının ortası durum olmadığı durumdur.</span><span class="sxs-lookup"><span data-stu-id="0edc9-197">This is why the JSON property name `Wind` in the example is not camel case.</span></span>

### <a name="use-a-custom-json-property-naming-policy"></a><span data-ttu-id="0edc9-198">Özel bir JSON Özellik adlandırma ilkesi kullanma</span><span class="sxs-lookup"><span data-stu-id="0edc9-198">Use a custom JSON property naming policy</span></span>

<span data-ttu-id="0edc9-199">Özel bir JSON Özellik adlandırma ilkesi kullanmak için, <xref:System.Text.Json.JsonNamingPolicy> türeten bir sınıf oluşturun ve aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> yöntemini geçersiz kılın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-199">To use a custom JSON property naming policy, create a class that derives from <xref:System.Text.Json.JsonNamingPolicy> and override the <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> method, as shown in the following example:</span></span>

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

<span data-ttu-id="0edc9-200">Sonra <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> özelliğini, adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-200">Then set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> property to an instance of your naming policy class:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="0edc9-201">Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-201">Here's an example class to serialize and JSON output:</span></span>

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

<span data-ttu-id="0edc9-202">JSON özelliği adlandırma ilkesi:</span><span class="sxs-lookup"><span data-stu-id="0edc9-202">The JSON property naming policy:</span></span>

* <span data-ttu-id="0edc9-203">Serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-203">Applies to serialization and deserialization.</span></span>
* <span data-ttu-id="0edc9-204">`[JsonPropertyName]` öznitelikleri tarafından geçersiz kılınır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-204">Is overridden by `[JsonPropertyName]` attributes.</span></span> <span data-ttu-id="0edc9-205">Bu, örnekte `Wind` JSON özelliği adının büyük harfle değil.</span><span class="sxs-lookup"><span data-stu-id="0edc9-205">This is why the JSON property name `Wind` in the example is not upper case.</span></span>

### <a name="camel-case-dictionary-keys"></a><span data-ttu-id="0edc9-206">Camel durum sözlüğü anahtarları</span><span class="sxs-lookup"><span data-stu-id="0edc9-206">Camel case dictionary keys</span></span>

<span data-ttu-id="0edc9-207">Seri hale getirilecek bir nesnenin bir özelliği `Dictionary<string,TValue>` türünde ise, `string` anahtarlar ortası duruma dönüştürülebilir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-207">If a property of an object to be serialized is of type `Dictionary<string,TValue>`, the `string` keys can be converted to camel case.</span></span> <span data-ttu-id="0edc9-208">Bunu yapmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> ' ı `JsonNamingPolicy.CamelCase` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-208">To do that, set <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> to `JsonNamingPolicy.CamelCase`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="0edc9-209">Anahtar-değer çiftleri `"ColdMinTemp", 20` olan `TemperatureRanges` adlı bir sözlükten bir nesneyi serileştirmek ve `"HotMinTemp", 40` aşağıdaki örnekte olduğu gibi JSON çıktısına neden olur:</span><span class="sxs-lookup"><span data-stu-id="0edc9-209">Serializing an object with a dictionary named `TemperatureRanges` that has key-value pairs `"ColdMinTemp", 20` and `"HotMinTemp", 40` would result in JSON output like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "coldMinTemp": 20,
    "hotMinTemp": 40
  }
}
```

<span data-ttu-id="0edc9-210">Sözlük anahtarları için ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-210">The camel case naming policy for dictionary keys applies to serialization only.</span></span> <span data-ttu-id="0edc9-211">Bir sözlüğün serisini kaldırırsanız, `DictionaryKeyPolicy`için `JsonNamingPolicy.CamelCase` belirtseniz bile anahtarlar JSON dosyasıyla eşleşmeyecektir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-211">If you deserialize a dictionary, the keys will match the JSON file even if you specify `JsonNamingPolicy.CamelCase` for the `DictionaryKeyPolicy`.</span></span>

### <a name="enums-as-strings"></a><span data-ttu-id="0edc9-212">Dizeler dize olarak numaralandırmalar</span><span class="sxs-lookup"><span data-stu-id="0edc9-212">Enums as strings</span></span>

<span data-ttu-id="0edc9-213">Varsayılan olarak, numaralandırmalar sayı olarak serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-213">By default, enums are serialized as numbers.</span></span> <span data-ttu-id="0edc9-214">Enum adlarını dizeler olarak seri hale getirmek için <xref:System.Text.Json.Serialization.JsonStringEnumConverter>kullanın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-214">To serialize enum names as strings, use the <xref:System.Text.Json.Serialization.JsonStringEnumConverter>.</span></span>

<span data-ttu-id="0edc9-215">Örneğin, bir sabit listesi olan aşağıdaki sınıfı seri hale getirmeniz gerektiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="0edc9-215">For example, suppose you need to serialize the following class that has an enum:</span></span>

```csharp
class WeatherForecastWithEnum
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public Summary Summary { get; set; }
}

public enum Summary
{
    Cold, Cool, Warm, Hot
}
```

<span data-ttu-id="0edc9-216">Özet `Hot`, varsayılan olarak seri hale getirilmiş JSON sayısal değeri 3 ' tir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-216">If the Summary is `Hot`, by default the serialized JSON has the numeric value 3:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": 3
}
```

<span data-ttu-id="0edc9-217">Aşağıdaki örnek kod, bunun yerine enum adlarını seri hale getirir ve bunları ortası örneğine dönüştürür:</span><span class="sxs-lookup"><span data-stu-id="0edc9-217">The following sample code serializes the enum names instead, and converts them to camel case:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
jsonWithEnumsAsStrings = JsonSerializer.Serialize(weatherForecastWithEnum, options);
```

<span data-ttu-id="0edc9-218">Elde edilen JSON aşağıdaki örneğe benzer şekilde görünür:</span><span class="sxs-lookup"><span data-stu-id="0edc9-218">The resulting JSON looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "hot"
}
```

<span data-ttu-id="0edc9-219">Aşağıdaki örnekte gösterildiği gibi, diziler olarak Numaralandırmalar için bir dize desteği de, seri durumdan çıkarma için geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-219">The support for enums as strings applies to deserialization also, as shown in the following example:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
weatherForecastWithEnum = JsonSerializer.Deserialize<WeatherForecastWithEnum>(jsonWithEnumsAsStrings, options);
```

## <a name="exclude-properties-from-serialization"></a><span data-ttu-id="0edc9-220">Özellikleri serileştirme dışında tut</span><span class="sxs-lookup"><span data-stu-id="0edc9-220">Exclude properties from serialization</span></span>

<span data-ttu-id="0edc9-221">Varsayılan olarak, tüm ortak özellikler serileştirilir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-221">By default, all public properties are serialized.</span></span> <span data-ttu-id="0edc9-222">Bir kısmının JSON çıktısında görünmesini istemiyorsanız, birkaç seçeneğiniz vardır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-222">If you don't want some of them to appear in the JSON output, you have several options.</span></span> <span data-ttu-id="0edc9-223">Bu bölümde nasıl hariç tutulacak açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="0edc9-223">This section explains how to exclude:</span></span>

* <span data-ttu-id="0edc9-224">Bireysel Özellikler</span><span class="sxs-lookup"><span data-stu-id="0edc9-224">Individual properties</span></span>
* <span data-ttu-id="0edc9-225">Tüm salt okunurdur özellikleri</span><span class="sxs-lookup"><span data-stu-id="0edc9-225">All read-only properties</span></span>
* <span data-ttu-id="0edc9-226">Tüm null değerli özellikler</span><span class="sxs-lookup"><span data-stu-id="0edc9-226">All null-value properties</span></span> 

### <a name="exclude-individual-properties"></a><span data-ttu-id="0edc9-227">Bireysel özellikleri Dışla</span><span class="sxs-lookup"><span data-stu-id="0edc9-227">Exclude individual properties</span></span>

<span data-ttu-id="0edc9-228">Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-228">To ignore individual properties, use the [[JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) attribute.</span></span>

<span data-ttu-id="0edc9-229">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-229">Here's an example type to serialize and JSON output:</span></span>

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

### <a name="exclude-all-read-only-properties"></a><span data-ttu-id="0edc9-230">Tüm salt okuma özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="0edc9-230">Exclude all read-only properties</span></span>

<span data-ttu-id="0edc9-231">Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur.</span><span class="sxs-lookup"><span data-stu-id="0edc9-231">A property is read-only if it contains a public getter but not a public setter.</span></span> <span data-ttu-id="0edc9-232">Tüm salt okuma özelliklerini hariç tutmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> ' ı `true` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-232">To exclude all read-only properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="0edc9-233">Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-233">Here's an example type to serialize and JSON output:</span></span>

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

<span data-ttu-id="0edc9-234">Bu seçenek yalnızca serileştirme için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-234">This option applies only to serialization.</span></span> <span data-ttu-id="0edc9-235">Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-235">During deserialization, read-only properties are ignored by default.</span></span>

### <a name="exclude-all-null-value-properties"></a><span data-ttu-id="0edc9-236">Tüm null değer özelliklerini Dışla</span><span class="sxs-lookup"><span data-stu-id="0edc9-236">Exclude all null value properties</span></span>

<span data-ttu-id="0edc9-237">Tüm null değer özelliklerini dışlamak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> özelliğini `true` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-237">To exclude all null value properties, set the <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> property to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="0edc9-238">Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-238">Here's an example object to serialize and JSON output:</span></span>

|<span data-ttu-id="0edc9-239">Özellik</span><span class="sxs-lookup"><span data-stu-id="0edc9-239">Property</span></span> |<span data-ttu-id="0edc9-240">Değer</span><span class="sxs-lookup"><span data-stu-id="0edc9-240">Value</span></span>  |
|---------|---------|
| <span data-ttu-id="0edc9-241">Tarih</span><span class="sxs-lookup"><span data-stu-id="0edc9-241">Date</span></span>    | <span data-ttu-id="0edc9-242">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="0edc9-242">8/1/2019 12:00:00 AM -07:00</span></span>|
| <span data-ttu-id="0edc9-243">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="0edc9-243">TemperatureC</span></span>| <span data-ttu-id="0edc9-244">25</span><span class="sxs-lookup"><span data-stu-id="0edc9-244">25</span></span> |
| <span data-ttu-id="0edc9-245">Özet</span><span class="sxs-lookup"><span data-stu-id="0edc9-245">Summary</span></span>| <span data-ttu-id="0edc9-246">null</span><span class="sxs-lookup"><span data-stu-id="0edc9-246">null</span></span>|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

<span data-ttu-id="0edc9-247">Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-247">This setting applies to serialization and deserialization.</span></span> <span data-ttu-id="0edc9-248">Seri durumdan çıkarma üzerindeki etkisi hakkında daha fazla bilgi için bkz. [serisi kaldırılırken null değeri yoksay](#ignore-null-when-deserializing).</span><span class="sxs-lookup"><span data-stu-id="0edc9-248">For information about its effect on deserialization, see [Ignore null when deserializing](#ignore-null-when-deserializing).</span></span>

## <a name="customize-character-encoding"></a><span data-ttu-id="0edc9-249">Karakter kodlamasını özelleştirme</span><span class="sxs-lookup"><span data-stu-id="0edc9-249">Customize character encoding</span></span>

<span data-ttu-id="0edc9-250">Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-250">By default, the serializer escapes all non-ASCII characters.</span></span>  <span data-ttu-id="0edc9-251">Diğer bir deyişle, `xxxxx` karakterin Unicode kodu olduğu `\uxxxx` bunların yerini alır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-251">That is, it replaces them with `\uxxxx` where `xxxxx` is the Unicode code of the character.</span></span>  <span data-ttu-id="0edc9-252">Örneğin, `Summary` özelliği Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesnesi şu örnekte gösterildiği gibi serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-252">For example, if the `Summary` property is set to Cyrillic жарко, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a><span data-ttu-id="0edc9-253">Dil karakter kümelerini serileştirme</span><span class="sxs-lookup"><span data-stu-id="0edc9-253">Serialize language character sets</span></span>

<span data-ttu-id="0edc9-254">Bir veya daha fazla dilin karakter kümesini seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi, bir <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>örneği oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin:</span><span class="sxs-lookup"><span data-stu-id="0edc9-254">To serialize the character set(s) of one or more languages, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(UnicodeRanges.Cyrillic, UnicodeRanges.GreekExtended)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="0edc9-255">Bu kod, Kiril ve Yunanca karakterleri seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-255">This code serializes Cyrillic and Greek characters.</span></span> <span data-ttu-id="0edc9-256">Kiril karakterleri aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-256">Cyrillic characters are shown in the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жарко",
}
```

<span data-ttu-id="0edc9-257">Tüm dilleri belirtmek için <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>kullanın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-257">To specify all languages, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

### <a name="serialize-specific-characters"></a><span data-ttu-id="0edc9-258">Belirli karakterleri serileştirme</span><span class="sxs-lookup"><span data-stu-id="0edc9-258">Serialize specific characters</span></span>

<span data-ttu-id="0edc9-259">Diğer bir seçenek de, kaçırılmadan, izin vermek istediğiniz tek tek karakterleri belirtmektir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-259">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="0edc9-260">Aşağıdaki örnek, жарко 'in yalnızca ilk iki karakterini seri hale getirir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-260">The following example serializes only the first two characters of жарко:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
using System.Text.Unicode;
```

```csharp
var encoderSettings = new TextEncoderSettings();
encoderSettings.AllowCharacters('\u0436', '\u0430');
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.Create(encoderSettings)
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="0edc9-261">Yukarıdaki kod tarafından üretilen JSON örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-261">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a><span data-ttu-id="0edc9-262">Tüm karakterleri seri hale getirme</span><span class="sxs-lookup"><span data-stu-id="0edc9-262">Serialize all characters</span></span>

<span data-ttu-id="0edc9-263">Kaçı en aza indirmek için aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0edc9-263">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

```csharp
using System.Text.Encodings.Web;
using System.Text.Json;
```

```csharp
options = new JsonSerializerOptions
{
    Encoder = JavaScriptEncoder.UnsafeRelaxedJsonEscaping
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

> [!CAUTION]
> <span data-ttu-id="0edc9-264">Varsayılan kodlayıcının aksine, `UnsafeRelaxedJsonEscaping` Kodlayıcısı:</span><span class="sxs-lookup"><span data-stu-id="0edc9-264">Unlike the default encoder, the `UnsafeRelaxedJsonEscaping` encoder:</span></span>
>
> * <span data-ttu-id="0edc9-265">`<`, `>`, `&`ve `'`gibi HTML 'ye duyarlı karakterleri atmaz.</span><span class="sxs-lookup"><span data-stu-id="0edc9-265">Doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="0edc9-266">, Örneğin, *karakter kümesi*üzerinde istemci ve sunucu disagreeing neden olabilecek olanlar gibi XSS veya bilgi açıklaması saldırılarına karşı ek derinlemesine savunma korumaları sunmaz.</span><span class="sxs-lookup"><span data-stu-id="0edc9-266">Doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
> * <span data-ttu-id="0edc9-267">, Karakterlerin kaçışsız geçmesine izin verilen varsayılan kodlayıcıdan daha fazla izin verilir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-267">Is more permissive than the default encoder on which characters are allowed to pass through unescaped.</span></span>
>
> <span data-ttu-id="0edc9-268">Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-268">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="0edc9-269">Örneğin, sunucu yanıt üst bilgisini `Content-Type: application/json; charset=utf-8`gönderiyorsa onu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0edc9-269">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="0edc9-270">Ham `UnsafeRelaxedJsonEscaping` çıkışının bir HTML sayfasına veya bir `<script>` öğesine yayılmasın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-270">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="serialize-properties-of-derived-classes"></a><span data-ttu-id="0edc9-271">Türetilmiş sınıfların serileştirme özellikleri</span><span class="sxs-lookup"><span data-stu-id="0edc9-271">Serialize properties of derived classes</span></span>

<span data-ttu-id="0edc9-272">Derleme zamanında seri hale getirilecek tür için belirttiğiniz zaman polimorfik serileştirme desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0edc9-272">Polymorphic serialization isn't supported when you specify at compile time the type to be serialized.</span></span> <span data-ttu-id="0edc9-273">Örneğin, bir `WeatherForecast` sınıfa ve `WeatherForecastWithWind`türetilmiş bir sınıfa sahip olduğunuzu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="0edc9-273">For example, suppose you have a `WeatherForecast` class and a derived class `WeatherForecastWithWind`:</span></span>

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

<span data-ttu-id="0edc9-274">Ve derleme zamanında `Serialize` yönteminin tür bağımsız değişkeninin `WeatherForecast`olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="0edc9-274">And suppose the type argument of the `Serialize` method at compile time is `WeatherForecast`:</span></span>

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

<span data-ttu-id="0edc9-275">Bu senaryoda, `weatherForecast` nesnesi gerçekten `WeatherForecastWithWind` nesnesi olsa bile `WindSpeed` özelliği serileştirilmez.</span><span class="sxs-lookup"><span data-stu-id="0edc9-275">In this scenario, the `WindSpeed` property is not serialized even if the `weatherForecast` object is actually a `WeatherForecastWithWind` object.</span></span> <span data-ttu-id="0edc9-276">Yalnızca temel sınıf özellikleri serileştirilir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-276">Only the base class properties are serialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="0edc9-277">Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-277">This behavior is intended to help prevent accidental exposure of data in a derived runtime-created type.</span></span>

<span data-ttu-id="0edc9-278">Türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-278">To serialize the properties of the derived type, use one of the following approaches:</span></span>

* <span data-ttu-id="0edc9-279">Çalışma zamanında türü belirtmenize izin veren <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemesini çağırın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-279">Call an overload of <xref:System.Text.Json.JsonSerializer.Serialize%2A> that lets you specify the type at runtime:</span></span>

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* <span data-ttu-id="0edc9-280">`object`olarak seri hale getirilecek nesneyi bildirin.</span><span class="sxs-lookup"><span data-stu-id="0edc9-280">Declare the object to be serialized as `object`.</span></span>

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

<span data-ttu-id="0edc9-281">Yukarıdaki örnek senaryoda, her iki yaklaşım da `WindSpeed` özelliğinin JSON çıktısına dahil olmasına neden olur:</span><span class="sxs-lookup"><span data-stu-id="0edc9-281">In the preceding example scenario, both approaches cause the `WindSpeed` property to be included in the JSON output:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

<span data-ttu-id="0edc9-282">Çok biçimli seri kaldırma hakkında bilgi için bkz. çok [biçimli seri kaldırma desteği](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="0edc9-282">For information about polymorphic deserialization, see [Support polymorphic deserialization](system-text-json-converters-how-to.md#support-polymorphic-deserialization).</span></span>

## <a name="allow-comments-and-trailing-commas"></a><span data-ttu-id="0edc9-283">Yorumlara ve sondaki virgülleri izin ver</span><span class="sxs-lookup"><span data-stu-id="0edc9-283">Allow comments and trailing commas</span></span>

<span data-ttu-id="0edc9-284">Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="0edc9-284">By default, comments and trailing commas are not allowed in JSON.</span></span> <span data-ttu-id="0edc9-285">JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini `JsonCommentHandling.Skip` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-285">To allow comments in the JSON, set the <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> property to `JsonCommentHandling.Skip`.</span></span> <span data-ttu-id="0edc9-286">Sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-286">And to allow trailing commas, set the <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="0edc9-287">Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-287">The following example shows how to allow both:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

<span data-ttu-id="0edc9-288">Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-288">Here's example JSON with comments and a trailing comma:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a><span data-ttu-id="0edc9-289">Büyük/küçük harfe duyarsız Özellik eşleştirme</span><span class="sxs-lookup"><span data-stu-id="0edc9-289">Case-insensitive property matching</span></span>

<span data-ttu-id="0edc9-290">Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-290">By default, deserialization looks for case-sensitive property name matches between JSON and the target object properties.</span></span> <span data-ttu-id="0edc9-291">Bu davranışı değiştirmek için <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> ' ı `true` olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-291">To change that behavior, set the <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> to `true`:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

<span data-ttu-id="0edc9-292">Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-292">Here's example JSON with camel case property names.</span></span> <span data-ttu-id="0edc9-293">Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-293">It can be deserialized into the following type that has Pascal case property names.</span></span>

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

## <a name="handle-overflow-json"></a><span data-ttu-id="0edc9-294">Tutamaç taşması JSON</span><span class="sxs-lookup"><span data-stu-id="0edc9-294">Handle overflow JSON</span></span>

<span data-ttu-id="0edc9-295">Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0edc9-295">While deserializing, you might receive data in the JSON that is not represented by properties of the target type.</span></span> <span data-ttu-id="0edc9-296">Örneğin, hedef türünün bu olduğunu varsayalım:</span><span class="sxs-lookup"><span data-stu-id="0edc9-296">For example, suppose your target type is this:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="0edc9-297">Ve seri durumdan çıkarılacak JSON şu şekilde yapılır:</span><span class="sxs-lookup"><span data-stu-id="0edc9-297">And the JSON to be deserialized is this:</span></span>

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

<span data-ttu-id="0edc9-298">Gösterilen türde gösterilen JSON serisini kaldırırsanız `DatesAvailable` ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor.</span><span class="sxs-lookup"><span data-stu-id="0edc9-298">If you deserialize the JSON shown into the type shown, the `DatesAvailable` and `SummaryWords` properties have nowhere to go and are lost.</span></span> <span data-ttu-id="0edc9-299">Bu özellikler gibi ek verileri yakalamak için, [Jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini `Dictionary<string,object>` veya `Dictionary<string,JsonElement>` türünde bir özelliğe uygulayın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-299">To capture extra data such as these properties, apply the [JsonExtensionData](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) attribute to a property of type `Dictionary<string,object>` or `Dictionary<string,JsonElement>`:</span></span>

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

<span data-ttu-id="0edc9-300">Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veriler `ExtensionData` özelliğinin anahtar-değer çiftleri haline gelir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-300">When you deserialize the JSON shown earlier into this sample type, the extra data becomes key-value pairs of the `ExtensionData` property:</span></span>

|<span data-ttu-id="0edc9-301">Özellik</span><span class="sxs-lookup"><span data-stu-id="0edc9-301">Property</span></span> |<span data-ttu-id="0edc9-302">Değer</span><span class="sxs-lookup"><span data-stu-id="0edc9-302">Value</span></span>  |<span data-ttu-id="0edc9-303">Notlar</span><span class="sxs-lookup"><span data-stu-id="0edc9-303">Notes</span></span>  |
|---------|---------|---------|
| <span data-ttu-id="0edc9-304">Tarih</span><span class="sxs-lookup"><span data-stu-id="0edc9-304">Date</span></span>    | <span data-ttu-id="0edc9-305">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="0edc9-305">8/1/2019 12:00:00 AM -07:00</span></span>||
| <span data-ttu-id="0edc9-306">TemperatureC</span><span class="sxs-lookup"><span data-stu-id="0edc9-306">TemperatureC</span></span>| <span data-ttu-id="0edc9-307">0</span><span class="sxs-lookup"><span data-stu-id="0edc9-307">0</span></span> | <span data-ttu-id="0edc9-308">Büyük/küçük harfe duyarlı uyuşmazlık (JSON içinde `temperatureC`), bu nedenle özellik ayarlanmadı.</span><span class="sxs-lookup"><span data-stu-id="0edc9-308">Case-sensitive mismatch (`temperatureC` in the JSON), so the property isn't set.</span></span> |
| <span data-ttu-id="0edc9-309">Özet</span><span class="sxs-lookup"><span data-stu-id="0edc9-309">Summary</span></span> | <span data-ttu-id="0edc9-310">Kolay</span><span class="sxs-lookup"><span data-stu-id="0edc9-310">Hot</span></span> ||
| <span data-ttu-id="0edc9-311">ExtensionData</span><span class="sxs-lookup"><span data-stu-id="0edc9-311">ExtensionData</span></span> | <span data-ttu-id="0edc9-312">temperatureC: 25</span><span class="sxs-lookup"><span data-stu-id="0edc9-312">temperatureC: 25</span></span> |<span data-ttu-id="0edc9-313">Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.</span><span class="sxs-lookup"><span data-stu-id="0edc9-313">Since the case didn't match, this JSON property is an extra and becomes a key-value pair in the dictionary.</span></span>|
|| <span data-ttu-id="0edc9-314">DatesAvailable:</span><span class="sxs-lookup"><span data-stu-id="0edc9-314">DatesAvailable:</span></span><br>  <span data-ttu-id="0edc9-315">8/1/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="0edc9-315">8/1/2019 12:00:00 AM -07:00</span></span><br><span data-ttu-id="0edc9-316">8/2/2019 12:00:00-07:00</span><span class="sxs-lookup"><span data-stu-id="0edc9-316">8/2/2019 12:00:00 AM -07:00</span></span> |<span data-ttu-id="0edc9-317">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-317">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|
| |<span data-ttu-id="0edc9-318">SummaryWords:</span><span class="sxs-lookup"><span data-stu-id="0edc9-318">SummaryWords:</span></span><br><span data-ttu-id="0edc9-319">İyi</span><span class="sxs-lookup"><span data-stu-id="0edc9-319">Cool</span></span><br><span data-ttu-id="0edc9-320">Rüzgarlı</span><span class="sxs-lookup"><span data-stu-id="0edc9-320">Windy</span></span><br><span data-ttu-id="0edc9-321">İnsankimliği</span><span class="sxs-lookup"><span data-stu-id="0edc9-321">Humid</span></span> |<span data-ttu-id="0edc9-322">JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-322">Extra property from the JSON becomes a key-value pair, with an array as the value object.</span></span>|

<span data-ttu-id="0edc9-323">Hedef nesne serileştirildiğinde, uzantı veri anahtarı değer çiftleri, gelen JSON 'da olduğu gibi JSON özellikleri olur:</span><span class="sxs-lookup"><span data-stu-id="0edc9-323">When the target object is serialized, the extension data key value pairs become JSON properties just as they were in the incoming JSON:</span></span>

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

<span data-ttu-id="0edc9-324">`ExtensionData` özelliği adının JSON içinde görünmediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0edc9-324">Notice that the `ExtensionData` property name doesn't appear in the JSON.</span></span> <span data-ttu-id="0edc9-325">Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-325">This behavior lets the JSON make a round trip without losing any extra data that otherwise wouldn't be deserialized.</span></span>

## <a name="ignore-null-when-deserializing"></a><span data-ttu-id="0edc9-326">Seri durumdan çıkarılırken null değeri yoksay</span><span class="sxs-lookup"><span data-stu-id="0edc9-326">Ignore null when deserializing</span></span>

<span data-ttu-id="0edc9-327">Varsayılan olarak, JSON 'daki bir özellik null ise, hedef nesnedeki karşılık gelen özellik null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-327">By default, if a property in JSON is null, the corresponding property in the target object is set to null.</span></span> <span data-ttu-id="0edc9-328">Bazı senaryolarda, target özelliği varsayılan bir değere sahip olabilir ve varsayılan değeri geçersiz kılmak için null değer istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="0edc9-328">In some scenarios, the target property might have a default value, and you don't want a null value to override the default.</span></span>

<span data-ttu-id="0edc9-329">Örneğin, aşağıdaki kodun hedef nesneniz temsil ettiğini varsayalım:</span><span class="sxs-lookup"><span data-stu-id="0edc9-329">For example, suppose the following code represents your target object:</span></span>

```csharp
class WeatherForecastWithDefault
{
    public WeatherForecastWithDefault()
    {
        Summary = "No summary";
    }
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="0edc9-330">Ve aşağıdaki JSON öğesinin seri durumdan çıkarıldığını varsayalım:</span><span class="sxs-lookup"><span data-stu-id="0edc9-330">And suppose the following JSON is deserialized:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": null,
}
```

<span data-ttu-id="0edc9-331">Seri durumdan çıktıktan sonra, `WeatherForecastWithDefault` nesnesinin `Summary` özelliği null.</span><span class="sxs-lookup"><span data-stu-id="0edc9-331">After deserialization, the `Summary` property of the `WeatherForecastWithDefault` object is null.</span></span>

<span data-ttu-id="0edc9-332">Bu davranışı değiştirmek için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> `true`olarak ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="0edc9-332">To change this behavior, set <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> to `true`, as shown in the following example:</span></span>

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithDefault>(json, options);
```

<span data-ttu-id="0edc9-333">Bu seçenekle, `WeatherForecastWithDefault` nesnesinin `Summary` özelliği, serisini kaldırma işleminden sonra varsayılan "Özet yok" değeridir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-333">With this option, the `Summary` property of the `WeatherForecastWithDefault` object is the default value "No summary" after deserialization.</span></span>

<span data-ttu-id="0edc9-334">JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-334">Null values in the JSON are ignored only if they are valid.</span></span> <span data-ttu-id="0edc9-335">Nullable değer türleri için null değerler özel durumlara neden olur.</span><span class="sxs-lookup"><span data-stu-id="0edc9-335">Null values for non-nullable value types cause exceptions.</span></span> <span data-ttu-id="0edc9-336">Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [null yapılamayan değer türlerinde sorun](https://github.com/dotnet/corefx/issues/40922) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="0edc9-336">For more information, see the [issue on non-nullable value types](https://github.com/dotnet/corefx/issues/40922) in the dotnet/corefx repository on GitHub.</span></span>

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a><span data-ttu-id="0edc9-337">Utf8JsonReader, Utf8JsonWriter ve JsonDocument</span><span class="sxs-lookup"><span data-stu-id="0edc9-337">Utf8JsonReader, Utf8JsonWriter, and JsonDocument</span></span>

<span data-ttu-id="0edc9-338"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>, UTF-8 kodlu JSON metnine yönelik yüksek performanslı, düşük bir ayırma, salt ileri bir okuyucudur ve bir `ReadOnlySpan<byte>`okur.</span><span class="sxs-lookup"><span data-stu-id="0edc9-338"><xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="0edc9-339">`Utf8JsonReader`, özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="0edc9-339">The `Utf8JsonReader` is a low-level type that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="0edc9-340"><xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemi, kapsamakta olan `Utf8JsonReader` kullanır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-340">The <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method uses `Utf8JsonReader` under the covers.</span></span>

<span data-ttu-id="0edc9-341"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>, `String`, `Int32`ve `DateTime`gibi ortak .NET türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="0edc9-341"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> is a high-performance way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="0edc9-342">Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür.</span><span class="sxs-lookup"><span data-stu-id="0edc9-342">The writer is a low-level type that can be used to build custom serializers.</span></span> <span data-ttu-id="0edc9-343"><xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemi, kapsamakta olan `Utf8JsonWriter` kullanır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-343">The <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method uses `Utf8JsonWriter` under the covers.</span></span>

<span data-ttu-id="0edc9-344"><xref:System.Text.Json.JsonDocument?displayProperty=fullName>, `Utf8JsonReader`kullanarak salt okunurdur Belge Nesne Modeli (DOM) oluşturma olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-344"><xref:System.Text.Json.JsonDocument?displayProperty=fullName> provides the ability to build a read-only Document Object Model (DOM) by using `Utf8JsonReader`.</span></span> <span data-ttu-id="0edc9-345">DOM, bir JSON yükünde verilere rastgele erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-345">The DOM provides random access to data in a JSON payload.</span></span> <span data-ttu-id="0edc9-346">Yükü oluşturan JSON öğelerine <xref:System.Text.Json.JsonElement> türü aracılığıyla erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-346">The JSON elements that compose the payload can be accessed via the <xref:System.Text.Json.JsonElement> type.</span></span> <span data-ttu-id="0edc9-347">`JsonElement`, JSON metnini ortak .NET türlerine dönüştürmek için API 'lerle birlikte dizi ve nesne numaralandırıcıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-347">The `JsonElement` provides array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="0edc9-348">`JsonDocument`, bir <xref:System.Text.Json.JsonDocument.RootElement> özelliğini kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-348">`JsonDocument` exposes a <xref:System.Text.Json.JsonDocument.RootElement> property.</span></span>

<span data-ttu-id="0edc9-349">Aşağıdaki bölümlerde, bu araçların JSON okuma ve yazma için nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-349">The following sections show how to use these tools for reading and writing JSON.</span></span>

## <a name="use-jsondocument-for-access-to-data"></a><span data-ttu-id="0edc9-350">Veri erişimi için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="0edc9-350">Use JsonDocument for access to data</span></span>

<span data-ttu-id="0edc9-351">Aşağıdaki örnek, verileri rastgele erişim için <xref:System.Text.Json.JsonDocument> sınıfını nasıl kullanacağınızı gösterir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-351">The following example shows how to use the <xref:System.Text.Json.JsonDocument> class for random access to data:</span></span>

```csharp
double sum = 0;
int count = 0;

using (JsonDocument document = JsonDocument.Parse(jsonString))
{
    JsonElement root = document.RootElement;
    JsonElement studentsElement = root.GetProperty("Students");
    foreach (JsonElement student in studentsElement.EnumerateArray())
    {
        if (student.TryGetProperty("Grade", out JsonElement gradeElement))
        {
            sum += gradeElement.GetDouble();
        }
        else
        {
            sum += 70;
        }
        count++;
    }
}

double average = sum / count;
Console.WriteLine($"Average grade: {average}");
```

<span data-ttu-id="0edc9-352">Önceki kod:</span><span class="sxs-lookup"><span data-stu-id="0edc9-352">The preceding code:</span></span>

* <span data-ttu-id="0edc9-353">Çözümlenecek JSON 'ın `jsonString`adlı bir dizede olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-353">Assumes the JSON to analyze is in a string named `jsonString`.</span></span>
* <span data-ttu-id="0edc9-354">Bir `Grade` özelliğine sahip `Students` dizisindeki nesneler için Ortalama bir sınıf hesaplar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-354">Calculates an average grade for objects in a `Students` array that have a `Grade` property.</span></span> 
* <span data-ttu-id="0edc9-355">Bir sınıfa sahip olmayan öğrenciler için varsayılan bir 70 sınıfı atar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-355">Assigns a default grade of 70 for students who don't have a grade.</span></span>
* <span data-ttu-id="0edc9-356">Her yinelemeyle bir `count` değişkenini arttırarak öğrencileri sayar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-356">Counts students by incrementing a `count` variable with each iteration.</span></span> <span data-ttu-id="0edc9-357"><xref:System.Text.Json.JsonElement.GetArrayLength%2A>çağrısı yapmanız bir alternatiftir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-357">An alternative is to call <xref:System.Text.Json.JsonElement.GetArrayLength%2A>:</span></span>

  ```csharp
  count = studentsElement.GetArrayLength();
  ```

<span data-ttu-id="0edc9-358">Bu kodun işlediği JSON örneğine bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-358">Here's an example of the JSON that this code processes:</span></span>

```json
{
  "Class Name": "Science",
  "Teacher's Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-jsondocument-to-write-json"></a><span data-ttu-id="0edc9-359">JSON yazmak için JsonDocument kullanın</span><span class="sxs-lookup"><span data-stu-id="0edc9-359">Use JsonDocument to write JSON</span></span>

<span data-ttu-id="0edc9-360">Aşağıdaki örnek, bir <xref:System.Text.Json.JsonDocument>JSON yazmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-360">The following example shows how to write JSON from a <xref:System.Text.Json.JsonDocument>:</span></span>

```csharp
string jsonString = File.ReadAllText(inputFileName);

var writerOptions = new JsonWriterOptions { Indented = true };
var documentOptions = new JsonDocumentOptions { CommentHandling = JsonCommentHandling.Skip };

using (FileStream fs = File.Create(outputFileName))
using (var writer = new Utf8JsonWriter(fs, options: writerOptions))
using (JsonDocument document = JsonDocument.Parse(jsonString, documentOptions))
{
    JsonElement root = document.RootElement;

    if (root.ValueKind == JsonValueKind.Object)
    {
        writer.WriteStartObject();
    }
    else
    {
        return;
    }

    foreach (JsonProperty property in root.EnumerateObject())
    {
        property.WriteTo(writer);
    }

    writer.WriteEndObject();

    writer.Flush();
}
```

<span data-ttu-id="0edc9-361">Önceki kod:</span><span class="sxs-lookup"><span data-stu-id="0edc9-361">The preceding code:</span></span>

* <span data-ttu-id="0edc9-362">Bir JSON dosyası okur, verileri bir `JsonDocument`yükler ve bir dosyaya biçimlendirilen (düzgün yazdırılmış) JSON yazar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-362">Reads a JSON file, loads the data into a `JsonDocument`, and writes formatted (pretty-printed) JSON to a file.</span></span>
* <span data-ttu-id="0edc9-363">JSON girişi içindeki açıklamalara izin verildiğini ancak yok sayılacağını belirtmek için <xref:System.Text.Json.JsonDocumentOptions> kullanır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-363">Uses <xref:System.Text.Json.JsonDocumentOptions> to specify that comments in the input JSON are allowed but ignored.</span></span>
* <span data-ttu-id="0edc9-364">İşiniz bittiğinde, yazıcı <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> çağırır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-364">When finished, calls <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> on the writer.</span></span> <span data-ttu-id="0edc9-365">Diğer bir seçenek de yazıcı boşaltıatıldığı zaman yazıcının temizlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-365">An alternative is to let the writer autoflush when it's disposed.</span></span> 

<span data-ttu-id="0edc9-366">Örnek kod tarafından işlenecek JSON girişi örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-366">Here's an example of JSON input to be processed by the example code:</span></span>

```json
{"Class Name": "Science","Teacher's Name": "Jane","Semester": "2019-01-01","Students": [{"Name": "John","Grade": 94.3},{"Name": "James","Grade": 81.0},{"Name": "Julia","Grade": 91.9},{"Name": "Jessica","Grade": 72.4},{"Name": "Johnathan"}],"Final": true}
```

<span data-ttu-id="0edc9-367">Sonuç, aşağıdaki düzgün yazdırılmış JSON çıktıdır:</span><span class="sxs-lookup"><span data-stu-id="0edc9-367">The result is the following pretty-printed JSON output:</span></span>

```json
{
  "Class Name": "Science",
  "Teacher\u0027s Name": "Jane",
  "Semester": "2019-01-01",
  "Students": [
    {
      "Name": "John",
      "Grade": 94.3
    },
    {
      "Name": "James",
      "Grade": 81.0
    },
    {
      "Name": "Julia",
      "Grade": 91.9
    },
    {
      "Name": "Jessica",
      "Grade": 72.4
    },
    {
      "Name": "Johnathan"
    }
  ],
  "Final": true
}
```

## <a name="use-utf8jsonwriter"></a><span data-ttu-id="0edc9-368">Utf8JsonWriter kullanma</span><span class="sxs-lookup"><span data-stu-id="0edc9-368">Use Utf8JsonWriter</span></span>

<span data-ttu-id="0edc9-369">Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonWriter> sınıfının nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-369">The following example shows how to use the <xref:System.Text.Json.Utf8JsonWriter> class:</span></span>

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

## <a name="use-utf8jsonreader"></a><span data-ttu-id="0edc9-370">Utf8JsonReader kullanma</span><span class="sxs-lookup"><span data-stu-id="0edc9-370">Use Utf8JsonReader</span></span>

<span data-ttu-id="0edc9-371">Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonReader> sınıfının nasıl kullanılacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-371">The following example shows how to use the <xref:System.Text.Json.Utf8JsonReader> class:</span></span>

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

<span data-ttu-id="0edc9-372">Yukarıdaki kod, `jsonUtf8` değişkeninin UTF-8 olarak kodlanmış geçerli JSON içeren bir bayt dizisi olduğunu varsayar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-372">The preceding code assumes that the `jsonUtf8` variable is a byte array that contains valid JSON, encoded as UTF-8.</span></span>

### <a name="filter-data-using-utf8jsonreader"></a><span data-ttu-id="0edc9-373">Utf8JsonReader kullanarak verileri filtreleme</span><span class="sxs-lookup"><span data-stu-id="0edc9-373">Filter data using Utf8JsonReader</span></span>

<span data-ttu-id="0edc9-374">Aşağıdaki örnek, bir dosyanın zaman uyumlu olarak nasıl okunacağını ve bir değerin nasıl aranacağını gösterir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-374">The following example shows how to read a file synchronously and search for a value:</span></span>

```csharp
class Program
{
    private static readonly byte[] s_nameUtf8 = Encoding.UTF8.GetBytes("name");
    private static readonly byte[] s_universityUtf8 = Encoding.UTF8.GetBytes("University");

    private static void ReaderFromFileSync(string fileName)
    {
         string jsonString = File.ReadAllText(fileName);
         ReadOnlySpan<byte> jsonReadOnlySpan = Encoding.UTF8.GetBytes(jsonString);

        int count = 0;
        int total = 0;

        var json = new Utf8JsonReader(jsonReadOnlySpan, isFinalBlock: true, state: default);

        while (json.Read())
        {
            JsonTokenType tokenType = json.TokenType;

            switch (tokenType)
            {
                case JsonTokenType.StartObject:
                    total++;
                    break;
                case JsonTokenType.PropertyName:
                    if (json.ValueSpan.SequenceEqual(s_nameUtf8))
                    {
                        bool result = json.Read();

                        Debug.Assert(result);  // Assume valid JSON
                        Debug.Assert(json.TokenType == JsonTokenType.String);   // Assume known, valid JSON schema

                        if (json.ValueSpan.EndsWith(s_universityUtf8))
                        {
                            count++;
                        }
                    }
                    break;
            }
        }
        Console.WriteLine($"{count} out of {total} have names that end with 'University'");
    }
}
```

<span data-ttu-id="0edc9-375">Önceki kod:</span><span class="sxs-lookup"><span data-stu-id="0edc9-375">The preceding code:</span></span>

* <span data-ttu-id="0edc9-376">Dosyanın UTF-16 olarak kodlandığını varsayar ve bunu UTF-8 ' e dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0edc9-376">Assumes the file is encoded as UTF-16 and transcodes it into UTF-8.</span></span> <span data-ttu-id="0edc9-377">UTF-8 olarak kodlanmış bir dosya aşağıdaki kodu kullanarak doğrudan bir `ReadOnlySpan<byte>`okunabilir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-377">A file encoded as UTF-8 can be read directly into a `ReadOnlySpan<byte>`, by using the following code:</span></span>

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* <span data-ttu-id="0edc9-378">JSON 'un bir nesne dizisi içerdiğini ve her nesne dize türünde bir "ad" özelliği içerebildiği varsayılır.</span><span class="sxs-lookup"><span data-stu-id="0edc9-378">Assumes the JSON contains an array of objects and each object may contain a "name" property of type string.</span></span>
* <span data-ttu-id="0edc9-379">"University" ile biten nesneleri ve `name` özellik değerlerini sayar.</span><span class="sxs-lookup"><span data-stu-id="0edc9-379">Counts objects and `name` property values that end with "University".</span></span>

<span data-ttu-id="0edc9-380">Yukarıdaki kodun okuya, bir JSON örneği aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0edc9-380">Here's a JSON sample that the preceding code can read.</span></span> <span data-ttu-id="0edc9-381">Sonuçtaki Özet ileti "2 ' den 4 ' ün" University "ile biten adlara sahiptir:</span><span class="sxs-lookup"><span data-stu-id="0edc9-381">The resulting summary message is "2 out of 4 have names that end with 'University'":</span></span>

```json
[
  {
    "web_pages": [ "https://contoso.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contoso.edu" ],
    "name": "Contoso Community College"
  },
  {
    "web_pages": [ "http://fabrikam.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikam.edu" ],
    "name": "Fabrikam Community College"
  },
  {
    "web_pages": [ "http://www.contosouniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "contosouniversity.edu" ],
    "name": "Contoso University"
  },
  {
    "web_pages": [ "http://www.fabrikamuniversity.edu/" ],
    "alpha_two_code": "US",
    "state-province": null,
    "country": "United States",
    "domains": [ "fabrikamuniversity.edu" ],
    "name": "Fabrikam University"
  }
]
```

## <a name="additional-resources"></a><span data-ttu-id="0edc9-382">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="0edc9-382">Additional resources</span></span>

* [<span data-ttu-id="0edc9-383">System. Text. JSON genel bakış</span><span class="sxs-lookup"><span data-stu-id="0edc9-383">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="0edc9-384">System. Text. JSON API başvurusu</span><span class="sxs-lookup"><span data-stu-id="0edc9-384">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="0edc9-385">System. Text. JSON için özel dönüştürücüler yazma</span><span class="sxs-lookup"><span data-stu-id="0edc9-385">Write custom converters for System.Text.Json</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="0edc9-386">System. Text. JSON içinde DateTime ve DateTimeOffset desteği</span><span class="sxs-lookup"><span data-stu-id="0edc9-386">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
