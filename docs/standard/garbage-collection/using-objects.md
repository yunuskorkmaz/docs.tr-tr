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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160292"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="2f57b-102">IDisposable uygulayan nesneleri kullanma</span><span class="sxs-lookup"><span data-stu-id="2f57b-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="2f57b-103">Ortak dil runtime'ın çöp toplayıcısı yönetilen nesneler tarafından kullanılan belleği geri alır, ancak yönetilmeyen kaynakları kullanan türler, bu yönetilmeyen kaynaklara ayrılan belleğin geri alınmasına izin vermek için <xref:System.IDisposable> arabirimi uygular.</span><span class="sxs-lookup"><span data-stu-id="2f57b-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="2f57b-104">Uygulayan bir nesneyi kullanmayı <xref:System.IDisposable>bitirdiğinizde, nesnenin <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulamasını aramalısınız.</span><span class="sxs-lookup"><span data-stu-id="2f57b-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="2f57b-105">Bunu iki yoldan biriyle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2f57b-105">You can do this in one of two ways:</span></span>  
  
- <span data-ttu-id="2f57b-106">C# `using` deyimi veya Visual `Using` Basic deyimi ile.</span><span class="sxs-lookup"><span data-stu-id="2f57b-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
- <span data-ttu-id="2f57b-107">Bir `try/finally` blok uygulayarak.</span><span class="sxs-lookup"><span data-stu-id="2f57b-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="2f57b-108">Using deyimi</span><span class="sxs-lookup"><span data-stu-id="2f57b-108">The using statement</span></span>

<span data-ttu-id="2f57b-109">C# `using` ifadesi ve `Using` Visual Basic'teki deyim, bir nesne oluşturmak ve temizlemek için yazmanız gereken kodu basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="2f57b-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="2f57b-110">İfade `using` bir veya daha fazla kaynak elde eder, belirttiğiniz ifadeleri yürütür ve nesneyi otomatik olarak ortadan yıkar.</span><span class="sxs-lookup"><span data-stu-id="2f57b-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="2f57b-111">Ancak, `using` deyim yalnızca oluşturuldukları yöntem kapsamında kullanılan nesneler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="2f57b-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="2f57b-112">Aşağıdaki örnek, `using` bir <xref:System.IO.StreamReader?displayProperty=nameWithType> nesne oluşturmak ve serbest bırakmak için deyimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="2f57b-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="2f57b-113"><xref:System.IO.StreamReader> Sınıf, yönetilmeyen bir <xref:System.IDisposable> kaynak kullandığını gösteren arabirimi uygulasa da, örnek yöntemi açıkça <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> çağırmaz.</span><span class="sxs-lookup"><span data-stu-id="2f57b-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2f57b-114">C# veya Visual Basic derleyicisi ifadeyle `using` karşılaştığında, açıkça bir `try/finally` blok içeren aşağıdaki koda eşdeğer ara dil (IL) yayır.</span><span class="sxs-lookup"><span data-stu-id="2f57b-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="2f57b-115">C# `using` deyimi, iç içe kullanılan `using` ifadelere eşdeğer olan tek bir deyimde birden çok kaynak elde etmenizi de sağlar.</span><span class="sxs-lookup"><span data-stu-id="2f57b-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="2f57b-116">Aşağıdaki örnek, iki farklı <xref:System.IO.StreamReader> dosyanın içeriğini okumak için iki nesneyi anında okur.</span><span class="sxs-lookup"><span data-stu-id="2f57b-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="2f57b-117">Try/finally bloğu</span><span class="sxs-lookup"><span data-stu-id="2f57b-117">Try/finally block</span></span>

<span data-ttu-id="2f57b-118">Bir `try/finally` `using` bloğu bir deyimde sarmalamak yerine, `try/finally` bloğu doğrudan uygulamayı seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f57b-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="2f57b-119">Bu sizin kişisel kodlama stiliniz olabilir veya bunu aşağıdaki nedenlerden biri dolayısıyla yapmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2f57b-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
- <span data-ttu-id="2f57b-120">Blokta `catch` atılan özel durumları işlemek için `try` bir blok eklemek için.</span><span class="sxs-lookup"><span data-stu-id="2f57b-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="2f57b-121">Aksi takdirde, `using` bir `using` `try/catch` blok yoksa blok içinde atılan tüm özel durumlar gibi ekstre tarafından atılan tüm özel durumlar işlenmez.</span><span class="sxs-lookup"><span data-stu-id="2f57b-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
- <span data-ttu-id="2f57b-122">Kapsamı yerel olmayan bir nesneyi, <xref:System.IDisposable> içinde beyan edildiği blok için anında uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="2f57b-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="2f57b-123">Aşağıdaki `try/catch/finally` örnek, bir <xref:System.IO.StreamReader> nesneyi anlık olarak kullanmak, kullanmak ve elden çıkarmak ve <xref:System.IO.StreamReader> oluşturucu ve <xref:System.IO.StreamReader.ReadToEnd%2A> yöntemi tarafından atılan özel durumları işlemek için bir blok kullanması dışında önceki örneğe benzer.</span><span class="sxs-lookup"><span data-stu-id="2f57b-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="2f57b-124">Bloktaki kodun, `finally` uygulayan <xref:System.IDisposable> nesnenin `null` <xref:System.IDisposable.Dispose%2A> yöntemi aramadan önce olmadığını denetlediğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="2f57b-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="2f57b-125">Bunun yapılmaması, çalışma <xref:System.NullReferenceException> zamanında bir özel durumla sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="2f57b-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="2f57b-126">Programlama diliniz bir `try/finally` `using` deyimi desteklemediği, ancak <xref:System.IDisposable.Dispose%2A> yönteme doğrudan çağrılara izin verdiği için, bir engelleme uygulamayı veya uygulamanız gerekiyorsa bu temel deseni izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2f57b-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2f57b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2f57b-127">See also</span></span>

- [<span data-ttu-id="2f57b-128">Yönetilmeyen Kaynakları Temizleme</span><span class="sxs-lookup"><span data-stu-id="2f57b-128">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="2f57b-129">using Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="2f57b-129">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="2f57b-130">Using Deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2f57b-130">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
