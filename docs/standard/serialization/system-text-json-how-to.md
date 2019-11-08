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
# <a name="how-to-serialize-and-deserialize-json-in-net"></a>.NET 'te JSON serileştirme ve serisini kaldırma

> [!IMPORTANT]
> JSON serileştirme belgeleri oluşturma aşamasındadır. Bu makale tüm senaryoları kapsamamaktadır. Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [System. Text. JSON sorunlarını](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) , özellikle de [JSON-işlevselliği-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)etiketini inceleyin.

Bu makalede, JavaScript Nesne Gösterimi (JSON) içinde ve dışında seri hale getirmek ve seri durumdan çıkarmak için <xref:System.Text.Json> ad alanının nasıl kullanılacağı gösterilmektedir. Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.

## <a name="namespaces"></a>Ad Alanları

<xref:System.Text.Json> ad alanı tüm giriş noktalarını ve ana türleri içerir. <xref:System.Text.Json.Serialization> ad alanı, serileştirme ve seri durumdan çıkarma için özel gelişmiş senaryolar ve özelleştirmeler için öznitelikler ve API 'Leri içerir. Bu makalede gösterilen kod örnekleri, bu ad alanlarından biri veya her ikisi için `using` yönergeler gerektirir:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<xref:System.Runtime.Serialization> ad alanındaki öznitelikler Şu anda `System.Text.Json`desteklenmiyor.

## <a name="how-to-write-net-objects-to-json-serialize"></a>.NET nesnelerini JSON 'a yazma (serileştirme)

JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.

Aşağıdaki örnek bir dize olarak JSON oluşturur:

```csharp
string json = JsonSerializer.Serialize(weatherForecast);
```

Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:

```csharp
File.WriteAllText(outputFileName, JsonSerializer.Serialize(weatherForecast));
```

Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:

```csharp
using (FileStream fs = File.Create(outputFileName))
{
    await JsonSerializer.SerializeAsync(fs, weatherForecast);
}
```

Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır. `Serialize()` aşırı yüklemesi genel bir tür parametresi alır:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

### <a name="serialization-example"></a>Serileştirme örneği

Koleksiyonları ve iç içe sınıfları içeren örnek bir tür aşağıda verilmiştir:

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

Önceki türün bir örneğinin serileştirilmesi için JSON çıktısı aşağıdaki örnekteki gibi görünür. JSON çıktısı varsayılan olarak Mini olarak belirlenir: 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureC":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":{"DegreesCelsius":20},"Low":{"DegreesCelsius":-10}},"Hot":{"High":{"DegreesCelsius":60},"Low":{"DegreesCelsius":20}}},"SummaryWords":["Cool","Windy","Humid"]}
```

Aşağıdaki örnek, biçimlendirilen aynı JSON 'ı gösterir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):

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

### <a name="serialize-to-utf-8"></a>UTF-8 ' e serileştirme

UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemi çağırın:

```csharp
byte[] jsonUtf8Bytes = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

<xref:System.Text.Json.Utf8JsonWriter> alan <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemesi de mevcuttur.

UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır. Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).

## <a name="serialization-behavior"></a>Serileştirme davranışı

* Varsayılan olarak, tüm ortak özellikler serileştirilir. [Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties-from-serialization).
* [Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERIN, ASCII aralığındaki HTML duyarlı karakterlerin yanı sıra [JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterlerle çıkar.
* Varsayılan olarak JSON, Mini olarak belirlenir. JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.
* Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir. [JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names-and-values).
* Döngüsel başvurular algılandı ve özel durumlar oluşturuldu. Daha fazla bilgi için GitHub 'daki DotNet/corefx deposunda [Döngüsel başvurularda sorun](https://github.com/dotnet/corefx/issues/38579) bölümüne bakın.
* Şu anda, alanlar hariç tutulur.

Desteklenen türler şunlardır:

* Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.
* Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Tek boyutlu ve pürüzlü Diziler (`ArrayName[][]`).
* `TValue`;  `object`, `JsonElement` veya bir POCO.
* Aşağıdaki ad alanlarından Koleksiyonlar. Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [koleksiyon desteği sorunu](https://github.com/dotnet/corefx/issues/36643) bölümüne bakın.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

Ek türleri işlemek için [özel dönüştürücüler uygulayabilir](system-text-json-converters-how-to.md) veya yerleşik dönüştürücüler tarafından desteklenmeyen işlevler sağlayabilirsiniz.

## <a name="how-to-read-json-into-net-objects-deserialize"></a>JSON 'ı .NET Objects 'e okuma (serisini kaldırma)

Bir dizeden veya dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın.

Aşağıdaki örnek bir dizeden JSON okur:

```csharp
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

Zaman uyumlu kod kullanarak bir dosyadan seri durumdan çıkarmak için, aşağıdaki örnekte gösterildiği gibi dosyayı bir dizeye okuyun:

```csharp
string jsonString = File.ReadAllText(inputFileName);
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(jsonString);
```

Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> yöntemi çağırın:

```csharp
using (FileStream fs = File.OpenRead(inputFileName))
{
    weatherForecast = await JsonSerializer.DeserializeAsync<WeatherForecast>(fs);
}
```

Örnek bir tür ve karşılık gelen JSON için [serileştirme örnek](#serialization-example) bölümüne bakın.

### <a name="deserialize-from-utf-8"></a>UTF-8 ' den serisini kaldırma

UTF-8 ' den seri durumdan çıkarmak için, aşağıdaki örneklerde gösterildiği gibi `Utf8JsonReader` veya `ReadOnlySpan<byte>`alan <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> aşırı yüklemeyi çağırın. Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.

```csharp
var readOnlySpan = new ReadOnlySpan<byte>(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(readOnlySpan);
```

```csharp
var utf8Reader = new Utf8JsonReader(jsonUtf8Bytes);
weatherForecast = JsonSerializer.Deserialize<WeatherForecastMin>(ref utf8Reader);
```

## <a name="deserialization-behavior"></a>Seri durumdan çıkarma davranışı

* Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır. [Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).
* JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.
* Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.
* Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez. Daha fazla bilgi için bkz. [sabit nesne desteğiyle Ilgili GitHub sorunu](https://github.com/dotnet/corefx/issues/38569) ve GitHub 'daki DotNet/corefx deposundaki [salt okunurdur özellik desteği](https://github.com/dotnet/corefx/issues/38163) .
* Varsayılan olarak, numaralandırmalar sayı olarak desteklenir. [Enum adlarını dizeler olarak seri hale](#enums-as-strings)getirebilirsiniz.
* Alanlar desteklenmiyor.
* Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur. [Yorumlara ve sondaki virgüllerin bulunmasına izin](#allow-comments-and-trailing-commas)verebilirsiniz.
* [Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.

Yerleşik dönüştürücüler tarafından desteklenmeyen işlevselliği sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .

## <a name="serialize-to-formatted-json"></a>Biçimlendirilen JSON 'a serileştirme

JSON çıkışını oldukça yazdırmak için <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> ' ı `true` olarak ayarlayın:

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Aşağıda, seri hale getirilebilir ve düzgün şekilde yazdırılan JSON çıkışının örnek bir türü verilmiştir:

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

## <a name="customize-json-names-and-values"></a>JSON adlarını ve değerlerini özelleştirme

Varsayılan olarak, özellik adları ve sözlük anahtarları, büyük/küçük harf gibi JSON çıktısında değiştirilmez. Sabit listesi değerleri sayı olarak temsil edilir. Bu bölümde nasıl yapılacağı açıklanmaktadır:

* Bireysel özellik adlarını özelleştirme
* Tüm özellik adlarını ortası durumuna Dönüştür
* Özel özellik adlandırma ilkesi uygulama
* Sözlük anahtarlarını ortası örneğine Dönüştür
* Numaralandırmaları dizelere ve ortası örneğine Dönüştür 

JSON özellik adlarını ve değerlerini özel olarak işleme gerektiren diğer senaryolar için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md).

### <a name="customize-individual-property-names"></a>Bireysel özellik adlarını özelleştirme

Ayrı özelliklerin adını ayarlamak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) özniteliğini kullanın.

Serileştirme ve sonuç JSON için örnek bir tür aşağıda verilmiştir:

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

Bu öznitelik tarafından ayarlanan özellik adı:

* Serileştirme ve seri durumundan çıkarma için her iki yönde de geçerlidir.
* Özellik adlandırma ilkelerine göre önceliklidir.

### <a name="use-camel-case-for-all-json-property-names"></a>Tüm JSON Özellik adları için ortası Case kullanın

Tüm JSON Özellik adları için ortası durumunu kullanmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> ' ı `JsonNamingPolicy.CamelCase` olarak ayarlayın:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:

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

Ortası durum özelliği adlandırma ilkesi:

* Serileştirme ve seri durumdan çıkarma için geçerlidir.
* `[JsonPropertyName]` öznitelikleri tarafından geçersiz kılınır. Bu, örnekte `Wind` JSON özelliği adının ortası durum olmadığı durumdur.

### <a name="use-a-custom-json-property-naming-policy"></a>Özel bir JSON Özellik adlandırma ilkesi kullanma

Özel bir JSON Özellik adlandırma ilkesi kullanmak için, <xref:System.Text.Json.JsonNamingPolicy> türeten bir sınıf oluşturun ve aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> yöntemini geçersiz kılın:

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

Sonra <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> özelliğini, adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNamingPolicy = new UpperCaseNamingPolicy()
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:

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

JSON özelliği adlandırma ilkesi:

* Serileştirme ve seri durumdan çıkarma için geçerlidir.
* `[JsonPropertyName]` öznitelikleri tarafından geçersiz kılınır. Bu, örnekte `Wind` JSON özelliği adının büyük harfle değil.

### <a name="camel-case-dictionary-keys"></a>Camel durum sözlüğü anahtarları

Seri hale getirilecek bir nesnenin bir özelliği `Dictionary<string,TValue>` türünde ise, `string` anahtarlar ortası duruma dönüştürülebilir. Bunu yapmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> ' ı `JsonNamingPolicy.CamelCase` olarak ayarlayın:

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Anahtar-değer çiftleri `"ColdMinTemp", 20` olan `TemperatureRanges` adlı bir sözlükten bir nesneyi serileştirmek ve `"HotMinTemp", 40` aşağıdaki örnekte olduğu gibi JSON çıktısına neden olur:

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

Sözlük anahtarları için ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir. Bir sözlüğün serisini kaldırırsanız, `DictionaryKeyPolicy`için `JsonNamingPolicy.CamelCase` belirtseniz bile anahtarlar JSON dosyasıyla eşleşmeyecektir.

### <a name="enums-as-strings"></a>Dizeler dize olarak numaralandırmalar

Varsayılan olarak, numaralandırmalar sayı olarak serileştirilir. Enum adlarını dizeler olarak seri hale getirmek için <xref:System.Text.Json.Serialization.JsonStringEnumConverter>kullanın.

Örneğin, bir sabit listesi olan aşağıdaki sınıfı seri hale getirmeniz gerektiğini varsayalım:

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

Özet `Hot`, varsayılan olarak seri hale getirilmiş JSON sayısal değeri 3 ' tir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": 3
}
```

Aşağıdaki örnek kod, bunun yerine enum adlarını seri hale getirir ve bunları ortası örneğine dönüştürür:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
jsonWithEnumsAsStrings = JsonSerializer.Serialize(weatherForecastWithEnum, options);
```

Elde edilen JSON aşağıdaki örneğe benzer şekilde görünür:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "hot"
}
```

Aşağıdaki örnekte gösterildiği gibi, diziler olarak Numaralandırmalar için bir dize desteği de, seri durumdan çıkarma için geçerlidir:

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new JsonStringEnumConverter(JsonNamingPolicy.CamelCase));
weatherForecastWithEnum = JsonSerializer.Deserialize<WeatherForecastWithEnum>(jsonWithEnumsAsStrings, options);
```

## <a name="exclude-properties-from-serialization"></a>Özellikleri serileştirme dışında tut

Varsayılan olarak, tüm ortak özellikler serileştirilir. Bir kısmının JSON çıktısında görünmesini istemiyorsanız, birkaç seçeneğiniz vardır. Bu bölümde nasıl hariç tutulacak açıklanmaktadır:

* Bireysel Özellikler
* Tüm salt okunurdur özellikleri
* Tüm null değerli özellikler 

### <a name="exclude-individual-properties"></a>Bireysel özellikleri Dışla

Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.

Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:

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

### <a name="exclude-all-read-only-properties"></a>Tüm salt okuma özelliklerini Dışla

Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur. Tüm salt okuma özelliklerini hariç tutmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> ' ı `true` olarak ayarlayın:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreReadOnlyProperties = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:

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

Bu seçenek yalnızca serileştirme için geçerlidir. Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.

### <a name="exclude-all-null-value-properties"></a>Tüm null değer özelliklerini Dışla

Tüm null değer özelliklerini dışlamak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> özelliğini `true` olarak ayarlayın:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:

|Özellik |Değer  |
|---------|---------|
| Tarih    | 8/1/2019 12:00:00-07:00|
| TemperatureC| 25 |
| Özet| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir. Seri durumdan çıkarma üzerindeki etkisi hakkında daha fazla bilgi için bkz. [serisi kaldırılırken null değeri yoksay](#ignore-null-when-deserializing).

## <a name="customize-character-encoding"></a>Karakter kodlamasını özelleştirme

Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar.  Diğer bir deyişle, `xxxxx` karakterin Unicode kodu olduğu `\uxxxx` bunların yerini alır.  Örneğin, `Summary` özelliği Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesnesi şu örnekte gösterildiği gibi serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Dil karakter kümelerini serileştirme

Bir veya daha fazla dilin karakter kümesini seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi, bir <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>örneği oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin:

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

Bu kod, Kiril ve Yunanca karakterleri seri hale getirir. Kiril karakterleri aşağıdaki örnekte gösterilmiştir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жарко",
}
```

Tüm dilleri belirtmek için <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>kullanın.

### <a name="serialize-specific-characters"></a>Belirli karakterleri serileştirme

Diğer bir seçenek de, kaçırılmadan, izin vermek istediğiniz tek tek karakterleri belirtmektir. Aşağıdaki örnek, жарко 'in yalnızca ilk iki karakterini seri hale getirir:

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

Yukarıdaki kod tarafından üretilen JSON örneği aşağıda verilmiştir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Tüm karakterleri seri hale getirme

Kaçı en aza indirmek için aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>kullanabilirsiniz:

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
> Varsayılan kodlayıcının aksine, `UnsafeRelaxedJsonEscaping` Kodlayıcısı:
>
> * `<`, `>`, `&`ve `'`gibi HTML 'ye duyarlı karakterleri atmaz.
> * , Örneğin, *karakter kümesi*üzerinde istemci ve sunucu disagreeing neden olabilecek olanlar gibi XSS veya bilgi açıklaması saldırılarına karşı ek derinlemesine savunma korumaları sunmaz.
> * , Karakterlerin kaçışsız geçmesine izin verilen varsayılan kodlayıcıdan daha fazla izin verilir.
>
> Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın. Örneğin, sunucu yanıt üst bilgisini `Content-Type: application/json; charset=utf-8`gönderiyorsa onu kullanabilirsiniz. Ham `UnsafeRelaxedJsonEscaping` çıkışının bir HTML sayfasına veya bir `<script>` öğesine yayılmasın.

## <a name="serialize-properties-of-derived-classes"></a>Türetilmiş sınıfların serileştirme özellikleri

Derleme zamanında seri hale getirilecek tür için belirttiğiniz zaman polimorfik serileştirme desteklenmez. Örneğin, bir `WeatherForecast` sınıfa ve `WeatherForecastWithWind`türetilmiş bir sınıfa sahip olduğunuzu varsayalım:

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

Ve derleme zamanında `Serialize` yönteminin tür bağımsız değişkeninin `WeatherForecast`olduğunu varsayalım:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

Bu senaryoda, `weatherForecast` nesnesi gerçekten `WeatherForecastWithWind` nesnesi olsa bile `WindSpeed` özelliği serileştirilmez. Yalnızca temel sınıf özellikleri serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.

Türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:

* Çalışma zamanında türü belirtmenize izin veren <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemesini çağırın:

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* `object`olarak seri hale getirilecek nesneyi bildirin.

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

Yukarıdaki örnek senaryoda, her iki yaklaşım da `WindSpeed` özelliğinin JSON çıktısına dahil olmasına neden olur:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

Çok biçimli seri kaldırma hakkında bilgi için bkz. çok [biçimli seri kaldırma desteği](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

## <a name="allow-comments-and-trailing-commas"></a>Yorumlara ve sondaki virgülleri izin ver

Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez. JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini `JsonCommentHandling.Skip` olarak ayarlayın. Sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini `true` olarak ayarlayın. Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Büyük/küçük harfe duyarsız Özellik eşleştirme

Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar. Bu davranışı değiştirmek için <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> ' ı `true` olarak ayarlayın:

```csharp
var options = new JsonSerializerOptions
{
    PropertyNameCaseInsensitive = true,
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(weatherForecast, options);
```

Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir. Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.

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

## <a name="handle-overflow-json"></a>Tutamaç taşması JSON

Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz. Örneğin, hedef türünün bu olduğunu varsayalım:

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

Ve seri durumdan çıkarılacak JSON şu şekilde yapılır:

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

Gösterilen türde gösterilen JSON serisini kaldırırsanız `DatesAvailable` ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor. Bu özellikler gibi ek verileri yakalamak için, [Jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini `Dictionary<string,object>` veya `Dictionary<string,JsonElement>` türünde bir özelliğe uygulayın:

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

Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veriler `ExtensionData` özelliğinin anahtar-değer çiftleri haline gelir:

|Özellik |Değer  |Notlar  |
|---------|---------|---------|
| Tarih    | 8/1/2019 12:00:00-07:00||
| TemperatureC| 0 | Büyük/küçük harfe duyarlı uyuşmazlık (JSON içinde `temperatureC`), bu nedenle özellik ayarlanmadı. |
| Özet | Kolay ||
| ExtensionData | temperatureC: 25 |Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.|
|| DatesAvailable:<br>  8/1/2019 12:00:00-07:00<br>8/2/2019 12:00:00-07:00 |JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.|
| |SummaryWords:<br>İyi<br>Rüzgarlı<br>İnsankimliği |JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.|

Hedef nesne serileştirildiğinde, uzantı veri anahtarı değer çiftleri, gelen JSON 'da olduğu gibi JSON özellikleri olur:

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

`ExtensionData` özelliği adının JSON içinde görünmediğine dikkat edin. Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.

## <a name="ignore-null-when-deserializing"></a>Seri durumdan çıkarılırken null değeri yoksay

Varsayılan olarak, JSON 'daki bir özellik null ise, hedef nesnedeki karşılık gelen özellik null olarak ayarlanır. Bazı senaryolarda, target özelliği varsayılan bir değere sahip olabilir ve varsayılan değeri geçersiz kılmak için null değer istemezsiniz.

Örneğin, aşağıdaki kodun hedef nesneniz temsil ettiğini varsayalım:

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

Ve aşağıdaki JSON öğesinin seri durumdan çıkarıldığını varsayalım:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": null,
}
```

Seri durumdan çıktıktan sonra, `WeatherForecastWithDefault` nesnesinin `Summary` özelliği null.

Bu davranışı değiştirmek için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> `true`olarak ayarlayın:

```csharp
var options = new JsonSerializerOptions
{
    IgnoreNullValues = true
};
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithDefault>(json, options);
```

Bu seçenekle, `WeatherForecastWithDefault` nesnesinin `Summary` özelliği, serisini kaldırma işleminden sonra varsayılan "Özet yok" değeridir.

JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır. Nullable değer türleri için null değerler özel durumlara neden olur. Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [null yapılamayan değer türlerinde sorun](https://github.com/dotnet/corefx/issues/40922) bölümüne bakın.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter ve JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>, UTF-8 kodlu JSON metnine yönelik yüksek performanslı, düşük bir ayırma, salt ileri bir okuyucudur ve bir `ReadOnlySpan<byte>`okur. `Utf8JsonReader`, özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür. <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemi, kapsamakta olan `Utf8JsonReader` kullanır.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>, `String`, `Int32`ve `DateTime`gibi ortak .NET türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur. Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür. <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemi, kapsamakta olan `Utf8JsonWriter` kullanır.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>, `Utf8JsonReader`kullanarak salt okunurdur Belge Nesne Modeli (DOM) oluşturma olanağı sağlar. DOM, bir JSON yükünde verilere rastgele erişim sağlar. Yükü oluşturan JSON öğelerine <xref:System.Text.Json.JsonElement> türü aracılığıyla erişilebilir. `JsonElement`, JSON metnini ortak .NET türlerine dönüştürmek için API 'lerle birlikte dizi ve nesne numaralandırıcıları sağlar. `JsonDocument`, bir <xref:System.Text.Json.JsonDocument.RootElement> özelliğini kullanıma sunar.

Aşağıdaki bölümlerde, bu araçların JSON okuma ve yazma için nasıl kullanılacağı gösterilmektedir.

## <a name="use-jsondocument-for-access-to-data"></a>Veri erişimi için JsonDocument kullanın

Aşağıdaki örnek, verileri rastgele erişim için <xref:System.Text.Json.JsonDocument> sınıfını nasıl kullanacağınızı gösterir:

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

Önceki kod:

* Çözümlenecek JSON 'ın `jsonString`adlı bir dizede olduğunu varsayar.
* Bir `Grade` özelliğine sahip `Students` dizisindeki nesneler için Ortalama bir sınıf hesaplar. 
* Bir sınıfa sahip olmayan öğrenciler için varsayılan bir 70 sınıfı atar.
* Her yinelemeyle bir `count` değişkenini arttırarak öğrencileri sayar. <xref:System.Text.Json.JsonElement.GetArrayLength%2A>çağrısı yapmanız bir alternatiftir:

  ```csharp
  count = studentsElement.GetArrayLength();
  ```

Bu kodun işlediği JSON örneğine bir örnek aşağıda verilmiştir:

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

## <a name="use-jsondocument-to-write-json"></a>JSON yazmak için JsonDocument kullanın

Aşağıdaki örnek, bir <xref:System.Text.Json.JsonDocument>JSON yazmayı gösterir:

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

Önceki kod:

* Bir JSON dosyası okur, verileri bir `JsonDocument`yükler ve bir dosyaya biçimlendirilen (düzgün yazdırılmış) JSON yazar.
* JSON girişi içindeki açıklamalara izin verildiğini ancak yok sayılacağını belirtmek için <xref:System.Text.Json.JsonDocumentOptions> kullanır.
* İşiniz bittiğinde, yazıcı <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> çağırır. Diğer bir seçenek de yazıcı boşaltıatıldığı zaman yazıcının temizlemesini sağlar. 

Örnek kod tarafından işlenecek JSON girişi örneği aşağıda verilmiştir:

```json
{"Class Name": "Science","Teacher's Name": "Jane","Semester": "2019-01-01","Students": [{"Name": "John","Grade": 94.3},{"Name": "James","Grade": 81.0},{"Name": "Julia","Grade": 91.9},{"Name": "Jessica","Grade": 72.4},{"Name": "Johnathan"}],"Final": true}
```

Sonuç, aşağıdaki düzgün yazdırılmış JSON çıktıdır:

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

## <a name="use-utf8jsonwriter"></a>Utf8JsonWriter kullanma

Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonWriter> sınıfının nasıl kullanılacağını gösterir:

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

## <a name="use-utf8jsonreader"></a>Utf8JsonReader kullanma

Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonReader> sınıfının nasıl kullanılacağını gösterir:

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

Yukarıdaki kod, `jsonUtf8` değişkeninin UTF-8 olarak kodlanmış geçerli JSON içeren bir bayt dizisi olduğunu varsayar.

### <a name="filter-data-using-utf8jsonreader"></a>Utf8JsonReader kullanarak verileri filtreleme

Aşağıdaki örnek, bir dosyanın zaman uyumlu olarak nasıl okunacağını ve bir değerin nasıl aranacağını gösterir:

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

Önceki kod:

* Dosyanın UTF-16 olarak kodlandığını varsayar ve bunu UTF-8 ' e dönüştürür. UTF-8 olarak kodlanmış bir dosya aşağıdaki kodu kullanarak doğrudan bir `ReadOnlySpan<byte>`okunabilir:

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* JSON 'un bir nesne dizisi içerdiğini ve her nesne dize türünde bir "ad" özelliği içerebildiği varsayılır.
* "University" ile biten nesneleri ve `name` özellik değerlerini sayar.

Yukarıdaki kodun okuya, bir JSON örneği aşağıda verilmiştir. Sonuçtaki Özet ileti "2 ' den 4 ' ün" University "ile biten adlara sahiptir:

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

## <a name="additional-resources"></a>Ek kaynaklar

* [System. Text. JSON genel bakış](system-text-json-overview.md)
* [System. Text. JSON API başvurusu](xref:System.Text.Json)
* [System. Text. JSON için özel dönüştürücüler yazma](system-text-json-converters-how-to.md)
* [System. Text. JSON içinde DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
