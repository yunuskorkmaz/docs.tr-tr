---
title: DotNet NuGet kaynak komutunu etkinleştir
description: DotNet NuGet kaynak komutu, NuGet yapılandırma dosyalarınızda var olan bir kaynağı etkinleştirir.
ms.date: 03/20/2020
ms.openlocfilehash: b727844dd7d7cc82476e94a3f0ec4ecc6559d5ed
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537940"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="3aebc-103">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="3aebc-103">dotnet nuget enable source</span></span>

<span data-ttu-id="3aebc-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="3aebc-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3aebc-105">Name</span><span class="sxs-lookup"><span data-stu-id="3aebc-105">Name</span></span>

<span data-ttu-id="3aebc-106">`dotnet nuget enable source` -Bir NuGet kaynağını etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="3aebc-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3aebc-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="3aebc-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a><span data-ttu-id="3aebc-108">Description</span><span class="sxs-lookup"><span data-stu-id="3aebc-108">Description</span></span>

<span data-ttu-id="3aebc-109">`dotnet nuget enable source`Komut, NuGet yapılandırma dosyalarınızda var olan bir kaynağı mümkün bir şekilde sunar.</span><span class="sxs-lookup"><span data-stu-id="3aebc-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="3aebc-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="3aebc-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="3aebc-111">Kaynağın adı.</span><span class="sxs-lookup"><span data-stu-id="3aebc-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="3aebc-112">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="3aebc-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="3aebc-113">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="3aebc-113">The NuGet configuration file.</span></span> <span data-ttu-id="3aebc-114">Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="3aebc-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="3aebc-115">Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="3aebc-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="3aebc-116">Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="3aebc-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="3aebc-117">Örnekler</span><span class="sxs-lookup"><span data-stu-id="3aebc-117">Examples</span></span>

- <span data-ttu-id="3aebc-118">Şu ada sahip bir kaynağı etkinleştirin `mySource` :</span><span class="sxs-lookup"><span data-stu-id="3aebc-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="3aebc-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3aebc-119">See also</span></span>

- [<span data-ttu-id="3aebc-120">NuGet.config dosyalardaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="3aebc-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="3aebc-121">Sources komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="3aebc-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
