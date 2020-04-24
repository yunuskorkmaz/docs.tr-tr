---
title: openSUSE 15 'e install .NET Core - paket yöneticisi - .NET Core
description: OpenSUSE 15'e .NET Core SDK ve çalışma süresini yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: fc4c9e30ddb0cfd3e6fe79fa4f78206f4700eeee
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645672"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="e6575-103">openSUSE 15 Paket Yöneticisi - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="e6575-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="e6575-104">Bu makalede, openSUSE 15'e .NET Core yüklemek için paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e6575-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="e6575-105">Microsoft depo anahtarı ve özet akışı ekleme</span><span class="sxs-lookup"><span data-stu-id="e6575-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="e6575-106">.NET'i yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="e6575-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="e6575-107">Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e6575-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="e6575-108">Depoyu paket yöneticisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="e6575-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="e6575-109">Gerekli bağımlılıkları yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e6575-109">Install required dependencies.</span></span>

<span data-ttu-id="e6575-110">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="e6575-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="e6575-111">Bir terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e6575-111">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="e6575-112">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="e6575-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="e6575-113">Yükleme için kullanılabilen ürünleri güncelleştirin ve sonra .NET Core SDK'yı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e6575-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="e6575-114">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e6575-114">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="e6575-115">ASP.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="e6575-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="e6575-116">Yükleme için kullanılabilir ürünleri güncelleştirin ve ASP.NET çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e6575-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="e6575-117">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e6575-117">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="e6575-118">.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="e6575-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="e6575-119">Yükleme için kullanılabilen ürünleri güncelleştirin ve .NET Core çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e6575-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="e6575-120">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="e6575-120">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="e6575-121">Diğer sürümler nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="e6575-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="e6575-122">Paket yöneticisinin sorun giderme</span><span class="sxs-lookup"><span data-stu-id="e6575-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="e6575-123">Bu bölümde, .NET Core'u yüklemek için paket yöneticisini kullanırken karşılaşabileceğiniz sık karşılaşılan hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="e6575-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="e6575-124">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="e6575-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
