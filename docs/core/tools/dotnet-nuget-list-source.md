---
title: DotNet NuGet liste kaynağı komutu
description: DotNet NuGet liste kaynağı komutu, NuGet yapılandırma dosyalarınızda var olan tüm kaynakları listeler.
ms.date: 03/20/2020
ms.openlocfilehash: 071061e32aa1bf888e197ec6bf97f4e4f6859f0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537905"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="1fb31-103">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="1fb31-103">dotnet nuget list source</span></span>

<span data-ttu-id="1fb31-104">**Bu makale şu şekilde geçerlidir:** ✔️ .NET Core 3.1.200 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="1fb31-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="1fb31-105">Name</span><span class="sxs-lookup"><span data-stu-id="1fb31-105">Name</span></span>

<span data-ttu-id="1fb31-106">`dotnet nuget list source` -Tüm yapılandırılmış NuGet kaynaklarını listeler.</span><span class="sxs-lookup"><span data-stu-id="1fb31-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1fb31-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="1fb31-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a><span data-ttu-id="1fb31-108">Description</span><span class="sxs-lookup"><span data-stu-id="1fb31-108">Description</span></span>

<span data-ttu-id="1fb31-109">`dotnet nuget list source`Komut, NuGet yapılandırma dosyalarınızda var olan tüm kaynakları listeler.</span><span class="sxs-lookup"><span data-stu-id="1fb31-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="1fb31-110">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="1fb31-110">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="1fb31-111">NuGet yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="1fb31-111">The NuGet configuration file.</span></span> <span data-ttu-id="1fb31-112">Belirtilmişse, yalnızca bu dosyadaki ayarlar kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="1fb31-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="1fb31-113">Belirtilmemişse, geçerli dizinden yapılandırma dosyalarının hiyerarşisi kullanılacaktır.</span><span class="sxs-lookup"><span data-stu-id="1fb31-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="1fb31-114">Daha fazla bilgi için bkz. [ortak NuGet yapılandırması](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="1fb31-114">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format [Detailed|Short]`**

  <span data-ttu-id="1fb31-115">List komutunun çıktısının biçimi: `Detailed` (varsayılan) ve `Short` .</span><span class="sxs-lookup"><span data-stu-id="1fb31-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="1fb31-116">Örnekler</span><span class="sxs-lookup"><span data-stu-id="1fb31-116">Examples</span></span>

- <span data-ttu-id="1fb31-117">Geçerli dizinden yapılandırılmış kaynakları Listele:</span><span class="sxs-lookup"><span data-stu-id="1fb31-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="1fb31-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1fb31-118">See also</span></span>

- [<span data-ttu-id="1fb31-119">NuGet.config dosyalardaki paket kaynak bölümleri</span><span class="sxs-lookup"><span data-stu-id="1fb31-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="1fb31-120">Sources komutu (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="1fb31-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
