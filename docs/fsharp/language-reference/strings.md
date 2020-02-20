---
title: Dizeler
description: F# ' Dize ' türünün Unicode karakter dizisi olarak sabit metni nasıl temsil ettiğini öğrenin.
ms.date: 07/05/2019
ms.openlocfilehash: 002de464d09a49b6161608db6e46c619369f5ceb
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452824"
---
# <a name="strings"></a>Dizeler

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları sizi MSDN 'ye götürür.  Docs.microsoft.com API başvurusu tamamlanmadı.

`string` türü, Unicode karakter dizisi olarak sabit metni temsil eder. `string`, .NET Framework `System.String` için bir diğer addır.

## <a name="remarks"></a>Açıklamalar

Dize sabit değerleri tırnak işareti (") karakteriyle sınırlandırılmıştır. Ters eğik çizgi karakteri (\\) belirli özel karakterleri kodlamak için kullanılır. Ters eğik çizgi ve sonraki karakter birlikte *kaçış sırası*olarak bilinir. F# Dize sabit değerlerinde desteklenen kaçış dizileri aşağıdaki tabloda gösterilmiştir.

|Karakter|Kaçış sırası|
|---------|---------------|
|Uyarı|`\a`|
|Geri Al tuşu|`\b`|
|Form akışı|`\f`|
|Metninde|`\n`|
|Satır başı|`\r`|
|Tab|`\t`|
|Dikey sekme|`\v`|
|Ters eğik çizgi|`\\`|
|Tırnak işareti|`\"`|
|Kesme işareti|`\'`|
|Unicode karakter|`\DDD` (`D` ondalık basamağı gösterir; 000-255 aralığı; Örneğin, `\231` = "ç")|
|Unicode karakter|`\xHH` (`H` on altılı bir basamak, 00-FF aralığı; Örneğin, `\xE7` = "ç")|
|Unicode karakter|`\uHHHH` (UTF-16) (`H` onaltılık bir basamak, 0000-FFFF) aralığı;  Örneğin, `\u00E7` = "ç")|
|Unicode karakter|`\U00HHHHHH` (UTF-32) (`H` onaltılık bir basamak gösterir; 000000 yazın-10FFFF) aralığı  Örneğin, `\U0001F47D` = "👽")|

> [!IMPORTANT]
> `\DDD` kaçış sırası, diğer dillerin çoğunda, sekizli gösterimde değil ondalık gösterimidir. Bu nedenle, `8` ve `9` basamakları geçerlidir ve bir `\032` dizisi bir boşluk (U + 0020) temsil ederken, sekizlik gösterimde aynı kod noktası `\040`olur.

> [!NOTE]
> 0-255 (0xFF) aralığıyla sınırlandırılmakta, `\DDD` ve `\x` kaçış dizileri, ilk 256 Unicode kod noktalarıyla eşleştiğinden, etkin şekilde [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) karakter kümesidir.

## <a name="verbatim-strings"></a>Tam dizeler

Önünde @ sembolü varsa, değişmez değer tam bir dizedir. Bu, iki tırnak işareti karakterinin tek tırnak işareti karakteri olarak yorumlanmasının dışında, tüm kaçış dizileri yok sayılır.

## <a name="triple-quoted-strings"></a>Üçlü alıntılanmış dizeler

Ayrıca, bir dize, Üçlü tırnak içine alınmış olabilir. Bu durumda, çift tırnak işareti karakterleri de dahil olmak üzere tüm kaçış dizileri yok sayılır. Katıştırılmış bir alıntı dize içeren bir dize belirtmek için, tam bir dize veya Üçlü tırnak işareti kullanabilirsiniz. Tam bir dize kullanırsanız, tek tırnak işareti karakterini göstermek için iki tırnak işareti karakteri belirtmeniz gerekir. Üçlü olarak tırnak içine alınmış bir dize kullanırsanız, tek tırnak işareti karakterlerini dizenin sonu olarak ayrıştırılmaksızın kullanabilirsiniz. Bu teknik, ekli tırnak işaretleri içeren XML veya diğer yapılarla çalışırken yararlı olabilir.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

Kod içinde, satır sonları içeren dizeler kabul edilir ve satır sonları satır sonundan önce son karakter olan bir ters eğik çizgi karakteri olmayan bir şekilde newlines olarak yorumlanır. Ters eğik çizgi karakteri kullanıldığında sonraki satırdaki baştaki boşluk yok sayılır. Aşağıdaki kod, değer `"abc\ndef"` olan bir dize `str1` ve değer `"abcdef"`olan bir dize `str2` üretir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>Dize dizinleme ve dilimleme

Bir dizedeki ayrı karakterlere, aşağıdaki gibi dizi benzeri sözdizimini kullanarak erişebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Çıktı `b`.

Ya da aşağıdaki kodda gösterildiği gibi, dizi dilimi söz dizimini kullanarak alt dizeleri de ayıklayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Çıktı aşağıdaki gibidir:

```console
abc
def
```

ASCII dizelerini işaretsiz bayt dizileri ile temsil edebilirsiniz, `byte[]`yazın. Bir dize sabit değerinin bir ASCII dizesi olduğunu göstermek için sonek `B` eklersiniz. Bayt dizileri ile kullanılan ASCII dize sabit değerleri, Unicode kaçış dizileri hariç, Unicode dizeleriyle aynı kaçış dizilerini destekler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Dize İşleçleri

Dizeleri birleştirmek için iki yol vardır: `+` işlecini veya `^` işlecini kullanarak. `+` işleci, .NET Framework dize işleme özellikleriyle uyumluluğu korur.

Aşağıdaki örnekte dize birleştirme gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>String sınıfı

İçindeki F# dize türü aslında bir .NET Framework `System.String` türü olduğundan, tüm `System.String` üyeleri kullanılabilir. Bu, dizeleri birleştirmek için kullanılan `+` işlecini, `Length` özelliğini ve dizeyi bir Unicode karakter dizisi olarak döndüren `Chars` özelliğini içerir. Dizeler hakkında daha fazla bilgi için bkz. `System.String`.

`System.String``Chars` özelliğini kullanarak, aşağıdaki kodda gösterildiği gibi bir dizin belirterek bir dizedeki ayrı karakterlere erişebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Dize modülü

Dize işleme için ek işlevler, `FSharp.Core` ad alanındaki `String` modülüne dahildir. Daha fazla bilgi için bkz. [Core. String modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
