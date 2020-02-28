---
title: DotNet-sayaçlar-.NET Core
description: DotNet-Counter komut satırı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 02/26/2020
ms.openlocfilehash: 88f701a60d0ee03dd0236ae54c57679943e14939
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157888"
---
# <a name="dotnet-counters"></a><span data-ttu-id="7b29d-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="7b29d-103">dotnet-counters</span></span>

<span data-ttu-id="7b29d-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="7b29d-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="7b29d-105">DotNet-sayaçlar 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="7b29d-105">Install dotnet-counters</span></span>

<span data-ttu-id="7b29d-106">`dotnet-counters` [NuGet paketinin](https://www.nuget.org/packages/dotnet-counters)en son sürümünü yüklemek için [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="7b29d-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="7b29d-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="7b29d-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="7b29d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7b29d-108">Description</span></span>

<span data-ttu-id="7b29d-109">`dotnet-counters`, geçici sistem durumu izleme ve ilk düzey performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="7b29d-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="7b29d-110"><xref:System.Diagnostics.Tracing.EventCounter> API 'SI aracılığıyla yayınlanan performans sayacı değerlerini gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b29d-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="7b29d-111">Örneğin, `PerfView` veya `dotnet-trace`kullanarak daha ciddi performans araştırmasına gerek olmadan önce kuşkulu bir sorun olup olmadığını görmek için, CPU kullanımı gibi şeyleri veya .NET Core uygulamanızda oluşturulan özel durumların oranını hızlıca izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7b29d-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="7b29d-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7b29d-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="7b29d-113">DotNet-Counters yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7b29d-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="7b29d-114">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="7b29d-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="7b29d-115">Komutlar</span><span class="sxs-lookup"><span data-stu-id="7b29d-115">Commands</span></span>

| <span data-ttu-id="7b29d-116">Komut</span><span class="sxs-lookup"><span data-stu-id="7b29d-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="7b29d-117">DotNet-sayaçlar toplama</span><span class="sxs-lookup"><span data-stu-id="7b29d-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="7b29d-118">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="7b29d-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="7b29d-119">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="7b29d-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="7b29d-120">DotNet-sayaçlar PS 'si</span><span class="sxs-lookup"><span data-stu-id="7b29d-120">dotnet-counters ps</span></span>](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="7b29d-121">DotNet-sayaçlar toplama</span><span class="sxs-lookup"><span data-stu-id="7b29d-121">dotnet-counters collect</span></span>

<span data-ttu-id="7b29d-122">Seçili sayaç değerlerini düzenli olarak toplayın ve işleme sonrası için belirtilen dosya biçimine dışarı aktarın.</span><span class="sxs-lookup"><span data-stu-id="7b29d-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b29d-123">Özeti</span><span class="sxs-lookup"><span data-stu-id="7b29d-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="7b29d-124">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7b29d-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="7b29d-125">İzlenecek işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="7b29d-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="7b29d-126">Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="7b29d-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="7b29d-127">Sayaçların boşlukla ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="7b29d-127">A space separated list of counters.</span></span> <span data-ttu-id="7b29d-128">`provider_name[:counter_name]`, sayaçlar belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="7b29d-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="7b29d-129">`provider_name` uygun olmayan bir `counter_name`olmadan kullanılırsa, tüm sayaçlar gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7b29d-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="7b29d-130">Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b29d-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="7b29d-131">Aktarılacak biçim.</span><span class="sxs-lookup"><span data-stu-id="7b29d-131">TThe format to be exported.</span></span> <span data-ttu-id="7b29d-132">Şu anda kullanılabilir: CSV, JSON.</span><span class="sxs-lookup"><span data-stu-id="7b29d-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="7b29d-133">Çıktı dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="7b29d-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="7b29d-134">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7b29d-134">Examples</span></span>

- <span data-ttu-id="7b29d-135">Tüm sayaçları 3 saniyelik yenileme aralığında toplayın ve çıkış olarak bir CSV oluşturun:</span><span class="sxs-lookup"><span data-stu-id="7b29d-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="7b29d-136">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="7b29d-136">dotnet-counters list</span></span>

<span data-ttu-id="7b29d-137">Sağlayıcıya göre gruplandırılan sayaç adlarının ve açıklamalarının listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7b29d-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b29d-138">Özeti</span><span class="sxs-lookup"><span data-stu-id="7b29d-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="7b29d-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b29d-139">Example</span></span>

```console
> dotnet-counters list

    Showing well-known counters only. Specific processes may support additional counters.
    System.Runtime
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="7b29d-140">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="7b29d-140">dotnet-counters monitor</span></span>

<span data-ttu-id="7b29d-141">Seçili sayaçların değerlerini düzenli aralıklarla yenilemeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="7b29d-141">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b29d-142">Özeti</span><span class="sxs-lookup"><span data-stu-id="7b29d-142">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="7b29d-143">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7b29d-143">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="7b29d-144">İzlenecek işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="7b29d-144">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="7b29d-145">Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="7b29d-145">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="7b29d-146">Sayaçların boşlukla ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="7b29d-146">A space separated list of counters.</span></span> <span data-ttu-id="7b29d-147">`provider_name[:counter_name]`, sayaçlar belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="7b29d-147">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="7b29d-148">`provider_name` uygun olmayan bir `counter_name`olmadan kullanılırsa, tüm sayaçlar gösterilir.</span><span class="sxs-lookup"><span data-stu-id="7b29d-148">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="7b29d-149">Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="7b29d-149">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="7b29d-150">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7b29d-150">Examples</span></span>

- <span data-ttu-id="7b29d-151">`System.Runtime` tüm sayaçları 3 saniyelik yenileme aralığında izleyin:</span><span class="sxs-lookup"><span data-stu-id="7b29d-151">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- <span data-ttu-id="7b29d-152">`System.Runtime`yalnızca CPU kullanımı ve GC yığın boyutunu izle:</span><span class="sxs-lookup"><span data-stu-id="7b29d-152">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="7b29d-153">Kullanıcı tanımlı `EventSource``EventCounter` değerleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="7b29d-153">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="7b29d-154">Daha fazla bilgi için bkz. [öğretici: EventCounters kullanarak çok sık olaylar için performansı ölçme](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="7b29d-154">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="7b29d-155">DotNet-sayaçlar PS 'si</span><span class="sxs-lookup"><span data-stu-id="7b29d-155">dotnet-counters ps</span></span> 

<span data-ttu-id="7b29d-156">İzlenebilecek DotNet işlemlerinin bir listesini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="7b29d-156">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="7b29d-157">Özeti</span><span class="sxs-lookup"><span data-stu-id="7b29d-157">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="7b29d-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="7b29d-158">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
