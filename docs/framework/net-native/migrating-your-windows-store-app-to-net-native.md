---
description: 'Hakkında daha fazla bilgi edinin: .NET Native Windows mağazası uygulamanızı geçirme'
title: Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 39f8427474b37c42d856366bf4e4d677ba77e7f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738721"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a><span data-ttu-id="0c396-103">Windows mağazası uygulamanızı .NET Native geçirin</span><span class="sxs-lookup"><span data-stu-id="0c396-103">Migrate Your Windows Store App to .NET Native</span></span>

<span data-ttu-id="0c396-104">.NET Native, Windows Mağazası 'nda veya geliştiricinin bilgisayarındaki uygulamaların statik derlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c396-104">.NET Native provides static compilation of apps in the Windows Store or on the developer's computer.</span></span> <span data-ttu-id="0c396-105">Bu, tam zamanında (JıT) derleyici veya cihazdaki [Yerel Görüntü Oluşturucu (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) tarafından Windows Mağazası uygulamaları için gerçekleştirilen dinamik derlemeden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="0c396-105">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="0c396-106">Farklılıklara rağmen .NET Native, [Windows Mağazası uygulamaları için .net](/previous-versions/windows/apps/br230302(v=vs.140))ile uyumluluğu sürdürmenize çalışır.</span><span class="sxs-lookup"><span data-stu-id="0c396-106">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](/previous-versions/windows/apps/br230302(v=vs.140)).</span></span> <span data-ttu-id="0c396-107">Çoğu bölümde, Windows Mağazası uygulamaları için .NET üzerinde çalışan şeyler .NET Native de çalışır.</span><span class="sxs-lookup"><span data-stu-id="0c396-107">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="0c396-108">Ancak bazı durumlarda, davranış değişiklikleriyle karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c396-108">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="0c396-109">Bu belgede, Windows Mağazası uygulamaları için standart .NET ve aşağıdaki alanlardaki .NET Native arasındaki farklar ele alınmaktadır:</span><span class="sxs-lookup"><span data-stu-id="0c396-109">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>

- [<span data-ttu-id="0c396-110">Genel çalışma zamanı farklılıkları</span><span class="sxs-lookup"><span data-stu-id="0c396-110">General runtime differences</span></span>](#Runtime)

- [<span data-ttu-id="0c396-111">Dinamik programlama farkları</span><span class="sxs-lookup"><span data-stu-id="0c396-111">Dynamic programming differences</span></span>](#Dynamic)

- [<span data-ttu-id="0c396-112">Yansıma ile ilgili diğer farklar</span><span class="sxs-lookup"><span data-stu-id="0c396-112">Other reflection-related differences</span></span>](#Reflection)

- [<span data-ttu-id="0c396-113">Desteklenmeyen senaryolar ve API 'Ler</span><span class="sxs-lookup"><span data-stu-id="0c396-113">Unsupported scenarios and APIs</span></span>](#Unsupported)

- [<span data-ttu-id="0c396-114">Visual Studio farklılıkları</span><span class="sxs-lookup"><span data-stu-id="0c396-114">Visual Studio differences</span></span>](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a><span data-ttu-id="0c396-115">Genel çalışma zamanı farklılıkları</span><span class="sxs-lookup"><span data-stu-id="0c396-115">General runtime differences</span></span>

- <span data-ttu-id="0c396-116"><xref:System.TypeLoadException>Bir uygulama ortak dil çalışma zamanı (CLR) üzerinde çalışırken JIT derleyicisi tarafından oluşturulan özel durumlar, genellikle .NET Native tarafından işlendiğinde derleme zamanı hatalarına neden oluşur.</span><span class="sxs-lookup"><span data-stu-id="0c396-116">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>

- <span data-ttu-id="0c396-117"><xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType>Uygulamanın kullanıcı arabirimi iş parçacığından yöntemi çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="0c396-117">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="0c396-118">Bu, .NET Native kilitlenmeye neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-118">This can result in a deadlock on .NET Native.</span></span>

- <span data-ttu-id="0c396-119">Statik sınıf Oluşturucu çağırma sıralamasına güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="0c396-119">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="0c396-120">.NET Native, çağırma sırası standart çalışma zamanındaki siparişten farklıdır.</span><span class="sxs-lookup"><span data-stu-id="0c396-120">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="0c396-121">(Standart çalışma zamanı ile bile, statik sınıf oluşturucuların yürütme sırasına dayanmamanız gerekir.)</span><span class="sxs-lookup"><span data-stu-id="0c396-121">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>

- <span data-ttu-id="0c396-122">Herhangi bir iş parçacığında çağrı yapma (örneğin,) çağrısı yapılmadan sonsuz döngü `while(true);` , uygulamayı bir durabilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-122">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="0c396-123">Benzer şekilde, büyük veya sonsuz bir bekleme süresi uygulamayı bir durabilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-123">Similarly, large or infinite waits may bring the app to a halt.</span></span>

- <span data-ttu-id="0c396-124">Belirli genel başlatma döngüleri .NET Native özel durum oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="0c396-124">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="0c396-125">Örneğin, aşağıdaki kod <xref:System.TypeLoadException> standart CLR üzerinde bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0c396-125">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="0c396-126">.NET Native, değildir.</span><span class="sxs-lookup"><span data-stu-id="0c396-126">In .NET Native, it doesn't.</span></span>

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- <span data-ttu-id="0c396-127">Bazı durumlarda .NET Native, .NET Framework sınıf kitaplıklarının farklı uygulamalarını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c396-127">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="0c396-128">Bir yöntemden döndürülen bir nesne, döndürülen türün üyelerini her zaman uygular.</span><span class="sxs-lookup"><span data-stu-id="0c396-128">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="0c396-129">Ancak, kendi yedekleme uygulamaları farklı olduğundan, diğer .NET Framework platformlarındaki gibi aynı tür kümesine de atama yapamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0c396-129">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="0c396-130">Örneğin, bazı durumlarda, <xref:System.Collections.Generic.IEnumerable%601> veya gibi yöntemler tarafından döndürülen arabirim nesnesini de çevirebilirsiniz <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> `T[]` .</span><span class="sxs-lookup"><span data-stu-id="0c396-130">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>

- <span data-ttu-id="0c396-131">WinInet önbelleği, Windows Mağazası uygulamaları için .NET ' te varsayılan olarak etkinleştirilmez, ancak .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0c396-131">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="0c396-132">Bu, performansı artırır ancak çalışma kümesi etkilerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="0c396-132">This improves performance but has working set implications.</span></span> <span data-ttu-id="0c396-133">Geliştirici eylemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="0c396-133">No developer action is necessary.</span></span>

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a><span data-ttu-id="0c396-134">Dinamik programlama farkları</span><span class="sxs-lookup"><span data-stu-id="0c396-134">Dynamic programming differences</span></span>

<span data-ttu-id="0c396-135">Kod, en yüksek performans için yerel koda .NET Framework kodda statik olarak bağlantı .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0c396-135">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="0c396-136">Ancak, ikili boyutların küçük kalması gerekir, bu nedenle tüm .NET Framework alınamaz.</span><span class="sxs-lookup"><span data-stu-id="0c396-136">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="0c396-137">.NET Native derleyici, kullanılmayan koda başvuruları kaldıran bir Dependency Reducer kullanarak bu sınırlamayı çözer.</span><span class="sxs-lookup"><span data-stu-id="0c396-137">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="0c396-138">Ancak .NET Native, bu bilgiler derleme zamanında statik olarak çıkarsanamıyor, ancak çalışma zamanında dinamik olarak alınırsa, bazı tür bilgileri ve kod üretilemez.</span><span class="sxs-lookup"><span data-stu-id="0c396-138">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>

<span data-ttu-id="0c396-139">.NET Native, yansıma ve dinamik programlamayı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="0c396-139">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="0c396-140">Ancak, oluşturulan kod boyutunu çok büyük hale getirmek (özellikle de .NET Framework ortak API 'lerde yansıtma desteklendiğinden) için tüm türler yansıma için işaretlenemez.</span><span class="sxs-lookup"><span data-stu-id="0c396-140">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="0c396-141">.NET Native derleyicisi, hangi türlerin yansıma desteklemesi gerektiği konusunda akıllı seçimler yapar ve meta verileri korur ve yalnızca bu türler için kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0c396-141">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>

<span data-ttu-id="0c396-142">Örneğin, veri bağlama bir uygulamanın özellik adlarını işlevlerle eşleştirebilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="0c396-142">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="0c396-143">Windows Mağazası uygulamaları için .NET sürümünde ortak dil çalışma zamanı, bu özelliği yönetilen türler ve genel kullanıma açık yerel türler için otomatik olarak yansıma kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c396-143">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="0c396-144">.NET Native, derleyici, verileri bağlacağınız türler için otomatik olarak meta veriler içerir.</span><span class="sxs-lookup"><span data-stu-id="0c396-144">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>

<span data-ttu-id="0c396-145">.NET Native derleyici, ve gibi yaygın olarak kullanılan genel türleri de işleyebilir <xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602> herhangi bir ipucu veya yönergesi gerekmeden çalışır.</span><span class="sxs-lookup"><span data-stu-id="0c396-145">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="0c396-146">[Dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) anahtar sözcüğü belirli sınırlar içinde de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0c396-146">The [dynamic](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) keyword is also supported within certain limits.</span></span>

> [!NOTE]
> <span data-ttu-id="0c396-147">Uygulamanızı .NET Native taşıma sırasında tüm dinamik kod yollarını iyice test etmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="0c396-147">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>

<span data-ttu-id="0c396-148">.NET Native için varsayılan yapılandırma çoğu geliştirici için yeterlidir, ancak bazı geliştiriciler çalışma zamanı yönergeleri (.rd.xml) dosyası kullanarak yapılandırmalarını ince ayar yapmak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-148">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="0c396-149">Ayrıca, bazı durumlarda .NET Native derleyicisi, özellikle aşağıdaki durumlarda, yansıma için hangi meta verilerin kullanılabilir olması gerektiğini belirleyemez ve ipuçlarına dayanır:</span><span class="sxs-lookup"><span data-stu-id="0c396-149">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>

- <span data-ttu-id="0c396-150">Ve gibi bazı <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yapılar <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> statik olarak belirlenemez.</span><span class="sxs-lookup"><span data-stu-id="0c396-150">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>

- <span data-ttu-id="0c396-151">Derleyici örneklemeleri belirleyemediği için, üzerinde yansıtmak istediğiniz genel bir türün çalışma zamanı yönergeleri tarafından belirtilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="0c396-151">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="0c396-152">Bu, tüm kodun dahil olması gerektiğinden, ancak genel türlerde yansıma bir sonsuz döngüye (örneğin, genel bir tür üzerinde çağrıldığında genel bir yöntem çağrıldığında) sahip olduğu için bu değildir.</span><span class="sxs-lookup"><span data-stu-id="0c396-152">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>

> [!NOTE]
> <span data-ttu-id="0c396-153">Çalışma zamanı yönergeleri, bir çalışma zamanı yönergeleri (.rd.xml) dosyasında tanımlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0c396-153">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="0c396-154">Bu dosyayı kullanma hakkında genel bilgi için [bkz. Başlarken](getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="0c396-154">For general information about using this file, see [Getting Started](getting-started-with-net-native.md).</span></span> <span data-ttu-id="0c396-155">Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="0c396-155">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md).</span></span>

<span data-ttu-id="0c396-156">.NET Native Ayrıca, geliştiricinin varsayılan küme dışında hangi türlerin yansıma destekleceğini belirlemesine yardımcı olan profil oluşturma araçlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="0c396-156">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a><span data-ttu-id="0c396-157">Yansıma ile ilgili diğer farklar</span><span class="sxs-lookup"><span data-stu-id="0c396-157">Other reflection-related differences</span></span>

<span data-ttu-id="0c396-158">Windows Mağazası uygulamaları ve .NET Native için .NET arasındaki davranıştaki farklı yansıma ile ilgili birçok fark vardır.</span><span class="sxs-lookup"><span data-stu-id="0c396-158">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>

<span data-ttu-id="0c396-159">.NET Native:</span><span class="sxs-lookup"><span data-stu-id="0c396-159">In .NET Native:</span></span>

- <span data-ttu-id="0c396-160">.NET Framework sınıf kitaplığındaki türler ve Üyeler üzerinde özel yansıma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-160">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="0c396-161">Bununla birlikte, kendi özel türlerinizin ve üyelerinizin yanı sıra üçüncü taraf kitaplıklardaki türler ve Üyeler üzerinde de yansıtma yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c396-161">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>

- <span data-ttu-id="0c396-162"><xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType>Özelliği, `false` <xref:System.Reflection.ParameterInfo> dönüş değerini temsil eden bir nesne için doğru şekilde döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0c396-162">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="0c396-163">Windows Mağazası uygulamaları için .NET ' te, döndürür `true` .</span><span class="sxs-lookup"><span data-stu-id="0c396-163">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="0c396-164">Ara dil (IL) bunu doğrudan desteklemez ve yorum dile bırakılır.</span><span class="sxs-lookup"><span data-stu-id="0c396-164">Intermediate language (IL) doesn't support this directly, and interpretation is left to the language.</span></span>

- <span data-ttu-id="0c396-165">Ve yapılarında ortak Üyeler <xref:System.RuntimeFieldHandle> <xref:System.RuntimeMethodHandle> desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-165">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="0c396-166">Bu türler yalnızca LINQ, ifade ağaçları ve statik dizi başlatma için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0c396-166">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>

- <span data-ttu-id="0c396-167"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> ve, <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> gizli üyeleri temel sınıflara dahil eder ve bu nedenle açık geçersiz kılmalar olmadan geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-167"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="0c396-168">Bu aynı zamanda diğer [Runtimereftactionextensions. GetRuntime \* metotlarından](xref:System.Reflection.RuntimeReflectionExtensions) de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0c396-168">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>

- <span data-ttu-id="0c396-169"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> belirli birleşimler oluşturmaya çalıştığınızda başarısız olmaz (örneğin, bir `byref` nesne dizisi).</span><span class="sxs-lookup"><span data-stu-id="0c396-169"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of `byref` objects).</span></span>

- <span data-ttu-id="0c396-170">İşaretçi parametrelerine sahip üyeleri çağırmak için yansıma kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0c396-170">You can't use reflection to invoke members that have pointer parameters.</span></span>

- <span data-ttu-id="0c396-171">Bir işaretçi alanı almak veya ayarlamak için yansıma kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0c396-171">You can't use reflection to get or set a pointer field.</span></span>

- <span data-ttu-id="0c396-172">Bağımsız değişken sayısı yanlış olduğunda ve bağımsız değişkenlerden birinin türü yanlış olduğunda .NET Native <xref:System.ArgumentException> bir yerine bir atar <xref:System.Reflection.TargetParameterCountException> .</span><span class="sxs-lookup"><span data-stu-id="0c396-172">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>

- <span data-ttu-id="0c396-173">Özel durumların ikili seri hale getirilmesi genellikle desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-173">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="0c396-174">Sonuç olarak, seri hale getirilebilir olmayan nesneler <xref:System.Exception.Data%2A?displayProperty=nameWithType> sözlüğe eklenebilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-174">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="0c396-175">Desteklenmeyen senaryolar ve API 'Ler</span><span class="sxs-lookup"><span data-stu-id="0c396-175">Unsupported scenarios and APIs</span></span>

<span data-ttu-id="0c396-176">Aşağıdaki bölümlerde, HTTPClient ve Windows Communication Foundation (WCF) gibi genel geliştirme, birlikte çalışma ve teknolojiler için desteklenmeyen senaryolar ve API 'Ler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="0c396-176">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>

- [<span data-ttu-id="0c396-177">Genel Geliştirme</span><span class="sxs-lookup"><span data-stu-id="0c396-177">General development</span></span>](#General)

- [<span data-ttu-id="0c396-178">HttpClient</span><span class="sxs-lookup"><span data-stu-id="0c396-178">HttpClient</span></span>](#HttpClient)

- [<span data-ttu-id="0c396-179">Interop</span><span class="sxs-lookup"><span data-stu-id="0c396-179">Interop</span></span>](#Interop)

- [<span data-ttu-id="0c396-180">Desteklenmeyen API 'Ler</span><span class="sxs-lookup"><span data-stu-id="0c396-180">Unsupported APIs</span></span>](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a><span data-ttu-id="0c396-181">Genel geliştirme farkları</span><span class="sxs-lookup"><span data-stu-id="0c396-181">General development differences</span></span>

<span data-ttu-id="0c396-182">**Değer türleri**</span><span class="sxs-lookup"><span data-stu-id="0c396-182">**Value types**</span></span>

- <span data-ttu-id="0c396-183"><xref:System.ValueType.Equals%2A?displayProperty=nameWithType> <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> Değer türü için ve yöntemlerini geçersiz kılarsınız, temel sınıf uygulamalarını çağırmayın.</span><span class="sxs-lookup"><span data-stu-id="0c396-183">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="0c396-184">Windows Mağazası uygulamaları için .NET ' te bu yöntemler yansıma kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c396-184">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="0c396-185">Derleme zamanında .NET Native, çalışma zamanı Reflection kullanmadığı bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0c396-185">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="0c396-186">Yani, bu iki yöntemi geçersiz kılmıyorsanız, .NET Native, derleme zamanında uygulamayı oluşturduğundan, beklendiği gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="0c396-186">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="0c396-187">Ancak, bu yöntemleri geçersiz kılmak ancak temel sınıf uygulamasını çağırmak bir özel durumla sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="0c396-187">However, overriding these methods but calling the base class implementation results in an exception.</span></span>

- <span data-ttu-id="0c396-188">1 megabayttan büyük değer türleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-188">Value types larger than 1 megabyte aren't supported.</span></span>

- <span data-ttu-id="0c396-189">Değer türlerinde .NET Native parametresiz Oluşturucu olamaz.</span><span class="sxs-lookup"><span data-stu-id="0c396-189">Value types can't have a parameterless constructor in .NET Native.</span></span> <span data-ttu-id="0c396-190">(C# ve Visual Basic değer türlerinde parametresiz oluşturucular yasaklıyor.</span><span class="sxs-lookup"><span data-stu-id="0c396-190">(C# and Visual Basic prohibit parameterless constructors on value types.</span></span> <span data-ttu-id="0c396-191">Ancak bunlar Il 'de oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="0c396-191">However, these can be created in IL.)</span></span>

<span data-ttu-id="0c396-192">**Diziler**</span><span class="sxs-lookup"><span data-stu-id="0c396-192">**Arrays**</span></span>

- <span data-ttu-id="0c396-193">Sıfırdan farklı bir alt sınır içeren diziler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-193">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="0c396-194">Genellikle, bu diziler <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> aşırı yükleme çağırarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="0c396-194">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

- <span data-ttu-id="0c396-195">Çok boyutlu dizilerin dinamik olarak oluşturulması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-195">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="0c396-196">Bu tür diziler genellikle <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> bir `lengths` parametre içeren veya yöntemi çağırarak yönteminin aşırı yüklemesi çağırarak oluşturulur <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0c396-196">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="0c396-197">Dört veya daha fazla boyut içeren çok boyutlu diziler desteklenmez; diğer bir deyişle, <xref:System.Array.Rank%2A?displayProperty=nameWithType> özellik değeri dört veya daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="0c396-197">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="0c396-198">Bunun yerine [pürüzlü dizileri](../../csharp/programming-guide/arrays/jagged-arrays.md) (dizi dizileri) kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c396-198">Use [jagged arrays](../../csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="0c396-199">Örneğin, `array[x,y,z]` geçersizdir, ancak `array[x][y][z]` değil.</span><span class="sxs-lookup"><span data-stu-id="0c396-199">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>

- <span data-ttu-id="0c396-200">Çok boyutlu dizilerin varyansı desteklenmez ve <xref:System.InvalidCastException> çalışma zamanında bir özel duruma neden olur.</span><span class="sxs-lookup"><span data-stu-id="0c396-200">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>

<span data-ttu-id="0c396-201">**Genel Türler**</span><span class="sxs-lookup"><span data-stu-id="0c396-201">**Generics**</span></span>

- <span data-ttu-id="0c396-202">Sonsuz genel tür genişletmesi bir derleyici hatası ile sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="0c396-202">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="0c396-203">Örneğin, bu kod derlenmesi başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="0c396-203">For example, this code fails to compile:</span></span>

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

<span data-ttu-id="0c396-204">**İşaretçiler**</span><span class="sxs-lookup"><span data-stu-id="0c396-204">**Pointers**</span></span>

- <span data-ttu-id="0c396-205">İşaretçilerin dizileri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-205">Arrays of pointers aren't supported.</span></span>

- <span data-ttu-id="0c396-206">Bir işaretçi alanı almak veya ayarlamak için yansıma kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="0c396-206">You can't use reflection to get or set a pointer field.</span></span>

<span data-ttu-id="0c396-207">**Serileştirme**</span><span class="sxs-lookup"><span data-stu-id="0c396-207">**Serialization**</span></span>

<span data-ttu-id="0c396-208"><xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29>Öznitelik desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="0c396-208">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="0c396-209"><xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29>Bunun yerine özniteliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c396-209">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>

<span data-ttu-id="0c396-210">**Kaynaklar**</span><span class="sxs-lookup"><span data-stu-id="0c396-210">**Resources**</span></span>

<span data-ttu-id="0c396-211">Sınıf ile yerelleştirilmiş kaynakların kullanımı <xref:System.Diagnostics.Tracing.EventSource> desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-211">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="0c396-212"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType>Özelliği yerelleştirilmiş kaynakları tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="0c396-212">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>

<span data-ttu-id="0c396-213">**Temsilciler**</span><span class="sxs-lookup"><span data-stu-id="0c396-213">**Delegates**</span></span>

<span data-ttu-id="0c396-214">`Delegate.BeginInvoke` ve `Delegate.EndInvoke` desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-214">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>

<span data-ttu-id="0c396-215">**Çeşitli API'ler**</span><span class="sxs-lookup"><span data-stu-id="0c396-215">**Miscellaneous APIs**</span></span>

- <span data-ttu-id="0c396-216">[TypeInfo. GUID](xref:System.Type.GUID) özelliği, <xref:System.PlatformNotSupportedException> bir <xref:System.Runtime.InteropServices.GuidAttribute> öznitelik türe uygulanmadıysa bir özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0c396-216">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="0c396-217">GUID öncelikle COM desteği için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="0c396-217">The GUID is used primarily for COM support.</span></span>

- <span data-ttu-id="0c396-218"><xref:System.DateTime.Parse%2A?displayProperty=nameWithType>Yöntemi, .NET Native kısa tarihleri içeren dizeleri doğru bir şekilde ayrıştırır.</span><span class="sxs-lookup"><span data-stu-id="0c396-218">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="0c396-219">Ancak, Microsoft Bilgi Bankası makalelerinde [KB2803771](https://support.microsoft.com/kb/2803771) ve [KB2803755](https://support.microsoft.com/kb/2803755)'de açıklanan tarih ve saat ayrıştırılırken yapılan değişikliklerle uyumluluğu korumaz.</span><span class="sxs-lookup"><span data-stu-id="0c396-219">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>

- <span data-ttu-id="0c396-220"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")`.NET Native, doğru şekilde yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="0c396-220"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="0c396-221">CLR 'nin bazı sürümlerinde, sonuç dizesi yuvarlatılmış yerine kesilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-221">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a><span data-ttu-id="0c396-222">HttpClient farkları</span><span class="sxs-lookup"><span data-stu-id="0c396-222">HttpClient differences</span></span>

<span data-ttu-id="0c396-223">.NET Native, <xref:System.Net.Http.HttpClientHandler> sınıf dahili olarak <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> Windows Mağazası uygulamaları için standart .net 'te kullanılan ve sınıfları yerine Winınet (sınıfı aracılığıyla) kullanır.</span><span class="sxs-lookup"><span data-stu-id="0c396-223">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="0c396-224">WinINet, sınıfın desteklediği tüm yapılandırma seçeneklerini desteklemez <xref:System.Net.Http.HttpClientHandler> .</span><span class="sxs-lookup"><span data-stu-id="0c396-224">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="0c396-225">Sonuç olarak:</span><span class="sxs-lookup"><span data-stu-id="0c396-225">As a result:</span></span>

- <span data-ttu-id="0c396-226">Bazı özellik özelliklerinden bazıları <xref:System.Net.Http.HttpClientHandler> `false` .NET Native Dönüşken `true` Windows Mağazası uygulamaları için standart .net ' de döndürülür.</span><span class="sxs-lookup"><span data-stu-id="0c396-226">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>

- <span data-ttu-id="0c396-227">Bazı yapılandırma özelliği erişimcileri, `get` Windows Mağazası uygulamaları için .net 'teki varsayılan yapılandırılabilir değerden farklı .NET Native her zaman sabit bir değer döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c396-227">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>

<span data-ttu-id="0c396-228">Bazı ek davranış farklılıkları aşağıdaki alt bölümlerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="0c396-228">Some additional behavior differences are covered in the following subsections.</span></span>

<span data-ttu-id="0c396-229">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="0c396-229">**Proxy**</span></span>

<span data-ttu-id="0c396-230"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter>Sınıfı, istek temelinde proxy 'nin yapılandırılmasını veya geçersiz kılınmasını desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0c396-230">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="0c396-231">Bu, .NET Native üzerindeki tüm isteklerin, özelliğin değerine bağlı olarak sistem tarafından yapılandırılan proxy sunucusunu veya proxy sunucu olmadığını kullandığı anlamına gelir <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0c396-231">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="0c396-232">Windows Mağazası uygulamaları için .NET ' te, proxy sunucu özelliği tarafından tanımlanır <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0c396-232">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="0c396-233">.NET Native ' de, öğesini dışında bir <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> değere ayarlamak `null` <xref:System.PlatformNotSupportedException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0c396-233">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="0c396-234"><xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType>Özelliği .NET Native döndürür `false` , ancak `true` Windows Mağazası uygulamaları için standart .NET Framework geri döner.</span><span class="sxs-lookup"><span data-stu-id="0c396-234">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>

<span data-ttu-id="0c396-235">**Otomatik yeniden yönlendirme**</span><span class="sxs-lookup"><span data-stu-id="0c396-235">**Automatic redirection**</span></span>

<span data-ttu-id="0c396-236"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter>Sınıfı, en fazla otomatik yeniden yönlendirme sayısının yapılandırılmasına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0c396-236">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="0c396-237">Özelliğinin değeri, <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> Windows Mağazası uygulamaları için standart .net ' de varsayılan olarak 50 ' dir ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-237">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="0c396-238">.NET Native, bu özelliğin değeri 10 ' dur ve değiştirme girişimi bir <xref:System.PlatformNotSupportedException> özel durum oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0c396-238">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="0c396-239"><xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType>Özelliği, `false` `true` Windows Mağazası uygulamaları için .net ' i döndürdüğünde, .NET Native döndürür.</span><span class="sxs-lookup"><span data-stu-id="0c396-239">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>

<span data-ttu-id="0c396-240">**Otomatik açma**</span><span class="sxs-lookup"><span data-stu-id="0c396-240">**Automatic decompression**</span></span>

<span data-ttu-id="0c396-241">Windows Mağazası uygulamaları için .NET <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> <xref:System.Net.DecompressionMethods.Deflate> , özelliği, <xref:System.Net.DecompressionMethods.GZip> <xref:System.Net.DecompressionMethods.Deflate> ve <xref:System.Net.DecompressionMethods.GZip> ya <xref:System.Net.DecompressionMethods.None> da olarak ayarlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="0c396-241">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="0c396-242">.NET Native yalnızca <xref:System.Net.DecompressionMethods.Deflate> veya ile birlikte desteklenir <xref:System.Net.DecompressionMethods.GZip> <xref:System.Net.DecompressionMethods.None> .</span><span class="sxs-lookup"><span data-stu-id="0c396-242">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="0c396-243"><xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A>Özelliği ya da <xref:System.Net.DecompressionMethods.Deflate> tek başına sessizce ayarlama girişimi, hem hem <xref:System.Net.DecompressionMethods.GZip> de olarak ayarlanır <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip> .</span><span class="sxs-lookup"><span data-stu-id="0c396-243">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>

<span data-ttu-id="0c396-244">**Özgü**</span><span class="sxs-lookup"><span data-stu-id="0c396-244">**Cookies**</span></span>

<span data-ttu-id="0c396-245">Tanımlama bilgisi işleme, ve WinINet tarafından aynı anda gerçekleştirilir <xref:System.Net.Http.HttpClient> .</span><span class="sxs-lookup"><span data-stu-id="0c396-245">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="0c396-246">' Dan tanımlama bilgileri, <xref:System.Net.CookieContainer> Winınet tanımlama bilgisi önbelleğindeki tanımlama bilgileriyle birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-246">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="0c396-247">' Dan bir tanımlama bilgisinin kaldırılması <xref:System.Net.CookieContainer> <xref:System.Net.Http.HttpClient> , tanımlama bilgisinin gönderilmesini engeller, ancak tanımlama bilgisi zaten Winınet tarafından görüleniyorsa ve tanımlama bilgileri Kullanıcı tarafından silinmediğinden, Winınet bunu gönderir.</span><span class="sxs-lookup"><span data-stu-id="0c396-247">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="0c396-248"><xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler> , Veya API kullanarak bir tanımlama bilgisinin Winınet 'dan program aracılığıyla kaldırılması mümkün değildir <xref:System.Net.CookieContainer> .</span><span class="sxs-lookup"><span data-stu-id="0c396-248">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="0c396-249"><xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType>Özelliği `false` yalnızca <xref:System.Net.Http.HttpClient> tanımlama bilgilerinin gönderilmesini durdurmasına neden olacak şekilde ayarlama; WinINet, isteğe tanımlama bilgilerini yine de dahil edebilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-249">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>

<span data-ttu-id="0c396-250">**Kimlik Bilgileri**</span><span class="sxs-lookup"><span data-stu-id="0c396-250">**Credentials**</span></span>

<span data-ttu-id="0c396-251">Windows Mağazası uygulamaları için .NET ' te, <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> ve <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> özellikleri bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="0c396-251">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="0c396-252">Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği arabirimini uygulayan tüm nesneleri kabul eder <xref:System.Net.ICredentials> .</span><span class="sxs-lookup"><span data-stu-id="0c396-252">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="0c396-253">.NET Native ' de, <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> özelliği `true` özelliğinin olmasına neden olur <xref:System.Net.Http.HttpClientHandler.Credentials%2A> `null` .</span><span class="sxs-lookup"><span data-stu-id="0c396-253">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="0c396-254">Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği yalnızca `null` , <xref:System.Net.CredentialCache.DefaultCredentials%2A> veya türünde bir nesne olarak ayarlanabilir <xref:System.Net.NetworkCredential> .</span><span class="sxs-lookup"><span data-stu-id="0c396-254">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="0c396-255">Diğer herhangi bir <xref:System.Net.ICredentials> nesneyi atama, en popüler olan <xref:System.Net.CredentialCache> <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği özelliğine bir atar <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="0c396-255">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="0c396-256">**Desteklenmeyen diğer veya yapılandırılamayan Özellikler**</span><span class="sxs-lookup"><span data-stu-id="0c396-256">**Other unsupported or unconfigurable features**</span></span>

<span data-ttu-id="0c396-257">.NET Native:</span><span class="sxs-lookup"><span data-stu-id="0c396-257">In .NET Native:</span></span>

- <span data-ttu-id="0c396-258"><xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType>Özelliğin değeri her zaman <xref:System.Net.Http.ClientCertificateOption.Automatic> .</span><span class="sxs-lookup"><span data-stu-id="0c396-258">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="0c396-259">Windows Mağazası uygulamaları için .NET sürümünde varsayılan değer <xref:System.Net.Http.ClientCertificateOption.Manual> .</span><span class="sxs-lookup"><span data-stu-id="0c396-259">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>

- <span data-ttu-id="0c396-260"><xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType>Özelliği yapılandırılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="0c396-260">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>

- <span data-ttu-id="0c396-261"><xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType>Özelliği her zaman `true` .</span><span class="sxs-lookup"><span data-stu-id="0c396-261">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="0c396-262">Windows Mağazası uygulamaları için .NET sürümünde varsayılan değer `false` .</span><span class="sxs-lookup"><span data-stu-id="0c396-262">In .NET for Windows Store apps, the default is `false`.</span></span>

- <span data-ttu-id="0c396-263">`SetCookie2`Yanıtlarındaki üst bilgi eski olarak yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="0c396-263">The `SetCookie2` header in responses is ignored as obsolete.</span></span>

<a name="Interop"></a>

### <a name="interop-differences"></a><span data-ttu-id="0c396-264">Birlikte çalışma farklılıkları</span><span class="sxs-lookup"><span data-stu-id="0c396-264">Interop differences</span></span>

 <span data-ttu-id="0c396-265">**Kullanım dışı API 'Ler**</span><span class="sxs-lookup"><span data-stu-id="0c396-265">**Deprecated APIs**</span></span>

 <span data-ttu-id="0c396-266">Yönetilen kodla birlikte çalışabilirlik için sık kullanılan birçok API kullanım dışı bırakılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0c396-266">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="0c396-267">.NET Native ile kullanıldığında, bu API 'Ler bir <xref:System.NotImplementedException> veya <xref:System.PlatformNotSupportedException> özel durum oluşturabilir ya da bir derleyici hatasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-267">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="0c396-268">Windows Mağazası uygulamaları için .NET sürümünde, bu API 'Ler, bir derleyici hatası yerine bir derleyici uyarısı üretse de eski olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="0c396-268">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>

 <span data-ttu-id="0c396-269">Hazırlama için kullanımdan kaldırılan API 'Ler `VARIANT` şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0c396-269">Deprecated APIs for `VARIANT` marshaling include:</span></span>

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <span data-ttu-id="0c396-270"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> desteklenir, ancak, [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) veya varyantlar ile kullanıldığı durumlar gibi bazı senaryolarda bir özel durum oluşturur `byref` .</span><span class="sxs-lookup"><span data-stu-id="0c396-270"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or `byref` variants.</span></span>

 <span data-ttu-id="0c396-271">[IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) desteği için kullanım dışı API 'ler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0c396-271">Deprecated APIs for [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

<span data-ttu-id="0c396-272">Klasik COM olayları için kullanım dışı API 'Ler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0c396-272">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<span data-ttu-id="0c396-273">Arabirimde kullanılmayan API 'Ler <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> , .NET Native desteklenmez, şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="0c396-273">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>

- <span data-ttu-id="0c396-274"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="0c396-274"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="0c396-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="0c396-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="0c396-276"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="0c396-276"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

<span data-ttu-id="0c396-277">Desteklenmeyen diğer birlikte çalışma özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="0c396-277">Other unsupported interop features include:</span></span>

- <span data-ttu-id="0c396-278"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="0c396-278"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>
- <span data-ttu-id="0c396-279"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (tüm Üyeler)</span><span class="sxs-lookup"><span data-stu-id="0c396-279"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 <span data-ttu-id="0c396-280">Nadiren kullanılan sıralama API 'Leri:</span><span class="sxs-lookup"><span data-stu-id="0c396-280">Rarely used marshaling APIs:</span></span>

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

 <span data-ttu-id="0c396-281">**Platform çağırma ve COM birlikte çalışma uyumluluğu**</span><span class="sxs-lookup"><span data-stu-id="0c396-281">**Platform invoke and COM interop compatibility**</span></span>

 <span data-ttu-id="0c396-282">Çoğu platform çağırma ve COM birlikte çalışma senaryosu hala .NET Native desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="0c396-282">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="0c396-283">Özellikle, Windows Çalışma Zamanı (WinRT) API 'Leriyle birlikte çalışabilirlik ve Windows Çalışma Zamanı için gereken tüm sıralama desteklenir.</span><span class="sxs-lookup"><span data-stu-id="0c396-283">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="0c396-284">Bu, için sıralama desteğini içerir:</span><span class="sxs-lookup"><span data-stu-id="0c396-284">This includes marshaling support for:</span></span>

- <span data-ttu-id="0c396-285">Diziler (dahil <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType> )</span><span class="sxs-lookup"><span data-stu-id="0c396-285">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>

- `BStr`

- <span data-ttu-id="0c396-286">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="0c396-286">Delegates</span></span>

- <span data-ttu-id="0c396-287">Dizeler (Unicode, ANSI ve HSTRıNG)</span><span class="sxs-lookup"><span data-stu-id="0c396-287">Strings (Unicode, ANSI, and HSTRING)</span></span>

- <span data-ttu-id="0c396-288">Yapılar ( `byref` ve `byval` )</span><span class="sxs-lookup"><span data-stu-id="0c396-288">Structs (`byref` and `byval`)</span></span>

- <span data-ttu-id="0c396-289">Birleşimler</span><span class="sxs-lookup"><span data-stu-id="0c396-289">Unions</span></span>

- <span data-ttu-id="0c396-290">Win32 tutamaçları</span><span class="sxs-lookup"><span data-stu-id="0c396-290">Win32 handles</span></span>

- <span data-ttu-id="0c396-291">Tüm WinRT yapıları</span><span class="sxs-lookup"><span data-stu-id="0c396-291">All WinRT constructs</span></span>

- <span data-ttu-id="0c396-292">Değişken türlerini hazırlama için kısmi destek.</span><span class="sxs-lookup"><span data-stu-id="0c396-292">Partial support for marshaling variant types.</span></span> <span data-ttu-id="0c396-293">Aşağıdakiler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="0c396-293">The following are supported:</span></span>

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

  - [<span data-ttu-id="0c396-294">IUnknown</span><span class="sxs-lookup"><span data-stu-id="0c396-294">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

<span data-ttu-id="0c396-295">Ancak, .NET Native aşağıdakileri desteklemez:</span><span class="sxs-lookup"><span data-stu-id="0c396-295">However, .NET Native doesn't support the following:</span></span>

- <span data-ttu-id="0c396-296">Klasik COM olaylarını kullanma</span><span class="sxs-lookup"><span data-stu-id="0c396-296">Using classic COM events</span></span>

- <span data-ttu-id="0c396-297"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>Arabirimi yönetilen bir tür üzerinde uygulama</span><span class="sxs-lookup"><span data-stu-id="0c396-297">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>

- <span data-ttu-id="0c396-298">Öznitelik aracılığıyla bir yönetilen tür üzerinde [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimini uygulama <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="0c396-298">Implementing the [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="0c396-299">Ancak, COM nesnelerini aracılığıyla çağıramaz `IDispatch` ve Yönetilen nesneniz uygulayamaz `IDispatch` .</span><span class="sxs-lookup"><span data-stu-id="0c396-299">However, you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>

<span data-ttu-id="0c396-300">Bir platform çağırma yöntemi çağırmak için yansıma kullanılması desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-300">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="0c396-301">Yöntem çağrısını başka bir yöntemde sarmalayarak ve bunun yerine sarmalayıcı çağırmak için yansıma kullanarak bu sınırlamaya geçici bir çözüm bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0c396-301">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="0c396-302">Windows Mağazası uygulamaları için .NET API 'Lerinden diğer farklılıklar</span><span class="sxs-lookup"><span data-stu-id="0c396-302">Other differences from .NET APIs for Windows Store apps</span></span>

<span data-ttu-id="0c396-303">Bu bölümde, .NET Native desteklenmeyen kalan API 'Ler listelenir.</span><span class="sxs-lookup"><span data-stu-id="0c396-303">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="0c396-304">Desteklenmeyen API 'lerin en büyük kümesi Windows Communication Foundation (WCF) API 'lerdir.</span><span class="sxs-lookup"><span data-stu-id="0c396-304">The largest set of the unsupported APIs is the Windows Communication Foundation (WCF) APIs.</span></span>

<span data-ttu-id="0c396-305">**Dataaçıklamalarda (System. ComponentModel. Dataaçıklamalarda)**</span><span class="sxs-lookup"><span data-stu-id="0c396-305">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>

<span data-ttu-id="0c396-306">Ve ad alanlarındaki türler <xref:System.ComponentModel.DataAnnotations> <xref:System.ComponentModel.DataAnnotations.Schema> .NET Native desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-306">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="0c396-307">Bunlar, Windows 8 için Windows Mağazası uygulamaları için .NET sürümünde mevcut olan aşağıdaki türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="0c396-307">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>

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

 <span data-ttu-id="0c396-308">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="0c396-308">**Visual Basic**</span></span>

<span data-ttu-id="0c396-309">Visual Basic şu anda .NET Native desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="0c396-309">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="0c396-310"><xref:Microsoft.VisualBasic>Ve ad alanlarında bulunan aşağıdaki türler <xref:Microsoft.VisualBasic.CompilerServices> .NET Native kullanılamaz:</span><span class="sxs-lookup"><span data-stu-id="0c396-310">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>

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

<span data-ttu-id="0c396-311">**Yansıma bağlamı (System. Reflection. Context ad alanı)**</span><span class="sxs-lookup"><span data-stu-id="0c396-311">**Reflection Context (System.Reflection.Context namespace)**</span></span>

<span data-ttu-id="0c396-312"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType>Sınıf .NET Native desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="0c396-312">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>

<span data-ttu-id="0c396-313">**RTC (System .net. http. rtc)**</span><span class="sxs-lookup"><span data-stu-id="0c396-313">**RTC (System.Net.Http.Rtc)**</span></span>

<span data-ttu-id="0c396-314">`System.Net.Http.RtcRequestFactory`Sınıf .NET Native desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="0c396-314">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>

<span data-ttu-id="0c396-315">**Windows Communication Foundation (WCF) (System. ServiceModel. \* )**</span><span class="sxs-lookup"><span data-stu-id="0c396-315">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>

<span data-ttu-id="0c396-316">[System. ServiceModel. \* ad](xref:System.ServiceModel) alanlarındaki türler .NET Native desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="0c396-316">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="0c396-317">Bunlar aşağıdaki türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="0c396-317">These include the following types:</span></span>

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

### <a name="differences-in-serializers"></a><span data-ttu-id="0c396-318">Serileştiricilerle farklılıklar</span><span class="sxs-lookup"><span data-stu-id="0c396-318">Differences in serializers</span></span>

<span data-ttu-id="0c396-319">Aşağıdaki farklılıklar,, ve sınıflarıyla serileştirme ve seri durumdan çıkarma ile ilgilenmeyi de ister <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <xref:System.Xml.Serialization.XmlSerializer> :</span><span class="sxs-lookup"><span data-stu-id="0c396-319">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>

- <span data-ttu-id="0c396-320">.NET Native ' de <xref:System.Runtime.Serialization.DataContractSerializer> , <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> türü kök serileştirme türü olmayan bir temel sınıf üyesine sahip türetilmiş bir sınıfı seri hale getirme veya serisini kaldırma başarısız.</span><span class="sxs-lookup"><span data-stu-id="0c396-320">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="0c396-321">Örneğin, aşağıdaki kodda, `Y` sonuçları bir hata halinde serileştirme veya serisini kaldırma girişimi:</span><span class="sxs-lookup"><span data-stu-id="0c396-321">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  <span data-ttu-id="0c396-322">Seri hale `InnerType` getirici, taban sınıfının üyeleri serileştirme sırasında çapraz olmadığından tür serileştirici tarafından tanınmıyor.</span><span class="sxs-lookup"><span data-stu-id="0c396-322">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>

- <span data-ttu-id="0c396-323"><xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> arabirimi uygulayan bir sınıf veya yapıyı seri hale getirme başarısız olur <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="0c396-323"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="0c396-324">Örneğin, aşağıdaki türler seri hale getirilemez veya seri durumdan çıkarılamıyor:</span><span class="sxs-lookup"><span data-stu-id="0c396-324">For example, the following types fail to serialize or deserialize:</span></span>

- <span data-ttu-id="0c396-325"><xref:System.Xml.Serialization.XmlSerializer> Aşağıdaki nesne değeri seri hale getirilebilmesi için nesnenin tam türünü bilmez çünkü serileştirme:</span><span class="sxs-lookup"><span data-stu-id="0c396-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>

- <span data-ttu-id="0c396-326"><xref:System.Xml.Serialization.XmlSerializer> serileştirilmiş nesne türü ise seri hale getirilemez veya seri durumdan çıkarılamıyor <xref:System.Xml.XmlQualifiedName> .</span><span class="sxs-lookup"><span data-stu-id="0c396-326"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>

- <span data-ttu-id="0c396-327">Tüm serileştiriciler ( <xref:System.Runtime.Serialization.DataContractSerializer> , <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> ), türü için <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> veya içeren bir tür için serileştirme kodu üretemiyor <xref:System.Xml.Linq.XElement> .</span><span class="sxs-lookup"><span data-stu-id="0c396-327">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="0c396-328">Bunun yerine derleme zamanı hatalarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0c396-328">They display build-time errors instead.</span></span>

- <span data-ttu-id="0c396-329">Serileştirme türlerinin aşağıdaki oluşturucuların beklenen şekilde çalışması garanti edilmez:</span><span class="sxs-lookup"><span data-stu-id="0c396-329">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>

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

- <span data-ttu-id="0c396-330"><xref:System.Xml.Serialization.XmlSerializer> Aşağıdaki özniteliklerden herhangi birine sahip olan yöntemlere sahip bir tür için kod üretemiyor:</span><span class="sxs-lookup"><span data-stu-id="0c396-330"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <span data-ttu-id="0c396-331"><xref:System.Xml.Serialization.XmlSerializer><xref:System.Xml.Serialization.IXmlSerializable>özel serileştirme arabirimini dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="0c396-331"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="0c396-332">Bu arabirimi uygulayan bir sınıfınız varsa, <xref:System.Xml.Serialization.XmlSerializer> türü düz bir eskı CLR nesnesi (POCO) türü olarak nitelendirir ve yalnızca ortak özelliklerini serileştirir.</span><span class="sxs-lookup"><span data-stu-id="0c396-332">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>

- <span data-ttu-id="0c396-333">Düz bir nesneyi seri hale getirmek <xref:System.Exception> ve ile iyi çalışmaz <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> .</span><span class="sxs-lookup"><span data-stu-id="0c396-333">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>

## <a name="visual-studio-differences"></a><span data-ttu-id="0c396-334">Visual Studio farklılıkları</span><span class="sxs-lookup"><span data-stu-id="0c396-334">Visual Studio differences</span></span>

<span data-ttu-id="0c396-335">**Özel durumlar ve hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="0c396-335">**Exceptions and debugging**</span></span>

<span data-ttu-id="0c396-336">Hata ayıklayıcıda .NET Native kullanılarak derlenen uygulamalar çalıştırırken, ilk fırsat özel durumları aşağıdaki özel durum türleri için etkinleştirilir:</span><span class="sxs-lookup"><span data-stu-id="0c396-336">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

<span data-ttu-id="0c396-337">**Uygulama oluşturma**</span><span class="sxs-lookup"><span data-stu-id="0c396-337">**Building apps**</span></span>

<span data-ttu-id="0c396-338">Varsayılan olarak Visual Studio tarafından kullanılan x86 derleme araçlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c396-338">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="0c396-339">C:\Program Files (x86) \MSBuild\12.0\bin\amd64; dizininde bulunan AMD64 MSBuild araçlarının kullanılmasını önermiyoruz. Bunlar, derleme sorunları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="0c396-339">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>

<span data-ttu-id="0c396-340">**Profil oluşturucular**</span><span class="sxs-lookup"><span data-stu-id="0c396-340">**Profilers**</span></span>

- <span data-ttu-id="0c396-341">Visual Studio CPU Profiler ve XAML Memory Profiler yalnızca-Code 'u doğru bir şekilde görüntülemiyor.</span><span class="sxs-lookup"><span data-stu-id="0c396-341">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>

- <span data-ttu-id="0c396-342">XAML bellek profili Oluşturucu yönetilen yığın verilerini doğru şekilde görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="0c396-342">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>

- <span data-ttu-id="0c396-343">CPU Profiler, modülleri doğru şekilde tanımlamaz ve önekli işlev adlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0c396-343">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>

<span data-ttu-id="0c396-344">**Birim test kitaplığı projeleri**</span><span class="sxs-lookup"><span data-stu-id="0c396-344">**Unit Test Library projects**</span></span>

<span data-ttu-id="0c396-345">Windows Mağazası uygulamaları projesi için bir birim testi kitaplığı üzerinde .NET Native etkinleştirme desteklenmez ve projenin derlenmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="0c396-345">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c396-346">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c396-346">See also</span></span>

- [<span data-ttu-id="0c396-347">Başlarken</span><span class="sxs-lookup"><span data-stu-id="0c396-347">Getting Started</span></span>](getting-started-with-net-native.md)
- [<span data-ttu-id="0c396-348">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="0c396-348">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- <span data-ttu-id="0c396-349">[Windows Mağazası uygulamalarına yönelik .NET genel bakış](/previous-versions/windows/apps/br230302(v=vs.140))</span><span class="sxs-lookup"><span data-stu-id="0c396-349">[.NET For Windows Store apps overview](/previous-versions/windows/apps/br230302(v=vs.140))</span></span>
- [<span data-ttu-id="0c396-350">Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği</span><span class="sxs-lookup"><span data-stu-id="0c396-350">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
