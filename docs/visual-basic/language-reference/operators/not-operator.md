---
title: Not İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 29e2b159e4c6261a62e788b537102b9b457fe0c8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69955831"
---
# <a name="not-operator-visual-basic"></a>Not İşleci (Visual Basic)
Bir `Boolean` ifadede mantıksal Olumsuzlaştırma veya sayısal ifadede bit tabanlı Olumsuzlaştırma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Herhangi `Boolean` bir veya sayısal ifade.  
  
 `expression`  
 Gerekli. Herhangi `Boolean` bir veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 İfadeler `Boolean` için aşağıdaki tabloda nasıl `result` belirlendiği gösterilmektedir.  
  
|`expression` İse|Öğesinin `result` değeri|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Sayısal ifadeler `Not` için işleç, herhangi bir sayısal ifadenin bit değerlerini tersine çevirir ve karşılık gelen `result` biti aşağıdaki tabloya göre ayarlar.  
  
|Eğer bit `expression` ise|İçindeki `result` bit|  
|-------------------------------|----------------------------|  
|1\.|0|  
|0|1\.|  
  
> [!NOTE]
> Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçlerden daha düşük önceliğe sahip olduğundan, doğru yürütmeyi sağlamak için herhangi bir bit düzeyinde işlemin parantez içine alınması gerekir.  
  
## <a name="data-types"></a>Veri Türleri  
 Boolean Olumsuzlaştırma için sonucun veri türü olur `Boolean`. Bit düzeyinde olumsuzlama için sonuç veri türü, ile `expression`aynıdır. Ancak, ifadesi `Decimal`ise sonuç olur `Long`.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 İşleç aşırı yüklenebilir, yani işleneni Bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `Not` Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `Not` `Boolean` ifadede mantıksal olumsuzlama gerçekleştirmek için işlecini kullanır. Sonuç, ifadenin değerinin `Boolean` ters çevrilme değerini temsil eden bir değerdir.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 Yukarıdaki örnek sırasıyla `False` ve `True`, sonuçları üretir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir sayısal `Not` ifadenin ayrı bitlerinin mantıksal olumsuzunu gerçekleştirmek için işlecini kullanır. Sonuç deseninin biti, işaret biti dahil olmak üzere işlenen deseninin karşılık gelen bitin ters olarak ayarlanır.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 Yukarıdaki örnek sırasıyla – 11, – 9 ve – 7 sonuçlarını üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
