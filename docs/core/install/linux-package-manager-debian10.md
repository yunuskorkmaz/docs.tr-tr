---
title: .NET Core 'u detem 10-Package Manager 'a (.NET Core) yükler
description: .NET Core SDK ve çalışma zamanını de, 10 ' da yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 038f5579f99f700ce47dc67be2fd344f01cf800c
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595663"
---
# <a name="debian-10-package-manager---install-net-core"></a><span data-ttu-id="abb83-103">Detem 10 Package Manager-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="abb83-103">Debian 10 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="abb83-104">Bu makalede, bir paket yöneticisinin .NET Core 'u de, 10 ' da yüklemek için nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="abb83-104">This article describes how to use a package manager to install .NET Core on Debian 10.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="abb83-105">Microsoft Repository anahtarı ve akışı Ekle</span><span class="sxs-lookup"><span data-stu-id="abb83-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="abb83-106">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="abb83-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="abb83-107">Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="abb83-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="abb83-108">Depoyu paket yöneticisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="abb83-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="abb83-109">Gerekli bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="abb83-109">Install required dependencies.</span></span>

<span data-ttu-id="abb83-110">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="abb83-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="abb83-111">Bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="abb83-111">Open a terminal and run the following commands.</span></span>

```bash
wget -O - https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/debian/10/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="abb83-112">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="abb83-112">Install the .NET Core SDK</span></span>

<span data-ttu-id="abb83-113">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="abb83-113">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="abb83-114">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="abb83-114">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="abb83-115">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="abb83-115">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="abb83-116">Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme.</span><span class="sxs-lookup"><span data-stu-id="abb83-116">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="abb83-117">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="abb83-117">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="abb83-118">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="abb83-118">Install the .NET Core runtime</span></span>

<span data-ttu-id="abb83-119">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="abb83-119">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="abb83-120">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="abb83-120">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="abb83-121">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="abb83-121">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="abb83-122">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="abb83-122">Troubleshoot the package manager</span></span>

<span data-ttu-id="abb83-123">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="abb83-123">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="abb83-124">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="abb83-124">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
