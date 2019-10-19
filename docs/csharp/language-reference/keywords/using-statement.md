---
title: using deyimleri- C# başvuru
ms.custom: seodec18
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 7e6d1b663007d430f71f81923f343f1c43f5dd2d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579176"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="08cad-102">using deyimleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="08cad-102">using statement (C# Reference)</span></span>

<span data-ttu-id="08cad-103">@No__t_0 nesnelerinin doğru kullanımını sağlayan uygun bir sözdizimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="08cad-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="08cad-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="08cad-104">Example</span></span>

<span data-ttu-id="08cad-105">Aşağıdaki örnek, `using` deyimin nasıl kullanılacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="08cad-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

<span data-ttu-id="08cad-106">8,0 ile C# başlayarak, küme ayraçları gerektirmeyen `using` bildiri için aşağıdaki alternatif sözdizimini kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="08cad-106">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a><span data-ttu-id="08cad-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08cad-107">Remarks</span></span>

<span data-ttu-id="08cad-108"><xref:System.IO.File> ve <xref:System.Drawing.Font>, yönetilmeyen kaynaklara erişen yönetilen türlerin örnekleridir (Bu durumda dosya tutamaçları ve cihaz bağlamları).</span><span class="sxs-lookup"><span data-stu-id="08cad-108"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="08cad-109">Birçok farklı türde yönetilmeyen kaynak ve bunları kapsülleyen sınıf kitaplığı türleri vardır.</span><span class="sxs-lookup"><span data-stu-id="08cad-109">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="08cad-110">Bu tür türler <xref:System.IDisposable> arabirimini gerçekleştirmelidir.</span><span class="sxs-lookup"><span data-stu-id="08cad-110">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="08cad-111">Bir `IDisposable` nesnesinin kullanım ömrü tek bir yöntemle sınırlıysa, bunu `using` bildiriminde bildirmeniz ve oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="08cad-111">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="08cad-112">@No__t_0 ifade, nesne üzerinde <xref:System.IDisposable.Dispose%2A> yöntemini doğru şekilde çağırır ve (daha önce gösterildiği gibi kullandığınızda), <xref:System.IDisposable.Dispose%2A> çağrıldığında nesnenin kendisinin kapsam dışına geçmesine da neden olur.</span><span class="sxs-lookup"><span data-stu-id="08cad-112">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="08cad-113">@No__t_0 bloğunda, nesnesi salt okunurdur ve değiştirilemez ya da yeniden atanamaz.</span><span class="sxs-lookup"><span data-stu-id="08cad-113">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="08cad-114">@No__t_0 bildiri, `using` bloğunda bir özel durum gerçekleşse bile <xref:System.IDisposable.Dispose%2A> çağırılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="08cad-114">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="08cad-115">Nesneyi `try` bloğunun içine yerleştirerek ve sonra <xref:System.IDisposable.Dispose%2A> bir `finally` bloğunda çağırarak aynı sonucu elde edebilirsiniz; Aslında `using` deyimin derleyici tarafından çevrilme yöntemi budur.</span><span class="sxs-lookup"><span data-stu-id="08cad-115">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="08cad-116">Kod örneği, derleme zamanında aşağıdaki koda genişletilir (nesne için sınırlı kapsam oluşturmak için ek küme ayraçları aklınızda):</span><span class="sxs-lookup"><span data-stu-id="08cad-116">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="08cad-117">Yeni `using` deyimin sözdizimi, çok benzer bir koda çevrilir.</span><span class="sxs-lookup"><span data-stu-id="08cad-117">The newer `using` statement syntax translates to very similar code.</span></span> <span data-ttu-id="08cad-118">@No__t_0 bloğu, değişkenin bildirildiği yerde açılır.</span><span class="sxs-lookup"><span data-stu-id="08cad-118">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="08cad-119">@No__t_0 bloğu, genellikle bir yöntemin sonunda kapsayan bloğun yakın bir tarafında eklenir.</span><span class="sxs-lookup"><span data-stu-id="08cad-119">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="08cad-120">@No__t_0 - `finally` ifadesiyle ilgili daha fazla bilgi için, [try-finally](try-finally.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="08cad-120">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="08cad-121">Aşağıdaki örnekte gösterildiği gibi, bir türün birden çok örneği `using` bildiriminde bildirilebilecek:</span><span class="sxs-lookup"><span data-stu-id="08cad-121">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="08cad-122">Aynı türde birden çok bildirimi, C# 8 ' in yanı sıra sunulan yeni sözdizimini kullanarak birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="08cad-122">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well.</span></span> <span data-ttu-id="08cad-123">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="08cad-123">This is shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

<span data-ttu-id="08cad-124">Kaynak nesnesini örnekleyebilirsiniz ve sonra değişkeni `using` ifadesine geçirebilirsiniz, ancak bu en iyi yöntem değildir.</span><span class="sxs-lookup"><span data-stu-id="08cad-124">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="08cad-125">Bu durumda, denetim `using` bloğundan ayrıldıktan sonra nesne kapsamda kalır, büyük olasılıkla yönetilmeyen kaynaklarına erişemez.</span><span class="sxs-lookup"><span data-stu-id="08cad-125">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="08cad-126">Diğer bir deyişle, artık tam olarak başlatılamaz.</span><span class="sxs-lookup"><span data-stu-id="08cad-126">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="08cad-127">Nesneyi `using` bloğunun dışında kullanmaya çalışırsanız, bir özel durumun bir istisna olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="08cad-127">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="08cad-128">Bu nedenle, `using` deyimindeki nesnenin örneğini oluşturmak ve kapsamını `using` bloğu ile sınırlandırmak genellikle daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="08cad-128">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="08cad-129">@No__t_0 nesnelerini elden atma hakkında daha fazla bilgi için, bkz. [IDisposable uygulayan nesneleri kullanma](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="08cad-129">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="08cad-130">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="08cad-130">C# language specification</span></span>

<span data-ttu-id="08cad-131">Daha fazla bilgi için, [ C# dil belirtiminde](../language-specification/index.md) [using ifadesine](~/_csharplang/spec/statements.md#the-using-statement) bakın.</span><span class="sxs-lookup"><span data-stu-id="08cad-131">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="08cad-132">Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.</span><span class="sxs-lookup"><span data-stu-id="08cad-132">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="08cad-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08cad-133">See also</span></span>

- [<span data-ttu-id="08cad-134">C#Başvurunun</span><span class="sxs-lookup"><span data-stu-id="08cad-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="08cad-135">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="08cad-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="08cad-136">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="08cad-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="08cad-137">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="08cad-137">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="08cad-138">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="08cad-138">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="08cad-139">IDisposable uygulayan nesneleri kullanma</span><span class="sxs-lookup"><span data-stu-id="08cad-139">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="08cad-140">IDisposable arabirimi</span><span class="sxs-lookup"><span data-stu-id="08cad-140">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="08cad-141">8,0 içinde C# using deyimleri</span><span class="sxs-lookup"><span data-stu-id="08cad-141">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
