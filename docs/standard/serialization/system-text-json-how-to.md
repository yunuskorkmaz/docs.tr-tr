---
title: .NET kullanarak C# JSON serileştirmek ve serisini kaldırma
ms.date: 09/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: a9c690e736a08c729a4099d5e7a519ed17ec282c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705801"
---
# <a name="how-to-serialize-and-deserialize-json-in-net"></a>.NET 'te JSON serileştirme ve serisini kaldırma

Bu makalede, JavaScript Nesne Gösterimi (JSON) içinde ve içinde seri hale getirmek ve seri durumdan çıkarmak için <xref:System.Text.Json> ad alanının nasıl kullanılacağı gösterilmektedir.

Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.

Seri hale getirme örnek kodunun çoğu, JSON 'ı (örneğin girintileme ve insanlar okunabilirlik için boşluk) `true` <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> belirler. Üretim kullanımı için genellikle bu ayar için `false` varsayılan değerini kabul etmiş olursunuz.

## <a name="namespaces"></a>{1&gt;Ad alanları&lt;1}

<xref:System.Text.Json> ad alanı tüm giriş noktalarını ve ana türleri içerir. <xref:System.Text.Json.Serialization> ad alanı, serileştirme ve seri durumdan çıkarma için özel gelişmiş senaryolar ve özelleştirmeler için öznitelikler ve API 'Leri içerir. Bu makalede gösterilen kod örnekleri, bu ad alanlarından biri veya her ikisi için `using` yönergeler gerektirir:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<xref:System.Runtime.Serialization> ad alanındaki öznitelikler Şu anda `System.Text.Json`desteklenmiyor.

## <a name="how-to-write-net-objects-to-json-serialize"></a>.NET nesnelerini JSON 'a yazma (serileştirme)

JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.

Aşağıdaki örnek bir dize olarak JSON oluşturur:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır. `Serialize()` aşırı yüklemesi genel bir tür parametresi alır:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>Serileştirme örneği

Aşağıda, koleksiyonları ve iç içe yerleştirilmiş bir sınıfı içeren örnek bir sınıf verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

Önceki türün bir örneğinin serileştirilmesi için JSON çıktısı aşağıdaki örnekteki gibi görünür. JSON çıktısı varsayılan olarak Mini olarak belirlenir: 

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

Aşağıdaki örnek, biçimlendirilen aynı JSON 'ı gösterir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):

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

### <a name="serialize-to-utf-8"></a>UTF-8 ' e serileştirme

UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemi çağırın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

<xref:System.Text.Json.Utf8JsonWriter> alan <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemesi de mevcuttur.

UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır. Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).

## <a name="serialization-behavior"></a>Serileştirme davranışı

* Varsayılan olarak, tüm ortak özellikler serileştirilir. [Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties-from-serialization).
* [Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.
* Varsayılan olarak JSON, Mini olarak belirlenir. JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.
* Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir. [JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names-and-values).
* Döngüsel başvurular algılandı ve özel durumlar oluşturuldu. Daha fazla bilgi için bkz. GitHub 'daki DotNet/corefx deposundaki [Döngüsel başvurularda 38579 sorunu](https://github.com/dotnet/corefx/issues/38579) .
* Şu anda, alanlar hariç tutulur.

Desteklenen türler şunlardır:

* Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.
* Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Tek boyutlu ve pürüzlü Diziler (`ArrayName[][]`).
* `Dictionary<string,TValue>` `TValue` `object`, `JsonElement`veya bir POCO.
* Aşağıdaki ad alanlarından Koleksiyonlar. Daha fazla bilgi için GitHub 'daki DotNet/corefx deposundaki [koleksiyon desteği sorunu](https://github.com/dotnet/corefx/issues/36643) bölümüne bakın.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

Ek türleri işlemek veya yerleşik dönüştürücüler tarafından desteklenmeyen işlevler sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .

## <a name="how-to-read-json-into-net-objects-deserialize"></a>JSON 'ı .NET Objects 'e okuma (serisini kaldırma)

Bir dizeden veya dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın.

Aşağıdaki örnek, bir dizeden JSON okur ve daha önce [serileştirme örneği](#serialization-example)için gösterilen `WeatherForecast` sınıfının bir örneğini oluşturur:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

Zaman uyumlu kod kullanarak bir dosyadan seri durumdan çıkarmak için, aşağıdaki örnekte gösterildiği gibi dosyayı bir dizeye okuyun:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> yöntemi çağırın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>UTF-8 ' den serisini kaldırma

UTF-8 ' den seri durumdan çıkarmak için, aşağıdaki örneklerde gösterildiği gibi `Utf8JsonReader` veya `ReadOnlySpan<byte>`alan <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> aşırı yüklemeyi çağırın. Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>Seri durumdan çıkarma davranışı

* Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır. [Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).
* JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.
* Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.
* Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez. Daha fazla bilgi için bkz. GitHub [sorunu 38569, sabit nesne desteği hakkında](https://github.com/dotnet/corefx/issues/38569) , GitHub 'daki DotNet/corefx deposundaki [salt okuma özellik desteği üzerinde 38163](https://github.com/dotnet/corefx/issues/38163) .
* Varsayılan olarak, numaralandırmalar sayı olarak desteklenir. [Enum adlarını dizeler olarak seri hale](#enums-as-strings)getirebilirsiniz.
* Alanlar desteklenmiyor.
* Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur. [Yorumlara ve sondaki virgüllerin bulunmasına izin](#allow-comments-and-trailing-commas)verebilirsiniz.
* [Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.

Yerleşik dönüştürücüler tarafından desteklenmeyen işlevselliği sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .

## <a name="serialize-to-formatted-json"></a>Biçimlendirilen JSON 'a serileştirme

JSON çıkışını gerçekten yazdırmak için <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true`olarak ayarlayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

Aşağıda, seri hale getirilebilir ve düzgün şekilde yazdırılan JSON çıkışının örnek bir türü verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="customize-json-names-and-values"></a>JSON adlarını ve değerlerini özelleştirme

Varsayılan olarak, özellik adları ve sözlük anahtarları, büyük/küçük harf gibi JSON çıktısında değiştirilmez. Sabit listesi değerleri sayı olarak temsil edilir. Bu bölümde nasıl yapılacağı açıklanmaktadır:

* [Bireysel özellik adlarını özelleştirme](#customize-individual-property-names)
* [Tüm özellik adlarını ortası durumuna Dönüştür](#use-camel-case-for-all-json-property-names)
* [Özel özellik adlandırma ilkesi uygulama](#use-a-custom-json-property-naming-policy)
* [Sözlük anahtarlarını ortası örneğine Dönüştür](#camel-case-dictionary-keys)
* [Numaralandırmaları dizelere ve ortası örneğine Dönüştür](#enums-as-strings) 

JSON özellik adlarını ve değerlerini özel olarak işleme gerektiren diğer senaryolar için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md).

### <a name="customize-individual-property-names"></a>Bireysel özellik adlarını özelleştirme

Ayrı özelliklerin adını ayarlamak için [[Jsonpropertyname]](xref:System.Text.Json.Serialization.JsonPropertyNameAttribute) özniteliğini kullanın.

Serileştirme ve sonuç JSON için örnek bir tür aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "Wind": 35
}
```

Bu öznitelik tarafından ayarlanan özellik adı:

* Serileştirme ve seri durumundan çıkarma için her iki yönde de geçerlidir.
* Özellik adlandırma ilkelerine göre önceliklidir.

### <a name="use-camel-case-for-all-json-property-names"></a>Tüm JSON Özellik adları için ortası Case kullanın

Tüm JSON Özellik adları için ortası durumunu kullanmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase`olarak ayarlayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

Sonra <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> özelliğini, adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

```json
{
  "DATE": "2019-08-01T00:00:00-07:00",
  "TEMPERATURECELSIUS": 25,
  "SUMMARY": "Hot",
  "Wind": 35
}
```

JSON özelliği adlandırma ilkesi:

* Serileştirme ve seri durumdan çıkarma için geçerlidir.
* `[JsonPropertyName]` öznitelikleri tarafından geçersiz kılınır. Bu, örnekte `Wind` JSON özelliği adının büyük harfle değil.

### <a name="camel-case-dictionary-keys"></a>Camel durum sözlüğü anahtarları

Seri hale getirilecek bir nesnenin özelliği `Dictionary<string,TValue>`türünde ise, `string` anahtarlar ortası duruma dönüştürülebilir. Bunu yapmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase`olarak ayarlayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

Anahtar-değer çiftleri `"ColdMinTemp", 20` olan `TemperatureRanges` adlı bir sözlükten bir nesneyi serileştirmek ve `"HotMinTemp", 40` aşağıdaki örnekte olduğu gibi JSON çıktısına neden olur:

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

Sözlük anahtarları için ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir. Bir sözlüğün serisini kaldırırsanız, `DictionaryKeyPolicy`için `JsonNamingPolicy.CamelCase` belirtseniz bile anahtarlar JSON dosyasıyla eşleşmeyecektir.

### <a name="enums-as-strings"></a>Dizeler dize olarak numaralandırmalar

Varsayılan olarak, numaralandırmalar sayı olarak serileştirilir. Enum adlarını dizeler olarak seri hale getirmek için <xref:System.Text.Json.Serialization.JsonStringEnumConverter>kullanın.

Örneğin, bir sabit listesi olan aşağıdaki sınıfı seri hale getirmeniz gerektiğini varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Özet `Hot`, varsayılan olarak seri hale getirilmiş JSON sayısal değeri 3 ' tir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

Aşağıdaki örnek kod, sayısal değerler yerine enum adlarını seri hale getirir ve adları ortası örneğine dönüştürür:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

Elde edilen JSON aşağıdaki örneğe benzer şekilde görünür:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

Aşağıdaki örnekte gösterildiği gibi, sabit listesi dize adları da seri durumdan çıkarılmış olabilir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a>Özellikleri serileştirme dışında tut

Varsayılan olarak, tüm ortak özellikler serileştirilir. Bir kısmının JSON çıktısında görünmesini istemiyorsanız, birkaç seçeneğiniz vardır. Bu bölümde nasıl hariç tutulacak açıklanmaktadır:

* [Bireysel Özellikler](#exclude-individual-properties)
* [Tüm salt okunurdur özellikleri](#exclude-all-read-only-properties)
* [Tüm null değerli özellikler](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a>Bireysel özellikleri Dışla

Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.

Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a>Tüm salt okuma özelliklerini Dışla

Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur. Tüm salt okuma özelliklerini hariç tutmak için, aşağıdaki örnekte gösterildiği gibi, <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> `true`olarak ayarlayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Bu seçenek yalnızca serileştirme için geçerlidir. Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.

### <a name="exclude-all-null-value-properties"></a>Tüm null değer özelliklerini Dışla

Tüm null değer özelliklerini dışlamak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> özelliğini `true`olarak ayarlayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:

|Özellik |Değer  |
|---------|---------|
| Tarih    | 8/1/2019 12:00:00-07:00|
| TemperatureCelsius| 25 |
| Özet| {1&gt;null&lt;1}|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir. Seri durumdan çıkarma üzerindeki etkisi hakkında daha fazla bilgi için bkz. [serisi kaldırılırken null değeri yoksay](#ignore-null-when-deserializing).

## <a name="customize-character-encoding"></a>Karakter kodlamasını özelleştirme

Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar.  Diğer bir deyişle, `xxxx` karakterin Unicode kodu olduğu `\uxxxx` bunların yerini alır.  Örneğin, `Summary` özelliği Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesnesi şu örnekte gösterildiği gibi serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Dil karakter kümelerini serileştirme

Bir veya daha fazla dilin karakter kümesini kaçış olmadan seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi, bir <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>örneği oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

Bu kod, Kiril veya Yunan karakterlerinden kaçış yapmaz. `Summary` özelliği Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesnesi şu örnekte gösterildiği gibi serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Tüm dil kümelerini kaçış olmadan seri hale getirmek için <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>kullanın.

### <a name="serialize-specific-characters"></a>Belirli karakterleri serileştirme

Diğer bir seçenek de, kaçırılmadan, izin vermek istediğiniz tek tek karakterleri belirtmektir. Aşağıdaki örnek, жарко 'in yalnızca ilk iki karakterini seri hale getirir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

Yukarıdaki kod tarafından üretilen JSON örneği aşağıda verilmiştir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Tüm karakterleri seri hale getirme

Kaçı en aza indirmek için aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>kullanabilirsiniz:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> Varsayılan kodlayıcıyla karşılaştırıldığında `UnsafeRelaxedJsonEscaping` kodlayıcı, karakterlerin kaçışsız geçmesine izin verme konusunda daha fazla izne sahiptir:
>
> * `<`, `>`, `&`ve `'`gibi HTML 'ye duyarlı karakterlerin kaçış yapmaz.
> * Bu, XSS veya bilgi açıklama saldırılarına karşı ek derinlemesine savunma korumaları sunmaz, örneğin, *karakter*kümesinde istemci ve sunucu disagreeing neden olabilir.
>
> Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın. Örneğin, sunucu yanıt üst bilgisini `Content-Type: application/json; charset=utf-8`gönderiyorsa onu kullanabilirsiniz. Ham `UnsafeRelaxedJsonEscaping` çıkışının bir HTML sayfasına veya bir `<script>` öğesine yayılmasın.

## <a name="serialize-properties-of-derived-classes"></a>Türetilmiş sınıfların serileştirme özellikleri

Derleme zamanında seri hale getirilecek tür için belirttiğiniz zaman polimorfik serileştirme desteklenmez. Örneğin, bir `WeatherForecast` sınıfa ve `WeatherForecastDerived`türetilmiş bir sınıfa sahip olduğunuzu varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

Ve derleme zamanında `Serialize` yönteminin tür bağımsız değişkeninin `WeatherForecast`olduğunu varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

Bu senaryoda, `weatherForecast` nesnesi gerçekten bir `WeatherForecastDerived` nesnesi olsa bile `WindSpeed` özelliği serileştirilmez. Yalnızca temel sınıf özellikleri serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.

Türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:

* Çalışma zamanında türü belirtmenize izin veren <xref:System.Text.Json.JsonSerializer.Serialize%2A> aşırı yüklemesini çağırın:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* `object`olarak seri hale getirilecek nesneyi bildirin.

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

Yukarıdaki örnek senaryoda, her iki yaklaşım da `WindSpeed` özelliğin JSON çıktısına dahil olmasına neden olur:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "WindSpeed": 35
}
```

Çok biçimli seri kaldırma hakkında bilgi için bkz. çok [biçimli seri kaldırma desteği](system-text-json-converters-how-to.md#support-polymorphic-deserialization).

## <a name="allow-comments-and-trailing-commas"></a>Yorumlara ve sondaki virgülleri izin ver

Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez. JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini `JsonCommentHandling.Skip`olarak ayarlayın.
Sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini `true`olarak ayarlayın. Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Büyük/küçük harfe duyarsız Özellik eşleştirme

Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar. Bu davranışı değiştirmek için <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> `true`olarak ayarlayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir. Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>Tutamaç taşması JSON

Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz. Örneğin, hedef türünün bu olduğunu varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Ve seri durumdan çıkarılacak JSON şu şekilde yapılır:

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

Gösterilen türde gösterilen JSON serisini kaldırırsanız, `DatesAvailable` ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor. Bu özellikler gibi ek verileri yakalamak için, `Dictionary<string,object>` veya `Dictionary<string,JsonElement>`türünde bir özelliğe [Jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini uygulayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veriler `ExtensionData` özelliğinin anahtar-değer çiftleri haline gelir:

|Özellik |Değer  |Notlar  |
|---------|---------|---------|
| Tarih    | 8/1/2019 12:00:00-07:00||
| TemperatureCelsius| 0 | Büyük/küçük harfe duyarlı uyuşmazlık (JSON içinde`temperatureCelsius`), bu nedenle özellik ayarlanmadı. |
| Özet | Sık Erişimli ||
| ExtensionData | temperatureCelsius: 25 |Büyük/küçük harf eşleşmediğinden, bu JSON özelliği çok fazla olur ve sözlükte anahtar-değer çifti olur.|
|| DatesAvailable:<br>  8/1/2019 12:00:00-07:00<br>8/2/2019 12:00:00-07:00 |JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.|
| |SummaryWords:<br>Seyrek Erişimli<br>Rüzgarlı<br>İnsankimliği |JSON 'dan fazladan özellik, değer nesnesi olarak bir dizi ile anahtar-değer çifti haline gelir.|

Hedef nesne serileştirildiğinde, uzantı veri anahtarı değer çiftleri, gelen JSON 'da olduğu gibi JSON özellikleri olur:

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

`ExtensionData` özelliği adının JSON içinde görünmediğine dikkat edin. Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.

## <a name="ignore-null-when-deserializing"></a>Seri durumdan çıkarılırken null değeri yoksay

Varsayılan olarak, JSON 'daki bir özellik null ise, hedef nesnedeki karşılık gelen özellik null olarak ayarlanır. Bazı senaryolarda, target özelliği varsayılan bir değere sahip olabilir ve varsayılan değeri geçersiz kılmak için null değer istemezsiniz.

Örneğin, aşağıdaki kodun hedef nesneniz temsil ettiğini varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

Ve aşağıdaki JSON öğesinin seri durumdan çıkarıldığını varsayalım:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Seri durumdan çıktıktan sonra, `WeatherForecastWithDefault` nesnesinin `Summary` özelliği null.

Bu davranışı değiştirmek için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> `true`olarak ayarlayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

Bu seçenekle, `WeatherForecastWithDefault` nesnesinin `Summary` özelliği, serisini kaldırma işleminden sonra varsayılan "Özet yok" değeridir.

JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır. Nullable değer türleri için null değerler özel durumlara neden olur. Daha fazla bilgi için bkz. GitHub 'daki DotNet/corefx deposundaki [null yapılamayan değer türlerinde 40922 sorunu](https://github.com/dotnet/corefx/issues/40922) .

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter ve JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>, UTF-8 kodlu JSON metnine yönelik yüksek performanslı, düşük bir ayırma, salt ileri bir okuyucudur ve bir `ReadOnlySpan<byte>`okur. `Utf8JsonReader`, özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür. <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemi, kapsamakta olan `Utf8JsonReader` kullanır.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>, `String`, `Int32`ve `DateTime`gibi ortak .NET türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur. Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür. <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemi, kapsamakta olan `Utf8JsonWriter` kullanır.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>, `Utf8JsonReader`kullanarak salt okunurdur Belge Nesne Modeli (DOM) oluşturma olanağı sağlar. DOM, bir JSON yükünde verilere rastgele erişim sağlar. Yükü oluşturan JSON öğelerine <xref:System.Text.Json.JsonElement> türü aracılığıyla erişilebilir. `JsonElement` türü, JSON metnini ortak .NET türlerine dönüştürmek için API 'lerle birlikte dizi ve nesne numaralandırıcıları sağlar. `JsonDocument`, bir <xref:System.Text.Json.JsonDocument.RootElement> özelliğini kullanıma sunar.

Aşağıdaki bölümlerde, bu araçların JSON okuma ve yazma için nasıl kullanılacağı gösterilmektedir.

## <a name="use-jsondocument-for-access-to-data"></a>Veri erişimi için JsonDocument kullanın

Aşağıdaki örnek, bir JSON dizesindeki verilere rastgele erişim için <xref:System.Text.Json.JsonDocument> sınıfının nasıl kullanılacağını gösterir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

Yukarıdaki kod:

* Çözümlenecek JSON 'ın `jsonString`adlı bir dizede olduğunu varsayar.
* Bir `Grade` özelliğine sahip `Students` dizisindeki nesneler için Ortalama bir sınıf hesaplar. 
* Bir sınıfa sahip olmayan öğrenciler için varsayılan bir 70 sınıfı atar.
* Her yinelemeyle bir `count` değişkenini arttırarak öğrencileri sayar. Aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonElement.GetArrayLength%2A>bir alternatif çağrdır:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

Bu kodun işlediği JSON örneğine bir örnek aşağıda verilmiştir:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>JSON yazmak için JsonDocument kullanın

Aşağıdaki örnek, bir <xref:System.Text.Json.JsonDocument>JSON yazmayı gösterir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

Yukarıdaki kod:

* Bir JSON dosyası okur, verileri bir `JsonDocument`yükler ve bir dosyaya biçimlendirilen (düzgün yazdırılmış) JSON yazar.
* JSON girişi içindeki açıklamalara izin verildiğini ancak yok sayılacağını belirtmek için <xref:System.Text.Json.JsonDocumentOptions> kullanır.
* İşiniz bittiğinde, yazıcı <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> çağırır. Diğer bir seçenek de yazıcı boşaltıatıldığı zaman yazıcının temizlemesini sağlar. 

Örnek kod tarafından işlenecek JSON girişi örneği aşağıda verilmiştir:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

Sonuç, aşağıdaki düzgün yazdırılmış JSON çıktıdır:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Utf8JsonWriter kullanma

Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonWriter> sınıfının nasıl kullanılacağını gösterir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Utf8JsonReader kullanma

Aşağıdaki örnek, <xref:System.Text.Json.Utf8JsonReader> sınıfının nasıl kullanılacağını gösterir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

Yukarıdaki kod, `jsonUtf8` değişkeninin UTF-8 olarak kodlanmış geçerli JSON içeren bir bayt dizisi olduğunu varsayar.

### <a name="filter-data-using-utf8jsonreader"></a>Utf8JsonReader kullanarak verileri filtreleme

Aşağıdaki örnek, bir dosyanın zaman uyumlu olarak nasıl okunacağını ve bir değerin nasıl aranacağını gösterir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

Yukarıdaki kod:

* Dosyanın UTF-16 olarak kodlandığını varsayar ve bunu UTF-8 ' e dönüştürür. UTF-8 olarak kodlanmış bir dosya aşağıdaki kodu kullanarak doğrudan bir `ReadOnlySpan<byte>`okunabilir:

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName); 
  ```

* JSON 'un bir nesne dizisi içerdiğini ve her nesne dize türünde bir "ad" özelliği içerebildiği varsayılır.
* "University" ile biten nesneleri ve `name` özellik değerlerini sayar.

Yukarıdaki kodun okuya, bir JSON örneği aşağıda verilmiştir. Sonuçtaki Özet ileti "2 ' den 4 ' ün" University "ile biten adlara sahiptir:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a>Ek kaynaklar

* [System. Text. JSON genel bakış](system-text-json-overview.md)
* [System. Text. JSON API başvurusu](xref:System.Text.Json)
* [System. Text. JSON için özel dönüştürücüler yazma](system-text-json-converters-how-to.md)
* [System. Text. JSON içinde DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
* [DotNet/corefx deposunda JSON işlevleri etiketli GitHub sorunları-doc](https://github.com/dotnet/corefx/labels/json-functionality-doc) 
