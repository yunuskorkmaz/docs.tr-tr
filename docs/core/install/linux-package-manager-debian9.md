---
title: .NET Core 'u detem 9-Package Manager 'a (.NET Core) yükler
description: Bir paket Yöneticisi kullanarak .NET Core SDK ve çalışma zamanını de, 9 ' da yüklemek için.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: e0aed17a7283a1d032aa8d6da723bc5b115d91a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74451040"
---
# <a name="debian-9-package-manager---install-net-core"></a><span data-ttu-id="59ef9-103">Detem 9 Paket Yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="59ef9-103">Debian 9 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="59ef9-104">Bu makalede, bir paket yöneticisinin .NET Core 'u debir 9 ' a yüklemek için nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="59ef9-104">This article describes how to use a package manager to install .NET Core on Debian 9.</span></span> <span data-ttu-id="59ef9-105">Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="59ef9-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="59ef9-106">Microsoft anahtar ve akışını Kaydet</span><span class="sxs-lookup"><span data-stu-id="59ef9-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="59ef9-107">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="59ef9-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="59ef9-108">Microsoft anahtarını kaydetme</span><span class="sxs-lookup"><span data-stu-id="59ef9-108">Register the Microsoft key</span></span>
- <span data-ttu-id="59ef9-109">Ürün deposunu kaydetme</span><span class="sxs-lookup"><span data-stu-id="59ef9-109">register the product repository</span></span>
- <span data-ttu-id="59ef9-110">Gerekli bağımlılıkları yükler</span><span class="sxs-lookup"><span data-stu-id="59ef9-110">Install required dependencies</span></span>

<span data-ttu-id="59ef9-111">Bu, makine başına yalnızca bir kez yapılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="59ef9-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="59ef9-112">Bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59ef9-112">Open a terminal and run the following commands.</span></span>

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget -q https://packages.microsoft.com/config/debian/9/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="59ef9-113">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="59ef9-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="59ef9-114">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="59ef9-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="59ef9-115">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59ef9-115">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.0
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="59ef9-116">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="59ef9-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="59ef9-117">Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme.</span><span class="sxs-lookup"><span data-stu-id="59ef9-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="59ef9-118">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59ef9-118">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.0
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="59ef9-119">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="59ef9-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="59ef9-120">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="59ef9-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="59ef9-121">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="59ef9-121">In your terminal, run the following commands.</span></span>

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.0
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="59ef9-122">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="59ef9-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
