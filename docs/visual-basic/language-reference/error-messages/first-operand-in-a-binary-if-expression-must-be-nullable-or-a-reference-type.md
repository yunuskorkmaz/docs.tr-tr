---
title: "Bir ikili &#39; ilk işlenen varsa &#39; ifade boş değer atanabilir veya bir başvuru türü"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f66b110c02076120c55a3bff28c3d7614bf8be26
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="af4b0-102">Bir ikili &#39; ilk işlenen varsa &#39; ifade boş değer atanabilir veya bir başvuru türü</span><span class="sxs-lookup"><span data-stu-id="af4b0-102">First operand in a binary &#39;If&#39; expression must be nullable or a reference type</span></span>
<span data-ttu-id="af4b0-103">Bir `If` ifadesi, iki veya üç bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="af4b0-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="af4b0-104">Yalnızca iki bağımsız değişken gönderdiğinizde, ilk bağımsız değişkeni bir başvuru türü veya boş değer atanabilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="af4b0-104">When you send only two arguments, the first argument must be a reference type or a nullable type.</span></span> <span data-ttu-id="af4b0-105">İlk bağımsız değişkeni için herhangi bir şey dışında değerlendirilirse `Nothing`, bu değer döndürülür.</span><span class="sxs-lookup"><span data-stu-id="af4b0-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="af4b0-106">İlk bağımsız değişken değerlendirilirse `Nothing`, ikinci bağımsız değişkeni değerlendirilir ve döndürdü.</span><span class="sxs-lookup"><span data-stu-id="af4b0-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="af4b0-107">Örneğin, aşağıdaki kod iki içeren `If` ifadeleri, üç bağımsız değişkenlerle diğeri iki bağımsız değişkenlere sahip.</span><span class="sxs-lookup"><span data-stu-id="af4b0-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="af4b0-108">İfadeleri hesaplamak ve aynı değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="af4b0-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="af4b0-109">Aşağıdaki ifadeler bu hataya neden:</span><span class="sxs-lookup"><span data-stu-id="af4b0-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="af4b0-110">**Hata Kimliği:** BC33107</span><span class="sxs-lookup"><span data-stu-id="af4b0-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="af4b0-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="af4b0-111">To correct this error</span></span>  
  
-   <span data-ttu-id="af4b0-112">İlk bağımsız değişkeni bir boş değer atanabilir veya reference türü böylece kodu değiştiremezsiniz, üç değişkenine dönüştürmeyi göz önüne `If` ifadesi veya bir `If...Then...Else` deyimi.</span><span class="sxs-lookup"><span data-stu-id="af4b0-112">If you cannot change the code so that the first argument is a nullable type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="af4b0-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="af4b0-113">See Also</span></span>  
 [<span data-ttu-id="af4b0-114">Varsa işleci</span><span class="sxs-lookup"><span data-stu-id="af4b0-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="af4b0-115">If... Then... Else deyimi</span><span class="sxs-lookup"><span data-stu-id="af4b0-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="af4b0-116">Boş değer atanabilen değer türleri</span><span class="sxs-lookup"><span data-stu-id="af4b0-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
