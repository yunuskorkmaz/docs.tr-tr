---
title: Debian 9'a .NET Core yükle - paket yöneticisi - .NET Core
description: .NET Core SDK'yı ve çalışma süresini Debian 9'a yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 2e45698d6b87499a54a25b6779ec1a767a2ece6b
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645374"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="77197-103">Debian 9 Paket Yöneticisi - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="77197-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="77197-104">Bu makalede, Debian 9'a .NET Core yüklemek için paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="77197-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="77197-105">Microsoft depo anahtarı ve özet akışı ekleme</span><span class="sxs-lookup"><span data-stu-id="77197-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="77197-106">.NET'i yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="77197-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="77197-107">Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="77197-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="77197-108">Depoyu paket yöneticisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="77197-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="77197-109">Gerekli bağımlılıkları yükleyin.</span><span class="sxs-lookup"><span data-stu-id="77197-109">Install required dependencies.</span></span>

<span data-ttu-id="77197-110">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="77197-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="77197-111">Bir terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="77197-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="77197-112">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="77197-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="77197-113">Yükleme için kullanılabilen ürünleri güncelleştirin ve sonra .NET Core SDK'yı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="77197-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="77197-114">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="77197-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="77197-115">ASP.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="77197-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="77197-116">Yükleme için kullanılabilir ürünleri güncelleştirin ve ASP.NET çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="77197-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="77197-117">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="77197-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="77197-118">.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="77197-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="77197-119">Yükleme için kullanılabilen ürünleri güncelleştirin ve .NET Core çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="77197-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="77197-120">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="77197-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="77197-121">Diğer sürümler nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="77197-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="77197-122">Paket yöneticisinin sorun giderme</span><span class="sxs-lookup"><span data-stu-id="77197-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="77197-123">Bu bölümde, .NET Core'u yüklemek için paket yöneticisini kullanırken karşılaşabileceğiniz sık karşılaşılan hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="77197-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="77197-124">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="77197-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
