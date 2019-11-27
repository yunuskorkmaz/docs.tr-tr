---
title: <<= İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: cc89e0dadc7148b21e695a53a2e746a00ed66441
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350951"
---
# <a name="-operator-visual-basic"></a>\<\<= Işleci (Visual Basic)
Bir değişkenin veya özelliğin değerinde aritmetik sola kaydırma gerçekleştirir ve sonucu değişkenine veya özelliğe geri atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. İntegral türünün değişkeni veya özelliği (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`veya `ULong`).  
  
 `amount`  
 Gerekli. `Integer`için widens bir veri türünün sayısal ifadesi.  
  
## <a name="remarks"></a>Açıklamalar  
 `<<=` işlecinin sol tarafındaki öğe basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz.  
  
 `<<=` işleci ilk olarak değişkenin veya özelliğin değerinde bir aritmetik sola kaydırma gerçekleştirir. İşleci daha sonra bu işlemin sonucunu bu değişkene veya özelliğe yeniden atar.  
  
 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [< < işleci](../../../visual-basic/language-reference/operators/left-shift-operator.md) *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `<<` işleci aşırı yükleme `<<=` işlecinin davranışını etkiler. Kodunuz, `<<`aşırı yükleyen bir sınıf veya yapı üzerinde `<<=` kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir `Integer` değişkeninin bit modelini belirtilen miktarda sola kaydırmak ve sonucu değişkenine atamak için `<<=` işlecini kullanır.  
  
 [!code-vb[VbVbalrOperators#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#13)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [<< İşleci](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Bit Kaydırma İşleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
