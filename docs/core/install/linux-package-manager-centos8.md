---
title: Linux CentOS 8 Paket Yöneticisi 'ne .NET Core 'u yükler-.NET Core
description: CentOS 8 ' de .NET Core SDK ve çalışma zamanı yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 05/01/2020
ms.openlocfilehash: b4cf5975e18aa8dfa8649c0d038caf38d648ad86
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728521"
---
# <a name="centos-8-package-manager---install-net-core"></a><span data-ttu-id="33a35-103">CentOS 8 Paket Yöneticisi-.NET Core 'ı yükler</span><span class="sxs-lookup"><span data-stu-id="33a35-103">CentOS 8 Package Manager - Install .NET Core</span></span>

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

<span data-ttu-id="33a35-104">Bu makalede, CentOS 8 ' de .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.</span><span class="sxs-lookup"><span data-stu-id="33a35-104">This article describes how to use a package manager to install .NET Core on CentOS 8.</span></span>

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="install-the-net-core-sdk"></a><span data-ttu-id="33a35-105">.NET Core SDK’sını yükleme</span><span class="sxs-lookup"><span data-stu-id="33a35-105">Install the .NET Core SDK</span></span>

<span data-ttu-id="33a35-106">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33a35-106">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a><span data-ttu-id="33a35-107">ASP.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="33a35-107">Install the ASP.NET Core Runtime</span></span>

<span data-ttu-id="33a35-108">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33a35-108">In your terminal, run the following command.</span></span>

```bash
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a><span data-ttu-id="33a35-109">.NET Core çalışma zamanını yükler</span><span class="sxs-lookup"><span data-stu-id="33a35-109">Install the .NET Core Runtime</span></span>

<span data-ttu-id="33a35-110">Terminalinizde aşağıdaki komutu çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33a35-110">In your terminal, run the following command.</span></span>

```bash
sudo dnf install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a><span data-ttu-id="33a35-111">Diğer sürümleri nasıl yüklenir</span><span class="sxs-lookup"><span data-stu-id="33a35-111">How to install other versions</span></span>

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]
