---
title: DotNet-sos-.NET Core
description: DotNet-sos komut satırı aracını yüklemeyi ve kullanmayı öğrenin.
ms.date: 08/26/2020
ms.openlocfilehash: ba83105718909038ca56129ed8a5063aeff12e89
ms.sourcegitcommit: a69d548f90a03e105ee6701236c38390ecd9ccd1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90065090"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="c5964-103">SOS yükleyicisi (DotNet-sos)</span><span class="sxs-lookup"><span data-stu-id="c5964-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="c5964-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="c5964-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install-dotnet-sos"></a><span data-ttu-id="c5964-105">DotNet 'yi yükler-sos</span><span class="sxs-lookup"><span data-stu-id="c5964-105">Install dotnet-sos</span></span>

<span data-ttu-id="c5964-106">NuGet paketinin en son sürümünü yüklemek için `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="c5964-106">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-sos
```

## <a name="synopsis"></a><span data-ttu-id="c5964-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="c5964-107">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="c5964-108">Description</span><span class="sxs-lookup"><span data-stu-id="c5964-108">Description</span></span>

<span data-ttu-id="c5964-109">`dotnet-sos`Küresel araç, Windows üzerinde WinDbg/CDB ve Linux ve macOS 'ta lldb gibi yerel hata ayıklayıcılarından [yönetilen .NET Core durumunun incelemesinin](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) yapılmasına izin veren [sos hata ayıklayıcı uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) da yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="c5964-109">The `dotnet-sos` global tool installs the [SOS debugger extension](../../framework/tools/sos-dll-sos-debugging-extension.md) allowing [inspection of managed .NET Core state](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) from native debuggers like WinDbg/cdb on Windows and lldb on Linux and macOS.</span></span> <span data-ttu-id="c5964-110">Windows hata ayıklayıcının son sürümleri (>= WinDbg veya CDB 'nin 10.0.18317.1001 sürümü), SOS 'yi Microsoft uzantı Galerisi 'nden otomatik olarak yükler, bu nedenle aracı aracılığıyla SOS yüklemek `dotnet-sos` yalnızca Linux ve macOS 'ta veya daha eski hata ayıklama araçları kullanılıyorsa Windows 'ta gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c5964-110">Recent versions of the Windows Debugger (>= version 10.0.18317.1001 of WinDbg or cdb) will load SOS automatically from the Microsoft extension gallery, so installing SOS via the `dotnet-sos` tool is only needed on Linux and macOS or on Windows if using older debugging tools.</span></span>

## <a name="options"></a><span data-ttu-id="c5964-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="c5964-111">Options</span></span>

- **`--version`**

  <span data-ttu-id="c5964-112">Sürüm bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c5964-112">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="c5964-113">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c5964-113">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="c5964-114">DotNet-sos yüklemesi</span><span class="sxs-lookup"><span data-stu-id="c5964-114">dotnet-sos install</span></span>

<span data-ttu-id="c5964-115">.NET Core işlemlerinde hata ayıklamak için [SOS uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) yerel olarak kurar.</span><span class="sxs-lookup"><span data-stu-id="c5964-115">Installs the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) locally for debugging .NET Core processes.</span></span> <span data-ttu-id="c5964-116">MacOS ve Linux 'ta, uzantısının lldb başlatması sırasında otomatik olarak yüklenmesi için. lldbinit dosyası güncelleştirilecektir.</span><span class="sxs-lookup"><span data-stu-id="c5964-116">On macOS and Linux, the .lldbinit file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="c5964-117">Daha eski hata ayıklama araçları (< Version 10.0.18317.1001) ile Windows 'a SOS yüklüyorsanız, hata ayıklayıcıda çalıştırarak, uzantıyı WinDbg veya CDB 'de el ile yüklemeniz gerekir `.load %USERPROFILE%\.dotnet\sos\sos.dll` .</span><span class="sxs-lookup"><span data-stu-id="c5964-117">If installing SOS on Windows with older debugging tools (< version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="c5964-118">Özeti</span><span class="sxs-lookup"><span data-stu-id="c5964-118">Synopsis</span></span>

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="c5964-119">DotNet-sos kaldır</span><span class="sxs-lookup"><span data-stu-id="c5964-119">dotnet-sos uninstall</span></span>

<span data-ttu-id="c5964-120">[SOS uzantısını](../../framework/tools/sos-dll-sos-debugging-extension.md) kaldırır ve Linux veya MacOS 'ta ise lldb yapılandırmasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="c5964-120">Uninstalls the [SOS extension](../../framework/tools/sos-dll-sos-debugging-extension.md) and, if on Linux or macOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="c5964-121">Özeti</span><span class="sxs-lookup"><span data-stu-id="c5964-121">Synopsis</span></span>

```console
dotnet-sos uninstall
```
