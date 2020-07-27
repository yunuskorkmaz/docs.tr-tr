---
title: .NET Sözlüğü
description: .NET belgelerinde kullanılan seçili koşulların anlamını öğrenin.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: 529b1d9142ddf7982a6712c355c10666f0414d73
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163113"
---
# <a name="net-glossary"></a><span data-ttu-id="a13ec-103">.NET Sözlüğü</span><span class="sxs-lookup"><span data-stu-id="a13ec-103">.NET Glossary</span></span>

<span data-ttu-id="a13ec-104">Bu sözlükteki birincil hedef, .NET belgelerinde tanım olmadan sık görüntülenen seçili koşulların ve kısaltmalardan anlamaktır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="a13ec-105">AOT</span><span class="sxs-lookup"><span data-stu-id="a13ec-105">AOT</span></span>

<span data-ttu-id="a13ec-106">Sonraki süre derleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a13ec-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="a13ec-107">[JIT](#jit)'e benzer şekilde, bu derleyici Ayrıca [Il](#il) 'yi makine koduna çevirir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="a13ec-108">JıT derlemesinin aksine, uygulama yürütülmeden önce AOT derlemesi olur ve genellikle farklı bir makinede gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="a13ec-109">AOT aracı zincirleri çalışma zamanında derlenmediğinden, bu sürenin derlenmesi sırasında geçen süreyi en aza indirmeleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a13ec-109">Because AOT tool chains don't compile at run time, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="a13ec-110">Bu, daha iyi zaman harcayabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="a13ec-111">AOT bağlamı tüm uygulama olduğundan, AOT derleyicisi Ayrıca çapraz modül bağlamayı ve tam program analizini gerçekleştirir, bu da tüm başvuruların izlendiği ve tek bir yürütülebilir dosyanın oluşturulduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="a13ec-112">Bkz. [Corert](#corert) ve [.NET Native](#net-native).</span><span class="sxs-lookup"><span data-stu-id="a13ec-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="aspnet"></a><span data-ttu-id="a13ec-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a13ec-113">ASP.NET</span></span>

<span data-ttu-id="a13ec-114">.NET Framework ile birlikte gelen özgün ASP.NET uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="a13ec-115">Bazen ASP.NET, ASP.NET Core dahil olmak üzere hem ASP.NET uygulamalarına başvuran bir şemsiye terimidir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="a13ec-116">Belirli bir örnekte yer alan dönemin, bağlam tarafından belirlendiği anlamı.</span><span class="sxs-lookup"><span data-stu-id="a13ec-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="a13ec-117">Her iki uygulamayı da belirtmek için ASP.NET kullanmadığınız net bir ASP.NET 4. x öğesine başvurun.</span><span class="sxs-lookup"><span data-stu-id="a13ec-117">Refer to ASP.NET 4.x when you want to make it clear that you're not using ASP.NET to mean both implementations.</span></span>

<span data-ttu-id="a13ec-118">Bkz. [ASP.net belgeleri](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="a13ec-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="a13ec-119">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="a13ec-119">ASP.NET Core</span></span>

<span data-ttu-id="a13ec-120">.NET Core üzerinde oluşturulan ASP.NET platformlar arası, yüksek performanslı, açık kaynaklı bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="a13ec-120">A cross-platform, high-performance, open-source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="a13ec-121">[ASP.NET Core belgelerine](/aspnet/#pivot=core)bakın.</span><span class="sxs-lookup"><span data-stu-id="a13ec-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="a13ec-122">derleme</span><span class="sxs-lookup"><span data-stu-id="a13ec-122">assembly</span></span>

<span data-ttu-id="a13ec-123">*.dll* / Uygulamalar veya diğer derlemeler tarafından çağrılabilecek bir API koleksiyonu içerebilen bir. dll *. exe* dosyası.</span><span class="sxs-lookup"><span data-stu-id="a13ec-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="a13ec-124">Bir bütünleştirilmiş kod, arabirimler, sınıflar, yapılar, numaralandırmalar ve temsilciler gibi türler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="a13ec-125">Projenin *bin* klasöründeki derlemeler bazen *ikili dosyalar*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="a13ec-126">Ayrıca bkz. [kitaplık](#library).</span><span class="sxs-lookup"><span data-stu-id="a13ec-126">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="a13ec-127">CLR</span><span class="sxs-lookup"><span data-stu-id="a13ec-127">CLR</span></span>

<span data-ttu-id="a13ec-128">Ortak dil çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a13ec-128">Common Language Runtime.</span></span>

<span data-ttu-id="a13ec-129">Tam anlamı bağlama bağlıdır, ancak ortak dil çalışma zamanı genellikle .NET Framework çalışma zamanına başvurur.</span><span class="sxs-lookup"><span data-stu-id="a13ec-129">The exact meaning depends on the context, but Common Language Runtime usually refers to the runtime of .NET Framework.</span></span> <span data-ttu-id="a13ec-130">CLR bellek ayırmayı ve yönetimini işler.</span><span class="sxs-lookup"><span data-stu-id="a13ec-130">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="a13ec-131">CLR Ayrıca, yalnızca uygulamaları yürüten ancak aynı zamanda bir [JIT](#jit) derleyicisi kullanarak anında kod oluşturup derleyen bir sanal makinedir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-131">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span> <span data-ttu-id="a13ec-132">Geçerli Microsoft CLR uygulama yalnızca Windows.</span><span class="sxs-lookup"><span data-stu-id="a13ec-132">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="a13ec-133">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="a13ec-133">CoreCLR</span></span>

<span data-ttu-id="a13ec-134">.NET Core ortak dil çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a13ec-134">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="a13ec-135">Bu CLR, CLR ile aynı kod tabanında oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="a13ec-135">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="a13ec-136">Özgün olarak CoreCLR, Silverlight 'ın çalışma zamanı ve birden çok platformda çalışacak şekilde tasarlandı, özellikle Windows ve OS X. CoreCLR artık .NET Core 'un bir parçası ve CLR 'nin basitleştirilmiş bir sürümünü temsil etmektedir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-136">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="a13ec-137">Artık çok sayıda Linux dağıtımı desteği de dahil olmak üzere [platformlar arası](#cross-platform) bir çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a13ec-137">It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="a13ec-138">CoreCLR Ayrıca JıT ve kod yürütme özelliklerine sahip bir sanal makinedir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-138">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="a13ec-139">CoreFx</span><span class="sxs-lookup"><span data-stu-id="a13ec-139">CoreFx</span></span>

<span data-ttu-id="a13ec-140">.NET Core temel sınıf kitaplığı (BCL)</span><span class="sxs-lookup"><span data-stu-id="a13ec-140">.NET Core Base Class Library (BCL)</span></span>

> [!TIP]
> <span data-ttu-id="a13ec-141">*FX* *Framework*için temsil eder.</span><span class="sxs-lookup"><span data-stu-id="a13ec-141">*Fx* stands for *framework*.</span></span>

<span data-ttu-id="a13ec-142">Sistemi oluşturan kitaplıkların bir kümesi. \* (ve sınırlı bir ölçüde Microsoft. \* ) öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="a13ec-142">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="a13ec-143">BCL, ASP.NET Core gibi daha üst düzey uygulama çerçevelerinin üzerine inşa eden genel amaçlı, alt düzey bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-143">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="a13ec-144">.NET Core BCL kaynak kodu, [.NET Core çalışma zamanı deposunda](https://github.com/dotnet/runtime)bulunur.</span><span class="sxs-lookup"><span data-stu-id="a13ec-144">The source code of the .NET Core BCL is contained in the [.NET Core runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="a13ec-145">Ancak, .NET Core API 'lerinin çoğunluğu .NET Framework de mevcuttur. bu sayede CoreFX ' i .NET Framework BCL çatalını olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a13ec-145">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="a13ec-146">CoreRT</span><span class="sxs-lookup"><span data-stu-id="a13ec-146">CoreRT</span></span>

<span data-ttu-id="a13ec-147">.NET Core çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a13ec-147">.NET Core runtime.</span></span>

<span data-ttu-id="a13ec-148">CLR/CoreCLR 'nin aksine CoreRT bir sanal makine değildir, bu da bir [JIT](#jit)içermediğinden kod oluşturma ve çalıştırma tesislerini içermediği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-148">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="a13ec-149">Ancak, [GC](#gc) ve çalışma zamanı türü tanımlama (rtti) ve yansıma özelliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-149">It does, however, include the [GC](#gc) and the ability for run-time type identification (RTTI) and reflection.</span></span> <span data-ttu-id="a13ec-150">Ancak, tür sistemi yansıma için meta verilerin gerekli olmaması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-150">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="a13ec-151">Meta verilerin gerekli olmaması, gereksiz meta verileri bağlayabilen bir [AOT](#aot) araç zinciri olmasını ve (daha önemlisi) uygulamanın kullanmayan kodu belirlemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-151">Not requiring metadata enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="a13ec-152">CoreRT geliştirme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-152">CoreRT is in development.</span></span>

<span data-ttu-id="a13ec-153">[.NET Native ve CoreRT Için tanıtım](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a13ec-153">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="a13ec-154">platformlar arası</span><span class="sxs-lookup"><span data-stu-id="a13ec-154">cross-platform</span></span>

<span data-ttu-id="a13ec-155">Her biri için özel olarak yeniden yazmak zorunda kalmadan, Linux, Windows ve iOS gibi birden çok farklı işletim sisteminde kullanılabilen bir uygulamayı geliştirebilir ve yürütebilme özelliği.</span><span class="sxs-lookup"><span data-stu-id="a13ec-155">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows, and iOS, without having to rewrite specifically for each one.</span></span> <span data-ttu-id="a13ec-156">Bu, farklı platformlardaki uygulamalar arasında kod yeniden kullanımını ve tutarlılığı sunar.</span><span class="sxs-lookup"><span data-stu-id="a13ec-156">This enables code reuse and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="a13ec-157">ekosistemi</span><span class="sxs-lookup"><span data-stu-id="a13ec-157">ecosystem</span></span>

<span data-ttu-id="a13ec-158">Belirli bir teknoloji için uygulama derlemek ve çalıştırmak için kullanılan tüm çalışma zamanı yazılımları, geliştirme araçları ve topluluk kaynakları.</span><span class="sxs-lookup"><span data-stu-id="a13ec-158">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="a13ec-159">".NET ekosistemi" terimi, üçüncü taraf uygulama ve kitaplıkları dahil olmak üzere ".NET Stack" gibi benzer terimlerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-159">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="a13ec-160">Tümcede bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a13ec-160">Here's an example in a sentence:</span></span>

- <span data-ttu-id="a13ec-161">" [.NET Standard](#net-standard) arkasındaki mosyon, .net ekosisteminde daha fazla esneklik sağlamak."</span><span class="sxs-lookup"><span data-stu-id="a13ec-161">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span>

## <a name="framework"></a><span data-ttu-id="a13ec-162">çerçeve</span><span class="sxs-lookup"><span data-stu-id="a13ec-162">framework</span></span>

<span data-ttu-id="a13ec-163">Genel olarak, belirli bir teknolojiyi temel alan uygulamaların geliştirilmesini ve dağıtılmasını kolaylaştıran kapsamlı bir API koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="a13ec-163">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="a13ec-164">Bu genel anlamda, ASP.NET Core ve Windows Forms uygulama çerçevelerinin örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-164">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="a13ec-165">Ayrıca bkz. [kitaplık](#library).</span><span class="sxs-lookup"><span data-stu-id="a13ec-165">See also [library](#library).</span></span>

<span data-ttu-id="a13ec-166">"Framework" sözcüğünün aşağıdaki koşullarda daha belirli bir teknik anlamı vardır:</span><span class="sxs-lookup"><span data-stu-id="a13ec-166">The word "framework" has a more specific technical meaning in the following terms:</span></span>

- [<span data-ttu-id="a13ec-167">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a13ec-167">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="a13ec-168">hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="a13ec-168">target framework</span></span>](#target-framework)
- [<span data-ttu-id="a13ec-169">TFD (hedef çerçeve bilinen adı)</span><span class="sxs-lookup"><span data-stu-id="a13ec-169">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="a13ec-170">Mevcut belgelerde, "Framework" Bazen bir [.NET uygulamasını](#implementation-of-net)ifade eder.</span><span class="sxs-lookup"><span data-stu-id="a13ec-170">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="a13ec-171">Örneğin, bir makale .NET Core Framework 'ü çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-171">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="a13ec-172">Bu karışık kullanımı belgelerden ortadan kaldırmaya planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a13ec-172">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="a13ec-173">GC</span><span class="sxs-lookup"><span data-stu-id="a13ec-173">GC</span></span>

<span data-ttu-id="a13ec-174">Çöp toplayıcı.</span><span class="sxs-lookup"><span data-stu-id="a13ec-174">Garbage collector.</span></span>

<span data-ttu-id="a13ec-175">Çöp toplayıcı, otomatik bellek yönetiminin bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-175">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="a13ec-176">GC, artık kullanılmayan nesnelerin kapladığı belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-176">The GC frees memory occupied by objects that are no longer in use.</span></span>

<span data-ttu-id="a13ec-177">Bkz. [çöp toplama](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="a13ec-177">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="a13ec-178">IL</span><span class="sxs-lookup"><span data-stu-id="a13ec-178">IL</span></span>

<span data-ttu-id="a13ec-179">Ara dil.</span><span class="sxs-lookup"><span data-stu-id="a13ec-179">Intermediate language.</span></span>

<span data-ttu-id="a13ec-180">C# gibi daha üst düzey .NET dilleri, ara dil (IL) olarak adlandırılan donanımdan bağımsız bir yönerge kümesine derler.</span><span class="sxs-lookup"><span data-stu-id="a13ec-180">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="a13ec-181">Il bazen MSIL (Microsoft Il) veya CıL (ortak Il) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-181">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="a13ec-182">JIT</span><span class="sxs-lookup"><span data-stu-id="a13ec-182">JIT</span></span>

<span data-ttu-id="a13ec-183">Just-In-Time derleyicisi.</span><span class="sxs-lookup"><span data-stu-id="a13ec-183">Just-in-time compiler.</span></span>

<span data-ttu-id="a13ec-184">[AOT](#aot)'ye benzer şekilde, bu derleyici [Il](#il) 'yi işlemcinin anladığı makine koduna dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="a13ec-184">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="a13ec-185">AOT 'nin aksine JıT derleme isteğe bağlı olur ve kodun üzerinde çalışması gereken makinede gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-185">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="a13ec-186">Uygulamanın yürütülmesi sırasında JıT derlemesi gerçekleşdiğinden, derleme süresi çalışma zamanının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-186">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="a13ec-187">Bu nedenle, JıT derleyicileri, kodu en iyi duruma getirmeye harcanan süreyi, sonuçta elde edilen kodun üretebildiği tasarruflarla dengelemeye yönelik</span><span class="sxs-lookup"><span data-stu-id="a13ec-187">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="a13ec-188">Ancak, bir JıT gerçek donanımı bilir ve geliştiricilerin farklı uygulamalar sunmalarını ücretsiz olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-188">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="a13ec-189">.NET uygulama</span><span class="sxs-lookup"><span data-stu-id="a13ec-189">implementation of .NET</span></span>

<span data-ttu-id="a13ec-190">.NET uygulamasının şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="a13ec-190">An implementation of .NET includes:</span></span>

- <span data-ttu-id="a13ec-191">Bir veya daha fazla çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="a13ec-191">One or more runtimes.</span></span> <span data-ttu-id="a13ec-192">Örnekler: CLR, CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="a13ec-192">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="a13ec-193">.NET Standard bir sürümünü uygulayan ve ek API 'Ler içerebilen bir sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="a13ec-193">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="a13ec-194">Örnekler: .NET Framework temel sınıf kitaplığı, .NET Core temel sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="a13ec-194">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="a13ec-195">İsteğe bağlı olarak, bir veya daha fazla uygulama çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="a13ec-195">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="a13ec-196">Örnekler: ASP.NET, Windows Forms ve WPF .NET Framework dahil edilmiştir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-196">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="a13ec-197">İsteğe bağlı olarak, geliştirme araçları.</span><span class="sxs-lookup"><span data-stu-id="a13ec-197">Optionally, development tools.</span></span> <span data-ttu-id="a13ec-198">Bazı geliştirme araçları birden çok uygulama arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-198">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="a13ec-199">.NET uygulamalarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="a13ec-199">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="a13ec-200">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a13ec-200">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="a13ec-201">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a13ec-201">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="a13ec-202">Evrensel Windows Platformu (UWP)</span><span class="sxs-lookup"><span data-stu-id="a13ec-202">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="a13ec-203">kitaplık</span><span class="sxs-lookup"><span data-stu-id="a13ec-203">library</span></span>

<span data-ttu-id="a13ec-204">Uygulamalar veya diğer kitaplıklar tarafından çağrılabilen API 'lerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a13ec-204">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="a13ec-205">Bir .NET kitaplığı, bir [veya daha fazla](#assembly)derlemeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="a13ec-205">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="a13ec-206">Sözcükler kitaplığı ve [Framework](#framework) genellikle terimler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-206">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="a13ec-207">metapackage</span><span class="sxs-lookup"><span data-stu-id="a13ec-207">metapackage</span></span>

<span data-ttu-id="a13ec-208">Kendi kitaplığı olmayan ancak yalnızca bağımlılıklar listesi olan bir NuGet paketi.</span><span class="sxs-lookup"><span data-stu-id="a13ec-208">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="a13ec-209">Dahil edilen paketler, isteğe bağlı olarak bir hedef çerçeve için API 'YI kurabilir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-209">The included packages can optionally establish the API for a target framework.</span></span>

## <a name="mono"></a><span data-ttu-id="a13ec-210">Mono</span><span class="sxs-lookup"><span data-stu-id="a13ec-210">Mono</span></span>

<span data-ttu-id="a13ec-211">Mono, genellikle küçük bir çalışma zamanı gerektiğinde kullanılan açık kaynaklı, [platformlar arası](#cross-platform) bir .net uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-211">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="a13ec-212">Android, Mac, iOS, tvOS ve watchOS üzerinde Xamarin uygulamalarını güçlendirir ve öncelikle küçük bir ayak izi gerektiren uygulamalara odaklanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-212">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS, and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="a13ec-213">Şu anda yayımlanmış .NET Standard sürümlerinin tümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="a13ec-213">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="a13ec-214">Tarihsel olarak, mono .NET Framework daha büyük API 'sini uyguladık ve UNIX üzerinde en popüler yeteneklerin bazılarını öykünüyler.</span><span class="sxs-lookup"><span data-stu-id="a13ec-214">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="a13ec-215">Bu özellik bazen UNIX üzerinde bu özellikleri kullanan .NET uygulamalarını çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-215">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="a13ec-216">Mono genellikle tam zamanında bir derleyici ile kullanılır, ancak iOS gibi platformlarda kullanılan tam bir statik derleyici (güncel derleme) da sunar.</span><span class="sxs-lookup"><span data-stu-id="a13ec-216">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="a13ec-217">Mono hakkında daha fazla bilgi edinmek için [mono belgelerine](https://www.mono-project.com/docs/)bakın.</span><span class="sxs-lookup"><span data-stu-id="a13ec-217">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="a13ec-218">.NET</span><span class="sxs-lookup"><span data-stu-id="a13ec-218">.NET</span></span>

<span data-ttu-id="a13ec-219">[.NET Standard](#net-standard) ve tüm [.NET uygulamaları](#implementation-of-net) ve iş yükleri için şemsiye terimi.</span><span class="sxs-lookup"><span data-stu-id="a13ec-219">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="a13ec-220">Her zaman tamamen büyük harf, hiçbir zaman ".net".</span><span class="sxs-lookup"><span data-stu-id="a13ec-220">Always fully capitalized, never ".Net".</span></span>

<span data-ttu-id="a13ec-221">Bkz. [.net Kılavuzu](index.yml)</span><span class="sxs-lookup"><span data-stu-id="a13ec-221">See the [.NET guide](index.yml)</span></span>

## <a name="net-core"></a><span data-ttu-id="a13ec-222">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a13ec-222">.NET Core</span></span>

<span data-ttu-id="a13ec-223">.NET için platformlar arası, yüksek performanslı, açık kaynaklı bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="a13ec-223">A cross-platform, high-performance, open-source implementation of .NET.</span></span> <span data-ttu-id="a13ec-224">Çekirdek ortak dil çalışma zamanını (CoreCLR), çekirdek AOT çalışma zamanını (, geliştirme sırasında CoreRT), çekirdek temel sınıf kitaplığını ve temel SDK 'Yı içerir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-224">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="a13ec-225">Bkz. [.NET Core](../core/index.yml).</span><span class="sxs-lookup"><span data-stu-id="a13ec-225">See [.NET Core](../core/index.yml).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="a13ec-226">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="a13ec-226">.NET Core CLI</span></span>

<span data-ttu-id="a13ec-227">.NET Core uygulamaları geliştirmek için platformlar arası araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="a13ec-227">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="a13ec-228">Bkz. [.NET Core CLI](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="a13ec-228">See [.NET Core CLI](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="a13ec-229">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="a13ec-229">.NET Core SDK</span></span>

<span data-ttu-id="a13ec-230">Geliştiricilerin .NET Core Uygulamaları ve kitaplıkları oluşturmalarına izin veren bir kitaplık ve araç kümesi.</span><span class="sxs-lookup"><span data-stu-id="a13ec-230">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="a13ec-231">Uygulamalar oluşturmaya yönelik [.NET Core CLI](#net-core-cli) , uygulamalar oluşturmak ve çalıştırmak Için .NET Core kitaplıklarını ve çalışma ZAMANıNı ve CLI komutlarını çalıştıran ve uygulamaları çalıştıran DotNet çalıştırılabilir (*dotnet.exe*) bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-231">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="a13ec-232">[.NET Core SDK genel bakış](../core/sdk.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="a13ec-232">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="a13ec-233">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="a13ec-233">.NET Framework</span></span>

<span data-ttu-id="a13ec-234">Yalnızca Windows üzerinde çalışan bir .NET uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-234">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="a13ec-235">Ortak dil çalışma zamanını (CLR), temel sınıf kitaplığını ve ASP.NET, Windows Forms ve WPF gibi uygulama çerçevesi kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-235">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="a13ec-236">[.NET Framework Kılavuzu](../framework/index.yml)' na bakın.</span><span class="sxs-lookup"><span data-stu-id="a13ec-236">See [.NET Framework Guide](../framework/index.yml).</span></span>

## <a name="net-native"></a><span data-ttu-id="a13ec-237">.NET Yerel</span><span class="sxs-lookup"><span data-stu-id="a13ec-237">.NET Native</span></span>

<span data-ttu-id="a13ec-238">Anında yerel kod üreten bir derleyici aracı zinciri (AOT)-ın-Time (JıT) yerine.</span><span class="sxs-lookup"><span data-stu-id="a13ec-238">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="a13ec-239">Derleme, geliştirici makinesinde C++ derleyicisinin ve bağlayıcının çalışmasına benzer şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-239">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="a13ec-240">Kullanılmayan kodu kaldırır ve iyileştirerek daha fazla zaman harcamalar.</span><span class="sxs-lookup"><span data-stu-id="a13ec-240">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="a13ec-241">Kodu kitaplıklardan ayıklar ve çalıştırılabilirle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-241">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="a13ec-242">Sonuç, uygulamanın tamamını temsil eden tek bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="a13ec-242">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="a13ec-243">UWP, .NET Native tarafından desteklenen ilk uygulama çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-243">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="a13ec-244">Şimdi Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="a13ec-244">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="a13ec-245">[.NET Native ve CoreRT tanıtımı](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md) konusuna bakın</span><span class="sxs-lookup"><span data-stu-id="a13ec-245">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="a13ec-246">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="a13ec-246">.NET Standard</span></span>

<span data-ttu-id="a13ec-247">.NET API 'lerinin her bir .NET uygulamasında kullanılabilen resmi bir belirtimi.</span><span class="sxs-lookup"><span data-stu-id="a13ec-247">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="a13ec-248">.NET Standard belirtimine bazen belgelerde bir kitaplık denir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-248">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="a13ec-249">Bir kitaplık yalnızca belirtim (arabirimler) değil API uygulamalarını içerdiğinden, bir "Library" .NET Standard çağırmak yanıltıcıdır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-249">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="a13ec-250">.NET Standard metapackage () adı ile ilgili olarak, belgelerden bu kullanımı ortadan kaldırmaya planlıyoruz `NETStandard.Library` .</span><span class="sxs-lookup"><span data-stu-id="a13ec-250">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="a13ec-251">Bkz. [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="a13ec-251">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="a13ec-252">NGEN</span><span class="sxs-lookup"><span data-stu-id="a13ec-252">NGEN</span></span>

<span data-ttu-id="a13ec-253">Yerel (görüntü) oluşturma.</span><span class="sxs-lookup"><span data-stu-id="a13ec-253">Native (image) generation.</span></span>

<span data-ttu-id="a13ec-254">Bu teknolojiyi kalıcı bir JıT derleyicisi olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a13ec-254">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="a13ec-255">Genellikle kodun yürütüldüğü makinede kodu derler, ancak derleme genellikle yüklemesi sırasında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-255">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="a13ec-256">leyebilir</span><span class="sxs-lookup"><span data-stu-id="a13ec-256">package</span></span>

<span data-ttu-id="a13ec-257">Bir NuGet paketi &mdash; veya yalnızca bir paket &mdash; , aynı ada sahip bir veya daha fazla bütünleştirilmiş kod içeren bir *. zip* dosyasıdır ve yazar adı gibi ek meta verilerle birlikte.</span><span class="sxs-lookup"><span data-stu-id="a13ec-257">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="a13ec-258">*. Zip* dosyası *. nupkg* uzantısına sahiptir ve birden çok hedef çerçeve ve sürümde kullanılmak üzere *. dll* dosyaları ve *. xml* dosyaları gibi varlıkları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-258">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="a13ec-259">Bir uygulama veya kitaplığa yüklendiğinde, uygun varlıklar uygulama veya kitaplık tarafından belirtilen hedef çerçeveye göre seçilir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-259">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="a13ec-260">Arabirimi tanımlayan varlıklar *ref* klasöründedir ve uygulamayı tanımlayan varlıklar *lib* klasöründedir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-260">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="a13ec-261">platform</span><span class="sxs-lookup"><span data-stu-id="a13ec-261">platform</span></span>

<span data-ttu-id="a13ec-262">Windows, macOS, Linux, iOS ve Android gibi bir işletim sistemi ve üzerinde çalıştığı donanım.</span><span class="sxs-lookup"><span data-stu-id="a13ec-262">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="a13ec-263">Cümlelerde kullanım örnekleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a13ec-263">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="a13ec-264">".NET Core, .NET 'in platformlar arası bir uygulamasıdır."</span><span class="sxs-lookup"><span data-stu-id="a13ec-264">".NET Core is a cross-platform implementation of .NET."</span></span>
- <span data-ttu-id="a13ec-265">"PCL profilleri Microsoft platformlarını temsil ederken .NET Standard platforma göre belirsizdir."</span><span class="sxs-lookup"><span data-stu-id="a13ec-265">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="a13ec-266">.NET belgeleri, .NET veya .NET Stack 'in tüm uygulamalar dahil bir uygulamasını ifade etmek için sık sık ".NET platformu" kullanır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-266">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="a13ec-267">Bu kullanımların her ikisi de birincil (OS/donanım) anlamı ile karıştırılmamalıdır. bu nedenle, bu kullanımları belgelerden ortadan kaldırmaya planlanıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a13ec-267">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="a13ec-268">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="a13ec-268">runtime</span></span>

<span data-ttu-id="a13ec-269">Yönetilen programın yürütme ortamı.</span><span class="sxs-lookup"><span data-stu-id="a13ec-269">The execution environment for a managed program.</span></span>

<span data-ttu-id="a13ec-270">İşletim sistemi çalışma zamanı ortamının bir parçasıdır ancak .NET çalışma zamanının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-270">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="a13ec-271">.NET çalışma zamanlarının bazı örnekleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="a13ec-271">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="a13ec-272">Ortak Dil Çalışma Zamanı (CLR)</span><span class="sxs-lookup"><span data-stu-id="a13ec-272">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="a13ec-273">Çekirdek ortak dil çalışma zamanı (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="a13ec-273">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="a13ec-274">.NET Native (UWP için)</span><span class="sxs-lookup"><span data-stu-id="a13ec-274">.NET Native (for UWP)</span></span>
- <span data-ttu-id="a13ec-275">Mono çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="a13ec-275">Mono runtime</span></span>

<span data-ttu-id="a13ec-276">.NET belgeleri bazen .NET uygulamasının bir uygulamasını ifade etmek için "Runtime" kullanır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-276">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="a13ec-277">Örneğin, aşağıdaki cümleler "Runtime" ın "uygulama" ile değiştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="a13ec-277">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="a13ec-278">"Çeşitli .NET çalışma zamanları .NET Standard belirli sürümlerini uygular."</span><span class="sxs-lookup"><span data-stu-id="a13ec-278">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="a13ec-279">"Birden çok çalışma zamanında çalıştırılması amaçlanan kitaplıkların bu çerçeveyi hedeflemesi gerekir."</span><span class="sxs-lookup"><span data-stu-id="a13ec-279">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="a13ec-280">(.NET Standard başvurma)</span><span class="sxs-lookup"><span data-stu-id="a13ec-280">(referring to .NET Standard)</span></span>
- <span data-ttu-id="a13ec-281">"Çeşitli .NET çalışma zamanları .NET Standard belirli sürümlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="a13ec-281">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="a13ec-282">…</span><span class="sxs-lookup"><span data-stu-id="a13ec-282">…</span></span> <span data-ttu-id="a13ec-283">Her .NET çalışma zamanı sürümü, desteklediği en yüksek .NET Standard sürümünü tanıtır... "</span><span class="sxs-lookup"><span data-stu-id="a13ec-283">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="a13ec-284">Bu tutarsız kullanımı ortadan kaldırmaya planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="a13ec-284">We plan to eliminate this inconsistent usage.</span></span>

## <a name="stack"></a><span data-ttu-id="a13ec-285">yığın</span><span class="sxs-lookup"><span data-stu-id="a13ec-285">stack</span></span>

<span data-ttu-id="a13ec-286">Uygulamaları derlemek ve çalıştırmak için birlikte kullanılan bir programlama teknolojileri kümesi.</span><span class="sxs-lookup"><span data-stu-id="a13ec-286">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="a13ec-287">".NET Stack" .NET Standard ve tüm .NET uygulamalarını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="a13ec-287">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="a13ec-288">"A .NET Stack" ifadesi bir .NET uygulamasına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-288">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span>

## <a name="target-framework"></a><span data-ttu-id="a13ec-289">hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="a13ec-289">target framework</span></span>

<span data-ttu-id="a13ec-290">Bir .NET uygulamasının veya kitaplığının dayandığı API 'lerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="a13ec-290">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="a13ec-291">Bir uygulama veya kitaplık, tüm .NET uygulamalarında standartlaştırılmış bir API kümesine yönelik belirtim olan .NET Standard bir sürümünü (örneğin, .NET Standard 2,0) hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-291">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="a13ec-292">Bir uygulama veya kitaplık, belirli bir .NET uygulamasının bir sürümünü de hedefleyebilir ve bu durumda uygulamaya özgü API 'lere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a13ec-292">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="a13ec-293">Örneğin, Xamarin. iOS 'u hedefleyen bir uygulama Xamarin tarafından sağlanmış iOS API sarmalayıcılarını erişim altına alır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-293">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="a13ec-294">Bazı hedef çerçeveler için (örneğin, .NET Framework) kullanılabilir API 'ler, .NET uygulamasının uygulama çerçevesi API 'Leri içerebilen bir sisteme yüklediği derlemeler tarafından tanımlanır (örneğin, ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="a13ec-294">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="a13ec-295">Paket tabanlı hedef çerçeveler için (.NET Standard ve .NET Core gibi), çerçeve API 'Leri, uygulama veya kitaplıkta yüklü paketler tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-295">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="a13ec-296">Bu durumda, hedef çerçeve örtülü olarak Framework 'ü oluşturan tüm paketlere başvuran bir metapackage belirler.</span><span class="sxs-lookup"><span data-stu-id="a13ec-296">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="a13ec-297">Bkz. [hedef çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a13ec-297">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="a13ec-298">TFM</span><span class="sxs-lookup"><span data-stu-id="a13ec-298">TFM</span></span>

<span data-ttu-id="a13ec-299">Hedef Framework bilinen adı.</span><span class="sxs-lookup"><span data-stu-id="a13ec-299">Target framework moniker.</span></span>

<span data-ttu-id="a13ec-300">.NET uygulaması veya kitaplığının hedef çerçevesini belirtmek için standartlaştırılmış bir belirteç biçimi.</span><span class="sxs-lookup"><span data-stu-id="a13ec-300">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="a13ec-301">Hedef çerçevelere genellikle gibi kısa bir ad başvurulur `net462` .</span><span class="sxs-lookup"><span data-stu-id="a13ec-301">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="a13ec-302">Uzun biçimli TFMs (gibi. NETFramework, Version = 4.6.2) var, ancak genellikle bir hedef çerçeve belirtmek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="a13ec-302">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="a13ec-303">Bkz. [hedef çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="a13ec-303">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="a13ec-304">UWP</span><span class="sxs-lookup"><span data-stu-id="a13ec-304">UWP</span></span>

<span data-ttu-id="a13ec-305">Evrensel Windows Platformu.</span><span class="sxs-lookup"><span data-stu-id="a13ec-305">Universal Windows Platform.</span></span>

<span data-ttu-id="a13ec-306">Nesnelerin İnterneti (IoT) için modern, dokunmatik özellikli Windows Uygulamaları ve yazılım oluşturmak için kullanılan bir .NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="a13ec-306">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="a13ec-307">Bilgisayar, tabletler, telefonlar ve hatta Xbox dahil olmak üzere hedeflemek isteyebileceğiniz farklı cihaz türlerini içerecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-307">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="a13ec-308">UWP, merkezi bir App Store, bir yürütme ortamı (AppContainer) ve Win32 (WinRT) yerine kullanılacak bir dizi Windows API 'si gibi birçok hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="a13ec-308">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="a13ec-309">Uygulamalar C++, C#, Visual Basic ve JavaScript 'te yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="a13ec-309">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="a13ec-310">C# ve Visual Basic kullanılırken .NET API 'Leri .NET Core tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a13ec-310">When using C# and Visual Basic, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="a13ec-311">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a13ec-311">See also</span></span>

- [<span data-ttu-id="a13ec-312">.NET kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a13ec-312">.NET Guide</span></span>](index.yml)
- [<span data-ttu-id="a13ec-313">.NET Framework Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="a13ec-313">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="a13ec-314">.NET Core</span><span class="sxs-lookup"><span data-stu-id="a13ec-314">.NET Core</span></span>](../core/index.yml)
- [<span data-ttu-id="a13ec-315">ASP.NET genel bakış</span><span class="sxs-lookup"><span data-stu-id="a13ec-315">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="a13ec-316">ASP.NET Core genel bakış</span><span class="sxs-lookup"><span data-stu-id="a13ec-316">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
