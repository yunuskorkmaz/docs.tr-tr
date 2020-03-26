---
title: .NET'te karakter kodlamasına giriş
description: .NET'te karakter kodlama ve kod çözme hakkında bilgi edinin.
ms.date: 03/09/2020
no-loc:
- Rune
- char
- string
dev_langs:
- csharp
helpviewer_keywords:
- encoding, understanding
ms.openlocfilehash: 34b1577f8bcea80c1f41b6f9605bf47d132fdb4f
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134428"
---
# <a name="character-encoding-in-net"></a>.NET'te karakter kodlaması

Bu makalede, .NET tarafından kullanılan karakter kodlama sistemlerine giriş sağlar. Makalede, <xref:System.Char>Unicode, <xref:System.Text.Rune>UTF-16 ve <xref:System.Globalization.StringInfo> UTF-8 ile nasıl çalıştığı açıklanmaktadır. <xref:System.String>

*Karakter* terimi *burada, okuyucunun tek bir görüntü öğesi olarak algıladığı*genel anlamda kullanılır. Yaygın örnekler "a", sembol "@" ve emoji🐂" ". Bazen [grafme kümeleri](#grapheme-clusters) üzerindeki bölüm açıklandığı gibi, bir karakter gibi görünen şey aslında birden çok bağımsız görüntü öğesinden oluşur.

## <a name="the-string-and-char-types"></a>Dize ve char türleri

[Dize](xref:System.String) sınıfının bir örneği bazı metni temsil eder. A `string` mantıksal olarak 16 bitdeğerlerinden oluşan bir dizidir ve bunların her biri [char](xref:System.Char) struct'un bir örneğidir. [İp. Uzunluk](xref:System.String.Length) `char` `string` özelliği, örnekteki örneklerin sayısını döndürür.

Aşağıdaki örnek işlevi, tüm örneklerin `char` heksadesit gösterimindeki değerleri `string`yazdırır:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/PrintStringChars.cs" id="SnippetPrintChars":::

"Merhaba" dizesini bu işleve geçirin ve aşağıdaki çıktıyı alırsınız:

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

Her karakter tek `char` bir değerle temsil edilir. Bu model dünya dillerinin çoğu için geçerlidir. Örneğin, burada *nů hůo* ve ortalama *Merhaba*gibi ses iki Çince karakter için çıkış' s:

```csharp
PrintChars("你好");
```

```output
"你好".Length = 2
s[0] = '你' ('\u4f60')
s[1] = '好' ('\u597d')
```

Ancak, bazı diller ve bazı semboller ve `char` emoji için, tek bir karakteri temsil etmek için iki örnek alır. Örneğin, Osage dilinde `char` *Osage* anlamına gelen sözcükteki karakterleri ve örnekleri karşılaştırın:

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

Önceki örnekte, boşluk dışındaki her karakter iki `char` örnekle temsil edilir.

Tek bir Unicode emoji de `char`iki s tarafından temsil edilir, bir öküz emoji gösteren aşağıdaki örnekte görüldüğü gibi:

```
"🐂".Length = 2
s[0] = '�' ('\ud83d')
s[1] = '�' ('\udc02')
```

Bu örnekler, `string.Length` `char` örnek sayısını gösteren değerin görüntülenen karakter sayısını göstermesi gerekmediğini gösterir. Tek `char` bir örnek tek başına mutlaka bir karakteri temsil etmez.

Tek `char` bir karakterle eşleyen *çiftlere vekil çiftler*denir. Nasıl çalıştıklarını anlamak için Unicode ve UTF-16 kodlamasını anlamanız gerekir.

## <a name="unicode-code-points"></a>Unicode kod noktaları

Unicode çeşitli platformlarda ve çeşitli dillerde ve komut dosyaları ile kullanılmak üzere uluslararası bir kodlama standardıdır.

Unicode Standardı 1,1 milyondan fazla [kod noktası](https://www.unicode.org/glossary/#code_point)tanımlar. Kod noktası, 0 ile `U+10FFFF` (ondalık 1.114.111) arasında değişen bir tamsayı değeridir. Bazı kod noktaları harflere, sembollere veya emojilere atanır. Diğerleri, yeni bir satıra ilerlemek gibi metin veya karakterlerin nasıl görüntüleneceğini denetleyen eylemlere atanır. Birçok kod noktası henüz atanmamış.

Aşağıda, göründükleri Unicode grafiklerine bağlantılar içeren kod noktası atamalarına bazı örnekler verilmiştir:

|Ondalık|Onaltılık       |Örnek|Açıklama|
|------:|----------|-------|-----------|
|10     | `U+000A` |Yok| [HAT BESLEMESI](https://www.unicode.org/charts/PDF/U0000.pdf) |
|65     | `U+0061` | a | [LATIN KÜÇÜK HARF A](https://www.unicode.org/charts/PDF/U0000.pdf) |
|562    | `U+0232` | A.B.D | [MACRON İlE LATIN SERMAYE MEKTUBU Y](https://www.unicode.org/charts/PDF/U0180.pdf) |
|68,675 | `U+10C43`| 𐱃 | [ESKI TÜRK HARFI ORKHON AT](https://www.unicode.org/charts/PDF/U10C00.pdf) |
|127,801| `U+1F339`| 🌹 | [GÜL emoji](https://www.unicode.org/charts/PDF/U1F300.pdf) |

Kod noktaları, hex kodlanmış tamsayı `U+xxxx`değerinin `xxxx` bulunduğu sözdizimi kullanılarak özel olarak adlandırılır.

Tüm kod noktaları aralığında iki alt aralık vardır:

* **Temel Çok Dilli Düzlem (BMP)** aralığında. `U+0000..U+FFFF` Bu 16 bitlik aralık, dünyanın yazı sistemlerinin çoğunu kapsayacak kadar 65.536 kod puanı sağlar.
* Aralıktaki `U+10000..U+10FFFF` **tamamlayıcı kod noktaları.** Bu 21 bit aralık, daha az bilinen diller ve emojiler gibi diğer amaçlar için kullanılabilecek bir milyondan fazla ek kod noktası sağlar.

Aşağıdaki diyagram, BMP ve ek kod noktaları arasındaki ilişkiyi göstermektedir.

:::image type="content" source="media/character-encoding-introduction/bmp-and-supplementary.svg" alt-text="BMP ve ek kod noktaları":::

## <a name="utf-16-code-units"></a>UTF-16 kod birimleri

16 bit Unicode Dönüşüm Biçimi[(UTF-16),](https://www.unicode.org/faq/utf_bom.html#UTF16)Unicode kod noktalarını temsil etmek için 16 bit *kod birimleri* kullanan bir karakter kodlama sistemidir. .NET, metni kodlamak için UTF-16'yı `string`kullanır. Bir `char` örnek 16 bitkodlu kod birimini temsil eder.

Tek bir 16 bit kod birimi, Temel Çok Dilli Düzlemin 16 bit aralığındaki herhangi bir kod noktasını temsil edebilir. Ancak ek aralıktaki bir kod noktası `char` için iki örnek gereklidir.

## <a name="surrogate-pairs"></a>Vekil çiftleri

İki 16 bit değerin tek bir 21 bit değerine çevrilme, vekil kod noktaları `U+D800` `U+DFFF` olarak adlandırılan özel bir aralıkla (ondalık 55.296 ile 57.343), dahil olmak üzere, (ondalık kod *noktaları)* ile kolaylaştırılır.

Aşağıdaki diyagram, BMP ve vekil kod noktaları arasındaki ilişkiyi göstermektedir.

:::image type="content" source="media/character-encoding-introduction/bmp-and-surrogate.svg" alt-text="BMP ve vekil kod noktaları":::

Yüksek *vekil* kod noktası`U+D800..U+DBFF`( ) hemen *düşük* bir`U+DC00..U+DFFF`vekil kod noktası ( ) tarafından takip edildiğinde, çifti aşağıdaki formül kullanılarak tamamlayıcı bir kod noktası olarak yorumlanır:

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

*Yüksek* vekil kod noktası, *düşük* bir vekil kod noktasından daha yüksek bir sayı değerine sahip değildir. Tam 21 bit kod noktası aralığının üst düzey 11 bitini hesaplamak için kullanıldığından, yüksek vekil kod noktası "yüksek" olarak adlandırılır. Düşük vekil kod noktası, alt sıra 10 bitini hesaplamak için kullanılır.

Örneğin, vekil çifte `0xD83C` karşılık gelen ve `0xDF39` aşağıdaki gibi hesaplanan gerçek kod noktası:

```
actual = 0x10000 + ((0xD83C - 0xD800) * 0x0400) + (0xDF39 - 0xDC00)
       = 0x10000 + (          0x003C  * 0x0400) +           0x0339
       = 0x10000 +                      0xF000  +           0x0339
       = 0x1F339
```

Ondalık gösterimi kullanarak aynı hesaplama aşağıda verilmiştir:

```
actual =  65,536 + ((55,356 - 55,296) * 1,024) + (57,145 - 56320)
       =  65,536 + (              60  * 1,024) +             825
       =  65,536 +                     61,440  +             825
       = 127,801
```

Yukarıdaki örnek, daha `"\ud83c\udf39"` önce bahsedilen kod noktasının `U+1F339 ROSE ('🌹')` UTF-16 kodlaması olduğunu göstermektedir.

## <a name="unicode-scalar-values"></a>Unicode skaler değerler

[Unicode skaler değeri](https://www.unicode.org/glossary/#unicode_scalar_value) terimi, vekil kod noktaları dışındaki tüm kod noktalarını ifade eder. Başka bir deyişle, skaler değer, bir karakter atanan veya gelecekte bir karakter atanabilir herhangi bir kod noktasıdır. Buradaki "Karakter" kod noktasına atanabilen ve metnin veya karakterlerin nasıl görüntüleneceğini denetleyen eylemler gibi şeyleri içeren herhangi bir şeyi ifade eder.

Aşağıdaki diyagramskalar değer kodu noktalarını göstermektedir.

:::image type="content" source="media/character-encoding-introduction/scalar-values.svg" alt-text="Skaler değerler":::

### <a name="the-opno-locrune-type-as-a-scalar-value"></a>Skaler değer olarak Rune türü

.NET Core 3.0 ile <xref:System.Text.Rune?displayProperty=fullName> başlayarak, tür Unicode skaler değerini temsil eder. **`Rune`.NET Core 2.x veya .NET Framework 4.x'te kullanılamaz.**

Kurucular, `Rune` ortaya çıkan örneğin geçerli bir Unicode skaler değer olduğunu doğrular, aksi takdirde bir özel durum atarlar. Aşağıdaki örnek, giriş geçerli skaler `Rune` değerleri temsil ettiği için örnekleri başarıyla anında gösteren kodu gösterir:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetValid":::

Kod noktası vekil aralığında olduğundan ve bir vekil çiftinin parçası olmadığından aşağıdaki örnek bir özel durum oluşturur:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidSurrogate":::

Kod noktası ek aralığın dışında olduğundan aşağıdaki örnek bir özel durum oluşturur:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InstantiateRunes.cs" id="SnippetInvalidHigh":::

### <a name="opno-locrune-usage-example-changing-letter-case"></a>Runekullanım örneği: harf örneği değiştirme

Bir api `char` alır ve skaler bir değer bir kod noktası ile çalıştığını varsayar bir `char` API bir vekil çifti ise doğru çalışmaz. Örneğin, aşağıdaki <xref:System.Char.ToUpperInvariant%2A?displayProperty=nameWithType> char yöntemi göz önünde bulundurun stringher biri çağırır:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetBadExample":::

`input` string Küçük Deseret harfi `er` ()`𐑉`içeriyorsa, bu kod onu büyük`𐐡`harfe dönüştürmez ( ). Kod, `char.ToUpperInvariant` her vekil kod noktasında `U+D801` ayrı `U+DC49`ayrı çağırır ve . Ama `U+D801` tek başına küçük bir mektup olarak tanımlamak için yeterli `char.ToUpperInvariant` bilgiye sahip değil, bu yüzden yalnız bırakır. Ve aynı `U+DC49` şekilde işliyor. Sonuç olarak küçük harf ''' `input` string büyük harf ''' dönüştürülür almaz.

A'yı büyük string harfe doğru dönüştürmek için iki seçenek aşağıda verilmiştir:

* -by-`char`. `char` <xref:System.String.ToUpperInvariant%2A?displayProperty=nameWithType> string Yöntem, `string.ToUpperInvariant` her vekil çiftinin her iki bölümüne de erişebilir, böylece tüm Unicode kod noktalarını doğru şekilde işleyebilir.
* Aşağıdaki örnekte gösterildiği gibi, `Rune` `char` örnek yerine Örnek olarak Unicode skaler değerleri üzerinden yineleyin. Bir `Rune` örnek geçerli bir Unicode skaler değer olduğundan, skaler bir değer üzerinde çalışmayı bekleyen API'lere geçirilebilir. Örneğin, aşağıdaki <xref:System.Text.Rune.ToUpperInvariant%2A?displayProperty=nameWithType> örnekte gösterildiği gibi arama doğru sonuçlar verir:

  :::code language="csharp" source="snippets/character-encoding-introduction/csharp/ConvertToUpper.cs" id="SnippetGoodExample":::

### <a name="other-opno-locrune-apis"></a>Diğer Rune API'ler

Bu `Rune` `char` tür, API'lerin çoğunun analoglarını ortaya çıkarır. Örneğin, aşağıdaki yöntemler statik API'leri türe `char` yansıtmaktadır:

* <xref:System.Text.Rune.IsLetter%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsWhiteSpace%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.IsLetterOrDigit%2A?displayProperty=nameWithType>
* <xref:System.Text.Rune.GetUnicodeCategory%2A?displayProperty=nameWithType>

Bir `Rune` örnekten ham skaler değeri elde <xref:System.Text.Rune.Value%2A?displayProperty=nameWithType> etmek için özelliği kullanın.

Bir `Rune` örneği `char`s, kullanım <xref:System.Text.Rune.ToString%2A?displayProperty=nameWithType> veya <xref:System.Text.Rune.EncodeToUtf16%2A?displayProperty=nameWithType> yöntem dizisine dönüştürmek için.

Herhangi bir Unicode skaler değer tek `char` bir veya bir vekil `Rune` çifti tarafından temsil edilebilir `char` olduğundan, herhangi bir örnek en fazla 2 örnek tarafından temsil edilebilir. Bir <xref:System.Text.Rune.Utf16SequenceLength%2A?displayProperty=nameWithType> `Rune` örneği temsil `char` etmek için kaç örnek gerektiğini görmek için kullanın.

.NET `Rune` türü hakkında daha fazla bilgi için [ `Rune` API başvurusuna](xref:System.Text.Rune)bakın.

## <a name="grapheme-clusters"></a>Grapheme kümeleri

Bir karakter gibi görünen şey, birden çok kod noktasının birleşiminden kaynaklanabilir, bu nedenle genellikle "karakter" yerine kullanılan daha açıklayıcı bir terim [grafme kümesidir.](https://www.unicode.org/glossary/#grapheme_cluster) .NET'teki eşdeğer terim [metin öğesidir.](xref:System.Globalization.StringInfo.GetTextElementEnumerator%2A)

`string` "a", "á" örneklerini göz önünde bulundurun. "á", ve`👩🏽‍🚒`" ". İşletim sisteminiz bunları Unicode standardında belirtildiği şekilde işlerse, bu `string` örneklerin her biri tek bir metin öğesi veya grafi kümesi olarak görünür. Ancak son ikisi birden fazla skaler değer kodu noktasıyla temsil edilir.

* string "A" bir skaler değerle temsil edilir `char` ve bir örnek içerir.

  * `U+0061 LATIN SMALL LETTER A`

* string "Á" bir skaler değerle temsil edilir `char` ve bir örnek içerir.

  * `U+00E1 LATIN SMALL LETTER E WITH ACUTE`

* string "Á" "á" ile aynı görünür, ancak iki skaler değerle `char` temsil edilir ve iki örnek içerir.

  * `U+0065 LATIN SMALL LETTER A`
  * `U+0301 COMBINING ACUTE ACCENT`

* Son string olarak,`👩🏽‍🚒`" " " dört skaler değerle temsil edilir ve yedi `char` örnek içerir.

  * `U+1F469 WOMAN`(ek aralığı, bir vekil çifti gerektirir)
  * `U+1F3FD EMOJI MODIFIER FITZPATRICK TYPE-4`(ek aralığı, bir vekil çifti gerektirir)
  * `U+200D ZERO WIDTH JOINER`
  * `U+1F692 FIRE ENGINE`(ek aralığı, bir vekil çifti gerektirir)

Önceki örneklerin bazılarında - vurgu değiştirici veya cilt tonu değiştirici birleştirme gibi - kod noktası ekranda bağımsız bir öğe olarak görüntülenmiyor. Bunun yerine, ondan önce gelen bir metin öğesigörünümünü değiştirmek için hizmet vermektedir. Bu örnekler, tek bir "karakter" veya "grafeme kümesi" olarak düşündüğümüz şeyi uydurmak için birden çok skaler değer gerektirebileceğini göstermektedir.

Bir `string`grapheme kümelerini sıralamak için aşağıdaki <xref:System.Globalization.StringInfo> örnekte gösterildiği gibi sınıfı kullanın. Swift'i tanıyorsanız,.NET `StringInfo` türü kavramsal olarak [ `character` Swift'in türüne](https://developer.apple.com/documentation/swift/character)benzer.

### <a name="example-count-opno-locchar-opno-locrune-and-text-element-instances"></a>Örnek: charsaymak , Runeve metin öğesi örnekleri

.NET API'lerinde grafme kümesine *metin öğesi*denir. Aşağıdaki yöntem, metin `char` `Rune`öğesi örnekleri arasındaki farkları gösterir: `string`

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCountMethod":::

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/CountTextElements.cs" id="SnippetCallCountMethod":::

Bu kodu .NET Framework veya .NET Core 3.1 veya daha önce çalıştırDıysanız, emoji için metin öğesi sayısı gösterir. `4` Bunun nedeni, `StringInfo` sınıftaki .NET 5'te sabitlenmiş bir hatadır.

### <a name="example-splitting-opno-locstring-instances"></a>Örnek: string örnekleri bölme

Örnekleri `string` bölerken, vekil çiftleri ve grafme kümelerini bölmekten kaçının. Satır sonları eklemek niyetinde yanlış kod, aşağıdaki örnek stringdüşünün:

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetBadExample":::

Bu kod örnekleri sıraladığı `char` için, 10-sınıra`char` binen bir vekil çifti bölünür ve aralarında yeni bir satır enjekte edilir. Bu ekleme, vekil kod noktaları yalnızca çiftler olarak anlamlı olduğundan, veri bozulması nı tanıtır.

Örnekler yerine örnekleri (skaler değerler) sayısalad `Rune` ederseniz, veri bozulması potansiyeli ortadan kaldırılmaz. `char` Bir dizi `Rune` örnek,`char` 10-sınıra bağlı bir grafme kümesini kapsaabilir. Grafme küme kümesi bölünürse, doğru yorumlanamaz.

Daha iyi bir yaklaşım, aşağıdaki örnekte olduğu gibi grafeme kümelerini veya metin öğelerini sayarak kırmaktır: string

:::code language="csharp" source="snippets/character-encoding-introduction/csharp/InsertNewlines.cs" id="SnippetGoodExample":::

Ancak daha önce de belirtildiği gibi, .NET 5 dışındaki `StringInfo` .NET uygulamalarında, sınıf bazı grafme kümelerini yanlış işleyebilir.

## <a name="utf-8-and-utf-32"></a>UTF-8 ve UTF-32

Önceki bölümler UTF-16'ya odaklanmıştır, çünkü .NET örnekleri `string` kodlamak için bunu kullanır. Utf-8 ve [UTF-32](https://www.unicode.org/faq/utf_bom.html#UTF32)- Unicode için diğer kodlama sistemleri vardır. [UTF-8](https://www.unicode.org/faq/utf_bom.html#UTF8) Bu kodlamalar sırasıyla 8-bit kod birimleri ve 32-bit kod birimleri kullanır.

UTF-16 gibi UTF-8 de bazı Unicode skaler değerlerini temsil etmek için birden çok kod birimi gerektirir. UTF-32, tek bir 32 bitkodlu kod birimindeki herhangi bir skaler değeri temsil edebilir.

Bu üç Unicode kodlama sisteminin her birinde aynı Unicode kod noktasının nasıl temsil edildiğini gösteren bazı örnekler aşağıda verilmiştir:

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

Daha önce belirtildiği gibi, bir [vekil çifti](#surrogate-pairs) tek bir UTF-16 kod birimi kendisi tarafından anlamsızdır. Aynı şekilde, tek bir UTF-8 kod birimi, skaler bir değeri hesaplamak için kullanılan iki, üç veya dört sırahalindeyse tek başına anlamsızdır.

### <a name="endianness"></a>Endianness

.NET'te, a'nın string UTF-16 kod birimleri bitişik bellekte 16 bittamsedi (örnekler)`char` dizisi olarak depolanır. Tek tek kod birimlerinin bitleri, geçerli mimarinin [sonluluğuna](https://en.wikipedia.org/wiki/Endianness) göre düzenlenir.

Biraz endian mimarisinde, string UTF-16 kod noktalarından `[ D801 DCCC ]` oluşan bayt olarak bellekte ortaya `[ 0x01, 0xD8, 0xCC, 0xDC ]`konulacaktır. Büyük-endian mimarisinde aynı string bayt `[ 0xD8, 0x01, 0xDC, 0xCC ]`olarak bellekte ortaya konulmuş olurdu.

Birbiriyle iletişim kurandaki bilgisayar sistemleri, kabloyu geçen verilerin temsili üzerinde anlaşmalıdır. Çoğu ağ protokolü, kısmen küçük endian makinesiyle iletişim kuran büyük endian makinesinden kaynaklanabilir sorunları önlemek için, metin aktarırken UTF-8'i standart olarak kullanır. UTF-8 kod noktalarından string `[ F0 90 93 8C ]` oluşan her zaman endianness `[ 0xF0, 0x90, 0x93, 0x8C ]` ne olursa olsun bayt olarak temsil edilecektir.

Metin iletmek için UTF-8 kullanmak için ,NET uygulamaları genellikle aşağıdaki örnekgibi kod kullanır:

```csharp
string stringToWrite = GetString();
byte[] stringAsUtf8Bytes = Encoding.UTF8.GetBytes(stringToWrite);
await outputStream.WriteAsync(stringAsUtf8Bytes, 0, stringAsUtf8Bytes.Length);
```

Önceki örnekte, Yöntem [Encoding.UTF8.GetBytes](xref:System.Text.UTF8Encoding.GetBytes%2A) unicode skaler `string` değerleri bir dizi geri UTF-16 deşifre, sonra UTF-8 içine bu skaler değerleri yeniden kodlar ve bir `byte` dizi içine ortaya çıkan sırayı yerleştirir. Yöntem [Encoding.UTF8.GetString](xref:System.Text.UTF8Encoding.GetString%2A) bir UTF-8 `byte` dizi bir UTF-16 `string`dönüştürerek, ters dönüşüm gerçekleştirir.

> [!WARNING]
> UTF-8 internet üzerinde olağan olduğundan, tel ham bayt okumak ve UTF-8 sanki verileri tedavi etmek cazip olabilir. Ancak, gerçekten iyi biçimlendirilmiş olduğunu doğrulamak gerekir. Kötü niyetli bir istemci kötü biçimlendirilmiş UTF-8'i hizmetinize gönderebilir. Bu verileri iyi biçimlendirilmiş gibi çalıştırArsanız, uygulamanızda hatalara veya güvenlik açıklarına neden olabilir. UTF-8 verilerini doğrulamak için, `Encoding.UTF8.GetString`gelen verileri bir . `string`

### <a name="well-formed-encoding"></a>İyi biçimlendirilmiş kodlama

İyi biçimlendirilmiş Unicode kodlaması, string unicode skaler değerleri dizisine hatasız ve hatasız olarak çözülebilen kod birimlerinden biridir. İyi biçimlendirilmiş veriler UTF-8, UTF-16 ve UTF-32 arasında serbestçe ileri geri kodlanabilir.

Kodlama dizisinin iyi oluşup oluşmadığı sorusu, bir makinenin mimarisinin sonilişkisiyle ilgisi yoktur. Kötü biçimlendirilmiş bir UTF-8 dizisi hem büyük endian hem de küçük endian makinelerde aynı şekilde kötü biçimlendirilmiştir.

Aşağıda, yanlış biçimlendirilmiş kodlamalara bazı örnekler verilmiştir:

* UTF-8'de, `[ 6C C2 61 ]` dizi kötü biçimlendirilmiştir `C2` çünkü `61`takip edilemez.

* UTF-16'da, `[ DC00 DD00 ]` düşük vekil başka bir string `"\udc00\udd00"`düşük vekil `DC00` `DD00`tarafından takip edilemediği için dizi (veya C#, the) kötü biçimlendirilir.

* UTF-32'de, `[ 0011ABCD ]` Unicode skaler değerlerinin aralığının dışında `0011ABCD` olduğu için dizi kötü biçimlendirilir.

.NET'te, `string` örnekler hemen hemen her zaman iyi biçimlendirilmiş UTF-16 verileri içerir, ancak bu garanti değildir. Aşağıdaki örnekler, kötü biçimlendirilmiş UTF-16 verilerini örneklerde `string` oluşturan geçerli C# kodunu gösterir.

* Kötü biçimli bir edebi:

  ```csharp
  const string s = "\ud800";
  ```

* Bir vekil çifti ayıran bir alt dize:

  ```csharp
  string x = "\ud83e\udd70"; // "🥰"
  string y = x.Substring(1, 1); // "\udd70" standalone low surrogate
  ```

API'ler kötü biçimlendirilmiş [`Encoding.UTF8.GetString`](xref:System.Text.UTF8Encoding.GetString%2A) `string` örnekleri asla iade etmek gibi. `Encoding.GetString`ve `Encoding.GetBytes` yöntemler girişte yanlış biçimlendirilmiş dizileri algılar ve çıktıyı oluştururken karakter ikamesi gerçekleştirir. Örneğin, girişte ASCII olmayan bir bayt [`Encoding.ASCII.GetString(byte[])`](xref:System.Text.ASCIIEncoding.GetString%2A) görürse (U+0000..U+007F aralığının dışında), döndürülen `string` örneğe bir '?' ekler. [`Encoding.UTF8.GetString(byte[])`](xref:System.Text.UTF8Encoding.GetString%2A)kötü biçimlendirilmiş UTF-8 dizilerini `U+FFFD REPLACEMENT CHARACTER ('�')` döndürülen `string` örnekte değiştirir. Daha fazla bilgi için [Unicode Standardı,](https://www.unicode.org/versions/latest/)Bölüm 5.22 ve 3.9'a bakın.

Yerleşik `Encoding` sınıflar, yanlış biçimlendirilmiş diziler görüldüğünde karakter ikamesi gerçekleştirmek yerine bir özel durum atmak için de yapılandırılabilir. Bu yaklaşım genellikle karakter değiştirmenin kabul edilemeyebildiği güvenliğe duyarlı uygulamalarda kullanılır.

```csharp
byte[] utf8Bytes = ReadFromNetwork();
UTF8Encoding encoding = new UTF8Encoding(encoderShouldEmitUTF8Identifier: false, throwOnInvalidBytes: true);
string asString = encoding.GetString(utf8Bytes); // will throw if 'utf8Bytes' is ill-formed
```

Yerleşik `Encoding` sınıfların nasıl kullanılacağı hakkında bilgi için [.NET'te karakter kodlama sınıfları nasıl kullanılır.](character-encoding.md)

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String>
- <xref:System.Char>
- <xref:System.Text.Rune>
- [Küreselleşme ve Yerelleştirme](../../../docs/standard/globalization-localization/index.md)
