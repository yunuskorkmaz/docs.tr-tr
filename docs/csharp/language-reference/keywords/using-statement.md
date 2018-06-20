---
title: using Deyimi (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 7bf9138721ecee63c65c2e39922aee96b1dfaa41
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208410"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="7bc29-102">using Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="7bc29-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="7bc29-103">Doğru kullanımı sağlar kullanışlı bir sözdizimi sağlar <xref:System.IDisposable> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="7bc29-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bc29-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7bc29-104">Example</span></span>  
 <span data-ttu-id="7bc29-105">Aşağıdaki örnekte nasıl kullanılacağını gösterir `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7bc29-105">The following example shows how to use the `using` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="7bc29-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bc29-106">Remarks</span></span>  
 <span data-ttu-id="7bc29-107"><xref:System.IO.File> ve <xref:System.Drawing.Font> yönetilmeyen kaynaklara (Bu örnek dosya tanıtıcıları ve cihaz bağlamları) erişim yönetilen türlerine örnek olarak verilebilir.</span><span class="sxs-lookup"><span data-stu-id="7bc29-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="7bc29-108">Yönetilmeyen kaynakları ve bunları saklayan sınıf kitaplığı türleri pek çok değişik vardır.</span><span class="sxs-lookup"><span data-stu-id="7bc29-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="7bc29-109">Tüm türleri uygulamalıdır <xref:System.IDisposable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="7bc29-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
<span data-ttu-id="7bc29-110">Zaman ömrü bir `IDisposable` nesnesidir tek bir yöntem sınırlı, bildirme ve içinde örneği `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="7bc29-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="7bc29-111">`using` Deyimi çağrıları <xref:System.IDisposable.Dispose%2A> doğru bir şekilde ve (daha önce gösterildiği gibi kullandığınız zaman) nesnesi üzerinde yöntemi de neden nesnenin kendisini kapsamının dışına gitmek için hemen <xref:System.IDisposable.Dispose%2A> olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="7bc29-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="7bc29-112">İçinde `using` bloğu, nesneyi salt okunur ve yeniden atandığında veya değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="7bc29-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="7bc29-113">`using` Deyimi sağlar <xref:System.IDisposable.Dispose%2A> içinde bir özel durum oluştuğunda dahi adlı `using` bloğu.</span><span class="sxs-lookup"><span data-stu-id="7bc29-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="7bc29-114">Nesne içinde koyarak aynı sonucu elde edebilirsiniz bir `try` bloğu ve ardından çağırma <xref:System.IDisposable.Dispose%2A> içinde bir `finally` engelle; aslında, bu nasıl `using` deyimi derleyici tarafından çevrilir.</span><span class="sxs-lookup"><span data-stu-id="7bc29-114">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="7bc29-115">Kod örneği, aşağıdaki kodu önceden derleme zamanında genişletir. (nesne için sınırlı kapsamı oluşturmak için ek süslü ayraçlar unutmayın):</span><span class="sxs-lookup"><span data-stu-id="7bc29-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
 
 <span data-ttu-id="7bc29-116">Hakkında daha fazla bilgi için `try` - `finally` deyimi, bkz: [try-finally](try-finally.md) konu.</span><span class="sxs-lookup"><span data-stu-id="7bc29-116">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>
  
 <span data-ttu-id="7bc29-117">İçinde bir türü birden çok örneğini bildirilebilir `using` deyimi, aşağıdaki örnekte gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="7bc29-117">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 <span data-ttu-id="7bc29-118">Kaynak nesne örneği ve daha sonra değişkeni geçirin `using` deyimi değildir, ancak bu en iyi yöntem.</span><span class="sxs-lookup"><span data-stu-id="7bc29-118">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="7bc29-119">Bu durumda, Denetim bırakır sonra `using` engellemek, kapsamdaki nesne kalır ancak büyük olasılıkla yönetilmeyen kaynaklarına erişim yok.</span><span class="sxs-lookup"><span data-stu-id="7bc29-119">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="7bc29-120">Diğer bir deyişle, onu tam olarak artık başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="7bc29-120">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="7bc29-121">Nesne dışında kullanmayı denerseniz `using` engellemek, bir özel durum oluşturulmasına neden risk.</span><span class="sxs-lookup"><span data-stu-id="7bc29-121">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="7bc29-122">Bu nedenle, nesne örneğini oluşturmak genellikle daha iyi `using` deyimi ve bunun kapsamına sınırlamak `using` bloğu.</span><span class="sxs-lookup"><span data-stu-id="7bc29-122">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
<span data-ttu-id="7bc29-123">Atma hakkında daha fazla bilgi için `IDisposable` nesneleri bkz [IDisposable uygulayan nesneler kullanma](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="7bc29-123">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7bc29-124">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="7bc29-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7bc29-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7bc29-125">See Also</span></span>  
 [<span data-ttu-id="7bc29-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="7bc29-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7bc29-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="7bc29-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7bc29-128">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="7bc29-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="7bc29-129">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="7bc29-129">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="7bc29-130">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="7bc29-130">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
 [<span data-ttu-id="7bc29-131">IDisposable uygulayan nesneler kullanma</span><span class="sxs-lookup"><span data-stu-id="7bc29-131">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)  
 [<span data-ttu-id="7bc29-132">IDisposable arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bc29-132">IDisposable interface</span></span>](xref:System.IDisposable)
