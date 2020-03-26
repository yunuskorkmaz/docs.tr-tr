---
title: SLES 12'ye .NET Core yükle - paket yöneticisi - .NET Core
description: .NET Core SDK'yı ve çalışma süresini SLES 12'ye yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 8358107c682274fc2b75bf72689eaa4b168a86c5
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134212"
---
# <a name="sles-12-package-manager---install-net-core"></a>SLES 12 Paket Yöneticisi - Install .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Bu makalede, SLES 12'ye .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="register-microsoft-key-and-feed"></a>Microsoft anahtarını ve akışını kaydetme

.NET'i yüklemeden önce şunları yapmanız gerekir:

- Microsoft anahtarını kaydedin.
- Ürün deposunu kaydedin.
- Gerekli bağımlılıkları yükleyin.

Bu işlemin makine başına tek bir kez yapılması yeterlidir.

Bir terminal açın ve aşağıdaki komutu çalıştırın.

```bash
sudo rpm -Uvh https://packages.microsoft.com/config/sles/12/packages-microsoft-prod.rpm
```

## <a name="install-the-net-core-sdk"></a>.NET Core SDK’sını yükleme

Yükleme için kullanılabilen ürünleri güncelleştirin ve sonra .NET Core SDK'yı yükleyin. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo zypper install dotnet-sdk-3.1
```

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core çalışma süresini yükleme

Yükleme için kullanılabilir ürünleri güncelleştirin ve ASP.NET çalışma süresini yükleyin. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo zypper install aspnetcore-runtime-3.1
```

## <a name="install-the-net-core-runtime"></a>.NET Core çalışma süresini yükleme

Yükleme için kullanılabilen ürünleri güncelleştirin ve .NET Core çalışma süresini yükleyin. Terminalinizde aşağıdaki komutu çalıştırın.

```bash
sudo zypper install dotnet-runtime-3.1
```

## <a name="how-to-install-other-versions"></a>Diğer sürümler nasıl yüklenir?

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Paket yöneticisinin sorun giderme

Bu bölümde, .NET Core'u yüklemek için paket yöneticisini kullanırken karşılaşabileceğiniz sık karşılaşılan hatalar hakkında bilgi verilmektedir.

### <a name="failed-to-fetch"></a>Getirilemedi

[!INCLUDE [package-manager-failed-to-fetch-rpm](includes/package-manager-failed-to-fetch-rpm.md)]
