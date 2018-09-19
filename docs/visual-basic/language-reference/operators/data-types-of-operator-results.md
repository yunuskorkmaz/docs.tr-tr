---
title: İşleç Sonuçlarının Veri Türleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: 135c44217debcddb15fd4cef7e73ca2f98903c43
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003704"
---
# <a name="data-types-of-operator-results-visual-basic"></a>İşleç Sonuçlarının Veri Türleri (Visual Basic)
Visual Basic işlenen veri türlerine göre bir işlem sonucu veri türünü belirler. Bazı durumlarda bu iki işlenenden ait olandan daha kapsamlı bir veri türü olabilir.  
  
## <a name="data-type-ranges"></a>Veri Türü Aralıkları  
 Sırada küçük değerden büyük, ilgili veri türü aralıkları şu şekildedir:  
  
-   [Boole](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — iki olası değerler  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bayt](../../../visual-basic/language-reference/data-types/byte-data-type.md) — 256 olası tamsayı değerler  
  
-   [Kısa](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65.536 (6.5... E + 4) olası tamsayı değerler  
  
-   [Tamsayı](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uınteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4,294,967,296 (4.2... E + 9) olası tamsayı değerler  
  
-   [Uzun](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18,446,744,073,709,551,615 (1.8... E + 19) olası tamsayı değerler  
  
-   [Ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) —... 1.5 E + 29 olası tamsayı değerlerini en büyük aralık... 7,9 E + 28 (mutlak değer)  
  
-   [Tek](../../../visual-basic/language-reference/data-types/single-data-type.md) — en büyük aralık 3.4... E + 38 (mutlak değer)  
  
-   [Çift](../../../visual-basic/language-reference/data-types/double-data-type.md) — en büyük aralık 1.7... E + 308 (mutlak değer)  
  
 Visual Basic veri türleri hakkında daha fazla bilgi için bkz. [veri türleri](../../../visual-basic/language-reference/data-types/index.md).  
  
 Bir işlenen değerlendirilirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md), isteğe bağlı olarak Visual Basic aritmetik işleçler sıfır olarak değerlendir.  
  
## <a name="decimal-arithmetic"></a>Ondalık aritmetik  
 Unutmayın [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) veri türü olan hiçbiri kayan nokta ya da tamsayı.  
  
 Her iki işleneni bir `+`, `–`, `*`, `/`, veya `Mod` işlem `Decimal` ve diğer değil `Single` veya `Double`, Visual Basic diğer işlenen içinwidens`Decimal`. İşlemi gerçekleştiren `Decimal`, ve sonuç veri türü `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Kayan nokta aritmetiği  
 Visual Basic içinde çoğu kayan nokta aritmetiği gerçekleştirir [çift](../../../visual-basic/language-reference/data-types/double-data-type.md), en etkili verileri olduğu gibi işlemler için yazın. Ancak, bir işlenen ise [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) ve diğer değil `Double`, Visual Basic işlemi gerçekleştiren `Single`. Her işlenen işleminden önce uygun veri türü için gerekli olarak widens ve sonuç, veri türüne sahip.  
  
### <a name="-and--operators"></a>/ ve ^ işleçleri  
 `/` İşleci yalnızca tanımlanmış [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [tek](../../../visual-basic/language-reference/data-types/single-data-type.md), ve [çift](../../../visual-basic/language-reference/data-types/double-data-type.md) veri türleri. Visual Basic işleminden önce uygun veri türünün gerekli olduğu her işlenen widens ve sonuç, veri türüne sahip.  
  
 Aşağıdaki tablo sonuç veri türleri için gösterir `/` işleci. Bu tabloda simetrik olduğunu unutmayın; işlenen veri türleri belirli bir birleşimi için sonuç veri türü işlenen sırasını bağımsız olarak aynıdır.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Herhangi bir tamsayı türü|  
|`Decimal`|Ondalık|Tek|Çift|Ondalık|  
|`Single`|Tek|Tek|Çift|Tek|  
|`Double`|Çift|Çift|Çift|Çift|  
|Herhangi bir tamsayı türü|Ondalık|Tek|Çift|Çift|  
  
 `^` İşleci yalnızca tanımlanmış `Double` veri türü. Visual Basic widens gerekli olduğu her işlenen `Double` önce işlem ve veri türü, her zaman sonucu `Double`.  
  
## <a name="integer-arithmetic"></a>Tamsayı aritmetik  
 Bir tamsayı işleminin sonucu veri türü işlenen veri türlerine bağlıdır. Genel olarak, Visual Basic, sonuç veri türünü belirlemek için aşağıdaki kuralları kullanır:  
  
-   İkili işleç her iki işleneni de aynı olup olmadığını veri türü, bu veri türü sonucu vardır. Bir özel durum `Boolean`, için zorlanan `Short`.  
  
-   İmzalı bir işlenen işaretsiz bir işlenen yer alıyorsa, sonucu ile işaretli bir türe büyük olarak en az bir aralık iki işlenenden var.  
  
-   Aksi halde, sonuç genellikle büyük iki işlenen veri türleri vardır.  
  
 Sonuç veri türü ya da işlenen veri türü ile aynı olmayabileceğini unutmayın.  
  
> [!NOTE]
>  Sonuç veri türü her zaman işlemin sonucu tüm olası değerlerini tutabilecek kadar büyük değil. Bir <xref:System.OverflowException> değeri sonuç veri türü için çok büyük ise özel durum meydana gelebilir.  
  
### <a name="unary--and--operators"></a>Birli + ve -işleçleri  
 Aşağıdaki tablo sonuç veri türleri iki birli işleçler için gösterir `+` ve `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Birli `+`|kısa|SByte|Bayt|kısa|UShort|Tamsayı|Uınteger|uzun|ULong|  
|Birli `–`|kısa|SByte|kısa|kısa|Tamsayı|Tamsayı|uzun|uzun|Ondalık|  
  
### <a name="-and--operators"></a><\< ve >> işleçleri  
 Aşağıdaki tablo sonuç veri türleri iki bit kaydırma işleçleri için gösterir `<<` ve `>>`. Visual Basic her bit kaydırma işleci (kaydırılmasına bit deseni) sol işlenen üzerinde birli işleç olarak değerlendirir.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|kısa|SByte|Bayt|kısa|UShort|Tamsayı|Uınteger|uzun|ULong|  
  
 Sol işlenen ise `Decimal`, `Single`, `Double`, veya `String`, Visual Basic çalışır öğesine dönüştürmek `Long` önce işlem ve veri türü sonucu `Long`. Sağ işlenen (kaydırılacak bit konumları sayısı) olmalıdır `Integer` ya da bir tür için widens `Integer`.  
  
### <a name="binary----and-mod-operators"></a>İkili +, -, * ve Mod işleçleri  
 Aşağıdaki tablo sonuç veri türleri için ikili gösterir `+` ve `–` işleçler ve `*` ve `Mod` işleçleri. Bu tabloda simetrik olduğunu unutmayın; işlenen veri türleri belirli bir birleşimi için sonuç veri türü işlenen sırasını bağımsız olarak aynıdır.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|kısa|SByte|kısa|kısa|Tamsayı|Tamsayı|uzun|uzun|Ondalık|  
|`SByte`|SByte|SByte|kısa|kısa|Tamsayı|Tamsayı|uzun|uzun|Ondalık|  
|`Byte`|kısa|kısa|Bayt|kısa|UShort|Tamsayı|Uınteger|uzun|ULong|  
|`Short`|kısa|kısa|kısa|kısa|Tamsayı|Tamsayı|uzun|uzun|Ondalık|  
|`UShort`|Tamsayı|Tamsayı|UShort|Tamsayı|UShort|Tamsayı|Uınteger|uzun|ULong|  
|`Integer`|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|uzun|uzun|Ondalık|  
|`UInteger`|uzun|uzun|Uınteger|uzun|Uınteger|uzun|Uınteger|uzun|ULong|  
|`Long`|uzun|uzun|uzun|uzun|uzun|uzun|uzun|uzun|Ondalık|  
|`ULong`|Ondalık|Ondalık|ULong|Ondalık|ULong|Ondalık|ULong|Ondalık|ULong|  
  
### <a name="-operator"></a>\ İşleci  
 Aşağıdaki tablo sonuç veri türleri için gösterir `\` işleci. Bu tabloda simetrik olduğunu unutmayın; işlenen veri türleri belirli bir birleşimi için sonuç veri türü işlenen sırasını bağımsız olarak aynıdır.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|kısa|SByte|kısa|kısa|Tamsayı|Tamsayı|uzun|uzun|uzun|  
|`SByte`|SByte|SByte|kısa|kısa|Tamsayı|Tamsayı|uzun|uzun|uzun|  
|`Byte`|kısa|kısa|Bayt|kısa|UShort|Tamsayı|Uınteger|uzun|ULong|  
|`Short`|kısa|kısa|kısa|kısa|Tamsayı|Tamsayı|uzun|uzun|uzun|  
|`UShort`|Tamsayı|Tamsayı|UShort|Tamsayı|UShort|Tamsayı|Uınteger|uzun|ULong|  
|`Integer`|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|uzun|uzun|uzun|  
|`UInteger`|uzun|uzun|Uınteger|uzun|Uınteger|uzun|Uınteger|uzun|ULong|  
|`Long`|uzun|uzun|uzun|uzun|uzun|uzun|uzun|uzun|uzun|  
|`ULong`|uzun|uzun|ULong|uzun|ULong|uzun|ULong|uzun|ULong|  
  
 Her iki işleneninin `\` işleci [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [tek](../../../visual-basic/language-reference/data-types/single-data-type.md), veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic çalışır öğesine dönüştürmek [uzun](../../../visual-basic/language-reference/data-types/long-data-type.md)önce işlem ve veri türü sonucu `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>İlişkisel ve bit düzeyinde karşılaştırmaları  
 İlişkisel bir veri işleminin sonucu veri türü (`=`, `<>`, `<`, `>`, `<=`, `>=`) her zaman `Boolean` [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Aynı mantıksal işlemleri için geçerlidir (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) üzerinde `Boolean` işlenen.  
  
 Bit düzeyinde bir mantıksal işlem sonucu veri türünü işlenenden veri türlerine bağlıdır. Unutmayın `AndAlso` ve `OrElse` yalnızca tanımlanan `Boolean`, ve Visual Basic, her işlenen gerektiği şekilde dönüştürür `Boolean` işlemi gerçekleştirmeden önce.  
  
### <a name="-----and--operators"></a>= <>, \<, >, \<= ve > işleçler =  
 Her iki işlenen de olursa `Boolean`, Visual Basic göz önünde bulundurur `True` olacak şekilde küçüktür `False`. Bir sayısal tür ile karşılaştırılır, bir `String`, Visual Basic dönüştürme girişimlerini `String` için `Double` işleminden önce. A `Char` veya `Date` işlenen, yalnızca aynı veri türünde başka bir işleneni ile karşılaştırılabilir. Sonuç veri türünün her zaman olduğu `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Bit düzeyinde Not işleci  
 Aşağıdaki tablo sonuç veri türleri için bit düzeyinde gösterir `Not` işleci.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boole değeri|SByte|Bayt|kısa|UShort|Tamsayı|Uınteger|uzun|ULong|  
  
 İşlenen `Decimal`, `Single`, `Double`, veya `String`, Visual Basic çalışır öğesine dönüştürmek `Long` önce işlem ve veri türü sonucu `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bitwise ve, veya ve Xor işleçleri  
 Aşağıdaki tablo sonuç veri türleri için bit düzeyinde gösterir `And`, `Or`, ve `Xor` işleçleri. Bu tabloda simetrik olduğunu unutmayın; işlenen veri türleri belirli bir birleşimi için sonuç veri türü işlenen sırasını bağımsız olarak aynıdır.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boole değeri|SByte|kısa|kısa|Tamsayı|Tamsayı|uzun|uzun|uzun|  
|`SByte`|SByte|SByte|kısa|kısa|Tamsayı|Tamsayı|uzun|uzun|uzun|  
|`Byte`|kısa|kısa|Bayt|kısa|UShort|Tamsayı|Uınteger|uzun|ULong|  
|`Short`|kısa|kısa|kısa|kısa|Tamsayı|Tamsayı|uzun|uzun|uzun|  
|`UShort`|Tamsayı|Tamsayı|UShort|Tamsayı|UShort|Tamsayı|Uınteger|uzun|ULong|  
|`Integer`|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|uzun|uzun|uzun|  
|`UInteger`|uzun|uzun|Uınteger|uzun|Uınteger|uzun|Uınteger|uzun|ULong|  
|`Long`|uzun|uzun|uzun|uzun|uzun|uzun|uzun|uzun|uzun|  
|`ULong`|uzun|uzun|ULong|uzun|ULong|uzun|ULong|uzun|ULong|  
  
 Bir işlenen `Decimal`, `Single`, `Double`, veya `String`, Visual Basic çalışır öğesine dönüştürmek `Long` işlenen zaten olsaydı olarak önce işlemi ve sonuçta elde edilen veri türü aynıdır `Long`.  
  
## <a name="miscellaneous-operators"></a>Çeşitli İşleçler  
 `&` İşleci yalnızca birleşimi için tanımlanan `String` işlenen. Visual Basic, her işlenen gerektiği şekilde dönüştürür `String` önce işlem ve veri türü, her zaman sonucu `String`. Amacıyla `&` işleç, tüm dönüştürmeler `String` genişletme olması için değerlendirilir olsa bile `Option Strict` olduğu `On`.  
  
 `Is` Ve `IsNot` işleçler iki işlenen de bir başvuru türü olmasını gerektirir. `TypeOf`... `Is` ilk işleneni başvuru türünde olması ve bir veri türünün adı olacak şekilde ikinci işlenen ifadesi gerektirir. Tüm durumlarda sonuç verilerini türüdür `Boolean`.  
  
 `Like` İşleci yalnızca deseni, eşleşen için tanımlanan `String` işlenen. Visual Basic dönüştürmek için gerektiği gibi her işlenen girişimlerini `String` işleminden önce. Sonuç veri türünün her zaman olduğu `Boolean`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)  
 [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [İşleçler](../../../visual-basic/language-reference/operators/index.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Karşılaştırma İşleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
