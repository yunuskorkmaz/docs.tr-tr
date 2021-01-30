---
title: JSON serileştirme-.NET için özel dönüştürücüler yazma
description: Ad alanında belirtilen JSON serileştirme sınıfları için özel dönüştürücüler oluşturmayı öğrenin System.Text.Json .
ms.date: 01/22/2021
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 5406f862eeec83b619f660716e68b85f3d90b28f
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2021
ms.locfileid: "99216362"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a>.NET 'teki JSON serileştirme (sıralama) için özel dönüştürücüler yazma

Bu makalede, ad alanında belirtilen JSON serileştirme sınıfları için özel dönüştürücüler oluşturma işlemi gösterilmektedir <xref:System.Text.Json> . Uygulamasına giriş için `System.Text.Json` bkz. [.net 'te JSON serileştirme ve seri durumdan çıkarma](system-text-json-how-to.md).

*Dönüştürücü* bir nesneyi veya BIR değeri JSON öğesine veya bir değere dönüştüren bir sınıftır. `System.Text.Json`Ad alanı, JavaScript temel elemanlarına eşleyen en basit türlerin yerleşik Dönüştürücülerine sahiptir. Özel dönüştürücüler yazabilirsiniz:

* Yerleşik dönüştürücünün varsayılan davranışını geçersiz kılmak için. Örneğin, `DateTime` değerlerin aa/gg/yyyy biçimiyle temsil olmasını isteyebilirsiniz. Varsayılan olarak, RFC 3339 profili de dahil olmak üzere ISO 8601-1:2019 desteklenir. Daha fazla bilgi için, bkz. [' de System.Text.Json DateTime ve DateTimeOffset desteği ](../datetime/system-text-json-support.md).
* Özel bir değer türünü desteklemek için. Örneğin, bir `PhoneNumber` struct.

Ayrıca, `System.Text.Json` geçerli sürüme dahil olmayan işlevlerle özelleştirmek veya genişletmek için özel dönüştürücüler yazabilirsiniz. Bu makalenin ilerleyen bölümlerinde aşağıdaki senaryolar ele alınmıştır:

::: zone pivot="dotnet-5-0"

* [Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).
* [Polimorfik serisini destekler](#support-polymorphic-deserialization).
* [Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).
* [Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key).
* [Polimorfik serisini destekler](#support-polymorphic-deserialization).
* [Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).
::: zone-end

Özel bir dönüştürücü için yazdığınız kodda, yeni örnekleri kullanmaya yönelik önemli performans cezası hakkında dikkat edin <xref:System.Text.Json.JsonSerializerOptions> . Daha fazla bilgi için bkz. [JsonSerializerOptions örneklerini yeniden kullanma](system-text-json-configure-options.md#reuse-jsonserializeroptions-instances).

## <a name="custom-converter-patterns"></a>Özel dönüştürücü desenleri

Özel dönüştürücü oluşturmak için iki desen vardır: temel desen ve fabrika düzeni. Fabrika deseninin türü `Enum` veya açık genel türleri işleyen dönüştürücüler içindir. Temel model, genel olmayan ve kapalı genel türler içindir.  Örneğin, aşağıdaki türler için dönüştürücüler fabrika deseninin olmasını gerektirir:

* <xref:System.Collections.Generic.Dictionary%602>
* <xref:System.Enum>
* <xref:System.Collections.Generic.List%601>

Temel model tarafından işlenebilen türlerin bazı örnekleri şunlardır:

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* <xref:System.DateTime>
* <xref:System.Int32>

Temel model, bir türü işleyebileceğini bir sınıf oluşturur. Fabrika stili, çalışma zamanında, belirli bir türün gerekli olduğunu ve uygun dönüştürücüyü dinamik olarak oluşturduğunu belirleyen bir sınıf oluşturur.

## <a name="sample-basic-converter"></a>Örnek temel dönüştürücü

Aşağıdaki örnek, varolan bir veri türü için varsayılan Serileştirmeyi geçersiz kılan bir dönüştürücütür. Dönüştürücü özellikler için aa/gg/yyyy biçimini kullanır `DateTimeOffset` .

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DateTimeOffsetConverter.cs":::

## <a name="sample-factory-pattern-converter"></a>Örnek fabrika deseninin Dönüştürücüsü

Aşağıdaki kod ile birlikte çalışarak özel bir dönüştürücüyü gösterir `Dictionary<Enum,TValue>` . İlk genel tür parametresi olduğundan ve ikincisi açık olduğundan, kod fabrika düzeniyle uyar `Enum` . `CanConvert`Yöntemi `true` yalnızca, bir türü olan, yalnızca `Dictionary` iki genel parametre içeren için döndürür `Enum` . İç dönüştürücü, için çalışma zamanında hangi türün sağlandığını işlemek üzere mevcut bir dönüştürücüyü alır `TValue` .

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

Yukarıdaki kod, bu makalede daha sonra [dize olmayan anahtarla destek sözlüğünde](#support-dictionary-with-non-string-key) gösterilenle aynıdır.

## <a name="steps-to-follow-the-basic-pattern"></a>Temel kalıbı izlemeye yönelik adımlar

Aşağıdaki adımlarda, temel kalıbı izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:

* Öğesinden türetilen, <xref:System.Text.Json.Serialization.JsonConverter%601> `T` seri hale getirilecek ve seri durumdan çıkarılacak bir sınıf oluşturun.
* `Read`Gelen JSON serisini kaldırmak ve türe dönüştürmek için yöntemini geçersiz kılın `T` . <xref:System.Text.Json.Utf8JsonReader>JSON 'ı okumak için yöntemine geçirilen öğesini kullanın. Seri hale getirici geçerli JSON kapsamının tüm verilerini geçirdiğinde kısmi verilerin işlenmesine endişelenmeniz gerekmez. <xref:System.Text.Json.Utf8JsonReader.Skip%2A> <xref:System.Text.Json.Utf8JsonReader.TrySkip%2A> Bu nedenle, bu döndürmeleri çağırmak veya doğrulamak gerekli değildir <xref:System.Text.Json.Utf8JsonReader.Read%2A> `true` .
* `Write`Türündeki gelen nesneyi seri hale getirmek için yöntemini geçersiz kılın `T` . <xref:System.Text.Json.Utf8JsonWriter>JSON yazmak için yöntemine geçirilen öğesini kullanın.
* `CanConvert`Yöntemi yalnızca gerektiğinde geçersiz kılın. Varsayılan uygulama, `true` dönüştürülecek tür tür olduğunda döndürür `T` . Bu nedenle, yalnızca türü destekleyen dönüştürücüler `T` Bu yöntemi geçersiz kılmalıdır. Bu yöntemi geçersiz kılmanın gerekli olduğu dönüştürücünün bir örneği için, bu makalenin ilerleyen kısımlarında yer alan [polimorfik serisini kaldırma](#support-polymorphic-deserialization) bölümüne bakın.

[Yerleşik dönüştürücüler kaynak koduna](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/) , özel dönüştürücüler yazmak için başvuru uygulamaları olarak başvurabilirsiniz.

## <a name="steps-to-follow-the-factory-pattern"></a>Fabrika deseninin izlenmesi için adımlar

Aşağıdaki adımlarda, fabrika modelini izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:

* Öğesinden türetilen bir sınıf oluşturun <xref:System.Text.Json.Serialization.JsonConverterFactory> .
* `CanConvert`Dönüştürülecek tür dönüştürücünün işleyebileceği bir ise true döndürecek şekilde yöntemi geçersiz kılın. Örneğin, dönüştürücü için ise `List<T>` yalnızca `List<int>` , `List<string>` ve işleyebilir `List<DateTime>` .
* `CreateConverter`Çalışma zamanında belirtilen tür dönüşümü işleyecek bir dönüştürücü sınıfının örneğini döndürmek için yöntemini geçersiz kılın.
* Yöntemin örnekleyen Converter sınıfını oluşturun `CreateConverter` .

Açık genel türler için fabrika deseninin olması gerekir çünkü bir nesneyi bir dizeye ve bu dizeden dönüştürecek kod tüm türler için aynı değildir. Açık genel tür için bir dönüştürücü ( `List<T>` Örneğin,), arka plandaki bir kapalı genel tür (örneğin) için bir dönüştürücü oluşturmaktır `List<DateTime>` . Dönüştürücünün işleyebileceği her bir kapalı genel türü işlemek için kodun yazılması gerekir.

`Enum`Tür, açık bir genel türe benzer: bir dönüştürücünün, `Enum` `Enum` arka planda belirli bir (örneğin,) bir dönüştürücü oluşturması gerekir `WeekdaysEnum` .

## <a name="error-handling"></a>Hata işleme

Seri hale getirici özel durum türleri ve için özel işleme sağlar <xref:System.Text.Json.JsonException> <xref:System.NotSupportedException> .

### <a name="jsonexception"></a>JsonException

İleti olmadan bir oluşturursanız `JsonException` , serileştirici, hataya neden olan JSON bölümünün yolunu içeren bir ileti oluşturur. Örneğin, ifade `throw new JsonException()` Aşağıdaki örnekte olduğu gibi bir hata iletisi üretir:

```output
Unhandled exception. System.Text.Json.JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

Bir ileti sağlarsanız (örneğin, `throw new JsonException("Error occurred")` seri hale getirici hala <xref:System.Text.Json.JsonException.Path> , <xref:System.Text.Json.JsonException.LineNumber> ve özelliklerini ayarlarsa) <xref:System.Text.Json.JsonException.BytePositionInLine> .

### <a name="notsupportedexception"></a>NotSupportedException

Bir oluşturursanız `NotSupportedException` , her zaman iletideki yol bilgilerini alırsınız. Bir ileti sağlarsanız, yol bilgileri buna eklenir. Örneğin, ifade `throw new NotSupportedException("Error occurred.")` Aşağıdaki örnekte olduğu gibi bir hata iletisi üretir:

```output
Error occurred. The unsupported member type is located on type
'System.Collections.Generic.Dictionary`2[Samples.SummaryWords,System.Int32]'.
Path: $.TemperatureRanges | LineNumber: 4 | BytePositionInLine: 24
```

### <a name="when-to-throw-which-exception-type"></a>Hangi özel durum türünü throw

JSON yükü, seri durumdan çıkarılacak tür için geçerli olmayan belirteçler içerdiğinde bir oluşturun `JsonException` .

Belirli türlere izin vermemek istediğinizde, oluşturun `NotSupportedException` . Bu özel durum, seri hale getiricinin desteklenmeyen türler için otomatik olarak ne yaptığını oluşturur. Örneğin, `System.Type` Güvenlik nedenleriyle desteklenmez. bu nedenle, bunun sonucunda sonuçları serisini kaldırma girişimi `NotSupportedException` .

Gerektiğinde başka özel durumlar da oluşturabilirsiniz, ancak bunlar otomatik olarak JSON yol bilgilerini içermez.

## <a name="register-a-custom-converter"></a>Özel dönüştürücüyü kaydetme

 `Serialize` Ve yöntemlerinin onu kullanmasını sağlamak için özel bir dönüştürücü kaydedin `Deserialize` . Aşağıdaki yaklaşımlardan birini seçin:

* Koleksiyona Converter sınıfının bir örneğini ekleyin <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> .
* Özel dönüştürücü gerektiren özelliklere [[Jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) özniteliğini uygulayın.
* [[Jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) özniteliğini bir sınıfa veya özel bir değer türünü temsil eden bir yapıya uygulayın.

## <a name="registration-sample---converters-collection"></a>Kayıt örneği-dönüştürücüler koleksiyonu

Aşağıda <xref:System.ComponentModel.DateTimeOffsetConverter> , türü özellikler için varsayılan değer sağlayan bir örnek verilmiştir <xref:System.DateTimeOffset> :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Serialize":::

Aşağıdaki türde bir örneği serileştirdiğinizi varsayın:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

Özel dönüştürücünün kullanıldığını gösteren bir JSON çıkışı örneği aşağıda verilmiştir:

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Aşağıdaki kod özel dönüştürücüyü kullanarak seri durumdan çıkarmak için aynı yaklaşımı kullanır `DateTimeOffset` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithConvertersCollection.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-property"></a>Kayıt örneği-[JsonConverter] bir özellikte

Aşağıdaki kod, özelliği için özel bir dönüştürücü seçer `Date` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithConverterAttribute":::

Seri hale getirilecek kod şunu kullanılmasını `WeatherForecastWithConverterAttribute` gerektirmez `JsonSerializeOptions.Converters` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Serialize":::

Seri durumdan çıkarılacak kod ayrıca kullanımını gerektirmez `Converters` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RegisterConverterWithAttributeOnProperty.cs" id="Deserialize":::

## <a name="registration-sample---jsonconverter-on-a-type"></a>Kayıt örneği-[JsonConverter] bir tür üzerinde

Bir struct oluşturan ve özniteliği uygulayan kod aşağıda verilmiştir `[JsonConverter]` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Temperature.cs":::

Önceki yapı için özel dönüştürücü aşağıda verilmiştir:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/TemperatureConverter.cs":::

`[JsonConvert]`Yapı üzerindeki özniteliği özel dönüştürücüyü türü özellikler için varsayılan olarak kaydeder `Temperature` . Dönüştürücü, `TemperatureCelsius` seri hale getirmek veya serisini kaldırmak için aşağıdaki türün özelliğinde otomatik olarak kullanılır:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithTemperatureStruct":::

## <a name="converter-registration-precedence"></a>Dönüştürücü kayıt önceliği

Serileştirme veya seri durumundan çıkarma sırasında, en yüksek öncelikten en düşüğe doğru listelenen her bir JSON öğesi için bir dönüştürücü seçilir:

* `[JsonConverter]` bir özelliğe uygulandı.
* Koleksiyona eklenen bir dönüştürücü `Converters` .
* `[JsonConverter]` özel bir değer türüne veya POCO 'a uygulandı.

Bir tür için birden çok özel dönüştürücü `Converters` koleksiyonda kayıtlıysa, için true döndüren ilk dönüştürücü `CanConvert` kullanılır.

Yalnızca uygulanabilir özel dönüştürücü kayıtlı değilse, yerleşik bir dönüştürücü seçilir.

## <a name="converter-samples-for-common-scenarios"></a>Yaygın senaryolar için dönüştürücü örnekleri

Aşağıdaki bölümlerde, yerleşik işlevlerin sağlamadığı bazı yaygın senaryolar ele alan dönüştürücü örnekleri sağlanmaktadır.

::: zone pivot="dotnet-5-0"

* [Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).
* [Polimorfik serisini destekler](#support-polymorphic-deserialization).
* [Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).
::: zone-end

::: zone pivot="dotnet-core-3-1"

* [Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).
* [Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key).
* [Polimorfik serisini destekler](#support-polymorphic-deserialization).
* [Yığın \<T> için gidiş dönüş desteği](#support-round-trip-for-stackt).
::: zone-end

### <a name="deserialize-inferred-types-to-object-properties"></a>Çıkartılan türlerin nesne özelliklerine serisini kaldırma

Türünde bir özelliğe seri durumdan çıkarılırken `object` bir `JsonElement` nesne oluşturulur. Bunun nedeni, seri hale getiricinin oluşturulacak CLR türünü bilmeyeceği ve tahmin etmeye çalışmayın. Örneğin, bir JSON özelliğinde "true" varsa, seri hale getirici değerin bir olduğunu `Boolean` ve bir öğede "01/01/2019" varsa, seri hale getiricinin bir olduğunu çıkarmaz `DateTime` .

Tür çıkarımı yanlış olabilir. Seri hale getirici, ondalık noktası olmayan bir JSON numarasını ayrıştırır `long` . Bu, değerin başlangıçta veya olarak seri hale getirilmediği durumlarda Aralık dışı sorunlara yol açabilir `ulong` `BigInteger` . `double`Sayı ilk olarak bir olarak seri hale getirilemediği takdirde, ondalık noktası olan bir sayının ayrıştırmasında duyarlık kaybolabilir `decimal` .

Tür çıkarımı gerektiren senaryolar için aşağıdaki kod, özellikler için özel bir dönüştürücü gösterir `object` . Kod dönüştürür:

* `true` ve `false` için `Boolean`
* Ondalık olmayan sayılar `long`
* Ondalık sayı olan sayılar `double`
* Tarihler `DateTime`
* Dizeler `string`
* Diğer her şey `JsonElement`

::: zone pivot="dotnet-5-0"

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterInferredTypesToObject.cs":::

Örnekte, dönüştürücü kodu ve `WeatherForecast` özellikleri olan bir sınıf gösterilmektedir `object` . `Main`Yöntemi, `WeatherForecast` önce dönüştürücüyü kullanmadan, sonra dönüştürücüyü kullanarak bir JSON dizesini bir örneğe seri hale getirir. Konsol çıktısı, özelliği için çalışma zamanı türü olan dönüştürücü olmadan, `Date` `JsonElement` çalışma zamanı türünün olduğunu gösterir `DateTime` .

Ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/tree/c72b54243ade2e1118ab24476220a2eba6057466/src/libraries/System.Text.Json/tests/Serialization/) , `System.Text.Json.Serialization` özellikleri seri durumdan çıkarmayı işleyen özel dönüştürücülerin daha fazla örneklerine sahiptir `object` .

:::zone-end

::: zone pivot="dotnet-core-3-1"

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/ObjectToInferredTypesConverter.cs":::

Aşağıdaki kod dönüştürücüyü kaydeder:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DeserializeInferredTypesToObject.cs" id="Register":::

Özelliklere sahip örnek bir tür aşağıda verilmiştir `object` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithObjectProperties":::

Seri durumdan çıkarılacak aşağıdaki JSON örneği,, ve olarak seri durumdan çıkarılacak değerler `DateTime` içerir `long` `string` :

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Özel dönüştürücü olmadan, seri durumdan çıkarma `JsonElement` her özelliğe bir koyar.

Ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) , `System.Text.Json.Serialization` özellikleri seri durumdan çıkarmayı işleyen özel dönüştürücülerin daha fazla örneklerine sahiptir `object` .

:::zone-end

::: zone pivot="dotnet-core-3-1"

### <a name="support-dictionary-with-non-string-key"></a>Dize olmayan anahtarla destek sözlüğü

Sözlük koleksiyonları için yerleşik destek `Dictionary<string, TValue>` . Diğer bir deyişle, anahtar bir dize olmalıdır. Anahtar olarak bir tamsayı veya başka tür içeren bir sözlüğü desteklemek için özel bir dönüştürücü gerekir.

Aşağıdaki kod ile birlikte çalışarak özel bir dönüştürücüyü göstermektedir `Dictionary<Enum,TValue>` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/DictionaryTKeyEnumTValueConverter.cs":::

Aşağıdaki kod dönüştürücüyü kaydeder:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripDictionaryTkeyEnumTValue.cs" id="Register":::

Dönüştürücü, aşağıdakileri `TemperatureRanges` kullanan aşağıdaki sınıfın özelliğini seri hale getirebilirsiniz ve serisini kaldıramıyor `Enum` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithEnumDictionary":::

Seri hale getirme işleminden alınan JSON çıktısı aşağıdaki örneğe benzer şekilde görünür:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

Ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) , `System.Text.Json.Serialization` dize dışı anahtar sözlüklerini işleyen özel dönüştürücülere daha fazla örnek içerir.
::: zone-end

### <a name="support-polymorphic-deserialization"></a>Polimorfik serisini destekler

Yerleşik özellikler sınırlı sayıda [polimorfik serileştirme](system-text-json-polymorphism.md) sağlar, ancak hiçbir zaman serisini kaldırma desteği yoktur. Seri durumdan çıkarma özel bir dönüştürücü gerektirir.

Örneğin, `Person` `Employee` ve türetilmiş sınıflar içeren bir soyut taban sınıfınız olduğunu varsayalım `Customer` . Polimorfik seri kaldırma, tasarım zamanında `Person` , seri durumdan çıkarma hedefi olarak belirtebileceğiniz ve `Customer` `Employee` JSON 'daki nesnelerin çalışma zamanında doğru bir şekilde seri durumdan çıkarılması anlamına gelir. Seri durumdan çıkarma sırasında, JSON 'da gerekli türü tanımlayan ipuçları bulmanız gerekir. Kullanılabilir ipuçları türleri her senaryoya göre farklılık gösterir. Örneğin, bir Ayrıştırıcı özelliği kullanılabilir olabilir veya belirli bir özelliğin varlığına veya yokluğuna güvenebilirsiniz. Geçerli sürümü, çok `System.Text.Json` biçimli seri kaldırma senaryolarını nasıl işleyeceğinizi belirtmek için öznitelikler sağlamaz, bu nedenle özel dönüştürücüler gereklidir.

Aşağıdaki kod, temel sınıfı, iki türetilmiş sınıfı ve bunlar için özel bir dönüştürücüyü gösterir. Dönüştürücü, çok biçimli seri kaldırma işlemi yapmak için bir Ayrıştırıcı özelliği kullanır. Tür ayrıştırıcısı sınıf tanımlarında değildir, ancak serileştirme sırasında oluşturulur ve seri durumundan çıkarma sırasında okunabilir.

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/Person.cs" id="Person":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/PersonConverterWithTypeDiscriminator.cs":::

Aşağıdaki kod dönüştürücüyü kaydeder:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripPolymorphic.cs" id="Register":::

Dönüştürücü, serileştirme için aynı dönüştürücü kullanılarak oluşturulan JSON serisini kaldıramıyor, örneğin:

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

Yukarıdaki örnekteki dönüştürücü kodu, her bir özelliği el ile okur ve yazar. Bir alternatif, çalışmanın bir `Deserialize` kısmını çağırmak veya yapmak için kullanılır `Serialize` . Bir örnek için, [Bu StackOverflow gönderisini](https://stackoverflow.com/a/59744873/12509023)inceleyin.

### <a name="support-round-trip-for-stackt"></a>Yığın için gidiş dönüş desteği\<T>

Bir JSON dizesini bir nesneye serisini çıkardıysanız <xref:System.Collections.Generic.Stack%601> ve sonra bu nesneyi serileştirmek istiyorsanız, yığının içeriği ters sıralardır. Bu davranış, aşağıdaki türler ve arabirim için ve bunlardan türetilmiş Kullanıcı tanımlı türler için geçerlidir:

* <xref:System.Collections.Stack>
* <xref:System.Collections.Generic.Stack%601>
* <xref:System.Collections.Concurrent.ConcurrentStack%601>
* <xref:System.Collections.Immutable.ImmutableStack%601>
* <xref:System.Collections.Immutable.IImmutableStack%601>

Yığın içinde orijinal sırayı koruyan serileştirme ve serisini desteklemek için özel bir dönüştürücü gereklidir.

Aşağıdaki kod, nesnelerinden ve nesnelerden gidiş dönüşü sağlayan özel bir dönüştürücüyü gösterir `Stack<T>` :

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/JsonConverterFactoryForStackOfT.cs":::

Aşağıdaki kod dönüştürücüyü kaydeder:

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripStackOfT.cs" id="Register":::

## <a name="handle-null-values"></a>Null değerleri işleme

Varsayılan olarak, seri hale getirici null değerlerini aşağıdaki şekilde işler:

* Başvuru türleri ve <xref:System.Nullable%601> türleri için:

  * `null`Serileştirme sırasında özel Dönüştürücülerine geçmez.
  * `JsonTokenType.Null`Seri durumdan çıkarma sırasında özel Dönüştürücülerine geçmez.
  * `null`Seri durumdan çıkarma üzerine bir örnek döndürür.
  * `null`Serileştirme üzerinde doğrudan yazıcıya yazar.

* Null yapılamayan değer türleri için:

  * `JsonTokenType.Null`Seri durumdan çıkarma sırasında özel Dönüştürücülerine geçer. (Özel dönüştürücü yoksa, `JsonException` tür için iç dönüştürücü tarafından bir özel durum oluşturulur.)

Bu null işleme davranışı öncelikle, dönüştürücünün ek bir çağrısını atlayarak performansı iyileştirir. Ayrıca, `null` her `Read` ve `Write` yöntemi geçersiz kılmanın başlangıcında olup olmadığını kontrol etmek için null yapılabilir türler için dönüştürücüler zorlamaktan kaçınır.

::: zone pivot="dotnet-5-0"
Bir özel dönüştürücünün `null` bir başvuru veya değer türü için işlemesini sağlamak için, <xref:System.Text.Json.Serialization.JsonConverter%601.HandleNull%2A?displayProperty=nameWithType> `true` Aşağıdaki örnekte gösterildiği gibi, döndürecek şekilde geçersiz kılın:

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CustomConverterHandleNull.cs" highlight="18":::
::: zone-end

## <a name="other-custom-converter-samples"></a>Diğer özel dönüştürücü örnekleri

' [Den Newtonsoft.Json System.Text.Json geçiş](system-text-json-migrate-from-newtonsoft-how-to.md) , özel dönüştürücülerin ek örneklerini içerir.

Kaynak kodundaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) `System.Text.Json.Serialization` , gibi diğer özel dönüştürücü örneklerini içerir:

* [Seri durumdan çıkarma sırasında null değeri 0 olarak dönüştüren Int32 Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [Seri durumdan çıkarma sırasında hem dize hem de sayı değerlerine izin veren Int32 Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [Sabit Listesi Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [\<T>Dış verileri kabul eden liste Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* [Long [] bir sayı listesi ile birlikte çalışma](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)

Varolan bir yerleşik dönüştürücünün davranışını değiştiren bir dönüştürücü yapmanız gerekiyorsa, varolan dönüştürücünün özelleştirme için bir başlangıç noktası olarak sunmak üzere [kaynak kodunu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) alabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

* [Yerleşik dönüştürücüler için kaynak kodu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [System.Text.Json bakýþ](system-text-json-overview.md)
* [JSON’u seri hale getirme ve seri halden çıkarma](system-text-json-how-to.md)
* [JsonSerializerOptions örneklerinin örneğini oluşturma](system-text-json-configure-options.md)
* [Büyük/küçük harf duyarlı eşlemeyi etkinleştirme](system-text-json-character-casing.md)
* [Özellik adlarını ve değerlerini özelleştirme](system-text-json-customize-properties.md)
* [Özellikleri yoksayma](system-text-json-ignore-properties.md)
* [Geçersiz JSON’a izin verme](system-text-json-invalid-json.md)
* [Sap taşması JSON’ı](system-text-json-handle-overflow.md)
* [Başvuruları koruma](system-text-json-preserve-references.md)
* [Sabit türler ve genel olmayan erişimciler](system-text-json-immutability.md)
* [Polimorfik serileştirme](system-text-json-polymorphism.md)
* [' Den ' a geçiş Newtonsoft.JsonSystem.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [Karakter kodlamasını özelleştirme](system-text-json-character-encoding.md)
* [Özel serileştiriciler ve seri hale getiriciler yazma](write-custom-serializer-deserializer.md)
* [DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
* [System.Text.Json API başvurusu](xref:System.Text.Json)
* [System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)
