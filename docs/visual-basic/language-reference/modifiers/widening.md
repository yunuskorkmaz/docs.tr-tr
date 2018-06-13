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
ms.openlocfilehash: 2323aa38c81ce4e027f256d0e29c069f7ec77c00
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33595319"
---
# <a name="widening-visual-basic"></a>Genişletme (Visual Basic)
Belirten bir dönüşüm işleci (`CType`) bir sınıf veya yapı özgün sınıf veya yapı tüm olası değerlerini tutan bir türe dönüştürür.  
  
## <a name="converting-with-the-widening-keyword"></a>Genişletme anahtar sözcüğü ile dönüştürme  
 Dönüştürme yordamı belirtmelisiniz `Public Shared` ek olarak `Widening`.  
  
 Genişletme dönüşümleri çalışma zamanında her zaman başarılı ve hiçbir zaman veri kaybına neden. Örnekler `Single` için `Double`, `Char` için `String`ve türetilmiş bir tür için temel türü. Türetilmiş bir tür temel türdeki tüm üyelerin içerir ve bu nedenle temel türü örneği olduğundan bu son dönüştürme genişletme.  
  
 Kullanıcı kodu kullanmak zorunda kalmazsınız `CType` dönüşümleri, için bile `Option Strict` olan `On`.  
  
 `Widening` Anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Örneğin genişletme ve daraltma dönüşüm işleçleri tanımları bkz [nasıl yapılır: bir dönüşüm işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)  
 [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)  
 [CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)  
 [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
