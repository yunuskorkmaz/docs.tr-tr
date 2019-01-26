---
title: DotNet komutu
description: Dotnet komut (.NET Core CLI araçları için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 06/04/2018
ms.openlocfilehash: 53eb96ee6fe809b2e6e42eec4e7e9b5f7c5edf2a
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/25/2019
ms.locfileid: "55066447"
---
# <a name="dotnet-command"></a><span data-ttu-id="4f61f-103">DotNet komutu</span><span class="sxs-lookup"><span data-stu-id="4f61f-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4f61f-104">Ad</span><span class="sxs-lookup"><span data-stu-id="4f61f-104">Name</span></span>

<span data-ttu-id="4f61f-105">`dotnet` -.NET kaynak kodu ve ikili dosyaları yönetme bir araç.</span><span class="sxs-lookup"><span data-stu-id="4f61f-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4f61f-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="4f61f-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4f61f-107">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4f61f-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4f61f-108">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="4f61f-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4f61f-109">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="4f61f-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```
---

## <a name="description"></a><span data-ttu-id="4f61f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f61f-110">Description</span></span>

<span data-ttu-id="4f61f-111">`dotnet` .NET kaynak kodu ve ikili dosyaları yönetmek için bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="4f61f-112">Gibi belirli görevleri gerçekleştiren komutları gösteren [ `dotnet build` ](dotnet-build.md) ve [ `dotnet run` ](dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="4f61f-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="4f61f-113">Her komut bağımsız kendi değişkenlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-113">Each command defines its own arguments.</span></span> <span data-ttu-id="4f61f-114">Tür `--help` kısa erişmek için her komuttan sonra Yardım belgeleri.</span><span class="sxs-lookup"><span data-stu-id="4f61f-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="4f61f-115">`dotnet` DLL, uygulama belirterek uygulamaları çalıştırmak için kullanılan `dotnet myapp.dll`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="4f61f-116">Bkz: [.NET Core uygulama dağıtımı](../deploying/index.md) için dağıtım seçenekleri hakkında bilgi edinmek için.</span><span class="sxs-lookup"><span data-stu-id="4f61f-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="4f61f-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="4f61f-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4f61f-118">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4f61f-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="4f61f-119">Ek yolu *deps.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="4f61f-119">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="4f61f-120">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="4f61f-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="4f61f-121">Tanılama çıkışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="4f61f-122">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="4f61f-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="4f61f-123">Belirli bir komut için belgeler gibi yazdırır `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="4f61f-124">`dotnet --help` Kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="4f61f-125">Bir .NET Core yüklemesi ve geçerli işletim sistemi ve .NET Core sürümünün SHA tamamlama gibi makine ortamı hakkında ayrıntılı bilgi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="4f61f-126">Yüklü .NET Core çalışma zamanlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="4f61f-127">Yüklü .NET Core SDK'ları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="4f61f-128">Gerekli paylaşılan çerçeve olmadığında davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-128">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="4f61f-129">`N` aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="4f61f-129">`N` can be:</span></span>
 * <span data-ttu-id="4f61f-130">`0` -Daha alt sürümü ileri sarma devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="4f61f-130">`0` - Disable even minor version roll forward.</span></span>
 * <span data-ttu-id="4f61f-131">`1` -İkincil sürüm, ancak ana sürüm İleri sarmanın.</span><span class="sxs-lookup"><span data-stu-id="4f61f-131">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="4f61f-132">Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-132">This is the default behavior.</span></span>
 * <span data-ttu-id="4f61f-133">`2` -Küçük ve büyük sürüme göre İleri sarmanın.</span><span class="sxs-lookup"><span data-stu-id="4f61f-133">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="4f61f-134">Daha fazla bilgi için [İleri sarmanın](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="4f61f-134">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4f61f-135">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-135">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4f61f-136">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-136">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4f61f-137">Her komutu desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="4f61f-137">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="4f61f-138">Kullanımda .NET Core SDK'sı sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-138">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4f61f-139">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="4f61f-139">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="4f61f-140">Ek yolu *deps.json* dosya.</span><span class="sxs-lookup"><span data-stu-id="4f61f-140">Path to additional *deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="4f61f-141">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="4f61f-141">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="4f61f-142">Tanılama çıkışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-142">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="4f61f-143">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="4f61f-143">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="4f61f-144">Belirli bir komut için belgeler gibi yazdırır `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="4f61f-145">`dotnet --help` Kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-145">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="4f61f-146">Bir .NET Core yüklemesi ve geçerli işletim sistemi ve .NET Core sürümünün SHA tamamlama gibi makine ortamı hakkında ayrıntılı bilgi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-146">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="4f61f-147">Devre dışı bırakır podverze Top iletme, eğer ayarlanmış `0`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-147">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="4f61f-148">Daha fazla bilgi için [İleri sarmanın](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="4f61f-148">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4f61f-149">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4f61f-150">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4f61f-151">Her komutu desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="4f61f-151">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="4f61f-152">Kullanımda .NET Core SDK'sı sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-152">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4f61f-153">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="4f61f-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="4f61f-154">Algılama İlkesi ve araştırma için derlemeleri içeren yolu.</span><span class="sxs-lookup"><span data-stu-id="4f61f-154">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="4f61f-155">Tanılama çıkışı sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-155">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="4f61f-156">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanı sürümü.</span><span class="sxs-lookup"><span data-stu-id="4f61f-156">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="4f61f-157">Belirli bir komut için belgeler gibi yazdırır `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-157">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="4f61f-158">`dotnet --help` Kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-158">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="4f61f-159">Bir .NET Core yüklemesi ve geçerli işletim sistemi ve .NET Core sürümünün SHA tamamlama gibi makine ortamı hakkında ayrıntılı bilgi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-159">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4f61f-160">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4f61f-161">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="4f61f-162">Her komutu desteklenmiyor; Bu seçenek kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="4f61f-162">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="4f61f-163">Kullanımda .NET Core SDK'sı sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-163">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="4f61f-164">DotNet komutları</span><span class="sxs-lookup"><span data-stu-id="4f61f-164">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="4f61f-165">Genel</span><span class="sxs-lookup"><span data-stu-id="4f61f-165">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4f61f-166">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4f61f-166">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="4f61f-167">Komut</span><span class="sxs-lookup"><span data-stu-id="4f61f-167">Command</span></span>                                       | <span data-ttu-id="4f61f-168">İşlev</span><span class="sxs-lookup"><span data-stu-id="4f61f-168">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="4f61f-169">dotnet build</span><span class="sxs-lookup"><span data-stu-id="4f61f-169">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="4f61f-170">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f61f-170">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="4f61f-171">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="4f61f-171">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="4f61f-172">Bir derleme tarafından başlatılan sunucularıyla etkileşim kurar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-172">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="4f61f-173">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="4f61f-173">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="4f61f-174">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-174">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="4f61f-175">dotnet help</span><span class="sxs-lookup"><span data-stu-id="4f61f-175">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="4f61f-176">Komut için çevrimiçi belgeleri ayrıntılı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-176">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="4f61f-177">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="4f61f-177">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="4f61f-178">Geçerli bir önizleme 2 projesi bir .NET Core SDK'sı 1.0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-178">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="4f61f-179">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="4f61f-179">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="4f61f-180">MSBuild komut satırını erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-180">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="4f61f-181">dotnet new</span><span class="sxs-lookup"><span data-stu-id="4f61f-181">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="4f61f-182">Başlatan bir C# veya F# verilen şablonu için proje.</span><span class="sxs-lookup"><span data-stu-id="4f61f-182">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="4f61f-183">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="4f61f-183">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="4f61f-184">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f61f-184">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="4f61f-185">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="4f61f-185">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="4f61f-186">.NET framework bağımlı veya kendi içinde uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-186">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="4f61f-187">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="4f61f-187">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="4f61f-188">Belirli bir uygulama için bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-188">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="4f61f-189">dotnet run</span><span class="sxs-lookup"><span data-stu-id="4f61f-189">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="4f61f-190">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-190">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="4f61f-191">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="4f61f-191">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="4f61f-192">Eklemek için seçenekler kaldırın ve çözüm dosyasındaki projeleri listeleyin.</span><span class="sxs-lookup"><span data-stu-id="4f61f-192">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="4f61f-193">dotnet store</span><span class="sxs-lookup"><span data-stu-id="4f61f-193">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="4f61f-194">Derlemeler çalışma zamanı Paket Deposu.</span><span class="sxs-lookup"><span data-stu-id="4f61f-194">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="4f61f-195">dotnet test</span><span class="sxs-lookup"><span data-stu-id="4f61f-195">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="4f61f-196">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-196">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4f61f-197">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="4f61f-197">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="4f61f-198">Komut</span><span class="sxs-lookup"><span data-stu-id="4f61f-198">Command</span></span>                             | <span data-ttu-id="4f61f-199">İşlev</span><span class="sxs-lookup"><span data-stu-id="4f61f-199">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="4f61f-200">dotnet build</span><span class="sxs-lookup"><span data-stu-id="4f61f-200">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="4f61f-201">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f61f-201">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="4f61f-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="4f61f-202">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="4f61f-203">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-203">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="4f61f-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="4f61f-204">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="4f61f-205">Komut için çevrimiçi belgeleri ayrıntılı gösterir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="4f61f-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="4f61f-206">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="4f61f-207">Geçerli bir önizleme 2 projesi bir .NET Core SDK'sı 1.0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="4f61f-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="4f61f-208">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="4f61f-209">MSBuild komut satırını erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="4f61f-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="4f61f-210">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="4f61f-211">Başlatan bir C# veya F# verilen şablonu için proje.</span><span class="sxs-lookup"><span data-stu-id="4f61f-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="4f61f-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="4f61f-212">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="4f61f-213">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f61f-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="4f61f-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="4f61f-214">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="4f61f-215">.NET framework bağımlı veya kendi içinde uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="4f61f-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="4f61f-216">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="4f61f-217">Belirli bir uygulama için bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="4f61f-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="4f61f-218">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="4f61f-219">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="4f61f-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="4f61f-220">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="4f61f-221">Eklemek için seçenekler kaldırın ve çözüm dosyasındaki projeleri listeleyin.</span><span class="sxs-lookup"><span data-stu-id="4f61f-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="4f61f-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="4f61f-222">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="4f61f-223">Derlemeler çalışma zamanı Paket Deposu.</span><span class="sxs-lookup"><span data-stu-id="4f61f-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="4f61f-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="4f61f-224">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="4f61f-225">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-225">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4f61f-226">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="4f61f-226">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="4f61f-227">Komut</span><span class="sxs-lookup"><span data-stu-id="4f61f-227">Command</span></span>                             | <span data-ttu-id="4f61f-228">İşlev</span><span class="sxs-lookup"><span data-stu-id="4f61f-228">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="4f61f-229">dotnet build</span><span class="sxs-lookup"><span data-stu-id="4f61f-229">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="4f61f-230">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f61f-230">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="4f61f-231">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="4f61f-231">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="4f61f-232">Temiz yapı çıkarır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-232">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="4f61f-233">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="4f61f-233">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="4f61f-234">Geçerli bir önizleme 2 projesi bir .NET Core SDK'sı 1.0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-234">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="4f61f-235">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="4f61f-235">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="4f61f-236">MSBuild komut satırını erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-236">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="4f61f-237">dotnet new</span><span class="sxs-lookup"><span data-stu-id="4f61f-237">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="4f61f-238">Başlatan bir C# veya F# verilen şablonu için proje.</span><span class="sxs-lookup"><span data-stu-id="4f61f-238">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="4f61f-239">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="4f61f-239">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="4f61f-240">Kodunuzun bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="4f61f-240">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="4f61f-241">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="4f61f-241">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="4f61f-242">.NET framework bağımlı veya kendi içinde uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-242">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="4f61f-243">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="4f61f-243">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="4f61f-244">Belirli bir uygulama için bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-244">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="4f61f-245">dotnet run</span><span class="sxs-lookup"><span data-stu-id="4f61f-245">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="4f61f-246">Uygulama kaynağından çalışır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-246">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="4f61f-247">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="4f61f-247">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="4f61f-248">Eklemek için seçenekler kaldırın ve çözüm dosyasındaki projeleri listeleyin.</span><span class="sxs-lookup"><span data-stu-id="4f61f-248">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="4f61f-249">dotnet test</span><span class="sxs-lookup"><span data-stu-id="4f61f-249">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="4f61f-250">Test Çalıştırıcısı kullanarak testleri çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-250">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="4f61f-251">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="4f61f-251">Project references</span></span>

<span data-ttu-id="4f61f-252">Komut</span><span class="sxs-lookup"><span data-stu-id="4f61f-252">Command</span></span> | <span data-ttu-id="4f61f-253">İşlev</span><span class="sxs-lookup"><span data-stu-id="4f61f-253">Function</span></span>
--- | ---
[<span data-ttu-id="4f61f-254">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="4f61f-254">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="4f61f-255">Bir proje başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-255">Adds a project reference.</span></span>
[<span data-ttu-id="4f61f-256">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="4f61f-256">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="4f61f-257">Proje başvuruları listeler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-257">Lists project references.</span></span>
[<span data-ttu-id="4f61f-258">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="4f61f-258">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="4f61f-259">Bir proje başvurusu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-259">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="4f61f-260">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="4f61f-260">NuGet packages</span></span>

<span data-ttu-id="4f61f-261">Komut</span><span class="sxs-lookup"><span data-stu-id="4f61f-261">Command</span></span> | <span data-ttu-id="4f61f-262">İşlev</span><span class="sxs-lookup"><span data-stu-id="4f61f-262">Function</span></span>
--- | ---
[<span data-ttu-id="4f61f-263">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="4f61f-263">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="4f61f-264">Bir NuGet paketi ekler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-264">Adds a NuGet package.</span></span>
[<span data-ttu-id="4f61f-265">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="4f61f-265">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="4f61f-266">Bir NuGet Paketi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-266">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="4f61f-267">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="4f61f-267">NuGet commands</span></span>

<span data-ttu-id="4f61f-268">Komut</span><span class="sxs-lookup"><span data-stu-id="4f61f-268">Command</span></span> | <span data-ttu-id="4f61f-269">İşlev</span><span class="sxs-lookup"><span data-stu-id="4f61f-269">Function</span></span>
--- | ---
[<span data-ttu-id="4f61f-270">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="4f61f-270">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="4f61f-271">Sunucudan bir paket unlists veya siler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-271">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="4f61f-272">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="4f61f-272">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="4f61f-273">Temizler veya http istek önbelleği, geçici bir önbellekte veya makine genelindeki genel paketleri klasörü gibi yerel NuGet kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-273">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="4f61f-274">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="4f61f-274">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="4f61f-275">Sunucuya bir paket gönderir ve belgeyi yayımlar.</span><span class="sxs-lookup"><span data-stu-id="4f61f-275">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="4f61f-276">Genel Araçlar komutları</span><span class="sxs-lookup"><span data-stu-id="4f61f-276">Global Tools commands</span></span>

<span data-ttu-id="4f61f-277">[.NET core Araçları Genel](global-tools.md) 2.1.300 .NET Core SDK ile başlayarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="4f61f-277">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="4f61f-278">Komut</span><span class="sxs-lookup"><span data-stu-id="4f61f-278">Command</span></span> | <span data-ttu-id="4f61f-279">İşlev</span><span class="sxs-lookup"><span data-stu-id="4f61f-279">Function</span></span>
--- | ---
[<span data-ttu-id="4f61f-280">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="4f61f-280">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="4f61f-281">Makinenize genel bir aracı yükler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-281">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="4f61f-282">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="4f61f-282">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="4f61f-283">Tüm genel varsayılan dizinde makinenizde veya belirtilen yolda yüklü araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="4f61f-283">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="4f61f-284">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="4f61f-284">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="4f61f-285">Genel bir aracı makinenizde kaldırır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-285">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="4f61f-286">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="4f61f-286">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="4f61f-287">Genel bir aracı makinenizde güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-287">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="4f61f-288">Ek araçlar</span><span class="sxs-lookup"><span data-stu-id="4f61f-288">Additional tools</span></span>

<span data-ttu-id="4f61f-289">.NET Core SDK 2.1.300, yalnızca bir proje kullanarak mevcut araçlar ile başlayan `DotnetCliToolReference` artık .NET Core SDK'sını bir parçası olarak.</span><span class="sxs-lookup"><span data-stu-id="4f61f-289">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="4f61f-290">Bu araçlar aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="4f61f-290">These tools are listed in the following table:</span></span>

| <span data-ttu-id="4f61f-291">Aracı</span><span class="sxs-lookup"><span data-stu-id="4f61f-291">Tool</span></span>                                              | <span data-ttu-id="4f61f-292">İşlev</span><span class="sxs-lookup"><span data-stu-id="4f61f-292">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="4f61f-293">dev-certs</span><span class="sxs-lookup"><span data-stu-id="4f61f-293">dev-certs</span></span>                                         | <span data-ttu-id="4f61f-294">Oluşturur ve geliştirme sertifikaları yönetir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-294">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="4f61f-295">EF</span><span class="sxs-lookup"><span data-stu-id="4f61f-295">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="4f61f-296">Entity Framework Core komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="4f61f-296">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="4f61f-297">SQL önbellek</span><span class="sxs-lookup"><span data-stu-id="4f61f-297">sql-cache</span></span>                                         | <span data-ttu-id="4f61f-298">SQL Server önbellek komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="4f61f-298">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="4f61f-299">kullanıcı parolaları</span><span class="sxs-lookup"><span data-stu-id="4f61f-299">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="4f61f-300">Geliştirme kullanıcı parolalarını yönetir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-300">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="4f61f-301">İzleme</span><span class="sxs-lookup"><span data-stu-id="4f61f-301">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="4f61f-302">Bir komut dosyaları değiştirdiğinizde çalıştıran bir dosya İzleyicisi başlatır.</span><span class="sxs-lookup"><span data-stu-id="4f61f-302">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="4f61f-303">Her araç hakkında daha fazla bilgi için türü `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-303">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="4f61f-304">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4f61f-304">Examples</span></span>

<span data-ttu-id="4f61f-305">Yeni bir .NET Core konsol uygulaması oluşturur:</span><span class="sxs-lookup"><span data-stu-id="4f61f-305">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="4f61f-306">Belirli bir uygulamanın bağımlılıklarını geri yükleme:</span><span class="sxs-lookup"><span data-stu-id="4f61f-306">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="4f61f-307">Bir proje ve bağımlılıkları belirli bir dizinde oluşturun:</span><span class="sxs-lookup"><span data-stu-id="4f61f-307">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="4f61f-308">DLL, uygulama çalıştırmak `myapp.dll`:</span><span class="sxs-lookup"><span data-stu-id="4f61f-308">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="4f61f-309">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="4f61f-309">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="4f61f-310">.NET core 2.1</span><span class="sxs-lookup"><span data-stu-id="4f61f-310">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="4f61f-311">Birincil paket önbelleğini.</span><span class="sxs-lookup"><span data-stu-id="4f61f-311">The primary package cache.</span></span> <span data-ttu-id="4f61f-312">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows üzerinde.</span><span class="sxs-lookup"><span data-stu-id="4f61f-312">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="4f61f-313">Çalışma zamanı yüklerken paylaşılan bir ana bilgisayar tarafından kullanılacak bakım dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-313">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="4f61f-314">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="4f61f-315">Kümesine `true` ayrılma telemetri özelliği (değerleri `true`, `1`, veya `yes` kabul).</span><span class="sxs-lookup"><span data-stu-id="4f61f-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="4f61f-316">Aksi takdirde, kümesine `false` telemetri özelliklerini kabul etme (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="4f61f-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="4f61f-317">Varsayılan ayarlanmazsa `false` ve telemetri özellik etkin durumda.</span><span class="sxs-lookup"><span data-stu-id="4f61f-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="4f61f-318">.NET Core çalışma zamanı, paylaşılan çerçeve veya SDK olup olmadığını çözümlenen genel konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="4f61f-319">Ayarlanmazsa, varsayılan olarak, `true`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-319">If not set, it defaults to `true`.</span></span> <span data-ttu-id="4f61f-320">Kümesine `false` değil genel konumundan çözmek ve .NET Core yüklemeleri yalıtıncaya (değerleri `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="4f61f-320">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="4f61f-321">Çok düzeyli arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="4f61f-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="4f61f-322">Devre dışı bırakır podverze Top iletme, eğer ayarlanmış `0`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-322">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="4f61f-323">Daha fazla bilgi için [İleri sarmanın](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="4f61f-323">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="4f61f-324">.NET core 2.0</span><span class="sxs-lookup"><span data-stu-id="4f61f-324">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="4f61f-325">Birincil paket önbelleğini.</span><span class="sxs-lookup"><span data-stu-id="4f61f-325">The primary package cache.</span></span> <span data-ttu-id="4f61f-326">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows üzerinde.</span><span class="sxs-lookup"><span data-stu-id="4f61f-326">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="4f61f-327">Çalışma zamanı yüklerken paylaşılan bir ana bilgisayar tarafından kullanılacak bakım dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-327">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="4f61f-328">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-328">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="4f61f-329">Kümesine `true` ayrılma telemetri özelliği (değerleri `true`, `1`, veya `yes` kabul).</span><span class="sxs-lookup"><span data-stu-id="4f61f-329">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="4f61f-330">Aksi takdirde, kümesine `false` telemetri özelliklerini kabul etme (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="4f61f-330">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="4f61f-331">Varsayılan ayarlanmazsa `false` ve telemetri özellik etkin durumda.</span><span class="sxs-lookup"><span data-stu-id="4f61f-331">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="4f61f-332">.NET Core çalışma zamanı, paylaşılan çerçeve veya SDK olup olmadığını çözümlenen genel konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-332">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="4f61f-333">Ayarlanmazsa, varsayılan olarak, `true`.</span><span class="sxs-lookup"><span data-stu-id="4f61f-333">If not set, it defaults to `true`.</span></span> <span data-ttu-id="4f61f-334">Kümesine `false` değil genel konumundan çözmek ve .NET Core yüklemeleri yalıtıncaya (değerleri `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="4f61f-334">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="4f61f-335">Çok düzeyli arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="4f61f-335">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4f61f-336">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="4f61f-336">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="4f61f-337">Birincil paket önbelleğini.</span><span class="sxs-lookup"><span data-stu-id="4f61f-337">The primary package cache.</span></span> <span data-ttu-id="4f61f-338">Ayarlanmazsa, varsayılan olarak, `$HOME/.nuget/packages` UNIX üzerinde veya `%HOME%\NuGet\Packages` Windows üzerinde.</span><span class="sxs-lookup"><span data-stu-id="4f61f-338">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%HOME%\NuGet\Packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="4f61f-339">Çalışma zamanı yüklerken paylaşılan bir ana bilgisayar tarafından kullanılacak bakım dizin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-339">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="4f61f-340">.NET Core araçları kullanımıyla ilgili veriler toplanır ve Microsoft'a gönderilen olup olmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="4f61f-340">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="4f61f-341">Kümesine `true` ayrılma telemetri özelliği (değerleri `true`, `1`, veya `yes` kabul).</span><span class="sxs-lookup"><span data-stu-id="4f61f-341">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="4f61f-342">Aksi takdirde, kümesine `false` telemetri özelliklerini kabul etme (değerleri `false`, `0`, veya `no` kabul).</span><span class="sxs-lookup"><span data-stu-id="4f61f-342">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="4f61f-343">Varsayılan ayarlanmazsa `false` ve telemetri özellik etkin durumda.</span><span class="sxs-lookup"><span data-stu-id="4f61f-343">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
