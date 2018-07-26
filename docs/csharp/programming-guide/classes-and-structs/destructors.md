---
title: Sonlandırıcılar (C# programlama Kılavuzu)
ms.date: 05/10/2017
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: fc15818883736015419f8599d482185bbab5120a
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960523"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="0303a-102">Sonlandırıcılar (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="0303a-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="0303a-103">Sonlandırıcılar, sınıfların örneklerini yok etmek üzere kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0303a-103">Finalizers are used to destruct instances of classes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0303a-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0303a-104">Remarks</span></span>  
  
-   <span data-ttu-id="0303a-105">Sonlandırıcılar yapılarda tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="0303a-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="0303a-106">Bunlar, yalnızca sınıf ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0303a-106">They are only used with classes.</span></span>  
  
-   <span data-ttu-id="0303a-107">Bir sınıf, bir sonlandırıcı yalnızca olabilir.</span><span class="sxs-lookup"><span data-stu-id="0303a-107">A class can only have one finalizer.</span></span>  
  
-   <span data-ttu-id="0303a-108">Sonlandırıcılar devralınmış veya aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="0303a-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
-   <span data-ttu-id="0303a-109">Sonlandırıcılar çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="0303a-109">Finalizers cannot be called.</span></span> <span data-ttu-id="0303a-110">Bunlar otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0303a-110">They are invoked automatically.</span></span>  
  
-   <span data-ttu-id="0303a-111">Bir sonlandırıcı değiştiriciler alın veya parametreleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0303a-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="0303a-112">Örneğin, bir sonlandırıcı için bildirimi aşağıdaki gibidir `Car` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0303a-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

<span data-ttu-id="0303a-113">Bir Sonlandırıcı, aşağıdaki örnekte gösterildiği gibi bir ifade gövdesi tanımı da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="0303a-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="0303a-114">Sonlandırıcı örtük olarak çağırır <xref:System.Object.Finalize%2A> nesnenin temel sınıfı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="0303a-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="0303a-115">Bu nedenle, bir sonlandırıcı bir çağrı örtük olarak aşağıdaki kodu çevrilir:</span><span class="sxs-lookup"><span data-stu-id="0303a-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 <span data-ttu-id="0303a-116">Diğer bir deyişle `Finalize` yöntemi çağrılır yinelemeli devralma zincirini tüm örnekler için en çok türetilen en az türetilen için.</span><span class="sxs-lookup"><span data-stu-id="0303a-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0303a-117">Boş Sonlandırıcıları kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="0303a-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="0303a-118">Bir sınıf, bir sonlandırıcı içeriyorsa, bir giriş oluşturulan `Finalize` kuyruk.</span><span class="sxs-lookup"><span data-stu-id="0303a-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="0303a-119">Sonlandırıcı çağrıldığında çöp toplayıcı kuyruğu işlemek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="0303a-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="0303a-120">Boş Sonlandırıcı yalnızca gereksiz bir performans kaybı neden olur.</span><span class="sxs-lookup"><span data-stu-id="0303a-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="0303a-121">Bu çöp toplayıcı tarafından belirlenir çünkü Sonlandırıcı çağrıldığında Programcı üzerinde denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0303a-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="0303a-122">Çöp toplayıcı uygulama tarafından artık kullanılmayan nesneleri denetler.</span><span class="sxs-lookup"><span data-stu-id="0303a-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="0303a-123">Bu nesne sonlandırma için uygun olarak değerlendirir, sonlandırıcı (varsa) çağırır ve nesne depolamak için kullanılan belleği geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="0303a-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> <span data-ttu-id="0303a-124">Program çıkış yaptığı andaki sonlandırıcılar da denir.</span><span class="sxs-lookup"><span data-stu-id="0303a-124">Finalizers are also called when the program exits.</span></span>  
  
 <span data-ttu-id="0303a-125">Çağırarak atık toplamayı zorlamak mümkün mü <xref:System.GC.Collect%2A>, ancak performans sorunları oluşturabilir, çünkü çoğu zaman bu kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="0303a-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="0303a-126">Yayın kaynaklara sonlandırıcılar kullanma</span><span class="sxs-lookup"><span data-stu-id="0303a-126">Using Finalizers to Release Resources</span></span>  
 <span data-ttu-id="0303a-127">Genel olarak, C# bir çalışma zamanının atık toplama ile hedeflemiyor bir dil ile geliştirdiğinizde gerektiği kadar bellek yönetimi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="0303a-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="0303a-128">.NET Framework atık toplayıcı, örtük olarak sağlanmasını ve ayrılmasını, nesneler için bellek yönetir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="0303a-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="0303a-129">Ancak, uygulamanızı windows, dosyaları ve ağ bağlantıları gibi yönetilmeyen kaynakları yalıtan, bu kaynakları serbest bırakacak sonlandırıcılar kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0303a-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="0303a-130">Nesne sonlandırma için uygun olduğunda, Atık toplayıcısının çalışacağı `Finalize` nesnesinin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0303a-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="0303a-131">Açık kaynak sürümü</span><span class="sxs-lookup"><span data-stu-id="0303a-131">Explicit Release of Resources</span></span>  
 <span data-ttu-id="0303a-132">Uygulamanızı pahalı bir dış kaynağa kullanıyorsanız, çöp toplayıcı nesneyi serbest bırakan önce kaynak açıkça serbest bırakmak için bir yol sağlamak da öneririz.</span><span class="sxs-lookup"><span data-stu-id="0303a-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="0303a-133">Uygulayarak bunu bir `Dispose` yönteminden <xref:System.IDisposable> nesne için gerekli temizleme gerçekleştirir arabirimi.</span><span class="sxs-lookup"><span data-stu-id="0303a-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="0303a-134">Bu, uygulamanın performansını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="0303a-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="0303a-135">Bile bu açık denetime ile kaynakları, sonlandırıcı durumunda kaynakları temizlemek için bir önlem haline gelir. çağrı `Dispose` yöntemi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="0303a-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="0303a-136">Kaynakları temizleme hakkında daha fazla ayrıntı için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="0303a-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
-   [<span data-ttu-id="0303a-137">Yönetilmeyen Kaynakları Temizleme</span><span class="sxs-lookup"><span data-stu-id="0303a-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
-   [<span data-ttu-id="0303a-138">Dispose Yöntemi Uygulama</span><span class="sxs-lookup"><span data-stu-id="0303a-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [<span data-ttu-id="0303a-139">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="0303a-139">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="0303a-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="0303a-140">Example</span></span>  
 <span data-ttu-id="0303a-141">Aşağıdaki örnek, bir devralma zincirini olun üç sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0303a-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="0303a-142">Sınıf `First` temel sınıf `Second` türetilir `First`, ve `Third` türetilir `Second`.</span><span class="sxs-lookup"><span data-stu-id="0303a-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="0303a-143">Üç sonlandırıcılar vardır.</span><span class="sxs-lookup"><span data-stu-id="0303a-143">All three have finalizers.</span></span> <span data-ttu-id="0303a-144">İçinde `Main`, en çok türetilen sınıfın bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0303a-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="0303a-145">Program çalıştığında sonlandırıcılar üç sınıfları için otomatik olarak ve sırasıyla en çok türetilen en az türetilen için gelen çağrılır, dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="0303a-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0303a-146">C# Dil Belirtimi</span><span class="sxs-lookup"><span data-stu-id="0303a-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0303a-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0303a-147">See Also</span></span>  
 <xref:System.IDisposable>  
 [<span data-ttu-id="0303a-148">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="0303a-148">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0303a-149">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="0303a-149">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="0303a-150">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="0303a-150">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
