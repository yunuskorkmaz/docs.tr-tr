---
title: DotNet aracı install komutu
description: DotNet aracı yükleme komutu, makinenizde belirtilen .NET aracını yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 1dd870a8f91e557a2f59919682616aa8817fc070
ms.sourcegitcommit: b201d177e01480a139622f3bf8facd367657a472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2020
ms.locfileid: "94634330"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="24d24-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="24d24-103">dotnet tool install</span></span>

<span data-ttu-id="24d24-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="24d24-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="24d24-105">Name</span><span class="sxs-lookup"><span data-stu-id="24d24-105">Name</span></span>

<span data-ttu-id="24d24-106">`dotnet tool install` -Makinenizde belirtilen [.NET aracını](global-tools.md) yükleme.</span><span class="sxs-lookup"><span data-stu-id="24d24-106">`dotnet tool install` - Installs the specified [.NET tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="24d24-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="24d24-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a><span data-ttu-id="24d24-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="24d24-108">Description</span></span>

<span data-ttu-id="24d24-109">Bu `dotnet tool install` komut, makinenizde .NET araçları yüklemenizi sağlayan bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="24d24-109">The `dotnet tool install` command provides a way for you to install .NET tools on your machine.</span></span> <span data-ttu-id="24d24-110">Komutunu kullanmak için aşağıdaki yükleme seçeneklerinden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="24d24-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="24d24-111">Genel bir aracı varsayılan konuma yüklemek için `--global` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="24d24-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="24d24-112">Bir genel aracı özel bir konuma yüklemek için `--tool-path` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="24d24-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="24d24-113">Yerel bir araç yüklemek için `--global` ve `--tool-path` seçeneklerini atlayın.</span><span class="sxs-lookup"><span data-stu-id="24d24-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="24d24-114">**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="24d24-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="24d24-115">Veya seçeneğini belirttiğinizde, genel araçlar varsayılan olarak aşağıdaki dizinlere yüklenir `-g` `--global` :</span><span class="sxs-lookup"><span data-stu-id="24d24-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="24d24-116">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="24d24-116">OS</span></span>          | <span data-ttu-id="24d24-117">Yol</span><span class="sxs-lookup"><span data-stu-id="24d24-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="24d24-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="24d24-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="24d24-119">Windows</span><span class="sxs-lookup"><span data-stu-id="24d24-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="24d24-120">Yerel araçlar, geçerli dizinin altındaki bir *. config* dizinindeki *dotnet-tools.js* dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="24d24-120">Local tools are added to a *dotnet-tools.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="24d24-121">Henüz bir bildirim dosyası yoksa, aşağıdaki komutu çalıştırarak oluşturun:</span><span class="sxs-lookup"><span data-stu-id="24d24-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="24d24-122">Daha fazla bilgi için bkz. [yerel araç yüklemesi](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="24d24-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="24d24-123">Arguments</span><span class="sxs-lookup"><span data-stu-id="24d24-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="24d24-124">Yüklenecek .NET aracını içeren NuGet paketinin adı/KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="24d24-124">Name/ID of the NuGet package that contains the .NET tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="24d24-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="24d24-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="24d24-126">Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="24d24-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="24d24-127">Kullanılacak NuGet yapılandırma ( *nuget.config* ) dosyası.</span><span class="sxs-lookup"><span data-stu-id="24d24-127">The NuGet configuration ( *nuget.config* ) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="24d24-128">Aracının yükleneceği [hedef çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="24d24-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="24d24-129">.NET SDK varsayılan olarak en uygun hedef çerçeveyi seçmenizi dener.</span><span class="sxs-lookup"><span data-stu-id="24d24-129">By default, the .NET SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="24d24-130">Yüklemenin Kullanıcı genelinde olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="24d24-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="24d24-131">`--tool-path`Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="24d24-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="24d24-132">Her ikisini de atlayarak `--global` `--tool-path` bir yerel araç yüklemesi belirtilir.</span><span class="sxs-lookup"><span data-stu-id="24d24-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="24d24-133">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="24d24-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="24d24-134">Genel aracın yükleneceği konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="24d24-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="24d24-135">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="24d24-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="24d24-136">YOL yoksa, komut onu oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="24d24-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="24d24-137">Her ikisini de atlayarak `--global` `--tool-path` bir yerel araç yüklemesi belirtilir.</span><span class="sxs-lookup"><span data-stu-id="24d24-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="24d24-138">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="24d24-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="24d24-139">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="24d24-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="24d24-140">Yüklenecek aracın sürümü.</span><span class="sxs-lookup"><span data-stu-id="24d24-140">The version of the tool to install.</span></span> <span data-ttu-id="24d24-141">Varsayılan olarak, en son kararlı paket sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="24d24-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="24d24-142">Aracının önizlemesini veya eski sürümlerini yüklemek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="24d24-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="24d24-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="24d24-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="24d24-144">Varsayılan konumda [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel araç olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="24d24-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="24d24-145">Özel bir Windows dizininde [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel bir araç olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="24d24-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="24d24-146">[Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) , belirli bir Linux/MacOS dizininde küresel bir araç olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="24d24-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="24d24-147">[Dotnetme](https://www.nuget.org/packages/dotnetsay/) 'nin 2.0.0 sürümünü küresel bir araç olarak kurar.</span><span class="sxs-lookup"><span data-stu-id="24d24-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="24d24-148">Geçerli dizin için [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) 'ı yerel bir araç olarak kurar.</span><span class="sxs-lookup"><span data-stu-id="24d24-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="24d24-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="24d24-149">See also</span></span>

- [<span data-ttu-id="24d24-150">.NET araçları</span><span class="sxs-lookup"><span data-stu-id="24d24-150">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="24d24-151">Öğretici: .NET CLı kullanarak .NET genel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="24d24-151">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="24d24-152">Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="24d24-152">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
