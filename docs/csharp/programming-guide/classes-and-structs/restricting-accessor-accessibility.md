---
title: Erişime Erişimin Kısıtlanması - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- read-only properties [C#]
- read-only indexers [C#]
- accessors [C#]
- properties [C#], read-only
- asymmetric accessor accessibility [C#]
- indexers [C#], read-only
ms.assetid: 6e655798-e112-4301-a680-6310a6e012e1
ms.openlocfilehash: a332fef814f0c81914eb7b8c308de68f719fbaac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714689"
---
# <a name="restricting-accessor-accessibility-c-programming-guide"></a><span data-ttu-id="7d4f0-102">Erişimci Erişilebilirliğini Kısıtlama (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="7d4f0-102">Restricting Accessor Accessibility (C# Programming Guide)</span></span>
<span data-ttu-id="7d4f0-103">Bir özelliğin veya dizinleyicinin [alın](../../language-reference/keywords/get.md) ve [ayarla](../../language-reference/keywords/set.md) *bölümlerine erişimci*denir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-103">The [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) portions of a property or indexer are called *accessors*.</span></span> <span data-ttu-id="7d4f0-104">Varsayılan olarak bu erişimedenler, ait oldukları özellik veya dizinleyicinin aynı görünürlüğüne veya erişim düzeyine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-104">By default these accessors have the same visibility or access level of the property or indexer to which they belong.</span></span> <span data-ttu-id="7d4f0-105">Daha fazla bilgi için [erişilebilirlik düzeylerine](../../language-reference/keywords/accessibility-levels.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-105">For more information, see [accessibility levels](../../language-reference/keywords/accessibility-levels.md).</span></span> <span data-ttu-id="7d4f0-106">Ancak, bazen bu erişime erişimin kısıtlanması yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-106">However, it is sometimes useful to restrict access to one of these accessors.</span></span> <span data-ttu-id="7d4f0-107">Genellikle, bu, `set` erişime erişimin kısıtlanmasıve erişimin `get` herkese açık tutulmasını içerir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-107">Typically, this involves restricting the accessibility of the `set` accessor, while keeping the `get` accessor publicly accessible.</span></span> <span data-ttu-id="7d4f0-108">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7d4f0-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#6)]  
  
 <span data-ttu-id="7d4f0-109">Bu örnekte, adlı `Name` bir `get` özellik `set` a ve erişimci tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-109">In this example, a property called `Name` defines a `get` and `set` accessor.</span></span> <span data-ttu-id="7d4f0-110">Bu `get` durumda, erişimci, [korumalı](../../language-reference/keywords/protected.md) erişim `public` değiştiriciyi erişimsahibinin kendisine uygulanarak açıkça kısıtlanırken, `set` erişimsahibi özelliğin erişilebilirlik düzeyini alır.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-110">The `get` accessor receives the accessibility level of the property itself, `public` in this case, while the `set` accessor is explicitly restricted by applying the [protected](../../language-reference/keywords/protected.md) access modifier to the accessor itself.</span></span>  
  
## <a name="restrictions-on-access-modifiers-on-accessors"></a><span data-ttu-id="7d4f0-111">Erişimcilere Erişim Kısıtlamaları</span><span class="sxs-lookup"><span data-stu-id="7d4f0-111">Restrictions on Access Modifiers on Accessors</span></span>  
 <span data-ttu-id="7d4f0-112">Özellik veya dizinleyiciler üzerinde aksesuar değiştiricilerin kullanılması aşağıdaki koşullara tabidir:</span><span class="sxs-lookup"><span data-stu-id="7d4f0-112">Using the accessor modifiers on properties or indexers is subject to these conditions:</span></span>  
  
- <span data-ttu-id="7d4f0-113">Bir arabirimde veya açık [arabirim](../../language-reference/keywords/interface.md) üyesi uygulamasında erişim değiştirici leri kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-113">You cannot use accessor modifiers on an interface or an explicit [interface](../../language-reference/keywords/interface.md) member implementation.</span></span>  
  
- <span data-ttu-id="7d4f0-114">Erişim değiştiricileri yalnızca özellik veya dizinleyicihem `set` de `get` erişimciler varsa kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-114">You can use accessor modifiers only if the property or indexer has both `set` and `get` accessors.</span></span> <span data-ttu-id="7d4f0-115">Bu durumda, değiştirici yalnızca iki erişimcilerin birinde izin verilir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-115">In this case, the modifier is permitted on only one of the two accessors.</span></span>  
  
- <span data-ttu-id="7d4f0-116">Özellik veya dizinleyicibir [geçersiz kılma](../../language-reference/keywords/override.md) değiştirici varsa, erişimdeğiştirici geçersiz kılınan erişime sahip, varsa, geçersiz kılınan erişime sahip olanla eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-116">If the property or indexer has an [override](../../language-reference/keywords/override.md) modifier, the accessor modifier must match the accessor of the overridden accessor, if any.</span></span>  
  
- <span data-ttu-id="7d4f0-117">Erişilebilirlik düzeyi, özellik veya dizinleyicinin kendisindeki erişilebilirlik düzeyinden daha kısıtlayıcı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-117">The accessibility level on the accessor must be more restrictive than the accessibility level on the property or indexer itself.</span></span>  
  
## <a name="access-modifiers-on-overriding-accessors"></a><span data-ttu-id="7d4f0-118">Access'i Geçersiz Kılanlar'da Değiştiricilere Erişin</span><span class="sxs-lookup"><span data-stu-id="7d4f0-118">Access Modifiers on Overriding Accessors</span></span>  
 <span data-ttu-id="7d4f0-119">Bir özelliği veya dizinleyiciyi geçersiz kaldığınızda, geçersiz kılınan erişime erişilenler için geçersiz kılınan koda erişilebilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-119">When you override a property or indexer, the overridden accessors must be accessible to the overriding code.</span></span> <span data-ttu-id="7d4f0-120">Ayrıca, hem özellik/dizinleyicinin hem de erişime girenlerin ilgili geçersiz kılınan özellik/dizinleyici ile ve erişime girenlerle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-120">Also, the accessibility of both the property/indexer and its accessors must match the corresponding overridden property/indexer and its accessors.</span></span> <span data-ttu-id="7d4f0-121">Örnek:</span><span class="sxs-lookup"><span data-stu-id="7d4f0-121">For example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#7)]  
  
## <a name="implementing-interfaces"></a><span data-ttu-id="7d4f0-122">Arayüzleri Uygulama</span><span class="sxs-lookup"><span data-stu-id="7d4f0-122">Implementing Interfaces</span></span>  
 <span data-ttu-id="7d4f0-123">Arabirimi uygulamak için bir erişimci kullandığınızda, erişimsahibinin bir erişim değiştiricisi olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-123">When you use an accessor to implement an interface, the accessor may not have an access modifier.</span></span> <span data-ttu-id="7d4f0-124">Ancak, arabirimi aşağıdaki örnekte olduğu gibi, diğer erişimcinin bir erişim değiştiricisi olabilir gibi `get`bir erişimci kullanarak uygularsanız:</span><span class="sxs-lookup"><span data-stu-id="7d4f0-124">However, if you implement the interface using one accessor, such as `get`, the other accessor can have an access modifier, as in the following example:</span></span>  
  
 [!code-csharp[csProgGuideIndexers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#8)]  
  
## <a name="accessor-accessibility-domain"></a><span data-ttu-id="7d4f0-125">Erişilebilirlik Etki Alanı</span><span class="sxs-lookup"><span data-stu-id="7d4f0-125">Accessor Accessibility Domain</span></span>  
 <span data-ttu-id="7d4f0-126">Erişim değiştiriciüzerinde bir erişim değiştiricisi kullanıyorsanız, erişime [erişim etki alanı](../../language-reference/keywords/accessibility-domain.md) bu değiştirici tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-126">If you use an access modifier on the accessor, the [accessibility domain](../../language-reference/keywords/accessibility-domain.md) of the accessor is determined by this modifier.</span></span>  
  
 <span data-ttu-id="7d4f0-127">Erişim değiştiriciüzerinde bir erişim değiştirici kullanmadıysanız, erişime erişim etki alanı özellik veya dizinleyicinin erişilebilirlik düzeyine göre belirlenir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-127">If you did not use an access modifier on the accessor, the accessibility domain of the accessor is determined by the accessibility level of the property or indexer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d4f0-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="7d4f0-128">Example</span></span>  
 <span data-ttu-id="7d4f0-129">Aşağıdaki örnekte üç `BaseClass`sınıf `DerivedClass`ve `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-129">The following example contains three classes, `BaseClass`, `DerivedClass`, and `MainClass`.</span></span> <span data-ttu-id="7d4f0-130">`BaseClass` `Name` Ve `Id` her iki sınıfta iki özellik vardır.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-130">There are two properties on the `BaseClass`, `Name` and `Id` on both classes.</span></span> <span data-ttu-id="7d4f0-131">Örnek, [korumalı](../../language-reference/keywords/protected.md) [veya](../../language-reference/keywords/private.md)özel gibi kısıtlayıcı `Id` `BaseClass` bir erişim değiştirici kullandığınızda üzerindeki `Id` `DerivedClass` özelliğin özellik tarafından nasıl gizlenebileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-131">The example demonstrates how the property `Id` on `DerivedClass` can be hidden by the property `Id` on `BaseClass` when you use a restrictive access modifier such as [protected](../../language-reference/keywords/protected.md) or [private](../../language-reference/keywords/private.md).</span></span> <span data-ttu-id="7d4f0-132">Bu nedenle, bu özelliğe değer atadığınızda, `BaseClass` sınıfüzerindeki özellik bunun yerine çağrılır.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-132">Therefore, when you assign values to this property, the property on the `BaseClass` class is called instead.</span></span> <span data-ttu-id="7d4f0-133">Erişim değiştiricinin [genel](../../language-reference/keywords/public.md) tarafından değiştirilmesi özelliği erişilebilir hale getirecektir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-133">Replacing the access modifier by [public](../../language-reference/keywords/public.md) will make the property accessible.</span></span>  
  
 <span data-ttu-id="7d4f0-134">Örnek ayrıca, `private` `protected` `set` `Name` özellik erişimcisi gibi kısıtlayıcı bir erişim değiştiricinin erişime erişimi `DerivedClass` engellediğini ve ona atadığınızda bir hata oluşturduğunu da gösterir.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-134">The example also demonstrates that a restrictive access modifier, such as `private` or `protected`, on the `set` accessor of the `Name` property in `DerivedClass` prevents access to the accessor and generates an error when you assign to it.</span></span>  
  
 [!code-csharp[csProgGuideIndexers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideIndexers/CS/Indexers.cs#5)]  
  
## <a name="comments"></a><span data-ttu-id="7d4f0-135">Yorumlar</span><span class="sxs-lookup"><span data-stu-id="7d4f0-135">Comments</span></span>  
 <span data-ttu-id="7d4f0-136">Bildirimi `new private string Id` değiştirirseniz `new public string Id`çıktıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="7d4f0-136">Notice that if you replace the declaration `new private string Id` by `new public string Id`, you get the output:</span></span>  
  
 `Name and ID in the base class: Name-BaseClass, ID-BaseClass`  
  
 `Name and ID in the derived class: John, John123`  
  
## <a name="see-also"></a><span data-ttu-id="7d4f0-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d4f0-137">See also</span></span>

- [<span data-ttu-id="7d4f0-138">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7d4f0-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7d4f0-139">Özellikler</span><span class="sxs-lookup"><span data-stu-id="7d4f0-139">Properties</span></span>](./properties.md)
- [<span data-ttu-id="7d4f0-140">Dizin Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="7d4f0-140">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="7d4f0-141">Erişim Değiştiricileri</span><span class="sxs-lookup"><span data-stu-id="7d4f0-141">Access Modifiers</span></span>](./access-modifiers.md)
