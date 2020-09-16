---
title: DotNet NuGet kaynağı Kaldır komutu
description: DotNet NuGet Remove Source komutu, var olan bir kaynağı NuGet yapılandırma dosyalarınızda kaldırır.
ms.date: 03/20/2020
ms.openlocfilehash: b5575c31c0008d6e3e5a2e52906a076614217dd0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537904"
---
# <a name="dotnet-nuget-remove-source"></a><span data-ttu-id="1b59d-103">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="1b59d-103">dotnet nuget remove source</span></span>

<span data-ttu-id="1b59d-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="1b59d-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1b59d-105">Name</span><span class="sxs-lookup"><span data-stu-id="1b59d-105">Name</span></span>

<span data-ttu-id="1b59d-106">`dotnet nuget remove source` -Bir NuGet kaynağını kaldırın.</span><span class="sxs-lookup"><span data-stu-id="1b59d-106">`dotnet nuget remove source` - Remove a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1b59d-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="1b59d-107">Synopsis</span></span>

```dotnetcli
dotnet nuget remove source <NAME> [--configfile <FILE>]

dotnet nuget remove source -h|--help
```

## <a name="description"></a><span data-ttu-id="1b59d-108">Description</span><span class="sxs-lookup"><span data-stu-id="1b59d-108">Description</span></span>

<span data-ttu-id="1b59d-109">`dotnet nuget remove source`Komut varolan bir kaynağı NuGet yapılandırma dosyalarından kaldırır.</span><span class="sxs-lookup"><span data-stu-id="1b59d-109">The `dotnet nuget remove source` command removes an existing source from your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="1b59d-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="1b59d-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="1b59d-111">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="1b59d-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="1b59d-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1b59d-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="1b59d-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="1b59d-113">The NuGet configuration file.</span></span> <span data-ttu-id="1b59d-114">Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="1b59d-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="1b59d-115">Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="1b59d-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="1b59d-116">Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="1b59d-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="1b59d-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1b59d-117">Examples</span></span>

- <span data-ttu-id="1b59d-118">Şu ada sahip bir kaynağı Kaldır `mySource` :</span><span class="sxs-lookup"><span data-stu-id="1b59d-118">Remove a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="1b59d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b59d-119">See also</span></span>

- [<span data-ttu-id="1b59d-120">NuGet.config dosyalardaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="1b59d-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="1b59d-121">Sources komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="1b59d-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
