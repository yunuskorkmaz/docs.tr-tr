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
ms.openlocfilehash: a092c1a916e3dc4bf6d96660c532540945e57554
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520714"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="26921-103">biçimindeki telefon numarasıdır.</span><span class="sxs-lookup"><span data-stu-id="26921-103">.</span></span> <span data-ttu-id="26921-104">İşleci (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="26921-104">Operator (C# Reference)</span></span>
<span data-ttu-id="26921-105">Nokta işleci (`.`) üye erişimi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26921-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="26921-106">Dot işleci, bir tür veya ad alanı üyesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="26921-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="26921-107">Örneğin, nokta işleci, .NET Framework sınıf kitaplıkları belirli yöntemlerinde erişmek için kullanılır:</span><span class="sxs-lookup"><span data-stu-id="26921-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="26921-108">Örneğin, aşağıdaki sınıf göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="26921-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="26921-109">Değişken `s` iki üyesi olan `a` ve `b`; bunlara erişmek için nokta işlecini kullanın:</span><span class="sxs-lookup"><span data-stu-id="26921-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="26921-110">Nokta ad alanı veya arabirimi, örneğin, ait oldukları belirten adlarının tam adları oluşturmak için de kullanılır.</span><span class="sxs-lookup"><span data-stu-id="26921-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="26921-111">Using yönergesi bazı ad niteliği isteğe bağlı yapar:</span><span class="sxs-lookup"><span data-stu-id="26921-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="26921-112">Ancak, bir tanımlayıcı belirsiz olduğunda nitelenmelidir:</span><span class="sxs-lookup"><span data-stu-id="26921-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="26921-113">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="26921-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="26921-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="26921-114">See Also</span></span>

- [<span data-ttu-id="26921-115">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="26921-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="26921-116">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="26921-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="26921-117">C# İşleçleri</span><span class="sxs-lookup"><span data-stu-id="26921-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
