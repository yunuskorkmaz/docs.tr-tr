---
title: Erişimci erişilebilirliği kısıtlama- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: ca990693d29f8c8abd2e4ba2488a429a797afaec
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596179"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="e0bb4-102">Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e0bb4-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="e0bb4-103">Bir özelliğin veya dizin oluşturucunun [Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) bölümlerine *erişimciler*denir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-103">The [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="e0bb4-104">Varsayılan olarak, bu erişimciler ait oldukları özelliğin veya dizin oluşturucunun aynı görünürlük veya erişim düzeyine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-104">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="e0bb4-105">Daha fazla bilgi için bkz. [Erişilebilirlik düzeyleri](../../language-reference/keywords/accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e0bb4-105">For more information, see [accessibility levels](../../language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="e0bb4-106">Ancak, bu Erişimcilerde erişimi kısıtlamak bazen yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="e0bb4-107">Genellikle bu, erişimcinin erişilebilirliğini `set` kısıtlamadan, `get` erişimcinin genel olarak erişilebilir tutulması ile ilgilidir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="e0bb4-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e0bb4-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="e0bb4-109">Bu örnekte, adlı `Name` bir özellik bir `get` ve `set` erişimcisi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-109">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="e0bb4-110">Erişimci, özelliğin `public` kendi erişilebilirlik düzeyini alır, `set` bu durumda erişimci kendisine korumalı erişim değiştiricisi uygulanarak açıkça kısıtlanır. [](../../language-reference/keywords/protected.md) `get`</span><span class="sxs-lookup"><span data-stu-id="e0bb4-110">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="e0bb4-111">Erişimcilerde erişim değiştiricilerine yönelik kısıtlamalar</span><span class="sxs-lookup"><span data-stu-id="e0bb4-111">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="e0bb4-112">Özelliklerde veya dizin oluşturucularda erişimci değiştiricilerin kullanılması şu koşullara tabidir:</span><span class="sxs-lookup"><span data-stu-id="e0bb4-112">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
- <span data-ttu-id="e0bb4-113">Bir arabirimde veya açık [arabirim](../../language-reference/keywords/interface.md) üyesi uygulamasında erişimci değiştiricileri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-113">You cannot use accessor modifiers on an interface or an explicit [interface](../../language-reference/keywords/interface.md) member implementation.</span></span>  
  
- <span data-ttu-id="e0bb4-114">Erişimci değiştiricileri yalnızca özellik veya dizin oluşturucunun hem hem `set` `get` de erişimcileri varsa kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-114">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="e0bb4-115">Bu durumda, değiştiriciye yalnızca iki erişimcinin yalnızca birinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-115">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
- <span data-ttu-id="e0bb4-116">Özelliğin veya dizin oluşturucunun bir [geçersiz kılma](../../language-reference/keywords/override.md) değiştiricisi varsa, erişimci değiştiricisi, varsa geçersiz kılınan erişimcinin erişimcisi ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-116">If the property or indexer has an [override](../../language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
- <span data-ttu-id="e0bb4-117">Erişimcinin erişilebilirlik düzeyi, özelliğin veya dizin oluşturucunun kendi erişilebilirlik düzeyinden daha kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-117">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="e0bb4-118">Geçersiz kılma erişimcileri üzerindeki erişim değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="e0bb4-118">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="e0bb4-119">Bir özelliği veya dizin oluşturucuyu geçersiz kıldığınızda geçersiz kılınan erişimcilere geçersiz kılma kodu tarafından erişilebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-119">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="e0bb4-120">Ayrıca, hem Property/Indexer hem de erişimcilerinin erişilebilirliği karşılık gelen geçersiz kılınan Özellik/Dizin Oluşturucu ve erişimcileri ile eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-120">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="e0bb4-121">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e0bb4-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="e0bb4-122">Arabirimleri uygulama</span><span class="sxs-lookup"><span data-stu-id="e0bb4-122">Implementing Interfaces</span></span>  
 <span data-ttu-id="e0bb4-123">Bir arabirim uygulamak için erişimci kullandığınızda, erişimci bir erişim değiştiricisine sahip olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-123">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="e0bb4-124">Ancak, gibi bir erişimci `get`kullanarak arabirimi uygularsanız, diğer erişimci aşağıdaki örnekte olduğu gibi bir erişim değiştiricisine sahip olabilir:</span><span class="sxs-lookup"><span data-stu-id="e0bb4-124">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="e0bb4-125">Erişimci erişilebilirlik etki alanı</span><span class="sxs-lookup"><span data-stu-id="e0bb4-125">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="e0bb4-126">Erişimci üzerinde bir erişim değiştiricisi kullanırsanız, erişimcinin [erişilebilirlik etki alanı](../../language-reference/keywords/accessibility-domain.md) bu değiştiriciye göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-126">If you use an access modifier on the accessor, the [accessibility domain](../../language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="e0bb4-127">Erişimci üzerinde bir erişim değiştiricisi kullanmıyorsanız, erişimcinin erişilebilirlik etki alanı, özelliğin veya dizin oluşturucunun erişilebilirlik düzeyine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-127">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0bb4-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="e0bb4-128">Example</span></span>  
 <span data-ttu-id="e0bb4-129">Aşağıdaki örnek üç sınıf `BaseClass` `DerivedClass`içerir,, ve `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-129">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="e0bb4-130">Üzerinde `BaseClass` `Name` ve herikisınıftaikiözelliğivardır.`Id`</span><span class="sxs-lookup"><span data-stu-id="e0bb4-130">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="e0bb4-131">Örnek, [korumalı](../../language-reference/keywords/protected.md) veya [özel](../../language-reference/keywords/private.md)gibi kısıtlayıcı `DerivedClass` bir erişim değiştiricisi kullandığınızda üzerinde özelliğinin `Id` `Id` nasıl `BaseClass` gizlendiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-131">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../language-reference/keywords/protected.md) or [private](../../language-reference/keywords/private.md).</span></span> <span data-ttu-id="e0bb4-132">Bu nedenle, bu özelliğe değer atadığınızda, `BaseClass` sınıfındaki özelliği yerine çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-132">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="e0bb4-133">Erişim değiştiricisinin [genel](../../language-reference/keywords/public.md) olarak değiştirilmesi, özelliği erişilebilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-133">Replacing the access modifier by [public](../../language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="e0bb4-134">Örnek ayrıca `private` , içindeki `Name` `protected` özelliğininerişimcisinde`set` bulunan veya gibi kısıtlayıcı bir erişim değiştiricisinin erişimciye erişimi önlediği ve ' a atarken bir hata üretmesinin gerektiğini gösterir. `DerivedClass` içerdiği.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-134">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="e0bb4-135">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0bb4-135">Comments</span></span>  
 <span data-ttu-id="e0bb4-136">Bildirimini `new private string Id` ile`new public string Id`değiştirmeniz durumunda çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="e0bb4-136">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="e0bb4-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e0bb4-137">See also</span></span>

- [<span data-ttu-id="e0bb4-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e0bb4-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e0bb4-139">Özellikler</span><span class="sxs-lookup"><span data-stu-id="e0bb4-139">Properties</span></span>](./properties.md)
- [<span data-ttu-id="e0bb4-140">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e0bb4-140">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="e0bb4-141">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="e0bb4-141">Access Modifiers</span></span>](./access-modifiers.md)
