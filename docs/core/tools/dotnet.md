---
title: DotNet komutu
description: DotNet komutu (.NET Core CLI için genel sürücü) ve kullanımı hakkında bilgi edinin.
ms.date: 02/13/2020
ms.openlocfilehash: 4476dcf36455e0dc1b89712409818cf7e0352f2c
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537671"
---
# <a name="dotnet-command"></a><span data-ttu-id="9cbf8-103">DotNet komutu</span><span class="sxs-lookup"><span data-stu-id="9cbf8-103">dotnet command</span></span>

<span data-ttu-id="9cbf8-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="9cbf8-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9cbf8-105">Name</span><span class="sxs-lookup"><span data-stu-id="9cbf8-105">Name</span></span>

<span data-ttu-id="9cbf8-106">`dotnet` -.NET Core CLI için genel sürücü.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9cbf8-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="9cbf8-107">Synopsis</span></span>

<span data-ttu-id="9cbf8-108">Kullanılabilir komutlar ve ortam hakkında bilgi almak için:</span><span class="sxs-lookup"><span data-stu-id="9cbf8-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [--version] [--info] [--list-runtimes] [--list-sdks]

dotnet -h|--help
```

<span data-ttu-id="9cbf8-109">Bir komutu çalıştırmak için (SDK yüklemesi gerektirir):</span><span class="sxs-lookup"><span data-stu-id="9cbf8-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity <LEVEL>]
    [command-options] [arguments]
```

<span data-ttu-id="9cbf8-110">Bir uygulamayı çalıştırmak için:</span><span class="sxs-lookup"><span data-stu-id="9cbf8-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath <PATH>] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps <PATH>]
    [--fx-version <VERSION>]  [--roll-forward <SETTING>]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="9cbf8-111">`--roll-forward` , .NET Core 3. x sürümünden bu yana kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="9cbf8-112">`--roll-forward-on-no-candidate-fx`.NET Core 2. x için kullanın.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="9cbf8-113">Description</span><span class="sxs-lookup"><span data-stu-id="9cbf8-113">Description</span></span>

<span data-ttu-id="9cbf8-114">`dotnet`Komutun iki işlevi vardır:</span><span class="sxs-lookup"><span data-stu-id="9cbf8-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="9cbf8-115">.NET Core projeleriyle çalışmak için komutlar sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="9cbf8-116">Örneğin, [`dotnet build`](dotnet-build.md) bir proje oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="9cbf8-117">Her komut kendi seçeneklerini ve bağımsız değişkenlerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="9cbf8-118">Tüm komutlar, `--help` komutu kullanma hakkında kısa bir belge yazdırma seçeneğini destekler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="9cbf8-119">.NET Core uygulamaları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="9cbf8-120">Uygulamayı çalıştırmak için bir uygulama dosyasının yolunu belirtin `.dll` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-120">You specify the path to an application `.dll` file to run the application.</span></span>  <span data-ttu-id="9cbf8-121">Uygulamayı çalıştırmak için, konsol uygulamaları söz konusu olduğunda giriş noktasını bulmak ve yürütmek anlamına gelir `Main` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-121">To run the application means to find and execute the entry point, which in the case of console apps is the `Main` method.</span></span> <span data-ttu-id="9cbf8-122">Örneğin, `dotnet myapp.dll` `myapp` uygulamayı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-122">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="9cbf8-123">Dağıtım seçenekleri hakkında bilgi edinmek için bkz. [.NET Core uygulama dağıtımı](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-123">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="9cbf8-124">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9cbf8-124">Options</span></span>

<span data-ttu-id="9cbf8-125">Farklı seçenekler, `dotnet` bir komut çalıştırmak ve bir uygulamayı çalıştırmak için tek başına kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-125">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="9cbf8-126">Tek başına DotNet seçenekleri</span><span class="sxs-lookup"><span data-stu-id="9cbf8-126">Options for dotnet by itself</span></span>

<span data-ttu-id="9cbf8-127">Aşağıdaki seçenekler `dotnet` kendi kendine yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-127">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="9cbf8-128">Örneğin, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-128">For example, `dotnet --info`.</span></span> <span data-ttu-id="9cbf8-129">Ortamla ilgili bilgi yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-129">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="9cbf8-130">.NET Core yüklemesi ve geçerli işletim sistemi gibi makine ortamıyla ilgili ayrıntılı bilgileri yazdırır ve .NET Core sürümünün SHA 'sini yürütün.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-130">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="9cbf8-131">Kullanımda olan .NET Core SDK sürümünü yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-131">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="9cbf8-132">Yüklü .NET Core çalışma zamanlarının listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-132">Prints out a list of the installed .NET Core runtimes.</span></span> <span data-ttu-id="9cbf8-133">SDK 'nın x86 sürümü yalnızca x86 çalışma zamanlarını listeler ve SDK 'nın x64 sürümü yalnızca x64 çalışma zamanları listeler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-133">An x86 version of the SDK lists only x86 runtimes, and an x64 version of the SDK lists only x64 runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="9cbf8-134">Yüklü .NET Core SDK 'larının listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-134">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9cbf8-135">Kullanılabilir komutların bir listesini yazdırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-135">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="9cbf8-136">Komut çalıştırmak için SDK seçenekleri</span><span class="sxs-lookup"><span data-stu-id="9cbf8-136">SDK options for running a command</span></span>

<span data-ttu-id="9cbf8-137">Aşağıdaki seçenekler `dotnet` bir komutla yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-137">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="9cbf8-138">Örneğin, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-138">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="9cbf8-139">Tanılama çıkışını izin vermez.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-139">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="9cbf8-140">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9cbf8-141">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="9cbf8-142">Her komutta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-142">Not supported in every command.</span></span> <span data-ttu-id="9cbf8-143">Bu seçeneğin kullanılabilir olup olmadığını anlamak için belirli komut sayfasına bakın.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-143">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9cbf8-144">Gibi belirli bir komutun belgelerini yazdırır `dotnet build --help` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-144">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="9cbf8-145">Her komut, bu komuta özgü seçenekleri tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-145">Each command defines options specific to that command.</span></span> <span data-ttu-id="9cbf8-146">Kullanılabilir seçeneklerin listesi için bkz. özel komut sayfası.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-146">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="9cbf8-147">Çalışma zamanı seçenekleri</span><span class="sxs-lookup"><span data-stu-id="9cbf8-147">Runtime options</span></span>

<span data-ttu-id="9cbf8-148">Bir uygulama çalıştırıldığında aşağıdaki seçenekler mevcuttur `dotnet` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-148">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="9cbf8-149">Örneğin, `dotnet myapp.dll --roll-forward Major`.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-149">For example, `dotnet myapp.dll --roll-forward Major`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="9cbf8-150">Araştırmanın yoklama ilkesini ve derlemelerini içeren yol.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-150">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="9cbf8-151">Dosyadaki ek *.deps.js* yolu.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-151">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="9cbf8-152">Dosyadaki bir *deps.js* , derleme çakışmalarını çözmek için kullanılan bağımlılıklar, derleme bağımlılıkları ve sürüm bilgilerinin bir listesini içerir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-152">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="9cbf8-153">Daha fazla bilgi için bkz. GitHub 'da [çalışma zamanı yapılandırma dosyaları](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-153">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--depsfile <PATH_TO_DEPSFILE>`**

  <span data-ttu-id="9cbf8-154">Dosyadaki *deps.js* yolu.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-154">Path to the *deps.json* file.</span></span> <span data-ttu-id="9cbf8-155">*deps.js* dosyadaki bir yapılandırma, uygulamayı çalıştırmak için gerekli bağımlılıklar hakkında bilgiler içeren bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-155">A *deps.json* file is a configuration file that contains information about dependencies necessary to run the application.</span></span> <span data-ttu-id="9cbf8-156">Bu dosya .NET Core SDK tarafından oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-156">This file is generated by the .NET Core SDK.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="9cbf8-157">Dosyadaki bir *runtimeconfig.js* yolu.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-157">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="9cbf8-158">Dosya *runtimeconfig.js* , çalışma zamanı ayarlarını içeren bir yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-158">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="9cbf8-159">Daha fazla bilgi için bkz. [.NET Core çalışma zamanı yapılandırma ayarları](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="9cbf8-159">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="9cbf8-160">**`--roll-forward <SETTING>`\*\*\*\*.NET Core SDK 3,0 ' den başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="9cbf8-160">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="9cbf8-161">Uygulamaya nasıl iletme uygulanacağını denetler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-161">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="9cbf8-162">`SETTING`Aşağıdaki değerlerden biri olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-162">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="9cbf8-163">Belirtilmemişse, `Minor` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-163">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="9cbf8-164">`LatestPatch` -En yüksek düzeltme eki sürümüne ilet.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-164">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="9cbf8-165">Bu, ikincil sürüm iletmeyi devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-165">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="9cbf8-166">`Minor` -İstenen alt sürüm eksikse, en düşük düzeydeki sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-166">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="9cbf8-167">İstenen ikincil sürüm varsa, LatestPatch ilkesi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-167">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="9cbf8-168">`Major` -İstenen ana sürüm eksikse, en düşük ana sürüme ve en düşük alt sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-168">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="9cbf8-169">İstenen ana sürüm varsa, Ikincil ilke kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-169">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="9cbf8-170">`LatestMinor` -İstenen alt sürüm mevcut olsa bile en yüksek düzeyde alt sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-170">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="9cbf8-171">Bileşen barındırma senaryolarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-171">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="9cbf8-172">`LatestMajor` -İstenen ana mevcut olsa bile en yüksek ve en yüksek düzeyde alt sürüme ilet.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-172">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="9cbf8-173">Bileşen barındırma senaryolarına yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-173">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="9cbf8-174">`Disable` -İleri geri alma.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-174">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="9cbf8-175">Yalnızca belirtilen sürüme bağlayın.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-175">Only bind to specified version.</span></span> <span data-ttu-id="9cbf8-176">Bu ilke, en son düzeltme eklerine iletme özelliğini devre dışı bıraktığından genel kullanım için önerilmez.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-176">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="9cbf8-177">Bu değer yalnızca test için önerilir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-177">This value is only recommended for testing.</span></span>

  <span data-ttu-id="9cbf8-178">Hariç `Disable` olmak üzere, tüm ayarlar kullanılabilir en yüksek düzeltme eki sürümünü kullanacaktır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-178">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

  <span data-ttu-id="9cbf8-179">İleri sarma davranışı Ayrıca bir proje dosyası özelliği, çalışma zamanı yapılandırma dosyası özelliği ve ortam değişkeni içinde de yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-179">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="9cbf8-180">Daha fazla bilgi için bkz. [ana sürüm çalışma zamanı ileri iletme](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="9cbf8-180">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="9cbf8-181">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*.NET Core 2. x SDK ' da kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="9cbf8-181">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="9cbf8-182">Gerekli paylaşılan çerçeve kullanılabilir olmadığında davranışını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-182">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="9cbf8-183">`N` şunları yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9cbf8-183">`N` can be:</span></span>

  - <span data-ttu-id="9cbf8-184">`0` -Hatta ikincil sürüm iletmeyi devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-184">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="9cbf8-185">`1` -Önemli sürümde değil, küçük sürümde ilet.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-185">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="9cbf8-186">Bu, varsayılan davranıştır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-186">This is the default behavior.</span></span>
  - <span data-ttu-id="9cbf8-187">`2` -Küçük ve büyük sürümlerde ilet.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-187">`2` - Roll forward on minor and major versions.</span></span>

  <span data-ttu-id="9cbf8-188">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="9cbf8-188">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="9cbf8-189">.NET Core 3,0 ile başlayarak bu seçeneğin yerini almıştır `--roll-forward` ve bunun yerine bu seçenek kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-189">Starting with .NET Core 3.0, this option is superseded by `--roll-forward`, and that option should be used instead.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="9cbf8-190">Uygulamayı çalıştırmak için kullanılacak .NET Core çalışma zamanının sürümü.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-190">Version of the .NET Core runtime to use to run the application.</span></span>

  <span data-ttu-id="9cbf8-191">Bu seçenek, uygulamanın dosyasındaki ilk Framework başvurusunun sürümünü geçersiz kılar `.runtimeconfig.json` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-191">This option overrides the version of the first framework reference in the application's `.runtimeconfig.json` file.</span></span> <span data-ttu-id="9cbf8-192">Bu, yalnızca tek bir çerçeve başvurusu varsa beklendiği gibi çalıştığı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-192">This means it only works as expected if there's just one framework reference.</span></span> <span data-ttu-id="9cbf8-193">Uygulamanın birden fazla Framework başvurusu varsa, bu seçeneğin kullanılması hatalara neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-193">If the application has more than one framework reference, using this option may cause errors.</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="9cbf8-194">dotnet komutları</span><span class="sxs-lookup"><span data-stu-id="9cbf8-194">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="9cbf8-195">Genel</span><span class="sxs-lookup"><span data-stu-id="9cbf8-195">General</span></span>

| <span data-ttu-id="9cbf8-196">Komut</span><span class="sxs-lookup"><span data-stu-id="9cbf8-196">Command</span></span>                                       | <span data-ttu-id="9cbf8-197">İşlev</span><span class="sxs-lookup"><span data-stu-id="9cbf8-197">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="9cbf8-198">dotnet build</span><span class="sxs-lookup"><span data-stu-id="9cbf8-198">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="9cbf8-199">.NET Core uygulaması oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-199">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="9cbf8-200">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="9cbf8-200">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="9cbf8-201">Bir yapı tarafından başlatılan sunucularla etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-201">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="9cbf8-202">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="9cbf8-202">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="9cbf8-203">Derleme çıktılarını temizle.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-203">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="9cbf8-204">dotnet help</span><span class="sxs-lookup"><span data-stu-id="9cbf8-204">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="9cbf8-205">Komutu için çevrimiçi daha ayrıntılı belgeler gösterir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-205">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="9cbf8-206">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="9cbf8-206">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="9cbf8-207">Geçerli bir Preview 2 projesini .NET Core SDK 1,0 projesine geçirir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-207">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="9cbf8-208">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="9cbf8-208">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="9cbf8-209">MSBuild komut satırına erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-209">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="9cbf8-210">dotnet new</span><span class="sxs-lookup"><span data-stu-id="9cbf8-210">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="9cbf8-211">Belirli bir şablon için C# veya F # projesi başlatır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-211">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="9cbf8-212">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="9cbf8-212">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="9cbf8-213">Kodunuzun bir NuGet paketini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-213">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="9cbf8-214">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="9cbf8-214">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="9cbf8-215">.NET Framework 'e bağımlı veya kendi kendine içerilen bir uygulama yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-215">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="9cbf8-216">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="9cbf8-216">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="9cbf8-217">Belirli bir uygulama için bağımlılıkları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-217">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="9cbf8-218">dotnet run</span><span class="sxs-lookup"><span data-stu-id="9cbf8-218">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="9cbf8-219">Uygulamayı kaynaktan çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-219">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="9cbf8-220">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="9cbf8-220">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="9cbf8-221">Bir çözüm dosyasındaki projeleri ekleme, kaldırma ve listeleme seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-221">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="9cbf8-222">dotnet store</span><span class="sxs-lookup"><span data-stu-id="9cbf8-222">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="9cbf8-223">Derlemeleri çalışma zamanı paket deposunda depolar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-223">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="9cbf8-224">dotnet test</span><span class="sxs-lookup"><span data-stu-id="9cbf8-224">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="9cbf8-225">Testleri bir Test Çalıştırıcısı kullanarak çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-225">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="9cbf8-226">Proje başvuruları</span><span class="sxs-lookup"><span data-stu-id="9cbf8-226">Project references</span></span>

<span data-ttu-id="9cbf8-227">Komut</span><span class="sxs-lookup"><span data-stu-id="9cbf8-227">Command</span></span> | <span data-ttu-id="9cbf8-228">İşlev</span><span class="sxs-lookup"><span data-stu-id="9cbf8-228">Function</span></span>
--- | ---
[<span data-ttu-id="9cbf8-229">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="9cbf8-229">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="9cbf8-230">Bir proje başvurusu ekler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-230">Adds a project reference.</span></span>
[<span data-ttu-id="9cbf8-231">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="9cbf8-231">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="9cbf8-232">Proje başvurularını listeler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-232">Lists project references.</span></span>
[<span data-ttu-id="9cbf8-233">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="9cbf8-233">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="9cbf8-234">Proje başvurusunu kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-234">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="9cbf8-235">NuGet paketleri</span><span class="sxs-lookup"><span data-stu-id="9cbf8-235">NuGet packages</span></span>

<span data-ttu-id="9cbf8-236">Komut</span><span class="sxs-lookup"><span data-stu-id="9cbf8-236">Command</span></span> | <span data-ttu-id="9cbf8-237">İşlev</span><span class="sxs-lookup"><span data-stu-id="9cbf8-237">Function</span></span>
--- | ---
[<span data-ttu-id="9cbf8-238">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="9cbf8-238">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="9cbf8-239">Bir NuGet paketi ekler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-239">Adds a NuGet package.</span></span>
[<span data-ttu-id="9cbf8-240">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="9cbf8-240">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="9cbf8-241">Bir NuGet paketini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-241">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="9cbf8-242">NuGet komutları</span><span class="sxs-lookup"><span data-stu-id="9cbf8-242">NuGet commands</span></span>

<span data-ttu-id="9cbf8-243">Komut</span><span class="sxs-lookup"><span data-stu-id="9cbf8-243">Command</span></span> | <span data-ttu-id="9cbf8-244">İşlev</span><span class="sxs-lookup"><span data-stu-id="9cbf8-244">Function</span></span>
--- | ---
[<span data-ttu-id="9cbf8-245">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="9cbf8-245">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="9cbf8-246">Sunucudan bir paketi siler veya listesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-246">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="9cbf8-247">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="9cbf8-247">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="9cbf8-248">Bir paketi sunucuya gönderir ve yayımlar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-248">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="9cbf8-249">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="9cbf8-249">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="9cbf8-250">Http-istek önbelleği, geçici önbellek veya makine genelindeki genel paketler klasörü gibi yerel NuGet kaynaklarını temizler veya listeler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-250">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="9cbf8-251">dotnet nuget add source</span><span class="sxs-lookup"><span data-stu-id="9cbf8-251">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="9cbf8-252">Bir NuGet kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-252">Adds a NuGet source.</span></span>
[<span data-ttu-id="9cbf8-253">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="9cbf8-253">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="9cbf8-254">Bir NuGet kaynağını devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-254">Disables a NuGet source.</span></span>
[<span data-ttu-id="9cbf8-255">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="9cbf8-255">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="9cbf8-256">Bir NuGet kaynağını sunar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-256">Enables a NuGet source.</span></span>
[<span data-ttu-id="9cbf8-257">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="9cbf8-257">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="9cbf8-258">Tüm yapılandırılmış NuGet kaynaklarını listeler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-258">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="9cbf8-259">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="9cbf8-259">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="9cbf8-260">Bir NuGet kaynağını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-260">Removes a NuGet source.</span></span>
[<span data-ttu-id="9cbf8-261">dotnet nuget update source</span><span class="sxs-lookup"><span data-stu-id="9cbf8-261">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="9cbf8-262">Bir NuGet kaynağını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-262">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="9cbf8-263">Küresel, araç yolu ve yerel araçlar komutları</span><span class="sxs-lookup"><span data-stu-id="9cbf8-263">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="9cbf8-264">Araçlar, NuGet paketlerinden yüklenen ve komut isteminden çağrılan konsol uygulamalarıdır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-264">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="9cbf8-265">Araçları kendiniz yazabilir veya üçüncü taraflarca yazılmış Araçları yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-265">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="9cbf8-266">Araçlar genel araçlar, araç yolu araçları ve yerel araçlar olarak da bilinir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-266">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="9cbf8-267">Daha fazla bilgi için bkz. [.NET Core araçlarına genel bakış](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="9cbf8-267">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="9cbf8-268">Genel ve araç yolu araçları .NET Core SDK 2,1 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-268">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="9cbf8-269">Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-269">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="9cbf8-270">Komut</span><span class="sxs-lookup"><span data-stu-id="9cbf8-270">Command</span></span> | <span data-ttu-id="9cbf8-271">İşlev</span><span class="sxs-lookup"><span data-stu-id="9cbf8-271">Function</span></span>
--- | ---
[<span data-ttu-id="9cbf8-272">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="9cbf8-272">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="9cbf8-273">Makinenize bir araç kurar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-273">Installs a tool on your machine.</span></span>
[<span data-ttu-id="9cbf8-274">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="9cbf8-274">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="9cbf8-275">Makinenizde yüklü olan tüm genel, araç-yol veya yerel araçları listeler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-275">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="9cbf8-276">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="9cbf8-276">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="9cbf8-277">Bir aracı makinenizden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-277">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="9cbf8-278">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="9cbf8-278">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="9cbf8-279">Makinenizde yüklü bir aracı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-279">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="9cbf8-280">Ek araçlar</span><span class="sxs-lookup"><span data-stu-id="9cbf8-280">Additional tools</span></span>

<span data-ttu-id="9cbf8-281">.NET Core SDK 2.1.300 ' den itibaren, yalnızca kullanılarak proje bazında kullanılabilen birçok araç, `DotnetCliToolReference` .NET Core SDK bir parçası olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-281">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="9cbf8-282">Bu araçlar aşağıdaki tabloda listelenmiştir:</span><span class="sxs-lookup"><span data-stu-id="9cbf8-282">These tools are listed in the following table:</span></span>

| <span data-ttu-id="9cbf8-283">Araç</span><span class="sxs-lookup"><span data-stu-id="9cbf8-283">Tool</span></span>                                              | <span data-ttu-id="9cbf8-284">İşlev</span><span class="sxs-lookup"><span data-stu-id="9cbf8-284">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="9cbf8-285">geliştirme-CERT</span><span class="sxs-lookup"><span data-stu-id="9cbf8-285">dev-certs</span></span>                                         | <span data-ttu-id="9cbf8-286">Geliştirme sertifikaları oluşturur ve yönetir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-286">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="9cbf8-287">aşv</span><span class="sxs-lookup"><span data-stu-id="9cbf8-287">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="9cbf8-288">Komut satırı araçlarını Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-288">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="9cbf8-289">SQL-Cache</span><span class="sxs-lookup"><span data-stu-id="9cbf8-289">sql-cache</span></span>                                         | <span data-ttu-id="9cbf8-290">Önbellek komut satırı araçlarını SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-290">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="9cbf8-291">Kullanıcı gizli dizileri</span><span class="sxs-lookup"><span data-stu-id="9cbf8-291">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="9cbf8-292">Geliştirme Kullanıcı gizli dizilerini yönetir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-292">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="9cbf8-293">Servisi</span><span class="sxs-lookup"><span data-stu-id="9cbf8-293">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="9cbf8-294">Dosyalar değiştiğinde bir komutu çalıştıran bir dosya İzleyicisi başlatır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-294">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="9cbf8-295">Her araç hakkında daha fazla bilgi için, yazın `dotnet <tool-name> --help` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-295">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="9cbf8-296">Örnekler</span><span class="sxs-lookup"><span data-stu-id="9cbf8-296">Examples</span></span>

<span data-ttu-id="9cbf8-297">Yeni bir .NET Core konsol uygulaması oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9cbf8-297">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="9cbf8-298">Belirli bir dizinde bir proje ve onun bağımlılıklarını oluşturun:</span><span class="sxs-lookup"><span data-stu-id="9cbf8-298">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="9cbf8-299">Bir uygulamayı çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="9cbf8-299">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="9cbf8-300">Ortam değişkenleri</span><span class="sxs-lookup"><span data-stu-id="9cbf8-300">Environment variables</span></span>

- <span data-ttu-id="9cbf8-301">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="9cbf8-301">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="9cbf8-302">Varsayılan konumda yüklü değilse, .NET Core çalışma zamanlarının konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-302">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="9cbf8-303">Windows üzerinde varsayılan konum `C:\Program Files\dotnet` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-303">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="9cbf8-304">Linux ve macOS 'ta varsayılan konum `/usr/share/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-304">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="9cbf8-305">Bu ortam değişkeni yalnızca oluşturulan yürütülebilir dosyalar (apphosts) aracılığıyla uygulamalar çalıştırılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-305">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="9cbf8-306">`DOTNET_ROOT(x86)` , 64 bit IŞLETIM sisteminde 32 bitlik bir yürütülebilir dosya çalıştırılırken kullanılır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-306">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="9cbf8-307">Genel paketler klasörü.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-307">The global packages folder.</span></span> <span data-ttu-id="9cbf8-308">Ayarlanmamışsa, varsayılan olarak `~/.nuget/packages` UNIX veya `%userprofile%\.nuget\packages` Windows üzerinde olur.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-308">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="9cbf8-309">Çalışma zamanı yüklenirken paylaşılan konak tarafından kullanılacak bakım dizininin konumunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-309">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="9cbf8-310">.NET Core karşılama ve telemetri iletilerinin ilk çalıştırmada görüntülenip görüntülenmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-310">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="9cbf8-311">`true`Bu iletilerin sessize (değerler `true` , `1` veya `yes` kabul edildi) veya `false` izin ver (değerler `false` , `0` veya `no` kabul edildi) olarak ayarlanmış olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-311">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="9cbf8-312">Ayarlanmamışsa, varsayılan olur `false` ve iletiler ilk çalıştırmada görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-312">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="9cbf8-313">Bu bayrağın telemetri üzerinde hiçbir etkisi yoktur ( `DOTNET_CLI_TELEMETRY_OPTOUT` telemetri göndermek için bkz.).</span><span class="sxs-lookup"><span data-stu-id="9cbf8-313">This flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="9cbf8-314">.NET Core araçları kullanımıyla ilgili verilerin toplanıp Microsoft 'a gönderilip gönderilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-314">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="9cbf8-315">`true`Telemetri özelliğini devre dışı bırakmak için olarak ayarlayın (değerler `true` , `1` veya `yes` kabul edildi).</span><span class="sxs-lookup"><span data-stu-id="9cbf8-315">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="9cbf8-316">Aksi takdirde, `false` telemetri özelliklerini (değerler `false` , `0` veya `no` kabul edildi) kabul etmek için olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-316">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="9cbf8-317">Ayarlanmamışsa, varsayılan olarak `false` ve telemetri özelliği etkindir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-317">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="9cbf8-318">.NET Core çalışma zamanı, paylaşılan Framework veya SDK 'nın genel konumdan çözümlenip çözümlenmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-318">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="9cbf8-319">Ayarlanmazsa, varsayılan olarak 1 (mantıksal) olur `true` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-319">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="9cbf8-320">`false`Genel konumdan çözümlenmemelidir ve yalıtılmış .NET Core yüklemelerine sahip olmak için 0 (mantıksal) olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-320">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="9cbf8-321">Çoklu düzey arama hakkında daha fazla bilgi için bkz. [çok düzeyli SharedFX arama](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="9cbf8-321">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="9cbf8-322">`DOTNET_ROLL_FORWARD`**.NET Core 3. x ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="9cbf8-322">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="9cbf8-323">İleri alma davranışını belirler.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-323">Determines roll forward behavior.</span></span> <span data-ttu-id="9cbf8-324">Daha fazla bilgi için `--roll-forward` Bu makaledeki önceki seçeneğe bakın.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-324">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="9cbf8-325">`DOTNET_ROLL_FORWARD_TO_PRERELEASE`**.NET Core 3. x ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="9cbf8-325">`DOTNET_ROLL_FORWARD_TO_PRERELEASE` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="9cbf8-326">`1`(Etkin) olarak ayarlandıysa, yayın sürümünden yayın öncesi sürümüne ileri doğru bir şekilde geri dönme imkanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-326">If set to `1` (enabled), enables rolling forward to a pre-release version from a release version.</span></span> <span data-ttu-id="9cbf8-327">Varsayılan olarak ( `0` -Disabled), .NET Core çalışma zamanının yayın sürümü istendiğinde, geri alma yalnızca sürüm sürümlerini göz önünde bulunduracaktır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-327">By default (`0` - disabled), when a release version of .NET Core runtime is requested, roll-forward will only consider installed release versions.</span></span>

  <span data-ttu-id="9cbf8-328">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="9cbf8-328">For more information, see [Roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

- <span data-ttu-id="9cbf8-329">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**.NET Core 2. x ' te kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="9cbf8-329">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x.**</span></span>

  <span data-ttu-id="9cbf8-330">, Olarak ayarlandıysa, ikincil sürüm iletmeyi devre dışı bırakır `0` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-330">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="9cbf8-331">Daha fazla bilgi için bkz. [Ileri alma](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="9cbf8-331">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

  <span data-ttu-id="9cbf8-332">Bu ayarın yerini .NET Core 3,0 ' de almıştır `DOTNET_ROLL_FORWARD` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-332">This setting is superseded in .NET Core 3.0 by `DOTNET_ROLL_FORWARD`.</span></span> <span data-ttu-id="9cbf8-333">Bunun yerine yeni ayarlar kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-333">The new settings should be used instead.</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="9cbf8-334">CLı Kullanıcı arabiriminin dilini, gibi bir yerel ayar değeri kullanarak ayarlar `en-us` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-334">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="9cbf8-335">Desteklenen değerler, Visual Studio ile aynıdır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-335">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="9cbf8-336">Daha fazla bilgi için [Visual Studio yükleme belgelerindeki](/visualstudio/install/install-visual-studio?view=vs-2019)yükleyici dilini değiştirme bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-336">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="9cbf8-337">.NET Resource Manager kuralları uygulanır, bu sayede tam bir eşleşme seçmeniz gerekmez, ağaçta alt &mdash; öğeleri de seçebilirsiniz `CultureInfo` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-337">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="9cbf8-338">Örneğin, olarak ayarlarsanız `fr-CA` , CLI çevirileri bulur ve kullanır `fr` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-338">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="9cbf8-339">Bunu desteklenmeyen bir dile ayarlarsanız, CLı Ingilizce 'ye geri döner.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-339">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="9cbf8-340">GUI özellikli oluşturulan yürütülebilir dosyalar için-normalde belirli hata sınıfları için gösterilen iletişim kutusu açılır penceresini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-340">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="9cbf8-341">Bu durumda yalnızca öğesine yazar `stderr` ve çıkar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-341">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="9cbf8-342">CLı seçeneğine eşdeğerdir `--additional-deps` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-342">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="9cbf8-343">Algılanan RID 'yi geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-343">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="9cbf8-344">Bazı durumlarda derleme çözümlemenin geri döndürüleceği "paylaşılan deponun" konumu.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-344">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="9cbf8-345">Başlangıç kancalarını yüklemek ve yürütmek için derlemelerin listesi.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-345">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="9cbf8-346">`DOTNET_BUNDLE_EXTRACT_BASE_DIR`**.NET Core 3. x ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="9cbf8-346">`DOTNET_BUNDLE_EXTRACT_BASE_DIR` **Available starting with .NET Core 3.x.**</span></span>

  <span data-ttu-id="9cbf8-347">Yürütülmeden önce tek dosya uygulamasının ayıklandığı bir dizini belirtir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-347">Specifies a directory to which a single-file application is extracted before it is executed.</span></span>

  <span data-ttu-id="9cbf8-348">Daha fazla bilgi için bkz. [tek dosya yürütülebilir dosyaları](../whats-new/dotnet-core-3-0.md#single-file-executables).</span><span class="sxs-lookup"><span data-stu-id="9cbf8-348">For more information, see [Single-file executables](../whats-new/dotnet-core-3-0.md#single-file-executables).</span></span>

- <span data-ttu-id="9cbf8-349">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="9cbf8-349">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="9cbf8-350">, Ve gibi barındırma bileşenlerinden tanılama izlemeyi denetler `dotnet.exe` `hostfxr` `hostpolicy` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-350">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

  * <span data-ttu-id="9cbf8-351">`COREHOST_TRACE=[0/1]` -Varsayılan, `0` -izleme devre dışı.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-351">`COREHOST_TRACE=[0/1]` - default is `0` - tracing disabled.</span></span> <span data-ttu-id="9cbf8-352">Olarak ayarlanırsa `1` , tanılama izlemesi etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-352">If set to `1`, diagnostics tracing is enabled.</span></span>
  * <span data-ttu-id="9cbf8-353">`COREHOST_TRACEFILE=<file path>` -yalnızca izleme etkinse etkilidir `COREHOST_TRACE=1` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-353">`COREHOST_TRACEFILE=<file path>` - only has effect if tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="9cbf8-354">Ayarlandığında, izleme bilgileri belirtilen dosyaya yazılır, aksi takdirde izleme bilgileri üzerine yazılır `stderr` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-354">When set, the tracing information is written to the specified file, otherwise the tracing information is written to `stderr`.</span></span> <span data-ttu-id="9cbf8-355">**.NET Core 3. x ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="9cbf8-355">**Available starting with .NET Core 3.x.**</span></span>
  * <span data-ttu-id="9cbf8-356">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` -Varsayılan değer `4` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-356">`COREHOST_TRACE_VERBOSITY=[1/2/3/4]` - default is `4`.</span></span> <span data-ttu-id="9cbf8-357">Ayar yalnızca, ile izleme etkinleştirildiğinde kullanılır `COREHOST_TRACE=1` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-357">The setting is used only when tracing is enabled via `COREHOST_TRACE=1`.</span></span> <span data-ttu-id="9cbf8-358">**.NET Core 3. x ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="9cbf8-358">**Available starting with .NET Core 3.x.**</span></span>
    * <span data-ttu-id="9cbf8-359">`4` -Tüm izleme bilgileri yazılır</span><span class="sxs-lookup"><span data-stu-id="9cbf8-359">`4` - all tracing information is written</span></span>
    * <span data-ttu-id="9cbf8-360">`3` -yalnızca bilgilendirme, uyarı ve hata iletileri yazılır</span><span class="sxs-lookup"><span data-stu-id="9cbf8-360">`3` - only informational, warning and error messages are written</span></span>
    * <span data-ttu-id="9cbf8-361">`2` -yalnızca uyarı ve hata iletileri yazılır</span><span class="sxs-lookup"><span data-stu-id="9cbf8-361">`2` - only warning and error messages are written</span></span>
    * <span data-ttu-id="9cbf8-362">`1` -yalnızca hata iletileri yazılır</span><span class="sxs-lookup"><span data-stu-id="9cbf8-362">`1` - only error messages are written</span></span>

  <span data-ttu-id="9cbf8-363">Uygulama başlatma hakkında ayrıntılı izleme bilgileri almanın tipik yolu, `COREHOST_TRACE=1` uygulamayı ayarlamak ve çalıştırmak için kullanılır `COREHOST_TRACEFILE=host_trace.txt` .</span><span class="sxs-lookup"><span data-stu-id="9cbf8-363">The typical way to get detailed trace information about application startup is to set `COREHOST_TRACE=1` and `COREHOST_TRACEFILE=host_trace.txt` and then run the application.</span></span> <span data-ttu-id="9cbf8-364">`host_trace.txt`Geçerli dizinde ayrıntılı bilgiler içeren yeni bir dosya oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-364">A new file `host_trace.txt` will be created in the current directory with the detailed information.</span></span>

## <a name="see-also"></a><span data-ttu-id="9cbf8-365">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cbf8-365">See also</span></span>

- [<span data-ttu-id="9cbf8-366">Çalışma zamanı yapılandırma dosyaları</span><span class="sxs-lookup"><span data-stu-id="9cbf8-366">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="9cbf8-367">.NET Core çalışma zamanı yapılandırma ayarları</span><span class="sxs-lookup"><span data-stu-id="9cbf8-367">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
