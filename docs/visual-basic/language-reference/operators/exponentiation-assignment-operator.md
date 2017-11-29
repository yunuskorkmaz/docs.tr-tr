---
title: "^= İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9d87d2f090a8c18aaab742e73878c7b80f55c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>^= İşleci (Visual Basic)
Bir değişken ya da ifade gücüne özellik değerini başlatır ve değişken veya özelliği için sonuç atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Tüm sayısal değişken veya özellik.  
  
 `expression`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe sol tarafındaki `^=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `^=` İşleci ilk başlatır değişken veya özellik (sol taraftaki işlecinin) değeri (sağ taraftaki işlecinin) ifadesinin değerini güç için. İşleci, daha sonra değişken veya özellik için bu işlemin sonucu olarak atar.  
  
 Visual Basic her zaman içinde üs gerçekleştirir [Double veri türü](../../../visual-basic/language-reference/data-types/double-data-type.md). Tüm farklı türündeki işlenenler için dönüştürülür `Double`, ve sonucu her zaman `Double`.  
  
 Değeri `expression` kesir olabilir negatif veya her ikisi de.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [^ İşleci](../../../visual-basic/language-reference/operators/exponentiation-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `^` işleci davranışını etkileyen `^=` işleci. Kodunuzu kullanıyorsa `^=` bir sınıf veya overloads yapısı `^`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `^=` bir değeri yükseltmek için işleci `Integer` ikinci bir değişken ve ata ilk değişkenin sonucu gücünü değişken.  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [^ İşleci](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Aritmetik işleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Deyimleri](../../../visual-basic/programming-guide/language-features/statements.md)
