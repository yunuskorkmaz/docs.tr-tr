---
title: değiştirici C# başvurusunu geçersiz kıl
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: bbdbcaf466e0b4dca4b78902ca9e7a49b02ac718
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394231"
---
# <a name="override-c-reference"></a><span data-ttu-id="f6410-102">override (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f6410-102">override (C# Reference)</span></span>

<span data-ttu-id="f6410-103">`override` Değiştirici, devralınan bir metodun, özelliğin, dizin oluşturucunun veya olayın soyut veya sanal uygulamasını genişletmek ya da değiştirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="f6410-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="f6410-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6410-104">Example</span></span>

<span data-ttu-id="f6410-105">Bu örnekte,, soyut `Square` `GetArea` `GetArea` sınıftandevralınmışolduğundan,sınıfınıngeçersizkılınanbir`Shape` uygulamasını sağlaması gerekir:</span><span class="sxs-lookup"><span data-stu-id="f6410-105">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="f6410-106">Bir `override` yöntemi, temel sınıftan devralınan bir üyenin yeni bir uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6410-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="f6410-107">Bir `override` bildirim tarafından geçersiz kılınan yöntem, geçersiz kılınan temel yöntem olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="f6410-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="f6410-108">Geçersiz kılınan temel yöntemin, `override` yöntemiyle aynı imzaya sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f6410-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="f6410-109">Devralma hakkında daha fazla bilgi için bkz. [Devralma](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="f6410-109">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="f6410-110">Sanal olmayan veya statik bir yöntemi geçersiz kılamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f6410-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="f6410-111">Geçersiz kılınan taban yöntemi `virtual`, `abstract`veya `override`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6410-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="f6410-112">Bildirim, `virtual` yönteminin erişilebilirliğini değiştiremez. `override`</span><span class="sxs-lookup"><span data-stu-id="f6410-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="f6410-113">Hem yöntemi hem de yöntemi aynı [erişim düzeyi değiştiricisine](access-modifiers.md)sahip olmalıdır. `virtual` `override`</span><span class="sxs-lookup"><span data-stu-id="f6410-113">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="f6410-114">Bir `new` `static` `virtual` yöntemi değiştirmek için, veya değiştiricilerini kullanamazsınız. `override`</span><span class="sxs-lookup"><span data-stu-id="f6410-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="f6410-115">Geçersiz kılma özelliği bildirimi, devralınan özellik olarak tam olarak aynı erişim değiştiricisini, türü ve adı belirtmeli ve geçersiz kılınan özellik `virtual`, `abstract`veya `override`olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f6410-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="f6410-116">`override` Anahtar sözcüğünü kullanma hakkında daha fazla bilgi için, bkz. [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="f6410-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="f6410-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="f6410-117">Example</span></span>

<span data-ttu-id="f6410-118">Bu örnek `Employee`, adlı bir temel sınıfı ve adlı `SalesEmployee`türetilmiş bir sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="f6410-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="f6410-119">Sınıfı ek bir `salesbonus`alan içerir ve bunu hesaba almak için yöntemi `CalculatePay` geçersiz kılar. `SalesEmployee`</span><span class="sxs-lookup"><span data-stu-id="f6410-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="f6410-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="f6410-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f6410-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6410-121">See also</span></span>

- [<span data-ttu-id="f6410-122">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="f6410-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f6410-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f6410-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f6410-124">Devralma</span><span class="sxs-lookup"><span data-stu-id="f6410-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="f6410-125">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f6410-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f6410-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="f6410-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="f6410-127">abstract</span><span class="sxs-lookup"><span data-stu-id="f6410-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="f6410-128">virtual</span><span class="sxs-lookup"><span data-stu-id="f6410-128">virtual</span></span>](virtual.md)
- [<span data-ttu-id="f6410-129">Yeni (değiştirici)</span><span class="sxs-lookup"><span data-stu-id="f6410-129">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="f6410-130">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="f6410-130">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
