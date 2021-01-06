---
title: DotNet-sos Tanılama aracı-.NET CLı
description: Windows ve Linux 'ta yerel hata ayıklayıcıları ile kullanılan SOS hata ayıklayıcı uzantısını yönetmek için DotNet-sos CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 09e8228c47bdc632bccf3c9ad2296d55fe420060
ms.sourcegitcommit: c0b803bffaf101e12f071faf94ca21b46d04ff30
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/24/2020
ms.locfileid: "97765013"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="e5fcb-103">SOS yükleyicisi (DotNet-sos)</span><span class="sxs-lookup"><span data-stu-id="e5fcb-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="e5fcb-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="e5fcb-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="e5fcb-105">Yükleme</span><span class="sxs-lookup"><span data-stu-id="e5fcb-105">Install</span></span>

<span data-ttu-id="e5fcb-106">İndirmek ve yüklemek için iki yol vardır `dotnet-sos` :</span><span class="sxs-lookup"><span data-stu-id="e5fcb-106">There are two ways to download and install `dotnet-sos`:</span></span>

- <span data-ttu-id="e5fcb-107">**DotNet genel aracı:**</span><span class="sxs-lookup"><span data-stu-id="e5fcb-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="e5fcb-108">NuGet paketinin en son sürümünü yüklemek için `dotnet-sos` [](https://www.nuget.org/packages/dotnet-sos) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="e5fcb-108">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- <span data-ttu-id="e5fcb-109">**Doğrudan indirme:**</span><span class="sxs-lookup"><span data-stu-id="e5fcb-109">**Direct download:**</span></span>

  <span data-ttu-id="e5fcb-110">Platformunuzla eşleşen araç yürütülebilirini indirin:</span><span class="sxs-lookup"><span data-stu-id="e5fcb-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="e5fcb-111">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="e5fcb-111">OS</span></span>  | <span data-ttu-id="e5fcb-112">Platform</span><span class="sxs-lookup"><span data-stu-id="e5fcb-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="e5fcb-113">Windows</span><span class="sxs-lookup"><span data-stu-id="e5fcb-113">Windows</span></span> | <span data-ttu-id="e5fcb-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [ARM](https://aka.ms/dotnet-sos/win-arm) \| [ARM-x64](https://aka.ms/dotnet-sos/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="e5fcb-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span></span> |
  | <span data-ttu-id="e5fcb-115">macOS</span><span class="sxs-lookup"><span data-stu-id="e5fcb-115">macOS</span></span>   | [<span data-ttu-id="e5fcb-116">x64</span><span class="sxs-lookup"><span data-stu-id="e5fcb-116">x64</span></span>](https://aka.ms/dotnet-sos/osx-x64) |
  | <span data-ttu-id="e5fcb-117">Linux</span><span class="sxs-lookup"><span data-stu-id="e5fcb-117">Linux</span></span>   | <span data-ttu-id="e5fcb-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [ARM](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="e5fcb-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="e5fcb-119">Özeti</span><span class="sxs-lookup"><span data-stu-id="e5fcb-119">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="e5fcb-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e5fcb-120">Description</span></span>

<span data-ttu-id="e5fcb-121">`dotnet-sos`Genel araç, [sos hata ayıklayıcı uzantısını](sos-debugging-extension.md)yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-121">The `dotnet-sos` global tool installs the [SOS debugger extension](sos-debugging-extension.md).</span></span> <span data-ttu-id="e5fcb-122">Bu uzantı, lldb ve WinDbg gibi yerel hata ayıklayıcılarından yönetilen .NET Core durumunu incelemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-122">This extension lets you inspect managed .NET Core state from native debuggers like lldb and windbg.</span></span>

> [!NOTE]
> <span data-ttu-id="e5fcb-123">Aracı aracılığıyla SOS yükleme `dotnet-sos` yalnızca Linux veya macOS 'ta gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-123">Installing SOS via the `dotnet-sos` tool is only needed on Linux or macOS.</span></span>  <span data-ttu-id="e5fcb-124">Ayrıca, daha eski hata ayıklama araçları kullanıyorsanız Windows 'da da gerekli olabilir.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-124">It may also be needed on Windows if you're using older debugging tools.</span></span> <span data-ttu-id="e5fcb-125">[Windows hata ayıklayıcının](/windows-hardware/drivers/debugger/debugger-download-tools) son sürümleri (>= 10.0.18317.1001 of WinDbg veya CDB) Microsoft uzantı galerisinden otomatik olarak yük sos.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-125">Recent versions of the [Windows Debugger](/windows-hardware/drivers/debugger/debugger-download-tools) (>= version 10.0.18317.1001 of WinDbg or cdb) load SOS automatically from the Microsoft extension gallery.</span></span>  

## <a name="options"></a><span data-ttu-id="e5fcb-126">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e5fcb-126">Options</span></span>

- **`--version`**

  <span data-ttu-id="e5fcb-127">Sürüm bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-127">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="e5fcb-128">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-128">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="e5fcb-129">DotNet-sos yüklemesi</span><span class="sxs-lookup"><span data-stu-id="e5fcb-129">dotnet-sos install</span></span>

<span data-ttu-id="e5fcb-130">.NET Core işlemlerinde hata ayıklamak için [SOS uzantısını](sos-debugging-extension.md) yerel olarak kurar.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-130">Installs the [SOS extension](sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="e5fcb-131">MacOS ve Linux 'ta, uzantısının lldb başlatması sırasında otomatik olarak yüklenmesi için *. lldbinit* dosyası güncelleştirilecektir.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-131">On macOS and Linux, the *.lldbinit* file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="e5fcb-132">Windows 'a eski hata ayıklama araçlarıyla SOS yüklüyorsanız (sürüm 10.0.18317.1001 ' den önce), hata ayıklayıcıda çalıştırarak, uzantıyı WinDbg veya CDB 'ye el ile yüklemeniz gerekir `.load %USERPROFILE%\.dotnet\sos\sos.dll` .</span><span class="sxs-lookup"><span data-stu-id="e5fcb-132">If you're installing SOS on Windows with older debugging tools (prior to version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e5fcb-133">Özeti</span><span class="sxs-lookup"><span data-stu-id="e5fcb-133">Synopsis</span></span>

```console
dotnet-sos install [--architecture <arch>]
```

### <a name="options"></a><span data-ttu-id="e5fcb-134">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e5fcb-134">Options</span></span>

- **`--architecture <arch>`**

  <span data-ttu-id="e5fcb-135">Yüklenecek SOS ikililerinin işlemci mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-135">Specifies the processor architecture of the SOS binaries to install.</span></span> <span data-ttu-id="e5fcb-136">Varsayılan olarak, `dotnet-sos` konak makinenin mimarisini yükleme.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-136">By default, `dotnet-sos` installs the architecture of the host machine.</span></span> <span data-ttu-id="e5fcb-137">DotNet konak mimarisinden farklı bir mimariye SOS yüklemek istediğinizde bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-137">Use this option when you want to install SOS for an architecture that's different from the dotnet host architecture.</span></span> <span data-ttu-id="e5fcb-138">Örneğin, bir Arm64 ana bilgisayardan Arm32 ikili dosyaları çalıştırıyorsanız, ile SOS 'i yüklemeniz gerekir `dotnet-sos install --architecture Arm` .</span><span class="sxs-lookup"><span data-stu-id="e5fcb-138">For example, if you're running Arm32 binaries from an Arm64 host, you will need to install SOS with `dotnet-sos install --architecture Arm`.</span></span>

  <span data-ttu-id="e5fcb-139">Aşağıdaki mimariler mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="e5fcb-139">The following architectures are available:</span></span>

  - `Arm`
  - `Arm64`
  - `X86`
  - `X64`

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="e5fcb-140">DotNet-sos kaldır</span><span class="sxs-lookup"><span data-stu-id="e5fcb-140">dotnet-sos uninstall</span></span>

<span data-ttu-id="e5fcb-141">[SOS uzantısını](sos-debugging-extension.md) kaldırır ve Linux ve MacOS 'ta, lldb yapılandırmasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e5fcb-141">Uninstalls the [SOS extension](sos-debugging-extension.md) and, on Linux and macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="e5fcb-142">Özeti</span><span class="sxs-lookup"><span data-stu-id="e5fcb-142">Synopsis</span></span>

```console
dotnet-sos uninstall
```
