---
title: Debian 10'a .NET Core yükle - paket yöneticisi - .NET Core
description: .NET Core SDK'yı ve çalışma süresini Debian 10'a yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: a312496ed9a26783198cdd038db7ffa2bdc7381e
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645286"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="cb2ab-103">Debian 10 Paket Yöneticisi - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="cb2ab-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="cb2ab-104">Bu makalede, Debian 10'a .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="cb2ab-105">Microsoft depo anahtarı ve özet akışı ekleme</span><span class="sxs-lookup"><span data-stu-id="cb2ab-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="cb2ab-106">.NET'i yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="cb2ab-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="cb2ab-107">Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="cb2ab-108">Depoyu paket yöneticisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="cb2ab-109">Gerekli bağımlılıkları yükleyin.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-109">Install required dependencies.</span></span>

<span data-ttu-id="cb2ab-110">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="cb2ab-111">Bir terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="cb2ab-112">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="cb2ab-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="cb2ab-113">Yükleme için kullanılabilen ürünleri güncelleştirin ve sonra .NET Core SDK'yı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="cb2ab-114">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="cb2ab-115">ASP.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="cb2ab-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="cb2ab-116">Yükleme için kullanılabilir ürünleri güncelleştirin ve ASP.NET çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="cb2ab-117">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="cb2ab-118">.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="cb2ab-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="cb2ab-119">Yükleme için kullanılabilen ürünleri güncelleştirin ve .NET Core çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="cb2ab-120">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="cb2ab-121">Diğer sürümler nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="cb2ab-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="cb2ab-122">Paket yöneticisinin sorun giderme</span><span class="sxs-lookup"><span data-stu-id="cb2ab-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="cb2ab-123">Bu bölümde, .NET Core'u yüklemek için paket yöneticisini kullanırken karşılaşabileceğiniz sık karşılaşılan hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="cb2ab-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="cb2ab-124">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="cb2ab-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
