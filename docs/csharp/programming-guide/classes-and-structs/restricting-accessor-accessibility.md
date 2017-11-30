---
title: "Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accesibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a4905885323f59d8b8b2654a5331e02054334398
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="2a043-102">Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="2a043-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="2a043-103">[Almak](../../../csharp/language-reference/keywords/get.md) ve [ayarlamak](../../../csharp/language-reference/keywords/set.md) bir özellik veya dizin bölümlerini çağrılır *erişimciler*.</span><span class="sxs-lookup"><span data-stu-id="2a043-103">The [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="2a043-104">Varsayılan olarak bu erişimciler aynı görünürlüğe sahip veya erişim düzeyi:, ait oldukları özelliği ya da dizin oluşturucu.</span><span class="sxs-lookup"><span data-stu-id="2a043-104">By default these accessors have the same visibility, or access level: that of the property or indexer to which they belong.</span></span> <span data-ttu-id="2a043-105">Daha fazla bilgi için bkz: [erişilebilirlik düzeyleri](../../../csharp/language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2a043-105">For more information, see [accessibility levels](../../../csharp/language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="2a043-106">Ancak, bazen bu erişimciler birine erişimi kısıtlamak yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2a043-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="2a043-107">Genellikle, bu erişilebilirliğini kısıtlama içerir `set` tutma sırasında erişimcisi `get` erişimci genel olarak erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="2a043-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="2a043-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a043-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_1.cs)]  
  
 <span data-ttu-id="2a043-109">Bu örnekte, bir özellik olarak adlandırılan `Name` tanımlayan bir `get` ve `set` erişimcisi.</span><span class="sxs-lookup"><span data-stu-id="2a043-109">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="2a043-110">`get` Erişimci alır özelliğin kendisine erişilebilirlik düzeyi `public` bu durumda, while `set` erişimci açıkça kısıtlanmış uygulayarak [korumalı](../../../csharp/language-reference/keywords/protected.md) erişim değiştiricisi erişimci kendisi.</span><span class="sxs-lookup"><span data-stu-id="2a043-110">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../../csharp/language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="2a043-111">Erişim değiştiricileri kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="2a043-111">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="2a043-112">Özellikler ve dizin oluşturucular erişimci değiştiricilerini kullanarak bu koşullara tabi şöyledir:</span><span class="sxs-lookup"><span data-stu-id="2a043-112">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
-   <span data-ttu-id="2a043-113">Bir arabirim veya açık bir erişimci değiştiricileri kullanamazsınız [arabirimi](../../../csharp/language-reference/keywords/interface.md) üye uygulama.</span><span class="sxs-lookup"><span data-stu-id="2a043-113">You cannot use accessor modifiers on an interface or an explicit [interface](../../../csharp/language-reference/keywords/interface.md) member implementation.</span></span>  
  
-   <span data-ttu-id="2a043-114">Yalnızca özellik veya dizin oluşturucu her ikisi de varsa erişimcisi değiştiricileri kullanabilirsiniz `set` ve `get` erişimciler.</span><span class="sxs-lookup"><span data-stu-id="2a043-114">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="2a043-115">Bu durumda, değiştiricisi birinde yalnızca iki erişimciler izin verilir.</span><span class="sxs-lookup"><span data-stu-id="2a043-115">In this case, the modifier is permitted on one only of the two accessors.</span></span>  
  
-   <span data-ttu-id="2a043-116">Özellik veya dizin oluşturucu varsa bir [geçersiz kılma](../../../csharp/language-reference/keywords/override.md) değiştiricisi, erişimci değiştiricisi eşleşmelidir geçersiz kılınan erişimci erişimcisi varsa.</span><span class="sxs-lookup"><span data-stu-id="2a043-116">If the property or indexer has an [override](../../../csharp/language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
-   <span data-ttu-id="2a043-117">Erişilebilirlik düzeyi erişimcisi üzerinde erişilebilirlik düzeyi özelliği veya dizin oluşturucu kendisini daha kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2a043-117">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="2a043-118">Erişimciler geçersiz kılma üzerinde erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="2a043-118">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="2a043-119">Bir özellik veya dizin oluşturucu geçersiz kıldığınızda, geçersiz kılınan erişimciler geçersiz kılma koda erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2a043-119">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="2a043-120">Ayrıca, hem özelliği/dizin oluşturucu erişilebilirlik düzeyi ve erişimciler, karşılık gelen geçersiz kılınan özelliği/dizin oluşturucu ve erişimciler aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2a043-120">Also, the accessibility level of both the property/indexer, and that of the accessors must match the corresponding overridden property/indexer and the accessors.</span></span> <span data-ttu-id="2a043-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2a043-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_2.cs)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="2a043-122">Arabirimler uygulama</span><span class="sxs-lookup"><span data-stu-id="2a043-122">Implementing Interfaces</span></span>  
 <span data-ttu-id="2a043-123">Bir arabirim için bir erişimci kullandığınızda, bir erişim değiştiricisi erişimcisi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="2a043-123">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="2a043-124">Ancak, bir erişimci gibi kullanılarak arabirimini uygulayan varsa `get`, diğer erişimcisi aşağıdaki örnekteki gibi bir erişim değiştiricisi sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="2a043-124">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_3.cs)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="2a043-125">Erişimci erişilebilirlik etki alanı</span><span class="sxs-lookup"><span data-stu-id="2a043-125">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="2a043-126">Erişimci üzerinde bir erişim değiştiricisi kullanırsanız [erişilebilirlik etki alanı](../../../csharp/language-reference/keywords/accessibility-domain.md) erişimcisine bu değiştirici tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2a043-126">If you use an access modifier on the accessor, the [accessibility domain](../../../csharp/language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="2a043-127">Bir erişim değiştiricisi erişimcisine kullanmadıysanız erişimci erişilebilirlik etki alanı özelliği veya dizin oluşturucu erişilebilirlik düzeyi tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="2a043-127">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a043-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a043-128">Example</span></span>  
 <span data-ttu-id="2a043-129">Aşağıdaki örnek, üç sınıfları içerir `BaseClass`, `DerivedClass`, ve `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="2a043-129">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="2a043-130">İki özellik vardır `BaseClass`, `Name` ve `Id` hem sınıfları.</span><span class="sxs-lookup"><span data-stu-id="2a043-130">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="2a043-131">Örnek gösterir nasıl özelliği `Id` üzerinde `DerivedClass` özelliği tarafından gizli `Id` üzerinde `BaseClass` kullandığınızda kısıtlayıcı erişim değiştiricisi gibi [korumalı](../../../csharp/language-reference/keywords/protected.md) veya [ özel](../../../csharp/language-reference/keywords/private.md).</span><span class="sxs-lookup"><span data-stu-id="2a043-131">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../../csharp/language-reference/keywords/protected.md) or [private](../../../csharp/language-reference/keywords/private.md).</span></span> <span data-ttu-id="2a043-132">Bu nedenle, atadığınızda bu özellik, özellik değerleri üzerinde `BaseClass` sınıfı yerine çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2a043-132">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="2a043-133">Tarafından erişim değiştiricisi değiştirme [ortak](../../../csharp/language-reference/keywords/public.md) özelliği erişilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="2a043-133">Replacing the access modifier by [public](../../../csharp/language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="2a043-134">Bu örnek ayrıca gösteren bir kısıtlayıcı erişim değiştiricisi gibi `private` veya `protected`, `set` erişimcisine `Name` özelliğinde `DerivedClass` erişimci erişimi engeller ve atadığınızda, içerik için bir hata oluşturur .</span><span class="sxs-lookup"><span data-stu-id="2a043-134">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/restricting-accessor-accessibility_4.cs)]  
  
## <a name="comments"></a><span data-ttu-id="2a043-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a043-135">Comments</span></span>  
 <span data-ttu-id="2a043-136">Bildirim değiştirirseniz dikkat `new private string Id` tarafından `new public string Id`, çıktı alın:</span><span class="sxs-lookup"><span data-stu-id="2a043-136">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="2a043-137">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2a043-137">See Also</span></span>  
 [<span data-ttu-id="2a043-138">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="2a043-138">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2a043-139">Özellikleri</span><span class="sxs-lookup"><span data-stu-id="2a043-139">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="2a043-140">Dizin oluşturucular</span><span class="sxs-lookup"><span data-stu-id="2a043-140">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="2a043-141">Erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="2a043-141">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
