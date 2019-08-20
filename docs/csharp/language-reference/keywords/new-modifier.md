---
title: Yeni değiştirici C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: f62255be9c74a221836b23058bd48a835f38f629
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608621"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="3c868-102">Yeni değiştirici (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="3c868-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="3c868-103">Bir bildirim değiştiricisi `new` olarak kullanıldığında anahtar sözcüğü, temel sınıftan devralınan bir üyeyi açıkça gizler.</span><span class="sxs-lookup"><span data-stu-id="3c868-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="3c868-104">Devralınmış bir üyeyi gizlediğinizde, üyenin türetilmiş sürümü temel sınıf sürümünün yerini alır.</span><span class="sxs-lookup"><span data-stu-id="3c868-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="3c868-105">`new` Değiştiricisini kullanmadan üyeleri gizleyebilseniz de bir derleyici uyarısı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="3c868-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="3c868-106">Bir üyeyi açıkça `new` gizlemek için kullanırsanız, bu uyarıyı bastırır.</span><span class="sxs-lookup"><span data-stu-id="3c868-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="3c868-107">Anahtar sözcüğünü, `new` bir türün veya [genel tür kısıtlamasının](./new-constraint.md)bir [örneğini oluşturmak](../operators/new-operator.md) için de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c868-107">You can also use the `new` keyword to [create an instance of a type](../operators/new-operator.md) or as a [generic type constraint](./new-constraint.md).</span></span>

<span data-ttu-id="3c868-108">Devralınan bir üyeyi gizlemek için, aynı üye adını kullanarak türetilmiş sınıfta bildirin ve `new` anahtar sözcüğü ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="3c868-108">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="3c868-109">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3c868-109">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="3c868-110">Bu örnekte, `BaseC.Invoke` tarafından `DerivedC.Invoke`gizlenir.</span><span class="sxs-lookup"><span data-stu-id="3c868-110">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="3c868-111">Bu alan `x` , benzer bir adla gizlenmediği için etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="3c868-111">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="3c868-112">Devralma yoluyla ad gizleme aşağıdaki biçimlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="3c868-112">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="3c868-113">Genellikle, bir sınıfta veya yapıda tanıtılan bir sabit, alan, özellik veya tür, adını paylaşan tüm temel sınıf üyelerini gizler.</span><span class="sxs-lookup"><span data-stu-id="3c868-113">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span> <span data-ttu-id="3c868-114">Özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="3c868-114">There are special cases.</span></span> <span data-ttu-id="3c868-115">Örneğin, bir adı `N` olan yeni bir alanı, Not olmayan bir türe sahip olacak şekilde bildirirseniz ve temel tür bir yöntem olduğunu bildirirse `N` , yeni alan, çağırma sözdiziminde temel bildirimi gizlemez.</span><span class="sxs-lookup"><span data-stu-id="3c868-115">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span> <span data-ttu-id="3c868-116">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [üye arama](~/_csharplang/spec/expressions.md#member-lookup) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3c868-116">For more information, see the [Member lookup](~/_csharplang/spec/expressions.md#member-lookup) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

- <span data-ttu-id="3c868-117">Bir sınıf veya yapı içinde tanıtılan bir yöntem, temel sınıfta bu adı paylaşan özellikleri, alanları ve türleri gizler.</span><span class="sxs-lookup"><span data-stu-id="3c868-117">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="3c868-118">Aynı imzaya sahip tüm temel sınıf yöntemlerini de gizler.</span><span class="sxs-lookup"><span data-stu-id="3c868-118">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="3c868-119">Bir sınıf veya yapı içinde tanıtılan bir Dizin Oluşturucu, aynı imzaya sahip olan tüm temel sınıf dizin oluşturucularının gizlenmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c868-119">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="3c868-120">İki değiştiricinin birbirini dışlamalı anlamları `new` olduğundan, aynı üye üzerinde hem hem de [geçersiz kılma](override.md) kullanılması hatadır.</span><span class="sxs-lookup"><span data-stu-id="3c868-120">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="3c868-121">`new` Değiştirici aynı ada sahip yeni bir üye oluşturur ve orijinal üyenin gizli hale gelmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="3c868-121">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="3c868-122">`override` Değiştirici, devralınan bir üyenin uygulamasını genişletir.</span><span class="sxs-lookup"><span data-stu-id="3c868-122">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="3c868-123">Devralınmış bir üyeyi gizlemez bir bildirimde değiştiricininkullanılmasıbiruyarıoluşturur.`new`</span><span class="sxs-lookup"><span data-stu-id="3c868-123">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="3c868-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c868-124">Example</span></span>

<span data-ttu-id="3c868-125">Bu örnekte, bir temel sınıf, `BaseC`ve türetilmiş bir `DerivedC`sınıf, devralınan alanın değerini gizleyen aynı alan adını `x`kullanır.</span><span class="sxs-lookup"><span data-stu-id="3c868-125">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="3c868-126">Örnek, `new` değiştiricinin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c868-126">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="3c868-127">Ayrıca, temel sınıfın gizli üyelerine tam nitelikli adlarını kullanarak nasıl erişileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c868-127">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="3c868-128">Örnek</span><span class="sxs-lookup"><span data-stu-id="3c868-128">Example</span></span>

<span data-ttu-id="3c868-129">Bu örnekte, iç içe yerleştirilmiş bir sınıf, temel sınıfta aynı ada sahip bir sınıfı gizler.</span><span class="sxs-lookup"><span data-stu-id="3c868-129">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="3c868-130">Örnek, uyarı iletisini ortadan kaldırmak ve `new` tam nitelikli adlarını kullanarak gizli sınıf üyelerine erişmek için değiştiricinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="3c868-130">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="3c868-131">`new` Değiştirici kaldırırsanız, program derleme ve çalıştırmaya devam eder, ancak şu uyarıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="3c868-131">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```text
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="3c868-132">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="3c868-132">C# language specification</span></span>

<span data-ttu-id="3c868-133">Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Yeni değiştirici](~/_csharplang/spec/classes.md#the-new-modifier) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3c868-133">For more information, see [The new modifier](~/_csharplang/spec/classes.md#the-new-modifier) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c868-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3c868-134">See also</span></span>

- [<span data-ttu-id="3c868-135">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="3c868-135">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="3c868-136">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="3c868-136">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3c868-137">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="3c868-137">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3c868-138">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="3c868-138">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="3c868-139">Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3c868-139">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="3c868-140">Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme</span><span class="sxs-lookup"><span data-stu-id="3c868-140">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
