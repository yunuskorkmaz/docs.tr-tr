---
title: DotNet aracı yükleme komutu
description: Dotnet araç belirtilen .NET Core genel aracı komut yükler makinenize yükleyin.
ms.date: 05/29/2018
ms.openlocfilehash: 1348eb1165c77376a885fdcbf094bd17b2aa3514
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563710"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="b40ba-103">DotNet aracı yükleme</span><span class="sxs-lookup"><span data-stu-id="b40ba-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="b40ba-104">Ad</span><span class="sxs-lookup"><span data-stu-id="b40ba-104">Name</span></span>

<span data-ttu-id="b40ba-105">`dotnet tool install` -Belirtilen yükler [.NET Core genel aracı](global-tools.md) makinenizde.</span><span class="sxs-lookup"><span data-stu-id="b40ba-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b40ba-106">Synopsis</span><span class="sxs-lookup"><span data-stu-id="b40ba-106">Synopsis</span></span>

```console
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="b40ba-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b40ba-107">Description</span></span>

<span data-ttu-id="b40ba-108">`dotnet tool install` Komutu, makinenizde .NET Core genel Araçları'nı yüklemek bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="b40ba-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="b40ba-109">Komutunu kullanmak için ya da kullanarak bir kullanıcı genelinde yükleme istediğinizi belirtmek zorunda `--global` kullanarak yüklemek için bir yol belirtin veya seçeneği `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b40ba-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="b40ba-110">Genel araçları yüklü aşağıdaki dizinlerindeki varsayılan olarak belirttiğinizde `-g` (veya `--global`) seçeneği:</span><span class="sxs-lookup"><span data-stu-id="b40ba-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="b40ba-111">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="b40ba-111">OS</span></span>          | <span data-ttu-id="b40ba-112">Yol</span><span class="sxs-lookup"><span data-stu-id="b40ba-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="b40ba-113">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="b40ba-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="b40ba-114">Windows</span><span class="sxs-lookup"><span data-stu-id="b40ba-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="b40ba-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="b40ba-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="b40ba-116">.NET Core genel yüklemek için aracı içeren NuGet paket adı/kimliği.</span><span class="sxs-lookup"><span data-stu-id="b40ba-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="b40ba-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="b40ba-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="b40ba-118">Yükleme sırasında kullanmak üzere ek bir NuGet paket kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="b40ba-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="b40ba-119">NuGet yapılandırma (*nuget.config*) dosyasını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b40ba-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="b40ba-120">Belirtir [hedef Framework'ü](../../standard/frameworks.md) için aracı yüklemek için.</span><span class="sxs-lookup"><span data-stu-id="b40ba-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="b40ba-121">Varsayılan olarak, .NET Core SDK'sını en uygun hedef Framework'ü seçmek çalışır.</span><span class="sxs-lookup"><span data-stu-id="b40ba-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="b40ba-122">Yükleme kullanıcı geniş olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b40ba-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="b40ba-123">İle birleştirilemez `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b40ba-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="b40ba-124">Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--tool-path` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b40ba-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="b40ba-125">Komut için kısa bir Yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="b40ba-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="b40ba-126">Genel aracı yükleneceği konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="b40ba-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="b40ba-127">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="b40ba-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="b40ba-128">YOL mevcut değilse komut onu oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="b40ba-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="b40ba-129">İle birleştirilemez `--global` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b40ba-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="b40ba-130">Bu seçeneği belirtmezseniz, belirtmeniz gerekir `--global` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="b40ba-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="b40ba-131">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b40ba-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b40ba-132">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b40ba-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="b40ba-133">Yüklenecek aracı sürümü.</span><span class="sxs-lookup"><span data-stu-id="b40ba-133">The version of the tool to install.</span></span> <span data-ttu-id="b40ba-134">Varsayılan olarak, en son kararlı Paket sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="b40ba-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="b40ba-135">Önizleme veya aracın eski sürümlerini yüklemek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="b40ba-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="b40ba-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="b40ba-136">Examples</span></span>

<span data-ttu-id="b40ba-137">Yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel araç varsayılan konumda:</span><span class="sxs-lookup"><span data-stu-id="b40ba-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="b40ba-138">Yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) belirli bir Windows klasöründeki Genel aracı:</span><span class="sxs-lookup"><span data-stu-id="b40ba-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="b40ba-139">Yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) belirli bir Linux/macOS klasöründe genel aracı:</span><span class="sxs-lookup"><span data-stu-id="b40ba-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="b40ba-140">2.0.0 sürümü yükler [dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracı:</span><span class="sxs-lookup"><span data-stu-id="b40ba-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="b40ba-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b40ba-141">See also</span></span>

- [<span data-ttu-id="b40ba-142">.NET core Araçları Genel</span><span class="sxs-lookup"><span data-stu-id="b40ba-142">.NET Core Global Tools</span></span>](global-tools.md)
