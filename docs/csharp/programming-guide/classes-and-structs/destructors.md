---
title: Sonlandırıcılar- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 9936d56582afd160bf3464d18efd3acf47c7af60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924491"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="e456a-102">Sonlandırıcılar (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="e456a-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="e456a-103">Sonlandırıcılar (yani **Yıkıcılar**olarak da bilinir), bir sınıf örneği çöp toplayıcısı tarafından toplandığında gerekli son temizleme işlemini gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e456a-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e456a-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e456a-104">Remarks</span></span>  
  
- <span data-ttu-id="e456a-105">Sonlandırıcılar yapılar içinde tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="e456a-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="e456a-106">Bunlar yalnızca sınıflarla birlikte kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e456a-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="e456a-107">Bir sınıfın yalnızca bir sonlandırıcısı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e456a-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="e456a-108">Sonlandırıcılar devralınamaz veya aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="e456a-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="e456a-109">Sonlandırıcılar çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="e456a-109">Finalizers cannot be called.</span></span> <span data-ttu-id="e456a-110">Bunlar otomatik olarak çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e456a-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="e456a-111">Sonlandırıcı değiştirici almaz veya parametrelere sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="e456a-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="e456a-112">Örneğin, aşağıdaki, `Car` sınıfı için sonlandırıcının bir bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="e456a-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="e456a-113">Bir Sonlandırıcı, aşağıdaki örnekte gösterildiği gibi bir ifade gövdesi tanımı olarak da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="e456a-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="e456a-114">Sonlandırıcı nesnenin temel sınıfında <xref:System.Object.Finalize%2A> örtülü olarak çağrı çağırır.</span><span class="sxs-lookup"><span data-stu-id="e456a-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="e456a-115">Bu nedenle, sonlandırıcının çağrısı dolaylı olarak aşağıdaki koda çevrilir:</span><span class="sxs-lookup"><span data-stu-id="e456a-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="e456a-116">Bu, `Finalize` metodun devralma zincirindeki tüm örnekler için özyinelemeli olarak çağrıldığı ve en az türetilen en düşük olan ' dır.</span><span class="sxs-lookup"><span data-stu-id="e456a-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e456a-117">Boş sonlandırıcılar kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="e456a-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="e456a-118">Bir sınıf bir Sonlandırıcı içerdiğinde, `Finalize` kuyrukta bir giriş oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e456a-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="e456a-119">Sonlandırıcı çağrıldığında, atık toplayıcı kuyruğu işleyecek şekilde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e456a-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="e456a-120">Boş bir Sonlandırıcı yalnızca gereksiz performans kaybına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e456a-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="e456a-121">Bu, çöp toplayıcı tarafından belirlendiği için sonlandırıcının çağrıldığı zaman üzerinde denetime sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="e456a-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="e456a-122">Çöp toplayıcı, artık uygulama tarafından kullanılmayan nesneleri denetler.</span><span class="sxs-lookup"><span data-stu-id="e456a-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="e456a-123">Sonlandırma için uygun bir nesne kabul eder, sonlandırıcıyı çağırır (varsa) ve nesneyi depolamak için kullanılan belleği geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="e456a-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> 
 
 <span data-ttu-id="e456a-124">.NET Framework uygulamalarda (.NET Core uygulamalarında değil), program çıkıldığında sonlandırıcılar da çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e456a-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span> 
  
 <span data-ttu-id="e456a-125">Çöp toplamayı çağırarak <xref:System.GC.Collect%2A>, ancak çoğu zaman performans sorunları oluşturabileceğinden bu durum kaçınılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e456a-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="e456a-126">Kaynakları serbest bırakmak için sonlandırıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="e456a-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="e456a-127">Genel olarak, C# çöp toplama ile çalışma zamanını hedeflemez bir dille geliştirirken gereken kadar bellek yönetimi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="e456a-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="e456a-128">Bunun nedeni, .NET Framework atık toplayıcının nesneleriniz için bellek ayırmayı ve serbest bırakma işlemini örtülü olarak yönetmesinden kaynaklanır.</span><span class="sxs-lookup"><span data-stu-id="e456a-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="e456a-129">Ancak, uygulamanız Windows, dosyalar ve ağ bağlantıları gibi yönetilmeyen kaynakları kapsüller, bu kaynakları serbest bırakmak için sonlandırıcıları kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e456a-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="e456a-130">Nesne sonlandırmaya uygun olduğunda, çöp toplayıcı nesnenin `Finalize` yöntemini çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="e456a-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="e456a-131">Kaynakların açık yayını</span><span class="sxs-lookup"><span data-stu-id="e456a-131">Explicit release of resources</span></span>  
 <span data-ttu-id="e456a-132">Uygulamanız pahalı bir dış kaynak kullanıyorsa, atık toplayıcı nesneyi serbest bırakmadan önce kaynağı açıkça serbest bırakmak için bir yol sağlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="e456a-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="e456a-133">Bu, nesnesi için gerekli temizleme `Dispose` işlemini gerçekleştiren <xref:System.IDisposable> arabirimden bir yöntem uygulayarak yapılır.</span><span class="sxs-lookup"><span data-stu-id="e456a-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="e456a-134">Bu, uygulamanın performansını önemli ölçüde iyileştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="e456a-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="e456a-135">Kaynak üzerinde bu açık denetimle birlikte, `Dispose` Yöntem çağrısı başarısız olursa Sonlandırıcı, kaynakları temizlemek için bir güvenlik önlemi haline gelir.</span><span class="sxs-lookup"><span data-stu-id="e456a-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="e456a-136">Kaynakları Temizleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="e456a-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
- [<span data-ttu-id="e456a-137">Yönetilmeyen Kaynakları Temizleme</span><span class="sxs-lookup"><span data-stu-id="e456a-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="e456a-138">Dispose Yöntemi Uygulama</span><span class="sxs-lookup"><span data-stu-id="e456a-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="e456a-139">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="e456a-139">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="e456a-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="e456a-140">Example</span></span>  
 <span data-ttu-id="e456a-141">Aşağıdaki örnek, bir devralım zinciri oluşturan üç sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e456a-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="e456a-142">Sınıfı `First` temel sınıftır, `Second` öğesinden `First`türetilir ve `Third` öğesinden `Second`türetilir.</span><span class="sxs-lookup"><span data-stu-id="e456a-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="e456a-143">Tüm üçünün sonlandırıcıları vardır.</span><span class="sxs-lookup"><span data-stu-id="e456a-143">All three have finalizers.</span></span> <span data-ttu-id="e456a-144">' `Main`De, en çok türetilmiş sınıfın bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e456a-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="e456a-145">Program çalıştığında, üç sınıfa ait sonlandırıcılara otomatik olarak ve sırasıyla en az türetilmiş ' dan türetilmiş ' a göre çağrıldığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e456a-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e456a-146">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="e456a-146">C# language specification</span></span>  

<span data-ttu-id="e456a-147">Daha fazla bilgi için [ C# dil belirtiminin](../../language-reference/language-specification/index.md) [Yıkıcılar](~/_csharplang/spec/classes.md#destructors) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="e456a-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](../../language-reference/language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e456a-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e456a-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="e456a-149">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="e456a-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e456a-150">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="e456a-150">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="e456a-151">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="e456a-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
