---
title: DotNet-sayaçlar-.NET Core
description: DotNet-Counter komut satırı aracını yüklemeyi ve kullanmayı öğrenin.
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: b2fab239713d9d19c580580496e73a91ceafcc52
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321591"
---
# <a name="dotnet-counters"></a><span data-ttu-id="dcc93-103">DotNet-sayaçlar</span><span class="sxs-lookup"><span data-stu-id="dcc93-103">dotnet-counters</span></span>

<span data-ttu-id="dcc93-104">**Bu makale şu şekilde geçerlidir: ✓** .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="dcc93-104">**This article applies to: ✓** .NET Core 3.0 SDK and later versions</span></span>

## <a name="install-dotnet-counters"></a><span data-ttu-id="dcc93-105">DotNet-sayaçlar 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="dcc93-105">Install dotnet-counters</span></span>

<span data-ttu-id="dcc93-106">@No__t-0 [NuGet paketinin](https://www.nuget.org/packages/dotnet-counters)en son sürümünü yüklemek için [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="dcc93-106">To install the latest release version of the `dotnet-counters` [NuGet package](https://www.nuget.org/packages/dotnet-counters), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a><span data-ttu-id="dcc93-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="dcc93-107">Synopsis</span></span>

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="dcc93-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dcc93-108">Description</span></span>

<span data-ttu-id="dcc93-109">`dotnet-counters`, geçici sistem durumu izleme ve ilk düzey performans araştırması için bir performans izleme aracıdır.</span><span class="sxs-lookup"><span data-stu-id="dcc93-109">`dotnet-counters` is a performance monitoring tool for ad-hoc health monitoring and first-level performance investigation.</span></span> <span data-ttu-id="dcc93-110">@No__t-0 API 'SI aracılığıyla yayınlanan performans sayacı değerlerini gözlemleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dcc93-110">It can observe performance counter values that are published via the <xref:System.Diagnostics.Tracing.EventCounter> API.</span></span> <span data-ttu-id="dcc93-111">Örneğin, `PerfView` veya `dotnet-trace` ' i kullanarak daha ciddi performans araştırmasına gerek olmadan önce şüpheli bir sorun olup olmadığını görmek için, CPU kullanımı veya .NET Core uygulamanızda oluşturulan özel durumların oranı gibi şeyleri hızlıca izleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dcc93-111">For example, you can quickly monitor things like the CPU usage or the rate of exceptions being thrown in your .NET Core application to see if there's anything suspicious before diving into more serious performance investigation using `PerfView` or `dotnet-trace`.</span></span>

## <a name="options"></a><span data-ttu-id="dcc93-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="dcc93-112">Options</span></span>

- **`--version`**

  <span data-ttu-id="dcc93-113">DotNet-Counters yardımcı programının sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dcc93-113">Displays the version of the dotnet-counters utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="dcc93-114">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="dcc93-114">Shows command-line help.</span></span>

## <a name="commands"></a><span data-ttu-id="dcc93-115">Komutlar</span><span class="sxs-lookup"><span data-stu-id="dcc93-115">Commands</span></span>

| <span data-ttu-id="dcc93-116">Komut</span><span class="sxs-lookup"><span data-stu-id="dcc93-116">Command</span></span>                                             |
| --------------------------------------------------- |
| [<span data-ttu-id="dcc93-117">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="dcc93-117">dotnet-counters list</span></span>](#dotnet-counters-list)       |
| [<span data-ttu-id="dcc93-118">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="dcc93-118">dotnet-counters monitor</span></span>](#dotnet-counters-monitor) |

## <a name="dotnet-counters-list"></a><span data-ttu-id="dcc93-119">DotNet-sayaçlar listesi</span><span class="sxs-lookup"><span data-stu-id="dcc93-119">dotnet-counters list</span></span>

<span data-ttu-id="dcc93-120">Sağlayıcıya göre gruplandırılan sayaç adlarının ve açıklamalarının listesini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dcc93-120">Displays a list of counter names and descriptions, grouped by provider.</span></span>

### <a name="synopsis"></a><span data-ttu-id="dcc93-121">Özeti</span><span class="sxs-lookup"><span data-stu-id="dcc93-121">Synopsis</span></span>

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a><span data-ttu-id="dcc93-122">Örnek</span><span class="sxs-lookup"><span data-stu-id="dcc93-122">Example</span></span>

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

## <a name="dotnet-counters-monitor"></a><span data-ttu-id="dcc93-123">DotNet-sayaçlar İzleyicisi</span><span class="sxs-lookup"><span data-stu-id="dcc93-123">dotnet-counters monitor</span></span>

<span data-ttu-id="dcc93-124">Seçili sayaçların değerlerini düzenli aralıklarla yenilemeyi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dcc93-124">Displays periodically refreshing values of selected counters.</span></span>

### <a name="synopsis"></a><span data-ttu-id="dcc93-125">Özeti</span><span class="sxs-lookup"><span data-stu-id="dcc93-125">Synopsis</span></span>

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a><span data-ttu-id="dcc93-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="dcc93-126">Options</span></span>

- **`-p|--process-id <PID>`**

  <span data-ttu-id="dcc93-127">İzlenecek işlemin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="dcc93-127">The ID of the process to be monitored.</span></span>

- **`--refresh-interval <SECONDS>`**

  <span data-ttu-id="dcc93-128">Görüntülenecek sayaçların güncelleştirilmesi arasındaki gecikme süresi (saniye)</span><span class="sxs-lookup"><span data-stu-id="dcc93-128">The number of seconds to delay between updating the displayed counters</span></span>

- **`counter_list <COUNTERS>`**

  <span data-ttu-id="dcc93-129">Sayaçların boşlukla ayrılmış bir listesi.</span><span class="sxs-lookup"><span data-stu-id="dcc93-129">A space separated list of counters.</span></span> <span data-ttu-id="dcc93-130">Sayaçlar @no__t belirtilebilir-0.</span><span class="sxs-lookup"><span data-stu-id="dcc93-130">Counters can be specified `provider_name[:counter_name]`.</span></span> <span data-ttu-id="dcc93-131">@No__t-0, niteleyen bir `counter_name` olmadan kullanılırsa, tüm sayaçlar gösterilir.</span><span class="sxs-lookup"><span data-stu-id="dcc93-131">If the `provider_name` is used without a qualifying `counter_name`, then all counters are shown.</span></span> <span data-ttu-id="dcc93-132">Sağlayıcı ve sayaç adlarını saptamak için [DotNet-Counters listesi](#dotnet-counters-list) komutunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="dcc93-132">To discover provider and counter names, use the [dotnet-counters list](#dotnet-counters-list) command.</span></span>

### <a name="examples"></a><span data-ttu-id="dcc93-133">Örnekler</span><span class="sxs-lookup"><span data-stu-id="dcc93-133">Examples</span></span>

- <span data-ttu-id="dcc93-134">@No__t-0 ' dan tüm sayaçları 3 saniyelik yenileme aralığında izleyin:</span><span class="sxs-lookup"><span data-stu-id="dcc93-134">Monitor all counters from `System.Runtime` at a refresh interval of 3 seconds:</span></span>

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

- <span data-ttu-id="dcc93-135">@No__t-0 ' dan yalnızca CPU kullanımını ve GC yığın boyutunu izle:</span><span class="sxs-lookup"><span data-stu-id="dcc93-135">Monitor just CPU usage and GC heap size from `System.Runtime`:</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- <span data-ttu-id="dcc93-136">Kullanıcı tanımlı `EventSource` ' den `EventCounter` değerlerini izleyin.</span><span class="sxs-lookup"><span data-stu-id="dcc93-136">Monitor `EventCounter` values from user-defined `EventSource`.</span></span> <span data-ttu-id="dcc93-137">Daha fazla bilgi için bkz. [öğretici: EventCounters kullanarak çok sık olaylar için performansı ölçme](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span><span class="sxs-lookup"><span data-stu-id="dcc93-137">For more information, see [Tutorial: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md).</span></span>

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
