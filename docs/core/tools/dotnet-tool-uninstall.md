---
title: DotNet Aracı kaldırma komutu
description: DotNet Aracı kaldırma komutu, belirtilen .NET Core küresel aracını makinenizden kaldırır.
ms.date: 05/29/2018
ms.openlocfilehash: 033753f44464e78b826e908e0b6cdf276da8a179
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117545"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="abc78-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="abc78-103">dotnet tool uninstall</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="abc78-104">Ad</span><span class="sxs-lookup"><span data-stu-id="abc78-104">Name</span></span>

<span data-ttu-id="abc78-105">`dotnet tool uninstall`-Belirtilen [.NET Core küresel aracını](global-tools.md) makinenizden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="abc78-105">`dotnet tool uninstall` - Uninstalls the specified [.NET Core Global Tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="abc78-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="abc78-106">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="abc78-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="abc78-107">Description</span></span>

<span data-ttu-id="abc78-108">Komut `dotnet tool uninstall` , makinenizden .NET Core küresel araçlarını kaldırmanız için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="abc78-108">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core Global Tools from your machine.</span></span> <span data-ttu-id="abc78-109">Komutunu kullanmak için, `--global` seçeneğini kullanarak bir Kullanıcı genelindeki aracı kaldırmak istediğinizi belirtmeniz veya `--tool-path` seçeneği kullanılarak aracın yüklendiği konuma bir yol belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="abc78-109">To use the command, you either have to specify that you want to remove a user-wide tool using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="abc78-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="abc78-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="abc78-111">Kaldırılacak .NET Core küresel aracını içeren NuGet paketinin adı/KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="abc78-111">Name/ID of the NuGet package that contains the .NET Core Global Tool to uninstall.</span></span> <span data-ttu-id="abc78-112">[DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak paket adını bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="abc78-112">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="abc78-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="abc78-113">Options</span></span>

`-g|--global`

<span data-ttu-id="abc78-114">Kaldırılacak aracın Kullanıcı genelindeki bir yüklemeden olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="abc78-114">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="abc78-115">`--tool-path` Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="abc78-115">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="abc78-116">Bu seçeneği belirtmezseniz, `--tool-path` seçeneğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="abc78-116">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="abc78-117">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="abc78-117">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="abc78-118">Genel aracının kaldırılacağı konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="abc78-118">Specifies the location where to uninstall the Global Tool.</span></span> <span data-ttu-id="abc78-119">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="abc78-119">PATH can be absolute or relative.</span></span> <span data-ttu-id="abc78-120">`--global` Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="abc78-120">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="abc78-121">Bu seçeneği belirtmezseniz, `--global` seçeneğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="abc78-121">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="abc78-122">Örnekler</span><span class="sxs-lookup"><span data-stu-id="abc78-122">Examples</span></span>

<span data-ttu-id="abc78-123">[Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel aracını kaldırır:</span><span class="sxs-lookup"><span data-stu-id="abc78-123">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool uninstall -g dotnetsay`

<span data-ttu-id="abc78-124">[Dotnetsöyleme](https://www.nuget.org/packages/dotnetsay/) genel aracını belirli bir Windows klasöründen kaldırır:</span><span class="sxs-lookup"><span data-stu-id="abc78-124">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Windows folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="abc78-125">[Dotnetsöyleyin](https://www.nuget.org/packages/dotnetsay/) küresel aracını belirli bir Linux/MacOS klasöründen kaldırır:</span><span class="sxs-lookup"><span data-stu-id="abc78-125">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Linux/macOS folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="abc78-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abc78-126">See also</span></span>

- [<span data-ttu-id="abc78-127">.NET Core küresel araçları</span><span class="sxs-lookup"><span data-stu-id="abc78-127">.NET Core Global Tools</span></span>](global-tools.md)
