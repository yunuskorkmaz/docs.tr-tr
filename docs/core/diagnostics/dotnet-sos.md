---
title: DotNet-sos-.NET Core
description: DotNet-sos komut satırı aracını yükleme ve kullanma.
ms.date: 08/26/2020
ms.openlocfilehash: 3ce7ca79bbc2c72958d395e9d312e3001ec9fbf8
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598353"
---
# <a name="sos-installer-dotnet-sos"></a><span data-ttu-id="1b52c-103">SOS yükleyicisi (DotNet-sos)</span><span class="sxs-lookup"><span data-stu-id="1b52c-103">SOS installer (dotnet-sos)</span></span>

<span data-ttu-id="1b52c-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="1b52c-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="install-dotnet-sos"></a><span data-ttu-id="1b52c-105">DotNet 'yi yükler-sos</span><span class="sxs-lookup"><span data-stu-id="1b52c-105">Install dotnet-sos</span></span>

<span data-ttu-id="1b52c-106">NuGet paketinin en son sürümünü yüklemek için `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos) [DotNet aracı install](../tools/dotnet-tool-install.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="1b52c-106">To install the latest release version of the `dotnet-sos` [NuGet package](https://www.nuget.org/packages/dotnet-sos), use the [dotnet tool install](../tools/dotnet-tool-install.md) command:</span></span>

```dotnetcli
dotnet tool install -g dotnet-sos
```

## <a name="synopsis"></a><span data-ttu-id="1b52c-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="1b52c-107">Synopsis</span></span>

```console
dotnet-sos [-h|--help] [options] [command]]
```

## <a name="description"></a><span data-ttu-id="1b52c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b52c-108">Description</span></span>

<span data-ttu-id="1b52c-109">`dotnet-sos`Küresel araç, Windows üzerinde WinDbg/CDB ve Linux ve MacOS 'ta lldb gibi yerel hata ayıklayıcılarından [yönetilen .NET Core durumunun incelemesinin](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) yapılmasına izin veren [sos hata ayıklayıcı uzantısını](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) da yüklüyor.</span><span class="sxs-lookup"><span data-stu-id="1b52c-109">The `dotnet-sos` global tool installs the [SOS debugger extension](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) allowing [inspection of managed .NET Core state](https://github.com/dotnet/diagnostics/blob/master/documentation/sos-debugging-extension.md) from native debuggers like WinDbg/cdb on Windows and lldb on Linux and MacOS.</span></span> <span data-ttu-id="1b52c-110">Windows hata ayıklayıcı 'nın (>= sürüm 10.0.18317.1001) (WinDbg veya CDB) son sürümlerinin SOS 'yi Microsoft uzantı galerisinden otomatik olarak yükleytiğine, bu nedenle aracı aracılığıyla SOS 'in yüklenmesi `dotnet-sos` yalnızca Linux ve MacOS 'ta veya daha eski hata ayıklama araçları kullanılıyorsa Windows 'da gereklidir.</span><span class="sxs-lookup"><span data-stu-id="1b52c-110">Note that recent versions of the Windows Debugger (>= version 10.0.18317.1001 of WinDbg or cdb) will load SOS automatically from the Microsoft extension gallery, so installing SOS via the `dotnet-sos` tool is only needed on Linux and MacOS or on Windows if using older debugging tools.</span></span>

## <a name="options"></a><span data-ttu-id="1b52c-111">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1b52c-111">Options</span></span>

- **`--version`**

  <span data-ttu-id="1b52c-112">Sürüm bilgilerini görüntüler.</span><span class="sxs-lookup"><span data-stu-id="1b52c-112">Displays version information.</span></span>

- **`-h|--help`**

  <span data-ttu-id="1b52c-113">Komut satırı yardımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="1b52c-113">Shows command-line help.</span></span>

## <a name="dotnet-sos-install"></a><span data-ttu-id="1b52c-114">DotNet-sos yüklemesi</span><span class="sxs-lookup"><span data-stu-id="1b52c-114">dotnet-sos install</span></span>

<span data-ttu-id="1b52c-115">.NET Core işlemlerinde hata ayıklama kullanımı için [SOS uzantısını yerel olarak](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) kurar.</span><span class="sxs-lookup"><span data-stu-id="1b52c-115">Installs the [SOS extension locally](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) for use debugging .NET Core processes.</span></span> <span data-ttu-id="1b52c-116">MacOS ve Linux 'ta, uzantısının lldb başlatması sırasında otomatik olarak yüklenmesi için. lldbinit dosyası güncelleştirilecektir.</span><span class="sxs-lookup"><span data-stu-id="1b52c-116">On MacOS and Linux, the .lldbinit file will be updated so that the extension automatically loads at lldb startup.</span></span> <span data-ttu-id="1b52c-117">Daha eski hata ayıklama araçları (< Version 10.0.18317.1001) ile Windows 'a SOS yüklüyorsanız, hata ayıklayıcıda çalıştırarak, uzantıyı WinDbg veya CDB 'de el ile yüklemeniz gerekir `.load %USERPROFILE%\.dotnet\sos\sos.dll` .</span><span class="sxs-lookup"><span data-stu-id="1b52c-117">If installing SOS on Windows with older debugging tools (< version 10.0.18317.1001), you will need to manually load the extension in WinDbg or cdb by running `.load %USERPROFILE%\.dotnet\sos\sos.dll` in the debugger.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1b52c-118">Özeti</span><span class="sxs-lookup"><span data-stu-id="1b52c-118">Synopsis</span></span>

```console
dotnet-sos install
```

## <a name="dotnet-sos-uninstall"></a><span data-ttu-id="1b52c-119">DotNet-sos kaldır</span><span class="sxs-lookup"><span data-stu-id="1b52c-119">dotnet-sos uninstall</span></span>

<span data-ttu-id="1b52c-120">[SOS uzantısını](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) kaldırır ve Linux veya MacOS 'ta ise lldb yapılandırmasından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1b52c-120">Uninstalls the [SOS extension](https://docs.microsoft.com/dotnet/framework/tools/sos-dll-sos-debugging-extension) and, if on Linux or MacOS, removes it from lldb configuration.</span></span>

### <a name="synopsis"></a><span data-ttu-id="1b52c-121">Özeti</span><span class="sxs-lookup"><span data-stu-id="1b52c-121">Synopsis</span></span>

```console
dotnet-sos uninstall
```
