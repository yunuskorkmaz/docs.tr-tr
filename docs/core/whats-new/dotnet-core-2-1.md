---
title: .NET Core 2.1 yenilikler nelerdir?
description: .NET Core 2.1 içinde bulunan yeni özellikler hakkında bilgi edinin.
author: rpetrusha
ms.author: ronpet
ms.date: 05/30/2018
ms.openlocfilehash: a7e0ae3c65a18376a7648198a43f1272a2bddafd
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696461"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="bdb24-103">.NET Core 2.1 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="bdb24-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="bdb24-104">.NET core 2.1 aşağıdaki alanlarda geliştirmeler ve yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="bdb24-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="bdb24-105">Araçları</span><span class="sxs-lookup"><span data-stu-id="bdb24-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="bdb24-106">İleri alma</span><span class="sxs-lookup"><span data-stu-id="bdb24-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="bdb24-107">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="bdb24-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="bdb24-108">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="bdb24-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="bdb24-109">JIT Derleyici geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bdb24-109">JIT compiler improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="bdb24-110">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="bdb24-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="bdb24-111">Araçları</span><span class="sxs-lookup"><span data-stu-id="bdb24-111">Tooling</span></span>

<span data-ttu-id="bdb24-112">.NET Core 2.1.300 SDK'sı, .NET Core 2.1 ile dahil araç aşağıdaki değişiklikler ve geliştirmeler içerir:</span><span class="sxs-lookup"><span data-stu-id="bdb24-112">The .NET Core 2.1.300 SDK, the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="bdb24-113">Derleme performans geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bdb24-113">Build performance improvements</span></span>

<span data-ttu-id="bdb24-114">.NET Core 2.1 bir ana odağını özellikle artımlı derlemeler için derleme zamanı performans artırma.</span><span class="sxs-lookup"><span data-stu-id="bdb24-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="bdb24-115">Bu performans iyileştirmeleri kullanarak her iki komut satırı derlemeleri uygulama `dotnet build` ve Visual Studio derlemelerde.</span><span class="sxs-lookup"><span data-stu-id="bdb24-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="bdb24-116">Geliştirme, tek tek bazı alanlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bdb24-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="bdb24-117">Paket varlık çözümlemesi için tüm varlıkları yerine bir yapı tarafından kullanılan varlıklar çözümleniyor.</span><span class="sxs-lookup"><span data-stu-id="bdb24-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="bdb24-118">Derleme referanslarını önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="bdb24-118">Caching of assembly references.</span></span>

- <span data-ttu-id="bdb24-119">Uzun süre çalışan SDK kullanımını yapı arasında tek span işlemler sunucuları `dotnet build` çağrılarını.</span><span class="sxs-lookup"><span data-stu-id="bdb24-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="bdb24-120">Her zaman olan JIT derleme büyük kod bloklarını gerek ortadan `dotnet build` çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="bdb24-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="bdb24-121">İşlemleri otomatik olarak aşağıdaki komutla sonlandırılabilir sunucu oluşturun:</span><span class="sxs-lookup"><span data-stu-id="bdb24-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="bdb24-122">Yeni CLI komutları</span><span class="sxs-lookup"><span data-stu-id="bdb24-122">New CLI commands</span></span>

<span data-ttu-id="bdb24-123">Yalnızca bir başına proje temel kullanarak kullanılabilir araçları sayısı [ `DotnetCliToolReference` ](../tools/extensibility.md) artık kullanılabilir .NET Core SDK'ın bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="bdb24-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="bdb24-124">Bu araçlar içerir:</span><span class="sxs-lookup"><span data-stu-id="bdb24-124">These tools include:</span></span>

- <span data-ttu-id="bdb24-125">`dotnet watch` belirlenen bir dizi komut yürütülmeden önce değiştirmek bir dosya bekler bir dosya sistemi İzleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdb24-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="bdb24-126">Örneğin, aşağıdaki komutu otomatik olarak geçerli projenin yeniden oluşturur ve bir dosyada değiştiğinde ayrıntılı çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="bdb24-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```console
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="bdb24-127">Daha fazla bilgi için bkz: [dotnet Gözcü kullanarak geliştirme ASP.NET Core uygulamaları](/aspnet/core/tutorials/dotnet-watch)</span><span class="sxs-lookup"><span data-stu-id="bdb24-127">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span></span>

- <span data-ttu-id="bdb24-128">`dotnet dev-certs` oluşturur ve ASP.NET Core uygulamaları geliştirme sırasında kullanılan sertifikaları yönetir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-128">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="bdb24-129">`dotnet user-secrets` ASP.NET Core uygulamaları kullanıcı gizli deposunda gizli anahtarları yönetir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-129">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="bdb24-130">`dotnet sql-cache` Dağıtılmış önbelleğe alma işlemi için kullanılacak bir Microsoft SQL Server veritabanındaki bir tablo ve dizinler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bdb24-130">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="bdb24-131">`dotnet ef` veritabanlarını yönetmek için bir araçtır <xref:Microsoft.EntityFrameworkCore.DbContext> nesneleri ve Entity Framework Çekirdek uygulamalarında geçişleri.</span><span class="sxs-lookup"><span data-stu-id="bdb24-131">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="bdb24-132">Daha fazla bilgi için bkz: [EF çekirdek .NET komut satırı araçları](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="bdb24-132">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="bdb24-133">Genel araçları</span><span class="sxs-lookup"><span data-stu-id="bdb24-133">Global Tools</span></span>

<span data-ttu-id="bdb24-134">.NET core 2.1 destekler *genel Araçları* --genel komut satırından kullanılabilir diğer bir deyişle, özel araçlar.</span><span class="sxs-lookup"><span data-stu-id="bdb24-134">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="bdb24-135">Önceki sürümlerinde .NET Core, genişletilebilirlik modeli özel araçlar kullanılabilir bir proje başına temelinde yalnızca kullanılarak yapılan [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).</span><span class="sxs-lookup"><span data-stu-id="bdb24-135">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="bdb24-136">Genel bir aracı yüklemek için kullandığınız [dotnet aracı yükleme](..\tools\dotnet-tool-install.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="bdb24-136">To install a Global Tool, you use the [dotnet tool install](..\tools\dotnet-tool-install.md) command.</span></span> <span data-ttu-id="bdb24-137">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="bdb24-137">For example:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="bdb24-138">Bir kez yüklendikten sonra aracı adı belirterek aracını komut satırından çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-138">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="bdb24-139">Daha fazla bilgi için bkz: [.NET Core genel araçlarına genel bakış](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="bdb24-139">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="single-source-tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="bdb24-140">Tek kaynak aracı yönetimiyle `dotnet tool` komutu</span><span class="sxs-lookup"><span data-stu-id="bdb24-140">Single-source tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="bdb24-141">.NET Core 2.1 tüm araçlar işlemlerini kullanmak `dotnet tool` komutu.</span><span class="sxs-lookup"><span data-stu-id="bdb24-141">In .NET Core 2.1, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="bdb24-142">Aşağıdaki seçenekler mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="bdb24-142">The following options are available:</span></span>

- <span data-ttu-id="bdb24-143">`dotnet tool install` bir aracı yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="bdb24-143">`dotnet tool install` to install a tool.</span></span>

- <span data-ttu-id="bdb24-144">`dotnet tool update` etkili bir şekilde güncelleştiren bir aracı kaldırıp için.</span><span class="sxs-lookup"><span data-stu-id="bdb24-144">`dotnet tool update` to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="bdb24-145">`dotnet tool list` şu anda yüklü listesinde Araçları'na gidin.</span><span class="sxs-lookup"><span data-stu-id="bdb24-145">`dotnet tool list` to list currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="bdb24-146">İleri alma</span><span class="sxs-lookup"><span data-stu-id="bdb24-146">Roll forward</span></span>

<span data-ttu-id="bdb24-147">En son sürüme otomatik olarak .NET Core 2. 0'ile başlayan tüm .NET Core uygulamaları ileriye *alt sürüm* bir sistemde yüklü.</span><span class="sxs-lookup"><span data-stu-id="bdb24-147">All .NET Core applications starting with the .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span> <span data-ttu-id="bdb24-148">Diğer bir deyişle, bir uygulama ile oluşturulan .NET Core sürüm mevcut değilse, uygulama en son yüklenen alt sürüm karşı çalışır.</span><span class="sxs-lookup"><span data-stu-id="bdb24-148">That is, if the .NET Core version that an application was built with is not present, the application runs against the latest installed minor version.</span></span> <span data-ttu-id="bdb24-149">Diğer bir deyişle, bir uygulamayı .NET Core 2.0 ile oluşturulmuş ve .NET Core 2.0 kendi ana bilgisayar sisteminde mevcut değil ancak .NET Core 2.1, uygulama .NET Core 2.1 ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="bdb24-149">In other words, if an application is built with .NET Core 2.0 and .NET Core 2.0 itself is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bdb24-150">Bu İleri alma davranışını Önizleme sürümleri için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-150">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="bdb24-151">Ya da ana sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-151">Nor does it apply to major releases.</span></span> <span data-ttu-id="bdb24-152">Örneğin, bir .NET Core 1.0 uygulaması .NET Core 2.0 veya .NET Core 2.1 ileriye olmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="bdb24-152">For example, a .NET Core 1.0 application wouldn't roll forward to .NET Core 2.0 or .NET Core 2.1.</span></span>

<span data-ttu-id="bdb24-153">Alt sürüm toplama İleri herhangi üç yolla devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bdb24-153">You can also disable minor version roll forward in any of three ways:</span></span>

- <span data-ttu-id="bdb24-154">Ayarlama `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` ortam değişkeni 0'a eşit</span><span class="sxs-lookup"><span data-stu-id="bdb24-154">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable equal to 0,</span></span>

- <span data-ttu-id="bdb24-155">Aşağıdaki satırı runtimeconfig.json dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="bdb24-155">Add the following line to the runtimeconfig.json file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="bdb24-156">Kullanırken [.NET Core CLI araçlarını](../tools/index.md), .NET Core komutu aşağıdaki seçeneğiyle gibi içeren `run`:</span><span class="sxs-lookup"><span data-stu-id="bdb24-156">When using [.NET Core CLI tools](../tools/index.md), include the following option with a .NET Core command such as `run`:</span></span>

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a><span data-ttu-id="bdb24-157">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="bdb24-157">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="bdb24-158">Kendi içinde bulunan uygulama hizmeti</span><span class="sxs-lookup"><span data-stu-id="bdb24-158">Self-contained application servicing</span></span>

<span data-ttu-id="bdb24-159">`dotnet publish` Şimdi bir hizmet verilen çalışma zamanı sürümü müstakil uygulamalarla yayımlar.</span><span class="sxs-lookup"><span data-stu-id="bdb24-159">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="bdb24-160">.NET Core 2.1 SDK'sı kendi içinde bulunan bir uygulama yayımladığınızda, uygulamanız bu SDK'sı tarafından bilinen en son hizmet verilen çalışma zamanı sürümü içerir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-160">When you publish a self-contained application with the .NET Core 2.1 SDK, your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="bdb24-161">Son SDK'sını yükselttiğinizde, en son .NET çekirdeği çalışma zamanı sürümü ile yayımlama.</span><span class="sxs-lookup"><span data-stu-id="bdb24-161">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="bdb24-162">Bu, .NET Core 1.0 çalışma zamanları ve sonraki sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-162">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="bdb24-163">NuGet.org sürümlerinde çalışma zamanı müstakil yayımlama kullanır. Hizmet verilen çalışma zamanı makinenizde olması gerekmez.</span><span class="sxs-lookup"><span data-stu-id="bdb24-163">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="bdb24-164">Farklı bir sürümü aracılığıyla belirtilmediği sürece .NET Core 2.0 SDK'yı kullanarak, kendi içinde bulunan uygulamalar .NET Core 2.0.0 çalışma zamanı ile yayımlanan `RuntimeFrameworkVersion` özelliği.</span><span class="sxs-lookup"><span data-stu-id="bdb24-164">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="bdb24-165">Bu yeni davranış ile artık kendi başına bir uygulama için daha yüksek bir çalışma zamanı sürümü seçmek için bu özelliği ayarlamak gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-165">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="bdb24-166">İleride en kolay yaklaşım .NET Core 2.1 SDK ile her zaman yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="bdb24-166">The easiest approach going forward is to always publish with .NET Core 2.1 SDK.</span></span>

## <a name="windows-compatibility-pack"></a><span data-ttu-id="bdb24-167">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="bdb24-167">Windows Compatibility Pack</span></span>

<span data-ttu-id="bdb24-168">.NET Framework var olan koddan .NET Core için bağlantı noktası olduğunda, kullanabileceğiniz [Windows Uyumluluk Paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="bdb24-168">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="bdb24-169">.NET Core bulunandan daha fazla API'leri 20.000 erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdb24-169">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="bdb24-170">Bu API'leri türler <xref:System.Drawing?displayProperty="nameWithType"> ad alanı, <xref:System.Diagnostics.EventLog> sınıfı, WMI, performans sayaçları, Windows Hizmetleri ve Windows kayıt defteri türleri ve üyeleri.</span><span class="sxs-lookup"><span data-stu-id="bdb24-170">These APIs include types in the <xref:System.Drawing?displayProperty="nameWithType"> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="bdb24-171">JIT Derleyici geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bdb24-171">JIT compiler improvements</span></span>

<span data-ttu-id="bdb24-172">.NET core içerir adlı yeni bir JIT Derleyici teknoloji *katmanlı derleme* (olarak da bilinen *Uyarlamalı iyileştirme*), önemli ölçüde performansı geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-172">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span>

<span data-ttu-id="bdb24-173">JIT Derleyici tarafından gerçekleştirilen önemli görevlerden birini kod yürütmeyi en iyi duruma getiriyor.</span><span class="sxs-lookup"><span data-stu-id="bdb24-173">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="bdb24-174">Az kullanılan kod yolları için ancak, çalışma zamanı iyileştirilmemiş kod çalıştırmasını harcadığı daha kodu en iyi duruma getirme daha uzun derleyici harcayabilir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-174">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="bdb24-175">Katmanlı derleme JIT derleme iki aşamada sunar:</span><span class="sxs-lookup"><span data-stu-id="bdb24-175">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="bdb24-176">A **ilk katmanı**, hangi oluşturur kod mümkün olan en kısa sürede.</span><span class="sxs-lookup"><span data-stu-id="bdb24-176">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="bdb24-177">A **ikinci katman**, iyileştirilmiş kodda sık gerçekleştirilen bu yöntemleri için hangi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bdb24-177">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="bdb24-178">İkinci katmanın derlemesinin paralel Gelişmiş performans için gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-178">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="bdb24-179">Aşağıdaki ortam değişkenini ayarlayarak katmanlı derleme .NET Core 2.1 uygulama ile test edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="bdb24-179">You can test tiered compilation with a .NET Core 2.1 app by setting the following environment variable:</span></span>

```console
COMPlus_TieredCompilation="1"
```

## <a name="api-changes"></a><span data-ttu-id="bdb24-180">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="bdb24-180">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="bdb24-181">`Span<T>` Ve `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="bdb24-181">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="bdb24-182">.NET core 2.1 çalışma dizilerine sahip olun bazı yeni türleri ve çok daha verimli bellek diğer türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-182">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="bdb24-183">Yeni türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="bdb24-183">The new types include:</span></span>

- <span data-ttu-id="bdb24-184"><xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bdb24-184"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="bdb24-185"><xref:System.Memory%601?displayProperty=nameWithType> ve <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bdb24-185"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="bdb24-186">Böyle öğeleri bir dizi bir kısmı veya bir bölümünü bellek arabelleği olarak geçirirken bu türleri, bir yönteme geçirmeden önce verileri kısmı bir kopyasını yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-186">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="bdb24-187">Bu tür ek bellek ayırma ve kopyalama işlemleri ortadan kaldırır, veriler sanal bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdb24-187">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="bdb24-188">Aşağıdaki örnek kullanan bir <xref:System.Span%601> örneği dizi 10 öğelerini sanal bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="bdb24-188">The following example uses a <xref:System.Span%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a><span data-ttu-id="bdb24-189">Brotli sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="bdb24-189">Brotli compression</span></span>

<span data-ttu-id="bdb24-190">.NET core 2.1 Brotli sıkıştırma ve açma desteğini ekler.</span><span class="sxs-lookup"><span data-stu-id="bdb24-190">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="bdb24-191">Brotli tanımlanan bir genel amaçlı kayıpsız sıkıştırma algoritması olan [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) ve birçok web tarayıcıları ve önde gelen web sunucusu tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-191">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="bdb24-192">Akış tabanlı kullanabilirsiniz <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> sınıf veya yüksek performanslı Yayılma temelli <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> ve <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="bdb24-192">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="bdb24-193">Aşağıdaki örnek ile sıkıştırma gösterilmektedir <xref:System.IO.Compression.BrotliStream> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="bdb24-193">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<span data-ttu-id="bdb24-194"><xref:System.IO.Compression.BrotliStream> Davranıştır aynı <xref:System.IO.Compression.DeflateStream> ve <xref:System.IO.Compression.GZipStream>, hangi kolaylaştırır bu API'leri çağıran dönüştürme kodu <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="bdb24-194">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="bdb24-195">Yeni şifreleme API'leri ve şifreleme geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bdb24-195">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="bdb24-196">.NET core 2.1 API şifreleme çeşitli geliştirmeler içerir:</span><span class="sxs-lookup"><span data-stu-id="bdb24-196">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="bdb24-197"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> System.Security.Cryptography.Pkcs paketinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-197"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="bdb24-198">Aynı uygulamasıdır <xref:System.Security.Cryptography.Pkcs.SignedCms> .NET Framework sınıf.</span><span class="sxs-lookup"><span data-stu-id="bdb24-198">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="bdb24-199">Yeni aşırı <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> yöntemleri kabul dışında SHA-1 algoritmaları kullanarak sertifika parmak izi değerleri almak arayanlar etkinleştirmek için bir karma algoritması tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="bdb24-199">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="bdb24-200">Yeni <xref:System.Span%601>-tabanlı şifreleme API'leri karma için HMAC, şifreleme rastgele sayı oluşturma, asimetrik imza oluşturma, asimetrik imza işleme ve RSA şifreleme kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-200">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="bdb24-201">Performansını <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> % 15'hakkında kullanılarak geliştirilmiş bir <xref:System.Span%601>-temel.</span><span class="sxs-lookup"><span data-stu-id="bdb24-201">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="bdb24-202">Yeni <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> sınıfı, iki yeni yöntemleri içerir:</span><span class="sxs-lookup"><span data-stu-id="bdb24-202">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="bdb24-203"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> bir sabit için herhangi iki giriş kullanmaya uygun yan kanal bilgilerini zamanlama için katkıda bulunan önlemek için şifreleme doğrulamasında kolaylaştırır aynı uzunlukta döndürmek için gereken süre.</span><span class="sxs-lookup"><span data-stu-id="bdb24-203"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="bdb24-204"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> iyileştirilemiyor bir bellek temizleme yordamdır.</span><span class="sxs-lookup"><span data-stu-id="bdb24-204"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="bdb24-205">Statik <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> yöntemi dolgular bir <xref:System.Span%601> rastgele değerlere sahip.</span><span class="sxs-lookup"><span data-stu-id="bdb24-205">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=fullName> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="bdb24-206"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Linux ve maxOS artık desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="bdb24-206">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and maxOS.</span></span>

- <span data-ttu-id="bdb24-207">Eliptik Eğri Diffie-Hellman (ECDH) bulunan şimdi <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> sınıf ailesi.</span><span class="sxs-lookup"><span data-stu-id="bdb24-207">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="bdb24-208">Yüzey alanını .NET Framework ile aynı değil.</span><span class="sxs-lookup"><span data-stu-id="bdb24-208">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="bdb24-209">Tarafından döndürülen örnek <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> şifrelemek veya SHA-2 özet kullanarak OAEP ile şifresini yanı sıra oluşturabilir veya RSA-PSS kullanarak imzaları doğrular.</span><span class="sxs-lookup"><span data-stu-id="bdb24-209">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="bdb24-210">Yuva geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="bdb24-210">Sockets improvements</span></span>

<span data-ttu-id="bdb24-211">.NET core içeren yeni bir tür <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>ve bir yeniden <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, üst düzey ağ API'leri temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="bdb24-211">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="bdb24-212"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, örneğin, temelini <xref:System.Net.Http.HttpClient> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="bdb24-212"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="bdb24-213">.NET Core önceki sürümlerinde, üst düzey API'leri yerel ağ uygulamalarında temel alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="bdb24-213">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="bdb24-214">.NET Core 2.1 içinde sunulan yuva uygulaması, çok sayıda avantaj vardır:</span><span class="sxs-lookup"><span data-stu-id="bdb24-214">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="bdb24-215">Önceki bir uygulama ile karşılaştırıldığında önemli performans geliştirmesi.</span><span class="sxs-lookup"><span data-stu-id="bdb24-215">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="bdb24-216">Dağıtım ve Bakım kolaylaştıran eleme platform bağımlılıklarla.</span><span class="sxs-lookup"><span data-stu-id="bdb24-216">Elimination on platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="bdb24-217">Tüm .NET Core platformlar genelinde tutarlı davranışı.</span><span class="sxs-lookup"><span data-stu-id="bdb24-217">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="bdb24-218">Yuva temel alarak <xref:System.Net.Http.SocketsHttpHandler> .NET Core 2.1 varsayılan uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="bdb24-218">Sockets based on <xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="bdb24-219">Ancak, eski kullanmak için uygulamanızı yapılandırabilirsiniz <xref:System.Net.Http.HttpClientHandler> çağırarak sınıfı <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="bdb24-219">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty="nameWithType"> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.useSocketsHttpHandler", false);
```

<span data-ttu-id="bdb24-220">Bir ortam de kullanabilirsiniz kullanarak dışında tercih değişkeni yuva göre uygulamaları <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="bdb24-220">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="bdb24-221">Bunu yapmak için ayarlayın `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` ya da `false` veya 0.</span><span class="sxs-lookup"><span data-stu-id="bdb24-221">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="bdb24-222">Windows, ayrıca kullanmayı tercih edebilirsiniz <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, yerel bir uygulama üzerinde kullanır veya <xref:System.Net.Http.SocketsHttpHandler> sınıfının bir örneğini geçirerek sınıfı <xref:System.Net.Http.HttpClient> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="bdb24-222">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="bdb24-223">Linux ve macOS, yalnızca yapılandırabilirsiniz <xref:System.Net.Http.HttpClient> işlem başına temelinde.</span><span class="sxs-lookup"><span data-stu-id="bdb24-223">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="bdb24-224">Linux üzerinde dağıtmanız gerekir. [libcurl](https://curl.haxx.se/libcurl/) eski kullanmak istiyorsanız, <xref:System.Net.Http.HttpClient> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="bdb24-224">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="bdb24-225">(.NET Core 2.0 ile yüklenir.)</span><span class="sxs-lookup"><span data-stu-id="bdb24-225">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="bdb24-226">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdb24-226">See also</span></span>

[<span data-ttu-id="bdb24-227">​.NET Core'daki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="bdb24-227">What's new in .NET Core</span></span>](index.md)  
[<span data-ttu-id="bdb24-228">EF çekirdek 2.1 yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="bdb24-228">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)  
[<span data-ttu-id="bdb24-229">ASP.NET Core 2.1 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="bdb24-229">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
