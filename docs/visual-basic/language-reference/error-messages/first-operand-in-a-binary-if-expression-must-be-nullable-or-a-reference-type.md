---
title: İkili bir 'If' ifadesindeki ilk işlenen boş değer atanabilir veya bir başvuru türü olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 4b520949cb59b63ea39441632dc5e2c6d000d711
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249532"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>İkili bir 'If' ifadesindeki ilk işlenen boş değer atanabilir veya bir başvuru türü olmalıdır
Bir `If` ifade iki veya üç bağımsız değişken alabilir. Yalnızca iki bağımsız değişken gönderdiğinde, ilk bağımsız değişken bir başvuru türü veya nullable değer türü olmalıdır. İlk bağımsız değişken, başka bir `Nothing`şeye değer biçilirse, değeri döndürülür. İlk bağımsız değişken `Nothing`, ikinci bağımsız değişken olarak değerlendirilir ve döndürülür.  
  
 Örneğin, aşağıdaki kod, `If` biri üç bağımsız değişkenli, diğeri iki bağımsız değişkenli olmak üzere iki ifade içerir. İfadeler aynı değeri hesaplar ve döndürer.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Aşağıdaki ifadeler bu hataya neden olur:  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 **Hata Kimliği:** BC33107  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Kodu, ilk bağımsız değişkenin geçersiz bir değer türü veya başvuru türü olacak şekilde değiştiremiyorsanız, üç bağımsız değişkenli `If` ifadeye veya bir `If...Then...Else` deyime dönüştürmeyi düşünün.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [If İşleci](../../../visual-basic/language-reference/operators/if-operator.md)
- [If...Then...Else Deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Boş Değer Atanabilen Değer Türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
