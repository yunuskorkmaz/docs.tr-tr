---
title: << = işleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
ms.openlocfilehash: 4c262da906a6033680b05f6a4099a6a1dc8bfab5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260638"
---
# <a name="-operator-visual-basic"></a>\<\<= İşleci (Visual Basic)
Bir değişken veya özellik değerini temel aritmetik sola kaydırma gerçekleştirir ve sonucu değişken veya özellik için atar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>Bölümler  
 `variableorproperty`  
 Gerekli. Değişken veya özellik bir tamsayı türü (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).  
  
 `amount`  
 Gerekli. Sayısal ifade bir veri türünün için widens `Integer`.  
  
## <a name="remarks"></a>Açıklamalar  
 Öğe sol tarafındaki `<<=` işleci, bir basit skaler değişkeni, bir özellik veya dizi öğesi olabilir. Değişken veya özellik olamaz [salt okunur](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `<<=` İşleci ilk değişken veya özellik değerini temel aritmetik sola kaydırma gerçekleştirir. İşleci, bu işlemin sonucunu daha sonra değişken veya özellik geri atar.  
  
 Sonucu ucunu kaydırılacak bitlerin diğer sonunda yeniden girmesini yok anlamına gelir özelliği aritmetik kaydırmalar döngüsel, değildir. Aritmetik sola kaydırma, sonuç veri türü aralığının dışında kaydırılacak bitlerin atılır ve sağ tarafta işleci boşaltılmış bit konumları sıfır olarak ayarlanır.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 [<< İşleci](../../../visual-basic/language-reference/operators/left-shift-operator.md) olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Aşırı yükleme `<<` işleci davranışını etkileyen `<<=` işleci. Kodunuzu kullanıyorsa `<<=` bir sınıf veya aşırı yapısı `<<`, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `<<=` bit desenini kaydırılacak işleci bir `Integer` değişkeni değişkene atama sonucu ve belirtilen süre kaldı.  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [<< İşleci](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Bit Kaydırma İşleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
