---
title: dotnet nuget etkinleştirmek kaynak komutu
description: Dotnet nuget enable kaynak komutu NuGet yapılandırma dosyalarınızda varolan bir kaynağı etkinleştirin.
ms.date: 03/20/2020
ms.openlocfilehash: 1f18e7db6a6c8631bb432676dd97dabfad5b0ab8
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148563"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="025bc-103">dotnet nuget etkinleştirmek kaynak</span><span class="sxs-lookup"><span data-stu-id="025bc-103">dotnet nuget enable source</span></span>

<span data-ttu-id="025bc-104">**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="025bc-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="025bc-105">Adı</span><span class="sxs-lookup"><span data-stu-id="025bc-105">Name</span></span>

<span data-ttu-id="025bc-106">`dotnet nuget enable source`- Bir NuGet kaynağını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="025bc-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="025bc-107">Özet</span><span class="sxs-lookup"><span data-stu-id="025bc-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile]
dotnet nuget enable source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="025bc-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="025bc-108">Description</span></span>

<span data-ttu-id="025bc-109">Komut, `dotnet nuget enable source` NuGet yapılandırma dosyalarınızda varolan bir kaynağı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="025bc-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="025bc-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="025bc-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="025bc-111">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="025bc-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="025bc-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="025bc-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="025bc-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="025bc-113">The NuGet configuration file.</span></span> <span data-ttu-id="025bc-114">Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="025bc-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="025bc-115">Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="025bc-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="025bc-116">Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.</span><span class="sxs-lookup"><span data-stu-id="025bc-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="025bc-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="025bc-117">Examples</span></span>

- <span data-ttu-id="025bc-118">Adı olan bir `mySource`kaynağı etkinleştirin:</span><span class="sxs-lookup"><span data-stu-id="025bc-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="025bc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="025bc-119">See also</span></span>

- [<span data-ttu-id="025bc-120">NuGet.config dosyalarındaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="025bc-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="025bc-121">kaynaklar komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="025bc-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
