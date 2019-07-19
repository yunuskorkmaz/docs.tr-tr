---
title: DotNet komutu
description: DotNet komutu (.NET Core CLI araçları için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 06/04/2018
ms.openlocfilehash: e1571bea1594b492427bdf5b3a7959733459c54e
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331014"
---
# <a name="dotnet-command"></a><span data-ttu-id="be426-103">DotNet komutu</span><span class="sxs-lookup"><span data-stu-id="be426-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="be426-104">Ad</span><span class="sxs-lookup"><span data-stu-id="be426-104">Name</span></span>

<span data-ttu-id="be426-105">`dotnet`-.NET kaynak kodu ve ikili dosyaları yönetmeye yönelik bir araç.</span><span class="sxs-lookup"><span data-stu-id="be426-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="be426-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="be426-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="be426-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="be426-107">.NET Core 2.1</span></span>](#tab/netcore21)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="be426-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="be426-108">.NET Core 2.0</span></span>](#tab/netcore20)

```
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="be426-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="be426-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet [command] [arguments] [--additionalprobingpath] [-d|--diagnostics] [--fx-version]
    [-h|--help] [--info] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="be426-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be426-110">Description</span></span>

<span data-ttu-id="be426-111">`dotnet`, .NET kaynak kodu ve ikili dosyalarını yönetmeye yönelik bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="be426-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="be426-112">[`dotnet build`](dotnet-build.md) [Ve`dotnet run`](dotnet-run.md)gibi belirli görevleri gerçekleştiren komutları açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="be426-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="be426-113">Her komut kendi bağımsız değişkenlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="be426-113">Each command defines its own arguments.</span></span> <span data-ttu-id="be426-114">Kısa `--help` yardım belgelerine erişmek için her komuttan sonra yazın.</span><span class="sxs-lookup"><span data-stu-id="be426-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="be426-115">`dotnet`, gibi bir uygulama DLL `dotnet myapp.dll`belirterek uygulamaları çalıştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be426-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="be426-116">Dağıtım seçenekleri hakkında bilgi edinmek için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="be426-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="be426-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="be426-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="be426-118">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="be426-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="be426-119">Ek *. Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="be426-119">Path to additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="be426-120">Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.</span><span class="sxs-lookup"><span data-stu-id="be426-120">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="be426-121">Tanılama çıkışını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="be426-121">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="be426-122">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="be426-122">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="be426-123">Gibi belirli bir komutun `dotnet build --help`belgelerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be426-123">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="be426-124">`dotnet --help`kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be426-124">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="be426-125">.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.</span><span class="sxs-lookup"><span data-stu-id="be426-125">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="be426-126">Yüklü .NET Core çalışma zamanlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="be426-126">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="be426-127">Yüklü .NET Core SDK 'larını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="be426-127">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="be426-128">Gerekli paylaşılan çerçeve kullanılabilir olmadığında davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="be426-128">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="be426-129">`N` aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="be426-129">`N` can be:</span></span>
* <span data-ttu-id="be426-130">`0`-Hatta ikincil sürüm iletmeyi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="be426-130">`0` - Disable even minor version roll forward.</span></span>
* <span data-ttu-id="be426-131">`1`-Önemli sürümde değil, küçük sürümde ilet.</span><span class="sxs-lookup"><span data-stu-id="be426-131">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="be426-132">Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="be426-132">This is the default behavior.</span></span>
* <span data-ttu-id="be426-133">`2`-Küçük ve büyük sürümlerde ilet.</span><span class="sxs-lookup"><span data-stu-id="be426-133">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="be426-134">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="be426-134">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="be426-135">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="be426-135">Sets the verbosity level of the command.</span></span> <span data-ttu-id="be426-136">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="be426-136">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="be426-137">Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="be426-137">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="be426-138">Kullanımda olan .NET Core SDK sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be426-138">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="be426-139">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="be426-139">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="be426-140">Ek *. Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="be426-140">Path to additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="be426-141">Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.</span><span class="sxs-lookup"><span data-stu-id="be426-141">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="be426-142">Tanılama çıkışını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="be426-142">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="be426-143">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="be426-143">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="be426-144">Gibi belirli bir komutun `dotnet build --help`belgelerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be426-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="be426-145">`dotnet --help`kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be426-145">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="be426-146">.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.</span><span class="sxs-lookup"><span data-stu-id="be426-146">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="be426-147">, Olarak `0`ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="be426-147">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="be426-148">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="be426-148">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="be426-149">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="be426-149">Sets the verbosity level of the command.</span></span> <span data-ttu-id="be426-150">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="be426-150">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="be426-151">Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="be426-151">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="be426-152">Kullanımda olan .NET Core SDK sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be426-152">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="be426-153">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="be426-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="be426-154">Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.</span><span class="sxs-lookup"><span data-stu-id="be426-154">Path containing probing policy and assemblies to probe.</span></span>

`-d|--diagnostics`

<span data-ttu-id="be426-155">Tanılama çıkışını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="be426-155">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="be426-156">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="be426-156">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="be426-157">Gibi belirli bir komutun `dotnet build --help`belgelerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be426-157">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="be426-158">`dotnet --help`kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be426-158">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="be426-159">.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.</span><span class="sxs-lookup"><span data-stu-id="be426-159">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="be426-160">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="be426-160">Sets the verbosity level of the command.</span></span> <span data-ttu-id="be426-161">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="be426-161">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="be426-162">Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="be426-162">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="be426-163">Kullanımda olan .NET Core SDK sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="be426-163">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="be426-164">dotnet komutları</span><span class="sxs-lookup"><span data-stu-id="be426-164">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="be426-165">Genel</span><span class="sxs-lookup"><span data-stu-id="be426-165">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="be426-166">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="be426-166">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="be426-167">Komut</span><span class="sxs-lookup"><span data-stu-id="be426-167">Command</span></span>                                       | <span data-ttu-id="be426-168">İşlev</span><span class="sxs-lookup"><span data-stu-id="be426-168">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="be426-169">dotnet build</span><span class="sxs-lookup"><span data-stu-id="be426-169">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="be426-170">.NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be426-170">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="be426-171">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="be426-171">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="be426-172">Bir yapı tarafından başlatılan sunucularla etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="be426-172">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="be426-173">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="be426-173">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="be426-174">Derleme çıktılarını temizle.</span><span class="sxs-lookup"><span data-stu-id="be426-174">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="be426-175">dotnet help</span><span class="sxs-lookup"><span data-stu-id="be426-175">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="be426-176">Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="be426-176">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="be426-177">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="be426-177">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="be426-178">Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="be426-178">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="be426-179">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="be426-179">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="be426-180">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="be426-180">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="be426-181">dotnet new</span><span class="sxs-lookup"><span data-stu-id="be426-181">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="be426-182">Belirli bir C# şablon F# için bir veya projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="be426-182">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="be426-183">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="be426-183">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="be426-184">Kodunuzun bir NuGet paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be426-184">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="be426-185">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="be426-185">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="be426-186">.NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="be426-186">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="be426-187">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="be426-187">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="be426-188">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="be426-188">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="be426-189">dotnet run</span><span class="sxs-lookup"><span data-stu-id="be426-189">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="be426-190">Uygulamayı kaynaktan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="be426-190">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="be426-191">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="be426-191">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="be426-192">Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="be426-192">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="be426-193">dotnet store</span><span class="sxs-lookup"><span data-stu-id="be426-193">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="be426-194">Derlemeleri çalışma zamanı paket deposunda depolar.</span><span class="sxs-lookup"><span data-stu-id="be426-194">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="be426-195">dotnet test</span><span class="sxs-lookup"><span data-stu-id="be426-195">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="be426-196">Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="be426-196">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="be426-197">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="be426-197">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="be426-198">Komut</span><span class="sxs-lookup"><span data-stu-id="be426-198">Command</span></span>                             | <span data-ttu-id="be426-199">İşlev</span><span class="sxs-lookup"><span data-stu-id="be426-199">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="be426-200">dotnet build</span><span class="sxs-lookup"><span data-stu-id="be426-200">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="be426-201">.NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be426-201">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="be426-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="be426-202">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="be426-203">Derleme çıktılarını temizle.</span><span class="sxs-lookup"><span data-stu-id="be426-203">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="be426-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="be426-204">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="be426-205">Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="be426-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="be426-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="be426-206">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="be426-207">Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="be426-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="be426-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="be426-208">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="be426-209">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="be426-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="be426-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="be426-210">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="be426-211">Belirli bir C# şablon F# için bir veya projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="be426-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="be426-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="be426-212">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="be426-213">Kodunuzun bir NuGet paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be426-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="be426-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="be426-214">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="be426-215">.NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="be426-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="be426-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="be426-216">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="be426-217">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="be426-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="be426-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="be426-218">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="be426-219">Uygulamayı kaynaktan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="be426-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="be426-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="be426-220">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="be426-221">Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="be426-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="be426-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="be426-222">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="be426-223">Derlemeleri çalışma zamanı paket deposunda depolar.</span><span class="sxs-lookup"><span data-stu-id="be426-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="be426-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="be426-224">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="be426-225">Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="be426-225">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="be426-226">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="be426-226">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="be426-227">Komut</span><span class="sxs-lookup"><span data-stu-id="be426-227">Command</span></span>                             | <span data-ttu-id="be426-228">İşlev</span><span class="sxs-lookup"><span data-stu-id="be426-228">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="be426-229">dotnet build</span><span class="sxs-lookup"><span data-stu-id="be426-229">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="be426-230">.NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be426-230">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="be426-231">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="be426-231">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="be426-232">Derleme çıktılarını temizle.</span><span class="sxs-lookup"><span data-stu-id="be426-232">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="be426-233">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="be426-233">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="be426-234">Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="be426-234">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="be426-235">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="be426-235">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="be426-236">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="be426-236">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="be426-237">dotnet new</span><span class="sxs-lookup"><span data-stu-id="be426-237">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="be426-238">Belirli bir C# şablon F# için bir veya projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="be426-238">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="be426-239">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="be426-239">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="be426-240">Kodunuzun bir NuGet paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be426-240">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="be426-241">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="be426-241">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="be426-242">.NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="be426-242">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="be426-243">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="be426-243">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="be426-244">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="be426-244">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="be426-245">dotnet run</span><span class="sxs-lookup"><span data-stu-id="be426-245">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="be426-246">Uygulamayı kaynaktan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="be426-246">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="be426-247">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="be426-247">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="be426-248">Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="be426-248">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="be426-249">dotnet test</span><span class="sxs-lookup"><span data-stu-id="be426-249">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="be426-250">Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="be426-250">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="be426-251">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="be426-251">Project references</span></span>

<span data-ttu-id="be426-252">Komut</span><span class="sxs-lookup"><span data-stu-id="be426-252">Command</span></span> | <span data-ttu-id="be426-253">İşlev</span><span class="sxs-lookup"><span data-stu-id="be426-253">Function</span></span>
--- | ---
[<span data-ttu-id="be426-254">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="be426-254">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="be426-255">Bir proje başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="be426-255">Adds a project reference.</span></span>
[<span data-ttu-id="be426-256">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="be426-256">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="be426-257">Proje başvurularını listeler.</span><span class="sxs-lookup"><span data-stu-id="be426-257">Lists project references.</span></span>
[<span data-ttu-id="be426-258">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="be426-258">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="be426-259">Proje başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="be426-259">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="be426-260">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="be426-260">NuGet packages</span></span>

<span data-ttu-id="be426-261">Komut</span><span class="sxs-lookup"><span data-stu-id="be426-261">Command</span></span> | <span data-ttu-id="be426-262">İşlev</span><span class="sxs-lookup"><span data-stu-id="be426-262">Function</span></span>
--- | ---
[<span data-ttu-id="be426-263">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="be426-263">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="be426-264">Bir NuGet paketi ekler.</span><span class="sxs-lookup"><span data-stu-id="be426-264">Adds a NuGet package.</span></span>
[<span data-ttu-id="be426-265">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="be426-265">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="be426-266">Bir NuGet paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="be426-266">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="be426-267">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="be426-267">NuGet commands</span></span>

<span data-ttu-id="be426-268">Komut</span><span class="sxs-lookup"><span data-stu-id="be426-268">Command</span></span> | <span data-ttu-id="be426-269">İşlev</span><span class="sxs-lookup"><span data-stu-id="be426-269">Function</span></span>
--- | ---
[<span data-ttu-id="be426-270">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="be426-270">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="be426-271">Sunucudan bir paketi siler veya listesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="be426-271">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="be426-272">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="be426-272">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="be426-273">Http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="be426-273">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="be426-274">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="be426-274">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="be426-275">Bir paketi sunucuya gönderir ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="be426-275">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="be426-276">Küresel araçlar komutları</span><span class="sxs-lookup"><span data-stu-id="be426-276">Global Tools commands</span></span>

<span data-ttu-id="be426-277">[.NET Core küresel araçlar](global-tools.md) .NET Core SDK 2.1.300 ile başlayarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="be426-277">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="be426-278">Komut</span><span class="sxs-lookup"><span data-stu-id="be426-278">Command</span></span> | <span data-ttu-id="be426-279">İşlev</span><span class="sxs-lookup"><span data-stu-id="be426-279">Function</span></span>
--- | ---
[<span data-ttu-id="be426-280">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="be426-280">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="be426-281">Makinenize küresel bir araç kurar.</span><span class="sxs-lookup"><span data-stu-id="be426-281">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="be426-282">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="be426-282">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="be426-283">Makinenizde varsayılan dizinde veya belirtilen yolda yüklü olan tüm genel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="be426-283">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="be426-284">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="be426-284">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="be426-285">Bir genel aracı makinenizden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="be426-285">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="be426-286">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="be426-286">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="be426-287">Makinenizde küresel bir aracı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="be426-287">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="be426-288">Ek araçlar</span><span class="sxs-lookup"><span data-stu-id="be426-288">Additional tools</span></span>

<span data-ttu-id="be426-289">.NET Core SDK 2.1.300 ' den itibaren, yalnızca kullanılarak `DotnetCliToolReference` proje bazında kullanılabilen birçok araç, .NET Core SDK bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be426-289">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="be426-290">Bu araçlar aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="be426-290">These tools are listed in the following table:</span></span>

| <span data-ttu-id="be426-291">Aracı</span><span class="sxs-lookup"><span data-stu-id="be426-291">Tool</span></span>                                              | <span data-ttu-id="be426-292">İşlev</span><span class="sxs-lookup"><span data-stu-id="be426-292">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="be426-293">geliştirme-CERT</span><span class="sxs-lookup"><span data-stu-id="be426-293">dev-certs</span></span>                                         | <span data-ttu-id="be426-294">Geliştirme sertifikaları oluşturur ve yönetir.</span><span class="sxs-lookup"><span data-stu-id="be426-294">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="be426-295">aşv</span><span class="sxs-lookup"><span data-stu-id="be426-295">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="be426-296">Komut satırı araçlarını Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="be426-296">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="be426-297">SQL-Cache</span><span class="sxs-lookup"><span data-stu-id="be426-297">sql-cache</span></span>                                         | <span data-ttu-id="be426-298">Önbellek komut satırı araçlarını SQL Server.</span><span class="sxs-lookup"><span data-stu-id="be426-298">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="be426-299">Kullanıcı gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="be426-299">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="be426-300">Geliştirme Kullanıcı gizli dizilerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="be426-300">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="be426-301">Servisi</span><span class="sxs-lookup"><span data-stu-id="be426-301">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="be426-302">Dosyalar değiştiğinde bir komutu çalıştıran bir dosya İzleyicisi başlatır.</span><span class="sxs-lookup"><span data-stu-id="be426-302">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="be426-303">Her araç hakkında daha fazla bilgi için, `dotnet <tool-name> --help`yazın.</span><span class="sxs-lookup"><span data-stu-id="be426-303">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="be426-304">Örnekler</span><span class="sxs-lookup"><span data-stu-id="be426-304">Examples</span></span>

<span data-ttu-id="be426-305">Yeni bir .NET Core konsol uygulaması oluşturur:</span><span class="sxs-lookup"><span data-stu-id="be426-305">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="be426-306">Belirli bir uygulama için bağımlılıkları geri yükle:</span><span class="sxs-lookup"><span data-stu-id="be426-306">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="be426-307">Belirli bir dizinde bir proje ve onun bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="be426-307">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="be426-308">Bir uygulama DLL 'SI çalıştırın, `myapp.dll`örneğin:</span><span class="sxs-lookup"><span data-stu-id="be426-308">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="be426-309">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="be426-309">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="be426-310">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="be426-310">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="be426-311">Genel paketler klasörü.</span><span class="sxs-lookup"><span data-stu-id="be426-311">The global packages folder.</span></span> <span data-ttu-id="be426-312">Ayarlanmamışsa, varsayılan `~/.nuget/packages` olarak UNIX veya `%userprofile%\.nuget\packages` Windows üzerinde olur.</span><span class="sxs-lookup"><span data-stu-id="be426-312">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="be426-313">Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="be426-313">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="be426-314">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be426-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="be426-315">Telemetri özelliğini `true` devre dışı bırakmak için olarak ayarlayın (değerler `true`, `1`veya `yes` kabul edildi).</span><span class="sxs-lookup"><span data-stu-id="be426-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="be426-316">Aksi takdirde, telemetri `false` özelliklerini (değerler `false`, `0`veya `no` kabul edildi) kabul etmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="be426-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="be426-317">Ayarlanmamışsa, varsayılan `false` olarak ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="be426-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="be426-318">.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be426-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="be426-319">Ayarlanmamışsa, varsayılan olarak `true`olur.</span><span class="sxs-lookup"><span data-stu-id="be426-319">If not set, it defaults to `true`.</span></span> <span data-ttu-id="be426-320">Genel konumdan `false` çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olacak şekilde ayarlayın (değerler `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="be426-320">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="be426-321">Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="be426-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="be426-322">, Olarak `0`ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="be426-322">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="be426-323">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="be426-323">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="be426-324">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="be426-324">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="be426-325">Birincil paket önbelleği.</span><span class="sxs-lookup"><span data-stu-id="be426-325">The primary package cache.</span></span> <span data-ttu-id="be426-326">Ayarlanmamışsa, varsayılan `$HOME/.nuget/packages` olarak UNIX veya `%userprofile%\.nuget\packages` Windows üzerinde olur.</span><span class="sxs-lookup"><span data-stu-id="be426-326">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="be426-327">Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="be426-327">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="be426-328">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be426-328">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="be426-329">Telemetri özelliğini `true` devre dışı bırakmak için olarak ayarlayın (değerler `true`, `1`veya `yes` kabul edildi).</span><span class="sxs-lookup"><span data-stu-id="be426-329">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="be426-330">Aksi takdirde, telemetri `false` özelliklerini (değerler `false`, `0`veya `no` kabul edildi) kabul etmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="be426-330">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="be426-331">Ayarlanmamışsa, varsayılan `false` olarak ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="be426-331">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="be426-332">.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be426-332">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="be426-333">Ayarlanmamışsa, varsayılan olarak `true`olur.</span><span class="sxs-lookup"><span data-stu-id="be426-333">If not set, it defaults to `true`.</span></span> <span data-ttu-id="be426-334">Genel konumdan `false` çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olacak şekilde ayarlayın (değerler `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="be426-334">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="be426-335">Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="be426-335">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="be426-336">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="be426-336">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="be426-337">Birincil paket önbelleği.</span><span class="sxs-lookup"><span data-stu-id="be426-337">The primary package cache.</span></span> <span data-ttu-id="be426-338">Ayarlanmamışsa, varsayılan `$HOME/.nuget/packages` olarak UNIX veya `%userprofile%\.nuget\packages` Windows üzerinde olur.</span><span class="sxs-lookup"><span data-stu-id="be426-338">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="be426-339">Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="be426-339">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="be426-340">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be426-340">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="be426-341">Telemetri özelliğini `true` devre dışı bırakmak için olarak ayarlayın (değerler `true`, `1`veya `yes` kabul edildi).</span><span class="sxs-lookup"><span data-stu-id="be426-341">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="be426-342">Aksi takdirde, telemetri `false` özelliklerini (değerler `false`, `0`veya `no` kabul edildi) kabul etmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="be426-342">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="be426-343">Ayarlanmamışsa, varsayılan `false` olarak ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="be426-343">If not set, the default is `false` and the telemetry feature is active.</span></span>

---
