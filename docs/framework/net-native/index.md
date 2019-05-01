---
title: .NET Yerel ile Uygulama Derleme
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6900bca2bd94f52ea5603c752681163cde52ce19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61867036"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="bd344-102">.NET Yerel ile Uygulama Derleme</span><span class="sxs-lookup"><span data-stu-id="bd344-102">Compiling Apps with .NET Native</span></span>
[!INCLUDE[net_native](../../../includes/net-native-md.md)] <span data-ttu-id="bd344-103">Visual Studio 2015 ve sonraki sürümlerine dahil olan oluşturmak ve Windows uygulamalarını dağıtmak için bir ön derleme teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="bd344-103">is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="bd344-104">Yönetilen kodda yazılmış uygulamalar yayım sürümünü otomatik olarak derler (C# veya Visual Basic) ve hedef .NET Framework ve Windows 10 için yerel kod.</span><span class="sxs-lookup"><span data-stu-id="bd344-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>  
  
 <span data-ttu-id="bd344-105">Genellikle, .NET Framework'ü hedefleyen uygulamaları Ara dil (IL) derlenir.</span><span class="sxs-lookup"><span data-stu-id="bd344-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="bd344-106">Çalışma zamanında, just-ın-time (JIT) derleyici yerel kod için IL çevirir.</span><span class="sxs-lookup"><span data-stu-id="bd344-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="bd344-107">Buna karşılık, [!INCLUDE[net_native](../../../includes/net-native-md.md)] Windows uygulamaları doğrudan yerel kod için derler.</span><span class="sxs-lookup"><span data-stu-id="bd344-107">In contrast, [!INCLUDE[net_native](../../../includes/net-native-md.md)] compiles Windows apps directly to native code.</span></span> <span data-ttu-id="bd344-108">Geliştiriciler için bu anlamına gelir:</span><span class="sxs-lookup"><span data-stu-id="bd344-108">For developers, this means:</span></span>  
  
- <span data-ttu-id="bd344-109">Uygulamalarınızı yerel kod performansını özellik.</span><span class="sxs-lookup"><span data-stu-id="bd344-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="bd344-110">Genellikle, performans için IL önce derlenmiş ve sonra JIT derleyicisi tarafından yerel kod olarak derlenen kod için üstün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="bd344-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span> 
  
- <span data-ttu-id="bd344-111">İçinde program devam edebilirsiniz C# veya Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bd344-111">You can continue to program in C# or Visual Basic.</span></span>  
  
- <span data-ttu-id="bd344-112">Kendi sınıf kitaplığı, otomatik bellek yönetimi ve atık toplama ve özel durum işleme dahil olan .NET Framework tarafından sağlanan kaynaklar yararlanmak devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="bd344-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>  
  
 <span data-ttu-id="bd344-113">Kullanıcıların, uygulamalarınızın [!INCLUDE[net_native](../../../includes/net-native-md.md)] aşağıdaki avantajları sunar:</span><span class="sxs-lookup"><span data-stu-id="bd344-113">For users of your apps, [!INCLUDE[net_native](../../../includes/net-native-md.md)] offers these advantages:</span></span>  
  
- <span data-ttu-id="bd344-114">Çoğu uygulama ve senaryoları için daha hızlı yürütme süreleri.</span><span class="sxs-lookup"><span data-stu-id="bd344-114">Faster execution times for the majority of apps and scenarios.</span></span>
  
- <span data-ttu-id="bd344-115">Çoğu uygulama ve senaryoları için daha hızlı başlangıç süreleri.</span><span class="sxs-lookup"><span data-stu-id="bd344-115">Faster startup times for the majority of apps and scenarios.</span></span> 
  
- <span data-ttu-id="bd344-116">Dağıtım ve güncelleştirme maliyetleri düşük.</span><span class="sxs-lookup"><span data-stu-id="bd344-116">Low deployment and update costs.</span></span>  
  
- <span data-ttu-id="bd344-117">Uygulamanın bellek kullanımı İyileştirildi.</span><span class="sxs-lookup"><span data-stu-id="bd344-117">Optimized app memory usage.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="bd344-118">Uygulamalar ve senaryoları büyük çoğunluğu için .NET Native önemli ölçüde daha hızlı başlangıç süreleri ve IL veya NGEN görüntü için derlenmiş uygulama karşılaştırıldığında daha üstün performans sunar.</span><span class="sxs-lookup"><span data-stu-id="bd344-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="bd344-119">Ancak, sonuçlar farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="bd344-119">However, your results may vary.</span></span> <span data-ttu-id="bd344-120">Uygulamanızı .NET Native'nın performans iyileştirmeleriyle benefited olmak için performansını, uygulamanızın .NET Native sürümü ile karşılaştırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd344-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="bd344-121">Daha fazla bilgi için [performans oturumuna genel bakış](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="bd344-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>
 
<span data-ttu-id="bd344-122">Ancak [!INCLUDE[net_native](../../../includes/net-native-md.md)] birden çok yerel kod için bir derleme içerir.</span><span class="sxs-lookup"><span data-stu-id="bd344-122">But [!INCLUDE[net_native](../../../includes/net-native-md.md)] involves more than a compilation to native code.</span></span> <span data-ttu-id="bd344-123">Bu, .NET Framework uygulamaları yerleşik ve yürütülen şekilde dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="bd344-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="bd344-124">Özellikle:</span><span class="sxs-lookup"><span data-stu-id="bd344-124">In particular:</span></span>  
  
- <span data-ttu-id="bd344-125">Esnasında, gerekli bölümleri .NET Framework'ün uygulamanıza statik olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="bd344-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="bd344-126">Bu uygulamanın .NET Framework ve derleyici genel analiz gerçekleştirmek için performans WINS sunmak için uygulama yerel kitaplıkları ile çalışmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="bd344-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="bd344-127">Sonuç olarak, uygulamaları bile .NET Framework güncelleştirmeleri sonrasında tutarlı bir şekilde daha hızlı başlatma.</span><span class="sxs-lookup"><span data-stu-id="bd344-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>  
  
- <span data-ttu-id="bd344-128">[!INCLUDE[net_native](../../../includes/net-native-md.md)] Çalışma zamanı statik ön derleme için en iyi duruma getirilmiş ve çalışmaları büyük çoğunluğu üstün performans sunar.</span><span class="sxs-lookup"><span data-stu-id="bd344-128">The [!INCLUDE[net_native](../../../includes/net-native-md.md)] runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="bd344-129">Aynı anda geliştiricileri kadar üretken Bul temel yansıma özelliklerini korur.</span><span class="sxs-lookup"><span data-stu-id="bd344-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>  
  
- [!INCLUDE[net_native](../../../includes/net-native-md.md)] <span data-ttu-id="bd344-130">Son olarak aynı geri kullanır C++ statik ön derleme senaryolar için en iyi duruma getirilmiş derleyici.</span><span class="sxs-lookup"><span data-stu-id="bd344-130">uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] <span data-ttu-id="bd344-131">Performans avantajlarının alamazsa C++ yönetilen kod geliştiricilerin olarak aynı veya benzer araçları kullandığından C++ bu tabloda gösterildiği gibi başlık altında.</span><span class="sxs-lookup"><span data-stu-id="bd344-131">is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>  
  
||[!INCLUDE[net_native](../../../includes/net-native-md.md)]|<span data-ttu-id="bd344-132">C++</span><span class="sxs-lookup"><span data-stu-id="bd344-132">C++</span></span>|  
|-|----------------------------------------------------------------|-----------|  
|<span data-ttu-id="bd344-133">Kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="bd344-133">Libraries</span></span>|<span data-ttu-id="bd344-134">.NET Framework ve Windows çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="bd344-134">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="bd344-135">Win32 + Windows çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="bd344-135">Win32 + Windows Runtime</span></span>|  
|<span data-ttu-id="bd344-136">Derleyici</span><span class="sxs-lookup"><span data-stu-id="bd344-136">Compiler</span></span>|<span data-ttu-id="bd344-137">İyileştirici derleyiciyi UTC</span><span class="sxs-lookup"><span data-stu-id="bd344-137">UTC optimizing compiler</span></span>|<span data-ttu-id="bd344-138">İyileştirici derleyiciyi UTC</span><span class="sxs-lookup"><span data-stu-id="bd344-138">UTC optimizing compiler</span></span>|  
|<span data-ttu-id="bd344-139">dağıtılan</span><span class="sxs-lookup"><span data-stu-id="bd344-139">Deployed</span></span>|<span data-ttu-id="bd344-140">Çalıştırılmaya hazır ikili dosyaları</span><span class="sxs-lookup"><span data-stu-id="bd344-140">Ready-to-run binaries</span></span>|<span data-ttu-id="bd344-141">Çalıştırılmaya hazır ikili dosyaları (ASM)</span><span class="sxs-lookup"><span data-stu-id="bd344-141">Ready-to-run binaries (ASM)</span></span>|  
|<span data-ttu-id="bd344-142">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="bd344-142">Runtime</span></span>|<span data-ttu-id="bd344-143">MRT.dll (Minimal CLR Runtime)</span><span class="sxs-lookup"><span data-stu-id="bd344-143">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="bd344-144">CRT.dll (C Runtime)</span><span class="sxs-lookup"><span data-stu-id="bd344-144">CRT.dll (C Runtime)</span></span>|  
  
 <span data-ttu-id="bd344-145">Windows 10 için Windows uygulamaları için .NET yerel kodu derleme ikili dosyaları uygulama paketleri (.appx dosyaları) için Windows Store yükleyin.</span><span class="sxs-lookup"><span data-stu-id="bd344-145">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd344-146">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="bd344-146">In This Section</span></span>  
 <span data-ttu-id="bd344-147">.NET yerel kodu derleme ile uygulamaları geliştirme hakkında daha fazla bilgi için şu konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="bd344-147">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>  
  
- [<span data-ttu-id="bd344-148">.NET yerel kodu derlemesi ile çalışmaya başlama: Geliştirici deneyimi Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="bd344-148">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](../../../docs/framework/net-native/getting-started-with-net-native.md)  
  
- <span data-ttu-id="bd344-149">[.NET native ve derleme:](../../../docs/framework/net-native/net-native-and-compilation.md) Nasıl .NET Native yerel kod projenize derler.</span><span class="sxs-lookup"><span data-stu-id="bd344-149">[.NET Native and Compilation:](../../../docs/framework/net-native/net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>  
  
- [<span data-ttu-id="bd344-150">Yansıma ve .NET Native</span><span class="sxs-lookup"><span data-stu-id="bd344-150">Reflection and .NET Native</span></span>](../../../docs/framework/net-native/reflection-and-net-native.md)  
  
    - [<span data-ttu-id="bd344-151">Yansıma Kullanan API'ler</span><span class="sxs-lookup"><span data-stu-id="bd344-151">APIs That Rely on Reflection</span></span>](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
    - [<span data-ttu-id="bd344-152">Yansıma API'si Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bd344-152">Reflection API Reference</span></span>](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
    - [<span data-ttu-id="bd344-153">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="bd344-153">Runtime Directives (rd.xml) Configuration File Reference</span></span>](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
- [<span data-ttu-id="bd344-154">Serileştirme ve Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="bd344-154">Serialization and Metadata</span></span>](../../../docs/framework/net-native/serialization-and-metadata.md)  
  
- [<span data-ttu-id="bd344-155">Windows Mağazası Uygulamanızı .NET Native'e Taşıma</span><span class="sxs-lookup"><span data-stu-id="bd344-155">Migrating Your Windows Store App to .NET Native</span></span>](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md)  
  
- [<span data-ttu-id="bd344-156">.NET Native Genel Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="bd344-156">.NET Native General Troubleshooting</span></span>](../../../docs/framework/net-native/net-native-general-troubleshooting.md)
