---
title: dotnet nuget devre dışı kaynak komutu
description: Dotnet nuget devre dışı kaynak komutu NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı devre dışı kılabilir.
ms.date: 03/20/2020
ms.openlocfilehash: 5aa16c842bcddeead180fdeec3d9dcdda33f7ed9
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148556"
---
# <a name="dotnet-nuget-disable-source"></a><span data-ttu-id="4fdfb-103">dotnet nuget devre dışı kaynak</span><span class="sxs-lookup"><span data-stu-id="4fdfb-103">dotnet nuget disable source</span></span>

<span data-ttu-id="4fdfb-104">**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="4fdfb-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="4fdfb-105">Adı</span><span class="sxs-lookup"><span data-stu-id="4fdfb-105">Name</span></span>

<span data-ttu-id="4fdfb-106">`dotnet nuget disable source`- Bir NuGet kaynağını devre dışı kalın.</span><span class="sxs-lookup"><span data-stu-id="4fdfb-106">`dotnet nuget disable source` - Disable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4fdfb-107">Özet</span><span class="sxs-lookup"><span data-stu-id="4fdfb-107">Synopsis</span></span>

```dotnetcli
dotnet nuget disable source <NAME> [--configfile]
dotnet nuget disable source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="4fdfb-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fdfb-108">Description</span></span>

<span data-ttu-id="4fdfb-109">Komut, `dotnet nuget disable source` NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="4fdfb-109">The `dotnet nuget disable source` command disables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="4fdfb-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="4fdfb-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="4fdfb-111">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="4fdfb-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="4fdfb-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="4fdfb-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="4fdfb-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="4fdfb-113">The NuGet configuration file.</span></span> <span data-ttu-id="4fdfb-114">Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4fdfb-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="4fdfb-115">Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="4fdfb-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="4fdfb-116">Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.</span><span class="sxs-lookup"><span data-stu-id="4fdfb-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="4fdfb-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="4fdfb-117">Examples</span></span>

- <span data-ttu-id="4fdfb-118">Adı `mySource`olan bir kaynağı devre dışı:</span><span class="sxs-lookup"><span data-stu-id="4fdfb-118">Disable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="4fdfb-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fdfb-119">See also</span></span>

- [<span data-ttu-id="4fdfb-120">NuGet.config dosyalarındaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="4fdfb-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="4fdfb-121">kaynaklar komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="4fdfb-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
