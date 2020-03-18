---
title: Erişilebilirlik Düzeyleri - C# Referans
ms.date: 12/06/2017
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
ms.openlocfilehash: 26fbc2a6d86aead537465c304146630f8bcd3ad4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713823"
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="dfe14-102">Erişilebilirlik Düzeyleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="dfe14-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="dfe14-103">Üyeler için aşağıdaki bildirilen `public` `protected`erişilebilirlik düzeylerinden birini belirtmek için erişim değiştiriciler, , , `internal`, veya `private`, kullanın.</span><span class="sxs-lookup"><span data-stu-id="dfe14-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="dfe14-104">Bildirilen erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="dfe14-104">Declared accessibility</span></span>|<span data-ttu-id="dfe14-105">Anlamı</span><span class="sxs-lookup"><span data-stu-id="dfe14-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="dfe14-106">Erişim sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="dfe14-107">Erişim, içeren sınıfveya içeren sınıftan türetilen türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="dfe14-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="dfe14-108">Erişim geçerli derleme ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="dfe14-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="dfe14-109">Erişim, geçerli derleme yle veya içeren sınıftan türetilen türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="dfe14-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="dfe14-110">Erişim, içeren türle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="dfe14-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="dfe14-111">Erişim, geçerli derleme içindeki içeren sınıftan türetilen sınıf veya türlerle sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="dfe14-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="dfe14-112">C# 7.2'den beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="dfe14-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="dfe14-113">Bir üye veya tür için, bir üye `protected internal` veya `private protected` kombinasyonları kullandığınız zamanlar dışında yalnızca bir erişim değiştiricisine izin verilir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="dfe14-114">Ad alanlarında erişim değiştiricilere izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="dfe14-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="dfe14-115">Ad alanlarının erişim kısıtlaması yoktur.</span><span class="sxs-lookup"><span data-stu-id="dfe14-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="dfe14-116">Üye bildiriminin gerçekleştiği içeriğe bağlı olarak, yalnızca belirli bildirilen erişimlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="dfe14-117">Üye bildiriminde erişim değiştirici belirtilmemişse, varsayılan erişilebilirlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dfe14-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="dfe14-118">Diğer türlerde iç içe olmayan üst düzey türler `internal` yalnızca `public` erişebilirveya erişilebilirolabilir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="dfe14-119">Bu türler için varsayılan erişilebilirlik. `internal`</span><span class="sxs-lookup"><span data-stu-id="dfe14-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="dfe14-120">Diğer türlerin üyesi olan iç içe geçen türler, aşağıdaki tabloda belirtildiği gibi erişilebilirliklerini bildirmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="dfe14-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="dfe14-121">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="dfe14-121">Members of</span></span>|<span data-ttu-id="dfe14-122">Varsayılan üye erişilebilirliği</span><span class="sxs-lookup"><span data-stu-id="dfe14-122">Default member accessibility</span></span>|<span data-ttu-id="dfe14-123">Üyenin bildirilen erişilebilirliğine izin verilen</span><span class="sxs-lookup"><span data-stu-id="dfe14-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="dfe14-124">None</span><span class="sxs-lookup"><span data-stu-id="dfe14-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="dfe14-125">None</span><span class="sxs-lookup"><span data-stu-id="dfe14-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="dfe14-126">İç içe geçen bir türün [erişilebilirliği,](./accessibility-domain.md)hem üyenin bildirilen erişilebilirliği hem de hemen içeren türün erişilebilirlik etki alanı tarafından belirlenen erişilebilirlik etki alanına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dfe14-126">The accessibility of a nested type depends on its [accessibility domain](./accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="dfe14-127">Ancak, iç içe bir türün erişilebilirlik etki alanı, içeren türü aşamaz.</span><span class="sxs-lookup"><span data-stu-id="dfe14-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="dfe14-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="dfe14-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dfe14-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfe14-129">See also</span></span>

- [<span data-ttu-id="dfe14-130">C# Referans</span><span class="sxs-lookup"><span data-stu-id="dfe14-130">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dfe14-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="dfe14-131">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dfe14-132">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="dfe14-132">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="dfe14-133">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="dfe14-133">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="dfe14-134">Erişilebilirlik Etki Alanı</span><span class="sxs-lookup"><span data-stu-id="dfe14-134">Accessibility Domain</span></span>](./accessibility-domain.md)
- [<span data-ttu-id="dfe14-135">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="dfe14-135">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="dfe14-136">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="dfe14-136">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="dfe14-137">Kamu</span><span class="sxs-lookup"><span data-stu-id="dfe14-137">public</span></span>](./public.md)
- [<span data-ttu-id="dfe14-138">Özel</span><span class="sxs-lookup"><span data-stu-id="dfe14-138">private</span></span>](./private.md)
- [<span data-ttu-id="dfe14-139">protected</span><span class="sxs-lookup"><span data-stu-id="dfe14-139">protected</span></span>](./protected.md)
- [<span data-ttu-id="dfe14-140">Iç</span><span class="sxs-lookup"><span data-stu-id="dfe14-140">internal</span></span>](./internal.md)
