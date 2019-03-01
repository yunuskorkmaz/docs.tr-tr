---
title: Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 92e4f416e26e5af9124593f2bef8d8042fcfc953
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966794"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="e37c0-102">Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma</span><span class="sxs-lookup"><span data-stu-id="e37c0-102">Migrating Your Windows Store App to .NET Native</span></span>
<span data-ttu-id="e37c0-103">.NET yerel uygulamaları Windows Store veya Geliştirici bilgisayara statik derlenmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e37c0-103">.NET Native provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="e37c0-104">Bu Windows Store uygulamaları için tam zamanında (JIT) derleyici tarafından gerçekleştirilen dinamik derlemeden farklıdır veya [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) cihazda.</span><span class="sxs-lookup"><span data-stu-id="e37c0-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="e37c0-105">Farklar rağmen .NET Native ile uyumluluğu korumak çalışır [.NET için Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span><span class="sxs-lookup"><span data-stu-id="e37c0-105">Despite the differences, .NET Native tries to maintain compatibility with the [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29).</span></span> <span data-ttu-id="e37c0-106">Çoğunlukla, .NET için Windows Store uygulamaları iş öğeleri de .NET Native ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-106">For the most part, things that work on the .NET for Windows Store apps also work with .NET Native.</span></span>  <span data-ttu-id="e37c0-107">Ancak, bazı durumlarda, davranış değişiklikleri karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e37c0-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="e37c0-108">Bu belge aşağıdaki alanlarda standart .NET için Windows Store uygulamaları ve .NET Native arasındaki farklar açıklanır:</span><span class="sxs-lookup"><span data-stu-id="e37c0-108">This document discusses these differences between the standard .NET for Windows Store apps and .NET Native in the following areas:</span></span>  
  
-   [<span data-ttu-id="e37c0-109">Genel çalışma zamanı farkları</span><span class="sxs-lookup"><span data-stu-id="e37c0-109">General runtime differences</span></span>](#Runtime)  
  
-   [<span data-ttu-id="e37c0-110">Dinamik programlama farkları</span><span class="sxs-lookup"><span data-stu-id="e37c0-110">Dynamic programming differences</span></span>](#Dynamic)  
  
-   [<span data-ttu-id="e37c0-111">Yansıma ile ilgili diğer farklar</span><span class="sxs-lookup"><span data-stu-id="e37c0-111">Other reflection-related differences</span></span>](#Reflection)  
  
-   [<span data-ttu-id="e37c0-112">Desteklenmeyen senaryolar ve API'ler</span><span class="sxs-lookup"><span data-stu-id="e37c0-112">Unsupported scenarios and APIs</span></span>](#Unsupported)  
  
-   [<span data-ttu-id="e37c0-113">Visual Studio farkları</span><span class="sxs-lookup"><span data-stu-id="e37c0-113">Visual Studio differences</span></span>](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a><span data-ttu-id="e37c0-114">Genel çalışma zamanı farkları</span><span class="sxs-lookup"><span data-stu-id="e37c0-114">General runtime differences</span></span>  
  
-   <span data-ttu-id="e37c0-115">Özel durumlar gibi <xref:System.TypeLoadException>, durum JIT derleyicisi tarafından üzerinde ortak bir uygulama çalıştırdığında dil çalışma zamanı (CLR) .NET Native tarafından işlendiğinde derleme zamanı hatalarına genellikle sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by .NET Native.</span></span>  
  
-   <span data-ttu-id="e37c0-116">Remove() çağırmayın <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> uygulamanın UI iş parçacığından yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e37c0-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="e37c0-117">Bu karşılıklı bir kilitlenme .NET Native neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-117">This can result in a deadlock on .NET Native.</span></span>  
  
-   <span data-ttu-id="e37c0-118">Statik sınıf oluşturucu çağrı sırası güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="e37c0-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="e37c0-119">.NET Native çağırma farklı standart çalışma zamanı üzerinde sırasıdır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-119">In .NET Native, the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="e37c0-120">(Hatta standart çalışma zamanıyla statik sınıf oluşturucuları yürütülmesini bazında güvenmemelisiniz.)</span><span class="sxs-lookup"><span data-stu-id="e37c0-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>  
  
-   <span data-ttu-id="e37c0-121">Döngü sonsuz bir çağrı yapmadan (örneğin, `while(true);`) herhangi bir iş parçacığı üzerinde bir durdurmak için uygulamayı getir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="e37c0-122">Benzer şekilde, büyük ya da sonsuz bekler, bir durdurmak için uygulamayı getiriyor.</span><span class="sxs-lookup"><span data-stu-id="e37c0-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>  
  
-   <span data-ttu-id="e37c0-123">Bazı genel başlatma döngüleri özel .NET Native durumlar yok.</span><span class="sxs-lookup"><span data-stu-id="e37c0-123">Certain generic initialization cycles don't throw exceptions in .NET Native.</span></span> <span data-ttu-id="e37c0-124">Örneğin, aşağıdaki oluşturur kod bir <xref:System.TypeLoadException> standart CLR özel durum.</span><span class="sxs-lookup"><span data-stu-id="e37c0-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="e37c0-125">.NET Native içinde bu değil.</span><span class="sxs-lookup"><span data-stu-id="e37c0-125">In .NET Native, it doesn't.</span></span>  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   <span data-ttu-id="e37c0-126">Bazı durumlarda, .NET Framework sınıf kitaplıkları farklı uygulamaları .NET Native sağlar.</span><span class="sxs-lookup"><span data-stu-id="e37c0-126">In some cases, .NET Native provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="e37c0-127">Yöntemi tarafından döndürülen bir nesne, döndürülen tür üyelerinin her zaman uygular.</span><span class="sxs-lookup"><span data-stu-id="e37c0-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="e37c0-128">Yedekleme uygulaması farklı olduğundan, ancak, diğer .NET Framework platformunda çalışan de aynı türleri kümesi için tür dönüştürme mümkün olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="e37c0-129">Örneğin, bazı durumlarda, size bir şekilde yayınlanabilirler olmayabilir <xref:System.Collections.Generic.IEnumerable%601> arabirimi nesnesi gibi yöntemler tarafından döndürülen <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> veya <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> için `T[]`.</span><span class="sxs-lookup"><span data-stu-id="e37c0-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>  
  
-   <span data-ttu-id="e37c0-130">Varsayılan olarak .NET için Windows Store apps WinInet önbelleğinde etkin değil ancak .NET Native üzerinde olacaktır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on .NET Native.</span></span> <span data-ttu-id="e37c0-131">Bu durum peformansı artırmasına karşın çalışma kümesi etkileri vardır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="e37c0-132">Herhangi bir geliştirici eylemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-132">No developer action is necessary.</span></span>  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a><span data-ttu-id="e37c0-133">Dinamik programlama farkları</span><span class="sxs-lookup"><span data-stu-id="e37c0-133">Dynamic programming differences</span></span>  
 <span data-ttu-id="e37c0-134">.NET native statik olarak en yüksek performans için uygulama yerel kod yapmak için .NET Framework kodundaki bağlar.</span><span class="sxs-lookup"><span data-stu-id="e37c0-134">.NET Native statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="e37c0-135">Ancak, ikili boyutları küçük kalır. böylece, tüm .NET Framework yapılamıyor gerekir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="e37c0-136">.NET yerel derleyici, kullanılmayan kod başvurularını kaldırır bir bağımlılık Azaltıcı kullanarak bu sınırlama çözümler.</span><span class="sxs-lookup"><span data-stu-id="e37c0-136">The .NET Native compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="e37c0-137">Ancak, .NET Native korumak veya olmayabilir bu bilgiler, statik olarak derleme zamanında çıkarsanamıyor, ancak bunun yerine çalışma zamanında dinamik olarak alınır olduğunda bazı tür bilgilerini ve kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e37c0-137">However, .NET Native might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>  
  
 <span data-ttu-id="e37c0-138">.NET native yansıtma ve dinamik programlama etkinleştirmez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-138">.NET Native does enable reflection and dynamic programming.</span></span> <span data-ttu-id="e37c0-139">Ancak, tüm türleri (özellikle .NET Framework'teki ortak API'lerde yansıtan desteklendiğinden) bu oluşturulan kod boyutu çok büyük yapacağı için yansıma için işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="e37c0-140">.NET yerel derleyici, yansıma türlerini desteklemesi ve hakkında meta veriler tutar ve yalnızca bu türleri için kod oluşturur akıllı seçimlerini yapar.</span><span class="sxs-lookup"><span data-stu-id="e37c0-140">The .NET Native compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>  
  
 <span data-ttu-id="e37c0-141">Örneğin, veri bağlama işlevleri için özellik adlarını eşleştirmek için uygulama gerektiriyor.</span><span class="sxs-lookup"><span data-stu-id="e37c0-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="e37c0-142">.NET için Windows Store uygulamalarında ortak dil çalışma zamanı yansıma yönetilen türleri ve genel kullanıma açık yerel türler için bu yeteneği vermek otomatik olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="e37c0-143">.NET Native, derleyici, otomatik olarak veri bağlama türleri için meta verileri içerir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-143">In .NET Native, the compiler automatically includes metadata for types to which you bind data.</span></span>  
  
 <span data-ttu-id="e37c0-144">.NET derleyici ayrıca işleyebilir genellikle yerel genel türler gibi kullanılan <xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602>, hangi ipuçlarının ya da yönergeleri gerektirmeden çalışır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-144">The .NET Native compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="e37c0-145">[Dinamik](~/docs/csharp/language-reference/keywords/dynamic.md) anahtar sözcüğü de bazı sınırlar içinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-145">The [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e37c0-146">Tüm dinamik kod yolları .NET Native uygulamanıza taşırken sınamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-146">You should test all dynamic code paths thoroughly when porting your app to .NET Native.</span></span>  
  
 <span data-ttu-id="e37c0-147">.NET Native için varsayılan yapılandırma Çoğu geliştirici için yeterli olmakla birlikte, bazı geliştiriciler ince yapılandırmalarına bir çalışma zamanı yönergeleri kullanarak ayarlama isteyebilirsiniz (. rd.xml) dosyası.</span><span class="sxs-lookup"><span data-stu-id="e37c0-147">The default configuration for .NET Native is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="e37c0-148">Ayrıca, bazı durumlarda, .NET yerel derleyici hangi meta verilerini yansıma için kullanılabilir olmalıdır ve ipuçları, özellikle aşağıdaki durumlarda dayanan belirlenemiyor:</span><span class="sxs-lookup"><span data-stu-id="e37c0-148">In addition, in some cases, the .NET Native compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>  
  
-   <span data-ttu-id="e37c0-149">Bazı yapıları ister <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> ve <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> statik olarak belirlenemez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>  
  
-   <span data-ttu-id="e37c0-150">Derleyici örneklemeleri belirleyemediğinden yansıtmak istediğiniz genel bir tür tarafından çalışma zamanı yönergeleri belirtilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="e37c0-151">Bu, yalnızca tüm kod dahil olması gerektiğinden, ancak genel türlerde yansıma (örneğin, genel türde bir genel yöntem çağrıldığında) sonsuz bir döngü oluşturur çünkü değildir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e37c0-152">Çalışma zamanı yönergeleri, bir çalışma zamanı yönergeleri tanımlanır (. rd.xml) dosyası.</span><span class="sxs-lookup"><span data-stu-id="e37c0-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="e37c0-153">Bu dosyayı kullanma hakkında genel bilgi için bkz. [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="e37c0-153">For general information about using this file, see [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span> <span data-ttu-id="e37c0-154">Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="e37c0-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
 <span data-ttu-id="e37c0-155">.NET native ayrıca profil varsayılan dışındaki hangi tür yansıma desteklemelidir belirlemek geliştiricilere araçları içerir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-155">.NET Native also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a><span data-ttu-id="e37c0-156">Yansıma ile ilgili diğer farklar</span><span class="sxs-lookup"><span data-stu-id="e37c0-156">Other reflection-related differences</span></span>  
 <span data-ttu-id="e37c0-157">Diğer tek tek yansıma ilgili arasındaki davranış farklılıkları .NET için Windows Store uygulamaları ve .NET Native vardır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and .NET Native.</span></span>  
  
 <span data-ttu-id="e37c0-158">.NET yerel:</span><span class="sxs-lookup"><span data-stu-id="e37c0-158">In .NET Native:</span></span>  
  
-   <span data-ttu-id="e37c0-159">Özel yansıma üzerinden türler ve üyeler .NET Framework Sınıf Kitaplığı'nda desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e37c0-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="e37c0-160">Ancak, kendi özel türler ve üyeler, hem de türler ve üyeler üçüncü taraf kitaplıklarındaki üzerinden yansıtacak olabilir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>  
  
-   <span data-ttu-id="e37c0-161"><xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Özelliği doğru bir şekilde döndürür `false` için bir <xref:System.Reflection.ParameterInfo> dönüş değeri temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="e37c0-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="e37c0-162">.NET için Windows Store uygulamalarında döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="e37c0-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="e37c0-163">Ara dil (IL) bu doğrudan desteklemez ve dil yorumu kaldı.</span><span class="sxs-lookup"><span data-stu-id="e37c0-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>  
  
-   <span data-ttu-id="e37c0-164">Ortak üyelerde <xref:System.RuntimeFieldHandle> ve <xref:System.RuntimeMethodHandle> yapıları desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="e37c0-165">Bu tür, yalnızca LINQ ifade ağaçları ve statik dizi başlatma için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>  
  
-   <span data-ttu-id="e37c0-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> ve <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> taban sınıflardaki gizli üyeleri içerir ve bu nedenle açık geçersiz kılmalar geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="e37c0-167">Bu ayrıca diğer true [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="e37c0-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](xref:System.Reflection.RuntimeReflectionExtensions) methods.</span></span>  
  
-   <span data-ttu-id="e37c0-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> belirli birleşimleri (örneğin, zkratka dizisi) oluşturmaya çalıştığınızda başarısız yok.</span><span class="sxs-lookup"><span data-stu-id="e37c0-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>  
  
-   <span data-ttu-id="e37c0-169">Yansıma, işaretçi parametrelere sahip bir üye çağırmak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e37c0-169">You can't use reflection to invoke members that have pointer parameters.</span></span>  
  
-   <span data-ttu-id="e37c0-170">Alınacak veya ayarlanacak bir işaretçi alan yansıma kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e37c0-170">You can't use reflection to get or set a pointer field.</span></span>  
  
-   <span data-ttu-id="e37c0-171">.NET Native oluşturur, bağımsız değişken sayısı yanlış olduğunda ve bağımsız değişkenler birinin türü yanlış bir <xref:System.ArgumentException> yerine bir <xref:System.Reflection.TargetParameterCountException>.</span><span class="sxs-lookup"><span data-stu-id="e37c0-171">When the argument count is wrong and the type of one of the arguments is incorrect, .NET Native throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>  
  
-   <span data-ttu-id="e37c0-172">İkili serileştirme özel durumlar genellikle desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e37c0-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="e37c0-173">Seri hale getirilemeyen nesneleri sonucu olarak eklenebilir <xref:System.Exception.Data%2A?displayProperty=nameWithType> sözlüğü.</span><span class="sxs-lookup"><span data-stu-id="e37c0-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="e37c0-174">Desteklenmeyen senaryolar ve API'ler</span><span class="sxs-lookup"><span data-stu-id="e37c0-174">Unsupported scenarios and APIs</span></span>  
 <span data-ttu-id="e37c0-175">Aşağıdaki bölümlerde, genel geliştirme, birlikte çalışabilirlik ve HTTPClient ve Windows Communication Foundation (WCF) gibi teknolojiler için desteklenmeyen senaryolar ve API'leri listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="e37c0-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>  
  
-   [<span data-ttu-id="e37c0-176">Genel Geliştirme</span><span class="sxs-lookup"><span data-stu-id="e37c0-176">General development</span></span>](#General)  
  
-   [<span data-ttu-id="e37c0-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="e37c0-177">HttpClient</span></span>](#HttpClient)  
  
-   [<span data-ttu-id="e37c0-178">Interop</span><span class="sxs-lookup"><span data-stu-id="e37c0-178">Interop</span></span>](#Interop)  
  
-   [<span data-ttu-id="e37c0-179">Desteklenmeyen API'leri</span><span class="sxs-lookup"><span data-stu-id="e37c0-179">Unsupported APIs</span></span>](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a><span data-ttu-id="e37c0-180">Genel Geliştirme farkları</span><span class="sxs-lookup"><span data-stu-id="e37c0-180">General development differences</span></span>  
 <span data-ttu-id="e37c0-181">**Değer türleri**</span><span class="sxs-lookup"><span data-stu-id="e37c0-181">**Value types**</span></span>  
  
-   <span data-ttu-id="e37c0-182">Kılarsanız <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> ve <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> bir değer türü için yöntemleri taban sınıf uygulamaları çağrı yok.</span><span class="sxs-lookup"><span data-stu-id="e37c0-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="e37c0-183">.NET için Windows Store uygulamalarında yansıma bu yöntemleri kullanan.</span><span class="sxs-lookup"><span data-stu-id="e37c0-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="e37c0-184">Derleme zamanında .NET yerel çalışma zamanı yansıma kullanan olmayan bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e37c0-184">At compile time, .NET Native generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="e37c0-185">Bu, bu iki yöntem geçersiz kılmazsanız .NET yerel derleme zamanında bir uygulama oluşturur çünkü bunlar beklendiği gibi çalışmasını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-185">This means that if you don't override these two methods, they will work as expected, because .NET Native generates the implementation at compile time.</span></span> <span data-ttu-id="e37c0-186">Ancak, bu yöntemleri geçersiz ancak taban sınıf uygulamasını çağırmak bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="e37c0-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>  
  
-   <span data-ttu-id="e37c0-187">Bir megabayttan büyük değer türleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-187">Value types larger than one megabyte aren't supported.</span></span>  
  
-   <span data-ttu-id="e37c0-188">Değer türleri, varsayılan bir oluşturucu .NET Native sahip olamaz.</span><span class="sxs-lookup"><span data-stu-id="e37c0-188">Value types can't have a default constructor in .NET Native.</span></span> <span data-ttu-id="e37c0-189">(C# ve Visual Basic değer türleri üzerinde varsayılan oluşturucular yasaktır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-189">(C# and Visual Basic prohibit default constructors on value types.</span></span> <span data-ttu-id="e37c0-190">Ancak, bunlar IL içinde oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="e37c0-190">However, these can be created in IL.)</span></span>  
  
 <span data-ttu-id="e37c0-191">**Diziler**</span><span class="sxs-lookup"><span data-stu-id="e37c0-191">**Arrays**</span></span>  
  
-   <span data-ttu-id="e37c0-192">Alt sınırı sıfır dışındaki dizilerle desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="e37c0-193">Genellikle, bu dizileri çağrılarak oluşturulmuş <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="e37c0-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
-   <span data-ttu-id="e37c0-194">Dinamik oluşturulmasını çok boyutlu diziler desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e37c0-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="e37c0-195">Bu tür diziler, genellikle bir aşırı yüklemesini çağırarak oluşturulan <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> içeren yöntem bir `lengths` parametresi veya çağırarak <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="e37c0-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="e37c0-196">Dört veya daha fazla boyuta sahip çok boyutlu diziler desteklenmez; diğer bir deyişle, kendi <xref:System.Array.Rank%2A?displayProperty=nameWithType> özellik değeri, dört veya daha büyük.</span><span class="sxs-lookup"><span data-stu-id="e37c0-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="e37c0-197">Kullanım [basit dizileri](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (dizi) bunun yerine.</span><span class="sxs-lookup"><span data-stu-id="e37c0-197">Use [jagged arrays](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="e37c0-198">Örneğin, `array[x,y,z]` geçersiz, ancak `array[x][y][z]` değil.</span><span class="sxs-lookup"><span data-stu-id="e37c0-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>  
  
-   <span data-ttu-id="e37c0-199">Çok boyutlu diziler için varyans desteklenmiyor ve neden olan bir <xref:System.InvalidCastException> çalışma zamanında özel durum.</span><span class="sxs-lookup"><span data-stu-id="e37c0-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>  
  
 <span data-ttu-id="e37c0-200">**Genel Türler**</span><span class="sxs-lookup"><span data-stu-id="e37c0-200">**Generics**</span></span>  
  
-   <span data-ttu-id="e37c0-201">Sınırsız genel tür genişletme bir derleyici hatasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e37c0-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="e37c0-202">Örneğin, bu kodu derlemek başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="e37c0-202">For example, this code fails to compile:</span></span>  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 <span data-ttu-id="e37c0-203">**İşaretçiler**</span><span class="sxs-lookup"><span data-stu-id="e37c0-203">**Pointers**</span></span>  
  
-   <span data-ttu-id="e37c0-204">İşaretçileri dizilerini desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-204">Arrays of pointers aren't supported.</span></span>  
  
-   <span data-ttu-id="e37c0-205">Alınacak veya ayarlanacak bir işaretçi alan yansıma kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="e37c0-205">You can't use reflection to get or set a pointer field.</span></span>  
  
 <span data-ttu-id="e37c0-206">**Serileştirme**</span><span class="sxs-lookup"><span data-stu-id="e37c0-206">**Serialization**</span></span>  
  
 <span data-ttu-id="e37c0-207"><xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Özniteliği desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e37c0-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="e37c0-208">Kullanım <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> yerine özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e37c0-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>  
  
 <span data-ttu-id="e37c0-209">**Kaynaklar**</span><span class="sxs-lookup"><span data-stu-id="e37c0-209">**Resources**</span></span>  
  
 <span data-ttu-id="e37c0-210">Yerelleştirilmiş kaynaklar ile kullanımını <xref:System.Diagnostics.Tracing.EventSource> sınıfı desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e37c0-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="e37c0-211"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Özelliği, yerelleştirilmiş kaynaklar tanımlamıyor.</span><span class="sxs-lookup"><span data-stu-id="e37c0-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>  
  
 <span data-ttu-id="e37c0-212">**Temsilciler**</span><span class="sxs-lookup"><span data-stu-id="e37c0-212">**Delegates**</span></span>  
  
 <span data-ttu-id="e37c0-213">`Delegate.BeginInvoke` ve `Delegate.EndInvoke` desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>  
  
 <span data-ttu-id="e37c0-214">**Çeşitli API'ler**</span><span class="sxs-lookup"><span data-stu-id="e37c0-214">**Miscellaneous APIs**</span></span>  
  
-   <span data-ttu-id="e37c0-215">[TypeInfo.GUID](xref:System.Type.GUID) özelliği oluşturur bir <xref:System.PlatformNotSupportedException> özel durum, bir <xref:System.Runtime.InteropServices.GuidAttribute> öznitelik türü için uygulanan değil.</span><span class="sxs-lookup"><span data-stu-id="e37c0-215">The [TypeInfo.GUID](xref:System.Type.GUID) property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="e37c0-216">GUID kullanılan birincil COM desteği.</span><span class="sxs-lookup"><span data-stu-id="e37c0-216">The GUID is used primarily for COM support.</span></span>  
  
-   <span data-ttu-id="e37c0-217"><xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Yöntemi .NET Native kısa tarihler içeren dizeleri doğru bir şekilde ayrıştırılır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-217">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in .NET Native.</span></span> <span data-ttu-id="e37c0-218">Ancak, tarih değişikliği uyumluluk saklamaz ve zaman ayrıştırma Microsoft Bilgi Bankası makalelerinde açıklandığı [KB2803771](https://support.microsoft.com/kb/2803771) ve [KB2803755](https://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="e37c0-218">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](https://support.microsoft.com/kb/2803771) and [KB2803755](https://support.microsoft.com/kb/2803755).</span></span>  
  
-   <span data-ttu-id="e37c0-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` doğru .NET Native yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-219"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in .NET Native.</span></span> <span data-ttu-id="e37c0-220">CLR'nin bazı sürümleri, sonuç dizesine yerine kesilmiş yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-220">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a><span data-ttu-id="e37c0-221">HttpClient farkları</span><span class="sxs-lookup"><span data-stu-id="e37c0-221">HttpClient differences</span></span>  
 <span data-ttu-id="e37c0-222">.NET Native içinde <xref:System.Net.Http.HttpClientHandler> sınıfı dahili olarak, WinINet kullanır (aracılığıyla <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> sınıfı) yerine <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> standart .NET için Windows Store uygulamalarında kullanılan sınıflar.</span><span class="sxs-lookup"><span data-stu-id="e37c0-222">In .NET Native, the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="e37c0-223">WinINet tüm desteklemiyor yapılandırma seçeneklerini <xref:System.Net.Http.HttpClientHandler> sınıfı destekler.</span><span class="sxs-lookup"><span data-stu-id="e37c0-223">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="e37c0-224">Sonuç olarak:</span><span class="sxs-lookup"><span data-stu-id="e37c0-224">As a result:</span></span>  
  
-   <span data-ttu-id="e37c0-225">Özellik özellikleri bazıları <xref:System.Net.Http.HttpClientHandler> dönüş `false` .NET Native üzerinde döndürmeleri ise `true` standart .NET için Windows Store uygulamalarında.</span><span class="sxs-lookup"><span data-stu-id="e37c0-225">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on .NET Native, whereas they return `true` in the standard .NET for Windows Store apps.</span></span>  
  
-   <span data-ttu-id="e37c0-226">Bazı yapılandırma özelliği `get` erişimcileri her zaman bir sabit değer döndürür üzerinde .NET, .NET için Windows Store apps varsayılan yapılandırılabilir değeri farklı olan yerel.</span><span class="sxs-lookup"><span data-stu-id="e37c0-226">Some of the configuration property `get` accessors always return a fixed value on .NET Native that is different than the default configurable value in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="e37c0-227">Bazı ek davranış farklılıklarının aşağıdaki alt bölümlerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-227">Some additional behavior differences are covered in the following subsections.</span></span>  
  
 <span data-ttu-id="e37c0-228">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="e37c0-228">**Proxy**</span></span>  
  
 <span data-ttu-id="e37c0-229"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Sınıfı, yapılandırma veya istek başına temelinde proxy geçersiz kılmayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-229">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="e37c0-230">Bu .NET Native tüm istekleri sistem yapılandırılmış bir proxy sunucusu veya değerine bağlı olarak, proxy sunucusu kullanmak anlamına gelir <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e37c0-230">This means that all requests on .NET Native use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="e37c0-231">.NET için Windows Store uygulamalarında proxy sunucusu tarafından tanımlanan <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="e37c0-231">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="e37c0-232">Ayarı .NET Native üzerinde <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> dışında bir değere `null` oluşturur bir <xref:System.PlatformNotSupportedException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="e37c0-232">On .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="e37c0-233"><xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Özelliği döndürür `false` .NET Native üzerinde döndürür ancak `true` standart .NET Framework için Windows Store uygulamalarında.</span><span class="sxs-lookup"><span data-stu-id="e37c0-233">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>  
  
 <span data-ttu-id="e37c0-234">**Otomatik yeniden yönlendirme**</span><span class="sxs-lookup"><span data-stu-id="e37c0-234">**Automatic redirection**</span></span>  
  
 <span data-ttu-id="e37c0-235"><xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Sınıfı yapılandırılması için otomatik yeniden yönlendirmeleri sayısı izin vermez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-235">The <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="e37c0-236">Değerini <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> özelliği varsayılan olarak standart .NET için Windows Store apps 50'dir ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-236">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="e37c0-237">.NET Native üzerinde bu özelliğin değeri 10 ve atar değiştirmeye çalışırken bir <xref:System.PlatformNotSupportedException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="e37c0-237">On .NET Native, the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="e37c0-238"><xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Özelliği döndürür `false` .NET Native üzerinde döndürür ancak `true` .NET için Windows Store uygulamalarında.</span><span class="sxs-lookup"><span data-stu-id="e37c0-238">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on .NET Native, whereas it returns `true` in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="e37c0-239">**Otomatik Sıkıştırma**</span><span class="sxs-lookup"><span data-stu-id="e37c0-239">**Automatic decompression**</span></span>  
  
 <span data-ttu-id="e37c0-240">.NET için Windows Store apps ayarlamanıza olanak tanır <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> özelliğini <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>hem <xref:System.Net.DecompressionMethods.Deflate> ve <xref:System.Net.DecompressionMethods.GZip>, veya <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="e37c0-240">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="e37c0-241">Yalnızca .NET native destekler <xref:System.Net.DecompressionMethods.Deflate> ile birlikte <xref:System.Net.DecompressionMethods.GZip>, veya <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="e37c0-241">.NET Native only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="e37c0-242">Ayarlanmaya çalışılırken <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> ya da özellik <xref:System.Net.DecompressionMethods.Deflate> veya <xref:System.Net.DecompressionMethods.GZip> tek başına sessizce hem de ayarlar <xref:System.Net.DecompressionMethods.Deflate> ve <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="e37c0-242">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>  
  
 <span data-ttu-id="e37c0-243">**Çerezler**</span><span class="sxs-lookup"><span data-stu-id="e37c0-243">**Cookies**</span></span>  
  
 <span data-ttu-id="e37c0-244">Tanımlama bilgisi işleme ile aynı anda gerçekleştirilen <xref:System.Net.Http.HttpClient> ve WinINet.</span><span class="sxs-lookup"><span data-stu-id="e37c0-244">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="e37c0-245">Tanımlama bilgilerine <xref:System.Net.CookieContainer> WinINet tanımlama bilgisi önbelleğinde tanımlama bilgileri ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-245">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="e37c0-246">Tanımlama bilgisinden kaldırma <xref:System.Net.CookieContainer> engeller <xref:System.Net.Http.HttpClient> tanımlama bilgisi, zaten WinINet tarafından görülen ve tanımlama bilgileri, kullanıcı tarafından silinmiş olmayan ancak tanımlama bilgisi göndermesini WinINet gönderir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-246">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="e37c0-247">Program aracılığıyla kullanarak bir tanımlama bilgisi WinINet kaldırmak mümkün değildir <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, veya <xref:System.Net.CookieContainer> API.</span><span class="sxs-lookup"><span data-stu-id="e37c0-247">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="e37c0-248">Ayarı <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> özelliğini `false` yalnızca neden <xref:System.Net.Http.HttpClient> tanımlama bilgileri göndermeyi durdurun WinINet, yine de isteğinde, tanımlama bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-248">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>  
  
 <span data-ttu-id="e37c0-249">**Kimlik bilgileri**</span><span class="sxs-lookup"><span data-stu-id="e37c0-249">**Credentials**</span></span>  
  
 <span data-ttu-id="e37c0-250">.NET için Windows Store uygulamalarında <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> ve <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> özellikleri bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-250">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="e37c0-251">Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği uygulayan nesne kabul eden <xref:System.Net.ICredentials> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e37c0-251">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="e37c0-252">Ayarı .NET Native içinde <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> özelliğini `true` neden <xref:System.Net.Http.HttpClientHandler.Credentials%2A> olacak özelliği `null`.</span><span class="sxs-lookup"><span data-stu-id="e37c0-252">In .NET Native, setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="e37c0-253">Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği yalnızca ayarlanabilir `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, veya bir nesne türü <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="e37c0-253">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="e37c0-254">Diğer atama <xref:System.Net.ICredentials> en popüler olan nesne, <xref:System.Net.CredentialCache>, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği oluşturur bir <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="e37c0-254">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>  
  
 <span data-ttu-id="e37c0-255">**Diğer desteklenmeyen veya unconfigurable özellikleri**</span><span class="sxs-lookup"><span data-stu-id="e37c0-255">**Other unsupported or unconfigurable features**</span></span>  
  
 <span data-ttu-id="e37c0-256">.NET yerel:</span><span class="sxs-lookup"><span data-stu-id="e37c0-256">In .NET Native:</span></span>  
  
-   <span data-ttu-id="e37c0-257">Değerini <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> özelliği her zaman <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="e37c0-257">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="e37c0-258">.NET için Windows Store uygulamalarında varsayılandır <xref:System.Net.Http.ClientCertificateOption.Manual>.</span><span class="sxs-lookup"><span data-stu-id="e37c0-258">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>  
  
-   <span data-ttu-id="e37c0-259"><xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Özelliği yapılandırılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-259">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>  
  
-   <span data-ttu-id="e37c0-260"><xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Özelliği her zaman `true`.</span><span class="sxs-lookup"><span data-stu-id="e37c0-260">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="e37c0-261">.NET için Windows Store uygulamalarında varsayılandır `false`.</span><span class="sxs-lookup"><span data-stu-id="e37c0-261">In .NET for Windows Store apps, the default is `false`.</span></span>  
  
-   <span data-ttu-id="e37c0-262">`SetCookie2` Yanıtları üstbilgisinde eski olarak sayılır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-262">The `SetCookie2` header in responses is ignored as obsolete.</span></span>  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a><span data-ttu-id="e37c0-263">Birlikte çalışma farkları</span><span class="sxs-lookup"><span data-stu-id="e37c0-263">Interop differences</span></span>  
 <span data-ttu-id="e37c0-264">**Kaldırılmış API'ler**</span><span class="sxs-lookup"><span data-stu-id="e37c0-264">**Deprecated APIs**</span></span>  
  
 <span data-ttu-id="e37c0-265">Yönetilen kod ile birlikte çalışabilirlik için sık kullanılan API'ler birkaç kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="e37c0-265">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="e37c0-266">Bu API'ler .NET Native ile kullanıldığında, oluşturabilecek bir <xref:System.NotImplementedException> veya <xref:System.PlatformNotSupportedException> özel durum ya da bir derleyici hatası sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="e37c0-266">When used with .NET Native, these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="e37c0-267">Bunların çağrılması bir derleyici hatası yerine derleyici uyarısı oluşturur ancak .NET için Windows Store uygulamalarında bu API'leri eski işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="e37c0-267">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>  
  
 <span data-ttu-id="e37c0-268">API'ler için kullanım dışı `VARIANT` hazırlamayı içerir:</span><span class="sxs-lookup"><span data-stu-id="e37c0-268">Deprecated APIs for `VARIANT` marshaling include:</span></span>  

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>  
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>  
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>
  
 <span data-ttu-id="e37c0-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> desteklenir, ancak bir özel durum ile kullanıldığında gibi bazı senaryolarda oluşturur [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) veya türevleri byref.</span><span class="sxs-lookup"><span data-stu-id="e37c0-269"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) or byref variants.</span></span>  
  
 <span data-ttu-id="e37c0-270">API'ler için kullanım dışı [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) desteğini içerir:</span><span class="sxs-lookup"><span data-stu-id="e37c0-270">Deprecated APIs for [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) support include:</span></span>  
  
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName> 
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>  

<span data-ttu-id="e37c0-271">Kaldırılmış API'ler klasik COM olayları için şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="e37c0-271">Deprecated APIs for classic COM events include:</span></span>

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>
  
<span data-ttu-id="e37c0-272">Kullanım dışı API'leri <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> .NET Native desteklenmiyor, arabirim gösterilebilir:</span><span class="sxs-lookup"><span data-stu-id="e37c0-272">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in .NET Native, include:</span></span>  
  
- <span data-ttu-id="e37c0-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (tüm üyeler)</span><span class="sxs-lookup"><span data-stu-id="e37c0-273"><xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (all members)</span></span>  
- <span data-ttu-id="e37c0-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (tüm üyeler)</span><span class="sxs-lookup"><span data-stu-id="e37c0-274"><xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (all members)</span></span>  
- <span data-ttu-id="e37c0-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (tüm üyeler)</span><span class="sxs-lookup"><span data-stu-id="e37c0-275"><xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (all members)</span></span>  
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>  
  
<span data-ttu-id="e37c0-276">Diğer desteklenmeyen birlikte çalışma özellikleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e37c0-276">Other unsupported interop features include:</span></span>  
  
- <span data-ttu-id="e37c0-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (tüm üyeler)</span><span class="sxs-lookup"><span data-stu-id="e37c0-277"><xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (all members)</span></span>  
- <span data-ttu-id="e37c0-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (tüm üyeler)</span><span class="sxs-lookup"><span data-stu-id="e37c0-278"><xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (all members)</span></span>  
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>  
  
 <span data-ttu-id="e37c0-279">Hazırlama API nadiren kullanılır:</span><span class="sxs-lookup"><span data-stu-id="e37c0-279">Rarely used marshalling APIs:</span></span>  
  
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
  
 <span data-ttu-id="e37c0-280">**Platform çağırma ve COM birlikte çalışma uyumluluğu**</span><span class="sxs-lookup"><span data-stu-id="e37c0-280">**Platform invoke and COM interop compatibility**</span></span>  
  
 <span data-ttu-id="e37c0-281">Çoğu platform çağırma ve COM birlikte çalışma senaryolar hala .NET Native desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-281">Most platform invoke and COM interop scenarios are still supported in .NET Native.</span></span> <span data-ttu-id="e37c0-282">Özellikle, Windows çalışma zamanı (WinRT) API'leri ile tüm birlikte çalışabilirlik ve Windows çalışma zamanı için gerekli tüm hazırlama desteklenir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-282">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="e37c0-283">Bu, sıralama için destek içerir:</span><span class="sxs-lookup"><span data-stu-id="e37c0-283">This includes marshaling support for:</span></span>  
  
-   <span data-ttu-id="e37c0-284">Diziler (dahil olmak üzere <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="e37c0-284">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>  
  
-   `BStr`  
  
-   <span data-ttu-id="e37c0-285">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="e37c0-285">Delegates</span></span>  
  
-   <span data-ttu-id="e37c0-286">Dizeler (Unicode, ANSI ve HSTRING)</span><span class="sxs-lookup"><span data-stu-id="e37c0-286">Strings (Unicode, Ansi, and HSTRING)</span></span>  
  
-   <span data-ttu-id="e37c0-287">Yapılar (`byref` ve `byval`)</span><span class="sxs-lookup"><span data-stu-id="e37c0-287">Structs (`byref` and `byval`)</span></span>  
  
-   <span data-ttu-id="e37c0-288">Birleşimler</span><span class="sxs-lookup"><span data-stu-id="e37c0-288">Unions</span></span>  
  
-   <span data-ttu-id="e37c0-289">Win32 tanıtıcıları</span><span class="sxs-lookup"><span data-stu-id="e37c0-289">Win32 handles</span></span>  
  
-   <span data-ttu-id="e37c0-290">Tüm WinRT yapıları</span><span class="sxs-lookup"><span data-stu-id="e37c0-290">All WinRT constructs</span></span>  
  
-   <span data-ttu-id="e37c0-291">VARIANT türlerini hazırlama için kısmi destek.</span><span class="sxs-lookup"><span data-stu-id="e37c0-291">Partial support for marshaling variant types.</span></span> <span data-ttu-id="e37c0-292">Aşağıdakiler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="e37c0-292">The following are supported:</span></span>  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [<span data-ttu-id="e37c0-293">IUnknown</span><span class="sxs-lookup"><span data-stu-id="e37c0-293">IUnknown</span></span>](/windows/desktop/api/unknwn/nn-unknwn-iunknown)  
  
 <span data-ttu-id="e37c0-294">Ancak, .NET Native aşağıdakileri desteklemez:</span><span class="sxs-lookup"><span data-stu-id="e37c0-294">However, .NET Native doesn't support the following:</span></span>  
  
-   <span data-ttu-id="e37c0-295">Kullanarak klasik COM olayları</span><span class="sxs-lookup"><span data-stu-id="e37c0-295">Using classic COM events</span></span>  
  
-   <span data-ttu-id="e37c0-296">Uygulama <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> yönetilen tür arabirimi</span><span class="sxs-lookup"><span data-stu-id="e37c0-296">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>  
  
-   <span data-ttu-id="e37c0-297">Uygulama [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) arabirimi yönetilen türe göre <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="e37c0-297">Implementing the [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="e37c0-298">Ancak, COM nesneleri aracılığıyla çağrılamıyor unutmayın `IDispatch`, ve yönetilen nesnenizin uygulayamaz `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="e37c0-298">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>  
  
 <span data-ttu-id="e37c0-299">Yansıma kullanarak bir platform çağırma yöntemi çağırma desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="e37c0-299">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="e37c0-300">Başka bir yöntem yöntem çağrısının sarmalama ve bunun yerine sarmalayıcı çağırmak için yansıma kullanarak bu sınırlandırma çerçevesinde çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e37c0-300">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="e37c0-301">.NET API için Windows Store uygulamalarından diğer farklar</span><span class="sxs-lookup"><span data-stu-id="e37c0-301">Other differences from .NET APIs for Windows Store apps</span></span>  
 <span data-ttu-id="e37c0-302">Bu bölüm .NET Native desteklenmeyen kalan API'ları listeler.</span><span class="sxs-lookup"><span data-stu-id="e37c0-302">This section lists the remaining APIs that aren't supported in .NET Native.</span></span> <span data-ttu-id="e37c0-303">Windows Communication Foundation (WCF) API'leri en büyük dizi desteklenmeyen API var.</span><span class="sxs-lookup"><span data-stu-id="e37c0-303">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>  
  
 <span data-ttu-id="e37c0-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="e37c0-304">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>  
  
 <span data-ttu-id="e37c0-305">Türlerinde <xref:System.ComponentModel.DataAnnotations> ve <xref:System.ComponentModel.DataAnnotations.Schema> ad alanları .NET Native desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-305">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in .NET Native.</span></span> <span data-ttu-id="e37c0-306">Bu, Windows 8 için .NET için Windows Store apps bulunan aşağıdaki türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e37c0-306">These include the following types that are present in .NET for Windows Store apps for Windows 8:</span></span>  
  
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
  
 <span data-ttu-id="e37c0-307">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="e37c0-307">**Visual Basic**</span></span>  
  
 <span data-ttu-id="e37c0-308">Visual Basic .NET Native şu anda desteklenmemektedir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-308">Visual Basic isn't currently supported in .NET Native.</span></span> <span data-ttu-id="e37c0-309">Aşağıdaki türleri içinde <xref:Microsoft.VisualBasic> ve <xref:Microsoft.VisualBasic.CompilerServices> ad alanları .NET Native kullanıma sunulmaz:</span><span class="sxs-lookup"><span data-stu-id="e37c0-309">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in .NET Native:</span></span>  

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
  
 <span data-ttu-id="e37c0-310">**Yansıma bağlam (System.Reflection.Context ad alanı)**</span><span class="sxs-lookup"><span data-stu-id="e37c0-310">**Reflection Context (System.Reflection.Context namespace)**</span></span>  
  
 <span data-ttu-id="e37c0-311"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Sınıfı .NET Native desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-311">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in .NET Native.</span></span>  
  
 <span data-ttu-id="e37c0-312">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="e37c0-312">**RTC (System.Net.Http.Rtc)**</span></span>  
  
 <span data-ttu-id="e37c0-313">`System.Net.Http.RtcRequestFactory` Sınıfı .NET Native desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-313">The `System.Net.Http.RtcRequestFactory` class isn't supported in .NET Native.</span></span>  
  
 <span data-ttu-id="e37c0-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="e37c0-314">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>  
  
 <span data-ttu-id="e37c0-315">Türlerinde [System.ServiceModel.\* ad alanları](xref:System.ServiceModel) .NET Native desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-315">The types in the [System.ServiceModel.\* namespaces](xref:System.ServiceModel) aren't supported in .NET Native.</span></span> <span data-ttu-id="e37c0-316">Bunlar aşağıdaki türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="e37c0-316">These includes the following types:</span></span>  
  
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
  
### <a name="differences-in-serializers"></a><span data-ttu-id="e37c0-317">Seri hale getiricileri genişletme farklılıkları</span><span class="sxs-lookup"><span data-stu-id="e37c0-317">Differences in serializers</span></span>  
 <span data-ttu-id="e37c0-318">Aşağıdaki farklar ilgilendiriyor serileştirme ve seri durumdan çıkarma ile <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer> sınıflar:</span><span class="sxs-lookup"><span data-stu-id="e37c0-318">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>  
  
-   <span data-ttu-id="e37c0-319">.NET Native içinde <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serileştirmek veya seri durumdan türü olmayan bir kök serileştirme türü bir temel sınıf üyesinin türetilmiş bir sınıf başarısız.</span><span class="sxs-lookup"><span data-stu-id="e37c0-319">In .NET Native, <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="e37c0-320">Örneğin, aşağıdaki kodda, serileştirmek veya seri durumdan çalışılırken `Y` hatayla sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="e37c0-320">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     <span data-ttu-id="e37c0-321">Tür `InnerType` seri hale getirici için temel sınıf üyelerini serileştirme sırasında geçiş değildir çünkü bilinen değil.</span><span class="sxs-lookup"><span data-stu-id="e37c0-321">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>  
  
-   <span data-ttu-id="e37c0-322"><xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sınıf veya yapı uygulayan serileştirmek başarısız <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e37c0-322"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="e37c0-323">Örneğin, aşağıdaki türleri serileştirmek veya seri durumdan çıkarmak başarısız:</span><span class="sxs-lookup"><span data-stu-id="e37c0-323">For example, the following types fail to serialize or deserialize:</span></span>  
  
  
  
-   <span data-ttu-id="e37c0-324"><xref:System.Xml.Serialization.XmlSerializer> serileştirilecek nesnenin tam tür bilmediği aşağıdaki nesne değeri serileştirmek başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="e37c0-324"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>  
  
  
  
-   <span data-ttu-id="e37c0-325"><xref:System.Xml.Serialization.XmlSerializer> serileştirmek veya seri hale getirilmiş nesne türü ise seri durumdan başaramıyor <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="e37c0-325"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>  
  
-   <span data-ttu-id="e37c0-326">Tüm seri hale getiricileri genişletme (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer>) tür için serileştirme kod oluşturmak başarısız <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> ya da içeren bir tür için <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e37c0-326">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="e37c0-327">Bunlar bunun yerine derleme zamanı hataları görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="e37c0-327">They display build-time errors instead.</span></span>  
  
-   <span data-ttu-id="e37c0-328">Seri hale getirme türlerinde şu oluşturuculardan beklendiği şekilde çalışması için garantili değildir:</span><span class="sxs-lookup"><span data-stu-id="e37c0-328">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>  
  
-   <span data-ttu-id="e37c0-329"><xref:System.Xml.Serialization.XmlSerializer> Aşağıdaki özniteliklerden birini öznitelikli yöntem olan bir türü için kod oluşturmak üzere başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="e37c0-329"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <span data-ttu-id="e37c0-330"><xref:System.Xml.Serialization.XmlSerializer> ne uygun olmayan <xref:System.Xml.Serialization.IXmlSerializable> özel seri hale getirme arabirimi.</span><span class="sxs-lookup"><span data-stu-id="e37c0-330"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="e37c0-331">Bu arabirimi uygulayan bir sınıf varsa <xref:System.Xml.Serialization.XmlSerializer> türü düz eski bir CLR nesnesi (POCO) türü olarak değerlendirir ve yalnızca genel özelliklerini serileştirir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-331">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>  
  
-   <span data-ttu-id="e37c0-332">Düz bir'seri hale getirme <xref:System.Exception> nesne ile iyi çalışmaz <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e37c0-332">Serializing a plain <xref:System.Exception> object doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>.</span></span>

<a name="VS"></a>   
## <a name="visual-studio-differences"></a><span data-ttu-id="e37c0-333">Visual Studio farkları</span><span class="sxs-lookup"><span data-stu-id="e37c0-333">Visual Studio differences</span></span>  
 <span data-ttu-id="e37c0-334">**Özel durumlar ve hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="e37c0-334">**Exceptions and debugging**</span></span>  
  
 <span data-ttu-id="e37c0-335">.NET yerel hata ayıklayıcıda kullanılarak derlenmiş uygulamalar çalıştırırken, ilk şans özel durumlar aşağıdaki özel durum türleri için etkinleştirilir:</span><span class="sxs-lookup"><span data-stu-id="e37c0-335">When you're running apps compiled by using .NET Native in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 <span data-ttu-id="e37c0-336">**Uygulamaları oluşturma**</span><span class="sxs-lookup"><span data-stu-id="e37c0-336">**Building apps**</span></span>  
  
 <span data-ttu-id="e37c0-337">Varsayılan olarak Visual Studio tarafından kullanılan x86 derleme araçlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e37c0-337">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="e37c0-338">C:\Program Files (x86)\MSBuild\12.0\bin\amd64; bulunan AMD64 MSBuild araçları kullanımı önerilmemektedir Bu derleme sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e37c0-338">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>  
  
 <span data-ttu-id="e37c0-339">**Profil oluşturucular**</span><span class="sxs-lookup"><span data-stu-id="e37c0-339">**Profilers**</span></span>  
  
-   <span data-ttu-id="e37c0-340">Visual Studio CPU Profiler ve XAML bellek Profiler Just My-kod düzgün görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-340">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>  
  
-   <span data-ttu-id="e37c0-341">XAML bellek Profiler, yönetilen yığın verileri doğru bir şekilde görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="e37c0-341">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>  
  
-   <span data-ttu-id="e37c0-342">CPU Profiler doğru modülleri belirlemek değil ve işlev adlarını görüntüler öneki.</span><span class="sxs-lookup"><span data-stu-id="e37c0-342">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>  
  
 <span data-ttu-id="e37c0-343">**Birim testi kitaplığı projeleri**</span><span class="sxs-lookup"><span data-stu-id="e37c0-343">**Unit Test Library projects**</span></span>  
  
 <span data-ttu-id="e37c0-344">.NET yerel bir Windows Store uygulamaları projesi için bir birim testi kitaplığı üzerindeki etkinleştirme desteklenmez ve projeyi oluşturmak başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="e37c0-344">Enabling .NET Native on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e37c0-345">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e37c0-345">See also</span></span>
- [<span data-ttu-id="e37c0-346">Başlarken</span><span class="sxs-lookup"><span data-stu-id="e37c0-346">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [<span data-ttu-id="e37c0-347">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="e37c0-347">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="e37c0-348">.NET için Windows Store uygulamalarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="e37c0-348">.NET For Windows Store apps overview</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [<span data-ttu-id="e37c0-349">Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği</span><span class="sxs-lookup"><span data-stu-id="e37c0-349">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
