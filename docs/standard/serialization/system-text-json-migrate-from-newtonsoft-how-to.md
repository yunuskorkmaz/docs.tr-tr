---
title: Newtonsoft. JSON 'dan System. Text. JSON-.NET ' e geçiş yapın
author: tdykstra
ms.author: tdykstra
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 01f94bcfce97da8c71b1b709baa34c2b7509a5e5
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116692"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Newtonsoft. JSON 'dan System. Text. JSON 'a geçiş

Bu makalede [Newtonsoft. JSON](https://www.newtonsoft.com/json) ' dan <xref:System.Text.Json>' a nasıl geçiş yapılacağı gösterilmektedir.

 `System.Text.Json` öncelikle performans, güvenlik ve standartlar uyumluluğuna odaklanır. Varsayılan davranışta bazı önemli farklılıklar vardır ve `Newtonsoft.Json`Özellik eşliği yoktur. Bazı senaryolarda `System.Text.Json` yerleşik işlevselliği yoktur, ancak önerilen geçici çözümler vardır. Diğer senaryolar için geçici çözümler pratik bir şekilde yapılır. Uygulamanız eksik bir özelliğe bağımlıysa, senaryonuza yönelik desteğin eklenip eklenemediğine ulaşmak için [bir sorun](https://github.com/dotnet/runtime/issues/new) yerleştirmeyi düşünün.

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

Bu makalenin çoğu, <xref:System.Text.Json.JsonSerializer> API 'sini kullanma hakkında, ancak aynı zamanda <xref:System.Text.Json.JsonDocument> (Belge Nesne Modeli ya da DOM), <xref:System.Text.Json.Utf8JsonReader>ve <xref:System.Text.Json.Utf8JsonWriter> türlerini temsil eden yönergeler de içerir. Makale aşağıdaki sırada bölümler halinde düzenlenmiştir:

* [Newtonsoft. JSON ile karşılaştırıldığında **varsayılan** jsonserializer davranışındaki farklılıklar](#differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson)
* [Geçici çözüm gerektiren JsonSerializer kullanan senaryolar](#scenarios-using-jsonserializer-that-require-workarounds)
* [JsonSerializer 'ın Şu anda desteklemediği senaryolar](#scenarios-that-jsonserializer-currently-doesnt-support)
* [JToken (JObject, JArray gibi) ile karşılaştırılan JsonDocument ve JsonElement](#jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray)
* [Utf8JsonReader, JsonTextReader ile karşılaştırılır](#utf8jsonreader-compared-to-jsontextreader)
* [Utf8JsonWriter, JsonTextWriter ile karşılaştırılır](#utf8jsonwriter-compared-to-jsontextwriter)

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Newtonsoft. JSON ile karşılaştırıldığında varsayılan JsonSerializer davranışındaki farklılıklar

<xref:System.Text.Json>, varsayılan olarak katı olur ve arayan adına tahmin veya yorumlamayı önler, belirleyici davranışı vurgulayarak. Kitaplık, performans ve güvenlik için kasıtlı olarak bu şekilde tasarlanmıştır. `Newtonsoft.Json` varsayılan olarak esnektir. Tasarımda bu temel fark, varsayılan davranıştaki aşağıdaki belirli farklılıklardan birçoğın arkasında bulunur.

### <a name="case-insensitive-deserialization"></a>Büyük/küçük harfe duyarsız seri hale 

Seri durumdan çıkarma sırasında `Newtonsoft.Json`, varsayılan olarak büyük/küçük harfe duyarsız Özellik adı eşleştirmeyi yapar. <xref:System.Text.Json> varsayılan, büyük/küçük harfe duyarlıdır ve tam bir eşleşme yaptığından daha iyi performans sağlar. Büyük/küçük harfe duyarsız eşleşme yapma hakkında daha fazla bilgi için bkz. [büyük/küçük harfe duyarsız Özellik eşleştirme](system-text-json-how-to.md#case-insensitive-property-matching).

ASP.NET Core kullanarak dolaylı `System.Text.Json` kullanıyorsanız, `Newtonsoft.Json`gibi davranışları almak için herhangi bir şey yapmanız gerekmez. ASP.NET Core, `System.Text.Json`kullandığında [Camel](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) ve büyük/küçük harfe duyarsız eşleşme ayarlarını belirtir.

### <a name="comments"></a>Açıklamalar

Seri durumdan çıkarma sırasında, `Newtonsoft.Json` JSON 'daki açıklamaları varsayılan olarak yoksayar. <xref:System.Text.Json> varsayılan, [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtiminde bunları içermediğinden, açıklamalar için özel durumlar atmak şeklindedir. Açıklamalara izin verme hakkında daha fazla bilgi için bkz. [yorumlara Izin verme ve sondaki virgüller](system-text-json-how-to.md#allow-comments-and-trailing-commas).

### <a name="trailing-commas"></a>Sondaki virgüller

Seri durumdan çıkarma sırasında `Newtonsoft.Json`, varsayılan olarak sondaki virgülleri yoksayar. Ayrıca, birden çok sondaki virgül yoksayar (örneğin, `[{"Color":"Red"},{"Color":"Green"},,]`). <xref:System.Text.Json> varsayılan, [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi bunlara izin vermediğinden, sondaki virgüller için özel durumlar atmak şeklindedir. `System.Text.Json` kabul etme hakkında daha fazla bilgi için bkz. [yorumlara Izin verme ve sondaki virgüller](system-text-json-how-to.md#allow-comments-and-trailing-commas). Birden çok bitiş virgülne izin vermenin bir yolu yoktur.

### <a name="json-strings-property-names-and-string-values"></a>JSON dizeleri (özellik adları ve dize değerleri)

Seri durumdan çıkarma sırasında, `Newtonsoft.Json` çift tırnak, tek tırnak veya tırnak işaretleri olmadan çevrelenmiş özellik adlarını kabul eder. Çift tırnak veya tek tırnak işareti içine alınmış dize değerlerini kabul eder. Örneğin, `Newtonsoft.Json` aşağıdaki JSON 'ı kabul eder:

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json` yalnızca çift tırnak içindeki özellik adlarını ve dize değerlerini kabul eder çünkü bu biçim, [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi için gereklidir ve geçerli JSON olarak kabul edilen tek biçimdir.

Tek tırnak içine alınmış bir değer, aşağıdaki iletiyle birlikte bir [Jsonexception](xref:System.Text.Json.JsonException) ile sonuçlanır:

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Dize özellikleri için dize olmayan değerler

`Newtonsoft.Json` dize olmayan değerleri kabul eder, örneğin bir sayı veya sabit değer `true` ve `false`, tür dizesinin özelliklerine seri durumundan çıkarma için. Aşağıdaki sınıfa başarıyla seri hale getirilen `Newtonsoft.Json` JSON örneği aşağıda verilmiştir:

```json
{
  "String1": 1,
  "String2": true,
  "String3": false
}
```

```csharp
public class ExampleClass
{
    public string String1 { get; set; }
    public string String2 { get; set; }
    public string String3 { get; set; }
}
```

`System.Text.Json` dize olmayan değerlerin dize özelliklerine serisini kaldıramıyor. Bir dize alanı için alınan dize olmayan bir değer, aşağıdaki iletiyle birlikte bir [Jsonexception](xref:System.Text.Json.JsonException) ile sonuçlanır:

```
The JSON value could not be converted to System.String.
```

### <a name="converter-registration-precedence"></a>Dönüştürücü kayıt önceliği

Özel dönüştürücüler için `Newtonsoft.Json` kayıt önceliği aşağıdaki gibidir:

* Özelliğindeki öznitelik
* Türündeki öznitelik
* [Dönüştürücüler](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm) koleksiyonu

Bu sıra, `Converters` koleksiyonundaki özel bir dönüştürücünün, tür düzeyinde bir öznitelik uygulanarak kaydedilen bir dönüştürücü tarafından geçersiz kılındığı anlamına gelir. Bu kayıtların her ikisi de özellik düzeyindeki bir öznitelik tarafından geçersiz kılınır.

Özel dönüştürücüler için <xref:System.Text.Json> kayıt önceliği farklıdır:

* Özelliğindeki öznitelik
* <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyonu
* Türündeki öznitelik

Burada fark, `Converters` koleksiyonundaki özel dönüştürücünün tür düzeyinde bir özniteliği geçersiz kılar. Bu öncelik sırasının arkasındaki amaç, çalışma zamanı değişikliklerinin tasarım zamanı seçimlerini geçersiz kılmasını sağlamak olacaktır. Önceliği değiştirme yolu yoktur.

Özel dönüştürücü kaydı hakkında daha fazla bilgi için bkz. [özel dönüştürücüyü kaydetme](system-text-json-converters-how-to.md#register-a-custom-converter).

### <a name="character-escaping"></a>Karakter kaçış

Serileştirme sırasında `Newtonsoft.Json`, karakterlerin kaçış olmadan geçmesine izin verme konusunda görece bir şekilde izin verir. Diğer bir deyişle, `xxxx` karakterin kod noktası olduğu `\uxxxx` değiştirmez. Burada kaçış yaptığı yerde, karakterden önce bir `\` yayarak (örneğin, `"` `\"`olur). <xref:System.Text.Json>, siteler arası komut dosyası (XSS) veya bilgi açıklama saldırılarına karşı derinlemesine savunma korumaları sağlamak için varsayılan olarak daha fazla karakter çıkar ve altı karakterli sırayı kullanarak bunu yapar. `System.Text.Json`, tüm ASCII olmayan karakterleri varsayılan olarak çıkar, bu nedenle `Newtonsoft.Json``StringEscapeHandling.EscapeNonAscii` kullanıyorsanız herhangi bir şey yapmanız gerekmez. `System.Text.Json` Ayrıca, varsayılan olarak HTML duyarlı karakterleri de çıkar. Varsayılan `System.Text.Json` davranışının nasıl geçersiz kılındığı hakkında daha fazla bilgi için bkz. [Özelleştirme karakter kodlaması](system-text-json-how-to.md#customize-character-encoding).

### <a name="deserialization-of-object-properties"></a>Nesne özelliklerinin serisini kaldırma

`Newtonsoft.Json` POCOs 'ta veya `Dictionary<string, object>`türündeki sözlüklerde `object` özellikler için seri hale geldiğinde:

* JSON yükünde (`null`dışında) ilkel değerlerin türünü ve paketlenmiş bir nesne olarak depolanan `string`, `long`, `double`, `boolean`veya `DateTime` döndürür. *İlkel değerler* , JSON numarası, dize, `true`, `false`veya `null`gıbı tek JSON değerlerdir.
* JSON yükünde karmaşık değerler için bir `JObject` veya `JArray` döndürür. *Karmaşık değerler* , küme ayraçları (`{}`) içindeki JSON anahtar-değer çiftlerinin veya köşeli ayraçlar (`[]`) içindeki değer listelerinde bulunan koleksiyonlardır. Küme ayraçları ve köşeli ayraçlar içindeki Özellikler ve değerler ek özelliklere veya değerlere sahip olabilir.
* Yükün `null` JSON sabit değeri olduğunda null bir başvuru döndürür.

<xref:System.Text.Json>, `System.Object` özellik veya sözlük değeri içinde hem ilkel hem de karmaşık değerler için kutulanmış `JsonElement` depolar. Ancak, `null` `Newtonsoft.Json` aynı şekilde davranır ve yükün içinde `null` JSON sabit değeri olduğunda null bir başvuru döndürür.

`object` özellikleri için tür çıkarımı uygulamak için, [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties)bölümünde örnek gibi bir dönüştürücü oluşturun.

### <a name="maximum-depth"></a>En yüksek derinlik

`Newtonsoft.Json` varsayılan olarak en yüksek derinlik sınırına sahip değildir. <xref:System.Text.Json> için varsayılan bir 64 sınırı vardır ve <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>ayarlanarak yapılandırılabilir.

### <a name="omit-null-value-properties"></a>Null değer özelliklerini atla

`Newtonsoft.Json`, null değerli özelliklerin Serileştirmeden dışlanmasına neden olan genel bir ayara sahiptir: [Nullvaluehandling. Ignore](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_NullValueHandling.htm). <xref:System.Text.Json> ilgili seçenek <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues%2A>.

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>Geçici çözüm gerektiren JsonSerializer kullanan senaryolar

Aşağıdaki senaryolar yerleşik işlevsellik tarafından desteklenmez, ancak geçici kod geçici çözümler için verilmiştir. Geçici çözümlerin çoğu için [özel dönüştürücüler](system-text-json-converters-how-to.md)uygulamanız gerekir.

### <a name="specify-date-format"></a>Tarih biçimini belirtin

`Newtonsoft.Json`, `DateTime` ve `DateTimeOffset` türlerinin özelliklerinin serileştirilme ve seri durumdan çıkarılme biçimini denetlemek için çeşitli yollar sağlar:

* `DateTimeZoneHandling` ayarı, tüm `DateTime` değerlerini UTC tarihleri olarak seri hale getirmek için kullanılabilir.
* `DateFormatString` ayar ve `DateTime` dönüştürücüler, tarih dizelerinin biçimini özelleştirmek için kullanılabilir.

<xref:System.Text.Json>' de, yerleşik desteği olan tek Biçim ISO 8601-1:2019 ' dir ve bu yana büyük ölçüde benimsediğinden ve tam olarak gidiş dönüş yaptığından emin olur. Başka bir biçim kullanmak için özel bir dönüştürücü oluşturun. Daha fazla bilgi için bkz. [System. Text. JSON Içinde DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md).

### <a name="quoted-numbers"></a>Tırnak işaretli sayılar

`Newtonsoft.Json`, JSON dizeleri (tırnak içine alınmış) tarafından temsil edilen sayıları seri hale verebilir veya serisini kaldıramıyor. Örneğin, bunu kabul edebilir: `{"DegreesCelsius":23}`yerine `{"DegreesCelsius":"23"}`. <xref:System.Text.Json>' de bu davranışı etkinleştirmek için, aşağıdaki örnekte olduğu gibi özel bir dönüştürücü uygulayın. Dönüştürücü `long`olarak tanımlanan özellikleri işler:

* Onları JSON dizeleri olarak serileştirir. 
* Seri durumdan çıkarılırken, tırnak içindeki JSON numaralarını ve sayıları kabul eder.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

Bu özel dönüştürücüyü ayrı `long` özelliklerde [bir öznitelik kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) veya dönüştürücüyü <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyonuna [ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) kaydettirin.

### <a name="dictionary-with-non-string-key"></a>Dize olmayan anahtarla sözlük

`Newtonsoft.Json`, `Dictionary<TKey, TValue>`türündeki koleksiyonları destekler. <xref:System.Text.Json> sözlük koleksiyonları için yerleşik destek `Dictionary<string, TValue>`sınırlıdır. Diğer bir deyişle, anahtar bir dize olmalıdır.

Anahtar olarak bir tamsayı veya diğer tür ile bir sözlüğü desteklemek için, [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key)bölümünde örnek gibi bir dönüştürücü oluşturun.

### <a name="polymorphic-serialization"></a>Polimorfik serileştirme

`Newtonsoft.Json` otomatik olarak çok biçimli serileştirme işlemi yapar. <xref:System.Text.Json>'ın sınırlı sayıda polimorfik serileştirme özellikleri hakkında bilgi için bkz. [türetilmiş sınıfların serileştirme özellikleri](system-text-json-how-to.md#serialize-properties-of-derived-classes).

Burada açıklanan geçici çözüm, `object`tür olarak türetilmiş sınıflar içerebilen özellikleri tanımlamaktır. Bu mümkün değilse, diğer bir seçenek de [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#support-polymorphic-deserialization)içindeki örnek gibi tüm devralma türü hiyerarşisi için `Write` yöntemiyle bir dönüştürücü oluşturmaktır.

### <a name="polymorphic-deserialization"></a>Polimorfik seri kaldırma

`Newtonsoft.Json` serileştirilirken JSON 'a tür adı meta verileri ekleyen bir `TypeNameHandling` ayarı vardır. Seri durumdan çıkarma sırasında çok biçimli seri kaldırma işlemi yaparken meta verileri kullanır. <xref:System.Text.Json>, çok sayıda [polimorfik serileştirme](system-text-json-how-to.md#serialize-properties-of-derived-classes) , ancak polimorfik seri hale getirme olamaz.

Polimorfik serisini desteklemek için [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#support-polymorphic-deserialization)bölümünde örnek gibi bir dönüştürücü oluşturun.

### <a name="required-properties"></a>Gerekli özellikler

Seri durumdan çıkarma sırasında, hedef türün özelliklerinden biri için JSON 'da hiçbir değer alınmazsa, <xref:System.Text.Json> bir özel durum oluşturmaz. Örneğin, bir `WeatherForecast` sınıfınız varsa:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Aşağıdaki JSON, hata olmadan seri durumdan çıkarılacak:

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

JSON içinde `Date` özelliği yoksa seriyi kaldırma başarısız olması için özel bir dönüştürücü uygulayın. Aşağıdaki örnek dönüştürücü kodu, seri kaldırma tamamlandıktan sonra `Date` özelliği ayarlanmamışsa bir özel durum oluşturur:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

[POCO sınıfında bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) veya <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyonuna [dönüştürücü ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) bu özel dönüştürücüyü kaydettirin.

Bu kalıbı izlerseniz, <xref:System.Text.Json.JsonSerializer.Serialize%2A> veya <xref:System.Text.Json.JsonSerializer.Deserialize%2A>yinelemeli olarak çağırırken Options nesnesine geçiş yapmayın. Options nesnesi <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> koleksiyonunu içerir. `Serialize` veya `Deserialize`' a geçirirseniz, özel dönüştürücü kendi kendine çağırır ve yığın taşması özel durumuyla sonuçlanan sonsuz bir döngü yapar. Varsayılan seçenekler uygun değilse, gereken ayarlarla seçeneklerin yeni bir örneğini oluşturun. Her yeni örnek bağımsız olarak önbelleğe aldığından bu yaklaşım yavaş olur.

Yukarıdaki dönüştürücü kodu basitleştirilmiş bir örnektir. Öznitelikleri (örneğin, [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) veya farklı seçenekler (özel kodlayıcılar gibi) işlemeniz gerekiyorsa ek mantık gerekir. Ayrıca, örnek kod, oluşturucuda varsayılan bir değer ayarlanan özellikleri işlemez. Bu yaklaşım aşağıdaki senaryolar arasında ayrım yapmaz:

* JSON 'da bir özellik eksik.
* Null atanamaz bir tür için bir özellik JSON içinde bulunur, ancak değer, `int`için sıfır gibi varsayılan değerdir.
* JSON 'da null yapılabilir bir tür özelliği var, ancak değer null.

### <a name="deserialize-null-to-non-nullable-type"></a>Null olamayan tür için null serisini kaldırma 

`Newtonsoft.Json` aşağıdaki senaryoda bir özel durum oluşturmaz:

* `NullValueHandling` `Ignore`olarak ayarlanır ve
* Seri durumdan çıkarma sırasında JSON null yapılamayan bir tür için null değer içerir.

Aynı senaryoda <xref:System.Text.Json> bir özel durum oluşturur. (Karşılık gelen null işleme ayarı <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>.)

Hedef türün sahibiyseniz, en iyi geçici çözüm, özelliğin boş değer atanabilir olmasını (örneğin, `int` `int?`olarak değiştirmesini) sağlar.

Farklı bir geçici çözüm, `DateTimeOffset` türleri için null değerleri işleyen aşağıdaki örnek gibi tür için bir dönüştürücü hale getirme örneğidir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

Bu özel dönüştürücüyü [, özellik üzerindeki bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) veya dönüştürücüyü <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyonuna [ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) kaydettirin.

**Note:** Önceki dönüştürücü, varsayılan değerleri belirten POCOs 'lar için `Newtonsoft.Json` göre **null değerleri farklı işler** . Örneğin, aşağıdaki kodun hedef nesneniz temsil ettiğini varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

Ve önceki dönüştürücüyü kullanarak aşağıdaki JSON 'nin seri durumdan çıkarıldığını varsayalım:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Seri durumdan çıktıktan sonra, `Date` özelliği 1/1/0001 (`default(DateTimeOffset)`), yani oluşturucuda ayarlanan değerin üzerine yazılır. Aynı POCO ve JSON verildiğinde `Newtonsoft.Json` serisini kaldırma, `Date` özelliğinde 1/1/2001 ' i bırakır.

### <a name="deserialize-to-immutable-classes-and-structs"></a>Sabit sınıflar ve yapılar için seri durumdan çıkarma

`Newtonsoft.Json`, parametreleri olan oluşturucuları kullanabilmesi için sabit sınıflar ve yapılar için seri durumdan çıkarabilirler. <xref:System.Text.Json> yalnızca ortak parametresiz oluşturucuları destekler. Geçici bir çözüm olarak, özel bir dönüştürücüde parametreleri olan bir Oluşturucu çağırabilirsiniz.

İşte birden çok Oluşturucu parametresi olan değişmez bir struct:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

İşte bu yapıyı seri hale getirir ve seri hale getirir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

Dönüştürücüyü <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyonuna [ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) bu özel dönüştürücüyü kaydedin.

Açık genel özellikleri işleyen benzer dönüştürücünün bir örneği için bkz. [anahtar-değer çiftleri için yerleşik dönüştürücü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).

### <a name="specify-constructor-to-use"></a>Kullanılacak oluşturucuyu belirtin

`Newtonsoft.Json` `[JsonConstructor]` özniteliği bir POCO 'ya seri durumdan çıkarılırken hangi oluşturucunun çağrılacağını belirtmenizi sağlar. <xref:System.Text.Json> yalnızca parametresiz oluşturucuları destekler. Geçici bir çözüm olarak, özel bir dönüştürücüde hangi oluşturucuyu ihtiyacınız olduğunu çağırabilirsiniz. [Sabit sınıflar ve yapılar Için seri durumdan çıkarma](#deserialize-to-immutable-classes-and-structs)örneğine bakın.

### <a name="conditionally-ignore-a-property"></a>Özelliği koşullu olarak Yoksay

`Newtonsoft.Json` serileştirme veya seri durumdan çıkarma için bir özelliği koşullu olarak yoksaymanın birkaç yolu vardır:

* `DefaultContractResolver`, rastgele ölçütlere göre dahil edilecek veya hariç tutulacak özellikleri seçmenizi sağlar. 
* `JsonSerializerSettings` `NullValueHandling` ve `DefaultValueHandling` ayarları, tüm null değer veya varsayılan değer özelliklerinin yok sayılacağını belirtmenize olanak tanır.
* `[JsonProperty]` özniteliğinde `NullValueHandling` ve `DefaultValueHandling` ayarları, null ya da varsayılan değer olarak ayarlandığında yoksayılacak tek tek özellikleri belirtmenize izin verir.

<xref:System.Text.Json> serileştirilirken özellikleri atlamak için aşağıdaki yolları sağlar:

* Bir özellikte [[Jsonıgnore]](system-text-json-how-to.md#exclude-individual-properties) özniteliği, serileştirme SıRASıNDA özelliğin JSON 'dan atlanmasına neden olur.
* [Ignorenullvalues](system-text-json-how-to.md#exclude-all-null-value-properties) genel seçeneği, tüm null değerli özellikleri dışlamanızı sağlar.
* [Ignorereadonlyproperties](system-text-json-how-to.md#exclude-all-read-only-properties) genel seçeneği, tüm salt okunurdur özellikleri dışlamanızı sağlar.

Bu seçenekler **şunları yapmanızı sağlar** :

* Türü için varsayılan değere sahip tüm özellikleri yoksayın.
* Türü için varsayılan değere sahip seçili özellikleri yoksayın.
* Değerleri null ise seçili özellikleri yoksayın.
* Çalışma zamanında değerlendirilen rastgele ölçütlere göre seçili özellikleri yoksayın. 

Bu işlevsellik için özel bir dönüştürücü yazabilirsiniz. İşte bu yaklaşımı gösteren örnek bir POCO ve özel dönüştürücü.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

Dönüştürücü, değeri null, boş bir dize veya "N/A" ise, `Summary` özelliğinin Serileştirmeden atlanmasına neden olur. 

Bu özel dönüştürücüyü [sınıfında bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) veya dönüştürücüyü <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyonuna [ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) kaydettirin.

Bu yaklaşım aşağıdaki durumlarda ek mantık gerektirir:

* POCO, karmaşık özellikler içerir.
* `[JsonIgnore]` veya özel kodlayıcılar gibi seçenekler gibi öznitelikleri işlemeniz gerekir.

### <a name="callbacks"></a>Çağrı

`Newtonsoft.Json` serileştirme veya seri kaldırma işleminde özel kodu birkaç noktada yürütmenize imkan tanır:

* Onserisini kaldırma (bir nesnenin serisini kaldırmada başlayan)
* Onseri durumdan çıkarılan (bir nesnenin serisini kaldırma tamamlandığında)
* Onserileştirilme (bir nesne seri hale getirilmeye Başlarken)
* Onserileştirilmiş (bir nesne serileştirildiğinde)

<xref:System.Text.Json>, özel bir dönüştürücü yazarak geri çağırmaların benzetimini yapabilirsiniz. Aşağıdaki örnek bir POCO için özel dönüştürücüyü gösterir. Dönüştürücü, `Newtonsoft.Json` geri çağırmaya karşılık gelen her bir noktada bir ileti görüntüleyen kodu içerir.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

Bu özel dönüştürücüyü [sınıfında bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) veya dönüştürücüyü <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyonuna [ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) kaydettirin.

Önceki örneği takip eden özel bir dönüştürücü kullanıyorsanız:

* `OnDeserializing` kodun yeni POCO örneğine erişimi yok. Yeni POCO örneğini serisini kaldırma başlangıcında işlemek için, bu kodu POCO yapıcısına koyun.
* `Serialize` veya `Deserialize`yinelemeli olarak çağrılırken Options nesnesine geçiş yapmayın. Options nesnesi `Converters` koleksiyonunu içerir. `Serialize` veya `Deserialize`' a geçirirseniz, dönüştürücü kullanılır ve yığın taşması özel durumuna neden olan sonsuz bir döngü oluşturulur.

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>JsonSerializer 'ın Şu anda desteklemediği senaryolar

Aşağıdaki senaryolar için geçici çözümler olasıdır, ancak bazılarının uygulanması görece zor olabilir. Bu makale, bu senaryolar için geçici çözümler için kod örnekleri sağlamaz.

Bu, `System.Text.Json`eşdeğerleri olmayan `Newtonsoft.Json` özelliklerinin ayrıntılı bir listesi değildir. Listede, [GitHub sorunları](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) veya [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) gönderileri için istenen birçok senaryo bulunur.

Bu senaryolardan biri için geçici çözüm uygular ve kodu paylaşabilir, sayfanın alt kısmındaki "**Bu sayfa**" düğmesini seçin. Bu, bir GitHub sorunu oluşturur ve sayfanın alt kısmında listelenen sorunlara ekler.

### <a name="types-without-built-in-support"></a>Yerleşik destek olmadan türler

<xref:System.Text.Json>, aşağıdaki türler için yerleşik destek sağlamaz:

* <xref:System.Data.DataTable> ve ilgili türler
* F#[ayırt edici birleşimler](../../fsharp/language-reference/discriminated-unions.md), [kayıt türleri](../../fsharp/language-reference/records.md)ve [anonim kayıt türleri](../../fsharp/language-reference/anonymous-records.md)gibi türler.
* <xref:System.Collections.Specialized> ad alanındaki koleksiyon türleri
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple> ve ilişkili genel türleri

Özel dönüştürücüler, yerleşik desteği olmayan türler için uygulanabilir.

### <a name="public-and-non-public-fields"></a>Ortak ve genel olmayan alanlar

`Newtonsoft.Json` alanları seri hale getirmek ve seri durumdan çıkarmak için özellikleri. <xref:System.Text.Json> yalnızca ortak özelliklerle birlikte kullanılabilir. Özel dönüştürücüler, bu işlevselliği sağlayabilir.

### <a name="internal-and-private-property-setters-and-getters"></a>İç ve özel özellik ayarlayıcıları ve alıcılar

`Newtonsoft.Json`, özel ve iç özellik ayarlayıcıları ve geticileri `JsonProperty` özniteliği aracılığıyla kullanabilir. <xref:System.Text.Json> yalnızca genel ayarlayıcıları destekler. Özel dönüştürücüler, bu işlevselliği sağlayabilir.

### <a name="preserve-object-references-and-handle-loops"></a>Nesne başvurularını koruma ve döngüleri işleme

Varsayılan olarak, `Newtonsoft.Json` değere göre seri hale getirir. Örneğin, bir nesne aynı `Person` nesnesine bir başvuru içeren iki özellik içeriyorsa, bu `Person` nesnesinin özelliklerinin değerleri JSON içinde yinelenir.

`Newtonsoft.Json`, başvuruya göre serileştirmenize olanak tanıyan `JsonSerializerSettings` `PreserveReferencesHandling` bir ayara sahiptir:

* İlk `Person` nesnesi için oluşturulan JSON 'a tanımlayıcı meta verileri eklenir.
* İkinci `Person` nesnesi için oluşturulan JSON, özellik değerleri yerine bu tanımlayıcıya bir başvuru içerir.

Ayrıca `Newtonsoft.Json` bir özel durum oluşturmak yerine döngüsel başvuruları yoksaymanıza imkan tanıyan bir `ReferenceLoopHandling` ayarı da vardır.

<xref:System.Text.Json> yalnızca değere göre Serileştirmeyi destekler ve döngüsel başvurular için bir özel durum oluşturur.

### <a name="systemruntimeserialization-attributes"></a>System. Runtime. Serialization öznitelikleri

<xref:System.Text.Json>, `DataMemberAttribute` ve `IgnoreDataMemberAttribute`gibi `System.Runtime.Serialization` ad alanındaki öznitelikleri desteklemez.

### <a name="octal-numbers"></a>Sekizlik sayılar

`Newtonsoft.Json` sayı, sekizli sayı olarak önünde sıfır ile davranır. [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi bunlara izin vermediğinden <xref:System.Text.Json> baştaki sıfıra izin vermez.

### <a name="populate-existing-objects"></a>Mevcut nesneleri doldur

' Deki `JsonConvert.PopulateObject` yöntemi, yeni bir örnek oluşturmak yerine bir JSON belgesini bir sınıfın var olan bir örneğine seri hale getirir `Newtonsoft.Json`. <xref:System.Text.Json> her zaman varsayılan genel parametresiz oluşturucuyu kullanarak hedef türün yeni bir örneğini oluşturur. Özel dönüştürücüler, var olan bir örneğe serisini kaldıramıyor.

### <a name="reuse-rather-than-replace-properties"></a>Özellikleri değiştirmek yerine yeniden kullan

`Newtonsoft.Json` `ObjectCreationHandling` ayarı, özellikleri içindeki nesnelerin seri durumundan çıkarma sırasında yerine kullanılması gerektiğini belirtmenize olanak tanır. <xref:System.Text.Json> her zaman özelliklerde nesneleri değiştirir.  Özel dönüştürücüler, bu işlevselliği sağlayabilir.

### <a name="add-to-collections-without-setters"></a>Ayarlayıcısız koleksiyonlara Ekle

Seri durumundan çıkarma sırasında `Newtonsoft.Json`, özelliğin ayarlayıcısı olmasa bile nesneleri bir koleksiyona ekler. <xref:System.Text.Json>, ayarlayıcıları olmayan özellikleri yoksayar. Özel dönüştürücüler, bu işlevselliği sağlayabilir.

### <a name="missingmemberhandling"></a>MissingMemberHandling

`Newtonsoft.Json`, JSON, hedef türünde eksik olan özellikler içeriyorsa, seri durumdan çıkarma sırasında özel durumlar atmak üzere yapılandırılabilir. <xref:System.Text.Json>, [[Jsonextensiondata] özniteliğini](system-text-json-how-to.md#handle-overflow-json)kullandığınız durumlar dışında, JSON 'daki ek özellikleri yoksayar. Eksik üye özelliği için geçici çözüm yoktur.

### <a name="tracewriter"></a>TraceWriter

`Newtonsoft.Json`, serileştirme veya serisini kaldırma tarafından oluşturulan günlükleri görüntülemek için `TraceWriter` kullanarak hata ayıklamanıza olanak tanır. <xref:System.Text.Json> günlüğe kaydetme yapmaz.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JToken (JObject, JArray gibi) ile karşılaştırılan JsonDocument ve JsonElement

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>, var olan JSON yüklerden **salt okunurdur** bir belge nesne MODELI (DOM) ayrıştırabilme ve derleme olanağı sağlar. DOM, bir JSON yükünde verilere rastgele erişim sağlar. Yükü oluşturan JSON öğelerine <xref:System.Text.Json.JsonElement> türü aracılığıyla erişilebilir. `JsonElement` türü, JSON metnini ortak .NET türlerine dönüştürmek için API 'Ler sağlar. `JsonDocument`, bir <xref:System.Text.Json.JsonDocument.RootElement> özelliğini kullanıma sunar.

### <a name="jsondocument-is-idisposable"></a>JsonDocument, IDisposable

`JsonDocument`, toplanan arabellekte verilerin bellek içi bir görünümünü oluşturur. Bu nedenle, `Newtonsoft.Json``JObject` veya `JArray` aksine, `JsonDocument` türü `IDisposable` uygular ve bir using bloğu içinde kullanılması gerekir. 

Yalnızca yaşam süresi sahipliğini aktarmak ve arayana atmak istiyorsanız API 'nizden bir `JsonDocument` döndürün. Çoğu senaryoda, bu gerekli değildir. Çağıranın tüm JSON belgesiyle çalışması gerekiyorsa, bir <xref:System.Text.Json.JsonElement><xref:System.Text.Json.JsonDocument.RootElement%2A><xref:System.Text.Json.JsonElement.Clone%2A> döndürün. Çağıranın JSON belgesi içinde belirli bir öğeyle çalışması gerekiyorsa, bu <xref:System.Text.Json.JsonElement><xref:System.Text.Json.JsonElement.Clone%2A> döndürün. Bir `Clone`oluşturmadan doğrudan `RootElement` veya alt öğe döndürdüğünüzde, çağıran `JsonElement`, bu, ona sahip olan `JsonDocument` atıldıktan sonra, döndürülen erişemez.

İşte `Clone`yapmanızı gerektiren bir örnek:

```csharp
public JsonElement LookAndLoad(JsonElement source)
{
    string json = File.ReadAllText(source.GetProperty("fileName").GetString());
   
    using (JsonDocument doc = JsonDocument.Parse(json))
    {
        return doc.RootElement.Clone();
    }
}
```

Yukarıdaki kod, `fileName` özelliği içeren bir `JsonElement` bekler. JSON dosyasını açar ve bir `JsonDocument`oluşturur. Yöntemi, çağıranın tüm belgeyle çalışmak istediğini varsayar, bu nedenle `RootElement``Clone` döndürür. 

Bir `JsonElement` alırsanız ve bir alt öğe döndürüyorsa, alt öğenin bir `Clone` döndürülmesi gerekli değildir. Çağıranın, geçirilen `JsonElement` ait olduğu `JsonDocument` canlı tutulmasından sorumludur. Örneğin:

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument salt okunurdur

<xref:System.Text.Json> DOM, JSON öğelerini ekleyemez, kaldıramaz veya değiştiremez. Bu, performans için bu şekilde tasarlanmıştır ve ortak JSON yük boyutlarını (yani, < 1 MB) ayrıştırmak için ayırmaları azaltır. Senaryonuz Şu anda değiştirilebilir bir DOM kullanıyorsa, aşağıdaki geçici çözümlerden biri uygulanabilir olabilir:

* Sıfırdan bir `JsonDocument` oluşturmak için (yani, var olan bir JSON yükünü `Parse` yöntemine geçirmeden), `Utf8JsonWriter` kullanarak JSON metnini yazın ve yeni bir `JsonDocument`oluşturmak için bu çıktıyı ayrıştırın.
* Var olan bir `JsonDocument`değiştirmek için, JSON metni yazmak, yazarken değişiklikler yapmak ve yeni bir `JsonDocument`oluşturmak için bu çıkışı ayrıştırmak üzere kullanın.
* Var olan JSON belgelerini `Newtonsoft.Json``JObject.Merge` veya `JContainer.Merge` API 'Lerine eşit olarak birleştirmek için [Bu GitHub sorununa](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853)bakın.

### <a name="jsonelement-is-a-union-struct"></a>JsonElement bir UNION yapısı

`JsonDocument`, bir UNION, herhangi bir JSON öğesini kapsayan yapı türü olan <xref:System.Text.Json.JsonElement>türünde bir özellik olarak `RootElement` sunar. `Newtonsoft.Json`, `JObject`,`JArray`, `JToken`gibi özel sıradüzenli türler kullanır. `JsonElement`, üzerinde arama ve listeleme yapabileceklerdir ve `JsonElement` kullanarak JSON öğelerini .NET türlerine çalıştırabilirsiniz.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Bir JsonDocument ve JsonElement öğelerini alt öğeler için arama

`JObject` veya `JArray` kullanarak JSON belirteçlerini aramak, bazı sözlükte arama yapıldığından nispeten hızlı bir şekilde `Newtonsoft.Json` eğilimindedir. Karşılaştırmayla, `JsonElement` aramalar özellikler için sıralı bir arama gerektirir ve bu nedenle nispeten yavaş olur (örneğin, `TryGetProperty`kullanılırken). <xref:System.Text.Json>, arama süresi yerine ilk ayrıştırma süresini en aza indirmek için tasarlanmıştır. Bu nedenle, bir `JsonDocument` nesnesinde arama yaparken performansı iyileştirmek için aşağıdaki yaklaşımları kullanın:

* Kendi dizin oluşturma veya döngülerinizi yapmak yerine yerleşik numaralandırıcıları (<xref:System.Text.Json.JsonElement.EnumerateArray%2A> ve <xref:System.Text.Json.JsonElement.EnumerateObject%2A>) kullanın.
* Tüm `JsonDocument` `RootElement`kullanarak her özellik için sıralı arama yapmayın. Bunun yerine, JSON verilerinin bilinen yapısına bağlı olarak iç içe geçmiş JSON nesnelerinde arama yapın. Örneğin, `Student` nesnelerinde `Grade` bir özelliği arıyorsanız `Student` nesneleri aracılığıyla ilerleyin ve `JsonElement` özellikleri arayan tüm `Grade` nesneleri arasında arama yapmak yerine her biri için `Grade` değerini alın. İkincisini yapmak, aynı verilerin üzerinde gereksiz bir şekilde geçiş oluşmasına neden olur.

Kod örneği için bkz. [veri erişimi Için JsonDocument kullanma](system-text-json-how-to.md#use-jsondocument-for-access-to-data).

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader, JsonTextReader ile karşılaştırılır

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName> UTF-8 kodlu JSON metnine yönelik yüksek performanslı, düşük bir ayırma, salt ileri bir okuyucudur, [Readonlyspan\<byte >](xref:System.ReadOnlySpan%601) veya [readonlysequence\<byte >](xref:System.Buffers.ReadOnlySequence%601). `Utf8JsonReader`, özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür.

Aşağıdaki bölümlerde `Utf8JsonReader`kullanımı için önerilen programlama düzenleri açıklanmaktadır.

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader bir başvuru yapısı

`Utf8JsonReader` türü bir *başvuru yapısı*olduğundan, [belirli sınırlamalar](../../csharp/language-reference/keywords/ref.md#ref-struct-types)vardır. Örneğin, bir sınıf veya yapı üzerinde bir başvuru yapısı dışında bir alan olarak depolanamaz. Yüksek performans elde etmek için, bu tür bir `ref struct` olması gerekir, çünkü bu, kendisini bir ref yapısı olan [Readonlyspan\<byte >](xref:System.ReadOnlySpan%601)önbelleğe almalıdır. Ayrıca, bu tür durum taşıdığı için değişebilir olur. Bu nedenle, bunu değere göre değil **ref 'e geçirin** . Değere göre geçirmek bir yapı kopyasının oluşmasına neden olur ve durum değişiklikleri arayan tarafından görülemez. `Newtonsoft.Json` `JsonTextReader` bir sınıf olduğundan bu `Newtonsoft.Json` farklıdır. Başvuru yapılarını kullanma hakkında daha fazla bilgi için bkz. [yazma güvenli ve C# verimli kod](../../csharp/write-safe-efficient-code.md).

### <a name="read-utf-8-text"></a>UTF-8 metnini oku

`Utf8JsonReader`kullanırken mümkün olan en iyi performansı elde etmek için, UTF-16 dizeleri yerine UTF-8 ile kodlanmış JSON yüklerini okuyun. Kod örneği için bkz. [Utf8JsonReader kullanarak filtre verileri](system-text-json-how-to.md#filter-data-using-utf8jsonreader).

### <a name="read-with-a-stream-or-pipereader"></a>Stream veya Pıpereader ile okuma

`Utf8JsonReader`, UTF-8 kodlamalı [Readonlyspan\<byte >](xref:System.ReadOnlySpan%601) veya [readonlysequence\<byte >](xref:System.Buffers.ReadOnlySequence%601) (bir <xref:System.IO.Pipelines.PipeReader>okuma sonucu olan) okumayı destekler.

Zaman uyumlu okuma için, akışın sonuna kadar bir bayt dizisine kadar JSON yükünü okuyabilir ve bunu okuyucuya geçirebilirsiniz. Dizeden okuma (UTF-16 olarak kodlanmış) için, <xref:System.Text.Encoding.UTF8>çağırın.<xref:System.Text.Encoding.GetBytes%2A> İlk olarak dizeyi bir UTF-8 kodlu bayt dizisine dönüştürme. Sonra bu `Utf8JsonReader`geçirin. 

`Utf8JsonReader` girişin JSON metni olduğunu düşündüğü için UTF-8 bayt sırası işareti (BOM) geçersiz JSON olarak kabul edilir. Çağıranın verileri okuyucuya geçirmeden önce onu filtrelemeniz gerekir.

Kod örnekleri için bkz. [Use Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).

### <a name="read-with-multi-segment-readonlysequence"></a>Çok kesimli ReadOnlySequence ile oku

JSON girişi bir [Readonlyspan\<byte >](xref:System.ReadOnlySpan%601), okuma döngüsüne GITTIĞINIZDE her JSON öğesine okuyucudaki `ValueSpan` özelliğinden erişilebilir. Ancak, giriş bir [Readonlysequence\<bayt >](xref:System.Buffers.ReadOnlySequence%601) (bir <xref:System.IO.Pipelines.PipeReader>okuma sonucu) ise, bazı JSON öğeleri `ReadOnlySequence<byte>` nesnesinin birden çok segmentine Straddle. Bu öğelere, ardışık bellek bloğundaki <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> erişilemez. Bunun yerine, giriş olarak çok bölgeli `ReadOnlySequence<byte>` her seferinde, geçerli JSON öğesine nasıl erişebileceğinizi anlamak için okuyucudaki <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> özelliğini yoklayın. Önerilen bir model aşağıda verilmiştir:

```csharp
while (reader.Read())
{
    switch (reader.TokenType)
    {
        // ...
        ReadOnlySpan<byte> jsonElement = reader.HasValueSequence ?
            reader.ValueSequence.ToArray() :
            reader.ValueSpan;
        // ...
    }
}
```

### <a name="use-valuetextequals-for-property-name-lookups"></a>Özellik adı aramaları için ValueTextEquals kullanın

Özellik adı aramaları için <xref:System.MemoryExtensions.SequenceEqual%2A> çağırarak bayt başına karşılaştırmalar yapmak için <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> kullanmayın. Bunun yerine <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> çağırın, çünkü bu yöntem JSON içinde Atlanan tüm karakterleri kaldırır. "Ad" adlı bir özelliğin nasıl aranacağını gösteren bir örnek aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>Null değerleri null yapılabilir değer türlerine oku

`Newtonsoft.Json`, `ReadAsBoolean`gibi <xref:System.Nullable%601>döndüren API 'Ler sağlar. Bu, `TokenType` döndürerek bir `Null` `bool?`işler. Yerleşik `System.Text.Json` API 'Leri yalnızca null yapılamayan değer türleri döndürüyor. Örneğin, <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> `bool`döndürür. JSON içinde `Null` bulduğunda bir özel durum oluşturur. Aşağıdaki örneklerde, bir tane null yapılabilir değer türü döndürerek ve bir tane varsayılan değeri döndürerek, null değerlerini işlemek için iki yol gösterilmektedir:

```csharp
public bool? ReadAsNullableBoolean()
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return null;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

```csharp
public bool ReadAsBoolean(bool defaultValue)
{
    _reader.Read();
    if (_reader.TokenType == JsonTokenType.Null)
    {
        return defaultValue;
    }
    if (_reader.TokenType != JsonTokenType.True && _reader.TokenType != JsonTokenType.False)
    {
        throw new JsonException();
    }
    return _reader.GetBoolean();
}
```

### <a name="multi-targeting"></a>Çoklu hedefleme

Belirli hedef çerçeveler için `Newtonsoft.Json` kullanmaya devam etmeniz gerekiyorsa, çok hedefleyebilir ve iki uygulamanız vardır. Ancak, bu önemsiz değildir ve bazı `#ifdefs` ve kaynak yinelemesi gerektirir. Mümkün olduğunca çok kodu paylaşmanın bir yolu, `Utf8JsonReader` ve `Newtonsoft.Json` `JsonTextReader`etrafında `ref struct` sarmalayıcı oluşturmaktır. Bu sarmalayıcı, davranış farklarını yalıtma sırasında genel yüzey alanını birleştirecektir. Bu, değişiklikleri öncelikle tür oluşturma ile birlikte ayırmanızı sağlar ve yeni türü başvuruya göre geçirerek. Bu, [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) kitaplığı 'nın izlediği düzendir:

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter, JsonTextWriter ile karşılaştırılır

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>, `String`, `Int32`ve `DateTime`gibi ortak .NET türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur. Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür.

Aşağıdaki bölümlerde `Utf8JsonWriter`kullanımı için önerilen programlama düzenleri açıklanmaktadır.

### <a name="write-with-utf-8-text"></a>UTF-8 metniyle yazma

`Utf8JsonWriter`kullanırken mümkün olan en iyi performansı elde etmek için, UTF-16 dizeleri yerine zaten UTF-8 ile kodlanmış JSON yüklerini yazın. Bilinen dize özellik adlarını ve değerlerini eskime olarak önbelleğe almak ve önceden kodlamak için <xref:System.Text.Json.JsonEncodedText> kullanın ve UTF-16 dize sabit değerleri kullanmak yerine yazıcıya geçirin. Bu, önbelleğe alma ve UTF-8 bayt dizilerini kullanmayla daha hızlıdır.

Özel kaçış yapmanız gerekiyorsa bu yaklaşım da geçerlidir. `System.Text.Json` dize yazarken kaçış özelliğini devre dışı bırakmanızı sağlar. Ancak, kendi özel <xref:System.Text.Encodings.Web.JavaScriptEncoder> yazıcıya bir seçenek olarak geçirebilir veya kaçış yapmak için `JavascriptEncoder` kullanan kendi `JsonEncodedText` oluşturabilir ve sonra dize yerine `JsonEncodedText` yazabilirsiniz. Daha fazla bilgi için bkz. [karakter kodlamasını özelleştirme](system-text-json-how-to.md#customize-character-encoding).

### <a name="write-raw-values"></a>Ham değerleri yaz

`Newtonsoft.Json` `WriteRawValue` yöntemi, bir değerin beklenildiği ham JSON yazar. <xref:System.Text.Json> doğrudan eşdeğerini yoktur, ancak şu şekilde yalnızca geçerli JSON yazılmasını sağlayan bir geçici çözüm verilmiştir:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Karakter kaçış 'yi özelleştirme

`JsonTextWriter` [Stringescapehandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) AYARı, ASCII olmayan tüm karakterlerin **veya** HTML karakterlerinin kaçış seçeneklerini sunar. Varsayılan olarak, `Utf8JsonWriter` ASCII olmayan **ve** HTML karakterlerinin tümünü çıkar. Bu kaçış, derinlemesine savunma güvenlik nedenleriyle yapılır. Farklı bir kaçış ilkesi belirtmek için bir <xref:System.Text.Encodings.Web.JavaScriptEncoder> oluşturun ve <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>ayarlayın. Daha fazla bilgi için bkz. [karakter kodlamasını özelleştirme](system-text-json-how-to.md#customize-character-encoding).

### <a name="customize-json-format"></a>JSON biçimini Özelleştir

`JsonTextWriter`, `Utf8JsonWriter` eşdeğeri olmayan aşağıdaki ayarları içerir:

* [Girintileme](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) -girintilemek için kaç karakter kullanılacağını belirtir. `Utf8JsonWriter` her zaman 2 karakterlik girintileme yapar.
* [Inztchar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) -girintileme için kullanılacak karakteri belirtir.  `Utf8JsonWriter` her zaman boşluk kullanır.
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) -dize değerlerini çevrelemek için kullanılacak karakteri belirtir.  `Utf8JsonWriter` her zaman çift tırnak kullanır.
* [QUOTENAME](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) -özellik adlarının tırnak işaretleriyle saranıp çevrelenmeyeceğini belirtir.  `Utf8JsonWriter` her zaman tırnak işaretleriyle çevreler.

Bu yollarla `Utf8JsonWriter` tarafından üretilen JSON 'ı özelleştirmenizi sağlayan geçici çözümler yoktur.

### <a name="write-null-values"></a>Null değerleri yaz

`Utf8JsonWriter`kullanarak null değerler yazmak için şunu çağırın:

* değer olarak null ile bir anahtar-değer çifti yazmak <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A>.
* JSON dizisinin bir öğesi olarak null yazmak <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A>.

Dize özelliği için, dize null ise, <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> ve <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> `WriteNull` ve `WriteNullValue`eşdeğerdir.

### <a name="write-timespan-uri-or-char-values"></a>TimeSpan, Uri veya Char değerlerini yaz

`JsonTextWriter` [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm), [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)ve [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) değerleri için `WriteValue` yöntemler sağlar. `Utf8JsonWriter` eşdeğer yöntemlere sahip değildir. Bunun yerine, bu değerleri dizeler olarak biçimlendirin (örneğin `ToString()`çağırarak) ve <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>çağırın.

### <a name="multi-targeting"></a>Çoklu hedefleme

Belirli hedef çerçeveler için `Newtonsoft.Json` kullanmaya devam etmeniz gerekiyorsa, çok hedefleyebilir ve iki uygulamanız vardır. Ancak, bu önemsiz değildir ve bazı `#ifdefs` ve kaynak yinelemesi gerektirir. Mümkün olduğunca çok kodu paylaşmanın bir yolu, `Utf8JsonWriter` ve `JsonTextWriter``Newtonsoft` etrafında bir sarmalayıcı oluşturmaktır. Bu sarmalayıcı, davranış farklarını yalıtma sırasında genel yüzey alanını birleştirecektir. Bu, değişiklikleri genellikle türün yapılacağı şekilde yalıtmanızı sağlar. [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) kitaplığı aşağıdaki gibidir:

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>Ek kaynaklar

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System. Text. JSON genel bakış](system-text-json-overview.md)
* [System. Text. JSON kullanma](system-text-json-how-to.md)
* [Özel dönüştürücüler yazma](system-text-json-converters-how-to.md)
* [System. Text. JSON içinde DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md)
* [System. Text. JSON API başvurusu](xref:System.Text.Json)
* [System. Text. JSON. Serialization API başvurusu](xref:System.Text.Json.Serialization)
