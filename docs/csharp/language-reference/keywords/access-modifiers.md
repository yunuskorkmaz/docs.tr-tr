---
title: Erişim değiştiricileri- C# başvuru
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 754949e42771de30cc2dce7e4e610f70ada6dfd4
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713852"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="af5da-102">Erişim Değiştiricileri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="af5da-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="af5da-103">Erişim değiştiriciler, bir üyenin veya bir türün belirtilen erişilebilirliğini belirtmek için kullanılan anahtar kelimelerdir.</span><span class="sxs-lookup"><span data-stu-id="af5da-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="af5da-104">Bu bölüm dört erişim değiştiricilerini tanıtır:</span><span class="sxs-lookup"><span data-stu-id="af5da-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="af5da-105">Aşağıdaki altı erişilebilirlik düzeyi erişim değiştiricilerini kullanarak belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="af5da-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="af5da-106">[`public`](public.md): erişim kısıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="af5da-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="af5da-107">[`protected`](protected.md): erişim, kapsayan sınıftan türetilmiş olan sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="af5da-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="af5da-108">[`internal`](internal.md): erişim geçerli derleme ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="af5da-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="af5da-109">[`protected internal`](protected-internal.md): erişim, geçerli derleme veya içeren sınıftan türetilmiş türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="af5da-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="af5da-110">[`private`](private.md): erişim, kapsayan tür ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="af5da-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="af5da-111">[`private protected`](private-protected.md): erişim, geçerli derleme içindeki içeren sınıftan türetilmiş içeren sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="af5da-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="af5da-112">Bu bölüm ayrıca şunları da tanıtır:</span><span class="sxs-lookup"><span data-stu-id="af5da-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="af5da-113">[Erişilebilirlik düzeyleri](./accessibility-levels.md): altı erişilebilirlik düzeyi tanımlamak için dört erişim değiştiricilerini kullanma.</span><span class="sxs-lookup"><span data-stu-id="af5da-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="af5da-114">[Erişilebilirlik etki alanı](./accessibility-domain.md): program bölümlerinde bir üyeye başvurulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="af5da-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="af5da-115">[Erişilebilirlik düzeylerini kullanma kısıtlamaları](./restrictions-on-using-accessibility-levels.md): belirtilen erişilebilirlik düzeylerini kullanma kısıtlamalarının Özeti.</span><span class="sxs-lookup"><span data-stu-id="af5da-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af5da-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af5da-116">See also</span></span>

- [<span data-ttu-id="af5da-117">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="af5da-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="af5da-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="af5da-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="af5da-119">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="af5da-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="af5da-120">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="af5da-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="af5da-121">Erişim Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="af5da-121">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="af5da-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="af5da-122">Modifiers</span></span>](index.md)
