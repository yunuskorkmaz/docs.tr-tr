---
title: "public (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords: public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 197ef4a2a8544d439b0c34ec14bb7752b760ea06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="public-c-reference"></a><span data-ttu-id="13eb8-102">public (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="13eb8-102">public (C# Reference)</span></span>
<span data-ttu-id="13eb8-103">`public` Sözcüktür türleri ve tür üyeleri için bir erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="13eb8-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="13eb8-104">Genel erişim en fazla izne sahip erişim düzeyi değil.</span><span class="sxs-lookup"><span data-stu-id="13eb8-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="13eb8-105">Bu örnekte olduğu gibi ortak üyelere erişme hiçbir kısıtlamaları vardır:</span><span class="sxs-lookup"><span data-stu-id="13eb8-105">There are no restrictions on accessing public members, as in this example:</span></span>  
  
```  
class SampleClass  
{  
    public int x; // No access restrictions.  
}  
```  
  
 <span data-ttu-id="13eb8-106">Bkz: [erişim değiştiricileri](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) ve [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md) daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="13eb8-106">See [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md) for more information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13eb8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="13eb8-107">Example</span></span>  
 <span data-ttu-id="13eb8-108">Aşağıdaki örnekte, iki sınıf bildirilir, `PointTest` ve `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="13eb8-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="13eb8-109">Genel üyeler `x` ve `y` , `PointTest` doğrudan erişilen `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="13eb8-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#13](../../../csharp/language-reference/keywords/codesnippet/CSharp/public_1.cs)]  
  
 <span data-ttu-id="13eb8-110">Değiştirirseniz `public` erişim düzeyini [özel](../../../csharp/language-reference/keywords/private.md) veya [korumalı](../../../csharp/language-reference/keywords/protected.md), hata iletisi alırsınız:</span><span class="sxs-lookup"><span data-stu-id="13eb8-110">If you change the `public` access level to [private](../../../csharp/language-reference/keywords/private.md) or [protected](../../../csharp/language-reference/keywords/protected.md), you will get the error message:</span></span>  
  
 <span data-ttu-id="13eb8-111">'PointTest.y' koruma düzeyi nedeniyle erişilemiyor.</span><span class="sxs-lookup"><span data-stu-id="13eb8-111">'PointTest.y' is inaccessible due to its protection level.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="13eb8-112">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="13eb8-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="13eb8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13eb8-113">See Also</span></span>  
 [<span data-ttu-id="13eb8-114">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="13eb8-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="13eb8-115">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="13eb8-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="13eb8-116">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="13eb8-116">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="13eb8-117">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="13eb8-117">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="13eb8-118">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="13eb8-118">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="13eb8-119">Erişilebilirlik düzeyleri</span><span class="sxs-lookup"><span data-stu-id="13eb8-119">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="13eb8-120">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="13eb8-120">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="13eb8-121">Özel</span><span class="sxs-lookup"><span data-stu-id="13eb8-121">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="13eb8-122">korumalı</span><span class="sxs-lookup"><span data-stu-id="13eb8-122">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="13eb8-123">İç</span><span class="sxs-lookup"><span data-stu-id="13eb8-123">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
