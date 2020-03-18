---
title: değiştirici geçersiz kılma - C# Reference
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: acad3aa3b196c184132ad1acdf52b18a799b0896
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713254"
---
# <a name="override-c-reference"></a><span data-ttu-id="50e08-102">override (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="50e08-102">override (C# Reference)</span></span>

<span data-ttu-id="50e08-103">`override` Değiştirici, devralınan bir yöntemin, özelliğin, dizinleyicinin veya olayın soyut veya sanal uygulamasını genişletmek veya değiştirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="50e08-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="50e08-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="50e08-104">Example</span></span>

<span data-ttu-id="50e08-105">Bu örnekte, `Square` sınıf soyut `GetArea` `GetArea` `Shape` sınıftan devralınan çünkü geçersiz bir uygulama sağlamalıdır:</span><span class="sxs-lookup"><span data-stu-id="50e08-105">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="50e08-106">Yöntem, `override` taban sınıftan devralınan bir üyenin yeni bir uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="50e08-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="50e08-107">Bir `override` bildirim tarafından geçersiz kılınan yöntem, geçersiz kılınan temel yöntem olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="50e08-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="50e08-108">Geçersiz kılınan temel yöntem, yöntemle `override` aynı imzaya sahip olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50e08-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="50e08-109">Devralma hakkında bilgi için [bkz.](../../programming-guide/classes-and-structs/inheritance.md)</span><span class="sxs-lookup"><span data-stu-id="50e08-109">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="50e08-110">Sanal olmayan veya statik bir yöntemi geçersiz kılamazsınız.</span><span class="sxs-lookup"><span data-stu-id="50e08-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="50e08-111">Geçersiz kılınan baz yöntemi `virtual` `abstract`, `override`veya .</span><span class="sxs-lookup"><span data-stu-id="50e08-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="50e08-112">Bir `override` bildirim `virtual` yöntemin erişilebilirliğini değiştiremez.</span><span class="sxs-lookup"><span data-stu-id="50e08-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="50e08-113">Hem `override` yöntem hem `virtual` de yöntem aynı [erişim düzeyi değiştirici](access-modifiers.md)olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="50e08-113">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="50e08-114">Bir `override` yöntemi `new`değiştirmek `static`için `virtual` , veya değiştiriciler kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="50e08-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="50e08-115">Geçersiz kılınan bir özellik bildirimi, devralınan özellikle tam olarak aynı erişim değiştiricisini, türünü `virtual`ve `abstract`adını `override`belirtmelidir ve geçersiz kılınan özellik , yani .</span><span class="sxs-lookup"><span data-stu-id="50e08-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="50e08-116">Anahtar kelimenin `override` nasıl kullanılacağı hakkında daha fazla bilgi için, [Geçersiz Kılma ve Yeni Anahtar Kelimelerle Sürüm](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) leme ve Geçersiz Kılma ve Yeni Anahtar [Kelimeleri'nin ne zaman kullanılacağını bilmek](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)için bkz.</span><span class="sxs-lookup"><span data-stu-id="50e08-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="50e08-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="50e08-117">Example</span></span>

<span data-ttu-id="50e08-118">Bu örnek, adlı `Employee`bir taban sınıf ve `SalesEmployee`türetilmiş bir sınıf tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="50e08-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="50e08-119">Sınıf `SalesEmployee` fazladan bir alan `salesbonus`içerir ve bunu `CalculatePay` dikkate almak için yöntemi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="50e08-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="50e08-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="50e08-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="50e08-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50e08-121">See also</span></span>

- [<span data-ttu-id="50e08-122">C# Referans</span><span class="sxs-lookup"><span data-stu-id="50e08-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="50e08-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="50e08-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="50e08-124">Devralma</span><span class="sxs-lookup"><span data-stu-id="50e08-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="50e08-125">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="50e08-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="50e08-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="50e08-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="50e08-127">Soyut</span><span class="sxs-lookup"><span data-stu-id="50e08-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="50e08-128">virtual</span><span class="sxs-lookup"><span data-stu-id="50e08-128">virtual</span></span>](virtual.md)
- [<span data-ttu-id="50e08-129">yeni (değiştirici)</span><span class="sxs-lookup"><span data-stu-id="50e08-129">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="50e08-130">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="50e08-130">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
