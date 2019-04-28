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
ms.openlocfilehash: ad74e3ebc947af4f36022be838b69df6ce24997a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61608286"
---
# <a name="-operator-visual-basic"></a>= İşleci (Visual Basic)
Bir değişken veya özellik için bir değer atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Herhangi bir yazılabilir değişkeni veya herhangi bir özelliği.  
  
 `value`  
 Tüm değişmez değeri, sabit veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Eşittir işaretinin sol tarafındaki öğesi (`=`) basit bir skaler değişkeni, bir özellik veya dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md). `=` İşleci sağındakiyle değişkenine değer veya özelliği, sol taraftaki atar.  
  
> [!NOTE]
>  `=` İşleci bir karşılaştırma işleci da kullanılır. Ayrıntılar için bkz [Karşılaştırma işleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `=` İlişkisel karşılaştırma işleci olarak yalnızca, bir atama işleci olarak değil işleci aşırı yüklenmiş olabilir. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, atama işlecini gösterir. Sağdaki değerin sol değişkenine atanır.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [&= İşleci](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= İşleci](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= İşleci](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/ = İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\= İşleci](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= İşleci](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
- [Karşılaştırma İşleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Yerel Çıkarım](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
