---
title: JSON serileştirme-.NET için özel dönüştürücüler yazma
ms.date: 10/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: efbaf852f07b2b59111f0e330cf52470e3eca4c3
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705814"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a>.NET 'teki JSON serileştirme için özel dönüştürücüler yazma

Bu makalede, <xref:System.Text.Json> ad alanında belirtilen JSON serileştirme sınıfları için özel dönüştürücüler oluşturma işlemi gösterilmektedir. `System.Text.Json`giriş için bkz. [.net 'TE JSON serileştirme ve seri durumdan çıkarma](system-text-json-how-to.md).

*Dönüştürücü* bir nesneyi veya BIR değeri JSON öğesine veya bir değere dönüştüren bir sınıftır. `System.Text.Json` ad alanı, JavaScript temel elemanlarına eşleyen en basit türler için yerleşik dönüştürücülerde bulunur. Özel dönüştürücüler yazabilirsiniz:

* Yerleşik dönüştürücünün varsayılan davranışını geçersiz kılmak için. Örneğin, `DateTime` değerlerinin varsayılan ISO 8601-1:2019 biçimi yerine aa/gg/yyyy biçiminde temsil olmasını isteyebilirsiniz.
* Özel bir değer türünü desteklemek için. Örneğin, bir `PhoneNumber` yapısı.

Ayrıca, geçerli sürüme dahil olmayan işlevlerle `System.Text.Json` genişletmek için özel dönüştürücüler yazabilirsiniz. Bu makalenin ilerleyen bölümlerinde aşağıdaki senaryolar ele alınmıştır:

* [Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties).
* [Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key).
* [Polimorfik serisini destekler](#support-polymorphic-deserialization).

## <a name="custom-converter-patterns"></a>Özel dönüştürücü desenleri

Özel dönüştürücü oluşturmak için iki desen vardır: temel desen ve fabrika düzeni. Fabrika deseninin türü `Enum` işleyen veya genel türleri açık olan dönüştürücüler içindir. Temel model, genel olmayan ve kapalı genel türler içindir.  Örneğin, aşağıdaki türler için dönüştürücüler fabrika deseninin olmasını gerektirir:

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

Aşağıdaki örnek, varolan bir veri türü için varsayılan Serileştirmeyi geçersiz kılan bir dönüştürücütür. Dönüştürücü `DateTimeOffset` özellikleri için aa/gg/yyyy biçimini kullanır.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a>Örnek fabrika deseninin Dönüştürücüsü

Aşağıdaki kod, `Dictionary<Enum,TValue>`ile birlikte çalışarak özel bir dönüştürücüyü gösterir. İlk genel tür parametresi `Enum` ve ikincisi açık olduğundan, kod fabrika düzeniyle uyar. `CanConvert` yöntemi, yalnızca bir `Enum` türü olan iki genel parametre içeren bir `Dictionary` için `true` döndürür. İç dönüştürücü, `TValue`çalışma zamanında hangi türün sağlandığını işlemek için mevcut bir dönüştürücüyü alır. 

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

Yukarıdaki kod, bu makalede daha sonra [dize olmayan anahtarla destek sözlüğünde](#support-dictionary-with-non-string-key) gösterilenle aynıdır.

## <a name="steps-to-follow-the-basic-pattern"></a>Temel kalıbı izlemeye yönelik adımlar

Aşağıdaki adımlarda, temel kalıbı izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:

* Seri hale getirilecek ve seri durumdan çıkarılacak tür `T` <xref:System.Text.Json.Serialization.JsonConverter%601> türetilen bir sınıf oluşturun.
* Gelen JSON serisini kaldırmak için `Read` yöntemini geçersiz kılın ve `T`türüne dönüştürün. JSON 'ı okumak için yöntemine geçirilen <xref:System.Text.Json.Utf8JsonReader> kullanın.
* `T`türündeki gelen nesneyi seri hale getirmek için `Write` yöntemini geçersiz kılın. JSON yazmak için yöntemine geçirilen <xref:System.Text.Json.Utf8JsonWriter> kullanın.
* `CanConvert` yöntemini yalnızca gerekirse geçersiz kılın. Varsayılan uygulama, dönüştürülecek tür `T`tür olduğunda `true` döndürür. Bu nedenle, yalnızca tür `T` destekleyen dönüştürücüler Bu yöntemi geçersiz kılmalıdır. Bu yöntemi geçersiz kılmanın gerekli olduğu dönüştürücünün bir örneği için, bu makalenin ilerleyen kısımlarında yer alan [polimorfik serisini kaldırma](#support-polymorphic-deserialization) bölümüne bakın.

[Yerleşik dönüştürücüler kaynak koduna](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) , özel dönüştürücüler yazmak için başvuru uygulamaları olarak başvurabilirsiniz.

## <a name="steps-to-follow-the-factory-pattern"></a>Fabrika deseninin izlenmesi için adımlar

Aşağıdaki adımlarda, fabrika modelini izleyerek bir dönüştürücünün nasıl oluşturulacağı açıklanmaktadır:

* <xref:System.Text.Json.Serialization.JsonConverterFactory>türeten bir sınıf oluşturun.
* Dönüştürülecek tür dönüştürücünün işleyebileceği bir ise true döndürecek şekilde `CanConvert` yöntemini geçersiz kılın. Örneğin, dönüştürücü `List<T>` için ise yalnızca `List<int>`, `List<string>`ve `List<DateTime>`işleyebilir. 
* Çalışma zamanında belirtilen tür dönüşümü işleyecek bir dönüştürücü sınıfının örneğini döndürmek için `CreateConverter` yöntemini geçersiz kılın.
* `CreateConverter` yönteminin örnekleyen Converter sınıfını oluşturun. 

Açık genel türler için fabrika deseninin olması gerekir çünkü bir nesneyi bir dizeye ve bu dizeden dönüştürecek kod tüm türler için aynı değildir. Açık genel bir tür (örneğin`List<T>`) için bir dönüştürücü, arka planda kapalı bir genel tür (örneğin`List<DateTime>`) için bir dönüştürücü oluşturmak zorunda. Dönüştürücünün işleyebileceği her bir kapalı genel türü işlemek için kodun yazılması gerekir.

`Enum` türü açık bir genel türe benzer: bir `Enum` dönüştürücünün arka planda belirli bir `Enum` (örneğin,`WeekdaysEnum`) için bir dönüştürücü oluşturması gerekir. 

## <a name="error-handling"></a>Hata işleme

Hata işleme kodunda bir özel durum oluşturmanız gerekiyorsa, ileti olmadan bir <xref:System.Text.Json.JsonException> yerleştirmeyi düşünün. Bu özel durum türü otomatik olarak, hataya neden olan JSON bölümünün yolunu içeren bir ileti oluşturur. Örneğin, `throw new JsonException();`, aşağıdaki örnekte olduğu gibi bir hata iletisi üretir:

```
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

Bir ileti sağlarsanız (örneğin, `throw new JsonException("Error occurred")`, özel durum yine de <xref:System.Text.Json.JsonException.Path> özelliğinde yolunu sağlar.

## <a name="register-a-custom-converter"></a>Özel dönüştürücüyü kaydetme

`Serialize` ve `Deserialize` yöntemlerinin onu kullanmasını sağlamak için özel bir dönüştürücü *kaydedin* . Aşağıdaki yaklaşımlardan birini seçin:

* Dönüştürücü sınıfının bir örneğini <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> koleksiyonuna ekleyin.
* Özel dönüştürücü gerektiren özelliklere [[Jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) özniteliğini uygulayın.
* [[Jsonconverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) özniteliğini bir sınıfa veya özel bir değer türünü temsil eden bir yapıya uygulayın.

## <a name="registration-sample---converters-collection"></a>Kayıt örneği-dönüştürücüler koleksiyonu 

Aşağıda, <xref:System.DateTimeOffset>türü özellikler için <xref:System.ComponentModel.DateTimeOffsetConverter> varsayılan değer veren bir örnek verilmiştir:

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

Aşağıdaki kod, özel `DateTimeOffset` dönüştürücüsünü kullanarak seri durumdan çıkarmak için aynı yaklaşımı kullanır:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a>Kayıt örneği-[JsonConverter] bir özellikte

Aşağıdaki kod `Date` özelliği için özel bir dönüştürücü seçer:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

`WeatherForecastWithConverterAttribute` seri hale getirilecek kod `JsonSerializeOptions.Converters`kullanımını gerektirmez:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

Seri durumdan çıkarılacak kod ayrıca `Converters`kullanımını gerektirmez:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a>Kayıt örneği-[JsonConverter] bir tür üzerinde

Bir struct oluşturan ve `[JsonConverter]` özniteliğini uygulayan kod aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

Önceki yapı için özel dönüştürücü aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

Yapı üzerindeki `[JsonConvert]` özniteliği, özel dönüştürücüyü `Temperature`türü özellikler için varsayılan olarak kaydeder. Dönüştürücü, seri hale getirmek veya serisini kaldırmak için aşağıdaki türün `TemperatureCelsius` özelliğinde otomatik olarak kullanılır:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a>Dönüştürücü kayıt önceliği

Serileştirme veya seri durumundan çıkarma sırasında, en yüksek öncelikten en düşüğe doğru listelenen her bir JSON öğesi için bir dönüştürücü seçilir:

* bir özelliğe uygulandı `[JsonConverter]`.
* `Converters` koleksiyonuna bir dönüştürücü eklendi.
* özel bir değer türüne veya POCO 'a uygulanan `[JsonConverter]`.

Bir tür için birden çok özel dönüştürücü `Converters` koleksiyonuna kayıtlıysa, `CanConvert` için true döndüren ilk dönüştürücü kullanılır.

Yalnızca uygulanabilir özel dönüştürücü kayıtlı değilse, yerleşik bir dönüştürücü seçilir.

## <a name="converter-samples-for-common-scenarios"></a>Yaygın senaryolar için dönüştürücü örnekleri

Aşağıdaki bölümlerde, yerleşik işlevlerin sağlamadığı bazı yaygın senaryolar ele alan dönüştürücü örnekleri sağlanmaktadır.

* [Çıkartılan türlerin nesne özelliklerine serisini kaldırma](#deserialize-inferred-types-to-object-properties)
* [Dize olmayan anahtarla destek sözlüğü](#support-dictionary-with-non-string-key)
* [Polimorfik serisini destekler](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a>Çıkartılan türlerin nesne özelliklerine serisini kaldırma

`Object`türünde bir özelliğin serisi kaldırılırken, bir `JsonElement` nesnesi oluşturulur. Bunun nedeni, seri hale getiricinin oluşturulacak CLR türünü bilmeyeceği ve tahmin etmeye çalışmayın. Örneğin, bir JSON özelliğinde "true" varsa, seri hale getirici değerin bir `Boolean`olduğunu ve bir öğede "01/01/2019" varsa, seri hale getirici bir `DateTime`olduğunu çıkarmaz.

Tür çıkarımı yanlış olabilir. Seri hale getirici, `long`olarak ondalık noktası olmayan bir JSON numarası ayrıştırdığında, bu, değerin başlangıçta bir `ulong` veya `BigInteger`olarak serileştirildiği, Aralık dışı sorunlara yol açabilir. Sayı ilk olarak bir `decimal`olarak seri hale getirileolduysa, `double` ondalık noktası olan bir sayının çözümlenmesi duyarlık kaybedebilir.

Tür çıkarımı gerektiren senaryolar için aşağıdaki kodda `Object` özellikleri için özel bir dönüştürücü gösterilmektedir. Kod dönüştürür:

* `Boolean` `true` ve `false`
* `long` veya `double` sayılar
* `DateTime` tarihler
* `string` dizeler
* `JsonElement` diğer her şey

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

Aşağıdaki kod dönüştürücüyü kaydeder:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertInferredTypesToObject.cs?name=SnippetRegister)]

Aşağıda `Object` özelliklere sahip örnek bir tür verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

Seri durumdan çıkarılacak aşağıdaki JSON örneği, `DateTime`, `long`ve `string`olarak seri durumdan çıkarılacak değerler içerir:

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

Özel dönüştürücü olmadan, seri durumdan çıkarma her özelliğe bir `JsonElement` koyar.

`System.Text.Json.Serialization` ad alanındaki [birim testleri klasörü](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) , nesne özelliklerine seri durumdan çıkarmayı işleyen özel dönüştürücülerin daha fazla örneklerine sahiptir.

### <a name="support-dictionary-with-non-string-key"></a>Dize olmayan anahtarla destek sözlüğü

Sözlük koleksiyonları için yerleşik destek `Dictionary<string, TValue>`içindir. Diğer bir deyişle, anahtar bir dize olmalıdır. Anahtar olarak bir tamsayı veya başka tür içeren bir sözlüğü desteklemek için özel bir dönüştürücü gerekir.

Aşağıdaki kod, `Dictionary<Enum,TValue>`ile birlikte çalışarak özel bir dönüştürücüyü gösterir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

Aşağıdaki kod dönüştürücüyü kaydeder:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

Dönüştürücü aşağıdaki `Enum`kullanan aşağıdaki sınıfın `TemperatureRanges` özelliğini seri hale getirebilirsiniz ve serisini kaldıramıyor:

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

`System.Text.Json.Serialization` ad alanındaki [birim testleri klasörü](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) , dize dışı anahtar sözlüklerini işleyen özel dönüştürücülere daha fazla örnek içerir.

### <a name="support-polymorphic-deserialization"></a>Polimorfik serisini destekler

[Polimorfik serileştirme](system-text-json-how-to.md#serialize-properties-of-derived-classes) özel bir dönüştürücü gerektirmez, ancak seri durumundan çıkarma özel bir dönüştürücü gerektirir.

Örneğin, `Employee` ve `Customer` türetilmiş sınıflarla `Person` soyut bir temel sınıfınız olduğunu varsayalım. Polimorfik seri kaldırma, tasarım zamanında `Person` serisini kaldırma hedefi olarak belirtebileceğiniz ve `Customer` ve JSON 'daki `Employee` nesnelerinin çalışma zamanında doğru şekilde seri durumdan çıkarılmasıdır. Seri durumdan çıkarma sırasında, JSON 'da gerekli türü tanımlayan ipuçları bulmanız gerekir. Kullanılabilir ipuçları türleri her senaryoya göre farklılık gösterir. Örneğin, bir Ayrıştırıcı özelliği kullanılabilir olabilir veya belirli bir özelliğin varlığına veya yokluğuna güvenebilirsiniz. `System.Text.Json` geçerli sürümü, çok biçimli seri kaldırma senaryolarının nasıl işleneceğini belirtmek için öznitelikler sağlamaz, bu nedenle özel dönüştürücüler gereklidir.

Aşağıdaki kod, temel sınıfı, iki türetilmiş sınıfı ve bunlar için özel bir dönüştürücüyü gösterir. Dönüştürücü, çok biçimli seri kaldırma işlemi yapmak için bir Ayrıştırıcı özelliği kullanır. Tür ayrıştırıcısı sınıf tanımlarında değildir, ancak serileştirme sırasında oluşturulur ve seri durumundan çıkarma sırasında okunabilir.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

Aşağıdaki kod dönüştürücüyü kaydeder:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ConvertPolymorphic.cs?name=SnippetRegister)]

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

## <a name="other-custom-converter-samples"></a>Diğer özel dönüştürücü örnekleri

`System.Text.Json.Serialization` kaynak kodundaki [birim testleri klasörü](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) , aşağıdakiler gibi diğer özel dönüştürücü örneklerini içerir:

* seri durumdan çıkarma sırasında null değeri 0 olarak dönüştüren `Int32` Dönüştürücüsü
* seri durumdan çıkarma sırasında hem dize hem de sayı değerlerine izin veren `Int32` Dönüştürücüsü
* `Enum` Dönüştürücüsü
* dış veri kabul eden `List<T>` Dönüştürücüsü
* virgülle ayrılmış bir sayı listesi ile birlikte kullanılan `Long[]` Dönüştürücüsü 

## <a name="additional-resources"></a>Ek kaynaklar

* [System. Text. JSON genel bakış](system-text-json-overview.md)
* [System. Text. JSON API başvurusu](xref:System.Text.Json)
* [System. Text. JSON kullanma](system-text-json-how-to.md)
* [Yerleşik dönüştürücüler için kaynak kodu](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* `System.Text.Json` yönelik özel dönüştürücüler ile ilgili GitHub sorunları
  * [36639 özel dönüştürücüler tanıtımı](https://github.com/dotnet/corefx/issues/36639)
  * [Nesne serisini kaldırma hakkında 38713](https://github.com/dotnet/corefx/issues/38713)
  * [dize olmayan anahtar sözlükleri hakkında 40120](https://github.com/dotnet/corefx/issues/40120)
  * [çok biçimli seri kaldırma hakkında 37787](https://github.com/dotnet/corefx/issues/37787)
