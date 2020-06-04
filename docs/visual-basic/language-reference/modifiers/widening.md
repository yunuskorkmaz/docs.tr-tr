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
ms.openlocfilehash: 69040bf48b44a54f7a231738b88db1cbc716ebb3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359909"
---
# <a name="widening-visual-basic"></a>Genişletme (Visual Basic)
Bir dönüştürme işlecinin () bir `CType` sınıfı ya da yapıyı özgün sınıf veya yapının tüm olası değerlerini tutabilecek bir türe dönüştürdüğü anlamına gelir.  
  
## <a name="converting-with-the-widening-keyword"></a>Genişletme anahtar sözcüğüyle dönüştürme  
 Dönüştürme yordamının öğesine ek olarak belirtmeniz gerekir `Public Shared` `Widening` .  
  
 Genişletme dönüştürmeleri her zaman çalışma zamanında başarılı olur ve veri kaybına neden olmaz. Örnekler `Single` `Double` , `Char` `String` temel türüne ve türetilmiş bir türe örnektir. Türetilmiş tür temel türün tüm üyelerini içerdiğinden ve bu nedenle temel türün bir örneği olduğundan, bu son dönüştürme işlemi genişletme.  
  
 Tüketim kodu, `CType` olsa bile, genişletme dönüştürmeleri için kullanmak zorunda değildir `Option Strict` `On` .  
  
 `Widening`Anahtar sözcüğü bu bağlamda kullanılabilir:  
  
 [Operator Deyimi](../statements/operator-statement.md)  
  
 Genişletme ve daraltma dönüştürme işleçlerinin tanımları için bkz. [nasıl yapılır: dönüştürme Işleci tanımlama](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Operator Deyimi](../statements/operator-statement.md)
- [Narrowing](narrowing.md)
- [Genişletme ve Daraltma Dönüşümleri](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Nasıl yapılır: İşleç Tanımlama](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [CType İşlevi](../functions/ctype-function.md)
- [Option Strict Deyimi](../statements/option-strict-statement.md)
- [Nasıl yapılır: Dönüştürme İşleci Tanımlama](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
