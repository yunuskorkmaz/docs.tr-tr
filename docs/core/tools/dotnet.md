---
title: DotNet command - .NET Core CLI
description: Dotnet komutu (.NET Core CLI araçlarını genel sürücüsü) ve kullanımı hakkında bilgi edinin.
author: mairaw
ms.author: mairaw
ms.date: 03/20/2018
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2d22124cb613152df402046541650f3262e7e202
ms.sourcegitcommit: 6f967c86dde55472440f0c8669b0e910ee3c53ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="dotnet-command"></a><span data-ttu-id="d55aa-103">DotNet komutu</span><span class="sxs-lookup"><span data-stu-id="d55aa-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d55aa-104">Ad</span><span class="sxs-lookup"><span data-stu-id="d55aa-104">Name</span></span>

<span data-ttu-id="d55aa-105">`dotnet` -Komut satırı komutlarını çalıştırmak için genel sürücüsü.</span><span class="sxs-lookup"><span data-stu-id="d55aa-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d55aa-106">Özet</span><span class="sxs-lookup"><span data-stu-id="d55aa-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d55aa-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="d55aa-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d55aa-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d55aa-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="d55aa-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d55aa-109">Description</span></span>

<span data-ttu-id="d55aa-110">`dotnet` Komut satırı arabirimi (CLI) zincirinin için genel bir sürücüsüdür.</span><span class="sxs-lookup"><span data-stu-id="d55aa-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="d55aa-111">Kendi kendine çağrılan kısa kullanım yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d55aa-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="d55aa-112">Her belirli bir özellik, bir komut olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="d55aa-113">Bu özelliği kullanmak için komut sonra belirtilen `dotnet`, gibi [ `dotnet build` ](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="d55aa-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="d55aa-114">Tüm komut aşağıdaki bağımsız değişkenleri, kendi bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="d55aa-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="d55aa-115">Yalnızca bir kez `dotnet` kendi başına bir komut çalıştırmaktır olarak kullanılan [framework bağımlı uygulamaları](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d55aa-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="d55aa-116">Bir uygulama DLL belirtin sonra `dotnet` uygulamasını çalıştırmak için fiili (örneğin, `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="d55aa-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="d55aa-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d55aa-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d55aa-118">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="d55aa-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additional-deps <PATH>`

<span data-ttu-id="d55aa-119">Ek yoluna *deps.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="d55aa-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="d55aa-120">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="d55aa-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="d55aa-121">Tanılama çıktıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="d55aa-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="d55aa-122">Uygulamayı çalıştırmak için kullanılacak yüklü .NET çekirdeği çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="d55aa-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="d55aa-123">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-123">Prints out a short help for the command.</span></span> <span data-ttu-id="d55aa-124">İle kullanıyorsanız, `dotnet`, ayrıca kullanılabilir komutların listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="d55aa-125">CLI araçları ve geçerli işletim sistemi gibi ortam hakkında ayrıntılı bilgi yazdırır, sürüm ve diğer bilgiler için SHA uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d55aa-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="d55aa-126">Dökümünü hiçbir aday paylaşılan Framework'te iletin.</span><span class="sxs-lookup"><span data-stu-id="d55aa-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d55aa-127">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d55aa-127">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d55aa-128">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d55aa-128">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d55aa-129">Her komut desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="d55aa-129">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="d55aa-130">Kullanımdaki .NET Core SDK sürümü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-130">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d55aa-131">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d55aa-131">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="d55aa-132">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="d55aa-132">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="d55aa-133">Tanılama çıktıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="d55aa-133">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="d55aa-134">Uygulamayı çalıştırmak için kullanılacak yüklü .NET çekirdeği çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="d55aa-134">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="d55aa-135">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-135">Prints out a short help for the command.</span></span> <span data-ttu-id="d55aa-136">İle kullanıyorsanız, `dotnet`, ayrıca kullanılabilir komutların listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-136">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="d55aa-137">CLI araçları ve geçerli işletim sistemi gibi ortam hakkında ayrıntılı bilgi yazdırır, sürüm ve diğer bilgiler için SHA uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d55aa-137">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d55aa-138">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d55aa-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d55aa-139">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d55aa-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d55aa-140">Her komut desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="d55aa-140">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="d55aa-141">Kullanımdaki .NET Core SDK sürümü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-141">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="d55aa-142">DotNet komutları</span><span class="sxs-lookup"><span data-stu-id="d55aa-142">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="d55aa-143">Genel</span><span class="sxs-lookup"><span data-stu-id="d55aa-143">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d55aa-144">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="d55aa-144">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="d55aa-145">Komut</span><span class="sxs-lookup"><span data-stu-id="d55aa-145">Command</span></span>                             | <span data-ttu-id="d55aa-146">İşlev</span><span class="sxs-lookup"><span data-stu-id="d55aa-146">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d55aa-147">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d55aa-147">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="d55aa-148">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d55aa-148">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d55aa-149">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d55aa-149">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="d55aa-150">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-150">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="d55aa-151">dotnet help</span><span class="sxs-lookup"><span data-stu-id="d55aa-151">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="d55aa-152">Komutu için çevrimiçi belgeleri ayrıntılı gösterir.</span><span class="sxs-lookup"><span data-stu-id="d55aa-152">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="d55aa-153">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d55aa-153">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="d55aa-154">Geçerli bir önizleme 2 projeyi .NET Core SDK 1.0 projeye geçirir.</span><span class="sxs-lookup"><span data-stu-id="d55aa-154">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d55aa-155">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d55aa-155">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="d55aa-156">MSBuild komut satırında erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d55aa-156">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d55aa-157">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d55aa-157">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="d55aa-158">Bir C# veya belirli bir şablon için F # projesine başlatır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-158">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d55aa-159">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d55aa-159">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="d55aa-160">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d55aa-160">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d55aa-161">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d55aa-161">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="d55aa-162">.NET framework bağımlı veya kendi içinde bulunan uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="d55aa-162">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d55aa-163">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d55aa-163">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="d55aa-164">Belirli bir uygulamayla ilgili bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="d55aa-164">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d55aa-165">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d55aa-165">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="d55aa-166">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-166">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d55aa-167">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d55aa-167">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="d55aa-168">Eklemek için seçenekler kaldırın ve bir çözüm dosyasında projelerini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="d55aa-168">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d55aa-169">dotnet store</span><span class="sxs-lookup"><span data-stu-id="d55aa-169">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="d55aa-170">Derlemeleri çalışma zamanı paketi deposunda saklar.</span><span class="sxs-lookup"><span data-stu-id="d55aa-170">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="d55aa-171">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d55aa-171">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="d55aa-172">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-172">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d55aa-173">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d55aa-173">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="d55aa-174">Komut</span><span class="sxs-lookup"><span data-stu-id="d55aa-174">Command</span></span>                             | <span data-ttu-id="d55aa-175">İşlev</span><span class="sxs-lookup"><span data-stu-id="d55aa-175">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="d55aa-176">dotnet build</span><span class="sxs-lookup"><span data-stu-id="d55aa-176">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="d55aa-177">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d55aa-177">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="d55aa-178">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="d55aa-178">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="d55aa-179">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-179">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="d55aa-180">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="d55aa-180">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="d55aa-181">Geçerli bir önizleme 2 projeyi .NET Core SDK 1.0 projeye geçirir.</span><span class="sxs-lookup"><span data-stu-id="d55aa-181">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="d55aa-182">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="d55aa-182">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="d55aa-183">MSBuild komut satırında erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d55aa-183">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="d55aa-184">dotnet new</span><span class="sxs-lookup"><span data-stu-id="d55aa-184">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="d55aa-185">Bir C# veya belirli bir şablon için F # projesine başlatır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-185">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="d55aa-186">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="d55aa-186">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="d55aa-187">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d55aa-187">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="d55aa-188">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d55aa-188">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="d55aa-189">.NET framework bağımlı veya kendi içinde bulunan uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="d55aa-189">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="d55aa-190">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d55aa-190">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="d55aa-191">Belirli bir uygulamayla ilgili bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="d55aa-191">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="d55aa-192">dotnet run</span><span class="sxs-lookup"><span data-stu-id="d55aa-192">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="d55aa-193">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-193">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="d55aa-194">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="d55aa-194">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="d55aa-195">Eklemek için seçenekler kaldırın ve bir çözüm dosyasında projelerini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="d55aa-195">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="d55aa-196">dotnet test</span><span class="sxs-lookup"><span data-stu-id="d55aa-196">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="d55aa-197">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="d55aa-197">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="d55aa-198">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="d55aa-198">Project references</span></span>

<span data-ttu-id="d55aa-199">Komut</span><span class="sxs-lookup"><span data-stu-id="d55aa-199">Command</span></span> | <span data-ttu-id="d55aa-200">İşlev</span><span class="sxs-lookup"><span data-stu-id="d55aa-200">Function</span></span>
--- | ---
[<span data-ttu-id="d55aa-201">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="d55aa-201">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="d55aa-202">Proje başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d55aa-202">Add a project reference.</span></span>
[<span data-ttu-id="d55aa-203">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="d55aa-203">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="d55aa-204">Proje başvuruları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="d55aa-204">List project references.</span></span>
[<span data-ttu-id="d55aa-205">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="d55aa-205">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="d55aa-206">Proje başvurusu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d55aa-206">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="d55aa-207">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="d55aa-207">NuGet packages</span></span>

<span data-ttu-id="d55aa-208">Komut</span><span class="sxs-lookup"><span data-stu-id="d55aa-208">Command</span></span> | <span data-ttu-id="d55aa-209">İşlev</span><span class="sxs-lookup"><span data-stu-id="d55aa-209">Function</span></span>
--- | ---
[<span data-ttu-id="d55aa-210">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="d55aa-210">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="d55aa-211">NuGet paketini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="d55aa-211">Add a NuGet package.</span></span>
[<span data-ttu-id="d55aa-212">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="d55aa-212">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="d55aa-213">Bir NuGet paketi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="d55aa-213">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="d55aa-214">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="d55aa-214">NuGet commands</span></span>

<span data-ttu-id="d55aa-215">Komut</span><span class="sxs-lookup"><span data-stu-id="d55aa-215">Command</span></span> | <span data-ttu-id="d55aa-216">İşlev</span><span class="sxs-lookup"><span data-stu-id="d55aa-216">Function</span></span>
--- | ---
[<span data-ttu-id="d55aa-217">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="d55aa-217">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="d55aa-218">Sunucudan paket unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="d55aa-218">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="d55aa-219">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="d55aa-219">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="d55aa-220">Temizler veya http isteği önbelleği, geçici önbelleği veya makine genelinde genel paketler klasörü gibi yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="d55aa-220">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="d55aa-221">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="d55aa-221">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="d55aa-222">Sunucuya bir paket gönderir ve onu yayımlar.</span><span class="sxs-lookup"><span data-stu-id="d55aa-222">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="d55aa-223">Örnekler</span><span class="sxs-lookup"><span data-stu-id="d55aa-223">Examples</span></span>

<span data-ttu-id="d55aa-224">Derlenmiş ve çalıştıran bir örnek .NET Core konsol uygulaması başlatılamadı:</span><span class="sxs-lookup"><span data-stu-id="d55aa-224">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="d55aa-225">Belirli bir uygulamayla ilgili bağımlılıkları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="d55aa-225">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="d55aa-226">Proje ve bağımlılıklarını belirli bir dizinde oluşturun:</span><span class="sxs-lookup"><span data-stu-id="d55aa-226">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="d55aa-227">Adlı framework bağımlı uygulamayı çalıştırma `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="d55aa-227">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="d55aa-228">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="d55aa-228">Environment variables</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d55aa-229">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="d55aa-229">.NET Core 2.x</span></span>](#tab/netcore2x)

`DOTNET_PACKAGES`

<span data-ttu-id="d55aa-230">Birincil paketi önbelleği.</span><span class="sxs-lookup"><span data-stu-id="d55aa-230">The primary package cache.</span></span> <span data-ttu-id="d55aa-231">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows.</span><span class="sxs-lookup"><span data-stu-id="d55aa-231">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="d55aa-232">Çalışma zamanı yüklerken paylaşılan ana bilgisayar tarafından kullanılacak hizmet dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d55aa-232">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="d55aa-233">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d55aa-233">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d55aa-234">Kümesine `true` telemetri özelliğini çevirin için (değerleri `true`, `1`, veya `yes` kabul) Aksi takdirde ayarlanmış `false` katılımı telemetri özellikleri için (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="d55aa-234">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d55aa-235">Ayarlanmadı, Varsayılanları olup olmadığını `false`, ve telemetri özellik etkindir.</span><span class="sxs-lookup"><span data-stu-id="d55aa-235">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="d55aa-236">.NET çekirdeği çalışma zamanı, paylaşılan framework veya SDK olmadığını çözümlenmiş genel konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d55aa-236">Specifies whether .NET Core runtime, shared framework or SDK are resolved from the global location.</span></span> <span data-ttu-id="d55aa-237">Ayarlanmazsa, varsayılan olarak, `true`.</span><span class="sxs-lookup"><span data-stu-id="d55aa-237">If not set, it defaults to `true`.</span></span> <span data-ttu-id="d55aa-238">Kümesine `false` değil genel konumdan çözmek ve .NET çekirdeği yüklemeleri buluncaya (değerleri `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="d55aa-238">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="d55aa-239">Birden çok düzeyli arama hakkında daha fazla bilgi için bkz: [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="d55aa-239">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d55aa-240">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d55aa-240">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="d55aa-241">Birincil paketi önbelleği.</span><span class="sxs-lookup"><span data-stu-id="d55aa-241">The primary package cache.</span></span> <span data-ttu-id="d55aa-242">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows.</span><span class="sxs-lookup"><span data-stu-id="d55aa-242">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="d55aa-243">Çalışma zamanı yüklerken paylaşılan ana bilgisayar tarafından kullanılacak hizmet dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d55aa-243">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="d55aa-244">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d55aa-244">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="d55aa-245">Kümesine `true` telemetri özelliğini çevirin için (değerleri `true`, `1`, veya `yes` kabul) Aksi takdirde ayarlanmış `false` katılımı telemetri özellikleri için (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="d55aa-245">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="d55aa-246">Ayarlanmadı, Varsayılanları olup olmadığını `false`, ve telemetri özellik etkindir.</span><span class="sxs-lookup"><span data-stu-id="d55aa-246">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>

---
