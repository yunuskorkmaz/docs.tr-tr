---
title: "^ İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.^
helpviewer_keywords:
- raising numbers to powers
- ^ operator [Visual Basic], exponention
- square operator [Visual Basic]
- ^ operator [Visual Basic]
- exponentiation operator [Visual Basic]
- exponent
- numbers [Visual Basic], rasing
- powers
- arithmetic operators [Visual Basic], exponentiation
ms.assetid: d89a1ca8-83da-4784-a87b-a9d7dceb3f62
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9e7159f289b687055c7d75cc8da58d6f76607a83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>^ İşleci (Visual Basic)
Bir sayıyı diğer bir sayının kuvvetine yükseltir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
number ^ exponent  
```  
  
## <a name="parts"></a>Bölümler  
 `number`  
 Gerekli. Herhangi bir sayısal ifade.  
  
 `exponent`  
 Gerekli. Herhangi bir sayısal ifade.  
  
## <a name="result"></a>Sonuç  
 Sonuç `number` üssünü `exponent`, her zaman olarak bir `Double` değeri.  
  
## <a name="supported-types"></a>Desteklenen türler  
 `Double`. Tüm farklı türündeki işlenenler için dönüştürülür `Double`.  
  
## <a name="remarks"></a>Açıklamalar  
 Visual Basic her zaman içinde üs gerçekleştirir [Double veri türü](../../../visual-basic/language-reference/data-types/double-data-type.md).  
  
 Değeri `exponent` kesir olabilir negatif veya her ikisi de.  
  
 Tek bir deyimde birden fazla üs gerçekleştirildiğinde `^` işleci soldan sağa karşılaşılana olarak değerlendirilir.  
  
> [!NOTE]
>  `^` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `^` işleci üs gücünü sayıya yükseltin. İkinci üssünün ilk işlenen sonucudur.  
  
 [!code-vb[VbVbalrOperators#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-operator_1.vb)]  
  
 Önceki örnekte aşağıdaki sonuçları verir:  
  
 `exp1`(2 kare) 4'e ayarlanır.  
  
 `exp2`19683 (3 küpünü, ardından küpünü bu değere) ayarlayın.  
  
 `exp3`-125 (küpünü -5) olarak ayarlanır.  
  
 `exp4`625'in (Dördüncü gücüne -5) ayarlanır.  
  
 `exp5`2 (8 kökündeki küpü)'ye ayarlanır.  
  
 `exp6`0,5 (8 küp kök tarafından bölünmüş 1.0) ayarlanır.  
  
 Önceki örnekte ifadelerde parantez önemini unutmayın. Nedeniyle *İşleç önceliği*, Visual Basic normalde gerçekleştirir `^` herhangi diğer önce işleci birli bile `–` işleci. Varsa `exp4` ve `exp6` hesaplanan parantez olmadan, bunlar üretilen aşağıdaki sonuçları:  
  
 `exp4 = -5 ^ 4`(5 olarak – dördüncü güç), hesaplanan-625 içinde sonuçlanacak.  
  
 `exp6 = 8 ^ -1.0 / 3.0`(8 – 1 güç veya 0,125) olarak hesaplanır 0.041666666666666666666666666666667 içinde oluşturacağı 3.0 bölü.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [^ = İşleci](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Aritmetik işleçler](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
