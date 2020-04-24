---
title: Fedora 29'a .NET Core yükle - paket yöneticisi - .NET Core
description: .NET Core SDK'yı ve çalışma süresini Fedora 29'a yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: d1cbe38f4f104a8e178d8bcfd1fa1bd6d7645261
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645305"
---
# <a name="fedora-29-package-manager---install-net-core"></a><span data-ttu-id="427d3-103">Fedora 29 Paket Yöneticisi - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="427d3-103">Fedora 29 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="427d3-104">Bu makalede, Fedora 29'a .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="427d3-104">This article describes how to use a package manager to install .NET Core on Fedora 29.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="427d3-105">Microsoft depo anahtarı ve özet akışı ekleme</span><span class="sxs-lookup"><span data-stu-id="427d3-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="427d3-106">.NET'i yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="427d3-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="427d3-107">Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="427d3-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="427d3-108">Depoyu paket yöneticisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="427d3-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="427d3-109">Gerekli bağımlılıkları yükleyin.</span><span class="sxs-lookup"><span data-stu-id="427d3-109">Install required dependencies.</span></span>

<span data-ttu-id="427d3-110">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="427d3-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="427d3-111">Bir terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="427d3-111">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="427d3-112">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="427d3-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="427d3-113">Yükleme için kullanılabilen ürünleri güncelleştirin ve sonra .NET Core SDK'yı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="427d3-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="427d3-114">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="427d3-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="427d3-115">ASP.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="427d3-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="427d3-116">Yükleme için kullanılabilir ürünleri güncelleştirin ve ASP.NET çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="427d3-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="427d3-117">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="427d3-117">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="427d3-118">.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="427d3-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="427d3-119">Yükleme için kullanılabilen ürünleri güncelleştirin ve .NET Core çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="427d3-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="427d3-120">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="427d3-120">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="427d3-121">Diğer sürümler nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="427d3-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="427d3-122">Paket yöneticisinin sorun giderme</span><span class="sxs-lookup"><span data-stu-id="427d3-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="427d3-123">Bu bölümde, .NET Core'u yüklemek için paket yöneticisini kullanırken karşılaşabileceğiniz sık karşılaşılan hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="427d3-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="427d3-124">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="427d3-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
