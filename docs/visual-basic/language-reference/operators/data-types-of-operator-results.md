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
ms.openlocfilehash: c2e94a80e83becf25bf47ef7837362f0ebf441a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605439"
---
# <a name="data-types-of-operator-results-visual-basic"></a>İşleç Sonuçlarının Veri Türleri (Visual Basic)
Visual Basic işlenen veri türlerine bağlı bir işlem sonucu veri türünü belirler. Bazı durumlarda bu iki işlenen daha büyük bir aralık ile bir veri türü olabilir.  
  
## <a name="data-type-ranges"></a>Veri Türü Aralıkları  
 Sırada küçük değerden büyük, ilgili veri türleri aralıkları aşağıdaki gibidir:  
  
-   [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — iki olası değerler  
  
-   [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bayt](../../../visual-basic/language-reference/data-types/byte-data-type.md) — 256 olası tam sayı değerleri  
  
-   [Kısa](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65.536 (6.5... E + 4) olası tam sayı değerleri  
  
-   [Tamsayı](../../../visual-basic/language-reference/data-types/integer-data-type.md), [Uınteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4,294,967,296 (4.2... E + 9) olası tam sayı değerleri  
  
-   [Uzun](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18,446,744,073,709,551,615 (1.8... E + 19) olası tam sayı değerleri  
  
-   [Ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) —... 1.5 E + 29 olası tam sayı değerleri, en fazla aralık... 7,9 E + 28 (mutlak değer)  
  
-   [Tek](../../../visual-basic/language-reference/data-types/single-data-type.md) — üst aralık 3.4... E + 38 (mutlak değer)  
  
-   [Çift](../../../visual-basic/language-reference/data-types/double-data-type.md) — üst aralık 1.7... E + 308 (mutlak değer)  
  
 Visual Basic veri türleri hakkında daha fazla bilgi için bkz: [veri türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
 İşleneni değerlendirilirse [hiçbir şey](../../../visual-basic/language-reference/nothing.md), Visual Basic aritmetik işleçler, sıfır olarak ele alın.  
  
## <a name="decimal-arithmetic"></a>Ondalık aritmetik  
 Unutmayın [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) veri türü olan hiçbiri kayan veya tamsayı.  
  
 Varsa ya da işleneni bir `+`, `–`, `*`, `/`, veya `Mod` işlemi `Decimal` ve diğer değil `Single` veya `Double`, Visual Basic widens diğerişlenenin`Decimal`. İşlemi gerçekleştiren `Decimal`, ve sonuç veri türü `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Kayan nokta aritmetik  
 Visual Basic gerçekleştirir, çoğu kayan nokta aritmetik [çift](../../../visual-basic/language-reference/data-types/double-data-type.md), en verimli veri olduğu gibi işlemler için yazın. Ancak, bir işlenen ise [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) ve diğer değil `Double`, Visual Basic işlemi gerçekleştiren `Single`. Her işleneni işleminden önce uygun veri türü için gerekli olarak widens ve sonuç, veri türüne sahip.  
  
### <a name="-and--operators"></a>/ ve ^ işleçleri  
 `/` İşleci yalnızca için tanımlanmış [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [tek](../../../visual-basic/language-reference/data-types/single-data-type.md), ve [çift](../../../visual-basic/language-reference/data-types/double-data-type.md) veri türleri. Visual Basic işleminden önce uygun veri türü için gereken her işlenen widens ve sonuç, veri türüne sahip.  
  
 Sonuç veri türleri için aşağıdaki tabloda gösterilmektedir `/` işleci. Bu tablo simetrik olduğunu unutmayın; işlenen veri türlerinin belirli bir birleşimini sonuç veri türü işlenenler sırasını bakılmaksızın aynı değil.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Herhangi bir tamsayı türü|  
|`Decimal`|Ondalık|Tek|Çift|Ondalık|  
|`Single`|Tek|Tek|Çift|Tek|  
|`Double`|Çift|Çift|Çift|Çift|  
|Herhangi bir tamsayı türü|Ondalık|Tek|Çift|Çift|  
  
 `^` İşleci yalnızca için tanımlanmış `Double` veri türü. Visual Basic widens için gereken her işlenen `Double` işlemi ve veri türü olan her zaman sonuç önce `Double`.  
  
## <a name="integer-arithmetic"></a>Tamsayı aritmetiğini  
 Sonuç veri türü tamsayı işlemi işlenen veri türlerine bağlıdır. Genel olarak, Visual Basic, sonuç veri türü belirlemek için aşağıdaki kuralları kullanır:  
  
-   İkili işleç hem işlenenleri aynı olup olmadığını veri türü, sonuç, veri türüne sahip. Bir özel durum `Boolean`, için zorunlu `Short`.  
  
-   İmzasız işleneni imzalı terimiyle katılıyorsa, sonuç ile işaretli bir türe büyük olarak en az bir ya da işleneni olarak aralığındadır.  
  
-   Aksi takdirde, sonuç genellikle büyük iki işlenen veri türlerinin sahiptir.  
  
 Sonuç veri türü ya da işlenen veri türü ile aynı olmayabileceğini unutmayın.  
  
> [!NOTE]
>  Sonuç veri türü her zaman işlemin sonucu tüm olası değerlerini tutabilecek kadar büyük değil. Bir <xref:System.OverflowException> değeri sonuç veri türü için çok büyük ise özel durum meydana gelebilir.  
  
### <a name="unary--and--operators"></a>Birli + ve – işleçleri  
 Aşağıdaki tabloda sonuç veri türleri için iki birli işleç, gösterilmektedir `+` ve `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Birli `+`|kısa|SByte|Bayt|kısa|UShort|Tamsayı|Uınteger|uzun|ULong|  
|Birli `–`|kısa|SByte|kısa|kısa|Tamsayı|Tamsayı|uzun|uzun|Ondalık|  
  
### <a name="-and--operators"></a><\< ve >> işleçleri  
 Aşağıdaki tabloda sonuç veri türleri iki bit kaydırma işleçleri gösterilmektedir `<<` ve `>>`. Visual Basic her bit kaydırma işleci birli işleç (gölgeye için bit desen), sol işleneni üzerinde olarak değerlendirir.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|kısa|SByte|Bayt|kısa|UShort|Tamsayı|Uınteger|uzun|ULong|  
  
 Sol işleneni ise `Decimal`, `Single`, `Double`, veya `String`, Visual Basic dönüştürebilir girişimlerini `Long` işlemi ve veri türü sonucu önce `Long`. Sağ işleneni (kaydırılacak bit konumları sayısı) olmalıdır `Integer` veya için widens bir türü `Integer`.  
  
### <a name="binary----and-mod-operators"></a>İkili +, -, * ve Mod işleçleri  
 Aşağıdaki tabloda, ikili veri türlerinde sonucu gösterilmektedir `+` ve `–` işleçler ve `*` ve `Mod` işleçler. Bu tablo simetrik olduğunu unutmayın; işlenen veri türlerinin belirli bir birleşimini sonuç veri türü işlenenler sırasını bakılmaksızın aynı değil.  
  
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
 Sonuç veri türleri için aşağıdaki tabloda gösterilmektedir `\` işleci. Bu tablo simetrik olduğunu unutmayın; işlenen veri türlerinin belirli bir birleşimini sonuç veri türü işlenenler sırasını bakılmaksızın aynı değil.  
  
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
  
 Varsa ya da işleneni `\` işlecidir [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [tek](../../../visual-basic/language-reference/data-types/single-data-type.md), veya [çift](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic dönüştürebilir girişimlerini [uzun](../../../visual-basic/language-reference/data-types/long-data-type.md)işlemi ve veri türü sonucu önce `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>İlişkisel ve bit tabanlı karşılaştırma  
 İlişkisel bir işlemin sonucu veri türü (`=`, `<>`, `<`, `>`, `<=`, `>=`) her zaman `Boolean` [Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Aynı mantıksal işlemleri için geçerlidir (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) üzerinde `Boolean` işlenen.  
  
 Bit tabanlı mantıksal işlemi sonuç veri türü işlenen veri türlerine bağlıdır. Unutmayın `AndAlso` ve `OrElse` yalnızca için tanımlanan `Boolean`, ve Visual Basic dönüştürür için gereken her işlenen `Boolean` işlemi gerçekleştirmeden önce.  
  
### <a name="-----and--operators"></a>=, <>, \<, >, \<= ve > = işleç  
 Her iki işlenen olursa `Boolean`, Visual Basic göz önünde bulundurur `True` olmasını değerinden `False`. Sayısal bir tür ile karşılaştırıldığında, bir `String`, Visual Basic çalışır dönüştürmek `String` için `Double` işleminden önce. A `Char` veya `Date` işleneni yalnızca aynı veri türünde başka bir işlenen ile karşılaştırılabilir. Sonuç veri türü her zaman olan `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Bitwise Not işleci  
 Aşağıdaki tabloda sonuç veri türleri için bitwise gösterilmektedir `Not` işleci.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boole değeri|SByte|Bayt|kısa|UShort|Tamsayı|Uınteger|uzun|ULong|  
  
 İşlenen ise `Decimal`, `Single`, `Double`, veya `String`, Visual Basic dönüştürebilir girişimlerini `Long` işlemi ve veri türü sonucu önce `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bit düzeyinde ve veya ve Xor işleçleri  
 Aşağıdaki tabloda sonuç veri türleri için bitwise gösterilmektedir `And`, `Or`, ve `Xor` işleçler. Bu tablo simetrik olduğunu unutmayın; işlenen veri türlerinin belirli bir birleşimini sonuç veri türü işlenenler sırasını bakılmaksızın aynı değil.  
  
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
  
 İşleneni ise `Decimal`, `Single`, `Double`, veya `String`, Visual Basic dönüştürebilir girişimlerini `Long` işlenen zaten yüklenmiş gibi işlemi ve sonuçta elde edilen veri önce türü aynı ise `Long`.  
  
## <a name="miscellaneous-operators"></a>Çeşitli İşleçler  
 `&` İşleci yalnızca birleşimi için tanımlanan `String` işlenen. Visual Basic dönüştürür için gereken her işlenen `String` işlemi ve veri türü olan her zaman sonuç önce `String`. Amacı `&` işleç, tüm dönüştürme `String` genişletme olması için kabul olsa bile `Option Strict` olan `On`.  
  
 `Is` Ve `IsNot` işleçleri her iki işlenen başvuru türünde olması gerekir. `TypeOf`... `Is` ifadesi başvuru türünde olması için ilk işlenen ve bir veri türü adı olacak biçimde ikinci işlenen gerektirir. Tüm bu durumlarda sonuç veri türüdür `Boolean`.  
  
 `Like` İşleci yalnızca desen, eşleştirme için tanımlanmış `String` işlenen. Visual Basic girişimleri için gereken her işlenen dönüştürmek `String` işleminden önce. Sonuç veri türü her zaman olan `Boolean`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Veri Türleri](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Visual Basic'de Karşılaştırma işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [İşleçler](../../../visual-basic/language-reference/operators/index.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Karşılaştırma İşleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
