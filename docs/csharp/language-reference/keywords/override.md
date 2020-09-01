---
description: değiştirici-C# başvurusunu geçersiz kıl
title: değiştirici-C# başvurusunu geçersiz kıl
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 51ca806310214981b7ff24a796fe078d902dca4d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134466"
---
# <a name="override-c-reference"></a><span data-ttu-id="70e40-103">override (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="70e40-103">override (C# Reference)</span></span>

<span data-ttu-id="70e40-104">`override`Değiştirici, devralınan bir metodun, özelliğin, dizin oluşturucunun veya olayın soyut veya sanal uygulamasını genişletmek ya da değiştirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="70e40-104">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="70e40-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="70e40-105">Example</span></span>

<span data-ttu-id="70e40-106">Bu örnekte,, `Square` `GetArea` `GetArea` soyut sınıftan devralınmış olduğundan, sınıfının geçersiz kılınan bir uygulamasını sağlaması gerekir `Shape` :</span><span class="sxs-lookup"><span data-stu-id="70e40-106">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="70e40-107">Bir `override` yöntemi, temel sınıftan devralınan bir üyenin yeni bir uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="70e40-107">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="70e40-108">Bir bildirim tarafından geçersiz kılınan yöntem, `override` geçersiz kılınan temel yöntem olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="70e40-108">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="70e40-109">Geçersiz kılınan temel yöntemin, yöntemiyle aynı imzaya sahip olması gerekir `override` .</span><span class="sxs-lookup"><span data-stu-id="70e40-109">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="70e40-110">Devralma hakkında daha fazla bilgi için bkz. [Devralma](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="70e40-110">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="70e40-111">Sanal olmayan veya statik bir yöntemi geçersiz kılamazsınız.</span><span class="sxs-lookup"><span data-stu-id="70e40-111">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="70e40-112">Geçersiz kılınan taban yöntemi `virtual` , veya olmalıdır `abstract` `override` .</span><span class="sxs-lookup"><span data-stu-id="70e40-112">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="70e40-113">`override`Bildirim, yönteminin erişilebilirliğini değiştiremez `virtual` .</span><span class="sxs-lookup"><span data-stu-id="70e40-113">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="70e40-114">Hem `override` yöntemi hem de `virtual` yöntemi aynı [erişim düzeyi değiştiricisine](access-modifiers.md)sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="70e40-114">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="70e40-115">`new` `static` `virtual` Bir yöntemi değiştirmek için, veya değiştiricilerini kullanamazsınız `override` .</span><span class="sxs-lookup"><span data-stu-id="70e40-115">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="70e40-116">Geçersiz kılma özelliği bildirimi, devralınan özellik olarak tam olarak aynı erişim değiştiricisini, türü ve adı belirtmeli ve geçersiz kılınan özellik `virtual` , `abstract` veya olmalıdır `override` .</span><span class="sxs-lookup"><span data-stu-id="70e40-116">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="70e40-117">Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için `override` , bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="70e40-117">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="70e40-118">Örnek</span><span class="sxs-lookup"><span data-stu-id="70e40-118">Example</span></span>

<span data-ttu-id="70e40-119">Bu örnek, adlı bir temel sınıfı `Employee` ve adlı türetilmiş bir sınıfı tanımlar `SalesEmployee` .</span><span class="sxs-lookup"><span data-stu-id="70e40-119">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="70e40-120">`SalesEmployee`Sınıfı ek bir alan içerir `salesbonus` ve `CalculatePay` bunu hesaba almak için yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="70e40-120">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="70e40-121">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="70e40-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="70e40-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70e40-122">See also</span></span>

- [<span data-ttu-id="70e40-123">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="70e40-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="70e40-124">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="70e40-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="70e40-125">Devralma</span><span class="sxs-lookup"><span data-stu-id="70e40-125">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="70e40-126">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="70e40-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="70e40-127">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="70e40-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="70e40-128">abstract</span><span class="sxs-lookup"><span data-stu-id="70e40-128">abstract</span></span>](abstract.md)
- [<span data-ttu-id="70e40-129">virtual</span><span class="sxs-lookup"><span data-stu-id="70e40-129">virtual</span></span>](virtual.md)
- [<span data-ttu-id="70e40-130">Yeni (değiştirici)</span><span class="sxs-lookup"><span data-stu-id="70e40-130">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="70e40-131">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="70e40-131">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
