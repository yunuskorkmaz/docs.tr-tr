---
title: Dizeler
description: F# 'string' türünün değişmez metni Unicode karakter dizisi olarak nasıl temsil edeni öğrenin.
ms.date: 07/05/2019
ms.openlocfilehash: 242a2cefa1cce8995090dddd1d1fd7181e0f5e0c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739563"
---
# <a name="strings"></a>Dizeler

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları sizi MSDN'ye götürür.  docs.microsoft.com API başvurusu tamamlanmadı.

Tür, `string` değişmez metni Unicode karakter dizisi olarak temsil eder. `string`.NET Framework'de bir `System.String` diğer addır.

## <a name="remarks"></a>Açıklamalar

String literals tırnak işareti (") karakteri ile sınırlıdır. Ters eğik \\ çizgi karakteri ( ) belirli özel karakterleri kodlamak için kullanılır. Backslash ve sonraki karakter birlikte bir *kaçış dizisi*olarak bilinir. F# string literals desteklenen kaçış dizileri aşağıdaki tabloda gösterilmiştir.

|Karakter|Kaçış sırası|
|---------|---------------|
|Uyarı|`\a`|
|Geri Al tuşu|`\b`|
|Form akışı|`\f`|
|Newline|`\n`|
|Satır başı|`\r`|
|Tab|`\t`|
|Dikey sekme|`\v`|
|Ters eğik çizgi|`\\`|
|Teklif işareti|`\"`|
|Kesme işareti|`\'`|
|Unicode karakter|`\DDD`(ondalık basamak gösterir; `D` 000 - 255 aralığı; `\231` örneğin, = "ç")|
|Unicode karakter|`\xHH`(hexadecimal `H` basamak; 00 - FF aralığı; örneğin `\xE7` , = "ç")|
|Unicode karakter|`\uHHHH`(UTF-16) (burada `H` bir hexadecimal basamak gösterir; 0000 aralığı - FFFF;  örneğin, `\u00E7` = "ç")|
|Unicode karakter|`\U00HHHHHH`(UTF-32) (hexadecimal `H` basamak gösterir; 000000 - 10FFFF aralığı;  örneğin, `\U0001F47D` =👽" ")|

> [!IMPORTANT]
> Kaçış `\DDD` sırası ondalık gösterimdir, diğer dillerdeki gibi sekizli gösterim değildir. Bu nedenle, `8` `9` basamak ve geçerli ve `\032` bir boşluk (U+0020) temsil eder, octal gösterimaynı `\040`kod noktası ise .

> [!NOTE]
> 0 - 255 (0xFF) aralığıyla sınırlandırılan `\x` ve `\DDD` kaçış sekansları, ilk 256 Unicode kod puanıyla eşleştiğinden etkili bir şekilde [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) karakter kümesidir.

## <a name="verbatim-strings"></a>Verbatim Dizeleri

@ sembolünden önce yse, literal harfi harfi harfine dizedir. Bu, iki tırnak işareti karakterinin bir tırnak işareti karakteri olarak yorumlanması dışında, herhangi bir kaçış dizisinin yoksayılması anlamına gelir.

## <a name="triple-quoted-strings"></a>Üçlü Tırnaklı Dizeleri

Ayrıca, bir dize üçlü tırnak ile eklenebilir. Bu durumda, çift tırnak işareti karakterleri de dahil olmak üzere tüm kaçış dizileri yoksayılır. Katıştılı bir alıntı dizesini içeren bir dize belirtmek için, bir harfi harfini veya üç tırnaklı dizeyi kullanabilirsiniz. Bir harfi harfini dize kullanıyorsanız, tek bir tırnak işareti karakterini belirtmek için iki tırnak işareti karakteri belirtmeniz gerekir. Üç tırnaklı bir dize kullanıyorsanız, tek tırnak işareti karakterlerini dize sonu olarak ayrıştıolmadan kullanabilirsiniz. Bu teknik, XML veya gömülü tırnak işaretleri içeren diğer yapılarla çalışırken yararlı olabilir.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

Kodda, satır sonları olan dizeleri kabul edilir ve satır sonu, satır sonu kesmeden önceki son karakter olmadığı sürece, tam anlamıyla yeni satırlar olarak yorumlanır. Ters eğik çizgi karakteri kullanıldığında bir sonraki satırda satırda satır satır beyaz boşluk yoksayılır. `str1` Aşağıdaki kod değeri `"abc\ndef"` olan bir dize `str2` ve `"abcdef"`değeri olan bir dize üretir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>Dize Dizini Oluşturma ve Dilimleme

Dizi benzeri sözdizimini kullanarak bir dizedeki tek tek karakterlere erişebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Çıktı. `b`

Veya aşağıdaki kodda gösterildiği gibi dizi dilimi sözdizimini kullanarak alt dizeleri ayıklayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Çıktı aşağıdaki gibidir:

```console
abc
def
```

ASCII dizelerini imzasız bayt dizilerine göre `byte[]`temsil edebilirsiniz. Bir ASCII `B` dize olduğunu belirtmek için bir dize literal soneki ekleyin. Byte dizileriyle kullanılan ASCII dize literalleri, Unicode kaçış dizileri dışında Unicode dizeleriyle aynı kaçış dizilerini destekler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Dize İşleçleri

İşleç, `+` .NET Framework dize işleme özellikleriyle uyumluluğu koruyarak dizeleri birleştirmek için kullanılabilir. Aşağıdaki örnek, dize boğma gösterir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Yaylı Çalgılar Sınıfı

F# dize türü aslında bir .NET Framework `System.String` `System.String` türü olduğundan, tüm üyeler kullanılabilir. Bu, `+` dizeleri, `Length` özelliği ve diziyi Unicode karakter `Chars` dizisi olarak döndüren özelliği birleştirmek için kullanılan işleci içerir. Dizeleri hakkında daha fazla `System.String`bilgi için bkz.

`System.String`, özelliğini kullanarak, `Chars` aşağıdaki kodda gösterildiği gibi bir dizin belirterek bir dize tek tek karakterlererişebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Yaylı Modül

Dize işleme için ek işlevsellik `String` `FSharp.Core` ad alanında modüle dahildir. Daha fazla bilgi için [Core.String Modülü'ne](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d)bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dil Referansı](index.md)
