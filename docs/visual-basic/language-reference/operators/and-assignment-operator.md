---
title: '&amp;= İşleci (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 929a9e8c3384451679fc52ad478eb03219d67192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="amp-operator-visual-basic"></a>&amp;= İşleci (Visual Basic)
Art arda ekler bir `String` ifade bir `String` değişken veya özellik ve değişken ya da özelliği için sonuç atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Tüm `String` değişken veya özellik.  
  
 `expression`  
 Gerekli. Tüm `String` ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe sol tarafındaki `&=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md). `&=` İşleci art arda ekler `String` ifadesi, sağ taraftaki `String` değişkenin veya özelliğin, sol taraftaki ve değişken ya da kendi soldaki özelliğin sonucu atar.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [& İşleci](../../../visual-basic/language-reference/operators/concatenation-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `&` işleci davranışını etkileyen `&=` işleci. Kodunuzu kullanıyorsa `&=` bir sınıf veya overloads yapısı `&`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `&=` iki birleştirme işleci `String` değişkenleri ve ata ilk değişken sonucu.  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [& İşleci](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [+= İşleci](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Birleştirme işleçleri](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Deyimleri](../../../visual-basic/programming-guide/language-features/statements.md)
