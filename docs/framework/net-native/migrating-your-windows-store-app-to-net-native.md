---
title: Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 987669fc51eeaf7e3bdef3e91a2f1ce23164a055
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389712"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a><span data-ttu-id="7c178-102">Windows Mağazası Uygulamanızı .NET Native'e geçirin</span><span class="sxs-lookup"><span data-stu-id="7c178-102">Migrate Your Windows Store App to .NET Native</span></span>

<span data-ttu-id="7c178-103">.NET Native, Windows Mağazası'ndaki veya geliştiricinin bilgisayarındaki uygulamaların statik derlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c178-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="7c178-104">Bu, Windows Mağazası uygulamaları için aygıttaki tam zamanında (JIT) derleyiciveya [Yerel Görüntü Üreteci (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) tarafından gerçekleştirilen dinamik derlemeden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="7c178-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="7c178-105">Farklılıklara rağmen,.NET Native [Windows Mağazası uygulamaları için .NET](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)ile uyumluluğu korumaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="7c178-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span></span> <span data-ttu-id="7c178-106">Çoğunlukla, Windows Mağazası uygulamaları için .NET'te çalışan şeyler de .NET Native ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="7c178-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="7c178-107">Ancak, bazı durumlarda davranış değişiklikleriyle karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c178-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="7c178-108">Bu belgede, Windows Mağazası uygulamaları için standart .NET ile aşağıdaki alanlarda .NET Native arasındaki farklar açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="7c178-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>

- [<span data-ttu-id="7c178-109">Genel çalışma zamanı farkları</span><span class="sxs-lookup"><span data-stu-id="7c178-109">General runtime differences</span></span>](#Runtime)

- [<span data-ttu-id="7c178-110">Dinamik programlama farklılıkları</span><span class="sxs-lookup"><span data-stu-id="7c178-110">Dynamic programming differences</span></span>](#Dynamic)

- [<span data-ttu-id="7c178-111">Yansımayla ilgili diğer farklar</span><span class="sxs-lookup"><span data-stu-id="7c178-111">Other reflection-related differences</span></span>](#Reflection)

- [<span data-ttu-id="7c178-112">Desteklenmeyen senaryolar ve API'ler</span><span class="sxs-lookup"><span data-stu-id="7c178-112">Unsupported scenarios and APIs</span></span>](#Unsupported)

- [<span data-ttu-id="7c178-113">Visual Studio farklılıkları</span><span class="sxs-lookup"><span data-stu-id="7c178-113">Visual Studio differences</span></span>](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a><span data-ttu-id="7c178-114">Genel çalışma zamanı farkları</span><span class="sxs-lookup"><span data-stu-id="7c178-114">General runtime differences</span></span>

- <span data-ttu-id="7c178-115">Bir uygulama ortak <xref:System.TypeLoadException>dil çalışma zamanında (CLR) çalıştığında JIT derleyicisi tarafından atılan , genellikle .NET Native tarafından işlendiğinde derleme zamanı hatalarına neden olur gibi özel durumlar.</span><span class="sxs-lookup"><span data-stu-id="7c178-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>

- <span data-ttu-id="7c178-116">Yöntemi bir uygulamanın <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> Ara Birimi iş parçacığından aramayın.</span><span class="sxs-lookup"><span data-stu-id="7c178-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="7c178-117">Bu, .NET Native'de bir kilitlenmeyle sonuçlanabilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-117">This can result in a deadlock on .NET Native.</span></span>

- <span data-ttu-id="7c178-118">Statik sınıf oluşturucu çağırma siparişine güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="7c178-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="7c178-119">.NET Native'de çağırma sırası standart çalışma zamanındaki sıralamadan farklıdır.</span><span class="sxs-lookup"><span data-stu-id="7c178-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="7c178-120">(Standart çalışma süresinde bile, statik sınıf oluşturucuların yürütme sırasına güvenmemeniz gerekir.)</span><span class="sxs-lookup"><span data-stu-id="7c178-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>

- <span data-ttu-id="7c178-121">Herhangi bir iş parçacığı üzerinde bir `while(true);`arama yapmadan sonsuz döngü (örneğin, ) bir durma noktasına getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c178-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="7c178-122">Benzer şekilde, büyük veya sonsuz beklemeler uygulamayı durdurabilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>

- <span data-ttu-id="7c178-123">Bazı genel başlatma döngüleri .NET Native'de özel durumlar belirlemez.</span><span class="sxs-lookup"><span data-stu-id="7c178-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="7c178-124">Örneğin, aşağıdaki kod standart <xref:System.TypeLoadException> CLR bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="7c178-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="7c178-125">.NET Native'de öyle değil.</span><span class="sxs-lookup"><span data-stu-id="7c178-125">In .NET Native, it doesn't.</span></span>

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- <span data-ttu-id="7c178-126">Bazı durumlarda,.NET Native .NET Framework sınıf kitaplıklarının farklı uygulamalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c178-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="7c178-127">Yöntemden döndürülen bir nesne her zaman döndürülen türün üyelerini uygular.</span><span class="sxs-lookup"><span data-stu-id="7c178-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="7c178-128">Ancak, destek uygulaması farklı olduğundan, diğer .NET Framework platformlarında olduğu gibi aynı tür kümesine döküm mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="7c178-129">Örneğin, bazı durumlarda, döndürülen arabirim <xref:System.Collections.Generic.IEnumerable%601> nesnesini <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> `T[]`' gibi yöntemlerle atamayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c178-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>

- <span data-ttu-id="7c178-130">WinInet önbelleği Windows Mağazası uygulamaları için .NET'te varsayılan olarak etkinleştirilemez, ancak .NET Native'dedir.</span><span class="sxs-lookup"><span data-stu-id="7c178-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="7c178-131">Bu, performansı artırır, ancak çalışma kümesi etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="7c178-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="7c178-132">Geliştirici eylemi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-132">No developer action is necessary.</span></span>

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a><span data-ttu-id="7c178-133">Dinamik programlama farklılıkları</span><span class="sxs-lookup"><span data-stu-id="7c178-133">Dynamic programming differences</span></span>

<span data-ttu-id="7c178-134">.NET Native, maksimum performans için kodu uygulama nın yerel olmasını sağlamak için .NET Framework'den kod olarak statik olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="7c178-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="7c178-135">Ancak, ikili boyutlar küçük kalmak zorunda, bu nedenle tüm .NET Framework getirilemez.</span><span class="sxs-lookup"><span data-stu-id="7c178-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="7c178-136">.NET Native derleyicisi, kullanılmayan koda yapılan başvuruları kaldıran bir bağımlılık azaltıcısı kullanarak bu sınırlamayı çözer.</span><span class="sxs-lookup"><span data-stu-id="7c178-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="7c178-137">Ancak,.NET Native, bu bilgiler derleme zamanında statik olarak çıkarılamadıklarında bazı tür bilgilerini ve kodlarını koruyamaz veya oluşturamaz, ancak bunun yerine çalışma zamanında dinamik olarak alınır.</span><span class="sxs-lookup"><span data-stu-id="7c178-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>

<span data-ttu-id="7c178-138">.NET Native yansıma ve dinamik programlama sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c178-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="7c178-139">Ancak, bu, oluşturulan kod boyutunu çok büyük yapacağından (özellikle .NET Framework'deki genel API'lere yansıtılması desteklendiği için) tüm türler yansıma için işaretlenemez.</span><span class="sxs-lookup"><span data-stu-id="7c178-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="7c178-140">.NET Native derleyicisi, hangi türlerin yansımayı desteklemesi gerektiği konusunda akıllı seçimler yapar ve meta verileri tutar ve yalnızca bu türler için kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c178-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>

<span data-ttu-id="7c178-141">Örneğin, veri bağlama özelliği adlarını işlevlerle eşlenebilmek için bir uygulama gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c178-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="7c178-142">Windows Mağazası uygulamaları için .NET'te, yönetilen türler ve genel kullanıma açık yerel türler için bu özelliği sağlamak için ortak dil çalışma süresi otomatik olarak yansımayı kullanır.</span><span class="sxs-lookup"><span data-stu-id="7c178-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="7c178-143">.NET Native'de derleyici, verileri bağladığınız türler için meta verileri otomatik olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="7c178-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>

<span data-ttu-id="7c178-144">.NET Native derleyicisi, herhangi bir ipucu <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.Dictionary%602>veya yönerge gerektirmeden çalışan ve yaygın olarak kullanılan genel türleri de işleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="7c178-145">[Dinamik](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) anahtar kelime de belirli sınırlar içinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7c178-145">The [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) keyword is also supported within certain limits.</span></span>

> [!NOTE]
> <span data-ttu-id="7c178-146">Uygulamanızı .NET Native'e aktarırken tüm dinamik kod yollarını iyice test etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7c178-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>

<span data-ttu-id="7c178-147">.NET Native için varsayılan yapılandırma çoğu geliştirici için yeterlidir, ancak bazı geliştiriciler çalışma zamanı yönergeleri (.rd.xml) dosyasını kullanarak yapılandırmalarında ince ayar yapmak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="7c178-148">Buna ek olarak, bazı durumlarda ,NET Native derleyicisi hangi meta verilerin yansıtılması için kullanılabilir olması gerektiğini belirleyemiyor ve özellikle aşağıdaki durumlarda ipuçlarına dayanıyor:</span><span class="sxs-lookup"><span data-stu-id="7c178-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>

- <span data-ttu-id="7c178-149">Bazı yapılar <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> statik <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> olarak gibi ve belirlenemez.</span><span class="sxs-lookup"><span data-stu-id="7c178-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>

- <span data-ttu-id="7c178-150">Derleyici anlık açıklamaları belirleyemediğinden, yansıtmak istediğiniz genel bir tür çalışma zamanı yönergeleri tarafından belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7c178-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="7c178-151">Bunun nedeni yalnızca tüm kodun eklenmesi gerektiği değil, genel türlere yansımanın sonsuz bir döngü oluşturabilmesidir (örneğin, genel bir yöntem genel bir türde çağrıldığında).</span><span class="sxs-lookup"><span data-stu-id="7c178-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>

> [!NOTE]
> <span data-ttu-id="7c178-152">Çalışma zamanı yönergeleri bir çalışma zamanı yönergeleri (.rd.xml) dosyasında tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7c178-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="7c178-153">Bu dosyayı kullanma hakkında genel bilgi için [başlarken](getting-started-with-net-native.md)bkz.</span><span class="sxs-lookup"><span data-stu-id="7c178-153">For general information about using this file, see [Getting Started](getting-started-with-net-native.md).</span></span> <span data-ttu-id="7c178-154">Çalışma zamanı yönergeleri hakkında bilgi için [Runtime Yönergeleri (rd.xml) Yapılandırma Dosya Başvurusu'na](runtime-directives-rd-xml-configuration-file-reference.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="7c178-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>

<span data-ttu-id="7c178-155">.NET Native, geliştiricinin varsayılan küme dışındaki türlerin yansımayı desteklemesi gerektiğini belirlemesinde yardımcı olan profil oluşturma araçlarını da içerir.</span><span class="sxs-lookup"><span data-stu-id="7c178-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a><span data-ttu-id="7c178-156">Yansımayla ilgili diğer farklar</span><span class="sxs-lookup"><span data-stu-id="7c178-156">Other reflection-related differences</span></span>

<span data-ttu-id="7c178-157">Windows Mağazası uygulamaları için .NET ile .NET Native arasında yansımayla ilgili diğer bireysel farklar vardır.</span><span class="sxs-lookup"><span data-stu-id="7c178-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>

<span data-ttu-id="7c178-158">.NET Yerel olarak:</span><span class="sxs-lookup"><span data-stu-id="7c178-158">In .NET Native:</span></span>

- <span data-ttu-id="7c178-159">.NET Framework sınıf kitaplığındaki türler ve üyeler üzerinde özel yansıma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="7c178-160">Ancak, kendi özel türlerinizi ve üyelerinizi, üçüncü taraf kitaplıklarında türleri ve üyeleri yansıtabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c178-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>

- <span data-ttu-id="7c178-161">Özellik, <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> iade `false` değerini <xref:System.Reflection.ParameterInfo> temsil eden bir nesne için doğru şekilde döndürür.</span><span class="sxs-lookup"><span data-stu-id="7c178-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="7c178-162">Windows Mağazası uygulamaları için .NET'te geri döner. `true`</span><span class="sxs-lookup"><span data-stu-id="7c178-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="7c178-163">Ara dil (IL) bunu doğrudan desteklemez ve yorumlama dile bırakılır.</span><span class="sxs-lookup"><span data-stu-id="7c178-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>

- <span data-ttu-id="7c178-164">Kamu üyeleri <xref:System.RuntimeFieldHandle> ve <xref:System.RuntimeMethodHandle> yapılar desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="7c178-165">Bu türler yalnızca LINQ, ifade ağaçları ve statik dizi başlatma için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7c178-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>

- <span data-ttu-id="7c178-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType>ve <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> temel sınıflarda gizli üyeleri içerir ve böylece açık geçersiz kılmalar olmadan geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="7c178-167">Bu diğer [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) yöntemleri için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="7c178-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>

- <span data-ttu-id="7c178-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>ve <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> belirli kombinasyonlar (örneğin, bir `byref` dizi nesne) oluşturmaya çalıştığınızda başarısız olmayın.</span><span class="sxs-lookup"><span data-stu-id="7c178-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of `byref` objects).</span></span>

- <span data-ttu-id="7c178-169">İşaretçi parametreleri olan üyeleri çağırmak için yansımayı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7c178-169">You can't use reflection to invoke members that have pointer parameters.</span></span>

- <span data-ttu-id="7c178-170">Bir işaretçi alanını almak veya ayarlamak için yansımayı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7c178-170">You can't use reflection to get or set a pointer field.</span></span>

- <span data-ttu-id="7c178-171">Bağımsız değişken sayısı yanlış sayılsa ve bağımsız değişkenlerden birinin <xref:System.ArgumentException> türü yanlışsa, .NET Native bir <xref:System.Reflection.TargetParameterCountException>. yerine bir</span><span class="sxs-lookup"><span data-stu-id="7c178-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>

- <span data-ttu-id="7c178-172">Özel durumların ikili serileştirilmesi genellikle desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="7c178-173">Sonuç olarak, seri olarak izlenebilir olmayan nesneler <xref:System.Exception.Data%2A?displayProperty=nameWithType> sözlüğe eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="7c178-174">Desteklenmeyen senaryolar ve API'ler</span><span class="sxs-lookup"><span data-stu-id="7c178-174">Unsupported scenarios and APIs</span></span>

<span data-ttu-id="7c178-175">Aşağıdaki bölümlerde, httpclient ve Windows Communication Foundation (WCF) gibi genel geliştirme, interop ve teknolojiler için desteklenmeyen senaryolar ve API'ler listelenir:</span><span class="sxs-lookup"><span data-stu-id="7c178-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>

- [<span data-ttu-id="7c178-176">Genel Geliştirme</span><span class="sxs-lookup"><span data-stu-id="7c178-176">General development</span></span>](#General)

- [<span data-ttu-id="7c178-177">httpİsteC</span><span class="sxs-lookup"><span data-stu-id="7c178-177">HttpClient</span></span>](#HttpClient)

- [<span data-ttu-id="7c178-178">Interop</span><span class="sxs-lookup"><span data-stu-id="7c178-178">Interop</span></span>](#Interop)

- [<span data-ttu-id="7c178-179">Desteklenmeyen API'ler</span><span class="sxs-lookup"><span data-stu-id="7c178-179">Unsupported APIs</span></span>](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a><span data-ttu-id="7c178-180">Genel gelişim farklılıkları</span><span class="sxs-lookup"><span data-stu-id="7c178-180">General development differences</span></span>

<span data-ttu-id="7c178-181">**Değer türleri**</span><span class="sxs-lookup"><span data-stu-id="7c178-181">**Value types**</span></span>

- <span data-ttu-id="7c178-182">Değer türü için <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> yöntemleri ve yöntemleri geçersiz kılarsanız, taban sınıf uygulamalarını aramayın.</span><span class="sxs-lookup"><span data-stu-id="7c178-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="7c178-183">Windows Mağazası uygulamaları için .NET'te bu yöntemler yansımaya dayanır.</span><span class="sxs-lookup"><span data-stu-id="7c178-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="7c178-184">Derleme zamanında ,NET Native çalışma zamanı yansımasına dayanmayan bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c178-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="7c178-185">Bu, bu iki yöntemi geçersiz kılmazsanız, beklendiği gibi çalışacakları anlamına gelir, çünkü .NET Native uygulamayı derleme zamanında oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c178-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="7c178-186">Ancak, bu yöntemleri geçersiz kılmak, ancak taban sınıf uygulamasını çağırmak bir özel durum la sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="7c178-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>

- <span data-ttu-id="7c178-187">1 megabayttan büyük değer türleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-187">Value types larger than 1 megabyte aren't supported.</span></span>

- <span data-ttu-id="7c178-188">Değer türlerinin .NET Native'de parametresiz bir oluşturucusu olamaz.</span><span class="sxs-lookup"><span data-stu-id="7c178-188">Value types can't have a parameterless constructor in .NET Native.</span></span> <span data-ttu-id="7c178-189">(C# ve Visual Basic değer türlerinde parametresiz yapıcıları yasaklar.</span><span class="sxs-lookup"><span data-stu-id="7c178-189">(C# and Visual Basic prohibit parameterless constructors on value types.</span></span> <span data-ttu-id="7c178-190">Ancak, bunlar IL'de oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="7c178-190">However, these can be created in IL.)</span></span>

<span data-ttu-id="7c178-191">**Diziler**</span><span class="sxs-lookup"><span data-stu-id="7c178-191">**Arrays**</span></span>

- <span data-ttu-id="7c178-192">Sıfırdan daha düşük bir sınıra sahip diziler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="7c178-193">Genellikle, bu diziler <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> aşırı yükleme çağırarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7c178-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

- <span data-ttu-id="7c178-194">Çok boyutlu dizilerin dinamik oluşturulması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="7c178-195">Bu tür diziler genellikle bir <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> `lengths` parametre içeren yöntemin aşırı yüklenmesi çağırılarak veya <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> yöntemi çağırarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7c178-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="7c178-196">Dört veya daha fazla boyutu olan çok boyutlu diziler desteklenmez; diğer bir <xref:System.Array.Rank%2A?displayProperty=nameWithType> şey, onların mülkiyet değeri dört veya daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="7c178-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="7c178-197">Bunun yerine [pürüzlü diziler](../../csharp/programming-guide/arrays/jagged-arrays.md) (diziler dizisi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c178-197">Use [jagged arrays](../../csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="7c178-198">Örneğin, `array[x,y,z]` geçersizdir, ancak `array[x][y][z]` değil.</span><span class="sxs-lookup"><span data-stu-id="7c178-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>

- <span data-ttu-id="7c178-199">Çok boyutlu diziler için varyans desteklenmez <xref:System.InvalidCastException> ve çalışma zamanında bir özel durum neden olur.</span><span class="sxs-lookup"><span data-stu-id="7c178-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>

<span data-ttu-id="7c178-200">**Genel Türler**</span><span class="sxs-lookup"><span data-stu-id="7c178-200">**Generics**</span></span>

- <span data-ttu-id="7c178-201">Sonsuz genel tür genişletme derleyici hatasıyla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="7c178-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="7c178-202">Örneğin, bu kodu derlemek için başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="7c178-202">For example, this code fails to compile:</span></span>

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

<span data-ttu-id="7c178-203">**İşaretçiler**</span><span class="sxs-lookup"><span data-stu-id="7c178-203">**Pointers**</span></span>

- <span data-ttu-id="7c178-204">İşaretçiler dizileri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-204">Arrays of pointers aren't supported.</span></span>

- <span data-ttu-id="7c178-205">Bir işaretçi alanını almak veya ayarlamak için yansımayı kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="7c178-205">You can't use reflection to get or set a pointer field.</span></span>

<span data-ttu-id="7c178-206">**Serileştirme**</span><span class="sxs-lookup"><span data-stu-id="7c178-206">**Serialization**</span></span>

<span data-ttu-id="7c178-207">Öznitelik <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7c178-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="7c178-208">Bunun <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> yerine özniteliği kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c178-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>

<span data-ttu-id="7c178-209">**Kaynaklar**</span><span class="sxs-lookup"><span data-stu-id="7c178-209">**Resources**</span></span>

<span data-ttu-id="7c178-210">Yerelleştirilmiş kaynakların <xref:System.Diagnostics.Tracing.EventSource> sınıfla kullanımı desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="7c178-211">Özellik <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> yerelleştirilmiş kaynakları tanımlamaz.</span><span class="sxs-lookup"><span data-stu-id="7c178-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>

<span data-ttu-id="7c178-212">**Temsilciler**</span><span class="sxs-lookup"><span data-stu-id="7c178-212">**Delegates**</span></span>

<span data-ttu-id="7c178-213">`Delegate.BeginInvoke`ve `Delegate.EndInvoke` desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>

<span data-ttu-id="7c178-214">**Çeşitli API'ler**</span><span class="sxs-lookup"><span data-stu-id="7c178-214">**Miscellaneous APIs**</span></span>

- <span data-ttu-id="7c178-215">[TypeInfo.GUID](xref:System.Type.GUID) özelliği, türe <xref:System.PlatformNotSupportedException> bir <xref:System.Runtime.InteropServices.GuidAttribute> öznitelik uygulanmıyorsa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c178-215">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="7c178-216">GUID öncelikle COM desteği için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7c178-216">The GUID is used primarily for COM support.</span></span>

- <span data-ttu-id="7c178-217">Yöntem, <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> .NET Native'de kısa tarihler içeren dizeleri doğru bir şekilde ayrışdırır.</span><span class="sxs-lookup"><span data-stu-id="7c178-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="7c178-218">Ancak, Microsoft Bilgi Bankası [makaleleri KB2803771](https://support.microsoft.com/kb/2803771) ve [KB2803755](https://support.microsoft.com/kb/2803755)açıklanan tarih ve saat ayrıştırma değişiklikleri ile uyumluluğu korumaz.</span><span class="sxs-lookup"><span data-stu-id="7c178-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>

- <span data-ttu-id="7c178-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")` .NET Native'de doğru bir şekilde yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="7c178-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="7c178-220">CLR'nin bazı sürümlerinde, sonuç dizesi yuvarlatılmalı yerine kesilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a><span data-ttu-id="7c178-221">Httpİstek farklılıkları</span><span class="sxs-lookup"><span data-stu-id="7c178-221">HttpClient differences</span></span>

<span data-ttu-id="7c178-222">.NET Native'de <xref:System.Net.Http.HttpClientHandler> sınıf, Windows Mağazası uygulamaları <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> için standart .NET'te kullanılan sınıflar <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> sınıflar yerine dahili olarak WinINet kullanır.</span><span class="sxs-lookup"><span data-stu-id="7c178-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="7c178-223"><xref:System.Net.Http.HttpClientHandler> WinINet, sınıfın desteklediği tüm yapılandırma seçeneklerini desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7c178-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="7c178-224">Sonuç olarak:</span><span class="sxs-lookup"><span data-stu-id="7c178-224">As a result:</span></span>

- <span data-ttu-id="7c178-225">.NET Native'de <xref:System.Net.Http.HttpClientHandler> `false` iade edilen bazı yetenek özellikleri, windows mağazası uygulamaları için standart .NET'te geri dönerken. `true`</span><span class="sxs-lookup"><span data-stu-id="7c178-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>

- <span data-ttu-id="7c178-226">Yapılandırma özelliği `get` erişimcilerinden bazıları ,.NET Native'de windows mağazası uygulamaları için .NET'teki varsayılan yapılandırılabilir değerden farklı sabit bir değer döndürer.</span><span class="sxs-lookup"><span data-stu-id="7c178-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>

<span data-ttu-id="7c178-227">Bazı ek davranış farklılıkları aşağıdaki alt bölümlerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="7c178-227">Some additional behavior differences are covered in the following subsections.</span></span>

<span data-ttu-id="7c178-228">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="7c178-228">**Proxy**</span></span>

<span data-ttu-id="7c178-229">Sınıf, <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> proxy'yi istek başına yapılandırmayı veya geçersiz kılmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="7c178-229">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="7c178-230">Bu, .NET Native'deki tüm <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> isteklerin, özelliğin değerine bağlı olarak sistem tarafından yapılandırılmış proxy sunucusunu kullandığı veya proxy sunucusu kullanmadığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="7c178-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="7c178-231">Windows Mağazası uygulamaları için .NET'te proxy <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> sunucusu özellik tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="7c178-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="7c178-232">.NET Native'de, <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> özel <xref:System.PlatformNotSupportedException> durum `null` atmak dışında bir değer ekidir.</span><span class="sxs-lookup"><span data-stu-id="7c178-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="7c178-233">Özellik <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> .NET Native'de döndürürken, `false` Windows Mağazası uygulamaları için standart .NET Framework'de döner. `true`</span><span class="sxs-lookup"><span data-stu-id="7c178-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>

<span data-ttu-id="7c178-234">**Otomatik yeniden yönlendirme**</span><span class="sxs-lookup"><span data-stu-id="7c178-234">**Automatic redirection**</span></span>

<span data-ttu-id="7c178-235">Sınıf, <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> en fazla otomatik yeniden yönlendirme sayısının yapılandırılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="7c178-235">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="7c178-236">Özelliğin <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> değeri, Windows Mağazası uygulamaları için standart .NET'te varsayılan olarak 50'dir ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="7c178-237">.NET Native'de, bu özelliğin değeri 10'dur ve <xref:System.PlatformNotSupportedException> değiştirmeye çalışmak bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c178-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="7c178-238">Özellik <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> .NET Native'de döndürürken, `false` Windows Mağazası uygulamaları için .NET'te döner. `true`</span><span class="sxs-lookup"><span data-stu-id="7c178-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>

<span data-ttu-id="7c178-239">**Otomatik dekompresyon**</span><span class="sxs-lookup"><span data-stu-id="7c178-239">**Automatic decompression**</span></span>

<span data-ttu-id="7c178-240">.NET Windows Mağazası uygulamaları için <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> özelliği <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>her <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>ikisi <xref:System.Net.DecompressionMethods.None>ve , veya .</span><span class="sxs-lookup"><span data-stu-id="7c178-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="7c178-241">.NET Native <xref:System.Net.DecompressionMethods.Deflate> yalnızca <xref:System.Net.DecompressionMethods.GZip>' <xref:System.Net.DecompressionMethods.None>veya .</span><span class="sxs-lookup"><span data-stu-id="7c178-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="7c178-242"><xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> Ya <xref:System.Net.DecompressionMethods.Deflate> da <xref:System.Net.DecompressionMethods.GZip> tek başına özelliği ayarlamak için çalışırken <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>sessizce hem de ayarlar .</span><span class="sxs-lookup"><span data-stu-id="7c178-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>

<span data-ttu-id="7c178-243">**Çerezler**</span><span class="sxs-lookup"><span data-stu-id="7c178-243">**Cookies**</span></span>

<span data-ttu-id="7c178-244">Çerez işleme wininet <xref:System.Net.Http.HttpClient> tarafından aynı anda gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="7c178-245"><xref:System.Net.CookieContainer> Çerezler WinINet çerez önbelleğindeki çerezlerle birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="7c178-246">Çerezin kaldırılması <xref:System.Net.CookieContainer> çerezin <xref:System.Net.Http.HttpClient> gönderilmesini engeller, ancak çerez WinINet tarafından zaten görüldüyse ve tanımlama bilgileri kullanıcı tarafından silinmediyse, WinINet çerezi gönderir.</span><span class="sxs-lookup"><span data-stu-id="7c178-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="7c178-247">Bir çerezi , veya <xref:System.Net.Http.HttpClient> <xref:System.Net.Http.HttpClientHandler> <xref:System.Net.CookieContainer> API kullanarak WinINet'ten programlı bir şekilde kaldırmak mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="7c178-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="7c178-248">Özelliği <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> yalnızca `false` tanımlama <xref:System.Net.Http.HttpClient> bilgisi göndermeyi durdurmaya neden olacak şekilde ayarlamak; WinINet yine de istekteki çerezlerini ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>

<span data-ttu-id="7c178-249">**Kimlik Bilgileri**</span><span class="sxs-lookup"><span data-stu-id="7c178-249">**Credentials**</span></span>

<span data-ttu-id="7c178-250">Windows Mağazası uygulamaları için .NET'te ve <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> özellikleri bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="7c178-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="7c178-251">Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özellik <xref:System.Net.ICredentials> arabirimi uygulayan herhangi bir nesneyi kabul eder.</span><span class="sxs-lookup"><span data-stu-id="7c178-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="7c178-252">.NET Native'de, <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> özelliği `true` <xref:System.Net.Http.HttpClientHandler.Credentials%2A> `null`niçin .</span><span class="sxs-lookup"><span data-stu-id="7c178-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="7c178-253">Buna ek <xref:System.Net.Http.HttpClientHandler.Credentials%2A> olarak, özellik yalnızca `null` <xref:System.Net.CredentialCache.DefaultCredentials%2A>, veya tür <xref:System.Net.NetworkCredential>bir nesne olarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="7c178-254">Atanherhangi bir <xref:System.Net.ICredentials> nesne, en popüler <xref:System.Net.CredentialCache>olan , <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği ne <xref:System.PlatformNotSupportedException>atar .</span><span class="sxs-lookup"><span data-stu-id="7c178-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="7c178-255">**Diğer desteklenmeyen veya yapılandırılamayan özellikler**</span><span class="sxs-lookup"><span data-stu-id="7c178-255">**Other unsupported or unconfigurable features**</span></span>

<span data-ttu-id="7c178-256">.NET Yerel olarak:</span><span class="sxs-lookup"><span data-stu-id="7c178-256">In .NET Native:</span></span>

- <span data-ttu-id="7c178-257">Özelliğin <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> değeri her <xref:System.Net.Http.ClientCertificateOption.Automatic>zaman .</span><span class="sxs-lookup"><span data-stu-id="7c178-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="7c178-258">Windows Mağazası uygulamaları için .NET'te varsayılan <xref:System.Net.Http.ClientCertificateOption.Manual>değer.</span><span class="sxs-lookup"><span data-stu-id="7c178-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>

- <span data-ttu-id="7c178-259">Özellik <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> yapılandırılamaz.</span><span class="sxs-lookup"><span data-stu-id="7c178-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>

- <span data-ttu-id="7c178-260">Mülkiyet <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> her `true`zaman .</span><span class="sxs-lookup"><span data-stu-id="7c178-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="7c178-261">Windows Mağazası uygulamaları için .NET'te varsayılan `false`değer.</span><span class="sxs-lookup"><span data-stu-id="7c178-261">In .NET for Windows Store apps, the default is `false`.</span></span>

- <span data-ttu-id="7c178-262">Yanıtlardaki `SetCookie2` üstbilgi eski olarak yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="7c178-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>

<a name="Interop"></a>
### <a name="interop-differences"></a><span data-ttu-id="7c178-263">Interop farkları</span><span class="sxs-lookup"><span data-stu-id="7c178-263">Interop differences</span></span>
 <span data-ttu-id="7c178-264">**Amortismana UYru'lar**</span><span class="sxs-lookup"><span data-stu-id="7c178-264">**Deprecated APIs**</span></span>

 <span data-ttu-id="7c178-265">Yönetilen kodla birlikte çalışabilirlik için seyrek kullanılan bir dizi API'ler amortismana kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="7c178-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="7c178-266">.NET Native ile kullanıldığında, bu API'ler bir <xref:System.NotImplementedException> özel <xref:System.PlatformNotSupportedException> durum veya özel durum atabilir veya derleyici hatasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="7c178-267">Windows Mağazası uygulamaları için .NET'te bu API'ler eski olarak işaretlenir, ancak bunları çağırmak derleyici hatası yerine derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7c178-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>

 <span data-ttu-id="7c178-268">Marshaling için `VARIANT` amortismana küçümsülen API'ler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7c178-268">Deprecated APIs for `VARIANT` marshaling include:</span></span>

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <span data-ttu-id="7c178-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>desteklenir, ancak [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) veya `byref` türevleri ile kullanıldığında gibi bazı senaryolarda bir özel durum atar.</span><span class="sxs-lookup"><span data-stu-id="7c178-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or `byref` variants.</span></span>

 <span data-ttu-id="7c178-270">[IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) desteği için amortismana hazır API'ler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7c178-270">Deprecated APIs for [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

<span data-ttu-id="7c178-271">Klasik COM etkinlikleri için amortismana hazır API'ler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7c178-271">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<span data-ttu-id="7c178-272">.NET Native'de desteklenmeyen <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> arabirimdeki amortismana kılmış API'ler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7c178-272">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>

- <span data-ttu-id="7c178-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(tüm üyeler)</span><span class="sxs-lookup"><span data-stu-id="7c178-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="7c178-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(tüm üyeler)</span><span class="sxs-lookup"><span data-stu-id="7c178-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="7c178-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(tüm üyeler)</span><span class="sxs-lookup"><span data-stu-id="7c178-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

<span data-ttu-id="7c178-276">Diğer desteklenmeyen interop özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7c178-276">Other unsupported interop features include:</span></span>

- <span data-ttu-id="7c178-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(tüm üyeler)</span><span class="sxs-lookup"><span data-stu-id="7c178-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="7c178-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(tüm üyeler)</span><span class="sxs-lookup"><span data-stu-id="7c178-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 <span data-ttu-id="7c178-279">Nadiren kullanılan mareşalAP'lar:</span><span class="sxs-lookup"><span data-stu-id="7c178-279">Rarely used marshaling APIs:</span></span>

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 <span data-ttu-id="7c178-280">**Platform çağırma ve COM interop uyumluluğu**</span><span class="sxs-lookup"><span data-stu-id="7c178-280">**Platform invoke and COM interop compatibility**</span></span>

 <span data-ttu-id="7c178-281">Çoğu platform çağrılabilir ve COM interop senaryoları hala .NET Native desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7c178-281">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="7c178-282">Özellikle, Windows Runtime (WinRT) API'leri ile birlikte çalışabilirlik ve Windows Runtime için gereken tüm mareşallik desteklenir.</span><span class="sxs-lookup"><span data-stu-id="7c178-282">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="7c178-283">Bu, şunlar için mareşal desteği içerir:</span><span class="sxs-lookup"><span data-stu-id="7c178-283">This includes marshaling support for:</span></span>

- <span data-ttu-id="7c178-284">Diziler (dahil) <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7c178-284">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>

- `BStr`

- <span data-ttu-id="7c178-285">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="7c178-285">Delegates</span></span>

- <span data-ttu-id="7c178-286">Dizeleri (Unicode, Ansi ve HSTRING)</span><span class="sxs-lookup"><span data-stu-id="7c178-286">Strings (Unicode, Ansi, and HSTRING)</span></span>

- <span data-ttu-id="7c178-287">Structs`byref` ( `byval`ve )</span><span class="sxs-lookup"><span data-stu-id="7c178-287">Structs (`byref` and `byval`)</span></span>

- <span data-ttu-id="7c178-288">Birleşimler</span><span class="sxs-lookup"><span data-stu-id="7c178-288">Unions</span></span>

- <span data-ttu-id="7c178-289">Win32 kulpları</span><span class="sxs-lookup"><span data-stu-id="7c178-289">Win32 handles</span></span>

- <span data-ttu-id="7c178-290">Tüm WinRT yapıları</span><span class="sxs-lookup"><span data-stu-id="7c178-290">All WinRT constructs</span></span>

- <span data-ttu-id="7c178-291">Varyant türlerini mareşalleme için kısmi destek.</span><span class="sxs-lookup"><span data-stu-id="7c178-291">Partial support for marshaling variant types.</span></span> <span data-ttu-id="7c178-292">Aşağıdakiler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="7c178-292">The following are supported:</span></span>

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [<span data-ttu-id="7c178-293">IUnknown</span><span class="sxs-lookup"><span data-stu-id="7c178-293">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

<span data-ttu-id="7c178-294">Ancak, .NET Native aşağıdakileri desteklemez:</span><span class="sxs-lookup"><span data-stu-id="7c178-294">However, .NET Native doesn't support the following:</span></span>

- <span data-ttu-id="7c178-295">Klasik COM olaylarını kullanma</span><span class="sxs-lookup"><span data-stu-id="7c178-295">Using classic COM events</span></span>

- <span data-ttu-id="7c178-296"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> Yönetilen bir türde arabirimi uygulama</span><span class="sxs-lookup"><span data-stu-id="7c178-296">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>

- <span data-ttu-id="7c178-297">[Öznitelik](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) aracılığıyla yönetilen bir türüzerinde <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> IDispatch arabiriminin uygulanması.</span><span class="sxs-lookup"><span data-stu-id="7c178-297">Implementing the [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="7c178-298">Ancak, COM nesnelerini aracılığıyla `IDispatch`arayamadığınızı ve yönetilen nesneniz uygulayamaz. `IDispatch`</span><span class="sxs-lookup"><span data-stu-id="7c178-298">However, you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>

<span data-ttu-id="7c178-299">Bir platform çağırma yöntemi çağırmak için yansıma kullanma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-299">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="7c178-300">Yöntem çağrısını başka bir yöntemde sararak ve bunun yerine sarmalayıcıyı aramak için yansımayı kullanarak bu sınırlamayı çözebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7c178-300">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="7c178-301">Windows Mağazası uygulamaları için .NET API'lerinden diğer farklar</span><span class="sxs-lookup"><span data-stu-id="7c178-301">Other differences from .NET APIs for Windows Store apps</span></span>

<span data-ttu-id="7c178-302">Bu bölümde,.NET Native'de desteklenmeyen kalan API'ler listelenir.</span><span class="sxs-lookup"><span data-stu-id="7c178-302">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="7c178-303">Desteklenmeyen API'lerin en büyük kümesi Windows Communication Foundation (WCF) API'leridir.</span><span class="sxs-lookup"><span data-stu-id="7c178-303">The largest set of the unsupported APIs is the Windows Communication Foundation (WCF) APIs.</span></span>

<span data-ttu-id="7c178-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="7c178-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>

<span data-ttu-id="7c178-305">.NET Native'de ve <xref:System.ComponentModel.DataAnnotations> <xref:System.ComponentModel.DataAnnotations.Schema> ad alanlarındaki türler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-305">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="7c178-306">Bunlar, Windows 8 için Windows Mağazası uygulamaları için .NET'te bulunan aşağıdaki türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="7c178-306">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 <span data-ttu-id="7c178-307">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="7c178-307">**Visual Basic**</span></span>

<span data-ttu-id="7c178-308">Visual Basic şu anda .NET Native'de desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7c178-308">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="7c178-309">.NET Native'de aşağıdaki türler <xref:Microsoft.VisualBasic> ve <xref:Microsoft.VisualBasic.CompilerServices> ad boşlukları bulunmamaktadır:</span><span class="sxs-lookup"><span data-stu-id="7c178-309">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

<span data-ttu-id="7c178-310">**Yansıma Bağlamı (System.Reflection.Context namespace)**</span><span class="sxs-lookup"><span data-stu-id="7c178-310">**Reflection Context (System.Reflection.Context namespace)**</span></span>

<span data-ttu-id="7c178-311">Sınıf <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> .NET Native'de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-311">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>

<span data-ttu-id="7c178-312">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="7c178-312">**RTC (System.Net.Http.Rtc)**</span></span>

<span data-ttu-id="7c178-313">Sınıf `System.Net.Http.RtcRequestFactory` .NET Native'de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-313">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>

<span data-ttu-id="7c178-314">**Windows İletişim Vakfı (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="7c178-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>

<span data-ttu-id="7c178-315">[System.ServiceModel.\* ad alanlarındaki](xref:System.ServiceModel) türler .NET Native'de desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7c178-315">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="7c178-316">Bunlar aşağıdaki türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="7c178-316">These include the following types:</span></span>

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a><span data-ttu-id="7c178-317">Serializers farklılıklar</span><span class="sxs-lookup"><span data-stu-id="7c178-317">Differences in serializers</span></span>

<span data-ttu-id="7c178-318">Aşağıdaki farklar , <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>ve sınıflar ile serileştirme ve <xref:System.Xml.Serialization.XmlSerializer> deserialization ile ilgilidir:</span><span class="sxs-lookup"><span data-stu-id="7c178-318">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>

- <span data-ttu-id="7c178-319">.NET Native'de <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve <xref:System.Runtime.Serialization.DataContractSerializer> türü kök serileştirme türü olmayan bir taban sınıf üyesi olan türemiş bir sınıfı serihale getirmek veya deserialize etmek için başarısız.</span><span class="sxs-lookup"><span data-stu-id="7c178-319">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="7c178-320">Örneğin, aşağıdaki kodda, bir hatayla sonuçlanırken `Y` sonuçları seri hale getirmeye veya deserialize etmeye çalışmak:</span><span class="sxs-lookup"><span data-stu-id="7c178-320">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  <span data-ttu-id="7c178-321">Tür `InnerType` serileştirici tarafından bilinmiyor, çünkü taban sınıfın üyeleri serileştirme sırasında geçiş yapmıyor.</span><span class="sxs-lookup"><span data-stu-id="7c178-321">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>

- <span data-ttu-id="7c178-322"><xref:System.Runtime.Serialization.DataContractSerializer>ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> arabirimi uygulayan bir sınıfı veya <xref:System.Collections.Generic.IEnumerable%601> yapıyı seri hale getirmekte başarısız olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-322"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="7c178-323">Örneğin, aşağıdaki türler serihale veya deserialize başarısız:</span><span class="sxs-lookup"><span data-stu-id="7c178-323">For example, the following types fail to serialize or deserialize:</span></span>

- <span data-ttu-id="7c178-324"><xref:System.Xml.Serialization.XmlSerializer>serihale edilecek nesnenin tam türünü bilmediğinden, aşağıdaki nesne değerini serihale getiremez:</span><span class="sxs-lookup"><span data-stu-id="7c178-324"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>

- <span data-ttu-id="7c178-325"><xref:System.Xml.Serialization.XmlSerializer>serileştirilmiş nesnenin <xref:System.Xml.XmlQualifiedName>türü.</span><span class="sxs-lookup"><span data-stu-id="7c178-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>

- <span data-ttu-id="7c178-326">Tüm serializers<xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>( <xref:System.Xml.Serialization.XmlSerializer>, , ve ) türü <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> veya içeren <xref:System.Xml.Linq.XElement>bir tür için serileştirme kodu oluşturmak için başarısız .</span><span class="sxs-lookup"><span data-stu-id="7c178-326">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="7c178-327">Bunun yerine yapı zamanı hatalarını görüntülerler.</span><span class="sxs-lookup"><span data-stu-id="7c178-327">They display build-time errors instead.</span></span>

- <span data-ttu-id="7c178-328">Serileştirme türlerinin aşağıdaki oluşturucularının beklendiği gibi çalışması garanti değildir:</span><span class="sxs-lookup"><span data-stu-id="7c178-328">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <span data-ttu-id="7c178-329"><xref:System.Xml.Serialization.XmlSerializer>aşağıdaki özniteliklerden herhangi biriyle atfedilen yöntemleri olan bir tür için kod oluşturmak için başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="7c178-329"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <span data-ttu-id="7c178-330"><xref:System.Xml.Serialization.XmlSerializer>özel serileştirme <xref:System.Xml.Serialization.IXmlSerializable> arabirimini onurlandırmaz.</span><span class="sxs-lookup"><span data-stu-id="7c178-330"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="7c178-331">Bu arabirimi uygulayan bir sınıfvarsa, <xref:System.Xml.Serialization.XmlSerializer> türü düz eski CLR nesnesi (POCO) türünü dikkate alır ve yalnızca ortak özelliklerini serileştirir.</span><span class="sxs-lookup"><span data-stu-id="7c178-331">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>

- <span data-ttu-id="7c178-332">Düz bir <xref:System.Exception> nesneyi seri hale <xref:System.Runtime.Serialization.DataContractSerializer> getirmek <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>iyi çalışmaz ve .</span><span class="sxs-lookup"><span data-stu-id="7c178-332">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>

## <a name="visual-studio-differences"></a><span data-ttu-id="7c178-333">Visual Studio farklılıkları</span><span class="sxs-lookup"><span data-stu-id="7c178-333">Visual Studio differences</span></span>

<span data-ttu-id="7c178-334">**Özel durumlar ve hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="7c178-334">**Exceptions and debugging**</span></span>

<span data-ttu-id="7c178-335">Hata ayıklamada .NET Native kullanarak derlenen uygulamaları çalıştırırken, aşağıdaki özel durum türleri için ilk şans özel durumları etkinleştirilir:</span><span class="sxs-lookup"><span data-stu-id="7c178-335">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

<span data-ttu-id="7c178-336">**Uygulama oluşturma**</span><span class="sxs-lookup"><span data-stu-id="7c178-336">**Building apps**</span></span>

<span data-ttu-id="7c178-337">Visual Studio tarafından varsayılan olarak kullanılan x86 yapı araçlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c178-337">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="7c178-338">C:\Program Files (x86)\MSBuild\12.0\bin\amd64 bulunur AMD64 MSBuild araçları, kullanmanızı öneririz; bunlar yapı sorunları yaratabilir.</span><span class="sxs-lookup"><span data-stu-id="7c178-338">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>

<span data-ttu-id="7c178-339">**Profilleyicilerini**</span><span class="sxs-lookup"><span data-stu-id="7c178-339">**Profilers**</span></span>

- <span data-ttu-id="7c178-340">Visual Studio CPU Profiler ve XAML Memory Profiler Just-My-Code'u doğru görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="7c178-340">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>

- <span data-ttu-id="7c178-341">XAML Memory Profiler yönetilen yığın verilerini doğru bir şekilde görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="7c178-341">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>

- <span data-ttu-id="7c178-342">CPU Profiler modülleri doğru tanımlamaz ve önceden belirlenmiş işlev adlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7c178-342">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>

<span data-ttu-id="7c178-343">**Ünite Test Kitaplığı projeleri**</span><span class="sxs-lookup"><span data-stu-id="7c178-343">**Unit Test Library projects**</span></span>

<span data-ttu-id="7c178-344">Bir Windows Mağazası uygulamaları projesi için Birim Test Kitaplığı'nda .NET Native'i etkinleştirmek desteklenmez ve projenin oluşturulmasında başarısız olması nedeniyle.</span><span class="sxs-lookup"><span data-stu-id="7c178-344">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c178-345">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c178-345">See also</span></span>

- [<span data-ttu-id="7c178-346">Başlarken</span><span class="sxs-lookup"><span data-stu-id="7c178-346">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="7c178-347">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="7c178-347">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="7c178-348">.NET Windows Mağazası uygulamalarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="7c178-348">.NET For Windows Store apps overview</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [<span data-ttu-id="7c178-349">Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği</span><span class="sxs-lookup"><span data-stu-id="7c178-349">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
