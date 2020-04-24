---
title: JSON serileştirme-.NET için özel dönüştürücüler yazma
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 310967f39c3aa7a46d79087bcbf0cb016f7d7284
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159578"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a>.NET 'teki JSON serileştirme (sıralama) için özel dönüştürücüler yazma

Bu makalede, <xref:[!OP.NO-LOC(System.Text.Json)]> ad alanında belirtilen JSON serileştirme sınıfları için özel dönüştürücüler oluşturma işlemi gösterilmektedir. Uygulamasına `[!OP.NO-LOC(System.Text.Json)]`giriş için bkz. [.net 'te JSON serileştirme ve seri durumdan çıkarma](system-text-json-how-to.md).

*Dönüştürücü* bir nesneyi veya BIR değeri JSON öğesine veya bir değere dönüştüren bir sınıftır. Ad `[!OP.NO-LOC(System.Text.Json)]` alanı, JavaScript temel elemanlarına eşleyen en basit türlerin yerleşik Dönüştürücülerine sahiptir. Özel dönüştürücüler yazabilirsiniz:

* Yerleşik dönüştürücünün varsayılan davranışını geçersiz kılmak için. Örneğin, varsayılan ISO 8601-1:2019 biçimi `DateTime` yerine, değerlerin aa/gg/yyyy biçiminde temsil olmasını isteyebilirsiniz.
* Özel bir değer türünü desteklemek için. Örneğin, bir `PhoneNumber` struct.

Ayrıca, geçerli sürüme dahil olmayan işlevlerle özelleştirmek veya genişletmek `[!OP.NO-LOC(System.Text.Json)]` için özel dönüştürücüler yazabilirsiniz. Bu makalenin ilerleyen bölümlerinde aşağıdaki senaryolar ele alınmıştır:

* [Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).
* [Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key).
* [Polimorfik serisini destekler](#support-polymorphic-deserialization).

## <a name="custom-converter-patterns"></a>Özel dönüştürücü desenleri

Özel dönüştürücü oluşturmak için iki desen vardır: temel desen ve fabrika düzeni. Fabrika deseninin türü `Enum` veya açık genel türleri işleyen dönüştürücüler içindir. Temel model, genel olmayan ve kapalı genel türler içindir.  Örneğin, aşağıdaki türler için dönüştürücüler fabrika deseninin olmasını gerektirir:

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

Temel model tarafından işlenebilen türlerin bazı örnekleri şunlardır:

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

Temel model, bir türü işleyebileceğini bir sınıf oluşturur. Factory stili, çalışma zamanında belirli bir türün gerekli olduğunu ve uygun dönüştürücüyü dinamik olarak oluşturduğunu belirleyen bir sınıf oluşturur.

## <a name="sample-basic-converter"></a>Örnek temel dönüştürücü

Aşağıdaki örnek, varolan bir veri türü için varsayılan Serileştirmeyi geçersiz kılan bir dönüştürücütür. Dönüştürücü özellikler için `DateTimeOffset` aa/gg/yyyy biçimini kullanır.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a>Örnek fabrika deseninin Dönüştürücüsü

Aşağıdaki kod ile birlikte `Dictionary<Enum,TValue>`çalışarak özel bir dönüştürücüyü gösterir. İlk genel tür parametresi olduğundan `Enum` ve ikincisi açık olduğundan, kod fabrika düzeniyle uyar. `CanConvert` Yöntemi yalnızca, `true` bir `Dictionary` `Enum` türü olan, yalnızca iki genel parametre içeren için döndürür. İç dönüştürücü, için `TValue`çalışma zamanında hangi türün sağlandığını işlemek üzere mevcut bir dönüştürücüyü alır.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

Yukarıdaki kod, bu makalede daha sonra [dize olmayan anahtarla destek sözlüğünde](#support-dictionary-with-non-string-key) gösterilenle aynıdır.

## <a name="steps-to-follow-the-basic-pattern"></a>Temel kalıbı izlemeye yönelik adımlar

Aşağıdaki adımlarda, temel kalıbı izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:

* Öğesinden <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverter%601> `T` türetilen, seri hale getirilecek ve seri durumdan çıkarılacak bir sınıf oluşturun.
* Gelen JSON `Read` serisini kaldırmak ve türe `T`dönüştürmek için yöntemini geçersiz kılın. <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonReader> JSON 'ı okumak için yöntemine geçirilen öğesini kullanın.
* Türündeki `T`gelen `Write` nesneyi seri hale getirmek için yöntemini geçersiz kılın. <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonWriter> JSON yazmak için yöntemine geçirilen öğesini kullanın.
* `CanConvert` Yöntemi yalnızca gerektiğinde geçersiz kılın. Varsayılan uygulama, dönüştürülecek `true` tür tür `T`olduğunda döndürür. Bu nedenle, yalnızca türü `T` destekleyen dönüştürücüler Bu yöntemi geçersiz kılmalıdır. Bu yöntemi geçersiz kılmanın gerekli olduğu dönüştürücünün bir örneği için, bu makalenin ilerleyen kısımlarında yer alan [polimorfik serisini kaldırma](#support-polymorphic-deserialization) bölümüne bakın.

[Yerleşik dönüştürücüler kaynak koduna](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/[!OP.NO-LOC(System.Text.Json)]/src/[!OP.NO-LOC(System/Text/Json)]/Serialization/Converters/) , özel dönüştürücüler yazmak için başvuru uygulamaları olarak başvurabilirsiniz.

## <a name="steps-to-follow-the-factory-pattern"></a>Fabrika deseninin izlenmesi için adımlar

Aşağıdaki adımlarda, fabrika modelini izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:

* Öğesinden <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterFactory>türetilen bir sınıf oluşturun.
* Dönüştürülecek tür `CanConvert` dönüştürücünün işleyebileceği bir ise true döndürecek şekilde yöntemi geçersiz kılın. Örneğin `List<T>` , dönüştürücü için ise yalnızca, `List<int>` `List<string>`ve `List<DateTime>`işleyebilir.
* Çalışma zamanında `CreateConverter` belirtilen tür dönüşümü işleyecek bir dönüştürücü sınıfının örneğini döndürmek için yöntemini geçersiz kılın.
* `CreateConverter` Yöntemin örnekleyen Converter sınıfını oluşturun.

Açık genel türler için fabrika deseninin olması gerekir çünkü bir nesneyi bir dizeye ve bu dizeden dönüştürecek kod tüm türler için aynı değildir. Açık genel tür için bir dönüştürücü (`List<T>`Örneğin,), arka plandaki bir kapalı genel tür (`List<DateTime>`örneğin) için bir dönüştürücü oluşturmaktır. Dönüştürücünün işleyebileceği her bir kapalı genel türü işlemek için kodun yazılması gerekir.

`Enum` Tür, açık bir genel türe benzer: bir dönüştürücünün `Enum` , arka planda belirli `Enum` bir (`WeekdaysEnum`Örneğin,) bir dönüştürücü oluşturması gerekir.

## <a name="error-handling"></a>Hata işleme

Hata işleme kodunda bir özel durum oluşturmanız gerekiyorsa, ileti olmadan bir <xref:[!OP.NO-LOC(System.Text.Json)].JsonException> ileti yerleştirmeyi düşünün. Bu özel durum türü otomatik olarak, hataya neden olan JSON bölümünün yolunu içeren bir ileti oluşturur. Örneğin, ifade `throw new JsonException();` aşağıdaki örnekte olduğu gibi bir hata iletisi üretir:

```
Unhandled exception. [!OP.NO-LOC(System.Text.Json)].JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

Bir ileti sağlarsanız (örneğin, `throw new JsonException("Error occurred")`özel durum hala <xref:[!OP.NO-LOC(System.Text.Json)].JsonException.Path> özelliğindeki yolu sağlar.

## <a name="register-a-custom-converter"></a>Özel dönüştürücüyü kaydetme

Ve yöntemlerinin onu kullanmasını sağlamak için özel bir dönüştürücü *kaydedin.* `Serialize` `Deserialize` Aşağıdaki yaklaşımlardan birini seçin:

* <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters?displayProperty=nameWithType> Koleksiyona Converter sınıfının bir örneğini ekleyin.
* Özel dönüştürücü gerektiren özelliklere [[Jsonconverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute) özniteliğini uygulayın.
* [[Jsonconverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute) özniteliğini bir sınıfa veya özel bir değer türünü temsil eden bir yapıya uygulayın.

## <a name="registration-sample---converters-collection"></a>Kayıt örneği-dönüştürücüler koleksiyonu

Aşağıda <xref:System.ComponentModel.DateTimeOffsetConverter> , türü <xref:System.DateTimeOffset>özellikler için varsayılan değer sağlayan bir örnek verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

Aşağıdaki türde bir örneği serileştirdiğinizi varsayın:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Özel dönüştürücünün kullanıldığını gösteren bir JSON çıkışı örneği aşağıda verilmiştir:

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

Aşağıdaki kod özel `DateTimeOffset` dönüştürücüyü kullanarak seri durumdan çıkarmak için aynı yaklaşımı kullanır:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a>Kayıt örneği-[JsonConverter] bir özellikte

Aşağıdaki kod, `Date` özelliği için özel bir dönüştürücü seçer:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

Seri hale `WeatherForecastWithConverterAttribute` getirilecek kod şunu kullanılmasını gerektirmez `JsonSerializeOptions.Converters`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

Seri durumdan çıkarılacak kod ayrıca kullanımını gerektirmez `Converters`:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a>Kayıt örneği-[JsonConverter] bir tür üzerinde

Bir struct oluşturan ve `[JsonConverter]` özniteliği uygulayan kod aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

Önceki yapı için özel dönüştürücü aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

Yapı `[JsonConvert]` üzerindeki özniteliği özel dönüştürücüyü türü `Temperature`özellikler için varsayılan olarak kaydeder. Dönüştürücü, seri hale getirmek veya serisini `TemperatureCelsius` kaldırmak için aşağıdaki türün özelliğinde otomatik olarak kullanılır:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a>Dönüştürücü kayıt önceliği

Serileştirme veya seri durumundan çıkarma sırasında, en yüksek öncelikten en düşüğe doğru listelenen her bir JSON öğesi için bir dönüştürücü seçilir:

* `[JsonConverter]`bir özelliğe uygulandı.
* `Converters` Koleksiyona eklenen bir dönüştürücü.
* `[JsonConverter]`özel bir değer türüne veya POCO 'a uygulandı.

Bir tür için birden çok özel dönüştürücü `Converters` koleksiyonda kayıtlıysa, için `CanConvert` true döndüren ilk dönüştürücü kullanılır.

Yalnızca uygulanabilir özel dönüştürücü kayıtlı değilse, yerleşik bir dönüştürücü seçilir.

## <a name="converter-samples-for-common-scenarios"></a>Yaygın senaryolar için dönüştürücü örnekleri

Aşağıdaki bölümlerde, yerleşik işlevlerin sağlamadığı bazı yaygın senaryolar ele alan dönüştürücü örnekleri sağlanmaktadır.

* [Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties)
* [Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key)
* [Polimorfik serisini destekler](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a>Çıkartılan türlerin nesne özelliklerine serisini kaldırma

Türünde `object`bir özelliğe seri durumdan çıkarılırken bir `JsonElement` nesne oluşturulur. Bunun nedeni, seri hale getiricinin oluşturulacak CLR türünü bilmeyeceği ve tahmin etmeye çalışmayın. Örneğin, bir JSON özelliğinde "true" varsa, seri hale getirici değerin bir `Boolean`olduğunu ve bir öğede "01/01/2019" varsa, seri hale getiricinin bir `DateTime`olduğunu çıkarmaz.

Tür çıkarımı yanlış olabilir. Seri hale getirici, ondalık noktası olmayan bir `long`JSON numarasını ayrıştırır. Bu, değerin başlangıçta `ulong` veya `BigInteger`olarak seri hale getirilmediği durumlarda Aralık dışı sorunlara yol açabilir. Sayı ilk olarak bir `double` `decimal`olarak seri hale getirilemediği takdirde, ondalık noktası olan bir sayının ayrıştırmasında duyarlık kaybolabilir.

Tür çıkarımı gerektiren senaryolar için aşağıdaki kod, özellikler için `object` özel bir dönüştürücü gösterir. Kod dönüştürür:

* `true`ve `false` için`Boolean`
* Ondalık olmayan sayılar`long`
* Ondalık sayı olan sayılar`double`
* Tarihler`DateTime`
* Dizeler`string`
* Diğer her şey`JsonElement`

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

Aşağıdaki kod dönüştürücüyü kaydeder:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

Özelliklere sahip `object` örnek bir tür aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

Seri durumdan çıkarılacak aşağıdaki JSON örneği,, ve `DateTime` `long` `string`olarak seri durumdan çıkarılacak değerler içerir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Özel dönüştürücü olmadan, seri durumdan çıkarma her `JsonElement` özelliğe bir koyar.

Ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) , `object` özellikleri seri durumdan çıkarmayı işleyen özel dönüştürücülerin daha fazla örneklerine sahiptir. `System.Text.Json.Serialization`

### <a name="support-dictionary-with-non-string-key"></a>Dize olmayan anahtarla destek sözlüğü

Sözlük koleksiyonları için yerleşik destek `Dictionary<string, TValue>`. Diğer bir deyişle, anahtar bir dize olmalıdır. Anahtar olarak bir tamsayı veya başka tür içeren bir sözlüğü desteklemek için özel bir dönüştürücü gerekir.

Aşağıdaki kod ile birlikte `Dictionary<Enum,TValue>`çalışarak özel bir dönüştürücüyü göstermektedir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

Aşağıdaki kod dönüştürücüyü kaydeder:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

Dönüştürücü, aşağıdakileri kullanan aşağıdaki sınıfın `TemperatureRanges` özelliğini seri hale getirebilirsiniz ve serisini kaldıramıyor: `Enum`

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

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

Ad alanındaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) , dize dışı anahtar sözlüklerini işleyen özel dönüştürücülere daha fazla örnek içerir. `System.Text.Json.Serialization`

### <a name="support-polymorphic-deserialization"></a>Polimorfik serisini destekler

Yerleşik özellikler sınırlı sayıda [polimorfik serileştirme](system-text-json-how-to.md#serialize-properties-of-derived-classes) sağlar, ancak hiçbir zaman serisini kaldırma desteği yoktur. Seri durumdan çıkarma özel bir dönüştürücü gerektirir.

Örneğin, ve `Person` `Employee` `Customer` türetilmiş sınıflar içeren bir soyut taban sınıfınız olduğunu varsayalım. Polimorfik seri kaldırma, tasarım zamanında, seri `Person` durumdan çıkarma hedefi olarak BELIRTEBILECEĞINIZ ve `Customer` JSON `Employee` 'daki nesneler çalışma zamanında doğru şekilde seri durumdan çıkarılan anlamına gelir. Seri durumdan çıkarma sırasında, JSON 'da gerekli türü tanımlayan ipuçları bulmanız gerekir. Kullanılabilir ipuçları türleri her senaryoya göre farklılık gösterir. Örneğin, bir Ayrıştırıcı özelliği kullanılabilir olabilir veya belirli bir özelliğin varlığına veya yokluğuna güvenebilirsiniz. Geçerli sürümü, çok `System.Text.Json` biçimli seri kaldırma senaryolarını nasıl işleyeceğinizi belirtmek için öznitelikler sağlamaz, bu nedenle özel dönüştürücüler gereklidir.

Aşağıdaki kod, temel sınıfı, iki türetilmiş sınıfı ve bunlar için özel bir dönüştürücüyü gösterir. Dönüştürücü, çok biçimli seri kaldırma işlemi yapmak için bir Ayrıştırıcı özelliği kullanır. Tür ayrıştırıcısı sınıf tanımlarında değildir, ancak serileştirme sırasında oluşturulur ve seri durumundan çıkarma sırasında okunabilir.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

Aşağıdaki kod dönüştürücüyü kaydeder:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

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

Yukarıdaki örnekteki dönüştürücü kodu, her bir özelliği el ile okur ve yazar. Bir alternatif, çalışmanın bir `Deserialize` kısmını `Serialize` çağırmak veya yapmak için kullanılır. Bir örnek için, [Bu StackOverflow gönderisini](https://stackoverflow.com/a/59744873/12509023)inceleyin.

## <a name="other-custom-converter-samples"></a>Diğer özel dönüştürücü örnekleri

' [Den Newtonsoft.Json System.Text.Json geçiş](system-text-json-migrate-from-newtonsoft-how-to.md) , özel dönüştürücülerin ek örneklerini içerir.

Kaynak kodundaki [birim testleri klasörü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) , gibi diğer özel dönüştürücü örneklerini içerir: `System.Text.Json.Serialization`

* [Seri durumdan çıkarma sırasında null değeri 0 olarak dönüştüren Int32 Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)
* [Seri durumdan çıkarma sırasında hem dize hem de sayı değerlerine izin veren Int32 Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)
* [Sabit Listesi Dönüştürücüsü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)
* [Dış\<verileri kabul eden T> Dönüştürücüsü listeleyin](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)
* [Long [] bir sayı listesi ile birlikte çalışma](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)

Varolan bir yerleşik dönüştürücünün davranışını değiştiren bir dönüştürücü yapmanız gerekiyorsa, varolan dönüştürücünün özelleştirme için bir başlangıç noktası olarak sunmak üzere [kaynak kodunu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) alabilirsiniz.

## <a name="additional-resources"></a>Ek kaynaklar

* [Yerleşik dönüştürücüler için kaynak kodu](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)
* [İçinde DateTime ve DateTimeOffset desteğiSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.Jsonbakýþ](system-text-json-overview.md)
* [Nasıl kullanılırSystem.Text.Json](system-text-json-how-to.md)
* [Öğesinden geçişNewtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)
* [System.Text.JsonAPI başvurusu](xref:System.Text.Json)
* [System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
