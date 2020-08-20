---
title: DotNet-gcdump-.NET Core
description: DotNet-gcdump komut satırı aracını yükleme ve kullanma.
ms.date: 07/26/2020
ms.openlocfilehash: a7b19f4d7487677b975621e7267a17894dae2e3a
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656657"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="2aaa2-103">Yığın Analizi Aracı (DotNet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="2aaa2-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="2aaa2-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="2aaa2-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install-dotnet-gcdump"></a><span data-ttu-id="2aaa2-105">DotNet-gcdump 'i yükler</span><span class="sxs-lookup"><span data-stu-id="2aaa2-105">Install dotnet-gcdump</span></span>

<span data-ttu-id="2aaa2-106">NuGet paketinin en son sürümünü yüklemek için `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="2aaa2-106">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-gcdump
```

## <a name="synopsis"></a><span data-ttu-id="2aaa2-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="2aaa2-107">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="2aaa2-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2aaa2-108">Description</span></span>

<span data-ttu-id="2aaa2-109">`dotnet-gcdump`Genel araç, canlı .net IŞLEMLERININ GC (çöp toplayıcısı) dökümlerini toplamanın bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-109">The `dotnet-gcdump` global tool is a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span> <span data-ttu-id="2aaa2-110">Windows üzerinde ETW için platformlar arası bir alternatif olan EventPipe teknolojisini kullanır.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-110">It uses the EventPipe technology, which is a cross-platform alternative to ETW on Windows.</span></span> <span data-ttu-id="2aaa2-111">GC dökümleri, hedef işlemde bir GC tetikleyerek, özel olayları açıp, nesne kökleri grafiğini Olay akışından yeniden oluşturarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-111">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="2aaa2-112">Bu işlem, işlem çalışırken ve en az ek yük ile GC dökümlerinin toplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-112">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="2aaa2-113">Bu dökümler birkaç senaryo için yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="2aaa2-113">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="2aaa2-114">Yığın üzerindeki nesne sayısını zaman içinde birkaç noktada karşılaştırma.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-114">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="2aaa2-115">Nesnelerin kökleri çözümleniyor ("Bu tür için hala bir başvuru var?" gibi sorulara yanıt verme).</span><span class="sxs-lookup"><span data-stu-id="2aaa2-115">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="2aaa2-116">Yığındaki nesnelerin sayılarıyla ilgili genel istatistikleri toplama.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-116">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="2aaa2-117">DotNet-gcdump öğesinden yakalanan GC dökümünü görüntüleme</span><span class="sxs-lookup"><span data-stu-id="2aaa2-117">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="2aaa2-118">Windows 'da, `.gcdump` dosyalar, analiz veya Visual Studio 'Da [PerfView](https://github.com/microsoft/perfview) ' de görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-118">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="2aaa2-119">Şu anda Windows dışı platformlarda ' ı açma yöntemi yoktur `.gcdump` .</span><span class="sxs-lookup"><span data-stu-id="2aaa2-119">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="2aaa2-120">`.gcdump`Bir karşılaştırma deneyimi almak için birden çok s toplayabilir ve bunları Visual Studio 'da eşzamanlı olarak açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-120">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="2aaa2-121">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2aaa2-121">Options</span></span>

- **`--version`**

  <span data-ttu-id="2aaa2-122">`dotnet-gcdump`Yardımcı programın sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-122">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2aaa2-123">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-123">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="2aaa2-124">Şu anda çalışan bir işlemden bir GC dökümü toplar.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-124">Collects a GC dump from a currently running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2aaa2-125">Özeti</span><span class="sxs-lookup"><span data-stu-id="2aaa2-125">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="2aaa2-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2aaa2-126">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="2aaa2-127">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-127">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="2aaa2-128">GC dökümünü toplanacak işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-128">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="2aaa2-129">Toplanan GC dökümlerinin yazılması gereken yol.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-129">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="2aaa2-130">Varsayılan olarak olur *. \\ YYYYMMDD \_ HHMMSS \_ \<pid> . gcdump*.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-130">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="2aaa2-131">GC dökümünü toplarken günlüğü çıkış.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-131">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="2aaa2-132">Bu çok saniyeden daha uzun sürerse GC dökümünü toplama hakkında bilgi verin.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-132">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="2aaa2-133">Varsayılan değer 30’dur.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-133">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="2aaa2-134">GC dökümünü toplanacak işlemin adı.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-134">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="2aaa2-135">GC dökümlerinin toplanabilecek DotNet süreçlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-135">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2aaa2-136">Özeti</span><span class="sxs-lookup"><span data-stu-id="2aaa2-136">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="2aaa2-137">Önceden oluşturulmuş bir GC dökümünden veya çalışan bir işlemden rapor oluşturun ve öğesine yazın `stdout` .</span><span class="sxs-lookup"><span data-stu-id="2aaa2-137">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="2aaa2-138">Özeti</span><span class="sxs-lookup"><span data-stu-id="2aaa2-138">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="2aaa2-139">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2aaa2-139">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="2aaa2-140">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-140">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="2aaa2-141">GC dökümünü toplanacak işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-141">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="2aaa2-142">Oluşturulacak raporun türü.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-142">The type of report to generate.</span></span> <span data-ttu-id="2aaa2-143">Kullanılabilir seçenekler: heapstat (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="2aaa2-143">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="2aaa2-144">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="2aaa2-144">Troubleshoot</span></span>

- <span data-ttu-id="2aaa2-145">Gcdump içinde tür bilgisi yok.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-145">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="2aaa2-146">.NET Core 3,1 ' den önce, EventPipe ile çağrıldığında gcdumps arasında bir tür önbelleğinin temizlenmediği bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-146">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="2aaa2-147">Bu, ikinci ve sonraki gcdumps için gönderilmemiş tür bilgilerinin belirlenmesi için gereken olaylara neden oldu.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-147">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="2aaa2-148">Bu, .NET Core 3,1-preview2 ' de düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-148">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="2aaa2-149">COM ve statik türler GC dökümünde değildir.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-149">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="2aaa2-150">.NET Core 3,1-preview2 öncesinde, GC dökümü EventPipe aracılığıyla çağrıldığında statik ve COM türlerinin gönderilmediği bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-150">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="2aaa2-151">Bu, .NET Core 3,1-preview2 ' de düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="2aaa2-151">This has been fixed in .NET Core 3.1-preview2.</span></span>
