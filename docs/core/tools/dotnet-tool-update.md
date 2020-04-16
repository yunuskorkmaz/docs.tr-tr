---
title: dotnet araç güncelleme komutu
description: Dotnet araç güncelleştirme komutu makinenizde belirtilen .NET Core aracını güncelleştirir.
ms.date: 02/14/2020
ms.openlocfilehash: 6176846dbe8e2a91d9c6959dede15718d8f983b2
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463295"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="30b23-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="30b23-103">dotnet tool update</span></span>

<span data-ttu-id="30b23-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="30b23-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="30b23-105">Adı</span><span class="sxs-lookup"><span data-stu-id="30b23-105">Name</span></span>

<span data-ttu-id="30b23-106">`dotnet tool update`- Makinenizde belirtilen [.NET Core aracını](global-tools.md) güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="30b23-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="30b23-107">Özet</span><span class="sxs-lookup"><span data-stu-id="30b23-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="30b23-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30b23-108">Description</span></span>

<span data-ttu-id="30b23-109">Komut, `dotnet tool update` makinenizdeki .NET Core araçlarını paketin en son kararlı sürümüne güncellemeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="30b23-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="30b23-110">Komut, bir aracı etkin bir şekilde güncelleyerek bir aracı yükler ve yeniden yükler.</span><span class="sxs-lookup"><span data-stu-id="30b23-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="30b23-111">Komutu kullanmak için aşağıdaki seçeneklerden birini belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="30b23-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="30b23-112">Varsayılan konumda yüklü olan genel bir aracı güncelleştirmek `--global` için,</span><span class="sxs-lookup"><span data-stu-id="30b23-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="30b23-113">Özel bir konumda yüklenen genel bir aracı güncelleştirmek `--tool-path` için seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="30b23-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="30b23-114">Yerel bir aracı güncelleştirmek için, seçenekleri `--global` ve seçenekleri `--tool-path` atleyin.</span><span class="sxs-lookup"><span data-stu-id="30b23-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="30b23-115">**Yerel araçlar .NET Core SDK 3.0 ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="30b23-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="30b23-116">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="30b23-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="30b23-117">Güncelleştirilen .NET Core global aracını içeren NuGet paketinin adı/kimliği.</span><span class="sxs-lookup"><span data-stu-id="30b23-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="30b23-118">Paket adını [dotnet araç listesi](dotnet-tool-list.md) komutunu kullanarak bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30b23-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="30b23-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="30b23-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="30b23-120">Yükleme sırasında kullanmak üzere ek bir NuGet paket kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="30b23-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="30b23-121">NuGet yapılandırması (*nuget.config*) dosyasını kullanmak.</span><span class="sxs-lookup"><span data-stu-id="30b23-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="30b23-122">Aracı güncelleştirmek için [hedef çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="30b23-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="30b23-123">Güncelleştirmenin kullanıcı çapında bir araç için olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="30b23-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="30b23-124">`--tool-path` Seçenekle birleştirilemeyiz.</span><span class="sxs-lookup"><span data-stu-id="30b23-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="30b23-125">Her ikisini `--global` de `--tool-path` atlayarak ve güncellenecek aracın yerel bir araç olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="30b23-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="30b23-126">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="30b23-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="30b23-127">Genel aracın yüklendiği yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="30b23-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="30b23-128">PATH mutlak veya göreceli olabilir.</span><span class="sxs-lookup"><span data-stu-id="30b23-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="30b23-129">`--global` Seçenekle birleştirilemeyiz.</span><span class="sxs-lookup"><span data-stu-id="30b23-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="30b23-130">Her ikisini `--global` de `--tool-path` atlayarak ve güncellenecek aracın yerel bir araç olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="30b23-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="30b23-131">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="30b23-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="30b23-132">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="30b23-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="30b23-133">Örnekler</span><span class="sxs-lookup"><span data-stu-id="30b23-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="30b23-134">[Noktanetsay](https://www.nuget.org/packages/dotnetsay/) global aracını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="30b23-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="30b23-135">Belirli bir Windows dizininde bulunan [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global aracını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="30b23-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="30b23-136">Belirli bir Linux/macOS dizininde bulunan [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global aracını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="30b23-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="30b23-137">Geçerli dizin için yüklenen [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yerel aracını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="30b23-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="30b23-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30b23-138">See also</span></span>

- [<span data-ttu-id="30b23-139">.NET Çekirdek araçları</span><span class="sxs-lookup"><span data-stu-id="30b23-139">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="30b23-140">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="30b23-140">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="30b23-141">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="30b23-141">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
