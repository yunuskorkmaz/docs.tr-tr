---
title: .NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama
description: Yönetilen derlemeleri yüklemek ve kaldırmak için toplanabilir bir AssemblyLoadContext ve kaldırma başarısını önlemek için sorunları nasıl ayıklayacağınız hakkında bilgi edinin.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159747"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="870fd-103">.NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="870fd-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="870fd-104">.NET Core 3,0 ile başlayarak, bir derleme kümesini yükleme ve daha sonra kaldırma özelliği desteklenir.</span><span class="sxs-lookup"><span data-stu-id="870fd-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="870fd-105">.NET Framework, bu amaçla özel uygulama etki alanları kullanılmıştır, ancak .NET Core yalnızca tek bir varsayılan uygulama etki alanını destekler.</span><span class="sxs-lookup"><span data-stu-id="870fd-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="870fd-106">.NET Core 3,0 ve sonraki sürümleri, <xref:System.Runtime.Loader.AssemblyLoadContext>aracılığıyla bir unkullanılabilirliği destekler.</span><span class="sxs-lookup"><span data-stu-id="870fd-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="870fd-107">Bir dizi derlemeyi toplanabilir bir `AssemblyLoadContext`yükleyebilir, bunlarda Yöntemler yürütebilir veya yansıma kullanarak bunları inceleyebilirsiniz, son olarak da `AssemblyLoadContext`kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="870fd-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="870fd-108">Bu, `AssemblyLoadContext`yüklenen derlemeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="870fd-108">That unloads the assemblies loaded into the `AssemblyLoadContext`.</span></span>

<span data-ttu-id="870fd-109">`AssemblyLoadContext` kullanarak ve AppDomain kullanarak kaldırma arasında bir çok fark vardır.</span><span class="sxs-lookup"><span data-stu-id="870fd-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="870fd-110">AppDomain ile, kaldırma zorlanır.</span><span class="sxs-lookup"><span data-stu-id="870fd-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="870fd-111">Kaldırma sırasında, hedef AppDomain 'de çalışan tüm iş parçacıkları iptal edilir, hedef AppDomain 'te oluşturulan yönetilen COM nesneleri yok edilir ve bu şekilde devam eder.</span><span class="sxs-lookup"><span data-stu-id="870fd-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, and so on.</span></span> <span data-ttu-id="870fd-112">`AssemblyLoadContext`, kaldırma "işbirliği" dir.</span><span class="sxs-lookup"><span data-stu-id="870fd-112">With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="870fd-113"><xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> yöntemini çağırmak, kaldırmayı yalnızca başlatır.</span><span class="sxs-lookup"><span data-stu-id="870fd-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="870fd-114">Kaldırma işlemi şu tarihten sonra bitiyor:</span><span class="sxs-lookup"><span data-stu-id="870fd-114">The unloading finishes after:</span></span>

- <span data-ttu-id="870fd-115">Hiçbir iş parçacığı, çağrı yığınlarında `AssemblyLoadContext` yüklenen derlemelerden yöntemlere sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="870fd-115">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="870fd-116">`AssemblyLoadContext`yüklenmeyen derlemelerden türlerin hiçbiri, bu türlerin örneklerine ve derlemelerin kendileri tarafından başvuruluyor:</span><span class="sxs-lookup"><span data-stu-id="870fd-116">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types, and the assemblies themselves are referenced by:</span></span>
  - <span data-ttu-id="870fd-117">Zayıf başvurular (<xref:System.WeakReference> veya <xref:System.WeakReference%601>) dışında `AssemblyLoadContext`dışında başvurular.</span><span class="sxs-lookup"><span data-stu-id="870fd-117">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="870fd-118">`AssemblyLoadContext`içindeki ve dışındaki güçlü çöp toplayıcı (GC) tutamaçları ([GCHandleType. normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) veya [GCHandleType. sabitlenmiş](xref:System.Runtime.InteropServices.GCHandleType.Pinned)).</span><span class="sxs-lookup"><span data-stu-id="870fd-118">Strong garbage collector (GC) handles ([GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) or [GCHandleType.Pinned](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="870fd-119">Toplanabilir AssemblyLoadContext kullanın</span><span class="sxs-lookup"><span data-stu-id="870fd-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="870fd-120">Bu bölümde, bir .NET Core uygulamasını toplanabilir bir `AssemblyLoadContext`yüklemek, giriş noktasını yürütmek ve sonra kaldırmak için kullanabileceğiniz basit bir yol gösteren ayrıntılı bir adım adım öğretici yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="870fd-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="870fd-121">[https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)' de tüm bir örnek bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="870fd-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="870fd-122">Toplanabilir bir AssemblyLoadContext oluşturma</span><span class="sxs-lookup"><span data-stu-id="870fd-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="870fd-123"><xref:System.Runtime.Loader.AssemblyLoadContext> sınıfınızı türetmeniz ve <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metodunu aşırı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="870fd-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="870fd-124">Bu yöntem, bu `AssemblyLoadContext`yüklenen derlemelerin bağımlılıkları olan tüm derlemelere yönelik başvuruları çözer.</span><span class="sxs-lookup"><span data-stu-id="870fd-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="870fd-125">Aşağıdaki kod, en basit özel `AssemblyLoadContext`örneğidir:</span><span class="sxs-lookup"><span data-stu-id="870fd-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="870fd-126">Gördüğünüz gibi `Load` yöntemi `null`döndürür.</span><span class="sxs-lookup"><span data-stu-id="870fd-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="870fd-127">Bu, tüm bağımlılık derlemelerinin varsayılan bağlamına yüklendiği ve yeni bağlamın yalnızca açıkça kendisine yüklenmiş derlemeleri içerdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="870fd-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="870fd-128">Bağımlılıkların bir kısmını veya tümünü `AssemblyLoadContext` yüklemek istiyorsanız, `Load` yönteminde `AssemblyDependencyResolver` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="870fd-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="870fd-129">`AssemblyDependencyResolver`, derleme adlarını mutlak derleme dosyası yollarına çözümler.</span><span class="sxs-lookup"><span data-stu-id="870fd-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths.</span></span> <span data-ttu-id="870fd-130">Çözümleyici, bağlamına yüklenen ana derlemenin dizinindeki *. Deps. JSON* dosyasını ve derleme dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="870fd-130">The resolver uses the *.deps.json* file and assembly files in the directory of the main assembly loaded into the context.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="870fd-131">Özel toplanabilir bir AssemblyLoadContext kullanın</span><span class="sxs-lookup"><span data-stu-id="870fd-131">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="870fd-132">Bu bölüm `TestAssemblyLoadContext` 'in daha basit sürümünün kullanıldığını varsayar.</span><span class="sxs-lookup"><span data-stu-id="870fd-132">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="870fd-133">Özel `AssemblyLoadContext` bir örneğini oluşturabilir ve buna aşağıdaki gibi bir derlemeyi yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="870fd-133">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="870fd-134">Yüklenen derleme tarafından başvurulan derlemelerin her biri için `TestAssemblyLoadContext.Load` yöntemi, `TestAssemblyLoadContext` derlemenin nereden alınacağını seçebilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-134">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="870fd-135">Bizim örneğimizde, varsayılan olarak çalışma zamanının derlemeleri yüklemek için kullandığı konumlardan varsayılan bağlamına yüklenmesi gerektiğini göstermek için `null` döndürür.</span><span class="sxs-lookup"><span data-stu-id="870fd-135">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="870fd-136">Bir derleme yüklendikten sonra, bundan sonra bir yöntemi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="870fd-136">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="870fd-137">`Main` yöntemini çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="870fd-137">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="870fd-138">`Main` yöntemi çağrıldıktan sonra, özel `AssemblyLoadContext` `Unload` yöntemini çağırarak veya `AssemblyLoadContext`sahip olduğunuz başvurunun kurtumı aracılığıyla kaldırma işlemini başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="870fd-138">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="870fd-139">Bu, test derlemesini kaldırmak için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="870fd-139">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="870fd-140">`TestAssemblyLoadContext`, `Assembly`ve `MethodInfo` (`Assembly.EntryPoint`) yığın yuvası başvuruları (gerçek veya JıT tarafından tanıtılan Yereller) tarafından etkin tutulabileceğinden emin olmak için bunu tamamen ayrı bir bağımsız olmayan yönteme koyalım.</span><span class="sxs-lookup"><span data-stu-id="870fd-140">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="870fd-141">Bu, `TestAssemblyLoadContext` canlı tutabilir ve kaldırma özelliğini engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-141">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="870fd-142">Ayrıca, daha sonra kaldırma tamamlamayı algılamak üzere kullanabilmek için `AssemblyLoadContext` zayıf bir başvuru döndürün.</span><span class="sxs-lookup"><span data-stu-id="870fd-142">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="870fd-143">Artık derlemeyi yüklemek, çalıştırmak ve kaldırmak için bu işlevi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="870fd-143">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="870fd-144">Ancak, kaldırma hemen tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="870fd-144">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="870fd-145">Daha önce belirtildiği gibi, tüm nesneleri test derlemesinden toplamak için çöp toplayıcıyı kullanır.</span><span class="sxs-lookup"><span data-stu-id="870fd-145">As previously mentioned, it relies on the garbage collector to collect all the objects from the test assembly.</span></span> <span data-ttu-id="870fd-146">Çoğu durumda, kaldırma işleminin tamamlanmasını beklemek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="870fd-146">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="870fd-147">Ancak, kaldırma işlemi bittiğini bilmemiz yararlı olduğu durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="870fd-147">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="870fd-148">Örneğin, diskten özel `AssemblyLoadContext` yüklenen derleme dosyasını silmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="870fd-148">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="870fd-149">Böyle bir durumda, aşağıdaki kod parçacığı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-149">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="870fd-150">Çöp toplamayı tetikler ve özel `AssemblyLoadContext` zayıf başvurusu, hedef nesnenin toplandığını belirten `null`olarak ayarlanana kadar bir döngüde bekleyen sonlandırıcıları bekler.</span><span class="sxs-lookup"><span data-stu-id="870fd-150">It triggers garbage collection and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="870fd-151">Çoğu durumda, yalnızca bir geçiş döngüsü gerekir.</span><span class="sxs-lookup"><span data-stu-id="870fd-151">In most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="870fd-152">Ancak, `AssemblyLoadContext` çalışan kod tarafından oluşturulan nesnelerin sonlandırıcılarda olduğu daha karmaşık durumlarda daha fazla geçiş gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-152">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="870fd-153">Kaldırma olayı</span><span class="sxs-lookup"><span data-stu-id="870fd-153">The Unloading event</span></span>

<span data-ttu-id="870fd-154">Bazı durumlarda, kaldırma işlemi başlatıldığında bazı temizleme işlemleri gerçekleştirmek için özel bir `AssemblyLoadContext` yüklenen kod için gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-154">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="870fd-155">Örneğin, iş parçacıklarını durdurmanız veya güçlü GC tutamaçları temizlemesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-155">For example, it may need to stop threads or clean up strong GC handles.</span></span> <span data-ttu-id="870fd-156">`Unloading` olay bu gibi durumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-156">The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="870fd-157">Gerekli temizleme işlemini gerçekleştiren bir işleyici bu olaya bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-157">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="870fd-158">Kaldırma sorunları sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="870fd-158">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="870fd-159">Boşaltma 'nın işbirliğinin doğası gereği, bir toplanabilir `AssemblyLoadContext` canlı bir şekilde korunmuş ve kaldırma işlemini engellediği başvuruları unutmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="870fd-159">Due to the cooperative nature of the unloading, it's easy to forget about references that may be keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="870fd-160">Aşağıda, başvuruları tutabilecek varlıkların (bazı belirgin olmayan) bir özeti verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="870fd-160">Here is a summary of entities (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="870fd-161">Bir yığın yuvasında veya bir işlemci kaydındaki (Kullanıcı kodu tarafından açıkça oluşturulan veya örtük olarak tam zamanında (JıT) derleyici), statik bir değişken ya da güçlü (sabitleme) bir GC tutamacı veya bir güçlü (sabitleme) `AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="870fd-161">Regular references held from outside of the collectible `AssemblyLoadContext` that are stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the just-in-time (JIT) compiler), a static variable, or a strong (pinning) GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="870fd-162">Toplanabilir `AssemblyLoadContext`yüklenmiş bir bütünleştirilmiş kod.</span><span class="sxs-lookup"><span data-stu-id="870fd-162">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="870fd-163">Bu tür bir derlemeden bir tür.</span><span class="sxs-lookup"><span data-stu-id="870fd-163">A type from such an assembly.</span></span>
  - <span data-ttu-id="870fd-164">Bu tür bir derlemeden bir türün örneği.</span><span class="sxs-lookup"><span data-stu-id="870fd-164">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="870fd-165">Toplanabilir `AssemblyLoadContext`yüklenmiş bir derlemeden kod çalıştıran iş parçacıkları.</span><span class="sxs-lookup"><span data-stu-id="870fd-165">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="870fd-166">Toplanabilir `AssemblyLoadContext`içinde oluşturulan özel, toplanabilir olmayan `AssemblyLoadContext` türlerinin örnekleri.</span><span class="sxs-lookup"><span data-stu-id="870fd-166">Instances of custom, non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="870fd-167">Geri çağırmalar içeren <xref:System.Threading.RegisteredWaitHandle> örnekleri, özel `AssemblyLoadContext`metotlar olarak ayarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="870fd-167">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`.</span></span>

> [!TIP]
> <span data-ttu-id="870fd-168">Yığın yuvaları veya işlemci kayıtları 'nda depolanan ve bir `AssemblyLoadContext` kaldırılmasını engelleyebilecek nesne başvuruları aşağıdaki durumlarda oluşabilir:</span><span class="sxs-lookup"><span data-stu-id="870fd-168">Object references that are stored in stack slots or processor registers and that could prevent unloading of an `AssemblyLoadContext` can occur in the following situations:</span></span>
>
> - <span data-ttu-id="870fd-169">İşlev çağırma sonuçları, Kullanıcı tarafından oluşturulan yerel değişken olmasa bile, doğrudan başka bir işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-169">When function call results are passed directly to another function, even though there is no user-created local variable.</span></span>
> - <span data-ttu-id="870fd-170">JıT derleyicisi, bir yöntemde bir noktada kullanılabilir olan bir nesneye bir başvuru tutar.</span><span class="sxs-lookup"><span data-stu-id="870fd-170">When the JIT compiler keeps a reference to an object that was available at some point in a method.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="870fd-171">Hata ayıklama kaldırma sorunları</span><span class="sxs-lookup"><span data-stu-id="870fd-171">Debug unloading issues</span></span>

<span data-ttu-id="870fd-172">Kaldırma ile ilgili hata ayıklama sorunları sıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-172">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="870fd-173">`AssemblyLoadContext` canlı olarak neler yapabileceğini bildiğiniz durumlara ulaşabilirsiniz, ancak kaldırma başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="870fd-173">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span> <span data-ttu-id="870fd-174">Bu, sos eklentisi ile WinDbg (UNIX üzerinde lldb) ile ilgili yardım için en iyi uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="870fd-174">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="870fd-175">Belirli `AssemblyLoadContext` canlı olan `LoaderAllocator` tutmayı bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="870fd-175">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span> <span data-ttu-id="870fd-176">SOS eklentisi, GC yığın nesnelerine, hiyerarşilerine ve köklerine bakabilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="870fd-176">The SOS plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>

<span data-ttu-id="870fd-177">Eklentiyi hata ayıklayıcıya yüklemek için, hata ayıklayıcı komut satırına aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="870fd-177">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="870fd-178">WinDbg 'de (.NET Core uygulamasına bölünmediği zaman, WinDbg olarak görünür):</span><span class="sxs-lookup"><span data-stu-id="870fd-178">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="870fd-179">LLDB 'de:</span><span class="sxs-lookup"><span data-stu-id="870fd-179">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="870fd-180">Daha sonra, kaldırma sorunları olan bir örnek programda hata ayıklaması yapmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="870fd-180">Let's debug an example program that has problems with unloading.</span></span> <span data-ttu-id="870fd-181">Kaynak kodu aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="870fd-181">Source code is included below.</span></span> <span data-ttu-id="870fd-182">Bunu WinDbg altında çalıştırdığınızda, program, kaldırma başarısını denetlemeye çalıştıktan sonra hata ayıklayıcıya hemen sonra sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="870fd-182">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="870fd-183">Daha sonra Bu küller için aramaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="870fd-183">You can then start looking for the culprits.</span></span>

> [!TIP]
> <span data-ttu-id="870fd-184">UNIX üzerinde LLDB kullanarak hata ayıklaması yaparsanız, aşağıdaki örneklerde yer alan SOS komutlarının önünde `!` yoktur.</span><span class="sxs-lookup"><span data-stu-id="870fd-184">If you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="870fd-185">Bu komut, GC yığınındaki `LoaderAllocator` içeren bir tür adına sahip tüm nesneleri döker.</span><span class="sxs-lookup"><span data-stu-id="870fd-185">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="870fd-186">Örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="870fd-186">Here is an example:</span></span>

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

<span data-ttu-id="870fd-187">Aşağıdaki "Istatistikler:" bölümünde, ilgilendiğimiz nesne olan `System.Reflection.LoaderAllocator`ait `MT` (`MethodTable`) kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="870fd-187">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="870fd-188">Ardından, başındaki listede, kendisiyle eşleşen `MT` olan girdiyi bulun ve nesnenin adresini alın.</span><span class="sxs-lookup"><span data-stu-id="870fd-188">Then, in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="870fd-189">Bu durumda, "000002b78000ce40" olur.</span><span class="sxs-lookup"><span data-stu-id="870fd-189">In our case, it is "000002b78000ce40".</span></span>

<span data-ttu-id="870fd-190">Artık `LoaderAllocator` nesnesinin adresini öğrendiğimiz için, GC köklerinin bulmak için başka bir komut de kullanabiliriz:</span><span class="sxs-lookup"><span data-stu-id="870fd-190">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots:</span></span>

```console
!gcroot -all 0x000002b78000ce40
```

<span data-ttu-id="870fd-191">Bu komut, `LoaderAllocator` örneğine yol açabilecek nesne başvuruları zincirini döker.</span><span class="sxs-lookup"><span data-stu-id="870fd-191">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="870fd-192">Liste, `LoaderAllocator` etkin tutan ve bu nedenle sorunun temel aldığı varlık olan kökle başlar.</span><span class="sxs-lookup"><span data-stu-id="870fd-192">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem.</span></span> <span data-ttu-id="870fd-193">Kök bir yığın yuvası, bir işlemci kaydı, bir GC tanıtıcısı veya statik değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-193">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="870fd-194">`gcroot` komutunun çıktısının bir örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="870fd-194">Here is an example of the output of the `gcroot` command:</span></span>

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

<span data-ttu-id="870fd-195">Sonraki adım, kökün nerede olduğunu anlamak için, onu düzeltemedi.</span><span class="sxs-lookup"><span data-stu-id="870fd-195">The next step is to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="870fd-196">En kolay durum, kök bir yığın yuvası veya bir işlemci kaydı olduğunda olur.</span><span class="sxs-lookup"><span data-stu-id="870fd-196">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="870fd-197">Bu durumda `gcroot`, çerçevesi kök içeren ve bu işlevi yürüten iş parçacığı olan işlevin adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="870fd-197">In that case, the `gcroot` shows the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="870fd-198">Zor durum, kökün bir statik değişken veya bir GC tutamacı olması durumunda olur.</span><span class="sxs-lookup"><span data-stu-id="870fd-198">The difficult case is when the root is a static variable or a GC handle.</span></span>

<span data-ttu-id="870fd-199">Önceki örnekte, ilk kök, `System.Reflection.RuntimeMethodInfo` `example.Program.Main(System.String[])` işlevin çerçevesinde depolanan bir tür yereldir `rbp-20` (`rbp`, işlemci yazmacı `rbp` ve-20 Bu kaydın onaltılık bir uzaklığında oluşur).</span><span class="sxs-lookup"><span data-stu-id="870fd-199">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="870fd-200">İkinci kök, `test.Test` sınıfının bir örneğine başvuru tutan bir normal (güçlü) `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="870fd-200">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span>

<span data-ttu-id="870fd-201">Üçüncü kök sabitlenmiş bir `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="870fd-201">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="870fd-202">Bu, aslında statik bir değişkendir, ancak ne yazık ki, söylemek için bir yol yoktur.</span><span class="sxs-lookup"><span data-stu-id="870fd-202">This one is actually a static variable, but unfortunately, there is no way to tell.</span></span> <span data-ttu-id="870fd-203">Başvuru türleri için statiği, iç çalışma zamanı yapılarında yönetilen nesne dizisinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="870fd-203">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="870fd-204">Bir `AssemblyLoadContext` kaldırılmasını engelleyebilecek başka bir durum, bir iş parçacığı, yığınında `AssemblyLoadContext` yüklenen bir derlemeden bir yöntem çerçevesine sahip olduğunda olabilir.</span><span class="sxs-lookup"><span data-stu-id="870fd-204">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="870fd-205">Tüm iş parçacıklarının yönetilen çağrı yığınlarının dökümünü yaparak bunu kontrol edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="870fd-205">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="870fd-206">Komutu, "`!clrstack` komutuna tüm iş parçacıkları için geçerlidir" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="870fd-206">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="870fd-207">Örnek için bu komutun çıktısı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="870fd-207">The following is the output of that command for the example.</span></span> <span data-ttu-id="870fd-208">Ne yazık ki, UNIX üzerinde LLDB, tüm iş parçacıklarına komut uygulamak için herhangi bir yola sahip değildir, bu nedenle iş parçacıklarını el ile geçmeniz ve `clrstack` komutunu tekrarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="870fd-208">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you must manually switch threads and repeat the `clrstack` command.</span></span> <span data-ttu-id="870fd-209">Hata ayıklayıcının "yönetilen yığında ilerleme yapılamıyor" ifadesini belirten tüm iş parçacıklarını yoksayın.</span><span class="sxs-lookup"><span data-stu-id="870fd-209">Ignore all threads where the debugger says "Unable to walk the managed stack".</span></span>

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

<span data-ttu-id="870fd-210">Gördüğünüz gibi, son iş parçacığında `test.Program.ThreadProc()`vardır.</span><span class="sxs-lookup"><span data-stu-id="870fd-210">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="870fd-211">Bu, `AssemblyLoadContext`yüklenen derlemeden bir işlevdir ve `AssemblyLoadContext` canlı tutar.</span><span class="sxs-lookup"><span data-stu-id="870fd-211">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="870fd-212">Loadability sorunları olan örnek kaynak</span><span class="sxs-lookup"><span data-stu-id="870fd-212">Example source with unloadability issues</span></span>

<span data-ttu-id="870fd-213">Aşağıdaki kod, önceki hata ayıklama örneğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="870fd-213">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="870fd-214">Ana test programı</span><span class="sxs-lookup"><span data-stu-id="870fd-214">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="870fd-215">TestAssemblyLoadContext içine yüklenen program</span><span class="sxs-lookup"><span data-stu-id="870fd-215">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="870fd-216">Aşağıdaki kod, ana test programındaki `ExecuteAndUnload` metoduna geçirilen *test. dll dosyasını* temsil eder.</span><span class="sxs-lookup"><span data-stu-id="870fd-216">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
