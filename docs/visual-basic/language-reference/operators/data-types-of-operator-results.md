---
title: İşleç Sonuçlarının Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: 3867d433ea5f9a6effe70db0ff4162390fb50b5c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331464"
---
# <a name="data-types-of-operator-results-visual-basic"></a>İşleç Sonuçlarının Veri Türleri (Visual Basic)
Visual Basic, işlenen veri türlerine göre bir işlemin sonuç veri türünü belirler. Bazı durumlarda bu, iki işlenenden daha büyük bir aralığa sahip bir veri türü olabilir.  
  
## <a name="data-type-ranges"></a>Veri Türü Aralıkları  
 En küçükten en büyüğe doğru sırada ilgili veri türlerinin aralıkları şunlardır:  
  
- [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) — iki olası değer  
  
- [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [byte](../../../visual-basic/language-reference/data-types/byte-data-type.md) — 256 olası integral değeri  
  
- [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [ushort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) — 65.536 (6.5... E + 4) olası integral değerleri  
  
- [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [uinteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) — 4.294.967.296 (4.2... E + 9) olası integral değerleri  
  
- [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) — 18446744073709551615 (1.8... E + 19) olası integral değerleri  
  
- [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) — 1,5... E + 29 olası integral değerleri, maksimum Aralık 7.9... E + 28 (mutlak değer)  
  
- [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) — maksimum Aralık 3.4... E + 38 (mutlak değer)  
  
- [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) — maksimum Aralık 1.7... E + 308 (mutlak değer)  
  
 Visual Basic veri türleri hakkında daha fazla bilgi için bkz. [veri türleri](../../../visual-basic/language-reference/data-types/index.md).  
  
 Bir işlenen [hiçbir şey](../../../visual-basic/language-reference/nothing.md)kabul verirse, Visual Basic aritmetik işleçleri onu sıfır olarak değerlendirir.  
  
## <a name="decimal-arithmetic"></a>Ondalık aritmetik  
 [Ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md) veri türünün ne kayan nokta ne de tamsayı olduğunu unutmayın.  
  
 `+`, `–`, `*`, `/`veya `Mod` işleminin herhangi bir işleneni `Decimal` ve diğeri `Single` veya `Double`değilse, Visual Basic diğer işleneni `Decimal`. `Decimal`işlemi gerçekleştirir ve sonuç veri türü `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Kayan nokta aritmetiği  
 Visual Basic, bu tür işlemler için en verimli veri türü olan [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)'ta çoğu kayan nokta aritmetiği gerçekleştirir. Ancak, bir işlenen [tek](../../../visual-basic/language-reference/data-types/single-data-type.md) ve diğeri `Double`değilse, Visual Basic `Single`işlemini gerçekleştirir. Her işleneni, işlem öncesinde uygun veri türü için gereken şekilde widens ve sonuç bu veri türüne sahip olur.  
  
### <a name="-and--operators"></a>/ve ^ Işleçleri  
 `/` işleci yalnızca [ondalık](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [tek](../../../visual-basic/language-reference/data-types/single-data-type.md)ve [çift](../../../visual-basic/language-reference/data-types/double-data-type.md) veri türleri için tanımlanır. Her işleneni, işlem öncesinde uygun veri türü için gereken şekilde widens Visual Basic ve sonuç bu veri türüne sahip.  
  
 Aşağıdaki tabloda `/` işlecinin sonuç veri türleri gösterilmektedir. Bu tablonun simetrik olduğunu unutmayın; belirli bir işlenen veri türleri birleşimi için, sonuç veri türü işlenen sıralarından bağımsız olarak aynıdır.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Herhangi bir tamsayı türü|  
|`Decimal`|Ondalık|Tek|Çift|Ondalık|  
|`Single`|Tek|Tek|Çift|Tek|  
|`Double`|Çift|Çift|Çift|Çift|  
|Herhangi bir tamsayı türü|Ondalık|Tek|Çift|Çift|  
  
 `^` işleci yalnızca `Double` veri türü için tanımlanır. Visual Basic her işleneni, işlem öncesinde `Double` için gereken şekilde `Double`ve sonuç veri türü her zaman.  
  
## <a name="integer-arithmetic"></a>Tamsayı aritmetik  
 Bir tamsayı işleminin sonuç veri türü, işlenenlerinin veri türlerine bağlıdır. Genel olarak, Visual Basic sonuç veri türünü belirlemek için aşağıdaki ilkeleri kullanır:  
  
- İkili işlecin her iki işleneni de aynı veri türüne sahipse, sonuç bu veri türüne sahiptir. Bir özel durum `Boolean``Short`zorlanır.  
  
- İşaretsiz bir işlenen imzalı bir işlenen ile katılıyorsa, sonuç, en azından işlenen olarak en az bir Aralık olan imzalı bir tür içerir.  
  
- Aksi halde, sonuç genellikle iki işlenen veri türünden daha büyük olur.  
  
 Sonuç veri türünün işlenen veri türü ile aynı olamayacağını unutmayın.  
  
> [!NOTE]
> Sonuç veri türü, işlemin sonucu olan tüm olası değerleri tutabilecek kadar her zaman büyük değildir. Değer sonuç veri türü için çok büyükse <xref:System.OverflowException> bir özel durum oluşabilir.  
  
### <a name="unary--and--operators"></a>Birli + ve – Işleçler  
 Aşağıdaki tabloda, `+` ve `–`iki birli operatör için sonuç veri türleri gösterilmektedir.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Birli `+`|Kısa|SByte|Bayt|Kısa|UShort|Tamsayı|UInteger|Uzun|'Tur|  
|Birli `–`|Kısa|SByte|Kısa|Kısa|Tamsayı|Tamsayı|Uzun|Uzun|Ondalık|  
  
### <a name="-and--operators"></a><\< ve > > Işleçleri  
 Aşağıdaki tabloda, `<<` ve `>>`iki bit kaydırma işleci için sonuç veri türleri gösterilmektedir. Visual Basic her bir bit kaydırma işlecini sol işleneninde birli işleç olarak değerlendirir (kaydırılan bit kalıbı).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Kısa|SByte|Bayt|Kısa|UShort|Tamsayı|UInteger|Uzun|'Tur|  
  
 Sol işlenen `Decimal`, `Single`, `Double`veya `String`, Visual Basic işlemi işlemden önce `Long` dönüştürmeye çalışır ve sonuç veri türü `Long`olur. Sağ işlenen (kaydırma yapılacak bit konumlarının sayısı) `Integer` veya `Integer`için widens bir tür olmalıdır.  
  
### <a name="binary----and-mod-operators"></a>İkili +, –, \*ve mod Işleçleri  
 Aşağıdaki tabloda, ikili `+` ve `–` işleçleri ve `*` ve `Mod` işleçleri için sonuç veri türleri gösterilmektedir. Bu tablonun simetrik olduğunu unutmayın; belirli bir işlenen veri türleri birleşimi için, sonuç veri türü işlenen sıralarından bağımsız olarak aynıdır.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Kısa|SByte|Kısa|Kısa|Tamsayı|Tamsayı|Uzun|Uzun|Ondalık|  
|`SByte`|SByte|SByte|Kısa|Kısa|Tamsayı|Tamsayı|Uzun|Uzun|Ondalık|  
|`Byte`|Kısa|Kısa|Bayt|Kısa|UShort|Tamsayı|UInteger|Uzun|'Tur|  
|`Short`|Kısa|Kısa|Kısa|Kısa|Tamsayı|Tamsayı|Uzun|Uzun|Ondalık|  
|`UShort`|Tamsayı|Tamsayı|UShort|Tamsayı|UShort|Tamsayı|UInteger|Uzun|'Tur|  
|`Integer`|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Uzun|Uzun|Ondalık|  
|`UInteger`|Uzun|Uzun|UInteger|Uzun|UInteger|Uzun|UInteger|Uzun|'Tur|  
|`Long`|Uzun|Uzun|Uzun|Uzun|Uzun|Uzun|Uzun|Uzun|Ondalık|  
|`ULong`|Ondalık|Ondalık|'Tur|Ondalık|'Tur|Ondalık|'Tur|Ondalık|'Tur|  
  
### <a name="-operator"></a>\\ İşleci  
 Aşağıdaki tabloda `\` işlecinin sonuç veri türleri gösterilmektedir. Bu tablonun simetrik olduğunu unutmayın; belirli bir işlenen veri türleri birleşimi için, sonuç veri türü işlenen sıralarından bağımsız olarak aynıdır.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Kısa|SByte|Kısa|Kısa|Tamsayı|Tamsayı|Uzun|Uzun|Uzun|  
|`SByte`|SByte|SByte|Kısa|Kısa|Tamsayı|Tamsayı|Uzun|Uzun|Uzun|  
|`Byte`|Kısa|Kısa|Bayt|Kısa|UShort|Tamsayı|UInteger|Uzun|'Tur|  
|`Short`|Kısa|Kısa|Kısa|Kısa|Tamsayı|Tamsayı|Uzun|Uzun|Uzun|  
|`UShort`|Tamsayı|Tamsayı|UShort|Tamsayı|UShort|Tamsayı|UInteger|Uzun|'Tur|  
|`Integer`|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Uzun|Uzun|Uzun|  
|`UInteger`|Uzun|Uzun|UInteger|Uzun|UInteger|Uzun|UInteger|Uzun|'Tur|  
|`Long`|Uzun|Uzun|Uzun|Uzun|Uzun|Uzun|Uzun|Uzun|Uzun|  
|`ULong`|Uzun|Uzun|'Tur|Uzun|'Tur|Uzun|'Tur|Uzun|'Tur|  
  
 `\` işlecinin herhangi bir işleneni [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)veya [Double](../../../visual-basic/language-reference/data-types/double-data-type.md)ise, Visual Basic işlemden önce [uzun bir süre](../../../visual-basic/language-reference/data-types/long-data-type.md) dönüştürmeye çalışır ve sonuç veri türü `Long`olur.  
  
## <a name="relational-and-bitwise-comparisons"></a>İlişkisel ve bit düzeyinde karşılaştırmalar  
 İlişkisel işlemin sonuç veri türü (`=`, `<>`, `<`, `>`, `<=`, `>=`) her zaman `Boolean`[Boole veri türü](../../../visual-basic/language-reference/data-types/boolean-data-type.md). `OrElse`işlenenleri üzerinde mantıksal işlemler (`And`, `AndAlso`, `Not`, `Or`, `Xor`, `Boolean`) için de geçerlidir.  
  
 Bit düzeyinde mantıksal bir işlemin sonuç veri türü, işlenenlerinin veri türlerine bağlıdır. `AndAlso` ve `OrElse` yalnızca `Boolean`için tanımlandığını ve Visual Basic her işleneni, işlemi gerçekleştirmeden önce `Boolean` gereken şekilde dönüştürdüğüne unutmayın.  
  
### <a name="-----and--operators"></a>=, < >, \<, >, \<= ve > = Işleçleri  
 Her iki işlenen de `Boolean`, Visual Basic `False``True` daha küçük olacak şekilde kabul eder. Sayısal tür bir `String`karşılaştırılır, Visual Basic işlemden önce `Double` `String` dönüştürmeye çalışır. Bir `Char` veya `Date` işleneni yalnızca aynı veri türünün başka bir işleneniyle karşılaştırılabilir. Sonuç veri türü her zaman `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Bit düzeyinde Not Işleci  
 Aşağıdaki tabloda, bit düzeyinde `Not` işlecinin sonuç veri türleri gösterilmektedir.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boole değeri|SByte|Bayt|Kısa|UShort|Tamsayı|UInteger|Uzun|'Tur|  
  
 İşlenen `Decimal`, `Single`, `Double`veya `String`, Visual Basic işlemi işlemden önce `Long` dönüştürmeye çalışır ve sonuç veri türü `Long`olur.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bit düzeyinde and, or ve XOR Işleçleri  
 Aşağıdaki tabloda, bit düzeyinde `And`, `Or`ve `Xor` işleçleri için sonuç veri türleri gösterilmektedir. Bu tablonun simetrik olduğunu unutmayın; belirli bir işlenen veri türleri birleşimi için, sonuç veri türü işlenen sıralarından bağımsız olarak aynıdır.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boole değeri|SByte|Kısa|Kısa|Tamsayı|Tamsayı|Uzun|Uzun|Uzun|  
|`SByte`|SByte|SByte|Kısa|Kısa|Tamsayı|Tamsayı|Uzun|Uzun|Uzun|  
|`Byte`|Kısa|Kısa|Bayt|Kısa|UShort|Tamsayı|UInteger|Uzun|'Tur|  
|`Short`|Kısa|Kısa|Kısa|Kısa|Tamsayı|Tamsayı|Uzun|Uzun|Uzun|  
|`UShort`|Tamsayı|Tamsayı|UShort|Tamsayı|UShort|Tamsayı|UInteger|Uzun|'Tur|  
|`Integer`|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Uzun|Uzun|Uzun|  
|`UInteger`|Uzun|Uzun|UInteger|Uzun|UInteger|Uzun|UInteger|Uzun|'Tur|  
|`Long`|Uzun|Uzun|Uzun|Uzun|Uzun|Uzun|Uzun|Uzun|Uzun|  
|`ULong`|Uzun|Uzun|'Tur|Uzun|'Tur|Uzun|'Tur|Uzun|'Tur|  
  
 Bir işlenen `Decimal`, `Single`, `Double`veya `String`, Visual Basic işlemi işlemden önce `Long` dönüştürmeye çalışır ve sonuç veri türü, o işlenenin zaten `Long`ile aynı olur.  
  
## <a name="miscellaneous-operators"></a>Çeşitli İşleçler  
 `&` işleci yalnızca `String` işlenenleri birleştirmek için tanımlanmıştır. Visual Basic, her işleneni işlemden önce `String` için gereken şekilde dönüştürür ve sonuç veri türü her zaman `String`. `&` işlecinin amaçları doğrultusunda, `Option Strict` `On`olsa bile tüm `String` dönüştürmelerin genişleyen olduğu kabul edilir.  
  
 `Is` ve `IsNot` işleçleri her iki işlenenin de bir başvuru türü olmasını gerektirir. `TypeOf`...`Is` ifadesi, İlk işlenenin bir başvuru türünde olmasını ve ikinci işlenenin bir veri türünün adı olmasını gerektirir. Tüm bu durumlarda sonuç veri türü `Boolean`.  
  
 `Like` işleci yalnızca `String` işlenenlerinin örüntüsünün eşleşmesi için tanımlanır. Visual Basic, her işleneni işlemden önce `String` gereken şekilde dönüştürmeye çalışır. Sonuç veri türü her zaman `Boolean`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri Türleri](../../../visual-basic/language-reference/data-types/index.md)
- [İşleçler ve İfadeler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic karşılaştırma Işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [işleçler](../../../visual-basic/language-reference/operators/index.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Karşılaştırma İşleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
