---
title: "Erişilebilirlik Düzeyleri (C# Başvurusu)"
ms.date: 12/06/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- access modifiers [C#], accessibility levels
- accessibility levels
ms.assetid: dc083921-0073-413e-8936-a613e8bb7df4
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: fed7d6d0eb3eda4d8d2e1847259dd8d23700d3e7
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="accessibility-levels-c-reference"></a><span data-ttu-id="d959a-102">Erişilebilirlik Düzeyleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="d959a-102">Accessibility Levels (C# Reference)</span></span>

<span data-ttu-id="d959a-103">Erişim değiştiricileri kullanmak `public`, `protected`, `internal`, veya `private`, aşağıdaki bildirilen erişilebilirlik düzeylerinden birini üyeleri için belirtin.</span><span class="sxs-lookup"><span data-stu-id="d959a-103">Use the access modifiers, `public`, `protected`, `internal`, or `private`, to specify one of the following declared accessibility levels for members.</span></span>  
  
|<span data-ttu-id="d959a-104">Bildirilen erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="d959a-104">Declared accessibility</span></span>|<span data-ttu-id="d959a-105">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d959a-105">Meaning</span></span>|  
|----------------------------|-------------|  
|[`public`](public.md)|<span data-ttu-id="d959a-106">Erişim sınırlı değildir.</span><span class="sxs-lookup"><span data-stu-id="d959a-106">Access is not restricted.</span></span>|  
|[`protected`](protected.md)|<span data-ttu-id="d959a-107">Erişim sınıfı veya içeren sınıfından türetilen türler içeren sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="d959a-107">Access is limited to the containing class or types derived from the containing class.</span></span>|  
|[`internal`](internal.md)|<span data-ttu-id="d959a-108">Erişim geçerli derlemeye sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="d959a-108">Access is limited to the current assembly.</span></span>|  
|[`protected internal`](protected-internal.md)|<span data-ttu-id="d959a-109">Geçerli derleme veya içeren sınıfından türetilen türler için erişim sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="d959a-109">Access is limited to the current assembly or types derived from the containing class.</span></span>|  
|[`private`](private.md)|<span data-ttu-id="d959a-110">Erişim içeren türü ile sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="d959a-110">Access is limited to the containing type.</span></span>|  
|[`private protected`](private-protected.md)|<span data-ttu-id="d959a-111">Erişim sınıfı veya geçerli derlemedeki içeren sınıfından türetilmiş türler içeren sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="d959a-111">Access is limited to the containing class or types derived from the containing class within the current assembly.</span></span> <span data-ttu-id="d959a-112">C# 7.2 itibaren kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d959a-112">Available since C# 7.2.</span></span> |  
  
 <span data-ttu-id="d959a-113">Yalnızca bir erişim değiştiricisi izin verilen bir üye veya türü için dışında kullandığınızda `protected internal` veya `private protected` birleşimleri.</span><span class="sxs-lookup"><span data-stu-id="d959a-113">Only one access modifier is allowed for a member or type, except when you use the `protected internal` or `private protected` combinations.</span></span>  
  
 <span data-ttu-id="d959a-114">Erişim değiştiricileri ad alanında bulunan izin verilmez.</span><span class="sxs-lookup"><span data-stu-id="d959a-114">Access modifiers are not allowed on namespaces.</span></span> <span data-ttu-id="d959a-115">Ad alanları, hiçbir erişim kısıtlamaları vardır.</span><span class="sxs-lookup"><span data-stu-id="d959a-115">Namespaces have no access restrictions.</span></span>  
  
 <span data-ttu-id="d959a-116">Üye bildirimi gerçekleştiği bağlamı bağlı olarak, yalnızca belirli bildirilen eriþebilirlik izin verilir.</span><span class="sxs-lookup"><span data-stu-id="d959a-116">Depending on the context in which a member declaration occurs, only certain declared accessibilities are permitted.</span></span> <span data-ttu-id="d959a-117">Herhangi bir erişim değiştiricisi üye bildiriminde belirtilmezse, varsayılan erişilebilirlik kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d959a-117">If no access modifier is specified in a member declaration, a default accessibility is used.</span></span>  
  
 <span data-ttu-id="d959a-118">Diğer türlerinde içe değil, üst düzey türleri yalnızca olabilir `internal` veya `public` erişilebilirlik.</span><span class="sxs-lookup"><span data-stu-id="d959a-118">Top-level types, which are not nested in other types, can only have `internal` or `public` accessibility.</span></span> <span data-ttu-id="d959a-119">Bu tür için varsayılan erişilebilirlik olduğu `internal`.</span><span class="sxs-lookup"><span data-stu-id="d959a-119">The default accessibility for these types is `internal`.</span></span>  
  
 <span data-ttu-id="d959a-120">Diğer türleri üyeleri olan, iç içe geçmiş türler eriþebilirlik aşağıdaki tabloda gösterildiği gibi bildirilen.</span><span class="sxs-lookup"><span data-stu-id="d959a-120">Nested types, which are members of other types, can have declared accessibilities as indicated in the following table.</span></span>  
  
|<span data-ttu-id="d959a-121">Üyeleri</span><span class="sxs-lookup"><span data-stu-id="d959a-121">Members of</span></span>|<span data-ttu-id="d959a-122">Varsayılan üye erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="d959a-122">Default member accessibility</span></span>|<span data-ttu-id="d959a-123">Üyenin izin verilen bildirilen erişilebilirlik</span><span class="sxs-lookup"><span data-stu-id="d959a-123">Allowed declared accessibility of the member</span></span>|  
|----------------|----------------------------------|--------------------------------------------------|  
|`enum`|`public`|<span data-ttu-id="d959a-124">Yok.</span><span class="sxs-lookup"><span data-stu-id="d959a-124">None</span></span>|  
|`class`|`private`|`public`<br /><br /> `protected`<br /><br /> `internal`<br /><br /> `private`<br /><br /> `protected internal` <br /><br />`private protected`|  
|`interface`|`public`|<span data-ttu-id="d959a-125">Yok.</span><span class="sxs-lookup"><span data-stu-id="d959a-125">None</span></span>|  
|`struct`|`private`|`public`<br /><br /> `internal`<br /><br /> `private`|  
  
 <span data-ttu-id="d959a-126">İç içe geçmiş tür erişilebilirliğini bağlıdır, [erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md), üyenin bildirilen erişilebilirlik ve hemen kapsayan tür erişilebilirlik etki alanı tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="d959a-126">The accessibility of a nested type depends on its [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md), which is determined by both the declared accessibility of the member and the accessibility domain of the immediately containing type.</span></span> <span data-ttu-id="d959a-127">Ancak, iç içe geçmiş tür erişilebilirlik etki alanı, kapsayan tür aşamaz.</span><span class="sxs-lookup"><span data-stu-id="d959a-127">However, the accessibility domain of a nested type cannot exceed that of the containing type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="d959a-128">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="d959a-128">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d959a-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d959a-129">See Also</span></span>  
 [<span data-ttu-id="d959a-130">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="d959a-130">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d959a-131">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="d959a-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d959a-132">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="d959a-132">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="d959a-133">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="d959a-133">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="d959a-134">Erişilebilirlik Etki Alanı</span><span class="sxs-lookup"><span data-stu-id="d959a-134">Accessibility Domain</span></span>](../../../csharp/language-reference/keywords/accessibility-domain.md)  
 [<span data-ttu-id="d959a-135">Erişilebilirlik Düzeylerinin Kullanılmasındaki Kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="d959a-135">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [<span data-ttu-id="d959a-136">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="d959a-136">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [<span data-ttu-id="d959a-137">public</span><span class="sxs-lookup"><span data-stu-id="d959a-137">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="d959a-138">private</span><span class="sxs-lookup"><span data-stu-id="d959a-138">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="d959a-139">protected</span><span class="sxs-lookup"><span data-stu-id="d959a-139">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)  
 [<span data-ttu-id="d959a-140">internal</span><span class="sxs-lookup"><span data-stu-id="d959a-140">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
