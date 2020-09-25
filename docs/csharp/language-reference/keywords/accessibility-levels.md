---
description: Erişilebilirlik düzeyleri-C# başvurusu
title: Erişilebilirlik düzeyleri-C# başvurusu
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 6e1a5bddc0d40b0b62c7b07dbc6b4134a3447a95
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91168796"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="95a81-103">Erişilebilirlik Düzeyleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="95a81-103">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="95a81-104">`public` `protected` `internal` `private` Üyeler için aşağıdaki tanımlanmış erişilebilirlik düzeylerinden birini belirtmek için,,, veya erişim değiştiricilerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="95a81-104">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="95a81-105">Tanımlanan erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="95a81-105">Declared accessibility</span></span>|<span data-ttu-id="95a81-106">Anlamı</span><span class="sxs-lookup"><span data-stu-id="95a81-106">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="95a81-107">Erişim kısıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="95a81-107">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="95a81-108">Erişim, kapsayan sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="95a81-108">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="95a81-109">Erişim, geçerli derleme ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="95a81-109">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="95a81-110">Erişim, geçerli derleme veya kapsayan sınıftan türetilmiş türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="95a81-110">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="95a81-111">Erişim, kapsayan tür ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="95a81-111">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="95a81-112">Erişim, geçerli derleme içindeki içeren sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="95a81-112">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="95a81-113">C# 7,2 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="95a81-113">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="95a81-114">Veya kombinasyonlarını kullandığınızda, bir üye veya tür için yalnızca bir erişim değiştiricisine izin verilir `protected internal` `private protected` .</span><span class="sxs-lookup"><span data-stu-id="95a81-114">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="95a81-115">Ad alanlarında erişim değiştiricilerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="95a81-115">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="95a81-116">Ad alanlarının erişim kısıtlamaları yoktur.</span><span class="sxs-lookup"><span data-stu-id="95a81-116">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="95a81-117">Üye bildiriminin gerçekleştiği içeriğe bağlı olarak, yalnızca belirli olarak tanımlanmış erişilebilirlik izin verilir.</span><span class="sxs-lookup"><span data-stu-id="95a81-117">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="95a81-118">Üye bildiriminde erişim değiştiricisi belirtilmemişse, varsayılan bir erişilebilirlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="95a81-118">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="95a81-119">Diğer türlerde iç içe olmayan en üst düzey türler yalnızca `internal` veya `public` erişilebilirliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="95a81-119">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="95a81-120">Bu türlerin varsayılan erişilebilirliği `internal` .</span><span class="sxs-lookup"><span data-stu-id="95a81-120">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="95a81-121">Diğer türlerin üyeleri olan iç içe türler, aşağıdaki tabloda gösterildiği gibi, erişilebilir olarak bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="95a81-121">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="95a81-122">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="95a81-122">Members of</span></span>|<span data-ttu-id="95a81-123">Varsayılan üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="95a81-123">Default member accessibility</span></span>|<span data-ttu-id="95a81-124">Üyenin izin verilen erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="95a81-124">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="95a81-125">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="95a81-125">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="95a81-126">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="95a81-126">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="95a81-127">İç içe bir türün erişilebilirliği, hem belirtilen üyenin hem de hem de hem de kapsayan türdeki erişilebilirlik etki alanı tarafından belirlenen [erişilebilirlik etki alanına](./accessibility-domain.md)bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="95a81-127">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="95a81-128">Ancak, iç içe geçmiş bir türün erişilebilirlik etki alanı, kapsayan türden bu türü aşamaz.</span><span class="sxs-lookup"><span data-stu-id="95a81-128">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="95a81-129">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="95a81-129">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="95a81-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95a81-130">See also</span></span>

- [<span data-ttu-id="95a81-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="95a81-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="95a81-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="95a81-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="95a81-133">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="95a81-133">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="95a81-134">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="95a81-134">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="95a81-135">Erişilebilirlik Etki Alanı</span><span class="sxs-lookup"><span data-stu-id="95a81-135">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="95a81-136">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="95a81-136">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="95a81-137">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="95a81-137">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="95a81-138">genel</span><span class="sxs-lookup"><span data-stu-id="95a81-138">public</span></span>](./public.md)
- [<span data-ttu-id="95a81-139">private</span><span class="sxs-lookup"><span data-stu-id="95a81-139">private</span></span>](./private.md)
- [<span data-ttu-id="95a81-140">protected</span><span class="sxs-lookup"><span data-stu-id="95a81-140">protected</span></span>](./protected.md)
- [<span data-ttu-id="95a81-141">internal</span><span class="sxs-lookup"><span data-stu-id="95a81-141">internal</span></span>](./internal.md)
