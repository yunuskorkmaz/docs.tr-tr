---
title: Linux RHEL 8,1 Paket Yöneticisi 'ne .NET Core 'u yükler-.NET Core
description: RHEL 8,1 üzerinde .NET Core SDK ve çalışma zamanı yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 20fb3e9e517858b9cc5d6e9c1bd97bf949558843
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800736"
---
# <a name="rhel-81-package-manager---install-net-core"></a>RHEL 8,1 Paket Yöneticisi-.NET Core 'u yükler

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Bu makalede, RHEL 8,1 üzerinde .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.

> [!NOTE]
> RHEL 8,0, .NET Core 3,0 içermez. RHEL 8,1 ' ye güncelleştirmek için komut `yum upgrade` kullanın.

## <a name="register-your-red-hat-subscription"></a>Red Hat aboneliğinizi kaydetme

RHEL 'de Red Hat 'ten .NET Core yüklemek için, önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir. Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.NET Core Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net_core/)bakın.

## <a name="install-the-net-core-sdk"></a>.NET Core SDK 'i yükler

Abonelik Yöneticisi ile kaydolduktan sonra, .NET Core SDK yüklenmeye ve etkinleştirmeye hazırsınız demektir. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
dnf install dotnet-sdk-3.0
scl enable dotnet-sdk-3.0 bash
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core çalışma zamanını yükler

Abonelik Yöneticisi ile kaydolduktan sonra, ASP.NET Core çalışma zamanını yüklemek ve etkinleştirmek için hazırsınız demektir. Terminalinizde aşağıdaki komutları çalıştırın.

<!-- TODO: is this the correct value? Taken from the webpage but it doesn't have aspnet in the name -->
```bash
dnf install aspnetcore-runtime-3.0
scl enable aspnetcore-runtime-3.0 bash
```

## <a name="install-the-net-core-runtime"></a>.NET Core çalışma zamanını yükler

Abonelik Yöneticisi ile kaydolduktan sonra .NET Core çalışma zamanını yüklemeye ve etkinleştirmeye hazırsınız demektir. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo dnf install dotnet-runtime-3.0
scl enable dotnet-runtime-3.0 bash
```

## <a name="see-also"></a>Ayrıca bkz.

- [Red Hat Enterprise Linux 8 üzerinde .NET Core 3,0 kullanma](https://access.redhat.com/documentation/en-us/net_core/3.0/html/getting_started_guide_for_rhel_8/gs_install_dotnet)
