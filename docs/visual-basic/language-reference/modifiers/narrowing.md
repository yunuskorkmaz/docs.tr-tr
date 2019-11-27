---
title: Daraltma
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: b252f7939e812f31103d4bd98ffd50953679f042
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351470"
---
# <a name="narrowing-visual-basic"></a>Daraltma (Visual Basic)
Bir dönüştürme işlecinin (`CType`) bir sınıfı ya da yapıyı özgün sınıf veya yapının olası bazı değerlerini tutabilecek bir türe dönüştürdüğü anlamına gelir.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Daraltma anahtar sözcüğüyle dönüştürme  
 Dönüştürme yordamının `Narrowing`ek olarak `Public Shared` belirtmesi gerekir.  
  
 Daraltma dönüştürmeleri her zaman çalışma zamanında başarılı olmaz ve veri kaybına neden olabilir. Örnekler, türetilmiş bir türe `Integer`, `Date``String` ve temel bir tür `Long`. Temel tür türetilmiş türün tüm üyelerini içermediğinden ve bu nedenle türetilmiş türün bir örneği olmadığından, bu son dönüştürme daraltma yapılır.  
  
 `Option Strict` `On`, tüketen kodun tüm daraltma dönüştürmeleri için `CType` kullanması gerekir.  
  
 `Narrowing` anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Operator Deyimi](../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../visual-basic/language-reference/modifiers/widening.md)
- [Genişletme ve Daraltma Dönüştürmeleri](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Nasıl yapılır: İşleç Tanımlama](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType İşlevi](../../../visual-basic/language-reference/functions/ctype-function.md)
- [Option Strict Deyimi](../../../visual-basic/language-reference/statements/option-strict-statement.md)
