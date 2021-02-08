---
description: "Daha fazla bilgi edinin: BC33107: bir ikili ' If ' ifadesindeki Ilk işlenen null yapılabilir veya bir başvuru türü olmalıdır"
title: İkili bir 'If' ifadesindeki ilk işlenen boş değer atanabilir veya bir başvuru türü olmalıdır
ms.date: 07/20/2015
f1_keywords:
- bc33107
- vbc33107
helpviewer_keywords:
- BC33107
ms.assetid: 493c8899-3f6b-4471-8eb6-9284e8492768
ms.openlocfilehash: 4a0037680e31a8220cb796e6d8f3215139e01b20
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796255"
---
# <a name="bc33107-first-operand-in-a-binary-if-expression-must-be-nullable-or-a-reference-type"></a><span data-ttu-id="0265e-103">BC33107: bir ikili ' If ' ifadesindeki Ilk işlenen null yapılabilir veya bir başvuru türü olmalıdır</span><span class="sxs-lookup"><span data-stu-id="0265e-103">BC33107: First operand in a binary 'If' expression must be nullable or a reference type</span></span>

<span data-ttu-id="0265e-104">Bir `If` ifade iki ya da üç bağımsız değişken alabilir.</span><span class="sxs-lookup"><span data-stu-id="0265e-104">An `If` expression can take either two or three arguments.</span></span> <span data-ttu-id="0265e-105">Yalnızca iki bağımsız değişken gönderdiğinizde, ilk bağımsız değişken bir başvuru türü veya null olabilen bir değer türü olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0265e-105">When you send only two arguments, the first argument must be a reference type or a nullable value type.</span></span> <span data-ttu-id="0265e-106">İlk bağımsız değişken dışında herhangi bir şeyi değerlendiriyorsa `Nothing` , değeri döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0265e-106">If the first argument evaluates to anything other than `Nothing`, its value is returned.</span></span> <span data-ttu-id="0265e-107">İlk bağımsız değişken olarak değerlendirilirse `Nothing` , ikinci bağımsız değişken değerlendirilir ve döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0265e-107">If the first argument evaluates to `Nothing`, the second argument is evaluated and returned.</span></span>

 <span data-ttu-id="0265e-108">Örneğin, aşağıdaki kod, `If` biri üç bağımsız değişkene ve diğeri iki bağımsız değişkene sahip iki ifade içerir.</span><span class="sxs-lookup"><span data-stu-id="0265e-108">For example, the following code contains two `If` expressions, one with three arguments and one with two arguments.</span></span> <span data-ttu-id="0265e-109">İfadeler aynı değeri hesaplar ve döndürür.</span><span class="sxs-lookup"><span data-stu-id="0265e-109">The expressions calculate and return the same value.</span></span>

```vb
' firstChoice is a nullable value type.
Dim firstChoice? As Integer = Nothing
Dim secondChoice As Integer = 1128
' If expression with three arguments.
Console.WriteLine(If(firstChoice IsNot Nothing, firstChoice, secondChoice))
' If expression with two arguments.
Console.WriteLine(If(firstChoice, secondChoice))
```

 <span data-ttu-id="0265e-110">Aşağıdaki ifadeler bu hataya neden olur:</span><span class="sxs-lookup"><span data-stu-id="0265e-110">The following expressions cause this error:</span></span>

```vb
Dim choice1 = 4
Dim choice2 = 5
Dim booleanVar = True

' Not valid.
'Console.WriteLine(If(choice1 < choice2, 1))
' Not valid.
'Console.WriteLine(If(booleanVar, "Test returns True."))
```

 <span data-ttu-id="0265e-111">**Hata kimliği:** BC33107</span><span class="sxs-lookup"><span data-stu-id="0265e-111">**Error ID:** BC33107</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0265e-112">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="0265e-112">To correct this error</span></span>

- <span data-ttu-id="0265e-113">Kodu, ilk bağımsız değişkenin null yapılabilir bir değer türü veya başvuru türü olması için değiştirememesi için üç bağımsız değişkenli `If` ifadeye veya bir ifadeye dönüştürmeyi düşünün `If...Then...Else` .</span><span class="sxs-lookup"><span data-stu-id="0265e-113">If you cannot change the code so that the first argument is a nullable value type or reference type, consider converting to a three-argument `If` expression, or to an `If...Then...Else` statement.</span></span>

```vb
Console.WriteLine(If(choice1 < choice2, 1, 2))
Console.WriteLine(If(booleanVar, "Test returns True.", "Test returns False."))
```

## <a name="see-also"></a><span data-ttu-id="0265e-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0265e-114">See also</span></span>

- [<span data-ttu-id="0265e-115">If İşleci</span><span class="sxs-lookup"><span data-stu-id="0265e-115">If Operator</span></span>](../operators/if-operator.md)
- [<span data-ttu-id="0265e-116">If...Then...Else Deyimi</span><span class="sxs-lookup"><span data-stu-id="0265e-116">If...Then...Else Statement</span></span>](../statements/if-then-else-statement.md)
- [<span data-ttu-id="0265e-117">Null yapılabilir değer türleri</span><span class="sxs-lookup"><span data-stu-id="0265e-117">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
