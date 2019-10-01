---
title: '>>= İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: 08d4e251a96ca387a709319e752351db6825d9e8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701350"
---
# <a name="-operator-visual-basic"></a>> > = Işleci (Visual Basic)
Bir değişkenin veya özelliğin değerinde aritmetik sağa kaydırma gerçekleştirir ve sonucu değişkenine veya özelliğe geri atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. İntegral türünün değişkeni veya özelliği (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` veya `ULong`).  
  
 `amount`  
 Gerekli. @No__t-0 ' a widens bir veri türünün sayısal ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t-0 işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.  
  
 @No__t-0 işleci ilk olarak değişkenin veya özelliğin değerinde bir aritmetik sağa kaydırma gerçekleştirir. İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe geri atar.  
  
 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Aritmetik sağa kaydırma ' de, en sağdaki bit konumlarından daha fazla kaydırılan bitler atılır ve en soldaki bit, sol taraftaki bit konumlarına yayılır. Bu, `variableorproperty` negatif bir değer içeriyorsa, karıştırılmış konumların bir tane olarak ayarlanmasıdır. @No__t-0 pozitifse veya veri türü işaretsiz bir tür ise, karıştırılmış konumlar sıfır olarak ayarlanır.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [> > işleci](../../../visual-basic/language-reference/operators/right-shift-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. @No__t aşırı yükleme-0 işleci `>>=` işlecinin davranışını etkiler. Kodunuz, `>>` ' i aşırı yükleyen bir sınıf veya yapıda `>>=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `Integer` değişkeninin bit modelini belirtilen miktarda sağa kaydırmak ve sonucu değişkenine atamak için `>>=` işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [>> İşleci](../../../visual-basic/language-reference/operators/right-shift-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Bit Kaydırma İşleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
