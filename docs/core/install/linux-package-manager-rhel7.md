---
title: Linux RHEL 7 Paket Yöneticisi 'ne .NET Core 'u yükler-.NET Core
description: .NET Core SDK ve çalışma zamanını RHEL 7 ' ye yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: f17a410ccea1ef4dec32de1d80ef6aac889aa6f3
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74836957"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="1c38c-103">RHEL 7 Paket Yöneticisi-.NET Core 'u yükler</span><span class="sxs-lookup"><span data-stu-id="1c38c-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="1c38c-104">Bu makalede, RHEL 7 üzerinde .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="1c38c-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span> <span data-ttu-id="1c38c-105">.NET Core 3,1, RHEL 7 için henüz kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="1c38c-105">.NET Core 3.1 is not yet available for RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="1c38c-106">Red Hat aboneliğinizi kaydetme</span><span class="sxs-lookup"><span data-stu-id="1c38c-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="1c38c-107">RHEL 'de Red Hat 'ten .NET Core yüklemek için, önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="1c38c-107">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="1c38c-108">Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.NET Core Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net_core/)bakın.</span><span class="sxs-lookup"><span data-stu-id="1c38c-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="1c38c-109">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="1c38c-109">Install the .NET Core SDK</span></span>

<span data-ttu-id="1c38c-110">Abonelik Yöneticisi ile kaydolduktan sonra, .NET Core SDK yüklenmeye ve etkinleştirmeye hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="1c38c-110">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="1c38c-111">Terminalinizde, RHEL 7 DotNet kanalını etkinleştirmek ve yüklemek için aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1c38c-111">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="1c38c-112">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="1c38c-112">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="1c38c-113">Abonelik Yöneticisi ile kaydolduktan sonra, ASP.NET Core çalışma zamanını yüklemek ve etkinleştirmek için hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="1c38c-113">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="1c38c-114">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1c38c-114">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-aspnetcore-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="1c38c-115">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="1c38c-115">Install the .NET Core Runtime</span></span>

<span data-ttu-id="1c38c-116">Abonelik Yöneticisi ile kaydolduktan sonra .NET Core çalışma zamanını yüklemeye ve etkinleştirmeye hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="1c38c-116">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="1c38c-117">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="1c38c-117">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="see-also"></a><span data-ttu-id="1c38c-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c38c-118">See also</span></span>

- [<span data-ttu-id="1c38c-119">Red Hat Enterprise Linux 7 ' de .NET Core 3,0 kullanma</span><span class="sxs-lookup"><span data-stu-id="1c38c-119">Using .NET Core 3.0 on Red Hat Enterprise Linux 7</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide/gs_install_dotnet)
