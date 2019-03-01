---
title: .NET Core 2.1 yenilikler nelerdir?
description: .NET Core 2.1 içinde bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 10/10/2018
ms.openlocfilehash: e28ff83d673951a978e24d9c89621fbbe950f50e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975218"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="d46fd-103">.NET Core 2.1 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="d46fd-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="d46fd-104">.NET core 2.1 aşağıdaki alanlarda geliştirmeler ve yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="d46fd-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="d46fd-105">Araç kullanımı</span><span class="sxs-lookup"><span data-stu-id="d46fd-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="d46fd-106">İleri Sarma</span><span class="sxs-lookup"><span data-stu-id="d46fd-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="d46fd-107">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="d46fd-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="d46fd-108">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="d46fd-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="d46fd-109">JIT derleme geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d46fd-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="d46fd-110">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="d46fd-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="d46fd-111">Araç kullanımı</span><span class="sxs-lookup"><span data-stu-id="d46fd-111">Tooling</span></span>

<span data-ttu-id="d46fd-112">.NET Core 2.1 SDK'sı (v 2.1.300), .NET Core 2.1 ile dahil olan araçları, aşağıdaki değişiklikler ve iyileştirmeler içerir:</span><span class="sxs-lookup"><span data-stu-id="d46fd-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="d46fd-113">Derleme performans geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d46fd-113">Build performance improvements</span></span>

<span data-ttu-id="d46fd-114">Özellikle, artımlı derlemeleri için derleme zamanında kalkış performansı önemli bir .NET Core 2.1 odağı gelişiyor.</span><span class="sxs-lookup"><span data-stu-id="d46fd-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="d46fd-115">Bu performans geliştirmelerine kullanarak her iki komut satırı derlemeleri uygulama `dotnet build` ve Visual Studio'daki derlemeler.</span><span class="sxs-lookup"><span data-stu-id="d46fd-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="d46fd-116">Tek tek bazı geliştirilecek alanlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d46fd-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="d46fd-117">Paket varlık çözümlemesi için yalnızca tüm varlıkları yerine bir derleme tarafından kullanılan varlıklar çözümleniyor.</span><span class="sxs-lookup"><span data-stu-id="d46fd-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="d46fd-118">Derleme başvuruları önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="d46fd-118">Caching of assembly references.</span></span>

- <span data-ttu-id="d46fd-119">Uzun süre çalışan SDK kullanımı arasında bireysel kapsayan süreçleri sunucuları, derleme `dotnet build` çağrıları.</span><span class="sxs-lookup"><span data-stu-id="d46fd-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="d46fd-120">Bunlar her zaman büyük kod bloklarını JIT derleme gereksinimi ortadan `dotnet build` çalıştırılır.</span><span class="sxs-lookup"><span data-stu-id="d46fd-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="d46fd-121">Derleme işlemlerini otomatik olarak aşağıdaki komutla sonlandırılabilir sunucusu:</span><span class="sxs-lookup"><span data-stu-id="d46fd-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```console
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="d46fd-122">Yeni CLI komutları</span><span class="sxs-lookup"><span data-stu-id="d46fd-122">New CLI commands</span></span>

<span data-ttu-id="d46fd-123">Yalnızca bir proje kullanarak mevcut Araçlar [ `DotnetCliToolReference` ](../tools/extensibility.md) artık .NET Core SDK'sını bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="d46fd-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="d46fd-124">Bu araçlar şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="d46fd-124">These tools include:</span></span>

- <span data-ttu-id="d46fd-125">`dotnet watch` belirlenmiş bir komut kümesini çalıştırmadan önce değiştirmek bir dosya için bekleyen bir dosya sistemi İzleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="d46fd-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="d46fd-126">Örneğin, aşağıdaki komutu otomatik olarak geçerli proje oluşturur ve bir dosyada her değiştiğinde ayrıntılı çıktıyı üretir:</span><span class="sxs-lookup"><span data-stu-id="d46fd-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```console
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="d46fd-127">Not `--` önündeki seçeneği `--verbose` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="d46fd-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="d46fd-128">Doğrudan geçirilen seçenekleri sınırlandırır `dotnet watch` alt öğesine geçirilen bağımsız değişkenler komutunu `dotnet` işlem.</span><span class="sxs-lookup"><span data-stu-id="d46fd-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="d46fd-129">Bu olmadan, `--verbose` seçeneği uygulandığı `dotnet watch` komutu, `dotnet build` komutu.</span><span class="sxs-lookup"><span data-stu-id="d46fd-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="d46fd-130">Daha fazla bilgi için [dotnet izleme kullanarak ASP.NET Core geliştirme uygulamaları](/aspnet/core/tutorials/dotnet-watch)</span><span class="sxs-lookup"><span data-stu-id="d46fd-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span></span>

- <span data-ttu-id="d46fd-131">`dotnet dev-certs` oluşturur ve ASP.NET Core uygulamaları geliştirme sırasında kullanılan sertifikalar yönetir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="d46fd-132">`dotnet user-secrets` ASP.NET Core uygulamalarında kullanıcı bir gizli dizi deposu gizli yönetir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="d46fd-133">`dotnet sql-cache` Dağıtılmış önbelleğe alma işlemi için kullanılacak bir Microsoft SQL Server veritabanındaki bir tablo ve dizin oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d46fd-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="d46fd-134">`dotnet ef` veritabanlarını yönetmek için bir araçtır <xref:Microsoft.EntityFrameworkCore.DbContext> nesneleri ve Entity Framework Core uygulamalarında geçişler.</span><span class="sxs-lookup"><span data-stu-id="d46fd-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="d46fd-135">Daha fazla bilgi için [EF Core .NET komut satırı araçları](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="d46fd-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="d46fd-136">Genel araçları</span><span class="sxs-lookup"><span data-stu-id="d46fd-136">Global Tools</span></span>

<span data-ttu-id="d46fd-137">.NET core 2.1 destekler *genel Araçları* --genel olarak komut satırından kullanılabilen diğer bir deyişle, özel araçlar.</span><span class="sxs-lookup"><span data-stu-id="d46fd-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="d46fd-138">Genişletilebilirlik modeli '.NET Core önceki sürümlerinde özel araçlarla proje bazında yalnızca kullanarak sunulan [ `DotnetCliToolReference` ](../tools/extensibility.md#consuming-per-project-tools).</span><span class="sxs-lookup"><span data-stu-id="d46fd-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="d46fd-139">Genel bir aracı yüklemek için kullandığınız [dotnet aracı yükleme](../tools/dotnet-tool-install.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="d46fd-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="d46fd-140">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d46fd-140">For example:</span></span>

```console
dotnet tool install -g dotnetsay
```

<span data-ttu-id="d46fd-141">Yüklendikten sonra aracı komut satırından aracı adı belirtilerek çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="d46fd-142">Daha fazla bilgi için [.NET Core Araçları Genel genel bakış](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="d46fd-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="d46fd-143">Aracı ile Yönetim `dotnet tool` komutu</span><span class="sxs-lookup"><span data-stu-id="d46fd-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="d46fd-144">.NET Core 2.1 SDK tüm araçları işlemler kullanın `dotnet tool` komutu.</span><span class="sxs-lookup"><span data-stu-id="d46fd-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="d46fd-145">Aşağıdaki seçenekler mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="d46fd-145">The following options are available:</span></span>

- <span data-ttu-id="d46fd-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) bir aracı yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="d46fd-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="d46fd-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) etkili bir şekilde güncelleştiren bir aracı kaldırıp için.</span><span class="sxs-lookup"><span data-stu-id="d46fd-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="d46fd-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) şu anda listelemek için araçları yüklü.</span><span class="sxs-lookup"><span data-stu-id="d46fd-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="d46fd-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) şu anda yüklü araçları kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="d46fd-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="d46fd-150">İleri Sarma</span><span class="sxs-lookup"><span data-stu-id="d46fd-150">Roll forward</span></span>

<span data-ttu-id="d46fd-151">.NET Core 2.0 ile otomatik olarak itibaren tüm .NET Core uygulamaları en son İleri sarmanın *podverze* bir sisteme yüklenmiş.</span><span class="sxs-lookup"><span data-stu-id="d46fd-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="d46fd-152">Bir uygulamanın derlendiği .NET Core sürümü çalışma zamanında mevcut değilse, .NET Core 2.0 ile başlayarak, uygulama otomatik olarak en son yüklenen karşı çalışır *podverze* .NET core'un.</span><span class="sxs-lookup"><span data-stu-id="d46fd-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="d46fd-153">Diğer bir deyişle, .NET Core 2.0 ile bir uygulama oluşturulur ve .NET Core 2.1 .NET Core 2.0, ana sistemde mevcut değil. ancak, uygulama .NET Core 2.1 ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="d46fd-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d46fd-154">Bu sarma davranışı Önizleme sürümleri için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="d46fd-155">Varsayılan olarak, ana sürümler için de geçerli değildir, ancak bu ayarlarla değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="d46fd-156">Hiçbir aday paylaşılan Framework sarma ayarını değiştirerek bu davranışı değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d46fd-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="d46fd-157">Kullanılabilir ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d46fd-157">The available settings are:</span></span>
- <span data-ttu-id="d46fd-158">`0` -ikincil sürüm sarma davranışı devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="d46fd-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="d46fd-159">Bu ayar, .NET Core 2.0.0 için oluşturulmuş bir uygulamada İleri .NET Core 2.0.1, ancak .NET Core 2.2.0 veya .NET Core 3.0.0 dökümünü yapar.</span><span class="sxs-lookup"><span data-stu-id="d46fd-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="d46fd-160">`1` -ikincil sürüm sarma davranışı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d46fd-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="d46fd-161">Bu ayar için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-161">This is the default value for the setting.</span></span> <span data-ttu-id="d46fd-162">Bu ayar, .NET Core 2.0.0 için oluşturulmuş bir uygulamada ileriye ya da .NET Core için 2.0.1 veya .NET Core hangisini seçtiğinize bağlı olarak yüklü, ancak bunu İleri 3.0.0 .NET Core için döküm değil 2.2.0 dökümünü yapar.</span><span class="sxs-lookup"><span data-stu-id="d46fd-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="d46fd-163">`2` -küçük ve büyük sürüm sarma davranışı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="d46fd-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="d46fd-164">.NET Core 2.0.0 için oluşturulmuş bir uygulama için .NET Core 3.0.0 İleri sarmanın şekilde ayarlanmışsa, hatta farklı ana sürümleri kabul edilir</span><span class="sxs-lookup"><span data-stu-id="d46fd-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="d46fd-165">Bu ayarı üç yoldan herhangi birini değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d46fd-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="d46fd-166">Ayarlama `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` ortam değişkeni istenen değeri.</span><span class="sxs-lookup"><span data-stu-id="d46fd-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="d46fd-167">İstenen değeri içeren aşağıdaki satırı ekleyin `runtimeconfig.json` dosyası:</span><span class="sxs-lookup"><span data-stu-id="d46fd-167">Add the following line with the desired value to the `runtimeconfig.json` file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="d46fd-168">Kullanırken [.NET Core CLI Araçları](../tools/index.md), istenen değeri aşağıdaki seçenek gibi .NET Core komut ekleme `run`:</span><span class="sxs-lookup"><span data-stu-id="d46fd-168">When using [.NET Core CLI tools](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```console
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="d46fd-169">Düzeltme eki sürümü alma İleri bu ayarı bağımsızdır ve tüm olası ikincil sonra Bitti veya ana sürüm ileri sarma uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d46fd-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="d46fd-170">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="d46fd-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="d46fd-171">Kendi içinde Uygulama Bakımı</span><span class="sxs-lookup"><span data-stu-id="d46fd-171">Self-contained application servicing</span></span>

<span data-ttu-id="d46fd-172">`dotnet publish` artık kendi başına bir hizmet verilen çalışma zamanı sürümü uygulamalarla yayımlar.</span><span class="sxs-lookup"><span data-stu-id="d46fd-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="d46fd-173">.NET Core 2.1 SDK'sı (v 2.1.300) kendi içinde bir uygulama yayımladığınızda, uygulamanız bu SDK'sı tarafından bilinen en son hizmet verilen çalışma zamanı sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="d46fd-174">En son SDK'yı yükselttiğinizde, en son .NET Core çalışma zamanı sürümüyle yayımlama.</span><span class="sxs-lookup"><span data-stu-id="d46fd-174">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="d46fd-175">Bu .NET Core 1.0 çalışma zamanları ve sonrası için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="d46fd-176">Çalışma zamanı sürümleri nuget.org müstakil yayımlama kullanır. Hizmet verilen çalışma zamanı, makinenizdeki gerekmez.</span><span class="sxs-lookup"><span data-stu-id="d46fd-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="d46fd-177">Farklı bir sürümü aracılığıyla belirtilmediği sürece .NET Core 2.0 SDK'sını kullanarak kendi içindeki uygulamaları .NET Core 2.0.0 çalışma zamanı ile yayımlanan `RuntimeFrameworkVersion` özelliği.</span><span class="sxs-lookup"><span data-stu-id="d46fd-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="d46fd-178">Bu yeni davranış artık kendi içinde bir uygulama için daha yüksek bir çalışma zamanı sürümünü seçmek için bu özelliği ayarlayın gerekir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-178">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="d46fd-179">İleriye dönük en kolay yaklaşım .NET Core 2.1 SDK (v 2.1.300) her zaman yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="d46fd-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="d46fd-180">Daha fazla bilgi için [müstakil dağıtım çalışma zamanı, ileri sarma](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="d46fd-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="d46fd-181">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="d46fd-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="d46fd-182">.NET Framework mevcut koddan .NET Core için bağlantı noktası, kullanabileceğiniz [Windows Uyumluluk Paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="d46fd-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="d46fd-183">' De .NET Core bulunandan daha fazla API 20.000 erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d46fd-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="d46fd-184">Bu API'ler türler <xref:System.Drawing?displayProperty=nameWithType> ad alanı, <xref:System.Diagnostics.EventLog> sınıf, WMI, performans sayaçları, Windows Hizmetleri ve Windows kayıt defteri türleri ve üyeleri.</span><span class="sxs-lookup"><span data-stu-id="d46fd-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="d46fd-185">JIT Derleyici iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d46fd-185">JIT compiler improvements</span></span>

<span data-ttu-id="d46fd-186">.NET core içerir adlı yeni bir JIT derleyicisi teknoloji *katmanlı derleme* (olarak da bilinen *Uyarlamalı iyileştirme*), önemli ölçüde performansı geliştirebilir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="d46fd-187">Katmanlı derleme, bir katılım ayarıdır.</span><span class="sxs-lookup"><span data-stu-id="d46fd-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="d46fd-188">JIT derleyicisi tarafından gerçekleştirilen önemli görevlerinden birini ve kod yürütme en iyi duruma getiriyor.</span><span class="sxs-lookup"><span data-stu-id="d46fd-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="d46fd-189">Az kullanılan kodu yolları için ancak derleyici iyileştirilmemiş kod çalıştırma, çalışma zamanı geçirdiği daha kodu en iyi duruma getirme daha fazla zaman harcayabilir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="d46fd-190">Katmanlı bir derleme JIT derlemesi iki aşamada sunar:</span><span class="sxs-lookup"><span data-stu-id="d46fd-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="d46fd-191">A **ilk katman**, mümkün olan en kısa sürede kod oluşturduğu.</span><span class="sxs-lookup"><span data-stu-id="d46fd-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="d46fd-192">A **ikinci katman**, oluşturduğu kodu sık yürütülen bu yöntemleri için en iyi duruma getirilmiş.</span><span class="sxs-lookup"><span data-stu-id="d46fd-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="d46fd-193">Derleme, ikinci katman, Gelişmiş performans için paralel gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="d46fd-194">İki yöntemden biriyle katmanlı derleme kabul edebileceğiniz.</span><span class="sxs-lookup"><span data-stu-id="d46fd-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="d46fd-195">.NET Core 2.1 SDK'sını kullanan tüm projelerde katmanlı derleme kullanmak için aşağıdaki ortam değişkenlerini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="d46fd-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="d46fd-196">Katmanlı derleme proje başına temelinde kullanılacak ekleme `<TieredCompilation>` özelliğini `<PropertyGroup>` MSBuild proje dosyası, aşağıdaki örnekte gösterildiği gibi bir bölümünü:</span><span class="sxs-lookup"><span data-stu-id="d46fd-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="d46fd-197">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="d46fd-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="d46fd-198">`Span<T>` ve `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="d46fd-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="d46fd-199">.NET core 2.1 dizileri ile çalışmayı kolaylaştıran bazı yeni türlerini ve çok daha verimli bellek diğer türleri içerir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="d46fd-200">Yeni türleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d46fd-200">The new types include:</span></span>

- <span data-ttu-id="d46fd-201"><xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d46fd-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="d46fd-202"><xref:System.Memory%601?displayProperty=nameWithType> ve <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d46fd-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d46fd-203">Bu tür öğeleri dizi değerinin bir bölümü veya bir bölümünü bellek arabelleği olarak geçirirken bu türleri, bir yönteme iletmeden önce bölümü verilerin bir kopyasını yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="d46fd-204">Bu türler ek bellek ayırma ve kopyalama işlemleri ihtiyacını ortadan kaldırır, verilerin sanal bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="d46fd-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="d46fd-205">Aşağıdaki örnekte bir <xref:System.Span%601> ve <xref:System.Memory%601> dizi 10 öğelerini sanal bir görünümünü sağlamak için örneği.</span><span class="sxs-lookup"><span data-stu-id="d46fd-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!CODE-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

[!CODE-vb[Memory\<T>](~/samples/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="d46fd-206">Brotli sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="d46fd-206">Brotli compression</span></span>

<span data-ttu-id="d46fd-207">.NET core 2.1 Brotli sıkıştırma ve açma desteğini ekler.</span><span class="sxs-lookup"><span data-stu-id="d46fd-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="d46fd-208">Brotli tanımlanan bir genel amaçlı kayıpsız sıkıştırma algoritması olan [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) ve web tarayıcıları ve ana web sunucuları tarafından desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="d46fd-209">Akış tabanlı kullanabileceğiniz <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> sınıfı veya yüksek performanslı aralık tabanlı <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> ve <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="d46fd-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="d46fd-210">Sıkıştırmasıyla aşağıdaki örnekte <xref:System.IO.Compression.BrotliStream> sınıfı:</span><span class="sxs-lookup"><span data-stu-id="d46fd-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!CODE-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

<span data-ttu-id="d46fd-211"><xref:System.IO.Compression.BrotliStream> Davranışı aynıdır <xref:System.IO.Compression.DeflateStream> ve <xref:System.IO.Compression.GZipStream>, kolaylaştıran için bu API'leri çağıran koda dönüştürme <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="d46fd-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="d46fd-212">Yeni şifreleme API'leri ve şifreleme geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d46fd-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="d46fd-213">.NET core 2.1 şifreleme API'leri için çeşitli iyileştirmeler içerir:</span><span class="sxs-lookup"><span data-stu-id="d46fd-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="d46fd-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> System.Security.Cryptography.Pkcs pakette kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="d46fd-215">Uygulama ile aynı olduğu <xref:System.Security.Cryptography.Pkcs.SignedCms> .NET Framework sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d46fd-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="d46fd-216">Yeni aşırı yüklemeleri <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> yöntemleri dışında SHA-1 algoritmaları kullanarak sertifika parmak izi değerleri almak çağıranlar etkinleştirmek için bir karma algoritması tanımlayıcı kabul edin.</span><span class="sxs-lookup"><span data-stu-id="d46fd-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="d46fd-217">Yeni <xref:System.Span%601>-karma işlevi için HMAC, şifreleme rastgele sayı oluşturma, asimetrik imza oluşturma, asimetrik imza işleme ve RSA şifreleme tabanlı şifreleme API'leri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="d46fd-218">Performansını <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> yaklaşık 15 oranında kullanılarak geliştirilmiş bir <xref:System.Span%601>-uygulama tabanlı.</span><span class="sxs-lookup"><span data-stu-id="d46fd-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="d46fd-219">Yeni <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> sınıfı iki yeni yöntemler içerir:</span><span class="sxs-lookup"><span data-stu-id="d46fd-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="d46fd-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> Bu kullanım için uygun yan kanal bilgileri zamanlama için katkıda bulunan önlemek için şifreleme doğrulama yapar aynı uzunlukta iki tüm girişleri için döndürülecek sabit bir süre sürer.</span><span class="sxs-lookup"><span data-stu-id="d46fd-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="d46fd-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> hale getirilemeyen bir bellek temizleme yordamdır.</span><span class="sxs-lookup"><span data-stu-id="d46fd-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="d46fd-222">Statik <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> yöntemi dolduran bir <xref:System.Span%601> rasgele değerlere sahip.</span><span class="sxs-lookup"><span data-stu-id="d46fd-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="d46fd-223"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Linux ve maxOS artık desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="d46fd-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and maxOS.</span></span>

- <span data-ttu-id="d46fd-224">Eliptik Eğri Diffie-Hellman (ECDH) içinde kullanıma sunuldu <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> sınıf ailesi.</span><span class="sxs-lookup"><span data-stu-id="d46fd-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="d46fd-225">Yüzey alanı .NET Framework olduğu gibi aynıdır.</span><span class="sxs-lookup"><span data-stu-id="d46fd-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="d46fd-226">Tarafından döndürülen örneği <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> şifrelemek veya şifresini bir SHA-2 özet kullanarak OAEP ile hem de oluşturabilir veya kullanılarak RSA-PSS imza doğrulama.</span><span class="sxs-lookup"><span data-stu-id="d46fd-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="d46fd-227">Yuva geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d46fd-227">Sockets improvements</span></span>

<span data-ttu-id="d46fd-228">.NET core içeren yeni bir tür <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>ve bir yeniden <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, üst düzey ağ API'leri temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d46fd-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="d46fd-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, örneğin, temelidir <xref:System.Net.Http.HttpClient> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="d46fd-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="d46fd-230">.NET Core önceki sürümlerinde, yerel ağ uygulamalarında üst düzey API'ler temel alınmıştır.</span><span class="sxs-lookup"><span data-stu-id="d46fd-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="d46fd-231">.NET Core 2.1 içinde tanıtılan bir yuva uygulaması, çok sayıda avantaj vardır:</span><span class="sxs-lookup"><span data-stu-id="d46fd-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="d46fd-232">Önceki bir uygulama ile karşılaştırıldığında önemli bir performans geliştirmesi.</span><span class="sxs-lookup"><span data-stu-id="d46fd-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="d46fd-233">Dağıtımı ve bakımı kolaylaştıran eleme, platform bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="d46fd-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="d46fd-234">Tüm .NET Core platformlar genelinde tutarlı davranışı.</span><span class="sxs-lookup"><span data-stu-id="d46fd-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="d46fd-235"><xref:System.Net.Http.SocketsHttpHandler> .NET Core 2.1 içinde varsayılan uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="d46fd-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="d46fd-236">Ancak, eski kullanmak için uygulamanızı yapılandırabileceğiniz <xref:System.Net.Http.HttpClientHandler> çağırarak sınıfı <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemi:</span><span class="sxs-lookup"><span data-stu-id="d46fd-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="d46fd-237">Bir ortam kullanabilirsiniz kullanarak dışında kabul etmek için değişken yuva göre uygulamaları <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="d46fd-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="d46fd-238">Bunu yapmak için ayarlanmış `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` ya da `false` veya 0.</span><span class="sxs-lookup"><span data-stu-id="d46fd-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="d46fd-239">Windows üzerinde de kullanmayı seçebilirsiniz <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, yerel bir uygulama üzerinde kullanır veya <xref:System.Net.Http.SocketsHttpHandler> sınıfı örneğini geçirerek sınıf <xref:System.Net.Http.HttpClient> Oluşturucusu.</span><span class="sxs-lookup"><span data-stu-id="d46fd-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="d46fd-240">Linux ve Macos'ta, yalnızca yapılandırabilirsiniz <xref:System.Net.Http.HttpClient> işlem başına temelinde.</span><span class="sxs-lookup"><span data-stu-id="d46fd-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="d46fd-241">Linux üzerinde dağıtmanız gerekir. [libcurl](https://curl.haxx.se/libcurl/) eski kullanmak istiyorsanız <xref:System.Net.Http.HttpClient> uygulaması.</span><span class="sxs-lookup"><span data-stu-id="d46fd-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="d46fd-242">(.NET Core 2.0 ile yüklenir.)</span><span class="sxs-lookup"><span data-stu-id="d46fd-242">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="d46fd-243">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d46fd-243">See also</span></span>

- [<span data-ttu-id="d46fd-244">​.NET Core'daki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="d46fd-244">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="d46fd-245">EF Core 2.1 yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="d46fd-245">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="d46fd-246">ASP.NET Core 2.1 yenilikler nelerdir?</span><span class="sxs-lookup"><span data-stu-id="d46fd-246">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
