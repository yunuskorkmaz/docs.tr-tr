---
title: Karşılaştırma İşleçleri
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- comparison operators [Visual Basic], comparing objects
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- string comparison [Visual Basic], operators
- objects [Visual Basic], comparing
- numbers [Visual Basic], comparing
- Visual Basic code, operators
- string comparison [Visual Basic]
- numeric values [Visual Basic], comparing
- comparison operators [Visual Basic], comparing numeric values
- operators [Visual Basic], comparison
ms.assetid: 0b570339-5407-474f-8421-e183a8b303ee
ms.openlocfilehash: 7a93928ff95e307c64149da7ab21476ffd4fa77d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388835"
---
# <a name="comparison-operators-in-visual-basic"></a>Visual Basic'de Karşılaştırma İşleçleri
Karşılaştırma işleçleri iki ifadeyi karşılaştırır ve `Boolean` değerlerinin ilişkisini temsil eden bir değer döndürür. Sayısal değerleri karşılaştırma işleçleri, dizeleri karşılaştırmak için İşleçleri ve nesneleri karşılaştırmak için işleçleri vardır. Üç tür işlecin hepsi burada açıklanmıştır.  
  
## <a name="comparing-numeric-values"></a>Sayısal değerleri karşılaştırma  
 Visual Basic altı sayısal karşılaştırma işlecini kullanarak sayısal değerleri karşılaştırır. Her operatör, işlenen iki ifade olarak sayısal değerler değerlendirir. Aşağıdaki tablo işleçleri listeler ve bunların örneklerini gösterir.  
  
|Operatör|Durum test edildi|Örnekler|  
|--------------|----------------------|--------------|  
|`=`Eþit|İkincinin değerine eşit olan ilk ifadenin değeri mi?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>`Olmama|İlk ifadenin değeri ikincinin değerine eşit değil mi?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<`(Küçüktür)|İlk ifadenin değeri ikinciden küçük mi?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>`(Büyüktür)|İkincisinin değerinden büyük olan ilk ifadenin değeri mi?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=`(Küçüktür veya eşittir)|İlk ifadenin değeri ikinciden küçük veya ona eşit mi?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=`(Büyüktür veya eşittir)|İlk ifadenin değeri ikinciden büyük veya ona eşit mi?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Dizeleri Karşılaştırma  
 Visual Basic, dizeleri [benzer işleci](../../../language-reference/operators/like-operator.md) ve sayısal karşılaştırma işleçleri ile karşılaştırır. `Like`İşleci, bir model belirtmenize olanak tanır. Daha sonra dize, bu düzene göre karşılaştırılır ve eşleşiyorsa sonuç olur `True` . Aksi takdirde, sonuç olur `False` . Sayısal işleçler, `String` Aşağıdaki örnekte gösterildiği gibi, değerlerini sıralama sıralarına göre karşılaştırmanıza imkan tanır.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 Önceki örnekteki sonuç, `True` ilk dizedeki ilk karakter ikinci dizedeki ilk karakterden önce sıralandığından oluşur. İlk karakter eşitse, karşılaştırma her iki dizelerde de bir sonraki karaktere devam eder ve bu şekilde devam eder. Ayrıca, aşağıdaki örnekte gösterildiği gibi, eşitlik işlecini kullanarak dizelerin eşitliğini test edebilirsiniz.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Bir dize diğerinin ön eki ise (örneğin, "AA" ve "aaa"), daha uzun dize, daha kısa dizeden daha büyük olarak değerlendirilir. Aşağıdaki örnek bunu göstermektedir.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 Sıralama düzeni, ayarına bağlı olarak bir ikili karşılaştırmaya veya metinsel karşılaştırmaya göre belirlenir `Option Compare` . Daha fazla bilgi için bkz. [Option Compare deyimleri](../../../language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Nesneleri karşılaştırma  
 Visual Basic, iki nesne başvuru değişkenini [,, işleç](../../../language-reference/operators/is-operator.md) ve [IsNot işleci](../../../language-reference/operators/isnot-operator.md)ile karşılaştırır. İki başvuru değişkeninin aynı nesne örneğine başvuruda bulunduğunu anlamak için bu işleçlerden birini kullanabilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 Yukarıdaki örnekte,, `x Is y` `True` her iki değişken de aynı örneğe başvurduğundan olarak değerlendirilir. Bu sonucu aşağıdaki örnekle karşıtın.  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 Önceki örnekte, `x Is y` olarak değerlendirilir `False` , çünkü değişkenler aynı türdeki nesnelere başvurmakla birlikte, bu tür farklı örneklere başvururlar.  
  
 Aynı örneğe işaret eden iki nesne için test etmek istediğinizde, `IsNot` işleç, ve ' nin dilbilgisi ve birleşimini önlemenize olanak sağlar `Not` `Is` . Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 Yukarıdaki örnekte, `If a IsNot b` öğesine eşdeğerdir `If Not a Is b` .  
  
### <a name="comparing-object-type"></a>Nesne türünü karşılaştırma  
 Bir nesnenin `TypeOf` ... ifadesiyle belirli bir türde olup olmadığını test edebilirsiniz `Is` . Söz dizimi aşağıdaki gibidir:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 `typename`Bir arabirim türü belirttiğinde, `TypeOf` `Is` `True` nesne arabirim türünü uygularsa... ifadesi döndürür. `typename`, Bir sınıf türü olduğunda, `True` nesne belirtilen sınıfın bir örneği veya belirtilen sınıftan türetilen bir sınıf ise, ifade döndürür. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 Önceki örnekte, `TypeOf x Is Control` ifadesi, `True` `x` `Button` ' den devralan, türü olduğu için olarak değerlendirilir `Control` .  
  
 Daha fazla bilgi için bkz. [typeof işleci](../../../language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değer Karşılaştırmaları](value-comparisons.md)
- [Karşılaştırma Işleçleri](../../../language-reference/operators/comparison-operators.md)
- [İşleçler](../../../language-reference/operators/index.md)
- [Visual Basic'de Aritmetik İşleçler](arithmetic-operators.md)
- [Visual Basic'de Birleştirme İşleçleri](concatenation-operators.md)
- [Visual Basic'de Mantıksal ve Bit Düzeyinde İşleçler](logical-and-bitwise-operators.md)
