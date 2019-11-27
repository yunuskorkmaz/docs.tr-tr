---
title: /= İşleci
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
ms.openlocfilehash: a8a031e968df90496a4e263ae78d47045ccdc923
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331043"
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
 `/=` işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.  
  
 `/=` işleci, ilk olarak değişkenin değerini (işlecin sol tarafında), ifadenin değeri (işlecin sağ tarafında) ile ayırır. İşleci daha sonra bu işlemin kayan nokta sonucunu değişkenine veya özelliğe atar.  
  
 Bu ifade, soldaki değişkene veya özelliğe bir `Double` değeri atar. `Option Strict` `On`, `variableorproperty` bir `Double`olmalıdır. `Option Strict` `Off`, Visual Basic örtük bir dönüştürme gerçekleştirir ve sonuçta elde edilen değeri, çalışma zamanında olası bir hatayla `variableorproperty`atar. Daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) ve [Option Strict deyimdir](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `/` işleci aşırı yükleme `/=` işlecinin davranışını etkiler. Kodunuz, `/`aşırı yükleyen bir sınıf veya yapı üzerinde `/=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `Integer` değişkenini ikinci bir kez bölmek ve bölümü ilk değişkene atamak için `/=` işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [/İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\= Işleci](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
