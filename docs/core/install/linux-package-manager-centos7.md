---
title: CentOS 7'ye .NET Core yükle - paket yöneticisi - .NET Core
description: CentOS 7'ye .NET Core SDK ve çalışma süresini yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: f8c4115b9d85edc36809f0daed5f6825149c8411
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645410"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="5c8d4-103">CentOS 7 Paket Yöneticisi - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="5c8d4-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="5c8d4-104">Bu makalede, CentOS 7'ye .NET Core yüklemek için paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="5c8d4-105">Microsoft depo anahtarı ve özet akışı ekleme</span><span class="sxs-lookup"><span data-stu-id="5c8d4-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="5c8d4-106">.NET'i yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="5c8d4-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="5c8d4-107">Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="5c8d4-108">Depoyu paket yöneticisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="5c8d4-109">Gerekli bağımlılıkları yükleyin.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-109">Install required dependencies.</span></span>

<span data-ttu-id="5c8d4-110">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="5c8d4-111">Bir terminal açın ve aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="5c8d4-112">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="5c8d4-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="5c8d4-113">Yükleme için kullanılabilen ürünleri güncelleştirin ve sonra .NET Core SDK'yı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="5c8d4-114">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-114">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="5c8d4-115">ASP.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="5c8d4-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="5c8d4-116">Yükleme için kullanılabilir ürünleri güncelleştirin ve ASP.NET çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="5c8d4-117">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-117">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="5c8d4-118">.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="5c8d4-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="5c8d4-119">Yükleme için kullanılabilen ürünleri güncelleştirin ve .NET Core çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="5c8d4-120">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-120">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="5c8d4-121">Diğer sürümler nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="5c8d4-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="5c8d4-122">Paket yöneticisinin sorun giderme</span><span class="sxs-lookup"><span data-stu-id="5c8d4-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="5c8d4-123">Bu bölümde, .NET Core'u yüklemek için paket yöneticisini kullanırken karşılaşabileceğiniz sık karşılaşılan hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5c8d4-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="5c8d4-124">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="5c8d4-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
