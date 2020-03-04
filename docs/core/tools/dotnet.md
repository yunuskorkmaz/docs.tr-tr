---
title: DotNet komutu
description: DotNet komutu (.NET Core CLI için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240876"
---
# <a name="dotnet-command"></a><span data-ttu-id="77a50-103">DotNet komutu</span><span class="sxs-lookup"><span data-stu-id="77a50-103">dotnet command</span></span>

<span data-ttu-id="77a50-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="77a50-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="77a50-105">Name</span><span class="sxs-lookup"><span data-stu-id="77a50-105">Name</span></span>

<span data-ttu-id="77a50-106">`dotnet`-.NET Core CLI genel sürücü.</span><span class="sxs-lookup"><span data-stu-id="77a50-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="77a50-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="77a50-107">Synopsis</span></span>

<span data-ttu-id="77a50-108">Kullanılabilir komutlar ve ortam hakkında bilgi almak için:</span><span class="sxs-lookup"><span data-stu-id="77a50-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="77a50-109">Bir komutu çalıştırmak için (SDK yüklemesi gerektirir):</span><span class="sxs-lookup"><span data-stu-id="77a50-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="77a50-110">Bir uygulamayı çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="77a50-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="77a50-111">`--roll-forward` .NET Core 3. x sürümünden bu yana kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77a50-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="77a50-112">.NET Core 2. x için `--roll-forward-on-no-candidate-fx` kullanın.</span><span class="sxs-lookup"><span data-stu-id="77a50-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="77a50-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="77a50-113">Description</span></span>

<span data-ttu-id="77a50-114">`dotnet` komutu iki işleve sahiptir:</span><span class="sxs-lookup"><span data-stu-id="77a50-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="77a50-115">.NET Core projeleriyle çalışmak için komutlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="77a50-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="77a50-116">Örneğin, [`dotnet build`](dotnet-build.md) bir proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77a50-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="77a50-117">Her komut kendi seçeneklerini ve bağımsız değişkenlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="77a50-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="77a50-118">Tüm komutlar, komutu kullanma hakkında kısa bir belge yazdırmak için `--help` seçeneğini destekler.</span><span class="sxs-lookup"><span data-stu-id="77a50-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="77a50-119">.NET Core uygulamaları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="77a50-120">Uygulamayı çalıştırmak için bir uygulama `.dll` dosyasının yolunu belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77a50-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="77a50-121">Örneğin, `dotnet myapp.dll` `myapp` uygulamayı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="77a50-122">Dağıtım seçenekleri hakkında bilgi edinmek için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="77a50-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="77a50-123">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="77a50-123">Options</span></span>

<span data-ttu-id="77a50-124">Farklı seçenekler, bir komut çalıştırmak ve bir uygulamayı çalıştırmak için tek başına `dotnet` vardır.</span><span class="sxs-lookup"><span data-stu-id="77a50-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="77a50-125">Tek başına DotNet seçenekleri</span><span class="sxs-lookup"><span data-stu-id="77a50-125">Options for dotnet by itself</span></span>

<span data-ttu-id="77a50-126">Aşağıdaki seçenekler kendi `dotnet` içindir.</span><span class="sxs-lookup"><span data-stu-id="77a50-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="77a50-127">Örneğin, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="77a50-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="77a50-128">Ortamla ilgili bilgi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="77a50-129">.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.</span><span class="sxs-lookup"><span data-stu-id="77a50-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="77a50-130">Kullanımda olan .NET Core SDK sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="77a50-131">Yüklü .NET Core çalışma zamanlarının listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="77a50-132">Yüklü .NET Core SDK 'larının listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="77a50-133">Kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="77a50-134">Komut çalıştırmak için SDK seçenekleri</span><span class="sxs-lookup"><span data-stu-id="77a50-134">SDK options for running a command</span></span>

<span data-ttu-id="77a50-135">Aşağıdaki seçenekler bir komutla `dotnet` içindir.</span><span class="sxs-lookup"><span data-stu-id="77a50-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="77a50-136">Örneğin, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="77a50-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="77a50-137">Tanılama çıkışını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="77a50-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="77a50-138">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="77a50-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="77a50-139">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="77a50-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="77a50-140">Her komutta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="77a50-140">Not supported in every command.</span></span> <span data-ttu-id="77a50-141">Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="77a50-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="77a50-142">`dotnet build --help`gibi belirli bir komutun belgelerini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="77a50-143">Her komut, bu komuta özgü seçenekleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="77a50-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="77a50-144">Kullanılabilir seçeneklerin listesi için bkz. özel komut sayfası.</span><span class="sxs-lookup"><span data-stu-id="77a50-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="77a50-145">Çalışma zamanı seçenekleri</span><span class="sxs-lookup"><span data-stu-id="77a50-145">Runtime options</span></span>

<span data-ttu-id="77a50-146">`dotnet` bir uygulama çalıştırdığında aşağıdaki seçenekler kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77a50-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="77a50-147">Örneğin, `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="77a50-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="77a50-148">Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.</span><span class="sxs-lookup"><span data-stu-id="77a50-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="77a50-149">Ek *. Deps. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="77a50-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="77a50-150">Bir *Deps. JSON* dosyası, derleme çakışmalarını çözmek için kullanılan bağımlılıklar, derleme bağımlılıkları ve sürüm bilgilerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="77a50-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="77a50-151">Daha fazla bilgi için bkz. GitHub 'da [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) .</span><span class="sxs-lookup"><span data-stu-id="77a50-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="77a50-152">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="77a50-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="77a50-153">*Runtimeconfig. JSON* dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="77a50-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="77a50-154">*Runtimeconfig. JSON* dosyası, çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="77a50-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="77a50-155">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="77a50-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="77a50-156">**`--roll-forward-on-no-candidate-fx <N>`** **.NET Core 2. x SDK ' da kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="77a50-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="77a50-157">Gerekli paylaşılan çerçeve kullanılabilir olmadığında davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="77a50-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="77a50-158">`N` şu olabilir:</span><span class="sxs-lookup"><span data-stu-id="77a50-158">`N` can be:</span></span>

  - <span data-ttu-id="77a50-159">`0`-alt düzey sürüm iletmeyi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="77a50-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="77a50-160">`1`-önemli sürümde değil, küçük sürümde ilet.</span><span class="sxs-lookup"><span data-stu-id="77a50-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="77a50-161">Bu varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="77a50-161">This is the default behavior.</span></span>
  - <span data-ttu-id="77a50-162">`2`-küçük ve büyük sürümlerde ilet.</span><span class="sxs-lookup"><span data-stu-id="77a50-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="77a50-163">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="77a50-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="77a50-164">**`--roll-forward <SETTING>`** **.NET Core SDK 3,0 ' den başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="77a50-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="77a50-165">Uygulamaya nasıl iletme uygulanacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="77a50-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="77a50-166">`SETTING` aşağıdaki değerlerden biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="77a50-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="77a50-167">Belirtilmemişse, varsayılan değer `Minor`.</span><span class="sxs-lookup"><span data-stu-id="77a50-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="77a50-168">`LatestPatch`-en yüksek düzeltme eki sürümüne ilet.</span><span class="sxs-lookup"><span data-stu-id="77a50-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="77a50-169">Bu, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="77a50-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="77a50-170">`Minor`, gerekli alt sürüm eksikse, en düşük düzeydeki sürüme ileri doğru alın.</span><span class="sxs-lookup"><span data-stu-id="77a50-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="77a50-171">İstenen ikincil sürüm varsa, LatestPatch ilkesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77a50-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="77a50-172">`Major`-en düşük ana sürüme ve istenen ana sürüm eksikse en düşük alt sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="77a50-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="77a50-173">İstenen ana sürüm varsa, Ikincil ilke kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77a50-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="77a50-174">`LatestMinor`, istenen alt sürüm mevcut olsa bile en yüksek alt sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="77a50-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="77a50-175">Bileşen barındırma senaryolarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="77a50-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="77a50-176">`LatestMajor`, istenen ana mevcut olsa bile en yüksek büyük ve en yüksek düzeydeki sürüme ileri alın.</span><span class="sxs-lookup"><span data-stu-id="77a50-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="77a50-177">Bileşen barındırma senaryolarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="77a50-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="77a50-178">`Disable`-ileri geri alma.</span><span class="sxs-lookup"><span data-stu-id="77a50-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="77a50-179">Yalnızca belirtilen sürüme bağlayın.</span><span class="sxs-lookup"><span data-stu-id="77a50-179">Only bind to specified version.</span></span> <span data-ttu-id="77a50-180">Bu ilke, en son düzeltme eklerine iletme özelliğini devre dışı bıraktığından genel kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="77a50-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="77a50-181">Bu değer yalnızca test için önerilir.</span><span class="sxs-lookup"><span data-stu-id="77a50-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="77a50-182">`Disable`özel durumu ile, tüm ayarlar kullanılabilir en yüksek düzeltme eki sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="77a50-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="77a50-183">İleri sarma davranışı Ayrıca bir proje dosyası özelliği, çalışma zamanı yapılandırma dosyası özelliği ve ortam değişkeni içinde de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="77a50-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="77a50-184">Daha fazla bilgi için bkz. [ana sürüm çalışma zamanı ileri iletme](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="77a50-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="77a50-185">dotnet komutları</span><span class="sxs-lookup"><span data-stu-id="77a50-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="77a50-186">Genel</span><span class="sxs-lookup"><span data-stu-id="77a50-186">General</span></span>

| <span data-ttu-id="77a50-187">Komut</span><span class="sxs-lookup"><span data-stu-id="77a50-187">Command</span></span>                                       | <span data-ttu-id="77a50-188">İşlev</span><span class="sxs-lookup"><span data-stu-id="77a50-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="77a50-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="77a50-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="77a50-190">.NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77a50-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="77a50-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="77a50-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="77a50-192">Bir yapı tarafından başlatılan sunucularla etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="77a50-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="77a50-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="77a50-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="77a50-194">Derleme çıktılarını temizle.</span><span class="sxs-lookup"><span data-stu-id="77a50-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="77a50-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="77a50-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="77a50-196">Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="77a50-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="77a50-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="77a50-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="77a50-198">Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="77a50-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="77a50-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="77a50-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="77a50-200">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="77a50-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="77a50-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="77a50-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="77a50-202">Belirli bir C# şablon F# için bir veya projesini başlatır.</span><span class="sxs-lookup"><span data-stu-id="77a50-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="77a50-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="77a50-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="77a50-204">Kodunuzun bir NuGet paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="77a50-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="77a50-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="77a50-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="77a50-206">.NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="77a50-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="77a50-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="77a50-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="77a50-208">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="77a50-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="77a50-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="77a50-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="77a50-210">Uygulamayı kaynaktan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="77a50-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="77a50-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="77a50-212">Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="77a50-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="77a50-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="77a50-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="77a50-214">Derlemeleri çalışma zamanı paket deposunda depolar.</span><span class="sxs-lookup"><span data-stu-id="77a50-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="77a50-215">dotnet test</span><span class="sxs-lookup"><span data-stu-id="77a50-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="77a50-216">Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="77a50-217">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="77a50-217">Project references</span></span>

<span data-ttu-id="77a50-218">Komut</span><span class="sxs-lookup"><span data-stu-id="77a50-218">Command</span></span> | <span data-ttu-id="77a50-219">İşlev</span><span class="sxs-lookup"><span data-stu-id="77a50-219">Function</span></span>
--- | ---
[<span data-ttu-id="77a50-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="77a50-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="77a50-221">Bir proje başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="77a50-221">Adds a project reference.</span></span>
[<span data-ttu-id="77a50-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="77a50-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="77a50-223">Proje başvurularını listeler.</span><span class="sxs-lookup"><span data-stu-id="77a50-223">Lists project references.</span></span>
[<span data-ttu-id="77a50-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="77a50-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="77a50-225">Proje başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="77a50-226">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="77a50-226">NuGet packages</span></span>

<span data-ttu-id="77a50-227">Komut</span><span class="sxs-lookup"><span data-stu-id="77a50-227">Command</span></span> | <span data-ttu-id="77a50-228">İşlev</span><span class="sxs-lookup"><span data-stu-id="77a50-228">Function</span></span>
--- | ---
[<span data-ttu-id="77a50-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="77a50-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="77a50-230">Bir NuGet paketi ekler.</span><span class="sxs-lookup"><span data-stu-id="77a50-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="77a50-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="77a50-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="77a50-232">Bir NuGet paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="77a50-233">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="77a50-233">NuGet commands</span></span>

<span data-ttu-id="77a50-234">Komut</span><span class="sxs-lookup"><span data-stu-id="77a50-234">Command</span></span> | <span data-ttu-id="77a50-235">İşlev</span><span class="sxs-lookup"><span data-stu-id="77a50-235">Function</span></span>
--- | ---
[<span data-ttu-id="77a50-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="77a50-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="77a50-237">Sunucudan bir paketi siler veya listesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="77a50-238">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="77a50-238">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="77a50-239">Http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="77a50-239">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="77a50-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="77a50-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="77a50-241">Bir paketi sunucuya gönderir ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="77a50-241">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="77a50-242">Küresel, araç yolu ve yerel araçlar komutları</span><span class="sxs-lookup"><span data-stu-id="77a50-242">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="77a50-243">Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="77a50-243">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="77a50-244">Araçları kendiniz yazabilir veya üçüncü taraflarca yazılmış Araçları yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77a50-244">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="77a50-245">Araçlar genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="77a50-245">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="77a50-246">Daha fazla bilgi için bkz. [.NET Core araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="77a50-246">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="77a50-247">Genel ve araç yolu araçları .NET Core SDK 2,1 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77a50-247">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="77a50-248">Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="77a50-248">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="77a50-249">Komut</span><span class="sxs-lookup"><span data-stu-id="77a50-249">Command</span></span> | <span data-ttu-id="77a50-250">İşlev</span><span class="sxs-lookup"><span data-stu-id="77a50-250">Function</span></span>
--- | ---
[<span data-ttu-id="77a50-251">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="77a50-251">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="77a50-252">Makinenize bir araç kurar.</span><span class="sxs-lookup"><span data-stu-id="77a50-252">Installs a tool on your machine.</span></span>
[<span data-ttu-id="77a50-253">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="77a50-253">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="77a50-254">Makinenizde yüklü olan tüm genel, araç-yol veya yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="77a50-254">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="77a50-255">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="77a50-255">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="77a50-256">Bir aracı makinenizden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="77a50-256">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="77a50-257">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="77a50-257">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="77a50-258">Makinenizde yüklü bir aracı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="77a50-258">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="77a50-259">Ek araçlar</span><span class="sxs-lookup"><span data-stu-id="77a50-259">Additional tools</span></span>

<span data-ttu-id="77a50-260">.NET Core SDK 2.1.300 ile başlayarak, yalnızca .NET Core SDK bir parçası olarak yalnızca `DotnetCliToolReference` kullanılarak proje temelinde kullanılabilen birçok araç vardır.</span><span class="sxs-lookup"><span data-stu-id="77a50-260">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="77a50-261">Bu araçlar aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="77a50-261">These tools are listed in the following table:</span></span>

| <span data-ttu-id="77a50-262">Aracı</span><span class="sxs-lookup"><span data-stu-id="77a50-262">Tool</span></span>                                              | <span data-ttu-id="77a50-263">İşlev</span><span class="sxs-lookup"><span data-stu-id="77a50-263">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="77a50-264">geliştirme-CERT</span><span class="sxs-lookup"><span data-stu-id="77a50-264">dev-certs</span></span>                                         | <span data-ttu-id="77a50-265">Geliştirme sertifikaları oluşturur ve yönetir.</span><span class="sxs-lookup"><span data-stu-id="77a50-265">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="77a50-266">aşv</span><span class="sxs-lookup"><span data-stu-id="77a50-266">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="77a50-267">Komut satırı araçlarını Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="77a50-267">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="77a50-268">SQL-Cache</span><span class="sxs-lookup"><span data-stu-id="77a50-268">sql-cache</span></span>                                         | <span data-ttu-id="77a50-269">Önbellek komut satırı araçlarını SQL Server.</span><span class="sxs-lookup"><span data-stu-id="77a50-269">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="77a50-270">Kullanıcı gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="77a50-270">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="77a50-271">Geliştirme Kullanıcı gizli dizilerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="77a50-271">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="77a50-272">Servisi</span><span class="sxs-lookup"><span data-stu-id="77a50-272">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="77a50-273">Dosyalar değiştiğinde bir komutu çalıştıran bir dosya İzleyicisi başlatır.</span><span class="sxs-lookup"><span data-stu-id="77a50-273">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="77a50-274">Her araç hakkında daha fazla bilgi için `dotnet <tool-name> --help`yazın.</span><span class="sxs-lookup"><span data-stu-id="77a50-274">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="77a50-275">Örnekler</span><span class="sxs-lookup"><span data-stu-id="77a50-275">Examples</span></span>

<span data-ttu-id="77a50-276">Yeni bir .NET Core konsol uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="77a50-276">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="77a50-277">Belirli bir dizinde bir proje ve onun bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="77a50-277">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="77a50-278">Bir uygulamayı çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="77a50-278">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="77a50-279">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="77a50-279">Environment variables</span></span>

- <span data-ttu-id="77a50-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="77a50-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="77a50-281">Varsayılan konumda yüklü değilse, .NET Core çalışma zamanlarının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="77a50-281">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="77a50-282">Windows üzerindeki varsayılan konum `C:\Program Files\dotnet`.</span><span class="sxs-lookup"><span data-stu-id="77a50-282">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="77a50-283">Linux ve macOS 'ta varsayılan konum `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="77a50-283">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="77a50-284">Bu ortam değişkeni yalnızca oluşturulan yürütülebilir dosyalar (apphosts) aracılığıyla uygulamalar çalıştırılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77a50-284">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="77a50-285">`DOTNET_ROOT(x86)`, 64 bit IŞLETIM sisteminde 32 bitlik bir yürütülebilir dosya çalıştırılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="77a50-285">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="77a50-286">Genel paketler klasörü.</span><span class="sxs-lookup"><span data-stu-id="77a50-286">The global packages folder.</span></span> <span data-ttu-id="77a50-287">Ayarlanmamışsa, varsayılan olarak UNIX veya Windows üzerinde `%userprofile%\.nuget\packages` `~/.nuget/packages`.</span><span class="sxs-lookup"><span data-stu-id="77a50-287">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="77a50-288">Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="77a50-288">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="77a50-289">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="77a50-289">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="77a50-290">Telemetri özelliğinin (değerler `true`, `1`veya `yes` kabul edilir) devre dışı bırakmak için `true` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="77a50-290">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="77a50-291">Aksi takdirde, telemetri özelliklerine (değerler `false`, `0`veya `no` kabul edilir) kabul etmek için `false` olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="77a50-291">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="77a50-292">Ayarlanmamışsa, varsayılan `false` ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="77a50-292">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="77a50-293">.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="77a50-293">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="77a50-294">Ayarlanmazsa, varsayılan olarak 1 ' dir (mantıksal `true`).</span><span class="sxs-lookup"><span data-stu-id="77a50-294">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="77a50-295">Genel konumdan çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olmak için 0 (mantıksal `false`) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="77a50-295">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="77a50-296">Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="77a50-296">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="77a50-297">`DOTNET_ROLL_FORWARD` **.NET Core 3. x SDK ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="77a50-297">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="77a50-298">İleri alma davranışını belirler.</span><span class="sxs-lookup"><span data-stu-id="77a50-298">Determines roll forward behavior.</span></span> <span data-ttu-id="77a50-299">Daha fazla bilgi için bu makalenin önceki `--roll-forward` seçeneğine bakın.</span><span class="sxs-lookup"><span data-stu-id="77a50-299">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="77a50-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **.NET Core 2. x SDK ' da kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="77a50-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="77a50-301">`0`olarak ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="77a50-301">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="77a50-302">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="77a50-302">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="77a50-303">`en-us`gibi bir yerel ayar değeri kullanarak CLı Kullanıcı arabiriminin dilini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="77a50-303">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="77a50-304">Desteklenen değerler, Visual Studio ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="77a50-304">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="77a50-305">Daha fazla bilgi için [Visual Studio yükleme belgelerindeki](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)yükleyici dilini değiştirme bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="77a50-305">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="77a50-306">.NET Resource Manager kuralları uygulanır, böylece tam bir eşleşme seçmeniz gerekmez&mdash;`CultureInfo` ağacındaki alt öğeleri de seçebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="77a50-306">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="77a50-307">Örneğin, `fr-CA`olarak ayarlarsanız, CLı `fr` çevirileri bulur ve kullanır.</span><span class="sxs-lookup"><span data-stu-id="77a50-307">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="77a50-308">Bunu desteklenmeyen bir dile ayarlarsanız, CLı Ingilizce 'ye geri döner.</span><span class="sxs-lookup"><span data-stu-id="77a50-308">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="77a50-309">GUI özellikli oluşturulan yürütülebilir dosyalar için, normalde belirli hata sınıfları için gösterilen iletişim kutusu açılır penceresini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="77a50-309">For GUI-enabled generated executables - disables dialog popup which normally shows for certain classes of errors.</span></span> <span data-ttu-id="77a50-310">Yalnızca `stderr` yazar ve bu durumlarda çıkar.</span><span class="sxs-lookup"><span data-stu-id="77a50-310">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="77a50-311">CLı seçeneğine eşdeğerdir `--additional-deps`.</span><span class="sxs-lookup"><span data-stu-id="77a50-311">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="77a50-312">Algılanan RID 'yi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="77a50-312">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="77a50-313">Bazı durumlarda derleme çözümlemenin geri döndürüleceği "paylaşılan deponun" konumu.</span><span class="sxs-lookup"><span data-stu-id="77a50-313">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="77a50-314">Başlangıç kancalarını yüklemek ve yürütmek için derlemelerin listesi.</span><span class="sxs-lookup"><span data-stu-id="77a50-314">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="77a50-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="77a50-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="77a50-316">`dotnet.exe`, `hostfxr`ve `hostpolicy`gibi barındırma bileşenlerinden tanılama izlemeyi denetler.</span><span class="sxs-lookup"><span data-stu-id="77a50-316">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="77a50-317">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77a50-317">See also</span></span>

- [<span data-ttu-id="77a50-318">Çalışma zamanı yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="77a50-318">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="77a50-319">.NET Core çalışma zamanı yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="77a50-319">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
