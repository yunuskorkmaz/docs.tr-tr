---
title: "&gt;&gt;= İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7e388471b9adf424c55b1ad1042e5aed1ea8ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;= İşleci (Visual Basic)
Bir değişkenin veya özelliğin değerini aritmetik sağa kaydırma gerçekleştirir ve değişken veya özelliği için sonuç atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Değişken ya da bir tam sayı türü özelliği (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).  
  
 `amount`  
 Gerekli. Sayısal ifade bir veri türündeki için widens `Integer`.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe sol tarafındaki `>>=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `>>=` İşleci değişken veya özellik değeri üzerinde ilk aritmetik sağa kaydırma gerçekleştirir. İşleci, daha sonra değişken veya özellik için bu işlemin sonucu olarak atar.  
  
 Aritmetik kaydırmalar sonucu ucunu gölgeye BITS diğer sonunda yeniden girmesini olmayan başka bir deyişle, döngüsel, değil. Aritmetik sağa kaydırma, en sağdaki bit konumu gölgeye BITS atılır ve soldaki bit solda vacated bit konumları içine yayılır. Bu olması durumunda gelir `variableorproperty` negatif bir değere sahip vacated konumlar için ayarlanır. Varsa `variableorproperty` pozitifse veya kendi veri türü imzasız bir tür ise, vacated konumlar sıfıra ayarlanır.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [>> İşleci](../../../visual-basic/language-reference/operators/right-shift-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `>>` işleci davranışını etkileyen `>>=` işleci. Kodunuzu kullanıyorsa `>>=` bir sınıf veya overloads yapısı `>>`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `>>=` bit desenini kaydırılacak işleci bir `Integer` değişken sağ tarafından belirtilen tutar ve ata değişkene sonucu.  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [>> İşleci](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Bit kaydırma işleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Deyimleri](../../../visual-basic/programming-guide/language-features/statements.md)
