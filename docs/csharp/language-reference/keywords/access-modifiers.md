---
title: Erişim değiştiricileri - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: d87ea1ff18c4697a2c04f22cbf67720f21cbf459
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59118137"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="3fac1-102">Erişim Değiştiricileri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="3fac1-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="3fac1-103">Erişim değiştiricileri öğesinin bildirilen erişilebilirliği üyesi veya bir tür belirtmek için kullanılan anahtar sözcüklerdir.</span><span class="sxs-lookup"><span data-stu-id="3fac1-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="3fac1-104">Bu bölümde, dört erişim değiştiricilerini tanıtır:</span><span class="sxs-lookup"><span data-stu-id="3fac1-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="3fac1-105">Erişim değiştiricilerini kullanarak aşağıdaki altı erişilebilirlik düzeyleri belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="3fac1-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="3fac1-106">[`public`](public.md): Erişim sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="3fac1-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="3fac1-107">[`protected`](protected.md): Erişim içeren sınıfı veya içeren sınıfından türetilen türler sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fac1-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="3fac1-108">[`internal`](internal.md): Geçerli derleme için erişim sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fac1-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="3fac1-109">[`protected internal`](protected-internal.md): Geçerli derleme veya içeren sınıfından türetilen türler için erişim sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fac1-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="3fac1-110">[`private`](private.md): Erişimi, kapsadığı tür için sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fac1-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="3fac1-111">[`private protected`](private-protected.md): Erişim içeren sınıfı veya geçerli derlemedeki içeren sınıfından türetilen türler sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="3fac1-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="3fac1-112">Bu bölümde Ayrıca aşağıdakileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="3fac1-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="3fac1-113">[Erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md): Altı düzeyde erişilebilirlik bildirmek için dört erişim değiştiricilerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="3fac1-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="3fac1-114">[Erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md): Burada, program bölümlerde üyesi başvurulabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="3fac1-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="3fac1-115">[Erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): Erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar özetini bildirilir.</span><span class="sxs-lookup"><span data-stu-id="3fac1-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fac1-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3fac1-116">See also</span></span>

- [<span data-ttu-id="3fac1-117">C# Başvurusu</span><span class="sxs-lookup"><span data-stu-id="3fac1-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="3fac1-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3fac1-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3fac1-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3fac1-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="3fac1-120">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="3fac1-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="3fac1-121">Erişim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3fac1-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)
- [<span data-ttu-id="3fac1-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="3fac1-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
