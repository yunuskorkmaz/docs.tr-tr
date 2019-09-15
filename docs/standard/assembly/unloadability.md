---
title: .NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama
description: Yönetilen derlemeleri yüklemek ve kaldırmak için toplanabilir bir AssemblyLoadContext ve kaldırma başarısını önlemek için sorunları nasıl ayıklayacağınız hakkında bilgi edinin.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 52cd864393342e2bc31f872b9d09cb484c2c8463
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2019
ms.locfileid: "70972993"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="fe537-103">.NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="fe537-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="fe537-104">.NET Core 3,0 ile başlayarak, bir derleme kümesini yükleme ve daha sonra kaldırma özelliği desteklenir.</span><span class="sxs-lookup"><span data-stu-id="fe537-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="fe537-105">.NET Framework, bu amaçla özel uygulama etki alanları kullanılmıştır, ancak .NET Core yalnızca tek bir varsayılan uygulama etki alanını destekler.</span><span class="sxs-lookup"><span data-stu-id="fe537-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="fe537-106">.NET Core 3,0 ve sonraki sürümleri, aracılığıyla <xref:System.Runtime.Loader.AssemblyLoadContext>tasbilirliğini destekler.</span><span class="sxs-lookup"><span data-stu-id="fe537-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="fe537-107">Bir dizi derlemeyi toplanabilir `AssemblyLoadContext`bir şekilde yükleyebilir, bunlarda Yöntemler yürütebilir veya yansıma kullanarak bunları inceleyebilirsiniz, son olarak `AssemblyLoadContext`yüklemesini kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe537-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="fe537-108">Bu, yüklenmiş `AssemblyLoadContext`derlemeleri kaldırır.</span><span class="sxs-lookup"><span data-stu-id="fe537-108">That unloads the assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="fe537-109">Uygulama etki alanları kullanarak `AssemblyLoadContext` ve kullanarak kaldırma arasında bir sorun olduğunu fark eden bir farklılık vardır.</span><span class="sxs-lookup"><span data-stu-id="fe537-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="fe537-110">AppDomain ile, kaldırma zorlanır.</span><span class="sxs-lookup"><span data-stu-id="fe537-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="fe537-111">Kaldırma sırasında, hedef AppDomain 'de çalışan tüm iş parçacıkları iptal edilir, hedef AppDomain 'de oluşturulan yönetilen COM nesneleri yok edilir vb. İle `AssemblyLoadContext`, kaldırma "işbirliği" dir.</span><span class="sxs-lookup"><span data-stu-id="fe537-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, etc. With `AssemblyLoadContext`, the unload is "cooperative."</span></span> <span data-ttu-id="fe537-112"><xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> Yöntemi çağırmak yalnızca kaldırma işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="fe537-112">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="fe537-113">Kaldırma işlemi şu tarihten sonra bitiyor:</span><span class="sxs-lookup"><span data-stu-id="fe537-113">The unloading finishes after:</span></span>

- <span data-ttu-id="fe537-114">Hiçbir iş parçacığı, `AssemblyLoadContext` çağrı yığınlarında öğesine yüklenen derlemelerden yöntemlere sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="fe537-114">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="fe537-115">İçinde `AssemblyLoadContext`yüklü derlemelerden hiçbir türden hiçbirisi, bu türlerin örneklerine ve kendi dışındaki `AssemblyLoadContext` derlemelere şunun tarafından başvuruluyor:</span><span class="sxs-lookup"><span data-stu-id="fe537-115">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types and the assemblies themselves outside of the `AssemblyLoadContext` are referenced by:</span></span>
  - <span data-ttu-id="fe537-116">Zayıf başvurular haricinde ( `AssemblyLoadContext`<xref:System.WeakReference> veya <xref:System.WeakReference%601>) dışında başvuruları.</span><span class="sxs-lookup"><span data-stu-id="fe537-116">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="fe537-117">Güçlü GC tutamaçları (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span><span class="sxs-lookup"><span data-stu-id="fe537-117">Strong GC handles (<xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Normal></span></span> <span data-ttu-id="fe537-118">ya <xref:System.Runtime.InteropServices.GCHandleType>da<xref:System.Runtime.InteropServices.GCHandleType.Pinned>.), `AssemblyLoadContext`hem içinde hem de dışında.</span><span class="sxs-lookup"><span data-stu-id="fe537-118">or <xref:System.Runtime.InteropServices.GCHandleType>.<xref:System.Runtime.InteropServices.GCHandleType.Pinned>) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="fe537-119">Toplanabilir AssemblyLoadContext kullanın</span><span class="sxs-lookup"><span data-stu-id="fe537-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="fe537-120">Bu bölüm `AssemblyLoadContext`, bir .NET Core uygulamasını toplanabilir bir şekilde yüklemek, giriş noktasını yürütmek ve sonra kaldırmak için basit bir yol gösteren ayrıntılı bir adım adım öğretici içerir.</span><span class="sxs-lookup"><span data-stu-id="fe537-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="fe537-121">' De tüm bir örnek [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe537-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="fe537-122">Toplanabilir bir AssemblyLoadContext oluşturma</span><span class="sxs-lookup"><span data-stu-id="fe537-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="fe537-123">Sınıfından sınıfınızı <xref:System.Runtime.Loader.AssemblyLoadContext> türetmeniz ve <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> metodunu aşırı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe537-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fe537-124">Bu yöntem, yüklenmiş `AssemblyLoadContext`derlemelerin bağımlılıkları olan tüm derlemelere başvuruları çözümler.</span><span class="sxs-lookup"><span data-stu-id="fe537-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>
<span data-ttu-id="fe537-125">Aşağıdaki kod, en basit özel `AssemblyLoadContext`örneğine bir örnektir:</span><span class="sxs-lookup"><span data-stu-id="fe537-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="fe537-126">Gördüğünüz gibi, `Load` yöntemi döndürür `null`.</span><span class="sxs-lookup"><span data-stu-id="fe537-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="fe537-127">Bu, tüm bağımlılık derlemelerinin varsayılan bağlamına yüklendiği ve yeni bağlamın yalnızca açıkça kendisine yüklenmiş derlemeleri içerdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fe537-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="fe537-128">Bağımlılıkların `AssemblyLoadContext` bir kısmını veya tümünü de yüklemek istiyorsanız, `Load` yöntemi `AssemblyDependencyResolver` içinde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe537-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="fe537-129">, `AssemblyDependencyResolver` Derleme adlarını, bağlam içine yüklenen ana derlemenin dizininde bulunan *. Deps. JSON* dosyasını ve bu dizindeki derleme dosyalarını kullanarak mutlak derleme dosya yollarına dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="fe537-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths using the *.deps.json* file contained in the directory of the main assembly loaded into the context and using assembly files in that directory.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="fe537-130">Özel toplanabilir bir AssemblyLoadContext kullanın</span><span class="sxs-lookup"><span data-stu-id="fe537-130">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="fe537-131">Bu bölümde, öğesinin `TestAssemblyLoadContext` daha basit sürümünün kullanıldığını varsayılır.</span><span class="sxs-lookup"><span data-stu-id="fe537-131">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="fe537-132">Özel `AssemblyLoadContext` bir örneği oluşturabilir ve bunu aşağıdaki gibi bir derlemeyi yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fe537-132">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="fe537-133">Yüklenen derleme `TestAssemblyLoadContext.Load` tarafından başvurulan derlemelerin her biri için yöntemi çağrılır, böylece, `TestAssemblyLoadContext` derlemenin nereden alınacağını karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="fe537-133">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="fe537-134">Bizim örneğimizde, varsayılan olarak `null` çalışma zamanının derlemeleri yüklemek için kullandığı konumlardan varsayılan bağlamına yüklenmesi gerektiğini göstermek için döndürür.</span><span class="sxs-lookup"><span data-stu-id="fe537-134">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="fe537-135">Bir derleme yüklendikten sonra, bundan sonra bir yöntemi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe537-135">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="fe537-136">`Main` Yöntemi çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="fe537-136">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="fe537-137">Yöntem çağrıldıktan sonra, `Unload` yöntemi özel `AssemblyLoadContext` üzerinde çağırarak veya bir başvuruya sahip olduğunuz başvurunun `AssemblyLoadContext`kurtumı aracılığıyla kaldırmayı başlatabilirsiniz. `Main`</span><span class="sxs-lookup"><span data-stu-id="fe537-137">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="fe537-138">Bu, test derlemesini kaldırmak için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="fe537-138">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="fe537-139">`TestAssemblyLoadContext`, ,Ve`MethodInfo` ( )`Assembly.EntryPoint`öğesinin yığın yuvası başvuruları (gerçek veya JIT tarafından tanıtılan Yereller) tarafından etkin tutulmasını gerektirmediğinden emin olmak için bunu tamamen ayrı bir bağımsız olmayan yönteme yerleştirelim `Assembly`.</span><span class="sxs-lookup"><span data-stu-id="fe537-139">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="fe537-140">Bu, `TestAssemblyLoadContext` canlı kalmasını sağlayabilir ve kaldırma özelliğini engelleyebilir.</span><span class="sxs-lookup"><span data-stu-id="fe537-140">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="fe537-141">Ayrıca, daha sonra kaldırma tamamlamayı algılamak için `AssemblyLoadContext` kullanabilmeniz için zayıf bir başvuru döndürün.</span><span class="sxs-lookup"><span data-stu-id="fe537-141">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="fe537-142">Artık derlemeyi yüklemek, çalıştırmak ve kaldırmak için bu işlevi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe537-142">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="fe537-143">Ancak, kaldırma hemen tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="fe537-143">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="fe537-144">Daha önce belirtildiği gibi, test derlemesindeki tüm nesneleri toplamak için GC 'yi kullanır.</span><span class="sxs-lookup"><span data-stu-id="fe537-144">As previously mentioned, it relies on the GC to collect all the objects from the test assembly.</span></span> <span data-ttu-id="fe537-145">Çoğu durumda, kaldırma işleminin tamamlanmasını beklemek gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="fe537-145">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="fe537-146">Ancak, kaldırma işlemi bittiğini bilmemiz yararlı olduğu durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="fe537-146">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="fe537-147">Örneğin, diskten özel `AssemblyLoadContext` olarak yüklenen derleme dosyasını silmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe537-147">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="fe537-148">Böyle bir durumda, aşağıdaki kod parçacığı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe537-148">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="fe537-149">Bir GC tetikleyip, özel `AssemblyLoadContext` 'e yönelik zayıf başvuru olarak `null`, hedef nesnenin toplandığını belirten bir döngüde bekleyen sonlandırıcıları bekler.</span><span class="sxs-lookup"><span data-stu-id="fe537-149">It triggers a GC and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="fe537-150">Çoğu durumda döngünün yalnızca bir geçişinin gerekli olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="fe537-150">Note that in most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="fe537-151">Bununla birlikte, içinde `AssemblyLoadContext` çalışan kod tarafından oluşturulan nesnelerin sonlandırıcılarda olduğu daha karmaşık durumlarda daha fazla geçiş gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="fe537-151">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="fe537-152">Kaldırma olayı</span><span class="sxs-lookup"><span data-stu-id="fe537-152">The Unloading event</span></span>

<span data-ttu-id="fe537-153">Bazı durumlarda, kaldırma işlemi başlatıldığında bir özel `AssemblyLoadContext` öğesine yüklenen kodun bazı temizleme işlemleri gerçekleştirmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="fe537-153">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="fe537-154">Örneğin, iş parçacıklarını durdurmalı, bazı güçlü GC tutamaçlarını temizleyebiliyor. `Unloading` Olay bu gibi durumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="fe537-154">For example, it may need to stop threads, clean up some strong GC handles, etc. The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="fe537-155">Gerekli temizleme işlemini gerçekleştiren bir işleyici bu olaya bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="fe537-155">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="fe537-156">Kaldırma sorunları sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="fe537-156">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="fe537-157">Boşaltma 'nın işbirliksel doğası nedeniyle, verileri toplanabilir `AssemblyLoadContext` bir şekilde tutmanın ve kaldırma işlemini engellediği başvuruların hakkında unutmak çok kolay.</span><span class="sxs-lookup"><span data-stu-id="fe537-157">Due to the cooperative nature of the unloading, it's easy to forget about references keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="fe537-158">Bu, başvuruları tutabilecek öğelerin (bazı belirgin olmayan) bir özeti aşağıdadır:</span><span class="sxs-lookup"><span data-stu-id="fe537-158">Here is a summary of things (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="fe537-159">Bir yığın yuvasında veya bir işlemci kaydındaki saklanan düzenli `AssemblyLoadContext`başvurular (Kullanıcı kodu tarafından açıkça oluşturulan ya da dolaylı olarak JIT tarafından), bir statik değişken veya güçlü/sabitleme GC tutamacı ve geçişli işaret:</span><span class="sxs-lookup"><span data-stu-id="fe537-159">Regular references held from outside of the collectible `AssemblyLoadContext`, stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the JIT), a static variable or a strong / pinning GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="fe537-160">Toplanabilir öğesine yüklenmiş bir bütünleştirilmiş kod `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="fe537-160">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="fe537-161">Bu tür bir derlemeden bir tür.</span><span class="sxs-lookup"><span data-stu-id="fe537-161">A type from such an assembly.</span></span>
  - <span data-ttu-id="fe537-162">Bu tür bir derlemeden bir türün örneği.</span><span class="sxs-lookup"><span data-stu-id="fe537-162">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="fe537-163">Toplanabilir öğesine yüklenen bir derlemeden kod çalıştıran iş parçacıkları `AssemblyLoadContext`.</span><span class="sxs-lookup"><span data-stu-id="fe537-163">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="fe537-164">Toplanabilir içinde oluşturulan özel toplanabilir `AssemblyLoadContext` türlerin örnekleri`AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="fe537-164">Instances of custom non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`</span></span>
- <span data-ttu-id="fe537-165">Geri <xref:System.Threading.RegisteredWaitHandle> çağırmaların özel içindeki yöntemlere ayarlandığı bekleyen örnekler`AssemblyLoadContext`</span><span class="sxs-lookup"><span data-stu-id="fe537-165">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`</span></span>

<span data-ttu-id="fe537-166">Yığın yuvası/işlemci kaydını bulma ipuçları bir nesneyi kök olarak kaydeder:</span><span class="sxs-lookup"><span data-stu-id="fe537-166">Hints to find stack slot / processor register rooting an object:</span></span>

- <span data-ttu-id="fe537-167">İşlev çağrısı sonuçlarının doğrudan başka bir işleve geçirilmesi, Kullanıcı tarafından oluşturulmuş bir yerel değişken olmasa da kök oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="fe537-167">Passing function call results directly to another function may create a root even though there is no user-created local variable.</span></span>
- <span data-ttu-id="fe537-168">Bir nesne başvurusu bir yöntemde herhangi bir noktada kullanılabilirse JıT, başvuruyu, geçerli işlevde istediği sürece bir yığın yuvası/işlemci kaydı içinde tutmaya karar vermiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe537-168">If a reference to an object was available at any point in a method, the JIT might have decided to keep the reference in a stack slot / processor register for as long as it wants in the current function.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="fe537-169">Hata ayıklama kaldırma sorunları</span><span class="sxs-lookup"><span data-stu-id="fe537-169">Debug unloading issues</span></span>

<span data-ttu-id="fe537-170">Kaldırma ile ilgili hata ayıklama sorunları sıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe537-170">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="fe537-171">`AssemblyLoadContext` Canlı neleri tutabilen, ancak kaldırma başarısız olursa, bu durumlara ulaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe537-171">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span>
<span data-ttu-id="fe537-172">Bu, sos eklentisi ile WinDbg (UNIX üzerinde lldb) ile ilgili yardım için en iyi uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="fe537-172">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="fe537-173">`LoaderAllocator` Belirli`AssemblyLoadContext` bir canlı kuruluşa ait olanları bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe537-173">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span>
<span data-ttu-id="fe537-174">Bu eklenti, GC yığın nesnelerine, hiyerarşilerine ve köklerine bakabilmeniz için izin verir.</span><span class="sxs-lookup"><span data-stu-id="fe537-174">This plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>
<span data-ttu-id="fe537-175">Eklentiyi hata ayıklayıcıya yüklemek için, hata ayıklayıcı komut satırına aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="fe537-175">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="fe537-176">WinDbg 'de (.NET Core uygulamasına bölünmediği zaman, WinDbg olarak görünür):</span><span class="sxs-lookup"><span data-stu-id="fe537-176">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="fe537-177">LLDB 'de:</span><span class="sxs-lookup"><span data-stu-id="fe537-177">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="fe537-178">Daha sonra, kaldırma sorunları olan bir örnek programda hata ayıklamaya deneyelim.</span><span class="sxs-lookup"><span data-stu-id="fe537-178">Let's try to debug an example program that has problems with unloading.</span></span> <span data-ttu-id="fe537-179">Kaynak kodu aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe537-179">Source code is included below.</span></span> <span data-ttu-id="fe537-180">Bunu WinDbg altında çalıştırdığınızda, program, kaldırma başarısını denetlemeye çalıştıktan sonra hata ayıklayıcıya hemen sonra sonlandırır.</span><span class="sxs-lookup"><span data-stu-id="fe537-180">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="fe537-181">Daha sonra Bu küller için aramaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fe537-181">You can then start looking for the culprits.</span></span>

<span data-ttu-id="fe537-182">UNIX üzerinde lldb kullanarak hata ayıklaması yaparsanız, aşağıdaki örneklerde yer alan sos komutlarının önünde yoktur `!` .</span><span class="sxs-lookup"><span data-stu-id="fe537-182">Note that if you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="fe537-183">Bu komut, GC yığınında olan içeren `LoaderAllocator` bir tür adı olan tüm nesneleri döker.</span><span class="sxs-lookup"><span data-stu-id="fe537-183">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="fe537-184">Aşağıda bir örnek verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fe537-184">Here is an example:</span></span>

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

<span data-ttu-id="fe537-185">Aşağıdaki "İstatistikler:" bölümünde, ilgilendiğimiz nesne olan `MT` öğesine`MethodTable` `System.Reflection.LoaderAllocator`ait olan () öğesini işaretleyin.</span><span class="sxs-lookup"><span data-stu-id="fe537-185">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="fe537-186">Ardından, başındaki listede, `MT` eşleşen girdiyi bulun ve nesnenin adresini alın.</span><span class="sxs-lookup"><span data-stu-id="fe537-186">Then in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="fe537-187">Bu durumda, "000002b78000ce40"</span><span class="sxs-lookup"><span data-stu-id="fe537-187">In our case, it is "000002b78000ce40"</span></span>

<span data-ttu-id="fe537-188">Artık `LoaderAllocator` nesnenin adresini öğrendiğimiz için, GC köklerinin bulunması için başka bir komut de kullanabiliriz</span><span class="sxs-lookup"><span data-stu-id="fe537-188">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots</span></span>

```console
!gcroot -all 0x000002b78000ce40 
```

<span data-ttu-id="fe537-189">Bu komut, `LoaderAllocator` örneğe yol açabilecek nesne başvuruları zincirini döker.</span><span class="sxs-lookup"><span data-stu-id="fe537-189">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="fe537-190">Liste, `LoaderAllocator` etkin olan ve bu nedenle hata ayıklaması yaptığınız sorunun çekirdeği olan köküyle başlar.</span><span class="sxs-lookup"><span data-stu-id="fe537-190">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem you're debugging.</span></span> <span data-ttu-id="fe537-191">Kök bir yığın yuvası, bir işlemci kaydı, bir GC tanıtıcısı veya statik değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="fe537-191">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="fe537-192">`gcroot` Komutun çıktısının bir örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="fe537-192">Here is an example of the output of the `gcroot` command:</span></span>

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

<span data-ttu-id="fe537-193">Şimdi, bu işlemi çözebilmeniz için kökün bulunduğu yeri belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe537-193">Now you need to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="fe537-194">En kolay durum, kök bir yığın yuvası veya bir işlemci kaydı olduğunda olur.</span><span class="sxs-lookup"><span data-stu-id="fe537-194">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="fe537-195">Bu durumda, `gcroot` çerçevesi kök içeren ve bu işlevi yürüten iş parçacığı olan işlevin adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fe537-195">In that case, the `gcroot` shows you the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="fe537-196">Zor durum, kökün bir statik değişken veya bir GC tutamacı olması durumunda olur.</span><span class="sxs-lookup"><span data-stu-id="fe537-196">The difficult case is when the root is a static variable or a GC handle.</span></span> 

<span data-ttu-id="fe537-197">Önceki örnekte, ilk kök, adresindeki `System.Reflection.RuntimeMethodInfo` `rbp-20` işlevin `example.Program.Main(System.String[])` çerçevesinde depolanan tür yereldir (`rbp` işlemci yazmacı `rbp` olur ve-20 Bu kaydın onaltılık bir uzaklığında oluşur).</span><span class="sxs-lookup"><span data-stu-id="fe537-197">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="fe537-198">İkinci kök, `test.Test` sınıfının bir örneğine başvuru tutan normal `GCHandle` (güçlü) bir sınıftır.</span><span class="sxs-lookup"><span data-stu-id="fe537-198">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span> 

<span data-ttu-id="fe537-199">Üçüncü kök sabitlenmiş `GCHandle`bir.</span><span class="sxs-lookup"><span data-stu-id="fe537-199">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="fe537-200">Bu, aslında statik bir değişkendir.</span><span class="sxs-lookup"><span data-stu-id="fe537-200">This one is actually a static variable.</span></span> <span data-ttu-id="fe537-201">Ne yazık ki, söylemek için bir yol yoktur.</span><span class="sxs-lookup"><span data-stu-id="fe537-201">Unfortunately, there is no way to tell.</span></span> <span data-ttu-id="fe537-202">Başvuru türleri için statiği, iç çalışma zamanı yapılarında yönetilen nesne dizisinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="fe537-202">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="fe537-203">Bir iş parçacığının, `AssemblyLoadContext` `AssemblyLoadContext` yığınında üzerine yüklenmiş bir derlemeden bir yöntemi olduğunda bir, öğesinin kaldırılmasını engelleyebilen başka bir durum.</span><span class="sxs-lookup"><span data-stu-id="fe537-203">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="fe537-204">Tüm iş parçacıklarının yönetilen çağrı yığınlarının dökümünü yaparak bunu kontrol edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="fe537-204">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="fe537-205">Komut "tüm iş parçacıkları `!clrstack` için geçerlidir" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="fe537-205">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="fe537-206">Örnek için bu komutun çıktısı aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="fe537-206">The following is the output of that command for the example.</span></span> <span data-ttu-id="fe537-207">Ne yazık ki, UNIX üzerinde lldb tüm iş parçacıkları için bir komut uygulamak için herhangi bir yola sahip değildir, bu nedenle iş parçacıklarını el ile değiştirmek ve `clrstack` komutu yinelemek için çare olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe537-207">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you'll need to resort to manually switching threads and repeating the `clrstack` command.</span></span>
<span data-ttu-id="fe537-208">Hata ayıklayıcının "yönetilen yığında ilerleme yapılamıyor" ifadesini belirten tüm iş parçacıklarını yoksayın.</span><span class="sxs-lookup"><span data-stu-id="fe537-208">Ignore all threads where the debugger says "Unable to walk the managed stack."</span></span>

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

<span data-ttu-id="fe537-209">Gördüğünüz gibi son iş parçacığı `test.Program.ThreadProc()`.</span><span class="sxs-lookup"><span data-stu-id="fe537-209">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="fe537-210">Bu, öğesine `AssemblyLoadContext`yüklenen derlemeden bir işlevdir ve bu sayede `AssemblyLoadContext` canlı tutar.</span><span class="sxs-lookup"><span data-stu-id="fe537-210">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="fe537-211">Loadability sorunları olan örnek kaynak</span><span class="sxs-lookup"><span data-stu-id="fe537-211">Example source with unloadability issues</span></span>

<span data-ttu-id="fe537-212">Aşağıdaki kod, önceki hata ayıklama örneğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="fe537-212">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="fe537-213">Ana test programı</span><span class="sxs-lookup"><span data-stu-id="fe537-213">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="fe537-214">TestAssemblyLoadContext içine yüklenen program</span><span class="sxs-lookup"><span data-stu-id="fe537-214">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="fe537-215">Aşağıdaki kod, ana test programındaki `ExecuteAndUnload` yöntemine geçirilen *test. dll dosyasını* temsil eder.</span><span class="sxs-lookup"><span data-stu-id="fe537-215">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
