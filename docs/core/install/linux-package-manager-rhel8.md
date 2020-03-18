---
title: Linux RHEL 8 paket yöneticisine .NET Core yükle - .NET Core
description: .NET Core SDK'yı ve çalışma süresini RHEL 8'e yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 054494a9b77e1c7803e42c947e067d3eb290f73c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78849812"
---
# <a name="rhel-8-package-manager---install-net-core"></a><span data-ttu-id="0f8ce-103">RHEL 8 Paket Yöneticisi - Install .NET Core</span><span class="sxs-lookup"><span data-stu-id="0f8ce-103">RHEL 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="0f8ce-104">Bu makalede, RHEL 8'e .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0f8ce-104">This article describes how to use a package manager to install .NET Core on RHEL 8.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="0f8ce-105">Red Hat aboneliğinizi kaydedin</span><span class="sxs-lookup"><span data-stu-id="0f8ce-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="0f8ce-106">RHEL'e Red Hat'ten .NET Core'u yüklemek için öncelikle Red Hat Subscription Manager'ı kullanarak kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0f8ce-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="0f8ce-107">Bu durum sisteminizde yapılmadıysa veya emin değilseniz [,.NET Core için Red Hat Ürün Belgeleri'ne](https://access.redhat.com/documentation/net_core/)bakın.</span><span class="sxs-lookup"><span data-stu-id="0f8ce-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="0f8ce-108">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="0f8ce-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="0f8ce-109">Abonelik Yöneticisi'ne kaydolduktan sonra .NET Core SDK'yı yüklemeye ve etkinleştirmeye hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="0f8ce-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="0f8ce-110">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0f8ce-110">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="0f8ce-111">ASP.NET Core Runtime'ı yükleyin</span><span class="sxs-lookup"><span data-stu-id="0f8ce-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="0f8ce-112">Abonelik Yöneticisi'ne kaydolduktan sonra, Core Runtime'ASP.NET yüklemeye ve etkinleştirmeye hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="0f8ce-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="0f8ce-113">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0f8ce-113">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="0f8ce-114">.NET Çekirdek Çalışma Süresini Yükleyin</span><span class="sxs-lookup"><span data-stu-id="0f8ce-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="0f8ce-115">Abonelik Yöneticisi'ne kaydolduktan sonra .NET Core Runtime'ı yüklemeye ve etkinleştirmeye hazırsınız.</span><span class="sxs-lookup"><span data-stu-id="0f8ce-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="0f8ce-116">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="0f8ce-116">In your terminal, run the following commands.</span></span>

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a><span data-ttu-id="0f8ce-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0f8ce-117">See also</span></span>

- [<span data-ttu-id="0f8ce-118">Red Hat Enterprise Linux 8'de .NET Core 3.1 kullanma</span><span class="sxs-lookup"><span data-stu-id="0f8ce-118">Using .NET Core 3.1 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
