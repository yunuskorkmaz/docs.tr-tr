---
title: ​.NET Core 2.1’deki yenilikler
description: .NET Core 2.1'de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 54ace52fc6a8f4614c1f762b65453979bcb92c7a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398869"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="b385e-103">​.NET Core 2.1’deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="b385e-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="b385e-104">.NET Core 2.1 aşağıdaki alanlardaki geliştirmeleri ve yeni özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b385e-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="b385e-105">Araçlar</span><span class="sxs-lookup"><span data-stu-id="b385e-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="b385e-106">İleri yuvarlan</span><span class="sxs-lookup"><span data-stu-id="b385e-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="b385e-107">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="b385e-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="b385e-108">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="b385e-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="b385e-109">JIT derleme geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b385e-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="b385e-110">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="b385e-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="b385e-111">Araçlar</span><span class="sxs-lookup"><span data-stu-id="b385e-111">Tooling</span></span>

<span data-ttu-id="b385e-112">.NET Core 2.1 SDK (v 2.1.300), .NET Core 2.1 ile birlikte araç, aşağıdaki değişiklikleri ve geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b385e-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="b385e-113">Performans iyileştirmeleri oluşturun</span><span class="sxs-lookup"><span data-stu-id="b385e-113">Build performance improvements</span></span>

<span data-ttu-id="b385e-114">.NET Core 2.1'in ana odak noktası, özellikle artımlı yapılar için yapı zamanı performansını geliştirmektir.</span><span class="sxs-lookup"><span data-stu-id="b385e-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="b385e-115">Bu performans iyileştirmeleri, Visual Studio'da `dotnet build` hem komut satırı kullanarak hem de oluşturmalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b385e-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="b385e-116">Bazı bireysel iyileştirme alanları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b385e-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="b385e-117">Paket kıymet çözümü için, tüm varlıklar yerine yalnızca bir yapı tarafından kullanılan varlıkları çözümleme.</span><span class="sxs-lookup"><span data-stu-id="b385e-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="b385e-118">Derleme başvurularının önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="b385e-118">Caching of assembly references.</span></span>

- <span data-ttu-id="b385e-119">Uzun süredir çalışan SDK yapı sunucularının kullanımı, `dotnet build` tek tek çağrıları kapsayan işlemlerdir.</span><span class="sxs-lookup"><span data-stu-id="b385e-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="b385e-120">Her çalıştırılışta `dotnet build` büyük kod bloklarını JIT derleme gereksinimini ortadan kaldırırlar.</span><span class="sxs-lookup"><span data-stu-id="b385e-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="b385e-121">Yapı sunucusu işlemleri aşağıdaki komutla otomatik olarak sonlandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="b385e-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="b385e-122">Yeni CLI komutları</span><span class="sxs-lookup"><span data-stu-id="b385e-122">New CLI commands</span></span>

<span data-ttu-id="b385e-123">Sadece proje bazında `DotnetCliToolReference` kullanılabilen bir dizi araç artık .NET Core SDK'nın bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b385e-123">A number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="b385e-124">Bu araçlar şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="b385e-124">These tools include:</span></span>

- <span data-ttu-id="b385e-125">`dotnet watch`belirlenmiş bir komut kümesini yürütmeden önce bir dosyanın değişmesini bekleyen bir dosya sistemi izleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b385e-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="b385e-126">Örneğin, aşağıdaki komut geçerli projeyi otomatik olarak yeniden oluşturur ve içinde bir dosya değiştiğinde ayrıntılı çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="b385e-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="b385e-127">Seçenekten `--` önce gelen `--verbose` seçeneği not edin.</span><span class="sxs-lookup"><span data-stu-id="b385e-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="b385e-128">Alt `dotnet watch` `dotnet` işleme geçirilen bağımsız değişkenlerden doğrudan komuta geçirilen seçenekleri sınırlandırmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b385e-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="b385e-129">Onsuz, `--verbose` seçenek `dotnet watch` `dotnet build` komut için değil, komut için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b385e-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="b385e-130">Daha fazla bilgi için [dotnet watch kullanarak ASP.NET Core uygulamaları geliştir'e](/aspnet/core/tutorials/dotnet-watch)bakın.</span><span class="sxs-lookup"><span data-stu-id="b385e-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch).</span></span>

- <span data-ttu-id="b385e-131">`dotnet dev-certs`ASP.NET Core uygulamalarında geliştirme sırasında kullanılan sertifikaları oluşturur ve yönetir.</span><span class="sxs-lookup"><span data-stu-id="b385e-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="b385e-132">`dotnet user-secrets`ASP.NET Core uygulamalarında bir kullanıcı gizli mağazasında sırları yönetir.</span><span class="sxs-lookup"><span data-stu-id="b385e-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="b385e-133">`dotnet sql-cache`dağıtılmış önbelleğe alma için kullanılmak üzere Microsoft SQL Server veritabanında bir tablo ve dizinler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="b385e-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="b385e-134">`dotnet ef`Varlık Framework Core uygulamalarındaki <xref:Microsoft.EntityFrameworkCore.DbContext> veritabanlarını, nesneleri ve geçişleri yönetmek için bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="b385e-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="b385e-135">Daha fazla bilgi için [BKZ.](/ef/core/miscellaneous/cli/dotnet)</span><span class="sxs-lookup"><span data-stu-id="b385e-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="b385e-136">Genel Araçlar</span><span class="sxs-lookup"><span data-stu-id="b385e-136">Global Tools</span></span>

<span data-ttu-id="b385e-137">.NET Core 2.1, *Genel Araçları* destekler -- yani komut satırından küresel olarak kullanılabilen özel araçlar.</span><span class="sxs-lookup"><span data-stu-id="b385e-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="b385e-138">.NET Core'un önceki sürümlerindeki genişletilebilirlik modeli, özel araçları yalnızca `DotnetCliToolReference`proje bazında kullanılabilir hale getirdi.</span><span class="sxs-lookup"><span data-stu-id="b385e-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using `DotnetCliToolReference`.</span></span>

<span data-ttu-id="b385e-139">Genel Bir Araç yüklemek için [dotnet aracı yükleme](../tools/dotnet-tool-install.md) komutunu kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="b385e-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="b385e-140">Örnek:</span><span class="sxs-lookup"><span data-stu-id="b385e-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="b385e-141">Yüklendikten sonra, araç komut satırından araç adını belirterek çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b385e-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="b385e-142">Daha fazla bilgi için [.NET Core Global Tools genel bakış](../tools/global-tools.md)bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="b385e-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="b385e-143">`dotnet tool` Komut ile araç yönetimi</span><span class="sxs-lookup"><span data-stu-id="b385e-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="b385e-144">.NET Core 2.1 SDK'da tüm `dotnet tool` araçlar işlemleri komutu kullanır.</span><span class="sxs-lookup"><span data-stu-id="b385e-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="b385e-145">Aşağıdaki seçenekler mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="b385e-145">The following options are available:</span></span>

- <span data-ttu-id="b385e-146">[`dotnet tool install`](../tools/dotnet-tool-install.md)bir araç yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="b385e-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="b385e-147">[`dotnet tool update`](../tools/dotnet-tool-update.md)etkili bir şekilde güncelleyen bir aracı kaldırmak ve yeniden yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="b385e-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="b385e-148">[`dotnet tool list`](../tools/dotnet-tool-list.md)şu anda yüklü araçları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="b385e-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="b385e-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md)şu anda yüklü araçları kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="b385e-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="b385e-150">İleri yuvarlan</span><span class="sxs-lookup"><span data-stu-id="b385e-150">Roll forward</span></span>

<span data-ttu-id="b385e-151">.NET Core 2.0 ile başlayan tüm .NET Core uygulamaları otomatik olarak bir sisteme yüklenen en son *küçük sürüme* doğru ilerler.</span><span class="sxs-lookup"><span data-stu-id="b385e-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="b385e-152">.NET Core 2.0 ile başlayarak, bir uygulamanın birlikte üretilmiş olduğu .NET Core sürümü çalışma zamanında yoksa, uygulama otomatik olarak .NET Core'un en son yüklenen *küçük sürümüne* göre çalışır.</span><span class="sxs-lookup"><span data-stu-id="b385e-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="b385e-153">Başka bir deyişle, bir uygulama .NET Core 2.0 ile oluşturulmuşsa ve .NET Core 2.0 ana bilgisayar sisteminde yoksa,.NET Core 2.1 ise, uygulama .NET Core 2.1 ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="b385e-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b385e-154">Bu roll-forward davranışı önizleme sürümleri için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="b385e-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="b385e-155">Varsayılan olarak, büyük sürümler için de geçerli değildir, ancak bu aşağıdaki ayarlarla değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b385e-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="b385e-156">Bu davranışı, aday paylaşılan bir çerçevede yuvarlanmayın ayarını değiştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b385e-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="b385e-157">Kullanılabilir ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b385e-157">The available settings are:</span></span>

- <span data-ttu-id="b385e-158">`0`- küçük sürüm roll-forward davranışını devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="b385e-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="b385e-159">Bu ayar ile .NET Core 2.0.0 için oluşturulmuş bir uygulama .NET Core 2.0.1'e doğru iletilir, ancak .NET Core 2.2.0 veya .NET Core 3.0.0'a değil.</span><span class="sxs-lookup"><span data-stu-id="b385e-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="b385e-160">`1`- küçük sürüm roll-forward davranışını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b385e-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="b385e-161">Bu, ayar için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="b385e-161">This is the default value for the setting.</span></span> <span data-ttu-id="b385e-162">Bu ayar ile .NET Core 2.0.0 için oluşturulmuş bir uygulama,.NET Core 2.0.1 veya .NET Core 2.2.0'a, hangisinin yüklendiğine bağlı olarak ileri ye doğru yuvarlanır, ancak .NET Core 3.0.0'a doğru yuvarlanmayacaktır.</span><span class="sxs-lookup"><span data-stu-id="b385e-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="b385e-163">`2`- küçük ve ana sürüm roll-forward davranışını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b385e-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="b385e-164">Ayarlanırsa, farklı ana sürümler bile dikkate alınır, bu nedenle .NET Core 2.0.0 için oluşturulmuş bir uygulama .NET Core 3.0.0'a doğru yuvarlanır.</span><span class="sxs-lookup"><span data-stu-id="b385e-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="b385e-165">Bu ayarı üç şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b385e-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="b385e-166">Ortam `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` değişkenini istenilen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b385e-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="b385e-167">*.runtimeconfig.json* dosyasına istenilen değere sahip aşağıdaki satırı ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b385e-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="b385e-168">[.NET Core CLI](../tools/index.md)kullanırken, aşağıdaki seçeneği istenilen değere sahip bir `run`.NET Core komutu gibi ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b385e-168">When using the [.NET Core CLI](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="b385e-169">Patch sürüm roll forward bu ayarınbağımsızdır ve herhangi bir potansiyel küçük veya ana sürüm roll forward uygulandıktan sonra yapılır.</span><span class="sxs-lookup"><span data-stu-id="b385e-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="b385e-170">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="b385e-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="b385e-171">Bağımsız uygulama hizmeti</span><span class="sxs-lookup"><span data-stu-id="b385e-171">Self-contained application servicing</span></span>

<span data-ttu-id="b385e-172">`dotnet publish`şimdi hizmet eken çalışma zamanı sürümüyle bağımsız uygulamalar yayımlar.</span><span class="sxs-lookup"><span data-stu-id="b385e-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="b385e-173">.NET Core 2.1 SDK (v 2.1.300) ile bağımsız bir uygulama yayımladığınızda, uygulamanız bu SDK tarafından bilinen en son servisli çalışma zamanı sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="b385e-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="b385e-174">En son SDK'ya yükselttiğinde, en son .NET Core çalışma zamanı sürümüyle yayımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="b385e-174">When you upgrade to the latest SDK, you'll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="b385e-175">Bu, .NET Core 1.0 çalışma saatleri ve sonrası için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="b385e-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="b385e-176">Bağımsız yayımlama, NuGet.org'daki çalışma zamanı sürümlerine dayanır. Makinenizde servis edilen çalışma süresine sahip olmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b385e-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="b385e-177">.NET Core 2.0 SDK kullanılarak, `RuntimeFrameworkVersion` özellik üzerinden farklı bir sürüm belirtilmedikçe,.NET Core 2.0.0 çalışma süresi ile bağımsız uygulamalar yayınlanır.</span><span class="sxs-lookup"><span data-stu-id="b385e-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="b385e-178">Bu yeni davranışla, artık bu özelliği, bağımsız bir uygulama için daha yüksek bir çalışma zamanı sürümü seçecek şekilde ayarlamanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b385e-178">With this new behavior, you'll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="b385e-179">İleriye dönük en kolay yaklaşım her zaman .NET Core 2.1 SDK (v 2.1.300) ile yayınlamaktır.</span><span class="sxs-lookup"><span data-stu-id="b385e-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="b385e-180">Daha fazla bilgi için bkz: [Bağımsız dağıtım çalışma zamanı ileri sarma.](../deploying/runtime-patch-selection.md)</span><span class="sxs-lookup"><span data-stu-id="b385e-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="b385e-181">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="b385e-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="b385e-182">Varolan kodu .NET Framework'den .NET Core'a taşımadığınızda, [Windows Uyumluluk Paketini](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b385e-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="b385e-183">.NET Core'da bulunandan 20.000 daha fazla API'ye erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="b385e-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="b385e-184">Bu API'ler <xref:System.Drawing?displayProperty=nameWithType> ad alanı, <xref:System.Diagnostics.EventLog> sınıf, WMI, Performans Sayaçları, Windows Hizmetleri ve Windows kayıt defteri türleri ve üyeleri türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b385e-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="b385e-185">JIT derleyici geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b385e-185">JIT compiler improvements</span></span>

<span data-ttu-id="b385e-186">.NET Core, performansı önemli ölçüde artırabilen *katmanlı derleme* *(uyarlamalı optimizasyon*olarak da bilinir) adı verilen yeni bir JIT derleyici sİstemi içerir.</span><span class="sxs-lookup"><span data-stu-id="b385e-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="b385e-187">Katmanlı derleme bir opt-in ayarıdır.</span><span class="sxs-lookup"><span data-stu-id="b385e-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="b385e-188">JIT derleyicisi tarafından gerçekleştirilen önemli görevlerden biri kod yürütmeyi en iyi duruma getirmektir.</span><span class="sxs-lookup"><span data-stu-id="b385e-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="b385e-189">Ancak az kullanılan kod yolları için derleyici, en iyi duruma getirilmemiş kodu çalıştırmak için çalışma süresi harcadığından daha fazla zaman geçirebilir.</span><span class="sxs-lookup"><span data-stu-id="b385e-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="b385e-190">Katmanlı derleme JIT derlemesinde iki aşama yı tanıtır:</span><span class="sxs-lookup"><span data-stu-id="b385e-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="b385e-191">Kodu mümkün olduğunca çabuk üreten **birinci katman.**</span><span class="sxs-lookup"><span data-stu-id="b385e-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="b385e-192">Sık sık yürütülen bu yöntemler için en iyi duruma getirilmiş kod üreten ikinci bir **katman.**</span><span class="sxs-lookup"><span data-stu-id="b385e-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="b385e-193">İkinci derleme katmanı, gelişmiş performans için paralel olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b385e-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="b385e-194">Katmanlı derlemeyi iki şekilde de seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b385e-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="b385e-195">.NET Core 2.1 SDK kullanan tüm projelerde katmanlı derleme kullanmak için aşağıdaki ortam değişkenini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="b385e-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="b385e-196">Katmanlı derlemeyi proje başına kullanmak için, aşağıdaki `<TieredCompilation>` örnekte `<PropertyGroup>` görüldüğü gibi özelliği MSBuild proje dosyasının bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="b385e-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="b385e-197">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="b385e-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="b385e-198">`Span<T>` ve `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="b385e-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="b385e-199">.NET Core 2.1 dizileri ve bellek diğer türleri ile çalışma çok daha verimli hale bazı yeni türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b385e-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="b385e-200">Yeni türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="b385e-200">The new types include:</span></span>

- <span data-ttu-id="b385e-201"><xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b385e-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="b385e-202"><xref:System.Memory%601?displayProperty=nameWithType> ve <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b385e-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b385e-203">Bu türler olmadan, bu tür öğeleri bir dizinin bölümü veya bellek arabelleği bölümü olarak geçerken, bir yönteme geçirmeden önce verilerin bir bölümünün bir kopyasını oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b385e-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="b385e-204">Bu türler, ek bellek ayırma ve kopyalama işlemleri gereksinimini ortadan kaldıran bu verilerin sanal bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="b385e-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="b385e-205">Aşağıdaki örnek, <xref:System.Span%601> bir <xref:System.Memory%601> dizinin 10 öğesinin sanal görünümünü sağlamak için bir ve örnek kullanır.</span><span class="sxs-lookup"><span data-stu-id="b385e-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/program.cs)]

[!code-vb[Memory\<T>](~/samples/snippets/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="b385e-206">Brotli sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="b385e-206">Brotli compression</span></span>

<span data-ttu-id="b385e-207">.NET Core 2.1 Brotli sıkıştırma ve dekompresyon desteği ekler.</span><span class="sxs-lookup"><span data-stu-id="b385e-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="b385e-208">Brotli, [RFC 7932'de](https://www.ietf.org/rfc/rfc7932.txt) tanımlanan ve çoğu web tarayıcısı ve büyük web sunucuları tarafından desteklenen genel amaçlı kayıpsız sıkıştırma algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="b385e-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="b385e-209">Akış tabanlı <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> sınıfı veya yüksek performanslı yayılma tabanlı <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> ve sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b385e-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="b385e-210">Aşağıdaki örnek, sınıfla <xref:System.IO.Compression.BrotliStream> sıkıştırmayı göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="b385e-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/csharp/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/snippets/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

<span data-ttu-id="b385e-211">Davranış <xref:System.IO.Compression.BrotliStream> aynıdır <xref:System.IO.Compression.DeflateStream> ve <xref:System.IO.Compression.GZipStream>, bu API'leri <xref:System.IO.Compression.BrotliStream>çağıran kodu dönüştürmeyi kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="b385e-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="b385e-212">Yeni şifreleme API'leri ve şifreleme geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b385e-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="b385e-213">.NET Core 2.1 şifreleme API'leri için çok sayıda geliştirme içerir:</span><span class="sxs-lookup"><span data-stu-id="b385e-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="b385e-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>System.Security.Cryptography.Pkcs paketinde mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b385e-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="b385e-215">Uygulama .NET Framework'deki <xref:System.Security.Cryptography.Pkcs.SignedCms> sınıfla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b385e-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="b385e-216">Yeni aşırı yükler <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> ve yöntemler, arayanların SHA-1 dışındaki algoritmaları kullanarak sertifika parmak izi değerlerini almalarını sağlamak için karma algoritma tanımlayıcısını kabul eder.</span><span class="sxs-lookup"><span data-stu-id="b385e-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="b385e-217">Karma, HMAC, şifreleme rastgele sayı oluşturma, asimetrik imza oluşturma, asimetrik imza işleme ve RSA şifrelemesi için yeni <xref:System.Span%601>tabanlı şifreleme API'leri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b385e-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="b385e-218">Performans, <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> tabanlı bir <xref:System.Span%601>uygulama kullanılarak yaklaşık %15 oranında iyileşmiştir.</span><span class="sxs-lookup"><span data-stu-id="b385e-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="b385e-219">Yeni <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> sınıf iki yeni yöntem içerir:</span><span class="sxs-lookup"><span data-stu-id="b385e-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="b385e-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>aynı uzunluktaki iki giriş için döndürülmesi için belirli bir süre alır, bu da yan kanal bilgilerinin zamanlamasına katkıda bulunmaktan kaçınmak için şifreleme doğrulamada kullanıma uygun hale getirir.</span><span class="sxs-lookup"><span data-stu-id="b385e-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="b385e-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>en iyi duruma getirilen bir bellek temizleme yordamıdır.</span><span class="sxs-lookup"><span data-stu-id="b385e-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="b385e-222">Statik <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> yöntem a'yı <xref:System.Span%601> rasgele değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="b385e-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="b385e-223">Şimdi <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Linux ve macOS üzerinde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="b385e-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and macOS.</span></span>

- <span data-ttu-id="b385e-224">Eliptik-Eğri Diffie-Hellman (ECDH) artık <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> sınıf ailesinde mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="b385e-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="b385e-225">Yüzey alanı .NET Framework ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b385e-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="b385e-226">Döndürülen <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> örnek, SHA-2 özeti kullanarak OAEP ile şifrelenebilir veya şifresini çözebilir ve RSA-PSS kullanarak imza oluşturabilir veya doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="b385e-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="b385e-227">Soket iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="b385e-227">Sockets improvements</span></span>

<span data-ttu-id="b385e-228">.NET Core, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>üst düzey ağ API'lerinin temelini oluşturan yeni bir tür ve yeniden yazılmış <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>bir tür içerir.</span><span class="sxs-lookup"><span data-stu-id="b385e-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="b385e-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, örneğin, uygulamanın <xref:System.Net.Http.HttpClient> temelidir.</span><span class="sxs-lookup"><span data-stu-id="b385e-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="b385e-230">.NET Core'un önceki sürümlerinde, üst düzey API'ler yerel ağ uygulamalarını temel alıyordu.</span><span class="sxs-lookup"><span data-stu-id="b385e-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="b385e-231">.NET Core 2.1'de tanıtılan soket uygulamasının bir takım avantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="b385e-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="b385e-232">Önceki uygulamaile karşılaştırıldığında önemli bir performans artışı.</span><span class="sxs-lookup"><span data-stu-id="b385e-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="b385e-233">Dağıtım ve servis işlemlerini kolaylaştıran platform bağımlılıklarının ortadan kaldırılması.</span><span class="sxs-lookup"><span data-stu-id="b385e-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="b385e-234">Tüm .NET Core platformlarında tutarlı davranış.</span><span class="sxs-lookup"><span data-stu-id="b385e-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="b385e-235"><xref:System.Net.Http.SocketsHttpHandler>.NET Core 2.1'deki varsayılan uygulamadır.</span><span class="sxs-lookup"><span data-stu-id="b385e-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="b385e-236">Ancak, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemi çağırarak uygulamanızı eski <xref:System.Net.Http.HttpClientHandler> sınıfı kullanacak şekilde yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b385e-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="b385e-237">Soket uygulamalarını temel alan uygulamadan çıkmak için bir <xref:System.Net.Http.SocketsHttpHandler>ortam değişkeni de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b385e-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="b385e-238">Bunu yapmak için, `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` ya `false` da 0 ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="b385e-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="b385e-239">Windows'da, sınıfın bir <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>örneğini <xref:System.Net.Http.HttpClient> oluşturucuya geçirerek yerel <xref:System.Net.Http.SocketsHttpHandler> bir uygulamaya veya sınıfa dayanan bir sınıfı kullanmayı da seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b385e-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="b385e-240">Linux ve macOS'ta yalnızca <xref:System.Net.Http.HttpClient> işlem başına göre yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b385e-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="b385e-241">Linux'ta, eski <xref:System.Net.Http.HttpClient> uygulamayı kullanmak istiyorsanız [libcurl](https://curl.haxx.se/libcurl/) dağıtmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b385e-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="b385e-242">(.NET Core 2.0 ile yüklenir.)</span><span class="sxs-lookup"><span data-stu-id="b385e-242">(It is installed with .NET Core 2.0.)</span></span>

### <a name="breaking-changes"></a><span data-ttu-id="b385e-243">Yeni değişiklikler</span><span class="sxs-lookup"><span data-stu-id="b385e-243">Breaking changes</span></span>

<span data-ttu-id="b385e-244">Değişiklikleri kesme hakkında bilgi için, [sürüm 2.0'dan 2.1'e geçiş için Kesme değişikliklerine](../compatibility/2.0-2.1.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="b385e-244">For information about breaking changes, see [Breaking changes for migration from version 2.0 to 2.1](../compatibility/2.0-2.1.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b385e-245">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b385e-245">See also</span></span>

- [<span data-ttu-id="b385e-246">​.NET Core'daki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="b385e-246">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="b385e-247">EF Core 2.1'deki yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="b385e-247">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="b385e-248">ASP.NET Core 2.1'deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="b385e-248">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
