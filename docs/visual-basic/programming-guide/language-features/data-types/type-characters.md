---
title: Tür Karakterleri
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
ms.openlocfilehash: a48260694c1dfcbbb8f804f220fe89b1663c7319
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393084"
---
# <a name="type-characters-visual-basic"></a>Tür karakterleri (Visual Basic)

Bir bildirim bildiriminde bir veri türü belirtmenin yanı sıra, bazı programlama öğelerinin veri türünü bir *tür karakteriyle*zorlayabilirsiniz. Tür karakteri, hiçbir türden hiçbir araya girmeden önce öğesini hemen izlemelidir.

Tür karakteri öğenin adının bir parçası değil. Tür karakteriyle tanımlanmış bir öğeye, tür karakteri olmadan başvurulabilir.

## <a name="identifier-type-characters"></a>Tanımlayıcı türü karakterleri

Visual Basic, bir değişkenin veya sabitin veri türünü belirtmek için bir bildirimde kullanabileceğiniz *tanımlayıcı türü karakterlerinin* bir kümesini sağlar. Aşağıdaki tabloda, kullanılabilir tanımlayıcı türü karakterleri kullanım örnekleri ile gösterilmektedir.
  
|Tanımlayıcı türü karakteri|Veri türü|Örnek|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 ,,,,,,,,, `Boolean` `Byte` `Char` `Date` `Object` `SByte` `Short` `UInteger` `ULong` Veya `UShort` veri türleri için ya da diziler ya da yapılar gibi herhangi bir bileşik veri türü için tanımlayıcı türü karakterler yok.

Bazı durumlarda, `$` `Left$` `Left` türü döndürülen bir değer elde etmek için, örneğin yerine bir Visual Basic işleve bir karakter ekleyebilirsiniz `String` .

Her durumda, tanımlayıcı türü karakteri tanımlayıcı adını hemen izlemelidir.

## <a name="literal-type-characters"></a>Değişmez değer türü karakterleri

*Değişmez* değer, bir veri türünün belirli bir değerinin metinsel gösterimidir.  

### <a name="default-literal-types"></a>Varsayılan değişmez değer türleri

Kodunuzda göründüğü gibi bir sabit değerin biçimi normalde veri türünü belirler. Aşağıdaki tabloda bu varsayılan türler gösterilmektedir.  
  
|Sabit değerin metin biçimi|Varsayılan veri türü|Örnek|  
|-----------------------------|-----------------------|-------------|  
|Sayısal, kesirli bölüm yok|`Integer`|`2147483647`|  
|Sayısal, kesirli bölüm yok, için çok büyük`Integer`|`Long`|`2147483648`|  
|Sayısal, kesirli bölüm|`Double`|`1.2`|  
|Çift tırnak işareti içine alınmış|`String`|`"A"`|  
|Sayı işaretleri içine alınmış|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Zorunlu değişmez değer türleri

Visual Basic değişmez değer *türü karakterleri*sağlar, bu, bir hazır değeri, kendi formu dışında bir veri türünü varsaymaya zorlamak için kullanabilirsiniz. Bu, karakteri sabit değerin sonuna ekleyerek yapabilirsiniz. Aşağıdaki tabloda, kullanılabilir değişmez değer türü karakterleri kullanım örnekleri ile gösterilmektedir.
  
|Değişmez değer türü karakteri|Veri türü|Örnek|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

,,,, `Boolean` `Byte` `Date` `Object` `SByte` Veya `String` veri türleri için ya da diziler ya da yapılar gibi herhangi bir bileşik veri türü için değişmez değer türü karakterleri yok.

Değişmez değerler, `%` `&` `@` `!` `#` `$` değişkenler, sabitler ve ifadeler gibi tanımlayıcı türü karakterlerini de (,,,,,) kullanabilir. Ancak, değişmez değer türü karakterleri ( `S` , `I` , `L` , `D` , `F` , `R` , `C` ) yalnızca sabit karakterlerle kullanılabilir.

Her durumda, değişmez değer türü karakteri hemen sabit değeri izlemelidir.

## <a name="hexadecimal-binary-and-octal-literals"></a>Onaltılık, ikili ve sekizlik sabit değerler

Derleyici normalde bir tamsayı değişmez değerini ondalık (10 tabanında) sayı sisteminde olacak şekilde yorumlar. Ön eke sahip bir tam sayı (taban 16) numarası, ön eke sahip bir `&H` ikili (taban 2) numarası olarak `&B` ve ön eki olan sekizli (taban 8) numarası olarak bir tamsayı sabit değeri de tanımlayabilirsiniz `&O` . Ön eki izleyen basamakların sayı sistemine uygun olması gerekir. Aşağıdaki tabloda bu gösterilmektedir.  
  
|Sayı tabanı|Ön ek|Geçerli basamak değerleri|Örnek|
|-----------------|------------|------------------------|-------------|
|Onaltılı (taban 16)|`&H`|0-9 ve A-F|`&HFFFF`|
|İkili (taban 2)|`&B`|0-1|`&B01111100`|
|Sekizlik (taban 8)|`&O`|0-7|`&O77`|

Visual Basic 2017 ' den başlayarak, bir `_` integral sabit değerinin okunabilirliğini geliştirmek için alt çizgi karakterini () Grup ayırıcısı olarak kullanabilirsiniz. Aşağıdaki örnek, `_` bir ikili sabit değeri 8 bitlik gruplar halinde gruplandırmak için karakterini kullanır:

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

Ön ek değişmez değerini, değişmez değer türü karakteriyle izleyebilirsiniz. Aşağıdaki örnek bunu gösterir.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

Önceki örnekte, `counter` -32768 ondalık değerine sahiptir ve `flags` + 32768 ondalık değerine sahiptir.

Visual Basic 15,5 ' den başlayarak, alt çizgi karakterini ( `_` ) ön ek ile onaltılı, ikili veya sekizlik basamaklar arasında önde gelen bir ayırıcı olarak da kullanabilirsiniz. Örnek:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](index.md)
- [Başlangıç Veri Türleri](elementary-data-types.md)
- [Değer Türleri ve Başvuru Türleri](value-types-and-reference-types.md)
- [Visual Basic'de Tür Dönüştürmeleri](type-conversions.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [Değişken Bildirimi](../variables/variable-declaration.md)
- [Veri türleri](../../../language-reference/data-types/index.md)
