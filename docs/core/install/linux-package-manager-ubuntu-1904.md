---
title: Ubuntu 19,04 paket yöneticisi 'ne .NET Core 'u yükler-.NET Core
description: Ubuntu 19,04 ' de .NET Core SDK ve çalışma zamanı yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: df7f2b093c91a0056f612f167450b5244ebd451c
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595669"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a><span data-ttu-id="4c34c-103">Ubuntu 19,04 paket yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="4c34c-103">Ubuntu 19.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="4c34c-104">Bu makalede, Ubuntu 19,04 ' de .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="4c34c-104">This article describes how to use a package manager to install .NET Core on Ubuntu 19.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="4c34c-105">Microsoft Repository anahtarı ve akışı Ekle</span><span class="sxs-lookup"><span data-stu-id="4c34c-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="4c34c-106">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="4c34c-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="4c34c-107">Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c34c-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="4c34c-108">Depoyu paket yöneticisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="4c34c-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="4c34c-109">Gerekli bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="4c34c-109">Install required dependencies.</span></span>

<span data-ttu-id="4c34c-110">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="4c34c-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="4c34c-111">Bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c34c-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="4c34c-112">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="4c34c-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="4c34c-113">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="4c34c-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="4c34c-114">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c34c-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="4c34c-115">**DotNet-SDK-3,1**' i bulamıyor gibi bir hata iletisi alırsanız, bkz. [Paket Yöneticisi sorunlarını giderme](#troubleshoot-the-package-manager) bölümü.</span><span class="sxs-lookup"><span data-stu-id="4c34c-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="4c34c-116">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="4c34c-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="4c34c-117">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından ASP.NET Core çalışma zamanını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="4c34c-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="4c34c-118">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c34c-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="4c34c-119">Bir hata iletisi alırsanız, **aspnetcore-Runtime-3,1 paketini bulamazsanız**, bkz. [Package Manager sorunlarını giderme](#troubleshoot-the-package-manager) bölümü.</span><span class="sxs-lookup"><span data-stu-id="4c34c-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="4c34c-120">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="4c34c-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="4c34c-121">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="4c34c-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="4c34c-122">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c34c-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="4c34c-123">**DotNet-Runtime-3,1 bulunamadı**hatasıyla benzer bir hata iletisi alırsanız, [Paket Yöneticisi sorunlarını giderme](#troubleshoot-the-package-manager) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="4c34c-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="4c34c-124">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="4c34c-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="4c34c-125">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="4c34c-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="4c34c-126">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4c34c-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="4c34c-127">Bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="4c34c-127">Unable to locate</span></span>

<span data-ttu-id="4c34c-128">**{.NET Core Package} paketi bulunamadı**hatasıyla benzer bir hata iletisi alırsanız aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c34c-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="4c34c-129">Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4c34c-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="4c34c-130">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="4c34c-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
