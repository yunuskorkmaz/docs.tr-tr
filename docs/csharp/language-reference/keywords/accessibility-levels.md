---
description: Erişilebilirlik düzeyleri-C# başvurusu
title: Erişilebilirlik düzeyleri-C# başvurusu
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 509902e9998af421c0afd31070b1be36d64df0f8
ms.sourcegitcommit: 46cfed35d79d70e08c313b9c664c7e76babab39e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102604599"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="c5b63-103">Erişilebilirlik Düzeyleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="c5b63-103">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="c5b63-104">`public` `protected` `internal` `private` Üyeler için aşağıdaki tanımlanmış erişilebilirlik düzeylerinden birini belirtmek için,,, veya erişim değiştiricilerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c5b63-104">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="c5b63-105">Tanımlanan erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="c5b63-105">Declared accessibility</span></span>|<span data-ttu-id="c5b63-106">Anlamı</span><span class="sxs-lookup"><span data-stu-id="c5b63-106">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="c5b63-107">Erişim kısıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="c5b63-107">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="c5b63-108">Erişim, kapsayan sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5b63-108">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="c5b63-109">Erişim, geçerli derleme ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5b63-109">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="c5b63-110">Erişim, geçerli derleme veya kapsayan sınıftan türetilmiş türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5b63-110">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="c5b63-111">Erişim, kapsayan tür ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5b63-111">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="c5b63-112">Erişim, geçerli derleme içindeki içeren sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5b63-112">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="c5b63-113">C# 7,2 sürümünden itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c5b63-113">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="c5b63-114">Veya kombinasyonlarını kullandığınızda, bir üye veya tür için yalnızca bir erişim değiştiricisine izin verilir `protected internal` `private protected` .</span><span class="sxs-lookup"><span data-stu-id="c5b63-114">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="c5b63-115">Ad alanlarında erişim değiştiricilerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="c5b63-115">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="c5b63-116">Ad alanlarının erişim kısıtlamaları yoktur.</span><span class="sxs-lookup"><span data-stu-id="c5b63-116">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="c5b63-117">Üye bildiriminin gerçekleştiği içeriğe bağlı olarak, yalnızca belirli olarak tanımlanmış erişilebilirlik izin verilir.</span><span class="sxs-lookup"><span data-stu-id="c5b63-117">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="c5b63-118">Üye bildiriminde erişim değiştiricisi belirtilmemişse, varsayılan bir erişilebilirlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c5b63-118">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="c5b63-119">Diğer türlerde iç içe olmayan en üst düzey türler yalnızca `internal` veya `public` erişilebilirliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="c5b63-119">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="c5b63-120">Bu türlerin varsayılan erişilebilirliği `internal` .</span><span class="sxs-lookup"><span data-stu-id="c5b63-120">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="c5b63-121">Diğer türlerin üyeleri olan iç içe türler, aşağıdaki tabloda gösterildiği gibi, erişilebilir olarak bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="c5b63-121">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="c5b63-122">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="c5b63-122">Members of</span></span>|<span data-ttu-id="c5b63-123">Varsayılan üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="c5b63-123">Default member accessibility</span></span>|<span data-ttu-id="c5b63-124">Üyenin izin verilen erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="c5b63-124">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="c5b63-125">Yok</span><span class="sxs-lookup"><span data-stu-id="c5b63-125">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`\*<br /><br /> `protected internal` <br /><br />`private protected`|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  

<span data-ttu-id="c5b63-126">\*`interface`Erişilebilirliği olan bir üyenin `private` varsayılan bir uygulamasına sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="c5b63-126">\* An `interface` member with `private` accessibility must have a default implementation.</span></span>

<span data-ttu-id="c5b63-127">İç içe bir türün erişilebilirliği, hem belirtilen üyenin hem de hem de hem de kapsayan türdeki erişilebilirlik etki alanı tarafından belirlenen [erişilebilirlik etki alanına](./accessibility-domain.md)bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="c5b63-127">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="c5b63-128">Ancak, iç içe geçmiş bir türün erişilebilirlik etki alanı, kapsayan türden bu türü aşamaz.</span><span class="sxs-lookup"><span data-stu-id="c5b63-128">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="c5b63-129">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="c5b63-129">C# Language Specification</span></span>  

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c5b63-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c5b63-130">See also</span></span>

- [<span data-ttu-id="c5b63-131">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="c5b63-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c5b63-132">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c5b63-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c5b63-133">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="c5b63-133">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c5b63-134">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="c5b63-134">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="c5b63-135">Erişilebilirlik Etki Alanı</span><span class="sxs-lookup"><span data-stu-id="c5b63-135">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="c5b63-136">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="c5b63-136">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="c5b63-137">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="c5b63-137">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="c5b63-138">genel</span><span class="sxs-lookup"><span data-stu-id="c5b63-138">public</span></span>](./public.md)
- [<span data-ttu-id="c5b63-139">özelleştirme</span><span class="sxs-lookup"><span data-stu-id="c5b63-139">private</span></span>](./private.md)
- [<span data-ttu-id="c5b63-140">protected</span><span class="sxs-lookup"><span data-stu-id="c5b63-140">protected</span></span>](./protected.md)
- [<span data-ttu-id="c5b63-141">internal</span><span class="sxs-lookup"><span data-stu-id="c5b63-141">internal</span></span>](./internal.md)
