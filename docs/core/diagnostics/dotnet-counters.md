---
title: DotNet-sayaçlar-.NET Core
description: DotNet-Counter komut satırı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 10/14/2019
ms.openlocfilehash: 399d5908e8ac52bcd4a20c1a819fc6c99f4de2f4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76737711"
---
# <a name="dotnet-counters"></a><span data-ttu-id="1ae64-103">dotnet-counters</span><span class="sxs-lookup"><span data-stu-id="1ae64-103">dotnet-counters</span></span>

<span data-ttu-id="1ae64-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="1ae64-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="1ae64-105">DotNet-sayaçlar 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="1ae64-105">Install dotnet-counters</span></span>

<span data-ttu-id="1ae64-106">`dotnet-counters` [NuGet paketinin](https://www.nuget.org/packages/dotnet-counters)en son sürümünü yüklemek için [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1ae64-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="1ae64-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="1ae64-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="1ae64-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1ae64-108">Description</span></span>

<span data-ttu-id="1ae64-109">`dotnet-counters`, geçici sistem durumu izleme ve ilk düzey performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="1ae64-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="1ae64-110"><xref:System.Diagnostics.Tracing.EventCounter> API 'SI aracılığıyla yayınlanan performans sayacı değerlerini gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ae64-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="1ae64-111">Örneğin, `PerfView` veya `dotnet-trace`kullanarak daha ciddi performans araştırmasına gerek olmadan önce kuşkulu bir sorun olup olmadığını görmek için, CPU kullanımı gibi şeyleri veya .NET Core uygulamanızda oluşturulan özel durumların oranını hızlıca izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1ae64-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="1ae64-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1ae64-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="1ae64-113">DotNet-Counters yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1ae64-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="1ae64-114">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1ae64-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="1ae64-115">Komutlar</span><span class="sxs-lookup"><span data-stu-id="1ae64-115">Commands</span></span>

| <span data-ttu-id="1ae64-116">Komut</span><span class="sxs-lookup"><span data-stu-id="1ae64-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="1ae64-117">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="1ae64-117">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="1ae64-118">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="1ae64-118">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |

## <a name="dotnet-counters-list"></a><span data-ttu-id="1ae64-119">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="1ae64-119">dotnet-counters list</span></span>

<span data-ttu-id="1ae64-120">Sağlayıcıya göre gruplandırılan sayaç adlarının ve açıklamalarının listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1ae64-120">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1ae64-121">Özeti</span><span class="sxs-lookup"><span data-stu-id="1ae64-121">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="1ae64-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="1ae64-122">Example</span></span>

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

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="1ae64-123">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="1ae64-123">dotnet-counters monitor</span></span>

<span data-ttu-id="1ae64-124">Seçili sayaçların değerlerini düzenli aralıklarla yenilemeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1ae64-124">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1ae64-125">Özeti</span><span class="sxs-lookup"><span data-stu-id="1ae64-125">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="1ae64-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1ae64-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="1ae64-127">İzlenecek işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1ae64-127">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="1ae64-128">Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="1ae64-128">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="1ae64-129">Sayaçların boşlukla ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="1ae64-129">A space separated list of counters.</span></span> <span data-ttu-id="1ae64-130">`provider_name[:counter_name]`, sayaçlar belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="1ae64-130">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="1ae64-131">`provider_name` uygun olmayan bir `counter_name`olmadan kullanılırsa, tüm sayaçlar gösterilir.</span><span class="sxs-lookup"><span data-stu-id="1ae64-131">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="1ae64-132">Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="1ae64-132">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="1ae64-133">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1ae64-133">Examples</span></span>

- <span data-ttu-id="1ae64-134">`System.Runtime` tüm sayaçları 3 saniyelik yenileme aralığında izleyin:</span><span class="sxs-lookup"><span data-stu-id="1ae64-134">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="1ae64-135">`System.Runtime`yalnızca CPU kullanımı ve GC yığın boyutunu izle:</span><span class="sxs-lookup"><span data-stu-id="1ae64-135">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="1ae64-136">Kullanıcı tanımlı `EventSource``EventCounter` değerleri izleyin.</span><span class="sxs-lookup"><span data-stu-id="1ae64-136">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="1ae64-137">Daha fazla bilgi için bkz. [öğretici: EventCounters kullanarak çok sık olaylar için performansı ölçme](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="1ae64-137">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
