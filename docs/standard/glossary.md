---
title: .NET Sözlüğü
description: .NET belgelerinde kullanılan seçili terimlerin anlamını öğrenin.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 590d44ac64bc2b86ed0a082ae5185cf60b28c36c
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291560"
---
# <a name="net-glossary"></a><span data-ttu-id="96bd0-103">.NET Sözlüğü</span><span class="sxs-lookup"><span data-stu-id="96bd0-103">.NET Glossary</span></span>

<span data-ttu-id="96bd0-104">Bu sözlüğün birincil amacı, .NET belgelerinde tanımları olmadan sık sık görünen seçili terimlerin ve kısaltmaların anlamlarını netleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="96bd0-105">AOT</span><span class="sxs-lookup"><span data-stu-id="96bd0-105">AOT</span></span>

<span data-ttu-id="96bd0-106">Zaman compiler'ı.</span><span class="sxs-lookup"><span data-stu-id="96bd0-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="96bd0-107">[JIT](#jit)benzer, bu derleyici de makine kodu [IL](#il) çevirir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="96bd0-108">JIT derlemesinin aksine, AOT derlemesi uygulama yürütülmeden önce gerçekleşir ve genellikle farklı bir makinede gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="96bd0-109">AOT takım zincirleri çalışma zamanında derlenmediği için derleme için harcanan zamanı en aza indirmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-109">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="96bd0-110">Bu da optimizasyon için daha fazla zaman harcayabilecekleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="96bd0-111">AOT bağlamı tüm uygulama olduğundan, AOT derleyicisi ayrıca tüm başvuruların takip edildiği ve tek bir çalıştırılabilir üretildiği anlamına gelen çapraz modül bağlantı ve tam program analizi ni gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="96bd0-112">[Bkz. CoreRT](#corert) ve [.NET Native](#net-native).</span><span class="sxs-lookup"><span data-stu-id="96bd0-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="aspnet"></a><span data-ttu-id="96bd0-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="96bd0-113">ASP.NET</span></span>

<span data-ttu-id="96bd0-114">.NET Framework ile yapılan orijinal ASP.NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="96bd0-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="96bd0-115">Bazen ASP.NET, ASP.NET Core dahil olmak üzere her iki ASP.NET uygulamaları ifade eden bir şemsiye terimdir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="96bd0-116">Terimin herhangi bir durumda taşıdığı anlam bağlam tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="96bd0-117">Her iki uygulama anlamına ASP.NET kullanmadığınızı açıkça belirtmek istediğinizde ASP.NET 4.x'e bakın.</span><span class="sxs-lookup"><span data-stu-id="96bd0-117">Refer to ASP.NET 4.x when you want to make it clear that you're not using ASP.NET to mean both implementations.</span></span>

<span data-ttu-id="96bd0-118">[ASP.NET dokümantasyona](/aspnet/#pivot=aspnet)bakın.</span><span class="sxs-lookup"><span data-stu-id="96bd0-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="96bd0-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="96bd0-119">ASP.NET Core</span></span>

<span data-ttu-id="96bd0-120">.NET Core üzerine kurulu ASP.NET çapraz platform, yüksek performanslı, açık kaynak uygulaması.</span><span class="sxs-lookup"><span data-stu-id="96bd0-120">A cross-platform, high-performance, open-source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="96bd0-121">[Bkz. ASP.NET Çekirdek belgeleri.](/aspnet/#pivot=core)</span><span class="sxs-lookup"><span data-stu-id="96bd0-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="96bd0-122">derleme</span><span class="sxs-lookup"><span data-stu-id="96bd0-122">assembly</span></span>

<span data-ttu-id="96bd0-123">Uygulamalar veya diğer derlemeler tarafından çağrılabilen bir API koleksiyonu içerebilen *.dll*/*.exe* dosyası.</span><span class="sxs-lookup"><span data-stu-id="96bd0-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="96bd0-124">Derleme, arabirimler, sınıflar, yapılar, sayısallamalar ve temsilciler gibi türleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="96bd0-125">Projenin *çöp kutusu* klasöründeki derlemeler bazen *ikili*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="96bd0-126">Ayrıca [kitaplık](#library)bakın.</span><span class="sxs-lookup"><span data-stu-id="96bd0-126">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="96bd0-127">CLR</span><span class="sxs-lookup"><span data-stu-id="96bd0-127">CLR</span></span>

<span data-ttu-id="96bd0-128">Ortak Dil Çalışma Zamanı.</span><span class="sxs-lookup"><span data-stu-id="96bd0-128">Common Language Runtime.</span></span>

<span data-ttu-id="96bd0-129">Tam anlamı içeriğe bağlıdır, ancak Ortak Dil Çalışma Süresi genellikle .NET Framework'ün çalışma zamanını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="96bd0-129">The exact meaning depends on the context, but Common Language Runtime usually refers to the runtime of .NET Framework.</span></span> <span data-ttu-id="96bd0-130">CLR bellek ayırma ve yönetimi işler.</span><span class="sxs-lookup"><span data-stu-id="96bd0-130">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="96bd0-131">CLR aynı zamanda sadece uygulamaları yürütmekle kalmamış, aynı zamanda [bir JIT](#jit) derleyicisi kullanarak anında kod üreten ve derleyen sanal bir makinedir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-131">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span> <span data-ttu-id="96bd0-132">Geçerli Microsoft CLR uygulaması yalnızca Windows'dur.</span><span class="sxs-lookup"><span data-stu-id="96bd0-132">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="96bd0-133">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="96bd0-133">CoreCLR</span></span>

<span data-ttu-id="96bd0-134">.NET Çekirdek Ortak Dil Çalışma Zamanı.</span><span class="sxs-lookup"><span data-stu-id="96bd0-134">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="96bd0-135">Bu CLR, CLR ile aynı kod tabanından oluşturulmuştür.</span><span class="sxs-lookup"><span data-stu-id="96bd0-135">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="96bd0-136">Başlangıçta, CoreCLR Silverlight çalışma zamanı ve birden fazla platformda çalıştırmak için tasarlanmıştır, özellikle Windows ve OS X. CoreCLR şimdi .NET Core bir parçasıdır ve CLR basitleştirilmiş bir sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="96bd0-136">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="96bd0-137">Hala birçok Linux dağıtımı için destek de dahil olmak üzere, bir [çapraz platform](#cross-platform) çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="96bd0-137">It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="96bd0-138">CoreCLR aynı zamanda JIT ve kod yürütme yetenekleri ile sanal bir makinedir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-138">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="96bd0-139">CoreFX</span><span class="sxs-lookup"><span data-stu-id="96bd0-139">CoreFX</span></span>

<span data-ttu-id="96bd0-140">.NET Çekirdek Taban Sınıf Kitaplığı (BCL)</span><span class="sxs-lookup"><span data-stu-id="96bd0-140">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="96bd0-141">Sistemi oluşturan bir dizi kitaplık. \* (ve sınırlı bir ölçüde\*Microsoft. ) ad boşlukları.</span><span class="sxs-lookup"><span data-stu-id="96bd0-141">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="96bd0-142">BCL, ASP.NET Core gibi üst düzey uygulama çerçevelerinin temeline sahip olan genel bir amaç, alt düzey bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-142">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="96bd0-143">.NET Core BCL'nin kaynak kodu [.NET Core çalışma zamanı deposunda](https://github.com/dotnet/runtime)bulunur.</span><span class="sxs-lookup"><span data-stu-id="96bd0-143">The source code of the .NET Core BCL is contained in the [.NET Core runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="96bd0-144">Ancak, .NET Core API'lerinin çoğu .NET Framework'de de mevcuttur, böylece CoreFX'i .NET Framework BCL'nin çatalı olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96bd0-144">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="96bd0-145">CoreRT</span><span class="sxs-lookup"><span data-stu-id="96bd0-145">CoreRT</span></span>

<span data-ttu-id="96bd0-146">.NET Çekirdek çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="96bd0-146">.NET Core runtime.</span></span>

<span data-ttu-id="96bd0-147">CLR /CoreCLR'nin aksine CoreRT sanal bir makine değildir, bu da [jit](#jit)içermediği için anında kod oluşturma ve çalıştırma olanaklarını içermediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-147">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="96bd0-148">Ancak, [GC](#gc) ve çalışma zamanı türü tanımlama (RTTI) ve yansıma yeteneği içerir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-148">It does, however, include the [GC](#gc) and the ability for run-time type identification (RTTI) and reflection.</span></span> <span data-ttu-id="96bd0-149">Ancak, yazı sistemi yansıma için meta veri gerekli olmayacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-149">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="96bd0-150">Meta veri gerektirmemesi, gereksiz meta verileri birbirine bağlayabilen ve (daha da önemlisi) uygulamanın kullanmadığı kodu tanımlayabilen bir [AOT](#aot) araç zincirine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="96bd0-150">Not requiring metadata enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="96bd0-151">CoreRT geliştirilmekte.</span><span class="sxs-lookup"><span data-stu-id="96bd0-151">CoreRT is in development.</span></span>

<span data-ttu-id="96bd0-152">Bkz. [Intro to .NET Native ve CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span><span class="sxs-lookup"><span data-stu-id="96bd0-152">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="96bd0-153">platformlar arası</span><span class="sxs-lookup"><span data-stu-id="96bd0-153">cross-platform</span></span>

<span data-ttu-id="96bd0-154">Linux, Windows ve iOS gibi birden çok farklı işletim sisteminde, her biri için özel olarak yeniden yazmak zorunda kalmadan kullanılabilen bir uygulama geliştirme ve yürütme olanağı.</span><span class="sxs-lookup"><span data-stu-id="96bd0-154">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows, and iOS, without having to rewrite specifically for each one.</span></span> <span data-ttu-id="96bd0-155">Bu, kodun yeniden kullanılmasını ve farklı platformlardaki uygulamalar arasında tutarlılık sağlar.</span><span class="sxs-lookup"><span data-stu-id="96bd0-155">This enables code reuse and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="96bd0-156">Ekosistem</span><span class="sxs-lookup"><span data-stu-id="96bd0-156">ecosystem</span></span>

<span data-ttu-id="96bd0-157">Belirli bir teknoloji için uygulamalar oluşturmak ve çalıştırmak için kullanılan tüm çalışma zamanı yazılımları, geliştirme araçları ve topluluk kaynakları.</span><span class="sxs-lookup"><span data-stu-id="96bd0-157">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="96bd0-158">".NET ekosistemi" terimi, üçüncü taraf uygulamaları ve kitaplıkları dahil etmede ".NET yığını" gibi benzer terimlerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-158">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="96bd0-159">Bir cümlede bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="96bd0-159">Here's an example in a sentence:</span></span>

- <span data-ttu-id="96bd0-160">[".NET Standardının](#net-standard) arkasındaki motivasyon .NET ekosisteminde daha fazla tekdüzelik oluşturmaktır."</span><span class="sxs-lookup"><span data-stu-id="96bd0-160">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span>

## <a name="framework"></a><span data-ttu-id="96bd0-161">çerçeve</span><span class="sxs-lookup"><span data-stu-id="96bd0-161">framework</span></span>

<span data-ttu-id="96bd0-162">Genel olarak, belirli bir teknolojiye dayalı uygulamaların geliştirilmesini ve dağıtılmasını kolaylaştıran kapsamlı bir API koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="96bd0-162">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="96bd0-163">Bu genel anlamda, ASP.NET Çekirdek ve Windows Formları uygulama çerçevelerine örnektir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-163">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="96bd0-164">Ayrıca [kitaplık](#library)bakın.</span><span class="sxs-lookup"><span data-stu-id="96bd0-164">See also [library](#library).</span></span>

<span data-ttu-id="96bd0-165">"Çerçeve" sözcüğünün aşağıdaki terimlerde daha spesifik bir teknik anlamı vardır:</span><span class="sxs-lookup"><span data-stu-id="96bd0-165">The word "framework" has a more specific technical meaning in the following terms:</span></span>

- [<span data-ttu-id="96bd0-166">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="96bd0-166">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="96bd0-167">hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="96bd0-167">target framework</span></span>](#target-framework)
- [<span data-ttu-id="96bd0-168">TFM (hedef çerçeve takma adıyla)</span><span class="sxs-lookup"><span data-stu-id="96bd0-168">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="96bd0-169">Varolan belgelerde "çerçeve" bazen [.NET'in uygulanmasını](#implementation-of-net)ifade eder.</span><span class="sxs-lookup"><span data-stu-id="96bd0-169">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="96bd0-170">Örneğin, bir makale .NET Core'u bir çerçeve olarak adlandırabilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-170">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="96bd0-171">Bu kafa karıştırıcı kullanımı belgelerden ortadan kaldırmayı planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="96bd0-171">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="96bd0-172">GC</span><span class="sxs-lookup"><span data-stu-id="96bd0-172">GC</span></span>

<span data-ttu-id="96bd0-173">Çöp toplayıcısı.</span><span class="sxs-lookup"><span data-stu-id="96bd0-173">Garbage collector.</span></span>

<span data-ttu-id="96bd0-174">Çöp toplayıcı otomatik bellek yönetiminin bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-174">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="96bd0-175">GC, artık kullanılmayan nesneler tarafından işgal edilen belleği serbest eder.</span><span class="sxs-lookup"><span data-stu-id="96bd0-175">The GC frees memory occupied by objects that are no longer in use.</span></span>

<span data-ttu-id="96bd0-176">[Bkz. Çöp Toplama](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="96bd0-176">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="96bd0-177">IL</span><span class="sxs-lookup"><span data-stu-id="96bd0-177">IL</span></span>

<span data-ttu-id="96bd0-178">Ara dil.</span><span class="sxs-lookup"><span data-stu-id="96bd0-178">Intermediate language.</span></span>

<span data-ttu-id="96bd0-179">C# gibi üst düzey .NET dilleri, Ara Dil (IL) olarak adlandırılan donanım-agnostik yönerge kümesine kadar derlenir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-179">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="96bd0-180">IL bazen MSIL (Microsoft IL) veya CIL (Ortak IL) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-180">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="96bd0-181">JIT</span><span class="sxs-lookup"><span data-stu-id="96bd0-181">JIT</span></span>

<span data-ttu-id="96bd0-182">Tam zamanında derleyici.</span><span class="sxs-lookup"><span data-stu-id="96bd0-182">Just-in-time compiler.</span></span>

<span data-ttu-id="96bd0-183">[AOT'ye](#aot)benzer şekilde, bu derleyici [IL'yi](#il) işlemcinin anladığı makine koduna çevirir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-183">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="96bd0-184">AOT'nin aksine, JIT derlemesi isteğe bağlı olarak gerçekleşir ve kodun çalışması gereken makinede gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-184">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="96bd0-185">JIT derlemesi uygulamanın yürütülmesi sırasında oluştuğundan derleme süresi çalışma süresinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-185">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="96bd0-186">Bu nedenle, JIT derleyicileri, kodu en iyi duruma getirmek için harcanan zamanı, ortaya çıkan kodun oluşturabileceği tasarruflara göre dengelemek zorunda kalır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-186">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="96bd0-187">Ama bir JIT gerçek donanım bilir ve farklı uygulamalar gemi sahip geliştiriciler ücretsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-187">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="96bd0-188">.NET uygulaması</span><span class="sxs-lookup"><span data-stu-id="96bd0-188">implementation of .NET</span></span>

<span data-ttu-id="96bd0-189">.NET'in bir uygulaması şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="96bd0-189">An implementation of .NET includes:</span></span>

- <span data-ttu-id="96bd0-190">Bir veya daha fazla çalışma saatleri.</span><span class="sxs-lookup"><span data-stu-id="96bd0-190">One or more runtimes.</span></span> <span data-ttu-id="96bd0-191">Örnekler: CLR, CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="96bd0-191">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="96bd0-192">.NET Standardının bir sürümünü uygulayan ve ek API'ler içerebilen bir sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="96bd0-192">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="96bd0-193">Örnekler: .NET Framework Base Sınıf Kitaplığı, .NET Çekirdek Taban Sınıf Kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="96bd0-193">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="96bd0-194">İsteğe bağlı olarak, bir veya daha fazla uygulama çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="96bd0-194">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="96bd0-195">Örnekler: ASP.NET, Windows Formları ve WPF .NET Çerçevesi'ne dahildir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-195">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="96bd0-196">İsteğe bağlı olarak, geliştirme araçları.</span><span class="sxs-lookup"><span data-stu-id="96bd0-196">Optionally, development tools.</span></span> <span data-ttu-id="96bd0-197">Bazı geliştirme araçları birden çok uygulama arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-197">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="96bd0-198">.NET uygulamalarına örnekler:</span><span class="sxs-lookup"><span data-stu-id="96bd0-198">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="96bd0-199">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="96bd0-199">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="96bd0-200">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96bd0-200">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="96bd0-201">Evrensel Windows Platformu (UWP)</span><span class="sxs-lookup"><span data-stu-id="96bd0-201">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="96bd0-202">kitaplık</span><span class="sxs-lookup"><span data-stu-id="96bd0-202">library</span></span>

<span data-ttu-id="96bd0-203">Uygulamalar veya diğer kitaplıklar tarafından çağrılabilen API koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="96bd0-203">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="96bd0-204">.NET kitaplığı bir veya daha fazla [derlemeden](#assembly)oluşur.</span><span class="sxs-lookup"><span data-stu-id="96bd0-204">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="96bd0-205">Kitaplık ve [çerçeve](#framework) sözcükleri genellikle eş anlamlı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-205">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="96bd0-206">metapaketi</span><span class="sxs-lookup"><span data-stu-id="96bd0-206">metapackage</span></span>

<span data-ttu-id="96bd0-207">Kendi kitaplığı olmayan ancak yalnızca bağımlılıkların bir listesi olan Bir NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="96bd0-207">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="96bd0-208">Dahil edilen paketler isteğe bağlı olarak bir hedef çerçeve için API'yi kurabilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-208">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="96bd0-209">Bkz. [Paketler, Metapaketler ve Çerçeveler](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="96bd0-209">See [Packages, Metapackages, and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="96bd0-210">Mono</span><span class="sxs-lookup"><span data-stu-id="96bd0-210">Mono</span></span>

<span data-ttu-id="96bd0-211">Mono, çoğunlukla küçük bir çalışma süresi gerektiğinde kullanılan açık kaynak kodlu, [çapraz platform](#cross-platform) .NET uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-211">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="96bd0-212">Android, Mac, iOS, tvOS ve watchOS'taki Xamarin uygulamalarına güç veren ve öncelikle küçük bir ayak izi gerektiren uygulamalara odaklanan çalışma zamanıdır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-212">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS, and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="96bd0-213">Şu anda yayınlanan tüm .NET Standard sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="96bd0-213">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="96bd0-214">Tarihsel olarak, Mono .NET Framework'ün daha büyük API'sini uyguladı ve Unix'teki en popüler yeteneklerden bazılarını taklit etti.</span><span class="sxs-lookup"><span data-stu-id="96bd0-214">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="96bd0-215">Bazen Unix'teki bu özelliklere dayanan .NET uygulamalarını çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-215">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="96bd0-216">Mono genellikle tam zamanında derleyici ile kullanılır, ancak aynı zamanda iOS gibi platformlarda kullanılan tam bir statik derleyici (ileri-zaman derleme) özellikleri.</span><span class="sxs-lookup"><span data-stu-id="96bd0-216">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="96bd0-217">Mono hakkında daha fazla bilgi edinmek için [Mono belgelerine](https://www.mono-project.com/docs/)bakın.</span><span class="sxs-lookup"><span data-stu-id="96bd0-217">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="96bd0-218">.NET</span><span class="sxs-lookup"><span data-stu-id="96bd0-218">.NET</span></span>

<span data-ttu-id="96bd0-219">[.NET Standard](#net-standard) ve tüm [.NET uygulamaları](#implementation-of-net) ve iş yükleri için şemsiye terim.</span><span class="sxs-lookup"><span data-stu-id="96bd0-219">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="96bd0-220">Her zaman tamamen büyük harfle, asla ".Net".</span><span class="sxs-lookup"><span data-stu-id="96bd0-220">Always fully capitalized, never ".Net".</span></span>

<span data-ttu-id="96bd0-221">[.NET Kılavuzuna](index.md) Bakın</span><span class="sxs-lookup"><span data-stu-id="96bd0-221">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="96bd0-222">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96bd0-222">.NET Core</span></span>

<span data-ttu-id="96bd0-223">.NET'in çapraz platform, yüksek performanslı, açık kaynak uygulaması.</span><span class="sxs-lookup"><span data-stu-id="96bd0-223">A cross-platform, high-performance, open-source implementation of .NET.</span></span> <span data-ttu-id="96bd0-224">Core Common Language Runtime (CoreCLR), Core AOT Runtime (CoreRT, geliştirme), Core Base Sınıf Kitaplığı ve Core SDK'yı içerir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-224">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="96bd0-225">Bkz. [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="96bd0-225">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="96bd0-226">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="96bd0-226">.NET Core CLI</span></span>

<span data-ttu-id="96bd0-227">.NET Core uygulamalarını geliştirmek için bir çapraz platform araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="96bd0-227">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="96bd0-228">Bkz. [.NET Çekirdek CLI](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="96bd0-228">See [.NET Core CLI](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="96bd0-229">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="96bd0-229">.NET Core SDK</span></span>

<span data-ttu-id="96bd0-230">Geliştiricilerin .NET Core uygulamaları ve kitaplıkları oluşturmasına olanak tanıyan kitaplıklar ve araçlar kümesi.</span><span class="sxs-lookup"><span data-stu-id="96bd0-230">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="96bd0-231">Uygulama oluşturmak için [.NET Core CLI'yi,](#net-core-cli) .NET Core kitaplıklarını ve uygulamaları oluşturmak ve çalıştırmak için çalışma süresini ve CLI komutlarını çalıştıran ve uygulamaları çalıştıran*dotnet(dotnet.exe)* içerir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-231">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="96bd0-232">Bkz. [.NET Core SDK Genel Bakış](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="96bd0-232">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="96bd0-233">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="96bd0-233">.NET Framework</span></span>

<span data-ttu-id="96bd0-234">.NET'in yalnızca Windows'da çalışan bir uygulaması.</span><span class="sxs-lookup"><span data-stu-id="96bd0-234">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="96bd0-235">Ortak Dil Çalışma Zamanı (CLR), Temel Sınıf Kitaplığı ve ASP.NET, Windows Forms ve WPF gibi uygulama çerçevesi kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-235">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="96bd0-236">Bkz. [.NET Çerçeve Rehberi](../framework/index.yml).</span><span class="sxs-lookup"><span data-stu-id="96bd0-236">See [.NET Framework Guide](../framework/index.yml).</span></span>

## <a name="net-native"></a><span data-ttu-id="96bd0-237">.NET Yerel</span><span class="sxs-lookup"><span data-stu-id="96bd0-237">.NET Native</span></span>

<span data-ttu-id="96bd0-238">Tam zamanında (JIT) aksine, yerel kodu zamanından önce (AOT) üreten bir derleyici araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="96bd0-238">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="96bd0-239">Derleme, geliştiricinin makinesinde C++ derleyicisi ve bağlayıcısının çalışma şekline benzer şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-239">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="96bd0-240">Kullanılmayan kodu kaldırır ve en iyi duruma çıkarmak için daha fazla zaman harcar.</span><span class="sxs-lookup"><span data-stu-id="96bd0-240">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="96bd0-241">Kitaplıklardan kod ayıklar ve bunları yürütülebilir kodlarla birleştirir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-241">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="96bd0-242">Sonuç, tüm uygulamayı temsil eden tek bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="96bd0-242">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="96bd0-243">UWP, .NET Native tarafından desteklenen ilk uygulama çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-243">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="96bd0-244">Artık Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="96bd0-244">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="96bd0-245">Bkz. [Intro to .NET Native ve CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="96bd0-245">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="96bd0-246">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="96bd0-246">.NET Standard</span></span>

<span data-ttu-id="96bd0-247">Her .NET uygulamasında bulunan .NET API'lerinin resmi bir belirtimi.</span><span class="sxs-lookup"><span data-stu-id="96bd0-247">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="96bd0-248">.NET Standart belirtimi bazen belgelerde kitaplık olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-248">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="96bd0-249">Kitaplık API uygulamalarını içerdiğinden, yalnızca belirtimler (arabirimler) değil, .NET Standard'a "kitaplık" demek yanıltıcıdır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-249">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="96bd0-250">.NET Standart metapaketinin adı dışında bu kullanımı belgelerden ortadan kaldırmayı`NETStandard.Library`planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="96bd0-250">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="96bd0-251">Bkz. [.NET Standart](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="96bd0-251">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="96bd0-252">Ngen</span><span class="sxs-lookup"><span data-stu-id="96bd0-252">NGEN</span></span>

<span data-ttu-id="96bd0-253">Yerli (görüntü) nesil.</span><span class="sxs-lookup"><span data-stu-id="96bd0-253">Native (image) generation.</span></span>

<span data-ttu-id="96bd0-254">Bu teknolojiyi kalıcı bir JIT derleyicisi olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="96bd0-254">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="96bd0-255">Genellikle kodun yürütüldüğü makinede kod derler, ancak derleme genellikle yükleme zamanında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-255">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="96bd0-256">Paket</span><span class="sxs-lookup"><span data-stu-id="96bd0-256">package</span></span>

<span data-ttu-id="96bd0-257">NuGet paketi &mdash; veya yalnızca &mdash; bir paket, yazar adı gibi ek meta verilerin yanı sıra aynı adı taşıyan bir veya daha fazla derlemeye sahip bir *.zip* dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-257">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="96bd0-258">*.zip* dosyası *.nupkg* uzantısına sahiptir ve birden çok hedef çerçevesi ve sürümü yle kullanılmak üzere *.dll* dosyaları ve *.xml* dosyaları gibi varlıklar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-258">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="96bd0-259">Bir uygulamaya veya kitaplıkta yüklendiğinde, uygulama veya kitaplık tarafından belirlenen hedef çerçeveye göre uygun varlıklar seçilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-259">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="96bd0-260">Arabirimi tanımlayan varlıklar *ref* klasöründe, uygulamayı tanımlayan varlıklar *ise lib* klasöründedir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-260">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="96bd0-261">platform</span><span class="sxs-lookup"><span data-stu-id="96bd0-261">platform</span></span>

<span data-ttu-id="96bd0-262">Windows, macOS, Linux, iOS ve Android gibi bir işletim sistemi ve çalıştırılaç donanımı.</span><span class="sxs-lookup"><span data-stu-id="96bd0-262">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="96bd0-263">Cümlelerdeki kullanım örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="96bd0-263">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="96bd0-264">".NET Core .NET bir çapraz platform uygulamasıdır."</span><span class="sxs-lookup"><span data-stu-id="96bd0-264">".NET Core is a cross-platform implementation of .NET."</span></span>
- <span data-ttu-id="96bd0-265">"PCL profilleri Microsoft platformlarını temsil ederken,.NET Standardı platforma agnostiktir."</span><span class="sxs-lookup"><span data-stu-id="96bd0-265">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="96bd0-266">.NET dokümantasyonu sık sık ".NET platformu"nu tüm uygulamaları içeren .NET veya .NET yığınının uygulanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-266">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="96bd0-267">Bu kullanımların her ikisi de birincil (işletim sistemi/donanım) anlamı ile karıştırılma eğilimindedir, bu nedenle bu kullanımları belgelerden ortadan kaldırmayı planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="96bd0-267">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="96bd0-268">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="96bd0-268">runtime</span></span>

<span data-ttu-id="96bd0-269">Yönetilen bir programın yürütme ortamı.</span><span class="sxs-lookup"><span data-stu-id="96bd0-269">The execution environment for a managed program.</span></span>

<span data-ttu-id="96bd0-270">İşletim sistemi çalışma zamanı ortamının bir parçasıdır, ancak .NET çalışma zamanının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-270">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="96bd0-271">Aşağıda .NET çalışma saatlerine ait bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="96bd0-271">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="96bd0-272">Ortak Dil Çalışma Zamanı (CLR)</span><span class="sxs-lookup"><span data-stu-id="96bd0-272">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="96bd0-273">Çekirdek Ortak Dil Çalışma Süresi (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="96bd0-273">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="96bd0-274">.NET Yerel (UWP için)</span><span class="sxs-lookup"><span data-stu-id="96bd0-274">.NET Native (for UWP)</span></span>
- <span data-ttu-id="96bd0-275">Mono çalışma süresi</span><span class="sxs-lookup"><span data-stu-id="96bd0-275">Mono runtime</span></span>

<span data-ttu-id="96bd0-276">.NET dokümantasyonu bazen .NET'in uygulanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-276">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="96bd0-277">Örneğin, aşağıdaki cümlelerde "çalışma zamanı" "uygulama" ile değiştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="96bd0-277">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="96bd0-278">"Çeşitli .NET çalışma saatleri .NET Standard'ın belirli sürümlerini uygular."</span><span class="sxs-lookup"><span data-stu-id="96bd0-278">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="96bd0-279">"Birden çok çalışma zamanında çalışması amaçlanan kitaplıklar bu çerçeveyi hedeflemelidir."</span><span class="sxs-lookup"><span data-stu-id="96bd0-279">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="96bd0-280">(.NET Standardına atıfta bulunarak)</span><span class="sxs-lookup"><span data-stu-id="96bd0-280">(referring to .NET Standard)</span></span>
- <span data-ttu-id="96bd0-281">"Çeşitli .NET çalışma saatleri .NET Standard'ın belirli sürümlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="96bd0-281">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="96bd0-282">…</span><span class="sxs-lookup"><span data-stu-id="96bd0-282">…</span></span> <span data-ttu-id="96bd0-283">Her .NET çalışma zamanı sürümü, desteklediği en yüksek .NET Standart sürümünün reklamını yapan ..."</span><span class="sxs-lookup"><span data-stu-id="96bd0-283">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="96bd0-284">Bu tutarsız kullanımı ortadan kaldırmayı planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="96bd0-284">We plan to eliminate this inconsistent usage.</span></span>

## <a name="stack"></a><span data-ttu-id="96bd0-285">yığın</span><span class="sxs-lookup"><span data-stu-id="96bd0-285">stack</span></span>

<span data-ttu-id="96bd0-286">Uygulamaları oluşturmak ve çalıştırmak için birlikte kullanılan programlama teknolojileri kümesi.</span><span class="sxs-lookup"><span data-stu-id="96bd0-286">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="96bd0-287">".NET yığını" .NET Standard ve tüm .NET uygulamalarını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="96bd0-287">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="96bd0-288">".NET yığını" deyimi .NET'in bir uygulamasına atıfta bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-288">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span>

## <a name="target-framework"></a><span data-ttu-id="96bd0-289">hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="96bd0-289">target framework</span></span>

<span data-ttu-id="96bd0-290">Bir .NET uygulamasının veya kitaplığın güvendiği API koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="96bd0-290">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="96bd0-291">Bir uygulama veya kitaplık, tüm .NET uygulamalarında standartlaştırılmış bir API kümesinin belirtimi olan .NET Standard'ın (örneğin, .NET Standart 2.0) bir sürümünü hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-291">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="96bd0-292">Bir uygulama veya kitaplık, belirli bir .NET uygulamasının bir sürümünü de hedefleyebilir ve bu durumda uygulamaya özgü API'lere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-292">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="96bd0-293">Örneğin, Xamarin.iOS hedefleyen bir uygulama Xamarin sağlanan iOS API sarmalayıcılarına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-293">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="96bd0-294">Bazı hedef çerçeveler için (örneğin, .NET Framework) kullanılabilir API'ler, bir .NET uygulamasının bir sisteme yüklediği derlemeler tarafından tanımlanır ve bu da uygulama çerçevesi API'lerini (örneğin, ASP.NET, WinForms) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-294">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="96bd0-295">Paket tabanlı hedef çerçeveler (.NET Standardı ve .NET Core gibi) için, çerçeve API'leri uygulama veya kitaplıkta yüklü paketler tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-295">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="96bd0-296">Bu durumda, hedef çerçeve örtülü olarak çerçeveyi oluşturan tüm paketlere başvuran bir meta paketi belirtir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-296">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="96bd0-297">Bkz. [Hedef Çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="96bd0-297">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="96bd0-298">Tfm</span><span class="sxs-lookup"><span data-stu-id="96bd0-298">TFM</span></span>

<span data-ttu-id="96bd0-299">Hedef çerçeve takma.</span><span class="sxs-lookup"><span data-stu-id="96bd0-299">Target framework moniker.</span></span>

<span data-ttu-id="96bd0-300">Bir .NET uygulamasının veya kitaplığın hedef çerçevesini belirtmek için standartlaştırılmış belirteç biçimi.</span><span class="sxs-lookup"><span data-stu-id="96bd0-300">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="96bd0-301">Hedef çerçeveler genellikle kısa bir adla başvurulmaktadır. `net462`</span><span class="sxs-lookup"><span data-stu-id="96bd0-301">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="96bd0-302">Uzun formlu TFM'ler (. NETFramework,Sürüm=4.6.2) vardır, ancak genellikle hedef çerçeve belirtmek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="96bd0-302">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="96bd0-303">Bkz. [Hedef Çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="96bd0-303">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="96bd0-304">UWP</span><span class="sxs-lookup"><span data-stu-id="96bd0-304">UWP</span></span>

<span data-ttu-id="96bd0-305">Evrensel Windows Platformu.</span><span class="sxs-lookup"><span data-stu-id="96bd0-305">Universal Windows Platform.</span></span>

<span data-ttu-id="96bd0-306">Nesnelerin İnterneti (IoT) için modern, dokunmatik özellikli Windows uygulamaları ve yazılımları oluşturmak için kullanılan .NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="96bd0-306">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="96bd0-307">Cd'ler, tabletler, telefonlar ve hatta Xbox dahil olmak üzere hedeflemek isteyebileceğiniz farklı türde aygıtları birletmek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-307">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="96bd0-308">UWP, merkezi bir uygulama deposu, yürütme ortamı (AppContainer) ve Win32 (WinRT) yerine kullanılacak bir dizi Windows API'si gibi birçok hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="96bd0-308">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="96bd0-309">Uygulamalar C++, C#, Visual Basic ve JavaScript ile yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="96bd0-309">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="96bd0-310">C# ve Visual Basic kullanırken .NET API'leri .NET Core tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="96bd0-310">When using C# and Visual Basic, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="96bd0-311">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96bd0-311">See also</span></span>

- [<span data-ttu-id="96bd0-312">.NET Rehberi</span><span class="sxs-lookup"><span data-stu-id="96bd0-312">.NET Guide</span></span>](index.md)
- [<span data-ttu-id="96bd0-313">.NET Çerçeve Rehberi</span><span class="sxs-lookup"><span data-stu-id="96bd0-313">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="96bd0-314">.NET Core</span><span class="sxs-lookup"><span data-stu-id="96bd0-314">.NET Core</span></span>](../core/index.md)
- [<span data-ttu-id="96bd0-315">ASP.NET Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="96bd0-315">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="96bd0-316">ASP.NET Çekirdek Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="96bd0-316">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
