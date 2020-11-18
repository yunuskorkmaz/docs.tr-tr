---
title: DotNet-gcdump Tanılama aracı-.NET CLı
description: .NET EventPipe kullanarak canlı .NET işlemlerinin GC (çöp toplayıcısı) dökümlerini toplamak için DotNet-gcdump CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 59de1845ada9e5bdd0b24bf4312517283324ce94
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94826046"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="f809e-103">Yığın Analizi Aracı (DotNet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="f809e-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="f809e-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="f809e-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="f809e-105">Yükleme</span><span class="sxs-lookup"><span data-stu-id="f809e-105">Install</span></span>

<span data-ttu-id="f809e-106">İndirmek ve yüklemek için iki yol vardır `dotnet-gcdump` :</span><span class="sxs-lookup"><span data-stu-id="f809e-106">There are two ways to download and install `dotnet-gcdump`:</span></span>

- <span data-ttu-id="f809e-107">**DotNet genel aracı:**</span><span class="sxs-lookup"><span data-stu-id="f809e-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="f809e-108">NuGet paketinin en son sürümünü yüklemek için `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f809e-108">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- <span data-ttu-id="f809e-109">**Doğrudan indirme:**</span><span class="sxs-lookup"><span data-stu-id="f809e-109">**Direct download:**</span></span>

  <span data-ttu-id="f809e-110">Platformunuzla eşleşen araç yürütülebilirini indirin:</span><span class="sxs-lookup"><span data-stu-id="f809e-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="f809e-111">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="f809e-111">OS</span></span>  | <span data-ttu-id="f809e-112">Platform</span><span class="sxs-lookup"><span data-stu-id="f809e-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="f809e-113">Windows</span><span class="sxs-lookup"><span data-stu-id="f809e-113">Windows</span></span> | <span data-ttu-id="f809e-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [ARM](https://aka.ms/dotnet-gcdump/win-arm) \| [ARM-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="f809e-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span></span> |
  | <span data-ttu-id="f809e-115">macOS</span><span class="sxs-lookup"><span data-stu-id="f809e-115">macOS</span></span>   | [<span data-ttu-id="f809e-116">x64</span><span class="sxs-lookup"><span data-stu-id="f809e-116">x64</span></span>](https://aka.ms/dotnet-gcdump/osx-x64) |
  | <span data-ttu-id="f809e-117">Linux</span><span class="sxs-lookup"><span data-stu-id="f809e-117">Linux</span></span>   | <span data-ttu-id="f809e-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [ARM](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="f809e-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="f809e-119">Özeti</span><span class="sxs-lookup"><span data-stu-id="f809e-119">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="f809e-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f809e-120">Description</span></span>

<span data-ttu-id="f809e-121">`dotnet-gcdump`Genel araç, [eventpipe](./eventpipe.md)kullanarak canlı .net Işlemlerinin GC (çöp toplayıcısı) dökümlerini toplar.</span><span class="sxs-lookup"><span data-stu-id="f809e-121">The `dotnet-gcdump` global tool collects GC (Garbage Collector) dumps of live .NET processes using [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="f809e-122">GC dökümleri, hedef işlemde bir GC tetikleyerek, özel olayları açıp, nesne kökleri grafiğini Olay akışından yeniden oluşturarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="f809e-122">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="f809e-123">Bu işlem, işlem çalışırken ve en az ek yük ile GC dökümlerinin toplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f809e-123">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="f809e-124">Bu dökümler birkaç senaryo için yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="f809e-124">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="f809e-125">Yığın üzerindeki nesne sayısını zaman içinde birkaç noktada karşılaştırma.</span><span class="sxs-lookup"><span data-stu-id="f809e-125">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="f809e-126">Nesnelerin kökleri çözümleniyor ("Bu tür için hala bir başvuru var?" gibi sorulara yanıt verme).</span><span class="sxs-lookup"><span data-stu-id="f809e-126">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="f809e-127">Yığındaki nesnelerin sayılarıyla ilgili genel istatistikleri toplama.</span><span class="sxs-lookup"><span data-stu-id="f809e-127">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="f809e-128">DotNet-gcdump öğesinden yakalanan GC dökümünü görüntüleme</span><span class="sxs-lookup"><span data-stu-id="f809e-128">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="f809e-129">Windows 'da, `.gcdump` dosyalar, analiz veya Visual Studio 'Da [PerfView](https://github.com/microsoft/perfview) ' de görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="f809e-129">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="f809e-130">Şu anda Windows dışı platformlarda ' ı açma yöntemi yoktur `.gcdump` .</span><span class="sxs-lookup"><span data-stu-id="f809e-130">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="f809e-131">`.gcdump`Bir karşılaştırma deneyimi almak için birden çok s toplayabilir ve bunları Visual Studio 'da eşzamanlı olarak açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f809e-131">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="f809e-132">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f809e-132">Options</span></span>

- **`--version`**

  <span data-ttu-id="f809e-133">`dotnet-gcdump`Yardımcı programın sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f809e-133">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f809e-134">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f809e-134">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="f809e-135">Şu anda çalışan bir işlemden bir GC dökümü toplar.</span><span class="sxs-lookup"><span data-stu-id="f809e-135">Collects a GC dump from a currently running process.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f809e-136">Özeti</span><span class="sxs-lookup"><span data-stu-id="f809e-136">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="f809e-137">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f809e-137">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f809e-138">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f809e-138">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="f809e-139">GC dökümünü toplanacak işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f809e-139">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="f809e-140">Toplanan GC dökümlerinin yazılması gereken yol.</span><span class="sxs-lookup"><span data-stu-id="f809e-140">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="f809e-141">Varsayılan olarak olur *. \\ YYYYMMDD \_ HHMMSS \_ \<pid> . gcdump*.</span><span class="sxs-lookup"><span data-stu-id="f809e-141">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="f809e-142">GC dökümünü toplarken günlüğü çıkış.</span><span class="sxs-lookup"><span data-stu-id="f809e-142">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="f809e-143">Bu çok saniyeden daha uzun sürerse GC dökümünü toplama hakkında bilgi verin.</span><span class="sxs-lookup"><span data-stu-id="f809e-143">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="f809e-144">Varsayılan değer 30’dur.</span><span class="sxs-lookup"><span data-stu-id="f809e-144">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="f809e-145">GC dökümünü toplanacak işlemin adı.</span><span class="sxs-lookup"><span data-stu-id="f809e-145">The name of the process to collect the GC dump from.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="f809e-146">GC dökümlerinin toplanabilecek DotNet süreçlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="f809e-146">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f809e-147">Özeti</span><span class="sxs-lookup"><span data-stu-id="f809e-147">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="f809e-148">Önceden oluşturulmuş bir GC dökümünden veya çalışan bir işlemden rapor oluşturun ve öğesine yazın `stdout` .</span><span class="sxs-lookup"><span data-stu-id="f809e-148">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="f809e-149">Özeti</span><span class="sxs-lookup"><span data-stu-id="f809e-149">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="f809e-150">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="f809e-150">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="f809e-151">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="f809e-151">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="f809e-152">GC dökümünü toplanacak işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="f809e-152">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="f809e-153">Oluşturulacak raporun türü.</span><span class="sxs-lookup"><span data-stu-id="f809e-153">The type of report to generate.</span></span> <span data-ttu-id="f809e-154">Kullanılabilir seçenekler: heapstat (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="f809e-154">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="f809e-155">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="f809e-155">Troubleshoot</span></span>

- <span data-ttu-id="f809e-156">Gcdump içinde tür bilgisi yok.</span><span class="sxs-lookup"><span data-stu-id="f809e-156">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="f809e-157">.NET Core 3,1 ' den önce, EventPipe ile çağrıldığında gcdumps arasında bir tür önbelleğinin temizlenmediği bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="f809e-157">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="f809e-158">Bu, ikinci ve sonraki gcdumps için gönderilmemiş tür bilgilerinin belirlenmesi için gereken olaylara neden oldu.</span><span class="sxs-lookup"><span data-stu-id="f809e-158">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="f809e-159">Bu, .NET Core 3,1-preview2 ' de düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f809e-159">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="f809e-160">COM ve statik türler GC dökümünde değildir.</span><span class="sxs-lookup"><span data-stu-id="f809e-160">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="f809e-161">.NET Core 3,1-preview2 öncesinde, GC dökümü EventPipe aracılığıyla çağrıldığında statik ve COM türlerinin gönderilmediği bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="f809e-161">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="f809e-162">Bu, .NET Core 3,1-preview2 ' de düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f809e-162">This has been fixed in .NET Core 3.1-preview2.</span></span>
