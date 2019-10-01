---
title: Or İşleci (Visual Basic)
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
ms.openlocfilehash: 03decb4ad32e8ff2c03e3b64a272bce779282973
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701234"
---
# <a name="or-operator-visual-basic"></a>Or İşleci (Visual Basic)
İki `Boolean` ifadelerinde mantıksal bir ayırma veya iki sayısal ifadeye bit tabanlı bir ayırıcı uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade. @No__t-0 karşılaştırması için, `result` iki `Boolean` değerinin kapsamlı mantıksal bir birleşimdir. Bit düzeyinde işlemler için `result`, iki sayısal bit desenlerinin kapsamlı bit düzeyinde bir ilişkisini temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade.  
  
 `expression2`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t 0 karşılaştırması için, `result` `False` ' dir ve yalnızca hem `expression1` hem de `expression2` `False` olarak değerlendirilir. Aşağıdaki tabloda `result` ' ın nasıl belirlendiği gösterilmektedir.  
  
|@No__t-0 ise|Ve `expression2`|@No__t-0 değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> @No__t-0 karşılaştırmasına `Or` işleci her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir. [OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md) *kısa*devre uygular, yani `expression1` `True` ise `expression2` değerlendirilmez.  
  
 Bit düzeyinde işlemler için `Or` işleci iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve `result` ' de karşılık gelen biti aşağıdaki tabloya göre ayarlar.  
  
|Bit `expression1` ise|Ve bit `expression2` ' dır|@No__t-0 ' daki bit|  
|--------------------------------|---------------------------------|----------------------------|  
|1\.|1\.|1\.|  
|1\.|0|1\.|  
|0|1\.|1\.|  
|0|0|0|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenenler bir `Boolean` ifadesinde ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadesini sayısal bir değere dönüştürür (-1 `True` ve `False` için 0) ve bit düzeyinde bir işlem gerçekleştirir.  
  
 @No__t 0 karşılaştırması için sonucun veri türü `Boolean` ' dir. Bit düzeyinde karşılaştırma için sonuç veri türü, `expression1` ve `expression2` veri türleri için uygun sayısal bir türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 @No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki ifadeye kapsamlı bir mantıksal ayırıcı gerçekleştirmek için `Or` işlecini kullanır. Sonuç, iki ifadeden birinin `True` olup olmadığını temsil eden bir `Boolean` değeridir.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Yukarıdaki örnek sırasıyla `True`, `True` ve `False` sonuçları üretir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki sayısal ifadenin tek bir bit üzerinde kapsamlı mantıksal ayırıcı gerçekleştirmek için `Or` işlecini kullanır. Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin biri 1 olarak ayarlandıysa ayarlanır.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 Yukarıdaki örnek sırasıyla 10, 14 ve 14 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse İşleci](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
