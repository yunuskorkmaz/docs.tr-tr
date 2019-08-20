---
title: Erişilebilirlik düzeyleri- C# başvuru
ms.custom: seodec18
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 2d6605a305e5003e19f4fe1dd260746302691215
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602392"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="9ce46-102">Erişilebilirlik Düzeyleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="9ce46-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="9ce46-103">Üyeler için aşağıdaki tanımlanmış erişilebilirlik `public`düzeylerinden birini `internal`belirtmek için `private`,,, veya erişim değiştiricilerini `protected`kullanın.</span><span class="sxs-lookup"><span data-stu-id="9ce46-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="9ce46-104">Tanımlanan erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="9ce46-104">Declared accessibility</span></span>|<span data-ttu-id="9ce46-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ce46-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="9ce46-106">Erişim kısıtlı değil.</span><span class="sxs-lookup"><span data-stu-id="9ce46-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="9ce46-107">Erişim, kapsayan sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ce46-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="9ce46-108">Erişim, geçerli derleme ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ce46-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="9ce46-109">Erişim, geçerli derleme veya kapsayan sınıftan türetilmiş türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ce46-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="9ce46-110">Erişim, kapsayan tür ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ce46-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="9ce46-111">Erişim, geçerli derleme içindeki içeren sınıftan türetilmiş kapsayan sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ce46-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="9ce46-112">7,2 sürümünden C# itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9ce46-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="9ce46-113">`protected internal` Veya`private protected` kombinasyonlarını kullandığınızda, bir üye veya tür için yalnızca bir erişim değiştiricisine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9ce46-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="9ce46-114">Ad alanlarında erişim değiştiricilerine izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="9ce46-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="9ce46-115">Ad alanlarının erişim kısıtlamaları yoktur.</span><span class="sxs-lookup"><span data-stu-id="9ce46-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="9ce46-116">Üye bildiriminin gerçekleştiği içeriğe bağlı olarak, yalnızca belirli olarak tanımlanmış erişilebilirlik izin verilir.</span><span class="sxs-lookup"><span data-stu-id="9ce46-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="9ce46-117">Üye bildiriminde erişim değiştiricisi belirtilmemişse, varsayılan bir erişilebilirlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9ce46-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="9ce46-118">Diğer türlerde iç içe olmayan en üst düzey türler yalnızca `internal` veya `public` erişilebilirliği olabilir.</span><span class="sxs-lookup"><span data-stu-id="9ce46-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="9ce46-119">Bu türlerin `internal`varsayılan erişilebilirliği.</span><span class="sxs-lookup"><span data-stu-id="9ce46-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="9ce46-120">Diğer türlerin üyeleri olan iç içe türler, aşağıdaki tabloda gösterildiği gibi, erişilebilir olarak bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="9ce46-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="9ce46-121">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="9ce46-121">Members of</span></span>|<span data-ttu-id="9ce46-122">Varsayılan üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="9ce46-122">Default member accessibility</span></span>|<span data-ttu-id="9ce46-123">Üyenin izin verilen erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="9ce46-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="9ce46-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="9ce46-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="9ce46-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="9ce46-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="9ce46-126">İç içe bir türün erişilebilirliği, hem belirtilen üyenin hem de hem de hem de kapsayan türdeki erişilebilirlik etki alanı tarafından belirlenen [erişilebilirlik etki alanına](./accessibility-domain.md)bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ce46-126">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="9ce46-127">Ancak, iç içe geçmiş bir türün erişilebilirlik etki alanı, kapsayan türden bu türü aşamaz.</span><span class="sxs-lookup"><span data-stu-id="9ce46-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9ce46-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="9ce46-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9ce46-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ce46-129">See also</span></span>

- [<span data-ttu-id="9ce46-130">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="9ce46-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9ce46-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="9ce46-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9ce46-132">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9ce46-132">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="9ce46-133">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="9ce46-133">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="9ce46-134">Erişilebilirlik Etki Alanı</span><span class="sxs-lookup"><span data-stu-id="9ce46-134">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="9ce46-135">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="9ce46-135">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="9ce46-136">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="9ce46-136">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="9ce46-137">public</span><span class="sxs-lookup"><span data-stu-id="9ce46-137">public</span></span>](./public.md)
- [<span data-ttu-id="9ce46-138">private</span><span class="sxs-lookup"><span data-stu-id="9ce46-138">private</span></span>](./private.md)
- [<span data-ttu-id="9ce46-139">protected</span><span class="sxs-lookup"><span data-stu-id="9ce46-139">protected</span></span>](./protected.md)
- [<span data-ttu-id="9ce46-140">internal</span><span class="sxs-lookup"><span data-stu-id="9ce46-140">internal</span></span>](./internal.md)
