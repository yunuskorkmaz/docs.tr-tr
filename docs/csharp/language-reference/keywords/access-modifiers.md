---
title: Erişim değiştiricileri- C# başvuru
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 5568d79c4a13b7b0db5a46bb4ebb2168ea66a2c9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606100"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="cf8a6-102">Erişim Değiştiricileri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="cf8a6-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="cf8a6-103">Erişim değiştiriciler, bir üyenin veya bir türün belirtilen erişilebilirliğini belirtmek için kullanılan anahtar kelimelerdir.</span><span class="sxs-lookup"><span data-stu-id="cf8a6-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="cf8a6-104">Bu bölüm dört erişim değiştiricilerini tanıtır:</span><span class="sxs-lookup"><span data-stu-id="cf8a6-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="cf8a6-105">Aşağıdaki altı erişilebilirlik düzeyi erişim değiştiricilerini kullanarak belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="cf8a6-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="cf8a6-106">[`public`](public.md): Erişim kısıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="cf8a6-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="cf8a6-107">[`protected`](protected.md): Erişim, kapsayan sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="cf8a6-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="cf8a6-108">[`internal`](internal.md): Erişim, geçerli derleme ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="cf8a6-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="cf8a6-109">[`protected internal`](protected-internal.md): Erişim, geçerli derleme veya kapsayan sınıftan türetilmiş türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="cf8a6-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="cf8a6-110">[`private`](private.md): Erişim, kapsayan tür ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="cf8a6-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="cf8a6-111">[`private protected`](private-protected.md): Erişim, geçerli derleme içindeki içeren sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="cf8a6-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="cf8a6-112">Bu bölüm ayrıca şunları da tanıtır:</span><span class="sxs-lookup"><span data-stu-id="cf8a6-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="cf8a6-113">[Erişilebilirlik düzeyleri](./accessibility-levels.md): Altı erişilebilirlik düzeyi tanımlamak için dört erişim değiştiricilerini kullanma.</span><span class="sxs-lookup"><span data-stu-id="cf8a6-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="cf8a6-114">[Erişilebilirlik etki alanı](./accessibility-domain.md): Program bölümlerinde, bir üyeye başvurulabileceği yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf8a6-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="cf8a6-115">[Erişilebilirlik düzeylerini kullanma kısıtlamaları](./restrictions-on-using-accessibility-levels.md): Tanımlanan erişilebilirlik düzeylerini kullanma kısıtlamalarının Özeti.</span><span class="sxs-lookup"><span data-stu-id="cf8a6-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf8a6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf8a6-116">See also</span></span>

- [<span data-ttu-id="cf8a6-117">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="cf8a6-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cf8a6-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="cf8a6-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cf8a6-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="cf8a6-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="cf8a6-120">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="cf8a6-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="cf8a6-121">Erişim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="cf8a6-121">Access Keywords</span></span>](./access-keywords.md)
- [<span data-ttu-id="cf8a6-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="cf8a6-122">Modifiers</span></span>](./modifiers.md)
