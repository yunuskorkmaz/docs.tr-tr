---
title: public (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 9bef5d076d9ab84aa15e2cdec2d176db8d1ac82b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171999"
---
# <a name="public-c-reference"></a><span data-ttu-id="d21e4-102">public (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d21e4-102">public (C# Reference)</span></span>
<span data-ttu-id="d21e4-103">`public` Sözcüktür türleri ve tür üyeleri için bir erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="d21e4-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="d21e4-104">Genel erişim en fazla izne sahip erişim düzeyi değil.</span><span class="sxs-lookup"><span data-stu-id="d21e4-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="d21e4-105">Bu örnekte olduğu gibi ortak üyelere erişme hiçbir kısıtlamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="d21e4-105">There are no restrictions on accessing public members, as in this example:</span></span>  
  
```csharp  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 <span data-ttu-id="d21e4-106">Bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) ve [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="d21e4-106">See [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d21e4-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="d21e4-107">Example</span></span>  
 <span data-ttu-id="d21e4-108">Aşağıdaki örnekte, iki sınıf bildirilir, `PointTest` ve `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="d21e4-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="d21e4-109">Genel üyeler `x` ve `y` , `PointTest` doğrudan erişilen `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="d21e4-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 <span data-ttu-id="d21e4-110">Değiştirirseniz `public` erişim düzeyini [özel](../../../csharp/language-reference/keywords/private.md) veya [korumalı](../../../csharp/language-reference/keywords/protected.md), hata iletisi alırsınız:</span><span class="sxs-lookup"><span data-stu-id="d21e4-110">If you change the `public` access level to [private](../../../csharp/language-reference/keywords/private.md) or [protected](../../../csharp/language-reference/keywords/protected.md), you will get the error message:</span></span>  
  
 <span data-ttu-id="d21e4-111">'PointTest.y' koruma düzeyi nedeniyle erişilemiyor.</span><span class="sxs-lookup"><span data-stu-id="d21e4-111">'PointTest.y' is inaccessible due to its protection level.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d21e4-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d21e4-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d21e4-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d21e4-113">See Also</span></span>  
 [<span data-ttu-id="d21e4-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d21e4-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d21e4-115">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d21e4-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d21e4-116">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="d21e4-116">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="d21e4-117">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d21e4-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d21e4-118">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="d21e4-118">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="d21e4-119">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="d21e4-119">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="d21e4-120">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="d21e4-120">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="d21e4-121">private</span><span class="sxs-lookup"><span data-stu-id="d21e4-121">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="d21e4-122">protected</span><span class="sxs-lookup"><span data-stu-id="d21e4-122">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="d21e4-123">internal</span><span class="sxs-lookup"><span data-stu-id="d21e4-123">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
