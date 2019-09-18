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
ms.openlocfilehash: 5993cfdb0f50d8e474a4f18280d181d9ec2fdfa4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049662"
---
# <a name="compiling-apps-with-net-native"></a><span data-ttu-id="309c2-102">.NET Yerel ile Uygulama Derleme</span><span class="sxs-lookup"><span data-stu-id="309c2-102">Compiling Apps with .NET Native</span></span>

<span data-ttu-id="309c2-103">.NET Native, Visual Studio 2015 ve sonraki sürümlerinde bulunan Windows uygulamaları oluşturmak ve dağıtmak için ön derleme teknolojisidir.</span><span class="sxs-lookup"><span data-stu-id="309c2-103">.NET Native is a precompilation technology for building and deploying Windows apps that is included with Visual Studio 2015 and later versions.</span></span> <span data-ttu-id="309c2-104">Yönetilen kodda (C# veya Visual Basic) yazılmış olan ve .NET Framework ve Windows 10 ' un yerel koda hedef alan uygulamaların yayın sürümünü otomatik olarak derler.</span><span class="sxs-lookup"><span data-stu-id="309c2-104">It automatically compiles the release version of apps that are written in managed code (C# or Visual Basic) and that target the .NET Framework and Windows 10 to native code.</span></span>

<span data-ttu-id="309c2-105">Genellikle, .NET Framework hedefleyen uygulamalar ara dil (IL) ile derlenir.</span><span class="sxs-lookup"><span data-stu-id="309c2-105">Typically, apps that target the .NET Framework are compiled to intermediate language (IL).</span></span> <span data-ttu-id="309c2-106">Çalışma zamanında, tam zamanında (JıT) derleyici, Il 'yi yerel koda dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="309c2-106">At run time, the just-in-time (JIT) compiler translates the IL to native code.</span></span> <span data-ttu-id="309c2-107">Buna karşılık, Windows uygulamalarını doğrudan yerel koda derler .NET Native.</span><span class="sxs-lookup"><span data-stu-id="309c2-107">In contrast, .NET Native compiles Windows apps directly to native code.</span></span> <span data-ttu-id="309c2-108">Geliştiriciler için şu anlama gelir:</span><span class="sxs-lookup"><span data-stu-id="309c2-108">For developers, this means:</span></span>

- <span data-ttu-id="309c2-109">Uygulamalarınızın yerel kodun performansı vardır.</span><span class="sxs-lookup"><span data-stu-id="309c2-109">Your apps feature the performance of native code.</span></span> <span data-ttu-id="309c2-110">Genellikle, ilk olarak Il 'de derlenen ve sonra JıT derleyicisi tarafından yerel koda derlenen kodların üst işlemi olur.</span><span class="sxs-lookup"><span data-stu-id="309c2-110">Usually, performance will be superior to code that is first compiled to IL and then compiled to native code by the JIT compiler.</span></span>

- <span data-ttu-id="309c2-111">C# Veya Visual Basic programda çalışmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="309c2-111">You can continue to program in C# or Visual Basic.</span></span>

- <span data-ttu-id="309c2-112">Sınıf kitaplığı, otomatik bellek yönetimi ve çöp toplama ve özel durum işleme dahil olmak üzere .NET Framework tarafından belirtilen kaynaklardan faydalanmaya devam edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="309c2-112">You can continue to take advantage of the resources provided by the .NET Framework, including its class library, automatic memory management and garbage collection, and exception handling.</span></span>

<span data-ttu-id="309c2-113">Uygulamalarınızın kullanıcıları için .NET Native şu avantajları sunar:</span><span class="sxs-lookup"><span data-stu-id="309c2-113">For users of your apps, .NET Native offers these advantages:</span></span>

- <span data-ttu-id="309c2-114">Uygulama ve senaryoların çoğunluğu için daha hızlı yürütme süreleri.</span><span class="sxs-lookup"><span data-stu-id="309c2-114">Faster execution times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="309c2-115">Uygulama ve senaryoların çoğunluğu için daha hızlı başlangıç süreleri.</span><span class="sxs-lookup"><span data-stu-id="309c2-115">Faster startup times for the majority of apps and scenarios.</span></span>

- <span data-ttu-id="309c2-116">Düşük dağıtım ve güncelleştirme maliyetleri.</span><span class="sxs-lookup"><span data-stu-id="309c2-116">Low deployment and update costs.</span></span>

- <span data-ttu-id="309c2-117">En iyileştirilmiş uygulama bellek kullanımı.</span><span class="sxs-lookup"><span data-stu-id="309c2-117">Optimized app memory usage.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="309c2-118">Uygulamalar ve senaryoların büyük çoğunluğu için .NET Native, Il 'ye veya NGEN görüntüsüne derlenen bir uygulamayla karşılaştırıldığında önemli ölçüde daha hızlı başlangıç süreleri ve üstün performans sunar.</span><span class="sxs-lookup"><span data-stu-id="309c2-118">For the vast majority of apps and scenarios, .NET Native offers significantly faster startup times and superior performance when compared to an app compiled to IL or to an NGEN image.</span></span> <span data-ttu-id="309c2-119">Ancak, sonuçlarınız farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="309c2-119">However, your results may vary.</span></span> <span data-ttu-id="309c2-120">Uygulamanızın .NET Native performans geliştirmelerinden benefited sahip olduğundan emin olmak için, performansını uygulamanızın non-.NET Native sürümüyle karşılaştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="309c2-120">To ensure that your app has benefited from the performance enhancements of .NET Native, you should compare its performance with that of the non-.NET Native version of your app.</span></span> <span data-ttu-id="309c2-121">Daha fazla bilgi için bkz. [performans oturumuna genel bakış](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span><span class="sxs-lookup"><span data-stu-id="309c2-121">For more information, see [Performance Session Overview](https://docs.microsoft.com/visualstudio/profiling/performance-session-overview).</span></span>

<span data-ttu-id="309c2-122">Ancak .NET Native yerel koda bir derlemeden daha fazlasını içerir.</span><span class="sxs-lookup"><span data-stu-id="309c2-122">But .NET Native involves more than a compilation to native code.</span></span> <span data-ttu-id="309c2-123">.NET Framework uygulamalarının oluşturulması ve yürütülmesi şeklini dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="309c2-123">It transforms the way that .NET Framework apps are built and executed.</span></span> <span data-ttu-id="309c2-124">Özellikle:</span><span class="sxs-lookup"><span data-stu-id="309c2-124">In particular:</span></span>

- <span data-ttu-id="309c2-125">Ön derleme sırasında .NET Framework gerekli bölümleri uygulamanıza statik olarak bağlanır.</span><span class="sxs-lookup"><span data-stu-id="309c2-125">During precompilation, required portions of the .NET Framework are statically linked into your app.</span></span> <span data-ttu-id="309c2-126">Bu, uygulamanın .NET Framework uygulama yerel kitaplıklarıyla çalışmasına ve derleyicinin küresel bir şekilde performans sağlamak için genel analizler gerçekleştirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="309c2-126">This allows the app to run with app-local libraries of the .NET Framework, and the compiler to perform global analysis to deliver performance wins.</span></span> <span data-ttu-id="309c2-127">Sonuç olarak, uygulamalar .NET Framework güncelleştirmelerden sonra bile sürekli olarak daha hızlı başlatılır.</span><span class="sxs-lookup"><span data-stu-id="309c2-127">As a result, apps launch consistently faster even after .NET Framework updates.</span></span>

- <span data-ttu-id="309c2-128">.NET Native çalışma zamanı statik ön derleme için iyileştirilmiştir ve durumların büyük çoğunluğunda üstün performans sağlar.</span><span class="sxs-lookup"><span data-stu-id="309c2-128">The .NET Native runtime is optimized for static precompilation and in the vast majority of cases offers superior performance.</span></span> <span data-ttu-id="309c2-129">Aynı zamanda, geliştiricilerin daha üretken bulduğu temel yansıma özelliklerini korur.</span><span class="sxs-lookup"><span data-stu-id="309c2-129">At the same time, it retains the core reflection features that developers find so productive.</span></span>

- <span data-ttu-id="309c2-130">.NET Native, C++ derleyici ile aynı arka ucu kullanarak statik ön derleme senaryolarında en iyi duruma getirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="309c2-130">.NET Native uses the same back end as the C++ compiler, which is optimized for static precompilation scenarios.</span></span>

<span data-ttu-id="309c2-131">.NET Native, bu tabloda gösterildiği gibi, aynı veya C++ benzer araçları C++ kullandığından, yönetilen kod geliştiricilerine ait performans avantajlarını getirebiliyor.</span><span class="sxs-lookup"><span data-stu-id="309c2-131">.NET Native is able to bring the performance benefits of C++ to managed code developers because it uses the same or similar tools as C++ under the hood, as shown in this table.</span></span>

||<span data-ttu-id="309c2-132">.NET Yerel</span><span class="sxs-lookup"><span data-stu-id="309c2-132">.NET Native</span></span>|<span data-ttu-id="309c2-133">C++</span><span class="sxs-lookup"><span data-stu-id="309c2-133">C++</span></span>|
|-|----------------------------------------------------------------|-----------|
|<span data-ttu-id="309c2-134">Kitaplıklar</span><span class="sxs-lookup"><span data-stu-id="309c2-134">Libraries</span></span>|<span data-ttu-id="309c2-135">.NET Framework + Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="309c2-135">The .NET Framework + Windows Runtime</span></span>|<span data-ttu-id="309c2-136">Win32 + Windows Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="309c2-136">Win32 + Windows Runtime</span></span>|
|<span data-ttu-id="309c2-137">Derleyici</span><span class="sxs-lookup"><span data-stu-id="309c2-137">Compiler</span></span>|<span data-ttu-id="309c2-138">UTC iyileştirmeli derleyici</span><span class="sxs-lookup"><span data-stu-id="309c2-138">UTC optimizing compiler</span></span>|<span data-ttu-id="309c2-139">UTC iyileştirmeli derleyici</span><span class="sxs-lookup"><span data-stu-id="309c2-139">UTC optimizing compiler</span></span>|
|<span data-ttu-id="309c2-140">Dağıtılan</span><span class="sxs-lookup"><span data-stu-id="309c2-140">Deployed</span></span>|<span data-ttu-id="309c2-141">Çalıştırılmaya hazırlama ikilileri</span><span class="sxs-lookup"><span data-stu-id="309c2-141">Ready-to-run binaries</span></span>|<span data-ttu-id="309c2-142">Çalıştırılmaya hazırlama ikilileri (ASM)</span><span class="sxs-lookup"><span data-stu-id="309c2-142">Ready-to-run binaries (ASM)</span></span>|
|<span data-ttu-id="309c2-143">Çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="309c2-143">Runtime</span></span>|<span data-ttu-id="309c2-144">MRT. dll (minimum CLR Runtime)</span><span class="sxs-lookup"><span data-stu-id="309c2-144">MRT.dll (Minimal CLR Runtime)</span></span>|<span data-ttu-id="309c2-145">CRT. dll (C çalışma zamanı)</span><span class="sxs-lookup"><span data-stu-id="309c2-145">CRT.dll (C Runtime)</span></span>|

<span data-ttu-id="309c2-146">Windows 10 için Windows uygulamaları için, uygulama paketlerinde (. appx dosyaları) .NET Native kod derleme ikililerini Windows Mağazası 'na yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="309c2-146">For Windows apps for Windows 10, you upload .NET Native Code Compilation binaries in app packages (.appx files) to the Windows Store.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="309c2-147">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="309c2-147">In This Section</span></span>

<span data-ttu-id="309c2-148">.NET Native kod derlemesi ile uygulama geliştirme hakkında daha fazla bilgi için şu konulara bakın:</span><span class="sxs-lookup"><span data-stu-id="309c2-148">For more information about developing apps with .NET Native Code Compilation, see these topics:</span></span>

- [<span data-ttu-id="309c2-149">.NET Native kodu derleme ile çalışmaya başlama: Geliştirici deneyimi Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="309c2-149">Getting Started with .NET Native Code Compilation: The Developer Experience Walkthrough</span></span>](getting-started-with-net-native.md)

- <span data-ttu-id="309c2-150">[.NET Native ve derleme:](net-native-and-compilation.md) .NET Native projenizi yerel koda nasıl derler.</span><span class="sxs-lookup"><span data-stu-id="309c2-150">[.NET Native and Compilation:](net-native-and-compilation.md) How .NET Native compiles your project to native code.</span></span>

- [<span data-ttu-id="309c2-151">Yansıma ve .NET Native</span><span class="sxs-lookup"><span data-stu-id="309c2-151">Reflection and .NET Native</span></span>](reflection-and-net-native.md)

  - [<span data-ttu-id="309c2-152">Yansıma Kullanan API'ler</span><span class="sxs-lookup"><span data-stu-id="309c2-152">APIs That Rely on Reflection</span></span>](apis-that-rely-on-reflection.md)

  - [<span data-ttu-id="309c2-153">Yansıma API'si Başvurusu</span><span class="sxs-lookup"><span data-stu-id="309c2-153">Reflection API Reference</span></span>](net-native-reflection-api-reference.md)

  - [<span data-ttu-id="309c2-154">Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu</span><span class="sxs-lookup"><span data-stu-id="309c2-154">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)

- [<span data-ttu-id="309c2-155">Serileştirme ve Meta Veriler</span><span class="sxs-lookup"><span data-stu-id="309c2-155">Serialization and Metadata</span></span>](serialization-and-metadata.md)

- [<span data-ttu-id="309c2-156">Windows Mağazası Uygulamanızı .NET Native'e Taşıma</span><span class="sxs-lookup"><span data-stu-id="309c2-156">Migrating Your Windows Store App to .NET Native</span></span>](migrating-your-windows-store-app-to-net-native.md)

- [<span data-ttu-id="309c2-157">.NET Native Genel Sorun Giderme</span><span class="sxs-lookup"><span data-stu-id="309c2-157">.NET Native General Troubleshooting</span></span>](net-native-general-troubleshooting.md)
