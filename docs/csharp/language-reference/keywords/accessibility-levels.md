---
title: "Erişilebilirlik Düzeyleri (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 77124554d7a0b38414e154e024aceddbfffcfbd4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="65f0d-102">Erişilebilirlik Düzeyleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="65f0d-102">Accessibility Levels (C# Reference)</span></span>
<span data-ttu-id="65f0d-103">Erişim değiştiricileri kullanmak [ortak](../../../csharp/language-reference/keywords/public.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), veya [özel](../../../csharp/language-reference/keywords/private.md)bildirilen aşağıdakilerden birini belirtmek için Erişilebilirlik düzeyleri üyeleri için.</span><span class="sxs-lookup"><span data-stu-id="65f0d-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="65f0d-104">Bildirilen erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="65f0d-104">Declared accessibility</span></span>|<span data-ttu-id="65f0d-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="65f0d-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="65f0d-106">Erişim sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="65f0d-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="65f0d-107">Erişim sınıfı veya içeren sınıfından türetilen türler içeren sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="65f0d-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="65f0d-108">Erişim geçerli derlemeye sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="65f0d-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="65f0d-109">Geçerli derleme veya içeren sınıfından türetilen türler için erişim sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="65f0d-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="65f0d-110">Erişim içeren türü ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="65f0d-110">Access is limited to the containing type.</span></span>|  
|`private protected`|<span data-ttu-id="65f0d-111">Erişim sınıfı veya geçerli derlemedeki içeren sınıfından türetilmiş türler içeren sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="65f0d-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span>|  
  
 <span data-ttu-id="65f0d-112">Yalnızca bir erişim değiştiricisi izin verilen bir üye veya türü için dışında kullandığınızda `protected internal` veya `private protected` birleşimleri.</span><span class="sxs-lookup"><span data-stu-id="65f0d-112">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="65f0d-113">Erişim değiştiricileri ad alanında bulunan izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="65f0d-113">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="65f0d-114">Ad alanları, hiçbir erişim kısıtlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="65f0d-114">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="65f0d-115">Üye bildirimi gerçekleştiği bağlamı bağlı olarak, yalnızca belirli bildirilen eriþebilirlik izin verilir.</span><span class="sxs-lookup"><span data-stu-id="65f0d-115">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="65f0d-116">Herhangi bir erişim değiştiricisi üye bildiriminde belirtilmezse, varsayılan erişilebilirlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="65f0d-116">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="65f0d-117">Diğer türlerinde içe değil, üst düzey türleri yalnızca olabilir `internal` veya `public` erişilebilirlik.</span><span class="sxs-lookup"><span data-stu-id="65f0d-117">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="65f0d-118">Bu tür için varsayılan erişilebilirlik olduğu `internal`.</span><span class="sxs-lookup"><span data-stu-id="65f0d-118">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="65f0d-119">Diğer türleri üyeleri olan, iç içe geçmiş türler eriþebilirlik aşağıdaki tabloda gösterildiği gibi bildirilen.</span><span class="sxs-lookup"><span data-stu-id="65f0d-119">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="65f0d-120">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="65f0d-120">Members of</span></span>|<span data-ttu-id="65f0d-121">Varsayılan üye erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="65f0d-121">Default member accessibility</span></span>|<span data-ttu-id="65f0d-122">Üyenin izin verilen bildirilen erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="65f0d-122">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="65f0d-123">Yok.</span><span class="sxs-lookup"><span data-stu-id="65f0d-123">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="65f0d-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="65f0d-124">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="65f0d-125">İç içe geçmiş tür erişilebilirliğini bağlıdır, [erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md), üyenin bildirilen erişilebilirlik ve hemen kapsayan tür erişilebilirlik etki alanı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="65f0d-125">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="65f0d-126">Ancak, iç içe geçmiş tür erişilebilirlik etki alanı, kapsayan tür aşamaz.</span><span class="sxs-lookup"><span data-stu-id="65f0d-126">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="65f0d-127">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="65f0d-127">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65f0d-128">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65f0d-128">See Also</span></span>  
 [<span data-ttu-id="65f0d-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="65f0d-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="65f0d-130">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="65f0d-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="65f0d-131">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="65f0d-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="65f0d-132">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="65f0d-132">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="65f0d-133">Erişilebilirlik etki alanı</span><span class="sxs-lookup"><span data-stu-id="65f0d-133">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="65f0d-134">Erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="65f0d-134">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="65f0d-135">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="65f0d-135">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="65f0d-136">Ortak</span><span class="sxs-lookup"><span data-stu-id="65f0d-136">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="65f0d-137">Özel</span><span class="sxs-lookup"><span data-stu-id="65f0d-137">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="65f0d-138">korumalı</span><span class="sxs-lookup"><span data-stu-id="65f0d-138">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="65f0d-139">İç</span><span class="sxs-lookup"><span data-stu-id="65f0d-139">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
