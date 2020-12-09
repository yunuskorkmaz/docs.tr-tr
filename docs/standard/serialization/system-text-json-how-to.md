---
title: C#-.NET kullanarak JSON serileştirmek ve serisini kaldırma
description: System.Text.Json.Net 'TEKI JSON 'a seri hale getirmek ve seri durumdan çıkarmak için ad alanını nasıl kullanacağınızı öğrenin. Örnek kod içerir.
ms.date: 12/02/2020
ms.custom: contperfq2
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: dc1f8dab0d8d1ab5001797140a3bbfe4a02cb52b
ms.sourcegitcommit: 0014aa4d5cb2da56a70e03fc68f663d64df5247a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2020
ms.locfileid: "96918573"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a>.NET içinde JSON ve seri hale getirme (sıralama ve kaldırma)

Bu makalede, <xref:System.Text.Json?displayProperty=fullName> JavaScript nesne gösterimi (JSON) ' den seri hale getirmek ve seri durumdan çıkarmak için ad alanının nasıl kullanılacağı gösterilmektedir. İçinden mevcut kodu aktarıyorsanız `Newtonsoft.Json` , bkz. [nasıl geçiş `System.Text.Json` yapılacağı ](system-text-json-migrate-from-newtonsoft-how-to.md).

Yönergeler ve örnek kod, kitaplığı, [ASP.NET Core](/aspnet/core/)gibi bir çerçeve aracılığıyla değil, doğrudan kullanır.

Serileştirme örnek kodunun çoğu, <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> `true` JSON (girintileme ve insanlar okunabilirlik için boşluk) olarak ayarlanır. Üretim kullanımı için genellikle bu ayar için varsayılan değerini kabul etmiş olursunuz `false` .

Kod örnekleri, aşağıdaki sınıfa ve türevlerini ifade eder:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="namespaces"></a>Ad alanları

<xref:System.Text.Json>Ad alanı tüm giriş noktalarını ve ana türleri içerir. <xref:System.Text.Json.Serialization>Ad alanı, serileştirme ve seri durumdan çıkarma ile ilgili gelişmiş senaryolar ve özelleştirme için öznitelikler ve API 'leri içerir. Bu makalede gösterilen kod örnekleri, `using` Bu ad alanlarından biri veya her ikisi için yönergeler gerektirir:

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

> [!IMPORTANT]
> <xref:System.Runtime.Serialization>Ad alanındaki öznitelikler ' de desteklenmez `System.Text.Json` .

## <a name="how-to-write-net-objects-as-json-serialize"></a>.NET nesnelerini JSON (serileştirme) olarak yazma

JSON 'yi bir dizeye veya bir dosyaya yazmak için <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> yöntemini çağırın.

Aşağıdaki örnek bir dize olarak JSON oluşturur:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::

Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumlu kod kullanır:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::

Aşağıdaki örnek, bir JSON dosyası oluşturmak için zaman uyumsuz kod kullanır:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::

Önceki örneklerde, serileştirilmekte olan türün tür çıkarımı kullanılır. Öğesinin aşırı yüklemesi `Serialize()` genel bir tür parametresi alır:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a>Serileştirme örneği

Aşağıda, koleksiyon türü özellikleri ve Kullanıcı tanımlı bir tür içeren örnek bir sınıf verilmiştir:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::

> [!TIP]
> "POCO", [düz eskı clr nesnesini](https://en.wikipedia.org/wiki/Plain_old_CLR_object)temsil eder. POCO, örneğin devralma veya öznitelikler aracılığıyla herhangi bir çerçeveye özgü türe bağımlı olmayan bir .NET türüdür.

Önceki türün bir örneğinin serileştirilmesi için JSON çıktısı aşağıdaki örnekteki gibi görünür. JSON çıktısı küçültülmüş (boşluk, girintileme ve yeni satır karakterleri kaldırılır) varsayılan olarak:

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

Aşağıdaki örnek aynı JSON 'ı gösterir, ancak biçimlendirilir (yani, boşluk ve girintileme ile düzgün şekilde yazdırılır):

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

## <a name="serialize-to-utf-8"></a>UTF-8 ' e serileştirme

UTF-8 ' e seri hale getirmek için <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> yöntemini çağırın:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::

' İ <xref:System.Text.Json.JsonSerializer.Serialize%2A> alan bir aşırı yükleme <xref:System.Text.Json.Utf8JsonWriter> de mevcuttur.

UTF-8 ' i seri hale getirmek, dize tabanlı yöntemler kullanmaktan daha hızlı% 5-10 daha hızlıdır. Aradaki fark, baytların (UTF-8 olarak) dizelere dönüştürülmesi gerekmez (UTF-16).

## <a name="serialization-behavior"></a>Serileştirme davranışı

::: zone pivot="dotnet-5-0"

* Varsayılan olarak, tüm ortak özellikler serileştirilir. [Yoksayılacak özellikleri belirtebilirsiniz](system-text-json-ignore-properties.md).
* [Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.
* Varsayılan olarak JSON, Mini olarak belirlenir. JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.
* Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir. [JSON adının büyük küçük harflerini özelleştirebilirsiniz](system-text-json-customize-properties.md).
* Varsayılan olarak, döngüsel başvurular algılanır ve özel durumlar oluşur. [Başvuruları koruyabilir ve döngüsel başvuruları işleyebilirsiniz](system-text-json-preserve-references.md).
* Varsayılan olarak, [alanlar](../../csharp/programming-guide/classes-and-structs/fields.md) yok sayılır. [Alanları dahil](#include-fields)edebilirsiniz.

System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır. Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* Varsayılan olarak, tüm ortak özellikler serileştirilir. [Yoksayılacak özellikleri belirtebilirsiniz](system-text-json-ignore-properties.md).
* [Varsayılan KODLAYıCı](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) ASCII olmayan KARAKTERLERI, ASCII ARALıĞı içindeki HTML duyarlı KARAKTERLERI ve [RFC 8259 JSON](https://tools.ietf.org/html/rfc8259#section-7)belirtimine göre kaçılması gereken karakterleri çıkar.
* Varsayılan olarak JSON, Mini olarak belirlenir. JSON 'ı [düzgün](#serialize-to-formatted-json)bir şekilde yazdırabilirsiniz.
* Varsayılan olarak, JSON adlarının büyük küçük harfleri .NET adlarıyla eşleşir. [JSON adının büyük küçük harflerini özelleştirebilirsiniz](system-text-json-customize-properties.md).
* Döngüsel başvurular algılandı ve özel durumlar oluşturuldu.
* [Alanlar](../../csharp/programming-guide/classes-and-structs/fields.md) yok sayılır.
::: zone-end

Desteklenen türler şunlardır:
::: zone pivot="dotnet-5-0"

* Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.
* Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).
* Tek boyutlu ve pürüzlü Diziler ( `T[][]` ).
* Aşağıdaki ad alanlarından gelen koleksiyonlar ve sözlükler.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* Sayısal türler, dizeler ve Boole gibi JavaScript temel elemanlarına eşleyen .NET temel türleri.
* Kullanıcı tanımlı [düz eskı clr nesneleri (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).
* Tek boyutlu ve pürüzlü Diziler ( `ArrayName[][]` ).
* `Dictionary<string,TValue>` Burada `TValue` , `object` `JsonElement` veya bir poco.
* Aşağıdaki ad alanlarından Koleksiyonlar.
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

Ek türleri işlemek veya yerleşik dönüştürücüler tarafından desteklenmeyen işlevler sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .

## <a name="how-to-read-json-as-net-objects-deserialize"></a>.NET nesneleri olarak JSON okuma (serisini kaldırma)

Bir dizeden veya dosyadan seri durumdan çıkarmak için <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> yöntemini çağırın.

Aşağıdaki örnek, bir dizeden JSON okur ve `WeatherForecastWithPOCOs` daha önce [serileştirme örneği](#serialization-example)için gösterilen sınıfının bir örneğini oluşturur:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::

Zaman uyumlu kod kullanarak bir dosyadan seri durumdan çıkarmak için, aşağıdaki örnekte gösterildiği gibi dosyayı bir dizeye okuyun:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::

Zaman uyumsuz kod kullanarak bir dosyadan seri durumdan çıkarmak için yöntemini çağırın <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::

## <a name="deserialize-from-utf-8"></a>UTF-8 ' den serisini kaldırma

UTF-8 ' den seri durumdan çıkarmak için, <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> `ReadOnlySpan<byte>` `Utf8JsonReader` Aşağıdaki örneklerde gösterildiği gibi bir veya içeren bir aşırı yükleme çağırın. Örnekler, JSON 'ın jsonUtf8Bytes adlı bir bayt dizisinde olduğunu varsayar.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::

## <a name="deserialization-behavior"></a>Seri durumdan çıkarma davranışı

JSON serisi kaldırılırken aşağıdaki davranışlar geçerlidir:

::: zone pivot="dotnet-5-0"

* Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır. [Büyük/küçük harf duyarlı belirtebilirsiniz](system-text-json-character-casing.md).
* JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.
* Ortak olmayan oluşturucular seri hale getirici tarafından yok sayılır.
* Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenir. Bkz. [değişmez türler ve kayıtlar](system-text-json-immutability.md).
* Varsayılan olarak, numaralandırmalar sayı olarak desteklenir. [Enum adlarını dizeler olarak seri hale](system-text-json-customize-properties.md#enums-as-strings)getirebilirsiniz.
* Varsayılan olarak, alanlar yok sayılır. [Alanları dahil](#include-fields)edebilirsiniz.
* Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur. [Yorumlara ve sondaki virgüllerin bulunmasına izin](system-text-json-invalid-json.md)verebilirsiniz.
* [Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.

System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır. Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* Özellik adı eşleştirme, varsayılan olarak büyük/küçük harfe duyarlıdır. [Büyük/küçük harf duyarlı belirtebilirsiniz](system-text-json-character-casing.md). ASP.NET Core uygulamalar [Varsayılan olarak büyük/küçük harf duyarlı belirtir](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).
* JSON salt okunurdur özelliği için bir değer içeriyorsa, değer yok sayılır ve hiçbir özel durum oluşturulmaz.
* Seri durumdan çıkarma için genel, iç veya özel olabilen parametresiz bir Oluşturucu kullanılır.
* Sabit nesneler veya salt okunurdur özellikleri seri durumundan çıkarma desteklenmez.
* Varsayılan olarak, numaralandırmalar sayı olarak desteklenir. [Enum adlarını dizeler olarak seri hale](system-text-json-customize-properties.md#enums-as-strings)getirebilirsiniz.
* Alanlar desteklenmiyor.
* Varsayılan olarak, JSON 'daki açıklama veya sondaki virgüller özel durum oluşturur. [Yorumlara ve sondaki virgüllerin bulunmasına izin](system-text-json-invalid-json.md)verebilirsiniz.
* [Varsayılan en yüksek derinlik](xref:System.Text.Json.JsonReaderOptions.MaxDepth) 64 ' dir.

System.Text.JsonASP.NET Core uygulamasında dolaylı olarak kullandığınızda, bazı varsayılan davranışlar farklıdır. Daha fazla bilgi için bkz. [JsonSerializerOptions Için Web Varsayılanları](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).
::: zone-end

Yerleşik dönüştürücüler tarafından desteklenmeyen işlevselliği sağlamak için [özel dönüştürücüler uygulayabilirsiniz](system-text-json-converters-how-to.md) .

## <a name="serialize-to-formatted-json"></a>Biçimlendirilen JSON 'a serileştirme

JSON çıkışını gerçekten yazdırmak için şu <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> şekilde ayarlayın `true` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::

Aşağıda, seri hale getirilebilir ve düzgün şekilde yazdırılan JSON çıkışının örnek bir türü verilmiştir:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

`JsonSerializerOptions`Aynı seçeneklerle tekrar tekrar kullanırsanız, `JsonSerializerOptions` her kullandığınızda yeni bir örnek oluşturmayın. Her çağrı için aynı örneği yeniden kullanın. Daha fazla bilgi için bkz. [JsonSerializerOptions örneklerini yeniden kullanma](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).

## <a name="include-fields"></a>Dahil etme alanları

::: zone pivot="dotnet-5-0"
<xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType>Aşağıdaki örnekte gösterildiği gibi, seri hale getirilirken veya seri durumdan çıkarılırken alanları dahil etmek için genel ayarını veya [[jsonınclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) özniteliğini kullanın:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::

Salt okuma alanlarını yok saymak için <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> genel ayarını kullanın.
::: zone-end

::: zone pivot="dotnet-core-3-1"
Alanlar System.Text.Json .NET Core 3,1 ' de desteklenmez. [Özel dönüştürücüler](system-text-json-converters-how-to.md) , bu işlevselliği sağlayabilir.
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a>HttpClient ve HttpContent genişletme yöntemleri

::: zone pivot="dotnet-5-0"

JSON yüklerini ağdan serileştirmek ve serisini kaldırma yaygın işlemlerdir. [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) ve [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) üzerindeki genişletme yöntemleri, bu işlemleri tek bir kod satırında yapmanızı sağlar. Bu uzantı yöntemleri, [JsonSerializerOptions için Web varsayılanlarını](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)kullanır.

Aşağıdaki örnek, ve kullanımını göstermektedir <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType> :

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::

Ayrıca, HttpContent için uzantı yöntemleri de vardır System.Text.Json . [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions)
::: zone-end

::: zone pivot="dotnet-core-3-1"
Ve ' de uzantı yöntemleri `HttpClient` `HttpContent` System.Text.Json .NET Core 3,1 ' de kullanılamaz.
::: zone-end

## <a name="see-also"></a>Ayrıca bkz.

* [System.Text.Json bakýþ](system-text-json-overview.md)
* [Özel dönüştürücü yazma](system-text-json-converters-how-to.md)
* [Öğesinden geçiş Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [İçinde DateTime ve DateTimeOffset desteği System.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
