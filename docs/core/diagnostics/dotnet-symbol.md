---
title: DotNet-symbol Tanılama aracı-.NET CLı
description: .NET dökümlerinde ve mini dökümlerinde hata ayıklamak için gereken dosyaları indirmek için DotNet-symbol CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 5cc304a3917921a964ceb61bc2c58e942b0baa85
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102105329"
---
# <a name="symbol-downloader-dotnet-symbol"></a><span data-ttu-id="4baa4-103">Sembol yükleyici (DotNet-Symbol)</span><span class="sxs-lookup"><span data-stu-id="4baa4-103">Symbol downloader (dotnet-symbol)</span></span>

<span data-ttu-id="4baa4-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="4baa4-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="4baa4-105">Yükleme</span><span class="sxs-lookup"><span data-stu-id="4baa4-105">Install</span></span>

<span data-ttu-id="4baa4-106">NuGet paketinin en son sürümünü yüklemek için `dotnet-symbol` [](https://www.nuget.org/packages/dotnet-symbol) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="4baa4-106">To install the latest release version of the `dotnet-symbol` [NuGet package](https://www.nuget.org/packages/dotnet-symbol), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install --global dotnet-symbol
```

## <a name="synopsis"></a><span data-ttu-id="4baa4-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="4baa4-107">Synopsis</span></span>

```console
dotnet-symbol [-h|--help] [options] <FILES>
```

## <a name="description"></a><span data-ttu-id="4baa4-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4baa4-108">Description</span></span>

<span data-ttu-id="4baa4-109">`dotnet-symbol`Genel araç, çekirdek dökümlerinde ve mini dökümlerinde hata ayıklamak için gereken dosyaları (semboller, dac, modüller vb.) indirir.</span><span class="sxs-lookup"><span data-stu-id="4baa4-109">The `dotnet-symbol` global tool downloads files (symbols, DAC, modules, etc.) needed for debugging core dumps and minidumps.</span></span> <span data-ttu-id="4baa4-110">Bu, başka bir makinede yakalanan dökümlerinin hata ayıklaması sırasında yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="4baa4-110">This can be useful when debugging dumps captured on another machine.</span></span> <span data-ttu-id="4baa4-111">`dotnet-symbol` , dökümünü çözümlemek için gereken modülleri ve sembolleri indirebilir.</span><span class="sxs-lookup"><span data-stu-id="4baa4-111">`dotnet-symbol` can download modules and symbols needed to analyze the dump.</span></span>

## <a name="options"></a><span data-ttu-id="4baa4-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="4baa4-112">Options</span></span>

- **`--microsoft-symbol-server`**

  <span data-ttu-id="4baa4-113">' http://msdl.microsoft.com/download/symbols ' Sembol sunucusu yolu ekleyin (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="4baa4-113">Add 'http://msdl.microsoft.com/download/symbols' symbol server path (default).</span></span>

- **`--server-path <symbol server path>`**

  <span data-ttu-id="4baa4-114">Sunucu yoluna bir sembol sunucusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4baa4-114">Add a symbol server to the server path.</span></span>

- **`authenticated-server-path <pat> <server path>`**

  <span data-ttu-id="4baa4-115">Bir kişisel erişim belirteci (PAT) kullanarak sunucu yoluna kimliği doğrulanmış bir sembol sunucusu ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4baa4-115">Add an authenticated symbol server to the server path using a personal access token (PAT).</span></span>

- **`--cache-directory <file cache directory>`**

  <span data-ttu-id="4baa4-116">Önbellek dizini ekler.</span><span class="sxs-lookup"><span data-stu-id="4baa4-116">Adds a cache directory.</span></span>

- **`--recurse-subdirectories`**

  <span data-ttu-id="4baa4-117">Giriş dosyalarını tüm alt dizinlerde işle.</span><span class="sxs-lookup"><span data-stu-id="4baa4-117">Process input files in all subdirectories.</span></span>

- **`--host-only`**

  <span data-ttu-id="4baa4-118">Yalnızca, çekirdek dökümlerini yüklemek için gereken ana bilgisayar programını (DotNet) indirin.</span><span class="sxs-lookup"><span data-stu-id="4baa4-118">Download only the host program (that is, dotnet) that lldb needs for loading core dumps.</span></span>

- **`--symbols`**

  <span data-ttu-id="4baa4-119">Sembol dosyalarını (. pdb,. dbg,. Dwarf) indirin.</span><span class="sxs-lookup"><span data-stu-id="4baa4-119">Download symbol files (.pdb, .dbg, .dwarf).</span></span>

- **`--modules`**

  <span data-ttu-id="4baa4-120">Modül dosyalarını (. dll,. so,. dylib) indirin.</span><span class="sxs-lookup"><span data-stu-id="4baa4-120">Download the module files (.dll, .so, .dylib).</span></span>

- **`--debugging`**

  <span data-ttu-id="4baa4-121">Özel hata ayıklama modüllerini (DAC, DBI, SOS) indirin.</span><span class="sxs-lookup"><span data-stu-id="4baa4-121">Download the special debugging modules (DAC, DBI, SOS).</span></span>

- **`--windows-pdbs`**

  <span data-ttu-id="4baa4-122">Taşınabilir pdb 'leri de kullanılabilir olduğunda Windows pdb 'leri indirmeye zorlayın.</span><span class="sxs-lookup"><span data-stu-id="4baa4-122">Force the downloading of the Windows PDBs when Portable PDBs are also available.</span></span>

- **`-o, --output <output directory>`**

  <span data-ttu-id="4baa4-123">Çıkış dizinini ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="4baa4-123">Set the output directory.</span></span> <span data-ttu-id="4baa4-124">Aksi takdirde, giriş dosyasının yanına yazın (varsayılan).</span><span class="sxs-lookup"><span data-stu-id="4baa4-124">Otherwise, write next to the input file (default).</span></span>

- **`-d, --diagnostics`**

  <span data-ttu-id="4baa4-125">Tanılama çıkışını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="4baa4-125">Enable diagnostic output.</span></span>

- **`-h|--help`**

  <span data-ttu-id="4baa4-126">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="4baa4-126">Shows command-line help.</span></span>

## <a name="download-symbols"></a><span data-ttu-id="4baa4-127">Sembolleri indir</span><span class="sxs-lookup"><span data-stu-id="4baa4-127">Download symbols</span></span>

<span data-ttu-id="4baa4-128">`dotnet-symbol`Bir döküm dosyasına karşı çalıştırmak, varsayılan olarak, yönetilen derlemeler dahil olmak üzere dökümdeki hataları ayıklamak için gereken tüm modülleri, sembolleri ve dac/DBı dosyalarını indirir.</span><span class="sxs-lookup"><span data-stu-id="4baa4-128">Running `dotnet-symbol` against a dump file will, by default, download all the modules, symbols, and DAC/DBI files needed to debug the dump including the managed assemblies.</span></span> <span data-ttu-id="4baa4-129">SOS artık gerektiğinde sembolleri indirebildiğinden, çoğu Linux çekirdek dökümü yalnızca Konak (DotNet) ve hata ayıklama modülleriyle lldb kullanılarak analiz edilebilir.</span><span class="sxs-lookup"><span data-stu-id="4baa4-129">Because SOS can now download symbols when needed, most Linux core dumps can be analyzed using lldb with only the host (dotnet) and debugging modules.</span></span> <span data-ttu-id="4baa4-130">Lldb çalıştırmasında bir çekirdek dökümünü tanılamak için gerekli olan bu dosyaları almak için:</span><span class="sxs-lookup"><span data-stu-id="4baa4-130">To get these files necessary for diagnosing a core dump with lldb run:</span></span>

```console
dotnet-symbol --host-only --debugging <dump file path>
```

## <a name="troubleshoot"></a><span data-ttu-id="4baa4-131">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="4baa4-131">Troubleshoot</span></span>

- <span data-ttu-id="4baa4-132">sembol indirilirken 404 bulunamadı.</span><span class="sxs-lookup"><span data-stu-id="4baa4-132">404 Not Found while downloading symbols.</span></span>

   <span data-ttu-id="4baa4-133">Sembol indirme yalnızca resmi [Web sitesi](https://dotnet.microsoft.com/download/dotnet) gibi resmi kanallar aracılığıyla elde edilen resmi .NET Core çalışma zamanı sürümleri ve [DotNet yükleme betiklerindeki varsayılan kaynaklar](../tools/dotnet-install-script.md)için desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4baa4-133">Symbol download is only supported for official .NET Core runtime versions acquired through official channels such as [the official web site](https://dotnet.microsoft.com/download/dotnet) and the [default sources in the dotnet installation scripts](../tools/dotnet-install-script.md).</span></span> <span data-ttu-id="4baa4-134">Hata ayıklama dosyalarını karşıdan yüklerken 404 hatası, döküm dosyasının yerel olarak veya belirli bir Linux dışından oluşturulmuş bir .NET Core çalışma zamanı ile oluşturulduğunu veya arşiv Linux gibi topluluk sitelerini gösteriyor olabilir.</span><span class="sxs-lookup"><span data-stu-id="4baa4-134">A 404 error while downloading debugging files may indicate that the dump was created with a .NET Core runtime from another source, such as one built from source locally or for a particular Linux distro, or from community sites like archlinux.</span></span> <span data-ttu-id="4baa4-135">Bu gibi durumlarda, hata ayıklama için gereken dosya (DotNet, libcoreclr.so ve libmscordaccore.so) bu kaynaklardan veya döküm dosyasının oluşturulduğu ortamdan kopyalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="4baa4-135">In such cases, file necessary for debugging (dotnet, libcoreclr.so, and libmscordaccore.so) should be copied from those sources or from the environment the dump file was created in.</span></span>

## <a name="see-also"></a><span data-ttu-id="4baa4-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4baa4-136">See also</span></span>

* [<span data-ttu-id="4baa4-137">Semboller ile hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="4baa4-137">Debugging with symbols</span></span>](/windows/win32/dxtecharts/debugging-with-symbols)
* [<span data-ttu-id="4baa4-138">Taşınabilir pdb 'leri</span><span class="sxs-lookup"><span data-stu-id="4baa4-138">Portable PDBs</span></span>](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md)
