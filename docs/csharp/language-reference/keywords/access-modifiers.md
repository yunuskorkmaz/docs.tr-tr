---
title: "Erişim Değiştiricileri (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23f99d0925aefde7ef43888d16e888a0943dfc21
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="dd91b-102">Erişim Değiştiricileri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="dd91b-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="dd91b-103">Erişim değiştiricileri anahtar sözcükler bildirilen erişilebilirlik üyesi veya bir türü belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dd91b-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="dd91b-104">Bu bölümde, dört erişim değiştiricileri sunar:</span><span class="sxs-lookup"><span data-stu-id="dd91b-104">This section introduces the four access modifiers:</span></span>  
  
-   [<span data-ttu-id="dd91b-105">Ortak</span><span class="sxs-lookup"><span data-stu-id="dd91b-105">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
  
-   [<span data-ttu-id="dd91b-106">korumalı</span><span class="sxs-lookup"><span data-stu-id="dd91b-106">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
  
-   [<span data-ttu-id="dd91b-107">İç</span><span class="sxs-lookup"><span data-stu-id="dd91b-107">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
  
-   [<span data-ttu-id="dd91b-108">Özel</span><span class="sxs-lookup"><span data-stu-id="dd91b-108">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
  
 <span data-ttu-id="dd91b-109">Erişim değiştiricileri kullanarak aşağıdaki altı erişilebilirlik düzeyleri belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="dd91b-109">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
 <span data-ttu-id="dd91b-110">`public`: Erişim sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="dd91b-110">`public`: Access is not restricted.</span></span>  
  
 <span data-ttu-id="dd91b-111">`protected`: Erişim sınıfı veya içeren sınıfından türetilen türler içeren sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="dd91b-111">`protected`: Access is limited to the containing class or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="dd91b-112">`internal`: Geçerli derlemeye erişim sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="dd91b-112">`internal`: Access is limited to the current assembly.</span></span>  
  
 <span data-ttu-id="dd91b-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): Geçerli derleme ya da içeren sınıfından türetilen türler erişim sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="dd91b-113">[`protected internal`](../../../csharp/language-reference/keywords/protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
 <span data-ttu-id="dd91b-114">`private`: Erişim içeren türü ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="dd91b-114">`private`: Access is limited to the containing type.</span></span>  

 <span data-ttu-id="dd91b-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): Erişim sınıfı veya geçerli derlemedeki içeren sınıfından türetilmiş türler içeren sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="dd91b-115">[`private protected`](../../../csharp/language-reference/keywords/private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="dd91b-116">Bu bölümde ayrıca aşağıdaki sunar:</span><span class="sxs-lookup"><span data-stu-id="dd91b-116">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="dd91b-117">[Erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md): erişilebilirlik altı düzeylerini bildirmek için dört erişim değiştiricileri kullanma.</span><span class="sxs-lookup"><span data-stu-id="dd91b-117">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="dd91b-118">[Erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md): program bölümlerde üyesi olduğu, başvurulabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="dd91b-118">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="dd91b-119">[Erişilebilirlik düzeyleri kullanarak kısıtlamalar](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar özetini bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="dd91b-119">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd91b-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dd91b-120">See Also</span></span>  
 [<span data-ttu-id="dd91b-121">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="dd91b-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="dd91b-122">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dd91b-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="dd91b-123">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="dd91b-123">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="dd91b-124">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="dd91b-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="dd91b-125">Anahtar sözcüklere erişim</span><span class="sxs-lookup"><span data-stu-id="dd91b-125">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="dd91b-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="dd91b-126">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
