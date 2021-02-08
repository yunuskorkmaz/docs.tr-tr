---
description: 'Daha fazla bilgi edinin: daraltma (Visual Basic)'
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
ms.openlocfilehash: 1dd9185ccf30fb6f9dc9360f75450c2533ab90e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795358"
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
