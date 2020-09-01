---
title: DotNet-dump-.NET Core
description: DotNet-dump komut satırı aracını yükleme ve kullanma.
ms.date: 10/14/2019
ms.openlocfilehash: 5489011538a4a11d60b333f0230a718c88722c97
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140938"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a><span data-ttu-id="43e59-103">Döküm toplama ve çözümleme yardımcı programı (DotNet-dump)</span><span class="sxs-lookup"><span data-stu-id="43e59-103">Dump collection and analysis utility (dotnet-dump)</span></span>

<span data-ttu-id="43e59-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="43e59-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

> [!NOTE]
> <span data-ttu-id="43e59-105">`dotnet-dump` macOS 'ta desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="43e59-105">`dotnet-dump` isn't supported on macOS.</span></span>

## <a name="install-dotnet-dump"></a><span data-ttu-id="43e59-106">DotNet 'yi yükler-döküm</span><span class="sxs-lookup"><span data-stu-id="43e59-106">Install dotnet-dump</span></span>

<span data-ttu-id="43e59-107">NuGet paketinin en son sürümünü yüklemek için `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="43e59-107">To install the latest release version of the `dotnet-dump` [NuGet package](https://www.nuget.org/packages/dotnet-dump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a><span data-ttu-id="43e59-108">Özeti</span><span class="sxs-lookup"><span data-stu-id="43e59-108">Synopsis</span></span>

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="43e59-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43e59-109">Description</span></span>

<span data-ttu-id="43e59-110">`dotnet-dump`Genel araç, Linux üzerinde yer alan herhangi bir yerel hata ayıklayıcı olmadan Windows ve Linux dökümlerinin toplanması ve çözümlenmesi için bir yoldur `lldb` .</span><span class="sxs-lookup"><span data-stu-id="43e59-110">The `dotnet-dump` global tool is a way to collect and analyze Windows and Linux dumps without any native debugger involved like `lldb` on Linux.</span></span> <span data-ttu-id="43e59-111">Bu araç alp Linux gibi tam olarak çalışan `lldb` kullanılabilir olmayan platformlarda önemlidir.</span><span class="sxs-lookup"><span data-stu-id="43e59-111">This tool is important on platforms like Alpine Linux where a fully working `lldb` isn't available.</span></span> <span data-ttu-id="43e59-112">`dotnet-dump`Araç, çökmeleri ve çöp toplayıcıyı (GC) çözümlemek IÇIN sos komutları çalıştırmanızı sağlar, ancak yerel yığın çerçevelerini görüntüleme gibi şeyler desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="43e59-112">The `dotnet-dump` tool allows you to run SOS commands to analyze crashes and the garbage collector (GC), but it isn't a native debugger so things like displaying native stack frames aren't supported.</span></span>

## <a name="options"></a><span data-ttu-id="43e59-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="43e59-113">Options</span></span>

- **`--version`**

  <span data-ttu-id="43e59-114">DotNet-dump yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-114">Displays the version of the dotnet-dump utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="43e59-115">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="43e59-115">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="43e59-116">Komutlar</span><span class="sxs-lookup"><span data-stu-id="43e59-116">Commands</span></span>

| <span data-ttu-id="43e59-117">Komut</span><span class="sxs-lookup"><span data-stu-id="43e59-117">Command</span></span>                                     |
| ------------------------------------------- |
| [<span data-ttu-id="43e59-118">DotNet-döküm toplama</span><span class="sxs-lookup"><span data-stu-id="43e59-118">dotnet-dump collect</span></span>](#dotnet-dump-collect) |
| [<span data-ttu-id="43e59-119">DotNet-döküm Analizi</span><span class="sxs-lookup"><span data-stu-id="43e59-119">dotnet-dump analyze</span></span>](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a><span data-ttu-id="43e59-120">DotNet-döküm toplama</span><span class="sxs-lookup"><span data-stu-id="43e59-120">dotnet-dump collect</span></span>

<span data-ttu-id="43e59-121">Bir işlemden döküm yakalar.</span><span class="sxs-lookup"><span data-stu-id="43e59-121">Captures a dump from a process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="43e59-122">Özeti</span><span class="sxs-lookup"><span data-stu-id="43e59-122">Synopsis</span></span>

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a><span data-ttu-id="43e59-123">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="43e59-123">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="43e59-124">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="43e59-124">Shows command-line help.</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="43e59-125">Kaynağından bir bellek dökümü toplanacak işlem KIMLIĞI sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="43e59-125">Specifies the process ID number to collect a memory dump from.</span></span>

- **`--type <Heap|Mini>`**

  <span data-ttu-id="43e59-126">İşlemden toplanan bilgi türlerini belirleyen döküm türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="43e59-126">Specifies the dump type, which determines the kinds of information that are collected from the process.</span></span> <span data-ttu-id="43e59-127">İki tür vardır:</span><span class="sxs-lookup"><span data-stu-id="43e59-127">There are two types:</span></span>

  - <span data-ttu-id="43e59-128">`Heap` -Modül listelerini, iş parçacığı listelerini, tüm yığınları, özel durum bilgilerini, tanıtıcı bilgilerini ve eşlenmiş görüntüler hariç tüm belleği içeren büyük ve görece kapsamlı bir döküm.</span><span class="sxs-lookup"><span data-stu-id="43e59-128">`Heap` - A large and relatively comprehensive dump containing module lists, thread lists, all stacks, exception information, handle information, and all memory except for mapped images.</span></span>
  - <span data-ttu-id="43e59-129">`Mini` -Modül listelerini, iş parçacığı listelerini, özel durum bilgilerini ve tüm yığınları içeren küçük bir döküm.</span><span class="sxs-lookup"><span data-stu-id="43e59-129">`Mini` - A small dump containing module lists, thread lists, exception information, and all stacks.</span></span>

  <span data-ttu-id="43e59-130">Belirtilmemişse, `Heap` varsayılandır.</span><span class="sxs-lookup"><span data-stu-id="43e59-130">If not specified, `Heap` is the default.</span></span>

- **`-o|--output <output_dump_path>`**

  <span data-ttu-id="43e59-131">Toplanan dökümün yazılması gereken tam yol ve dosya adı.</span><span class="sxs-lookup"><span data-stu-id="43e59-131">The full path and file name where the collected dump should be written.</span></span>

  <span data-ttu-id="43e59-132">Belirtilmezse:</span><span class="sxs-lookup"><span data-stu-id="43e59-132">If not specified:</span></span>

  - <span data-ttu-id="43e59-133">Varsayılan olarak *. \ dump_YYYYMMDD_HHMMSS. dmp* Windows üzerinde.</span><span class="sxs-lookup"><span data-stu-id="43e59-133">Defaults to *.\dump_YYYYMMDD_HHMMSS.dmp* on Windows.</span></span>
  - <span data-ttu-id="43e59-134">Linux üzerinde varsayılan olarak *./core_YYYYMMDD_HHMMSS* .</span><span class="sxs-lookup"><span data-stu-id="43e59-134">Defaults to *./core_YYYYMMDD_HHMMSS* on Linux.</span></span>

  <span data-ttu-id="43e59-135">YYYYMMDD yıl/ay/gün ve SSMMSS saat/dakika/saniye şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="43e59-135">YYYYMMDD is Year/Month/Day and HHMMSS is Hour/Minute/Second.</span></span>

- **`--diag`**

  <span data-ttu-id="43e59-136">Döküm toplama tanılama günlüğünü etkinleştir.</span><span class="sxs-lookup"><span data-stu-id="43e59-136">Enables dump collection diagnostic logging.</span></span>

## <a name="dotnet-dump-analyze"></a><span data-ttu-id="43e59-137">DotNet-döküm Analizi</span><span class="sxs-lookup"><span data-stu-id="43e59-137">dotnet-dump analyze</span></span>

<span data-ttu-id="43e59-138">Bir dökümü araştırmak için etkileşimli bir kabuk başlatır.</span><span class="sxs-lookup"><span data-stu-id="43e59-138">Starts an interactive shell to explore a dump.</span></span> <span data-ttu-id="43e59-139">Kabuk çeşitli [sos komutlarını](#analyze-sos-commands)kabul eder.</span><span class="sxs-lookup"><span data-stu-id="43e59-139">The shell accepts various [SOS commands](#analyze-sos-commands).</span></span>

### <a name="synopsis"></a><span data-ttu-id="43e59-140">Özeti</span><span class="sxs-lookup"><span data-stu-id="43e59-140">Synopsis</span></span>

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a><span data-ttu-id="43e59-141">Arguments</span><span class="sxs-lookup"><span data-stu-id="43e59-141">Arguments</span></span>

- **`<dump_path>`**

  <span data-ttu-id="43e59-142">Analiz edilecek döküm dosyasının yolunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="43e59-142">Specifies the path to the dump file to analyze.</span></span>

### <a name="options"></a><span data-ttu-id="43e59-143">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="43e59-143">Options</span></span>

- **`-c|--command <debug_command>`**

  <span data-ttu-id="43e59-144">Başlatma sırasında kabukta çalıştırılacak [komutu](#analyze-sos-commands) belirtir.</span><span class="sxs-lookup"><span data-stu-id="43e59-144">Specifies the [command](#analyze-sos-commands) to run in the shell on start.</span></span>

### <a name="analyze-sos-commands"></a><span data-ttu-id="43e59-145">SOS komutlarını çözümle</span><span class="sxs-lookup"><span data-stu-id="43e59-145">Analyze SOS commands</span></span>

| <span data-ttu-id="43e59-146">Komut</span><span class="sxs-lookup"><span data-stu-id="43e59-146">Command</span></span>                             | <span data-ttu-id="43e59-147">İşlev</span><span class="sxs-lookup"><span data-stu-id="43e59-147">Function</span></span>                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | <span data-ttu-id="43e59-148">Tüm kullanılabilir komutları görüntüler</span><span class="sxs-lookup"><span data-stu-id="43e59-148">Displays all available commands</span></span>                                                               |
| `soshelp|help <command>`            | <span data-ttu-id="43e59-149">Belirtilen komutu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-149">Displays the specified command.</span></span>                                                               |
| `exit|quit`                         | <span data-ttu-id="43e59-150">Etkileşimli moddan çıkar.</span><span class="sxs-lookup"><span data-stu-id="43e59-150">Exits interactive mode.</span></span>                                                                       |
| `clrstack <arguments>`              | <span data-ttu-id="43e59-151">Yalnızca bir yönetilen kodların bir yığın izlemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="43e59-151">Provides a stack trace of managed code only.</span></span>                                                  |
| `clrthreads <arguments>`            | <span data-ttu-id="43e59-152">Çalıştıran yönetilen iş parçacıklarını listeler.</span><span class="sxs-lookup"><span data-stu-id="43e59-152">Lists the managed threads running.</span></span>                                                            |
| `dumpasync <arguments>`             | <span data-ttu-id="43e59-153">Atık toplanan yığında zaman uyumsuz durum makineleri hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-153">Displays information about async state machines on the garbage-collected heap.</span></span>                |
| `dumpassembly <arguments>`          | <span data-ttu-id="43e59-154">Bir derleme hakkındaki ayrıntıları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-154">Displays details about an assembly.</span></span>                                                           |
| `dumpclass <arguments>`             | <span data-ttu-id="43e59-155">Belirtilen adresteki bir EE sınıfı yapısı hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-155">Displays information about a EE class structure at the specified address.</span></span>                     |
| `dumpdelegate <arguments>`          | <span data-ttu-id="43e59-156">Bir temsilciyle ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-156">Displays information about a delegate.</span></span>                                                        |
| `dumpdomain <arguments>`            | <span data-ttu-id="43e59-157">Tüm AppDomain ve etki alanları içindeki tüm derlemelerin bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-157">Displays information all the AppDomains and all assemblies within the domains.</span></span>                |
| `dumpheap <arguments>`              | <span data-ttu-id="43e59-158">Çöp toplanmış yığın ve nesneler hakkında koleksiyon istatistikleri hakkında bilgi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-158">Displays info about the garbage-collected heap and collection statistics about objects.</span></span>       |
| `dumpil <arguments>`                | <span data-ttu-id="43e59-159">Yönetilen bir yöntemle ilişkili Microsoft ara dilini (MSIL) görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-159">Displays the Microsoft intermediate language (MSIL) that is associated with a managed method.</span></span> |
| `dumplog <arguments>`               | <span data-ttu-id="43e59-160">Bir bellek içi yük günlüğünün içeriğini belirtilen dosyaya yazar.</span><span class="sxs-lookup"><span data-stu-id="43e59-160">Writes the contents of an in-memory stress log to the specified file.</span></span>                         |
| `dumpmd <arguments>`                | <span data-ttu-id="43e59-161">Belirtilen adresteki bir MethodDesc yapısıyla ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-161">Displays information about a MethodDesc structure at the specified address.</span></span>                   |
| `dumpmodule <arguments>`            | <span data-ttu-id="43e59-162">Belirtilen adresteki bir EE modül yapısıyla ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-162">Displays information about a EE module structure at the specified address.</span></span>                    |
| `dumpmt <arguments>`                | <span data-ttu-id="43e59-163">Belirtilen bir adresteki bir yöntem tablosuyla ilgili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-163">Displays information about a method table at the specified address.</span></span>                           |
| `dumpobj <arguments>`               | <span data-ttu-id="43e59-164">Belirtilen adresteki bir nesne hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-164">Displays info about an object at the specified address.</span></span>                                       |
| `dso|dumpstackobjects <arguments>`  | <span data-ttu-id="43e59-165">Geçerli yığının sınırları içinde bulunan tüm yönetilen nesneleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-165">Displays all managed objects found within the bounds of the current stack.</span></span>                    |
| `eeheap <arguments>`                | <span data-ttu-id="43e59-166">İç çalışma zamanı veri yapıları tarafından tüketilen işlem belleği hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-166">Displays info about process memory consumed by internal runtime data structures.</span></span>              |
| `finalizequeue <arguments>`         | <span data-ttu-id="43e59-167">Sonlandırma için kaydolan tüm nesneleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-167">Displays all objects registered for finalization.</span></span>                                             |
| `gcroot <arguments>`                | <span data-ttu-id="43e59-168">Belirtilen adresteki bir nesneye başvurular (veya köklerle) hakkındaki bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-168">Displays info about references (or roots) to an object at the specified address.</span></span>              |
| `gcwhere <arguments>`               | <span data-ttu-id="43e59-169">Geçirilen bağımsız değişkenin GC yığınındaki konumu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-169">Displays the location in the GC heap of the argument passed in.</span></span>                               |
| `ip2md <arguments>`                 | <span data-ttu-id="43e59-170">JıT kodundaki belirtilen adreste MethodDesc yapısını görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-170">Displays the MethodDesc structure at the specified address in JIT code.</span></span>                       |
| `histclear <arguments>`             | <span data-ttu-id="43e59-171">Komut ailesi tarafından kullanılan tüm kaynakları serbest bırakır `hist*` .</span><span class="sxs-lookup"><span data-stu-id="43e59-171">Releases any resources used by the family of `hist*` commands.</span></span>                                |
| `histinit <arguments>`              | <span data-ttu-id="43e59-172">Hatası ayıklanana kaydedilen yük günlüğünden SOS yapılarını başlatır.</span><span class="sxs-lookup"><span data-stu-id="43e59-172">Initializes the SOS structures from the stress log saved in the debuggee.</span></span>                     |
| `histobj <arguments>`               | <span data-ttu-id="43e59-173">İle ilgili çöp toplama stres günlüğü yeniden konumlarını görüntüler `<arguments>` .</span><span class="sxs-lookup"><span data-stu-id="43e59-173">Displays the garbage collection stress log relocations related to `<arguments>`.</span></span>              |
| `histobjfind <arguments>`           | <span data-ttu-id="43e59-174">Belirtilen adresteki bir nesneye başvuran tüm günlük girişlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-174">Displays all the log entries that reference an object at the specified address.</span></span>               |
| `histroot <arguments>`              | <span data-ttu-id="43e59-175">Belirtilen kökün tanıtımlarıyla ve yeniden konumlandırılmalarıyla ilişkili bilgileri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-175">Displays information related to both promotions and relocations of the specified root.</span></span>        |
| `lm|modules`                        | <span data-ttu-id="43e59-176">İşlemdeki yerel modülleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-176">Displays the native modules in the process.</span></span>                                                   |
| `name2ee <arguments>`               | <span data-ttu-id="43e59-177">İçin MethodTable yapısını ve EEClass yapısını görüntüler `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="43e59-177">Displays the MethodTable structure and EEClass structure for the `<argument>`.</span></span>                |
| `pe|printexception <arguments>`     | <span data-ttu-id="43e59-178">Adreste özel durum sınıfından türetilmiş tüm nesneleri görüntüler `<argument>` .</span><span class="sxs-lookup"><span data-stu-id="43e59-178">Displays any object derived from the Exception class at the address `<argument>`.</span></span>             |
| `setsymbolserver <arguments>`       | <span data-ttu-id="43e59-179">Sembol sunucusu desteğini sunar</span><span class="sxs-lookup"><span data-stu-id="43e59-179">Enables the symbol server support</span></span>                                                             |
| `syncblk <arguments>`               | <span data-ttu-id="43e59-180">SyncBlock tutucusu bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-180">Displays the SyncBlock holder info.</span></span>                                                           |
| `threads|setthread <threadid>`      | <span data-ttu-id="43e59-181">SOS komutlarının geçerli iş parçacığı KIMLIĞINI ayarlar veya görüntüler.</span><span class="sxs-lookup"><span data-stu-id="43e59-181">Sets or displays the current thread ID for the SOS commands.</span></span>                                  |

## <a name="using-dotnet-dump"></a><span data-ttu-id="43e59-182">`dotnet-dump` kullanma</span><span class="sxs-lookup"><span data-stu-id="43e59-182">Using `dotnet-dump`</span></span>

<span data-ttu-id="43e59-183">İlk adım bir döküm toplamaktır.</span><span class="sxs-lookup"><span data-stu-id="43e59-183">The first step is to collect a dump.</span></span> <span data-ttu-id="43e59-184">Bir temel döküm oluşturulmuşsa bu adım atlanabilir.</span><span class="sxs-lookup"><span data-stu-id="43e59-184">This step can be skipped if a core dump has already been generated.</span></span> <span data-ttu-id="43e59-185">İşletim sistemi veya .NET Core çalışma zamanının yerleşik [döküm oluşturma özelliği](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) , her biri çekirdek dökümler oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="43e59-185">The operating system or the .NET Core runtime's built-in [dump generation feature](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) can each create core dumps.</span></span>

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

<span data-ttu-id="43e59-186">Şimdi çekirdek dökümünü şu `analyze` komutla çözümleyin:</span><span class="sxs-lookup"><span data-stu-id="43e59-186">Now analyze the core dump with the `analyze` command:</span></span>

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

<span data-ttu-id="43e59-187">Bu eylem, şunun gibi komutları kabul eden etkileşimli bir oturum getirir:</span><span class="sxs-lookup"><span data-stu-id="43e59-187">This action brings up an interactive session that accepts commands like:</span></span>

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

<span data-ttu-id="43e59-188">Uygulamanızı sonlandıran işlenmeyen bir özel durumu görmek için:</span><span class="sxs-lookup"><span data-stu-id="43e59-188">To see an unhandled exception that killed your app:</span></span>

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

## <a name="special-instructions-for-docker"></a><span data-ttu-id="43e59-189">Docker için özel yönergeler</span><span class="sxs-lookup"><span data-stu-id="43e59-189">Special instructions for Docker</span></span>

<span data-ttu-id="43e59-190">Docker altında çalışıyorsanız, döküm toplama `SYS_PTRACE` Özelliği ( `--cap-add=SYS_PTRACE` veya `--privileged` ) gerektirir.</span><span class="sxs-lookup"><span data-stu-id="43e59-190">If you're running under Docker, dump collection requires `SYS_PTRACE` capabilities (`--cap-add=SYS_PTRACE` or `--privileged`).</span></span>

<span data-ttu-id="43e59-191">Microsoft .NET Core SDK Linux Docker görüntülerinde bazı `dotnet-dump` Komutlar aşağıdaki özel durumu oluşturabilir:</span><span class="sxs-lookup"><span data-stu-id="43e59-191">On Microsoft .NET Core SDK Linux Docker images, some `dotnet-dump` commands can throw the following exception:</span></span>

> <span data-ttu-id="43e59-192">İşlenmeyen özel durum: System.DllNotFoundException: paylaşılan ' libdl.so ' kitaplığı veya bağımlılıklarından biri ' özel durumu yüklenemiyor.</span><span class="sxs-lookup"><span data-stu-id="43e59-192">Unhandled exception: System.DllNotFoundException: Unable to load shared library 'libdl.so' or one of its dependencies' exception.</span></span>

<span data-ttu-id="43e59-193">Bu sorunu geçici olarak çözmek için "libc6-dev" paketini yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="43e59-193">To work around this problem, install the "libc6-dev" package.</span></span>

## <a name="see-also"></a><span data-ttu-id="43e59-194">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43e59-194">See also</span></span>

- [<span data-ttu-id="43e59-195">Bellek dökümlerinin toplanması ve çözümlenmesi</span><span class="sxs-lookup"><span data-stu-id="43e59-195">Collecting and analyzing memory dumps blog</span></span>](https://devblogs.microsoft.com/dotnet/collecting-and-analyzing-memory-dumps/)
- [<span data-ttu-id="43e59-196">Yığın Analizi Aracı (DotNet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="43e59-196">Heap analysis tool (dotnet-gcdump)</span></span>](dotnet-gcdump.md)
