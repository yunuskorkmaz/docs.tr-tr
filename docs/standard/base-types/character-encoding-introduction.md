---
title: .NET 'te karakter kodlamaya giriş
description: .NET 'te karakter kodlama ve kod çözme hakkında bilgi edinin.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 086430a720e6dc7f39d459a4b99d5bbdb1cfcac3
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82141300"
---
# <a name="character-encoding-in-net"></a>.NET içinde karakter kodlaması

Bu makalede, .NET tarafından kullanılan karakter kodlama sistemlerine giriş sağlanır. Makalesinde <xref:System.String>, <xref:System.Char> <xref:System.Text.Rune>,, ve <xref:System.Globalization.StringInfo> türlerinin Unicode, UTF-16 ve UTF-8 ile nasıl çalıştığı açıklanmaktadır.

Bu *karakter* , *bir okuyucunun tek bir görüntüleme öğesi olarak beyin bir*genel anlamda burada kullanılır. Ortak örnekler, "a", "@" simgesi ve Emoji "🐂" harftir. Bazı durumlarda, [grafem kümelerindeki](#grapheme-clusters) bölümünde açıklanan bir karakter aslında birden çok bağımsız görüntüleme öğelerinden oluşur.

## <a name="the-string-and-char-types"></a>Dize ve karakter türleri

[String](xref:System.String) sınıfının bir örneği bazı metinleri temsil eder. , `string` Her biri [char](xref:System.Char) yapısının bir örneği olan 16 bit değerlerden oluşan bir dizidir. [Dize. Length](xref:System.String.Length) özelliği, `char` `string` örnekteki örneklerin sayısını döndürür.

Aşağıdaki örnek işlev, içindeki tüm `char` örneklerin onaltılı gösterimindeki değerleri yazdırır: `string`

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

"Hello" dizesini bu işleve geçirin ve aşağıdaki çıktıyı alın:

```csharp
PrintChars("Hello");
```

```output
"Hello".Length = 5
s[0] = 'H' ('\u0048')
s[1] = 'e' ('\u0065')
s[2] = 'l' ('\u006c')
s[3] = 'l' ('\u006c')
s[4] = 'o' ('\u006f')
```

Her karakter tek `char` bir değerle temsil edilir. Bu kalıp, dünyanın çoğu dili için geçerli bir değer içerir. Örneğin, *nǐ hǎo* ve " *Hello*" gibi sesli iki Çince karakterin çıktısı aşağıda verilmiştir:

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

Ancak bazı dillerde ve bazı semboller ve Emoji için tek bir karakteri temsil eden iki `char` örnek sürer. Örneğin, sözcükteki karakter ve `char` örnekleri, Ozu dilinde kullanılacak şekilde *Osage* karşılaştırın:

```csharp
PrintChars("𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟");
```

```output
"𐓏𐓘𐓻𐓘𐓻𐓟 𐒻𐓟".Length = 17
s[0] = '�' ('\ud801')
s[1] = '�' ('\udccf')
s[2] = '�' ('\ud801')
s[3] = '�' ('\udcd8')
s[4] = '�' ('\ud801')
s[5] = '�' ('\udcfb')
s[6] = '�' ('\ud801')
s[7] = '�' ('\udcd8')
s[8] = '�' ('\ud801')
s[9] = '�' ('\udcfb')
s[10] = '�' ('\ud801')
s[11] = '�' ('\udcdf')
s[12] = ' ' ('\u0020')
s[13] = '�' ('\ud801')
s[14] = '�' ('\udcbb')
s[15] = '�' ('\ud801')
s[16] = '�' ('\udcdf')
```

Yukarıdaki örnekte, boşluk hariç her bir karakter iki `char` örnek tarafından temsil edilir.

Tek bir Unicode emoji Ayrıca, aşağıdaki örnekte görüldüğü `char`gibi bir Ox emoji gösterildiği gibi iki s tarafından da temsil edilir:

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

Bu örnekler `string.Length`, `char` örnek sayısını gösteren değerinin, görüntülenen karakter sayısını belirtmesinin gerekli olmadığını gösterir. Tek `char` bir örnek bir karakteri temsil etmesi gerekmez.

Tek `char` bir karakterle eşlenen çiftler *vekil çiftler*olarak adlandırılır. Nasıl çalıştığını anlamak için Unicode ve UTF-16 kodlamasını anlamanız gerekir.

## <a name="unicode-code-points"></a>Unicode kod noktaları

Unicode, çeşitli platformlarda ve çeşitli diller ve betiklerle kullanım için uluslararası bir kodlama standardıdır.

Unicode standart 1.100.000 ' den fazla [kod noktasını](https://www.unicode.org/glossary/#code_point)tanımlar. Kod noktası, 0 ile `U+10FFFF` (ondalık 1.114.111) arasında değişebilir bir tamsayı değeridir. Bazı kod noktaları harflere, simgelere veya emoji 'ye atanır. Diğer bir deyişle, yeni bir satıra ilerlemek gibi metin veya karakterlerin nasıl görüntülendiğini denetleyen eylemlere atanır. Birçok kod noktası henüz atanmadı.

Aşağıda göründükleri Unicode grafiklerine yönelik bağlantılarla birlikte kod noktası atamalarından oluşan bazı örnekler verilmiştir:

|Ondalık|Onaltılık       |Örnek|Açıklama|
|------:|----------|-------|-----------|
|10     | `U+000A` |Yok| [SATıR BESLEME](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [LATIN KÜÇÜK HARF A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | Ȳ | [LATIN BÜYÜK HARF Y WITH MACRON](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68.675 | `U+10C43`| 𐱃 | [ESKI TÜRKIC LETTER ORKHON](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127.801| `U+1F339`| 🌹 | [GÜL emoji](https://www.unicode.org/charts/PDF/U1F300.pdf) |

Kod noktaları, sözdizimi `U+xxxx`kullanılarak geleneksel adlandırılır; burada `xxxx` onaltılık kodlanmış tamsayı değeridir.

Kod noktalarının tam aralığı içinde iki alt Aralık vardır:

* `U+0000..U+FFFF`Aralıktaki **temel çok dıllı düzlem (BMP)** . Bu 16 bit Aralık, dünyanın yazma sistemlerinin çoğunluğunu kapsayacak kadar 65.536 kod noktası sağlar.
* Aralıktaki `U+10000..U+10FFFF` **tamamlayıcı kod noktaları** . Bu 21 bitlik Aralık, daha az bilinen diller ve emojıs gibi diğer amaçlar için kullanılabilen bir milyon ek kod noktası sağlar.

Aşağıdaki diyagramda, BMP ve ek kod noktaları arasındaki ilişki gösterilmektedir.

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP ve ek kod noktaları":::

## <a name="utf-16-code-units"></a>UTF-16 kod birimleri

16 bit Unicode dönüştürme biçimi ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)), Unicode kod noktalarını temsil etmek için 16 bit *kod birimi* kullanan bir karakter kodlama sistemidir. .NET, içindeki metni kodlamak için UTF-16 kullanır `string`. `char` Örnek, 16 bit kod birimini temsil eder.

Tek bir 16 bit kod birimi, temel çok dilli düzlemin 16 bit aralığında herhangi bir kod noktasını temsil edebilir. Ancak, tamamlayıcı aralıktaki bir kod noktası için iki `char` örnek gereklidir.

## <a name="surrogate-pairs"></a>Vekil çiftleri

2 16 bitlik değerlerin tek 21 bitlik bir değere çevrilmesi, ' den `U+D800` (Decimal 55.296-57.343), dahil olmak üzere `U+DFFF` , *vekil kod noktaları*adlı özel bir Aralık tarafından kolaylaştırılacaktır.

Aşağıdaki diyagramda, BMP ve vekil kod noktaları arasındaki ilişki gösterilmektedir.

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP ve vekil kod noktaları":::

Yüksek bir *yedek* kod noktası (`U+D800..U+DBFF`) hemen sonrasında *düşük bir yedek* kod noktası (`U+DC00..U+DFFF`) olduğunda, Çift, aşağıdaki formül kullanılarak bir ek kod noktası olarak yorumlanır:

```
code point = 0x10000 +
  ((high surrogate code point - 0xD800) * 0x0400) +
  (low surrogate code point - 0xDC00)
```

Ondalık gösterimi kullanan aynı formül aşağıda verilmiştir:

```
code point = 65,536 +
  ((high surrogate code point - 55,296) * 1,024) +
  (low surrogate code point - 56,320)
```

*Üst* yedek kod noktası, *düşük* bir vekil kod noktasına göre daha yüksek bir sayı değerine sahip değildir. Yüksek yedek kod noktası, tam 21 bit kod noktası aralığının daha yüksek sıralı 11 bitini hesaplamak için kullanıldığından, "yüksek" olarak adlandırılır. Düşük yedek kod noktası, alt sıra 10 bitlerini hesaplamak için kullanılır.

Örneğin, yedek çiftine `0xD83C` `0xDF39` karşılık gelen gerçek kod noktası aşağıdaki şekilde hesaplanır:

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

Ondalık gösterimi kullanılarak aynı hesaplama aşağıda verilmiştir:

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

Yukarıdaki örnek, daha önce `"\ud83c\udf39"` bahsedilen `U+1F339 ROSE ('🌹')` kod noktasının UTF-16 kodlaması olduğunu gösterir.

## <a name="unicode-scalar-values"></a>Unicode skaler değerleri

[Unicode skaler değeri](https://www.unicode.org/glossary/#unicode_scalar_value) , yedek kod noktalarından başka tüm kod noktalarına başvurur. Diğer bir deyişle, skaler bir değer bir karakter atanmış veya gelecekte bir karakter atanabilir olan herhangi bir kod noktasıdır. Burada "karakter", metin veya karakterlerin nasıl görüntülendiğini denetleyen eylemler gibi şeyler içeren bir kod noktasına atanabilecek her şeyi ifade eder.

Aşağıdaki diyagramda skaler değer kod noktaları gösterilmektedir.

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Skaler değerler":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a>Skalar Rune değer olarak tür

.NET Core 3,0 ile başlayarak, <xref:System.Text.Rune?displayProperty=fullName> tür bir Unicode skaler değeri temsil eder. **`Rune`.NET Core 2. x veya .NET Framework 4. x sürümünde kullanılamaz.**

`Rune` Oluşturucular, sonuçta elde edilen örneğin geçerli bir Unicode skaler değeri olduğunu doğrular, aksi takdirde bir özel durum oluşturur. Aşağıdaki örnek, giriş geçerli skaler değerleri temsil `Rune` ettiğinden örnekleri başarıyla örnekleyen kodu gösterir:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

Aşağıdaki örnek, bir özel durum oluşturur çünkü kod noktası vekil aralıkta ve bir yedek çiftinin parçası değil:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

Aşağıdaki örnek bir özel durum oluşturur çünkü kod noktası, tamamlayıcı aralığın ötesinde:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>RuneKullanım örneği: harf durumunu değiştirme

Bir ' a `char` sahip olan ve bir vekil çiftten `char` ise, skaler bir değer olan bir kod noktasıyla ÇALıŞTıĞıNı varsayan bir API. Örneğin, her <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> char birinde ' de çağıran aşağıdaki yöntemi göz önünde bulundurun string:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

`input` string Küçük harfli Deseret harfini `er` içeriyorsa (`𐑉`), bu kod bunu büyük harfe (`𐐡`) dönüştürmez. Kod, `char.ToUpperInvariant` `U+D801` her yedek kod noktasında ayrı olarak çağırır `U+DC49`. Ancak `U+D801` kendi kendine küçük harf olarak tanımlamak için yeterli bilgi yok, bu nedenle `char.ToUpperInvariant` tek başına çıkar. Aynı şekilde işler `U+DC49` . Sonuç, içindeki `input` string küçük harfli ' 𐑉 ' ' 𐑉 ' değerine dönüştürülmez.

Doğru bir string şekilde büyük harfe dönüştürmek için iki seçenek vardır:

* Giriş <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> string üzerinde, yineleme `char`yerine çağırın`char`. `string.ToUpperInvariant` Yöntemi her bir yedek çiftinin her iki bölümüne erişebilir, bu nedenle tüm Unicode kod noktalarını doğru bir şekilde işleyebilir.
* Aşağıdaki örnekte gösterildiği gibi, UNICODE skaler `Rune` değerlerini `char` örnekler yerine örnekler olarak yineleyin. `Rune` Örnek geçerli bir Unicode skaler değeri olduğundan, skaler bir değer üzerinde çalışmasını bekleyen API 'lere geçirilebilir. Örneğin, aşağıdaki örnekte <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> gösterildiği gibi çağırmak doğru sonuçlar verir:

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a>Diğer Rune API 'ler

`Rune` Tür, `char` API 'lerin çoğunun analoglarından sunar. Örneğin, aşağıdaki yöntemler `char` tür üzerinde statik API 'leri yansıtır:

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

Bir `Rune` örnekten ham skaler değer almak için <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> özelliğini kullanın.

Bir `Rune` örneği bir dizi `char`için geri dönüştürmek için veya <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> yöntemini kullanın.

Herhangi bir Unicode skaler değeri tek `char` veya bir vekil çifti tarafından gösterilebilir olduğundan, herhangi bir `Rune` örnek en fazla 2 `char` örnek tarafından temsil edilebilir. Bir <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> `Rune` örneği göstermek için kaç `char` örnek gerektiğini görmek için kullanın.

.Net `Rune` türü hakkında daha fazla bilgi için bkz. [ `Rune` API başvurusu](xref:System.Text.Rune).

## <a name="grapheme-clusters"></a>Grapheme kümeleri

Tek bir karakter, birden çok kod noktasının birleşiminden kaynaklanabilir. bu nedenle, genellikle "character" yerine kullanılan daha açıklayıcı bir terim [grafem](https://www.unicode.org/glossary/#grapheme_cluster)kümesidir. .NET 'teki denk terim [metin öğesidir](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).

"A `string` ", "á" örneklerini göz önünde bulundurun. "á" ve "`👩🏽‍🚒`". İşletim sisteminiz, Unicode standardı tarafından belirtildiği gibi bunları işlediğinde, bu `string` örneklerin her biri tek bir metin öğesi veya grafem kümesi olarak görünür. Ancak son ikisi birden fazla skaler değer kod noktasıyla temsil edilir.

* " string A", bir skaler değerle temsil edilir ve bir `char` örnek içerir.

  * `U+0061 LATIN SMALL LETTER A`

* " string Á", bir skaler değerle temsil edilir ve bir `char` örnek içerir.

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* string "Á", "á" ile aynı görünür, ancak iki skaler değerle temsil edilir ve iki `char` örnek içerir.

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* Son olarak, string "`👩🏽‍🚒`" dört skaler değer ile temsil edilir ve yedi `char` örnek içerir.

  * `U+1F469 WOMAN`(tamamlayıcı Aralık, yedek çifti gerektirir)
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(tamamlayıcı Aralık, yedek çifti gerektirir)
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE`(tamamlayıcı Aralık, yedek çifti gerektirir)

Önceki örneklerde, örneğin, vurgulu vurgu değiştiricisi veya kaplama tonu değiştiricisi gibi-kod noktası ekranda tek başına bir öğe olarak görüntülenmez. Bunun yerine, daha önce gelen bir metin öğesinin görünümünü değiştirmek için kullanılır. Bu örnekler, tek bir "karakter" veya "grapheme kümesi" olarak düşündüğimizi oluşturmak için birden çok skalar değer alıp verebileceğini gösterir.

Bir a `string`'nın grafem kümelerini numaralandırmak için aşağıdaki örnekte gösterildiği <xref:System.Globalization.StringInfo> gibi sınıfını kullanın. Swift hakkında bilginiz varsa, .NET `StringInfo` türü [Swift 'ın `character` tipine](https://developer.apple.com/documentation/swift/character)benzer.

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a>Örnek: Count char, Rune, ve metin öğesi örnekleri

.NET API 'lerinde, bir grafem kümesine *metin öğesi*denir. Aşağıdaki yöntem, `char` `Rune`, ve içindeki metin öğesi örnekleri arasındaki farkları göstermektedir `string`:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

Bu kodu .NET Framework veya .NET Core 3,1 veya önceki sürümlerde çalıştırırsanız, emoji için metin öğesi sayısı gösterilir `4`. Bunun nedeni, .NET 5 ' te düzeltilen `StringInfo` sınıftaki bir hatadır.

### <a name="example-splitting-opno-locstring-instances"></a>Örnek: örnekleri string bölme

Örnekleri bölrken `string` , vekil çiftleri ve grafem kümelerini bölmemeye özen gösterin. Aşağıdaki hatalı kod örneğini göz önünde bulundurun. Bu, her 10 karakterden oluşan satır sonlarını bir stringaraya eklemeyi amaçlar:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

Bu kod örnekleri numaralandırdığından `char` , Straddle bir 10`char` sınır olarak gerçekleşen bir yedek çift bölünecektir ve aralarında bir yeni satır eklenebilir. Bu ekleme veri bozulması sunarak, vekil kod noktaları yalnızca çiftler olarak anlamlıdır.

Örnekler yerine `Rune` `char` örnekleri (skaler değerler) numaralandırdıysanız veri bozulması olasılığı ortadan kalkar. Bir dizi `Rune` örnek, 10`char` sınırını izleyen bir grafem kümesi oluşturur. Grafem kümesi ayarlandıysa, doğru yorumlanamaz.

Aşağıdaki örnekte olduğu gibi, grafem kümelerini veya metin öğelerini sayarak daha iyi bir yaklaşım vardır string :

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

Ancak daha önce belirtildiği gibi, .NET 5 dışındaki .NET uygulamalarında, `StringInfo` sınıfı bazı grafem kümelerini yanlış işleyebilir.

## <a name="utf-8-and-utf-32"></a>UTF-8 ve UTF-32

Önceki bölümlerde, .NET 'in örnekleri kodlamak `string` için KULLANDıĞı, UTF-16 ' a odaklanan bölümler vardır. Unicode- [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) ve [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)için başka kodlama sistemleri vardır. Bu kodlamalar sırasıyla 8 bit kod birimleri ve 32 bit kod birimleri kullanır.

UTF-16 gibi, UTF-8, bazı Unicode skaler değerleri temsil etmek için birden çok kod birimi gerektirir. UTF-32, tek bir 32 bit kod biriminde herhangi bir skaler değeri temsil edebilir.

Bu üç Unicode kodlama sisteminin her birinde aynı Unicode kod noktasının nasıl temsil edileceğini gösteren bazı örnekler aşağıda verilmiştir:

```
Scalar: U+0061 LATIN SMALL LETTER A ('a')
UTF-8 : [ 61 ]           (1x  8-bit code unit  = 8 bits total)
UTF-16: [ 0061 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000061 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+0429 CYRILLIC CAPITAL LETTER SHCHA ('Щ')
UTF-8 : [ D0 A9 ]        (2x  8-bit code units = 16 bits total)
UTF-16: [ 0429 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 00000429 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+A992 JAVANESE LETTER GA ('ꦒ')
UTF-8 : [ EA A6 92 ]     (3x  8-bit code units = 24 bits total)
UTF-16: [ A992 ]         (1x 16-bit code unit  = 16 bits total)
UTF-32: [ 0000A992 ]     (1x 32-bit code unit  = 32 bits total)

Scalar: U+104CC OSAGE CAPITAL LETTER TSHA ('𐓌')
UTF-8 : [ F0 90 93 8C ]  (4x  8-bit code units = 32 bits total)
UTF-16: [ D801 DCCC ]    (2x 16-bit code units = 32 bits total)
UTF-32: [ 000104CC ]     (1x 32-bit code unit  = 32 bits total)
```

Daha önce belirtildiği gibi, bir [vekil çiftin](#surrogate-pairs) tek bir UTF-16 kod birimi kendi kendine daha az anlamlı olur. Aynı şekilde, tek bir UTF-8 kod birimi, skalar bir değeri hesaplamak için kullanılan iki, üç veya dört dizilirse, kendisini anlamlı hale gelir.

### <a name="endianness"></a>Endian

.NET ' te, UTF-16 kod birimleri string , 16 bit tamsayılar (`char` örnekler) dizisi olarak bitişik bellekte depolanır. Bağımsız kod birimlerinin bitleri geçerli mimarinin [bitimcisine](https://en.wikipedia.org/wiki/Endianness) göre düzenlenir.

Küçük endian mimarisinde, UTF-16 kod string noktalarından `[ D801 DCCC ]` oluşan bir tanesi bayt `[ 0x01, 0xD8, 0xCC, 0xDC ]`olarak bellekte düzenlenir. Aynı büyüklükte bir mimaride, bayt string `[ 0xD8, 0x01, 0xDC, 0xCC ]`olarak bellekte aynı şekilde düzenlenir.

Birbirleriyle iletişim kuran bilgisayar sistemleri, kablo ile kesişen verilerin gösterimini kabul etmelidir. Çoğu ağ protokolü, metin aktarırken bir standart olarak UTF-8 kullanır, kısmen de az endian bir makineyle iletişim kuran büyük endian makinesinden kaynaklanan sorunlardan kaçınmaktır. UTF string -8 kod noktalarından `[ F0 90 93 8C ]` oluşan bir işlem, her zaman bitime yönteminden bağımsız olarak `[ 0xF0, 0x90, 0x93, 0x8C ]` bayt olarak temsil edilir.

Metin aktarmak için UTF-8 ' i kullanmak için, .NET uygulamaları genellikle aşağıdaki örnek gibi bir kod kullanır:

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

Önceki örnekte, [. UTF8. GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) YÖNTEMI, UTF-16 `string` ' ı bir dizi Unicode skaler değere geri çözer, ardından bu skaler değerleri UTF-8 ' e yeniden kodlar ve sonuç sırasını bir `byte` diziye koyar. [Encoding. UTF8. GetString](xref:System.Text.UTF8Encoding.GetString%2A) yöntemi, bir UTF-8 `byte` dizisini UTF-16 `string`' a dönüştürerek ters dönüştürmeyi gerçekleştirir.

> [!WARNING]
> UTF-8 internet 'te ortak olduğundan, ham baytları kablolu olarak okumak ve verileri UTF-8 gibi değerlendirmek mümkün olabilir. Ancak, gerçekten doğru biçimlendirildiğini doğrulamanız gerekir. Kötü amaçlı bir istemci, hizmetinize hatalı biçimlendirilmiş UTF-8 gönderebilir. Doğru biçimlendirilmiş gibi bu veriler üzerinde işlem yaparsanız, uygulamanızda hatalara veya güvenlik delikleri oluşmasına neden olabilir. UTF-8 verilerini doğrulamak için, gibi `Encoding.UTF8.GetString`bir yöntemi kullanabilirsiniz. Bu, gelen verileri bir `string`öğesine dönüştürürken doğrulama işlemi gerçekleştirecek.

### <a name="well-formed-encoding"></a>İyi biçimlendirilmiş kodlama

İyi biçimlendirilmiş bir Unicode kodlaması, belirsiz bir string şekilde çözülemeyen ve bir Unicode skaler değerler dizisine hatasız bir şekilde kodu oluşturulan kod birimleridir. İyi biçimlendirilmiş veriler UTF-8, UTF-16 ve UTF-32 arasında serbestçe dağıtılabilir.

Bir kodlama sırasının doğru biçimlendirilmiş olup olmadığı ve bir makinenin mimarisinin BİTİLMESİ ile ilgisi olmadığı hakkında soru. Hatalı biçimlendirilmiş bir UTF-8 sırası, büyük endian ve az endian makinelerde aynı şekilde hatalı biçimlendirilmiş bir dizelerdir.

Hatalı biçimlendirilmiş kodlamalar örnekleri aşağıda verilmiştir:

* UTF-8 ' de, izleyen `[ 6C C2 61 ]` sıra hatalı biçimlendirilmiş `C2` `61`.

* UTF-16 ' da, dizi `[ DC00 DD00 ]` ( string `"\udc00\udd00"`veya C# ' ta) hatalı biçimlendirilmiş olduğundan düşük vekil `DC00` başka bir düşük yedek `DD00`tarafından izlenemiyor.

* UTF-32 ' de, dizi `[ 0011ABCD ]` , Unicode skaler değerler aralığının `0011ABCD` dışında olduğundan, sıra hatalı biçimlendirilmiş.

.NET sürümünde `string` örnekler neredeyse her zaman ıyı biçimlendirilmiş UTF-16 verileri içerir, ancak bu garanti edilmez. Aşağıdaki örneklerde, `string` örneklerde hatalı biçimlendirilmiş UTF-16 verileri oluşturan geçerli C# kodu gösterilmektedir.

* Hatalı biçimlendirilmiş değişmez değer:

  ```csharp
  const string s = "\ud800";
  ```

* Bir vekil çifti ayıran alt dize:

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

Hiçbir şekilde [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) hatalı oluşturulmuş `string` örnekler döndürmeyen API 'ler. `Encoding.GetString`ve `Encoding.GetBytes` yöntemleri, girişte hatalı biçimlendirilmiş dizileri tespit edin ve çıkış oluştururken karakter değiştirme işlemi gerçekleştirir. Örneğin, girişte ASCII [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) olmayan bir bayt görürseniz (U + 0000.. U + 007F aralığı dışında), döndürülen `string` örneğe bir '? ' ekler. [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)Hatalı biçimlendirilmiş UTF-8 dizilerini döndürülen `U+FFFD REPLACEMENT CHARACTER ('�')` `string` örnekteki ile değiştirir. Daha fazla bilgi için bkz. [Unicode standart](https://www.unicode.org/versions/latest/), Bölüm 5,22 ve 3,9.

Yerleşik `Encoding` sınıflar, hatalı biçimlendirilmiş diziler görüldüğünde karakter değişimi gerçekleştirmek yerine bir özel durum oluşturmak için de yapılandırılabilir. Bu yaklaşım, genellikle karakter değiştirme 'nin kabul edilebilir olabileceği güvenliğe duyarlı uygulamalarda kullanılır.

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

Yerleşik `Encoding` sınıfların nasıl kullanılacağı hakkında daha fazla bilgi için bkz. [.net 'te karakter kodlama sınıfları kullanma](character-encoding.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [Genelleştirme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
