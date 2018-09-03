---
title: using Deyimi (C# Başvurusu)
ms.date: 07/20/2015
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: ec4849dda0f28ad1f0e0ebb2c493a33005107db4
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43480713"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="f54e1-102">using Deyimi (C# Başvurusu)</span><span class="sxs-lookup"><span data-stu-id="f54e1-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="f54e1-103">Doğru kullanımını güvence altına kullanışlı bir söz dizimi sağlar <xref:System.IDisposable> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="f54e1-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f54e1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f54e1-104">Example</span></span>  
 <span data-ttu-id="f54e1-105">Aşağıdaki örnek nasıl kullanılacağını gösterir `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f54e1-105">The following example shows how to use the `using` statement.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="f54e1-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f54e1-106">Remarks</span></span>  
 <span data-ttu-id="f54e1-107"><xref:System.IO.File> ve <xref:System.Drawing.Font> (içinde bu durum dosya tanıtıcıları ve cihaz bağlamları) yönetilmeyen kaynaklara erişen Yönetilen türlerin örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="f54e1-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="f54e1-108">Yönetilmeyen kaynakları bunları kapsayan sınıf kitaplığı türleri ve diğer birçok tür vardır.</span><span class="sxs-lookup"><span data-stu-id="f54e1-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="f54e1-109">Tüm türleri uygulamalıdır <xref:System.IDisposable> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="f54e1-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
<span data-ttu-id="f54e1-110">Zaman ömrünü bir `IDisposable` nesne tek bir yöntem sınırlıdır, bildirme ve içinde örneği `using` deyimi.</span><span class="sxs-lookup"><span data-stu-id="f54e1-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="f54e1-111">`using` Deyim aramaları <xref:System.IDisposable.Dispose%2A> doğru bir şekilde ve (daha önce gösterildiği gibi kullandığınız zaman) nesnesi üzerinde yöntemi de neden nesne kapsam dışına çıkmadan kendisine hemen sonra <xref:System.IDisposable.Dispose%2A> çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f54e1-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="f54e1-112">İçinde `using` blok, nesne, salt okunur ve yeniden atandığında veya değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="f54e1-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="f54e1-113">`using` Bildirimi sağlar <xref:System.IDisposable.Dispose%2A> bile içinde özel bir durum oluştuğunda çağrılır `using` blok.</span><span class="sxs-lookup"><span data-stu-id="f54e1-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="f54e1-114">Nesnenin içine koyarak aynı sonucu elde edebileceğiniz bir `try` blok ve ardından arama <xref:System.IDisposable.Dispose%2A> içinde bir `finally` engelle; aslında bu, nasıl `using` deyimi, derleyici tarafından çevrilir.</span><span class="sxs-lookup"><span data-stu-id="f54e1-114">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="f54e1-115">Kod örneği, daha önce aşağıdaki kodu derleme zamanında genişletir (nesne için sınırlı kapsamı oluşturmak için ek küme ayracı unutmayın):</span><span class="sxs-lookup"><span data-stu-id="f54e1-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
 
 <span data-ttu-id="f54e1-116">Hakkında daha fazla bilgi için `try` - `finally` deyimi bkz [try-finally](try-finally.md) konu.</span><span class="sxs-lookup"><span data-stu-id="f54e1-116">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>
  
 <span data-ttu-id="f54e1-117">Birden fazla örneğini bir tür içinde bildirilebilir `using` aşağıdaki örnekte gösterildiği gibi deyimi:</span><span class="sxs-lookup"><span data-stu-id="f54e1-117">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 <span data-ttu-id="f54e1-118">Kaynak nesne örneği oluşturun ve ardından değişkenine geçirin `using` deyimi değildir, ancak bu en iyi uygulama.</span><span class="sxs-lookup"><span data-stu-id="f54e1-118">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="f54e1-119">Bu durumda, sonra Denetim leaves `using` engellemek, kapsam içinde nesne kalır ancak büyük olasılıkla kendi yönetilmeyen kaynaklara erişim yok.</span><span class="sxs-lookup"><span data-stu-id="f54e1-119">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="f54e1-120">Diğer bir deyişle, tam olarak artık başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f54e1-120">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="f54e1-121">Nesne dışında kullanmayı denerseniz `using` bir özel durum oluşturulmasına neden risk engelleyin.</span><span class="sxs-lookup"><span data-stu-id="f54e1-121">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="f54e1-122">Bu nedenle, nesneyi oluşturmak genellikle daha iyi `using` deyimi ve sınırlandırmak için kapsamı `using` blok.</span><span class="sxs-lookup"><span data-stu-id="f54e1-122">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
<span data-ttu-id="f54e1-123">Atma hakkında daha fazla bilgi için `IDisposable` nesneleri bkz [IDisposable uygulayan nesneler kullanma](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="f54e1-123">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f54e1-124">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="f54e1-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f54e1-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f54e1-125">See Also</span></span>

- [<span data-ttu-id="f54e1-126">C# başvurusu</span><span class="sxs-lookup"><span data-stu-id="f54e1-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="f54e1-127">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f54e1-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f54e1-128">C# Anahtar Sözcükleri</span><span class="sxs-lookup"><span data-stu-id="f54e1-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="f54e1-129">using Yönergesi</span><span class="sxs-lookup"><span data-stu-id="f54e1-129">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
- [<span data-ttu-id="f54e1-130">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="f54e1-130">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
- [<span data-ttu-id="f54e1-131">IDisposable uygulayan nesneler kullanma</span><span class="sxs-lookup"><span data-stu-id="f54e1-131">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)  
- [<span data-ttu-id="f54e1-132">IDisposable arabirimi</span><span class="sxs-lookup"><span data-stu-id="f54e1-132">IDisposable interface</span></span>](xref:System.IDisposable)
