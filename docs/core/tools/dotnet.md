---
title: DotNet komutu
description: DotNet komutu (.NET Core CLI araçları için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 06/04/2018
ms.openlocfilehash: 8de6a6f7e584dc472dc23d60f113b03610abb3ef
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926233"
---
# <a name="dotnet-command"></a><span data-ttu-id="511d0-103">DotNet komutu</span><span class="sxs-lookup"><span data-stu-id="511d0-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="511d0-104">Ad</span><span class="sxs-lookup"><span data-stu-id="511d0-104">Name</span></span>

<span data-ttu-id="511d0-105">`dotnet`-.NET kaynak kodu ve ikili dosyaları yönetmeye yönelik bir araç.</span><span class="sxs-lookup"><span data-stu-id="511d0-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="511d0-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="511d0-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="511d0-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="511d0-107">.NET Core 2.1</span></span>](#tab/netcore21)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="511d0-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="511d0-108">.NET Core 2.0</span></span>](#tab/netcore20)

```console
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="511d0-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="511d0-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="511d0-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="511d0-110">Description</span></span>

<span data-ttu-id="511d0-111">`dotnet`, .NET kaynak kodu ve ikili dosyalarını yönetmeye yönelik bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="511d0-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="511d0-112">[`dotnet build`](dotnet-build.md) [Ve`dotnet run`](dotnet-run.md)gibi belirli görevleri gerçekleştiren komutları açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="511d0-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="511d0-113">Her komut kendi bağımsız değişkenlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-113">Each command defines its own arguments.</span></span> <span data-ttu-id="511d0-114">Kısa `--help` yardım belgelerine erişmek için her komuttan sonra yazın.</span><span class="sxs-lookup"><span data-stu-id="511d0-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="511d0-115">`dotnet`, gibi bir uygulama DLL `dotnet myapp.dll`belirterek uygulamaları çalıştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="511d0-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="511d0-116">Dağıtım seçenekleri hakkında bilgi edinmek için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="511d0-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="511d0-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="511d0-117">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="511d0-118">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="511d0-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="511d0-119">Ek *. Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="511d0-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="511d0-120">Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.</span><span class="sxs-lookup"><span data-stu-id="511d0-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="511d0-121">Bir *Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="511d0-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="511d0-122">Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıkların, derleme bağımlılıklarının ve sürüm bilgilerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="511d0-122">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="511d0-123">Bu dosya hakkında daha fazla bilgi için bkz. GitHub üzerinde [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) .</span><span class="sxs-lookup"><span data-stu-id="511d0-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="511d0-124">Tanılama çıkışını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="511d0-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="511d0-125">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="511d0-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="511d0-126">Gibi belirli bir komutun `dotnet build --help`belgelerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="511d0-127">`dotnet --help`kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="511d0-128">.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.</span><span class="sxs-lookup"><span data-stu-id="511d0-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="511d0-129">Yüklü .NET Core çalışma zamanlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="511d0-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="511d0-130">Yüklü .NET Core SDK 'larını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="511d0-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="511d0-131">Gerekli paylaşılan çerçeve kullanılabilir olmadığında davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="511d0-132">`N` aşağıdakilerden biri olabilir:</span><span class="sxs-lookup"><span data-stu-id="511d0-132">`N` can be:</span></span>

- <span data-ttu-id="511d0-133">`0`-Hatta ikincil sürüm iletmeyi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="511d0-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="511d0-134">`1`-Önemli sürümde değil, küçük sürümde ilet.</span><span class="sxs-lookup"><span data-stu-id="511d0-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="511d0-135">Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="511d0-135">This is the default behavior.</span></span>
- <span data-ttu-id="511d0-136">`2`-Küçük ve büyük sürümlerde ilet.</span><span class="sxs-lookup"><span data-stu-id="511d0-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="511d0-137">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="511d0-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="511d0-138">*Runtimeconfig. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="511d0-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="511d0-139">*Runtimeconfig. JSON* dosyası, çalışma zamanı yapılandırma ayarlarını içeren bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="511d0-139">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="511d0-140">Daha fazla bilgi için bkz. GitHub 'da [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) .</span><span class="sxs-lookup"><span data-stu-id="511d0-140">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="511d0-141">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="511d0-142">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="511d0-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="511d0-143">Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="511d0-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="511d0-144">Kullanımda olan .NET Core SDK sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="511d0-145">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="511d0-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="511d0-146">Ek *. Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="511d0-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="511d0-147">Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.</span><span class="sxs-lookup"><span data-stu-id="511d0-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="511d0-148">Bir *Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="511d0-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="511d0-149">Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıkların, derleme bağımlılıklarının ve sürüm bilgilerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="511d0-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="511d0-150">Bu dosya hakkında daha fazla bilgi için bkz. [GitHub üzerinde çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="511d0-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="511d0-151">Tanılama çıkışını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="511d0-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="511d0-152">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="511d0-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="511d0-153">Gibi belirli bir komutun `dotnet build --help`belgelerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="511d0-154">`dotnet --help`kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="511d0-155">.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.</span><span class="sxs-lookup"><span data-stu-id="511d0-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="511d0-156">, Olarak `0`ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="511d0-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="511d0-157">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="511d0-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="511d0-158">*Runtimeconfig. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="511d0-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="511d0-159">*Runtimeconfig. JSON* dosyası, çalışma zamanı yapılandırma ayarlarını içeren bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="511d0-159">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="511d0-160">Daha ayrıntılı bilgi için bkz. [GitHub 'Da çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="511d0-160">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="511d0-161">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="511d0-162">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="511d0-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="511d0-163">Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="511d0-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="511d0-164">Kullanımda olan .NET Core SDK sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="511d0-165">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="511d0-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="511d0-166">Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.</span><span class="sxs-lookup"><span data-stu-id="511d0-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="511d0-167">Bir *Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="511d0-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="511d0-168">Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıkların, derleme bağımlılıklarının ve sürüm bilgilerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="511d0-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="511d0-169">Bu dosya hakkında daha fazla bilgi için bkz. [GitHub üzerinde çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="511d0-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="511d0-170">Tanılama çıkışını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="511d0-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="511d0-171">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="511d0-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="511d0-172">Gibi belirli bir komutun `dotnet build --help`belgelerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="511d0-173">`dotnet --help`kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="511d0-174">.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.</span><span class="sxs-lookup"><span data-stu-id="511d0-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="511d0-175">*Runtimeconfig. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="511d0-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="511d0-176">*Runtimeconfig. JSON* dosyası, çalışma zamanı yapılandırma ayarlarını içeren bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="511d0-176">A *runtimeconfig.json* file is a configuration file containing runtime configuration settings.</span></span> <span data-ttu-id="511d0-177">Daha ayrıntılı bilgi için bkz. [GitHub 'Da çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="511d0-177">For more details, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="511d0-178">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="511d0-179">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="511d0-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="511d0-180">Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="511d0-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="511d0-181">Kullanımda olan .NET Core SDK sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="511d0-182">dotnet komutları</span><span class="sxs-lookup"><span data-stu-id="511d0-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="511d0-183">Genel</span><span class="sxs-lookup"><span data-stu-id="511d0-183">General</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="511d0-184">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="511d0-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="511d0-185">Komut</span><span class="sxs-lookup"><span data-stu-id="511d0-185">Command</span></span>                                       | <span data-ttu-id="511d0-186">İşlev</span><span class="sxs-lookup"><span data-stu-id="511d0-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="511d0-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="511d0-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="511d0-188">.NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="511d0-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="511d0-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="511d0-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="511d0-190">Bir yapı tarafından başlatılan sunucularla etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="511d0-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="511d0-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="511d0-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="511d0-192">Derleme çıktılarını temizle.</span><span class="sxs-lookup"><span data-stu-id="511d0-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="511d0-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="511d0-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="511d0-194">Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="511d0-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="511d0-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="511d0-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="511d0-196">Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="511d0-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="511d0-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="511d0-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="511d0-198">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="511d0-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="511d0-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="511d0-200">Belirli bir C# şablon F# için bir veya projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="511d0-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="511d0-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="511d0-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="511d0-202">Kodunuzun bir NuGet paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="511d0-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="511d0-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="511d0-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="511d0-204">.NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="511d0-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="511d0-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="511d0-206">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="511d0-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="511d0-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="511d0-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="511d0-208">Uygulamayı kaynaktan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="511d0-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="511d0-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="511d0-210">Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="511d0-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="511d0-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="511d0-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="511d0-212">Derlemeleri çalışma zamanı paket deposunda depolar.</span><span class="sxs-lookup"><span data-stu-id="511d0-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="511d0-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="511d0-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="511d0-214">Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="511d0-215">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="511d0-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="511d0-216">Komut</span><span class="sxs-lookup"><span data-stu-id="511d0-216">Command</span></span>                             | <span data-ttu-id="511d0-217">İşlev</span><span class="sxs-lookup"><span data-stu-id="511d0-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="511d0-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="511d0-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="511d0-219">.NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="511d0-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="511d0-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="511d0-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="511d0-221">Derleme çıktılarını temizle.</span><span class="sxs-lookup"><span data-stu-id="511d0-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="511d0-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="511d0-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="511d0-223">Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="511d0-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="511d0-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="511d0-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="511d0-225">Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="511d0-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="511d0-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="511d0-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="511d0-227">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="511d0-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="511d0-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="511d0-229">Belirli bir C# şablon F# için bir veya projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="511d0-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="511d0-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="511d0-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="511d0-231">Kodunuzun bir NuGet paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="511d0-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="511d0-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="511d0-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="511d0-233">.NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="511d0-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="511d0-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="511d0-235">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="511d0-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="511d0-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="511d0-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="511d0-237">Uygulamayı kaynaktan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="511d0-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="511d0-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="511d0-239">Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="511d0-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="511d0-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="511d0-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="511d0-241">Derlemeleri çalışma zamanı paket deposunda depolar.</span><span class="sxs-lookup"><span data-stu-id="511d0-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="511d0-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="511d0-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="511d0-243">Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="511d0-244">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="511d0-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="511d0-245">Komut</span><span class="sxs-lookup"><span data-stu-id="511d0-245">Command</span></span>                             | <span data-ttu-id="511d0-246">İşlev</span><span class="sxs-lookup"><span data-stu-id="511d0-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="511d0-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="511d0-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="511d0-248">.NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="511d0-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="511d0-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="511d0-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="511d0-250">Derleme çıktılarını temizle.</span><span class="sxs-lookup"><span data-stu-id="511d0-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="511d0-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="511d0-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="511d0-252">Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="511d0-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="511d0-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="511d0-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="511d0-254">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="511d0-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="511d0-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="511d0-256">Belirli bir C# şablon F# için bir veya projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="511d0-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="511d0-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="511d0-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="511d0-258">Kodunuzun bir NuGet paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="511d0-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="511d0-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="511d0-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="511d0-260">.NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="511d0-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="511d0-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="511d0-262">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="511d0-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="511d0-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="511d0-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="511d0-264">Uygulamayı kaynaktan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="511d0-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="511d0-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="511d0-266">Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="511d0-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="511d0-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="511d0-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="511d0-268">Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="511d0-269">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="511d0-269">Project references</span></span>

<span data-ttu-id="511d0-270">Komut</span><span class="sxs-lookup"><span data-stu-id="511d0-270">Command</span></span> | <span data-ttu-id="511d0-271">İşlev</span><span class="sxs-lookup"><span data-stu-id="511d0-271">Function</span></span>
--- | ---
[<span data-ttu-id="511d0-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="511d0-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="511d0-273">Bir proje başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="511d0-273">Adds a project reference.</span></span>
[<span data-ttu-id="511d0-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="511d0-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="511d0-275">Proje başvurularını listeler.</span><span class="sxs-lookup"><span data-stu-id="511d0-275">Lists project references.</span></span>
[<span data-ttu-id="511d0-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="511d0-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="511d0-277">Proje başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="511d0-278">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="511d0-278">NuGet packages</span></span>

<span data-ttu-id="511d0-279">Komut</span><span class="sxs-lookup"><span data-stu-id="511d0-279">Command</span></span> | <span data-ttu-id="511d0-280">İşlev</span><span class="sxs-lookup"><span data-stu-id="511d0-280">Function</span></span>
--- | ---
[<span data-ttu-id="511d0-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="511d0-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="511d0-282">Bir NuGet paketi ekler.</span><span class="sxs-lookup"><span data-stu-id="511d0-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="511d0-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="511d0-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="511d0-284">Bir NuGet paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="511d0-285">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="511d0-285">NuGet commands</span></span>

<span data-ttu-id="511d0-286">Komut</span><span class="sxs-lookup"><span data-stu-id="511d0-286">Command</span></span> | <span data-ttu-id="511d0-287">İşlev</span><span class="sxs-lookup"><span data-stu-id="511d0-287">Function</span></span>
--- | ---
[<span data-ttu-id="511d0-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="511d0-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="511d0-289">Sunucudan bir paketi siler veya listesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="511d0-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="511d0-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="511d0-291">Http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="511d0-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="511d0-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="511d0-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="511d0-293">Bir paketi sunucuya gönderir ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="511d0-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tools-commands"></a><span data-ttu-id="511d0-294">Küresel araçlar komutları</span><span class="sxs-lookup"><span data-stu-id="511d0-294">Global Tools commands</span></span>

<span data-ttu-id="511d0-295">[.NET Core küresel araçlar](global-tools.md) .NET Core SDK 2.1.300 ile başlayarak kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="511d0-295">[.NET Core Global Tools](global-tools.md) are available starting with .NET Core SDK 2.1.300:</span></span>

<span data-ttu-id="511d0-296">Komut</span><span class="sxs-lookup"><span data-stu-id="511d0-296">Command</span></span> | <span data-ttu-id="511d0-297">İşlev</span><span class="sxs-lookup"><span data-stu-id="511d0-297">Function</span></span>
--- | ---
[<span data-ttu-id="511d0-298">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="511d0-298">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="511d0-299">Makinenize küresel bir araç kurar.</span><span class="sxs-lookup"><span data-stu-id="511d0-299">Installs a Global Tool on your machine.</span></span>
[<span data-ttu-id="511d0-300">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="511d0-300">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="511d0-301">Makinenizde varsayılan dizinde veya belirtilen yolda yüklü olan tüm genel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="511d0-301">Lists all Global Tools currently installed in the default directory on your machine or in the specified path.</span></span>
[<span data-ttu-id="511d0-302">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="511d0-302">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="511d0-303">Bir genel aracı makinenizden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="511d0-303">Uninstalls a Global Tool from your machine.</span></span>
[<span data-ttu-id="511d0-304">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="511d0-304">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="511d0-305">Makinenizde küresel bir aracı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="511d0-305">Updates a Global Tool on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="511d0-306">Ek araçlar</span><span class="sxs-lookup"><span data-stu-id="511d0-306">Additional tools</span></span>

<span data-ttu-id="511d0-307">.NET Core SDK 2.1.300 ' den itibaren, yalnızca kullanılarak `DotnetCliToolReference` proje bazında kullanılabilen birçok araç, .NET Core SDK bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="511d0-307">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="511d0-308">Bu araçlar aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="511d0-308">These tools are listed in the following table:</span></span>

| <span data-ttu-id="511d0-309">Aracı</span><span class="sxs-lookup"><span data-stu-id="511d0-309">Tool</span></span>                                              | <span data-ttu-id="511d0-310">İşlev</span><span class="sxs-lookup"><span data-stu-id="511d0-310">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="511d0-311">geliştirme-CERT</span><span class="sxs-lookup"><span data-stu-id="511d0-311">dev-certs</span></span>                                         | <span data-ttu-id="511d0-312">Geliştirme sertifikaları oluşturur ve yönetir.</span><span class="sxs-lookup"><span data-stu-id="511d0-312">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="511d0-313">aşv</span><span class="sxs-lookup"><span data-stu-id="511d0-313">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="511d0-314">Komut satırı araçlarını Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="511d0-314">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="511d0-315">SQL-Cache</span><span class="sxs-lookup"><span data-stu-id="511d0-315">sql-cache</span></span>                                         | <span data-ttu-id="511d0-316">Önbellek komut satırı araçlarını SQL Server.</span><span class="sxs-lookup"><span data-stu-id="511d0-316">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="511d0-317">Kullanıcı gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="511d0-317">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="511d0-318">Geliştirme Kullanıcı gizli dizilerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="511d0-318">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="511d0-319">Servisi</span><span class="sxs-lookup"><span data-stu-id="511d0-319">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="511d0-320">Dosyalar değiştiğinde bir komutu çalıştıran bir dosya İzleyicisi başlatır.</span><span class="sxs-lookup"><span data-stu-id="511d0-320">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="511d0-321">Her araç hakkında daha fazla bilgi için, `dotnet <tool-name> --help`yazın.</span><span class="sxs-lookup"><span data-stu-id="511d0-321">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="511d0-322">Örnekler</span><span class="sxs-lookup"><span data-stu-id="511d0-322">Examples</span></span>

<span data-ttu-id="511d0-323">Yeni bir .NET Core konsol uygulaması oluşturur:</span><span class="sxs-lookup"><span data-stu-id="511d0-323">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="511d0-324">Belirli bir uygulama için bağımlılıkları geri yükle:</span><span class="sxs-lookup"><span data-stu-id="511d0-324">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="511d0-325">Belirli bir dizinde bir proje ve onun bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="511d0-325">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="511d0-326">Bir uygulama DLL 'SI çalıştırın, `myapp.dll`örneğin:</span><span class="sxs-lookup"><span data-stu-id="511d0-326">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="511d0-327">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="511d0-327">Environment variables</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="511d0-328">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="511d0-328">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="511d0-329">Genel paketler klasörü.</span><span class="sxs-lookup"><span data-stu-id="511d0-329">The global packages folder.</span></span> <span data-ttu-id="511d0-330">Ayarlanmamışsa, varsayılan `~/.nuget/packages` olarak UNIX veya `%userprofile%\.nuget\packages` Windows üzerinde olur.</span><span class="sxs-lookup"><span data-stu-id="511d0-330">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="511d0-331">Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="511d0-331">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="511d0-332">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="511d0-332">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="511d0-333">Telemetri özelliğini `true` devre dışı bırakmak için olarak ayarlayın (değerler `true`, `1`veya `yes` kabul edildi).</span><span class="sxs-lookup"><span data-stu-id="511d0-333">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="511d0-334">Aksi takdirde, telemetri `false` özelliklerini (değerler `false`, `0`veya `no` kabul edildi) kabul etmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="511d0-334">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="511d0-335">Ayarlanmamışsa, varsayılan `false` olarak ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="511d0-335">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="511d0-336">.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="511d0-336">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="511d0-337">Ayarlanmamışsa, varsayılan olarak `true`olur.</span><span class="sxs-lookup"><span data-stu-id="511d0-337">If not set, it defaults to `true`.</span></span> <span data-ttu-id="511d0-338">Genel konumdan `false` çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olacak şekilde ayarlayın (değerler `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="511d0-338">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="511d0-339">Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="511d0-339">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="511d0-340">, Olarak `0`ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="511d0-340">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="511d0-341">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="511d0-341">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="511d0-342">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="511d0-342">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="511d0-343">Birincil paket önbelleği.</span><span class="sxs-lookup"><span data-stu-id="511d0-343">The primary package cache.</span></span> <span data-ttu-id="511d0-344">Ayarlanmamışsa, varsayılan `$HOME/.nuget/packages` olarak UNIX veya `%userprofile%\.nuget\packages` Windows üzerinde olur.</span><span class="sxs-lookup"><span data-stu-id="511d0-344">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="511d0-345">Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="511d0-345">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="511d0-346">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="511d0-346">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="511d0-347">Telemetri özelliğini `true` devre dışı bırakmak için olarak ayarlayın (değerler `true`, `1`veya `yes` kabul edildi).</span><span class="sxs-lookup"><span data-stu-id="511d0-347">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="511d0-348">Aksi takdirde, telemetri `false` özelliklerini (değerler `false`, `0`veya `no` kabul edildi) kabul etmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="511d0-348">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="511d0-349">Ayarlanmamışsa, varsayılan `false` olarak ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="511d0-349">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="511d0-350">.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="511d0-350">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="511d0-351">Ayarlanmamışsa, varsayılan olarak `true`olur.</span><span class="sxs-lookup"><span data-stu-id="511d0-351">If not set, it defaults to `true`.</span></span> <span data-ttu-id="511d0-352">Genel konumdan `false` çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olacak şekilde ayarlayın (değerler `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="511d0-352">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="511d0-353">Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="511d0-353">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="511d0-354">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="511d0-354">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="511d0-355">Birincil paket önbelleği.</span><span class="sxs-lookup"><span data-stu-id="511d0-355">The primary package cache.</span></span> <span data-ttu-id="511d0-356">Ayarlanmamışsa, varsayılan `$HOME/.nuget/packages` olarak UNIX veya `%userprofile%\.nuget\packages` Windows üzerinde olur.</span><span class="sxs-lookup"><span data-stu-id="511d0-356">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="511d0-357">Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="511d0-357">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="511d0-358">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="511d0-358">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="511d0-359">Telemetri özelliğini `true` devre dışı bırakmak için olarak ayarlayın (değerler `true`, `1`veya `yes` kabul edildi).</span><span class="sxs-lookup"><span data-stu-id="511d0-359">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="511d0-360">Aksi takdirde, telemetri `false` özelliklerini (değerler `false`, `0`veya `no` kabul edildi) kabul etmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="511d0-360">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="511d0-361">Ayarlanmamışsa, varsayılan `false` olarak ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="511d0-361">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="511d0-362">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="511d0-362">See also</span></span>

- [<span data-ttu-id="511d0-363">Çalışma zamanı yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="511d0-363">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
