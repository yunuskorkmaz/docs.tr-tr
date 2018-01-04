---
title: DotNet command - .NET Core CLI
description: "Dotnet komutu (.NET Core CLI araçlarını genel sürücüsü) ve kullanımı hakkında bilgi edinin."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 6db2bb6003e630aab900222eb20e33af287cf9c5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-command"></a><span data-ttu-id="344f3-103">DotNet komutu</span><span class="sxs-lookup"><span data-stu-id="344f3-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="344f3-104">Ad</span><span class="sxs-lookup"><span data-stu-id="344f3-104">Name</span></span>

<span data-ttu-id="344f3-105">`dotnet`-Komut satırı komutlarını çalıştırmak için genel sürücüsü.</span><span class="sxs-lookup"><span data-stu-id="344f3-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="344f3-106">Özet</span><span class="sxs-lookup"><span data-stu-id="344f3-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="344f3-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="344f3-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbose] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="344f3-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="344f3-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [-v|--verbose] [--version]
```
---

## <a name="description"></a><span data-ttu-id="344f3-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="344f3-109">Description</span></span>

<span data-ttu-id="344f3-110">`dotnet`Komut satırı arabirimi (CLI) zincirinin için genel bir sürücüsüdür.</span><span class="sxs-lookup"><span data-stu-id="344f3-110">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="344f3-111">Kendi kendine çağrılan kısa kullanım yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="344f3-111">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="344f3-112">Her belirli bir özellik, bir komut olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="344f3-112">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="344f3-113">Bu özelliği kullanmak için komut sonra belirtilen `dotnet`, gibi [ `dotnet build` ](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="344f3-113">In order to use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="344f3-114">Tüm komut aşağıdaki bağımsız değişkenleri, kendi bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="344f3-114">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="344f3-115">Yalnızca bir kez `dotnet` kendi başına bir komut çalıştırmaktır olarak kullanılan [framework bağımlı uygulamaları](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="344f3-115">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="344f3-116">Bir uygulama DLL belirtin sonra `dotnet` uygulamasını çalıştırmak için fiili (örneğin, `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="344f3-116">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="344f3-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="344f3-117">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="344f3-118">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="344f3-118">.NET Core 2.x</span></span>](#tab/netcore2x)

`--additionaldeps <PATH>`

<span data-ttu-id="344f3-119">Ek yoluna *deps.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="344f3-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="344f3-120">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="344f3-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="344f3-121">Tanılama çıktıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="344f3-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="344f3-122">Uygulamayı çalıştırmak için kullanılacak yüklü .NET çekirdeği çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="344f3-122">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="344f3-123">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="344f3-123">Prints out a short help for the command.</span></span> <span data-ttu-id="344f3-124">İle kullanıyorsanız, `dotnet`, ayrıca kullanılabilir komutların listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="344f3-124">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="344f3-125">CLI araçları ve geçerli işletim sistemi gibi ortam hakkında ayrıntılı bilgi yazdırır, sürüm ve diğer bilgiler için SHA uygulayın.</span><span class="sxs-lookup"><span data-stu-id="344f3-125">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="344f3-126">Dökümünü hiçbir aday paylaşılan Framework'te iletin.</span><span class="sxs-lookup"><span data-stu-id="344f3-126">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbose`

<span data-ttu-id="344f3-127">Ayrıntılı çıktı sağlar.</span><span class="sxs-lookup"><span data-stu-id="344f3-127">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="344f3-128">Kullanımdaki .NET Core SDK sürümü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="344f3-128">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="344f3-129">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="344f3-129">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="344f3-130">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="344f3-130">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="344f3-131">Tanılama çıktıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="344f3-131">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="344f3-132">Uygulamayı çalıştırmak için kullanılacak yüklü .NET çekirdeği çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="344f3-132">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="344f3-133">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="344f3-133">Prints out a short help for the command.</span></span> <span data-ttu-id="344f3-134">İle kullanıyorsanız, `dotnet`, ayrıca kullanılabilir komutların listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="344f3-134">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="344f3-135">CLI araçları ve geçerli işletim sistemi gibi ortam hakkında ayrıntılı bilgi yazdırır, sürüm ve diğer bilgiler için SHA uygulayın.</span><span class="sxs-lookup"><span data-stu-id="344f3-135">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbose`

<span data-ttu-id="344f3-136">Ayrıntılı çıktı sağlar.</span><span class="sxs-lookup"><span data-stu-id="344f3-136">Enables verbose output.</span></span>

`--version`

<span data-ttu-id="344f3-137">Kullanımdaki .NET Core SDK sürümü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="344f3-137">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="344f3-138">DotNet komutları</span><span class="sxs-lookup"><span data-stu-id="344f3-138">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="344f3-139">Genel</span><span class="sxs-lookup"><span data-stu-id="344f3-139">General</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="344f3-140">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="344f3-140">.NET Core 2.x</span></span>](#tab/netcore2x)

| <span data-ttu-id="344f3-141">Komut</span><span class="sxs-lookup"><span data-stu-id="344f3-141">Command</span></span>                             | <span data-ttu-id="344f3-142">İşlev</span><span class="sxs-lookup"><span data-stu-id="344f3-142">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="344f3-143">dotnet build</span><span class="sxs-lookup"><span data-stu-id="344f3-143">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="344f3-144">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="344f3-144">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="344f3-145">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="344f3-145">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="344f3-146">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="344f3-146">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="344f3-147">dotnet help</span><span class="sxs-lookup"><span data-stu-id="344f3-147">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="344f3-148">Komutu için çevrimiçi belgeleri ayrıntılı gösterir.</span><span class="sxs-lookup"><span data-stu-id="344f3-148">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="344f3-149">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="344f3-149">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="344f3-150">Geçerli bir önizleme 2 projeyi .NET Core SDK 1.0 projeye geçirir.</span><span class="sxs-lookup"><span data-stu-id="344f3-150">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="344f3-151">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="344f3-151">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="344f3-152">MSBuild komut satırında erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="344f3-152">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="344f3-153">dotnet new</span><span class="sxs-lookup"><span data-stu-id="344f3-153">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="344f3-154">Bir C# veya belirli bir şablon için F # projesine başlatır.</span><span class="sxs-lookup"><span data-stu-id="344f3-154">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="344f3-155">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="344f3-155">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="344f3-156">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="344f3-156">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="344f3-157">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="344f3-157">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="344f3-158">.NET framework bağımlı veya kendi içinde bulunan uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="344f3-158">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="344f3-159">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="344f3-159">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="344f3-160">Belirli bir uygulamayla ilgili bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="344f3-160">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="344f3-161">dotnet run</span><span class="sxs-lookup"><span data-stu-id="344f3-161">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="344f3-162">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="344f3-162">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="344f3-163">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="344f3-163">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="344f3-164">Eklemek için seçenekler kaldırın ve bir çözüm dosyasında projelerini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="344f3-164">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="344f3-165">dotnet store</span><span class="sxs-lookup"><span data-stu-id="344f3-165">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="344f3-166">Derlemeleri çalışma zamanı paketi deposunda saklar.</span><span class="sxs-lookup"><span data-stu-id="344f3-166">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="344f3-167">dotnet test</span><span class="sxs-lookup"><span data-stu-id="344f3-167">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="344f3-168">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="344f3-168">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="344f3-169">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="344f3-169">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="344f3-170">Komut</span><span class="sxs-lookup"><span data-stu-id="344f3-170">Command</span></span>                             | <span data-ttu-id="344f3-171">İşlev</span><span class="sxs-lookup"><span data-stu-id="344f3-171">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="344f3-172">dotnet build</span><span class="sxs-lookup"><span data-stu-id="344f3-172">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="344f3-173">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="344f3-173">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="344f3-174">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="344f3-174">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="344f3-175">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="344f3-175">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="344f3-176">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="344f3-176">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="344f3-177">Geçerli bir önizleme 2 projeyi .NET Core SDK 1.0 projeye geçirir.</span><span class="sxs-lookup"><span data-stu-id="344f3-177">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="344f3-178">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="344f3-178">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="344f3-179">MSBuild komut satırında erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="344f3-179">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="344f3-180">dotnet new</span><span class="sxs-lookup"><span data-stu-id="344f3-180">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="344f3-181">Bir C# veya belirli bir şablon için F # projesine başlatır.</span><span class="sxs-lookup"><span data-stu-id="344f3-181">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="344f3-182">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="344f3-182">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="344f3-183">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="344f3-183">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="344f3-184">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="344f3-184">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="344f3-185">.NET framework bağımlı veya kendi içinde bulunan uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="344f3-185">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="344f3-186">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="344f3-186">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="344f3-187">Belirli bir uygulamayla ilgili bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="344f3-187">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="344f3-188">dotnet run</span><span class="sxs-lookup"><span data-stu-id="344f3-188">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="344f3-189">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="344f3-189">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="344f3-190">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="344f3-190">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="344f3-191">Eklemek için seçenekler kaldırın ve bir çözüm dosyasında projelerini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="344f3-191">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="344f3-192">dotnet test</span><span class="sxs-lookup"><span data-stu-id="344f3-192">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="344f3-193">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="344f3-193">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="344f3-194">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="344f3-194">Project references</span></span>

<span data-ttu-id="344f3-195">Komut</span><span class="sxs-lookup"><span data-stu-id="344f3-195">Command</span></span> | <span data-ttu-id="344f3-196">İşlev</span><span class="sxs-lookup"><span data-stu-id="344f3-196">Function</span></span>
--- | ---
[<span data-ttu-id="344f3-197">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="344f3-197">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="344f3-198">Proje başvurusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="344f3-198">Add a project reference.</span></span>
[<span data-ttu-id="344f3-199">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="344f3-199">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="344f3-200">Proje başvuruları listeleyin.</span><span class="sxs-lookup"><span data-stu-id="344f3-200">List project references.</span></span>
[<span data-ttu-id="344f3-201">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="344f3-201">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="344f3-202">Proje başvurusu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="344f3-202">Remove a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="344f3-203">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="344f3-203">NuGet packages</span></span>

<span data-ttu-id="344f3-204">Komut</span><span class="sxs-lookup"><span data-stu-id="344f3-204">Command</span></span> | <span data-ttu-id="344f3-205">İşlev</span><span class="sxs-lookup"><span data-stu-id="344f3-205">Function</span></span>
--- | ---
[<span data-ttu-id="344f3-206">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="344f3-206">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="344f3-207">NuGet paketini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="344f3-207">Add a NuGet package.</span></span>
[<span data-ttu-id="344f3-208">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="344f3-208">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="344f3-209">Bir NuGet paketi kaldırın.</span><span class="sxs-lookup"><span data-stu-id="344f3-209">Remove a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="344f3-210">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="344f3-210">NuGet commands</span></span>

<span data-ttu-id="344f3-211">Komut</span><span class="sxs-lookup"><span data-stu-id="344f3-211">Command</span></span> | <span data-ttu-id="344f3-212">İşlev</span><span class="sxs-lookup"><span data-stu-id="344f3-212">Function</span></span>
--- | ---
[<span data-ttu-id="344f3-213">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="344f3-213">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="344f3-214">Sunucudan paket unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="344f3-214">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="344f3-215">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="344f3-215">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="344f3-216">Temizler veya http isteği önbelleği, geçici önbelleği veya makine genelinde genel paketler klasörü gibi yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="344f3-216">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="344f3-217">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="344f3-217">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="344f3-218">Sunucuya bir paket gönderir ve onu yayımlar.</span><span class="sxs-lookup"><span data-stu-id="344f3-218">Pushes a package to the server and publishes it.</span></span>

## <a name="examples"></a><span data-ttu-id="344f3-219">Örnekler</span><span class="sxs-lookup"><span data-stu-id="344f3-219">Examples</span></span>

<span data-ttu-id="344f3-220">Derlenmiş ve çalıştıran bir örnek .NET Core konsol uygulaması başlatılamadı:</span><span class="sxs-lookup"><span data-stu-id="344f3-220">Initialize a sample .NET Core console application that can be compiled and run:</span></span>

`dotnet new console`

<span data-ttu-id="344f3-221">Belirli bir uygulamayla ilgili bağımlılıkları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="344f3-221">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="344f3-222">Proje ve bağımlılıklarını belirli bir dizinde oluşturun:</span><span class="sxs-lookup"><span data-stu-id="344f3-222">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="344f3-223">Adlı framework bağımlı uygulamayı çalıştırma `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="344f3-223">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="344f3-224">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="344f3-224">Environment variables</span></span>

`DOTNET_PACKAGES`

<span data-ttu-id="344f3-225">Birincil paketi önbelleği.</span><span class="sxs-lookup"><span data-stu-id="344f3-225">The primary package cache.</span></span> <span data-ttu-id="344f3-226">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows.</span><span class="sxs-lookup"><span data-stu-id="344f3-226">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="344f3-227">Çalışma zamanı yüklerken paylaşılan ana bilgisayar tarafından kullanılacak hizmet dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="344f3-227">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="344f3-228">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="344f3-228">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="344f3-229">Kümesine `true` telemetri özelliğini çevirin için (değerleri `true`, `1`, veya `yes` kabul) Aksi takdirde ayarlanmış `false` katılımı telemetri özellikleri için (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="344f3-229">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted); otherwise, set to `false` to opt-in to the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="344f3-230">Ayarlanmadı, Varsayılanları olup olmadığını `false`, ve telemetri özellik etkindir.</span><span class="sxs-lookup"><span data-stu-id="344f3-230">If not set, the defaults is `false`, and the telemetry feature is active.</span></span>
