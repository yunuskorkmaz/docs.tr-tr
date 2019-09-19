---
title: DotNet aracı install komutu
description: DotNet aracı yükleme komutu, makinenizde belirtilen .NET Core küresel aracını yükler.
ms.date: 05/29/2018
ms.openlocfilehash: d6f691117e93a39c9837b282dca19e452515c80a
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117474"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="5dda7-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="5dda7-103">dotnet tool install</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="5dda7-104">Ad</span><span class="sxs-lookup"><span data-stu-id="5dda7-104">Name</span></span>

<span data-ttu-id="5dda7-105">`dotnet tool install`-Makinenizde belirtilen [.NET Core küresel aracını](global-tools.md) yükleme.</span><span class="sxs-lookup"><span data-stu-id="5dda7-105">`dotnet tool install` - Installs the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5dda7-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="5dda7-106">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="5dda7-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5dda7-107">Description</span></span>

<span data-ttu-id="5dda7-108">Bu `dotnet tool install` komut, makinenizde .NET Core küresel araçları yüklemenizi sağlayan bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="5dda7-108">The `dotnet tool install` command provides a way for you to install .NET Core Global Tools on your machine.</span></span> <span data-ttu-id="5dda7-109">Komutunu kullanmak için, `--global` seçeneğini kullanarak Kullanıcı genelindeki bir yüklemeyi istediğinizi veya `--tool-path` seçeneğini kullanarak yüklemek için bir yol belirtmenizi belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5dda7-109">To use the command, you either have to specify that you want a user-wide installation using the `--global` option or you specify a path to install it using the `--tool-path` option.</span></span>

<span data-ttu-id="5dda7-110">Genel araçlar, `-g` (veya `--global`) seçeneğini belirttiğinizde varsayılan olarak aşağıdaki dizinlere yüklenir:</span><span class="sxs-lookup"><span data-stu-id="5dda7-110">Global Tools are installed in the following directories by default when you specify the `-g` (or `--global`) option:</span></span>

| <span data-ttu-id="5dda7-111">OS</span><span class="sxs-lookup"><span data-stu-id="5dda7-111">OS</span></span>          | <span data-ttu-id="5dda7-112">Yol</span><span class="sxs-lookup"><span data-stu-id="5dda7-112">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="5dda7-113">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="5dda7-113">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="5dda7-114">Windows</span><span class="sxs-lookup"><span data-stu-id="5dda7-114">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

## <a name="arguments"></a><span data-ttu-id="5dda7-115">Arguments</span><span class="sxs-lookup"><span data-stu-id="5dda7-115">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="5dda7-116">Yüklenecek .NET Core küresel aracını içeren NuGet paketinin adı/KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="5dda7-116">Name/ID of the NuGet package that contains the .NET Core Global Tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="5dda7-117">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="5dda7-117">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="5dda7-118">Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="5dda7-118">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="5dda7-119">Kullanılacak NuGet yapılandırma (*NuGet. config*) dosyası.</span><span class="sxs-lookup"><span data-stu-id="5dda7-119">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="5dda7-120">Aracının yükleneceği [hedef çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="5dda7-120">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="5dda7-121">.NET Core SDK, varsayılan olarak en uygun hedef Framework 'ü seçmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="5dda7-121">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

`-g|--global`

<span data-ttu-id="5dda7-122">Yüklemenin Kullanıcı genelinde olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5dda7-122">Specifies that the installation is user wide.</span></span> <span data-ttu-id="5dda7-123">`--tool-path` Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="5dda7-123">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="5dda7-124">Bu seçeneği belirtmezseniz, `--tool-path` seçeneğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5dda7-124">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="5dda7-125">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="5dda7-125">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="5dda7-126">Genel aracın yükleneceği konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="5dda7-126">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="5dda7-127">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="5dda7-127">PATH can be absolute or relative.</span></span> <span data-ttu-id="5dda7-128">YOL yoksa, komut onu oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="5dda7-128">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="5dda7-129">`--global` Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="5dda7-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="5dda7-130">Bu seçeneği belirtmezseniz, `--global` seçeneğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5dda7-130">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="5dda7-131">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="5dda7-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="5dda7-132">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="5dda7-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version <VERSION_NUMBER>`

<span data-ttu-id="5dda7-133">Yüklenecek aracın sürümü.</span><span class="sxs-lookup"><span data-stu-id="5dda7-133">The version of the tool to install.</span></span> <span data-ttu-id="5dda7-134">Varsayılan olarak, en son kararlı paket sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="5dda7-134">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="5dda7-135">Aracının önizlemesini veya eski sürümlerini yüklemek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="5dda7-135">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="5dda7-136">Örnekler</span><span class="sxs-lookup"><span data-stu-id="5dda7-136">Examples</span></span>

<span data-ttu-id="5dda7-137">[Dotnetsay](https://www.nuget.org/packages/dotnetsay/) genel aracını varsayılan konuma yüklenir:</span><span class="sxs-lookup"><span data-stu-id="5dda7-137">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool in the default location:</span></span>

`dotnet tool install -g dotnetsay`

<span data-ttu-id="5dda7-138">Özel bir Windows klasörüne [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel aracını yükleme:</span><span class="sxs-lookup"><span data-stu-id="5dda7-138">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Windows folder:</span></span>

`dotnet tool install dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="5dda7-139">Belirli bir Linux/macOS klasörüne [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel aracını yükleme:</span><span class="sxs-lookup"><span data-stu-id="5dda7-139">Installs the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool on a specific Linux/macOS folder:</span></span>

`dotnet tool install dotnetsay --tool-path ~/bin`

<span data-ttu-id="5dda7-140">[Dotnetsay](https://www.nuget.org/packages/dotnetsay/) küresel aracının 2.0.0 sürümünü kurar:</span><span class="sxs-lookup"><span data-stu-id="5dda7-140">Installs version 2.0.0 of the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool install -g dotnetsay --version 2.0.0`

## <a name="see-also"></a><span data-ttu-id="5dda7-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5dda7-141">See also</span></span>

- [<span data-ttu-id="5dda7-142">.NET Core küresel araçları</span><span class="sxs-lookup"><span data-stu-id="5dda7-142">.NET Core Global Tools</span></span>](global-tools.md)
