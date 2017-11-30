---
title: "Bir ikili &#39; ilk işlenen varsa &#39; ifade boş değer atanabilir veya bir başvuru türü"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords: BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f66b110c02076120c55a3bff28c3d7614bf8be26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a>Bir ikili &#39; ilk işlenen varsa &#39; ifade boş değer atanabilir veya bir başvuru türü
Bir `If` ifadesi, iki veya üç bağımsız değişken alabilir. Yalnızca iki bağımsız değişken gönderdiğinizde, ilk bağımsız değişkeni bir başvuru türü veya boş değer atanabilir bir tür olmalıdır. İlk bağımsız değişkeni için herhangi bir şey dışında değerlendirilirse `Nothing`, bu değer döndürülür. İlk bağımsız değişken değerlendirilirse `Nothing`, ikinci bağımsız değişkeni değerlendirilir ve döndürdü.  
  
 Örneğin, aşağıdaki kod iki içeren `If` ifadeleri, üç bağımsız değişkenlerle diğeri iki bağımsız değişkenlere sahip. İfadeleri hesaplamak ve aynı değeri döndürür.  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 Aşağıdaki ifadeler bu hataya neden:  
  
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
  
-   İlk bağımsız değişkeni bir boş değer atanabilir veya reference türü böylece kodu değiştiremezsiniz, üç değişkenine dönüştürmeyi göz önüne `If` ifadesi veya bir `If...Then...Else` deyimi.  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Varsa işleci](../../../visual-basic/language-reference/operators/if-operator.md)  
 [If... Then... Else deyimi](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [Boş değer atanabilen değer türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
