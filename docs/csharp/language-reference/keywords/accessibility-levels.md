---
title: "Erişilebilirlik Düzeyleri (C# Başvurusu)"
ms.date: 12/06/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 816ee0fab3fae21bff2ffbfcbfe39d04dcf95025
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="fdf9f-102">Erişilebilirlik Düzeyleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fdf9f-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="fdf9f-103">Erişim değiştiricileri kullanmak [ortak](../../../csharp/language-reference/keywords/public.md), [korumalı](../../../csharp/language-reference/keywords/protected.md), [iç](../../../csharp/language-reference/keywords/internal.md), veya [özel](../../../csharp/language-reference/keywords/private.md)bildirilen aşağıdakilerden birini belirtmek için Erişilebilirlik düzeyleri üyeleri için.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-103">Use the access modifiers, [public](../../../csharp/language-reference/keywords/public.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), or [private](../../../csharp/language-reference/keywords/private.md), to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="fdf9f-104">Bildirilen erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="fdf9f-104">Declared accessibility</span></span>|<span data-ttu-id="fdf9f-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fdf9f-105">Meaning</span></span>|  
|----------------------------|-------------|  
|`public`|<span data-ttu-id="fdf9f-106">Erişim sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-106">Access is not restricted.</span></span>|  
|`protected`|<span data-ttu-id="fdf9f-107">Erişim sınıfı veya içeren sınıfından türetilen türler içeren sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|`internal`|<span data-ttu-id="fdf9f-108">Erişim geçerli derlemeye sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-108">Access is limited to the current assembly.</span></span>|  
|`protected internal`|<span data-ttu-id="fdf9f-109">Geçerli derleme veya içeren sınıfından türetilen türler için erişim sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|`private`|<span data-ttu-id="fdf9f-110">Erişim içeren türü ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-110">Access is limited to the containing type.</span></span>|  
|`private protected`|<span data-ttu-id="fdf9f-111">Erişim sınıfı veya geçerli derlemedeki içeren sınıfından türetilmiş türler içeren sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="fdf9f-112">C# 7.2 itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="fdf9f-113">Yalnızca bir erişim değiştiricisi izin verilen bir üye veya türü için dışında kullandığınızda `protected internal` veya `private protected` birleşimleri.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="fdf9f-114">Erişim değiştiricileri ad alanında bulunan izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="fdf9f-115">Ad alanları, hiçbir erişim kısıtlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="fdf9f-116">Üye bildirimi gerçekleştiği bağlamı bağlı olarak, yalnızca belirli bildirilen eriþebilirlik izin verilir.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="fdf9f-117">Herhangi bir erişim değiştiricisi üye bildiriminde belirtilmezse, varsayılan erişilebilirlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="fdf9f-118">Diğer türlerinde içe değil, üst düzey türleri yalnızca olabilir `internal` veya `public` erişilebilirlik.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="fdf9f-119">Bu tür için varsayılan erişilebilirlik olduğu `internal`.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="fdf9f-120">Diğer türleri üyeleri olan, iç içe geçmiş türler eriþebilirlik aşağıdaki tabloda gösterildiği gibi bildirilen.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="fdf9f-121">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="fdf9f-121">Members of</span></span>|<span data-ttu-id="fdf9f-122">Varsayılan üye erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="fdf9f-122">Default member accessibility</span></span>|<span data-ttu-id="fdf9f-123">Üyenin izin verilen bildirilen erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="fdf9f-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="fdf9f-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="fdf9f-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="fdf9f-126">İç içe geçmiş tür erişilebilirliğini bağlıdır, [erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md), üyenin bildirilen erişilebilirlik ve hemen kapsayan tür erişilebilirlik etki alanı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-126">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="fdf9f-127">Ancak, iç içe geçmiş tür erişilebilirlik etki alanı, kapsayan tür aşamaz.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="fdf9f-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="fdf9f-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="fdf9f-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fdf9f-129">See Also</span></span>  
 [<span data-ttu-id="fdf9f-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fdf9f-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fdf9f-131">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fdf9f-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fdf9f-132">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fdf9f-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="fdf9f-133">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="fdf9f-133">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="fdf9f-134">Erişilebilirlik etki alanı</span><span class="sxs-lookup"><span data-stu-id="fdf9f-134">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="fdf9f-135">Erişilebilirlik düzeylerinin kullanılmasındaki kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="fdf9f-135">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="fdf9f-136">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="fdf9f-136">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="fdf9f-137">Ortak</span><span class="sxs-lookup"><span data-stu-id="fdf9f-137">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="fdf9f-138">Özel</span><span class="sxs-lookup"><span data-stu-id="fdf9f-138">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="fdf9f-139">korumalı</span><span class="sxs-lookup"><span data-stu-id="fdf9f-139">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="fdf9f-140">İç</span><span class="sxs-lookup"><span data-stu-id="fdf9f-140">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
