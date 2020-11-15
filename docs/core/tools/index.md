---
title: .NET CLı
titleSuffix: ''
description: .NET CLı ve özelliklerine genel bakış.
ms.topic: overview
ms.date: 02/13/2020
ms.openlocfilehash: 6a12e2d16afe36092c10e14a7465fa3bdbb23f32
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94633862"
---
# <a name="net-cli-overview"></a><span data-ttu-id="4a009-103">.NET CLı genel bakış</span><span class="sxs-lookup"><span data-stu-id="4a009-103">.NET CLI overview</span></span>

<span data-ttu-id="4a009-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="4a009-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="4a009-105">.NET komut satırı arabirimi (CLı), .NET uygulamaları geliştirmeye, oluşturmaya, çalıştırmaya ve yayımlamaya yönelik platformlar arası bir araç zinciridir.</span><span class="sxs-lookup"><span data-stu-id="4a009-105">The .NET command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET applications.</span></span>

<span data-ttu-id="4a009-106">.Net CLı, [.NET SDK 'ya](../sdk.md)dahildir.</span><span class="sxs-lookup"><span data-stu-id="4a009-106">The .NET CLI is included with the [.NET SDK](../sdk.md).</span></span> <span data-ttu-id="4a009-107">.NET SDK 'yı yüklemeyi öğrenmek için bkz. [.NET Core 'U yüklemek](../install/windows.md).</span><span class="sxs-lookup"><span data-stu-id="4a009-107">To learn how to install the .NET SDK, see [Install .NET Core](../install/windows.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="4a009-108">CLI komutları</span><span class="sxs-lookup"><span data-stu-id="4a009-108">CLI commands</span></span>

<span data-ttu-id="4a009-109">Aşağıdaki komutlar varsayılan olarak yüklenir:</span><span class="sxs-lookup"><span data-stu-id="4a009-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="4a009-110">Temel komutlar</span><span class="sxs-lookup"><span data-stu-id="4a009-110">Basic commands</span></span>

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

### <a name="project-modification-commands"></a><span data-ttu-id="4a009-111">Proje değişikliği komutları</span><span class="sxs-lookup"><span data-stu-id="4a009-111">Project modification commands</span></span>

- [`add package`](dotnet-add-package.md)
- [`add reference`](dotnet-add-reference.md)
- [`remove package`](dotnet-remove-package.md)
- [`remove reference`](dotnet-remove-reference.md)
- [`list reference`](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="4a009-112">Gelişmiş komutlar</span><span class="sxs-lookup"><span data-stu-id="4a009-112">Advanced commands</span></span>

- [`nuget delete`](dotnet-nuget-delete.md)
- [`nuget locals`](dotnet-nuget-locals.md)
- [`nuget push`](dotnet-nuget-push.md)
- [`msbuild`](dotnet-msbuild.md)
- [`dotnet install script`](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="4a009-113">Araç yönetimi komutları</span><span class="sxs-lookup"><span data-stu-id="4a009-113">Tool management commands</span></span>

- [`tool install`](dotnet-tool-install.md)
- [`tool list`](dotnet-tool-list.md)
- [`tool update`](dotnet-tool-update.md)
- <span data-ttu-id="4a009-114">[`tool restore`](global-tools.md#install-a-local-tool) 3,0 .NET Core SDK bu yana kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a009-114">[`tool restore`](global-tools.md#install-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- <span data-ttu-id="4a009-115">[`tool run`](global-tools.md#invoke-a-local-tool) 3,0 .NET Core SDK bu yana kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a009-115">[`tool run`](global-tools.md#invoke-a-local-tool) Available since .NET Core SDK 3.0.</span></span>
- [`tool uninstall`](dotnet-tool-uninstall.md)

<span data-ttu-id="4a009-116">Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="4a009-116">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="4a009-117">Araçları kendiniz yazabilir veya üçüncü taraflarca yazılmış Araçları yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4a009-117">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="4a009-118">Araçlar genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="4a009-118">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="4a009-119">Daha fazla bilgi için bkz. [.net araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="4a009-119">For more information, see [.NET tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="4a009-120">Komut yapısı</span><span class="sxs-lookup"><span data-stu-id="4a009-120">Command structure</span></span>

<span data-ttu-id="4a009-121">CLı komut yapısı, [sürücüden ("DotNet")](#driver), [komuttan](#command)ve muhtemelen komut [bağımsız değişkenlerinden](#arguments) ve [seçeneklerden](#options)oluşur.</span><span class="sxs-lookup"><span data-stu-id="4a009-121">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="4a009-122">Bu kalıbı, yeni bir konsol uygulaması oluşturma ve aşağıdaki komutlar *my_app* adlı bir dizinden yürütüldüğünde gösterildiği gibi komut satırından çalıştırma gıbı birçok CLI işlemi içinde görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="4a009-122">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app* :</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="4a009-123">Sürücü</span><span class="sxs-lookup"><span data-stu-id="4a009-123">Driver</span></span>

<span data-ttu-id="4a009-124">Sürücü [DotNet](dotnet.md) olarak adlandırılır ve [çerçeveye bağlı bir uygulama](../deploying/index.md) çalıştırarak ya da bir komut yürüten iki sorumluluklara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="4a009-124">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="4a009-125">Çerçeveye bağımlı bir uygulama çalıştırmak için, uygulamayı sürücüden sonra belirtin, örneğin, `dotnet /path/to/my_app.dll` .</span><span class="sxs-lookup"><span data-stu-id="4a009-125">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="4a009-126">Komutu, uygulamanın DLL 'sinin bulunduğu klasörden yürütürken yalnızca yürütün `dotnet my_app.dll` .</span><span class="sxs-lookup"><span data-stu-id="4a009-126">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="4a009-127">.NET çalışma zamanının belirli bir sürümünü kullanmak istiyorsanız, `--fx-version <VERSION>` seçeneğini kullanın ( [DotNet komut](dotnet.md) başvurusuna bakın).</span><span class="sxs-lookup"><span data-stu-id="4a009-127">If you want to use a specific version of the .NET Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="4a009-128">Sürücüye bir komut sağlarsanız, `dotnet.exe` CLI komutu yürütme işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="4a009-128">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="4a009-129">Örnek:</span><span class="sxs-lookup"><span data-stu-id="4a009-129">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="4a009-130">İlk olarak, sürücü kullanılacak SDK sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="4a009-130">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="4a009-131">Dosyada [global.js](global-json.md) yoksa, SDK 'nın en son sürümü kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4a009-131">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="4a009-132">Bu, makinede en son nelerin olduğuna bağlı olarak önizleme veya kararlı bir sürüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="4a009-132">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="4a009-133">SDK sürümü belirlendikten sonra, komutunu yürütür.</span><span class="sxs-lookup"><span data-stu-id="4a009-133">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="4a009-134">Komut</span><span class="sxs-lookup"><span data-stu-id="4a009-134">Command</span></span>

<span data-ttu-id="4a009-135">Komut bir eylem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="4a009-135">The command performs an action.</span></span> <span data-ttu-id="4a009-136">Örneğin, `dotnet build` derleme kodu.</span><span class="sxs-lookup"><span data-stu-id="4a009-136">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="4a009-137">`dotnet publish` kodu yayımlar.</span><span class="sxs-lookup"><span data-stu-id="4a009-137">`dotnet publish` publishes code.</span></span> <span data-ttu-id="4a009-138">Komutlar, bir kural kullanılarak konsol uygulaması olarak uygulanır `dotnet {command}` .</span><span class="sxs-lookup"><span data-stu-id="4a009-138">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="4a009-139">Arguments</span><span class="sxs-lookup"><span data-stu-id="4a009-139">Arguments</span></span>

<span data-ttu-id="4a009-140">Komut satırında geçirdiğiniz bağımsız değişkenler çağrılan komutun bağımsız değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="4a009-140">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="4a009-141">Örneğin, çalıştırdığınızda `dotnet publish my_app.csproj` `my_app.csproj` bağımsız değişkeni yayımlanacak projeyi belirtir ve `publish` komutuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="4a009-141">For example, when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="4a009-142">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="4a009-142">Options</span></span>

<span data-ttu-id="4a009-143">Komut satırında geçirdiğiniz seçenekler çağrılan komuta yönelik seçeneklerdir.</span><span class="sxs-lookup"><span data-stu-id="4a009-143">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="4a009-144">Örneğin, yürüttüğünüzde `dotnet publish --output /build_output` , `--output` seçeneği ve değeri `publish` komutuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="4a009-144">For example, when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="4a009-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4a009-145">See also</span></span>

- [<span data-ttu-id="4a009-146">DotNet/SDK GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="4a009-146">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="4a009-147">.NET yükleme kılavuzu</span><span class="sxs-lookup"><span data-stu-id="4a009-147">.NET installation guide</span></span>](../install/windows.md)
