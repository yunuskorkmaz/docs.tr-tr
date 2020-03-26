---
title: Linux RHEL 7 paket yöneticisine .NET Core'u yükleyin - .NET Core
description: .NET Core SDK'yı ve çalışma süresini RHEL 7'ye yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: d1f1372b32c7b2471a96492d48aab5533dadb64a
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134210"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="d8c01-103">RHEL 7 Paket Yöneticisi - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="d8c01-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="d8c01-104">Bu makalede, RHEL 7'ye .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d8c01-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="d8c01-105">Red Hat aboneliğinizi kaydedin</span><span class="sxs-lookup"><span data-stu-id="d8c01-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="d8c01-106">RHEL'e Red Hat'ten .NET Core'u yüklemek için öncelikle Red Hat Subscription Manager'ı kullanarak kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="d8c01-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="d8c01-107">Bu durum sisteminizde yapılmadıysa veya emin değilseniz [,.NET Core için Red Hat Ürün Belgeleri'ne](https://access.redhat.com/documentation/net_core/)bakın.</span><span class="sxs-lookup"><span data-stu-id="d8c01-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="d8c01-108">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="d8c01-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="d8c01-109">Abonelik Yöneticisi'ne kaydolduktan sonra .NET Core SDK'yı yüklemeye ve etkinleştirmeye hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="d8c01-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="d8c01-110">Terminalinizde, RHEL 7 dotnet kanalını etkinleştirmek ve yüklemek için aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d8c01-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="d8c01-111">ASP.NET Core Runtime'ı yükleyin</span><span class="sxs-lookup"><span data-stu-id="d8c01-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="d8c01-112">Abonelik Yöneticisi'ne kaydolduktan sonra, Core Runtime'ASP.NET yüklemeye ve etkinleştirmeye hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="d8c01-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="d8c01-113">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d8c01-113">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="d8c01-114">.NET Çekirdek Çalışma Süresini Yükleyin</span><span class="sxs-lookup"><span data-stu-id="d8c01-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="d8c01-115">Abonelik Yöneticisi'ne kaydolduktan sonra .NET Core Runtime'ı yüklemeye ve etkinleştirmeye hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="d8c01-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="d8c01-116">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="d8c01-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a><span data-ttu-id="d8c01-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8c01-117">See also</span></span>

- [<span data-ttu-id="d8c01-118">Red Hat Enterprise Linux 7'de .NET Core 3.1 kullanma</span><span class="sxs-lookup"><span data-stu-id="d8c01-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
