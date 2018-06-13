---
title: '&amp; İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: 28d8cdb22974d77edf055ab9b2c6c767872e6783
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604308"
---
# <a name="amp-operator-visual-basic"></a>&amp; İşleci (Visual Basic)
İki ifadenin dize birleştirmesini oluşturur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tüm `String` veya `Object` değişkeni.  
  
 `expression1`  
 Gerekli. İçin widens bir veri türüne sahip herhangi bir ifade `String`.  
  
 `expression2`  
 Gerekli. İçin widens bir veri türüne sahip herhangi bir ifade `String`.  
  
## <a name="remarks"></a>Açıklamalar  
 Veri türü `expression1` veya `expression2` değil `String` ancak için widens `String`, dönüştürülmeden `String`. Veri türlerinden birini değil genişletmek için `String`, derleyici bir hata oluşturur.  
  
 Veri türü `result` olan `String`. İçin bir veya iki ifade değerlendirin varsa [hiçbir şey](../../../visual-basic/language-reference/nothing.md) veya değerine sahip <xref:System.DBNull.Value?displayProperty=nameWithType>, değerini bir dize olarak kabul edilir "".  
  
> [!NOTE]
>  `&` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
>  (&) Karakteri de değişkenleri türü olarak tanımlamak için kullanılabilir `Long`. Daha fazla bilgi için bkz: [türü karakterleri](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Örnek  
 Bu örnekte `&` dize birleştirme zorlamak için işleci. Sonuç, iki dize işlenenleri birleşimini temsil eden bir dize değeridir.  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [&= İşleci](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de birleştirme işleçleri](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
