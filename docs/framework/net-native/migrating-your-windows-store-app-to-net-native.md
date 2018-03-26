---
title: Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ce23d66f79f94af74250cff137499f6c8b1582ac
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="migrating-your-windows-store-app-to-net-native"></a><span data-ttu-id="77b36-102">Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma</span><span class="sxs-lookup"><span data-stu-id="77b36-102">Migrating Your Windows Store App to .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="77b36-103"> uygulamaların Windows Mağazası'nda veya geliştiricinin bilgisayarda statik derleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="77b36-103"> provides static compilation of apps in the Windows Store or on the developer’s computer.</span></span> <span data-ttu-id="77b36-104">Bu Windows mağazası uygulamaları için tam zamanında (JIT) derleyici tarafından gerçekleştirilen dinamik derleme farklıdır veya [yerel Görüntü Oluşturucu (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) cihazda.</span><span class="sxs-lookup"><span data-stu-id="77b36-104">This differs from the dynamic compilation performed for Windows Store apps by the just-in-time (JIT) compiler or the [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) on the device.</span></span> <span data-ttu-id="77b36-105">Farkları rağmen [!INCLUDE[net_native](../../../includes/net-native-md.md)] ile uyumluluğu korumak çalışır [.NET için Windows mağazası uygulamaları](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span><span class="sxs-lookup"><span data-stu-id="77b36-105">Despite the differences, [!INCLUDE[net_native](../../../includes/net-native-md.md)] tries to maintain compatibility with the [.NET for Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br230302.aspx).</span></span> <span data-ttu-id="77b36-106">Çoğunlukla, .NET için Windows mağazası uygulamaları üzerinde çalışır şeyler de çalışmak [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-106">For the most part, things that work on the .NET for Windows Store apps also work with [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  <span data-ttu-id="77b36-107">Ancak, bazı durumlarda davranış değişiklikleri karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77b36-107">However, in some cases, you may encounter behavioral changes.</span></span> <span data-ttu-id="77b36-108">Bu belge standart .NET için Windows mağazası uygulamaları arasındaki bu farklılıkları açıklar ve [!INCLUDE[net_native](../../../includes/net-native-md.md)] aşağıdaki alanlarda:</span><span class="sxs-lookup"><span data-stu-id="77b36-108">This document discusses these differences between the standard .NET for Windows Store apps and [!INCLUDE[net_native](../../../includes/net-native-md.md)] in the following areas:</span></span>  
  
-   [<span data-ttu-id="77b36-109">Genel çalışma zamanı farklar</span><span class="sxs-lookup"><span data-stu-id="77b36-109">General runtime differences</span></span>](#Runtime)  
  
-   [<span data-ttu-id="77b36-110">Dinamik programlama farkları</span><span class="sxs-lookup"><span data-stu-id="77b36-110">Dynamic programming differences</span></span>](#Dynamic)  
  
-   [<span data-ttu-id="77b36-111">Yansıma ile ilgili diğer farklar</span><span class="sxs-lookup"><span data-stu-id="77b36-111">Other reflection-related differences</span></span>](#Reflection)  
  
-   [<span data-ttu-id="77b36-112">Desteklenmeyen senaryolar ve API'leri</span><span class="sxs-lookup"><span data-stu-id="77b36-112">Unsupported scenarios and APIs</span></span>](#Unsupported)  
  
-   [<span data-ttu-id="77b36-113">Visual Studio farklar</span><span class="sxs-lookup"><span data-stu-id="77b36-113">Visual Studio differences</span></span>](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a><span data-ttu-id="77b36-114">Genel çalışma zamanı farklar</span><span class="sxs-lookup"><span data-stu-id="77b36-114">General runtime differences</span></span>  
  
-   <span data-ttu-id="77b36-115">Özel durumlar gibi <xref:System.TypeLoadException>, durum JIT Derleyici tarafından üzerinde ortak bir uygulama çalıştırdığında dil çalışma zamanı (CLR) genellikle neden tarafından işlendiğinde derleme zamanı hataları [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-115">Exceptions, such as <xref:System.TypeLoadException>, that are thrown by the JIT compiler when an app runs on the common language runtime (CLR) generally result in compile-time errors when processed by [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="77b36-116">Çağrı yok <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> bir uygulamanın kullanıcı Arabirimi iş parçacığı yönteminden.</span><span class="sxs-lookup"><span data-stu-id="77b36-116">Don't call the <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> method from an app's UI thread.</span></span> <span data-ttu-id="77b36-117">Bu üzerinde bir kilitlenmeyle sonuçlanabilir [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-117">This can result in a deadlock on [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
-   <span data-ttu-id="77b36-118">Statik sınıf oluşturucu çağırma sıralama güvenmeyin.</span><span class="sxs-lookup"><span data-stu-id="77b36-118">Don't rely on static class constructor invocation ordering.</span></span> <span data-ttu-id="77b36-119">İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], çağırma sırası standart çalışma zamanı siparişte farklıdır.</span><span class="sxs-lookup"><span data-stu-id="77b36-119">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the invocation order is different from the order on the standard runtime.</span></span> <span data-ttu-id="77b36-120">(Hatta standart çalışma zamanı ile statik sınıf oluşturucular yürütme terabayt güvenmemelisiniz.)</span><span class="sxs-lookup"><span data-stu-id="77b36-120">(Even with the standard runtime, you shouldn't rely on the order of execution of static class constructors.)</span></span>  
  
-   <span data-ttu-id="77b36-121">Döngü sonsuz bir çağrı yapmaya gerek olmadan (örneğin, `while(true);`) herhangi bir iş parçacığı üzerinde uygulama durdurmak için getir.</span><span class="sxs-lookup"><span data-stu-id="77b36-121">Infinite looping without making a call (for example, `while(true);`) on any thread may bring the app to a halt.</span></span> <span data-ttu-id="77b36-122">Benzer şekilde, büyük ya da sonsuz bekler uygulama getirin ve bu da durdurmak için.</span><span class="sxs-lookup"><span data-stu-id="77b36-122">Similarly, large or infinite waits may bring the app to a halt.</span></span>  
  
-   <span data-ttu-id="77b36-123">Bazı genel başlatma döngüleri özel durumlar oluşturma yok [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-123">Certain generic initialization cycles don't throw exceptions in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="77b36-124">Örneğin, aşağıdaki atar kod bir <xref:System.TypeLoadException> standart CLR özel durum.</span><span class="sxs-lookup"><span data-stu-id="77b36-124">For example, the following code throws a <xref:System.TypeLoadException> exception on the standard CLR.</span></span> <span data-ttu-id="77b36-125">İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], yoktur.</span><span class="sxs-lookup"><span data-stu-id="77b36-125">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], it doesn't.</span></span>  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   <span data-ttu-id="77b36-126">Bazı durumlarda, [!INCLUDE[net_native](../../../includes/net-native-md.md)] .NET Framework sınıf kitaplıkları farklı uygulamaları sağlar.</span><span class="sxs-lookup"><span data-stu-id="77b36-126">In some cases, [!INCLUDE[net_native](../../../includes/net-native-md.md)] provides different implementations of .NET Framework class libraries.</span></span> <span data-ttu-id="77b36-127">Bir yönteminden döndürülen nesne her zaman döndürülen tür üyeleri gerçekleştireceksiniz.</span><span class="sxs-lookup"><span data-stu-id="77b36-127">An object returned from a method will always implement the members of the returned type.</span></span> <span data-ttu-id="77b36-128">Yedekleme uygulaması farklı olduğundan, Bununla birlikte, diğer .NET Framework platformlarda de türleri aynı kümesine yayınlanamıyor mümkün olabilir değil.</span><span class="sxs-lookup"><span data-stu-id="77b36-128">However, since its backing implementation is different, you may not be able to cast it to the same set of types as you could on other .NET Framework platforms.</span></span> <span data-ttu-id="77b36-129">Örneğin, bazı durumlarda, cast mümkün olmayabilir <xref:System.Collections.Generic.IEnumerable%601> gibi yöntemler tarafından döndürülen arabirimi nesnesi <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> veya <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> için `T[]`.</span><span class="sxs-lookup"><span data-stu-id="77b36-129">For example, in some cases, you may not be able to cast the <xref:System.Collections.Generic.IEnumerable%601> interface object returned by methods such as <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> or <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> to `T[]`.</span></span>  
  
-   <span data-ttu-id="77b36-130">WinINet önbellek .NET için Windows mağazası uygulamaları üzerinde varsayılan olarak etkin değildir, ancak açıktır [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-130">The WinInet cache isn't enabled by default on .NET for Windows Store apps, but it is on [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="77b36-131">Bu performansı artırır ancak kümesi etkileri çalışma sahiptir.</span><span class="sxs-lookup"><span data-stu-id="77b36-131">This improves performance but has working set implications.</span></span> <span data-ttu-id="77b36-132">Herhangi bir geliştirici eylemi gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="77b36-132">No developer action is necessary.</span></span>  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a><span data-ttu-id="77b36-133">Dinamik programlama farkları</span><span class="sxs-lookup"><span data-stu-id="77b36-133">Dynamic programming differences</span></span>  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="77b36-134"> kodu en yüksek performans için uygulama yerel kod yapmak için .NET Framework ile statik olarak bağlar.</span><span class="sxs-lookup"><span data-stu-id="77b36-134"> statically links in code from the .NET Framework to make the code app-local for maximum performance.</span></span> <span data-ttu-id="77b36-135">Ancak, ikili boyutları tüm .NET Framework duruma getirilemiyor böylece küçük, kalması gerekir.</span><span class="sxs-lookup"><span data-stu-id="77b36-135">However, binary sizes have to remain small, so the entire .NET Framework can't be brought in.</span></span> <span data-ttu-id="77b36-136">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Derleyici kullanılmayan kod başvuruları kaldırır bir bağımlılık reducer kullanarak bu sınırlamaya giderir.</span><span class="sxs-lookup"><span data-stu-id="77b36-136">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler resolves this limitation by using a dependency reducer that removes references to unused code.</span></span> <span data-ttu-id="77b36-137">Ancak, [!INCLUDE[net_native](../../../includes/net-native-md.md)] korumak veya olmayabilir bu bilgileri derleme zamanında statik olarak çıkarsanamıyor, ancak bunun yerine çalışma zamanında dinamik olarak alınır olduğunda bazı tür bilgilerini ve kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77b36-137">However, [!INCLUDE[net_native](../../../includes/net-native-md.md)] might not maintain or generate some type information and code when that information can't be inferred statically at compile time, but instead is retrieved dynamically at runtime.</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="77b36-138"> Yansıma ve dinamik programlama etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="77b36-138"> does enable reflection and dynamic programming.</span></span> <span data-ttu-id="77b36-139">Ancak, tüm türleri (özellikle .NET Framework'teki ortak API'ler yansıtacak şekilde desteklendiğinden) bu oluşturulan kod boyutu çok büyük yapmayacağı yansıma için işaretlenebilir.</span><span class="sxs-lookup"><span data-stu-id="77b36-139">However, not all types can be marked for reflection, because this would make the generated code size too large (especially because reflecting on public APIs in the .NET Framework is supported).</span></span> <span data-ttu-id="77b36-140">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Derleyici hangi türlerini yansıma desteklemesi ve meta veriler tutar ve yalnızca bu türleri için kod oluşturur akıllı seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="77b36-140">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler makes smart choices about which types should support reflection, and it keeps the metadata and generates code only for those types.</span></span>  
  
 <span data-ttu-id="77b36-141">Örneğin, veri bağlama özellik adları işlevlere Eşle yapabilmek için bir uygulama gerekiyor.</span><span class="sxs-lookup"><span data-stu-id="77b36-141">For example, data binding requires an app to be able to map property names to functions.</span></span> <span data-ttu-id="77b36-142">.NET için Windows mağazası uygulamalarında ortak dil çalışma zamanı yansıma yönetilen türler ve genel kullanıma açık yerel türleri için bu yeteneği sağlamak için otomatik olarak kullanır.</span><span class="sxs-lookup"><span data-stu-id="77b36-142">In .NET for Windows Store apps, the common language runtime automatically uses reflection to provide this capability for managed types and publicly available native types.</span></span> <span data-ttu-id="77b36-143">İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], derleyici meta verileri için bağladığınız türleri için otomatik olarak ekler.</span><span class="sxs-lookup"><span data-stu-id="77b36-143">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the compiler automatically includes metadata for types to which you bind data.</span></span>  
  
 <span data-ttu-id="77b36-144">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Derleyici de gibi yaygın olarak kullanılan genel türleri işlemek <xref:System.Collections.Generic.List%601> ve <xref:System.Collections.Generic.Dictionary%602>, hangi herhangi bir ipuçları veya yönergeleri gerektirmeden çalışır.</span><span class="sxs-lookup"><span data-stu-id="77b36-144">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler can also handle commonly used generic types such as <xref:System.Collections.Generic.List%601> and <xref:System.Collections.Generic.Dictionary%602>, which work without requiring any hints or directives.</span></span> <span data-ttu-id="77b36-145">[Dinamik](~/docs/csharp/language-reference/keywords/dynamic.md) anahtar sözcüğü belirli sınırları içinde de desteklenir.</span><span class="sxs-lookup"><span data-stu-id="77b36-145">The [dynamic](~/docs/csharp/language-reference/keywords/dynamic.md) keyword is also supported within certain limits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77b36-146">Tüm dinamik kod yollarının uygulamanıza bağlantı noktası oluşturma, sınamanız gerekir [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-146">You should test all dynamic code paths thoroughly when porting your app to [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="77b36-147">İçin varsayılan yapılandırmayı [!INCLUDE[net_native](../../../includes/net-native-md.md)] için çoğu geliştirici, ancak bazı geliştiriciler ince yapılandırmalarına çalışma zamanı yönergeleri kullanarak ayarlama isteyebilirsiniz yeterlidir (. rd.xml) dosyası.</span><span class="sxs-lookup"><span data-stu-id="77b36-147">The default configuration for [!INCLUDE[net_native](../../../includes/net-native-md.md)] is sufficient for most developers, but some developers might want to fine- tune their configurations by using a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="77b36-148">Ayrıca, bazı durumlarda, [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleyici hangi meta verilerini yansıma için kullanılabilir olmalıdır ve ipuçları, aşağıdaki durumlarda özellikle dayanır belirlenemiyor:</span><span class="sxs-lookup"><span data-stu-id="77b36-148">In addition, in some cases, the [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiler is unable to determine which metadata must be available for reflection and relies on hints, particularly in the following cases:</span></span>  
  
-   <span data-ttu-id="77b36-149">Bazı yapıları ister <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> ve <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> statik olarak belirlenemez.</span><span class="sxs-lookup"><span data-stu-id="77b36-149">Some constructs like <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> and <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> can't be determined statically.</span></span>  
  
-   <span data-ttu-id="77b36-150">Derleyici örneklemesi belirleyemediğinden yansıtmak istediğiniz genel bir tür çalışma zamanı yönergeleri tarafından belirtilmiş olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="77b36-150">Because the compiler can't determine the instantiations, a generic type that you want to reflect on has to be specified by runtime directives.</span></span> <span data-ttu-id="77b36-151">Bu, yalnızca tüm kod dahil olması gerektiğinden, ancak genel türlerde yansıma sonsuz bir döngü (örneğin, genel türde bir genel yöntem çağrıldığında) form çünkü değildir.</span><span class="sxs-lookup"><span data-stu-id="77b36-151">This isn't just because all code must be included, but because reflection on generic types can form an infinite cycle (for example, when a generic method is invoked on a generic type).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77b36-152">Çalışma zamanı yönergeleri, bir çalışma zamanı yönergeleri tanımlanır (. rd.xml) dosyası.</span><span class="sxs-lookup"><span data-stu-id="77b36-152">Runtime directives are defined in a runtime directives (.rd.xml) file.</span></span> <span data-ttu-id="77b36-153">Bu dosyayı kullanma hakkında genel bilgi için bkz: [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md).</span><span class="sxs-lookup"><span data-stu-id="77b36-153">For general information about using this file, see [Getting Started](../../../docs/framework/net-native/getting-started-with-net-native.md).</span></span> <span data-ttu-id="77b36-154">Çalışma zamanı yönergeleri hakkında daha fazla bilgi için bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span><span class="sxs-lookup"><span data-stu-id="77b36-154">For information about the runtime directives, see [Runtime Directives (rd.xml) Configuration File Reference](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="77b36-155"> Ayrıca profil varsayılan kümenin dışında hangi tür yansıma desteklemelidir belirlemek Geliştirici yardım araçları içerir.</span><span class="sxs-lookup"><span data-stu-id="77b36-155"> also includes profiling tools that help the developer determine which types outside the default set should support reflection.</span></span>  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a><span data-ttu-id="77b36-156">Yansıma ile ilgili diğer farklar</span><span class="sxs-lookup"><span data-stu-id="77b36-156">Other reflection-related differences</span></span>  
 <span data-ttu-id="77b36-157">Diğer tek yansıma ilgili arasındaki davranış farklılıkları .NET için Windows mağazası uygulamaları dizi vardır ve [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-157">There are a number of other individual reflection-related differences in behavior between the .NET for Windows Store apps and [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="77b36-158">İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="77b36-158">In [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
-   <span data-ttu-id="77b36-159">Özel yansıma türleri ve üyeleri .NET Framework Sınıf Kitaplığı'nda üzerinde desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="77b36-159">Private reflection over types and members in the .NET Framework class library is not supported.</span></span> <span data-ttu-id="77b36-160">Ancak, kendi özel türleri ve üyeleri, yanı sıra türleri ve üçüncü taraf kitaplıklar üyelerinde üzerinden yansıtacak olabilir.</span><span class="sxs-lookup"><span data-stu-id="77b36-160">You can, however, reflect over your own private types and members, as well as types and members in third-party libraries.</span></span>  
  
-   <span data-ttu-id="77b36-161"><xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Özelliği doğru döndürür `false` için bir <xref:System.Reflection.ParameterInfo> dönüş değerini temsil eden nesne.</span><span class="sxs-lookup"><span data-stu-id="77b36-161">The <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> property correctly returns `false` for a <xref:System.Reflection.ParameterInfo> object that represents a return value.</span></span> <span data-ttu-id="77b36-162">.NET için Windows mağazası uygulamalarında döndürdüğü `true`.</span><span class="sxs-lookup"><span data-stu-id="77b36-162">In the .NET for Windows Store apps, it returns `true`.</span></span> <span data-ttu-id="77b36-163">Ara dile (IL) bu doğrudan desteklemez ve dil yorumlama bırakılır.</span><span class="sxs-lookup"><span data-stu-id="77b36-163">Intermediate language (IL) doesn’t support this directly, and interpretation is left to the language.</span></span>  
  
-   <span data-ttu-id="77b36-164">Ortak üye <xref:System.RuntimeFieldHandle> ve <xref:System.RuntimeMethodHandle> yapıları desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="77b36-164">Public members on the <xref:System.RuntimeFieldHandle> and <xref:System.RuntimeMethodHandle> structures aren't supported.</span></span> <span data-ttu-id="77b36-165">Bu tür yalnızca LINQ ifade ağaçları ve statik dizi başlatma için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="77b36-165">These types are supported only for LINQ, expression trees, and static array initialization.</span></span>  
  
-   <span data-ttu-id="77b36-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> ve <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> temel sınıflarda gizli üyeleri Ekle ve bu nedenle açık geçersiz kılmalar geçersiz kılınabilir.</span><span class="sxs-lookup"><span data-stu-id="77b36-166"><xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> and <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> include hidden members in base classes and thus may be overridden without explicit overrides.</span></span> <span data-ttu-id="77b36-167">Bu ayrıca diğer geçerlidir [RuntimeReflectionExtensions.GetRuntime\*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="77b36-167">This is also true of other [RuntimeReflectionExtensions.GetRuntime\*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) methods.</span></span>  
  
-   <span data-ttu-id="77b36-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> belirli birleşimleri (örneğin, ByRef'ler dizisi) oluşturmayı denediğinizde başarısız yok.</span><span class="sxs-lookup"><span data-stu-id="77b36-168"><xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> and <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> don't fail when you try to create certain combinations (for example, an array of byrefs).</span></span>  
  
-   <span data-ttu-id="77b36-169">İşaretçi parametrelere sahip üyeler çağrılacak yansıma kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="77b36-169">You can't use reflection to invoke members that have pointer parameters.</span></span>  
  
-   <span data-ttu-id="77b36-170">Yansıma almak veya bir işaretçi alanı ayarlamak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="77b36-170">You can't use reflection to get or set a pointer field.</span></span>  
  
-   <span data-ttu-id="77b36-171">Bağımsız değişken sayısı yanlış olduğunda ve bir bağımsız değişken türü geçersiz [!INCLUDE[net_native](../../../includes/net-native-md.md)] oluşturur bir <xref:System.ArgumentException> yerine bir <xref:System.Reflection.TargetParameterCountException>.</span><span class="sxs-lookup"><span data-stu-id="77b36-171">When the argument count is wrong and the type of one of the arguments is incorrect, [!INCLUDE[net_native](../../../includes/net-native-md.md)] throws an <xref:System.ArgumentException> instead of a <xref:System.Reflection.TargetParameterCountException>.</span></span>  
  
-   <span data-ttu-id="77b36-172">İkili seri hale getirme özel durumların genellikle desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="77b36-172">Binary serialization of exceptions is generally not supported.</span></span> <span data-ttu-id="77b36-173">Serileştirilebilir olmayan nesneler sonucu olarak eklenebilir <xref:System.Exception.Data%2A?displayProperty=nameWithType> sözlük.</span><span class="sxs-lookup"><span data-stu-id="77b36-173">As a result, non-serializable objects can be added to the <xref:System.Exception.Data%2A?displayProperty=nameWithType> dictionary.</span></span>  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a><span data-ttu-id="77b36-174">Desteklenmeyen senaryolar ve API'leri</span><span class="sxs-lookup"><span data-stu-id="77b36-174">Unsupported scenarios and APIs</span></span>  
 <span data-ttu-id="77b36-175">Aşağıdaki bölümlerde, genel geliştirme, birlikte çalışabilirlik ve HTTPClient ve Windows Communication Foundation (WCF) gibi teknolojileri için desteklenmeyen senaryolar ve API'leri listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="77b36-175">The following sections list unsupported scenarios and APIs for general development, interop, and technologies such as HTTPClient and Windows Communication Foundation (WCF):</span></span>  
  
-   [<span data-ttu-id="77b36-176">Genel Geliştirme</span><span class="sxs-lookup"><span data-stu-id="77b36-176">General development</span></span>](#General)  
  
-   [<span data-ttu-id="77b36-177">HttpClient</span><span class="sxs-lookup"><span data-stu-id="77b36-177">HttpClient</span></span>](#HttpClient)  
  
-   [<span data-ttu-id="77b36-178">Interop</span><span class="sxs-lookup"><span data-stu-id="77b36-178">Interop</span></span>](#Interop)  
  
-   [<span data-ttu-id="77b36-179">Desteklenmeyen API'leri</span><span class="sxs-lookup"><span data-stu-id="77b36-179">Unsupported APIs</span></span>](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a><span data-ttu-id="77b36-180">Genel Geliştirme farklar</span><span class="sxs-lookup"><span data-stu-id="77b36-180">General development differences</span></span>  
 <span data-ttu-id="77b36-181">**Değer türleri**</span><span class="sxs-lookup"><span data-stu-id="77b36-181">**Value types**</span></span>  
  
-   <span data-ttu-id="77b36-182">Geçersiz kılarsanız <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> ve <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> yöntemleri bir değer türü için temel sınıf uygulamaları çağrısı yok.</span><span class="sxs-lookup"><span data-stu-id="77b36-182">If you override the <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> and <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> methods for a value type, don't call the base class implementations.</span></span> <span data-ttu-id="77b36-183">.NET için Windows mağazası uygulamalarında bu yöntemleri yansıma kullanan.</span><span class="sxs-lookup"><span data-stu-id="77b36-183">In .NET for Windows Store apps, these methods rely on reflection.</span></span> <span data-ttu-id="77b36-184">Derleme zamanında [!INCLUDE[net_native](../../../includes/net-native-md.md)] çalışma zamanı yansıma kullanan olmayan bir uygulama oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77b36-184">At compile time, [!INCLUDE[net_native](../../../includes/net-native-md.md)] generates an implementation that doesn't rely on runtime reflection.</span></span> <span data-ttu-id="77b36-185">Bu iki yöntem geçersiz kılmaz, bunlar beklendiği gibi çünkü çalışmayacak, yani [!INCLUDE[net_native](../../../includes/net-native-md.md)] derleme zamanında uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77b36-185">This means that if you don't override these two methods, they will work as expected, because [!INCLUDE[net_native](../../../includes/net-native-md.md)] generates the implementation at compile time.</span></span> <span data-ttu-id="77b36-186">Ancak, bu yöntemleri geçersiz kılma ancak temel sınıf uygulamasını çağıran bir özel durum oluşur.</span><span class="sxs-lookup"><span data-stu-id="77b36-186">However, overriding these methods but calling the base class implementation results in an exception.</span></span>  
  
-   <span data-ttu-id="77b36-187">Bir megabayttan büyük değer türleri desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="77b36-187">Value types larger than one megabyte aren't supported.</span></span>  
  
-   <span data-ttu-id="77b36-188">Değer türleri varsayılan bir oluşturucu olamaz [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-188">Value types can't have a default constructor in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="77b36-189">(C# ve Visual Basic varsayılan oluşturucular değer türleri üzerinde engelliyor.</span><span class="sxs-lookup"><span data-stu-id="77b36-189">(C# and Visual Basic prohibit default constructors on value types.</span></span> <span data-ttu-id="77b36-190">Ancak, bunlar IL içinde oluşturulabilir.)</span><span class="sxs-lookup"><span data-stu-id="77b36-190">However, these can be created in IL.)</span></span>  
  
 <span data-ttu-id="77b36-191">**Diziler**</span><span class="sxs-lookup"><span data-stu-id="77b36-191">**Arrays**</span></span>  
  
-   <span data-ttu-id="77b36-192">Sıfır dışındaki bir alt sınırı ile diziler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="77b36-192">Arrays with a lower bound other than zero aren't supported.</span></span> <span data-ttu-id="77b36-193">Genellikle, bu diziler çağrılarak oluşturulan <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> aşırı yükleme.</span><span class="sxs-lookup"><span data-stu-id="77b36-193">Typically, these arrays are created by calling the <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> overload.</span></span>  
  
-   <span data-ttu-id="77b36-194">Çok boyutlu diziler dinamik oluşturulması desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="77b36-194">Dynamic creation of multidimensional arrays isn't supported.</span></span> <span data-ttu-id="77b36-195">Bu tür diziler, genellikle bir aşırı yüklemesini çağrılarak oluşturulan <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> içeren yöntem bir `lengths` parametresi veya çağırarak <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="77b36-195">Such arrays are typically created by calling an overload of the <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> method that includes a `lengths` parameter, or by calling the <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="77b36-196">Dört veya daha fazla boyutlarda çok boyutlu diziler desteklenmez; diğer bir deyişle, kendi <xref:System.Array.Rank%2A?displayProperty=nameWithType> özellik değeri olan dört veya daha büyük.</span><span class="sxs-lookup"><span data-stu-id="77b36-196">Multidimensional arrays that have four or more dimensions aren't supported; that is, their <xref:System.Array.Rank%2A?displayProperty=nameWithType> property value is four or greater.</span></span> <span data-ttu-id="77b36-197">Kullanım [basit dizileri](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (oluşan bir dizi) yerine.</span><span class="sxs-lookup"><span data-stu-id="77b36-197">Use [jagged arrays](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (an array of arrays) instead.</span></span> <span data-ttu-id="77b36-198">Örneğin, `array[x,y,z]` geçersiz, ancak `array[x][y][z]` değil.</span><span class="sxs-lookup"><span data-stu-id="77b36-198">For example, `array[x,y,z]` is invalid, but `array[x][y][z]` isn't.</span></span>  
  
-   <span data-ttu-id="77b36-199">Çok boyutlu diziler için varyansı desteklenmiyor ve neden olan bir <xref:System.InvalidCastException> çalışma zamanında özel durum.</span><span class="sxs-lookup"><span data-stu-id="77b36-199">Variance for multidimensional arrays isn't supported and causes an <xref:System.InvalidCastException> exception at run time.</span></span>  
  
 <span data-ttu-id="77b36-200">**Genel Türler**</span><span class="sxs-lookup"><span data-stu-id="77b36-200">**Generics**</span></span>  
  
-   <span data-ttu-id="77b36-201">Sınırsız genel tür genişletme derleyici hataya yol açar.</span><span class="sxs-lookup"><span data-stu-id="77b36-201">Infinite generic type expansion results in a compiler error.</span></span> <span data-ttu-id="77b36-202">Örneğin, bu kodu derlemek başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="77b36-202">For example, this code fails to compile:</span></span>  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 <span data-ttu-id="77b36-203">**İşaretçiler**</span><span class="sxs-lookup"><span data-stu-id="77b36-203">**Pointers**</span></span>  
  
-   <span data-ttu-id="77b36-204">İşaretçileri diziler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="77b36-204">Arrays of pointers aren't supported.</span></span>  
  
-   <span data-ttu-id="77b36-205">Yansıma almak veya bir işaretçi alanı ayarlamak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="77b36-205">You can't use reflection to get or set a pointer field.</span></span>  
  
 <span data-ttu-id="77b36-206">**Serileştirme**</span><span class="sxs-lookup"><span data-stu-id="77b36-206">**Serialization**</span></span>  
  
 <span data-ttu-id="77b36-207"><xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Öznitelik desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="77b36-207">The <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> attribute isn't supported.</span></span> <span data-ttu-id="77b36-208">Kullanım <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> yerine özniteliği.</span><span class="sxs-lookup"><span data-stu-id="77b36-208">Use the <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> attribute instead.</span></span>  
  
 <span data-ttu-id="77b36-209">**Kaynaklar**</span><span class="sxs-lookup"><span data-stu-id="77b36-209">**Resources**</span></span>  
  
 <span data-ttu-id="77b36-210">Yerelleştirilmiş kaynaklar ile kullanımını <xref:System.Diagnostics.Tracing.EventSource> sınıfı desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="77b36-210">The use of localized resources with the <xref:System.Diagnostics.Tracing.EventSource> class isn't supported.</span></span> <span data-ttu-id="77b36-211"><xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Özellik yerelleştirilmiş kaynaklar tanımlamak değil.</span><span class="sxs-lookup"><span data-stu-id="77b36-211">The <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> property doesn't define localized resources.</span></span>  
  
 <span data-ttu-id="77b36-212">**Temsilciler**</span><span class="sxs-lookup"><span data-stu-id="77b36-212">**Delegates**</span></span>  
  
 <span data-ttu-id="77b36-213">`Delegate.BeginInvoke` ve `Delegate.EndInvoke` desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="77b36-213">`Delegate.BeginInvoke` and `Delegate.EndInvoke` aren't supported.</span></span>  
  
 <span data-ttu-id="77b36-214">**Async**</span><span class="sxs-lookup"><span data-stu-id="77b36-214">**Async**</span></span>  
  
 <span data-ttu-id="77b36-215">Görev IAsync aşırı mantığında iş parçacığı oluşturma desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="77b36-215">Threading logic in overloads of Task IAsync isn't supported.</span></span>  
  
 <span data-ttu-id="77b36-216">**Çeşitli API'ler**</span><span class="sxs-lookup"><span data-stu-id="77b36-216">**Miscellaneous APIs**</span></span>  
  
-   <span data-ttu-id="77b36-217"><xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> Özelliği atar bir <xref:System.PlatformNotSupportedException> özel durum, bir <xref:System.Runtime.InteropServices.GuidAttribute> öznitelik türü için uygulanan değil.</span><span class="sxs-lookup"><span data-stu-id="77b36-217">The <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> property throws a <xref:System.PlatformNotSupportedException> exception if a <xref:System.Runtime.InteropServices.GuidAttribute> attribute isn't applied to the type.</span></span> <span data-ttu-id="77b36-218">Kullanılan GUID öncelikle COM desteği.</span><span class="sxs-lookup"><span data-stu-id="77b36-218">The GUID is used primarily for COM support.</span></span>  
  
-   <span data-ttu-id="77b36-219"><xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Yöntemi doğru kısa tarihleri içeren dizeleri ayrıştırma [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-219">The <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> method correctly parses strings that contain short dates in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="77b36-220">Ancak, bu değişikliklerle uyumluluk tarih bilgisini korumaz ve ayrıştırma süresi Microsoft Bilgi Bankası makalelerinde açıklandığı [KB2803771](http://support.microsoft.com/kb/2803771) ve [KB2803755](http://support.microsoft.com/kb/2803755).</span><span class="sxs-lookup"><span data-stu-id="77b36-220">However, it doesn't maintain compatibility with the changes in date and time parsing described in the Microsoft Knowledge Base articles [KB2803771](http://support.microsoft.com/kb/2803771) and [KB2803755](http://support.microsoft.com/kb/2803755).</span></span>  
  
-   <span data-ttu-id="77b36-221"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` içinde doğru yuvarlanır [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-221"><xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` is correctly rounded in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="77b36-222">CLR bazı sürümlerinde yerine Sonuç dizesini kesilir yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="77b36-222">In some versions of the CLR, the result string is truncated instead of rounded.</span></span>  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a><span data-ttu-id="77b36-223">HttpClient farklar</span><span class="sxs-lookup"><span data-stu-id="77b36-223">HttpClient differences</span></span>  
 <span data-ttu-id="77b36-224">İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Net.Http.HttpClientHandler> sınıfı WinINet düzenlenmemeli (aracılığıyla [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) sınıfı) yerine <xref:System.Net.WebRequest> ve <xref:System.Net.WebResponse> standart .NET için Windows mağazası uygulamalarında kullanılan sınıflar.</span><span class="sxs-lookup"><span data-stu-id="77b36-224">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], the <xref:System.Net.Http.HttpClientHandler> class internally uses WinINet (through the [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class) instead of the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes used in the standard .NET for Windows Store apps.</span></span>  <span data-ttu-id="77b36-225">WinINet tüm desteklemiyor yapılandırma seçenekleri <xref:System.Net.Http.HttpClientHandler> sınıf destekler.</span><span class="sxs-lookup"><span data-stu-id="77b36-225">WinINet doesn't support all the configuration options that the <xref:System.Net.Http.HttpClientHandler> class supports.</span></span>  <span data-ttu-id="77b36-226">Sonuç olarak:</span><span class="sxs-lookup"><span data-stu-id="77b36-226">As a result:</span></span>  
  
-   <span data-ttu-id="77b36-227">Yetenek özelliklerinden bazıları <xref:System.Net.Http.HttpClientHandler> dönmek `false` üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], döndürmeleri ancak `true` standart .NET için Windows mağazası uygulamalarında.</span><span class="sxs-lookup"><span data-stu-id="77b36-227">Some of the capability properties on <xref:System.Net.Http.HttpClientHandler> return `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas they return `true` in the standard .NET for Windows Store apps.</span></span>  
  
-   <span data-ttu-id="77b36-228">Bazı yapılandırma özelliği `get` erişimciler her zaman geri sabit bir değer üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)] .NET için Windows mağazası uygulamalarında varsayılan yapılandırılabilir değerinden farklı.</span><span class="sxs-lookup"><span data-stu-id="77b36-228">Some of the configuration property `get` accessors always return a fixed value on [!INCLUDE[net_native](../../../includes/net-native-md.md)] that is different than the default configurable value in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="77b36-229">Bazı ek davranış farklılıkları aşağıdaki alt bölümlerde ele alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="77b36-229">Some additional behavior differences are covered in the following subsections.</span></span>  
  
 <span data-ttu-id="77b36-230">**Proxy**</span><span class="sxs-lookup"><span data-stu-id="77b36-230">**Proxy**</span></span>  
  
 <span data-ttu-id="77b36-231">[HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) sınıfı, yapılandırma veya istek başına temelinde proxy geçersiz kılma desteklemiyor.</span><span class="sxs-lookup"><span data-stu-id="77b36-231">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn’t support configuring or overriding the proxy on a per-request basis.</span></span>  <span data-ttu-id="77b36-232">Tüm istekleri üzerinde yani [!INCLUDE[net_native](../../../includes/net-native-md.md)] yapılandırılmış sistemi proxy sunucusu veya değerine bağlı olarak hiçbir Ara sunucunun kullanmak <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="77b36-232">This means that all requests on [!INCLUDE[net_native](../../../includes/net-native-md.md)] use the system-configured proxy server or no proxy server, depending on the value of the <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="77b36-233">.NET için Windows mağazası uygulamalarında proxy sunucusu tarafından tanımlanan <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="77b36-233">In .NET for Windows Store apps, the proxy server is defined by the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> property.</span></span>  <span data-ttu-id="77b36-234">Üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], ayar <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> dışında bir değere `null` oluşturur bir <xref:System.PlatformNotSupportedException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="77b36-234">On [!INCLUDE[net_native](../../../includes/net-native-md.md)], setting the <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> to a value other than `null` throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="77b36-235"><xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Özelliği döndürür `false` üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], onu verir kullanılabilirken `true` standart Windows mağazası için .NET Framework uygulamalarında.</span><span class="sxs-lookup"><span data-stu-id="77b36-235">The <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> property returns `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas it returns `true` in the standard .NET Framework for Windows Store apps.</span></span>  
  
 <span data-ttu-id="77b36-236">**Otomatik yeniden yönlendirme**</span><span class="sxs-lookup"><span data-stu-id="77b36-236">**Automatic redirection**</span></span>  
  
 <span data-ttu-id="77b36-237">[HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) sınıfı yapılandırılması için otomatik yeniden yönlendirme en fazla izin vermez.</span><span class="sxs-lookup"><span data-stu-id="77b36-237">The [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) class doesn't allow the maximum number of automatic redirections to be configured.</span></span>  <span data-ttu-id="77b36-238">Değeri <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> özelliği varsayılan olarak standart .NET için Windows mağazası uygulamaları 50'dir ve değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="77b36-238">The value of the <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> property is 50 by default in the standard .NET for Windows Store apps and can be modified.</span></span> <span data-ttu-id="77b36-239">Üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], bu özelliğin değeri 10 ve atar değiştirmeye çalışırken bir <xref:System.PlatformNotSupportedException> özel durum.</span><span class="sxs-lookup"><span data-stu-id="77b36-239">On [!INCLUDE[net_native](../../../includes/net-native-md.md)], the value of this property is 10, and trying to modify it throws a <xref:System.PlatformNotSupportedException> exception.</span></span>  <span data-ttu-id="77b36-240"><xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Özelliği döndürür `false` üzerinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], onu verir kullanılabilirken `true` .NET için Windows mağazası uygulamalarında.</span><span class="sxs-lookup"><span data-stu-id="77b36-240">The <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> property returns `false` on [!INCLUDE[net_native](../../../includes/net-native-md.md)], whereas it returns `true` in .NET for Windows Store apps.</span></span>  
  
 <span data-ttu-id="77b36-241">**Otomatik açma**</span><span class="sxs-lookup"><span data-stu-id="77b36-241">**Automatic decompression**</span></span>  
  
 <span data-ttu-id="77b36-242">.NET için Windows mağazası uygulamaları ayarlamanıza olanak tanır <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> özelliğine <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, her iki <xref:System.Net.DecompressionMethods.Deflate> ve <xref:System.Net.DecompressionMethods.GZip>, veya <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="77b36-242">.NET for Windows Store apps allows you to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> property to <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="77b36-243"> yalnızca destekler <xref:System.Net.DecompressionMethods.Deflate> ile birlikte <xref:System.Net.DecompressionMethods.GZip>, veya <xref:System.Net.DecompressionMethods.None>.</span><span class="sxs-lookup"><span data-stu-id="77b36-243"> only supports <xref:System.Net.DecompressionMethods.Deflate> together with <xref:System.Net.DecompressionMethods.GZip>, or <xref:System.Net.DecompressionMethods.None>.</span></span>  <span data-ttu-id="77b36-244">Ayarlanmaya çalışılırken <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> ya da özellik <xref:System.Net.DecompressionMethods.Deflate> veya <xref:System.Net.DecompressionMethods.GZip> tek başına sessizce hem de ayarlar <xref:System.Net.DecompressionMethods.Deflate> ve <xref:System.Net.DecompressionMethods.GZip>.</span><span class="sxs-lookup"><span data-stu-id="77b36-244">Trying to set the <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> property to either <xref:System.Net.DecompressionMethods.Deflate> or <xref:System.Net.DecompressionMethods.GZip> alone silently sets it to both <xref:System.Net.DecompressionMethods.Deflate> and <xref:System.Net.DecompressionMethods.GZip>.</span></span>  
  
 <span data-ttu-id="77b36-245">**Çerezler**</span><span class="sxs-lookup"><span data-stu-id="77b36-245">**Cookies**</span></span>  
  
 <span data-ttu-id="77b36-246">Tanımlama bilgisi işleme ile aynı anda gerçekleştirilen <xref:System.Net.Http.HttpClient> ve WinINet.</span><span class="sxs-lookup"><span data-stu-id="77b36-246">Cookie handling is performed simultaneously by <xref:System.Net.Http.HttpClient> and WinINet.</span></span>  <span data-ttu-id="77b36-247">Tanımlama bilgilerini <xref:System.Net.CookieContainer> WinINet tanımlama bilgisi önbelleğinde tanımlama bilgisi ile birleştirilir.</span><span class="sxs-lookup"><span data-stu-id="77b36-247">Cookies from the <xref:System.Net.CookieContainer> are combined with cookies in the WinINet cookie cache.</span></span>  <span data-ttu-id="77b36-248">Bir tanımlama bilgisinden kaldırma <xref:System.Net.CookieContainer> engeller <xref:System.Net.Http.HttpClient> ancak tanımlama bilgisi zaten WinINet tarafından görülen ve tanımlama bilgileri, kullanıcı tarafından silinmiş doğru tanımlama bilgisi, göndermesinin WinINet gönderir.</span><span class="sxs-lookup"><span data-stu-id="77b36-248">Removing a cookie from <xref:System.Net.CookieContainer> prevents <xref:System.Net.Http.HttpClient> from sending the cookie, but if the cookie was already seen by WinINet, and cookies weren't deleted by the user, WinINet sends it.</span></span>  <span data-ttu-id="77b36-249">Program aracılığıyla kullanarak bir tanımlama bilgisi WinINet kaldırmak kurulamadığı <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, veya <xref:System.Net.CookieContainer> API.</span><span class="sxs-lookup"><span data-stu-id="77b36-249">It isn't possible to programmatically remove a cookie from WinINet by using the <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, or <xref:System.Net.CookieContainer> API.</span></span>  <span data-ttu-id="77b36-250">Ayarı <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> özelliğine `false` yalnızca neden <xref:System.Net.Http.HttpClient> tanımlama bilgilerini; gönderilmesini durdurmak için WinINet istekte hala, tanımlama bilgileri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="77b36-250">Setting the <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> property to `false` causes only <xref:System.Net.Http.HttpClient> to stop sending cookies; WinINet might still include its cookies in the request.</span></span>  
  
 <span data-ttu-id="77b36-251">**kimlik bilgileri**</span><span class="sxs-lookup"><span data-stu-id="77b36-251">**Credentials**</span></span>  
  
 <span data-ttu-id="77b36-252">.NET için Windows mağazası uygulamalarında <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> ve <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> özellikleri bağımsız olarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="77b36-252">In .NET for Windows Store apps, the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> properties work independently.</span></span>  <span data-ttu-id="77b36-253">Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği kabul uygulayan herhangi bir nesne <xref:System.Net.ICredentials> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="77b36-253">Additionally, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property accepts any object that implements the <xref:System.Net.ICredentials> interface.</span></span>  <span data-ttu-id="77b36-254">İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], ayar <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> özelliğine `true` neden <xref:System.Net.Http.HttpClientHandler.Credentials%2A> olmasını özelliği `null`.</span><span class="sxs-lookup"><span data-stu-id="77b36-254">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], setting the <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> property to `true` causes the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property to become `null`.</span></span>  <span data-ttu-id="77b36-255">Ayrıca, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği yalnızca ayarlanabilir `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, veya bir nesne türü <xref:System.Net.NetworkCredential>.</span><span class="sxs-lookup"><span data-stu-id="77b36-255">In addition, the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property can be set only to `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, or an object of type <xref:System.Net.NetworkCredential>.</span></span>  <span data-ttu-id="77b36-256">Diğer atama <xref:System.Net.ICredentials> en popüler olduğu nesne <xref:System.Net.CredentialCache>, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> özelliği atar bir <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="77b36-256">Assigning any other <xref:System.Net.ICredentials> object, the most popular of which is <xref:System.Net.CredentialCache>, to the <xref:System.Net.Http.HttpClientHandler.Credentials%2A> property throws a <xref:System.PlatformNotSupportedException>.</span></span>  
  
 <span data-ttu-id="77b36-257">**Diğer desteklenmeyen veya unconfigurable özellikleri**</span><span class="sxs-lookup"><span data-stu-id="77b36-257">**Other unsupported or unconfigurable features**</span></span>  
  
 <span data-ttu-id="77b36-258">İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="77b36-258">In [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
-   <span data-ttu-id="77b36-259">Değeri <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> özelliktir her zaman <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span><span class="sxs-lookup"><span data-stu-id="77b36-259">The value of the <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> property is always <xref:System.Net.Http.ClientCertificateOption.Automatic>.</span></span>  <span data-ttu-id="77b36-260">.NET için Windows mağazası uygulamalarında varsayılandır <xref:System.Net.Http.ClientCertificateOption.Manual>.</span><span class="sxs-lookup"><span data-stu-id="77b36-260">In .NET for Windows Store apps, the default is <xref:System.Net.Http.ClientCertificateOption.Manual>.</span></span>  
  
-   <span data-ttu-id="77b36-261"><xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Özelliği yapılandırılabilir değildir.</span><span class="sxs-lookup"><span data-stu-id="77b36-261">The <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> property isn't configurable.</span></span>  
  
-   <span data-ttu-id="77b36-262"><xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Özelliktir her zaman `true`.</span><span class="sxs-lookup"><span data-stu-id="77b36-262">The <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> property is always `true`.</span></span>  <span data-ttu-id="77b36-263">.NET için Windows mağazası uygulamalarında varsayılandır `false`.</span><span class="sxs-lookup"><span data-stu-id="77b36-263">In .NET for Windows Store apps, the default is `false`.</span></span>  
  
-   <span data-ttu-id="77b36-264">`SetCookie2` Yanıtları üstbilgisinde geçersiz yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="77b36-264">The `SetCookie2` header in responses is ignored as obsolete.</span></span>  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a><span data-ttu-id="77b36-265">Birlikte çalışma farklar</span><span class="sxs-lookup"><span data-stu-id="77b36-265">Interop differences</span></span>  
 <span data-ttu-id="77b36-266">**Kullanım dışı API'leri**</span><span class="sxs-lookup"><span data-stu-id="77b36-266">**Deprecated APIs**</span></span>  
  
 <span data-ttu-id="77b36-267">Yönetilen kod ile birlikte çalışabilirlik için sık kullanılan API'leri sayısı kullanım dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="77b36-267">A number of infrequently used APIs for interoperability with managed code have been deprecated.</span></span> <span data-ttu-id="77b36-268">İle kullanıldığında [!INCLUDE[net_native](../../../includes/net-native-md.md)], bu API'leri atabilir bir <xref:System.NotImplementedException> veya <xref:System.PlatformNotSupportedException> özel durum ya da bir derleyici hatası sonuçlanır.</span><span class="sxs-lookup"><span data-stu-id="77b36-268">When used with [!INCLUDE[net_native](../../../includes/net-native-md.md)], these APIs may throw a <xref:System.NotImplementedException> or <xref:System.PlatformNotSupportedException> exception, or result in a compiler error.</span></span> <span data-ttu-id="77b36-269">Derleyici Hatası yerine bir derleyici uyarısı oluşturur, bunları çağırma rağmen .NET için Windows mağazası uygulamalarında bu API'leri kullanılmayan olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="77b36-269">In .NET for Windows Store apps, these APIs are marked as obsolete, although calling them generates a compiler warning rather than a compiler error.</span></span>  
  
 <span data-ttu-id="77b36-270">Kullanım dışı API'ler `VARIANT` hazırlama:</span><span class="sxs-lookup"><span data-stu-id="77b36-270">Deprecated APIs for `VARIANT` marshaling:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>|  
  
 <span data-ttu-id="77b36-271"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> desteklenir, ancak ile kullanıldığında gibi bazı senaryolarda bir özel durum oluşturur [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) veya byref değişkenleri.</span><span class="sxs-lookup"><span data-stu-id="77b36-271"><xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> is supported, but it throws an exception in some scenarios, such as when it is used with [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) or byref variants.</span></span>  
  
 <span data-ttu-id="77b36-272">Kullanım dışı API'ler [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) destekler:</span><span class="sxs-lookup"><span data-stu-id="77b36-272">Deprecated APIs for [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) support:</span></span>  
  
|<span data-ttu-id="77b36-273">Tür</span><span class="sxs-lookup"><span data-stu-id="77b36-273">Type</span></span>|<span data-ttu-id="77b36-274">Üye</span><span class="sxs-lookup"><span data-stu-id="77b36-274">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>|<span data-ttu-id="77b36-275">Öznitelik desteklenmiyor</span><span class="sxs-lookup"><span data-stu-id="77b36-275">Attribute isn't supported</span></span>|  
  
 <span data-ttu-id="77b36-276">Kullanım dışı API'ler klasik COM olayları için:</span><span class="sxs-lookup"><span data-stu-id="77b36-276">Deprecated APIs for classic COM events:</span></span>  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 <span data-ttu-id="77b36-277">Kullanım dışı API'leri <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> içinde desteklenmeyen arabirimi [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="77b36-277">Deprecated APIs in the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface, which isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
|<span data-ttu-id="77b36-278">Tür</span><span class="sxs-lookup"><span data-stu-id="77b36-278">Type</span></span>|<span data-ttu-id="77b36-279">Üye</span><span class="sxs-lookup"><span data-stu-id="77b36-279">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>|<span data-ttu-id="77b36-280">Tüm üyeler.</span><span class="sxs-lookup"><span data-stu-id="77b36-280">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>|<span data-ttu-id="77b36-281">Tüm üyeler.</span><span class="sxs-lookup"><span data-stu-id="77b36-281">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>|<span data-ttu-id="77b36-282">Tüm üyeler.</span><span class="sxs-lookup"><span data-stu-id="77b36-282">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=nameWithType>|  
  
 <span data-ttu-id="77b36-283">Başka desteklenmeyen birlikte çalışma özellikleri:</span><span class="sxs-lookup"><span data-stu-id="77b36-283">Other unsupported interop features:</span></span>  
  
|<span data-ttu-id="77b36-284">Tür</span><span class="sxs-lookup"><span data-stu-id="77b36-284">Type</span></span>|<span data-ttu-id="77b36-285">Üye</span><span class="sxs-lookup"><span data-stu-id="77b36-285">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>|<span data-ttu-id="77b36-286">Tüm üyeler.</span><span class="sxs-lookup"><span data-stu-id="77b36-286">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>|<span data-ttu-id="77b36-287">Tüm üyeler.</span><span class="sxs-lookup"><span data-stu-id="77b36-287">All members.</span></span>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 <span data-ttu-id="77b36-288">Sıralama API'leri nadiren kullanılır:</span><span class="sxs-lookup"><span data-stu-id="77b36-288">Rarely used marshalling APIs:</span></span>  
  
|<span data-ttu-id="77b36-289">Tür</span><span class="sxs-lookup"><span data-stu-id="77b36-289">Type</span></span>|<span data-ttu-id="77b36-290">Üye</span><span class="sxs-lookup"><span data-stu-id="77b36-290">Member</span></span>|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 <span data-ttu-id="77b36-291">**Platform çağırma ve COM birlikte çalışma uyumluluğu**</span><span class="sxs-lookup"><span data-stu-id="77b36-291">**Platform invoke and COM interop compatibility**</span></span>  
  
 <span data-ttu-id="77b36-292">Çoğu platform çağırma ve COM birlikte çalışma senaryoları içinde hala desteklenmektedir [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-292">Most platform invoke and COM interop scenarios are still supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="77b36-293">Özellikle, Windows çalışma zamanı (WinRT) API ile tüm birlikte çalışabilirlik ve tüm hazırlama Windows çalışma zamanı için gerekli desteklenir.</span><span class="sxs-lookup"><span data-stu-id="77b36-293">In particular, all interoperability with Windows Runtime (WinRT) APIs and all marshaling required for the Windows Runtime is supported.</span></span> <span data-ttu-id="77b36-294">Bu, sıralama için destek içerir:</span><span class="sxs-lookup"><span data-stu-id="77b36-294">This includes marshaling support for:</span></span>  
  
-   <span data-ttu-id="77b36-295">Diziler (de dahil olmak üzere <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span><span class="sxs-lookup"><span data-stu-id="77b36-295">Arrays (including <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)</span></span>  
  
-   `BStr`  
  
-   <span data-ttu-id="77b36-296">Temsilciler</span><span class="sxs-lookup"><span data-stu-id="77b36-296">Delegates</span></span>  
  
-   <span data-ttu-id="77b36-297">Dizeler (Unicode, ANSI ve HSTRING)</span><span class="sxs-lookup"><span data-stu-id="77b36-297">Strings (Unicode, Ansi, and HSTRING)</span></span>  
  
-   <span data-ttu-id="77b36-298">Yapılar (`byref` ve `byval`)</span><span class="sxs-lookup"><span data-stu-id="77b36-298">Structs (`byref` and `byval`)</span></span>  
  
-   <span data-ttu-id="77b36-299">Birleşimler</span><span class="sxs-lookup"><span data-stu-id="77b36-299">Unions</span></span>  
  
-   <span data-ttu-id="77b36-300">Win32 tanıtıcıları</span><span class="sxs-lookup"><span data-stu-id="77b36-300">Win32 handles</span></span>  
  
-   <span data-ttu-id="77b36-301">Tüm WinRT yapıları</span><span class="sxs-lookup"><span data-stu-id="77b36-301">All WinRT constructs</span></span>  
  
-   <span data-ttu-id="77b36-302">VARIANT türlerini hazırlama kısmi desteği.</span><span class="sxs-lookup"><span data-stu-id="77b36-302">Partial support for marshaling variant types.</span></span> <span data-ttu-id="77b36-303">Aşağıdakiler desteklenir:</span><span class="sxs-lookup"><span data-stu-id="77b36-303">The following are supported:</span></span>  
  
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
  
    -   [<span data-ttu-id="77b36-304">IUnknown</span><span class="sxs-lookup"><span data-stu-id="77b36-304">IUnknown</span></span>](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 <span data-ttu-id="77b36-305">Ancak, [!INCLUDE[net_native](../../../includes/net-native-md.md)] aşağıdakileri desteklemez:</span><span class="sxs-lookup"><span data-stu-id="77b36-305">However, [!INCLUDE[net_native](../../../includes/net-native-md.md)] doesn't support the following:</span></span>  
  
-   <span data-ttu-id="77b36-306">Klasik COM olaylarını kullanma</span><span class="sxs-lookup"><span data-stu-id="77b36-306">Using classic COM events</span></span>  
  
-   <span data-ttu-id="77b36-307">Uygulama <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> yönetilen tür arabirimi</span><span class="sxs-lookup"><span data-stu-id="77b36-307">Implementing the <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interface on a managed type</span></span>  
  
-   <span data-ttu-id="77b36-308">Uygulama [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) yoluyla bir yönetilen türü arabirimde <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="77b36-308">Implementing the [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) interface on a managed type through the <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> attribute.</span></span> <span data-ttu-id="77b36-309">Ancak, COM nesneleri aracılığıyla çağrılamıyor unutmayın `IDispatch`, ve yönetilen nesnenizin uygulayamaz `IDispatch`.</span><span class="sxs-lookup"><span data-stu-id="77b36-309">However, note that you can't call COM objects through `IDispatch`, and your managed object can't implement `IDispatch`.</span></span>  
  
 <span data-ttu-id="77b36-310">Bir platform çağrılacak yansıma kullanarak yöntem çağırma desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="77b36-310">Using reflection to invoke a platform invoke method isn't supported.</span></span> <span data-ttu-id="77b36-311">Yöntem çağrısının içinde başka bir yöntem kaydırma ve bunun yerine sarmalayıcı çağrılacak yansıma kullanarak bu sınırlamaya geçici çalışabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77b36-311">You can work around this limitation by wrapping the method call in another method and using reflection to call the wrapper instead.</span></span>  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a><span data-ttu-id="77b36-312">Diğer .NET API'leri için Windows mağazası uygulamaları arasındaki farklar</span><span class="sxs-lookup"><span data-stu-id="77b36-312">Other differences from .NET APIs for Windows Store apps</span></span>  
 <span data-ttu-id="77b36-313">Bu bölüm içinde desteklenmeyen kalan API'ları listeler [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-313">This section lists the remaining APIs that aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="77b36-314">En büyük desteklenmeyen API kümesidir Windows Communication Foundation (WCF) API'leri.</span><span class="sxs-lookup"><span data-stu-id="77b36-314">The largest set of the unsupported APIs are Windows Communication Foundation (WCF) APIs.</span></span>  
  
 <span data-ttu-id="77b36-315">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span><span class="sxs-lookup"><span data-stu-id="77b36-315">**DataAnnotations (System.ComponentModel.DataAnnotations)**</span></span>  
  
 <span data-ttu-id="77b36-316">Türler <xref:System.ComponentModel.DataAnnotations> ve <xref:System.ComponentModel.DataAnnotations.Schema> ad alanları desteklenmeyen [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-316">The types in the <xref:System.ComponentModel.DataAnnotations> and <xref:System.ComponentModel.DataAnnotations.Schema> namespaces aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="77b36-317">Bu, Windows 8 için .NET için Windows mağazası uygulamaları yok aşağıdaki türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="77b36-317">These include the following types that are present in the .NET for Windows Store apps for Windows 8:</span></span>  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>|  
  
 <span data-ttu-id="77b36-318">**Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="77b36-318">**Visual Basic**</span></span>  
  
 <span data-ttu-id="77b36-319">Visual Basic şu anda desteklenmiyor [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-319">Visual Basic isn't currently supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="77b36-320">Aşağıdaki türleri <xref:Microsoft.VisualBasic> ve <xref:Microsoft.VisualBasic.CompilerServices> kullanılabilir olmayan ad alanlarını [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="77b36-320">The following types in the <xref:Microsoft.VisualBasic> and <xref:Microsoft.VisualBasic.CompilerServices> namespaces aren't available in [!INCLUDE[net_native](../../../includes/net-native-md.md)]:</span></span>  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>|  
  
 <span data-ttu-id="77b36-321">**Yansıma bağlam (System.Reflection.Context ad alanı)**</span><span class="sxs-lookup"><span data-stu-id="77b36-321">**Reflection Context (System.Reflection.Context namespace)**</span></span>  
  
 <span data-ttu-id="77b36-322"><xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Sınıfı desteklenmiyor [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-322">The <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> class isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="77b36-323">**RTC (System.Net.Http.Rtc)**</span><span class="sxs-lookup"><span data-stu-id="77b36-323">**RTC (System.Net.Http.Rtc)**</span></span>  
  
 <span data-ttu-id="77b36-324"><xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> Sınıfı desteklenmiyor [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-324">The <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> class isn't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span>  
  
 <span data-ttu-id="77b36-325">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span><span class="sxs-lookup"><span data-stu-id="77b36-325">**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**</span></span>  
  
 <span data-ttu-id="77b36-326">Türler [System.ServiceModel.\* ad alanları](http://msdn.microsoft.com/library/gg145010.aspx) içinde desteklenmeyen [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span><span class="sxs-lookup"><span data-stu-id="77b36-326">The types in the [System.ServiceModel.\* namespaces](http://msdn.microsoft.com/library/gg145010.aspx) aren't supported in [!INCLUDE[net_native](../../../includes/net-native-md.md)].</span></span> <span data-ttu-id="77b36-327">Bunlar aşağıdaki türleri içerir:</span><span class="sxs-lookup"><span data-stu-id="77b36-327">These includes the following types:</span></span>  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>|  
  
### <a name="differences-in-serializers"></a><span data-ttu-id="77b36-328">Serileştiricileri farklılıkları</span><span class="sxs-lookup"><span data-stu-id="77b36-328">Differences in serializers</span></span>  
 <span data-ttu-id="77b36-329">Aşağıdaki farkları ilgilendiren seri hale getirme ve seri durumundan çıkarma ile <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer> sınıfları:</span><span class="sxs-lookup"><span data-stu-id="77b36-329">The following differences concern serialization and deserialization with the <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer> classes:</span></span>  
  
-   <span data-ttu-id="77b36-330">İçinde [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> serileştirmek veya seri durumdan, türü kök seri hale getirme türü olmayan bir taban sınıfı üyenin türetilmiş bir sınıf başarısız.</span><span class="sxs-lookup"><span data-stu-id="77b36-330">In [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize or deserialize a derived class that has a base class member whose type isn't a root serialization type.</span></span> <span data-ttu-id="77b36-331">Örneğin, aşağıdaki kodda serileştirmek veya seri durumdan çalışılırken `Y` hatayla sonuçlanır:</span><span class="sxs-lookup"><span data-stu-id="77b36-331">For example, in the following code, trying to serialize or deserialize `Y` results in an error:</span></span>  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     <span data-ttu-id="77b36-332">Tür `InnerType` taban sınıfı üyeleri seri hale getirme sırasında geçiş değil çünkü seri hale getirici için bilinen değil.</span><span class="sxs-lookup"><span data-stu-id="77b36-332">Type `InnerType` isn't known to the serializer, because the members of the base class aren't traversed during serialization.</span></span>  
  
-   <span data-ttu-id="77b36-333"><xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> bir sınıf veya uygulayan yapısı serileştirmek başarısız <xref:System.Collections.Generic.IEnumerable%601> arabirimi.</span><span class="sxs-lookup"><span data-stu-id="77b36-333"><xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> fail to serialize a class or structure that implements the <xref:System.Collections.Generic.IEnumerable%601> interface.</span></span> <span data-ttu-id="77b36-334">Örneğin, aşağıdaki türleri serileştirmek veya serisini kaldırmak başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="77b36-334">For example, the following types fail to serialize or deserialize:</span></span>  
  
  
  
-   <span data-ttu-id="77b36-335"><xref:System.Xml.Serialization.XmlSerializer> serileştirilecek nesnenin tam türü bilmiyor çünkü aşağıdaki nesne değeri serileştirmek başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="77b36-335"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize the following object value, because it doesn't know the exact type of the object to be serialized:</span></span>  
  
  
  
-   <span data-ttu-id="77b36-336"><xref:System.Xml.Serialization.XmlSerializer> serileştirmek veya seri durumdan serileştirilmiş nesne türü buysa başarısız <xref:System.Xml.XmlQualifiedName>.</span><span class="sxs-lookup"><span data-stu-id="77b36-336"><xref:System.Xml.Serialization.XmlSerializer> fails to serialize or deserialize if the type of the serialized object is <xref:System.Xml.XmlQualifiedName>.</span></span>  
  
-   <span data-ttu-id="77b36-337">Tüm serileştiricileri (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, ve <xref:System.Xml.Serialization.XmlSerializer>) türü seri hale getirme kodunu oluşturmak başarısız <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> veya içeren bir türü için <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="77b36-337">All serializers (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, and <xref:System.Xml.Serialization.XmlSerializer>) fail to generate serialization code for type <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> or for a type that contains <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="77b36-338">Bunun yerine, derleme zamanı hataları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="77b36-338">They display build-time errors instead.</span></span>  
  
-   <span data-ttu-id="77b36-339">Seri hale getirme türlerinde şu oluşturuculardan beklendiği şekilde çalışması için garanti değil:</span><span class="sxs-lookup"><span data-stu-id="77b36-339">The following constructors of the serialization types aren't guaranteed to work as expected:</span></span>  
  
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
  
-   <span data-ttu-id="77b36-340"><xref:System.Xml.Serialization.XmlSerializer> herhangi bir aşağıdaki özniteliklere öznitelikli yöntemleri olan bir türü için kod oluşturmanın başarısız olur:</span><span class="sxs-lookup"><span data-stu-id="77b36-340"><xref:System.Xml.Serialization.XmlSerializer> fails to generate code for a type that has methods attributed with any of the following attributes:</span></span>  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <span data-ttu-id="77b36-341"><xref:System.Xml.Serialization.XmlSerializer> kabul etmez <xref:System.Xml.Serialization.IXmlSerializable> özel seri duruma getirme arabirimi.</span><span class="sxs-lookup"><span data-stu-id="77b36-341"><xref:System.Xml.Serialization.XmlSerializer> doesn't honor the <xref:System.Xml.Serialization.IXmlSerializable> custom serialization interface.</span></span> <span data-ttu-id="77b36-342">Bu arabirimi uygulayan bir sınıf varsa <xref:System.Xml.Serialization.XmlSerializer> türü düz bir eski CLR nesnesi (POCO) türü olarak değerlendirir ve yalnızca genel özellikleri serileştirir.</span><span class="sxs-lookup"><span data-stu-id="77b36-342">If you have a class that implements this interface, <xref:System.Xml.Serialization.XmlSerializer> considers the type a plain old CLR object (POCO) type and serializes only its public properties.</span></span>  
  
-   <span data-ttu-id="77b36-343">Bir düz seri hale getirme <xref:System.Exception> aşağıdaki gibi nesne ile iyi işe yaramazsa <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span><span class="sxs-lookup"><span data-stu-id="77b36-343">Serializing a plain <xref:System.Exception> object, such as the following, doesn't work well with <xref:System.Runtime.Serialization.DataContractSerializer> and <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a><span data-ttu-id="77b36-344">Visual Studio farklar</span><span class="sxs-lookup"><span data-stu-id="77b36-344">Visual Studio differences</span></span>  
 <span data-ttu-id="77b36-345">**Özel durumlar ve hata ayıklama**</span><span class="sxs-lookup"><span data-stu-id="77b36-345">**Exceptions and debugging**</span></span>  
  
 <span data-ttu-id="77b36-346">Ne zaman çalıştırdığınız kullanarak derlenmiş uygulamaları [!INCLUDE[net_native](../../../includes/net-native-md.md)] Hata Ayıklayıcısı'ndaki ilk fırsat özel durumlar için aşağıdaki özel durum türleri etkinleştirilir:</span><span class="sxs-lookup"><span data-stu-id="77b36-346">When you're running apps compiled by using [!INCLUDE[net_native](../../../includes/net-native-md.md)] in the debugger, first-chance exceptions are enabled for the following exception types:</span></span>  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 <span data-ttu-id="77b36-347">**Yapı uygulamalar**</span><span class="sxs-lookup"><span data-stu-id="77b36-347">**Building apps**</span></span>  
  
 <span data-ttu-id="77b36-348">Varsayılan olarak Visual Studio tarafından kullanılan x86 derleme araçlarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="77b36-348">Use the x86 build tools that are used by default by Visual Studio.</span></span> <span data-ttu-id="77b36-349">C:\Program Files (x86)\MSBuild\12.0\bin\amd64; bulunan AMD64 MSBuild araçları kullanarak öneririz yok Bu yapı sorunlara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="77b36-349">We don't recommend using the AMD64 MSBuild tools, which are found in C:\Program Files (x86)\MSBuild\12.0\bin\amd64; these may create build problems.</span></span>  
  
 <span data-ttu-id="77b36-350">**Profil oluşturucular**</span><span class="sxs-lookup"><span data-stu-id="77b36-350">**Profilers**</span></span>  
  
-   <span data-ttu-id="77b36-351">Visual Studio CPU profil oluşturucu ve XAML bellek profil oluşturucu sadece kendi-kodumu doğru görüntülemiyor.</span><span class="sxs-lookup"><span data-stu-id="77b36-351">The Visual Studio CPU Profiler and XAML Memory Profiler don't display Just-My-Code correctly.</span></span>  
  
-   <span data-ttu-id="77b36-352">XAML bellek profil oluşturucu doğru şekilde yönetilen yığın veri görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="77b36-352">The XAML Memory Profiler doesn't accurately display managed heap data.</span></span>  
  
-   <span data-ttu-id="77b36-353">CPU profil oluşturucu doğru modülleri belirlemek değil ve işlev adları görüntüler öneki.</span><span class="sxs-lookup"><span data-stu-id="77b36-353">The CPU Profiler doesn't correctly identify modules, and displays prefixed function names.</span></span>  
  
 <span data-ttu-id="77b36-354">**Birim testi kitaplık projeleri**</span><span class="sxs-lookup"><span data-stu-id="77b36-354">**Unit Test Library projects**</span></span>  
  
 <span data-ttu-id="77b36-355">Etkinleştirme [!INCLUDE[net_native](../../../includes/net-native-md.md)] Birim Test kitaplığının bir Windows mağazası uygulamaları projesi desteklenmiyor ve projeyi oluşturmak başarısız olmasına neden olur.</span><span class="sxs-lookup"><span data-stu-id="77b36-355">Enabling [!INCLUDE[net_native](../../../includes/net-native-md.md)] on a Unit Test Library for a Windows Store apps project isn't supported and causes the project to fail to build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77b36-356">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77b36-356">See Also</span></span>  
 [<span data-ttu-id="77b36-357">Başlarken</span><span class="sxs-lookup"><span data-stu-id="77b36-357">Getting Started</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [<span data-ttu-id="77b36-358">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="77b36-358">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [<span data-ttu-id="77b36-359">.NET için Windows mağazası uygulamalarına genel bakış</span><span class="sxs-lookup"><span data-stu-id="77b36-359">.NET For Windows Store apps overview</span></span>](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [<span data-ttu-id="77b36-360">Windows Mağazası Uygulamaları ve Windows Çalışma Zamanı için .NET Framework Desteği</span><span class="sxs-lookup"><span data-stu-id="77b36-360">.NET Framework Support for Windows Store Apps and Windows Runtime</span></span>](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
