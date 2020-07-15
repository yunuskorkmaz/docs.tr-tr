---
title: DotNet Aracı güncelleştirme komutu
description: DotNet Aracı güncelleştirme komutu makinenizde belirtilen .NET Core aracını güncelleştirir.
ms.date: 07/08/2020
ms.openlocfilehash: a212fbb40af68019c1bc9a63963d960292be6b08
ms.sourcegitcommit: 0fa2b7b658bf137e813a7f4d09589d64c148ebf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/14/2020
ms.locfileid: "86308877"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="20053-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="20053-103">dotnet tool update</span></span>

<span data-ttu-id="20053-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 2,1 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="20053-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="20053-105">Name</span><span class="sxs-lookup"><span data-stu-id="20053-105">Name</span></span>

<span data-ttu-id="20053-106">`dotnet tool update`-Makinenizde belirtilen [.NET Core aracını](global-tools.md) güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="20053-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="20053-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="20053-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--disable-parallel] [--framework <FRAMEWORK>]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="20053-108">Description</span><span class="sxs-lookup"><span data-stu-id="20053-108">Description</span></span>

<span data-ttu-id="20053-109">Bu `dotnet tool update` komut, makinenizde .NET Core araçlarını paketin en son kararlı sürümüne güncelleştirmeniz için bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="20053-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="20053-110">Komut, bir aracı kaldırır ve etkin bir şekilde güncelleştiren bir araç yükler.</span><span class="sxs-lookup"><span data-stu-id="20053-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="20053-111">Komutunu kullanmak için aşağıdaki seçeneklerden birini belirtin:</span><span class="sxs-lookup"><span data-stu-id="20053-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="20053-112">Varsayılan konumda yüklü olan küresel bir aracı güncelleştirmek için, seçeneğini kullanın. `--global`</span><span class="sxs-lookup"><span data-stu-id="20053-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="20053-113">Özel bir konuma yüklenmiş olan küresel bir aracı güncelleştirmek için `--tool-path` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="20053-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="20053-114">Yerel bir aracı güncelleştirmek için `--local` seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="20053-114">To update a local tool, use the `--local` option.</span></span>

<span data-ttu-id="20053-115">**Yerel araçlar .NET Core SDK 3,0 ' den başlayarak kullanılabilir.**</span><span class="sxs-lookup"><span data-stu-id="20053-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="20053-116">Arguments</span><span class="sxs-lookup"><span data-stu-id="20053-116">Arguments</span></span>

- **`PACKAGE_ID`**

  <span data-ttu-id="20053-117">Güncelleştirilecek .NET Core küresel aracını içeren NuGet paketinin adı/KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="20053-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="20053-118">[DotNet araç listesi](dotnet-tool-list.md) komutunu kullanarak paket adını bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="20053-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="20053-119">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="20053-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="20053-120">Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="20053-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="20053-121">Kullanılacak NuGet yapılandırma (*nuget.config*) dosyası.</span><span class="sxs-lookup"><span data-stu-id="20053-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="20053-122">Paralel olarak birden çok projenin geri yüklenmesini engelleyin.</span><span class="sxs-lookup"><span data-stu-id="20053-122">Prevent restoring multiple projects in parallel.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="20053-123">Aracının güncelleştirilmesi için [hedef çerçeveyi](../../standard/frameworks.md) belirtir.</span><span class="sxs-lookup"><span data-stu-id="20053-123">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="20053-124">Paket kaynağı başarısızlıklarını uyarı olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="20053-124">Treat package source failures as warnings.</span></span>

- **`--interactive`**

  <span data-ttu-id="20053-125">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya).</span><span class="sxs-lookup"><span data-stu-id="20053-125">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`--local`**

  <span data-ttu-id="20053-126">Aracı ve yerel araç bildirimini güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="20053-126">Update the tool and the local tool manifest.</span></span> <span data-ttu-id="20053-127">`--global`Seçeneği veya seçeneği ile birleştirilemez `--tool-path` .</span><span class="sxs-lookup"><span data-stu-id="20053-127">Can't be combined with the `--global` option or the `--tool-path` option.</span></span>

- **`--no-cache`**

  <span data-ttu-id="20053-128">Paketleri ve HTTP isteklerini önbelleğe vermeyin.</span><span class="sxs-lookup"><span data-stu-id="20053-128">Do not cache packages and HTTP requests.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="20053-129">Bildirim dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="20053-129">Path to the manifest file.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="20053-130">Genel aracın yüklendiği konumu belirtir.</span><span class="sxs-lookup"><span data-stu-id="20053-130">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="20053-131">YOL mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="20053-131">PATH can be absolute or relative.</span></span> <span data-ttu-id="20053-132">`--global`Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="20053-132">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="20053-133">Her ikisini de atlayarak, `--global` `--tool-path` güncelleşmiş olan aracın yerel bir araç olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="20053-133">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`--version <VERSION>`**

  <span data-ttu-id="20053-134">Güncelleştirilecek araç paketinin sürüm aralığı.</span><span class="sxs-lookup"><span data-stu-id="20053-134">The version range of the tool package to update to.</span></span> <span data-ttu-id="20053-135">Bu, sürümleri düşürme için kullanılamaz, `uninstall` önce yeni sürümlere sahip olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="20053-135">This cannot be used to downgrade versions, you must `uninstall` newer versions first.</span></span>

- **`-g|--global`**

  <span data-ttu-id="20053-136">Güncelleştirmenin Kullanıcı genelindeki bir araç için olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="20053-136">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="20053-137">`--tool-path`Seçeneğiyle birleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="20053-137">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="20053-138">Her ikisini de atlayarak, `--global` `--tool-path` güncelleşmiş olan aracın yerel bir araç olduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="20053-138">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="20053-139">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="20053-139">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="20053-140">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="20053-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="20053-141">İzin verilen değerler,,, `q[uiet]` `m[inimal]` `n[ormal]` `d[etailed]` ve `diag[nostic]` .</span><span class="sxs-lookup"><span data-stu-id="20053-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="20053-142">Örnekler</span><span class="sxs-lookup"><span data-stu-id="20053-142">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="20053-143">[Dotnetsay](https://www.nuget.org/packages/dotnetsay/) küresel aracını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="20053-143">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="20053-144">Belirli bir Windows dizininde bulunan [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracı 'nı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="20053-144">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="20053-145">Belirli bir Linux/macOS dizininde bulunan [dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracı 'nı güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="20053-145">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="20053-146">Geçerli dizin için yüklenen [dotnetsöyleme](https://www.nuget.org/packages/dotnetsay/) yerel aracını güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="20053-146">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  <span data-ttu-id="20053-147">[Dotnetsöyleyin](https://www.nuget.org/packages/dotnetsay/) küresel aracını en son düzeltme eki sürümüne, ana sürümüne `2` ve ikincil sürümüne günceller `0` .</span><span class="sxs-lookup"><span data-stu-id="20053-147">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the latest patch version, with a major version of `2`, and a minor version of `0`.</span></span>

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  <span data-ttu-id="20053-148">[Dotnetdeyin](https://www.nuget.org/packages/dotnetsay/) küresel aracı 'nı belirtilen aralıktaki en düşük sürümle güncelleştirir `(> 2.0.0 && < 2.1.4)` , sürüm `2.1.0` yüklenir.</span><span class="sxs-lookup"><span data-stu-id="20053-148">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the lowest version within the specified range `(> 2.0.0 && < 2.1.4)`, version `2.1.0` would be installed.</span></span> <span data-ttu-id="20053-149">Anlamsal sürüm oluşturma aralıkları hakkında daha fazla bilgi için bkz. [NuGet paketleme sürümü aralıkları](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="20053-149">For more information on semantic versioning ranges, see [NuGet packaging version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

## <a name="see-also"></a><span data-ttu-id="20053-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20053-150">See also</span></span>

- [<span data-ttu-id="20053-151">.NET Core araçları</span><span class="sxs-lookup"><span data-stu-id="20053-151">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="20053-152">Anlamsal sürüm oluşturma</span><span class="sxs-lookup"><span data-stu-id="20053-152">Semantic versioning</span></span>](https://semver.org)
- [<span data-ttu-id="20053-153">Öğretici: .NET Core CLI kullanarak .NET Core küresel aracı 'nı yükleyip kullanın</span><span class="sxs-lookup"><span data-stu-id="20053-153">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="20053-154">Öğretici: .NET Core CLI kullanarak bir .NET Core yerel aracı yükleyip kullanın</span><span class="sxs-lookup"><span data-stu-id="20053-154">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
