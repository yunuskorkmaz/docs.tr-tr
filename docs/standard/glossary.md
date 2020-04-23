---
title: .NET Sözlüğü
description: .NET belgelerinde kullanılan seçili terimlerin anlamını öğrenin.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: e7608ee7e68300d691df51aed923db0e8b518165
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102482"
---
# <a name="net-glossary"></a><span data-ttu-id="584f7-103">.NET Sözlüğü</span><span class="sxs-lookup"><span data-stu-id="584f7-103">.NET Glossary</span></span>

<span data-ttu-id="584f7-104">Bu sözlüğün birincil amacı, .NET belgelerinde tanımları olmadan sık sık görünen seçili terimlerin ve kısaltmaların anlamlarını netleştirmektir.</span><span class="sxs-lookup"><span data-stu-id="584f7-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="584f7-105">AOT</span><span class="sxs-lookup"><span data-stu-id="584f7-105">AOT</span></span>

<span data-ttu-id="584f7-106">Zaman compiler'ı.</span><span class="sxs-lookup"><span data-stu-id="584f7-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="584f7-107">[JIT](#jit)benzer, bu derleyici de makine kodu [IL](#il) çevirir.</span><span class="sxs-lookup"><span data-stu-id="584f7-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="584f7-108">JIT derlemesinin aksine, AOT derlemesi uygulama yürütülmeden önce gerçekleşir ve genellikle farklı bir makinede gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="584f7-109">AOT takım zincirleri çalışma zamanında derlenmediği için derleme için harcanan zamanı en aza indirmek zorunda değildir.</span><span class="sxs-lookup"><span data-stu-id="584f7-109">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="584f7-110">Bu da optimizasyon için daha fazla zaman harcayabilecekleri anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="584f7-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="584f7-111">AOT bağlamı tüm uygulama olduğundan, AOT derleyicisi ayrıca tüm başvuruların takip edildiği ve tek bir çalıştırılabilir üretildiği anlamına gelen çapraz modül bağlantı ve tam program analizi ni gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="584f7-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="584f7-112">[Bkz. CoreRT](#corert) ve [.NET Native](#net-native).</span><span class="sxs-lookup"><span data-stu-id="584f7-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="aspnet"></a><span data-ttu-id="584f7-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="584f7-113">ASP.NET</span></span>

<span data-ttu-id="584f7-114">.NET Framework ile yapılan orijinal ASP.NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="584f7-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="584f7-115">Bazen ASP.NET, ASP.NET Core dahil olmak üzere her iki ASP.NET uygulamaları ifade eden bir şemsiye terimdir.</span><span class="sxs-lookup"><span data-stu-id="584f7-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="584f7-116">Terimin herhangi bir durumda taşıdığı anlam bağlam tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="584f7-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="584f7-117">Her iki uygulama anlamına ASP.NET kullanmadığınızı açıkça belirtmek istediğinizde ASP.NET 4.x'e bakın.</span><span class="sxs-lookup"><span data-stu-id="584f7-117">Refer to ASP.NET 4.x when you want to make it clear that you're not using ASP.NET to mean both implementations.</span></span>

<span data-ttu-id="584f7-118">[ASP.NET dokümantasyona](/aspnet/#pivot=aspnet)bakın.</span><span class="sxs-lookup"><span data-stu-id="584f7-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="584f7-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="584f7-119">ASP.NET Core</span></span>

<span data-ttu-id="584f7-120">.NET Core üzerine kurulu ASP.NET çapraz platform, yüksek performanslı, açık kaynak uygulaması.</span><span class="sxs-lookup"><span data-stu-id="584f7-120">A cross-platform, high-performance, open-source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="584f7-121">[Bkz. ASP.NET Çekirdek belgeleri.](/aspnet/#pivot=core)</span><span class="sxs-lookup"><span data-stu-id="584f7-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="584f7-122">derleme</span><span class="sxs-lookup"><span data-stu-id="584f7-122">assembly</span></span>

<span data-ttu-id="584f7-123">Uygulamalar veya diğer derlemeler tarafından çağrılabilen bir API koleksiyonu içerebilen *.dll*/*.exe* dosyası.</span><span class="sxs-lookup"><span data-stu-id="584f7-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="584f7-124">Derleme, arabirimler, sınıflar, yapılar, sayısallamalar ve temsilciler gibi türleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="584f7-125">Projenin *çöp kutusu* klasöründeki derlemeler bazen *ikili*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="584f7-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="584f7-126">Ayrıca [kitaplık](#library)bakın.</span><span class="sxs-lookup"><span data-stu-id="584f7-126">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="584f7-127">CLR</span><span class="sxs-lookup"><span data-stu-id="584f7-127">CLR</span></span>

<span data-ttu-id="584f7-128">Ortak Dil Çalışma Zamanı.</span><span class="sxs-lookup"><span data-stu-id="584f7-128">Common Language Runtime.</span></span>

<span data-ttu-id="584f7-129">Tam anlamı içeriğe bağlıdır, ancak Ortak Dil Çalışma Süresi genellikle .NET Framework'ün çalışma zamanını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="584f7-129">The exact meaning depends on the context, but Common Language Runtime usually refers to the runtime of .NET Framework.</span></span> <span data-ttu-id="584f7-130">CLR bellek ayırma ve yönetimi işler.</span><span class="sxs-lookup"><span data-stu-id="584f7-130">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="584f7-131">CLR aynı zamanda sadece uygulamaları yürütmekle kalmamış, aynı zamanda [bir JIT](#jit) derleyicisi kullanarak anında kod üreten ve derleyen sanal bir makinedir.</span><span class="sxs-lookup"><span data-stu-id="584f7-131">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span> <span data-ttu-id="584f7-132">Geçerli Microsoft CLR uygulaması yalnızca Windows'dur.</span><span class="sxs-lookup"><span data-stu-id="584f7-132">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="584f7-133">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="584f7-133">CoreCLR</span></span>

<span data-ttu-id="584f7-134">.NET Çekirdek Ortak Dil Çalışma Zamanı.</span><span class="sxs-lookup"><span data-stu-id="584f7-134">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="584f7-135">Bu CLR, CLR ile aynı kod tabanından oluşturulmuştür.</span><span class="sxs-lookup"><span data-stu-id="584f7-135">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="584f7-136">Başlangıçta, CoreCLR Silverlight çalışma zamanı ve birden fazla platformda çalıştırmak için tasarlanmıştır, özellikle Windows ve OS X. CoreCLR şimdi .NET Core bir parçasıdır ve CLR basitleştirilmiş bir sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="584f7-136">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="584f7-137">Hala birçok Linux dağıtımı için destek de dahil olmak üzere, bir [çapraz platform](#cross-platform) çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="584f7-137">It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="584f7-138">CoreCLR aynı zamanda JIT ve kod yürütme yetenekleri ile sanal bir makinedir.</span><span class="sxs-lookup"><span data-stu-id="584f7-138">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="584f7-139">CoreFx</span><span class="sxs-lookup"><span data-stu-id="584f7-139">CoreFx</span></span>

<span data-ttu-id="584f7-140">.NET Çekirdek Taban Sınıf Kitaplığı (BCL)</span><span class="sxs-lookup"><span data-stu-id="584f7-140">.NET Core Base Class Library (BCL)</span></span>

> [!TIP]
> <span data-ttu-id="584f7-141">*Fx* *çerçeve*anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="584f7-141">*Fx* stands for *framework*.</span></span>

<span data-ttu-id="584f7-142">Sistemi oluşturan bir dizi kitaplık. \* (ve sınırlı bir ölçüde\*Microsoft. ) ad boşlukları.</span><span class="sxs-lookup"><span data-stu-id="584f7-142">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="584f7-143">BCL, ASP.NET Core gibi üst düzey uygulama çerçevelerinin temeline sahip olan genel bir amaç, alt düzey bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="584f7-143">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="584f7-144">.NET Core BCL'nin kaynak kodu [.NET Core çalışma zamanı deposunda](https://github.com/dotnet/runtime)bulunur.</span><span class="sxs-lookup"><span data-stu-id="584f7-144">The source code of the .NET Core BCL is contained in the [.NET Core runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="584f7-145">Ancak, .NET Core API'lerinin çoğu .NET Framework'de de mevcuttur, böylece CoreFX'i .NET Framework BCL'nin çatalı olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="584f7-145">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="584f7-146">CoreRT</span><span class="sxs-lookup"><span data-stu-id="584f7-146">CoreRT</span></span>

<span data-ttu-id="584f7-147">.NET Çekirdek çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="584f7-147">.NET Core runtime.</span></span>

<span data-ttu-id="584f7-148">CLR /CoreCLR'nin aksine CoreRT sanal bir makine değildir, bu da [jit](#jit)içermediği için anında kod oluşturma ve çalıştırma olanaklarını içermediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="584f7-148">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="584f7-149">Ancak, [GC](#gc) ve çalışma zamanı türü tanımlama (RTTI) ve yansıma yeteneği içerir.</span><span class="sxs-lookup"><span data-stu-id="584f7-149">It does, however, include the [GC](#gc) and the ability for run-time type identification (RTTI) and reflection.</span></span> <span data-ttu-id="584f7-150">Ancak, yazı sistemi yansıma için meta veri gerekli olmayacak şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="584f7-150">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="584f7-151">Meta veri gerektirmemesi, gereksiz meta verileri birbirine bağlayabilen ve (daha da önemlisi) uygulamanın kullanmadığı kodu tanımlayabilen bir [AOT](#aot) araç zincirine sahip olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="584f7-151">Not requiring metadata enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="584f7-152">CoreRT geliştirilmekte.</span><span class="sxs-lookup"><span data-stu-id="584f7-152">CoreRT is in development.</span></span>

<span data-ttu-id="584f7-153">Bkz. [Intro to .NET Native ve CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span><span class="sxs-lookup"><span data-stu-id="584f7-153">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="584f7-154">platformlar arası</span><span class="sxs-lookup"><span data-stu-id="584f7-154">cross-platform</span></span>

<span data-ttu-id="584f7-155">Linux, Windows ve iOS gibi birden çok farklı işletim sisteminde, her biri için özel olarak yeniden yazmak zorunda kalmadan kullanılabilen bir uygulama geliştirme ve yürütme olanağı.</span><span class="sxs-lookup"><span data-stu-id="584f7-155">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows, and iOS, without having to rewrite specifically for each one.</span></span> <span data-ttu-id="584f7-156">Bu, kodun yeniden kullanılmasını ve farklı platformlardaki uygulamalar arasında tutarlılık sağlar.</span><span class="sxs-lookup"><span data-stu-id="584f7-156">This enables code reuse and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="584f7-157">Ekosistem</span><span class="sxs-lookup"><span data-stu-id="584f7-157">ecosystem</span></span>

<span data-ttu-id="584f7-158">Belirli bir teknoloji için uygulamalar oluşturmak ve çalıştırmak için kullanılan tüm çalışma zamanı yazılımları, geliştirme araçları ve topluluk kaynakları.</span><span class="sxs-lookup"><span data-stu-id="584f7-158">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="584f7-159">".NET ekosistemi" terimi, üçüncü taraf uygulamaları ve kitaplıkları dahil etmede ".NET yığını" gibi benzer terimlerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="584f7-159">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="584f7-160">Bir cümlede bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="584f7-160">Here's an example in a sentence:</span></span>

- <span data-ttu-id="584f7-161">[".NET Standardının](#net-standard) arkasındaki motivasyon .NET ekosisteminde daha fazla tekdüzelik oluşturmaktır."</span><span class="sxs-lookup"><span data-stu-id="584f7-161">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span>

## <a name="framework"></a><span data-ttu-id="584f7-162">çerçeve</span><span class="sxs-lookup"><span data-stu-id="584f7-162">framework</span></span>

<span data-ttu-id="584f7-163">Genel olarak, belirli bir teknolojiye dayalı uygulamaların geliştirilmesini ve dağıtılmasını kolaylaştıran kapsamlı bir API koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="584f7-163">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="584f7-164">Bu genel anlamda, ASP.NET Çekirdek ve Windows Formları uygulama çerçevelerine örnektir.</span><span class="sxs-lookup"><span data-stu-id="584f7-164">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="584f7-165">Ayrıca [kitaplık](#library)bakın.</span><span class="sxs-lookup"><span data-stu-id="584f7-165">See also [library](#library).</span></span>

<span data-ttu-id="584f7-166">"Çerçeve" sözcüğünün aşağıdaki terimlerde daha spesifik bir teknik anlamı vardır:</span><span class="sxs-lookup"><span data-stu-id="584f7-166">The word "framework" has a more specific technical meaning in the following terms:</span></span>

- [<span data-ttu-id="584f7-167">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="584f7-167">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="584f7-168">hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="584f7-168">target framework</span></span>](#target-framework)
- [<span data-ttu-id="584f7-169">TFM (hedef çerçeve takma adıyla)</span><span class="sxs-lookup"><span data-stu-id="584f7-169">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="584f7-170">Varolan belgelerde "çerçeve" bazen [.NET'in uygulanmasını](#implementation-of-net)ifade eder.</span><span class="sxs-lookup"><span data-stu-id="584f7-170">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="584f7-171">Örneğin, bir makale .NET Core'u bir çerçeve olarak adlandırabilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-171">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="584f7-172">Bu kafa karıştırıcı kullanımı belgelerden ortadan kaldırmayı planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="584f7-172">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="584f7-173">GC</span><span class="sxs-lookup"><span data-stu-id="584f7-173">GC</span></span>

<span data-ttu-id="584f7-174">Çöp toplayıcısı.</span><span class="sxs-lookup"><span data-stu-id="584f7-174">Garbage collector.</span></span>

<span data-ttu-id="584f7-175">Çöp toplayıcı otomatik bellek yönetiminin bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="584f7-175">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="584f7-176">GC, artık kullanılmayan nesneler tarafından işgal edilen belleği serbest eder.</span><span class="sxs-lookup"><span data-stu-id="584f7-176">The GC frees memory occupied by objects that are no longer in use.</span></span>

<span data-ttu-id="584f7-177">[Bkz. Çöp Toplama](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="584f7-177">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="584f7-178">IL</span><span class="sxs-lookup"><span data-stu-id="584f7-178">IL</span></span>

<span data-ttu-id="584f7-179">Ara dil.</span><span class="sxs-lookup"><span data-stu-id="584f7-179">Intermediate language.</span></span>

<span data-ttu-id="584f7-180">C# gibi üst düzey .NET dilleri, Ara Dil (IL) olarak adlandırılan donanım-agnostik yönerge kümesine kadar derlenir.</span><span class="sxs-lookup"><span data-stu-id="584f7-180">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="584f7-181">IL bazen MSIL (Microsoft IL) veya CIL (Ortak IL) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="584f7-181">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="584f7-182">JIT</span><span class="sxs-lookup"><span data-stu-id="584f7-182">JIT</span></span>

<span data-ttu-id="584f7-183">Tam zamanında derleyici.</span><span class="sxs-lookup"><span data-stu-id="584f7-183">Just-in-time compiler.</span></span>

<span data-ttu-id="584f7-184">[AOT'ye](#aot)benzer şekilde, bu derleyici [IL'yi](#il) işlemcinin anladığı makine koduna çevirir.</span><span class="sxs-lookup"><span data-stu-id="584f7-184">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="584f7-185">AOT'nin aksine, JIT derlemesi isteğe bağlı olarak gerçekleşir ve kodun çalışması gereken makinede gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-185">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="584f7-186">JIT derlemesi uygulamanın yürütülmesi sırasında oluştuğundan derleme süresi çalışma süresinin bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="584f7-186">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="584f7-187">Bu nedenle, JIT derleyicileri, kodu en iyi duruma getirmek için harcanan zamanı, ortaya çıkan kodun oluşturabileceği tasarruflara göre dengelemek zorunda kalır.</span><span class="sxs-lookup"><span data-stu-id="584f7-187">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="584f7-188">Ama bir JIT gerçek donanım bilir ve farklı uygulamalar gemi sahip geliştiriciler ücretsiz olabilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-188">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="584f7-189">.NET uygulaması</span><span class="sxs-lookup"><span data-stu-id="584f7-189">implementation of .NET</span></span>

<span data-ttu-id="584f7-190">.NET'in bir uygulaması şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="584f7-190">An implementation of .NET includes:</span></span>

- <span data-ttu-id="584f7-191">Bir veya daha fazla çalışma saatleri.</span><span class="sxs-lookup"><span data-stu-id="584f7-191">One or more runtimes.</span></span> <span data-ttu-id="584f7-192">Örnekler: CLR, CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="584f7-192">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="584f7-193">.NET Standardının bir sürümünü uygulayan ve ek API'ler içerebilen bir sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="584f7-193">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="584f7-194">Örnekler: .NET Framework Base Sınıf Kitaplığı, .NET Çekirdek Taban Sınıf Kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="584f7-194">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="584f7-195">İsteğe bağlı olarak, bir veya daha fazla uygulama çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="584f7-195">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="584f7-196">Örnekler: ASP.NET, Windows Formları ve WPF .NET Çerçevesi'ne dahildir.</span><span class="sxs-lookup"><span data-stu-id="584f7-196">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="584f7-197">İsteğe bağlı olarak, geliştirme araçları.</span><span class="sxs-lookup"><span data-stu-id="584f7-197">Optionally, development tools.</span></span> <span data-ttu-id="584f7-198">Bazı geliştirme araçları birden çok uygulama arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="584f7-198">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="584f7-199">.NET uygulamalarına örnekler:</span><span class="sxs-lookup"><span data-stu-id="584f7-199">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="584f7-200">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="584f7-200">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="584f7-201">.NET Core</span><span class="sxs-lookup"><span data-stu-id="584f7-201">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="584f7-202">Evrensel Windows Platformu (UWP)</span><span class="sxs-lookup"><span data-stu-id="584f7-202">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="584f7-203">kitaplık</span><span class="sxs-lookup"><span data-stu-id="584f7-203">library</span></span>

<span data-ttu-id="584f7-204">Uygulamalar veya diğer kitaplıklar tarafından çağrılabilen API koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="584f7-204">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="584f7-205">.NET kitaplığı bir veya daha fazla [derlemeden](#assembly)oluşur.</span><span class="sxs-lookup"><span data-stu-id="584f7-205">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="584f7-206">Kitaplık ve [çerçeve](#framework) sözcükleri genellikle eş anlamlı olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="584f7-206">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="584f7-207">metapaketi</span><span class="sxs-lookup"><span data-stu-id="584f7-207">metapackage</span></span>

<span data-ttu-id="584f7-208">Kendi kitaplığı olmayan ancak yalnızca bağımlılıkların bir listesi olan Bir NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="584f7-208">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="584f7-209">Dahil edilen paketler isteğe bağlı olarak bir hedef çerçeve için API'yi kurabilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-209">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="584f7-210">Bkz. [Paketler, Metapaketler ve Çerçeveler](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="584f7-210">See [Packages, Metapackages, and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="584f7-211">Mono</span><span class="sxs-lookup"><span data-stu-id="584f7-211">Mono</span></span>

<span data-ttu-id="584f7-212">Mono, çoğunlukla küçük bir çalışma süresi gerektiğinde kullanılan açık kaynak kodlu, [çapraz platform](#cross-platform) .NET uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="584f7-212">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="584f7-213">Android, Mac, iOS, tvOS ve watchOS'taki Xamarin uygulamalarına güç veren ve öncelikle küçük bir ayak izi gerektiren uygulamalara odaklanan çalışma zamanıdır.</span><span class="sxs-lookup"><span data-stu-id="584f7-213">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS, and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="584f7-214">Şu anda yayınlanan tüm .NET Standard sürümlerini destekler.</span><span class="sxs-lookup"><span data-stu-id="584f7-214">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="584f7-215">Tarihsel olarak, Mono .NET Framework'ün daha büyük API'sini uyguladı ve Unix'teki en popüler yeteneklerden bazılarını taklit etti.</span><span class="sxs-lookup"><span data-stu-id="584f7-215">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="584f7-216">Bazen Unix'teki bu özelliklere dayanan .NET uygulamalarını çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="584f7-216">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="584f7-217">Mono genellikle tam zamanında derleyici ile kullanılır, ancak aynı zamanda iOS gibi platformlarda kullanılan tam bir statik derleyici (ileri-zaman derleme) özellikleri.</span><span class="sxs-lookup"><span data-stu-id="584f7-217">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="584f7-218">Mono hakkında daha fazla bilgi edinmek için [Mono belgelerine](https://www.mono-project.com/docs/)bakın.</span><span class="sxs-lookup"><span data-stu-id="584f7-218">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="584f7-219">.NET</span><span class="sxs-lookup"><span data-stu-id="584f7-219">.NET</span></span>

<span data-ttu-id="584f7-220">[.NET Standard](#net-standard) ve tüm [.NET uygulamaları](#implementation-of-net) ve iş yükleri için şemsiye terim.</span><span class="sxs-lookup"><span data-stu-id="584f7-220">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="584f7-221">Her zaman tamamen büyük harfle, asla ".Net".</span><span class="sxs-lookup"><span data-stu-id="584f7-221">Always fully capitalized, never ".Net".</span></span>

<span data-ttu-id="584f7-222">[.NET kılavuzuna](index.yml) bakın</span><span class="sxs-lookup"><span data-stu-id="584f7-222">See the [.NET guide](index.yml)</span></span>

## <a name="net-core"></a><span data-ttu-id="584f7-223">.NET Core</span><span class="sxs-lookup"><span data-stu-id="584f7-223">.NET Core</span></span>

<span data-ttu-id="584f7-224">.NET'in çapraz platform, yüksek performanslı, açık kaynak uygulaması.</span><span class="sxs-lookup"><span data-stu-id="584f7-224">A cross-platform, high-performance, open-source implementation of .NET.</span></span> <span data-ttu-id="584f7-225">Core Common Language Runtime (CoreCLR), Core AOT Runtime (CoreRT, geliştirme), Core Base Sınıf Kitaplığı ve Core SDK'yı içerir.</span><span class="sxs-lookup"><span data-stu-id="584f7-225">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="584f7-226">Bkz. [.NET Core](../core/index.yml).</span><span class="sxs-lookup"><span data-stu-id="584f7-226">See [.NET Core](../core/index.yml).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="584f7-227">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="584f7-227">.NET Core CLI</span></span>

<span data-ttu-id="584f7-228">.NET Core uygulamalarını geliştirmek için bir çapraz platform araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="584f7-228">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="584f7-229">Bkz. [.NET Çekirdek CLI](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="584f7-229">See [.NET Core CLI](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="584f7-230">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="584f7-230">.NET Core SDK</span></span>

<span data-ttu-id="584f7-231">Geliştiricilerin .NET Core uygulamaları ve kitaplıkları oluşturmasına olanak tanıyan kitaplıklar ve araçlar kümesi.</span><span class="sxs-lookup"><span data-stu-id="584f7-231">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="584f7-232">Uygulama oluşturmak için [.NET Core CLI'yi,](#net-core-cli) .NET Core kitaplıklarını ve uygulamaları oluşturmak ve çalıştırmak için çalışma süresini ve CLI komutlarını çalıştıran ve uygulamaları çalıştıran*dotnet(dotnet.exe)* içerir.</span><span class="sxs-lookup"><span data-stu-id="584f7-232">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="584f7-233">Bkz. [.NET Core SDK Genel Bakış](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="584f7-233">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="584f7-234">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="584f7-234">.NET Framework</span></span>

<span data-ttu-id="584f7-235">.NET'in yalnızca Windows'da çalışan bir uygulaması.</span><span class="sxs-lookup"><span data-stu-id="584f7-235">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="584f7-236">Ortak Dil Çalışma Zamanı (CLR), Temel Sınıf Kitaplığı ve ASP.NET, Windows Forms ve WPF gibi uygulama çerçevesi kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="584f7-236">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="584f7-237">Bkz. [.NET Çerçeve Rehberi](../framework/index.yml).</span><span class="sxs-lookup"><span data-stu-id="584f7-237">See [.NET Framework Guide](../framework/index.yml).</span></span>

## <a name="net-native"></a><span data-ttu-id="584f7-238">.NET Yerel</span><span class="sxs-lookup"><span data-stu-id="584f7-238">.NET Native</span></span>

<span data-ttu-id="584f7-239">Tam zamanında (JIT) aksine, yerel kodu zamanından önce (AOT) üreten bir derleyici araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="584f7-239">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="584f7-240">Derleme, geliştiricinin makinesinde C++ derleyicisi ve bağlayıcısının çalışma şekline benzer şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="584f7-240">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="584f7-241">Kullanılmayan kodu kaldırır ve en iyi duruma çıkarmak için daha fazla zaman harcar.</span><span class="sxs-lookup"><span data-stu-id="584f7-241">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="584f7-242">Kitaplıklardan kod ayıklar ve bunları yürütülebilir kodlarla birleştirir.</span><span class="sxs-lookup"><span data-stu-id="584f7-242">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="584f7-243">Sonuç, tüm uygulamayı temsil eden tek bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="584f7-243">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="584f7-244">UWP, .NET Native tarafından desteklenen ilk uygulama çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="584f7-244">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="584f7-245">Artık Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="584f7-245">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="584f7-246">Bkz. [Intro to .NET Native ve CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="584f7-246">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="584f7-247">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="584f7-247">.NET Standard</span></span>

<span data-ttu-id="584f7-248">Her .NET uygulamasında bulunan .NET API'lerinin resmi bir belirtimi.</span><span class="sxs-lookup"><span data-stu-id="584f7-248">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="584f7-249">.NET Standart belirtimi bazen belgelerde kitaplık olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="584f7-249">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="584f7-250">Kitaplık API uygulamalarını içerdiğinden, yalnızca belirtimler (arabirimler) değil, .NET Standard'a "kitaplık" demek yanıltıcıdır.</span><span class="sxs-lookup"><span data-stu-id="584f7-250">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="584f7-251">.NET Standart metapaketinin adı dışında bu kullanımı belgelerden ortadan kaldırmayı`NETStandard.Library`planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="584f7-251">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="584f7-252">Bkz. [.NET Standart](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="584f7-252">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="584f7-253">Ngen</span><span class="sxs-lookup"><span data-stu-id="584f7-253">NGEN</span></span>

<span data-ttu-id="584f7-254">Yerli (görüntü) nesil.</span><span class="sxs-lookup"><span data-stu-id="584f7-254">Native (image) generation.</span></span>

<span data-ttu-id="584f7-255">Bu teknolojiyi kalıcı bir JIT derleyicisi olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="584f7-255">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="584f7-256">Genellikle kodun yürütüldüğü makinede kod derler, ancak derleme genellikle yükleme zamanında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="584f7-256">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="584f7-257">Paket</span><span class="sxs-lookup"><span data-stu-id="584f7-257">package</span></span>

<span data-ttu-id="584f7-258">NuGet paketi &mdash; veya yalnızca &mdash; bir paket, yazar adı gibi ek meta verilerin yanı sıra aynı adı taşıyan bir veya daha fazla derlemeye sahip bir *.zip* dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="584f7-258">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="584f7-259">*.zip* dosyası *.nupkg* uzantısına sahiptir ve birden çok hedef çerçevesi ve sürümü yle kullanılmak üzere *.dll* dosyaları ve *.xml* dosyaları gibi varlıklar içerebilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-259">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="584f7-260">Bir uygulamaya veya kitaplıkta yüklendiğinde, uygulama veya kitaplık tarafından belirlenen hedef çerçeveye göre uygun varlıklar seçilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-260">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="584f7-261">Arabirimi tanımlayan varlıklar *ref* klasöründe, uygulamayı tanımlayan varlıklar *ise lib* klasöründedir.</span><span class="sxs-lookup"><span data-stu-id="584f7-261">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="584f7-262">platform</span><span class="sxs-lookup"><span data-stu-id="584f7-262">platform</span></span>

<span data-ttu-id="584f7-263">Windows, macOS, Linux, iOS ve Android gibi bir işletim sistemi ve çalıştırılaç donanımı.</span><span class="sxs-lookup"><span data-stu-id="584f7-263">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="584f7-264">Cümlelerdeki kullanım örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="584f7-264">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="584f7-265">".NET Core .NET bir çapraz platform uygulamasıdır."</span><span class="sxs-lookup"><span data-stu-id="584f7-265">".NET Core is a cross-platform implementation of .NET."</span></span>
- <span data-ttu-id="584f7-266">"PCL profilleri Microsoft platformlarını temsil ederken,.NET Standardı platforma agnostiktir."</span><span class="sxs-lookup"><span data-stu-id="584f7-266">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="584f7-267">.NET dokümantasyonu sık sık ".NET platformu"nu tüm uygulamaları içeren .NET veya .NET yığınının uygulanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="584f7-267">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="584f7-268">Bu kullanımların her ikisi de birincil (işletim sistemi/donanım) anlamı ile karıştırılma eğilimindedir, bu nedenle bu kullanımları belgelerden ortadan kaldırmayı planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="584f7-268">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="584f7-269">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="584f7-269">runtime</span></span>

<span data-ttu-id="584f7-270">Yönetilen bir programın yürütme ortamı.</span><span class="sxs-lookup"><span data-stu-id="584f7-270">The execution environment for a managed program.</span></span>

<span data-ttu-id="584f7-271">İşletim sistemi çalışma zamanı ortamının bir parçasıdır, ancak .NET çalışma zamanının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="584f7-271">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="584f7-272">Aşağıda .NET çalışma saatlerine ait bazı örnekler verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="584f7-272">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="584f7-273">Ortak Dil Çalışma Zamanı (CLR)</span><span class="sxs-lookup"><span data-stu-id="584f7-273">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="584f7-274">Çekirdek Ortak Dil Çalışma Süresi (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="584f7-274">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="584f7-275">.NET Yerel (UWP için)</span><span class="sxs-lookup"><span data-stu-id="584f7-275">.NET Native (for UWP)</span></span>
- <span data-ttu-id="584f7-276">Mono çalışma süresi</span><span class="sxs-lookup"><span data-stu-id="584f7-276">Mono runtime</span></span>

<span data-ttu-id="584f7-277">.NET dokümantasyonu bazen .NET'in uygulanması anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="584f7-277">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="584f7-278">Örneğin, aşağıdaki cümlelerde "çalışma zamanı" "uygulama" ile değiştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="584f7-278">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="584f7-279">"Çeşitli .NET çalışma saatleri .NET Standard'ın belirli sürümlerini uygular."</span><span class="sxs-lookup"><span data-stu-id="584f7-279">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="584f7-280">"Birden çok çalışma zamanında çalışması amaçlanan kitaplıklar bu çerçeveyi hedeflemelidir."</span><span class="sxs-lookup"><span data-stu-id="584f7-280">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="584f7-281">(.NET Standardına atıfta bulunarak)</span><span class="sxs-lookup"><span data-stu-id="584f7-281">(referring to .NET Standard)</span></span>
- <span data-ttu-id="584f7-282">"Çeşitli .NET çalışma saatleri .NET Standard'ın belirli sürümlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="584f7-282">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="584f7-283">…</span><span class="sxs-lookup"><span data-stu-id="584f7-283">…</span></span> <span data-ttu-id="584f7-284">Her .NET çalışma zamanı sürümü, desteklediği en yüksek .NET Standart sürümünün reklamını yapan ..."</span><span class="sxs-lookup"><span data-stu-id="584f7-284">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="584f7-285">Bu tutarsız kullanımı ortadan kaldırmayı planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="584f7-285">We plan to eliminate this inconsistent usage.</span></span>

## <a name="stack"></a><span data-ttu-id="584f7-286">yığın</span><span class="sxs-lookup"><span data-stu-id="584f7-286">stack</span></span>

<span data-ttu-id="584f7-287">Uygulamaları oluşturmak ve çalıştırmak için birlikte kullanılan programlama teknolojileri kümesi.</span><span class="sxs-lookup"><span data-stu-id="584f7-287">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="584f7-288">".NET yığını" .NET Standard ve tüm .NET uygulamalarını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="584f7-288">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="584f7-289">".NET yığını" deyimi .NET'in bir uygulamasına atıfta bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-289">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span>

## <a name="target-framework"></a><span data-ttu-id="584f7-290">hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="584f7-290">target framework</span></span>

<span data-ttu-id="584f7-291">Bir .NET uygulamasının veya kitaplığın güvendiği API koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="584f7-291">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="584f7-292">Bir uygulama veya kitaplık, tüm .NET uygulamalarında standartlaştırılmış bir API kümesinin belirtimi olan .NET Standard'ın (örneğin, .NET Standart 2.0) bir sürümünü hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-292">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="584f7-293">Bir uygulama veya kitaplık, belirli bir .NET uygulamasının bir sürümünü de hedefleyebilir ve bu durumda uygulamaya özgü API'lere erişebilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-293">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="584f7-294">Örneğin, Xamarin.iOS hedefleyen bir uygulama Xamarin sağlanan iOS API sarmalayıcılarına erişebilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-294">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="584f7-295">Bazı hedef çerçeveler için (örneğin, .NET Framework) kullanılabilir API'ler, bir .NET uygulamasının bir sisteme yüklediği derlemeler tarafından tanımlanır ve bu da uygulama çerçevesi API'lerini (örneğin, ASP.NET, WinForms) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-295">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="584f7-296">Paket tabanlı hedef çerçeveler (.NET Standardı ve .NET Core gibi) için, çerçeve API'leri uygulama veya kitaplıkta yüklü paketler tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="584f7-296">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="584f7-297">Bu durumda, hedef çerçeve örtülü olarak çerçeveyi oluşturan tüm paketlere başvuran bir meta paketi belirtir.</span><span class="sxs-lookup"><span data-stu-id="584f7-297">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="584f7-298">Bkz. [Hedef Çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="584f7-298">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="584f7-299">Tfm</span><span class="sxs-lookup"><span data-stu-id="584f7-299">TFM</span></span>

<span data-ttu-id="584f7-300">Hedef çerçeve takma.</span><span class="sxs-lookup"><span data-stu-id="584f7-300">Target framework moniker.</span></span>

<span data-ttu-id="584f7-301">Bir .NET uygulamasının veya kitaplığın hedef çerçevesini belirtmek için standartlaştırılmış belirteç biçimi.</span><span class="sxs-lookup"><span data-stu-id="584f7-301">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="584f7-302">Hedef çerçeveler genellikle kısa bir adla başvurulmaktadır. `net462`</span><span class="sxs-lookup"><span data-stu-id="584f7-302">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="584f7-303">Uzun formlu TFM'ler (. NETFramework,Sürüm=4.6.2) vardır, ancak genellikle hedef çerçeve belirtmek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="584f7-303">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="584f7-304">Bkz. [Hedef Çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="584f7-304">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="584f7-305">UWP</span><span class="sxs-lookup"><span data-stu-id="584f7-305">UWP</span></span>

<span data-ttu-id="584f7-306">Evrensel Windows Platformu.</span><span class="sxs-lookup"><span data-stu-id="584f7-306">Universal Windows Platform.</span></span>

<span data-ttu-id="584f7-307">Nesnelerin İnterneti (IoT) için modern, dokunmatik özellikli Windows uygulamaları ve yazılımları oluşturmak için kullanılan .NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="584f7-307">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="584f7-308">Cd'ler, tabletler, telefonlar ve hatta Xbox dahil olmak üzere hedeflemek isteyebileceğiniz farklı türde aygıtları birletmek üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="584f7-308">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="584f7-309">UWP, merkezi bir uygulama deposu, yürütme ortamı (AppContainer) ve Win32 (WinRT) yerine kullanılacak bir dizi Windows API'si gibi birçok hizmet sağlar.</span><span class="sxs-lookup"><span data-stu-id="584f7-309">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="584f7-310">Uygulamalar C++, C#, Visual Basic ve JavaScript ile yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="584f7-310">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="584f7-311">C# ve Visual Basic kullanırken .NET API'leri .NET Core tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="584f7-311">When using C# and Visual Basic, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="584f7-312">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="584f7-312">See also</span></span>

- [<span data-ttu-id="584f7-313">.NET Rehberi</span><span class="sxs-lookup"><span data-stu-id="584f7-313">.NET Guide</span></span>](index.yml)
- [<span data-ttu-id="584f7-314">.NET Çerçeve Rehberi</span><span class="sxs-lookup"><span data-stu-id="584f7-314">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="584f7-315">.NET Core</span><span class="sxs-lookup"><span data-stu-id="584f7-315">.NET Core</span></span>](../core/index.yml)
- [<span data-ttu-id="584f7-316">ASP.NET Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="584f7-316">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="584f7-317">ASP.NET Çekirdek Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="584f7-317">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
