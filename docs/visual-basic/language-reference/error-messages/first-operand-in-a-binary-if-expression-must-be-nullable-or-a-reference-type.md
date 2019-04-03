---
title: İkili bir 'If' ifadesindeki ilk işlenen boş değer atanabilir veya bir başvuru türü olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 32ff0adca9d35e6b5439ae06be85414924dac2e6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838631"
---
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="0e903-102">İkili bir 'If' ifadesindeki ilk işlenen boş değer atanabilir veya bir başvuru türü olmalıdır</span><span class="sxs-lookup"><span data-stu-id="0e903-102">First operand in a binary 'If' expression must be nullable or a reference type</span></span>
<span data-ttu-id="0e903-103">Bir `If` ifadesi, iki veya üç bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="0e903-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="0e903-104">Yalnızca iki bağımsız değişken gönderdiğinizde, ilk bağımsız değişkeninin bir başvuru türüyle veya null yapılabilir bir tür olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0e903-104">When you send only two arguments, the first argument must be a reference type or a nullable type.</span></span> <span data-ttu-id="0e903-105">İlk bağımsız değişken için bir şey dışında değerlendirilirse `Nothing`, bu değer döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0e903-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="0e903-106">İlk bağımsız değişken değerlendirilirse `Nothing`, ikinci bağımsız değişken değerlendirilir ve döndürdü.</span><span class="sxs-lookup"><span data-stu-id="0e903-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="0e903-107">Örneğin, aşağıdaki kod iki tane `If` üç bağımsız değişken biri diğeri iki bağımsız değişkenler ile ifadeler.</span><span class="sxs-lookup"><span data-stu-id="0e903-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="0e903-108">İfadeler, hesaplar ve aynı değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="0e903-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="0e903-109">Aşağıdaki ifadeler bu hataya neden:</span><span class="sxs-lookup"><span data-stu-id="0e903-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="0e903-110">**Hata Kimliği:** BC33107</span><span class="sxs-lookup"><span data-stu-id="0e903-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0e903-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0e903-111">To correct this error</span></span>  
  
-   <span data-ttu-id="0e903-112">Kod değiştiremiyorsanız, ilk bağımsız değişken bir boş değer atanabilir tür veya başvuru türü olması için üç bağımsız değişken bir dönüştürme göz önünde bulundurun `If` ifade veya bir `If...Then...Else` deyimi.</span><span class="sxs-lookup"><span data-stu-id="0e903-112">If you cannot change the code so that the first argument is a nullable type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="0e903-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e903-113">See also</span></span>

- [<span data-ttu-id="0e903-114">If İşleci</span><span class="sxs-lookup"><span data-stu-id="0e903-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="0e903-115">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="0e903-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="0e903-116">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="0e903-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
