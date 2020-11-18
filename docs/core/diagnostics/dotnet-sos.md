---
title: DotNet-sos Tanılama aracı-.NET CLı
description: Windows ve Linux 'ta yerel hata ayıklayıcıları ile kullanılan SOS hata ayıklayıcı uzantısını yönetmek için DotNet-sos CLı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 11/17/2020
ms.openlocfilehash: 59512c42a778f68bb3cd092dc854dcc727fd2881
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825448"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="58a94-103">SOS yükleyicisi (DotNet-sos)</span><span class="sxs-lookup"><span data-stu-id="58a94-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="58a94-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="58a94-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install"></a><span data-ttu-id="58a94-105">Yükleme</span><span class="sxs-lookup"><span data-stu-id="58a94-105">Install</span></span>

<span data-ttu-id="58a94-106">İndirmek ve yüklemek için iki yol vardır `dotnet-sos` :</span><span class="sxs-lookup"><span data-stu-id="58a94-106">There are two ways to download and install `dotnet-sos`:</span></span>

- <span data-ttu-id="58a94-107">**DotNet genel aracı:**</span><span class="sxs-lookup"><span data-stu-id="58a94-107">**dotnet global tool:**</span></span>

  <span data-ttu-id="58a94-108">NuGet paketinin en son sürümünü yüklemek için `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="58a94-108">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

  ```dotnetcli
  dotnet tool install --global dotnet-sos
  ```

- <span data-ttu-id="58a94-109">**Doğrudan indirme:**</span><span class="sxs-lookup"><span data-stu-id="58a94-109">**Direct download:**</span></span>

  <span data-ttu-id="58a94-110">Platformunuzla eşleşen araç yürütülebilirini indirin:</span><span class="sxs-lookup"><span data-stu-id="58a94-110">Download the tool executable that matches your platform:</span></span>

  | <span data-ttu-id="58a94-111">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="58a94-111">OS</span></span>  | <span data-ttu-id="58a94-112">Platform</span><span class="sxs-lookup"><span data-stu-id="58a94-112">Platform</span></span> |
  | --- | -------- |
  | <span data-ttu-id="58a94-113">Windows</span><span class="sxs-lookup"><span data-stu-id="58a94-113">Windows</span></span> | <span data-ttu-id="58a94-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [ARM](https://aka.ms/dotnet-sos/win-arm) \| [ARM-x64](https://aka.ms/dotnet-sos/win-arm64)</span><span class="sxs-lookup"><span data-stu-id="58a94-114">[x86](https://aka.ms/dotnet-sos/win-x86) \| [x64](https://aka.ms/dotnet-sos/win-x64) \| [arm](https://aka.ms/dotnet-sos/win-arm) \| [arm-x64](https://aka.ms/dotnet-sos/win-arm64)</span></span> |
  | <span data-ttu-id="58a94-115">macOS</span><span class="sxs-lookup"><span data-stu-id="58a94-115">macOS</span></span>   | [<span data-ttu-id="58a94-116">x64</span><span class="sxs-lookup"><span data-stu-id="58a94-116">x64</span></span>](https://aka.ms/dotnet-sos/osx-x64) |
  | <span data-ttu-id="58a94-117">Linux</span><span class="sxs-lookup"><span data-stu-id="58a94-117">Linux</span></span>   | <span data-ttu-id="58a94-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [ARM](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [MUSL-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [MUSL-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span><span class="sxs-lookup"><span data-stu-id="58a94-118">[x64](https://aka.ms/dotnet-sos/linux-x64) \| [arm](https://aka.ms/dotnet-sos/linux-arm) \| [arm64](https://aka.ms/dotnet-sos/linux-arm64) \| [musl-x64](https://aka.ms/dotnet-sos/linux-musl-x64) \| [musl-arm64](https://aka.ms/dotnet-sos/linux-musl-arm64)</span></span> |

## <a name="synopsis"></a><span data-ttu-id="58a94-119">Özeti</span><span class="sxs-lookup"><span data-stu-id="58a94-119">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="58a94-120">Açıklama</span><span class="sxs-lookup"><span data-stu-id="58a94-120">Description</span></span>

<span data-ttu-id="58a94-121">`dotnet-sos`Küresel araç, Windows üzerinde WinDbg/CDB ve Linux ve macOS 'ta lldb gibi yerel hata ayıklayıcılarından [yönetilen .NET Core durumunun incelemesinin](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) yapılmasına izin veren [sos hata ayıklayıcı uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) da yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="58a94-121">The `dotnet-sos` global tool installs the [SOS debugger extension](../../framework/tools/sos-dll-sos-debugging-extension.md) allowing [inspection of managed .NET Core state](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) from native debuggers like WinDbg/cdb on Windows and lldb on Linux and macOS.</span></span> <span data-ttu-id="58a94-122">Windows hata ayıklayıcının son sürümleri (>= WinDbg veya CDB 'nin 10.0.18317.1001 sürümü), SOS 'yi Microsoft uzantı Galerisi 'nden otomatik olarak yükler, bu nedenle aracı aracılığıyla SOS yüklemek `dotnet-sos` yalnızca Linux ve macOS 'ta veya daha eski hata ayıklama araçları kullanılıyorsa Windows 'ta gereklidir.</span><span class="sxs-lookup"><span data-stu-id="58a94-122">Recent versions of the Windows Debugger (>= version 10.0.18317.1001 of WinDbg or cdb) will load SOS automatically from the Microsoft extension gallery, so installing SOS via the `dotnet-sos` tool is only needed on Linux and macOS or on Windows if using older debugging tools.</span></span>

## <a name="options"></a><span data-ttu-id="58a94-123">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="58a94-123">Options</span></span>

- **`--version`**

  <span data-ttu-id="58a94-124">Sürüm bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="58a94-124">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="58a94-125">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="58a94-125">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="58a94-126">DotNet-sos yüklemesi</span><span class="sxs-lookup"><span data-stu-id="58a94-126">dotnet-sos install</span></span>

<span data-ttu-id="58a94-127">.NET Core işlemlerinde hata ayıklamak için [SOS uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) yerel olarak kurar.</span><span class="sxs-lookup"><span data-stu-id="58a94-127">Installs the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="58a94-128">MacOS ve Linux 'ta, uzantısının lldb başlatması sırasında otomatik olarak yüklenmesi için. lldbinit dosyası güncelleştirilecektir.</span><span class="sxs-lookup"><span data-stu-id="58a94-128">On macOS and Linux, the .lldbinit file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="58a94-129">Daha eski hata ayıklama araçları (< Version 10.0.18317.1001) ile Windows 'a SOS yüklüyorsanız, hata ayıklayıcıda çalıştırarak, uzantıyı WinDbg veya CDB 'de el ile yüklemeniz gerekir `.load %USERPROFILE%\.dotnet\sos\sos.dll` .</span><span class="sxs-lookup"><span data-stu-id="58a94-129">If installing SOS on Windows with older debugging tools (< version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="58a94-130">Özeti</span><span class="sxs-lookup"><span data-stu-id="58a94-130">Synopsis</span></span>

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="58a94-131">DotNet-sos kaldır</span><span class="sxs-lookup"><span data-stu-id="58a94-131">dotnet-sos uninstall</span></span>

<span data-ttu-id="58a94-132">[SOS uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) kaldırır ve Linux veya MacOS 'ta ise lldb yapılandırmasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="58a94-132">Uninstalls the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) and, if on Linux or macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="58a94-133">Özeti</span><span class="sxs-lookup"><span data-stu-id="58a94-133">Synopsis</span></span>

```console
dotnet-sos uninstall
```
