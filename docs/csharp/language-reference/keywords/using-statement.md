---
title: using Deyimi (C# Başvurusu)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fdf37e1bfc57bf850b332f167e57d3e05d23e78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="f9dcd-102">using Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f9dcd-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="f9dcd-103">Doğru kullanımı sağlar kullanışlı bir sözdizimi sağlar <xref:System.IDisposable> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9dcd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f9dcd-104">Example</span></span>  
 <span data-ttu-id="f9dcd-105">Aşağıdaki örnek kullanarak kullanmayı gösterir deyimi.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-105">The following example shows how to use the using statement.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="f9dcd-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f9dcd-106">Remarks</span></span>  
 <span data-ttu-id="f9dcd-107"><xref:System.IO.File>ve <xref:System.Drawing.Font> yönetilmeyen kaynaklara (Bu örnek dosya tanıtıcıları ve cihaz bağlamları) erişim yönetilen türlerine örnek olarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="f9dcd-108">Yönetilmeyen kaynakları ve bunları saklayan sınıf kitaplığı türleri pek çok değişik vardır.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="f9dcd-109">Tüm türleri uygulamalıdır <xref:System.IDisposable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
<span data-ttu-id="f9dcd-110">Zaman ömrü bir `IDisposable` nesnesidir tek bir yöntem sınırlı, bildirme ve içinde örneği bir `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in a `using` statement.</span></span> <span data-ttu-id="f9dcd-111">`using` Deyimi çağrıları <xref:System.IDisposable.Dispose%2A> doğru bir şekilde ve (daha önce gösterildiği gibi kullandığınız zaman) nesnesi üzerinde yöntemi de neden nesnenin kendisini kapsamının dışına gitmek için hemen <xref:System.IDisposable.Dispose%2A> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="f9dcd-112">İçinde `using` bloğu, nesneyi salt okunur ve yeniden atandığında veya değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="f9dcd-113">`using` Deyimi sağlar <xref:System.IDisposable.Dispose%2A> dahi nesnede yöntemleri çağırma bir özel durum oluşursa çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs while you are calling methods on the object.</span></span> <span data-ttu-id="f9dcd-114">Try bloğunun bir nesne koyma ve ardından çağırma aynı sonucu elde edebilirsiniz <xref:System.IDisposable.Dispose%2A> içinde bir finally bloğunda; aslında, bu nasıl `using` deyimi derleyici tarafından çevrilir.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-114">You can achieve the same result by putting the object inside a try block and then calling <xref:System.IDisposable.Dispose%2A> in a finally block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="f9dcd-115">Kod örneği, aşağıdaki kodu önceden derleme zamanında genişletir. (nesne için sınırlı kapsamı oluşturmak için ek süslü ayraçlar unutmayın):</span><span class="sxs-lookup"><span data-stu-id="f9dcd-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 <span data-ttu-id="f9dcd-116">Bir türde birden çok örneği içinde bildirilen bir `using` aşağıdaki örnekte gösterildiği gibi deyimi.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-116">Multiple instances of a type can be declared in a `using` statement, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 <span data-ttu-id="f9dcd-117">Kaynak nesne örneği ve daha sonra değişkeni geçirin `using` deyimi değildir, ancak bu en iyi yöntem.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-117">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="f9dcd-118">Bu durumda, nesne denetimi terk sonra kapsam içinde kalır `using` rağmen büyük olasılıkla artık yönetilmeyen kaynaklarına erişebilir engelleyin.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-118">In this case, the object remains in scope after control leaves the `using` block even though it will probably no longer have access to its unmanaged resources.</span></span> <span data-ttu-id="f9dcd-119">Diğer bir deyişle, onu artık tam olarak başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-119">In other words, it will no longer be fully initialized.</span></span> <span data-ttu-id="f9dcd-120">Nesne dışında kullanmayı denerseniz `using` engellemek, bir özel durum oluşturulmasına neden risk.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-120">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="f9dcd-121">Bu nedenle, nesne örneğini oluşturmak genellikle daha iyi `using` deyimi ve bunun kapsamına sınırlamak `using` bloğu.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-121">For this reason, it is generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
<span data-ttu-id="f9dcd-122">Atma hakkında daha fazla bilgi için `IDisposable` nesneleri bkz [IDisposable uygulayan nesneler kullanma](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f9dcd-122">For more information on disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f9dcd-123">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f9dcd-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f9dcd-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f9dcd-124">See Also</span></span>  
 [<span data-ttu-id="f9dcd-125">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f9dcd-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f9dcd-126">C# programlama kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f9dcd-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f9dcd-127">C# anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f9dcd-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f9dcd-128">using yönergesi</span><span class="sxs-lookup"><span data-stu-id="f9dcd-128">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="f9dcd-129">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="f9dcd-129">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
 [<span data-ttu-id="f9dcd-130">IDisposable uygulayan nesneler kullanma</span><span class="sxs-lookup"><span data-stu-id="f9dcd-130">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)  
 [<span data-ttu-id="f9dcd-131">IDisposable arabirimi</span><span class="sxs-lookup"><span data-stu-id="f9dcd-131">IDisposable interface</span></span>](xref:System.IDisposable)
