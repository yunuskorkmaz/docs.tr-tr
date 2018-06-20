---
title: () İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 82dfc2e11d6a8a025aa9b7557255a13b69ffa508
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208437"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="56349-102">() İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="56349-102">() Operator (C# Reference)</span></span>
<span data-ttu-id="56349-103">Bir ifadeyi işlemlerin sırasını belirlemek için kullanılan ek olarak, parantez aşağıdaki görevleri gerçekleştirmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="56349-103">In addition to being used to specify the order of operations in an expression, parentheses are used to perform the following tasks:</span></span>  
  
1.  <span data-ttu-id="56349-104">Atamaları belirtin veya türü dönüşümleri.</span><span class="sxs-lookup"><span data-stu-id="56349-104">Specify casts, or type conversions.</span></span>  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  <span data-ttu-id="56349-105">Yöntemler veya temsilciler çağırır.</span><span class="sxs-lookup"><span data-stu-id="56349-105">Invoke methods or delegates.</span></span>  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="56349-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="56349-106">Remarks</span></span>  
 <span data-ttu-id="56349-107">Bir cast açıkça başka bir türden diğerine dönüştürme işleci çağırır; Bu tür bir dönüşüm işleci tanımlanan dönüştürme başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="56349-107">A cast explicitly invokes the conversion operator from one type to another; the cast fails if no such conversion operator is defined.</span></span> <span data-ttu-id="56349-108">Bir dönüşüm işleci tanımlama için bkz: [açık](../../../csharp/language-reference/keywords/explicit.md) ve [örtük](../../../csharp/language-reference/keywords/implicit.md).</span><span class="sxs-lookup"><span data-stu-id="56349-108">To define a conversion operator, see [explicit](../../../csharp/language-reference/keywords/explicit.md) and [implicit](../../../csharp/language-reference/keywords/implicit.md).</span></span>  
  
 <span data-ttu-id="56349-109">`()` İşleci olamaz aşırı yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="56349-109">The `()` operator cannot be overloaded.</span></span>  
  
 <span data-ttu-id="56349-110">Daha fazla bilgi için bkz: [atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="56349-110">For more information, see [Casting and Type Conversions](../../../csharp/programming-guide/types/casting-and-type-conversions.md).</span></span>  
  
 <span data-ttu-id="56349-111">Yöntem çağırma hakkında daha fazla bilgi için bkz: [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md).</span><span class="sxs-lookup"><span data-stu-id="56349-111">For more information about method invocation, see [Methods](../../../csharp/programming-guide/classes-and-structs/methods.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="56349-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="56349-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="56349-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="56349-113">See Also</span></span>  
 [<span data-ttu-id="56349-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="56349-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="56349-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="56349-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="56349-116">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="56349-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
