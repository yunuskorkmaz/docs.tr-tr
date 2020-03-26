---
title: dotnet nuget kaldırmak kaynak komutu
description: Kaynak komutunu kaldır komutu dotnet nuget'i NuGet yapılandırma dosyalarınızdan varolan bir kaynağı kaldırır.
ms.date: 03/20/2020
ms.openlocfilehash: 65c97b98ab50121fb4ebc184da65f021c16e0634
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148542"
---
# <a name="dotnet-nuget-remove-source"></a><span data-ttu-id="3174b-103">dotnet nuget kaynak kaldırmak</span><span class="sxs-lookup"><span data-stu-id="3174b-103">dotnet nuget remove source</span></span>

<span data-ttu-id="3174b-104">**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="3174b-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3174b-105">Adı</span><span class="sxs-lookup"><span data-stu-id="3174b-105">Name</span></span>

<span data-ttu-id="3174b-106">`dotnet nuget remove source`- NuGet kaynağını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="3174b-106">`dotnet nuget remove source` - Remove a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3174b-107">Özet</span><span class="sxs-lookup"><span data-stu-id="3174b-107">Synopsis</span></span>

```dotnetcli
dotnet nuget remove source <NAME> [--configfile]
dotnet nuget remove source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="3174b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3174b-108">Description</span></span>

<span data-ttu-id="3174b-109">Komut, `dotnet nuget remove source` Varolan bir kaynağı NuGet yapılandırma dosyalarınızdan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3174b-109">The `dotnet nuget remove source` command removes an existing source from your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="3174b-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="3174b-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="3174b-111">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="3174b-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="3174b-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="3174b-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="3174b-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="3174b-113">The NuGet configuration file.</span></span> <span data-ttu-id="3174b-114">Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3174b-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="3174b-115">Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="3174b-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="3174b-116">Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.</span><span class="sxs-lookup"><span data-stu-id="3174b-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="3174b-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="3174b-117">Examples</span></span>

- <span data-ttu-id="3174b-118">Adı olan bir `mySource`kaynağı kaldırın:</span><span class="sxs-lookup"><span data-stu-id="3174b-118">Remove a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="3174b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3174b-119">See also</span></span>

- [<span data-ttu-id="3174b-120">NuGet.config dosyalarındaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="3174b-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="3174b-121">kaynaklar komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="3174b-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
