---
title: '>>= İşleci'
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
ms.openlocfilehash: cad021c7730782d6233c60841483df7173308dc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351989"
---
# <a name="-operator-visual-basic"></a>> > = Işleci (Visual Basic)
Bir değişkenin veya özelliğin değerinde aritmetik sağa kaydırma gerçekleştirir ve sonucu değişkenine veya özelliğe geri atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. İntegral türünün değişkeni veya özelliği (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`veya `ULong`).  
  
 `amount`  
 Gerekli. `Integer`için widens bir veri türünün sayısal ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 `>>=` işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.  
  
 `>>=` işleci ilk olarak değişkenin veya özelliğin değerinde bir aritmetik sağa kaydırma gerçekleştirir. İşleci daha sonra bu işlemin sonucunu değişkenine veya özelliğe geri atar.  
  
 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Aritmetik sağa kaydırma ' de, en sağdaki bit konumlarından daha fazla kaydırılan bitler atılır ve en soldaki bit, sol taraftaki bit konumlarına yayılır. Bu, `variableorproperty` negatif bir değer içeriyorsa, vakatılmış konumların bir olarak ayarlanmasıdır. `variableorproperty` pozitifse veya veri türü işaretsiz bir tür ise, karıştırılmış konumlar sıfır olarak ayarlanır.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [> > işleci](../../../visual-basic/language-reference/operators/right-shift-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `>>` işleci aşırı yükleme `>>=` işlecinin davranışını etkiler. Kodunuz, `>>`aşırı yükleyen bir sınıf veya yapı üzerinde `>>=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
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
