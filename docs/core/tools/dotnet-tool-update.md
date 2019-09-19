---
title: DotNet Aracı güncelleştirme komutu
description: DotNet Aracı güncelleştirme komutu makinenizde belirtilen .NET Core küresel aracını güncelleştirir.
ms.date: 05/29/2018
ms.openlocfilehash: b10ce39c8b9d4df23243bcf672454a455e34eec1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117528"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="ff567-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="ff567-103">dotnet tool update</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="ff567-104">Ad</span><span class="sxs-lookup"><span data-stu-id="ff567-104">Name</span></span>

<span data-ttu-id="ff567-105">`dotnet tool update`-Makinenizde belirtilen [.NET Core küresel aracı](global-tools.md) 'nı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="ff567-105">`dotnet tool update` - Updates the specified [.NET Core Global Tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ff567-106">Özeti</span><span class="sxs-lookup"><span data-stu-id="ff567-106">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="ff567-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ff567-107">Description</span></span>

<span data-ttu-id="ff567-108">Komut `dotnet tool update` , makinenizde .NET Core küresel araçlarını paketin en son kararlı sürümüne güncelleştirmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="ff567-108">The `dotnet tool update` command provides a way for you to update .NET Core Global Tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="ff567-109">Komut, bir aracı kaldırır ve etkin bir şekilde güncelleştiren bir araç yükler.</span><span class="sxs-lookup"><span data-stu-id="ff567-109">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="ff567-110">Komutunu kullanmak için, `--global` seçeneğini kullanarak Kullanıcı genelindeki bir yüklemeden bir aracı güncelleştirmek istediğinizi belirtmeniz veya `--tool-path` seçeneği kullanılarak aracın yüklendiği konuma bir yol belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff567-110">To use the command, you either have to specify that you want to update a tool from a user-wide installation using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="ff567-111">Arguments</span><span class="sxs-lookup"><span data-stu-id="ff567-111">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="ff567-112">Güncelleştirilecek .NET Core küresel aracını içeren NuGet paketinin adı/KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="ff567-112">Name/ID of the NuGet package that contains the .NET Core Global Tool to update.</span></span> <span data-ttu-id="ff567-113">[DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak paket adını bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ff567-113">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="ff567-114">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="ff567-114">Options</span></span>

`--add-source <SOURCE>`

<span data-ttu-id="ff567-115">Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="ff567-115">Adds an additional NuGet package source to use during installation.</span></span>

`--configfile <FILE>`

<span data-ttu-id="ff567-116">Kullanılacak NuGet yapılandırma (*NuGet. config*) dosyası.</span><span class="sxs-lookup"><span data-stu-id="ff567-116">The NuGet configuration (*nuget.config*) file to use.</span></span>

`--framework <FRAMEWORK>`

<span data-ttu-id="ff567-117">Aracının güncelleştirilmesi için [hedef çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff567-117">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

`-g|--global`

<span data-ttu-id="ff567-118">Güncelleştirmenin Kullanıcı genelindeki bir araç için olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff567-118">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="ff567-119">`--tool-path` Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="ff567-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="ff567-120">Bu seçeneği belirtmezseniz, `--tool-path` seçeneğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff567-120">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="ff567-121">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="ff567-121">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="ff567-122">Genel aracın yüklendiği konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="ff567-122">Specifies the location where the Global Tool is installed.</span></span> <span data-ttu-id="ff567-123">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="ff567-123">PATH can be absolute or relative.</span></span> <span data-ttu-id="ff567-124">`--global` Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="ff567-124">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="ff567-125">Bu seçeneği belirtmezseniz, `--global` seçeneğini belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ff567-125">If you don't specify this option, you must specify the `--global` option.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="ff567-126">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ff567-126">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ff567-127">İzin verilen değerler `q[uiet]` `m[inimal]` ,`n[ormal]`,, ve .`diag[nostic]` `d[etailed]`</span><span class="sxs-lookup"><span data-stu-id="ff567-127">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="ff567-128">Örnekler</span><span class="sxs-lookup"><span data-stu-id="ff567-128">Examples</span></span>

<span data-ttu-id="ff567-129">[Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel aracını güncelleştirir:</span><span class="sxs-lookup"><span data-stu-id="ff567-129">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool update -g dotnetsay`

<span data-ttu-id="ff567-130">Belirli bir Windows klasöründe bulunan [dotnetsöyleme](https://www.nuget.org/packages/dotnetsay/) küresel aracını güncelleştirir:</span><span class="sxs-lookup"><span data-stu-id="ff567-130">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Windows folder:</span></span>

`dotnet tool update dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="ff567-131">Belirli bir Linux/macOS klasöründe bulunan [dotnetsay](https://www.nuget.org/packages/dotnetsay/) küresel aracını güncelleştirir:</span><span class="sxs-lookup"><span data-stu-id="ff567-131">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool located on a specific Linux/macOS folder:</span></span>

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="ff567-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff567-132">See also</span></span>

- [<span data-ttu-id="ff567-133">.NET Core küresel araçları</span><span class="sxs-lookup"><span data-stu-id="ff567-133">.NET Core Global Tools</span></span>](global-tools.md)
