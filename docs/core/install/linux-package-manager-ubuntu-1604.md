---
title: Ubuntu 16,04 paket yöneticisi 'ne .NET Core 'u yükler-.NET Core
description: Ubuntu 16,04 ' de .NET Core SDK ve çalışma zamanı yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 6038e64a2aa50d09923454e346f05c58a6c1e2fb
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920707"
---
# <a name="ubuntu-1604-package-manager---install-net-core"></a><span data-ttu-id="8d0ec-103">Ubuntu 16,04 paket yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="8d0ec-103">Ubuntu 16.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="8d0ec-104">Bu makalede, Ubuntu 16,04 ' de .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-104">This article describes how to use a package manager to install .NET Core on Ubuntu 16.04.</span></span> <span data-ttu-id="8d0ec-105">Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="8d0ec-106">Microsoft anahtar ve akışını Kaydet</span><span class="sxs-lookup"><span data-stu-id="8d0ec-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="8d0ec-107">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8d0ec-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="8d0ec-108">Microsoft anahtarını kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="8d0ec-109">Ürün deposunu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-109">Register the product repository.</span></span>
- <span data-ttu-id="8d0ec-110">Gerekli bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-110">Install required dependencies.</span></span>

<span data-ttu-id="8d0ec-111">Bu, makine başına yalnızca bir kez yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="8d0ec-112">Bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="8d0ec-113">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="8d0ec-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="8d0ec-114">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="8d0ec-115">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="8d0ec-116">**DotNet-SDK-3,1**' i bulamıyor gibi bir hata iletisi alırsanız, bkz. [Paket Yöneticisi sorunlarını giderme](#troubleshoot-the-package-manager) bölümü.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="8d0ec-117">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="8d0ec-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="8d0ec-118">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından ASP.NET Core çalışma zamanını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="8d0ec-119">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-119">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="8d0ec-120">Bir hata iletisi alırsanız, **aspnetcore-Runtime-3,1 paketini bulamazsanız**, bkz. [Package Manager sorunlarını giderme](#troubleshoot-the-package-manager) bölümü.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="8d0ec-121">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="8d0ec-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="8d0ec-122">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="8d0ec-123">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-123">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="8d0ec-124">**DotNet-Runtime-3,1 bulunamadı**hatasıyla benzer bir hata iletisi alırsanız, [Paket Yöneticisi sorunlarını giderme](#troubleshoot-the-package-manager) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="8d0ec-125">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="8d0ec-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="8d0ec-126">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="8d0ec-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="8d0ec-127">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-127">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="8d0ec-128">Bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="8d0ec-128">Unable to locate</span></span>

<span data-ttu-id="8d0ec-129">**{.NET Core Package} paketi bulunamadı**hatasıyla benzer bir hata iletisi alırsanız aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-129">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="8d0ec-130">Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8d0ec-130">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/16.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="8d0ec-131">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="8d0ec-131">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
