---
title: IDisposable uygulayan nesneler kullanma
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: fd78c2f99ca5c8ffe3c753e158ceba3e0c458c5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="96090-102">IDisposable uygulayan nesneler kullanma</span><span class="sxs-lookup"><span data-stu-id="96090-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="96090-103">Ortak dil çalışma zamanı 's atık toplayıcı yönetilen nesneler tarafından kullanılan bellek kaldırsa ancak yönetilmeyen kaynakları kullanmak türleri uygulayan <xref:System.IDisposable> geri kazanılacak bu yönetilmeyen kaynaklar için ayrılan bellek izin vermek için arabirim.</span><span class="sxs-lookup"><span data-stu-id="96090-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the memory allocated to these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="96090-104">Arabirimini uygulayan bir nesneye kullanarak tamamladığınızda <xref:System.IDisposable>, nesnenin çağırmalıdır <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="96090-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="96090-105">Bunu iki yoldan biriyle yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="96090-105">You can do this in one of two ways:</span></span>  
  
* <span data-ttu-id="96090-106">C# ile `using` deyimi veya Visual Basic `Using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="96090-106">With the C# `using` statement or the Visual Basic `Using` statement.</span></span>  
  
* <span data-ttu-id="96090-107">Uygulama tarafından bir `try/finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="96090-107">By implementing a `try/finally` block.</span></span>  

## <a name="the-using-statement"></a><span data-ttu-id="96090-108">Using deyimi</span><span class="sxs-lookup"><span data-stu-id="96090-108">The using statement</span></span>

<span data-ttu-id="96090-109">`using` Deyimi C# ve `Using` Visual Basic'de deyimini oluşturun ve nesneyi temizlemek amacıyla yazmalısınız kod basitleştirin.</span><span class="sxs-lookup"><span data-stu-id="96090-109">The `using` statement in C# and the `Using` statement in Visual Basic simplify the code that you must write to create and clean up an object.</span></span> <span data-ttu-id="96090-110">`using` Deyimi bir veya daha fazla kaynak alır, belirtin ve otomatik olarak nesnesinin siler deyimleri yürütür.</span><span class="sxs-lookup"><span data-stu-id="96090-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="96090-111">Ancak, `using` deyimi, bunlar oluşturulan yöntemi kapsamında kullanılan nesneler için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="96090-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>  
  
<span data-ttu-id="96090-112">Aşağıdaki örnek kullanır `using` oluşturmak ve yayın için deyimi bir <xref:System.IO.StreamReader?displayProperty=nameWithType> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="96090-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>  
  
[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]  
  
<span data-ttu-id="96090-113">Ancak unutmayın <xref:System.IO.StreamReader> uygulayan sınıf <xref:System.IDisposable> gösteren bir yönetilmeyen kaynak kullanır, örneğin açıkça çağırın değil arabirimi <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="96090-113">Note that although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="96090-114">C# veya Visual Basic derleyici karşılaştığında `using` deyimi, açıkça içeren aşağıdaki kodu eşdeğerdir Ara dile (IL) yayar bir `try/finally` bloğu.</span><span class="sxs-lookup"><span data-stu-id="96090-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>  
  
[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]  
  
<span data-ttu-id="96090-115">C# `using` deyimi de sağlar, iç içe geçmiş dahili olarak eşdeğer olan tek bir deyimde birden çok kaynaklarında edinmeye `using` deyimleri.</span><span class="sxs-lookup"><span data-stu-id="96090-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="96090-116">Aşağıdaki örnekte iki başlatır <xref:System.IO.StreamReader> nesneleri iki farklı dosyaların içeriğini okumak için.</span><span class="sxs-lookup"><span data-stu-id="96090-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>  
  
[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="96090-117">Try/finally bloğu</span><span class="sxs-lookup"><span data-stu-id="96090-117">Try/finally block</span></span>

<span data-ttu-id="96090-118">Kaydırma yerine bir `try/finally` engelleyin bir `using` deyimi, aktarmızı uygulamak `try/finally` doğrudan engelleyin.</span><span class="sxs-lookup"><span data-stu-id="96090-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="96090-119">Bu sizin kişisel kodlama stiliniz olabilir veya bunu aşağıdaki nedenlerden biri dolayısıyla yapmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="96090-119">This may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>  
  
* <span data-ttu-id="96090-120">Eklenecek bir `catch` oluşturulan tüm özel durumları işlemek için blok `try` bloğu.</span><span class="sxs-lookup"><span data-stu-id="96090-120">To include a `catch` block to handle any exceptions thrown in the `try` block.</span></span> <span data-ttu-id="96090-121">Aksi takdirde, tarafından oluşturulan özel durumlar `using` içinde oluşturulan tüm özel durumları olarak deyimi işlenmemiş, `using` bloke bir `try/catch` blok mevcut değil.</span><span class="sxs-lookup"><span data-stu-id="96090-121">Otherwise, any exceptions thrown by the `using` statement are unhandled, as are any exceptions thrown within the `using` block if a `try/catch` block isn't present.</span></span>  
  
* <span data-ttu-id="96090-122">Uygulayan bir nesne örneği oluşturmak için <xref:System.IDisposable> , kapsam içinde beyan blok yerel değil.</span><span class="sxs-lookup"><span data-stu-id="96090-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>  
  
<span data-ttu-id="96090-123">Kullandığı aşağıdaki örnek önceki örneğe benzerdir bir `try/catch/finally` örneği, kullanın ve elden blok bir <xref:System.IO.StreamReader> nesnesi ve tarafından oluşturulan tüm özel durumları işlemek için <xref:System.IO.StreamReader> oluşturucusu ve kendi <xref:System.IO.StreamReader.ReadToEnd%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="96090-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="96090-124">Unutmayın kodda `finally` blok denetler nesne uygulayan <xref:System.IDisposable> değil `null` çağırmadan önce <xref:System.IDisposable.Dispose%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="96090-124">Note that the code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="96090-125">Bunu yapmak için hata sonuçlanabilir bir <xref:System.NullReferenceException> çalışma zamanında özel durum.</span><span class="sxs-lookup"><span data-stu-id="96090-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>  
  
[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]  
  
<span data-ttu-id="96090-126">Uygulanacak seçerseniz veya uygulamalıdır temel bu deseni takip edebilirsiniz bir `try/finally` programlama dilinizi desteklemediğinden bloğunu bir `using` deyimi doğrudan çağrıları izin vermez ancak <xref:System.IDisposable.Dispose%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="96090-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="96090-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96090-127">See also</span></span>

<span data-ttu-id="96090-128">[Yönetilmeyen kaynakları temizleme](../../../docs/standard/garbage-collection/unmanaged.md) </span><span class="sxs-lookup"><span data-stu-id="96090-128">[Cleaning Up Unmanaged Resources](../../../docs/standard/garbage-collection/unmanaged.md) </span></span>  
<span data-ttu-id="96090-129">[using deyimi (C# Başvurusu)](~/docs/csharp/language-reference/keywords/using-statement.md) </span><span class="sxs-lookup"><span data-stu-id="96090-129">[using Statement (C# Reference)](~/docs/csharp/language-reference/keywords/using-statement.md) </span></span>  
[<span data-ttu-id="96090-130">Using deyimi (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96090-130">Using Statement (Visual Basic)</span></span>](~/docs/visual-basic/language-reference/statements/using-statement.md)
