---
title: .NET sözlüğü
description: .NET belgelerde kullanılan seçili koşulları anlamını öğrenin.
author: tdykstra
ms.author: tdykstra
ms.date: 07/08/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 195fbb799432b9d01a5faf301c9f8f2d1edfa1ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579411"
---
# <a name="net-glossary"></a><span data-ttu-id="86c7f-103">.NET sözlüğü</span><span class="sxs-lookup"><span data-stu-id="86c7f-103">.NET Glossary</span></span>

<span data-ttu-id="86c7f-104">Birincil Bu sözlük anlamları seçili terimleri ve tanımları olmadan .NET belgelerinde sık görünen kısaltmalar açıklamak için hedefidir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-104">The primary goal of this glossary is to clarify meanings of selected terms and acronyms that appear frequently in the .NET documentation without definitions.</span></span>

## <a name="aot"></a><span data-ttu-id="86c7f-105">UYGULAMA NESNE AĞACI</span><span class="sxs-lookup"><span data-stu-id="86c7f-105">AOT</span></span>

<span data-ttu-id="86c7f-106">Zaman tamamlanan derleyicisi.</span><span class="sxs-lookup"><span data-stu-id="86c7f-106">Ahead-of-time compiler.</span></span>

<span data-ttu-id="86c7f-107">Benzer şekilde [JIT](#jit), bu derleyici ayrıca çevirir [IL](#il) makine kodu.</span><span class="sxs-lookup"><span data-stu-id="86c7f-107">Similar to [JIT](#jit), this compiler also translates [IL](#il) to machine code.</span></span> <span data-ttu-id="86c7f-108">Uygulama yürütülür ve genellikle farklı bir makineye gerçekleştirilen önce JIT derleme aksine, uygulama nesne AĞACI derleme olur.</span><span class="sxs-lookup"><span data-stu-id="86c7f-108">In contrast to JIT compilation, AOT compilation happens before the application is executed and is usually performed on a different machine.</span></span> <span data-ttu-id="86c7f-109">Çalışma zamanında uygulama nesne AĞACI aracı zincirleri derleme yoktur çünkü harcanan süre derleme en aza indirmek yok.</span><span class="sxs-lookup"><span data-stu-id="86c7f-109">Because AOT tool chains don't compile at runtime, they don't have to minimize time spent compiling.</span></span> <span data-ttu-id="86c7f-110">Daha fazla zaman iyileştirme harcayabilir anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-110">That means they can spend more time optimizing.</span></span> <span data-ttu-id="86c7f-111">Uygulama Nesne AĞACI bağlamında tüm uygulama olduğundan, uygulama nesne AĞACI derleyici çapraz modülü bağlama ve tüm başvuruları izlenir ve tek bir yürütülebilir dosya üretilen anlamına gelir tüm program analizi de gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-111">Since the context of AOT is the entire application, the AOT compiler also performs cross-module linking and whole-program analysis, which means that all references are followed and a single executable is produced.</span></span>

## <a name="aspnet"></a><span data-ttu-id="86c7f-112">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="86c7f-112">ASP.NET</span></span> 

<span data-ttu-id="86c7f-113">.NET Framework ile birlikte gelen özgün ASP.NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="86c7f-113">The original ASP.NET implementation that ships with the .NET Framework.</span></span>

<span data-ttu-id="86c7f-114">Bazen ASP.NET ASP.NET Core dahil olmak üzere iki ASP.NET uygulamaları başvuran bir genel bir terimdir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-114">Sometimes ASP.NET is an umbrella term that refers to both ASP.NET implementations including ASP.NET Core.</span></span> <span data-ttu-id="86c7f-115">Verilen örnek terimi taşıyan anlamı bağlam tarafından belirlenir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-115">The meaning that the term carries in any given instance is determined by context.</span></span> <span data-ttu-id="86c7f-116">Başvurmak için ASP.NET aldığınız temizleyin sağlamak istediğinizde 4.x değil kullanmakta olduğunuz ASP.NET hem uygulamaları anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-116">Refer to ASP.NET 4.x when you want to make it clear that you’re not using ASP.NET to mean both implementations.</span></span> 

<span data-ttu-id="86c7f-117">Bkz: [ASP.NET belgelerine](/aspnet/#pivot=aspnet).</span><span class="sxs-lookup"><span data-stu-id="86c7f-117">See [ASP.NET documentation](/aspnet/#pivot=aspnet).</span></span>

## <a name="aspnet-core"></a><span data-ttu-id="86c7f-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="86c7f-118">ASP.NET Core</span></span>

<span data-ttu-id="86c7f-119">Bir platformlar arası, yüksek performanslı, açık kaynak uygulaması, ASP .NET Core üzerinde oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="86c7f-119">A cross-platform, high-performance, open source implementation of ASP.NET built on .NET Core.</span></span>

<span data-ttu-id="86c7f-120">Bkz: [ASP.NET Core belgeleri](/aspnet/#pivot=core).</span><span class="sxs-lookup"><span data-stu-id="86c7f-120">See [ASP.NET Core documentation](/aspnet/#pivot=core).</span></span>

## <a name="assembly"></a><span data-ttu-id="86c7f-121">derleme</span><span class="sxs-lookup"><span data-stu-id="86c7f-121">assembly</span></span>

<span data-ttu-id="86c7f-122">A *.dll*/*.exe* uygulamaları veya diğer derlemelerden tarafından çağrılabilir API'leri koleksiyonunu içeren dosya.</span><span class="sxs-lookup"><span data-stu-id="86c7f-122">A *.dll*/*.exe* file that can contain a collection of APIs that can be called by apps or other assemblies.</span></span>

<span data-ttu-id="86c7f-123">Bir derlemeyi arabirimleri, sınıflar, yapılar, numaralandırmalar ve temsilciler gibi türlerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-123">An assembly may include types such as interfaces, classes, structures, enumerations, and delegates.</span></span> <span data-ttu-id="86c7f-124">Bir projenin derlemelerde *bin* klasörü bazen denir *ikili dosyaları*.</span><span class="sxs-lookup"><span data-stu-id="86c7f-124">Assemblies in a project's *bin* folder are sometimes referred to as *binaries*.</span></span> <span data-ttu-id="86c7f-125">Ayrıca bkz. [Kitaplığı](#library).</span><span class="sxs-lookup"><span data-stu-id="86c7f-125">See also [library](#library).</span></span>

## <a name="clr"></a><span data-ttu-id="86c7f-126">CLR</span><span class="sxs-lookup"><span data-stu-id="86c7f-126">CLR</span></span>

<span data-ttu-id="86c7f-127">Ortak dil çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="86c7f-127">Common Language Runtime.</span></span>

<span data-ttu-id="86c7f-128">Bağlama, tam anlamını bağlıdır, ancak bu genellikle .NET Framework çalışma zamanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-128">The exact meaning depends on the context, but this usually refers to the runtime of the .NET Framework.</span></span> <span data-ttu-id="86c7f-129">Bellek ayırma ve yönetim CLR işler.</span><span class="sxs-lookup"><span data-stu-id="86c7f-129">The CLR handles memory allocation and management.</span></span> <span data-ttu-id="86c7f-130">CLR ayrıca yalnızca uygulamaları yürütülen ancak aynı zamanda oluşturur ve kod üzerinde-JIT Derleyici kullanarak çalışma sırasında derlenen bir sanal makine bulunuyor.</span><span class="sxs-lookup"><span data-stu-id="86c7f-130">The CLR is also a virtual machine that not only executes apps but also generates and compiles code on-the-fly using a JIT compiler.</span></span> <span data-ttu-id="86c7f-131">Geçerli Microsoft CLR Windows yalnızca uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-131">The current Microsoft CLR implementation is Windows only.</span></span>

## <a name="coreclr"></a><span data-ttu-id="86c7f-132">CoreCLR</span><span class="sxs-lookup"><span data-stu-id="86c7f-132">CoreCLR</span></span>

<span data-ttu-id="86c7f-133">.NET core ortak dil çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="86c7f-133">.NET Core Common Language Runtime.</span></span>

<span data-ttu-id="86c7f-134">Bu CLR aynı kod CLR tabanını oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="86c7f-134">This CLR is built from the same code base as the CLR.</span></span> <span data-ttu-id="86c7f-135">İlk olarak, CoreCLR Silverlight'ın çalışma zamanı olan ve birden çok platformda çalışacak biçimde tasarlanan, özellikle Windows ve OS x CoreCLR şimdi parçası .NET Core ve CLR basitleştirilmiş bir sürümünü temsil eder.</span><span class="sxs-lookup"><span data-stu-id="86c7f-135">Originally, CoreCLR was the runtime of Silverlight and was designed to run on multiple platforms, specifically Windows and OS X. CoreCLR is now part of .NET Core and represents a simplified version of the CLR.</span></span> <span data-ttu-id="86c7f-136">Bu hala şimdi birçok Linux dağıtımları için destek dahil olmak üzere bir platformlar arası çalışma zamanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-136">It's still a cross platform runtime, now including support for many Linux distributions.</span></span> <span data-ttu-id="86c7f-137">Ayrıca CoreCLR JIT ve kod yürütme özelliklerine sahip bir sanal makine ' dir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-137">CoreCLR is also a virtual machine with JIT and code execution capabilities.</span></span>

## <a name="corefx"></a><span data-ttu-id="86c7f-138">CoreFX</span><span class="sxs-lookup"><span data-stu-id="86c7f-138">CoreFX</span></span>

<span data-ttu-id="86c7f-139">.NET core temel sınıf kitaplığı (BCL)</span><span class="sxs-lookup"><span data-stu-id="86c7f-139">.NET Core Base Class Library (BCL)</span></span>

<span data-ttu-id="86c7f-140">Set System.* oluşturan kitaplıkları'nın (ve sınırlı ölçüde Microsoft.*) ad alanları.</span><span class="sxs-lookup"><span data-stu-id="86c7f-140">A set of libraries that comprise the System.* (and to a limited extent  Microsoft.*) namespaces.</span></span> <span data-ttu-id="86c7f-141">BCL genel amaçlı, ASP.NET Core gibi daha üst düzey uygulama çerçeveleri derleme üzerinde alt düzey framework olur.</span><span class="sxs-lookup"><span data-stu-id="86c7f-141">The BCL is a general purpose, lower-level framework that higher-level application frameworks, such as ASP.NET Core, build on.</span></span> <span data-ttu-id="86c7f-142">.NET Core BCL kaynak kodunu yer [CoreFX depo](https://github.com/dotnet/corefx).</span><span class="sxs-lookup"><span data-stu-id="86c7f-142">The source code of the .NET Core BCL is contained in the [CoreFX repository](https://github.com/dotnet/corefx).</span></span> <span data-ttu-id="86c7f-143">Ancak, .NET Core API'ları çoğunluğu kullanılabilir de .NET Framework şekilde CoreFX bir .NET Framework BCL çatalı düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86c7f-143">However, the majority of the .NET Core APIs are also available in the .NET Framework, so you can think of CoreFX as a fork of the .NET Framework BCL.</span></span>

## <a name="corert"></a><span data-ttu-id="86c7f-144">CoreRT</span><span class="sxs-lookup"><span data-stu-id="86c7f-144">CoreRT</span></span>

<span data-ttu-id="86c7f-145">.NET çekirdeği çalışma zamanı.</span><span class="sxs-lookup"><span data-stu-id="86c7f-145">.NET Core runtime.</span></span>

<span data-ttu-id="86c7f-146">CLR/CoreCLR aksine CoreRT oluşturmak ve bunu içermediği için kod üzerinde-çalışma sırasında çalıştırmak için kullanılan olanakları içermez anlamına gelen bir sanal makine, değil bir [JIT](#jit).</span><span class="sxs-lookup"><span data-stu-id="86c7f-146">In contrast to the CLR/CoreCLR, CoreRT is not a virtual machine, which means it doesn't include the facilities to generate and run code on-the-fly because it doesn't include a [JIT](#jit).</span></span> <span data-ttu-id="86c7f-147">Ancak, içerir [GC](#gc) ve çalışma zamanı tür kimliği (RTTI) ve yansıma yeteneği.</span><span class="sxs-lookup"><span data-stu-id="86c7f-147">It does, however, include the [GC](#gc) and the ability for runtime type identification (RTTI) and reflection.</span></span> <span data-ttu-id="86c7f-148">Ancak, böylece meta verilerini yansıma için gerekli değildir, tür sistemi tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-148">However, its type system is designed so that metadata for reflection isn't required.</span></span> <span data-ttu-id="86c7f-149">Bu sahip sağlayan bir [Uygulama Nesne AĞACI](#aot) aracı koyma gereksiz meta veri bağlantı ve uygulama kullanmayan kodu (daha da önemlisi) tanımlamak zinciri.</span><span class="sxs-lookup"><span data-stu-id="86c7f-149">This enables having an [AOT](#aot) tool chain that can link away superfluous metadata and (more importantly) identify code that the app doesn't use.</span></span> <span data-ttu-id="86c7f-150">CoreRT geliştirme ' dir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-150">CoreRT is in development.</span></span>

<span data-ttu-id="86c7f-151">Bkz: [.NET yerel ve CoreRT giriş](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="86c7f-151">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="ecosystem"></a><span data-ttu-id="86c7f-152">ekosistemi</span><span class="sxs-lookup"><span data-stu-id="86c7f-152">ecosystem</span></span>

<span data-ttu-id="86c7f-153">Tüm çalışma zamanı yazılım, geliştirme araçları ve oluşturmak ve belirli bir teknolojinin uygulamaları çalıştırmak için kullanılan topluluk kaynakları.</span><span class="sxs-lookup"><span data-stu-id="86c7f-153">All of the runtime software, development tools, and community resources that are used to build and run applications for a given technology.</span></span>

<span data-ttu-id="86c7f-154">".NET ekosistemi" terimi ".NET yığını" gibi benzer terimler, üçüncü taraf uygulamaların ve kitaplıkları, kataloğa farklıdır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-154">The term ".NET ecosystem" differs from similar terms such as ".NET stack" in its inclusion of third-party apps and libraries.</span></span> <span data-ttu-id="86c7f-155">Bir tümcedeki örneği şöyledir:</span><span class="sxs-lookup"><span data-stu-id="86c7f-155">Here's an example in a sentence:</span></span>

- <span data-ttu-id="86c7f-156">"Arkasında motivasyon [.NET standart](#net-standard) .NET ekosistemi büyük bütünlüğünü oluşturmaktır."</span><span class="sxs-lookup"><span data-stu-id="86c7f-156">"The motivation behind the [.NET Standard](#net-standard) is to establish greater uniformity in the .NET ecosystem."</span></span> 

## <a name="framework"></a><span data-ttu-id="86c7f-157">çerçeve</span><span class="sxs-lookup"><span data-stu-id="86c7f-157">framework</span></span>

<span data-ttu-id="86c7f-158">Genel olarak, geniş kapsamlı bir koleksiyon API'leri, geliştirme ve belirli teknolojiye dayalı uygulamalarının dağıtımını hızlandırır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-158">In general, a comprehensive collection of APIs that facilitates development and deployment of applications that are based on a particular technology.</span></span> <span data-ttu-id="86c7f-159">Bu genel olarak, ASP.NET Core ve Windows Forms uygulama çerçeveleri örnekleridir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-159">In this general sense, ASP.NET Core and Windows Forms are examples of application frameworks.</span></span> <span data-ttu-id="86c7f-160">Ayrıca bkz. [Kitaplığı](#library).</span><span class="sxs-lookup"><span data-stu-id="86c7f-160">See also [library](#library).</span></span>

<span data-ttu-id="86c7f-161">"Framework" sözcüğünü aşağıdaki terimler içinde daha belirgin bir teknik anlam sahiptir:</span><span class="sxs-lookup"><span data-stu-id="86c7f-161">The word "framework" has a more specific technical meaning in the following terms:</span></span>
* [<span data-ttu-id="86c7f-162">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="86c7f-162">.NET Framework</span></span>](#net-framework)
* [<span data-ttu-id="86c7f-163">hedef çerçevesi</span><span class="sxs-lookup"><span data-stu-id="86c7f-163">target framework</span></span>](#target-framework)
* [<span data-ttu-id="86c7f-164">TFM (hedef framework takma ad)</span><span class="sxs-lookup"><span data-stu-id="86c7f-164">TFM (target framework moniker)</span></span>](#tfm)

<span data-ttu-id="86c7f-165">Varolan belgelerde başvurduğu bazen "framework" bir [.NET uygulaması](#implementation-of-net).</span><span class="sxs-lookup"><span data-stu-id="86c7f-165">In the existing documentation, "framework" sometimes refers to an [implementation of .NET](#implementation-of-net).</span></span> <span data-ttu-id="86c7f-166">Örneğin, bir makale bir çerçeve .NET Core çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-166">For example, an article may call .NET Core a framework.</span></span> <span data-ttu-id="86c7f-167">Bu karmaşık kullanım belgelerindeki ortadan planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="86c7f-167">We plan to eliminate this confusing usage from the documentation.</span></span>

## <a name="gc"></a><span data-ttu-id="86c7f-168">GC</span><span class="sxs-lookup"><span data-stu-id="86c7f-168">GC</span></span>

<span data-ttu-id="86c7f-169">Çöp toplayıcı.</span><span class="sxs-lookup"><span data-stu-id="86c7f-169">Garbage collector.</span></span>

<span data-ttu-id="86c7f-170">Çöp toplayıcı otomatik bellek yönetimi uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-170">The garbage collector is an implementation of automatic memory management.</span></span>  <span data-ttu-id="86c7f-171">GC artık kullanımda olmayan nesneler tarafından kullanılan belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-171">The GC frees memory occupied by objects that are no longer in use.</span></span> 

<span data-ttu-id="86c7f-172">Bkz: [çöp toplama](garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="86c7f-172">See [Garbage Collection](garbage-collection/index.md).</span></span>

## <a name="il"></a><span data-ttu-id="86c7f-173">IL</span><span class="sxs-lookup"><span data-stu-id="86c7f-173">IL</span></span>

<span data-ttu-id="86c7f-174">Ara dil.</span><span class="sxs-lookup"><span data-stu-id="86c7f-174">Intermediate language.</span></span>

<span data-ttu-id="86c7f-175">C# gibi daha üst düzey .NET dilleri Ara dile (IL) olarak adlandırılır ve donanım belirsiz yönerge kümesi aşağıya doğru derleyin.</span><span class="sxs-lookup"><span data-stu-id="86c7f-175">Higher-level .NET languages, such as C#, compile down to a hardware-agnostic instruction set, which is called Intermediate Language (IL).</span></span> <span data-ttu-id="86c7f-176">IL bazen MSIL (Microsoft IL) veya CIL (ortak IL) olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-176">IL is sometimes referred to as MSIL (Microsoft IL) or CIL (Common IL).</span></span>

## <a name="jit"></a><span data-ttu-id="86c7f-177">JIT</span><span class="sxs-lookup"><span data-stu-id="86c7f-177">JIT</span></span>

<span data-ttu-id="86c7f-178">Yalnızca zaman derleyicisi.</span><span class="sxs-lookup"><span data-stu-id="86c7f-178">Just-in-time compiler.</span></span>

<span data-ttu-id="86c7f-179">Benzer şekilde [Uygulama Nesne AĞACI](#aot), bu derleyici çevirir [IL](#il) işlemci anlar makine kodu.</span><span class="sxs-lookup"><span data-stu-id="86c7f-179">Similar to [AOT](#aot), this compiler translates [IL](#il) to machine code that the processor understands.</span></span> <span data-ttu-id="86c7f-180">Uygulama Nesne AĞACI, aksine JIT derleme isteğe bağlı olur ve kodu çalıştırmak için gereken aynı makine üzerinde gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-180">Unlike AOT, JIT compilation happens on demand and is performed on the same machine that the code needs to run on.</span></span> <span data-ttu-id="86c7f-181">JIT derleme uygulama yürütme sırasında oluştuğunda gerçekleştiğinden derleme zamanında çalışma zamanında bir parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-181">Since JIT compilation occurs during execution of the application, compile time is part of the run time.</span></span> <span data-ttu-id="86c7f-182">Bu nedenle, zamanın en iyi duruma getirme kodu ortaya çıkan kodu oluşturmak üzere tasarrufları karşı dengelemek JIT derleyicileri sahip.</span><span class="sxs-lookup"><span data-stu-id="86c7f-182">Thus, JIT compilers have to balance time spent optimizing code against the savings that the resulting code can produce.</span></span> <span data-ttu-id="86c7f-183">Ancak bir JIT gerçek donanım bilir ve farklı uygulamaları sevk gerek kalmadan gelen geliştiriciler boş.</span><span class="sxs-lookup"><span data-stu-id="86c7f-183">But a JIT knows the actual hardware and can free developers from having to ship different implementations.</span></span>

## <a name="implementation-of-net"></a><span data-ttu-id="86c7f-184">.NET uygulaması</span><span class="sxs-lookup"><span data-stu-id="86c7f-184">implementation of .NET</span></span>

<span data-ttu-id="86c7f-185">.NET uygulaması aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="86c7f-185">An implementation of .NET includes the following:</span></span>

- <span data-ttu-id="86c7f-186">Bir veya daha fazla çalışma zamanları.</span><span class="sxs-lookup"><span data-stu-id="86c7f-186">One or more runtimes.</span></span> <span data-ttu-id="86c7f-187">Örnekler: CLR, CoreCLR, CoreRT.</span><span class="sxs-lookup"><span data-stu-id="86c7f-187">Examples: CLR, CoreCLR, CoreRT.</span></span>
- <span data-ttu-id="86c7f-188">.NET standart sürümü uygular ve ek API'leri içerebilir sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="86c7f-188">A class library that implements a version of the .NET Standard and may include additional APIs.</span></span> <span data-ttu-id="86c7f-189">Örnekler: .NET Framework temel sınıf kitaplığı, .NET Core temel sınıf kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="86c7f-189">Examples: .NET Framework Base Class Library, .NET Core Base Class Library.</span></span>
- <span data-ttu-id="86c7f-190">İsteğe bağlı olarak, bir veya daha fazla uygulama çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="86c7f-190">Optionally, one or more application frameworks.</span></span> <span data-ttu-id="86c7f-191">Örnekler: ASP.NET, Windows Forms ve WPF .NET Framework dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-191">Examples: ASP.NET, Windows Forms, and WPF are included in the .NET Framework.</span></span>
- <span data-ttu-id="86c7f-192">İsteğe bağlı olarak, geliştirme araçları.</span><span class="sxs-lookup"><span data-stu-id="86c7f-192">Optionally, development tools.</span></span> <span data-ttu-id="86c7f-193">Bazı geliştirme araçları birden çok uygulamalar arasında paylaşılır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-193">Some development tools are shared among multiple implementations.</span></span>

<span data-ttu-id="86c7f-194">.NET uygulamaları örnekleri:</span><span class="sxs-lookup"><span data-stu-id="86c7f-194">Examples of .NET implementations:</span></span>

- [<span data-ttu-id="86c7f-195">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="86c7f-195">.NET Framework</span></span>](#net-framework)
- [<span data-ttu-id="86c7f-196">.NET Core</span><span class="sxs-lookup"><span data-stu-id="86c7f-196">.NET Core</span></span>](#net-core)
- [<span data-ttu-id="86c7f-197">Evrensel Windows Platformu (UWP)</span><span class="sxs-lookup"><span data-stu-id="86c7f-197">Universal Windows Platform (UWP)</span></span>](#uwp)

## <a name="library"></a><span data-ttu-id="86c7f-198">kitaplık</span><span class="sxs-lookup"><span data-stu-id="86c7f-198">library</span></span>

<span data-ttu-id="86c7f-199">Uygulamaları veya diğer kitaplıkları tarafından çağrılabilir API'leri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="86c7f-199">A collection of APIs that can be called by apps or other libraries.</span></span> <span data-ttu-id="86c7f-200">Bir veya daha fazla .NET kitaplığı oluşan [derlemeler](#assembly).</span><span class="sxs-lookup"><span data-stu-id="86c7f-200">A .NET library is composed of one or more [assemblies](#assembly).</span></span>

<span data-ttu-id="86c7f-201">Sözcükler kitaplığı ve [framework](#framework) genellikle maliyetle aynı anlamda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-201">The words library and [framework](#framework) are often used synonymously.</span></span>

## <a name="metapackage"></a><span data-ttu-id="86c7f-202">metapackage</span><span class="sxs-lookup"><span data-stu-id="86c7f-202">metapackage</span></span>

<span data-ttu-id="86c7f-203">Kendi ancak hiçbir kitaplığı olan bir NuGet paketi yalnızca bağımlılıkları bir listesidir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-203">A NuGet package that has no library of its own but is only a list of dependencies.</span></span> <span data-ttu-id="86c7f-204">Eklenen paketler isteğe bağlı olarak bir hedef çerçeve için API kurabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86c7f-204">The included packages can optionally establish the API for a target framework.</span></span>

<span data-ttu-id="86c7f-205">Bkz: [paketleri, Metapackages ve çerçeveleri](../core/packages.md)</span><span class="sxs-lookup"><span data-stu-id="86c7f-205">See [Packages, Metapackages and Frameworks](../core/packages.md)</span></span>

## <a name="mono"></a><span data-ttu-id="86c7f-206">Mono</span><span class="sxs-lookup"><span data-stu-id="86c7f-206">Mono</span></span>

<span data-ttu-id="86c7f-207">Mono küçük bir çalışma zamanı gerekli olduğunda, genel olarak kullanılan bir .NET uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-207">Mono is a .NET implementation that is mainly used when a small runtime is required.</span></span> <span data-ttu-id="86c7f-208">Bu, Android, Mac, iOS, tvOS ve watchOS Xamarin uygulamalarını çalıştırır ve öncelikle küçük bir yer gerektiren uygulamalar üzerinde odaklanmıştır çalışma zamanı gösterir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-208">It is the runtime that powers Xamarin applications on Android, Mac, iOS, tvOS and watchOS and is focused primarily on apps that require a small footprint.</span></span>

<span data-ttu-id="86c7f-209">Şu anda yayımlanan .NET standart sürümlerin tümünü destekler.</span><span class="sxs-lookup"><span data-stu-id="86c7f-209">It supports all of the currently published .NET Standard versions.</span></span>

<span data-ttu-id="86c7f-210">Geçmişte, Mono büyük API'si .NET Framework'ün uygulanan ve bazı UNIX üzerindeki en popüler özelliklerini benzetilmiş.</span><span class="sxs-lookup"><span data-stu-id="86c7f-210">Historically, Mono implemented the larger API of the .NET Framework and emulated some of the most popular capabilities on Unix.</span></span> <span data-ttu-id="86c7f-211">Bazı durumlarda, bu yetenekleri UNIX Bel .NET uygulamalarını çalıştırmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-211">It is sometimes used to run .NET applications that rely on those capabilities on Unix.</span></span>

<span data-ttu-id="86c7f-212">Mono genellikle tam zamanı derleyicisi ile kullanılır, ancak ayrıca iOS gibi platformlarda kullanılan bir tam statik derleyici (biri zamanında tamamlanan derleme) sahiptir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-212">Mono is typically used with a just-in-time compiler, but it also features a full static compiler (ahead-of-time compilation) that is used on platforms like iOS.</span></span>

<span data-ttu-id="86c7f-213">Mono hakkında daha fazla bilgi için bkz: [Mono belgelerine](https://www.mono-project.com/docs/).</span><span class="sxs-lookup"><span data-stu-id="86c7f-213">To learn more about Mono, see the [Mono documentation](https://www.mono-project.com/docs/).</span></span>

## <a name="net"></a><span data-ttu-id="86c7f-214">.NET</span><span class="sxs-lookup"><span data-stu-id="86c7f-214">.NET</span></span>

<span data-ttu-id="86c7f-215">Şemsiyesi dönem için [.NET standart](#net-standard) ve tüm [.NET uygulamalarında](#implementation-of-net) ve iş yükleri.</span><span class="sxs-lookup"><span data-stu-id="86c7f-215">The umbrella term for [.NET Standard](#net-standard) and all [.NET implementations](#implementation-of-net) and workloads.</span></span> <span data-ttu-id="86c7f-216">Her zaman büyük harfle, hiçbir zaman ".Net".</span><span class="sxs-lookup"><span data-stu-id="86c7f-216">Always capitalized, never ".Net".</span></span>

<span data-ttu-id="86c7f-217">Bkz: [.NET Kılavuzu](index.md)</span><span class="sxs-lookup"><span data-stu-id="86c7f-217">See the [.NET Guide](index.md)</span></span>

## <a name="net-core"></a><span data-ttu-id="86c7f-218">.NET Core</span><span class="sxs-lookup"><span data-stu-id="86c7f-218">.NET Core</span></span> 

<span data-ttu-id="86c7f-219">.NET platformlar arası, yüksek performanslı, açık kaynaklı uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-219">A cross-platform, high-performance, open source implementation of .NET.</span></span> <span data-ttu-id="86c7f-220">Çekirdek ortak dil çalışma zamanı (CoreCLR), çekirdek Uygulama Nesne AĞACI çalışma zamanı (geliştirme, CoreRT), çekirdek temel sınıf kitaplığı ve çekirdek SDK'sı içerir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-220">Includes the Core Common Language Runtime (CoreCLR), the Core AOT Runtime (CoreRT, in development), the Core Base Class Library, and the Core SDK.</span></span>

<span data-ttu-id="86c7f-221">Bkz: [.NET Core](../core/index.md).</span><span class="sxs-lookup"><span data-stu-id="86c7f-221">See [.NET Core](../core/index.md).</span></span>

## <a name="net-core-cli"></a><span data-ttu-id="86c7f-222">.NET core CLI</span><span class="sxs-lookup"><span data-stu-id="86c7f-222">.NET Core CLI</span></span>

<span data-ttu-id="86c7f-223">.NET Core uygulamaları geliştirmek için bir platformlar arası araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="86c7f-223">A cross-platform toolchain for developing .NET Core applications.</span></span>

<span data-ttu-id="86c7f-224">Bkz: [.NET Core komut satırı arabirimi (CLI) araçları](../core/tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="86c7f-224">See [.NET Core command-line interface (CLI) tools](../core/tools/index.md).</span></span>

## <a name="net-core-sdk"></a><span data-ttu-id="86c7f-225">.NET core SDK</span><span class="sxs-lookup"><span data-stu-id="86c7f-225">.NET Core SDK</span></span>

<span data-ttu-id="86c7f-226">Kitaplıkları ve .NET Core uygulamaları ve kitaplıkları oluşturmak geliştiriciler izin araçlar kümesi.</span><span class="sxs-lookup"><span data-stu-id="86c7f-226">A set of libraries and tools that allow developers to create .NET Core applications and libraries.</span></span> <span data-ttu-id="86c7f-227">İçeren [.NET Core CLI](#net-core-cli) uygulamalar, .NET Core kitaplıkları ve oluşturmaya ve çalıştırmaya uygulamalar ve yürütülebilir dotnet için çalışma zamanı oluşturmak için (*dotnet.exe*), CLI komutları çalıştırır ve uygulamaları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-227">Includes the [.NET Core CLI](#net-core-cli) for building apps, .NET Core libraries and runtime for building and running apps, and the dotnet executable (*dotnet.exe*) that runs CLI commands and runs applications.</span></span>

<span data-ttu-id="86c7f-228">Bkz: [.NET Core SDK Genel Bakış](../core/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="86c7f-228">See [.NET Core SDK Overview](../core/sdk.md).</span></span>

## <a name="net-framework"></a><span data-ttu-id="86c7f-229">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="86c7f-229">.NET Framework</span></span>

<span data-ttu-id="86c7f-230">Yalnızca Windows üzerinde çalışan .NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="86c7f-230">An implementation of .NET that runs only on Windows.</span></span> <span data-ttu-id="86c7f-231">Ortak dil çalışma zamanı (CLR), temel sınıf kitaplığı ve ASP.NET, Windows Forms ve WPF gibi uygulama framework kitaplıkları içerir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-231">Includes the Common Language Runtime (CLR), the Base Class Library, and application framework libraries such as ASP.NET, Windows Forms, and WPF.</span></span>

<span data-ttu-id="86c7f-232">Bkz: [.NET Framework Kılavuzu](../framework/index.md).</span><span class="sxs-lookup"><span data-stu-id="86c7f-232">See [.NET Framework Guide](../framework/index.md).</span></span>

## <a name="net-native"></a><span data-ttu-id="86c7f-233">.NET Yerel</span><span class="sxs-lookup"><span data-stu-id="86c7f-233">.NET Native</span></span>

<span data-ttu-id="86c7f-234">Yerel kod tamamlanan-in-time (Uygulama Nesne AĞACI) tam zamanında (JIT) aksine üreten derleyici araç zinciri.</span><span class="sxs-lookup"><span data-stu-id="86c7f-234">A compiler tool chain that produces native code ahead-of-time (AOT), as opposed to just-in-time (JIT).</span></span>

<span data-ttu-id="86c7f-235">Derleme benzer şekilde Geliştirici makinede C++ derleyicisi ve bağlayıcı works olur.</span><span class="sxs-lookup"><span data-stu-id="86c7f-235">Compilation happens on the developer's machine similar to the way a C++ compiler and linker works.</span></span> <span data-ttu-id="86c7f-236">Kullanılmayan kodunu kaldırır ve bu en iyi duruma getirme daha fazla zaman harcayan.</span><span class="sxs-lookup"><span data-stu-id="86c7f-236">It removes unused code and spends more time optimizing it.</span></span> <span data-ttu-id="86c7f-237">Kod kitaplıklarından ayıklar ve bunları yürütülebilir birleştirir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-237">It extracts code from libraries and merges them into the executable.</span></span> <span data-ttu-id="86c7f-238">Sonuç tüm uygulamayı temsil eden tek bir modüldür.</span><span class="sxs-lookup"><span data-stu-id="86c7f-238">The result is a single module that represents the entire app.</span></span>

<span data-ttu-id="86c7f-239">UWP .NET yerel tarafından desteklenen ilk uygulama çerçevesi oluştu.</span><span class="sxs-lookup"><span data-stu-id="86c7f-239">UWP was the first application framework supported by .NET Native.</span></span> <span data-ttu-id="86c7f-240">Artık, Windows, macOS ve Linux için yerel konsol uygulamaları oluşturmayı destekler.</span><span class="sxs-lookup"><span data-stu-id="86c7f-240">Now, we support building native console apps for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="86c7f-241">Bkz: [.NET yerel ve CoreRT giriş](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span><span class="sxs-lookup"><span data-stu-id="86c7f-241">See [Intro to .NET Native and CoreRT](https://github.com/dotnet/corert/blob/master/Documentation/intro-to-corert.md)</span></span>

## <a name="net-standard"></a><span data-ttu-id="86c7f-242">.NET standart</span><span class="sxs-lookup"><span data-stu-id="86c7f-242">.NET Standard</span></span>

<span data-ttu-id="86c7f-243">Her .NET uygulamasında kullanılabilen .NET API'lerini biçimsel belirtimini.</span><span class="sxs-lookup"><span data-stu-id="86c7f-243">A formal specification of .NET APIs that are available in each .NET implementation.</span></span>

<span data-ttu-id="86c7f-244">.NET standart belirtimi, belge kitaplığında adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-244">The .NET Standard specification is sometimes called a library in the documentation.</span></span> <span data-ttu-id="86c7f-245">Bir kitaplık API uygulamaları, yalnızca belirtimleri (arabirimler) içerdiğinden .NET standart bir "kitaplığı." çağırmak için yanıltıcı</span><span class="sxs-lookup"><span data-stu-id="86c7f-245">Because a library includes API implementations, not only specifications (interfaces), it's misleading to call .NET Standard a "library."</span></span> <span data-ttu-id="86c7f-246">Bu kullanım belgelerindeki dışında .NET standart metapackage adı bağlamında ortadan planlıyoruz (`NETStandard.Library`).</span><span class="sxs-lookup"><span data-stu-id="86c7f-246">We plan to eliminate that usage from the documentation, except in reference to the name of the .NET Standard metapackage (`NETStandard.Library`).</span></span>

<span data-ttu-id="86c7f-247">Bkz: [.NET standart](net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="86c7f-247">See [.NET Standard](net-standard.md).</span></span>

## <a name="ngen"></a><span data-ttu-id="86c7f-248">NGEN</span><span class="sxs-lookup"><span data-stu-id="86c7f-248">NGEN</span></span>

<span data-ttu-id="86c7f-249">Yerel (görüntü) oluşturma.</span><span class="sxs-lookup"><span data-stu-id="86c7f-249">Native (image) generation.</span></span>

<span data-ttu-id="86c7f-250">Bu teknoloji kalıcı bir JIT Derleyici düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86c7f-250">You can think of this technology as a persistent JIT compiler.</span></span> <span data-ttu-id="86c7f-251">Genellikle, burada kod yürütülür, ancak derleme genellikle yükleme zamanında oluşuyor makinede kodu derler.</span><span class="sxs-lookup"><span data-stu-id="86c7f-251">It usually compiles code on the machine where the code is executed, but compilation typically occurs at install time.</span></span>

## <a name="package"></a><span data-ttu-id="86c7f-252">Paket</span><span class="sxs-lookup"><span data-stu-id="86c7f-252">package</span></span>

<span data-ttu-id="86c7f-253">Bir NuGet paketi &mdash; veya yeni bir paket &mdash; olan bir *.zip* yazar adı gibi ek meta verilerin yanı sıra aynı ada sahip bir veya daha fazla derlemeler ile dosya.</span><span class="sxs-lookup"><span data-stu-id="86c7f-253">A NuGet package &mdash; or just a package &mdash; is a *.zip* file with one or more assemblies of the same name along with additional metadata such as the author name.</span></span>

<span data-ttu-id="86c7f-254">*.Zip* dosya sahip bir *.nupkg* uzantısı ve varlıkları gibi içerebilir *.dll* dosyaları ve *.xml* dosyaları, birden çok hedef ile kullanmak için çerçeveler ve sürümleri.</span><span class="sxs-lookup"><span data-stu-id="86c7f-254">The *.zip* file has a *.nupkg* extension and may contain assets, such as *.dll* files and *.xml* files, for use with multiple target frameworks and versions.</span></span> <span data-ttu-id="86c7f-255">Bir uygulama veya kitaplığa yüklendiğinde uygun varlıklar uygulama veya kitaplığı tarafından belirtilen hedef çerçevede göre seçilir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-255">When installed in an app or library, the appropriate assets are selected based on the target framework specified by the app or library.</span></span> <span data-ttu-id="86c7f-256">Arabirim tanımlayın varlıklar bulunan *ref* klasörü ve uygulama tanımlamak varlıklar olan *lib* klasör.</span><span class="sxs-lookup"><span data-stu-id="86c7f-256">The assets that define the interface are in the *ref* folder, and the assets that define the implementation are in the *lib* folder.</span></span>

## <a name="platform"></a><span data-ttu-id="86c7f-257">platform</span><span class="sxs-lookup"><span data-stu-id="86c7f-257">platform</span></span>

<span data-ttu-id="86c7f-258">Bir işletim sistemi ve donanım bunu, Windows, macOS, Linux, iOS ve Android gibi çalışır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-258">An operating system and the hardware it runs on, such as Windows, macOS, Linux, iOS, and Android.</span></span>

<span data-ttu-id="86c7f-259">Cümle içinde kullanım örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="86c7f-259">Here are examples of usage in sentences:</span></span>

- <span data-ttu-id="86c7f-260">".NET core bir .NET platformlar arası uygulamasıdır."</span><span class="sxs-lookup"><span data-stu-id="86c7f-260">".NET Core is a cross-platform implementation of .NET."</span></span> 
- <span data-ttu-id="86c7f-261">".NET standart platformuna bağımsızdır ederken Microsoft platformları, PCL profilleri'temsil eder."</span><span class="sxs-lookup"><span data-stu-id="86c7f-261">"PCL profiles represent Microsoft platforms, while the .NET Standard is agnostic to platform."</span></span>

<span data-ttu-id="86c7f-262">.NET belgelerine ".NET platformu" sık kullandığı .NET uygulaması ya da tüm uygulamaları dahil olmak üzere .NET yığını anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-262">The .NET documentation frequently uses ".NET platform" to mean either an implementation of .NET or the .NET stack including all implementations.</span></span> <span data-ttu-id="86c7f-263">Bu kullanımları her ikisi de bu kullanımları belgelerindeki ortadan planlıyoruz birincil (işletim sistemi/donanım) anlamı ile kafası almak eğilimindedir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-263">Both of these usages tend to get confused with the primary (OS/hardware) meaning, so we plan to eliminate these usages from the documentation.</span></span>

## <a name="runtime"></a><span data-ttu-id="86c7f-264">çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="86c7f-264">runtime</span></span>

<span data-ttu-id="86c7f-265">Yönetilen bir program yürütme ortamı.</span><span class="sxs-lookup"><span data-stu-id="86c7f-265">The execution environment for a managed program.</span></span>

<span data-ttu-id="86c7f-266">İşletim Sisteminin çalışma zamanı ortamı parçası olan ancak .NET çalışma zamanı parçası değil.</span><span class="sxs-lookup"><span data-stu-id="86c7f-266">The OS is part of the runtime environment but is not part of the .NET runtime.</span></span> <span data-ttu-id="86c7f-267">.NET çalışma zamanları bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="86c7f-267">Here are some examples of .NET runtimes:</span></span>

- <span data-ttu-id="86c7f-268">Ortak Dil Çalışma Zamanı (CLR)</span><span class="sxs-lookup"><span data-stu-id="86c7f-268">Common Language Runtime (CLR)</span></span>
- <span data-ttu-id="86c7f-269">Çekirdek ortak dil çalışma zamanı (CoreCLR)</span><span class="sxs-lookup"><span data-stu-id="86c7f-269">Core Common Language Runtime (CoreCLR)</span></span>
- <span data-ttu-id="86c7f-270">(UWP için) .NET yerel</span><span class="sxs-lookup"><span data-stu-id="86c7f-270">.NET Native (for UWP)</span></span>
- <span data-ttu-id="86c7f-271">Mono çalışma zamanı</span><span class="sxs-lookup"><span data-stu-id="86c7f-271">Mono runtime</span></span>

<span data-ttu-id="86c7f-272">.NET belgelerine bazen "çalışma zamanı".NET uygulaması anlamına için kullanır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-272">The .NET documentation sometimes uses "runtime" to mean an implementation of .NET.</span></span> <span data-ttu-id="86c7f-273">Örneğin, aşağıdaki cümlelerde "çalışma zamanı" "uygulama" ile değiştirilmelidir:</span><span class="sxs-lookup"><span data-stu-id="86c7f-273">For example, in the following sentences "runtime" should be replaced with "implementation":</span></span>

- <span data-ttu-id="86c7f-274">"Çeşitli .NET çalışma zamanları .NET standart belirli sürümlerini uygulayın."</span><span class="sxs-lookup"><span data-stu-id="86c7f-274">"The various .NET runtimes implement specific versions of .NET Standard."</span></span>
- <span data-ttu-id="86c7f-275">"Birden çok çalışma zamanları üzerinde çalıştırmak için tasarlanmıştır kitaplıkları bu framework hedeflemelidir."</span><span class="sxs-lookup"><span data-stu-id="86c7f-275">"Libraries that are intended to run on multiple runtimes should target this framework."</span></span> <span data-ttu-id="86c7f-276">(.NET standart başvuran)</span><span class="sxs-lookup"><span data-stu-id="86c7f-276">(referring to .NET Standard)</span></span>
- <span data-ttu-id="86c7f-277">".NET standart belirli sürümlerini çeşitli .NET çalışma zamanları uygulayın.</span><span class="sxs-lookup"><span data-stu-id="86c7f-277">"The various .NET runtimes implement specific versions of .NET Standard.</span></span> <span data-ttu-id="86c7f-278">…</span><span class="sxs-lookup"><span data-stu-id="86c7f-278">…</span></span> <span data-ttu-id="86c7f-279">Her .NET çalışma zamanı sürümü en yüksek .NET standart sürümünü destekler... bildirir."</span><span class="sxs-lookup"><span data-stu-id="86c7f-279">Each .NET runtime version advertises the highest .NET Standard version it supports …"</span></span>

<span data-ttu-id="86c7f-280">Bu tutarsız kullanımını ortadan planlıyoruz.</span><span class="sxs-lookup"><span data-stu-id="86c7f-280">We plan to eliminate this inconsistent usage.</span></span> 

## <a name="stack"></a><span data-ttu-id="86c7f-281">yığın</span><span class="sxs-lookup"><span data-stu-id="86c7f-281">stack</span></span>

<span data-ttu-id="86c7f-282">Birlikte oluşturmak ve uygulamaları çalıştırmak için kullanılan teknolojiler programlama kümesi.</span><span class="sxs-lookup"><span data-stu-id="86c7f-282">A set of programming technologies that are used together to build and run applications.</span></span>

<span data-ttu-id="86c7f-283">".NET yığını".NET standart ve tüm .NET uygulamaları için anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-283">"The .NET stack" refers to the .NET Standard and all .NET implementations.</span></span> <span data-ttu-id="86c7f-284">".NET yığını" tümceciği için bir .NET uygulaması başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-284">The phrase "a .NET stack" may refer to one implementation of .NET.</span></span> 

## <a name="target-framework"></a><span data-ttu-id="86c7f-285">hedef çerçevesi</span><span class="sxs-lookup"><span data-stu-id="86c7f-285">target framework</span></span>

<span data-ttu-id="86c7f-286">.NET uygulaması veya kitaplık dayanan API'leri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="86c7f-286">The collection of APIs that a .NET app or library relies on.</span></span>

<span data-ttu-id="86c7f-287">Bir uygulama ya da kitaplık .NET Standard (örneğin, .NET standart 2.0), sürüm belirtimi için standartlaştırılmış bir API kümesi tüm .NET uygulamaları arasında olduğu hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86c7f-287">An app or library can target a version of .NET Standard (for example, .NET Standard 2.0), which is specification for a standardized set of APIs across all .NET implementations.</span></span> <span data-ttu-id="86c7f-288">Bir uygulama ya da kitaplık Ayrıca belirli bir .NET uygulaması sürümü, uygulamaya özel API'leri alır erişimi durumda hedefleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="86c7f-288">An app or library can also target a version of a specific .NET implementation, in which case it gets access to implementation-specific APIs.</span></span> <span data-ttu-id="86c7f-289">Örneğin, Xamarin.iOS hedefleyen bir uygulama erişimi için sağlanan Xamarin iOS API sarmalayıcıları alır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-289">For example, an app that targets Xamarin.iOS gets access to Xamarin-provided iOS API wrappers.</span></span>

<span data-ttu-id="86c7f-290">Kullanılabilir API'ler bir sistemde bir .NET uygulaması yükler derlemeleri tarafından tanımlanan bazı hedef çerçeveyi (örneğin, .NET Framework), hangi uygulama çerçevesi API'leri (örneğin, ASP.NET, WinForms) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-290">For some target frameworks (for example, the .NET Framework) the available APIs are defined by the assemblies that a .NET implementation installs on a system, which may include application framework APIs (for example, ASP.NET, WinForms).</span></span> <span data-ttu-id="86c7f-291">Paket tabanlı bir hedef çerçeve için (örneğin, .NET standart ve .NET Core), framework API'leri uygulama veya kitaplıkta yüklü paketleri tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-291">For package-based target frameworks (such as .NET Standard and .NET Core), the framework APIs are defined by the packages installed in the app or library.</span></span> <span data-ttu-id="86c7f-292">Bu durumda, hedef Framework'ü örtük olarak birlikte çerçevesi olun tüm paketler başvuruda bulunan bir metapackage belirtir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-292">In that case, the target framework implicitly specifies a metapackage that references all the packages that together make up the framework.</span></span>

<span data-ttu-id="86c7f-293">Bkz: [hedef çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="86c7f-293">See [Target Frameworks](frameworks.md).</span></span>

## <a name="tfm"></a><span data-ttu-id="86c7f-294">TFM</span><span class="sxs-lookup"><span data-stu-id="86c7f-294">TFM</span></span>

<span data-ttu-id="86c7f-295">Hedef framework ad.</span><span class="sxs-lookup"><span data-stu-id="86c7f-295">Target framework moniker.</span></span>

<span data-ttu-id="86c7f-296">Bir .NET uygulaması ya da kitaplık hedef Framework'ü belirtmek için standartlaştırılmış bir belirteci biçimi.</span><span class="sxs-lookup"><span data-stu-id="86c7f-296">A standardized token format for specifying the target framework of a .NET app or library.</span></span> <span data-ttu-id="86c7f-297">Bir hedef çerçeveyi genellikle başvuru kısa bir ad tarafından gibi `net462`.</span><span class="sxs-lookup"><span data-stu-id="86c7f-297">Target frameworks are typically referenced by a short name, such as `net462`.</span></span> <span data-ttu-id="86c7f-298">Uzun formlu TFMs (örn. NETFramework, sürüm = 4.6.2) var, ancak genellikle bir hedef Framework'ü belirtmek için kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="86c7f-298">Long-form TFMs (such as .NETFramework,Version=4.6.2) exist but are not generally used to specify a target framework.</span></span>

<span data-ttu-id="86c7f-299">Bkz: [hedef çerçeveler](frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="86c7f-299">See [Target Frameworks](frameworks.md).</span></span>

## <a name="uwp"></a><span data-ttu-id="86c7f-300">UWP</span><span class="sxs-lookup"><span data-stu-id="86c7f-300">UWP</span></span>

<span data-ttu-id="86c7f-301">Evrensel Windows platformu.</span><span class="sxs-lookup"><span data-stu-id="86c7f-301">Universal Windows Platform.</span></span>

<span data-ttu-id="86c7f-302">Windows uygulamaları ve yazılım modern, Dokunmatik özellikli nesnelerin interneti için (IOT) oluşturmak için kullanılan .NET uygulaması.</span><span class="sxs-lookup"><span data-stu-id="86c7f-302">An implementation of .NET that is used for building modern, touch-enabled Windows applications and software for the Internet of Things (IoT).</span></span> <span data-ttu-id="86c7f-303">Bu farklı türde hedeflemek isteyebilirsiniz cihazları birleştirmek için PC'ler, tabletler, phablets, telefonlar ve bile Xbox dahil olmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-303">It's designed to unify the different types of devices that you may want to target, including PCs, tablets, phablets, phones, and even the Xbox.</span></span> <span data-ttu-id="86c7f-304">UWP Merkezi uygulama mağazası, Yürütme Ortamı (Appcontaıner) ve Windows API'larını Win32 yerine kullanılacak bir dizi gibi birçok hizmetler sağlar (WinRT).</span><span class="sxs-lookup"><span data-stu-id="86c7f-304">UWP provides many services, such as a centralized app store, an execution environment (AppContainer), and a set of Windows APIs to use instead of Win32 (WinRT).</span></span> <span data-ttu-id="86c7f-305">Uygulamalar, C++, C#, VB.NET ve JavaScript yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="86c7f-305">Apps can be written in C++, C#, VB.NET, and JavaScript.</span></span> <span data-ttu-id="86c7f-306">C# ve VB.NET kullanırken, .NET API'lerini .NET Core tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="86c7f-306">When using C# and VB.NET, the .NET APIs are provided by .NET Core.</span></span>

## <a name="see-also"></a><span data-ttu-id="86c7f-307">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="86c7f-307">See also</span></span>

[<span data-ttu-id="86c7f-308">.NET Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="86c7f-308">.NET Guide</span></span>](index.md)  
[<span data-ttu-id="86c7f-309">.NET Framework Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="86c7f-309">.NET Framework Guide</span></span>](../framework/index.md)  
[<span data-ttu-id="86c7f-310">.NET Core</span><span class="sxs-lookup"><span data-stu-id="86c7f-310">.NET Core</span></span>](../core/index.md)  
[<span data-ttu-id="86c7f-311">ASP.NET genel bakış</span><span class="sxs-lookup"><span data-stu-id="86c7f-311">ASP.NET Overview</span></span>](/aspnet/index#pivot=aspnet)  
[<span data-ttu-id="86c7f-312">ASP.NET çekirdeği genel bakış</span><span class="sxs-lookup"><span data-stu-id="86c7f-312">ASP.NET Core Overview</span></span>](/aspnet/index#pivot=core)  

