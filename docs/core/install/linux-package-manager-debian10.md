---
title: .NET Core 'u detem 10-Package Manager 'a (.NET Core) yükler
description: .NET Core SDK ve çalışma zamanını de, 10 ' da yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: 94bcb493536bdee71ba83053d9e671d529226ac3
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920829"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="149b9-103">Detem 10 Package Manager-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="149b9-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="149b9-104">Bu makalede, bir paket yöneticisinin .NET Core 'u de, 10 ' da yüklemek için nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="149b9-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span> <span data-ttu-id="149b9-105">Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="149b9-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="149b9-106">Microsoft anahtar ve akışını Kaydet</span><span class="sxs-lookup"><span data-stu-id="149b9-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="149b9-107">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="149b9-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="149b9-108">Microsoft anahtarını kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="149b9-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="149b9-109">Ürün deposunu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="149b9-109">Register the product repository.</span></span>
- <span data-ttu-id="149b9-110">Gerekli bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="149b9-110">Install required dependencies.</span></span>

<span data-ttu-id="149b9-111">Bu, makine başına yalnızca bir kez yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="149b9-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="149b9-112">Bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="149b9-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="149b9-113">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="149b9-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="149b9-114">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="149b9-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="149b9-115">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="149b9-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="149b9-116">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="149b9-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="149b9-117">Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme.</span><span class="sxs-lookup"><span data-stu-id="149b9-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="149b9-118">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="149b9-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="149b9-119">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="149b9-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="149b9-120">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="149b9-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="149b9-121">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="149b9-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="149b9-122">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="149b9-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="149b9-123">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="149b9-123">Troubleshoot the package manager</span></span>

<span data-ttu-id="149b9-124">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="149b9-124">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="149b9-125">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="149b9-125">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
