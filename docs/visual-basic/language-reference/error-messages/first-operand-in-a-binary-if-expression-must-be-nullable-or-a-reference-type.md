---
title: Bir ikili ilk işlenen &#39;varsa&#39; ifadesi null olmalı veya bir başvuru türü
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 76078d315b2c32a2a29aa652a65b463622afec36
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33590835"
---
# <a name="first-operand-in-a-binary-39if39-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="daeb6-102">Bir ikili ilk işlenen &#39;varsa&#39; ifadesi null olmalı veya bir başvuru türü</span><span class="sxs-lookup"><span data-stu-id="daeb6-102">First operand in a binary &#39;If&#39; expression must be nullable or a reference type</span></span>
<span data-ttu-id="daeb6-103">Bir `If` ifadesi, iki veya üç bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="daeb6-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="daeb6-104">Yalnızca iki bağımsız değişken gönderdiğinizde, ilk bağımsız değişkeni bir başvuru türü veya boş değer atanabilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="daeb6-104">When you send only two arguments, the first argument must be a reference type or a nullable type.</span></span> <span data-ttu-id="daeb6-105">İlk bağımsız değişkeni için herhangi bir şey dışında değerlendirilirse `Nothing`, bu değer döndürülür.</span><span class="sxs-lookup"><span data-stu-id="daeb6-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="daeb6-106">İlk bağımsız değişken değerlendirilirse `Nothing`, ikinci bağımsız değişkeni değerlendirilir ve döndürdü.</span><span class="sxs-lookup"><span data-stu-id="daeb6-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="daeb6-107">Örneğin, aşağıdaki kod iki içeren `If` ifadeleri, üç bağımsız değişkenlerle diğeri iki bağımsız değişkenlere sahip.</span><span class="sxs-lookup"><span data-stu-id="daeb6-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="daeb6-108">İfadeleri hesaplamak ve aynı değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="daeb6-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="daeb6-109">Aşağıdaki ifadeler bu hataya neden:</span><span class="sxs-lookup"><span data-stu-id="daeb6-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="daeb6-110">**Hata Kimliği:** BC33107</span><span class="sxs-lookup"><span data-stu-id="daeb6-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="daeb6-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="daeb6-111">To correct this error</span></span>  
  
-   <span data-ttu-id="daeb6-112">İlk bağımsız değişkeni bir boş değer atanabilir veya reference türü böylece kodu değiştiremezsiniz, üç değişkenine dönüştürmeyi göz önüne `If` ifadesi veya bir `If...Then...Else` deyimi.</span><span class="sxs-lookup"><span data-stu-id="daeb6-112">If you cannot change the code so that the first argument is a nullable type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="daeb6-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="daeb6-113">See Also</span></span>  
 [<span data-ttu-id="daeb6-114">If İşleci</span><span class="sxs-lookup"><span data-stu-id="daeb6-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)  
 [<span data-ttu-id="daeb6-115">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="daeb6-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="daeb6-116">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="daeb6-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
