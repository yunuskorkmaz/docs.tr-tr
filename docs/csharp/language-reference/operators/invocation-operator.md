---
title: "() İşleci (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d62e6c93dcc69c892d4ca96ace3806cb1c8d989
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="8f89e-102">() İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8f89e-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="8f89e-103">Bir ifadeyi işlemlerin sırasını belirlemek için kullanılan ek olarak, parantez aşağıdaki görevleri gerçekleştirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="8f89e-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="8f89e-104">Atamaları belirtin veya türü dönüşümleri.</span><span class="sxs-lookup"><span data-stu-id="8f89e-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="8f89e-105">Yöntemler veya temsilciler çağırır.</span><span class="sxs-lookup"><span data-stu-id="8f89e-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="8f89e-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f89e-106">Remarks</span></span>  
 <span data-ttu-id="8f89e-107">Bir cast açıkça başka bir türden diğerine dönüştürme işleci çağırır; Bu tür bir dönüşüm işleci tanımlanan dönüştürme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="8f89e-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="8f89e-108">Bir dönüşüm işleci tanımlama için bkz: [açık](../../../csharp/language-reference/keywords/explicit.md) ve [örtük](../../../csharp/language-reference/keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="8f89e-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="8f89e-109">`()` İşleci olamaz aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="8f89e-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="8f89e-110">Daha fazla bilgi için bkz: [atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="8f89e-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="8f89e-111">Cast ifadesi belirsiz sözdizimine yol açabilir.</span><span class="sxs-lookup"><span data-stu-id="8f89e-111">A cast expression could lead to ambiguous syntax.</span></span> <span data-ttu-id="8f89e-112">Örneğin, ifade `(x)–y` ya da bir cast ifadesi (– tür x y cast) veya bir ADDITIVE olarak yorumlanabilecek x – değeri hesaplar ve parantez içine alınmış ifade ile birlikte ifade y.</span><span class="sxs-lookup"><span data-stu-id="8f89e-112">For example, the expression `(x)–y` could be either interpreted as a cast expression (a cast of –y to type x) or as an additive expression combined with a parenthesized expression, which computes the value x – y.</span></span>  
  
 <span data-ttu-id="8f89e-113">Yöntem çağırma hakkında daha fazla bilgi için bkz: [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="8f89e-113">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="8f89e-114">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="8f89e-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8f89e-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8f89e-115">See Also</span></span>  
 [<span data-ttu-id="8f89e-116">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8f89e-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8f89e-117">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8f89e-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8f89e-118">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="8f89e-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
