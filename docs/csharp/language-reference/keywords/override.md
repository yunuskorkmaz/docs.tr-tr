---
title: geçersiz kılma değiştiricisi (C# Başvurusu)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: cbd5e21e7ca71a4986099a0386c684a6db37c3e8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43886298"
---
# <a name="override-c-reference"></a><span data-ttu-id="1bff7-102">override (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="1bff7-102">override (C# Reference)</span></span>

<span data-ttu-id="1bff7-103">`override` Değiştiricisi, genişletme veya soyut ya da sanal uygulaması devralınan yöntemi, özelliği, dizin oluşturucusu veya olayı değiştirmek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1bff7-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="1bff7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bff7-104">Example</span></span>

<span data-ttu-id="1bff7-105">Bu örnekte, `Square` sınıfı, geçersiz kılınan bir uygulamasını sağlaması gerektiği `Area` çünkü `Area` Özet devralınan `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="1bff7-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="1bff7-106">Bir `override` yöntemi, bir temel sınıftan devralınan bir üyenin yeni bir uygulamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="1bff7-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="1bff7-107">Yöntemi tarafından geçersiz kılınan bir `override` bildirimi geçersiz kılınan taban yöntemi bilinir.</span><span class="sxs-lookup"><span data-stu-id="1bff7-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="1bff7-108">Geçersiz kılınan taban yöntemi olarak aynı imzaya sahip olmalıdır `override` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1bff7-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="1bff7-109">Devralma hakkında daha fazla bilgi için bkz: [devralma](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="1bff7-109">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="1bff7-110">Sanal olmayan veya statik bir yöntemi geçersiz kılınamıyor.</span><span class="sxs-lookup"><span data-stu-id="1bff7-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="1bff7-111">Geçersiz kılınan taban yöntemi olmalıdır `virtual`, `abstract`, veya `override`.</span><span class="sxs-lookup"><span data-stu-id="1bff7-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="1bff7-112">Bir `override` bildirimi erişilebilirliğini değiştiremez `virtual` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1bff7-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="1bff7-113">Her iki `override` yöntemi ve `virtual` yöntemi aynı olmalıdır [erişim düzeyi değiştiricisi](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="1bff7-113">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="1bff7-114">Kullanamazsınız `new`, `static`, veya `virtual` değiştirmek için değiştiriciler bir `override` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1bff7-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="1bff7-115">Devralınan özellik olarak geçersiz kılan bir özellik bildirimi tam olarak aynı erişim değiştiricisi, türü ve adı belirtmeniz gerekir ve geçersiz kılınan özelliğin olmalıdır `virtual`, `abstract`, veya `override`.</span><span class="sxs-lookup"><span data-stu-id="1bff7-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="1bff7-116">Nasıl kullanılacağı hakkında daha fazla bilgi için `override` anahtar sözcüğü, bkz: [geçersiz kılma ve yeni anahtar sözcüklerle sürüm oluşturma](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) ve [geçersiz kılma ve yeni anahtar sözcüklerin ne zaman kullanılacağını bilme](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="1bff7-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="1bff7-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="1bff7-117">Example</span></span>

<span data-ttu-id="1bff7-118">Bu örnek adlı bir temel sınıf tanımlar `Employee`ve adlı bir türetilmiş sınıf `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="1bff7-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="1bff7-119">`SalesEmployee` Sınıfı içeren ek bir alan `salesbonus`ve metot geçersiz kılmaları `CalculatePay` hesaba katması için.</span><span class="sxs-lookup"><span data-stu-id="1bff7-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="1bff7-120">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="1bff7-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1bff7-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bff7-121">See also</span></span>

- [<span data-ttu-id="1bff7-122">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="1bff7-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1bff7-123">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="1bff7-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1bff7-124">Devralma</span><span class="sxs-lookup"><span data-stu-id="1bff7-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="1bff7-125">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="1bff7-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1bff7-126">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="1bff7-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="1bff7-127">abstract</span><span class="sxs-lookup"><span data-stu-id="1bff7-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="1bff7-128">virtual</span><span class="sxs-lookup"><span data-stu-id="1bff7-128">virtual</span></span>](virtual.md)
- [<span data-ttu-id="1bff7-129">new</span><span class="sxs-lookup"><span data-stu-id="1bff7-129">new</span></span>](new.md)
- [<span data-ttu-id="1bff7-130">Çok biçimlilik</span><span class="sxs-lookup"><span data-stu-id="1bff7-130">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
