---
description: ': = Işleci hakkında daha fazla bilgi edinin (Visual Basic)'
title: = İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 3cf45fb93bf5138f9e7fa5a43650019ab58674fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774258"
---
# <a name="-operator-visual-basic"></a>= İşleci (Visual Basic)

Bir değişkene veya özelliğe bir değer atar.  
  
## <a name="syntax"></a>Syntax  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a>Bölümler  

 `variableorproperty`  
 Herhangi bir yazılabilir değişken veya herhangi bir özellik.  
  
 `value`  
 Herhangi bir sabit değer, sabit veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  

 Eşittir işaretinin () sol tarafındaki öğesi `=` basit bir skaler değişken, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik [ReadOnly](../modifiers/readonly.md)olamaz. `=`İşleci değeri, sol tarafında bulunan değişkene veya özelliğe doğru değerini atar.  
  
> [!NOTE]
> `=`İşleci bir karşılaştırma işleci olarak da kullanılır. Ayrıntılar için bkz. [karşılaştırma işleçleri](comparison-operators.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  

 `=`İşleci, atama işleci olarak değil yalnızca ilişkisel karşılaştırma işleci olarak aşırı yüklenebilir. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, atama işlecini gösterir. Sağdaki değer soldaki değişkene atanır.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [&= Işleci](and-assignment-operator.md)
- [* = İşleci](multiplication-assignment-operator.md)
- [+ = İşleci](addition-assignment-operator.md)
- [-= İşleci (Visual Basic)](subtraction-assignment-operator.md)
- [/= İşleci (Visual Basic)](floating-point-division-assignment-operator.md)
- [\\= İşleci](integer-division-assignment-operator.md)
- [^ = İşleci](exponentiation-assignment-operator.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
- [Karşılaştırma Işleçleri](comparison-operators.md)
- [Özelliğinin](../modifiers/readonly.md)
- [Yerel Tür Arabirimi](../../programming-guide/language-features/variables/local-type-inference.md)
