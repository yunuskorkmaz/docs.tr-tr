---
title: -= İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: 29a178ece41763dfdf9fe1ff042f419bc879dcd9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675060"
---
# <a name="--operator-visual-basic"></a>-= İşleci (Visual Basic)
Değerin bir ifade bir değişken veya özellik değerini çıkarır ve sonucu değişken veya özellik atar.  
  
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
 Öğe sol tarafındaki `-=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `-=` İşleci ilk çıkarır (işlecin sağ tarafındaki) ifade değeri değişken veya özellik (üzerinde işlecinin sol tarafı) değerinden. İşleci, bu işlemin sonucunu daha sonra değişken veya özellik atar.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [-İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `-` işleci davranışını etkileyen `-=` işleci. Kodunuzu kullanıyorsa `-=` bir sınıf veya aşırı yapısı `-`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `-=` biri çıkarılacak işleci `Integer` başka bir değişken ve sonucu ikinci değişkenine atayın.  
  
 [!code-vb[VbVbalrOperators#11](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [-İşleci (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
