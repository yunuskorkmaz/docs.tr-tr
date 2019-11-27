---
title: And İşleci
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
ms.openlocfilehash: 78a65843a449bd15d5615710e1685f40d94c37f7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350249"
---
# <a name="and-operator-visual-basic"></a>And İşleci (Visual Basic)
İki `Boolean` ifadeye veya iki sayısal ifadeye bit düzeyinde bir birlikte mantıksal bir birlikte gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = expression1 And expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade. Boolean karşılaştırma için, iki `Boolean` değerinin mantıksal bir `result`. Bit düzeyinde işlemler için `result`, iki sayısal bit deseninin bit düzeyinde birlikte temsil eden sayısal bir değerdir.  
  
 `expression1`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade.  
  
 `expression2`  
 Gerekli. Herhangi bir `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Boolean karşılaştırma için, yalnızca hem `expression1` hem de `expression2` `True`olarak değerlendirip `result` `True`. Aşağıdaki tabloda `result` nasıl belirlendiği gösterilmektedir.  
  
|`expression1`|Ve `expression2`|`result` değeri|  
|-------------------------|--------------------------|------------------------------|  
|`True`|`True`|`True`|  
|`True`|`False`|`False`|  
|`False`|`True`|`False`|  
|`False`|`False`|`False`|  
  
> [!NOTE]
> Boole karşılaştırmasına `And` işleci her zaman her iki ifadeyi değerlendirir ve bu da yordam çağrıları yapmayı içerebilir. [AndAlso işleci de](../../../visual-basic/language-reference/operators/andalso-operator.md) *kısa*devre uygular, yani `expression1` `False`, `expression2` değerlendirilmez.  
  
 Sayısal değerlere uygulandığında `And` işleci iki sayısal ifadede aynı şekilde konumlandırılmış bitlerin bit düzeyinde karşılaştırmasını gerçekleştirir ve aşağıdaki tabloya göre `result` karşılık gelen biti ayarlar.  
  
|`expression1` bit ise|Ve `expression2` bit|`result` bit|  
|--------------------------------|---------------------------------|----------------------------|  
|1|1|1|  
|1|0|0|  
|0|1|0|  
|0|0|0|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru sonuçları sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
## <a name="data-types"></a>Veri Türleri  
 İşlenenler bir `Boolean` ifadeden ve bir sayısal ifadeden oluşur Visual Basic, `Boolean` ifadesini sayısal bir değere dönüştürür (`True` için – 1 ve `False`için 0) ve bit düzeyinde bir işlem gerçekleştirir.  
  
 Boolean karşılaştırma için sonucun veri türü `Boolean`. Bit düzeyinde karşılaştırma için, sonuç veri türü `expression1` ve `expression2`veri türleri için uygun bir sayısal türdür. [Işleç sonuçlarının veri türlerinde](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md)"Ilişkisel ve bit düzeyinde karşılaştırmalar" tablosuna bakın.  
  
> [!NOTE]
> `And` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki ifadeye mantıksal bir birlikte gerçekleştirmek için `And` işlecini kullanır. Sonuç, her iki ifadenin `True`olup olmadığını temsil eden bir `Boolean` değeridir.  
  
 [!code-vb[VbVbalrOperators#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#22)]  
  
 Yukarıdaki örnek, sırasıyla `True` ve `False`sonuçları üretir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, iki sayısal ifadenin ayrı bitleri üzerinde mantıksal bir işlem gerçekleştirmek için `And` işlecini kullanır. Sonuç düzenindeki bit, işlenenlerde karşılık gelen bitlerin her ikisi de 1 olarak ayarlandıysa ayarlanır.  
  
 [!code-vb[VbVbalrOperators#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#23)]  
  
 Yukarıdaki örnek sırasıyla 8, 2 ve 0 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [AndAlso İşleci](../../../visual-basic/language-reference/operators/andalso-operator.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
