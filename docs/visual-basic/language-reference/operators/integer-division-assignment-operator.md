---
title: "\\=İşleci"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ba74f7a433687b306e8b4273f3a2a6d60583396
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator"></a>\\= İşleci
Bir değişken ya da özellik değeri bir ifadenin değerini tarafından böler ve tamsayı sonuç değişken ya da özelliğin atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Tüm sayısal değişken veya özellik.  
  
 `expression`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe sol tarafındaki `\=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `\=` İşleci bir değişken ya da kendi soldaki özellik değeri, sağdaki değeriyle böler ve tamsayı sonuç değişkenin veya özelliğin, sol taraftaki atar  
  
 Tamsayı bölme hakkında daha fazla bilgi için bkz: [\ işleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `\` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `\` işleci davranışını etkileyen `\=` işleci. Kodunuzu kullanıyorsa `\=` bir sınıf veya overloads yapısı `\`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `\=` bir bölme işleci `Integer` değişken ikinci ve tamsayı sonuç ilk değişkenine atayın.  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\ İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [/ = İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Aritmetik işleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Deyimleri](../../../visual-basic/programming-guide/language-features/statements.md)
