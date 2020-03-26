---
title: SLES 15'e .NET Core yükle - paket yöneticisi - .NET Core
description: .NET Core SDK'yı ve çalışma süresini SLES 15'e yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: b86b97bf17165f2f7a70e80ff581750ba39be375
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134182"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="fd9b4-103">SLES 15 Paket Yöneticisi - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="fd9b4-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="fd9b4-104">Bu makalede, SLES 15'e .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="fd9b4-105">Microsoft anahtarını ve akışını kaydetme</span><span class="sxs-lookup"><span data-stu-id="fd9b4-105">Register Microsoft key and feed</span></span>

<span data-ttu-id="fd9b4-106">.NET'i yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="fd9b4-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="fd9b4-107">Microsoft anahtarını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-107">Register the Microsoft key.</span></span>
- <span data-ttu-id="fd9b4-108">Ürün deposunu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-108">Register the product repository.</span></span>
- <span data-ttu-id="fd9b4-109">Gerekli bağımlılıkları yükleyin.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-109">Install required dependencies.</span></span>

<span data-ttu-id="fd9b4-110">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="fd9b4-111">Bir terminal açın ve aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="fd9b4-112">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="fd9b4-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="fd9b4-113">Yükleme için kullanılabilen ürünleri güncelleştirin ve sonra .NET Core SDK'yı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="fd9b4-114">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-114">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="fd9b4-115">ASP.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="fd9b4-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="fd9b4-116">Yükleme için kullanılabilir ürünleri güncelleştirin ve ASP.NET çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="fd9b4-117">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-117">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="fd9b4-118">.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="fd9b4-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="fd9b4-119">Yükleme için kullanılabilen ürünleri güncelleştirin ve .NET Core çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="fd9b4-120">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-120">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="fd9b4-121">Diğer sürümler nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="fd9b4-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="fd9b4-122">Paket yöneticisinin sorun giderme</span><span class="sxs-lookup"><span data-stu-id="fd9b4-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="fd9b4-123">Bu bölümde, .NET Core'u yüklemek için paket yöneticisini kullanırken karşılaşabileceğiniz sık karşılaşılan hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="fd9b4-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="fd9b4-124">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="fd9b4-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-rpm.md)]
