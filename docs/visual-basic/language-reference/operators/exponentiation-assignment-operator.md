---
title: ^= İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: 73705df376284edd9d8f20baaf4306c41b1d3943
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54699733"
---
# <a name="-operator-visual-basic"></a>^= İşleci (Visual Basic)
Bir değişken veya özellik değerini bir ifade değeri oluşturur ve sonucu değişken veya özellik için atar.  
  
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
 Öğe sol tarafındaki `^=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `^=` İşleci ilk başlatır değişken veya özellik (üzerinde işlecinin sol tarafı) değerini gücüne (işlecin sağ tarafındaki) ifade değeri. İşleci, bu işlemin sonucunu daha sonra değişken veya özellik için atar.  
  
 Visual Basic içinde üs her zaman gerçekleştirir [Double veri türü](../../../visual-basic/language-reference/data-types/double-data-type.md). Tüm farklı türündeki işlenenler için dönüştürülür `Double`, ve sonucu her zaman `Double`.  
  
 Değerini `expression` kesir olabilir negatif veya her ikisini de.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [^ İşleci](../../../visual-basic/language-reference/operators/exponentiation-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `^` işleci davranışını etkileyen `^=` işleci. Kodunuzu kullanıyorsa `^=` bir sınıf veya aşırı yapısı `^`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `^=` değerini artırmak için işleci `Integer` değişkenini ikinci değişken ve ata birinci değişken sonucu.  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [^ İşleci](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetik İşleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
