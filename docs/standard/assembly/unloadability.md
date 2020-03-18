---
title: .NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama
description: Yönetilen derlemeleri yüklemek ve boşaltmak için tahsil edilebilir AssemblyLoadContext'ı nasıl kullanacağınızı ve boşaltma başarısını engelleyen sorunları nasıl hata ayıkleyeceğinizi öğrenin.
author: janvorli
ms.author: janvorli
ms.date: 02/05/2019
ms.openlocfilehash: 267c2209556b66ab3541c9c79c99d7eceb2024da
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159747"
---
# <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="111da-103">.NET Core’da kaldırabilme özelliğini kullanma ve hatalarını ayıklama</span><span class="sxs-lookup"><span data-stu-id="111da-103">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="111da-104">.NET Core 3.0 ile başlayarak, bir dizi derlemeyi yükleme ve daha sonra boşaltma olanağı desteklenir.</span><span class="sxs-lookup"><span data-stu-id="111da-104">Starting with .NET Core 3.0, the ability to load and later unload a set of assemblies is supported.</span></span> <span data-ttu-id="111da-105">.NET Framework'de bu amaç için özel uygulama etki alanları kullanıldı, ancak .NET Core yalnızca tek bir varsayılan uygulama etki alanını destekler.</span><span class="sxs-lookup"><span data-stu-id="111da-105">In .NET Framework, custom app domains were used for this purpose, but .NET Core only supports a single default app domain.</span></span>

<span data-ttu-id="111da-106">.NET Core 3.0 ve sonraki sürümler üzerinden <xref:System.Runtime.Loader.AssemblyLoadContext>yüklenebilirliği destekler.</span><span class="sxs-lookup"><span data-stu-id="111da-106">.NET Core 3.0 and later versions support unloadability through <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="111da-107">Bir koleksiyon içine derlemeler bir dizi `AssemblyLoadContext`yükleyebilir, onları yöntemleri yürütmek ya da sadece `AssemblyLoadContext`yansıma kullanarak bunları incelemek ve nihayet boşaltmak .</span><span class="sxs-lookup"><span data-stu-id="111da-107">You can load a set of assemblies into a collectible `AssemblyLoadContext`, execute methods in them or just inspect them using reflection, and finally unload the `AssemblyLoadContext`.</span></span> <span data-ttu-id="111da-108">Bu, yüklenen montajları `AssemblyLoadContext`boşaltıyor.</span><span class="sxs-lookup"><span data-stu-id="111da-108">That unloads the assemblies loaded into the `AssemblyLoadContext`.</span></span>

<span data-ttu-id="111da-109">AppDomains kullanarak `AssemblyLoadContext` boşaltma ve kullanma arasında kayda değer bir fark vardır.</span><span class="sxs-lookup"><span data-stu-id="111da-109">There's one noteworthy difference between the unloading using `AssemblyLoadContext` and using AppDomains.</span></span> <span data-ttu-id="111da-110">AppDomains ile, boşaltma zorlanır.</span><span class="sxs-lookup"><span data-stu-id="111da-110">With AppDomains, the unloading is forced.</span></span> <span data-ttu-id="111da-111">Boşaltma zamanında, hedef AppDomain'de çalışan tüm iş parçacıkları iptal edilir, hedef AppDomain'de oluşturulan yönetilen COM nesneleri yok edilir ve böyle devam eder.</span><span class="sxs-lookup"><span data-stu-id="111da-111">At unload time, all threads running in the target AppDomain are aborted, managed COM objects created in the target AppDomain are destroyed, and so on.</span></span> <span data-ttu-id="111da-112">Ile `AssemblyLoadContext`, boşaltma "kooperatif".</span><span class="sxs-lookup"><span data-stu-id="111da-112">With `AssemblyLoadContext`, the unload is "cooperative".</span></span> <span data-ttu-id="111da-113"><xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> Yöntemi çağırmak sadece boşaltmayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="111da-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.Unload%2A?displayProperty=nameWithType> method just initiates the unloading.</span></span> <span data-ttu-id="111da-114">Boşaltma aşağıdakilerden sonra sona erer:</span><span class="sxs-lookup"><span data-stu-id="111da-114">The unloading finishes after:</span></span>

- <span data-ttu-id="111da-115">Hiçbir iş parçacığı, çağrı yığınlarına `AssemblyLoadContext` yüklenen derlemelerden gelen yöntemleri yoktur.</span><span class="sxs-lookup"><span data-stu-id="111da-115">No threads have methods from the assemblies loaded into the `AssemblyLoadContext` on their call stacks.</span></span>
- <span data-ttu-id="111da-116">Bu tür, örneklere `AssemblyLoadContext`yüklenen derlemelerden hiçbirtürü ve derlemelerin kendileri aşağıdakiler tarafından başvurulan değildir:</span><span class="sxs-lookup"><span data-stu-id="111da-116">None of the types from the assemblies loaded into the `AssemblyLoadContext`, instances of those types, and the assemblies themselves are referenced by:</span></span>
  - <span data-ttu-id="111da-117">Zayıf `AssemblyLoadContext`referanslar dışında referanslar<xref:System.WeakReference> ( <xref:System.WeakReference%601>veya ).</span><span class="sxs-lookup"><span data-stu-id="111da-117">References outside of the `AssemblyLoadContext`, except of weak references (<xref:System.WeakReference> or <xref:System.WeakReference%601>).</span></span>
  - <span data-ttu-id="111da-118">Güçlü çöp toplayıcı (GC) kolları[(GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) veya [GCHandleType.Pinned)](xref:System.Runtime.InteropServices.GCHandleType.Pinned) `AssemblyLoadContext`hem içinden hem de dışından .</span><span class="sxs-lookup"><span data-stu-id="111da-118">Strong garbage collector (GC) handles ([GCHandleType.Normal](xref:System.Runtime.InteropServices.GCHandleType.Normal) or [GCHandleType.Pinned](xref:System.Runtime.InteropServices.GCHandleType.Pinned)) from both inside and outside of the `AssemblyLoadContext`.</span></span>

## <a name="use-collectible-assemblyloadcontext"></a><span data-ttu-id="111da-119">Tahsil Edilebilir AssemblyLoadContext kullanın</span><span class="sxs-lookup"><span data-stu-id="111da-119">Use collectible AssemblyLoadContext</span></span>

<span data-ttu-id="111da-120">Bu bölümde, bir .NET Core uygulamasını koleksiyona `AssemblyLoadContext`yüklemenin, giriş noktasını çalıştırmanın ve sonra boşaltmanın basit bir yolunu gösteren ayrıntılı bir adım adım öğretici içerir.</span><span class="sxs-lookup"><span data-stu-id="111da-120">This section contains a detailed step-by-step tutorial that shows a simple way to load a .NET Core application into a collectible `AssemblyLoadContext`, execute its entry point, and then unload it.</span></span> <span data-ttu-id="111da-121">Tam bir örnek [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading)bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="111da-121">You can find a complete sample at [https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading](https://github.com/dotnet/samples/tree/master/core/tutorials/Unloading).</span></span>

### <a name="create-a-collectible-assemblyloadcontext"></a><span data-ttu-id="111da-122">Tahsil edilebilir bir AssemblyLoadContext oluşturun</span><span class="sxs-lookup"><span data-stu-id="111da-122">Create a collectible AssemblyLoadContext</span></span>

<span data-ttu-id="111da-123">Sınıfınızı kendi <xref:System.Runtime.Loader.AssemblyLoadContext> <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> yönteminden türemiş ve aşırı yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="111da-123">You need to derive your class from the <xref:System.Runtime.Loader.AssemblyLoadContext> and overload its <xref:System.Runtime.Loader.AssemblyLoadContext.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="111da-124">Bu yöntem, bu `AssemblyLoadContext`bağlı bağlı meclislerin bağımlılıkları olan tüm derlemelere yapılan başvuruları çözer.</span><span class="sxs-lookup"><span data-stu-id="111da-124">That method resolves references to all assemblies that are dependencies of assemblies loaded into that `AssemblyLoadContext`.</span></span>

<span data-ttu-id="111da-125">Aşağıdaki kod en basit özel `AssemblyLoadContext`bir örnektir:</span><span class="sxs-lookup"><span data-stu-id="111da-125">The following code is an example of the simplest custom `AssemblyLoadContext`:</span></span>

[!code-csharp[Simple custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/simple_example.cs#1)]

<span data-ttu-id="111da-126">Gördüğünüz gibi, `Load` yöntem döndürür. `null`</span><span class="sxs-lookup"><span data-stu-id="111da-126">As you can see, the `Load` method returns `null`.</span></span> <span data-ttu-id="111da-127">Bu, tüm bağımlılık derlemelerinin varsayılan içeriğe yüklendiği ve yeni bağlamın yalnızca açıkça yüklenen derlemeleri içerdiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="111da-127">That means that all the dependency assemblies are loaded into the default context, and the new context contains only the assemblies explicitly loaded into it.</span></span>

<span data-ttu-id="111da-128">Bağımlılıkların bir kısmını veya tamamını `AssemblyLoadContext` çok yüklemek istiyorsanız, `AssemblyDependencyResolver` `Load` yöntemde kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="111da-128">If you want to load some or all of the dependencies into the `AssemblyLoadContext` too, you can use the `AssemblyDependencyResolver` in the `Load` method.</span></span> <span data-ttu-id="111da-129">Derleme `AssemblyDependencyResolver` adlarını mutlak derleme dosya yollarına giderir.</span><span class="sxs-lookup"><span data-stu-id="111da-129">The `AssemblyDependencyResolver` resolves the assembly names to absolute assembly file paths.</span></span> <span data-ttu-id="111da-130">Çözümleyici, bağlama yüklenen ana derlemenin dizininde *.deps.json* dosyasını ve derleme dosyalarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="111da-130">The resolver uses the *.deps.json* file and assembly files in the directory of the main assembly loaded into the context.</span></span>

[!code-csharp[Advanced custom AssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/complex_assemblyloadcontext.cs)]

### <a name="use-a-custom-collectible-assemblyloadcontext"></a><span data-ttu-id="111da-131">Özel bir tahsil AssemblyLoadContext kullanın</span><span class="sxs-lookup"><span data-stu-id="111da-131">Use a custom collectible AssemblyLoadContext</span></span>

<span data-ttu-id="111da-132">Bu bölümde kullanılan basit sürümü `TestAssemblyLoadContext` varsayar.</span><span class="sxs-lookup"><span data-stu-id="111da-132">This section assumes the simpler version of the `TestAssemblyLoadContext` is being used.</span></span>

<span data-ttu-id="111da-133">Özel `AssemblyLoadContext` bir örnek oluşturabilir ve aşağıdaki gibi bir derleme yükleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="111da-133">You can create an instance of the custom `AssemblyLoadContext` and load an assembly into it as follows:</span></span>

[!code-csharp[Part 1](~/samples/snippets/standard/assembly/unloading/simple_example.cs#3)]

<span data-ttu-id="111da-134">Yüklenen derleme tarafından başvurulan derlemelerin her `TestAssemblyLoadContext.Load` biri için, derlemenin nereden alınacağına karar `TestAssemblyLoadContext` verebilmeleri için yöntem çağrılır.</span><span class="sxs-lookup"><span data-stu-id="111da-134">For each of the assemblies referenced by the loaded assembly, the `TestAssemblyLoadContext.Load` method is called so that the `TestAssemblyLoadContext` can decide where to get the assembly from.</span></span> <span data-ttu-id="111da-135">Bizim durumumuzda, `null` çalışma zamanı varsayılan olarak derlemeleri yüklemek için kullandığı konumlardan varsayılan içeriğe yüklenmesi gerektiğini belirtmek için döner.</span><span class="sxs-lookup"><span data-stu-id="111da-135">In our case, it returns `null` to indicate that it should be loaded into the default context from locations that the runtime uses to load assemblies by default.</span></span>

<span data-ttu-id="111da-136">Artık bir derleme yüklendiğine göre, ondan bir yöntem uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="111da-136">Now that an assembly was loaded, you can execute a method from it.</span></span> <span data-ttu-id="111da-137">Yöntemi `Main` çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="111da-137">Run the `Main` method:</span></span>

[!code-csharp[Part 2](~/samples/snippets/standard/assembly/unloading/simple_example.cs#4)]

<span data-ttu-id="111da-138">Yöntem döndükten sonra, özel `AssemblyLoadContext` yöntem ekime `Unload` göre arayarak veya aşağıdakilere sahip olduğunuz `AssemblyLoadContext`başvurudan kurtularak boşaltma işlemini başlatabilirsiniz: `Main`</span><span class="sxs-lookup"><span data-stu-id="111da-138">After the `Main` method returns, you can initiate unloading by either calling the `Unload` method on the custom `AssemblyLoadContext` or getting rid of the reference you have to the `AssemblyLoadContext`:</span></span>

[!code-csharp[Part 3](~/samples/snippets/standard/assembly/unloading/simple_example.cs#5)]

<span data-ttu-id="111da-139">Bu, test montajını boşaltmak için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="111da-139">This is sufficient to unload the test assembly.</span></span> <span data-ttu-id="111da-140">Tüm bunları, yığın yuvası referansları (gerçek veya JIT tarafından `TestAssemblyLoadContext` `Assembly`tanıtılan `MethodInfo` yerel `Assembly.EntryPoint`halklar) tarafından canlı tutulamadığından emin olmak için ayrı bir inlineable olmayan yönteme koyalım.</span><span class="sxs-lookup"><span data-stu-id="111da-140">Let's actually put all of this into a separate non-inlineable method to ensure that the `TestAssemblyLoadContext`, `Assembly`, and `MethodInfo` (the `Assembly.EntryPoint`) can't be kept alive by stack slot references (real- or JIT-introduced locals).</span></span> <span data-ttu-id="111da-141">Bu hayatta `TestAssemblyLoadContext` kalabilir ve boşaltmayı önleyebilir.</span><span class="sxs-lookup"><span data-stu-id="111da-141">That could keep the `TestAssemblyLoadContext` alive and prevent the unload.</span></span>

<span data-ttu-id="111da-142">Ayrıca, daha sonra boşaltma `AssemblyLoadContext` tamamlama algılamak için kullanabilirsiniz böylece zayıf bir başvuru döndürün.</span><span class="sxs-lookup"><span data-stu-id="111da-142">Also, return a weak reference to the `AssemblyLoadContext` so that you can use it later to detect unload completion.</span></span>

[!code-csharp[Part 4](~/samples/snippets/standard/assembly/unloading/simple_example.cs#2)]

<span data-ttu-id="111da-143">Artık bu işlevi derlemeyi yüklemek, yürütmek ve boşaltmak için çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="111da-143">Now you can run this function to load, execute, and unload the assembly.</span></span>

[!code-csharp[Part 5](~/samples/snippets/standard/assembly/unloading/simple_example.cs#6)]

<span data-ttu-id="111da-144">Ancak, boşaltma hemen tamamlanmaz.</span><span class="sxs-lookup"><span data-stu-id="111da-144">However, the unload doesn't complete immediately.</span></span> <span data-ttu-id="111da-145">Daha önce de belirtildiği gibi, test derlemetüm nesneleri toplamak için çöp toplayıcı güveniyor.</span><span class="sxs-lookup"><span data-stu-id="111da-145">As previously mentioned, it relies on the garbage collector to collect all the objects from the test assembly.</span></span> <span data-ttu-id="111da-146">Çoğu durumda, boşaltma nın tamamlanmasını beklemek gerekmez.</span><span class="sxs-lookup"><span data-stu-id="111da-146">In many cases, it isn't necessary to wait for the unload completion.</span></span> <span data-ttu-id="111da-147">Ancak, boşaltmanın bittiğini bilmenin yararlı olduğu durumlar vardır.</span><span class="sxs-lookup"><span data-stu-id="111da-147">However, there are cases where it's useful to know that the unload has finished.</span></span> <span data-ttu-id="111da-148">Örneğin, özel `AssemblyLoadContext` ekine yüklenen derleme dosyasını diskten silmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="111da-148">For example, you may want to delete the assembly file that was loaded into the custom `AssemblyLoadContext` from disk.</span></span> <span data-ttu-id="111da-149">Böyle bir durumda, aşağıdaki kod parçacığı kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="111da-149">In such a case, the following code snippet can be used.</span></span> <span data-ttu-id="111da-150">Çöp toplamayı tetikler ve özele `AssemblyLoadContext` zayıf başvuru ayarlanana kadar bekleyen sonlandırıcıları bir döngüiçinde `null`bekler, hedef nesnenin toplandığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="111da-150">It triggers garbage collection and waits for pending finalizers in a loop until the weak reference to the custom `AssemblyLoadContext` is set to `null`, indicating the target object was collected.</span></span> <span data-ttu-id="111da-151">Çoğu durumda, döngü den sadece bir geçiş gereklidir.</span><span class="sxs-lookup"><span data-stu-id="111da-151">In most cases, just one pass through the loop is required.</span></span> <span data-ttu-id="111da-152">Ancak, kod tarafından oluşturulan nesnelerin sonlandırıcılara `AssemblyLoadContext` sahip olduğu daha karmaşık durumlarda daha fazla geçiş gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="111da-152">However, for more complex cases where objects created by the code running in the `AssemblyLoadContext` have finalizers, more passes may be needed.</span></span>

[!code-csharp[Part 6](~/samples/snippets/standard/assembly/unloading/simple_example.cs#7)]

### <a name="the-unloading-event"></a><span data-ttu-id="111da-153">Boşaltma olayı</span><span class="sxs-lookup"><span data-stu-id="111da-153">The Unloading event</span></span>

<span data-ttu-id="111da-154">Bazı durumlarda, özel bir `AssemblyLoadContext` koda yüklenen kodun, boşaltma başlatıldığında bazı temizleme işlemleri gerçekleştirmesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="111da-154">In some cases, it may be necessary for the code loaded into a custom `AssemblyLoadContext` to perform some cleanup when the unloading is initiated.</span></span> <span data-ttu-id="111da-155">Örneğin, iş parçacıklarını durdurması veya güçlü GC tutamaçları temizlemesi gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="111da-155">For example, it may need to stop threads or clean up strong GC handles.</span></span> <span data-ttu-id="111da-156">Olay `Unloading` bu gibi durumlarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="111da-156">The `Unloading` event can be used in such cases.</span></span> <span data-ttu-id="111da-157">Gerekli temizlemeyi gerçekleştiren bir işleyici bu olaya bağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="111da-157">A handler that performs the necessary cleanup can be hooked to this event.</span></span>

### <a name="troubleshoot-unloadability-issues"></a><span data-ttu-id="111da-158">Sorun giderme yüklenebilirlik sorunları</span><span class="sxs-lookup"><span data-stu-id="111da-158">Troubleshoot unloadability issues</span></span>

<span data-ttu-id="111da-159">Boşaltma nın işbirlikçi doğası nedeniyle, bir koleksiyon `AssemblyLoadContext` da canlı şeyler tutmak ve boşaltma önleme olabilir referansları unutmak kolaydır.</span><span class="sxs-lookup"><span data-stu-id="111da-159">Due to the cooperative nature of the unloading, it's easy to forget about references that may be keeping the stuff in a collectible `AssemblyLoadContext` alive and preventing unload.</span></span> <span data-ttu-id="111da-160">Burada, referansları tutabilen varlıkların (bazıları açık olmayan) bir özeti ver:</span><span class="sxs-lookup"><span data-stu-id="111da-160">Here is a summary of entities (some of them non-obvious) that can hold the references:</span></span>

- <span data-ttu-id="111da-161">Bir yığın yuvasında veya `AssemblyLoadContext` işlemci kaydında depolanan koleksiyon dışından tutulan düzenli başvurular (kullanıcı kodu tarafından açıkça oluşturulan veya tam zamanında (JIT) derleyici tarafından dolaylı olarak oluşturulan yöntem yerlileri), statik bir değişken veya güçlü (sabitleme) GC tutamacı ve geçişli olarak işaret eden:</span><span class="sxs-lookup"><span data-stu-id="111da-161">Regular references held from outside of the collectible `AssemblyLoadContext` that are stored in a stack slot or a processor register (method locals, either explicitly created by the user code or implicitly by the just-in-time (JIT) compiler), a static variable, or a strong (pinning) GC handle, and transitively pointing to:</span></span>
  - <span data-ttu-id="111da-162">Tahsil edilen ekime `AssemblyLoadContext`yüklenen bir montaj.</span><span class="sxs-lookup"><span data-stu-id="111da-162">An assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
  - <span data-ttu-id="111da-163">Böyle bir derlemeden bir tür.</span><span class="sxs-lookup"><span data-stu-id="111da-163">A type from such an assembly.</span></span>
  - <span data-ttu-id="111da-164">Böyle bir derleme bir tür örneği.</span><span class="sxs-lookup"><span data-stu-id="111da-164">An instance of a type from such an assembly.</span></span>
- <span data-ttu-id="111da-165">Tahsil edilen bir derlemeden kod çalıştıran iş `AssemblyLoadContext`parçacıkları.</span><span class="sxs-lookup"><span data-stu-id="111da-165">Threads running code from an assembly loaded into the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="111da-166">Özel örnekleri, tahsil olmayan `AssemblyLoadContext` türlerinde koleksiyon `AssemblyLoadContext`içinde oluşturulan.</span><span class="sxs-lookup"><span data-stu-id="111da-166">Instances of custom, non-collectible `AssemblyLoadContext` types created inside of the collectible `AssemblyLoadContext`.</span></span>
- <span data-ttu-id="111da-167">Özel <xref:System.Threading.RegisteredWaitHandle> `AssemblyLoadContext`yöntemlere ayarlanmış geri aramabekleyen örnekleri.</span><span class="sxs-lookup"><span data-stu-id="111da-167">Pending <xref:System.Threading.RegisteredWaitHandle> instances with callbacks set to methods in the custom `AssemblyLoadContext`.</span></span>

> [!TIP]
> <span data-ttu-id="111da-168">Yığın yuvalarında veya işlemci kayıtlarında depolanan ve aşağıdaki durumlarda bir `AssemblyLoadContext` nesnenin boşaltılmasını önleyebilecek nesne başvuruları:</span><span class="sxs-lookup"><span data-stu-id="111da-168">Object references that are stored in stack slots or processor registers and that could prevent unloading of an `AssemblyLoadContext` can occur in the following situations:</span></span>
>
> - <span data-ttu-id="111da-169">Kullanıcı tarafından oluşturulan yerel değişken olmamasına rağmen, işlev çağrı sonuçları doğrudan başka bir işleve geçirildiğinde.</span><span class="sxs-lookup"><span data-stu-id="111da-169">When function call results are passed directly to another function, even though there is no user-created local variable.</span></span>
> - <span data-ttu-id="111da-170">JIT derleyicisi bir yöntemde bir noktada kullanılabilir bir nesneye bir başvuru tutar.</span><span class="sxs-lookup"><span data-stu-id="111da-170">When the JIT compiler keeps a reference to an object that was available at some point in a method.</span></span>

## <a name="debug-unloading-issues"></a><span data-ttu-id="111da-171">Hata ayıklama sorunları</span><span class="sxs-lookup"><span data-stu-id="111da-171">Debug unloading issues</span></span>

<span data-ttu-id="111da-172">Boşaltma ile ilgili hata ayıklama sorunları sıkıcı olabilir.</span><span class="sxs-lookup"><span data-stu-id="111da-172">Debugging issues with unloading can be tedious.</span></span> <span data-ttu-id="111da-173">Bir `AssemblyLoadContext` canlı tutan ne olduğunu bilmiyorum durumlara girebilirsiniz, ama boşaltma başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="111da-173">You can get into situations where you don't know what can be holding an `AssemblyLoadContext` alive, but the unload fails.</span></span> <span data-ttu-id="111da-174">Bu konuda yardımcı olmak için en iyi silah WINDbg (LLDB Unix üzerinde) SOS eklentisi ile.</span><span class="sxs-lookup"><span data-stu-id="111da-174">The best weapon to help with that is WinDbg (LLDB on Unix) with the SOS plugin.</span></span> <span data-ttu-id="111da-175">Bir `LoaderAllocator` ait olanı `AssemblyLoadContext` canlı tutan şeyi bulmalısın.</span><span class="sxs-lookup"><span data-stu-id="111da-175">You need to find what's keeping a `LoaderAllocator` belonging to the specific `AssemblyLoadContext` alive.</span></span> <span data-ttu-id="111da-176">SOS eklentisi GC yığın nesneleri, hiyerarşileri ve kökleri bakmak için izin verir.</span><span class="sxs-lookup"><span data-stu-id="111da-176">The SOS plugin allows you to look at GC heap objects, their hierarchies, and roots.</span></span>

<span data-ttu-id="111da-177">Eklentiyi hata ayıkleyiciye yüklemek için hata ayıklama komut satırına aşağıdaki komutu girin:</span><span class="sxs-lookup"><span data-stu-id="111da-177">To load the plugin into the debugger, enter the following command in the debugger command line:</span></span>

<span data-ttu-id="111da-178">WinDbg (WinDbg otomatik olarak .NET Core uygulamasına girerken yapar gibi görünüyor):</span><span class="sxs-lookup"><span data-stu-id="111da-178">In WinDbg (it seems WinDbg does that automatically when breaking into .NET Core application):</span></span>

```console
.loadby sos coreclr
```

<span data-ttu-id="111da-179">LLDB olarak:</span><span class="sxs-lookup"><span data-stu-id="111da-179">In LLDB:</span></span>

```console
plugin load /path/to/libsosplugin.so
```

<span data-ttu-id="111da-180">Boşaltma ile ilgili sorunları olan bir örnek programı hata ayıklayalım.</span><span class="sxs-lookup"><span data-stu-id="111da-180">Let's debug an example program that has problems with unloading.</span></span> <span data-ttu-id="111da-181">Kaynak kodu aşağıda yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="111da-181">Source code is included below.</span></span> <span data-ttu-id="111da-182">WinDbg altında çalıştırdığınızda, program boşaltma başarısını denetlemeye çalıştıktan hemen sonra hata ayıklamaya girer.</span><span class="sxs-lookup"><span data-stu-id="111da-182">When you run it under WinDbg, the program breaks into the debugger right after attempting to check for the unload success.</span></span> <span data-ttu-id="111da-183">Daha sonra suçluları aramaya başlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="111da-183">You can then start looking for the culprits.</span></span>

> [!TIP]
> <span data-ttu-id="111da-184">Unix'te LLDB kullanarak hata ayıklama ederseniz, aşağıdaki örneklerdeki `!` SOS komutlarının önünde yoktur.</span><span class="sxs-lookup"><span data-stu-id="111da-184">If you debug using LLDB on Unix, the SOS commands in the following examples don't have the `!` in front of them.</span></span>

```console
!dumpheap -type LoaderAllocator
```

<span data-ttu-id="111da-185">Bu komut, GC yığınında bulunan `LoaderAllocator` bir tür adı içeren tüm nesneleri atar.</span><span class="sxs-lookup"><span data-stu-id="111da-185">This command dumps all objects with a type name containing `LoaderAllocator` that are in the GC heap.</span></span> <span data-ttu-id="111da-186">Örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="111da-186">Here is an example:</span></span>

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

<span data-ttu-id="111da-187">Aşağıdaki "İstatistikler:" bölümünde, `MT` önemsediğimiz nesneolan `System.Reflection.LoaderAllocator`nesneye ait (`MethodTable`) bölümünü kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="111da-187">In the "Statistics:" part below, check the `MT` (`MethodTable`) belonging to the `System.Reflection.LoaderAllocator`, which is the object we care about.</span></span> <span data-ttu-id="111da-188">Daha sonra, başlangıçtaki listede, bu `MT` ile eşleşen girişi bulmak ve nesnenin kendisi adresini almak.</span><span class="sxs-lookup"><span data-stu-id="111da-188">Then, in the list at the beginning, find the entry with `MT` matching that one and get the address of the object itself.</span></span> <span data-ttu-id="111da-189">Bizim durumumuzda, "000002b78000ce40".</span><span class="sxs-lookup"><span data-stu-id="111da-189">In our case, it is "000002b78000ce40".</span></span>

<span data-ttu-id="111da-190">Artık `LoaderAllocator` nesnenin adresini bildiğimize göre, GC köklerini bulmak için başka bir komut kullanabiliriz:</span><span class="sxs-lookup"><span data-stu-id="111da-190">Now that we know the address of the `LoaderAllocator` object, we can use another command to find its GC roots:</span></span>

```console
!gcroot -all 0x000002b78000ce40
```

<span data-ttu-id="111da-191">Bu komut, örneğine yol açan nesne `LoaderAllocator` başvuruları zincirini çöpe atar.</span><span class="sxs-lookup"><span data-stu-id="111da-191">This command dumps the chain of object references that lead to the `LoaderAllocator` instance.</span></span> <span data-ttu-id="111da-192">Liste kökle başlar, ki bu bizim `LoaderAllocator` canlı tutan varlıktır ve böylece sorunun özüdür.</span><span class="sxs-lookup"><span data-stu-id="111da-192">The list starts with the root, which is the entity that keeps our `LoaderAllocator` alive and thus is the core of the problem.</span></span> <span data-ttu-id="111da-193">Kök bir yığın yuvası, bir işlemci kaydı, bir GC tutamacı veya statik bir değişken olabilir.</span><span class="sxs-lookup"><span data-stu-id="111da-193">The root can be a stack slot, a processor register, a GC handle, or a static variable.</span></span>

<span data-ttu-id="111da-194">Aşağıda `gcroot` komutun çıktısının bir örneği verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="111da-194">Here is an example of the output of the `gcroot` command:</span></span>

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

<span data-ttu-id="111da-195">Bir sonraki adım, kökün nerede olduğunu bulmak, böylece onu düzeltebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="111da-195">The next step is to figure out where the root is located so you can fix it.</span></span> <span data-ttu-id="111da-196">En kolay durum, kök bir yığın yuvası veya işlemci kaydı olduğunda.</span><span class="sxs-lookup"><span data-stu-id="111da-196">The easiest case is when the root is a stack slot or a processor register.</span></span> <span data-ttu-id="111da-197">Bu durumda, `gcroot` çerçeve kök ve bu işlevi yürüten iş parçacığı içeren işlevin adını gösterir.</span><span class="sxs-lookup"><span data-stu-id="111da-197">In that case, the `gcroot` shows the name of the function whose frame contains the root and the thread executing that function.</span></span> <span data-ttu-id="111da-198">Zor durumda kök statik bir değişken veya GC kolu olduğunda.</span><span class="sxs-lookup"><span data-stu-id="111da-198">The difficult case is when the root is a static variable or a GC handle.</span></span>

<span data-ttu-id="111da-199">Önceki örnekte, ilk kök adresteki `System.Reflection.RuntimeMethodInfo` `example.Program.Main(System.String[])` `rbp-20` işlevçerçevesinde depolanan tür yereldir`rbp` (işlemci kaydıdır `rbp` ve -20 bu kayıttan bir hexadecimal ofsettir).</span><span class="sxs-lookup"><span data-stu-id="111da-199">In the previous example, the first root is a local of type `System.Reflection.RuntimeMethodInfo` stored in the frame of the function `example.Program.Main(System.String[])` at address `rbp-20` (`rbp` is the processor register `rbp` and -20 is a hexadecimal offset from that register).</span></span>

<span data-ttu-id="111da-200">İkinci kök, `GCHandle` `test.Test` sınıfın bir örneğine başvuru tutan normal (güçlü) bir köktür.</span><span class="sxs-lookup"><span data-stu-id="111da-200">The second root is a normal (strong) `GCHandle` that holds a reference to an instance of the `test.Test` class.</span></span>

<span data-ttu-id="111da-201">Üçüncü kök sabitlenmiş. `GCHandle`</span><span class="sxs-lookup"><span data-stu-id="111da-201">The third root is a pinned `GCHandle`.</span></span> <span data-ttu-id="111da-202">Bu aslında statik bir değişken, ama ne yazık ki, bunu söylemenin bir yolu yok.</span><span class="sxs-lookup"><span data-stu-id="111da-202">This one is actually a static variable, but unfortunately, there is no way to tell.</span></span> <span data-ttu-id="111da-203">Başvuru türleri için statik, iç çalışma zamanı yapılarında yönetilen bir nesne dizisinde depolanır.</span><span class="sxs-lookup"><span data-stu-id="111da-203">Statics for reference types are stored in a managed object array in internal runtime structures.</span></span>

<span data-ttu-id="111da-204">Bir `AssemblyLoadContext` iş parçacığının boşaltılmasını önleyebilecek başka bir örnek de, bir `AssemblyLoadContext` iş parçacığının yığınına yüklenen bir derlemeden bir yöntem çerçevesine sahip olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="111da-204">Another case that can prevent unloading of an `AssemblyLoadContext` is when a thread has a frame of a method from an assembly loaded into the `AssemblyLoadContext` on its stack.</span></span> <span data-ttu-id="111da-205">Tüm iş parçacıklarının yönetilen çağrı yığınlarını damping tarafından kontrol edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="111da-205">You can check that by dumping managed call stacks of all threads:</span></span>

```console
~*e !clrstack
```

<span data-ttu-id="111da-206">Komut , "tüm iş parçacıkları `!clrstack` komutu için geçerli" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="111da-206">The command means "apply to all threads the `!clrstack` command".</span></span> <span data-ttu-id="111da-207">Aşağıdaki örnek için bu komutun çıktısi.</span><span class="sxs-lookup"><span data-stu-id="111da-207">The following is the output of that command for the example.</span></span> <span data-ttu-id="111da-208">Ne yazık ki, Unix LLDB tüm iş parçacıkları için bir komut uygulamak için herhangi bir `clrstack` yolu yoktur, bu yüzden el ile iş parçacığı geçiş ve komutu tekrarlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="111da-208">Unfortunately, LLDB on Unix doesn't have any way to apply a command to all threads, so you must manually switch threads and repeat the `clrstack` command.</span></span> <span data-ttu-id="111da-209">Hata ayıklamanın "Yönetilen yığında yürüyemiyor" dediği tüm iş parçacıklarını yoksayın.</span><span class="sxs-lookup"><span data-stu-id="111da-209">Ignore all threads where the debugger says "Unable to walk the managed stack".</span></span>

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

<span data-ttu-id="111da-210">Gördüğünüz gibi, son iş `test.Program.ThreadProc()`parçacığı .</span><span class="sxs-lookup"><span data-stu-id="111da-210">As you can see, the last thread has `test.Program.ThreadProc()`.</span></span> <span data-ttu-id="111da-211">Bu, montajdan `AssemblyLoadContext`yüklenen bir fonksiyondur ve bu `AssemblyLoadContext` yüzden canlı tutar.</span><span class="sxs-lookup"><span data-stu-id="111da-211">This is a function from the assembly loaded into the `AssemblyLoadContext`, and so it keeps the `AssemblyLoadContext` alive.</span></span>

## <a name="example-source-with-unloadability-issues"></a><span data-ttu-id="111da-212">Yüklenebilirlik sorunları olan örnek kaynak</span><span class="sxs-lookup"><span data-stu-id="111da-212">Example source with unloadability issues</span></span>

<span data-ttu-id="111da-213">Önceki hata ayıklama örneğinde aşağıdaki kod kullanılır.</span><span class="sxs-lookup"><span data-stu-id="111da-213">The following code is used in the previous debugging example.</span></span>

### <a name="main-testing-program"></a><span data-ttu-id="111da-214">Ana test programı</span><span class="sxs-lookup"><span data-stu-id="111da-214">Main testing program</span></span>

[!code-csharp[Main testing program](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_main.cs)]

## <a name="program-loaded-into-the-testassemblyloadcontext"></a><span data-ttu-id="111da-215">TestAssemblyLoadContext'a yüklenen program</span><span class="sxs-lookup"><span data-stu-id="111da-215">Program loaded into the TestAssemblyLoadContext</span></span>

<span data-ttu-id="111da-216">Aşağıdaki kod, ana test programında `ExecuteAndUnload` yönteme geçen *test.dll'yi* temsil eder.</span><span class="sxs-lookup"><span data-stu-id="111da-216">The following code represents the *test.dll* passed to the `ExecuteAndUnload` method in the main testing program.</span></span>

[!code-csharp[Program loaded into the TestAssemblyLoadContext](~/samples/snippets/standard/assembly/unloading/unloadability_issues_example_test.cs)]
