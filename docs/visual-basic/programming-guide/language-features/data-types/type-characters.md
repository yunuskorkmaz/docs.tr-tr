---
title: Tür Karakterleri (Visual Basic)
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
ms.openlocfilehash: a469a08ebadd77d5abbfa95b270784c9ef534691
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906756"
---
# <a name="type-characters-visual-basic"></a>Tür karakterleri (Visual Basic)

Bir bildirim deyiminde veri türü belirtmeye ek olarak, bazı programlama öğeleri ile veri türünü zorlayabilirsiniz bir *türü karakteri*. Tür karakteri hemen öğe, müdahalede bulunan karakter herhangi bir türde izlemeniz gerekir.

Tür karakteri öğe adı bir parçası değil. Tür karakteri bir tür karakteri ile tanımlanan bir öğe başvurulabilir.

## <a name="identifier-type-characters"></a>Tanımlayıcı türü karakterleri

Visual Basic sağlayan bir dizi *tanımlayıcı türü karakterleri* bir bildiriminde bir değişken veya sabit veri türünü belirtmek için kullanabilirsiniz. Aşağıdaki tabloda kullanılabilir tanımlayıcı türü karakterleri kullanım örnekleri ile gösterilmektedir.
  
|Tanımlayıcı türü karakteri|Veri türü|Örnek|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Hiçbir tanımlayıcı türü karakterleri mevcut `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, veya `UShort` veri türleri veya herhangi bir için diziler veya yapılar gibi bileşik veri türleri.

Bazı durumlarda, eklediğiniz `$` Visual Basic işlevi için örneğin karakter `Left$` yerine `Left`türünde döndürülen bir değer elde etmek için `String`.

Her durumda, tanımlayıcı türü karakteri hemen tanımlayıcı adı izlemelidir.

## <a name="literal-type-characters"></a>Değişmez değer türü karakterleri

A *değişmez değer* veri türünün belirli bir değeri değerinin metinsel bir gösterimini olduğu.  

### <a name="default-literal-types"></a>Varsayılan değişmez değer türleri

Kodunuzda normalde göründüğü gibi bir sabit değer biçiminde veri türünü belirler. Aşağıdaki tabloda, bu varsayılan türleri gösterilmektedir.  
  
|Sabit değerinin metinsel formu|Varsayılan veri türü|Örnek|  
|-----------------------------|-----------------------|-------------|  
|Sayısal, Hayır kesirli bölümü|`Integer`|`2147483647`|  
|Sayısal, Hayır kesirli bölümü, çok büyük `Integer`|`Long`|`2147483648`|  
|Sayısal, kesirli bölümü|`Double`|`1.2`|  
|Çift tırnak işareti içine alınmış|`String`|`"A"`|  
|Sayı işaretleri alınmış|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Zorlanmış değişmez değer türleri

Visual Basic sağlayan bir dizi *değişmez değer türü karakterleri*, farklı bir veri türü, form varsaymak bir sabit değer zorlamak için kullanabileceğiniz gösterir. Karakter sabit değerinin sonuna ekleyerek bunu yapabilirsiniz. Aşağıdaki tabloda kullanılabilir değişmez değer türü karakterleri kullanım örnekleri ile gösterilmektedir.
  
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

Hiçbir değişmez değer türü karakterleri mevcut `Boolean`, `Byte`, `Date`, `Object`, `SByte`, veya `String` veri türleri veya dizi veya yapılar gibi tüm bileşik veri türleri için.

Değişmez değerler tanımlayıcı türü karakterleri de kullanabilir (`%`, `&`, `@`, `!`, `#`, `$`), değişkenleri, sabitleri ve ifadeler gibi. Ancak, değişmez değer türü karakterleri (`S`, `I`, `L`, `D`, `F`, `R`, `C`) yalnızca değişmez değerleri ile kullanılabilir.

Her durumda, değişmez değer türü karakteri hemen değişmez değer izlemeniz gerekir.

## <a name="hexadecimal-binary-and-octal-literals"></a>Onaltılık, ikili ve sekizlik değişmez değerler

Derleyici, ondalık (10 tabanında) sayı sisteminde olacak tamsayı değişmez değer normal olarak yorumlar. Tamsayı sabit değeri bir onaltılık (16 tabanında) sayı olarak tanımlayabilirsiniz `&H` ikili (taban 2) bir sayı olarak ön eki `&B` öneki ve bir sekizlik (Temel 8) olarak numaranızı `&O` önek. Önek izleyen basamaklı sayı sistemi için uygun olmalıdır. Aşağıdaki tablo bunu göstermektedir.  
  
|Sayı tabanı|Ön eki|Geçerli basamaklı değerler|Örnek|
|-----------------|------------|------------------------|-------------|
|Onaltılık (16 tabanında)|`&H`|0-9 ve A-F|`&HFFFF`|
|İkili (2 tabanı)|`&B`|0-1|`&B01111100`|
|Octal (8 tabanı)|`&O`|0-7|`&O77`|

Visual Basic 2017'den itibaren alt çizgi karakterini kullanabilirsiniz (`_`) bir integral sabit değerinin okunabilirliği artırmak için bir grup ayracı olarak. Aşağıdaki örnekte `_` karakter sabit değeri bir ikili 8-bit gruplar halinde gruplandırmak için:

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

Değişmez değer türü karakteri ile ön ekli bir sabit değer takip edebilirsiniz. Aşağıdaki örnekte bu gösterir.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

Önceki örnekte, `counter` -32768, ondalık değeri vardır ve `flags` +32768 ondalık değerine sahiptir.

Visual Basic 15.5 ile başlayarak, alt çizgi karakteri de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizlik basamak arasında önde gelen bir ayırıcı olarak. Örneğin:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)
