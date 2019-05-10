---
title: Sonlandırıcılar - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 87755eadeaebb72c5a8ce147ba2e6faf109e6c12
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64584379"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="8eae9-102">Sonlandırıcılar (C# programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="8eae9-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="8eae9-103">Sonlandırıcılar (de denir **yok ediciler**) çöp toplayıcısı tarafından toplanmış bir sınıf örneği, tüm gerekli son temizleme gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8eae9-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8eae9-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8eae9-104">Remarks</span></span>  
  
- <span data-ttu-id="8eae9-105">Sonlandırıcılar yapılarda tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="8eae9-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="8eae9-106">Bunlar, yalnızca sınıf ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8eae9-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="8eae9-107">Bir sınıf, bir sonlandırıcı yalnızca olabilir.</span><span class="sxs-lookup"><span data-stu-id="8eae9-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="8eae9-108">Sonlandırıcılar devralınmış veya aşırı yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="8eae9-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="8eae9-109">Sonlandırıcılar çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="8eae9-109">Finalizers cannot be called.</span></span> <span data-ttu-id="8eae9-110">Bunlar otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8eae9-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="8eae9-111">Bir sonlandırıcı değiştiriciler alın veya parametreleri desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8eae9-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="8eae9-112">Örneğin, bir sonlandırıcı için bildirimi aşağıdaki gibidir `Car` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="8eae9-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="8eae9-113">Bir Sonlandırıcı, aşağıdaki örnekte gösterildiği gibi bir ifade gövdesi tanımı da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="8eae9-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="8eae9-114">Sonlandırıcı örtük olarak çağırır <xref:System.Object.Finalize%2A> nesnenin temel sınıfı üzerinde.</span><span class="sxs-lookup"><span data-stu-id="8eae9-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="8eae9-115">Bu nedenle, bir sonlandırıcı bir çağrı örtük olarak aşağıdaki kodu çevrilir:</span><span class="sxs-lookup"><span data-stu-id="8eae9-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="8eae9-116">Diğer bir deyişle `Finalize` yöntemi çağrılır yinelemeli devralma zincirini tüm örnekler için en çok türetilen en az türetilen için.</span><span class="sxs-lookup"><span data-stu-id="8eae9-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8eae9-117">Boş Sonlandırıcıları kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="8eae9-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="8eae9-118">Bir sınıf, bir sonlandırıcı içeriyorsa, bir giriş oluşturulan `Finalize` kuyruk.</span><span class="sxs-lookup"><span data-stu-id="8eae9-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="8eae9-119">Sonlandırıcı çağrıldığında çöp toplayıcı kuyruğu işlemek için çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8eae9-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="8eae9-120">Boş Sonlandırıcı yalnızca gereksiz bir performans kaybı neden olur.</span><span class="sxs-lookup"><span data-stu-id="8eae9-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="8eae9-121">Bu çöp toplayıcı tarafından belirlenir çünkü Sonlandırıcı çağrıldığında Programcı üzerinde denetimi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8eae9-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="8eae9-122">Çöp toplayıcı uygulama tarafından artık kullanılmayan nesneleri denetler.</span><span class="sxs-lookup"><span data-stu-id="8eae9-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="8eae9-123">Bu nesne sonlandırma için uygun olarak değerlendirir, sonlandırıcı (varsa) çağırır ve nesne depolamak için kullanılan belleği geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="8eae9-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> 
 
 <span data-ttu-id="8eae9-124">Program çıkış yaptığı andaki .NET Framework uygulamalarında (ancak .NET Core uygulamalarında), bir sonlandırıcı da denir.</span><span class="sxs-lookup"><span data-stu-id="8eae9-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span> 
  
 <span data-ttu-id="8eae9-125">Çağırarak atık toplamayı zorlamak mümkün mü <xref:System.GC.Collect%2A>, ancak performans sorunları oluşturabilir, çünkü çoğu zaman bu kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8eae9-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="8eae9-126">Kaynaklar serbest bırakılacaksa Sonlandırıcı kullanma</span><span class="sxs-lookup"><span data-stu-id="8eae9-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="8eae9-127">Genel olarak, C# bir çalışma zamanının atık toplama ile hedeflemiyor bir dil ile geliştirdiğinizde gerektiği kadar bellek yönetimi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="8eae9-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="8eae9-128">.NET Framework atık toplayıcı, örtük olarak sağlanmasını ve ayrılmasını, nesneler için bellek yönetir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8eae9-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="8eae9-129">Ancak, uygulamanızı windows, dosyaları ve ağ bağlantıları gibi yönetilmeyen kaynakları yalıtan, bu kaynakları serbest bırakacak sonlandırıcılar kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8eae9-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="8eae9-130">Nesne sonlandırma için uygun olduğunda, Atık toplayıcısının çalışacağı `Finalize` nesnesinin yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8eae9-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="8eae9-131">Açık kaynak sürümü</span><span class="sxs-lookup"><span data-stu-id="8eae9-131">Explicit release of resources</span></span>  
 <span data-ttu-id="8eae9-132">Uygulamanızı pahalı bir dış kaynağa kullanıyorsanız, çöp toplayıcı nesneyi serbest bırakan önce kaynak açıkça serbest bırakmak için bir yol sağlamak da öneririz.</span><span class="sxs-lookup"><span data-stu-id="8eae9-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="8eae9-133">Uygulayarak bunu bir `Dispose` yönteminden <xref:System.IDisposable> nesne için gerekli temizleme gerçekleştirir arabirimi.</span><span class="sxs-lookup"><span data-stu-id="8eae9-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="8eae9-134">Bu, uygulamanın performansını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="8eae9-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="8eae9-135">Bile bu açık denetime ile kaynakları, sonlandırıcı durumunda kaynakları temizlemek için bir önlem haline gelir. çağrı `Dispose` yöntemi başarısız oldu.</span><span class="sxs-lookup"><span data-stu-id="8eae9-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="8eae9-136">Kaynakları temizleme hakkında daha fazla ayrıntı için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="8eae9-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
- [<span data-ttu-id="8eae9-137">Yönetilmeyen Kaynakları Temizleme</span><span class="sxs-lookup"><span data-stu-id="8eae9-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="8eae9-138">Dispose Yöntemi Uygulama</span><span class="sxs-lookup"><span data-stu-id="8eae9-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="8eae9-139">using Deyimi</span><span class="sxs-lookup"><span data-stu-id="8eae9-139">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="8eae9-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="8eae9-140">Example</span></span>  
 <span data-ttu-id="8eae9-141">Aşağıdaki örnek, bir devralma zincirini olun üç sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8eae9-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="8eae9-142">Sınıf `First` temel sınıf `Second` türetilir `First`, ve `Third` türetilir `Second`.</span><span class="sxs-lookup"><span data-stu-id="8eae9-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="8eae9-143">Üç sonlandırıcılar vardır.</span><span class="sxs-lookup"><span data-stu-id="8eae9-143">All three have finalizers.</span></span> <span data-ttu-id="8eae9-144">İçinde `Main`, en çok türetilen sınıfın bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="8eae9-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="8eae9-145">Program çalıştığında sonlandırıcılar üç sınıfları için otomatik olarak ve sırasıyla en çok türetilen en az türetilen için gelen çağrılır, dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="8eae9-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8eae9-146">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="8eae9-146">C# language specification</span></span>  

<span data-ttu-id="8eae9-147">Daha fazla bilgi için [yok ediciler](~/_csharplang/spec/classes.md#destructors) bölümünü [ C# dil belirtimi](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8eae9-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](../../language-reference/language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8eae9-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8eae9-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="8eae9-149">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="8eae9-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8eae9-150">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="8eae9-150">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="8eae9-151">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="8eae9-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
