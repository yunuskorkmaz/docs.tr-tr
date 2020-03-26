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
# <a name="rhel-7-package-manager---install-net-core"></a>RHEL 7 Paket Yöneticisi - Install .NET Core

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Bu makalede, RHEL 7'ye .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a>Red Hat aboneliğinizi kaydedin

RHEL'e Red Hat'ten .NET Core'u yüklemek için öncelikle Red Hat Subscription Manager'ı kullanarak kaydolmanız gerekir. Bu durum sisteminizde yapılmadıysa veya emin değilseniz [,.NET Core için Red Hat Ürün Belgeleri'ne](https://access.redhat.com/documentation/net_core/)bakın.

## <a name="install-the-net-core-sdk"></a>.NET Core SDK’sını yükleme

Abonelik Yöneticisi'ne kaydolduktan sonra .NET Core SDK'yı yüklemeye ve etkinleştirmeye hazırsınız. Terminalinizde, RHEL 7 dotnet kanalını etkinleştirmek ve yüklemek için aşağıdaki komutları çalıştırın.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core Runtime'ı yükleyin

Abonelik Yöneticisi'ne kaydolduktan sonra, Core Runtime'ASP.NET yüklemeye ve etkinleştirmeye hazırsınız. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a>.NET Çekirdek Çalışma Süresini Yükleyin

Abonelik Yöneticisi'ne kaydolduktan sonra .NET Core Runtime'ı yüklemeye ve etkinleştirmeye hazırsınız. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a>Ayrıca bkz.

- [Red Hat Enterprise Linux 7'de .NET Core 3.1 kullanma](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
