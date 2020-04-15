---
title: dotnet aracı geri yükleme komutu
description: Dotnet aracı geri yükleme komutu makinenize geçerli dizinin kapsamı içinde olan .NET Core yerel araçlarını yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 0d1e67ec809ddd725721698cc741f9acc99e1ce7
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389612"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="d37ff-103">dotnet tool restore</span><span class="sxs-lookup"><span data-stu-id="d37ff-103">dotnet tool restore</span></span>

<span data-ttu-id="d37ff-104">**Bu makale şu şekilde dir:** ✔️ .NET Core 3.0 SDK ve sonraki sürümler</span><span class="sxs-lookup"><span data-stu-id="d37ff-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d37ff-105">Adı</span><span class="sxs-lookup"><span data-stu-id="d37ff-105">Name</span></span>

<span data-ttu-id="d37ff-106">`dotnet tool restore`- Makinenize geçerli dizinin kapsamı içinde olan .NET Core yerel araçlarını yükler.</span><span class="sxs-lookup"><span data-stu-id="d37ff-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d37ff-107">Özet</span><span class="sxs-lookup"><span data-stu-id="d37ff-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME>
    [--configfile] [--add-source] [tool-manifest]
    [--disable-parallel] [--ignore-failed-sources]
    [--no-cache] [--interactive] [-v|--verbosity]

dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="d37ff-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d37ff-108">Description</span></span>

<span data-ttu-id="d37ff-109">Komut, `dotnet tool restore` geçerli dizinin kapsamı içinde olan araç bildirimi dosyasını bulur ve içinde listelenen araçları yükler.</span><span class="sxs-lookup"><span data-stu-id="d37ff-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="d37ff-110">Bildirim dosyaları hakkında bilgi için [bkz.](global-tools.md#install-a-local-tool) [Invoke a local tool](global-tools.md#invoke-a-local-tool)</span><span class="sxs-lookup"><span data-stu-id="d37ff-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="d37ff-111">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="d37ff-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="d37ff-112">Yüklemek için .NET Core aracını içeren NuGet paketinin adı/kimliği.</span><span class="sxs-lookup"><span data-stu-id="d37ff-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="d37ff-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="d37ff-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="d37ff-114">NuGet yapılandırması (*nuget.config*) dosyasını kullanmak.</span><span class="sxs-lookup"><span data-stu-id="d37ff-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="d37ff-115">Yükleme sırasında kullanmak üzere ek bir NuGet paket kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="d37ff-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="d37ff-116">Bildirim dosyasına giden yol.</span><span class="sxs-lookup"><span data-stu-id="d37ff-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="d37ff-117">Birden çok projeyi paralel olarak geri getirmeyi önleyin.</span><span class="sxs-lookup"><span data-stu-id="d37ff-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="d37ff-118">Paket kaynağı hatalarını uyarı olarak ele ala.</span><span class="sxs-lookup"><span data-stu-id="d37ff-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="d37ff-119">Paketleri ve http isteklerini önbelleğe almıyor.</span><span class="sxs-lookup"><span data-stu-id="d37ff-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="d37ff-120">Komutun durmasına ve kullanıcı girişinin veya eylemini beklemesine izin verir (örneğin kimlik doğrulamasını tamamlamak için).</span><span class="sxs-lookup"><span data-stu-id="d37ff-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="d37ff-121">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="d37ff-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="d37ff-122">Komutun ayrıntılı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d37ff-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d37ff-123">İzin verilen `q[uiet]` `m[inimal]`değerler `n[ormal]` `d[etailed]`, `diag[nostic]`, , , ve .</span><span class="sxs-lookup"><span data-stu-id="d37ff-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="d37ff-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="d37ff-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="d37ff-125">Geçerli dizin için yerel araçları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="d37ff-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="d37ff-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d37ff-126">See also</span></span>

- [<span data-ttu-id="d37ff-127">.NET Çekirdek araçları</span><span class="sxs-lookup"><span data-stu-id="d37ff-127">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="d37ff-128">Öğretici: .NET Core CLI'yi kullanarak bir .NET Core yerel aracı nı yükleyin ve kullanın</span><span class="sxs-lookup"><span data-stu-id="d37ff-128">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
