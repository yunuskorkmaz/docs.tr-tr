---
title: '?: İşleci (C# Başvurusu)'
ms.date: 07/20/2015
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 150149453a67d8e5319461266865cb25be180347
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506438"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="766ed-102">?: İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="766ed-102">?: Operator (C# Reference)</span></span>
<span data-ttu-id="766ed-103">Koşullu işleç (`?:`), yaygın olarak bilinen bir Üçlü koşullu işleç, bir Boolean ifadesinin değerine bağlı olarak iki değerden birini döndürür.</span><span class="sxs-lookup"><span data-stu-id="766ed-103">The conditional operator (`?:`), commonly known as the ternary conditional operator, returns one of two values depending on the value of a Boolean expression.</span></span> <span data-ttu-id="766ed-104">Aşağıda, koşullu işlecin sözdizimi belirtilmiştir.</span><span class="sxs-lookup"><span data-stu-id="766ed-104">Following is the syntax for the conditional operator.</span></span>  
  
```  
condition ? first_expression : second_expression;  
```  
  
## <a name="remarks"></a><span data-ttu-id="766ed-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="766ed-105">Remarks</span></span>  
 <span data-ttu-id="766ed-106">`condition` Değerlendirilmelidir `true` veya `false`.</span><span class="sxs-lookup"><span data-stu-id="766ed-106">The `condition` must evaluate to `true` or `false`.</span></span> <span data-ttu-id="766ed-107">Varsa `condition` olduğu `true`, `first_expression` değerlendirilir ve sonuç olur.</span><span class="sxs-lookup"><span data-stu-id="766ed-107">If `condition` is `true`, `first_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="766ed-108">Varsa `condition` olduğu `false`, `second_expression` değerlendirilir ve sonuç olur.</span><span class="sxs-lookup"><span data-stu-id="766ed-108">If `condition` is `false`, `second_expression` is evaluated and becomes the result.</span></span> <span data-ttu-id="766ed-109">İki ifadeden yalnızca biri değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="766ed-109">Only one of the two expressions is evaluated.</span></span>  
  
 <span data-ttu-id="766ed-110">İki tür `first_expression` ve `second_expression` aynı olmalıdır veya bir örtük dönüştürme bir türden diğerine bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="766ed-110">Either the type of `first_expression` and `second_expression` must be the same, or an implicit conversion must exist from one type to the other.</span></span>  
  
 <span data-ttu-id="766ed-111">Aksi takdirde gerektirebilecek hesaplamaları ifade edebilirsiniz bir `if-else` koşullu işleç kullanarak daha kısaca oluşturma.</span><span class="sxs-lookup"><span data-stu-id="766ed-111">You can express calculations that might otherwise require an `if-else` construction more concisely by using the conditional operator.</span></span> <span data-ttu-id="766ed-112">Örneğin, aşağıdaki kod önce kullanan bir `if` deyimi ve sonra bir tamsayı artı veya eksi olarak sınıflandırmak için koşullu bir işleç.</span><span class="sxs-lookup"><span data-stu-id="766ed-112">For example, the following code uses first an `if` statement and then a conditional operator to classify an integer as positive or negative.</span></span>  
  
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
  
 <span data-ttu-id="766ed-113">Koşullu işleç, sağa ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="766ed-113">The conditional operator is right-associative.</span></span> <span data-ttu-id="766ed-114">İfade `a ? b : c ? d : e` değerlendirmesinde `a ? b : (c ? d : e)`, olarak değil `(a ? b : c) ? d : e`.</span><span class="sxs-lookup"><span data-stu-id="766ed-114">The expression `a ? b : c ? d : e` is evaluated as `a ? b : (c ? d : e)`, not as `(a ? b : c) ? d : e`.</span></span>  
  
 <span data-ttu-id="766ed-115">Koşullu işleç aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="766ed-115">The conditional operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="766ed-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="766ed-116">Example</span></span>  
 [!code-csharp[csRefOperators#41](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="766ed-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="766ed-117">See Also</span></span>

- [<span data-ttu-id="766ed-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="766ed-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="766ed-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="766ed-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="766ed-120">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="766ed-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="766ed-121">if-else</span><span class="sxs-lookup"><span data-stu-id="766ed-121">if-else</span></span>](../../../csharp/language-reference/keywords/if-else.md)  
- <span data-ttu-id="766ed-122">[?. and ?[] İşleçleri](../../../csharp/language-reference/operators/null-conditional-operators.md)</span><span class="sxs-lookup"><span data-stu-id="766ed-122">[?. and ?[] Operators](../../../csharp/language-reference/operators/null-conditional-operators.md)</span></span>  
- [<span data-ttu-id="766ed-123">?? İşleç</span><span class="sxs-lookup"><span data-stu-id="766ed-123">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
