---
title: .NET Sözlüğü
description: .NET belgelerinde kullanılan seçili terimlerin anlamını öğrenin.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: d8f16579ea4dcbc9260aac83e16d3fbd30db519c
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635578"
---
# <a name="net-glossary"></a><span data-ttu-id="a4c3c-103">.NET Sözlüğü</span><span class="sxs-lookup"><span data-stu-id="a4c3c-103">.NET Glossary</span></span>

<span data-ttu-id="a4c3c-104">Bu sözlüğün birincil amacı, .NET belgelerinde tanımları olmadan sık sık görünen seçili terimlerin ve kısaltmaların anlamlarını netleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="a4c3c-105">AOT</span><span class="sxs-lookup"><span data-stu-id="a4c3c-105">AOT</span></span>

<span data-ttu-id="a4c3c-106">Zaman compiler'ı.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="a4c3c-107">[JIT](#jit)benzer, bu derleyici de makine kodu [IL](#il) çevirir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="a4c3c-108">JIT derlemesinin aksine, AOT derlemesi uygulama yürütülmeden önce gerçekleşir ve genellikle farklı bir makinede gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="a4c3c-109">AOT takım zincirleri çalışma zamanında derlenmediği için derleme için harcanan zamanı en aza indirmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-109">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="a4c3c-110">Bu da optimizasyon için daha fazla zaman harcayabilecekleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="a4c3c-111">AOT bağlamı tüm uygulama olduğundan, AOT derleyicisi ayrıca tüm başvuruların takip edildiği ve tek bir çalıştırılabilir üretildiği anlamına gelen çapraz modül bağlantı ve tam program analizi ni gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="a4c3c-112">[Bkz. CoreRT](#corert) ve [.NET Native](#net-native).</span><span class="sxs-lookup"><span data-stu-id="a4c3c-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="aspnet"></a><span data-ttu-id="a4c3c-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a4c3c-113">ASP.NET</span></span>

<span data-ttu-id="a4c3c-114">.NET Framework ile yapılan orijinal ASP.NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="a4c3c-115">Bazen ASP.NET, ASP.NET Core dahil olmak üzere her iki ASP.NET uygulamaları ifade eden bir şemsiye terimdir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="a4c3c-116">Terimin herhangi bir durumda taşıdığı anlam bağlam tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="a4c3c-117">Her iki uygulama anlamına ASP.NET kullanmadığınızı açıkça belirtmek istediğinizde ASP.NET 4.x'e bakın.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-117">Refer to ASP.NET 4.x when you want to make it clear that you're not using ASP.NET to mean both implementations.</span></span>

<span data-ttu-id="a4c3c-118">[ASP.NET dokümantasyona](/aspnet/#pivot=aspnet)bakın.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="a4c3c-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a4c3c-119">ASP.NET Core</span></span>

<span data-ttu-id="a4c3c-120">.NET Core üzerine kurulu ASP.NET çapraz platform, yüksek performanslı, açık kaynak uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-120">A cross-platform, high-performance, open-source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="a4c3c-121">[Bkz. ASP.NET Çekirdek belgeleri.](/aspnet/#pivot=core)</span><span class="sxs-lookup"><span data-stu-id="a4c3c-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="a4c3c-122">derleme</span><span class="sxs-lookup"><span data-stu-id="a4c3c-122">assembly</span></span>

<span data-ttu-id="a4c3c-123">Uygulamalar veya diğer derlemeler tarafından çağrılabilen bir API koleksiyonu içerebilen *.dll*/*.exe* dosyası.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="a4c3c-124">Derleme, arabirimler, sınıflar, yapılar, sayısallamalar ve temsilciler gibi türleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="a4c3c-125">Projenin *çöp kutusu* klasöründeki derlemeler bazen *ikili*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="a4c3c-126">Ayrıca [kitaplık](#library)bakın.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-126">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="a4c3c-127">CLR</span><span class="sxs-lookup"><span data-stu-id="a4c3c-127">CLR</span></span>

<span data-ttu-id="a4c3c-128">Ortak Dil Çalışma Zamanı.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-128">Common Language Runtime.</span></span>

<span data-ttu-id="a4c3c-129">Tam anlamı içeriğe bağlıdır, ancak Ortak Dil Çalışma Süresi genellikle .NET Framework'ün çalışma zamanını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-129">The exact meaning depends on the context, but Common Language Runtime usually refers to the runtime of .NET Framework.</span></span> <span data-ttu-id="a4c3c-130">CLR bellek ayırma ve yönetimi işler.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-130">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="a4c3c-131">CLR aynı zamanda sadece uygulamaları yürütmekle kalmamış, aynı zamanda [bir JIT](#jit) derleyicisi kullanarak anında kod üreten ve derleyen sanal bir makinedir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-131">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span> <span data-ttu-id="a4c3c-132">Geçerli Microsoft CLR uygulaması yalnızca Windows'dur.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-132">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="a4c3c-133">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="a4c3c-133">CoreCLR</span></span>

<span data-ttu-id="a4c3c-134">.NET Çekirdek Ortak Dil Çalışma Zamanı.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-134">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="a4c3c-135">Bu CLR, CLR ile aynı kod tabanından oluşturulmuştür.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-135">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="a4c3c-136">Başlangıçta, CoreCLR Silverlight çalışma zamanı ve birden fazla platformda çalıştırmak için tasarlanmıştır, özellikle Windows ve OS X. CoreCLR şimdi .NET Core bir parçasıdır ve CLR basitleştirilmiş bir sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-136">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="a4c3c-137">Hala birçok Linux dağıtımı için destek de dahil olmak üzere, bir [çapraz platform](#cross-platform) çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-137">It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="a4c3c-138">CoreCLR aynı zamanda JIT ve kod yürütme yetenekleri ile sanal bir makinedir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-138">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="a4c3c-139">CoreFX</span><span class="sxs-lookup"><span data-stu-id="a4c3c-139">CoreFX</span></span>

<span data-ttu-id="a4c3c-140">.NET Çekirdek Taban Sınıf Kitaplığı (BCL)</span><span class="sxs-lookup"><span data-stu-id="a4c3c-140">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="a4c3c-141">Sistemi oluşturan bir dizi kitaplık. \* (ve sınırlı bir ölçüde\*Microsoft. ) ad boşlukları.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-141">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="a4c3c-142">BCL, ASP.NET Core gibi üst düzey uygulama çerçevelerinin temeline sahip olan genel bir amaç, alt düzey bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-142">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="a4c3c-143">.NET Core BCL'nin kaynak kodu [.NET Core çalışma zamanı deposunda](https://github.com/dotnet/runtime)bulunur.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-143">The source code of the .NET Core BCL is contained in the [.NET Core runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="a4c3c-144">Ancak, .NET Core API'lerinin çoğu .NET Framework'de de mevcuttur, böylece CoreFX'i .NET Framework BCL'nin çatalı olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-144">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="a4c3c-145">CoreRT</span><span class="sxs-lookup"><span data-stu-id="a4c3c-145">CoreRT</span></span>

<span data-ttu-id="a4c3c-146">.NET Çekirdek çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-146">.NET Core runtime.</span></span>

<span data-ttu-id="a4c3c-147">CLR /CoreCLR'nin aksine CoreRT sanal bir makine değildir, bu da [jit](#jit)içermediği için anında kod oluşturma ve çalıştırma olanaklarını içermediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-147">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="a4c3c-148">Ancak, [GC](#gc) ve çalışma zamanı türü tanımlama (RTTI) ve yansıma yeteneği içerir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-148">It does, however, include the [GC](#gc) and the ability for run-time type identification (RTTI) and reflection.</span></span> <span data-ttu-id="a4c3c-149">Ancak, yazı sistemi yansıma için meta veri gerekli olmayacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-149">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="a4c3c-150">Meta veri gerektirmemesi, gereksiz meta verileri birbirine bağlayabilen ve (daha da önemlisi) uygulamanın kullanmadığı kodu tanımlayabilen bir [AOT](#aot) araç zincirine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-150">Not requiring metadata enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="a4c3c-151">CoreRT geliştirilmekte.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-151">CoreRT is in development.</span></span>

<span data-ttu-id="a4c3c-152">Bkz. [Intro to .NET Native ve CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span><span class="sxs-lookup"><span data-stu-id="a4c3c-152">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="a4c3c-153">platformlar arası</span><span class="sxs-lookup"><span data-stu-id="a4c3c-153">cross-platform</span></span>

<span data-ttu-id="a4c3c-154">Linux, Windows ve iOS gibi birden çok farklı işletim sisteminde, her biri için özel olarak yeniden yazmak zorunda kalmadan kullanılabilen bir uygulama geliştirme ve yürütme olanağı.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-154">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows, and iOS, without having to rewrite specifically for each one.</span></span> <span data-ttu-id="a4c3c-155">Bu, kodun yeniden kullanılmasını ve farklı platformlardaki uygulamalar arasında tutarlılık sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-155">This enables code reuse and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="a4c3c-156">Ekosistem</span><span class="sxs-lookup"><span data-stu-id="a4c3c-156">ecosystem</span></span>

<span data-ttu-id="a4c3c-157">Belirli bir teknoloji için uygulamalar oluşturmak ve çalıştırmak için kullanılan tüm çalışma zamanı yazılımları, geliştirme araçları ve topluluk kaynakları.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-157">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="a4c3c-158">".NET ekosistemi" terimi, üçüncü taraf uygulamaları ve kitaplıkları dahil etmede ".NET yığını" gibi benzer terimlerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-158">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="a4c3c-159">Bir cümlede bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a4c3c-159">Here's an example in a sentence:</span></span>

- <span data-ttu-id="a4c3c-160">[".NET Standardının](#net-standard) arkasındaki motivasyon .NET ekosisteminde daha fazla tekdüzelik oluşturmaktır."</span><span class="sxs-lookup"><span data-stu-id="a4c3c-160">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span>

## <a name="framework"></a><span data-ttu-id="a4c3c-161">çerçeve</span><span class="sxs-lookup"><span data-stu-id="a4c3c-161">framework</span></span>

<span data-ttu-id="a4c3c-162">Genel olarak, belirli bir teknolojiye dayalı uygulamaların geliştirilmesini ve dağıtılmasını kolaylaştıran kapsamlı bir API koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-162">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="a4c3c-163">Bu genel anlamda, ASP.NET Çekirdek ve Windows Formları uygulama çerçevelerine örnektir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-163">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="a4c3c-164">Ayrıca [kitaplık](#library)bakın.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-164">See also [library](#library).</span></span>

<span data-ttu-id="a4c3c-165">"Çerçeve" sözcüğünün aşağıdaki terimlerde daha spesifik bir teknik anlamı vardır:</span><span class="sxs-lookup"><span data-stu-id="a4c3c-165">The word "framework" has a more specific technical meaning in the following terms:</span></span>

- [<span data-ttu-id="a4c3c-166">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a4c3c-166">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="a4c3c-167">hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="a4c3c-167">target framework</span></span>](#target-framework)
- [<span data-ttu-id="a4c3c-168">TFM (hedef çerçeve takma adıyla)</span><span class="sxs-lookup"><span data-stu-id="a4c3c-168">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="a4c3c-169">Varolan belgelerde "çerçeve" bazen [.NET'in uygulanmasını](#implementation-of-net)ifade eder.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-169">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="a4c3c-170">Örneğin, bir makale .NET Core'u bir çerçeve olarak adlandırabilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-170">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="a4c3c-171">Bu kafa karıştırıcı kullanımı belgelerden ortadan kaldırmayı planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-171">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="a4c3c-172">GC</span><span class="sxs-lookup"><span data-stu-id="a4c3c-172">GC</span></span>

<span data-ttu-id="a4c3c-173">Çöp toplayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-173">Garbage collector.</span></span>

<span data-ttu-id="a4c3c-174">Çöp toplayıcı otomatik bellek yönetiminin bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-174">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="a4c3c-175">GC, artık kullanılmayan nesneler tarafından işgal edilen belleği serbest eder.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-175">The GC frees memory occupied by objects that are no longer in use.</span></span>

<span data-ttu-id="a4c3c-176">[Bkz. Çöp Toplama](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="a4c3c-176">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="a4c3c-177">IL</span><span class="sxs-lookup"><span data-stu-id="a4c3c-177">IL</span></span>

<span data-ttu-id="a4c3c-178">Ara dil.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-178">Intermediate language.</span></span>

<span data-ttu-id="a4c3c-179">C# gibi üst düzey .NET dilleri, Ara Dil (IL) olarak adlandırılan donanım-agnostik yönerge kümesine kadar derlenir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-179">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="a4c3c-180">IL bazen MSIL (Microsoft IL) veya CIL (Ortak IL) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-180">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="a4c3c-181">JIT</span><span class="sxs-lookup"><span data-stu-id="a4c3c-181">JIT</span></span>

<span data-ttu-id="a4c3c-182">Tam zamanında derleyici.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-182">Just-in-time compiler.</span></span>

<span data-ttu-id="a4c3c-183">[AOT'ye](#aot)benzer şekilde, bu derleyici [IL'yi](#il) işlemcinin anladığı makine koduna çevirir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-183">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="a4c3c-184">AOT'nin aksine, JIT derlemesi isteğe bağlı olarak gerçekleşir ve kodun çalışması gereken makinede gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-184">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="a4c3c-185">JIT derlemesi uygulamanın yürütülmesi sırasında oluştuğundan derleme süresi çalışma süresinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-185">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="a4c3c-186">Bu nedenle, JIT derleyicileri, kodu en iyi duruma getirmek için harcanan zamanı, ortaya çıkan kodun oluşturabileceği tasarruflara göre dengelemek zorunda kalır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-186">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="a4c3c-187">Ama bir JIT gerçek donanım bilir ve farklı uygulamalar gemi sahip geliştiriciler ücretsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-187">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="a4c3c-188">.NET uygulaması</span><span class="sxs-lookup"><span data-stu-id="a4c3c-188">implementation of .NET</span></span>

<span data-ttu-id="a4c3c-189">.NET'in bir uygulaması şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="a4c3c-189">An implementation of .NET includes:</span></span>

- <span data-ttu-id="a4c3c-190">Bir veya daha fazla çalışma saatleri.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-190">One or more runtimes.</span></span> <span data-ttu-id="a4c3c-191">Örnekler: CLR, CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-191">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="a4c3c-192">.NET Standardının bir sürümünü uygulayan ve ek API'ler içerebilen bir sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-192">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="a4c3c-193">Örnekler: .NET Framework Base Sınıf Kitaplığı, .NET Çekirdek Taban Sınıf Kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-193">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="a4c3c-194">İsteğe bağlı olarak, bir veya daha fazla uygulama çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-194">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="a4c3c-195">Örnekler: ASP.NET, Windows Formları ve WPF .NET Çerçevesi'ne dahildir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-195">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="a4c3c-196">İsteğe bağlı olarak, geliştirme araçları.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-196">Optionally, development tools.</span></span> <span data-ttu-id="a4c3c-197">Bazı geliştirme araçları birden çok uygulama arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-197">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="a4c3c-198">.NET uygulamalarına örnekler:</span><span class="sxs-lookup"><span data-stu-id="a4c3c-198">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="a4c3c-199">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a4c3c-199">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="a4c3c-200">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a4c3c-200">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="a4c3c-201">Evrensel Windows Platformu (UWP)</span><span class="sxs-lookup"><span data-stu-id="a4c3c-201">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="a4c3c-202">kitaplık</span><span class="sxs-lookup"><span data-stu-id="a4c3c-202">library</span></span>

<span data-ttu-id="a4c3c-203">Uygulamalar veya diğer kitaplıklar tarafından çağrılabilen API koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-203">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="a4c3c-204">.NET kitaplığı bir veya daha fazla [derlemeden](#assembly)oluşur.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-204">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="a4c3c-205">Kitaplık ve [çerçeve](#framework) sözcükleri genellikle eş anlamlı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-205">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="a4c3c-206">metapaketi</span><span class="sxs-lookup"><span data-stu-id="a4c3c-206">metapackage</span></span>

<span data-ttu-id="a4c3c-207">Kendi kitaplığı olmayan ancak yalnızca bağımlılıkların bir listesi olan Bir NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-207">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="a4c3c-208">Dahil edilen paketler isteğe bağlı olarak bir hedef çerçeve için API'yi kurabilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-208">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="a4c3c-209">Bkz. [Paketler, Metapaketler ve Çerçeveler](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="a4c3c-209">See [Packages, Metapackages, and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="a4c3c-210">Mono</span><span class="sxs-lookup"><span data-stu-id="a4c3c-210">Mono</span></span>

<span data-ttu-id="a4c3c-211">Mono, çoğunlukla küçük bir çalışma süresi gerektiğinde kullanılan açık kaynak kodlu, [çapraz platform](#cross-platform) .NET uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-211">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="a4c3c-212">Android, Mac, iOS, tvOS ve watchOS'taki Xamarin uygulamalarına güç veren ve öncelikle küçük bir ayak izi gerektiren uygulamalara odaklanan çalışma zamanıdır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-212">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS, and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="a4c3c-213">Şu anda yayınlanan tüm .NET Standard sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-213">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="a4c3c-214">Tarihsel olarak, Mono .NET Framework'ün daha büyük API'sini uyguladı ve Unix'teki en popüler yeteneklerden bazılarını taklit etti.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-214">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="a4c3c-215">Bazen Unix'teki bu özelliklere dayanan .NET uygulamalarını çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-215">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="a4c3c-216">Mono genellikle tam zamanında derleyici ile kullanılır, ancak aynı zamanda iOS gibi platformlarda kullanılan tam bir statik derleyici (ileri-zaman derleme) özellikleri.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-216">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="a4c3c-217">Mono hakkında daha fazla bilgi edinmek için [Mono belgelerine](https://www.mono-project.com/docs/)bakın.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-217">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="a4c3c-218">.NET</span><span class="sxs-lookup"><span data-stu-id="a4c3c-218">.NET</span></span>

<span data-ttu-id="a4c3c-219">[.NET Standard](#net-standard) ve tüm [.NET uygulamaları](#implementation-of-net) ve iş yükleri için şemsiye terim.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-219">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="a4c3c-220">Her zaman tamamen büyük harfle, asla ".Net".</span><span class="sxs-lookup"><span data-stu-id="a4c3c-220">Always fully capitalized, never ".Net".</span></span>

<span data-ttu-id="a4c3c-221">[.NET kılavuzuna](index.yml) bakın</span><span class="sxs-lookup"><span data-stu-id="a4c3c-221">See the [.NET guide](index.yml)</span></span>

## <a name="net-core"></a><span data-ttu-id="a4c3c-222">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a4c3c-222">.NET Core</span></span>

<span data-ttu-id="a4c3c-223">.NET'in çapraz platform, yüksek performanslı, açık kaynak uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-223">A cross-platform, high-performance, open-source implementation of .NET.</span></span> <span data-ttu-id="a4c3c-224">Core Common Language Runtime (CoreCLR), Core AOT Runtime (CoreRT, geliştirme), Core Base Sınıf Kitaplığı ve Core SDK'yı içerir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-224">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="a4c3c-225">Bkz. [.NET Core](../core/index.yml).</span><span class="sxs-lookup"><span data-stu-id="a4c3c-225">See [.NET Core](../core/index.yml).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="a4c3c-226">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="a4c3c-226">.NET Core CLI</span></span>

<span data-ttu-id="a4c3c-227">.NET Core uygulamalarını geliştirmek için bir çapraz platform araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-227">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="a4c3c-228">Bkz. [.NET Çekirdek CLI](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="a4c3c-228">See [.NET Core CLI](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="a4c3c-229">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a4c3c-229">.NET Core SDK</span></span>

<span data-ttu-id="a4c3c-230">Geliştiricilerin .NET Core uygulamaları ve kitaplıkları oluşturmasına olanak tanıyan kitaplıklar ve araçlar kümesi.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-230">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="a4c3c-231">Uygulama oluşturmak için [.NET Core CLI'yi,](#net-core-cli) .NET Core kitaplıklarını ve uygulamaları oluşturmak ve çalıştırmak için çalışma süresini ve CLI komutlarını çalıştıran ve uygulamaları çalıştıran*dotnet(dotnet.exe)* içerir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-231">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="a4c3c-232">Bkz. [.NET Core SDK Genel Bakış](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="a4c3c-232">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="a4c3c-233">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a4c3c-233">.NET Framework</span></span>

<span data-ttu-id="a4c3c-234">.NET'in yalnızca Windows'da çalışan bir uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-234">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="a4c3c-235">Ortak Dil Çalışma Zamanı (CLR), Temel Sınıf Kitaplığı ve ASP.NET, Windows Forms ve WPF gibi uygulama çerçevesi kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-235">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="a4c3c-236">Bkz. [.NET Çerçeve Rehberi](../framework/index.yml).</span><span class="sxs-lookup"><span data-stu-id="a4c3c-236">See [.NET Framework Guide](../framework/index.yml).</span></span>

## <a name="net-native"></a><span data-ttu-id="a4c3c-237">.NET Yerel</span><span class="sxs-lookup"><span data-stu-id="a4c3c-237">.NET Native</span></span>

<span data-ttu-id="a4c3c-238">Tam zamanında (JIT) aksine, yerel kodu zamanından önce (AOT) üreten bir derleyici araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-238">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="a4c3c-239">Derleme, geliştiricinin makinesinde C++ derleyicisi ve bağlayıcısının çalışma şekline benzer şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-239">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="a4c3c-240">Kullanılmayan kodu kaldırır ve en iyi duruma çıkarmak için daha fazla zaman harcar.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-240">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="a4c3c-241">Kitaplıklardan kod ayıklar ve bunları yürütülebilir kodlarla birleştirir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-241">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="a4c3c-242">Sonuç, tüm uygulamayı temsil eden tek bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-242">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="a4c3c-243">UWP, .NET Native tarafından desteklenen ilk uygulama çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-243">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="a4c3c-244">Artık Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-244">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="a4c3c-245">Bkz. [Intro to .NET Native ve CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="a4c3c-245">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="a4c3c-246">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="a4c3c-246">.NET Standard</span></span>

<span data-ttu-id="a4c3c-247">Her .NET uygulamasında bulunan .NET API'lerinin resmi bir belirtimi.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-247">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="a4c3c-248">.NET Standart belirtimi bazen belgelerde kitaplık olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-248">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="a4c3c-249">Kitaplık API uygulamalarını içerdiğinden, yalnızca belirtimler (arabirimler) değil, .NET Standard'a "kitaplık" demek yanıltıcıdır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-249">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="a4c3c-250">.NET Standart metapaketinin adı dışında bu kullanımı belgelerden ortadan kaldırmayı`NETStandard.Library`planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-250">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="a4c3c-251">Bkz. [.NET Standart](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="a4c3c-251">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="a4c3c-252">Ngen</span><span class="sxs-lookup"><span data-stu-id="a4c3c-252">NGEN</span></span>

<span data-ttu-id="a4c3c-253">Yerli (görüntü) nesil.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-253">Native (image) generation.</span></span>

<span data-ttu-id="a4c3c-254">Bu teknolojiyi kalıcı bir JIT derleyicisi olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-254">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="a4c3c-255">Genellikle kodun yürütüldüğü makinede kod derler, ancak derleme genellikle yükleme zamanında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-255">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="a4c3c-256">Paket</span><span class="sxs-lookup"><span data-stu-id="a4c3c-256">package</span></span>

<span data-ttu-id="a4c3c-257">NuGet paketi &mdash; veya yalnızca &mdash; bir paket, yazar adı gibi ek meta verilerin yanı sıra aynı adı taşıyan bir veya daha fazla derlemeye sahip bir *.zip* dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-257">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="a4c3c-258">*.zip* dosyası *.nupkg* uzantısına sahiptir ve birden çok hedef çerçevesi ve sürümü yle kullanılmak üzere *.dll* dosyaları ve *.xml* dosyaları gibi varlıklar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-258">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="a4c3c-259">Bir uygulamaya veya kitaplıkta yüklendiğinde, uygulama veya kitaplık tarafından belirlenen hedef çerçeveye göre uygun varlıklar seçilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-259">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="a4c3c-260">Arabirimi tanımlayan varlıklar *ref* klasöründe, uygulamayı tanımlayan varlıklar *ise lib* klasöründedir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-260">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="a4c3c-261">platform</span><span class="sxs-lookup"><span data-stu-id="a4c3c-261">platform</span></span>

<span data-ttu-id="a4c3c-262">Windows, macOS, Linux, iOS ve Android gibi bir işletim sistemi ve çalıştırılaç donanımı.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-262">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="a4c3c-263">Cümlelerdeki kullanım örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a4c3c-263">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="a4c3c-264">".NET Core .NET bir çapraz platform uygulamasıdır."</span><span class="sxs-lookup"><span data-stu-id="a4c3c-264">".NET Core is a cross-platform implementation of .NET."</span></span>
- <span data-ttu-id="a4c3c-265">"PCL profilleri Microsoft platformlarını temsil ederken,.NET Standardı platforma agnostiktir."</span><span class="sxs-lookup"><span data-stu-id="a4c3c-265">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="a4c3c-266">.NET dokümantasyonu sık sık ".NET platformu"nu tüm uygulamaları içeren .NET veya .NET yığınının uygulanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-266">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="a4c3c-267">Bu kullanımların her ikisi de birincil (işletim sistemi/donanım) anlamı ile karıştırılma eğilimindedir, bu nedenle bu kullanımları belgelerden ortadan kaldırmayı planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-267">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="a4c3c-268">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="a4c3c-268">runtime</span></span>

<span data-ttu-id="a4c3c-269">Yönetilen bir programın yürütme ortamı.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-269">The execution environment for a managed program.</span></span>

<span data-ttu-id="a4c3c-270">İşletim sistemi çalışma zamanı ortamının bir parçasıdır, ancak .NET çalışma zamanının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-270">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="a4c3c-271">Aşağıda .NET çalışma saatlerine ait bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a4c3c-271">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="a4c3c-272">Ortak Dil Çalışma Zamanı (CLR)</span><span class="sxs-lookup"><span data-stu-id="a4c3c-272">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="a4c3c-273">Çekirdek Ortak Dil Çalışma Süresi (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="a4c3c-273">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="a4c3c-274">.NET Yerel (UWP için)</span><span class="sxs-lookup"><span data-stu-id="a4c3c-274">.NET Native (for UWP)</span></span>
- <span data-ttu-id="a4c3c-275">Mono çalışma süresi</span><span class="sxs-lookup"><span data-stu-id="a4c3c-275">Mono runtime</span></span>

<span data-ttu-id="a4c3c-276">.NET dokümantasyonu bazen .NET'in uygulanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-276">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="a4c3c-277">Örneğin, aşağıdaki cümlelerde "çalışma zamanı" "uygulama" ile değiştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="a4c3c-277">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="a4c3c-278">"Çeşitli .NET çalışma saatleri .NET Standard'ın belirli sürümlerini uygular."</span><span class="sxs-lookup"><span data-stu-id="a4c3c-278">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="a4c3c-279">"Birden çok çalışma zamanında çalışması amaçlanan kitaplıklar bu çerçeveyi hedeflemelidir."</span><span class="sxs-lookup"><span data-stu-id="a4c3c-279">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="a4c3c-280">(.NET Standardına atıfta bulunarak)</span><span class="sxs-lookup"><span data-stu-id="a4c3c-280">(referring to .NET Standard)</span></span>
- <span data-ttu-id="a4c3c-281">"Çeşitli .NET çalışma saatleri .NET Standard'ın belirli sürümlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-281">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="a4c3c-282">…</span><span class="sxs-lookup"><span data-stu-id="a4c3c-282">…</span></span> <span data-ttu-id="a4c3c-283">Her .NET çalışma zamanı sürümü, desteklediği en yüksek .NET Standart sürümünün reklamını yapan ..."</span><span class="sxs-lookup"><span data-stu-id="a4c3c-283">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="a4c3c-284">Bu tutarsız kullanımı ortadan kaldırmayı planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-284">We plan to eliminate this inconsistent usage.</span></span>

## <a name="stack"></a><span data-ttu-id="a4c3c-285">yığın</span><span class="sxs-lookup"><span data-stu-id="a4c3c-285">stack</span></span>

<span data-ttu-id="a4c3c-286">Uygulamaları oluşturmak ve çalıştırmak için birlikte kullanılan programlama teknolojileri kümesi.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-286">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="a4c3c-287">".NET yığını" .NET Standard ve tüm .NET uygulamalarını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-287">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="a4c3c-288">".NET yığını" deyimi .NET'in bir uygulamasına atıfta bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-288">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span>

## <a name="target-framework"></a><span data-ttu-id="a4c3c-289">hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="a4c3c-289">target framework</span></span>

<span data-ttu-id="a4c3c-290">Bir .NET uygulamasının veya kitaplığın güvendiği API koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-290">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="a4c3c-291">Bir uygulama veya kitaplık, tüm .NET uygulamalarında standartlaştırılmış bir API kümesinin belirtimi olan .NET Standard'ın (örneğin, .NET Standart 2.0) bir sürümünü hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-291">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="a4c3c-292">Bir uygulama veya kitaplık, belirli bir .NET uygulamasının bir sürümünü de hedefleyebilir ve bu durumda uygulamaya özgü API'lere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-292">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="a4c3c-293">Örneğin, Xamarin.iOS hedefleyen bir uygulama Xamarin sağlanan iOS API sarmalayıcılarına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-293">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="a4c3c-294">Bazı hedef çerçeveler için (örneğin, .NET Framework) kullanılabilir API'ler, bir .NET uygulamasının bir sisteme yüklediği derlemeler tarafından tanımlanır ve bu da uygulama çerçevesi API'lerini (örneğin, ASP.NET, WinForms) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-294">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="a4c3c-295">Paket tabanlı hedef çerçeveler (.NET Standardı ve .NET Core gibi) için, çerçeve API'leri uygulama veya kitaplıkta yüklü paketler tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-295">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="a4c3c-296">Bu durumda, hedef çerçeve örtülü olarak çerçeveyi oluşturan tüm paketlere başvuran bir meta paketi belirtir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-296">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="a4c3c-297">Bkz. [Hedef Çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a4c3c-297">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="a4c3c-298">Tfm</span><span class="sxs-lookup"><span data-stu-id="a4c3c-298">TFM</span></span>

<span data-ttu-id="a4c3c-299">Hedef çerçeve takma.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-299">Target framework moniker.</span></span>

<span data-ttu-id="a4c3c-300">Bir .NET uygulamasının veya kitaplığın hedef çerçevesini belirtmek için standartlaştırılmış belirteç biçimi.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-300">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="a4c3c-301">Hedef çerçeveler genellikle kısa bir adla başvurulmaktadır. `net462`</span><span class="sxs-lookup"><span data-stu-id="a4c3c-301">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="a4c3c-302">Uzun formlu TFM'ler (. NETFramework,Sürüm=4.6.2) vardır, ancak genellikle hedef çerçeve belirtmek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-302">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="a4c3c-303">Bkz. [Hedef Çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a4c3c-303">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="a4c3c-304">UWP</span><span class="sxs-lookup"><span data-stu-id="a4c3c-304">UWP</span></span>

<span data-ttu-id="a4c3c-305">Evrensel Windows Platformu.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-305">Universal Windows Platform.</span></span>

<span data-ttu-id="a4c3c-306">Nesnelerin İnterneti (IoT) için modern, dokunmatik özellikli Windows uygulamaları ve yazılımları oluşturmak için kullanılan .NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-306">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="a4c3c-307">Cd'ler, tabletler, telefonlar ve hatta Xbox dahil olmak üzere hedeflemek isteyebileceğiniz farklı türde aygıtları birletmek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-307">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="a4c3c-308">UWP, merkezi bir uygulama deposu, yürütme ortamı (AppContainer) ve Win32 (WinRT) yerine kullanılacak bir dizi Windows API'si gibi birçok hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-308">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="a4c3c-309">Uygulamalar C++, C#, Visual Basic ve JavaScript ile yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-309">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="a4c3c-310">C# ve Visual Basic kullanırken .NET API'leri .NET Core tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-310">When using C# and Visual Basic, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4c3c-311">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a4c3c-311">See also</span></span>

- [<span data-ttu-id="a4c3c-312">.NET Rehberi</span><span class="sxs-lookup"><span data-stu-id="a4c3c-312">.NET Guide</span></span>](index.yml)
- [<span data-ttu-id="a4c3c-313">.NET Çerçeve Rehberi</span><span class="sxs-lookup"><span data-stu-id="a4c3c-313">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="a4c3c-314">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a4c3c-314">.NET Core</span></span>](../core/index.yml)
- [<span data-ttu-id="a4c3c-315">ASP.NET Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a4c3c-315">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="a4c3c-316">ASP.NET Çekirdek Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a4c3c-316">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
