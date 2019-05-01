---
title: IDisposable uygulayan nesneler kullanma
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 25c5ffa89e6ce4e589b8f12a7b8518272426c9e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969500"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="491d6-102">IDisposable uygulayan nesneler kullanma</span><span class="sxs-lookup"><span data-stu-id="491d6-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="491d6-103">Ortak dil çalışma zamanının atık toplayıcı yönetilen nesneler tarafından kullanılan belleği geri kazanır, ancak yönetilmeyen kaynakları kullanan türler <xref:System.IDisposable> kazanılacak bu yönetilmeyen kaynakların tahsis edilen bellek izin vermek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="491d6-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="491d6-104">Bitirdiğinizde uygulayan bir nesne kullanarak <xref:System.IDisposable>, nesnenin çağırmalıdır <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="491d6-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="491d6-105">Bunu iki yoldan biriyle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="491d6-105">You can do this in one of two ways:</span></span>  
  
* <span data-ttu-id="491d6-106">C# ile `using` deyimi veya Visual Basic `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="491d6-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
* <span data-ttu-id="491d6-107">Uygulayarak bir `try/finally` blok.</span><span class="sxs-lookup"><span data-stu-id="491d6-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="491d6-108">Using deyimi</span><span class="sxs-lookup"><span data-stu-id="491d6-108">The using statement</span></span>

<span data-ttu-id="491d6-109">`using` C# deyimi ve `Using` Visual Basic'de deyimini oluşturmak ve bir nesneyi temizlemek için yazmanız gereken kodu basitleştirin.</span><span class="sxs-lookup"><span data-stu-id="491d6-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="491d6-110">`using` Deyimi bir veya daha fazla kaynağı alır, belirtin ve nesnenin otomatik olarak atar deyimleri yürütür.</span><span class="sxs-lookup"><span data-stu-id="491d6-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="491d6-111">Ancak, `using` deyimi, bunlar oluşturulan yöntem kapsamında kullanılan nesneler için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="491d6-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="491d6-112">Aşağıdaki örnekte `using` oluşturmak ve serbest bırakmak için deyimi bir <xref:System.IO.StreamReader?displayProperty=nameWithType> nesne.</span><span class="sxs-lookup"><span data-stu-id="491d6-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="491d6-113">Ancak dikkat <xref:System.IO.StreamReader> sınıfının Implements <xref:System.IDisposable> gösteren yönetilmeyen bir kaynağı kullanır, örneğin açıkça çağırmak değil arabirimi <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="491d6-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="491d6-114">C# veya Visual Basic derleyici karşılaştığında `using` deyimi, açıkça içeren aşağıdaki koda denk olan ara dil (IL) yayar bir `try/finally` blok.</span><span class="sxs-lookup"><span data-stu-id="491d6-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="491d6-115">C# `using` deyimi de sayesinde iç içe geçmiş dahili olarak denk olan tek bir deyimde birden çok kaynak elde `using` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="491d6-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="491d6-116">Aşağıdaki örnek iki başlatır <xref:System.IO.StreamReader> nesneleri iki farklı dosyanın içeriğini okumak için.</span><span class="sxs-lookup"><span data-stu-id="491d6-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="491d6-117">Try/finally bloğu</span><span class="sxs-lookup"><span data-stu-id="491d6-117">Try/finally block</span></span>

<span data-ttu-id="491d6-118">Kaydırmak yerine bir `try/finally` engelleyin bir `using` deyimi, seçebilirsiniz `try/finally` doğrudan engelleyin.</span><span class="sxs-lookup"><span data-stu-id="491d6-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="491d6-119">Bu sizin kişisel kodlama stiliniz olabilir veya bunu aşağıdaki nedenlerden biri dolayısıyla yapmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="491d6-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
* <span data-ttu-id="491d6-120">Eklenecek bir `catch` oluşturulan özel durumları işlemek için blok `try` blok.</span><span class="sxs-lookup"><span data-stu-id="491d6-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="491d6-121">Aksi takdirde, tarafından oluşturulan özel durumlar `using` içinde oluşturulan özel durumlar olarak deyimi işlenmemiş, `using` bloke bir `try/catch` blok mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="491d6-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
* <span data-ttu-id="491d6-122">Uygulayan bir nesne örneği <xref:System.IDisposable> kapsamı içinde beyan blokta yerel değil.</span><span class="sxs-lookup"><span data-stu-id="491d6-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="491d6-123">Bunu kullanması hariç, aşağıdaki örnek önceki örneğe benzer bir `try/catch/finally` elden oluşturmak ve kullanmak için blok bir <xref:System.IO.StreamReader> nesnesi ve tarafından oluşturulan özel durumları işlemek için <xref:System.IO.StreamReader> oluşturucusu ve <xref:System.IO.StreamReader.ReadToEnd%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="491d6-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="491d6-124">Unutmayın kodda `finally` blok denetler uygulayan nesnenin <xref:System.IDisposable> değil `null` çağırmadan önce <xref:System.IDisposable.Dispose%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="491d6-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="491d6-125">Bunun yapılmaması sonuçlanabilir bir <xref:System.NullReferenceException> çalışma zamanında özel durum.</span><span class="sxs-lookup"><span data-stu-id="491d6-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="491d6-126">Uygulamak seçin ya da uygulamalıdır bu temel modeli izleyebilirsiniz bir `try/finally` block programlama diliniz desteklemediğinden bir `using` deyimi doğrudan çağrıları izin vermez ancak <xref:System.IDisposable.Dispose%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="491d6-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="491d6-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="491d6-127">See also</span></span>

- [<span data-ttu-id="491d6-128">Yönetilmeyen Kaynakları Temizleme</span><span class="sxs-lookup"><span data-stu-id="491d6-128">Cleaning Up Unmanaged Resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
- [<span data-ttu-id="491d6-129">using deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="491d6-129">using Statement (C# Reference)</span></span>](~/docs/csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="491d6-130">Using deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="491d6-130">Using Statement (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/statements/using-statement.md)
