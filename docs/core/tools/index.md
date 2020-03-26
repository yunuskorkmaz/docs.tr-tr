---
title: .NET Core CLI
titleSuffix: ''
description: .NET Core CLI ve özelliklerine genel bakış.
ms.date: 02/13/2020
ms.openlocfilehash: ac5988bacbef41326f2501a2cff6c3f5aa0be798
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110847"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="ff35c-103">.NET Core CLI’ya genel bakış</span><span class="sxs-lookup"><span data-stu-id="ff35c-103">.NET Core CLI overview</span></span>

<span data-ttu-id="ff35c-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="ff35c-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="ff35c-105">.NET Core komut satırı arabirimi (CLI), .NET Core uygulamalarını geliştirmek, oluşturmak, çalıştırmak ve yayınlamak için bir çapraz platform araç zinciridir.</span><span class="sxs-lookup"><span data-stu-id="ff35c-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="ff35c-106">.NET Çekirdek CLI [.NET Çekirdek SDK](../sdk.md)ile birlikte verilir.</span><span class="sxs-lookup"><span data-stu-id="ff35c-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="ff35c-107">.NET Core SDK'yı nasıl yükleyin, [bkz.](../install/sdk.md)</span><span class="sxs-lookup"><span data-stu-id="ff35c-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="ff35c-108">CLI komutları</span><span class="sxs-lookup"><span data-stu-id="ff35c-108">CLI commands</span></span>

<span data-ttu-id="ff35c-109">Aşağıdaki komutlar varsayılan olarak yüklenir:</span><span class="sxs-lookup"><span data-stu-id="ff35c-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="ff35c-110">Temel komutlar</span><span class="sxs-lookup"><span data-stu-id="ff35c-110">Basic commands</span></span>

- [`new`](dotnet-new.md)
- [`restore`](dotnet-restore.md)
- [`build`](dotnet-build.md)
- [`publish`](dotnet-publish.md)
- [`run`](dotnet-run.md)
- [`test`](dotnet-test.md)
- [`vstest`](dotnet-vstest.md)
- [`pack`](dotnet-pack.md)
- [`migrate`](dotnet-migrate.md)
- [`clean`](dotnet-clean.md)
- [`sln`](dotnet-sln.md)
- [`help`](dotnet-help.md)
- [`store`](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="ff35c-111">Proje değişikliği komutları</span><span class="sxs-lookup"><span data-stu-id="ff35c-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="ff35c-112">Gelişmiş komutlar</span><span class="sxs-lookup"><span data-stu-id="ff35c-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="ff35c-113">Araç yönetimi komutları</span><span class="sxs-lookup"><span data-stu-id="ff35c-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="ff35c-114">[`tool restore`](global-tools.md#install-a-local-tool).NET Çekirdek SDK 3.0'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="ff35c-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="ff35c-115">[`tool run`](global-tools.md#invoke-a-local-tool).NET Çekirdek SDK 3.0'dan beri mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="ff35c-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="ff35c-116">Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="ff35c-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="ff35c-117">Araçları kendiniz yazabilir veya üçüncü şahıslar tarafından yazılmış araçları yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff35c-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="ff35c-118">Araçlar, genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="ff35c-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="ff35c-119">Daha fazla bilgi için [.NET Core araçlarına genel bakış](global-tools.md)ala.</span><span class="sxs-lookup"><span data-stu-id="ff35c-119">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="ff35c-120">Komut yapısı</span><span class="sxs-lookup"><span data-stu-id="ff35c-120">Command structure</span></span>

<span data-ttu-id="ff35c-121">CLI komut yapısı [sürücü ("dotnet")](#driver)oluşur, [komutu](#command)ve muhtemelen komut [bağımsız değişkenleri](#arguments) ve [seçenekleri](#options).</span><span class="sxs-lookup"><span data-stu-id="ff35c-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="ff35c-122">Bu deseni, yeni bir konsol uygulaması oluşturma ve komut satırından çalıştırmak gibi çoğu CLI işlemlerinde *my_app*adlı bir dizinden yürütüldüğünde aşağıdaki komutların gösterdiği gibi görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="ff35c-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="ff35c-123">Sürücü</span><span class="sxs-lookup"><span data-stu-id="ff35c-123">Driver</span></span>

<span data-ttu-id="ff35c-124">Sürücü [dotnet](dotnet.md) olarak adlandırılır ve iki sorumlulukları vardır, ya [bir çerçeve bağımlı uygulama](../deploying/index.md) çalıştırarak veya bir komut yürütme.</span><span class="sxs-lookup"><span data-stu-id="ff35c-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="ff35c-125">Çerçeveye bağımlı bir uygulamayı çalıştırmak için, uygulamayı sürücüden `dotnet /path/to/my_app.dll`sonra belirtin, örneğin.</span><span class="sxs-lookup"><span data-stu-id="ff35c-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="ff35c-126">Uygulamayın DLL'sinin bulunduğu klasörden komutu çalıştırırken, `dotnet my_app.dll`yürütmenizi yeterli</span><span class="sxs-lookup"><span data-stu-id="ff35c-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="ff35c-127">.NET Core Runtime'ın belirli bir sürümünü kullanmak `--fx-version <VERSION>` istiyorsanız, seçeneği kullanın [(dotnet komut](dotnet.md) başvurusuna bakın).</span><span class="sxs-lookup"><span data-stu-id="ff35c-127">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="ff35c-128">Sürücüye bir komut verdiyseniz, `dotnet.exe` CLI komut yürütme işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="ff35c-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="ff35c-129">Örnek:</span><span class="sxs-lookup"><span data-stu-id="ff35c-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="ff35c-130">İlk olarak, sürücü SDK'nın kullanacağı sürümü belirler.</span><span class="sxs-lookup"><span data-stu-id="ff35c-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="ff35c-131">[Global.json](global-json.md) dosyası yoksa, Kullanılabilir SDK'nın en son sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ff35c-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="ff35c-132">Bu, makinede en son ne olduğuna bağlı olarak bir önizleme veya kararlı sürüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="ff35c-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="ff35c-133">SDK sürümü belirlendikten sonra komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="ff35c-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="ff35c-134">Komut</span><span class="sxs-lookup"><span data-stu-id="ff35c-134">Command</span></span>

<span data-ttu-id="ff35c-135">Komut bir eylem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="ff35c-135">The command performs an action.</span></span> <span data-ttu-id="ff35c-136">Örneğin, `dotnet build` kod oluşturur.</span><span class="sxs-lookup"><span data-stu-id="ff35c-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="ff35c-137">`dotnet publish`kod yayımlar.</span><span class="sxs-lookup"><span data-stu-id="ff35c-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="ff35c-138">Komutlar bir `dotnet {command}` kuralkuralı kullanılarak konsol uygulaması olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ff35c-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="ff35c-139">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="ff35c-139">Arguments</span></span>

<span data-ttu-id="ff35c-140">Komut satırında geçirdiğiniz bağımsız değişkenler çağrılan komutun bağımsız değişkenleridir.</span><span class="sxs-lookup"><span data-stu-id="ff35c-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="ff35c-141">Örneğin, yürüttuğunuzda, `dotnet publish my_app.csproj` `my_app.csproj` bağımsız değişken yayımlanacak projeyi `publish` gösterir ve komuta geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ff35c-141">For example, when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="ff35c-142">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="ff35c-142">Options</span></span>

<span data-ttu-id="ff35c-143">Komut satırında geçirdiğiniz seçenekler, çağrılan komutun seçenekleridir.</span><span class="sxs-lookup"><span data-stu-id="ff35c-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="ff35c-144">Örneğin, çalıştırdığınızda, `dotnet publish --output /build_output` `--output` seçenek ve değeri komuta `publish` geçirilir.</span><span class="sxs-lookup"><span data-stu-id="ff35c-144">For example, when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff35c-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff35c-145">See also</span></span>

- [<span data-ttu-id="ff35c-146">dotnet/sdk GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="ff35c-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="ff35c-147">.NET Core kurulum kılavuzu</span><span class="sxs-lookup"><span data-stu-id="ff35c-147">.NET Core installation guide</span></span>](../install/sdk.md)
