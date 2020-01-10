---
title: OpenSUSE 15-Package Manager-.NET Core 'a .NET Core 'u yükler
description: OpenSUSE 15 üzerinde .NET Core SDK ve çalışma zamanı yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/26/2019
ms.openlocfilehash: cba07bafc32cc71a1cdaec08902284e105af4776
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740675"
---
# <a name="opensuse-15-package-manager---install-net-core"></a><span data-ttu-id="164d6-103">openSUSE 15 Paket Yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="164d6-103">openSUSE 15 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="164d6-104">Bu makalede, openSUSE 15 ' te .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="164d6-104">This article describes how to use a package manager to install .NET Core on openSUSE 15.</span></span> <span data-ttu-id="164d6-105">Çalışma zamanını yüklüyorsanız, hem .NET Core 'u hem de ASP.NET Core çalışma zamanlarını içerdiğinden [ASP.NET Core çalışma zamanını](#install-the-aspnet-core-runtime)yüklemenizi öneririz.</span><span class="sxs-lookup"><span data-stu-id="164d6-105">If you're installing the runtime, we suggest you install the [ASP.NET Core runtime](#install-the-aspnet-core-runtime), as it includes both .NET Core and ASP.NET Core runtimes.</span></span>

## <a name="register-microsoft-key-and-feed"></a><span data-ttu-id="164d6-106">Microsoft anahtarını ve akışını kaydetme</span><span class="sxs-lookup"><span data-stu-id="164d6-106">Register Microsoft key and feed</span></span>

<span data-ttu-id="164d6-107">.NET yüklemeden önce şunları yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="164d6-107">Before installing .NET, you'll need to:</span></span>

- <span data-ttu-id="164d6-108">Microsoft anahtarını kaydettirin.</span><span class="sxs-lookup"><span data-stu-id="164d6-108">Register the Microsoft key.</span></span>
- <span data-ttu-id="164d6-109">Ürün deposunu kaydedin.</span><span class="sxs-lookup"><span data-stu-id="164d6-109">Register the product repository.</span></span>
- <span data-ttu-id="164d6-110">Gerekli bağımlılıkları yükler.</span><span class="sxs-lookup"><span data-stu-id="164d6-110">Install required dependencies.</span></span>

<span data-ttu-id="164d6-111">Bu işlemin makine başına tek bir kez yapılması yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="164d6-111">This only needs to be done once per machine.</span></span>

<span data-ttu-id="164d6-112">Bir Terminal açın ve aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="164d6-112">Open a terminal and run the following commands.</span></span>

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget -q https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
```

## <a name="dependency-error-with-net-core-31"></a><span data-ttu-id="164d6-113">.NET Core 3,1 ile bağımlılık hatası</span><span class="sxs-lookup"><span data-stu-id="164d6-113">Dependency error with .NET Core 3.1</span></span>

<span data-ttu-id="164d6-114">OpenSUSE için .NET Core 3,1 paket akışında **krb5** bağımlılığıyla ilgili bir sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="164d6-114">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="164d6-115">.NET Core 3,1 veya ASP.NET Core 3,1 ' ü yüklemeden önce doğru bağımlılıkları yüklemek için aşağıdaki komutu kullanın.</span><span class="sxs-lookup"><span data-stu-id="164d6-115">Use the following command to install the correct dependencies prior to installing .NET Core 3.1 or ASP.NET Core 3.1.</span></span>

```bash
sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
```

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="164d6-116">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="164d6-116">Install the .NET Core SDK</span></span>

<span data-ttu-id="164d6-117">Yükleme için kullanılabilen ürünleri güncelleştirin, ardından .NET Core SDK yükleme.</span><span class="sxs-lookup"><span data-stu-id="164d6-117">Update the products available for installation, then install the .NET Core SDK.</span></span> <span data-ttu-id="164d6-118">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="164d6-118">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-sdk-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="164d6-119">OpenSUSE için .NET Core 3,1 paket akışında **krb5** bağımlılığıyla ilgili bir sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="164d6-119">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="164d6-120">Doğru bağımlılıkları yüklemek için aşağıdaki komutu kullanın, ardından .NET Core 3,1 SDK 'sını yükler.</span><span class="sxs-lookup"><span data-stu-id="164d6-120">Use the following command to install the correct dependencies, then install the .NET Core 3.1 SDK.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="164d6-121">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="164d6-121">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="164d6-122">Yükleme için kullanılabilen ürünleri güncelleştirin, sonra ASP.NET çalışma zamanını yükleme.</span><span class="sxs-lookup"><span data-stu-id="164d6-122">Update the products available for installation, then install the ASP.NET runtime.</span></span> <span data-ttu-id="164d6-123">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="164d6-123">In your terminal, run the following command.</span></span>

```bash
sudo zypper install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="164d6-124">OpenSUSE için .NET Core 3,1 paket akışında **krb5** bağımlılığıyla ilgili bir sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="164d6-124">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="164d6-125">Doğru bağımlılıkları yüklemek için aşağıdaki komutu kullanın ve ardından ASP.NET Core 3,1 çalışma zamanını yüklemelisiniz.</span><span class="sxs-lookup"><span data-stu-id="164d6-125">Use the following command to install the correct dependencies, then install the ASP.NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="164d6-126">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="164d6-126">Install the .NET Core runtime</span></span>

<span data-ttu-id="164d6-127">Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından .NET Core çalışma zamanı 'nı yükleme.</span><span class="sxs-lookup"><span data-stu-id="164d6-127">Update the products available for installation, then install the .NET Core runtime.</span></span> <span data-ttu-id="164d6-128">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="164d6-128">In your terminal, run the following command.</span></span>

```bash
sudo zypper install dotnet-runtime-3.1
```

> [!IMPORTANT]
> <span data-ttu-id="164d6-129">OpenSUSE için .NET Core 3,1 paket akışında **krb5** bağımlılığıyla ilgili bir sorun vardır.</span><span class="sxs-lookup"><span data-stu-id="164d6-129">The .NET Core 3.1 package feed for openSUSE has a problem with the **krb5** dependency.</span></span> <span data-ttu-id="164d6-130">Doğru bağımlılıkları yüklemek için aşağıdaki komutu kullanın, ardından .NET Core 3,1 çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="164d6-130">Use the following command to install the correct dependencies, then install the .NET Core 3.1 runtime.</span></span>
>
> ```bash
> sudo zypper install https://packages.microsoft.com/opensuse/15/prod/dotnet-runtime-deps-3.1.0-opensuse.42-x64.rpm
> ```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="164d6-131">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="164d6-131">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
