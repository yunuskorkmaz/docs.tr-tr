---
title: Or İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.Or
helpviewer_keywords:
- Or operator [Visual Basic]
- operators [Visual Basic], bitwise
- inclusive Or operator [Visual Basic]
- bitwise operators [Visual Basic], OR operator
- Or keyword [Visual Basic]
- operators [Visual Basic], inclusive or
- operators [Visual Basic], disjunction
- bitwise comparison [Visual Basic]
- logical disjunction
- disjunction operator [Visual Basic]
ms.assetid: 41ed6905-bf3d-468a-9e3b-03c10d461891
ms.openlocfilehash: 8f28026b526c29a6122725b2689e53b7f6ee7327
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348248"
---
# <a name="or-operator-visual-basic"></a>Or İşleci (Visual Basic)
İki `Boolean` ifadelerinde mantıksal bir ayırıcı ya da iki sayısal ifadeye bit düzeyinde ayırıcı uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade. `Boolean` karşılaştırma için, `result` iki `Boolean` değerin kapsamlı mantıksal bir birleşimi olur. Bit düzeyinde işlemler için `result`, iki sayısal bit desenlerinin kapsamlı bit düzeyinde debirleşimin temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade.  
  
 `expression2`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Boolean` karşılaştırma için `result` `False` ve yalnızca hem `expression1` hem de `expression2` `False`olarak değerlendirilir. Aşağıdaki tabloda `result` nasıl belirlendiği gösterilmektedir.  
  
|`expression1`|Ve `expression2`|`result` değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> `Boolean` bir karşılaştırmayla `Or` işleci her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir. [OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md) *kısa*devre uygular. Bu, `expression1` `True`, `expression2` değerlendirilmediği anlamına gelir.  
  
 Bit düzeyinde işlemler için `Or` işleci, iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve aşağıdaki tabloya göre `result` karşılık gelen biti ayarlar.  
  
|`expression1` bit ise|Ve `expression2` bit|`result` bit|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|1|  
|0|1|1|  
|0|0|0|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadesini sayısal bir değere dönüştürür (`True` için – 1 ve `False`için 0) ve bit düzeyinde bir işlem gerçekleştirir.  
  
 `Boolean` karşılaştırma için sonucun veri türü `Boolean`. Bit düzeyinde karşılaştırma için, sonuç veri türü `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Or` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki ifadeye kapsamlı bir mantıksal ayırıcı gerçekleştirmek için `Or` işlecini kullanır. Sonuç, iki deyimden birinin `True`olup olmadığını temsil eden bir `Boolean` değeridir.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Yukarıdaki örnek, sırasıyla `True`, `True`ve `False`sonuçları üretir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki sayısal ifadenin tek bir bit biti üzerinde kapsamlı mantıksal ayırıcı gerçekleştirmek için `Or` işlecini kullanır. Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin biri 1 olarak ayarlandıysa ayarlanır.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 Yukarıdaki örnek sırasıyla 10, 14 ve 14 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse İşleci](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
