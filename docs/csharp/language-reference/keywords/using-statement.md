---
title: using deyimleri-C# başvurusu
ms.date: 04/07/2020
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 3c479faeeb66865b8c368edba881429a7cb956ec
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199683"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="fc4b1-102">using deyimleri (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="fc4b1-102">using statement (C# Reference)</span></span>

<span data-ttu-id="fc4b1-103"><xref:System.IDisposable> Nesnelerin doğru kullanımını sağlayan uygun bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span> <span data-ttu-id="fc4b1-104">C# 8,0 ' `using` den başlayarak, ifade <xref:System.IAsyncDisposable> nesnelerin doğru kullanımını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-104">Beginning in C# 8.0, the `using` statement ensures the correct use of <xref:System.IAsyncDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="fc4b1-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="fc4b1-105">Example</span></span>

<span data-ttu-id="fc4b1-106">Aşağıdaki örnek, `using` ifadesinin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-106">The following example shows how to use the `using` statement.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetFirstExample":::

<span data-ttu-id="fc4b1-107">C# 8,0 ' den başlayarak, küme ayraçları gerektirmeyen `using` ifade için aşağıdaki alternatif sözdizimini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fc4b1-107">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernUsing":::

## <a name="remarks"></a><span data-ttu-id="fc4b1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fc4b1-108">Remarks</span></span>

<span data-ttu-id="fc4b1-109"><xref:System.IO.File>ve <xref:System.Drawing.Font> yönetilmeyen kaynaklara erişen yönetilen türlerin örnekleridir (Bu durumda dosya tutamaçları ve cihaz bağlamları).</span><span class="sxs-lookup"><span data-stu-id="fc4b1-109"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="fc4b1-110">Birçok farklı türde yönetilmeyen kaynak ve bunları kapsülleyen sınıf kitaplığı türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-110">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="fc4b1-111">Bu tür türler <xref:System.IDisposable> arabirimini veya <xref:System.IAsyncDisposable> arabirimini gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-111">All such types must implement the <xref:System.IDisposable> interface, or the <xref:System.IAsyncDisposable> interface.</span></span>

<span data-ttu-id="fc4b1-112">Bir `IDisposable` nesnenin yaşam süresi tek bir yöntemle sınırlı olduğunda, bu örneği `using` bildiriminde belirtmeniz ve oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-112">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="fc4b1-113">`using` İfade, <xref:System.IDisposable.Dispose%2A> yöntemi nesnesi üzerinde doğru şekilde çağırır ve (daha önce gösterildiği gibi kullandığınızda), bu da nesnenin kendisinin kapsam <xref:System.IDisposable.Dispose%2A> dışına geçmesine neden olur ve çağrılır.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-113">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="fc4b1-114">`using` Blok içinde, nesne salt okunurdur ve değiştirilemez ya da yeniden atanamaz.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-114">Within the `using` block, the object is read-only and can't be modified or reassigned.</span></span> <span data-ttu-id="fc4b1-115">Nesnesi yerine uygularsa `IAsyncDisposable` , `IDisposable` `using` <xref:System.IAsyncDisposable.DisposeAsync%2A> ifade öğesini ve `awaits` döndürülen <xref:System.Threading.Tasks.Task>öğesini çağırır.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-115">If the object implements `IAsyncDisposable` instead of `IDisposable`, the `using` statement calls the <xref:System.IAsyncDisposable.DisposeAsync%2A> and `awaits` the returned <xref:System.Threading.Tasks.Task>.</span></span>

<span data-ttu-id="fc4b1-116">Bu `using` <xref:System.IDisposable.Dispose%2A> ifade, `using` bloğunda bir özel <xref:System.IAsyncDisposable.DisposeAsync%2A>durum gerçekleşse bile (veya) çağrısı yapılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-116">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="fc4b1-117">Nesneyi bir `try` bloğun içine yerleştirerek ve sonra da (veya <xref:System.IDisposable.Dispose%2A> <xref:System.IAsyncDisposable.DisposeAsync%2A>) bir `finally` blokta çağırarak aynı sonucu elde edebilirsiniz; Aslında, `using` deyimin derleyici tarafından çevrilme yöntemi budur.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-117">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> (or <xref:System.IAsyncDisposable.DisposeAsync%2A>) in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="fc4b1-118">Kod örneği, derleme zamanında aşağıdaki koda genişletilir (nesne için sınırlı kapsam oluşturmak için ek küme ayraçları aklınızda):</span><span class="sxs-lookup"><span data-stu-id="fc4b1-118">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetTryFinallyExample":::

<span data-ttu-id="fc4b1-119">Daha yeni `using` ifade söz dizimi benzer bir koda dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-119">The newer `using` statement syntax translates to similar code.</span></span> <span data-ttu-id="fc4b1-120">`try` Blok, değişkenin bildirildiği yerde açılır.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-120">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="fc4b1-121">`finally` Blok, genellikle bir yöntemin sonunda kapsayan bloğa yakın bir zamanda eklenir.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-121">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="fc4b1-122">İfadesiyle ilgili `try` - daha fazla bilgi için bkz. [try-finally](try-finally.md) makalesi. `finally`</span><span class="sxs-lookup"><span data-stu-id="fc4b1-122">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) article.</span></span>

<span data-ttu-id="fc4b1-123">Aşağıdaki örnekte gösterildiği gibi, bir türün birden çok örneği tek `using` bir bildirimde bildirilebilecek.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-123">Multiple instances of a type can be declared in a single `using` statement, as shown in the following example.</span></span> <span data-ttu-id="fc4b1-124">Tek bir ifadede birden çok değişken bildirdiğinizde örtük olarak`var`yazılmış değişkenleri () kullanamıyoruz.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-124">Notice that you can't use implicitly typed variables (`var`) when you declare multiple variables in a single statement:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareMultipleVariables":::

<span data-ttu-id="fc4b1-125">Aşağıdaki örnekte gösterildiği gibi, C# 8 ile sunulan yeni sözdizimini kullanarak aynı türdeki birden çok bildirimi birleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fc4b1-125">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetModernMultipleVariables":::

<span data-ttu-id="fc4b1-126">Kaynak nesnesini örnekleyebilirsiniz ve sonra değişkeni `using` ifadeye geçirebilirsiniz, ancak bu en iyi yöntem değildir.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-126">You can instantiate the resource object and then pass the variable to the `using` statement, but this isn't a best practice.</span></span> <span data-ttu-id="fc4b1-127">Bu durumda, Denetim `using` bloğundan ayrıldıktan sonra nesne kapsamda kalır, büyük olasılıkla yönetilmeyen kaynaklarına erişemez.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-127">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="fc4b1-128">Diğer bir deyişle, artık tam olarak başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-128">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="fc4b1-129">Nesneyi `using` bloğunun dışında kullanmaya çalışırsanız, bir özel durumun oluşturulması riskiyle karşılaşırsınız.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-129">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="fc4b1-130">Bu nedenle, `using` deyimindeki nesnenin örneğini oluşturmak ve kapsamını `using` bloğa sınırlamak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-130">For this reason, it's better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

:::code language="csharp" source="snippets/usings.cs" id="SnippetDeclareBeforeUsing":::

<span data-ttu-id="fc4b1-131">`IDisposable` Nesneleri elden atma hakkında daha fazla bilgi için bkz. [IDisposable uygulayan nesneleri kullanma](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="fc4b1-131">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fc4b1-132">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="fc4b1-132">C# language specification</span></span>

<span data-ttu-id="fc4b1-133">Daha fazla bilgi için [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [using ifadesine](~/_csharplang/spec/statements.md#the-using-statement) bakın.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-133">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="fc4b1-134">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-134">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="fc4b1-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc4b1-135">See also</span></span>

- [<span data-ttu-id="fc4b1-136">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="fc4b1-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fc4b1-137">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="fc4b1-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fc4b1-138">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="fc4b1-138">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fc4b1-139">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="fc4b1-139">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="fc4b1-140">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="fc4b1-140">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="fc4b1-141">IDisposable uygulayan nesneleri kullanma</span><span class="sxs-lookup"><span data-stu-id="fc4b1-141">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="fc4b1-142">IDisposable arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc4b1-142">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="fc4b1-143">C# 8,0 ' de using deyimleri</span><span class="sxs-lookup"><span data-stu-id="fc4b1-143">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
