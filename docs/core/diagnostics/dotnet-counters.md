---
title: dotnet sayaçları - .NET Core
description: Dotnet-counter komut satırı aracını nasıl yükleyip kullanacağınızı öğrenin.
ms.date: 02/26/2020
ms.openlocfilehash: dc95297478784ca06fe442a939f8489a40b29da7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147184"
---
# <a name="dotnet-counters"></a><span data-ttu-id="1f7ea-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="1f7ea-103">dotnet-counters</span></span>

<span data-ttu-id="1f7ea-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="1f7ea-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="1f7ea-105">dotnet sayaçları yükleme</span><span class="sxs-lookup"><span data-stu-id="1f7ea-105">Install dotnet-counters</span></span>

<span data-ttu-id="1f7ea-106">`dotnet-counters` [NuGet paketinin](https://www.nuget.org/packages/dotnet-counters)en son sürüm sürümünü yüklemek [için, dotnet aracı yükleme](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1f7ea-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="1f7ea-107">Özet</span><span class="sxs-lookup"><span data-stu-id="1f7ea-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="1f7ea-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f7ea-108">Description</span></span>

<span data-ttu-id="1f7ea-109">`dotnet-counters`özel sağlık izleme ve birinci düzey performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="1f7ea-110"><xref:System.Diagnostics.Tracing.EventCounter> API üzerinden yayınlanan performans sayacı değerlerini gözlemleyebilir.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="1f7ea-111">Örneğin, CPU kullanımı veya .NET Core uygulamanızda atılan özel durumlar gibi şeyleri hızlı bir şekilde izleyerek daha ciddi bir performans `PerfView` `dotnet-trace`araştırması yapmadan önce şüpheli bir şey olup olmadığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="1f7ea-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1f7ea-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="1f7ea-113">Dotnet sayaçları yardımcı programı sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="1f7ea-114">Komut satırı yardımlarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="1f7ea-115">Komutlar</span><span class="sxs-lookup"><span data-stu-id="1f7ea-115">Commands</span></span>

| <span data-ttu-id="1f7ea-116">Komut</span><span class="sxs-lookup"><span data-stu-id="1f7ea-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="1f7ea-117">dotnet sayaçları toplamak</span><span class="sxs-lookup"><span data-stu-id="1f7ea-117">dotnet-counters collect</span></span>](#dotnet-counters-collect) |
| [<span data-ttu-id="1f7ea-118">dotnet sayaçları listesi</span><span class="sxs-lookup"><span data-stu-id="1f7ea-118">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="1f7ea-119">dotnet sayaçları monitör</span><span class="sxs-lookup"><span data-stu-id="1f7ea-119">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |
| [<span data-ttu-id="1f7ea-120">dotnet sayaçları ps</span><span class="sxs-lookup"><span data-stu-id="1f7ea-120">dotnet-counters ps</span></span>](#dotnet-counters-ps) |

## <a name="dotnet-counters-collect"></a><span data-ttu-id="1f7ea-121">dotnet sayaçları toplamak</span><span class="sxs-lookup"><span data-stu-id="1f7ea-121">dotnet-counters collect</span></span>

<span data-ttu-id="1f7ea-122">Seçili sayaç değerlerini düzenli aralıklarla toplayın ve işlem sonrası için belirli bir dosya biçimine aktarın.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-122">Periodically collect selected counter values and export them into a specified file format for post-processing.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1f7ea-123">Özet</span><span class="sxs-lookup"><span data-stu-id="1f7ea-123">Synopsis</span></span>

```console
dotnet-counters collect [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list] [--format] [-o|--output]
```

### <a name="options"></a><span data-ttu-id="1f7ea-124">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1f7ea-124">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="1f7ea-125">İzlenecek işlemin kimliği.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-125">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="1f7ea-126">Görüntülenen sayaçları güncelleştirmek arasında geciktirecek saniye sayısı</span><span class="sxs-lookup"><span data-stu-id="1f7ea-126">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="1f7ea-127">Sayaçların ayrılmış bir boşluk listesi.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-127">A space separated list of counters.</span></span> <span data-ttu-id="1f7ea-128">Sayaçlar belirtilebilir. `provider_name[:counter_name]`</span><span class="sxs-lookup"><span data-stu-id="1f7ea-128">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="1f7ea-129">Bir `provider_name` eleme olmadan `counter_name`kullanılırsa, o zaman tüm sayaçları gösterilir.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-129">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="1f7ea-130">Sağlayıcı ve sayaç adlarını bulmak için [dotnet sayaçları liste](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-130">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

- **`--format <csv|json>`**

  <span data-ttu-id="1f7ea-131">TThe biçimi dışa aktarılacak.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-131">TThe format to be exported.</span></span> <span data-ttu-id="1f7ea-132">Şu anda kullanılabilir: csv, json.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-132">Currently available: csv, json.</span></span>

- **`-o|--output <output>`**

  <span data-ttu-id="1f7ea-133">Çıktı dosyasının adı.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-133">The name of the output file.</span></span>

### <a name="examples"></a><span data-ttu-id="1f7ea-134">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1f7ea-134">Examples</span></span>

- <span data-ttu-id="1f7ea-135">Tüm sayaçları 3 saniyelik bir yenileme aralığında toplayın ve çıktı olarak bir csv oluşturun:</span><span class="sxs-lookup"><span data-stu-id="1f7ea-135">Collect all counters at a refresh interval of 3 seconds and generate a csv as output:</span></span>

  ```console
  > dotnet-counters collect --process-id 1902 --refresh-interval 3 --format csv

  counter_list is unspecified. Monitoring all counters by default.
  Starting a counter session. Press Q to quit.
  ```

## <a name="dotnet-counters-list"></a><span data-ttu-id="1f7ea-136">dotnet sayaçları listesi</span><span class="sxs-lookup"><span data-stu-id="1f7ea-136">dotnet-counters list</span></span>

<span data-ttu-id="1f7ea-137">Sağlayıcıya göre gruplanmış sayaç adlarının ve açıklamaların listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-137">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1f7ea-138">Özet</span><span class="sxs-lookup"><span data-stu-id="1f7ea-138">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="1f7ea-139">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f7ea-139">Example</span></span>

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

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="1f7ea-140">dotnet sayaçları monitör</span><span class="sxs-lookup"><span data-stu-id="1f7ea-140">dotnet-counters monitor</span></span>

<span data-ttu-id="1f7ea-141">Seçili sayaçların periyodik olarak yenilenme değerlerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-141">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1f7ea-142">Özet</span><span class="sxs-lookup"><span data-stu-id="1f7ea-142">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="1f7ea-143">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1f7ea-143">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="1f7ea-144">İzlenecek işlemin kimliği.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-144">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="1f7ea-145">Görüntülenen sayaçları güncelleştirmek arasında geciktirecek saniye sayısı</span><span class="sxs-lookup"><span data-stu-id="1f7ea-145">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="1f7ea-146">Sayaçların ayrılmış bir boşluk listesi.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-146">A space separated list of counters.</span></span> <span data-ttu-id="1f7ea-147">Sayaçlar belirtilebilir. `provider_name[:counter_name]`</span><span class="sxs-lookup"><span data-stu-id="1f7ea-147">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="1f7ea-148">Bir `provider_name` eleme olmadan `counter_name`kullanılırsa, o zaman tüm sayaçları gösterilir.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-148">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="1f7ea-149">Sağlayıcı ve sayaç adlarını bulmak için [dotnet sayaçları liste](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-149">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="1f7ea-150">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1f7ea-150">Examples</span></span>

- <span data-ttu-id="1f7ea-151">Tüm sayaçları `System.Runtime` 3 saniyelik bir yenileme aralığından izleyin:</span><span class="sxs-lookup"><span data-stu-id="1f7ea-151">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="1f7ea-152">Monitör sadece CPU kullanımı ve GC yığın boyutu: `System.Runtime`</span><span class="sxs-lookup"><span data-stu-id="1f7ea-152">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="1f7ea-153">`EventCounter` Değerleri kullanıcı tanımlı `EventSource`olarak izleyin.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-153">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="1f7ea-154">Daha fazla bilgi için [Bkz. Öğretici: EventCounters'ı kullanarak çok sık karşılaşılan olaylar için performans nasıl ölçülür?](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)</span><span class="sxs-lookup"><span data-stu-id="1f7ea-154">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
  
## <a name="dotnet-counters-ps"></a><span data-ttu-id="1f7ea-155">dotnet sayaçları ps</span><span class="sxs-lookup"><span data-stu-id="1f7ea-155">dotnet-counters ps</span></span>

<span data-ttu-id="1f7ea-156">İzlenebilen dotnet işlemlerinin listesini görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="1f7ea-156">Display a list of dotnet processes that can be monitored.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1f7ea-157">Özet</span><span class="sxs-lookup"><span data-stu-id="1f7ea-157">Synopsis</span></span>

```console
dotnet-counters ps [-h|--help]
```

### <a name="example"></a><span data-ttu-id="1f7ea-158">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f7ea-158">Example</span></span>

```console
> dotnet-counters ps
  
  15683 WebApi     /home/suwhang/repos/WebApi/WebApi
  16324 dotnet     /usr/local/share/dotnet/dotnet
```
