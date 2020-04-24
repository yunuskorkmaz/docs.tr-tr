---
title: openSUSE 15 'e install .NET Core - paket yöneticisi - .NET Core
description: OpenSUSE 15'e .NET Core SDK ve çalışma süresini yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: fc4c9e30ddb0cfd3e6fe79fa4f78206f4700eeee
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645672"
---
# <a name="opensuse-15-package-manager---install-net-core"></a>openSUSE 15 Paket Yöneticisi - Install .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Bu makalede, openSUSE 15'e .NET Core yüklemek için paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a>Microsoft depo anahtarı ve özet akışı ekleme

.NET'i yüklemeden önce şunları yapmanız gerekir:

- Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.
- Depoyu paket yöneticisine ekleyin.
- Gerekli bağımlılıkları yükleyin.

Bu işlemin makine başına tek bir kez yapılması yeterlidir.

Bir terminal açın ve aşağıdaki komutları çalıştırın.

```bash
sudo zypper install libicu
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
wget https://packages.microsoft.com/config/opensuse/15/prod.repo
sudo mv prod.repo /etc/zypp/repos.d/microsoft-prod.repo
sudo chown root:root /etc/zypp/repos.d/microsoft-prod.repo
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
