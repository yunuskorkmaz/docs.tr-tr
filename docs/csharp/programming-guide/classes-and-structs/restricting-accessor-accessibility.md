---
title: Erişimci erişilebilirliği kısıtlama-C# Programlama Kılavuzu
description: C# içindeki bir özelliğin get ve set erişimcileri, varsayılan olarak ait oldukları özellik olarak aynı görünürlük veya erişim düzeyine sahiptir. Erişimi kısıtlayabilirsiniz.
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: be7be4fc67a9a6f62a71f8473d6daa1fac49e842
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199035"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="3d6a5-104">Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="3d6a5-104">Restricting Accessor Accessibility (C# Programming Guide)</span></span>

<span data-ttu-id="3d6a5-105">Bir özelliğin veya dizin oluşturucunun [Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) bölümlerine *erişimciler*denir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-105">The [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="3d6a5-106">Varsayılan olarak, bu erişimciler ait oldukları özelliğin veya dizin oluşturucunun aynı görünürlük veya erişim düzeyine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-106">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="3d6a5-107">Daha fazla bilgi için bkz. [Erişilebilirlik düzeyleri](../../language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="3d6a5-107">For more information, see [accessibility levels](../../language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="3d6a5-108">Ancak, bu Erişimcilerde erişimi kısıtlamak bazen yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-108">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="3d6a5-109">Genellikle bu, erişimcinin erişilebilirliğini kısıtlamadan `set` , `get` erişimcinin genel olarak erişilebilir tutulması ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-109">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="3d6a5-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3d6a5-110">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="3d6a5-111">Bu örnekte, adlı bir özellik `Name` bir `get` ve erişimcisi tanımlar `set` .</span><span class="sxs-lookup"><span data-stu-id="3d6a5-111">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="3d6a5-112">Erişimci, `get` özelliğin kendi erişilebilirlik düzeyini alır, `public` Bu durumda `set` erişimci kendisine [korumalı](../../language-reference/keywords/protected.md) erişim değiştiricisi uygulanarak açıkça kısıtlanır.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-112">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="3d6a5-113">Erişimcilerde erişim değiştiricilerine yönelik kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="3d6a5-113">Restrictions on Access Modifiers on Accessors</span></span>  

 <span data-ttu-id="3d6a5-114">Özelliklerde veya dizin oluşturucularda erişimci değiştiricilerin kullanılması şu koşullara tabidir:</span><span class="sxs-lookup"><span data-stu-id="3d6a5-114">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
- <span data-ttu-id="3d6a5-115">Bir arabirimde veya açık [arabirim](../../language-reference/keywords/interface.md) üyesi uygulamasında erişimci değiştiricileri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-115">You cannot use accessor modifiers on an interface or an explicit [interface](../../language-reference/keywords/interface.md) member implementation.</span></span>  
  
- <span data-ttu-id="3d6a5-116">Erişimci değiştiricileri yalnızca özellik veya dizin oluşturucunun hem hem de erişimcileri varsa kullanabilirsiniz `set` `get` .</span><span class="sxs-lookup"><span data-stu-id="3d6a5-116">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="3d6a5-117">Bu durumda, değiştiriciye yalnızca iki erişimcinin yalnızca birinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-117">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
- <span data-ttu-id="3d6a5-118">Özelliğin veya dizin oluşturucunun bir [geçersiz kılma](../../language-reference/keywords/override.md) değiştiricisi varsa, erişimci değiştiricisi, varsa geçersiz kılınan erişimcinin erişimcisi ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-118">If the property or indexer has an [override](../../language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
- <span data-ttu-id="3d6a5-119">Erişimcinin erişilebilirlik düzeyi, özelliğin veya dizin oluşturucunun kendi erişilebilirlik düzeyinden daha kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-119">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="3d6a5-120">Geçersiz kılma erişimcileri üzerindeki erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="3d6a5-120">Access Modifiers on Overriding Accessors</span></span>  

 <span data-ttu-id="3d6a5-121">Bir özelliği veya dizin oluşturucuyu geçersiz kıldığınızda geçersiz kılınan erişimcilere geçersiz kılma kodu tarafından erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-121">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="3d6a5-122">Ayrıca, hem Property/Indexer hem de erişimcilerinin erişilebilirliği karşılık gelen geçersiz kılınan Özellik/Dizin Oluşturucu ve erişimcileri ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-122">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="3d6a5-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3d6a5-123">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="3d6a5-124">Arabirimleri uygulama</span><span class="sxs-lookup"><span data-stu-id="3d6a5-124">Implementing Interfaces</span></span>  

 <span data-ttu-id="3d6a5-125">Bir arabirim uygulamak için erişimci kullandığınızda, erişimci bir erişim değiştiricisine sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-125">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="3d6a5-126">Ancak, gibi bir erişimci kullanarak arabirimi uygularsanız, `get` diğer erişimci aşağıdaki örnekte olduğu gibi bir erişim değiştiricisine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="3d6a5-126">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="3d6a5-127">Erişimci erişilebilirlik etki alanı</span><span class="sxs-lookup"><span data-stu-id="3d6a5-127">Accessor Accessibility Domain</span></span>  

 <span data-ttu-id="3d6a5-128">Erişimci üzerinde bir erişim değiştiricisi kullanırsanız, erişimcinin [erişilebilirlik etki alanı](../../language-reference/keywords/accessibility-domain.md) bu değiştiriciye göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-128">If you use an access modifier on the accessor, the [accessibility domain](../../language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="3d6a5-129">Erişimci üzerinde bir erişim değiştiricisi kullanmıyorsanız, erişimcinin erişilebilirlik etki alanı, özelliğin veya dizin oluşturucunun erişilebilirlik düzeyine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-129">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d6a5-130">Örnek</span><span class="sxs-lookup"><span data-stu-id="3d6a5-130">Example</span></span>  

 <span data-ttu-id="3d6a5-131">Aşağıdaki örnek üç sınıf içerir,, `BaseClass` `DerivedClass` ve `MainClass` .</span><span class="sxs-lookup"><span data-stu-id="3d6a5-131">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="3d6a5-132">Üzerinde `BaseClass` `Name` ve `Id` her iki sınıfta iki özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-132">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="3d6a5-133">Örnek, `Id` `DerivedClass` `Id` `BaseClass` [korumalı](../../language-reference/keywords/protected.md) veya [özel](../../language-reference/keywords/private.md)gibi kısıtlayıcı bir erişim değiştiricisi kullandığınızda üzerinde özelliğinin nasıl gizlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-133">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../language-reference/keywords/protected.md) or [private](../../language-reference/keywords/private.md).</span></span> <span data-ttu-id="3d6a5-134">Bu nedenle, bu özelliğe değer atadığınızda, `BaseClass` sınıfındaki özelliği yerine çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-134">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="3d6a5-135">Erişim değiştiricisinin [genel](../../language-reference/keywords/public.md) olarak değiştirilmesi, özelliği erişilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-135">Replacing the access modifier by [public](../../language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="3d6a5-136">Örnek ayrıca, `private` içindeki özelliğinin erişimcisinde bulunan veya gibi kısıtlayıcı bir erişim `protected` `set` `Name` `DerivedClass` değiştiricisinin erişimciye erişimi önlediği ve kendisine atarken bir hata oluşturduğu bir hata üretdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-136">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="3d6a5-137">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="3d6a5-137">Comments</span></span>  

 <span data-ttu-id="3d6a5-138">Bildirimini ile değiştirmeniz durumunda `new private string Id` `new public string Id` çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="3d6a5-138">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="3d6a5-139">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3d6a5-139">See also</span></span>

- [<span data-ttu-id="3d6a5-140">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3d6a5-140">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3d6a5-141">Özellikler</span><span class="sxs-lookup"><span data-stu-id="3d6a5-141">Properties</span></span>](./properties.md)
- [<span data-ttu-id="3d6a5-142">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="3d6a5-142">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="3d6a5-143">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="3d6a5-143">Access Modifiers</span></span>](./access-modifiers.md)
