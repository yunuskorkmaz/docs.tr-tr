---
title: Linux RHEL 7 Paket Yöneticisi 'ne .NET Core 'u yükler-.NET Core
description: .NET Core SDK ve çalışma zamanını RHEL 7 ' ye yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.openlocfilehash: 4893271ebd32036d8ec09e6b718c12b11acb8d59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450984"
---
# <a name="rhel-7-package-manager---install-net-core"></a><span data-ttu-id="118f2-103">RHEL 7 Paket Yöneticisi-.NET Core 'u yükler</span><span class="sxs-lookup"><span data-stu-id="118f2-103">RHEL 7 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="118f2-104">Bu makalede, RHEL 7 üzerinde .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="118f2-104">This article describes how to use a package manager to install .NET Core on RHEL 7.</span></span>

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="118f2-105">Red Hat aboneliğinizi kaydetme</span><span class="sxs-lookup"><span data-stu-id="118f2-105">Register your Red Hat subscription</span></span>

<span data-ttu-id="118f2-106">RHEL 'de Red Hat 'ten .NET Core yüklemek için, önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="118f2-106">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="118f2-107">Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.NET Core Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net_core/)bakın.</span><span class="sxs-lookup"><span data-stu-id="118f2-107">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="118f2-108">.NET Core SDK 'i yükler</span><span class="sxs-lookup"><span data-stu-id="118f2-108">Install the .NET Core SDK</span></span>

<span data-ttu-id="118f2-109">Abonelik Yöneticisi ile kaydolduktan sonra, .NET Core SDK yüklenmeye ve etkinleştirmeye hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="118f2-109">After registering with the Subscription Manager, you're ready to install and enable the .NET Core SDK.</span></span> <span data-ttu-id="118f2-110">Terminalinizde, RHEL 7 DotNet kanalını etkinleştirmek ve yüklemek için aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="118f2-110">In your terminal, run the following commands to enable the RHEL 7 dotnet channel and install .</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="118f2-111">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="118f2-111">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="118f2-112">Abonelik Yöneticisi ile kaydolduktan sonra, ASP.NET Core çalışma zamanını yüklemek ve etkinleştirmek için hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="118f2-112">After registering with the Subscription Manager, you're ready to install and enable the ASP.NET Core Runtime.</span></span> <span data-ttu-id="118f2-113">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="118f2-113">In your terminal, run the following commands.</span></span>

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="118f2-114">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="118f2-114">Install the .NET Core Runtime</span></span>

<span data-ttu-id="118f2-115">Abonelik Yöneticisi ile kaydolduktan sonra .NET Core çalışma zamanını yüklemeye ve etkinleştirmeye hazırsınız demektir.</span><span class="sxs-lookup"><span data-stu-id="118f2-115">After registering with the Subscription Manager, you're ready to install and enable the .NET Core Runtime.</span></span> <span data-ttu-id="118f2-116">Terminalinizde aşağıdaki komutları çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="118f2-116">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet30-dotnet-runtime-3.0 -y
scl enable rh-dotnet30 bash
```
