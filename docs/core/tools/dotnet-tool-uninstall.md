---
title: dotnet aracı kaldırma komutu
description: Dotnet aracı kaldırma komutu, belirtilen .NET Core aracını makinenizden kaldırz.
ms.date: 02/14/2020
ms.openlocfilehash: 0416f91019a49e17f1be14a1d928ad1fafaa736c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463306"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="2baec-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="2baec-103">dotnet tool uninstall</span></span>

<span data-ttu-id="2baec-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="2baec-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2baec-105">Adı</span><span class="sxs-lookup"><span data-stu-id="2baec-105">Name</span></span>

<span data-ttu-id="2baec-106">`dotnet tool uninstall`- Belirtilen [.NET Core aracını](global-tools.md) makinenizden kaldırın.</span><span class="sxs-lookup"><span data-stu-id="2baec-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2baec-107">Özet</span><span class="sxs-lookup"><span data-stu-id="2baec-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a><span data-ttu-id="2baec-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2baec-108">Description</span></span>

<span data-ttu-id="2baec-109">Komut, `dotnet tool uninstall` makinenizden .NET Core araçlarını kaldırmanız için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="2baec-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="2baec-110">Komutu kullanmak için aşağıdaki seçeneklerden birini belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2baec-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="2baec-111">Varsayılan konumda yüklü olan genel bir aracı kaldırmak için `--global` seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="2baec-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="2baec-112">Özel bir konumda yüklenen genel bir aracı kaldırmak için `--tool-path` seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="2baec-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="2baec-113">Yerel bir aracı kaldırmak için, `--global` seçenekleri `--tool-path` ve seçenekleri atleyin.</span><span class="sxs-lookup"><span data-stu-id="2baec-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="2baec-114">**Yerel araçlar .NET Core SDK 3.0 ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="2baec-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="2baec-115">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2baec-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="2baec-116">Kaldırılmak için .NET Core aracını içeren NuGet paketinin adı/kimliği.</span><span class="sxs-lookup"><span data-stu-id="2baec-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="2baec-117">Paket adını [dotnet araç listesi](dotnet-tool-list.md) komutunu kullanarak bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2baec-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="2baec-118">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2baec-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="2baec-119">Kaldırılacak aracın kullanıcı çapındaki bir yüklemeden olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2baec-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="2baec-120">`--tool-path` Seçenekle birleştirilemeyiz.</span><span class="sxs-lookup"><span data-stu-id="2baec-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="2baec-121">Her ikisini `--global` de `--tool-path` atlayan ve kaldırılacak aracın yerel bir araç olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2baec-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="2baec-122">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2baec-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="2baec-123">Aracın kaldırılabildiği yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="2baec-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="2baec-124">PATH mutlak veya göreceli olabilir.</span><span class="sxs-lookup"><span data-stu-id="2baec-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="2baec-125">`--global` Seçenekle birleştirilemeyiz.</span><span class="sxs-lookup"><span data-stu-id="2baec-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="2baec-126">Her ikisini `--global` de `--tool-path` atlayan ve kaldırılacak aracın yerel bir araç olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="2baec-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="2baec-127">Örnekler</span><span class="sxs-lookup"><span data-stu-id="2baec-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="2baec-128">[Dotnetsay](https://www.nuget.org/packages/dotnetsay/) global aracını yükler.</span><span class="sxs-lookup"><span data-stu-id="2baec-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="2baec-129">Belirli bir Windows dizininden [noktanetsay](https://www.nuget.org/packages/dotnetsay/) global aracını kaldır.</span><span class="sxs-lookup"><span data-stu-id="2baec-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="2baec-130">Belirli bir Linux/macOS dizininden [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global aracını kaldırır.</span><span class="sxs-lookup"><span data-stu-id="2baec-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="2baec-131">Geçerli dizinden [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yerel aracını kaldır.</span><span class="sxs-lookup"><span data-stu-id="2baec-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="2baec-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2baec-132">See also</span></span>

- [<span data-ttu-id="2baec-133">.NET Çekirdek araçları</span><span class="sxs-lookup"><span data-stu-id="2baec-133">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="2baec-134">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="2baec-134">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="2baec-135">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="2baec-135">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
