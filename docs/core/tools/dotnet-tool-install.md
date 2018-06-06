---
title: DotNet aracı yükleme komutunu - .NET Core CLI
description: Dotnet araç belirtilen .NET Core genel aracı komut yükler makinenize yükleyin.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: f3068848910d6672a10ecfb639bac8e18a72818d
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34697293"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="7c408-103">DotNet aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="7c408-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="7c408-104">Ad</span><span class="sxs-lookup"><span data-stu-id="7c408-104">Name</span></span>

<span data-ttu-id="7c408-105">`dotnet tool install` -Yükler belirtilen [.NET Core genel aracı](global-tools.md) makinenizde.</span><span class="sxs-lookup"><span data-stu-id="7c408-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7c408-106">Özet</span><span class="sxs-lookup"><span data-stu-id="7c408-106">Synopsis</span></span>

```
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="7c408-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c408-107">Description</span></span>

<span data-ttu-id="7c408-108">`dotnet tool install` Komutu, makinenizde .NET Core genel araçları yüklemeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c408-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="7c408-109">Komutunu kullanmak için ya da kullanıcı genelinde yükleme kullanarak istediğiniz belirtmek zorunda `--global` seçeneği veya kullanarak yüklemek için bir yol belirtin `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7c408-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="7c408-110">Genel araçları yüklü aşağıdaki dizinlerindeki varsayılan olarak belirttiğiniz zaman `-g` (veya `--global`) seçeneği:</span><span class="sxs-lookup"><span data-stu-id="7c408-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="7c408-111">İŞLETİM SİSTEMİ</span><span class="sxs-lookup"><span data-stu-id="7c408-111">OS</span></span>          | <span data-ttu-id="7c408-112">Yol</span><span class="sxs-lookup"><span data-stu-id="7c408-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="7c408-113">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="7c408-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="7c408-114">Windows</span><span class="sxs-lookup"><span data-stu-id="7c408-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="7c408-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="7c408-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="7c408-116">.NET Core genel yüklemek için Aracı'nı içeren NuGet paketi adı/kimliği.</span><span class="sxs-lookup"><span data-stu-id="7c408-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="7c408-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="7c408-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="7c408-118">Yükleme sırasında kullanmak için ek bir NuGet paketi kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="7c408-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="7c408-119">NuGet yapılandırması (*nuget.config*) kullanmak üzere bir dosya.</span><span class="sxs-lookup"><span data-stu-id="7c408-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="7c408-120">Belirtir [hedef framework](../../standard/frameworks.md) için Aracı'nı yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="7c408-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="7c408-121">Varsayılan olarak, .NET Core SDK en uygun hedef Framework'ü seçmek çalışır.</span><span class="sxs-lookup"><span data-stu-id="7c408-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="7c408-122">Yükleme kullanıcı geniş olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c408-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="7c408-123">Birleştirilemez `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7c408-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="7c408-124">Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7c408-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="7c408-125">Komutu için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="7c408-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="7c408-126">Genel aracın yükleneceği konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="7c408-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="7c408-127">YOL, mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c408-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="7c408-128">YOL yoksa, komut onu oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="7c408-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="7c408-129">Birleştirilemez `--global` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7c408-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="7c408-130">Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--global` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="7c408-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="7c408-131">Komutun ayrıntı düzeyi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="7c408-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="7c408-132">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="7c408-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="7c408-133">Yüklemek için aracı sürümü.</span><span class="sxs-lookup"><span data-stu-id="7c408-133">The version of the tool to install.</span></span> <span data-ttu-id="7c408-134">Varsayılan olarak, en son kararlı Paket sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="7c408-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="7c408-135">Önizleme veya aracın eski sürümlerini yüklemek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="7c408-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="7c408-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="7c408-136">Examples</span></span>

<span data-ttu-id="7c408-137">Yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel araç varsayılan konumda:</span><span class="sxs-lookup"><span data-stu-id="7c408-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="7c408-138">Yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracını kullanarak belirli bir Windows klasörü:</span><span class="sxs-lookup"><span data-stu-id="7c408-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="7c408-139">Yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) belirli bir Linux/macOS klasördeki genel aracı:</span><span class="sxs-lookup"><span data-stu-id="7c408-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="7c408-140">2.0.0 sürümünü yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracı:</span><span class="sxs-lookup"><span data-stu-id="7c408-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="7c408-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c408-141">See also</span></span>

[<span data-ttu-id="7c408-142">.NET core genel araçları</span><span class="sxs-lookup"><span data-stu-id="7c408-142">.NET Core Global Tools</span></span>](global-tools.md)