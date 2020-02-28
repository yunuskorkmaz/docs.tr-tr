---
title: DotNet Aracı güncelleştirme komutu
description: DotNet Aracı güncelleştirme komutu makinenizde belirtilen .NET Core aracını güncelleştirir.
ms.date: 02/14/2020
ms.openlocfilehash: 80e807a0fc06ad762334f888e701f6d9c448369a
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156952"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="fbcdb-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="fbcdb-103">dotnet tool update</span></span>

<span data-ttu-id="fbcdb-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="fbcdb-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fbcdb-105">Adı</span><span class="sxs-lookup"><span data-stu-id="fbcdb-105">Name</span></span>

<span data-ttu-id="fbcdb-106">`dotnet tool update`-makinenizde belirtilen [.NET Core aracını](global-tools.md) güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fbcdb-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="fbcdb-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="fbcdb-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbcdb-108">Description</span></span>

<span data-ttu-id="fbcdb-109">`dotnet tool update` komutu, makinenizde .NET Core araçlarını paketin en son kararlı sürümüne güncelleştirmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="fbcdb-110">Komut, bir aracı kaldırır ve etkin bir şekilde güncelleştiren bir araç yükler.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="fbcdb-111">Komutunu kullanmak için aşağıdaki seçeneklerden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="fbcdb-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="fbcdb-112">Varsayılan konumda yüklü olan küresel bir aracı güncelleştirmek için `--global` seçeneğini kullanın</span><span class="sxs-lookup"><span data-stu-id="fbcdb-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="fbcdb-113">Özel bir konuma yüklenmiş olan küresel bir aracı güncelleştirmek için `--tool-path` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="fbcdb-114">Yerel bir aracı güncelleştirmek için `--global` ve `--tool-path` seçeneklerini atlayın.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="fbcdb-115">**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="fbcdb-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="fbcdb-116">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="fbcdb-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="fbcdb-117">Güncelleştirilecek .NET Core küresel aracını içeren NuGet paketinin adı/KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="fbcdb-118">[DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak paket adını bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="fbcdb-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="fbcdb-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="fbcdb-120">Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="fbcdb-121">Kullanılacak NuGet yapılandırma (*NuGet. config*) dosyası.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="fbcdb-122">Aracının güncelleştirilmesi için [hedef çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="fbcdb-123">Güncelleştirmenin Kullanıcı genelindeki bir araç için olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="fbcdb-124">`--tool-path` seçeneği ile birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="fbcdb-125">`--global` ve `--tool-path` her ikisi de kullanılmazsa, güncellenen aracın yerel bir araç olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="fbcdb-126">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="fbcdb-127">Genel aracın yüklendiği konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="fbcdb-128">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="fbcdb-129">`--global` seçeneği ile birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="fbcdb-130">`--global` ve `--tool-path` her ikisi de kullanılmazsa, güncellenen aracın yerel bir araç olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="fbcdb-131">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fbcdb-132">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="fbcdb-133">Örnekler</span><span class="sxs-lookup"><span data-stu-id="fbcdb-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="fbcdb-134">[Dotnetsay](https://www.nuget.org/packages/dotnetsay/) küresel aracını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="fbcdb-135">Belirli bir Windows dizininde bulunan [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracı 'nı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="fbcdb-136">Belirli bir Linux/macOS dizininde bulunan [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracı 'nı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="fbcdb-137">Geçerli dizin için yüklenen [dotnetsöyleme](https://www.nuget.org/packages/dotnetsay/) yerel aracını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="fbcdb-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fbcdb-138">See also</span></span>

- [<span data-ttu-id="fbcdb-139">.NET Core araçları</span><span class="sxs-lookup"><span data-stu-id="fbcdb-139">.NET Core tools</span></span>](global-tools.md)
