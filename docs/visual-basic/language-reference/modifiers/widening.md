---
title: Genişletme (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: 3b9d1ec15c6c2000fb0842abe25848f853cdf986
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54703721"
---
# <a name="widening-visual-basic"></a>Genişletme (Visual Basic)
Bildiren bir dönüştürme operatörünün (`CType`) bir sınıf ya da yapıyı özgün sınıf veya yapının tüm olası değerlerini tutabilecek bir türe dönüştürür.  
  
## <a name="converting-with-the-widening-keyword"></a>Genişletme anahtar sözcüğü ile dönüştürme  
 Dönüştürme yordamı belirtmelisiniz `Public Shared` ek olarak `Widening`.  
  
 Genişletme dönüştürmeleri, çalışma zamanında her zaman başarılı ve hiçbir zaman veri kaybına neden. Örnekler `Single` için `Double`, `Char` için `String`ve türetilmiş bir tür yerine bunun temel türü. Türetilmiş tür temel türünün tüm üyelerini içerir ve bu nedenle temel türün bir örneği olduğundan, bu son dönüştürme genişletme.  
  
 Tüketici kod kullanmak zorunda kalmazsınız `CType` genişletme dönüştürmeleri, için bile `Option Strict` olduğu `On`.  
  
 `Widening` Anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Örneğin genişletme ve daraltma dönüştürme operatörlerini tanımları bkz [nasıl yapılır: Bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Nasıl yapılır: Bir işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Nasıl yapılır: Bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
