---
title: DotNet tool güncelleştirme komutu - .NET Core CLI
description: Dotnet aracı güncelleştirme komut belirtilen .NET Core genel aracı makinenizde güncelleştirir.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 90b0dc91f74d890420dc7185642aa89100cadba8
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389478"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="6fa3d-103">DotNet aracı güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="6fa3d-103">dotnet tool update</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="6fa3d-104">Ad</span><span class="sxs-lookup"><span data-stu-id="6fa3d-104">Name</span></span>

<span data-ttu-id="6fa3d-105">`dotnet tool update` -Güncelleştirmeleri belirtilen [.NET Core genel aracı](global-tools.md) makinenizde.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-105">`dotnet tool update` - Updates the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6fa3d-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="6fa3d-106">Synopsis</span></span>

```console
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="6fa3d-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6fa3d-107">Description</span></span>

<span data-ttu-id="6fa3d-108">`dotnet tool update` Komutu, paketin en son kararlı sürüme makinenizde .NET Core genel Araçları'nı güncelleştirmek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-108">The `dotnet tool update` command provides a way for you to update .NET Core Global Tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="6fa3d-109">Komut kaldırır ve etkili bir şekilde güncelleştirirken bir aracı yükler.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-109">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="6fa3d-110">Komutunu kullanmak için ya da bir araç kullanarak kullanıcı genelinde yükleme güncelleştirmek istediğiniz belirtmeniz gerekir `--global` nerede yolunu belirtin veya seçeneği kullanılarak yüklenen aracı `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-110">To use the command, you either have to specify that you want to update a tool from a user-wide installation using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="6fa3d-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="6fa3d-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="6fa3d-112">.NET Core genel güncelleştirme için Aracı'nı içeren NuGet paket adı/kimliği.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-112">Name/ID of the NuGet package that contains the .NET Core Global Tool to update.</span></span> <span data-ttu-id="6fa3d-113">Paket adını kullanarak bulabilirsiniz [dotnet araç listesi](dotnet-tool-list.md) komutu.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-113">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="6fa3d-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="6fa3d-114">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="6fa3d-115">Yükleme sırasında kullanmak üzere ek bir NuGet paket kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-115">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="6fa3d-116">NuGet yapılandırma (*nuget.config*) dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-116">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="6fa3d-117">Belirtir [hedef Framework'ü](../../standard/frameworks.md) araç için güncelleştirilecek.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-117">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

`-g|--global`

<span data-ttu-id="6fa3d-118">Güncelleştirme için kullanıcı genelinde aracı olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-118">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="6fa3d-119">İle birleştirilemez `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="6fa3d-120">Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-120">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="6fa3d-121">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-121">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="6fa3d-122">Genel aracı yüklendiği konum belirtir.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-122">Specifies the location where the Global Tool is installed.</span></span> <span data-ttu-id="6fa3d-123">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-123">PATH can be absolute or relative.</span></span> <span data-ttu-id="6fa3d-124">İle birleştirilemez `--global` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-124">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="6fa3d-125">Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--global` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-125">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="6fa3d-126">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6fa3d-127">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-127">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="6fa3d-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="6fa3d-128">Examples</span></span>

<span data-ttu-id="6fa3d-129">Güncelleştirmeleri [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracı:</span><span class="sxs-lookup"><span data-stu-id="6fa3d-129">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool update -g dotnetsay`

<span data-ttu-id="6fa3d-130">Güncelleştirmeleri [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracı, belirli bir Windows klasöründe bulunur:</span><span class="sxs-lookup"><span data-stu-id="6fa3d-130">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Windows folder:</span></span>

`dotnet tool update dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="6fa3d-131">Güncelleştirmeleri [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracı, belirli bir Linux/macOS klasöründe bulunur:</span><span class="sxs-lookup"><span data-stu-id="6fa3d-131">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Linux/macOS folder:</span></span>

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="6fa3d-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6fa3d-132">See also</span></span>

* [<span data-ttu-id="6fa3d-133">.NET core Araçları Genel</span><span class="sxs-lookup"><span data-stu-id="6fa3d-133">.NET Core Global Tools</span></span>](global-tools.md)