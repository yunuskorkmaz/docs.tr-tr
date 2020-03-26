---
title: Linux RHEL 8 paket yöneticisine .NET Core yükle - .NET Core
description: .NET Core SDK'yı ve çalışma süresini RHEL 8'e yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: b564a386eb67b6e414a832ad3bca10d3d09022bd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134187"
---
# <a name="rhel-8-package-manager---install-net-core"></a>RHEL 8 Paket Yöneticisi - Install .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Bu makalede, RHEL 8'e .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Red Hat aboneliğinizi kaydedin

RHEL'e Red Hat'ten .NET Core'u yüklemek için öncelikle Red Hat Subscription Manager'ı kullanarak kaydolmanız gerekir. Bu durum sisteminizde yapılmadıysa veya emin değilseniz [,.NET Core için Red Hat Ürün Belgeleri'ne](https://access.redhat.com/documentation/net_core/)bakın.

## <a name="install-the-net-core-sdk"></a>.NET Core SDK’sını yükleme

Abonelik Yöneticisi'ne kaydolduktan sonra .NET Core SDK'yı yüklemeye ve etkinleştirmeye hazırsınız. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo dnf update
sudo dnf install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core Runtime'ı yükleyin

Abonelik Yöneticisi'ne kaydolduktan sonra, Core Runtime'ASP.NET yüklemeye ve etkinleştirmeye hazırsınız. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo dnf update
sudo dnf install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>.NET Çekirdek Çalışma Süresini Yükleyin

Abonelik Yöneticisi'ne kaydolduktan sonra .NET Core Runtime'ı yüklemeye ve etkinleştirmeye hazırsınız. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo dnf update
sudo dnf install dotnet-runtime-3.1
```

## <a name="see-also"></a>Ayrıca bkz.

- [Red Hat Enterprise Linux 8'de .NET Core 3.1 kullanma](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/developing_.net_applications_in_rhel_8/index)
