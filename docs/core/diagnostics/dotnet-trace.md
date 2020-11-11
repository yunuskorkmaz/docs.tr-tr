---
title: DotNet-izleme aracı-.NET Core
description: DotNet-Trace komut satırı aracını yükleme ve kullanma.
ms.date: 11/21/2019
ms.openlocfilehash: d4175ccad785b21f860044a4fd5d691624ec495e
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507234"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="0602b-103">DotNet-izleme performansı Analizi yardımcı programı</span><span class="sxs-lookup"><span data-stu-id="0602b-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="0602b-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="0602b-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-trace"></a><span data-ttu-id="0602b-105">DotNet 'yi Install-Trace</span><span class="sxs-lookup"><span data-stu-id="0602b-105">Install dotnet-trace</span></span>

<span data-ttu-id="0602b-106">`dotnet-trace` [DotNet aracı install](../tools/dotnet-tool-install.md) komutuyla [NuGet paketini](https://www.nuget.org/packages/dotnet-trace) yükler:</span><span class="sxs-lookup"><span data-stu-id="0602b-106">Install `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace) with the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a><span data-ttu-id="0602b-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="0602b-107">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="0602b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0602b-108">Description</span></span>

<span data-ttu-id="0602b-109">`dotnet-trace`Araç:</span><span class="sxs-lookup"><span data-stu-id="0602b-109">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="0602b-110">, Platformlar arası bir .NET Core aracıdır.</span><span class="sxs-lookup"><span data-stu-id="0602b-110">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="0602b-111">Yerel bir profil oluşturucu olmadan çalışan bir işlemin .NET Core izlemelerinin toplanmasını mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="0602b-111">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="0602b-112">, `EventPipe` .NET Core çalışma zamanının platformlar arası teknolojisi etrafında oluşturulmuştur.</span><span class="sxs-lookup"><span data-stu-id="0602b-112">Is built around the cross-platform `EventPipe` technology of the .NET Core runtime.</span></span>
* <span data-ttu-id="0602b-113">Windows, Linux veya macOS 'ta aynı deneyimi sunar.</span><span class="sxs-lookup"><span data-stu-id="0602b-113">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="0602b-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0602b-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="0602b-115">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0602b-115">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="0602b-116">DotNet-Trace yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="0602b-116">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="0602b-117">Komutlar</span><span class="sxs-lookup"><span data-stu-id="0602b-117">Commands</span></span>

| <span data-ttu-id="0602b-118">Komut</span><span class="sxs-lookup"><span data-stu-id="0602b-118">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="0602b-119">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="0602b-119">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="0602b-120">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="0602b-120">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="0602b-121">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="0602b-121">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="0602b-122">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="0602b-122">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="0602b-123">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="0602b-123">dotnet-trace collect</span></span>

<span data-ttu-id="0602b-124">Çalışan bir işlemden bir tanılama izlemesi toplar.</span><span class="sxs-lookup"><span data-stu-id="0602b-124">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="0602b-125">Özeti</span><span class="sxs-lookup"><span data-stu-id="0602b-125">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>]  [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="0602b-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0602b-126">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="0602b-127">Bellek içi dairesel arabelleğin boyutunu megabayt cinsinden ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0602b-127">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="0602b-128">Varsayılan 256 MB.</span><span class="sxs-lookup"><span data-stu-id="0602b-128">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="0602b-129">Oluşturulacak CLR olaylarının ayrıntı düzeyi.</span><span class="sxs-lookup"><span data-stu-id="0602b-129">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="0602b-130">Görüntülenecek CLR çalışma zamanı olaylarının listesi.</span><span class="sxs-lookup"><span data-stu-id="0602b-130">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="0602b-131">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0602b-131">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="0602b-132">Varsayılan değer: `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="0602b-132">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="0602b-133">İzlemenin toplanacağı işlemin adı.</span><span class="sxs-lookup"><span data-stu-id="0602b-133">The name of the process to collect the trace from.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="0602b-134">Toplanan izleme verileri için çıkış yolu.</span><span class="sxs-lookup"><span data-stu-id="0602b-134">The output path for the collected trace data.</span></span> <span data-ttu-id="0602b-135">Belirtilmemişse, varsayılan olarak olur `trace.nettrace` .</span><span class="sxs-lookup"><span data-stu-id="0602b-135">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="0602b-136">İzlemeyi toplanacak işlem kimliği.</span><span class="sxs-lookup"><span data-stu-id="0602b-136">The process id to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="0602b-137">Yaygın izleme senaryolarına izin veren önceden tanımlanmış adlandırılmış bir dizi sağlayıcı yapılandırması succinctly.</span><span class="sxs-lookup"><span data-stu-id="0602b-137">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span>

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="0602b-138">Etkinleştirilecek sağlayıcıların virgülle ayrılmış listesi `EventPipe` .</span><span class="sxs-lookup"><span data-stu-id="0602b-138">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="0602b-139">Bu sağlayıcılar tarafından kapsanan tüm sağlayıcıları tamamlar `--profile <profile-name>` .</span><span class="sxs-lookup"><span data-stu-id="0602b-139">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="0602b-140">Belirli bir sağlayıcı için herhangi bir tutarsızlık varsa, bu yapılandırma profilden örtük yapılandırmadan önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="0602b-140">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="0602b-141">Bu sağlayıcı listesi şu biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="0602b-141">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="0602b-142">`Provider` Şu biçimdedir: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .</span><span class="sxs-lookup"><span data-stu-id="0602b-142">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="0602b-143">`KeyValueArgs` Şu biçimdedir: `[key1=value1][;key2=value2]` .</span><span class="sxs-lookup"><span data-stu-id="0602b-143">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- <span data-ttu-id="0602b-144">**`-- <command>` (yalnızca .NET 5,0 çalıştıran hedef uygulamalar için)**</span><span class="sxs-lookup"><span data-stu-id="0602b-144">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="0602b-145">Koleksiyon yapılandırma parametrelerinden sonra, Kullanıcı, `--` en az bir 5,0 çalışma zamanına sahip bir .NET uygulamasını başlatmak için ardından bir komut ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="0602b-145">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="0602b-146">Bu, işlemin başında gerçekleşen, başlangıç performansı sorunu veya derleme yükleyicisi ve bağlayıcı hataları gibi sorunları tanılarken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0602b-146">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="0602b-147">Bu seçeneğin kullanılması, araca geri iletişim kuran ilk .NET 5,0 işlemini izler, bu da komutunuz birden çok .NET uygulaması başlattığında yalnızca ilk uygulamayı toplayacaktır.</span><span class="sxs-lookup"><span data-stu-id="0602b-147">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="0602b-148">Bu nedenle, bu seçeneği kendi içinde bulunan uygulamalarda veya seçeneğini kullanarak kullanmanız önerilir `dotnet exec <app.dll>` .</span><span class="sxs-lookup"><span data-stu-id="0602b-148">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="0602b-149">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="0602b-149">dotnet-trace convert</span></span>

<span data-ttu-id="0602b-150">`nettrace`Diğer izleme çözümleme araçlarıyla birlikte kullanmak üzere izlemeleri alternatif biçimlere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="0602b-150">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="0602b-151">Özeti</span><span class="sxs-lookup"><span data-stu-id="0602b-151">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="0602b-152">Arguments</span><span class="sxs-lookup"><span data-stu-id="0602b-152">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="0602b-153">Dönüştürülecek giriş izleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="0602b-153">Input trace file to be converted.</span></span> <span data-ttu-id="0602b-154">*Trace. NetTrace* için varsayılanlar.</span><span class="sxs-lookup"><span data-stu-id="0602b-154">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="0602b-155">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0602b-155">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="0602b-156">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0602b-156">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="0602b-157">Çıkış dosya adı.</span><span class="sxs-lookup"><span data-stu-id="0602b-157">Output filename.</span></span> <span data-ttu-id="0602b-158">Hedef biçimin uzantısı eklenecek.</span><span class="sxs-lookup"><span data-stu-id="0602b-158">Extension of target format will be added.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="0602b-159">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="0602b-159">dotnet-trace ps</span></span>

 <span data-ttu-id="0602b-160">İzlemelerin toplanabilecek DotNet süreçlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="0602b-160">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="0602b-161">Özeti</span><span class="sxs-lookup"><span data-stu-id="0602b-161">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="0602b-162">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="0602b-162">dotnet-trace list-profiles</span></span>

<span data-ttu-id="0602b-163">Her profilde hangi sağlayıcıların ve filtrelerin olduğuna ilişkin bir açıklama ile önceden oluşturulmuş izleme profillerini listeler.</span><span class="sxs-lookup"><span data-stu-id="0602b-163">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="0602b-164">Özeti</span><span class="sxs-lookup"><span data-stu-id="0602b-164">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="0602b-165">DotNet-Trace ile izleme toplama</span><span class="sxs-lookup"><span data-stu-id="0602b-165">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="0602b-166">Kullanarak izlemeleri toplamak için `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="0602b-166">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="0602b-167">İzlemeleri toplanacak .NET Core uygulamasının işlem tanımlayıcısını (PID) alın.</span><span class="sxs-lookup"><span data-stu-id="0602b-167">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="0602b-168">Windows üzerinde, örneğin, Görev Yöneticisi 'ni veya `tasklist` komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0602b-168">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="0602b-169">Linux 'ta, örneğin, `ps` komutu.</span><span class="sxs-lookup"><span data-stu-id="0602b-169">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="0602b-170">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="0602b-170">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="0602b-171">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="0602b-171">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="0602b-172">Yukarıdaki komut aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0602b-172">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="0602b-173">Anahtara basarak toplamayı durdurun `<Enter>` .</span><span class="sxs-lookup"><span data-stu-id="0602b-173">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="0602b-174">`dotnet-trace` olayları *izleme. NetTrace* dosyasına kaydetme işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="0602b-174">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="0602b-175">Bir alt uygulama başlatın ve DotNet-Trace kullanarak başlangıçtan bir izleme toplayın</span><span class="sxs-lookup"><span data-stu-id="0602b-175">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

<span data-ttu-id="0602b-176">NOTE: Bu yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="0602b-176">NOTE: This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="0602b-177">Bazen bir işlemin başlangıcında bir izleme toplamak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="0602b-177">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="0602b-178">.NET 5,0 veya üzeri sürümlerini çalıştıran uygulamalar için bu, DotNet-Trace kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="0602b-178">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="0602b-179">Bu, `hello.exe` ile `arg1` ve `arg2` komut satırı bağımsız değişkenleri olarak başlatılır ve çalışma zamanı başlangıcında bir izleme toplar:</span><span class="sxs-lookup"><span data-stu-id="0602b-179">This will launch `hello.exe` with `arg1` and `arg2` as its command line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="0602b-180">Yukarıdaki komut aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="0602b-180">The preceding command generates output similar to the following:</span></span>

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

<span data-ttu-id="0602b-181">Veya tuşuna basarak izlemenin toplanmasını durdurabilirsiniz `<Enter>` `<Ctrl + C>` .</span><span class="sxs-lookup"><span data-stu-id="0602b-181">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="0602b-182">Bunun için de çıkış yapılır `hello.exe` .</span><span class="sxs-lookup"><span data-stu-id="0602b-182">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="0602b-183">`hello.exe`DotNet-Trace aracılığıyla başlatmak, giriş/çıkışının yeniden yönlendirilmesini sağlar ve stdin/stdout ile etkileşime giremeyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="0602b-183">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="0602b-184">CTRL + C veya SIGTERM aracılığıyla araçtan çıkmak, hem aracı hem de alt işlemi güvenle sonlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="0602b-184">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="0602b-185">Alt işlem, araçtan önce çıktığında, araç da sonlandırılır ve izlemenin güvenle görüntülenebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="0602b-185">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="0602b-186">DotNet 'den yakalanan izlemeyi görüntüleyin-Trace</span><span class="sxs-lookup"><span data-stu-id="0602b-186">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="0602b-187">Windows 'da *. NetTrace* dosyaları analiz Için [PerfView](https://github.com/microsoft/perfview) üzerinde görüntülenebilir: diğer platformlarda toplanan izlemeler Için, izleme dosyası PerfView 'Da görüntülenmek üzere bir Windows makinesine taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="0602b-187">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="0602b-188">Linux 'ta izleme, ' nin çıkış biçimi değiştirilerek görüntülenebilir `dotnet-trace` `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="0602b-188">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="0602b-189">Çıkış dosyası biçimi, seçeneği kullanılarak değiştirilebilir, `-f|--format` `-f speedscope` `dotnet-trace` bir `speedscope` dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0602b-189">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="0602b-190">`nettrace`(Varsayılan seçenek) ve arasında seçim yapabilirsiniz `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="0602b-190">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="0602b-191">`Speedscope` dosyalar ' de açılabilir <https://www.speedscope.app> .</span><span class="sxs-lookup"><span data-stu-id="0602b-191">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="0602b-192">.NET Core çalışma zamanı, biçimde izleme oluşturur `nettrace` .</span><span class="sxs-lookup"><span data-stu-id="0602b-192">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="0602b-193">İzlemeler, izleme tamamlandıktan sonra speedscope (belirtilmişse) olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="0602b-193">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="0602b-194">Bazı dönüştürmeler veri kaybına neden olabileceğinden, özgün `nettrace` Dosya Dönüştürülen dosyanın yanında korunur.</span><span class="sxs-lookup"><span data-stu-id="0602b-194">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="0602b-195">Zaman içinde sayaç değerlerini toplamak için DotNet-Trace kullanın</span><span class="sxs-lookup"><span data-stu-id="0602b-195">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="0602b-196">`dotnet-trace` erişebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="0602b-196">`dotnet-trace` can:</span></span>

* <span data-ttu-id="0602b-197">`EventCounter`Performans duyarlı ortamlarda temel sistem durumu izleme için kullanın.</span><span class="sxs-lookup"><span data-stu-id="0602b-197">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="0602b-198">Örneğin, üretimde.</span><span class="sxs-lookup"><span data-stu-id="0602b-198">For example, in production.</span></span>
* <span data-ttu-id="0602b-199">İzlemeleri toplayın, böylece gerçek zamanlı olarak görüntülenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="0602b-199">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="0602b-200">Örneğin, çalışma zamanı performans sayacı değerlerini toplamak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="0602b-200">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="0602b-201">Yukarıdaki komut, hafif sistem durumu izleme için çalışma zamanı sayaçlarına her saniye bir kez rapor vermesini söyler.</span><span class="sxs-lookup"><span data-stu-id="0602b-201">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="0602b-202">`EventCounterIntervalSec=1`Daha yüksek bir değerle değiştirme (örneğin, 60) sayaç verilerinde daha az ayrıntı düzeyi olan daha küçük bir izlemenin toplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="0602b-202">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="0602b-203">Aşağıdaki komut ek yükü ve izleme boyutunu önceki olandan daha fazla azaltır:</span><span class="sxs-lookup"><span data-stu-id="0602b-203">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="0602b-204">Yukarıdaki komut, çalışma zamanı olaylarını ve yönetilen yığın profil oluşturucuyu devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="0602b-204">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="net-providers"></a><span data-ttu-id="0602b-205">.NET sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="0602b-205">.NET Providers</span></span>

<span data-ttu-id="0602b-206">.NET Core çalışma zamanı, aşağıdaki .NET sağlayıcılarını destekler.</span><span class="sxs-lookup"><span data-stu-id="0602b-206">The .NET Core runtime supports the following .NET providers.</span></span> <span data-ttu-id="0602b-207">.NET Core, `Event Tracing for Windows (ETW)` ve izlemelerinin etkinleştirilmesi için aynı anahtar kelimeleri kullanır `EventPipe` .</span><span class="sxs-lookup"><span data-stu-id="0602b-207">.NET Core uses the same keywords to enable both `Event Tracing for Windows (ETW)` and `EventPipe` traces.</span></span>

| <span data-ttu-id="0602b-208">Sağlayıcı adı</span><span class="sxs-lookup"><span data-stu-id="0602b-208">Provider name</span></span>                            | <span data-ttu-id="0602b-209">Bilgi</span><span class="sxs-lookup"><span data-stu-id="0602b-209">Information</span></span> |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [<span data-ttu-id="0602b-210">Çalışma zamanı sağlayıcısı</span><span class="sxs-lookup"><span data-stu-id="0602b-210">The Runtime Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[<span data-ttu-id="0602b-211">CLR çalışma zamanı anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0602b-211">CLR Runtime Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [<span data-ttu-id="0602b-212">Özet sağlayıcı</span><span class="sxs-lookup"><span data-stu-id="0602b-212">The Rundown Provider</span></span>](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[<span data-ttu-id="0602b-213">CLR Özeti anahtar sözcükleri</span><span class="sxs-lookup"><span data-stu-id="0602b-213">CLR Rundown Keywords</span></span>](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | <span data-ttu-id="0602b-214">Örnek profil oluşturucuyu etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0602b-214">Enables the sample profiler.</span></span> |
