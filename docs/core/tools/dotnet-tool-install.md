---
title: dotnet aracı yükleme komutu
description: Dotnet araç yükleme komutu makinenize belirtilen .NET Core aracını yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 1e142773d1f981a8dc3b552d5a23d2864cdd82c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146469"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="97a94-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="97a94-103">dotnet tool install</span></span>

<span data-ttu-id="97a94-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 2.1 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="97a94-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="97a94-105">Adı</span><span class="sxs-lookup"><span data-stu-id="97a94-105">Name</span></span>

<span data-ttu-id="97a94-106">`dotnet tool install`- Belirtilen [.NET Core aracını](global-tools.md) makinenize yükler.</span><span class="sxs-lookup"><span data-stu-id="97a94-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="97a94-107">Özet</span><span class="sxs-lookup"><span data-stu-id="97a94-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME> <--tool-path>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="97a94-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="97a94-108">Description</span></span>

<span data-ttu-id="97a94-109">Komut, `dotnet tool install` makinenize .NET Core araçlarını yüklemeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="97a94-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="97a94-110">Komutu kullanmak için aşağıdaki yükleme seçeneklerinden birini belirtirsiniz:</span><span class="sxs-lookup"><span data-stu-id="97a94-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="97a94-111">Varsayılan konuma genel bir araç yüklemek `--global` için seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="97a94-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="97a94-112">Genel bir aracı özel bir konuma `--tool-path` yüklemek için seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="97a94-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="97a94-113">Yerel bir araç yüklemek için, `--global` `--tool-path` ve seçenekleri atla.</span><span class="sxs-lookup"><span data-stu-id="97a94-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="97a94-114">**Yerel araçlar .NET Core SDK 3.0 ile başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="97a94-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="97a94-115">Genel araçlar, aşağıdaki dizinlerde varsayılan olarak veya `-g` `--global` seçeneği belirttiğiniz zaman yüklenir:</span><span class="sxs-lookup"><span data-stu-id="97a94-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="97a94-116">İşletim Sistemi</span><span class="sxs-lookup"><span data-stu-id="97a94-116">OS</span></span>          | <span data-ttu-id="97a94-117">Yol</span><span class="sxs-lookup"><span data-stu-id="97a94-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="97a94-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="97a94-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="97a94-119">Windows</span><span class="sxs-lookup"><span data-stu-id="97a94-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="97a94-120">Yerel araçlar, geçerli dizini altında *bir .config* dizinindeki *bir araç bildirimi.json* dosyasına eklenir.</span><span class="sxs-lookup"><span data-stu-id="97a94-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="97a94-121">Bir bildirim dosyası henüz yoksa, aşağıdaki komutu çalıştırarak dosyayı oluşturun:</span><span class="sxs-lookup"><span data-stu-id="97a94-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="97a94-122">Daha fazla bilgi için [bkz.](global-tools.md#install-a-local-tool)</span><span class="sxs-lookup"><span data-stu-id="97a94-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="97a94-123">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="97a94-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="97a94-124">Yüklemek için .NET Core aracını içeren NuGet paketinin adı/kimliği.</span><span class="sxs-lookup"><span data-stu-id="97a94-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="97a94-125">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="97a94-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="97a94-126">Yükleme sırasında kullanmak üzere ek bir NuGet paket kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="97a94-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="97a94-127">NuGet yapılandırması (*nuget.config*) dosyasını kullanmak.</span><span class="sxs-lookup"><span data-stu-id="97a94-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="97a94-128">Aracı yüklemek için [hedef çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="97a94-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="97a94-129">Varsayılan olarak, .NET Core SDK en uygun hedef çerçeveyi seçmeye çalışır.</span><span class="sxs-lookup"><span data-stu-id="97a94-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="97a94-130">Yüklemenin kullanıcı genelinde olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="97a94-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="97a94-131">`--tool-path` Seçenekle birleştirilemeyiz.</span><span class="sxs-lookup"><span data-stu-id="97a94-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="97a94-132">Her ikisini `--global` de `--tool-path` atlayarak yerel bir araç yüklemesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="97a94-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="97a94-133">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="97a94-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="97a94-134">Genel Araç'ın yüklenmesi gereken yeri belirtir.</span><span class="sxs-lookup"><span data-stu-id="97a94-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="97a94-135">PATH mutlak veya göreceli olabilir.</span><span class="sxs-lookup"><span data-stu-id="97a94-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="97a94-136">PATH yoksa, komut onu oluşturmaya çalışır.</span><span class="sxs-lookup"><span data-stu-id="97a94-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="97a94-137">Her ikisini `--global` de `--tool-path` atlayarak yerel bir araç yüklemesi belirtir.</span><span class="sxs-lookup"><span data-stu-id="97a94-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="97a94-138">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="97a94-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="97a94-139">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="97a94-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="97a94-140">Yüklemek için aracın sürümü.</span><span class="sxs-lookup"><span data-stu-id="97a94-140">The version of the tool to install.</span></span> <span data-ttu-id="97a94-141">Varsayılan olarak, en son kararlı paket sürümü yüklenir.</span><span class="sxs-lookup"><span data-stu-id="97a94-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="97a94-142">Aracın önizlemesini veya eski sürümlerini yüklemek için bu seçeneği kullanın.</span><span class="sxs-lookup"><span data-stu-id="97a94-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="97a94-143">Örnekler</span><span class="sxs-lookup"><span data-stu-id="97a94-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="97a94-144">Varsayılan konumda genel bir araç olarak [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yükler.</span><span class="sxs-lookup"><span data-stu-id="97a94-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="97a94-145">Belirli bir Windows dizininde genel bir araç olarak [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yükler.</span><span class="sxs-lookup"><span data-stu-id="97a94-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="97a94-146">Belirli bir Linux/macOS dizininde global bir araç olarak [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yükler.</span><span class="sxs-lookup"><span data-stu-id="97a94-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="97a94-147">Genel bir araç olarak [dotnetsay](https://www.nuget.org/packages/dotnetsay/) sürüm 2.0.0 yükler.</span><span class="sxs-lookup"><span data-stu-id="97a94-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="97a94-148">Geçerli dizin için yerel bir araç olarak [dotnetsay](https://www.nuget.org/packages/dotnetsay/) yükler.</span><span class="sxs-lookup"><span data-stu-id="97a94-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="97a94-149">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="97a94-149">See also</span></span>

- [<span data-ttu-id="97a94-150">.NET Çekirdek araçları</span><span class="sxs-lookup"><span data-stu-id="97a94-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="97a94-151">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core global aracı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="97a94-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="97a94-152">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="97a94-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
