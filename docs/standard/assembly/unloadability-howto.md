---
title: Nasıl kullanılacağını ve hata ayıklama derlemesi unloadability .NET core'da
description: Toplanabilir AssemblyLoadContext yönetilen derlemeleri yükleme ve kaldırma ve kaldırma başarılı engelleyen sorunları hata ayıklamak nasıl kullanılacağını öğrenin.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 2929110952feb0913f21a9c69975cc605f49c646
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61627791"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="0db9f-103">Nasıl kullanılacağını ve hata ayıklama derlemesi unloadability .NET core'da</span><span class="sxs-lookup"><span data-stu-id="0db9f-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="0db9f-104">.NET Core 3.0 ile başlayarak, yükleme ve daha sonra bir derleme kümesi kaldırma olanağı desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="0db9f-105">.NET Framework'teki özel uygulama etki alanları bu amaç için kullanılan, ancak .NET Core, yalnızca tek bir varsayılan uygulama etki alanını destekler.</span><span class="sxs-lookup"><span data-stu-id="0db9f-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="0db9f-106">.NET core 3.0 ve sonraki sürümleri destekler unloadability aracılığıyla <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="0db9f-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="0db9f-107">Bir derleme kümesi toplanabilir yükleyebilir `AssemblyLoadContext`, bunları bir yöntem yürütülemez veya yalnızca bunları inceleyin yansıma kullanarak ve son olarak kaldırma `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0db9f-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="0db9f-108">Yüklenen derlemeler bellekten `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0db9f-108">That unloads the assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="0db9f-109">Kaldırma kullanarak arasında önemli bir fark `AssemblyLoadContext` ve uygulama etki alanları kullanma.</span><span class="sxs-lookup"><span data-stu-id="0db9f-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="0db9f-110">Uygulama etki alanları ile kaldırma zorlanır.</span><span class="sxs-lookup"><span data-stu-id="0db9f-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="0db9f-111">Unload zaman hedef AppDomain tüm iş parçacıkları iptal edilir, yönetilen vb. AppDomain yok edilir hedef oluşturulan COM nesnelerini. İle `AssemblyLoadContext`, kaldırma "" ortaktır.</span><span class="sxs-lookup"><span data-stu-id="0db9f-111">At the unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, etc. With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="0db9f-112">Çağırma <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> yöntemi yalnızca başlatır kaldırma.</span><span class="sxs-lookup"><span data-stu-id="0db9f-112">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="0db9f-113">Kaldırma tamamlandıktan sonra:</span><span class="sxs-lookup"><span data-stu-id="0db9f-113">The unloading finishes after:</span></span>

- <span data-ttu-id="0db9f-114">İş parçacığı içine yüklenen derlemeler yöntemlerinden sahip `AssemblyLoadContext` çağrı yığınlarıyla üzerinde.</span><span class="sxs-lookup"><span data-stu-id="0db9f-114">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="0db9f-115">Yüklenen derlemeler türlerden hiçbiri `AssemblyLoadContext`, bu türleri ve derlemeleri örnekleri dışında `AssemblyLoadContext` tarafından başvurulan:</span><span class="sxs-lookup"><span data-stu-id="0db9f-115">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types and the assemblies themselves outside of the `AssemblyLoadContext` are referenced by:</span></span>
  - <span data-ttu-id="0db9f-116">Dışında başvuran `AssemblyLoadContext`, hariç zayıf başvurular (<xref:System.WeakReference> veya <xref:System.WeakReference%601>).</span><span class="sxs-lookup"><span data-stu-id="0db9f-116">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="0db9f-117">Güçlü GC tutamaçlarını (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span><span class="sxs-lookup"><span data-stu-id="0db9f-117">Strong GC handles (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span></span> <span data-ttu-id="0db9f-118">veya <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) hem Azure içindeki hem de dışında `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0db9f-118">or <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="using-collectible-assemblyloadcontext"></a><span data-ttu-id="0db9f-119">Toplanabilir AssemblyLoadContext kullanma</span><span class="sxs-lookup"><span data-stu-id="0db9f-119">Using collectible AssemblyLoadContext</span></span>

<span data-ttu-id="0db9f-120">Bu bölüm .NET Core uygulamasını toplanabilir yüklemek için basit bir yol gösteren ayrıntılı adım adım bir öğretici içerir `AssemblyLoadContext`, kendi giriş noktası yürütün ve bunu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="0db9f-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="0db9f-121">Bir tam örneğini şurada bulabilirsiniz <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.</span><span class="sxs-lookup"><span data-stu-id="0db9f-121">You can find a complete sample at <https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading>.</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="0db9f-122">Toplanabilir AssemblyLoadContext oluşturma</span><span class="sxs-lookup"><span data-stu-id="0db9f-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="0db9f-123">Sizin sınıfınızdan türetmek gereken <xref:System.Runtime.Loader.AssemblyLoadContext> ve aşırı yükleme, <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0db9f-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="0db9f-124">Yöntemi, yüklenen derlemelerin bağımlılıklar tüm derlemeleri başvuruları çözümleniyor `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0db9f-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>
<span data-ttu-id="0db9f-125">Aşağıdaki kod, en basit özel örneğidir `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="0db9f-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="0db9f-126">Gördüğünüz gibi `Load` yöntemi döndürür `null`.</span><span class="sxs-lookup"><span data-stu-id="0db9f-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="0db9f-127">Bu, tüm bağımlılık derlemelerin varsayılan bağlamına yüklü olduğundan ve yalnızca açıkça içine yüklenen derlemeler yeni bağlam içeren anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="0db9f-128">Bazı veya tüm bağımlılıklarınızı yüklemek istiyorsanız `AssemblyLoadContext` de kullanabileceğiniz `AssemblyDependencyResolver` içinde `Load` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0db9f-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="0db9f-129">`AssemblyDependencyResolver` Kullanarak mutlak derleme dosya yolları için derleme adlarını çözümleyen `*.deps.json` ana derleme bağlamı ve derleme dosyaları dizindeki kullanarak yüklenen dizininde yer alan dosya.</span><span class="sxs-lookup"><span data-stu-id="0db9f-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths using the `*.deps.json` file contained in the directory of the main assembly loaded into the context and using assembly files in that directory.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="0db9f-130">Özel bir toplanabilir AssemblyLoadContext kullanın</span><span class="sxs-lookup"><span data-stu-id="0db9f-130">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="0db9f-131">Bu bölümde daha basit sürümü varsayılır `TestAssemblyLoadContext` kullanılıyor.</span><span class="sxs-lookup"><span data-stu-id="0db9f-131">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="0db9f-132">Özel bir örneğini oluşturabilirsiniz `AssemblyLoadContext` ve bir derleme içine aşağıdaki gibi yükleyin:</span><span class="sxs-lookup"><span data-stu-id="0db9f-132">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="0db9f-133">Her yüklenen derlemesi tarafından başvurulan derlemelerin `TestAssemblyLoadContext.Load` yöntemi çağrıldığında böylece `TestAssemblyLoadContext` derlemeden nereden karar verebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0db9f-133">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="0db9f-134">Bu örnekte, döndürür `null` bu derlemeleri yüklemeye çalışma zamanı kullanan konumlardan varsayılan bağlamına varsayılan yükleneceğini göstermek için.</span><span class="sxs-lookup"><span data-stu-id="0db9f-134">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="0db9f-135">Bir derleme yüklendi, ondan bir yöntem yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-135">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="0db9f-136">Çalıştırma `Main` yöntemi:</span><span class="sxs-lookup"><span data-stu-id="0db9f-136">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="0db9f-137">Sonra `Main` yöntemi döndürür, ya da çağrısı yaparak eklentiyi başlatabilirsiniz `Unload` özel metodunda `AssemblyLoadContext` veya zorunda başvurunun doğurduğu israftan `AssemblyLoadContext`:</span><span class="sxs-lookup"><span data-stu-id="0db9f-137">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="0db9f-138">Bu test derlemesini kaldırmak yeterli olur.</span><span class="sxs-lookup"><span data-stu-id="0db9f-138">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="0db9f-139">Şimdi tüm emin olmak için ayrı bir inlineable olmayan yönteme gerçekten put `TestAssemblyLoadContext`, `Assembly`, ve `MethodInfo` ( `Assembly.EntryPoint`) yığını yuvası başvuruları (gerçek veya JIT sunulan Yereller) tarafından etkin tutulan bağlantıyı destekliyorsa tutulması olamaz.</span><span class="sxs-lookup"><span data-stu-id="0db9f-139">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="0db9f-140">Tutun `TestAssemblyLoadContext` etkin tutulan bağlantıyı destekliyorsa ve yüklemelerini kaldırma engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-140">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="0db9f-141">Ayrıca, zayıf bir başvuru döndürmeyi `AssemblyLoadContext` böylece bunu daha sonra kaldırma tamamlama algılamak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0db9f-141">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="0db9f-142">Artık, yükleme, yürütme ve derlemeyi kaldırmak için bu işlevi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0db9f-142">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="0db9f-143">Ancak, kaldırma, hemen tamamlanmıyor.</span><span class="sxs-lookup"><span data-stu-id="0db9f-143">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="0db9f-144">Daha önce belirtildiği gibi tüm nesneleri test derlemesinden toplanacak GC kullanır.</span><span class="sxs-lookup"><span data-stu-id="0db9f-144">As previously mentioned, it relies on the GC to collect all the objects from the test assembly.</span></span> <span data-ttu-id="0db9f-145">Çoğu durumda, kaldırma tamamlanmasını beklemeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0db9f-145">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="0db9f-146">Ancak, kaldırma işleminin tamamlandığını bilmek de yararlı olduğu durumlar da vardır.</span><span class="sxs-lookup"><span data-stu-id="0db9f-146">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="0db9f-147">Örneğin, özel yüklenen derleme dosyasını silmek isteyebilirsiniz `AssemblyLoadContext` diskten.</span><span class="sxs-lookup"><span data-stu-id="0db9f-147">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="0db9f-148">Böyle bir durumda, aşağıdaki kod parçacığı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-148">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="0db9f-149">GC tetikler ve bir döngüde sonlandırıcılar bekleyen özel zayıf başvuruyu kadar bekler `AssemblyLoadContext` ayarlanır `null`, hedef nesneyi gösteren toplanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0db9f-149">It triggers a GC and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="0db9f-150">Çoğu durumda, yalnızca tek seferde döngü gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0db9f-150">Note that in most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="0db9f-151">Ancak, nesne oluşturulduğu çalışan kod tarafından daha karmaşık durumlarda `AssemblyLoadContext` Sonlandırıcıları sahip daha fazla geçiş gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-151">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="0db9f-152">Unloading olay</span><span class="sxs-lookup"><span data-stu-id="0db9f-152">The Unloading event</span></span>

<span data-ttu-id="0db9f-153">Bazı durumlarda, bir özel yüklenen kod için gerekli olabilir `AssemblyLoadContext` kaldırma başlatıldığında bazı temizleme işlemleri gerçekleştirmek için.</span><span class="sxs-lookup"><span data-stu-id="0db9f-153">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="0db9f-154">Örneğin, gereksinim duymayabilirsiniz iş parçacıklarını durdurma, temiz bazı güçlü GC tanıtıcıları, vb. `Unloading` Olay bu gibi durumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-154">For example, it may need to stop threads, clean up some strong GC handles, etc. The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="0db9f-155">Bu olay için gerekli temizleme işlemini gerçekleştiren bir işleyici bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-155">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="0db9f-156">Unloadability sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="0db9f-156">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="0db9f-157">İşbirlikçi yapısı nedeniyle, eklentiyi, her şeyi bir toplanabilir tutma başvurular hakkında unutmak çok kolaydır `AssemblyLoadContext` etkin tutulan bağlantıyı destekliyorsa ve engelleme kaldırma.</span><span class="sxs-lookup"><span data-stu-id="0db9f-157">Due to the cooperative nature of the unloading, it's easy to forget about references keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="0db9f-158">Başvuruları tutabilen ve nesnelerin interneti (bunlardan bazıları belirgin olmayan) bir özeti aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0db9f-158">Here is a summary of things (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="0db9f-159">Normal başvuruları tutulan gelen toplanabilir dışında `AssemblyLoadContext`, yığın yuvası veya işlemci kaydı (ya da kullanıcı kod tarafından veya örtük olarak JIT tarafından açıkça oluşturulan yöntemi Yereller), bir statik değişken veya bir güçlü / sabitleme GC tanıtıcı depolanır ve geçişli işaret eden:</span><span class="sxs-lookup"><span data-stu-id="0db9f-159">Regular references held from outside of the collectible `AssemblyLoadContext`, stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the JIT), a static variable or a strong / pinning GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="0db9f-160">Bir derleme yüklenen toplanabilir `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0db9f-160">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="0db9f-161">Böyle bir derlemeden bir tür.</span><span class="sxs-lookup"><span data-stu-id="0db9f-161">A type from such an assembly.</span></span>
  - <span data-ttu-id="0db9f-162">Böyle bir derlemeden bir tür örneği.</span><span class="sxs-lookup"><span data-stu-id="0db9f-162">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="0db9f-163">Bir derlemeye ait kod çalıştıran iş parçacığı toplanabilir yüklenen `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="0db9f-163">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="0db9f-164">Özel toplanabilir olmayan örneklerini `AssemblyLoadContext` toplanabilir içinde oluşturulan türleri `AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="0db9f-164">Instances of custom non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`</span></span>
- <span data-ttu-id="0db9f-165">Bekleyen <xref:System.Threading.RegisteredWaitHandle> geri çağırmaları örnekleriyle ayarlanmış özel yöntemler `AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="0db9f-165">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`</span></span>

<span data-ttu-id="0db9f-166">Yığın yuvası bulmak için ipuçları işlemci Register nesneyi kök dizini değiştirme:</span><span class="sxs-lookup"><span data-stu-id="0db9f-166">Hints to find stack slot / processor register rooting an object:</span></span>

- <span data-ttu-id="0db9f-167">İşlev çağrısı sonuçları doğrudan başka bir işlev için hiçbir kullanıcı tarafından oluşturulan yerel değişken olsa bile bir kök oluşturabilir geçirme.</span><span class="sxs-lookup"><span data-stu-id="0db9f-167">Passing function call results directly to another function may create a root even though there is no user-created local variable.</span></span>
- <span data-ttu-id="0db9f-168">Bir nesneye bir başvuru bir yöntem herhangi bir noktada mevcut olduğunda, JIT yığın yuvasında başvurusunu korumanız karar verdiğiniz / işlemcisi kaydetmek için geçerli işlevde istediği sürece.</span><span class="sxs-lookup"><span data-stu-id="0db9f-168">If a reference to an object was available at any point in a method, the JIT might have decided to keep the reference in a stack slot / processor register for as long as it wants in the current function.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="0db9f-169">Kaldırma sorunlarında hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="0db9f-169">Debug unloading issues</span></span>

<span data-ttu-id="0db9f-170">Hata ayıklama kaldırma sorunlarını can sıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-170">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="0db9f-171">Burada bilmediğiniz ne bulunduran durumlarda alabileceğiniz bir `AssemblyLoadContext` etkin tutulan bağlantıyı destekliyorsa, ancak kaldırma başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="0db9f-171">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span>
<span data-ttu-id="0db9f-172">İle yardımcı olması için en iyi Silah WinDbg (LLDB UNIX üzerinde) ile SOS eklentisidir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-172">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="0db9f-173">Tutuyor mu bulmanız gereken bir `LoaderAllocator` belirli ait `AssemblyLoadContext` tutma.</span><span class="sxs-lookup"><span data-stu-id="0db9f-173">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span>
<span data-ttu-id="0db9f-174">Bu eklenti, GC yığın nesnelerini, hiyerarşiler ve kökleri aramak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0db9f-174">This plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>
<span data-ttu-id="0db9f-175">Eklenti hata ayıklayıcısına yüklemek için hata ayıklayıcı komut satırında aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="0db9f-175">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="0db9f-176">(WinDbg otomatik olarak .NET Core uygulamasına bozucu olduğunda yapan görünüyor) WinDbg içinde:</span><span class="sxs-lookup"><span data-stu-id="0db9f-176">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="0db9f-177">LLDB içinde:</span><span class="sxs-lookup"><span data-stu-id="0db9f-177">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="0db9f-178">Örnek kaldırma sorunları olan bir programı hata ayıklama deneyelim.</span><span class="sxs-lookup"><span data-stu-id="0db9f-178">Let's try to debug an example program that has problems with unloading.</span></span> <span data-ttu-id="0db9f-179">Kaynak kodu, aşağıda yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="0db9f-179">Source code is included below.</span></span> <span data-ttu-id="0db9f-180">WinDbg altında çalıştırdığınızda, programın kaldırma başarı için denetlenecek denemeden sonra hata ayıklayıcı sağındaki keser.</span><span class="sxs-lookup"><span data-stu-id="0db9f-180">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="0db9f-181">Ardından, culprits için arama da başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0db9f-181">You can then start looking for the culprits.</span></span>

<span data-ttu-id="0db9f-182">Aşağıdaki örneklerde SOS komutlarının LLDB UNIX kullanarak hata ayıklama, yüklü olmadığını unutmayın `!` bunları önünde.</span><span class="sxs-lookup"><span data-stu-id="0db9f-182">Note that if you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="0db9f-183">Bu komut tüm nesneleri içeren bir tür adı ile dökümleri `LoaderAllocator` GC yığınında olan.</span><span class="sxs-lookup"><span data-stu-id="0db9f-183">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="0db9f-184">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="0db9f-184">Here is an example:</span></span>

```console
         Address               MT     Size
000002b78000ce40 00007ffadc93a288       48     
000002b78000ceb0 00007ffadc93a218       24     

Statistics:
              MT    Count    TotalSize Class Name
00007ffadc93a218        1           24 System.Reflection.LoaderAllocatorScout
00007ffadc93a288        1           48 System.Reflection.LoaderAllocator
Total 2 objects
```

<span data-ttu-id="0db9f-185">İçinde "istatistikleri:" bölümü altındaki onay `MT` (`MethodTable`) ait `System.Reflection.LoaderAllocator`, biz önem verdiğiniz nesne olduğu.</span><span class="sxs-lookup"><span data-stu-id="0db9f-185">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="0db9f-186">Ardından girişle başında listede bulun `MT` tek eşleştirme ve nesnenin adresini alın.</span><span class="sxs-lookup"><span data-stu-id="0db9f-186">Then in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="0db9f-187">Bu örnekte, "000002b78000ce40" olduğu</span><span class="sxs-lookup"><span data-stu-id="0db9f-187">In our case, it is "000002b78000ce40"</span></span>

<span data-ttu-id="0db9f-188">Biz adresini öğrendiğinize göre `LoaderAllocator` , GC kökleri bulmak için başka bir komuta kullanabileceğiniz nesnesi</span><span class="sxs-lookup"><span data-stu-id="0db9f-188">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots</span></span>

```console
!gcroot -all 0x000002b78000ce40 
```

<span data-ttu-id="0db9f-189">Bu komut zincirini neden nesne başvuruları dökümleri `LoaderAllocator` örneği.</span><span class="sxs-lookup"><span data-stu-id="0db9f-189">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="0db9f-190">Listenin tutan bir varlık kök ile başlar bizim `LoaderAllocator` etkin tutulan bağlantıyı destekliyorsa ve bu nedenle hata ayıklama sorunun temel.</span><span class="sxs-lookup"><span data-stu-id="0db9f-190">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem you're debugging.</span></span> <span data-ttu-id="0db9f-191">Kök yığın yuvası, işlemci kaydı, GC tanıtıcısı veya statik değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-191">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="0db9f-192">İşte bir örnek çıktısı `gcroot` komutu:</span><span class="sxs-lookup"><span data-stu-id="0db9f-192">Here is an example of the output of the `gcroot` command:</span></span>

```console
Thread 4ac:
    000000cf9499dd20 00007ffa7d0236bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
        rbp-20: 000000cf9499dd90
            ->  000002b78000d328 System.Reflection.RuntimeMethodInfo
            ->  000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
            ->  000002b78000d1d0 System.RuntimeType
            ->  000002b78000ce40 System.Reflection.LoaderAllocator

HandleTable:
    000002b7f8a81198 (strong handle)
    -> 000002b78000d948 test.Test
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

    000002b7f8a815f8 (pinned handle)
    -> 000002b790001038 System.Object[]
    -> 000002b78000d390 example.TestInfo
    -> 000002b78000d328 System.Reflection.RuntimeMethodInfo
    -> 000002b78000d1f8 System.RuntimeType+RuntimeTypeCache
    -> 000002b78000d1d0 System.RuntimeType
    -> 000002b78000ce40 System.Reflection.LoaderAllocator

Found 3 roots.
```

<span data-ttu-id="0db9f-193">Şimdi Bunu düzeltmek için kök bulunduğu kullanıma şekil gerekir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-193">Now you need to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="0db9f-194">Kök yığın yuvası ya da bir işlemci kayıt olduğunda kolay durum geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-194">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="0db9f-195">Bu durumda, `gcroot` olan çerçeveyi içeren kök ve bu işlev yürütme iş parçacığı işlevin adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-195">In that case, the `gcroot` shows you the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="0db9f-196">Kök statik bir değişken veya GC tanıtıcı olduğunda zor bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="0db9f-196">The difficult case is when the root is a static variable or a GC handle.</span></span> 

<span data-ttu-id="0db9f-197">Önceki örnekte, ilk kök yerel bir tür olan `System.Reflection.RuntimeMethodInfo` işlevi çerçevede depolanan `example.Program.Main(System.String[])` adresindeki `rbp-20` (`rbp` işlemci kaydıdır `rbp` ve -20 Bu kayıt onaltılık bir uzaklık).</span><span class="sxs-lookup"><span data-stu-id="0db9f-197">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="0db9f-198">İkinci köküdür (güçlü) normal `GCHandle` örneğine bir başvuru tutan `test.Test` sınıfı.</span><span class="sxs-lookup"><span data-stu-id="0db9f-198">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span> 

<span data-ttu-id="0db9f-199">Üçüncü kök sabitlenmiş olan `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="0db9f-199">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="0db9f-200">Bu, aslında bir statik değişken ' dir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-200">This one is actually a static variable.</span></span> <span data-ttu-id="0db9f-201">Ne yazık ki bildirmek için hiçbir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="0db9f-201">Unfortunately, there is no way to tell.</span></span> <span data-ttu-id="0db9f-202">Başvuru türleri için statikler iç çalışma zamanı yapılardaki bir yönetilen nesne dizisindeki depolanır.</span><span class="sxs-lookup"><span data-stu-id="0db9f-202">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="0db9f-203">Yüklemesini kaldırmak engelleyebilecek başka bir örneği bir `AssemblyLoadContext` bir iş parçacığı bir metodun çerçeve sahip olduğunda bir derleme yüklenen `AssemblyLoadContext` , yığında.</span><span class="sxs-lookup"><span data-stu-id="0db9f-203">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="0db9f-204">Yönetilen dökme tüm iş parçacığı yığınları çağırın denetleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="0db9f-204">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="0db9f-205">Komut anlamına gelir "tüm iş parçacıkları için geçerli `!clrstack` komut".</span><span class="sxs-lookup"><span data-stu-id="0db9f-205">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="0db9f-206">Örneğin bu komutun çıktısı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="0db9f-206">The following is the output of that command for the example.</span></span> <span data-ttu-id="0db9f-207">Ne yazık ki LLDB UNIX üzerinde el ile geçiş iş parçacıkları ve yinelenen başvurmadan gerekecek bir komutu tüm iş parçacıkları için uygulamak için herhangi bir şekilde yok `clrstack` komutu.</span><span class="sxs-lookup"><span data-stu-id="0db9f-207">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you'll need to resort to manually switching threads and repeating the `clrstack` command.</span></span>
<span data-ttu-id="0db9f-208">Burada "Yönetilen yığın yol alınamıyor." hata ayıklayıcı'ifadesini içeren tüm iş parçacıklarının yoksay</span><span class="sxs-lookup"><span data-stu-id="0db9f-208">Ignore all threads where the debugger says "Unable to walk the managed stack."</span></span>

```console
OS Thread Id: 0x6ba8 (0)
        Child SP               IP Call Site
0000001fc697d5c8 00007ffb50d9de12 [HelperMethodFrame: 0000001fc697d5c8] System.Diagnostics.Debugger.BreakInternal()
0000001fc697d6d0 00007ffa864765fa System.Diagnostics.Debugger.Break()
0000001fc697d700 00007ffa864736bc example.Program.Main(System.String[]) [E:\unloadability\example\Program.cs @ 70]
0000001fc697d998 00007ffae5fdc1e3 [GCFrame: 0000001fc697d998] 
0000001fc697df28 00007ffae5fdc1e3 [GCFrame: 0000001fc697df28] 
OS Thread Id: 0x2ae4 (1)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x61a4 (2)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x7fdc (3)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5390 (4)
Unable to walk the managed stack. The current thread is likely not a 
managed thread. You can run !threads to get a list of managed threads in
the process
Failed to start stack walk: 80070057
OS Thread Id: 0x5ec8 (5)
        Child SP               IP Call Site
0000001fc70ff6e0 00007ffb5437f6e4 [DebuggerU2MCatchHandlerFrame: 0000001fc70ff6e0] 
OS Thread Id: 0x4624 (6)
        Child SP               IP Call Site
GetFrameContext failed: 1
0000000000000000 0000000000000000 
OS Thread Id: 0x60bc (7)
        Child SP               IP Call Site
0000001fc727f158 00007ffb5437fce4 [HelperMethodFrame: 0000001fc727f158] System.Threading.Thread.SleepInternal(Int32)
0000001fc727f260 00007ffb37ea7c2b System.Threading.Thread.Sleep(Int32)
0000001fc727f290 00007ffa865005b3 test.Program.ThreadProc() [E:\unloadability\test\Program.cs @ 17]
0000001fc727f2c0 00007ffb37ea6a5b System.Threading.Thread.ThreadMain_ThreadStart()
0000001fc727f2f0 00007ffadbc4cbe3 System.Threading.ExecutionContext.RunInternal(System.Threading.ExecutionContext, System.Threading.ContextCallback, System.Object)
0000001fc727f568 00007ffae5fdc1e3 [GCFrame: 0000001fc727f568] 
0000001fc727f7f0 00007ffae5fdc1e3 [DebuggerU2MCatchHandlerFrame: 0000001fc727f7f0] 

```

<span data-ttu-id="0db9f-209">Gördüğünüz gibi son iş parçacığı vardır `test.Program.ThreadProc()`.</span><span class="sxs-lookup"><span data-stu-id="0db9f-209">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="0db9f-210">Bu derlemeden yüklenen işlevdir `AssemblyLoadContext`, ve sürdürür böylece `AssemblyLoadContext` tutma.</span><span class="sxs-lookup"><span data-stu-id="0db9f-210">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="0db9f-211">Örnek kaynak unloadability sorunları</span><span class="sxs-lookup"><span data-stu-id="0db9f-211">Example source with unloadability issues</span></span>

<span data-ttu-id="0db9f-212">Aşağıdaki kod, önceki örnekte hata ayıklama kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0db9f-212">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="0db9f-213">Test ana program</span><span class="sxs-lookup"><span data-stu-id="0db9f-213">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="0db9f-214">Program TestAssemblyLoadContext yüklendi</span><span class="sxs-lookup"><span data-stu-id="0db9f-214">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="0db9f-215">Aşağıdaki kod temsil `test.dll` geçirilen `ExecuteAndUnload` test eden ana program yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0db9f-215">The following code represents the `test.dll` passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
