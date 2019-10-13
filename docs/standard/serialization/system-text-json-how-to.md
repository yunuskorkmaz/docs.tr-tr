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
# <a name="how-to-serialize-and-deserialize-json-in-net"></a>.NET 'te JSON serileştirme ve serisini kaldırma

> [!IMPORTANT]
> JSON serileştirme belgeleri oluşturma aşamasındadır. Bu makale tüm senaryoları kapsamamaktadır. Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [System. Text. JSON sorunlarını](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) , özellikle de [JSON-işlevselliği-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)etiketini inceleyin.

Bu makalede, JavaScript Nesne Gösterimi (JSON) içinde ve dışında seri hale getirmek ve seri durumdan çıkarmak için <xref:System.Text.Json> ad alanının nasıl kullanılacağı gösterilmektedir. Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.

## <a name="namespaces"></a>Ad Alanları

@No__t-0 ad alanı tüm giriş noktalarını ve ana türleri içerir. @No__t-0 ad alanı, serileştirme ve seri durumdan çıkarma için özel gelişmiş senaryolar ve özelleştirmeler için öznitelikler ve API 'Leri içerir. Bu nedenle, bu makalede gösterilen kod örnekleri, aşağıdaki `using` yönergelerinden birini veya her ikisini de gerektirir:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

@No__t-0 ad alanındaki öznitelikler Şu anda `System.Text.Json` ' de desteklenmemektedir.

## <a name="how-to-write-net-objects-to-json-serialize"></a>.NET nesnelerini JSON 'a yazma (serileştirme)

JSON 'yi bir dizeye yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın. Aşağıdaki örnek genel tür parametresiyle bir aşırı yükleme kullanır:

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

Genel tür parametresini atlayabilir ve bunun yerine genel tür çıkarımı kullanabilirsiniz:

```csharp
WeatherForecast weatherForecast;
//...
string json = JsonSerializer.Serialize(weatherForecast);
```

Aşağıda, koleksiyonları ve iç içe sınıfları içeren bir örnek türü verilmiştir:

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

JSON çıktısı varsayılan olarak Mini olarak belirlenir: 

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

@No__t aşırı yüklemeleri-0 <xref:System.IO.Stream> ' e serileştirmenizi sağlar. @No__t-0 aşırı yüklemelerinin zaman uyumsuz sürümleri mevcuttur.

### <a name="serialize-to-utf-8"></a>UTF-8 ' e serileştirme

UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemini çağırın:

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

Alternatif olarak, bir <xref:System.Text.Json.Utf8JsonWriter> alan <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemesi kullanılabilir.

UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır. Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).

## <a name="serialization-behavior"></a>Serileştirme davranışı

* Varsayılan olarak, tüm ortak özellikler serileştirilir. [Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties).
* [Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERIN, ASCII aralığındaki HTML duyarlı karakterlerin yanı sıra [JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterlerle çıkar.
* Varsayılan olarak JSON, Mini olarak belirlenir. JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.
* Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir. [JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names).
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

## <a name="how-to-read-json-into-net-objects-deserialize"></a>JSON 'ı .NET Objects 'e okuma (serisini kaldırma)

Bir dizeden serisini kaldırmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın:

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

Bir örnek için [serileştirme](#how-to-write-net-objects-to-json-serialize) bölümüne bakın. JSON ve .NET nesnesi aynıdır, ancak yön ters çevrilir.

@No__t aşırı yüklemeleri-0 `Stream` ' den seri durumdan çıkarmasına izin verir.  @No__t-0 aşırı yüklemelerinin zaman uyumsuz sürümleri mevcuttur.

### <a name="deserialize-from-utf-8"></a>UTF-8 ' den serisini kaldırma

UTF-8 ' den seri durumdan çıkarmak için, aşağıdaki örneklerde gösterildiği gibi, `Utf8JsonReader` veya `ReadOnlySpan<byte>` alan <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> aşırı yüklemesini çağırın:

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

## <a name="deserialization-behavior"></a>Seri durumdan çıkarma davranışı

* Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır. [Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).
* JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.
* Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.
* Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez. Daha fazla bilgi için bkz. [sabit nesne desteğiyle Ilgili GitHub sorunu](https://github.com/dotnet/corefx/issues/38569) ve GitHub 'daki DotNet/corefx deposundaki [salt okunurdur özellik desteği](https://github.com/dotnet/corefx/issues/38163) .
* Varsayılan olarak, numaralandırmalar sayı olarak desteklenir.
* Alanlar desteklenmiyor.
* Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur. Gerekirse [açıklamalara ve sondaki virgüllerin belirtilmesine izin](#allow-comments-and-trailing-commas) verebilirsiniz.
* [Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.

## <a name="serialize-to-formatted-json"></a>Biçimlendirilen JSON 'a serileştirme

JSON çıkışını oldukça yazdırmak için <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> ' ı `true` olarak ayarlayın:

```csharp
var options = new JsonSerializerOptions
{
    WriteIndented = true,
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Seri hale getirilecek bir örnek türü ve JSON çıktısı aşağıda verilmiştir:

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

## <a name="allow-comments-and-trailing-commas"></a>Yorumlara ve sondaki virgülleri izin ver

JSON 'da varsayılan açıklamalara ve sondaki virgüllerin kullanımına izin verilmez. JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini `JsonCommentHandling.Skip` olarak ayarlayın. Sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini `true` olarak ayarlayın. Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:

```csharp
var options = new JsonSerializerOptions
{
    ReadCommentHandling = JsonCommentHandling.Skip,
    AllowTrailingCommas = true
};
var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="customize-json-names"></a>JSON adlarını özelleştirme

Varsayılan olarak, özellik adları ve sözlük anahtarları, büyük/küçük harf gibi JSON çıktısında değiştirilmez. Bu bölümde nasıl yapılacağı açıklanmaktadır:

* Bireysel özellik adlarını özelleştirme
* Tüm özellik adlarını ortası durumuna Dönüştür
* Özel özellik adlandırma ilkesi uygulama
* Sözlük anahtarlarını ortası örneğine Dönüştür

Şu anda, Numaralandırmaların otomatik olarak ortası örneğine dönüştürülmesi desteklenmez. Daha fazla bilgi için GitHub 'daki DotNet/corefx deposunda [kamel durum desteğinin numaralandırmasında sorun](https://github.com/dotnet/corefx/issues/37725) bölümüne bakın.

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

Ortası durum özelliği adlandırma ilkesi:

* Serileştirme ve seri durumdan çıkarma için geçerlidir.
* @No__t-0 öznitelikleri tarafından geçersiz kılınır.

### <a name="use-a-custom-json-property-naming-policy"></a>Özel bir JSON Özellik adlandırma ilkesi kullanma

Özel bir JSON Özellik adlandırma ilkesi kullanmak için, <xref:System.Text.Json.JsonNamingPolicy> ' dan türeten bir sınıf oluşturun ve aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> yöntemini geçersiz kılın:

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
* @No__t-0 öznitelikleri tarafından geçersiz kılınır.

### <a name="camel-case-dictionary-keys"></a>Camel durum sözlüğü anahtarları

Seri hale getirilecek bir nesnenin bir özelliği `Dictionary<string,TValue>` türünde ise, `string` anahtarlar ortası duruma dönüştürülebilir. Bunu yapmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> ' ı `JsonNamingPolicy.CamelCase` olarak ayarlayın:

```csharp
var options = new JsonSerializerOptions
{
    DictionaryKeyPolicy = JsonNamingPolicy.CamelCase
};
json = JsonSerializer.Serialize(weatherForecast, options);
```

Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:

|Özellik |Değer  |
|---------|---------|
| Tarih    | 8/1/2019 12:00:00-07:00|
| TemperatureC| 25 |
| Özet| Sık Erişimli|
| TemperatureRanges | Durgun, 20<br>Sık erişimli, 40|

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

Ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir.

## <a name="exclude-properties"></a>Dışlama özellikleri

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

Tüm salt okuma özelliklerini hariç tutmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> ' ı `true` olarak ayarlayın:

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

Bu seçenek yalnızca serileştirme için geçerlidir. Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır. Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur.

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
| Özet| değer|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25
}
```

Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir. Seri durumdan çıkarma sırasında, JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır. Nullable değer türleri için null değerler özel durumlara neden olur. Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [null yapılamayan değer türlerinde sorun](https://github.com/dotnet/corefx/issues/40922) bölümüne bakın.

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

## <a name="include-properties-of-derived-classes"></a>Türetilmiş sınıfların özelliklerini Ekle

Derleme zamanında seri hale getirilecek tür için belirttiğiniz zaman polimorfik serileştirme desteklenmez. Örneğin, `WeatherForecast` sınıfına ve türetilmiş bir sınıfa sahip olduğunuzu varsayalım-1 @no__t:

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

Ve, derleme zamanında `Serialize` yönteminin `WeatherForecast` olduğunu veya bu tür tarafından algılanır olduğunu varsayalım:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
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

* Çalışma zamanında türü belirtmenizi sağlayan <xref:System.Text.Json.JsonSerializer.Serialize%2A> ' nın aşırı yüklemesini çağırın:

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* @No__t-0 olarak seri hale getirilecek nesneyi bildirin.

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
| Özet | Sık Erişimli ||
| ExtensionData | temperatureC: 25 |Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.|
|| DatesAvailable:<br>  8/1/2019 12:00:00-07:00<br>8/2/2019 12:00:00-07:00 |JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.|
| |SummaryWords:<br>Seyrek Erişimli<br>Rüzgarlı<br>İnsankimliği |JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.|

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

@No__t-0 özellik adının JSON içinde görünmediğine dikkat edin. Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.

## <a name="use-utf8jsonwriter-directly"></a>Doğrudan Utf8JsonWriter kullanma

Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonWriter> sınıfının doğrudan nasıl kullanılacağını gösterir.

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

## <a name="use-utf8jsonreader-directly"></a>Doğrudan Utf8JsonReader kullanma

Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonReader> sınıfının doğrudan nasıl kullanılacağını gösterir. Kod, `jsonUtf8` değişkeninin UTF-8 olarak kodlanmış geçerli JSON içeren bir bayt dizisi olduğunu varsayar.

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

## <a name="additional-resources"></a>Ek kaynaklar

* [System. Text. JSON genel bakış](system-text-json-overview.md)
* [System. Text. JSON API başvurusu](xref:System.Text.Json)
* [System. Text. JSON içinde DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
