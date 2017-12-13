---
title: ".NET core komut satırı arabirimi (CLI) araçları"
description: ".NET Core komut satırı arabirimi (CLI) araçları ve özelliklerinin genel bakış."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 0f43f569cdb8b9e4be68b61ba7b5cc4686fdb871
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/12/2017
---
# <a name="net-core-command-line-interface-cli-tools"></a><span data-ttu-id="59eda-103">.NET core komut satırı arabirimi (CLI) araçları</span><span class="sxs-lookup"><span data-stu-id="59eda-103">.NET Core command-line interface (CLI) tools</span></span>

<span data-ttu-id="59eda-104">.NET Core komut satırı arabirimi (CLI) .NET uygulamaları geliştirmek için bir yeni çapraz platform araç zinciri ' dir.</span><span class="sxs-lookup"><span data-stu-id="59eda-104">The .NET Core command-line interface (CLI) is a new cross-platform toolchain for developing .NET applications.</span></span> <span data-ttu-id="59eda-105">Tümleşik geliştirme ortamlarını (IDE), düzenleyiciler ve yapı orchestrators tuttuğunuzda gibi CLI üst düzey hangi araçların üzerine temelidir.</span><span class="sxs-lookup"><span data-stu-id="59eda-105">The CLI is a foundation upon which higher-level tools, such as Integrated Development Environments (IDEs), editors, and build orchestrators, can rest.</span></span>

## <a name="installation"></a><span data-ttu-id="59eda-106">Yükleme</span><span class="sxs-lookup"><span data-stu-id="59eda-106">Installation</span></span>

<span data-ttu-id="59eda-107">Yerel yükleyicileri kullanın ya da yükleme Kabuk komut dosyalarını kullanın:</span><span class="sxs-lookup"><span data-stu-id="59eda-107">Either use the native installers or use the installation shell scripts:</span></span>

* <span data-ttu-id="59eda-108">Yerel yükleyicileri öncelikle Geliştirici makinelerinde kullanılır ve desteklenen kullanım her platformun yerel mekanizması, örneğin, Windows Ubuntu veya MSI paketleri DEB paketlerini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="59eda-108">The native installers are primarily used on developer's machines and use each supported platform's native install mechanism, for instance, DEB packages on Ubuntu or MSI bundles on Windows.</span></span> <span data-ttu-id="59eda-109">Bu yükleyiciler yüklemek ve geliştirici tarafından hemen kullanmak için ortamı yapılandırmak ancak makine üzerinde yönetim ayrıcalıkları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="59eda-109">These installers install and configure the environment for immediate use by the developer but require administrative privileges on the machine.</span></span> <span data-ttu-id="59eda-110">' Ndaki yükleme yönergelerine görüntüleyebilirsiniz [.NET Core Yükleme Kılavuzu'na](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="59eda-110">You can view the installation instructions in the [.NET Core installation guide](https://aka.ms/dotnetcoregs).</span></span>
* <span data-ttu-id="59eda-111">Kabuk komut dosyalarını öncelikle yapı sunucuları veya yönetim ayrıcalıklarına kalmadan araçları yüklemek istediğiniz zaman ayarlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59eda-111">Shell scripts are primarily used for setting up build servers or when you wish to install the tools without administrative privileges.</span></span> <span data-ttu-id="59eda-112">Yükleme betikleri el ile yüklenmesi gereken makinede Önkoşulları Yükleme yok.</span><span class="sxs-lookup"><span data-stu-id="59eda-112">Install scripts don't install prerequisites on the machine, which must be installed manually.</span></span> <span data-ttu-id="59eda-113">Daha fazla bilgi için bkz: [betik başvuru konusu yüklemek](dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="59eda-113">For more information, see the [install script reference topic](dotnet-install-script.md).</span></span> <span data-ttu-id="59eda-114">Sürekli Tümleştirme (CI) derleme sunucunuzda CLI'yı ayarlama hakkında daha fazla bilgi için bkz: [kullanarak .NET Core SDK'yı ve araçları, sürekli tümleştirme (CI)](using-ci-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="59eda-114">For information on how to set up CLI on your continuous integration (CI) build server, see [Using .NET Core SDK and tools in Continuous Integration (CI)](using-ci-with-cli.md).</span></span>

<span data-ttu-id="59eda-115">Varsayılan olarak, CLI bir yan yana (SxS) şekilde yüklediği CLI araçlarını birden fazla sürümünü tek bir makinede bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="59eda-115">By default, the CLI installs in a side-by-side (SxS) manner, so multiple versions of the CLI tools can coexist on a single machine.</span></span> <span data-ttu-id="59eda-116">Birden çok sürümü yüklü olduğu bir makineye kullanılan hangi sürümünün belirleme açıklanmıştır daha ayrıntılı olarak [sürücü](#driver) bölümü.</span><span class="sxs-lookup"><span data-stu-id="59eda-116">Determining which version is used on a machine where multiple versions are installed is explained in more detail in the [Driver](#driver) section.</span></span>

## <a name="cli-commands"></a><span data-ttu-id="59eda-117">CLI komutları</span><span class="sxs-lookup"><span data-stu-id="59eda-117">CLI commands</span></span>

<span data-ttu-id="59eda-118">Aşağıdaki komutlar, varsayılan olarak yüklenir:</span><span class="sxs-lookup"><span data-stu-id="59eda-118">The following commands are installed by default:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="59eda-119">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="59eda-119">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="59eda-120">**Temel komutları**</span><span class="sxs-lookup"><span data-stu-id="59eda-120">**Basic commands**</span></span>

* [<span data-ttu-id="59eda-121">Yeni</span><span class="sxs-lookup"><span data-stu-id="59eda-121">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="59eda-122">geri yükleme</span><span class="sxs-lookup"><span data-stu-id="59eda-122">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="59eda-123">derleme</span><span class="sxs-lookup"><span data-stu-id="59eda-123">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="59eda-124">Yayımlama</span><span class="sxs-lookup"><span data-stu-id="59eda-124">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="59eda-125">çalıştırma</span><span class="sxs-lookup"><span data-stu-id="59eda-125">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="59eda-126">test etme</span><span class="sxs-lookup"><span data-stu-id="59eda-126">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="59eda-127">vstest</span><span class="sxs-lookup"><span data-stu-id="59eda-127">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="59eda-128">pack</span><span class="sxs-lookup"><span data-stu-id="59eda-128">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="59eda-129">geçirme</span><span class="sxs-lookup"><span data-stu-id="59eda-129">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="59eda-130">Temizleme</span><span class="sxs-lookup"><span data-stu-id="59eda-130">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="59eda-131">sln</span><span class="sxs-lookup"><span data-stu-id="59eda-131">sln</span></span>](dotnet-sln.md)
* [<span data-ttu-id="59eda-132">Yardım</span><span class="sxs-lookup"><span data-stu-id="59eda-132">help</span></span>](dotnet-help.md)
* [<span data-ttu-id="59eda-133">Depolama</span><span class="sxs-lookup"><span data-stu-id="59eda-133">store</span></span>](dotnet-store.md)

<span data-ttu-id="59eda-134">**Proje değişikliği komutları**</span><span class="sxs-lookup"><span data-stu-id="59eda-134">**Project modification commands**</span></span>

* [<span data-ttu-id="59eda-135">Paket ekleme</span><span class="sxs-lookup"><span data-stu-id="59eda-135">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="59eda-136">başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="59eda-136">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="59eda-137">paketi kaldırma</span><span class="sxs-lookup"><span data-stu-id="59eda-137">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="59eda-138">başvurusunu kaldırın</span><span class="sxs-lookup"><span data-stu-id="59eda-138">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="59eda-139">listesi başvurusu</span><span class="sxs-lookup"><span data-stu-id="59eda-139">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="59eda-140">**Gelişmiş komutları**</span><span class="sxs-lookup"><span data-stu-id="59eda-140">**Advanced commands**</span></span>

* [<span data-ttu-id="59eda-141">nuget Sil</span><span class="sxs-lookup"><span data-stu-id="59eda-141">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="59eda-142">nuget yerel öğeler</span><span class="sxs-lookup"><span data-stu-id="59eda-142">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="59eda-143">nuget gönderme</span><span class="sxs-lookup"><span data-stu-id="59eda-143">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="59eda-144">MSBuild</span><span class="sxs-lookup"><span data-stu-id="59eda-144">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="59eda-145">DotNet yükleme betiği</span><span class="sxs-lookup"><span data-stu-id="59eda-145">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="59eda-146">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="59eda-146">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="59eda-147">**Temel komutları**</span><span class="sxs-lookup"><span data-stu-id="59eda-147">**Basic commands**</span></span>

* [<span data-ttu-id="59eda-148">Yeni</span><span class="sxs-lookup"><span data-stu-id="59eda-148">new</span></span>](dotnet-new.md)
* [<span data-ttu-id="59eda-149">geri yükleme</span><span class="sxs-lookup"><span data-stu-id="59eda-149">restore</span></span>](dotnet-restore.md)
* [<span data-ttu-id="59eda-150">derleme</span><span class="sxs-lookup"><span data-stu-id="59eda-150">build</span></span>](dotnet-build.md)
* [<span data-ttu-id="59eda-151">Yayımlama</span><span class="sxs-lookup"><span data-stu-id="59eda-151">publish</span></span>](dotnet-publish.md)
* [<span data-ttu-id="59eda-152">çalıştırma</span><span class="sxs-lookup"><span data-stu-id="59eda-152">run</span></span>](dotnet-run.md)
* [<span data-ttu-id="59eda-153">test etme</span><span class="sxs-lookup"><span data-stu-id="59eda-153">test</span></span>](dotnet-test.md)
* [<span data-ttu-id="59eda-154">vstest</span><span class="sxs-lookup"><span data-stu-id="59eda-154">vstest</span></span>](dotnet-vstest.md)
* [<span data-ttu-id="59eda-155">pack</span><span class="sxs-lookup"><span data-stu-id="59eda-155">pack</span></span>](dotnet-pack.md)
* [<span data-ttu-id="59eda-156">geçirme</span><span class="sxs-lookup"><span data-stu-id="59eda-156">migrate</span></span>](dotnet-migrate.md)
* [<span data-ttu-id="59eda-157">Temizleme</span><span class="sxs-lookup"><span data-stu-id="59eda-157">clean</span></span>](dotnet-clean.md)
* [<span data-ttu-id="59eda-158">sln</span><span class="sxs-lookup"><span data-stu-id="59eda-158">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="59eda-159">**Proje değişikliği komutları**</span><span class="sxs-lookup"><span data-stu-id="59eda-159">**Project modification commands**</span></span>

* [<span data-ttu-id="59eda-160">Paket ekleme</span><span class="sxs-lookup"><span data-stu-id="59eda-160">add package</span></span>](dotnet-add-package.md)
* [<span data-ttu-id="59eda-161">başvuru ekleme</span><span class="sxs-lookup"><span data-stu-id="59eda-161">add reference</span></span>](dotnet-add-reference.md)
* [<span data-ttu-id="59eda-162">paketi kaldırma</span><span class="sxs-lookup"><span data-stu-id="59eda-162">remove package</span></span>](dotnet-remove-package.md)
* [<span data-ttu-id="59eda-163">başvurusunu kaldırın</span><span class="sxs-lookup"><span data-stu-id="59eda-163">remove reference</span></span>](dotnet-remove-reference.md)
* [<span data-ttu-id="59eda-164">listesi başvurusu</span><span class="sxs-lookup"><span data-stu-id="59eda-164">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="59eda-165">**Gelişmiş komutları**</span><span class="sxs-lookup"><span data-stu-id="59eda-165">**Advanced commands**</span></span>

* [<span data-ttu-id="59eda-166">nuget Sil</span><span class="sxs-lookup"><span data-stu-id="59eda-166">nuget delete</span></span>](dotnet-nuget-delete.md)
* [<span data-ttu-id="59eda-167">nuget yerel öğeler</span><span class="sxs-lookup"><span data-stu-id="59eda-167">nuget locals</span></span>](dotnet-nuget-locals.md)
* [<span data-ttu-id="59eda-168">nuget gönderme</span><span class="sxs-lookup"><span data-stu-id="59eda-168">nuget push</span></span>](dotnet-nuget-push.md)
* [<span data-ttu-id="59eda-169">MSBuild</span><span class="sxs-lookup"><span data-stu-id="59eda-169">msbuild</span></span>](dotnet-msbuild.md)
* [<span data-ttu-id="59eda-170">DotNet yükleme betiği</span><span class="sxs-lookup"><span data-stu-id="59eda-170">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="59eda-171">CLI projeleriniz için ek araçlar belirtmenize olanak sağlayan genişletilebilirlik modeli devralır.</span><span class="sxs-lookup"><span data-stu-id="59eda-171">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="59eda-172">Daha fazla bilgi için bkz: [.NET Core CLI genişletilebilirlik modeli](extensibility.md) konu.</span><span class="sxs-lookup"><span data-stu-id="59eda-172">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="59eda-173">Komut yapısı</span><span class="sxs-lookup"><span data-stu-id="59eda-173">Command structure</span></span>

<span data-ttu-id="59eda-174">CLI komut yapısını oluşur [("dotnet") sürücü](#driver), [komutu (veya "eylem")](#command-verb)ve büyük olasılıkla komut [bağımsız değişkenleri](#arguments) ve [seçenekleri](#options).</span><span class="sxs-lookup"><span data-stu-id="59eda-174">CLI command structure consists of the [the driver ("dotnet")](#driver), [the command (or "verb")](#command-verb), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="59eda-175">Adlı bir dizinden çalıştırıldığında Göster bu modelinde yeni bir konsol uygulaması oluşturma ve aşağıdaki komutları komut satırından çalıştırma gibi CLI işlemlerinin çoğu, gördüğünüz *my_app_3.sft*:</span><span class="sxs-lookup"><span data-stu-id="59eda-175">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="59eda-176">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="59eda-176">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="59eda-177">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="59eda-177">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```


---

### <a name="driver"></a><span data-ttu-id="59eda-178">Sürücü</span><span class="sxs-lookup"><span data-stu-id="59eda-178">Driver</span></span>

<span data-ttu-id="59eda-179">Sürücü adlı [dotnet](dotnet.md) ve iki sorumlulukları, ya da çalışan bir [framework bağımlı uygulama](../deploying/index.md) veya bir komut yürütülürken.</span><span class="sxs-lookup"><span data-stu-id="59eda-179">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> <span data-ttu-id="59eda-180">Yalnızca bir kez `dotnet` bir uygulamayı başlatmak için kullanıldığında bir komuttur olmadan kullanılır.</span><span class="sxs-lookup"><span data-stu-id="59eda-180">The only time `dotnet` is used without a command is when it's used to start an application.</span></span>

<span data-ttu-id="59eda-181">Framework bağımlı uygulamayı çalıştırın, örneğin, sürücü sonra uygulamayı belirlemek için `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="59eda-181">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="59eda-182">Uygulamanın DLL bulunduğu klasöründen komutu yürütülürken, yalnızca yürütme `dotnet my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="59eda-182">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span>

<span data-ttu-id="59eda-183">Sürücü için bir komut sağladığında `dotnet.exe` CLI komutu yürütme işlemi başlatır.</span><span class="sxs-lookup"><span data-stu-id="59eda-183">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="59eda-184">İlk olarak, sürücü kullanmak için SDK sürümü belirler.</span><span class="sxs-lookup"><span data-stu-id="59eda-184">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="59eda-185">Sürüm komutu seçeneklerinde belirtilmezse, sürücü en son sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="59eda-185">If the version isn't specified in the command options, the driver uses the latest version available.</span></span> <span data-ttu-id="59eda-186">Son yüklü olan sürümü dışında bir sürüm belirtmek için kullanın `--fx-version <VERSION>` seçeneği (bkz [dotnet komutu](dotnet.md) başvuru).</span><span class="sxs-lookup"><span data-stu-id="59eda-186">To specify a version other than the latest installed version, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span> <span data-ttu-id="59eda-187">SDK sürümü belirlendikten sonra sürücü komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="59eda-187">Once the SDK version is determined, the driver executes the command.</span></span>

### <a name="command-verb"></a><span data-ttu-id="59eda-188">Komut ("eylem")</span><span class="sxs-lookup"><span data-stu-id="59eda-188">Command ("verb")</span></span>

<span data-ttu-id="59eda-189">Komut (veya "eylem"), bir eylem gerçekleştiren yalnızca bir komuttur.</span><span class="sxs-lookup"><span data-stu-id="59eda-189">The command (or "verb") is simply a command that performs an action.</span></span> <span data-ttu-id="59eda-190">Örneğin, `dotnet build` kodunuzu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="59eda-190">For example, `dotnet build` builds your code.</span></span> <span data-ttu-id="59eda-191">`dotnet publish`kodunuzu yayımlar.</span><span class="sxs-lookup"><span data-stu-id="59eda-191">`dotnet publish` publishes your code.</span></span> <span data-ttu-id="59eda-192">Komutlar bir konsol uygulaması kullanarak olarak uygulanan bir `dotnet {verb}` kuralı.</span><span class="sxs-lookup"><span data-stu-id="59eda-192">The commands are implemented as a console application using a `dotnet {verb}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="59eda-193">Arguments</span><span class="sxs-lookup"><span data-stu-id="59eda-193">Arguments</span></span>

<span data-ttu-id="59eda-194">Komut satırında geçirdiğiniz bağımsız çağrılan komut için bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="59eda-194">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="59eda-195">Örneğin, yürütülürken `dotnet publish my_app.csproj`, `my_app.csproj` bağımsız değişkeni yayımlanacak projeyi gösterir ve geçirilir `publish` komutu.</span><span class="sxs-lookup"><span data-stu-id="59eda-195">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="59eda-196">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="59eda-196">Options</span></span>

<span data-ttu-id="59eda-197">Komut satırında geçirdiğiniz çağrılan komut seçenekleri seçeneklerdir.</span><span class="sxs-lookup"><span data-stu-id="59eda-197">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="59eda-198">Örneğin, yürütülürken `dotnet publish --output /build_output`, `--output` seçeneği ve değerini için geçirilir `publish` komutu.</span><span class="sxs-lookup"><span data-stu-id="59eda-198">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span> 

## <a name="migration-from-projectjson"></a><span data-ttu-id="59eda-199">Project.json geçiş</span><span class="sxs-lookup"><span data-stu-id="59eda-199">Migration from project.json</span></span>

<span data-ttu-id="59eda-200">Önizleme üretmek için tooling 2 kullandıysanız *project.json*-tabanlı projeler başvurun [dotnet geçirmek](dotnet-migrate.md) projeniz için MSBuild geçirme hakkında bilgi için konu /*.csproj*yayın araçları ile kullanım için.</span><span class="sxs-lookup"><span data-stu-id="59eda-200">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="59eda-201">.NET Core Preview 2 araç sürümünden önce ya da el ile oluşturulan projeleri yer alan yönergeleri izleyerek proje güncelleştirme [.NET Core CLI (project.json) DNX geçiş](../migration/from-dnx.md) ve sonra da `dotnet migrate` veya doğrudan yükseltme projelerinizi.</span><span class="sxs-lookup"><span data-stu-id="59eda-201">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="59eda-202">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="59eda-202">See also</span></span>

 [<span data-ttu-id="59eda-203">DotNet/CLI GitHub deposunu</span><span class="sxs-lookup"><span data-stu-id="59eda-203">dotnet/CLI GitHub Repository</span></span>](https://github.com/dotnet/cli/)  
 [<span data-ttu-id="59eda-204">.NET core Yükleme Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="59eda-204">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)  
