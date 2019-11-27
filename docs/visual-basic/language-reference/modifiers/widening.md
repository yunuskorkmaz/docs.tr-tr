---
title: Genişletme
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
ms.openlocfilehash: 1c9aa78549ca6e41c9fe54c12e0aaec8e7cc30cb
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347838"
---
# <a name="widening-visual-basic"></a>Genişletme (Visual Basic)
Bir dönüştürme işlecinin (`CType`) bir sınıfı ya da yapıyı özgün sınıf veya yapının tüm olası değerlerini tutabilecek bir türe dönüştürdüğü anlamına gelir.  
  
## <a name="converting-with-the-widening-keyword"></a>Genişletme anahtar sözcüğüyle dönüştürme  
 Dönüştürme yordamının `Widening`ek olarak `Public Shared` belirtmesi gerekir.  
  
 Genişletme dönüştürmeleri her zaman çalışma zamanında başarılı olur ve veri kaybına neden olmaz. Örnekler, `String``Char` ve temel türüne türetilmiş bir tür `Double``Single`. Türetilmiş tür temel türün tüm üyelerini içerdiğinden ve bu nedenle temel türün bir örneği olduğundan, bu son dönüştürme işlemi genişletme.  
  
 Kullanım kodu, `Option Strict` `On`olsa bile, genişleyen dönüştürmeler için `CType` kullanmak zorunda değildir.  
  
 `Widening` anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 Genişletme ve daraltma dönüştürme işleçlerinin tanımları için bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
