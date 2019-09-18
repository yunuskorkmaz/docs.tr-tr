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
# <a name="how-to-serialize-json-in-net"></a>.NET ' te JSON seri hale getirme

> [!IMPORTANT]
> JSON serileştirme belgeleri oluşturma aşamasındadır. Bu makale tüm senaryoları kapsamamaktadır. Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [System. Text. JSON sorunlarını](https://github.com/dotnet/corefx/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) , özellikle de [JSON-işlevselliği-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc)etiketini inceleyin.

Bu makalede, <xref:System.Text.Json> JavaScript nesne gösterimi (JSON) ve öğesinden seri hale getirmek ve seri durumdan çıkarmak için ad alanı kullanımı gösterilmektedir. Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.

## <a name="namespaces"></a>Ad Alanları

<xref:System.Text.Json> Ad alanı tüm giriş noktalarını ve ana türleri içerir. Ad <xref:System.Text.Json.Serialization> alanı, serileştirme ve seri durumdan çıkarma ile ilgili gelişmiş senaryolar ve özelleştirme için öznitelikler ve API 'leri içerir. Bu nedenle, bu makalede gösterilen kod örnekleri aşağıdaki `using` yönergelerden birini veya her ikisini de gerektirir:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

Ad alanındaki öznitelikler Şu anda sürümünde `System.Text.Json`desteklenmemektedir. <xref:System.Runtime.Serialization>

## <a name="how-to-write-net-objects-to-json-serialize"></a>.NET nesnelerini JSON 'a yazma (serileştirme)

JSON 'yi bir dizeye yazmak için, genel tür parametresi veya genel tür çıkarımı kullanarak [Jsonserializer. Serialize](xref:System.Text.Json.JsonSerializer.Serialize*)çağırın:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast = ... ;
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

' Nin <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemeleri, ' a <xref:System.IO.Stream>serileştirmenizi sağlar. `Stream` Aşırı yüklemelerin zaman uyumsuz sürümleri mevcuttur.

### <a name="serialize-to-utf-8"></a>UTF-8 ' e serileştirme

[Jsonserializer. SerializeToUtf8Bytes](xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes*)çağrısı:

```csharp
byte[] utf8Json = JsonSerializer.SerializeToUtf8Bytes<WeatherForecast>(weatherForecast);
```

Alternatif olarak, ' ı <xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.Utf8JsonWriter> alan bir aşırı yükleme vardır.

UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır. Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).

## <a name="default-serialization-behavior"></a>Varsayılan serileştirme davranışı

* Tüm ortak özellikler serileştirilir. [Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties).
* [Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERIN, ASCII aralığındaki HTML duyarlı karakterlerin yanı sıra [JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterlerle çıkar.
* JSON, Mini kullanılıyor. İsteğe bağlı olarak [JSON 'ı yazdırabilirsiniz](#serialize-to-formatted-json).
* JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir. [JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names).
* [Döngüsel başvurular](https://github.com/dotnet/corefx/issues/38579) algılandı ve özel durumlar oluşturuldu.
* Alanlar hariç tutulur.

Desteklenen türler şunlardır:

* Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.
* Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Tek boyutlu ve pürüzlü Diziler (`ArrayName[][]`).
* `Dictionary<string,TValue>`burada, `TValue`veya birpoco.`object` `JsonElement`
* Aşağıdaki ad alanlarından [koleksiyon türleri](https://github.com/dotnet/corefx/issues/36643) :
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

## <a name="how-to-read-json-into-net-objects-deserialize"></a>JSON 'ı .NET Objects 'e okuma (serisini kaldırma)

Bir dizeden seri durumdan çıkarmak için, [Jsonserializer. serisini](xref:System.Text.Json.JsonSerializer.Deserialize*)çağırın:

```csharp
string json = ... ;

var weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json);
```

Bir örnek için [serileştirme](#how-to-write-net-objects-to-json-serialize) bölümüne bakın. JSON ve .NET nesnesi aynıdır, ancak yön ters çevrilir.

' Nin <xref:System.Text.Json.JsonSerializer.Deserialize*> aşırı yüklemeleri, ' `Stream`dan seri durumdan çıkarabilmeniz için  `Stream` Aşırı yüklemelerin zaman uyumsuz sürümleri mevcuttur.

### <a name="deserialize-from-utf-8"></a>UTF-8 ' den serisini kaldırma

Bir [jsonserializer çağırın.](xref:System.Text.Json.JsonSerializer.Deserialize*) bir `Utf8JsonReader` veya `ReadOnlySpan<byte>`alan aşırı yükleme serisini kaldırma:

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

## <a name="default-deserialization-behavior"></a>Varsayılan seri kaldırma davranışı

* Özellik adı eşleştirmesi büyük/küçük harfe duyarlıdır. İsteğe bağlı olarak [büyük/küçük harf](#case-insensitive-property-matching)duyarlı belirtebilirsiniz.
* JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.
* Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.
* [Sabit nesneler](https://github.com/dotnet/corefx/issues/38569) veya [salt okunurdur özellikleri](https://github.com/dotnet/corefx/issues/38163) seri durumundan çıkarma desteklenmez.
* Numaralandırmalar sayı olarak desteklenir.
* Alanlar desteklenmiyor.
* JSON 'da açıklama veya sondaki virgüller özel durum oluşturur. [Yorumlara ve sondaki virgüllerin bulunmasına izin](#allow-comments-and-trailing-commas)verebilirsiniz.
* [Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.

## <a name="serialize-to-formatted-json"></a>Biçimlendirilen JSON 'a serileştirme

Doğru <xref:System.Text.Json.JsonSerializerOptions.WriteIndented> olarak ayarla:

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

Olarak ayarlayın <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling> ve true olarak <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas>ayarlayın: `JsonCommentHandling.Skip`

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

## <a name="customize-json-names"></a>JSON adlarını özelleştirme

Bu bölümde nasıl yapılacağı açıklanmaktadır:

* Bireysel özellik adlarını özelleştirme
* Tüm özellik adlarını ortası durumuna Dönüştür
* Özel özellik adlandırma ilkesi uygulama
* Sözlük anahtarlarını ortası örneğine Dönüştür

[Numaralandırmaların otomatik olarak ortası örneğine dönüştürülmesi](https://github.com/dotnet/corefx/issues/37725)desteklenmez.

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

Ayarla <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> :`JsonNamingPolicy.CamelCase`

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
* Öznitelikleri tarafından `[JsonPropertyName]` geçersiz kılınır.

### <a name="use-a-custom-json-property-naming-policy"></a>Özel bir JSON Özellik adlandırma ilkesi kullanma

<xref:System.Text.Json.JsonNamingPolicy.ConvertName*>Türet <xref:System.Text.Json.JsonNamingPolicy> ve geçersiz kıl:

```csharp
class UpperCaseNamingPolicy : JsonNamingPolicy
{
    public override string ConvertName(string name)
    {
        return name.ToUpper();
    }
}
```

Adlandırma <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy> ilkesi sınıfınızın bir örneğine ayarlayın:

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
* Öznitelikleri tarafından `[JsonPropertyName]` geçersiz kılınır.

### <a name="camel-case-dictionary-keys"></a>Camel durum sözlüğü anahtarları

Seri hale getirilecek bir nesnenin özelliği tür `Dictionary<string,Tvalue>`ise `string` , anahtarlar ortası duruma dönüştürülebilir. Bunu yapmak için şu şekilde <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase`ayarlayın:

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
| Özet| kolay|
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

Bu bölümde nasıl hariç tutulacak açıklanmaktadır:

* Bireysel Özellikler
* Tüm salt okunurdur özellikleri
* Tüm null değerli özellikler 

### <a name="exclude-individual-properties"></a>Bireysel özellikleri Dışla

[[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.

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

Doğru <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties> olarak ayarla:

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

Doğru <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> olarak ayarla:

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

Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir. Seri durumdan çıkarma sırasında, JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır. [Nullable değer türleri Için null değerler özel durumlara neden olur](https://github.com/dotnet/corefx/issues/40922).

## <a name="case-insensitive-property-matching"></a>Büyük/küçük harfe duyarsız Özellik eşleştirme

Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar. Bu davranışı değiştirmek için, true <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive> olarak ayarlayın:

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

Derleme zamanında seri hale getirilecek tür için belirttiğiniz zaman polimorfik serileştirme desteklenmez. Örneğin, bir `WeatherForecast` sınıfınız ve türetilmiş bir sınıfınız `WeatherForecastWithWind`olduğunu varsayalım:

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

Ve, derleme `Serialize` `WeatherForecast`süresi sırasında yönteminin geçirildiği veya çıkartılan tür olduğunu varsayalım:

```csharp
string json = JsonSerializer.Serialize<WeatherForecast>(weatherForecast);
```

```csharp
WeatherForecast weatherForecast;
//...
json = JsonSerializer.Serialize(weatherForecast);
```

Bu senaryoda, `WindSpeed` `weatherForecast` nesne gerçekten bir `WeatherForecastWithWind` nesne olsa bile Özellik serileştirilmez. Yalnızca temel sınıf özellikleri serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.

Türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:

* Çalışma zamanında türü belirtmenize `Serialize` izin veren aşırı yüklemesini çağırın:

  ```csharp
  json = JsonSerializer.Serialize(weatherForecast, weatherForecast.GetType());
  ```

* Seri hale getirilecek `object`nesneyi bildirin.

  ```csharp
  json = JsonSerializer.Serialize<object>(weatherForecast);
  ```

Yukarıdaki örnek senaryoda, her iki yaklaşım `WindSpeed` özelliğin JSON çıktısına dahil olmasına neden olur:

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

Gösterilen `DatesAvailable` türde gösterilen JSON serisini kaldırırsanız, ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor. Bu özellikler gibi ek verileri yakalamak için, [jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini veya `Dictionary<string,object>` `Dictionary<string,JsonElement>`türünde bir özelliğe uygulayın:

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

Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veri `ExtensionData` özelliğin anahtar-değer çiftleri haline gelir:

|Özellik |Değer  |Notlar  |
|---------|---------|---------|
| Tarih    | 8/1/2019 12:00:00-07:00||
| TemperatureC| 0 | Büyük/küçük harfe duyarlı`temperatureC` uyuşmazlık (JSON 'da), bu nedenle özellik ayarlanmadı. |
| Özet | kolay ||
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

`ExtensionData` Özellik adının JSON içinde görünmediğine dikkat edin. Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.

## <a name="use-utf8jsonwriter-directly"></a>Doğrudan Utf8JsonWriter kullanma

Aşağıdaki örnek <xref:System.Text.Json.Utf8JsonWriter> sınıfının doğrudan nasıl kullanılacağını gösterir.

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

Aşağıdaki örnek <xref:System.Text.Json.Utf8JsonReader> sınıfının doğrudan nasıl kullanılacağını gösterir. Kod, `jsonUtf8` değişkenin UTF-8 olarak kodlanmış geçerli JSON içeren bir bayt dizisi olduğunu varsayar.

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

## <a name="additional-resources"></a>Ek kaynaklar

* [System. Text. JSON genel bakış](system-text-json-overview.md)
* [System. Text. JSON API başvurusu](xref:System.Text.Json)
* [System. Text. JSON içinde DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
