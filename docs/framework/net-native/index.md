---
description: 'Hakkında daha fazla bilgi edinin: .NET Native uygulamalar derleme'
title: .NET Yerel ile Uygulama Derleme
ms.date: 03/30/2017
helpviewer_keywords:
- native compilation
- .NET and native code
- compilation with .NET Native
- .NET Native
- C# and native compilation
ms.assetid: 47cd5648-9469-4b1d-804c-43cc04384045
ms.openlocfilehash: 2626daf17fda751edd7915f15fd4b68ffb623dff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747666"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="f005d-103">.NET Yerel ile Uygulama Derleme</span><span class="sxs-lookup"><span data-stu-id="f005d-103">Compiling Apps with .NET Native</span></span>

<span data-ttu-id="f005d-104">.NET Native, Visual Studio 2015 ve sonraki sürümlerinde bulunan Windows uygulamaları oluşturmak ve dağıtmak için ön derleme teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="f005d-104">.NET Native is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="f005d-105">Yönetilen kodda (C# veya Visual Basic) yazılmış uygulamaların yayın sürümünü otomatik olarak derler ve .NET Framework ve Windows 10 ' a yerel koda hedefleyin.</span><span class="sxs-lookup"><span data-stu-id="f005d-105">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>

<span data-ttu-id="f005d-106">Genellikle, .NET Framework hedefleyen uygulamalar ara dil (IL) ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="f005d-106">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="f005d-107">Çalışma zamanında, tam zamanında (JıT) derleyici, Il 'yi yerel koda dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f005d-107">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="f005d-108">Buna karşılık, Windows uygulamalarını doğrudan yerel koda derler .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f005d-108">In contrast, .NET Native compiles Windows apps directly to native code.</span></span> <span data-ttu-id="f005d-109">Geliştiriciler için şu anlama gelir:</span><span class="sxs-lookup"><span data-stu-id="f005d-109">For developers, this means:</span></span>

- <span data-ttu-id="f005d-110">Uygulamalarınızın yerel kodun performansı vardır.</span><span class="sxs-lookup"><span data-stu-id="f005d-110">Your apps feature the performance of native code.</span></span> <span data-ttu-id="f005d-111">Genellikle, ilk olarak Il 'de derlenen ve sonra JıT derleyicisi tarafından yerel koda derlenen kodların üst işlemi olur.</span><span class="sxs-lookup"><span data-stu-id="f005d-111">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span>

- <span data-ttu-id="f005d-112">C# veya Visual Basic programla çalışmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f005d-112">You can continue to program in C# or Visual Basic.</span></span>

- <span data-ttu-id="f005d-113">Sınıf kitaplığı, otomatik bellek yönetimi ve çöp toplama ve özel durum işleme dahil olmak üzere .NET Framework tarafından belirtilen kaynaklardan faydalanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f005d-113">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>

<span data-ttu-id="f005d-114">Uygulamalarınızın kullanıcıları için .NET Native şu avantajları sunar:</span><span class="sxs-lookup"><span data-stu-id="f005d-114">For users of your apps, .NET Native offers these advantages:</span></span>

- <span data-ttu-id="f005d-115">Uygulama ve senaryoların çoğunluğu için daha hızlı yürütme süreleri.</span><span class="sxs-lookup"><span data-stu-id="f005d-115">Faster execution times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="f005d-116">Uygulama ve senaryoların çoğunluğu için daha hızlı başlangıç süreleri.</span><span class="sxs-lookup"><span data-stu-id="f005d-116">Faster startup times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="f005d-117">Düşük dağıtım ve güncelleştirme maliyetleri.</span><span class="sxs-lookup"><span data-stu-id="f005d-117">Low deployment and update costs.</span></span>

- <span data-ttu-id="f005d-118">En iyileştirilmiş uygulama bellek kullanımı.</span><span class="sxs-lookup"><span data-stu-id="f005d-118">Optimized app memory usage.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f005d-119">Uygulamalar ve senaryoların büyük çoğunluğu için .NET Native, Il 'ye veya NGEN görüntüsüne derlenen bir uygulamayla karşılaştırıldığında önemli ölçüde daha hızlı başlangıç süreleri ve üstün performans sunar.</span><span class="sxs-lookup"><span data-stu-id="f005d-119">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="f005d-120">Ancak, sonuçlarınız farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="f005d-120">However, your results may vary.</span></span> <span data-ttu-id="f005d-121">Uygulamanızın .NET Native performans geliştirmelerinden benefited sahip olduğundan emin olmak için, performansını uygulamanızın non-.NET Native sürümüyle karşılaştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f005d-121">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="f005d-122">Daha fazla bilgi için bkz. [performans oturumuna genel bakış](/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="f005d-122">For more information, see [Performance Session Overview](/visualstudio/profiling/performance-session-overview).</span></span>

<span data-ttu-id="f005d-123">Ancak .NET Native yerel koda bir derlemeden daha fazlasını içerir.</span><span class="sxs-lookup"><span data-stu-id="f005d-123">But .NET Native involves more than a compilation to native code.</span></span> <span data-ttu-id="f005d-124">.NET Framework uygulamalarının oluşturulması ve yürütülmesi şeklini dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="f005d-124">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="f005d-125">Özellikle:</span><span class="sxs-lookup"><span data-stu-id="f005d-125">In particular:</span></span>

- <span data-ttu-id="f005d-126">Ön derleme sırasında .NET Framework gerekli bölümleri uygulamanıza statik olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="f005d-126">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="f005d-127">Bu, uygulamanın .NET Framework uygulama yerel kitaplıklarıyla çalışmasına ve derleyicinin küresel bir şekilde performans sağlamak için genel analizler gerçekleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="f005d-127">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="f005d-128">Sonuç olarak, uygulamalar .NET Framework güncelleştirmelerden sonra bile sürekli olarak daha hızlı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="f005d-128">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>

- <span data-ttu-id="f005d-129">.NET Native çalışma zamanı statik ön derleme için iyileştirilmiştir ve durumların büyük çoğunluğunda üstün performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="f005d-129">The .NET Native runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="f005d-130">Aynı zamanda, geliştiricilerin daha üretken bulduğu temel yansıma özelliklerini korur.</span><span class="sxs-lookup"><span data-stu-id="f005d-130">At the same time, it retains the core reflection features that developers find so productive.</span></span>

- <span data-ttu-id="f005d-131">.NET Native, statik ön derleme senaryolarında en iyi duruma getirilmiş C++ derleyicisi ile aynı arka ucu kullanır.</span><span class="sxs-lookup"><span data-stu-id="f005d-131">.NET Native uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>

<span data-ttu-id="f005d-132">.NET Native, bu tabloda gösterildiği gibi, aynı veya benzer araçlarla C++ ile aynı veya benzer araçları kullandığından, C++ ' ın performans avantajlarını yönetilen kod geliştiricilerine getirebiliyor.</span><span class="sxs-lookup"><span data-stu-id="f005d-132">.NET Native is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>

||<span data-ttu-id="f005d-133">.NET Yerel</span><span class="sxs-lookup"><span data-stu-id="f005d-133">.NET Native</span></span>|<span data-ttu-id="f005d-134">C++</span><span class="sxs-lookup"><span data-stu-id="f005d-134">C++</span></span>|
|-|----------------------------------------------------------------|-----------|
|<span data-ttu-id="f005d-135">Kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="f005d-135">Libraries</span></span>|<span data-ttu-id="f005d-136">.NET Framework + Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="f005d-136">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="f005d-137">Win32 + Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="f005d-137">Win32 + Windows Runtime</span></span>|
|<span data-ttu-id="f005d-138">Derleyici</span><span class="sxs-lookup"><span data-stu-id="f005d-138">Compiler</span></span>|<span data-ttu-id="f005d-139">UTC iyileştirmeli derleyici</span><span class="sxs-lookup"><span data-stu-id="f005d-139">UTC optimizing compiler</span></span>|<span data-ttu-id="f005d-140">UTC iyileştirmeli derleyici</span><span class="sxs-lookup"><span data-stu-id="f005d-140">UTC optimizing compiler</span></span>|
|<span data-ttu-id="f005d-141">Dağıtılan</span><span class="sxs-lookup"><span data-stu-id="f005d-141">Deployed</span></span>|<span data-ttu-id="f005d-142">Çalıştırılmaya hazırlama ikilileri</span><span class="sxs-lookup"><span data-stu-id="f005d-142">Ready-to-run binaries</span></span>|<span data-ttu-id="f005d-143">Çalıştırılmaya hazırlama ikilileri (ASM)</span><span class="sxs-lookup"><span data-stu-id="f005d-143">Ready-to-run binaries (ASM)</span></span>|
|<span data-ttu-id="f005d-144">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="f005d-144">Runtime</span></span>|<span data-ttu-id="f005d-145">MRT.dll (en düşük CLR çalışma zamanı)</span><span class="sxs-lookup"><span data-stu-id="f005d-145">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="f005d-146">CRT.dll (C çalışma zamanı)</span><span class="sxs-lookup"><span data-stu-id="f005d-146">CRT.dll (C Runtime)</span></span>|

<span data-ttu-id="f005d-147">Windows 10 için Windows uygulamaları için, uygulama paketlerinde (. appx dosyaları) .NET Native kod derleme ikililerini Windows Mağazası 'na yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="f005d-147">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f005d-148">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="f005d-148">In This Section</span></span>

<span data-ttu-id="f005d-149">.NET Native kod derlemesi ile uygulama geliştirme hakkında daha fazla bilgi için şu konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="f005d-149">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>

- [<span data-ttu-id="f005d-150">.NET Native kod derleme ile çalışmaya başlama: geliştirici deneyimi Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="f005d-150">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](getting-started-with-net-native.md)

- <span data-ttu-id="f005d-151">[.NET Native ve derleme:](net-native-and-compilation.md) .NET Native projenizi yerel koda nasıl derler.</span><span class="sxs-lookup"><span data-stu-id="f005d-151">[.NET Native and Compilation:](net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>

- [<span data-ttu-id="f005d-152">Yansıma ve .NET Yerel</span><span class="sxs-lookup"><span data-stu-id="f005d-152">Reflection and .NET Native</span></span>](reflection-and-net-native.md)

  - [<span data-ttu-id="f005d-153">Yansıma kullanan API'ler</span><span class="sxs-lookup"><span data-stu-id="f005d-153">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)

  - [<span data-ttu-id="f005d-154">Yansıma API'si Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f005d-154">Reflection API Reference</span></span>](net-native-reflection-api-reference.md)

  - [<span data-ttu-id="f005d-155">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="f005d-155">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)

- [<span data-ttu-id="f005d-156">Serileştirme ve Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="f005d-156">Serialization and Metadata</span></span>](serialization-and-metadata.md)

- [<span data-ttu-id="f005d-157">Windows Mağazası Uygulamanızı .NET Yerel'e Taşıma</span><span class="sxs-lookup"><span data-stu-id="f005d-157">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)

- [<span data-ttu-id="f005d-158">.NET Yerel Genel Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="f005d-158">.NET Native General Troubleshooting</span></span>](net-native-general-troubleshooting.md)
