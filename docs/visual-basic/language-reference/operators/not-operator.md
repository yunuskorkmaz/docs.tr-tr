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
ms.openlocfilehash: 4e54fdca9123ad5595eb9a8c5e2ac5bc303a8f6a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936623"
---
# <a name="not-operator-visual-basic"></a>Not İşleci (Visual Basic)
Mantıksal değilleme gerçekleştiren bir `Boolean` ifadesi veya sayısal bir ifadenin bit tabanlı değil işlecini uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = Not expression  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
 `expression`  
 Gerekli. Tüm `Boolean` veya sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 İçin `Boolean` ifadeleri, aşağıdaki tabloda gösterilmiştir nasıl `result` belirlenir.  
  
|Varsa `expression` olduğu|Değerini `result` olduğu|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 Sayısal ifadeler için `Not` işleci herhangi bir sayısal ifadeye bit değerleri tersine çevirir ve karşılık gelen, bit ayarlar `result` aşağıdaki tabloya göre.  
  
|Varsa, bit `expression` olduğu|Bit `result` olduğu|  
|-------------------------------|----------------------------|  
|1.|0|  
|0|1.|  
  
> [!NOTE]
>  Mantıksal ve bit düzeyinde işleçler diğer aritmetik ve ilişkisel işleçler düşük önceliğe sahip olduğundan, herhangi bir bit düzeyinde işlemler doğru yürütme emin olmak için parantez içine alınmalıdır.  
  
## <a name="data-types"></a>Veri Türleri  
 Bir mantıksal olumsuzlama için sonuç verileri türüdür `Boolean`. Bit tabanlı değil işlecini için sonuç veri türü, aynı olduğu `expression`. Ancak, ifade ise `Decimal`, sonuç `Long`.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `Not` İşleci olabilir *aşırı*, kendi işleneninin türü, sınıfın veya yapının olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Not` gerçekleştirmeniz mantıksal olumsuzlama işleci bir `Boolean` ifade. Sonuç bir `Boolean` ifade değerinin ters gösteren bir değer.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 Yukarıdaki örnekte sonuçlarını üretir `False` ve `True`sırasıyla.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `Not` mantıksal olumsuzlaştırma tek bit sayısal ifadenin için işleci. Karşılık gelen bit imza biti dahil işlenen deseninde, geriye doğru sonuç deseninde bit ayarlanır.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 Yukarıdaki örnekte sırasıyla –11 –9 ve –7, sonuçları üretir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Mantıksal/bit düzeyinde işleçler (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic'de mantıksal ve bit düzeyinde işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
