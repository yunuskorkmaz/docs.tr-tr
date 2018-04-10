---
title: Erişim Değiştiricileri (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d63cf724a2364059e5f3327254a9ec95f7493e5e
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="72912-102">Erişim Değiştiricileri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="72912-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="72912-103">Erişim değiştiricileri anahtar sözcükler bildirilen erişilebilirlik üyesi veya bir türü belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="72912-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="72912-104">Bu bölümde, dört erişim değiştiricileri sunar:</span><span class="sxs-lookup"><span data-stu-id="72912-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="72912-105">Erişim değiştiricileri kullanarak aşağıdaki altı erişilebilirlik düzeyleri belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="72912-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="72912-106">[`public`](public.md): Erişim sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="72912-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="72912-107">[`protected`](protected.md): Erişim sınıfı veya içeren sınıfından türetilen türler içeren sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="72912-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="72912-108">[`internal`](internal.md): Geçerli derlemeye erişim sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="72912-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="72912-109">[`protected internal`](protected-internal.md): Geçerli derleme ya da içeren sınıfından türetilen türler erişim sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="72912-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="72912-110">[`private`](private.md): Erişim içeren türü ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="72912-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="72912-111">[`private protected`](private-protected.md): Erişim sınıfı veya geçerli derlemedeki içeren sınıfından türetilmiş türler içeren sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="72912-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="72912-112">Bu bölümde ayrıca aşağıdaki sunar:</span><span class="sxs-lookup"><span data-stu-id="72912-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="72912-113">[Erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md): erişilebilirlik altı düzeylerini bildirmek için dört erişim değiştiricileri kullanma.</span><span class="sxs-lookup"><span data-stu-id="72912-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="72912-114">[Erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md): program bölümlerde üyesi olduğu, başvurulabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="72912-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="72912-115">[Erişilebilirlik düzeyleri kullanarak kısıtlamalar](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar özetini bildirilmiş.</span><span class="sxs-lookup"><span data-stu-id="72912-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72912-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72912-116">See Also</span></span>  
 [<span data-ttu-id="72912-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="72912-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="72912-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="72912-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="72912-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="72912-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="72912-120">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="72912-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="72912-121">Erişim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="72912-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
 [<span data-ttu-id="72912-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="72912-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
