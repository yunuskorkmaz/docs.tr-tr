---
title: DotNet-gcdump Tanılama aracı-.NET CLı
description: .NET EventPipe kullanarak canlı .NET işlemlerinin GC (çöp toplayıcısı) dökümlerini toplamak için DotNet-gcdump CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: fe7772eed642daadbd1754627751f58d0ab57b8e
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2021
ms.locfileid: "98188575"
---
# <a name="heap-analysis-tool-dotnet-gcdump"></a><span data-ttu-id="61652-103">Yığın Analizi Aracı (DotNet-gcdump)</span><span class="sxs-lookup"><span data-stu-id="61652-103">Heap analysis tool (dotnet-gcdump)</span></span>

<span data-ttu-id="61652-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="61652-104">**This article applies to:** ✔️ .NET Core 3.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="61652-105">Yükleme</span><span class="sxs-lookup"><span data-stu-id="61652-105">Install</span></span>

<span data-ttu-id="61652-106">İndirmek ve yüklemek için iki yol vardır `dotnet-gcdump` :</span><span class="sxs-lookup"><span data-stu-id="61652-106">There are two ways to download and install `dotnet-gcdump`:</span></span>

- <span data-ttu-id="61652-107">**DotNet genel aracı:**</span><span class="sxs-lookup"><span data-stu-id="61652-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="61652-108">NuGet paketinin en son sürümünü yüklemek için `dotnet-gcdump` [](https://www.nuget.org/packages/dotnet-gcdump) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="61652-108">To install the latest release version of the `dotnet-gcdump` [NuGet package](https://www.nuget.org/packages/dotnet-gcdump), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-gcdump
  ```

- <span data-ttu-id="61652-109">**Doğrudan indirme:**</span><span class="sxs-lookup"><span data-stu-id="61652-109">**Direct download:**</span></span>

  <span data-ttu-id="61652-110">Platformunuzla eşleşen araç yürütülebilirini indirin:</span><span class="sxs-lookup"><span data-stu-id="61652-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="61652-111">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="61652-111">OS</span></span>  | <span data-ttu-id="61652-112">Platform</span><span class="sxs-lookup"><span data-stu-id="61652-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="61652-113">Windows</span><span class="sxs-lookup"><span data-stu-id="61652-113">Windows</span></span> | <span data-ttu-id="61652-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [ARM](https://aka.ms/dotnet-gcdump/win-arm) \| [ARM-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="61652-114">[x86](https://aka.ms/dotnet-gcdump/win-x86) \| [x64](https://aka.ms/dotnet-gcdump/win-x64) \| [arm](https://aka.ms/dotnet-gcdump/win-arm) \| [arm-x64](https://aka.ms/dotnet-gcdump/win-arm64)</span></span> |
  | <span data-ttu-id="61652-115">Mac OS</span><span class="sxs-lookup"><span data-stu-id="61652-115">macOS</span></span>   | [<span data-ttu-id="61652-116">x64</span><span class="sxs-lookup"><span data-stu-id="61652-116">x64</span></span>](https://aka.ms/dotnet-gcdump/osx-x64) |
  | <span data-ttu-id="61652-117">Linux</span><span class="sxs-lookup"><span data-stu-id="61652-117">Linux</span></span>   | <span data-ttu-id="61652-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [ARM](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="61652-118">[x64](https://aka.ms/dotnet-gcdump/linux-x64) \| [arm](https://aka.ms/dotnet-gcdump/linux-arm) \| [arm64](https://aka.ms/dotnet-gcdump/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-gcdump/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-gcdump/linux-musl-arm64)</span></span> |

> [!NOTE]
> <span data-ttu-id="61652-119">`dotnet-gcdump`X86 uygulamasında kullanmak için, aracın karşılık gelen x86 sürümüne ihtiyacınız vardır.</span><span class="sxs-lookup"><span data-stu-id="61652-119">To use `dotnet-gcdump` on an x86 app, you need a corresponding x86 version of the tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="61652-120">Özeti</span><span class="sxs-lookup"><span data-stu-id="61652-120">Synopsis</span></span>

```console
dotnet-gcdump [-h|--help] [--version] <command>
```

## <a name="description"></a><span data-ttu-id="61652-121">Description</span><span class="sxs-lookup"><span data-stu-id="61652-121">Description</span></span>

<span data-ttu-id="61652-122">`dotnet-gcdump`Genel araç, [eventpipe](./eventpipe.md)kullanarak canlı .net Işlemlerinin GC (çöp toplayıcısı) dökümlerini toplar.</span><span class="sxs-lookup"><span data-stu-id="61652-122">The `dotnet-gcdump` global tool collects GC (Garbage Collector) dumps of live .NET processes using [EventPipe](./eventpipe.md).</span></span> <span data-ttu-id="61652-123">GC dökümleri, hedef işlemde bir GC tetikleyerek, özel olayları açıp, nesne kökleri grafiğini Olay akışından yeniden oluşturarak oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="61652-123">GC dumps are created by triggering a GC in the target process, turning on special events, and regenerating the graph of object roots from the event stream.</span></span> <span data-ttu-id="61652-124">Bu işlem, işlem çalışırken ve en az ek yük ile GC dökümlerinin toplanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="61652-124">This process allows for GC dumps to be collected while the process is running and with minimal overhead.</span></span> <span data-ttu-id="61652-125">Bu dökümler birkaç senaryo için yararlıdır:</span><span class="sxs-lookup"><span data-stu-id="61652-125">These dumps are useful for several scenarios:</span></span>

- <span data-ttu-id="61652-126">Yığın üzerindeki nesne sayısını zaman içinde birkaç noktada karşılaştırma.</span><span class="sxs-lookup"><span data-stu-id="61652-126">Comparing the number of objects on the heap at several points in time.</span></span>
- <span data-ttu-id="61652-127">Nesnelerin kökleri çözümleniyor ("Bu tür için hala bir başvuru var?" gibi sorulara yanıt verme).</span><span class="sxs-lookup"><span data-stu-id="61652-127">Analyzing roots of objects (answering questions like, "what still has a reference to this type?").</span></span>
- <span data-ttu-id="61652-128">Yığındaki nesnelerin sayılarıyla ilgili genel istatistikleri toplama.</span><span class="sxs-lookup"><span data-stu-id="61652-128">Collecting general statistics about the counts of objects on the heap.</span></span>

### <a name="view-the-gc-dump-captured-from-dotnet-gcdump"></a><span data-ttu-id="61652-129">DotNet-gcdump öğesinden yakalanan GC dökümünü görüntüleme</span><span class="sxs-lookup"><span data-stu-id="61652-129">View the GC dump captured from dotnet-gcdump</span></span>

<span data-ttu-id="61652-130">Windows 'da, `.gcdump` dosyalar, analiz veya Visual Studio 'Da [PerfView](https://github.com/microsoft/perfview) ' de görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="61652-130">On Windows, `.gcdump` files can be viewed in [PerfView](https://github.com/microsoft/perfview) for analysis or in Visual Studio.</span></span> <span data-ttu-id="61652-131">Şu anda Windows dışı platformlarda ' ı açma yöntemi yoktur `.gcdump` .</span><span class="sxs-lookup"><span data-stu-id="61652-131">Currently, There is no way of opening a `.gcdump` on non-Windows platforms.</span></span>

<span data-ttu-id="61652-132">`.gcdump`Bir karşılaştırma deneyimi almak için birden çok s toplayabilir ve bunları Visual Studio 'da eşzamanlı olarak açabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="61652-132">You can collect multiple `.gcdump`s and open them simultaneously in Visual Studio to get a comparison experience.</span></span>

## <a name="options"></a><span data-ttu-id="61652-133">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="61652-133">Options</span></span>

- **`--version`**

  <span data-ttu-id="61652-134">`dotnet-gcdump`Yardımcı programın sürümünü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="61652-134">Displays the version of the `dotnet-gcdump` utility.</span></span>

- **`-h|--help`**

  <span data-ttu-id="61652-135">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="61652-135">Shows command-line help.</span></span>

## `dotnet-gcdump collect`

<span data-ttu-id="61652-136">Şu anda çalışan bir işlemden bir GC dökümü toplar.</span><span class="sxs-lookup"><span data-stu-id="61652-136">Collects a GC dump from a currently running process.</span></span>

> [!WARNING]
> <span data-ttu-id="61652-137">GC yığınına yol göstermek için, bu komut, özellikle GC yığını büyük olduğunda, çalışma zamanını uzun bir süre askıya alabilen 2. nesil (tam) çöp toplamayı tetikler.</span><span class="sxs-lookup"><span data-stu-id="61652-137">To walk the GC heap, this command triggers a generation 2 (full) garbage collection, which can suspend the runtime for a long time, especially when the GC heap is large.</span></span> <span data-ttu-id="61652-138">GC yığını büyükse, performansa duyarlı ortamlarda bu komutu kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="61652-138">Don't use this command in performance-sensitive environments when the GC heap is large.</span></span>

### <a name="synopsis"></a><span data-ttu-id="61652-139">Özeti</span><span class="sxs-lookup"><span data-stu-id="61652-139">Synopsis</span></span>

```console
dotnet-gcdump collect [-h|--help] [-p|--process-id <pid>] [-o|--output <gcdump-file-path>] [-v|--verbose] [-t|--timeout <timeout>] [-n|--name <name>]
```

### <a name="options"></a><span data-ttu-id="61652-140">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="61652-140">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="61652-141">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="61652-141">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="61652-142">GC dökümünü toplanacak işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="61652-142">The process ID to collect the GC dump from.</span></span>

- **`-o|--output <gcdump-file-path>`**

  <span data-ttu-id="61652-143">Toplanan GC dökümlerinin yazılması gereken yol.</span><span class="sxs-lookup"><span data-stu-id="61652-143">The path where collected GC dumps should be written.</span></span> <span data-ttu-id="61652-144">Varsayılan olarak olur *. \\ YYYYMMDD \_ HHMMSS \_ \<pid> . gcdump*.</span><span class="sxs-lookup"><span data-stu-id="61652-144">Defaults to *.\\YYYYMMDD\_HHMMSS\_\<pid>.gcdump*.</span></span>

- **`-v|--verbose`**

  <span data-ttu-id="61652-145">GC dökümünü toplarken günlüğü çıkış.</span><span class="sxs-lookup"><span data-stu-id="61652-145">Output the log while collecting the GC dump.</span></span>

- **`-t|--timeout <timeout>`**

  <span data-ttu-id="61652-146">Bu çok saniyeden daha uzun sürerse GC dökümünü toplama hakkında bilgi verin.</span><span class="sxs-lookup"><span data-stu-id="61652-146">Give up on collecting the GC dump if it takes longer than this many seconds.</span></span> <span data-ttu-id="61652-147">Varsayılan değer 30’dur.</span><span class="sxs-lookup"><span data-stu-id="61652-147">The default value is 30.</span></span>

- **`-n|--name <name>`**

  <span data-ttu-id="61652-148">GC dökümünü toplanacak işlemin adı.</span><span class="sxs-lookup"><span data-stu-id="61652-148">The name of the process to collect the GC dump from.</span></span>

> [!NOTE]
> <span data-ttu-id="61652-149">Linux ve macOS 'ta, bu komut hedef uygulamayı bekler ve `dotnet-gcdump` aynı `TMPDIR` ortam değişkenini paylaşır.</span><span class="sxs-lookup"><span data-stu-id="61652-149">On Linux and macOS, this command expects the target application and `dotnet-gcdump` to share the same `TMPDIR` environment variable.</span></span> <span data-ttu-id="61652-150">Aksi takdirde, komut zaman aşımına uğrar.</span><span class="sxs-lookup"><span data-stu-id="61652-150">Otherwise, the command will time out.</span></span>

> [!NOTE]
> <span data-ttu-id="61652-151">Kullanarak bir GC dökümünü toplamak için `dotnet-gcdump` , kullanıcının hedef işlem çalıştıran kullanıcı veya kök olarak aynı kullanıcı olarak çalıştırılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="61652-151">To collect a GC dump using `dotnet-gcdump`, it needs to be run as the same user as the user running target process or as root.</span></span> <span data-ttu-id="61652-152">Aksi halde araç, hedef işlemle bağlantı kurmayacak.</span><span class="sxs-lookup"><span data-stu-id="61652-152">Otherwise, the tool will fail to establish a connection with the target process.</span></span>

## `dotnet-gcdump ps`

<span data-ttu-id="61652-153">GC dökümlerinin toplanabilecek DotNet süreçlerini listeler.</span><span class="sxs-lookup"><span data-stu-id="61652-153">Lists the dotnet processes that GC dumps can be collected for.</span></span>

### <a name="synopsis"></a><span data-ttu-id="61652-154">Özeti</span><span class="sxs-lookup"><span data-stu-id="61652-154">Synopsis</span></span>

```console
dotnet-gcdump ps
```

## `dotnet-gcdump report <gcdump_filename>`

<span data-ttu-id="61652-155">Önceden oluşturulmuş bir GC dökümünden veya çalışan bir işlemden rapor oluşturun ve öğesine yazın `stdout` .</span><span class="sxs-lookup"><span data-stu-id="61652-155">Generate a report from a previously generated GC dump or from a running process, and write to `stdout`.</span></span>

### <a name="synopsis"></a><span data-ttu-id="61652-156">Özeti</span><span class="sxs-lookup"><span data-stu-id="61652-156">Synopsis</span></span>

```console
dotnet-gcdump report [-h|--help] [-p|--process-id <pid>] [-t|--report-type <HeapStat>]
```

### <a name="options"></a><span data-ttu-id="61652-157">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="61652-157">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="61652-158">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="61652-158">Shows command-line help.</span></span>

- **`-p|--process-id <pid>`**

  <span data-ttu-id="61652-159">GC dökümünü toplanacak işlem KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="61652-159">The process ID to collect the GC dump from.</span></span>

- **`-t|--report-type <HeapStat>`**

  <span data-ttu-id="61652-160">Oluşturulacak raporun türü.</span><span class="sxs-lookup"><span data-stu-id="61652-160">The type of report to generate.</span></span> <span data-ttu-id="61652-161">Kullanılabilir seçenekler: heapstat (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="61652-161">Available options: heapstat (default).</span></span>

## <a name="troubleshoot"></a><span data-ttu-id="61652-162">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="61652-162">Troubleshoot</span></span>

- <span data-ttu-id="61652-163">Gcdump içinde tür bilgisi yok.</span><span class="sxs-lookup"><span data-stu-id="61652-163">There is no type information in the gcdump.</span></span>

   <span data-ttu-id="61652-164">.NET Core 3,1 ' den önce, EventPipe ile çağrıldığında gcdumps arasında bir tür önbelleğinin temizlenmediği bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="61652-164">Prior to .NET Core 3.1, there was an issue where a type cache was not cleared between gcdumps when they were invoked with EventPipe.</span></span> <span data-ttu-id="61652-165">Bu, ikinci ve sonraki gcdumps için gönderilmemiş tür bilgilerinin belirlenmesi için gereken olaylara neden oldu.</span><span class="sxs-lookup"><span data-stu-id="61652-165">This resulted in the events needed for determining type information not being sent for the second and subsequent gcdumps.</span></span> <span data-ttu-id="61652-166">Bu, .NET Core 3,1-preview2 ' de düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="61652-166">This was fixed in .NET Core 3.1-preview2.</span></span>

- <span data-ttu-id="61652-167">COM ve statik türler GC dökümünde değildir.</span><span class="sxs-lookup"><span data-stu-id="61652-167">COM and static types aren't in the GC dump.</span></span>

   <span data-ttu-id="61652-168">.NET Core 3,1-preview2 öncesinde, GC dökümü EventPipe aracılığıyla çağrıldığında statik ve COM türlerinin gönderilmediği bir sorun oluştu.</span><span class="sxs-lookup"><span data-stu-id="61652-168">Prior to .NET Core 3.1-preview2, there was an issue where static and COM types weren't sent when the GC dump was invoked via EventPipe.</span></span> <span data-ttu-id="61652-169">Bu, .NET Core 3,1-preview2 ' de düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="61652-169">This has been fixed in .NET Core 3.1-preview2.</span></span>
