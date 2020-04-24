---
title: Ubuntu 16.04 paket yöneticisine .NET Core yükle - .NET Core
description: .NET Core SDK'yı ve çalışma süresini Ubuntu 16.04'e yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 13aa23cb82b2e135ea818aed8d2a7e0e25366afd
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645636"
---
# <a name="ubuntu-1604-package-manager---install-net-core"></a><span data-ttu-id="0054c-103">Ubuntu 16.04 Paket Yöneticisi - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="0054c-103">Ubuntu 16.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="0054c-104">Bu makalede, Ubuntu 16.04'e .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0054c-104">This article describes how to use a package manager to install .NET Core on Ubuntu 16.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="0054c-105">Microsoft depo anahtarı ve özet akışı ekleme</span><span class="sxs-lookup"><span data-stu-id="0054c-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="0054c-106">.NET'i yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="0054c-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="0054c-107">Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0054c-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="0054c-108">Depoyu paket yöneticisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="0054c-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="0054c-109">Gerekli bağımlılıkları yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0054c-109">Install required dependencies.</span></span>

<span data-ttu-id="0054c-110">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="0054c-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="0054c-111">Bir terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0054c-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="0054c-112">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="0054c-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="0054c-113">Yükleme için kullanılabilen ürünleri güncelleştirin ve sonra .NET Core SDK'yı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0054c-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="0054c-114">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0054c-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="0054c-115">**Paket dotnet-sdk-3.1'i bulamayınca**benzer bir hata iletisi alırsanız, [sorun giderme bölümüne](#troubleshoot-the-package-manager) bakın.</span><span class="sxs-lookup"><span data-stu-id="0054c-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="0054c-116">ASP.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="0054c-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="0054c-117">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından ASP.NET Core çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0054c-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="0054c-118">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0054c-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="0054c-119">**Aspnetcore-runtime-3.1 paketini bulamayınca**benzer bir hata iletisi alırsanız, [Sorun Giderme Bölümü'ne](#troubleshoot-the-package-manager) bakın.</span><span class="sxs-lookup"><span data-stu-id="0054c-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="0054c-120">.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="0054c-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="0054c-121">Yükleme için kullanılabilen ürünleri güncelleştirin ve .NET Core çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="0054c-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="0054c-122">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0054c-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="0054c-123">**Paket dotnet-runtime-3.1'i bulamayınca**benzer bir hata iletisi alırsanız, [sorun giderme bölümüne](#troubleshoot-the-package-manager) bakın.</span><span class="sxs-lookup"><span data-stu-id="0054c-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="0054c-124">Diğer sürümler nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="0054c-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="0054c-125">Paket yöneticisinin sorun giderme</span><span class="sxs-lookup"><span data-stu-id="0054c-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="0054c-126">Bu bölümde, .NET Core'u yüklemek için paket yöneticisini kullanırken karşılaşabileceğiniz sık karşılaşılan hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="0054c-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="0054c-127">Bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="0054c-127">Unable to locate</span></span>

<span data-ttu-id="0054c-128">**{.NET Core paketi} paketini bulamayıncabenzer**bir hata iletisi alırsanız, aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0054c-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="0054c-129">Bu işe yaramazsa, aşağıdaki komutları içeren bir el ile yükleme çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0054c-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/16.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="0054c-130">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="0054c-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
