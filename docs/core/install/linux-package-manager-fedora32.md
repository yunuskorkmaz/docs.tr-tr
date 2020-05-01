---
title: .NET Core 'u Fedora 32-Package Manager-.NET Core 'a yükler
description: .NET Core SDK ve çalışma zamanını Fedora 32 ' ye yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 04/28/2020
ms.openlocfilehash: e5a69bf00e7e2969143e044aea4c9938fd5a610d
ms.sourcegitcommit: e09dbff13f0b21b569a101f3b3c5efa174aec204
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82624968"
---
# <a name="fedora-32-package-manager---install-net-core"></a><span data-ttu-id="52832-103">Fedora 32 Paket Yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="52832-103">Fedora 32 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

<span data-ttu-id="52832-104">Bu makalede, Fedora 32 ' de .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="52832-104">This article describes how to use a package manager to install .NET Core on Fedora 32.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

<span data-ttu-id="52832-105">Fedora 32 ile başlayarak, .NET Core 3,1, Fedora 'daki varsayılan paket depolarında sunulmaktadır.</span><span class="sxs-lookup"><span data-stu-id="52832-105">Starting with Fedora 32, .NET Core 3.1 is available in the default package repositories in Fedora.</span></span>

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="52832-106">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="52832-106">Install the .NET Core SDK</span></span>

<span data-ttu-id="52832-107">.NET Core SDK 'i yükler.</span><span class="sxs-lookup"><span data-stu-id="52832-107">Install the .NET Core SDK.</span></span> <span data-ttu-id="52832-108">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="52832-108">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="52832-109">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="52832-109">Install the ASP.NET Core runtime</span></span>

<span data-ttu-id="52832-110">ASP.NET çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="52832-110">Install the ASP.NET runtime.</span></span> <span data-ttu-id="52832-111">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="52832-111">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="52832-112">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="52832-112">Install the .NET Core runtime</span></span>

<span data-ttu-id="52832-113">.NET Core çalışma zamanını yükler.</span><span class="sxs-lookup"><span data-stu-id="52832-113">Install the .NET Core runtime.</span></span> <span data-ttu-id="52832-114">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="52832-114">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="52832-115">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="52832-115">How to install other versions</span></span>

<span data-ttu-id="52832-116">.NET Core 'un diğer sürümlerini yüklemek için [.NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) veya [.NET Core çalışma zamanını](runtime.md?pivots=os-linux#download-and-manually-install)el ile yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="52832-116">To install other versions of .NET Core, manually install [the .NET Core SDK](sdk.md?pivots=os-linux#download-and-manually-install) or [the .NET Core Runtime](runtime.md?pivots=os-linux#download-and-manually-install).</span></span>
