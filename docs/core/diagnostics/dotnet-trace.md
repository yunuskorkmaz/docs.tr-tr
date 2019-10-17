---
title: DotNet-Trace-.NET Core
description: DotNet-Trace komut satırı aracını yükleme ve kullanma.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 6513cf63070bc1984006da75313e9912d76a6c95
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321584"
---
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a><span data-ttu-id="60d1f-103">Performans Analizi yardımcı programı için izleme (`dotnet-trace`)</span><span class="sxs-lookup"><span data-stu-id="60d1f-103">Trace for performance analysis utility (`dotnet-trace`)</span></span>

<span data-ttu-id="60d1f-104">**Bu makale şu şekilde geçerlidir:** .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="60d1f-104">**This article applies to:** .NET Core 3.0 SDK and later versions</span></span>

## <a name="installing-dotnet-trace"></a><span data-ttu-id="60d1f-105">@No__t yükleniyor-0</span><span class="sxs-lookup"><span data-stu-id="60d1f-105">Installing `dotnet-trace`</span></span>

<span data-ttu-id="60d1f-106">@No__t-0 [NuGet paketinin](https://www.nuget.org/packages/dotnet-trace)en son sürümünü yüklemek için [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="60d1f-106">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="60d1f-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="60d1f-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="60d1f-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60d1f-108">Description</span></span>

<span data-ttu-id="60d1f-109">@No__t-0 aracı, herhangi bir yerel profil oluşturucu olmadan çalışan bir işlemin .NET Core izlemelerinin toplanmasını sağlayan platformlar arası CLı genel aracıdır.</span><span class="sxs-lookup"><span data-stu-id="60d1f-109">The `dotnet-trace` tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process without any native profiler involved.</span></span> <span data-ttu-id="60d1f-110">.NET Core çalışma zamanının platformlar arası `EventPipe` teknolojisi etrafında oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="60d1f-110">It's built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span> <span data-ttu-id="60d1f-111">`dotnet-trace`, Windows, Linux veya macOS 'ta aynı deneyimi sunar.</span><span class="sxs-lookup"><span data-stu-id="60d1f-111">`dotnet-trace` delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="60d1f-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="60d1f-112">Options</span></span>

- **`--version`**

<span data-ttu-id="60d1f-113">DotNet-Counters yardımcı programının sürümünü görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="60d1f-113">Display the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

<span data-ttu-id="60d1f-114">Komut satırı yardımını göster.</span><span class="sxs-lookup"><span data-stu-id="60d1f-114">Show command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="60d1f-115">Komutlar</span><span class="sxs-lookup"><span data-stu-id="60d1f-115">Commands</span></span>

| <span data-ttu-id="60d1f-116">Komut</span><span class="sxs-lookup"><span data-stu-id="60d1f-116">Command</span></span>                                                     |
| ----------------------------------------------------------- |
| [<span data-ttu-id="60d1f-117">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="60d1f-117">dotnet-trace collect</span></span>](#dotnet-trace-collect)               |
| [<span data-ttu-id="60d1f-118">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="60d1f-118">dotnet-trace convert</span></span>](#dotnet-trace-convert)               |
| [<span data-ttu-id="60d1f-119">DotNet-izleme listesi-süreçler</span><span class="sxs-lookup"><span data-stu-id="60d1f-119">dotnet-trace list-processes</span></span>](#dotnet-trace-list-processes) |
| [<span data-ttu-id="60d1f-120">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="60d1f-120">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="60d1f-121">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="60d1f-121">dotnet-trace collect</span></span>

<span data-ttu-id="60d1f-122">Çalışan bir işlemden bir tanılama izlemesi toplar.</span><span class="sxs-lookup"><span data-stu-id="60d1f-122">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="60d1f-123">Özeti</span><span class="sxs-lookup"><span data-stu-id="60d1f-123">Synopsis</span></span>

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a><span data-ttu-id="60d1f-124">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="60d1f-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="60d1f-125">İzlemeyi toplama işlemi.</span><span class="sxs-lookup"><span data-stu-id="60d1f-125">The process to collect the trace from.</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="60d1f-126">Bellek içi dairesel arabelleğin boyutunu megabayt cinsinden ayarlar.</span><span class="sxs-lookup"><span data-stu-id="60d1f-126">Sets the size of the in-memory circular buffer in megabytes.</span></span> <span data-ttu-id="60d1f-127">Varsayılan 256 MB.</span><span class="sxs-lookup"><span data-stu-id="60d1f-127">Default 256 MB.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="60d1f-128">Toplanan izleme verileri için çıkış yolu.</span><span class="sxs-lookup"><span data-stu-id="60d1f-128">The output path for the collected trace data.</span></span> <span data-ttu-id="60d1f-129">Belirtilmemişse, varsayılan olarak `trace.nettrace` olur.</span><span class="sxs-lookup"><span data-stu-id="60d1f-129">If not specified it defaults to `trace.nettrace`.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="60d1f-130">Etkinleştirilecek `EventPipe` sağlayıcılarının virgülle ayrılmış listesi.</span><span class="sxs-lookup"><span data-stu-id="60d1f-130">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="60d1f-131">Bu sağlayıcılar `--profile <profile-name>` tarafından kapsanan tüm sağlayıcıları tamamlar.</span><span class="sxs-lookup"><span data-stu-id="60d1f-131">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="60d1f-132">Belirli bir sağlayıcı için herhangi bir tutarsızlık varsa, buradaki yapılandırma profilden örtük yapılandırma üzerinden önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="60d1f-132">If there's any inconsistency for a particular provider, the configuration here takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="60d1f-133">Bu sağlayıcı listesi şu biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="60d1f-133">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="60d1f-134">`Provider` şu biçimdedir: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span><span class="sxs-lookup"><span data-stu-id="60d1f-134">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="60d1f-135">`KeyValueArgs` şu biçimdedir: `[key1=value1][;key2=value2]`.</span><span class="sxs-lookup"><span data-stu-id="60d1f-135">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="60d1f-136">Yaygın izleme senaryolarına izin veren önceden tanımlanmış adlandırılmış bir dizi sağlayıcı yapılandırması succinctly.</span><span class="sxs-lookup"><span data-stu-id="60d1f-136">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="60d1f-137">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="60d1f-137">Sets the output format for the trace file conversion.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="60d1f-138">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="60d1f-138">dotnet-trace convert</span></span>

<span data-ttu-id="60d1f-139">Alternatif izleme çözümleme araçlarıyla kullanmak üzere `nettrace` izlemelerini alternatif biçimlere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="60d1f-139">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="60d1f-140">Özeti</span><span class="sxs-lookup"><span data-stu-id="60d1f-140">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a><span data-ttu-id="60d1f-141">Arguments</span><span class="sxs-lookup"><span data-stu-id="60d1f-141">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="60d1f-142">Dönüştürülecek giriş izleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="60d1f-142">Input trace file to be converted.</span></span> <span data-ttu-id="60d1f-143">*Trace. NetTrace*için varsayılanlar.</span><span class="sxs-lookup"><span data-stu-id="60d1f-143">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="60d1f-144">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="60d1f-144">Options</span></span>

- **`--format <NetTrace|Speedscope>`**

  <span data-ttu-id="60d1f-145">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="60d1f-145">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="60d1f-146">Çıkış dosya adı.</span><span class="sxs-lookup"><span data-stu-id="60d1f-146">Output filename.</span></span> <span data-ttu-id="60d1f-147">Hedef biçimin uzantısı eklenecek.</span><span class="sxs-lookup"><span data-stu-id="60d1f-147">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-list-processes"></a><span data-ttu-id="60d1f-148">DotNet-izleme listesi-süreçler</span><span class="sxs-lookup"><span data-stu-id="60d1f-148">dotnet-trace list-processes</span></span>

<span data-ttu-id="60d1f-149">İzlenebilir DotNet süreçlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="60d1f-149">Lists dotnet processes that can be traced.</span></span>

### <a name="synopsis"></a><span data-ttu-id="60d1f-150">Özeti</span><span class="sxs-lookup"><span data-stu-id="60d1f-150">Synopsis</span></span>

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="60d1f-151">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="60d1f-151">dotnet-trace list-profiles</span></span>

<span data-ttu-id="60d1f-152">Her profilde hangi sağlayıcıların ve filtrelerin olduğuna ilişkin bir açıklama ile önceden oluşturulmuş izleme profillerini listeler.</span><span class="sxs-lookup"><span data-stu-id="60d1f-152">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="60d1f-153">Özeti</span><span class="sxs-lookup"><span data-stu-id="60d1f-153">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="60d1f-154">@No__t bir izleme toplayın-0</span><span class="sxs-lookup"><span data-stu-id="60d1f-154">Collect a trace with `dotnet-trace`</span></span>

- <span data-ttu-id="60d1f-155">@No__t-0 kullanarak izlemeleri toplamak için öncelikle .NET Core uygulamasının işlem tanımlayıcısını (PID), izlemeleri toplanacak şekilde bulmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="60d1f-155">To collect traces using `dotnet-trace`, you'll need to first, find out the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="60d1f-156">Windows 'da, Görev Yöneticisi 'ni veya `tasklist` komutunu kullanma gibi seçenekler vardır.</span><span class="sxs-lookup"><span data-stu-id="60d1f-156">On Windows, there are options such as using the task manager or the `tasklist` command.</span></span>
  - <span data-ttu-id="60d1f-157">Linux 'ta, önemsiz seçeneği `ps` komutu kullanıyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="60d1f-157">On Linux, the trivial option could be using `ps` command.</span></span>

<span data-ttu-id="60d1f-158">Ayrıca, hangi .NET Core işlemlerinin çalıştığını, bunların PID 'leri ile birlikte öğrenmek için [DotNet-Trace List-Processes](#dotnet-trace-list-processes) komutunu da kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60d1f-158">You may also use the [dotnet-trace list-processes](#dotnet-trace-list-processes) command to find out what .NET Core processes are running, along with their PIDs.</span></span>

- <span data-ttu-id="60d1f-159">Ardından, aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="60d1f-159">Then, run the following command:</span></span>

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- <span data-ttu-id="60d1f-160">Son olarak, `<Enter>` anahtarına basarak toplamayı durdurun ve `dotnet-trace` `trace.nettrace` dosyasına günlük olaylarını tamamlayacak.</span><span class="sxs-lookup"><span data-stu-id="60d1f-160">Finally, stop collection by pressing the `<Enter>` key, and `dotnet-trace` will finish logging events to `trace.nettrace` file.</span></span>

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="60d1f-161">@No__t yakalanan izlemeyi görüntüleme-0</span><span class="sxs-lookup"><span data-stu-id="60d1f-161">Viewing the trace captured from `dotnet-trace`</span></span>

<span data-ttu-id="60d1f-162">Windows 'da, yalnızca ETW veya LTTng ile toplanan izlemeler gibi `.nettrace` dosyaları, analiz için [PerfView](https://github.com/microsoft/perfview) üzerinde görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="60d1f-162">On Windows, `.nettrace` files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis, just like traces collected with ETW or LTTng.</span></span> <span data-ttu-id="60d1f-163">Linux 'ta toplanan izlemeler için, izlemeyi PerfView 'da görüntülenmek üzere bir Windows makinesine taşıyabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60d1f-163">For traces collected on Linux, you can move the trace to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="60d1f-164">Ayrıca, `dotnet-trace` ' ın çıkış biçimini `speedscope` olarak değiştirerek bir Linux makinesinde izlemeyi görüntüleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60d1f-164">You may also view the trace on a Linux machine by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="60d1f-165">@No__t-0 seçeneğini kullanarak çıkış dosyası biçimini değiştirebilirsiniz-`-f speedscope`, @no__t 3 bir dosya üretmek için `dotnet-trace` ' dir.</span><span class="sxs-lookup"><span data-stu-id="60d1f-165">You can change the output file format using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` to produce a `speedscope` file.</span></span> <span data-ttu-id="60d1f-166">Şu anda `nettrace` (varsayılan seçenek) ve `speedscope` arasında seçim yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60d1f-166">You can currently choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="60d1f-167">`Speedscope` dosyaları <https://www.speedscope.app> ' de açılabilir.</span><span class="sxs-lookup"><span data-stu-id="60d1f-167">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="60d1f-168">.NET Core çalışma zamanı, `nettrace` biçiminde izlemeler oluşturur ve izleme tamamlandıktan sonra speedscope (belirtilmişse) olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="60d1f-168">The .NET Core runtime generates traces in the `nettrace` format, and they're converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="60d1f-169">Bazı dönüştürmeler veri kaybına neden olabileceğinden, özgün `nettrace` dosyası Dönüştürülen dosyanın yanında korunur.</span><span class="sxs-lookup"><span data-stu-id="60d1f-169">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="60d1f-170">Zaman içinde sayaç değerlerini toplamak için `dotnet-trace` kullanma</span><span class="sxs-lookup"><span data-stu-id="60d1f-170">Using `dotnet-trace` to collect counter values over time</span></span>

<span data-ttu-id="60d1f-171">Üretim ortamları gibi performans duyarlı ayarlarda temel sistem durumu izleme için `EventCounter` ' ı kullanmaya çalışıyorsanız ve bunları gerçek zamanlı olarak izlemek yerine izlemeleri toplamak istiyorsanız, bunu `dotnet-trace` ile de yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60d1f-171">If you're trying to use `EventCounter` for basic health monitoring in  performance-sensitive settings like production environments and you want to collect traces instead of watching them in real time, you can do that with `dotnet-trace` as well.</span></span>

<span data-ttu-id="60d1f-172">Örneğin, çalışma zamanı performans sayacı değerlerini toplamak istiyorsanız aşağıdaki komutu kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="60d1f-172">For example, if you want to collect runtime performance counter values, you can use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="60d1f-173">Bu komut, hafif sistem durumu izleme için çalışma zamanı sayaçlarına her saniye bir kez rapor vermesini söyler.</span><span class="sxs-lookup"><span data-stu-id="60d1f-173">This command tells the runtime counters to be reported once every second for lightweight health monitoring.</span></span> <span data-ttu-id="60d1f-174">@No__t-0 ' ı daha yüksek bir değerle değiştirme (örneğin, 60) sayaç verilerinde daha az ayrıntı düzeyi olan daha küçük bir izleme toplamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="60d1f-174">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows you to collect a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="60d1f-175">Ek yükü (ve izleme boyutunu) daha da azaltmak üzere çalışma zamanı olaylarını devre dışı bırakmak istiyorsanız, çalışma zamanı olaylarını ve yönetilen yığın profil oluşturucuyu devre dışı bırakmak için aşağıdaki komutu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="60d1f-175">If you want to disable runtime events to reduce the overhead (and trace size) even further, you can use the following command to disable runtime events and managed stack profiler.</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a><span data-ttu-id="60d1f-176">.NET sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="60d1f-176">.NET Providers</span></span>

<span data-ttu-id="60d1f-177">.NET Core çalışma zamanı, aşağıdaki .NET sağlayıcılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="60d1f-177">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="60d1f-178">.NET Core, hem `Event Tracing for Windows (ETW)` hem de `EventPipe` izlemelerini etkinleştirmek için aynı anahtar kelimeleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="60d1f-178">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="60d1f-179">Sağlayıcı adı</span><span class="sxs-lookup"><span data-stu-id="60d1f-179">Provider name</span></span>                            | <span data-ttu-id="60d1f-180">Bilgiler</span><span class="sxs-lookup"><span data-stu-id="60d1f-180">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="60d1f-181">Çalışma zamanı sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="60d1f-181">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="60d1f-182">CLR çalışma zamanı anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="60d1f-182">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="60d1f-183">Özet sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="60d1f-183">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="60d1f-184">CLR Özeti anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="60d1f-184">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="60d1f-185">Örnek profil oluşturucuyu etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="60d1f-185">Enables the sample profiler.</span></span> |
