---
description: değiştirici-C# başvurusunu geçersiz kıl
title: değiştirici-C# başvurusunu geçersiz kıl
ms.date: 10/22/2020
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 618200183348e68a4600adb9592a635f61f6a875
ms.sourcegitcommit: 98d20cb038669dca4a195eb39af37d22ea9d008e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92434885"
---
# <a name="override-c-reference"></a><span data-ttu-id="fac52-103">override (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fac52-103">override (C# reference)</span></span>

<span data-ttu-id="fac52-104">`override`Değiştirici, devralınan bir metodun, özelliğin, dizin oluşturucunun veya olayın soyut veya sanal uygulamasını genişletmek ya da değiştirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="fac52-104">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

<span data-ttu-id="fac52-105">Aşağıdaki örnekte, `Square` sınıfı `GetArea` `GetArea` soyut sınıftan devralındığından, sınıfının geçersiz kılınan bir uygulamasını sağlaması gerekir `Shape` :</span><span class="sxs-lookup"><span data-stu-id="fac52-105">In the following example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="fac52-106">Bir `override` yöntemi, temel sınıftan devralınan yöntemin yeni bir uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fac52-106">An `override` method provides a new implementation of the method inherited from a base class.</span></span> <span data-ttu-id="fac52-107">Bir bildirim tarafından geçersiz kılınan yöntem, `override` geçersiz kılınan temel yöntem olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="fac52-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="fac52-108">Bir `override` yöntem geçersiz kılınan taban yöntemiyle aynı imzaya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fac52-108">An `override` method must have the same signature as the overridden base method.</span></span> <span data-ttu-id="fac52-109">C# 9,0 ' den başlayarak, `override` Yöntemler birlikte değişken dönüş türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="fac52-109">Beginning with C# 9.0, `override` methods support covariant return types.</span></span> <span data-ttu-id="fac52-110">Özellikle, bir yöntemin dönüş türü, `override` karşılık gelen temel yöntemin dönüş türünden türetilebilir.</span><span class="sxs-lookup"><span data-stu-id="fac52-110">In particular, the return type of an `override` method can derive from the return type of the corresponding base method.</span></span> <span data-ttu-id="fac52-111">C# 8,0 ve önceki sürümlerde, bir `override` yöntemin ve geçersiz kılınan temel yöntemin dönüş türleri aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fac52-111">In C# 8.0 and earlier, the return types of an `override` method and the overridden base method must be the same.</span></span>

<span data-ttu-id="fac52-112">Sanal olmayan veya statik bir yöntemi geçersiz kılamazsınız.</span><span class="sxs-lookup"><span data-stu-id="fac52-112">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="fac52-113">Geçersiz kılınan taban yöntemi `virtual` , veya olmalıdır `abstract` `override` .</span><span class="sxs-lookup"><span data-stu-id="fac52-113">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="fac52-114">`override`Bildirim, yönteminin erişilebilirliğini değiştiremez `virtual` .</span><span class="sxs-lookup"><span data-stu-id="fac52-114">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="fac52-115">Hem `override` yöntemi hem de `virtual` yöntemi aynı [erişim düzeyi değiştiricisine](access-modifiers.md)sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="fac52-115">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="fac52-116">`new` `static` `virtual` Bir yöntemi değiştirmek için, veya değiştiricilerini kullanamazsınız `override` .</span><span class="sxs-lookup"><span data-stu-id="fac52-116">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="fac52-117">Geçersiz kılma özelliği bildirimi, devralınan özellik olarak tam olarak aynı erişim değiştiricisini, türü ve adı belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="fac52-117">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property.</span></span> <span data-ttu-id="fac52-118">C# 9,0 ile başlayarak, salt okuma geçersiz kılma özellikleri birlikte değişken dönüş türlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="fac52-118">Beginning with C# 9.0, read-only overriding properties support covariant return types.</span></span> <span data-ttu-id="fac52-119">Geçersiz kılınan özellik `virtual` , veya olmalıdır `abstract` `override` .</span><span class="sxs-lookup"><span data-stu-id="fac52-119">The overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="fac52-120">Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için `override` , bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="fac52-120">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span> <span data-ttu-id="fac52-121">Devralma hakkında daha fazla bilgi için bkz. [Devralma](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="fac52-121">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

## <a name="example"></a><span data-ttu-id="fac52-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="fac52-122">Example</span></span>

<span data-ttu-id="fac52-123">Bu örnek, adlı bir temel sınıfı `Employee` ve adlı türetilmiş bir sınıfı tanımlar `SalesEmployee` .</span><span class="sxs-lookup"><span data-stu-id="fac52-123">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="fac52-124">`SalesEmployee`Sınıfı ek bir alan içerir `salesbonus` ve `CalculatePay` bunu hesaba almak için yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="fac52-124">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="fac52-125">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="fac52-125">C# language specification</span></span>

<span data-ttu-id="fac52-126">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [geçersiz kılma yöntemleri](~/_csharplang/spec/classes.md#override-methods) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="fac52-126">For more information, see the [Override methods](~/_csharplang/spec/classes.md#override-methods) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="fac52-127">Covaryant dönüş türleri hakkında daha fazla bilgi için bkz. [özellik teklifi Note](~/_csharplang/proposals/csharp-9.0/covariant-returns.md).</span><span class="sxs-lookup"><span data-stu-id="fac52-127">For more information about covariant return types, see the [feature proposal note](~/_csharplang/proposals/csharp-9.0/covariant-returns.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fac52-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fac52-128">See also</span></span>

- [<span data-ttu-id="fac52-129">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fac52-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fac52-130">Devralma</span><span class="sxs-lookup"><span data-stu-id="fac52-130">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="fac52-131">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fac52-131">C# keywords</span></span>](index.md)
- [<span data-ttu-id="fac52-132">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="fac52-132">Modifiers</span></span>](index.md)
- [<span data-ttu-id="fac52-133">abstract</span><span class="sxs-lookup"><span data-stu-id="fac52-133">abstract</span></span>](abstract.md)
- [<span data-ttu-id="fac52-134">virtual</span><span class="sxs-lookup"><span data-stu-id="fac52-134">virtual</span></span>](virtual.md)
- [<span data-ttu-id="fac52-135">Yeni (değiştirici)</span><span class="sxs-lookup"><span data-stu-id="fac52-135">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="fac52-136">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="fac52-136">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
