---
title: "-= İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 753e3efca311da9e09c67131969626ff59c130f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-visual-basic"></a>-= İşleci (Visual Basic)
Değerinden ifade bir değişken veya özellik değeri çıkarır ve değişken ya da özelliği için sonuç atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Tüm sayısal değişken veya özellik.  
  
 `expression`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe sol tarafındaki `-=` işleci basit bir skaler değişkeni, bir özellik veya bir dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `-=` İşleci ilk çıkarır (sağ taraftaki işlecinin) ifadesinin değerini değerinden değişkenin ya da özelliği (sol taraftaki işlecinin). İşleci değişken veya özelliği daha sonra işlemin sonucunu atar.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [-İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `-` işleci davranışını etkileyen `-=` işleci. Kodunuzu kullanıyorsa `-=` bir sınıf veya overloads yapısı `-`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `-=` bir çıkartılacak işleci `Integer` başka bir değişken ve ata ikinci değişken sonucu.  
  
 [!code-vb[VbVbalrOperators#11](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [-İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)  
 [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Aritmetik işleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Deyimleri](../../../visual-basic/programming-guide/language-features/statements.md)
