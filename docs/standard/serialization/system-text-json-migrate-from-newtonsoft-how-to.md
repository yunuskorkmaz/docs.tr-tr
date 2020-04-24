---
title: Sürümünden Newtonsoft.Json .net 'e System.Text.Json geçiş
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
# <a name="how-to-migrate-from-newtonsoftjson-to-systemtextjson"></a>Newtonsoft. JSON 'dan System. Text. JSON 'a geçiş

Bu makalede [Newtonsoft. JSON](https://www.newtonsoft.com/json) öğesinden öğesine <xref:System.Text.Json>nasıl geçiş yapılacağı gösterilmektedir.

Ad `System.Text.Json` alanı, JAVASCRIPT nesne GÖSTERIMI (JSON) öğesinden serileştirmek ve seri durumdan çıkarmak için işlevsellik sağlar. `System.Text.Json` Kitaplık, [.NET Core 3,0](https://aka.ms/netcore3download) paylaşılan çerçevesine dahildir. Diğer hedef çerçeveler için [System. Text. JSON](https://www.nuget.org/packages/System.Text.Json) NuGet paketini yükler. Paket şunları destekler:

* .NET Standard 2,0 ve sonraki sürümler
* .NET Framework 4.7.2 ve sonraki sürümler
* .NET Core 2,0, 2,1 ve 2,2

`System.Text.Json`Öncelikle performans, güvenlik ve standartlar uyumluluğuna odaklanır. Varsayılan davranışta bazı önemli farklılıklar vardır ve ile `Newtonsoft.Json`Özellik eşliği yoktur. Bazı senaryolarda `System.Text.Json` yerleşik işlevselliği yoktur, ancak önerilen geçici çözümler vardır. Diğer senaryolar için geçici çözümler pratik bir şekilde yapılır. Uygulamanız eksik bir özelliğe bağımlıysa, senaryonuza yönelik desteğin eklenip eklenemediğine ulaşmak için [bir sorun](https://github.com/dotnet/runtime/issues/new) yerleştirmeyi düşünün.

<!-- For information about which features might be added in future releases, see the [Roadmap](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md). [Restore this when the roadmap is updated.]-->

Bu <xref:System.Text.Json.JsonSerializer> makalenin çoğu, API 'yi kullanma ile ilgilidir, ancak aynı zamanda <xref:System.Text.Json.JsonDocument> (belge nesne modeli veya DOM), <xref:System.Text.Json.Utf8JsonReader>ve <xref:System.Text.Json.Utf8JsonWriter> türlerini temsil eder.

## <a name="table-of-differences-between-newtonsoftjson-and-systemtextjson"></a>Newtonsoft. JSON ve System. Text. JSON arasındaki farklar tablosu

Aşağıdaki tabloda Özellikler ve `Newtonsoft.Json` `System.Text.Json` eşdeğerleri listelenmektedir. Eşdeğerleri aşağıdaki kategorilere ayrılır:

* Yerleşik işlevsellik tarafından desteklenir. Benzer davranış `System.Text.Json` alma, bir öznitelik veya genel seçenek kullanımını gerektirebilir.
* Desteklenmez, geçici çözüm mümkündür. Geçici çözümler, `Newtonsoft.Json` işlevlerle tamamen eşlik sağlamayan [özel dönüştürücülerdir](system-text-json-converters-how-to.md). Bunlardan bazılarının örnek kodu örnek olarak verilmiştir. Bu `Newtonsoft.Json` özelliklerden yararlandıysanız geçiş, .NET nesne modellerinizde veya diğer kod değişikliklerinde değişiklik yapılmasını gerektirir.
* Desteklenmez, geçici çözüm pratik veya mümkün değildir. Bu `Newtonsoft.Json` özelliklerden yararlandıysanız geçiş önemli değişiklikler yapılmadan mümkün olmayacaktır.

| Newtonsoft. JSON özelliği                               | System. Text. JSON eşdeğeri |
|-------------------------------------------------------|-----------------------------|
| Varsayılan olarak büyük/küçük harfe duyarsız seri hale           | ✔️ [Propertynamecaseduyarsız genel ayarı](#case-insensitive-deserialization) |
| Camel-Case Özellik adları                             | ✔️ [Propertynamingpolicy genel ayarı](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) |
| En az karakter kaçış                            | ✔️ [katı karakter kaçış, yapılandırılabilir](#minimal-character-escaping) |
| `NullValueHandling.Ignore`Genel ayar             | ✔️ [ıgnorenullvalues genel seçeneği](system-text-json-how-to.md#exclude-all-null-value-properties) |
| Açıklamalara izin ver                                        | ✔️ [ReadCommentHandling genel ayarı](#comments) |
| Sondaki virgüllerin kullanılmasına izin ver                                 | ✔️ [Allowtrailingvirgüller genel ayarı](#trailing-commas) |
| Özel dönüştürücü kaydı                         | ✔️ [öncelik sırası farklı](#converter-registration-precedence) |
| Varsayılan olarak en fazla derinlik yok                           | ✔️ [varsayılan en yüksek derinlik 64, yapılandırılabilir](#maximum-depth) |
| Geniş kapsamlı türler için destek                    | ⚠️[Bazı türler için özel dönüştürücüler gerekir](#types-without-built-in-support) |
| Dizeleri sayı olarak seri durumdan çıkarma                        | ⚠️[Desteklenmez, geçici çözüm, örnek](#quoted-numbers) |
| Dize `Dictionary` olmayan anahtarla seri durumdan çıkarma          | ⚠️[Desteklenmez, geçici çözüm, örnek](#dictionary-with-non-string-key) |
| Polimorfik serileştirme                             | ⚠️[Desteklenmez, geçici çözüm, örnek](#polymorphic-serialization) |
| Polimorfik seri kaldırma                           | ⚠️[Desteklenmez, geçici çözüm, örnek](#polymorphic-deserialization) |
| Çıkarılan türden `object` özellikleri seri durumdan çıkar      | ⚠️[Desteklenmez, geçici çözüm, örnek](#deserialization-of-object-properties) |
| JSON `null` sabit değerinin null yapılamayan değer türlerine serisini kaldırma | ⚠️[Desteklenmez, geçici çözüm, örnek](#deserialize-null-to-non-nullable-type) |
| Sabit sınıflar ve yapılar için seri durumdan çıkarma          | ⚠️[Desteklenmez, geçici çözüm, örnek](#deserialize-to-immutable-classes-and-structs) |
| `[JsonConstructor]` özniteliği                         | ⚠️[Desteklenmez, geçici çözüm, örnek](#specify-constructor-to-use) |
| `Required`özniteliği üzerinde `[JsonProperty]` ayarlama        | ⚠️[Desteklenmez, geçici çözüm, örnek](#required-properties) |
| `NullValueHandling`özniteliği üzerinde `[JsonProperty]` ayarlama | ⚠️[Desteklenmez, geçici çözüm, örnek](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`özniteliği üzerinde `[JsonProperty]` ayarlama | ⚠️[Desteklenmez, geçici çözüm, örnek](#conditionally-ignore-a-property)  |
| `DefaultValueHandling`Genel ayar                 | ⚠️[Desteklenmez, geçici çözüm, örnek](#conditionally-ignore-a-property) |
| `DefaultContractResolver`özellikleri dışlamak için       | ⚠️[Desteklenmez, geçici çözüm, örnek](#conditionally-ignore-a-property) |
| `DateTimeZoneHandling`, `DateFormatString` ayarlar   | ⚠️[Desteklenmez, geçici çözüm, örnek](#specify-date-format) |
| Geri Çağırmalar                                             | ⚠️[Desteklenmez, geçici çözüm, örnek](#callbacks) |
| Ortak ve genel olmayan alanlar için destek              | ⚠️[Desteklenmez, geçici çözüm](#public-and-non-public-fields) |
| İç ve özel özellik ayarlayıcıları ve alıcılar için destek | ⚠️[Desteklenmez, geçici çözüm](#internal-and-private-property-setters-and-getters) |
| `JsonConvert.PopulateObject` yöntemi                   | ⚠️[Desteklenmez, geçici çözüm](#populate-existing-objects) |
| `ObjectCreationHandling`Genel ayar               | ⚠️[Desteklenmez, geçici çözüm](#reuse-rather-than-replace-properties) |
| Ayarlayıcısız koleksiyonlara Ekle                    | ⚠️[Desteklenmez, geçici çözüm](#add-to-collections-without-setters) |
| `PreserveReferencesHandling`Genel ayar           | ❌[Desteklenmiyor](#preserve-object-references-and-handle-loops) |
| `ReferenceLoopHandling`Genel ayar                | ❌[Desteklenmiyor](#preserve-object-references-and-handle-loops) |
| Öznitelikler için `System.Runtime.Serialization` destek | ❌[Desteklenmiyor](#systemruntimeserialization-attributes) |
| `MissingMemberHandling`Genel ayar                | ❌[Desteklenmiyor](#missingmemberhandling) |
| Tırnak işaretleri olmadan özellik adlarına izin ver                   | ❌[Desteklenmiyor](#json-strings-property-names-and-string-values) |
| Dize değerlerinin çevresinde tek tırnak işaretlerine izin ver              | ❌[Desteklenmiyor](#json-strings-property-names-and-string-values) |
| Dize özellikleri için dize olmayan JSON değerlerine izin ver    | ❌[Desteklenmiyor](#non-string-values-for-string-properties) |

Bu, `Newtonsoft.Json` özelliklerin kapsamlı bir listesi değildir. Listede, [GitHub sorunları](https://github.com/dotnet/runtime/issues?q=is%3Aopen+is%3Aissue+label%3Aarea-System.Text.Json) veya [StackOverflow](https://stackoverflow.com/questions/tagged/system.text.json) gönderileri için istenen birçok senaryo bulunur. Burada listelenen senaryolardan biri için şu anda örnek kodu olmayan bir geçici çözüm uygularsanız ve çözümünüzü paylaşmak istiyorsanız, bu sayfanın altındaki **geri bildirim** bölümünde **Bu sayfayı** seçin. Bu, bu belgenin GitHub deposunda bir sorun oluşturur ve bu sayfadaki **geri bildirim** bölümünde de listeler.

## <a name="differences-in-default-jsonserializer-behavior-compared-to-newtonsoftjson"></a>Newtonsoft. JSON ile karşılaştırıldığında varsayılan JsonSerializer davranışındaki farklılıklar

<xref:System.Text.Json>Varsayılan olarak katı olur ve arayan adına tahmin veya yorumlamayı önler, belirleyici davranışı vurgulayarak. Kitaplık, performans ve güvenlik için kasıtlı olarak bu şekilde tasarlanmıştır. `Newtonsoft.Json`Varsayılan olarak esnektir. Tasarımda bu temel fark, varsayılan davranıştaki aşağıdaki belirli farklılıklardan birçoğın arkasında bulunur.

### <a name="case-insensitive-deserialization"></a>Büyük/küçük harfe duyarsız seri hale

Seri durumdan çıkarma `Newtonsoft.Json` sırasında, varsayılan olarak büyük/küçük harfe duyarsız Özellik adı eşleştirmeyi yapar. <xref:System.Text.Json> Varsayılan değer büyük/küçük harfe duyarlıdır ve tam bir eşleşme yaptığından daha iyi performans sağlar. Büyük/küçük harfe duyarsız eşleşme yapma hakkında daha fazla bilgi için bkz. [büyük/küçük harfe duyarsız Özellik eşleştirme](system-text-json-how-to.md#case-insensitive-property-matching).

ASP.NET Core kullanarak dolaylı olarak `System.Text.Json` kullanıyorsanız, gibi `Newtonsoft.Json`davranışları almak için herhangi bir şey yapmanız gerekmez. ASP.NET Core, kullandığı `System.Text.Json` [Camel özellik adlarına](system-text-json-how-to.md#use-camel-case-for-all-json-property-names) ve büyük/küçük harfe duyarsız eşleştirmeye yönelik ayarları belirtir.

### <a name="minimal-character-escaping"></a>En az karakter kaçış

Serileştirme sırasında, `Newtonsoft.Json` karakterlerin kaçış olmadan üzerinden izin verme konusunda görece bir şekilde izin verilir. Diğer bir deyişle, bunları karakterin kod noktası `\uxxxx` olduğu `xxxx` yerde değiştirmez. Burada kaçış yaptığı yerlerde, karakterden önce bir (örneğin, `\` `"` olur `\"`) bir olarak yayarak bunu yapar. <xref:System.Text.Json>siteler arası betik (XSS) veya bilgi açıklama saldırılarına karşı derinlemesine savunma korumaları sağlamak için varsayılan olarak daha fazla karakter çıkar ve altı karakterli sırayı kullanarak bu şekilde yapılır. `System.Text.Json`ASCII olmayan tüm karakterleri varsayılan olarak çıkar, bu nedenle içinde `StringEscapeHandling.EscapeNonAscii` `Newtonsoft.Json`kullanıyorsanız herhangi bir şey yapmanız gerekmez. `System.Text.Json`Ayrıca, varsayılan olarak HTML duyarlı karakterleri de çıkar. Varsayılan `System.Text.Json` davranışı geçersiz kılma hakkında daha fazla bilgi için bkz. [karakter kodlamasını özelleştirme](system-text-json-how-to.md#customize-character-encoding).

### <a name="comments"></a>Açıklamalar

Seri durumdan çıkarma `Newtonsoft.Json` sırasında, varsayılan olarak JSON 'daki açıklamaları yoksayar. <xref:System.Text.Json> [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtiminde bunları içermediğinden, açıklamalar için özel durumlar oluşturmak varsayılan değer. Açıklamalara izin verme hakkında daha fazla bilgi için bkz. [yorumlara Izin verme ve sondaki virgüller](system-text-json-how-to.md#allow-comments-and-trailing-commas).

### <a name="trailing-commas"></a>Sondaki virgüller

Seri durumdan çıkarma `Newtonsoft.Json` sırasında, varsayılan olarak sondaki virgüllerin yok sayılır. Ayrıca, birden çok sondaki virgül yoksayar (örneğin, `[{"Color":"Red"},{"Color":"Green"},,]`). <xref:System.Text.Json> Varsayılan olarak, [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi bunlara izin vermediğinden, sondaki virgüller için özel durumlar throw. Bunları `System.Text.Json` kabul etme hakkında daha fazla bilgi için bkz. [yorumlara izin verme ve sondaki virgüller](system-text-json-how-to.md#allow-comments-and-trailing-commas). Birden çok bitiş virgülne izin vermenin bir yolu yoktur.

### <a name="converter-registration-precedence"></a>Dönüştürücü kayıt önceliği

Özel `Newtonsoft.Json` dönüştürücüler için kayıt önceliği aşağıdaki gibidir:

* Özelliğindeki öznitelik
* Türündeki öznitelik
* [Dönüştürücüler](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonSerializerSettings_Converters.htm) koleksiyonu

Bu sıra, `Converters` koleksiyondaki bir özel dönüştürücünün tür düzeyinde bir öznitelik uygulanarak kaydedilen bir dönüştürücü tarafından geçersiz kılındığı anlamına gelir. Bu kayıtların her ikisi de özellik düzeyindeki bir öznitelik tarafından geçersiz kılınır.

Özel <xref:System.Text.Json> dönüştürücüler için kayıt önceliği farklıdır:

* Özelliğindeki öznitelik
* <xref:System.Text.Json.JsonSerializerOptions.Converters>koleksiyon
* Türündeki öznitelik

Buradaki fark, `Converters` koleksiyondaki özel dönüştürücünün tür düzeyinde bir özniteliği geçersiz kılmanızdır. Bu öncelik sırasının arkasındaki amaç, çalışma zamanı değişikliklerinin tasarım zamanı seçimlerini geçersiz kılmasını sağlamak olacaktır. Önceliği değiştirme yolu yoktur.

Özel dönüştürücü kaydı hakkında daha fazla bilgi için bkz. [özel dönüştürücüyü kaydetme](system-text-json-converters-how-to.md#register-a-custom-converter).

### <a name="maximum-depth"></a>En yüksek derinlik

`Newtonsoft.Json`Varsayılan olarak en yüksek derinlik sınırına sahip değildir. Varsayılan <xref:System.Text.Json> 64 için bir sınır vardır ve bu ayar <xref:System.Text.Json.JsonSerializerOptions.MaxDepth?displayProperty=nameWithType>tarafından yapılandırılabilir.

### <a name="json-strings-property-names-and-string-values"></a>JSON dizeleri (özellik adları ve dize değerleri)

Seri durumdan çıkarma `Newtonsoft.Json` sırasında, çift tırnak, tek tırnak veya tırnak işaretleri olmadan çevrelenmiş özellik adlarını kabul eder. Çift tırnak veya tek tırnak işareti içine alınmış dize değerlerini kabul eder. Örneğin, aşağıdaki `Newtonsoft.Json` JSON 'yi kabul eder:

```json
{
  "name1": "value",
  'name2': "value",
  name3: 'value'
}
```

`System.Text.Json`yalnızca çift tırnak içindeki özellik adlarını ve dize değerlerini kabul eder çünkü bu biçim, [RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi için gereklidir ve geçerli JSON olarak kabul edilen tek biçimdir.

Tek tırnak içine alınmış bir değer, aşağıdaki iletiyle birlikte bir [Jsonexception](xref:System.Text.Json.JsonException) ile sonuçlanır:

```
''' is an invalid start of a value.
```

### <a name="non-string-values-for-string-properties"></a>Dize özellikleri için dize olmayan değerler

`Newtonsoft.Json`sayı veya sabit `true` değerler gibi dize olmayan değerleri kabul eder ve `false`tür dizesinin özelliklerine seri durumdan çıkarmak için. Aşağıdaki sınıfa `Newtonsoft.Json` başarıyla seri hale GETIRILEN bir JSON örneği aşağıda verilmiştir:

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

`System.Text.Json`dize olmayan değerlerin dize özelliklerine serileştirmez. Bir dize alanı için alınan dize olmayan bir değer, aşağıdaki iletiyle birlikte bir [Jsonexception](xref:System.Text.Json.JsonException) ile sonuçlanır:

```
The JSON value could not be converted to System.String.
```

## <a name="scenarios-using-jsonserializer-that-require-workarounds"></a>Geçici çözüm gerektiren JsonSerializer kullanan senaryolar

Aşağıdaki senaryolar yerleşik işlevsellik tarafından desteklenmez, ancak geçici çözümler mümkündür. Geçici çözümler, `Newtonsoft.Json` işlevlerle tamamen eşlik sağlamayan [özel dönüştürücülerdir](system-text-json-converters-how-to.md). Bunlardan bazılarının örnek kodu örnek olarak verilmiştir. Bu `Newtonsoft.Json` özelliklerden yararlandıysanız geçiş, .NET nesne modellerinizde veya diğer kod değişikliklerinde değişiklik yapılmasını gerektirir.

### <a name="types-without-built-in-support"></a>Yerleşik destek olmadan türler

<xref:System.Text.Json>, aşağıdaki türler için yerleşik destek sağlamaz:

* <xref:System.Data.DataTable>ve ilgili türler
* [Ayırt edici birleşimler](../../fsharp/language-reference/discriminated-unions.md), [kayıt türleri](../../fsharp/language-reference/records.md)ve [anonim kayıt türleri](../../fsharp/language-reference/anonymous-records.md)gibi F # türleri.
* <xref:System.Dynamic.ExpandoObject>
* <xref:System.TimeZoneInfo>
* <xref:System.Numerics.BigInteger>
* <xref:System.TimeSpan>
* <xref:System.DBNull>
* <xref:System.Type>
* <xref:System.ValueTuple>ve ilişkili genel türleri

Özel dönüştürücüler, yerleşik desteği olmayan türler için uygulanabilir.

### <a name="quoted-numbers"></a>Tırnak işaretli sayılar

`Newtonsoft.Json`JSON dizeleri (tırnak içine alınmış) tarafından temsil edilen sayıları seri hale getirme veya seri durumdan çıkarma. Örneğin, yerine şunları kabul edebilir: `{"DegreesCelsius":"23"}` `{"DegreesCelsius":23}`. İçindeki <xref:System.Text.Json>bu davranışı etkinleştirmek için, aşağıdaki örneğe benzer bir özel dönüştürücü uygulayın. Dönüştürücü şu şekilde `long`tanımlanan özellikleri işler:

* Onları JSON dizeleri olarak serileştirir.
* Seri durumdan çıkarılırken, tırnak içindeki JSON numaralarını ve sayıları kabul eder.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/LongToStringConverter.cs)]

Tek tek `long` özelliklerde [bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) veya [çeviriciyi](system-text-json-converters-how-to.md#registration-sample---converters-collection) <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyona ekleyerek bu özel dönüştürücüyü kaydettirin.

### <a name="dictionary-with-non-string-key"></a>Dize olmayan anahtarla sözlük

`Newtonsoft.Json`türündeki `Dictionary<TKey, TValue>`koleksiyonları destekler. ' Deki <xref:System.Text.Json> sözlük koleksiyonları için yerleşik destek ile `Dictionary<string, TValue>`sınırlıdır. Diğer bir deyişle, anahtar bir dize olmalıdır.

Anahtar olarak bir tamsayı veya diğer tür ile bir sözlüğü desteklemek için, [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#support-dictionary-with-non-string-key)bölümünde örnek gibi bir dönüştürücü oluşturun.

### <a name="polymorphic-serialization"></a>Polimorfik serileştirme

`Newtonsoft.Json`otomatik olarak polimorfik serileştirme yapar. ' Nin sınırlı çok <xref:System.Text.Json>biçimli serileştirme özellikleri hakkında daha fazla bilgi için bkz. [türetilmiş sınıfların serileştirme özellikleri](system-text-json-how-to.md#serialize-properties-of-derived-classes).

Açıklanan geçici çözüm, türü `object`olarak türetilmiş sınıflar içerebilen özellikleri tanımlamaktır. Bu mümkün değilse, diğer bir seçenek de [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#support-polymorphic-deserialization)içindeki örnek gibi `Write` tüm devralma türü hiyerarşisi için bir yöntemle dönüştürücü oluşturmaktır.

### <a name="polymorphic-deserialization"></a>Polimorfik seri kaldırma

`Newtonsoft.Json`serileştirme sırasında `TypeNameHandling` JSON 'a tür adı meta verileri ekleyen bir ayara sahiptir. Seri durumdan çıkarma sırasında çok biçimli seri kaldırma işlemi yaparken meta verileri kullanır. <xref:System.Text.Json>çok sayıda [polimorfik serileştirme](system-text-json-how-to.md#serialize-properties-of-derived-classes) , ancak polimorfik seri hale getirme işlemi yapabilir.

Polimorfik serisini desteklemek için [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#support-polymorphic-deserialization)bölümünde örnek gibi bir dönüştürücü oluşturun.

### <a name="deserialization-of-object-properties"></a>Nesne özelliklerinin serisini kaldırma

Seri `Newtonsoft.Json` <xref:System.Object>hale geldiğinde:

* , JSON yükünde `null`(dışındaki) ilkel değerlerin türünü ve depolanan `string`, `long`, `double`, `boolean`veya `DateTime` paketlenmiş nesne olarak döndürür. *İlkel değerler* , JSON numarası, dize, `true`, `false`veya `null`gibi tek JSON değerleridir.
* JSON yükünde `JObject` karmaşık `JArray` değerler için bir veya döndürür. *Karmaşık değerler* , küme ayracı (`{}`) içinde JSON anahtar-değer çiftleri veya köşeli ayraç (`[]`) içindeki değer listelerinde yer alan koleksiyonlardır. Küme ayraçları ve köşeli ayraçlar içindeki Özellikler ve değerler ek özelliklere veya değerlere sahip olabilir.
* Yükün `null` JSON sabit değeri olduğunda bir null başvurusu döndürür.

<xref:System.Text.Json>seri durumdan çıkarma `JsonElement` sırasında hem ilkel hem de karmaşık değerler için paketlenmiş <xref:System.Object>bir depolar, örneğin:

* Bir `object` özellik.
* `object` Sözlük değeri.
* Bir `object` dizi değeri.
* Bir kök `object`.

Ancak, `System.Text.Json` ile `null` aynı şekilde `Newtonsoft.Json` davranır ve yük içindeki `null` JSON değişmez değeri olduğunda bir null başvurusu döndürür.

Özellikler için `object` tür çıkarımı uygulamak için, [özel dönüştürücüler yazma](system-text-json-converters-how-to.md#deserialize-inferred-types-to-object-properties)bölümünde örnek gibi bir dönüştürücü oluşturun.

### <a name="deserialize-null-to-non-nullable-type"></a>Null olamayan tür için null serisini kaldırma

`Newtonsoft.Json`Aşağıdaki senaryoda özel durum oluşturmaz:

* `NullValueHandling``Ignore`, olarak ayarlanır ve
* Seri durumdan çıkarma sırasında JSON null yapılamayan bir değer türü için null değer içerir.

Aynı senaryoda <xref:System.Text.Json> bir özel durum oluşturur. (Karşılık gelen null işleme ayarı <xref:System.Text.Json.JsonSerializerOptions.IgnoreNullValues?displayProperty=nameWithType>.)

Hedef türün sahibiyseniz, en iyi geçici çözüm, özelliğin boş değer atanabilir olması (örneğin, olarak `int` `int?`değiştirin).

Farklı bir geçici çözüm, türler için `DateTimeOffset` null değerleri işleyen aşağıdaki örnek gibi tür için bir dönüştürücü hale getirme örneğidir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetNullHandlingConverter.cs)]

Bu özel dönüştürücüyü [, özellik üzerindeki bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-property) veya [dönüştürücüyü](system-text-json-converters-how-to.md#registration-sample---converters-collection) <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyona ekleyerek kaydettirin.

**Note:** Yukarıdaki dönüştürücü, varsayılan değerleri belirten POCOs `Newtonsoft.Json` için, **null değerleri farklı işler** . Örneğin, aşağıdaki kodun hedef nesneniz temsil ettiğini varsayalım:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithDefault)]

Ve önceki dönüştürücüyü kullanarak aşağıdaki JSON 'nin seri durumdan çıkarıldığını varsayalım:

```json
{
  "Date": null,
  "TemperatureCelsius": 25,
  "Summary": null
}
```

Seri durumdan çıktıktan sonra `Date` , özelliği 1/1/0001 (`default(DateTimeOffset)`) değerini içerir, diğer bir deyişle, oluşturucuda ayarlanan değerin üzerine yazılır. Aynı POCO ve JSON olarak verildiğinde, `Newtonsoft.Json` seri durumdan çıkarma `Date` özelliğinde 1/1/2001 ' i bırakır.

### <a name="deserialize-to-immutable-classes-and-structs"></a>Sabit sınıflar ve yapılar için seri durumdan çıkarma

`Newtonsoft.Json`parametreleri olan oluşturucuları kullanabilmesi için, sabit sınıflar ve yapılar için seri hale getirebilirsiniz. <xref:System.Text.Json>yalnızca ortak parametresiz oluşturucuları destekler. Geçici bir çözüm olarak, özel bir dönüştürücüde parametreleri olan bir Oluşturucu çağırabilirsiniz.

İşte birden çok Oluşturucu parametresi olan değişmez bir struct:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePoint.cs#ImmutablePoint)]

İşte bu yapıyı seri hale getirir ve seri hale getirir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ImmutablePointConverter.cs)]

[Dönüştürücüyü](system-text-json-converters-how-to.md#registration-sample---converters-collection) <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyona ekleyerek bu özel dönüştürücüyü kaydedin.

Açık genel özellikleri işleyen benzer dönüştürücünün bir örneği için bkz. [anahtar-değer çiftleri için yerleşik dönüştürücü](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters/JsonValueConverterKeyValuePair.cs).

### <a name="specify-constructor-to-use"></a>Kullanılacak oluşturucuyu belirtin

`Newtonsoft.Json` Özniteliği bir poco 'ya seri durumdan çıkarılırken hangi oluşturucunun çağrılacağını belirtmenizi `[JsonConstructor]` sağlar. <xref:System.Text.Json>yalnızca parametresiz oluşturucuları destekler. Geçici bir çözüm olarak, özel bir dönüştürücüde hangi oluşturucuyu ihtiyacınız olduğunu çağırabilirsiniz. [Sabit sınıflar ve yapılar Için seri durumdan çıkarma](#deserialize-to-immutable-classes-and-structs)örneğine bakın.

### <a name="required-properties"></a>Gerekli özellikler

' `Newtonsoft.Json`De, özniteliği için `Required` `[JsonProperty]` bir özelliğin gerekli olduğunu belirtirsiniz. `Newtonsoft.Json`JSON içinde gerekli olarak işaretlenmiş bir özellik için hiçbir değer alınmadığında bir özel durum oluşturur.

<xref:System.Text.Json>hedef türün özelliklerinden biri için hiçbir değer alınmazsa özel durum oluşturmaz. Örneğin, bir `WeatherForecast` sınıfınız varsa:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

Aşağıdaki JSON, hata olmadan seri durumdan çıkarılacak:

```json
{
    "TemperatureCelsius": 25,
    "Summary": "Hot"
}
```

JSON içinde herhangi `Date` bir özellik yoksa seriyi kaldırma başarısız olması için özel bir dönüştürücü uygulayın. Aşağıdaki örnek dönüştürücü kodu, seri kaldırma tamamlandıktan sonra `Date` özellik ayarlanmamışsa bir özel durum oluşturur:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastRequiredPropertyConverter.cs)]

[POCO sınıfında bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) veya [dönüştürücüyü](system-text-json-converters-how-to.md#registration-sample---converters-collection) <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyona ekleyerek bu özel dönüştürücüyü kaydettirin.

Bu kalıbı izlerseniz, veya <xref:System.Text.Json.JsonSerializer.Serialize%2A> <xref:System.Text.Json.JsonSerializer.Deserialize%2A>özyinelemeli olarak çağrılırken Options nesnesini geçirmeyin. Options nesnesi <xref:System.Text.Json.JsonSerializerOptions.Converters%2A> koleksiyonu içerir. Veya `Deserialize`' a geçirirseniz, özel `Serialize` dönüştürücü kendi kendine çağrı yapar ve yığın taşması özel durumuna neden olan sonsuz bir döngü sağlar. Varsayılan seçenekler uygun değilse, gereken ayarlarla seçeneklerin yeni bir örneğini oluşturun. Her yeni örnek bağımsız olarak önbelleğe aldığından bu yaklaşım yavaş olur.

Yukarıdaki dönüştürücü kodu basitleştirilmiş bir örnektir. Öznitelikleri (örneğin, [[Jsonıgnore]](xref:System.Text.Json.Serialization.JsonIgnoreAttribute) veya farklı seçenekler (özel kodlayıcılar gibi) işlemeniz gerekiyorsa ek mantık gerekir. Ayrıca, örnek kod, oluşturucuda varsayılan bir değer ayarlanan özellikleri işlemez. Bu yaklaşım aşağıdaki senaryolar arasında ayrım yapmaz:

* JSON 'da bir özellik eksik.
* Null atanamaz bir tür için bir özellik JSON içinde bulunur, ancak değer, türü için sıfır gibi varsayılan değerdir `int`.
* JSON 'da null olabilen bir değer türü özelliği var, ancak değer null.

### <a name="conditionally-ignore-a-property"></a>Özelliği koşullu olarak Yoksay

`Newtonsoft.Json`serileştirme veya seri durumdan çıkarma için bir özelliği koşullu olarak yoksaymanın birkaç yolu vardır:

* `DefaultContractResolver`Rastgele ölçütlere göre dahil edilecek veya hariç tutulacak özellikleri seçmenizi sağlar.
* Ve `NullValueHandling` `DefaultValueHandling` ayarları, tüm `JsonSerializerSettings` null değer veya varsayılan değer özelliklerinin yoksayılmasını belirtmenize izin verir.
* Öznitelikteki `DefaultValueHandling` ve ayarları, `NullValueHandling` null veya varsayılan değer olarak ayarlandığında yoksayılacak tek tek özellikleri belirtmenize izin verir. `[JsonProperty]`

<xref:System.Text.Json>serileştirilirken özellikleri atlamak için aşağıdaki yolları sağlar:

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

Dönüştürücü, değeri null `Summary` , boş bir dize veya "N/A" ise, özelliğin Serileştirmeden atlanmasına neden olur.

Bu özel dönüştürücüyü [sınıfında bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) veya [dönüştürücüyü](system-text-json-converters-how-to.md#registration-sample---converters-collection) <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyona ekleyerek kaydedin.

Bu yaklaşım aşağıdaki durumlarda ek mantık gerektirir:

* POCO, karmaşık özellikler içerir.
* Gibi öznitelikleri `[JsonIgnore]` veya özel kodlayıcılar gibi seçenekleri işlemeniz gerekir.

### <a name="specify-date-format"></a>Tarih biçimini belirtin

`Newtonsoft.Json`, `DateTime` ve `DateTimeOffset` türlerinin özelliklerinin serileştirilme ve seri durumdan çıkarılme biçimini denetlemek için çeşitli yollar sağlar:

* Ayar `DateTimeZoneHandling` , tüm `DateTime` değerleri UTC tarihleri olarak seri hale getirmek için kullanılabilir.
* Ayar `DateFormatString` ve `DateTime` dönüştürücüler, tarih dizelerinin biçimini özelleştirmek için kullanılabilir.

' <xref:System.Text.Json>De, yerleşik desteği olan tek biçim ISO 8601-1:2019 ' dir ve bu yana büyük ölçüde benimsediğinden ve tam olarak gidiş dönüş yaptığından emin olur. Başka bir biçim kullanmak için özel bir dönüştürücü oluşturun. Daha fazla bilgi için bkz. [System. Text. JSON Içinde DateTime ve DateTimeOffset desteği](../datetime/system-text-json-support.md).

### <a name="callbacks"></a>Geri Çağırmalar

`Newtonsoft.Json`serileştirme veya seri kaldırma işleminde özel kodu birkaç noktada yürütmenize imkan tanır:

* Onserisini kaldırma (bir nesnenin serisini kaldırmada başlayan)
* Onseri durumdan çıkarılan (bir nesnenin serisini kaldırma tamamlandığında)
* Onserileştirilme (bir nesne seri hale getirilmeye Başlarken)
* Onserileştirilmiş (bir nesne serileştirildiğinde)

' <xref:System.Text.Json>De, özel bir dönüştürücü yazarak geri çağırmaların benzetimini yapabilirsiniz. Aşağıdaki örnek bir POCO için özel dönüştürücüyü gösterir. Dönüştürücü, bir `Newtonsoft.Json` geri aramaya karşılık gelen her bir noktada bir ileti görüntüleyen kodu içerir.

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecastCallbacksConverter.cs)]

Bu özel dönüştürücüyü [sınıfında bir özniteliği kullanarak](system-text-json-converters-how-to.md#registration-sample---jsonconverter-on-a-type) veya [dönüştürücüyü](system-text-json-converters-how-to.md#registration-sample---converters-collection) <xref:System.Text.Json.JsonSerializerOptions.Converters> koleksiyona ekleyerek kaydedin.

Önceki örneği takip eden özel bir dönüştürücü kullanıyorsanız:

* `OnDeserializing` Kodun yeni poco örneğine erişimi yok. Yeni POCO örneğini serisini kaldırma başlangıcında işlemek için, bu kodu POCO yapıcısına koyun.
* Yinelemeli olarak veya `Serialize` `Deserialize`çağrılırken Options nesnesini geçmeyin. Options nesnesi `Converters` koleksiyonu içerir. `Serialize` Veya `Deserialize`' a geçirirseniz, dönüştürücü kullanılır ve yığın taşması özel durumuyla sonuçlanan sonsuz bir döngü oluşturulur.

### <a name="public-and-non-public-fields"></a>Ortak ve genel olmayan alanlar

`Newtonsoft.Json`alanları seri hale getirmek ve seri durumdan çıkarmak için özellikleri. <xref:System.Text.Json>yalnızca ortak özelliklerle birlikte kullanılabilir. Özel dönüştürücüler, bu işlevselliği sağlayabilir.

### <a name="internal-and-private-property-setters-and-getters"></a>İç ve özel özellik ayarlayıcıları ve alıcılar

`Newtonsoft.Json``JsonProperty` özniteliği aracılığıyla özel ve iç özellik ayarlayıcıları ve alıcıları öğeleri kullanılabilir. <xref:System.Text.Json>yalnızca genel ayarlayıcıları destekler. Özel dönüştürücüler, bu işlevselliği sağlayabilir.

### <a name="populate-existing-objects"></a>Mevcut nesneleri doldur

İçindeki `JsonConvert.PopulateObject` `Newtonsoft.Json` yöntemi, bir JSON belgesini, yeni bir örnek oluşturmak yerine, bir sınıfın varolan bir örneğine kaldırma. <xref:System.Text.Json>her zaman varsayılan genel parametresiz oluşturucuyu kullanarak hedef türün yeni bir örneğini oluşturur. Özel dönüştürücüler, var olan bir örneğe serisini kaldıramıyor.

### <a name="reuse-rather-than-replace-properties"></a>Özellikleri değiştirmek yerine yeniden kullan

Ayar `Newtonsoft.Json` `ObjectCreationHandling` , özellikleri içindeki nesnelerin seri durumundan çıkarma sırasında yerine kullanılması gerektiğini belirtmenize olanak tanır. <xref:System.Text.Json>her zaman özelliklerde nesneleri değiştirir.  Özel dönüştürücüler, bu işlevselliği sağlayabilir.

### <a name="add-to-collections-without-setters"></a>Ayarlayıcısız koleksiyonlara Ekle

Seri durumundan çıkarma `Newtonsoft.Json` sırasında, özelliğin ayarlayıcısı olmasa bile nesneleri bir koleksiyona ekler. <xref:System.Text.Json>ayarlayıcıları olmayan özellikleri yoksayar. Özel dönüştürücüler, bu işlevselliği sağlayabilir.

## <a name="scenarios-that-jsonserializer-currently-doesnt-support"></a>JsonSerializer 'ın Şu anda desteklemediği senaryolar

Aşağıdaki senaryolar için geçici çözümler pratik veya mümkün değildir. Bu `Newtonsoft.Json` özelliklerden yararlandıysanız geçiş önemli değişiklikler yapılmadan mümkün olmayacaktır.

### <a name="preserve-object-references-and-handle-loops"></a>Nesne başvurularını koruma ve döngüleri işleme

Varsayılan olarak, `Newtonsoft.Json` değere göre serileştirir. Örneğin, bir nesne aynı `Person` nesneye bir başvuru içeren iki özellik içeriyorsa, bu `Person` nesnenin özelliklerinin değerleri JSON içinde yinelenir.

`Newtonsoft.Json`, başvuruya `PreserveReferencesHandling` göre serileştirmenize olanak sağlayan üzerinde `JsonSerializerSettings` bir ayarı vardır:

* İlk `Person` nesne IÇIN oluşturulan JSON 'a bir tanımlayıcı meta verileri eklenir.
* İkinci `Person` nesne IÇIN oluşturulan JSON, özellik değerleri yerine bu tanımlayıcıya bir başvuru içerir.

`Newtonsoft.Json`Ayrıca, bir `ReferenceLoopHandling` özel durum oluşturmak yerine döngüsel başvuruları yoksaymanıza imkan tanıyan bir ayara sahiptir.

<xref:System.Text.Json>yalnızca değere göre serileştirme destekler ve döngüsel başvurular için bir özel durum oluşturur.

### <a name="systemruntimeserialization-attributes"></a>System. Runtime. Serialization öznitelikleri

<xref:System.Text.Json>, `System.Runtime.Serialization` `DataMemberAttribute` ve `IgnoreDataMemberAttribute`gibi ad alanındaki öznitelikleri desteklemez.

### <a name="octal-numbers"></a>Sekizlik sayılar

`Newtonsoft.Json`sayıları, sekizli sayı olarak önünde sıfır ile değerlendirir. <xref:System.Text.Json>[RFC 8259](https://tools.ietf.org/html/rfc8259) belirtimi bunlara izin vermediğinden önde gelen sıfıra izin vermez.

### <a name="missingmemberhandling"></a>MissingMemberHandling

`Newtonsoft.Json`JSON, hedef türünde eksik olan özellikler içeriyorsa, seri durumdan çıkarma sırasında özel durumlar atmak üzere yapılandırılabilir. <xref:System.Text.Json>[[Jsonextensiondata] özniteliğini](system-text-json-how-to.md#handle-overflow-json)kullandığınız durumlar dışında, JSON 'daki ek özellikleri yoksayar. Eksik üye özelliği için geçici çözüm yoktur.

### <a name="tracewriter"></a>TraceWriter

`Newtonsoft.Json`serileştirme veya seri durumdan çıkarma tarafından `TraceWriter` oluşturulan günlükleri görüntülemek için kullanarak hata ayıklamanıza olanak sağlar. <xref:System.Text.Json>günlüğe kaydetme yapmaz.

## <a name="jsondocument-and-jsonelement-compared-to-jtoken-like-jobject-jarray"></a>JToken (JObject, JArray gibi) ile karşılaştırılan JsonDocument ve JsonElement

<xref:System.Text.Json.JsonDocument?displayProperty=fullName>, var olan JSON yüklerden **salt okunurdur** belge nesne MODELI (DOM) ayrıştırabilme ve derleme olanağı sağlar. DOM, bir JSON yükünde verilere rastgele erişim sağlar. Yükü oluşturan JSON öğelerine <xref:System.Text.Json.JsonElement> tür aracılığıyla erişilebilir. Türü `JsonElement` , JSON metnini ortak .net türlerine dönüştürmek Için API 'ler sağlar. `JsonDocument`bir <xref:System.Text.Json.JsonDocument.RootElement> özellik sunar.

### <a name="jsondocument-is-idisposable"></a>JsonDocument, IDisposable

`JsonDocument`havuza alınmış arabellekte verilerin bellek içi bir görünümünü oluşturur. Bu nedenle, `JObject` veya `JArray` öğelerinden `Newtonsoft.Json`farklı olarak `JsonDocument` , türü `IDisposable` , bir using bloğu içinde kullanılması gerekir.

Yalnızca API 'nizden `JsonDocument` , yaşam süresi sahipliğini aktarmak ve arayan sorumluluğunu atmak istiyorsanız ' ı geri döndürün. Çoğu senaryoda, bu gerekli değildir. Çağıranın tüm JSON belgesi ile çalışması gerekiyorsa, <xref:System.Text.Json.JsonElement.Clone%2A> <xref:System.Text.Json.JsonDocument.RootElement%2A>' ın ' i döndürün. <xref:System.Text.Json.JsonElement> Çağıranın JSON belgesi içinde belirli bir öğeyle çalışması gerekiyorsa, ' <xref:System.Text.Json.JsonElement.Clone%2A> ın ' i döndürün. <xref:System.Text.Json.JsonElement> Ya da `RootElement` bir alt öğeyi doğrudan bir `Clone`olmadan geri döndürülürsünüz, çağıran, kendisine ait `JsonElement` `JsonDocument` olan öğesinden sonra döndürülen öğesine erişemez.

İşte şunları yapmanızı gerektiren bir `Clone`örnek:

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

Yukarıdaki kod, bir `JsonElement` `fileName` özellik içeren bir için bekliyor. JSON dosyasını açar ve bir `JsonDocument`oluşturur. Yöntemi, çağıranın tüm belge ile çalışmak istediğini varsayar, bu yüzden `Clone` öğesinin öğesini döndürür. `RootElement`

Bir `JsonElement` alır ve bir alt öğe döndürüyorsa, alt öğenin bir `Clone` kısmını döndürmek gerekli değildir. Çağıran, geçirilen ' ın `JsonDocument` `JsonElement` ait olduğu canlı tutmanın sorumluluğundadır. Örneğin:

```csharp
public JsonElement ReturnFileName(JsonElement source)
{
   return source.GetProperty("fileName");
}
```

### <a name="jsondocument-is-read-only"></a>JsonDocument salt okunurdur

<xref:System.Text.Json> Dom, JSON öğeleri ekleyemez, kaldıramaz veya değiştiremez. Bu, performans için bu şekilde tasarlanmıştır ve ortak JSON yük boyutlarını (yani, < 1 MB) ayrıştırmak için ayırmaları azaltır. Senaryonuz Şu anda değiştirilebilir bir DOM kullanıyorsa, aşağıdaki geçici çözümlerden biri uygulanabilir olabilir:

* Sıfırdan bir oluşturmak `JsonDocument` için (diğer bir deyişle, varolan bir JSON yükünü `Parse` yöntemine GEÇIRMEDEN), kullanarak JSON metnini yazın `Utf8JsonWriter` ve yeni `JsonDocument`bir yapmak için çıktıyı ayrıştırın.
* Varolan `JsonDocument`bir değişikliği değiştirmek IÇIN, JSON metni yazmak, yazarken değişiklikler yapmak ve yeni `JsonDocument`bir hale getirmek için bu çıkışı ayrıştırmak üzere kullanın.
* Var olan JSON belgelerini `JObject.Merge` , veya `JContainer.Merge` API 'leri `Newtonsoft.Json`ile eşdeğer olacak şekilde birleştirmek için [Bu GitHub sorununa](https://github.com/dotnet/corefx/issues/42466#issuecomment-570475853)bakın.

### <a name="jsonelement-is-a-union-struct"></a>JsonElement bir UNION yapısı

`JsonDocument`bir UNION `RootElement` , HERHANGI bir JSON öğesini <xref:System.Text.Json.JsonElement>kapsayan yapı türü olan türü bir özellik olarak gösterir. `Newtonsoft.Json`,, ve gibi `JObject``JArray` `JToken`adanmış sıradüzenli türler kullanır. `JsonElement`üzerinde arama ve listeleme yapabilecekleriniz vardır ve JSON öğelerini .NET türlerine getirmek `JsonElement` için kullanabilirsiniz.

### <a name="how-to-search-a-jsondocument-and-jsonelement-for-sub-elements"></a>Bir JsonDocument ve JsonElement öğelerini alt öğeler için arama

Bazı sözlüklerde arama yapıldığından `JObject` , `JArray` ya `Newtonsoft.Json` da ' dan veya ' den yararlanarak JSON belirteçlerini arar. Karşılaştırmayla, ' deki `JsonElement` aramalar özellikler için sıralı bir arama gerektirir ve bu nedenle nispeten yavaş olur (örneğin, kullanılırken `TryGetProperty`). <xref:System.Text.Json>Arama süresi yerine ilk ayrıştırma süresini en aza indirmek için tasarlanmıştır. Bu nedenle, bir `JsonDocument` nesnede arama yaparken performansı iyileştirmek için aşağıdaki yaklaşımları kullanın:

* Kendi dizin oluşturma veya döngülerinizi yapmak<xref:System.Text.Json.JsonElement.EnumerateArray%2A> yerine <xref:System.Text.Json.JsonElement.EnumerateObject%2A>yerleşik numaralandırıcıları (ve) kullanın.
* Kullanarak `JsonDocument` `RootElement`her bir özelliğin tamamında sıralı bir arama yapmayın. Bunun yerine, JSON verilerinin bilinen yapısına bağlı olarak iç içe geçmiş JSON nesnelerinde arama yapın. Örneğin `Grade` , `Student` nesnelerde bir özelliği arıyorsanız, özellikler için `Student` `Grade` `JsonElement` `Grade` arama yapmak yerine nesneler üzerinde döngü yapın ve her biri için değerini alın. İkincisini yapmak, aynı verilerin üzerinde gereksiz bir şekilde geçiş oluşmasına neden olur.

Kod örneği için bkz. [veri erişimi Için JsonDocument kullanma](system-text-json-how-to.md#use-jsondocument-for-access-to-data).

## <a name="utf8jsonreader-compared-to-jsontextreader"></a>Utf8JsonReader, JsonTextReader ile karşılaştırılır

<xref:System.Text.Json.Utf8JsonReader?displayProperty=fullName>, UTF-8 kodlu JSON metnine yönelik yüksek performanslı, düşük ayırma, Salt ilet okuyucu, [Readonlyspan\<Byte>](xref:System.ReadOnlySpan%601) veya [readonlysequence\<bayt>](xref:System.Buffers.ReadOnlySequence%601). , `Utf8JsonReader` Özel Çözümleyicileri ve seri hale getiriciler oluşturmak için kullanılabilen alt düzey bir türdür.

Aşağıdaki bölümlerde, kullanımı `Utf8JsonReader`için önerilen programlama düzenleri açıklanmaktadır.

### <a name="utf8jsonreader-is-a-ref-struct"></a>Utf8JsonReader bir başvuru yapısı

`Utf8JsonReader` Tür bir *başvuru yapısı*olduğundan, [belirli sınırlamalar](../../csharp/language-reference/builtin-types/struct.md#ref-struct)vardır. Örneğin, bir sınıf veya yapı üzerinde bir başvuru yapısı dışında bir alan olarak depolanamaz. Yüksek performans elde etmek için, bu tür bir başvuru `ref struct` yapısı olan giriş [readonlyspan\<bayt>](xref:System.ReadOnlySpan%601)önbelleğe alınması gerektiğinden bu tür bir olmalıdır. Ayrıca, bu tür durum taşıdığı için değişebilir olur. Bu nedenle, bunu değere göre değil **ref 'e geçirin** . Değere göre geçirmek bir yapı kopyasının oluşmasına neden olur ve durum değişiklikleri arayan tarafından görülemez. Bu, `Newtonsoft.Json` `JsonTextReader` öğesinden `Newtonsoft.Json` bu yana farklılık gösterir. Başvuru yapıları kullanma hakkında daha fazla bilgi için bkz. [Write Safe ve verimli C# kodu](../../csharp/write-safe-efficient-code.md).

### <a name="read-utf-8-text"></a>UTF-8 metnini oku

Kullanırken en iyi performansı elde etmek için `Utf8JsonReader`, UTF-16 dizeleri yerıne zaten UTF-8 Ile kodlanmış JSON yüklerini okuyun. Kod örneği için bkz. [Utf8JsonReader kullanarak filtre verileri](system-text-json-how-to.md#filter-data-using-utf8jsonreader).

### <a name="read-with-a-stream-or-pipereader"></a>Stream veya Pıpereader ile okuma

, `Utf8JsonReader` Bir UTF-8 kodlu [readonlyspan\<Byte>](xref:System.ReadOnlySpan%601) veya [readonlysequence\<bayt>](xref:System.Buffers.ReadOnlySequence%601) (bir <xref:System.IO.Pipelines.PipeReader>öğesinden okuma sonucu) okumayı destekler.

Zaman uyumlu okuma için, akışın sonuna kadar bir bayt dizisine kadar JSON yükünü okuyabilir ve bunu okuyucuya geçirebilirsiniz. Dizeden okumak için (UTF-16 olarak kodlanır), çağırın <xref:System.Text.Encoding.UTF8>.<xref:System.Text.Encoding.GetBytes%2A> İlk olarak dizeyi bir UTF-8 kodlu bayt dizisine dönüştürme. Ardından bunu öğesine geçirin `Utf8JsonReader`.

`Utf8JsonReader` Girişin JSON metni olduğunu düşündüğü için UTF-8 bayt sırası IŞARETI (BOM) geçersiz JSON olarak kabul edilir. Çağıranın verileri okuyucuya geçirmeden önce onu filtrelemeniz gerekir.

Kod örnekleri için bkz. [Use Utf8JsonReader](system-text-json-how-to.md#use-utf8jsonreader).

### <a name="read-with-multi-segment-readonlysequence"></a>Çok kesimli ReadOnlySequence ile oku

JSON girişi [Readonlyspan\<Byte>](xref:System.ReadOnlySpan%601)ise, okuma döngüsüne gittiğinizde her JSON öğesine okuyucudaki `ValueSpan` özellikten erişilebilir. Ancak, giriş, [Readonlysequence\<bayt>](xref:System.Buffers.ReadOnlySequence%601) (bir <xref:System.IO.Pipelines.PipeReader>' dan okuma sonucu) ise, bazı JSON öğeleri `ReadOnlySequence<byte>` nesnenin birden fazla segmentine Straddle edebilir. Bu öğelere, bir ardışık bellek bloğunun <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> içinden erişilemez. Bunun yerine, giriş `ReadOnlySequence<byte>` olarak çok bölgeli her seferinde, geçerli JSON öğesine <xref:System.Text.Json.Utf8JsonReader.HasValueSequence%2A> nasıl erişebileceğinizi anlamak için okuyucudaki özelliği yoklayın. Önerilen bir model aşağıda verilmiştir:

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

Özellik adı <xref:System.Text.Json.Utf8JsonReader.ValueSpan%2A> aramalarını çağırarak <xref:System.MemoryExtensions.SequenceEqual%2A> bayt başına karşılaştırmalar yapmak için kullanmayın. Bunun <xref:System.Text.Json.Utf8JsonReader.ValueTextEquals%2A> yerine çağırın, çünkü bu yöntem JSON 'da kaçan tüm karakterleri kaldırır. "Ad" adlı bir özelliğin nasıl aranacağını gösteren bir örnek aşağıda verilmiştir:

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetDefineUtf8Var)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ValueTextEqualsExample.cs?name=SnippetUseUtf8Var&highlight=11)]

### <a name="read-null-values-into-nullable-value-types"></a>Null değerleri null yapılabilir değer türlerine oku

`Newtonsoft.Json`döndüren API 'ler sağlar <xref:System.Nullable%601>; örneğin `ReadAsBoolean`, `Null` `TokenType` bir `bool?`döndürür. Yerleşik `System.Text.Json` API 'ler yalnızca null yapılamayan değer türleri döndürüyor. Örneğin, <xref:System.Text.Json.Utf8JsonReader.GetBoolean%2A?displayProperty=nameWithType> bir `bool`döndürür. JSON içinde bulursa `Null` bir özel durum oluşturur. Aşağıdaki örneklerde, bir tane null yapılabilir değer türü döndürerek ve bir tane varsayılan değeri döndürerek, null değerlerini işlemek için iki yol gösterilmektedir:

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

Belirli hedef çerçeveler için kullanmaya `Newtonsoft.Json` devam etmeniz gerekiyorsa, çoklu hedefleyebilir ve iki uygulamanız vardır. Ancak, bu önemsiz değildir ve bazı `#ifdefs` ve kaynak yinelemesi gerektirir. Mümkün olduğunca çok kodu paylaşmanın bir `ref struct` yolu, ve `Utf8JsonReader` `Newtonsoft.Json` `JsonTextReader`etrafında bir sarmalayıcı oluşturmaktır. Bu sarmalayıcı, davranış farklarını yalıtma sırasında genel yüzey alanını birleştirecektir. Bu, değişiklikleri öncelikle tür oluşturma ile birlikte ayırmanızı sağlar ve yeni türü başvuruya göre geçirerek. Bu, [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) kitaplığı 'nın izlediği düzendir:

* [UnifiedJsonReader.JsonTextReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.JsonTextReader.cs)
* [UnifiedJsonReader.Utf8JsonReader.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonReader.Utf8JsonReader.cs)

## <a name="utf8jsonwriter-compared-to-jsontextwriter"></a>Utf8JsonWriter, JsonTextWriter ile karşılaştırılır

<xref:System.Text.Json.Utf8JsonWriter?displayProperty=fullName>, `String` `Int32`ve `DateTime`gibi ortak .net türlerinden UTF-8 kodlu JSON metni yazmanın yüksek performanslı bir yoludur. Yazıcı, özel serileştiriciler oluşturmak için kullanılabilen alt düzey bir türdür.

Aşağıdaki bölümlerde, kullanımı `Utf8JsonWriter`için önerilen programlama düzenleri açıklanmaktadır.

### <a name="write-with-utf-8-text"></a>UTF-8 metniyle yazma

Kullanırken en iyi performansı elde etmek için `Utf8JsonWriter`, Write JSON yüklerini UTF-16 DIZELERI yerine UTF-8 ile kodlanmış olarak yazın. Bilinen <xref:System.Text.Json.JsonEncodedText> dize özellik adlarını ve değerlerini sıra olarak önbelleğe almak ve önceden kodlamak için kullanın ve UTF-16 dize sabit değerleri kullanmak yerine yazıcıya geçirin. Bu, önbelleğe alma ve UTF-8 bayt dizilerini kullanmayla daha hızlıdır.

Özel kaçış yapmanız gerekiyorsa bu yaklaşım da geçerlidir. `System.Text.Json`bir dize yazarken kaçış özelliğini devre dışı bırakmanızı sağlar. Bununla birlikte <xref:System.Text.Encodings.Web.JavaScriptEncoder> , yazıcıya kendi özel bir seçenek olarak geçirebilirsiniz ya da kaçış yapmak için kendi uygulamanızı `JsonEncodedText` `JavascriptEncoder` kullanarak kendi öğesini oluşturabilir ve sonra dize `JsonEncodedText` yerine yazın. Daha fazla bilgi için bkz. [karakter kodlamasını özelleştirme](system-text-json-how-to.md#customize-character-encoding).

### <a name="write-raw-values"></a>Ham değerleri yaz

Yöntemi `Newtonsoft.Json` `WriteRawValue` , bir değerin beklenildiği ham JSON yazar. <xref:System.Text.Json>doğrudan eşdeğeri yoktur, ancak şu şekilde yalnızca geçerli JSON yazılmasını sağlayan bir geçici çözüm verilmiştir:

```csharp
using JsonDocument doc = JsonDocument.Parse(string);
doc.WriteTo(writer);
```

### <a name="customize-character-escaping"></a>Karakter kaçış 'yi özelleştirme

[Stringescapehandling](https://www.newtonsoft.com/json/help/html/T_Newtonsoft_Json_StringEscapeHandling.htm) AYARı, ASCII `JsonTextWriter` olmayan tüm karakterleri **veya** HTML karakterlerinin kaçış seçeneklerini sunar. Varsayılan olarak, `Utf8JsonWriter` ASCII olmayan **ve** HTML karakterlerinin hepsini çıkar. Bu kaçış, derinlemesine savunma güvenlik nedenleriyle yapılır. Farklı bir kaçış ilkesi belirtmek için, oluşturun <xref:System.Text.Encodings.Web.JavaScriptEncoder> ve ayarlayın. <xref:System.Text.Json.JsonWriterOptions.Encoder?displayProperty=nameWithType> Daha fazla bilgi için bkz. [karakter kodlamasını özelleştirme](system-text-json-how-to.md#customize-character-encoding).

### <a name="customize-json-format"></a>JSON biçimini Özelleştir

`JsonTextWriter`eşdeğeri olmayan, için `Utf8JsonWriter` aşağıdaki ayarları içerir:

* [Girintileme](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_Indentation.htm) -girintilemek için kaç karakter kullanılacağını belirtir. `Utf8JsonWriter`her zaman 2 karakterlik girintileme yapar.
* [Inztchar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_IndentChar.htm) -girintileme için kullanılacak karakteri belirtir.  `Utf8JsonWriter`her zaman boşluk kullanır.
* [QuoteChar](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteChar.htm) -dize değerlerini çevrelemek için kullanılacak karakteri belirtir.  `Utf8JsonWriter`her zaman çift tırnak kullanır.
* [QUOTENAME](https://www.newtonsoft.com/json/help/html/P_Newtonsoft_Json_JsonTextWriter_QuoteName.htm) -özellik adlarının tırnak işaretleriyle saranıp çevrelenmeyeceğini belirtir.  `Utf8JsonWriter`her zaman tırnak işaretleriyle çevreler.

Tarafından `Utf8JsonWriter` üretilen JSON 'yi bu şekillerde özelleştirmenizi sağlayan geçici çözümler yoktur.

### <a name="write-null-values"></a>Null değerleri yaz

Kullanarak `Utf8JsonWriter`null değerler yazmak için şunu çağırın:

* <xref:System.Text.Json.Utf8JsonWriter.WriteNull%2A>değer olarak null ile bir anahtar-değer çifti yazmak.
* <xref:System.Text.Json.Utf8JsonWriter.WriteNullValue%2A>JSON dizisinin bir öğesi olarak null yazmak için.

Dize özelliği için <xref:System.Text.Json.Utf8JsonWriter.WriteString%2A> , dize null <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A> ise ve `WriteNull` ile `WriteNullValue`eşdeğerdir.

### <a name="write-timespan-uri-or-char-values"></a>TimeSpan, Uri veya Char değerlerini yaz

`JsonTextWriter`TimeSpan `WriteValue` , [Uri](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_22.htm)ve [char](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_3.htm) değerleri için yöntemler sağlar. [TimeSpan](https://www.newtonsoft.com/json/help/html/M_Newtonsoft_Json_JsonTextWriter_WriteValue_18.htm) `Utf8JsonWriter`eşdeğer yöntemlere sahip değildir. Bunun yerine, bu değerleri dizeler olarak biçimlendirin (örneğin `ToString()`, çağırarak) ve çağırın <xref:System.Text.Json.Utf8JsonWriter.WriteStringValue%2A>.

### <a name="multi-targeting"></a>Çoklu hedefleme

Belirli hedef çerçeveler için kullanmaya `Newtonsoft.Json` devam etmeniz gerekiyorsa, çoklu hedefleyebilir ve iki uygulamanız vardır. Ancak, bu önemsiz değildir ve bazı `#ifdefs` ve kaynak yinelemesi gerektirir. Mümkün olduğunca çok kodu paylaşmanın bir yolu, ve `Utf8JsonWriter` `Newtonsoft` `JsonTextWriter`etrafında bir sarmalayıcı oluşturmaktır. Bu sarmalayıcı, davranış farklarını yalıtma sırasında genel yüzey alanını birleştirecektir. Bu, değişiklikleri genellikle türün yapılacağı şekilde yalıtmanızı sağlar. [Microsoft. Extensions. DependencyModel](https://www.nuget.org/packages/Microsoft.Extensions.DependencyModel/3.1.0/) kitaplığı aşağıdaki gibidir:

* [UnifiedJsonWriter.JsonTextWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.JsonTextWriter.cs)
* [UnifiedJsonWriter.Utf8JsonWriter.cs](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/installer/managed/Microsoft.Extensions.DependencyModel/UnifiedJsonWriter.Utf8JsonWriter.cs)

## <a name="additional-resources"></a>Ek kaynaklar

<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)[Restore this when the roadmap is updated.]-->
* [System.Text.Jsonbakýþ](system-text-json-overview.md)
* [Nasıl kullanılırSystem.Text.Json](system-text-json-how-to.md)
* [Özel dönüştürücü yazma](system-text-json-converters-how-to.md)
* [İçinde DateTime ve DateTimeOffset desteğiSystem.Text.Json](../datetime/system-text-json-support.md)
* [System.Text.JsonAPI başvurusu](xref:System.Text.Json)
* [System.Text.Json. Serileştirme API başvurusu](xref:System.Text.Json.Serialization)
