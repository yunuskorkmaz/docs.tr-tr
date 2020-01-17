---
title: .NET Core 'u Fedora 31-Package Manager-.NET Core 'a yükler
description: .NET Core SDK ve çalışma zamanını Fedora 31 ' de yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/17/2019
ms.openlocfilehash: 25c670694ed2d9e89fe37cedf0b06efd8bc93293
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116968"
---
# <a name="fedora-31-package-manager---install-net-core"></a><span data-ttu-id="be238-103">Fedora 31 Paket Yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="be238-103">Fedora 31 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="be238-104">Bu makalede, Fedora 31 ' de .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="be238-104">This article describes how to use a package manager to install .NET Core on Fedora 31.</span></span> <span data-ttu-id="be238-105">Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="be238-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="be238-106">Microsoft anahtarını ve akışını kaydetme</span><span class="sxs-lookup"><span data-stu-id="be238-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="be238-107">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="be238-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="be238-108">Microsoft anahtarını kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="be238-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="be238-109">Ürün deposunu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="be238-109">Register the product repository.</span></span>
- <span data-ttu-id="be238-110">Gerekli bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="be238-110">Install required dependencies.</span></span>

<span data-ttu-id="be238-111">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="be238-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="be238-112">Bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="be238-112">Open a terminal and run the following commands.</span></span>

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -q -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/fedora/31/prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="be238-113">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="be238-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="be238-114">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="be238-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="be238-115">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="be238-115">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="be238-116">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="be238-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="be238-117">Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme.</span><span class="sxs-lookup"><span data-stu-id="be238-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="be238-118">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="be238-118">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="be238-119">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="be238-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="be238-120">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="be238-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="be238-121">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="be238-121">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="be238-122">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="be238-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
