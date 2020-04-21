---
title: Geçiş - Newtonsoft.Json System.Text.Json .NET
author: tdykstra
ms.author: tdykstra
no-loc:
- System.Text.Json
- Newtonsoft.Json
ms.date: 01/10/2020
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 0828a5654171df39230055215903d3a49690155d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739247"
---
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Newtonsoft.Json'dan System.Text.Json'a nasıl göç edilir?

Bu makalede [Newtonsoft.Json'dan](https://www.newtonsoft.com/json) .'a <xref:System.Text.Json>nasıl göç edileliştirilir gösterilmektedir.

Ad `System.Text.Json` alanı, JavaScript Object Notation'a (JSON) seri leştirme ve deserializing için işlevsellik sağlar. Kitaplık `System.Text.Json` [.NET Core 3.0](https://aka.ms/netcore3download) paylaşılan çerçevesine dahildir. Diğer hedef çerçeveler için [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yükleyin. Paket destekler:

* .NET Standart 2.0 ve sonraki sürümler
* .NET Framework 4.7.2 ve sonraki sürümler
* .NET Çekirdek 2.0, 2.1 ve 2.2

`System.Text.Json`performans, güvenlik ve standartlara uyum adabına odaklanır. Varsayılan davranışta bazı önemli farklılıklar vardır ve `Newtonsoft.Json`'ile özellik paritesi olmasını amaçlamaz. Bazı senaryolar `System.Text.Json` için yerleşik işlevselliği yoktur, ancak önerilen geçici çözüm vardır. Diğer senaryolar için geçici çözüm kullanışsızdır. Uygulamanız eksik bir özelliğe bağlıysa, senaryonuz için destek ekilip eklenmeyeceğini öğrenmek için [bir sorun dosyalamayı](https://github.com/dotnet/runtime/issues/new) düşünün.

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

Bu makalenin <xref:System.Text.Json.JsonSerializer> çoğu API'nin nasıl kullanılacağı yla ilgilidir, ancak <xref:System.Text.Json.JsonDocument> (Belge Nesnesi Modeli veya <xref:System.Text.Json.Utf8JsonReader>DOM'u temsil eden) ve <xref:System.Text.Json.Utf8JsonWriter> türleri nasıl kullanılacağına ilişkin yönergeler de içerir.

## <a name="table-of-differences-between-newtonsoftjson-and-systemtextjson"></a>Newtonsoft.Json ve System.Text.Json arasındaki farklar tablosu

Aşağıdaki tabloda `Newtonsoft.Json` özellikleri `System.Text.Json` ve eşdeğerleri listeledir. Eşdeğerleri aşağıdaki kategorilere girer:

* Yerleşik işlevsellik tarafından desteklenir. Benzer davranış `System.Text.Json` almak bir öznitelik veya genel seçeneğin kullanımını gerektirebilir.
* Desteklenmez, geçici çözüm mümkündür. Geçici çözüm, `Newtonsoft.Json` işlevsellikle tam bir eşlik sağlamayan özel [dönüştürücülerdir.](system-text-json-converters-how-to.md) Bunlardan bazıları için örnek kod örnek olarak sağlanır. Bu `Newtonsoft.Json` özelliklere güveniyorsanız, geçiş .NET nesne modellerinizde veya diğer kod değişikliklerinde değişiklik yapılmasını gerektirir.
* Desteklenmez, geçici çözüm pratik veya mümkün değildir. Bu `Newtonsoft.Json` özelliklere güveniyorsanız, önemli değişiklikler olmadan geçiş mümkün olmayacaktır.

| Newtonsoft.Json özelliği                               | System.Text.Json eşdeğeri |
|-------------------------------------------------------|-----------------------------|
| Varsayılan olarak büyük/küçük harf duyarlı deserialization           | ✔️ [PropertyNameCaseHassas küresel ayar](#case-insensitive-deserialization) |
| Deve kasa özellik adları                             | ✔️ [PropertyNamingPolicy genel ayarı](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| Minimum karakter kaçış                            | ✔️ [Sıkı karakter kaçan, yapılandırılabilir](#minimal-character-escaping) |
| `NullValueHandling.Ignore`küresel ayar             | ✔️ [IgnoreNullValues genel seçeneği](system-text-json-how-to.md#exclude-all-null-value-properties) |
| Yorumlara izin ver                                        | ✔️ [ReadCommentIşleme global ayarı](#comments) |
| İzleyen virgüle izin ver                                 | ✔️ [AllowTrailingCommas küresel ayarı](#trailing-commas) |
| Özel dönüştürücü kaydı                         | ✔️ [Öncelik Sırası farklıdır](#converter-registration-precedence) |
| Varsayılan olarak maksimum derinlik yok                           | ✔️ [Varsayılan maksimum derinlik 64, yapılandırılabilir](#maximum-depth) |
| Çok çeşitli türler için destek                    | ⚠️[Bazı türler özel dönüştürücüler gerektirir](#types-without-built-in-support) |
| Dizeleri sayı olarak deserialize                        | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#quoted-numbers) |
| Dize `Dictionary` olmayan anahtarla deserialize          | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#dictionary-with-non-string-key) |
| Polimorfik serileştirme                             | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#polymorphic-serialization) |
| Polimorfik deserialization                           | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#polymorphic-deserialization) |
| Çıkarılan türü `object` özelliklerine deserialize etme      | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#deserialization-of-object-properties) |
| JSON'u `null` gerçek olarak nullable olmayan değer türlerine deserialize etme | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#deserialize-null-to-non-nullable-type) |
| Değişmez sınıflara ve structs deserialize          | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#deserialize-to-immutable-classes-and-structs) |
| `[JsonConstructor]` özniteliği                         | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#specify-constructor-to-use) |
| `Required`öznitelik `[JsonProperty]` üzerinde ayarlama        | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#required-properties) |
| `NullValueHandling`öznitelik `[JsonProperty]` üzerinde ayarlama | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`öznitelik `[JsonProperty]` üzerinde ayarlama | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`küresel ayar                 | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#conditionally-ignore-a-property) |
| `DefaultContractResolver`özellikleri hariç tutmak için       | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`, `DateFormatString` ayarlar   | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#specify-date-format) |
| Geri Çağırmalar                                             | ⚠️[Desteklenmiyor, geçici çözüm, örnek](#callbacks) |
| Kamusal ve genel olmayan alanlara destek              | ⚠️[Desteklenmiyor, geçici çözüm](#public-and-non-public-fields) |
| Dahili ve özel mülkiyet ayarlayıcıları ve getters için destek | ⚠️[Desteklenmiyor, geçici çözüm](#internal-and-private-property-setters-and-getters) |
| `JsonConvert.PopulateObject` yöntemi                   | ⚠️[Desteklenmiyor, geçici çözüm](#populate-existing-objects) |
| `ObjectCreationHandling`küresel ayar               | ⚠️[Desteklenmiyor, geçici çözüm](#reuse-rather-than-replace-properties) |
| Ayarlayıcılar olmadan koleksiyonlara ekleme                    | ⚠️[Desteklenmiyor, geçici çözüm](#add-to-collections-without-setters) |
| `PreserveReferencesHandling`küresel ayar           | ❌[Desteklenmiyor](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling`küresel ayar                | ❌[Desteklenmiyor](#preserve-object-references-and-handle-loops) |
| Öznitelikler `System.Runtime.Serialization` için destek | ❌[Desteklenmiyor](#systemruntimeserialization-attributes) |
| `MissingMemberHandling`küresel ayar                | ❌[Desteklenmiyor](#missingmemberhandling) |
| Tırnak işaretleri olmadan özellik adlarını izin verme                   | ❌[Desteklenmiyor](#json-strings-property-names-and-string-values) |
| Dize değerleri etrafında tek tırnak izin ver              | ❌[Desteklenmiyor](#json-strings-property-names-and-string-values) |
| Dize özellikleri için dize dışı JSON değerlerine izin ver    | ❌[Desteklenmiyor](#non-string-values-for-string-properties) |

Bu `Newtonsoft.Json` özelliklerin ayrıntılı bir listesi değildir. Liste, [GitHub sorunları](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) veya [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) gönderilerinde istenen senaryoların çoğunu içerir. Burada listelenen ve şu anda örnek kodu olmayan senaryolardan biri için geçici çözüm uygularsanız ve çözümünüzü paylaşmak istiyorsanız, bu sayfanın altındaki **Geri Bildirim** **bölümündebu sayfayı** seçin. Bu, bu dokümantasyonun GitHub reposunda bir sorun oluşturur ve bu sayfadaki **Geri Bildirim** bölümünde de listeler.

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Newtonsoft.Json ile karşılaştırıldığında varsayılan JsonSerializer davranış farklılıkları

<xref:System.Text.Json>varsayılan olarak katıdır ve deterministik davranışı vurgulayarak, arayan adına herhangi bir tahmin veya yorum yapmaktan kaçınır. Kitaplık, performans ve güvenlik için kasıtlı olarak bu şekilde tasarlanmıştır. `Newtonsoft.Json`varsayılan olarak esnektir. Tasarımdaki bu temel fark, varsayılan davranıştaki aşağıdaki belirli farklılıkların çoğunun arkasındadır.

### <a name="case-insensitive-deserialization"></a>Büyük/küçük harf duyarsız deserialization

Deserialization sırasında, `Newtonsoft.Json` varsayılan olarak büyük/küçük harf duyarsız özellik adı eşleştirme yapar. Varsayılan <xref:System.Text.Json> değer, tam bir eşleşme yaptığı için daha iyi performans sağlayan büyük/küçük harf duyarlıdır. Büyük/küçük harf duyarsız eşleştirmenin nasıl yapılacağı hakkinda bilgi için [bkz.](system-text-json-how-to.md#case-insensitive-property-matching)

ASP.NET Core'u `System.Text.Json` kullanarak dolaylı olarak kullanıyorsanız, '' gibi `Newtonsoft.Json`davranışlar elde etmek için hiçbir şey yapmanız gerekmez. ASP.NET Core, [deve kasa özelliği adları](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) ve büyük/küçük harf duyarsız `System.Text.Json`eşleşmesi için ayarları kullanır.

### <a name="minimal-character-escaping"></a>Minimum karakter kaçış

Serileştirme sırasında, `Newtonsoft.Json` karakterlerden kaçmadan geçmelerine izin verme konusunda nispeten müsamahakardır. Diğer bir yerde, karakterin kod `\uxxxx` `xxxx` noktası nerede onları değiştirmez. Onlardan kaçtığı yerde, bunu karakterden önce `\` bir karakter yayan `"` `\"`(örneğin, olur) yayarak yapar. <xref:System.Text.Json>siteleri arası komut dosyası (XSS) veya bilgi açıklama saldırılarına karşı derinlemesine koruma sağlamak için varsayılan olarak daha fazla karakterden kaçar ve bunu altı karakterli sırayı kullanarak yapar. `System.Text.Json`varsayılan olarak TÜM ASCII olmayan karakterlerden kaçar, bu nedenle 'de kullanıyorsanız `StringEscapeHandling.EscapeNonAscii` `Newtonsoft.Json`hiçbir şey yapmanız gerekmez. `System.Text.Json`ayrıca varsayılan olarak HTML'ye duyarlı karakterlerden de kaçar. Varsayılan `System.Text.Json` davranışı niçin geçersiz kacağınız hakkında bilgi için [bkz.](system-text-json-how-to.md#customize-character-encoding)

### <a name="comments"></a>Yorumlar

Deserialization sırasında, `Newtonsoft.Json` varsayılan olarak JSON yorumyoklar. <xref:System.Text.Json> [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi bunları içermedığından, varsayılan olarak açıklamalar için özel durumlar atmaktır. Yorumlara nasıl izin verilebilen bilgiler için [bkz.](system-text-json-how-to.md#allow-comments-and-trailing-commas)

### <a name="trailing-commas"></a>Sondaki virgüller

Deserialization sırasında, `Newtonsoft.Json` varsayılan olarak sondaki virgülleri yok sayar. Ayrıca, birden çok takip eden virgül `[{"Color":"Red"},{"Color":"Green"},,]`(örneğin, ) yokslar. <xref:System.Text.Json> [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi izin vermedığından, varsayılan olarak virgülleri takip etmek için özel durumlar atmaktır. Bunları nasıl `System.Text.Json` kabul edebilirsiniz hakkında bilgi için, [bkz.](system-text-json-how-to.md#allow-comments-and-trailing-commas) Birden fazla virgüle izin vermenin bir yolu yok.

### <a name="converter-registration-precedence"></a>Dönüştürücü kayıt önceliği

Özel `Newtonsoft.Json` dönüştürücüler için kayıt önceliği aşağıdaki gibidir:

* Özellik üzerinde öznitelik
* Türe bağlı öznitelik
* [Dönüştürücüler](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm) koleksiyonu

Bu sipariş, `Converters` koleksiyondaki özel bir dönüştürücünün, tür düzeyinde bir öznitelik uygulanarak kayıtlı bir dönüştürücü tarafından geçersiz kılındığı anlamına gelir. Bu kayıtların her ikisi de özellik düzeyinde bir öznitelik tarafından geçersiz kılınan.

Özel <xref:System.Text.Json> dönüştürücüler için kayıt önceliği farklıdır:

* Özellik üzerinde öznitelik
* <xref:System.Text.Json.JsonSerializerOptions.Converters>Koleksiyon
* Türe bağlı öznitelik

Buradaki fark, koleksiyondaki özel bir `Converters` dönüştürücünün tür düzeyindeki bir özniteliği geçersiz kışuyor olmasıdır. Bu öncelik sırasının arkasındaki amaç, çalışma zamanı değişikliklerinin tasarım zamanı seçimlerini geçersiz kılmasını sağlamaktır. Önceliği değiştirmenin bir yolu yok.

Özel dönüştürücü kaydı hakkında daha fazla bilgi için özel [bir dönüştürücü kaydedin.](system-text-json-converters-how-to.md#register-a-custom-converter)

### <a name="maximum-depth"></a>Maksimum derinlik

`Newtonsoft.Json`varsayılan olarak maksimum derinlik sınırı yoktur. Varsayılan <xref:System.Text.Json> 64 sınırı vardır ve ayarlayarak <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>yapılandırılabilir.

### <a name="json-strings-property-names-and-string-values"></a>JSON dizeleri (özellik adları ve dize değerleri)

Deserialization sırasında, `Newtonsoft.Json` çift tırnak, tek tırnak veya tırnak olmadan çevrili özellik adlarını kabul eder. Çift tırnak veya tek tırnak la çevrili dize değerlerini kabul eder. Örneğin, `Newtonsoft.Json` aşağıdaki JSON kabul eder:

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json`bu biçim [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi tarafından gerekli olduğundan ve geçerli JSON olarak kabul edilen tek biçim olduğundan, yalnızca çift tırnak halinde özellik adlarını ve dize değerlerini kabul eder.

Tek tırnak içinde eklenen bir değer aşağıdaki ileti ile bir [JsonException](xref:System.Text.Json.JsonException) sonuçlanır:

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Dize özellikleri için dize dışı değerler

`Newtonsoft.Json`bir sayı veya literals `true` gibi non-string değerleri `false`kabul eder ve , tür dize özelliklerine deserialization için. Aşağıda, aşağıdaki sınıfa başarıyla deserialize olan `Newtonsoft.Json` JSON örneği verilmiştir:

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

`System.Text.Json`dize olmayan değerleri dize özelliklerine deserialize etmez. Bir dize alanı için alınan dize olmayan değer, aşağıdaki iletiyle bir [JsonException](xref:System.Text.Json.JsonException) ile sonuçlanır:

```
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>Geçici çözüm gerektiren JsonSerializer kullanan senaryolar

Aşağıdaki senaryolar yerleşik işlevsellik tarafından desteklenmez, ancak geçici çözüm mümkündür. Geçici çözüm, `Newtonsoft.Json` işlevsellikle tam bir eşlik sağlamayan özel [dönüştürücülerdir.](system-text-json-converters-how-to.md) Bunlardan bazıları için örnek kod örnek olarak sağlanır. Bu `Newtonsoft.Json` özelliklere güveniyorsanız, geçiş .NET nesne modellerinizde veya diğer kod değişikliklerinde değişiklik yapılmasını gerektirir.

### <a name="types-without-built-in-support"></a>Yerleşik desteği olmayan türler

<xref:System.Text.Json>aşağıdaki türler için yerleşik destek sağlamaz:

* <xref:System.Data.DataTable>ve ilgili türleri
* [Ayrımcı birliş,](../../fsharp/language-reference/discriminated-unions.md)kayıt [türleri](../../fsharp/language-reference/records.md)ve [anonim kayıt türleri](../../fsharp/language-reference/anonymous-records.md)gibi F# türleri.
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple>ve ilişkili genel türleri

Yerleşik desteği olmayan türler için özel dönüştürücüler uygulanabilir.

### <a name="quoted-numbers"></a>Alıntı yapılan sayılar

`Newtonsoft.Json`JSON dizeleri (tırnak işaretleri ile çevrili) tarafından temsil edilen sayıları serihale veya deserialize edebilirsiniz. Örneğin, kabul edebilir: `{"DegreesCelsius":"23"}` yerine `{"DegreesCelsius":23}`. Bu davranışı etkinleştirmek için <xref:System.Text.Json>aşağıdaki örnekgibi özel bir dönüştürücü uygulayın. Dönüştürücü olarak `long`tanımlanan özellikleri işler:

* Onları JSON dizeleri olarak serihale getirsin.
* Deserializing sırasında tırnak içinde JSON numaraları ve numaraları kabul eder.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

Bu özel dönüştürücü, tek tek `long` özellikler üzerinde [bir öznitelik kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) veya <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyona [dönüştürücü ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) kaydolun.

### <a name="dictionary-with-non-string-key"></a>Dize olmayan anahtarlı sözlük

`Newtonsoft.Json`tür `Dictionary<TKey, TValue>`koleksiyonlarını destekler. Sözlük koleksiyonları <xref:System.Text.Json> için yerleşik destek `Dictionary<string, TValue>`. Yani, anahtar bir dize olmalıdır.

Bir tamsayı veya anahtar olarak başka bir tür ile bir sözlük desteklemek [için, özel dönüştürücüler yazmak için nasıl](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key)örnek gibi bir dönüştürücü oluşturun.

### <a name="polymorphic-serialization"></a>Polimorfik serileştirme

`Newtonsoft.Json`otomatik olarak polimorfik serileştirme yapar. Sınırlı polimorfik serileştirme yetenekleri hakkında <xref:System.Text.Json>bilgi için, [türemiş sınıfların Serialize özelliklerini](system-text-json-how-to.md#serialize-properties-of-derived-classes)görmek.

Burada açıklanan geçici çözüm türü `object`olarak türetilmiş sınıflar içerebilecek özellikleri tanımlamak içindir. Bu mümkün değilse, başka bir seçenek [özel dönüştürücüler yazmak için nasıl](system-text-json-converters-how-to.md#support-polymorphic-deserialization)örnek gibi tüm devralma türü hiyerarşisi için bir yöntem ile bir `Write` dönüştürücü oluşturmaktır.

### <a name="polymorphic-deserialization"></a>Polimorfik deserialization

`Newtonsoft.Json`serihale `TypeNameHandling` ederken JSON'a tür adı meta verileri ekleyen bir ayarı vardır. Polimorfik deserialization yapmak için deserializing sırasında meta verileri kullanır. <xref:System.Text.Json>[polimorfik serileştirme](system-text-json-how-to.md#serialize-properties-of-derived-classes) sınırlı bir aralık yapabilir, ancak polimorfik deserialization.

Polimorfik deserialization desteklemek [için, özel dönüştürücüler yazmak için nasıl](system-text-json-converters-how-to.md#support-polymorphic-deserialization)örnek gibi bir dönüştürücü oluşturun.

### <a name="deserialization-of-object-properties"></a>Nesne özelliklerinin deserialization

Deserialize `Newtonsoft.Json` <xref:System.Object>olduğunda, o:

* JSON yükündeki ilkel değerlerin türünü (diğer) `null`çıkartır ve depolanan `string` `long`, `double` `boolean`, `DateTime` , , veya kutulu bir nesne olarak döndürür. *İlkel değerler,* JSON numarası, dize, `true`, `false`, `null`veya .
* JSON `JObject` `JArray` yükündeki karmaşık değerler için bir veya başka bir şey verir. *Karmaşık değerler,* ayraçlar içindeki JSON anahtar değeri`{}`çiftleri () veya`[]`parantez içindeki değerlerin listeleridir. Ayraçlar veya paranteziçindeki özellikler ve değerler ek özelliklere veya değerlere sahip olabilir.
* Yük `null` JSON harfine sahip olduğunda null bir başvuru verir.

<xref:System.Text.Json>örneğin, hem `JsonElement` ilkel hem de karmaşık değerler için kutulanmış bir kutuyu depolar: <xref:System.Object>

* Bir `object` mülk.
* Sözlük `object` değeri.
* Bir `object` dizi değeri.
* Bir `object`kök.

Ancak, `System.Text.Json` aynı `null` davranır `Newtonsoft.Json` ve yük `null` içinde JSON edebi olduğunda null bir başvuru döndürür.

Özellikler için tür çıkarımını uygulamak için, `object` özel [dönüştürücüler yazma özelliğindeki](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties)örnek gibi bir dönüştürücü oluşturun.

### <a name="deserialize-null-to-non-nullable-type"></a>Null'dan null'a, nullable olmayan türe deserialize

`Newtonsoft.Json`aşağıdaki senaryoda bir özel durum atmaz:

* `NullValueHandling`olarak ayarlanır `Ignore`ve
* Deserialization sırasında, JSON nullable değer türü için null değeri içerir.

Aynı senaryoda, <xref:System.Text.Json> bir özel durum atar. (Karşılık gelen null <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>işleme ayarı.)

Hedef türüne sahipseniz, en iyi geçici çözüm söz konusu özelliği geçersiz `int` kılınabilir hale getirmektir (örneğin, `int?`değiştirin).

Başka bir geçici çözüm türü için bir dönüştürücü yapmaktır, türler için `DateTimeOffset` null değerleri işleyen aşağıdaki örnek gibi:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

Özellik üzerinde bir [öznitelik kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) veya <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyona [dönüştürücü ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) bu özel dönüştürücü kaydedin.

**Not:** Önceki dönüştürücü, varsayılan değerleri belirten `Newtonsoft.Json` POC'lar için olduğundan **farklı olarak null değerlerini işler.** Örneğin, aşağıdaki kodun hedef nesnenizi temsil diğini varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

Ve aşağıdaki JSON önceki dönüştürücü kullanılarak deserialized varsayalım:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Deserialization sonra, `Date` özellik 1/1/0001`default(DateTimeOffset)`( ), yani, oluşturucu ayarlanan değer üzerine yazılır. Aynı POCO ve JSON `Newtonsoft.Json` göz önüne alındığında, deserialization `Date` özelliği 1/1/2001 bırakacaktır.

### <a name="deserialize-to-immutable-classes-and-structs"></a>Değişmez sınıflara ve structs deserialize

`Newtonsoft.Json`parametreleri olan yapıcılar kullanabilirsiniz, çünkü değişmez sınıflar ve yapılar için deserialize olabilir. <xref:System.Text.Json>yalnızca kamu parametresi siz oluşturucuları destekler. Geçici çözüm olarak, özel bir dönüştürücüparametreleri olan bir oluşturucu çağırabilirsiniz.

Burada birden çok oluşturucu parametreleri ile değişmez bir yapı:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

Ve burada serihale ve bu yapıyı deserialize bir dönüştürücü:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

Bu özel dönüştürücü, [konvertörü](system-text-json-converters-how-to.md#registration-sample---converters-collection) koleksiyona ekleyerek kaydedin. <xref:System.Text.Json.JsonSerializerOptions.Converters>

Açık genel özellikleri işleyen benzer bir dönüştürücü örneği [için, anahtar değer çiftleri için yerleşik dönüştürücüye](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs)bakın.

### <a name="specify-constructor-to-use"></a>Kullanılacak yapıcıyı belirtin

Öznitelik, bir POCO'ya `Newtonsoft.Json` `[JsonConstructor]` deserializing yaparken hangi oluşturucuyu çağıracaklarını belirtmenizi sağlar. <xref:System.Text.Json>yalnızca parametresiz yapıcıları destekler. Geçici çözüm olarak, özel bir dönüştürücüde ihtiyacınız olan yapıyı arayabilirsiniz. [Değişmez sınıflara ve structs deserialize](#deserialize-to-immutable-classes-and-structs)için örneğe bakın.

### <a name="required-properties"></a>Gerekli özellikler

, `Newtonsoft.Json`bir özelliği öznitelik üzerinde `Required` `[JsonProperty]` ayarlayarak gerekli olduğunu belirtin. `Newtonsoft.Json`json'da gerektiği gibi işaretlenmiş bir özellik için değer alınmazsa bir özel durum oluşturur.

<xref:System.Text.Json>hedef türünün özelliklerinden biri için değer alınmazsa özel durum atmaz. Örneğin, bir `WeatherForecast` sınıfınız varsa:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Aşağıdaki JSON hatasız olarak deserialized:

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

JSON'da özellik yoksa `Date` deserialization'ın başarısız olmasını sağlamak için özel bir dönüştürücü uygulayın. Özellik deserialization tamamlandıktan sonra ayarlanmamışsa aşağıdaki örnek dönüştürücü kodu bir özel durum `Date` atar:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

BU özel dönüştürücü, [POCO sınıfında bir öznitelik kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) veya <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyona [dönüştürücü ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) kaydedin.

Bu deseni izlerseniz, özyinelemeli olarak ararken <xref:System.Text.Json.JsonSerializer.Serialize%2A> seçenekler nesnesinde <xref:System.Text.Json.JsonSerializer.Deserialize%2A>geçmeyin veya . Seçenekler nesnesi <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> koleksiyonu içerir. Özel dönüştürücü kendisine `Serialize` `Deserialize`çağırır veya içine geçirirseniz, yığın taşması özel durumuyla sonuçlanan sonsuz bir döngü oluşturur. Varsayılan seçenekler uygun değilse, ihtiyacınız olan ayarlarla seçeneklerin yeni bir örneğini oluşturun. Her yeni örnek bağımsız olarak önbelleğe geldiğinden bu yaklaşım yavaş olacaktır.

Önceki dönüştürücü kodu basitleştirilmiş bir örnektir. Öznitelikleri [([JsonIgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) veya farklı seçenekler (özel kodlayıcılar gibi) işlemeniz gerekiyorsa ek mantık gerekir. Ayrıca, örnek kod, oluşturucuda varsayılan değer ayarlanan özellikleri işlemez. Ve bu yaklaşım aşağıdaki senaryolar arasında ayrım yapmaz:

* JSON'da bir mülk kayıp.
* Boşolmayan bir tür için bir özellik JSON'da bulunur, ancak değer bir `int`. için sıfır gibi tür için varsayılan değerdir.
* Geçersiz bir değer türü için bir özellik JSON'da bulunur, ancak değer null'dur.

### <a name="conditionally-ignore-a-property"></a>Bir özelliği koşullu olarak yoksay

`Newtonsoft.Json`bir özelliği koşullu olarak serileştirme veya deserialization'da yoksaymanın çeşitli yolları vardır:

* `DefaultContractResolver`rasgele ölçütlere göre eklenecek veya hariç olacak özellikleri seçmenize olanak tanır.
* Üzerindeki `NullValueHandling` `JsonSerializerSettings` `DefaultValueHandling` ve ayarları, tüm null-value veya varsayılan değer özelliklerinin yoksayılması gerektiğini belirtmenize izin verilir.
* `NullValueHandling` Öznitelik `DefaultValueHandling` teki `[JsonProperty]` ve ayarlar, null veya varsayılan değer olarak ayarlandığında göz ardı edilmesi gereken tek tek özellikleri belirtmenize izin verirken.

<xref:System.Text.Json>serihale ederken özellikleri atlamak için aşağıdaki yolları sağlar:

* Bir özellikteki [[JsonIgnore]](system-text-json-how-to.md#exclude-individual-properties) özelliği, özelliğin serileştirme sırasında JSON'dan atlanına neden olur.
* [IgnoreNullValues](system-text-json-how-to.md#exclude-all-null-value-properties) global seçeneği, tüm null-value özelliklerini hariç tutmanızı sağlar.
* [IgnoreReadOnlyProperties](system-text-json-how-to.md#exclude-all-read-only-properties) genel seçeneği, salt okunur tüm özellikleri hariç tutmanızı sağlar.

Bu **seçenekler** şunları anlamanızı sağlar:

* Tür için varsayılan değere sahip tüm özellikleri yoksayın.
* Tür için varsayılan değere sahip seçili özellikleri yoksayın.
* Seçili özellikleri, değerleri null ise yoksayın.
* Çalışma zamanında değerlendirilen rasgele ölçütlere göre seçili özellikleri yoksay.

Bu işlevsellik için özel bir dönüştürücü yazabilirsiniz. Burada bir örnek POCO ve bu yaklaşımı gösteren bunun için özel bir dönüştürücü' s:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRuntimeIgnoreConverter.cs)]

Dönüştürücü, değeri `Summary` null, boş bir dize veya "N/A" ise özelliğin serileştirmeden atlanına neden olur.

Bu özel dönüştürücü, [sınıf üzerinde bir öznitelik kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) veya <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyona [dönüştürücü ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) kaydolun.

Bu yaklaşım, şunları varsa ek mantık gerektirir:

* POCO karmaşık özelliklere sahiptir.
* Özel kodlayıcılar gibi `[JsonIgnore]` öznitelikleri veya seçenekleri işlemek gerekir.

### <a name="specify-date-format"></a>Tarih biçimini belirtin

`Newtonsoft.Json`özelliklerinin ve türlerinin `DateTime` serihale ve `DateTimeOffset` deserialized nasıl kontrol etmek için çeşitli yollar sağlar:

* Ayar, `DateTimeZoneHandling` tüm `DateTime` değerleri UTC tarihleri olarak seri hale getirmek için kullanılabilir.
* Ayar `DateFormatString` ve `DateTime` dönüştürücüler tarih dizeleri biçimini özelleştirmek için kullanılabilir.

Yerleşik <xref:System.Text.Json>destek veren tek format ISO 8601-1:2019'dur, çünkü yaygın olarak benimsenmiştir, kesindir ve tam olarak gidiş-dönüş gezileri yapar. Başka bir biçim kullanmak için özel bir dönüştürücü oluşturun. Daha fazla bilgi için [System.Text.Json'daki DateTime ve DateTimeOffset desteğine](../datetime/system-text-json-support.md)bakın.

### <a name="callbacks"></a>Geri Çağırmalar

`Newtonsoft.Json`serileştirme veya deserialization işleminde birkaç noktada özel kod yürütmenizi sağlar:

* OnDeserializing (bir nesneyi deserialize etmeye başlarken)
* OnDeserialized (bir nesneyi deserializing bittiğinde)
* OnSerializing (bir nesneyi serihale etmeye başlarken)
* OnSerialized (bir nesneyi serihale tamamladığında)

, <xref:System.Text.Json>özel bir dönüştürücü yazarak geri aramaları simüle edebilirsiniz. Aşağıdaki örnek, bir POCO için özel bir dönüştürücü gösterir. Dönüştürücü, geri aramayla karşılık gelen her noktada `Newtonsoft.Json` bir ileti görüntüleyen kod içerir.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

Bu özel dönüştürücü, [sınıf üzerinde bir öznitelik kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) veya <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters> koleksiyona [dönüştürücü ekleyerek](system-text-json-converters-how-to.md#registration-sample---converters-collection) kaydolun.

Önceki örneği izleyen özel bir dönüştürücü kullanıyorsanız:

* Kodun `OnDeserializing` yeni POCO örneğine erişimi yok. Deserialization başında yeni POCO örneğini işlemek için, bu kodu POCO oluşturucuya koyun.
* Özyinelemeli olarak ararken `Serialize` seçenekler nesnesinde geçmeyin `Deserialize`veya . Seçenekler nesnesi `Converters` koleksiyonu içerir. Eğer ya `Serialize` da, `Deserialize`dönüştürücü kullanılacak, bir yığın taşması özel durum neden sonsuz bir döngü yapma geçerseniz.

### <a name="public-and-non-public-fields"></a>Genel ve genel olmayan alanlar

`Newtonsoft.Json`alanları ve özellikleri serihale ve deserialize edebilirsiniz. <xref:System.Text.Json>yalnızca kamu malları ile çalışır. Özel dönüştürücüler bu işlevselliği sağlayabilir.

### <a name="internal-and-private-property-setters-and-getters"></a>Dahili ve özel mülkiyet ayarlayıcıları ve getters

`Newtonsoft.Json`özel ve dahili özellik ayarlayıcıları `JsonProperty` ve özel nitelik üzerinden getters kullanabilirsiniz. <xref:System.Text.Json>yalnızca genel ayarlayıcıları destekler. Özel dönüştürücüler bu işlevselliği sağlayabilir.

### <a name="populate-existing-objects"></a>Varolan nesneleri doldurma

JSON `JsonConvert.PopulateObject` `Newtonsoft.Json` belgesini yeni bir örnek oluşturmak yerine varolan bir sınıf örneğine deserialize eder. <xref:System.Text.Json>her zaman varsayılan kamu parametresiz oluşturucu kullanarak hedef türünün yeni bir örneği oluşturur. Özel dönüştürücüler varolan bir örne deserialize edebilirsiniz.

### <a name="reuse-rather-than-replace-properties"></a>Özellikleri değiştirmek yerine yeniden kullanma

Ayar, `Newtonsoft.Json` `ObjectCreationHandling` deserialization sırasında değiştirilen yerine özellikleri nesneleri yeniden gerektiğini belirtmenizi sağlar. <xref:System.Text.Json>özelliklerinesneleri her zaman değiştirir.  Özel dönüştürücüler bu işlevselliği sağlayabilir.

### <a name="add-to-collections-without-setters"></a>Ayarlayıcılar olmadan koleksiyonlara ekleme

Deserialization sırasında, `Newtonsoft.Json` özellik hiçbir ayarlayıcı olsa bile bir koleksiyona nesneleri ekler. <xref:System.Text.Json>ayarlayıcıları olmayan özellikleri yok sayar. Özel dönüştürücüler bu işlevselliği sağlayabilir.

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>JsonSerializer'ın şu anda desteklemediği senaryolar

Aşağıdaki senaryolar için geçici çözüm pratik veya mümkün değildir. Bu `Newtonsoft.Json` özelliklere güveniyorsanız, önemli değişiklikler olmadan geçiş mümkün olmayacaktır.

### <a name="preserve-object-references-and-handle-loops"></a>Nesne başvurularını ve işleme döngülerini koruyun

Varsayılan olarak, `Newtonsoft.Json` değere göre serileştirir. Örneğin, bir nesne aynı `Person` nesneye başvuru içeren iki özellik içeriyorsa, o `Person` nesnenin özelliklerinin değerleri JSON'da çoğaltılır.

`Newtonsoft.Json`referansa `PreserveReferencesHandling` göre `JsonSerializerSettings` serileştirmenizi sağlayan bir ayarı vardır:

* İlk `Person` nesne için oluşturulan JSON'a bir tanımlayıcı meta verisi eklenir.
* İkinci `Person` nesne için oluşturulan JSON özellik değerleri yerine bu tanımlayıcıya bir başvuru içerir.

`Newtonsoft.Json`ayrıca, `ReferenceLoopHandling` bir özel durum atmak yerine dairesel başvuruları yoksaymanızı sağlayan bir ayarı vardır.

<xref:System.Text.Json>yalnızca değere göre serileştirmeyi destekler ve dairesel başvurular için bir özel durum oluşturur.

### <a name="systemruntimeserialization-attributes"></a>System.Runtime.Serialization öznitelikleri

<xref:System.Text.Json>`System.Runtime.Serialization` gibi ad alanından öznitelikleri `DataMemberAttribute` desteklemez. `IgnoreDataMemberAttribute`

### <a name="octal-numbers"></a>Octal sayılar

`Newtonsoft.Json`satır sıfırlı sayıları sekizli sayılar olarak ele verir. <xref:System.Text.Json>[RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi izin vermediği için satır aralığı sıfırlarına izin vermez.

### <a name="missingmemberhandling"></a>Eksik Üye Taşıma

`Newtonsoft.Json`JSON hedef türünde eksik özellikleri içeriyorsa deserialization sırasında özel durumlar atmak için yapılandırılabilir. <xref:System.Text.Json>[[JsonExtensionData] özniteliğini](system-text-json-how-to.md#handle-overflow-json)kullandığınız zamanlar dışında, JSON'daki ek özellikleri yok sayar. Eksik üye özelliği için geçici çözüm yok.

### <a name="tracewriter"></a>TraceWriter

`Newtonsoft.Json`serileştirme veya deserialization tarafından oluşturulan günlükleri görüntülemek için bir `TraceWriter` kullanarak hata ayıklama sağlar. <xref:System.Text.Json>günlük yapmaz.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JsonDocument ve JsonElement JToken ile karşılaştırıldığında (JObject, JArray gibi)

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>varolan JSON yüklerinden **salt okunur** Belge Nesnesi Modelini (DOM) ayrıştırıp oluşturma olanağı sağlar. DOM, JSON yükündeki verilere rasgele erişim sağlar. Yükü oluşturan JSON öğelerine <xref:System.Text.Json.JsonElement> tür üzerinden erişilebilir. Tür, `JsonElement` JSON metnini ortak .NET türlerine dönüştürmek için API'ler sağlar. `JsonDocument`bir <xref:System.Text.Json.JsonDocument.RootElement> özelliği ortaya çıkarır.

### <a name="jsondocument-is-idisposable"></a>JsonDocument IDisposable olduğunu

`JsonDocument`verilerin birleştirilmiş arabelleği içine bir bellek görünümü oluşturur. Bu nedenle, `JArray` `Newtonsoft.Json`aksine `JObject` `JsonDocument` veya gelen, türü uygular `IDisposable` ve bir kullanarak blok içinde kullanılması gerekir.

Yalnızca ömür `JsonDocument` boyu sahiplik aktarmak ve sorumluluğu arayana atmak istiyorsanız API'nizden bir geri döndürün. Çoğu senaryoda, bu gerekli değildir. Arayan kişinin tüm JSON belgesiyle çalışması gerekiyorsa, <xref:System.Text.Json.JsonElement.Clone%2A> <xref:System.Text.Json.JsonDocument.RootElement%2A>bir . <xref:System.Text.Json.JsonElement> Arayan JSON belge içinde belirli bir öğe ile çalışması <xref:System.Text.Json.JsonElement.Clone%2A> gerekiyorsa, bu <xref:System.Text.Json.JsonElement>döndürülür. Bir oluşturmadan `RootElement` doğrudan bir alt öğeyi `Clone`döndürürseniz, arayan, sahibi `JsonElement` elden `JsonDocument` çıkarılındıktan sonra döndürülen öğeye erişemez.

Burada bir yapmak gerektiren bir `Clone`örnek:

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

Önceki kod bir `JsonElement` özellik içeren `fileName` bir bekliyor. Bu JSON dosyasını açar `JsonDocument`ve bir oluşturur. Yöntem, arayanın belgenin tamamıyla çalışmak istediğini varsayar, `Clone` bu `RootElement`nedenle .

Bir alt `JsonElement` öğe alıyorsanız ve bir alt öğeyi döndürüyorsanız, alt öğeden birini `Clone` döndürmeniz gerekmez. Arayan kişi, geçenin `JsonDocument` `JsonElement` ait olduğu şeyi canlı tutmaktan sorumludur. Örneğin:

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument salt okunur

<xref:System.Text.Json> DOM, JSON öğelerini ekemez, kaldıramaz veya değiştiremez. Performans için bu şekilde tasarlanmıştır ve ortak JSON yük boyutlarını ayrıştırmak için ayırmaları azaltmak için (yani 1 MB'<) . Senaryonuz şu anda değiştirilebilir bir DOM kullanıyorsa, aşağıdaki geçici çözümlerden biri uygulanabilir olabilir:

* Sıfırdan `JsonDocument` bir inşa etmek için (yani, `Parse` yönteme mevcut bir JSON yükü geçmeden), `Utf8JsonWriter` json metin kullanarak yazmak ve yeni `JsonDocument`bir yapmak için bu çıktı ayrıştırmak .
* Varolan `JsonDocument`bir değişiklik için, json metin yazmak için kullanabilirsiniz, yazarken değişiklik yapma, `JsonDocument`ve yeni bir yapmak için bu çıktı ayrıştırmak .
* Varolan JSON belgelerini birleştirmek `JObject.Merge` `JContainer.Merge` için, `Newtonsoft.Json`bu [GitHub sorununa](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853)bakın.

### <a name="jsonelement-is-a-union-struct"></a>JsonElement bir sendika yapıdır

`JsonDocument`herhangi bir `RootElement` JSON öğesini kapsayan bir birlik, yapı türü olan türü <xref:System.Text.Json.JsonElement>bir özellik olarak ortaya çıkarır. `Newtonsoft.Json`, , `JObject``JArray` `JToken`, ve benzeri gibi özel hiyerarşik türleri kullanır. `JsonElement`üzerinde arama ve sayısallaştırabileceğiniz ve JSON öğelerini .NET türlerine dönüştürmek için kullanabileceğiniz `JsonElement` bir şeydir.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Alt öğeler için JsonDocument ve JsonElement nasıl aranır?

JSON belirteçleri kullanarak `JObject` `JArray` veya `Newtonsoft.Json` bazı sözlükte arama lar çünkü nispeten hızlı olma eğilimindedir. Buna karşılık, arama `JsonElement` özellikleri sıralı bir arama gerektirir ve dolayısıyla nispeten `TryGetProperty`yavaş (örneğin kullanırken). <xref:System.Text.Json>arama süresi yerine ilk ayrıştırmanın süresini en aza indirmek için tasarlanmıştır. Bu nedenle, bir `JsonDocument` nesne de ararken performansı en iyi duruma getirmek için aşağıdaki yaklaşımları kullanın:

* Kendi dizin oluşturma veya döngüler <xref:System.Text.Json.JsonElement.EnumerateObject%2A>yapmak yerine yerleşik tümumerators (ve)<xref:System.Text.Json.JsonElement.EnumerateArray%2A> kullanın.
* Kullanarak her özellik üzerinden bütün `JsonDocument` bir ardışık `RootElement`arama yapmayın. Bunun yerine, JSON verilerinin bilinen yapısına göre iç içe geçen JSON nesnelerinde arama yapın. `Grade` Örneğin, nesnelerde `Student` bir özellik arıyorsanız, `Student` `Grade` `JsonElement` `Grade` nesneleri iletin ve özellikleri arayan tüm nesneleri aramak yerine her biri için değer alın. İkincisini yapmak, aynı veriler üzerinden gereksiz geçişler yapmasına neden olur.

Kod örneği için, [verilere erişim için JsonBelgesi'ni kullanın'a](system-text-json-how-to.md#use-jsondocument-for-access-to-data)bakın.

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader JsonTextReader ile karşılaştırıldığında

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>utf-8 kodlanmış JSON metin için yüksek performanslı, düşük tahsisat, ileri sadece okuyucu, [readOnlySpan\<bayt>](xref:System.ReadOnlySpan%601) veya [\<ReadOnlySequence bayt>](xref:System.Buffers.ReadOnlySequence%601)okuyun. Özel `Utf8JsonReader` ayrıştırıcılar ve deserializers oluşturmak için kullanılabilecek düşük düzeyli bir türüdür.

Aşağıdaki bölümlerde kullanmak `Utf8JsonReader`için önerilen programlama desenleri açıklayınız.

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader bir ref struct olduğunu

Türü bir *ref struct*olduğundan, [belirli sınırlamaları](../../csharp/language-reference/builtin-types/struct.md#ref-struct)vardır. `Utf8JsonReader` Örneğin, bir sınıf veya yapı üzerinde bir ref struct dışında bir alan olarak depolanabilir. Yüksek performans elde etmek için, `ref struct` bu tür bir giriş [>,\< ](xref:System.ReadOnlySpan%601)kendisi bir ref struct giriş önbellek gerekiyor beri olmalıdır. Buna ek olarak, bu tür durum tutar beri mutable. Bu nedenle, değer yerine **ref tarafından geçirin.** Değere göre geçirilmesi bir yapı kopyasına neden olur ve durum değişiklikleri arayan tarafından görülemez. Bu bir `Newtonsoft.Json` sınıf `Newtonsoft.Json` `JsonTextReader` olduğundan farklıdır. Ref yapılarının nasıl kullanılacağı hakkında daha fazla bilgi için [bkz.](../../csharp/write-safe-efficient-code.md)

### <a name="read-utf-8-text"></a>UTF-8 metnini okuyun

Kullanırken mümkün olan en `Utf8JsonReader`iyi performansı elde etmek için UTF-16 dizeleri yerine UTF-8 metni olarak kodlanmış JSON yüklerini okuyun. Kod örneği için [Utf8JsonReader kullanarak filtre verilerine](system-text-json-how-to.md#filter-data-using-utf8jsonreader)bakın.

### <a name="read-with-a-stream-or-pipereader"></a>Bir Akış veya PipeReader ile okuyun

UTF-8 kodlanmış [ReadOnlySpan\<bayt>](xref:System.ReadOnlySpan%601) veya [ReadOnlySequence\<bayt>](xref:System.Buffers.ReadOnlySequence%601) (bir okuma sonucu) okuma `Utf8JsonReader` <xref:System.IO.Pipelines.PipeReader>destekler.

Senkron okuma için, bir bayt dizisi içine akışı sonuna kadar JSON yük okuyabilir ve okuyucuya geçirebilirsiniz. Bir dize (UTF-16 olarak kodlanmış) okuma <xref:System.Text.Encoding.UTF8>için, arayın.<xref:System.Text.Encoding.GetBytes%2A> önce dizeyi UTF-8 kodlanmış bayt dizisine nakledin. O zaman bunu. `Utf8JsonReader`

Girişin `Utf8JsonReader` JSON metni olarak düşünüldüğünden, UTF- 8 bayt sürücü markı (BOM) geçersiz JSON olarak kabul edilir. Arayan okuyucuya veri aktarmadan önce filtre gerekir.

Kod örnekleri için [bkz.](system-text-json-how-to.md#use-utf8jsonreader)

### <a name="read-with-multi-segment-readonlysequence"></a>Çok segmentli ReadOnlySequence ile okuyun

JSON girişiniz [readOnlySpan\<bayt>](xref:System.ReadOnlySpan%601)ise, okuma döngüsünden geçerken `ValueSpan` her JSON öğesine okuyucudaki özellikten erişilebilir. Ancak, giriş bir [ReadOnlySequence\<bayt>](xref:System.Buffers.ReadOnlySequence%601) (bir okuma <xref:System.IO.Pipelines.PipeReader>sonucu), bazı JSON öğeleri nesnenin `ReadOnlySequence<byte>` birden çok segmentleri straddle olabilir. Bu öğelerbitişik bir <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> bellek bloğunda erişilebilir olmaz. Bunun yerine, girdi olarak çok `ReadOnlySequence<byte>` segmentli bir <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> zaman, geçerli JSON öğesine nasıl erişin yolunu bulmak için okuyucudaki özelliği yokla. Önerilen desen aşağıda veda edebilirsiniz:

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

### <a name="use-valuetextequals-for-property-name-lookups"></a>Özellik adı aramaları için ValueTextEquals'ı kullanma

Özellik adı <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> aramalarını arayarak <xref:System.MemoryExtensions.SequenceEqual%2A> bayt karşılaştırmaları yapmayın. Bunun <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> yerine arayın, çünkü bu yöntem JSON'da kaçan karakterlerden kurtulur. Aşağıda, "ad" adlı bir özelliğin nasıl arandığını gösteren bir örnek verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>Null değerlerini nullable değer türlerine okuma

`Newtonsoft.Json`bir döndürerek <xref:System.Nullable%601>sizin `ReadAsBoolean`için bir `Null` `TokenType` işleyen API'ler `bool?`sağlar, örneğin. Yerleşik `System.Text.Json` API'ler yalnızca nullable değer türlerini döndürer. Örneğin, <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> bir `bool`. JSON'da bulursa `Null` bir istisna olur. Aşağıdaki örnekler, nulls işlemek için iki yol gösterir, bir nullable değer türü döndürerek ve bir varsayılan değer döndürerek:

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

### <a name="multi-targeting"></a>Çok hedefleme

Belirli hedef çerçeveler `Newtonsoft.Json` için kullanmaya devam etmek gerekiyorsa, çok hedefli olabilir ve iki uygulamanız olabilir. Ancak, bu önemsiz değildir ve `#ifdefs` bazı ve kaynak çoğaltma gerektirir. Mümkün olduğunca çok kod paylaşmak için bir `ref struct` yolu `Utf8JsonReader` etrafında `Newtonsoft.Json` `JsonTextReader`bir sarmalayıcı oluşturmak ve . Bu sarıcı, davranış farklılıklarını yalıtırken ortak yüzey alanını birliyi birleşdirebilir. Bu, yeni türün başvuruyla etrafından geçirilmesiyle birlikte, değişiklikleri esas olarak türün yapısına yalıtmanıza olanak tanır. Bu, [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) kitaplığı aşağıdaki desendir:

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter JsonTextWriter ile karşılaştırıldığında

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>gibi ortak .NET türlerinden UTF-8 kodlanmış JSON metin yazmak `String` `Int32`için `DateTime`yüksek performanslı bir yoldur , ve . Yazar, özel serializers oluşturmak için kullanılabilecek düşük düzeyli bir türüdür.

Aşağıdaki bölümlerde kullanmak `Utf8JsonWriter`için önerilen programlama desenleri açıklayınız.

### <a name="write-with-utf-8-text"></a>UTF-8 metniyle yazma

Kullanırken mümkün olan en `Utf8JsonWriter`iyi performansı elde etmek için, UTF-16 dizeleri yerine UTF-8 metni olarak kodlanmış JSON yükleri yazın. Bilinen <xref:System.Text.Json.JsonEncodedText> dize özellik adlarını ve değerlerini statik olarak önbelleğe almak ve ön kodlamak için kullanın ve bunları UTF-16 dize literals kullanmak yerine yazara aktarın. Bu önbelleğe alma ve UTF-8 bayt dizileri kullanarak daha hızlıdır.

Bu yaklaşım, özel kaçış yapmanız gerekiyorsa da çalışır. `System.Text.Json`bir dize yazarken kaçmayı devre dışı bırakmaz. Ancak, yazar için bir <xref:System.Text.Encodings.Web.JavaScriptEncoder> seçenek olarak kendi özel geçmek, `JsonEncodedText` ya da `JavascriptEncoder` kaçan yapmak için kullanır kendi `JsonEncodedText` oluşturmak ve daha sonra dize yerine yazmak. Daha fazla bilgi için [bkz.](system-text-json-how-to.md#customize-character-encoding)

### <a name="write-raw-values"></a>Ham değerleri yazma

Yöntem, `Newtonsoft.Json` `WriteRawValue` bir değerin beklendiği ham JSON'u yazar. <xref:System.Text.Json>doğrudan eşdeğeri yoktur, ancak burada yalnızca geçerli JSON'un yazılmasını sağlayan bir geçici çözüm vardır:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Kaçan karakteri özelleştirme

[StringEscapeHandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) ayarı, ASCII olmayan tüm karakterlerden `JsonTextWriter` **veya** HTML karakterlerinden kaçmak için seçenekler sunar. Varsayılan olarak, `Utf8JsonWriter` ASCII **ve** HTML olmayan tüm karakterlerden kaçar. Bu kaçış derinlemesine güvenlik nedenleriyle yapılır. Farklı bir kaçış ilkesi belirtmek <xref:System.Text.Encodings.Web.JavaScriptEncoder> için, <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType>bir ve ayarla. Daha fazla bilgi için [bkz.](system-text-json-how-to.md#customize-character-encoding)

### <a name="customize-json-format"></a>JSON biçimini özelleştirme

`JsonTextWriter`eşdeğeri olmayan aşağıdaki `Utf8JsonWriter` ayarları içerir:

* [Girintisi](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) - Girintisi kaç karakter belirtir. `Utf8JsonWriter`her zaman 2 karaktergirini yapar.
* [IndentChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) - Girintisi için kullanılacak karakteri belirtir.  `Utf8JsonWriter`her zaman beyaz alan kullanır.
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) - Dize değerlerini çevreleyen karakteri belirtir.  `Utf8JsonWriter`her zaman çift tırnak kullanır.
* [QuoteName](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) - Özellik adlarının tırnak işaretleriyle çevrelenip çevrelemeyeceğini belirtir.  `Utf8JsonWriter`her zaman tırnak ile onları çevreleyen.

Bu yollarla üretilen `Utf8JsonWriter` JSON'u özelleştirmenize izin verecek geçici çözümler yoktur.

### <a name="write-null-values"></a>Null değerleri yazma

Kullanarak null değerleri `Utf8JsonWriter`yazmak için , arayın:

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A>değer olarak null ile bir anahtar değeri çifti yazmak için.
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A>bir JSON dizisinin bir öğesi olarak null yazmak için.

Bir dize özelliği için, dize <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> null `WriteNull` ise `WriteNullValue` <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> ve eşdeğer ve .

### <a name="write-timespan-uri-or-char-values"></a>Zaman aralığı, Uri veya char değerlerini yazın

`JsonTextWriter``WriteValue` [TimeSpan,](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm) [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)ve [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) değerleri için yöntemler sağlar. `Utf8JsonWriter`eşdeğer yöntemleri yoktur. Bunun yerine, bu değerleri dizeleri `ToString()`olarak biçimlendirin (örneğin arayarak) ve çağırın. <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>

### <a name="multi-targeting"></a>Çok hedefleme

Belirli hedef çerçeveler `Newtonsoft.Json` için kullanmaya devam etmek gerekiyorsa, çok hedefli olabilir ve iki uygulamanız olabilir. Ancak, bu önemsiz değildir ve `#ifdefs` bazı ve kaynak çoğaltma gerektirir. Mümkün olduğunca çok kod paylaşmak için bir yolu `Utf8JsonWriter` etrafında `Newtonsoft` `JsonTextWriter`bir sarmalayıcı oluşturmak ve . Bu sarıcı, davranış farklılıklarını yalıtırken ortak yüzey alanını birliyi birleşdirebilir. Bu, değişiklikleri esas olarak türün yapısında yalıtmanıza olanak tanır. [Microsoft.Extensions.DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) kitaplığı aşağıdaki gibidir:

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>Ek kaynaklar

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.JsonGenel bakış](system-text-json-overview.md)
* [Nasıl kullanılır?System.Text.Json](system-text-json-how-to.md)
* [Özel dönüştürücü yazma](system-text-json-converters-how-to.md)
* [DateTime ve DateTimeOffset desteğiSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonAPI başvurusu](xref:System.Text.Json)
* [System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)
