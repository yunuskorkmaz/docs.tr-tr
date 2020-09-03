---
title: .NET Sözlüğü
description: .NET belgelerinde kullanılan seçili koşulların anlamını öğrenin.
ms.date: 01/22/2019
ms.technology: dotnet-standard
ms.openlocfilehash: b79580baa12cc8081346678f06d49a9d0455375c
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89415023"
---
# <a name="net-glossary"></a><span data-ttu-id="5fbfe-103">.NET Sözlüğü</span><span class="sxs-lookup"><span data-stu-id="5fbfe-103">.NET Glossary</span></span>

<span data-ttu-id="5fbfe-104">Bu sözlükteki birincil hedef, .NET belgelerinde tanım olmadan sık görüntülenen seçili koşulların ve kısaltmalardan anlamaktır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="5fbfe-105">AOT</span><span class="sxs-lookup"><span data-stu-id="5fbfe-105">AOT</span></span>

<span data-ttu-id="5fbfe-106">Sonraki süre derleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="5fbfe-107">[JIT](#jit)'e benzer şekilde, bu derleyici Ayrıca [Il](#il) 'yi makine koduna çevirir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="5fbfe-108">JıT derlemesinin aksine, uygulama yürütülmeden önce AOT derlemesi olur ve genellikle farklı bir makinede gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="5fbfe-109">AOT aracı zincirleri çalışma zamanında derlenmediğinden, bu sürenin derlenmesi sırasında geçen süreyi en aza indirmeleri gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-109">Because AOT tool chains don't compile at run time, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="5fbfe-110">Bu, daha iyi zaman harcayabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="5fbfe-111">AOT bağlamı tüm uygulama olduğundan, AOT derleyicisi Ayrıca çapraz modül bağlamayı ve tam program analizini gerçekleştirir, bu da tüm başvuruların izlendiği ve tek bir yürütülebilir dosyanın oluşturulduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

<span data-ttu-id="5fbfe-112">Bkz. [Corert](#corert) ve [.NET Native](#net-native).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-112">See [CoreRT](#corert) and [.NET Native](#net-native).</span></span>

## <a name="aspnet"></a><span data-ttu-id="5fbfe-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="5fbfe-113">ASP.NET</span></span>

<span data-ttu-id="5fbfe-114">.NET Framework ile birlikte gelen özgün ASP.NET uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="5fbfe-115">Bazen ASP.NET, ASP.NET Core dahil olmak üzere hem ASP.NET uygulamalarına başvuran bir şemsiye terimidir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="5fbfe-116">Belirli bir örnekte yer alan dönemin, bağlam tarafından belirlendiği anlamı.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="5fbfe-117">Her iki uygulamayı da belirtmek için ASP.NET kullanmadığınız net bir ASP.NET 4. x öğesine başvurun.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-117">Refer to ASP.NET 4.x when you want to make it clear that you're not using ASP.NET to mean both implementations.</span></span>

<span data-ttu-id="5fbfe-118">Bkz. [ASP.net belgeleri](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="5fbfe-119">ASP.NET Çekirdeği</span><span class="sxs-lookup"><span data-stu-id="5fbfe-119">ASP.NET Core</span></span>

<span data-ttu-id="5fbfe-120">ASP.NET 'in platformlar arası, yüksek performanslı, açık kaynaklı bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-120">A cross-platform, high-performance, open-source implementation of ASP.NET.</span></span>

<span data-ttu-id="5fbfe-121">[ASP.NET Core belgelerine](/aspnet/#pivot=core)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="5fbfe-122">derleme</span><span class="sxs-lookup"><span data-stu-id="5fbfe-122">assembly</span></span>

<span data-ttu-id="5fbfe-123">*.dll* / Uygulamalar veya diğer derlemeler tarafından çağrılabilecek bir API koleksiyonu içerebilen bir. dll *. exe* dosyası.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by applications or other assemblies.</span></span>

<span data-ttu-id="5fbfe-124">Bir bütünleştirilmiş kod, arabirimler, sınıflar, yapılar, numaralandırmalar ve temsilciler gibi türler içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="5fbfe-125">Projenin *bin* klasöründeki derlemeler bazen *ikili dosyalar*olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="5fbfe-126">Ayrıca bkz. [kitaplık](#library).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-126">See also [library](#library).</span></span>

## <a name="bcl"></a><span data-ttu-id="5fbfe-127">BCL</span><span class="sxs-lookup"><span data-stu-id="5fbfe-127">BCL</span></span>

<span data-ttu-id="5fbfe-128">Temel sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-128">Base Class Library.</span></span> <span data-ttu-id="5fbfe-129">*Çerçeve kitaplıkları*olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-129">Also known as *framework libraries*.</span></span>

<span data-ttu-id="5fbfe-130">Sistemi oluşturan kitaplıkların bir kümesi. \* (ve sınırlı bir ölçüde Microsoft. \* ) öznitelikleri.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-130">A set of libraries that comprise the System.\* (and to a limited extent Microsoft.\*) namespaces.</span></span> <span data-ttu-id="5fbfe-131">BCL, ASP.NET Core gibi daha üst düzey uygulama çerçevelerinin üzerine inşa eden genel amaçlı, alt düzey bir çerçevedir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-131">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span>

<span data-ttu-id="5fbfe-132">[.NET 5 (ve .NET Core) ve sonraki SÜRÜMLERIN](#net-5-and-later-versions) BCL kaynak kodu, [.NET çalışma zamanı deposunda](https://github.com/dotnet/runtime)bulunur.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-132">The source code of the BCL for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions) is contained in the [.NET runtime repository](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="5fbfe-133">.NET 'in bu yeni uygulamasına yönelik BCL API 'Lerinin çoğu .NET Framework de mevcuttur. bu sayede, bu kaynak kodu .NET Framework BCL kaynak kodunun bir çatalı olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-133">The majority of the BCL APIs for this newer implementation of .NET are also available in .NET Framework, so you can think of this source code as a fork of the .NET Framework BCL source code.</span></span>

## <a name="clr"></a><span data-ttu-id="5fbfe-134">CLR</span><span class="sxs-lookup"><span data-stu-id="5fbfe-134">CLR</span></span>

<span data-ttu-id="5fbfe-135">Ortak dil çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-135">Common Language Runtime.</span></span>

<span data-ttu-id="5fbfe-136">Tam anlamı bağlama göre değişir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-136">The exact meaning depends on the context.</span></span> <span data-ttu-id="5fbfe-137">Ortak dil çalışma zamanı genellikle [.NET Framework](#net-framework) çalışma zamanına veya [.NET 5 (ve .NET Core) ve sonraki sürümlere](#net-5-and-later-versions)yönelik çalışma zamanına başvurur.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-137">Common Language Runtime usually refers to the runtime of [.NET Framework](#net-framework) or the runtime of [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span>

<span data-ttu-id="5fbfe-138">CLR bellek ayırmayı ve yönetimini işler.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-138">A CLR handles memory allocation and management.</span></span> <span data-ttu-id="5fbfe-139">CLR Ayrıca, yalnızca uygulamaları yürüten ancak aynı zamanda bir [JIT](#jit) derleyicisi kullanarak anında kod oluşturup derleyen bir sanal makinedir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-139">A CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a [JIT](#jit) compiler.</span></span>

<span data-ttu-id="5fbfe-140">.NET Framework için CLR uygulama yalnızca Windows ' a yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-140">The CLR implementation for .NET Framework is Windows only.</span></span>

<span data-ttu-id="5fbfe-141">.NET 5 ve sonraki sürümler için CLR uygulama (çekirdek CLR olarak da bilinir) .NET Framework CLR ile aynı kod tabanından oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-141">The CLR implementation for .NET 5 and later versions (also known as the Core CLR) is built from the same code base as the .NET Framework CLR.</span></span> <span data-ttu-id="5fbfe-142">Başlangıçta, çekirdek CLR Silverlight 'ın çalışma zamanı ve özellikle Windows ve OS X gibi birden çok platformda çalışmak üzere tasarlanmıştır. Artık çok sayıda Linux dağıtımı desteği de dahil olmak üzere [platformlar arası](#cross-platform) bir çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-142">Originally, the Core CLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. It's still a [cross-platform](#cross-platform) runtime, now including support for many Linux distributions.</span></span>

<span data-ttu-id="5fbfe-143">Ayrıca bkz. [çalışma zamanı](#runtime).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-143">See also [runtime](#runtime).</span></span>

## <a name="core-clr"></a><span data-ttu-id="5fbfe-144">Çekirdek CLR</span><span class="sxs-lookup"><span data-stu-id="5fbfe-144">Core CLR</span></span>

<span data-ttu-id="5fbfe-145">[.NET 5 (ve .NET Core) ve sonraki sürümler](#net-5-and-later-versions)Için ortak dil çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-145">The Common Language Runtime for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span>

<span data-ttu-id="5fbfe-146">Bkz. [clr](#clr)</span><span class="sxs-lookup"><span data-stu-id="5fbfe-146">See [CLR](#clr)</span></span>

## <a name="corert"></a><span data-ttu-id="5fbfe-147">CoreRT</span><span class="sxs-lookup"><span data-stu-id="5fbfe-147">CoreRT</span></span>

<span data-ttu-id="5fbfe-148">[Clr](#clr)'nin aksine corert sanal bir makine değildir, bu da bir [JIT](#jit)içermediğinden kod oluşturma ve çalıştırma tesislerini içermez.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-148">In contrast to the [CLR](#clr), CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="5fbfe-149">Ancak, [GC](#gc) ve çalışma zamanı türü tanımlama (rtti) ve yansıma özelliğini içerir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-149">It does, however, include the [GC](#gc) and the ability for run-time type identification (RTTI) and reflection.</span></span> <span data-ttu-id="5fbfe-150">Ancak, tür sistemi yansıma için meta verilerin gerekli olmaması için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-150">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="5fbfe-151">Meta verilerin gerekli olmaması, gereksiz meta verileri bağlayabilen bir [AOT](#aot) araç zinciri olmasını ve (daha önemlisi) uygulamanın kullanmayan kodu belirlemenizi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-151">Not requiring metadata enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="5fbfe-152">CoreRT geliştirme aşamasındadır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-152">CoreRT is in development.</span></span>

<span data-ttu-id="5fbfe-153">[.NET Native ve CoreRT Için tanıtım](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-153">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md).</span></span>

## <a name="cross-platform"></a><span data-ttu-id="5fbfe-154">platformlar arası</span><span class="sxs-lookup"><span data-stu-id="5fbfe-154">cross-platform</span></span>

<span data-ttu-id="5fbfe-155">Her biri için özel olarak yeniden yazmak zorunda kalmadan, Linux, Windows ve iOS gibi birden çok farklı işletim sisteminde kullanılabilen bir uygulamayı geliştirebilir ve yürütebilme özelliği.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-155">The ability to develop and execute an application that can be used on multiple different operating systems, such as Linux, Windows, and iOS, without having to rewrite specifically for each one.</span></span> <span data-ttu-id="5fbfe-156">Bu, farklı platformlardaki uygulamalar arasında kod yeniden kullanımını ve tutarlılığı sunar.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-156">This enables code reuse and consistency between applications on different platforms.</span></span>

## <a name="ecosystem"></a><span data-ttu-id="5fbfe-157">ekosistemi</span><span class="sxs-lookup"><span data-stu-id="5fbfe-157">ecosystem</span></span>

<span data-ttu-id="5fbfe-158">Belirli bir teknoloji için uygulama derlemek ve çalıştırmak için kullanılan tüm çalışma zamanı yazılımları, geliştirme araçları ve topluluk kaynakları.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-158">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="5fbfe-159">".NET ekosistemi" terimi, üçüncü taraf uygulama ve kitaplıkları dahil olmak üzere ".NET Stack" gibi benzer terimlerden farklıdır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-159">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="5fbfe-160">Tümcede bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5fbfe-160">Here's an example in a sentence:</span></span>

- <span data-ttu-id="5fbfe-161">" [.NET Standard](#net-standard) arkasındaki mosyon, .net ekosisteminde daha fazla esneklik sağlamak."</span><span class="sxs-lookup"><span data-stu-id="5fbfe-161">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span>

## <a name="framework"></a><span data-ttu-id="5fbfe-162">çerçeve</span><span class="sxs-lookup"><span data-stu-id="5fbfe-162">framework</span></span>

<span data-ttu-id="5fbfe-163">Genel olarak, belirli bir teknolojiyi temel alan uygulamaların geliştirilmesini ve dağıtılmasını kolaylaştıran kapsamlı bir API koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-163">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="5fbfe-164">Bu genel anlamda, ASP.NET Core ve Windows Forms uygulama çerçevelerinin örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-164">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="5fbfe-165">Ayrıca bkz. [kitaplık](#library).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-165">See also [library](#library).</span></span>

<span data-ttu-id="5fbfe-166">"Framework" sözcüğünün aşağıdaki koşullarda farklı anlamları vardır:</span><span class="sxs-lookup"><span data-stu-id="5fbfe-166">The word "framework" has a different meaning in the following terms:</span></span>

- [<span data-ttu-id="5fbfe-167">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5fbfe-167">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="5fbfe-168">hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="5fbfe-168">target framework</span></span>](#target-framework)
- [<span data-ttu-id="5fbfe-169">TFD (hedef çerçeve bilinen adı)</span><span class="sxs-lookup"><span data-stu-id="5fbfe-169">TFM (target framework moniker)</span></span>](#tfm)
- [<span data-ttu-id="5fbfe-170">çerçeveye bağımlı uygulama</span><span class="sxs-lookup"><span data-stu-id="5fbfe-170">framework-dependent app</span></span>](../core/deploying/index.md#publish-framework-dependent)

<span data-ttu-id="5fbfe-171">Eski .NET belgelerinde, "Framework" Bazen bir [.NET uygulamasını](#implementation-of-net)ifade eder.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-171">In legacy .NET documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="5fbfe-172">Örneğin, bir makale bir Framework .NET 5 ' i çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-172">For example, an article may call .NET 5 a framework.</span></span>

## <a name="gc"></a><span data-ttu-id="5fbfe-173">GC</span><span class="sxs-lookup"><span data-stu-id="5fbfe-173">GC</span></span>

<span data-ttu-id="5fbfe-174">Çöp toplayıcı.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-174">Garbage collector.</span></span>

<span data-ttu-id="5fbfe-175">Çöp toplayıcı, otomatik bellek yönetiminin bir uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-175">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="5fbfe-176">GC, artık kullanılmayan nesnelerin kapladığı belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-176">The GC frees memory occupied by objects that are no longer in use.</span></span>

<span data-ttu-id="5fbfe-177">Bkz. [çöp toplama](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-177">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="5fbfe-178">IL</span><span class="sxs-lookup"><span data-stu-id="5fbfe-178">IL</span></span>

<span data-ttu-id="5fbfe-179">Ara dil.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-179">Intermediate language.</span></span>

<span data-ttu-id="5fbfe-180">C# gibi daha üst düzey .NET dilleri, ara dil (IL) olarak adlandırılan donanımdan bağımsız bir yönerge kümesine derler.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-180">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="5fbfe-181">Il bazen MSIL (Microsoft Il) veya CıL (ortak Il) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-181">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="5fbfe-182">JIT</span><span class="sxs-lookup"><span data-stu-id="5fbfe-182">JIT</span></span>

<span data-ttu-id="5fbfe-183">Just-In-Time derleyicisi.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-183">Just-in-time compiler.</span></span>

<span data-ttu-id="5fbfe-184">[AOT](#aot)'ye benzer şekilde, bu derleyici [Il](#il) 'yi işlemcinin anladığı makine koduna dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-184">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="5fbfe-185">AOT 'nin aksine JıT derleme isteğe bağlı olur ve kodun üzerinde çalışması gereken makinede gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-185">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="5fbfe-186">Uygulamanın yürütülmesi sırasında JıT derlemesi gerçekleşdiğinden, derleme süresi çalışma zamanının bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-186">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="5fbfe-187">Bu nedenle, JıT derleyicileri, kodu en iyi duruma getirmeye harcanan süreyi, sonuçta elde edilen kodun üretebildiği tasarruflarla dengelemeye yönelik</span><span class="sxs-lookup"><span data-stu-id="5fbfe-187">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="5fbfe-188">Ancak, bir JıT gerçek donanımı bilir ve geliştiricilerin farklı uygulamalar sunmalarını ücretsiz olarak kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-188">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="5fbfe-189">.NET uygulama</span><span class="sxs-lookup"><span data-stu-id="5fbfe-189">implementation of .NET</span></span>

<span data-ttu-id="5fbfe-190">.NET uygulamasının şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="5fbfe-190">An implementation of .NET includes:</span></span>

- <span data-ttu-id="5fbfe-191">Bir veya daha fazla çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-191">One or more runtimes.</span></span> <span data-ttu-id="5fbfe-192">Örnekler: [clr](#clr), [corert](#corert).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-192">Examples: [CLR](#clr), [CoreRT](#corert).</span></span>
- <span data-ttu-id="5fbfe-193">.NET Standard bir sürümünü uygulayan ve ek API 'Ler içerebilen bir sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-193">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="5fbfe-194">Örnekler: [.NET Framework](#net-framework) ve [.NET 5 (ve .NET Core) ve sonraki sürümler](#net-5-and-later-versions)için [BCls](#bcl) .</span><span class="sxs-lookup"><span data-stu-id="5fbfe-194">Examples: the [BCLs](#bcl) for [.NET Framework](#net-framework) and [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span>
- <span data-ttu-id="5fbfe-195">İsteğe bağlı olarak, bir veya daha fazla uygulama çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-195">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="5fbfe-196">Örnekler: [ASP.net](#aspnet), WINDOWS Forms ve WPF, .NET Framework ve .NET 5 ' de yer almaktadır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-196">Examples: [ASP.NET](#aspnet), Windows Forms, and WPF are included in the .NET Framework and .NET 5.</span></span>
- <span data-ttu-id="5fbfe-197">İsteğe bağlı olarak, geliştirme araçları.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-197">Optionally, development tools.</span></span> <span data-ttu-id="5fbfe-198">Bazı geliştirme araçları birden çok uygulama arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-198">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="5fbfe-199">.NET uygulamalarına örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="5fbfe-199">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="5fbfe-200">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5fbfe-200">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="5fbfe-201">.NET 5 ve sonraki sürümleri (.NET Core 2.1-3.1 dahil)</span><span class="sxs-lookup"><span data-stu-id="5fbfe-201">.NET 5 and later versions (including .NET Core 2.1-3.1</span></span>](#net-5-and-later-versions)
- [<span data-ttu-id="5fbfe-202">Evrensel Windows Platformu (UWP)</span><span class="sxs-lookup"><span data-stu-id="5fbfe-202">Universal Windows Platform (UWP)</span></span>](#uwp)
- [<span data-ttu-id="5fbfe-203">Mono</span><span class="sxs-lookup"><span data-stu-id="5fbfe-203">Mono</span></span>](#mono)

## <a name="library"></a><span data-ttu-id="5fbfe-204">kitaplık</span><span class="sxs-lookup"><span data-stu-id="5fbfe-204">library</span></span>

<span data-ttu-id="5fbfe-205">Uygulamalar veya diğer kitaplıklar tarafından çağrılabilen API 'lerin bir koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-205">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="5fbfe-206">Bir .NET kitaplığı, bir [veya daha fazla](#assembly)derlemeden oluşur.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-206">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="5fbfe-207">Sözcükler kitaplığı ve [Framework](#framework) genellikle terimler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-207">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="mono"></a><span data-ttu-id="5fbfe-208">Mono</span><span class="sxs-lookup"><span data-stu-id="5fbfe-208">Mono</span></span>

<span data-ttu-id="5fbfe-209">Mono, genellikle küçük bir çalışma zamanı gerektiğinde kullanılan açık kaynaklı, [platformlar arası](#cross-platform) bir .net uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-209">Mono is an open source, [cross-platform](#cross-platform) .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="5fbfe-210">Android, Mac, iOS, tvOS ve watchOS üzerinde Xamarin uygulamalarını güçlendirir ve öncelikle küçük bir ayak izi gerektiren uygulamalara odaklanılmıştır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-210">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS, and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="5fbfe-211">Şu anda yayımlanmış .NET Standard sürümlerinin tümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-211">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="5fbfe-212">Tarihsel olarak, mono .NET Framework daha büyük API 'sini uyguladık ve UNIX üzerinde en popüler yeteneklerin bazılarını öykünüyler.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-212">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="5fbfe-213">Bu özellik bazen UNIX üzerinde bu özellikleri kullanan .NET uygulamalarını çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-213">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="5fbfe-214">Mono genellikle tam [zamanında bir derleyici](#jit)ile kullanılır, ancak iOS gibi platformlarda kullanılan tam bir [statik derleyici (güncel derleme)](#aot) da sunar.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-214">Mono is typically used with a [just-in-time compiler](#jit), but it also features a full [static compiler (ahead-of-time compilation)](#aot) that is used on platforms like iOS.</span></span>

<span data-ttu-id="5fbfe-215">[Mono belgelerine](https://www.mono-project.com/docs/)bakın.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-215">See the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="5fbfe-216">.NET</span><span class="sxs-lookup"><span data-stu-id="5fbfe-216">.NET</span></span>

<span data-ttu-id="5fbfe-217">[.NET Standard](#net-standard) ve tüm [.NET uygulamaları](#implementation-of-net) ve iş yükleri için şemsiye terimi.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-217">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="5fbfe-218">Her zaman tamamen büyük harf, hiçbir zaman ".net".</span><span class="sxs-lookup"><span data-stu-id="5fbfe-218">Always fully capitalized, never ".Net".</span></span>

<span data-ttu-id="5fbfe-219">[.NET 5](#net-5-and-later-versions) (Şu anda önizleme aşamasında) yayınlanmışsa, tüm yeni .NET geliştirme işlemleri için önerilen .NET uygulamaları olacaktır ve bu nedenle ".net" bazı bağlamlarda ".NET 5 ve sonraki sürümler" anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-219">When [.NET 5](#net-5-and-later-versions) (currently in preview) is released, it will be the recommended .NET implementation for all new .NET development, and so in some contexts ".NET" will imply ".NET 5 and later versions."</span></span>

<span data-ttu-id="5fbfe-220">Bkz. [.net temelleri](../fundamentals/index.yml)</span><span class="sxs-lookup"><span data-stu-id="5fbfe-220">See [.NET fundamentals](../fundamentals/index.yml)</span></span>

## <a name="net-5-and-later-versions"></a><span data-ttu-id="5fbfe-221">.NET 5 ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="5fbfe-221">.NET 5 and later versions</span></span>

<span data-ttu-id="5fbfe-222">.NET için platformlar arası, yüksek performanslı, açık kaynaklı bir uygulama.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-222">A cross-platform, high-performance, open-source implementation of .NET.</span></span> <span data-ttu-id="5fbfe-223">Ortak dil çalışma zamanı ([clr](#clr)), bir [AOT](#aot) çalışma[zamanı (,](#corert)geliştirme aşamasında), bir temel sınıf KITAPLıĞı ([BCL](#bcl)) ve [.NET SDK](#net-sdk)içerir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-223">Includes a Common Language Runtime ([CLR](#clr)), an [AOT](#aot) runtime ([CoreRT](#corert), in development), a Base Class Library ([BCL](#bcl)), and the [.NET SDK](#net-sdk).</span></span>

<span data-ttu-id="5fbfe-224">Bu .NET uygulamasının önceki sürümleri .NET Core olarak bilinir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-224">Earlier versions of this .NET implementation are known as .NET Core.</span></span> <span data-ttu-id="5fbfe-225">.NET 5,0, .NET Core 3,1 ' ü izleyen bir sonraki sürümdür.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-225">.NET 5.0 is the next version following .NET Core 3.1.</span></span> <span data-ttu-id="5fbfe-226">Sürüm 4, daha yeni bir .NET uygulamasının [.NET Framework](#net-framework)olarak bilinen eski uygulamayla karışmasını önlemek için atlandı.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-226">Version 4 was skipped to avoid confusing this newer implementation of .NET with the older implementation that is known as [.NET Framework](#net-framework).</span></span> <span data-ttu-id="5fbfe-227">.NET Framework geçerli sürümü 4,8 ' dir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-227">The current version of .NET Framework is 4.8.</span></span>

<span data-ttu-id="5fbfe-228">Bkz. [.net temelleri](../fundamentals/index.yml).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-228">See [.NET fundamentals](../fundamentals/index.yml).</span></span>

## <a name="net-cli"></a><span data-ttu-id="5fbfe-229">.NET CLı</span><span class="sxs-lookup"><span data-stu-id="5fbfe-229">.NET CLI</span></span>

<span data-ttu-id="5fbfe-230">[.NET 5 (ve .NET Core) ve sonraki sürümler](#net-5-and-later-versions)için uygulama ve kitaplıklar geliştirmeye yönelik platformlar arası araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-230">A cross-platform toolchain for developing applications and libraries for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span> <span data-ttu-id="5fbfe-231">.NET Core CLI olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-231">Also known as the .NET Core CLI.</span></span>

<span data-ttu-id="5fbfe-232">Bkz. [.net CLI](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-232">See [.NET CLI](../core/tools/index.md).</span></span>

## <a name="net-core"></a><span data-ttu-id="5fbfe-233">.NET Core</span><span class="sxs-lookup"><span data-stu-id="5fbfe-233">.NET Core</span></span>

<span data-ttu-id="5fbfe-234">Bkz. [.NET 5 ve sonraki sürümler](#net-5-and-later-versions).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-234">See [.NET 5 and later versions](#net-5-and-later-versions).</span></span>

## <a name="net-framework"></a><span data-ttu-id="5fbfe-235">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="5fbfe-235">.NET Framework</span></span>

<span data-ttu-id="5fbfe-236">Yalnızca Windows üzerinde çalışan bir .NET uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-236">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="5fbfe-237">Ortak dil çalışma zamanını ([clr](#clr)), temel sınıf kitaplığını ([BCL](#bcl)) ve [ASP.net](#aspnet), Windows Forms ve WPF gibi uygulama çerçevesi kitaplıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-237">Includes the Common Language Runtime ([CLR](#clr)), the Base Class Library ([BCL](#bcl)), and application framework libraries such as [ASP.NET](#aspnet), Windows Forms, and WPF.</span></span>

<span data-ttu-id="5fbfe-238">[.NET Framework Kılavuzu](../framework/index.yml)' na bakın.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-238">See [.NET Framework Guide](../framework/index.yml).</span></span>

## <a name="net-native"></a><span data-ttu-id="5fbfe-239">.NET Yerel</span><span class="sxs-lookup"><span data-stu-id="5fbfe-239">.NET Native</span></span>

<span data-ttu-id="5fbfe-240">Anında yerel kod üreten bir derleyici aracı zinciri ([AOT](#aot))-ın-Time ([JIT](#jit)) yerine.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-240">A compiler tool chain that produces native code ahead-of-time ([AOT](#aot)), as opposed to just-in-time ([JIT](#jit)).</span></span>

<span data-ttu-id="5fbfe-241">Derleme, geliştirici makinesinde C++ derleyicisinin ve bağlayıcının çalışmasına benzer şekilde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-241">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="5fbfe-242">Kullanılmayan kodu kaldırır ve iyileştirerek daha fazla zaman harcamalar.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-242">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="5fbfe-243">Kodu kitaplıklardan ayıklar ve çalıştırılabilirle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-243">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="5fbfe-244">Sonuç, uygulamanın tamamını temsil eden tek bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-244">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="5fbfe-245">UWP, .NET Native tarafından desteklenen ilk uygulama çerçevesidir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-245">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="5fbfe-246">Şimdi Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekliyoruz.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-246">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="5fbfe-247">[.NET Native ve CoreRT tanıtımı](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md) konusuna bakın</span><span class="sxs-lookup"><span data-stu-id="5fbfe-247">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-sdk"></a><span data-ttu-id="5fbfe-248">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="5fbfe-248">.NET SDK</span></span>

<span data-ttu-id="5fbfe-249">Geliştiricilerin [.NET 5 (ve .NET Core) ve sonraki sürümler](#net-5-and-later-versions)için .NET uygulamaları ve kitaplıkları oluşturmalarına izin veren bir kitaplıklar ve araçlar kümesi.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-249">A set of libraries and tools that allow developers to create .NET applications and libraries for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span> <span data-ttu-id="5fbfe-250">.NET Core SDK olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-250">Also known as the .NET Core SDK.</span></span>

<span data-ttu-id="5fbfe-251">Uygulamalar oluşturmaya yönelik [.net CLI](#net-cli) , uygulamalar oluşturmak ve çalıştırmak için .NET, .NET kitaplıkları ve çalışma zamanı ve CLI komutlarını çalıştıran ve uygulamaları çalıştıran DotNet çalıştırılabilir (*dotnet.exe*) içerir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-251">Includes the [.NET CLI](#net-cli) for building apps, .NET libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="5fbfe-252">Bkz. [.NET SDK 'Ya genel bakış](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-252">See [.NET SDK Overview](../core/sdk.md).</span></span>

## <a name="net-standard"></a><span data-ttu-id="5fbfe-253">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="5fbfe-253">.NET Standard</span></span>

<span data-ttu-id="5fbfe-254">.NET API 'lerinin her bir .NET uygulamasında kullanılabilen resmi bir belirtimi.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-254">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="5fbfe-255">.NET Standard belirtimine bazen belgelerde bir kitaplık denir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-255">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="5fbfe-256">Bir kitaplık yalnızca belirtim (arabirimler) değil API uygulamalarını içerdiğinden, bir "Library" .NET Standard çağırmak yanıltıcıdır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-256">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span>

<span data-ttu-id="5fbfe-257">Bkz. [.NET Standard](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-257">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="5fbfe-258">NGEN</span><span class="sxs-lookup"><span data-stu-id="5fbfe-258">NGEN</span></span>

<span data-ttu-id="5fbfe-259">Yerel (görüntü) oluşturma.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-259">Native (image) generation.</span></span>

<span data-ttu-id="5fbfe-260">Bu teknolojiyi kalıcı bir [JIT](#jit) derleyicisi olarak düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-260">You can think of this technology as a persistent [JIT](#jit) compiler.</span></span> <span data-ttu-id="5fbfe-261">Genellikle kodun yürütüldüğü makinede kodu derler, ancak derleme genellikle yüklemesi sırasında gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-261">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="5fbfe-262">leyebilir</span><span class="sxs-lookup"><span data-stu-id="5fbfe-262">package</span></span>

<span data-ttu-id="5fbfe-263">Bir NuGet paketi &mdash; veya yalnızca bir paket &mdash; , aynı ada sahip bir veya daha fazla bütünleştirilmiş kod içeren bir *. zip* dosyasıdır ve yazar adı gibi ek meta verilerle birlikte.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-263">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="5fbfe-264">*. Zip* dosyası *. nupkg* uzantısına sahiptir ve birden çok hedef çerçeve ve sürümde kullanılmak üzere *. dll* dosyaları ve *. xml* dosyaları gibi varlıkları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-264">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="5fbfe-265">Bir uygulama veya kitaplığa yüklendiğinde, uygun varlıklar uygulama veya kitaplık tarafından belirtilen hedef çerçeveye göre seçilir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-265">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="5fbfe-266">Arabirimi tanımlayan varlıklar *ref* klasöründedir ve uygulamayı tanımlayan varlıklar *lib* klasöründedir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-266">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="5fbfe-267">platform</span><span class="sxs-lookup"><span data-stu-id="5fbfe-267">platform</span></span>

<span data-ttu-id="5fbfe-268">Windows, macOS, Linux, iOS ve Android gibi bir işletim sistemi ve üzerinde çalıştığı donanım.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-268">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="5fbfe-269">Cümlelerde kullanım örnekleri aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5fbfe-269">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="5fbfe-270">".NET Core, .NET 'in platformlar arası bir uygulamasıdır."</span><span class="sxs-lookup"><span data-stu-id="5fbfe-270">".NET Core is a cross-platform implementation of .NET."</span></span>
- <span data-ttu-id="5fbfe-271">"PCL profilleri Microsoft platformlarını temsil ederken .NET Standard platforma göre belirsizdir."</span><span class="sxs-lookup"><span data-stu-id="5fbfe-271">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="5fbfe-272">Eski .NET belgeleri bazen .NET veya .NET [Stack](#stack) 'in tüm uygulamalar dahil bir [uygulamasını](#implementation-of-net) ifade etmek için ".NET platformu" kullanır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-272">Legacy .NET documentation sometimes uses ".NET platform" to mean either an [implementation of .NET](#implementation-of-net) or the .NET [stack](#stack) including all implementations.</span></span> <span data-ttu-id="5fbfe-273">Bu kullanımların her ikisi de birincil (OS/donanım) anlamını aşmaya eğilimlidir, bu nedenle bu kullanımlardan kaçınmaya çalışırız.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-273">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we try to avoid these usages.</span></span>

<span data-ttu-id="5fbfe-274">"Platform" ifadesi, uygulama oluşturmak ve çalıştırmak için araçlar ve kitaplıklar sağlayan yazılıma işaret eden "geliştirici platformu" cümlecide farklı anlamdadır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-274">"Platform" has a different meaning in the phrase "developer platform," which refers to software that provides tools and libraries for building and running apps.</span></span> <span data-ttu-id="5fbfe-275">.NET, birçok farklı uygulama türü oluşturmak için platformlar arası, açık kaynaklı bir geliştirici platformudur.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-275">.NET is a cross-platform, open source developer platform for building many different types of applications.</span></span>

## <a name="runtime"></a><span data-ttu-id="5fbfe-276">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="5fbfe-276">runtime</span></span>

<span data-ttu-id="5fbfe-277">Genel olarak, yönetilen programın yürütme ortamı.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-277">In general, the execution environment for a managed program.</span></span> <span data-ttu-id="5fbfe-278">İşletim sistemi çalışma zamanı ortamının bir parçasıdır ancak .NET çalışma zamanının bir parçası değildir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-278">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="5fbfe-279">İşte bu sözcüğün bu anlamda bazı .NET çalışma zamanları örnekleri verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="5fbfe-279">Here are some examples of .NET runtimes in this sense of the word:</span></span>

- <span data-ttu-id="5fbfe-280">Ortak dil çalışma zamanı ([clr](#clr))</span><span class="sxs-lookup"><span data-stu-id="5fbfe-280">Common Language Runtime ([CLR](#clr))</span></span>
- <span data-ttu-id="5fbfe-281">.NET Native (UWP için)</span><span class="sxs-lookup"><span data-stu-id="5fbfe-281">.NET Native (for UWP)</span></span>
- <span data-ttu-id="5fbfe-282">Mono çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="5fbfe-282">Mono runtime</span></span>

<span data-ttu-id="5fbfe-283">"Runtime" sözcüğünün aşağıdaki bağlamlarda farklı bir anlamı vardır:</span><span class="sxs-lookup"><span data-stu-id="5fbfe-283">The word "runtime" has a different meaning in the following contexts:</span></span>

* <span data-ttu-id="5fbfe-284">[.Net indirme sayfası](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-284">The [.NET download page](https://dotnet.microsoft.com/download).</span></span>

  <span data-ttu-id="5fbfe-285">Burada "Runtime" burada [clr](#clr) 'nin bir makineye indirip yükleyebilecekleri [BCL](#bcl) (çerçeve kitaplıkları) ile birlikte, makineye [bağlı](../core/deploying/index.md#publish-framework-dependent) uygulamaları makinede çalıştırabilmeniz için bir makineye indirebilir ve yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-285">"Runtime" here means the [CLR](#clr) together with the [BCL](#bcl) (framework libraries), that you can download and install on a machine so that you can run [framework-dependent](../core/deploying/index.md#publish-framework-dependent) apps on the machine.</span></span>

* <span data-ttu-id="5fbfe-286">[.NET 5 (ve .NET Core) ve sonraki sürümler](#net-5-and-later-versions)Için [çalışma zamanı tanımlayıcısı (RID)](../core/rid-catalog.md) .</span><span class="sxs-lookup"><span data-stu-id="5fbfe-286">The [Runtime Identifier (RID)](../core/rid-catalog.md) for [.NET 5 (and .NET Core) and later versions](#net-5-and-later-versions).</span></span>

  <span data-ttu-id="5fbfe-287">Burada "Runtime", .NET uygulamasının üzerinde çalıştığı işletim sistemi platformu ve CPU mimarisi anlamına gelir, örneğin: `linux-x64` .</span><span class="sxs-lookup"><span data-stu-id="5fbfe-287">"Runtime" here means the OS platform and CPU architecture that a .NET app runs on, for example: `linux-x64`.</span></span>

<span data-ttu-id="5fbfe-288">Eski .NET belgeleri bazen, aşağıdaki örneklerde olduğu gibi, [.NET uygulamasının bir uygulama](#implementation-of-net)açısından "Runtime" kullanır:</span><span class="sxs-lookup"><span data-stu-id="5fbfe-288">Legacy .NET documentation sometimes uses "runtime" in the sense of an [implementation of .NET](#implementation-of-net), as in the following examples:</span></span>

- <span data-ttu-id="5fbfe-289">"Çeşitli .NET çalışma zamanları .NET Standard belirli sürümlerini uygular."</span><span class="sxs-lookup"><span data-stu-id="5fbfe-289">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="5fbfe-290">"Birden çok çalışma zamanında çalıştırılması amaçlanan kitaplıkların bu çerçeveyi hedeflemesi gerekir."</span><span class="sxs-lookup"><span data-stu-id="5fbfe-290">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="5fbfe-291">(.NET Standard başvurma)</span><span class="sxs-lookup"><span data-stu-id="5fbfe-291">(referring to .NET Standard)</span></span>
- <span data-ttu-id="5fbfe-292">"Çeşitli .NET çalışma zamanları .NET Standard belirli sürümlerini uygular.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-292">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="5fbfe-293">…</span><span class="sxs-lookup"><span data-stu-id="5fbfe-293">…</span></span> <span data-ttu-id="5fbfe-294">Her .NET çalışma zamanı sürümü, desteklediği en yüksek .NET Standard sürümünü tanıtır... "</span><span class="sxs-lookup"><span data-stu-id="5fbfe-294">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

## <a name="stack"></a><span data-ttu-id="5fbfe-295">yığın</span><span class="sxs-lookup"><span data-stu-id="5fbfe-295">stack</span></span>

<span data-ttu-id="5fbfe-296">Uygulamaları derlemek ve çalıştırmak için birlikte kullanılan bir programlama teknolojileri kümesi.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-296">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="5fbfe-297">".NET Stack" .NET Standard ve tüm .NET uygulamalarını ifade eder.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-297">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="5fbfe-298">"A .NET Stack" ifadesi bir .NET uygulamasına başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-298">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span>

## <a name="target-framework"></a><span data-ttu-id="5fbfe-299">hedef çerçeve</span><span class="sxs-lookup"><span data-stu-id="5fbfe-299">target framework</span></span>

<span data-ttu-id="5fbfe-300">Bir .NET uygulamasının veya kitaplığının dayandığı API 'lerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-300">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="5fbfe-301">Bir uygulama veya kitaplık, tüm .NET uygulamalarında standartlaştırılmış bir API kümesine yönelik belirtim olan .NET Standard bir sürümünü (örneğin, .NET Standard 2,0) hedefleyebilir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-301">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is a specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="5fbfe-302">Bir uygulama veya kitaplık, belirli bir .NET uygulamasının bir sürümünü de hedefleyebilir ve bu durumda uygulamaya özgü API 'lere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-302">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="5fbfe-303">Örneğin, Xamarin. iOS 'u hedefleyen bir uygulama Xamarin tarafından sağlanmış iOS API sarmalayıcılarını erişim altına alır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-303">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="5fbfe-304">Bazı hedef çerçeveler için (örneğin, .NET Framework) kullanılabilir API 'ler, .NET uygulamasının uygulama çerçevesi API 'Leri içerebilen bir sisteme yüklediği derlemeler tarafından tanımlanır (örneğin, ASP.NET, WinForms).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-304">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="5fbfe-305">Paket tabanlı hedef çerçeveler için (.NET Standard ve .NET Core gibi), çerçeve API 'Leri, uygulama veya kitaplıkta yüklü paketler tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-305">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="5fbfe-306">Bu durumda, hedef çerçeve dolaylı olarak çerçeveyi oluşturan tüm paketlere başvuran bir paketi belirtir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-306">In that case, the target framework implicitly specifies a package that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="5fbfe-307">Bkz. [hedef çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-307">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="5fbfe-308">TFM</span><span class="sxs-lookup"><span data-stu-id="5fbfe-308">TFM</span></span>

<span data-ttu-id="5fbfe-309">Hedef Framework bilinen adı.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-309">Target framework moniker.</span></span>

<span data-ttu-id="5fbfe-310">.NET uygulaması veya kitaplığının hedef çerçevesini belirtmek için standartlaştırılmış bir belirteç biçimi.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-310">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="5fbfe-311">Hedef çerçevelere genellikle gibi kısa bir ad başvurulur `net462` .</span><span class="sxs-lookup"><span data-stu-id="5fbfe-311">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="5fbfe-312">Uzun biçimli TFMs (gibi. NETFramework, Version = 4.6.2) var, ancak genellikle bir hedef çerçeve belirtmek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-312">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="5fbfe-313">Bkz. [hedef çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="5fbfe-313">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="5fbfe-314">UWP</span><span class="sxs-lookup"><span data-stu-id="5fbfe-314">UWP</span></span>

<span data-ttu-id="5fbfe-315">Evrensel Windows Platformu.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-315">Universal Windows Platform.</span></span>

<span data-ttu-id="5fbfe-316">Nesnelerin İnterneti (IoT) için modern, dokunmatik özellikli Windows Uygulamaları ve yazılım oluşturmak için kullanılan bir .NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-316">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="5fbfe-317">Bilgisayar, tabletler, telefonlar ve hatta Xbox dahil olmak üzere hedeflemek isteyebileceğiniz farklı cihaz türlerini içerecek şekilde tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-317">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phones, and even the Xbox.</span></span> <span data-ttu-id="5fbfe-318">UWP, merkezi bir App Store, bir yürütme ortamı (AppContainer) ve Win32 (WinRT) yerine kullanılacak bir dizi Windows API 'si gibi birçok hizmeti sağlar.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-318">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="5fbfe-319">Uygulamalar C++, C#, Visual Basic ve JavaScript 'te yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-319">Apps can be written in C++, C#, Visual Basic, and JavaScript.</span></span> <span data-ttu-id="5fbfe-320">C# ve Visual Basic kullanılırken .NET API 'Leri .NET 5 (ve .NET Core) ve sonraki sürümler tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-320">When using C# and Visual Basic, the .NET APIs are provided by .NET 5 (and .NET Core) and later versions.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fbfe-321">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5fbfe-321">See also</span></span>

- [<span data-ttu-id="5fbfe-322">.NET temelleri</span><span class="sxs-lookup"><span data-stu-id="5fbfe-322">.NET fundamentals</span></span>](../fundamentals/index.yml)
- [<span data-ttu-id="5fbfe-323">.NET Framework Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5fbfe-323">.NET Framework Guide</span></span>](../framework/index.yml)
- [<span data-ttu-id="5fbfe-324">ASP.NET genel bakış</span><span class="sxs-lookup"><span data-stu-id="5fbfe-324">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)
- [<span data-ttu-id="5fbfe-325">ASP.NET Core genel bakış</span><span class="sxs-lookup"><span data-stu-id="5fbfe-325">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)
