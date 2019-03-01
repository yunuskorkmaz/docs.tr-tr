---
title: Visual Basic'de Karşılaştırma İşleçleri
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
ms.openlocfilehash: cd7ee90e749be76012cf7143787bc6f1d096da03
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969381"
---
# <a name="comparison-operators-in-visual-basic"></a>Visual Basic'de Karşılaştırma İşleçleri
Karşılaştırma işleçleri iki ifadeden karşılaştırın ve dönüş bir `Boolean` değerleri arasındaki ilişkiyi gösteren bir değer. Sayısal değerler için dizeleri Karşılaştırma işleçleri ve nesneleri Karşılaştırma işleçleri karşılaştırmak için işleci vardır. Üç tür işleç tüm burada ele alınmıştır.  
  
## <a name="comparing-numeric-values"></a>Sayısal değerleri karşılaştırma  
 Visual Basic altı sayısal Karşılaştırma işleçleri kullanarak sayısal değeri karşılaştırır. Her işleç sayısal değerlere dönüşen iki ifade işlenenleri olarak alır. Aşağıdaki tabloda işleçleri listelenir ve her örneklerini gösterir.  
  
|İşleç|Test koşulu|Örnekler|  
|--------------|----------------------|--------------|  
|`=` (Eşitlik)|İlk ifade değerini ikinci değerine mi?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>` (Eşitsizlik)|İlk ifade değeri, ikinci değerine eşit mi?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<` (Küçüktür)|İlk ifade değeri değerinden ikinci değeri mi?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>` (Büyüktür)|İlk ifade değeri ikinci değerinden büyük mü?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=` (Küçüktür veya eşittir)|Değer ilk ifadenin saniye değerini küçüktür veya eşittir mi?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=` (Büyüktür veya eşittir)|Büyüktür veya eşittir saniye değerini ilk ifadenin değeri mi?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Dizeleri Karşılaştırma  
 Visual Basic kullanarak dizeleri karşılaştırır [gibi işleci](../../../../visual-basic/language-reference/operators/like-operator.md) sayısal Karşılaştırma işleçleri yanı sıra. `Like` İşleci, bir desen belirtmenize olanak sağlar. Dize, daha sonra düzeni ile karşılaştırılır ve eşleşirse, sonuç `True`. Aksi halde sonuç, `False`. Sayısal işleçleri, karşılaştırmanızı sağlar `String` değerlerini aşağıdaki örnekte gösterildiği gibi sıralama düzenlerine bağlı.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 Önceki örnekte sonuç `True` olduğundan ikinci dizenin ilk karakteri önce ilk dizenin ilk karakteri sıralar. İlk karakteri eşit ise karşılaştırma iki dize içindeki sonraki karakteri devam ve benzeri. Ayrıca aşağıdaki örnekte gösterildiği gibi eşitlik işlecini kullanarak dize eşitliğini test edebilirsiniz.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Başka bir önek "aa" ve "aaa" gibi bir dize ise, uzun dizeyi kısa dize büyük olması kabul edilir. Aşağıdaki örnek bunu göstermektedir.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 İkili karşılaştırma veya ayarına bağlı olarak metinsel karşılaştırma sıralama düzenini temel `Option Compare`. Daha fazla bilgi için [seçenek karşılaştırma ifadesini](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Nesneleri karşılaştırma  
 Visual Basic ile iki nesne başvurusu değişkenini karşılaştırır [işleci olan](../../../../visual-basic/language-reference/operators/is-operator.md) ve [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md). Bu işleçler birini iki başvuru değişkeni aynı nesne örneğine başvuruyorsa belirlemek için kullanabilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#65)]  
  
 Önceki örnekte `x Is y` değerlendiren `True`, her iki değişken aynı örneğine bakın. Bu sonuç aşağıdaki örnek ile karşılaştırın.  
  
 [!code-vb[VbVbalrOperators#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#66)]  
  
 Önceki örnekte `x Is y` değerlendiren `False`, değişkenler aynı türde nesnelere atıfta olsa da, bunlar türü farklı örneklere bakın.  
  
 İki nesnenin aynı örneğine işaret eden değil için test etmek istediğiniz zaman `IsNot` işleci bakımından biçimsiz birleşimi önlemenize olanak tanır `Not` ve `Is`. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#67)]  
  
 Önceki örnekte `If a IsNot b` eşdeğerdir `If Not a Is b`.  
  
### <a name="comparing-object-type"></a>Nesne türü karşılaştırma  
 İle belirli bir türdeki bir nesne olup olmadığını test edebilirsiniz `TypeOf`... `Is` ifade. Söz dizimi aşağıdaki gibidir:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Zaman `typename` bir arabirim türü belirtir sonra `TypeOf`... `Is` ifade döndürür `True` nesne arabirimi uyguluyorsa. Zaman `typename` ifade döndürür sonra bir sınıf türüdür `True` nesnenin belirtilen sınıfın veya belirtilen sınıfından türetilen bir sınıfın bir örneği ise. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#68)]  
  
 Önceki örnekte `TypeOf x Is Control` ifadeyi hesaplar için `True` çünkü türünü `x` olduğu `Button`, işlevinden devralan `Control`.  
  
 Daha fazla bilgi için [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Değer Karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Karşılaştırma İşleçleri](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [İşleçler](../../../../visual-basic/language-reference/operators/index.md)
- [Visual Basic'de aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic'de birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
- [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
