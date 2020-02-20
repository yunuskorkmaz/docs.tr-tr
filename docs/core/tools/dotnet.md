---
title: DotNet komutu
description: DotNet komutu (.NET Core CLI için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 02/13/2020
ms.openlocfilehash: 364978465b63401907b46ead64dbceb2f15c8169
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77451174"
---
# <a name="dotnet-command"></a><span data-ttu-id="0e814-103">DotNet komutu</span><span class="sxs-lookup"><span data-stu-id="0e814-103">dotnet command</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0e814-104">Name</span><span class="sxs-lookup"><span data-stu-id="0e814-104">Name</span></span>

<span data-ttu-id="0e814-105">`dotnet`-.NET kaynak kodu ve ikili dosyaları yönetmeye yönelik bir araç.</span><span class="sxs-lookup"><span data-stu-id="0e814-105">`dotnet` - A tool for managing .NET source code and binaries.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0e814-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="0e814-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21"></a>[<span data-ttu-id="0e814-107">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0e814-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--list-runtimes] [--list-sdks] [--roll-forward-on-no-candidate-fx] [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-20"></a>[<span data-ttu-id="0e814-108">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="0e814-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet [command] [arguments] [--additional-deps] [--additionalprobingpath] [--depsfile]
    [-d|--diagnostics] [--fx-version] [-h|--help] [--info] [--roll-forward-on-no-candidate-fx]
    [--runtimeconfig] [-v|--verbosity] [--version]
```

# <a name="net-core-1x"></a>[<span data-ttu-id="0e814-109">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="0e814-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet [command] [arguments] [--additionalprobingpath] [--depsfile] [-d|--diagnostics]
    [--fx-version] [-h|--help] [--info] [--runtimeconfig] [-v|--verbosity] [--version]
```

---

## <a name="description"></a><span data-ttu-id="0e814-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0e814-110">Description</span></span>

<span data-ttu-id="0e814-111">`dotnet` .NET kaynak kodu ve ikili dosyalarını yönetmeye yönelik bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="0e814-111">`dotnet` is a tool for managing .NET source code and binaries.</span></span> <span data-ttu-id="0e814-112">[`dotnet build`](dotnet-build.md) ve [`dotnet run`](dotnet-run.md)gibi belirli görevleri gerçekleştiren komutları açığa çıkarır.</span><span class="sxs-lookup"><span data-stu-id="0e814-112">It exposes commands that perform specific tasks, such as [`dotnet build`](dotnet-build.md) and [`dotnet run`](dotnet-run.md).</span></span> <span data-ttu-id="0e814-113">Her komut kendi bağımsız değişkenlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-113">Each command defines its own arguments.</span></span> <span data-ttu-id="0e814-114">Kısa yardım belgelerine erişmek için her komuttan sonra `--help` yazın.</span><span class="sxs-lookup"><span data-stu-id="0e814-114">Type `--help` after each command to access brief help documentation.</span></span>

<span data-ttu-id="0e814-115">`dotnet`, `dotnet myapp.dll`gibi bir uygulama DLL belirterek uygulamaları çalıştırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e814-115">`dotnet` can be used to run applications, by specifying an application DLL, such as `dotnet myapp.dll`.</span></span> <span data-ttu-id="0e814-116">Dağıtım seçenekleri hakkında bilgi edinmek için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="0e814-116">See [.NET Core application deployment](../deploying/index.md) for to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="0e814-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0e814-117">Options</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="0e814-118">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0e814-118">.NET Core 2.1</span></span>](#tab/netcore21)

`--additional-deps <PATH>`

<span data-ttu-id="0e814-119">Ek *. Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="0e814-119">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="0e814-120">Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.</span><span class="sxs-lookup"><span data-stu-id="0e814-120">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="0e814-121">Bir *Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="0e814-121">Path to a *deps.json* file.</span></span>

<span data-ttu-id="0e814-122">Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıklar, derleme bağımlılıkları ve sürüm bilgilerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0e814-122">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="0e814-123">Bu dosya hakkında daha fazla bilgi için bkz. GitHub üzerinde [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) .</span><span class="sxs-lookup"><span data-stu-id="0e814-123">For more information about this file, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

`-d|--diagnostics`

<span data-ttu-id="0e814-124">Tanılama çıkışını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0e814-124">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="0e814-125">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="0e814-125">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="0e814-126">`dotnet build --help`gibi belirli bir komutun belgelerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-126">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="0e814-127">`dotnet --help`, kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-127">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="0e814-128">.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.</span><span class="sxs-lookup"><span data-stu-id="0e814-128">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--list-runtimes`

<span data-ttu-id="0e814-129">Yüklü .NET Core çalışma zamanlarını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0e814-129">Displays the installed .NET Core runtimes.</span></span>

`--list-sdks`

<span data-ttu-id="0e814-130">Yüklü .NET Core SDK 'larını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0e814-130">Displays the installed .NET Core SDKs.</span></span>

`--roll-forward-on-no-candidate-fx <N>`

<span data-ttu-id="0e814-131">Gerekli paylaşılan çerçeve kullanılabilir olmadığında davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-131">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="0e814-132">`N` şu olabilir:</span><span class="sxs-lookup"><span data-stu-id="0e814-132">`N` can be:</span></span>

- <span data-ttu-id="0e814-133">`0`-alt düzey sürüm iletmeyi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="0e814-133">`0` - Disable even minor version roll forward.</span></span>
- <span data-ttu-id="0e814-134">`1`-önemli sürümde değil, küçük sürümde ilet.</span><span class="sxs-lookup"><span data-stu-id="0e814-134">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="0e814-135">Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="0e814-135">This is the default behavior.</span></span>
- <span data-ttu-id="0e814-136">`2`-küçük ve büyük sürümlerde ilet.</span><span class="sxs-lookup"><span data-stu-id="0e814-136">`2` - Roll forward on minor and major versions.</span></span>

 <span data-ttu-id="0e814-137">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0e814-137">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="0e814-138">*Runtimeconfig. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="0e814-138">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="0e814-139">*Runtimeconfig. JSON* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="0e814-139">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="0e814-140">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="0e814-140">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="0e814-141">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0e814-142">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0e814-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0e814-143">Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="0e814-143">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="0e814-144">Kullanımda olan .NET Core SDK sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-144">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="0e814-145">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="0e814-145">.NET Core 2.0</span></span>](#tab/netcore20)

`--additional-deps <PATH>`

<span data-ttu-id="0e814-146">Ek *. Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="0e814-146">Path to an additional *.deps.json* file.</span></span>

`--additionalprobingpath <PATH>`

<span data-ttu-id="0e814-147">Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.</span><span class="sxs-lookup"><span data-stu-id="0e814-147">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="0e814-148">Bir *Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="0e814-148">Path to a *deps.json* file.</span></span>

<span data-ttu-id="0e814-149">Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıkların, derleme bağımlılıklarının ve sürüm bilgilerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0e814-149">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="0e814-150">Bu dosya hakkında daha fazla bilgi için bkz. [GitHub üzerinde çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="0e814-150">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="0e814-151">Tanılama çıkışını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0e814-151">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="0e814-152">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="0e814-152">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="0e814-153">`dotnet build --help`gibi belirli bir komutun belgelerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-153">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="0e814-154">`dotnet --help`, kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-154">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="0e814-155">.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.</span><span class="sxs-lookup"><span data-stu-id="0e814-155">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--roll-forward-on-no-candidate-fx`

 <span data-ttu-id="0e814-156">`0`olarak ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="0e814-156">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="0e814-157">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0e814-157">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

`--runtimeconfig`

<span data-ttu-id="0e814-158">*Runtimeconfig. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="0e814-158">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="0e814-159">*Runtimeconfig. JSON* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="0e814-159">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="0e814-160">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="0e814-160">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="0e814-161">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-161">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0e814-162">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0e814-162">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0e814-163">Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="0e814-163">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="0e814-164">Kullanımda olan .NET Core SDK sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-164">Prints out the version of the .NET Core SDK in use.</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="0e814-165">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="0e814-165">.NET Core 1.x</span></span>](#tab/netcore1x)

`--additionalprobingpath <PATH>`

<span data-ttu-id="0e814-166">Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.</span><span class="sxs-lookup"><span data-stu-id="0e814-166">Path containing probing policy and assemblies to probe.</span></span>

`--depsfile`

<span data-ttu-id="0e814-167">Bir *Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="0e814-167">Path to a *deps.json* file.</span></span>

<span data-ttu-id="0e814-168">Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıkların, derleme bağımlılıklarının ve sürüm bilgilerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="0e814-168">A *deps.json* file contains a list of dependencies, compilation dependencies and version information used to address assembly conflicts.</span></span> <span data-ttu-id="0e814-169">Bu dosya hakkında daha fazla bilgi için bkz. [GitHub üzerinde çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span><span class="sxs-lookup"><span data-stu-id="0e814-169">For more details on this file, see [Runtime Configuration Files on GitHub](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md).</span></span>

`-d|--diagnostics`

<span data-ttu-id="0e814-170">Tanılama çıkışını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="0e814-170">Enables diagnostic output.</span></span>

`--fx-version <VERSION>`

<span data-ttu-id="0e814-171">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="0e814-171">Version of the .NET Core runtime to use to run the application.</span></span>

`-h|--help`

<span data-ttu-id="0e814-172">`dotnet build --help`gibi belirli bir komutun belgelerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-172">Prints out documentation for a given command, such as `dotnet build --help`.</span></span> <span data-ttu-id="0e814-173">`dotnet --help`, kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-173">`dotnet --help` prints a list of available commands.</span></span>

`--info`

<span data-ttu-id="0e814-174">.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.</span><span class="sxs-lookup"><span data-stu-id="0e814-174">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

`--runtimeconfig`

<span data-ttu-id="0e814-175">*Runtimeconfig. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="0e814-175">Path to a *runtimeconfig.json* file.</span></span>

<span data-ttu-id="0e814-176">*Runtimeconfig. JSON* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="0e814-176">A *runtimeconfig.json* file is a configuration file containing run-time settings.</span></span> <span data-ttu-id="0e814-177">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="0e814-177">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="0e814-178">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-178">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0e814-179">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0e814-179">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0e814-180">Her komutta desteklenmez; Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="0e814-180">Not supported in every command; see specific command page to determine if this option is available.</span></span>

`--version`

<span data-ttu-id="0e814-181">Kullanımda olan .NET Core SDK sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-181">Prints out the version of the .NET Core SDK in use.</span></span>

---

## <a name="dotnet-commands"></a><span data-ttu-id="0e814-182">dotnet komutları</span><span class="sxs-lookup"><span data-stu-id="0e814-182">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="0e814-183">Genel</span><span class="sxs-lookup"><span data-stu-id="0e814-183">General</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="0e814-184">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0e814-184">.NET Core 2.1</span></span>](#tab/netcore21)

| <span data-ttu-id="0e814-185">Komut</span><span class="sxs-lookup"><span data-stu-id="0e814-185">Command</span></span>                                       | <span data-ttu-id="0e814-186">İşlev</span><span class="sxs-lookup"><span data-stu-id="0e814-186">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="0e814-187">dotnet build</span><span class="sxs-lookup"><span data-stu-id="0e814-187">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="0e814-188">.NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e814-188">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="0e814-189">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="0e814-189">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="0e814-190">Bir yapı tarafından başlatılan sunucularla etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="0e814-190">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="0e814-191">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="0e814-191">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="0e814-192">Derleme çıktılarını temizle.</span><span class="sxs-lookup"><span data-stu-id="0e814-192">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="0e814-193">dotnet help</span><span class="sxs-lookup"><span data-stu-id="0e814-193">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="0e814-194">Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e814-194">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="0e814-195">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="0e814-195">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="0e814-196">Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="0e814-196">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="0e814-197">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="0e814-197">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="0e814-198">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-198">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="0e814-199">dotnet new</span><span class="sxs-lookup"><span data-stu-id="0e814-199">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="0e814-200">Belirli bir C# şablon F# için bir veya projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="0e814-200">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="0e814-201">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="0e814-201">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="0e814-202">Kodunuzun bir NuGet paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e814-202">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="0e814-203">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="0e814-203">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="0e814-204">.NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-204">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="0e814-205">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="0e814-205">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="0e814-206">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="0e814-206">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="0e814-207">dotnet run</span><span class="sxs-lookup"><span data-stu-id="0e814-207">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="0e814-208">Uygulamayı kaynaktan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-208">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="0e814-209">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="0e814-209">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="0e814-210">Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="0e814-210">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="0e814-211">dotnet store</span><span class="sxs-lookup"><span data-stu-id="0e814-211">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="0e814-212">Derlemeleri çalışma zamanı paket deposunda depolar.</span><span class="sxs-lookup"><span data-stu-id="0e814-212">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="0e814-213">dotnet test</span><span class="sxs-lookup"><span data-stu-id="0e814-213">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="0e814-214">Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-214">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-20"></a>[<span data-ttu-id="0e814-215">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="0e814-215">.NET Core 2.0</span></span>](#tab/netcore20)

| <span data-ttu-id="0e814-216">Komut</span><span class="sxs-lookup"><span data-stu-id="0e814-216">Command</span></span>                             | <span data-ttu-id="0e814-217">İşlev</span><span class="sxs-lookup"><span data-stu-id="0e814-217">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="0e814-218">dotnet build</span><span class="sxs-lookup"><span data-stu-id="0e814-218">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="0e814-219">.NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e814-219">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="0e814-220">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="0e814-220">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="0e814-221">Derleme çıktılarını temizle.</span><span class="sxs-lookup"><span data-stu-id="0e814-221">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="0e814-222">dotnet help</span><span class="sxs-lookup"><span data-stu-id="0e814-222">dotnet help</span></span>](dotnet-help.md)       | <span data-ttu-id="0e814-223">Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e814-223">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="0e814-224">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="0e814-224">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="0e814-225">Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="0e814-225">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="0e814-226">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="0e814-226">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="0e814-227">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-227">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="0e814-228">dotnet new</span><span class="sxs-lookup"><span data-stu-id="0e814-228">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="0e814-229">Belirli bir C# şablon F# için bir veya projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="0e814-229">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="0e814-230">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="0e814-230">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="0e814-231">Kodunuzun bir NuGet paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e814-231">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="0e814-232">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="0e814-232">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="0e814-233">.NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-233">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="0e814-234">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="0e814-234">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="0e814-235">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="0e814-235">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="0e814-236">dotnet run</span><span class="sxs-lookup"><span data-stu-id="0e814-236">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="0e814-237">Uygulamayı kaynaktan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-237">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="0e814-238">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="0e814-238">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="0e814-239">Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="0e814-239">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="0e814-240">dotnet store</span><span class="sxs-lookup"><span data-stu-id="0e814-240">dotnet store</span></span>](dotnet-store.md)     | <span data-ttu-id="0e814-241">Derlemeleri çalışma zamanı paket deposunda depolar.</span><span class="sxs-lookup"><span data-stu-id="0e814-241">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="0e814-242">dotnet test</span><span class="sxs-lookup"><span data-stu-id="0e814-242">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="0e814-243">Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-243">Runs tests using a test runner.</span></span>                                     |

# <a name="net-core-1x"></a>[<span data-ttu-id="0e814-244">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="0e814-244">.NET Core 1.x</span></span>](#tab/netcore1x)

| <span data-ttu-id="0e814-245">Komut</span><span class="sxs-lookup"><span data-stu-id="0e814-245">Command</span></span>                             | <span data-ttu-id="0e814-246">İşlev</span><span class="sxs-lookup"><span data-stu-id="0e814-246">Function</span></span>                                                            |
| ----------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="0e814-247">dotnet build</span><span class="sxs-lookup"><span data-stu-id="0e814-247">dotnet build</span></span>](dotnet-build.md)     | <span data-ttu-id="0e814-248">.NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e814-248">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="0e814-249">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="0e814-249">dotnet clean</span></span>](dotnet-clean.md)     | <span data-ttu-id="0e814-250">Derleme çıktılarını temizle.</span><span class="sxs-lookup"><span data-stu-id="0e814-250">Clean build outputs.</span></span>                                              |
| [<span data-ttu-id="0e814-251">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="0e814-251">dotnet migrate</span></span>](dotnet-migrate.md) | <span data-ttu-id="0e814-252">Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="0e814-252">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="0e814-253">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="0e814-253">dotnet msbuild</span></span>](dotnet-msbuild.md) | <span data-ttu-id="0e814-254">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-254">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="0e814-255">dotnet new</span><span class="sxs-lookup"><span data-stu-id="0e814-255">dotnet new</span></span>](dotnet-new.md)         | <span data-ttu-id="0e814-256">Belirli bir C# şablon F# için bir veya projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="0e814-256">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="0e814-257">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="0e814-257">dotnet pack</span></span>](dotnet-pack.md)       | <span data-ttu-id="0e814-258">Kodunuzun bir NuGet paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e814-258">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="0e814-259">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="0e814-259">dotnet publish</span></span>](dotnet-publish.md) | <span data-ttu-id="0e814-260">.NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-260">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="0e814-261">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="0e814-261">dotnet restore</span></span>](dotnet-restore.md) | <span data-ttu-id="0e814-262">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="0e814-262">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="0e814-263">dotnet run</span><span class="sxs-lookup"><span data-stu-id="0e814-263">dotnet run</span></span>](dotnet-run.md)         | <span data-ttu-id="0e814-264">Uygulamayı kaynaktan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-264">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="0e814-265">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="0e814-265">dotnet sln</span></span>](dotnet-sln.md)         | <span data-ttu-id="0e814-266">Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="0e814-266">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="0e814-267">dotnet test</span><span class="sxs-lookup"><span data-stu-id="0e814-267">dotnet test</span></span>](dotnet-test.md)       | <span data-ttu-id="0e814-268">Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-268">Runs tests using a test runner.</span></span>                                     |

---

### <a name="project-references"></a><span data-ttu-id="0e814-269">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="0e814-269">Project references</span></span>

<span data-ttu-id="0e814-270">Komut</span><span class="sxs-lookup"><span data-stu-id="0e814-270">Command</span></span> | <span data-ttu-id="0e814-271">İşlev</span><span class="sxs-lookup"><span data-stu-id="0e814-271">Function</span></span>
--- | ---
[<span data-ttu-id="0e814-272">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="0e814-272">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="0e814-273">Bir proje başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="0e814-273">Adds a project reference.</span></span>
[<span data-ttu-id="0e814-274">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="0e814-274">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="0e814-275">Proje başvurularını listeler.</span><span class="sxs-lookup"><span data-stu-id="0e814-275">Lists project references.</span></span>
[<span data-ttu-id="0e814-276">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="0e814-276">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="0e814-277">Proje başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-277">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="0e814-278">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="0e814-278">NuGet packages</span></span>

<span data-ttu-id="0e814-279">Komut</span><span class="sxs-lookup"><span data-stu-id="0e814-279">Command</span></span> | <span data-ttu-id="0e814-280">İşlev</span><span class="sxs-lookup"><span data-stu-id="0e814-280">Function</span></span>
--- | ---
[<span data-ttu-id="0e814-281">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="0e814-281">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="0e814-282">Bir NuGet paketi ekler.</span><span class="sxs-lookup"><span data-stu-id="0e814-282">Adds a NuGet package.</span></span>
[<span data-ttu-id="0e814-283">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="0e814-283">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="0e814-284">Bir NuGet paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-284">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="0e814-285">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="0e814-285">NuGet commands</span></span>

<span data-ttu-id="0e814-286">Komut</span><span class="sxs-lookup"><span data-stu-id="0e814-286">Command</span></span> | <span data-ttu-id="0e814-287">İşlev</span><span class="sxs-lookup"><span data-stu-id="0e814-287">Function</span></span>
--- | ---
[<span data-ttu-id="0e814-288">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="0e814-288">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="0e814-289">Sunucudan bir paketi siler veya listesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-289">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="0e814-290">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="0e814-290">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="0e814-291">Http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="0e814-291">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="0e814-292">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="0e814-292">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="0e814-293">Bir paketi sunucuya gönderir ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="0e814-293">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="0e814-294">Küresel, araç yolu ve yerel araçlar komutları</span><span class="sxs-lookup"><span data-stu-id="0e814-294">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="0e814-295">Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="0e814-295">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="0e814-296">Araçları kendiniz yazabilir veya üçüncü taraflarca yazılmış Araçları yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e814-296">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="0e814-297">Araçlar genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="0e814-297">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="0e814-298">Daha fazla bilgi için bkz. [.NET Core araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0e814-298">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="0e814-299">Genel ve araç yolu araçları .NET Core SDK 2,1 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e814-299">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="0e814-300">Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e814-300">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="0e814-301">Komut</span><span class="sxs-lookup"><span data-stu-id="0e814-301">Command</span></span> | <span data-ttu-id="0e814-302">İşlev</span><span class="sxs-lookup"><span data-stu-id="0e814-302">Function</span></span>
--- | ---
[<span data-ttu-id="0e814-303">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="0e814-303">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="0e814-304">Makinenize bir araç kurar.</span><span class="sxs-lookup"><span data-stu-id="0e814-304">Installs a tool on your machine.</span></span>
[<span data-ttu-id="0e814-305">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="0e814-305">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="0e814-306">Makinenizde yüklü olan tüm genel, araç-yol veya yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="0e814-306">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="0e814-307">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="0e814-307">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="0e814-308">Bir aracı makinenizden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="0e814-308">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="0e814-309">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="0e814-309">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="0e814-310">Makinenizde yüklü bir aracı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="0e814-310">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="0e814-311">Ek araçlar</span><span class="sxs-lookup"><span data-stu-id="0e814-311">Additional tools</span></span>

<span data-ttu-id="0e814-312">.NET Core SDK 2.1.300 ile başlayarak, yalnızca .NET Core SDK bir parçası olarak yalnızca `DotnetCliToolReference` kullanılarak proje temelinde kullanılabilen birçok araç vardır.</span><span class="sxs-lookup"><span data-stu-id="0e814-312">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="0e814-313">Bu araçlar aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="0e814-313">These tools are listed in the following table:</span></span>

| <span data-ttu-id="0e814-314">Aracı</span><span class="sxs-lookup"><span data-stu-id="0e814-314">Tool</span></span>                                              | <span data-ttu-id="0e814-315">İşlev</span><span class="sxs-lookup"><span data-stu-id="0e814-315">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="0e814-316">geliştirme-CERT</span><span class="sxs-lookup"><span data-stu-id="0e814-316">dev-certs</span></span>                                         | <span data-ttu-id="0e814-317">Geliştirme sertifikaları oluşturur ve yönetir.</span><span class="sxs-lookup"><span data-stu-id="0e814-317">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="0e814-318">aşv</span><span class="sxs-lookup"><span data-stu-id="0e814-318">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="0e814-319">Komut satırı araçlarını Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="0e814-319">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="0e814-320">SQL-Cache</span><span class="sxs-lookup"><span data-stu-id="0e814-320">sql-cache</span></span>                                         | <span data-ttu-id="0e814-321">Önbellek komut satırı araçlarını SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0e814-321">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="0e814-322">Kullanıcı gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="0e814-322">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="0e814-323">Geliştirme Kullanıcı gizli dizilerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="0e814-323">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="0e814-324">Servisi</span><span class="sxs-lookup"><span data-stu-id="0e814-324">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="0e814-325">Dosyalar değiştiğinde bir komutu çalıştıran bir dosya İzleyicisi başlatır.</span><span class="sxs-lookup"><span data-stu-id="0e814-325">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="0e814-326">Her araç hakkında daha fazla bilgi için `dotnet <tool-name> --help`yazın.</span><span class="sxs-lookup"><span data-stu-id="0e814-326">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="0e814-327">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0e814-327">Examples</span></span>

<span data-ttu-id="0e814-328">Yeni bir .NET Core konsol uygulaması oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0e814-328">Creates a new .NET Core console application:</span></span>

`dotnet new console`

<span data-ttu-id="0e814-329">Belirli bir uygulama için bağımlılıkları geri yükle:</span><span class="sxs-lookup"><span data-stu-id="0e814-329">Restore dependencies for a given application:</span></span>

`dotnet restore`

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="0e814-330">Belirli bir dizinde bir proje ve onun bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0e814-330">Build a project and its dependencies in a given directory:</span></span>

`dotnet build`

<span data-ttu-id="0e814-331">`myapp.dll`gibi bir uygulama DLL 'SI çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0e814-331">Run an application DLL, such as `myapp.dll`:</span></span>

`dotnet myapp.dll`

## <a name="environment-variables"></a><span data-ttu-id="0e814-332">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="0e814-332">Environment variables</span></span>

# <a name="net-core-21"></a>[<span data-ttu-id="0e814-333">.NET Core 2,1</span><span class="sxs-lookup"><span data-stu-id="0e814-333">.NET Core 2.1</span></span>](#tab/netcore21)

`DOTNET_PACKAGES`

<span data-ttu-id="0e814-334">Genel paketler klasörü.</span><span class="sxs-lookup"><span data-stu-id="0e814-334">The global packages folder.</span></span> <span data-ttu-id="0e814-335">Ayarlanmamışsa, varsayılan olarak UNIX veya Windows üzerinde `%userprofile%\.nuget\packages` `~/.nuget/packages`.</span><span class="sxs-lookup"><span data-stu-id="0e814-335">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="0e814-336">Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e814-336">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="0e814-337">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e814-337">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="0e814-338">Telemetri özelliğinin (değerler `true`, `1`veya `yes` kabul edilir) devre dışı bırakmak için `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0e814-338">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="0e814-339">Aksi takdirde, telemetri özelliklerine (değerler `false`, `0`veya `no` kabul edilir) kabul etmek için `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0e814-339">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0e814-340">Ayarlanmamışsa, varsayılan `false` ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="0e814-340">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="0e814-341">.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e814-341">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="0e814-342">Ayarlanmamışsa, varsayılan olarak `true`olur.</span><span class="sxs-lookup"><span data-stu-id="0e814-342">If not set, it defaults to `true`.</span></span> <span data-ttu-id="0e814-343">Genel konumdan çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olmak için `false` olarak ayarlayın (değerler `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="0e814-343">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="0e814-344">Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="0e814-344">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`

<span data-ttu-id="0e814-345">`0`olarak ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="0e814-345">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="0e814-346">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0e814-346">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

# <a name="net-core-20"></a>[<span data-ttu-id="0e814-347">.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="0e814-347">.NET Core 2.0</span></span>](#tab/netcore20)

`DOTNET_PACKAGES`

<span data-ttu-id="0e814-348">Birincil paket önbelleği.</span><span class="sxs-lookup"><span data-stu-id="0e814-348">The primary package cache.</span></span> <span data-ttu-id="0e814-349">Ayarlanmamışsa, varsayılan olarak UNIX veya Windows üzerinde `%userprofile%\.nuget\packages` `$HOME/.nuget/packages`.</span><span class="sxs-lookup"><span data-stu-id="0e814-349">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="0e814-350">Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e814-350">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="0e814-351">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e814-351">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="0e814-352">Telemetri özelliğinin (değerler `true`, `1`veya `yes` kabul edilir) devre dışı bırakmak için `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0e814-352">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="0e814-353">Aksi takdirde, telemetri özelliklerine (değerler `false`, `0`veya `no` kabul edilir) kabul etmek için `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0e814-353">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0e814-354">Ayarlanmamışsa, varsayılan `false` ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="0e814-354">If not set, the default is `false` and the telemetry feature is active.</span></span>

`DOTNET_MULTILEVEL_LOOKUP`

<span data-ttu-id="0e814-355">.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e814-355">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="0e814-356">Ayarlanmamışsa, varsayılan olarak `true`olur.</span><span class="sxs-lookup"><span data-stu-id="0e814-356">If not set, it defaults to `true`.</span></span> <span data-ttu-id="0e814-357">Genel konumdan çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olmak için `false` olarak ayarlayın (değerler `0` veya `false` kabul edilir).</span><span class="sxs-lookup"><span data-stu-id="0e814-357">Set to `false` to not resolve from the global location and have isolated .NET Core installations (values `0` or `false` are accepted).</span></span> <span data-ttu-id="0e814-358">Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="0e814-358">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

# <a name="net-core-1x"></a>[<span data-ttu-id="0e814-359">.NET Core 1. x</span><span class="sxs-lookup"><span data-stu-id="0e814-359">.NET Core 1.x</span></span>](#tab/netcore1x)

`DOTNET_PACKAGES`

<span data-ttu-id="0e814-360">Birincil paket önbelleği.</span><span class="sxs-lookup"><span data-stu-id="0e814-360">The primary package cache.</span></span> <span data-ttu-id="0e814-361">Ayarlanmamışsa, varsayılan olarak UNIX veya Windows üzerinde `%userprofile%\.nuget\packages` `$HOME/.nuget/packages`.</span><span class="sxs-lookup"><span data-stu-id="0e814-361">If not set, it defaults to `$HOME/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

`DOTNET_SERVICING`

<span data-ttu-id="0e814-362">Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e814-362">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

`DOTNET_CLI_TELEMETRY_OPTOUT`

<span data-ttu-id="0e814-363">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="0e814-363">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="0e814-364">Telemetri özelliğinin (değerler `true`, `1`veya `yes` kabul edilir) devre dışı bırakmak için `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0e814-364">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="0e814-365">Aksi takdirde, telemetri özelliklerine (değerler `false`, `0`veya `no` kabul edilir) kabul etmek için `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0e814-365">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0e814-366">Ayarlanmamışsa, varsayılan `false` ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="0e814-366">If not set, the default is `false` and the telemetry feature is active.</span></span>

---

## <a name="see-also"></a><span data-ttu-id="0e814-367">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e814-367">See also</span></span>

- [<span data-ttu-id="0e814-368">Çalışma zamanı yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="0e814-368">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="0e814-369">.NET Core çalışma zamanı yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="0e814-369">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
