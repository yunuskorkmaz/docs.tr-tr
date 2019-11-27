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
ms.openlocfilehash: e1feb08539e47ec6fda64aa1a1f8ec2cc19f7b62
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346062"
---
# <a name="comparison-operators-in-visual-basic"></a>Visual Basic'de Karşılaştırma İşleçleri
Karşılaştırma işleçleri iki ifadeyi karşılaştırır ve değerlerinin ilişkisini temsil eden bir `Boolean` değeri döndürür. Sayısal değerleri karşılaştırma işleçleri, dizeleri karşılaştırmak için İşleçleri ve nesneleri karşılaştırmak için işleçleri vardır. Üç tür işlecin hepsi burada açıklanmıştır.  
  
## <a name="comparing-numeric-values"></a>Sayısal değerleri karşılaştırma  
 Visual Basic altı sayısal karşılaştırma işlecini kullanarak sayısal değerleri karşılaştırır. Her operatör, işlenen iki ifade olarak sayısal değerler değerlendirir. Aşağıdaki tablo işleçleri listeler ve bunların örneklerini gösterir.  
  
|İşleç|Durum test edildi|Örnekler|  
|--------------|----------------------|--------------|  
|`=` (eşitlik)|İkincinin değerine eşit olan ilk ifadenin değeri mi?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (eşitsizlik)|İlk ifadenin değeri ikincinin değerine eşit değil mi?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (küçüktür)|İlk ifadenin değeri ikinciden küçük mi?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (büyüktür)|İkincisinin değerinden büyük olan ilk ifadenin değeri mi?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (küçüktür veya eşittir)|İlk ifadenin değeri ikinciden küçük veya ona eşit mi?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (büyüktür veya eşittir)|İlk ifadenin değeri ikinciden büyük veya ona eşit mi?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Dizeleri Karşılaştırma  
 Visual Basic, dizeleri [benzer işleci](../../../../visual-basic/language-reference/operators/like-operator.md) ve sayısal karşılaştırma işleçleri ile karşılaştırır. `Like` işleci, bir model belirtmenize olanak tanır. Daha sonra dize, bu düzene göre karşılaştırılır ve eşleşiyorsa sonuç `True`. Aksi takdirde, sonuç `False`. Sayısal işleçler, aşağıdaki örnekte gösterildiği gibi, sıralama sıralamasına göre `String` değerlerini karşılaştırmanıza imkan tanır.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 Önceki örnekteki sonuç, ilk dizedeki ilk karakter ikinci dizedeki ilk karakterden önce sıralandığı için `True`. İlk karakter eşitse, karşılaştırma her iki dizelerde de bir sonraki karaktere devam eder ve bu şekilde devam eder. Ayrıca, aşağıdaki örnekte gösterildiği gibi, eşitlik işlecini kullanarak dizelerin eşitliğini test edebilirsiniz.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Bir dize diğerinin ön eki ise (örneğin, "AA" ve "aaa"), daha uzun dize, daha kısa dizeden daha büyük olarak değerlendirilir. Aşağıdaki örnek bunu göstermektedir.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 Sıralama düzeni, `Option Compare`ayarına bağlı olarak bir ikili karşılaştırmaya veya bir metinsel karşılaştırmaya göre belirlenir. Daha fazla bilgi için bkz. [Option Compare deyimleri](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Nesneleri karşılaştırma  
 Visual Basic, iki nesne başvuru değişkenini [,, işleç](../../../../visual-basic/language-reference/operators/is-operator.md) ve [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md)ile karşılaştırır. İki başvuru değişkeninin aynı nesne örneğine başvuruda bulunduğunu anlamak için bu işleçlerden birini kullanabilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 Yukarıdaki örnekte, her iki değişken de aynı örneğe başvurduğundan, `x Is y` `True`olarak değerlendirilir. Bu sonucu aşağıdaki örnekle karşıtın.  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 Yukarıdaki örnekte, `x Is y` `False`değerlendirilir, çünkü değişkenler aynı türdeki nesnelere başvurmakla birlikte, bu türden farklı örneklere başvururlar.  
  
 Aynı örneği işaret eden iki nesne için test etmek istediğinizde `IsNot` işleci, `Not` ve `Is`dilbilgisi ve bir birleşimini önlemenize olanak sağlar. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 Yukarıdaki örnekte, `If a IsNot b` `If Not a Is b`eşdeğerdir.  
  
### <a name="comparing-object-type"></a>Nesne türünü karşılaştırma  
 Bir nesnenin `TypeOf`...`Is` ifadesiyle belirli türde olup olmadığını test edebilirsiniz. Sözdizimi aşağıdaki gibidir:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 `typename` bir arabirim türü belirttiğinde, nesne arabirim türünü uygularsa, `TypeOf`...`Is` ifadesi `True` döndürür. `typename` bir sınıf türüsiyse, nesne belirtilen sınıfın bir örneği veya belirtilen sınıftan türetilen bir sınıf ise `True` döndürür. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 Yukarıdaki örnekte, `x` türü `Control`devralan `Button`olduğundan `TypeOf x Is Control` ifadesi `True` olarak değerlendirilir.  
  
 Daha fazla bilgi için bkz. [typeof işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Değer Karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Karşılaştırma İşleçleri](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [işleçler](../../../../visual-basic/language-reference/operators/index.md)
- [Visual Basic aritmetik Işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic birleştirme Işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
