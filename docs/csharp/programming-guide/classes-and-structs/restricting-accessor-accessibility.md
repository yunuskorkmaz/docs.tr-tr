---
title: -Erişimci erişilebilirliğini kısıtlama C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: 2f9580e018684f65762bc40e131a19215e9690c2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544672"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="2a1a8-102">Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2a1a8-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="2a1a8-103">[Alma](../../../csharp/language-reference/keywords/get.md) ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) bölümlerini özelliğin veya dizin oluşturucu çağrılır *erişimcileri*.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-103">The [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="2a1a8-104">Varsayılan olarak, özellik veya dizin oluşturucu ait oldukları aynı görünürlük veya erişim düzeyini bu erişimcilerine sahip.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-104">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="2a1a8-105">Daha fazla bilgi için [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2a1a8-105">For more information, see [accessibility levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="2a1a8-106">Ancak, bazen bu erişimcileri birine erişimi kısıtlamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="2a1a8-107">Genellikle, bu erişilebilirliğini kısıtlama içerir `set` tutma sırasında erişimci `get` erişimci genel olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="2a1a8-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a1a8-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 <span data-ttu-id="2a1a8-109">Bu örnekte, bir özelliğin çağırılır `Name` tanımlayan bir `get` ve `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-109">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="2a1a8-110">`get` Erişimci özelliğin kendisine erişilebilirlik düzeyi alır `public` bu durumda, while `set` erişimci açıkça kısıtlanan uygulayarak [korumalı](../../../csharp/language-reference/keywords/protected.md) erişim değiştiricisi erişimci kendisi.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-110">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../../csharp/language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="2a1a8-111">Erişim değiştiricileri kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="2a1a8-111">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="2a1a8-112">Erişimci değiştiriciler özellikleri veya dizin oluşturucuları kullanarak bu koşullara tabi olan:</span><span class="sxs-lookup"><span data-stu-id="2a1a8-112">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
-   <span data-ttu-id="2a1a8-113">Bir arabirim veya açık bir erişimci değiştiriciler kullanamazsınız [arabirimi](../../../csharp/language-reference/keywords/interface.md) üye uygulaması.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-113">You cannot use accessor modifiers on an interface or an explicit [interface](../../../csharp/language-reference/keywords/interface.md) member implementation.</span></span>  
  
-   <span data-ttu-id="2a1a8-114">Erişimci değiştiricileri yalnızca özellik veya dizin oluşturucusu hem de varsa kullanabilirsiniz `set` ve `get` erişimcileri.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-114">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="2a1a8-115">Bu durumda, değiştirici biri yalnızca iki erişimci üzerinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-115">In this case, the modifier is permitted on one only of the two accessors.</span></span>  
  
-   <span data-ttu-id="2a1a8-116">Özellik veya dizin oluşturucusu varsa bir [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) değiştiricisi, erişimci değiştiricisi eşleşmelidir geçersiz kılınan erişimcisinin erişimcisi varsa.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-116">If the property or indexer has an [override](../../../csharp/language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
-   <span data-ttu-id="2a1a8-117">Erişimci erişilebilirliği düzeyde erişilebilirlik düzeyi özelliği veya dizin oluşturucu kendisini daha kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-117">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="2a1a8-118">Erişimciler geçersiz kılma üzerinde erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="2a1a8-118">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="2a1a8-119">Bir özellik veya dizin oluşturucu geçersiz kıldığınızda, geçersiz kılınan erişimcileri geçersiz kılma koda erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-119">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="2a1a8-120">Ayrıca, hem özellik/dizin oluşturucu ve onun erişimcilerinin erişilebilirliği, karşılık gelen geçersiz kılınan özelliğin/dizin oluşturucu ve onun erişimcilerinin eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-120">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="2a1a8-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a1a8-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="2a1a8-122">Arabirimleri uygulama</span><span class="sxs-lookup"><span data-stu-id="2a1a8-122">Implementing Interfaces</span></span>  
 <span data-ttu-id="2a1a8-123">Bir arabirim uygulamak için bir erişimci kullandığınızda, bir erişim değiştiricisidir erişimci olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-123">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="2a1a8-124">Ancak, bir erişimci gibi kullanarak arabirim uygular, `get`, aşağıdaki örnekte olduğu gibi bir erişim değiştiricisidir diğer erişimcisi olabilir:</span><span class="sxs-lookup"><span data-stu-id="2a1a8-124">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="2a1a8-125">Erişimcisinin erişilebilirlik etki alanı</span><span class="sxs-lookup"><span data-stu-id="2a1a8-125">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="2a1a8-126">Erişimci üzerinde bir erişim değiştiricisidir kullanırsanız [erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md) erişimcisine bu değiştirici tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-126">If you use an access modifier on the accessor, the [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="2a1a8-127">Bir erişim değiştiricisidir erişimcisine kullanmadıysanız erişimcisinin erişilebilirlik etki alanı özellik veya dizin oluşturucu erişilebilirlik düzeyi tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-127">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a1a8-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a1a8-128">Example</span></span>  
 <span data-ttu-id="2a1a8-129">Aşağıdaki örnek, üç sınıfları içerir. `BaseClass`, `DerivedClass`, ve `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-129">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="2a1a8-130">İki özelliği vardır `BaseClass`, `Name` ve `Id` hem sınıfları.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-130">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="2a1a8-131">Örnek gösterir nasıl özelliği `Id` üzerinde `DerivedClass` özelliğiyle gizlenebilir `Id` üzerinde `BaseClass` kullandığınızda bir kısıtlayıcı erişim değiştiricisi gibi [korumalı](../../../csharp/language-reference/keywords/protected.md) veya [ özel](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="2a1a8-131">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../../csharp/language-reference/keywords/protected.md) or [private](../../../csharp/language-reference/keywords/private.md).</span></span> <span data-ttu-id="2a1a8-132">Bu nedenle, atadığınızda bu özellik, özellik değerleri üzerinde `BaseClass` sınıfı yerine çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-132">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="2a1a8-133">Erişim değiştiricisi ile değiştirerek [genel](../../../csharp/language-reference/keywords/public.md) özelliği erişilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-133">Replacing the access modifier by [public](../../../csharp/language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="2a1a8-134">Bu örnek ayrıca gösteren bir kısıtlayıcı erişim değiştiricisi gibi `private` veya `protected`, `set` erişimcisine `Name` özelliğinde `DerivedClass` erişimciye erişimi engeller ve atadığınız bir hata oluşturur .</span><span class="sxs-lookup"><span data-stu-id="2a1a8-134">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## <a name="comments"></a><span data-ttu-id="2a1a8-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a1a8-135">Comments</span></span>  
 <span data-ttu-id="2a1a8-136">Bildirimi değiştirirseniz dikkat `new private string Id` tarafından `new public string Id`, çıkış alırsınız:</span><span class="sxs-lookup"><span data-stu-id="2a1a8-136">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="2a1a8-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a1a8-137">See also</span></span>

- [<span data-ttu-id="2a1a8-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2a1a8-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2a1a8-139">Özellikler</span><span class="sxs-lookup"><span data-stu-id="2a1a8-139">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="2a1a8-140">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="2a1a8-140">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="2a1a8-141">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="2a1a8-141">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
