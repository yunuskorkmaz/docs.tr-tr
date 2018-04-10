---
title: . İşleci (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2bb636bc110f57ace9a824a43afdd86246ed0a5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3c488-103">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="3c488-103">.</span></span> <span data-ttu-id="3c488-104">İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3c488-104">Operator (C# Reference)</span></span>
<span data-ttu-id="3c488-105">Nokta işleci (`.`) üye erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c488-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="3c488-106">Nokta işleci türü veya ad alanı üyesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c488-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="3c488-107">Örneğin, dot işleci, .NET Framework sınıf kitaplıkları içinde belirli yöntemler erişmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="3c488-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="3c488-108">Örneğin, aşağıdaki sınıf göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="3c488-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="3c488-109">Değişkeni `s` iki üyesi olan `a` ve `b`; erişmesine, nokta işlecini kullanın:</span><span class="sxs-lookup"><span data-stu-id="3c488-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="3c488-110">Nokta da ad alanı veya arabirim, örneğin, ait oldukları belirtin adları nitelenmiş adlar oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3c488-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="3c488-111">Using yönergesi bazı ad niteliği isteğe bağlı yapar:</span><span class="sxs-lookup"><span data-stu-id="3c488-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="3c488-112">Ancak bir tanımlayıcı belirsiz olduğunda nitelenmelidir:</span><span class="sxs-lookup"><span data-stu-id="3c488-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="3c488-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="3c488-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3c488-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c488-114">See Also</span></span>  
 [<span data-ttu-id="3c488-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="3c488-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3c488-116">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3c488-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3c488-117">C# işleçleri</span><span class="sxs-lookup"><span data-stu-id="3c488-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
