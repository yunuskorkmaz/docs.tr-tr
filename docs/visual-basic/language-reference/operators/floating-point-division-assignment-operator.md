---
title: /= İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: 642307bc531e7d9ce21a932b112795b35e7b3182
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604100"
---
# <a name="-operator-visual-basic"></a>/= İşleci (Visual Basic)
Bir değişken ya da özellik değeri bir ifadenin değerini tarafından böler ve kayan noktalı bir sonuç değişken ya da özelliğin atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Tüm sayısal değişken veya özellik.  
  
 `expression`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe sol tarafındaki `/=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `/=` İşleci ilk böler değişkeni veya (sol taraftaki işlecinin) özellik değerini (sağ taraftaki işlecinin) ifadesinin değerini tarafından. İşleci kayan nokta işlemin sonucu olarak, değişken veya özellik sonra atar.  
  
 Bu ifade atar bir `Double` değişken ya da sol taraftaki özelliğin değeri. Varsa `Option Strict` olan `On`, `variableorproperty` olmalıdır bir `Double`. Varsa `Option Strict` olan `Off`, Visual Basic örtük bir dönüştürme gerçekleştirir ve çıkan değeri atar `variableorproperty`, çalışma zamanında olası hata. Daha fazla bilgi için bkz: [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `/` işleci davranışını etkileyen `/=` işleci. Kodunuzu kullanıyorsa `/=` bir sınıf veya overloads yapısı `/`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `/=` bir bölme işleci `Integer` değişken ikinci ve sayının ilk değişkenine atayın.  
  
 [!code-vb[VbVbalrOperators#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/floating-point-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)  
 [\\= İşleci](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
