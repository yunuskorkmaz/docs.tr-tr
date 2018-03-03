---
title: "?: İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: bbd434e02ece4843bab4ffded6877f81f622950c
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/02/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9fab7-102">?: İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9fab7-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="9fab7-103">Koşullu işleç (`?:`), yaygın olarak bilinen Üçlü koşullu işleç Boole ifadesi değerine bağlı olarak iki değerden birini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9fab7-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="9fab7-104">Aşağıda, koşullu işlecin sözdizimi belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="9fab7-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="9fab7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9fab7-105">Remarks</span></span>  
 <span data-ttu-id="9fab7-106">`condition` Değerlendirilmelidir `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="9fab7-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="9fab7-107">Varsa `condition` olan `true`, `first_expression` değerlendirilir ve sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="9fab7-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="9fab7-108">Varsa `condition` olan `false`, `second_expression` değerlendirilir ve sonucu olur.</span><span class="sxs-lookup"><span data-stu-id="9fab7-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="9fab7-109">İki ifadeden yalnızca biri değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="9fab7-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="9fab7-110">İki tür `first_expression` ve `second_expression` aynı olmalı ya da örtük bir dönüştürme bir türden diğerine bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9fab7-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="9fab7-111">Aksi takdirde gerektirebilir hesaplamalar express bir `if-else` koşullu işleç kullanarak daha az ama öz oluşturma.</span><span class="sxs-lookup"><span data-stu-id="9fab7-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="9fab7-112">Örneğin, aşağıdaki kodu ilk kullanan bir `if` deyimi ve tamsayı olumlu veya olumsuz olarak sınıflandırmak için koşullu bir işleç.</span><span class="sxs-lookup"><span data-stu-id="9fab7-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
```csharp
int input = Convert.ToInt32(Console.ReadLine());  
string classify;  
  
// if-else construction.  
if (input > 0)  
    classify = "positive";  
else  
    classify = "negative";  
  
// ?: conditional operator.  
classify = (input > 0) ? "positive" : "negative";  
```  
  
 <span data-ttu-id="9fab7-113">Koşullu işleç, sağa ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="9fab7-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="9fab7-114">İfade `a ? b : c ? d : e` olarak değerlendirilir `a ? b : (c ? d : e)`, olarak değil `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="9fab7-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="9fab7-115">Koşullu işleç aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="9fab7-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9fab7-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="9fab7-116">Example</span></span>  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9fab7-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9fab7-117">See Also</span></span>  
 [<span data-ttu-id="9fab7-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="9fab7-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9fab7-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9fab7-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9fab7-120">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="9fab7-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="9fab7-121">if-else</span><span class="sxs-lookup"><span data-stu-id="9fab7-121">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
 [<span data-ttu-id="9fab7-122">?. ve? İşleçler</span><span class="sxs-lookup"><span data-stu-id="9fab7-122">?. and ?Operators</span></span>](../../../csharp/language-reference/operators/null-conditional-operators.md)  
 [<span data-ttu-id="9fab7-123">?? İşleç</span><span class="sxs-lookup"><span data-stu-id="9fab7-123">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)
