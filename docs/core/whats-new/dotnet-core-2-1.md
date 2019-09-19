---
title: ​.NET Core 2.1’deki yenilikler
description: .NET Core 2,1 ' de bulunan yeni özellikler hakkında bilgi edinin.
dev_langs:
- csharp
- vb
author: rpetrusha
ms.author: ronpet
ms.date: 10/10/2018
ms.openlocfilehash: 519c55dbe8b55191b682067da558167f86199b7e
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116215"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="eb2aa-103">​.NET Core 2.1’deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="eb2aa-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="eb2aa-104">.NET Core 2,1, aşağıdaki alanlarda geliştirmeler ve yeni özellikler içerir:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="eb2aa-105">Araçları</span><span class="sxs-lookup"><span data-stu-id="eb2aa-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="eb2aa-106">İleri al</span><span class="sxs-lookup"><span data-stu-id="eb2aa-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="eb2aa-107">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="eb2aa-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="eb2aa-108">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="eb2aa-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="eb2aa-109">JıT derleme geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="eb2aa-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="eb2aa-110">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="eb2aa-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="eb2aa-111">Araçlar</span><span class="sxs-lookup"><span data-stu-id="eb2aa-111">Tooling</span></span>

<span data-ttu-id="eb2aa-112">.NET Core 2,1 ' de yer alan araç, .NET Core 2,1 SDK (v 2.1.300), aşağıdaki değişiklikleri ve geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="eb2aa-113">Derleme performansı iyileştirmeleri</span><span class="sxs-lookup"><span data-stu-id="eb2aa-113">Build performance improvements</span></span>

<span data-ttu-id="eb2aa-114">.NET Core 2,1 ' nin önemli bir odağında, özellikle Artımlı derlemeler için derleme zamanı performansı geliştiriyoruz.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="eb2aa-115">Bu performans geliştirmeleri, Visual Studio 'daki derlemeler ve için kullanılan `dotnet build` komut satırı derlemeleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="eb2aa-116">İyileşme özgü bazı alanlarda şunlar vardır:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="eb2aa-117">Paket varlık çözümlemesi için, yalnızca tüm varlıklar yerine bir derleme tarafından kullanılan varlıkları çözümleme.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="eb2aa-118">Derleme başvurularını önbelleğe alma.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-118">Caching of assembly references.</span></span>

- <span data-ttu-id="eb2aa-119">Tek tek `dotnet build` etkinleştirmeleri genelinde yayılan süreçler olan uzun süre çalışan SDK yapı sunucularının kullanımı.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="eb2aa-120">Her `dotnet build` çalıştırıldığında büyük kod bloklarını JIT derleme ihtiyacını ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="eb2aa-121">Yapı sunucusu işlemi aşağıdaki komutla otomatik olarak sonlandırılabilir:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="eb2aa-122">Yeni CLı komutları</span><span class="sxs-lookup"><span data-stu-id="eb2aa-122">New CLI commands</span></span>

<span data-ttu-id="eb2aa-123">Artık .NET Core SDK bir parçası olarak, kullanılarak [`DotnetCliToolReference`](../tools/extensibility.md) yalnızca proje bazında kullanılabilen birçok araç mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="eb2aa-124">Bu araçlar şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-124">These tools include:</span></span>

- <span data-ttu-id="eb2aa-125">`dotnet watch`belirli bir komut kümesini yürütmeden önce bir dosyanın değiştirilmesini bekleyen bir dosya sistem izleyicisi sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="eb2aa-126">Örneğin, aşağıdaki komut, geçerli projeyi otomatik olarak yeniden oluşturur ve her bir dosya değiştiğinde ayrıntılı çıkış üretir:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="eb2aa-127">Seçenekten önce gelen seçeneğe göz önüne alın. `--` `--verbose`</span><span class="sxs-lookup"><span data-stu-id="eb2aa-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="eb2aa-128">`dotnet watch` Alt`dotnet` işleme geçirilen bağımsız değişkenlerden doğrudan komutuna geçirilen seçenekleri ayırır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="eb2aa-129">Bu `--verbose` seçenek olmadan, komut komutuna değil `dotnet build` , `dotnet watch` komut için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="eb2aa-130">Daha fazla bilgi için bkz. [DotNet Watch kullanarak ASP.NET Core uygulamaları geliştirme](/aspnet/core/tutorials/dotnet-watch)</span><span class="sxs-lookup"><span data-stu-id="eb2aa-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch)</span></span>

- <span data-ttu-id="eb2aa-131">`dotnet dev-certs`ASP.NET Core uygulamalarında geliştirme sırasında kullanılan sertifikaları oluşturur ve yönetir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="eb2aa-132">`dotnet user-secrets`ASP.NET Core uygulamalarında bir Kullanıcı gizli deposundaki gizli dizileri yönetir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="eb2aa-133">`dotnet sql-cache`dağıtılmış önbelleğe alma için kullanılacak bir Microsoft SQL Server veritabanında tablo ve dizinler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="eb2aa-134">`dotnet ef`, Entity Framework Core uygulamalarında veritabanlarını, <xref:Microsoft.EntityFrameworkCore.DbContext> nesneleri ve geçişleri yönetmeye yönelik bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="eb2aa-135">Daha fazla bilgi için bkz. [.NET komut satırı araçlarını EF Core](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="eb2aa-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="eb2aa-136">Genel Araçlar</span><span class="sxs-lookup"><span data-stu-id="eb2aa-136">Global Tools</span></span>

<span data-ttu-id="eb2aa-137">.NET Core 2,1, *genel araçları* destekler-diğer bir deyişle, komut satırından küresel olarak kullanılabilir özel araçlar.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="eb2aa-138">.NET Core 'un önceki sürümlerindeki genişletilebilirlik modeli, yalnızca kullanarak [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools)bir proje temelinde bulunan özel araçları kullanıma sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="eb2aa-139">Küresel bir araç yüklemek için [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="eb2aa-140">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="eb2aa-141">Yüklendikten sonra araç, araç adı belirtilerek komut satırından çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="eb2aa-142">Daha fazla bilgi için bkz. [.NET Core genel araçlarına genel bakış](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="eb2aa-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="eb2aa-143">`dotnet tool` Komutuyla araç yönetimi</span><span class="sxs-lookup"><span data-stu-id="eb2aa-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="eb2aa-144">.NET Core 2,1 SDK 'da tüm araçlar işlemleri `dotnet tool` komutunu kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="eb2aa-145">Aşağıdaki seçenekler mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-145">The following options are available:</span></span>

- <span data-ttu-id="eb2aa-146">[`dotnet tool install`](../tools/dotnet-tool-install.md)bir araç yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="eb2aa-147">[`dotnet tool update`](../tools/dotnet-tool-update.md)etkin bir şekilde güncelleştiren bir aracı kaldırmak ve yeniden yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="eb2aa-148">[`dotnet tool list`](../tools/dotnet-tool-list.md)yüklü olan araçları listelemek için.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="eb2aa-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md)yüklü olan araçları kaldırmak için.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="eb2aa-150">İleri al</span><span class="sxs-lookup"><span data-stu-id="eb2aa-150">Roll forward</span></span>

<span data-ttu-id="eb2aa-151">.NET Core 2,0 ile başlayan tüm .NET Core Uygulamaları, bir sistemde yüklü en son alt *sürüme* otomatik olarak ileri doğru iletir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="eb2aa-152">.NET Core 2,0 ile başlayarak, bir uygulamanın derlenme .NET Core sürümü çalışma zamanında mevcut değilse, uygulama otomatik olarak .NET Core 'un en son yüklenen alt *sürümünde* çalışır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="eb2aa-153">Diğer bir deyişle, bir uygulama .NET Core 2,0 ile derlen, ancak .NET Core 2,0 de ana bilgisayar sisteminde yoksa ancak .NET Core 2,1 ise, uygulama .NET Core 2,1 ile çalışır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="eb2aa-154">Bu geri alma davranışı önizleme sürümleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="eb2aa-155">Varsayılan olarak, ana yayınlar için de uygulanmaz, ancak bu, aşağıdaki ayarlarla değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="eb2aa-156">Bu davranışı, aday paylaşılan çerçeve olmadan geri alma ayarını değiştirerek değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="eb2aa-157">Kullanılabilir ayarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-157">The available settings are:</span></span>

- <span data-ttu-id="eb2aa-158">`0`-ikincil sürüm alma-iletme davranışını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="eb2aa-159">Bu ayarla, .NET Core 2.0.0 için oluşturulmuş bir uygulama .NET Core 2.0.1 'e, ancak .NET Core 2.2.0 veya .NET Core 3.0.0 'e geri alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="eb2aa-160">`1`-ikincil sürüm alma-iletme davranışını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="eb2aa-161">Bu ayar için varsayılan değerdir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-161">This is the default value for the setting.</span></span> <span data-ttu-id="eb2aa-162">Bu ayarla, .NET Core 2.0.0 için oluşturulmuş bir uygulama, ne olduğuna bağlı olarak .NET Core 2.0.1 veya .NET Core 2.2.0 'e doğru bir şekilde gönderilir, ancak .NET Core 3.0.0 'e geri almaz.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="eb2aa-163">`2`-küçük ve ana sürüm alma-iletme davranışını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="eb2aa-164">Ayarlanırsa, farklı ana sürümler de dikkate alınır, bu nedenle .NET Core 2.0.0 için derlenmiş bir uygulama .NET Core 3.0.0 'e geri alınacaktır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="eb2aa-165">Bu ayarı, üç şekilde değiştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="eb2aa-166">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` Ortam değişkenini istenen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="eb2aa-167">Aşağıdaki satırı, istenen değeri *. runtimeconfig. JSON* dosyasına ekleyin:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="eb2aa-168">[.NET Core CLI araçlarını](../tools/index.md)kullanırken, aşağıdaki seçeneği gibi bir .NET Core komutuna `run`istenen değeri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-168">When using [.NET Core CLI tools](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="eb2aa-169">Düzeltme Eki Sürümü ileri, bu ayardan bağımsızdır ve herhangi bir olası küçük veya büyük sürüm ileri doğru uygulandıktan sonra yapılır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="eb2aa-170">Dağıtım</span><span class="sxs-lookup"><span data-stu-id="eb2aa-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="eb2aa-171">Kendi içinde uygulama Bakımı</span><span class="sxs-lookup"><span data-stu-id="eb2aa-171">Self-contained application servicing</span></span>

<span data-ttu-id="eb2aa-172">`dotnet publish`Şimdi, hizmet verilen çalışma zamanı sürümü ile bağımsız uygulamalar yayımlar.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="eb2aa-173">Bir bağımsız uygulamayı .NET Core 2,1 SDK (v 2.1.300) ile yayımladığınızda, uygulamanız ilgili SDK tarafından bilinen en son hizmet verilen çalışma zamanı sürümünü içerir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="eb2aa-174">En son SDK 'ya yükselttiğinizde, en son .NET Core çalışma zamanı sürümü ile yayımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-174">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="eb2aa-175">Bu, .NET Core 1,0 çalışma zamanları ve üzeri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="eb2aa-176">Kendi içinde yayımlama, NuGet.org üzerinde çalışma zamanı sürümlerini kullanır. Makinenizde bakım çalışma zamanına sahip olmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="eb2aa-177">.NET Core 2,0 SDK 'sını kullanarak, `RuntimeFrameworkVersion` özelliği aracılığıyla farklı bir sürüm belirtilmediği takdirde, kendi içinde bulunan uygulamalar .NET Core 2.0.0 Runtime ile yayımlanır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="eb2aa-178">Bu yeni davranışla birlikte, bu özelliği, otomatik olarak kapsanan bir uygulama için daha yüksek bir çalışma zamanı sürümü seçmek üzere ayarlamanıza gerek kalmaz.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-178">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="eb2aa-179">En kolay yaklaşım .NET Core 2,1 SDK (v 2.1.300) ile her zaman yayımlamaktır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="eb2aa-180">Daha fazla bilgi için bkz. [kendi kendine içerilen dağıtım çalışma zamanı ileri](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="eb2aa-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="eb2aa-181">Windows Uyumluluk Paketi</span><span class="sxs-lookup"><span data-stu-id="eb2aa-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="eb2aa-182">.NET Framework mevcut koddan .NET Core 'a bağlantı oluşturduğunuzda [Windows Uyumluluk Paketi](https://www.nuget.org/packages/Microsoft.Windows.Compatibility)' ni kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="eb2aa-183">.NET Core 'da bulunandan daha fazla 20.000 API erişimi sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="eb2aa-184">Bu API 'ler <xref:System.Drawing?displayProperty=nameWithType> ad alanı <xref:System.Diagnostics.EventLog> , sınıf, WMI, performans sayaçları, Windows Hizmetleri ve Windows kayıt defteri türleri ve üyeleri türlerini içerir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="eb2aa-185">JıT derleyicisi geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="eb2aa-185">JIT compiler improvements</span></span>

<span data-ttu-id="eb2aa-186">.NET Core, performansı önemli ölçüde iyileştirebilen *katmanlı derleme* ( *Uyarlamalı iyileştirme*olarak da bilinir) adlı yeni bir JIT Derleyici teknolojisini içerir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="eb2aa-187">Katmanlı derleme, bir katılım ayarıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="eb2aa-188">JıT derleyicisi tarafından gerçekleştirilen önemli görevlerden biri, kod yürütmeyi iyileştiriliyor.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="eb2aa-189">Ancak, daha az kullanılan kod yolları için, derleyici en iyi duruma getirilmiş kodu çalıştırmaya kıyasla kodu en iyi duruma getirmek için daha fazla zaman harcayabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="eb2aa-190">Katmanlı derleme JıT derlemesinde iki aşama sunar:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="eb2aa-191">Mümkün olduğunca hızlı bir şekilde kod üreten **ilk katman**.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="eb2aa-192">Sık çalıştırılan yöntemler için iyileştirilmiş kod üreten **ikinci bir katman**.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="eb2aa-193">İkinci derleme katmanı, gelişmiş performans için paralel olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="eb2aa-194">Katmanlı derlemeyi iki şekilde seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="eb2aa-195">Katmanlı derlemeyi .NET Core 2,1 SDK kullanan tüm projelerde kullanmak için aşağıdaki ortam değişkenini ayarlayın:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="eb2aa-196">Katmanlı derlemeyi proje başına temelinde kullanmak için, aşağıdaki örnekte gösterildiği gibi, `<TieredCompilation>` özelliği `<PropertyGroup>` MSBuild proje dosyasının bölümüne ekleyin:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="eb2aa-197">API değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="eb2aa-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="eb2aa-198">`Span<T>` ve `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="eb2aa-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="eb2aa-199">.NET Core 2,1, diziler ve diğer bellek türleriyle çalışmayı çok daha verimli hale getirmek için bazı yeni türler içerir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="eb2aa-200">Yeni türler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-200">The new types include:</span></span>

- <span data-ttu-id="eb2aa-201"><xref:System.Span%601?displayProperty=nameWithType>ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="eb2aa-202"><xref:System.Memory%601?displayProperty=nameWithType>ve <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="eb2aa-203">Bu türler olmadan, bu tür öğeleri bir dizinin bir bölümü veya bir bellek arabelleğinin bir bölümü olarak geçirirken, bir yönteme geçirmeden önce verilerin bir kısmının kopyasını oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="eb2aa-204">Bu türler, ek bellek ayırma ve kopyalama işlemlerine gereksinimi ortadan kaldıran bu verilerin sanal bir görünümünü sağlar.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="eb2aa-205">Aşağıdaki örnek, bir <xref:System.Span%601> dizi 10 öğenin sanal görünümünü sağlamak için ve <xref:System.Memory%601> örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

[!code-vb[Memory\<T>](~/samples/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="eb2aa-206">Brotli sıkıştırma</span><span class="sxs-lookup"><span data-stu-id="eb2aa-206">Brotli compression</span></span>

<span data-ttu-id="eb2aa-207">.NET Core 2,1, Brotli sıkıştırma ve açma için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="eb2aa-208">Brotli, [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) ' de tanımlanan ve çoğu Web tarayıcısı ve ana Web sunucusu tarafından desteklenen genel amaçlı kayıpsız bir sıkıştırma algoritmasıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="eb2aa-209">Stream tabanlı <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> sınıfı veya yüksek performanslı yayılma tabanlı <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> ve <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> sınıfları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="eb2aa-210">Aşağıdaki örnek, <xref:System.IO.Compression.BrotliStream> sınıfıyla sıkıştırmayı gösterir:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

<span data-ttu-id="eb2aa-211">Davranışı ve ile <xref:System.IO.Compression.GZipStream>aynıdır ve bu API 'leri <xref:System.IO.Compression.BrotliStream>çağıran kodu dönüştürmeyi kolaylaştırır. <xref:System.IO.Compression.DeflateStream> <xref:System.IO.Compression.BrotliStream></span><span class="sxs-lookup"><span data-stu-id="eb2aa-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="eb2aa-212">Yeni şifreleme API 'Leri ve şifreleme geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="eb2aa-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="eb2aa-213">.NET Core 2,1, şifreleme API 'Lerinde çok sayıda geliştirme içerir:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="eb2aa-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType>System. Security. Cryptography. Pkcs paketinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="eb2aa-215">Uygulama, .NET Framework <xref:System.Security.Cryptography.Pkcs.SignedCms> sınıfıyla aynıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="eb2aa-216"><xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> Ve<xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> yöntemlerinin yeni aşırı yüklemeleri, çağıranların SHA-1 dışındaki algoritmaları kullanarak sertifika parmak izi değerlerini almasını sağlamak için bir karma algoritma tanımlayıcısı kabul eder.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="eb2aa-217">Yeni <xref:System.Span%601>tabanlı şifreleme API 'leri, karma, HMAC, şifreleme rastgele sayı oluşturma, asimetrik imza oluşturma, asimetrik imza işleme ve RSA şifrelemesi için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="eb2aa-218">Performansı <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> , tabanlı bir <xref:System.Span%601>uygulama kullanılarak% 15 oranında artmıştır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="eb2aa-219">Yeni <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> sınıf iki yeni yöntem içerir:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="eb2aa-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A>aynı uzunlukta olan iki giriş için geri dönüş için sabit bir zaman alır. Bu, zamanlama tarafı kanal bilgilerine katkıda bulunmaktan kaçınmak için şifreleme doğrulamasında kullanılması uygun hale getirir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="eb2aa-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A>, iyileştirelemeyen bir bellek temizleme yordamdır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="eb2aa-222">Statik <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> Yöntem bir <xref:System.Span%601> değerini rastgele değerlerle doldurur.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="eb2aa-223"><xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> Artık Linux ve Maxos üzerinde desteklenmektedir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and maxOS.</span></span>

- <span data-ttu-id="eb2aa-224">Eliptik Eğri Diffie-Hellman (ecdh) artık <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> sınıf ailesinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="eb2aa-225">Yüzey alanı .NET Framework ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="eb2aa-226">Tarafından <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> döndürülen örnek, bir SHA-2 Özeti kullanarak oaep ile şifreleyebilir veya şifresini çözebilir, ayrıca RSA-PSS kullanarak imzaları oluşturabilir veya doğrulayabilir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="eb2aa-227">Yuva geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="eb2aa-227">Sockets improvements</span></span>

<span data-ttu-id="eb2aa-228">.NET Core, daha üst düzey ağ <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>API 'lerinin temelini oluşturan <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>yeni bir tür ve yeniden yazma içerir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="eb2aa-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>Örneğin, <xref:System.Net.Http.HttpClient> uygulamanın temelini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="eb2aa-230">.NET Core 'un önceki sürümlerinde, daha üst düzey API 'Ler yerel ağ uygulamalarına dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="eb2aa-231">.NET Core 2,1 ' de tanıtılan yuva uygulamasının çeşitli avantajları vardır:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="eb2aa-232">Önceki uygulamayla karşılaştırıldığında önemli bir performans geliştirmesi.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="eb2aa-233">Dağıtım ve hizmeti kolaylaştıran platform bağımlılıklarını eleme.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="eb2aa-234">Tüm .NET Core platformları genelinde tutarlı davranış.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="eb2aa-235"><xref:System.Net.Http.SocketsHttpHandler>, .NET Core 2,1 ' de varsayılan uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="eb2aa-236">Ancak, <xref:System.Net.Http.HttpClientHandler> <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> yöntemini çağırarak uygulamanızı eski sınıfı kullanacak şekilde yapılandırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="eb2aa-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="eb2aa-237">Ayrıca, ' yi temel alan <xref:System.Net.Http.SocketsHttpHandler>yuva uygulamalarını kullanmaya geri çevirmek için bir ortam değişkeni de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="eb2aa-238">Bunu yapmak için, `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` öğesini ya da `false` 0 olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="eb2aa-239">Windows 'da, bir yerel uygulamaya bağlı olan <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType> <xref:System.Net.Http.SocketsHttpHandler> veya sınıfı <xref:System.Net.Http.HttpClient> bir örneği oluşturucuya geçirerek sınıfı kullanmayı da seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="eb2aa-240">Linux ve MacOS 'ta yalnızca işlem başına temelinde yapılandırabilirsiniz <xref:System.Net.Http.HttpClient> .</span><span class="sxs-lookup"><span data-stu-id="eb2aa-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="eb2aa-241">Linux 'ta, eski <xref:System.Net.Http.HttpClient> uygulamayı kullanmak istiyorsanız [libkıvrık](https://curl.haxx.se/libcurl/) dağıtım yapmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="eb2aa-242">(.NET Core 2,0 ile yüklenir.)</span><span class="sxs-lookup"><span data-stu-id="eb2aa-242">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="eb2aa-243">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb2aa-243">See also</span></span>

- [<span data-ttu-id="eb2aa-244">​.NET Core'daki Yenilikler</span><span class="sxs-lookup"><span data-stu-id="eb2aa-244">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="eb2aa-245">EF Core 2,1 ' deki yeni özellikler</span><span class="sxs-lookup"><span data-stu-id="eb2aa-245">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="eb2aa-246">ASP.NET Core 2,1 ' deki yenilikler</span><span class="sxs-lookup"><span data-stu-id="eb2aa-246">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
