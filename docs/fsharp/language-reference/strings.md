---
title: Dizeler (F#)
description: "F # 'string' türü değişmez metin Unicode karakter dizisi nasıl temsil öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: df7624e5-ca6c-4e77-9e2b-87ca7e5e6f52
ms.openlocfilehash: 96a398ebcd53681481b10d1a2bee5f1e5442a5cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="strings"></a>Dizeler

> [!NOTE]
Bu makalede API başvuru bağlantılar için MSDN götürür.  Docs.microsoft.com API Başvurusu tamamlanmadı.

`string` Türü değişmez metin Unicode karakter dizisi temsil eder. `string`bir diğer adı için `System.String` .NET Framework'teki.

## <a name="remarks"></a>Açıklamalar
Dize değişmez değerleri tırnak işareti (") karakteriyle ayrılmış. Ters eğik çizgi karakteri (\) özel karakterleri kodlamak için kullanılır. Ters eğik çizgi ve birlikte sonraki karakteri olarak bilinen bir *kaçış dizisi*. Kaçış dizilerine değişmez değerleri aşağıdaki tabloda gösterilen F # dize desteklenir.

|Karakter|Kaçış sırası|
|---------|---------------|
|Geri Al tuşu|\b|
|Yeni satır|\n|
|satır başı|\r|
|Tab|\t|
|ters eğik çizgi|\\|
|Tırnak işareti|\"|
|Kesme işareti|\'|
|Unicode karakter|\u*XXXX* veya \U*XXXXXXXX* (burada *X* onaltılık basamak gösterir)|

Öncesinde, @ sembolü, sabit verbatim bir dizedir. İki tırnak işareti karakteri tek tırnak işareti karakteri olarak yorumlanır dışında bu, tüm çıkış sıraları göz ardı, anlamına gelir.

Ayrıca, bir dize Üçlü tırnak içine. Bu durumda, çift tırnak işareti karakterleri dahil olmak üzere tüm çıkış sıraları yoksayılır. Sınırlandırılmış bir katıştırılmış içeren bir dize belirtmek için ya da bir verbatim veya Üçlü tırnak içine alınmış bir dize kullanabilirsiniz. Harfi harfine bir dize kullanmak, tek tırnak işareti karakteri belirtmek için iki tırnak işareti karakteri belirtmeniz gerekir. Üçlü tırnak içine alınmış bir dize kullanmak, bunları dize sonu Ayrıştırılmakta olmadan tek tırnak işareti karakter kullanabilirsiniz. Bu yöntem, XML veya katıştırılmış tırnak işaretleri dahil diğer yapıları çalışırken yararlı olabilir.

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

Kodda, satır sonları sahip dizeleri kabul edilir ve satır sonundan önceki son karakter bir ters bölü karakteri olmadığı sürece satır sonları tam anlamıyla satır başı yorumlanır. Ters eğik çizgi karakteri kullanıldığında, sonraki satıra öndeki boşlukları göz ardı edilir. Aşağıdaki kod bir dize oluşturur `str1` değeri olan `"abc\n     def"` ve bir dize `str2` değeri olan `"abcdef"`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

Bir dizede tek tek karakterleri şekilde dizi benzeri sözdizimi kullanarak erişebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

Çıktı `b`.

Veya, alt dizeler dizisi dilim sözdizimini kullanarak aşağıdaki kodda gösterildiği gibi ayıklayabilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

Çıktı aşağıdaki gibidir:

```
abc
def
```

İmzasız bayt sayısı, türü diziler tarafından ASCII dizeleri gösterebilir `byte[]`. Soneki eklemek `B` bir ASCII dizesi olduğunu belirtmek için bir dize için. Bayt dizileri ile kullanılan ASCII dize değişmez değerleri aynı kaçış sıraları Unicode kaçış sıraları dışında Unicode dizeleri olarak destekler.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a>Dize İşleçleri
Dizeyi birleştirmek için iki yolu vardır: kullanarak `+` işleci veya kullanarak `^` işleci. `+` İşleci .NET Framework dize özellikleri işleme ile uyumluluk korur.

Aşağıdaki örnek, dize birleştirme gösterilmektedir.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a>String sınıfı
F # dize türü gerçekte bir .NET Framework olduğundan `System.String` türü, tüm `System.String` üyeleri kullanılabilir. Bu içerir `+` dizeyi birleştirmek için kullanılan işleci `Length` özelliği ve `Chars` özelliği dize Unicode karakter dizisi döndürür. Dizeleri hakkında daha fazla bilgi için bkz: `System.String`.

Kullanarak `Chars` özelliği `System.String`, aşağıdaki kodda gösterildiği gibi bir dizin belirterek bir dizedeki karakterleri tek tek erişebilirsiniz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a>String modülü
Dize işleme için ek işlevler dahil `String` modülünde `FSharp.Core` ad alanı. Daha fazla bilgi için bkz: [Core.String modülü](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).

## <a name="see-also"></a>Ayrıca Bkz.
[F # dili başvurusu](index.md)
