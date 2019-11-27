---
title: '&amp;= Işleci'
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
ms.openlocfilehash: 8668bfcbf32bb34b422efe8116bbd12a2d80b1d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350261"
---
# <a name="amp-operator-visual-basic"></a>&amp;= Işleci (Visual Basic)
Bir `String` ifadesini `String` değişkenine veya özelliğe ekler ve sonucu değişkenine veya özelliğe atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Herhangi bir `String` değişkeni veya özelliği.  
  
 `expression`  
 Gerekli. Herhangi bir `String` ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 `&=` işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz. `&=` işleci, sol tarafında bulunan `String` değişkenine veya özelliğe sağ taraftaki `String` ifadesini birleştirir ve sonucu, sol tarafında bulunan değişkene veya özelliğe atar.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [& işleci](../../../visual-basic/language-reference/operators/concatenation-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `&` işleci aşırı yükleme `&=` işlecinin davranışını etkiler. Kodunuz, `&`aşırı yükleyen bir sınıf veya yapı üzerinde `&=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki `String` değişkeni birleştirmek ve sonucu ilk değişkene atamak için `&=` işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [& İşleci](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [+= İşleci](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
