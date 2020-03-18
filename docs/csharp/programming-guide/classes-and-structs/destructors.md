---
title: Finalistler - C# Programlama Kılavuzu
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: c8ad738baa3ff76cf9ae8367f2fd2a1fb44a79d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170305"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="6061b-102">Finalistler (C# Programlama Kılavuzu)</span><span class="sxs-lookup"><span data-stu-id="6061b-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="6061b-103">**Sonlandırıcılar (yıkıcılar**olarak da adlandırılır) bir sınıf örneği çöp toplayıcı tarafından toplanırken gerekli son temizlemeyi gerçekleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6061b-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6061b-104">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6061b-104">Remarks</span></span>  
  
- <span data-ttu-id="6061b-105">Sonlandırıcılar structs olarak tanımlanamaz.</span><span class="sxs-lookup"><span data-stu-id="6061b-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="6061b-106">Onlar sadece sınıflar ile kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6061b-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="6061b-107">Bir sınıfın sadece bir finalleştiricisi olabilir.</span><span class="sxs-lookup"><span data-stu-id="6061b-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="6061b-108">Finalistler devralınamaz veya aşırı yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="6061b-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="6061b-109">Sonlandırıcılar çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="6061b-109">Finalizers cannot be called.</span></span> <span data-ttu-id="6061b-110">Otomatik olarak çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6061b-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="6061b-111">Bir sonlandırıcı değiştiriciler almaz veya parametreleri var.</span><span class="sxs-lookup"><span data-stu-id="6061b-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="6061b-112">Örneğin, aşağıdaki `Car` sınıf için bir sonlandırıcı bildirimidir.</span><span class="sxs-lookup"><span data-stu-id="6061b-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="6061b-113">Bir sonlandırıcı, aşağıdaki örnekte de görüldüğü gibi, ifade gövdesi tanımı olarak da uygulanabilir.</span><span class="sxs-lookup"><span data-stu-id="6061b-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="6061b-114">Sonlandırıcı dolaylı olarak <xref:System.Object.Finalize%2A> nesnenin taban sınıfını çağırır.</span><span class="sxs-lookup"><span data-stu-id="6061b-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="6061b-115">Bu nedenle, bir sonlandırıcı için bir çağrı örtülü olarak aşağıdaki koda çevrilir:</span><span class="sxs-lookup"><span data-stu-id="6061b-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="6061b-116">Bu, yöntemin `Finalize` devralma zincirindeki tüm örnekler için, en çok türetilmiş olandan en az türetilmiş olana kadar özyinelemeli olarak çağrıldığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="6061b-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6061b-117">Boş sonlandırıcılar kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="6061b-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="6061b-118">Bir sınıf bir sonlandırıcı içeriyorsa, `Finalize` sırada bir giriş oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6061b-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="6061b-119">Sonlandırıcı çağrıldığında, sırayı işlemek için çöp toplayıcısı çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6061b-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="6061b-120">Boş bir finalize sadece performans gereksiz bir kaybına neden olur.</span><span class="sxs-lookup"><span data-stu-id="6061b-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="6061b-121">Bu çöp toplayıcı tarafından belirlenir, çünkü sonlandırıcı çağrıldığında programcı üzerinde hiçbir kontrole sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6061b-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="6061b-122">Çöp toplayıcı, uygulama tarafından artık kullanılmayan nesneleri denetler.</span><span class="sxs-lookup"><span data-stu-id="6061b-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="6061b-123">Bir nesneyi sonlandırmaiçin uygun görürse, sonlandırıcıyı (varsa) çağırır ve nesneyi depolamak için kullanılan belleği geri alır.</span><span class="sxs-lookup"><span data-stu-id="6061b-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="6061b-124">.NET Framework uygulamalarında (ancak .NET Core uygulamalarında değil), program çıktığında sonlandırıcılar da çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6061b-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="6061b-125">Çöp toplamayı çağırarak zorlamak <xref:System.GC.Collect%2A>mümkündür, ancak çoğu zaman performans sorunları oluşturabileceğinden bu kaçınılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6061b-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="6061b-126">Kaynakları serbest bırakmak için sonlandırıcıları kullanma</span><span class="sxs-lookup"><span data-stu-id="6061b-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="6061b-127">Genel olarak, C# çöp toplama ile çalışma süresini hedeflemeyen bir dil ile geliştirdiğiniz zaman gerektiği kadar bellek yönetimi gerektirmez.</span><span class="sxs-lookup"><span data-stu-id="6061b-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="6061b-128">Bunun nedeni, .NET Framework çöp toplayıcısının nesneleriniz için bellek tahsisini ve serbest bırakılmasını dolaylı olarak yönetmesidir.</span><span class="sxs-lookup"><span data-stu-id="6061b-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="6061b-129">Ancak, uygulamanız windows, dosyalar ve ağ bağlantıları gibi yönetilmeyen kaynakları kapsüllediğinde, bu kaynakları serbest leştirmek için sonlandırıcılar kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6061b-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="6061b-130">Nesne sonlandırma için uygun olduğunda, çöp `Finalize` toplayıcı nesnenin yöntemini çalıştırAr.</span><span class="sxs-lookup"><span data-stu-id="6061b-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="6061b-131">Kaynakların açık serbest bırakılması</span><span class="sxs-lookup"><span data-stu-id="6061b-131">Explicit release of resources</span></span>  
 <span data-ttu-id="6061b-132">Uygulamanız pahalı bir dış kaynak kullanıyorsa, çöp toplayıcı nesneyi serbest bırakmadan önce kaynağı açıkça serbest bırakmanın bir yolunu da sağlamanızı öneririz.</span><span class="sxs-lookup"><span data-stu-id="6061b-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="6061b-133">Bunu, nesne için `Dispose` gerekli temizlemeyi gerçekleştiren <xref:System.IDisposable> arabirimden bir yöntem uygulayarak yaparsınız.</span><span class="sxs-lookup"><span data-stu-id="6061b-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="6061b-134">Bu, uygulamanın performansını önemli ölçüde artırabilir.</span><span class="sxs-lookup"><span data-stu-id="6061b-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="6061b-135">Kaynaklar üzerindeki bu açık denetime rağmen, `Dispose` sonlandırıcı, yönteme çağrı başarısız olursa kaynakları temizlemek için bir koruma haline gelir.</span><span class="sxs-lookup"><span data-stu-id="6061b-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="6061b-136">Kaynakları temizleme hakkında daha fazla bilgi için aşağıdaki konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="6061b-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
- [<span data-ttu-id="6061b-137">Yönetilmeyen Kaynakları Temizleme</span><span class="sxs-lookup"><span data-stu-id="6061b-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="6061b-138">Dispose Yöntemi Uygulama</span><span class="sxs-lookup"><span data-stu-id="6061b-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="6061b-139">Ekstresi'ni kullanma</span><span class="sxs-lookup"><span data-stu-id="6061b-139">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="6061b-140">Örnek</span><span class="sxs-lookup"><span data-stu-id="6061b-140">Example</span></span>  
 <span data-ttu-id="6061b-141">Aşağıdaki örnek, bir devralma zinciri oluşturan üç sınıf oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6061b-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="6061b-142">Sınıf `First` taban sınıftır, `Second` `First`türetilmiştir `Third` , ve `Second`türetilmiştir .</span><span class="sxs-lookup"><span data-stu-id="6061b-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="6061b-143">Üçünün de finalistleri var.</span><span class="sxs-lookup"><span data-stu-id="6061b-143">All three have finalizers.</span></span> <span data-ttu-id="6061b-144">Içinde `Main`, en çok türetilmiş sınıfın bir örneği oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="6061b-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="6061b-145">Program çalıştığında, üç sınıfın sonlandırıcılarının otomatik olarak ve sırayla en çok türetilmiş olandan en az türetilmiş olana çağrıldığına dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="6061b-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6061b-146">C# dili belirtimi</span><span class="sxs-lookup"><span data-stu-id="6061b-146">C# language specification</span></span>  

<span data-ttu-id="6061b-147">Daha fazla bilgi için [C# dil belirtiminin](/dotnet/csharp/language-reference/language-specification/introduction) [Yıkıcılar](~/_csharplang/spec/classes.md#destructors) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="6061b-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="6061b-148">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6061b-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="6061b-149">C# Programlama Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="6061b-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="6061b-150">Oluşturucular</span><span class="sxs-lookup"><span data-stu-id="6061b-150">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="6061b-151">Çöp Toplama</span><span class="sxs-lookup"><span data-stu-id="6061b-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
