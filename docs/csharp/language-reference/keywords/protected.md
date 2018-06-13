---
title: protected (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: a3115fe82b452f52ee75cf222302ece0fc67b330
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269576"
---
# <a name="protected-c-reference"></a><span data-ttu-id="7ad7a-102">protected (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7ad7a-102">protected (C# Reference)</span></span>
<span data-ttu-id="7ad7a-103">`protected` Sözcüktür üye erişim değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-103">The `protected` keyword is a member access modifier.</span></span> 

 > <span data-ttu-id="7ad7a-104">Bu sayfayı kapsayan `protected` erişim.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-104">This page covers `protected` access.</span></span> <span data-ttu-id="7ad7a-105">`protected` Sözcüktür ayrıca parçası [ `protected internal` ](./protected-internal.md) ve [ `private protected` ](./private-protected.md) erişim değiştiricileri.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-105">The `protected` keyword is also part of the [`protected internal`](./protected-internal.md) and [`private protected`](./private-protected.md) access modifiers.</span></span> 

<span data-ttu-id="7ad7a-106">Korumalı üye kendi sınıfı içinde ve türetilen sınıf örnekleri tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-106">A protected member is accessible within its class and by derived class instances.</span></span> 

<span data-ttu-id="7ad7a-107">Bir karşılaştırması `protected` diğer erişim değiştiricileri ile bkz [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="7ad7a-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> 
  
## <a name="example"></a><span data-ttu-id="7ad7a-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ad7a-108">Example</span></span>  
 <span data-ttu-id="7ad7a-109">Yalnızca erişim üzerinden türetilmiş sınıf türü oluşuyorsa korumalı bir temel sınıf üyesi türetilen bir sınıfta erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="7ad7a-110">Örneğin, aşağıdaki kod kesimi göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="7ad7a-110">For example, consider the following code segment:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 <span data-ttu-id="7ad7a-111">Deyim `a.x = 10` ana statik yöntemi içinde oluşturulur ve b sınıf örneği değil çünkü bir hata oluşturur</span><span class="sxs-lookup"><span data-stu-id="7ad7a-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>  
  
 <span data-ttu-id="7ad7a-112">Yapı üyeleri yapısı devraldığından korunamaz.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ad7a-113">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ad7a-113">Example</span></span>  
 <span data-ttu-id="7ad7a-114">Bu örnekte, sınıf `DerivedPoint` türetildiği `Point`.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="7ad7a-115">Bu nedenle, doğrudan türetilmiş sınıftan temel sınıfın korumalı üyeleri erişebilir.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 <span data-ttu-id="7ad7a-116">Erişim düzeyleri değiştirirseniz `x` ve `y` için [özel](../../../csharp/language-reference/keywords/private.md), derleyici hata iletileri verecek:</span><span class="sxs-lookup"><span data-stu-id="7ad7a-116">If you change the access levels of `x` and `y` to [private](../../../csharp/language-reference/keywords/private.md), the compiler will issue the error messages:</span></span>  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a><span data-ttu-id="7ad7a-117">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="7ad7a-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7ad7a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ad7a-118">See Also</span></span>  
 [<span data-ttu-id="7ad7a-119">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7ad7a-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7ad7a-120">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7ad7a-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7ad7a-121">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="7ad7a-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7ad7a-122">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="7ad7a-122">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [<span data-ttu-id="7ad7a-123">Erişilebilirlik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="7ad7a-123">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [<span data-ttu-id="7ad7a-124">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="7ad7a-124">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="7ad7a-125">public</span><span class="sxs-lookup"><span data-stu-id="7ad7a-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)  
 [<span data-ttu-id="7ad7a-126">private</span><span class="sxs-lookup"><span data-stu-id="7ad7a-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)  
 [<span data-ttu-id="7ad7a-127">internal</span><span class="sxs-lookup"><span data-stu-id="7ad7a-127">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)  
 <span data-ttu-id="7ad7a-128">[İç sanal anahtar ile ilgili güvenlik konuları](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="7ad7a-128">[Security concerns for internal virtual keywords](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))</span></span>