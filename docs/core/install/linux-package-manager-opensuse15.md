---
title: OpenSUSE 15-Package Manager-.NET Core 'a .NET Core 'u yükler
description: OpenSUSE 15 üzerinde .NET Core SDK ve çalışma zamanı yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: aaece5e3554ab567cf82c23265c8fba1656298d8
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920766"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="e23b1-103">openSUSE 15 Paket Yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="e23b1-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="e23b1-104">Bu makalede, openSUSE 15 ' te .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="e23b1-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span> <span data-ttu-id="e23b1-105">Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="e23b1-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="e23b1-106">Microsoft anahtar ve akışını Kaydet</span><span class="sxs-lookup"><span data-stu-id="e23b1-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="e23b1-107">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="e23b1-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="e23b1-108">Microsoft anahtarını kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="e23b1-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="e23b1-109">Ürün deposunu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="e23b1-109">Register the product repository.</span></span>
- <span data-ttu-id="e23b1-110">Gerekli bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="e23b1-110">Install required dependencies.</span></span>

<span data-ttu-id="e23b1-111">Bu, makine başına yalnızca bir kez yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e23b1-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="e23b1-112">Bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e23b1-112">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="e23b1-113">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="e23b1-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="e23b1-114">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="e23b1-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="e23b1-115">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e23b1-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="e23b1-116">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="e23b1-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="e23b1-117">Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme.</span><span class="sxs-lookup"><span data-stu-id="e23b1-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="e23b1-118">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e23b1-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="e23b1-119">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="e23b1-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="e23b1-120">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="e23b1-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="e23b1-121">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e23b1-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e23b1-122">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="e23b1-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="e23b1-123">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="e23b1-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="e23b1-124">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e23b1-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="e23b1-125">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="e23b1-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
