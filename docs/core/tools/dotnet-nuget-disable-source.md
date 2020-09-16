---
title: DotNet NuGet kaynak komutunu devre dışı bırak
description: DotNet NuGet kaynak komutu, NuGet yapılandırma dosyalarınızda var olan bir kaynağı devre dışı bırakır.
ms.date: 03/20/2020
ms.openlocfilehash: af37a6589cebaf0501ee5647ebadb83125d0f56e
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537957"
---
# <a name="dotnet-nuget-disable-source"></a><span data-ttu-id="b39ef-103">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="b39ef-103">dotnet nuget disable source</span></span>

<span data-ttu-id="b39ef-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="b39ef-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b39ef-105">Name</span><span class="sxs-lookup"><span data-stu-id="b39ef-105">Name</span></span>

<span data-ttu-id="b39ef-106">`dotnet nuget disable source` -Bir NuGet kaynağını devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="b39ef-106">`dotnet nuget disable source` - Disable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b39ef-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="b39ef-107">Synopsis</span></span>

```dotnetcli
dotnet nuget disable source <NAME> [--configfile <FILE>]

dotnet nuget disable source -h|--help
```

## <a name="description"></a><span data-ttu-id="b39ef-108">Description</span><span class="sxs-lookup"><span data-stu-id="b39ef-108">Description</span></span>

<span data-ttu-id="b39ef-109">`dotnet nuget disable source`Komut, NuGet yapılandırma dosyalarınızda var olan bir kaynağı devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="b39ef-109">The `dotnet nuget disable source` command disables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="b39ef-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="b39ef-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="b39ef-111">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="b39ef-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="b39ef-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="b39ef-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="b39ef-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="b39ef-113">The NuGet configuration file.</span></span> <span data-ttu-id="b39ef-114">Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="b39ef-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="b39ef-115">Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="b39ef-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="b39ef-116">Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="b39ef-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="b39ef-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b39ef-117">Examples</span></span>

- <span data-ttu-id="b39ef-118">Şu ada sahip bir kaynağı devre dışı bırak `mySource` :</span><span class="sxs-lookup"><span data-stu-id="b39ef-118">Disable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="b39ef-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b39ef-119">See also</span></span>

- [<span data-ttu-id="b39ef-120">NuGet.config dosyalardaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="b39ef-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="b39ef-121">Sources komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="b39ef-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
