---
title: dotnet nuget listesi kaynak komutu
description: Dotnet nuget listesi kaynak komutu, NuGet yapılandırma dosyalarınızdaki tüm varolan kaynakları listeler.
ms.date: 03/20/2020
ms.openlocfilehash: 8b14413949bd60ddeed977d19eec9bb99982da70
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463550"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="87e49-103">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="87e49-103">dotnet nuget list source</span></span>

<span data-ttu-id="87e49-104">**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="87e49-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="87e49-105">Adı</span><span class="sxs-lookup"><span data-stu-id="87e49-105">Name</span></span>

<span data-ttu-id="87e49-106">`dotnet nuget list source`- Tüm yapılandırılan NuGet kaynaklarını listeler.</span><span class="sxs-lookup"><span data-stu-id="87e49-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="87e49-107">Özet</span><span class="sxs-lookup"><span data-stu-id="87e49-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a><span data-ttu-id="87e49-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87e49-108">Description</span></span>

<span data-ttu-id="87e49-109">Komut, `dotnet nuget list source` NuGet yapılandırma dosyalarınızdaki tüm varolan kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="87e49-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="87e49-110">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="87e49-110">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="87e49-111">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="87e49-111">The NuGet configuration file.</span></span> <span data-ttu-id="87e49-112">Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87e49-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="87e49-113">Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="87e49-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="87e49-114">Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.</span><span class="sxs-lookup"><span data-stu-id="87e49-114">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format [Detailed|Short]`**

  <span data-ttu-id="87e49-115">Liste komutu çıktısının `Detailed` biçimi: (varsayılan) ve `Short`.</span><span class="sxs-lookup"><span data-stu-id="87e49-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="87e49-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="87e49-116">Examples</span></span>

- <span data-ttu-id="87e49-117">Geçerli dizinden yapılandırılan kaynakları listele:</span><span class="sxs-lookup"><span data-stu-id="87e49-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="87e49-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87e49-118">See also</span></span>

- [<span data-ttu-id="87e49-119">NuGet.config dosyalarındaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="87e49-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="87e49-120">kaynaklar komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="87e49-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
