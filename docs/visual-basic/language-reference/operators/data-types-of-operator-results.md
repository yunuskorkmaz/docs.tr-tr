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
ms.openlocfilehash: b80508c5619770da0c7dc78003ff9d4847dd94d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371433"
---
# <a name="data-types-of-operator-results-visual-basic"></a>İşleç Sonuçlarının Veri Türleri (Visual Basic)
Visual Basic, işlenen veri türlerine göre bir işlemin sonuç veri türünü belirler. Bazı durumlarda bu, iki işlenenden daha büyük bir aralığa sahip bir veri türü olabilir.  
  
## <a name="data-type-ranges"></a>Veri Türü Aralıkları  
 En küçükten en büyüğe doğru sırada ilgili veri türlerinin aralıkları şunlardır:  
  
- [Boolean](../data-types/boolean-data-type.md) — iki olası değer  
  
- [SByte](../data-types/sbyte-data-type.md), [byte](../data-types/byte-data-type.md) — 256 olası integral değeri  
  
- [Short](../data-types/short-data-type.md), [ushort](../data-types/ushort-data-type.md) — 65.536 (6.5... E + 4) olası integral değerleri  
  
- [Integer](../data-types/integer-data-type.md), [uinteger](../data-types/uinteger-data-type.md) — 4.294.967.296 (4.2... E + 9) olası integral değerleri  
  
- [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md) — 18446744073709551615 (1.8... E + 19) olası integral değerleri  
  
- [Decimal](../data-types/decimal-data-type.md) — 1,5... E + 29 olası integral değerleri, maksimum Aralık 7.9... E + 28 (mutlak değer)  
  
- [Single](../data-types/single-data-type.md) — maksimum Aralık 3.4... E + 38 (mutlak değer)  
  
- [Double](../data-types/double-data-type.md) — maksimum Aralık 1.7... E + 308 (mutlak değer)  
  
 Visual Basic veri türleri hakkında daha fazla bilgi için bkz. [veri türleri](../data-types/index.md).  
  
 Bir işlenen [hiçbir şey](../nothing.md)kabul verirse, Visual Basic aritmetik işleçleri onu sıfır olarak değerlendirir.  
  
## <a name="decimal-arithmetic"></a>Ondalık aritmetik  
 [Ondalık](../data-types/decimal-data-type.md) veri türünün ne kayan nokta ne de tamsayı olduğunu unutmayın.  
  
 ,,, Veya işleminin herhangi bir işleneni `+` `–` `*` `/` `Mod` ise `Decimal` ve diğeri `Single` veya değilse `Double` , diğer işleneni widens Visual Basic `Decimal` . Üzerinde işlemi gerçekleştirir `Decimal` ve sonuç veri türü olur `Decimal` .  
  
## <a name="floating-point-arithmetic"></a>Kayan nokta aritmetiği  
 Visual Basic, bu tür işlemler için en verimli veri türü olan [Double](../data-types/double-data-type.md)'ta çoğu kayan nokta aritmetiği gerçekleştirir. Ancak, bir işlenen [tek](../data-types/single-data-type.md) ise ve diğeri değilse `Double` , Visual Basic içinde işlem gerçekleştirir `Single` . Her işleneni, işlem öncesinde uygun veri türü için gereken şekilde widens ve sonuç bu veri türüne sahip olur.  
  
### <a name="-and--operators"></a>/ve ^ Işleçleri  
 `/`İşleci yalnızca [Decimal](../data-types/decimal-data-type.md), [Single](../data-types/single-data-type.md)ve [Double](../data-types/double-data-type.md) veri türleri için tanımlanır. Her işleneni, işlem öncesinde uygun veri türü için gereken şekilde widens Visual Basic ve sonuç bu veri türüne sahip.  
  
 Aşağıdaki tabloda operatör için sonuç veri türleri gösterilmektedir `/` . Bu tablonun simetrik olduğunu unutmayın; belirli bir işlenen veri türleri birleşimi için, sonuç veri türü işlenen sıralarından bağımsız olarak aynıdır.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Herhangi bir tamsayı türü|  
|`Decimal`|Ondalık|Tek|Çift|Ondalık|  
|`Single`|Tek|Tek|Çift|Tek|  
|`Double`|Çift|Çift|Çift|Çift|  
|Herhangi bir tamsayı türü|Ondalık|Tek|Çift|Çift|  
  
 `^`İşleci yalnızca `Double` veri türü için tanımlanır. Her bir işleneni işlemden önce gereken şekilde widens Visual Basic `Double` ve sonuç veri türü her zaman olur `Double` .  
  
## <a name="integer-arithmetic"></a>Tamsayı aritmetik  
 Bir tamsayı işleminin sonuç veri türü, işlenenlerinin veri türlerine bağlıdır. Genel olarak, Visual Basic sonuç veri türünü belirlemek için aşağıdaki ilkeleri kullanır:  
  
- İkili işlecin her iki işleneni de aynı veri türüne sahipse, sonuç bu veri türüne sahiptir. İçin zorunlu olan bir özel durum `Boolean` `Short` .  
  
- İşaretsiz bir işlenen imzalı bir işlenen ile katılıyorsa, sonuç, en azından işlenen olarak en az bir Aralık olan imzalı bir tür içerir.  
  
- Aksi halde, sonuç genellikle iki işlenen veri türünden daha büyük olur.  
  
 Sonuç veri türünün işlenen veri türü ile aynı olamayacağını unutmayın.  
  
> [!NOTE]
> Sonuç veri türü, işlemin sonucu olan tüm olası değerleri tutabilecek kadar her zaman büyük değildir. <xref:System.OverflowException>Değer sonuç veri türü için çok büyükse bir özel durum oluşabilir.  
  
### <a name="unary--and--operators"></a>Birli + ve – Işleçler  
 Aşağıdaki tabloda, iki birli işleç ve için sonuç veri türleri gösterilmektedir `+` `–` .  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Li`+`|Kısadır|SByte|Bayt|Kısadır|UShort|Tamsayı|UInteger|Kalacağını|'Tur|  
|Li`–`|Kısadır|SByte|Kısadır|Kısadır|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Ondalık|  
  
### <a name="-and--operators"></a><\< and >> Işleçleri  
 Aşağıdaki tabloda, iki bit kaydırma işleci ve için sonuç veri türleri gösterilmektedir `<<` `>>` . Visual Basic her bir bit kaydırma işlecini sol işleneninde birli işleç olarak değerlendirir (kaydırılan bit kalıbı).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Kısadır|SByte|Bayt|Kısadır|UShort|Tamsayı|UInteger|Kalacağını|'Tur|  
  
 Sol işlenen,,, `Decimal` `Single` `Double` veya `String` Visual Basic, `Long` işlemi işlemden önce dönüştürmeye çalışır ve sonuç veri türü olur `Long` . Sağ işlenen (kaydırma yapılacak bit konumlarının sayısı) `Integer` veya widens bir tür olmalıdır `Integer` .  
  
### <a name="binary----and-mod-operators"></a>İkili +, –, \* , ve mod işleçleri  
 Aşağıdaki tabloda, ikili `+` ve `–` İşleçler ve `*` ve işleçleri için sonuç veri türleri gösterilmektedir `Mod` . Bu tablonun simetrik olduğunu unutmayın; belirli bir işlenen veri türleri birleşimi için, sonuç veri türü işlenen sıralarından bağımsız olarak aynıdır.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Kısadır|SByte|Kısadır|Kısadır|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Ondalık|  
|`SByte`|SByte|SByte|Kısadır|Kısadır|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Ondalık|  
|`Byte`|Kısadır|Kısadır|Bayt|Kısadır|UShort|Tamsayı|UInteger|Kalacağını|'Tur|  
|`Short`|Kısadır|Kısadır|Kısadır|Kısadır|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Ondalık|  
|`UShort`|Tamsayı|Tamsayı|UShort|Tamsayı|UShort|Tamsayı|UInteger|Kalacağını|'Tur|  
|`Integer`|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Ondalık|  
|`UInteger`|Kalacağını|Kalacağını|UInteger|Kalacağını|UInteger|Kalacağını|UInteger|Kalacağını|'Tur|  
|`Long`|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Ondalık|  
|`ULong`|Ondalık|Ondalık|'Tur|Ondalık|'Tur|Ondalık|'Tur|Ondalık|'Tur|  
  
### <a name="-operator"></a>\\ İşleci  
 Aşağıdaki tabloda operatör için sonuç veri türleri gösterilmektedir `\` . Bu tablonun simetrik olduğunu unutmayın; belirli bir işlenen veri türleri birleşimi için, sonuç veri türü işlenen sıralarından bağımsız olarak aynıdır.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Kısadır|SByte|Kısadır|Kısadır|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Kalacağını|  
|`SByte`|SByte|SByte|Kısadır|Kısadır|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Kalacağını|  
|`Byte`|Kısadır|Kısadır|Bayt|Kısadır|UShort|Tamsayı|UInteger|Kalacağını|'Tur|  
|`Short`|Kısadır|Kısadır|Kısadır|Kısadır|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Kalacağını|  
|`UShort`|Tamsayı|Tamsayı|UShort|Tamsayı|UShort|Tamsayı|UInteger|Kalacağını|'Tur|  
|`Integer`|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Kalacağını|  
|`UInteger`|Kalacağını|Kalacağını|UInteger|Kalacağını|UInteger|Kalacağını|UInteger|Kalacağını|'Tur|  
|`Long`|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|  
|`ULong`|Kalacağını|Kalacağını|'Tur|Kalacağını|'Tur|Kalacağını|'Tur|Kalacağını|'Tur|  
  
 İşlecin her iki işleneni de `\` [Decimal](../data-types/decimal-data-type.md), [Single](../data-types/single-data-type.md)veya [Double](../data-types/double-data-type.md)Ise, Visual Basic işlemden önce [uzun bir süre](../data-types/long-data-type.md) önce dönüştürmeye çalışır ve sonuç veri türü olur `Long` .  
  
## <a name="relational-and-bitwise-comparisons"></a>İlişkisel ve bit düzeyinde karşılaştırmalar  
 İlişkisel işlemin sonuç veri türü ( `=` , `<>` ,, `<` `>` , `<=` , `>=` ) her zaman `Boolean` [Boole veri türüdür](../data-types/boolean-data-type.md). Aynı değer, `And` `AndAlso` `Not` `Or` `OrElse` `Xor` `Boolean` işlenenler üzerindeki mantıksal işlemler (,,,,,) için de geçerlidir.  
  
 Bit düzeyinde mantıksal bir işlemin sonuç veri türü, işlenenlerinin veri türlerine bağlıdır. `AndAlso`Ve `OrElse` ' nin yalnızca için tanımlandığını `Boolean` ve Visual Basic işlemi gerçekleştirmeden önce her işleneni gerektiği şekilde dönüştürdüğüne unutmayın `Boolean` .  
  
### <a name="-----and--operators"></a>=,  <>, \<, > , \<=, and > = işleçleri  
 Her iki işlenen de `Boolean` Visual Basic, ' `True` den küçük olarak kabul edilir `False` . Sayısal bir tür bir ile karşılaştırılsa `String` , Visual Basic `String` işlemden önce öğesine dönüştürmeye çalışır `Double` . Bir `Char` veya `Date` işleneni yalnızca aynı veri türünün başka bir işleneniyle karşılaştırılabilir. Sonuç veri türü her zaman `Boolean` .  
  
### <a name="bitwise-not-operator"></a>Bit düzeyinde Not Işleci  
 Aşağıdaki tabloda bit düzeyinde operatör için sonuç veri türleri gösterilmektedir `Not` .  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boole|SByte|Bayt|Kısadır|UShort|Tamsayı|UInteger|Kalacağını|'Tur|  
  
 İşleneni,, `Decimal` `Single` `Double` veya `String` Visual Basic, `Long` işlemi işlemden önce dönüştürmeye çalışır ve sonuç veri türü olur `Long` .  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bit düzeyinde and, or ve XOR Işleçleri  
 Aşağıdaki tabloda bit düzeyinde `And` , `Or` , ve işleçleri için sonuç veri türleri gösterilmektedir `Xor` . Bu tablonun simetrik olduğunu unutmayın; belirli bir işlenen veri türleri birleşimi için, sonuç veri türü işlenen sıralarından bağımsız olarak aynıdır.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boole|SByte|Kısadır|Kısadır|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Kalacağını|  
|`SByte`|SByte|SByte|Kısadır|Kısadır|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Kalacağını|  
|`Byte`|Kısadır|Kısadır|Bayt|Kısadır|UShort|Tamsayı|UInteger|Kalacağını|'Tur|  
|`Short`|Kısadır|Kısadır|Kısadır|Kısadır|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Kalacağını|  
|`UShort`|Tamsayı|Tamsayı|UShort|Tamsayı|UShort|Tamsayı|UInteger|Kalacağını|'Tur|  
|`Integer`|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Tamsayı|Kalacağını|Kalacağını|Kalacağını|  
|`UInteger`|Kalacağını|Kalacağını|UInteger|Kalacağını|UInteger|Kalacağını|UInteger|Kalacağını|'Tur|  
|`Long`|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|Kalacağını|  
|`ULong`|Kalacağını|Kalacağını|'Tur|Kalacağını|'Tur|Kalacağını|'Tur|Kalacağını|'Tur|  
  
 Bir işlenen,, `Decimal` `Single` `Double` veya `String` Visual Basic, bunu işlemden önceki öğesine dönüştürmeye çalışır `Long` ve sonuç veri türü, o işlenenin zaten olduğu gibi olur `Long` .  
  
## <a name="miscellaneous-operators"></a>Çeşitli İşleçler  
 `&`İşleci yalnızca işlenenleri birleştirmek için tanımlanır `String` . Visual Basic, her işleneni işlemden önce gereken şekilde dönüştürür `String` ve sonuç veri türü her zaman olur `String` . İşlecinin amaçları doğrultusunda, `&` öğesine yapılan tüm dönüştürmeler, `String` olsa bile, genişletme olarak kabul edilir `Option Strict` `On` .  
  
 `Is`Ve `IsNot` işleçleri, her iki işlenenin de bir başvuru türü olmasını gerektirir. `TypeOf`... `Is` İfadesi, İlk işlenenin bir başvuru türünde olmasını ve ikinci işlenenin bir veri türünün adı olmasını gerektirir. Tüm bu durumlarda sonuç veri türü olur `Boolean` .  
  
 `Like`İşleci yalnızca işlenenlerle eşleşen desenler için tanımlanır `String` . Visual Basic, her işleneni işlemden önce gereken şekilde dönüştürmeye çalışır `String` . Sonuç veri türü her zaman `Boolean` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Veri türleri](../data-types/index.md)
- [İşleçler ve Ifadeler](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Visual Basic'de Aritmetik İşleçler](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic'de Karşılaştırma İşleçleri](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [İşleçler](index.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Aritmetik İşleçler](arithmetic-operators.md)
- [Karşılaştırma Işleçleri](comparison-operators.md)
- [Option Strict Deyimi](../statements/option-strict-statement.md)
