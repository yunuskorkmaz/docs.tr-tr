---
title: Linux dökümlerinin hatasını ayıklama
description: Bu makalede, Linux ortamlarından dökümleri nasıl toplayacağınızı ve analiz edeceğinizi öğreneceksiniz.
ms.date: 08/27/2020
ms.openlocfilehash: 94f923f2ec7b5fa20c2ebc9b83540094348dff03
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099152"
---
# <a name="debug-linux-dumps"></a><span data-ttu-id="4ee50-103">Linux dökümlerinin hatasını ayıklama</span><span class="sxs-lookup"><span data-stu-id="4ee50-103">Debug Linux dumps</span></span>

<span data-ttu-id="4ee50-104">**Bu makale şu şekilde geçerlidir: ✔️** .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="4ee50-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

## <a name="collect-dumps-on-linux"></a><span data-ttu-id="4ee50-105">Linux üzerinde dökümleri topla</span><span class="sxs-lookup"><span data-stu-id="4ee50-105">Collect dumps on Linux</span></span>

<span data-ttu-id="4ee50-106">Linux üzerinde dökümler toplamanın iki önerilen yolu [`dotnet-dump`](dotnet-dump.md) veya [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) araçlardır.</span><span class="sxs-lookup"><span data-stu-id="4ee50-106">The two recommended ways of collecting dumps on Linux are the [`dotnet-dump`](dotnet-dump.md) or [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) tools.</span></span>

### <a name="managed-dumps-with-dotnet-dump"></a><span data-ttu-id="4ee50-107">İle yönetilen dökümler `dotnet-dump`</span><span class="sxs-lookup"><span data-stu-id="4ee50-107">Managed dumps with `dotnet-dump`</span></span>

<span data-ttu-id="4ee50-108">[`dotnet-dump`](dotnet-dump.md)Aracın kullanımı basittir ve herhangi bir yerel hata ayıklayıcıya bağımlılığı yoktur.</span><span class="sxs-lookup"><span data-stu-id="4ee50-108">The [`dotnet-dump`](dotnet-dump.md) tool is simple to use, and does not have a dependency on any native debuggers.</span></span> <span data-ttu-id="4ee50-109">`dotnet-dump` geleneksel hata ayıklama araçlarının kullanılamadığı çok sayıda Linux platformunda (alp veya ARM32/ARM64 gibi) çalışmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4ee50-109">`dotnet-dump` works on a wide variety of Linux platforms (like Alpine or ARM32/ARM64) where traditional debugging tools may not be available.</span></span> <span data-ttu-id="4ee50-110">Ancak, `dotnet-dump` yalnızca yönetilen durumu yakalar, bu nedenle yerel koddaki hata ayıklama sorunları için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4ee50-110">However, `dotnet-dump` only captures managed state so it can't be used for debugging issues in native code.</span></span> <span data-ttu-id="4ee50-111">Tarafından toplanan dökümler, `dotnet-dump` dökümün oluşturulduğu işletim sistemi ve mimarili bir ortamda çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="4ee50-111">Dumps collected by `dotnet-dump` are analyzed in an environment with the same OS and architecture the dump was created on.</span></span> <span data-ttu-id="4ee50-112">[`dotnet-gcdump`](dotnet-gcdump.md)Araç yalnızca GC yığın bilgilerini yakalayan, ancak Windows üzerinde çözümlenebilecek dökümler üreten bir alternatif olarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ee50-112">The [`dotnet-gcdump`](dotnet-gcdump.md) tool can be used as an alternative that only captures GC heap information but produces dumps that can be analyzed on Windows.</span></span>

### <a name="core-dumps-with-createdump"></a><span data-ttu-id="4ee50-113">İle temel dökümler `createdump`</span><span class="sxs-lookup"><span data-stu-id="4ee50-113">Core dumps with `createdump`</span></span>

<span data-ttu-id="4ee50-114">`dotnet-dump`Yalnızca yönetilen dökümler oluşturan öğesine alternatif olarak, [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) hem yerel hem de yönetilen bilgileri içeren Linux üzerinde çekirdek dökümler oluşturmaya yönelik önerilen araçtır.</span><span class="sxs-lookup"><span data-stu-id="4ee50-114">As an alternative to `dotnet-dump`, which creates managed-only dumps, [`createdump`](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) is the recommended tool for creating core dumps on Linux containing both native and managed information.</span></span> <span data-ttu-id="4ee50-115">GDB veya gcore gibi diğer araçlar da temel dökümler oluşturmak için kullanılabilir ancak yönetilen hata ayıklama için gereken durumu kaçırabilir ve analiz sırasında "BILINMEYEN" tür veya işlev adlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4ee50-115">Other tools like gdb or gcore can also be used to create core dumps but may miss state needed for managed debugging, resulting in "UNKNOWN" type or function names during analysis.</span></span>

<span data-ttu-id="4ee50-116">`createdump`Araç .NET Core çalışma zamanı ile yüklenir ve libcoreclr.so ' nin yanında (genellikle "/usr/share/DotNet/Shared/Microsoft.NETCore.app/[Version]" içinde) bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="4ee50-116">The `createdump` tool is installed with the .NET Core runtime and can be found next to libcoreclr.so (typically in "/usr/share/dotnet/shared/Microsoft.NETCore.App/[version]").</span></span> <span data-ttu-id="4ee50-117">Araç, birincil bağımsız değişkeni olarak döküm toplamak için bir işlem KIMLIĞI alır ve toplanacak döküm türünü belirten isteğe bağlı parametreleri de alabilir (yığın içeren bir mini döküm varsayılandır).</span><span class="sxs-lookup"><span data-stu-id="4ee50-117">The tool takes a process ID to collect a dump from as its primary argument and can also take optional parameters specifying what kind of dump to collect (a minidump with heap is the default).</span></span> <span data-ttu-id="4ee50-118">Seçeneklere şunlar dahildir:</span><span class="sxs-lookup"><span data-stu-id="4ee50-118">Options include:</span></span>

- **`<input-filename>`**

  <span data-ttu-id="4ee50-119">Dönüştürülecek giriş izleme dosyası.</span><span class="sxs-lookup"><span data-stu-id="4ee50-119">Input trace file to be converted.</span></span> <span data-ttu-id="4ee50-120">*Trace. NetTrace* için varsayılanlar.</span><span class="sxs-lookup"><span data-stu-id="4ee50-120">Defaults to *trace.nettrace*.</span></span>

### <a name="options"></a><span data-ttu-id="4ee50-121">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="4ee50-121">Options</span></span>

- **`-f|--name <output-filename>`**

  <span data-ttu-id="4ee50-122">Döküm yazılacak dosya.</span><span class="sxs-lookup"><span data-stu-id="4ee50-122">The file to write the dump to.</span></span> <span data-ttu-id="4ee50-123">Varsayılan değer, hedef işlemin işlem KIMLIĞI olan% p olan '/tmp/coredump.%p '.</span><span class="sxs-lookup"><span data-stu-id="4ee50-123">Default is '/tmp/coredump.%p' where %p is the process ID of the target process.</span></span>

- **`-n|--normal`**

  <span data-ttu-id="4ee50-124">Mini döküm oluştur.</span><span class="sxs-lookup"><span data-stu-id="4ee50-124">Create a minidump.</span></span>

- **`-h|--withheap`**

  <span data-ttu-id="4ee50-125">Yığın ile bir mini döküm oluştur (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="4ee50-125">Create a minidump with heap (default).</span></span>

- **`-t|--triage`**

  <span data-ttu-id="4ee50-126">Önceliklendirme mini döküm dosyası oluşturma.</span><span class="sxs-lookup"><span data-stu-id="4ee50-126">Create a triage minidump.</span></span>

- **`-u|--full`**

  <span data-ttu-id="4ee50-127">Tam çekirdek dökümü oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4ee50-127">Create a full core dump.</span></span>

- **`-d|--diag`**

  <span data-ttu-id="4ee50-128">Tanılama iletilerini etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="4ee50-128">Enable diagnostic messages.</span></span>

<span data-ttu-id="4ee50-129">Çekirdek dökümlerinin toplanması, `SYS_PTRACE` özelliği ya da `createdump` sudo veya su ile çalıştırılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4ee50-129">Collecting core dumps requires either the `SYS_PTRACE` capability or that `createdump` be run with sudo or su.</span></span>

## <a name="analyze-dumps-on-linux"></a><span data-ttu-id="4ee50-130">Linux 'ta dökümleri çözümleme</span><span class="sxs-lookup"><span data-stu-id="4ee50-130">Analyze dumps on Linux</span></span>

<span data-ttu-id="4ee50-131">İle toplanan yönetilen dökümler `dotnet-dump` ve ile toplanan temel dökümler, `createdump` `dotnet-dump` komutu kullanılarak araçla analiz edilebilir `dotnet-dump analyze` .</span><span class="sxs-lookup"><span data-stu-id="4ee50-131">Both managed dumps collected with `dotnet-dump` and core dumps collected with `createdump` can be analyzed with the `dotnet-dump` tool using the `dotnet-dump analyze` command.</span></span> <span data-ttu-id="4ee50-132">, `dotnet dump` Dökümünü çözümleyen ortamın, dökümün yakalandığı ortamla aynı işletim sistemine ve mimariye sahip olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="4ee50-132">The `dotnet dump` requires that the environment analyzing the dump has the same OS and architecture as the environment the dump was captured in.</span></span>

<span data-ttu-id="4ee50-133">Alternatif olarak, hem yönetilen hem de yerel çerçevelerin analizine olanak tanıyan Linux üzerinde çekirdek dökümlerini çözümlemek için [Lldb](https://lldb.llvm.org/) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ee50-133">Alternatively, [LLDB](https://lldb.llvm.org/) can be used to analyze core dumps on Linux, which allows analysis of both managed and native frames.</span></span> <span data-ttu-id="4ee50-134">LLDB, yönetilen kodun hatalarını ayıklamak için SOS uzantısını kullanır.</span><span class="sxs-lookup"><span data-stu-id="4ee50-134">LLDB uses the SOS extension to debug managed code.</span></span> <span data-ttu-id="4ee50-135">[`dotnet-sos`](dotnet-sos.md)CLI Aracı, yönetilen kodda hata ayıklama için [birçok yararlı komuta](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) sahip sos 'yi yüklemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ee50-135">The [`dotnet-sos`](dotnet-sos.md) CLI tool can be used to install SOS, which has [many useful commands](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) for debugging managed code.</span></span> <span data-ttu-id="4ee50-136">.NET Core dökümlerini çözümlemek için, LLDB ve SOS, döküm oluşturulan ortamdan aşağıdaki .NET Core ikililerini gerektirir:</span><span class="sxs-lookup"><span data-stu-id="4ee50-136">In order to analyze .NET Core dumps, LLDB and SOS require the following .NET Core binaries from the environment the dump was created in:</span></span>

1. <span data-ttu-id="4ee50-137">libmscordaccore.so</span><span class="sxs-lookup"><span data-stu-id="4ee50-137">libmscordaccore.so</span></span>
2. <span data-ttu-id="4ee50-138">libcoreclr.so</span><span class="sxs-lookup"><span data-stu-id="4ee50-138">libcoreclr.so</span></span>
3. <span data-ttu-id="4ee50-139">DotNet (uygulamayı başlatmak için kullanılan ana bilgisayar)</span><span class="sxs-lookup"><span data-stu-id="4ee50-139">dotnet (the host used to launch the app)</span></span>

<span data-ttu-id="4ee50-140">Çoğu durumda, bu ikili dosyalar araç kullanılarak indirilebilir [`dotnet-symbol`](dotnet-symbol.md) .</span><span class="sxs-lookup"><span data-stu-id="4ee50-140">In most cases, these binaries can be downloaded using the [`dotnet-symbol`](dotnet-symbol.md) tool.</span></span> <span data-ttu-id="4ee50-141">Gerekli ikililer ile indirilemez `dotnet-symbol` (örneğin, kaynaktan oluşturulan özel bir .NET Core sürümü kullanılıyorsa), yukarıda listelenen dosyaları dökümün oluşturulduğu ortamdan kopyalamak gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4ee50-141">If the necessary binaries can't be downloaded with `dotnet-symbol` (for example, if a private version of .NET Core built from source was in use), it may be necessary to copy the files listed above from the environment the dump was created in.</span></span> <span data-ttu-id="4ee50-142">Dosyalar döküm dosyasının yanında bulunmuyorsa, ' `setclrpath <path>` den yüklenmesi gereken yolu ayarlamak ve `setsymbolserver -directory <path>` sembol dosyaları için aranacak yolu ayarlamak için lldb/sos komutunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4ee50-142">If the files aren't located next to the dump file, you can use the LLDB/SOS command `setclrpath <path>` to set the path they should be loaded from and `setsymbolserver -directory <path>` to set the path to look in for symbol files.</span></span>

<span data-ttu-id="4ee50-143">Gerekli dosyalar kullanılabilir olduğunda, hata ayıklaması yapılacak yürütülebilir dosya olarak DotNet ana bilgisayarı belirtilerek, döküm LLDB 'ye yüklenebilir:</span><span class="sxs-lookup"><span data-stu-id="4ee50-143">Once the necessary files are available, the dump can be loaded in LLDB by specifying the dotnet host as the executable to debug:</span></span>

```console
lldb --core <dump-file> <host-program>
```

<span data-ttu-id="4ee50-144">Yukarıdaki komut satırında, `<dump-file>` analiz edilecek döküm yoludur ve `<host-program>` .NET Core uygulamasını Başlatan yerel programdır.</span><span class="sxs-lookup"><span data-stu-id="4ee50-144">In the above command line, `<dump-file>` is the path of the dump to analyze and `<host-program>` is the native program that started the .NET Core application.</span></span> <span data-ttu-id="4ee50-145">`dotnet`Uygulama kendi kendine dahil olmadığı müddetçe genellikle ikili bir durumdur, bu durumda dll uzantısı olmayan uygulamanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="4ee50-145">This is typically the `dotnet` binary unless the app is self-contained, in which case it is the name of the application without the dll extension.</span></span>

<span data-ttu-id="4ee50-146">LLDB başladıktan sonra, `setsymbolserver` komutun doğru sembol konumunu işaret etmek için ( `setsymbolserver -ms` Microsoft 'un sembol sunucusunu kullanmak veya `setsymbolserver -directory <path>` yerel bir yol belirtmek için) kullanılması gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="4ee50-146">Once LLDB starts, it may be necessary to use the `setsymbolserver` command to point at the correct symbol location (`setsymbolserver -ms` to use Microsoft's symbol server or `setsymbolserver -directory <path>` to specify a local path).</span></span> <span data-ttu-id="4ee50-147">Yerel semboller çalıştırılarak çalıştırılabilir `loadsymbols` .</span><span class="sxs-lookup"><span data-stu-id="4ee50-147">Native symbols can be loaded by running `loadsymbols`.</span></span> <span data-ttu-id="4ee50-148">Bu noktada, dökümünü çözümlemek için [sos komutları](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4ee50-148">At this point, [SOS commands](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) can be used to analyze the dump.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ee50-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ee50-149">See also</span></span>

- <span data-ttu-id="4ee50-150">, SOS uzantısını yükleme hakkında daha fazla bilgi için [DotNet-sos](dotnet-sos.md) .</span><span class="sxs-lookup"><span data-stu-id="4ee50-150">[dotnet-sos](dotnet-sos.md) for more details on installing the SOS extension.</span></span>
- <span data-ttu-id="4ee50-151">[DotNet-](dotnet-symbol.md) sembol indirme aracını yükleme ve kullanma hakkında daha fazla ayrıntı için.</span><span class="sxs-lookup"><span data-stu-id="4ee50-151">[dotnet-symbol](dotnet-symbol.md) for more details on installing and using the symbol download tool.</span></span>
- <span data-ttu-id="4ee50-152">Yararlı bir SSS dahil olmak üzere hata ayıklama hakkında daha fazla ayrıntı için [.NET Core tanılama deposu](https://github.com/dotnet/diagnostics/blob/master/documentation/) .</span><span class="sxs-lookup"><span data-stu-id="4ee50-152">[.NET Core diagnostics repo](https://github.com/dotnet/diagnostics/blob/master/documentation/) for more details on debugging, including a useful FAQ.</span></span>
- <span data-ttu-id="4ee50-153">Lldb 'yi Linux veya Mac 'e yükleme yönergeleri için [yükleme](https://github.com/dotnet/diagnostics/blob/master/documentation/sos.md#getting-lldb) .</span><span class="sxs-lookup"><span data-stu-id="4ee50-153">[Installing LLDB](https://github.com/dotnet/diagnostics/blob/master/documentation/sos.md#getting-lldb) for instructions on installing LLDB on Linux or Mac.</span></span>
