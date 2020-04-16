---
title: dotnet nuget etkinleştirmek kaynak komutu
description: Dotnet nuget enable kaynak komutu NuGet yapılandırma dosyalarınızda varolan bir kaynağı etkinleştirin.
ms.date: 03/20/2020
ms.openlocfilehash: 38fb5917361bd7952fef9c31ed897fb81f005155
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463555"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="a5a6d-103">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="a5a6d-103">dotnet nuget enable source</span></span>

<span data-ttu-id="a5a6d-104">**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="a5a6d-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a5a6d-105">Adı</span><span class="sxs-lookup"><span data-stu-id="a5a6d-105">Name</span></span>

<span data-ttu-id="a5a6d-106">`dotnet nuget enable source`- Bir NuGet kaynağını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="a5a6d-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a5a6d-107">Özet</span><span class="sxs-lookup"><span data-stu-id="a5a6d-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a><span data-ttu-id="a5a6d-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a5a6d-108">Description</span></span>

<span data-ttu-id="a5a6d-109">Komut, `dotnet nuget enable source` NuGet yapılandırma dosyalarınızda varolan bir kaynağı etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="a5a6d-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="a5a6d-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="a5a6d-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="a5a6d-111">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="a5a6d-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="a5a6d-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="a5a6d-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="a5a6d-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="a5a6d-113">The NuGet configuration file.</span></span> <span data-ttu-id="a5a6d-114">Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5a6d-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="a5a6d-115">Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="a5a6d-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="a5a6d-116">Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.</span><span class="sxs-lookup"><span data-stu-id="a5a6d-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="a5a6d-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="a5a6d-117">Examples</span></span>

- <span data-ttu-id="a5a6d-118">Adı olan bir `mySource`kaynağı etkinleştirin:</span><span class="sxs-lookup"><span data-stu-id="a5a6d-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="a5a6d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5a6d-119">See also</span></span>

- [<span data-ttu-id="a5a6d-120">NuGet.config dosyalarındaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="a5a6d-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="a5a6d-121">kaynaklar komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="a5a6d-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
