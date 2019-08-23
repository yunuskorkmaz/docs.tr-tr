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
ms.openlocfilehash: 1d11a6d009f6ecfea9fb1a86b00c67b87d5555dc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955835"
---
# <a name="or-operator-visual-basic"></a>Or İşleci (Visual Basic)
İki `Boolean` ifadeye mantıksal bir ayırıcı ya da iki sayısal ifadeye bit düzeyinde ayırıcı uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = expression1 Or expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi `Boolean` bir veya sayısal ifade. Karşılaştırma için `Boolean` iki değerden`Boolean` oluşan kapsamlı mantıksal ayırıcı olur. `result` Bit düzeyinde işlemler `result` için iki sayısal bit deseninin kapsamlı bit düzeyinde debirleşimin temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gerekli. Herhangi `Boolean` bir veya sayısal ifade.  
  
 `expression2`  
 Gerekli. Herhangi `Boolean` bir veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `Boolean` `expression1` Karşılaştırma için`False`ve yalnızca her ikisi de olarak`False`değerlendirilir `expression2`. `result` Aşağıdaki tabloda nasıl `result` belirlendiği gösterilmektedir.  
  
|`expression1` İse|Ve `expression2`|Öğesinin `result` değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`True`|  
|`False`|`True`|`True`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Bir `Boolean` karşılaştırmada`Or` , işleç her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir. [OrElse işleci](../../../visual-basic/language-reference/operators/orelse-operator.md) *kısa* `expression1` devre uygular, yani ise `True` `expression2` , hesaplanmaz.  
  
 Bit düzeyinde işlemler için, `Or` işleç iki sayısal ifadede aynı şekilde `result` konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve karşılık gelen biti aşağıdaki tabloya göre ayarlar.  
  
|Eğer bit `expression1` ise|Ve bit `expression2` ,|İçindeki `result` bit|  
|--------------------------------|---------------------------------|----------------------------|  
|1\.|1\.|1\.|  
|1|0|1\.|  
|0|1\.|1|  
|0|0|0|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadeyi sayısal bir `True` değere dönüştürür (– `False`1 ve için 0) ve bit düzeyinde bir işlem gerçekleştirir.  
  
 Bir `Boolean` karşılaştırma için sonucun veri türü olur `Boolean`. Bit düzeyinde karşılaştırma için, sonuç veri türü `expression1` ve `expression2`veri türleri için uygun sayısal bir türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `Or` Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki ifadeye `Or` kapsamlı bir mantıksal ayırıcı gerçekleştirmek için işlecini kullanır. Sonuç, iki `Boolean` `True`deyimden birinin olup olmadığını temsil eden bir değerdir.  
  
 [!code-vb[VbVbalrOperators#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#35)]  
  
 Yukarıdaki örnek sırasıyla `True`, `True`, ve `False`sonuçlarını üretir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki sayısal `Or` ifadenin ayrı bitleri üzerinde kapsamlı mantıksal ayırıcı gerçekleştirmek için işlecini kullanır. Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin biri 1 olarak ayarlandıysa ayarlanır.  
  
 [!code-vb[VbVbalrOperators#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#36)]  
  
 Yukarıdaki örnek sırasıyla 10, 14 ve 14 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [OrElse İşleci](../../../visual-basic/language-reference/operators/orelse-operator.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
