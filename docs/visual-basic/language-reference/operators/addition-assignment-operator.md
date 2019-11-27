---
title: += İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: 31a6da163061b905b8ffddcfc4b44978f5cdd55e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350302"
---
# <a name="-operator-visual-basic"></a>+= İşleci (Visual Basic)
Sayısal bir ifadenin değerini bir sayısal değişkenin veya özelliğin değerine ekler ve sonucu değişkenine veya özelliğe atar. Ayrıca, bir `String` ifadesini `String` değişkenine veya özelliğe birleştirmek ve sonucu değişkenine veya özelliğe atamak için de kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Herhangi bir sayısal veya `String` değişken veya özellik.  
  
 `expression`  
 Gerekli. Herhangi bir sayısal veya `String` ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 `+=` işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.  
  
 `+=` işleci, solundaki değeri, sol taraftaki değişkene veya özelliğe ekler ve sonucu sol taraftaki değişkene veya özelliğe atar. `+=` işleci Ayrıca, sol tarafında bulunan `String` değişkeni veya özelliği için `String` ifadesini birleştirmek için de kullanılabilir ve sonucu, sol tarafında bulunan değişkene veya özelliğe atar.  
  
> [!NOTE]
> `+=` işlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz. Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için, birleştirme için `&=` işlecini kullanın.  
  
 Bu atama işleci, derleme ortamı katı semantiği zorlarsa, örtülü olarak genişleyen ancak daraltma dönüştürmesi gerçekleştirmez. Bu dönüşümler hakkında daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Katı ve izin veren semantiği hakkında daha fazla bilgi için bkz. [Option Strict deyimin](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 İzin verilen semantiğe izin veriliyorsa, `+=` işleci, `+` işleci tarafından gerçekleştirilmiş olanlarla özdeş olarak çeşitli dize ve sayısal dönüşümler gerçekleştirir. Bu dönüşümlerde Ayrıntılar için bkz. [+ işleci](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `+` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `+` işleci aşırı yükleme `+=` işlecinin davranışını etkiler. Kodunuz, `+`aşırı yükleyen bir sınıf veya yapı üzerinde `+=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir değişkenin değerini diğeri ile birleştirmek için `+=` işlecini kullanır. İlk bölüm, bir değeri başka bir değer eklemek için sayısal değişkenlerle birlikte `+=` kullanır. İkinci bölüm, bir değeri başka bir değerle birleştirmek için `String` değişkenlerle `+=` kullanır. Her iki durumda da sonuç ilk değişkene atanır.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 `num1` değeri artık 13 ' dir ve `str1` değeri artık "103".  
  
## <a name="see-also"></a>Ayrıca bkz.

- [+ İşleci](../../../visual-basic/language-reference/operators/addition-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
