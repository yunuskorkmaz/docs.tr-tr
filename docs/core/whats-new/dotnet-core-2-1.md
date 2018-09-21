---
title: .NET Core 2.1 yenilikler nelerdir?
description: .NET Core 2.1 içinde bulunan yeni özellikler hakkında bilgi edinin.
author: rpetrusha
ms.author: ronpet
ms.date: 06/06/2018
ms.openlocfilehash: aa80e6b7214f91c49803adde49a1e03d1971b3f6
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/20/2018
ms.locfileid: "46473466"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="34090-103">.NET Core 2.1 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="34090-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="34090-104">.NET core 2.1 aşağıdaki alanlarda geliştirmeler ve yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="34090-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="34090-105">Araç kullanımı</span><span class="sxs-lookup"><span data-stu-id="34090-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="34090-106">İleri Sarma</span><span class="sxs-lookup"><span data-stu-id="34090-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="34090-107">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="34090-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="34090-108">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="34090-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="34090-109">JIT derleme geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="34090-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="34090-110">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="34090-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="34090-111">Araç kullanımı</span><span class="sxs-lookup"><span data-stu-id="34090-111">Tooling</span></span>

<span data-ttu-id="34090-112">.NET Core 2.1 SDK'sı (v 2.1.300), .NET Core 2.1 ile dahil olan araçları, aşağıdaki değişiklikler ve iyileştirmeler içerir:</span><span class="sxs-lookup"><span data-stu-id="34090-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="34090-113">Derleme performans geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="34090-113">Build performance improvements</span></span>

<span data-ttu-id="34090-114">Özellikle, artımlı derlemeleri için derleme zamanında kalkış performansı önemli bir .NET Core 2.1 odağı gelişiyor.</span><span class="sxs-lookup"><span data-stu-id="34090-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="34090-115">Bu performans geliştirmelerine kullanarak her iki komut satırı derlemeleri uygulama `dotnet build` ve Visual Studio'daki derlemeler.</span><span class="sxs-lookup"><span data-stu-id="34090-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="34090-116">Tek tek bazı geliştirilecek alanlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="34090-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="34090-117">Paket varlık çözümlemesi için yalnızca tüm varlıkları yerine bir derleme tarafından kullanılan varlıklar çözümleniyor.</span><span class="sxs-lookup"><span data-stu-id="34090-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="34090-118">Derleme başvuruları önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="34090-118">Caching of assembly references.</span></span>

- <span data-ttu-id="34090-119">Uzun süre çalışan SDK kullanımı arasında bireysel kapsayan süreçleri sunucuları, derleme `dotnet build` çağrıları.</span><span class="sxs-lookup"><span data-stu-id="34090-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="34090-120">Bunlar her zaman büyük kod bloklarını JIT derleme gereksinimi ortadan `dotnet build` çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="34090-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="34090-121">Derleme işlemlerini otomatik olarak aşağıdaki komutla sonlandırılabilir sunucusu:</span><span class="sxs-lookup"><span data-stu-id="34090-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="34090-122">Yeni CLI komutları</span><span class="sxs-lookup"><span data-stu-id="34090-122">New CLI commands</span></span>

<span data-ttu-id="34090-123">Yalnızca bir proje kullanarak mevcut Araçlar [ `DotnetCliToolReference` ](../tools/extensibility.md) artık .NET Core SDK'sını bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="34090-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="34090-124">Bu araçlar şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="34090-124">These tools include:</span></span>

- <span data-ttu-id="34090-125">`dotnet watch` belirlenmiş bir komut kümesini çalıştırmadan önce değiştirmek bir dosya için bekleyen bir dosya sistemi İzleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="34090-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="34090-126">Örneğin, aşağıdaki komutu otomatik olarak geçerli proje oluşturur ve bir dosyada her değiştiğinde ayrıntılı çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="34090-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```console
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="34090-127">Not `--` önündeki seçeneği `--verbose` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="34090-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="34090-128">Doğrudan geçirilen seçenekleri sınırlandırır `dotnet watch` alt öğesine geçirilen bağımsız değişkenler komutunu `dotnet` işlem.</span><span class="sxs-lookup"><span data-stu-id="34090-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="34090-129">Bu olmadan, `--verbose` seçeneği uygulandığı `dotnet watch` komutu, `dotnet build` komutu.</span><span class="sxs-lookup"><span data-stu-id="34090-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="34090-130">Daha fazla bilgi için [dotnet izleme kullanarak ASP.NET Core geliştirme uygulamaları](/aspnet/core/tutorials/dotnet-watch)</span><span class="sxs-lookup"><span data-stu-id="34090-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span></span>

- <span data-ttu-id="34090-131">`dotnet dev-certs` oluşturur ve ASP.NET Core uygulamaları geliştirme sırasında kullanılan sertifikalar yönetir.</span><span class="sxs-lookup"><span data-stu-id="34090-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="34090-132">`dotnet user-secrets` ASP.NET Core uygulamalarında kullanıcı bir gizli dizi deposu gizli yönetir.</span><span class="sxs-lookup"><span data-stu-id="34090-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="34090-133">`dotnet sql-cache` Dağıtılmış önbelleğe alma işlemi için kullanılacak bir Microsoft SQL Server veritabanındaki bir tablo ve dizin oluşturur.</span><span class="sxs-lookup"><span data-stu-id="34090-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="34090-134">`dotnet ef` veritabanlarını yönetmek için bir araçtır <xref:Microsoft.EntityFrameworkCore.DbContext> nesneleri ve Entity Framework Core uygulamalarında geçişler.</span><span class="sxs-lookup"><span data-stu-id="34090-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="34090-135">Daha fazla bilgi için [EF Core .NET komut satırı araçları](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="34090-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="34090-136">Genel araçları</span><span class="sxs-lookup"><span data-stu-id="34090-136">Global Tools</span></span>

<span data-ttu-id="34090-137">.NET core 2.1 destekler *genel Araçları* --genel olarak komut satırından kullanılabilen diğer bir deyişle, özel araçlar.</span><span class="sxs-lookup"><span data-stu-id="34090-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="34090-138">Genişletilebilirlik modeli '.NET Core önceki sürümlerinde özel araçlarla proje bazında yalnızca kullanarak sunulan [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).</span><span class="sxs-lookup"><span data-stu-id="34090-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="34090-139">Genel bir aracı yüklemek için kullandığınız [dotnet aracı yükleme](../tools/dotnet-tool-install.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="34090-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="34090-140">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="34090-140">For example:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="34090-141">Yüklendikten sonra aracı komut satırından aracı adı belirtilerek çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="34090-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="34090-142">Daha fazla bilgi için [.NET Core Araçları Genel genel bakış](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="34090-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="34090-143">Aracı ile Yönetim `dotnet tool` komutu</span><span class="sxs-lookup"><span data-stu-id="34090-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="34090-144">.NET Core SDK 2.1 (v 2.1.300), tüm araçları işlemler kullanın `dotnet tool` komutu.</span><span class="sxs-lookup"><span data-stu-id="34090-144">In .NET Core SDK 2.1 (v 2.1.300), all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="34090-145">Aşağıdaki seçenekler mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="34090-145">The following options are available:</span></span>

- <span data-ttu-id="34090-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) bir aracı yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="34090-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="34090-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) etkili bir şekilde güncelleştiren bir aracı kaldırıp için.</span><span class="sxs-lookup"><span data-stu-id="34090-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="34090-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) şu anda listelemek için araçları yüklü.</span><span class="sxs-lookup"><span data-stu-id="34090-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="34090-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) şu anda yüklü araçları kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="34090-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="34090-150">İleri Sarma</span><span class="sxs-lookup"><span data-stu-id="34090-150">Roll forward</span></span>

<span data-ttu-id="34090-151">.NET Core 2.0 ile otomatik olarak itibaren tüm .NET Core uygulamaları en son İleri sarmanın *podverze* bir sisteme yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="34090-151">All .NET Core applications starting with the .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="34090-152">Bir uygulamanın derlendiği .NET Core sürümü çalışma zamanında mevcut değilse, .NET Core 2.0 ile başlayarak, uygulama otomatik olarak en son yüklenen karşı çalışır *podverze* .NET core'un.</span><span class="sxs-lookup"><span data-stu-id="34090-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="34090-153">Diğer bir deyişle, .NET Core 2.0 ile bir uygulama oluşturulur ve .NET Core 2.1 .NET Core 2.0, ana sistemde mevcut değil. ancak, uygulama .NET Core 2.1 ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="34090-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="34090-154">Bu sarma davranışı Önizleme sürümleri için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="34090-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="34090-155">Ya da ana sürümler için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="34090-155">Nor does it apply to major releases.</span></span> <span data-ttu-id="34090-156">Örneğin, bir .NET Core 1.0 uygulamasını İleri .NET Core 2.0 veya .NET Core 2.1 döküm mıydı.</span><span class="sxs-lookup"><span data-stu-id="34090-156">For example, a .NET Core 1.0 application wouldn't roll forward to .NET Core 2.0 or .NET Core 2.1.</span></span>

<span data-ttu-id="34090-157">Alt sürüm ileri sarma içinde üç yoldan herhangi birini devre dışı bırakabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="34090-157">You can also disable minor version roll forward in any of three ways:</span></span>

- <span data-ttu-id="34090-158">Ayarlama `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` ortam değişkeni 0.</span><span class="sxs-lookup"><span data-stu-id="34090-158">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to 0.</span></span>

- <span data-ttu-id="34090-159">Aşağıdaki satırı runtimeconfig.json dosyaya ekleyin:</span><span class="sxs-lookup"><span data-stu-id="34090-159">Add the following line to the runtimeconfig.json file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="34090-160">Kullanırken [.NET Core CLI Araçları](../tools/index.md), .NET Core komut aşağıdaki seçenek gibi dahil `run`:</span><span class="sxs-lookup"><span data-stu-id="34090-160">When using [.NET Core CLI tools](../tools/index.md), include the following option with a .NET Core command such as `run`:</span></span>

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

## <a name="deployment"></a><span data-ttu-id="34090-161">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="34090-161">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="34090-162">Kendi içinde Uygulama Bakımı</span><span class="sxs-lookup"><span data-stu-id="34090-162">Self-contained application servicing</span></span>

<span data-ttu-id="34090-163">`dotnet publish` artık kendi başına bir hizmet verilen çalışma zamanı sürümü uygulamalarla yayımlar.</span><span class="sxs-lookup"><span data-stu-id="34090-163">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="34090-164">.NET Core 2.1 SDK'sı (v 2.1.300) kendi içinde bir uygulama yayımladığınızda, uygulamanız bu SDK'sı tarafından bilinen en son hizmet verilen çalışma zamanı sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="34090-164">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="34090-165">En son SDK'yı yükselttiğinizde, en son .NET Core çalışma zamanı sürümüyle yayımlama.</span><span class="sxs-lookup"><span data-stu-id="34090-165">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="34090-166">Bu .NET Core 1.0 çalışma zamanları ve sonrası için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="34090-166">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="34090-167">Çalışma zamanı sürümleri nuget.org müstakil yayımlama kullanır. Hizmet verilen çalışma zamanı, makinenizdeki gerekmez.</span><span class="sxs-lookup"><span data-stu-id="34090-167">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="34090-168">Farklı bir sürümü aracılığıyla belirtilmediği sürece .NET Core 2.0 SDK'sını kullanarak kendi içindeki uygulamaları .NET Core 2.0.0 çalışma zamanı ile yayımlanan `RuntimeFrameworkVersion` özelliği.</span><span class="sxs-lookup"><span data-stu-id="34090-168">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="34090-169">Bu yeni davranış artık kendi içinde bir uygulama için daha yüksek bir çalışma zamanı sürümünü seçmek için bu özelliği ayarlayın gerekir.</span><span class="sxs-lookup"><span data-stu-id="34090-169">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="34090-170">İleriye dönük en kolay yaklaşım .NET Core 2.1 SDK (v 2.1.300) her zaman yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="34090-170">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="34090-171">Daha fazla bilgi için [müstakil azure'daki çalışma zamanı, ileri sarma](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="34090-171">For more information, see [Self-contained deploymnet runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="34090-172">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="34090-172">Windows Compatibility Pack</span></span>

<span data-ttu-id="34090-173">.NET Framework mevcut koddan .NET Core için bağlantı noktası, kullanabileceğiniz [Windows Uyumluluk Paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="34090-173">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="34090-174">' De .NET Core bulunandan daha fazla API 20.000 erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="34090-174">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="34090-175">Bu API'ler türler <xref:System.Drawing?displayProperty=nameWithType> ad alanı, <xref:System.Diagnostics.EventLog> sınıf, WMI, performans sayaçları, Windows Hizmetleri ve Windows kayıt defteri türleri ve üyeleri.</span><span class="sxs-lookup"><span data-stu-id="34090-175">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="34090-176">JIT Derleyici iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="34090-176">JIT compiler improvements</span></span>

<span data-ttu-id="34090-177">.NET core içerir adlı yeni bir JIT derleyicisi teknoloji *katmanlı derleme* (olarak da bilinen *Uyarlamalı iyileştirme*), önemli ölçüde performansı geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="34090-177">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="34090-178">Katmanlı derleme, bir katılım ayarıdır.</span><span class="sxs-lookup"><span data-stu-id="34090-178">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="34090-179">JIT derleyicisi tarafından gerçekleştirilen önemli görevlerinden birini ve kod yürütme en iyi duruma getiriyor.</span><span class="sxs-lookup"><span data-stu-id="34090-179">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="34090-180">Az kullanılan kodu yolları için ancak derleyici iyileştirilmemiş kod çalıştırma, çalışma zamanı geçirdiği daha kodu en iyi duruma getirme daha fazla zaman harcayabilir.</span><span class="sxs-lookup"><span data-stu-id="34090-180">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="34090-181">Katmanlı bir derleme JIT derlemesi iki aşamada sunar:</span><span class="sxs-lookup"><span data-stu-id="34090-181">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="34090-182">A **ilk katman**, mümkün olan en kısa sürede kod oluşturduğu.</span><span class="sxs-lookup"><span data-stu-id="34090-182">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="34090-183">A **ikinci katman**, oluşturduğu kodu sık yürütülen bu yöntemleri için en iyi duruma getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="34090-183">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="34090-184">Derleme, ikinci katman, Gelişmiş performans için paralel gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="34090-184">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="34090-185">İki yöntemden biriyle katmanlı derleme kabul edebileceğiniz.</span><span class="sxs-lookup"><span data-stu-id="34090-185">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="34090-186">.NET Core 2.1 SDK'sını kullanan tüm projelerde katmanlı derleme kullanmak için aşağıdaki ortam değişkenlerini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="34090-186">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="34090-187">Katmanlı derleme proje başına temelinde kullanılacak ekleme `<TieredCompilation>` özelliğini `<PropertyGroup>` MSBuild proje dosyası, aşağıdaki örnekte gösterildiği gibi bir bölümünü:</span><span class="sxs-lookup"><span data-stu-id="34090-187">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="34090-188">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="34090-188">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="34090-189">`Span<T>` ve `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="34090-189">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="34090-190">.NET core 2.1 dizileri ile çalışmayı kolaylaştıran bazı yeni türlerini ve çok daha verimli bellek diğer türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="34090-190">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="34090-191">Yeni türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="34090-191">The new types include:</span></span>

- <span data-ttu-id="34090-192"><xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="34090-192"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="34090-193"><xref:System.Memory%601?displayProperty=nameWithType> ve <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="34090-193"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="34090-194">Bu tür öğeleri dizi değerinin bir bölümü veya bir bölümünü bellek arabelleği olarak geçirirken bu türleri, bir yönteme iletmeden önce bölümü verilerin bir kopyasını yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="34090-194">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="34090-195">Bu türler ek bellek ayırma ve kopyalama işlemleri ihtiyacını ortadan kaldırır, verilerin sanal bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="34090-195">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="34090-196">Aşağıdaki örnekte bir <xref:System.Span%601> dizi 10 öğelerini sanal bir görünümünü sağlamak için örneği.</span><span class="sxs-lookup"><span data-stu-id="34090-196">The following example uses a <xref:System.Span%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

### <a name="brotli-compression"></a><span data-ttu-id="34090-197">Brotli sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="34090-197">Brotli compression</span></span>

<span data-ttu-id="34090-198">.NET core 2.1 Brotli sıkıştırma ve açma desteğini ekler.</span><span class="sxs-lookup"><span data-stu-id="34090-198">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="34090-199">Brotli tanımlanan bir genel amaçlı kayıpsız sıkıştırma algoritması olan [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) ve web tarayıcıları ve ana web sunucuları tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="34090-199">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="34090-200">Akış tabanlı kullanabileceğiniz <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> sınıfı veya yüksek performanslı aralık tabanlı <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> ve <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="34090-200">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="34090-201">Sıkıştırmasıyla aşağıdaki örnekte <xref:System.IO.Compression.BrotliStream> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="34090-201">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<span data-ttu-id="34090-202"><xref:System.IO.Compression.BrotliStream> Davranışı aynıdır <xref:System.IO.Compression.DeflateStream> ve <xref:System.IO.Compression.GZipStream>, kolaylaştıran için bu API'leri çağıran koda dönüştürme <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="34090-202">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="34090-203">Yeni şifreleme API'leri ve şifreleme geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="34090-203">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="34090-204">.NET core 2.1 şifreleme API'leri için çeşitli iyileştirmeler içerir:</span><span class="sxs-lookup"><span data-stu-id="34090-204">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="34090-205"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> System.Security.Cryptography.Pkcs pakette kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34090-205"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="34090-206">Uygulama ile aynı olduğu <xref:System.Security.Cryptography.Pkcs.SignedCms> .NET Framework sınıfı.</span><span class="sxs-lookup"><span data-stu-id="34090-206">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="34090-207">Yeni aşırı yüklemeleri <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> yöntemleri dışında SHA-1 algoritmaları kullanarak sertifika parmak izi değerleri almak çağıranlar etkinleştirmek için bir karma algoritması tanımlayıcı kabul edin.</span><span class="sxs-lookup"><span data-stu-id="34090-207">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="34090-208">Yeni <xref:System.Span%601>-karma işlevi için HMAC, şifreleme rastgele sayı oluşturma, asimetrik imza oluşturma, asimetrik imza işleme ve RSA şifreleme tabanlı şifreleme API'leri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="34090-208">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="34090-209">Performansını <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> yaklaşık 15 oranında kullanılarak geliştirilmiş bir <xref:System.Span%601>-uygulama tabanlı.</span><span class="sxs-lookup"><span data-stu-id="34090-209">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="34090-210">Yeni <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> sınıfı iki yeni yöntemler içerir:</span><span class="sxs-lookup"><span data-stu-id="34090-210">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="34090-211"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> Bu kullanım için uygun yan kanal bilgileri zamanlama için katkıda bulunan önlemek için şifreleme doğrulama yapar aynı uzunlukta iki tüm girişleri için döndürülecek sabit bir süre sürer.</span><span class="sxs-lookup"><span data-stu-id="34090-211"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="34090-212"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> hale getirilemeyen bir bellek temizleme yordamdır.</span><span class="sxs-lookup"><span data-stu-id="34090-212"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="34090-213">Statik <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> yöntemi dolduran bir <xref:System.Span%601> rasgele değerlere sahip.</span><span class="sxs-lookup"><span data-stu-id="34090-213">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="34090-214"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Linux ve maxOS artık desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="34090-214">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and maxOS.</span></span>

- <span data-ttu-id="34090-215">Eliptik Eğri Diffie-Hellman (ECDH) içinde kullanıma sunuldu <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> sınıf ailesi.</span><span class="sxs-lookup"><span data-stu-id="34090-215">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="34090-216">Yüzey alanı .NET Framework olduğu gibi aynıdır.</span><span class="sxs-lookup"><span data-stu-id="34090-216">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="34090-217">Tarafından döndürülen örneği <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> şifrelemek veya şifresini bir SHA-2 özet kullanarak OAEP ile hem de oluşturabilir veya kullanılarak RSA-PSS imza doğrulama.</span><span class="sxs-lookup"><span data-stu-id="34090-217">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="34090-218">Yuva geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="34090-218">Sockets improvements</span></span>

<span data-ttu-id="34090-219">.NET core içeren yeni bir tür <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>ve bir yeniden <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, üst düzey ağ API'leri temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="34090-219">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="34090-220"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, örneğin, temelidir <xref:System.Net.Http.HttpClient> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="34090-220"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="34090-221">.NET Core önceki sürümlerinde, yerel ağ uygulamalarında üst düzey API'ler temel alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="34090-221">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="34090-222">.NET Core 2.1 içinde tanıtılan bir yuva uygulaması, çok sayıda avantaj vardır:</span><span class="sxs-lookup"><span data-stu-id="34090-222">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="34090-223">Önceki bir uygulama ile karşılaştırıldığında önemli bir performans geliştirmesi.</span><span class="sxs-lookup"><span data-stu-id="34090-223">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="34090-224">Dağıtımı ve bakımı kolaylaştıran eleme, platform bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="34090-224">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="34090-225">Tüm .NET Core platformlar genelinde tutarlı davranışı.</span><span class="sxs-lookup"><span data-stu-id="34090-225">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="34090-226"><xref:System.Net.Http.SocketsHttpHandler> .NET Core 2.1 içinde varsayılan uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="34090-226"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="34090-227">Ancak, eski kullanmak için uygulamanızı yapılandırabileceğiniz <xref:System.Net.Http.HttpClientHandler> çağırarak sınıfı <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="34090-227">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="34090-228">Bir ortam kullanabilirsiniz kullanarak dışında kabul etmek için değişken yuva göre uygulamaları <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="34090-228">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="34090-229">Bunu yapmak için ayarlanmış `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` ya da `false` veya 0.</span><span class="sxs-lookup"><span data-stu-id="34090-229">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="34090-230">Windows üzerinde de kullanmayı seçebilirsiniz <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, yerel bir uygulama üzerinde kullanır veya <xref:System.Net.Http.SocketsHttpHandler> sınıfı örneğini geçirerek sınıf <xref:System.Net.Http.HttpClient> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="34090-230">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="34090-231">Linux ve Macos'ta, yalnızca yapılandırabilirsiniz <xref:System.Net.Http.HttpClient> işlem başına temelinde.</span><span class="sxs-lookup"><span data-stu-id="34090-231">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="34090-232">Linux üzerinde dağıtmanız gerekir. [libcurl](https://curl.haxx.se/libcurl/) eski kullanmak istiyorsanız <xref:System.Net.Http.HttpClient> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="34090-232">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="34090-233">(.NET Core 2.0 ile yüklenir.)</span><span class="sxs-lookup"><span data-stu-id="34090-233">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="34090-234">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="34090-234">See also</span></span>

* [<span data-ttu-id="34090-235">​.NET Core'daki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="34090-235">What's new in .NET Core</span></span>](index.md)  
* [<span data-ttu-id="34090-236">EF Core 2.1 yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="34090-236">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)  
* [<span data-ttu-id="34090-237">ASP.NET Core 2.1 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="34090-237">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
