---
title: "Visual Basic'de Karşılaştırma İşleçleri"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d8bf37ad30f410251f18aea6747734fc24d42cd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="comparison-operators-in-visual-basic"></a>Visual Basic'de Karşılaştırma İşleçleri
Karşılaştırma işleçleri iki ifadeye karşılaştırır ve dönüş bir `Boolean` değerlerine ilişkiyi gösteren bir değer. Sayısal değerler, dizeleri Karşılaştırma işleçleri ve nesneleri Karşılaştırma işleçleri Karşılaştırma işleçleri vardır. Üç tür işleçleri burada açıklanmıştır.  
  
## <a name="comparing-numeric-values"></a>Sayısal değerleri karşılaştırma  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]altı sayısal Karşılaştırma işleçleri kullanarak sayısal değerleri karşılaştırır. Her işleç sayısal değerlere değerlendirmek iki ifadeye işlenen alır. Aşağıdaki tabloda işleçleri listeler ve her örnekler gösterir.  
  
|İşleç|Test durumu|Örnekler|  
|--------------|----------------------|--------------|  
|`=`(Eşitlik)|İlk ifade değerini ikinci değerine mi?|`23`   `=`   `33    ' False`<br /><br /> `23`   `=`   `23    ' True`<br /><br /> `23`   `=`   `12    ' False`|  
|`<>`(Eşitsizlik)|İlk ifade değeri ikinci değerine eşit mi?|`23`   `<>`   `33    ' True`<br /><br /> `23`   `<>`   `23    ' False`<br /><br /> `23`   `<>`   `12    ' True`|  
|`<`(Küçüktür)|İlk ifade değerden daha az saniye değerini mi?|`23`   `<`   `33    ' True`<br /><br /> `23`   `<`   `23    ' False`<br /><br /> `23`   `<`   `12    ' False`|  
|`>`(Büyük)|İlk ifade değeri ikinci değerinden büyük mü?|`23`   `>`   `33    ' False`<br /><br /> `23`   `>`   `23    ' False`<br /><br /> `23`   `>`   `12    ' True`|  
|`<=`(Küçük veya eşittir)|İlk ifade değeri ikinci değerine eşit veya daha az mi?|`23`   `<=`   `33    ' True`<br /><br /> `23`   `<=`   `23    ' True`<br /><br /> `23`   `<=`   `12    ' False`|  
|`>=`(Büyük veya eşittir)|İlk ifade değeri ikinci değerine eşit veya daha büyük mi?|`23`   `>=`   `33    ' False`<br /><br /> `23`   `>=`   `23    ' True`<br /><br /> `23`   `>=`   `12    ' True`|  
  
## <a name="comparing-strings"></a>Dizeleri Karşılaştırma  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]kullanarak dizeleri karşılaştırır [gibi işleci](../../../../visual-basic/language-reference/operators/like-operator.md) sayısal Karşılaştırma işleçleri yanı sıra. `Like` İşleci bir desen belirtmenize olanak verir. Dize desenini karşı karşılaştırılır ve eşleşirse sonucudur `True`. Aksi takdirde, sonuç değer `False`. Sayısal işleçleri, karşılaştırmanızı sağlar `String` değerler aşağıdaki örnekte gösterildiği gibi sıralama düzeni üzerinde temel.  
  
 `"73" < "9"`  
  
 `' The result of the preceding comparison is True.`  
  
 Önceki örnekte sonuç `True` ikinci dizedeki ilk karakter önce ilk dizedeki ilk karakter sıralar olduğundan. İlk karakteri eşit olsaydı, karşılaştırma iki dize sonraki karakteri devam ve benzeri. Ayrıca aşağıdaki örnekte gösterildiği gibi eşitlik işleci kullanarak dizeleri eşitlik test edebilirsiniz.  
  
 `"734" = "734"`  
  
 `' The result of the preceding comparison is True.`  
  
 Başka bir önek "aa" ve "aaa" gibi bir dize ise, uzun dizeyi kısa dize büyük olması kabul edilir. Aşağıdaki örnek bunu göstermektedir.  
  
 `"aaa" > "aa"`  
  
 `' The result of the preceding comparison is True.`  
  
 İkili karşılaştırma ya da bir metinsel karşılaştırma ayarını bağlı olarak sıralama düzenini temel `Option Compare`. Daha fazla bilgi için bkz: [Option Compare deyimi](../../../../visual-basic/language-reference/statements/option-compare-statement.md).  
  
## <a name="comparing-objects"></a>Nesneleri karşılaştırma  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]karşılaştırır iki nesne başvuru değişkenlerle [Is işlecini](../../../../visual-basic/language-reference/operators/is-operator.md) ve [IsNot işleci](../../../../visual-basic/language-reference/operators/isnot-operator.md). Aynı nesne örneğini iki başvuru değişkenleri başvurduğundan belirlemek için bu işleçlere birini kullanabilirsiniz. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#65](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_1.vb)]  
  
 Önceki örnekte `x Is y` değerlendiren `True`, her iki değişken aynı örneğine bakın. Aşağıdaki örnekte bu sonuçla karşılaştırın.  
  
 [!code-vb[VbVbalrOperators#66](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_2.vb)]  
  
 Önceki örnekte `x Is y` değerlendiren `False`, değişkenleri aynı türde nesnelere atıfta karşın, bu tür farklı örneklerine başvurduğundan.  
  
 İki nesnenin aynı örneğine işaret değil için test etmek istediğiniz zaman `IsNot` işleci dilbilgisi açısından biçimsiz bileşimini kaçının olanak tanır `Not` ve `Is`. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#67](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_3.vb)]  
  
 Önceki örnekte `If a IsNot b` eşdeğerdir `If Not a Is b`.  
  
### <a name="comparing-object-type"></a>Nesne türü karşılaştırma  
 İle belirli bir türdeki bir nesne olup olmadığını sınayabilirsiniz `TypeOf`... `Is` ifade. Söz dizimi aşağıdaki gibidir:  
  
 `TypeOf <objectexpression> Is <typename>`  
  
 Zaman `typename` bir arabirim türü belirtir sonra `TypeOf`... `Is` ifadesi döndürür `True` nesne arabirim türü uyguluyorsa. Zaman `typename` ifade döndürür sonra bir sınıf türü olan `True` nesne örneğini belirtilen sınıf veya belirtilen sınıfından türeyen bir sınıf ise. Aşağıdaki örnek bunu göstermektedir.  
  
 [!code-vb[VbVbalrOperators#68](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/comparison-operators_4.vb)]  
  
 Önceki örnekte `TypeOf x Is Control` ifadeyi hesaplar için `True` çünkü türünü `x` olan `Button`, devralan `Control`.  
  
 Daha fazla bilgi için bkz: [TypeOf işleci](../../../../visual-basic/language-reference/operators/typeof-operator.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Değer karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)  
 [Karşılaştırma işleçleri](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [İşleçler](../../../../visual-basic/language-reference/operators/index.md)  
 [Visual Basic'de aritmetik işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Visual Basic'de birleştirme işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)  
 [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
