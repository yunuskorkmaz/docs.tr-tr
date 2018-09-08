---
title: Erişim Değiştiricileri (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: ff313df9683dbc76bab684ff484b746ad05e065a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44195588"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="8b22e-102">Erişim Değiştiricileri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="8b22e-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="8b22e-103">Erişim değiştiricileri öğesinin bildirilen erişilebilirliği üyesi veya bir tür belirtmek için kullanılan anahtar sözcüklerdir.</span><span class="sxs-lookup"><span data-stu-id="8b22e-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="8b22e-104">Bu bölümde, dört erişim değiştiricilerini tanıtır:</span><span class="sxs-lookup"><span data-stu-id="8b22e-104">This section introduces the four access modifiers:</span></span>  
  
-   `public`
-   `protected`
-   `internal`
-   `private`
  
 <span data-ttu-id="8b22e-105">Erişim değiştiricilerini kullanarak aşağıdaki altı erişilebilirlik düzeyleri belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="8b22e-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="8b22e-106">[`public`](public.md): Erişim sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="8b22e-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="8b22e-107">[`protected`](protected.md): Erişim içeren sınıfı veya içeren sınıfından türetilen türler sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b22e-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="8b22e-108">[`internal`](internal.md): Geçerli derlemeye erişim sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b22e-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="8b22e-109">[`protected internal`](protected-internal.md): Geçerli derleme veya içeren sınıfından türetilen türler erişim sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b22e-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="8b22e-110">[`private`](private.md): Erişimi, kapsadığı tür için sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b22e-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="8b22e-111">[`private protected`](private-protected.md): Erişim içeren sınıfı veya geçerli derlemedeki içeren sınıfından türetilen türler sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="8b22e-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="8b22e-112">Bu bölümde Ayrıca aşağıdakileri sağlar:</span><span class="sxs-lookup"><span data-stu-id="8b22e-112">This section also introduces the following:</span></span>  
  
-   <span data-ttu-id="8b22e-113">[Erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md): altı düzeyde erişilebilirlik bildirmek için dört erişim değiştiricilerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="8b22e-113">[Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
-   <span data-ttu-id="8b22e-114">[Erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md): Burada, program bölümlerde üyesi başvurulabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="8b22e-114">[Accessibility Domain](../../../csharp/language-reference/keywords/accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
-   <span data-ttu-id="8b22e-115">[Erişilebilirlik düzeyleri kullanarak kısıtlamalar](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): bildirilen erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar özeti.</span><span class="sxs-lookup"><span data-stu-id="8b22e-115">[Restrictions on Using Accessibility Levels](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b22e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8b22e-116">See Also</span></span>  
- [<span data-ttu-id="8b22e-117">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="8b22e-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="8b22e-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8b22e-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="8b22e-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8b22e-119">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="8b22e-120">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="8b22e-120">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [<span data-ttu-id="8b22e-121">Erişim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="8b22e-121">Access Keywords</span></span>](../../../csharp/language-reference/keywords/access-keywords.md)  
- [<span data-ttu-id="8b22e-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="8b22e-122">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
