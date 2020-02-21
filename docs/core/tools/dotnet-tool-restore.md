---
title: DotNet aracı geri yükleme komutu
description: DotNet aracı geri yükleme komutu, makinenizde geçerli dizin için kapsamdaki .NET Core yerel araçları yükler.
ms.date: 02/14/2020
ms.openlocfilehash: 2900d431987661a9232ceed10d9a424093f8be45
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543910"
---
# <a name="dotnet-tool-restore"></a><span data-ttu-id="2a242-103">DotNet aracı geri yükleme</span><span class="sxs-lookup"><span data-stu-id="2a242-103">dotnet tool restore</span></span>

<span data-ttu-id="2a242-104">**Bu makale şu şekilde geçerlidir:** ✔️ .net Core 3,0 SDK ve sonraki sürümleri</span><span class="sxs-lookup"><span data-stu-id="2a242-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2a242-105">Adı</span><span class="sxs-lookup"><span data-stu-id="2a242-105">Name</span></span>

<span data-ttu-id="2a242-106">`dotnet tool restore`-makinenizde geçerli dizin için kapsamdaki .NET Core yerel araçları yüklenir.</span><span class="sxs-lookup"><span data-stu-id="2a242-106">`dotnet tool restore` - Installs on your machine the .NET Core local tools that are in scope for the current directory.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2a242-107">Özeti</span><span class="sxs-lookup"><span data-stu-id="2a242-107">Synopsis</span></span>

```dotnetcli
dotnet tool restore <PACKAGE_NAME> [--configfile] [--add-source] [tool-manifest] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [-interactive] [-v|--verbosity]
dotnet tool restore <-h|--help>
```

## <a name="description"></a><span data-ttu-id="2a242-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2a242-108">Description</span></span>

<span data-ttu-id="2a242-109">`dotnet tool restore` komutu, geçerli dizinin kapsamındaki araç bildirim dosyasını bulur ve içinde listelenen araçları kurar.</span><span class="sxs-lookup"><span data-stu-id="2a242-109">The `dotnet tool restore` command finds the tool manifest file that is in scope for the current directory and installs the tools that are listed in it.</span></span> <span data-ttu-id="2a242-110">Bildirim dosyaları hakkında daha fazla bilgi için bkz. [yerel araç yükleyip](global-tools.md#install-a-local-tool) [yerel bir araç çağırma](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="2a242-110">For information about manifest files, see [Install a local tool](global-tools.md#install-a-local-tool) and [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="2a242-111">Bağımsız Değişkenler</span><span class="sxs-lookup"><span data-stu-id="2a242-111">Arguments</span></span>

- **`PACKAGE_NAME`**

<span data-ttu-id="2a242-112">Yüklenecek .NET Core aracını içeren NuGet paketinin adı/KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2a242-112">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="2a242-113">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="2a242-113">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="2a242-114">Kullanılacak NuGet yapılandırma (*NuGet. config*) dosyası.</span><span class="sxs-lookup"><span data-stu-id="2a242-114">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="2a242-115">Yükleme sırasında kullanmak üzere ek bir NuGet paketi kaynağı ekler.</span><span class="sxs-lookup"><span data-stu-id="2a242-115">Adds an additional NuGet package source to use during installation.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="2a242-116">Bildirim dosyasının yolu.</span><span class="sxs-lookup"><span data-stu-id="2a242-116">Path to the manifest file.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="2a242-117">Paralel olarak birden çok projenin geri yüklenmesini engelleyin.</span><span class="sxs-lookup"><span data-stu-id="2a242-117">Prevent restoring multiple projects in parallel.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="2a242-118">Paket kaynağı başarısızlıklarını uyarı olarak değerlendirin.</span><span class="sxs-lookup"><span data-stu-id="2a242-118">Treat package source failures as warnings.</span></span>

- **`--no-cache`**

  <span data-ttu-id="2a242-119">Paketleri ve http isteklerini önbelleğe vermeyin.</span><span class="sxs-lookup"><span data-stu-id="2a242-119">Do not cache packages and http requests.</span></span>

- **`--interactive`**

  <span data-ttu-id="2a242-120">Komutun Kullanıcı girişini veya eylemini durdurmasına ve beklemesine izin verir (örneğin, kimlik doğrulamasını tamamlamaya).</span><span class="sxs-lookup"><span data-stu-id="2a242-120">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`-h|--help`**

  <span data-ttu-id="2a242-121">Komut için kısa bir yardım yazdırır.</span><span class="sxs-lookup"><span data-stu-id="2a242-121">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="2a242-122">Komutun ayrıntı düzeyini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="2a242-122">Sets the verbosity level of the command.</span></span> <span data-ttu-id="2a242-123">İzin verilen değerler `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`ve `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="2a242-123">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="example"></a><span data-ttu-id="2a242-124">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a242-124">Example</span></span>

- **`dotnet tool restore`**

  <span data-ttu-id="2a242-125">Geçerli dizin için yerel araçları geri yükler.</span><span class="sxs-lookup"><span data-stu-id="2a242-125">Restores local tools for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a242-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a242-126">See also</span></span>

- [<span data-ttu-id="2a242-127">.NET Core araçları</span><span class="sxs-lookup"><span data-stu-id="2a242-127">.NET Core tools</span></span>](global-tools.md)
