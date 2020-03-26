---
title: dotnet komutu
description: Dotnet komutu (.NET Core CLI için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 02/13/2020
ms.openlocfilehash: 8692d419afd528bf49e1dc7dc1a7a5fd698b363b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134069"
---
# <a name="dotnet-command"></a><span data-ttu-id="7bac7-103">dotnet komutu</span><span class="sxs-lookup"><span data-stu-id="7bac7-103">dotnet command</span></span>

<span data-ttu-id="7bac7-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="7bac7-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7bac7-105">Adı</span><span class="sxs-lookup"><span data-stu-id="7bac7-105">Name</span></span>

<span data-ttu-id="7bac7-106">`dotnet`- .NET Core CLI için genel sürücü.</span><span class="sxs-lookup"><span data-stu-id="7bac7-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7bac7-107">Özet</span><span class="sxs-lookup"><span data-stu-id="7bac7-107">Synopsis</span></span>

<span data-ttu-id="7bac7-108">Kullanılabilir komutlar ve ortam hakkında bilgi almak için:</span><span class="sxs-lookup"><span data-stu-id="7bac7-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="7bac7-109">Bir komutçalıştırmak için (SDK yüklemegerektirir):</span><span class="sxs-lookup"><span data-stu-id="7bac7-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="7bac7-110">Bir uygulamayı çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="7bac7-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="7bac7-111">`--roll-forward`.NET Core 3.x'ten beri kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="7bac7-112">.NET Core 2.x için kullanın. `--roll-forward-on-no-candidate-fx`</span><span class="sxs-lookup"><span data-stu-id="7bac7-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="7bac7-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bac7-113">Description</span></span>

<span data-ttu-id="7bac7-114">Komutun `dotnet` iki işlevi vardır:</span><span class="sxs-lookup"><span data-stu-id="7bac7-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="7bac7-115">.NET Core projeleri ile çalışmak için komutlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="7bac7-116">Örneğin, [`dotnet build`](dotnet-build.md) bir proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7bac7-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="7bac7-117">Her komut kendi seçeneklerini ve bağımsız değişkenlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="7bac7-118">Tüm komutlar, `--help` komutun nasıl kullanılacağı hakkında kısa belgeler yazdırma seçeneğini destekler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="7bac7-119">.NET Core uygulamalarını çalıştırıyor.</span><span class="sxs-lookup"><span data-stu-id="7bac7-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="7bac7-120">Uygulamayı çalıştırmak için bir `.dll` uygulama dosyasına giden yolu belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bac7-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="7bac7-121">Örneğin, `dotnet myapp.dll` `myapp` uygulamayı çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="7bac7-122">Dağıtım seçenekleri hakkında bilgi edinmek için [.NET Core uygulama dağıtımına](../deploying/index.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="7bac7-123">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7bac7-123">Options</span></span>

<span data-ttu-id="7bac7-124">Tek `dotnet` başına, bir komutu çalıştırmak ve bir uygulamayı çalıştırmak için farklı seçenekler mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="7bac7-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="7bac7-125">Dotnet seçenekleri tek başına</span><span class="sxs-lookup"><span data-stu-id="7bac7-125">Options for dotnet by itself</span></span>

<span data-ttu-id="7bac7-126">Aşağıdaki seçenekler tek `dotnet` başına vardır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="7bac7-127">Örneğin, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="7bac7-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="7bac7-128">Çevre yle ilgili bilgileri yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="7bac7-129">Geçerli işletim sistemi gibi bir .NET Core yüklemesi ve makine ortamı hakkında ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA'sını işler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="7bac7-130">.NET Core SDK'nın kullanımdaki sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="7bac7-131">Yüklenen .NET Core çalışma saatlerinin listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="7bac7-132">Yüklenen .NET Core SDK'ların listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="7bac7-133">Kullanılabilir komutların listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="7bac7-134">Komut çalıştırmak için SDK seçenekleri</span><span class="sxs-lookup"><span data-stu-id="7bac7-134">SDK options for running a command</span></span>

<span data-ttu-id="7bac7-135">Aşağıdaki seçenekler bir `dotnet` komut ile vardır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="7bac7-136">Örneğin, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="7bac7-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="7bac7-137">Tanılama çıktısını sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="7bac7-138">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7bac7-139">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="7bac7-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="7bac7-140">Her komutta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="7bac7-140">Not supported in every command.</span></span> <span data-ttu-id="7bac7-141">Bu seçeneğin kullanılabilir olup olmadığını belirlemek için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="7bac7-142">Belirli bir komut için belgeleri yazdırır, örneğin. `dotnet build --help`</span><span class="sxs-lookup"><span data-stu-id="7bac7-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="7bac7-143">Her komut, bu komuta özgü seçenekleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="7bac7-144">Kullanılabilir seçeneklerlistesi için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="7bac7-145">Çalışma zamanı seçenekleri</span><span class="sxs-lookup"><span data-stu-id="7bac7-145">Runtime options</span></span>

<span data-ttu-id="7bac7-146">Bir uygulama çalıştırıldığında `dotnet` aşağıdaki seçenekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="7bac7-147">Örneğin, `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="7bac7-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="7bac7-148">Sondalama ilkesi ve sondalama için derlemeler içeren yol.</span><span class="sxs-lookup"><span data-stu-id="7bac7-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="7bac7-149">Ek bir *.deps.json* dosyasına giden yol.</span><span class="sxs-lookup"><span data-stu-id="7bac7-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="7bac7-150">*Deps.json* dosyası, derleme çakışmalarını gidermek için kullanılan bağımlılıkların, derleme bağımlılıklarının ve sürüm bilgilerinin listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="7bac7-151">Daha fazla bilgi için GitHub'daki [Runtime Configuration Files'a](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) bakın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="7bac7-152">.NET Core çalışma zamanı sürümü uygulamayı çalıştırmak için kullanmak.</span><span class="sxs-lookup"><span data-stu-id="7bac7-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="7bac7-153">*Runtimeconfig.json* dosyasına giden yol.</span><span class="sxs-lookup"><span data-stu-id="7bac7-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="7bac7-154">*Runtimeconfig.json* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="7bac7-155">Daha fazla bilgi için [.NET Core çalışma zamanı yapılandırma ayarlarına](../run-time-config/index.md#runtimeconfigjson)bakın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="7bac7-156">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*.NET Core 2.x SDK'da mevcuttur.**</span><span class="sxs-lookup"><span data-stu-id="7bac7-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="7bac7-157">Gerekli paylaşılan çerçeve kullanılamadığında davranışı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="7bac7-158">`N`olabilir:</span><span class="sxs-lookup"><span data-stu-id="7bac7-158">`N` can be:</span></span>

  - <span data-ttu-id="7bac7-159">`0`- Hatta küçük sürümü ileri rulo devre dışı.</span><span class="sxs-lookup"><span data-stu-id="7bac7-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="7bac7-160">`1`- Roll ileri küçük sürümü, ancak ana sürümünde değil.</span><span class="sxs-lookup"><span data-stu-id="7bac7-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="7bac7-161">Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-161">This is the default behavior.</span></span>
  - <span data-ttu-id="7bac7-162">`2`- Küçük ve ana versiyonlarda ileri ye doğru yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="7bac7-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="7bac7-163">Daha fazla bilgi için [bkz.](../whats-new/dotnet-core-2-1.md#roll-forward)</span><span class="sxs-lookup"><span data-stu-id="7bac7-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="7bac7-164">**`--roll-forward <SETTING>`\*\*\*\*.NET Core SDK 3.0 ile başlayan kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="7bac7-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="7bac7-165">Kullanıma almanın uygulamaya nasıl uygulandığını denetler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="7bac7-166">Aşağıdaki `SETTING` değerlerden biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="7bac7-167">Belirtilmemişse, `Minor` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="7bac7-168">`LatestPatch`- En yüksek yama sürümüne doğru yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="7bac7-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="7bac7-169">Bu, küçük sürümün devrilmelerini devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="7bac7-170">`Minor`- İstenen küçük sürüm eksikse, en düşük yüksek minör sürüme doğru ileri doğru yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="7bac7-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="7bac7-171">İstenen küçük sürüm varsa, En Son Yama ilkesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="7bac7-172">`Major`- İstenen ana sürüm eksikse, en düşük yüksek ana sürüme ve en düşük küçük sürüme yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="7bac7-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="7bac7-173">İstenen ana sürüm varsa, Küçük ilke kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="7bac7-174">`LatestMinor`- İstenen küçük sürüm mevcut olsa bile, en yüksek minör sürüme doğru yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="7bac7-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="7bac7-175">Bileşen barındırma senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="7bac7-176">`LatestMajor`- İstenilen ana sürüm mevcut olsa bile, en yüksek majör ve en yüksek minör sürüme doğru yuvarlan.</span><span class="sxs-lookup"><span data-stu-id="7bac7-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="7bac7-177">Bileşen barındırma senaryoları için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="7bac7-178">`Disable`- Öne yuvarlanmayın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="7bac7-179">Yalnızca belirtilen sürüme bağla.</span><span class="sxs-lookup"><span data-stu-id="7bac7-179">Only bind to specified version.</span></span> <span data-ttu-id="7bac7-180">Bu ilke, en son düzeltme ekilerine ilerleme yitirme özelliğini devre dışı kattığı için genel kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="7bac7-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="7bac7-181">Bu değer yalnızca sınama için önerilir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="7bac7-182">`Disable`Hariç, tüm ayarlar mevcut en yüksek yama sürümünü kullanır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="7bac7-183">Roll forward davranışı, proje dosyası özelliğinde, çalışma zamanı yapılandırma dosyası özelliğinde ve ortam değişkeninde de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="7bac7-184">Daha fazla bilgi için [Bkz. Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="7bac7-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="7bac7-185">dotnet komutları</span><span class="sxs-lookup"><span data-stu-id="7bac7-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="7bac7-186">Genel</span><span class="sxs-lookup"><span data-stu-id="7bac7-186">General</span></span>

| <span data-ttu-id="7bac7-187">Komut</span><span class="sxs-lookup"><span data-stu-id="7bac7-187">Command</span></span>                                       | <span data-ttu-id="7bac7-188">İşlev</span><span class="sxs-lookup"><span data-stu-id="7bac7-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="7bac7-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="7bac7-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="7bac7-190">Bir .NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7bac7-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="7bac7-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="7bac7-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="7bac7-192">Bir yapı tarafından başlatılan sunucularla etkileşim de eder.</span><span class="sxs-lookup"><span data-stu-id="7bac7-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="7bac7-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="7bac7-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="7bac7-194">Yapı çıktılarını temizleyin.</span><span class="sxs-lookup"><span data-stu-id="7bac7-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="7bac7-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="7bac7-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="7bac7-196">Komut için çevrimiçi olarak daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="7bac7-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="7bac7-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="7bac7-198">Geçerli bir Önizleme 2 projesini bir .NET Core SDK 1.0 projesine geçirin.</span><span class="sxs-lookup"><span data-stu-id="7bac7-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="7bac7-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="7bac7-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="7bac7-200">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="7bac7-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="7bac7-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="7bac7-202">Belirli bir şablon için C# veya F# projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="7bac7-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="7bac7-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="7bac7-204">Kodunuzu bir NuGet paketi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="7bac7-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="7bac7-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="7bac7-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="7bac7-206">.NET framework'e bağımlı veya bağımsız bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="7bac7-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="7bac7-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="7bac7-208">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="7bac7-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="7bac7-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="7bac7-210">Uygulamayı kaynaktan çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="7bac7-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="7bac7-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="7bac7-212">Çözüm dosyasına proje ekleme, kaldırma ve listele etme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="7bac7-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="7bac7-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="7bac7-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="7bac7-214">Montajları çalışma zamanı paket deposunda saklar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="7bac7-215">dotnet test</span><span class="sxs-lookup"><span data-stu-id="7bac7-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="7bac7-216">Bir test koşucusu kullanarak testler çalışır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="7bac7-217">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="7bac7-217">Project references</span></span>

<span data-ttu-id="7bac7-218">Komut</span><span class="sxs-lookup"><span data-stu-id="7bac7-218">Command</span></span> | <span data-ttu-id="7bac7-219">İşlev</span><span class="sxs-lookup"><span data-stu-id="7bac7-219">Function</span></span>
--- | ---
[<span data-ttu-id="7bac7-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="7bac7-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="7bac7-221">Proje başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-221">Adds a project reference.</span></span>
[<span data-ttu-id="7bac7-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="7bac7-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="7bac7-223">Proje başvurularını listeler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-223">Lists project references.</span></span>
[<span data-ttu-id="7bac7-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="7bac7-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="7bac7-225">Proje başvurularını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="7bac7-226">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="7bac7-226">NuGet packages</span></span>

<span data-ttu-id="7bac7-227">Komut</span><span class="sxs-lookup"><span data-stu-id="7bac7-227">Command</span></span> | <span data-ttu-id="7bac7-228">İşlev</span><span class="sxs-lookup"><span data-stu-id="7bac7-228">Function</span></span>
--- | ---
[<span data-ttu-id="7bac7-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="7bac7-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="7bac7-230">Bir NuGet paketi ekler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="7bac7-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="7bac7-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="7bac7-232">NuGet paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="7bac7-233">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="7bac7-233">NuGet commands</span></span>

<span data-ttu-id="7bac7-234">Komut</span><span class="sxs-lookup"><span data-stu-id="7bac7-234">Command</span></span> | <span data-ttu-id="7bac7-235">İşlev</span><span class="sxs-lookup"><span data-stu-id="7bac7-235">Function</span></span>
--- | ---
[<span data-ttu-id="7bac7-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="7bac7-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="7bac7-237">Bir paketi sunucudan siler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="7bac7-238">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="7bac7-238">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="7bac7-239">Bir paketi sunucuya iter ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-239">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="7bac7-240">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="7bac7-240">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="7bac7-241">Http isteği önbelleği, geçici önbellek veya makine çapında ki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-241">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="7bac7-242">dotnet nuget kaynak eklemek</span><span class="sxs-lookup"><span data-stu-id="7bac7-242">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="7bac7-243">Bir NuGet kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-243">Adds a NuGet source.</span></span>
[<span data-ttu-id="7bac7-244">dotnet nuget devre dışı kaynak</span><span class="sxs-lookup"><span data-stu-id="7bac7-244">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="7bac7-245">NuGet kaynağını devre dışı kılmış olur.</span><span class="sxs-lookup"><span data-stu-id="7bac7-245">Disables a NuGet source.</span></span>
[<span data-ttu-id="7bac7-246">dotnet nuget etkinleştirmek kaynak</span><span class="sxs-lookup"><span data-stu-id="7bac7-246">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="7bac7-247">Bir NuGet kaynağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-247">Enables a NuGet source.</span></span>
[<span data-ttu-id="7bac7-248">dotnet nuget listesi kaynak</span><span class="sxs-lookup"><span data-stu-id="7bac7-248">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="7bac7-249">Tüm yapılandırılan NuGet kaynaklarını listeler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-249">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="7bac7-250">dotnet nuget kaynak kaldırmak</span><span class="sxs-lookup"><span data-stu-id="7bac7-250">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="7bac7-251">NuGet kaynağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-251">Removes a NuGet source.</span></span>
[<span data-ttu-id="7bac7-252">dotnet nuget güncelleme kaynağı</span><span class="sxs-lookup"><span data-stu-id="7bac7-252">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="7bac7-253">Bir NuGet kaynağını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-253">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="7bac7-254">Genel, araç yolu ve yerel araçlar komutları</span><span class="sxs-lookup"><span data-stu-id="7bac7-254">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="7bac7-255">Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-255">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="7bac7-256">Araçları kendiniz yazabilir veya üçüncü şahıslar tarafından yazılmış araçları yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7bac7-256">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="7bac7-257">Araçlar, genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-257">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="7bac7-258">Daha fazla bilgi için [.NET Core araçlarına genel bakış](global-tools.md)ala.</span><span class="sxs-lookup"><span data-stu-id="7bac7-258">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="7bac7-259">.NET Core SDK 2.1 ile başlayan global ve araç yolu araçları mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="7bac7-259">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="7bac7-260">Yerel araçlar .NET Core SDK 3.0 ile başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-260">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="7bac7-261">Komut</span><span class="sxs-lookup"><span data-stu-id="7bac7-261">Command</span></span> | <span data-ttu-id="7bac7-262">İşlev</span><span class="sxs-lookup"><span data-stu-id="7bac7-262">Function</span></span>
--- | ---
[<span data-ttu-id="7bac7-263">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="7bac7-263">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="7bac7-264">Makinenize bir alet yükler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-264">Installs a tool on your machine.</span></span>
[<span data-ttu-id="7bac7-265">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="7bac7-265">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="7bac7-266">Şu anda makinenizde yüklü olan tüm genel, araç yolu veya yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-266">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="7bac7-267">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="7bac7-267">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="7bac7-268">Makinenizdeki bir aracı kaldırın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-268">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="7bac7-269">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="7bac7-269">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="7bac7-270">Makinenize yüklenen bir aracı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-270">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="7bac7-271">Ek araçlar</span><span class="sxs-lookup"><span data-stu-id="7bac7-271">Additional tools</span></span>

<span data-ttu-id="7bac7-272">.NET Core SDK 2.1.300 ile başlayarak, sadece proje bazında `DotnetCliToolReference` kullanılabilen bir dizi araç artık .NET Core SDK'nın bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-272">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="7bac7-273">Bu araçlar aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="7bac7-273">These tools are listed in the following table:</span></span>

| <span data-ttu-id="7bac7-274">Araç</span><span class="sxs-lookup"><span data-stu-id="7bac7-274">Tool</span></span>                                              | <span data-ttu-id="7bac7-275">İşlev</span><span class="sxs-lookup"><span data-stu-id="7bac7-275">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="7bac7-276">dev-certs</span><span class="sxs-lookup"><span data-stu-id="7bac7-276">dev-certs</span></span>                                         | <span data-ttu-id="7bac7-277">Geliştirme sertifikaları oluşturur ve yönetir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-277">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="7bac7-278">Ef</span><span class="sxs-lookup"><span data-stu-id="7bac7-278">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="7bac7-279">Entity Framework Core komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="7bac7-279">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="7bac7-280">sql önbellek</span><span class="sxs-lookup"><span data-stu-id="7bac7-280">sql-cache</span></span>                                         | <span data-ttu-id="7bac7-281">SQL Server önbellek komut satırı araçları.</span><span class="sxs-lookup"><span data-stu-id="7bac7-281">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="7bac7-282">kullanıcı sırları</span><span class="sxs-lookup"><span data-stu-id="7bac7-282">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="7bac7-283">Geliştirme kullanıcı sırlarını yönetir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-283">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="7bac7-284">Izle</span><span class="sxs-lookup"><span data-stu-id="7bac7-284">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="7bac7-285">Dosyalar değiştiğinde komutu çalıştıran bir dosya izleyicisi başlatır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-285">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="7bac7-286">Her araç hakkında daha `dotnet <tool-name> --help`fazla bilgi için yazın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-286">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="7bac7-287">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7bac7-287">Examples</span></span>

<span data-ttu-id="7bac7-288">Yeni bir .NET Core konsol uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7bac7-288">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="7bac7-289">Belirli bir dizinde bir proje ve bağımlılıkları oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7bac7-289">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="7bac7-290">Bir uygulama çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="7bac7-290">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="7bac7-291">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="7bac7-291">Environment variables</span></span>

- <span data-ttu-id="7bac7-292">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="7bac7-292">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="7bac7-293">Varsayılan konumda yüklü değillerse .NET Core çalışma saatlerinin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-293">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="7bac7-294">Windows'daki varsayılan `C:\Program Files\dotnet`konum.</span><span class="sxs-lookup"><span data-stu-id="7bac7-294">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="7bac7-295">Linux ve macOS üzerinde `/usr/share/dotnet`varsayılan konum .</span><span class="sxs-lookup"><span data-stu-id="7bac7-295">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="7bac7-296">Bu ortam değişkeni yalnızca oluşturulan yürütülebilir uygulamalar (ek hosts) aracılığıyla uygulamaları çalıştırırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-296">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="7bac7-297">`DOTNET_ROOT(x86)`bunun yerine, 64 bit işletim sistemi üzerinde 32 bit çalıştırılabilir çalıştırılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-297">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="7bac7-298">Genel paketler klasörü.</span><span class="sxs-lookup"><span data-stu-id="7bac7-298">The global packages folder.</span></span> <span data-ttu-id="7bac7-299">Ayarlanmamışsa, varsayılan `~/.nuget/packages` olarak Unix'te veya `%userprofile%\.nuget\packages` Windows'da olur.</span><span class="sxs-lookup"><span data-stu-id="7bac7-299">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="7bac7-300">Çalışma süresini yüklerken paylaşılan ana bilgisayar tarafından kullanılacak servis dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-300">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="7bac7-301">.NET Core karşılama ve telemetri iletilerinin ilk çalıştırmada görüntülenip görüntülenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-301">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="7bac7-302">`true` Bu iletileri `true`(değerler, veya `1` `yes` kabul edilen) veya izin `false` verecek şekilde `false` `0`(değerler, , veya `no` kabul edilen) sessize almak üzere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-302">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="7bac7-303">Ayarlanmazsa, varsayılan `false` değerdir ve iletiler ilk çalıştırmada görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-303">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="7bac7-304">Bu bayrağın telemetri üzerinde hiçbir `DOTNET_CLI_TELEMETRY_OPTOUT` etkisi olmadığını unutmayın (telemetri göndermeyi devre dışı bırakmak için bkz.</span><span class="sxs-lookup"><span data-stu-id="7bac7-304">Note that this flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="7bac7-305">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft'a gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-305">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="7bac7-306">Telemetri özelliğini devre dışı bırakacak şekilde `1`ayarlayın `yes` (değerler `true`, veya kabul edilir). `true`</span><span class="sxs-lookup"><span data-stu-id="7bac7-306">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="7bac7-307">Aksi takdirde, `false` telemetri özellikleri `false`(değerler , `0`veya `no` kabul) içine tercih etmek için ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-307">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="7bac7-308">Ayaredilmezse, varsayılan `false` ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-308">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="7bac7-309">.NET Core çalışma zamanı, paylaşılan çerçeve veya SDK'nın genel konumdan çözülüp çözülmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-309">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="7bac7-310">Ayarlanmazise, varsayılan olarak 1 `true`(mantıksal).</span><span class="sxs-lookup"><span data-stu-id="7bac7-310">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="7bac7-311">Genel konumdan `false`çözüme kavuşturulması ve .NET Core yüklemelerini yalıtmak için 0 (mantıksal) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-311">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="7bac7-312">Çok düzeyli arama hakkında daha fazla bilgi [için, Çok düzeyli SharedFX Arama'ya](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-312">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="7bac7-313">`DOTNET_ROLL_FORWARD`**.NET Core 3.x SDK ile başlayan kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="7bac7-313">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="7bac7-314">Yuvarlanan ileri davranışını belirler.</span><span class="sxs-lookup"><span data-stu-id="7bac7-314">Determines roll forward behavior.</span></span> <span data-ttu-id="7bac7-315">Daha fazla bilgi `--roll-forward` için bu makalenin önceki seçeneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-315">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="7bac7-316">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**.NET Core 2.x SDK'da mevcuttur.**</span><span class="sxs-lookup"><span data-stu-id="7bac7-316">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="7bac7-317">Devre dışı bırakır küçük sürüm, `0`eğer ayarlanırsa.</span><span class="sxs-lookup"><span data-stu-id="7bac7-317">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="7bac7-318">Daha fazla bilgi için [bkz.](../whats-new/dotnet-core-2-1.md#roll-forward)</span><span class="sxs-lookup"><span data-stu-id="7bac7-318">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="7bac7-319">CLI UI'nin dilini ayarlar. `en-us`</span><span class="sxs-lookup"><span data-stu-id="7bac7-319">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="7bac7-320">Desteklenen değerler Visual Studio ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-320">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="7bac7-321">Daha fazla bilgi için [Visual Studio yükleme belgelerinde](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)yükleyici dilini değiştirme bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7bac7-321">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="7bac7-322">.NET kaynak yöneticisi kuralları geçerlidir, böylece&mdash; `CultureInfo` ağaçtaki torunları da seçebileceğiniz tam bir eşleşme seçmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="7bac7-322">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="7bac7-323">Örneğin, bunu `fr-CA`ayarlarsanız, CLI `fr` çevirileri bulur ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="7bac7-323">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="7bac7-324">Desteklenmeyen bir dile ayarlarsanız, CLI İngilizce'ye geri döner.</span><span class="sxs-lookup"><span data-stu-id="7bac7-324">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="7bac7-325">GUI özellikli oluşturulan yürütülebilirler için - normalde belirli hata sınıfları için gösteren iletişim açılır pencereaçılır penceresini devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-325">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="7bac7-326">Sadece bu `stderr` gibi durumlarda yazar ve çıkar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-326">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="7bac7-327">CLI seçeneğine `--additional-deps`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="7bac7-327">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="7bac7-328">Algılanan RID geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="7bac7-328">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="7bac7-329">Montaj çözünürlüğünün bazı durumlarda geri aldığı "paylaşılan deponun" konumu.</span><span class="sxs-lookup"><span data-stu-id="7bac7-329">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="7bac7-330">Başlangıç kancalarını yüklemek ve çalıştırmak için montajların listesi.</span><span class="sxs-lookup"><span data-stu-id="7bac7-330">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="7bac7-331">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="7bac7-331">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="7bac7-332">Barındırma bileşenlerinden gelen tanılama izlemelerini `dotnet.exe` `hostfxr`denetler, örneğin , , ve `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="7bac7-332">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="7bac7-333">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bac7-333">See also</span></span>

- [<span data-ttu-id="7bac7-334">Runtime Yapılandırma Dosyaları</span><span class="sxs-lookup"><span data-stu-id="7bac7-334">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="7bac7-335">.NET Core çalışma zamanı yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="7bac7-335">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
