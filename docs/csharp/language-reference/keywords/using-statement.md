---
title: deyimi kullanarak - C# Reference
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: a237a90b4782e0460857c3d5d887771bcc8ccaaf
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989187"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="43530-102">deyimi kullanarak (C# Reference)</span><span class="sxs-lookup"><span data-stu-id="43530-102">using statement (C# Reference)</span></span>

<span data-ttu-id="43530-103"><xref:System.IDisposable> Nesnelerin doğru kullanımını sağlayan kullanışlı bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="43530-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span> <span data-ttu-id="43530-104">C# 8.0'dan `using` başlayarak, deyim <xref:System.IAsyncDisposable> nesnelerin doğru kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="43530-104">Beginning in C# 8.0, the `using` statement ensures the correct use of <xref:System.IAsyncDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="43530-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="43530-105">Example</span></span>

<span data-ttu-id="43530-106">Aşağıdaki örnek, deyimin `using` nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="43530-106">The following example shows how to use the `using` statement.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

<span data-ttu-id="43530-107">C# 8.0 ile başlayarak, ayraç gerektirmeyen `using` ifade için aşağıdaki alternatif sözdizimini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="43530-107">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a><span data-ttu-id="43530-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43530-108">Remarks</span></span>

<span data-ttu-id="43530-109"><xref:System.IO.File>ve <xref:System.Drawing.Font> yönetilmeyen kaynaklara erişen yönetilen türlere örneklerdir (bu durumda dosya işletmek ve aygıt bağlamları).</span><span class="sxs-lookup"><span data-stu-id="43530-109"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="43530-110">Yönetilmeyen kaynakların ve bunları kapsülleyen sınıf kitaplık türlerinin başka türleri de vardır.</span><span class="sxs-lookup"><span data-stu-id="43530-110">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="43530-111">Tüm bu tür <xref:System.IDisposable> arabirimi veya <xref:System.IAsyncDisposable> arabirimi uygulamalıdır.</span><span class="sxs-lookup"><span data-stu-id="43530-111">All such types must implement the <xref:System.IDisposable> interface, or the <xref:System.IAsyncDisposable> interface.</span></span>

<span data-ttu-id="43530-112">Bir `IDisposable` nesnenin ömrü tek bir yöntemle sınırlıysa, `using` bunu ifadede beyan etmeli ve anında bildirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="43530-112">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="43530-113">Deyim, `using` nesne <xref:System.IDisposable.Dispose%2A> üzerindeki yöntemi doğru şekilde çağırır ve (daha önce gösterildiği gibi kullandığınızda) nesnenin kendisini de <xref:System.IDisposable.Dispose%2A> çağrıldığı anda kapsam dışına çıkmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="43530-113">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="43530-114">`using` Blok içinde, nesne salt okunur ve değiştirilemez veya yeniden atanamaz.</span><span class="sxs-lookup"><span data-stu-id="43530-114">Within the `using` block, the object is read-only and can't be modified or reassigned.</span></span> <span data-ttu-id="43530-115">Nesne yerine `IAsyncDisposable` `IDisposable`uygularsa, `using` deyimi çağırır <xref:System.IAsyncDisposable.DisposeAsync%2A> `awaits` ve <xref:System.Threading.Tasks.Task>döndürülür.</span><span class="sxs-lookup"><span data-stu-id="43530-115">If the object implements `IAsyncDisposable` instead of `IDisposable`, the `using` statement calls the <xref:System.IAsyncDisposable.DisposeAsync%2A> and `awaits` the returned <xref:System.Threading.Tasks.Task>.</span></span>

<span data-ttu-id="43530-116">İfade, `using` <xref:System.IDisposable.Dispose%2A> `using` blok içinde <xref:System.IAsyncDisposable.DisposeAsync%2A>bir özel durum oluşsa bile (veya) çağrılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="43530-116">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="43530-117">Nesneyi `try` bir bloğun içine koyup (veya <xref:System.IDisposable.Dispose%2A> <xref:System.IAsyncDisposable.DisposeAsync%2A> bir `finally` blokta; aslında `using` deyim derleyici tarafından bu şekilde çevrilmiştir) çağırarak aynı sonucu elde edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43530-117">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="43530-118">Kod örneği daha önce derleme zamanında aşağıdaki koda genişletir (nesne için sınırlı kapsamı oluşturmak için ekstra kıvırcık ayraçlara dikkat edin):</span><span class="sxs-lookup"><span data-stu-id="43530-118">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

<span data-ttu-id="43530-119">Yeni `using` deyim sözdizimi benzer koda çevirir.</span><span class="sxs-lookup"><span data-stu-id="43530-119">The newer `using` statement syntax translates to similar code.</span></span> <span data-ttu-id="43530-120">Blok, `try` değişkenin beyan edildiği yerde açılır.</span><span class="sxs-lookup"><span data-stu-id="43530-120">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="43530-121">Blok, `finally` genellikle bir yöntemin sonunda, çevreleyen bloğun kapanışına eklenir.</span><span class="sxs-lookup"><span data-stu-id="43530-121">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="43530-122">İfade hakkında `try` - daha fazla bilgi [için, try-finally](try-finally.md) makalesine bakın. `finally`</span><span class="sxs-lookup"><span data-stu-id="43530-122">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) article.</span></span>

<span data-ttu-id="43530-123">Bir türün birden çok örneği, `using` aşağıdaki örnekte gösterildiği gibi tek bir deyimle bildirilebilir.</span><span class="sxs-lookup"><span data-stu-id="43530-123">Multiple instances of a type can be declared in a single `using` statement, as shown in the following example.</span></span> <span data-ttu-id="43530-124">Tek bir ifadede birden çok değişken ilettiğinizde örtülü olarak yazılan değişkenleri ()`var`kullanamayacağınızı unutmayın:</span><span class="sxs-lookup"><span data-stu-id="43530-124">Notice that you can't use implicitly typed variables (`var`) when you declare multiple variables in a single statement:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

<span data-ttu-id="43530-125">Aşağıdaki örnekte gösterildiği gibi, C# 8 ile tanıtılan yeni sözdizimini kullanarak aynı türden birden çok bildirimi birleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="43530-125">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

<span data-ttu-id="43530-126">Kaynak nesnesini anında anlayabilir ve sonra değişkeni `using` ifadeye geçirebilirsiniz, ancak bu en iyi uygulama değildir.</span><span class="sxs-lookup"><span data-stu-id="43530-126">You can instantiate the resource object and then pass the variable to the `using` statement, but this isn't a best practice.</span></span> <span data-ttu-id="43530-127">Bu durumda, denetim `using` bloğu terk ettikten sonra, nesne kapsamda kalır, ancak büyük olasılıkla yönetilmeyen kaynaklarına erişimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="43530-127">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="43530-128">Başka bir deyişle, artık tam olarak başharfe biçilemedi.</span><span class="sxs-lookup"><span data-stu-id="43530-128">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="43530-129">Nesneyi `using` bloğun dışında kullanmaya çalışırsanız, bir özel durum atılmasını göze alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="43530-129">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="43530-130">Bu nedenle, `using` nesnenin ifadedeki anlık olarak anlık olarak ve kapsamını `using` blokla sınırlamak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="43530-130">For this reason, it's better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

<span data-ttu-id="43530-131">`IDisposable` Nesnelerin atılması hakkında daha fazla bilgi için [bkz.](../../../standard/garbage-collection/using-objects.md)</span><span class="sxs-lookup"><span data-stu-id="43530-131">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="43530-132">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="43530-132">C# language specification</span></span>

<span data-ttu-id="43530-133">Daha fazla bilgi için [C# Language Specification'daki](/dotnet/csharp/language-reference/language-specification/introduction) [using deyimine](~/_csharplang/spec/statements.md#the-using-statement) bakın.</span><span class="sxs-lookup"><span data-stu-id="43530-133">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="43530-134">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="43530-134">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="43530-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43530-135">See also</span></span>

- [<span data-ttu-id="43530-136">C# Referans</span><span class="sxs-lookup"><span data-stu-id="43530-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="43530-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="43530-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="43530-138">C# Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="43530-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="43530-139">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="43530-139">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="43530-140">Çöp Toplama</span><span class="sxs-lookup"><span data-stu-id="43530-140">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="43530-141">IDisposable uygulayan nesneleri kullanma</span><span class="sxs-lookup"><span data-stu-id="43530-141">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="43530-142">IDisposable arayüzü</span><span class="sxs-lookup"><span data-stu-id="43530-142">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="43530-143">C# 8.0'da ifade kullanma</span><span class="sxs-lookup"><span data-stu-id="43530-143">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
