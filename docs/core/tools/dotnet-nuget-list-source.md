---
title: dotnet nuget listesi kaynak komutu
description: Dotnet nuget listesi kaynak komutu, NuGet yapılandırma dosyalarınızdaki tüm varolan kaynakları listeler.
ms.date: 03/20/2020
ms.openlocfilehash: 4d7bc3dbd3ab5eb14c1ebf592044b685d28355cd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148577"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="adb87-103">dotnet nuget listesi kaynak</span><span class="sxs-lookup"><span data-stu-id="adb87-103">dotnet nuget list source</span></span>

<span data-ttu-id="adb87-104">**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="adb87-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="adb87-105">Adı</span><span class="sxs-lookup"><span data-stu-id="adb87-105">Name</span></span>

<span data-ttu-id="adb87-106">`dotnet nuget list source`- Tüm yapılandırılan NuGet kaynaklarını listeler.</span><span class="sxs-lookup"><span data-stu-id="adb87-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="adb87-107">Özet</span><span class="sxs-lookup"><span data-stu-id="adb87-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format] [--configfile]
dotnet nuget list source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="adb87-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="adb87-108">Description</span></span>

<span data-ttu-id="adb87-109">Komut, `dotnet nuget list source` NuGet yapılandırma dosyalarınızdaki tüm varolan kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="adb87-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="adb87-110">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="adb87-110">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="adb87-111">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="adb87-111">The NuGet configuration file.</span></span> <span data-ttu-id="adb87-112">Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="adb87-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="adb87-113">Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="adb87-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="adb87-114">Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.</span><span class="sxs-lookup"><span data-stu-id="adb87-114">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format`**

  <span data-ttu-id="adb87-115">Liste komutu çıktısının `Detailed` biçimi: (varsayılan) ve `Short`.</span><span class="sxs-lookup"><span data-stu-id="adb87-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="adb87-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="adb87-116">Examples</span></span>

- <span data-ttu-id="adb87-117">Geçerli dizinden yapılandırılan kaynakları listele:</span><span class="sxs-lookup"><span data-stu-id="adb87-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="adb87-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="adb87-118">See also</span></span>

- [<span data-ttu-id="adb87-119">NuGet.config dosyalarındaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="adb87-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="adb87-120">kaynaklar komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="adb87-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
