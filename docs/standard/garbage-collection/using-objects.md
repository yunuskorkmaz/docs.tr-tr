---
title: IDisposable uygulayan nesneleri kullanma
ms.date: 05/13/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: d0d55a9253fee1ffcfd5c10714a1118883f6c4ce
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396967"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="e145b-102">IDisposable uygulayan nesneleri kullanma</span><span class="sxs-lookup"><span data-stu-id="e145b-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="e145b-103">Ortak dil çalışma zamanının atık toplayıcısı, yönetilen nesneler tarafından kullanılan belleği geri kazanır, ancak yönetilmeyen kaynakları kullanan türler, <xref:System.IDisposable> Bu yönetilmeyen kaynakların gerektirdiği kaynakların geri kazanılabileceği şekilde arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="e145b-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the resources needed by these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="e145b-104">Uygulayan bir nesneyi kullanmayı bitirdiğinizde <xref:System.IDisposable> nesnenin uygulamasını çağırmanız gerekir <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e145b-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="e145b-105">Bunu iki yoldan biriyle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e145b-105">You can do this in one of two ways:</span></span>

- <span data-ttu-id="e145b-106">C# `using` ifadesiyle ( `Using` Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="e145b-106">With the C# `using` statement (`Using` in Visual Basic).</span></span>
- <span data-ttu-id="e145b-107">Bir blok uygulayarak `try/finally` ve içinde öğesini çağırarak <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> `finally` .</span><span class="sxs-lookup"><span data-stu-id="e145b-107">By implementing a `try/finally` block, and calling the <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> in the `finally`.</span></span>

## <a name="the-using-statement"></a><span data-ttu-id="e145b-108">Using deyimi</span><span class="sxs-lookup"><span data-stu-id="e145b-108">The using statement</span></span>

<span data-ttu-id="e145b-109">C# [ `using` ve içindeki deyimindeki ifade](../../csharp/language-reference/keywords/using-statement.md) , [ `Using` ](../../visual-basic/language-reference/statements/using-statement.md) bir nesneyi temizlemek için yazmanız gereken kodu basitleştirir Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e145b-109">The [`using` statement](../../csharp/language-reference/keywords/using-statement.md) in C# and the [`Using` statement](../../visual-basic/language-reference/statements/using-statement.md) in Visual Basic simplify the code that you must write to cleanup an object.</span></span> <span data-ttu-id="e145b-110">`using`Deyimi bir veya daha fazla kaynak edinir, belirttiğiniz deyimleri yürütür ve nesneyi otomatik olarak atar.</span><span class="sxs-lookup"><span data-stu-id="e145b-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="e145b-111">Ancak, `using` ifade yalnızca oluşturuldukları yöntemin kapsamı içinde kullanılan nesneler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e145b-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>

<span data-ttu-id="e145b-112">Aşağıdaki örnek, `using` bir nesnesi oluşturmak ve serbest bırakmak için ifadesini kullanır <xref:System.IO.StreamReader?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e145b-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

<span data-ttu-id="e145b-113">Sınıfı, <xref:System.IO.StreamReader> <xref:System.IDisposable> yönetilmeyen bir kaynak kullandığını belirten arabirimini uygular; ancak, örnek yöntemi açıkça çağırmaz <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e145b-113">Although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e145b-114">C# veya Visual Basic Derleyicisi `using` ifadesiyle karşılaştığında, açıkça bir blok içeren aşağıdaki koda denk olan ara dili (IL) yayar `try/finally` .</span><span class="sxs-lookup"><span data-stu-id="e145b-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

<span data-ttu-id="e145b-115">C# `using` deyimi Ayrıca, iç içe geçmiş deyimlere dahili olarak eşdeğer olan tek bir deyimde birden fazla kaynak almanızı sağlar `using` .</span><span class="sxs-lookup"><span data-stu-id="e145b-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="e145b-116">Aşağıdaki örnek <xref:System.IO.StreamReader> iki farklı dosyanın içeriğini okumak için iki nesne örneği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e145b-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="e145b-117">Try/finally bloğu</span><span class="sxs-lookup"><span data-stu-id="e145b-117">Try/finally block</span></span>

<span data-ttu-id="e145b-118">Bir deyime bir blok sarmalama yerine `try/finally` `using` , `try/finally` bloğu doğrudan uygulamayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e145b-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="e145b-119">Kişisel kodlama stiliniz olabilir veya bunu aşağıdaki nedenlerden biri için yapmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="e145b-119">It may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>

- <span data-ttu-id="e145b-120">`catch`Blokta oluşan özel durumları işlemek üzere bir blok eklemek için `try` .</span><span class="sxs-lookup"><span data-stu-id="e145b-120">To include a `catch` block to handle exceptions thrown in the `try` block.</span></span> <span data-ttu-id="e145b-121">Aksi takdirde, bildiriminde oluşturulan özel durumlar `using` işlenmemiş değildir.</span><span class="sxs-lookup"><span data-stu-id="e145b-121">Otherwise, any exceptions thrown within the `using` statement are unhandled.</span></span>

- <span data-ttu-id="e145b-122"><xref:System.IDisposable>Kapsamı, içinde bildirildiği bloğa yerel olmayan uygulayan bir nesne örneğini oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="e145b-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>

<span data-ttu-id="e145b-123">Aşağıdaki örnek, `try/catch/finally` bir nesnenin örneğini oluşturma, kullanma ve atma, <xref:System.IO.StreamReader> <xref:System.IO.StreamReader> Oluşturucu ve yöntemi tarafından oluşturulan özel durumları işlemek için bir blok kullanması dışında, önceki örneğe benzer <xref:System.IO.StreamReader.ReadToEnd%2A> .</span><span class="sxs-lookup"><span data-stu-id="e145b-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="e145b-124">Bloktaki kod, `finally` uygulayan nesnenin <xref:System.IDisposable> `null` yöntemini çağırmadan önce olmadığını denetler <xref:System.IDisposable.Dispose%2A> .</span><span class="sxs-lookup"><span data-stu-id="e145b-124">The code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="e145b-125">Bunun başarısız olması, <xref:System.NullReferenceException> çalışma zamanında bir özel durum oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e145b-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

<span data-ttu-id="e145b-126">`try/finally`Programlama diliniz bir ifadeyi desteklemediğinden, `using` ancak yönteme doğrudan çağrı yapmasına izin vereceğinden, bir blok uygulamayı uygulamayı veya uygulamayı tercih etmeniz gerekiyorsa, bu temel kalıbı izleyebilirsiniz <xref:System.IDisposable.Dispose%2A> .</span><span class="sxs-lookup"><span data-stu-id="e145b-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>

## <a name="idisposable-instance-members"></a><span data-ttu-id="e145b-127">IDisposable örnek üyeleri</span><span class="sxs-lookup"><span data-stu-id="e145b-127">IDisposable instance members</span></span>

<span data-ttu-id="e145b-128">Bir sınıf bir <xref:System.IDisposable> uygulama, bir alan veya özellik olan bir örnek üye olarak tutuyorsa, sınıf da uygulamalıdır <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="e145b-128">If a class holds an <xref:System.IDisposable> implementation as an instance member, either a field or a property, the class should also implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="e145b-129">Daha fazla bilgi için bkz. [Cascade Dispose uygulama](implementing-dispose.md#cascade-dispose-calls).</span><span class="sxs-lookup"><span data-stu-id="e145b-129">For more information, see [implement a cascade dispose](implementing-dispose.md#cascade-dispose-calls).</span></span>

## <a name="see-also"></a><span data-ttu-id="e145b-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e145b-130">See also</span></span>

- [<span data-ttu-id="e145b-131">Yönetilmeyen kaynakları Temizleme</span><span class="sxs-lookup"><span data-stu-id="e145b-131">Cleaning up unmanaged resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="e145b-132">using Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="e145b-132">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="e145b-133">Using Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e145b-133">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
