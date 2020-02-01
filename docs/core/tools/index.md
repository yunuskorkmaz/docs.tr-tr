---
title: .NET Core CLI
titleSuffix: ''
description: .NET Core CLI ve özelliklerine genel bir bakış.
ms.date: 08/14/2017
ms.openlocfilehash: b0a8e0dd8cf77bb6f7567c27e9972f62515ec0f2
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920480"
---
# <a name="net-core-cli-overview"></a><span data-ttu-id="5a040-103">.NET Core CLI genel bakış</span><span class="sxs-lookup"><span data-stu-id="5a040-103">.NET Core CLI overview</span></span>

<span data-ttu-id="5a040-104">.NET Core komut satırı arabirimi (CLı), .NET Core uygulamaları geliştirmeye, oluşturmaya, çalıştırmaya ve yayımlamaya yönelik platformlar arası bir araç zinciridir.</span><span class="sxs-lookup"><span data-stu-id="5a040-104">The .NET Core command-line interface (CLI) is a cross-platform toolchain for developing, building, running, and publishing .NET Core applications.</span></span>

<span data-ttu-id="5a040-105">.NET Core CLI, [.NET Core SDK](../sdk.md)dahil edilir.</span><span class="sxs-lookup"><span data-stu-id="5a040-105">The .NET Core CLI is included with the [.NET Core SDK](../sdk.md).</span></span> <span data-ttu-id="5a040-106">.NET Core SDK nasıl yükleneceğini öğrenmek için bkz. [.NET Core SDK yüklemesi](../install/sdk.md).</span><span class="sxs-lookup"><span data-stu-id="5a040-106">To learn how to install the .NET Core SDK, see [Install the .NET Core SDK](../install/sdk.md).</span></span>

## <a name="cli-commands"></a><span data-ttu-id="5a040-107">CLı komutları</span><span class="sxs-lookup"><span data-stu-id="5a040-107">CLI commands</span></span>

<span data-ttu-id="5a040-108">Aşağıdaki komutlar varsayılan olarak yüklenir:</span><span class="sxs-lookup"><span data-stu-id="5a040-108">The following commands are installed by default:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="5a040-109">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="5a040-109">.NET Core 2.x</span></span>](#tab/netcore2x)

<span data-ttu-id="5a040-110">**Temel komutlar**</span><span class="sxs-lookup"><span data-stu-id="5a040-110">**Basic commands**</span></span>

- [<span data-ttu-id="5a040-111">new</span><span class="sxs-lookup"><span data-stu-id="5a040-111">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="5a040-112">restore</span><span class="sxs-lookup"><span data-stu-id="5a040-112">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="5a040-113">derlemeyi</span><span class="sxs-lookup"><span data-stu-id="5a040-113">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="5a040-114">yayınlamanız</span><span class="sxs-lookup"><span data-stu-id="5a040-114">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="5a040-115">çalışmaz</span><span class="sxs-lookup"><span data-stu-id="5a040-115">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="5a040-116">sınamanız</span><span class="sxs-lookup"><span data-stu-id="5a040-116">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="5a040-117">VSTest</span><span class="sxs-lookup"><span data-stu-id="5a040-117">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="5a040-118">pack</span><span class="sxs-lookup"><span data-stu-id="5a040-118">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="5a040-119">geçiremezsiniz</span><span class="sxs-lookup"><span data-stu-id="5a040-119">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="5a040-120">temizlenemedi</span><span class="sxs-lookup"><span data-stu-id="5a040-120">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="5a040-121">sln</span><span class="sxs-lookup"><span data-stu-id="5a040-121">sln</span></span>](dotnet-sln.md)
- [<span data-ttu-id="5a040-122">Yardım</span><span class="sxs-lookup"><span data-stu-id="5a040-122">help</span></span>](dotnet-help.md)
- [<span data-ttu-id="5a040-123">saklayabilir</span><span class="sxs-lookup"><span data-stu-id="5a040-123">store</span></span>](dotnet-store.md)

<span data-ttu-id="5a040-124">**Proje değiştirme komutları**</span><span class="sxs-lookup"><span data-stu-id="5a040-124">**Project modification commands**</span></span>

- [<span data-ttu-id="5a040-125">Paket ekle</span><span class="sxs-lookup"><span data-stu-id="5a040-125">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="5a040-126">Başvuru Ekle</span><span class="sxs-lookup"><span data-stu-id="5a040-126">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="5a040-127">paketi kaldır</span><span class="sxs-lookup"><span data-stu-id="5a040-127">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="5a040-128">başvuruyu kaldır</span><span class="sxs-lookup"><span data-stu-id="5a040-128">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="5a040-129">liste başvurusu</span><span class="sxs-lookup"><span data-stu-id="5a040-129">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="5a040-130">**Gelişmiş komutlar**</span><span class="sxs-lookup"><span data-stu-id="5a040-130">**Advanced commands**</span></span>

- [<span data-ttu-id="5a040-131">NuGet silme</span><span class="sxs-lookup"><span data-stu-id="5a040-131">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="5a040-132">NuGet Yereller</span><span class="sxs-lookup"><span data-stu-id="5a040-132">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="5a040-133">NuGet gönderim</span><span class="sxs-lookup"><span data-stu-id="5a040-133">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="5a040-134">MSBUILD</span><span class="sxs-lookup"><span data-stu-id="5a040-134">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="5a040-135">DotNet install betiği</span><span class="sxs-lookup"><span data-stu-id="5a040-135">dotnet install script</span></span>](dotnet-install-script.md)

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5a040-136">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="5a040-136">.NET Core 1.x</span></span>](#tab/netcore1x)

<span data-ttu-id="5a040-137">**Temel komutlar**</span><span class="sxs-lookup"><span data-stu-id="5a040-137">**Basic commands**</span></span>

- [<span data-ttu-id="5a040-138">new</span><span class="sxs-lookup"><span data-stu-id="5a040-138">new</span></span>](dotnet-new.md)
- [<span data-ttu-id="5a040-139">restore</span><span class="sxs-lookup"><span data-stu-id="5a040-139">restore</span></span>](dotnet-restore.md)
- [<span data-ttu-id="5a040-140">derlemeyi</span><span class="sxs-lookup"><span data-stu-id="5a040-140">build</span></span>](dotnet-build.md)
- [<span data-ttu-id="5a040-141">yayınlamanız</span><span class="sxs-lookup"><span data-stu-id="5a040-141">publish</span></span>](dotnet-publish.md)
- [<span data-ttu-id="5a040-142">çalışmaz</span><span class="sxs-lookup"><span data-stu-id="5a040-142">run</span></span>](dotnet-run.md)
- [<span data-ttu-id="5a040-143">sınamanız</span><span class="sxs-lookup"><span data-stu-id="5a040-143">test</span></span>](dotnet-test.md)
- [<span data-ttu-id="5a040-144">VSTest</span><span class="sxs-lookup"><span data-stu-id="5a040-144">vstest</span></span>](dotnet-vstest.md)
- [<span data-ttu-id="5a040-145">pack</span><span class="sxs-lookup"><span data-stu-id="5a040-145">pack</span></span>](dotnet-pack.md)
- [<span data-ttu-id="5a040-146">geçiremezsiniz</span><span class="sxs-lookup"><span data-stu-id="5a040-146">migrate</span></span>](dotnet-migrate.md)
- [<span data-ttu-id="5a040-147">temizlenemedi</span><span class="sxs-lookup"><span data-stu-id="5a040-147">clean</span></span>](dotnet-clean.md)
- [<span data-ttu-id="5a040-148">sln</span><span class="sxs-lookup"><span data-stu-id="5a040-148">sln</span></span>](dotnet-sln.md)

<span data-ttu-id="5a040-149">**Proje değiştirme komutları**</span><span class="sxs-lookup"><span data-stu-id="5a040-149">**Project modification commands**</span></span>

- [<span data-ttu-id="5a040-150">Paket ekle</span><span class="sxs-lookup"><span data-stu-id="5a040-150">add package</span></span>](dotnet-add-package.md)
- [<span data-ttu-id="5a040-151">Başvuru Ekle</span><span class="sxs-lookup"><span data-stu-id="5a040-151">add reference</span></span>](dotnet-add-reference.md)
- [<span data-ttu-id="5a040-152">paketi kaldır</span><span class="sxs-lookup"><span data-stu-id="5a040-152">remove package</span></span>](dotnet-remove-package.md)
- [<span data-ttu-id="5a040-153">başvuruyu kaldır</span><span class="sxs-lookup"><span data-stu-id="5a040-153">remove reference</span></span>](dotnet-remove-reference.md)
- [<span data-ttu-id="5a040-154">liste başvurusu</span><span class="sxs-lookup"><span data-stu-id="5a040-154">list reference</span></span>](dotnet-list-reference.md)

<span data-ttu-id="5a040-155">**Gelişmiş komutlar**</span><span class="sxs-lookup"><span data-stu-id="5a040-155">**Advanced commands**</span></span>

- [<span data-ttu-id="5a040-156">NuGet silme</span><span class="sxs-lookup"><span data-stu-id="5a040-156">nuget delete</span></span>](dotnet-nuget-delete.md)
- [<span data-ttu-id="5a040-157">NuGet Yereller</span><span class="sxs-lookup"><span data-stu-id="5a040-157">nuget locals</span></span>](dotnet-nuget-locals.md)
- [<span data-ttu-id="5a040-158">NuGet gönderim</span><span class="sxs-lookup"><span data-stu-id="5a040-158">nuget push</span></span>](dotnet-nuget-push.md)
- [<span data-ttu-id="5a040-159">MSBUILD</span><span class="sxs-lookup"><span data-stu-id="5a040-159">msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="5a040-160">DotNet install betiği</span><span class="sxs-lookup"><span data-stu-id="5a040-160">dotnet install script</span></span>](dotnet-install-script.md)

---

<span data-ttu-id="5a040-161">CLı, projeleriniz için ek araçlar belirtmenize olanak tanıyan bir genişletilebilirlik modeli benimsemektedir.</span><span class="sxs-lookup"><span data-stu-id="5a040-161">The CLI adopts an extensibility model that allows you to specify additional tools for your projects.</span></span> <span data-ttu-id="5a040-162">Daha fazla bilgi için [.NET Core CLI genişletilebilirlik modeli](extensibility.md) konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="5a040-162">For more information, see the [.NET Core CLI extensibility model](extensibility.md) topic.</span></span>

## <a name="command-structure"></a><span data-ttu-id="5a040-163">Komut yapısı</span><span class="sxs-lookup"><span data-stu-id="5a040-163">Command structure</span></span>

<span data-ttu-id="5a040-164">CLı komut yapısı, [sürücüden ("DotNet")](#driver), [komuttan](#command)ve muhtemelen komut [bağımsız değişkenlerinden](#arguments) ve [seçeneklerden](#options)oluşur.</span><span class="sxs-lookup"><span data-stu-id="5a040-164">CLI command structure consists of [the driver ("dotnet")](#driver), [the command](#command), and possibly command [arguments](#arguments) and [options](#options).</span></span> <span data-ttu-id="5a040-165">Bu kalıbı, yeni bir konsol uygulaması oluşturma ve aşağıdaki komutlar *my_app*adlı bir dizinden yürütüldüğünde gösterildiği gibi komut satırından çalıştırma gıbı birçok CLI işlemi içinde görürsünüz:</span><span class="sxs-lookup"><span data-stu-id="5a040-165">You see this pattern in most CLI operations, such as creating a new console app and running it from the command line as the following commands show when executed from a directory named *my_app*:</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="5a040-166">.NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="5a040-166">.NET Core 2.x</span></span>](#tab/netcore2x)

```dotnetcli
dotnet new console
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="5a040-167">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="5a040-167">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet new console
dotnet restore
dotnet build --output /build_output
dotnet /build_output/my_app.dll
```

---

### <a name="driver"></a><span data-ttu-id="5a040-168">Sürücü</span><span class="sxs-lookup"><span data-stu-id="5a040-168">Driver</span></span>

<span data-ttu-id="5a040-169">Sürücü [DotNet](dotnet.md) olarak adlandırılır ve [çerçeveye bağlı bir uygulama](../deploying/index.md) çalıştırarak ya da bir komut yürüten iki sorumluluklara sahiptir.</span><span class="sxs-lookup"><span data-stu-id="5a040-169">The driver is named [dotnet](dotnet.md) and has two responsibilities, either running a [framework-dependent app](../deploying/index.md) or executing a command.</span></span> 

<span data-ttu-id="5a040-170">Çerçeveye bağımlı bir uygulama çalıştırmak için, uygulamayı sürücüden sonra belirtin, örneğin, `dotnet /path/to/my_app.dll`.</span><span class="sxs-lookup"><span data-stu-id="5a040-170">To run a framework-dependent app, specify the app after the driver, for example, `dotnet /path/to/my_app.dll`.</span></span> <span data-ttu-id="5a040-171">Uygulamanın DLL 'sinin bulunduğu klasörden komutu yürütürken `dotnet my_app.dll`yürütmek yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="5a040-171">When executing the command from the folder where the app's DLL resides, simply execute `dotnet my_app.dll`.</span></span> <span data-ttu-id="5a040-172">.NET Core çalışma zamanının belirli bir sürümünü kullanmak istiyorsanız, `--fx-version <VERSION>` seçeneğini kullanın ( [DotNet komut](dotnet.md) başvurusuna bakın).</span><span class="sxs-lookup"><span data-stu-id="5a040-172">If you want to use a specific version of the .NET Core Runtime, use the `--fx-version <VERSION>` option (see the [dotnet command](dotnet.md) reference).</span></span>

<span data-ttu-id="5a040-173">Sürücüye bir komut sağlarsanız, `dotnet.exe` CLı komutu yürütme işlemini başlatır.</span><span class="sxs-lookup"><span data-stu-id="5a040-173">When you supply a command to the driver, `dotnet.exe` starts the CLI command execution process.</span></span> <span data-ttu-id="5a040-174">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="5a040-174">For example:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="5a040-175">İlk olarak, sürücü kullanılacak SDK sürümünü belirler.</span><span class="sxs-lookup"><span data-stu-id="5a040-175">First, the driver determines the version of the SDK to use.</span></span> <span data-ttu-id="5a040-176">[' Global. json '](global-json.md)yoksa SDK 'nın kullanılabilir en son sürümü kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5a040-176">If there is no ['global.json'](global-json.md), the latest version of the SDK available is used.</span></span> <span data-ttu-id="5a040-177">Bu, makinede en son nelerin olduğuna bağlı olarak önizleme veya kararlı bir sürüm olabilir.</span><span class="sxs-lookup"><span data-stu-id="5a040-177">This might be either a preview or stable version, depending on what is latest on the machine.</span></span>  <span data-ttu-id="5a040-178">SDK sürümü belirlendikten sonra, komutunu yürütür.</span><span class="sxs-lookup"><span data-stu-id="5a040-178">Once the SDK version is determined, it executes the command.</span></span>

### <a name="command"></a><span data-ttu-id="5a040-179">Komut</span><span class="sxs-lookup"><span data-stu-id="5a040-179">Command</span></span>

<span data-ttu-id="5a040-180">Komut bir eylem gerçekleştirir.</span><span class="sxs-lookup"><span data-stu-id="5a040-180">The command performs an action.</span></span> <span data-ttu-id="5a040-181">Örneğin, `dotnet build` derleme kodu.</span><span class="sxs-lookup"><span data-stu-id="5a040-181">For example, `dotnet build` builds code.</span></span> <span data-ttu-id="5a040-182">`dotnet publish` kodu yayınlar.</span><span class="sxs-lookup"><span data-stu-id="5a040-182">`dotnet publish` publishes code.</span></span> <span data-ttu-id="5a040-183">Komutlar bir `dotnet {command}` kuralı kullanılarak konsol uygulaması olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="5a040-183">The commands are implemented as a console application using a `dotnet {command}` convention.</span></span>

### <a name="arguments"></a><span data-ttu-id="5a040-184">Arguments</span><span class="sxs-lookup"><span data-stu-id="5a040-184">Arguments</span></span>

<span data-ttu-id="5a040-185">Komut satırında geçirdiğiniz bağımsız değişkenler çağrılan komutun bağımsız değişkenlerdir.</span><span class="sxs-lookup"><span data-stu-id="5a040-185">The arguments you pass on the command line are the arguments to the command invoked.</span></span> <span data-ttu-id="5a040-186">Örneğin, `dotnet publish my_app.csproj`yürüttüğünüzde, `my_app.csproj` bağımsız değişkeni yayımlanacak projeyi belirtir ve `publish` komutuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5a040-186">For example when you execute `dotnet publish my_app.csproj`, the `my_app.csproj` argument indicates the project to publish and is passed to the `publish` command.</span></span>

### <a name="options"></a><span data-ttu-id="5a040-187">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5a040-187">Options</span></span>

<span data-ttu-id="5a040-188">Komut satırında geçirdiğiniz seçenekler çağrılan komuta yönelik seçeneklerdir.</span><span class="sxs-lookup"><span data-stu-id="5a040-188">The options you pass on the command line are the options to the command invoked.</span></span> <span data-ttu-id="5a040-189">Örneğin `dotnet publish --output /build_output`yürüttüğünüzde, `--output` seçeneği ve değeri `publish` komutuna geçirilir.</span><span class="sxs-lookup"><span data-stu-id="5a040-189">For example when you execute `dotnet publish --output /build_output`, the `--output` option and its value are passed to the `publish` command.</span></span>

## <a name="migration-from-projectjson"></a><span data-ttu-id="5a040-190">Project. JSON 'dan geçiş</span><span class="sxs-lookup"><span data-stu-id="5a040-190">Migration from project.json</span></span>

<span data-ttu-id="5a040-191">*Project. JSON*tabanlı projeler oluşturmak için Preview 2 araçları 'nı kullandıysanız, sürüm araçları ile kullanmak üzere projenizi MSBuild/ *. csproj* 'a geçirme hakkında bilgi edinmek için [DotNet geçiş](dotnet-migrate.md) konusuna başvurun.</span><span class="sxs-lookup"><span data-stu-id="5a040-191">If you used Preview 2 tooling to produce *project.json*-based projects, consult the [dotnet migrate](dotnet-migrate.md) topic for information on migrating your project to MSBuild/*.csproj* for use with release tooling.</span></span> <span data-ttu-id="5a040-192">Preview 2 araçları 'nın yayınlanmasından önce oluşturulan .NET Core projeleri için, [DNX 'ten .NET Core CLI (Project. JSON) ' den geçiş yapma bölümündeki kılavuzdan](../migration/from-dnx.md) sonra projeyi el ile güncelleştirin ve `dotnet migrate` kullanın ya da projelerinizi doğrudan yükseltin.</span><span class="sxs-lookup"><span data-stu-id="5a040-192">For .NET Core projects created prior to the release of Preview 2 tooling, either manually update the project following the guidance in [Migrating from DNX to .NET Core CLI (project.json)](../migration/from-dnx.md) and then use `dotnet migrate` or directly upgrade your projects.</span></span>

## <a name="see-also"></a><span data-ttu-id="5a040-193">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a040-193">See also</span></span>

- [<span data-ttu-id="5a040-194">DotNet/SDK GitHub deposu</span><span class="sxs-lookup"><span data-stu-id="5a040-194">dotnet/sdk GitHub repository</span></span>](https://github.com/dotnet/sdk/)
- [<span data-ttu-id="5a040-195">.NET Core yükleme kılavuzu</span><span class="sxs-lookup"><span data-stu-id="5a040-195">.NET Core installation guide</span></span>](https://aka.ms/dotnetcoregs)
