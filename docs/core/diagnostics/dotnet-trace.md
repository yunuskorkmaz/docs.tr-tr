---
title: DotNet-izleme aracı-.NET Core
description: DotNet-Trace komut satırı aracını yükleme ve kullanma.
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737652"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="9d273-103">DotNet-izleme performansı Analizi yardımcı programı</span><span class="sxs-lookup"><span data-stu-id="9d273-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="9d273-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="9d273-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="9d273-105">DotNet 'yi Install-Trace</span><span class="sxs-lookup"><span data-stu-id="9d273-105">Install dotnet-trace</span></span>

<span data-ttu-id="9d273-106">[DotNet aracı install](../tools/dotnet-tool-install.md) komutuyla `dotnet-trace` [NuGet paketini](https://www.nuget.org/packages/dotnet-trace) yükler:</span><span class="sxs-lookup"><span data-stu-id="9d273-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="9d273-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="9d273-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="9d273-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9d273-108">Description</span></span>

<span data-ttu-id="9d273-109">`dotnet-trace` aracı:</span><span class="sxs-lookup"><span data-stu-id="9d273-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="9d273-110">, Platformlar arası bir .NET Core aracıdır.</span><span class="sxs-lookup"><span data-stu-id="9d273-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="9d273-111">Yerel bir profil oluşturucu olmadan çalışan bir işlemin .NET Core izlemelerinin toplanmasını mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="9d273-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="9d273-112">, .NET Core çalışma zamanının platformlar arası `EventPipe` teknolojisi etrafında oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="9d273-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="9d273-113">Windows, Linux veya macOS 'ta aynı deneyimi sunar.</span><span class="sxs-lookup"><span data-stu-id="9d273-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="9d273-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9d273-114">Options</span></span>

- **`--version`**

  <span data-ttu-id="9d273-115">DotNet-Counters yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="9d273-115">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9d273-116">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="9d273-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="9d273-117">Komutlar</span><span class="sxs-lookup"><span data-stu-id="9d273-117">Commands</span></span>

| <span data-ttu-id="9d273-118">Komut</span><span class="sxs-lookup"><span data-stu-id="9d273-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="9d273-119">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="9d273-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="9d273-120">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="9d273-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="9d273-121">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="9d273-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="9d273-122">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="9d273-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="9d273-123">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="9d273-123">dotnet-trace collect</span></span>

<span data-ttu-id="9d273-124">Çalışan bir işlemden bir tanılama izlemesi toplar.</span><span class="sxs-lookup"><span data-stu-id="9d273-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9d273-125">Özeti</span><span class="sxs-lookup"><span data-stu-id="9d273-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="9d273-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9d273-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="9d273-127">İzlemeyi toplama işlemi.</span><span class="sxs-lookup"><span data-stu-id="9d273-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="9d273-128">Bellek içi dairesel arabelleğin boyutunu megabayt cinsinden ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9d273-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="9d273-129">Varsayılan 256 MB.</span><span class="sxs-lookup"><span data-stu-id="9d273-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="9d273-130">Toplanan izleme verileri için çıkış yolu.</span><span class="sxs-lookup"><span data-stu-id="9d273-130">The output path for the collected trace data.</span></span> <span data-ttu-id="9d273-131">Belirtilmemişse, varsayılan olarak `trace.nettrace`olur.</span><span class="sxs-lookup"><span data-stu-id="9d273-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="9d273-132">Etkinleştirilecek `EventPipe` sağlayıcılarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="9d273-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="9d273-133">Bu sağlayıcılar `--profile <profile-name>`tarafından kapsanan tüm sağlayıcıları tamamlar.</span><span class="sxs-lookup"><span data-stu-id="9d273-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="9d273-134">Belirli bir sağlayıcı için herhangi bir tutarsızlık varsa, bu yapılandırma profilden örtük yapılandırmadan önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="9d273-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="9d273-135">Bu sağlayıcı listesi şu biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="9d273-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="9d273-136">`Provider` şu biçimdedir: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="9d273-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="9d273-137">`KeyValueArgs` şu biçimdedir: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="9d273-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="9d273-138">Yaygın izleme senaryolarına izin veren önceden tanımlanmış adlandırılmış bir dizi sağlayıcı yapılandırması succinctly.</span><span class="sxs-lookup"><span data-stu-id="9d273-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="9d273-139">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9d273-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="9d273-140">Varsayılan, `NetTrace` değeridir.</span><span class="sxs-lookup"><span data-stu-id="9d273-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="9d273-141">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="9d273-141">dotnet-trace convert</span></span>

<span data-ttu-id="9d273-142">Alternatif izleme çözümleme araçlarıyla kullanılmak üzere `nettrace` izlemelerini alternatif biçimlere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="9d273-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9d273-143">Özeti</span><span class="sxs-lookup"><span data-stu-id="9d273-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="9d273-144">Arguments</span><span class="sxs-lookup"><span data-stu-id="9d273-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="9d273-145">Dönüştürülecek giriş izleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="9d273-145">Input trace file to be converted.</span></span> <span data-ttu-id="9d273-146">*Trace. NetTrace*için varsayılanlar.</span><span class="sxs-lookup"><span data-stu-id="9d273-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="9d273-147">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="9d273-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="9d273-148">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9d273-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="9d273-149">Çıkış dosya adı.</span><span class="sxs-lookup"><span data-stu-id="9d273-149">Output filename.</span></span> <span data-ttu-id="9d273-150">Hedef biçimin uzantısı eklenecek.</span><span class="sxs-lookup"><span data-stu-id="9d273-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="9d273-151">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="9d273-151">dotnet-trace ps</span></span>

<span data-ttu-id="9d273-152">İliştirilebilecek DotNet süreçlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="9d273-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9d273-153">Özeti</span><span class="sxs-lookup"><span data-stu-id="9d273-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="9d273-154">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="9d273-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="9d273-155">Her profilde hangi sağlayıcıların ve filtrelerin olduğuna ilişkin bir açıklama ile önceden oluşturulmuş izleme profillerini listeler.</span><span class="sxs-lookup"><span data-stu-id="9d273-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="9d273-156">Özeti</span><span class="sxs-lookup"><span data-stu-id="9d273-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="9d273-157">DotNet-Trace ile izleme toplama</span><span class="sxs-lookup"><span data-stu-id="9d273-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="9d273-158">`dotnet-trace`kullanarak izlemeleri toplamak için:</span><span class="sxs-lookup"><span data-stu-id="9d273-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="9d273-159">İzlemeleri toplanacak .NET Core uygulamasının işlem tanımlayıcısını (PID) alın.</span><span class="sxs-lookup"><span data-stu-id="9d273-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="9d273-160">Windows 'da, örneğin, Görev Yöneticisi 'ni veya `tasklist` komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d273-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="9d273-161">Linux 'ta, örneğin, `ps` komutu.</span><span class="sxs-lookup"><span data-stu-id="9d273-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="9d273-162">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="9d273-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="9d273-163">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="9d273-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="9d273-164">Yukarıdaki komut aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="9d273-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="9d273-165">`<Enter>` tuşuna basarak toplamayı durdurun.</span><span class="sxs-lookup"><span data-stu-id="9d273-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="9d273-166">`dotnet-trace`, *izleme. NetTrace* dosyasına günlük olaylarını tamamlayacak.</span><span class="sxs-lookup"><span data-stu-id="9d273-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="9d273-167">DotNet 'den yakalanan izlemeyi görüntüleyin-Trace</span><span class="sxs-lookup"><span data-stu-id="9d273-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="9d273-168">Windows 'da *. NetTrace* dosyaları analiz Için [PerfView](https://github.com/microsoft/perfview) üzerinde görüntülenebilir: diğer platformlarda toplanan izlemeler Için, izleme dosyası PerfView 'Da görüntülenmek üzere bir Windows makinesine taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="9d273-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="9d273-169">Linux 'ta, `dotnet-trace` çıktı biçimi `speedscope`olarak değiştirilerek izleme görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="9d273-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="9d273-170">Çıkış dosyası biçimi `-f|--format` seçeneği kullanılarak değiştirilebilir-`-f speedscope`, `speedscope` bir dosya `dotnet-trace` oluşturacak.</span><span class="sxs-lookup"><span data-stu-id="9d273-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="9d273-171">`nettrace` (varsayılan seçenek) ve `speedscope`arasında seçim yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9d273-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="9d273-172">`Speedscope` dosyalar <https://www.speedscope.app>açılabilirler.</span><span class="sxs-lookup"><span data-stu-id="9d273-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="9d273-173">.NET Core çalışma zamanı, `nettrace` biçiminde izleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d273-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="9d273-174">İzlemeler, izleme tamamlandıktan sonra speedscope (belirtilmişse) olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="9d273-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="9d273-175">Bazı dönüştürmeler veri kaybına neden olabileceğinden, özgün `nettrace` dosyası Dönüştürülen dosyanın yanında korunur.</span><span class="sxs-lookup"><span data-stu-id="9d273-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="9d273-176">Zaman içinde sayaç değerlerini toplamak için DotNet-Trace kullanın</span><span class="sxs-lookup"><span data-stu-id="9d273-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="9d273-177">`dotnet-trace` şunları yapabilir:</span><span class="sxs-lookup"><span data-stu-id="9d273-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="9d273-178">Performans duyarlı ortamlarda temel sistem durumu izleme için `EventCounter` kullanın.</span><span class="sxs-lookup"><span data-stu-id="9d273-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="9d273-179">Örneğin, üretimde.</span><span class="sxs-lookup"><span data-stu-id="9d273-179">For example, in production.</span></span>
* <span data-ttu-id="9d273-180">İzlemeleri toplayın, böylece gerçek zamanlı olarak görüntülenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="9d273-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="9d273-181">Örneğin, çalışma zamanı performans sayacı değerlerini toplamak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="9d273-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="9d273-182">Yukarıdaki komut, hafif sistem durumu izleme için çalışma zamanı sayaçlarına her saniye bir kez rapor vermesini söyler.</span><span class="sxs-lookup"><span data-stu-id="9d273-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="9d273-183">`EventCounterIntervalSec=1` daha yüksek bir değerle değiştirmek (örneğin, 60) sayaç verilerinde daha az ayrıntı düzeyi olan daha küçük bir izlemenin toplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d273-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="9d273-184">Aşağıdaki komut ek yükü ve izleme boyutunu önceki olandan daha fazla azaltır:</span><span class="sxs-lookup"><span data-stu-id="9d273-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="9d273-185">Yukarıdaki komut, çalışma zamanı olaylarını ve yönetilen yığın profil oluşturucuyu devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="9d273-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="9d273-186">.NET sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="9d273-186">.NET Providers</span></span>

<span data-ttu-id="9d273-187">.NET Core çalışma zamanı, aşağıdaki .NET sağlayıcılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="9d273-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="9d273-188">.NET Core hem `Event Tracing for Windows (ETW)` hem de `EventPipe` izlemelerini etkinleştirmek için aynı anahtar kelimeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="9d273-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="9d273-189">Sağlayıcı adı</span><span class="sxs-lookup"><span data-stu-id="9d273-189">Provider name</span></span>                            | <span data-ttu-id="9d273-190">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="9d273-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="9d273-191">Çalışma zamanı sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="9d273-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="9d273-192">CLR çalışma zamanı anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9d273-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="9d273-193">Özet sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="9d273-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="9d273-194">CLR Özeti anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="9d273-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="9d273-195">Örnek profil oluşturucuyu etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9d273-195">Enables the sample profiler.</span></span> |
