---
title: Dizeler
description: Bilgi nasıl F# 'string' türü sabit metin Unicode karakter dizisi olarak temsil eder.
ms.date: 07/05/2019
ms.openlocfilehash: ec895723cc6d21a701a27b5d70d053bb681ce2b3
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660605"
---
# <a name="strings"></a>Dizeler

> [!NOTE]
> Bu makaledeki API başvuru bağlantıları için MSDN sürer.  Docs.microsoft.com API başvuru tamamlanmadı.

`string` Türü sabit metin Unicode karakter dizisi olarak temsil eder. `string` için bir diğer addır `System.String` .NET Framework'teki.

## <a name="remarks"></a>Açıklamalar

Dize değişmez değerleri tırnak işareti (") karakteriyle ayrılır. Ters eğik çizgi karakteri ( \\ ) özel karakterleri kodlamak için kullanılır. Ters eğik çizgi ve birlikte sonraki karakteri olarak bilinen bir *kaçış dizisi*. Kaçış dizileri desteklenen F# dize değişmez değerleri aşağıdaki tabloda gösterilmiştir.

|Karakter|Kaçış sırası|
|---------|---------------|
|Uyarı|`\a`|
|Geri Al tuşu|`\b`|
|form besleme|`\f`|
|Yeni satır|`\n`|
|satır başı|`\r`|
|Tab|`\t`|
|dikey sekme|`\v`|
|Ters eğik çizgi|`\\`|
|Tırnak işareti|`\"`|
|Kesme işareti|`\'`|
|Unicode karakter|`\DDD` (burada `D` gösteren bir ondalık basamak; aralığı 000 - 255; Örneğin, `\231` "ç" =)|
|Unicode karakter|`\xHH` (burada `H` onaltılık bir basamaktır; 00 - FF; aralığını gösteren örnek `\xE7` "ç" =)|
|Unicode karakter|`\uHHHH` (UTF-16) (burada `H` onaltılık bir basamaktır; 0000 - FFFF; aralığını gösterir  Örneğin, `\u00E7` "ç" =)|
|Unicode karakter|`\U00HHHHHH` (UTF-32) (burada `H` onaltılık bir basamaktır; 000000 - 10FFFF; aralığını gösterir  Örneğin, `\U0001F47D` = "👽")|

> [!IMPORTANT]
> `\DDD` Kaçış dizisi olan ondalık gösterim, çoğu dil gibi değil sekizlik gösterim. Bu nedenle, basamak `8` ve `9` geçerli olduğundan ve bir dizi `\032` bir alanını temsil eder (U + 0020), o aynı kod noktası sekizlik gösterimde olabilir ancak `\040`.

> [!NOTE]
> 0 aralığına kısıtlanmasını - 255 (0xFF) `\DDD` ve `\x` kaçış dizileri, esas [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , ilk 256 Unicode kod noktaları eşleştiğinden karakter kümesi.

Öncesinde, @ sembolü, değişmez değer verbatim bir dizedir. İki tırnak karakteri tek tırnak işareti karakteri yorumlanır dışında bu, herhangi bir kaçış dizileri göz ardı, anlamına gelir.

Ayrıca, bir dize Üçlü tırnak işareti içine alınabilir. Bu durumda, çift tırnak işareti karakterleri dahil olmak üzere tüm kaçış dizileri yoksayılır. Sınırlandırılmış bir katıştırılmış içeren bir dize belirtmek için ya da bir harfi harfine veya bir Üçlü alıntılanmış dize kullanabilirsiniz. Verbatim dizesi kullanıyorsanız, iki tırnak karakteri tek tırnak işareti karakteri belirtmek için belirtmeniz gerekir. Üçlü tırnak içine bir dize kullanmak, bunları dize sonu Ayrıştırılmakta olmadan tek tırnak işareti karakter kullanabilirsiniz. Bu teknik, XML veya katıştırılmış tırnak işaretleri dahil diğer yapılar çalışırken yararlı olabilir.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

Kodda satır sonları olan dizeleri kabul edilir ve son karakter satır sonundan önce bir ters eğik çizgi karakteri olmadığı sürece satır sonları tam anlamıyla yeni satırlardan yorumlanır. Ters eğik çizgi karakteri kullanıldığında sonraki satıra önde gelen boşluk yoksayılır. Aşağıdaki kod bir dize üretir `str1` değeri olan `"abc\ndef"` ve bir dize `str2` değeri olan `"abcdef"`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Aşağıdaki gibi bir dizi benzeri sözdizimi kullanarak, bir dizedeki karakterlerin tek tek erişebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Çıktı `b`.

Veya, alt dizeler dizisi dilim söz dizimini kullanarak aşağıdaki kodda gösterildiği gibi ayıklayabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Çıktı aşağıdaki gibidir:

```
abc
def
```

ASCII dizelerinde işaretsiz bayt sayısı, türü bir dizi temsil edebilen `byte[]`. Sonek Ekle `B` için bir ASCII dizesi olduğunu belirten bir dize. Bayt dizileri ile kullanılan ASCII dize değişmez değerleri, Unicode kaçış dizileri dışında Unicode dize olarak aynı kaçış dizileri destekler.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a>Dize İşleçleri

Dizeleri birleştirmek için iki yolu vardır: kullanarak `+` işleci kullanarak veya `^` işleci. `+` İşleci özellikleri işleme .NET Framework dize ile uyumluluk sağlar.

Aşağıdaki örnekte, dize birleştirme gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a>Dize sınıfı

Çünkü dize türü içinde F# aslında bir .NET Framework `System.String` yazın, tümünü `System.String` üyeleri kullanılabilir. Bu içerir `+` dizeyi birleştirmek için kullanılır, operatör `Length` özelliği ve `Chars` dize Unicode karakter dizisi olarak döndüren özellik. Dizeleri hakkında daha fazla bilgi için bkz. `System.String`.

Kullanarak `Chars` özelliği `System.String`, aşağıdaki kodda gösterildiği gibi bir dizin belirterek, bir dizedeki karakterlerin tek tek erişebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a>String modülü

Dize işleme için ek işlevler dahil `String` modülünde `FSharp.Core` ad alanı. Daha fazla bilgi için [Core.String modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Ayrıca bkz.

- [F# Dili Başvurusu](index.md)
