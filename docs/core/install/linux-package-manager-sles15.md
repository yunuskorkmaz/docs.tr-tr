---
title: SLES 15-Package Manager-.NET Core 'a .NET Core 'u yükler
description: .NET Core SDK ve çalışma zamanını SLES 15 ' e yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: be5a21db8c3942bfe8827dfbce41bcf88aec342a
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595667"
---
# <a name="sles-15-package-manager---install-net-core"></a><span data-ttu-id="a83f4-103">SLES 15 Paket Yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="a83f4-103">SLES 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="a83f4-104">Bu makalede, SLES 15 üzerinde .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="a83f4-104">This article describes how to use a package manager to install .NET Core on SLES 15.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a><span data-ttu-id="a83f4-105">Microsoft Repository anahtarı ve akışı Ekle</span><span class="sxs-lookup"><span data-stu-id="a83f4-105">Add Microsoft repository key and feed</span></span>

<span data-ttu-id="a83f4-106">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="a83f4-106">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="a83f4-107">Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a83f4-107">Add the Microsoft package signing key to the list of trusted keys.</span></span>
- <span data-ttu-id="a83f4-108">Depoyu paket yöneticisine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a83f4-108">Add the repository to the package manager.</span></span>
- <span data-ttu-id="a83f4-109">Gerekli bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="a83f4-109">Install required dependencies.</span></span>

<span data-ttu-id="a83f4-110">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="a83f4-110">This only needs to be done once per machine.</span></span>

<span data-ttu-id="a83f4-111">Bir Terminal açın ve aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a83f4-111">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/15/packages-microsoft-prod.rpm
```

<span data-ttu-id="a83f4-112">Şu anda, SLES 15 Microsoft Repository kurulum paketi *Microsoft-prod. repo* dosyasını yanlış dizine yüklüyor ve .NET Core paketlerini bulmadan zypper 'yi engellemektedir.</span><span class="sxs-lookup"><span data-stu-id="a83f4-112">Currently, the SLES 15 Microsoft repository setup package installs the *microsoft-prod.repo* file to the wrong directory, preventing zypper from finding the .NET Core packages.</span></span> <span data-ttu-id="a83f4-113">Bu sorunu gidermek için doğru dizinde bir oluşturmaksızın oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a83f4-113">To fix this problem, create a symlink in the correct directory.</span></span>

```bash
sudo ln -s /etc/yum.repos.d/microsoft-prod.repo /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="a83f4-114">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="a83f4-114">Install the .NET Core SDK</span></span>

<span data-ttu-id="a83f4-115">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="a83f4-115">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="a83f4-116">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a83f4-116">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="a83f4-117">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="a83f4-117">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="a83f4-118">Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme.</span><span class="sxs-lookup"><span data-stu-id="a83f4-118">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="a83f4-119">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a83f4-119">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="a83f4-120">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="a83f4-120">Install the .NET Core runtime</span></span>

<span data-ttu-id="a83f4-121">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="a83f4-121">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="a83f4-122">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a83f4-122">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="a83f4-123">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="a83f4-123">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a><span data-ttu-id="a83f4-124">Paket yöneticisinin sorunlarını giderme</span><span class="sxs-lookup"><span data-stu-id="a83f4-124">Troubleshoot the package manager</span></span>

<span data-ttu-id="a83f4-125">Bu bölüm, .NET Core 'u yüklemek için Paket Yöneticisi 'ni kullanırken karşılaşabileceğiniz yaygın hatalarla ilgili bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a83f4-125">This section provides information on common errors you may get while using the package manager to install .NET Core.</span></span>

### <a name="failed-to-fetch"></a><span data-ttu-id="a83f4-126">Getirilemedi</span><span class="sxs-lookup"><span data-stu-id="a83f4-126">Failed to fetch</span></span>

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-rpm.md)]
