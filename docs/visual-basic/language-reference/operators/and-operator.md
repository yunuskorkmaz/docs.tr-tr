---
title: And İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.And
helpviewer_keywords:
- operators [Visual Basic], bitwise
- logical conjunction
- bitwise AND operator [Visual Basic]
- conjunction operator [Visual Basic]
- And operator [Visual Basic]
- bitwise operators [Visual Basic], AND operator
- operators [Visual Basic], conjunction
- bitwise comparison [Visual Basic]
ms.assetid: 2ea711f3-439a-4c7c-9e3a-1ffe3b0d6046
ms.openlocfilehash: a1802d3a7018b1b6190ff5601eba055e16e62371
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913166"
---
# <a name="and-operator-visual-basic"></a>And İşleci (Visual Basic)
İki `Boolean` ifadeye bir mantıksal birlikte veya iki sayısal ifadeye bit tabanlı bir birlikte uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi `Boolean` bir veya sayısal ifade. Boolean karşılaştırma `result` için iki `Boolean` değerden oluşan mantıksal bir değer. Bit düzeyinde işlemler için `result` , iki sayısal bit deseninin bit düzeyinde birlikte temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gerekli. Herhangi `Boolean` bir veya sayısal ifade.  
  
 `expression2`  
 Gerekli. Herhangi `Boolean` bir veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 `result` Boolean karşılaştırma `expression1` içinveyalnızca`True`her ikisi de olarak değerlendirilir.`expression2` `True` Aşağıdaki tabloda nasıl `result` belirlendiği gösterilmektedir.  
  
|`expression1` İse|Ve `expression2`|Öğesinin `result` değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Boole karşılaştırmasına, `And` işleç her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir. [AndAlso işleci de](../../../visual-basic/language-reference/operators/andalso-operator.md) *kısa* `expression1` devre `False`uygular, yani varsa, `expression2` değerlendirilmez.  
  
 Sayısal değerlere `And` uygulandığında operatör iki sayısal ifadede aynı şekilde `result` konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve karşılık gelen biti aşağıdaki tabloya göre ayarlar.  
  
|Eğer bit `expression1` ise|Ve bit `expression2` ,|İçindeki `result` bit|  
|--------------------------------|---------------------------------|----------------------------|  
|1\.|1\.|1\.|  
|1|0|0|  
|0|1\.|0|  
|0|0|0|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru sonuçları sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadeyi sayısal bir `True` değere dönüştürür (– `False`1 ve için 0) ve bit düzeyinde bir işlem gerçekleştirir.  
  
 Boolean karşılaştırma için sonucun veri türü olur `Boolean`. Bit düzeyinde karşılaştırma için, sonuç veri türü `expression1` ve `expression2`veri türleri için uygun sayısal bir türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.  
  
> [!NOTE]
> İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `And` Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki ifadeye `And` mantıksal bir birlikte gerçekleştirmek için işlecini kullanır. Sonuç, `Boolean` `True`ifadelerin her ikisinin de olup olmadığını temsil eden bir değerdir.  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 Yukarıdaki örnek sırasıyla `True` ve `False`, sonuçları üretir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki sayısal `And` ifadenin ayrı bitleri üzerinde mantıksal bir işlem gerçekleştirmek için işlecini kullanır. Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin her ikisi de 1 olarak ayarlandıysa ayarlanır.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 Yukarıdaki örnek sırasıyla 8, 2 ve 0 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso İşleci](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
