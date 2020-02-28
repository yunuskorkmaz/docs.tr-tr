---
title: IDisposable uygulayan nesneleri kullanma
ms.date: 04/07/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: c5232aa89064c514e71f3a18bc754159e9c9b15b
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160292"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="cbbd5-102">IDisposable uygulayan nesneleri kullanma</span><span class="sxs-lookup"><span data-stu-id="cbbd5-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="cbbd5-103">Ortak dil çalışma zamanının atık toplayıcısı, yönetilen nesneler tarafından kullanılan belleği geri kazanır, ancak yönetilmeyen kaynakları kullanan türler, bu yönetilmeyen kaynaklara ayrılan belleğin geri kazanılmaya izin vermek için <xref:System.IDisposable> arabirimini uygular.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="cbbd5-104"><xref:System.IDisposable>uygulayan bir nesneyi kullanmayı bitirdiğinizde nesnenin <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamasını çağırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="cbbd5-105">Bunu iki yoldan biriyle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cbbd5-105">You can do this in one of two ways:</span></span>  
  
- <span data-ttu-id="cbbd5-106">C# `using` ifadesiyle veya Visual Basic `Using` ifadesiyle.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
- <span data-ttu-id="cbbd5-107">`try/finally` bir blok uygulayarak.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="cbbd5-108">Using deyimi</span><span class="sxs-lookup"><span data-stu-id="cbbd5-108">The using statement</span></span>

<span data-ttu-id="cbbd5-109">İçindeki `using` ve içindeki C# `Using` ifadesinde Visual Basic, bir nesneyi oluşturmak ve temizlemek için yazmanız gereken kodu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="cbbd5-110">`using` deyimi bir veya daha fazla kaynak edinir, belirttiğiniz deyimleri yürütür ve nesneyi otomatik olarak atar.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="cbbd5-111">Ancak `using` deyimleri yalnızca oluşturuldukları yöntemin kapsamı içinde kullanılan nesneler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="cbbd5-112">Aşağıdaki örnek, bir <xref:System.IO.StreamReader?displayProperty=nameWithType> nesnesini oluşturmak ve serbest bırakmak için `using` ifadesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="cbbd5-113"><xref:System.IO.StreamReader> sınıfı, yönetilmeyen bir kaynak kullandığını gösteren <xref:System.IDisposable> arabirimini uygulasa da, örneğin <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> yöntemini açıkça çağırmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="cbbd5-114">C# Veya Visual Basic Derleyicisi `using` bildirimiyle karşılaştığında, açıkça bir `try/finally` bloğunu içeren aşağıdaki koda denk olan ara DILI (IL) yayar.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="cbbd5-115">C# `using` deyimi, iç içe `using` deyimlerine dahili olarak eşdeğer olan tek bir deyimde birden fazla kaynak elde etmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="cbbd5-116">Aşağıdaki örnek iki farklı dosyanın içeriğini okumak için iki <xref:System.IO.StreamReader> nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="cbbd5-117">Try/finally bloğu</span><span class="sxs-lookup"><span data-stu-id="cbbd5-117">Try/finally block</span></span>

<span data-ttu-id="cbbd5-118">Bir `using` bildiriminde `try/finally` bloğunu sarmalama yerine, `try/finally` bloğunu doğrudan uygulamayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="cbbd5-119">Bu sizin kişisel kodlama stiliniz olabilir veya bunu aşağıdaki nedenlerden biri dolayısıyla yapmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="cbbd5-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
- <span data-ttu-id="cbbd5-120">`try` bloğunda oluşan tüm özel durumları işlemek üzere bir `catch` bloğu eklemek için.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="cbbd5-121">Aksi takdirde, bir `try/catch` bloğu yoksa, `using` bloğunda oluşturulan özel durumlar gibi `using` ifadesiyle oluşturulan özel durumlar da işlenmez.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
- <span data-ttu-id="cbbd5-122">Kapsamı, içinde bildirildiği bloğa yerel olmayan <xref:System.IDisposable> uygulayan bir nesne oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="cbbd5-123">Aşağıdaki örnek, bir önceki örneğe benzerdir, ancak bir <xref:System.IO.StreamReader> nesnesinin örneğini oluşturmak, kullanmak ve atmak ve <xref:System.IO.StreamReader> Oluşturucusu ve <xref:System.IO.StreamReader.ReadToEnd%2A> yöntemi tarafından oluşturulan tüm özel durumları işlemek için `try/catch/finally` bir blok kullanması dışında.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="cbbd5-124">`finally` bloğundaki kodun, <xref:System.IDisposable.Dispose%2A> yöntemini çağırmadan önce <xref:System.IDisposable> uygulayan nesnenin `null` olmadığını kontrol ettiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="cbbd5-125">Bunun yapılmaması, çalışma zamanında <xref:System.NullReferenceException> özel durumuyla sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="cbbd5-126">Programlama diliniz bir `using` ifadesini desteklemediğinden, ancak <xref:System.IDisposable.Dispose%2A> yöntemine doğrudan çağrılara izin veren bir `try/finally` bloğunu uygulamayı tercih etmeniz veya uygulamanız gerekiyorsa, bu temel kalıbı izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="cbbd5-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-127">See also</span></span>

- [<span data-ttu-id="cbbd5-128">Yönetilmeyen Kaynakları Temizleme</span><span class="sxs-lookup"><span data-stu-id="cbbd5-128">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="cbbd5-129">using deyimleri (C# başvuru)</span><span class="sxs-lookup"><span data-stu-id="cbbd5-129">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="cbbd5-130">Using deyimleri (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cbbd5-130">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
