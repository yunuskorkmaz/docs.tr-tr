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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9262c57c5773b947f18fd9e8cf9087bb8e02de7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653513"
---
# <a name="type-characters-visual-basic"></a>Karakterlerini (Visual Basic)

Bir veri türü bildirimi deyiminde belirtmeye ek olarak, bazı programlama öğeleri ile veri türünü zorlayabilirsiniz bir *türü karakteri*. Tür karakteri hemen öğe, herhangi bir türde müdahalede bulunan hiçbir karakter izlemeniz gerekir.

Tür karakteri öğesinin adı bir parçası değil. Tür karakteri ile tanımlanmış bir öğe türü karakteri başvurulabilir.

## <a name="identifier-type-characters"></a>Tanımlayıcı türü karakterleri

Visual Basic sağlayan bir dizi *tanımlayıcı türü karakterleri* değişkeni ya da sabit veri türünü belirtmek için bir bildiriminde kullanabilirsiniz. Aşağıdaki tabloda kullanılabilir tanımlayıcı türü karakterleri kullanım örnekleri ile gösterilir.
  
|Tanımlayıcı türü karakteri|Veri türü|Örnek|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 Hiçbir tanımlayıcı türü karakterleri mevcut `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, veya `UShort` veri türleri veya herhangi bileşik veri türleri dizileri veya yapıları gibi.

Bazı durumlarda, ekleyebilirsiniz `$` için Visual Basic işlevi, örneğin karakter `Left$` yerine `Left`, döndürülen değer türü elde etmek için `String`.

Tüm durumlarda tanımlayıcı türü karakteri hemen tanımlayıcı adı izlemeniz gerekir.

## <a name="literal-type-characters"></a>Değişmez değer türü karakterleri

A *değişmez değer* bir veri türünün belirli bir değerinin metinsel gösterimini değil.  

### <a name="default-literal-types"></a>Varsayılan değişmez değer türleri

Kodunuzda normalde göründüğü gibi bir hazır değer form veri türünü belirler. Aşağıdaki tabloda, bu varsayılan türleri gösterilmektedir.  
  
|Metin biçiminde değişmez değeri|Varsayılan veri türü|Örnek|  
|-----------------------------|-----------------------|-------------|  
|Sayısal, Hayır kesirli bölümü|`Integer`|`2147483647`|  
|Sayısal, Hayır kesirli bölümü, için çok büyük `Integer`|`Long`|`2147483648`|  
|Sayısal, kesirli bölümü|`Double`|`1.2`|  
|Çift tırnak işaretleri içine|`String`|`"A"`|  
|İçinde sayı işaretleri arasına|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Zorlanmış değişmez değer türleri

Visual Basic sağlayan bir dizi *değişmez değer türü karakterleri*, farklı bir veri türü, form varsaymak bir hazır değer zorlamak için kullanabileceğiniz gösterir. Karakter sabit değeri sonuna ekleyerek bunu yapabilirsiniz. Aşağıdaki tabloda kullanılabilir değişmez değer türü karakterleri kullanım örnekleri ile gösterilir.
  
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

Değişmez değer türü karakterleri mevcut `Boolean`, `Byte`, `Date`, `Object`, `SByte`, veya `String` veri türleri veya dizileri veya yapıları gibi tüm bileşik veri türleri için.

Değişmez değerler tanımlayıcı türü karakterleri da kullanabilirsiniz (`%`, `&`, `@`, `!`, `#`, `$`) değişkenlerinin, sabitleri ve ifadeler gibi. Ancak, sabit karakterleri yazın (`S`, `I`, `L`, `D`, `F`, `R`, `C`) yalnızca değişmez değerler ile kullanılabilir.

Tüm durumlarda değişmez değer türü karakteri hemen hazır değeri izlemeniz gerekir.

## <a name="hexadecimal-binary-and-octal-literals"></a>Onaltılık, ikili ve sekizlik değişmez değerler

Derleyici ondalık (10 tabanı) sayı sisteminde olacak şekilde bir tamsayı değişmez değer normal olarak yorumlar. Değişmez değer bir tamsayı olan bir onaltılı (16 tabanı) sayı olarak tanımlayabilirsiniz `&H` öneki ile ikili (2 tabanı) sayı olarak `&B` öneki ve bir sekizli (8 tabanı) olarak numara ile `&O` öneki. Önek izleyin basamaklı sayı sistemi için uygun olmalıdır. Aşağıdaki tabloda bu gösterilmektedir.  
  
|Temel numarası|önek|Geçerli basamaklı değerler|Örnek|
|-----------------|------------|------------------------|-------------|
|Onaltılı (16 tabanı)|`&H`|0-9 ve A-F|`&HFFFF`|
|İkili (2 tabanı)|`&B`|0-1|`&B01111100`|
|Octal (8 tabanı)|`&O`|0-7|`&O77`|

Visual Basic 2017'dan başlayarak, alt çizgi karakterini kullanabilirsiniz (`_`) bir tam sayı sabit değeri okunabilirliğini artırmak için Grup ayırıcı olarak. Aşağıdaki örnek kullanır `_` karakter sabit değeri bir ikili 8 bit gruplar halinde gruplandırmak için:

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

Değişmez değer türü karakteri ile önekli bir hazır değer izleyebilirsiniz. Aşağıdaki örnekte bu gösterir.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

Önceki örnekte, `counter` -32768, ondalık değeri vardır ve `flags` +32768 ondalık değerine sahip.

Visual Basic 15,5 ile başlayarak, alt çizgi karakterini de kullanabilirsiniz (`_`) öneki ve onaltılık, ikili veya sekizli basamak arasında başında ayırıcı olarak. Örneğin:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>Ayrıca Bkz.

 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Değişken Bildirimi](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Veri Türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
