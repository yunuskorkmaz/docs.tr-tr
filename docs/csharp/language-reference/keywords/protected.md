---
title: "protected (C# Başvurusu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 18278ed28f899d9030d6056eca9bbe83ebec04c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="protected-c-reference"></a><span data-ttu-id="e43d5-102">protected (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e43d5-102">protected (C# Reference)</span></span>
<span data-ttu-id="e43d5-103">`protected` Sözcüktür üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="e43d5-103">The `protected` keyword is a member access modifier.</span></span> 

 > <span data-ttu-id="e43d5-104">Bu sayfayı kapsayan `protected` erişim.</span><span class="sxs-lookup"><span data-stu-id="e43d5-104">This page covers `protected` access.</span></span> <span data-ttu-id="e43d5-105">`protected` Sözcüktür ayrıca parçası [ `protected internal` ](./protected-internal.md) ve [ `private protected` ](./private-protected.md) erişim değiştiricileri.</span><span class="sxs-lookup"><span data-stu-id="e43d5-105">The `protected` keyword is also part of the [`protected internal`](./protected-internal.md) and [`private protected`](./private-protected.md) access modifiers.</span></span> 

<span data-ttu-id="e43d5-106">Korumalı üye kendi sınıfı içinde ve türetilen sınıf örnekleri tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e43d5-106">A protected member is accessible within its class and by derived class instances.</span></span> 

<span data-ttu-id="e43d5-107">Bir karşılaştırması `protected` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e43d5-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
  
## <a name="example"></a><span data-ttu-id="e43d5-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="e43d5-108">Example</span></span>  
 <span data-ttu-id="e43d5-109">Yalnızca erişim üzerinden türetilmiş sınıf türü oluşuyorsa korumalı bir temel sınıf üyesi türetilen bir sınıfta erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="e43d5-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="e43d5-110">Örneğin, aşağıdaki kod kesimi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e43d5-110">For example, consider the following code segment:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 <span data-ttu-id="e43d5-111">Deyim `a.x = 10` ana statik yöntemi içinde oluşturulur ve b sınıf örneği değil çünkü bir hata oluşturur</span><span class="sxs-lookup"><span data-stu-id="e43d5-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>  
  
 <span data-ttu-id="e43d5-112">Yapı üyeleri yapısı devraldığından korunamaz.</span><span class="sxs-lookup"><span data-stu-id="e43d5-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e43d5-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="e43d5-113">Example</span></span>  
 <span data-ttu-id="e43d5-114">Bu örnekte, sınıf `DerivedPoint` türetildiği `Point`.</span><span class="sxs-lookup"><span data-stu-id="e43d5-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="e43d5-115">Bu nedenle, doğrudan türetilmiş sınıftan temel sınıfın korumalı üyeleri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="e43d5-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 <span data-ttu-id="e43d5-116">Erişim düzeyleri değiştirirseniz `x` ve `y` için [özel](../../../csharp/language-reference/keywords/private.md), derleyici hata iletileri verecek:</span><span class="sxs-lookup"><span data-stu-id="e43d5-116">If you change the access levels of `x` and `y` to [private](../../../csharp/language-reference/keywords/private.md), the compiler will issue the error messages:</span></span>  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="e43d5-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="e43d5-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e43d5-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e43d5-118">See Also</span></span>  
 [<span data-ttu-id="e43d5-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="e43d5-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e43d5-120">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e43d5-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e43d5-121">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="e43d5-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e43d5-122">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="e43d5-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="e43d5-123">Erişilebilirlik düzeyleri</span><span class="sxs-lookup"><span data-stu-id="e43d5-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="e43d5-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="e43d5-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="e43d5-125">Ortak</span><span class="sxs-lookup"><span data-stu-id="e43d5-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="e43d5-126">Özel</span><span class="sxs-lookup"><span data-stu-id="e43d5-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="e43d5-127">İç</span><span class="sxs-lookup"><span data-stu-id="e43d5-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 <span data-ttu-id="e43d5-128">[İç sanal anahtar ile ilgili güvenlik konuları](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="e43d5-128">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>