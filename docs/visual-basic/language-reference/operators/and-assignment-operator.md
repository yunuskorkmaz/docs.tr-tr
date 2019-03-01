---
title: '&amp;= İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: fa009168be3781c727cd5a9cb6976b8c16fb2843
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967496"
---
# <a name="amp-operator-visual-basic"></a>&amp;= İşleci (Visual Basic)
Birleştiren bir `String` ifade bir `String` değişken veya özellik ve sonucu değişken veya özellik atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Tüm `String` değişken veya özellik.  
  
 `expression`  
 Gerekli. Tüm `String` ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe sol tarafındaki `&=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md). `&=` İşleci art arda ekler `String` sağındakiyle için ifade `String` değişken veya özellik, sol taraftaki ve sonucu bir değişken veya özellik, sol taraftaki atar.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [& İşleci](../../../visual-basic/language-reference/operators/concatenation-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `&` işleci davranışını etkileyen `&=` işleci. Kodunuzu kullanıyorsa `&=` bir sınıf veya aşırı yapısı `&`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `&=` işleci iki birleştirmek için `String` değişkenleri ve sonuç ilk değişkenine atayın.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [& İşleci](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [+= İşleci](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
