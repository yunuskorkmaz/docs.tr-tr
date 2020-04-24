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
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>.NET içinde JSON ve seri hale getirme (sıralama ve kaldırma)

Bu makalede, <xref:System.Text.Json> JAVASCRIPT nesne GÖSTERIMI (JSON) ve öğesinden seri hale getirmek ve seri durumdan çıkarmak için ad alanı kullanımı gösterilmektedir. İçinden `Newtonsoft.Json`mevcut kodu aktarıyorsanız, bkz. [nasıl geçiş `System.Text.Json`yapılacağı ](system-text-json-migrate-from-newtonsoft-how-to.md).

Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.

Serileştirme örnek kodunun çoğu, JSON ( <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> girintileme `true` ve insanlar okunabilirlik için boşluk) olarak ayarlanır. Üretim kullanımı için genellikle bu ayar `false` için varsayılan değerini kabul etmiş olursunuz.

Kod örnekleri, aşağıdaki sınıfa ve türevlerini ifade eder:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a>Ad Alanları

<xref:System.Text.Json> Ad alanı tüm giriş noktalarını ve ana türleri içerir. Ad <xref:System.Text.Json.Serialization> alanı, serileştirme ve seri durumdan çıkarma ile ilgili gelişmiş senaryolar ve özelleştirme için öznitelikler ve API 'leri içerir. Bu makalede gösterilen kod örnekleri, bu ad `using` alanlarından biri veya her ikisi için yönergeler gerektirir:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<xref:System.Runtime.Serialization> Ad alanındaki öznitelikler Şu anda sürümünde `System.Text.Json`desteklenmemektedir.

## <a name="how-to-write-net-objects-to-json-serialize"></a>.NET nesnelerini JSON 'a yazma (serileştirme)

JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.

Aşağıdaki örnek bir dize olarak JSON oluşturur:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToString.cs?name=SnippetSerialize)]

Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır. Öğesinin `Serialize()` aşırı yüklemesi genel bir tür parametresi alır:

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

UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemini çağırın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

' <xref:System.Text.Json.JsonSerializer.Serialize%2A> İ alan <xref:System.Text.Json.Utf8JsonWriter> bir aşırı yükleme de mevcuttur.

UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır. Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).

## <a name="serialization-behavior"></a>Serileştirme davranışı

* Varsayılan olarak, tüm ortak özellikler serileştirilir. [Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties-from-serialization).
* [Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.
* Varsayılan olarak JSON, Mini olarak belirlenir. JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.
* Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir. [JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names-and-values).
* Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.
* Şu anda, alanlar hariç tutulur.

Desteklenen türler şunlardır:

* Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.
* Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Tek boyutlu ve pürüzlü Diziler (`ArrayName[][]`).
* `Dictionary<string,TValue>``object`burada, veya bir poco `TValue` `JsonElement`.
* Aşağıdaki ad alanlarından Koleksiyonlar.
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

Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> yöntemini çağırın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>UTF-8 ' den serisini kaldırma

UTF-8 ' den seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> , aşağıdaki örneklerde gösterildiği `Utf8JsonReader` gibi bir `ReadOnlySpan<byte>`veya içeren bir aşırı yükleme çağırın. Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

## <a name="deserialization-behavior"></a>Seri durumdan çıkarma davranışı

* Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır. [Büyük/küçük harf duyarlı belirtebilirsiniz](#case-insensitive-property-matching).
* JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.
* Parametresiz bir Oluşturucu olmadan başvuru türlerine seri durumundan çıkarma desteklenmez.
* Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez.
* Varsayılan olarak, numaralandırmalar sayı olarak desteklenir. [Enum adlarını dizeler olarak seri hale](#enums-as-strings)getirebilirsiniz.
* Alanlar desteklenmiyor.
* Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur. [Yorumlara ve sondaki virgüllerin bulunmasına izin](#allow-comments-and-trailing-commas)verebilirsiniz.
* [Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.

Yerleşik dönüştürücüler tarafından desteklenmeyen işlevselliği sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .

## <a name="serialize-to-formatted-json"></a>Biçimlendirilen JSON 'a serileştirme

JSON çıkışını gerçekten yazdırmak için şu şekilde <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true`ayarlayın:

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

Tüm JSON Özellik adları için ortası durumunu kullanmak için, aşağıdaki <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> örnekte `JsonNamingPolicy.CamelCase`gösterildiği gibi olarak ayarlanır:

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
* Öznitelikleri tarafından `[JsonPropertyName]` geçersiz kılınır. Bu nedenle, örnekteki JSON Özellik adının `Wind` ortası durum olmaması neden olur.

### <a name="use-a-custom-json-property-naming-policy"></a>Özel bir JSON Özellik adlandırma ilkesi kullanma

Özel bir JSON Özellik adlandırma ilkesi kullanmak için, aşağıdaki örnekte gösterildiği gibi <xref:System.Text.Json.JsonNamingPolicy> <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> yönteminden türeten bir sınıf oluşturun ve yöntemi geçersiz kılın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/UpperCaseNamingPolicy.cs)]

Daha sonra özelliği <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> , adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:

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
* Öznitelikleri tarafından `[JsonPropertyName]` geçersiz kılınır. Bu, örnekteki JSON Özellik adının `Wind` büyük harfle değil.

### <a name="camel-case-dictionary-keys"></a>Camel durum sözlüğü anahtarları

Seri hale getirilecek bir nesnenin özelliği tür `Dictionary<string,TValue>`ise, `string` anahtarlar ortası duruma dönüştürülebilir. Bunu yapmak için, aşağıdaki <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> örnekte `JsonNamingPolicy.CamelCase`gösterildiği gibi öğesini olarak ayarlayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

Anahtar-değer çiftlerine `TemperatureRanges` `"ColdMinTemp", 20` sahip adlı bir sözlük ile bir nesneyi serileştirmek ve `"HotMinTemp", 40` aşağıdaki örnekte olduğu gibi JSON çıktısına neden olur:

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

Sözlük anahtarları için ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir. Bir sözlüğün serisini kaldırırsanız, için belirtseniz `JsonNamingPolicy.CamelCase` bıle anahtarlar JSON dosyasıyla eşleşir. `DictionaryKeyPolicy`

### <a name="enums-as-strings"></a>Dizeler dize olarak numaralandırmalar

Varsayılan olarak, numaralandırmalar sayı olarak serileştirilir. Sabit listesi adlarını dizeler olarak seri hale getirmek için <xref:System.Text.Json.Serialization.JsonStringEnumConverter>öğesini kullanın.

Örneğin, bir sabit listesi olan aşağıdaki sınıfı seri hale getirmeniz gerektiğini varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Özet ise `Hot`, varsayılan olarak serileştirilmiş JSON sayısal değer 3 ' ü içerir:

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

Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur. Tüm salt okunurdur özelliklerini hariç tutmak için, aşağıdaki örnekte <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> gösterildiği `true`gibi öğesini olarak ayarlayın:

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

Tüm null değer özelliklerini dışlamak için, aşağıdaki örnekte <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> gösterildiği gibi `true`özelliğini olarak ayarlayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

Seri hale getirmek ve JSON çıktısı için örnek bir nesne aşağıda verilmiştir:

|Özellik |Değer  |
|---------|---------|
| Tarih    | 8/1/2019 12:00:00-07:00|
| TemperatureCelsius| 25 |
| Özet| null|

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25
}
```

Bu ayar serileştirme ve seri durumdan çıkarma için geçerlidir. Seri durumdan çıkarma üzerindeki etkisi hakkında daha fazla bilgi için bkz. [serisi kaldırılırken null değeri yoksay](#ignore-null-when-deserializing).

## <a name="customize-character-encoding"></a>Karakter kodlamasını özelleştirme

Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar.  Diğer bir deyişle, bu, karakterin `\uxxxx` Unicode `xxxx` kodunun bulunduğu konum ile değiştirilir.  Örneğin, `Summary` özelliği Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Dil karakter kümelerini serileştirme

Bir veya daha fazla dilin karakter kümesini kaçış olmadan seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi bir örneği <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

Bu kod, Kiril veya Yunan karakterlerinden kaçış yapmaz. `Summary` Özellik Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:

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

Aşağıdaki örnekte gösterildiği gibi, kullanarak <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>kaçı en aza indirin:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> Varsayılan kodlayıcıyla karşılaştırıldığında `UnsafeRelaxedJsonEscaping` kodlayıcı, karakterlerin kaçışsız geçmesine izin verme konusunda daha fazla izne sahiptir:
>
> * , `<`, Ve `>` `&` `'`gibi HTML 'ye duyarlı karakterleri atmaz.
> * Bu, XSS veya bilgi açıklama saldırılarına karşı ek derinlemesine savunma korumaları sunmaz, örneğin, *karakter*kümesinde istemci ve sunucu disagreeing neden olabilir.
>
> Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın. Örneğin, sunucu yanıt üst bilgisini `Content-Type: application/json; charset=utf-8`gönderiyorsa onu kullanabilirsiniz. Ham `UnsafeRelaxedJsonEscaping` ÇıKıŞıN bir HTML sayfasına veya bir `<script>` öğeye yayılmasın.

## <a name="serialize-properties-of-derived-classes"></a>Türetilmiş sınıfların serileştirme özellikleri

Çok biçimli bir tür hiyerarşisinin serileştirilmesi desteklenmiyor. Örneğin, bir özellik bir arabirim ya da soyut sınıf olarak tanımlanmışsa, çalışma zamanı türü ek özelliklere sahip olsa bile yalnızca arabirim veya soyut sınıf üzerinde tanımlanan özellikler serileştirilir. Bu davranışın istisnaları, bu bölümde açıklanmaktadır.

Örneğin, bir `WeatherForecast` sınıfınız ve türetilmiş bir sınıfınız `WeatherForecastDerived`olduğunu varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

Ve derleme zamanında `Serialize` yöntemin tür bağımsız değişkeninin şu olduğunu `WeatherForecast`varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

Bu senaryoda, `WindSpeed` `weatherForecast` nesne gerçekten bir `WeatherForecastDerived` nesne olsa bile Özellik serileştirilmez. Yalnızca temel sınıf özellikleri serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.

Yukarıdaki örnekteki türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:

* Çalışma zamanında türü belirtmenize <xref:System.Text.Json.JsonSerializer.Serialize%2A> izin veren aşırı yüklemesini çağırın:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* Seri hale getirilecek nesneyi bildirin `object`.

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

Yukarıdaki örnek senaryoda, her iki yaklaşım `WindSpeed` özelliğin JSON çıktısına dahil olmasına neden olur:

```json
{
  "WindSpeed": 35,
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

> [!IMPORTANT]
> Bu yaklaşımlar yalnızca kök nesnenin seri hale getirilmesi için, bu kök nesnenin özellikleri için değil, polimorfik serileştirme sağlar.

Bunları tür `object`olarak tanımlarsanız alt düzey nesneler için polimorfik serileştirme alabilirsiniz. Örneğin, `WeatherForecast` sınıfınızın, tür `PreviousForecast` `WeatherForecast` olarak tanımlanabilen adında bir özelliği olduğunu varsayalım: `object`

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

`PreviousForecast` Özelliği bir örneği içeriyorsa `WeatherForecastDerived`:

* Serileştirmede `WeatherForecastWithPrevious` JSON çıktısı **içermez** `WindSpeed`.
* Serileştirmede `WeatherForecastWithPreviousAsObject` JSON çıktısı **dahildir** `WindSpeed`.

Seri hale `WeatherForecastWithPreviousAsObject`getirmek için, ya `Serialize<object>` `GetType` da kök nesnesi türetilmiş bir tür olabilecek bir nesne olmadığından çağırmak gerekmez. Aşağıdaki kod örneği, veya `Serialize<object>` `GetType`çağırmaz:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

Yukarıdaki kod doğru şekilde serileştirir `WeatherForecastWithPreviousAsObject`:

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

Özellikleri `object` , arabirimler ile birlikte tanımlamaya yönelik aynı yaklaşım. Aşağıdaki arabirime ve uygulamaya sahip olduğunuzu ve uygulama örnekleri içeren özelliklerle bir sınıfı seri hale getirmek istediğinizi varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/IForecast.cs)]

Bir `Forecasts`örneğini serileştirçalıştığınızda, yalnızca `Tuesday` `WindSpeed` özelliğini gösterir, çünkü `Tuesday` şu şekilde `object`tanımlanır:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

Aşağıdaki örnek, önceki koddan elde edilen JSON 'u göstermektedir:

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

Polimorfik **serileştirme**hakkında daha fazla bilgi edinmek ve **serisini kaldırma**hakkında bilgi Için, bkz. [Newtonsoft. JSON 'Dan System. Text. JSON 'a geçiş](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).

## <a name="allow-comments-and-trailing-commas"></a>Yorumlara ve sondaki virgülleri izin ver

Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez. JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini olarak `JsonCommentHandling.Skip`ayarlayın.
Ve sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini olarak `true`ayarlayın. Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:

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

Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar. Bu davranışı değiştirmek için şu şekilde <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> `true`ayarlayın:

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

Gösterilen türde gösterilen JSON serisini kaldırırsanız, `DatesAvailable` ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor. Bu özellikler gibi ek verileri yakalamak için, [Jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini veya `Dictionary<string,object>` `Dictionary<string,JsonElement>`türünde bir özelliğe uygulayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veri `ExtensionData` özelliğin anahtar-değer çiftleri haline gelir:

|Özellik |Değer  |Notlar  |
|---------|---------|---------|
| Tarih    | 8/1/2019 12:00:00-07:00||
| TemperatureCelsius| 0 | Büyük/küçük harfe duyarlı`temperatureCelsius` UYUŞMAZLıK (JSON 'da), bu nedenle özellik ayarlanmadı. |
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

`ExtensionData` ÖZELLIK adının JSON içinde görünmediğine dikkat edin. Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.

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

Seri durumdan çıktıktan sonra `Summary` , `WeatherForecastWithDefault` nesnesinin özelliği null olur.

Bu davranışı değiştirmek için, aşağıdaki <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> örnekte `true`gösterildiği gibi öğesini olarak ayarlayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

Bu seçenekle `Summary` `WeatherForecastWithDefault` nesnenin özelliği, serisini kaldırma işleminden sonra varsayılan "Özet yok" değeridir.

JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır. Nullable değer türleri için null değerler özel durumlara neden olur.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter ve JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>, bir veya `ReadOnlySpan<byte>` `ReadOnlySequence<byte>`' dan okunan UTF-8 kodlu JSON metin için yüksek performanslı, düşük bir ayırma, Salt ilet okuyucu olur. , `Utf8JsonReader` Özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür. <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> Yöntemi, kapakların altında kullanır `Utf8JsonReader` .

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>, `String` `Int32`ve `DateTime`gibi ortak .net türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur. Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür. <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> Yöntemi, kapakların altında kullanır `Utf8JsonWriter` .

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>kullanarak `Utf8JsonReader`salt okunurdur belge nesne MODELI (DOM) oluşturma yeteneği sağlar. DOM, bir JSON yükünde verilere rastgele erişim sağlar. Yükü oluşturan JSON öğelerine <xref:System.Text.Json.JsonElement> tür aracılığıyla erişilebilir. Türü `JsonElement` , JSON metnini ortak .net türlerine dönüştürmek için API 'lerle birlikte dizi ve nesne numaralandırıcıları sağlar. `JsonDocument`bir <xref:System.Text.Json.JsonDocument.RootElement> özellik sunar.

Aşağıdaki bölümlerde, bu araçların JSON okuma ve yazma için nasıl kullanılacağı gösterilmektedir.

## <a name="use-jsondocument-for-access-to-data"></a>Veri erişimi için JsonDocument kullanın

Aşağıdaki örnek, bir JSON dizesindeki verilere rastgele <xref:System.Text.Json.JsonDocument> erişim için sınıfının nasıl kullanılacağını gösterir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

Yukarıdaki kod:

* Analiz edilecek JSON 'in adlı `jsonString`bir dizede olduğunu varsayar.
* `Grade` Özelliği olan bir `Students` dizideki nesneler için Ortalama bir sınıf hesaplar.
* Bir sınıfa sahip olmayan öğrenciler için varsayılan bir 70 sınıfı atar.
* Her yinelemeyle bir `count` değişkeni arttırarak öğrencileri sayar. Aşağıdaki örnekte gösterildiği gibi bir <xref:System.Text.Json.JsonElement.GetArrayLength%2A>alternatif çağrdır:

  [!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

Bu kodun işlediği JSON örneğine bir örnek aşağıda verilmiştir:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>JSON yazmak için JsonDocument kullanın

Aşağıdaki örnek, öğesinden nasıl JSON yazılacağını göstermektedir <xref:System.Text.Json.JsonDocument>:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

Yukarıdaki kod:

* Bir JSON dosyasını okur, verileri bir `JsonDocument`dosyasına yükler ve bir dosyaya biçimli (düzgün YAZDıRıLMıŞ) JSON yazar.
* JSON <xref:System.Text.Json.JsonDocumentOptions> girişi içindeki açıklamalara izin verildiğini ancak yok sayılacağını belirtmek için kullanır.
* İşiniz bittiğinde, yazıcı <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> üzerindeki çağrılar. Diğer bir seçenek de yazıcı boşaltıatıldığı zaman yazıcının temizlemesini sağlar.

Örnek kod tarafından işlenecek JSON girişi örneği aşağıda verilmiştir:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Grades.json)]

Sonuç, aşağıdaki düzgün yazdırılmış JSON çıktıdır:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Utf8JsonWriter kullanma

Aşağıdaki örnek <xref:System.Text.Json.Utf8JsonWriter> sınıfının nasıl kullanılacağını gösterir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Utf8JsonReader kullanma

Aşağıdaki örnek <xref:System.Text.Json.Utf8JsonReader> sınıfının nasıl kullanılacağını gösterir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

Yukarıdaki kod, `jsonUtf8` değişkenin UTF-8 olarak KODLANMıŞ geçerli JSON içeren bir bayt dizisi olduğunu varsayar.

### <a name="filter-data-using-utf8jsonreader"></a>Utf8JsonReader kullanarak verileri filtreleme

Aşağıdaki örnek, bir dosyanın zaman uyumlu olarak nasıl okunacağını ve bir değerin nasıl aranacağını gösterir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Utf8ReaderFromFile.cs)]

Yukarıdaki kod:

* JSON 'un bir nesne dizisi içerdiğini ve her nesne dize türünde bir "ad" özelliği içerebildiği varsayılır.
* "University" ile biten nesneleri ve "ad" özellik değerlerini sayar.
* Dosyanın UTF-16 olarak kodlandığını varsayar ve bunu UTF-8 ' e dönüştürür. Aşağıdaki kod kullanılarak UTF-8 olarak kodlanmış bir dosya doğrudan bir `ReadOnlySpan<byte>`ile okunabilir:

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  Dosya bir UTF-8 bayt sırası işareti (BOM) içeriyorsa, okuyucu metin gerektirdiğinden, baytları öğesine `Utf8JsonReader`geçirmeden önce kaldırın. Aksi takdirde, BOM geçersiz JSON olarak değerlendirilir ve okuyucu bir özel durum oluşturur.

Yukarıdaki kodun okuya, bir JSON örneği aşağıda verilmiştir. Sonuçtaki Özet ileti "2 ' den 4 ' ün" University "ile biten adlara sahiptir:

[!code-json[](~/samples/snippets/core/system-text-json/csharp/Universities.json)]

## <a name="additional-resources"></a>Ek kaynaklar

* [System.Text.Jsonbakýþ](system-text-json-overview.md)
* [Özel dönüştürücü yazma](system-text-json-converters-how-to.md)
* [Öğesinden geçişNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [İçinde DateTime ve DateTimeOffset desteğiSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonAPI başvurusu](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
