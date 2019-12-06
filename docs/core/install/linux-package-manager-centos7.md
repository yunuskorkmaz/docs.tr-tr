---
title: CentOS 7-Package Manager-.NET Core 'a .NET Core 'u yükler
description: .NET Core SDK ve çalışma zamanını CentOS 7 ' de yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.openlocfilehash: cb65811d5cae5c747c2660b4b10486f3162b9f33
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836943"
---
# <a name="centos-7-package-manager---install-net-core"></a><span data-ttu-id="ea71c-103">CentOS 7 Paket Yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="ea71c-103">CentOS 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="ea71c-104">Bu makalede, CentOS 7 ' ye .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="ea71c-104">This article describes how to use a package manager to install .NET Core on CentOS 7.</span></span> <span data-ttu-id="ea71c-105">Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="ea71c-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="ea71c-106">Microsoft anahtarını ve akışını kaydetme</span><span class="sxs-lookup"><span data-stu-id="ea71c-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="ea71c-107">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="ea71c-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="ea71c-108">Microsoft anahtarını kaydetme</span><span class="sxs-lookup"><span data-stu-id="ea71c-108">Register the Microsoft key</span></span>
- <span data-ttu-id="ea71c-109">Ürün deposunu kaydetme</span><span class="sxs-lookup"><span data-stu-id="ea71c-109">register the product repository</span></span>
- <span data-ttu-id="ea71c-110">Gerekli bağımlılıkları yükler</span><span class="sxs-lookup"><span data-stu-id="ea71c-110">Install required dependencies</span></span>

<span data-ttu-id="ea71c-111">Bu işlemin makine başına bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="ea71c-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="ea71c-112">Bir Terminal açın ve aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ea71c-112">Open a terminal and run the following command.</span></span>

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="ea71c-113">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="ea71c-113">Install the .NET Core SDK</span></span>

<span data-ttu-id="ea71c-114">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="ea71c-114">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="ea71c-115">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ea71c-115">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="ea71c-116">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="ea71c-116">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="ea71c-117">Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme.</span><span class="sxs-lookup"><span data-stu-id="ea71c-117">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="ea71c-118">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ea71c-118">In your terminal, run the following command.</span></span>

```bash
sudo yum install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="ea71c-119">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="ea71c-119">Install the .NET Core runtime</span></span>

<span data-ttu-id="ea71c-120">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="ea71c-120">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="ea71c-121">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="ea71c-121">In your terminal, run the following command.</span></span>

```bash
sudo yum install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="ea71c-122">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="ea71c-122">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
