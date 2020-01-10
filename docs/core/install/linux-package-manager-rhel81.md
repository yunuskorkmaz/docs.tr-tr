---
title: Linux RHEL 8,1 Paket Yöneticisi 'ne .NET Core 'u yükler-.NET Core
description: RHEL 8,1 üzerinde .NET Core SDK ve çalışma zamanı yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 8781d6bd14daf975fcc602fd2924a333750d4256
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75714382"
---
# <a name="rhel-81-package-manager---install-net-core"></a><span data-ttu-id="96c4b-103">RHEL 8,1 Paket Yöneticisi-.NET Core 'u yükler</span><span class="sxs-lookup"><span data-stu-id="96c4b-103">RHEL 8.1 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="96c4b-104">Bu makalede, RHEL 8,1 üzerinde .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="96c4b-104">This article describes how to use a package manager to install .NET Core on RHEL 8.1.</span></span> <span data-ttu-id="96c4b-105">.NET Core 3,1, henüz RHEL 8,1 için kullanılabilir değil.</span><span class="sxs-lookup"><span data-stu-id="96c4b-105">.NET Core 3.1 is not yet available for RHEL 8.1.</span></span>

> [!NOTE]
> <span data-ttu-id="96c4b-106">RHEL 8,0, .NET Core 3,0 içermez.</span><span class="sxs-lookup"><span data-stu-id="96c4b-106">RHEL 8.0 does not include .NET Core 3.0.</span></span> <span data-ttu-id="96c4b-107">RHEL 8,1 ' ye güncelleştirmek için komut `yum upgrade` kullanın.</span><span class="sxs-lookup"><span data-stu-id="96c4b-107">Use the command `yum upgrade` to update to RHEL 8.1.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="96c4b-108">Red Hat aboneliğinizi kaydetme</span><span class="sxs-lookup"><span data-stu-id="96c4b-108">Register your Red Hat subscription</span></span>

<span data-ttu-id="96c4b-109">RHEL 'de Red Hat 'ten .NET Core yüklemek için, önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="96c4b-109">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="96c4b-110">Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.NET Core Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net_core/)bakın.</span><span class="sxs-lookup"><span data-stu-id="96c4b-110">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="96c4b-111">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="96c4b-111">Install the .NET Core SDK</span></span>

<span data-ttu-id="96c4b-112">Abonelik Yöneticisi ile kaydolduktan sonra, .NET Core SDK yüklenmeye ve etkinleştirmeye hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="96c4b-112">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="96c4b-113">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96c4b-113">In your terminal, run the following commands.</span></span>

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="96c4b-114">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="96c4b-114">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="96c4b-115">Abonelik Yöneticisi ile kaydolduktan sonra, ASP.NET Core çalışma zamanını yüklemek ve etkinleştirmek için hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="96c4b-115">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="96c4b-116">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96c4b-116">In your terminal, run the following commands.</span></span>

```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="96c4b-117">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="96c4b-117">Install the .NET Core Runtime</span></span>

<span data-ttu-id="96c4b-118">Abonelik Yöneticisi ile kaydolduktan sonra .NET Core çalışma zamanını yüklemeye ve etkinleştirmeye hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="96c4b-118">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="96c4b-119">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="96c4b-119">In your terminal, run the following commands.</span></span>

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a><span data-ttu-id="96c4b-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="96c4b-120">See also</span></span>

- [<span data-ttu-id="96c4b-121">Red Hat Enterprise Linux 8 üzerinde .NET Core 3,0 kullanma</span><span class="sxs-lookup"><span data-stu-id="96c4b-121">Using .NET Core 3.0 on Red Hat Enterprise Linux 8</span></span>](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
