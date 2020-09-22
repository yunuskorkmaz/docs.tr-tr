---
title: Narrowing
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
ms.openlocfilehash: 77515357ac9dc972992df09c471695aad13985c4
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90867937"
---
# <a name="narrowing-visual-basic"></a>Daraltma (Visual Basic)

Bir dönüştürme işlecinin () bir `CType` sınıfı ya da yapıyı özgün sınıf veya yapının olası bazı değerlerini tutabilecek bir türe dönüştürdüğü anlamına gelir.  
  
## <a name="converting-with-the-narrowing-keyword"></a>Daraltma anahtar sözcüğüyle dönüştürme  

 Dönüştürme yordamının öğesine ek olarak belirtmeniz gerekir `Public Shared` `Narrowing` .  
  
 Daraltma dönüştürmeleri her zaman çalışma zamanında başarılı olmaz ve veri kaybına neden olabilir. Örnekler `Long` `Integer` , `String` `Date` türetilmiş bir türe ve temel türe örnektir. Temel tür türetilmiş türün tüm üyelerini içermediğinden ve bu nedenle türetilmiş türün bir örneği olmadığından, bu son dönüştürme daraltma yapılır.  
  
 `Option Strict`İse `On` , tüketim kodu `CType` tüm daraltma dönüştürmeleri için kullanılmalıdır.  
  
 `Narrowing`Anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Operator Deyimi](../statements/operator-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Operator Deyimi](../statements/operator-statement.md)
- [Genişletme](widening.md)
- [Genişletme ve Daraltma Dönüşümleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Nasıl yapılır: İşleç Tanımlama](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType İşlevi](../functions/ctype-function.md)
- [Option Strict Deyimi](../statements/option-strict-statement.md)
