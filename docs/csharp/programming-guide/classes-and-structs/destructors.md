---
title: Sonlandırıcılar-C# Programlama Kılavuzu
description: Yok ediciler olarak da adlandırılan C# içindeki sonlandırıcılar, bir sınıf örneği çöp toplayıcı tarafından toplandığında gerekli son temizleme işlemini gerçekleştirir.
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 392b69633e596f0682fdfb4a5875f46755203ff7
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474897"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="42157-103">Sonlandırıcılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="42157-103">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="42157-104">Sonlandırıcılar (yani **Yıkıcılar**olarak da bilinir), bir sınıf örneği çöp toplayıcısı tarafından toplandığında gerekli son temizleme işlemini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42157-104">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42157-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="42157-105">Remarks</span></span>  
  
- <span data-ttu-id="42157-106">Sonlandırıcılar yapılar içinde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="42157-106">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="42157-107">Bunlar yalnızca sınıflarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="42157-107">They are only used with classes.</span></span>  
  
- <span data-ttu-id="42157-108">Bir sınıfın yalnızca bir sonlandırıcısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="42157-108">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="42157-109">Sonlandırıcılar devralınamaz veya aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="42157-109">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="42157-110">Sonlandırıcılar çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="42157-110">Finalizers cannot be called.</span></span> <span data-ttu-id="42157-111">Bunlar otomatik olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="42157-111">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="42157-112">Sonlandırıcı değiştirici almaz veya parametrelere sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="42157-112">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="42157-113">Örneğin, aşağıdaki, sınıfı için sonlandırıcının bir bildirimidir `Car` .</span><span class="sxs-lookup"><span data-stu-id="42157-113">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="42157-114">Bir Sonlandırıcı, aşağıdaki örnekte gösterildiği gibi bir ifade gövdesi tanımı olarak da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="42157-114">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="42157-115">Sonlandırıcı nesnenin temel sınıfında örtülü olarak çağrı çağırır <xref:System.Object.Finalize%2A> .</span><span class="sxs-lookup"><span data-stu-id="42157-115">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="42157-116">Bu nedenle, sonlandırıcının çağrısı dolaylı olarak aşağıdaki koda çevrilir:</span><span class="sxs-lookup"><span data-stu-id="42157-116">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="42157-117">Bu tasarım, bir `Finalize` metodun devralma zincirindeki tüm örnekler için yinelemeli olarak çağrıldığı, en az türetilen ' ın en az türetiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="42157-117">This design means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="42157-118">Boş sonlandırıcılar kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="42157-118">Empty finalizers should not be used.</span></span> <span data-ttu-id="42157-119">Bir sınıf bir Sonlandırıcı içerdiğinde, kuyrukta bir giriş oluşturulur `Finalize` .</span><span class="sxs-lookup"><span data-stu-id="42157-119">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="42157-120">Sonlandırıcı çağrıldığında, atık toplayıcı kuyruğu işleyecek şekilde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="42157-120">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="42157-121">Boş bir Sonlandırıcı yalnızca gereksiz performans kaybına neden olur.</span><span class="sxs-lookup"><span data-stu-id="42157-121">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="42157-122">Programcının Sonlandırıcı çağrıldığında hiçbir denetimi yoktur; Çöp toplayıcı, ne zaman çağrılacağını belirler.</span><span class="sxs-lookup"><span data-stu-id="42157-122">The programmer has no control over when the finalizer is called; the garbage collector decides when to call it.</span></span> <span data-ttu-id="42157-123">Çöp toplayıcı, artık uygulama tarafından kullanılmayan nesneleri denetler.</span><span class="sxs-lookup"><span data-stu-id="42157-123">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="42157-124">Sonlandırma için uygun bir nesne kabul eder, sonlandırıcıyı çağırır (varsa) ve nesneyi depolamak için kullanılan belleği geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="42157-124">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="42157-125">.NET Framework uygulamalarda (.NET Core uygulamalarında değil), program çıkıldığında sonlandırıcılar da çağırılır.</span><span class="sxs-lookup"><span data-stu-id="42157-125">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="42157-126">Çöp toplamayı çağırarak <xref:System.GC.Collect%2A> , ancak çoğu zaman, performans sorunları oluşturabileceğinden Bu çağrının önlenebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="42157-126">It's possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this call should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="42157-127">Kaynakları serbest bırakmak için sonlandırıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="42157-127">Using finalizers to release resources</span></span>  
 <span data-ttu-id="42157-128">Genellikle C#, bir çalışma zamanını çöp koleksiyonuyla hedeflemez diller olarak geliştirici bölümünde çok fazla bellek yönetimi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="42157-128">In general, C# does not require as much memory management on the part of the developer as languages that don't target a runtime with garbage collection.</span></span> <span data-ttu-id="42157-129">Bunun nedeni, .NET çöp toplayıcı 'nin nesneleriniz için bellek ayırmayı ve serbest bırakma işlemini örtülü olarak yönetmesinden kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="42157-129">This is because the .NET garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="42157-130">Ancak, uygulamanız Windows, dosyalar ve ağ bağlantıları gibi yönetilmeyen kaynakları kapsüller, bu kaynakları serbest bırakmak için sonlandırıcıları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="42157-130">However, when your application encapsulates unmanaged resources, such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="42157-131">Nesne sonlandırmaya uygun olduğunda, çöp toplayıcı `Finalize` nesnenin yöntemini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="42157-131">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="42157-132">Kaynakların açık yayını</span><span class="sxs-lookup"><span data-stu-id="42157-132">Explicit release of resources</span></span>  
 <span data-ttu-id="42157-133">Uygulamanız pahalı bir dış kaynak kullanıyorsa, atık toplayıcı nesneyi serbest bırakmadan önce kaynağı açıkça serbest bırakmak için bir yol sağlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="42157-133">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="42157-134">Kaynağı serbest bırakmak için, `Dispose` <xref:System.IDisposable> arabiriminden nesne için gerekli temizleme işlemini gerçekleştiren bir yöntem uygulayın.</span><span class="sxs-lookup"><span data-stu-id="42157-134">To release the resource, implement a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="42157-135">Bu, uygulamanın performansını önemli ölçüde iyileştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="42157-135">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="42157-136">Kaynak üzerinde bu açık denetimle birlikte, yöntem çağrısı başarısız olursa Sonlandırıcı, kaynakları temizlemek için bir güvenlik önlemi haline gelir `Dispose` .</span><span class="sxs-lookup"><span data-stu-id="42157-136">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method fails.</span></span>  
  
 <span data-ttu-id="42157-137">Kaynakları Temizleme hakkında daha fazla bilgi için aşağıdaki makalelere bakın:</span><span class="sxs-lookup"><span data-stu-id="42157-137">For more information about cleaning up resources, see the following articles:</span></span>  
  
- [<span data-ttu-id="42157-138">Yönetilmeyen Kaynakları Temizleme</span><span class="sxs-lookup"><span data-stu-id="42157-138">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="42157-139">Dispose Yöntemi Uygulama</span><span class="sxs-lookup"><span data-stu-id="42157-139">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="42157-140">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="42157-140">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="42157-141">Örnek</span><span class="sxs-lookup"><span data-stu-id="42157-141">Example</span></span>  
 <span data-ttu-id="42157-142">Aşağıdaki örnek, bir devralım zinciri oluşturan üç sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="42157-142">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="42157-143">Sınıfı `First` temel sınıftır, `Second` öğesinden türetilir `First` ve `Third` öğesinden türetilir `Second` .</span><span class="sxs-lookup"><span data-stu-id="42157-143">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="42157-144">Tüm üçünün sonlandırıcıları vardır.</span><span class="sxs-lookup"><span data-stu-id="42157-144">All three have finalizers.</span></span> <span data-ttu-id="42157-145">`Main`' De, en çok türetilmiş sınıfın bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="42157-145">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="42157-146">Program çalıştığında, üç sınıfa ait sonlandırıcılara otomatik olarak ve sırasıyla en az türetilmiş ' dan türetilmiş ' a göre çağrıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="42157-146">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="42157-147">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="42157-147">C# language specification</span></span>  

<span data-ttu-id="42157-148">Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [Yıkıcılar](~/_csharplang/spec/classes.md#destructors) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="42157-148">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="42157-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="42157-149">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="42157-150">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="42157-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="42157-151">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="42157-151">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="42157-152">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="42157-152">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
