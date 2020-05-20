---
title: Ubuntu 20,04 paket yöneticisi 'ne .NET Core 'u yükler-.NET Core
description: Ubuntu 20,04 ' de .NET Core SDK ve çalışma zamanı yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 05/13/2020
ms.openlocfilehash: 4d7d7ee9117314ef360097fee929f24943c7a7f2
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83619290"
---
# <a name="ubuntu-2004-package-manager---install-net-core"></a><span data-ttu-id="7770f-103">Ubuntu 20,04 paket yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="7770f-103">Ubuntu 20.04 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="7770f-104">Bu makalede, Ubuntu 20,04 ' de .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="7770f-104">This article describes how to use a package manager to install .NET Core on Ubuntu 20.04.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="7770f-105">Microsoft Repository anahtarı ve akışı Ekle</span><span class="sxs-lookup"><span data-stu-id="7770f-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="7770f-106">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="7770f-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="7770f-107">Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7770f-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="7770f-108">Depoyu paket yöneticisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7770f-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="7770f-109">Gerekli bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="7770f-109">Install required dependencies.</span></span>

<span data-ttu-id="7770f-110">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="7770f-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="7770f-111">Bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7770f-111">Open a terminal and run the following commands.</span></span>

```bash
wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="7770f-112">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="7770f-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="7770f-113">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="7770f-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="7770f-114">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7770f-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="7770f-115">**DotNet-SDK-3,1**' i bulamıyor gibi bir hata iletisi alırsanız, bkz. [Paket Yöneticisi sorunlarını giderme](#troubleshoot-the-package-manager) bölümü.</span><span class="sxs-lookup"><span data-stu-id="7770f-115">If you receive an error message similar to **Unable to locate package dotnet-sdk-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="7770f-116">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="7770f-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="7770f-117">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından ASP.NET Core çalışma zamanını yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="7770f-117">Update the products available for installation, then install the ASP.NET Core runtime.</span></span> <span data-ttu-id="7770f-118">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7770f-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="7770f-119">Bir hata iletisi alırsanız, **aspnetcore-Runtime-3,1 paketini bulamazsanız**, bkz. [Package Manager sorunlarını giderme](#troubleshoot-the-package-manager) bölümü.</span><span class="sxs-lookup"><span data-stu-id="7770f-119">If you receive an error message similar to **Unable to locate package aspnetcore-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="7770f-120">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="7770f-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="7770f-121">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="7770f-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="7770f-122">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7770f-122">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="7770f-123">**DotNet-Runtime-3,1 bulunamadı**hatasıyla benzer bir hata iletisi alırsanız, [Paket Yöneticisi sorunlarını giderme](#troubleshoot-the-package-manager) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="7770f-123">If you receive an error message similar to **Unable to locate package dotnet-runtime-3.1**, see the [Troubleshoot the package manager](#troubleshoot-the-package-manager) section.</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="7770f-124">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="7770f-124">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="7770f-125">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="7770f-125">Troubleshoot the package manager</span></span>

<span data-ttu-id="7770f-126">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7770f-126">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="unable-to-locate"></a><span data-ttu-id="7770f-127">Bulunamıyor</span><span class="sxs-lookup"><span data-stu-id="7770f-127">Unable to locate</span></span>

<span data-ttu-id="7770f-128">**{.NET Core Package} paketi bulunamadı**hatasıyla benzer bir hata iletisi alırsanız aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="7770f-128">If you receive an error message similar to **Unable to locate package {the .NET Core package}**, run the following commands.</span></span>

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

<span data-ttu-id="7770f-129">Bu işe yaramazsa, aşağıdaki komutlarla el ile yüklemeyi çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7770f-129">If that doesn't work, you can run a manual install with the following commands.</span></span>

```bash
sudo apt-get install -y gpg
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/20.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a><span data-ttu-id="7770f-130">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="7770f-130">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
