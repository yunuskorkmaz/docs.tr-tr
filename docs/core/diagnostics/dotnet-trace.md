---
title: DotNet-Trace Tanılama aracı-.NET CLı
description: .NET EventPipe kullanarak, yerel profil oluşturucu olmadan çalışan bir işlemin .NET izlemelerini toplamak için DotNet-Trace CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: a3b5748cb2a6c2060971fbad0d81ade00dc83087
ms.sourcegitcommit: 35ca2255c6c86968eaef9e3a251c9739ce8e4288
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2020
ms.locfileid: "97753682"
---
# <a name="dotnet-trace-performance-analysis-utility"></a><span data-ttu-id="36f1f-103">DotNet-izleme performansı Analizi yardımcı programı</span><span class="sxs-lookup"><span data-stu-id="36f1f-103">dotnet-trace performance analysis utility</span></span>

<span data-ttu-id="36f1f-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="36f1f-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="36f1f-105">Yükleme</span><span class="sxs-lookup"><span data-stu-id="36f1f-105">Install</span></span>

<span data-ttu-id="36f1f-106">İndirmek ve yüklemek için iki yol vardır `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="36f1f-106">There are two ways to download and install `dotnet-trace`:</span></span>

- <span data-ttu-id="36f1f-107">**DotNet genel aracı:**</span><span class="sxs-lookup"><span data-stu-id="36f1f-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="36f1f-108">NuGet paketinin en son sürümünü yüklemek için `dotnet-trace` [](https://www.nuget.org/packages/dotnet-trace) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="36f1f-108">To install the latest release version of the `dotnet-trace` [NuGet package](https://www.nuget.org/packages/dotnet-trace), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-trace
  ```

- <span data-ttu-id="36f1f-109">**Doğrudan indirme:**</span><span class="sxs-lookup"><span data-stu-id="36f1f-109">**Direct download:**</span></span>

  <span data-ttu-id="36f1f-110">Platformunuzla eşleşen araç yürütülebilirini indirin:</span><span class="sxs-lookup"><span data-stu-id="36f1f-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="36f1f-111">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="36f1f-111">OS</span></span>  | <span data-ttu-id="36f1f-112">Platform</span><span class="sxs-lookup"><span data-stu-id="36f1f-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="36f1f-113">Windows</span><span class="sxs-lookup"><span data-stu-id="36f1f-113">Windows</span></span> | <span data-ttu-id="36f1f-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [ARM](https://aka.ms/dotnet-trace/win-arm) \| [ARM-x64](https://aka.ms/dotnet-trace/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="36f1f-114">[x86](https://aka.ms/dotnet-trace/win-x86) \| [x64](https://aka.ms/dotnet-trace/win-x64) \| [arm](https://aka.ms/dotnet-trace/win-arm) \| [arm-x64](https://aka.ms/dotnet-trace/win-arm64)</span></span> |
  | <span data-ttu-id="36f1f-115">macOS</span><span class="sxs-lookup"><span data-stu-id="36f1f-115">macOS</span></span>   | [<span data-ttu-id="36f1f-116">x64</span><span class="sxs-lookup"><span data-stu-id="36f1f-116">x64</span></span>](https://aka.ms/dotnet-trace/osx-x64) |
  | <span data-ttu-id="36f1f-117">Linux</span><span class="sxs-lookup"><span data-stu-id="36f1f-117">Linux</span></span>   | <span data-ttu-id="36f1f-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [ARM](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="36f1f-118">[x64](https://aka.ms/dotnet-trace/linux-x64) \| [arm](https://aka.ms/dotnet-trace/linux-arm) \| [arm64](https://aka.ms/dotnet-trace/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-trace/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-trace/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="36f1f-119">Özeti</span><span class="sxs-lookup"><span data-stu-id="36f1f-119">Synopsis</span></span>

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="36f1f-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36f1f-120">Description</span></span>

<span data-ttu-id="36f1f-121">`dotnet-trace`Araç:</span><span class="sxs-lookup"><span data-stu-id="36f1f-121">The `dotnet-trace` tool:</span></span>

* <span data-ttu-id="36f1f-122">, Platformlar arası bir .NET Core aracıdır.</span><span class="sxs-lookup"><span data-stu-id="36f1f-122">Is a cross-platform .NET Core tool.</span></span>
* <span data-ttu-id="36f1f-123">Yerel bir profil oluşturucu olmadan çalışan bir işlemin .NET Core izlemelerinin toplanmasını mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="36f1f-123">Enables the collection of .NET Core traces of a running process without a native profiler.</span></span>
* <span data-ttu-id="36f1f-124">, [`EventPipe`](./eventpipe.md) .NET Core çalışma zamanı üzerine kurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="36f1f-124">Is built on [`EventPipe`](./eventpipe.md) of the .NET Core runtime.</span></span>
* <span data-ttu-id="36f1f-125">Windows, Linux veya macOS 'ta aynı deneyimi sunar.</span><span class="sxs-lookup"><span data-stu-id="36f1f-125">Delivers the same experience on Windows, Linux, or macOS.</span></span>

## <a name="options"></a><span data-ttu-id="36f1f-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="36f1f-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="36f1f-127">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-127">Shows command-line help.</span></span>

- **`--version`**

  <span data-ttu-id="36f1f-128">DotNet-Trace yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="36f1f-128">Displays the version of the dotnet-trace utility.</span></span>

## <a name="commands"></a><span data-ttu-id="36f1f-129">Komutlar</span><span class="sxs-lookup"><span data-stu-id="36f1f-129">Commands</span></span>

| <span data-ttu-id="36f1f-130">Komut</span><span class="sxs-lookup"><span data-stu-id="36f1f-130">Command</span></span>                                                   |
|-----------------------------------------------------------|
| [<span data-ttu-id="36f1f-131">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="36f1f-131">dotnet-trace collect</span></span>](#dotnet-trace-collect)             |
| [<span data-ttu-id="36f1f-132">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="36f1f-132">dotnet-trace convert</span></span>](#dotnet-trace-convert)             |
| [<span data-ttu-id="36f1f-133">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="36f1f-133">dotnet-trace ps</span></span>](#dotnet-trace-ps)                       |
| [<span data-ttu-id="36f1f-134">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="36f1f-134">dotnet-trace list-profiles</span></span>](#dotnet-trace-list-profiles) |

## <a name="dotnet-trace-collect"></a><span data-ttu-id="36f1f-135">DotNet-izleme toplama</span><span class="sxs-lookup"><span data-stu-id="36f1f-135">dotnet-trace collect</span></span>

<span data-ttu-id="36f1f-136">Çalışan bir işlemden bir tanılama izlemesi toplar.</span><span class="sxs-lookup"><span data-stu-id="36f1f-136">Collects a diagnostic trace from a running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="36f1f-137">Özeti</span><span class="sxs-lookup"><span data-stu-id="36f1f-137">Synopsis</span></span>

```console
dotnet-trace collect [--buffersize <size>] [--clreventlevel <clreventlevel>] [--clrevents <clrevents>]
    [--format <Chromium|NetTrace|Speedscope>] [-h|--help]
    [-n, --name <name>] [--diagnostic-port] [-o|--output <trace-file-path>] [-p|--process-id <pid>]
    [--profile <profile-name>] [--providers <list-of-comma-separated-providers>]
    [-- <command>] (for target applications running .NET 5.0 or later)
```

### <a name="options"></a><span data-ttu-id="36f1f-138">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="36f1f-138">Options</span></span>

- **`--buffersize <size>`**

  <span data-ttu-id="36f1f-139">Bellek içi dairesel arabelleğin boyutunu megabayt cinsinden ayarlar.</span><span class="sxs-lookup"><span data-stu-id="36f1f-139">Sets the size of the in-memory circular buffer, in megabytes.</span></span> <span data-ttu-id="36f1f-140">Varsayılan 256 MB.</span><span class="sxs-lookup"><span data-stu-id="36f1f-140">Default 256 MB.</span></span>

- **`--clreventlevel <clreventlevel>`**

  <span data-ttu-id="36f1f-141">Oluşturulacak CLR olaylarının ayrıntı düzeyi.</span><span class="sxs-lookup"><span data-stu-id="36f1f-141">Verbosity of CLR events to be emitted.</span></span>

- **`--clrevents <clrevents>`**

  <span data-ttu-id="36f1f-142">Görüntülenecek CLR çalışma zamanı olaylarının listesi.</span><span class="sxs-lookup"><span data-stu-id="36f1f-142">List of CLR runtime events to emit.</span></span>

- **`--format {Chromium|NetTrace|Speedscope}`**

  <span data-ttu-id="36f1f-143">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="36f1f-143">Sets the output format for the trace file conversion.</span></span> <span data-ttu-id="36f1f-144">Varsayılan değer: `NetTrace`.</span><span class="sxs-lookup"><span data-stu-id="36f1f-144">The default is `NetTrace`.</span></span>

- **`-n, --name <name>`**

  <span data-ttu-id="36f1f-145">İzlemenin toplanacağı işlemin adı.</span><span class="sxs-lookup"><span data-stu-id="36f1f-145">The name of the process to collect the trace from.</span></span>

- **`--diagnostic-port <path-to-port>`**

  <span data-ttu-id="36f1f-146">Oluşturulacak tanılama bağlantı noktasının adı.</span><span class="sxs-lookup"><span data-stu-id="36f1f-146">The name of the diagnostic port to create.</span></span> <span data-ttu-id="36f1f-147">Uygulamanın başlangıcında bir izleme toplamak için bu seçeneği nasıl kullanacağınızı öğrenmek için bkz. [Uygulama başlangıcında bir izleme toplamak için tanılama bağlantı noktası kullanma](#use-diagnostic-port-to-collect-a-trace-from-app-startup) .</span><span class="sxs-lookup"><span data-stu-id="36f1f-147">See [Use diagnostic port to collect a trace from app startup](#use-diagnostic-port-to-collect-a-trace-from-app-startup) to learn how to use this option to collect a trace from app startup.</span></span>

- **`-o|--output <trace-file-path>`**

  <span data-ttu-id="36f1f-148">Toplanan izleme verileri için çıkış yolu.</span><span class="sxs-lookup"><span data-stu-id="36f1f-148">The output path for the collected trace data.</span></span> <span data-ttu-id="36f1f-149">Belirtilmemişse, varsayılan olarak olur `trace.nettrace` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-149">If not specified, it defaults to `trace.nettrace`.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="36f1f-150">İzlemeyi toplanacak işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="36f1f-150">The process ID to collect the trace from.</span></span>

- **`--profile <profile-name>`**

  <span data-ttu-id="36f1f-151">Yaygın izleme senaryolarına izin veren önceden tanımlanmış adlandırılmış bir dizi sağlayıcı yapılandırması succinctly.</span><span class="sxs-lookup"><span data-stu-id="36f1f-151">A named pre-defined set of provider configurations that allows common tracing scenarios to be specified succinctly.</span></span> <span data-ttu-id="36f1f-152">Aşağıdaki profiller mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="36f1f-152">The following profiles are available:</span></span>

 | <span data-ttu-id="36f1f-153">Profil</span><span class="sxs-lookup"><span data-stu-id="36f1f-153">Profile</span></span> | <span data-ttu-id="36f1f-154">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36f1f-154">Description</span></span> |
 |---------|-------------|
 |`cpu-sampling`|<span data-ttu-id="36f1f-155">CPU kullanımını ve genel .NET çalışma zamanı bilgilerini izlemek için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="36f1f-155">Useful for tracking CPU usage and general .NET runtime information.</span></span> <span data-ttu-id="36f1f-156">Profil veya sağlayıcı belirtilmemişse bu varsayılan seçenektir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-156">This is the default option if no profile or providers are specified.</span></span>|
 |`gc-verbose`|<span data-ttu-id="36f1f-157">GC koleksiyonlarını izler ve nesne ayırmalarını örnekler.</span><span class="sxs-lookup"><span data-stu-id="36f1f-157">Tracks GC collections and samples object allocations.</span></span>|
 |`gc-collect`|<span data-ttu-id="36f1f-158">GC koleksiyonlarını yalnızca çok düşük ek yüklerle izler.</span><span class="sxs-lookup"><span data-stu-id="36f1f-158">Tracks GC collections only at very low overhead.</span></span>|

- **`--providers <list-of-comma-separated-providers>`**

  <span data-ttu-id="36f1f-159">Etkinleştirilecek sağlayıcıların virgülle ayrılmış listesi `EventPipe` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-159">A comma-separated list of `EventPipe` providers to be enabled.</span></span> <span data-ttu-id="36f1f-160">Bu sağlayıcılar tarafından kapsanan tüm sağlayıcıları tamamlar `--profile <profile-name>` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-160">These providers supplement any providers implied by `--profile <profile-name>`.</span></span> <span data-ttu-id="36f1f-161">Belirli bir sağlayıcı için herhangi bir tutarsızlık varsa, bu yapılandırma profilden örtük yapılandırmadan önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-161">If there's any inconsistency for a particular provider, this configuration takes precedence over the implicit configuration from the profile.</span></span>

  <span data-ttu-id="36f1f-162">Bu sağlayıcı listesi şu biçimdedir:</span><span class="sxs-lookup"><span data-stu-id="36f1f-162">This list of providers is in the form:</span></span>

  - `Provider[,Provider]`
  - <span data-ttu-id="36f1f-163">`Provider` Şu biçimdedir: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-163">`Provider` is in the form: `KnownProviderName[:Flags[:Level][:KeyValueArgs]]`.</span></span>
  - <span data-ttu-id="36f1f-164">`KeyValueArgs` Şu biçimdedir: `[key1=value1][;key2=value2]` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-164">`KeyValueArgs` is in the form: `[key1=value1][;key2=value2]`.</span></span>

- <span data-ttu-id="36f1f-165">**`-- <command>` (yalnızca .NET 5,0 çalıştıran hedef uygulamalar için)**</span><span class="sxs-lookup"><span data-stu-id="36f1f-165">**`-- <command>` (for target applications running .NET 5.0 only)**</span></span>

  <span data-ttu-id="36f1f-166">Koleksiyon yapılandırma parametrelerinden sonra, Kullanıcı, `--` en az bir 5,0 çalışma zamanına sahip bir .NET uygulamasını başlatmak için ardından bir komut ekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-166">After the collection configuration parameters, the user can append `--` followed by a command to start a .NET application with at least a 5.0 runtime.</span></span> <span data-ttu-id="36f1f-167">Bu, işlemin başında gerçekleşen, başlangıç performansı sorunu veya derleme yükleyicisi ve bağlayıcı hataları gibi sorunları tanılarken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-167">This may be helpful when diagnosing issues that happen early in the process, such as startup performance issue or assembly loader and binder errors.</span></span>

  > [!NOTE]
  > <span data-ttu-id="36f1f-168">Bu seçeneğin kullanılması, araca geri iletişim kuran ilk .NET 5,0 işlemini izler, bu da komutunuz birden çok .NET uygulaması başlattığında yalnızca ilk uygulamayı toplayacaktır.</span><span class="sxs-lookup"><span data-stu-id="36f1f-168">Using this option monitors the first .NET 5.0 process that communicates back to the tool, which means if your command launches multiple .NET applications, it will only collect the first app.</span></span> <span data-ttu-id="36f1f-169">Bu nedenle, bu seçeneği kendi içinde bulunan uygulamalarda veya seçeneğini kullanarak kullanmanız önerilir `dotnet exec <app.dll>` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-169">Therefore, it is recommended you use this option on self-contained applications, or using the `dotnet exec <app.dll>` option.</span></span>

> [!NOTE]
> <span data-ttu-id="36f1f-170">İzlemenin durdurulması, büyük uygulamalar için uzun zaman alabilir (en fazla dakika).</span><span class="sxs-lookup"><span data-stu-id="36f1f-170">Stopping the trace may take a long time (up to minutes) for large applications.</span></span> <span data-ttu-id="36f1f-171">Çalışma zamanının, izlemede yakalanan tüm yönetilen kodlar için tür önbelleğinin üzerine gönderilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-171">The runtime needs to send over the type cache for all managed code that was captured in the trace.</span></span>

## <a name="dotnet-trace-convert"></a><span data-ttu-id="36f1f-172">DotNet-Trace Dönüştür</span><span class="sxs-lookup"><span data-stu-id="36f1f-172">dotnet-trace convert</span></span>

<span data-ttu-id="36f1f-173">`nettrace`Diğer izleme çözümleme araçlarıyla birlikte kullanmak üzere izlemeleri alternatif biçimlere dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="36f1f-173">Converts `nettrace` traces to alternate formats for use with alternate trace analysis tools.</span></span>

### <a name="synopsis"></a><span data-ttu-id="36f1f-174">Özeti</span><span class="sxs-lookup"><span data-stu-id="36f1f-174">Synopsis</span></span>

```console
dotnet-trace convert [<input-filename>] [--format <Chromium|NetTrace|Speedscope>] [-h|--help] [-o|--output <output-filename>]
```

### <a name="arguments"></a><span data-ttu-id="36f1f-175">Arguments</span><span class="sxs-lookup"><span data-stu-id="36f1f-175">Arguments</span></span>

- **`<input-filename>`**

  <span data-ttu-id="36f1f-176">Dönüştürülecek giriş izleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="36f1f-176">Input trace file to be converted.</span></span> <span data-ttu-id="36f1f-177">*Trace. NetTrace* için varsayılanlar.</span><span class="sxs-lookup"><span data-stu-id="36f1f-177">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="36f1f-178">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="36f1f-178">Options</span></span>

- **`--format <Chromium|NetTrace|Speedscope>`**

  <span data-ttu-id="36f1f-179">İzleme dosyası dönüştürmesi için çıkış biçimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="36f1f-179">Sets the output format for the trace file conversion.</span></span>

- **`-o|--output <output-filename>`**

  <span data-ttu-id="36f1f-180">Çıkış dosya adı.</span><span class="sxs-lookup"><span data-stu-id="36f1f-180">Output filename.</span></span> <span data-ttu-id="36f1f-181">Hedef biçimin uzantısı eklenecek.</span><span class="sxs-lookup"><span data-stu-id="36f1f-181">Extension of target format will be added.</span></span>

> [!NOTE]
> <span data-ttu-id="36f1f-182">`nettrace`Dosyaları `chromium` veya dosyaları dönüştürme `speedscope` işlemi geri alınamaz.</span><span class="sxs-lookup"><span data-stu-id="36f1f-182">Converting `nettrace` files to `chromium` or `speedscope` files is irreversible.</span></span> <span data-ttu-id="36f1f-183">`speedscope` dosyalar `chromium` , dosyaları yeniden oluşturmak için gereken tüm bilgileri içermez `nettrace` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-183">`speedscope` and `chromium` files don't have all the information necessary to reconstruct `nettrace` files.</span></span> <span data-ttu-id="36f1f-184">Ancak, `convert` komut özgün `nettrace` dosyayı korur, bu nedenle daha sonra açmayı planlıyorsanız bu dosyayı silmeyin.</span><span class="sxs-lookup"><span data-stu-id="36f1f-184">However, the `convert` command preserves the original `nettrace` file, so don't delete this file if you plan to open it in the future.</span></span>

## <a name="dotnet-trace-ps"></a><span data-ttu-id="36f1f-185">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="36f1f-185">dotnet-trace ps</span></span>

 <span data-ttu-id="36f1f-186">İzlemelerin toplanabilecek DotNet süreçlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="36f1f-186">Lists the dotnet processes that traces can be collected from.</span></span>

### <a name="synopsis"></a><span data-ttu-id="36f1f-187">Özeti</span><span class="sxs-lookup"><span data-stu-id="36f1f-187">Synopsis</span></span>

```console
dotnet-trace ps [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a><span data-ttu-id="36f1f-188">DotNet-izleme listesi-profiller</span><span class="sxs-lookup"><span data-stu-id="36f1f-188">dotnet-trace list-profiles</span></span>

<span data-ttu-id="36f1f-189">Her profilde hangi sağlayıcıların ve filtrelerin olduğuna ilişkin bir açıklama ile önceden oluşturulmuş izleme profillerini listeler.</span><span class="sxs-lookup"><span data-stu-id="36f1f-189">Lists pre-built tracing profiles with a description of what providers and filters are in each profile.</span></span>

### <a name="synopsis"></a><span data-ttu-id="36f1f-190">Özeti</span><span class="sxs-lookup"><span data-stu-id="36f1f-190">Synopsis</span></span>

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a><span data-ttu-id="36f1f-191">DotNet-Trace ile izleme toplama</span><span class="sxs-lookup"><span data-stu-id="36f1f-191">Collect a trace with dotnet-trace</span></span>

<span data-ttu-id="36f1f-192">Kullanarak izlemeleri toplamak için `dotnet-trace` :</span><span class="sxs-lookup"><span data-stu-id="36f1f-192">To collect traces using `dotnet-trace`:</span></span>

- <span data-ttu-id="36f1f-193">İzlemeleri toplanacak .NET Core uygulamasının işlem tanımlayıcısını (PID) alın.</span><span class="sxs-lookup"><span data-stu-id="36f1f-193">Get the process identifier (PID) of the .NET Core application to collect traces from.</span></span>

  - <span data-ttu-id="36f1f-194">Windows üzerinde, örneğin, Görev Yöneticisi 'ni veya `tasklist` komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36f1f-194">On Windows, you can use Task Manager or the `tasklist` command, for example.</span></span>
  - <span data-ttu-id="36f1f-195">Linux 'ta, örneğin, `ps` komutu.</span><span class="sxs-lookup"><span data-stu-id="36f1f-195">On Linux, for example, the `ps` command.</span></span>
  - [<span data-ttu-id="36f1f-196">DotNet-izleme PS 'si</span><span class="sxs-lookup"><span data-stu-id="36f1f-196">dotnet-trace ps</span></span>](#dotnet-trace-ps)

- <span data-ttu-id="36f1f-197">Şu komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="36f1f-197">Run the following command:</span></span>

  ```console
  dotnet-trace collect --process-id <PID>
  ```

  <span data-ttu-id="36f1f-198">Yukarıdaki komut aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="36f1f-198">The preceding command generates output similar to the following:</span></span>

  ```console
  Press <Enter> to exit...
  Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
  Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
  ```

- <span data-ttu-id="36f1f-199">Anahtara basarak toplamayı durdurun `<Enter>` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-199">Stop collection by pressing the `<Enter>` key.</span></span> <span data-ttu-id="36f1f-200">`dotnet-trace` olayları *izleme. NetTrace* dosyasına kaydetme işlemi tamamlanır.</span><span class="sxs-lookup"><span data-stu-id="36f1f-200">`dotnet-trace` will finish logging events to the *trace.nettrace* file.</span></span>

## <a name="launch-a-child-application-and-collect-a-trace-from-its-startup-using-dotnet-trace"></a><span data-ttu-id="36f1f-201">Bir alt uygulama başlatın ve DotNet-Trace kullanarak başlangıçtan bir izleme toplayın</span><span class="sxs-lookup"><span data-stu-id="36f1f-201">Launch a child application and collect a trace from its startup using dotnet-trace</span></span>

> [!IMPORTANT]
> <span data-ttu-id="36f1f-202">Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-202">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="36f1f-203">Bazen bir işlemin başlangıcında bir izleme toplamak yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-203">Sometimes it may be useful to collect a trace of a process from its startup.</span></span> <span data-ttu-id="36f1f-204">.NET 5,0 veya üzeri sürümlerini çalıştıran uygulamalar için bu, DotNet-Trace kullanılarak yapılabilir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-204">For apps running .NET 5.0 or later, it is possible to do this by using dotnet-trace.</span></span>

<span data-ttu-id="36f1f-205">Bu, `hello.exe` `arg1` ve `arg2` komut satırı bağımsız değişkenleriyle başlatılır ve çalışma zamanı başlangıcında bir izleme toplar:</span><span class="sxs-lookup"><span data-stu-id="36f1f-205">This will launch `hello.exe` with `arg1` and `arg2` as its command-line arguments and collect a trace from its runtime startup:</span></span>

```console
dotnet-trace collect -- hello.exe arg1 arg2
```

<span data-ttu-id="36f1f-206">Yukarıdaki komut aşağıdakine benzer bir çıktı oluşturur:</span><span class="sxs-lookup"><span data-stu-id="36f1f-206">The preceding command generates output similar to the following:</span></span>

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

<span data-ttu-id="36f1f-207">Veya tuşuna basarak izlemenin toplanmasını durdurabilirsiniz `<Enter>` `<Ctrl + C>` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-207">You can stop collecting the trace by pressing `<Enter>` or `<Ctrl + C>` key.</span></span> <span data-ttu-id="36f1f-208">Bunun için de çıkış yapılır `hello.exe` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-208">Doing this will also exit `hello.exe`.</span></span>

> [!NOTE]
> <span data-ttu-id="36f1f-209">`hello.exe`DotNet-Trace aracılığıyla başlatmak, giriş/çıkışının yeniden yönlendirilmesini sağlar ve stdin/stdout ile etkileşime giremeyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="36f1f-209">Launching `hello.exe` via dotnet-trace will make its input/output to be redirected and you won't be able to interact with its stdin/stdout.</span></span>
> <span data-ttu-id="36f1f-210">CTRL + C veya SIGTERM aracılığıyla araçtan çıkmak, hem aracı hem de alt işlemi güvenle sonlandıracaktır.</span><span class="sxs-lookup"><span data-stu-id="36f1f-210">Exiting the tool via CTRL+C or SIGTERM will safely end both the tool and the child process.</span></span>
> <span data-ttu-id="36f1f-211">Alt işlem, araçtan önce çıktığında, araç da sonlandırılır ve izlemenin güvenle görüntülenebilir olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-211">If the child process exits before the tool, the tool will exit as well and the trace should be safely viewable.</span></span>

## <a name="use-diagnostic-port-to-collect-a-trace-from-app-startup"></a><span data-ttu-id="36f1f-212">Uygulama başlangıcında bir izleme toplamak için tanılama bağlantı noktasını kullan</span><span class="sxs-lookup"><span data-stu-id="36f1f-212">Use diagnostic port to collect a trace from app startup</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="36f1f-213">Bu, yalnızca .NET 5,0 veya sonraki sürümleri çalıştıran uygulamalar için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-213">This works for apps running .NET 5.0 or later only.</span></span>

<span data-ttu-id="36f1f-214">Tanılama bağlantı noktası, .NET 5 ' te eklenen ve uygulama başlangıcında izlemeye başlayabilmeniz için yeni bir çalışma zamanı özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-214">Diagnostic port is a new runtime feature that was added in .NET 5 that allows you to start tracing from app startup.</span></span> <span data-ttu-id="36f1f-215">Bunu kullanarak yapmak için `dotnet-trace` `dotnet-trace collect -- <command>` Yukarıdaki örneklerde açıklandığı gibi kullanabilirsiniz veya `--diagnostic-port` seçeneğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36f1f-215">To do this using `dotnet-trace`, you can either use `dotnet-trace collect -- <command>` as described in the examples above, or use the `--diagnostic-port` option.</span></span>

<span data-ttu-id="36f1f-216">`dotnet-trace <collect|monitor> -- <command>`Uygulamayı bir alt işlem olarak başlatmak için kullanmak, bunu başlangıçtan hızlı bir şekilde izlemenin en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="36f1f-216">Using `dotnet-trace <collect|monitor> -- <command>` to launch the application as a child process is the simplest way to quickly trace it from its startup.</span></span>

<span data-ttu-id="36f1f-217">Ancak, izlenen uygulamanın ömrü boyunca daha ayrıntılı bir denetim elde etmek istediğinizde (örneğin, uygulamayı yalnızca ilk 10 dakika boyunca izleyin ve yürütülmeye devam edin) veya CLı kullanarak uygulamayla etkileşime ihtiyacınız varsa, kullanma `--diagnostic-port` seçeneği, hem izlenen hem de hedef uygulamayı denetlemenize olanak tanır `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-217">However, when you want to gain a finer control over the lifetime of the app being traced (for example, monitor the app for the first 10 minutes only and continue executing) or if you need to interact with the app using the CLI, using `--diagnostic-port` option allows you to control both the target app being monitored and `dotnet-trace`.</span></span>

1. <span data-ttu-id="36f1f-218">Aşağıdaki komut `dotnet-trace` adlı bir tanılama yuvası oluşturur `myport.sock` ve bir bağlantı bekler.</span><span class="sxs-lookup"><span data-stu-id="36f1f-218">The command below makes `dotnet-trace` create a diagnostics socket named `myport.sock` and wait for a connection.</span></span>

    > ```dotnet-cli
    > dotnet-trace collect --diagnostic-port myport.sock
    > ```

    <span data-ttu-id="36f1f-219">Çıkış:</span><span class="sxs-lookup"><span data-stu-id="36f1f-219">Output:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ```

2. <span data-ttu-id="36f1f-220">Ayrı bir konsolda, hedef uygulamayı `DOTNET_DiagnosticPorts` Çıkış içindeki değere ayarlanmış ortam değişkeni ile başlatın `dotnet-trace` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-220">In a separate console, launch the target application with the environment variable `DOTNET_DiagnosticPorts` set to the value in the `dotnet-trace` output.</span></span>

    > ```bash
    > export DOTNET_DiagnosticPorts=/home/user/myport.sock
    > ./my-dotnet-app arg1 arg2
    > ```

    <span data-ttu-id="36f1f-221">`dotnet-trace`İzlemeye başlamak için bu daha sonra etkinleştirmelisiniz `my-dotnet-app` :</span><span class="sxs-lookup"><span data-stu-id="36f1f-221">This should then enable `dotnet-trace` to start tracing `my-dotnet-app`:</span></span>

    > ```bash
    > Waiting for connection on myport.sock
    > Start an application with the following environment variable: DOTNET_DiagnosticPorts=myport.sock
    > Starting a counter session. Press Q to quit.
    > ```

    > [!IMPORTANT]
    > <span data-ttu-id="36f1f-222">`dotnet run`DotNet CLI, uygulamanız olmayan çok sayıda alt işlem oluşturduğundan ve uygulamanızın `dotnet-trace` çalışma zamanında askıya alınması için uygulamadan önce bağlanabildikleri için uygulamanızın ile başlatılması sorunlu olabilir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-222">Launching your app with `dotnet run` can be problematic because the dotnet CLI may spawn many child processes that are not your app and they can connect to `dotnet-trace` before your app, leaving your app to be suspended at runtime.</span></span> <span data-ttu-id="36f1f-223">Uygulamanın otomatik olarak kapsanan bir sürümünü kullanmanız veya `dotnet exec` uygulamayı başlatmak için kullanmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-223">It is recommended you directly use a self-contained version of the app or use `dotnet exec` to launch the application.</span></span>

## <a name="view-the-trace-captured-from-dotnet-trace"></a><span data-ttu-id="36f1f-224">DotNet 'den yakalanan izlemeyi görüntüleyin-Trace</span><span class="sxs-lookup"><span data-stu-id="36f1f-224">View the trace captured from dotnet-trace</span></span>

<span data-ttu-id="36f1f-225">Windows 'da *. NetTrace* dosyaları analiz Için [PerfView](https://github.com/microsoft/perfview) üzerinde görüntülenebilir: diğer platformlarda toplanan izlemeler Için, izleme dosyası PerfView 'Da görüntülenmek üzere bir Windows makinesine taşınabilir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-225">On Windows, *.nettrace* files can be viewed on [PerfView](https://github.com/microsoft/perfview) for analysis: For traces collected on other platforms, the trace file can be moved to a Windows machine to be viewed on PerfView.</span></span>

<span data-ttu-id="36f1f-226">Linux 'ta izleme, ' nin çıkış biçimi değiştirilerek görüntülenebilir `dotnet-trace` `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-226">On Linux, the trace can be viewed by changing the output format of `dotnet-trace` to `speedscope`.</span></span> <span data-ttu-id="36f1f-227">Çıkış dosyası biçimi, seçeneği kullanılarak değiştirilebilir, `-f|--format` `-f speedscope` `dotnet-trace` bir `speedscope` dosya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="36f1f-227">The output file format can be changed using the `-f|--format` option - `-f speedscope` will make `dotnet-trace` produce a `speedscope` file.</span></span> <span data-ttu-id="36f1f-228">`nettrace`(Varsayılan seçenek) ve arasında seçim yapabilirsiniz `speedscope` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-228">You can choose between `nettrace` (the default option) and `speedscope`.</span></span> <span data-ttu-id="36f1f-229">`Speedscope` dosyalar ' de açılabilir <https://www.speedscope.app> .</span><span class="sxs-lookup"><span data-stu-id="36f1f-229">`Speedscope` files can be opened at <https://www.speedscope.app>.</span></span>

> [!NOTE]
> <span data-ttu-id="36f1f-230">.NET Core çalışma zamanı, biçimde izleme oluşturur `nettrace` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-230">The .NET Core runtime generates traces in the `nettrace` format.</span></span> <span data-ttu-id="36f1f-231">İzlemeler, izleme tamamlandıktan sonra speedscope (belirtilmişse) olarak dönüştürülür.</span><span class="sxs-lookup"><span data-stu-id="36f1f-231">The traces are converted to speedscope (if specified) after the trace is completed.</span></span> <span data-ttu-id="36f1f-232">Bazı dönüştürmeler veri kaybına neden olabileceğinden, özgün `nettrace` Dosya Dönüştürülen dosyanın yanında korunur.</span><span class="sxs-lookup"><span data-stu-id="36f1f-232">Since some conversions may result in loss of data, the original `nettrace` file is preserved next to the converted file.</span></span>

## <a name="use-dotnet-trace-to-collect-counter-values-over-time"></a><span data-ttu-id="36f1f-233">Zaman içinde sayaç değerlerini toplamak için DotNet-Trace kullanın</span><span class="sxs-lookup"><span data-stu-id="36f1f-233">Use dotnet-trace to collect counter values over time</span></span>

<span data-ttu-id="36f1f-234">`dotnet-trace` erişebilirsiniz</span><span class="sxs-lookup"><span data-stu-id="36f1f-234">`dotnet-trace` can:</span></span>

* <span data-ttu-id="36f1f-235">`EventCounter`Performans duyarlı ortamlarda temel sistem durumu izleme için kullanın.</span><span class="sxs-lookup"><span data-stu-id="36f1f-235">Use `EventCounter` for basic health monitoring in performance-sensitive environments.</span></span> <span data-ttu-id="36f1f-236">Örneğin, üretimde.</span><span class="sxs-lookup"><span data-stu-id="36f1f-236">For example, in production.</span></span>
* <span data-ttu-id="36f1f-237">İzlemeleri toplayın, böylece gerçek zamanlı olarak görüntülenmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="36f1f-237">Collect traces so they don't need to be viewed in real time.</span></span>

<span data-ttu-id="36f1f-238">Örneğin, çalışma zamanı performans sayacı değerlerini toplamak için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="36f1f-238">For example, to collect runtime performance counter values, use the following command:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

<span data-ttu-id="36f1f-239">Yukarıdaki komut, hafif sistem durumu izleme için çalışma zamanı sayaçlarına her saniye bir kez rapor vermesini söyler.</span><span class="sxs-lookup"><span data-stu-id="36f1f-239">The preceding command tells the runtime counters to report once every second for lightweight health monitoring.</span></span> <span data-ttu-id="36f1f-240">`EventCounterIntervalSec=1`Daha yüksek bir değerle değiştirme (örneğin, 60) sayaç verilerinde daha az ayrıntı düzeyi olan daha küçük bir izlemenin toplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="36f1f-240">Replacing `EventCounterIntervalSec=1` with a higher value (for example, 60) allows collection of a smaller trace with less granularity in the counter data.</span></span>

<span data-ttu-id="36f1f-241">Aşağıdaki komut ek yükü ve izleme boyutunu önceki olandan daha fazla azaltır:</span><span class="sxs-lookup"><span data-stu-id="36f1f-241">The following command reduces overhead and trace size more than the preceding one:</span></span>

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

<span data-ttu-id="36f1f-242">Yukarıdaki komut, çalışma zamanı olaylarını ve yönetilen yığın profil oluşturucuyu devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="36f1f-242">The preceding command disables runtime events and the managed stack profiler.</span></span>

## <a name="use-rsp-file-to-avoid-typing-long-commands"></a><span data-ttu-id="36f1f-243">Uzun komutların yazımasını önlemek için. rsp dosyasını kullanın</span><span class="sxs-lookup"><span data-stu-id="36f1f-243">Use .rsp file to avoid typing long commands</span></span>

<span data-ttu-id="36f1f-244">`dotnet-trace` `.rsp` Geçirilecek bağımsız değişkenleri içeren bir dosyayla başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36f1f-244">You can launch `dotnet-trace` with an `.rsp` file that contains the arguments to pass.</span></span> <span data-ttu-id="36f1f-245">Bu, uzun bağımsız değişkenler bekleyen veya karakter şeritleri kullanan bir kabuk ortamını kullanırken yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-245">This can be useful when enabling providers that expect lengthy arguments or when using a shell environment that strips characters.</span></span>

<span data-ttu-id="36f1f-246">Örneğin, aşağıdaki sağlayıcı, izlemek istediğiniz her seferinde yazmamasız bir şekilde olabilir:</span><span class="sxs-lookup"><span data-stu-id="36f1f-246">For example, the following provider can be cumbersome to type out each time you want to trace:</span></span>

```cmd
dotnet-trace collect --providers Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="36f1f-247">Ayrıca, önceki örnek `"` bağımsız değişkenin bir parçası olarak içerir.</span><span class="sxs-lookup"><span data-stu-id="36f1f-247">In addition, the previous example contains `"` as part of the argument.</span></span> <span data-ttu-id="36f1f-248">Teklifler her kabukta eşit olarak işlenmediğinden, farklı kabuklar kullanırken çeşitli sorunlarla karşılaşabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="36f1f-248">Because quotes are not handled equally by each shell, you may experience various issues when using different shells.</span></span> <span data-ttu-id="36f1f-249">Örneğin, içine girilecek komut `zsh` içindeki komutuna farklıdır `cmd` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-249">For example, the command to enter in `zsh` is different to the command in `cmd`.</span></span>

<span data-ttu-id="36f1f-250">Bu her seferinde yazmak yerine, aşağıdaki metni adlı bir dosyaya kaydedebilirsiniz `myprofile.rsp` .</span><span class="sxs-lookup"><span data-stu-id="36f1f-250">Instead of typing this each time, you can save the following text into a file called `myprofile.rsp`.</span></span>

```txt
--providers
Microsoft-Diagnostics-DiagnosticSource:0x3:5:FilterAndPayloadSpecs="SqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandBefore@Activity1Start:-Command;Command.CommandText;ConnectionId;Operation;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nSqlClientDiagnosticListener/System.Data.SqlClient.WriteCommandAfter@Activity1Stop:\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuting@Activity2Start:-Command;Command.CommandText;ConnectionId;IsAsync;Command.Connection.ClientConnectionId;Command.Connection.ServerVersion;Command.CommandTimeout;Command.CommandType;Command.Connection.ConnectionString;Command.Connection.Database;Command.Connection.DataSource;Command.Connection.PacketSize\r\nMicrosoft.EntityFrameworkCore/Microsoft.EntityFrameworkCore.Database.Command.CommandExecuted@Activity2Stop:",OtherProvider,AnotherProvider
```

<span data-ttu-id="36f1f-251">Kaydettikten sonra `myprofile.rsp` , `dotnet-trace` aşağıdaki komutu kullanarak bu yapılandırmayla başlatabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="36f1f-251">Once you've saved `myprofile.rsp`, you can launch `dotnet-trace` with this configuration using the following command:</span></span>

```bash
dotnet-trace @myprofile.rsp
```

## <a name="see-also"></a><span data-ttu-id="36f1f-252">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36f1f-252">See also</span></span>

- [<span data-ttu-id="36f1f-253">.NET 'ten tanınmış olay sağlayıcıları</span><span class="sxs-lookup"><span data-stu-id="36f1f-253">Well-known event providers from .NET</span></span>](well-known-event-providers.md)
