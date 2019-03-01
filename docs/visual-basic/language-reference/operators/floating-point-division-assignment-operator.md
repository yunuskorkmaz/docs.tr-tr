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
ms.openlocfilehash: c8fb990533d9db90eacf76aff424ea3cf96b0875
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970525"
---
# <a name="-operator-visual-basic"></a>/= İşleci (Visual Basic)
Bir değişken veya özellik değeri tarafından bir ifadenin değerine böler ve kayan noktalı bir sonuç değişken veya özellik atar.  
  
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
 Öğe sol tarafındaki `/=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `/=` İşleci ilk ayırır değişken veya özellikte (işlecinin sol tarafı) değerini (işlecin sağ tarafındaki) ifadesinin değere göre. İşleci, kayan nokta, işlemin sonucunu daha sonra değişken veya özellik atar.  
  
 Bu bildirimi atar bir `Double` değişken ya da sol taraftaki özelliğin değeri. Varsa `Option Strict` olduğu `On`, `variableorproperty` olmalıdır bir `Double`. Varsa `Option Strict` olduğu `Off`, Visual Basic örtülü bir dönüştürme uygulayan ve çıkan değeri atar `variableorproperty`, çalışma zamanında olası bir hata ile. Daha fazla bilgi için [Widening ve daraltma dönüşümleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `/` işleci davranışını etkileyen `/=` işleci. Kodunuzu kullanıyorsa `/=` bir sınıf veya aşırı yapısı `/`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `/=` bir bölme işleci `Integer` değişkenini, saniye ve sayının ilk değişkenine atayın.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [/ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\= İşleci](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
