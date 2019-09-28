---
title: = İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: ca4c519dd80c07f54dc1c3dfe70daf6948446363
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591834"
---
# <a name="-operator-visual-basic"></a>= İşleci (Visual Basic)
Bir değişkene veya özelliğe bir değer atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Herhangi bir yazılabilir değişken veya herhangi bir özellik.  
  
 `value`  
 Herhangi bir sabit değer, sabit veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Eşittir işaretinin (`=`) sol tarafındaki öğesi basit bir skaler değişken, özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz. @No__t-0 işleci, solundaki değeri sağ taraftaki değişkene veya özelliğe atar.  
  
> [!NOTE]
> @No__t-0 işleci bir karşılaştırma işleci olarak da kullanılır. Ayrıntılar için bkz. [karşılaştırma işleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 @No__t-0 işleci, atama işleci olarak değil yalnızca ilişkisel karşılaştırma işleci olarak aşırı yüklenebilir. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, atama işlecini gösterir. Sağdaki değer soldaki değişkene atanır.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [&= İşleci](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= İşleci](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= İşleci](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\ = Işleci](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= İşleci](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
- [Karşılaştırma İşleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
