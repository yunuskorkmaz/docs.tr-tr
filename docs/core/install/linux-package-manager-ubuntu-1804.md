---
title: Ubuntu 18,04 paket yöneticisi 'ne .NET Core 'u yükler-.NET Core
description: Ubuntu 18,04 ' de .NET Core SDK ve çalışma zamanı yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 38568b31bf9cd02a19a15addfe4926e8857a87b5
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74959802"
---
# <a name="ubuntu-1804-package-manager---install-net-core"></a><span data-ttu-id="837d3-103">Ubuntu 18,04 paket yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="837d3-103">Ubuntu 18.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="837d3-104">Bu makalede, Ubuntu 18,04 ' de .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="837d3-104">This article describes how to use a package manager to install .NET Core on Ubuntu 18.04.</span></span> <span data-ttu-id="837d3-105">Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="837d3-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="837d3-106">Microsoft anahtarını ve akışını kaydetme</span><span class="sxs-lookup"><span data-stu-id="837d3-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="837d3-107">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="837d3-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="837d3-108">Microsoft anahtarını kaydetme</span><span class="sxs-lookup"><span data-stu-id="837d3-108">Register the Microsoft key</span></span>
- <span data-ttu-id="837d3-109">Ürün deposunu kaydetme</span><span class="sxs-lookup"><span data-stu-id="837d3-109">register the product repository</span></span>
- <span data-ttu-id="837d3-110">Gerekli bağımlılıkları yükler</span><span class="sxs-lookup"><span data-stu-id="837d3-110">Install required dependencies</span></span>

<span data-ttu-id="837d3-111">Bu işlemin makine başına bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="837d3-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="837d3-112">Bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="837d3-112">Open a terminal and run the following commands.</span></span>

```bash
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="837d3-113">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="837d3-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="837d3-114">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="837d3-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="837d3-115">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="837d3-115">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="837d3-116">**DotNet-SDK-3,1**' i bulamıyor gibi bir hata iletisi alırsanız, bkz. [Paket Yöneticisi sorunlarını giderme](#troubleshoot-the-package-manager) bölümü.</span><span class="sxs-lookup"><span data-stu-id="837d3-116">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="837d3-117">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="837d3-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="837d3-118">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından ASP.NET Core çalışma zamanını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="837d3-118">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="837d3-119">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="837d3-119">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="837d3-120">Bir hata iletisi alırsanız, **aspnetcore-Runtime-3,1 paketini bulamazsanız**, bkz. [Package Manager sorunlarını giderme](#troubleshoot-the-package-manager) bölümü.</span><span class="sxs-lookup"><span data-stu-id="837d3-120">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="837d3-121">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="837d3-121">Install the .NET Core runtime</span></span>

<span data-ttu-id="837d3-122">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="837d3-122">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="837d3-123">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="837d3-123">In your terminal, run the following commands.</span></span>

```bash
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="837d3-124">**DotNet-Runtime-3,1 bulunamadı**hatasıyla benzer bir hata iletisi alırsanız, [Paket Yöneticisi sorunlarını giderme](#troubleshoot-the-package-manager) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="837d3-124">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="837d3-125">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="837d3-125">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="837d3-126">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="837d3-126">Troubleshoot the package manager</span></span>

<span data-ttu-id="837d3-127">**{.NET Core Package} paketi bulunamadı**hatasıyla benzer bir hata iletisi alırsanız aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="837d3-127">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="837d3-128">Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="837d3-128">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/ubuntu/18.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```
