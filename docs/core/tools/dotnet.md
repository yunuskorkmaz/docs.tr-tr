---
title: DotNet command - .NET Core CLI
description: Dotnet komut (.NET Core CLI araçları için genel sürücü) ve kullanımı hakkında bilgi edinin.
author: mairaw
ms.author: mairaw
ms.date: 06/04/2018
ms.openlocfilehash: 53e8f8bab1cbaabaa7926aa68197c18843b0b637
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079822"
---
# <a name="dotnet-command"></a><span data-ttu-id="1e931-103">DotNet komutu</span><span class="sxs-lookup"><span data-stu-id="1e931-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="1e931-104">Ad</span><span class="sxs-lookup"><span data-stu-id="1e931-104">Name</span></span>

<span data-ttu-id="1e931-105">`dotnet` -.NET kaynak kodu ve ikili dosyaları yönetme bir araç.</span><span class="sxs-lookup"><span data-stu-id="1e931-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1e931-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="1e931-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1e931-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="1e931-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1e931-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="1e931-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1e931-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="1e931-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="1e931-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1e931-110">Description</span></span>

<span data-ttu-id="1e931-111">`dotnet` .NET kaynak kodu ve ikili dosyaları yönetmek için bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="1e931-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="1e931-112">Gibi belirli görevleri gerçekleştiren komutları gösteren [ `dotnet build` ](dotnet-build.md) ve [ `dotnet run` ](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="1e931-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="1e931-113">Her komut bağımsız kendi değişkenlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-113">Each command defines its own arguments.</span></span> <span data-ttu-id="1e931-114">Tür `--help` kısa erişmek için her komuttan sonra Yardım belgeleri.</span><span class="sxs-lookup"><span data-stu-id="1e931-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="1e931-115">`dotnet` DLL, uygulama belirterek uygulamaları çalıştırmak için kullanılan `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="1e931-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="1e931-116">Bkz: [.NET Core uygulama dağıtımı](../deploying/index.md) için dağıtım seçenekleri hakkında bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="1e931-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="1e931-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1e931-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1e931-118">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="1e931-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="1e931-119">Ek yolu *deps.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="1e931-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="1e931-120">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="1e931-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="1e931-121">Tanılama çıkışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="1e931-122">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="1e931-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="1e931-123">Belirli bir komut için belgeler gibi yazdırır `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="1e931-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="1e931-124">`dotnet --help` Kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="1e931-125">Bir .NET Core yüklemesi ve geçerli işletim sistemi ve .NET Core sürümünün SHA tamamlama gibi makine ortamı hakkında ayrıntılı bilgi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="1e931-126">Yüklü .NET Core çalışma zamanlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1e931-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="1e931-127">Yüklü .NET Core SDK'ları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1e931-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="1e931-128">Devre dışı bırakır podverze Top iletme, eğer ayarlanmış `0`.</span><span class="sxs-lookup"><span data-stu-id="1e931-128">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="1e931-129">Daha fazla bilgi için [İleri sarmanın](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="1e931-129">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="1e931-130">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-130">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1e931-131">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1e931-131">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="1e931-132">Her komutu desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="1e931-132">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="1e931-133">Kullanımda .NET Core SDK'sı sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-133">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1e931-134">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="1e931-134">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="1e931-135">Ek yolu *deps.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="1e931-135">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="1e931-136">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="1e931-136">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="1e931-137">Tanılama çıkışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-137">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="1e931-138">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="1e931-138">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="1e931-139">Belirli bir komut için belgeler gibi yazdırır `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="1e931-139">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="1e931-140">`dotnet --help` Kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-140">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="1e931-141">Bir .NET Core yüklemesi ve geçerli işletim sistemi ve .NET Core sürümünün SHA tamamlama gibi makine ortamı hakkında ayrıntılı bilgi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-141">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="1e931-142">Devre dışı bırakır podverze Top iletme, eğer ayarlanmış `0`.</span><span class="sxs-lookup"><span data-stu-id="1e931-142">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="1e931-143">Daha fazla bilgi için [İleri sarmanın](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="1e931-143">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="1e931-144">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-144">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1e931-145">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1e931-145">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="1e931-146">Her komutu desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="1e931-146">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="1e931-147">Kullanımda .NET Core SDK'sı sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-147">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1e931-148">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="1e931-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="1e931-149">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="1e931-149">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="1e931-150">Tanılama çıkışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-150">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="1e931-151">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="1e931-151">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="1e931-152">Belirli bir komut için belgeler gibi yazdırır `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="1e931-152">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="1e931-153">`dotnet --help` Kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-153">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="1e931-154">Bir .NET Core yüklemesi ve geçerli işletim sistemi ve .NET Core sürümünün SHA tamamlama gibi makine ortamı hakkında ayrıntılı bilgi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-154">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="1e931-155">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-155">Sets the verbosity level of the command.</span></span> <span data-ttu-id="1e931-156">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="1e931-156">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="1e931-157">Her komutu desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="1e931-157">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="1e931-158">Kullanımda .NET Core SDK'sı sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-158">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="1e931-159">DotNet komutları</span><span class="sxs-lookup"><span data-stu-id="1e931-159">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="1e931-160">Genel</span><span class="sxs-lookup"><span data-stu-id="1e931-160">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1e931-161">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="1e931-161">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="1e931-162">Komut</span><span class="sxs-lookup"><span data-stu-id="1e931-162">Command</span></span>                                       | <span data-ttu-id="1e931-163">İşlev</span><span class="sxs-lookup"><span data-stu-id="1e931-163">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="1e931-164">dotnet build</span><span class="sxs-lookup"><span data-stu-id="1e931-164">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="1e931-165">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e931-165">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="1e931-166">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="1e931-166">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="1e931-167">Bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.</span><span class="sxs-lookup"><span data-stu-id="1e931-167">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="1e931-168">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="1e931-168">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="1e931-169">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="1e931-169">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="1e931-170">dotnet help</span><span class="sxs-lookup"><span data-stu-id="1e931-170">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="1e931-171">Komut için çevrimiçi belgeleri ayrıntılı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e931-171">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="1e931-172">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="1e931-172">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="1e931-173">Geçerli bir önizleme 2 projesi bir .NET Core SDK'sı 1.0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="1e931-173">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="1e931-174">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="1e931-174">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="1e931-175">MSBuild komut satırını erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-175">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="1e931-176">dotnet new</span><span class="sxs-lookup"><span data-stu-id="1e931-176">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="1e931-177">Bir C# veya F # projesi için belirli bir şablon başlatır.</span><span class="sxs-lookup"><span data-stu-id="1e931-177">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="1e931-178">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="1e931-178">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="1e931-179">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e931-179">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="1e931-180">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="1e931-180">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="1e931-181">.NET framework bağımlı veya kendi içinde uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-181">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="1e931-182">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="1e931-182">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="1e931-183">Belirli bir uygulama için bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="1e931-183">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="1e931-184">dotnet run</span><span class="sxs-lookup"><span data-stu-id="1e931-184">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="1e931-185">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="1e931-185">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="1e931-186">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="1e931-186">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="1e931-187">Eklemek için seçenekler kaldırın ve çözüm dosyasındaki projeleri listeleyin.</span><span class="sxs-lookup"><span data-stu-id="1e931-187">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="1e931-188">dotnet store</span><span class="sxs-lookup"><span data-stu-id="1e931-188">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="1e931-189">Derlemeler çalışma zamanı Paket Deposu.</span><span class="sxs-lookup"><span data-stu-id="1e931-189">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="1e931-190">dotnet test</span><span class="sxs-lookup"><span data-stu-id="1e931-190">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="1e931-191">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-191">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1e931-192">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="1e931-192">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="1e931-193">Komut</span><span class="sxs-lookup"><span data-stu-id="1e931-193">Command</span></span>                             | <span data-ttu-id="1e931-194">İşlev</span><span class="sxs-lookup"><span data-stu-id="1e931-194">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="1e931-195">dotnet build</span><span class="sxs-lookup"><span data-stu-id="1e931-195">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="1e931-196">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e931-196">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="1e931-197">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="1e931-197">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="1e931-198">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="1e931-198">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="1e931-199">dotnet help</span><span class="sxs-lookup"><span data-stu-id="1e931-199">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="1e931-200">Komut için çevrimiçi belgeleri ayrıntılı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1e931-200">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="1e931-201">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="1e931-201">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="1e931-202">Geçerli bir önizleme 2 projesi bir .NET Core SDK'sı 1.0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="1e931-202">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="1e931-203">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="1e931-203">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="1e931-204">MSBuild komut satırını erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-204">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="1e931-205">dotnet new</span><span class="sxs-lookup"><span data-stu-id="1e931-205">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="1e931-206">Bir C# veya F # projesi için belirli bir şablon başlatır.</span><span class="sxs-lookup"><span data-stu-id="1e931-206">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="1e931-207">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="1e931-207">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="1e931-208">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e931-208">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="1e931-209">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="1e931-209">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="1e931-210">.NET framework bağımlı veya kendi içinde uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-210">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="1e931-211">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="1e931-211">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="1e931-212">Belirli bir uygulama için bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="1e931-212">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="1e931-213">dotnet run</span><span class="sxs-lookup"><span data-stu-id="1e931-213">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="1e931-214">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="1e931-214">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="1e931-215">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="1e931-215">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="1e931-216">Eklemek için seçenekler kaldırın ve çözüm dosyasındaki projeleri listeleyin.</span><span class="sxs-lookup"><span data-stu-id="1e931-216">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="1e931-217">dotnet store</span><span class="sxs-lookup"><span data-stu-id="1e931-217">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="1e931-218">Derlemeler çalışma zamanı Paket Deposu.</span><span class="sxs-lookup"><span data-stu-id="1e931-218">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="1e931-219">dotnet test</span><span class="sxs-lookup"><span data-stu-id="1e931-219">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="1e931-220">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-220">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1e931-221">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="1e931-221">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="1e931-222">Komut</span><span class="sxs-lookup"><span data-stu-id="1e931-222">Command</span></span>                             | <span data-ttu-id="1e931-223">İşlev</span><span class="sxs-lookup"><span data-stu-id="1e931-223">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="1e931-224">dotnet build</span><span class="sxs-lookup"><span data-stu-id="1e931-224">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="1e931-225">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e931-225">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="1e931-226">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="1e931-226">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="1e931-227">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="1e931-227">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="1e931-228">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="1e931-228">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="1e931-229">Geçerli bir önizleme 2 projesi bir .NET Core SDK'sı 1.0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="1e931-229">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="1e931-230">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="1e931-230">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="1e931-231">MSBuild komut satırını erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-231">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="1e931-232">dotnet new</span><span class="sxs-lookup"><span data-stu-id="1e931-232">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="1e931-233">Bir C# veya F # projesi için belirli bir şablon başlatır.</span><span class="sxs-lookup"><span data-stu-id="1e931-233">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="1e931-234">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="1e931-234">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="1e931-235">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1e931-235">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="1e931-236">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="1e931-236">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="1e931-237">.NET framework bağımlı veya kendi içinde uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-237">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="1e931-238">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="1e931-238">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="1e931-239">Belirli bir uygulama için bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="1e931-239">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="1e931-240">dotnet run</span><span class="sxs-lookup"><span data-stu-id="1e931-240">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="1e931-241">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="1e931-241">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="1e931-242">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="1e931-242">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="1e931-243">Eklemek için seçenekler kaldırın ve çözüm dosyasındaki projeleri listeleyin.</span><span class="sxs-lookup"><span data-stu-id="1e931-243">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="1e931-244">dotnet test</span><span class="sxs-lookup"><span data-stu-id="1e931-244">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="1e931-245">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-245">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="1e931-246">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="1e931-246">Project references</span></span>

<span data-ttu-id="1e931-247">Komut</span><span class="sxs-lookup"><span data-stu-id="1e931-247">Command</span></span> | <span data-ttu-id="1e931-248">İşlev</span><span class="sxs-lookup"><span data-stu-id="1e931-248">Function</span></span>
--- | ---
[<span data-ttu-id="1e931-249">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="1e931-249">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="1e931-250">Bir proje başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="1e931-250">Adds a project reference.</span></span>
[<span data-ttu-id="1e931-251">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="1e931-251">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="1e931-252">Proje başvuruları listeler.</span><span class="sxs-lookup"><span data-stu-id="1e931-252">Lists project references.</span></span>
[<span data-ttu-id="1e931-253">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="1e931-253">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="1e931-254">Bir proje başvurusu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-254">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="1e931-255">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="1e931-255">NuGet packages</span></span>

<span data-ttu-id="1e931-256">Komut</span><span class="sxs-lookup"><span data-stu-id="1e931-256">Command</span></span> | <span data-ttu-id="1e931-257">İşlev</span><span class="sxs-lookup"><span data-stu-id="1e931-257">Function</span></span>
--- | ---
[<span data-ttu-id="1e931-258">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="1e931-258">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="1e931-259">Bir NuGet paketi ekler.</span><span class="sxs-lookup"><span data-stu-id="1e931-259">Adds a NuGet package.</span></span>
[<span data-ttu-id="1e931-260">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="1e931-260">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="1e931-261">Bir NuGet Paketi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-261">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="1e931-262">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="1e931-262">NuGet commands</span></span>

<span data-ttu-id="1e931-263">Komut</span><span class="sxs-lookup"><span data-stu-id="1e931-263">Command</span></span> | <span data-ttu-id="1e931-264">İşlev</span><span class="sxs-lookup"><span data-stu-id="1e931-264">Function</span></span>
--- | ---
[<span data-ttu-id="1e931-265">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="1e931-265">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="1e931-266">Sunucudan bir paket unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="1e931-266">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="1e931-267">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="1e931-267">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="1e931-268">Temizler veya http istek önbelleği, geçici bir önbellekte veya makine genelindeki genel paketleri klasörü gibi yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="1e931-268">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="1e931-269">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="1e931-269">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="1e931-270">Sunucuya bir paket gönderir ve belgeyi yayımlar.</span><span class="sxs-lookup"><span data-stu-id="1e931-270">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="1e931-271">Genel Araçlar komutları</span><span class="sxs-lookup"><span data-stu-id="1e931-271">Global Tools commands</span></span>

<span data-ttu-id="1e931-272">[.NET core Araçları Genel](global-tools.md) 2.1.300 .NET Core SDK ile başlayarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="1e931-272">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="1e931-273">Komut</span><span class="sxs-lookup"><span data-stu-id="1e931-273">Command</span></span> | <span data-ttu-id="1e931-274">İşlev</span><span class="sxs-lookup"><span data-stu-id="1e931-274">Function</span></span>
--- | ---
[<span data-ttu-id="1e931-275">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="1e931-275">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="1e931-276">Makinenize genel bir aracı yükler.</span><span class="sxs-lookup"><span data-stu-id="1e931-276">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="1e931-277">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="1e931-277">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="1e931-278">Tüm genel varsayılan dizinde makinenizde veya belirtilen yolda yüklü araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="1e931-278">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="1e931-279">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="1e931-279">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="1e931-280">Genel bir aracı makinenizde kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1e931-280">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="1e931-281">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="1e931-281">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="1e931-282">Genel bir aracı makinenizde güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="1e931-282">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="1e931-283">Ek araçlar</span><span class="sxs-lookup"><span data-stu-id="1e931-283">Additional tools</span></span>

<span data-ttu-id="1e931-284">.NET Core SDK 2.1.300, yalnızca bir proje kullanarak mevcut araçlar ile başlayan `DotnetCliToolReference` artık .NET Core SDK'sını bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="1e931-284">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="1e931-285">Bu araçlar aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="1e931-285">These tools are listed in the following table:</span></span>

| <span data-ttu-id="1e931-286">Aracı</span><span class="sxs-lookup"><span data-stu-id="1e931-286">Tool</span></span>                                              | <span data-ttu-id="1e931-287">İşlev</span><span class="sxs-lookup"><span data-stu-id="1e931-287">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="1e931-288">dev-certs</span><span class="sxs-lookup"><span data-stu-id="1e931-288">dev-certs</span></span>                                         | <span data-ttu-id="1e931-289">Oluşturur ve geliştirme sertifikaları yönetir.</span><span class="sxs-lookup"><span data-stu-id="1e931-289">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="1e931-290">EF</span><span class="sxs-lookup"><span data-stu-id="1e931-290">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="1e931-291">Entity Framework Core komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="1e931-291">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="1e931-292">SQL önbellek</span><span class="sxs-lookup"><span data-stu-id="1e931-292">sql-cache</span></span>                                         | <span data-ttu-id="1e931-293">SQL Server önbellek komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="1e931-293">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="1e931-294">kullanıcı parolaları</span><span class="sxs-lookup"><span data-stu-id="1e931-294">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="1e931-295">Geliştirme kullanıcı parolalarını yönetir.</span><span class="sxs-lookup"><span data-stu-id="1e931-295">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="1e931-296">İzleme</span><span class="sxs-lookup"><span data-stu-id="1e931-296">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="1e931-297">Bir komut dosyaları değiştirdiğinizde çalıştıran bir dosya İzleyicisi başlatır.</span><span class="sxs-lookup"><span data-stu-id="1e931-297">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="1e931-298">Her araç hakkında daha fazla bilgi için türü `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="1e931-298">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="1e931-299">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1e931-299">Examples</span></span>

<span data-ttu-id="1e931-300">Yeni bir .NET Core konsol uygulaması oluşturur:</span><span class="sxs-lookup"><span data-stu-id="1e931-300">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="1e931-301">Belirli bir uygulamanın bağımlılıklarını geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="1e931-301">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="1e931-302">Bir proje ve bağımlılıkları belirli bir dizinde oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1e931-302">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="1e931-303">DLL, uygulama çalıştırmak `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="1e931-303">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="1e931-304">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="1e931-304">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="1e931-305">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="1e931-305">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="1e931-306">Birincil paket önbelleğini.</span><span class="sxs-lookup"><span data-stu-id="1e931-306">The primary package cache.</span></span> <span data-ttu-id="1e931-307">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows üzerinde.</span><span class="sxs-lookup"><span data-stu-id="1e931-307">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="1e931-308">Çalışma zamanı yüklerken paylaşılan bir ana bilgisayar tarafından kullanılacak bakım dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e931-308">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="1e931-309">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e931-309">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="1e931-310">Kümesine `true` ayrılma telemetri özelliği (değerleri `true`, `1`, veya `yes` kabul).</span><span class="sxs-lookup"><span data-stu-id="1e931-310">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="1e931-311">Aksi takdirde, kümesine `false` telemetri özelliklerini kabul etme (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="1e931-311">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="1e931-312">Varsayılan ayarlanmazsa `false` ve telemetri özellik etkin durumda.</span><span class="sxs-lookup"><span data-stu-id="1e931-312">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="1e931-313">.NET Core çalışma zamanı, paylaşılan çerçeve veya SDK olup olmadığını çözümlenen genel konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e931-313">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="1e931-314">Ayarlanmazsa, varsayılan olarak, `true`.</span><span class="sxs-lookup"><span data-stu-id="1e931-314">If not set, it defaults to `true`.</span></span> <span data-ttu-id="1e931-315">Kümesine `false` değil genel konumundan çözmek ve .NET Core yüklemeleri yalıtıncaya (değerleri `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="1e931-315">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="1e931-316">Çok düzeyli arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="1e931-316">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="1e931-317">Devre dışı bırakır podverze Top iletme, eğer ayarlanmış `0`.</span><span class="sxs-lookup"><span data-stu-id="1e931-317">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="1e931-318">Daha fazla bilgi için [İleri sarmanın](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="1e931-318">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="1e931-319">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="1e931-319">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="1e931-320">Birincil paket önbelleğini.</span><span class="sxs-lookup"><span data-stu-id="1e931-320">The primary package cache.</span></span> <span data-ttu-id="1e931-321">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows üzerinde.</span><span class="sxs-lookup"><span data-stu-id="1e931-321">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="1e931-322">Çalışma zamanı yüklerken paylaşılan bir ana bilgisayar tarafından kullanılacak bakım dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e931-322">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="1e931-323">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e931-323">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="1e931-324">Kümesine `true` ayrılma telemetri özelliği (değerleri `true`, `1`, veya `yes` kabul).</span><span class="sxs-lookup"><span data-stu-id="1e931-324">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="1e931-325">Aksi takdirde, kümesine `false` telemetri özelliklerini kabul etme (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="1e931-325">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="1e931-326">Varsayılan ayarlanmazsa `false` ve telemetri özellik etkin durumda.</span><span class="sxs-lookup"><span data-stu-id="1e931-326">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="1e931-327">.NET Core çalışma zamanı, paylaşılan çerçeve veya SDK olup olmadığını çözümlenen genel konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e931-327">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="1e931-328">Ayarlanmazsa, varsayılan olarak, `true`.</span><span class="sxs-lookup"><span data-stu-id="1e931-328">If not set, it defaults to `true`.</span></span> <span data-ttu-id="1e931-329">Kümesine `false` değil genel konumundan çözmek ve .NET Core yüklemeleri yalıtıncaya (değerleri `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="1e931-329">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="1e931-330">Çok düzeyli arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="1e931-330">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="1e931-331">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="1e931-331">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="1e931-332">Birincil paket önbelleğini.</span><span class="sxs-lookup"><span data-stu-id="1e931-332">The primary package cache.</span></span> <span data-ttu-id="1e931-333">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows üzerinde.</span><span class="sxs-lookup"><span data-stu-id="1e931-333">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="1e931-334">Çalışma zamanı yüklerken paylaşılan bir ana bilgisayar tarafından kullanılacak bakım dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e931-334">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="1e931-335">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1e931-335">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="1e931-336">Kümesine `true` ayrılma telemetri özelliği (değerleri `true`, `1`, veya `yes` kabul).</span><span class="sxs-lookup"><span data-stu-id="1e931-336">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="1e931-337">Aksi takdirde, kümesine `false` telemetri özelliklerini kabul etme (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="1e931-337">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="1e931-338">Varsayılan ayarlanmazsa `false` ve telemetri özellik etkin durumda.</span><span class="sxs-lookup"><span data-stu-id="1e931-338">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
