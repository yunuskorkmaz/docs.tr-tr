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
ms.openlocfilehash: b4855e8270a329f9345339060a323b5ca9cd9792
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592183"
---
# <a name="-operator-visual-basic"></a>/= İşleci (Visual Basic)
Bir değişkenin veya özelliğin değerini bir ifadenin değerine böler ve kayan nokta sonucunu değişkenine veya özelliğe atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Herhangi bir sayısal değişken veya özellik.  
  
 `expression`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.  
  
 @No__t-0 işleci ilk olarak değişkenin değerini (işlecin sol tarafında), ifadenin değeri (işlecin sağ tarafında) ile ayırır (işlecin sağ tarafındaki). İşleci daha sonra bu işlemin kayan nokta sonucunu değişkenine veya özelliğe atar.  
  
 Bu ifade, soldaki değişkene veya özelliğe `Double` değeri atar. @No__t-0 `On` ise, `variableorproperty` `Double` olmalıdır. @No__t-0 `Off` ise, Visual Basic örtük bir dönüştürme gerçekleştirir ve elde edilen değeri, çalışma zamanında olası bir hatayla `variableorproperty` ' ye atar. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimdir](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. @No__t aşırı yükleme-0 işleci `/=` işlecinin davranışını etkiler. Kodunuz, `/` ' i aşırı yükleyen bir sınıf veya yapıda `/=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `Integer` değişkenini ikinci kez bölmek ve bölümü ilk değişkene atamak için `/=` işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\ = Işleci](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
