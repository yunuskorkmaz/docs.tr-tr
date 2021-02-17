---
title: DotNet-Trace Tanılama aracı-.NET CLı
description: .NET EventPipe kullanarak, yerel profil oluşturucu olmadan çalışan bir işlemin .NET izlemelerini toplamak için DotNet-Trace CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: abf98df6e31747ea3e8013fc77b246613a3402ad
ms.sourcegitcommit: f0fc5db7bcbf212e46933e9cf2d555bb82666141
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/17/2021
ms.locfileid: "100583005"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="578be-103">DotNet-izleme performansı Analizi yardımcı programı</span><span class="sxs-lookup"><span data-stu-id="578be-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="578be-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="578be-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="578be-105">Yükleme</span><span class="sxs-lookup"><span data-stu-id="578be-105">Install</span></span>

<span data-ttu-id="578be-106">İndirmek ve yüklemek için iki yol vardır `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="578be-106">There are two ways to download and install `dotnet-trace`:</span></span>

- <span data-ttu-id="578be-107">**DotNet genel aracı:**</span><span class="sxs-lookup"><span data-stu-id="578be-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="578be-108">NuGet paketinin en son sürümünü yüklemek için `dotnet-trace` [](https://www.nuget.org/packages/dotnet-trace) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="578be-108">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- <span data-ttu-id="578be-109">**Doğrudan indirme:**</span><span class="sxs-lookup"><span data-stu-id="578be-109">**Direct download:**</span></span>

  <span data-ttu-id="578be-110">Platformunuzla eşleşen araç yürütülebilirini indirin:</span><span class="sxs-lookup"><span data-stu-id="578be-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="578be-111">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="578be-111">OS</span></span>  | <span data-ttu-id="578be-112">Platform</span><span class="sxs-lookup"><span data-stu-id="578be-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="578be-113">Windows</span><span class="sxs-lookup"><span data-stu-id="578be-113">Windows</span></span> | <span data-ttu-id="578be-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [ARM](https://aka.ms/dotnet-trace/win-arm) \| [ARM-x64](https://aka.ms/dotnet-trace/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="578be-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span></span> |
  | <span data-ttu-id="578be-115">Mac OS</span><span class="sxs-lookup"><span data-stu-id="578be-115">macOS</span></span>   | [<span data-ttu-id="578be-116">x64</span><span class="sxs-lookup"><span data-stu-id="578be-116">x64</span></span>](https://aka.ms/dotnet-trace/osx-x64) |
  | <span data-ttu-id="578be-117">Linux</span><span class="sxs-lookup"><span data-stu-id="578be-117">Linux</span></span>   | <span data-ttu-id="578be-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [ARM](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="578be-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="578be-119">`dotnet-trace`X86 uygulamasında kullanmak için, aracın karşılık gelen x86 sürümüne ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="578be-119">To use `dotnet-trace` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="578be-120">Özeti</span><span class="sxs-lookup"><span data-stu-id="578be-120">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="578be-121">Description</span><span class="sxs-lookup"><span data-stu-id="578be-121">Description</span></span>

<span data-ttu-id="578be-122">`dotnet-trace`Araç:</span><span class="sxs-lookup"><span data-stu-id="578be-122">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="578be-123">, Platformlar arası bir .NET Core aracıdır.</span><span class="sxs-lookup"><span data-stu-id="578be-123">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="578be-124">Yerel bir profil oluşturucu olmadan çalışan bir işlemin .NET Core izlemelerinin toplanmasını mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="578be-124">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="578be-125">, [`EventPipe`](./eventpipe.md) .NET Core çalışma zamanı üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="578be-125">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="578be-126">Windows, Linux veya macOS 'ta aynı deneyimi sunar.</span><span class="sxs-lookup"><span data-stu-id="578be-126">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="578be-127">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="578be-127">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="578be-128">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="578be-128">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="578be-129">DotNet-Trace yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="578be-129">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="578be-130">Komutlar</span><span class="sxs-lookup"><span data-stu-id="578be-130">Commands</span></span>

| <span data-ttu-id="578be-131">Komut</span><span class="sxs-lookup"><span data-stu-id="578be-131">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="578be-132">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="578be-132">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="578be-133">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="578be-133">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="578be-134">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="578be-134">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="578be-135">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="578be-135">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="578be-136">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="578be-136">dotnet-trace collect</span></span>

<span data-ttu-id="578be-137">Çalışan bir işlemden bir tanılama izlemesi toplar.</span><span class="sxs-lookup"><span data-stu-id="578be-137">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="578be-138">Özeti</span><span class="sxs-lookup"><span data-stu-id="578be-138">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="578be-139">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="578be-139">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="578be-140">Bellek içi dairesel arabelleğin boyutunu megabayt cinsinden ayarlar.</span><span class="sxs-lookup"><span data-stu-id="578be-140">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="578be-141">Varsayılan 256 MB.</span><span class="sxs-lookup"><span data-stu-id="578be-141">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="578be-142">Oluşturulacak CLR olaylarının ayrıntı düzeyi.</span><span class="sxs-lookup"><span data-stu-id="578be-142">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="578be-143">Boşluklarla ayrılmış olarak etkinleştirilecek CLR çalışma zamanı sağlayıcısı anahtar kelimeleriyle bir liste `+` .</span><span class="sxs-lookup"><span data-stu-id="578be-143">A list of CLR runtime provider keywords to enable separated by `+` signs.</span></span> <span data-ttu-id="578be-144">Bu, onaltılık değerleri yerine dize diğer adları aracılığıyla olay anahtar sözcükleri belirtmenize imkan tanıyan basit bir eşlemedir.</span><span class="sxs-lookup"><span data-stu-id="578be-144">This is a simple mapping that lets you specify event keywords via string aliases rather than their hex values.</span></span> <span data-ttu-id="578be-145">Örneğin, `dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:3:4` aynı olay kümesini ile ister `dotnet-trace collect --clrevents gc+gchandle --clreventlevel informational` .</span><span class="sxs-lookup"><span data-stu-id="578be-145">For example, `dotnet-trace collect --providers Microsoft-Windows-DotNETRuntime:3:4` requests the same set of events as `dotnet-trace collect --clrevents gc+gchandle --clreventlevel informational`.</span></span> <span data-ttu-id="578be-146">Aşağıdaki tabloda kullanılabilir anahtar sözcüklerin listesi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="578be-146">The table below shows the list of available keywords:</span></span>

  | <span data-ttu-id="578be-147">Anahtar sözcük dize diğer adı</span><span class="sxs-lookup"><span data-stu-id="578be-147">Keyword String Alias</span></span> | <span data-ttu-id="578be-148">Anahtar sözcük onaltılı değeri</span><span class="sxs-lookup"><span data-stu-id="578be-148">Keyword Hex Value</span></span> |
  | ------------ | ------------------- |
  | `gc` | `0x1` |
  | `gchandle` | `0x2` |
  | `fusion` | `0x4` |
  | `loader` | `0x8` |
  | `jit` | `0x10` |
  | `ngen` | `0x20` |
  | `startenumeration` | `0x40` |
  | `endenumeration` | `0x80` |
  | `security` | `0x400` |
  | `appdomainresourcemanagement` | `0x800` |
  | `jittracing` | `0x1000` |
  | `interop` | `0x2000` |
  | `contention` | `0x4000` |
  | `exception` | `0x8000` |
  | `threading` | `0x10000` |
  | `jittedmethodiltonativemap` | `0x20000` |
  | `overrideandsuppressngenevents` | `0x40000` |
  | `type` | `0x80000` |
  | `gcheapdump` | `0x100000` |
  | `gcsampledobjectallocationhigh` | `0x200000` |
  | `gcheapsurvivalandmovement` | `0x400000` |
  | `gcheapcollect` | `0x800000` |
  | `gcheapandtypenames` | `0x1000000` |
  | `gcsampledobjectallocationlow` | `0x2000000` |
  | `perftrack` | `0x20000000` |
  | `stack` | `0x40000000` |
  | `threadtransfer` | `0x80000000` |
  | `debugger` | `0x100000000` |
  | `monitoring` | `0x200000000` |
  | `codesymbols` | `0x400000000` |
  | `eventsource` | `0x800000000` |
  | `compilation` | `0x1000000000` |
  | `compilationdiagnostic` | `0x2000000000` |
  | `methoddiagnostic` | `0x4000000000` |
  | `typediagnostic` | `0x8000000000` |

  <span data-ttu-id="578be-149">CLR sağlayıcısı hakkında daha ayrıntılı bilgi için bkz. [.NET çalışma zamanı sağlayıcısı başvuru belgeleri](../../fundamentals/diagnostics/runtime-events.md).</span><span class="sxs-lookup"><span data-stu-id="578be-149">You can read about the CLR provider more in detail on the [.NET runtime provider reference documentation](../../fundamentals/diagnostics/runtime-events.md).</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="578be-150">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="578be-150">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="578be-151">Varsayılan değer: `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="578be-151">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="578be-152">İzlemenin toplanacağı işlemin adı.</span><span class="sxs-lookup"><span data-stu-id="578be-152">The name of the process to collect the trace from.</span></span>

- **`--diagnostic-port <path-to-port>`**

  <span data-ttu-id="578be-153">Oluşturulacak tanılama bağlantı noktasının adı.</span><span class="sxs-lookup"><span data-stu-id="578be-153">The name of the diagnostic port to create.</span></span> <span data-ttu-id="578be-154">Uygulamanın başlangıcında bir izleme toplamak için bu seçeneği nasıl kullanacağınızı öğrenmek için bkz. [Uygulama başlangıcında bir izleme toplamak için tanılama bağlantı noktası kullanma](#use-diagnostic-port-to-collect-a-trace-from-app-startup) .</span><span class="sxs-lookup"><span data-stu-id="578be-154">See [Use diagnostic port to collect a trace from app startup](#use-diagnostic-port-to-collect-a-trace-from-app-startup) to learn how to use this option to collect a trace from app startup.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="578be-155">Toplanan izleme verileri için çıkış yolu.</span><span class="sxs-lookup"><span data-stu-id="578be-155">The output path for the collected trace data.</span></span> <span data-ttu-id="578be-156">Belirtilmemişse, varsayılan olarak olur `trace.nettrace` .</span><span class="sxs-lookup"><span data-stu-id="578be-156">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="578be-157">İzlemeyi toplanacak işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="578be-157">The process ID to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="578be-158">Yaygın izleme senaryolarına izin veren önceden tanımlanmış adlandırılmış bir dizi sağlayıcı yapılandırması succinctly.</span><span class="sxs-lookup"><span data-stu-id="578be-158">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span> <span data-ttu-id="578be-159">Aşağıdaki profiller mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="578be-159">The following profiles are available:</span></span>

 | <span data-ttu-id="578be-160">Profil</span><span class="sxs-lookup"><span data-stu-id="578be-160">Profile</span></span> | <span data-ttu-id="578be-161">Description</span><span class="sxs-lookup"><span data-stu-id="578be-161">Description</span></span> |
 |---------|-------------|
 |`cpu-sampling`|<span data-ttu-id="578be-162">CPU kullanımını ve genel .NET çalışma zamanı bilgilerini izlemek için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="578be-162">Useful for tracking CPU usage and general .NET runtime information.</span></span> <span data-ttu-id="578be-163">Profil veya sağlayıcı belirtilmemişse bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="578be-163">This is the default option if no profile or providers are specified.</span></span>|
 |`gc-verbose`|<span data-ttu-id="578be-164">GC koleksiyonlarını izler ve nesne ayırmalarını örnekler.</span><span class="sxs-lookup"><span data-stu-id="578be-164">Tracks GC collections and samples object allocations.</span></span>|
 |`gc-collect`|<span data-ttu-id="578be-165">GC koleksiyonlarını yalnızca çok düşük ek yüklerle izler.</span><span class="sxs-lookup"><span data-stu-id="578be-165">Tracks GC collections only at very low overhead.</span></span>|

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="578be-166">Etkinleştirilecek sağlayıcıların virgülle ayrılmış listesi `EventPipe` .</span><span class="sxs-lookup"><span data-stu-id="578be-166">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="578be-167">Bu sağlayıcılar tarafından kapsanan tüm sağlayıcıları tamamlar `--profile <profile-name>` .</span><span class="sxs-lookup"><span data-stu-id="578be-167">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="578be-168">Belirli bir sağlayıcı için herhangi bir tutarsızlık varsa, bu yapılandırma profilden örtük yapılandırmadan önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="578be-168">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="578be-169">Bu sağlayıcı listesi şu biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="578be-169">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="578be-170">`Provider` Şu biçimdedir: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .</span><span class="sxs-lookup"><span data-stu-id="578be-170">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="578be-171">`KeyValueArgs` Şu biçimdedir: `[key1=value1][;key2=value2]` .</span><span class="sxs-lookup"><span data-stu-id="578be-171">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

  <span data-ttu-id="578be-172">.NET 'teki iyi bilinen sağlayıcılar hakkında daha fazla bilgi edinmek için [iyi bilinen olay sağlayıcılarına](./well-known-event-providers.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="578be-172">To learn more about some of the well-known providers in .NET, refer to [Well-known Event Providers](./well-known-event-providers.md).</span></span>

- <span data-ttu-id="578be-173">**`-- <command>` (yalnızca .NET 5,0 çalıştıran hedef uygulamalar için)**</span><span class="sxs-lookup"><span data-stu-id="578be-173">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="578be-174">Koleksiyon yapılandırma parametrelerinden sonra, Kullanıcı, `--` en az bir 5,0 çalışma zamanına sahip bir .NET uygulamasını başlatmak için ardından bir komut ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="578be-174">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="578be-175">Bu, işlemin başında gerçekleşen, başlangıç performansı sorunu veya derleme yükleyicisi ve bağlayıcı hataları gibi sorunları tanılarken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="578be-175">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="578be-176">Bu seçeneğin kullanılması, araca geri iletişim kuran ilk .NET 5,0 işlemini izler, bu da komutunuz birden çok .NET uygulaması başlattığında yalnızca ilk uygulamayı toplayacaktır.</span><span class="sxs-lookup"><span data-stu-id="578be-176">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="578be-177">Bu nedenle, bu seçeneği kendi içinde bulunan uygulamalarda veya seçeneğini kullanarak kullanmanız önerilir `dotnet exec <app.dll>` .</span><span class="sxs-lookup"><span data-stu-id="578be-177">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

> [!NOTE]
> <span data-ttu-id="578be-178">İzlemenin durdurulması, büyük uygulamalar için uzun zaman alabilir (en fazla dakika).</span><span class="sxs-lookup"><span data-stu-id="578be-178">Stopping the trace may take a long time (up to minutes) for large applications.</span></span> <span data-ttu-id="578be-179">Çalışma zamanının, izlemede yakalanan tüm yönetilen kodlar için tür önbelleğinin üzerine gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="578be-179">The runtime needs to send over the type cache for all managed code that was captured in the trace.</span></span>

> [!NOTE]
> <span data-ttu-id="578be-180">Linux ve macOS 'ta, bu komut hedef uygulamayı bekler ve `dotnet-trace` aynı `TMPDIR` ortam değişkenini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="578be-180">On Linux and macOS, this command expects the target application and `dotnet-trace` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="578be-181">Aksi takdirde, komut zaman aşımına uğrar.</span><span class="sxs-lookup"><span data-stu-id="578be-181">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="578be-182">Kullanarak bir izleme toplamak için `dotnet-trace` , hedef işlem ya da kök olarak çalışan kullanıcı ile aynı kullanıcı olarak çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="578be-182">To collect a trace using `dotnet-trace`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="578be-183">Aksi halde araç, hedef işlemle bağlantı kurmayacak.</span><span class="sxs-lookup"><span data-stu-id="578be-183">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

> [!NOTE]
> <span data-ttu-id="578be-184">Aşağıdakine benzer bir hata iletisi görürseniz `[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.` , `dotnet-trace` hedef işleme karşı eşleşmeyen bit genişliğine sahip olan kullanmaya çalışıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="578be-184">If you see an error message similar to the following one: `[ERROR] System.ComponentModel.Win32Exception (299): A 32 bit processes cannot access modules of a 64 bit process.`, you are trying to use `dotnet-trace` that has mismatched bitness against the target process.</span></span> <span data-ttu-id="578be-185">[Yükleme](#install) bağlantısında aracın doğru bit durumunu indirdiğinizden emin olun.</span><span class="sxs-lookup"><span data-stu-id="578be-185">Make sure to download the correct bitness of the tool in the [install](#install) link.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="578be-186">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="578be-186">dotnet-trace convert</span></span>

<span data-ttu-id="578be-187">`nettrace`Diğer izleme çözümleme araçlarıyla birlikte kullanmak üzere izlemeleri alternatif biçimlere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="578be-187">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="578be-188">Özeti</span><span class="sxs-lookup"><span data-stu-id="578be-188">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="578be-189">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="578be-189">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="578be-190">Dönüştürülecek giriş izleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="578be-190">Input trace file to be converted.</span></span> <span data-ttu-id="578be-191">*Trace. NetTrace* için varsayılanlar.</span><span class="sxs-lookup"><span data-stu-id="578be-191">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="578be-192">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="578be-192">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="578be-193">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="578be-193">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="578be-194">Çıkış dosya adı.</span><span class="sxs-lookup"><span data-stu-id="578be-194">Output filename.</span></span> <span data-ttu-id="578be-195">Hedef biçimin uzantısı eklenecek.</span><span class="sxs-lookup"><span data-stu-id="578be-195">Extension of target format will be added.</span></span>

> [!NOTE]
> <span data-ttu-id="578be-196">`nettrace`Dosyaları `chromium` veya dosyaları dönüştürme `speedscope` işlemi geri alınamaz.</span><span class="sxs-lookup"><span data-stu-id="578be-196">Converting `nettrace` files to `chromium` or `speedscope` files is irreversible.</span></span> <span data-ttu-id="578be-197">`speedscope` dosyalar `chromium` , dosyaları yeniden oluşturmak için gereken tüm bilgileri içermez `nettrace` .</span><span class="sxs-lookup"><span data-stu-id="578be-197">`speedscope` and `chromium` files don't have all the information necessary to reconstruct `nettrace` files.</span></span> <span data-ttu-id="578be-198">Ancak, `convert` komut özgün `nettrace` dosyayı korur, bu nedenle daha sonra açmayı planlıyorsanız bu dosyayı silmeyin.</span><span class="sxs-lookup"><span data-stu-id="578be-198">However, the `convert` command preserves the original `nettrace` file, so don't delete this file if you plan to open it in the future.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="578be-199">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="578be-199">dotnet-trace ps</span></span>

 <span data-ttu-id="578be-200">İzlemelerin toplanabilecek DotNet süreçlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="578be-200">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="578be-201">Özeti</span><span class="sxs-lookup"><span data-stu-id="578be-201">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="578be-202">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="578be-202">dotnet-trace list-profiles</span></span>

<span data-ttu-id="578be-203">Her profilde hangi sağlayıcıların ve filtrelerin olduğuna ilişkin bir açıklama ile önceden oluşturulmuş izleme profillerini listeler.</span><span class="sxs-lookup"><span data-stu-id="578be-203">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="578be-204">Özeti</span><span class="sxs-lookup"><span data-stu-id="578be-204">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="578be-205">DotNet-Trace ile izleme toplama</span><span class="sxs-lookup"><span data-stu-id="578be-205">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="578be-206">Kullanarak izlemeleri toplamak için `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="578be-206">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="578be-207">İzlemeleri toplanacak .NET Core uygulamasının işlem tanımlayıcısını (PID) alın.</span><span class="sxs-lookup"><span data-stu-id="578be-207">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="578be-208">Windows üzerinde, örneğin, Görev Yöneticisi 'ni veya `tasklist` komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="578be-208">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="578be-209">Linux 'ta, örneğin, `ps` komutu.</span><span class="sxs-lookup"><span data-stu-id="578be-209">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="578be-210">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="578be-210">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="578be-211">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="578be-211">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="578be-212">Yukarıdaki komut aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="578be-212">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="578be-213">Anahtara basarak toplamayı durdurun `<Enter>` .</span><span class="sxs-lookup"><span data-stu-id="578be-213">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="578be-214">`dotnet-trace` olayları *izleme. NetTrace* dosyasına kaydetme işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="578be-214">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="578be-215">Bir alt uygulama başlatın ve DotNet-Trace kullanarak başlangıçtan bir izleme toplayın</span><span class="sxs-lookup"><span data-stu-id="578be-215">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

> [!IMPORTANT]
> <span data-ttu-id="578be-216">Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="578be-216">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="578be-217">Bazen bir işlemin başlangıcında bir izleme toplamak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="578be-217">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="578be-218">.NET 5,0 veya üzeri sürümlerini çalıştıran uygulamalar için bu, DotNet-Trace kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="578be-218">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="578be-219">Bu, `hello.exe` `arg1` ve `arg2` komut satırı bağımsız değişkenleriyle başlatılır ve çalışma zamanı başlangıcında bir izleme toplar:</span><span class="sxs-lookup"><span data-stu-id="578be-219">This will launch `hello.exe` with `arg1` and `arg2` as its command-line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="578be-220">Yukarıdaki komut aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="578be-220">The preceding command generates output similar to the following:</span></span>

```console
No profile or providers specified, defaulting to trace profile 'cpu-sampling'

Provider Name                           Keywords            Level               Enabled By
Microsoft-DotNETCore-SampleProfiler     0x0000F00000000000  Informational(4)    --profile
Microsoft-Windows-DotNETRuntime         0x00000014C14FCCBD  Informational(4)    --profile

Process        : E:\temp\gcperfsim\bin\Debug\net5.0\gcperfsim.exe
Output File    : E:\temp\gcperfsim\trace.nettrace


[00:00:00:05]   Recording trace 122.244  (KB)
Press <Enter> or <Ctrl+C> to exit...
```

<span data-ttu-id="578be-221">Veya tuşuna basarak izlemenin toplanmasını durdurabilirsiniz `<Enter>` `<Ctrl + C>` .</span><span class="sxs-lookup"><span data-stu-id="578be-221">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="578be-222">Bunun için de çıkış yapılır `hello.exe` .</span><span class="sxs-lookup"><span data-stu-id="578be-222">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="578be-223">`hello.exe`DotNet-Trace aracılığıyla başlatmak, giriş/çıkışının yeniden yönlendirilmesini sağlar ve stdin/stdout ile etkileşime giremeyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="578be-223">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="578be-224">CTRL + C veya SIGTERM aracılığıyla araçtan çıkmak, hem aracı hem de alt işlemi güvenle sonlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="578be-224">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="578be-225">Alt işlem, araçtan önce çıktığında, araç da sonlandırılır ve izlemenin güvenle görüntülenebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="578be-225">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a><span data-ttu-id="578be-226">Uygulama başlangıcında bir izleme toplamak için tanılama bağlantı noktasını kullan</span><span class="sxs-lookup"><span data-stu-id="578be-226">Use diagnostic port to collect a trace from app startup</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="578be-227">Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="578be-227">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="578be-228">Tanılama bağlantı noktası, .NET 5 ' te eklenen ve uygulama başlangıcında izlemeye başlayabilmeniz için yeni bir çalışma zamanı özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="578be-228">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start tracing from app startup.</span></span> <span data-ttu-id="578be-229">Bunu kullanarak yapmak için `dotnet-trace` `dotnet-trace collect -- <command>` Yukarıdaki örneklerde açıklandığı gibi kullanabilirsiniz veya `--diagnostic-port` seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="578be-229">To do this using `dotnet-trace`, you can either use `dotnet-trace collect -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="578be-230">`dotnet-trace <collect|monitor> -- <command>`Uygulamayı bir alt işlem olarak başlatmak için kullanmak, bunu başlangıçtan hızlı bir şekilde izlemenin en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="578be-230">Using `dotnet-trace <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly trace it from its startup.</span></span>

<span data-ttu-id="578be-231">Ancak, izlenen uygulamanın ömrü boyunca daha ayrıntılı bir denetim elde etmek istediğinizde (örneğin, uygulamayı yalnızca ilk 10 dakika boyunca izleyin ve yürütülmeye devam edin) veya CLı kullanarak uygulamayla etkileşime ihtiyacınız varsa, kullanma `--diagnostic-port` seçeneği, hem izlenen hem de hedef uygulamayı denetlemenize olanak tanır `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="578be-231">However, when you want to gain a finer control over the lifetime of the app being traced (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-trace`.</span></span>

1. <span data-ttu-id="578be-232">Aşağıdaki komut `dotnet-trace` adlı bir tanılama yuvası oluşturur `myport.sock` ve bir bağlantı bekler.</span><span class="sxs-lookup"><span data-stu-id="578be-232">The command below makes `dotnet-trace` create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="578be-233">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="578be-233">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="578be-234">Ayrı bir konsolda, hedef uygulamayı `DOTNET_DiagnosticPorts` Çıkış içindeki değere ayarlanmış ortam değişkeni ile başlatın `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="578be-234">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-trace` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="578be-235">`dotnet-trace`İzlemeye başlamak için bu daha sonra etkinleştirmelisiniz `my-dotnet-app` :</span><span class="sxs-lookup"><span data-stu-id="578be-235">This should then enable `dotnet-trace` to start tracing `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="578be-236">`dotnet run`DotNet CLI, uygulamanız olmayan çok sayıda alt işlem oluşturduğundan ve uygulamanızın `dotnet-trace` çalışma zamanında askıya alınması için uygulamadan önce bağlanabildikleri için uygulamanızın ile başlatılması sorunlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="578be-236">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-trace` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="578be-237">Uygulamanın otomatik olarak kapsanan bir sürümünü kullanmanız veya `dotnet exec` uygulamayı başlatmak için kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="578be-237">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="578be-238">DotNet 'den yakalanan izlemeyi görüntüleyin-Trace</span><span class="sxs-lookup"><span data-stu-id="578be-238">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="578be-239">Windows 'da *. NetTrace* dosyaları analiz Için [PerfView](https://github.com/microsoft/perfview) üzerinde görüntülenebilir: diğer platformlarda toplanan izlemeler Için, izleme dosyası PerfView 'Da görüntülenmek üzere bir Windows makinesine taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="578be-239">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="578be-240">Linux 'ta izleme, ' nin çıkış biçimi değiştirilerek görüntülenebilir `dotnet-trace` `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="578be-240">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="578be-241">Çıkış dosyası biçimi, seçeneği kullanılarak değiştirilebilir, `-f|--format` `-f speedscope` `dotnet-trace` bir `speedscope` dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="578be-241">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="578be-242">`nettrace`(Varsayılan seçenek) ve arasında seçim yapabilirsiniz `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="578be-242">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="578be-243">`Speedscope` dosyalar ' de açılabilir <https://www.speedscope.app> .</span><span class="sxs-lookup"><span data-stu-id="578be-243">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="578be-244">.NET Core çalışma zamanı, biçimde izleme oluşturur `nettrace` .</span><span class="sxs-lookup"><span data-stu-id="578be-244">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="578be-245">İzlemeler, izleme tamamlandıktan sonra speedscope (belirtilmişse) olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="578be-245">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="578be-246">Bazı dönüştürmeler veri kaybına neden olabileceğinden, özgün `nettrace` Dosya Dönüştürülen dosyanın yanında korunur.</span><span class="sxs-lookup"><span data-stu-id="578be-246">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="578be-247">Zaman içinde sayaç değerlerini toplamak için DotNet-Trace kullanın</span><span class="sxs-lookup"><span data-stu-id="578be-247">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="578be-248">`dotnet-trace` erişebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="578be-248">`dotnet-trace` can:</span></span>

* <span data-ttu-id="578be-249">`EventCounter`Performans duyarlı ortamlarda temel sistem durumu izleme için kullanın.</span><span class="sxs-lookup"><span data-stu-id="578be-249">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="578be-250">Örneğin, üretimde.</span><span class="sxs-lookup"><span data-stu-id="578be-250">For example, in production.</span></span>
* <span data-ttu-id="578be-251">İzlemeleri toplayın, böylece gerçek zamanlı olarak görüntülenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="578be-251">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="578be-252">Örneğin, çalışma zamanı performans sayacı değerlerini toplamak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="578be-252">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="578be-253">Yukarıdaki komut, hafif sistem durumu izleme için çalışma zamanı sayaçlarına her saniye bir kez rapor vermesini söyler.</span><span class="sxs-lookup"><span data-stu-id="578be-253">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="578be-254">`EventCounterIntervalSec=1`Daha yüksek bir değerle değiştirme (örneğin, 60) sayaç verilerinde daha az ayrıntı düzeyi olan daha küçük bir izlemenin toplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="578be-254">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="578be-255">Aşağıdaki komut ek yükü ve izleme boyutunu önceki olandan daha fazla azaltır:</span><span class="sxs-lookup"><span data-stu-id="578be-255">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="578be-256">Yukarıdaki komut, çalışma zamanı olaylarını ve yönetilen yığın profil oluşturucuyu devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="578be-256">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="use-rsp-file-to-avoid-typing-long-commands"></a><span data-ttu-id="578be-257">Uzun komutların yazımasını önlemek için. rsp dosyasını kullanın</span><span class="sxs-lookup"><span data-stu-id="578be-257">Use .rsp file to avoid typing long commands</span></span>

<span data-ttu-id="578be-258">`dotnet-trace` `.rsp` Geçirilecek bağımsız değişkenleri içeren bir dosyayla başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="578be-258">You can launch `dotnet-trace` with an `.rsp` file that contains the arguments to pass.</span></span> <span data-ttu-id="578be-259">Bu, uzun bağımsız değişkenler bekleyen veya karakter şeritleri kullanan bir kabuk ortamını kullanırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="578be-259">This can be useful when enabling providers that expect lengthy arguments or when using a shell environment that strips characters.</span></span>

<span data-ttu-id="578be-260">Örneğin, aşağıdaki sağlayıcı, izlemek istediğiniz her seferinde yazmamasız bir şekilde olabilir:</span><span class="sxs-lookup"><span data-stu-id="578be-260">For example, the following provider can be cumbersome to type out each time you want to trace:</span></span>

```cmd
dotnet-trace collect --providers Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="578be-261">Ayrıca, önceki örnek `"` bağımsız değişkenin bir parçası olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="578be-261">In addition, the previous example contains `"` as part of the argument.</span></span> <span data-ttu-id="578be-262">Teklifler her kabukta eşit olarak işlenmediğinden, farklı kabuklar kullanırken çeşitli sorunlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="578be-262">Because quotes are not handled equally by each shell, you may experience various issues when using different shells.</span></span> <span data-ttu-id="578be-263">Örneğin, içine girilecek komut `zsh` içindeki komutuna farklıdır `cmd` .</span><span class="sxs-lookup"><span data-stu-id="578be-263">For example, the command to enter in `zsh` is different to the command in `cmd`.</span></span>

<span data-ttu-id="578be-264">Bu her seferinde yazmak yerine, aşağıdaki metni adlı bir dosyaya kaydedebilirsiniz `myprofile.rsp` .</span><span class="sxs-lookup"><span data-stu-id="578be-264">Instead of typing this each time, you can save the following text into a file called `myprofile.rsp`.</span></span>

```txt
--providers
Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="578be-265">Kaydettikten sonra `myprofile.rsp` , `dotnet-trace` aşağıdaki komutu kullanarak bu yapılandırmayla başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="578be-265">Once you've saved `myprofile.rsp`, you can launch `dotnet-trace` with this configuration using the following command:</span></span>

```bash
dotnet-trace @myprofile.rsp
```

## <a name="see-also"></a><span data-ttu-id="578be-266">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="578be-266">See also</span></span>

- [<span data-ttu-id="578be-267">.NET 'ten tanınmış olay sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="578be-267">Well-known event providers from .NET</span></span>](well-known-event-providers.md)
