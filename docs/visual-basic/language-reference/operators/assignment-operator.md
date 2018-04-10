---
title: = İşleci (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 230005640b2b494e5413b14ba13a7cb82ee9f22b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>= İşleci (Visual Basic)
Bir değişkenin veya özelliğin değeri atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Herhangi bir yazılabilir değişken veya herhangi bir özellik.  
  
 `value`  
 Herhangi değişmez değeri, sabit değer veya ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Eşittir işaretinden sol tarafındaki öğesi (`=`) basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md). `=` İşleci değişken, sağdaki değeri veya özelliği, sol taraftaki atar.  
  
> [!NOTE]
>  `=` İşleci bir karşılaştırma işleci da kullanılır. Ayrıntılar için bkz [Karşılaştırma işleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `=` Yalnızca bir ilişkisel karşılaştırma işleci olarak değil olarak atama işleci işleci aşırı yüklenmiş olabilir. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, atama işleci gösterir. Sağdaki değeri, sol taraftaki değişkene atanır.  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [& = işleci](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [* = İşleci](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [+= İşleci](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [-= İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)  
 [/ = İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\\= İşleci](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [^ = İşleci](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Deyimleri](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Karşılaştırma işleçleri](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Yerel tür çıkarımı](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
