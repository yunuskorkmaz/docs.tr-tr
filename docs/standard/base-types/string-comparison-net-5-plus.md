---
title: .NET 5 + ' da dizeleri karşılaştırırken davranış değişiklikleri
description: .NET 5 ve sonraki Windows sürümlerindeki dize karşılaştırma davranışı değişiklikleri hakkında bilgi edinin.
ms.date: 12/07/2020
ms.openlocfilehash: a53c36b31785fb43c0aa5f5040042abb6d40031a
ms.sourcegitcommit: 45c7148f2483db2501c1aa696ab6ed2ed8cb71b2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96851757"
---
# <a name="behavior-changes-when-comparing-strings-on-net-5"></a>.NET 5 + ' da dizeleri karşılaştırırken davranış değişiklikleri

.NET 5,0, genelleştirme API 'Lerinin artık tüm desteklenen platformlar arasında [Varsayılan olarak ICU 'yi kullandığı](../../core/compatibility/globalization/5.0/icu-globalization-api.md) bir çalışma zamanı davranış değişikliği sunar. Bu, önceki .NET Core sürümlerinden ve Windows üzerinde çalışırken işletim sisteminin ulusal dil desteği (NLS) işlevselliğini kullanan .NET Framework bir sistemdir. Bu değişiklikler hakkında daha fazla bilgi için, davranış değişikliğini alan uyumluluk anahtarları dahil, bkz. [.NET Genelleştirme ve ıCU](../globalization-localization/globalization-icu.md).

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, birleştirme için sunulmuştur. Tüm desteklenen işletim sistemleri genelinde NET ' in Genelleştirme davranışı. Ayrıca, uygulamaların işletim sisteminin yerleşik kitaplıklarına göre değil, kendi Genelleştirme kitaplıklarını paketleyebilme olanağı da sağlar. Daha fazla bilgi için bkz. [Son değişiklik bildirimi](../../core/compatibility/globalization/5.0/icu-globalization-api.md).

## <a name="behavioral-differences"></a>Davranış farkları

`string.IndexOf(string)`Bir bağımsız değişken alan aşırı yüklemeyi çağırmadan gibi işlevleri kullanırsanız <xref:System.StringComparison> , bir *sıra* araması gerçekleştirmeyi düşünebilirsiniz, bunun yerine kültüre özgü davranışa istemeden bir bağımlılık yapmanız gerekir. NLS ve ıCU, dil karşılaştırıcılarında farklı mantık uygulamayı yaptığından, gibi yöntemlerin sonuçları `string.IndexOf(string)` beklenmedik değerler döndürebilir.

Bu, her zaman Genelleştirme tesislerinin etkin olmasını beklemeyen yerlerde bile kendi kendine bildirimde bulunabilir. Örneğin, aşağıdaki kod, geçerli çalışma zamanına bağlı olarak farklı bir yanıt oluşturabilir.

```cs
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);

// The snippet prints:
//
// '6' when running on .NET Framework (Windows)
// '6' when running on .NET Core 2.x - 3.x (Windows)
// '-1' when running on .NET 5 (Windows)
// '-1' when running on .NET Core 2.x - 3.x or .NET 5 (non-Windows)
// '6' when running on .NET Core 2.x or .NET 5 (in invariant mode)
```

## <a name="guard-against-unexpected-behavior"></a>Beklenmeyen davranışa karşı koruma

Bu bölümde, .NET 5,0 ' deki beklenmedik davranış değişiklikleriyle ilgili iki seçenek sunulmaktadır.

### <a name="enable-code-analyzers"></a>Kod Çözümleyicileri etkinleştir

[Kod Çözümleyicileri](../../fundamentals/code-analysis/overview.md) , muhtemelen önemlidir çağrı sitelerini algılayabilir. Herhangi bir ortaya çıkacak davranışa karşı koruma sağlamaya yardımcı olmak için, projenizde .NET derleyici platformu (Roslyn) Çözümleyicileri etkinleştirmenizi öneririz. Çözümleyiciler, bir sıralı karşılaştırıcı büyük olasılıkla tasarlandıysa, istemeden bir dil karşılaştırıcısı kullanmanın farkında olabilecek kodu işaret eder. Aşağıdaki kurallar, bu sorunları bayrağa getirmenize yardımcı olmalıdır:

- [CA1307: Daha anlaşılır olması için StringComparison belirtin](../../fundamentals/code-analysis/quality-rules/ca1307.md)
- [CA1309: Sıralı StringComparison kullanın](../../fundamentals/code-analysis/quality-rules/ca1309.md)
- [CA1310: Doğruluk için StringComparison belirtin](../../fundamentals/code-analysis/quality-rules/ca1310.md)

Bu özel kurallar varsayılan olarak etkinleştirilmemiştir. Bunları etkinleştirmek ve derleme hatası olarak herhangi bir ihlali göstermek için, proje dosyanızda aşağıdaki özellikleri ayarlayın:

```xml
<PropertyGroup>
  <AnalysisMode>AllEnabledByDefault</AnalysisMode>
  <WarningsAsErrors>$(WarningsAsErrors);CA1307;CA1309;CA1310</WarningsAsErrors>
</PropertyGroup>
```

Aşağıdaki kod parçacığında ilgili kod Çözümleyicisi uyarılarını veya hatalarını üreten kod örnekleri gösterilmektedir.

```cs
//
// Potentially incorrect code - answer might vary based on locale.
//
string s = GetString();
// Produces analyzer warning CA1310 for string; CA1307 matches on char ','
int idx = s.IndexOf(",");
Console.WriteLine(idx);

//
// Corrected code - matches the literal substring ",".
//
string s = GetString();
int idx = s.IndexOf(",", StringComparison.Ordinal);
Console.WriteLine(idx);

//
// Corrected code (alternative) - searches for the literal ',' character.
//
string s = GetString();
int idx = s.IndexOf(',');
Console.WriteLine(idx);
```

Benzer şekilde, bir dizi dizeyi veya varolan dize tabanlı bir koleksiyonu sıralarken bir açık karşılaştırıcı belirtin.

```cs
//
// Potentially incorrect code - behavior might vary based on locale.
//
SortedSet<string> mySet = new SortedSet<string>();
List<string> list = GetListOfStrings();
list.Sort();

//
// Corrected code - uses ordinal sorting; doesn't vary by locale.
//
SortedSet<string> mySet = new SortedSet<string>(StringComparer.Ordinal);
List<string> list = GetListOfStrings();
list.Sort(StringComparer.Ordinal);
```

### <a name="revert-back-to-nls-behaviors"></a>NLS davranışlarına geri dön

.NET 5 uygulamalarını Windows üzerinde çalışırken eski NLS davranışlarına geri dönmek için [.NET Genelleştirme ve ıCU](../globalization-localization/globalization-icu.md)içindeki adımları izleyin. Bu uygulama genelinde uyumluluk anahtarı, uygulama düzeyinde ayarlanmalıdır. Tek tek kitaplıklar bu davranışı kabul edebilir veya devre dışı bırakılamaz.

> [!TIP]
> Kod durumu 'yı artırmaya ve var olan tüm hata hatalarını bulmaya yardımcı olması için [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md), [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md)ve [CA1310](../../fundamentals/code-analysis/quality-rules/ca1310.md) kod analizi kurallarını etkinleştirmenizi önemle öneririz. Daha fazla bilgi için bkz. [kod Çözümleyicileri etkinleştirme](#enable-code-analyzers).

## <a name="affected-apis"></a>Etkilenen API’ler

.NET 5,0 ' deki değişiklikler nedeniyle .NET uygulamalarının çoğu beklenmeyen davranışlarla karşılaşmaz. Ancak, etkilenen API 'lerin sayısı ve bu API 'Lerin daha geniş .NET ekosistemine ne olduğu konusunda, istenmeyen davranışları ortaya çıkarmak veya uygulamanızda zaten mevcut olan görünmeyen hataları ortaya çıkarmak için .NET 5,0 potansiyelini bilmeniz gerekir.

Etkilenen API 'Ler şunları içerir:

- <xref:System.String.Compare%2A?displayProperty=fullName>
- <xref:System.String.EndsWith%2A?displayProperty=fullName>
- <xref:System.String.IndexOf%2A?displayProperty=fullName>
- <xref:System.String.StartsWith%2A?displayProperty=fullName>
- <xref:System.String.ToLower%2A?displayProperty=fullName>
- <xref:System.String.ToLowerInvariant%2A?displayProperty=fullName>
- <xref:System.String.ToUpper%2A?displayProperty=fullName>
- <xref:System.String.ToUpperInvariant%2A?displayProperty=fullName>
- <xref:System.Globalization.TextInfo?displayProperty=fullName> (çoğu üye)
- <xref:System.Globalization.CompareInfo?displayProperty=fullName> (çoğu üye)
- <xref:System.Array.Sort%2A?displayProperty=fullName> (dize dizilerini sıralarken)
- <xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (liste öğeleri dizeler olduğunda)
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (anahtarlar dizeler olduğunda)
- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (anahtarlar dizeler olduğunda)
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (küme dizeler içerdiğinde)

> [!NOTE]
> Bu, etkilenen API 'lerin ayrıntılı bir listesi değildir.

Yukarıdaki tüm API 'Ler, varsayılan olarak iş parçacığının [geçerli kültürünü](xref:System.Threading.Thread.CurrentCulture)kullanarak *dilsel* dize aramayı ve karşılaştırmayı kullanır. *Dilsel* ve *sıralı* arama ve karşılaştırma arasındaki farklılıklar, [Ordinal ve dilsel arama ve karşılaştırma](#ordinal-vs-linguistic-search-and-comparison)bakımından çağrılır.

ICU, .NET Core veya .NET Framework önceki bir sürümünden .NET 5,0 ' e yükseltme yapan ve etkilenen API 'lerden birini çağıran, API 'lerin farklı davranışlar sergilediğine yönelik olarak, dil dizesi karşılaştırmaları, Microsoft 'un önceki bir sürümünden farklı olan Windows tabanlı uygulamalar 'dan farklı bir şekilde uygular.

### <a name="exceptions"></a>Özel Durumlar

* Bir API açık `StringComparison` veya parametre kabul ediyorsa `CultureInfo` , bu parametre API 'nin varsayılan davranışını geçersiz kılar.
* `System.String` İlk parametrenin türünde olduğu Üyeler `char` (örneğin, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType> ), veya belirten bir açık bağımsız değişken geçirmediği takdirde sıralı arama kullanın `StringComparison` `CurrentCulture[IgnoreCase]` `InvariantCulture[IgnoreCase]` .

Her API 'nin varsayılan davranışının daha ayrıntılı bir analizi için <xref:System.String> , [varsayılan arama ve karşılaştırma türleri](#default-search-and-comparison-types) bölümüne bakın.

## <a name="ordinal-vs-linguistic-search-and-comparison"></a>Ordinal ve dilsel arama ve karşılaştırma

*Sıra sayısı* ( *dil olmayan*) arama ve karşılaştırma, bir dizeyi tek tek öğelerine ayırır ve bir Char- `char` by-char araması veya karşılaştırması gerçekleştirir. Örneğin, `"dog"` `"dog"` *equal* `Ordinal` iki dize tam olarak aynı karakter sırasından bulunduğundan, dizeler ve bir karşılaştırıcı altında eşit olarak karşılaştırın. Ancak, `"dog"` `"Dog"` tam olarak aynı karakter dizisinden oluşmadığından, bir karşılaştırıcı altında *eşit değildir* olarak karşılaştırın `Ordinal` . Diğer bir deyişle, büyük harfli `'D'` kod noktası, `U+0044` küçük harfli kod noktası öncesinde oluşur `'d'` `U+0064` ve daha `"dog"` önce sıralamaya neden olur `"Dog"` .

Bir `OrdinalIgnoreCase` karşılaştırıcı, char-char temelinde hala çalışır, ancak işlemi gerçekleştirirken büyük/küçük harf farklarını ortadan kaldırır. Bir karşılaştırıcı altında char, `OrdinalIgnoreCase` `'d'` `'D'` ve karakter çiftleri ve gibi *eşit* olarak karşılaştırılmaktadır `'á'` `'Á'` . Ancak, vurgusuz karakter, `'a'` aksanlı char *değerine eşit değil* olarak karşılaştırılmaktadır `'á'` .

Bunun bazı örnekleri aşağıdaki tabloda verilmiştir:

| Dize 1 | Dize 2 | `Ordinal` Il | `OrdinalIgnoreCase` Il |
|---|---|---|---|
| `"dog"` | `"dog"` | equal | equal |
| `"dog"` | `"Dog"` | eşit değildir | equal |
| `"resume"` | `"Resume"` | eşit değildir | equal |
| `"resume"` | `"résumé"` | eşit değildir | eşit değildir |

Unicode Ayrıca dizelerin birçok farklı bellek içi gösterimlerine sahip olmasını sağlar. Örneğin, bir e-Acute (é) iki olası şekilde gösterilebilir:

* Tek bir sabit `'é'` karakter (aynı zamanda olarak yazılmış `'\u00E9'` ).
* Vurgulanmış `'e'` aksan değiştirici karakteri ve ardından düz bir aksanlı karakter `'\u0301'` .

Bu, aşağıdaki _dört_ dizenin, `"résumé"` yapısal parçaları farklı olsa da, görüntülendiği zaman bir sonucu olduğu anlamına gelir. Dizeler, değişmez `'é'` karakterlerin veya değişmez değer aksanlı karakterlerin bileşimini ve `'e'` Birleşik vurgu değiştiricisini kullanır `'\u0301'` .

* `"r\u00E9sum\u00E9"`
* `"r\u00E9sume\u0301"`
* `"re\u0301sum\u00E9"`
* `"re\u0301sume\u0301"`

Sıralı karşılaştırıcı altında, Bu dizelerin hiçbiri birbirleriyle eşit olarak karşılaştırılmaktadır. Bunun nedeni, ekranda işlense de, her şey farklı temel karakter dizileri içerse de, hepsi aynı şekilde görünür.

Bir işlem gerçekleştirirken `string.IndexOf(..., StringComparison.Ordinal)` , çalışma zamanı tam bir alt dize eşleşmesi arar. Sonuçlar aşağıdaki gibidir.

```cs
Console.WriteLine("resume".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("resume".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
```

Sıralı arama ve karşılaştırma yordamları, geçerli iş parçacığının kültür ayarından hiçbir şekilde etkilenmez.

*Dilsel* arama ve karşılaştırma yordamları, *harmanlama öğelerine* bir dize ayırır ve bu öğelerde arama veya karşılaştırmalar gerçekleştirir. Bir dizenin karakterleri ile onun bileşen harmanlama öğeleri arasında 1:1 eşleme olması gerekmez. Örneğin, 2 uzunluğunda bir dize yalnızca bir tek harmanlama öğesinden oluşabilir. İki dize dile duyarlı bir biçimde karşılaştırıldığı zaman, karşılaştırıcı, dizenin sabit karakterleri farklı olsa da, iki dizenin harmanlama öğelerinin aynı anlamsal anlamı olup olmadığını denetler.

Dizeyi `"résumé"` ve dört farklı temsilini tekrar düşünün. Aşağıdaki tabloda, harmanlama öğelerine bölünmüş her bir temsil gösterilmektedir.

| Dize | Harmanlama öğeleri olarak |
|---|---|
| `"r\u00E9sum\u00E9"` | `"r" + "\u00E9" + "s" + "u" + "m" + "\u00E9"` |
| `"r\u00E9sume\u0301"` | `"r" + "\u00E9" + "s" + "u" + "m" + "e\u0301"` |
| `"re\u0301sum\u00E9"` | `"r" + "e\u0301" + "s" + "u" + "m" + "\u00E9"` |
| `"re\u0301sume\u0301"` | `"r" + "e\u00E9" + "s" + "u" + "m" + "e\u0301"` |

Harmanlama öğesi, okuyucuların tek bir karakter veya karakter kümesi olarak düşündüklerini gevşektir. Bu, kavramsal olarak bir [grafem kümesine](character-encoding-introduction.md#grapheme-clusters) benzer ancak biraz daha büyük bir şemsiye kapsar.

Bir dil karşılaştırıcısı altında, tam eşleşmeler gerekli değildir. Harmanlama öğeleri anlam anlamlarına göre karşılaştırılır. Örneğin, bir dil karşılaştırıcısı, `"\u00E9"` `"e\u0301"` her ikisi de "dar vurgu değiştiricisi ile küçük harf e" olarak kullanıldığından, alt dizeleri ve eşit olarak davranır. Bu yöntem, `IndexOf` `"e\u0301"` `"\u00E9"` Aşağıdaki kod örneğinde gösterildiği gibi, anlam ile eşdeğer alt dizeyi içeren daha büyük bir dizedeki alt dizeden eşleşmesi için yönteminin kullanılmasına izin verir.

```cs
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e")); // prints '-1' (not found)
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e\u00E9")); // prints '1'
Console.WriteLine("\u00E9".IndexOf("e\u00E9")); // prints '0'
```

Bunun sonucunda, bir dil karşılaştırması kullanılıyorsa farklı uzunluklardan oluşan iki dize eşit olarak karşılaştırılabilir. Çağıranlar, bu tür senaryolarda dize uzunluğu ile ilgilenen özel durum mantığına dikkat edilmelidir.

*Kültüre duyarlı* arama ve karşılaştırma yordamları, dil arama ve karşılaştırma yordamlarının özel bir biçimidir. Kültüre duyarlı bir karşılaştırıcı kapsamında, harmanlama öğesi kavramı, belirtilen kültüre özgü bilgileri içerecek şekilde genişletilir.

Örneğin, [Macarca alfabede](https://en.wikipedia.org/wiki/Hungarian_alphabet)iki karakter geri döndüğünüzde \<dz\> , ya da veya birbirinden farklı olan benzersiz mektuplardan ayrı olarak değerlendirilir \<d\> \<z\> . Bu \<dz\> , bir dize içinde görüldüğünde, bir Macarca kültüre duyarlı bir karşılaştırıcının tek bir harmanlama öğesi olarak davrandığı anlamına gelir.

| Dize | Harmanlama öğeleri olarak | Açıklamalar |
|---|---|---|
| `"endz"` | `"e" + "n" + "d" + "z"` | (Standart bir dil karşılaştırıcısı kullanarak) |
| `"endz"` | `"e" + "n" + "dz"` | (Macarca kültüre duyarlı bir karşılaştırıcı kullanarak) |

Bir Macarca kültüre duyarlı bir karşılaştırıcı kullanırken bu, dizenin alt `"endz"` dizeden *bitmediği* anlamına gelir `"z"` , çünkü < \dz \> ve < \z, \> farklı anlam anlamı olan harmanlama öğeleri olarak değerlendirilir.

```cs
// Set thread culture to Hungarian
CultureInfo.CurrentCulture = CultureInfo.GetCultureInfo("hu-HU");
Console.WriteLine("endz".EndsWith("z")); // Prints 'False'

// Set thread culture to invariant culture
CultureInfo.CurrentCulture = CultureInfo.InvariantCulture;
Console.WriteLine("endz".EndsWith("z")); // Prints 'True'
```

> [!NOTE]
>
> - Davranış: dilsel ve kültüre duyarlı karşılaştırıcılarla, zaman zaman davranış ayarlamalarını olumsuz şekilde gerçekleştirebilir. Hem ıCU hem de eski Windows NLS özelliği, dünya dillerinin nasıl değişdiklerini hesaba göre güncelleştirilir. Daha fazla bilgi için bkz. Web günlüğü gönderi [yerel ayar (kültür) veri karmaşası](/archive/blogs/shawnste/locale-culture-data-churn). *Sıralı* karşılaştırıcı davranışı, tam bit düzeyinde arama ve karşılaştırma gerçekleştirdiğinden dolayı hiçbir şekilde değişmeyecektir. Bununla birlikte, daha fazla karakter kümesi kapsayacak şekilde Unicode büyüdükçe ve mevcut büyük küçük harf verilerinde da ihmallerinden 'yi düzelterek *OrdinalIgnoreCase* karşılaştırıcı davranışı değişebilir.
> - Kullanım: karşılaştırıcılarla `StringComparison.InvariantCulture` ve `StringComparison.InvariantCultureIgnoreCase` kültüre duyarlı olmayan dil Karşılaştırıcılar. Diğer bir deyişle, bu Karşılaştırıcılar, birden çok olası temel temsilde sahip olan ve bu tür temsillerin eşit olarak değerlendirilme karakteri gibi kavramları anlamalıdır. Ancak kültüre duyarlı olmayan dil Karşılaştırıcılar \<dz\> \<d\> \<z\> , yukarıda gösterildiği gibi veya ' den farklı olarak özel işleme içermez. Ayrıca, Almanya Eszett (ß) gibi özel durum karakterleri de olmaz.

.NET ayrıca *sabit Genelleştirme modunu* da sunmaktadır. Bu katılım modu, dilsel arama ve karşılaştırma yordamlarına yönelik kod yollarını devre dışı bırakır. Bu modda tüm işlemler, *Ordinal* *OrdinalIgnoreCase* `CultureInfo` `StringComparison` çağıranın sağladığı veya bağımsız değişkenden bağımsız olarak Ordinal veya OrdinalIgnoreCase davranışları kullanır. Daha fazla bilgi için bkz. Genelleştirme ve [.NET Core Genelleştirme sabit modu](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md) [için çalışma zamanı yapılandırma seçenekleri](../../core/run-time-config/globalization.md) .

Daha fazla bilgi için bkz. [.net 'teki dizeleri karşılaştırmak Için en iyi uygulamalar](best-practices-strings.md).

## <a name="security-implications"></a>Güvenlik üzerindeki etkileri

Uygulamanız filtreleme için etkilenen bir API kullanıyorsa, bir sıra araması yerine bir dil aramasının yanlışlıkla kullanıldığı yerleri bulmaya yardımcı olması için CA1307 ve CA1309 kod analizi kurallarının etkinleştirilmesini öneririz. Aşağıdakiler gibi kod desenleri güvenlik açıklarına maruz kalabilir.

```cs
//
// THIS SAMPLE CODE IS INCORRECT.
// DO NOT USE IT IN PRODUCTION.
//
public bool ContainsHtmlSensitiveCharacters(string input)
{
    if (input.IndexOf("<") >= 0) { return true; }
    if (input.IndexOf("&") >= 0) { return true; }
    return false;
}
```

`string.IndexOf(string)`Yöntemi varsayılan olarak bir dilsel arama kullandığından, bir dize bir sabit değer `'<'` veya `'&'` karakter içermesi ve `string.IndexOf(string)` yordamın dönmesi için arama alt dizesinin `-1` bulunamadığını gösterir. Kod analizi kuralları CA1307 ve CA1309 bayrağıyla ilgili siteler ve geliştirici olası bir sorun olduğunu bildirir.

## <a name="default-search-and-comparison-types"></a>Varsayılan arama ve karşılaştırma türleri

Aşağıdaki tabloda, çeşitli dize ve dize benzeri API 'Ler için varsayılan arama ve karşılaştırma türleri listelenmektedir. Çağıran açık `CultureInfo` veya `StringComparison` parametre sağlıyorsa, bu parametre varsayılan olarak kabul edilir.

| API | Varsayılan davranış | Açıklamalar |
|---|---|---|
| `string.Compare` | CurrentCulture | |
| `string.CompareTo` | CurrentCulture | |
| `string.Contains` | Sıralı | |
| `string.EndsWith` | Sıralı | (ilk parametre bir olduğunda `char` ) |
| `string.EndsWith` | CurrentCulture | (ilk parametre bir olduğunda `string` ) |
| `string.Equals` | Sıralı | |
| `string.GetHashCode` | Sıralı | |
| `string.IndexOf` | Sıralı | (ilk parametre bir olduğunda `char` ) |
| `string.IndexOf` | CurrentCulture | (ilk parametre bir olduğunda `string` ) |
| `string.IndexOfAny` | Sıralı | |
| `string.LastIndexOf` | Sıralı | (ilk parametre bir olduğunda `char` ) |
| `string.LastIndexOf` | CurrentCulture | (ilk parametre bir olduğunda `string` ) |
| `string.LastIndexOfAny` | Sıralı | |
| `string.Replace` | Sıralı | |
| `string.Split` | Sıralı | |
| `string.StartsWith` | Sıralı | (ilk parametre bir olduğunda `char` ) |
| `string.StartsWith` | CurrentCulture | (ilk parametre bir olduğunda `string` ) |
| `string.ToLower` | CurrentCulture | |
| `string.ToLowerInvariant` | InvariantCulture | |
| `string.ToUpper` | CurrentCulture | |
| `string.ToUpperInvariant` | InvariantCulture | |
| `string.Trim` | Sıralı | |
| `string.TrimEnd` | Sıralı | |
| `string.TrimStart` | Sıralı | |
| `string == string` | Sıralı | |
| `string != string` | Sıralı | |

API 'lerden farklı olarak `string` , tüm `MemoryExtensions` API 'ler varsayılan olarak *sıralı* aramalar ve karşılaştırmalar gerçekleştirerek aşağıdaki özel durumlarla yapılır.

| API | Varsayılan davranış | Açıklamalar |
|---|---|---|
| `MemoryExtensions.ToLower` | CurrentCulture | (null `CultureInfo` bağımsız değişken geçirildiğinde) |
| `MemoryExtensions.ToLowerInvariant` | InvariantCulture | |
| `MemoryExtensions.ToUpper` | CurrentCulture | (null `CultureInfo` bağımsız değişken geçirildiğinde) |
| `MemoryExtensions.ToUpperInvariant` | InvariantCulture | |

Sonuç olarak, kodun tüketme 'den kullanıma dönüştürülmesi `string` `ReadOnlySpan<char>` , davranış değişikliklerinin yanlışlıkla tanıtılmasından bir sonucudur. Buna bir örnek aşağıda verilmiştir.

```cs
string str = GetString();
if (str.StartsWith("Hello")) { /* do something */ } // this is a CULTURE-AWARE (linguistic) comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello")) { /* do something */ } // this is an ORDINAL (non-linguistic) comparison
```

Bunu ele almak için önerilen yol, bu API 'lere açık bir parametre geçirmektir `StringComparison` . CA1307 ve CA1309 kod analizi kuralları buna yardımcı olabilir.

```cs
string str = GetString();
if (str.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison
```

## <a name="see-also"></a>Ayrıca bkz.

- [Genelleştirme son değişiklikleri](../../core/compatibility/globalization.md)
- [.NET 'teki dizeleri karşılaştırmak için en iyi yöntemler](best-practices-strings.md)
- [C 'de dizeleri karşılaştırma #](../../csharp/how-to/compare-strings.md)
- [.NET Genelleştirme ve ıCU](../globalization-localization/globalization-icu.md)
- [Ordinal ve kültüre duyarlı dize işlemleri](/dotnet/api/system.string#ordinal-vs-culture-sensitive-operations)
- [.NET kaynak kodu çözümlemesine genel bakış](../../fundamentals/code-analysis/overview.md)
