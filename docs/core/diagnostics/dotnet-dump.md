---
title: DotNet-döküm Tanılama aracı-.NET CLı
description: Yerel hata ayıklayıcı olmadan Windows ve Linux dökümlerinin toplanması ve çözümlenmesi için DotNet-dump CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 84b3796f4ee92880e6d432df606a6addfd2471b0
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189810"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="d361a-103">Döküm toplama ve çözümleme yardımcı programı (DotNet-dump)</span><span class="sxs-lookup"><span data-stu-id="d361a-103">Dump collection and analysis utility (dotnet-dump)</span></span>

<span data-ttu-id="d361a-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="d361a-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="d361a-105">`dotnet-dump` macOS için yalnızca .NET 5,0 ve üzeri sürümlerde desteklenir.</span><span class="sxs-lookup"><span data-stu-id="d361a-105">`dotnet-dump` for macOS is only supported with .NET 5.0 and later versions.</span></span>

## <a name="install"></a><span data-ttu-id="d361a-106">Yükleme</span><span class="sxs-lookup"><span data-stu-id="d361a-106">Install</span></span>

<span data-ttu-id="d361a-107">İndirmek ve yüklemek için iki yol vardır `dotnet-dump` :</span><span class="sxs-lookup"><span data-stu-id="d361a-107">There are two ways to download and install `dotnet-dump`:</span></span>

- <span data-ttu-id="d361a-108">**DotNet genel aracı:**</span><span class="sxs-lookup"><span data-stu-id="d361a-108">**dotnet global tool:**</span></span>

  <span data-ttu-id="d361a-109">NuGet paketinin en son sürümünü yüklemek için `dotnet-dump` [](https://www.nuget.org/packages/dotnet-dump) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="d361a-109">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-dump
  ```

- <span data-ttu-id="d361a-110">**Doğrudan indirme:**</span><span class="sxs-lookup"><span data-stu-id="d361a-110">**Direct download:**</span></span>

  <span data-ttu-id="d361a-111">Platformunuzla eşleşen araç yürütülebilirini indirin:</span><span class="sxs-lookup"><span data-stu-id="d361a-111">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="d361a-112">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="d361a-112">OS</span></span>  | <span data-ttu-id="d361a-113">Platform</span><span class="sxs-lookup"><span data-stu-id="d361a-113">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="d361a-114">Windows</span><span class="sxs-lookup"><span data-stu-id="d361a-114">Windows</span></span> | <span data-ttu-id="d361a-115">[x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [ARM](https://aka.ms/dotnet-dump/win-arm) \| [ARM-x64](https://aka.ms/dotnet-dump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="d361a-115">[x86](https://aka.ms/dotnet-dump/win-x86) \| [x64](https://aka.ms/dotnet-dump/win-x64) \| [arm](https://aka.ms/dotnet-dump/win-arm) \| [arm-x64](https://aka.ms/dotnet-dump/win-arm64)</span></span> |
  | <span data-ttu-id="d361a-116">Mac OS</span><span class="sxs-lookup"><span data-stu-id="d361a-116">macOS</span></span>   | [<span data-ttu-id="d361a-117">x64</span><span class="sxs-lookup"><span data-stu-id="d361a-117">x64</span></span>](https://aka.ms/dotnet-dump/osx-x64) |
  | <span data-ttu-id="d361a-118">Linux</span><span class="sxs-lookup"><span data-stu-id="d361a-118">Linux</span></span>   | <span data-ttu-id="d361a-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \| [ARM](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="d361a-119">[x64](https://aka.ms/dotnet-dump/linux-x64) \| [arm](https://aka.ms/dotnet-dump/linux-arm) \| [arm64](https://aka.ms/dotnet-dump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-dump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-dump/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="d361a-120">`dotnet-dump`X86 uygulamasında kullanmak için, aracın karşılık gelen x86 sürümüne ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="d361a-120">To use `dotnet-dump` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d361a-121">Özeti</span><span class="sxs-lookup"><span data-stu-id="d361a-121">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="d361a-122">Description</span><span class="sxs-lookup"><span data-stu-id="d361a-122">Description</span></span>

<span data-ttu-id="d361a-123">`dotnet-dump`Genel araç, Linux üzerinde yer alan herhangi bir yerel hata ayıklayıcı olmadan Windows ve Linux dökümlerinin toplanması ve çözümlenmesi için bir yoldur `lldb` .</span><span class="sxs-lookup"><span data-stu-id="d361a-123">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="d361a-124">Bu araç alp Linux gibi tam olarak çalışan `lldb` kullanılabilir olmayan platformlarda önemlidir.</span><span class="sxs-lookup"><span data-stu-id="d361a-124">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="d361a-125">`dotnet-dump`Araç, çökmeleri ve çöp toplayıcıyı (GC) çözümlemek IÇIN sos komutları çalıştırmanızı sağlar, ancak yerel yığın çerçevelerini görüntüleme gibi şeyler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="d361a-125">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="d361a-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d361a-126">Options</span></span>

- **`--version`**

  <span data-ttu-id="d361a-127">DotNet-dump yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-127">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d361a-128">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d361a-128">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="d361a-129">Komutlar</span><span class="sxs-lookup"><span data-stu-id="d361a-129">Commands</span></span>

| <span data-ttu-id="d361a-130">Komut</span><span class="sxs-lookup"><span data-stu-id="d361a-130">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="d361a-131">DotNet-döküm toplama</span><span class="sxs-lookup"><span data-stu-id="d361a-131">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="d361a-132">DotNet-döküm Analizi</span><span class="sxs-lookup"><span data-stu-id="d361a-132">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="d361a-133">DotNet-döküm toplama</span><span class="sxs-lookup"><span data-stu-id="d361a-133">dotnet-dump collect</span></span>

<span data-ttu-id="d361a-134">Bir işlemden döküm yakalar.</span><span class="sxs-lookup"><span data-stu-id="d361a-134">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="d361a-135">Özeti</span><span class="sxs-lookup"><span data-stu-id="d361a-135">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [-n|--name] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="d361a-136">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d361a-136">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="d361a-137">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d361a-137">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="d361a-138">Döküm toplanacak işlem KIMLIĞI sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d361a-138">Specifies the process ID number to collect a dump from.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="d361a-139">Döküm toplanacak işlemin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d361a-139">Specifies the name of the process to collect a dump from.</span></span>

- **`--type <Full|Heap|Mini>`**

  <span data-ttu-id="d361a-140">İşlemden toplanan bilgi türlerini belirleyen döküm türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="d361a-140">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="d361a-141">Üç tür vardır:</span><span class="sxs-lookup"><span data-stu-id="d361a-141">There are three types:</span></span>

  - <span data-ttu-id="d361a-142">`Full` -Modül görüntüleri dahil olmak üzere tüm belleği içeren en büyük döküm.</span><span class="sxs-lookup"><span data-stu-id="d361a-142">`Full` - The largest dump containing all memory including the module images.</span></span>
  - <span data-ttu-id="d361a-143">`Heap` -Modül listelerini, iş parçacığı listelerini, tüm yığınları, özel durum bilgilerini, tanıtıcı bilgilerini ve eşlenmiş görüntüler hariç tüm belleği içeren büyük ve görece kapsamlı bir döküm.</span><span class="sxs-lookup"><span data-stu-id="d361a-143">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="d361a-144">`Mini` -Modül listelerini, iş parçacığı listelerini, özel durum bilgilerini ve tüm yığınları içeren küçük bir döküm.</span><span class="sxs-lookup"><span data-stu-id="d361a-144">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="d361a-145">Belirtilmemişse, `Full` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="d361a-145">If not specified, `Full` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="d361a-146">Toplanan dökümün yazılması gereken tam yol ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="d361a-146">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="d361a-147">Belirtilmezse:</span><span class="sxs-lookup"><span data-stu-id="d361a-147">If not specified:</span></span>

  - <span data-ttu-id="d361a-148">Varsayılan olarak *. \ dump_YYYYMMDD_HHMMSS. dmp* Windows üzerinde.</span><span class="sxs-lookup"><span data-stu-id="d361a-148">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="d361a-149">Linux üzerinde varsayılan olarak *./core_YYYYMMDD_HHMMSS* .</span><span class="sxs-lookup"><span data-stu-id="d361a-149">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="d361a-150">YYYYMMDD yıl/ay/gün ve SSMMSS saat/dakika/saniye şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="d361a-150">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="d361a-151">Döküm toplama tanılama günlüğünü etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="d361a-151">Enables dump collection diagnostic logging.</span></span>

> [!NOTE]
> <span data-ttu-id="d361a-152">Linux ve macOS 'ta, bu komut hedef uygulamayı bekler ve `dotnet-dump` aynı `TMPDIR` ortam değişkenini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="d361a-152">On Linux and macOS, this command expects the target application and `dotnet-dump` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="d361a-153">Aksi takdirde, komut zaman aşımına uğrar.</span><span class="sxs-lookup"><span data-stu-id="d361a-153">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="d361a-154">Kullanarak bir döküm toplamak için `dotnet-dump` , hedef işlem ya da kök olarak çalışan kullanıcı ile aynı kullanıcı olarak çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="d361a-154">To collect a dump using `dotnet-dump`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="d361a-155">Aksi halde araç, hedef işlemle bağlantı kurmayacak.</span><span class="sxs-lookup"><span data-stu-id="d361a-155">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="d361a-156">DotNet-döküm Analizi</span><span class="sxs-lookup"><span data-stu-id="d361a-156">dotnet-dump analyze</span></span>

<span data-ttu-id="d361a-157">Bir dökümü araştırmak için etkileşimli bir kabuk başlatır.</span><span class="sxs-lookup"><span data-stu-id="d361a-157">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="d361a-158">Kabuk çeşitli [sos komutlarını](#analyze-sos-commands)kabul eder.</span><span class="sxs-lookup"><span data-stu-id="d361a-158">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="d361a-159">Özeti</span><span class="sxs-lookup"><span data-stu-id="d361a-159">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="d361a-160">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="d361a-160">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="d361a-161">Analiz edilecek döküm dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="d361a-161">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="d361a-162">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d361a-162">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="d361a-163">Başlatma sırasında kabukta çalıştırılacak [komutu](#analyze-sos-commands) belirtir.</span><span class="sxs-lookup"><span data-stu-id="d361a-163">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="d361a-164">SOS komutlarını çözümle</span><span class="sxs-lookup"><span data-stu-id="d361a-164">Analyze SOS commands</span></span>

| <span data-ttu-id="d361a-165">Komut</span><span class="sxs-lookup"><span data-stu-id="d361a-165">Command</span></span>                             | <span data-ttu-id="d361a-166">İşlev</span><span class="sxs-lookup"><span data-stu-id="d361a-166">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="d361a-167">Tüm kullanılabilir komutları görüntüler</span><span class="sxs-lookup"><span data-stu-id="d361a-167">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="d361a-168">Belirtilen komutu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-168">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="d361a-169">Etkileşimli moddan çıkar.</span><span class="sxs-lookup"><span data-stu-id="d361a-169">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="d361a-170">Yalnızca bir yönetilen kodların bir yığın izlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d361a-170">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="d361a-171">Çalıştıran yönetilen iş parçacıklarını listeler.</span><span class="sxs-lookup"><span data-stu-id="d361a-171">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="d361a-172">Atık toplanan yığında zaman uyumsuz durum makineleri hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-172">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="d361a-173">Belirtilen adresteki derleme hakkındaki ayrıntıları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-173">Displays details about the assembly at the specified address.</span></span>                                 |
| `dumpclass <arguments>`             | <span data-ttu-id="d361a-174">`EEClass`Belirtilen adresteki yapıyla ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-174">Displays information about the `EEClass` structure at the specified address.</span></span>                  |
| `dumpdelegate <arguments>`          | <span data-ttu-id="d361a-175">Belirtilen adresteki temsilciyle ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-175">Displays information about the delegate at the specified address.</span></span>                             |
| `dumpdomain <arguments>`            | <span data-ttu-id="d361a-176">Tüm AppDomain 'ler ve belirtilen etki alanı içindeki tüm derlemeler için bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-176">Displays information all the AppDomains and all assemblies within the specified domain.</span></span>       |
| `dumpheap <arguments>`              | <span data-ttu-id="d361a-177">Çöp toplanmış yığın ve nesneler hakkında koleksiyon istatistikleri hakkında bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-177">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="d361a-178">Yönetilen bir yöntemle ilişkili Microsoft ara dilini (MSIL) görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-178">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="d361a-179">Bir bellek içi yük günlüğünün içeriğini belirtilen dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="d361a-179">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="d361a-180">`MethodDesc`Belirtilen adresteki yapıyla ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-180">Displays information about the `MethodDesc` structure at the specified address.</span></span>               |
| `dumpmodule <arguments>`            | <span data-ttu-id="d361a-181">Belirtilen adresteki modülle ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-181">Displays information about the module at the specified address.</span></span>                               |
| `dumpmt <arguments>`                | <span data-ttu-id="d361a-182">Belirtilen adresteki hakkında bilgileri görüntüler `MethodTable` .</span><span class="sxs-lookup"><span data-stu-id="d361a-182">Displays information about the `MethodTable` at the specified address.</span></span>                        |
| `dumpobj <arguments>`               | <span data-ttu-id="d361a-183">Belirtilen adresteki nesne hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-183">Displays info about the object at the specified address.</span></span>                                      |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="d361a-184">Geçerli yığının sınırları içinde bulunan tüm yönetilen nesneleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-184">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="d361a-185">İç çalışma zamanı veri yapıları tarafından tüketilen işlem belleği hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-185">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="d361a-186">Sonlandırma için kaydolan tüm nesneleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-186">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="d361a-187">Belirtilen adresteki nesnenin başvuruları (veya kökleri) hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-187">Displays info about references (or roots) to the object at the specified address.</span></span>             |
| `gcwhere <arguments>`               | <span data-ttu-id="d361a-188">Geçirilen bağımsız değişkenin GC yığınındaki konumu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-188">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="d361a-189">`MethodDesc`Belirtilen adresteki YAPıYı JIT kodunda görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-189">Displays the `MethodDesc` structure at the specified address in JIT code.</span></span>                     |
| `histclear <arguments>`             | <span data-ttu-id="d361a-190">Komut ailesi tarafından kullanılan tüm kaynakları serbest bırakır `hist*` .</span><span class="sxs-lookup"><span data-stu-id="d361a-190">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="d361a-191">Hatası ayıklanana kaydedilen yük günlüğünden SOS yapılarını başlatır.</span><span class="sxs-lookup"><span data-stu-id="d361a-191">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="d361a-192">İle ilgili çöp toplama stres günlüğü yeniden konumlarını görüntüler `<arguments>` .</span><span class="sxs-lookup"><span data-stu-id="d361a-192">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="d361a-193">Belirtilen adresteki nesneye başvuran tüm günlük girişlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-193">Displays all the log entries that reference the object at the specified address.</span></span>              |
| `histroot <arguments>`              | <span data-ttu-id="d361a-194">Belirtilen kökün tanıtımlarıyla ve yeniden konumlandırılmalarıyla ilişkili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-194">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="d361a-195">İşlemdeki yerel modülleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-195">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="d361a-196">`MethodTable` `EEClass` İçin ve yapılarını görüntüler `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="d361a-196">Displays the `MethodTable` and `EEClass` structures for the `<argument>`.</span></span>                     |
| `pe|printexception <arguments>`     | <span data-ttu-id="d361a-197">Sınıfından türetilmiş tüm nesneleri görüntüler <xref:System.Exception> `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="d361a-197">Displays any object derived from the <xref:System.Exception> class for the `<argument>`.</span></span>      |
| `setsymbolserver <arguments>`       | <span data-ttu-id="d361a-198">Sembol sunucusu desteğini sunar</span><span class="sxs-lookup"><span data-stu-id="d361a-198">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="d361a-199">SyncBlock tutucusu bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-199">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="d361a-200">SOS komutlarının geçerli iş parçacığı KIMLIĞINI ayarlar veya görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d361a-200">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

> [!NOTE]
> <span data-ttu-id="d361a-201">Ek ayrıntılar, [.net Için sos hata ayıklama uzantısında](sos-debugging-extension.md)bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="d361a-201">Additional details can be found in [SOS Debugging Extension for .NET](sos-debugging-extension.md).</span></span>

## <a name="using-dotnet-dump"></a><span data-ttu-id="d361a-202">`dotnet-dump` kullanma</span><span class="sxs-lookup"><span data-stu-id="d361a-202">Using `dotnet-dump`</span></span>

<span data-ttu-id="d361a-203">İlk adım bir döküm toplamaktır.</span><span class="sxs-lookup"><span data-stu-id="d361a-203">The first step is to collect a dump.</span></span> <span data-ttu-id="d361a-204">Bir temel döküm oluşturulmuşsa bu adım atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d361a-204">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="d361a-205">İşletim sistemi veya .NET Core çalışma zamanının yerleşik [döküm oluşturma özelliği](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) , her biri çekirdek dökümler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="d361a-205">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="d361a-206">Şimdi çekirdek dökümünü şu `analyze` komutla çözümleyin:</span><span class="sxs-lookup"><span data-stu-id="d361a-206">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="d361a-207">Bu eylem, şunun gibi komutları kabul eden etkileşimli bir oturum getirir:</span><span class="sxs-lookup"><span data-stu-id="d361a-207">This action brings up an interactive session that accepts commands like:</span></span>

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

<span data-ttu-id="d361a-208">Uygulamanızı sonlandıran işlenmeyen bir özel durumu görmek için:</span><span class="sxs-lookup"><span data-stu-id="d361a-208">To see an unhandled exception that killed your app:</span></span>

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a><span data-ttu-id="d361a-209">Docker için özel yönergeler</span><span class="sxs-lookup"><span data-stu-id="d361a-209">Special instructions for Docker</span></span>

<span data-ttu-id="d361a-210">Docker altında çalışıyorsanız, döküm toplama `SYS_PTRACE` Özelliği ( `--cap-add=SYS_PTRACE` veya `--privileged` ) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="d361a-210">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="d361a-211">Microsoft .NET Core SDK Linux Docker görüntülerinde bazı `dotnet-dump` Komutlar aşağıdaki özel durumu oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="d361a-211">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="d361a-212">İşlenmeyen özel durum: System.DllNotFoundException: paylaşılan ' libdl.so ' kitaplığı veya bağımlılıklarından biri ' özel durumu yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="d361a-212">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="d361a-213">Bu sorunu geçici olarak çözmek için "libc6-dev" paketini yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="d361a-213">To work around this problem, install the "libc6-dev" package.</span></span>

## <a name="see-also"></a><span data-ttu-id="d361a-214">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d361a-214">See also</span></span>

- [<span data-ttu-id="d361a-215">Bellek dökümlerinin toplanması ve çözümlenmesi</span><span class="sxs-lookup"><span data-stu-id="d361a-215">Collecting and analyzing memory dumps blog</span></span>](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [<span data-ttu-id="d361a-216">Yığın Analizi Aracı (DotNet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="d361a-216">Heap analysis tool (dotnet-gcdump)</span></span>](dotnet-gcdump.md)
