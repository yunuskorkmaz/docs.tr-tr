---
title: yeni değiştirici - C# Referans
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 6c4fedd469efb79f91780dff26da89b586de2d1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713339"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="e2a2a-102">yeni değiştirici (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="e2a2a-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="e2a2a-103">Bildirim değiştiricisi olarak kullanıldığında, `new` anahtar kelime taban sınıftan devralınan bir üyeyi açıkça gizler.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="e2a2a-104">Devralınan bir üyeyi gizlediğinizde, üyenin türetilmiş sürümü taban sınıf sürümünün yerini alır.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="e2a2a-105">Değiştiriciyi kullanmadan `new` üyeleri gizleyebilirsiniz, ancak derleyici uyarısı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="e2a2a-106">Bir üyeyi açıkça gizlemek için kullanırsanız, `new` bu uyarıyı bastırır.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="e2a2a-107">Anahtar kelimeyi, `new` bir [tür örneğini oluşturmak](../operators/new-operator.md) veya genel bir [tür kısıtlaması](./new-constraint.md)olarak da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="e2a2a-108">Devralınan bir üyeyi gizlemek için, aynı üye adını kullanarak türetilmiş `new` sınıfta bildirin ve anahtar kelimeyle değiştirin.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="e2a2a-109">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e2a2a-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="e2a2a-110">Bu örnekte, `BaseC.Invoke` `DerivedC.Invoke`tarafından gizlidir.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="e2a2a-111">`x` Alan, benzer bir adla gizlenmediği için etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="e2a2a-112">Devralma yoluyla gizlenen ad aşağıdaki formlardan birini alır:</span><span class="sxs-lookup"><span data-stu-id="e2a2a-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="e2a2a-113">Genellikle, bir sınıfveya yapıda tanıtılan bir sabit, alan, özellik veya tür, adını paylaşan tüm taban sınıf üyelerini gizler.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="e2a2a-114">Özel durumlar var.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-114">There are special cases.</span></span> <span data-ttu-id="e2a2a-115">Örneğin, adı `N` olan yeni bir alanı, çağrılamayan bir türe sahip olarak bildirirseniz ve bir taban türü bir yöntem olarak bildirirse, `N` yeni alan temel bildirimi çağırma sözdiziminde gizlemez.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="e2a2a-116">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Üye arama](~/_csharplang/spec/expressions.md#member-lookup) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="e2a2a-117">Bir sınıf veya yapıda tanıtılan bir yöntem, bu adı taban sınıfta paylaşan özellikleri, alanları ve türleri gizler.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="e2a2a-118">Ayrıca, aynı imzaya sahip tüm taban sınıf yöntemlerini gizler.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="e2a2a-119">Bir sınıf veya yapıda tanıtılan bir dizinleyici, aynı imzaya sahip tüm taban sınıf dizinleyicilerini gizler.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="e2a2a-120">İki değiştiricinin birbirini `new` dışlayan anlamları olduğundan, her ikisini de kullanmak ve aynı üyeüzerinde [geçersiz kılmak](override.md) bir hatadır.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="e2a2a-121">`new` Değiştirici aynı ada sahip yeni bir üye oluşturur ve özgün üyenin gizlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="e2a2a-122">`override` Değiştirici, devralınan bir üyeiçin uygulamayı genişletir.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="e2a2a-123">Devralınan `new` bir üyeyi gizlemeyen bir bildirimde değiştiricinin kullanılması bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="e2a2a-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2a2a-124">Example</span></span>

<span data-ttu-id="e2a2a-125">Bu örnekte, bir `BaseC`taban sınıf ve `DerivedC`türetilmiş sınıf, `x`devralınan alanın değerini gizleyen aynı alan adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="e2a2a-126">`new` Örnek, değiştiricinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="e2a2a-127">Ayrıca, tam nitelikli adlarını kullanarak taban sınıfın gizli üyelerine nasıl erişeceklerini de gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="e2a2a-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="e2a2a-128">Example</span></span>

<span data-ttu-id="e2a2a-129">Bu örnekte, iç içe geçen bir sınıf, taban sınıfta aynı ada sahip bir sınıfı gizler.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="e2a2a-130">Örnek, uyarı iletisini `new` ortadan kaldırmak için değiştiricinin nasıl kullanılacağını ve tam nitelikli adlarını kullanarak gizli sınıf üyelerine nasıl erişeceklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="e2a2a-131">`new` Değiştiriyi kaldırırsanız, program yine derleyip çalışır, ancak aşağıdaki uyarıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="e2a2a-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="e2a2a-132">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e2a2a-132">C# language specification</span></span>

<span data-ttu-id="e2a2a-133">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yeni değiştirici](~/_csharplang/spec/classes.md#the-new-modifier) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2a2a-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2a2a-134">See also</span></span>

- [<span data-ttu-id="e2a2a-135">C# Referans</span><span class="sxs-lookup"><span data-stu-id="e2a2a-135">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="e2a2a-136">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e2a2a-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e2a2a-137">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="e2a2a-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e2a2a-138">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="e2a2a-138">Modifiers</span></span>](index.md)
- [<span data-ttu-id="e2a2a-139">Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e2a2a-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="e2a2a-140">Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme</span><span class="sxs-lookup"><span data-stu-id="e2a2a-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
