---
title: Linux RHEL 7 Paket Yöneticisi 'ne .NET Core 'u yükler-.NET Core
description: .NET Core SDK ve çalışma zamanını RHEL 7 ' ye yüklemek için bir paket Yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.openlocfilehash: 4f85ed3da8a434fcd5b6ee88491daf623c3c8b31
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980190"
---
# <a name="rhel-7-package-manager---install-net-core"></a>RHEL 7 Paket Yöneticisi-.NET Core 'u yükler

[!INCLUDE [package-manager-switcher](includes/package-manager-switcher.md)]

Bu makalede, RHEL 7 üzerinde .NET Core yüklemek için bir paket yöneticisi 'nin nasıl kullanılacağı açıklanır.

## <a name="register-your-red-hat-subscription"></a>Red Hat aboneliğinizi kaydetme

RHEL 'de Red Hat 'ten .NET Core yüklemek için, önce Red Hat abonelik Yöneticisi 'Ni kullanarak kaydolmanız gerekir. Bu, sisteminizde yapmadıysanız veya emin değilseniz, [.NET Core Için Red Hat ürün belgelerine](https://access.redhat.com/documentation/net_core/)bakın.

## <a name="install-the-net-core-sdk"></a>.NET Core SDK 'i yükler

Abonelik Yöneticisi ile kaydolduktan sonra, .NET Core SDK yüklenmeye ve etkinleştirmeye hazırsınız demektir. Terminalinizde, RHEL 7 DotNet kanalını etkinleştirmek ve yüklemek için aşağıdaki komutları çalıştırın.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core çalışma zamanını yükler

Abonelik Yöneticisi ile kaydolduktan sonra, ASP.NET Core çalışma zamanını yüklemek ve etkinleştirmek için hazırsınız demektir. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="install-the-net-core-runtime"></a>.NET Core çalışma zamanını yükler

Abonelik Yöneticisi ile kaydolduktan sonra .NET Core çalışma zamanını yüklemeye ve etkinleştirmeye hazırsınız demektir. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-dotnet-runtime-3.1 -y
scl enable rh-dotnet31 bash
```

## <a name="see-also"></a>Ayrıca bkz.

- [Red Hat Enterprise Linux 7 ' de .NET Core 3,1 kullanma](https://access.redhat.com/documentation/en-us/net_core/3.1/html/getting_started_guide/gs_install_dotnet)
