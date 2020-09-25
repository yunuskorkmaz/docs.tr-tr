---
description: Erişim değiştiricileri-C# başvurusu
title: Erişim değiştiricileri-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: e941fc673c508f10863ee49b6544d6886bd594a3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168822"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="1f458-103">Erişim Değiştiricileri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1f458-103">Access Modifiers (C# Reference)</span></span>

<span data-ttu-id="1f458-104">Erişim değiştiriciler, bir üyenin veya bir türün belirtilen erişilebilirliğini belirtmek için kullanılan anahtar kelimelerdir.</span><span class="sxs-lookup"><span data-stu-id="1f458-104">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="1f458-105">Bu bölüm dört erişim değiştiricilerini tanıtır:</span><span class="sxs-lookup"><span data-stu-id="1f458-105">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="1f458-106">Aşağıdaki altı erişilebilirlik düzeyi erişim değiştiricilerini kullanarak belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="1f458-106">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="1f458-107">[`public`](public.md): Erişim kısıtlanmaz.</span><span class="sxs-lookup"><span data-stu-id="1f458-107">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="1f458-108">[`protected`](protected.md): Erişim, kapsayan sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f458-108">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="1f458-109">[`internal`](internal.md): Erişim geçerli derleme ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f458-109">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="1f458-110">[`protected internal`](protected-internal.md): Erişim, içeren sınıftan türetilmiş geçerli derleme veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f458-110">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="1f458-111">[`private`](private.md): Erişim, kapsayan tür ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f458-111">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="1f458-112">[`private protected`](private-protected.md): Erişim, geçerli derleme içindeki içeren sınıftan türetilmiş, kapsayan sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="1f458-112">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="1f458-113">Bu bölüm ayrıca şunları da tanıtır:</span><span class="sxs-lookup"><span data-stu-id="1f458-113">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="1f458-114">[Erişilebilirlik düzeyleri](./accessibility-levels.md): altı erişilebilirlik düzeyi tanımlamak için dört erişim değiştiricilerini kullanma.</span><span class="sxs-lookup"><span data-stu-id="1f458-114">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="1f458-115">[Erişilebilirlik etki alanı](./accessibility-domain.md): program bölümlerinde bir üyeye başvurulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1f458-115">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="1f458-116">[Erişilebilirlik düzeylerini kullanma kısıtlamaları](./restrictions-on-using-accessibility-levels.md): belirtilen erişilebilirlik düzeylerini kullanma kısıtlamalarının Özeti.</span><span class="sxs-lookup"><span data-stu-id="1f458-116">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f458-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f458-117">See also</span></span>

- [<span data-ttu-id="1f458-118">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1f458-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1f458-119">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1f458-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1f458-120">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1f458-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="1f458-121">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="1f458-121">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="1f458-122">Anahtar Sözcüklere Erişim</span><span class="sxs-lookup"><span data-stu-id="1f458-122">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="1f458-123">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="1f458-123">Modifiers</span></span>](index.md)
