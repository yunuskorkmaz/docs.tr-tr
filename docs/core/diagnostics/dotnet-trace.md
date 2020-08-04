---
title: DotNet-izleme aracı-.NET Core
description: DotNet-Trace komut satırı aracını yükleme ve kullanma.
ms.date: 11/21/2019
ms.openlocfilehash: 25178a0e59ce9edb69d15ee761c1b9e56aa5eb3a
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517314"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="5ebad-103">DotNet-izleme performansı Analizi yardımcı programı</span><span class="sxs-lookup"><span data-stu-id="5ebad-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="5ebad-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="5ebad-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="5ebad-105">DotNet 'yi Install-Trace</span><span class="sxs-lookup"><span data-stu-id="5ebad-105">Install dotnet-trace</span></span>

<span data-ttu-id="5ebad-106">`dotnet-trace` [DotNet aracı install](../tools/dotnet-tool-install.md) komutuyla [NuGet paketini](https://www.nuget.org/packages/dotnet-trace) yükler:</span><span class="sxs-lookup"><span data-stu-id="5ebad-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="5ebad-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="5ebad-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="5ebad-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ebad-108">Description</span></span>

<span data-ttu-id="5ebad-109">`dotnet-trace`Araç:</span><span class="sxs-lookup"><span data-stu-id="5ebad-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="5ebad-110">, Platformlar arası bir .NET Core aracıdır.</span><span class="sxs-lookup"><span data-stu-id="5ebad-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="5ebad-111">Yerel bir profil oluşturucu olmadan çalışan bir işlemin .NET Core izlemelerinin toplanmasını mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="5ebad-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="5ebad-112">, `EventPipe` .NET Core çalışma zamanının platformlar arası teknolojisi etrafında oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="5ebad-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="5ebad-113">Windows, Linux veya macOS 'ta aynı deneyimi sunar.</span><span class="sxs-lookup"><span data-stu-id="5ebad-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="5ebad-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5ebad-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="5ebad-115">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ebad-115">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="5ebad-116">DotNet-Trace yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="5ebad-116">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="5ebad-117">Komutlar</span><span class="sxs-lookup"><span data-stu-id="5ebad-117">Commands</span></span>

| <span data-ttu-id="5ebad-118">Komut</span><span class="sxs-lookup"><span data-stu-id="5ebad-118">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="5ebad-119">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="5ebad-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="5ebad-120">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="5ebad-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="5ebad-121">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="5ebad-121">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="5ebad-122">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="5ebad-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="5ebad-123">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="5ebad-123">dotnet-trace collect</span></span>

<span data-ttu-id="5ebad-124">Çalışan bir işlemden bir tanılama izlemesi toplar.</span><span class="sxs-lookup"><span data-stu-id="5ebad-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="5ebad-125">Özeti</span><span class="sxs-lookup"><span data-stu-id="5ebad-125">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
```

### <a name="options"></a><span data-ttu-id="5ebad-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5ebad-126">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="5ebad-127">Bellek içi dairesel arabelleğin boyutunu megabayt cinsinden ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5ebad-127">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="5ebad-128">Varsayılan 256 MB.</span><span class="sxs-lookup"><span data-stu-id="5ebad-128">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="5ebad-129">Oluşturulacak CLR olaylarının ayrıntı düzeyi.</span><span class="sxs-lookup"><span data-stu-id="5ebad-129">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="5ebad-130">Görüntülenecek CLR çalışma zamanı olaylarının listesi.</span><span class="sxs-lookup"><span data-stu-id="5ebad-130">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="5ebad-131">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5ebad-131">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="5ebad-132">Varsayılan değer: `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="5ebad-132">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="5ebad-133">İzlemenin toplanacağı işlemin adı.</span><span class="sxs-lookup"><span data-stu-id="5ebad-133">The name of the process to collect the trace from.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="5ebad-134">Toplanan izleme verileri için çıkış yolu.</span><span class="sxs-lookup"><span data-stu-id="5ebad-134">The output path for the collected trace data.</span></span> <span data-ttu-id="5ebad-135">Belirtilmemişse, varsayılan olarak olur `trace.nettrace` .</span><span class="sxs-lookup"><span data-stu-id="5ebad-135">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="5ebad-136">İzlemeyi toplanacak işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="5ebad-136">The process id to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="5ebad-137">Yaygın izleme senaryolarına izin veren önceden tanımlanmış adlandırılmış bir dizi sağlayıcı yapılandırması succinctly.</span><span class="sxs-lookup"><span data-stu-id="5ebad-137">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="5ebad-138">Etkinleştirilecek sağlayıcıların virgülle ayrılmış listesi `EventPipe` .</span><span class="sxs-lookup"><span data-stu-id="5ebad-138">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="5ebad-139">Bu sağlayıcılar tarafından kapsanan tüm sağlayıcıları tamamlar `--profile <profile-name>` .</span><span class="sxs-lookup"><span data-stu-id="5ebad-139">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="5ebad-140">Belirli bir sağlayıcı için herhangi bir tutarsızlık varsa, bu yapılandırma profilden örtük yapılandırmadan önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="5ebad-140">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="5ebad-141">Bu sağlayıcı listesi şu biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="5ebad-141">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="5ebad-142">`Provider`Şu biçimdedir: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .</span><span class="sxs-lookup"><span data-stu-id="5ebad-142">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="5ebad-143">`KeyValueArgs`Şu biçimdedir: `[key1=value1][;key2=value2]` .</span><span class="sxs-lookup"><span data-stu-id="5ebad-143">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="5ebad-144">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="5ebad-144">dotnet-trace convert</span></span>

<span data-ttu-id="5ebad-145">`nettrace`Diğer izleme çözümleme araçlarıyla birlikte kullanmak üzere izlemeleri alternatif biçimlere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="5ebad-145">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="5ebad-146">Özeti</span><span class="sxs-lookup"><span data-stu-id="5ebad-146">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="5ebad-147">Arguments</span><span class="sxs-lookup"><span data-stu-id="5ebad-147">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="5ebad-148">Dönüştürülecek giriş izleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="5ebad-148">Input trace file to be converted.</span></span> <span data-ttu-id="5ebad-149">*Trace. NetTrace*için varsayılanlar.</span><span class="sxs-lookup"><span data-stu-id="5ebad-149">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="5ebad-150">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5ebad-150">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="5ebad-151">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5ebad-151">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="5ebad-152">Çıkış dosya adı.</span><span class="sxs-lookup"><span data-stu-id="5ebad-152">Output filename.</span></span> <span data-ttu-id="5ebad-153">Hedef biçimin uzantısı eklenecek.</span><span class="sxs-lookup"><span data-stu-id="5ebad-153">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="5ebad-154">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="5ebad-154">dotnet-trace ps</span></span>

 <span data-ttu-id="5ebad-155">İzlemelerin toplanabilecek DotNet süreçlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="5ebad-155">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="5ebad-156">Özeti</span><span class="sxs-lookup"><span data-stu-id="5ebad-156">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="5ebad-157">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="5ebad-157">dotnet-trace list-profiles</span></span>

<span data-ttu-id="5ebad-158">Her profilde hangi sağlayıcıların ve filtrelerin olduğuna ilişkin bir açıklama ile önceden oluşturulmuş izleme profillerini listeler.</span><span class="sxs-lookup"><span data-stu-id="5ebad-158">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="5ebad-159">Özeti</span><span class="sxs-lookup"><span data-stu-id="5ebad-159">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="5ebad-160">DotNet-Trace ile izleme toplama</span><span class="sxs-lookup"><span data-stu-id="5ebad-160">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="5ebad-161">Kullanarak izlemeleri toplamak için `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="5ebad-161">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="5ebad-162">İzlemeleri toplanacak .NET Core uygulamasının işlem tanımlayıcısını (PID) alın.</span><span class="sxs-lookup"><span data-stu-id="5ebad-162">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="5ebad-163">Windows üzerinde, örneğin, Görev Yöneticisi 'ni veya `tasklist` komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5ebad-163">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="5ebad-164">Linux 'ta, örneğin, `ps` komutu.</span><span class="sxs-lookup"><span data-stu-id="5ebad-164">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="5ebad-165">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="5ebad-165">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="5ebad-166">Aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="5ebad-166">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="5ebad-167">Yukarıdaki komut aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="5ebad-167">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="5ebad-168">Anahtara basarak toplamayı durdurun `<Enter>` .</span><span class="sxs-lookup"><span data-stu-id="5ebad-168">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="5ebad-169">`dotnet-trace`olayları *izleme. NetTrace* dosyasına kaydetme işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="5ebad-169">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="5ebad-170">DotNet 'den yakalanan izlemeyi görüntüleyin-Trace</span><span class="sxs-lookup"><span data-stu-id="5ebad-170">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="5ebad-171">Windows 'da *. NetTrace* dosyaları analiz Için [PerfView](https://github.com/microsoft/perfview) üzerinde görüntülenebilir: diğer platformlarda toplanan izlemeler Için, izleme dosyası PerfView 'Da görüntülenmek üzere bir Windows makinesine taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="5ebad-171">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="5ebad-172">Linux 'ta izleme, ' nin çıkış biçimi değiştirilerek görüntülenebilir `dotnet-trace` `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="5ebad-172">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="5ebad-173">Çıkış dosyası biçimi, seçeneği kullanılarak değiştirilebilir, `-f|--format` `-f speedscope` `dotnet-trace` bir `speedscope` dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5ebad-173">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="5ebad-174">`nettrace`(Varsayılan seçenek) ve arasında seçim yapabilirsiniz `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="5ebad-174">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="5ebad-175">`Speedscope`dosyalar ' de açılabilir <https://www.speedscope.app> .</span><span class="sxs-lookup"><span data-stu-id="5ebad-175">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="5ebad-176">.NET Core çalışma zamanı, biçimde izleme oluşturur `nettrace` .</span><span class="sxs-lookup"><span data-stu-id="5ebad-176">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="5ebad-177">İzlemeler, izleme tamamlandıktan sonra speedscope (belirtilmişse) olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="5ebad-177">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="5ebad-178">Bazı dönüştürmeler veri kaybına neden olabileceğinden, özgün `nettrace` Dosya Dönüştürülen dosyanın yanında korunur.</span><span class="sxs-lookup"><span data-stu-id="5ebad-178">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="5ebad-179">Zaman içinde sayaç değerlerini toplamak için DotNet-Trace kullanın</span><span class="sxs-lookup"><span data-stu-id="5ebad-179">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="5ebad-180">`dotnet-trace`erişebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="5ebad-180">`dotnet-trace` can:</span></span>

* <span data-ttu-id="5ebad-181">`EventCounter`Performans duyarlı ortamlarda temel sistem durumu izleme için kullanın.</span><span class="sxs-lookup"><span data-stu-id="5ebad-181">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="5ebad-182">Örneğin, üretimde.</span><span class="sxs-lookup"><span data-stu-id="5ebad-182">For example, in production.</span></span>
* <span data-ttu-id="5ebad-183">İzlemeleri toplayın, böylece gerçek zamanlı olarak görüntülenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="5ebad-183">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="5ebad-184">Örneğin, çalışma zamanı performans sayacı değerlerini toplamak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="5ebad-184">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="5ebad-185">Yukarıdaki komut, hafif sistem durumu izleme için çalışma zamanı sayaçlarına her saniye bir kez rapor vermesini söyler.</span><span class="sxs-lookup"><span data-stu-id="5ebad-185">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="5ebad-186">`EventCounterIntervalSec=1`Daha yüksek bir değerle değiştirme (örneğin, 60) sayaç verilerinde daha az ayrıntı düzeyi olan daha küçük bir izlemenin toplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="5ebad-186">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="5ebad-187">Aşağıdaki komut ek yükü ve izleme boyutunu önceki olandan daha fazla azaltır:</span><span class="sxs-lookup"><span data-stu-id="5ebad-187">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="5ebad-188">Yukarıdaki komut, çalışma zamanı olaylarını ve yönetilen yığın profil oluşturucuyu devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5ebad-188">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="5ebad-189">.NET sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="5ebad-189">.NET Providers</span></span>

<span data-ttu-id="5ebad-190">.NET Core çalışma zamanı, aşağıdaki .NET sağlayıcılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="5ebad-190">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="5ebad-191">.NET Core, `Event Tracing for Windows (ETW)` ve izlemelerinin etkinleştirilmesi için aynı anahtar kelimeleri kullanır `EventPipe` .</span><span class="sxs-lookup"><span data-stu-id="5ebad-191">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="5ebad-192">Sağlayıcı adı</span><span class="sxs-lookup"><span data-stu-id="5ebad-192">Provider name</span></span>                            | <span data-ttu-id="5ebad-193">Bilgi</span><span class="sxs-lookup"><span data-stu-id="5ebad-193">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="5ebad-194">Çalışma zamanı sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="5ebad-194">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="5ebad-195">CLR çalışma zamanı anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5ebad-195">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="5ebad-196">Özet sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="5ebad-196">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="5ebad-197">CLR Özeti anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="5ebad-197">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="5ebad-198">Örnek profil oluşturucuyu etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="5ebad-198">Enables the sample profiler.</span></span> |
