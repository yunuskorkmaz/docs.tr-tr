---
title: dotnet komutu
description: Dotnet komutu (.NET Core CLI için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 02/13/2020
ms.openlocfilehash: 9446808d7f23d762c7a3c8a58252664fc5dade5b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389604"
---
# <a name="dotnet-command"></a><span data-ttu-id="97174-103">dotnet komutu</span><span class="sxs-lookup"><span data-stu-id="97174-103">dotnet command</span></span>

<span data-ttu-id="97174-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="97174-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="97174-105">Adı</span><span class="sxs-lookup"><span data-stu-id="97174-105">Name</span></span>

<span data-ttu-id="97174-106">`dotnet`- .NET Core CLI için genel sürücü.</span><span class="sxs-lookup"><span data-stu-id="97174-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="97174-107">Özet</span><span class="sxs-lookup"><span data-stu-id="97174-107">Synopsis</span></span>

<span data-ttu-id="97174-108">Kullanılabilir komutlar ve ortam hakkında bilgi almak için:</span><span class="sxs-lookup"><span data-stu-id="97174-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="97174-109">Bir komutçalıştırmak için (SDK yüklemegerektirir):</span><span class="sxs-lookup"><span data-stu-id="97174-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="97174-110">Bir uygulamayı çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="97174-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="97174-111">`--roll-forward`.NET Core 3.x'ten beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97174-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="97174-112">.NET Core 2.x için kullanın. `--roll-forward-on-no-candidate-fx`</span><span class="sxs-lookup"><span data-stu-id="97174-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="97174-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97174-113">Description</span></span>

<span data-ttu-id="97174-114">Komutun `dotnet` iki işlevi vardır:</span><span class="sxs-lookup"><span data-stu-id="97174-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="97174-115">.NET Core projeleri ile çalışmak için komutlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="97174-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="97174-116">Örneğin, [`dotnet build`](dotnet-build.md) bir proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97174-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="97174-117">Her komut kendi seçeneklerini ve bağımsız değişkenlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97174-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="97174-118">Tüm komutlar, `--help` komutun nasıl kullanılacağı hakkında kısa belgeler yazdırma seçeneğini destekler.</span><span class="sxs-lookup"><span data-stu-id="97174-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="97174-119">.NET Core uygulamalarını çalıştırıyor.</span><span class="sxs-lookup"><span data-stu-id="97174-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="97174-120">Uygulamayı çalıştırmak için bir `.dll` uygulama dosyasına giden yolu belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97174-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="97174-121">Uygulamayı çalıştırmak için bulmak ve konsol uygulamaları durumunda `Main` yöntemdir giriş noktası yürütmek anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="97174-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="97174-122">Örneğin, `dotnet myapp.dll` `myapp` uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="97174-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="97174-123">Dağıtım seçenekleri hakkında bilgi edinmek için [.NET Core uygulama dağıtımına](../deploying/index.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="97174-123">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="97174-124">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="97174-124">Options</span></span>

<span data-ttu-id="97174-125">Tek `dotnet` başına, bir komutu çalıştırmak ve bir uygulamayı çalıştırmak için farklı seçenekler mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="97174-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="97174-126">Dotnet seçenekleri tek başına</span><span class="sxs-lookup"><span data-stu-id="97174-126">Options for dotnet by itself</span></span>

<span data-ttu-id="97174-127">Aşağıdaki seçenekler tek `dotnet` başına vardır.</span><span class="sxs-lookup"><span data-stu-id="97174-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="97174-128">Örneğin, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="97174-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="97174-129">Çevre yle ilgili bilgileri yazdırır.</span><span class="sxs-lookup"><span data-stu-id="97174-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="97174-130">Geçerli işletim sistemi gibi bir .NET Core yüklemesi ve makine ortamı hakkında ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA'sını işler.</span><span class="sxs-lookup"><span data-stu-id="97174-130">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="97174-131">.NET Core SDK'nın kullanımdaki sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="97174-131">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="97174-132">Yüklenen .NET Core çalışma saatlerinin listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="97174-132">Prints out a list of the installed .NET Core runtimes.</span></span> <span data-ttu-id="97174-133">SDK'nın x86 sürümü yalnızca x86 çalışma saatlerini listeler ve SDK'nın x64 sürümü yalnızca x64 çalışma saatlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="97174-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="97174-134">Yüklenen .NET Core SDK'ların listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="97174-134">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="97174-135">Kullanılabilir komutların listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="97174-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="97174-136">Komut çalıştırmak için SDK seçenekleri</span><span class="sxs-lookup"><span data-stu-id="97174-136">SDK options for running a command</span></span>

<span data-ttu-id="97174-137">Aşağıdaki seçenekler bir `dotnet` komut ile vardır.</span><span class="sxs-lookup"><span data-stu-id="97174-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="97174-138">Örneğin, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="97174-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="97174-139">Tanılama çıktısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="97174-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="97174-140">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="97174-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="97174-141">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="97174-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="97174-142">Her komutta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="97174-142">Not supported in every command.</span></span> <span data-ttu-id="97174-143">Bu seçeneğin kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="97174-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="97174-144">Belirli bir komut için belgeleri yazdırır, örneğin. `dotnet build --help`</span><span class="sxs-lookup"><span data-stu-id="97174-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="97174-145">Her komut, bu komuta özgü seçenekleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97174-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="97174-146">Kullanılabilir seçeneklerlistesi için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="97174-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="97174-147">Çalışma zamanı seçenekleri</span><span class="sxs-lookup"><span data-stu-id="97174-147">Runtime options</span></span>

<span data-ttu-id="97174-148">Bir uygulama çalıştırıldığında `dotnet` aşağıdaki seçenekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97174-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="97174-149">Örneğin, `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="97174-149">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="97174-150">Sondalama ilkesi ve sondalama için derlemeler içeren yol.</span><span class="sxs-lookup"><span data-stu-id="97174-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="97174-151">Ek bir *.deps.json* dosyasına giden yol.</span><span class="sxs-lookup"><span data-stu-id="97174-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="97174-152">*Deps.json* dosyası, derleme çakışmalarını gidermek için kullanılan bağımlılıkların, derleme bağımlılıklarının ve sürüm bilgilerinin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="97174-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="97174-153">Daha fazla bilgi için GitHub'daki [Runtime Configuration Files'a](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="97174-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="97174-154">.NET Core çalışma zamanı sürümü uygulamayı çalıştırmak için kullanmak.</span><span class="sxs-lookup"><span data-stu-id="97174-154">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="97174-155">*Runtimeconfig.json* dosyasına giden yol.</span><span class="sxs-lookup"><span data-stu-id="97174-155">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="97174-156">*Runtimeconfig.json* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="97174-156">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="97174-157">Daha fazla bilgi için [.NET Core çalışma zamanı yapılandırma ayarlarına](../run-time-config/index.md#runtimeconfigjson)bakın.</span><span class="sxs-lookup"><span data-stu-id="97174-157">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="97174-158">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*.NET Core 2.x SDK'da mevcuttur.**</span><span class="sxs-lookup"><span data-stu-id="97174-158">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="97174-159">Gerekli paylaşılan çerçeve kullanılamadığında davranışı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="97174-159">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="97174-160">`N`olabilir:</span><span class="sxs-lookup"><span data-stu-id="97174-160">`N` can be:</span></span>

  - <span data-ttu-id="97174-161">`0`- Hatta küçük sürümü ileri rulo devre dışı.</span><span class="sxs-lookup"><span data-stu-id="97174-161">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="97174-162">`1`- Roll ileri küçük sürümü, ancak ana sürümünde değil.</span><span class="sxs-lookup"><span data-stu-id="97174-162">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="97174-163">Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="97174-163">This is the default behavior.</span></span>
  - <span data-ttu-id="97174-164">`2`- Küçük ve ana versiyonlarda ileri ye doğru yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="97174-164">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="97174-165">Daha fazla bilgi için [bkz.](../whats-new/dotnet-core-2-1.md#roll-forward)</span><span class="sxs-lookup"><span data-stu-id="97174-165">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="97174-166">**`--roll-forward <SETTING>`\*\*\*\*.NET Core SDK 3.0 ile başlayan kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="97174-166">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="97174-167">Kullanıma almanın uygulamaya nasıl uygulandığını denetler.</span><span class="sxs-lookup"><span data-stu-id="97174-167">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="97174-168">Aşağıdaki `SETTING` değerlerden biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="97174-168">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="97174-169">Belirtilmemişse, `Minor` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="97174-169">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="97174-170">`LatestPatch`- En yüksek yama sürümüne doğru yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="97174-170">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="97174-171">Bu, küçük sürümün devrilmelerini devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="97174-171">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="97174-172">`Minor`- İstenen küçük sürüm eksikse, en düşük yüksek minör sürüme doğru ileri doğru yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="97174-172">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="97174-173">İstenen küçük sürüm varsa, En Son Yama ilkesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97174-173">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="97174-174">`Major`- İstenen ana sürüm eksikse, en düşük yüksek ana sürüme ve en düşük küçük sürüme yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="97174-174">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="97174-175">İstenen ana sürüm varsa, Küçük ilke kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97174-175">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="97174-176">`LatestMinor`- İstenen küçük sürüm mevcut olsa bile, en yüksek minör sürüme doğru yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="97174-176">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="97174-177">Bileşen barındırma senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="97174-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="97174-178">`LatestMajor`- İstenilen ana sürüm mevcut olsa bile, en yüksek majör ve en yüksek minör sürüme doğru yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="97174-178">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="97174-179">Bileşen barındırma senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="97174-179">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="97174-180">`Disable`- Öne yuvarlanmayın.</span><span class="sxs-lookup"><span data-stu-id="97174-180">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="97174-181">Yalnızca belirtilen sürüme bağla.</span><span class="sxs-lookup"><span data-stu-id="97174-181">Only bind to specified version.</span></span> <span data-ttu-id="97174-182">Bu ilke, en son düzeltme ekilerine ilerleme yitirme özelliğini devre dışı kattığı için genel kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="97174-182">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="97174-183">Bu değer yalnızca sınama için önerilir.</span><span class="sxs-lookup"><span data-stu-id="97174-183">This value is only recommended for testing.</span></span>

<span data-ttu-id="97174-184">`Disable`Hariç, tüm ayarlar mevcut en yüksek yama sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="97174-184">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="97174-185">Roll forward davranışı, proje dosyası özelliğinde, çalışma zamanı yapılandırma dosyası özelliğinde ve ortam değişkeninde de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="97174-185">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="97174-186">Daha fazla bilgi için [Bkz. Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="97174-186">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="97174-187">dotnet komutları</span><span class="sxs-lookup"><span data-stu-id="97174-187">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="97174-188">Genel</span><span class="sxs-lookup"><span data-stu-id="97174-188">General</span></span>

| <span data-ttu-id="97174-189">Komut</span><span class="sxs-lookup"><span data-stu-id="97174-189">Command</span></span>                                       | <span data-ttu-id="97174-190">İşlev</span><span class="sxs-lookup"><span data-stu-id="97174-190">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="97174-191">dotnet build</span><span class="sxs-lookup"><span data-stu-id="97174-191">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="97174-192">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97174-192">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="97174-193">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="97174-193">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="97174-194">Bir yapı tarafından başlatılan sunucularla etkileşim de eder.</span><span class="sxs-lookup"><span data-stu-id="97174-194">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="97174-195">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="97174-195">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="97174-196">Yapı çıktılarını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="97174-196">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="97174-197">dotnet help</span><span class="sxs-lookup"><span data-stu-id="97174-197">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="97174-198">Komut için çevrimiçi olarak daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="97174-198">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="97174-199">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="97174-199">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="97174-200">Geçerli bir Önizleme 2 projesini bir .NET Core SDK 1.0 projesine geçirin.</span><span class="sxs-lookup"><span data-stu-id="97174-200">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="97174-201">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="97174-201">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="97174-202">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="97174-202">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="97174-203">dotnet new</span><span class="sxs-lookup"><span data-stu-id="97174-203">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="97174-204">Belirli bir şablon için C# veya F# projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="97174-204">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="97174-205">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="97174-205">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="97174-206">Kodunuzu bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="97174-206">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="97174-207">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="97174-207">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="97174-208">.NET framework'e bağımlı veya bağımsız bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="97174-208">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="97174-209">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="97174-209">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="97174-210">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="97174-210">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="97174-211">dotnet run</span><span class="sxs-lookup"><span data-stu-id="97174-211">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="97174-212">Uygulamayı kaynaktan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="97174-212">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="97174-213">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="97174-213">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="97174-214">Çözüm dosyasına proje ekleme, kaldırma ve listele etme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="97174-214">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="97174-215">dotnet store</span><span class="sxs-lookup"><span data-stu-id="97174-215">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="97174-216">Montajları çalışma zamanı paket deposunda saklar.</span><span class="sxs-lookup"><span data-stu-id="97174-216">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="97174-217">dotnet test</span><span class="sxs-lookup"><span data-stu-id="97174-217">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="97174-218">Bir test koşucusu kullanarak testler çalışır.</span><span class="sxs-lookup"><span data-stu-id="97174-218">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="97174-219">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="97174-219">Project references</span></span>

<span data-ttu-id="97174-220">Komut</span><span class="sxs-lookup"><span data-stu-id="97174-220">Command</span></span> | <span data-ttu-id="97174-221">İşlev</span><span class="sxs-lookup"><span data-stu-id="97174-221">Function</span></span>
--- | ---
[<span data-ttu-id="97174-222">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="97174-222">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="97174-223">Proje başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="97174-223">Adds a project reference.</span></span>
[<span data-ttu-id="97174-224">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="97174-224">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="97174-225">Proje başvurularını listeler.</span><span class="sxs-lookup"><span data-stu-id="97174-225">Lists project references.</span></span>
[<span data-ttu-id="97174-226">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="97174-226">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="97174-227">Proje başvurularını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="97174-227">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="97174-228">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="97174-228">NuGet packages</span></span>

<span data-ttu-id="97174-229">Komut</span><span class="sxs-lookup"><span data-stu-id="97174-229">Command</span></span> | <span data-ttu-id="97174-230">İşlev</span><span class="sxs-lookup"><span data-stu-id="97174-230">Function</span></span>
--- | ---
[<span data-ttu-id="97174-231">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="97174-231">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="97174-232">Bir NuGet paketi ekler.</span><span class="sxs-lookup"><span data-stu-id="97174-232">Adds a NuGet package.</span></span>
[<span data-ttu-id="97174-233">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="97174-233">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="97174-234">NuGet paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="97174-234">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="97174-235">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="97174-235">NuGet commands</span></span>

<span data-ttu-id="97174-236">Komut</span><span class="sxs-lookup"><span data-stu-id="97174-236">Command</span></span> | <span data-ttu-id="97174-237">İşlev</span><span class="sxs-lookup"><span data-stu-id="97174-237">Function</span></span>
--- | ---
[<span data-ttu-id="97174-238">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="97174-238">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="97174-239">Bir paketi sunucudan siler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="97174-239">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="97174-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="97174-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="97174-241">Bir paketi sunucuya iter ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="97174-241">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="97174-242">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="97174-242">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="97174-243">Http isteği önbelleği, geçici önbellek veya makine çapında ki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="97174-243">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="97174-244">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="97174-244">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="97174-245">Bir NuGet kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="97174-245">Adds a NuGet source.</span></span>
[<span data-ttu-id="97174-246">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="97174-246">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="97174-247">NuGet kaynağını devre dışı kılmış olur.</span><span class="sxs-lookup"><span data-stu-id="97174-247">Disables a NuGet source.</span></span>
[<span data-ttu-id="97174-248">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="97174-248">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="97174-249">Bir NuGet kaynağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="97174-249">Enables a NuGet source.</span></span>
[<span data-ttu-id="97174-250">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="97174-250">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="97174-251">Tüm yapılandırılan NuGet kaynaklarını listeler.</span><span class="sxs-lookup"><span data-stu-id="97174-251">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="97174-252">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="97174-252">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="97174-253">NuGet kaynağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="97174-253">Removes a NuGet source.</span></span>
[<span data-ttu-id="97174-254">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="97174-254">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="97174-255">Bir NuGet kaynağını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="97174-255">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="97174-256">Genel, araç yolu ve yerel araçlar komutları</span><span class="sxs-lookup"><span data-stu-id="97174-256">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="97174-257">Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="97174-257">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="97174-258">Araçları kendiniz yazabilir veya üçüncü şahıslar tarafından yazılmış araçları yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="97174-258">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="97174-259">Araçlar, genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="97174-259">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="97174-260">Daha fazla bilgi için [.NET Core araçlarına genel bakış](global-tools.md)ala.</span><span class="sxs-lookup"><span data-stu-id="97174-260">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="97174-261">.NET Core SDK 2.1 ile başlayan global ve araç yolu araçları mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="97174-261">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="97174-262">Yerel araçlar .NET Core SDK 3.0 ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97174-262">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="97174-263">Komut</span><span class="sxs-lookup"><span data-stu-id="97174-263">Command</span></span> | <span data-ttu-id="97174-264">İşlev</span><span class="sxs-lookup"><span data-stu-id="97174-264">Function</span></span>
--- | ---
[<span data-ttu-id="97174-265">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="97174-265">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="97174-266">Makinenize bir alet yükler.</span><span class="sxs-lookup"><span data-stu-id="97174-266">Installs a tool on your machine.</span></span>
[<span data-ttu-id="97174-267">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="97174-267">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="97174-268">Şu anda makinenizde yüklü olan tüm genel, araç yolu veya yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="97174-268">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="97174-269">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="97174-269">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="97174-270">Makinenizdeki bir aracı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="97174-270">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="97174-271">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="97174-271">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="97174-272">Makinenize yüklenen bir aracı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="97174-272">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="97174-273">Ek araçlar</span><span class="sxs-lookup"><span data-stu-id="97174-273">Additional tools</span></span>

<span data-ttu-id="97174-274">.NET Core SDK 2.1.300 ile başlayarak, sadece proje bazında `DotnetCliToolReference` kullanılabilen bir dizi araç artık .NET Core SDK'nın bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="97174-274">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="97174-275">Bu araçlar aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="97174-275">These tools are listed in the following table:</span></span>

| <span data-ttu-id="97174-276">Araç</span><span class="sxs-lookup"><span data-stu-id="97174-276">Tool</span></span>                                              | <span data-ttu-id="97174-277">İşlev</span><span class="sxs-lookup"><span data-stu-id="97174-277">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="97174-278">dev-certs</span><span class="sxs-lookup"><span data-stu-id="97174-278">dev-certs</span></span>                                         | <span data-ttu-id="97174-279">Geliştirme sertifikaları oluşturur ve yönetir.</span><span class="sxs-lookup"><span data-stu-id="97174-279">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="97174-280">Ef</span><span class="sxs-lookup"><span data-stu-id="97174-280">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="97174-281">Entity Framework Core komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="97174-281">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="97174-282">sql önbellek</span><span class="sxs-lookup"><span data-stu-id="97174-282">sql-cache</span></span>                                         | <span data-ttu-id="97174-283">SQL Server önbellek komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="97174-283">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="97174-284">kullanıcı sırları</span><span class="sxs-lookup"><span data-stu-id="97174-284">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="97174-285">Geliştirme kullanıcı sırlarını yönetir.</span><span class="sxs-lookup"><span data-stu-id="97174-285">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="97174-286">Izle</span><span class="sxs-lookup"><span data-stu-id="97174-286">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="97174-287">Dosyalar değiştiğinde komutu çalıştıran bir dosya izleyicisi başlatır.</span><span class="sxs-lookup"><span data-stu-id="97174-287">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="97174-288">Her araç hakkında daha `dotnet <tool-name> --help`fazla bilgi için yazın.</span><span class="sxs-lookup"><span data-stu-id="97174-288">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="97174-289">Örnekler</span><span class="sxs-lookup"><span data-stu-id="97174-289">Examples</span></span>

<span data-ttu-id="97174-290">Yeni bir .NET Core konsol uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="97174-290">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="97174-291">Belirli bir dizinde bir proje ve bağımlılıkları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="97174-291">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="97174-292">Bir uygulama çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="97174-292">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="97174-293">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="97174-293">Environment variables</span></span>

- <span data-ttu-id="97174-294">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="97174-294">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="97174-295">Varsayılan konumda yüklü değillerse .NET Core çalışma saatlerinin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="97174-295">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="97174-296">Windows'daki varsayılan `C:\Program Files\dotnet`konum.</span><span class="sxs-lookup"><span data-stu-id="97174-296">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="97174-297">Linux ve macOS üzerinde `/usr/share/dotnet`varsayılan konum .</span><span class="sxs-lookup"><span data-stu-id="97174-297">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="97174-298">Bu ortam değişkeni yalnızca oluşturulan yürütülebilir uygulamalar (ek hosts) aracılığıyla uygulamaları çalıştırırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97174-298">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="97174-299">`DOTNET_ROOT(x86)`bunun yerine, 64 bit işletim sistemi üzerinde 32 bit çalıştırılabilir çalıştırılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="97174-299">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="97174-300">Genel paketler klasörü.</span><span class="sxs-lookup"><span data-stu-id="97174-300">The global packages folder.</span></span> <span data-ttu-id="97174-301">Ayarlanmamışsa, varsayılan `~/.nuget/packages` olarak Unix'te veya `%userprofile%\.nuget\packages` Windows'da olur.</span><span class="sxs-lookup"><span data-stu-id="97174-301">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="97174-302">Çalışma süresini yüklerken paylaşılan ana bilgisayar tarafından kullanılacak servis dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="97174-302">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="97174-303">.NET Core karşılama ve telemetri iletilerinin ilk çalıştırmada görüntülenip görüntülenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="97174-303">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="97174-304">`true` Bu iletileri `true`(değerler, veya `1` `yes` kabul edilen) veya izin `false` verecek şekilde `false` `0`(değerler, , veya `no` kabul edilen) sessize almak üzere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="97174-304">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="97174-305">Ayarlanmazsa, varsayılan `false` değerdir ve iletiler ilk çalıştırmada görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="97174-305">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="97174-306">Bu bayrağın telemetri üzerinde hiçbir `DOTNET_CLI_TELEMETRY_OPTOUT` etkisi olmadığını unutmayın (telemetri göndermeyi devre dışı bırakmak için bkz.</span><span class="sxs-lookup"><span data-stu-id="97174-306">Note that this flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="97174-307">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft'a gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="97174-307">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="97174-308">Telemetri özelliğini devre dışı bırakacak şekilde `1`ayarlayın `yes` (değerler `true`, veya kabul edilir). `true`</span><span class="sxs-lookup"><span data-stu-id="97174-308">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="97174-309">Aksi takdirde, `false` telemetri özellikleri `false`(değerler , `0`veya `no` kabul) içine tercih etmek için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="97174-309">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="97174-310">Ayaredilmezse, varsayılan `false` ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="97174-310">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="97174-311">.NET Core çalışma zamanı, paylaşılan çerçeve veya SDK'nın genel konumdan çözülüp çözülmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="97174-311">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="97174-312">Ayarlanmazise, varsayılan olarak 1 `true`(mantıksal).</span><span class="sxs-lookup"><span data-stu-id="97174-312">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="97174-313">Genel konumdan `false`çözüme kavuşturulması ve .NET Core yüklemelerini yalıtmak için 0 (mantıksal) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="97174-313">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="97174-314">Çok düzeyli arama hakkında daha fazla bilgi [için, Çok düzeyli SharedFX Arama'ya](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="97174-314">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="97174-315">`DOTNET_ROLL_FORWARD`**.NET Core 3.x SDK ile başlayan kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="97174-315">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="97174-316">Yuvarlanan ileri davranışını belirler.</span><span class="sxs-lookup"><span data-stu-id="97174-316">Determines roll forward behavior.</span></span> <span data-ttu-id="97174-317">Daha fazla bilgi `--roll-forward` için bu makalenin önceki seçeneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="97174-317">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="97174-318">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**.NET Core 2.x SDK'da mevcuttur.**</span><span class="sxs-lookup"><span data-stu-id="97174-318">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="97174-319">Devre dışı bırakır küçük sürüm, `0`eğer ayarlanırsa.</span><span class="sxs-lookup"><span data-stu-id="97174-319">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="97174-320">Daha fazla bilgi için [bkz.](../whats-new/dotnet-core-2-1.md#roll-forward)</span><span class="sxs-lookup"><span data-stu-id="97174-320">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="97174-321">CLI UI'nin dilini ayarlar. `en-us`</span><span class="sxs-lookup"><span data-stu-id="97174-321">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="97174-322">Desteklenen değerler Visual Studio ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="97174-322">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="97174-323">Daha fazla bilgi için [Visual Studio yükleme belgelerinde](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)yükleyici dilini değiştirme bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="97174-323">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="97174-324">.NET kaynak yöneticisi kuralları geçerlidir, böylece&mdash; `CultureInfo` ağaçtaki torunları da seçebileceğiniz tam bir eşleşme seçmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="97174-324">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="97174-325">Örneğin, bunu `fr-CA`ayarlarsanız, CLI `fr` çevirileri bulur ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="97174-325">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="97174-326">Desteklenmeyen bir dile ayarlarsanız, CLI İngilizce'ye geri döner.</span><span class="sxs-lookup"><span data-stu-id="97174-326">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="97174-327">GUI özellikli oluşturulan yürütülebilirler için - normalde belirli hata sınıfları için gösteren iletişim açılır pencereaçılır penceresini devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="97174-327">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="97174-328">Sadece bu `stderr` gibi durumlarda yazar ve çıkar.</span><span class="sxs-lookup"><span data-stu-id="97174-328">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="97174-329">CLI seçeneğine `--additional-deps`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="97174-329">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="97174-330">Algılanan RID geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="97174-330">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="97174-331">Montaj çözünürlüğünün bazı durumlarda geri aldığı "paylaşılan deponun" konumu.</span><span class="sxs-lookup"><span data-stu-id="97174-331">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="97174-332">Başlangıç kancalarını yüklemek ve çalıştırmak için montajların listesi.</span><span class="sxs-lookup"><span data-stu-id="97174-332">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="97174-333">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="97174-333">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="97174-334">Barındırma bileşenlerinden gelen tanılama izlemelerini `dotnet.exe` `hostfxr`denetler, örneğin , , ve `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="97174-334">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="97174-335">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97174-335">See also</span></span>

- [<span data-ttu-id="97174-336">Runtime Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="97174-336">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="97174-337">.NET Core çalışma zamanı yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="97174-337">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
