---
title: Ubuntu 19.04 paket yöneticisine .NET Core yükle - .NET Core
description: .NET Core SDK'yı ve çalışma süresini Ubuntu 19.04'e yüklemek için bir paket yöneticisi kullanın.
author: thraka
ms.author: adegeo
ms.date: 03/17/2020
ms.openlocfilehash: 3f338832185ed626289141f48cec88c1bf2e3a33
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645598"
---
# <a name="ubuntu-1904-package-manager---install-net-core"></a>Ubuntu 19.04 Paket Yöneticisi - Install .NET Core

[!INCLUDE [package-manager-switcher](./includes/package-manager-switcher.md)]

Bu makalede, Ubuntu 19.04'e .NET Core yüklemek için bir paket yöneticisinin nasıl kullanılacağı açıklanmaktadır.

[!INCLUDE [package-manager-intro-sdk-vs-runtime](includes/package-manager-intro-sdk-vs-runtime.md)]

## <a name="add-microsoft-repository-key-and-feed"></a>Microsoft depo anahtarı ve özet akışı ekleme

.NET'i yüklemeden önce şunları yapmanız gerekir:

- Microsoft paketi imzalama anahtarını güvenilen anahtarlar listesine ekleyin.
- Depoyu paket yöneticisine ekleyin.
- Gerekli bağımlılıkları yükleyin.

Bu işlemin makine başına tek bir kez yapılması yeterlidir.

Bir terminal açın ve aşağıdaki komutları çalıştırın.

```bash
wget https://packages.microsoft.com/config/ubuntu/19.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
```

## <a name="install-the-net-core-sdk"></a>.NET Core SDK’sını yükleme

Yükleme için kullanılabilen ürünleri güncelleştirin ve sonra .NET Core SDK'yı yükleyin. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

> [!IMPORTANT]
> **Paket dotnet-sdk-3.1'i bulamayınca**benzer bir hata iletisi alırsanız, [sorun giderme bölümüne](#troubleshoot-the-package-manager) bakın.

## <a name="install-the-aspnet-core-runtime"></a>ASP.NET Core çalışma süresini yükleme

Yükleme için kullanılabilen ürünleri güncelleştirin ve ardından ASP.NET Core çalışma süresini yükleyin. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install aspnetcore-runtime-3.1
```

> [!IMPORTANT]
> **Aspnetcore-runtime-3.1 paketini bulamayınca**benzer bir hata iletisi alırsanız, [Sorun Giderme Bölümü'ne](#troubleshoot-the-package-manager) bakın.

## <a name="install-the-net-core-runtime"></a>.NET Core çalışma süresini yükleme

Yükleme için kullanılabilen ürünleri güncelleştirin ve .NET Core çalışma süresini yükleyin. Terminalinizde aşağıdaki komutları çalıştırın.

```bash
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-runtime-3.1
```

> [!IMPORTANT]
> **Paket dotnet-runtime-3.1'i bulamayınca**benzer bir hata iletisi alırsanız, [sorun giderme bölümüne](#troubleshoot-the-package-manager) bakın.

## <a name="how-to-install-other-versions"></a>Diğer sürümler nasıl yüklenir?

[!INCLUDE [package-manager-switcher](./includes/package-manager-heading-hack-pkgname.md)]

## <a name="troubleshoot-the-package-manager"></a>Paket yöneticisinin sorun giderme

Bu bölümde, .NET Core'u yüklemek için paket yöneticisini kullanırken karşılaşabileceğiniz sık karşılaşılan hatalar hakkında bilgi verilmektedir.

### <a name="unable-to-locate"></a>Bulunamıyor

**{.NET Core paketi} paketini bulamayıncabenzer**bir hata iletisi alırsanız, aşağıdaki komutları çalıştırın.

```bash
sudo dpkg --purge packages-microsoft-prod && sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

Bu işe yaramazsa, aşağıdaki komutları içeren bir el ile yükleme çalıştırabilirsiniz.

```bash
sudo apt-get install -y gpg
wget -O- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor -o microsoft.asc.gpg
sudo mv microsoft.asc.gpg /etc/apt/trusted.gpg.d/
wget https://packages.microsoft.com/config/ubuntu/19.04/prod.list
sudo mv prod.list /etc/apt/sources.list.d/microsoft-prod.list
sudo chown root:root /etc/apt/trusted.gpg.d/microsoft.asc.gpg
sudo chown root:root /etc/apt/sources.list.d/microsoft-prod.list
sudo apt-get install -y apt-transport-https
sudo apt-get update
sudo apt-get install {the .NET Core package}
```

### <a name="failed-to-fetch"></a>Getirilemedi

[!INCLUDE [package-manager-failed-to-fetch-deb](includes/package-manager-failed-to-fetch-deb.md)]
