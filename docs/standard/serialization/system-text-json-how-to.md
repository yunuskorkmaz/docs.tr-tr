---
title: C#-.NET kullanarak JSON serileştirmek ve serisini kaldırma
description: Bu makalede, System.Text.Json .net 'TEKI JSON 'a seri hale getirmek ve seri durumdan çıkarmak için ad alanını nasıl kullanabileceğiniz gösterilmektedir. Örnek kod içerir.
ms.date: 05/13/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 72ba79784d3eb1beb43eab8db0a448a7e3b18eb6
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90557846"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>.NET içinde JSON ve seri hale getirme (sıralama ve kaldırma)

Bu makalede, <xref:System.Text.Json> JavaScript nesne gösterimi (JSON) ve öğesinden seri hale getirmek ve seri durumdan çıkarmak için ad alanı kullanımı gösterilmektedir. İçinden mevcut kodu aktarıyorsanız `Newtonsoft.Json` , bkz. [nasıl geçiş `System.Text.Json` yapılacağı ](system-text-json-migrate-from-newtonsoft-how-to.md).

Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.

Serileştirme örnek kodunun çoğu, <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` JSON (girintileme ve insanlar okunabilirlik için boşluk) olarak ayarlanır. Üretim kullanımı için genellikle bu ayar için varsayılan değerini kabul etmiş olursunuz `false` .

Kod örnekleri, aşağıdaki sınıfa ve türevlerini ifade eder:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="namespaces"></a>Ad alanları

<xref:System.Text.Json>Ad alanı tüm giriş noktalarını ve ana türleri içerir. <xref:System.Text.Json.Serialization>Ad alanı, serileştirme ve seri durumdan çıkarma ile ilgili gelişmiş senaryolar ve özelleştirme için öznitelikler ve API 'leri içerir. Bu makalede gösterilen kod örnekleri, `using` Bu ad alanlarından biri veya her ikisi için yönergeler gerektirir:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

<xref:System.Runtime.Serialization>Ad alanındaki öznitelikler Şu anda sürümünde desteklenmemektedir `System.Text.Json` .

## <a name="how-to-write-net-objects-to-json-serialize"></a>.NET nesnelerini JSON 'a yazma (serileştirme)

JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.

Aşağıdaki örnek bir dize olarak JSON oluşturur:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerialize)]

Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetSerialize)]

Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetSerialize)]

Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır. Öğesinin aşırı yüklemesi `Serialize()` genel bir tür parametresi alır:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializeWithGenericParameter)]

### <a name="serialization-example"></a>Serileştirme örneği

Aşağıda, koleksiyonları ve iç içe yerleştirilmiş bir sınıfı içeren örnek bir sınıf verilmiştir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPOCOs)]

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

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetSerialize)]

' İ <xref:System.Text.Json.JsonSerializer.Serialize%2A> alan bir aşırı yükleme <xref:System.Text.Json.Utf8JsonWriter> de mevcuttur.

UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır. Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).

## <a name="serialization-behavior"></a>Serileştirme davranışı

* Varsayılan olarak, tüm ortak özellikler serileştirilir. [Dışlanacak özellikleri belirtebilirsiniz](#exclude-properties-from-serialization).
* [Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.
* Varsayılan olarak JSON, Mini olarak belirlenir. JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.
* Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir. [JSON adının büyük küçük harflerini özelleştirebilirsiniz](#customize-json-names-and-values).
* Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.
* Şu anda, [alanlar](../../csharp/programming-guide/classes-and-structs/fields.md) hariç tutulur.

Desteklenen türler şunlardır:

* Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.
* Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://stackoverflow.com/questions/250001/poco-definition).
* Tek boyutlu ve pürüzlü Diziler ( `ArrayName[][]` ).
* `Dictionary<string,TValue>` Burada `TValue` , `object` `JsonElement` veya bir poco.
* Aşağıdaki ad alanlarından Koleksiyonlar.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>

Ek türleri işlemek veya yerleşik dönüştürücüler tarafından desteklenmeyen işlevler sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .

## <a name="how-to-read-json-into-net-objects-deserialize"></a>JSON 'ı .NET Objects 'e okuma (serisini kaldırma)

Bir dizeden veya dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın.

Aşağıdaki örnek, bir dizeden JSON okur ve `WeatherForecast` daha önce [serileştirme örneği](#serialization-example)için gösterilen sınıfının bir örneğini oluşturur:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetDeserialize)]

Zaman uyumlu kod kullanarak bir dosyadan seri durumdan çıkarmak için, aşağıdaki örnekte gösterildiği gibi dosyayı bir dizeye okuyun:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFile.cs?name=SnippetDeserialize)]

Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için yöntemini çağırın <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs?name=SnippetDeserialize)]

### <a name="deserialize-from-utf-8"></a>UTF-8 ' den serisini kaldırma

UTF-8 ' den seri durumdan çıkarmak için, <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> `Utf8JsonReader` `ReadOnlySpan<byte>` Aşağıdaki örneklerde gösterildiği gibi bir veya içeren bir aşırı yükleme çağırın. Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize1)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs?name=SnippetDeserialize2)]

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

JSON çıkışını gerçekten yazdırmak için şu <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> şekilde ayarlayın `true` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripToString.cs?name=SnippetSerializePrettyPrint)]

Aşağıda, seri hale getirilebilir ve düzgün şekilde yazdırılan JSON çıkışının örnek bir türü verilmiştir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

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

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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

Tüm JSON Özellik adları için ortası durumunu kullanmak için, <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> `JsonNamingPolicy.CamelCase` Aşağıdaki örnekte gösterildiği gibi olarak ayarlanır:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundTripCamelCasePropertyNames.cs?name=Serialize)]

Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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
* Öznitelikleri tarafından geçersiz kılınır `[JsonPropertyName]` . Bu nedenle, örnekteki JSON Özellik adının `Wind` ortası durum olmaması neden olur.

### <a name="use-a-custom-json-property-naming-policy"></a>Özel bir JSON Özellik adlandırma ilkesi kullanma

Özel bir JSON Özellik adlandırma ilkesi kullanmak için, <xref:System.Text.Json.JsonNamingPolicy> <xref:System.Text.Json.JsonNamingPolicy.ConvertName%2A> Aşağıdaki örnekte gösterildiği gibi yönteminden türeten bir sınıf oluşturun ve yöntemi geçersiz kılın:

[!code-csharp[](snippets/system-text-json-how-to/csharp/UpperCaseNamingPolicy.cs)]

Daha sonra <xref:System.Text.Json.JsonSerializerOptions.PropertyNamingPolicy?displayProperty=nameWithType> özelliği, adlandırma ilkesi sınıfınızın bir örneğine ayarlayın:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripPropertyNamingPolicy.cs?name=SnippetSerialize)]

Seri hale getirmek ve JSON çıktısı için örnek bir sınıf aşağıda verilmiştir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPropertyNameAttribute)]

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
* Öznitelikleri tarafından geçersiz kılınır `[JsonPropertyName]` . Bu, örnekteki JSON Özellik adının `Wind` büyük harfle değil.

### <a name="camel-case-dictionary-keys"></a>Camel durum sözlüğü anahtarları

Seri hale getirilecek bir nesnenin özelliği tür ise `Dictionary<string,TValue>` , `string` anahtarlar ortası duruma dönüştürülebilir. Bunu yapmak için, <xref:System.Text.Json.JsonSerializerOptions.DictionaryKeyPolicy> `JsonNamingPolicy.CamelCase` Aşağıdaki örnekte gösterildiği gibi öğesini olarak ayarlayın:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCamelCaseDictionaryKeys.cs?name=SnippetSerialize)]

Anahtar-değer çiftlerine sahip adlı bir sözlük ile bir nesneyi serileştirmek `TemperatureRanges` `"ColdMinTemp", 20` ve `"HotMinTemp", 40` Aşağıdaki örnekte olduğu gibi JSON çıktısına neden olur:

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

Sözlük anahtarları için ortası örnek adlandırma ilkesi yalnızca serileştirme için geçerlidir. Bir sözlüğün serisini kaldırırsanız, için belirtseniz bile anahtarlar JSON dosyasıyla eşleşir `JsonNamingPolicy.CamelCase` `DictionaryKeyPolicy` .

### <a name="enums-as-strings"></a>Dizeler dize olarak numaralandırmalar

Varsayılan olarak, numaralandırmalar sayı olarak serileştirilir. Sabit listesi adlarını dizeler olarak seri hale getirmek için öğesini kullanın <xref:System.Text.Json.Serialization.JsonStringEnumConverter> .

Örneğin, bir sabit listesi olan aşağıdaki sınıfı seri hale getirmeniz gerektiğini varsayalım:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithEnum)]

Özet ise `Hot` , varsayılan olarak SERILEŞTIRILMIŞ JSON sayısal değer 3 ' ü içerir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": 3
}
```

Aşağıdaki örnek kod, sayısal değerler yerine enum adlarını seri hale getirir ve adları ortası örneğine dönüştürür:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetSerialize)]

Elde edilen JSON aşağıdaki örneğe benzer şekilde görünür:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "hot"
}
```

Aşağıdaki örnekte gösterildiği gibi, sabit listesi dize adları da seri durumdan çıkarılmış olabilir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/RoundtripEnumAsString.cs?name=SnippetDeserialize)]

## <a name="exclude-properties-from-serialization"></a>Özellikleri serileştirme dışında tut

Varsayılan olarak, tüm ortak özellikler serileştirilir. Bir kısmının JSON çıktısında görünmesini istemiyorsanız, birkaç seçeneğiniz vardır. Bu bölümde nasıl hariç tutulacak açıklanmaktadır:

* [Bireysel Özellikler](#exclude-individual-properties)
* [Tüm salt okunurdur özellikleri](#exclude-all-read-only-properties)
* [Tüm null değerli özellikler](#exclude-all-null-value-properties)

### <a name="exclude-individual-properties"></a>Bireysel özellikleri Dışla

Ayrı özellikleri yoksaymak için [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) özniteliğini kullanın.

Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithIgnoreAttribute)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
}
```

### <a name="exclude-all-read-only-properties"></a>Tüm salt okuma özelliklerini Dışla

Bir özellik, genel bir alıcı içeriyorsa ancak genel bir ayarlayıcı içermiyorsa salt okunurdur. Tüm salt okunurdur özelliklerini hariç tutmak için, <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyProperties?displayProperty=nameWithType> `true` Aşağıdaki örnekte gösterildiği gibi öğesini olarak ayarlayın:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeReadOnlyProperties.cs?name=SnippetSerialize)]

Seri hale getirmek ve JSON çıktısı için örnek bir tür aşağıda verilmiştir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithROProperty)]

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Bu seçenek yalnızca serileştirme için geçerlidir. Seri durumdan çıkarma sırasında salt okuma özellikleri varsayılan olarak yoksayılır.

### <a name="exclude-all-null-value-properties"></a>Tüm null değer özelliklerini Dışla

Tüm null değer özelliklerini dışlamak için, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues> `true` Aşağıdaki örnekte gösterildiği gibi özelliğini olarak ayarlayın:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeExcludeNullValueProperties.cs?name=SnippetSerialize)]

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

Varsayılan olarak, seri hale getirici ASCII olmayan tüm karakterleri çıkar.  Diğer bir deyişle, bu, `\uxxxx` karakterin Unicode kodunun bulunduğu konum ile değiştirilir `xxxx` .  Örneğin, `Summary` özelliği Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

### <a name="serialize-language-character-sets"></a>Dil karakter kümelerini serileştirme

Bir veya daha fazla dilin karakter kümesini kaçış olmadan seri hale getirmek için, aşağıdaki örnekte gösterildiği gibi bir örneği oluştururken [Unicode aralığı](xref:System.Text.Unicode.UnicodeRanges) belirtin <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName> :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetLanguageSets)]

Bu kod, Kiril veya Yunan karakterlerinden kaçış yapmaz. `Summary`Özellik Kiril жарко olarak ayarlandıysa, `WeatherForecast` nesne şu örnekte gösterildiği gibi serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

Tüm dil kümelerini kaçış olmadan seri hale getirmek için kullanın <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType> .

### <a name="serialize-specific-characters"></a>Belirli karakterleri serileştirme

Diğer bir seçenek de, kaçırılmadan, izin vermek istediğiniz tek tek karakterleri belirtmektir. Aşağıdaki örnek, жарко 'in yalnızca ilk iki karakterini seri hale getirir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetSelectedCharacters)]

Yukarıdaki kod tarafından üretilen JSON örneği aşağıda verilmiştir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

### <a name="serialize-all-characters"></a>Tüm karakterleri seri hale getirme

<xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, kullanarak kaçı en aza indirin:

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUsings)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs?name=SnippetUnsafeRelaxed)]

> [!CAUTION]
> Varsayılan kodlayıcıyla karşılaştırıldığında kodlayıcı, `UnsafeRelaxedJsonEscaping` karakterlerin kaçışsız geçmesine izin verme konusunda daha fazla izne sahiptir:
>
> * ,, Ve gibi HTML 'ye duyarlı karakterleri atmaz `<` `>` `&` `'` .
> * Bu, XSS veya bilgi açıklama saldırılarına karşı ek derinlemesine savunma korumaları sunmaz, örneğin, *karakter*kümesinde istemci ve sunucu disagreeing neden olabilir.
>
> Güvenli olmayan kodlayıcıyı yalnızca istemcinin, elde edilen yükü UTF-8 ile kodlanmış JSON olarak yorumladığı bilindiğinde kullanın. Örneğin, sunucu yanıt üst bilgisini gönderiyorsa onu kullanabilirsiniz `Content-Type: application/json; charset=utf-8` . Ham `UnsafeRelaxedJsonEscaping` çıkışın BIR HTML sayfasına veya bir öğeye yayılmasın `<script>` .

## <a name="serialize-properties-of-derived-classes"></a>Türetilmiş sınıfların serileştirme özellikleri

Çok biçimli bir tür hiyerarşisinin serileştirilmesi desteklenmiyor. Örneğin, bir özellik bir arabirim ya da soyut sınıf olarak tanımlanmışsa, çalışma zamanı türü ek özelliklere sahip olsa bile yalnızca arabirim veya soyut sınıf üzerinde tanımlanan özellikler serileştirilir. Bu davranışın istisnaları, bu bölümde açıklanmaktadır.

Örneğin, bir `WeatherForecast` sınıfınız ve türetilmiş bir sınıfınız olduğunu varsayalım `WeatherForecastDerived` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFDerived)]

Ve derleme zamanında yöntemin tür bağımsız değişkeninin `Serialize` Şu olduğunu varsayalım `WeatherForecast` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeDefault)]

Bu senaryoda, `WindSpeed` `weatherForecast` nesne gerçekten bir nesne olsa bile Özellik serileştirilmez `WeatherForecastDerived` . Yalnızca temel sınıf özellikleri serileştirilir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Bu davranış, türetilmiş çalışma zamanında oluşturulan bir türdeki verilerin yanlışlıkla açıklanmasını önlemeye yardımcı olmak için tasarlanmıştır.

Yukarıdaki örnekteki türetilmiş türün özelliklerini seri hale getirmek için aşağıdaki yaklaşımlardan birini kullanın:

* <xref:System.Text.Json.JsonSerializer.Serialize%2A>Çalışma zamanında türü belirtmenize olanak sağlayan aşırı yüklemesini çağırın:

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeGetType)]

* Seri hale getirilecek nesneyi bildirin `object` .

  [!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeObject)]

Yukarıdaki örnek senaryoda, her iki yaklaşım `WindSpeed` ÖZELLIĞIN JSON çıktısına dahil olmasına neden olur:

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

Bunları tür olarak tanımlarsanız alt düzey nesneler için polimorfik serileştirme alabilirsiniz `object` . Örneğin, `WeatherForecast` sınıfınızın, tür olarak tanımlanabilen adında bir özelliği olduğunu varsayalım `PreviousForecast` `WeatherForecast` `object` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPrevious)]

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithPreviousAsObject)]

`PreviousForecast`Özelliği bir örneği içeriyorsa `WeatherForecastDerived` :

* Serileştirmede JSON çıktısı `WeatherForecastWithPrevious` **içermez** `WindSpeed` .
* Serileştirmede JSON çıktısı `WeatherForecastWithPreviousAsObject` **dahildir** `WindSpeed` .

Seri hale getirmek için `WeatherForecastWithPreviousAsObject` , `Serialize<object>` ya da `GetType` kök nesnesi türetilmiş bir tür olabilecek bir nesne olmadığından çağırmak gerekmez. Aşağıdaki kod örneği, `Serialize<object>` veya çağırmaz `GetType` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeSecondLevel)]

Yukarıdaki kod doğru şekilde serileştirir `WeatherForecastWithPreviousAsObject` :

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

Özellikleri, arabirimler ile birlikte tanımlamaya yönelik aynı yaklaşım `object` . Aşağıdaki arabirime ve uygulamaya sahip olduğunuzu ve uygulama örnekleri içeren özelliklerle bir sınıfı seri hale getirmek istediğinizi varsayalım:

[!code-csharp[](snippets/system-text-json-how-to/csharp/IForecast.cs)]

Bir örneğini serileştirçalıştığınızda `Forecasts` , yalnızca `Tuesday` `WindSpeed` özelliğini gösterir, çünkü `Tuesday` Şu şekilde tanımlanır `object` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/SerializePolymorphic.cs?name=SnippetSerializeInterface)]

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

Polimorfik **serileştirme**hakkında daha fazla bilgi için ve **serisini kaldırma**hakkında bilgi için, bkz. ' [den Newtonsoft.Json System.Text.Json ' ye geçiş ](system-text-json-migrate-from-newtonsoft-how-to.md#polymorphic-serialization).

## <a name="allow-comments-and-trailing-commas"></a>Yorumlara ve sondaki virgülleri izin ver

Varsayılan olarak, JSON 'da yorumlara ve sondaki virgüllerin kullanımına izin verilmez. JSON 'da açıklamalara izin vermek için <xref:System.Text.Json.JsonSerializerOptions.ReadCommentHandling?displayProperty=nameWithType> özelliğini olarak ayarlayın `JsonCommentHandling.Skip` .
Ve sondaki virgüllerin kullanılmasına izin vermek için <xref:System.Text.Json.JsonSerializerOptions.AllowTrailingCommas?displayProperty=nameWithType> özelliğini olarak ayarlayın `true` . Aşağıdaki örnek, her ikisine de izin vermeyi göstermektedir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCommasComments.cs?name=SnippetDeserialize)]

Yorumlar ve sondaki virgülden oluşan örnek JSON aşağıda verilmiştir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25, // Fahrenheit 77
  "Summary": "Hot", /* Zharko */
}
```

## <a name="case-insensitive-property-matching"></a>Büyük/küçük harfe duyarsız Özellik eşleştirme

Varsayılan olarak, seri durumdan çıkarma JSON ile hedef nesne özellikleri arasındaki büyük/küçük harfe duyarlı Özellik adı eşleşmelerini arar. Bu davranışı değiştirmek için şu <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive?displayProperty=nameWithType> şekilde ayarlayın `true` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeCaseInsensitive.cs?name=SnippetDeserialize)]

Aşağıda, ortası Case özellik adlarına sahip JSON örneği verilmiştir. Bu,, Pascal case özellik adlarına sahip olan aşağıdaki türde seri durumdan çıkarılmış olabilir.

```json
{
  "date": "2019-08-01T00:00:00-07:00",
  "temperatureCelsius": 25,
  "summary": "Hot",
}
```

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

## <a name="handle-overflow-json"></a>Tutamaç taşması JSON

Seri durumdan çıkarma sırasında, JSON 'da hedef türünün özellikleriyle temsil edilmeyen verileri alabilirsiniz. Örneğin, hedef türünün bu olduğunu varsayalım:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWF)]

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

Gösterilen türde gösterilen JSON serisini kaldırırsanız, `DatesAvailable` ve `SummaryWords` özellikleri nonereye gidebileceği ve kaybediliyor. Bu özellikler gibi ek verileri yakalamak için, [Jsonextensiondata](xref:System.Text.Json.Serialization.JsonExtensionDataAttribute) özniteliğini veya türünde bir özelliğe uygulayın `Dictionary<string,object>` `Dictionary<string,JsonElement>` :

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithExtensionData)]

Daha önce Bu örnek türünde gösterilen JSON serisini kaldırdığınızda, ek veri özelliğin anahtar-değer çiftleri haline gelir `ExtensionData` :

|Özellik |Değer  |Notlar  |
|---------|---------|---------|
| Tarih    | 8/1/2019 12:00:00-07:00||
| TemperatureCelsius| 0 | Büyük/küçük harfe duyarlı uyuşmazlık ( `temperatureCelsius` JSON 'da), bu nedenle özellik ayarlanmadı. |
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

`ExtensionData`Özellik ADıNıN JSON içinde görünmediğine dikkat edin. Bu davranış, JSON 'nin seri durumdan çıkarılmazsız ek verileri kaybetmeden bir gidiş dönüş yapmasını sağlar.

## <a name="ignore-null-when-deserializing"></a>Seri durumdan çıkarılırken null değeri yoksay

Varsayılan olarak, JSON 'daki bir özellik null ise, hedef nesnedeki karşılık gelen özellik null olarak ayarlanır. Bazı senaryolarda, target özelliği varsayılan bir değere sahip olabilir ve varsayılan değeri geçersiz kılmak için null değer istemezsiniz.

Örneğin, aşağıdaki kodun hedef nesneniz temsil ettiğini varsayalım:

[!code-csharp[](snippets/system-text-json-how-to/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

Ve aşağıdaki JSON öğesinin seri durumdan çıkarıldığını varsayalım:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Seri durumdan çıktıktan sonra, `Summary` nesnesinin özelliği `WeatherForecastWithDefault` null olur.

Bu davranışı değiştirmek için, <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType> `true` Aşağıdaki örnekte gösterildiği gibi öğesini olarak ayarlayın:

[!code-csharp[](snippets/system-text-json-how-to/csharp/DeserializeIgnoreNull.cs?name=SnippetDeserialize)]

Bu seçenekle `Summary` nesnenin özelliği, `WeatherForecastWithDefault` serisini kaldırma işleminden sonra varsayılan "Özet yok" değeridir.

JSON içindeki null değerler yalnızca geçerli olmaları durumunda yok sayılır. Nullable değer türleri için null değerler özel durumlara neden olur.

## <a name="utf8jsonreader-utf8jsonwriter-and-jsondocument"></a>Utf8JsonReader, Utf8JsonWriter ve JsonDocument

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> , bir veya ' dan okunan UTF-8 kodlu JSON metin için yüksek performanslı, düşük bir ayırma, Salt ilet okuyucu olur `ReadOnlySpan<byte>` `ReadOnlySequence<byte>` . , `Utf8JsonReader` Özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür. <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>Yöntemi `Utf8JsonReader` , kapakların altında kullanır.

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName> , ve gibi ortak .NET türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur `String` `Int32` `DateTime` . Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür. <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>Yöntemi `Utf8JsonWriter` , kapakların altında kullanır.

<xref:System.Text.Json.JsonDocument?displayProperty=fullName> kullanarak salt okunurdur Belge Nesne Modeli (DOM) oluşturma yeteneği sağlar `Utf8JsonReader` . DOM, bir JSON yükünde verilere rastgele erişim sağlar. Yükü oluşturan JSON öğelerine tür aracılığıyla erişilebilir <xref:System.Text.Json.JsonElement> . `JsonElement`Türü, JSON metnini ortak .net türlerine dönüştürmek Için API 'lerle birlikte dizi ve nesne numaralandırıcıları sağlar. `JsonDocument` bir <xref:System.Text.Json.JsonDocument.RootElement> özellik sunar.

Aşağıdaki bölümlerde, bu araçların JSON okuma ve yazma için nasıl kullanılacağı gösterilmektedir.

## <a name="use-jsondocument-for-access-to-data"></a>Veri erişimi için JsonDocument kullanın

Aşağıdaki örnek, <xref:System.Text.Json.JsonDocument> BIR JSON dizesindeki verilere rastgele erişim için sınıfının nasıl kullanılacağını gösterir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades1)]

Yukarıdaki kod:

* Analiz edilecek JSON 'in adlı bir dizede olduğunu varsayar `jsonString` .
* Özelliği olan bir dizideki nesneler için Ortalama bir sınıf hesaplar `Students` `Grade` .
* Bir sınıfa sahip olmayan öğrenciler için varsayılan bir 70 sınıfı atar.
* Her yinelemeyle bir değişkeni arttırarak öğrencileri sayar `count` . <xref:System.Text.Json.JsonElement.GetArrayLength%2A>Aşağıdaki örnekte gösterildiği gibi bir alternatif çağrdır:

  [!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentDataAccess.cs?name=SnippetAverageGrades2)]

Bu kodun işlediği JSON örneğine bir örnek aşağıda verilmiştir:

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-jsondocument-to-write-json"></a>JSON yazmak için JsonDocument kullanın

Aşağıdaki örnek, öğesinden nasıl JSON yazılacağını göstermektedir <xref:System.Text.Json.JsonDocument> :

[!code-csharp[](snippets/system-text-json-how-to/csharp/JsonDocumentWriteJson.cs?name=SnippetSerialize)]

Yukarıdaki kod:

* Bir JSON dosyasını okur, verileri bir `JsonDocument` dosyasına yükler ve bir dosyaya biçimli (düzgün yazdırılmış) JSON yazar.
* <xref:System.Text.Json.JsonDocumentOptions>JSON girişi içindeki açıklamalara izin verildiğini ancak yok sayılacağını belirtmek için kullanır.
* İşiniz bittiğinde, <xref:System.Text.Json.Utf8JsonWriter.Flush%2A> Yazıcı üzerindeki çağrılar. Diğer bir seçenek de yazıcı boşaltıatıldığı zaman yazıcının temizlemesini sağlar.

Örnek kod tarafından işlenecek JSON girişi örneği aşağıda verilmiştir:

[!code-json[](snippets/system-text-json-how-to/csharp/Grades.json)]

Sonuç, aşağıdaki düzgün yazdırılmış JSON çıktıdır:

[!code-json[](snippets/system-text-json-how-to/csharp/GradesPrettyPrint.json)]

## <a name="use-utf8jsonwriter"></a>Utf8JsonWriter kullanma

Aşağıdaki örnek sınıfının nasıl kullanılacağını gösterir <xref:System.Text.Json.Utf8JsonWriter> :

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8WriterToStream.cs?name=SnippetSerialize)]

## <a name="use-utf8jsonreader"></a>Utf8JsonReader kullanma

Aşağıdaki örnek sınıfının nasıl kullanılacağını gösterir <xref:System.Text.Json.Utf8JsonReader> :

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromBytes.cs?name=SnippetDeserialize)]

Yukarıdaki kod, `jsonUtf8` DEĞIŞKENIN UTF-8 olarak kodlanmış GEÇERLI JSON içeren bir bayt dizisi olduğunu varsayar.

### <a name="filter-data-using-utf8jsonreader"></a>Utf8JsonReader kullanarak verileri filtreleme

Aşağıdaki örnek, bir dosyanın zaman uyumlu olarak nasıl okunacağını ve bir değerin nasıl aranacağını gösterir:

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderFromFile.cs)]

Yukarıdaki kod:

* JSON 'un bir nesne dizisi içerdiğini ve her nesne dize türünde bir "ad" özelliği içerebildiği varsayılır.
* "University" ile biten nesneleri ve "ad" özellik değerlerini sayar.
* Dosyanın UTF-16 olarak kodlandığını varsayar ve bunu UTF-8 ' e dönüştürür. Aşağıdaki kod kullanılarak UTF-8 olarak kodlanmış bir dosya doğrudan bir ile okunabilir `ReadOnlySpan<byte>` :

  ```csharp
  ReadOnlySpan<byte> jsonReadOnlySpan = File.ReadAllBytes(fileName);
  ```

  Dosya bir UTF-8 bayt sırası işareti (BOM) içeriyorsa, okuyucu metin gerektirdiğinden, baytları öğesine geçirmeden önce kaldırın `Utf8JsonReader` . Aksi takdirde, BOM geçersiz JSON olarak değerlendirilir ve okuyucu bir özel durum oluşturur.

Yukarıdaki kodun okuya, bir JSON örneği aşağıda verilmiştir. Sonuçtaki Özet ileti "2 ' den 4 ' ün" University "ile biten adlara sahiptir:

[!code-json[](snippets/system-text-json-how-to/csharp/Universities.json)]

### <a name="read-from-a-stream-using-utf8jsonreader"></a>Utf8JsonReader kullanarak akıştan okuma

Büyük bir dosyayı (örneğin, boyutu bir gigabayt veya daha fazla) okurken, dosyanın tamamını aynı anda belleğe yükleme zorunluluğunu ortadan kaldırmak isteyebilirsiniz. Bu senaryo için bir kullanabilirsiniz <xref:System.IO.FileStream> .

`Utf8JsonReader`Bir akıştan okumak için kullanırken, aşağıdaki kurallar geçerlidir:

* Kısmi JSON yükünün bulunduğu arabellek en az, onun içindeki en büyük JSON belirteci kadar büyük olmalıdır, böylece okuyucu ilerlemeye devam edebilir.
* Arabellek en az JSON içindeki boşluk olan en büyük dizi kadar büyük olmalıdır.
* Okuyucu, JSON yükünde bir sonrakini tamamen okuuncaya kadar okuduğu verileri takip etmez <xref:System.Text.Json.Utf8JsonReader.TokenType%2A> . Bu nedenle, arabellekte kalan baytlar varsa, bunları okuyucuya yeniden geçirmeniz gerekir. <xref:System.Text.Json.Utf8JsonReader.BytesConsumed%2A>Kaç baytın kaldığını anlamak için kullanabilirsiniz.

Aşağıdaki kod bir akıştan nasıl okunacağını gösterir. Örnek bir gösterir <xref:System.IO.MemoryStream> . Benzer kod, <xref:System.IO.FileStream> `FileStream` Başlangıç AŞAMASıNDA bir UTF-8 bom içerdiğinde, ile birlikte çalışır. Bu durumda, kalan baytları öğesine geçirmeden önce bu üç baytı arabellekten çıkarmanız gerekir `Utf8JsonReader` . Aksi halde, BOM JSON 'ın geçerli bir parçası olarak kabul edilmediğinden okuyucu bir özel durum oluşturur.

Örnek kod, bir 4KB arabelleğiyle başlar ve boyutun, bir bütün JSON belirtecine sığamayacak kadar büyük olmadığını bulduğu her seferinde arabellek boyutunu iki katına çıkarır. Bu, okuyucunun JSON yükünde ilerlemesinin ilerlemesini sağlamak için gereklidir. Kod parçacığında belirtilen JSON örneği, yalnızca çok küçük bir başlangıç arabelleği boyutu ayarlarsanız (örneğin, 10 bayt) bir arabellek boyutunu tetikler. Başlangıçtaki arabellek boyutunu 10 olarak ayarlarsanız, `Console.WriteLine` deyimler arabellek boyutunun arttığı nedeni ve etkisini gösterir. 4 KB ilk arabellek boyutunda, tüm örnek JSON her biri tarafından gösterilir `Console.WriteLine` ve arabellek boyutunun hiçbir zaman artırılması gerekmez.

[!code-csharp[](snippets/system-text-json-how-to/csharp/Utf8ReaderPartialRead.cs)]

Yukarıdaki örnek, arabelleğin ne kadar büyüeceği hakkında sınır yoktur. Belirteç boyutu çok büyükse, kod bir <xref:System.OutOfMemoryException> özel durumla başarısız olabilir. Bu, JSON 1 GB veya daha fazla boyuttaki bir belirteç içeriyorsa, 1 GB boyutunun, arabelleğe sığamayacak kadar büyük bir boyuta neden olduğundan bu durum oluşabilir `int32` .

## <a name="additional-resources"></a>Ek kaynaklar

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [Özel dönüştürücü yazma](system-text-json-converters-how-to.md)
* [Öğesinden geçiş Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [İçinde DateTime ve DateTimeOffset desteği System.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
