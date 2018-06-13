---
title: biçimindeki telefon numarasıdır. İşleci (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 088f1991cafa92a69e11ca14bd2d983b36c0e3ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33271035"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="132ca-103">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="132ca-103">.</span></span> <span data-ttu-id="132ca-104">İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="132ca-104">Operator (C# Reference)</span></span>
<span data-ttu-id="132ca-105">Nokta işleci (`.`) üye erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="132ca-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="132ca-106">Nokta işleci türü veya ad alanı üyesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="132ca-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="132ca-107">Örneğin, dot işleci, .NET Framework sınıf kitaplıkları içinde belirli yöntemler erişmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="132ca-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="132ca-108">Örneğin, aşağıdaki sınıf göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="132ca-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="132ca-109">Değişkeni `s` iki üyesi olan `a` ve `b`; erişmesine, nokta işlecini kullanın:</span><span class="sxs-lookup"><span data-stu-id="132ca-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="132ca-110">Nokta da ad alanı veya arabirim, örneğin, ait oldukları belirtin adları nitelenmiş adlar oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="132ca-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="132ca-111">Using yönergesi bazı ad niteliği isteğe bağlı yapar:</span><span class="sxs-lookup"><span data-stu-id="132ca-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="132ca-112">Ancak bir tanımlayıcı belirsiz olduğunda nitelenmelidir:</span><span class="sxs-lookup"><span data-stu-id="132ca-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="132ca-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="132ca-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="132ca-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="132ca-114">See Also</span></span>  
 [<span data-ttu-id="132ca-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="132ca-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="132ca-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="132ca-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="132ca-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="132ca-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
