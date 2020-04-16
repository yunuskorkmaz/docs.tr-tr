---
title: dotnet nuget devre dışı kaynak komutu
description: Dotnet nuget devre dışı kaynak komutu NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı devre dışı kılabilir.
ms.date: 03/20/2020
ms.openlocfilehash: 54acb40b1944eaff347107e8f3439578ec8e0f3c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463574"
---
# <a name="dotnet-nuget-disable-source"></a><span data-ttu-id="05e4c-103">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="05e4c-103">dotnet nuget disable source</span></span>

<span data-ttu-id="05e4c-104">**Bu makale şu şekildedir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="05e4c-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="05e4c-105">Adı</span><span class="sxs-lookup"><span data-stu-id="05e4c-105">Name</span></span>

<span data-ttu-id="05e4c-106">`dotnet nuget disable source`- Bir NuGet kaynağını devre dışı kalın.</span><span class="sxs-lookup"><span data-stu-id="05e4c-106">`dotnet nuget disable source` - Disable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="05e4c-107">Özet</span><span class="sxs-lookup"><span data-stu-id="05e4c-107">Synopsis</span></span>

```dotnetcli
dotnet nuget disable source <NAME> [--configfile <FILE>]

dotnet nuget disable source -h|--help
```

## <a name="description"></a><span data-ttu-id="05e4c-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="05e4c-108">Description</span></span>

<span data-ttu-id="05e4c-109">Komut, `dotnet nuget disable source` NuGet yapılandırma dosyalarınızdaki varolan bir kaynağı devre dışı kılabilir.</span><span class="sxs-lookup"><span data-stu-id="05e4c-109">The `dotnet nuget disable source` command disables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="05e4c-110">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="05e4c-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="05e4c-111">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="05e4c-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="05e4c-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="05e4c-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="05e4c-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="05e4c-113">The NuGet configuration file.</span></span> <span data-ttu-id="05e4c-114">Belirtilirse, yalnızca bu dosyadaki ayarlar kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05e4c-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="05e4c-115">Belirtilmemişse, geçerli dizindeki yapılandırma dosyaları hiyerarşisi kullanılır.</span><span class="sxs-lookup"><span data-stu-id="05e4c-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="05e4c-116">Daha fazla bilgi için [Ortak NuGet Yapılandırmaları'na](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior)bakın.</span><span class="sxs-lookup"><span data-stu-id="05e4c-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="05e4c-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="05e4c-117">Examples</span></span>

- <span data-ttu-id="05e4c-118">Adı `mySource`olan bir kaynağı devre dışı:</span><span class="sxs-lookup"><span data-stu-id="05e4c-118">Disable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="05e4c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05e4c-119">See also</span></span>

- [<span data-ttu-id="05e4c-120">NuGet.config dosyalarındaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="05e4c-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="05e4c-121">kaynaklar komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="05e4c-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
