---
title: Erişim Değiştiriciler - C# Başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- access modifiers [C#]
ms.assetid: 61c3fa51-c00f-48cb-9b49-c805dedd62d7
ms.openlocfilehash: 754949e42771de30cc2dce7e4e610f70ada6dfd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713852"
---
# <a name="access-modifiers-c-reference"></a><span data-ttu-id="b5c57-102">Erişim Değiştiricileri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="b5c57-102">Access Modifiers (C# Reference)</span></span>
<span data-ttu-id="b5c57-103">Erişim değiştiriciler, bir üyenin veya bir türün bildirilen erişilebilirliğini belirtmek için kullanılan anahtar kelimelerdir.</span><span class="sxs-lookup"><span data-stu-id="b5c57-103">Access modifiers are keywords used to specify the declared accessibility of a member or a type.</span></span> <span data-ttu-id="b5c57-104">Bu bölümde dört erişim değiştiriciler tanıtıyor:</span><span class="sxs-lookup"><span data-stu-id="b5c57-104">This section introduces the four access modifiers:</span></span>  
  
- `public`
- `protected`
- `internal`
- `private`
  
 <span data-ttu-id="b5c57-105">Aşağıdaki altı erişilebilirlik düzeyi erişim değiştiriciler kullanılarak belirtilebilir:</span><span class="sxs-lookup"><span data-stu-id="b5c57-105">The following six accessibility levels can be specified using the access modifiers:</span></span>  
  
- <span data-ttu-id="b5c57-106">[`public`](public.md): Erişim kısıtlanmaz.</span><span class="sxs-lookup"><span data-stu-id="b5c57-106">[`public`](public.md): Access is not restricted.</span></span>  
  
- <span data-ttu-id="b5c57-107">[`protected`](protected.md): Erişim, içeren sınıf veya içeren sınıftan türetilen türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5c57-107">[`protected`](protected.md): Access is limited to the containing class or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="b5c57-108">[`internal`](internal.md): Erişim geçerli derleme ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5c57-108">[`internal`](internal.md): Access is limited to the current assembly.</span></span>  
  
- <span data-ttu-id="b5c57-109">[`protected internal`](protected-internal.md): Erişim, geçerli derleme yle veya içeren sınıftan türetilen türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5c57-109">[`protected internal`](protected-internal.md): Access is limited to the current assembly or types derived from the containing class.</span></span>  
  
- <span data-ttu-id="b5c57-110">[`private`](private.md): Erişim içeren türle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5c57-110">[`private`](private.md): Access is limited to the containing type.</span></span>  

- <span data-ttu-id="b5c57-111">[`private protected`](private-protected.md): Erişim, geçerli derleme içinde içeren sınıftan türetilen sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5c57-111">[`private protected`](private-protected.md): Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>  
  
 <span data-ttu-id="b5c57-112">Bu bölümde ayrıca aşağıdakileri tanıtın:</span><span class="sxs-lookup"><span data-stu-id="b5c57-112">This section also introduces the following:</span></span>  
  
- <span data-ttu-id="b5c57-113">[Erişilebilirlik Düzeyleri](./accessibility-levels.md): Altı erişilebilirlik düzeyi bildirmek için dört erişim değiştiricisi kullanma.</span><span class="sxs-lookup"><span data-stu-id="b5c57-113">[Accessibility Levels](./accessibility-levels.md): Using the four access modifiers to declare six levels of accessibility.</span></span>  
  
- <span data-ttu-id="b5c57-114">[Erişilebilirlik Etki Alanı](./accessibility-domain.md): Program bölümlerinde bir üyenin başvurulabileceği yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="b5c57-114">[Accessibility Domain](./accessibility-domain.md): Specifies where, in the program sections, a member can be referenced.</span></span>  
  
- <span data-ttu-id="b5c57-115">[Erişilebilirlik Düzeylerini Kullanma Kısıtlamaları](./restrictions-on-using-accessibility-levels.md): Bildirilen erişilebilirlik düzeylerini kullanma kısıtlamalarının özeti.</span><span class="sxs-lookup"><span data-stu-id="b5c57-115">[Restrictions on Using Accessibility Levels](./restrictions-on-using-accessibility-levels.md): A summary of the restrictions on using declared accessibility levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5c57-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b5c57-116">See also</span></span>

- [<span data-ttu-id="b5c57-117">C# Referans</span><span class="sxs-lookup"><span data-stu-id="b5c57-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b5c57-118">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="b5c57-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b5c57-119">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="b5c57-119">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="b5c57-120">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="b5c57-120">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="b5c57-121">Anahtar Sözcüklere Erişim</span><span class="sxs-lookup"><span data-stu-id="b5c57-121">Access Keywords</span></span>](base.md)
- [<span data-ttu-id="b5c57-122">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="b5c57-122">Modifiers</span></span>](index.md)
