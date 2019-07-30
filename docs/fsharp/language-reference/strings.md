---
title: Dizeler
description: F# ' Dize ' türünün Unicode karakter dizisi olarak sabit metni nasıl temsil ettiğini öğrenin.
ms.date: 07/05/2019
ms.openlocfilehash: 284de939c90c4d9d4ea064fb4db1fb90a37038e2
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627109"
---
# <a name="strings"></a>Dizeler

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları sizi MSDN 'ye götürür.  Docs.microsoft.com API başvurusu tamamlanmadı.

Tür `string` , Unicode karakter dizisi olarak sabit metni temsil eder. `string`, .NET Framework için `System.String` bir diğer addır.

## <a name="remarks"></a>Açıklamalar

Dize sabit değerleri tırnak işareti (") karakteriyle sınırlandırılmıştır. Ters eğik çizgi karakteri \\ () belirli özel karakterleri kodlamak için kullanılır. Ters eğik çizgi ve sonraki karakter birlikte *kaçış sırası*olarak bilinir. F# Dize sabit değerlerinde desteklenen kaçış dizileri aşağıdaki tabloda gösterilmiştir.

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
|Unicode karakter|`\DDD`(ondalık basamağı `\231` belirtir;000-255aralığı;Örneğin,=`D` "ç")|
|Unicode karakter|`\xHH`(onaltılık basamağı `\xE7` belirtir;00-FFaralığı;Örneğin,=`H` "ç")|
|Unicode karakter|`\uHHHH`(UTF-16) (onaltılık basamağı belirtir; 0000-ffff aralığı; `H`  Örneğin, `\u00E7` = "ç")|
|Unicode karakter|`\U00HHHHHH`(UTF-32) (onaltılık basamağı belirtir; 000000 yazın-10FFFF) aralığı `H`  Örneğin, `\U0001F47D` = "👽")|

> [!IMPORTANT]
> `\DDD` Kaçış sırası, diğer dillerin çoğunda, sekizli gösterimi değil ondalık gösterimidir. Bu nedenle, `8` rakamlar `9` ve geçerli ve bir dizisi `\032` bir boşluk (U + 0020) temsil ederken, sekizlik gösterimde aynı kod noktası olur `\040`.

> [!NOTE]
> 0-255 (0xFF) `\DDD` aralığıyla sınırlandırılmakta, ve `\x` kaçış dizileri, ilk 256 Unicode kod noktalarıyla eşleştiğinden, etkin şekilde [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) karakter kümesidir.

Önünde @ sembolü varsa, değişmez değer tam bir dizedir. Bu, iki tırnak işareti karakterinin tek tırnak işareti karakteri olarak yorumlanmasının dışında, tüm kaçış dizileri yok sayılır.

Ayrıca, bir dize, Üçlü tırnak içine alınmış olabilir. Bu durumda, çift tırnak işareti karakterleri de dahil olmak üzere tüm kaçış dizileri yok sayılır. Katıştırılmış bir alıntı dize içeren bir dize belirtmek için, tam bir dize veya Üçlü tırnak işareti kullanabilirsiniz. Tam bir dize kullanırsanız, tek tırnak işareti karakterini göstermek için iki tırnak işareti karakteri belirtmeniz gerekir. Üçlü olarak tırnak içine alınmış bir dize kullanırsanız, tek tırnak işareti karakterlerini dizenin sonu olarak ayrıştırılmaksızın kullanabilirsiniz. Bu teknik, ekli tırnak işaretleri içeren XML veya diğer yapılarla çalışırken yararlı olabilir.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

Kod içinde, satır sonları içeren dizeler kabul edilir ve satır sonları satır sonundan önce son karakter olan bir ters eğik çizgi karakteri olmayan bir şekilde newlines olarak yorumlanır. Ters eğik çizgi karakteri kullanıldığında sonraki satırdaki baştaki boşluk yok sayılır. Aşağıdaki kod değeri `"abc\ndef"` olan bir dize `str1` ve değeri `"abcdef"`olan bir `str2` dize oluşturur.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Bir dizedeki ayrı karakterlere, aşağıdaki gibi dizi benzeri sözdizimini kullanarak erişebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Çıktı `b`.

Ya da aşağıdaki kodda gösterildiği gibi, dizi dilimi söz dizimini kullanarak alt dizeleri de ayıklayabilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Çıktı aşağıdaki gibidir:

```
abc
def
```

ASCII dizelerini işaretsiz bayt dizileri ile temsil edebilirsiniz, şunu yazın `byte[]`. Bir ASCII dizesi olduğunu `B` göstermek için son eki bir dize değişmez değerine eklersiniz. Bayt dizileri ile kullanılan ASCII dize sabit değerleri, Unicode kaçış dizileri hariç, Unicode dizeleriyle aynı kaçış dizilerini destekler.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Dize İşleçleri

Dizeleri birleştirmek için iki yol vardır: `+` işlecini kullanarak veya `^` işlecini kullanarak. `+` İşleci .NET Framework dize işleme özellikleriyle uyumluluğu korur.

Aşağıdaki örnekte dize birleştirme gösterilmektedir.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>String sınıfı

İçindeki F# dize türü aslında .NET Framework `System.String` bir `System.String` tür olduğundan tüm Üyeler kullanılabilir. Bu, dizeleri `+` `Length` , özelliği ve `Chars` bir Unicode karakter dizisi olarak dizeyi döndüren özelliğini birleştirmek için kullanılan işleci içerir. Dizeler hakkında daha fazla bilgi için bkz `System.String`.

`Chars` Özelliğini kullanarak ,aşağıdakikoddagösterildiğigibibirdizinbelirterekbirdizedeki`System.String`ayrı karakterlere erişebilirsiniz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>Dize modülü

Dize işleme için ek işlevler, `String` `FSharp.Core` ad alanındaki modüle dahil edilmiştir. Daha fazla bilgi için bkz. [Core. String modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
