---
title: char.Net ' te acter kodlamaya giriş
description: char.Net 'te acter kodlama ve kod çözme hakkında bilgi edinin.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: a5d838176bf4437a295ebe6c2cea8b1fe0eeeb61
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656299"
---
# <a name="character-encoding-in-net"></a>.NET içinde karakter kodlaması

Bu makalede char , .NET tarafından kullanılan kodlama sistemlerine yönelik bir giriş sunulmaktadır. Makalesinde,,, <xref:System.String> <xref:System.Char> <xref:System.Text.Rune> ve <xref:System.Globalization.StringInfo> türlerinin Unicode, UTF-16 ve UTF-8 ile nasıl çalıştığı açıklanmaktadır.

* char Acter* terimi, *bir okuyucunun tek bir görüntüleme öğesi olarak beyin bir*genel anlamda burada kullanılır. Ortak örnekler, "a", "@" simgesi ve Emoji "" harftir 🐂 . Bazı durumlarda char , [grafem kümelerindeki](#grapheme-clusters) bölümünde açıklandığı gibi, bir acter aslında birden çok bağımsız görüntüleme öğelerinden oluşur.

## <a name="the-no-locstring-and-no-locchar-types"></a>stringVe char türleri

Sınıfının bir örneği [string](xref:System.String) bazı metinleri temsil eder. `string`, Her biri yapının bir örneği olan 16 bit değerlerden oluşan bir dizidir [char](xref:System.Char) . [ string . Length](xref:System.String.Length) özelliği `char` , örnekteki örneklerin sayısını döndürür `string` .

Aşağıdaki örnek işlev, içindeki tüm örneklerin onaltılı gösterimindeki değerleri yazdırır `char` `string` :

::: Code Language = "CSharp" Source = "parçacıklar/ char acter-Encoding-tanıtımı/CSharp/PrintStringChars. cs" id = "SnippetPrintChars":::

string"Hello" ifadesini bu işleve geçirin ve aşağıdaki çıktıyı alın:

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

Her char bir acter tek bir değer ile temsil edilir `char` . Bu kalıp, dünyanın çoğu dili için geçerli bir değer içerir. Örneğin, char *nǐ hǎo* ve " *Hello*" gibi sesli iki Çince acters çıkışı aşağıda verilmiştir:

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

Ancak bazı dillerde ve bazı semboller ve Emoji için `char` tek bir acter temsil eden iki örnek sürer char . Örneğin, char sözcük içindeki acters ve `char` örnekleri, Ozu dilinde *Ozu* anlamına gelir:

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

Yukarıdaki örnekte, char boşluk hariç her bir acter iki örnekle temsil edilir `char` .

Tek bir Unicode emoji Ayrıca `char` , aşağıdaki örnekte görüldüğü gibi bir Ox emoji gösterildiği gibi iki s tarafından da temsil edilir:

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

Bu örnekler `string.Length` , örneklerinin sayısını gösteren değerinin, `char` görüntülenen acters sayısını belirtmesinin gerekli olmadığını gösterir char . Tek bir `char` örnek bir acter temsil etmesi gereken değildir char .

`char`Tek bir acter ile eşlenen çiftler char *vekil çiftleri*olarak adlandırılır. Nasıl çalıştığını anlamak için Unicode ve UTF-16 kodlamasını anlamanız gerekir.

## <a name="unicode-code-points"></a>Unicode kod noktaları

Unicode, çeşitli platformlarda ve çeşitli diller ve betiklerle kullanım için uluslararası bir kodlama standardıdır.

Unicode standart 1.100.000 ' den fazla [kod noktasını](https://www.unicode.org/glossary/#code_point)tanımlar. Kod noktası, 0 ile `U+10FFFF` (ondalık 1.114.111) arasında değişebilir bir tamsayı değeridir. Bazı kod noktaları harflere, simgelere veya emoji 'ye atanır. Diğer char bir deyişle, yeni bir satıra ilerlemek gibi metin veya acters 'nin nasıl görüntülendiğini denetleyen eylemlere atanır. Birçok kod noktası henüz atanmadı.

Aşağıda göründükleri Unicode TS bağlantıları ile kod noktası atamalarının bazı örnekleri verilmiştir char :

|Ondalık|Onaltılık       |Örnek|Açıklama|
|------:|----------|-------|-----------|
|10     | `U+000A` |N/A| [SATıR BESLEME](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [LATIN KÜÇÜK HARF A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | Ȳ | [LATIN BÜYÜK HARF Y WITH MACRON](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68.675 | `U+10C43`| 𐱃 | [ESKI TÜRKIC LETTER ORKHON](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127.801| `U+1F339`| 🌹 | [GÜL emoji](https://www.unicode.org/charts/PDF/U1F300.pdf) |

Kod noktaları, sözdizimi kullanılarak geleneksel adlandırılır `U+xxxx` ; burada `xxxx` onaltılık kodlanmış tamsayı değeridir.

Kod noktalarının tam aralığı içinde iki alt Aralık vardır:

* Aralıktaki **temel çok dilli düzlem (BMP)** `U+0000..U+FFFF` . Bu 16 bit Aralık, dünyanın yazma sistemlerinin çoğunluğunu kapsayacak kadar 65.536 kod noktası sağlar.
* Aralıktaki **tamamlayıcı kod noktaları** `U+10000..U+10FFFF` . Bu 21 bitlik Aralık, daha az bilinen diller ve emojıs gibi diğer amaçlar için kullanılabilen bir milyon ek kod noktası sağlar.

Aşağıdaki diyagramda, BMP ve ek kod noktaları arasındaki ilişki gösterilmektedir.

:::image type="content" source="media/:::No-Loc (Char)::: acter-Encoding-introduction/BMP-and-Supplementary. SVG "alt-text =" BMP ve ek kod noktaları ":::

## <a name="utf-16-code-units"></a>UTF-16 kod birimleri

16 bit Unicode dönüştürme biçimi ([UTF-16](https://www.unicode.org/faq/utf_bom.html#UTF16)), char Unicode kod noktalarını temsil etmek için 16 bit *kod birimi* kullanan bir acter kodlama sistemidir. .NET, içindeki metni kodlamak için UTF-16 kullanır `string` . `char`Örnek, 16 bit kod birimini temsil eder.

Tek bir 16 bit kod birimi, temel çok dilli düzlemin 16 bit aralığında herhangi bir kod noktasını temsil edebilir. Ancak, tamamlayıcı aralıktaki bir kod noktası için iki `char` örnek gereklidir.

## <a name="surrogate-pairs"></a>Vekil çiftleri

2 16 bitlik değerlerin tek 21 bitlik bir değere çevrilmesi, ' den *surrogate code points* `U+D800` `U+DFFF` (Decimal 55.296-57.343), dahil olmak üzere, vekil kod noktaları adlı özel bir Aralık tarafından kolaylaştırılacaktır.

Aşağıdaki diyagramda, BMP ve vekil kod noktaları arasındaki ilişki gösterilmektedir.

:::image type="content" source="media/:::No-Loc (Char)::: acter-Encoding-introduction/BMP-and-Surrogate. SVG "alt-text =" BMP ve vekil kod noktaları ":::

Yüksek bir *yedek* kod noktası ( `U+D800..U+DBFF` ) hemen sonrasında *düşük bir yedek* kod noktası () olduğunda `U+DC00..U+DFFF` , Çift, aşağıdaki formül kullanılarak bir ek kod noktası olarak yorumlanır:

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

Örneğin, yedek çiftine karşılık gelen gerçek kod noktası `0xD83C` `0xDF39`  aşağıdaki şekilde hesaplanır:

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

Yukarıdaki örnek, `"\ud83c\udf39"` `U+1F339 ROSE ('🌹')` daha önce bahsedilen kod noktasının UTF-16 kodlaması olduğunu gösterir.

## <a name="unicode-scalar-values"></a>Unicode skaler değerleri

[Unicode skaler değeri](https://www.unicode.org/glossary/#unicode_scalar_value) , yedek kod noktalarından başka tüm kod noktalarına başvurur. Diğer bir deyişle, skaler bir değer, bir char acter atanmış veya gelecekte bir acter atanabilir olan herhangi bir kod noktasıdır char . Burada "character", metin veya acters 'nin nasıl görüntülendiğini denetleyen eylemler gibi şeyler içeren bir kod noktasına atanabilecek her şeyi ifade eder char .

Aşağıdaki diyagramda skaler değer kod noktaları gösterilmektedir.

:::image type="content" source="media/:::No-Loc (Char)::: acter-Encoding-introduction/scalar-values. SVG "alt-text =" skaler değerler ":::

### <a name="the-no-locrune-type-as-a-scalar-value"></a>RuneSkalar değer olarak tür

.NET Core 3,0 ile başlayarak, <xref:System.Text.Rune?displayProperty=fullName> tür bir Unicode skaler değeri temsil eder. **`Rune` .NET Core 2. x veya .NET Framework 4. x sürümünde kullanılamaz.**

`Rune`Oluşturucular, sonuçta elde edilen örneğin geçerli bir Unicode skaler değeri olduğunu doğrular, aksi takdirde bir özel durum oluşturur. Aşağıdaki örnek, `Rune` giriş geçerli skaler değerleri temsil ettiğinden örnekleri başarıyla örnekleyen kodu gösterir:

::: Code Language = "CSharp" Source = "parçacıklar/ char acter-Encoding-giriş/CSharp/örnek oluştur Rune s.cs" id = "SnippetValid":::

Aşağıdaki örnek, bir özel durum oluşturur çünkü kod noktası vekil aralıkta ve bir yedek çiftinin parçası değil:

::: Code Language = "CSharp" Source = "parçacıklar/ char acter-Encoding-giriş/CSharp/örnek oluştur Rune s.cs" id = "SnippetInvalidSurrogate":::

Aşağıdaki örnek bir özel durum oluşturur çünkü kod noktası, tamamlayıcı aralığın ötesinde:

::: Code Language = "CSharp" Source = "parçacıklar/ char acter-Encoding-giriş/CSharp/örnek oluştur Rune s.cs" id = "SnippetInvalidHigh":::

### <a name="no-locrune-usage-example-changing-letter-case"></a>Rune Kullanım örneği: harf durumunu değiştirme

Bir ' a sahip olan `char` ve bir vekil çiftten ise, skaler bir değer olan bir kod noktasıyla çalıştığını varsayan BIR API `char` . Örneğin, her birinde ' de çağıran aşağıdaki yöntemi göz önünde bulundurun <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> char string :

::: Code Language = "CSharp" Source = "parçacıklar/ char acter-Encoding-tanıtımı/CSharp/ConvertToUpper. cs" ID = "SnippetBadExample":::

`input` string Küçük harfli Deseret harfini içeriyorsa `er` ( `𐑉` ), bu kod bunu büyük harfe ( `𐐡` ) dönüştürmez. Kod `char.ToUpperInvariant` , her yedek kod noktasında ayrı olarak çağırır `U+D801` `U+DC49` . Ancak `U+D801` kendi kendine küçük harf olarak tanımlamak için yeterli bilgi yok, `char.ToUpperInvariant` Bu nedenle tek başına çıkar. `U+DC49`Aynı şekilde işler. Sonuç, içindeki küçük harfli ' 𐑉 ' `input` string ' 𐑉 ' değerine dönüştürülmez.

Doğru bir şekilde büyük harfe dönüştürmek için iki seçenek vardır string :

* <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType>Giriş üzerinde, yineleme yerine çağırın string `char` `char` . `string.ToUpperInvariant`Yöntemi her bir yedek çiftinin her iki bölümüne erişebilir, bu nedenle tüm Unicode kod noktalarını doğru bir şekilde işleyebilir.
* `Rune` `char` Aşağıdaki örnekte gösterildiği gibi, UNICODE skaler değerlerini örnekler yerine örnekler olarak yineleyin. `Rune`Örnek geçerli bir Unicode skaler değeri olduğundan, skaler bir değer üzerinde çalışmasını bekleyen API 'lere geçirilebilir. Örneğin, <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi çağırmak doğru sonuçlar verir:

  ::: Code Language = "CSharp" Source = "parçacıklar/ char acter-Encoding-tanıtımı/CSharp/ConvertToUpper. cs" ID = "SnippetGoodExample":::

### <a name="other-no-locrune-apis"></a>Diğer Rune API 'ler

`Rune`Tür, API 'lerin çoğunun analoglarından sunar `char` . Örneğin, aşağıdaki yöntemler tür üzerinde statik API 'Leri yansıtır `char` :

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

Bir örnekten ham skaler değer almak için `Rune` <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> özelliğini kullanın.

Bir örneği bir `Rune` dizi için geri dönüştürmek için `char` <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> veya <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> yöntemini kullanın.

Herhangi bir Unicode skaler değeri tek `char` veya bir vekil çifti tarafından gösterilebilir olduğundan, herhangi bir `Rune` örnek en fazla 2 örnek tarafından temsil edilebilir `char` . <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> `char` Bir örneği göstermek için kaç örnek gerektiğini görmek için kullanın `Rune` .

.NET türü hakkında daha fazla bilgi için `Rune` bkz. [ `Rune` API başvurusu](xref:System.Text.Rune).

## <a name="grapheme-clusters"></a>Grapheme kümeleri

Bir char acter, birden çok kod noktasının birleşiminden kaynaklanabilir. bu nedenle, genellikle "acter" yerine kullanılan daha açıklayıcı bir terim, char [grafem](https://www.unicode.org/glossary/#grapheme_cluster)kümesidir. .NET 'teki denk terim [metin öğesidir](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A).

`string`"A", "á", "á" ve "" örneklerini göz önünde bulundurun `👩🏽‍🚒` . İşletim sisteminiz, Unicode standardı tarafından belirtildiği gibi bunları işlediğinde, bu örneklerin her biri `string` tek bir metin öğesi veya grafem kümesi olarak görünür. Ancak son ikisi birden fazla skaler değer kod noktasıyla temsil edilir.

* string"A", bir skaler değerle temsil edilir ve bir örnek içerir `char` .

  * `U+0061 LATIN SMALL LETTER A`

* string"Á", bir skaler değerle temsil edilir ve bir örnek içerir `char` .

  * `U+00E1 LATIN SMALL LETTER A WITH ACUTE`

* string"Á", "á" ile aynı görünür, ancak iki skaler değerle temsil edilir ve iki örnek içerir `char` .

  * `U+0061 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* Son olarak, string " `👩🏽‍🚒` " dört skaler değer ile temsil edilir ve yedi `char` örnek içerir.

  * `U+1F469 WOMAN` (tamamlayıcı Aralık, yedek çifti gerektirir)
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4` (tamamlayıcı Aralık, yedek çifti gerektirir)
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE` (tamamlayıcı Aralık, yedek çifti gerektirir)

Önceki örneklerde, örneğin, vurgulu vurgu değiştiricisi veya kaplama tonu değiştiricisi gibi-kod noktası ekranda tek başına bir öğe olarak görüntülenmez. Bunun yerine, daha önce gelen bir metin öğesinin görünümünü değiştirmek için kullanılır. Bu örnekler, tek bir " char acter," veya "grapheme kümesi" olarak düşündüğimizi oluşturmak için birden çok skalar değer alıp verebileceğini gösterir.

Bir a 'nın grafem kümelerini numaralandırmak için `string` <xref:System.Globalization.StringInfo> Aşağıdaki örnekte gösterildiği gibi sınıfını kullanın. Swift hakkında bilginiz varsa, .NET `StringInfo` türü [Swift 'ın `character` tipine](https://developer.apple.com/documentation/swift/character)benzer.

### <a name="example-count-no-locchar-no-locrune-and-text-element-instances"></a>Örnek: Count char , Rune , ve metin öğesi örnekleri

.NET API 'lerinde, bir grafem kümesine *metin öğesi*denir. Aşağıdaki yöntem `char` ,, `Rune` ve içindeki metin öğesi örnekleri arasındaki farkları göstermektedir `string` :

::: Code Language = "CSharp" Source = "parçacıklar/ char acter-Encoding-tanıtımı/CSharp/CountTextElements. cs" ID = "SnippetCountMethod":::

::: Code Language = "CSharp" Source = "parçacıklar/ char acter-Encoding-tanıtımı/CSharp/CountTextElements. cs" ID = "SnippetCallCountMethod":::

Bu kodu .NET Framework veya .NET Core 3,1 veya önceki sürümlerde çalıştırırsanız, emoji için metin öğesi sayısı gösterilir `4` . Bunun nedeni, `StringInfo` .NET 5 ' te düzeltilen sınıftaki bir hatadır.

### <a name="example-splitting-no-locstring-instances"></a>Örnek: string örnekleri bölme

Örnekleri bölrken `string` , vekil çiftleri ve grafem kümelerini bölmemeye özen gösterin. Aşağıdaki hatalı kod örneğini göz önünde bulundurun: her 10 acters satır sonu eklemeyi amaçlayan char string

::: Code Language = "CSharp" Source = "parçacıklar/ char acter-Encoding-tanıtım/CSharp/ınsertnewlines. cs" ID = "SnippetBadExample":::

Bu kod örnekleri numaralandırdığından `char` , Straddle bir 10 sınır olarak gerçekleşen bir yedek çift `char` bölünecektir ve aralarında bir yeni satır eklenebilir. Bu ekleme veri bozulması sunarak, vekil kod noktaları yalnızca çiftler olarak anlamlıdır.

Örnekler `Rune` yerine örnekleri (skaler değerler) numaralandırdıysanız veri bozulması olasılığı ortadan kalkar `char` . Bir dizi `Rune` örnek, 10 sınırını izleyen bir grafem kümesi oluşturur `char` . Grafem kümesi ayarlandıysa, doğru yorumlanamaz.

stringAşağıdaki örnekte olduğu gibi, grafem kümelerini veya metin öğelerini sayarak daha iyi bir yaklaşım vardır:

::: Code Language = "CSharp" Source = "parçacıklar/ char acter-Encoding-tanıtım/CSharp/ınsertnewlines. cs" ID = "SnippetGoodExample":::

Ancak daha önce belirtildiği gibi, .NET 5 dışındaki .NET uygulamalarında, `StringInfo` sınıfı bazı grafem kümelerini yanlış işleyebilir.

## <a name="utf-8-and-utf-32"></a>UTF-8 ve UTF-32

Önceki bölümlerde, .NET 'in örnekleri kodlamak için kullandığı, UTF-16 ' a odaklanan bölümler vardır `string` . Unicode- [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) ve [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)için başka kodlama sistemleri vardır. Bu kodlamalar sırasıyla 8 bit kod birimleri ve 32 bit kod birimleri kullanır.

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

.NET ' te, UTF-16 kod birimleri, string 16 bit tamsayılar (örnekler) dizisi olarak bitişik bellekte depolanır `char` . Bağımsız kod birimlerinin bitleri geçerli mimarinin [bitimcisine](https://en.wikipedia.org/wiki/Endianness) göre düzenlenir.

Küçük endian mimarisinde, string UTF-16 kod noktalarından oluşan bir tanesi `[ D801 DCCC ]` bayt olarak bellekte düzenlenir `[ 0x01, 0xD8, 0xCC, 0xDC ]` . Aynı büyüklükte bir mimaride string , bayt olarak bellekte aynı şekilde düzenlenir `[ 0xD8, 0x01, 0xDC, 0xCC ]` .

Birbirleriyle iletişim kuran bilgisayar sistemleri, kablo ile kesişen verilerin gösterimini kabul etmelidir. Çoğu ağ protokolü, metin aktarırken bir standart olarak UTF-8 kullanır, kısmen de az endian bir makineyle iletişim kuran büyük endian makinesinden kaynaklanan sorunlardan kaçınmaktır. stringUTF-8 kod noktalarından oluşan bir işlem, `[ F0 90 93 8C ]` her zaman bitime yönteminden bağımsız olarak bayt olarak temsil edilir `[ 0xF0, 0x90, 0x93, 0x8C ]` .

Metin aktarmak için UTF-8 ' i kullanmak için, .NET uygulamaları genellikle aşağıdaki örnek gibi bir kod kullanır:

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

Önceki örnekte, [. UTF8. GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) YÖNTEMI, UTF-16 `string` ' ı bir dizi Unicode skaler değere geri çözer, ardından bu skaler değerleri UTF-8 ' e yeniden kodlar ve sonuç sırasını bir `byte` diziye koyar. [Encoding. UTF8. GetString](xref:System.Text.UTF8Encoding.GetString%2A) yöntemi, bir UTF-8 `byte` dizisini UTF-16 ' a dönüştürerek ters dönüştürmeyi gerçekleştirir `string` .

> [!WARNING]
> UTF-8 internet 'te ortak olduğundan, ham baytları kablolu olarak okumak ve verileri UTF-8 gibi değerlendirmek mümkün olabilir. Ancak, gerçekten doğru biçimlendirildiğini doğrulamanız gerekir. Kötü amaçlı bir istemci, hizmetinize hatalı biçimlendirilmiş UTF-8 gönderebilir. Doğru biçimlendirilmiş gibi bu veriler üzerinde işlem yaparsanız, uygulamanızda hatalara veya güvenlik delikleri oluşmasına neden olabilir. UTF-8 verilerini doğrulamak için, gibi bir yöntemi kullanabilirsiniz `Encoding.UTF8.GetString` . Bu, gelen verileri bir öğesine dönüştürürken doğrulama işlemi gerçekleştirecek `string` .

### <a name="well-formed-encoding"></a>İyi biçimlendirilmiş kodlama

İyi biçimlendirilmiş bir Unicode kodlaması, belirsiz bir string şekilde çözülemeyen ve bir Unicode skaler değerler dizisine hatasız bir şekilde kodu oluşturulan kod birimleridir. İyi biçimlendirilmiş veriler UTF-8, UTF-16 ve UTF-32 arasında serbestçe dağıtılabilir.

Bir kodlama sırasının doğru biçimlendirilmiş olup olmadığı ve bir makinenin mimarisinin BİTİLMESİ ile ilgisi olmadığı hakkında soru. Hatalı biçimlendirilmiş bir UTF-8 sırası, büyük endian ve az endian makinelerde aynı şekilde hatalı biçimlendirilmiş bir dizelerdir.

Hatalı biçimlendirilmiş kodlamalar örnekleri aşağıda verilmiştir:

* UTF-8 ' de, `[ 6C C2 61 ]` izleyen sıra hatalı biçimlendirilmiş `C2` `61` .

* UTF-16 ' da, dizi `[ DC00 DD00 ]` (veya C# ' ta string `"\udc00\udd00"` ) hatalı biçimlendirilmiş olduğundan düşük vekil `DC00` başka bir düşük yedek tarafından izlenemiyor `DD00` .

* UTF-32 ' de, dizi, `[ 0011ABCD ]` `0011ABCD` Unicode skaler değerler aralığının dışında olduğundan, sıra hatalı biçimlendirilmiş.

.NET sürümünde `string` örnekler neredeyse her zaman iyi BIÇIMLENDIRILMIŞ UTF-16 verileri içerir, ancak bu garanti edilmez. Aşağıdaki örneklerde, örneklerde hatalı biçimlendirilmiş UTF-16 verileri oluşturan geçerli C# kodu gösterilmektedir `string` .

* Hatalı biçimlendirilmiş değişmez değer:

  ```csharp
  const string s = "\ud800";
  ```

* stringBir vekil çifti ayıran Sub:

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

Hiçbir şekilde [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) hatalı oluşturulmuş örnekler döndürmeyen API 'ler `string` . `Encoding.GetString` ve `Encoding.GetBytes` yöntemleri, girişte hatalı biçimlendirilmiş dizileri tespit ediyor ve çıkış oluştururken char acter değiştirme işlemi gerçekleştirmiyor. Örneğin, [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) GIRIŞTE ASCII olmayan bir bayt görürseniz (U + 0000.. U + 007F aralığı dışında), döndürülen örneğe bir '? ' ekler `string` . [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A) Hatalı biçimlendirilmiş UTF-8 dizilerini `U+FFFD REPLACEMENT CHARACTER ('�')` döndürülen örnekteki ile değiştirir `string` . Daha fazla bilgi için bkz. [Unicode standart](https://www.unicode.org/versions/latest/), Bölüm 5,22 ve 3,9.

Yerleşik `Encoding` sınıflar, char Hatalı biçimlendirilmiş diziler görüldüğünde, acter değiştirme yerine özel bir durum oluşturmak için de yapılandırılabilir. Bu yaklaşım, genellikle char acter değiştirme 'nin kabul edilebilir olabileceği güvenlik duyarlı uygulamalarda kullanılır.

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

Yerleşik sınıfların nasıl kullanılacağı hakkında daha fazla bilgi için `Encoding` bkz. [ char .net 'te acter kodlama sınıfları kullanma](character-encoding.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [Genelleştirme ve yerelleştirme](../globalization-localization/index.md)
