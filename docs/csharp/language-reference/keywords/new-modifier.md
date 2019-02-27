---
title: New değiştiricisi - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
ms.openlocfilehash: d5fd244ea22fd48bf5b81d2cdf55127f745c145b
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835024"
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="6713b-102">New değiştiricisi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="6713b-102">new modifier (C# Reference)</span></span>

<span data-ttu-id="6713b-103">Bir bildirim değiştirici olarak kullanıldığında `new` anahtar sözcüğü açıkça bir temel sınıftan devralınan üyeyi gizler.</span><span class="sxs-lookup"><span data-stu-id="6713b-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="6713b-104">Devralınmış bir üyeyi gizlediğinizde, üyenin sürümü temel sınıftaki sürümün yerine geçer.</span><span class="sxs-lookup"><span data-stu-id="6713b-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="6713b-105">Üyeleri kullanmadan gizleyebilmenize rağmen `new` değiştiricisi, bir derleyici uyarısı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="6713b-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="6713b-106">Kullanırsanız `new` bir üyeyi açıkça gizlemek için bu uyarı bastırılır.</span><span class="sxs-lookup"><span data-stu-id="6713b-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>

<span data-ttu-id="6713b-107">Devralınan bir üyeyi gizlemek için türetilen sınıfta aynı üye adını kullanarak bildirin ve değiştirin `new` anahtar sözcüğü.</span><span class="sxs-lookup"><span data-stu-id="6713b-107">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="6713b-108">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="6713b-108">For example:</span></span>

[!code-csharp[csrefKeywordsOperator#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#8)]

<span data-ttu-id="6713b-109">Bu örnekte, `BaseC.Invoke` tarafından gizleniyor `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="6713b-109">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="6713b-110">Alan `x` çünkü benzer bir adla gizlenmediğinden etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="6713b-110">The field `x` is not affected because it is not hidden by a similar name.</span></span>

<span data-ttu-id="6713b-111">Devralma üzerinden ad gizleme aşağıdaki biçimlerden birini alır:</span><span class="sxs-lookup"><span data-stu-id="6713b-111">Name hiding through inheritance takes one of the following forms:</span></span>

- <span data-ttu-id="6713b-112">Genellikle, bir sabit, alan, özelliği veya bir sınıf veya yapı içinde tanıtılan türü kendi adını paylaşan tüm taban sınıfı üyelerini gizler.</span><span class="sxs-lookup"><span data-stu-id="6713b-112">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span>  <span data-ttu-id="6713b-113">Özel durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="6713b-113">There are special cases.</span></span>  <span data-ttu-id="6713b-114">Örneğin, adı ile yeni bir alan bildirmek `N` çağrılmayan bir tür ve temel tür olduğunu `N` bir yöntemi olması için yeni alan taban bildirimini çağırma sözdiziminde gizlemez.</span><span class="sxs-lookup"><span data-stu-id="6713b-114">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span>  <span data-ttu-id="6713b-115">Bkz: [5.0 C# dil belirtimi](https://www.microsoft.com/download/details.aspx?id=7029) için ayrıntıları ("Expressions" bölümünde "Üye arama" bölümüne bakın).</span><span class="sxs-lookup"><span data-stu-id="6713b-115">See the [C# 5.0 language specification](https://www.microsoft.com/download/details.aspx?id=7029) for details (see section "Member Lookup" in section "Expressions").</span></span>

- <span data-ttu-id="6713b-116">Bir sınıf ya da struct'a dahil edilen bir yöntem özellikleri, alanları ve temel sınıfta bu adı paylaşan türleri gizler.</span><span class="sxs-lookup"><span data-stu-id="6713b-116">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="6713b-117">Ayrıca, aynı imzaya sahip tüm taban sınıfı yöntemlerini gizler.</span><span class="sxs-lookup"><span data-stu-id="6713b-117">It also hides all base class methods that have the same signature.</span></span>

- <span data-ttu-id="6713b-118">Bir sınıf veya yapı içinde tanıtılan bir dizin oluşturucu, aynı imzaya sahip tüm taban sınıfı dizin oluşturucularını gizler.</span><span class="sxs-lookup"><span data-stu-id="6713b-118">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>

<span data-ttu-id="6713b-119">Her ikisi de kullanmak için bir hata olduğunu `new` ve [geçersiz kılma](override.md) aynı üyede, çünkü iki değiştirici karşılıklı özel anlamlara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6713b-119">It is an error to use both `new` and [override](override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="6713b-120">`new` Değiştiricisi, aynı ada sahip yeni bir üye oluşturur ve ilk üyenin gizli hale gelmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="6713b-120">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="6713b-121">`override` Değiştiricisi devralınan bir üyenin uygulanmasını genişletir.</span><span class="sxs-lookup"><span data-stu-id="6713b-121">The `override` modifier extends the implementation for an inherited member.</span></span>

<span data-ttu-id="6713b-122">Kullanarak `new` değiştiricisi devralınan bir üyeyi gizlemek olmayan bir bildirimde kullanmak bir uyarı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6713b-122">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>

## <a name="example"></a><span data-ttu-id="6713b-123">Örnek</span><span class="sxs-lookup"><span data-stu-id="6713b-123">Example</span></span>

<span data-ttu-id="6713b-124">Bu örnekte, bir temel sınıf `BaseC`ve bir türetilen sınıf `DerivedC`, aynı alan adını kullanan `x`, devralınan alandaki değeri gizleyen.</span><span class="sxs-lookup"><span data-stu-id="6713b-124">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="6713b-125">Bu örnek kullanımını gösterir `new` değiştiricisi.</span><span class="sxs-lookup"><span data-stu-id="6713b-125">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="6713b-126">Ayrıca bunların tam nitelikli adlarını kullanarak taban sınıfının gizlenmiş üyelerine nasıl erişileceğini gösteren.</span><span class="sxs-lookup"><span data-stu-id="6713b-126">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#9)]

## <a name="example"></a><span data-ttu-id="6713b-127">Örnek</span><span class="sxs-lookup"><span data-stu-id="6713b-127">Example</span></span>

<span data-ttu-id="6713b-128">Bu örnekte, iç içe geçmiş bir sınıf taban sınıfında aynı ada sahip bir sınıfı gizler.</span><span class="sxs-lookup"><span data-stu-id="6713b-128">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="6713b-129">Bu örnek nasıl kullanılacağını gösterir `new` değiştiricisi uyarı iletisini ve gizli sınıf üyelerine bunların tam nitelikli adlarını kullanarak erişmek nasıl ortadan kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="6713b-129">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>

[!code-csharp[csrefKeywordsOperator#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#10)]

<span data-ttu-id="6713b-130">Kaldırırsanız `new` değiştiricisi, program hala derler ve çalışır, ancak aşağıdaki uyarıyı alırsınız:</span><span class="sxs-lookup"><span data-stu-id="6713b-130">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>

```
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.
```

## <a name="c-language-specification"></a><span data-ttu-id="6713b-131">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6713b-131">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6713b-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6713b-132">See also</span></span>

- [<span data-ttu-id="6713b-133">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="6713b-133">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="6713b-134">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6713b-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6713b-135">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6713b-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6713b-136">İşleç Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="6713b-136">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="6713b-137">Değiştiriciler</span><span class="sxs-lookup"><span data-stu-id="6713b-137">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="6713b-138">Geçersiz Kılma ve Yeni Anahtar Sözcüklerle Sürüm Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6713b-138">Versioning with the Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)
- [<span data-ttu-id="6713b-139">Geçersiz Kılmanın ve Yeni Anahtar Sözcüklerin Ne Zaman Kullanılacağını Bilme</span><span class="sxs-lookup"><span data-stu-id="6713b-139">Knowing When to Use Override and New Keywords</span></span>](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
