---
title: = İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 75f303219b9bf32613989f65f90a9096ef70e02e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350198"
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
 Eşittir işaretinin (`=`) sol tarafındaki öğesi basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)olamaz. `=` işleci, solundaki değeri, sol tarafındaki değişkene veya özelliğe atar.  
  
> [!NOTE]
> `=` işleci bir karşılaştırma işleci olarak da kullanılır. Ayrıntılar için bkz. [karşılaştırma işleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `=` işleci, atama işleci olarak değil yalnızca ilişkisel karşılaştırma işleci olarak aşırı yüklenebilir. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, atama işlecini gösterir. Sağdaki değer soldaki değişkene atanır.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [&= İşleci](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= İşleci](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= İşleci](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\= Işleci](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= İşleci](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
- [Karşılaştırma İşleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
