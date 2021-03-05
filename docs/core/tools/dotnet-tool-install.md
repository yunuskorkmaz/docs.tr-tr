---
title: DotNet aracı install komutu
description: DotNet aracı yükleme komutu, makinenizde belirtilen .NET aracını yükler.
ms.date: 02/14/2020
ms.openlocfilehash: b04e7fd24edce5d5da67cdd83fbea797118689b4
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206487"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="0c216-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="0c216-103">dotnet tool install</span></span>

<span data-ttu-id="0c216-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="0c216-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0c216-105">Name</span><span class="sxs-lookup"><span data-stu-id="0c216-105">Name</span></span>

<span data-ttu-id="0c216-106">`dotnet tool install` -Makinenizde belirtilen [.NET aracını](global-tools.md) yükleme.</span><span class="sxs-lookup"><span data-stu-id="0c216-106">`dotnet tool install` - Installs the specified [.NET tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0c216-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="0c216-107">Synopsis</span></span>

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

## <a name="description"></a><span data-ttu-id="0c216-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0c216-108">Description</span></span>

<span data-ttu-id="0c216-109">Bu `dotnet tool install` komut, makinenizde .NET araçları yüklemenizi sağlayan bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="0c216-109">The `dotnet tool install` command provides a way for you to install .NET tools on your machine.</span></span> <span data-ttu-id="0c216-110">Komutunu kullanmak için aşağıdaki yükleme seçeneklerinden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="0c216-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="0c216-111">Genel bir aracı varsayılan konuma yüklemek için `--global` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c216-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="0c216-112">Bir genel aracı özel bir konuma yüklemek için `--tool-path` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c216-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="0c216-113">Yerel bir araç yüklemek için `--global` ve `--tool-path` seçeneklerini atlayın.</span><span class="sxs-lookup"><span data-stu-id="0c216-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="0c216-114">**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="0c216-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="0c216-115">Veya seçeneğini belirttiğinizde, genel araçlar varsayılan olarak aşağıdaki dizinlere yüklenir `-g` `--global` :</span><span class="sxs-lookup"><span data-stu-id="0c216-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="0c216-116">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="0c216-116">OS</span></span>          | <span data-ttu-id="0c216-117">Yol</span><span class="sxs-lookup"><span data-stu-id="0c216-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="0c216-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="0c216-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="0c216-119">Windows</span><span class="sxs-lookup"><span data-stu-id="0c216-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="0c216-120">Yerel araçlar, geçerli dizinin altındaki bir *. config* dizinindeki *dotnet-tools.js* dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="0c216-120">Local tools are added to a *dotnet-tools.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="0c216-121">Henüz bir bildirim dosyası yoksa, aşağıdaki komutu çalıştırarak oluşturun:</span><span class="sxs-lookup"><span data-stu-id="0c216-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="0c216-122">Daha fazla bilgi için bkz. [yerel araç yüklemesi](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="0c216-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="0c216-123">Bağımsız değişkenler</span><span class="sxs-lookup"><span data-stu-id="0c216-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="0c216-124">Yüklenecek .NET aracını içeren NuGet paketinin adı/KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="0c216-124">Name/ID of the NuGet package that contains the .NET tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="0c216-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="0c216-125">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="0c216-126">Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="0c216-126">Adds an additional NuGet package source to use during installation.</span></span> <span data-ttu-id="0c216-127">Akışlara, bir öncelik sırasına göre değil, paralel olarak erişilir.</span><span class="sxs-lookup"><span data-stu-id="0c216-127">Feeds are accessed in parallel, not sequentially in some order of precedence.</span></span> <span data-ttu-id="0c216-128">Aynı paket ve sürüm birden çok akışda varsa, en hızlı akış kazanır.</span><span class="sxs-lookup"><span data-stu-id="0c216-128">If the same package and version is in multiple feeds, the fastest feed wins.</span></span> <span data-ttu-id="0c216-129">Daha fazla bilgi için bkz. [bir NuGet paketi yüklendiğinde ne olur?](/nuget/concepts/package-installation-process).</span><span class="sxs-lookup"><span data-stu-id="0c216-129">For more information, see [What happens when a NuGet package is installed?](/nuget/concepts/package-installation-process).</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="0c216-130">Kullanılacak NuGet yapılandırma (*nuget.config*) dosyası.</span><span class="sxs-lookup"><span data-stu-id="0c216-130">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="0c216-131">Aracının yükleneceği [hedef çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c216-131">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="0c216-132">.NET SDK varsayılan olarak en uygun hedef çerçeveyi seçmenizi dener.</span><span class="sxs-lookup"><span data-stu-id="0c216-132">By default, the .NET SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="0c216-133">Yüklemenin Kullanıcı genelinde olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c216-133">Specifies that the installation is user wide.</span></span> <span data-ttu-id="0c216-134">`--tool-path`Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="0c216-134">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="0c216-135">Her ikisini de atlayarak `--global` `--tool-path` bir yerel araç yüklemesi belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0c216-135">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0c216-136">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="0c216-136">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="0c216-137">Genel aracın yükleneceği konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="0c216-137">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="0c216-138">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="0c216-138">PATH can be absolute or relative.</span></span> <span data-ttu-id="0c216-139">YOL yoksa, komut onu oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="0c216-139">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="0c216-140">Her ikisini de atlayarak `--global` `--tool-path` bir yerel araç yüklemesi belirtilir.</span><span class="sxs-lookup"><span data-stu-id="0c216-140">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0c216-141">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0c216-141">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0c216-142">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="0c216-142">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="0c216-143">Yüklenecek aracın sürümü.</span><span class="sxs-lookup"><span data-stu-id="0c216-143">The version of the tool to install.</span></span> <span data-ttu-id="0c216-144">Varsayılan olarak, en son kararlı paket sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0c216-144">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="0c216-145">Aracının önizlemesini veya eski sürümlerini yüklemek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="0c216-145">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="0c216-146">Örnekler</span><span class="sxs-lookup"><span data-stu-id="0c216-146">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="0c216-147">Varsayılan konumda [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel araç olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0c216-147">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="0c216-148">Özel bir Windows dizininde [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) genel bir araç olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0c216-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="0c216-149">[Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) , belirli bir Linux/MacOS dizininde küresel bir araç olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="0c216-149">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="0c216-150">[Dotnetme](https://www.nuget.org/packages/dotnetsay/) 'nin 2.0.0 sürümünü küresel bir araç olarak kurar.</span><span class="sxs-lookup"><span data-stu-id="0c216-150">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="0c216-151">Geçerli dizin için [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) 'ı yerel bir araç olarak kurar.</span><span class="sxs-lookup"><span data-stu-id="0c216-151">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="0c216-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0c216-152">See also</span></span>

- [<span data-ttu-id="0c216-153">.NET araçları</span><span class="sxs-lookup"><span data-stu-id="0c216-153">.NET tools</span></span>](global-tools.md)
- [<span data-ttu-id="0c216-154">Öğretici: .NET CLı kullanarak .NET genel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="0c216-154">Tutorial: Install and use a .NET global tool using the .NET CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="0c216-155">Öğretici: .NET CLı kullanarak .NET yerel aracını yükleyip kullanma</span><span class="sxs-lookup"><span data-stu-id="0c216-155">Tutorial: Install and use a .NET local tool using the .NET CLI</span></span>](local-tools-how-to-use.md)
