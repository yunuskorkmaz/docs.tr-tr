---
title: .NET sözlüğü
description: .NET belgelerde kullanılan seçili koşulları anlamını öğrenin.
keywords: .NET sözlüğü, .NET sözlük, .NET terminolojisi, .NET platformu, .NET framework, .NET çalışma zamanı
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 33123732514a53574036f6f8e948b2cf9acb9229
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="net-glossary"></a><span data-ttu-id="ce380-104">.NET sözlüğü</span><span class="sxs-lookup"><span data-stu-id="ce380-104">.NET Glossary</span></span>

<span data-ttu-id="ce380-105">Birincil Bu sözlük anlamları seçili terimleri ve tanımları olmadan .NET belgelerinde sık görünen kısaltmalar açıklamak için hedefidir.</span><span class="sxs-lookup"><span data-stu-id="ce380-105">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="ce380-106">AOT</span><span class="sxs-lookup"><span data-stu-id="ce380-106">AOT</span></span>

<span data-ttu-id="ce380-107">Zaman tamamlanan derleyicisi.</span><span class="sxs-lookup"><span data-stu-id="ce380-107">Ahead-of-time compiler.</span></span>

<span data-ttu-id="ce380-108">Benzer şekilde [JIT](#jit), bu derleyici ayrıca çevirir [IL](#il) makine kodu.</span><span class="sxs-lookup"><span data-stu-id="ce380-108">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="ce380-109">Uygulama yürütülür ve genellikle farklı bir makineye gerçekleştirilen önce JIT derleme aksine, uygulama nesne AĞACI derleme olur.</span><span class="sxs-lookup"><span data-stu-id="ce380-109">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="ce380-110">Çalışma zamanında uygulama nesne AĞACI aracı zincirleri derleme yoktur çünkü harcanan süre derleme en aza indirmek yok.</span><span class="sxs-lookup"><span data-stu-id="ce380-110">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="ce380-111">Daha fazla zaman iyileştirme harcayabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ce380-111">That means they can spend more time optimizing.</span></span> <span data-ttu-id="ce380-112">Uygulama Nesne AĞACI bağlamında tüm uygulama olduğundan, uygulama nesne AĞACI derleyici çapraz modülü bağlama ve tüm başvuruları izlenir ve tek bir yürütülebilir dosya üretilen anlamına gelir tüm program analizi de gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ce380-112">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

## <a name="aspnet"></a><span data-ttu-id="ce380-113">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ce380-113">ASP.NET</span></span> 

<span data-ttu-id="ce380-114">.NET Framework ile birlikte gelen özgün ASP.NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="ce380-114">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="ce380-115">Bazen ASP.NET ASP.NET Core dahil olmak üzere iki ASP.NET uygulamaları başvuran bir genel bir terimdir.</span><span class="sxs-lookup"><span data-stu-id="ce380-115">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="ce380-116">Verilen örnek terimi taşıyan anlamı bağlam tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="ce380-116">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="ce380-117">Başvurmak için ASP.NET aldığınız temizleyin sağlamak istediğinizde 4.x değil kullanmakta olduğunuz ASP.NET hem uygulamaları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ce380-117">Refer to ASP.NET 4.x when you want to make it clear that you’re not using ASP.NET to mean both implementations.</span></span> 

<span data-ttu-id="ce380-118">Bkz: [ASP.NET belgelerine](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="ce380-118">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="ce380-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce380-119">ASP.NET Core</span></span>

<span data-ttu-id="ce380-120">Bir platformlar arası, yüksek performanslı, açık kaynak uygulaması, ASP .NET Core üzerinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="ce380-120">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="ce380-121">Bkz: [ASP.NET Core belgeleri](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="ce380-121">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="ce380-122">derleme</span><span class="sxs-lookup"><span data-stu-id="ce380-122">assembly</span></span>

<span data-ttu-id="ce380-123">A *.dll*/*.exe* uygulamaları veya diğer derlemelerden tarafından çağrılabilir API'leri koleksiyonunu içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="ce380-123">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by apps or other assemblies.</span></span>

<span data-ttu-id="ce380-124">Bir derlemeyi arabirimleri, sınıflar, yapılar, numaralandırmalar ve temsilciler gibi türlerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ce380-124">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="ce380-125">Bir projenin derlemelerde *bin* klasörü bazen denir *ikili dosyaları*.</span><span class="sxs-lookup"><span data-stu-id="ce380-125">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="ce380-126">Ayrıca bkz. [Kitaplığı](#library).</span><span class="sxs-lookup"><span data-stu-id="ce380-126">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="ce380-127">CLR</span><span class="sxs-lookup"><span data-stu-id="ce380-127">CLR</span></span>

<span data-ttu-id="ce380-128">Ortak dil çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="ce380-128">Common Language Runtime.</span></span>

<span data-ttu-id="ce380-129">Bağlama, tam anlamını bağlıdır, ancak bu genellikle .NET Framework çalışma zamanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce380-129">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="ce380-130">Bellek ayırma ve yönetim CLR işler.</span><span class="sxs-lookup"><span data-stu-id="ce380-130">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="ce380-131">CLR ayrıca yalnızca uygulamaları yürütülen ancak aynı zamanda oluşturur ve kod üzerinde-JIT Derleyici kullanarak çalışma sırasında derlenen bir sanal makine bulunuyor.</span><span class="sxs-lookup"><span data-stu-id="ce380-131">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a JIT compiler.</span></span> <span data-ttu-id="ce380-132">Geçerli Microsoft CLR Windows yalnızca uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ce380-132">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="ce380-133">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="ce380-133">CoreCLR</span></span>

<span data-ttu-id="ce380-134">.NET core ortak dil çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="ce380-134">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="ce380-135">Bu CLR aynı kod CLR tabanını oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ce380-135">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="ce380-136">İlk olarak, CoreCLR Silverlight'ın çalışma zamanı olan ve birden çok platformda çalışacak biçimde tasarlanan, özellikle Windows ve OS x CoreCLR şimdi parçası .NET Core ve CLR basitleştirilmiş bir sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="ce380-136">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="ce380-137">Bu hala şimdi birçok Linux dağıtımları için destek dahil olmak üzere bir platformlar arası çalışma zamanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce380-137">It's still a cross platform runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="ce380-138">Ayrıca CoreCLR JIT ve kod yürütme özelliklerine sahip bir sanal makine ' dir.</span><span class="sxs-lookup"><span data-stu-id="ce380-138">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="ce380-139">CoreFX</span><span class="sxs-lookup"><span data-stu-id="ce380-139">CoreFX</span></span>

<span data-ttu-id="ce380-140">.NET core temel sınıf kitaplığı (BCL)</span><span class="sxs-lookup"><span data-stu-id="ce380-140">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="ce380-141">Set System.* oluşturan kitaplıkları'nın (ve sınırlı ölçüde Microsoft.*) ad alanları.</span><span class="sxs-lookup"><span data-stu-id="ce380-141">A set of libraries that comprise the System.* (and to a limited extent  Microsoft.*) namespaces.</span></span> <span data-ttu-id="ce380-142">BCL genel amaçlı, ASP.NET Core gibi daha üst düzey uygulama çerçeveleri derleme üzerinde alt düzey framework olur.</span><span class="sxs-lookup"><span data-stu-id="ce380-142">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="ce380-143">.NET Core BCL kaynak kodunu yer [CoreFX depo](https://github.com/dotnet/corefx).</span><span class="sxs-lookup"><span data-stu-id="ce380-143">The source code of the .NET Core BCL is contained in the [CoreFX repository](https://github.com/dotnet/corefx).</span></span> <span data-ttu-id="ce380-144">Ancak, .NET Core API'ları çoğunluğu kullanılabilir de .NET Framework şekilde CoreFX bir .NET Framework BCL çatalı düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce380-144">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="ce380-145">CoreRT</span><span class="sxs-lookup"><span data-stu-id="ce380-145">CoreRT</span></span>

<span data-ttu-id="ce380-146">.NET çekirdeği çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="ce380-146">.NET Core runtime.</span></span>

<span data-ttu-id="ce380-147">CLR/CoreCLR aksine CoreRT oluşturmak ve bunu içermediği için kod üzerinde-çalışma sırasında çalıştırmak için kullanılan olanakları içermez anlamına gelen bir sanal makine, değil bir [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="ce380-147">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="ce380-148">Ancak, içerir [GC](#gc) ve çalışma zamanı tür kimliği (RTTI) ve yansıma yeteneği.</span><span class="sxs-lookup"><span data-stu-id="ce380-148">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="ce380-149">Ancak, böylece meta verilerini yansıma için gerekli değildir, tür sistemi tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ce380-149">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="ce380-150">Bu sahip sağlayan bir [Uygulama Nesne AĞACI](#aot) aracı koyma gereksiz meta veri bağlantı ve uygulama kullanmayan kodu (daha da önemlisi) tanımlamak zinciri.</span><span class="sxs-lookup"><span data-stu-id="ce380-150">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="ce380-151">CoreRT geliştirme ' dir.</span><span class="sxs-lookup"><span data-stu-id="ce380-151">CoreRT is in development.</span></span>

<span data-ttu-id="ce380-152">Bkz: [.NET yerel ve CoreRT giriş](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="ce380-152">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="ecosystem"></a><span data-ttu-id="ce380-153">ekosistemi</span><span class="sxs-lookup"><span data-stu-id="ce380-153">ecosystem</span></span>

<span data-ttu-id="ce380-154">Tüm çalışma zamanı yazılım, geliştirme araçları ve oluşturmak ve belirli bir teknolojinin uygulamaları çalıştırmak için kullanılan topluluk kaynakları.</span><span class="sxs-lookup"><span data-stu-id="ce380-154">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="ce380-155">".NET ekosistemi" terimi ".NET yığını" gibi benzer terimler, üçüncü taraf uygulamaların ve kitaplıkları, kataloğa farklıdır.</span><span class="sxs-lookup"><span data-stu-id="ce380-155">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="ce380-156">Bir tümcedeki örneği şöyledir:</span><span class="sxs-lookup"><span data-stu-id="ce380-156">Here's an example in a sentence:</span></span>

- <span data-ttu-id="ce380-157">"Arkasında motivasyon [.NET standart](#net-standard) .NET ekosistemi büyük bütünlüğünü oluşturmaktır."</span><span class="sxs-lookup"><span data-stu-id="ce380-157">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span> 

## <a name="framework"></a><span data-ttu-id="ce380-158">çerçeve</span><span class="sxs-lookup"><span data-stu-id="ce380-158">framework</span></span>

<span data-ttu-id="ce380-159">Genel olarak, geniş kapsamlı bir koleksiyon API'leri, geliştirme ve belirli teknolojiye dayalı uygulamalarının dağıtımını hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="ce380-159">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="ce380-160">Bu genel olarak, ASP.NET Core ve Windows Forms uygulama çerçeveleri örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="ce380-160">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="ce380-161">Ayrıca bkz. [Kitaplığı](#library).</span><span class="sxs-lookup"><span data-stu-id="ce380-161">See also [library](#library).</span></span>

<span data-ttu-id="ce380-162">"Framework" sözcüğünü aşağıdaki terimler içinde daha belirgin bir teknik anlam sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ce380-162">The word "framework" has a more specific technical meaning in the following terms:</span></span>
* [<span data-ttu-id="ce380-163">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="ce380-163">.NET Framework</span></span>](#net-framework)
* [<span data-ttu-id="ce380-164">hedef çerçevesi</span><span class="sxs-lookup"><span data-stu-id="ce380-164">target framework</span></span>](#target-framework)
* [<span data-ttu-id="ce380-165">TFM (hedef framework takma ad)</span><span class="sxs-lookup"><span data-stu-id="ce380-165">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="ce380-166">Varolan belgelerde başvurduğu bazen "framework" bir [.NET uygulaması](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="ce380-166">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="ce380-167">Örneğin, bir makale bir çerçeve .NET Core çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="ce380-167">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="ce380-168">Bu karmaşık kullanım belgelerindeki ortadan planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="ce380-168">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="ce380-169">GC</span><span class="sxs-lookup"><span data-stu-id="ce380-169">GC</span></span>

<span data-ttu-id="ce380-170">Çöp toplayıcı.</span><span class="sxs-lookup"><span data-stu-id="ce380-170">Garbage collector.</span></span>

<span data-ttu-id="ce380-171">Çöp toplayıcı otomatik bellek yönetimi uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ce380-171">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="ce380-172">GC artık kullanımda olmayan nesneler tarafından kullanılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="ce380-172">The GC frees memory occupied by objects that are no longer in use.</span></span> 

<span data-ttu-id="ce380-173">Bkz: [çöp toplama](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce380-173">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="ce380-174">IL</span><span class="sxs-lookup"><span data-stu-id="ce380-174">IL</span></span>

<span data-ttu-id="ce380-175">Ara dil.</span><span class="sxs-lookup"><span data-stu-id="ce380-175">Intermediate language.</span></span>

<span data-ttu-id="ce380-176">C# gibi daha üst düzey .NET dilleri Ara dile (IL) olarak adlandırılır ve donanım belirsiz yönerge kümesi aşağıya doğru derleyin.</span><span class="sxs-lookup"><span data-stu-id="ce380-176">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="ce380-177">IL bazen MSIL (Microsoft IL) veya CIL (ortak IL) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ce380-177">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="ce380-178">JIT</span><span class="sxs-lookup"><span data-stu-id="ce380-178">JIT</span></span>

<span data-ttu-id="ce380-179">Yalnızca zaman derleyicisi.</span><span class="sxs-lookup"><span data-stu-id="ce380-179">Just-in-time compiler.</span></span>

<span data-ttu-id="ce380-180">Benzer şekilde [Uygulama Nesne AĞACI](#aot), bu derleyici çevirir [IL](#il) işlemci anlar makine kodu.</span><span class="sxs-lookup"><span data-stu-id="ce380-180">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="ce380-181">Uygulama Nesne AĞACI, aksine JIT derleme isteğe bağlı olur ve kodu çalıştırmak için gereken aynı makine üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ce380-181">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="ce380-182">JIT derleme uygulama yürütme sırasında oluştuğunda gerçekleştiğinden derleme zamanında çalışma zamanında bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="ce380-182">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="ce380-183">Bu nedenle, zamanın en iyi duruma getirme kodu ortaya çıkan kodu oluşturmak üzere tasarrufları karşı dengelemek JIT derleyicileri sahip.</span><span class="sxs-lookup"><span data-stu-id="ce380-183">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="ce380-184">Ancak bir JIT gerçek donanım bilir ve farklı uygulamaları sevk gerek kalmadan gelen geliştiriciler boş.</span><span class="sxs-lookup"><span data-stu-id="ce380-184">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="ce380-185">.NET uygulaması</span><span class="sxs-lookup"><span data-stu-id="ce380-185">implementation of .NET</span></span>

<span data-ttu-id="ce380-186">.NET uygulaması aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="ce380-186">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="ce380-187">Bir veya daha fazla çalışma zamanları.</span><span class="sxs-lookup"><span data-stu-id="ce380-187">One or more runtimes.</span></span> <span data-ttu-id="ce380-188">Örnekler: CLR, CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="ce380-188">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="ce380-189">.NET standart sürümü uygular ve ek API'leri içerebilir sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="ce380-189">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="ce380-190">Örnekler: .NET Framework temel sınıf kitaplığı, .NET Core temel sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="ce380-190">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="ce380-191">İsteğe bağlı olarak, bir veya daha fazla uygulama çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="ce380-191">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="ce380-192">Örnekler: ASP.NET, Windows Forms ve WPF .NET Framework dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="ce380-192">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="ce380-193">İsteğe bağlı olarak, geliştirme araçları.</span><span class="sxs-lookup"><span data-stu-id="ce380-193">Optionally, development tools.</span></span> <span data-ttu-id="ce380-194">Bazı geliştirme araçları birden çok uygulamalar arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="ce380-194">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="ce380-195">.NET uygulamaları örnekleri:</span><span class="sxs-lookup"><span data-stu-id="ce380-195">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="ce380-196">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="ce380-196">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="ce380-197">.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce380-197">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="ce380-198">Evrensel Windows Platformu (UWP)</span><span class="sxs-lookup"><span data-stu-id="ce380-198">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="ce380-199">kitaplık</span><span class="sxs-lookup"><span data-stu-id="ce380-199">library</span></span>

<span data-ttu-id="ce380-200">Uygulamaları veya diğer kitaplıkları tarafından çağrılabilir API'leri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ce380-200">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="ce380-201">Bir veya daha fazla .NET kitaplığı oluşan [derlemeler](#assembly).</span><span class="sxs-lookup"><span data-stu-id="ce380-201">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="ce380-202">Sözcükler kitaplığı ve [framework](#framework) genellikle maliyetle aynı anlamda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce380-202">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="ce380-203">metapackage</span><span class="sxs-lookup"><span data-stu-id="ce380-203">metapackage</span></span>

<span data-ttu-id="ce380-204">Kendi ancak hiçbir kitaplığı olan bir NuGet paketi yalnızca bağımlılıkları bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="ce380-204">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="ce380-205">Eklenen paketler isteğe bağlı olarak bir hedef çerçeve için API kurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce380-205">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="ce380-206">Bkz: [paketleri, Metapackages ve çerçeveleri](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="ce380-206">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="ce380-207">Mono</span><span class="sxs-lookup"><span data-stu-id="ce380-207">Mono</span></span>

<span data-ttu-id="ce380-208">Mono küçük bir çalışma zamanı gerekli olduğunda, genel olarak kullanılan bir .NET uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ce380-208">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="ce380-209">Bu, Android, Mac, iOS, tvOS ve watchOS Xamarin uygulamalarını çalıştırır ve öncelikle küçük bir yer gerektiren uygulamalar üzerinde odaklanmıştır çalışma zamanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ce380-209">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="ce380-210">Şu anda yayımlanan .NET standart sürümlerin tümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="ce380-210">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="ce380-211">Geçmişte, Mono büyük API'si .NET Framework'ün uygulanan ve bazı UNIX üzerindeki en popüler özelliklerini benzetilmiş.</span><span class="sxs-lookup"><span data-stu-id="ce380-211">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="ce380-212">Bazı durumlarda, bu yetenekleri UNIX Bel .NET uygulamalarını çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ce380-212">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="ce380-213">Mono genellikle tam zamanı derleyicisi ile kullanılır, ancak ayrıca iOS gibi platformlarda kullanılan bir tam statik derleyici (biri zamanında tamamlanan derleme) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ce380-213">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="ce380-214">Mono hakkında daha fazla bilgi için bkz: [Mono belgelerine](http://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="ce380-214">To learn more about Mono, see the [Mono documentation](http://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="ce380-215">.NET</span><span class="sxs-lookup"><span data-stu-id="ce380-215">.NET</span></span>

<span data-ttu-id="ce380-216">Şemsiyesi dönem için [.NET standart](#net-standard) ve tüm [.NET uygulamalarında](#implementation-of-net) ve iş yükleri.</span><span class="sxs-lookup"><span data-stu-id="ce380-216">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="ce380-217">Her zaman büyük harfle, hiçbir zaman ".Net".</span><span class="sxs-lookup"><span data-stu-id="ce380-217">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="ce380-218">Bkz: [.NET Kılavuzu](index.md)</span><span class="sxs-lookup"><span data-stu-id="ce380-218">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="ce380-219">.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce380-219">.NET Core</span></span> 

<span data-ttu-id="ce380-220">.NET platformlar arası, yüksek performanslı, açık kaynaklı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="ce380-220">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="ce380-221">Çekirdek ortak dil çalışma zamanı (CoreCLR), çekirdek Uygulama Nesne AĞACI çalışma zamanı (geliştirme, CoreRT), çekirdek temel sınıf kitaplığı ve çekirdek SDK'sı içerir.</span><span class="sxs-lookup"><span data-stu-id="ce380-221">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="ce380-222">Bkz: [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce380-222">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="ce380-223">.NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="ce380-223">.NET Core CLI</span></span>

<span data-ttu-id="ce380-224">.NET Core uygulamaları geliştirmek için bir platformlar arası araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="ce380-224">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="ce380-225">Bkz: [.NET Core komut satırı arabirimi (CLI) araçları](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce380-225">See [.NET Core command-line interface (CLI) tools](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="ce380-226">.NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="ce380-226">.NET Core SDK</span></span>

<span data-ttu-id="ce380-227">Kitaplıkları ve .NET Core uygulamaları ve kitaplıkları oluşturmak geliştiriciler izin araçlar kümesi.</span><span class="sxs-lookup"><span data-stu-id="ce380-227">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="ce380-228">İçeren [.NET Core CLI](#net-core-cli) uygulamalar, .NET Core kitaplıkları ve oluşturmaya ve çalıştırmaya uygulamalar ve yürütülebilir dotnet için çalışma zamanı oluşturmak için (*dotnet.exe*), CLI komutları çalıştırır ve uygulamaları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="ce380-228">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="ce380-229">Bkz: [.NET Core SDK Genel Bakış](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="ce380-229">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="ce380-230">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="ce380-230">.NET Framework</span></span>

<span data-ttu-id="ce380-231">Yalnızca Windows üzerinde çalışan .NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="ce380-231">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="ce380-232">Ortak dil çalışma zamanı (CLR), temel sınıf kitaplığı ve ASP.NET, Windows Forms ve WPF gibi uygulama framework kitaplıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="ce380-232">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="ce380-233">Bkz: [.NET Framework Kılavuzu](../framework/index.md).</span><span class="sxs-lookup"><span data-stu-id="ce380-233">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="ce380-234">.NET Yerel</span><span class="sxs-lookup"><span data-stu-id="ce380-234">.NET Native</span></span>

<span data-ttu-id="ce380-235">Yerel kod tamamlanan-in-time (Uygulama Nesne AĞACI) tam zamanında (JIT) aksine üreten derleyici araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="ce380-235">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="ce380-236">Derleme benzer şekilde Geliştirici makinede C++ derleyicisi ve bağlayıcı works olur.</span><span class="sxs-lookup"><span data-stu-id="ce380-236">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="ce380-237">Kullanılmayan kodunu kaldırır ve bu en iyi duruma getirme daha fazla zaman harcayan.</span><span class="sxs-lookup"><span data-stu-id="ce380-237">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="ce380-238">Kod kitaplıklarından ayıklar ve bunları yürütülebilir birleştirir.</span><span class="sxs-lookup"><span data-stu-id="ce380-238">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="ce380-239">Sonuç tüm uygulamayı temsil eden tek bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="ce380-239">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="ce380-240">UWP .NET yerel tarafından desteklenen ilk uygulama çerçevesi oluştu.</span><span class="sxs-lookup"><span data-stu-id="ce380-240">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="ce380-241">Artık, Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="ce380-241">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="ce380-242">Bkz: [.NET yerel ve CoreRT giriş](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="ce380-242">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="ce380-243">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="ce380-243">.NET Standard</span></span>

<span data-ttu-id="ce380-244">Her .NET uygulamasında kullanılabilen .NET API'lerini biçimsel belirtimini.</span><span class="sxs-lookup"><span data-stu-id="ce380-244">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="ce380-245">.NET standart belirtimi, belge kitaplığında adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="ce380-245">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="ce380-246">Bir kitaplık API uygulamaları, yalnızca belirtimleri (arabirimler) içerdiğinden .NET standart bir "kitaplığı." çağırmak için yanıltıcı</span><span class="sxs-lookup"><span data-stu-id="ce380-246">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="ce380-247">Bu kullanım belgelerindeki dışında .NET standart metapackage adı bağlamında ortadan planlıyoruz (`NETStandard.Library`).</span><span class="sxs-lookup"><span data-stu-id="ce380-247">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="ce380-248">Bkz: [.NET standart](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="ce380-248">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="ce380-249">NGEN</span><span class="sxs-lookup"><span data-stu-id="ce380-249">NGEN</span></span>

<span data-ttu-id="ce380-250">Yerel (görüntü) oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ce380-250">Native (image) generation.</span></span>

<span data-ttu-id="ce380-251">Bu teknoloji kalıcı bir JIT Derleyici düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce380-251">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="ce380-252">Genellikle, burada kod yürütülür, ancak derleme genellikle yükleme zamanında oluşuyor makinede kodu derler.</span><span class="sxs-lookup"><span data-stu-id="ce380-252">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="ce380-253">Paket</span><span class="sxs-lookup"><span data-stu-id="ce380-253">package</span></span>

<span data-ttu-id="ce380-254">Bir NuGet paketi &mdash; veya yeni bir paket &mdash; olan bir *.zip* yazar adı gibi ek meta verilerin yanı sıra aynı ada sahip bir veya daha fazla derlemeler ile dosya.</span><span class="sxs-lookup"><span data-stu-id="ce380-254">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="ce380-255">*.Zip* dosya sahip bir *.nupkg* uzantısı ve varlıkları gibi içerebilir *.dll* dosyaları ve *.xml* dosyaları, birden çok hedef ile kullanmak için çerçeveler ve sürümleri.</span><span class="sxs-lookup"><span data-stu-id="ce380-255">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="ce380-256">Bir uygulama veya kitaplığa yüklendiğinde uygun varlıklar uygulama veya kitaplığı tarafından belirtilen hedef çerçevede göre seçilir.</span><span class="sxs-lookup"><span data-stu-id="ce380-256">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="ce380-257">Arabirim tanımlayın varlıklar bulunan *ref* klasörü ve uygulama tanımlamak varlıklar olan *lib* klasör.</span><span class="sxs-lookup"><span data-stu-id="ce380-257">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="ce380-258">platform</span><span class="sxs-lookup"><span data-stu-id="ce380-258">platform</span></span>

<span data-ttu-id="ce380-259">Bir işletim sistemi ve donanım bunu, Windows, macOS, Linux, iOS ve Android gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="ce380-259">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="ce380-260">Cümle içinde kullanım örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ce380-260">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="ce380-261">".NET core bir .NET platformlar arası uygulamasıdır."</span><span class="sxs-lookup"><span data-stu-id="ce380-261">".NET Core is a cross-platform implementation of .NET."</span></span> 
- <span data-ttu-id="ce380-262">".NET standart platformuna bağımsızdır ederken Microsoft platformları, PCL profilleri'temsil eder."</span><span class="sxs-lookup"><span data-stu-id="ce380-262">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="ce380-263">.NET belgelerine ".NET platformu" sık kullandığı .NET uygulaması ya da tüm uygulamaları dahil olmak üzere .NET yığını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ce380-263">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="ce380-264">Bu kullanımları her ikisi de bu kullanımları belgelerindeki ortadan planlıyoruz birincil (işletim sistemi/donanım) anlamı ile kafası almak eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="ce380-264">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="ce380-265">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="ce380-265">runtime</span></span>

<span data-ttu-id="ce380-266">Yönetilen bir program yürütme ortamı.</span><span class="sxs-lookup"><span data-stu-id="ce380-266">The execution environment for a managed program.</span></span>

<span data-ttu-id="ce380-267">İşletim Sisteminin çalışma zamanı ortamı parçası olan ancak .NET çalışma zamanı parçası değil.</span><span class="sxs-lookup"><span data-stu-id="ce380-267">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="ce380-268">.NET çalışma zamanları bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ce380-268">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="ce380-269">Ortak Dil Çalışma Zamanı (CLR)</span><span class="sxs-lookup"><span data-stu-id="ce380-269">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="ce380-270">Çekirdek ortak dil çalışma zamanı (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="ce380-270">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="ce380-271">(UWP için) .NET yerel</span><span class="sxs-lookup"><span data-stu-id="ce380-271">.NET Native (for UWP)</span></span>
- <span data-ttu-id="ce380-272">Mono çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="ce380-272">Mono runtime</span></span>

<span data-ttu-id="ce380-273">.NET belgelerine bazen "çalışma zamanı".NET uygulaması anlamına için kullanır.</span><span class="sxs-lookup"><span data-stu-id="ce380-273">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="ce380-274">Örneğin, aşağıdaki cümlelerde "çalışma zamanı" "uygulama" ile değiştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="ce380-274">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="ce380-275">"Çeşitli .NET çalışma zamanları .NET standart belirli sürümlerini uygulayın."</span><span class="sxs-lookup"><span data-stu-id="ce380-275">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="ce380-276">"Birden çok çalışma zamanları üzerinde çalıştırmak için tasarlanmıştır kitaplıkları bu framework hedeflemelidir."</span><span class="sxs-lookup"><span data-stu-id="ce380-276">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="ce380-277">(.NET standart başvuran)</span><span class="sxs-lookup"><span data-stu-id="ce380-277">(referring to .NET Standard)</span></span>
- <span data-ttu-id="ce380-278">".NET standart belirli sürümlerini çeşitli .NET çalışma zamanları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="ce380-278">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="ce380-279">…</span><span class="sxs-lookup"><span data-stu-id="ce380-279">…</span></span> <span data-ttu-id="ce380-280">Her .NET çalışma zamanı sürümü en yüksek .NET standart sürümünü destekler... bildirir."</span><span class="sxs-lookup"><span data-stu-id="ce380-280">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="ce380-281">Bu tutarsız kullanımını ortadan planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="ce380-281">We plan to eliminate this inconsistent usage.</span></span> 

## <a name="stack"></a><span data-ttu-id="ce380-282">yığın</span><span class="sxs-lookup"><span data-stu-id="ce380-282">stack</span></span>

<span data-ttu-id="ce380-283">Birlikte oluşturmak ve uygulamaları çalıştırmak için kullanılan teknolojiler programlama kümesi.</span><span class="sxs-lookup"><span data-stu-id="ce380-283">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="ce380-284">".NET yığını".NET standart ve tüm .NET uygulamaları için anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="ce380-284">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="ce380-285">".NET yığını" tümceciği için bir .NET uygulaması başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="ce380-285">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span> 

## <a name="target-framework"></a><span data-ttu-id="ce380-286">hedef çerçevesi</span><span class="sxs-lookup"><span data-stu-id="ce380-286">target framework</span></span>

<span data-ttu-id="ce380-287">.NET uygulaması veya kitaplık dayanan API'leri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ce380-287">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="ce380-288">Bir uygulama ya da kitaplık .NET Standard (örneğin, .NET standart 2.0), sürüm belirtimi için standartlaştırılmış bir API kümesi tüm .NET uygulamaları arasında olduğu hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce380-288">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="ce380-289">Bir uygulama ya da kitaplık Ayrıca belirli bir .NET uygulaması sürümü, uygulamaya özel API'leri alır erişimi durumda hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ce380-289">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="ce380-290">Örneğin, Xamarin.iOS hedefleyen bir uygulama erişimi için sağlanan Xamarin iOS API sarmalayıcıları alır.</span><span class="sxs-lookup"><span data-stu-id="ce380-290">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="ce380-291">Kullanılabilir API'ler bir sistemde bir .NET uygulaması yükler derlemeleri tarafından tanımlanan bazı hedef çerçeveyi (örneğin, .NET Framework), hangi uygulama çerçevesi API'leri (örneğin, ASP.NET, WinForms) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="ce380-291">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="ce380-292">Paket tabanlı bir hedef çerçeve için (örneğin, .NET standart ve .NET Core), framework API'leri uygulama veya kitaplıkta yüklü paketleri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="ce380-292">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="ce380-293">Bu durumda, hedef Framework'ü örtük olarak birlikte çerçevesi olun tüm paketler başvuruda bulunan bir metapackage belirtir.</span><span class="sxs-lookup"><span data-stu-id="ce380-293">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="ce380-294">Bkz: [hedef çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ce380-294">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="ce380-295">TFM</span><span class="sxs-lookup"><span data-stu-id="ce380-295">TFM</span></span>

<span data-ttu-id="ce380-296">Hedef framework ad.</span><span class="sxs-lookup"><span data-stu-id="ce380-296">Target framework moniker.</span></span>

<span data-ttu-id="ce380-297">Bir .NET uygulaması ya da kitaplık hedef Framework'ü belirtmek için standartlaştırılmış bir belirteci biçimi.</span><span class="sxs-lookup"><span data-stu-id="ce380-297">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="ce380-298">Bir hedef çerçeveyi genellikle başvuru kısa bir ad tarafından gibi `net462`.</span><span class="sxs-lookup"><span data-stu-id="ce380-298">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="ce380-299">Uzun formlu TFMs (örn. NETFramework, sürüm = 4.6.2) var, ancak genellikle bir hedef Framework'ü belirtmek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="ce380-299">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="ce380-300">Bkz: [hedef çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="ce380-300">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="ce380-301">UWP</span><span class="sxs-lookup"><span data-stu-id="ce380-301">UWP</span></span>

<span data-ttu-id="ce380-302">Evrensel Windows platformu.</span><span class="sxs-lookup"><span data-stu-id="ce380-302">Universal Windows Platform.</span></span>

<span data-ttu-id="ce380-303">Windows uygulamaları ve yazılım modern, Dokunmatik özellikli nesnelerin interneti için (IOT) oluşturmak için kullanılan .NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="ce380-303">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="ce380-304">Bu farklı türde hedeflemek isteyebilirsiniz cihazları birleştirmek için PC'ler, tabletler, phablets, telefonlar ve bile Xbox dahil olmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ce380-304">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="ce380-305">UWP Merkezi uygulama mağazası, Yürütme Ortamı (Appcontaıner) ve Windows API'larını Win32 yerine kullanılacak bir dizi gibi birçok hizmetler sağlar (WinRT).</span><span class="sxs-lookup"><span data-stu-id="ce380-305">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="ce380-306">Uygulamalar, C++, C#, VB.NET ve JavaScript yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="ce380-306">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="ce380-307">C# ve VB.NET kullanırken, .NET API'lerini .NET Core tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ce380-307">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce380-308">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce380-308">See also</span></span>

[<span data-ttu-id="ce380-309">.NET Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ce380-309">.NET Guide</span></span>](index.md)  
[<span data-ttu-id="ce380-310">.NET Framework Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ce380-310">.NET Framework Guide</span></span>](../framework/index.md)  
[<span data-ttu-id="ce380-311">.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce380-311">.NET Core</span></span>](../core/index.md)  
[<span data-ttu-id="ce380-312">ASP.NET genel bakış</span><span class="sxs-lookup"><span data-stu-id="ce380-312">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)  
[<span data-ttu-id="ce380-313">ASP.NET çekirdeği genel bakış</span><span class="sxs-lookup"><span data-stu-id="ce380-313">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)  

