---
title: İşleçlerin Etkili Bileşimi
ms.date: 07/20/2015
helpviewer_keywords:
- expressions [Visual Basic], parentheses
- operators [Visual Basic], associativity
- expressions [Visual Basic], operators
- operators [Visual Basic], precedence
- Visual Basic code, operators
- Visual Basic code, expressions
- operators [Visual Basic], complex expressions
- expressions [Visual Basic], complex
- parentheses [Visual Basic], complex expressions
- numeric expressions
ms.assetid: bd22340e-b5be-458b-8772-3916c02309a4
ms.openlocfilehash: 83ad53e4c75490a75eba0f80a6bf0f078aa4d426
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348976"
---
# <a name="efficient-combination-of-operators-visual-basic"></a>İşleçlerin Etkili Bileşimi (Visual Basic)
Karmaşık ifadelerde birçok farklı işleç bulunabilir. Aşağıdaki örnek bunu göstermektedir.  
  
 `x = (45 * (y + z)) ^ (2 / 85) * 5 + z`  
  
 Önceki örnekteki gibi karmaşık ifadelerin oluşturulması, işleç önceliği kurallarının eksiksiz bir şekilde anlaşılmasına gerek duyar. Daha fazla bilgi için [Visual Basic operatör önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)bölümüne bakın.  
  
## <a name="parenthetical-expressions"></a>Parantez içinde Ifadeler  
 Genellikle işlemlerin operatör önceliğine göre belirlenen şekilde farklı bir sırada devam etmesini istiyorsunuz. Aşağıdaki örneği göz önünde bulundurun.  
  
 `x = z * y + 4`  
  
 Yukarıdaki örnek `z` `y`ile çarpar ve sonucu `4`ekler. Ancak, sonucu `z`çarpmadan önce `y` ve `4` eklemek istiyorsanız, parantez kullanarak normal operatör önceliğini geçersiz kılabilirsiniz. Bir ifadeyi parantez içine alarak, işleç önceliği ne olursa olsun, bu ifadenin ilk olarak değerlendirilmesini zorlarsınız. Önceki örneği öncelikle eklemeyi zorlamak için, aşağıdaki örnekte olduğu gibi yeniden yazabilirsiniz.  
  
 `x = z * (y + 4)`  
  
 Yukarıdaki örnek `y` ve `4`ekler ve sonra bu toplamı `z`ile çarpar.  
  
### <a name="nested-parenthetical-expressions"></a>İç içe geçmiş parantez Ifadeleri  
 Daha da fazla öncelik vermek için ifadeleri birden çok parantez düzeyinde iç içe yerleştirebilirsiniz. Parantez içinde en derin iç içe yerleştirilmiş ifadeler önce değerlendirilir, ardından sonraki en derin iç içe geçmiş ve bu, en az derin iç içe, son olarak da parantez dışında ifadeler. Aşağıdaki örnek bunu göstermektedir.  
  
 `x = (z * 4) ^ (y * (z + 2))`  
  
 Önceki örnekte, `z + 2` önce değerlendirilir, sonra diğer parantez içinde ifadeler. Normalde ekleme veya çarpmayla daha yüksek önceliğe sahip olan üs, bu örnekte en son değerlendirilir çünkü diğer ifadeler parantez içine alınmıştır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic aritmetik Işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Visual Basic karşılaştırma Işleçleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic mantıksal ve bit düzeyinde Işleçler](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [Mantıksal/bit düzeyinde Işleçler (Visual Basic)](../../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Boole İfadeleri](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [Değer Karşılaştırmaları](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [Nasıl yapılır: Sayısal Değerleri Hesaplama](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-calculate-numeric-values.md)
- [Visual Basic operatör önceliği](../../../../visual-basic/language-reference/operators/operator-precedence.md)
