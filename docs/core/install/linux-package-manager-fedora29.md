---
title: Fedora 29'a .NET Core yükle - paket yöneticisi - .NET Core
description: .NET Core SDK'yı ve çalışma süresini Fedora 29'a yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: d917c867e0d8cdb066b7dee64a9dbd767b56072d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920803"
---
# <a name="fedora-29-package-manager---install-net-core"></a><span data-ttu-id="4c604-103">Fedora 29 Paket Yöneticisi - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="4c604-103">Fedora 29 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="4c604-104">Bu makalede, Fedora 29'a .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4c604-104">This article describes how to use a package manager to install .NET Core on Fedora 29.</span></span> <span data-ttu-id="4c604-105">Çalışma süresini yüklüyorsanız, hem .NET Core hem de ASP.NET Core [çalışma sürelerini içerdiğinden, ASP.NET Core çalışma süresini](#install-the-aspnet-core-runtime)yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="4c604-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="4c604-106">Microsoft anahtarını ve akışını kaydetme</span><span class="sxs-lookup"><span data-stu-id="4c604-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="4c604-107">.NET'i yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="4c604-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="4c604-108">Microsoft anahtarını kaydedin.</span><span class="sxs-lookup"><span data-stu-id="4c604-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="4c604-109">Ürün deposunu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="4c604-109">Register the product repository.</span></span>
- <span data-ttu-id="4c604-110">Gerekli bağımlılıkları yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4c604-110">Install required dependencies.</span></span>

<span data-ttu-id="4c604-111">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="4c604-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="4c604-112">Bir terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c604-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/29/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="4c604-113">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="4c604-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="4c604-114">Yükleme için kullanılabilen ürünleri güncelleştirin ve sonra .NET Core SDK'yı yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4c604-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="4c604-115">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c604-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="4c604-116">ASP.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="4c604-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="4c604-117">Yükleme için kullanılabilir ürünleri güncelleştirin ve ASP.NET çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4c604-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="4c604-118">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c604-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="4c604-119">.NET Core çalışma süresini yükleme</span><span class="sxs-lookup"><span data-stu-id="4c604-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="4c604-120">Yükleme için kullanılabilen ürünleri güncelleştirin ve .NET Core çalışma süresini yükleyin.</span><span class="sxs-lookup"><span data-stu-id="4c604-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="4c604-121">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="4c604-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="4c604-122">Diğer sürümler nasıl yüklenir?</span><span class="sxs-lookup"><span data-stu-id="4c604-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="4c604-123">Paket yöneticisinin sorun giderme</span><span class="sxs-lookup"><span data-stu-id="4c604-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="4c604-124">Bu bölümde, .NET Core'u yüklemek için paket yöneticisini kullanırken karşılaşabileceğiniz sık karşılaşılan hatalar hakkında bilgi verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="4c604-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="4c604-125">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="4c604-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
