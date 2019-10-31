---
title: ​.NET Core 2.1’deki yenilikler
description: .NET Core 2,1 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 603e7ae4ffb9e6a4bb477af9597d6948bd63f55e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100743"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="3bea5-103">​.NET Core 2.1’deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="3bea5-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="3bea5-104">.NET Core 2,1, aşağıdaki alanlarda geliştirmeler ve yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="3bea5-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="3bea5-105">Araçları</span><span class="sxs-lookup"><span data-stu-id="3bea5-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="3bea5-106">İleri al</span><span class="sxs-lookup"><span data-stu-id="3bea5-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="3bea5-107">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="3bea5-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="3bea5-108">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="3bea5-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="3bea5-109">JıT derleme geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="3bea5-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="3bea5-110">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="3bea5-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="3bea5-111">Araçlar</span><span class="sxs-lookup"><span data-stu-id="3bea5-111">Tooling</span></span>

<span data-ttu-id="3bea5-112">.NET Core 2,1 ' de yer alan araç, .NET Core 2,1 SDK (v 2.1.300), aşağıdaki değişiklikleri ve geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="3bea5-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="3bea5-113">Derleme performansı iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="3bea5-113">Build performance improvements</span></span>

<span data-ttu-id="3bea5-114">.NET Core 2,1 ' nin önemli bir odağında, özellikle Artımlı derlemeler için derleme zamanı performansı geliştiriyoruz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="3bea5-115">Bu performans geliştirmeleri, `dotnet build` ve Visual Studio 'da derlemeler kullanılarak her iki komut satırı derlemesi için de geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="3bea5-116">İyileşme özgü bazı alanlarda şunlar vardır:</span><span class="sxs-lookup"><span data-stu-id="3bea5-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="3bea5-117">Paket varlık çözümlemesi için, yalnızca tüm varlıklar yerine bir derleme tarafından kullanılan varlıkları çözümleme.</span><span class="sxs-lookup"><span data-stu-id="3bea5-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="3bea5-118">Derleme başvurularını önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="3bea5-118">Caching of assembly references.</span></span>

- <span data-ttu-id="3bea5-119">Tek başına `dotnet build` çağırmaları arasında yayılan süreçler olan uzun süre çalışan SDK yapı sunucularının kullanımı.</span><span class="sxs-lookup"><span data-stu-id="3bea5-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="3bea5-120">Her `dotnet build` çalıştırıldığında büyük kod bloklarını JıT ile derleme ihtiyacını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="3bea5-121">Yapı sunucusu işlemi aşağıdaki komutla otomatik olarak sonlandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="3bea5-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="3bea5-122">Yeni CLı komutları</span><span class="sxs-lookup"><span data-stu-id="3bea5-122">New CLI commands</span></span>

<span data-ttu-id="3bea5-123">Yalnızca .NET Core SDK bir parçası olarak [`DotnetCliToolReference`](../tools/extensibility.md) kullanılarak proje başına kullanılabilen birçok araç vardır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="3bea5-124">Bu araçlar şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="3bea5-124">These tools include:</span></span>

- <span data-ttu-id="3bea5-125">`dotnet watch`, belirli bir komut kümesini yürütmeden önce bir dosyanın değiştirilmesini bekleyen bir dosya sistem izleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3bea5-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="3bea5-126">Örneğin, aşağıdaki komut, geçerli projeyi otomatik olarak yeniden oluşturur ve her bir dosya değiştiğinde ayrıntılı çıkış üretir:</span><span class="sxs-lookup"><span data-stu-id="3bea5-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="3bea5-127">`--verbose` seçeneğinden önce gelen `--` seçeneğine göz önüne alın.</span><span class="sxs-lookup"><span data-stu-id="3bea5-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="3bea5-128">Alt `dotnet` işlemine geçirilen bağımsız değişkenlerden `dotnet watch` komutuna doğrudan geçirilen seçenekleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="3bea5-129">Bu olmadan, `--verbose` seçeneği `dotnet build` komutuna değil `dotnet watch` komutu için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="3bea5-130">Daha fazla bilgi için bkz. [DotNet Watch kullanarak ASP.NET Core uygulamalar geliştirme](/aspnet/core/tutorials/dotnet-watch).</span><span class="sxs-lookup"><span data-stu-id="3bea5-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch).</span></span>

- <span data-ttu-id="3bea5-131">`dotnet dev-certs` ASP.NET Core uygulamalarda geliştirme sırasında kullanılan sertifikaları oluşturur ve yönetir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="3bea5-132">`dotnet user-secrets`, ASP.NET Core uygulamalarda Kullanıcı gizli deposundaki gizli dizileri yönetir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="3bea5-133">`dotnet sql-cache`, dağıtılmış önbellek için kullanılacak bir Microsoft SQL Server veritabanında tablo ve dizinler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3bea5-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="3bea5-134">`dotnet ef`, Entity Framework Core uygulamalardaki veritabanlarını, <xref:Microsoft.EntityFrameworkCore.DbContext> nesneleri ve geçişleri yönetmeye yönelik bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="3bea5-135">Daha fazla bilgi için bkz. [.NET komut satırı araçlarını EF Core](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="3bea5-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="3bea5-136">Genel Araçlar</span><span class="sxs-lookup"><span data-stu-id="3bea5-136">Global Tools</span></span>

<span data-ttu-id="3bea5-137">.NET Core 2,1, *genel araçları* destekler-diğer bir deyişle, komut satırından küresel olarak kullanılabilir özel araçlar.</span><span class="sxs-lookup"><span data-stu-id="3bea5-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="3bea5-138">.NET Core 'un önceki sürümlerindeki genişletilebilirlik modeli, yalnızca [`DotnetCliToolReference` ' i](../tools/extensibility.md#consuming-per-project-tools)kullanarak her proje için kullanılabilir özel araçları kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="3bea5-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="3bea5-139">Küresel bir araç yüklemek için [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="3bea5-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="3bea5-140">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="3bea5-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="3bea5-141">Yüklendikten sonra araç, araç adı belirtilerek komut satırından çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="3bea5-142">Daha fazla bilgi için bkz. [.NET Core genel araçlarına genel bakış](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="3bea5-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="3bea5-143">`dotnet tool` komutuyla araç yönetimi</span><span class="sxs-lookup"><span data-stu-id="3bea5-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="3bea5-144">.NET Core 2,1 SDK 'da tüm araçlar işlemleri `dotnet tool` komutunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="3bea5-145">Aşağıdaki seçenekler mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="3bea5-145">The following options are available:</span></span>

- <span data-ttu-id="3bea5-146">bir araç yüklemek için [`dotnet tool install`](../tools/dotnet-tool-install.md) .</span><span class="sxs-lookup"><span data-stu-id="3bea5-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="3bea5-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) ' i kaldırmak ve yeniden yüklemek için, etkin bir şekilde güncelleştiren bir araç.</span><span class="sxs-lookup"><span data-stu-id="3bea5-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="3bea5-148">Şu anda yüklü olan araçları listelemek için [`dotnet tool list`](../tools/dotnet-tool-list.md) .</span><span class="sxs-lookup"><span data-stu-id="3bea5-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="3bea5-149">yüklü olan araçları kaldırmak için [`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) .</span><span class="sxs-lookup"><span data-stu-id="3bea5-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="3bea5-150">İleri al</span><span class="sxs-lookup"><span data-stu-id="3bea5-150">Roll forward</span></span>

<span data-ttu-id="3bea5-151">.NET Core 2,0 ile başlayan tüm .NET Core Uygulamaları, bir sistemde yüklü en son alt *sürüme* otomatik olarak ileri doğru iletir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="3bea5-152">.NET Core 2,0 ile başlayarak, bir uygulamanın derlenme .NET Core sürümü çalışma zamanında mevcut değilse, uygulama otomatik olarak .NET Core 'un en son yüklenen alt *sürümünde* çalışır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="3bea5-153">Diğer bir deyişle, bir uygulama .NET Core 2,0 ile derlen, ancak .NET Core 2,0 de ana bilgisayar sisteminde yoksa ancak .NET Core 2,1 ise, uygulama .NET Core 2,1 ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3bea5-154">Bu geri alma davranışı önizleme sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="3bea5-155">Varsayılan olarak, ana yayınlar için de uygulanmaz, ancak bu, aşağıdaki ayarlarla değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="3bea5-156">Bu davranışı, aday paylaşılan çerçeve olmadan geri alma ayarını değiştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="3bea5-157">Kullanılabilir ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3bea5-157">The available settings are:</span></span>

- <span data-ttu-id="3bea5-158">`0`-ikincil sürüm alma-iletme davranışını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="3bea5-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="3bea5-159">Bu ayarla, .NET Core 2.0.0 için oluşturulmuş bir uygulama .NET Core 2.0.1 'e, ancak .NET Core 2.2.0 veya .NET Core 3.0.0 'e geri alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="3bea5-160">`1`-ikincil sürüm alma-iletme davranışını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3bea5-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="3bea5-161">Bu ayar için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-161">This is the default value for the setting.</span></span> <span data-ttu-id="3bea5-162">Bu ayarla, .NET Core 2.0.0 için oluşturulmuş bir uygulama, ne olduğuna bağlı olarak .NET Core 2.0.1 veya .NET Core 2.2.0 'e doğru bir şekilde gönderilir, ancak .NET Core 3.0.0 'e geri almaz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="3bea5-163">`2`-küçük ve ana sürüm alma-iletme davranışını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3bea5-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="3bea5-164">Ayarlanırsa, farklı ana sürümler de dikkate alınır, bu nedenle .NET Core 2.0.0 için derlenmiş bir uygulama .NET Core 3.0.0 'e geri alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="3bea5-165">Bu ayarı, üç şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3bea5-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="3bea5-166">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` ortam değişkenini istenen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3bea5-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="3bea5-167">Aşağıdaki satırı, istenen değeri *. runtimeconfig. JSON* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3bea5-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="3bea5-168">[.NET Core CLI araçlarını](../tools/index.md)kullanırken, istenen değeri `run` gibi bir .NET Core komutuna ekleyerek aşağıdaki seçeneği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3bea5-168">When using [.NET Core CLI tools](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="3bea5-169">Düzeltme Eki Sürümü ileri, bu ayardan bağımsızdır ve herhangi bir olası küçük veya büyük sürüm ileri doğru uygulandıktan sonra yapılır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="3bea5-170">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="3bea5-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="3bea5-171">Kendi içinde uygulama Bakımı</span><span class="sxs-lookup"><span data-stu-id="3bea5-171">Self-contained application servicing</span></span>

<span data-ttu-id="3bea5-172">`dotnet publish` artık hizmet verilen çalışma zamanı sürümü ile bağımsız uygulamalar yayımlar.</span><span class="sxs-lookup"><span data-stu-id="3bea5-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="3bea5-173">Bir bağımsız uygulamayı .NET Core 2,1 SDK (v 2.1.300) ile yayımladığınızda, uygulamanız ilgili SDK tarafından bilinen en son hizmet verilen çalışma zamanı sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="3bea5-174">En son SDK 'ya yükselttiğinizde, en son .NET Core çalışma zamanı sürümü ile yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-174">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="3bea5-175">Bu, .NET Core 1,0 çalışma zamanları ve üzeri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="3bea5-176">Kendi içinde yayımlama, NuGet.org üzerinde çalışma zamanı sürümlerini kullanır. Makinenizde bakım çalışma zamanına sahip olmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="3bea5-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="3bea5-177">.NET Core 2,0 SDK 'sını kullanarak, `RuntimeFrameworkVersion` özelliği aracılığıyla farklı bir sürüm belirtilmediği takdirde, kendi içinde bulunan uygulamalar .NET Core 2.0.0 çalışma zamanına yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="3bea5-178">Bu yeni davranışla birlikte, bu özelliği, otomatik olarak kapsanan bir uygulama için daha yüksek bir çalışma zamanı sürümü seçmek üzere ayarlamanıza gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-178">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="3bea5-179">En kolay yaklaşım .NET Core 2,1 SDK (v 2.1.300) ile her zaman yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="3bea5-180">Daha fazla bilgi için bkz. [kendi kendine içerilen dağıtım çalışma zamanı ileri](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="3bea5-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="3bea5-181">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="3bea5-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="3bea5-182">.NET Framework mevcut koddan .NET Core 'a bağlantı oluşturduğunuzda [Windows Uyumluluk Paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)' ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="3bea5-183">.NET Core 'da bulunandan daha fazla 20.000 API erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="3bea5-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="3bea5-184">Bu API 'Ler <xref:System.Drawing?displayProperty=nameWithType> ad alanı, <xref:System.Diagnostics.EventLog> sınıfı, WMI, performans sayaçları, Windows Hizmetleri ve Windows kayıt defteri türleri ve üyeleri türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="3bea5-185">JıT derleyicisi geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="3bea5-185">JIT compiler improvements</span></span>

<span data-ttu-id="3bea5-186">.NET Core, performansı önemli ölçüde iyileştirebilen *katmanlı derleme* ( *Uyarlamalı iyileştirme*olarak da bilinir) adlı yeni bir JIT Derleyici teknolojisini içerir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="3bea5-187">Katmanlı derleme, bir katılım ayarıdır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="3bea5-188">JıT derleyicisi tarafından gerçekleştirilen önemli görevlerden biri, kod yürütmeyi iyileştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="3bea5-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="3bea5-189">Ancak, daha az kullanılan kod yolları için, derleyici en iyi duruma getirilmiş kodu çalıştırmaya kıyasla kodu en iyi duruma getirmek için daha fazla zaman harcayabilir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="3bea5-190">Katmanlı derleme JıT derlemesinde iki aşama sunar:</span><span class="sxs-lookup"><span data-stu-id="3bea5-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="3bea5-191">Mümkün olduğunca hızlı bir şekilde kod üreten **ilk katman**.</span><span class="sxs-lookup"><span data-stu-id="3bea5-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="3bea5-192">Sık çalıştırılan yöntemler için iyileştirilmiş kod üreten **ikinci bir katman**.</span><span class="sxs-lookup"><span data-stu-id="3bea5-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="3bea5-193">İkinci derleme katmanı, gelişmiş performans için paralel olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="3bea5-194">Katmanlı derlemeyi iki şekilde seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="3bea5-195">Katmanlı derlemeyi .NET Core 2,1 SDK kullanan tüm projelerde kullanmak için aşağıdaki ortam değişkenini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="3bea5-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="3bea5-196">Katmanlı derlemeyi proje başına temelinde kullanmak için, aşağıdaki örnekte gösterildiği gibi, `<TieredCompilation>` özelliğini MSBuild proje dosyasının `<PropertyGroup>` bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="3bea5-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="3bea5-197">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="3bea5-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="3bea5-198">`Span<T>` ve `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="3bea5-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="3bea5-199">.NET Core 2,1, diziler ve diğer bellek türleriyle çalışmayı çok daha verimli hale getirmek için bazı yeni türler içerir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="3bea5-200">Yeni türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="3bea5-200">The new types include:</span></span>

- <span data-ttu-id="3bea5-201"><xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3bea5-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="3bea5-202"><xref:System.Memory%601?displayProperty=nameWithType> ve <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3bea5-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="3bea5-203">Bu türler olmadan, bu tür öğeleri bir dizinin bir bölümü veya bir bellek arabelleğinin bir bölümü olarak geçirirken, bir yönteme geçirmeden önce verilerin bir kısmının kopyasını oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="3bea5-204">Bu türler, ek bellek ayırma ve kopyalama işlemlerine gereksinimi ortadan kaldıran bu verilerin sanal bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="3bea5-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="3bea5-205">Aşağıdaki örnek, bir dizi 10 öğenin sanal görünümünü sağlamak için bir <xref:System.Span%601> ve <xref:System.Memory%601> örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

[!code-vb[Memory\<T>](~/samples/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="3bea5-206">Brotli sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="3bea5-206">Brotli compression</span></span>

<span data-ttu-id="3bea5-207">.NET Core 2,1, Brotli sıkıştırma ve açma için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="3bea5-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="3bea5-208">Brotli, [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) ' de tanımlanan ve çoğu Web tarayıcısı ve ana Web sunucusu tarafından desteklenen genel amaçlı kayıpsız bir sıkıştırma algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="3bea5-209">Stream tabanlı <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> sınıfını veya yüksek performanslı span tabanlı <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> ve <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> sınıflarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="3bea5-210">Aşağıdaki örnek <xref:System.IO.Compression.BrotliStream> sınıfıyla sıkıştırmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="3bea5-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

<span data-ttu-id="3bea5-211"><xref:System.IO.Compression.BrotliStream> davranış <xref:System.IO.Compression.DeflateStream> ve <xref:System.IO.Compression.GZipStream>aynıdır, bu da bu API 'Leri çağıran kodun <xref:System.IO.Compression.BrotliStream>dönüştürülmesini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="3bea5-212">Yeni şifreleme API 'Leri ve şifreleme geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="3bea5-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="3bea5-213">.NET Core 2,1, şifreleme API 'Lerinde çok sayıda geliştirme içerir:</span><span class="sxs-lookup"><span data-stu-id="3bea5-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="3bea5-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>, System. Security. Cryptography. Pkcs paketinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="3bea5-215">Uygulama, .NET Framework <xref:System.Security.Cryptography.Pkcs.SignedCms> sınıfıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="3bea5-216"><xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> ve <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> yöntemlerinin yeni aşırı yüklemeleri, çağıranların SHA-1 dışındaki algoritmaları kullanarak sertifika parmak izi değerlerini almasını sağlamak için bir karma algoritma tanımlayıcısı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="3bea5-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="3bea5-217">Yeni <xref:System.Span%601>tabanlı şifreleme API 'Leri, karma, HMAC, şifreleme rastgele sayı oluşturma, asimetrik imza oluşturma, asimetrik imza işleme ve RSA şifrelemesi için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="3bea5-218"><xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> performansı <xref:System.Span%601>tabanlı bir uygulama kullanılarak yaklaşık %15 oranında geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="3bea5-219">Yeni <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> sınıfı iki yeni yöntem içerir:</span><span class="sxs-lookup"><span data-stu-id="3bea5-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="3bea5-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>, aynı uzunlukta olan iki giriş için geri dönüş için sabit bir süre sürer. Bu, zamanlama tarafı kanal bilgilerine katkıda bulunmaktan kaçınmak için şifreleme doğrulamasında kullanılması uygun hale getirir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="3bea5-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>, iyileştirelemeyen bir bellek temizleme yordamdır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="3bea5-222">Statik <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> yöntemi rastgele değerlerle bir <xref:System.Span%601> doldurur.</span><span class="sxs-lookup"><span data-stu-id="3bea5-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="3bea5-223"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> artık Linux ve macOS 'ta desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and macOS.</span></span>

- <span data-ttu-id="3bea5-224">Eliptik Eğri Diffie-Hellman (ECDH) artık <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> sınıf ailesinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="3bea5-225">Yüzey alanı .NET Framework ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="3bea5-226"><xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> tarafından döndürülen örnek, bir SHA-2 Özeti kullanarak OAEP ile şifreleyebilir veya şifresini çözebilir, ayrıca RSA-PSS kullanarak imzaları oluşturabilir veya doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="3bea5-227">Yuva geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="3bea5-227">Sockets improvements</span></span>

<span data-ttu-id="3bea5-228">.NET Core, daha yüksek düzey ağ API 'Lerinin temelini oluşturan <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> ve bir yeniden yazma <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType> olan yeni bir tür içerir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="3bea5-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, örneğin, <xref:System.Net.Http.HttpClient> uygulamasının temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="3bea5-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="3bea5-230">.NET Core 'un önceki sürümlerinde, daha üst düzey API 'Ler yerel ağ uygulamalarına dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="3bea5-231">.NET Core 2,1 ' de tanıtılan yuva uygulamasının çeşitli avantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="3bea5-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="3bea5-232">Önceki uygulamayla karşılaştırıldığında önemli bir performans geliştirmesi.</span><span class="sxs-lookup"><span data-stu-id="3bea5-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="3bea5-233">Dağıtım ve hizmeti kolaylaştıran platform bağımlılıklarını eleme.</span><span class="sxs-lookup"><span data-stu-id="3bea5-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="3bea5-234">Tüm .NET Core platformları genelinde tutarlı davranış.</span><span class="sxs-lookup"><span data-stu-id="3bea5-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="3bea5-235"><xref:System.Net.Http.SocketsHttpHandler>, .NET Core 2,1 ' de varsayılan uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="3bea5-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="3bea5-236">Ancak, <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemini çağırarak uygulamanızı eski <xref:System.Net.Http.HttpClientHandler> sınıfını kullanacak şekilde yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3bea5-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="3bea5-237">Ayrıca, <xref:System.Net.Http.SocketsHttpHandler>dayalı yuva uygulamalarını kullanmayı devre dışı bırakmak için bir ortam değişkeni de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="3bea5-238">Bunu yapmak için `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` `false` ya da 0 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3bea5-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="3bea5-239">Windows 'da, bir yerel uygulamaya bağlı <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType> ' ı veya bir sınıfın örneğini <xref:System.Net.Http.HttpClient> oluşturucusuna geçirerek <xref:System.Net.Http.SocketsHttpHandler> sınıfını kullanmayı da seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="3bea5-240">Linux ve macOS 'ta, işlem başına temelinde yalnızca <xref:System.Net.Http.HttpClient> ' ı yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="3bea5-241">Linux 'ta, eski <xref:System.Net.Http.HttpClient> uygulamasını kullanmak istiyorsanız, [libkıvrık](https://curl.haxx.se/libcurl/) dağıtım yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="3bea5-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="3bea5-242">(.NET Core 2,0 ile yüklenir.)</span><span class="sxs-lookup"><span data-stu-id="3bea5-242">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="3bea5-243">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3bea5-243">See also</span></span>

- [<span data-ttu-id="3bea5-244">​.NET Core'daki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="3bea5-244">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="3bea5-245">EF Core 2,1 ' deki yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="3bea5-245">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="3bea5-246">ASP.NET Core 2,1 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="3bea5-246">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
