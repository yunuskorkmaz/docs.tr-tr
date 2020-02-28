---
title: DotNet Aracı kaldırma komutu
description: DotNet Aracı kaldırma komutu, belirtilen .NET Core aracını makinenizden kaldırır.
ms.date: 02/14/2020
ms.openlocfilehash: 7a15c169c73cf5a743e0fa6f47645d6bccedbde3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157051"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="87bce-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="87bce-103">dotnet tool uninstall</span></span>

<span data-ttu-id="87bce-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="87bce-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="87bce-105">Adı</span><span class="sxs-lookup"><span data-stu-id="87bce-105">Name</span></span>

<span data-ttu-id="87bce-106">`dotnet tool uninstall`-belirtilen [.NET Core aracını](global-tools.md) makinenizden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="87bce-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="87bce-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="87bce-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="87bce-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="87bce-108">Description</span></span>

<span data-ttu-id="87bce-109">`dotnet tool uninstall` komutu, makinenizden .NET Core araçlarını kaldırmanız için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="87bce-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="87bce-110">Komutunu kullanmak için aşağıdaki seçeneklerden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="87bce-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="87bce-111">Varsayılan konumda yüklü olan küresel bir aracı kaldırmak için `--global` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="87bce-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="87bce-112">Özel bir konuma yüklenmiş olan küresel bir aracı kaldırmak için `--tool-path` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="87bce-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="87bce-113">Yerel bir aracı kaldırmak için `--global` ve `--tool-path` seçeneklerini atlayın.</span><span class="sxs-lookup"><span data-stu-id="87bce-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="87bce-114">**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="87bce-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="87bce-115">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="87bce-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="87bce-116">Kaldırılacak .NET Core aracını içeren NuGet paketinin adı/KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="87bce-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="87bce-117">[DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak paket adını bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="87bce-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="87bce-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="87bce-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="87bce-119">Kaldırılacak aracın Kullanıcı genelindeki bir yüklemeden olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="87bce-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="87bce-120">`--tool-path` seçeneği ile birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="87bce-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="87bce-121">`--global` ve `--tool-path` her ikisi de kullanılmazsa, kaldırılacak aracın yerel bir araç olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="87bce-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="87bce-122">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="87bce-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="87bce-123">Aracının kaldırılacağı konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="87bce-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="87bce-124">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="87bce-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="87bce-125">`--global` seçeneği ile birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="87bce-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="87bce-126">`--global` ve `--tool-path` her ikisi de kullanılmazsa, kaldırılacak aracın yerel bir araç olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="87bce-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="87bce-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="87bce-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="87bce-128">[Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="87bce-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="87bce-129">[Dotnetsöyleme](https://www.nuget.org/packages/dotnetsay/) genel aracını belirli bir Windows dizininden kaldırır.</span><span class="sxs-lookup"><span data-stu-id="87bce-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="87bce-130">Belirli bir Linux/macOS dizininden [dotnetsöyleyin](https://www.nuget.org/packages/dotnetsay/) genel aracını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="87bce-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="87bce-131">Geçerli dizinden [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) yerel aracını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="87bce-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="87bce-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87bce-132">See also</span></span>

- [<span data-ttu-id="87bce-133">.NET Core araçları</span><span class="sxs-lookup"><span data-stu-id="87bce-133">.NET Core tools</span></span>](global-tools.md)
