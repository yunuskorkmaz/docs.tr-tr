---
title: DotNet command - .NET Core CLI
description: Dotnet komutu (.NET Core CLI araçlarını genel sürücüsü) ve kullanımı hakkında bilgi edinin.
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 6e9f37dbbf94d56266a7b424601845d4429b4a04
ms.sourcegitcommit: d8bf4976eafe3289275be3811e7cb721bfff7e1e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34753545"
---
# <a name="dotnet-command"></a><span data-ttu-id="6af97-103">DotNet komutu</span><span class="sxs-lookup"><span data-stu-id="6af97-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="6af97-104">Ad</span><span class="sxs-lookup"><span data-stu-id="6af97-104">Name</span></span>

<span data-ttu-id="6af97-105">`dotnet` -Komut satırı komutlarını çalıştırmak için genel sürücüsü.</span><span class="sxs-lookup"><span data-stu-id="6af97-105">`dotnet` - General driver for running the command-line commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6af97-106">Özet</span><span class="sxs-lookup"><span data-stu-id="6af97-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6af97-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6af97-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6af97-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6af97-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6af97-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6af97-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="6af97-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6af97-110">Description</span></span>

<span data-ttu-id="6af97-111">`dotnet` Komut satırı arabirimi (CLI) zincirinin için genel bir sürücüsüdür.</span><span class="sxs-lookup"><span data-stu-id="6af97-111">`dotnet` is a generic driver for the Command Line Interface (CLI) toolchain.</span></span> <span data-ttu-id="6af97-112">Kendi kendine çağrılan kısa kullanım yönergeleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-112">Invoked on its own, it provides brief usage instructions.</span></span>

<span data-ttu-id="6af97-113">Her belirli bir özellik, bir komut olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="6af97-113">Each specific feature is implemented as a command.</span></span> <span data-ttu-id="6af97-114">Bu özelliği kullanmak için komutu sonra belirtilen `dotnet`, gibi [ `dotnet build` ](dotnet-build.md).</span><span class="sxs-lookup"><span data-stu-id="6af97-114">To use the feature, the command is specified after `dotnet`, such as [`dotnet build`](dotnet-build.md).</span></span> <span data-ttu-id="6af97-115">Tüm komut aşağıdaki bağımsız değişkenleri, kendi bağımsız değişkenler.</span><span class="sxs-lookup"><span data-stu-id="6af97-115">All of the arguments following the command are its own arguments.</span></span>

<span data-ttu-id="6af97-116">Yalnızca bir kez `dotnet` kendi başına bir komut çalıştırmaktır olarak kullanılan [framework bağımlı uygulamaları](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="6af97-116">The only time `dotnet` is used as a command on its own is to run [framework-dependent apps](../deploying/index.md).</span></span> <span data-ttu-id="6af97-117">Bir uygulama DLL belirtin sonra `dotnet` uygulamasını çalıştırmak için fiili (örneğin, `dotnet myapp.dll`).</span><span class="sxs-lookup"><span data-stu-id="6af97-117">Specify an application DLL after the `dotnet` verb to execute the application (for example, `dotnet myapp.dll`).</span></span>

## <a name="options"></a><span data-ttu-id="6af97-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="6af97-118">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6af97-119">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6af97-119">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="6af97-120">Ek yoluna *deps.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="6af97-120">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="6af97-121">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="6af97-121">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="6af97-122">Tanılama çıktıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-122">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="6af97-123">Uygulamayı çalıştırmak için kullanılacak yüklü .NET çekirdeği çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="6af97-123">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="6af97-124">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-124">Prints out a short help for the command.</span></span> <span data-ttu-id="6af97-125">İle kullanıyorsanız, `dotnet`, ayrıca kullanılabilir komutların listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-125">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="6af97-126">CLI araçları ve geçerli işletim sistemi gibi ortam hakkında ayrıntılı bilgi yazdırır, sürüm ve diğer bilgiler için SHA uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6af97-126">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--list-runtimes`

<span data-ttu-id="6af97-127">Yüklü .NET çekirdeği çalışma zamanları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6af97-127">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="6af97-128">Yüklü .NET Core SDK'ları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="6af97-128">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="6af97-129">Dökümünü hiçbir aday paylaşılan Framework'te iletin.</span><span class="sxs-lookup"><span data-stu-id="6af97-129">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6af97-130">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6af97-131">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6af97-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="6af97-132">Her komut desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="6af97-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="6af97-133">Kullanımdaki .NET Core SDK sürümü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6af97-134">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6af97-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="6af97-135">Ek yoluna *deps.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="6af97-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="6af97-136">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="6af97-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="6af97-137">Tanılama çıktıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="6af97-138">Uygulamayı çalıştırmak için kullanılacak yüklü .NET çekirdeği çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="6af97-138">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="6af97-139">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-139">Prints out a short help for the command.</span></span> <span data-ttu-id="6af97-140">İle kullanıyorsanız, `dotnet`, ayrıca kullanılabilir komutların listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-140">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="6af97-141">CLI araçları ve geçerli işletim sistemi gibi ortam hakkında ayrıntılı bilgi yazdırır, sürüm ve diğer bilgiler için SHA uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6af97-141">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="6af97-142">Dökümünü hiçbir aday paylaşılan Framework'te iletin.</span><span class="sxs-lookup"><span data-stu-id="6af97-142">Rolls forward on no candidate shared framework.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6af97-143">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-143">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6af97-144">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6af97-144">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="6af97-145">Her komut desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="6af97-145">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="6af97-146">Kullanımdaki .NET Core SDK sürümü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-146">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6af97-147">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6af97-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="6af97-148">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="6af97-148">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="6af97-149">Tanılama çıktıları sağlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-149">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="6af97-150">Uygulamayı çalıştırmak için kullanılacak yüklü .NET çekirdeği çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="6af97-150">Version of the installed .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="6af97-151">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-151">Prints out a short help for the command.</span></span> <span data-ttu-id="6af97-152">İle kullanıyorsanız, `dotnet`, ayrıca kullanılabilir komutların listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-152">If using with `dotnet`, it also prints a list of the available commands.</span></span>

`--info`

<span data-ttu-id="6af97-153">CLI araçları ve geçerli işletim sistemi gibi ortam hakkında ayrıntılı bilgi yazdırır, sürüm ve diğer bilgiler için SHA uygulayın.</span><span class="sxs-lookup"><span data-stu-id="6af97-153">Prints out detailed information about the CLI tooling and the environment, such as the current operating system, commit SHA for the version, and other information.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6af97-154">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-154">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6af97-155">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6af97-155">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="6af97-156">Her komut desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="6af97-156">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="6af97-157">Kullanımdaki .NET Core SDK sürümü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-157">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="6af97-158">DotNet komutları</span><span class="sxs-lookup"><span data-stu-id="6af97-158">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="6af97-159">Genel</span><span class="sxs-lookup"><span data-stu-id="6af97-159">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6af97-160">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6af97-160">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="6af97-161">Komut</span><span class="sxs-lookup"><span data-stu-id="6af97-161">Command</span></span>                                       | <span data-ttu-id="6af97-162">İşlev</span><span class="sxs-lookup"><span data-stu-id="6af97-162">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="6af97-163">dotnet build</span><span class="sxs-lookup"><span data-stu-id="6af97-163">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="6af97-164">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6af97-164">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="6af97-165">DotNet yapı-sunucu</span><span class="sxs-lookup"><span data-stu-id="6af97-165">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="6af97-166">Bir yapı tarafından başlatılan sunucularıyla etkileşim kurar.</span><span class="sxs-lookup"><span data-stu-id="6af97-166">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="6af97-167">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="6af97-167">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="6af97-168">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6af97-168">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="6af97-169">dotnet help</span><span class="sxs-lookup"><span data-stu-id="6af97-169">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="6af97-170">Komutu için çevrimiçi belgeleri ayrıntılı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6af97-170">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="6af97-171">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="6af97-171">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="6af97-172">Geçerli bir önizleme 2 projeyi .NET Core SDK 1.0 projeye geçirir.</span><span class="sxs-lookup"><span data-stu-id="6af97-172">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="6af97-173">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="6af97-173">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="6af97-174">MSBuild komut satırında erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-174">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="6af97-175">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6af97-175">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="6af97-176">Bir C# veya belirli bir şablon için F # projesine başlatır.</span><span class="sxs-lookup"><span data-stu-id="6af97-176">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="6af97-177">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="6af97-177">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="6af97-178">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6af97-178">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="6af97-179">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="6af97-179">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="6af97-180">.NET framework bağımlı veya kendi içinde bulunan uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-180">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="6af97-181">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="6af97-181">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="6af97-182">Belirli bir uygulamayla ilgili bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="6af97-182">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="6af97-183">dotnet run</span><span class="sxs-lookup"><span data-stu-id="6af97-183">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="6af97-184">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="6af97-184">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="6af97-185">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="6af97-185">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="6af97-186">Eklemek için seçenekler kaldırın ve bir çözüm dosyasında projelerini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="6af97-186">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="6af97-187">dotnet store</span><span class="sxs-lookup"><span data-stu-id="6af97-187">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="6af97-188">Derlemeleri çalışma zamanı paketi deposunda saklar.</span><span class="sxs-lookup"><span data-stu-id="6af97-188">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="6af97-189">dotnet test</span><span class="sxs-lookup"><span data-stu-id="6af97-189">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="6af97-190">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-190">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6af97-191">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6af97-191">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="6af97-192">Komut</span><span class="sxs-lookup"><span data-stu-id="6af97-192">Command</span></span>                             | <span data-ttu-id="6af97-193">İşlev</span><span class="sxs-lookup"><span data-stu-id="6af97-193">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="6af97-194">dotnet build</span><span class="sxs-lookup"><span data-stu-id="6af97-194">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="6af97-195">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6af97-195">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="6af97-196">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="6af97-196">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="6af97-197">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6af97-197">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="6af97-198">dotnet help</span><span class="sxs-lookup"><span data-stu-id="6af97-198">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="6af97-199">Komutu için çevrimiçi belgeleri ayrıntılı gösterir.</span><span class="sxs-lookup"><span data-stu-id="6af97-199">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="6af97-200">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="6af97-200">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="6af97-201">Geçerli bir önizleme 2 projeyi .NET Core SDK 1.0 projeye geçirir.</span><span class="sxs-lookup"><span data-stu-id="6af97-201">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="6af97-202">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="6af97-202">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="6af97-203">MSBuild komut satırında erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-203">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="6af97-204">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6af97-204">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="6af97-205">Bir C# veya belirli bir şablon için F # projesine başlatır.</span><span class="sxs-lookup"><span data-stu-id="6af97-205">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="6af97-206">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="6af97-206">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="6af97-207">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6af97-207">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="6af97-208">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="6af97-208">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="6af97-209">.NET framework bağımlı veya kendi içinde bulunan uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-209">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="6af97-210">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="6af97-210">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="6af97-211">Belirli bir uygulamayla ilgili bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="6af97-211">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="6af97-212">dotnet run</span><span class="sxs-lookup"><span data-stu-id="6af97-212">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="6af97-213">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="6af97-213">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="6af97-214">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="6af97-214">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="6af97-215">Eklemek için seçenekler kaldırın ve bir çözüm dosyasında projelerini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="6af97-215">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="6af97-216">dotnet store</span><span class="sxs-lookup"><span data-stu-id="6af97-216">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="6af97-217">Derlemeleri çalışma zamanı paketi deposunda saklar.</span><span class="sxs-lookup"><span data-stu-id="6af97-217">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="6af97-218">dotnet test</span><span class="sxs-lookup"><span data-stu-id="6af97-218">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="6af97-219">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-219">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6af97-220">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6af97-220">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="6af97-221">Komut</span><span class="sxs-lookup"><span data-stu-id="6af97-221">Command</span></span>                             | <span data-ttu-id="6af97-222">İşlev</span><span class="sxs-lookup"><span data-stu-id="6af97-222">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="6af97-223">dotnet build</span><span class="sxs-lookup"><span data-stu-id="6af97-223">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="6af97-224">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6af97-224">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="6af97-225">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="6af97-225">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="6af97-226">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="6af97-226">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="6af97-227">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="6af97-227">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="6af97-228">Geçerli bir önizleme 2 projeyi .NET Core SDK 1.0 projeye geçirir.</span><span class="sxs-lookup"><span data-stu-id="6af97-228">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="6af97-229">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="6af97-229">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="6af97-230">MSBuild komut satırında erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-230">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="6af97-231">dotnet new</span><span class="sxs-lookup"><span data-stu-id="6af97-231">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="6af97-232">Bir C# veya belirli bir şablon için F # projesine başlatır.</span><span class="sxs-lookup"><span data-stu-id="6af97-232">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="6af97-233">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="6af97-233">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="6af97-234">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6af97-234">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="6af97-235">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="6af97-235">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="6af97-236">.NET framework bağımlı veya kendi içinde bulunan uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-236">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="6af97-237">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="6af97-237">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="6af97-238">Belirli bir uygulamayla ilgili bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="6af97-238">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="6af97-239">dotnet run</span><span class="sxs-lookup"><span data-stu-id="6af97-239">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="6af97-240">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="6af97-240">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="6af97-241">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="6af97-241">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="6af97-242">Eklemek için seçenekler kaldırın ve bir çözüm dosyasında projelerini listeleyin.</span><span class="sxs-lookup"><span data-stu-id="6af97-242">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="6af97-243">dotnet test</span><span class="sxs-lookup"><span data-stu-id="6af97-243">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="6af97-244">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-244">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="6af97-245">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="6af97-245">Project references</span></span>

<span data-ttu-id="6af97-246">Komut</span><span class="sxs-lookup"><span data-stu-id="6af97-246">Command</span></span> | <span data-ttu-id="6af97-247">İşlev</span><span class="sxs-lookup"><span data-stu-id="6af97-247">Function</span></span>
--- | ---
[<span data-ttu-id="6af97-248">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="6af97-248">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="6af97-249">Proje başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="6af97-249">Adds a project reference.</span></span>
[<span data-ttu-id="6af97-250">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="6af97-250">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="6af97-251">Proje başvuruları listeler.</span><span class="sxs-lookup"><span data-stu-id="6af97-251">Lists project references.</span></span>
[<span data-ttu-id="6af97-252">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="6af97-252">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="6af97-253">Proje başvurusu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-253">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="6af97-254">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="6af97-254">NuGet packages</span></span>

<span data-ttu-id="6af97-255">Komut</span><span class="sxs-lookup"><span data-stu-id="6af97-255">Command</span></span> | <span data-ttu-id="6af97-256">İşlev</span><span class="sxs-lookup"><span data-stu-id="6af97-256">Function</span></span>
--- | ---
[<span data-ttu-id="6af97-257">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="6af97-257">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="6af97-258">Bir NuGet paketi ekler.</span><span class="sxs-lookup"><span data-stu-id="6af97-258">Adds a NuGet package.</span></span>
[<span data-ttu-id="6af97-259">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="6af97-259">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="6af97-260">Bir NuGet Paketi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-260">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="6af97-261">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="6af97-261">NuGet commands</span></span>

<span data-ttu-id="6af97-262">Komut</span><span class="sxs-lookup"><span data-stu-id="6af97-262">Command</span></span> | <span data-ttu-id="6af97-263">İşlev</span><span class="sxs-lookup"><span data-stu-id="6af97-263">Function</span></span>
--- | ---
[<span data-ttu-id="6af97-264">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="6af97-264">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="6af97-265">Sunucudan paket unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="6af97-265">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="6af97-266">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="6af97-266">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="6af97-267">Temizler veya http isteği önbelleği, geçici önbelleği veya makine genelinde genel paketler klasörü gibi yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="6af97-267">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="6af97-268">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="6af97-268">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="6af97-269">Sunucuya bir paket gönderir ve onu yayımlar.</span><span class="sxs-lookup"><span data-stu-id="6af97-269">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="6af97-270">Genel Araçlar komutları</span><span class="sxs-lookup"><span data-stu-id="6af97-270">Global Tools commands</span></span>

<span data-ttu-id="6af97-271">[.NET core genel Araçları](global-tools.md) .NET Core SDK'sı 2.1.300 kullanılabilir strating şunlardır:</span><span class="sxs-lookup"><span data-stu-id="6af97-271">[.NET Core Global Tools](global-tools.md) are available strating with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="6af97-272">Komut</span><span class="sxs-lookup"><span data-stu-id="6af97-272">Command</span></span> | <span data-ttu-id="6af97-273">İşlev</span><span class="sxs-lookup"><span data-stu-id="6af97-273">Function</span></span>
--- | ---
[<span data-ttu-id="6af97-274">DotNet aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="6af97-274">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="6af97-275">Makinenize genel bir aracı yükler.</span><span class="sxs-lookup"><span data-stu-id="6af97-275">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="6af97-276">DotNet araç listesi</span><span class="sxs-lookup"><span data-stu-id="6af97-276">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="6af97-277">Tüm genel makinenizde varsayılan dizin veya belirtilen yol şu anda yüklü araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="6af97-277">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="6af97-278">DotNet Aracı kaldırma</span><span class="sxs-lookup"><span data-stu-id="6af97-278">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="6af97-279">Genel bir aracı makinenizden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6af97-279">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="6af97-280">DotNet aracı güncelleştirmesi</span><span class="sxs-lookup"><span data-stu-id="6af97-280">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="6af97-281">Genel bir aracı makinenizde güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="6af97-281">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="6af97-282">Ek araçlar</span><span class="sxs-lookup"><span data-stu-id="6af97-282">Additional tools</span></span>

<span data-ttu-id="6af97-283">.NET Core SDK 2.1.300, yalnızca bir başına proje temel kullanarak kullanılabilir araçları sayısı ile başlayan `DotnetCliToolReference` artık kullanılabilir .NET Core SDK'ın bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="6af97-283">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="6af97-284">Bu araçlar içerir:</span><span class="sxs-lookup"><span data-stu-id="6af97-284">These tools include:</span></span>

| <span data-ttu-id="6af97-285">Aracı</span><span class="sxs-lookup"><span data-stu-id="6af97-285">Tool</span></span>                                              | <span data-ttu-id="6af97-286">İşlev</span><span class="sxs-lookup"><span data-stu-id="6af97-286">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="6af97-287">Geliştirme sertifikaları</span><span class="sxs-lookup"><span data-stu-id="6af97-287">dev-certs</span></span>                                         | <span data-ttu-id="6af97-288">Oluşturur ve geliştirme sertifikaları yönetir.</span><span class="sxs-lookup"><span data-stu-id="6af97-288">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="6af97-289">EF</span><span class="sxs-lookup"><span data-stu-id="6af97-289">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="6af97-290">Entity Framework Çekirdek komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="6af97-290">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="6af97-291">SQL önbellek</span><span class="sxs-lookup"><span data-stu-id="6af97-291">sql-cache</span></span>                                         | <span data-ttu-id="6af97-292">SQL Server önbellek komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="6af97-292">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="6af97-293">kullanıcı parolaları</span><span class="sxs-lookup"><span data-stu-id="6af97-293">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="6af97-294">Geliştirme kullanıcı parolaları yönetir.</span><span class="sxs-lookup"><span data-stu-id="6af97-294">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="6af97-295">İzleme</span><span class="sxs-lookup"><span data-stu-id="6af97-295">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="6af97-296">Dosyalar değiştiğinde, bir komut çalıştıran bir dosya İzleyicisi başlatır.</span><span class="sxs-lookup"><span data-stu-id="6af97-296">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="6af97-297">Her aracı hakkında daha fazla bilgi için yürütme `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="6af97-297">For more information about each tool, execute `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="6af97-298">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6af97-298">Examples</span></span>

<span data-ttu-id="6af97-299">Yeni bir .NET Core konsol uygulaması oluşturur:</span><span class="sxs-lookup"><span data-stu-id="6af97-299">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="6af97-300">Belirli bir uygulamayla ilgili bağımlılıkları geri yükleyin:</span><span class="sxs-lookup"><span data-stu-id="6af97-300">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="6af97-301">Proje ve bağımlılıklarını belirli bir dizinde oluşturun:</span><span class="sxs-lookup"><span data-stu-id="6af97-301">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="6af97-302">Adlı framework bağımlı uygulamayı çalıştırma `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="6af97-302">Run a framework-dependent app named `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="6af97-303">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="6af97-303">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="6af97-304">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="6af97-304">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="6af97-305">Birincil paketi önbelleği.</span><span class="sxs-lookup"><span data-stu-id="6af97-305">The primary package cache.</span></span> <span data-ttu-id="6af97-306">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows.</span><span class="sxs-lookup"><span data-stu-id="6af97-306">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="6af97-307">Çalışma zamanı yüklerken paylaşılan ana bilgisayar tarafından kullanılacak hizmet dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6af97-307">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="6af97-308">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6af97-308">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="6af97-309">Kümesine `true` telemetri özelliğini çevirin için (değerleri `true`, `1`, veya `yes` kabul).</span><span class="sxs-lookup"><span data-stu-id="6af97-309">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="6af97-310">Aksi takdirde kümesine `false` telemetri özelliklerini geri çevirme (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="6af97-310">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="6af97-311">Ayarlanmazsa varsayılan olup olmadığını `false` ve telemetri özellik etkindir.</span><span class="sxs-lookup"><span data-stu-id="6af97-311">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="6af97-312">.NET çekirdeği çalışma zamanı, paylaşılan framework veya SDK olmadığını çözümlenmiş genel konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6af97-312">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="6af97-313">Ayarlanmazsa, varsayılan olarak, `true`.</span><span class="sxs-lookup"><span data-stu-id="6af97-313">If not set, it defaults to `true`.</span></span> <span data-ttu-id="6af97-314">Kümesine `false` değil genel konumdan çözmek ve .NET çekirdeği yüklemeleri buluncaya (değerleri `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="6af97-314">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="6af97-315">Birden çok düzeyli arama hakkında daha fazla bilgi için bkz: [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="6af97-315">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="6af97-316">İleriye doğru sürümü geri alma devre dışı bırakır küçük.</span><span class="sxs-lookup"><span data-stu-id="6af97-316">Disables minor version roll forward.</span></span> <span data-ttu-id="6af97-317">Daha fazla bilgi için bkz: [ileriye](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="6af97-317">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="6af97-318">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="6af97-318">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="6af97-319">Birincil paketi önbelleği.</span><span class="sxs-lookup"><span data-stu-id="6af97-319">The primary package cache.</span></span> <span data-ttu-id="6af97-320">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows.</span><span class="sxs-lookup"><span data-stu-id="6af97-320">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="6af97-321">Çalışma zamanı yüklerken paylaşılan ana bilgisayar tarafından kullanılacak hizmet dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6af97-321">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="6af97-322">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6af97-322">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="6af97-323">Kümesine `true` telemetri özelliğini çevirin için (değerleri `true`, `1`, veya `yes` kabul).</span><span class="sxs-lookup"><span data-stu-id="6af97-323">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="6af97-324">Aksi takdirde kümesine `false` telemetri özelliklerini geri çevirme (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="6af97-324">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="6af97-325">Ayarlanmazsa varsayılan olup olmadığını `false` ve telemetri özellik etkindir.</span><span class="sxs-lookup"><span data-stu-id="6af97-325">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="6af97-326">.NET çekirdeği çalışma zamanı, paylaşılan framework veya SDK olmadığını çözümlenmiş genel konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6af97-326">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="6af97-327">Ayarlanmazsa, varsayılan olarak, `true`.</span><span class="sxs-lookup"><span data-stu-id="6af97-327">If not set, it defaults to `true`.</span></span> <span data-ttu-id="6af97-328">Kümesine `false` değil genel konumdan çözmek ve .NET çekirdeği yüklemeleri buluncaya (değerleri `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="6af97-328">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="6af97-329">Birden çok düzeyli arama hakkında daha fazla bilgi için bkz: [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="6af97-329">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="6af97-330">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="6af97-330">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="6af97-331">Birincil paketi önbelleği.</span><span class="sxs-lookup"><span data-stu-id="6af97-331">The primary package cache.</span></span> <span data-ttu-id="6af97-332">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows.</span><span class="sxs-lookup"><span data-stu-id="6af97-332">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="6af97-333">Çalışma zamanı yüklerken paylaşılan ana bilgisayar tarafından kullanılacak hizmet dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6af97-333">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="6af97-334">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6af97-334">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="6af97-335">Kümesine `true` telemetri özelliğini çevirin için (değerleri `true`, `1`, veya `yes` kabul).</span><span class="sxs-lookup"><span data-stu-id="6af97-335">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="6af97-336">Aksi takdirde kümesine `false` telemetri özelliklerini geri çevirme (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="6af97-336">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="6af97-337">Ayarlanmazsa varsayılan olup olmadığını `false` ve telemetri özellik etkindir.</span><span class="sxs-lookup"><span data-stu-id="6af97-337">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
