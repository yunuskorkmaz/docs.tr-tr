---
title: dotnet izleme aracı - .NET Core
description: Dotnet izleme komut satırı aracını yüklemek ve kullanmak.
ms.date: 11/21/2019
ms.openlocfilehash: b19b159636fbf57fa2d461b398fcf9234aab491c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737652"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="40079-103">dotnet-trace performans analizi programı</span><span class="sxs-lookup"><span data-stu-id="40079-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="40079-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="40079-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="40079-105">Dotnet izleme yükleme</span><span class="sxs-lookup"><span data-stu-id="40079-105">Install dotnet-trace</span></span>

<span data-ttu-id="40079-106">`dotnet-trace` [Dotnet araç yükleme](../tools/dotnet-tool-install.md) komutu ile [NuGet paketini](https://www.nuget.org/packages/dotnet-trace) yükleyin:</span><span class="sxs-lookup"><span data-stu-id="40079-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="40079-107">Özet</span><span class="sxs-lookup"><span data-stu-id="40079-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="40079-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="40079-108">Description</span></span>

<span data-ttu-id="40079-109">Araç: `dotnet-trace`</span><span class="sxs-lookup"><span data-stu-id="40079-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="40079-110">Bir çapraz platform .NET Core aracıdır.</span><span class="sxs-lookup"><span data-stu-id="40079-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="40079-111">Yerel profil oluşturucu olmadan çalışan bir işlemin .NET Core izlerinin toplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="40079-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="40079-112">.NET Core çalışma `EventPipe` zamanının çapraz platform teknolojisi etrafında oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="40079-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="40079-113">Windows, Linux veya macOS'ta da aynı deneyimi sunar.</span><span class="sxs-lookup"><span data-stu-id="40079-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="40079-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="40079-114">Options</span></span>

- **`--version`**

  <span data-ttu-id="40079-115">Dotnet sayaçları yardımcı programı sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="40079-115">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="40079-116">Komut satırı yardımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="40079-116">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="40079-117">Komutlar</span><span class="sxs-lookup"><span data-stu-id="40079-117">Commands</span></span>

| <span data-ttu-id="40079-118">Komut</span><span class="sxs-lookup"><span data-stu-id="40079-118">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="40079-119">dotnet-iz toplama</span><span class="sxs-lookup"><span data-stu-id="40079-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="40079-120">dotnet izleme dönüştürme</span><span class="sxs-lookup"><span data-stu-id="40079-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="40079-121">dotnet izleme ps</span><span class="sxs-lookup"><span data-stu-id="40079-121">dotnet-trace ps</span></span>](#dotnet-trace-ps) |
| [<span data-ttu-id="40079-122">dotnet izleme listesi-profilleri</span><span class="sxs-lookup"><span data-stu-id="40079-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="40079-123">dotnet-iz toplama</span><span class="sxs-lookup"><span data-stu-id="40079-123">dotnet-trace collect</span></span>

<span data-ttu-id="40079-124">Çalışan bir işlemden tanılama izi toplar.</span><span class="sxs-lookup"><span data-stu-id="40079-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="40079-125">Özet</span><span class="sxs-lookup"><span data-stu-id="40079-125">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="40079-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="40079-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="40079-127">İzi toplama işlemi.</span><span class="sxs-lookup"><span data-stu-id="40079-127">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="40079-128">Megabaytlar halinde bellek içi dairesel arabellek boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="40079-128">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="40079-129">Varsayılan 256 MB.</span><span class="sxs-lookup"><span data-stu-id="40079-129">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="40079-130">Toplanan izleme verilerinin çıktı yolu.</span><span class="sxs-lookup"><span data-stu-id="40079-130">The output path for the collected trace data.</span></span> <span data-ttu-id="40079-131">Belirtilmemişse `trace.nettrace`varsayılan olarak .</span><span class="sxs-lookup"><span data-stu-id="40079-131">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="40079-132">Etkinleştirilecek virgülle `EventPipe` ayrılmış sağlayıcılistesi.</span><span class="sxs-lookup"><span data-stu-id="40079-132">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="40079-133">Bu sağlayıcılar tarafından `--profile <profile-name>`ima herhangi bir sağlayıcılar tamam.</span><span class="sxs-lookup"><span data-stu-id="40079-133">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="40079-134">Belirli bir sağlayıcı için herhangi bir tutarsızlık varsa, bu yapılandırma profildeki örtük yapılandırmadan önce gelir.</span><span class="sxs-lookup"><span data-stu-id="40079-134">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="40079-135">Bu sağlayıcı listesi şu şekildedir:</span><span class="sxs-lookup"><span data-stu-id="40079-135">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="40079-136">`Provider`şeklindedir: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="40079-136">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="40079-137">`KeyValueArgs`şeklindedir: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="40079-137">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="40079-138">Ortak izleme senaryolarının kısa bir şekilde belirtilmesine olanak tanıyan önceden tanımlanmış sağlayıcı yapılandırmaları kümesi.</span><span class="sxs-lookup"><span data-stu-id="40079-138">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format {NetTrace|Speedscope}`**

  <span data-ttu-id="40079-139">İzleme dosyası dönüştürmeiçin çıktı biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="40079-139">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="40079-140">Varsayılan değer: `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="40079-140">The default is `NetTrace`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="40079-141">dotnet izleme dönüştürme</span><span class="sxs-lookup"><span data-stu-id="40079-141">dotnet-trace convert</span></span>

<span data-ttu-id="40079-142">`nettrace` İzlemeleri alternatif izleme çözümleme araçlarıyla kullanılmak üzere alternatif biçimlere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="40079-142">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="40079-143">Özet</span><span class="sxs-lookup"><span data-stu-id="40079-143">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="40079-144">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="40079-144">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="40079-145">Dönüştürülecek giriş izleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="40079-145">Input trace file to be converted.</span></span> <span data-ttu-id="40079-146">*Trace.nettrace*için varsayılan .</span><span class="sxs-lookup"><span data-stu-id="40079-146">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="40079-147">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="40079-147">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="40079-148">İzleme dosyası dönüştürmeiçin çıktı biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="40079-148">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="40079-149">Çıktı dosya adı.</span><span class="sxs-lookup"><span data-stu-id="40079-149">Output filename.</span></span> <span data-ttu-id="40079-150">Hedef biçiminin uzantısı eklenecektir.</span><span class="sxs-lookup"><span data-stu-id="40079-150">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="40079-151">dotnet izleme ps</span><span class="sxs-lookup"><span data-stu-id="40079-151">dotnet-trace ps</span></span>

<span data-ttu-id="40079-152">Ekilen dotnet işlemlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="40079-152">Lists dotnet processes that can be attached to.</span></span>

### <a name="synopsis"></a><span data-ttu-id="40079-153">Özet</span><span class="sxs-lookup"><span data-stu-id="40079-153">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="40079-154">dotnet izleme listesi-profilleri</span><span class="sxs-lookup"><span data-stu-id="40079-154">dotnet-trace list-profiles</span></span>

<span data-ttu-id="40079-155">Her profilde hangi sağlayıcıların ve filtrelerin bulunduğuna dikkat içeren önceden oluşturulmuş izleme profillerini listeler.</span><span class="sxs-lookup"><span data-stu-id="40079-155">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="40079-156">Özet</span><span class="sxs-lookup"><span data-stu-id="40079-156">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="40079-157">Dotnet-trace ile bir izleme toplamak</span><span class="sxs-lookup"><span data-stu-id="40079-157">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="40079-158">Kullanarak `dotnet-trace`izleri toplamak için:</span><span class="sxs-lookup"><span data-stu-id="40079-158">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="40079-159">İzleri toplamak için .NET Core uygulamasının işlem tanımlayıcısını (PID) alın.</span><span class="sxs-lookup"><span data-stu-id="40079-159">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="40079-160">Windows'da, örneğin Görev Yöneticisi'ni veya komutu `tasklist` kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40079-160">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="40079-161">Linux'ta, örneğin, `ps` komut.</span><span class="sxs-lookup"><span data-stu-id="40079-161">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="40079-162">dotnet izleme ps</span><span class="sxs-lookup"><span data-stu-id="40079-162">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="40079-163">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="40079-163">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="40079-164">Önceki komut aşağıdakine benzer çıktı üretir:</span><span class="sxs-lookup"><span data-stu-id="40079-164">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="40079-165">Tuşa basarak `<Enter>` koleksiyonu durdurun.</span><span class="sxs-lookup"><span data-stu-id="40079-165">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="40079-166">`dotnet-trace`*trace.nettrace* dosyasına günlüğe kaydetme olayını tamamlayacaktır.</span><span class="sxs-lookup"><span data-stu-id="40079-166">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="40079-167">dotnet-trace'den yakalanan izi görüntüleme</span><span class="sxs-lookup"><span data-stu-id="40079-167">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="40079-168">*Windows'da,.nettrace* dosyaları analiz için [PerfView'da](https://github.com/microsoft/perfview) görüntülenebilir: Diğer platformlarda toplanan izlemeler için izleme dosyası PerfView'da görüntülenecek bir Windows makinesine taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="40079-168">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="40079-169">Linux'ta, izleme çıkış biçimini `dotnet-trace` değiştirerek `speedscope`görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="40079-169">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="40079-170">Çıktı dosyası biçimi `-f|--format` seçeneği kullanılarak değiştirilebilir `-f speedscope` - `dotnet-trace` bir `speedscope` dosya üretmek yapacaktır.</span><span class="sxs-lookup"><span data-stu-id="40079-170">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="40079-171">Aralarında `nettrace` (varsayılan seçenek) ve `speedscope`.</span><span class="sxs-lookup"><span data-stu-id="40079-171">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="40079-172">`Speedscope`dosyaları ' dan <https://www.speedscope.app>açılabilir.</span><span class="sxs-lookup"><span data-stu-id="40079-172">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="40079-173">.NET Core çalışma süresi `nettrace` biçiminde izlemeler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="40079-173">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="40079-174">İzleme tamamlandıktan sonra izlemeler hız stobuna (belirtilmişse) dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="40079-174">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="40079-175">Bazı dönüşümler veri kaybına neden olabileceğinden, özgün `nettrace` dosya dönüştürülen dosyanın yanında korunur.</span><span class="sxs-lookup"><span data-stu-id="40079-175">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="40079-176">Zaman içinde sayaç değerlerini toplamak için dotnet izleme</span><span class="sxs-lookup"><span data-stu-id="40079-176">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="40079-177">`dotnet-trace`-bilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="40079-177">`dotnet-trace` can:</span></span>

* <span data-ttu-id="40079-178">Performansa duyarlı ortamlarda temel sistem durumu izleme için kullanın. `EventCounter`</span><span class="sxs-lookup"><span data-stu-id="40079-178">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="40079-179">Örneğin, üretimde.</span><span class="sxs-lookup"><span data-stu-id="40079-179">For example, in production.</span></span>
* <span data-ttu-id="40079-180">Gerçek zamanlı olarak görüntülenmeleri gerekmesin diye izleri toplayın.</span><span class="sxs-lookup"><span data-stu-id="40079-180">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="40079-181">Örneğin, çalışma zamanı performans sayacı değerlerini toplamak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="40079-181">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="40079-182">Önceki komut, çalışma zamanı sayaçlarına hafif sistem durumu izleme için saniyede bir rapor vermelerini söyler.</span><span class="sxs-lookup"><span data-stu-id="40079-182">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="40079-183">Daha `EventCounterIntervalSec=1` yüksek bir değerle değiştirme (örneğin, 60) sayaç verilerinde daha az parçalılıkla daha küçük bir izlemenin toplanmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="40079-183">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="40079-184">Aşağıdaki komut, yükü ve izleme boyutunu bir öncekinden daha fazla azaltır:</span><span class="sxs-lookup"><span data-stu-id="40079-184">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="40079-185">Önceki komut çalışma zamanı olaylarını ve yönetilen yığın profiloluşturucuyu devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="40079-185">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="40079-186">.NET Sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="40079-186">.NET Providers</span></span>

<span data-ttu-id="40079-187">.NET Core çalışma süresi aşağıdaki .NET sağlayıcılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="40079-187">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="40079-188">.NET Core, hem hem `Event Tracing for Windows (ETW)` de `EventPipe` izleri etkinleştirmek için aynı anahtar kelimeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="40079-188">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="40079-189">Sağlayıcı adı</span><span class="sxs-lookup"><span data-stu-id="40079-189">Provider name</span></span>                            | <span data-ttu-id="40079-190">Bilgi</span><span class="sxs-lookup"><span data-stu-id="40079-190">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="40079-191">Çalışma Zamanı Sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="40079-191">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="40079-192">CLR Çalışma Zamanı Anahtar Kelimeleri</span><span class="sxs-lookup"><span data-stu-id="40079-192">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="40079-193">Rundown Sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="40079-193">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="40079-194">CLR Özeti Anahtar Kelimeler</span><span class="sxs-lookup"><span data-stu-id="40079-194">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="40079-195">Örnek profil oluşturucuyu etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="40079-195">Enables the sample profiler.</span></span> |
