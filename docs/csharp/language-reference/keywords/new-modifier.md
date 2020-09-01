---
description: Yeni değiştirici-C# başvurusu
title: Yeni değiştirici-C# başvurusu
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: 2da0a360868250169fb16380c80bf32c4b335d7a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139417"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="5db09-103">New değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="5db09-103">new modifier (C# Reference)</span></span>

<span data-ttu-id="5db09-104">Bir bildirim değiştiricisi olarak kullanıldığında `new` anahtar sözcüğü, temel sınıftan devralınan bir üyeyi açıkça gizler.</span><span class="sxs-lookup"><span data-stu-id="5db09-104">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="5db09-105">Devralınmış bir üyeyi gizlediğinizde, üyenin türetilmiş sürümü temel sınıf sürümünün yerini alır.</span><span class="sxs-lookup"><span data-stu-id="5db09-105">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="5db09-106">Değiştiricisini kullanmadan üyeleri gizleyebilseniz de `new` bir derleyici uyarısı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="5db09-106">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="5db09-107">`new`Bir üyeyi açıkça gizlemek için kullanırsanız, bu uyarıyı bastırır.</span><span class="sxs-lookup"><span data-stu-id="5db09-107">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="5db09-108">`new`Anahtar sözcüğünü, [bir türün](../operators/new-operator.md) veya [genel tür kısıtlamasının](./new-constraint.md)bir örneğini oluşturmak için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5db09-108">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="5db09-109">Devralınan bir üyeyi gizlemek için, aynı üye adını kullanarak türetilmiş sınıfta bildirin ve `new` anahtar sözcüğü ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="5db09-109">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="5db09-110">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5db09-110">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="5db09-111">Bu örnekte, `BaseC.Invoke` tarafından gizlenir `DerivedC.Invoke` .</span><span class="sxs-lookup"><span data-stu-id="5db09-111">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="5db09-112">Bu alan, `x` benzer bir adla gizlenmediği için etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="5db09-112">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="5db09-113">Devralma yoluyla ad gizleme aşağıdaki biçimlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="5db09-113">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="5db09-114">Genellikle, bir sınıfta veya yapıda tanıtılan bir sabit, alan, özellik veya tür, adını paylaşan tüm temel sınıf üyelerini gizler.</span><span class="sxs-lookup"><span data-stu-id="5db09-114">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="5db09-115">Özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="5db09-115">There are special cases.</span></span> <span data-ttu-id="5db09-116">Örneğin, bir adı olan yeni bir alanı `N` , Not olmayan bir türe sahip olacak şekilde bildirirseniz ve temel tür `N` bir yöntem olduğunu bildirirse, yeni alan, çağırma sözdiziminde temel bildirimi gizlemez.</span><span class="sxs-lookup"><span data-stu-id="5db09-116">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="5db09-117">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [üye arama](~/_csharplang/spec/expressions.md#member-lookup) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5db09-117">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="5db09-118">Bir sınıf veya yapı içinde tanıtılan bir yöntem, temel sınıfta bu adı paylaşan özellikleri, alanları ve türleri gizler.</span><span class="sxs-lookup"><span data-stu-id="5db09-118">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="5db09-119">Aynı imzaya sahip tüm temel sınıf yöntemlerini de gizler.</span><span class="sxs-lookup"><span data-stu-id="5db09-119">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="5db09-120">Bir sınıf veya yapı içinde tanıtılan bir Dizin Oluşturucu, aynı imzaya sahip olan tüm temel sınıf dizin oluşturucularının gizlenmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5db09-120">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="5db09-121">`new`İki değiştiricinin birbirini dışlamalı anlamları olduğundan, aynı üye üzerinde hem hem de [geçersiz kılma](override.md) kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="5db09-121">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="5db09-122">`new`Değiştirici aynı ada sahip yeni bir üye oluşturur ve orijinal üyenin gizli hale gelmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="5db09-122">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="5db09-123">`override`Değiştirici, devralınan bir üyenin uygulamasını genişletir.</span><span class="sxs-lookup"><span data-stu-id="5db09-123">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="5db09-124">Devralınmış bir `new` üyeyi gizlemez bir bildirimde değiştiricinin kullanılması bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5db09-124">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="5db09-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="5db09-125">Example</span></span>

<span data-ttu-id="5db09-126">Bu örnekte, bir temel sınıf, `BaseC` ve türetilmiş bir sınıf, `DerivedC` `x` devralınan alanın değerini gizleyen aynı alan adını kullanır.</span><span class="sxs-lookup"><span data-stu-id="5db09-126">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="5db09-127">Örnek, `new` değiştiricinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5db09-127">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="5db09-128">Ayrıca, temel sınıfın gizli üyelerine tam nitelikli adlarını kullanarak nasıl erişileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="5db09-128">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="5db09-129">Örnek</span><span class="sxs-lookup"><span data-stu-id="5db09-129">Example</span></span>

<span data-ttu-id="5db09-130">Bu örnekte, iç içe yerleştirilmiş bir sınıf, temel sınıfta aynı ada sahip bir sınıfı gizler.</span><span class="sxs-lookup"><span data-stu-id="5db09-130">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="5db09-131">Örnek, `new` uyarı iletisini ortadan kaldırmak ve tam nitelikli adlarını kullanarak gizli sınıf üyelerine erişmek için değiştiricinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5db09-131">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="5db09-132">Değiştirici kaldırırsanız, `new` program derleme ve çalıştırmaya devam eder, ancak şu uyarıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="5db09-132">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="5db09-133">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="5db09-133">C# language specification</span></span>

<span data-ttu-id="5db09-134">Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni değiştirici](~/_csharplang/spec/classes.md#the-new-modifier) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5db09-134">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5db09-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5db09-135">See also</span></span>

- [<span data-ttu-id="5db09-136">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="5db09-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5db09-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5db09-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5db09-138">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5db09-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="5db09-139">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="5db09-139">Modifiers</span></span>](index.md)
- [<span data-ttu-id="5db09-140">Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="5db09-140">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="5db09-141">Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme</span><span class="sxs-lookup"><span data-stu-id="5db09-141">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
