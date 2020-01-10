---
title: SLES 12-Package Manager-.NET Core 'a .NET Core 'u yükler
description: .NET Core SDK ve çalışma zamanını SLES 12 ' ye yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: a40180881ec0962d89f03c2c9d7aad9bbb052d2a
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740659"
---
# <a name="sles-12-package-manager---install-net-core"></a><span data-ttu-id="43316-103">SLES 12 Paket Yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="43316-103">SLES 12 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="43316-104">Bu makalede, SLES 12 ' ye .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="43316-104">This article describes how to use a package manager to install .NET Core on SLES 12.</span></span> <span data-ttu-id="43316-105">Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="43316-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="43316-106">Microsoft anahtarını ve akışını kaydetme</span><span class="sxs-lookup"><span data-stu-id="43316-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="43316-107">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="43316-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="43316-108">Microsoft anahtarını kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="43316-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="43316-109">Ürün deposunu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="43316-109">Register the product repository.</span></span>
- <span data-ttu-id="43316-110">Gerekli bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="43316-110">Install required dependencies.</span></span>

<span data-ttu-id="43316-111">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="43316-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="43316-112">Bir Terminal açın ve aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="43316-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="43316-113">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="43316-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="43316-114">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="43316-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="43316-115">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="43316-115">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="43316-116">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="43316-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="43316-117">Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme.</span><span class="sxs-lookup"><span data-stu-id="43316-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="43316-118">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="43316-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="43316-119">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="43316-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="43316-120">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="43316-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="43316-121">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="43316-121">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="43316-122">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="43316-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
