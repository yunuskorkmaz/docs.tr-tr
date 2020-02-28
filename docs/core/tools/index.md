---
title: .NET Core CLI
titleSuffix: ''
description: .NET Core CLI ve özelliklerine genel bir bakış.
ms.date: 02/13/2020
ms.openlocfilehash: d84f96889cabc3fb4521e39db25050aacdd11546
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156718"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="44aa0-103">.NET Core CLI genel bakış</span><span class="sxs-lookup"><span data-stu-id="44aa0-103">.NET Core CLI overview</span></span>

<span data-ttu-id="44aa0-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="44aa0-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

<span data-ttu-id="44aa0-105">.NET Core komut satırı arabirimi (CLı), .NET Core uygulamaları geliştirmeye, oluşturmaya, çalıştırmaya ve yayımlamaya yönelik platformlar arası bir araç zinciridir.</span><span class="sxs-lookup"><span data-stu-id="44aa0-105">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="44aa0-106">.NET Core CLI, [.NET Core SDK](../sdk.md)dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="44aa0-106">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="44aa0-107">.NET Core SDK nasıl yükleneceğini öğrenmek için bkz. [.NET Core SDK yüklemesi](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="44aa0-107">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="44aa0-108">CLı komutları</span><span class="sxs-lookup"><span data-stu-id="44aa0-108">CLI commands</span></span>

<span data-ttu-id="44aa0-109">Aşağıdaki komutlar varsayılan olarak yüklenir:</span><span class="sxs-lookup"><span data-stu-id="44aa0-109">The following commands are installed by default:</span></span>

### <a name="basic-commands"></a><span data-ttu-id="44aa0-110">Temel komutlar</span><span class="sxs-lookup"><span data-stu-id="44aa0-110">Basic commands</span></span>

- [<span data-ttu-id="44aa0-111">new</span><span class="sxs-lookup"><span data-stu-id="44aa0-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="44aa0-112">restore</span><span class="sxs-lookup"><span data-stu-id="44aa0-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="44aa0-113">derlemeyi</span><span class="sxs-lookup"><span data-stu-id="44aa0-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="44aa0-114">publish</span><span class="sxs-lookup"><span data-stu-id="44aa0-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="44aa0-115">çalışmaz</span><span class="sxs-lookup"><span data-stu-id="44aa0-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="44aa0-116">sınamanız</span><span class="sxs-lookup"><span data-stu-id="44aa0-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="44aa0-117">VSTest</span><span class="sxs-lookup"><span data-stu-id="44aa0-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="44aa0-118">pack</span><span class="sxs-lookup"><span data-stu-id="44aa0-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="44aa0-119">geçirme</span><span class="sxs-lookup"><span data-stu-id="44aa0-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="44aa0-120">temizlenemedi</span><span class="sxs-lookup"><span data-stu-id="44aa0-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="44aa0-121">sln</span><span class="sxs-lookup"><span data-stu-id="44aa0-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="44aa0-122">Yardım</span><span class="sxs-lookup"><span data-stu-id="44aa0-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="44aa0-123">saklayabilir</span><span class="sxs-lookup"><span data-stu-id="44aa0-123">store</span></span>](dotnet-store.md)

### <a name="project-modification-commands"></a><span data-ttu-id="44aa0-124">Proje değişikliği komutları</span><span class="sxs-lookup"><span data-stu-id="44aa0-124">Project modification commands</span></span>

- [<span data-ttu-id="44aa0-125">Paket ekle</span><span class="sxs-lookup"><span data-stu-id="44aa0-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="44aa0-126">Başvuru Ekle</span><span class="sxs-lookup"><span data-stu-id="44aa0-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="44aa0-127">paketi kaldır</span><span class="sxs-lookup"><span data-stu-id="44aa0-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="44aa0-128">başvuruyu kaldır</span><span class="sxs-lookup"><span data-stu-id="44aa0-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="44aa0-129">liste başvurusu</span><span class="sxs-lookup"><span data-stu-id="44aa0-129">list reference</span></span>](dotnet-list-reference.md)

### <a name="advanced-commands"></a><span data-ttu-id="44aa0-130">Gelişmiş komutlar</span><span class="sxs-lookup"><span data-stu-id="44aa0-130">Advanced commands</span></span>

- [<span data-ttu-id="44aa0-131">NuGet silme</span><span class="sxs-lookup"><span data-stu-id="44aa0-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="44aa0-132">NuGet Yereller</span><span class="sxs-lookup"><span data-stu-id="44aa0-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="44aa0-133">NuGet gönderim</span><span class="sxs-lookup"><span data-stu-id="44aa0-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="44aa0-134">MSBUILD</span><span class="sxs-lookup"><span data-stu-id="44aa0-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="44aa0-135">DotNet install betiği</span><span class="sxs-lookup"><span data-stu-id="44aa0-135">dotnet install script</span></span>](dotnet-install-script.md)

### <a name="tool-management-commands"></a><span data-ttu-id="44aa0-136">Araç yönetimi komutları</span><span class="sxs-lookup"><span data-stu-id="44aa0-136">Tool management commands</span></span>

- [<span data-ttu-id="44aa0-137">Araç yüklemesi</span><span class="sxs-lookup"><span data-stu-id="44aa0-137">tool install</span></span>](dotnet-tool-install.md)
- [<span data-ttu-id="44aa0-138">araç listesi</span><span class="sxs-lookup"><span data-stu-id="44aa0-138">tool list</span></span>](dotnet-tool-list.md)
- [<span data-ttu-id="44aa0-139">Araç güncelleştirmesi</span><span class="sxs-lookup"><span data-stu-id="44aa0-139">tool update</span></span>](dotnet-tool-update.md)
- <span data-ttu-id="44aa0-140">[araç geri yükleme](global-tools.md#install-a-local-tool) **.NET Core SDK 3,0 ile başlayarak kullanılabilir**</span><span class="sxs-lookup"><span data-stu-id="44aa0-140">[tool restore](global-tools.md#install-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- <span data-ttu-id="44aa0-141">**.NET Core SDK 3,0 ' den başlayarak** [araç çalıştırma](global-tools.md#invoke-a-local-tool) kullanılabilir</span><span class="sxs-lookup"><span data-stu-id="44aa0-141">[tool run](global-tools.md#invoke-a-local-tool) **Available starting with .NET Core SDK 3.0**</span></span>
- [<span data-ttu-id="44aa0-142">araç kaldırma</span><span class="sxs-lookup"><span data-stu-id="44aa0-142">tool uninstall</span></span>](dotnet-tool-uninstall.md)

<span data-ttu-id="44aa0-143">Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="44aa0-143">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="44aa0-144">Araçları kendiniz yazabilir veya üçüncü taraflarca yazılmış Araçları yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="44aa0-144">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="44aa0-145">Araçlar genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="44aa0-145">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="44aa0-146">Daha fazla bilgi için bkz. [.NET Core araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="44aa0-146">For more information, see [.NET Core tools overview](global-tools.md).</span></span>

## <a name="command-structure"></a><span data-ttu-id="44aa0-147">Komut yapısı</span><span class="sxs-lookup"><span data-stu-id="44aa0-147">Command structure</span></span>

<span data-ttu-id="44aa0-148">CLı komut yapısı, [sürücüden ("DotNet")](#driver), [komuttan](#command)ve muhtemelen komut [bağımsız değişkenlerinden](#arguments) ve [seçeneklerden](#options)oluşur.</span><span class="sxs-lookup"><span data-stu-id="44aa0-148">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="44aa0-149">Bu kalıbı, yeni bir konsol uygulaması oluşturma ve aşağıdaki komutlar *my_app*adlı bir dizinden yürütüldüğünde gösterildiği gibi komut satırından çalıştırma gıbı birçok CLI işlemi içinde görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="44aa0-149">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

### <a name="driver"></a><span data-ttu-id="44aa0-150">Sürücü</span><span class="sxs-lookup"><span data-stu-id="44aa0-150">Driver</span></span>

<span data-ttu-id="44aa0-151">Sürücü [DotNet](dotnet.md) olarak adlandırılır ve [çerçeveye bağlı bir uygulama](../deploying/index.md) çalıştırarak ya da bir komut yürüten iki sorumluluklara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="44aa0-151">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span>

<span data-ttu-id="44aa0-152">Çerçeveye bağımlı bir uygulama çalıştırmak için, uygulamayı sürücüden sonra belirtin, örneğin, `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="44aa0-152">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="44aa0-153">Uygulamanın DLL 'sinin bulunduğu klasörden komutu yürütürken `dotnet my_app.dll`yürütmek yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="44aa0-153">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="44aa0-154">.NET Core çalışma zamanının belirli bir sürümünü kullanmak istiyorsanız, `--fx-version <VERSION>` seçeneğini kullanın ( [DotNet komut](dotnet.md) başvurusuna bakın).</span><span class="sxs-lookup"><span data-stu-id="44aa0-154">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="44aa0-155">Sürücüye bir komut sağlarsanız, `dotnet.exe` CLı komutu yürütme işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="44aa0-155">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="44aa0-156">Örnek:</span><span class="sxs-lookup"><span data-stu-id="44aa0-156">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="44aa0-157">İlk olarak, sürücü kullanılacak SDK sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="44aa0-157">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="44aa0-158">[Global. JSON](global-json.md) dosyası yoksa, kullanılabilir SDK 'nın en son sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="44aa0-158">If there is no [global.json](global-json.md) file, the latest version of the SDK available is used.</span></span> <span data-ttu-id="44aa0-159">Bu, makinede en son nelerin olduğuna bağlı olarak önizleme veya kararlı bir sürüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="44aa0-159">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="44aa0-160">SDK sürümü belirlendikten sonra, komutunu yürütür.</span><span class="sxs-lookup"><span data-stu-id="44aa0-160">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="44aa0-161">Komut</span><span class="sxs-lookup"><span data-stu-id="44aa0-161">Command</span></span>

<span data-ttu-id="44aa0-162">Komut bir eylem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="44aa0-162">The command performs an action.</span></span> <span data-ttu-id="44aa0-163">Örneğin, `dotnet build` derleme kodu.</span><span class="sxs-lookup"><span data-stu-id="44aa0-163">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="44aa0-164">`dotnet publish` kodu yayınlar.</span><span class="sxs-lookup"><span data-stu-id="44aa0-164">`dotnet publish` publishes code.</span></span> <span data-ttu-id="44aa0-165">Komutlar bir `dotnet {command}` kuralı kullanılarak konsol uygulaması olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="44aa0-165">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="44aa0-166">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="44aa0-166">Arguments</span></span>

<span data-ttu-id="44aa0-167">Komut satırında geçirdiğiniz bağımsız değişkenler çağrılan komutun bağımsız değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="44aa0-167">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="44aa0-168">Örneğin, `dotnet publish my_app.csproj`yürüttüğünüzde, `my_app.csproj` bağımsız değişkeni yayımlanacak projeyi belirtir ve `publish` komutuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="44aa0-168">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="44aa0-169">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="44aa0-169">Options</span></span>

<span data-ttu-id="44aa0-170">Komut satırında geçirdiğiniz seçenekler çağrılan komuta yönelik seçeneklerdir.</span><span class="sxs-lookup"><span data-stu-id="44aa0-170">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="44aa0-171">Örneğin `dotnet publish --output /build_output`yürüttüğünüzde, `--output` seçeneği ve değeri `publish` komutuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="44aa0-171">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="see-also"></a><span data-ttu-id="44aa0-172">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44aa0-172">See also</span></span>

- [<span data-ttu-id="44aa0-173">DotNet/SDK GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="44aa0-173">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="44aa0-174">.NET Core yükleme kılavuzu</span><span class="sxs-lookup"><span data-stu-id="44aa0-174">.NET Core installation guide</span></span>](../install/sdk.md)
