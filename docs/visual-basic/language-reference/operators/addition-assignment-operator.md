---
title: += İşleci (Visual Basic)
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
ms.openlocfilehash: 249a19abfb08677c01ac4cc484d049a7ed1a983c
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591643"
---
# <a name="-operator-visual-basic"></a>+= İşleci (Visual Basic)
Sayısal bir ifadenin değerini bir sayısal değişkenin veya özelliğin değerine ekler ve sonucu değişkenine veya özelliğe atar. , Bir `String` ifadesini `String` değişkenine veya özelliğine birleştirmek ve sonucu değişkenine veya özelliğe atamak için de kullanılabilir.  
  
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
 @No__t-0 işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.  
  
 @No__t-0 işleci, solundaki değeri, sol taraftaki değişkene veya özelliğe ekler ve sonucu, sol tarafındaki değişkene veya özelliğe atar. @No__t-0 işleci Ayrıca, `String` ifadesini sağdaki `String` değişkenine veya özelliğine birleştirmek için de kullanılabilir ve sonucu, sol tarafında bulunan değişkene veya özelliğe atar.  
  
> [!NOTE]
> @No__t-0 işlecini kullandığınızda, ekleme veya dize birleştirme işleminin yapılıp yapılmayacağını belirleyemeyebilirsiniz. Belirsizliği ortadan kaldırmak ve kendi kendine belgeleme kodu sağlamak için, birleştirmek üzere `&=` işlecini kullanın.  
  
 Bu atama işleci, derleme ortamı katı semantiği zorlarsa, örtülü olarak genişleyen ancak daraltma dönüştürmesi gerçekleştirmez. Bu dönüşümler hakkında daha fazla bilgi için bkz. [genişletme ve daraltma dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). Katı ve izin veren semantiği hakkında daha fazla bilgi için bkz. [Option Strict deyimin](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
 İzin verilen semantiğe izin veriliyorsa `+=` işleci, `+` işleci tarafından gerçekleştirilmiş olanlarla özdeş olarak çeşitli dize ve sayısal dönüşümler gerçekleştirir. Bu dönüşümlerde Ayrıntılar için bkz. [+ işleci](../../../visual-basic/language-reference/operators/addition-operator.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 @No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. @No__t aşırı yükleme-0 işleci `+=` işlecinin davranışını etkiler. Kodunuz, `+` ' i aşırı yükleyen bir sınıf veya yapıda `+=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir değişkenin değerini diğeri ile birleştirmek için `+=` işlecini kullanır. İlk bölüm, bir değeri başka bir değer eklemek için sayısal değişkenlerle `+=` kullanır. İkinci bölüm, bir değeri başka bir değerle birleştirmek için `String` değişkenleriyle `+=` kullanır. Her iki durumda da sonuç ilk değişkene atanır.  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 @No__t-0 değeri artık 13 ' dir ve `str1` değeri artık "103".  
  
## <a name="see-also"></a>Ayrıca bkz.

- [+ İşleci](../../../visual-basic/language-reference/operators/addition-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Birleştirme İşleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
