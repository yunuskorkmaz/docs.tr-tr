---
title: Dizeler
description: "F # ' String ' türünün Unicode karakter dizisi olarak sabit metni nasıl temsil ettiğini öğrenin."
ms.date: 08/15/2020
ms.openlocfilehash: f6ec36feeb197bf785c702e7b626cf5cf80696ab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812217"
---
# <a name="strings"></a>Dizeler

`string`Tür, Unicode karakter dizisi olarak sabit metni temsil eder. `string` , .NET içindeki için bir diğer addır `System.String` .

## <a name="remarks"></a>Açıklamalar

Dize sabit değerleri tırnak işareti (") karakteriyle sınırlandırılmıştır. Ters eğik çizgi karakteri ( \\ ) belirli özel karakterleri kodlamak için kullanılır. Ters eğik çizgi ve sonraki karakter birlikte *kaçış sırası*olarak bilinir. F # dize değişmez değerlerinde desteklenen kaçış dizileri aşağıdaki tabloda gösterilmiştir.

|Karakter|Kaçış sırası|
|---------|---------------|
|Uyarı|`\a`|
|Geri Al tuşu|`\b`|
|Form akışı|`\f`|
|Metninde|`\n`|
|Satır başı|`\r`|
|Tab|`\t`|
|Dikey sekme|`\v`|
|Sola|`\\`|
|Tırnak işareti|`\"`|
|Kesme işareti|`\'`|
|Unicode karakter|`\DDD` ( `D` ondalık basamağı belirtir; 000-255 aralığı; Örneğin, `\231` = "ç")|
|Unicode karakter|`\xHH` ( `H` onaltılık basamağı belirtir; 00-FF aralığı; Örneğin, `\xE7` = "ç")|
|Unicode karakter|`\uHHHH` (UTF-16) ( `H` onaltılık basamağı belirtir; 0000-ffff aralığı;  Örneğin, `\u00E7` = "ç")|
|Unicode karakter|`\U00HHHHHH` (UTF-32) ( `H` onaltılık basamağı belirtir; 000000 yazın-10FFFF) aralığı  Örneğin, `\U0001F47D` = " 👽 ")|

> [!IMPORTANT]
> `\DDD`Kaçış sırası, diğer dillerin çoğunda, sekizli gösterimi değil ondalık gösterimidir. Bu nedenle, rakamlar `8` ve `9` geçerli ve bir dizisi `\032` bir boşluk (U + 0020) temsil ederken, sekizlik gösterimde aynı kod noktası olur `\040` .

> [!NOTE]
> 0-255 (0xFF) aralığıyla sınırlandırılmakta, `\DDD` ve `\x` kaçış dizileri, Ilk 256 Unicode kod noktalarıyla eşleştiğinden, etkin şekilde [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) karakter kümesidir.

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

Kod içinde, satır sonları içeren dizeler kabul edilir ve satır sonları satır sonundan önce son karakter olan bir ters eğik çizgi karakteri olmayan bir şekilde newlines olarak yorumlanır. Ters eğik çizgi karakteri kullanıldığında sonraki satırdaki baştaki boşluk yok sayılır. Aşağıdaki kod değeri olan bir dize `str1` `"abc\ndef"` ve değeri olan bir dize oluşturur `str2` `"abcdef"` .

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a>Dize dizinleme ve dilimleme

Bir dizedeki ayrı karakterlere, aşağıdaki gibi dizi benzeri sözdizimini kullanarak erişebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Çıktı `b` olur.

Ya da aşağıdaki kodda gösterildiği gibi, dizi dilimi söz dizimini kullanarak alt dizeleri de ayıklayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Çıktı aşağıdaki gibidir:

```console
abc
def
```

ASCII dizelerini işaretsiz bayt dizileri ile temsil edebilirsiniz, şunu yazın `byte[]` . Bir `B` ASCII dizesi olduğunu göstermek için son eki bir dize değişmez değerine eklersiniz. Bayt dizileri ile kullanılan ASCII dize sabit değerleri, Unicode kaçış dizileri hariç, Unicode dizeleriyle aynı kaçış dizilerini destekler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Dize İşleçleri

`+`İşleci, .NET Framework dize işleme özellikleriyle uyumluluğu korumak için dizeleri birleştirmek üzere kullanılabilir. Aşağıdaki örnekte dize birleştirme gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>String sınıfı

F # ' deki dize türü aslında .NET Framework bir tür olduğundan `System.String` tüm `System.String` Üyeler kullanılabilir. Bu, `+` dizeleri, `Length` özelliği ve `Chars` bir Unicode karakter dizisi olarak dizeyi döndüren özelliğini birleştirmek için kullanılan işleci içerir. Dizeler hakkında daha fazla bilgi için bkz `System.String` ..

`Chars`Özelliğini kullanarak `System.String` , aşağıdaki kodda gösterildiği gibi bir dizin belirterek bir dizedeki ayrı karakterlere erişebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Dize modülü

Dize işleme için ek işlevler, `String` ad alanındaki modüle dahil edilmiştir `FSharp.Core` . Daha fazla bilgi için bkz. [dize modülü](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html).

## <a name="see-also"></a>Ayrıca bkz.

- [F # dil başvurusu](index.md)
