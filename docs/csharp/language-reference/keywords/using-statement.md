---
title: deyimi kullanarak - C# Reference
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 52cde99fd029ce50f159b2a87fbfbf47fc79dccc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712968"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="17ef3-102">deyimi kullanarak (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="17ef3-102">using statement (C# Reference)</span></span>

<span data-ttu-id="17ef3-103"><xref:System.IDisposable> Nesnelerin doğru kullanımını sağlayan kullanışlı bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="17ef3-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="17ef3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="17ef3-104">Example</span></span>

<span data-ttu-id="17ef3-105">Aşağıdaki örnek, deyimin `using` nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="17ef3-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

<span data-ttu-id="17ef3-106">C# 8.0 ile başlayarak, ayraç gerektirmeyen `using` ifade için aşağıdaki alternatif sözdizimini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17ef3-106">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a><span data-ttu-id="17ef3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="17ef3-107">Remarks</span></span>

<span data-ttu-id="17ef3-108"><xref:System.IO.File>ve <xref:System.Drawing.Font> yönetilmeyen kaynaklara erişen yönetilen türlere örneklerdir (bu durumda dosya işletmek ve aygıt bağlamları).</span><span class="sxs-lookup"><span data-stu-id="17ef3-108"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="17ef3-109">Yönetilmeyen kaynakların ve bunları kapsülleyen sınıf kitaplık türlerinin başka türleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="17ef3-109">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="17ef3-110">Tüm bu tür <xref:System.IDisposable> arabirimi uygulamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="17ef3-110">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="17ef3-111">Bir `IDisposable` nesnenin ömrü tek bir yöntemle sınırlıysa, `using` bunu ifadede beyan etmeli ve anında bildirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="17ef3-111">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="17ef3-112">Deyim, `using` nesne <xref:System.IDisposable.Dispose%2A> üzerindeki yöntemi doğru şekilde çağırır ve (daha önce gösterildiği gibi kullandığınızda) nesnenin kendisini de <xref:System.IDisposable.Dispose%2A> çağrıldığı anda kapsam dışına çıkmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="17ef3-112">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="17ef3-113">`using` Blok içinde, nesne salt okunur ve değiştirilemez veya yeniden atanamaz.</span><span class="sxs-lookup"><span data-stu-id="17ef3-113">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="17ef3-114">İfade, `using` `using` blok <xref:System.IDisposable.Dispose%2A> içinde bir özel durum oluşsa bile bunun çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="17ef3-114">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="17ef3-115">Nesneyi bir `try` bloğun içine koyup bir <xref:System.IDisposable.Dispose%2A> `finally` bloğu arayarak aynı sonuca ulaşabilirsiniz; aslında, `using` bu nasıl ifade derleyici tarafından tercüme edilir.</span><span class="sxs-lookup"><span data-stu-id="17ef3-115">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="17ef3-116">Kod örneği daha önce derleme zamanında aşağıdaki koda genişletir (nesne için sınırlı kapsamı oluşturmak için ekstra kıvırcık ayraçlara dikkat edin):</span><span class="sxs-lookup"><span data-stu-id="17ef3-116">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="17ef3-117">Yeni `using` ifade sözdizimi çok benzer koda çevirir.</span><span class="sxs-lookup"><span data-stu-id="17ef3-117">The newer `using` statement syntax translates to very similar code.</span></span> <span data-ttu-id="17ef3-118">Blok, `try` değişkenin beyan edildiği yerde açılır.</span><span class="sxs-lookup"><span data-stu-id="17ef3-118">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="17ef3-119">Blok, `finally` genellikle bir yöntemin sonunda, çevreleyen bloğun kapanışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="17ef3-119">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="17ef3-120">İfade hakkında `try` - daha fazla bilgi [için, try-finally](try-finally.md) konusuna bakın. `finally`</span><span class="sxs-lookup"><span data-stu-id="17ef3-120">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="17ef3-121">Aşağıdaki örnekte gösterildiği gibi, `using` bir türün birden çok örneği deyimde bildirilebilir:</span><span class="sxs-lookup"><span data-stu-id="17ef3-121">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="17ef3-122">C# 8 ile tanıtılan yeni sözdizimini kullanarak aynı türdeki birden çok bildirimi de birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17ef3-122">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well.</span></span> <span data-ttu-id="17ef3-123">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="17ef3-123">This is shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

<span data-ttu-id="17ef3-124">Kaynak nesnesini anında anlayabilir ve sonra değişkeni `using` ifadeye geçirebilirsiniz, ancak bu en iyi uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="17ef3-124">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="17ef3-125">Bu durumda, denetim `using` bloğu terk ettikten sonra, nesne kapsamda kalır, ancak büyük olasılıkla yönetilmeyen kaynaklarına erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="17ef3-125">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="17ef3-126">Başka bir deyişle, artık tam olarak başharfe biçilemedi.</span><span class="sxs-lookup"><span data-stu-id="17ef3-126">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="17ef3-127">Nesneyi `using` bloğun dışında kullanmaya çalışırsanız, bir özel durum atılmasını göze alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="17ef3-127">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="17ef3-128">Bu nedenle, `using` genellikle ifadedeki nesneyi anında anlayıp kapsamını blokla `using` sınırlamak genellikle daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="17ef3-128">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="17ef3-129">`IDisposable` Nesnelerin atılması hakkında daha fazla bilgi için [bkz.](../../../standard/garbage-collection/using-objects.md)</span><span class="sxs-lookup"><span data-stu-id="17ef3-129">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="17ef3-130">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="17ef3-130">C# language specification</span></span>

<span data-ttu-id="17ef3-131">Daha fazla bilgi için [C# Language Specification'daki](/dotnet/csharp/language-reference/language-specification/introduction) [using deyimine](~/_csharplang/spec/statements.md#the-using-statement) bakın.</span><span class="sxs-lookup"><span data-stu-id="17ef3-131">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="17ef3-132">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="17ef3-132">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="17ef3-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17ef3-133">See also</span></span>

- [<span data-ttu-id="17ef3-134">C# Referans</span><span class="sxs-lookup"><span data-stu-id="17ef3-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="17ef3-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="17ef3-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="17ef3-136">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="17ef3-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="17ef3-137">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="17ef3-137">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="17ef3-138">Çöp Toplama</span><span class="sxs-lookup"><span data-stu-id="17ef3-138">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="17ef3-139">IDisposable uygulayan nesneleri kullanma</span><span class="sxs-lookup"><span data-stu-id="17ef3-139">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="17ef3-140">IDisposable arayüzü</span><span class="sxs-lookup"><span data-stu-id="17ef3-140">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="17ef3-141">C# 8.0'da ifade kullanma</span><span class="sxs-lookup"><span data-stu-id="17ef3-141">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
