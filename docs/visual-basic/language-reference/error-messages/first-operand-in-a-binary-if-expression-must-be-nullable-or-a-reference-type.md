---
title: İkili bir 'If' ifadesindeki ilk işlenen boş değer atanabilir veya bir başvuru türü olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: a93dd0a5422ce2a01a01c6fc77224e3ee946910e
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874151"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a>İkili bir 'If' ifadesindeki ilk işlenen boş değer atanabilir veya bir başvuru türü olmalıdır

Bir `If` ifade iki ya da üç bağımsız değişken alabilir. Yalnızca iki bağımsız değişken gönderdiğinizde, ilk bağımsız değişken bir başvuru türü veya null olabilen bir değer türü olmalıdır. İlk bağımsız değişken dışında herhangi bir şeyi değerlendiriyorsa `Nothing` , değeri döndürülür. İlk bağımsız değişken olarak değerlendirilirse `Nothing` , ikinci bağımsız değişken değerlendirilir ve döndürülür.  
  
 Örneğin, aşağıdaki kod, `If` biri üç bağımsız değişkene ve diğeri iki bağımsız değişkene sahip iki ifade içerir. İfadeler aynı değeri hesaplar ve döndürür.  
  
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
  
 **Hata kimliği:** BC33107  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
- Kodu, ilk bağımsız değişkenin null yapılabilir bir değer türü veya başvuru türü olması için değiştirememesi için üç bağımsız değişkenli `If` ifadeye veya bir ifadeye dönüştürmeyi düşünün `If...Then...Else` .  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [If İşleci](../operators/if-operator.md)
- [If...Then...Else Deyimi](../statements/if-then-else-statement.md)
- [Null yapılabilir değer türleri](../../programming-guide/language-features/data-types/nullable-value-types.md)
