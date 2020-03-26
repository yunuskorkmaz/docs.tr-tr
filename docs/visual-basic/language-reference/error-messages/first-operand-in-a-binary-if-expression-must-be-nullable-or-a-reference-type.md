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
# <a name="first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="13892-102">İkili bir 'If' ifadesindeki ilk işlenen boş değer atanabilir veya bir başvuru türü olmalıdır</span><span class="sxs-lookup"><span data-stu-id="13892-102">First operand in a binary 'If' expression must be nullable or a reference type</span></span>
<span data-ttu-id="13892-103">Bir `If` ifade iki veya üç bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="13892-103">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="13892-104">Yalnızca iki bağımsız değişken gönderdiğinde, ilk bağımsız değişken bir başvuru türü veya nullable değer türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="13892-104">When you send only two arguments, the first argument must be a reference type or a nullable value type.</span></span> <span data-ttu-id="13892-105">İlk bağımsız değişken, başka bir `Nothing`şeye değer biçilirse, değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="13892-105">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="13892-106">İlk bağımsız değişken `Nothing`, ikinci bağımsız değişken olarak değerlendirilir ve döndürülür.</span><span class="sxs-lookup"><span data-stu-id="13892-106">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>  
  
 <span data-ttu-id="13892-107">Örneğin, aşağıdaki kod, `If` biri üç bağımsız değişkenli, diğeri iki bağımsız değişkenli olmak üzere iki ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="13892-107">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="13892-108">İfadeler aynı değeri hesaplar ve döndürer.</span><span class="sxs-lookup"><span data-stu-id="13892-108">The expressions calculate and return the same value.</span></span>  
  
```vb  
' firstChoice is a nullable value type.  
Dim firstChoice? As Integer = Nothing  
Dim secondChoice As Integer = 1128  
' If expression with three arguments.  
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))  
' If expression with two arguments.  
Console.WriteLine(If(firstChoice, secondChoice))  
```  
  
 <span data-ttu-id="13892-109">Aşağıdaki ifadeler bu hataya neden olur:</span><span class="sxs-lookup"><span data-stu-id="13892-109">The following expressions cause this error:</span></span>  
  
```vb  
Dim choice1 = 4  
Dim choice2 = 5  
Dim booleanVar = True  
  
' Not valid.  
'Console.WriteLine(If(choice1 < choice2, 1))  
' Not valid.  
'Console.WriteLine(If(booleanVar, "Test returns True."))  
```  
  
 <span data-ttu-id="13892-110">**Hata Kimliği:** BC33107</span><span class="sxs-lookup"><span data-stu-id="13892-110">**Error ID:** BC33107</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="13892-111">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="13892-111">To correct this error</span></span>  
  
- <span data-ttu-id="13892-112">Kodu, ilk bağımsız değişkenin geçersiz bir değer türü veya başvuru türü olacak şekilde değiştiremiyorsanız, üç bağımsız değişkenli `If` ifadeye veya bir `If...Then...Else` deyime dönüştürmeyi düşünün.</span><span class="sxs-lookup"><span data-stu-id="13892-112">If you cannot change the code so that the first argument is a nullable value type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>  
  
```vb  
Console.WriteLine(If(choice1 < choice2, 1, 2))  
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))  
```  
  
## <a name="see-also"></a><span data-ttu-id="13892-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13892-113">See also</span></span>

- [<span data-ttu-id="13892-114">If İşleci</span><span class="sxs-lookup"><span data-stu-id="13892-114">If Operator</span></span>](../../../visual-basic/language-reference/operators/if-operator.md)
- [<span data-ttu-id="13892-115">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="13892-115">If...Then...Else Statement</span></span>](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="13892-116">Boş Değer Atanabilen Değer Türleri</span><span class="sxs-lookup"><span data-stu-id="13892-116">Nullable Value Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
