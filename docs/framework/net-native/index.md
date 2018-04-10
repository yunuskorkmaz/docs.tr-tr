---
title: .NET Yerel ile Uygulama Derleme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
caps.latest.revision: 27
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dec4d465b53f939f8fa711950ba6a000bd304e13
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/05/2018
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="70c72-102">.NET Yerel ile Uygulama Derleme</span><span class="sxs-lookup"><span data-stu-id="70c72-102">Compiling Apps with .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="70c72-103">Visual Studio 2015 ve sonraki sürümleri ile birlikte oluşturmak ve Windows uygulamalarını dağıtmak için bir ön derleme teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="70c72-103"> is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="70c72-104">Ayrıca yönetilen kod (C# veya Visual Basic) ve bu hedef .NET Framework ve Windows 10 yerel koda yazılan uygulamaları sürümünü otomatik olarak derler.</span><span class="sxs-lookup"><span data-stu-id="70c72-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>  
  
 <span data-ttu-id="70c72-105">Genellikle, .NET Framework hedefleyen uygulamalar Ara dile (IL) derlenir.</span><span class="sxs-lookup"><span data-stu-id="70c72-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="70c72-106">Çalışma zamanında tam zamanında (JIT) Derleyici IL yerel koda çevirir.</span><span class="sxs-lookup"><span data-stu-id="70c72-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="70c72-107">Buna karşılık, [!INCLUDE[net_native](../../../includes/net-native-md.md)] Windows uygulamaları doğrudan yerel kod derler.</span><span class="sxs-lookup"><span data-stu-id="70c72-107">In contrast, [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiles Windows apps directly to native code.</span></span> <span data-ttu-id="70c72-108">Geliştiriciler için bu anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="70c72-108">For developers, this means:</span></span>  
  
-   <span data-ttu-id="70c72-109">Yerel kod performansını uygulamalarınızı özelliği.</span><span class="sxs-lookup"><span data-stu-id="70c72-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="70c72-110">Genellikle, performans ilk IL için derlenmiş ve ardından JIT Derleyici tarafından yerel koda derlenmiş kod üstün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="70c72-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span> 
  
-   <span data-ttu-id="70c72-111">C# veya Visual Basic programı devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70c72-111">You can continue to program in C# or Visual Basic.</span></span>  
  
-   <span data-ttu-id="70c72-112">Sınıf kitaplığı, otomatik bellek yönetimi ve çöp toplama ve özel durum işleme dahil olan .NET Framework tarafından sağlanan kaynaklar yararlanmak devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="70c72-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>  
  
 <span data-ttu-id="70c72-113">Uygulamalarınızın, kullanıcılar için [!INCLUDE[net_native](../../../includes/net-native-md.md)] aşağıdaki avantajları sunar:</span><span class="sxs-lookup"><span data-stu-id="70c72-113">For users of your apps, [!INCLUDE[net_native](../../../includes/net-native-md.md)] offers these advantages:</span></span>  
  
-   <span data-ttu-id="70c72-114">Uygulamaları ve senaryoları çoğunluğu için daha hızlı yürütme süresi.</span><span class="sxs-lookup"><span data-stu-id="70c72-114">Faster execution times for the majority of apps and scenarios.</span></span>
  
-   <span data-ttu-id="70c72-115">Uygulamaları ve senaryoları çoğunluğu daha hızlı başlatma sürelerinin.</span><span class="sxs-lookup"><span data-stu-id="70c72-115">Faster startup times for the majority of apps and scenarios.</span></span> 
  
-   <span data-ttu-id="70c72-116">Düşük dağıtım ve güncelleştirme maliyetleri.</span><span class="sxs-lookup"><span data-stu-id="70c72-116">Low deployment and update costs.</span></span>  
  
-   <span data-ttu-id="70c72-117">En iyi duruma getirilmiş uygulama bellek kullanımı.</span><span class="sxs-lookup"><span data-stu-id="70c72-117">Optimized app memory usage.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="70c72-118">Uygulamaları ve senaryoları büyük çoğunluğu için .NET yerel önemli ölçüde daha hızlı başlangıç süreleri ve IL veya NGEN görüntü için derlenmiş bir uygulama karşılaştırıldığında üstün performans sunar.</span><span class="sxs-lookup"><span data-stu-id="70c72-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="70c72-119">Ancak, sonuçlarınızı farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="70c72-119">However, your results may vary.</span></span> <span data-ttu-id="70c72-120">Uygulamanız .NET yerel olarak performans iyileştirmeleriyle benefited olmak için uygulamanızı .NET yerel sürümü ile kendi performansını karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="70c72-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="70c72-121">Daha fazla bilgi için bkz: [performans oturumuna genel bakış](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="70c72-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>
 
<span data-ttu-id="70c72-122">Ancak [!INCLUDE[net_native](../../../includes/net-native-md.md)] birden çok derleme yerel koda içerir.</span><span class="sxs-lookup"><span data-stu-id="70c72-122">But [!INCLUDE[net_native](../../../includes/net-native-md.md)] involves more than a compilation to native code.</span></span> <span data-ttu-id="70c72-123">.NET Framework uygulamalarını yerleşik ve yürütülen şekilde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="70c72-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="70c72-124">Özellikle:</span><span class="sxs-lookup"><span data-stu-id="70c72-124">In particular:</span></span>  
  
-   <span data-ttu-id="70c72-125">Ön derlemesi esnasında, .NET Framework'ün gerekli bölümleri uygulamanıza statik olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="70c72-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="70c72-126">Bu, .NET Framework ve derleyici global analizi yapmak için performans WINS teslim etmek için uygulama yerel kitaplıklarıyla çalıştırmak için uygulamayı sağlar.</span><span class="sxs-lookup"><span data-stu-id="70c72-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="70c72-127">Sonuç olarak, .NET Framework bile güncelleştirildikten sonra uygulamaları tutarlı bir şekilde daha hızlı başlatın.</span><span class="sxs-lookup"><span data-stu-id="70c72-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>  
  
-   <span data-ttu-id="70c72-128">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Çalışma zamanı statik ön derlemesi için en iyi duruma getirilmiş ve çoğunluğu durumlarda üstün performans sunar.</span><span class="sxs-lookup"><span data-stu-id="70c72-128">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="70c72-129">Aynı anda geliştiricilere kadar üretken Bul çekirdek yansıma özellikleri korur.</span><span class="sxs-lookup"><span data-stu-id="70c72-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>  
  
-   [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="70c72-130">kullandığı aynı geri statik ön derleme senaryoları için en iyi duruma getirilmiş C++ derleyicisi olarak sonlandırın.</span><span class="sxs-lookup"><span data-stu-id="70c72-130"> uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)]<span data-ttu-id="70c72-131">başlık altında C++ aynı veya benzer araçları kullandığından C++ performans yararlarını yönetilen kod geliştiricilerin bu tabloda gösterildiği gibi Getir yapabiliyor.</span><span class="sxs-lookup"><span data-stu-id="70c72-131"> is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|<span data-ttu-id="70c72-132">C++</span><span class="sxs-lookup"><span data-stu-id="70c72-132">C++</span></span>|  
|-|----------------------------------------------------------------|-----------|  
|<span data-ttu-id="70c72-133">Kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="70c72-133">Libraries</span></span>|<span data-ttu-id="70c72-134">.NET Framework + Windows çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="70c72-134">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="70c72-135">Win32 + Windows çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="70c72-135">Win32 + Windows Runtime</span></span>|  
|<span data-ttu-id="70c72-136">Derleyici</span><span class="sxs-lookup"><span data-stu-id="70c72-136">Compiler</span></span>|<span data-ttu-id="70c72-137">UTC en iyi duruma getirme derleyici</span><span class="sxs-lookup"><span data-stu-id="70c72-137">UTC optimizing compiler</span></span>|<span data-ttu-id="70c72-138">UTC en iyi duruma getirme derleyici</span><span class="sxs-lookup"><span data-stu-id="70c72-138">UTC optimizing compiler</span></span>|  
|<span data-ttu-id="70c72-139">Dağıtılan</span><span class="sxs-lookup"><span data-stu-id="70c72-139">Deployed</span></span>|<span data-ttu-id="70c72-140">Hazır Çalıştır ikili dosyalar</span><span class="sxs-lookup"><span data-stu-id="70c72-140">Ready-to-run binaries</span></span>|<span data-ttu-id="70c72-141">Hazır Çalıştır ikili dosyaları (ASM)</span><span class="sxs-lookup"><span data-stu-id="70c72-141">Ready-to-run binaries (ASM)</span></span>|  
|<span data-ttu-id="70c72-142">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="70c72-142">Runtime</span></span>|<span data-ttu-id="70c72-143">MRT.dll (en az CLR çalışma zamanı)</span><span class="sxs-lookup"><span data-stu-id="70c72-143">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="70c72-144">CRT.dll (C çalışma zamanı)</span><span class="sxs-lookup"><span data-stu-id="70c72-144">CRT.dll (C Runtime)</span></span>|  
  
 <span data-ttu-id="70c72-145">Windows 10 için Windows uygulamaları için Windows Mağazası'na .NET yerel kodu derleme ikili dosyalarda uygulama paketleri (.appx dosyaları) yükleyin.</span><span class="sxs-lookup"><span data-stu-id="70c72-145">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="70c72-146">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="70c72-146">In This Section</span></span>  
 <span data-ttu-id="70c72-147">.NET yerel kodu derleme ile uygulamaları geliştirme hakkında daha fazla bilgi için şu konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="70c72-147">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>  
  
-   [<span data-ttu-id="70c72-148">.NET yerel kodu derleme ile Başlarken: geliştirici deneyimi gözden geçirme</span><span class="sxs-lookup"><span data-stu-id="70c72-148">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
-   <span data-ttu-id="70c72-149">[.NET yerel ve derleme:](../../../docs/framework/net-native/net-native-and-compilation.md) yerel kod projenize .NET nasıl yerel derler.</span><span class="sxs-lookup"><span data-stu-id="70c72-149">[.NET Native and Compilation:](../../../docs/framework/net-native/net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>  
  
-   [<span data-ttu-id="70c72-150">Yansıma ve .NET Native</span><span class="sxs-lookup"><span data-stu-id="70c72-150">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    -   [<span data-ttu-id="70c72-151">Yansıma Kullanan API'ler</span><span class="sxs-lookup"><span data-stu-id="70c72-151">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    -   [<span data-ttu-id="70c72-152">Yansıma API'si Başvurusu</span><span class="sxs-lookup"><span data-stu-id="70c72-152">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    -   [<span data-ttu-id="70c72-153">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="70c72-153">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
-   [<span data-ttu-id="70c72-154">Serileştirme ve Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="70c72-154">Serialization and Metadata</span></span>](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
-   [<span data-ttu-id="70c72-155">Windows Mağazası Uygulamanızı .NET Native'e Taşıma</span><span class="sxs-lookup"><span data-stu-id="70c72-155">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
-   [<span data-ttu-id="70c72-156">.NET Native Genel Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="70c72-156">.NET Native General Troubleshooting</span></span>](../../../docs/framework/net-native/net-native-general-troubleshooting.md)  
  
## <a name="see-also"></a><span data-ttu-id="70c72-157">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="70c72-157">See Also</span></span>  
 [<span data-ttu-id="70c72-158">.NET yerel ile ilgili SSS</span><span class="sxs-lookup"><span data-stu-id="70c72-158">.NET Native FAQ</span></span>](http://msdn.microsoft.com/vstudio/dn642499.aspx)
